---
title: Kom i gang med Microsoft 365 til sundhedssektoren
author: samanro
ms.author: samanro
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365solution-healthcare
- m365solution-overview
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ''
description: Få mere at vide om telemedicinfunktionerne i Microsoft 365 og Microsoft Teams, og hvordan du kan implementere dem i din sundhedsorganisation.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 0ce08e71a2bec105b2c9f2efe59cc7f440225b4e
ms.sourcegitcommit: 1efb75d033860977239b479f92e7eaf274b5fbf0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2022
ms.locfileid: "66827161"
---
# <a name="get-started-with-microsoft-365-for-healthcare-organizations"></a>Kom i gang med Microsoft 365 til sundhedssektoren

Microsoft 365 og Microsoft Teams tilbyder en række telemedicinfunktioner, der er nyttige for hospitaler og andre sundhedsorganisationer. Teams-funktioner er under udvikling for at hjælpe hospitaler med:

- Virtuelle aftaler og ehr-integration (Electronic Healthcare Record)
- Teams-politikpakker
- Sikre beskeder
- Teams-skabeloner
- Plejekoordinering og samarbejde

> [!NOTE]
> Denne funktionalitet er også en del af Microsoft Cloud for Healthcare. Få mere at vide om brug af denne løsning, der samler funktioner fra Azure, Dynamics 365 og Microsoft 365 på [Microsoft Cloud for Healthcare](/industry/healthcare).

Se følgende video for at få mere at vide om, hvordan du bruger samlingen af sundhedstjenester til at forbedre samarbejdet mellem sundhedsteams i Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hqan]

For at få mest muligt ud af din sundhedsorganisation skal du først vælge, hvilke scenarier Microsoft 365 og Microsoft Teams kan hjælpe dig med i dine daglige aktiviteter, og derefter sørge for, at du forbereder dit Teams-miljø med de rette grundlæggende funktioner, teams og apps til at understøtte disse scenarier.

