---
title: Administrer tidsplanejere for skiftstyring
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
description: Få mere at vide om, hvordan du administrerer skiftejere i forbindelse med planlægningsstyring. Du kan angive en politik for at hæve tilladelsen for et teammedlem til en planejer.
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- microsoftcloud-healthcare
- microsoftcloud-retail
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7e91519820adbefd780f27759c3da4ef31d7cb8f
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823954"
---
# <a name="schedule-owner-for-shift-management"></a>Planlæg ejer af skiftstyring

## <a name="overview"></a>Oversigt

Funktionen Planejer giver dig mulighed for at hæve tilladelserne for et teammedlem, så de kan administrere tidsplaner uden at gøre medarbejderen til teamejer. Med tilladelsen Planejer kan en medarbejder administrere teamets tidsplan uden at kunne ændre andre teamegenskaber, f.eks. opdatering, redigering eller sletning af teamkanaler.

Hvad kan en bruger med tilladelser som ejer af tidsplanen gøre?

- Opret, rediger og publicer tidsplaner for at administrere teamets flyttetildelinger.
- Få vist og godkend skiftanmodninger, herunder anmodninger om at skifte skiftehold og tage åbne vagter.
- Administrer indstillinger i Skift for at aktivere visse funktioner for teamet.
- Få vist og rediger teamets timeseddel for at behandle medarbejderlønninger.

## <a name="why-schedule-owner"></a>Hvorfor planejer?

Uden funktionen Planlæg ejer kan daglige forretningsfunktioner blive forstyrret. Selvom teamejeren hjælper med at køre teamet, er de muligvis ikke nødvendigvis den person, der er ansvarlig for den daglige planlægning. I dette tilfælde strømliner overførsel af kun ansvaret for planlægning til et andet teammedlem de daglige handlinger i teamet og fjerner forvirringen mellem to teammedlemmer, der har de samme adgangsrettigheder.

## <a name="scenario"></a>Scenario

Her er et eksempel på, hvordan din organisation kan bruge funktionen Planlæg ejer.

Du arbejder i en stor organisation, hvor afdelingsledere rapporterer direkte til butikschefen. Butikschefen har større autoritet i din virksomhed og er teamejer i Skiftehold. Afdelingschefer føjes til gengæld kun til vagter som teammedlemmer. Selvom butikschefer har mere anciennitet end afdelingschefer, giver det mere mening for afdelingschefer at håndtere den daglige planlægning af teamets medarbejdere.

*Uden Planejer* skal afdelingschefer have nøjagtigt de samme rettigheder som teamejeren. Afdelingsledere har for nylig flyttet rundt på oplysninger og ændret navnet på kanaler, og det har medført komplikationer med butikschefens arbejde. Butikschefen ønsker, at afdelingslederne skal kunne organisere deres tidsplaner, men ikke ønsker, at de skal kunne ændre andet i teamet uden for Skift.

*Med Planejer* kan afdelingslederne tildeles planlægningsrettigheder uden andre teamejerrettigheder.

## <a name="manage-schedule-ownership"></a>Administrer ejerskab af tidsplan

Som administrator bruger du politikker til at styre ejerskabet af planlægningsadministrationen i din organisation. Du administrerer disse politikker ved hjælp af følgende PowerShell-cmdlet'er:

- [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy?view=teams-ps)
- [Get-CsTeamsShiftsPolicy](/powershell/module/teams/get-csteamsshiftspolicy?view=teams-ps)
- [Set-CsTeamsShiftsPolicy](/powershell/module/teams/set-csteamsshiftspolicy?view=teams-ps)
- [Grant-CsTeamsShiftsPolicy](/powershell/module/teams/grant-csteamsshiftspolicy?view=teams-ps)
- [Remove-CsTeamsShiftsPolicy](/powershell/module/teams/remove-csteamsshiftspolicy?view=teams-ps)

### <a name="example-1"></a>Eksempel 1

Her opretter vi en ny politik med navnet ScheduleOwnerPolicy, hvor funktionen Planejer er slået til.

```powershell
New-CsTeamsShiftsPolicy –Identity ScheduleOwnerPolicy  -EnableScheduleOwnerPermissions $true -AccessType UnrestrictedAccess_TeamsApp
```

### <a name="example-2"></a>Eksempel 2

I dette eksempel tildeler vi en politik med navnet ScheduleOwnerPolicy til en bruger med navnet remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso.com -PolicyName ScheduleOwnerPolicy
```

## <a name="related-articles"></a>Relaterede artikler

- [Administrer appen Skift for din organisation i Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Administrer skiftbaseret adgang for frontlinjemedarbejdere i Teams](manage-shift-based-access-flw.md)
