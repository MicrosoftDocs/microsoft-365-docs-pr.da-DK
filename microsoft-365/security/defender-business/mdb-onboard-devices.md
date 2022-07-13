---
title: Om bord på enheder til Microsoft Defender til virksomheder
description: Se, hvordan du får enheder onboardet til Defender for Business for at beskytte dine enheder fra dag 1.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9b4228ba31594e8c6893d4bc45e2fc1994139231
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772210"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>Om bord på enheder til Microsoft Defender til virksomheder

Med Defender for Business har du flere muligheder at vælge imellem til onboarding af din virksomheds enheder. I denne artikel gennemgås disse muligheder, og du får et overblik over, hvordan onboarding fungerer.

## <a name="what-to-do"></a>Sådan gør du

1. Vælg en fane: 
   - **Windows 10 og 11**
   - **Mac**
   - **Servere** (NY! Windows Server eller Linux Server)
   - **Mobil** (til iOS-/iPadOS- eller Android-enheder)
2. Få vist dine onboardingindstillinger, og følg vejledningen på den valgte fane.
3. Fortsæt til de næste trin.

## <a name="windows-10-and-11"></a>[**Windows 10 og 11**](#tab/Windows10and11)

## <a name="windows-10-and-11"></a>Windows 10 og 11

Vælg en af følgende indstillinger for at føje Windows-klientenheder til Defender for Business:

