---
title: Onboarde og offboard macOS-enheder i overholdelsesløsninger ved hjælp af Microsoft Intune til Microsoft Defender for Endpoint kunder
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
description: Få mere at vide om, hvordan du onboarder og om bord på macOS-enheder i Microsoft Purview-løsninger ved hjælp af Microsoft Intune til MDE-kunder
ms.openlocfilehash: 3e6947483a4d3320b61211edeb0f9fdc3e31095d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623025"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers"></a>Onboard og offboard macOS-enheder i overholdelsesløsninger ved hjælp af Intune til Microsoft Defender for Endpoint-kunder

> [!IMPORTANT]
> Brug denne procedure ***, hvis du har*** installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- Kunder, der har installeret MDE på deres macOS-enheder.
- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)


## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at dine [macOS-enheder er onboardet i Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) og tilmeldt [Firmaportal-appen](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- Sørg for, at du har adgang til [Microsoft Endpoint Manager center](https://endpoint.microsoft.com/#home)
- Dette understøtter macOS-version Catalina 10.15 og nyere
- Installér v95+ Edge-browseren på dine macOS-enheder 

## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>Onboarde macOS-enheder i Microsoft Purview-løsninger ved hjælp af Microsoft Intune

Brug disse trin til at onboarde en macOS-enhed i løsninger til overholdelse af angivne standarder, hvis MDE allerede er udrullet til den.

1. Du skal bruge disse filer til denne procedure.

|fil, der er nødvendig for |Kilde |
|---------|---------|
|Tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvist eller i [en enkelt kombineret fil](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> 
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten downloade den kombinerede fil igen eller den enkelte opdaterede fil enkeltvist.

### <a name="create-system-configuration-profiles"></a>Opret systemkonfigurationsprofiler

1. Åbn **konfigurationsprofilerne** **for Microsoft Endpoint Manager centerenheder** >  > .

1. Vælg: **Opret profil**. 

1. Vælge:
    1. **Platform = macOS**
    1. **Profiltype = skabeloner**
    1. **Skabelonnavn = Brugerdefineret**

1. Vælg **Opret**

1. Vælg et navn til profilen, f.eks *. AccessibilityformacOS* i dette eksempel. Vælg **Næste**.

1. Vælg den **accessibility.mobileconfig-fil** , du downloadede i trin 1, som konfigurationsprofilfil.

1. Vælg **næste**

1. Under fanen **Tildelinger** skal du tilføje den gruppe, du vil installere disse konfigurationer i, og vælge **Næste**.

1. Gennemse dine indstillinger, og vælg **Opret** for at installere konfigurationen.

1. Åbn **Enhedskonfigurationsprofiler** > . Du kan se dine oprettede profiler der.

1. På siden **Konfigurationsprofiler** skal du vælge den profil, du lige har oprettet, i dette eksempel *AccessibilityformacOS* og vælge **Enhedsstatus** for at få vist en liste over enheder og installationsstatussen for konfigurationsprofilen.

### <a name="update-configuration-profiles"></a>Opdater konfigurationsprofiler

1. Opdater den eksisterende fulde diskadgangsprofil med **filen fulldisk.mobileconfig** .

1. Opdater profilen for eksisterende MDE-indstillinger med disse værdier
   
```xml
<key>features</key>
<dict>
    <key>systemExtensions</key>
    <string>enabled</string>
    <key>dataLossPrevention</key>
    <string>enabled</string>
</dict>
```

## <a name="offboard-macos-devices-using-intune"></a>MacOS-enheder uden for bord ved hjælp af Intune

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

1. Åbn **Profiler til konfiguration af** **enheder** >  i **Microsoft Endpoint Manager center**. Du kan se dine oprettede profiler der.

2. Vælg profilen **MDE-indstillinger på siden Konfigurationsprofiler** .

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
