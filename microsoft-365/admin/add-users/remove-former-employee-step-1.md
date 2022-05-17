---
title: Trin 1 – Undgå, at en tidligere medarbejder logger på og blokerer adgangen til Microsoft 365-tjenester
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
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Globale administratorer kan blokere en tidligere medarbejder fra at logge på og blokere deres adgang til Microsoft 365-tjenester.
ms.openlocfilehash: eec436a182f5e065f445167dea38fe99390ca105
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436641"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Trin 1 – Undgå, at en tidligere medarbejder logger på og blokerer adgangen til Microsoft 365-tjenester

Hvis du har brug for straks at forhindre en brugers logonadgang, skal du nulstille brugerens adgangskode. I dette trin skal du tvinge brugeren til at logge af Microsoft 365.

> [!NOTE]
> Du skal være global administrator for at kunne starte logon for andre administratorer. For brugere, der ikke er administratorer, kan du bruge en brugeradministrator eller en helpdeskadministratorbruger til at udføre denne handling. [Få mere at vide om administratorrollerne](about-admin-roles.md)

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .
2. Markér afkrydsningsfeltet ud for brugerens navn, og vælg derefter **Nulstil adgangskode**.
3. Angiv en ny adgangskode, og vælg derefter **Nulstil**. (Send den ikke til dem).
4. Vælg brugerens navn for at gå til ruden med egenskaber, og vælg **Log af alle sessioner** under fanen **Konto**.

Inden for en time – eller efter de forlader den aktuelle Microsoft 365 side, de er på – bliver de bedt om at logge på igen. Et adgangstoken er godt i en time, så tidslinjen afhænger af, hvor meget tid der er tilbage på dette token, og om de navigerer ud af deres aktuelle webside.
  
> [!IMPORTANT]
> Hvis brugeren er i Outlook på internettet og blot klikker sig rundt i sin postkasse, bliver vedkommende muligvis ikke smidt ud med det samme. Så snart de vælger et andet felt, f.eks. OneDrive eller opdaterer deres browser, startes logon-out.
  
Hvis du vil bruge PowerShell til at logge af en bruger med det samme, skal du se cmdlet'en [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
Du kan finde flere oplysninger om, hvor lang tid det tager at få en person ud af en mail, under [Hvad du skal vide om at afslutte en medarbejders mailsession](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Bloker en tidligere medarbejders adgang til Microsoft 365-tjenester

> [!IMPORTANT]
 > Det kan tage op til 24 timer, før blokering af en konto træder i kraft. Hvis du har brug for straks at forhindre en brugers logonadgang, skal du følge trinnene ovenfor og nulstille vedkommendes adgangskode.

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .
2. Vælg navnet på den medarbejder, du vil blokere, og vælg symbolet for **Bloker denne bruger** under brugerens navn.
3. Vælg **Bloker brugeren fra at logge på**, og vælg derefter **Gem**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Bloker en tidligere medarbejders adgang til mail (Exchange Online)

Hvis du har en mail som en del af dit Microsoft 365 abonnement, skal du logge på <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> og følge disse trin for at blokere din tidligere medarbejders adgang til deres mail.
  
1. Gå til Exchange Administration > <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">modtagerpostkasser</a>\>.
1. Vælg brugerpostkassen på listen, og vælg derefter **Administrer indstillinger for mailapps** i *ruden Detaljer* (til højre) under **Mailapps**. **Slå** skyderen fra for alle indstillingerne. **Mobil (Exchange ActiveSync)**, **Outlook på internettet**, **Outlook desktop (MAPI)**, **Exchange webtjenester**, **POP3** og **IMAP**.
1. Vælg **Gem**.

## <a name="related-content"></a>Relateret indhold

[Exchange Administration i Exchange Online](/exchange/exchange-admin-center) (artikel)\

[Gendan en bruger](restore-user.md) (artikel)
