---
title: Onboard og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF Pro
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
description: Få mere at vide om, hvordan du onboarder og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF-Pro
ms.openlocfilehash: bf15868b865afa80146df2b16199caf360a55ce2
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953421"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Onboard og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF Pro

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge JAMF-Pro til at onboarde macOS-enheder i Microsoft Purview-løsninger, f.eks. endpoint-forebyggelse af datatab.

> [!IMPORTANT]
> Brug denne fremgangsmåde, hvis du ***ikke*** har installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- [Forebyggelse af datatab for slutpunkt (DLP)](./endpoint-dlp-learn-about.md)
- [Styring af insider-risiko](insider-risk-management.md)

## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at dine [macOS-enheder administreres via JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) og er knyttet til en identitet (Azure AD joinforbundet UPN) via JAMF-Forbind eller Intune.
- Installér v95+ Edge-browseren på dine macOS-enheder

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>Onboarde enheder i Microsoft Purview-løsninger ved hjælp af JAMF-Pro

1. Du skal bruge disse filer til denne procedure.

|Filen skal bruges til|Kilde|
|---|---|
|Onboarding-pakke|Downloadet fra **onboardingpakken til overholdelsesportalen**, filnavn *DeviceComplianceOnboarding.plist*|
|Tilgængelighed|[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang|[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Netværksfilter| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Systemudvidelser|[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE-indstillinger|[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|MAU-indstillinger|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Installationspakke|downloadet fra **installationspakken** til overholdelsesportalen, filnavn *\*wdav.pkg*\*|

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvist eller i [en enkelt kombineret fil](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) , der indeholder:
>
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten downloade den kombinerede fil igen eller den enkelte opdaterede fil enkeltvist.

Onboarding af en macOS-enhed i overholdelsesløsninger er en proces med fleresfaser.

### <a name="get-the-device-onboarding-package"></a>Hent onboardingpakken til enheden

1. I **Compliance Center** skal **du åbne Indstillinger** >  **Device Onboarding** og vælge **Onboarding**.

1. **Vælg macOS for Vælg operativsystem for at starte onboardingprocessen** 

1. Vælg **Mobile Enhedshåndtering/Microsoft Intune** for **installationsmetode**

1. Vælg **Download onboarding-pakke**

1. Udpak indholdet af enhedens onboardingpakke. I mappen JAMF kan du se filen *DeviceComplainceOnboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Opret en JAMF-Pro konfigurationsprofil til onboardingpakken

1. Opret en ny konfigurationsprofil i JAMF-Pro. Se [administratorvejledningen til JAMF-Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP onboarding for macOS`
    - Beskrivelse: `MDATP EDR onboarding for macOS`
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

2. I JAMF-Pro konsollen > **Program & Brugerdefinerede indstillinger** skal du vælge **Upload** og derefter **tilføje**. Brug denne værdi:
    - Præferencedomæne: `com.microsoft.wdav.atp`

3. Vælg **upload,** og vælg onboardingfilen **DeviceComplianceOnboarding.plist**.

4. Vælg fanen **Område** .

5. Vælg destinationscomputerne.

6. Vælg **Gem**.

7. Vælg **Udført**.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>Konfigurer domænet Indstillinger ved hjælp af JAMF PRO-konsollen

> [!IMPORTANT]
> Du skal bruge ***com.microsoft.wdav** _ som værdien for præferencedomænet. Microsoft Defender for Endpoint bruger dette navn og _ *_com.microsoft.wdav.ext_** til at indlæse de administrerede indstillinger.

1. Opret en ny konfigurationsprofil i JAMF-Pro. Se [administratorvejledningen til JAMF-Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP MDAV configuration settings`
    - Beskrivelse: Lad dette være tomt
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

1. På fanen **Program & Brugerdefineret Indstillinger** skal du vælge **Eksterne programmer**, vælge **Tilføj** og vælge **Brugerdefineret skema for præferencedomænet**. Brug denne værdi:
    - Præferencedomæne: `com.microsoft.wdav`

1. Vælg **Tilføj skema**, og **Upload** for at overføre filen *schema.json*.

1. Vælg **Gem**.

1. Under **Indstillinger for domæneegenskaber** skal du vælge disse indstillinger
    - Funktioner
        - Brug systemudvidelser: `enabled` – påkrævet til netværksudvidelser på Catalina
        - Brug forebyggelse af datatab: `enabled`
    - Antivirusprogram > passiv tilstand: `true|false`. Bruges `true`kun, hvis der installeres DLP. Brug `false` eller tildel ikke en værdi, hvis du installerer DLP og Microsoft Defender for Endpoint (MDE).

1. Vælg fanen **Område** .

1. Vælg de grupper, denne konfigurationsprofil skal installeres i.

1. Vælg **Gem**.

### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Opret og udrul en konfigurationsprofil til Microsoft Automatiske opdateringer (MAU)

1. Opret en JAMF-Pro konfigurationsfil ved hjælp af **com.microsoft.autoupdate2.plist**. Se [administratorvejledningen til JAMF-Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP MDAV MAU settings`
    - Beskrivelse: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

1. I **& Brugerdefineret Indstillinger** skal du vælge **Upload** og **Tilføj**.

1. Angiv **i Indstillinger Domæne**, `com.microsoft.autoupdate2` og vælg derefter **Upload**.

1. Vælg filen **com.microsoft.autoupdate2.plist** .

1. Vælg **Gem**.

1. Vælg fanen **Område** .

1. Vælg destinationscomputerne.

1. Vælg **Gem**.

1. Vælg **Udført**.

### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Opret og installér en konfigurationsprofil for Tildel fuld diskadgang

1. Brug filen **fulldisk.mobileconfig** .

1. Upload filen **fulldisk.mobileconfig** til JAMF. Se [Udrulning af brugerdefinerede konfigurationsprofiler ved hjælp af JAMF-Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Opret og udrul en konfigurationsprofil til systemudvidelser

1. Opret en JAMF-Pro konfigurationsfil ved hjælp af procedurerne i [administratorvejledningen til JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP MDAV System Extensions`
    - Beskrivelse: `MDATP system extensions`
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

1. Angiv følgende værdier i **profilen Systemudvidelser** :
    - Vist navn: `Microsoft Corp. System Extensions`
    - Systemudvidelsestyper: `Allowed System Extensions`
    - Gruppe-id: `UBF8T346G9`
    - Tilladte systemudvidelser: `com.microsoft.wdav.epsext`, og `com.microsoft.wdav.netext`

1. Vælg fanen **Område** .

1. Vælg destinationscomputerne.

1. Vælg **Gem**.

1. Vælg **Udført**.

### <a name="configure-network-extension"></a>Konfigurer netværksudvidelse

1. Brug den **netfilter.mobileconfig-fil**, du har downloadet fra GitHub.

2. Upload til JAMF som beskrevet i [Udrulning af brugerdefinerede konfigurationsprofiler ved hjælp af Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>Tildel tilgængelighedsadgang til DLP

1. Brug den **accessibility.mobileconfig-fil**, du har downloadet fra GitHub.

2. Upload til JAMF som beskrevet i [Udrulning af brugerdefinerede konfigurationsprofiler ved hjælp af Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Hent installationspakken

1. I **Compliance Center** skal **du åbne Indstillinger** >  **Device Onboarding** og vælge **Onboarding**.

1. **Vælg macOS for Vælg operativsystem for at starte onboardingprocessen** 

1. Vælg **Mobile Enhedshåndtering/Microsoft Intune** for **installationsmetode**

1. Vælg **Download installationspakke**. Dette giver dig filen *wdav.pkg* .

### <a name="deploy-the-installation-package"></a>Installer installationspakken

1. Naviger til det placering, hvor du gemte `wdav.pkg` filen.

1. Åbn JAMF-dashboardet Pro.

1. Vælg computeren, og klik på tandhjulet øverst, og vælg derefter **Computeradministration**.

1. I **Pakker** skal du vælge **+Ny**. Angiv disse oplysninger:
    - Vist navn: Lad argumentet være tomt, da det nulstilles, når du vælger .pkg-filen.
    - Kategori: Ingen (standard)
    - Filnavn: Vælg fil, i dette tilfælde `wdav.pkg` filen.

1. Vælg **Åbn**. Sæt:
    - **Vist navn**: `Microsoft Endpoint Technology`
    - **Manifestfil**: ikke påkrævet
    - **Fanen Indstillinger**: Behold standardværdier
    - **Fanen Begrænsninger**: Behold standardværdier

1. Vælg **Gem**. Dette uploader pakken til JAMF-Pro.

1. Åbn siden **Politikker** .

1. Vælg **+Ny** for at oprette en ny politik.

1. Angiv disse værdier
    - **Vist navn**: `MDATP Onboarding200329 v100.86.92 or later`

1. Vælg **Tilbagevendende indtjekning**.

1. Vælg **Gem**.

1. Vælg **PakkerKonfigurer** > .

1. Vælg **Tilføj**.

1. Vælg **Gem**.

1. Vælg fanen **Område** .

1. Vælg destinationscomputerne.

1. Vælg **Tilføj**.

1. Vælg **Selvbetjening**.

1. Vælg **Udført**.

### <a name="check-the-macos-device"></a>Kontrollér macOS-enheden

1. Genstart macOS-enheden.

1. Åbn **SystemindstillingerProfiler** > .

1. Du burde kunne se:
    - Accessiblity
    - Fuld diskadgang
    - MAU
    - MDATP-onboarding
    - MDE-indstillinger
    - Administrationsprofil
    - Netværksfilter
    - Profil for systemudvidelse

## <a name="offboard-macos-devices-using-jamf-pro"></a>MacOS-enheder, der bruger JAMF-Pro

1. Fjern programmet (hvis det ikke bruger MDE)
    1. Se JAMF Pro Docs – Package Deployment – [JAMF Pro administratorvejledningJamf](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro Administratorvejledning

1. Genstart macOS-enheden – nogle programmer kan miste udskrivningsfunktionaliteten, indtil de genstartes

> [!IMPORTANT]
> Offboarding medfører, at enheden stopper med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, den har haft, bevares i op til seks måneder.
