---
title: Administrer skiftbaseret adgang for frontlinjemedarbejdere i Teams
author: LanaChin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du administrerer skiftbaseret adgang i Teams for frontlinjemedarbejdere i din organisation.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 0e8ed4d923375d8d839533b6c69a114c4c53aa28
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859063"
---
# <a name="manage-shift-based-access-for-frontline-workers-in-teams"></a>Administrer skiftbaseret adgang for frontlinjemedarbejdere i Teams

## <a name="overview"></a>Oversigt

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Tilstedeværelse i Microsoft Teams angiver en brugers aktuelle tilgængelighed og status for andre brugere. Frontlinjearbejderes tilstedeværelse er ofte mindre forudsigelig end andre medarbejdere, da deres arbejdstid normalt ikke er den samme hver dag. Som administrator kan du konfigurere Teams til at vise et sæt skiftbaserede tilstedeværelsestilstande for frontlinjemedarbejderne i din organisation for at angive, hvornår de er på og fra skift.

Disse skiftbaserede tilstedeværelsestilstande&mdash;![Et grønt flueben angiver Ved skift.](media/flw-presence-on-shift.png) **Når der skiftes**, ![angiver grå cirkel med x fra skift.](media/flw-presence-off-shift.png) **Fra shift**, ![udfyldt rød cirkel, angiver Optaget](media/flw-presence-busy.png) **optaget**&mdash;er adskilt fra [standardsættet af tilstedeværelsestilstande](/microsoftteams/presence-admins) i Teams. Med disse to sæt tilstedeværelsestilstande kan du konfigurere forskellige oplevelser for personer i din organisation baseret på deres rolle.

Med shift-baseret adgang kan du administrere adgang til Teams, når frontlinjemedarbejdere er på frihold. Du kan f.eks. indstille Teams til at vise en meddelelse, som frontlinjemedarbejdere skal bekræfte, før de kan bruge Teams, når de ikke er på et planlagt skift.  

## <a name="scenario"></a>Scenario

Her er et eksempel på, hvordan din organisation kan administrere skiftbaseret adgang.

Du har frontlinjearbejdere i din organisation, der kun skal betales for timer, de arbejder på et skiftehold, som deres leder har planlagt og godkendt. De skal ikke betales for den tid, de bruger på at arbejde uden for et planlagt skift, hvilket omfatter brug af Teams-appen. Du konfigurerer en brugerdefineret meddelelse med teksten "Din tid i Teams, når du er på frihold, tæller ikke med i de timer, du skal betale", som vises, når frontlinemedarbejdere forsøger at få adgang til Teams, når de er væk fra skift. Hvis de vælger at bruge Teams, klikker de på **Jeg accepterer** med den forståelse, at de ikke bliver betalt for denne gang.

Du har også informationsmedarbejdere i din organisation, der er funktionærer, og som ikke arbejder i skift. Du kan konfigurere dine informationsmedarbejdere til at bruge standardtilstandene for tilstedeværelse i Teams, samtidig med at du giver frontlinjemedarbejdere skiftbaseret tilstedeværelse.

## <a name="shift-based-presence-states"></a>Skiftbaserede tilstedeværelsestilstande

Her er de skiftbaserede tilstedeværelsestilstande.

|Appen er konfigureret |Brugerkonfigureret  |Flere oplysninger  |
|---------|---------|---------|
|![Grønt flueben angiver Ved skift.](media/flw-presence-on-shift.png) Ved skift     |         |Indstilles automatisk i starten af et skiftehold         |
|![Grå cirkel med x, angiver Skift fra](media/flw-presence-off-shift.png) Ikke på skift     |         |Indstilles automatisk i slutningen af et skiftehold         |
|![Udfyldt rød cirkel, angiver Optaget.](media/flw-presence-busy.png) Travl      | ![Udfyldt rød cirkel, angiver Optaget](media/flw-presence-busy.png) Travl         |Indstilles automatisk. Kan også angives manuelt, når frontlinjearbejderen er på skift.|

## <a name="off-shift-access-to-teams"></a>Ikke i skift adgang til Teams

Denne funktion giver dig mulighed for at administrere adgang til Teams, når frontlinjemedarbejdere er på frihold. Du kan indstille Teams til at vise en meddelelse til frontlinjemedarbejdere, hvis de får adgang til Teams, når de ikke er på skift. Frontlinjemedarbejdere skal klikke på **Jeg accepterer** for at bekræfte meddelelsen, før de kan bruge Teams.

Du kan bruge standardmeddelelsen, vælge mellem et sæt foruddefinerede meddelelser eller tilpasse meddelelsen, så den viser den ønskede tekst. Her er standardmeddelelsen:

![Skærmbillede af standardmeddelelsen.](media/shifts-presence-message.png)

