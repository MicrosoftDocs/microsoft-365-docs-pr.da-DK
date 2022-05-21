---
title: Send mailmeddelelser, og vis politiktip til DLP-politikker
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleNotifyUser
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan du føjer et politiktip til en DLP-politik (forebyggelse af datatab) for at give en bruger besked om, at vedkommende arbejder med indhold, der er i konflikt med en DLP-politik.
ms.openlocfilehash: ce6665227b62ea5937229696fa65b69e7cfb894a
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623227"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>Send mailmeddelelser, og vis politiktip til DLP-politikker

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge en DLP-politik (forebyggelse af datatab) Microsoft Purview til at identificere, overvåge og beskytte følsomme oplysninger på tværs af Office 365. Du vil gerne have, at personer i din organisation, der arbejder med disse følsomme oplysninger, forbliver kompatible med dine DLP-politikker, men du vil ikke forhindre dem unødvendigt i at få deres arbejde fra hånden. Det er her, mailmeddelelser og politiktips kan hjælpe.

![Meddelelseslinjen viser politiktip i Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Når du opretter en DLP-politik, kan du konfigurere brugermeddelelserne til:

- Send en mail til de personer, du vælger, som beskriver problemet.

- Vis et politiktip til indhold, der er i konflikt med DLP-politikken:

  - I forbindelse med mail i Outlook på internettet og Outlook 2013 og nyere vises politiktippen øverst i en meddelelse over modtagerne, mens meddelelsen oprettes.

  - For dokumenter på en OneDrive for Business konto eller SharePoint Online-websted er politiktippen angivet med et advarselsikon, der vises på elementet. Hvis du vil have vist flere oplysninger, kan du vælge et element og derefter vælge ikon for ruden **Oplysninger**![.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) i øverste højre hjørne af siden for at åbne detaljeruden.

  - I forbindelse med Excel, PowerPoint og Word-dokumenter, der er gemt på et OneDrive for Business websted eller SharePoint Online-websted, der er inkluderet i DLP-politikken, vises politiktip på meddelelseslinjen og Backstage-visningen (**oplysninger** i menuen \>**Filer**).

## <a name="add-user-notifications-to-a-dlp-policy"></a>Føj brugermeddelelser til en DLP-politik

Når du opretter en DLP-politik, kan du aktivere **brugermeddelelser**. Når brugermeddelelser er aktiveret, sender Microsoft 365 både mailmeddelelser og politiktips. Du kan tilpasse, hvem meddelelsesmails sendes til, mailteksten og teksten til politiktip.

1. Gå til [https://(https://compliance.microsoft.com/permissions](https://(https://compliance.microsoft.com/permissions).

2. Log på med din arbejds- eller skolekonto.

3. I den Microsoft Purview-compliance-portal \> venstre navigationspolitik \> **Politik til** \> **forebyggelse af** \> datatab **+ Opret en politik**.

    ![Opret en politikknap.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)

4. Vælg den DLP-politikskabelon, der beskytter de typer følsomme oplysninger, du vil beskytte \> **Næste**.

    Hvis du vil starte med en tom skabelon, skal du vælge **Brugerdefineret** \> **politik** \> **Næste**.

5. Navngiv politikken \> **Næste**.

6. Benyt en af følgende fremgangsmåder for at vælge de placeringer, som DLP-politikken skal beskytte:

   - Vælg **Alle placeringer i Office 365** \> **Næste**.

   - Vælg **Lad mig vælge bestemte placeringer** \> **Næste**.

   Hvis du vil medtage eller udelade en hel placering, f.eks. alle Exchange mail eller alle OneDrive konti, skal du slå **Status** for den pågældende placering til eller fra.

   Hvis du kun vil medtage bestemte SharePoint websteder eller OneDrive konti, skal du skifte **Status** til til og derefter klikke på linkene under **Medtag** for at vælge bestemte websteder eller konti.

7. Vælg **Brug avancerede indstillinger** \> **Næste**.

8. Vælg **+ Ny regel**.

9. Skift status til under **Brugermeddelelser** i regeleditoren.

    ![Afsnittet Brugermeddelelser i regeleditoren.](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Meddelelsesmails sendes ubeskyttet.

## <a name="options-for-configuring-email-notifications"></a>Indstillinger for konfiguration af mailmeddelelser

For hver regel i en DLP-politik kan du:

- Send meddelelsen til de personer, du vælger. Disse personer kan omfatte ejeren af indholdet, den person, der senest har ændret indholdet, ejeren af det websted, hvor indholdet er gemt, eller en bestemt bruger.

- Tilpas den tekst, der er inkluderet i meddelelsen, ved hjælp af HTML eller tokens. Se afsnittet nedenfor for at få flere oplysninger.

> [!NOTE]
> Mailmeddelelser kan kun sendes til individuelle modtagere – ikke grupper eller distributionslister. Det er kun nyt indhold, der udløser en mailmeddelelse. Redigering af eksisterende indhold udløser politiktip, men ikke en mailmeddelelse.

![Indstillinger for mailbeskeder.](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)

### <a name="default-email-notification"></a>Standardmeddelelse via mail

Meddelelser har en emnelinje, der starter med den udførte handling, f.eks. "Meddelelse", "Meddelelse blokeret" for mail eller "Adgang blokeret" for dokumenter. Hvis meddelelsen handler om et dokument, indeholder meddelelsesteksten et link, der fører dig til det websted, hvor dokumentet er gemt, og åbner politiktip til dokumentet, hvor du kan løse eventuelle problemer (se afsnittet nedenfor om politiktip). Hvis meddelelsen handler om en meddelelse, inkluderer meddelelsen den meddelelse, der svarer til en DLP-politik, som en vedhæftet fil som en vedhæftet fil.

![Meddelelse.](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)

Meddelelser viser som standard tekst, der ligner følgende, for et element på et websted. Meddelelsesteksten konfigureres separat for hver regel, så den tekst, der vises, varierer, afhængigt af hvilken regel der matches.

|Hvis DLP-politikreglen gør dette...|Derefter står der følgende i standardmeddelelsen for SharePoint eller OneDrive for Business dokumenter...|Derefter står der følgende i standardmeddelelsen for Outlook meddelelser...|
|---|---|---|
|Sender en meddelelse, men tillader ikke tilsidesættelse|Dette element er i konflikt med en politik i din organisation.|Din mail er i konflikt med en politik i din organisation.|
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse|Dette element er i konflikt med en politik i din organisation. Hvis du ikke løser denne konflikt, kan adgangen til denne fil blive blokeret.|Din mail er i konflikt med en politik i din organisation. Meddelelsen blev ikke leveret til alle modtagere.|
|Blokerer adgang og sender en meddelelse|Dette element er i konflikt med en politik i din organisation. Adgang til dette element er blokeret for alle undtagen ejeren, den sidste ændringsadministrator og den primære administrator af gruppen af websteder.|Din mail er i konflikt med en politik i din organisation. Meddelelsen blev ikke leveret til alle modtagere.|

### <a name="custom-email-notification"></a>Brugerdefineret mailmeddelelse

Du kan oprette en brugerdefineret mailmeddelelse i stedet for at sende standardmeddelelsen via mail til dine slutbrugere eller administratorer. Den brugerdefinerede mailmeddelelse understøtter HTML og har en grænse på 5.000 tegn. Du kan bruge HTML til at inkludere billeder, formatering og anden branding i meddelelsen.

Du kan også bruge følgende tokens til at tilpasse mailmeddelelsen. Disse tokens er variabler, der erstattes af specifikke oplysninger i meddelelsen, der sendes.

|Token|Beskrivelse|
|---|---|
|%%AppliedActions%%|De handlinger, der er anvendt på indholdet.|
|%%ContentURL%%|URL-adressen til dokumentet på SharePoint Online-webstedet eller OneDrive for Business-webstedet.|
|%%MatchedConditions%%|De betingelser, der blev matchet med indholdet. Brug dette token til at informere andre om mulige problemer med indholdet.|

![Meddelelse, der viser, hvor tokens vises.](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)

## <a name="options-for-configuring-policy-tips"></a>Indstillinger for konfiguration af politiktip

For hver regel i en DLP-politik kan du konfigurere politiktip til:

- Du skal blot give personen besked om, at indholdet er i konflikt med en DLP-politik, så vedkommende kan udføre handlinger for at løse konflikten. Du kan bruge standardteksten (se tabellerne nedenfor) eller angive brugerdefineret tekst om organisationens specifikke politikker.

- Tillad, at personen tilsidesætter DLP-politikken. Du kan eventuelt:

  - Kræv, at personen angiver en forretningsberettigelse for tilsidesættelse af politikken. Disse oplysninger logføres, og du kan se dem i DLP-rapporterne i sektionen **Rapporter** på portalen.

  - Tillad, at personen rapporterer en falsk positiv værdi, og tilsidesæt DLP-politikken. Disse oplysninger logføres også til rapportering, så du kan bruge falske positiver til at finjustere dine regler.

![Indstillinger for politiktip.](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)

Du kan f.eks. have anvendt en DLP-politik på OneDrive for Business websteder, der registrerer personidentificerbare oplysninger, og denne politik indeholder tre regler:

1. Første regel: Hvis der registreres færre end fem forekomster af disse følsomme oplysninger i et dokument, og dokumentet deles med personer i organisationen, viser handlingen **Send en meddelelse** et politiktip. I forbindelse med politiktips er ingen indstillinger for tilsidesættelse nødvendige, fordi denne regel ganske enkelt giver personer besked og ikke blokerer adgang.

2. Anden regel: Hvis der registreres mere end fem forekomster af disse følsomme oplysninger i et dokument, og dokumentet deles med personer i organisationen, begrænser handlingen **Bloker adgang til indhold** tilladelserne til filen, og handlingen **Send en meddelelse** giver personer mulighed for at tilsidesætte handlingerne i denne regel ved at angive en forretningsberettigelse. Organisationens virksomhed kræver nogle gange, at interne personer deler PII-data, og du ønsker ikke, at din DLP-politik blokerer for dette arbejde.

3. Tredje regel: Hvis der registreres mere end fem forekomster af disse følsomme oplysninger i et dokument, og dokumentet deles med personer uden for organisationen, begrænser handlingen **Bloker adgang til indhold** tilladelserne til filen, og handlingen **Send en meddelelse** tillader ikke, at personer tilsidesætter handlingerne i denne regel, fordi oplysningerne deles eksternt. Personer i din organisation må under ingen omstændigheder dele PII-data uden for organisationen.

### <a name="user-override-support"></a>Understøttelse af brugertilsidesættelse

Her er nogle fine punkter, hvor du kan forstå, hvordan du bruger et politiktip til at tilsidesætte en regel:

- Indstillingen til tilsidesættelse er pr. regel, og den tilsidesætter alle handlinger i reglen (undtagen afsendelse af en meddelelse, som ikke kan tilsidesættes).

- Det er muligt for indhold at matche flere regler i en DLP-politik, men det er kun politiktip fra den mest restriktive regel med højeste prioritet, der vises. Et politiktip fra en regel, der blokerer adgang til indhold, vises f.eks. via et politiktip fra en regel, der blot sender en meddelelse. Dette forhindrer folk i at se en overlappende række af politiktips.

- Hvis politiktips i den mest restriktive regel tillader, at andre tilsidesætter reglen, tilsidesætter tilsidesættelse af denne regel også andre regler, som indholdet matchede.

- Hvis Handlingen NotifyAllowOverride er angivet med WithoutJustification eller WithJustification eller FlasePositives, skal du kontrollere, at BlockAccess er angivet til sand, og at BlockAccessScope har den korrekte værdi. Ellers vises politiktip, men brugeren finder ikke en mulighed for at tilsidesætte mailen med begrundelse.

#### <a name="availability-of-override"></a>Tilgængelighed af tilsidesættelse

|Meddelelsesregel |Handlingen Giv besked/bloker  |Tilsidesæt tilgængelig  |Kræv justering  |
|---------|---------|---------|---------|
|Kun giv besked     |Advisér         |Nej         |Nej         |
|Notify + AllowOverride     |Advisér         |Nej         |Nej         |
|Notify + AllowOverride + False positive     |Advisér         |Nej         |Nej         |
|Notify + AllowOverride + With justification     |Advisér         |Nej         |Nej         |
|Notify + AllowOverride + False positive + Without justification    |Advisér         |Nej         |Nej         |
|Notify + AllowOverride + False positive + With justification     |Advisér         |Nej         |Nej         |
|Giv besked + blok     |Bloker         |Nej         |Nej         |
|Notify + Block + AllowOverride     |Bloker         |Ja         |Nej         |
|Notify + Block + AllowOverride + False positive     |Bloker         |Ja         |Nej         |
|Notify + Block + AllowOverride + With justification     |Bloker         |Ja         |Ja         |
|Notify + Block + AllowOverride + False positive + Without justification     |Bloker         |Ja         |Nej         |
|Notify + Block + AllowOverride + False positive + With justification     |Bloker         |Ja         |Ja         |


## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>Politiktips til OneDrive for Business websteder og SharePoint Online-websteder

Når et dokument på et OneDrive for Business websted eller SharePoint Online-websted stemmer overens med en regel i en DLP-politik, og denne regel bruger politiktip, viser politiktips specielle ikoner i dokumentet:

1. Hvis reglen sender en meddelelse om filen, vises advarselsikonet.

2. Hvis reglen blokerer adgangen til dokumentet, vises det blokerede ikon.

   ![Ikoner for politiktip til dokumenter på en OneDrive konto.](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)

Hvis du vil udføre en handling på et dokument, kan du vælge et element \> ved at vælge ikonet med ruden **Oplysninger**![.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) i øverste højre hjørne af siden for at åbne detaljeruden \> **Få vist politiktip**.

Politiktippen viser problemer med indholdet, og hvis politiktips er konfigureret med disse indstillinger, kan du vælge **Løs** og derefter **Tilsidesætte** politiktip eller **Rapportér** et falsk positivt.

![Ruden Oplysninger, der viser politiktip.](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)

![Politiktip med mulighed for at tilsidesætte.](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)

DLP-politikker synkroniseres til websteder, og indhold evalueres i forhold til dem med jævne mellemrum og asynkront, så der kan være en kort forsinkelse mellem den tid, du opretter DLP-politikken, og den tid, du begynder at se politiktips. Der kan være en lignende forsinkelse fra det tidspunkt, hvor du løser eller tilsidesætter et politiktip, til det tidspunkt, hvor ikonet på dokumentet på webstedet forsvinder.

### <a name="default-text-for-policy-tips-on-sites"></a>Standardtekst for politiktip på websteder

Politiktip viser som standard tekst, der ligner følgende, for et element på et websted. Meddelelsesteksten konfigureres separat for hver regel, så den tekst, der vises, varierer, afhængigt af hvilken regel der matches.

|Hvis DLP-politikreglen gør dette...|Så siger standardpolitiktip...|
|---|---|
|Sender en meddelelse, men tillader ikke tilsidesættelse|Dette element er i konflikt med en politik i din organisation.|
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse|Dette element er i konflikt med en politik i din organisation. Hvis du ikke løser denne konflikt, kan adgangen til denne fil blive blokeret.|
|Blokerer adgang og sender en meddelelse|Dette element er i konflikt med en politik i din organisation. Adgang til dette element er blokeret for alle undtagen ejeren, den sidste ændringsadministrator og den primære administrator af gruppen af websteder.|

### <a name="custom-text-for-policy-tips-on-sites"></a>Brugerdefineret tekst til politiktip på websteder

Du kan tilpasse teksten til politiktips separat fra mailmeddelelsen. I modsætning til brugerdefineret tekst til mailmeddelelser (se afsnittet ovenfor) accepterer brugerdefineret tekst til politiktip ikke HTML eller tokens. Brugerdefineret tekst til politiktip er i stedet kun almindelig tekst med en grænse på 256 tegn.

## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>Politiktips i Outlook på internettet og Outlook 2013 og nyere

Når du opretter en ny mail i Outlook på internettet og Outlook 2013 og nyere, får du vist et politiktip, hvis du tilføjer indhold, der stemmer overens med en regel i en DLP-politik, og denne regel bruger politiktip. Politiktip vises øverst i meddelelsen over modtagerne, mens meddelelsen sammensættes.

![Politiktip øverst i en meddelelse, der oprettes.](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)

Politiktip fungerer, uanset om de følsomme oplysninger vises i meddelelsens brødtekst, emnelinjen eller endda en vedhæftet meddelelse som vist her.

![Politiktip, der viser, at en vedhæftet fil er i konflikt med en DLP-politik.](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)

Hvis politiktips er konfigureret til at tillade tilsidesættelse, kan du vælge **Vis tilsidesættelse af**  \> detaljer \> angive en forretningsberettigelse eller rapportere en falsk positiv \> **tilsidesættelse**.

![Politiktip i meddelelse udvidet til at vise indstillingen Tilsidesæt.](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)

![Dialogboksen Med politiktip, hvor du kan tilsidesætte politiktip.](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)

Bemærk, at når du føjer følsomme oplysninger til en mail, kan der være ventetid mellem det tidspunkt, hvor de følsomme oplysninger tilføjes, og hvornår politiktip vises. Når mails krypteres med Microsoft Purview-meddelelseskryptering, og den politik, der bruges til at registrere dem, bruger politiktip til registrering af krypteringstilstand, vises ikke.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 og nyere understøtter kun visning af politiktips for nogle betingelser

I øjeblikket understøtter Outlook 2013 og nyere kun politiktips for disse betingelser:

- Indholdet indeholder
- Indholdet er delt

Bemærk, at undtagelser betragtes som betingelser, og alle disse betingelser fungerer i Outlook, hvor de matcher indhold og gennemtvinger beskyttende handlinger på indhold. Men visning af politiktip til brugere understøttes endnu ikke. Outlook understøtter heller ikke visning af politiktip til en DLP-politik, der anvendes på en dynamisk distributionsgruppe.

### <a name="policy-tips-in-the-exchange-admin-center-vs-the-microsoft-purview-compliance-portal"></a>Tip til politikker i Exchange Administration i forhold til portalen Microsoft Purview overholdelse

Politiktips kan enten fungere med DLP-politikker og regler for mailflow, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>, eller med DLP-politikker, der er oprettet i overholdelsesportalen, men ikke begge dele. Det skyldes, at disse politikker er gemt forskellige steder, men politiktip kan kun hentes fra en enkelt placering.

Hvis du har konfigureret politiktips i Exchange Administration, vises de politiktips, du konfigurerer på overholdelsesportalen, ikke for brugere i Outlook på internettet og Outlook 2013 og nyere, før du deaktiverer tipene i Exchange Administration. Dette sikrer, at dine aktuelle regler for Exchange mailflow (også kaldet transportregler) fortsat fungerer, indtil du vælger at skifte til overholdelsesportalen.

Bemærk, at selvom politiktips kun kan hentes fra en enkelt placering, sendes der altid mailmeddelelser, selvom du bruger DLP-politikker i både overholdelsesportalen og Exchange Administration.

### <a name="default-text-for-policy-tips-in-email"></a>Standardtekst for politiktip i mail

Politiktip viser som standard tekst, der ligner følgende for mail.

|Hvis DLP-politikreglen gør dette...|Så siger standardpolitiktip...|
|---|---|
|Sender en meddelelse, men tillader ikke tilsidesættelse|Din mail er i konflikt med en politik i din organisation.|
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse|Din mail er i konflikt med en politik i din organisation.|
|Blokerer adgang og sender en meddelelse|Din mail er i konflikt med en politik i din organisation.|

## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Politiktips i Excel, PowerPoint og Word

Når personer arbejder med følsomt indhold i skrivebordsversionerne af Excel, PowerPoint og Word, kan politiktips give dem besked i realtid om, at indholdet er i konflikt med en DLP-politik. Dette kræver, at:

- Det Office dokument er gemt på et OneDrive for Business websted eller på et SharePoint Online-websted.

- Webstedet er inkluderet i en DLP-politik, der er konfigureret til at bruge politiktip.

Office desktopprogrammer synkroniserer automatisk DLP-politikker direkte fra Office 365 og scanner derefter dine dokumenter for at sikre, at de ikke er i konflikt med dine DLP-politikker og viser politiktip i realtid.

> [!NOTE]
> Office desktopapps scanner dokumenter selv for at finde ud af, om tip til DLP-politikker skal vises. De viser ikke politiktips, som SharePoint onlinewebsteder eller OneDrive for Business websteder allerede har bestemt, skal vises i en fil. Derfor kan du muligvis ikke altid se et tip til en DLP-politik i de skrivebordsapps, du kan se på SharePoint Online-websteder eller på OneDrive for Business websteder. I modsætning hertil viser de Office programmer på internettet kun DLP-politiktips, som SharePoint onlinewebsteder eller OneDrive for Business websteder allerede har bestemt, skal vises.

Afhængigt af hvordan du konfigurerer politiktips i DLP-politikken, kan brugerne vælge blot at ignorere politiktips, tilsidesætte politikken med eller uden en forretningsberettigelse eller rapportere en falsk positiv.

Politiktip vises på meddelelseslinjen.

![Meddelelseslinjen viser politiktip i Excel 2016.](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Og politiktip vises også i Backstage-visningen (under fanen **Filer** ).

![Backstage viser politiktip i Excel 2016.](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)

Hvis politiktip i DLP-politikken er konfigureret med disse indstillinger, kan du vælge **Løs** for at **tilsidesætte** et politiktip eller **Rapportere** et falsk positivt.

![Indstillinger for politiktip i Backstage i Excel 2016.](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)

I hvert af disse Office desktopprogrammer kan folk vælge at deaktivere politiktips. Hvis indstillingen er slået fra, vises politiktip, der er enkle meddelelser, ikke på meddelelseslinjen eller Backstage-visningen (under fanen **Filer** ). Politiktips om blokering og tilsidesættelse vises dog stadig, og de modtager stadig mailmeddelelsen. Desuden fritager deaktivering af politiktip ikke dokumentet fra de DLP-politikker, der er anvendt på det.

### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>Standardtekst for politiktips i Excel 2016, PowerPoint 2016 og Word 2016

Politiktip viser som standard tekst, der ligner følgende, i Meddelelseslinje- og Backstage-visningen af et åbent dokument. Meddelelsesteksten konfigureres separat for hver regel, så den tekst, der vises, varierer, afhængigt af hvilken regel der matches.

|Hvis DLP-politikreglen gør dette...|Så siger standardpolitiktip...|
|---|---|
|Sender en meddelelse, men tillader ikke tilsidesættelse|Denne fil er i konflikt med en politik i din organisation. Gå til menuen **Filer** for at få flere oplysninger.|
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse|Denne fil er i konflikt med en politik i din organisation. Hvis du ikke løser denne konflikt, kan adgangen til denne fil blive blokeret. Gå til menuen **Filer** for at få flere oplysninger.|
|Blokerer adgang og sender en meddelelse|Denne fil er i konflikt med en politik i din organisation. Hvis du ikke løser denne konflikt, kan adgangen til denne fil blive blokeret. Gå til menuen **Filer** for at få flere oplysninger.|

### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Brugerdefineret tekst til politiktip i Excel, PowerPoint og Word

Du kan tilpasse teksten til politiktips separat fra mailmeddelelsen. I modsætning til brugerdefineret tekst til mailmeddelelser (se afsnittet ovenfor) accepterer brugerdefineret tekst til politiktip ikke HTML eller tokens. Brugerdefineret tekst til politiktip er i stedet kun almindelig tekst med en grænse på 256 tegn.

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
- [DLP-politikbetingelser, -undtagelser og -handlinger (prøveversion)](./dlp-microsoft-teams.md)
- [Opret en DLP-politik for at beskytte dokumenter med FCI eller andre egenskaber](protect-documents-that-have-fci-or-other-properties.md)
- [Hvad inkluderes i DLP-politikskabelonerne](what-the-dlp-policy-templates-include.md)
- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
