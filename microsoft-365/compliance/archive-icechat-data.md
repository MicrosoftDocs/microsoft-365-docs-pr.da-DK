---
title: Konfigurer en forbindelse til at arkivere ICE-chatdata
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
description: Administratorer kan konfigurere en forbindelse til at importere og arkivere data fra ICE-chatværktøjet i Microsoft 365. Dette giver dig mulighed for at arkivere data fra tredjepartsdatakilder i Microsoft 365, så du kan bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere organisationens tredjepartsdata.
ms.openlocfilehash: c29a39c8c398a0d8721931cbcb770aa18d0f3c4b
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568088"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>Konfigurer en forbindelse til at arkivere ICE-chatdata

Brug en indbygget forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere chatdata for finansielle tjenester fra ICE Chat-samarbejdsværktøjet. Når du har konfigureret en forbindelse, opretter den forbindelse til organisationens ICE Chat Secure FTP-websted (SFTP) én gang dagligt, konverterer indholdet af chatmeddelelser til et mailformat og importerer derefter disse elementer til postkasserne i Microsoft 365.

Når ICE-chatdata er gemt i brugerpostkasser, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks retslig tilbageholdelse, eDiscovery, arkivering, overvågning, overholdelse af kommunikation og Microsoft 365-opbevaringspolitikker til ICE-chatdata. Du kan f.eks. søge i ICE-chatmeddelelser ved hjælp af indholdssøgning eller knytte den postkasse, der indeholder ICE-chatdataene, til en medarbejder i en Advanced eDiscovery sag. Brug af en ICE-chatforbindelse til at importere og arkivere data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="overview-of-archiving-ice-chat-data"></a>Oversigt over arkivering af ICE-chatdata

Følgende oversigt beskriver processen med at bruge en forbindelse til at arkivere ICE-chatdata i Microsoft 365.

![ARBEJDSprocessen for arkivering af ICE-chat.](../media/ICEChatConnectorWorkflow.png)

1. Din organisation arbejder sammen med ICE-chat om at konfigurere et ICE-chatwebsted. Du kan også arbejde med ICE-chat for at konfigurere ICE-chat for at kopiere chatmeddelelser til din ICE-chatSFTP-websted.

2. Én gang i døgnet kopieres chatmeddelelser fra ICE-chat til din ICE-chatSFTP-websted.

3. DEN ICE-chatforbindelse, som du opretter i Microsoft 365 Overholdelsescenter, opretter forbindelse til ICE-chatwebstedet i SFTP hver dag og overfører chatmeddelelser fra de foregående 24 timer til et sikkert Azure Storage i Microsoft-skyen. Forbindelsen konverterer også indholdet af en chat til et mailformat.

4. Forbindelsen importerer chatmeddelelseselementer til postkasser for bestemte brugere. Der oprettes en ny mappe med navnet **ICE Chat** i brugerpostkasserne, og chatmeddelelseselementerne importeres til den pågældende mappe. Forbindelsen gør ved hjælp af værdien af *egenskaberne SenderEmail* *og RecipientEmail* . Hver chatmeddelelse indeholder disse egenskaber, som er udfyldt med mailadressen på afsenderen og hver modtager/deltager i chatmeddelelsen.

   Ud over automatisk brugertilknytning, der bruger værdierne fra egenskaben *SenderEmail* og *RecipientEmail* (hvilket betyder, at forbindelsen importerer en chatmeddelelse til afsenderens postkasse og postkasserne for hver modtager), kan du også definere brugerdefineret brugertilknytning ved at uploade en CSV-tilknytningsfil. Denne tilknytningsfil indeholder ICE Chat *ImId* og den tilsvarende Microsoft 365-postkasseadresse for hver bruger i organisationen. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytningsfil, vil forbindelsen først se på den brugerdefinerede tilknytningsfil for hvert chatelement. Hvis der ikke findes en gyldig Microsoft 365-brugerkonto, der svarer til en brugers ICE-chat-id, bruger forbindelsen egenskaberne *SenderEmail* og *RecipientEmail* for chatelementet til at importere elementet til chatdeltagernes postkasser. Hvis forbindelsen ikke finder en gyldig Microsoft 365-bruger i enten den brugerdefinerede tilknytningsfil eller egenskaberne *SenderEmail* og *RecipientEmail*, importeres elementet ikke.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Nogle af de implementeringstrin, der kræves for at arkivere ICE-chatdata, er eksterne Microsoft 365 og skal udføres, før du kan oprette forbindelsen i overholdelsescenteret.

