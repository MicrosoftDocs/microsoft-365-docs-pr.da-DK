---
title: Gør Windows enheder sikre
f1.keywords:
- CSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: medium
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
ms.openlocfilehash: b58e63abf19c3078eb5d4356b155df13804c95d5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704815"
---
# <a name="secure-windows-devices"></a>Gør Windows enheder sikre

Denne artikel gælder for Microsoft 365 Business Premium.

De indstillinger, du konfigurerer her, er en del af standardenhedspolitikken for Windows 10 eller 11. Alle brugere, der forbinder Windows enhed, herunder mobilenheder og pc'er, ved at logge på med deres arbejdskonto, modtager automatisk disse indstillinger. Vi anbefaler, at du accepterer standardpolitikken under installationen og senere tilføjer politikker, der er målrettet bestemte grupper af brugere.
  
## <a name="settings-to-secure-windows-10-devices"></a>Indstillinger at sikre Windows 10 enheder

Alle indstillinger er som standard **til.** Der findes følgende tilgængelige indstillinger: <br/><br/>

|Indstilling  <br/> |Beskrivelse  <br/> |
|:-----|:-----|
|Beskyt pc'er mod virus og andre trusler ved hjælp af Windows Defender Antivirus  <br/> |Kræver, Windows Defender Antivirus er slået til for at beskytte pc'er mod risici ved at forbinde til internettet.  <br/> |
|Beskyt pc'er mod webbaserede trusler i Microsoft Edge  <br/> |Slår indstillinger i Edge til for at beskytte brugere mod skadelige websteder og downloads.  <br/> |
|Hjælp med at beskytte filer og mapper på pc'er mod uautoriseret adgang med BitLocker  <br/> |BitLocker beskytter data ved at kryptere harddiske på computeren og beskytter mod dataeksponering, hvis en computer mistes eller bliver stjålet. Du kan finde flere oplysninger under [Ofte stillede spørgsmål om BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|Slå enhedsskærmen fra, når den er inaktiv i denne periode  <br/> |Sørg for, at virksomhedsdata er beskyttet, hvis en bruger er inaktiv. En bruger arbejder måske på et offentligt sted, f.eks. en café, og går væk eller bliver forstyrret et øjeblik, så deres enhed er sårbar over for tilfældige blikke. Med denne indstilling kan du styre, hvor længe brugeren kan være inaktiv, før skærmen slukker.  <br/> |
