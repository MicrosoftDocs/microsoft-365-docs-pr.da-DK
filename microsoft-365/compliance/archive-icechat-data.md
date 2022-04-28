---
title: Konfigurer en connector til arkivering af ICE Chat-data
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Administratorer kan konfigurere en connector til at importere og arkivere data fra ICE Chat-værktøjet i Microsoft 365. Det giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365 så du kan bruge funktioner til overholdelse af angivne standarder, f.eks. juridisk bevarelse, indholdssøgning og opbevaringspolitikker til at administrere din organisations tredjepartsdata.
ms.openlocfilehash: 1704795d28062bf6259129e2548e797b2f6bc7e9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090555"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>Konfigurer en connector til arkivering af ICE Chat-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]V

Brug en oprindelig connector i Microsoft Purview-overholdelsesportalen til at importere og arkivere chatdata for finansielle tjenester fra ICE Chat-samarbejdsværktøjet. Når du har konfigureret en connector, opretter den forbindelse til organisationens SFTP-websted (ICE Chat secure FTP) én gang om dagen, konverterer indholdet af chatbeskeder til et mailformat og importerer derefter disse elementer til postkasser i Microsoft 365.

Når ICE-chatdata er gemt i brugerpostkasser, kan du anvende Microsoft Purview-funktioner som f.eks. bevarelse af tvister, eDiscovery, arkivering, overvågning, overholdelse af kommunikation og Microsoft 365 opbevaringspolitikker på ICE Chat-data. Du kan f.eks. søge i ICE Chat-meddelelser ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder ICE Chat-dataene, til en tilsynsførende i en eDiscovery-sag (Premium). Brug af en ICE Chat-connector til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovgivningsmæssige politikker.

## <a name="overview-of-archiving-ice-chat-data"></a>Oversigt over arkivering af ICE Chat-data

I følgende oversigt forklares processen med at bruge en connector til at arkivere ICE-chatdata i Microsoft 365.

![ICE Chat-arkiveringsarbejdsproces.](../media/ICEChatConnectorWorkflow.png)

1. Din organisation arbejder sammen med ICE Chat om at oprette et ICE Chat SFTP-websted. Du skal også arbejde med ICE Chat for at konfigurere ICE Chat til at kopiere chatbeskeder til dit ICE Chat SFTP-websted.

2. Hver 24. time kopieres chatbeskeder fra ICE Chat til din ICE Chat SFTP-side.

3. Den ICE Chat-connector, du opretter på overholdelsesportalen, opretter forbindelse til ICE Chat SFTP-webstedet hver dag og overfører chatmeddelelserne fra de forrige 24 timer til en sikker Azure Storage placering i Microsoft-cloudmiljøet. Connectoren konverterer også indholdet af en chatmassage til et mailformat.

4. Connectoren importerer chatbeskedelementer til bestemte brugeres postkasser. Der oprettes en ny mappe med navnet **ICE Chat** i brugerpostkasserne, og elementerne i chatmeddelelsen importeres til den pågældende mappe. Det gør connectoren ved hjælp af værdien af egenskaberne *SenderEmail* og *RecipientEmail* . Alle chatbeskeder indeholder disse egenskaber, som udfyldes med afsenderens mailadresse og alle modtagere/deltagere i chatmeddelelsen.

   Ud over automatisk brugertilknytning, der bruger værdierne for egenskaben *SenderEmail* og *RecipientEmail* (hvilket betyder, at connectoren importerer en chatmeddelelse til afsenderens postkasse og postkasserne for hver modtager), kan du også definere brugerdefineret brugertilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder ICE Chat *ImId* og den tilsvarende Microsoft 365 postkasseadresse for alle brugere i organisationen. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytningsfil, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365 brugerkonto, der svarer til en brugers ICE Chat ImId, bruger connectoren egenskaberne *SenderEmail* og *RecipientEmail* for chatelementet til at importere elementet til chatdeltagernes postkasser. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger i enten den brugerdefinerede tilknytningsfil eller egenskaberne *SenderEmail* og *RecipientEmail*, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Nogle af de implementeringstrin, der kræves for at arkivere ICE Chat-data, er eksterne i forhold til Microsoft 365 og skal fuldføres, før du kan oprette connectoren i Overholdelsescenter.

- ICE Chat opkræver et gebyr for ekstern overholdelse af angivne standarder for deres kunder. Din organisation skal kontakte ICE Chat-salgsgruppen for at diskutere og underskrive ICE Chat-datatjenesteaftalen, som du kan få på [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf). Denne aftale er mellem ICE Chat og din organisation og involverer ikke Microsoft. Når du har konfigureret et ICE Chat SFTP-websted i Trin 2, leverer ICE Chat FTP-legitimationsoplysningerne direkte til din organisation. Derefter skal du angive disse legitimationsoplysninger til Microsoft, når du konfigurerer connectoren i Trin 3.

