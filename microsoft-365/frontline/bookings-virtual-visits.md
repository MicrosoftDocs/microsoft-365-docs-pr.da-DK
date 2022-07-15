---
title: Virtuelle aftaler med Microsoft Teams og Bookings-appen
author: lanachin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: ''
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- microsoftcloud-healthcare
- microsoftcloud-retail
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
ms.reviewer: ''
description: Få mere at vide om, hvordan du planlægger, administrerer og udfører virtuelle aftaler ved hjælp af appen Bookings i Teams.
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: ef4ca09cac8cc411e6b9b33b32b27c01265ddccf
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824074"
---
# <a name="virtual-appointments-with-microsoft-teams-and-the-bookings-app"></a>Virtuelle aftaler med Microsoft Teams og Bookings-appen

## <a name="overview"></a>Oversigt

[Appen Bookings](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5) i Microsoft Teams giver organisationer en nem måde at planlægge og administrere virtuelle aftaler for personale og deltagere på. Brug den til at planlægge aftaler som sundhedsbesøg, økonomiske konsultationer, interviews, kundesupport, virtuelle fittings og konsultationer, åbningstider for uddannelse og meget mere.

Bookings-appen gør det nemt at administrere komplekse planlægningsbehov for en hvilken som helst organisation. Planlæggere kan administrere flere afdelings- og personalekalendere samt kommunikation med interne og eksterne deltagere fra en enkelt oplevelse.

De virtuelle aftaler afholdes via Microsoft Teams-møder, som tilbyder robuste funktioner til videomøder. En læge kan f.eks. dele sin skærm og gennemgå testresultaterne med en patient. Eller en bankrådgiver kan anmode om elektroniske signaturer på dokumenter, så de kan lukke transaktioner eksternt.

Hver virtuel aftale indeholder et Teams-mødelink, der sendes til deltagere i en mail, hvor de nemt kan deltage fra en webbrowser eller i Teams på en hvilken som helst enhed. Automatiserede mailpåmindelser hjælper med at reducere antallet af no-shows og forbedre kunde- og klientengagementet.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4TQop]

Med Bookings får du en oplevelse, der er skræddersyet til din branche. Her er et par eksempler på, hvordan du kan bruge det i din organisation:

|Industri | Eksempler |
|---------|---------|
|Finansielle tjenester    |  Virtuelle aftaler for fjernsalg og -tjeneste<br/>Planlæg og administrer aftaler for bankrelationschefer, finansielle rådgivere og kravjusteringer for blot at nævne nogle få for at betjene dine kunder med øget effektivitet og bekvemmelighed.  |
|Detailhandel   | Virtuelle fittings og konsultationer <br/>Planlæg og administrer aftaler for dine salgspartnere, produkteksperter og designkonsulenter for at gennemføre virtuelle fittings og konsultationer med kunderne.   |
|Sundhedspleje   |  Virtuelle aftaler til patientpleje <br/>Planlæg og administrer aftaler, så dine medlemmer af plejeteamet kan mødes med patienter eller andre udbydere af sundhedspleje for at drøfte lægebehandling.   |

I denne artikel får du et overblik over, hvordan du planlægger, administrerer og foretager virtuelle aftaler ved hjælp af appen Bookings i Teams.

## <a name="before-you-get-started"></a>Før du kommer i gang

Hvis du er administrator, kan du se [Administrer bookingappen i Teams](/microsoftteams/bookings-app-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json) for at få mere at vide om forudsætningerne for at bruge Bookings-appen i Teams, hvordan du styrer adgangen til Bookings i din organisation og anbefalede politik- og administratorindstillinger.

Husk, at det kun er planlæggere i din organisation, der skal have appen Bookings installeret i Teams. Medarbejdere, der udfører eller deltager i virtuelle aftaler, behøver ikke appen. De deltager i aftaler fra deres Teams- eller Outlook-kalender eller ved hjælp af mødelinket i deres mail med reservationsbekræftelse.

## <a name="set-up-a-new-booking-calendar"></a>Konfigurer en ny bookingkalender

### <a name="create-the-booking-calendar"></a>Opret bookingkalenderen

I Teams skal du gå til **Bookings** > **Kom i gang** og derefter vælge **Ny bookingkalender**. Udfyld formularen, og sørg for at vælge den relevante forretningstype for din organisation.

:::image type="content" source="media/bookings-virtual-visits-new-booking-calendar.png" alt-text="Skærmbillede af skærmen ny bookingkalender, der viser virksomhedstyper":::

