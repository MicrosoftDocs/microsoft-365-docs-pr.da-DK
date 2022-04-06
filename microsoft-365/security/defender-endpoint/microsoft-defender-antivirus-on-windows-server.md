---
title: Microsoft Defender Antivirus på Windows Server
description: Lær, hvordan du aktiverer Microsoft Defender Antivirus konfigurerer Windows Server 2016, Windows Server 2019 og Windows Server 2022.
keywords: windows defender, server, scep, system center endpoint protection, server 2016, current branch, server 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 04/01/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 412033e274cce22b9350292c612b91ef6e34e209
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634839"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Microsoft Defender Antivirus på Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus fås i følgende udgaver/versioner af Windows Server:

- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 eller nyere
- Windows Server 2016
- Windows Server 2012 R2 (kræver Microsoft Defender for Endpoint)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Konfiguration af Microsoft Defender Antivirus på Windows Server

Processen med at konfigurere og køre Microsoft Defender Antivirus på Windows Server omfatter følgende trin:

1. [Aktivér grænsefladen](#enable-the-user-interface-on-windows-server).
2. [Installér Microsoft Defender Antivirus](#install-microsoft-defender-antivirus-on-windows-server).
3. [Kontrollér Microsoft Defender Antivirus kører](#verify-microsoft-defender-antivirus-is-running).
4. [Opdater din antimalwaresikkerhedsintelligens](#update-antimalware-security-intelligence).
5. (Efter behov) [Sende eksempler](#submit-samples).
6. (Efter behov) [Konfigurer automatisk udeladelse](#configure-automatic-exclusions).
7. (Kun, hvis det er nødvendigt) [Indstil Windows til passiv tilstand](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Aktivere brugergrænsefladen på Windows Server

> [!IMPORTANT]
> Hvis du bruger en Windows Server 2012 R2, skal du se [Indstillinger for at Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Som standard er Microsoft Defender Antivirus installeret og funktionelt på Windows Server. Nogle gange er brugergrænsefladen (GUI) installeret som standard. Den grafiske brugergrænseflade er ikke påkrævet. kan du bruge PowerShell, Gruppepolitik eller andre metoder til at administrere Microsoft Defender Antivirus. Mange organisationer foretrækker dog at bruge GUI til Microsoft Defender Antivirus. For at installere GUI'en skal du bruge en af procedurerne i følgende tabel:

| Procedure | Hvad kan du gøre? |
|:---|:---|
| Aktivere den grafiske brugergrænseflade ved hjælp af guiden Tilføj roller og funktioner | 1. Se [Installér roller,](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) rolletjenester og funktioner ved hjælp af guiden Tilføj roller og funktioner, og brug **guiden Tilføj roller og funktioner**. <br/><br/>2. Når du kommer til trinnet  Funktioner i guiden, skal **du under Windows Defender vælge** **GUI for Windows Defender** indstillinger. |
| Slå GUI til ved hjælp af PowerShell | 1. På Windows Server skal Windows PowerShell som administrator. <br/><br/>2. Kør følgende PowerShell-cmdlet: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installere Microsoft Defender Antivirus på Windows Server

Hvis du skal installere eller geninstallere Microsoft Defender Antivirus på Windows Server, skal du bruge en af fremgangsmåderne i følgende tabel:

| Procedure | Hvad kan du gøre? |
|:---|:---|
| Brug guiden Tilføj roller og funktioner til at installere Microsoft Defender Antivirus | 1. Se [Installere eller fjerne roller, rolletjenester eller](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) funktioner og bruge **guiden Tilføj roller og funktioner**. <br/><br/>2. Når du kommer til **trinnet** Funktioner i guiden, skal du Microsoft Defender Antivirus indstillingen. Vælg også **GUI for Windows Defender** indstilling. |
| Brug PowerShell til at installere Microsoft Defender Antivirus | 1. På Windows Server skal Windows PowerShell som administrator. <br/><br/>2. Kør følgende PowerShell-cmdlet: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Hændelsesmeddelelser for det antimalwareprogram, der Microsoft Defender Antivirus, kan findes [i Microsoft Defender Antivirus hændelser](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Kontrollér Microsoft Defender Antivirus kører

Når du har installeret (eller geninstalleret) Microsoft Defender Antivirus, er det næste trin at kontrollere, at det kører. Brug PowerShell-cmdletterne i følgende tabel:

| Procedure | PowerShell-cmdlet |
|:---|:---|
| Kontrollér, Microsoft Defender Antivirus kører | `Get-Service -Name windefend` |
| Kontrollér, at firewallbeskyttelse er slået til | `Get-Service -Name mpssvc` |

Som et alternativ til PowerShell kan du bruge Kommandoprompt til at bekræfte, Microsoft Defender Antivirus kører. Det gør du ved at køre følgende kommando fra en kommandoprompt:

```cmd
sc query Windefend
```

Kommandoen `sc query` returnerer oplysninger om Microsoft Defender Antivirus tjeneste. Når Microsoft Defender Antivirus kører, viser `STATE` værdien `RUNNING`.

Hvis du vil have vist alle de tjenester, der ikke kører, skal du køre følgende PowerShell-cmdlet:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Opdater antimalwaresikkerhedsintelligens

For at få dine almindelige sikkerhedsintelligensopdateringer skal Windows Update køre. Hvis du bruger en opdateringsstyringstjeneste, f.eks. Windows Server Update Services (WSUS), skal du sikre dig, at opdateringer til Microsoft Defender Antivirus Sikkerhedsintelligens er godkendt til de computere, du administrerer.

Som standard downloader Windows Update ikke opdateringer automatisk på Windows Server 2019 eller Windows Server 2022 eller Windows Server 2016. Du kan ændre denne konfiguration ved hjælp af en af følgende metoder:

| Metode | Beskrivelse |
|---|---|
| **Windows Update** i Kontrolpanel | **Installation af opdateringer resulterer** automatisk i, at alle opdateringer installeres automatisk, Windows Defender sikkerhedsintelligensopdateringer. <br/><br/> **Download opdateringer, men lad mig vælge**, om jeg vil installere dem, Windows Defender at downloade og installere Sikkerhedsintelligens-opdateringer automatisk, men andre opdateringer installeres ikke automatisk. |
| **Gruppepolitik** | Du kan konfigurere og administrere Windows Update ved hjælp af de indstillinger, der er tilgængelige i Gruppepolitik, på følgende sti: **Administrative skabeloner\Windows Components\Windows Update\Configure Automatic Updates** |
| **Registreringsdatabasenøglen AUOptions** | Følgende to værdier gør det muligt Windows Update hente og installere Sikkerhedsintelligens-opdateringer automatisk: <br/><br/> **4** -  **Installér opdateringer automatisk**. Denne værdi medfører, at alle opdateringer installeres automatisk, Windows Defender sikkerhedsintelligensopdateringer. <br/><br/> **3** -  **Hent opdateringer, men lad mig vælge, om jeg vil installere dem**. Denne værdi gør Windows Defender at downloade og installere Sikkerhedsintelligens-opdateringer automatisk, men andre opdateringer installeres ikke automatisk. |

For at sikre at beskyttelse mod malware bevares, skal du aktivere følgende tjenester:

- Windows Fejlrapportering tjeneste
- Windows Update tjeneste

I følgende tabel vises tjenesterne for Microsoft Defender Antivirus og de afhængige tjenester.

| Tjenestenavn | Filplacering | Beskrivelse |
|---|---|---|
| Windows Defender tjeneste (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Dette er den primære Microsoft Defender Antivirus, der skal køre altid.|
| Windows Fejlrapportering tjeneste (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Denne tjeneste sender fejlrapporter tilbage til Microsoft. |
| Windows Defender Firewall (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Vi anbefaler, at du Windows Defender Firewall-tjenesten. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update er nødvendig for at få sikkerhedsintelligensopdateringer og opdateringer til antimalwareprogrammet |

## <a name="submit-samples"></a>Sende eksempler

Eksempel på indsendelse giver Microsoft mulighed for at indsamle eksempler på potentielt skadelig software. For at give fortsat og opdateret beskyttelse bruger Microsofts stikprøver disse stikprøver til at analysere mistænkelige aktiviteter og producere opdateret antimalwaresikkerhedsintelligens. Vi indsamler eksekverbare programfiler, f.eks. .exe filer .dll filer. Vi indsamler ikke filer, der indeholder personlige data, f.eks. Microsoft Word dokumenter og PDF-filer.

### <a name="submit-a-file"></a>Send en fil

1. Gennemse [indsendelsesvejledningen](/windows/security/threat-protection/intelligence/submission-guide).

2. Gå til [eksempelindsendelsesportalen](https://www.microsoft.com/wdsi/filesubmission), og indsend din fil.

### <a name="enable-automatic-sample-submission"></a>Aktivér automatisk indsendelse af eksempler

Hvis du vil aktivere automatisk indsendelse af eksempler, skal du starte en Windows PowerShell-konsol som administrator og angive **værdien SubmitSamplesConsent** i overensstemmelse med en af følgende indstillinger:

|Indstilling|Beskrivelse|
|---|---|
| **0** -  **Spørg altid** | Den Microsoft Defender Antivirus beder dig om at bekræfte indsendelsen af alle nødvendige filer. Dette er standardindstillingen for Microsoft Defender Antivirus, men anbefales ikke til installationer på Windows Server 2016 eller 2019 eller Windows Server 2022 uden en GUI. |
| **1**  -  **Send sikre eksempler automatisk** | Tjenesten Microsoft Defender Antivirus sender alle filer, der er markeret som "sikre", og beder om resten af filerne. |
| **2** -  **Send aldrig** | Den Microsoft Defender Antivirus tjeneste spørger ikke og sender ikke nogen filer. |
| **3** -  **Send alle eksempler automatisk** | Tjenesten Microsoft Defender Antivirus sender alle filer uden at blive bedt om at bekræfte. |

> [!NOTE]
> Denne indstilling er ikke tilgængelig for Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Konfigurere automatiske udeladelse

For at sikre sikkerhed og ydeevne tilføjes visse undtagelser automatisk baseret på de roller og funktioner, du installerer, når du bruger Microsoft Defender Antivirus på Windows Server 2016 eller 2019 eller Windows Server 2022.

Se [Konfigurere udeladelse i Microsoft Defender Antivirus på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Passiv tilstand og Windows Server

Hvis du bruger et antivirusprodukt, der ikke er Microsoft, som din primære antivirusløsning på Windows Server, skal du indstille Microsoft Defender Antivirus til passiv tilstand eller deaktiveret tilstand. Hvis din Windows serverslutpunkt er onboardet til Microsoft Defender for Endpoint, kan du angive Microsoft Defender Antivirus til passiv tilstand. Hvis du ikke bruger en Microsoft Defender for Endpoint, skal du indstille Microsoft Defender Antivirus til deaktiveret tilstand. 

> [!TIP]
> Se [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md).

I følgende tabel beskrives metoder til at indstille Microsoft Defender Antivirus til passiv tilstand, deaktivere Microsoft Defender Antivirus og fjerne Microsoft Defender Antivirus:

| Procedure | Beskrivelse |
|---|---|
| Indstil Microsoft Defender Antivirus til passiv tilstand ved hjælp af en registreringsdatabasenøgle | Angiv registreringsdatabasenøglen ForceDefenderPassiveMode på følgende måde: <br/>- Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Navn: `ForceDefenderPassiveMode` <br/>- Type: `REG_DWORD` <br/>- Værdi: `1` |
| Deaktivere brugergrænsefladen Microsoft Defender Antivirus brugergrænsefladen ved hjælp af PowerShell | Åbn Windows PowerShell som administrator, og kør følgende PowerShell-cmdlet:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Deaktiver Microsoft Defender Antivirus hjælp af PowerShell | Brug følgende PowerShell-cmdlet: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Deaktivere Microsoft Defender Antivirus ved hjælp af guiden Fjern roller og funktioner | Se [Installere eller fjerne roller, rolletjenester eller funktioner](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) og bruge **guiden Fjern roller og funktioner**. <br/><br/>Når du kommer til **trinnet** Funktioner i guiden, skal du **Windows Defender indstillingen** Funktioner. <br/><br/> Hvis du fjerner **markeringen Windows Defender** sig selv under **sektionen Windows Defender Funktioner**, bliver du bedt om at fjerne grænsefladeindstillingen **GUI for Windows Defender**.<br/><br/>Microsoft Defender Antivirus kører stadig normalt uden brugergrænsefladen, men brugergrænsefladen kan ikke aktiveres, hvis du deaktiverer **kernefunktionen Windows Defender** brugergrænsefladen. |
| Fjern Microsoft Defender Antivirus ved hjælp af PowerShell | Brug følgende PowerShell-cmdlet: `Uninstall-WindowsFeature -Name Windows-Defender` |
| Deaktivere Microsoft Defender Antivirus ved hjælp af Gruppepolitik | I din Lokale Gruppepolitik-editor skal du gå til **Administrativ** >  **skabelon Windows Component** >  **Endpoint Protection** >  **Disable Endpoint Protection** og derefter **vælge EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Bruger du Windows Server 2012 R2 eller Windows Server 2016?

Hvis din Windows-server er onboardet til Microsoft Defender for Endpoint, kan du nu køre Microsoft Defender Antivirus i passiv tilstand på Windows Server 2012 R2 og Windows Server 2016. Se følgende artikler:

- [Indstillinger for installation Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows](microsoft-defender-antivirus-windows.md)

