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
keywords: automatiseret hændelsesrespons, undersøgelse, afhjælpning, trusselsbeskyttelse
ms.date: 01/29/2021
description: Se, hvordan automatiserede undersøgelses- og svarfunktioner fungerer i Microsoft Defender for Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7173d45fed25fe1d0d1e93dbcc259046c1f221cd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474261"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>Sådan fungerer automatiseret undersøgelse og svar i Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Når der udløses sikkerhedsadvarsler, er det op til dit sikkerhedsteam at undersøge disse vigtige beskeder og tage skridt til at beskytte din organisation. Nogle gange kan sikkerhedsteams føle sig overvældet af mængden af beskeder, der udløses. Automatiserede undersøgelses- og svarmuligheder (AIR) i Microsoft Defender for Office 365 kan hjælpe.

AIR gør det muligt for dit sikkerhedsteam at fungere mere effektivt. AIR-funktioner omfatter automatiserede undersøgelsesprocesser som reaktion på velkendte trusler, der findes i dag. Relevante afhjælpningshandlinger afventer godkendelse, så dit sikkerhedsteam kan reagere på registrerede trusler.

Denne artikel beskriver, hvordan AIR fungerer gennem flere eksempler. Når du er klar til at gå i gang med at bruge AIR, skal [du se Undersøg og svar automatisk på trusler](office-365-air.md).

- [Eksempel 1: En bruger-rapporteret phish-meddelelse åbner en undersøgelses-playbook](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [Eksempel 2: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [Eksempel 3: Et sikkerhedsteam integrerer AIR med deres SIEM ved hjælp Office 365 Management Activity API](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>Eksempel: En bruger-rapporteret phish-meddelelse starter en undersøgelses-playbook

Antag, at en bruger i organisationen modtager en mail, som brugeren mener er et forsøg på phishing. Brugeren, som er trænet til at rapportere sådanne meddelelser[](enable-the-report-message-add-in.md), bruger tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet [Report Phishing](enable-the-report-phish-add-in.md) til at sende det til Microsoft til analyse. Indsendelsen sendes også til dit system og er synlig i Stifinder i visningen  Indsendelser (tidligere kaldet visningen **Brugerrapporteret**). Desuden udløser den brugerrapporterede meddelelse nu en systembaseret informationsbesked, som automatisk starter undersøgelsens playbook.

I den egentlige undersøgelsesfase vurderes forskellige aspekter af mailen. Disse aspekter omfatter:

- En bestemmelse om, hvilken type trussel det kan være;
- Who har sendt den.
- Hvor mailen blev sendt fra (sendeinfrastruktur);
- Om andre forekomster af mailen blev leveret eller blokeret;
- En vurdering fra vores analytikere;
- Om mailen er knyttet til kendte kampagner;
- og meget mere.

Når rodundersøgelse er afsluttet, indeholder spilbogen en liste over anbefalede handlinger, der kan udføre med de oprindelige mails og enheder, der er knyttet til den.

Dernæst udføres flere trusselsundersøgelse og jagttrin:

- Lignende mails identificeres via søgninger i mailklynger.
- Signalet deles med andre platforme, f.eks[. Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- Der bliver taget beslutning om, hvorvidt nogen brugere har klikket via ondsindede links i mistænkelige mails.
- En kontrol udføres på tværs af Exchange Online Protection ([EOP](exchange-online-protection-overview.md) og ([Microsoft Defender for Office 365 for at](defender-for-office-365.md) se, om der er andre lignende meddelelser, der rapporteres af brugere.
- Der udføres en kontrol for at se, om en bruger er blevet kompromitteret. Denne kontrol udnytter signaler på tværs Office 365, [Microsoft Defender for Cloud Apps](/cloud-app-security) og [Azure Active Directory](/azure/active-directory) og korrelerer eventuelle relaterede brugeraktivitetsnomomier.

I løbet af jagtfasen tildeles risici og trusler til forskellige jagttrin.

Afhjælpning er den sidste fase af spilbogen. I denne fase tages der afhjælpningstrin baseret på undersøgelsen og jagtfaserne.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer

Ud over automatiserede undersøgelser, der udløses af en besked, kan din organisations sikkerhedsteam udløse en automatisk undersøgelse fra en visning i [Threat Explorer](threat-explorer.md).  Denne undersøgelse opretter også en alarm, så Microsoft 365 Defender og eksterne SIEM-værktøjer kan se, at denne undersøgelse er blevet udløst.

Antag f.eks., at du bruger **visningen Malware** i Stifinder. Ved hjælp af fanerne under diagrammet vælger du **fanen** Mail. Hvis du vælger et eller flere elementer på listen, **aktiveres knappen +** Handlinger.

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="Stifinder med markerede meddelelser" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::


Ved hjælp **af menuen** Handlinger kan du vælge **Undersøgelse af udløser**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="Menuen Handlinger for markerede meddelelser" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

På samme måde som afspilningsbøger, der udløses af en besked, omfatter automatiske undersøgelser, der udløses fra en visning i Stifinder, en rodundersøgelse, trin til at identificere og korrelere trusler og anbefalede handlinger til at afhjælpe disse trusler.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>Eksempel: Et sikkerhedsteam integrerer AIR med deres SIEM ved hjælp Office 365 Management Activity API

AIR-funktioner i Microsoft Defender for Office 365 indeholder [& detaljer](air-view-investigation-results.md), som sikkerhedsteams kan bruge til at overvåge og håndtere trusler. Men du kan også integrere AIR-funktioner med andre løsninger. Eksempler omfatter et system til sikkerhedsoplysninger og begivenhedsstyring (SIEM), et sagsstyringssystem eller en brugerdefineret rapporteringsløsning. Disse typer integrationer kan udføres ved hjælp af Office 365 [Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference).

For eksempel har en organisation for nylig konfigureret en måde for deres sikkerhedsteam til at få vist phish-beskeder, som allerede er blevet behandlet af AIR. Deres løsning integrerer relevante beskeder med organisationens SIEM-server og deres sagsstyringssystem. Løsningen reducerer markant antallet af falske positive, så deres sikkerhedsteam kan fokusere deres tid og anstrengelser på reelle trusler. Du kan få mere at vide om denne brugerdefinerede løsning under [Tech Community-blog: Forbedre effektiviteten af din SOC med Microsoft Defender for Office 365 og O365 Management API](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>Næste trin

- [Kom i gang med at bruge AIR](office-365-air.md)
- [Få vist afventende eller fuldførte afhjælpningshandlinger](air-review-approve-pending-completed-actions.md)