1. [Vælg de scenarier](#scenarios-for-healthcare) , du vil implementere.
2. [Konfigurer Microsoft 365](flw-setup-microsoft-365.md) – Konfigurer Microsoft 365-kerneelementer, Microsoft Teams og andre tjenester, du har brug for.
3. [Konfigurer tjenester og apps](flw-setup-microsoft-365.md#step-5-configure-apps-for-your-scenario) – Brug teamskabeloner til hurtigt at konfigurere de teams, du har brug for, herunder de kanaler og apps, du har brug for til din virksomhed. Tilføj andre apps fra Microsoft efter behov for at understøtte dine scenarier.

## <a name="scenarios-for-healthcare"></a>Scenarier til sundhedssektoren

Følgende scenarier er tilgængelige for sundhedsorganisationer:

| Scenario | Beskrivelse | Krav |
| -------- | -------- | -------- |
| [Virtuelle aftaler med ehr-integration (Electronic Healthcare Record)](#virtual-appointments-and-electronic-healthcare-record-ehr-integration) | Planlæg, administrer og udfør virtuelle aftaler med patienter. Dette scenarie forbinder Teams og Cerner- eller Epic-platformen for at understøtte virtuelle aftaler. | Aktivt abonnement på Microsoft Cloud for Healthcare eller abonnement på separat tilbud på Microsoft Teams EHR-connector. <br> Brugerne skal have en passende Licens til Microsoft 365 eller Office 365, der omfatter Teams-møder*. <br> Organisationer skal have Cerner-version november 2018 eller nyere eller Epic version november 2018 eller nyere. <br>Oplysninger om [Kravene til Cerner EHR](ehr-admin-cerner.md#before-you-begin) og [Epic EHR](ehr-admin-epic.md#before-you-begin) |
| [Virtuelle aftaler med Microsoft Bookings og appen Bookings](#virtual-appointments-and-electronic-healthcare-record-ehr-integration) | Planlæg, administrer og udfør virtuelle aftaler med patienter. Dette scenarie er afhængig af, at Microsoft Bookings understøtter virtuelle aftaler. | Microsoft Bookings skal være aktiveret for organisationen. <br> Alle brugere af Bookings-appen og alle medarbejdere, der deltager i møder, skal have en licens, der understøtter Teams-mødeplanlægning*. <br>[Oplysninger om bookingkrav](/microsoftteams/bookings-app-admin#prerequisites-to-use-the-bookings-app-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)|
| [Plejekoordinering og samarbejde](#care-coordination-and-collaboration) | Klinikere og medarbejdere kan samarbejde internt om tidsplaner, dokumenter, opgaver osv.| Brugerne skal have en passende licens*. |

*Office 365 A3, A5, E3, E5, F1, F3, Microsoft 365 A3, A5, E3 og E5, Business Standard understøttes. Du kan få flere oplysninger om generelle Teams-licenser under [Administrer brugeradgang til Teams](/microsoftteams/user-access).

Eller vælg mellem andre [scenarier](flw-choose-scenarios.md) for Microsoft 365 til frontlinjemedarbejdere, f.eks [. virksomhedskommunikation](flw-corp-comms.md) eller [trivsel og engagement](flw-wellbeing-engagement.md).

Og udnyt disse funktioner, der hjælper Microsoft Teams med at arbejde for din sundhedsorganisation:

| Funktion | Beskrivelse | Krav |
| -------- | -------- | -------- |
| [Teams-politikpakker](#teams-policy-packages)| Sørg for, at kliniske medarbejdere, informationsmedarbejdere og enheder i patientrum har den relevante adgang til Teams-funktionalitet.| Brugerne skal have en passende licens*. |
| [Sikre beskeder](#secure-messaging) | Få hurtigere opmærksomhed på vigtige meddelelser, og hav tillid til, at meddelelsen blev modtaget og læst. | Brugerne skal have en passende licens*.  |
| [Teams-skabeloner](#teams-templates-for-healthcare-organizations) | Opret teams, der indeholder en foruddefineret skabelon med indstillinger, kanaler og forudinstallerede apps til kommunikation og samarbejde i en afdeling, en afdeling eller mellem flere afdelinger, pods og afdelinger på et hospital. | Brugerne skal have en passende licens*.  |

## <a name="virtual-appointments-and-electronic-healthcare-record-ehr-integration"></a>Virtuelle aftaler og ehr-integration (Electronic Healthcare Record)

Brug den komplette mødeplatform i Teams til at planlægge, administrere og udføre virtuelle aftaler med patienter.

- Hvis din organisation allerede bruger elektroniske tilstandsposter eller EHR, kan du integrere Teams for at få en mere problemfri oplevelse. Teams EHR-connector (Electronic Health Record) gør det nemt for klinikere at starte en virtuel patientaftale eller konsultation med en anden udbyder i Teams direkte fra EHR-systemet. Du kan få mere at vide under [Virtuelle aftaler med Teams – integration i Cerner EHR](ehr-admin-cerner.md) og [virtuelle aftaler med Teams – integration i Epic EHR](ehr-admin-epic.md).
- Hvis du ikke bruger en understøttet EHR, kan du bruge Microsoft Bookings og appen Bookings i Teams. Du kan få mere at vide under [Virtuelle aftaler med Teams og appen Bookings](bookings-virtual-visits.md).

![Virtuelle aftaler med Microsoft Teams.](media/virtual-visits-teams.png)

## <a name="teams-policy-packages"></a>Teams-politikpakker

Anvend Teams-politikpakker til at definere, hvad forskellige roller kan gøre i Teams. Angiv f.eks. politikker for:

- Kliniske arbejdstagere, f.eks. registrerede sygeplejersker, leder sygeplejersker, læger og socialarbejdere, så de kan få fuld adgang til chat, opkald, skiftstyring og møder.
- It-medarbejdere i din sundhedsorganisation, f.eks. it-medarbejdere, it-medarbejdere, økonomiafdelingen og overholdelsesofficerer, kan have fuld adgang til chat, opkald og møder.
- Patientrum, til at styre indstillinger for enheder i patientrum.

Du kan få mere at vide under [Teams-politikpakker til sundhedssektoren](/microsoftteams/policy-packages-healthcare?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

## <a name="secure-messaging"></a>Sikre beskeder

Sikre beskeder understøtter samarbejde i tilstandsteams, herunder flere nye funktioner:

- En afsender af en meddelelse kan angive en særlig prioritet for sin meddelelse, så modtageren får besked gentagne gange, indtil vedkommende læser meddelelsen.
- En afsender af en meddelelse kan anmode om en kvittering for læsning, så vedkommende får besked, når en meddelelse, de har sendt, blev læst af meddelelsens modtager.

Tilsammen giver disse funktioner hurtigere opmærksomhed på vigtige meddelelser og tillid til, at meddelelsen blev modtaget og læst. Nye sundhedsteams, der bruger disse funktioner, kan oprettes pr. patient. Disse funktioner er politikbaserede og kan tildeles til enkeltpersoner eller hele Teams.

Du kan få mere at vide under [Kom i gang med Secure Messaging-politikker for sundhedssektorens organisationer](messaging-policies-hc.md).

Relateret til sikre beskeder er også muligheden for at have andre lejere i sundhedssektorens organisationsnetværk, hvilket giver mulighed for bedre kommunikation mellem lejere. (Se [Administrer eksterne møder og chat i Microsoft Teams](/microsoftteams/manage-external-access)).

## <a name="teams-templates-for-healthcare-organizations"></a>Teams-skabeloner til sundhedsorganisationer

Teams indeholder skabeloner, der er udviklet specielt til sundhedssektoren, hvilket gør det nemmere at oprette teams, så medarbejderne kan kommunikere og samarbejde om patientpleje eller driftsmæssige behov. Du kan få mere at vide under [Brug skabeloner til sundhedsteams](/microsoftteams/expand-teams-across-your-org/healthcare/healthcare-templates-admin-console?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

## <a name="care-coordination-and-collaboration"></a>Plejekoordinering og samarbejde

Samarbejd dit sundhedsteam for at koordinere pleje og samarbejde med Teams.

![Sundhedssektoren: Samarbejd med dit sundhedsteam i Teams.](media/teams-healthcare-collaborate-in-teams.png)

Teams gør det muligt for læger, klinikere, sygeplejersker og andre medarbejdere at samarbejde effektivt med inkluderede samarbejdsfunktioner i Teams, f.eks.:

- Konfigurer teams og kanaler til dine sundhedsteams og informationsmedarbejdere. Brug kanaler med faner som en måde at strukturere deres arbejde på med yderligere hjælp fra faner, som de kan fastgøre informationskilder til.
- Chat, send meddelelser og kommuniker. Dit team kan have vedvarende samtaler om forskellige patienter, der har brug for opmærksomhed.
- Ring til og mød medlemmer af sundhedsteamet. Konfigurer individuelle møder, eller brug kanalmøder til at administrere daglige møder, både med styrken ved Teams-lyd, video, skærmdeling, optagelse og transskriptionsfunktioner.
- Gem og del filer og dokumenter. Dit tilstandsteam er en del af et enkelt virtualiseret team, der arbejder og samarbejder om Office-dokumenter.

Derudover kan dit team bruge apps i Teams til at:

- Del lister, og spor oplysninger med appen Lister
- Spor og overvåg opgaver med appen Opgaver
- Strømline godkendelser med appen Godkendelser
- Opret, administrer og del tidsplaner med appen Skift

### <a name="share-lists-and-track-information-with-the-lists-app"></a>Del lister, og spor oplysninger med appen Lister

Appen Lister i Teams hjælper teams med at spore oplysninger og organisere arbejde. Appen er forudinstalleret for alle Teams-brugere og er tilgængelig som en fane i alle team og kanaler. Lister kan oprettes fra bunden, fra foruddefinerede skabeloner eller ved at importere data til Excel.

Sundhedsteams kan bruge skabelonen Patienter til at komme i gang. De kan oprette lister for at spore patienternes behov og status. Eksisterende patientdata i Excel-regneark kan hentes for at oprette en liste i Teams. Disse lister kan bruges til scenarier som runder og patientovervågning til at koordinere behandlingen.

En anlæggelsessygeplejerske opretter f.eks. en patientliste i et team, der omfatter alle medlemmer af sundhedsteamet. Under runder får sundhedsteamet adgang til Teams på deres mobilenheder og opdaterer patientoplysninger på listen, som alle i teamet kan se for at holde sig synkroniseret. Ved afrundingssessioner, hvor sundhedsteamet indsamler for at diskutere og evaluere vigtige målepunkter for tilstandsydeevnen for at sikre, at en patient er på den rette glidesti til udledning, kan de dele disse oplysninger ved hjælp af Teams på en stor skærm. medlemmer af sundhedsteamet, der ikke er på webstedet, kan tilmelde sig eksternt.

Her er et eksempel på en liste, der blev konfigureret til patientrunding.

:::image type="content" source="media/lists-patients-example.png" alt-text="Skærmbillede af eksempelliste til patientafrunding.":::

Du kan få mere at vide under [Administrer appen Lister for din organisation i Teams](/microsoftteams/manage-lists-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

### <a name="track-and-monitor-tasks-with-the-tasks-app"></a>Spor og overvåg opgaver med appen Opgaver

Brug [Opgaver](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070) i Teams til at spore, om der skal udføres elementer for hele tilstandsteamet. Dit tilstandsteam kan til enhver tid oprette, tildele og planlægge opgaver, kategorisere opgaver og opdatere status fra alle enheder, der kører Teams. It-teknikere og administratorer kan også publicere opgaver til bestemte teams for din organisation. Du kan f.eks. publicere et sæt opgaver for nye sikkerhedsprotokoller eller et nyt indtagstrin, der skal bruges på tværs af et hospital.

Du kan få mere at vide under [Administrer appen Opgaver for din organisation i Microsoft Teams](/microsoftteams/manage-tasks-app?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)

### <a name="streamline-approvals-with-the-approvals-app"></a>Strømline godkendelser med appen Godkendelser

Brug [Godkendelser](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3) til at strømline alle dine anmodninger og processer med dit team. Opret, administrer og del godkendelser direkte fra din hub til teamwork. Start et godkendelsesflow fra det samme sted, hvor du sender en chatsamtale, i en kanalsamtale eller fra selve appen Godkendelser. Du skal blot vælge en godkendelsestype, tilføje detaljer, vedhæfte filer og vælge godkendere. Når godkenderne er indsendt, får de besked og kan gennemse og reagere på anmodningen.

Du kan tillade appen Godkendelser for din organisation og føje den til dine teams. Du kan få mere at vide [under Administrer appen Godkendelser](/microsoftteams/approval-admin?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

### <a name="create-manage-and-share-schedules-with-the-shifts-app-and-frontline-worker-integration"></a>Opret, administrer og del tidsplaner med appen Skift og integration af Frontline Worker

Teams kan integreres med appen Shifts og Frontline Worker, som kan bruges til at koordinere funktioner for skiftehold og meget mere. I skiftehold kan sygeplejerskeledere f.eks. oprette og koordinere tidsplaner for deres personale, og sygeplejersker kan kontrollere tidsplaner og skifte skiftehold.

Du kan få mere at vide under [Administrer Appen Skift for din organisation i Microsoft Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json).

## <a name="help-your-clinical-and-information-workers-get-going-with-teams"></a>Hjælp dine kliniske medarbejdere og informationsmedarbejdere med at komme i gang med Teams

Der er mange tilgængelige ressourcer, der kan hjælpe alle brugerne i din organisation med at blive fortrolige med at bruge Teams:

- Besøg [Teams Adoption Center](https://adoption.microsoft.com/microsoft-teams/) for at få råd om udrulning af Teams, hvis du lige er begyndt på din organisations rejse med Teams eller udvider Teams til flere områder i din organisation.
- Overvej at konfigurere brugerdefinerede [læringsforløb](https://adoption.microsoft.com/microsoft-365-learning-pathways/) for dine brugere, så de kun dækker de opgaver, de skal udføre.
- Få hjælp og oplæring til dine brugere i, hvordan de udfører grundlæggende opgaver i Teams på [Teams-supportwebstedet](https://support.microsoft.com/teams), herunder [videoer til hurtig oplæring](https://support.microsoft.com/office/microsoft-teams-video-training-4f108e54-240b-4351-8084-b1089f0d21d7). Dette websted har også hjælp og træning til Teams-apps, herunder [lister](https://support.microsoft.com/office/get-started-with-lists-in-teams-c971e46b-b36c-491b-9c35-efeddd0297db), [opgaver](https://support.microsoft.com/office/use-the-tasks-app-in-teams-e32639f3-2e07-4b62-9a8c-fd706c12c070), [godkendelser](https://support.microsoft.com/office/what-is-approvals-a9a01c95-e0bf-4d20-9ada-f7be3fc283d3), [bookinger](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5) og [vagter](https://support.microsoft.com/office/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821).
