---
title: Skift fra en Microsoft 365 E-plan til en Microsoft 365 F-plan
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om de ting, du skal overveje, og hvordan du forbereder, hvis du skifter nogle af dine brugere fra en Microsoft 365 E-plan til en Microsoft 365 F-plan.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_FLW
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 90e29a5ec2ddf70afb299398113be034580eda85
ms.sourcegitcommit: 1efb75d033860977239b479f92e7eaf274b5fbf0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2022
ms.locfileid: "66827151"
---
# <a name="changing-from-a-microsoft-365-e-plan-to-a-microsoft-365-f-plan"></a>Skift fra en Microsoft 365 E-plan til en Microsoft 365 F-plan

Hvis du overvejer at skifte nogle af dine brugere fra en Microsoft 365 E-plan til en Microsoft 365 [F3](https://www.microsoft.com/microsoft-365/enterprise/f3) - eller [F1-plan](https://www.microsoft.com/microsoft-365/enterprise/f1) , indeholder denne artikel en vejledning, der hjælper dig med at forberede din organisation på ændringen. Hvis du skifter fra en E-plan til en F-plan, påvirker det de tjenester og funktioner, som brugerne har adgang til.

E-planer er beregnet til informationsmedarbejdere (medarbejdere, der typisk arbejder ved et skrivebord) og F-planer er beregnet til frontlinjearbejdere (medarbejdere, der er på farten, ofte på mobilenheder og arbejder direkte med kunder eller offentligheden). Hver plan kan fortsætte med at udvikle sig over tid for at blive mere skræddersyet til henholdsvis informationsmedarbejdere og frontlinjearbejdere. Du kan få mere at vide under [Forstå brugertyper og licenser for frontlinemedarbejdere](flw-licensing-options.md).

Du får et overblik over, hvad du kan forvente, når brugerne skifter til en F-plan, hvordan de skal forberede sig på ændringen, og hvad du skal gøre, når du har skiftet plan for at overgå frontlinjemedarbejderne i din organisation.

## <a name="understand-the-key-differences-between-e-and-f-plans"></a>Forstå de vigtigste forskelle mellem E- og F-planer

Start med at blive fortrolig med tjenesten og funktionsforskellene mellem planerne.

Nogle af de vigtigste forskelle omfatter:

- F-planer omfatter ikke Office-skrivebordsapps eller Outlook-skrivebordsappen.
- F-planer er begrænset til enheder med integrerede skærme, der er mindre end 10,1 tommer i Office-mobilapps.
- F planlægger [som standard fastgørelse af frontlinemedarbejderapps](pin-teams-apps-based-on-license.md) som Walkie Talkie, Opgaver, Skift og Godkendelser i Microsoft Teams.

I dette afsnit har vi inkluderet flere oplysninger om disse vigtige forskelle og fremhævet nogle yderligere forskelle, du skal være opmærksom på. Husk, at dette ikke er en omfattende liste. Få mere at vide:

- Se [Sammenligning af moderne arbejdsplan](https://go.microsoft.com/fwlink/p/?linkid=2139145) for at få en detaljeret sammenligning af, hvad der er inkluderet i E- og F-planer.
- Se [tilgængeligheden af tjenesten](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options#service-availability-within-each-microsoft-365-and-office-365-plan) og [tilgængeligheden af funktioner på tværs af planer](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description#feature-availability-across-some-plans) for at få en liste over service- og funktionstilgængelighed på tværs af E- og F-planer.

### <a name="office-apps"></a>Office-apps

Office-skrivebordsapps er ikke inkluderet i F3- og F1-planer. Dine frontlinjemedarbejdere kan bruge Office på internettet og Office-mobilapps til at få tingene fra hånden. Vær opmærksom på, at F3-brugere har fuld adgang til dokumenter i Office på internettet, og at F1-brugere har skrivebeskyttet adgang.

|Tjeneste eller funktion|Microsoft 365 E3/E5  |Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Office-skrivebordsapps (Word, Excel, OneNote, PowerPoint, Access, Publisher)|Ja|Nej|Nej|
|Office på internettet (Word, Excel, OneNote, PowerPoint)|Ja|Ja|Skrivebeskyttet|
|Office-mobilapps (Word, Excel, PowerPoint, Outlook, OneNote)|Ja|Ja&sup1;|Skrivebeskyttet|

&1. Redigering af filer, der understøttes på enheder med integrerede skærme på mindre end 10,1 tommer.

#### <a name="office-for-the-web"></a>Office til internettet

Med Office på internettet bruger frontlinjemedarbejderne en webbrowser til at åbne Word-, Excel-, OneNote- og PowerPoint-filer.

Her er nogle forskelle, du skal være opmærksom på, når du bruger Office på internettet. Du kan finde en detaljeret sammenligning af funktioner mellem Office på internettet og Office-skrivebordsapps [i Office på internettet tjenestebeskrivelse](/office365/servicedescriptions/office-online-service-description/office-online-service-description).

|Tjeneste eller funktion|Nogle forskelle |Lær mere|
|---------|---------|---------|
|**Word til internettet**|<ul><li> Kan åbne og redigere dokumenter (.docm) og skabeloner (.dotm), men makroer kan ikke køres.</li><li>Kan åbne, men ikke redigere brugerdefinerede tilladelser (UDP) IRM-beskyttede dokumenter (Information Rights Management).</li></ul>|<ul><li>[Beskrivelse af Word til webtjenesten](/office365/servicedescriptions/office-online-service-description/word-online)</li><li>[Forskelle mellem at bruge et dokument i browseren og i Word](https://support.microsoft.com//office/differences-between-using-a-document-in-the-browser-and-in-word-3e863ce3-e82c-4211-8f97-5b33c36c55f8)</li></ul>|
|**Excel til internettet**|<ul><li>Kan åbne og redigere projektmapper med aktiverede makroer (.xlsm), men makroer afspilles ikke.</li><li>[Begrænsninger for filstørrelse](https://support.microsoft.com/office/file-size-limits-for-workbooks-in-sharepoint-9e5bc6f8-018f-415a-b890-5452687b325e)<ul><li>Hvis du vil have vist eller interagere med en projektmappe, der er gemt i SharePoint Online, skal projektmappen være mindre end 100 MB. </li><li>Hvis du vil åbne en projektmappe, der er knyttet til en mail i Outlook på internettet, skal projektmappen være mindre end 10 MB.</li></ul></ul>|<ul><li>[beskrivelse af Excel på internettet tjeneste](/office365/servicedescriptions/office-online-service-description/excel-online)</li><li>[Forskelle mellem at bruge en projektmappe i browseren og i Excel](https://support.microsoft.com/office/differences-between-using-a-workbook-in-the-browser-and-in-excel-f0dc28ed-b85d-4e1d-be6d-5878005db3b6)</li><li>De fleste Excel-funktioner fungerer i en browser, som de gør i Excel. Du kan se en liste over undtagelser [under Funktioner i Excel og i Excel på internettet](https://support.microsoft.com/office/differences-between-using-a-workbook-in-the-browser-and-in-excel-f0dc28ed-b85d-4e1d-be6d-5878005db3b6#__functions).</li></ul>|
|**OneNote til internettet**|<ul><li>Søgning er begrænset til den aktuelle sektion.</li><li>Zoom ind og ud er ikke tilgængelig. Brugerne kan i stedet bruge zoomfunktionen i deres browser.</li></ul>|<ul><li>[beskrivelse af OneNote på internettet tjeneste](/office365/servicedescriptions/office-online-service-description/onenote-online)</li><li>[Forskelle mellem at bruge en notesbog i browseren og i OneNote](https://support.microsoft.com/office/differences-between-using-a-notebook-in-the-browser-and-in-onenote-a3d1fc13-ac74-456b-b391-b633a62aa83f)</li></ul>|
|**PowerPoint til internettet**|<ul><li>Kan åbne filer op til 2 GB.</li><li>Kan åbne og redigere præsentationer med aktiverede makroer (.pptm, .potm, .ppsm), men makroer kører ikke.</li></ul>|<ul><li>[beskrivelse af PowerPoint på internettet tjeneste](/office365/servicedescriptions/office-online-service-description/powerpoint-online)</li><li>[Sådan fungerer visse funktioner i webbaseret PowerPoint](https://support.microsoft.com/office/how-certain-features-behave-in-web-based-powerpoint-a931f0c8-1305-4428-8f7c-9cfa00ef28c5)</li></ul>|

#### <a name="office-mobile"></a>Office Mobile

Frontlinjemedarbejderne kan få Office på deres mobilenheder på to måder:

- Installér den Office-mobilapp, der kombinerer Word, Excel og PowerPoint.
- Installér individuelle Office-mobilapps til Word, Excel, PowerPoint og OneNote.

Du kan få mere at vide under [Installér og konfigurer Office på en Android og](https://support.microsoft.com/office/install-and-set-up-office-on-an-android-cafe9d6f-8b0c-4b03-b20a-12438a82a22d) [Installér og konfigurer Office på en iPhone eller iPad](https://support.microsoft.com/office/install-and-set-up-office-on-an-iphone-or-ipad-9df6d10c-7281-4671-8666-6ca8e339b628).

Du kan få flere oplysninger om de funktioner, der er tilgængelige i Office Mobile, [under Hvad du kan gøre i Office-apps på mobilenheder med et Microsoft 365-abonnement](https://support.microsoft.com/office/what-you-can-do-in-the-office-apps-on-mobile-devices-with-a-microsoft-365-subscription-9ef8b63a-05fd-4f9c-bac5-29da046833ea).

#### <a name="email"></a>E-mail

F3-brugere har en postkasse på 2 GB, som de kan få adgang til via Outlook på internettet. Hvis du vil have en sammenligning af funktioner mellem Outlook på internettet og Outlook-skrivebordsappen, skal [du se Sammenlign Outlook til pc, Outlook på internettet og Outlook til iOS & Android](https://support.microsoft.com/office/compare-outlook-for-pc-outlook-on-the-web-and-outlook-for-ios-android-b26a7bf5-0ac7-48ba-97af-984e0645dde5).

F1-brugere har ikke postkasserettigheder. Selvom en postkasse er klargjort til brugere via Exchange Kiosk-planen, er de ikke berettiget til at bruge den. Vi anbefaler, at du [deaktiverer Outlook på internettet](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) for F1-brugere.

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Exchange Online postkasse|Ja (postkasse på 100 GB)|Ja (2 GB postkasse)|Ingen&sup1;|
|Outlook-skrivebordsapp|Ja|Nej|Nej|
|Arkivpostkasse|Ja|Nej|Nej|
|Uddeleger adgang|Ja|Nej|Nej|

&1. F1 indeholder Exchange Kiosk-planen om kun at aktivere Teams-kalender og omfatter ikke postkasserettigheder.

Du kan få mere at vide [under Exchange Online tjenestebeskrivelse](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description).

#### <a name="teams"></a>Teams

F3- og F1-planer omfatter Teams-skrivebordsappen, mobilappen og webappen til frontlinemedarbejderkommunikation og -samarbejde. Dine frontlinjemedarbejdere har adgang til Teams-funktioner, herunder møder, chat, kanaler, indhold og apps. De kan dog ikke oprette livebegivenheder og webinarer eller bruge Teams Phone-funktioner.

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Livebegivenheder|Ja|Nej|Nej|
|Webinarer|Ja|Nej|Nej|
|Teams-telefon|Ja|Nej|Nej|

#### <a name="sharepoint"></a>SharePoint

F3- og F1-brugere kan samarbejde om dokumenter og få adgang til ressourcer for hele organisationen, f.eks. undervisningsmateriale, der er gemt i SharePoint. Vær opmærksom på, at F3- og F1-planer ikke indeholder webstedspostkasser eller personlige websteder.

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Webstedspostkasse|Ja|Nej|Nej|
|Personligt websted|Ja|Nej|Nej|

Du kan få mere at vide om SharePoint-grænser under [SharePoint-grænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).

#### <a name="content-services"></a>Indholdstjenester

F3- og F1-brugere har 2 GB OneDrive-lagerplads til at gemme og dele filer. Du kan få mere at vide under [Beskrivelse af OneDrive-tjeneste](/office365/servicedescriptions/onedrive-for-business-service-description).

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|OneDrive|Ubegrænset lagerplads&sup1;|2 GB lagerplads|2 GB lagerplads|
|Microsoft Stream|Ja|Ja&sup2;|Ja&sup2;|
|Sway|Ja|Ja|Nej|
|Visio til internettet|Ja|Ja|Skrivebeskyttet|
|Dykke|Ja|Nej|Nej|

&1. Op til 5 TB oprindeligt OneDrive-lager pr. bruger baseret på lejerens [standardkvote](/onedrive/set-default-storage-space) for abonnementer med mere end fem brugere. Der kan anmodes om mere lagerplads.</br>
&, sup2; Brugerne kan optage møder og forbruge Stream-indhold, men kan ikke publicere til eller dele i Stream.

#### <a name="insights-and-analytics"></a>Indsigt og analyse

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Viva Insights|Ja|Nej|Nej|
|Power BI|Ja|Nej|Nej|

#### <a name="work-management-and-automation"></a>Styring og automatisering af arbejde

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Power Apps|Ja|Ja|Nej|
|Power Automate|Ja|Ja|Nej|
|Power Virtual Agents|Ja|Ja|Nej|
|Dataverse til Teams|Ja|Ja|Nej|
|Microsoft Forms|Ja&sup1;|Ja&sup1;|Nej|
|Microsoft-opgave|Ja|Ja|Nej|

&1. Brugere med licens kan oprette, dele og administrere formularer. Der kræves ikke en licens for at udfylde eller besvare en formular.

#### <a name="windows"></a>Windows

|Tjeneste eller funktion|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Windows 11 Enterprise|Ja|Ja&sup1;|Nej|

&1. Ingen Long-Term servicekanal (LTSC) eller Microsoft Desktop Optimization Pack (MDOP). VDI (Virtual Desktop Infrastructure) gælder kun for brugere med licens til en delt enhed med QoS (Quality of Service) (undtagen Azure Virtual Desktop).

## <a name="what-to-expect"></a>Hvad kan du forvente?

I følgende tabel vises vigtige ting, du skal overveje og anbefale handlinger, der skal udføres under ændringsprocessen. Brug disse oplysninger til at identificere, hvad du skal gøre, før skift, og hvad du skal planlægge efter at kontakten er fuldført. 

Vi refererer til denne tabel i senere afsnit i denne artikel.

|Tjeneste eller funktion |Før kontakten|Efter kontakten|
|---------|---------|---------|
|Office-apps| <ul><li>Identificer filer, der er gemt på brugernes lokale computere, og hjælp brugerne med at flytte dem til deres OneDrive.</li><li>Vær opmærksom på, at Office-skrivebordsapps skifter til tilstand med reduceret funktionalitet, når du har skiftet til en F-plan. Vær forberedt på at fjerne Office Desktop-apps efter parameteren.</li></ul>| Brugere:</br> <ul><li>Log på [office.com](https://www.office.com) for at få adgang til Office på internettet.</li><li>[Installér og brug Office-mobilapps](https://support.microsoft.com/office/set-up-office-apps-and-email-on-a-mobile-device-7dabb6cb-0046-40b6-81fe-767e0b1f014f) (hvis ikke allerede).</li><li>Brugerne kan også samarbejde direkte om dokumenter fra SharePoint-dokumentbiblioteker, OneDrive, Teams og Yammer.</li></ul>Admins:<ul><li>Fjern Office-skrivebordsapps fra brugernes computere.</li></ul>      |
|Mail, Exchange, Outlook|<ul><li>Identificer brugerpostkasser på mere end 2 GB ved hjælp af [PowerShell-cmdlet'en Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics?view=exchange-ps) Exchange, og reducer derefter postkassens størrelse efter behov. Du kan få mere at vide under [Grænser for postkasselager i Outlook på internettet](https://support.microsoft.com/office/mailbox-storage-limits-in-outlook-on-the-web-f170fe90-b859-4034-bcda-e186fc6a26f5).</li><li>Hvis brugerne har en arkivpostkasse:</li><ul><li>Flyt indholdet i arkivpostkassen tilbage til brugerens postkasse.</li><li>Kontrollér, om der er arkivpolitikker, der automatisk kan flytte mails baseret på meddelelsernes alder ved hjælp af [Get-EXOMailbox](/powershell/module/exchange/get-exomailbox?view=exchange-ps) Exchange Online PowerShell-cmdlet'en.</li></ul> <li>Identificer adgang til og brug af webstedspostkasse.</li><li>Outlook-skrivebordsapp, -data og -konfiguration:</li><ul><li>Identificer brugere og computere, der bruger Outlook-datafiler (.pst).</li><li>Identificer og dokumenter eksisterende regler kun for Outlook-klienter.</li><li>Eksportér mailsignaturer.</li></ul></ul>|Brugere:</br><ul><li>Log på [office.com](https://www.office.com) for at få adgang til Outlook på internettet.</li><li>[Konfigurer mail på mobilenheder](https://support.microsoft.com/office/set-up-office-apps-and-email-on-a-mobile-device-7dabb6cb-0046-40b6-81fe-767e0b1f014f) (hvis ikke allerede).</li><li>Kontrollér og opdater mailsignaturer.</li><li>Kontrollér og opdater postkasseregler.</li></ul>Admins:<ul><li> [Deaktiver Outlook på internettet](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) for F1-brugere, og bed dem om ikke at få adgang til postkassen via andre metoder.</li></ul>|
|Teams | <ul><li>Identificer brugen af livebegivenheder og webinarer.</li><li>Identificer brugere, der har Aktiveret Teams-telefon. Hvis brugerne bruger denne funktion, er de muligvis ikke det rette sæt brugere til at skifte til en F-plan.</li></ul>      ||
|OneDrive | <ul><li>Identificer brugere, der bruger mere end eller tæt på 2 GB lagerplads. (OneDrive bliver skrivebeskyttet for brugere, der har overskredet grænsen på 2 GB efter skift til en F-plan).</li><li>Hjælp brugerne med at reducere antallet af filer, der er gemt i OneDrive, og den samlede mængde lagerplads, der bruges.</li><li>Sørg for, at alle filer er fuldt synkroniseret fra brugernes computere til OneDrive.</li></ul>| |

## <a name="prepare-to-switch-plans"></a>Forbered skift af planer

### <a name="create-a-change-management-strategy"></a>Opret en strategi for administration af ændringer

En optimal strategi for administration af ændringer omfatter, hvordan du kommunikerer med, oplærer og understøtter dine brugere før og efter, du skifter dem til en F-plan. Her er f.eks. et par ting, du skal overveje:

- Hvordan vil brugerne være opmærksomme på kontakten?
- Hvordan lærer brugerne at navigere i forskellene i tjenester og funktioner? Skiftet til en F-plan kan kræve en øget indsats inden for oplæring, da det kræver en ændring i funktionsmåden.
- Hvordan får brugerne hjælp og support?

Når du bygger din strategi, skal du overveje kommunikations- og oplæringspræferencer. For at hjælpe med at sikre en vellykket overgang kan du skræddersy dine beskeder, uddannelse og support til dine frontlinjearbejderes og virksomhedskulturens specifikke behov.

Her er nogle idéer, der kan hjælpe med at planlægge din strategi.

|Kommunikation|Uddannelse|Support|
|---------|---------|---------|
|<ul><li>E-mail</li><li>Afdelings- eller butikschefer</li><li>Champions</li><li>Teams og kanaler</li><li>Yammer-communities</li></ul> |<ul><li>Microsofts onlinehjælp, uddannelse og videoressourcer</li><li>In-house training</li></ul>|<ul><li>In-house helpdesk</li><li>Selvbetjent intranetwebsted</li><li>Microsofts onlinehjælp, uddannelse og videoressourcer</li><li>Gulvvandre og mestre</li></ul>         |

Du kan også se disse adoptionsressourcer for at hjælpe dig med at engagere og oplære dine brugere:

- [Microsoft 365 – Microsoft Adoption](https://adoption.microsoft.com/microsoft-365/)
- [Teams til frontlinjearbejdere – Microsoft Adoption](https://adoption.microsoft.com/microsoft-teams/frontline-workers/)

### <a name="back-up-or-prepare-data"></a>Sikkerhedskopiér eller forbered data

Identificer og sikkerhedskopiér eller forbered data, som brugerne vil beholde. Følg vejledningen i afsnittet [Hvad du kan forvente](#what-to-expect) tidligere i denne artikel, og fuldfør de anbefalede handlinger i kolonnen **Før skift** i tabellen for hver af følgende komponenter:

- Office-apps
- Mail, Exchange, Outlook
- Teams
- OneDrive

Du kan få flere oplysninger under [Sikkerhedskopiér data, før du skifter plan](/microsoft-365/commerce/subscriptions/back-up-data-before-switching-plans).

## <a name="switch-users-to-a-microsoft-365-f-plan"></a>Skift brugere til en Microsoft 365 F-plan

Du kan bruge Microsoft 365 Administration til manuelt at ændre planer eller en scriptet tilgang via PowerShell-cmdlet'er. Uanset hvilken metode du vælger, er det vigtigt at fuldføre tildelingen af licensændringen i én handling. Med andre ord skal du fjerne en eksisterende E-licens og erstatte den ved at tildele en F-licens i den samme handling.

Undgå at fjerne en eksisterende licens for en bruger og derefter tildele en ny på et senere tidspunkt. Dette kan påvirke en brugers data. Du kan få mere at vide under [Hvad sker der med en brugers data, når du fjerner brugerens licens?](/microsoft-365/admin/manage/remove-licenses-from-users?view=o365-worldwide#what-happens-to-a-users-data-when-you-remove-their-license).

Hvis du vil have en trinvis vejledning i, hvordan du ændrer planer i Microsoft Administration, skal du se [Skift Microsoft-planer manuelt](/microsoft-365/commerce/subscriptions/change-plans-manually).

## <a name="what-to-do-after-switching-plans"></a>Sådan gør du, når du har skiftet plan

Følg vejledningen i afsnittet [Hvad du kan forvente](#what-to-expect) tidligere i denne artikel, og fuldfør de anbefalede handlinger i kolonnen **Efter parameteren** i tabellen for hver af følgende komponenter:

- Office-apps
- Mail, Exchange, Outlook
- Teams
- OneDrive

Kommuniker med brugerne om, at ændringen er fuldført, og fortæl dem, hvordan de får hjælp som defineret i din strategi for administration af ændringer. Det kan være en god idé at inkludere links til [hjælp og læringsressourcer](#user-setup-help-and-learning-resources) for at understøtte dem i overgangen.

## <a name="user-setup-help-and-learning-resources"></a>Brugerkonfiguration, hjælp og læringsressourcer

Her er nogle links til konfiguration, hjælp og læringsressourcer, som du kan dele med dine frontlinjemedarbejdere til oplæring og support.

|App|Links |
|---------|---------|
|Office til internettet|<ul><li>[Office på internettet træning](https://support.microsoft.com/office/office-for-the-web-training-e315b031-2bd5-40a1-99ca-264ebf2c8f96)</li><li>[Kom i gang med Office på internettet i Microsoft 365](https://support.microsoft.com/office/get-started-with-office-for-the-web-in-microsoft-365-5622c7c9-721d-4b3d-8cb9-a7276c2470e5)</li></ul>|
|Outlook på internettet|<ul><li>[Lær Outlook på internettet at kende](https://support.microsoft.com/office/get-to-know-outlook-on-the-web-3f1a229b-0d60-438f-b515-dd7a28026bc1)</li><li>[Få hjælp til Outlook på internettet](https://support.microsoft.com/office/get-help-with-outlook-on-the-web-cf659288-35cc-4c6c-8c75-e8e4317fda11)</li><li>[Outlook på internettet videoer](https://support.microsoft.com/office/learn-more-about-outlook-on-the-web-adbacbab-fe59-4259-a550-6cb7f85f19ec)</li></ul>|
|Office Mobile|Installationsprogrammet:</br><ul><li>[Konfigurer Office-apps og -mail på Android](https://support.microsoft.com/office/set-up-office-apps-and-email-on-android-6ef2ebf2-fc2d-474a-be4a-5a801365c87f)</li><li>[Konfigurer Office-apps og -mail på iOS-enheder](https://support.microsoft.com/office/set-up-the-office-app-and-outlook-on-ios-devices-0402b37e-49c4-4419-a030-f34c2013041f)</li></ul>Hjælp til Office-mobilapp:<ul><li>[Hjælp til Office-mobilapp til Android](https://support.microsoft.com/office/microsoft-office-app-for-android-0383d031-a1c6-46c9-b734-53cd1d22765b)</li><li>[Hjælp til Office-app til iOS](https://support.microsoft.com/office/microsoft-office-app-for-ios-c8880c05-883a-46b6-ad32-9bffa31228d0)</li></ul>Individuel Hjælp til Office-mobilapp:<ul><li>[Word til Android telefoner](https://support.microsoft.com/office/word-for-android-phones-help-764afb31-ad50-4645-8f51-820ecf731d8f), [Word til Android tablets,Word](https://support.microsoft.com/office/word-for-android-tablets-help-8a0dcd56-fb32-4e0d-95d8-997c066125c8) [til iPhone](https://support.microsoft.com/office/word-for-iphone-help-d41a5299-f6fa-4cca-b529-46a8069c5796)[, Word til iPad](https://support.microsoft.com/office/word-for-ipad-help-6567cf2a-c949-4213-912d-f7a14f6264c5)</li><li>[Excel til Android telefoner](https://support.microsoft.com/office/excel-for-android-phones-help-f818cb37-bfac-485d-8480-363b3da40596), [Excel til Android tablets](https://support.microsoft.com/office/word-for-android-tablets-help-8a0dcd56-fb32-4e0d-95d8-997c066125c8), [Excel til iPhone](https://support.microsoft.com/office/excel-for-iphone-help-b367819b-05b4-4a56-ab1c-678da62e1fd3) [Excel til iPad](https://support.microsoft.com/office/excel-for-ipad-help-6b5dc2e1-a8e4-48e6-bb69-cb9a3964bc91)</li><li>[PowerPoint til Android telefoner](https://support.microsoft.com/office/powerpoint-for-android-phones-help-f6714e00-0ee2-48d1-bd3d-e1997565861f), [PowerPoint til Android tablets](https://support.microsoft.com/office/powerpoint-for-android-tablets-help-2ada1d22-3784-4943-bc47-9d1ede42875c), [PowerPoint til iPhone](https://support.microsoft.com/office/powerpoint-for-iphone-help-754fcb37-783b-4e8a-afca-edb900221b8b) [PowerPoint til iPad](https://support.microsoft.com/office/powerpoint-for-ipad-help-b75ce3bb-03e3-46df-a792-647573fef84a)</li><li>[OneNote til Android](https://support.microsoft.com/office/microsoft-onenote-for-android-46b4b49d-2bef-4746-9c30-6abb5e20b688), [OneNote til iPhone](https://support.microsoft.com/office/microsoft-onenote-for-iphone-b93a0ea8-1285-4d31-a7c5-86a849731902), [OneNote til iPad](https://support.microsoft.com/office/microsoft-onenote-help-ipad-f44e5bcd-5203-4553-9de4-0c56e6500825)</li></ul>
|Teams|<ul><li>[Videotræning i Teams](https://support.microsoft.com/office/microsoft-teams-video-training-4f108e54-240b-4351-8084-b1089f0d21d7)</li><li>[Teams hjælper med & læring](https://support.microsoft.com/teams)</li></ul>|

