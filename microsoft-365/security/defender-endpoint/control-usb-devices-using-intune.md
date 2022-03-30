---
title: Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Intune (Windows 10)
description: Du kan konfigurere Intune-indstillinger for at reducere trusler fra flytbare lager som f.eks. USB-enheder.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.author: dansimp
author: dansimp
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.technology: mde
ROBOTS: NOINDEX
ms.openlocfilehash: 6ad51065ca4e919fe51cc4a2d5f4b0d53bc474b1
ms.sourcegitcommit: 1ef30b82d97bd998149235dc69d3c0e450e95285
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 09/23/2021
ms.locfileid: "63599377"
---
# <a name="how-to-control-usb-devices-and-other-removable-media-using-microsoft-defender-for-endpoint"></a>Sådan styrer du USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til slutpunkt

**Gælder for:** [Microsoft Defender til slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2069559)

Microsoft anbefaler en lagdelt tilgang til sikring af flytbare [medier, og](https://aka.ms/devicecontrolblog) Microsoft Defender til slutpunkt indeholder flere overvågnings- og kontrolfunktioner for at forhindre trusler i uautoriserede eksterne enheder i at gå på kompromis med dine enheder:

1. [Opdag plug-ins og afspil tilknyttede hændelser for ydre enheder i Microsoft Defender til avanceret jagt på slutpunkter](#discover-plug-and-play-connected-events). Identificer eller undersøg mistænkelig brug.

2. Konfigurer for kun at tillade eller blokere bestemte flytbare enheder og forhindre trusler.
    1. [Tillad eller bloker flytbare](#allow-or-block-removable-devices) enheder, der er baseret på detaljeret konfiguration, for at nægte skriveadgang til flytbare diske og godkende eller afvise enheder ved hjælp af USB-enheds-cd'er. Fleksibel politiktildeling af installationsindstillinger for enheder baseret på en enkeltperson eller en gruppe Azure Active Directory brugere og enheder (Azure AD).

    2. [Undgå trusler fra flytbart lager introduceret](#prevent-threats-from-removable-storage) ved hjælp af flytbare lagringsenheder ved at aktivere:
        - Microsoft Defender Antivirus beskyttelse i realtid (RTP) for at scanne flytbart lager for malware.
        - ASR-reglen (Attack Surface Reduction) til at blokere upålidelige og usignerede processer, der kører fra USB.
        - DMA-beskyttelse (Direct Memory Access) for at reducere DMA-angreb, herunder Kernel DMA-beskyttelse til Thunderbolt og blokering af DMA, indtil en bruger logger på.

3. [Opret tilpassede beskeder og](#create-customized-alerts-and-response-actions) svarhandlinger for at overvåge brugen af flytbare enheder baseret på disse plug and play-hændelser eller andre Microsoft Defender til slutpunktshændelser med [brugerdefinerede registreringsregler](/microsoft-365/security/defender-endpoint/custom-detection-rules).

4. [Reagere på sikkerhedstrusler](#respond-to-threats) fra eksterne enheder i realtid baseret på egenskaber, der rapporteres af hver ekstern enhed.

> [!NOTE]
> Disse tiltag til reduktion af trusler er med til at forhindre malware i at komme ind i dit miljø. Hvis du vil beskytte virksomhedsdata mod at forlade dit miljø, kan du også konfigurere foranstaltninger til forebyggelse af datatab. På Windows 10-enheder kan du f.eks konfigurere [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview.md) og [Windows Information Protection](/windows/security/information-protection/create-wip-policy-using-intune-azure.md), som krypterer virksomhedsdata, også selvom de er gemt på en personlig enhed, eller du kan bruge [Storage/RemovableDiskDenyWriteAccess CSP](/windows/client-management/mdm/policy-csp-storage#storage-removablediskdenywriteaccess) til at afvise skriveadgang til flytbare diske. Desuden kan du klassificere og beskytte filer på [Windows enheder](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview) (herunder deres monterede USB-enheder) ved hjælp af Microsoft Defender til slutpunkt og Azure Information Protection.

## <a name="discover-plug-and-play-connected-events"></a>Opdag plug and play-forbundne begivenheder

Du kan få vist plug-ins og afspille forbundne hændelser i Microsoft Defender for Endpoint på avanceret jagt for at identificere mistænkelig brugsaktivitet eller udføre interne undersøgelser.
Du kan finde eksempler på avancerede forespørgselsforespørgsler om Defender til slutpunkter i [forespørgselsforespørgsler af Microsoft Defender til slutpunkt GitHub repo](https://github.com/Microsoft/WindowsDefenderATP-Hunting-Queries).

Eksempel Power BI rapportskabeloner er tilgængelige for Microsoft Defender til slutpunkt, som du kan bruge til avancerede forespørgselsforespørgsler. Med disse eksempelskabeloner, herunder en til enhedsstyring, kan du integrere styrken fra Avanceret Power BI. Se lager [GitHub til alle Power BI for at få](https://github.com/microsoft/MDATP-PowerBI-Templates) flere oplysninger. Se [Opret brugerdefinerede rapporter ved hjælp Power BI](/microsoft-365/security/defender-endpoint/api-power-bi) for at få mere at vide om Power BI integration.

## <a name="allow-or-block-removable-devices"></a>Tillad eller bloker flytbare enheder
I følgende tabel beskrives de måder, hvorpå Microsoft Defender til slutpunkt kan tillade eller blokere flytbare enheder, der er baseret på detaljeret konfiguration.

<br>

****

|Kontrolelement|Beskrivelse|
|---|---|
|[Begræns USB-drev og andre eksterne enheder](#restrict-usb-drives-and-other-peripherals)|Du kan tillade/forhindre brugere i kun at installere USB-drev og andre eksterne enheder på en liste over godkendte/uautoriserede enheder eller enhedstyper.|
|[Bloker installation og brug af flytbart lager](#block-installation-and-usage-of-removable-storage)|Du kan ikke installere eller bruge flytbart lager.|
|[Tillad installation og brug af særligt godkendte eksterne enheder](#allow-installation-and-usage-of-specifically-approved-peripherals)|Du kan kun installere og bruge godkendte eksterne enheder, der rapporterer bestemte egenskaber i deres firmware.|
|[Forebyd installation af særligt forbudte eksterne enheder](#prevent-installation-of-specifically-prohibited-peripherals)|Du kan ikke installere eller bruge forbudte ydre enheder, der rapporterer bestemte egenskaber i deres firmware.|
|[Tillad installation og brug af særligt godkendte eksterne enheder med matchende enhedsforekomst-cd'er](#allow-installation-and-usage-of-specifically-approved-peripherals-with-matching-device-instance-ids)|Du kan kun installere og bruge godkendte eksterne enheder, der svarer til et af disse enhedsforekomst-iD'er.|
|[Undgå installation og brug af særligt forbudte eksterne enheder med matchende enhedsforekomst-cd'er](#prevent-installation-and-usage-of-specifically-prohibited-peripherals-with-matching-device-instance-ids)|Du kan ikke installere eller bruge forbudte eksterne enheder, der svarer til nogen af disse enhedsforekomst-iD'er.|
|[Begræns de tjenester, der bruger Bluetooth](#limit-services-that-use-bluetooth)|Du kan begrænse de tjenester, der kan bruge Bluetooth.|
|

### <a name="restrict-usb-drives-and-other-peripherals"></a>Begræns USB-drev og andre eksterne enheder

For at forhindre malware inficeret eller datatab kan en organisation begrænse USB-drev og andre eksterne enheder. I følgende tabel beskrives de måder, som Microsoft Defender til slutpunkt kan hjælpe med at forhindre installation og brug af USB-drev og andre eksterne enheder.

<br>

****

|Kontrolelement|Beskrivelse
|---|---|
|[Tillad installation og brug af USB-drev og andre eksterne enheder](#allow-installation-and-usage-of-usb-drives-and-other-peripherals)|Tillad brugere kun at installere de USB-drev og andre eksterne enheder, der er inkluderet på en liste over autoriserede enheder eller enhedstyper|
|[Undgå installation og brug af USB-drev og andre eksterne enheder](#prevent-installation-and-usage-of-usb-drives-and-other-peripherals)|Undgå, at brugere installerer USB-drev og andre eksterne enheder på en liste over uautoriserede enheder og enhedstyper|
|

Alle ovenstående kontrolelementer kan angives via administrative skabeloner i Intune[.](/intune/administrative-templates-windows) De relevante politikker findes her i Intune-administratorskabelonerne:

![skærmbillede af listen over administratorskabeloner.](images/admintemplates.png)

> [!NOTE]
> Ved hjælp af Intune kan du anvende politikker for enhedskonfiguration på Azure AD-brugere og/eller -enhedsgrupper.
Ovenstående politikker kan også angives via [CSP-indstillingerne for enhedsinstallation](/windows/client-management/mdm/policy-csp-deviceinstallation) og [enhedsinstallations-GPOs](/previous-versions/dotnet/articles/bb530324(v=msdn.10)).
>
> Test og tilpas altid disse indstillinger med en pilotgruppe af brugere og enheder først, før de anvendes i produktion.
Du kan finde flere oplysninger om kontrol af USB-enheder [i Microsoft Defender for Endpoint-bloggen](https://www.microsoft.com/security/blog/2018/12/19/windows-defender-atp-has-protections-for-usb-and-removable-devices/).

#### <a name="allow-installation-and-usage-of-usb-drives-and-other-peripherals"></a>Tillad installation og brug af USB-drev og andre eksterne enheder

En metode til at gribe ind og tillade installation og brug af USB-drev og andre eksterne enheder er at starte med at tillade alt. Derefter kan du begynde at reducere de tilladte USB-drivere og andre eksterne enheder.

> [!NOTE]
> Da en uautoriseret USB-ekstern enhed kan have firmware, der efterligner sine USB-egenskaber, anbefaler vi, at du kun tillader specifikt godkendte USB-enheder og begrænser de brugere, der kan få adgang til dem.

1. **Aktivér Forebyd installation af enheder, der ikke er beskrevet i andre politikindstillinger**, for alle brugere.
2. **Aktivér Tillad installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration** for [alle klasser til konfiguration af enheder](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors).

Hvis du vil gennemtvinge politikken for allerede installerede enheder, skal du anvende politikken til at forhindre, at denne indstilling er konfigureret.

Når du konfigurerer politikken til installation af enheder, skal du også tillade alle overordnede attributter. Du kan få vist forældre til en enhed ved at åbne Enhedshåndtering og få vist efter forbindelse.

![Enheder efter forbindelse.](images/devicesbyconnection.png)

I dette eksempel skal følgende klasser tilføjes: HID, Tastatur og {36fc9e60-c465-11cf-8056-444553540000}. Se [Microsoft-leverede USB-drivere for](/windows-hardware/drivers/usbcon/supported-usb-classes) at få flere oplysninger.

![Controller, der er vært for enheden.](images/devicehostcontroller.jpg)

Hvis du vil begrænse til bestemte enheder, skal du fjerne enhedskonfigurationsklassen for den eksterne enhed, som du vil begrænse. Tilføj derefter det enheds-id, du vil tilføje. Enheds-id er baseret på værdierne for leverandør-id og produkt-id for en enhed. Du kan finde oplysninger om enheds-id-formater under [Standard USB-id'er](/windows-hardware/drivers/install/standard-usb-identifiers).

Du kan finde enheds-id'erne under [Slå enheds-id op](#look-up-device-id).

Eksempel:

1. Fjern klasse-USB-stik fra Tillad **installation af enheder med drivere, der passer til konfigurationen af enheden**.
2. Tilføj enheds-id'et, der skal **tillades, i Tillad installation af enhed, der svarer til et af disse enheds-id'er**.

#### <a name="prevent-installation-and-usage-of-usb-drives-and-other-peripherals"></a>Undgå installation og brug af USB-drev og andre eksterne enheder

Hvis du vil forhindre installation af en enhedsklasse eller bestemte enheder, kan du bruge politikkerne for at forhindre installation af enheder:

1. **Aktivér Forebyd installation af enheder, der svarer til et af disse enheds-cd'er**, og føj disse enheder til listen.
2. **Aktivér Afhold installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration**.

> [!NOTE]
> Politikkerne for at forhindre installation af enheder tilsidesætter politikkerne for at tillade installation af enheder.

Politikken **Forebyd** installation af enheder, der svarer til nogen af disse enheds-Windows muligt at angive en liste over enheder, Windows ikke kan installere.

Sådan forhindrer du installation af enheder, der svarer til et af disse enheds-cd'er:

1. [Slå enheds-id'et](#look-up-device-id) op for enheder, Windows vil forhindre i at blive installeret.

   ![Søg efter leverandør eller produkt-id.](images/lookup-vendor-product-id.png)

2. **Aktivér Forebyd installation af enheder**, der svarer til et af disse enheds-cd'er, og føj leverandøren eller produkt-cd'erne til listen.

    ![Tilføj leverandør-id for at forhindre listen.](images/add-vendor-id-to-prevent-list.png)

#### <a name="look-up-device-id"></a>Slå enheds-id op

Du kan bruge Enhedshåndtering til at slå et enheds-id op.

1. Åbn Enhedshåndtering.
2. Klik **på Vis** , og **vælg Enheder efter forbindelse**.
3. Højreklik på enheden i træet, og vælg **Egenskaber**.
4. Klik på fanen Detaljer i dialogboksen for den **valgte** enhed.
5. Klik på **rullelisten** Egenskab, og vælg **Hardware-id'er**.
6. Højreklik på den øverste id-værdi, og vælg **Kopiér**.

Du kan finde oplysninger om enheds-id-formater under [Standard USB-id'er](/windows-hardware/drivers/install/standard-usb-identifiers).

Du kan finde oplysninger om leverandør-iD'er under [USB-medlemmer](https://www.usb.org/members).

Følgende er et eksempel til at søge efter et enhedsleverandør-id eller produkt-id (som er en del af enheds-id'et) ved hjælp af PowerShell:

```powershell
Get-WMIObject -Class Win32_DiskDrive | Select-Object -Property *
```

Politik **for at forhindre installation** af enheder med drivere, der opfylder disse klasser for konfiguration af enhed, giver dig mulighed for at angive klasser for konfiguration af enheder, som Windows er forhindret i at installere.

Sådan forhindrer du installation af bestemte klasser af enheder:

1. Find GUID for enhedskonfigurationsklassen fra [Systemdefinerede klasser for enhedskonfiguration, der er tilgængelige for leverandører](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors).

2. **Aktivér Forebyd installation af enheder med drivere**, der svarer til disse klasser til enhedskonfiguration, og føj klasse-GUID til listen.

    > [!div class="mx-imgBorder"]
    > ![Tilføj enhedskonfigurationsklasse for at forhindre liste.](images/Add-device-setup-class-to-prevent-list.png)

### <a name="block-installation-and-usage-of-removable-storage"></a>Bloker installation og brug af flytbart lager

1. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/).

2. Klik **på Enheders** \> **konfigurationsprofiler** \> **Opret profil**.

    > [!div class="mx-imgBorder"]
    > ![Opret enhedskonfigurationsprofil.](images/create-device-configuration-profile.png)

3. Brug følgende indstillinger:
   - Navn: Skriv et navn til profilen
   - Beskrivelse: Skriv en beskrivelse
   - Platform: Windows 10 og nyere
   - Profiltype: Enhedsbegrænsninger

   > [!div class="mx-imgBorder"]
   > ![Opret profil.](images/create-profile.png)

4. Klik **på Konfigurer** \> **generelt**.

5. For **Flytbart lager og** **USB-forbindelse (kun mobil)** skal du vælge **Bloker**. **Flytbart lager** omfatter USB-drev, hvorimod **USB-forbindelse (** kun mobil) udelukker USB-opladning, men omfatter kun andre USB-forbindelser på mobilenheder.

   ![Generelle indstillinger.](images/general-settings.png)

6. Klik **på OK** for at **lukke Generelle** indstillinger og **Enhedsbegrænsninger**.

7. Klik **på Opret** for at gemme profilen.

### <a name="allow-installation-and-usage-of-specifically-approved-peripherals"></a>Tillad installation og brug af særligt godkendte eksterne enheder

Eksterne enheder, der har tilladelse til at blive installeret, kan angives af deres [hardwareidentitet](/windows-hardware/drivers/install/device-identification-strings). Du kan finde en liste over almindelige identifikatorstrukturer under [Enheds-id-formater](/windows-hardware/drivers/install/device-identifier-formats). Test konfigurationen, før den rulles ud, for at sikre, at den blokerer og tillader de forventede enheder. Test ideelt set forskellige forekomster af hardwaren. Test f.eks. flere USB-taster i stedet for kun én.

Hvis du vil se et SyncML-eksempel, der tillader installation af bestemte enheds-cd'er, skal du se [Enhedsinstallation/AllowInstallationOfMatchingDeviceIDs CSP](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceids). Hvis du vil tillade bestemte enhedsklasser, [skal du se DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses CSP](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses).
Tilladelse til installation af bestemte enheder kræver også aktivering af [DeviceInstallation/PreventInstallationOfDevicesNotDescribedByOtherPolicySettings](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofdevicesnotdescribedbyotherpolicysettings).

### <a name="prevent-installation-of-specifically-prohibited-peripherals"></a>Forebyd installation af særligt forbudte eksterne enheder

Microsoft Defender til Slutpunkt blokerer installation og brug af forbudte eksterne enheder ved hjælp af en af disse indstillinger:

- [Administrative skabeloner kan](/intune/administrative-templates-windows) blokere enhver enhed med et matchende hardware-id eller en matchende konfigurationsklasse.
- [CSP-indstillinger for installation](/windows/client-management/mdm/policy-csp-deviceinstallation) af enhed med en brugerdefineret profil i Intune. Du kan [forhindre installation af bestemte enheds-cd'er](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) eller [forhindre bestemte enhedsklasser](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdevicesetupclasses).

### <a name="allow-installation-and-usage-of-specifically-approved-peripherals-with-matching-device-instance-ids"></a>Tillad installation og brug af særligt godkendte eksterne enheder med matchende enhedsforekomst-cd'er

Eksterne enheder, der har tilladelse til at blive installeret, kan [angives af deres enhedsforekomst-id'er](/windows-hardware/drivers/install/device-instance-ids). Test konfigurationen, før den rulles ud, for at sikre, at den tillader de forventede enheder. Test ideelt set forskellige forekomster af hardwaren. Test f.eks. flere USB-taster i stedet for kun én.

Du kan tillade installation og brug af godkendte eksterne enheder med matchende enhedsforekomst-cd'er ved at konfigurere politikindstillingen [DeviceInstallation/AllowInstallationOfMatchingDeviceInstanceIDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceinstanceids) .

### <a name="prevent-installation-and-usage-of-specifically-prohibited-peripherals-with-matching-device-instance-ids"></a>Undgå installation og brug af særligt forbudte eksterne enheder med matchende enhedsforekomst-cd'er

Eksterne enheder, der ikke kan installeres, kan angives ved hjælp af deres [enhedsforekomst-id'er](/windows-hardware/drivers/install/device-instance-ids). Test konfigurationen, før den rulles ud, for at sikre, at den tillader de forventede enheder. Test ideelt set forskellige forekomster af hardwaren. Test f.eks. flere USB-taster i stedet for kun én.

Du kan forhindre installation af de forbudte ydre enheder med matchende enhedsforekomst-cd'er ved at konfigurere politikindstillingen [DeviceInstallation/PreventInstallationOfMatchingDeviceInstanceIDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceinstanceids) .

### <a name="limit-services-that-use-bluetooth"></a>Begræns de tjenester, der bruger Bluetooth

Ved hjælp af Intune kan du begrænse de tjenester, der kan bruge Bluetooth via ["Bluetooth tilladte tjenester"](/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide). Standardtilstanden for indstillingerne "Bluetooth tilladte tjenester" betyder, at alt er tilladt.  Så snart der tilføjes en tjeneste, bliver den listen over tilladte. Hvis kunden tilføjer værdierne for Tastaturer og Mus og ikke tilføjer filoverførsels-GUID'er, bør filoverførsel blive blokeret.

> [!div class="mx-imgBorder"]
> ![skærmbillede Bluetooth siden med indstillinger.](images/bluetooth.png)

## <a name="prevent-threats-from-removable-storage"></a>Undgå trusler fra flytbart lager

Flytbare lagringsenheder kan introducere yderligere sikkerhedsrisiko for din organisation. Microsoft Defender til Slutpunkt kan hjælpe med at identificere og blokere skadelige filer på flytbare lagringsenheder.

Microsoft Defender til slutpunkt kan også forhindre eksterne USB-enheder i at blive brugt på enheder for at forhindre eksterne trusler. Dette gøres ved hjælp af de egenskaber, der rapporteres af eksterne USB-enheder, for at afgøre, om de kan installeres og bruges på enheden.

Bemærk, at hvis du blokerer USB-enheder eller andre klasser af enheder, der anvender installationspolitikkerne for enheden, kan tilsluttede enheder, f.eks. telefoner, stadig oplade.

> [!NOTE]
> Test og tilpas altid disse indstillinger med en pilotgruppe af brugere og enheder først, før du distribuerer til hele organisationen.

I følgende tabel beskrives de måder, hvorpå Microsoft Defender til slutpunkt kan hjælpe med at forhindre trusler i flytbart lager.

Du kan finde flere oplysninger om kontrol af USB-enheder [i Microsoft Defender for Endpoint-bloggen](https://aka.ms/devicecontrolblog).

<br>

****

|Kontrolelement|Beskrivelse|
|---|---|
|[Aktivér Microsoft Defender Antivirus scanning](#enable-microsoft-defender-antivirus-scanning)|Aktivér Microsoft Defender Antivirus scanning for beskyttelse i realtid eller planlagte scanninger.|
|[Bloker upålidelige og usignerede processer på USB-eksterne enheder](#block-untrusted-and-unsigned-processes-on-usb-peripherals)|Bloker USB-filer, der er usignerede eller upålidelige.|
|[Beskyt dig mod DMA-angreb (Direct Memory Access)](#protect-against-direct-memory-access-dma-attacks)|Konfigurer indstillinger for at beskytte dig mod DMA-angreb.|
|

> [!NOTE]
> Da en uautoriseret USB-ekstern enhed kan have firmware, der efterligner sine USB-egenskaber, anbefaler vi, at du kun tillader specifikt godkendte USB-enheder og begrænser de brugere, der kan få adgang til dem.

### <a name="enable-microsoft-defender-antivirus-scanning"></a>Aktivér Microsoft Defender Antivirus scanning

Beskyttelse af godkendt flytbart lager med [Microsoft Defender Antivirus kræver aktivering](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) af beskyttelse i realtid eller planlægning af scanninger og konfiguration af flytbare drev til scanninger.

- Hvis beskyttelse i realtid er aktiveret, scannes filer, før de åbnes og udføres. Scanningsomfanget omfatter alle filer, herunder dem påmonterede flytbare enheder, f.eks. USB-drev. Du kan eventuelt køre et [PowerShell-script](/samples/browse/?redirectedfrom=TechNet-Gallery) for at udføre en brugerdefineret scanning af et USB-drev, når det ermonteret, så Microsoft Defender Antivirus starter scanningen af alle filer på en flytbar enhed, når den flytbare enhed er tilsluttet. Vi anbefaler dog, at du aktiverer beskyttelse i realtid for at få forbedret scanningsydeevne, især til store lagringsenheder.

- Hvis planlagte scanninger bruges, skal du deaktivere indstillingen DisableRemovableDriveScanning (aktiveret som standard) for at scanne den flytbare enhed under en fuld scanning. Flytbare enheder scannes under en hurtig eller brugerdefineret scanning uanset indstillingen DisableRemovableDriveScanning.

> [!NOTE]
> Vi anbefaler, at du aktiverer overvågning i realtid til scanning. I Intune kan du aktivere overvågning i realtid for **Windows 10 i** \>  \> Enhedsbegrænsninger **Konfigurer Microsoft Defender Antivirus** \> **realtidsovervågning**.

<!-- Need to build out point in the preceding note.
-->

### <a name="block-untrusted-and-unsigned-processes-on-usb-peripherals"></a>Bloker upålidelige og usignerede processer på USB-eksterne enheder

Slutbrugere kan tilslutte flytbare enheder, der er inficeret med malware.
For at forhindre virusser kan et firma blokere USB-filer, der ikke er signerede eller upålidelige.
Alternativt kan virksomheder udnytte overvågningsfunktionen i forbindelse med reduktionsregler for angrebsoverfladen til at overvåge aktiviteten af upålidelige og usignerede processer, der udføres på en USB-ekstern enhed.[](/microsoft-365/security/defender-endpoint/attack-surface-reduction)
Dette kan gøres ved at angive **henholdsvis Ikke-upålidelige** og usignerede processer, der kører  fra USB til henholdsvis **Bloker** eller Overvågning.
Med denne regel kan administratorer forhindre eller overvåge usignerede eller upålidelige eksekverbare filer i at køre fra USB-flytbare drev, herunder SD-kort.
Påvirkede filtyper omfatter eksekverbare filer (f.eks. .exe-, .dll- eller .scr) og scriptfiler som f.eks. en PowerShell-fil (.ps), VisualBasic- (.vbs) eller JavaScript-filer (.js).

Disse indstillinger [kræver aktivering af beskyttelse i realtid](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus).

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/).

2. Klik **på Enheder** \> **Windows Konfigurationspolitikker** \> **Opret** \> **profil**.

    ![Opret enhedskonfigurationsprofil.](images/create-device-configuration-profile.png)

3. Brug følgende indstillinger:
   - Platform: Windows 10 og nyere
   - Profiltype: Enhedsbegrænsninger

   > [!div class="mx-imgBorder"]
   > ![Opret profil til slutpunktsbeskyttelse.](images/create-endpoint-protection-profile.png)

4. Klik **på Opret**.

5. For **Usignerede og upålidelige processer, der kører fra USB, skal** du vælge **Bloker**.

   ![Bloker upålidelige processer.](images/block-untrusted-processes.png)

6. Klik **på OK** for at lukke indstillinger og **Enhedsbegrænsninger**.

### <a name="protect-against-direct-memory-access-dma-attacks"></a>Beskyt dig mod DMA-angreb (Direct Memory Access)

DMA-angreb kan føre til videregivelse af følsomme oplysninger på en pc eller endda indsatte malware, der gør det muligt for hackere at gå uden om låseskærmen eller kontrollere pc'er eksternt. Følgende indstillinger hjælper med at forhindre DMA-angreb:

1. Fra og Windows 10 version 1803 introducerede Microsoft [Kernel DMA Protection til Thunderbolt for](/windows/security/information-protection/kernel-dma-protection-for-thunderbolt.md) at give indbygget beskyttelse mod DMA-angreb via Thunderbolt-porte. Kernel DMA-beskyttelse for Thunderbolt aktiveres af systemproducenter og kan ikke slås til eller fra af brugere.

   Fra og Windows 10 version 1809 kan du justere niveauet for Kernel DMA Protection ved at [konfigurere DMA Guard CSP](/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy). Dette er en ekstra kontrol til eksterne enheder, der ikke understøtter hukommelsesisolation af enheden (også kaldet DMA-remapping). Hukommelsesisolation gør det muligt for operativsystemet at anvende I/O Memory Management Unit (IOMMU) på en enhed til at blokere for tilladt I/O eller hukommelsesadgang fra den eksterne enhed (hukommelsessandkasse). Med andre ord tildeler operativsystemet et bestemt hukommelsesområde til det eksterne udstyr. Hvis den eksterne enhed forsøger at læse/skrive i hukommelsen uden for det tildelte område, blokerer operativsystemet den.

   Eksterne enheder, der understøtter hukommelsesisolation af enheder, kan altid oprette forbindelse. Eksterne enheder, der ikke kan blokeres, tillades eller kun tillades, når brugeren logger på (standard).

2. På Windows 10 systemer, der ikke understøtter Kernel DMA-beskyttelse, kan du:

   - [Bloker DMA, indtil en bruger logger på](/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)
   - [Bloker alle forbindelser via Thunderbolt-portene (herunder USB-enheder)](https://support.microsoft.com/help/2516445/blocking-the-sbp-2-driver-and-thunderbolt-controllers-to-reduce-1394-d)

## <a name="create-customized-alerts-and-response-actions"></a>Oprette brugerdefinerede beskeder og svarhandlinger

Du kan oprette brugerdefinerede beskeder og svarhandlinger med WDATP-forbindelsen og de brugerdefinerede registreringsregler:

**Svarhandlinger for Wdatp Connector:**

**Undersøg:** Initier undersøgelser, indsaml undersøgelsespakke, og isoler en computer.

**Trusselsscanning** på USB-enheder.

**Begræns udførelsen af** alle programmer på computeren undtagen et foruddefineret sæt

MDATP-forbindelse er en af mere end 200 foruddefinerede forbindelser, Outlook, Teams, Slæk osv. Brugerdefinerede forbindelser kan oprettes.

- [Flere oplysninger om Svarhandlinger for WDATP-forbindelse](/connectors/wdatp/)

**Svarhandling for brugerdefinerede registreringsregler:**

Handlinger på både computer- og filniveau kan anvendes.

- [Flere oplysninger om svarhandlinger med brugerdefinerede registreringsregler](/microsoft-365/security/defender-endpoint/custom-detection-rules)

Du kan finde oplysninger om enhedsstyringsrelaterede advance-jagtbegivenheder og eksempler på, hvordan du opretter brugerdefinerede beskeder, under Avancerede jagtopdateringer [: USB-hændelser, handlinger på computerniveau og skemaændringer](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/Advanced-hunting-updates-USB-events-machine-level-actions-and/ba-p/824152).

## <a name="respond-to-threats"></a>Reagere på trusler

Du kan oprette brugerdefinerede beskeder og automatiske svarhandlinger med de brugerdefinerede [registreringsregler for Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/custom-detection-rules). Svarhandlinger inden for den brugerdefinerede registrering dækker handlinger på både computer- og filniveau. Du kan også oprette beskeder og handlinger for autosvar ved [hjælp Power Apps](https://powerapps.microsoft.com/) [og Flow](https://flow.microsoft.com/) med [forbindelsespunktet Microsoft Defender til slutpunkt](/connectors/wdatp/). Forbindelsen understøtter handlinger til undersøgelse, trusselsscanning og begrænsning af kørsel af programmer. Det er en af mere end 200 foruddefinerede forbindelser, herunder Outlook, Teams, Slæk og meget mere. Brugerdefinerede forbindelser kan også oprettes. Se [Forbindelser for at](/connectors/) få mere at vide om forbindelser.

Hvis du f.eks. bruger en af tilgange, kan du automatisk få Microsoft Defender Antivirus køre, når en USB-enhed ermonteret på en computer.

## <a name="related-topics"></a>Relaterede emner

- [Konfigurer beskyttelse i realtid til Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus)
- [Defender/AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)
- [Policy/DeviceInstallation CSP](/windows/client-management/mdm/policy-csp-deviceinstallation)
- [Udføre en brugerdefineret scanning af en flytbar enhed](/samples/browse/?redirectedfrom=TechNet-Gallery)
- [Skabelon til Power BI Enhedsstyring til brugerdefineret rapportering](https://github.com/microsoft/MDATP-PowerBI-Templates)
- [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview.md)
- [Windows beskyttelse af oplysninger](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure.md)
