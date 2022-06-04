---
title: Beskyt Windows-enheder
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: 21e5551f-fa35-4f13-9418-f80d668b6a2b
description: Få mere at vide om konfiguration af indstillingerne for standardenhedspolitikken, som alle Windows-enheder modtager, når de logger på deres arbejds- eller skolekonto.
ms.openlocfilehash: 5ac09788d609752d12a6ae6efadfa8739c5a4f9a
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893077"
---
# <a name="secure-windows-devices"></a>Beskyt Windows-enheder

Målet her er at konfigurere indstillinger, der er en del af standardenhedspolitikken for Windows 10 eller 11. Alle brugere, der opretter forbindelse til en Windows-enhed, herunder mobilenheder og pc'er ved at logge på med deres arbejdskonto, modtager automatisk disse indstillinger. Vi anbefaler, at du accepterer standardpolitikken under konfigurationen og tilføjer politikker senere, som er målrettet bestemte grupper af brugere.

## <a name="before-you-begin"></a>Før du begynder

Før du kan konfigurere Windows-enheder til Microsoft 365 Business Premium-brugere, skal du sørge for, at alle Windows-enheder kører Windows 10 Pro, version 1703 (Creators Update) eller Windows 11 Pro.

Windows 10 Pro (eller Windows 11 Pro) er en forudsætning for installation af Windows 10 Business, som er et sæt cloudtjenester og enhedshåndteringsfunktioner, der komplementerer Windows 10 Pro og Windows 11 Pro, og aktiverer central administration og sikkerhedskontroller i Microsoft 365 Business Premium.

[Få mere at vide om krav til Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro og Windows 11 Pro

Hvis du har Windows-enheder, der kører tidligere versioner af Windows, f.eks. Windows 7 Pro, Windows 8 Pro eller Windows 8.1 Pro, giver dit Microsoft 365 Business Premium-abonnement dig ret til at opgradere disse enheder til Windows 10 Pro eller Windows 11 Pro.
  
Du kan få flere oplysninger om, hvordan du opgraderer Windows-enheder, i følgende artikler:

- [Opgrader Windows Home til Windows 10 eller Windows 11 Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Opgrader til Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)

<!---
Could not find the Win11 equivalent upgrade link.
---> 
  
## <a name="secure-your-windows-10-and-11-devices"></a>Beskyt dine Windows 10- og 11-enheder

Alle indstillinger er som standard **Slået til**. Følgende indstillinger er tilgængelige: <br/><br/>

|Indstilling  <br/> |Beskrivelse  <br/> |
|:-----|:-----|
|Hjælp med at beskytte pc'er mod virus og andre trusler ved hjælp af Microsoft Defender Antivirus  <br/> |Kræver, at Microsoft Defender Antivirus er slået til for at beskytte pc'er mod farerne ved at have forbindelse til internettet.  <br/> |
|Hjælp med at beskytte pc'er mod webbaserede trusler i Microsoft Edge  <br/> |Slår indstillinger i Edge til, der hjælper med at beskytte brugere mod skadelige websteder og downloads.  <br/> |
|Hjælp med at beskytte filer og mapper på pc'er mod uautoriseret adgang med BitLocker  <br/> |BitLocker beskytter data ved at kryptere computerens harddiske og beskytte mod eksponering af data, hvis en computer mistes eller bliver stjålet. Du kan få flere oplysninger under [Ofte stillede spørgsmål om BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Slå enhedsskærmen fra, når den er inaktiv i så lang tid  <br/> |Sikrer, at firmadata er beskyttet, hvis en bruger er inaktiv. En bruger arbejder muligvis på et offentligt sted, f.eks. en café, og træder væk eller bliver distraheret et øjeblik, så enheden er sårbar over for tilfældige blik. Med denne indstilling kan du styre, hvor længe brugeren må være inaktiv, før skærmen lukkes.  <br/> |

## <a name="next-objective"></a>Næste mål

[Administrer Windows-enheder](m365bp-manage-windows-devices.md)
