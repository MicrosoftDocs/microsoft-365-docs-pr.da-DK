---
title: Fejlfinding af Microsoft Defender Antivirus under overførsel fra en tredjepartsløsning
description: Foretag fejlfinding af almindelige fejl ved overførsel til Microsoft Defender Antivirus
keywords: hændelse, fejlkode, logføring, fejlfinding, Microsoft Defender antivirus, Windows Defender antivirus, overførsel
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 5e0db56306b1e56ee0ab21d2c3728f30a8c47ec8
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468234"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Fejlfinding af Microsoft Defender Antivirus under overførsel fra en tredjepartsløsning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Antivirus](https://www.microsoft.com/windows/comprehensive-security)

**Platforme**
- Windows

Du kan finde hjælp her, hvis du oplever problemer under overførsel fra en sikkerhedsløsning fra en tredjepart for at Microsoft Defender Antivirus.

## <a name="review-event-logs"></a>Gennemse hændelseslogge

1. Åbn appen Logbog ved at vælge ikonet **Søg** på proceslinjen og søge efter *Logbog*.

    Du kan finde oplysninger om Microsoft Defender Antivirus under **Logfiler for** \> programmer og tjenester **Microsoft** \> **Windows** \> **Windows Defender**.

1. Herfra skal du vælge **Åbn** under **Drift**.

    Hvis du vælger en hændelse i detaljeruden, får du vist flere oplysninger om en hændelse i den nederste rude under fanerne **Generelt** og **Detaljer** .

## <a name="microsoft-defender-antivirus-wont-start"></a>Microsoft Defender Antivirus starter ikke

Dette problem kan manifesteres i form af flere forskellige hændelses-id'er, som alle har den samme underliggende årsag.

### <a name="associated-event-ids"></a>Tilknyttede hændelses-id'er

Hændelses-id|Lognavn|Beskrivelse|Kilde
---|---|---|---
15|Program|Status for Windows Defender blev opdateret til SECURITY_PRODUCT_STATE_OFF.|Security Center
5007|Microsoft-Windows-Windows Defender/Operationelt|Windows Defender Antivirus Konfiguration er ændret. Hvis dette er en uventet hændelse, skal du gennemse indstillingerne, da dette kan være resultatet af malware. <p> **Gammel værdi:** Default\IsServiceRunning = 0x0 <p> **Ny værdi:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operationelt|Windows Defender Antivirus scanning efter spyware og anden potentielt uønsket software er deaktiveret.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Sådan kan du se, om Microsoft Defender Antivirus ikke starter, fordi der er installeret et antivirusprogram fra en tredjepart

Hvis du ikke bruger Microsoft Defender for Endpoint på en Windows 10 eller Windows 11 enhed, og du har installeret et antivirusprogram fra tredjepart, vil Microsoft Defender Antivirus automatisk blive slået fra. Hvis du bruger Microsoft Defender for Endpoint, hvor der er installeret et antivirusprogram fra tredjepart, starter Microsoft Defender Antivirus i passiv tilstand med reduceret funktionalitet.

> [!TIP]
> Det netop beskrevne scenarie gælder kun for Windows 10 og Windows 11. Andre versioner af Windows har [forskellige svar på](microsoft-defender-antivirus-compatibility.md) Microsoft Defender Antivirus, der køres sammen med tredjepartssikkerhedssoftware.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Brug tjenesteappen til at kontrollere, om Microsoft Defender Antivirus er slået fra

Hvis du vil åbne appen Tjenester, skal du vælge ikonet **Søg** på proceslinjen og søge efter *tjenester*. Du kan også åbne appen fra kommandolinjen ved at skrive *services.msc*.

Oplysninger om Microsoft Defender Antivirus vises i appen Tjenester under **Windows Defender** \> **Drift**. Navnet på antivirustjenesten er *Windows Defender Antivirus Service*.

Når du kontrollerer appen, kan du se, at *Windows Defender Antivirus Service* er angivet til manuel, men når du forsøger at starte denne tjeneste manuelt, får du vist en advarsel om, at *tjenesten Windows Defender Antivirus service på den lokale computer startede og derefter stoppede. Nogle tjenester stopper automatisk, hvis de ikke bruges af andre tjenester eller programmer.*

Dette angiver, at Microsoft Defender Antivirus er blevet automatisk deaktiveret for at bevare kompatibilitet med et antivirusprogram fra tredjepart.

