---
title: Microsoft Defender Antivirus på Windows server
description: Få mere at vide om, hvordan du aktiverer og konfigurerer Microsoft Defender Antivirus på Windows Server 2016, Windows Server 2019 og Windows Server 2022.
keywords: windows defender, server, scep, system center endpoint protection, server 2016, aktuel forgrening, server 2012
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
ms.openlocfilehash: b93595375982e3ed61d1ac94ae410575b0d72307
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666982"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>Microsoft Defender Antivirus på Windows server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender Antivirus er tilgængelig i følgende versioner af Windows Server:

- Windows Server 2022
- Windows Server 2019
- Windows Server, version 1803 eller nyere
- Windows Server 2016
- Windows Server 2012 R2 (kræver Microsoft Defender for Endpoint)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>Konfiguration af Microsoft Defender Antivirus på Windows Server

Processen med at konfigurere og køre Microsoft Defender Antivirus på Windows Server omfatter følgende trin:

1. [Aktivér grænsefladen](#enable-the-user-interface-on-windows-server).
2. [Installer Microsoft Defender Antivirus](#install-microsoft-defender-antivirus-on-windows-server).
3. [Kontrollér Microsoft Defender Antivirus kører](#verify-microsoft-defender-antivirus-is-running).
4. [Opdater din antimalware-sikkerhedsintelligens](#update-antimalware-security-intelligence).
5. (Efter behov) [Send eksempler](#submit-samples).
6. (Efter behov) [Konfigurer automatiske udeladelser](#configure-automatic-exclusions).
7. (Kun hvis det er nødvendigt) Angiv [Windows Server til passiv tilstand](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>Aktivér brugergrænsefladen på Windows Server

> [!IMPORTANT]
> Hvis du bruger Windows Server 2012 R2, skal du se [Indstillinger for installation af Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

Microsoft Defender Antivirus er som standard installeret og funktionelt på Windows Server. Nogle gange installeres brugergrænsefladen som standard. Den grafiske brugergrænseflade er ikke påkrævet. Du kan bruge PowerShell, Gruppepolitik eller andre metoder til at administrere Microsoft Defender Antivirus. Mange organisationer foretrækker dog at bruge den grafiske brugergrænseflade til Microsoft Defender Antivirus. Hvis du vil installere den grafiske brugergrænseflade, skal du bruge en af fremgangsmåderne i følgende tabel:

| Procedure | Sådan gør du |
|:---|:---|
| Aktivér den grafiske brugergrænseflade ved hjælp af guiden Tilføj roller og funktioner | 1. Se [Installér roller, rolletjenester og funktioner ved hjælp af guiden Tilføj roller og funktioner](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), og brug **guiden Tilføj roller og funktioner**. <br/><br/>2. Når du kommer til trinnet **Funktioner** i guiden, skal du under **Windows Defender Funktioner** vælge indstillingen **GUI for Windows Defender**. |
| Slå GUI til ved hjælp af PowerShell | 1. Åbn Windows PowerShell som administrator på Windows-serveren. <br/><br/>2. Kør følgende PowerShell-cmdlet: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>Installér Microsoft Defender Antivirus på Windows Server

Hvis du har brug for at installere eller geninstallere Microsoft Defender Antivirus på Windows Server, skal du bruge en af procedurerne i følgende tabel:

| Procedure | Sådan gør du |
|:---|:---|
| Brug guiden Tilføj roller og funktioner til at installere Microsoft Defender Antivirus | 1. Se [Installér eller fjern roller, rolletjenester eller funktioner](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard), og brug **guiden Tilføj roller og funktioner**. <br/><br/>2. Når du kommer til trinnet **Funktioner** i guiden, skal du vælge indstillingen Microsoft Defender Antivirus. Vælg også **gui for Windows Defender** indstilling. |
| Brug PowerShell til at installere Microsoft Defender Antivirus | 1. Åbn Windows PowerShell som administrator på Windows-serveren. <br/><br/>2. Kør følgende PowerShell-cmdlet: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> Hændelsesmeddelelser til antimalwareprogrammet, der er inkluderet i Microsoft Defender Antivirus, kan findes i [Microsoft Defender Antivirus Events](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>Kontrollér Microsoft Defender Antivirus kører

Når du har installeret (eller geninstalleret) Microsoft Defender Antivirus, er dit næste trin at kontrollere, at den kører. Brug PowerShell-cmdlet'erne i følgende tabel:

| Procedure | PowerShell-cmdlet |
|:---|:---|
| Kontrollér, at Microsoft Defender Antivirus kører | `Get-Service -Name windefend` |
| Kontrollér, at firewallbeskyttelse er slået til | `Get-Service -Name mpssvc` |

Som et alternativ til PowerShell kan du bruge Kommandoprompt til at bekræfte, at Microsoft Defender Antivirus kører. Det gør du ved at køre følgende kommando fra en kommandoprompt:

```cmd
sc query Windefend
```

Kommandoen `sc query` returnerer oplysninger om Microsoft Defender Antivirus-tjenesten. Når Microsoft Defender Antivirus kører, vises `RUNNING`værdien `STATE` .

Hvis du vil have vist alle de tjenester, der ikke kører, skal du køre følgende PowerShell-cmdlet:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>Opdater antimalware-sikkerhedsintelligens

Hvis du vil hente dine regelmæssige opdateringer til sikkerhedsintelligens, skal Windows Update-tjenesten køre. Hvis du bruger en tjeneste til administration af opdateringer, f.eks. Windows Server Update Services (WSUS), skal du sørge for, at opdateringer til Microsoft Defender Antivirus Security Intelligence godkendes for de computere, du administrerer.

Som standard downloader og installerer Windows Update ikke opdateringer automatisk på Windows Server 2019 eller Windows Server 2022 eller Windows Server 2016. Du kan ændre denne konfiguration ved hjælp af en af følgende metoder:

| Metode | Beskrivelse |
|---|---|
| **Windows Update** i Kontrolpanel | **Installation af opdateringer medfører automatisk**, at alle opdateringer installeres automatisk, herunder Windows Defender Sikkerhedsintelligensopdateringer. <br/><br/> **Download opdateringer, men lad mig vælge, om jeg vil installere dem**, gør det muligt for Windows Defender at downloade og installere Sikkerhedsintelligensopdateringer automatisk, men andre opdateringer installeres ikke automatisk. |
| **Gruppepolitik** | Du kan konfigurere og administrere Windows Update ved hjælp af de indstillinger, der er tilgængelige i Gruppepolitik, i følgende sti: **Administrative skabeloner\Windows Komponenter\Windows Update\Konfigurer automatiske opdateringer** |
| **Registreringsdatabasenøglen AUOptions** | Følgende to værdier gør det muligt for Windows Update automatisk at downloade og installere Sikkerhedsintelligensopdateringer: <br/><br/> **4** -  **Installér opdateringer automatisk**. Denne værdi medfører, at alle opdateringer installeres automatisk, herunder Windows Defender sikkerhedsintelligensopdateringer. <br/><br/> **3** -  **Download opdateringer, men lad mig vælge, om jeg vil installere dem**. Denne værdi gør det muligt for Windows Defender at downloade og installere Sikkerhedsintelligensopdateringer automatisk, men andre opdateringer installeres ikke automatisk. |

Hvis du vil sikre, at beskyttelse mod malware opretholdes, skal du aktivere følgende tjenester:

- Windows Fejlrapportering tjeneste
- Windows Update tjeneste

I følgende tabel vises tjenesterne for Microsoft Defender Antivirus og de afhængige tjenester.

| Tjenestenavn | Filplacering | Beskrivelse |
|---|---|---|
| Windows Defender-tjeneste (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | Dette er den primære Microsoft Defender Antivirus tjeneste, der skal køre altid.|
| Windows Fejlrapportering-tjeneste (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | Denne tjeneste sender fejlrapporter tilbage til Microsoft. |
| Windows Defender Firewall (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | Vi anbefaler, at Windows Defender Firewall-tjenesten er aktiveret. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update er nødvendig for at få opdateringer til sikkerhedsintelligens og antimalwareprogrammer |

## <a name="submit-samples"></a>Send eksempler

Indsendelse af eksempler gør det muligt for Microsoft at indsamle eksempler på potentielt skadelig software. For at hjælpe med at levere fortsat og opdateret beskyttelse bruger Microsoft-forskere disse eksempler til at analysere mistænkelige aktiviteter og producere opdateret antimalware-sikkerhedsintelligens. Vi indsamler eksekverbare programfiler, f.eks. .exe filer og .dll filer. Vi indsamler ikke filer, der indeholder personlige data, f.eks. Microsoft Word dokumenter og PDF-filer.

### <a name="submit-a-file"></a>Send en fil

1. Gennemse [indsendelsesvejledningen](/windows/security/threat-protection/intelligence/submission-guide).

2. Besøg [portalen til eksempelindsendelse](https://www.microsoft.com/wdsi/filesubmission), og send din fil.

### <a name="enable-automatic-sample-submission"></a>Aktivér automatisk afsendelse af eksempel

Hvis du vil aktivere automatisk afsendelse af eksempel, skal du starte en Windows PowerShell konsol som administrator og angive værdidataene **for SubmitSamplesConsent** i henhold til en af følgende indstillinger:

|Indstilling|Beskrivelse|
|---|---|
| **0** -  **Spørg altid** | Tjenesten Microsoft Defender Antivirus beder dig om at bekræfte afsendelsen af alle nødvendige filer. Dette er standardindstillingen for Microsoft Defender Antivirus, men anbefales ikke til installationer på Windows Server 2016 eller 2019 eller Windows Server 2022 uden en GUI. |
| **1**  -  **Send automatisk sikre eksempler** | Tjenesten Microsoft Defender Antivirus sender alle filer, der er markeret som "sikre", og beder om resten af filerne. |
| **2** -  **Send aldrig** | Tjenesten Microsoft Defender Antivirus spørger ikke og sender ingen filer. |
| **3** -  **Send alle eksempler automatisk** | Tjenesten Microsoft Defender Antivirus sender alle filer uden at blive bedt om at bekræfte. |

> [!NOTE]
> Denne indstilling er ikke tilgængelig for Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>Konfigurer automatiske udeladelser

For at hjælpe med at sikre sikkerhed og ydeevne tilføjes visse undtagelser automatisk baseret på de roller og funktioner, du installerer, når du bruger Microsoft Defender Antivirus på Windows Server 2016 eller 2019 eller Windows Server 2022.

Se [Konfigurer udeladelser i Microsoft Defender Antivirus på Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>Passiv tilstand og Windows server

Hvis du bruger et antivirusprodukt, der ikke er fra Microsoft, som din primære antivirusløsning på Windows Server, skal du angive Microsoft Defender Antivirus til passiv tilstand eller deaktiveret tilstand. Hvis dit Windows Server-slutpunkt er onboardet til Microsoft Defender for Endpoint, kan du angive Microsoft Defender Antivirus til passiv tilstand. Hvis du ikke bruger Microsoft Defender for Endpoint, skal du angive Microsoft Defender Antivirus til deaktiveret tilstand. 

> [!TIP]
> Se [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md).

I følgende tabel beskrives, hvordan du angiver Microsoft Defender Antivirus til passiv tilstand, deaktiverer Microsoft Defender Antivirus og fjerner Microsoft Defender Antivirus:

| Procedure | Beskrivelse |
|---|---|
| Angiv Microsoft Defender Antivirus til passiv tilstand ved hjælp af en registreringsdatabasenøgle | Angiv registreringsdatabasenøglen ForceDefenderPassiveMode på følgende måde: <br/>- Sti: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- Navn: `ForceDefenderPassiveMode` <br/>- Type: `REG_DWORD` <br/>- Værdi: `1` |
| Slå den Microsoft Defender Antivirus brugergrænseflade fra ved hjælp af PowerShell | Åbn Windows PowerShell som administrator, og kør følgende PowerShell-cmdlet:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| Deaktiver Microsoft Defender Antivirus ved hjælp af PowerShell | Brug følgende PowerShell-cmdlet: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| Deaktiver Microsoft Defender Antivirus ved hjælp af guiden Fjern roller og funktioner | Se [Installér eller fjern roller, rolletjenester eller funktioner](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard), og brug **guiden Fjern roller og funktioner**. <br/><br/>Når du kommer til trinnet **Funktioner** i guiden, skal du fjerne markeringen af indstillingen **Windows Defender Funktioner**. <br/><br/> Hvis du rydder **Windows Defender** af sig selv i afsnittet **Windows Defender funktioner**, bliver du bedt om at fjerne **grænsefladeindstillingen GUI for Windows Defender**.<br/><br/>Microsoft Defender Antivirus kører stadig normalt uden brugergrænsefladen, men brugergrænsefladen kan ikke aktiveres, hvis du deaktiverer **Windows Defender** kernefunktion. |
| Fjern Microsoft Defender Antivirus ved hjælp af PowerShell | Brug følgende PowerShell-cmdlet: `Uninstall-WindowsFeature -Name Windows-Defender` |
| Deaktiver Microsoft Defender Antivirus ved hjælp af Gruppepolitik | I editoren til lokale Gruppepolitik skal du gå til **Administrativ skabelon** >  **Windows Component** >  **Endpoint Protection** >  **Disable Endpoint Protection** og derefter vælge **EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>Bruger du Windows Server 2012 R2 eller Windows Server 2016?

Hvis din Windows Server er onboardet til Microsoft Defender for Endpoint, kan du nu køre Microsoft Defender Antivirus i passiv tilstand på Windows Server 2012 R2 og Windows Server 2016. Se følgende artikler:

- [Indstillinger for installation af Microsoft Defender for Endpoint](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [Microsoft Defender Antivirus kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus i Windows](microsoft-defender-antivirus-windows.md)