Du kan også angive frekvensen, når meddelelsen vises, og angive en udvidet periode mellem, hvornår det første skift starter, eller sidste skift slutter, og hvornår adgangen til Teams er begrænset.

## <a name="manage-shift-based-access"></a>Administrer skiftbaseret adgang

Som administrator bruger du politikker til at styre skiftbaseret tilstedeværelse for frontlinjearbejdere i din organisation. Du administrerer disse politikker ved hjælp af følgende PowerShell-cmdlet'er:

- [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy)
- [Get-CsTeamsShiftsPolicy](/powershell/module/teams/get-csteamsshiftspolicy)
- [Set-CsTeamsShiftsPolicy](/powershell/module/teams/set-csteamsshiftspolicy)
- [Grant-CsTeamsShiftsPolicy](/powershell/module/teams/grant-csteamsshiftspolicy)
- [Remove-CsTeamsShiftsPolicy](/powershell/module/teams/remove-csteamsshiftspolicy)

Brug cmdlet'en New-CsTeamsShiftsPolicy til at oprette en ny politik, angive de ønskede politikindstillinger, og brug derefter Grant-CsTeamsShiftsPolicy-cmdlet'en til at tildele politikken til brugere.

Her er nogle eksempler. Du kan finde detaljerede oplysninger om hver politikindstilling og -parameter, herunder listen over foruddefinerede meddelelser uden for skift, som du kan vælge imellem, i [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-1"></a>Eksempel 1

I dette eksempel opretter vi en ny politik med navnet Off Shift Teams Access Default Message. I denne politik er skiftbaseret tilstedeværelse slået til, og standardmeddelelsen vises, hver gang en bruger, der har fået tildelt denne politik, tilgår Teams, når de er væk fra skift. Brugeren kan bruge Teams, når vedkommende er fri, hvis vedkommende accepterer meddelelsen, og den udvidede periode mellem det første skiftehold starter eller sidste skift slutter, og når adgangen er begrænset, er 10 minutter.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Default Message" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType DefaultMessage -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 10
```

> [!NOTE]
> Brug parameteren **ShiftNoticeMessageType** til at angive den meddelelse, du vil have vist. Hvis du vil se en liste over de foruddefinerede meddelelser, du kan vælge imellem til denne parameter, skal du se [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-2"></a>Eksempel 2 

I dette eksempel opretter vi en ny politik med navnet Off Shift Teams Access Custom Message. I denne politik er skiftbaseret tilstedeværelse slået til, og der vises en brugerdefineret meddelelse, hver gang en bruger, der har fået tildelt denne politik, får adgang til Teams, når de er væk fra skift. Brugeren kan bruge Teams, når vedkommende er fri, hvis vedkommende accepterer meddelelsen, og den udvidede periode mellem det første skiftehold starter eller sidste skift slutter, og når adgangen er begrænset, er 15 minutter.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Custom Message" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType CustomMessage -ShiftNoticeMessageCustom "Your time on Teams when on off shift won't count toward payable hours" -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 15
```

> [!NOTE]
> Brug parameteren **ShiftNoticeMessageType** til at angive den meddelelse, du vil have vist. Du kan få mere at vide under [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-3"></a>Eksempel 3

I dette eksempel opretter vi en ny politik med navnet Off Shift Teams Access Message1. I denne politik er skiftbaseret tilstedeværelse slået til, og følgende foruddefinerede meddelelse vises, hver gang en bruger, der har fået tildelt denne politik, får adgang til Teams, når de er væk fra skift.

  "Din arbejdsgiver godkender eller godkender ikke brugen af dens netværk, applikationer, systemer eller værktøjer af ikke-undtaget eller timelønnet ansatte i deres fridage. Ved at acceptere accepterer du, at din brug af Teams, mens du er fri, ikke er godkendt, og at du ikke vil blive kompenseret." 

Brugeren kan bruge Teams, når vedkommende er fri, hvis vedkommende accepterer meddelelsen, og den udvidede periode mellem det første skiftehold starter eller sidste skiftehold slutter, og når adgangen er begrænset, er tre minutter.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Message1" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType Message1 -AccessType  UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 3
```

> [!NOTE]
> Brug parameteren **ShiftNoticeMessageType** til at angive den meddelelse, du vil have vist. Hvis du vil se en liste over de foruddefinerede meddelelser, du kan vælge imellem til denne parameter, skal du se [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-4"></a>Eksempel 4

I dette eksempel tildeler vi en politik med navnet Off Shift Teams Access Custom Message til en bruger med navnet remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso.com -PolicyName "Off Shift Teams Access Custom Message"
```

## <a name="related-topics"></a>Relaterede emner

- [Administrer appen Skift for din organisation i Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Oversigt over Teams PowerShell](/microsoftteams/teams-powershell-overview)