- ICE-chat opkræver et gebyr for ekstern overholdelse. Din organisation skal kontakte den ICE-chatsalgsgruppe, der skal diskuteres, og signere serviceaftalen for ICE-chatdata, som du kan hente på [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf). Denne aftale er mellem ICE-chat og din organisation og involverer ikke Microsoft. Når du har konfigureret et ICE Chat SFTP-websted i trin 2, leverer ICE Chat FTP-legitimationsoplysningerne direkte til din organisation. Derefter skal du, som skal angive disse legitimationsoplysninger til Microsoft, når du konfigurerer forbindelsen i trin 3.

- Du skal konfigurere et ICE Chat SFTP-websted, før du opretter forbindelsen i trin 3. Når du har arbejdet med ICE-chat for at konfigurere SFTP-webstedet, uploades data fra ICE-chat til SFTP-webstedet hver dag. Den forbindelse, du opretter i trin 3, opretter forbindelse til dette SFTP-websted og overfører chatdataene til Microsoft 365 postkasser. SFTP krypterer også de ICE-chatdata, der sendes til postkasser under overførslen.

- Hvis du vil konfigurere en ICE-chatforbindelse, skal du bruge taster og tasteudskrifter for at opnå ret god beskyttelse af personlige oplysninger (PGP) og Secure Shell (SSH). Disse taster bruges til at konfigurere ICE Chat SFTP-webstedet og bruges af forbindelsen til at oprette forbindelse til ICE-chat SFTP-webstedet til at importere data til Microsoft 365. PGP-nøglen bruges til at konfigurere krypteringen af data, der overføres fra ICE-chat SFTP-webstedet til Microsoft 365. SSH-nøglen bruges til at konfigurere sikker shell til at aktivere en sikker ekstern logon, når forbindelsen opretter forbindelse til ICE-chat-SFTP-webstedet.

  Når du konfigurerer en forbindelse, har du mulighed for at bruge offentlige nøgler og nøgler, der leveres af Microsoft, eller du kan bruge dine egne private nøgler og adgangskode. Vi anbefaler, at du bruger de offentlige nøgler, der leveres af Microsoft. Men hvis din organisation allerede har konfigureret et ICE Chat SFTP-websted ved hjælp af private nøgler, kan du oprette en forbindelse ved hjælp af de samme private nøgler.

- ICE-chatforbindelse kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 elementer på SFTP-webstedet, importeres ingen af disse elementer til Microsoft 365.

- Den administrator, der opretter ICE-chatforbindelse i trin 3 (og som downloader de offentlige nøgler og IP-adressen i trin 1), skal have tildelt dataforbindelsesadministratorrollen. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Konfigurer en forbindelse ved hjælp af offentlige taster

Trinnene i dette afsnit viser, hvordan du konfigurerer en ICE-chatforbindelse ved hjælp af de offentlige taster for Pretty Good Privacy (PGP) og Secure Shell (SSH).

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>Trin 1: Hent offentlige PGP- og SSH-nøgler

Det første trin er at hente en kopi af de offentlige nøgler til Pretty Good Privacy (PGP) og Secure Shell (SSH). Du kan bruge disse taster i trin 2 til at konfigurere ICE-chat-SFTP-webstedet, så den forbindelse (som du opretter i trin 3) kan oprette forbindelse til SFTP-webstedet og overføre ICE-chatdata til Microsoft 365-postkasser. Du får også en IP-adresse i dette trin, som du bruger, når du konfigurerer ICE-chat-SFTP-webstedet.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. På siden **Dataforbindelser under** ICE **Chat skal du** klikke på **Vis**.

