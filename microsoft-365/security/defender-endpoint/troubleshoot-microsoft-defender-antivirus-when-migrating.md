---
title: Fejlfinding Microsoft Defender Antivirus under overførsel fra en tredjepartsløsning
description: Foretag fejlfinding af almindelige fejl under overførsel til Microsoft Defender Antivirus
keywords: hændelse, fejlkode, logføring, fejlfinding, microsoft defender antivirus, windows defender antivirus, overførsel
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.date: 10/19/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: c1b60b66977c4f93591bce20a5cf6ace0b7fc567
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63595886"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>Fejlfinding Microsoft Defender Antivirus under overførsel fra en tredjepartsløsning

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Du kan finde hjælp her, hvis du støder på problemer under overførsel fra en tredjeparts sikkerhedsløsning for at Microsoft Defender Antivirus.

## <a name="review-event-logs"></a>Gennemse hændelseslogfiler

1. Åbn appen Logvisning ved at vælge ikonet **Søg på** proceslinjen og søge efter *Log på*.

    Oplysninger om Microsoft Defender Antivirus kan findes under Program **- og tjenestelogfiler,** \> **som Microsoft** \> **Windows** \> **Windows Defender**.

1. Derfra skal du **vælge Åbn** under **Drift**.

    Hvis du vælger en begivenhed i detaljeruden, vises der flere oplysninger om en begivenhed i den nederste rude under **fanerne Generelt** **og** Detaljer.

## <a name="microsoft-defender-antivirus-wont-start"></a>Microsoft Defender Antivirus starter ikke

Dette problem kan manifestt i form af flere forskellige hændelses-jeg-sider, som alle har samme underliggende årsag.

### <a name="associated-event-ids"></a>Tilknyttede hændelses-iD'er

Hændelses-id|Lognavn|Beskrivelse|Kilde
---|---|---|---
15|Program|Opdateret Windows Defender status til at SECURITY_PRODUCT_STATE_OFF.|Security Center
5007|Microsoft-Windows-Windows Defender/drift|Windows Defender Antivirus konfigurationen er ændret. Hvis dette er en uventet hændelse, skal du gennemse indstillingerne, da dette kan være resultatet af malware. <p> **Gammel værdi:** Default\IsServiceRunning = 0x0 <p> **Ny værdi:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/drift|Windows Defender Antivirus scanning for spyware, og anden potentielt uønsket software deaktiveres.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>Hvordan ser jeg, Microsoft Defender Antivirus et antivirusprogram ikke starter, fordi der er installeret et antivirusprogram fra en tredjepart

Hvis du Windows 10 en Windows 11-enhed, og du ikke bruger Microsoft Defender til slutpunkt, og du har et antivirusprogram fra tredjepart installeret, vil Microsoft Defender Antivirus automatisk blive slået fra. Hvis du bruger Microsoft Defender til slutpunkt med et tredjeparts antivirusprogram installeret, starter Microsoft Defender Antivirus i passiv tilstand med begrænset funktionalitet.

> [!TIP]
> Det scenarie, der netop er beskrevet, gælder kun for Windows 10 og Windows 11. Andre versioner af Windows har [forskellige svar](microsoft-defender-antivirus-compatibility.md) på Microsoft Defender Antivirus der køres sammen med tredjepartssikkerhedssoftware.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>Brug services-appen til at kontrollere, Microsoft Defender Antivirus er slået fra

Hvis du vil åbne appen Tjenester, skal du **vælge** ikonet Søg fra proceslinjen og søge efter *tjenester*. Du kan også åbne appen fra kommandolinjen ved at skrive *services.msc*.

Oplysninger om Microsoft Defender Antivirus vises i Services-appen under **Windows Defender** \> **drift**. Navnet på antivirustjenesten *er Windows Defender Antivirus Tjeneste*.

Når du tjekker appen, kan du se, at *Windows Defender Antivirus-tjenesten* er indstillet til manuel, men når du forsøger at starte tjenesten manuelt, får du vist en advarsel, hvor der står Windows Defender Antivirus-tjenesten på lokal computer er startet og derefter stoppet *. Nogle tjenester stopper automatisk, hvis de ikke bruges af andre tjenester eller programmer.*

Dette angiver, Microsoft Defender Antivirus automatisk er slået fra for at bevare kompatibilitet med et tredjeparts antivirusprogram.

#### <a name="generate-a-detailed-report"></a>Generere en detaljeret rapport

