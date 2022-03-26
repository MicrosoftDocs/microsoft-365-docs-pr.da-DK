---
title: Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af SYLF Pro til Microsoft Defender til Slutpunkt-kunder (prøveversion)
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
description: Få mere at vide om, hvordan du onboarder og offboard macOS-enheder i Microsoft 365 Overholdelsesløsninger ved hjælp af SYLF Pro til Microsoft Defender for Endpoint-kunder (prøveversion)
ms.openlocfilehash: f260d901f8f02c2c02007b2cc0d49ab9ee57dafd
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716315"
---
# <a name="onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview"></a>Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af SYLF Pro til Microsoft Defender til Slutpunkt-kunder (prøveversion)

Du kan bruge SYLF-Pro til at onboarde macOS-enheder Microsoft 365 løsninger til overholdelse af regler og standarder.

> [!IMPORTANT]
> Brug denne fremgangsmåde ***, hvis du*** har installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- Kunder, der har MDE installeret på deres macOS-enheder.
- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)


## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at [dine macOS-enheder administreres via SYLF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) og er knyttet til en identitet (Azure AD forbundet UPN) via JAMF Forbind eller Intune.
- Installér browseren v95+ Edge på dine macOS-enheder

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>Onboard-enheder til Microsoft 365 løsninger til overholdelse af regler og standarder ved hjælp af SYLF Pro

Onboarding af en macOS-enhed til overholdelsesløsninger er en proces i flere faser.

### <a name="download-the-configuration-files"></a>Download konfigurationsfilerne

1. Du skal bruge disse filer til denne procedure.

|fil, der skal bruges til |kilde |
|---------|---------|
|tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|MDE-indstilling |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/schema/schema.json)

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvis eller i [en enkelt kombineret fil,](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten hente den kombinerede fil igen eller den enkelt opdaterede fil enkeltvis.

### <a name="update-the-existing-mde-preference-domain-profile-using-the-jamf-pro-console"></a>Opdater den eksisterende MDE Preference-domæneprofil ved hjælp af SYLF PRO-konsollen

1. Opdater profilen schema.xml **skema.json, du** lige har downloadet.

1. Under **Egenskaber for MDE-præferencedomæne** skal du vælge disse indstillinger
    - Funktioner 
        - Brug systemudvidelser: `enabled` - påkrævet til netværksudvidelser på Catalina
        - Brug forebyggelse af datatab: `enabled`

1. Vælg **fanen** Omfang.

1. Vælg de grupper, du vil installere denne konfigurationsprofil på.

1. Vælg **Gem**. 

### <a name="update-the-configuration-profile-for-grant-full-disk-access"></a>Opdater konfigurationsprofilen for At tildele fuld diskadgang

1. Opdater den eksisterende profil for fuld diskadgang med **filen fulldisk.mobileconfig** .

1. Upload **filen fulldisk.mobileconfig** til JAMF. Se Implementering [af brugerdefinerede konfigurationsprofiler ved hjælp af SYLF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="grant-accessibility-access-to-dlp"></a>Giv tilgængelighedsadgang til DLP

1. Brug den accessibility.mobileconfig-fil, du tidligere har downloadet.

1. Upload til SYLF som beskrevet i [Udrul brugerdefinerede konfigurationsprofiler ved hjælp af Sylf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="check-the-macos-device"></a>Kontrollér macOS-enheden 

1. Genstart macOS-enheden.

1. Åbn **SystemindstillingerProfiler** > .

1. Du bør se:
    - Accessiblity
    - Fuld diskadgang
    - Kerneludvidelsesprofil
    - MAU
    - MDATP Onboarding
    - MDE-indstillinger
    - Administrationsprofil
    - Netværksfilter
    - Meddelelser
    - Systemudvidelsesprofil

## <a name="offboard-macos-devices-using-jamf-pro"></a>Offboard macOS-enheder, der bruger SYLF Pro

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

Hvis du vil deaktivere en macOS-enhed, skal du følge disse trin

 1. Under **Egenskaber for MDE-præferencedomæne** skal du fjerne værdierne for disse indstillinger
    - Funktioner 
        - Brug systemudvidelser
        - Brug forebyggelse af datatab

1. Vælg **Gem**.
