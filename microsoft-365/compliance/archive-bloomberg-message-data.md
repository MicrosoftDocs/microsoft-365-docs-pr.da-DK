---
title: Konfigurer en forbindelse til at arkivere Bloomberg-meddelelsesdata
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorer kan konfigurere en dataforbindelse til at importere og arkivere data fra Bloomberg-mailværktøjet i Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: 5b1f32760542bf9ace2adaa8640571f665ba3ffb
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569859"
---
# <a name="set-up-a-connector-to-archive-bloomberg-message-data"></a>Konfigurer en forbindelse til at arkivere Bloomberg-meddelelsesdata

Brug en dataforbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere maildata om finansielle tjenester fra [samarbejdsværktøjet Bloomberg Message](https://www.bloomberg.com/professional/product/collaboration/). Når du har konfigureret en forbindelse, opretter den forbindelse til organisationens Bloomberg secure FTP-websted (SFTP) én gang om dagen og importerer mailelementer til postkasser i Microsoft 365.

Når Bloomberg-meddelelsesdata er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, indholdssøgning, Direkte arkivering, overvågning, Overholdelse af kommunikation og Microsoft 365-opbevaringspolitikker til Bloomberg-meddelelsesdata. Du kan f.eks. søge efter Bloomberg-mails ved hjælp af værktøjet til søgning efter indhold eller knytte den postkasse, der indeholder Bloomberg-meddelelsesdataene, til en medarbejder, der er Advanced eDiscovery sag. Hvis du bruger en Bloomberg-meddelelsesforbindelse til at importere og arkivere data i Microsoft 365 kan det hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-bloomberg-message-data"></a>Oversigt over arkivering af Bloomberg-meddelelsesdata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere Bloomberg-meddelelsesdata i Microsoft 365.

![Bloomberg Meddelelsesimport- og arkiveringsproces.](../media/BloombergMessageArchiving.png)

1. Din organisation arbejder sammen med Bloomberg om at oprette et Bloomberg SFTP-websted. Du skal også samarbejde med Bloomberg om at konfigurere Bloomberg-meddelelsen til at kopiere mails til webstedet Bloomberg SFTP.

2. Én gang i døgnet kopieres mails fra Bloomberg Message til webstedet Bloomberg SFTP.

3. Forbindelsen Bloomberg Message, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til Bloomberg SFTP-webstedet hver dag og overfører mails fra de foregående 24 timer til et sikkert Azure Storage-område i Microsoft Cloud.

4. Forbindelsen importerer mailelementerne til en bestemt brugers postkasse. Der oprettes en ny mappe med navnet BloombergMessage i den specifikke brugers postkasse, og elementerne importeres til den.

   Forbindelsen gør dette ved hjælp af værdien af egenskaben CorporateEmailAddress. Hver mail indeholder denne egenskab, som er udfyldt med mailadressen for hver deltager i mailen. Ud over automatisk brugertilknytning med værdien af *egenskaben CorporateEmailAddress* kan du også definere en brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder et Bloomberg UUID og den tilsvarende Microsoft 365-postkasseadresse for hver bruger i organisationen. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil forbindelsen for hvert mailelement først se på den brugerdefinerede tilknytningsfil. Hvis der ikke findes en gyldig Microsoft 365, der svarer til en brugers Bloomberg UUID, anvender forbindelsen *corporateEmailAddress-egenskaben* for mailelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller egenskaben *CorporateEmailAddress* for mailelementet, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere Bloomberg-meddelelsesdata er eksterne Microsoft 365 og skal udføres, før du kan oprette forbindelsen i overholdelsescenteret.

- Hvis du vil konfigurere en Bloomberg-meddelelsesforbindelse, skal du bruge nøgler og nøglenøgler for at opnå ret god beskyttelse af personlige oplysninger (PGP) og Secure Shell (SSH). Disse taster bruges til at konfigurere webstedet Bloomberg SFTP og bruges af forbindelsen til at oprette forbindelse til webstedet Bloomberg SFTP til at importere data til Microsoft 365. PGP-nøglen bruges til at konfigurere krypteringen af data, der er overført fra Bloomberg SFTP-webstedet til Microsoft 365. SSH-nøglen bruges til at konfigurere sikker shell for at aktivere en sikker fjernlogon, når forbindelsen opretter forbindelse til Bloomberg SFTP-webstedet.

  Når du konfigurerer en forbindelse, har du mulighed for at bruge offentlige nøgler og nøgler, der leveres af Microsoft, eller du kan bruge dine egne private nøgler og adgangskode. Vi anbefaler, at du bruger de offentlige nøgler, der leveres af Microsoft. Men hvis din organisation allerede har konfigureret et Bloomberg SFTP-websted ved hjælp af private nøgler, kan du oprette en forbindelse ved hjælp af de samme private nøgler.

- Abonner [på Bloomberg overalt](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Dette er påkrævet, for at du kan logge på Bloomberg overalt for at få adgang til webstedet Bloomberg SFTP, som du skal konfigurere og konfigurere.

- Konfigurer et Bloomberg SFTP-websted (Secure File Transfer Protocol). Når du har arbejdet med Bloomberg for at konfigurere SFTP-webstedet, uploades data fra Bloomberg Message til SFTP-webstedet hver dag. Den forbindelse, du opretter i trin 2, opretter forbindelse til dette SFTP-websted og overfører maildataene Microsoft 365 postkasser. SFTP krypterer også de Bloomberg-meddelelsesdata, der sendes til postkasser under overførslen.

  For oplysninger om Bloomberg SFTP (også kaldet *BB-SFTP*):

  - Se dokumentet "SFTP Connectivity Standards" hos [Bloomberg Support](https://www.bloomberg.com/professional/support/documentation/).

  - Kontakt [Bloombergs kundesupport](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

- Når du har arbejdet med Bloomberg om at konfigurere et SFTP-websted, giver Bloomberg dig nogle oplysninger, når du har besvaret meddelelsen om Bloombergs implementering. Gem en kopi af følgende oplysninger. Du kan bruge den til at konfigurere en forbindelse i trin 3.

  - Firmakode, som er et id for din organisation og bruges til at logge på Bloomberg SFTP-webstedet.

  - Adgangskode til dit Bloomberg SFTP-websted

  - URL-adresse til Bloomberg SFTP-websted (f.eks. sftp.bloomberg.com). Desuden kan Bloomberg også angive en tilsvarende IP-adresse til Bloomberg SFTP-webstedet, som også kan bruges til at konfigurere forbindelsen.

  - Portnummer for Bloomberg SFTP-websted

- Bloomberg-meddelelsesforbindelse kan importere 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 elementer på SFTP-webstedet, importeres ingen af disse elementer til Microsoft 365.

- Den bruger, der opretter en Bloomberg-meddelelsesforbindelse i trin 3 (og som downloader de offentlige nøgler og IP-adressen i trin 1), skal have tildelt administratorrollen Dataforbindelse. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurer en forbindelse ved hjælp af offentlige taster

Trinnene i dette afsnit viser, hvordan du konfigurerer en Bloomberg-meddelelsesforbindelse ved hjælp af de offentlige nøgler til Pretty Good Privacy (PGP) og Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>Trin 1: Hent offentlige PGP- og SSH-nøgler

Det første trin er at hente en kopi af de offentlige PGP- og SSH-nøgler. Du kan bruge disse taster i trin 2 til at konfigurere Bloomberg SFTP-webstedet, så den forbindelse (som du opretter i trin 3) kan oprette forbindelse til SFTP-webstedet og overføre Bloomberg-meddelelsesmaildataene til Microsoft 365-postkasser. Du kan også hente en IP-adresse i dette trin, som du bruger, når du konfigurerer Bloomberg SFTP-webstedet.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **Vis på siden Dataforbindelser** under **Bloomberg-meddelelse**.

3. Klik på **Tilføj forbindelse på** produktbeskrivelsen for **Bloomberg-meddelelsen**

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på Jeg vil bruge offentlige **PGP- og SSH-nøgler, der leveres af Microsoft**.

   ![Vælg indstillingen for at bruge offentlige nøgler.](../media/BloombergMessagePublicKeysOption.png)

6. Under trin 1 skal du klikke på **Download SSH-tasten**, **Download PGP-nøgle** og **Download IP-adresselinks** for at gemme en kopi af hver fil på din lokale computer.

   ![Links til at downloade offentlige nøgler og IP-adresse.](../media/BloombergMessagePublicKeyDownloadLinks.png)

   Disse filer indeholder følgende elementer, der bruges til at konfigurere Bloomberg SFTP-webstedet i trin 2:

   - Offentlig PGP-nøgle: Denne nøgle bruges til at konfigurere krypteringen af data, der overføres fra Bloomberg SFTP-webstedet til Microsoft 365.

   - Offentlig SSH-nøgle: Denne nøgle bruges til at konfigurere sikker shell til at aktivere en sikker ekstern logon, når forbindelsen opretter forbindelse til Bloomberg SFTP-webstedet.

   - IP-adresse: Bloomberg SFTP-webstedet er konfigureret til at acceptere forbindelsesanmodninger fra denne IP-adresse. Den samme IP-adresse bruges af forbindelsen Bloomberg Message til at oprette forbindelse til SFTP-webstedet og overføre Bloomberg-meddelelsesdata til Microsoft 365.

7. Klik **på Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 3 for at oprette forbindelsen.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>Trin 2: Konfigurer Bloomberg SFTP-webstedet

> [!NOTE]
> Hvis din organisation tidligere har konfigureret et Bloomberg SFTP-websted til at arkivere Instant Bloomberg-data ved hjælp af offentlige PGP- og SSH-nøgler, behøver du ikke at oprette endnu en. Du kan angive det samme SFTP-websted, når du opretter forbindelsen i trin 3.

Det næste trin er at bruge de offentlige PGP- og SSH-nøgler og den IP-adresse, du fik i trin 1, til at konfigurere PGP-kryptering og SSH-godkendelse til Bloomberg SFTP-webstedet. Det gør det muligt for forbindelsesværktøjet Bloomberg-meddelelse, som du opretter i trin 3, at oprette forbindelse til Bloomberg SFTP-webstedet og overføre Bloomberg-meddelelsesdata Microsoft 365. Du skal samarbejde med Bloombergs kundesupport for at konfigurere dit Bloomberg SFTP-websted. Kontakt [Bloombergs kundesupport for at](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) få hjælp.

> [!IMPORTANT]
> Bloomberg anbefaler, at du vedhæfter de tre filer, du hentede i trin 1, i en mail og sender den til deres kundesupportteam, når du arbejder med dem, for at konfigurere dit Bloomberg SFTP-websted.

### <a name="step-3-create-a-bloomberg-message-connector"></a>Trin 3: Opret en Bloomberg Message-forbindelse

Det sidste trin er at oprette en Bloomberg Message-forbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til Bloomberg SFTP-webstedet og overføre mails til de tilsvarende postkassefelter i Microsoft 365.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **Vis på siden Dataforbindelser** under **Bloomberg-meddelelse**.

3. Klik på **Tilføj forbindelse på** produktbeskrivelsen for **Bloomberg-meddelelsen**

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på Jeg vil bruge offentlige **PGP- og SSH-nøgler, der leveres af Microsoft**.

6. Under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Valider forbindelse**.

      - **Navn:** Navnet på forbindelsen. Det skal være entydigt i din organisation.

      - **Firmakode:** Id'et for din organisation, der bruges som brugernavn for Bloomberg SFTP-webstedet.

      - **Adgangskode:** Adgangskoden til din organisations Bloomberg SFTP-websted.

      - **SFTP-URL-ADRESSE:** URL-adressen for webstedet Bloomberg SFTP (f.eks. `sftp.bloomberg.com`). Du kan også bruge en IP-adresse til denne værdi.

      - **SFTP-port:** Portnummeret for Bloomberg SFTP-webstedet. Forbindelsen bruger denne port til at oprette forbindelse til SFTP-webstedet.

7. Klik på Næste, når forbindelsen er blevet **valideret**.

8. På siden **Definer bruger** skal du angive de brugere, der skal importere data til.

     - **Alle brugere i organisationen**. Markér denne indstilling for at importere data for alle brugere.

     - **Kun brugere, der er i retslig venteposition**. Markér denne indstilling for kun at importere data for brugere, hvis postkasser er placeret i retslig venteposition. Denne indstilling importerer data til brugerpostkasser, der har egenskaben LitigationHoldEnabled angivet til Sand. Få mere at vide under [Opret en retslig venteposition](create-a-litigation-hold.md).

9. På siden **Bloomberg-meddelelsesbrugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov.

   > [!NOTE]
   > Forbindelsen importerer meddelelseselementer til en bestemt brugers postkasse. Der oprettes en **ny mappe med navnet BloombergMessage** i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen gør ved hjælp af værdien af *egenskaben CorporateEmailAddress* . Alle chatbeskeder indeholder denne egenskab, og egenskaben udfyldes med mailadressen for hver deltager i chatmeddelelsen. Ud over automatisk brugertilknytning med værdien af *egenskaben CorporateEmailAddress* kan du også definere brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Tilknytningsfilen skal indeholde Bloomberg UUID og den tilhørende Microsoft 365-postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil forbindelsen for hvert meddelelseselement først se på brugerdefineret tilknytningsfil. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers Bloomberg UUID, vil forbindelsen bruge *egenskaben CorporateEmailAddress* for chatelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller egenskaben *CorporateEmailAddress* for meddelelseselementet, importeres elementet ikke.

10. Klik **på** Næste, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette forbindelsen.

11. Gå til siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse. Klik på forbindelsen for at få vist pop op-siden, der indeholder oplysninger om forbindelsen.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurer en forbindelse ved hjælp af private taster

Trinnene i dette afsnit viser, hvordan du konfigurerer en Bloomberg Message-forbindelse ved hjælp af private PGP- og SSH-nøgler. Denne indstilling for konfiguration af forbindelse er beregnet til organisationer, der allerede har konfigureret et Bloomberg SFTP-websted ved hjælp af private nøgler.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>Trin 1: Hent en IP-adresse for at konfigurere Bloomberg SFTP-webstedet

> [!NOTE]
> Hvis din organisation tidligere har konfigureret et Bloomberg SFTP-websted til at arkivere Instant Bloomberg-data ved hjælp af private PGP- og SSH-nøgler, behøver du ikke at konfigurere endnu en. Du kan angive det samme SFTP-websted, når du opretter forbindelsen i trin 2.

Hvis din organisation har brugt private PGP- og SSH-nøgler til at konfigurere et Bloomberg SFTP-websted, skal du hente en IP-adresse og levere den til Bloombergs kundesupport. Bloomberg SFTP-webstedet skal konfigureres til at acceptere forbindelsesanmodninger fra denne IP-adresse. Den samme IP-adresse bruges af forbindelsen Bloomberg Message til at oprette forbindelse til SFTP-webstedet og overføre Bloomberg-meddelelsesdata til Microsoft 365.

Sådan får du IP-adressen:

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **Vis på siden Dataforbindelser** under **Bloomberg-meddelelse**.

3. Klik på **Tilføj forbindelse på** produktbeskrivelsen for **Bloomberg-meddelelsen**

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke **på Jeg vil bruge private PGP- og SSH-nøgler**.

6. Under trin 1 skal du klikke **på Download IP-adresse** for at gemme en kopi af IP-adressefilen på din lokale computer.

   ![Download IP-adressen.](../media/BloombergMessageConnectorIPAddress.png)

7. Klik **på Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 2 for at oprette forbindelsen.

Du skal samarbejde med Bloombergs kundesupport for at konfigurere dit Bloomberg SFTP-websted til at acceptere forbindelsesanmodninger fra denne IP-adresse. Kontakt [Bloombergs kundesupport for at](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) få hjælp.

### <a name="step-2-create-a-bloomberg-message-connector"></a>Trin 2: Opret en Bloomberg Message-forbindelse

Når du har konfigureret dit Bloomberg SFTP-websted, er næste trin at oprette en Bloomberg-meddelelsesforbindelse Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til Bloomberg SFTP-webstedet og overføre mails til de tilsvarende postkassefelter i Microsoft 365. For at fuldføre dette trin skal du sørge for at have kopier af de samme private nøgler og nøgler, som du brugte til at konfigurere dit Bloomberg SFTP-websted.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. Klik på **Vis på siden Dataforbindelser** under **Bloomberg-meddelelse**.

3. Klik på **Tilføj forbindelse på** produktbeskrivelsen for **Bloomberg-meddelelsen**

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke **på Jeg vil bruge private PGP- og SSH-nøgler**.

   ![Vælg indstillingen for at bruge private nøgler.](../media/BloombergMessagePrivateKeysOption.png)

6. Under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Valider forbindelse**.

      - **Navn:** Navnet på forbindelsen. Det skal være entydigt i din organisation.

      - **Firmakode:** Id'et for din organisation, der bruges som brugernavn for Bloomberg SFTP-webstedet.

      - **Adgangskode:** Adgangskoden til din organisations Bloomberg SFTP-websted.

      - **SFTP-URL-ADRESSE:** URL-adressen for webstedet Bloomberg SFTP (f.eks. `sftp.bloomberg.com`). Du kan også bruge en IP-adresse til denne værdi.

      - **SFTP-port:** Portnummeret for Bloomberg SFTP-webstedet. Forbindelsen bruger denne port til at oprette forbindelse til SFTP-webstedet.

      - **Privat PGP-nøgle:** Den private PGP-nøgle til Bloomberg SFTP-webstedet. Sørg for at medtage hele den private nøgleværdi, herunder de første og sidste linjer i nøgleblokken.

      - **PGP-nøgle-adgangskode:** Adgangsordet for den private PGP-nøgle.

      - **Privat SSH-nøgle:** Den private SSH-nøgle til Bloomberg SFTP-webstedet. Sørg for at medtage hele den private nøgleværdi, herunder de første og sidste linjer i nøgleblokken.

      - **SSH-tasten adgangskode:** Adgangsordet for den private SSH-nøgle.

7. Klik på Næste, når forbindelsen er blevet **valideret**.

8. På siden **Definer bruger** skal du angive de brugere, der skal importere data for

     - **Alle brugere i organisationen**. Markér denne indstilling for at importere data for alle brugere.

     - **Kun brugere, der er i retslig venteposition**. Markér denne indstilling for kun at importere data for brugere, hvis postkasser er placeret i retslig venteposition. Denne indstilling importerer data til brugerpostkasser, der har egenskaben LitigationHoldEnabled angivet til Sand. Få mere at vide under [Opret en retslig venteposition](create-a-litigation-hold.md).

9. På siden **Bloomberg-meddelelsesbrugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov.

   > [!NOTE]
   > Forbindelsen importerer meddelelseselementer til en bestemt brugers postkasse. Der oprettes en **ny mappe med navnet BloombergMessage** i den specifikke brugers postkasse, og elementerne importeres til den. Forbindelsen gør ved hjælp af værdien af *egenskaben CorporateEmailAddress* . Alle chatbeskeder indeholder denne egenskab, og egenskaben udfyldes med mailadressen for hver deltager i chatmeddelelsen. Ud over automatisk brugertilknytning med værdien af *egenskaben CorporateEmailAddress* kan du også definere brugerdefineret tilknytning ved at uploade en CSV-tilknytningsfil. Tilknytningsfilen skal indeholde Bloomberg UUID og den tilhørende Microsoft 365-postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil forbindelsen for hvert meddelelseselement først se på brugerdefineret tilknytningsfil. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers Bloomberg UUID, vil forbindelsen bruge *egenskaben CorporateEmailAddress* for chatelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller egenskaben *CorporateEmailAddress* for meddelelseselementet, importeres elementet ikke.

10. Klik **på** Næste, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette forbindelsen.

11. Gå til siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse. Klik på forbindelsen for at få vist pop op-siden, der indeholder oplysninger om forbindelsen.

## <a name="known-issues"></a>Kendte problemer

- Trådning af Bloomberg-meddelelsesmail importeret til Microsoft 365 understøttes ikke. Individuelle meddelelser, der sendes til en person, importeres, men de præsenteres ikke i en samtaletråd. Microsoft arbejder på at understøtte trådning i nyere versioner af dataforbindelsesforbindelse Bloomberg Message.
