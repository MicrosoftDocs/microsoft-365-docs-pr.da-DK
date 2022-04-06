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
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 01/26/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 4962537e86010fceeb2845fdd6408270c97742dc
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469751"
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

I nogle tilfælde Microsoft Defender Antivirus kaldes det *Endpoint Protection*, men protectionprogrammet er det samme. Selvom funktionalitet, konfiguration og administration i høj grad er ens for [Microsoft Defender Antivirus på Windows 10](microsoft-defender-antivirus-windows.md) og Windows 11, er der nogle få vigtige forskelle på Windows Server:

- På Windows server anvendes [automatiske udeladelser](configure-server-exclusions-microsoft-defender-antivirus.md) baseret på din definerede Serverrolle.

- På Windows Server går Microsoft Defender Antivirus hverken i passiv tilstand eller deaktiveret tilstand automatisk, hvis du kører en ikke-Microsoft-antivirus-/antimalwareløsning. Du kan dog indstille Microsoft Defender Antivirus til passiv eller deaktiveret tilstand manuelt.

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Konfiguration af Microsoft Defender Antivirus på Windows Server

Processen med at konfigurere og køre Microsoft Defender Antivirus på en serverplatform indeholder adskillige trin:

1. [Aktivér grænsefladen](#enable-the-user-interface-on-windows-server).
2. [Installér Microsoft Defender Antivirus](#install-microsoft-defender-antivirus-on-windows-server).
3. [Kontrollér Microsoft Defender Antivirus kører](#verify-microsoft-defender-antivirus-is-running).
4. [Opdater din antimalwaresikkerhedsintelligens](#update-antimalware-security-intelligence).
5. (Efter behov) [Sende eksempler](#submit-samples).
6. (Efter behov) [Konfigurer automatisk udeladelse](#configure-automatic-exclusions).
7. (Kun, hvis det er nødvendigt) [Indstil Windows til passiv tilstand](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Aktivere brugergrænsefladen på Windows Server

Som standard er Microsoft Defender Antivirus installeret og funktionelt på Windows Server. Nogle gange er brugergrænsefladen (GUI) installeret som standard, men gui'en er ikke påkrævet. Du kan bruge PowerShell, Gruppepolitik eller andre metoder til at administrere Microsoft Defender Antivirus.

Hvis gui'en ikke er installeret på serveren, og du vil installere den, skal du enten bruge  guiden Tilføj roller og funktioner eller PowerShell-cmdlet'er.

> [!NOTE]
> Denne indstilling er ikke tilgængelig for Windows Server 2012 R2. Du kan finde flere oplysninger [under Indstillinger for installation Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>Aktivere den grafiske brugergrænseflade ved hjælp af guiden Tilføj roller og funktioner

1. Se [Installér roller, rolletjenester og](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) funktioner ved hjælp af guiden Tilføj roller og funktioner, og brug **guiden Tilføj roller og funktioner**.

2. Når du kommer til **trinnet** Funktioner i guiden, skal **du under Windows Defender vælge** **GUI for Windows Defender** indstillinger.

   I Windows Server 2016 **ser guiden Tilføj roller og funktioner** sådan ud:

   :::image type="content" source="images/server-add-gui.png" alt-text="Guiden Tilføj roller og funktioner, der viser GUI for Windows Defender indstillinger." lightbox="images/server-add-gui.png":::

   I Windows Server 2019 og Windows Server 2022 minder guiden Tilføj roller **og** funktioner om hinanden.

### <a name="turn-on-the-gui-using-powershell"></a>Slå GUI til ved hjælp af PowerShell

Følgende PowerShell-cmdlet aktiverer grænsefladen:

```powershell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installere Microsoft Defender Antivirus på Windows Server

Hvis du skal installere eller geninstallere Microsoft Defender Antivirus på Windows Server, kan du gøre dette ved enten at bruge guiden Tilføj roller og **funktioner** eller PowerShell.

### <a name="use-the-add-roles-and-features-wizard-to-install-microsoft-defender-antivirus"></a>Brug guiden Tilføj roller og funktioner til at installere Microsoft Defender Antivirus

1. Se denne [artikel](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), og brug **guiden Tilføj roller og funktioner**.

2. Når du kommer til **trinnet** Funktioner i guiden, skal du Microsoft Defender Antivirus indstillingen. Vælg også **GUI for Windows Defender** indstilling.

### <a name="use-powershell-to-install-microsoft-defender-antivirus"></a>Brug PowerShell til at installere Microsoft Defender Antivirus

Hvis du vil bruge PowerShell til at Microsoft Defender Antivirus, skal du køre følgende cmdlet:

```powershell
Install-WindowsFeature -Name Windows-Defender
```

Hændelsesmeddelelser for det antimalwareprogram, der Microsoft Defender Antivirus, kan findes [i Microsoft Defender Antivirus hændelser](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Kontrollér Microsoft Defender Antivirus kører

Når Microsoft Defender Antivirus er installeret, er det næste trin at kontrollere, at den kører. På slutpunktet Windows Server skal du køre følgende PowerShell-cmdlet:

```powershell
Get-Service -Name windefend
```

Kør følgende PowerShell-cmdlet for at bekræfte, at firewallbeskyttelse er slået til:

```powershell
Get-Service -Name mpssvc
```

Som et alternativ til PowerShell kan du bruge Kommandoprompt til at bekræfte, Microsoft Defender Antivirus kører. Det gør du ved at køre følgende kommando fra en kommandoprompt:

```console
sc query Windefend
```

Kommandoen `sc query` returnerer oplysninger om Microsoft Defender Antivirus tjeneste. Når Microsoft Defender Antivirus kører, viser `STATE` værdien `RUNNING`.

Hvis du vil have vist alle de tjenester, der ikke kører, skal du køre følgende PowerShell-cmdlet:

```console
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Opdater antimalwaresikkerhedsintelligens

For at få opdateret antimalwaresikkerhedsintelligens skal du have Windows Update tjeneste kørende. Hvis du bruger en opdateringsstyringstjeneste, f.eks. Windows Server Update Services (WSUS), skal du sikre dig, at opdateringer til Microsoft Defender Antivirus Sikkerhedsintelligens er godkendt til de computere, du administrerer.

Som standard downloader Windows Update ikke opdateringer automatisk på Windows Server 2019 eller Windows Server 2022 eller Windows Server 2016. Du kan ændre denne konfiguration ved hjælp af en af følgende metoder:

<br/><br/>

| Metode | Beskrivelse |
|---|---|
| **Windows Update** i Kontrolpanel | **Installation af opdateringer resulterer** automatisk i, at alle opdateringer installeres automatisk, Windows Defender sikkerhedsintelligensopdateringer. <br/><br/> **Download opdateringer, men lad mig vælge**, om jeg vil installere dem, Windows Defender at downloade og installere Sikkerhedsintelligens-opdateringer automatisk, men andre opdateringer installeres ikke automatisk. |
| **Gruppepolitik** | Du kan konfigurere og administrere Windows Update ved hjælp af de indstillinger, der er tilgængelige i Gruppepolitik, på følgende sti: **Administrative skabeloner\Windows Components\Windows Update\Configure Automatic Updates** |
| **Registreringsdatabasenøglen AUOptions** | Følgende to værdier gør det muligt Windows Update hente og installere Sikkerhedsintelligens-opdateringer automatisk: <br/><br/> **4** -  **Installér opdateringer automatisk**. Denne værdi medfører, at alle opdateringer installeres automatisk, Windows Defender sikkerhedsintelligensopdateringer. <br/><br/> **3** -  **Hent opdateringer, men lad mig vælge, om jeg vil installere dem**. Denne værdi gør Windows Defender at downloade og installere Sikkerhedsintelligens-opdateringer automatisk, men andre opdateringer installeres ikke automatisk. |

For at sikre at beskyttelsen mod malware bevares, anbefaler vi, at du aktiverer følgende tjenester:

- Windows Fejlrapportering tjeneste
- Windows Update tjeneste

I følgende tabel vises tjenesterne for Microsoft Defender Antivirus og de afhængige tjenester.

<br/><br/>


| Tjenestenavn | Filplacering | Beskrivelse |
|---|---|---|
| Windows Defender tjeneste (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Dette er den primære Microsoft Defender Antivirus, der skal køre hele tiden.|
| Windows Fejlrapportering tjeneste (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Denne tjeneste sender fejlrapporter tilbage til Microsoft. |
| Windows Defender Firewall (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Vi anbefaler, at Windows Defender Firewall-tjenesten er aktiveret. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update er nødvendig for at få sikkerhedsintelligensopdateringer og opdateringer til antimalwareprogrammet |

## <a name="submit-samples"></a>Sende eksempler

Eksempel på indsendelse giver Microsoft mulighed for at indsamle eksempler på potentielt skadelig software. For at give fortsat og opdateret beskyttelse bruger Microsofts stikprøver disse stikprøver til at analysere mistænkelige aktiviteter og producere opdateret antimalwaresikkerhedsintelligens. Vi indsamler eksekverbare programfiler, f.eks. .exe filer .dll filer. Vi indsamler ikke filer, der indeholder personlige data, f.eks. Microsoft Word dokumenter og PDF-filer.

### <a name="submit-a-file"></a>Send en fil

1. Gennemse [indsendelsesvejledningen](/windows/security/threat-protection/intelligence/submission-guide).
2. Gå til [eksempelindsendelsesportalen](https://www.microsoft.com/wdsi/filesubmission), og indsend din fil.

### <a name="enable-automatic-sample-submission"></a>Aktivér automatisk indsendelse af eksempler

Hvis du vil aktivere automatisk indsendelse af eksempler, skal du starte en Windows PowerShell-konsol som administrator og angive **værdien SubmitSamplesConsent** i overensstemmelse med en af følgende indstillinger:

<br/><br/>

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

Hvis du bruger et antivirusprodukt, der ikke er Microsoft, som din primære antivirusløsning på Windows Server, skal du indstille Microsoft Defender Antivirus til passiv tilstand eller deaktiveret tilstand.

Du kan finde flere oplysninger [under Microsoft Defender Antivirus på Windows Server](microsoft-defender-antivirus-on-windows-server.md#install-microsoft-defender-antivirus-on-windows-server).


### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>Indstil Microsoft Defender Antivirus til passiv tilstand ved hjælp af en registreringsdatabasenøgle

Du kan indstille Microsoft Defender Antivirus til passiv tilstand ved at angive følgende registreringsdatabasenøgle:
- Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- Navn: `ForceDefenderPassiveMode`
- Skriv: `REG_DWORD`
- Værdi: `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>Deaktivere Microsoft Defender Antivirus ved hjælp af guiden Fjern roller og funktioner

1. Se [Installere eller fjerne roller, rolletjenester eller funktioner](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) og bruge **guiden Fjern roller og funktioner**.

2. Når du kommer til **trinnet** Funktioner i guiden, skal du **Windows Defender indstillingen** Funktioner.

    Hvis du fjerner **markeringen Windows Defender** sig selv under **sektionen Windows Defender Funktioner**, bliver du bedt om at fjerne grænsefladeindstillingen **GUI for Windows Defender**.

    Microsoft Defender Antivirus kører stadig normalt uden brugergrænsefladen, men brugergrænsefladen kan ikke aktiveres, hvis du deaktiverer **kernefunktionen Windows Defender** brugergrænsefladen.

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>Deaktivere brugergrænsefladen Microsoft Defender Antivirus brugergrænsefladen ved hjælp af PowerShell

Hvis du vil deaktivere Microsoft Defender Antivirus GUI, skal du bruge følgende PowerShell-cmdlet:

```powershell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Bruger du Windows Server 2012 R2 eller Windows Server 2016?

Du kan nu køre Microsoft Defender Antivirus i passiv tilstand Windows Server 2012 R2 og Windows Server 2016. Du kan finde flere oplysninger [under Indstillinger for installation Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

<br/><br/>

| Procedure | Beskrivelse |
|---|---|
| Deaktivere Microsoft Defender Antivirus ved hjælp af Gruppepolitik | I din Lokale Gruppepolitik-editor skal du gå til **Administrativ** >  **skabelon Windows Component** >  **Endpoint Protection** >  **Disable Endpoint Protection** og derefter **vælge EnabledOK** > . |
| Deaktiver Microsoft Defender Antivirus ved hjælp af en registreringsdatabasenøgle | Hvis du vil bruge [registreringsdatabasenøglen DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware) , skal du gå til `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`og angive eller oprette en DWORD-post kaldet `DisableAntiSpyware`. Angiv dens værdi til `1` (som indstiller værdien for registreringsdatabasenøglen til *sand*). |
| Deaktiver Microsoft Defender Antivirus hjælp af PowerShell | Brug følgende PowerShell-cmdlet: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Fjern Microsoft Defender Antivirus ved hjælp af PowerShell | Brug følgende PowerShell-cmdlet: `Uninstall-WindowsFeature -Name Windows-Defender` |


## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows](microsoft-defender-antivirus-windows.md)
- [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md)
