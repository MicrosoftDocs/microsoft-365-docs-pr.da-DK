---
title: Overførsel fra en tredjeparts HIPS-regel til ASR-regler
description: Beskriver, hvordan du tilgange en overførsel fra en løsning fra et tredjepartssystem til forebyggelse af indtrængen (HIPS) i ASR-regler.
keywords: Regler for reduktion af angrebsoverfladen, asr-regler, hips, beskyttelsesregler for indtrængen, anti exploit, antiexploit, udnyttelse, forebyggelse af virus, Microsoft Defender til slutpunkt
ms.topic: article
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 2530f38bdcfdbb74bdd9a80c59c53c9e273e1449
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/17/2021
ms.locfileid: "63599348"
---
# <a name="migrating-from-a-third-party-hips-to-asr-rules"></a>Overførsel fra en tredjeparts HIPS-regel til ASR-regler

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Denne artikel hjælper dig med at knytte almindelige regler til Microsoft Defender for Endpoint.

## <a name="scenarios-when-migrating-from-a-third-party-hips-product-to-asr-rules"></a>Scenarier, når der overføres fra et tredjeparts-HIPS-produkt til ASR-regler

### <a name="block-creation-of-specific-files"></a>Bloker oprettelse af bestemte filer

- **Gælder for**- Alle processer
- **Handling**- Oprettelse af fil
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester- *.zeflot, *.odin, *.locky, *.jaff, *.lukitus, *.wnry, *.krab
- **Regler for reduktion af angrebsoverfladen** – ASR-regler blokerer angrebsteknikker og ikke Symboler for kompromis (IOC). Blokering af et bestemt filtypenavn er ikke altid nyttigt, da det ikke forhindrer en enhed i at gå på kompromis. Det er kun delvist modværks af et angreb, indtil hackere opretter en ny type udvidelse til nyttelasten.
- **Andre anbefalede funktioner**– At have Microsoft Defender AV aktiveret, sammen med Cloud Protection og Behavior Analysis anbefales kraftigt. Vi anbefaler, at du bruger anden forebyggelse, f.eks. ASR-reglen "Brug avanceret beskyttelse mod ransomware". Dette giver et højere niveau af beskyttelse mod ransomware-angreb. Desuden overvåges mange af disse registreringsdatabasenøgler af Microsoft Defender til slutpunkt, f.eks. ASEP-teknikker, som udløser bestemte beskeder. De registreringsdatabasenøgler, der bruges, kræver et minimum af lokale administratorrettigheder eller installationsrettigheder, der er tillid til, som kan ændres. Det anbefales at bruge et låst miljø med administrative konti eller rettigheder som minimum. Andre systemkonfigurationer kan aktiveres, herunder "Deaktiver fejlfinding for ikke-påkrævede roller", som er en del af vores bredere sikkerhedsanbefalinger.

### <a name="block-creation-of-specific-registry-keys"></a>Bloker oprettelse af bestemte registreringsdatabasenøgler

- **Gælder for**- alle processer
- **Processer**- I/T
- **Handling-** Ændringer i registreringsdatabasen
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer, tjenester**-  *\Software,HKCU*\Environment\UserInitMprLogonScript,HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs *\StartExe, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger, HKEY_CURRENT_USER\Software\Microsoft\HtmlHelp Author\location, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcess
- **Regler for reduktion af angrebsoverfladen** – ASR-regler blokerer angrebsteknikker og ikke Symboler for kompromis (IOC). Blokering af et bestemt filtypenavn er ikke altid nyttigt, da det ikke forhindrer en enhed i at gå på kompromis. Det er kun delvist modværks af et angreb, indtil hackere opretter en ny type udvidelse til nyttelasten.
- **Andre anbefalede funktioner**– At have Microsoft Defender AV aktiveret, sammen med Cloud Protection og Behavior Analysis anbefales kraftigt. Vi anbefaler, at du bruger yderligere forebyggelse, f.eks. ASR-reglen "Brug avanceret beskyttelse mod ransomware". Dette giver et højere niveau af beskyttelse mod ransomware-angreb. Desuden overvåges flere af disse registreringsdatabasenøgler af Microsoft Defender til slutpunkt, f.eks. ASEP-teknikker, som udløser bestemte beskeder. Desuden kræver de registreringsdatabasenøgler, der bruges, et minimum af lokale administrator- eller installationsprogramrettigheder, som kan ændres. Det anbefales at bruge et låst miljø med administrative konti eller rettigheder som minimum. Andre systemkonfigurationer kan aktiveres, herunder "Deaktiver fejlfinding for ikke-påkrævede roller", som er en del af vores bredere sikkerhedsanbefalinger.

### <a name="block-untrusted-programs-from-running-from-removable-drives"></a>Bloker upålidelige programmer fra at køre fra flytbare drev

