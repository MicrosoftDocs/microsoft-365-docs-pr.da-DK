---
title: Sådan fungerer automatiseret undersøgelse og svar i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: automatiseret svar på hændelser, undersøgelse, afhjælpning, trusselsbeskyttelse
ms.date: 01/29/2021
description: Se, hvordan automatiserede undersøgelses- og svarfunktioner fungerer i Microsoft Defender for Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78dc31c055f563f0f9f03bcf12642296459de491
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974229"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Sådan fungerer automatiseret undersøgelse og svar i Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Når sikkerhedsbeskeder udløses, er det op til dit team af sikkerhedshandlinger at undersøge disse beskeder og tage skridt til at beskytte din organisation. Nogle gange kan teams for sikkerhedshandlinger føle sig overvældet over mængden af beskeder, der udløses. Automatiserede air-funktioner (investigation and response) i Microsoft Defender for Office 365 kan hjælpe.

AIR gør det muligt for dit sikkerhedsteam at arbejde mere effektivt og effektivt. AIR-funktioner omfatter automatiserede undersøgelsesprocesser som svar på velkendte trusler, der findes i dag. Passende afhjælpningshandlinger afventer godkendelse, hvilket gør det muligt for dit team af sikkerhedshandlinger at reagere på registrerede trusler.

I denne artikel beskrives det, hvordan AIR fungerer gennem flere eksempler. Når du er klar til at komme i gang med at bruge AIR, skal du se [Undersøg og reager automatisk på trusler](office-365-air.md).

- [Eksempel 1: En brugerrapporteret phishmeddelelse starter en undersøgelseslegebog](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Eksempel 2: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Eksempel 3: Et team af sikkerhedshandlinger integrerer AIR med deres SIEM ved hjælp af API'en til administration af Office 365](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Eksempel: En brugerrapporteret phishmeddelelse starter en undersøgelses legebog

Lad os antage, at en bruger i din organisation modtager en mail, som de mener er et forsøg på phishing. Brugeren, der er oplært i at rapportere sådanne meddelelser, bruger [tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md) eller [tilføjelsesprogrammet Rapport phishing](enable-the-report-phish-add-in.md) til at sende det til Microsoft til analyse. Indsendelsen sendes også til dit system og er synlig i Stifinder i visningen **Indsendelser** (tidligere kaldet den **brugerrapporterede** visning). Desuden udløser den brugerrapporterede meddelelse nu en systembaseret informationsadvarsel, som automatisk starter undersøgelsens playbook.

Under den grundlæggende undersøgelsesfase vurderes forskellige aspekter af mailen. Disse aspekter omfatter:

- En beslutsomhed om, hvilken type trussel det kan være;
- Who sendte den.
- Hvor mailen blev sendt fra (sender infrastruktur);
- Om andre forekomster af mailen blev leveret eller blokeret;
- En vurdering fra vores analytikere;
- Om mailen er knyttet til kendte kampagner;
- og meget mere.

Når rodundersøgelsen er fuldført, indeholder playbooken en liste over anbefalede handlinger, der skal udføres på den oprindelige e-mail og enheder, der er knyttet til den.

Derefter udføres flere trusselsundersøgelser og jagttrin:

- Lignende mails identificeres via e-mailklyngesøgninger.
- Signalet deles med andre platforme, f.eks[. Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Det afgøres, om nogen brugere har klikket gennem skadelige links i mistænkelige mails.
- En kontrol udføres på tværs af Exchange Online Protection ([EOP](exchange-online-protection-overview.md) og ([Microsoft Defender for Office 365](defender-for-office-365.md) for at se, om der er andre lignende meddelelser rapporteret af brugere.
- Der foretages en kontrol for at se, om en bruger er blevet kompromitteret. Denne kontrol udnytter signaler på tværs af Office 365, [Microsoft Defender for Cloud Apps](/cloud-app-security) og [Azure Active Directory](/azure/active-directory) og korrelerer eventuelle relaterede uregelmæssigheder i brugeraktivitet.

I jagtfasen tildeles risici og trusler forskellige jagttrin.

Afhjælpning er den sidste fase af playbook. I denne fase udføres afhjælpningsforanstaltninger baseret på undersøgelses- og jagtfaser.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer

Ud over automatiserede undersøgelser, der udløses af en besked, kan organisationens team for sikkerhedshandlinger udløse en automatisk undersøgelse fra en visning i [Threat Explorer](threat-explorer.md). Denne undersøgelse opretter også en besked, så Microsoft 365 Defender hændelser og eksterne SIEM-værktøjer kan se, at denne undersøgelse blev udløst.

Lad os f.eks. antage, at du bruger visningen **Malware** i Stifinder. Ved hjælp af fanerne under diagrammet skal du vælge fanen **Mail** . Hvis du vælger et eller flere elementer på listen, aktiveres knappen **+ handlinger** .

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="Stifinder med markerede meddelelser" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::

Ved hjælp af menuen **Handlinger** kan du vælge **Undersøgelse af udløser**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Menuen Handlinger for markerede meddelelser" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

På samme måde som med playbooks, der udløses af en besked, omfatter automatiske undersøgelser, der udløses fra en visning i Stifinder, en rodundersøgelse, trin til at identificere og korrelere trusler og anbefalede handlinger til at afhjælpe disse trusler.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Eksempel: Et team af sikkerhedshandlinger integrerer AIR med deres SIEM ved hjælp af API'en til administration af Office 365

AIR-funktioner i Microsoft Defender for Office 365 omfatter [rapporter & oplysninger](air-view-investigation-results.md), som sikkerhedsteams kan bruge til at overvåge og håndtere trusler. Men du kan også integrere AIR-funktioner med andre løsninger. Eksempler omfatter et SIEM-system (Security Information and Event Management), et sagsstyringssystem eller en brugerdefineret rapporteringsløsning. Disse typer integrationer kan udføres ved hjælp af [API'en Office 365 managementaktivitet](/office/office-365-management-api/office-365-management-activity-api-reference).

For nylig har en organisation f.eks. konfigureret en måde for deres team for sikkerhedshandlinger på for at få vist brugerrapporterede phish-beskeder, der allerede er behandlet af AIR. Deres løsning integrerer relevante beskeder med organisationens SIEM-server og deres sagsstyringssystem. Løsningen reducerer antallet af falske positiver markant, så deres sikkerhedsteam kan fokusere deres tid og kræfter på reelle trusler. Hvis du vil vide mere om denne brugerdefinerede løsning, skal du se [Tech Community-bloggen: Gør din SOC mere effektiv med Microsoft Defender for Office 365 og O365 Management-API'en](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Næste trin

- [Kom i gang med at bruge AIR](office-365-air.md)
- [Vis ventende eller fuldførte afhjælpningshandlinger](air-review-approve-pending-completed-actions.md)