#### <a name="generate-a-detailed-report"></a>Generér en detaljeret rapport

Du kan generere en detaljeret rapport om aktive gruppepolitikker ved at åbne en kommandoprompt i **kør som administratortilstand** og derefter angive følgende kommando:

```console
GPresult.exe /h gpresult.html
```

Dette genererer en rapport, der er placeret på *./gpresult.html*. Åbn denne fil, og du kan få vist følgende resultater, afhængigt af hvordan Microsoft Defender Antivirus blev slået fra.

##### <a name="group-policy-results"></a>Gruppepolitikresultater

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Hvis sikkerhedsindstillinger implementeres via gruppepolitik (GPO) på domæne- eller lokalt niveau, eller via System Center Configuration Manager (SCCM)

I GPResults-rapporten under overskriften *Windows Komponenter/Windows Defender Antivirus* kan du se noget i stil med følgende post, der angiver, at Microsoft Defender Antivirus er slået fra.

Politik|Indstilling|Vindende gruppepolitikobjekt
---|---|---
Deaktiver Windows Defender Antivirus|Aktiveret|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Hvis sikkerhedsindstillinger implementeres via Gruppepolitikindstillinger

Under overskriften *Registry item (Key path: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Value name: DisableAntiSpyware)* kan du se noget i stil med følgende post, der angiver, at Microsoft Defender Antivirus er slået fra.

DisableAntiSpyware|-
---|---
Vindende gruppepolitikobjekt|Win10-Workstations
Resultat: Udført|
**Generel**|
Handling|Opdater
**Egenskaber**|
Hive|HKEY_LOCAL_MACHINE
Nøglesti|SOFTWARE\Policies\Microsoft\Windows Defender
Værdinavn|DisableAntiSpyware
Værditype|REG_DWORD
Værdidata|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Hvis sikkerhedsindstillingerne implementeres via registreringsdatabasenøglen

Rapporten kan indeholde følgende tekst, der angiver, at Microsoft Defender Antivirus er slået fra:

> Registreringsdatabase (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Hvis sikkerhedsindstillingerne er angivet i Windows eller Windows Server-afbildningen

Din indbildske administrator kan have angivet sikkerhedspolitikken **[DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** lokalt via *GPEdit.exe*, *LGPO.exe* eller ved at ændre registreringsdatabasen i opgavesekvensen. Du kan [konfigurere et billed-id, der er tillid](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) til, for Microsoft Defender Antivirus.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Slå Microsoft Defender Antivirus til igen

Microsoft Defender Antivirus aktiveres automatisk, hvis ingen andre antivirusprogrammer er aktive i øjeblikket. Du skal slå tredjeparts antivirus helt fra for at sikre, at Microsoft Defender Antivirus kan køre med fuld funktionalitet.

> [!WARNING]
> Løsninger, der foreslår, at du redigerer *startværdierne for Windows Defender* for *wdboot*, *wdfilter*, *wdnisdrv*, *wdnissvc* og *windefend* i HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services ikke understøttes, og kan tvinge dig til at genbillede dit system.

Passiv tilstand er tilgængelig, hvis du begynder at bruge Microsoft Defender for Endpoint og et antivirusprogram fra tredjepart sammen med Microsoft Defender Antivirus. Passiv tilstand gør det muligt for Microsoft Defender Antivirus at scanne filer og opdatere sig selv, men det afhjælper ikke trusler. Desuden er overvågning af funktionsmåde via [Realtidsbeskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md) ikke tilgængelig i passiv tilstand, medmindre [DLP (Endpoint Forebyggelse af datatab)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) er installeret.

En anden funktion, der kaldes [begrænset periodisk scanning](limited-periodic-scanning-microsoft-defender-antivirus.md), er tilgængelig for slutbrugere, når Microsoft Defender Antivirus er indstillet til automatisk at slå fra. Denne funktion gør det muligt for Microsoft Defender Antivirus jævnligt at scanne filer sammen med et antivirusprogram fra tredjepart ved hjælp af et begrænset antal registreringer.

> [!IMPORTANT]
> Begrænset periodisk scanning anbefales ikke i virksomhedsmiljøer. De registrerings-, administrations- og rapporteringsfunktioner, der er tilgængelige, når du kører Microsoft Defender Antivirus i denne tilstand, reduceres sammenlignet med aktiv tilstand.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)


### <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md)
- [Microsoft Defender Antivirus i appen Windows Sikkerhed](microsoft-defender-security-center-antivirus.md)