- Du skal konfigurere et ICE Chat SFTP-websted, før du opretter connectoren i trin 3. Efter at have arbejdet med ICE Chat for at oprette SFTP-webstedet, uploades data fra ICE Chat til SFTP-webstedet hver dag. Den connector, du opretter i trin 3, opretter forbindelse til dette SFTP-websted og overfører chatdataene til Microsoft 365 postkasser. SFTP krypterer også DE ICE Chat-data, der sendes til postkasser under overførselsprocessen.

- Hvis du vil konfigurere en ICE Chat-connector, skal du bruge nøgler og adgangsudtryk til Pretty Good Privacy (PGP) og Secure Shell (SSH). Disse nøgler bruges til at konfigurere ICE Chat SFTP-webstedet og bruges af connectoren til at oprette forbindelse til ICE Chat SFTP-webstedet for at importere data til Microsoft 365. PGP-nøglen bruges til at konfigurere krypteringen af data, der overføres fra ICE Chat SFTP-webstedet, til Microsoft 365. SSH-nøglen bruges til at konfigurere Secure Shell for at aktivere et sikkert fjernlogon, når connectoren opretter forbindelse til ICE Chat SFTP-webstedet.

  Når du konfigurerer en connector, har du mulighed for at bruge offentlige nøgler og nøgleadgangsudtryk fra Microsoft, eller du kan bruge dine egne private nøgler og adgangsudtryk. Vi anbefaler, at du bruger de offentlige nøgler, der leveres af Microsoft. Men hvis din organisation allerede har konfigureret et ICE Chat SFTP-websted ved hjælp af private nøgler, kan du oprette en connector ved hjælp af de samme private nøgler.

- ICE Chat-connectoren kan importere i alt 200.000 varer på én dag. Hvis der er mere end 200.000 elementer på SFTP-webstedet, importeres ingen af disse elementer til Microsoft 365.

- Den administrator, der opretter ICE Chat-connectoren i trin 3 (og som downloader de offentlige nøgler og IP-adressen i trin 1), skal tildeles rollen Data Connector-administrator. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurer en connector ved hjælp af offentlige nøgler

Trinnene i dette afsnit viser, hvordan du konfigurerer en ICE Chat-connector ved hjælp af de offentlige nøgler til PGP (Pretty Good Privacy) og Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>Trin 1: Hent offentlige PGP- og SSH-nøgler

Det første trin er at få en kopi af de offentlige nøgler til Pretty Good Privacy (PGP) og Secure Shell (SSH). Du kan bruge disse nøgler i trin 2 til at konfigurere ICE Chat SFTP-webstedet, så connectoren (som du opretter i trin 3) kan oprette forbindelse til SFTP-webstedet og overføre ICE Chat-dataene til Microsoft 365 postkasser. Du får også en IP-adresse i dette trin, som du bruger, når du konfigurerer ICE Chat SFTP-webstedet.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **ICE Chat**.

3. Klik på **Tilføj connector** på siden **ICE Chat**.

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. Klik på **Jeg vil bruge offentlige PGP- og SSH-nøgler fra Microsoft** på siden **Tilføj legitimationsoplysninger til indholdskilde**.

   ![Vælg indstillingen for at bruge offentlige nøgler.](../media/ICEChatPublicKeysOption.png)

6. Under trin 1 skal du klikke på linkene **Download SSH,** **Download PGP** og **Download IP-adresse** for at gemme en kopi af hver fil på din lokale computer.

   ![Links til download af offentlige nøgler og IP-adresse.](../media/ICEChatPublicKeyDownloadLinks.png)

   Disse filer indeholder følgende elementer, der bruges til at konfigurere ICE Chat SFTP-webstedet i trin 2:

   - Offentlig PGP-nøgle: Denne nøgle bruges til at konfigurere kryptering af data, der overføres fra ICE Chat SFTP-webstedet til Microsoft 365.

   - Offentlig SSH-nøgle: Denne nøgle bruges til at konfigurere Secure SSH til at aktivere et sikkert fjernlogon, når connectoren opretter forbindelse til ICE Chat SFTP-webstedet.

   - IP-adresse: ICE Chat SFTP-webstedet er konfigureret til kun at acceptere en forbindelsesanmodning fra denne IP-adresse, som bruges af ice Chat-connectoren, som du opretter i Trin 3.