3. Klik på **Tilføj forbindelse** på siden **ICE-chat**.

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke på Jeg vil bruge offentlige **PGP- og SSH-nøgler, der leveres af Microsoft**.

   ![Vælg indstillingen for at bruge offentlige nøgler.](../media/ICEChatPublicKeysOption.png)

6. Under trin 1 skal du klikke på **Download SSH-tasten**, **Download PGP-nøgle** og **Download IP-adresselinks** for at gemme en kopi af hver fil på din lokale computer.

   ![Links til at downloade offentlige nøgler og IP-adresse.](../media/ICEChatPublicKeyDownloadLinks.png)

   Disse filer indeholder følgende elementer, der bruges til at konfigurere ICE Chat SFTP-webstedet i trin 2:

   - Offentlig PGP-nøgle: Denne nøgle bruges til at konfigurere krypteringen af data, der overføres fra ICE-chat-SFTP-webstedet til Microsoft 365.

   - Offentlig SSH-nøgle: Denne nøgle bruges til at konfigurere Secure SSH til at aktivere en sikker ekstern logon, når forbindelsen opretter forbindelse til ICE Chat SFTP-webstedet.

   - IP-adresse: ICE-chat-SFTP-webstedet er konfigureret til kun at acceptere en forbindelsesanmodning fra denne IP-adresse, som bruges af den ICE-chatforbindelse, som du opretter i trin 3.

7. Klik **på Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 3 for at oprette forbindelsen.

### <a name="step-2-configure-the-ice-chat-sftp-site"></a>Trin 2: Konfigurer ICE-chatwebstedet

Det næste trin er at bruge de offentlige PGP- og SSH-nøgler og den IP-adresse, du fik i trin 1, til at konfigurere PGP-kryptering og SSH-godkendelse til ICE Chat SFTP-webstedet. Det gør det muligt for den ICE-chatforbindelse, som du opretter i trin 3, at oprette forbindelse til ICE-chatwebstedet og overføre ICE-chatdata Microsoft 365. Du skal arbejde med ICE Chat-kundesupport for at konfigurere dit ICE Chat SFTP-websted.

### <a name="step-3-create-an-ice-chat-connector"></a>Trin 3: Opret en ICE-chatforbindelse

Det sidste trin er at oprette en ICE-chatforbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til ICE Chat SFTP-webstedet og overføre chatmeddelelser til de tilsvarende postkassefelter for brugere Microsoft 365.

