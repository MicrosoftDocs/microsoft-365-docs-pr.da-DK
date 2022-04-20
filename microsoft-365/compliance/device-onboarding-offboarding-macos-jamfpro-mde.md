---
title: Onboarde og offboard macOS-enheder i overholdelsesløsninger ved hjælp af JAMF-Pro til Microsoft Defender for Endpoint kunder
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
description: Få mere at vide om, hvordan du onboarder og om bord på macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF-Pro til Microsoft Defender for Endpoint kunder
ms.openlocfilehash: ba2ff7723e54451ace46823fafb5323dcb35069e
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953377"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers"></a>Onboarde og offboard macOS-enheder i overholdelsesløsninger ved hjælp af JAMF-Pro til Microsoft Defender for Endpoint kunder

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge JAMF-Pro til at integrere macOS-enheder i Microsoft Purview-løsninger.

> [!IMPORTANT]
> Brug denne procedure ***, hvis du har*** installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- Kunder, der har installeret MDE på deres macOS-enheder.
- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)


## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at dine [macOS-enheder administreres via JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) og er knyttet til en identitet (Azure AD joinforbundet UPN) via JAMF-Forbind eller Intune.
- Installér v95+ Edge-browseren på dine macOS-enheder

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Onboarde enheder i Microsoft Purview-løsninger ved hjælp af JAMF-Pro

Onboarding af en macOS-enhed i overholdelsesløsninger er en proces med flere faser.

### <a name="download-the-configuration-files"></a>Download konfigurationsfilerne

1. Du skal bruge disse filer til denne procedure.

|fil, der er nødvendig for |Kilde |
|---------|---------|
|Tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|MDE-indstillinger |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvist eller i [en enkelt kombineret fil](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten downloade den kombinerede fil igen eller den enkelte opdaterede fil enkeltvist.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>Opdater den eksisterende domæneprofil for MDE-indstillinger ved hjælp af JAMF PRO-konsollen

1. Opdater den schema.xml profil med den **schema.json-fil** , du lige har downloadet.

1. Under **Egenskaber for MDE-præferencedomæne** skal du vælge disse indstillinger
    - Funktioner 
        - Brug systemudvidelser: `enabled` – påkrævet til netværksudvidelser på Catalina
        - Brug forebyggelse af datatab: `enabled`

1. Vælg fanen **Område** .

1. Vælg de grupper, denne konfigurationsprofil skal installeres i.

1. Vælg **Gem**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Opdater konfigurationsprofilen for Tildel fuld diskadgang

1. Opdater den eksisterende fulde diskadgangsprofil med **filen fulldisk.mobileconfig** .

1. Upload filen **fulldisk.mobileconfig** til JAMF. Se [Udrulning af brugerdefinerede konfigurationsprofiler ved hjælp af JAMF-Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>Tildel tilgængelighedsadgang til DLP

1. Brug den accessibility.mobileconfig-fil, du tidligere har downloadet.

1. Upload til JAMF som beskrevet i [Udrulning af brugerdefinerede konfigurationsprofiler ved hjælp af Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Kontrollér macOS-enheden 

1. Genstart macOS-enheden.

1. Åbn **SystemindstillingerProfiler** > .

1. Du burde kunne se:
    - Accessiblity
    - Fuld diskadgang
    - Profil for kerneudvidelse
    - MAU
    - MDATP-onboarding
    - MDE-indstillinger
    - Administrationsprofil
    - Netværksfilter
    - Meddelelser
    - Profil for systemudvidelse

## <a name="offboard-macos-devices-using-jamf-pro"></a>MacOS-enheder, der bruger JAMF-Pro

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.

Følg disse trin for at komme ombord på en macOS-enhed

 1. Fjern værdierne for disse indstillinger under **Domæneegenskaber for MDE-indstillinger**
    - Funktioner 
        - Brug systemudvidelser
        - Brug forebyggelse af datatab

1. Vælg **Gem**.
