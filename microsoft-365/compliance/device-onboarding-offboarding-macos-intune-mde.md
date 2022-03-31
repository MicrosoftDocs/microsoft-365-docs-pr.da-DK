---
title: Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp Microsoft Intune for Microsoft Defender til Endpoint-kunder (prøveversion)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Lær at onboarde og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp Microsoft Intune for MDE-kunder (preview)
ms.openlocfilehash: 6cc4362e924f291c6a8396bff342c6f628e33be3
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63601020"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview"></a>Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af Intune til Microsoft Defender til Endpoint-kunder (preview)

> [!IMPORTANT]
> Brug denne fremgangsmåde ***, hvis du*** har installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- Kunder, der har MDE installeret på deres macOS-enheder.
- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Før du begynder

- Sørg for, [at dine macOS-enheder er onboardet i Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) og Firmaportal [appen](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Sørg for, at du har adgang [til Microsoft Endpoint Manager center](https://endpoint.microsoft.com/#home)
- Dette understøtter macOS version Catalina 10.15 og nyere
- Installér browseren v95+ Edge på dine macOS-enheder 

## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>Onboard macOS-enheder i Microsoft 365 Compliance-løsninger ved hjælp Microsoft Intune

Brug disse trin til at implementere en macOS-enhed i Overholdelsesløsninger, hvis den allerede har installeret MDE.

1. Du skal bruge disse filer til denne procedure.

|fil, der skal bruges til |kilde |
|---------|---------|
|tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvis eller i [en enkelt kombineret fil,](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten hente den kombinerede fil igen eller den enkelt opdaterede fil enkeltvis.

### <a name="create-system-configuration-profiles"></a>Opret systemkonfigurationsprofiler

1. Åbn **Microsoft Endpoint Manager** **CenterKonfigurationsprofiler** >  > .

1. Vælg: **Opret profil**. 

1. Vælg:
    1. **Platform = macOS**
    1. **Profiltype = Skabeloner**
    1. **Skabelonnavn = Brugerdefineret**

1. Vælg **Opret**

1. Vælg et navn til profilen, f.eks *. AccessibilityformacOS* i dette eksempel. Vælg **Næste**.

1. Vælg den **accessibility.mobileconfig-fil** , du hentede i trin 1, som konfigurationsprofilfil.

1. Vælg **Næste**

1. På fanen **Opgaver skal** du tilføje den gruppe, du vil implementere disse konfigurationer i, og vælge **Næste**.

1. Gennemse dine indstillinger, og vælg **Opret** for at installere konfigurationen.

1. Åbn **EnhederKonfigurationsprofiler** > , bør du kunne se dine oprettede profiler der.

1. På siden **Konfigurationsprofiler** skal du vælge den profil, du lige har oprettet, i dette eksempel *AccessibilityformacOS* og vælge Enhedsstatus for at få vist en liste over enheder og installationsstatus for konfigurationsprofilen.

### <a name="update-configuration-profiles"></a>Opdater konfigurationsprofiler

1. Opdater den eksisterende profil for fuld diskadgang med **filen fulldisk.mobileconfig** .

1. Opdater eksisterende MDE-indstillingsprofil med disse værdier
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>Offboard macOS-enheder ved hjælp af Intune

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

1. I **Microsoft Endpoint Manager center** skal du **åbne** **EnhederKonfigurationsprofiler** > , hvor du bør kunne se dine oprettede profiler.

2. På siden **Konfigurationsprofiler** skal du vælge MDE-indstillingsprofilen.

1. Fjern disse indstillinger:
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```
3. **Gem**.