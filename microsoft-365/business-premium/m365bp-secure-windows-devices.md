---
title: Sikker Windows enheder
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
description: Få mere at vide om, hvordan du konfigurerer indstillingerne for standardenhedspolitikken, som alle Windows enheder modtager, når de logger på deres arbejds- eller skolekonto.
ms.openlocfilehash: e912ab639e5457d3c89155da4d3621399502267f
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319898"
---
# <a name="secure-windows-devices"></a>Sikker Windows enheder

Målet her er at konfigurere indstillinger, der er en del af standardenhedspolitikken for Windows 10 eller 11. Alle brugere, der opretter forbindelse til en Windows enhed, herunder mobilenheder og pc'er ved at logge på med deres arbejdskonto, modtager automatisk disse indstillinger. Vi anbefaler, at du accepterer standardpolitikken under konfigurationen og tilføjer politikker senere, som er målrettet bestemte grupper af brugere.
  
## <a name="settings-to-secure-windows-10-devices"></a>Indstillinger at sikre Windows 10 enheder

Alle indstillinger er som standard **Slået til**. Følgende indstillinger er tilgængelige: <br/><br/>

|Indstilling  <br/> |Beskrivelse  <br/> |
|:-----|:-----|
|Hjælp med at beskytte pc'er mod virus og andre trusler ved hjælp af Windows Defender Antivirus  <br/> |Kræver, at Windows Defender Antivirus er slået til for at beskytte pc'er mod farerne ved at have forbindelse til internettet.  <br/> |
|Hjælp med at beskytte pc'er mod webbaserede trusler i Microsoft Edge  <br/> |Slår indstillinger i Edge til, der hjælper med at beskytte brugere mod skadelige websteder og downloads.  <br/> |
|Hjælp med at beskytte filer og mapper på pc'er mod uautoriseret adgang med BitLocker  <br/> |BitLocker beskytter data ved at kryptere computerens harddiske og beskytte mod eksponering af data, hvis en computer mistes eller bliver stjålet. Du kan få flere oplysninger under [Ofte stillede spørgsmål om BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Slå enhedsskærmen fra, når den er inaktiv i så lang tid  <br/> |Sikrer, at firmadata er beskyttet, hvis en bruger er inaktiv. En bruger arbejder muligvis på et offentligt sted, f.eks. en café, og træder væk eller bliver distraheret et øjeblik, så enheden er sårbar over for tilfældige blik. Med denne indstilling kan du styre, hvor længe brugeren må være inaktiv, før skærmen lukkes.  <br/> |

## <a name="next-objective"></a>Næste mål

[Administrer Windows enheder](m365bp-manage-windows-devices.md)