Du kan generere en detaljeret rapport om aktive gruppepolitikker ved at åbne en kommandoprompt i Kør som **administratortilstand** og derefter angive følgende kommando:

```console
GPresult.exe /h gpresult.html
```

Dette genererer en rapport placeret på *./gpresult.html*. Åbn denne fil, så får du muligvis vist følgende resultater, afhængigt af Microsoft Defender Antivirus blev slået fra.

##### <a name="group-policy-results"></a>Gruppepolitikresultater

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>Hvis sikkerhedsindstillinger implementeres via gruppepolitik på domænet eller lokalt niveau, eller hvis System Center Configuration Manager (SCCM)

I GPResults-rapporten under overskriften Windows *Components/Windows Defender Antivirus* får du muligvis vist noget i retning af følgende post, der angiver, at Microsoft Defender Antivirus er slået fra.

Politik|Indstilling|Vindende gruppepolitikobjekt
---|---|---
Slå Windows Defender Antivirus fra|Aktiveret|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>Hvis sikkerhedsindstillinger implementeres via gruppepolitikindstillingen (GPP)

Under overskriften element i *registreringsdatabasen (Nøglesti: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender, Værdinavn: DisableAntiSpyware)* kan du se noget i retning af følgende post, der angiver, at Microsoft Defender Antivirus er slået fra.

DisableAntiSpyware|-
---|---
Vindende gruppepolitikobjekt|Win10-Workstations
Resultat: Succes|
**Generel**|
Handling|Opdater
**Egenskaber**|
Hive|HKEY_LOCAL_MACHINE
Nøglesti|SOFTWARE\Policies\Microsoft\Windows Defender
Værdiens navn|DisableAntiSpyware
Værditype|REG_DWORD
Værdidata|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>Hvis sikkerhedsindstillinger implementeres via registreringsdatabasenøgle

Rapporten kan indeholde følgende tekst, der angiver, at Microsoft Defender Antivirus er slået fra:

> Registreringsdatabase (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>Hvis sikkerhedsindstillingerne er angivet i Windows eller Windows Server

Din indbildningsadministrator har muligvis angivet sikkerhedspolitiken **[DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** lokalt via *GPEdit.exe*, *LGPO.exe* eller ved at ændre registreringsdatabasen i deres opgavesekvens. Du kan konfigurere [et billed-id, der er tillid](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) til, Microsoft Defender Antivirus.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>Slå Microsoft Defender Antivirus til igen

Microsoft Defender Antivirus automatisk, hvis intet andet antivirusprogram er aktivt i øjeblikket. Du skal slå tredjeparts antivirusprogrammet helt fra for at sikre, at Microsoft Defender Antivirus kan køre med fuld funktionalitet.

> [!WARNING]
> Løsninger, der foreslår, at  du redigerer Windows Defender-startværdierne for *wdboot*, *wdfilter*, *wdnisdrv*, *wdnissvc* og *windefend* i HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services understøttes ikke, og kan tvinge dig til at genafbilde dit system.

Passiv tilstand er tilgængelig, hvis du begynder at bruge Microsoft Defender til slutpunkt og et antivirusprogram fra tredjepart sammen med Microsoft Defender Antivirus. Passiv tilstand gør Microsoft Defender Antivirus at scanne filer og opdatere sig selv, men det afhjælper ikke trusler. Desuden er overvågning af funktionsmåder via [Beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md) i realtid ikke tilgængelig under passiv tilstand, medmindre forebyggelse af [datatab på slutpunkter (DLP)](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) er implementeret.

En anden funktion, der [kaldes begrænset periodisk scanner](limited-periodic-scanning-microsoft-defender-antivirus.md), er tilgængelig for slutbrugere, når Microsoft Defender Antivirus indstillet til automatisk at blive deaktiveret. Denne funktion gør Microsoft Defender Antivirus at scanne filer med jævne mellemrum sammen med et tredjeparts antivirusprogram ved hjælp af et begrænset antal registreringer.

> [!IMPORTANT]
> Begrænset periodisk scanner anbefales ikke i virksomhedsmiljøer. Registrerings-, administrations- og rapporteringsfunktionerne, der er tilgængelige, når Microsoft Defender Antivirus i denne tilstand, reduceres i forhold til aktiv tilstand.

### <a name="see-also"></a>Se også

- [Microsoft Defender Antivirus kompatibilitet](microsoft-defender-antivirus-compatibility.md)
- [Microsoft Defender Antivirus i Windows Sikkerhed appen](microsoft-defender-security-center-antivirus.md)
