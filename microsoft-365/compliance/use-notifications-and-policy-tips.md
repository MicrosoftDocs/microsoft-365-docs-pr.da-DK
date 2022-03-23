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
description: Få mere at vide om, hvordan du føjer et politiktip til en politik til forebyggelse af datatab (DLP) for at underrette en bruger om, at de arbejder med indhold, der er i konflikt med en DLP-politik.
ms.openlocfilehash: 793ae9410ff40d989fffa4dfeae457ff0e61e392
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587750"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>Send mailmeddelelser, og vis politiktip til DLP-politikker

Du kan bruge en politik til forebyggelse af datatab (DLP) til at identificere, overvåge og beskytte følsomme oplysninger på tværs Office 365. Du ønsker, at de personer i din organisation, som arbejder med disse følsomme oplysninger, skal forblive i overensstemmelse med dine DLP-politikker, men du ønsker ikke at hindre dem unødigt i at få arbejdet udført. Det er her, mailbeskeder og politiktip kan hjælpe.

![Meddelelseslinjen viser politiktip i Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Når du opretter en DLP-politik i Overholdelsescenter, kan du konfigurere brugermeddelelser til:

- Send en mail til de personer, du vælger, som beskriver problemet.

- Vis et politiktip for indhold, der er i konflikt med DLP-politikken:

  - For mails i Outlook på internettet og Outlook 2013 og nyere vises politiktip øverst i en meddelelse over modtagerne, mens meddelelsen er ved at blive skrevet.

  - For dokumenter på en OneDrive for Business-konto eller SharePoint Online-websted er politiktippen angivet med et advarselsikon, der vises på elementet. Hvis du vil have vist flere oplysninger, kan du vælge et element og derefter **vælge ruden** ![Oplysninger.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) i øverste højre hjørne på siden for at åbne detaljeruden.

  - For Excel-, PowerPoint- og Word-dokumenter, der er gemt på et OneDrive for Business-websted eller SharePoint Online-websted, som er inkluderet i DLP-politikken, vises politiktip på meddelelseslinjen og Backstage-visningen (**Oplysninger** om menuen **Filer**\>).

## <a name="add-user-notifications-to-a-dlp-policy"></a>Føj brugerbeskeder til en DLP-politik

Når du opretter en DLP-politik, kan du aktivere **brugermeddelelser**. Når brugerbeskeder er aktiveret, Microsoft 365 sende både mailbeskeder og politiktip. Du kan tilpasse, hvem der skal sendes mails til, mailteksten og politiktipteksten.

1. Gå til [https://(https://compliance.microsoft.com/permissions](https://(https://compliance.microsoft.com/permissions).

2. Log på med din arbejds- eller skolekonto. Du er nu i Security &amp; Compliance Center.

3. I Security Compliance &amp; Center venstre \> navigation Politik \> **for forebyggelse af** \> **datatab** \> **+ Opret en politik**.

    ![Knappen Opret en politik.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)

4. Vælg skabelonen DLP-politik, der beskytter de typer af følsomme oplysninger, du skal bruge \> **Næste**.

    Vælg Brugerdefineret politik Næste for at starte **med en** \> **tom** \> **skabelon**.

5. Navngive politikken \> **Næste**.

6. For at vælge de placeringer, du vil beskytte DLP-politikken for, skal du gøre et af følgende:

   - Vælg **Alle placeringer i Office 365** \> **Næste**.

   - Vælg **Lad mig vælge specifikke placeringer** \> **Næste**.

   Hvis du vil medtage eller udelade en hel placering, f.eks. alle Exchange mailkonti eller alle OneDrive-konti, skal du slå **status** for den pågældende placering til eller fra.

   Hvis du kun vil SharePoint bestemte websteder eller OneDrive-konti, skal du slå **Status** til og derefter klikke på linkene **under** Medtag for at vælge bestemte websteder eller konti.

7. Vælg **Brug avancerede indstillinger** \> **Næste**.

8. Vælg **+ Ny regel**.

9. I regeleditoren under **Brugerbeskeder** skal du slå status til.

    ![Afsnittet Brugerbeskeder i regeleditoren.](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Meddelelsesmails sendes ubeskyttet.

## <a name="options-for-configuring-email-notifications"></a>Indstillinger for konfiguration af mailbeskeder

For hver regel i en DLP-politik kan du:

- Send meddelelsen til de personer, du vælger. Disse personer kan omfatte ejeren af indholdet, den person, der senest har ændret indholdet, ejeren af det websted, hvor indholdet er gemt, eller en bestemt bruger.

- Tilpas den tekst, der er inkluderet i meddelelsen, ved hjælp af HTML eller tokens. Se afsnittet nedenfor for at få flere oplysninger.

> [!NOTE]
>  Mailbeskeder kan kun sendes til individuelle modtagere – ikke grupper eller distributionslister. Kun nyt indhold udløser en meddelelse via mail. Redigering af eksisterende indhold udløser politiktip, men ikke en mailmeddelelse.

![Indstillinger for mailbeskeder.](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)

### <a name="default-email-notification"></a>Standardmeddelelse via mail

Meddelelser har en emnelinje, der begynder med den handling, der foretages, f.eks. "Meddelelse", "Meddelelse blokeret" for mail eller "Adgang blokeret" for dokumenter. Hvis meddelelsen er om et dokument, indeholder brødteksten i meddelelse et link, der fører dig til det websted, hvor dokumentet er gemt, og åbner politiktip for dokumentet, hvor du kan løse eventuelle problemer (se afsnittet nedenfor om politiktip). Hvis meddelelsen er om en meddelelse, indeholder meddelelsen som en vedhæftet fil den meddelelse, der svarer til en DLP-politik.

![Meddelelse.](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)

Som standard viser meddelelser tekst i stil med følgende for et element på et websted. Meddelelsesteksten konfigureres separat for hver regel, så den viste tekst varierer, afhængigt af hvilken regel der er matchet.

|**Hvis DLP-politikreglen gør dette...**|**Derefter vises standardmeddelelsen for SharePoint eller OneDrive for Business, at dette ...**|**Derefter står der følgende som standardmeddelelse Outlook meddelelserne ...**|
|:-----|:-----|:-----|
|Sender en meddelelse, men tillader ikke tilsidesættelse  <br/> |Dette element er i konflikt med en politik i organisationen.  <br/> |Din mail er i konflikt med en politik i organisationen.  <br/> |
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse  <br/> |Dette element er i konflikt med en politik i organisationen. Hvis du ikke løser denne konflikt, kan adgangen til denne fil være blokeret.  <br/> |Din mail er i konflikt med en politik i organisationen. Meddelelsen blev ikke leveret til alle modtagere.  <br/> |
|Blokerer adgang og sender en meddelelse  <br/> |Dette element er i konflikt med en politik i organisationen. Adgang til dette element er blokeret for alle undtagen dets ejer, sidste ændring og den primære administrator af gruppen af websteder.  <br/> |Din mail er i konflikt med en politik i organisationen. Meddelelsen blev ikke leveret til alle modtagere.  <br/> |

### <a name="custom-email-notification"></a>Meddelelse om brugerdefineret mail

Du kan oprette en brugerdefineret mailbesked i stedet for at sende standardmailbeskeden til dine slutbrugere eller administratorer. Den brugerdefinerede mailmeddelelse understøtter HTML og har en tegngrænse på 5.000 tegn. Du kan bruge HTML til at medtage billeder, formatering og anden branding i meddelelsen.

Du kan også bruge følgende tokens til at tilpasse mailmeddelelsen. Disse tokens er variabler, der erstattes af bestemte oplysninger i den meddelelse, der sendes.

|**Token**|**Beskrivelse**|
|:-----|:-----|
|%%AppliedActions%%  <br/> |De handlinger, der anvendes på indholdet.  <br/> |
|%%ContentURL%%  <br/> |URL-adressen til dokumentet på SharePoint Online-webstedet eller OneDrive for Business webstedet.  <br/> |
|%%MatchedConditions%%  <br/> |De betingelser, der blev matchet af indholdet. Brug dette token til at informere andre om mulige problemer med indholdet.  <br/> |

![Meddelelse, der viser, hvor tokens vises.](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)

## <a name="options-for-configuring-policy-tips"></a>Indstillinger for konfiguration af politiktip

For hver regel i en DLP-politik kan du konfigurere politiktip til at:

- Du skal blot give personen besked om, at indholdet er i konflikt med en DLP-politik, så vedkommende kan handle for at løse konflikten. Du kan bruge standardteksten (se tabellerne nedenfor) eller angive brugerdefineret tekst om organisationens specifikke politikker.

- Tillad personen at tilsidesætte DLP-politikken. Du kan også:

  - Kræve, at personen angiver en forretningsberettigelse til tilsidesættelse af politikken. Disse oplysninger logføres, og du kan få dem vist i DLP-rapporterne i **afsnittet** Rapporter i Security &amp; Compliance Center.

  - Tillad personen at rapportere en falsk positiv og tilsidesætte DLP-politikken. Disse oplysninger logføres også til rapportering, så du kan bruge falske positive til at finjustere dine regler.

![Indstillinger for politiktip.](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)

Det kan f.eks. være, at du har en DLP-politik anvendt på OneDrive for Business websteder, der registrerer personlige id-oplysninger (PII), og denne politik har tre regler:

1. Første regel: Hvis der registreres færre end fem forekomster af disse følsomme oplysninger i et dokument, og dokumentet deles med personer i organisationen, viser handlingen **Send** en meddelelse et politiktip. For politiktip er det ikke nødvendigt at tilsidesætte indstillinger, fordi denne regel blot underretter personer og ikke blokerer adgang.

2. Anden regel: Hvis der registreres mere end fem forekomster af disse følsomme oplysninger i et dokument, og dokumentet deles med personer inden for organisationen, begrænser handlingen Bloker adgang til indhold tilladelserne for filen, og handlingen **Send** en meddelelse giver brugerne mulighed for at tilsidesætte handlingerne i denne regel ved at give en forretningsberettigelse. Din organisations virksomhed kræver nogle gange interne personer for at dele PII-data, og du ønsker ikke, at din DLP-politik blokerer dette arbejde.

3. Tredje regel: Hvis der registreres mere end fem forekomster af disse følsomme oplysninger i et dokument, og dokumentet deles med personer uden for organisationen, begrænser handlingen Bloker adgang til indhold tilladelserne for filen, og handlingen **Send** en meddelelse tillader ikke, at brugerne tilsidesætter handlingerne i denne regel, fordi oplysningerne deles eksternt. Under ingen omstændigheder bør personer i organisationen have tilladelse til at dele pii-data uden for organisationen.

### <a name="user-override-support"></a>Support til brugertilsidesættelse

Her er nogle gode tip til, hvordan du kan bruge et politiktip til at tilsidesætte en regel:

- Muligheden for at tilsidesætte er pr. regel, og den tilsidesætter alle handlinger i reglen (undtagen at sende en meddelelse, som ikke kan tilsidesættes).

- Det er muligt for indhold at matche flere regler i en DLP-politik, men kun politiktip fra den mest restriktive regel med højeste prioritet vises. Eksempelvis vises et politiktip fra en regel, der blokerer adgang til indhold, over et politiktip fra en regel, der blot sender en meddelelse. Dette forhindrer brugere i at se en kaskade af politiktip.

- Hvis politiktip i den mest restriktive regel tillader brugere at tilsidesætte reglen, tilsidesætter tilsidesættelsen af denne regel også andre regler, som indholdet har matchet.

- Hvis handlingen NotifyAllowOverride er angivet med WithoutJustification eller WithJustification eller FlasePositives, skal du sørge for, at BlockAccess er indstillet til sand, og BlockAccessScope har den relevante værdi. Ellers vises politiktip, men brugeren vil ikke kunne finde en mulighed for at tilsidesætte mailen med begrundelse.

#### <a name="availability-of-override"></a>Tilgængelighed af tilsidesættelse

|Meddelelsesregel |Handlingen Giv besked/bloker  |Tilsidesæt tilgængelig  |Kræve begrundelse  |
|---------|---------|---------|---------|
|Kun besked     |Giv besked         |Nej         |Nej         |
|Giv besked + AllowOverride     |Giv besked         |Nej         |Nej         |
|Giv besked + AllowOverride + Falsk positiv     |Giv besked         |Nej         |Nej         |
|Notify + AllowOverride + With justification     |Giv besked         |Nej         |Nej         |
|Notify + AllowOverride + False positiv + Without justification    |Giv besked         |Nej         |Nej         |
|Notify + AllowOverride + False positiv + With justification     |Giv besked         |Nej         |Nej         |
|Giv besked + blok     |Bloker         |Nej         |Nej         |
|Giv besked + Bloker + AllowOverride     |Bloker         |Ja         |Nej         |
|Giv besked + Bloker + AllowOverride + Falsk positiv     |Bloker         |Ja         |Nej         |
|Notify + Block + AllowOverride + With justification     |Bloker         |Ja         |Ja         |
|Notify + Block + AllowOverride + False positiv + Without justification     |Bloker         |Ja         |Nej         |
|Giv besked + Bloker + AllowOverride + Falsk positiv + Med begrundelse     |Bloker         |Ja         |Ja         |


## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>Politiktip på OneDrive for Business og SharePoint Online-websteder

Når et dokument på et OneDrive for Business-websted eller SharePoint Online-websted svarer til en regel i en DLP-politik, og denne regel bruger politiktip, viser politiktip særlige ikoner i dokumentet:

1. Hvis reglen sender en meddelelse om filen, vises advarselsikonet.

2. Hvis reglen blokerer adgangen til dokumentet, vises det blokerede ikon.

   ![Politiktipikoner på dokumenter i en OneDrive-konto.](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)

Hvis du vil handle på et dokument, kan du vælge et element ved at \> **vælge ikonet oplysningsrude**![.](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) i øverste højre hjørne på siden for at åbne detaljeruden Vis \> **politiktip**.

Politiktippen viser en liste over problemer med indholdet, og hvis politiktip er konfigureret med disse indstillinger, kan du vælge Løs og derefter Tilsidesætte  politiktip eller Rapportere en  falsk positiv.

![Oplysningsruden, der viser politiktip.](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)

![Politiktip med mulighed for at tilsidesætte.](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)

DLP-politikker synkroniseres med websteder, og indhold evalueres mod dem med jævne mellemrum og asynkront, så der kan være en kort forsinkelse mellem det tidspunkt, du opretter DLP-politikken, og det tidspunkt, hvor du begynder at se politiktip. Der kan være en lignende forsinkelse fra det tidspunkt, hvor du løser eller tilsidesætter et politiktip, til når ikonet på dokumentet på webstedet forsvinder.

### <a name="default-text-for-policy-tips-on-sites"></a>Standardtekst til politiktip på websteder

Politiktip viser som standard tekst, der ligner følgende for et element på et websted. Meddelelsesteksten konfigureres separat for hver regel, så den viste tekst varierer, afhængigt af hvilken regel der er matchet.

|**Hvis DLP-politikreglen gør dette...**|**Så står der følgende i standardpolitiktip :**|
|:-----|:-----|
|Sender en meddelelse, men tillader ikke tilsidesættelse  <br/> |Dette element er i konflikt med en politik i organisationen.  <br/> |
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse  <br/> |Dette element er i konflikt med en politik i organisationen. Hvis du ikke løser denne konflikt, kan adgangen til denne fil være blokeret.  <br/> |
|Blokerer adgang og sender en meddelelse  <br/> |Dette element er i konflikt med en politik i organisationen. Adgang til dette element er blokeret for alle undtagen dets ejer, sidste ændring og den primære administrator af gruppen af websteder.  <br/> |

### <a name="custom-text-for-policy-tips-on-sites"></a>Brugerdefineret tekst til politiktip på websteder

Du kan tilpasse teksten for politiktip separat fra mailmeddelelsen. I modsætning til brugerdefineret tekst til mailbeskeder (se ovenstående afsnit) accepterer brugerdefineret tekst til politiktip ikke HTML eller tokens. I stedet er brugerdefineret tekst til politiktip kun almindelig tekst med en grænse på 256 tegn.

## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>Politiktip i Outlook på internettet og Outlook 2013 og nyere

Når du opretter en ny mail i Outlook på internettet og Outlook 2013 og nyere, får du vist et politiktip, hvis du tilføjer indhold, der svarer til en regel i en DLP-politik, og denne regel bruger politiktip. Politiktippen vises øverst i meddelelsen over modtagerne, mens meddelelsen er ved at blive skrevet.

![Politiktip øverst i en meddelelse, der er ved at blive skrevet.](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)

Politiktip fungerer, uanset om de følsomme oplysninger vises i brødteksten, emnelinjen eller endda en vedhæftet fil i en meddelelse, som vist her.

![Politiktip, der viser, at en vedhæftet fil er i konflikt med en DLP-politik.](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)

Hvis politiktip er konfigureret til at tillade tilsidesættelse,  \>  \> kan du vælge Vis tilsidesættelse af detaljer Angive en forretningsberettigelse eller rapportere en falsk positiv \> **tilsidesættelse**.

![Politiktip i meddelelse udvidet til at vise indstillingen Tilsidesæt.](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)

![Dialogboks med politiktip, hvor du kan tilsidesætte politiktip.](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)

Bemærk, at når du føjer følsomme oplysninger til en mail, kan der være ventetid fra det tidspunkt, hvor de følsomme oplysninger tilføjes, og til politiktip vises.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 og nyere understøtter visning af politiktip for kun visse betingelser

Aktuelt understøtter Outlook 2013 og nyere kun politiktip til disse betingelser:

- Indhold indeholder
- Indhold deles

Bemærk, at Undtagelser betragtes som betingelser, og alle disse betingelser fungerer i Outlook, hvor de matcher indhold og gennemtvinger beskyttende handlinger for indhold. Men visning af politiktip til brugere understøttes endnu ikke. Desuden understøtter Outlook ikke visning af politiktip til en DLP-politik, der anvendes til en dynamisk distributionsgruppe.

### <a name="policy-tips-in-the-exchange-admin-center-vs-the-security-amp-compliance-center"></a>Politiktip i Exchange i forhold til Security &amp; Compliance Center

Politiktip kan enten fungere med DLP-politikker og regler for mailflow, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> Administration, eller med DLP-politikker, der er oprettet i Security &amp; Compliance Center, men ikke begge. Dette skyldes, at disse politikker er gemt på forskellige placeringer, men politiktip kan kun trækkes fra en enkelt placering.

Hvis du har konfigureret politiktip i Exchange Administration, vises politiktip, som du konfigurerer i Security &amp; Compliance Center, ikke for brugere i Outlook på internettet og Outlook 2013 og senere, før du deaktiverer tip i Exchange Administration. Dette sikrer, at dine aktuelle Exchange regler for mailflow (også kaldet transportregler) fortsat fungerer, indtil du vælger at skifte til Security &amp; Compliance Center.

Bemærk, at mens politiktip kun kan trækkes fra et enkelt sted, sendes der altid mailbeskeder, også selvom du bruger DLP-politikker i både Security &amp; Compliance Center og Exchange Administration.

### <a name="default-text-for-policy-tips-in-email"></a>Standardtekst til politiktip i mails

Politiktip viser som standard tekst, der ligner følgende for mail.

|**Hvis DLP-politikreglen gør dette...**|**Så står der følgende i standardpolitiktip :**|
|:-----|:-----|
|Sender en meddelelse, men tillader ikke tilsidesættelse  <br/> |Din mail er i konflikt med en politik i din organisation.  <br/> |
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse  <br/> |Din mail er i konflikt med en politik i din organisation.  <br/> |
|Blokerer adgang og sender en meddelelse  <br/> |Din mail er i konflikt med en politik i din organisation.  <br/> |

## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Politiktip i Excel, PowerPoint og Word

Når personer arbejder med følsomt indhold i desktopversionerne af Excel, PowerPoint og Word, kan politiktip give dem besked i realtid om, at indholdet er i konflikt med en DLP-politik. Dette kræver, at:

- Dokumentet Office på et websted eller OneDrive for Business et SharePoint Online-websted.

- Webstedet er inkluderet i en DLP-politik, der er konfigureret til at bruge politiktip.

Office-programmer synkroniserer automatisk DLP-politikker direkte fra Office 365 og scanner derefter dine dokumenter for at sikre, at de ikke er i konflikt med dine DLP-politikker og viser politiktip i realtid.

> [!NOTE]
> Office-skrivebordsapps scanner selv dokumenter for at afgøre, om tip til DLP-politik skal vises. De viser ikke politiktip, som SharePoint Online-websteder eller OneDrive for Business-websteder allerede har bestemt, skal vises på en fil. Det betyder, at du muligvis ikke altid får vist et tip til DLP-politikken i de skrivebordsapps, du kan se på SharePoint Online-websteder eller OneDrive for Business websteder. I modsætning hertil viser Office-programmerne på internettet kun tip til DLP-politikker, som SharePoint Online-websteder eller OneDrive for Business-websteder allerede har bestemt, skal vises.

Afhængigt af hvordan du konfigurerer politiktip i DLP-politikken, kan personer vælge blot at ignorere politiktip, tilsidesætte politikken med eller uden en forretningsberettigelse eller rapportere en falsk positiv.

Politiktip vises på meddelelseslinjen.

![Meddelelseslinjen viser politiktip Excel 2016.](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

Og politiktip vises også i Backstage-visningen (på **fanen** Filer).

![Backstage viser politiktip i Excel 2016.](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)

Hvis politiktip i DLP-politikken er konfigureret med disse indstillinger, kan du vælge  Løs for  at tilsidesætte et politiktip eller **Rapportere** en falsk positiv.

![Indstillinger for politiktip i Backstage i Excel 2016.](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)

I hver af disse Office programmer kan andre vælge at deaktivere politiktip. Hvis de er slået fra, vises politiktip, der er simple meddelelser, ikke på meddelelseslinjen eller Backstage-visningen (under **fanen** Filer). Politiktip om blokering og tilsidesættelse vises dog stadig, og de modtager stadig mailbeskeden. Desuden undtager de aktivering af politiktip ikke dokumentet fra eventuelle DLP-politikker, der er anvendt på det.

### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>Standardtekst til politiktip i Excel 2016, PowerPoint 2016 og Word 2016

Politiktip viser som standard tekst som følgende på meddelelseslinjen og Backstage-visningen i et åbent dokument. Meddelelsesteksten konfigureres separat for hver regel, så den viste tekst varierer, afhængigt af hvilken regel der er matchet.

|**Hvis DLP-politikreglen gør dette...**|**Så står der følgende i standardpolitiktip :**|
|:-----|:-----|
|Sender en meddelelse, men tillader ikke tilsidesættelse  <br/> |Denne fil er i konflikt med en politik i organisationen. Gå til menuen **Filer** for at få flere oplysninger.  <br/> |
|Blokerer adgang, sender en meddelelse og tillader tilsidesættelse  <br/> |Denne fil er i konflikt med en politik i organisationen. Hvis du ikke løser denne konflikt, kan adgangen til denne fil være blokeret. Gå til menuen **Filer** for at få flere oplysninger.  <br/> |
|Blokerer adgang og sender en meddelelse  <br/> |Denne fil er i konflikt med en politik i organisationen. Hvis du ikke løser denne konflikt, kan adgangen til denne fil være blokeret. Gå til menuen **Filer** for at få flere oplysninger.  <br/> |

### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Brugerdefineret tekst til politiktip i Excel, PowerPoint og Word

Du kan tilpasse teksten for politiktip separat fra mailmeddelelsen. I modsætning til brugerdefineret tekst til mailbeskeder (se ovenstående afsnit) accepterer brugerdefineret tekst til politiktip ikke HTML eller tokens. I stedet er brugerdefineret tekst til politiktip kun almindelig tekst med en grænse på 256 tegn.

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
- [DLP-politikbetingelser, undtagelser og handlinger (forhåndsvisning)](./dlp-microsoft-teams.md)
- [Opret en DLP-politik for at beskytte dokumenter med FCI eller andre egenskaber](protect-documents-that-have-fci-or-other-properties.md)
- [Hvad DLP-politikskabelonerne indeholder](what-the-dlp-policy-templates-include.md)
- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
