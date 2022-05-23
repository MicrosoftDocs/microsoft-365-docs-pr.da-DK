---
title: Trin 7 – Slet en tidligere medarbejders brugerkonto
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Når du har gemt og fået adgang til alle en tidligere medarbejders brugerdata, kan du slette den tidligere medarbejders konto i Microsoft 365 Administration.
ms.openlocfilehash: 5a1929ef1a5ff26ee0e84993f0a7cabb5ebc4617
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636168"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>Trin 7 – Slet en tidligere medarbejders brugerkonto

Når du har gemt og fået adgang til alle den tidligere medarbejders brugerdata, kan du slette den tidligere medarbejders konto.

> [!IMPORTANT]
> Slet ikke kontoen, hvis du har konfigureret videresendelse af mail eller konverteret den til en delt postkasse. Begge skal bruge kontoen for at forankre videresendelses- eller den delte postkasse.

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .
2. Vælg navnet på den medarbejder, du vil slette.
3. Vælg **Slet bruger** under brugerens navn. Vælg de ønskede indstillinger for denne bruger, og vælg derefter **Slet bruger**. Hvis du allerede har givet en anden bruger adgang til denne brugers mail og OneDrive, behøver du ikke at gøre det igen her.

Når du sletter en bruger, bliver kontoen inaktiv i ca. 30 dage. Du har indtil da til at gendanne kontoen, før den slettes permanent.

## <a name="watch-delete-a-former-employees-user-account"></a>Se: Slet en tidligere medarbejders brugerkonto

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

Hvis du har fundet denne video nyttig, kan du se hele [træningsserien for små virksomheder og dem, der ikke er Microsoft 365](../../business-video/index.yml).

## <a name="does-your-organization-use-active-directory"></a>Bruger din organisation Active Directory?

Hvis din organisation synkroniserer brugerkonti til Microsoft 365 fra et lokalt Active Directory-miljø, skal du slette og gendanne disse brugerkonti i din lokale Active Directory-tjeneste. Du kan ikke slette eller gendanne dem i Office 365.

Hvis du vil vide mere om, hvordan du sletter og gendanner en brugerkonto i Active Directory, skal du se [Slet en brugerkonto](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
Hvis du bruger Azure Active Directory, skal du se [PowerShell-cmdlet'en Remove-MsolUser](/powershell/module/msonline/remove-msoluser).
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Det har du brug for at vide om afslutning af en medarbejders mailsession

Her er oplysninger om, hvordan du får en medarbejder ud af mail (Exchange).

<br>

****

|Det kan du gøre|Sådan gør du det|
|:-----|:-----|
|Afslut en session (f.eks. Outlook på internettet, Outlook, Exchange aktiv synkronisering osv.), og tving til at åbne en ny session|Nulstil adgangskode|
|Afslut en session, og bloker adgang til fremtidige sessioner (for alle protokoller)|Deaktiver kontoen. I Exchange Administration eller ved hjælp af PowerShell: <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|Afslut sessionen for en bestemt protokol (f.eks. ActiveSync)|Deaktiver protokollen. I Exchange Administration eller ved hjælp af PowerShell: <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
|

Ovenstående handlinger kan udføres tre steder:
  
<br>

****

|Hvis du afslutter sessionen her|Hvor lang tid det tager|
|---|---|
|I Exchange Administration eller ved hjælp af PowerShell|Den forventede forsinkelse er inden for 30 min.|
|I Azure Active Directory Administration|Den forventede forsinkelse er 60 min.|
|I et lokalt miljø|Den forventede forsinkelse er 3 timer eller mere|
|

### <a name="how-to-get-fastest-response-for-account-termination"></a>Sådan får du hurtigst svar på kontoafslutning

**Hurtigst**: Brug Exchange Administration (brug PowerShell) eller Azure Active Directory Administration. I et lokalt miljø kan det tage flere timer at synkronisere ændringen via DirSync.
  
**Hurtigst for en bruger med tilstedeværelse i det lokale miljø og i Exchange Datacenter**: Afslut sessionen ved hjælp af Azure Active Directory Administration/Exchange Administration, og foretag også ændringen i det lokale miljø. Ellers overskrives ændringen i Azure Active Directory Administration/Exchange Administration af DirSync.
  
## <a name="related-content"></a>Relateret indhold

[Gendan en bruger](restore-user.md) (artikel)

[Nulstil adgangskoder](reset-passwords.md) (artikel)