7. Klik på **Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 3 for at oprette connectoren.

### <a name="step-2-configure-the-ice-chat-sftp-site"></a>Trin 2: Konfigurer SFTP-webstedet til ICE Chat

Det næste trin er at bruge de offentlige PGP- og SSH-nøgler og den IP-adresse, du fik i trin 1, til at konfigurere PGP-kryptering og SSH-godkendelse for ICE Chat SFTP-webstedet. Dette gør det muligt for den ICE Chat-connector, du opretter i Trin 3, at oprette forbindelse til ICE Chat SFTP-webstedet og overføre ICE Chat-data til Microsoft 365. Du skal arbejde med ICE Chat-kundesupport for at konfigurere din ICE Chat SFTP-side.

### <a name="step-3-create-an-ice-chat-connector"></a>Trin 3: Opret en ICE Chat-connector

Det sidste trin er at oprette en ICE Chat-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til ICE Chat SFTP-webstedet og overføre chatbeskeder til de tilsvarende brugerpostkasser i Microsoft 365.

1. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **ICE Chat**.

3. Klik på **Tilføj connector** på siden **ICE Chat**.

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på **Jeg vil bruge offentlige PGP- og SSH-nøgler**.

6. Angiv de nødvendige oplysninger i følgende felter under Trin 3, og klik derefter på **Valider forbindelse**.

   - **Firmakode:** Id'et for din organisation, der bruges som brugernavn for ICE Chat SFTP-webstedet.

   - **Adgangskode:** Adgangskoden til dit ICE Chat SFTP-websted.

   - **URL-adresse til SFTP:** URL-adressen til ICE Chat SFTP-webstedet (f.eks. `sftp.theice.com`). Du kan også bruge en IP-adresse til denne værdi.

   - **SFTP-port:** Portnummeret for ICE Chat SFTP-webstedet. Connectoren bruger denne port til at oprette forbindelse til SFTP-webstedet.

7. Når forbindelsen er valideret, skal du klikke på **Næste**.

8. Angiv de brugere, der skal importeres data for, på siden **Definer bruger** .

     - **Alle brugere i din organisation**. Vælg denne indstilling for at importere data for alle brugere.

     - **Kun brugere, der er i strid med procesførelse**. Vælg denne indstilling, hvis du kun vil importere data for brugere, hvis postkasser er sat i strid med procesførelse. Denne indstilling importerer data til brugerpostkasser, hvor egenskaben LitigationHoldEnabled er angivet til Sand. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](create-a-litigation-hold.md).

9. På siden **Knyt eksterne brugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov. Du kan downloade en kopi af CSV-filen til brugertilknytning på denne side. Du kan føje brugertilknytningerne til filen og derefter uploade den.

   > [!NOTE]
   > Som tidligere forklaret indeholder CSV-filen til den brugerdefinerede tilknytningsfil ICE Chat midt og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers ICE Chat midt i, importerer connectoren elementet til postkasserne for de brugere, der er angivet i egenskaberne *SenderEmail* og *RecipientEmail* for chatelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger ved enten automatisk eller brugerdefineret brugertilknytning, importeres elementet ikke.

10. Klik på **Næste**, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette connectoren.

11. Gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurer en connector ved hjælp af private nøgler

Trinnene i dette afsnit viser, hvordan du konfigurerer en ICE Chat-connector ved hjælp af private PGP- og SSH-nøgler. Denne indstilling for connectorkonfiguration er beregnet til organisationer, der allerede har konfigureret et ICE Chat SFTP-websted ved hjælp af private nøgler.

### <a name="step-1-obtain-an-ip-address-to-configure-the-ice-chat-sftp-site"></a>Trin 1: Få en IP-adresse for at konfigurere SFTP-webstedet til ICE Chat

Hvis din organisation har brugt private nøgler til PGP og SSH til at oprette et ICE Chat SFTP-websted, skal du hente en IP-adresse og give den til ICE Chat-kundesupport. ICE Chat SFTP-webstedet skal være konfigureret til at acceptere forbindelsesanmodninger fra denne IP-adresse. Den samme IP-adresse bruges af ICE Chat-connectoren til at oprette forbindelse til SFTP-webstedet og overføre ICE Chat-data til Microsoft 365.

Sådan henter du IP-adressen:

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **ICE Chat**.

3. På siden **med beskrivelsen af ICE Chat-produktet** skal du klikke på **Tilføj connector**

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på **Jeg vil bruge private PGP- og SSH-nøgler**.

   ![Vælg indstillingen for at bruge private nøgler.](../media/ICEChatPrivateKeysOption.png)

