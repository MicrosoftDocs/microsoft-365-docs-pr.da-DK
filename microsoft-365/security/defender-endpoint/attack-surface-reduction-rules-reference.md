---
title: Reference til regler for reduktion af angrebsoverflade
description: Viser oplysninger om regler for reduktion af angrebsoverflader pr. regel.
keywords: Angreb overfladereduktion regler, ASR, asr regler, hofter, vært indbrud forebyggelse system, beskyttelsesregler, anti-exploit regler, anti-exploit regler, anti-plotit, udnytte regler, infektion forebyggelse regler, Microsoft Defender for Endpoint, konfigurere ASR regler, ASR regel beskrivelse
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.date: 02/04/2022
ms.openlocfilehash: 2f76a8ec53d6f7c809ed9f6612f2c8abf7388d1b
ms.sourcegitcommit: f723ebbc56db8013598a88b0d7f13214d9d3eb10
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/10/2022
ms.locfileid: "65294772"
---
# <a name="attack-surface-reduction-rules-reference"></a>Reference til regler for reduktion af angrebsoverflade

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme:**

- Windows

Denne artikel indeholder oplysninger om regler for reduktion af angreb:

- [Understøttede versioner af operativsystemet](#supported-operating-systems)
- [Understøttede systemer til administration af konfiguration](#supported-configuration-management-systems)
- [Oplysninger om besked pr. regel og meddelelse](#per-rule-alert-and-notification-details)
- [Matrix for ASR-regler og GUID'er](#asr-rules-and-guids-matrix)
- [ASR-regeltilstande](#asr-rule-modes)
- [Beskrivelser pr. regel](#per-rule-descriptions)
  - Regelbeskrivelser
  - Navne på systemregel for konfigurationsstyring

## <a name="supported-operating-systems"></a>Understøttede operativsystemer

I følgende tabel vises de understøttede operativsystemer til regler, der i øjeblikket er offentligt tilgængelige. Reglerne vises alfabetisk i denne tabel.

> [!Note]
>
> Medmindre andet er angivet, er minimum Windows&nbsp; 10 build version 1709 (RS3, build 16299) eller nyere. Det mindste Windows&nbsp; Server-build er version 1809 eller nyere.
>
> Regler for reduktion af angrebsoverfladen i Windows&nbsp; Server2012R2&nbsp;&nbsp; og Windows&nbsp; Server2016&nbsp; er tilgængelige for enheder, der er onboardet ved hjælp af den moderne samlede løsningspakke. Du kan få flere oplysninger [under Ny funktionalitet i den moderne samlede løsning til Windows Server 2012 R2 og 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

| Regelnavn| &nbsp;Windows 11 <br>Og<br> &nbsp;Windows 10 | &nbsp;Windows Server <br> 2022 <br>Og<br>  &nbsp;Windows Server <br> 2019 | Windows Server | &nbsp;Windows Server <br> 2016 <br> <sup>[[1, 2](#fn1)]<sup></sup> | &nbsp;Windows Server <br> 2012R2&nbsp; <br> <sup>[[1, 2](#fn1)]<sup></sup> |
|:---|:---:|:---:|:---:|:---:|:---:|
| [Bloker misbrug af udnyttede sårbare bilister](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y | Y | Y <br> version 1803 (halvårlig kanal) eller nyere | Y | Y |
| [Bloker Adobe Reader fra at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Y version 1809 eller nyere | Y | Y | Y | Y |
| [Bloker alle Office programmer, så de ikke kan oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) | Y | Y | Y | Y | Y |
| [Bloker tyveri af legitimationsoplysninger fra delsystemet Windows lokale sikkerhedsmyndighed (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y <br> version 1803 eller nyere | Y | Y | Y | Y |
| [Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) | Y | Y | Y | Y | Y |
| [Bloker eksekverbare filer, så de ikke kører, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y <br> version 1803 eller nyere | Y | Y | Y | Y |
| [Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) | Y | Y | Y | Y | Y |
| [Bloker JavaScript eller VBScript fra start af downloadet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y | Y | Y | N | N |
| [Bloker Office programmer, så de ikke kan oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) | Y | Y | Y | Y | Y |
| [Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes)  | Y | Y | Y | Y | Y |
| [Bloker Office kommunikationsprogram fra oprettelse af underordnede processer](#block-office-communication-application-from-creating-child-processes) | Y | Y | Y | Y | Y |
| [Bloker vedholdenhed via WMI-hændelsesabonnement](#block-persistence-through-wmi-event-subscription) <br> \*_Fil- og mappeudeladelser understøttes ikke._ | Y <br> version 1903 (build 18362) eller nyere | Y | Y <br> version 1903 (build 18362) eller nyere | N | N |
| [Bloker procesoprettelser, der stammer fra kommandoerne PSExec og WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y <br> version 1803 eller nyere | Y | Y | Y | Y |
| [Bloker processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y | Y | Y | Y | Y |
| [Bloker Win32 API-kald fra Office makroer](#block-win32-api-calls-from-office-macros) | Y | Y | Y | N | N |
| [Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | Y <br> version 1803 eller nyere | Y | Y | Y | Y |

(<a id="fn1">1</a>) Refererer til den moderne samlede løsning til Windows Server 2012 og 2016. Du kan finde flere oplysninger under [Onboard Windows Servers til Defender for Endpoint-tjenesten](configure-server-endpoints.md).

(<a id="fn1">2</a>) For Windows&nbsp; Server 2016 og Windows&nbsp; Server 2012R2&nbsp; er den version af Microsoft Endpoint Configuration Manager, der som minimum kræves, version 2111.

## <a name="supported-configuration-management-systems"></a>Understøttede systemer til administration af konfiguration

Links til oplysninger om systemversioner til konfigurationsstyring, der refereres til i denne tabel, er angivet under denne tabel.

|Regelnavn | Intune | Microsoft Endpoint Manager |Microsoft Endpoint Configuration Manager |<sup>Gruppepolitik[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Bloker misbrug af udnyttede sårbare bilister](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y  | Y MEM OMA-URI |   | Y  |  Y  |
|[Bloker Adobe Reader fra at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Y |   |  | Y  | Y  |
|[Bloker alle Office programmer, så de ikke kan oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) | Y |   |Y <br><br> CB 1710 | Y  | Y  |
|[Bloker tyveri af legitimationsoplysninger fra delsystemet Windows lokale sikkerhedsmyndighed (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y  |   | Y <br><br>CB 1802 | Y  | Y  |
|[Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) | Y |  |Y <br><br> CB 1710 | Y | Y  |
|[Bloker eksekverbare filer, så de ikke kører, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y |   | Y <br><br> CB 1802 |  Y |  Y |
|[Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) | Y |   |  Y  <br><br> CB 1710 | Y  | Y  |
|[Bloker JavaScript eller VBScript fra start af downloadet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y |   | Y <br><br> CB 1710 | Y  | Y  |
|[Bloker Office programmer, så de ikke kan oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes) | Y |  | Y <br><br> CB 1710 | Y  | Y  |
|[Bloker Office kommunikationsprogram fra oprettelse af underordnede processer](#block-office-communication-application-from-creating-child-processes) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[Bloker vedholdenhed via WMI-hændelsesabonnement](#block-persistence-through-wmi-event-subscription) |  |  |  |Y   | Y  |
|[Bloker procesoprettelser, der stammer fra kommandoerne PSExec og WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y |   |   |  Y | Y  |
|[Bloker processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y |   |Y <br><br> CB 1802  | Y  | Y  |
|[Bloker Win32 API-kald fra Office makroer](#block-win32-api-calls-from-office-macros) | Y |   | Y <br><br> CB 1710  | Y  |  Y |
|[Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | Y |   | Y <br><br> CB 1802 | Y  | Y  |

  (<a id="fn1">1</a>) Du kan konfigurere regler for reduktion af angrebsoverflader pr. regel ved hjælp af en hvilken som helst regels GUID.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_SCCM er nu Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Pr. regeladvarsel og meddelelsesoplysninger

Toastbeskeder genereres for alle regler i bloktilstand. Regler i nogen anden tilstand genererer ikke toastbeskeder

For regler med "Regeltilstand" angivet:

- ASR-regler med \<ASR Rule, Rule State\> kombinationer bruges til at vise beskeder (toastbeskeder) på Microsoft Defender for Endpoint kun for enheder på blokniveau med høj sky. Enheder, der ikke har et højt skyblokeringsniveau, genererer ikke beskeder for nogen <ASR-regel, regeltilstand> kombinationer
- Slutpunktsregistrering og -svar beskeder genereres for ASR-regler i de angivne tilstande, men kun for enheder på højt skyblokeringsniveau.

| Regelnavn: | Regeltilstand: | Genererer beskeder i Slutpunktsregistrering og -svar? <br> (Ja&nbsp;\|&nbsp;Nej) | Genererer toastbeskeder? <br> (Ja&nbsp;\|&nbsp;Nej) |
|---|:---:|:---:|:---:|
|   |   |  _Kun for enheder med blokniveau i høj sky_ | _Kun i bloktilstand_ |
|[Bloker misbrug af udnyttede sårbare bilister](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | Y |
|[Bloker Adobe Reader fra at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Bloker  | Y <br> Kræver enhed på blokniveau med høj sky  | Y <br> Kræver enhed på blokniveau med høj sky |
|[Bloker alle Office programmer, så de ikke kan oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) |   | N | Y |
|[Bloker tyveri af legitimationsoplysninger fra delsystemet Windows lokale sikkerhedsmyndighed (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | Y |
|[Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) |   | Y <br> Kræver enhed på blokniveau med høj sky | Y <br> Kræver enhed på blokniveau med høj sky |
|[Bloker eksekverbare filer, så de ikke kører, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | Y |
|[Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) |  Overvågningsblok&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokniveau med høj sky  | N \| Y <br> Kræver enhed på blokniveau med høj sky |
|[Bloker JavaScript eller VBScript fra start af downloadet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Bloker | Y <br> Kræver enhed på blokniveau med høj sky  | Y <br> Kræver enhed på blokniveau med høj sky |
|[Bloker Office programmer, så de ikke kan oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) |   | N | Y |
|[Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | Y |
|[Bloker Office kommunikationsprogram fra oprettelse af underordnede processer](#block-office-communication-application-from-creating-child-processes) |  |  N | Y |
|[Bloker vedholdenhed via WMI-hændelsesabonnement](#block-persistence-through-wmi-event-subscription) |  Overvågningsblok&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokniveau med høj sky  | N \| Y <br> Kræver enhed på blokniveau med høj sky |
|[Bloker procesoprettelser, der stammer fra kommandoerne PSExec og WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | Y |
|[Bloker processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Overvågningsblok&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokniveau med høj sky  | N \| Y <br> Kræver enhed på blokniveau med høj sky |
|[Bloker Win32 API-kald fra Office makroer](#block-win32-api-calls-from-office-macros) |   | N | Y |
|[Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | Overvågningsblok&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokniveau med høj sky  | N \| Y <br> Kræver enhed på blokniveau med høj sky |
  
## <a name="asr-rules-and-guids-matrix"></a>Matrix for ASR-regler og GUID'er

| Regelnavn | Regel-GUID |
|:-----|:-----|
| Bloker misbrug af udnyttede sårbare bilister | 56a863a9-875e-4185-98a7-b882c64b5ce5 |
| Bloker Adobe Reader fra at oprette underordnede processer | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c |
| Bloker alle Office programmer, så de ikke kan oprette underordnede processer | d4f940ab-401b-4efc-aadc-ad5f3c50688a |
| Bloker tyveri af legitimationsoplysninger fra delsystemet Windows lokale sikkerhedsmyndighed (lsass.exe) | 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2 |
| Bloker eksekverbart indhold fra mailklient og webmail | be9ba2d9-53ea-4cdc-84e5-9b1eeee46550 |
| Bloker eksekverbare filer, så de ikke kører, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til | 01443614-cd74-433a-b99e-2ecdc07bfc25 |
| Bloker udførelse af potentielt slørede scripts | 5beb7efe-fd9a-4556-801d-275e5ffc04cc |
| Bloker JavaScript eller VBScript fra start af downloadet eksekverbart indhold | d3e037e1-3eb8-44c8-a917-57927947596d |
| Bloker Office programmer, så de ikke kan oprette eksekverbart indhold | 3b576869-a4ec-4529-8536-b80a7769e899 |
| Bloker Office programmer fra at indsætte kode i andre processer | 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84 |
| Bloker Office kommunikationsprogram fra oprettelse af underordnede processer | 26190899-1602-49e8-8b27-eb1d0a1ce869 |
| Bloker vedholdenhed via WMI-hændelsesabonnement <br>* Fil- og mappeudeladelser understøttes ikke. | e6db77e5-3df2-4cf1-b95a-636979351e5b |
| Bloker procesoprettelser, der stammer fra kommandoerne PSExec og WMI | d1e49aac-8f56-4280-b9ba-993a6d77406c |
| Bloker processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB | b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 |
| Bloker Win32 API-kald fra Office makroer | 92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b |
| Brug avanceret beskyttelse mod ransomware | c1db55ab-c21a-4637-bb3f-a12568109d35 |

## <a name="asr-rule-modes"></a>ASR-regeltilstande

- **Ikke konfigureret** eller **deaktiveret**: Dette er den tilstand, hvor ASR-reglen ikke er blevet aktiveret eller deaktiveret. Koden for denne tilstand = 0.
- **Blok**: Dette er den tilstand, som ASR-reglen er aktiveret i. Koden for denne tilstand er 1.
- **Overvågning**: Dette er den tilstand, som ASR-reglen evalueres i for dens virkningsfulde funktionsmåde over for den organisation eller det miljø, hvor den er udrullet. Koden for denne tilstand er 2.
- **Advare** Dette er den tilstand, hvor ASR-reglen er aktiveret og præsenterer en meddelelse til slutbrugeren, men tillader slutbrugeren at omgå blokken. Koden for denne tilstand er 6.

_Advarselstilstand_ er en type blokeringstilstand, der giver brugerne besked om potentielt risikable handlinger. Brugerne kan vælge at tilsidesætte advarselsmeddelelsen om blokering og tillade den underliggende handling. Brugerne kan vælge **OK** for at gennemtvinge blokken eller vælge bypassindstillingen – **Fjern blokering** – via den toastbesked om slutbrugerens pop op-meddelelse, der genereres på tidspunktet for blokken. Når blokeringen af advarslen er fjernet, tillades handlingen, indtil næste gang advarselsmeddelelsen vises, hvorefter slutbrugeren skal udføre handlingen igen.

Hvis der klikkes på knappen Tillad, undertrykkes blokken i 24 timer. Efter 24 timer skal slutbrugeren tillade blokken igen. Advarselstilstanden for ASR-regler understøttes kun for RS5+-enheder (1809+). Hvis bypass er tildelt ASR-regler på enheder med ældre versioner, vil reglen være i blokeret tilstand.

Du kan også angive en regel i advarselstilstand via PowerShell ved blot at angive AttackSurfaceReductionRules_Actions som "Advar". Eksempel:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Pr. regelbeskrivelser

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloker misbrug af udnyttede sårbare bilister

Denne regel forhindrer et program i at skrive en sårbar signeret driver til disken. Sårbare signerede drivere i naturen kan udnyttes af lokale programmer \- _, der har tilstrækkelige rettigheder_ \- til at få adgang til kernen. Sårbare signerede drivere gør det muligt for angribere at deaktivere eller omgå sikkerhedsløsninger, hvilket i sidste ende fører til, at systemet kompromitteres.

**Reglen block abuse of exploited vulnerable signed drivers** rule not block a driver already already on the system from beloaded.

> [!NOTE]
>
> Du kan konfigurere denne regel ved hjælp af MEM OMA-URI. Se [MEM OMA-URI](enable-attack-surface-reduction.md#mem) for at konfigurere brugerdefinerede regler.
>
> Du kan også konfigurere denne regel ved hjælp af [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Hvis du vil have undersøgt en faktor, skal du bruge dette websted til at [sende en driver til analyse](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

Intune navn: `Block abuse of exploited vulnerable signed drivers` (endnu ikke tilgængeligt)

Configuration Manager navn: Endnu ikke tilgængeligt
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies: none provided by engineering
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Bloker Adobe Reader fra at oprette underordnede processer

Denne regel forhindrer angreb ved at blokere Adobe Reader i at oprette processer.

Ved hjælp af social engineering eller udnyttelser kan malware downloade og starte nyttedata og bryde ud af Adobe Reader. Ved at blokere underordnede processer fra at blive genereret af Adobe Reader, forhindres malware, der forsøger at bruge den som en vektor, i at sprede sig.

Intune navn:`Process creation from Adobe Reader (beta)`

Configuration Manager navn: Endnu ikke tilgængeligt

GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Avanceret jagthandlingstype:

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

Afhængigheder: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Bloker alle Office programmer, så de ikke kan oprette underordnede processer

Denne regel blokerer Office apps fra at oprette underordnede processer. Office apps omfatter Word, Excel, PowerPoint, OneNote og Access.

Oprettelse af skadelige underordnede processer er en almindelig malwarestrategi. Malware, der misbruger Office som en vektor, kører ofte VBA-makroer og udnytter kode til at downloade og forsøge at køre flere nyttedata. Nogle legitime line of business-programmer kan dog også generere underordnede processer til godartede formål; f.eks. gydning af en kommandoprompt eller brug af PowerShell til at konfigurere indstillinger i registreringsdatabasen.

Intune navn:`Office apps launching child processes`

Configuration Manager navn:`Block Office application from creating child processes`

GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Avanceret jagthandlingstype:

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

Afhængigheder: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloker tyveri af legitimationsoplysninger fra delsystemet Windows lokale sikkerhedsmyndighed

Denne regel hjælper med at forhindre tyveri af legitimationsoplysninger ved at låse LSASS (Local Security Authority Subsystem Service) nede.

LSASS godkender brugere, der logger på en Windows computer. Microsoft Defender Credential Guard i Windows forhindrer normalt forsøg på at udtrække legitimationsoplysninger fra LSASS. Nogle organisationer kan dog ikke aktivere Credential Guard på alle deres computere på grund af kompatibilitetsproblemer med brugerdefinerede chipkortdrivere eller andre programmer, der indlæses i LSA (Local Security Authority). I disse tilfælde kan hackere bruge hackværktøjer som Mimikatz til at skrabe cleartext-adgangskoder og NTLM-hashen fra LSASS.

> [!NOTE]
> I nogle apps optæller koden alle kørende processer og forsøger at åbne dem med udtømmende tilladelser. Denne regel afviser appens handling for procesåbning og logfører oplysningerne i loggen over sikkerhedshændelser. Denne regel kan generere en masse støj. Hvis du har en app, der blot optæller LSASS, men ikke har nogen reel indvirkning på funktionaliteten, er det ikke nødvendigt at føje den til listen over undtagelser. I sig selv angiver denne post i hændelsesloggen ikke nødvendigvis en ondsindet trussel.
  
> [!IMPORTANT]
> Standardtilstanden for ASR-reglen (Attack Surface Reduction) "Block credential stealing from the Windows local security authority subsystem (lsass.exe)" ændres fra **Ikke konfigureret** til **Konfigureret**, og standardtilstanden er angivet til **Bloker**. Alle andre ASR-regler forbliver i standardtilstanden: **Ikke konfigureret**. Der er allerede indbygget yderligere filtreringslogik i reglen for at reducere slutbrugermeddelelser. Kunder kan konfigurere reglen til **tilstanden Overvågning**, **Advar** eller **Deaktiveret** , hvilket tilsidesætter standardtilstanden. Funktionaliteten af denne regel er den samme, uanset om reglen er konfigureret i standardtilstanden, eller hvis du aktiverer Bloker-tilstand manuelt.

Intune navn:`Flag credential stealing from the Windows local security authority subsystem`

Configuration Manager navn:`Block credential stealing from the Windows local security authority subsystem`

GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Avanceret jagthandlingstype:

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Afhængigheder: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloker eksekverbart indhold fra mailklient og webmail

Denne regel blokerer følgende filtyper fra at starte via mail, der er åbnet i Microsoft Outlook-programmet, eller Outlook.com og andre populære webmailudbydere:

- Eksekverbare filer (f.eks. .exe, .dll eller .scr)
- Scriptfiler (f.eks. en PowerShell .ps-, Visual Basic .vbs- eller JavaScript-.js-fil)

Intune navn:`Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager navn:`Block executable content from email client and webmail`

GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Avanceret jagthandlingstype:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Afhængigheder: MDAV

> [!NOTE]
> Reglen **Bloker eksekverbart indhold fra mailklienten og webmailen** har følgende alternative beskrivelser, afhængigt af hvilket program du bruger:
>
> - Intune (konfigurationsprofiler): Udførelse af eksekverbart indhold (exe, dll, ps, js, vbs osv.) blev droppet fra mail (webmail/mail-klient) (ingen undtagelser).
> - Endpoint Manager: Bloker download af eksekverbart indhold fra mail- og webmailklienter.
> - Gruppepolitik: Bloker eksekverbart indhold fra mailklient og webmail.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Bloker eksekverbare filer, så de ikke kører, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til

Denne regel blokerer eksekverbare filer, f.eks. .exe, .dll eller .scr, fra start. Det kan derfor være risikabelt at starte upålidelige eller ukendte eksekverbare filer, da det muligvis ikke indledningsvist er tydeligt, om filerne er skadelige.

> [!IMPORTANT]
> Du skal [aktivere skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) for at bruge denne regel.
>
> Reglen **Bloker kørsel af eksekverbare filer, medmindre de opfylder et prævalens-, alders- eller listekriterium med** GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` , der er tillid til, ejes af Microsoft og er ikke angivet af administratorer. Denne regel bruger skybaseret beskyttelse til at opdatere listen, der er tillid til, regelmæssigt.
>
> Du kan angive individuelle filer eller mapper (ved hjælp af mappestier eller fuldt kvalificerede ressourcenavne), men du kan ikke angive, hvilke regler eller undtagelser der gælder for.

Intune navn:`Executables that don't meet a prevalence, age, or trusted list criteria`

Configuration Manager navn:`Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

Avanceret jagthandlingstype:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Afhængigheder: MDAV, Cloud Protection

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloker udførelse af potentielt slørede scripts

Denne regel registrerer mistænkelige egenskaber i et sløret script.

Script tilsløring er en almindelig teknik, som både malware forfattere og legitime applikationer bruger til at skjule intellektuel ejendom eller reducere script indlæsningstider. Malware forfattere bruger også tilsløring til at gøre skadelig kode sværere at læse, hvilket forhindrer tæt kontrol af mennesker og sikkerhedssoftware.

Intune navn:`Obfuscated js/vbs/ps/macro code`

Configuration Manager navn:`Block execution of potentially obfuscated scripts`

GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Avanceret jagthandlingstype:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Afhængigheder: MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Bloker JavaScript eller VBScript fra start af downloadet eksekverbart indhold

Denne regel forhindrer scripts i at starte potentielt skadeligt downloadet indhold. Malware, der er skrevet i JavaScript eller VBScript, fungerer ofte som en downloader for at hente og starte anden malware fra internettet.

Selvom det ikke er almindeligt, bruger line of business-programmer nogle gange scripts til at downloade og starte installationsprogrammer.

Intune navn:`js/vbs executing payload downloaded from Internet (no exceptions)`

Configuration Manager navn:`Block JavaScript or VBScript from launching downloaded executable content`

GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

Avanceret jagthandlingstype:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Afhængigheder: MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Bloker Office programmer, så de ikke kan oprette eksekverbart indhold

Denne regel forhindrer, at Office apps, herunder Word, Excel og PowerPoint, opretter potentielt skadeligt eksekverbart indhold ved at blokere for, at skadelig kode skrives til disken.

Malware, der misbruger Office som en vektor, kan forsøge at bryde ud af Office og gemme skadelige komponenter på disken. Disse skadelige komponenter vil overleve en genstart af computeren og forblive på systemet. Derfor forsvarer denne regel sig mod en fælles vedholdenhedsteknik.

Intune navn:`Office apps/macros creating executable content`

SCCM-navn: `Block Office applications from creating executable content`

GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

Avanceret jagthandlingstype:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Afhængigheder: MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Bloker Office programmer fra at indsætte kode i andre processer

Denne regel blokerer kodeinjektionsforsøg fra Office apps i andre processer.

Hackere kan forsøge at bruge Office apps til at overføre skadelig kode til andre processer via kodeinjektion, så koden kan maskerade som en ren proces.

Der er ingen kendte legitime forretningsmæssige formål med at bruge kodeinjektion.

Denne regel gælder for Word, Excel og PowerPoint.

Intune navn:`Office apps injecting code into other processes (no exceptions)`

Configuration Manager navn:`Block Office applications from injecting code into other processes`

GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Avanceret jagthandlingstype:

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Afhængigheder: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Bloker Office kommunikationsprogram fra oprettelse af underordnede processer

Denne regel forhindrer, at Outlook opretter underordnede processer, samtidig med at legitime Outlook funktioner tillades.

Denne regel beskytter mod social engineering-angreb og forhindrer, at kode misbruges i Outlook. Den beskytter også mod [Outlook regler og formularer](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/), som hackere kan bruge, når en brugers legitimationsoplysninger kompromitteres.

> [!NOTE]
> Denne regel blokerer tip til DLP-politik og værktøjstip i Outlook. Denne regel gælder kun for Outlook og Outlook.com.

Intune navn:`Process creation from Office communication products (beta)`

Configuration Manager navn: Ikke tilgængeligt

GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

Avanceret jagthandlingstype:

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

Afhængigheder: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloker vedholdenhed via WMI-hændelsesabonnement

Denne regel forhindrer malware i at misbruge WMI for at opnå vedholdenhed på en enhed.

> [!IMPORTANT]
> Fil- og mappeudeladelser gælder ikke for denne regel for reduktion af angrebsoverfladen.

Filløse trusler anvender forskellige taktikker for at forblive skjult, for at undgå at blive set i filsystemet og for at få periodisk kontrol over udførelsen. Nogle trusler kan misbruge WMI-lageret og hændelsesmodellen for at forblive skjult.

Intune navn: Ikke tilgængeligt

Configuration Manager navn: Ikke tilgængeligt

GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Avanceret jagthandlingstype:

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

Afhængigheder: MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloker procesoprettelser, der stammer fra kommandoerne PSExec og WMI

Denne regel blokerer processer, der er oprettet via [PsExec](/sysinternals/downloads/psexec) og [WMI](/windows/win32/wmisdk/about-wmi) , fra at køre. Både PsExec og WMI kan udføre kode eksternt, så der er risiko for, at malware misbruger denne funktionalitet til kommando- og kontrolformål eller for at sprede en infektion i hele organisationens netværk.

> [!WARNING]
> Brug kun denne regel, hvis du administrerer dine enheder med [Intune](/intune) eller en anden MDM-løsning. Denne regel er ikke kompatibel med administration via [Microsoft Endpoint Configuration Manager](/configmgr), fordi denne regel blokerer WMI-kommandoer, som Configuration Manager klient bruger til at fungere korrekt.

Intune navn:`Process creation from PSExec and WMI commands`

Configuration Manager navn: Ikke relevant

GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Avanceret jagthandlingstype:

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

Afhængigheder: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloker processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB

Med denne regel kan administratorer forhindre usignerede eller upålidelige eksekverbare filer i at køre fra flytbare USB-drev, herunder SD-kort. Blokerede filtyper omfatter eksekverbare filer (f.eks. .exe, .dll eller .scr)

Intune navn:`Untrusted and unsigned processes that run from USB`

Configuration Manager navn:`Block untrusted and unsigned processes that run from USB`

GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Avanceret jagthandlingstype:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Afhængigheder: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Bloker Win32 API-kald fra Office makroer

Denne regel forhindrer VBA-makroer i at kalde Win32-API'er.

Office VBA aktiverer Win32 API-kald. Malware kan misbruge denne funktion, f.eks [. kalde Win32-API'er for at starte skadelig shellcode](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) uden at skrive noget direkte til disken. De fleste organisationer er ikke afhængige af muligheden for at kalde Win32-API'er i deres daglige funktion, selvom de bruger makroer på andre måder.

Understøttede operativsystemer:

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

Intune navn:`Win32 imports from Office macro code`

Configuration Manager navn:`Block Win32 API calls from Office macros`

GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Avanceret jagthandlingstype:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Afhængigheder: MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Brug avanceret beskyttelse mod ransomware

Denne regel giver et ekstra lag af beskyttelse mod ransomware. Den bruger både klient- og cloud-heuristik til at afgøre, om en fil ligner ransomware. Denne regel blokerer ikke filer, der har et eller flere af følgende egenskaber:

- Det er allerede konstateret, at filen ikke erharmful i Microsoft-cloudmiljøet.
- Filen er en gyldig signeret fil.
- Filen er udbredt nok til ikke at blive betragtet som ransomware.

Reglen har tendens til at fejle på den side af forsigtighed for at forhindre ransomware.

> [!NOTE]
> Du skal [aktivere skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) for at bruge denne regel.

Intune navn:`Advanced ransomware protection`

Configuration Manager navn:`Use advanced protection against ransomware`

GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

Avanceret jagthandlingstype:

- AsrRansomwareAudited
- AsrRansomwareBlocked

Afhængigheder: MDAV, Cloud Protection