- **Gælder for** ikke-upålidelige programmer fra USB
- **Processer**- *
- **Handling**- Procesudførelse
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer, tjenester:-*
- **Regler** for reduktion af angrebsoverfladen – ASR-regler har en indbygget regel for at forhindre lancering af upålidelige og usignerede programmer fra flytbare drev: "Bloker upålidelige og usignerede processer, der kører fra USB", GUID "b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4".
- **Andre anbefalede funktioner**– Udforsk yderligere kontrolelementer til USB-enheder og andre flytbare medier ved hjælp af Microsoft Defender til Slutpunkt:Sådan styrer du USB-enheder og andre flytbare medier ved hjælp [af Microsoft Defender til slutpunkt](/windows/security/threat-protection/device-control/control-usb-devices-using-intune).

### <a name="block-mshta-from-launching-certain-child-processes"></a>Bloker Mshta fra at starte visse underordnede processer

- **Gælder for**- Mshta
- **Processer**- mshta.exe
- **Handling**- Procesudførelse
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester powershell.exe, cmd.exe, regsvr32.exe
- **Regler for reduktion af angrebsoverfladen** – ASR-regler indeholder ikke specifikke regler til at forhindre underordnede processer fra "mshta.exe". Dette kontrolelement er inden for indbetalingen af Exploit Protection eller Windows Defender-programkontrol.
- **Andre anbefalede funktioner**: Aktivér Windows Defender Programkontrolelement for at forhindremshta.exe at køre helt. Hvis din organisation kræver "mshta.exe" for line of business-apps, skal du konfigurere en bestemt Windows Defender Exploit Protection-regel for at forhindre mshta.exe at starte underordnede processer.

### <a name="block-outlook-from-launching-child-processes"></a>Bloker Outlook at starte underordnede processer

- **Gælder for**- Outlook
- **Processer**- outlook.exe
- **Handling**- Procesudførelse
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer, tjenester** powershell.exe
- Regler for reduktion af angrebsoverfladen **–** ASR-regler har en indbygget regel til at forhindre Office-kommunikationsapps (Outlook, Skype og Teams) i at starte underordnede processer: "Bloker Office-kommunikationsprogram i at oprette børneprocesser", GUID "26190899-1602-49e8-8b27-eb1d0a1ce869".
- **Andre anbefalede funktioner** – Vi anbefaler, at du aktiverer begrænset sprogtilstand i PowerShell for at minimere angrebsoverfladen fra PowerShell.

### <a name="block-office-apps-from-launching-child-processes"></a>Bloker Office apps fra at starte underordnede processer

- **Gælder for**- Office
- **Processer** – winword.exe, powerpnt.exe, excel.exe
- **Handling**- Procesudførelse
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester powershell.exe, cmd.exe, wscript.exe, mshta.exe, EQNEDT32.EXE, regsrv32.exe
- **Regler** for reduktion af angrebsoverfladen – ASR-regler har en indbygget regel til at forhindre Office-apps i at starte underordnede processer: "Bloker alle Office-programmer i at oprette underordnede processer", GUID "d4f940ab-401b-4efc-aadc-ad5f3c50688a".
- **Andre anbefalede funktioner** - I/T

### <a name="block-office-apps-from-creating-executable-content"></a>Bloker Office apps i at oprette eksekverbart indhold

- **Gælder for**- Office
- **Processer** – winword.exe, powerpnt.exe, excel.exe
- **Handling**- Oprettelse af fil
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, Processer,** tjenester- C:\Brugere *\AppData **.exe, C:\ProgramData**.exe, C:\ProgramData**.com, C:\UsersAppData*\Local\**Temp.com, C:\Users*\Downloads**.exe, C:\Users *\AppData.scf **, C:\ProgramData.scf**, C:\Users\Public*.exe, C:\Users*\Desktop***.exe
- **Regler for reduktion af angrebsoverfladen** - I/T.

### <a name="block-wscript-from-reading-certain-types-of-files"></a>Bloker WScript fra at læse bestemte filtyper

