---
title: Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp af SYLF Pro (preview)
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
description: Få mere at vide om, hvordan du onboarder og offboard macOS-enheder Microsoft 365 overholdelsesløsninger ved hjælp af SYLF Pro (preview)
ms.openlocfilehash: e66c9ba88e7c829af3695675a72e264da17e7dc4
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63606755"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview"></a>Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp af SYLF Pro (preview)

Du kan bruge SYLF-Pro til at onboarde macOS-enheder Microsoft 365 løsninger til overholdelse af regler og standarder som f.eks. forebyggelse af datatab på slutpunkter.

> [!IMPORTANT]
> Brug denne fremgangsmåde, hvis ***du ikke har*** Installeret Microsoft Defender for Endpoint (MDE) på dine macOS-enheder

**Gælder for:**

- [Microsoft 365 forebyggelse af datatab på slutpunkter (DLP)](./endpoint-dlp-learn-about.md)
- [Insider-risikostyring](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Før du begynder

- Sørg for, at [dine macOS-enheder administreres via SYLF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) og er knyttet til en identitet (Azure AD forbundet UPN) via JAMF Forbind eller Intune.
- Installér browseren v95+ Edge på dine macOS-enheder 

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>Onboard-enheder til Microsoft 365 løsninger til overholdelse af regler og standarder ved hjælp af SYLF Pro

1. Du skal bruge disse filer til denne procedure.

|Fil, der skal bruges til |Kilde |
|---------|---------|
|Onboardingpakke    |Downloadet fra **onboardingpakken til overholdelsesportalen**, *filnavnet DeviceComplianceOnboarding.plist* |
|tilgængelighed |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
fuld diskadgang     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|Netværksfilter| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|Systemudvidelser |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|MDE-indstilling     |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|MAU-indstilling|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|Installationspakke     |downloadet fra installationspakken **til overholdelsesportalen**, *filnavnet\* wdav.pkg*\* |

> [!TIP]
> Du kan downloade *.mobileconfig-filerne* enkeltvis eller i [en enkelt kombineret fil,](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) der indeholder:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>Hvis nogen af disse individuelle filer opdateres, skal du enten hente den kombinerede fil igen eller den enkelt opdaterede fil enkeltvis.

Onboarding af en macOS-enhed til løsninger til overholdelse af regler og standarder er en proces i flere trin.

### <a name="get-the-device-onboarding-package"></a>Hent onboardingpakken til enheden

1. I **Overholdelsescenter** skal **du** **Indstillinger-onboarding** >  og vælge **Onboarding**.
 
1. Vælg macOS **for at vælge operativsystem for at starte** **onboardingprocessen**
 
1. **Udrulningsmetode** **vælger Administration/Microsoft Intune**
 
1. Vælg **Download onboardingpakke**
 
1. Udtræk indholdet af onboardingpakken til enheden. I mappen SYLF bør du kunne se filen *DeviceComplainceOnboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>Opret en SYLF-Pro konfigurationsprofil for onboardingpakken

1. Opret en ny konfigurationsprofil i SYLF Pro. Se guide til [SYLF Pro administratorer](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP onboarding for macOS`
    - Beskrivelse: `MDATP EDR onboarding for macOS`
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

2. Vælg Overfør og tilføj Pro > **af & AFSPILTEP** I  **PRO-konsollens brugerdefinerede indstillinger**. Brug denne værdi:
    - Preference-domæne: `com.microsoft.wdav.atp`

3. Vælg **Overfør** , og vælg onboardingfilen **DeviceComplianceOnboarding.plist**.

4. Vælg **fanen Omfang** .

5. Vælg destinationscomputerne.

6. Vælg **Gem**.

7. Vælg **Udført**.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>Konfigurere præferencedomæne ved hjælp af SYLF PRO-konsollen

> [!IMPORTANT]
> Du skal bruge ***com.microsoft.wdav** _ som præferencedomæneværdi. Microsoft Defender til Slutpunkt bruger dette navn og _ *_com.microsoft.wdav.ext_** til at indlæse de administrerede indstillinger.

1. Opret en ny konfigurationsprofil i SYLF Pro. Se guide til [SYLF Pro administratorer](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP MDAV configuration settings`
    - Beskrivelse: Lad dette være tomt
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

1. På fanen **Program & brugerdefineret Indstillinger** skal du vælge **Eksterne programmer**, vælge Tilføj og vælge **Brugerdefineret skema** for præferencedomænet. Brug denne værdi:
    - Præferencedomæne: `com.microsoft.wdav`

1. Vælg **Tilføj skema** og **Upload** at overføre *filen schema.json*.

1. Vælg **Gem**.

1. Vælg **disse indstillinger under Egenskaber for** præferencedomæne
    - Funktioner 
        - Brug systemudvidelser: `enabled` - påkrævet til netværksudvidelser på Catalina
        - Brug forebyggelse af datatab: `enabled`
    - Antivirusprogram > passiv tilstand: `true|false`. Brug `true`, hvis du kun installerer DLP. Brug `false` eller tildel ikke en værdi, hvis du installerer DLP og Microsoft Defender for Endpoint (MDE).

1. Vælg **fanen** Omfang.

1. Vælg de grupper, du vil installere denne konfigurationsprofil på.

1. Vælg **Gem**. 


### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>Oprette og installere en konfigurationsprofil for Microsoft Automatiske opdateringer (MAU)

1. Opret en SYLF-Pro konfigurationsfil ved hjælp **af com.microsoft.autoupdate2.plist**. Se guide til [SYLF Pro administratorer](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP MDAV MAU settings`
    - Beskrivelse: `Microsoft AutoUPdate settings for MDATP for macOS`
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

1. I **Program & Brugerdefineret Indstillinger** du **Upload** og **Tilføj**.

1. I **Indstillinger Domæne** skal du `com.microsoft.autoupdate2` indtaste og derefter **Upload**.

1. Vælg filen **com.microsoft.autoupdate2.plist** .

1. Vælg **Gem**.

1. Vælg **fanen** Omfang.

1. Vælg destinationscomputerne.

1. Vælg **Gem**.

1. Vælg **Udført**.


### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>Opret og implementer en konfigurationsprofil for At tildele fuld diskadgang

1. Brug **filen fulldisk.mobileconfig** .

1. Upload **filen fulldisk.mobileconfig** til JAMF. Se Implementering [af brugerdefinerede konfigurationsprofiler ved hjælp af SYLF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>Oprette og installere en konfigurationsprofil for systemudvidelser

1. Opret en SYLF Pro-konfigurationsfil ved hjælp af procedurerne i [JAMF Pro vejledning for administratorer](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). Brug disse værdier:
    - Navn: `MDATP MDAV System Extensions`
    - Beskrivelse: `MDATP system extensions`
    - Kategori: `none`
    - Distributionsmetode: `install automatically`
    - Niveau: `computer level`

1. I **profilen for** Systemudvidelser skal du angive disse værdier:
    - Visningsnavn: `Microsoft Corp. System Extensions`
    - Systemudvidelsestyper: `Allowed System Extensions`
    - Team-id: `UBF8T346G9`
    - Tilladte systemudvidelser: `com.microsoft.wdav.epsext`og `com.microsoft.wdav.netext`

1. Vælg **fanen** Omfang.

1. Vælg destinationscomputerne.

1. Vælg **Gem**.

1. Vælg **Udført**.

### <a name="configure-network-extension"></a>Konfigurere netværksudvidelse

1.  Brug filen **netfilter.mobileconfig**, som du hentede fra GitHub.

2.  Upload til SYLF som beskrevet i [Udrul brugerdefinerede konfigurationsprofiler ved hjælp af Sylf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>Giv tilgængelighedsadgang til DLP

1. Brug filen **accessibility.mobileconfig**, som du hentede fra GitHub.

2.  Upload til SYLF som beskrevet i [Udrul brugerdefinerede konfigurationsprofiler ved hjælp af Sylf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>Hent installationspakken

1. I **Overholdelsescenter** skal **du** **Indstillinger-onboarding** >  og vælge **Onboarding**.
 
1. Vælg macOS **for at vælge operativsystem for at starte** **onboardingprocessen**
 
1. **Udrulningsmetode** **vælger Administration/Microsoft Intune**
 
1. Vælg **Download installationspakke**. Dette giver dig *filen wdav.pkg* .


### <a name="deploy-the-installation-package"></a>Installér installationspakken

1. Gå til det sted, hvor du gemte `wdav.pkg` filen.

1. Åbn SYLEF Pro dashboardet.

1. Vælg din computer, og klik på tandhjulet øverst, og vælg derefter **Computeradministration**.

1. I **Pakker skal** du **vælge + Ny**. Angiv disse oplysninger:
    - Visningsnavn: Lad feltet være tomt, da den nulstilles, når du vælger .pkg-filen.
    - Kategori: Ingen (standard)
    - Filnavn: Vælg fil, i dette tilfælde `wdav.pkg` filen.

1. Vælg **Åbn**. Angiv:
    - **Visningsnavn**: `Microsoft Endpoint Technology`
    - **Manifestfil**: ikke påkrævet
    - **Fanen Indstillinger**: Lad standardværdierne være
    - **Fanen Begrænsninger**: Lad standardværdierne være

1. Vælg **Gem**. Dette uploader pakken til SYLF Pro.

1. Åbn **siden** Politikker.

1. Vælg **+Ny** for at oprette en ny politik.

1. Angiv disse værdier
    - **Visningsnavn**: `MDATP Onboarding200329 v100.86.92 or later`

1. Vælg **Tilbagevendende indtjekning**.

1. Vælg **Gem**.

1. Vælg **PackagesConfigure** > .

1. Vælg **Tilføj**.

1. Vælg **Gem**. 

1. Vælg **fanen** Omfang.

1. Vælg destinationscomputerne.

1. Vælg **Tilføj**.

1. Vælg **Selvbetjening**.

1. Vælg **Udført**.

### <a name="check-the-macos-device"></a>Kontrollér macOS-enheden 

1. Genstart macOS-enheden.

1. Åbn **SystemindstillingerProfiler** > .

1. Du bør se:
    - Accessiblity
    - Fuld diskadgang
    - MAU
    - MDATP Onboarding
    - MDE-indstillinger
    - Administrationsprofil
    - Netværksfilter
    - Systemudvidelsesprofil

## <a name="offboard-macos-devices-using-jamf-pro"></a>Offboard macOS-enheder, der bruger SYLF Pro

1. Fjern programmet (hvis det ikke bruger MDE)
    1. Se JAMF Pro Docs - Pakkeinstallation - [JAMF Pro-administratorer vejledning](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) Pro Administratorvejledning

1. Genstart macOS-enheden – nogle programmer kan miste udskrivningsfunktionalitet, indtil de genstartes

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.