- [Lokalt script](#local-script-for-windows-10-and-11) (til onboarding af enheder manuelt på portalen Microsoft 365 Defender)
- [Gruppepolitik](#group-policy-for-windows-10-and-11) (hvis du allerede bruger Gruppepolitik i din organisation)
- [Microsoft Intune](#intune-for-windows-10-and-11) (inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md))

### <a name="local-script-for-windows-10-and-11"></a>Lokalt script for Windows 10 og 11

Du kan bruge et lokalt script til at onboarde Windows-klientenheder. Når du kører onboardingscriptet på en enhed, oprettes der et tillidsforhold til Azure Active Directory, hvis denne tillid ikke allerede findes. tilmelder enheden i Microsoft Intune, hvis den ikke allerede er tilmeldt, og onboarder derefter enheden til Defender for Business. Den lokale scriptmetode fungerer, selvom du ikke har Intune i øjeblikket, og det er den anbefalede metode til Defender for Business-kunder.

> [!TIP]
> Vi anbefaler, at du onboarder op til 10 enheder ad gangen, når du bruger den lokale scriptmetode.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** > **Slutpunkter** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

3. Vælg **Windows 10 og 11**, og vælg derefter **Lokalt script** i afsnittet **Installationsmetode**. 

4. Vælg **Download onboarding-pakke**. Vi anbefaler, at du gemmer onboardingpakken på et flytbart drev.

5. På en Windows-enhed skal du udtrække indholdet af konfigurationspakken til en placering, f.eks. mappen Desktop. Du skal have en fil med navnet `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. Åbn en kommandoprompt som administrator.

7. Skriv placeringen af scriptfilen. Hvis du f.eks. kopierede filen til mappen Desktop, skulle du skrive `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`og derefter trykke på tasten Enter (eller vælge **OK**).

8. Når scriptet er kørt, [skal du køre en registreringstest](#run-a-detection-test-on-a-windows-10-or-11-device).

### <a name="group-policy-for-windows-10-and-11"></a>Gruppepolitik for Windows 10 og 11

Hvis du foretrækker at bruge Gruppepolitik til at onboarde Windows-klienter, skal du følge vejledningen i [Onboard Windows-enheder ved hjælp af Gruppepolitik](../defender-endpoint/configure-endpoints-gp.md). I denne artikel beskrives trinnene til onboarding til Microsoft Defender for Endpoint. Trinnene til onboarding til Defender for Business er de samme.

### <a name="intune-for-windows-10-and-11"></a>Intune for Windows 10 og 11

Hvis dit abonnement omfatter Intune, kan du onboarde Windows-klienter og andre enheder i Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Hvis du f.eks. har [Microsoft 365 Business Premium](../../business/index.yml), har du allerede Intune som en del af dit abonnement, og du kan bruge Intune til at onboarde enheder.  

Der findes flere metoder til tilmelding af enheder i Intune. Vi anbefaler, at du bruger en af følgende metoder:

- [Aktivér automatisk windows-tilmelding](/mem/intune/enrollment/windows-enroll) til virksomhedsejede eller virksomhedsadministrerede enheder
- [Bed brugerne om at tilmelde deres egne Windows 10/11-enheder på Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-10-and-11"></a>Sådan aktiveres automatisk tilmelding for Windows 10 og 11

Når du konfigurerer automatisk tilmelding, føjer brugerne deres arbejdskonto til enheden. I baggrunden registrerer og tilmelder enheden sig Azure Active Directory (Azure AD) og er tilmeldt Intune.

1. Gå til Azure Portal ([https://portal.azure.com/](https://portal.azure.com/)), og log på.

2. Vælg **Azure Active Directory** > **Mobility (MDM og MAM)** > **Microsoft Intune**.

3. Konfigurer **MDM-brugeromfanget** og **MAM-brugeromfanget**.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="Skærmbillede af angivelse af MDM-brugeromfang og MAM-brugeromfang i Intune.":::

   - I forbindelse med MDM-brugerområde anbefaler vi, at du vælger **Alle** , så alle brugere automatisk kan tilmelde deres Windows-enheder.
   - I afsnittet MAM-brugerområde anbefaler vi følgende standardværdier for URL-adresserne:

       - **MDM Vilkår for anvendelse AF URL-adresse**
       - **URL-adresse til MDM-registrering**
       - **URL-adresse til MDM-overholdelse**

4. Vælg **Gem**.

5. Når en enhed er tilmeldt Intune, kan du føje den til en enhedsgruppe i Defender for Business. [Få mere at vide om enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

> [!TIP]
> Du kan få mere at vide under [Aktivér automatisk tilmelding til Windows](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-10-and-11-devices"></a>Sådan tilmelder brugerne deres egne Windows 10 og 11 enheder

1. Se følgende video for at se, hvordan tilmelding fungerer:<br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. Del denne artikel med brugere i din organisation: [Tilmeld Windows 10/11-enheder i Intune](/mem/intune/user-help/enroll-windows-10-device).

3. Når en enhed er tilmeldt Intune, kan du føje den til en enhedsgruppe i Defender for Business. [Få mere at vide om enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

### <a name="run-a-detection-test-on-a-windows-10-or-11-device"></a>Kør en registreringstest på en Windows 10 eller 11-enhed

Når du har onboardet Windows-enheder til Defender for Business, kan du køre en registreringstest på enheden for at sikre, at alt fungerer korrekt.

1. Opret en mappe på Windows-enheden: `C:\test-MDATP-test`.

2. Åbn en kommandoprompt som administrator.

3. Kør følgende PowerShell-kommando i vinduet Kommandoprompt:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Når kommandoen er kørt, lukkes kommandopromptvinduet automatisk. Hvis det lykkes, markeres registreringstesten som fuldført, og der vises en ny besked på portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) for den nyligt onboardede enhed om ca. 10 minutter.

## <a name="view-a-list-of-onboarded-devices"></a>Få vist en liste over onboardede enheder

Hvis du vil have vist listen over enheder, der er onboardet til Defender for Business, skal du gå til portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Vælg **Enhedslager** under **Slutpunkter** i navigationsruden.

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge fanen for disse enheder ([Windows 10 og 11, Mac, servere eller mobilenheder](#what-to-do)) og følge vejledningen på denne fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Defender for Business](mdb-configure-security-settings.md)
- Se [Kom i gang med at bruge Defender for Business](mdb-get-started.md).

## <a name="mac"></a>[**Mac**](#tab/mac)

## <a name="mac"></a>Mac

> [!NOTE]
> Vi anbefaler, at du bruger et [lokalt script til at onboarde Mac](#local-script-for-mac). Selvom du kan [konfigurere tilmelding til Mac ved hjælp af Intune](/mem/intune/enrollment/macos-enroll), er det lokale script den nemmeste metode til onboarding af Mac til Defender for Business. 

Vælg en af følgende muligheder for at onboarde Mac:

- [Lokalt script til Mac](#local-script-for-mac) (*anbefales*)
- [Intune til Mac](#intune-for-mac)

### <a name="local-script-for-mac"></a>Lokalt script til Mac

Når du kører det lokale script på en Mac, oprettes der et tillidsforhold til Azure Active Directory, hvis denne tillid ikke allerede findes. tilmelder Mac i Microsoft Intune, hvis den ikke allerede er tilmeldt, og onboarder derefter Mac til Defender for Business. Den lokale scriptmetode fungerer, selvom du ikke har Intune i øjeblikket. Vi anbefaler, at du onboarder op til 10 enheder ad gangen ved hjælp af denne metode.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** > **Slutpunkter** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

3. Vælg **macOS**. Vælg **Lokalt script** i afsnittet **Installationsmetode**. 

4. Vælg **Download onboarding-pakke**, og gem den på et flytbart drev. Vælg også **Download installationspakken**, og gem den på din flytbare enhed.

5. På en Mac skal du gemme installationspakken i `wdav.pkg` en lokal mappe.

6. Gem onboardingpakken som `WindowsDefenderATPOnboardingPackage.zip` i den samme mappe, som du brugte til installationspakken.

7. Brug Finder til at navigere til `wdav.pkg` dig, der er gemt, og åbn den derefter.

8. Vælg **Fortsæt**, acceptér licensvilkårene, og angiv derefter din adgangskode, når du bliver bedt om det.

9. Du bliver bedt om at tillade installation af en driver fra Microsoft (enten "System Extension Blocked" eller "Installation er i venteposition" eller begge dele). Du skal tillade driverinstallationen: Vælg **Åbn sikkerhedsindstillinger** eller **Åbn systemindstillinger** > **Sikkerhed & Beskyttelse af personlige oplysninger**, og vælg derefter **Tillad**.

10. Brug følgende Python-kommando i Bash til at køre onboardingpakken: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.sh`

Når en Mac er tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

### <a name="intune-for-mac"></a>Intune til Mac

Hvis dit abonnement omfatter Microsoft Intune, kan du onboarde Mac i Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Hvis du f.eks. har [Microsoft 365 Business Premium](../../business/index.yml), har du allerede Intune som en del af dit abonnement.  

Der findes flere metoder til tilmelding af Mac i Intune. Vi anbefaler en af følgende metoder:

- [Vælg en indstilling for virksomhedsejet Mac](#options-for-company-owned-mac)
- [Bed brugerne om at tilmelde deres egen Mac på Intune](#ask-users-to-enroll-their-own-mac-in-intune)

#### <a name="options-for-company-owned-mac"></a>Indstillinger for virksomhedsejet Mac

Vælg en af følgende indstillinger for at tilmelde virksomhedsadministrerede Mac-enheder i Intune:

| Mulighed  | Beskrivelse  |
|---------|---------|
| Apple Automated Device Enrollment |  Brug denne metode til at automatisere tilmelding på enheder, der er købt via Apple Business Manager eller Apple School Manager. Automatiseret tilmelding af enheder installerer tilmeldingsprofilen "via luften", så du ikke behøver at have fysisk adgang til enheder. <br/><br/>Se [Tilmeld Mac automatisk med Apple Business Manager eller Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| Administrator af enhedsregistrering (DEM)  |  Brug denne metode til udrulninger i stor skala, og når der er flere personer i din organisation, som kan hjælpe med konfiguration af tilmelding. En person med administratorrettigheder til enhedsregistrering kan tilmelde op til 1.000 enheder med en enkelt Azure Active Directory-konto. Denne metode bruger Firmaportal-appen eller Microsoft Intune-appen til at tilmelde enheder. Du kan ikke bruge en demografikonto til at tilmelde enheder via automatiseret enhedsregistrering.<br/><br/> Se [Tilmeld enheder i Intune ved hjælp af en administratorkonto til enhedsregistrering](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| Direkte tilmelding  | Direkte tilmelding tilmelder enheder uden brugertilhør, så denne metode er bedst til enheder, der ikke er knyttet til en enkelt bruger. Denne metode kræver, at du har fysisk adgang til de Macs, du tilmelder dig. <br/><br/>Se [Brug direkte tilmelding til Mac](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-mac-in-intune"></a>Bed brugerne om at tilmelde deres egen Mac på Intune

Hvis din virksomhed foretrækker at få personer til at tilmelde deres egne enheder i Intune, kan du bede brugerne om at følge disse trin:

1. Gå til webstedet Firmaportal ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)), og log på.

2. Følg vejledningen på Firmaportal websted for at tilføje deres enhed.

3. Installér Firmaportal-appen på [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac), og følg vejledningen i appen.

### <a name="confirm-that-a-mac-is-onboarded"></a>Bekræft, at en Mac er onboardet

1. Hvis du vil bekræfte, at enheden er knyttet til din virksomhed, skal du bruge følgende Python-kommando i Bash:

   `mdatp health --field org_id`.

2. Hvis du bruger macOS 10.15 (Catalina) eller nyere, skal du give Defender for Business-samtykke for at beskytte din enhed. Gå til **Systemindstillinger** > **Sikkerhed & Beskyttelse af personlige oplysninger** >  > **Fuld diskadgang**. Vælg låseikonet nederst i dialogboksen for at foretage ændringer, og vælg derefter **Microsoft Defender til virksomheder** (eller **Defender for Endpoint**, hvis det er det, du ser).

3. Hvis du vil bekræfte, at enheden er onboardet, skal du bruge følgende kommando i Bash:

   `mdatp health --field real_time_protection_enabled`

Når en enhed er tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>Få vist en liste over onboardede enheder

Hvis du vil have vist listen over enheder, der er onboardet til Defender for Business, skal du gå til portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Vælg **Enhedslager** under **Slutpunkter** i navigationsruden.

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge fanen for disse enheder ([Windows 10 og 11, Mac, servere eller mobilenheder](#what-to-do)) og følge vejledningen på denne fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Defender for Business](mdb-configure-security-settings.md).
- Se [Kom i gang med at bruge Defender for Business](mdb-get-started.md).

## <a name="servers"></a>[**Servere**](#tab/Servers)

## <a name="servers"></a>Servere

> [!NOTE]
> **Muligheden for at onboarde en server er i øjeblikket en prøveversion**.

Vælg operativsystemet til serveren:

- [Windows Server](#windows-server)
- [Linux Server](#linux-server)

## <a name="windows-server"></a>Windows Server

> [!IMPORTANT]
> **Muligheden for at onboarde Windows Server-slutpunkter er i øjeblikket en prøveversion**. Sørg for, at du opfylder følgende krav, før du onboarder et Windows Server-slutpunkt:
> - Indstillingen **Prøveversionsfunktioner** er slået til. På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) skal du gå til **Indstillinger** > **Slutpunkter** > **Prøveversionsfunktioner til generelle** > **avancerede funktioner** > .
> - Håndhævelsesområdet for Windows Server er slået til. Gå til **Indstillinger** > **Slutpunkter** > **Administration af** >  konfiguration **Håndhævelsesområde**. Vælg **Brug MDE til at gennemtvinge sikkerhedskonfigurationsindstillinger fra MEM**, vælg  **Windows Server**, og vælg derefter **Gem**.

Du kan onboarde en forekomst af Windows Server til Defender for Business ved hjælp af et lokalt script.

### <a name="local-script-for-windows-server"></a>Lokalt script til Windows Server

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Indstillinger** > **Slutpunkter** i navigationsruden, og vælg derefter **Onboarding** under **Enhedshåndtering**.

3. Vælg et operativsystem, f.eks **. Windows Server 1803, 2019 og 2022**, og vælg derefter **Lokalt script** i afsnittet **Installationsmetode**. 

   Hvis du vælger **Windows Server 2012 R2 og 2016**, har du to pakker at downloade og køre: en installationspakke og en onboardingpakke. Installationspakken indeholder en MSI-fil, der installerer Defender for Business Agent. Onboardingpakken indeholder scriptet til onboarding af dit Windows Server-slutpunkt til Defender for Business.

4. Vælg **Download onboarding-pakke**. Vi anbefaler, at du gemmer onboardingpakken på et flytbart drev.

   Hvis du har valgt **Windows Server 2012 R2 og 2016**, skal du også vælge **Download installationspakke** og gemme pakken på et flytbart drev

5. Udpak indholdet af installations-/onboardingpakken på dit Windows Server-slutpunkt på en placering, f.eks. desktopmappen. Du skal have en fil med navnet `WindowsDefenderATPLocalOnboardingScript.cmd`. 

   Hvis du onboarder Windows Server 2012 R2 eller Windows Server 2016, skal du først pakke installationspakken ud.

6. Åbn en kommandoprompt som administrator.

7. Hvis du onboarder Windows Server 2012R2 eller Windows Server 2016, skal du køre følgende kommando:

   `Msiexec /i md4ws.msi /quiet` 

   Hvis du onboarder Windows Server 1803, 2019 eller 2022, skal du springe dette trin over og gå til trin 8.

8. Skriv placeringen af scriptfilen. Hvis du f.eks. kopierede filen til mappen Desktop, skal du skrive `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`og derefter trykke på Enter (eller vælge **OK**).

9. Gå til [Kør en registreringstest på Windows Server](#run-a-detection-test-on-windows-server).

### <a name="run-a-detection-test-on-windows-server"></a>Kør en registreringstest på Windows Server

Når du har onboardet dit Windows Server-slutpunkt til Defender for Business, kan du køre en registreringstest for at sikre, at alt fungerer korrekt:

1. Opret en mappe på Windows Server-enheden: `C:\test-MDATP-test`.

2. Åbn en kommandoprompt som administrator.

3. Kør følgende PowerShell-kommando i vinduet Kommandoprompt:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

Når kommandoen er kørt, lukkes kommandopromptvinduet automatisk. Hvis det lykkes, markeres registreringstesten som fuldført, og der vises en ny besked på portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) for den nyligt onboardede enhed om ca. 10 minutter.

## <a name="linux-server"></a>Linux Server

> [!IMPORTANT]
> **Muligheden for at onboarde Linux Server-slutpunkter er i øjeblikket en prøveversion**. Sørg for, at du opfylder følgende krav, før du onboarder et Linux Server-slutpunkt:
> - Indstillingen **Prøveversionsfunktioner** er slået til. På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) skal du gå til **Indstillinger** > **Slutpunkter** > **Prøveversionsfunktioner til generelle** > **avancerede funktioner** > .
> - Du opfylder [forudsætningerne for Microsoft Defender for Endpoint på Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).

### <a name="onboard-linux-server-endpoints"></a>Onboard Linux Server-slutpunkter

Du kan bruge følgende metoder til at onboarde en forekomst af Linux Server til Defender for Business:

- **Lokalt script:** Se [Installér Microsoft Defender for Endpoint på Linux manuelt](../defender-endpoint/linux-install-manually.md).
- **Ansible:** Se [Installér Microsoft Defender for Endpoint på Linux med Ansible](../defender-endpoint/linux-install-with-ansible.md).
- **Kok:** Se [Installér Defender for Endpoint på Linux med chef](../defender-endpoint/linux-deploy-defender-for-endpoint-with-chef.md).
- **Marionet:** Se [Installér Microsoft Defender for Endpoint på Linux med Dukke](../defender-endpoint/linux-install-with-puppet.md).

> [!NOTE]
> Onboarding af en forekomst af Linux Server til Defender for Business er det samme som onboarding til [Microsoft Defender for Endpoint på Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md).

## <a name="view-a-list-of-onboarded-devices"></a>Få vist en liste over onboardede enheder

Hvis du vil have vist listen over enheder, der er onboardet til Defender for Business, skal du gå til portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Vælg **Enhedslager** under **Slutpunkter** i navigationsruden.

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge fanen for disse enheder ([Windows 10 og 11, Mac, servere eller mobilenheder](#what-to-do)) og følge vejledningen på denne fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Defender for Business](mdb-configure-security-settings.md).
- Se [Kom i gang med at bruge Defender for Business](mdb-get-started.md).

## <a name="mobile-devices"></a>[**Mobilenheder**](#tab/mobiles)

## <a name="mobile-devices"></a>Mobilenheder

Du skal bruge Microsoft Intune til at onboarde mobilenheder, f.eks. Android- og iOS-/iPadOS-enheder. Hvis du har [Microsoft 365 Business Premium](../../business/index.yml), har du Intune. 

Se følgende ressourcer for at få hjælp til at tilmelde disse enheder til Intune:

- [Tilmeld Android-enheder](/mem/intune/enrollment/android-enroll)
- [Tilmeld iOS- eller iPadOS-enheder](/mem/intune/enrollment/ios-enroll)

Når en enhed er tilmeldt Intune, kan du føje den til en enhedsgruppe. [Få mere at vide om enhedsgrupper i Defender for Business](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>Næste trin

- Hvis du har andre enheder at onboarde, skal du vælge fanen for disse enheder ([Windows 10 og 11, Mac, servere eller mobilenheder](#what-to-do)) og følge vejledningen på denne fane.
- Hvis du er færdig med at onboarde enheder, skal du gå til [Trin 5: Konfigurer dine sikkerhedsindstillinger og politikker i Defender for Business](mdb-configure-security-settings.md).
- Se [Kom i gang med at bruge Defender for Business](mdb-get-started.md).