- **Gælder for**- Wscript
- **Processer**- wscript.exe
- **Handling**- Læsning af fil
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester- C:\Brugere *\AppData**.js, C:\Brugere*\Downloads**.js
- **Regler for reduktion af** angrebsoverfladen– På grund af pålideligheds- og ydeevneproblemer har ASR-regler ikke mulighed for at forhindre en bestemt proces i at læse en bestemt scriptfiltype. Vi har en regel til at forhindre angrebsvektorer, der kan komme fra disse scenarier. Regelnavnet er "Bloker JavaScript eller VBScript fra at starte downloadet eksekverbart indhold" (GUID "d3e037e1-3eb8-44c8-a917-57927947596d") og "Bloker udførelse af potentielt slørede scripts" (GUID " 5beb7efe-fd9a-4556-801d-275e5ffc04cc").
- Andre **anbefalede** funktioner– Selvom der er specifikke regler for asr,der afhjælper visse angrebsvektorer i disse scenarier, er det vigtigt at nævne, at AV som standard er i stand til at undersøge scripts (PowerShell, Windows Script Host, JavaScript, VBScript og mere) i realtid via ANTImalware Scan Interface (AMSI). Du kan finde flere oplysninger her: [Antimalware Scan Interface (AMSI)](/windows/win32/amsi/antimalware-scan-interface-portal).

### <a name="block-launch-of-child-processes"></a>Bloker start af underordnede processer

- **Gælder for**- Adobe Acrobat
- **Processer**- AcroRd32.exe, Acrobat.exe
- **Handling**- Procesudførelse
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester cmd.exe, powershell.exe, wscript.exe
- **Regler for reduktion af angrebsoverfladen** – ASR-regler tillader blokering af Adobe Reader i at starte børneprocesser. Regelnavnet er "Bloker Adobe Reader i at oprette underordnede processer", GUID "7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c".
- **Andre anbefalede funktioner** - I/T

### <a name="block-download-or-creation-of-executable-content"></a>Bloker download eller oprettelse af eksekverbart indhold

- **Gælder for**- CertUtil: Bloker download eller oprettelse af eksekverbar fil
- **Processer**- certutil.exe
- **Handling**- Oprettelse af fil
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer, tjenester**- *.exe
- **Regler for reduktion af angrebsoverfladen** – ASR-regler understøtter ikke disse scenarier, fordi de er en del Microsoft Defender Antivirus beskyttelse.
- **Andre anbefalede funktioner** – Microsoft Defender AV forhindrer CertUtil i at oprette eller downloade eksekverbart indhold.

### <a name="block-processes-from-stopping-critical-system-components"></a>Bloker processer fra at stoppe kritiske systemkomponenter

- **Gælder for**- alle processer
- **Processer**- *
- **Handling**- Afslutning af proces
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester- MsSense.exe, MsMpEng.exe, NisSrv.exe, svchost.exe*, services.exe, csrss.exe, smss.exe, wininit.exe og meget mere.
- **Regler for reduktion af** angrebsoverfladen – ASR-regler understøtter ikke disse scenarier, fordi de er beskyttet Windows indbyggede sikkerhedsbeskyttelse.
- **Andre anbefalede funktioner**: ELAM (Early Launch AntiMalware), PPL (Protection Process Light), PPL AntiMalware Light og System Guard.

### <a name="block-specific-launch-process-attempt"></a>Bloker et bestemt forsøg på startproces

- **Gælder for**- specifikke processer
- **Processer**- "Navngive din proces"
- **Handling**- Procesudførelse
- **Eksempler på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester tor.exe, bittorrent.exe, cmd.exe, powershell.exe og meget mere
- **Regler for reduktion af angrebsoverfladen** – Generelt er ASR-regler ikke designet til at fungere som programadministrator.
- **Andre anbefalede funktioner**: Hvis du vil forhindre brugere i at starte bestemte processer eller programmer, anbefales det at Windows Defender programkontrolelement. Microsoft Defender for endpoint-fil- og cert-indikatorer kan bruges i et hændelsesresponsscenarie (bør ikke ses som en programkontrolmekanismen).

### <a name="block-unauthorized-changes-to-microsoft-defender-antivirus-configurations"></a>Bloker uautoriserede ændringer i Microsoft Defender Antivirus konfigurationer

- **Gælder for**- alle processer
- **Processer**- *
- **Handling-** Ændringer i registreringsdatabasen
- Eksempler **på filer/mapper, registreringsdatabasenøgler/værdier, processer,** tjenester- HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware, HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowRealTimeMonitoring osv.
- **Regler for reduktion af** angrebsoverfladen – ASR-regler dækker ikke disse scenarier, fordi de er en del af den indbyggede Microsoft Defender til slutpunktsbeskyttelse.
- Andre **anbefalede** funktioner- Tamper Protection (tilmelding, administreres fra Intune) forhindrer uautoriserede ændringer af DisableAntiVirus, DisableAntiSpyware, DisableRealtimeMonitoring, DisableOnAccessProtection, DisableBehaviorMonitoring og DisableIOAVProtection-registreringsdatabasenøgler (og meget mere).

Se også

- [Ofte stillede spørgsmål om reduktion af angrebsoverfladen](attack-surface-reduction-faq.yml)
- [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md)
- [Evaluer regler for reduktion af angrebsoverfladen](evaluate-attack-surface-reduction.md)