Hvis du er en større organisation, kan du overveje at oprette mere end én bookingkalender, hvis du vil have, at deltagerne skal modtage en bookingmail fra en bestemt afdeling i stedet for din overordnede organisation.
Du kan få mere at vide under [Opret en Bookings-kalender](https://support.microsoft.com//office/create-a-bookings-calendar-921cfd26-a24d-4aca-9004-561594112148).

> [!NOTE]
> Hvis dette ikke er første gang i appen Bookings, eller hvis du vil arbejde i en eksisterende bookingkalender, skal du i Bookings vælge rullepilen ud for navnet på din organisation og derefter vælge **Eksisterende bookingkalender**. Herfra kan du søge efter det ønskede.

### <a name="add-staff"></a>Tilføj personale

I bookingkalenderen skal du gå til **Flere indstillinger** (...) > **Indstillinger** og derefter vælge **Personale**. Tilføj medarbejdere, og tildel en rolle til hver person, du tilføjer. Du kan føje op til 100 medarbejdere til en bookingkalender.

Appen Bookings kan integreres med Outlook. Når du har tilføjet personale, kan du se deres kalendertilgængelighed og planlægge bookinger for dem. Hvis du vil vide mere, skal du se [Tilføj personale og få vist en Bookings-kalender](https://support.microsoft.com/office/add-staff-and-view-a-bookings-calendar-6c579f61-8adb-4514-9458-021de2023fa0).  

### <a name="create-appointment-types"></a>Opret aftaletyper

Opret specifikke aftaletyper for at repræsentere de tjenester, der tilbydes af din organisation, og for at skræddersy bookingoplevelsen. Planlæggere kan derefter bruge aftaletypen til at planlægge en aftale.

I bookingkalenderen skal du gå til **Flere indstillinger** (...) > **Indstillinger**, vælge **Aftaletyper** og derefter vælge **Tilføj aftaletype**. Angiv et navn&mdash;, f.eks. åbning af konto, fornyelse af recept, høring af lån, skatteforberedelse&mdash;og andre oplysninger og indstillinger, du ønsker.

De oplysninger, du tilføjer, er inkluderet i mailbekræftelsen, der sendes til deltagerne, hver gang denne type aftale bestilles. Du kan angive mailpåmindelser og andre indstillinger, f.eks. om deltagerne kan [deltage fra en skrivebords- eller mobilbrowser](browser-join.md) uden at skulle downloade Teams.

Hvis du er administrator af Bookings, kan du oprette et link til op til fire formularer, som deltagerne kan udfylde, hver gang denne aftaletype bookes. Du kan f.eks. kræve, at deltagerne udfylder en registreringsformular, før de deltager i en aftale. Hvis du vil sammenkæde en formular, skal du vælge **Sammenkæde en formular**. Angiv URL-adressen til formularen, og vælg derefter **Link**. Hvis det er første gang, du sammenkæder en formular, bliver du bedt om at oprette en Microsoft 365-gruppe til lagring af formularer. Vælg **Opret gruppe** for at oprette gruppen. Du behøver kun at gøre dette én gang for bookingkalenderen.)

Når du arbejder med formularer, skal du være opmærksom på, at:

- Hvis du vil foretage ændringer i en formular, der allerede er sammenkædet med en aftaletype, skal du vælge formularen i aftaletypen eller i Microsoft 365-gruppen på [https://forms.office.com](https://forms.office.com).
- Overførsel af filer til formularer, der indeholder et [spørgsmål om filupload](https://support.microsoft.com/office/add-questions-that-allow-for-file-uploads-6a75a658-c02b-450e-b119-d068f3cba4cf) , understøttes, når alle deltagere er fra samme organisation.

Når en planlægger bruger aftaletypen til at planlægge en aftale, kan vedkommende vælge at inkludere formularen, fjerne den eller tilføje andre formularer, som du har knyttet til aftaletypen. Deltagerne skal udfylde formularen, før de deltager i aftalen.

> [!NOTE]
> Hvis du er sundhedsudbyder, skal oplysninger fra dig eller patienter i Teams (herunder formularappen, Bookings-appen, mødeoptagelser, hvis de er aktiveret af dig eller andre virtuelle Teams-aftaler), der er nødvendige for kontinuitets- eller opbevaringsformål, downloades, kopieres og/eller noteres direkte i sådanne poster af dig. Denne tjeneste vedligeholder ikke juridiske journaler eller et angivet postsæt.

Du kan få mere at vide under [Opret en aftaletype](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887).

## <a name="schedule-an-appointment"></a>Planlæg en aftale

Vælg **Ny booking** i bookingkalenderen. Vælg en aftaletype, og udfyld derefter de relevante oplysninger.

Dette omfatter kontaktoplysninger for deltagere, den medarbejder, der skal levere tjenesten, interne noter, som kun medarbejdere kan se, mailpåmindelser, og om deltageren kan deltage fra en mobilbrowser. Hvis en formular er sammenkædet med aftaletypen, kan du vælge at medtage den, fjerne den eller tilføje andre sammenkædede formularer.

Den mailbekræftelse, der sendes til deltageren, indeholder mødelinket og en vedhæftet fil, så de kan føje den virtuelle aftale til deres kalender. Personalet modtager også en mailbekræftelse og en mødeindkaldelse. Hvis en formular var inkluderet i aftalen, kan Bookings-administratorer og -planlæggere se, om formularen blev udfyldt af deltageren før aftalen og kan få vist deltagerens svar.

Du kan få mere at vide under [Planlæg en booking i Teams Bookings-appen](https://support.microsoft.com/office/schedule-a-booking-in-the-teams-bookings-app-e275049d-0d0f-4161-8526-461a9f29439f).

## <a name="conduct-an-appointment"></a>Foretag en aftale

I din Teams- eller Outlook-kalender skal du gå til bookingen og derefter vælge **Deltag** eller Teams-mødelinket. Kontrollér dine lyd- og videoindstillinger, og vælg derefter **Deltag nu**. Du kan få mere at vide under [Foretag en bookingaftale](https://support.microsoft.com/office/conduct-a-bookings-appointment-a86a4007-e26c-4909-9893-f7036e2747cd).

## <a name="monitor-appointments-and-get-real-time-status-updates"></a>Overvåg aftaler, og få statusopdateringer i realtid

[Køvisningen](https://support.microsoft.com/office/queue-view-in-bookings-3eea2840-a1e0-4bcd-8e09-d3cf51c184d6) i Bookings giver dine medarbejdere et dashboard til at overvåge alle virtuelle aftaler for dagen med opdateringer i realtid. Hvis du vil se køen, skal du gå til fanen **Kø** i Bookings.

:::image type="content" source="media/bookings-virtual-visits-queue.png" alt-text="Skærmbillede af køvisningen i Appen Bookings i Teams" lightbox="media/bookings-virtual-visits-queue.png":::

Fra køen kan planlæggere tilføje en ny booking, få vist relevante aftaleoplysninger og se aftalestatusser i løbet af dagen. Når en patient tilmelder sig venteværelset, ændres status, og deres ventetid vises og spores. Visningen opdateres automatisk med farvekodede opdateringer, så ændringer nemt kan identificeres.

Personalet kan endda deltage i og administrere aftaler direkte fra køen.

> [!NOTE]
> Appen Bookings understøtter i øjeblikket at tilføje op til 100 medarbejdere pr. bookingkalender. Hvis du har brugt Graph-API'er til at konfigurere og føje personale til en bookingkalender, gennemtvinges denne grænse muligvis ikke. I dette scenarie kan fanen **Kø** ikke gengive indhold for kalendere med mere end 100 medarbejdere. For at opnå en optimal oplevelse anbefaler vi, at du ikke føjer mere end 100 medarbejdere til en bookingkalender. Vi arbejder på at løse denne begrænsning i fremtidige versioner.

## <a name="additional-capabilities-with-the-bookings-web-app"></a>Yderligere funktioner med Bookings-webappen

Bookings-webappen giver dig yderligere funktioner. Du kan f.eks. publicere en selvbetjent onlinebookingside, hvor folk kan planlægge aftaler med dine medarbejdere. Hvis du vil have adgang til Bookings-webappen, skal du gå til **Flere indstillinger** (...) > **Åbn Bookings-webapp**.

Du kan få mere at vide under [Microsoft Bookings](/microsoft-365/bookings/bookings-overview).

## <a name="get-insight-into-virtual-appointments-usage"></a>Få indsigt i brug af virtuelle aftaler

[Brugsrapporten for virtuelle besøg](virtual-visits-usage-report.md) i Microsoft Teams Administration giver administratorer et overblik over Teams-aktiviteter med virtuelle aftaler i din organisation. Rapporten viser detaljerede analyser for virtuelle aftaler, herunder Bookings-aftaler.

Du kan få vist vigtige målepunkter, f.eks. lobbyventetid og aftalevarighed. Brug disse oplysninger til at få indsigt i brugstendenser for at hjælpe dig med at optimere virtuelle aftaler for at levere bedre forretningsresultater.

## <a name="related-articles"></a>Relaterede artikler

- [Administrer joinoplevelsen for virtuelle Teams-aftaler i browsere](browser-join.md)

- [Brugsrapport for virtuelle teams-besøg](virtual-visits-usage-report.md)

- [Kom i gang med Teams til sundhedssektoren](teams-in-hc.md)

- [Hjælp-dokumentation til Bookings-appen i Teams](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5)