1. Gå til og [https://compliance.microsoft.com](https://compliance.microsoft.com) klik **på Dataforbindelser** i venstre navigationslinje.

2. På siden **Dataforbindelser under** ICE **Chat skal du** klikke på **Vis**.

3. Klik på **Tilføj forbindelse** på siden **ICE-chat**.

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke **på Jeg vil bruge offentlige PGP- og SSH-nøgler**.

6. Under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Valider forbindelse**.

   - **Firmakode:** Id'et for din organisation, der bruges som brugernavnet for ICE Chat SFTP-webstedet.

   - **Adgangskode:** Adgangskoden til dit ICE Chat SFTP-websted.

   - **SFTP-URL-ADRESSE:** URL-adressen til ICE-chatwebstedet (f.eks. `sftp.theice.com`). Du kan også bruge en IP-adresse til denne værdi.

   - **SFTP-port:** Portnummeret for ICE Chat SFTP-webstedet. Forbindelsen bruger denne port til at oprette forbindelse til SFTP-webstedet.

7. Klik på Næste, når forbindelsen er blevet **valideret**.

8. På siden **Definer bruger** skal du angive de brugere, der skal importere data til.

     - **Alle brugere i organisationen**. Markér denne indstilling for at importere data for alle brugere.

     - **Kun brugere, der er i retslig venteposition**. Markér denne indstilling for kun at importere data for brugere, hvis postkasser er placeret i retslig venteposition. Denne indstilling importerer data til brugerpostkasser, der har egenskaben LitigationHoldEnabled angivet til Sand. Få mere at vide under [Opret en retslig venteposition](create-a-litigation-hold.md).

9. På siden **Tilknyt eksterne brugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov. Du kan downloade en kopi af CSV-filen med brugertilknytning på denne side. Du kan føje brugertilknytninger til filen og derefter overføre den.

   > [!NOTE]
   > Som tidligere nævnt indeholder den brugerdefinerede tilknytningsfil CSV-fil ICE-chat imidt og Microsoft 365-postkasseadressen for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning for hvert chatelement, kigger forbindelsen først på brugerdefineret tilknytningsfil. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers ICE-chat imidt, importerer forbindelsen elementet til postkasserne for de brugere, der er angivet i egenskaberne *SenderEmail* og *RecipientEmail* for chatelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365 bruger ved enten automatisk eller brugerdefineret brugertilknytning, importeres elementet ikke.

10. Klik **på** Næste, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette forbindelsen.

11. Gå til siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse.

## <a name="set-up-a-connector-using-private-keys"></a>Konfigurer en forbindelse ved hjælp af private taster

Trinnene i dette afsnit viser, hvordan du konfigurerer en ICE-chatforbindelse ved hjælp af private PGP- og SSH-nøgler. Denne indstilling for konfiguration af forbindelse er beregnet til organisationer, der allerede har konfigureret et ICE Chat SFTP-websted ved hjælp af private nøgler.

### <a name="step-1-obtain-an-ip-address-to-configure-the-ice-chat-sftp-site"></a>Trin 1: Hent en IP-adresse for at konfigurere ICE Chat SFTP-webstedet

Hvis din organisation har brugt private PGP- og SSH-nøgler til at konfigurere et ICE-chat SFTP-websted, skal du hente en IP-adresse og levere den til ICE Chat-kundesupport. ICE-chat SFTP-webstedet skal konfigureres til at acceptere forbindelsesanmodninger fra denne IP-adresse. Den samme IP-adresse bruges af ICE-chatforbindelse til at oprette forbindelse til SFTP-webstedet og overføre ICE-chatdata Microsoft 365.

Sådan får du IP-adressen:

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. På siden **Dataforbindelser under** ICE **Chat skal du** klikke på **Vis**.

3. Klik på **Tilføj forbindelse på** siden produktbeskrivelse for **ICE-chat**

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke **på Jeg vil bruge private PGP- og SSH-nøgler**.

   ![Vælg indstillingen for at bruge private nøgler.](../media/ICEChatPrivateKeysOption.png)

6. Under trin 1 skal du klikke **på Download IP-adresse** for at gemme en kopi af IP-adressefilen på din lokale computer.

   ![Download IP-adressen.](../media/ICEChatConnectorIPAddress.png)

7. Klik **på Annuller** for at lukke guiden. Du vender tilbage til denne guide i trin 2 for at oprette forbindelsen.

Du skal arbejde med ICE Chat-kundesupport for at konfigurere dit ICE Chat SFTP-websted til at acceptere forbindelsesanmodninger fra denne IP-adresse.

### <a name="step-2-create-an-ice-chat-connector"></a>Trin 2: Opret en ICE-chatforbindelse

Når dit ICE Chat SFTP-websted er konfigureret, er næste trin at oprette en ICE-chatforbindelse i Microsoft 365 Overholdelsescenter. Forbindelsen anvender de oplysninger, du angiver, til at oprette forbindelse til ICE Chat SFTP-webstedet og overføre mails til de tilsvarende postkassefelter i Microsoft 365. For at fuldføre dette trin skal du sørge for at have kopier af de samme private nøgler og vigtige adgangsord, som du brugte til at konfigurere dit ICE Chat SFTP-websted.

1. Gå til og <https://compliance.microsoft.com> klik **på Dataforbindelser** i venstre navigationslinje.

2. På siden **Dataforbindelser under** ICE **Chat skal du** klikke på **Vis**.

3. Klik på **Tilføj forbindelse på** siden produktbeskrivelse for **ICE-chat**

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for indholdskilde** skal du klikke **på Jeg vil bruge private PGP- og SSH-nøgler**.

6. Under Trin 3 skal du angive de nødvendige oplysninger i følgende felter og derefter klikke på **Valider forbindelse**.

      - **Navn:** Navnet på forbindelsen. Det skal være entydigt i din organisation.

      - **Firmakode:** Id'et for din organisation, der bruges som brugernavnet for ICE Chat SFTP-webstedet.

      - **Adgangskode:** Adgangskoden til din organisations ICE Chat SFTP-websted.

      - **SFTP-URL-ADRESSE:** URL-adressen til ICE-chatwebstedet (f.eks. `sftp.theice.com`). Du kan også bruge en IP-adresse til denne værdi.

      - **SFTP-port:** Portnummeret for ICE Chat SFTP-webstedet. Forbindelsen bruger denne port til at oprette forbindelse til SFTP-webstedet.

      - **Privat PGP-nøgle:** Den private PGP-nøgle til ICE Chat SFTP-webstedet. Sørg for at medtage hele den private nøgleværdi, herunder de første og sidste linjer i nøgleblokken.

      - **PGP-nøgle-adgangskode:** Adgangsordet for den private PGP-nøgle.

      - **Privat SSH-nøgle:** Den private SSH-nøgle til ICE Chat SFTP-webstedet. Sørg for at medtage hele den private nøgleværdi, herunder de første og sidste linjer i nøgleblokken.

      - **SSH-tasten adgangskode:** Adgangsordet for den private SSH-nøgle.

7. Klik på Næste, når forbindelsen er blevet **valideret**.

8. På siden **Definer bruger** skal du angive de brugere, der skal importere data til.

     - **Alle brugere i organisationen**. Markér denne indstilling for at importere data for alle brugere.

     - **Kun brugere, der er i retslig venteposition**. Markér denne indstilling for kun at importere data for brugere, hvis postkasser er placeret i retslig venteposition. Denne indstilling importerer data til brugerpostkasser, der har egenskaben LitigationHoldEnabled angivet til Sand. Få mere at vide under [Opret en retslig venteposition](create-a-litigation-hold.md).

9. På siden **Tilknyt ICE-chatbrugere Microsoft 365 brugere** skal du aktivere automatisk brugertilknytning og angive brugerdefineret brugertilknytning efter behov.

   > [!NOTE]
   > Som tidligere nævnt indeholder den brugerdefinerede tilknytningsfil CSV-fil ICE-chat imidt og Microsoft 365-postkasseadressen for hver bruger. Hvis du aktiverer automatisk brugertilknytning og angiver en brugerdefineret tilknytning for hvert chatelement, kigger forbindelsen først på brugerdefineret tilknytningsfil. Hvis der ikke findes en gyldig Microsoft 365-bruger, der svarer til en brugers ICE-chat imidt, importerer forbindelsen elementet til postkasserne for de brugere, der er angivet i egenskaberne *SenderEmail* og *RecipientEmail* for chatelementet. Hvis forbindelsen ikke finder en gyldig Microsoft 365 bruger ved enten automatisk eller brugerdefineret brugertilknytning, importeres elementet ikke.

10. Klik **på** Næste, gennemse indstillingerne, og klik derefter på **Udfør** for at oprette forbindelsen.

11. Gå til siden **Dataforbindelser for** at se status for importprocessen for den nye forbindelse. Klik på forbindelsen for at få vist pop op-siden, der indeholder oplysninger om forbindelsen.