6. Under trin 1 skal du klikke på **Download IP-adresse** for at gemme en kopi af IP-adressefilen på din lokale computer.

   ![Download IP-adressen.](../media/ICEChatConnectorIPAddress.png)

7. Klik på **Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 2 for at oprette connectoren.

Du skal arbejde med ICE Chat-kundesupport for at konfigurere dit ICE Chat SFTP-websted for at acceptere forbindelsesanmodninger fra denne IP-adresse.

### <a name="step-2-create-an-ice-chat-connector"></a>Trin 2: Opret en ICE Chat-connector

Når dit ICE Chat SFTP-websted er konfigureret, er det næste trin at oprette en ICE Chat-connector på overholdelsesportalen. Connectoren bruger de oplysninger, du angiver, til at oprette forbindelse til ICE Chat SFTP-webstedet og overføre mailmeddelelser til de tilsvarende brugerpostkasser i Microsoft 365. Hvis du vil fuldføre dette trin, skal du sørge for at have kopier af de samme private nøgler og adgangsudtryk, som du brugte til at konfigurere dit ICE Chat SFTP-websted.

1. Gå til , <https://compliance.microsoft.com> og klik på **Dataconnectors** i venstre navigationsrude.

2. Klik på **Vis** på siden **Dataconnectors** under **ICE Chat**.

3. På siden **med beskrivelsen af ICE Chat-produktet** skal du klikke på **Tilføj connector**

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på **Jeg vil bruge private PGP- og SSH-nøgler**.

6. Angiv de nødvendige oplysninger i følgende felter under Trin 3, og klik derefter på **Valider forbindelse**.

      - **Navn:** Navnet på connectoren. Det skal være entydigt i din organisation.

      - **Firmakode:** Det id for din organisation, der bruges som brugernavn for ICE Chat SFTP-webstedet.

      - **Adgangskode:** Adgangskoden til din organisations ICE Chat SFTP-websted.

      - **URL-adresse til SFTP:** URL-adressen til ICE Chat SFTP-webstedet (f.eks. `sftp.theice.com`). Du kan også bruge en IP-adresse til denne værdi.

      - **SFTP-port:** Portnummeret for ICE Chat SFTP-webstedet. Connectoren bruger denne port til at oprette forbindelse til SFTP-webstedet.

      - **Privat PGP-nøgle:** Den private PGP-nøgle til ICE Chat SFTP-webstedet. Sørg for at inkludere hele den private nøgleværdi, herunder start- og slutlinjerne for nøgleblokken.

      - **Adgangsudtryk til PGP-nøgle:** Adgangsudtrykket for den private PGP-nøgle.

      - **Privat SSH-nøgle:** Den private SSH-nøgle til ICE Chat SFTP-webstedet. Sørg for at inkludere hele den private nøgleværdi, herunder start- og slutlinjerne for nøgleblokken.

      - **Adgangsudtryk til SSH-nøgle:** Adgangsudtrykket for den private SSH-nøgle.

7. Når forbindelsen er valideret, skal du klikke på **Næste**.

8. Angiv de brugere, der skal importeres data for, på siden **Definer bruger** .

     - **Alle brugere i din organisation**. Vælg denne indstilling for at importere data for alle brugere.

     - **Kun brugere, der er i strid med procesførelse**. Vælg denne indstilling, hvis du kun vil importere data for brugere, hvis postkasser er sat i strid med procesførelse. Denne indstilling importerer data til brugerpostkasser, hvor egenskaben LitigationHoldEnabled er angivet til Sand. Du kan få flere oplysninger under [Opret en procesførelsesventeposition](create-a-litigation-hold.md).

9. På siden **Map ICE Chat-brugere til Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov.

   > [!NOTE]
   > Som tidligere forklaret indeholder CSV-filen til den brugerdefinerede tilknytningsfil ICE Chat midt og den tilsvarende Microsoft 365 postkasseadresse for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning, vil connectoren først se på den brugerdefinerede tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365 bruger, der svarer til en brugers ICE Chat midt i, importerer connectoren elementet til postkasserne for de brugere, der er angivet i egenskaberne *SenderEmail* og *RecipientEmail* for chatelementet. Hvis connectoren ikke finder en gyldig Microsoft 365 bruger ved enten automatisk eller brugerdefineret brugertilknytning, importeres elementet ikke.

10. Klik på **Næste**, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette connectoren.

11. Gå til siden **Dataconnectors** for at se status for importprocessen for den nye connector. Klik på connectoren for at få vist pop op-siden, der indeholder oplysninger om connectoren.
