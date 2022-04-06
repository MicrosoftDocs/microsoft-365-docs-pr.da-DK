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
description: Bloker en tidligere medarbejder fra at logge på og blokere adgangen til Microsoft 365-tjenester.
ms.openlocfilehash: abd6a6f47952b5af190b08f1ecae337840eaa312
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606534"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Trin 1 – Undgå, at en tidligere medarbejder logger på og blokerer adgangen til Microsoft 365-tjenester

Hvis du har brug for straks at forhindre en brugers logonadgang, skal du nulstille brugerens adgangskode. I dette trin skal du gennemtvinge et log af brugeren fra Microsoft 365.

> [!NOTE]
> Du skal være global administrator for at starte logon for andre administratorer. For brugere, der ikke er administratorer, kan du bruge en brugeradministrator eller en Helpdesk-administratorbruger til at udføre denne handling. [Få mere at vide om administratorroller](about-admin-roles.md)

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.
2. Markér afkrydsningsfeltet ud for brugerens navn, og vælg derefter Nulstil **adgangskode**.
3. Angiv en ny adgangskode, og vælg derefter **Nulstil**. Send den ikke til dem.
4. Vælg brugerens navn for at gå til ruden med egenskaber, **og vælg Log** af **alle sessioner under fanen Konto**.

Inden for en time – eller når de forlader Microsoft 365 side, de er på – bliver de bedt om at logge på igen. Et adgangstoken kan bruges i en time, så tidslinjen afhænger af, hvor meget tid der er tilbage på den pågældende token, og om de navigerer ud af deres aktuelle webside.
  
> [!IMPORTANT]
> Hvis brugeren er i Outlook på internettet, men blot klikker rundt i sin postkasse, bliver han eller hun muligvis ikke smedet ud med det samme. Når de vælger et andet felt, f.eks. OneDrive browser, eller opdaterer deres browser, startes logon.
  
Hvis du vil bruge PowerShell til at logge en bruger af med det samme, skal du se Tilbagekald [AzureADUserAllRefreshToken-cmdlet'en](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
Du kan finde flere oplysninger om, hvor lang tid det tager at få en person væk fra mail, under Hvad du bør vide om at afslutte [en medarbejders mailsession](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Blokere en tidligere medarbejders adgang til Microsoft 365 tjenester

> [!IMPORTANT]
 > Det kan tage op til 24 timer, før blokering af en konto træder i kraft. Hvis du har brug for straks at forhindre en brugers logonadgang, skal du følge trinnene ovenfor og nulstille brugerens adgangskode.

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.
2. Vælg navnet på den medarbejder, du vil blokere, og vælg symbolet for Bloker denne bruger under **brugerens navn**.
3. Vælg **Bloker brugeren fra at logge på**, og vælg derefter **Gem**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Blokere en tidligere medarbejders adgang til mail (Exchange Online)

Hvis du har mail som en del af dit Microsoft 365-abonnement, skal du logge på <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> Administration og følge disse trin for at blokere den tidligere medarbejders adgang til deres mail.
  
1. Gå til Exchange Administration > **Modtageres** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">postkasser</a>.
1. Vælg brugerpostkassen på listen, og vælg derefter Administrer indstillinger for mailapps **under** **Mailapps** i detaljeruden *(i* højre side). Slå **skyderen** fra for alle indstillingerne. **Mobil (Exchange ActiveSync),** **Outlook på internettet**, **Outlook (MAPI)** **og Exchange-webtjenester**, **POP3** **og IMAP**.
1. Vælg **Gem**.

## <a name="related-content"></a>Relateret indhold

[Exchange Administration i Exchange Online](/exchange/exchange-admin-center) (artikel)\

[Gendan en bruger](restore-user.md) (artikel)
