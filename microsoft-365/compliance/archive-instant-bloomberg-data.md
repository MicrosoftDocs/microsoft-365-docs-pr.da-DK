---
title: Konfigurer en connector til arkivering af Instant Bloomberg-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan administratorer kan konfigurere og bruge en dataconnector til at importere og arkivere data fra Chatværktøjet Instant Bloomberg til Microsoft 365.
ms.openlocfilehash: 3729c36df27e6def709dc5d2c976885c3db5a518
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64938659"
---
# <a name="set-up-a-connector-to-archive-instant-bloomberg-data"></a>Konfigurer en connector til arkivering af Instant Bloomberg-data

Brug en oprindelig connector i Microsoft Purview-overholdelsesportalen til at importere og arkivere chatdata om finansielle tjenester fra [Instant Bloomberg-samarbejdsværktøjet](https://www.bloomberg.com/professional/product/collaboration/) . Når du har konfigureret en connector, opretter den forbindelse til din organisations SFTP (Secure FTP Site) i Bloomberg én gang om dagen, konverterer indholdet af chatbeskeder til et mailformat og importerer derefter disse elementer til postkasser i Microsoft 365.

Når Instant Bloomberg-data er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner som Litigation Hold, Content Search, In-Place Archiving, Auditing, Communication compliance og Microsoft 365 retention policies på Instant Bloomberg-data. Du kan f.eks. søge i Chatbeskeder i Instant Bloomberg ved hjælp af Indholdssøgning eller knytte den postkasse, der indeholder Instant Bloomberg-dataene, til en tilsynsførende i en Microsoft Purview eDiscovery-sag (Premium). Brug af en Instant Bloomberg-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde de offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-instant-bloomberg-data"></a>Oversigt over arkivering af Instant Bloomberg-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere Instant Bloomberg-chatdata i Microsoft 365. 

![Øjeblikkelig Bloomberg import- og arkivproces.](../media/InstantBloombergDataArchiving.png)

1. Din organisation samarbejder med Bloomberg om at oprette et Bloomberg SFTP-websted. Du skal også samarbejde med Bloomberg om at konfigurere Instant Bloomberg til at kopiere chatbeskeder til din Bloomberg SFTP-side.

2. En gang hver 24 timer kopieres chatbeskeder fra Instant Bloomberg til Bloomberg SFTP-webstedet.

3. Den Instant Bloomberg-connector, du opretter på overholdelsesportalen, opretter forbindelse til Bloomberg SFTP-webstedet hver dag og overfører chatbeskederne fra de forrige 24 timer til et sikkert Azure Storage område i Microsoft Cloud. Connectoren konverterer også indholdet af en chatmassage til et mailformat.

4. Connectoren importerer chatmeddelelseselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet InstantBloomberg i den specifikke brugers postkasse, og elementerne importeres til den. Connectoren gør dette ved hjælp af værdien af egenskaben *CorporateEmailAddress* . Alle chatbeskeder indeholder denne egenskab, som udfyldes med mailadressen på hver deltager i chatmeddelelsen. Ud over automatisk brugertilknytning ved hjælp af værdien af egenskaben *CorporateEmailAddress* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil skal indeholde en Bloomberg UUID og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, kigger connectoren først på brugerdefineret tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers Bloomberg UUID, bruger connectoren egenskaben *CorporateEmailAddress* for chatelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede tilknytningsfil eller egenskaben *CorporateEmailAddress* for chatelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de implementeringstrin, der kræves for at arkivere Instant Bloomberg-data, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette connectoren i Overholdelsescenter.

- Hvis du vil konfigurere en Instant Bloomberg-connector, skal du bruge nøgler og adgangsudtryk til Pretty Good Privacy (PGP) og Secure Shell (SSH). Disse nøgler bruges til at konfigurere Bloomberg SFTP-webstedet og bruges af connectoren til at oprette forbindelse til Bloomberg SFTP-webstedet for at importere data til Microsoft 365. PGP-nøglen bruges til at konfigurere krypteringen af data, der overføres fra Bloomberg SFTP-webstedet, til Microsoft 365. SSH-nøglen bruges til at konfigurere Secure Shell for at aktivere et sikkert fjernlogon, når connectoren opretter forbindelse til Bloomberg SFTP-webstedet.

  Når du konfigurerer en connector, har du mulighed for at bruge offentlige nøgler og nøgleadgangsudtryk fra Microsoft, eller du kan bruge dine egne private nøgler og adgangsudtryk. Vi anbefaler, at du bruger de offentlige nøgler, der leveres af Microsoft. Men hvis din organisation allerede har konfigureret et Bloomberg SFTP-websted ved hjælp af private nøgler, kan du oprette en connector ved hjælp af de samme private nøgler.

- Abonner på [Bloomberg Anywhere](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Dette er påkrævet, så du kan logge ind på Bloomberg Anywhere for at få adgang til Bloomberg SFTP site, som du er nødt til at oprette og konfigurere.

- Konfigurer et Bloomberg SFTP-websted (Secure File Transfer Protocol). Efter at have samarbejdet med Bloomberg om at etablere SFTP-webstedet, uploades data fra Instant Bloomberg hver dag til SFTP-webstedet. Den connector, du opretter i trin 2, opretter forbindelse til dette SFTP-websted og overfører chatdataene til Microsoft 365 postkasser. SFTP krypterer også De Instant Bloomberg-chatdata, der sendes til postkasser under overførselsprocessen.

  For information om Bloomberg SFTP (også kaldet *BB-SFTP*):

  - Se dokumentet "SFTP Connectivity Standards" på [Bloomberg Support](https://www.bloomberg.com/professional/support/documentation/).

  - Kontakt [Bloombergs kundesupport](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

  Når du har arbejdet sammen med Bloomberg om at oprette en SFTP-hjemmeside, vil Bloomberg give dig nogle oplysninger, når du har svaret på Bloombergs implementeringsmailmeddelelse. Gem en kopi af følgende oplysninger. Du kan bruge den til at konfigurere en connector i trin 3.

  - Firmakode, som er et id for din organisation og bruges til at logge på Bloomberg SFTP-webstedet.

  - Adgangskode til dit Bloomberg SFTP-websted

  - URL-adresse til Bloomberg SFTP-websted (f.eks. sftp.bloomberg.com)

  - Portnummer til Bloomberg SFTP-grund

- Instant Bloomberg-connectoren kan importere i alt 200.000 varer på en enkelt dag. Hvis der er mere end 200.000 elementer på SFTP-webstedet, importeres ingen af disse elementer til Microsoft 365.

- Den bruger, der opretter en Instant Bloomberg-connector i trin 3 (og som downloader de offentlige nøgler og IP-adressen i trin 1), skal tildeles rollen Data Connector-administrator. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurer en connector ved hjælp af offentlige nøgler

Trinnene i dette afsnit viser, hvordan du konfigurerer en Instant Bloomberg-connector ved hjælp af de offentlige nøgler til PGP (Pretty Good Privacy) og Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-and-public-keys"></a>Trin 1: Hent PGP og SSH og offentlige nøgler

Det første trin er at få en kopi af de offentlige nøgler til Pretty Good Privacy (PGP) og Secure Shell (SSH). Du kan bruge disse nøgler i trin 2 til at konfigurere Bloomberg SFTP-webstedet, så connectoren (som du opretter i trin 3) kan oprette forbindelse til SFTP-webstedet og overføre Instant Bloomberg-chatdataene til Microsoft 365 postkasser. Du får også en IP-adresse i dette trin, som du bruger, når du konfigurerer Bloomberg SFTP-webstedet.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **Instant Bloomberg**.

3. Klik på **Tilføj connector** på siden **Instant Bloomberg-produktbeskrivelse**

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. Klik på **Jeg vil bruge offentlige PGP- og SSH-nøgler fra Microsoft** på siden **Tilføj legitimationsoplysninger til indholdskilde**.

   ![Vælg indstillingen for at bruge offentlige nøgler.](../media/InstantBloombergPublicKeysOption.png)

6. Under trin 1 skal du klikke på linkene **Download SSH,** **Download PGP** og **Download IP-adresse** for at gemme en kopi af hver fil på din lokale computer.

   ![Links til download af offentlige nøgler og IP-adresse.](../media/InstantBloombergPublicKeyDownloadLinks.png)

   Disse filer indeholder følgende elementer, der bruges til at konfigurere Bloomberg SFTP-webstedet i trin 2:

   - Offentlig PGP-nøgle: Denne nøgle bruges til at konfigurere krypteringen af data, der overføres fra Bloomberg SFTP-webstedet til Microsoft 365.

   - Offentlig SSH-nøgle: Denne nøgle bruges til at konfigurere sikker shell for at aktivere et sikkert fjernlogon, når connectoren opretter forbindelse til Bloomberg SFTP-webstedet.

   - IP-adresse: Bloomberg SFTP-webstedet er konfigureret til at acceptere forbindelsesanmodninger fra denne IP-adresse. Den samme IP-adresse bruges af Instant Bloomberg-connectoren til at oprette forbindelse til SFTP-webstedet og overføre Instant Bloomberg-data til Microsoft 365.

7. Klik på **Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 3 for at oprette connectoren.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>Trin 2: Konfigurer Bloomberg SFTP-webstedet

Næste trin er at bruge de offentlige PGP- og SSH-nøgler og den IP-adresse, du fik i trin 1, til at konfigurere PGP-kryptering og SSH-godkendelse for Bloomberg SFTP-webstedet. Det gør det muligt for Instant Bloomberg-connectoren, som du opretter i Trin 3, at oprette forbindelse til Bloomberg SFTP-webstedet og overføre Instant Bloomberg-data til Microsoft 365. Du skal samarbejde med Bloombergs kundesupport om at oprette dit Bloomberg SFTP site. Kontakt [Bloombergs kundesupport](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) for at få hjælp. 

> [!IMPORTANT]
> Bloomberg anbefaler, at du vedhæfter de tre filer, du downloadede i trin 1, til en mail og sender dem til deres kundesupportteam, når du arbejder sammen med dem om at oprette dit Bloomberg SFTP-websted.

### <a name="step-3-create-an-instant-bloomberg-connector"></a>Trin 3: Opret en Instant Bloomberg-connector

Det sidste trin er at oprette en Instant Bloomberg-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til Bloomberg SFTP-webstedet og overføre chatbeskeder til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , <https://compliance.microsoft.com> og klik derefter på **Data connectorsInstant** >  **Bloomberg**.

2. Klik på **Tilføj connector** på siden **Instant Bloomberg-produktbeskrivelse**

3. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

4. Angiv de nødvendige oplysninger i følgende felter under Trin 3 på **siden Tilføj legitimationsoplysninger til Bloomberg SFTP** , og klik derefter på **Næste**.

    - **Firmakode:** Det id for din organisation, der bruges som brugernavn for Bloomberg SFTP-webstedet.

    - **Adgangskode:** Adgangskode til Bloomberg SFTP site.

    - **URL-adresse til SFTP:** URL-adressen til Bloomberg SFTP-webstedet (f.eks. `sftp.bloomberg.com`). Du kan også bruge en IP-adresse til denne værdi.

    - **SFTP-port:** Portnummeret for Bloomberg SFTP-pladsen. Connectoren bruger denne port til at oprette forbindelse til SFTP-webstedet.

5. På siden **Definer bruger** skal du vælge en af følgende indstillinger for at angive de brugere, hvis data du vil importere.

    - **Alle brugere i din organisation**. Vælg denne indstilling for at importere data for alle brugere.

    - **Kun brugere, der er i strid med procesførelse**. Vælg denne indstilling, hvis du kun vil importere data for brugere, hvis postkasser er sat i strid med procesførelse. Denne indstilling importerer data til brugerpostkasser, hvor egenskaben LitigationHoldEnabled er angivet til Sand. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](create-a-litigation-hold.md).

6. På siden **Vælg de datatyper, der skal importeres** skal du vælge de datatyper, der skal importeres, bortset fra **Meddelelser**

7. På siden **Map Instant Bloomberg-brugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov

   > [!NOTE]
   > Connectoren importerer chatmeddelelseselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet **InstantBloomberg** i den specifikke brugers postkasse, og elementerne importeres til den. Det gør connectoren ved hjælp af værdien af egenskaben *CorporateEmailAddress* . Alle chatbeskeder indeholder denne egenskab, og egenskaben udfyldes med mailadressen på hver deltager i chatmeddelelsen. Ud over automatisk brugertilknytning ved hjælp af værdien af egenskaben *CorporateEmailAddress* kan du også definere brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Tilknytningsfilen skal indeholde Bloomberg UUID og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers Bloomberg UUID, bruger connectoren egenskaben *CorporateEmailAddress* for chatelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede *tilknytningsfil eller egenskaben CorporateEmailAddress* for chatelementet, importeres elementet ikke.

7. Klik på **Næste**, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette connectoren.

8. Gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector. Klik på connectoren for at få vist pop op-siden, der indeholder oplysninger om connectoren.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurer en connector ved hjælp af private nøgler

Trinnene i dette afsnit viser, hvordan du konfigurerer en Instant Bloomberg-connector ved hjælp af private PGP- og SSH-nøgler. Denne indstilling for connectorkonfiguration er beregnet til organisationer, der allerede har konfigureret et Bloomberg SFTP-websted ved hjælp af private nøgler.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>Trin 1: Få en IP-adresse for at konfigurere Bloomberg SFTP-webstedet

> [!NOTE]
> Hvis din organisation tidligere har konfigureret et Bloomberg SFTP-websted til arkivering af Bloomberg Message-data ved hjælp af private PGP- og SSH-nøgler, behøver du ikke at konfigurere en anden. Du kan angive det samme SFTP-websted, når du opretter connectoren i trin 2.

Hvis din organisation har brugt private nøgler til PGP og SSH til at oprette et Bloomberg SFTP-websted, skal du have en IP-adresse og give den til Bloombergs kundesupport. Bloomberg SFTP-webstedet skal være konfigureret til at acceptere forbindelsesanmodninger fra denne IP-adresse. Den samme IP-adresse bruges af Instant Bloomberg-connectoren til at oprette forbindelse til SFTP-webstedet og overføre Instant Bloomberg-data til Microsoft 365.

Sådan henter du IP-adressen:

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **Instant Bloomberg**.

3. Klik på **Tilføj connector** på siden **Instant Bloomberg-produktbeskrivelse**

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på **Jeg vil bruge private PGP- og SSH-nøgler**.

6. Under trin 1 skal du klikke på **Download IP-adresse** for at gemme en kopi af IP-adressefilen på din lokale computer.

   ![Download IP-adressen.](../media/InstantBloombergConnectorIPAddress.png)

7. Klik på **Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 2 for at oprette connectoren.

Du skal samarbejde med Bloombergs kundesupport om at konfigurere dit Bloomberg SFTP-websted til at acceptere forbindelsesanmodninger fra denne IP-adresse. Kontakt [Bloombergs kundesupport](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) for at få hjælp.

### <a name="step-2-create-an-instant-bloomberg-connector"></a>Trin 2: Opret en Instant Bloomberg-connector

Når dit Bloomberg SFTP-websted er konfigureret, er næste trin at oprette en Instant Bloomberg-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til Bloomberg SFTP-webstedet og overføre mailmeddelelser til de tilsvarende brugerpostkasser i Microsoft 365. For at fuldføre dette trin skal du sørge for at have kopier af de samme private nøgler og adgangsudtryk, som du brugte til at konfigurere dit Bloomberg SFTP-websted.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **Instant Bloomberg**.

3. Klik på **Tilføj connector** på siden **Instant Bloomberg-produktbeskrivelse**

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på **Jeg vil bruge private PGP- og SSH-nøgler**.

   ![Vælg indstillingen for at bruge private nøgler.](../media/InstantBloombergPrivateKeysOption.png)

6. Angiv de nødvendige oplysninger i følgende felter under Trin 3, og klik derefter på **Valider forbindelse**.

      - **Navn:** Navnet på connectoren. Det skal være entydigt i din organisation.

      - **Firmakode:** Det id for din organisation, der bruges som brugernavn for Bloomberg SFTP-webstedet.

      - **Adgangskode:** Adgangskoden til din organisations Bloomberg SFTP-hjemmeside.

      - **URL-adresse til SFTP:** URL-adressen for Bloomberg SFTP-webstedet (f.eks. `sftp.bloomberg.com`). Du kan også bruge en IP-adresse til denne værdi.

      - **SFTP-port:** Portnummeret for Bloomberg SFTP-pladsen. Connectoren bruger denne port til at oprette forbindelse til SFTP-webstedet.

      - **Privat PGP-nøgle:** Den private PGP-nøgle til Bloomberg SFTP-pladsen. Sørg for at inkludere hele den private nøgleværdi, herunder start- og slutlinjerne for nøgleblokken.

      - **Adgangsudtryk til PGP-nøgle:** Adgangsudtrykket for den private PGP-nøgle.

      - **Privat SSH-nøgle:** Den private SSH-nøgle til Bloomberg SFTP-webstedet. Sørg for at inkludere hele den private nøgleværdi, herunder start- og slutlinjerne for nøgleblokken.

      - **Adgangsudtryk til SSH-nøgle:** Adgangsudtrykket for den private SSH-nøgle.

7. Når forbindelsen er valideret, skal du klikke på **Næste**.

8. På siden **Definer bruger** skal du vælge en af følgende indstillinger for at angive de brugere, hvis data du vil importere.

    - **Alle brugere i din organisation**. Vælg denne indstilling for at importere data for alle brugere.

    - **Kun brugere, der er i strid med procesførelse**. Vælg denne indstilling, hvis du kun vil importere data for brugere, hvis postkasser er sat i strid med procesførelse. Denne indstilling importerer data til brugerpostkasser, hvor egenskaben LitigationHoldEnabled er angivet til Sand. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](create-a-litigation-hold.md).

9. På siden **Map Instant Bloomberg-brugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov.

   > [!NOTE]
   > Connectoren importerer chatmeddelelseselementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet **InstantBloomberg** i den specifikke brugers postkasse, og elementerne importeres til den. Det gør connectoren ved hjælp af værdien af egenskaben *CorporateEmailAddress* . Alle chatbeskeder indeholder denne egenskab, og egenskaben udfyldes med mailadressen på hver deltager i chatmeddelelsen. Ud over automatisk brugertilknytning ved hjælp af værdien af egenskaben *CorporateEmailAddress* kan du også definere brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Tilknytningsfilen skal indeholde Bloomberg UUID og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers Bloomberg UUID, bruger connectoren egenskaben *CorporateEmailAddress* for chatelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede *tilknytningsfil eller egenskaben CorporateEmailAddress* for chatelementet, importeres elementet ikke.

10. Klik på **Næste**, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette connectoren.

11. Gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector. Klik på connectoren for at få vist pop op-siden, der indeholder oplysninger om connectoren.
