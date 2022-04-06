---
title: Reference til begrænsningsregler for angrebsoverfladen
description: Viser detaljer om regler for reduktion af angrebsoverfladen på regelbasis.
keywords: Regler for reduktion af angrebsoverfladen, ASR-regler, asr-regler, hips, beskyttelsesregler for indtrængen, regler for forebyggelse af indtrængen, antiexploit, udnyttelsesregler, regler for forebyggelse af infning, Microsoft Defender til slutpunkt, konfigurer ASR-regler, beskrivelse af ASR-regel
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
ms.openlocfilehash: 5ffbe15fe9fa06e7c06546f9452d6c4f2bddfc39
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606811"
---
# <a name="attack-surface-reduction-rules-reference"></a>Reference til begrænsningsregler for angrebsoverfladen

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Denne artikel indeholder oplysninger om regler for reduktion af angreb:

- [Understøttede operativsystemversioner](#supported-operating-systems)
- [Understøttede konfigurationsstyringssystemer](#supported-configuration-management-systems)
- [Besked og beskedoplysninger for de forskellige regler](#per-rule-alert-and-notification-details)
- [Beskrivelser efter regel](#per-rule-descriptions)
  - Regelbeskrivelser
  - GUID'er
  - Navne på konfigurationsstyringssystemregel

## <a name="public-preview-supported-operating-systems"></a>Offentlig eksempelvisning: Understøttede operativsystemer

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

I følgende tabel vises de understøttede operativsystemer til reduktion af angrebsoverfladen, der i øjeblikket er foreløbige produkter. Reglerne er angivet i alfabetisk rækkefølge. Medmindre andet er angivet, er minimumversionen af Windows&nbsp; 10-buildet version 1709 (RS3, build 16299) eller nyere; minimum Windows&nbsp; Server-build er version 1809 eller nyere.

> [!NOTE]
> Regler for reduktion af angrebsoverfladen i Windows&nbsp; Server2012R2&nbsp;&nbsp; og Windows&nbsp; Server2016&nbsp; er tilgængelige for enheder, der er onboardet med den moderne samlede løsningspakke. Få mere at vide under Ny funktionalitet i den moderne samlede løsning [til Windows Server 2012 R2 og 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).
>

| Regelnavn | &nbsp;Windows Server 2016 <sup>[[1](#fn1)]<sup></sup> | &nbsp;Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup> |
|---|:---:|:---:|
|[Bloker misbrug af udnyttet sårbar signerede drivere](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y | Y |
|[Bloker Adobe Reader i at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Y | Y |
|[Bloker alle Office i at oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) | Y | Y |
|[Bloker for, at legitimations stjæler Windows det lokale sikkerhedscenters undersystem (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y | Y |
|[Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) | Y | Y |
|[Bloker eksekverbare filer fra at køre, medmindre de opfylder et alders-, alders- eller pålidelige listekriterium](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y | Y |
|[Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) | Y | Y |
|[Bloker JavaScript eller VBScript fra at starte hentet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | N | N |
|[Blokere Office programmer i at oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) | Y | Y |
|[Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes)  | Y | Y |
|[Bloker Office kommunikationsprogrammet i at oprette underordnede processer](#block-office-communication-application-from-creating-child-processes) | Y | Y |
|[Bloker vedholdenhed gennem WMI-hændelsesabonnementet](#block-persistence-through-wmi-event-subscription) \* _Udeladelse af filer og mapper understøttes ikke._ | N | N |
|[Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y | Y |
|[Bloker upålidelige og usignerede processer, der køres fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y | Y |
|[Bloker Win32 API-opkald Office makroer](#block-win32-api-calls-from-office-macros) | N | N |
|[Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | Y | Y |
|  |  |  |

(<a id="fn1">1</a>) Henviser til den moderne, samlede løsning til Windows Server 2012 og 2016. Få mere at vide under [Onboard Windows Servers til Defender for Endpoint-tjenesten](configure-server-endpoints.md).

_Afslut offentlig prøveversion: Understøttede operativsystemer_

## <a name="supported-operating-systems"></a>Understøttede operativsystemer

I følgende tabel vises de understøttede operativsystemer til regler, der i øjeblikket er udgivet til generel tilgængelighed. Reglerne er angivet i alfabetisk rækkefølge.

> [!Note]
>
> Medmindre andet er angivet, er minimumversionen af Windows&nbsp; 10-buildet version 1709 (RS3, build 16299) eller nyere; minimum Windows&nbsp; Server-build er version 1809 eller nyere.
>

|Regelnavn|&nbsp;Windows 10|&nbsp;Windows Server 2019|&nbsp;Windows Server|
|---|:---:|:---:|:---:|
|[Bloker misbrug af udnyttet sårbar signerede drivere](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y | Y | Y <br><br> version 1803 (halvårlige kanal) eller nyere |
|[Bloker Adobe Reader i at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Y version 1809 eller nyere | Y | Y  <br><br> |
|[Bloker alle Office i at oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) | Y | Y | Y <br><br> |
|[Bloker for, at legitimations stjæler Windows det lokale sikkerhedscenters undersystem (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y version 1803 eller nyere | Y <br><br> | Y <br><br> |
|[Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) | Y | Y <br><br> | Y <br><br> |
|[Bloker eksekverbare filer fra at køre, medmindre de opfylder et alders-, alders- eller pålidelige listekriterium](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y version 1803 eller nyere | Y <br><br> | Y <br><br> |
|[Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) | Y | Y <br><br> | Y <br><br> |
|[Bloker JavaScript eller VBScript fra at starte hentet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y | Y <br><br> | Y <br><br> |
|[Blokere Office programmer i at oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) | Y | Y <br><br> | Y <br><br> |
|[Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes)  | Y | Y <br><br> | Y <br><br> |
|[Bloker Office kommunikationsprogrammet i at oprette underordnede processer](#block-office-communication-application-from-creating-child-processes) | Y | Y <br><br> | Y <br><br> |
|[Bloker vedholdenhed gennem WMI-hændelsesabonnementet](#block-persistence-through-wmi-event-subscription) <br><br> \*_Udeladelse af filer og mapper understøttes ikke._ | Y version 1903 (build 18362) eller nyere| Y | Y <br><br> version 1903 (build 18362) eller nyere |
|[Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y version 1803 eller nyere | Y <br><br> | Y <br><br>  |
|[Bloker upålidelige og usignerede processer, der køres fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y | Y <br><br> | Y <br><br> |
|[Bloker Win32 API-opkald Office makroer](#block-win32-api-calls-from-office-macros) | Y | Y <br><br> | Y <br><br> |
|[Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | Y version 1803 eller nyere | Y <br><br> | Y <br><br> |
|  |  |  |  |

## <a name="supported-configuration-management-systems"></a>Understøttede konfigurationsstyringssystemer

Links til oplysninger om konfigurationsstyringssystemversioner, der refereres til i denne tabel, er angivet under denne tabel.

|Regelnavn | Intune | Microsoft Endpoint Manager |Microsoft Endpoint Configuration Manager |<sup>Gruppepolitik[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[Bloker misbrug af udnyttet sårbar signerede drivere](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y  | Y MEM OMA-URI |   | Y  |  Y |
|[Bloker Adobe Reader i at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Y |   | Y | Y  | Y  |
|[Bloker alle Office i at oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) | Y |   |Y <br><br> CB 1710 | Y  | Y  |
|[Bloker for, at legitimations stjæler Windows det lokale sikkerhedscenters undersystem (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y  |   | Y <br><br>CB 1802 | Y  | Y  |
|[Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) | Y |  |Y <br><br> CB 1710 | Y | Y  |
|[Bloker eksekverbare filer fra at køre, medmindre de opfylder et alders-, alders- eller pålidelige listekriterium](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y |   | Y <br><br> CB 1802 |  Y |  Y |
|[Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) | Y |   |  Y  <br><br> CB 1710 | Y  | Y  |
|[Bloker JavaScript eller VBScript fra at starte hentet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y |   | Y <br><br> CB 1710 | Y  | Y  |
|[Blokere Office programmer i at oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes) | Y |  | Y <br><br> CB 1710 | Y  | Y  |
|[Bloker Office kommunikationsprogrammet i at oprette underordnede processer](#block-office-communication-application-from-creating-child-processes) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[Bloker vedholdenhed gennem WMI-hændelsesabonnementet](#block-persistence-through-wmi-event-subscription) |  |  |  |Y   | Y  |
|[Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y |   |   |  Y | Y  |
|[Bloker upålidelige og usignerede processer, der køres fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y |   |Y <br><br> CB 1802  | Y  | Y  |
|[Bloker Win32 API-opkald Office makroer](#block-win32-api-calls-from-office-macros) | Y |   | Y <br><br> CB 1710  | Y  |  Y |
|[Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | Y |   | Y <br><br> CB 1802 | Y  | Y  |
|  |  |  |  |  |  |

  (<a id="fn1">1</a>) Du kan konfigurere regler for reduktion af angrebsoverfladen pr. regel ved hjælp af en regels GUID.

- [Konfigurationsstyring CB 1710](/configmgr/core/servers/manage/updates)
- [Konfigurationsstyring CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft Endpoint Manager CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_SCCM er nu Microsoft Endpoint Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>Besked om og meddelelse for hver regel

Toastbeskeder genereres for alle regler i bloktilstand. Regler i en anden tilstand vil ikke generere toastbeskeder

For regler, hvor "Regeltilstand" er angivet:

- ASR-regler \<ASR Rule, Rule State\> med kombinationer bruges kun til at få besked (toastbeskeder) på Microsoft Defender til slutpunkter på højt skybaseret blokniveau. Enheder, der ikke er på højt skyblokniveau, vil ikke generere beskeder for <ASR-regel,> kombinationer af regeltilstand
- Slutpunktsregistrering og -svar genereres for ASR-regler i de angivne tilstande, men kun for enheder med høj cloud-blok.

| Regelnavn: | Regeltilstand: | Genererer beskeder i Slutpunktsregistrering og -svar? <br> (Ja&nbsp;\|&nbsp;Nej) | Genererer toastbeskeder? <br> (Ja&nbsp;\|&nbsp;Nej) |
|---|:---:|:---:|:---:|
|   |   |  _Kun for enheder med høj cloud-blokniveau_ | _Kun i bloktilstand_ |
|[Bloker misbrug af udnyttet sårbar signerede drivere](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | Y |
|[Bloker Adobe Reader i at oprette underordnede processer](#block-adobe-reader-from-creating-child-processes) | Bloker  | Y <br> Kræver enhed på blokeringsniveau i høj skyen  | Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|[Bloker alle Office i at oprette underordnede processer](#block-all-office-applications-from-creating-child-processes) |   | N | Y |
|[Bloker for, at legitimations stjæler Windows det lokale sikkerhedscenters undersystem (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | Y |
|[Bloker eksekverbart indhold fra mailklient og webmail](#block-executable-content-from-email-client-and-webmail) |   | Y <br> Kræver enhed på blokeringsniveau i høj skyen | Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|[Bloker eksekverbare filer fra at køre, medmindre de opfylder et alders-, alders- eller pålidelige listekriterium](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | Y |
|[Bloker udførelse af potentielt slørede scripts](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokeringsniveau i høj skyen  | N \| Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|[Bloker JavaScript eller VBScript fra at starte hentet eksekverbart indhold](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Bloker | Y <br> Kræver enhed på blokeringsniveau i høj skyen  | Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|[Blokere Office programmer i at oprette eksekverbart indhold](#block-office-applications-from-creating-executable-content) |   | N | Y |
|[Bloker Office programmer fra at indsætte kode i andre processer](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | Y |
|[Bloker Office kommunikationsprogrammet i at oprette underordnede processer](#block-office-communication-application-from-creating-child-processes) |  |  N | Y |
|[Bloker vedholdenhed gennem WMI-hændelsesabonnementet](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokeringsniveau i høj skyen  | N \| Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|[Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | Y |
|[Bloker upålidelige og usignerede processer, der køres fra USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokeringsniveau i høj skyen  | N \| Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|[Bloker Win32 API-opkald Office makroer](#block-win32-api-calls-from-office-macros) |   | N | Y |
|[Brug avanceret beskyttelse mod ransomware](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> Kræver enhed på blokeringsniveau i høj skyen  | N \| Y <br> Kræver enhed på blokeringsniveau i høj skyen |
|   |   |   |   |
  
## <a name="asr-rule-modes"></a>ASR-regeltilstande

- **Ikke konfigureret** eller **deaktiveret**: Dette er den tilstand, hvor ASR-reglen ikke er aktiveret eller er blevet deaktiveret. Koden for denne stat = 0.
- **Blok**: Dette er den tilstand, hvor ASR-reglen er aktiveret. Koden for denne stat er 1.
- **Overvågning**: Dette er den tilstand, hvori ASR-reglen evalueres for dens virkningsfulde funktionsmåde i den organisation eller det miljø, hvori den installeres. Koden for denne stat er 2.
- **Advar** Dette er den tilstand, hvori ASR-reglen er aktiveret og viser en meddelelse til slutbrugeren, men tillader slutbrugeren at springe blokken over. Koden for denne stat er 6.

_Tilstanden Advar_ er en type blokering, der advarer brugerne om potentielt risikabelt arbejde. Brugere kan vælge at springe advarselsmeddelelsen uden om og tillade den underliggende handling. Brugerne kan vælge **OK** for at gennemtvinge blokeringen, eller de kan vælge bypass-indstillingen **– Fjern** blokeringen – via pop op-meddelelsen om toast til slutbrugeren, der genereres på tidspunktet for blokken. Når advarslen ikke er blokeret, er handlingen tilladt, indtil næste gang advarslen vises, hvorefter slutbrugeren skal genformularen for handlingen.

Hvis der klikkes på knappen Tillad, skjules blokken i 24 timer. Efter 24 timer skal slutbrugeren tillade blokken igen. Advarselstilstanden for ASR-regler understøttes kun for RS5+ (1809+)-enheder. Hvis tilgår er tildelt ASR-regler på enheder med ældre versioner, vil reglen være i blokeret tilstand.

Du kan også angive en regel i advarselstilstand via PowerShell ved blot at AttackSurfaceReductionRules_Actions som "Advar". Eksempel:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>Beskrivelser af de forskellige regler

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>Bloker misbrug af udnyttet sårbar signerede drivere

Denne regel forhindrer et program i at skrive en sårbar signeret driver til disk. In-the-wild, vulnerable signed drivers can beexploited by local applications \- _that have sufficient privileges_ \- to gain access to the kernel. Sårbar signerede drivere gør det muligt for hackere at deaktivere eller omgå sikkerhedsløsninger, hvilket i sidste ende førte til, at systemet blev kompromitteret.

Reglen **Bloker misbrug af udnyttet sårbar signerede drivere** blokerer ikke en driver, der allerede findes på systemet, fra at blive indlæst.

> [!NOTE]
>
> Du kan konfigurere denne regel ved hjælp af MEM OMA-URI. Se [MEM OMA-URI til](enable-attack-surface-reduction.md#mem) konfiguration af brugerdefinerede regler.
>
> Du kan også konfigurere denne regel ved hjælp af [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> Hvis du vil have en driver til at se nærmere på den, skal du bruge [dette websted til at sende en driver til analyse](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

Intune Name: `Block abuse of exploited vulnerable signed drivers` (endnu ikke tilgængelig)

Konfigurationsstyring navn: Endnu ikke tilgængelig
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies:
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>Bloker Adobe Reader i at oprette underordnede processer

Denne regel forhindrer angreb ved at blokere Adobe Reader i at oprette processer.

Malware kan via social engineering eller udnyttelse downloade og starte nyttedata og bryde ud af Adobe Reader. Ved at blokere børns processer i at blive genereret af Adobe Reader forhindres malware i at forsøge at bruge det som en vektor i at sprede sig.

Intune-navn: `Process creation from Adobe Reader (beta)`

Konfigurationsstyring navn: Endnu ikke tilgængelig

GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

Avanceret jagthandlingstype:

- AsrAdobeReaderProcessAudited
- AsrAdobeReaderProcessBlocked

Afhængigheder: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>Bloker alle Office i at oprette underordnede processer

Denne regel blokerer Office oprette underordnede processer. Office omfatter Word, Excel, PowerPoint, OneNote og Access.

Oprettelse af skadelige børns processer er en almindelig strategi for malware. Malware, som Office som en vektor, kører ofte VBA-makroer og udnytter kode til at downloade og forsøge at køre flere nyttedata. Nogle legitime line of business-programmer kan dog også generere børneprocesser til gode formål; f.eks. konfiguration af en kommandoprompt eller brug af PowerShell til at konfigurere indstillinger i registreringsdatabasen.

Intune-navn: `Office apps launching child processes`

Konfigurationsstyring navn: `Block Office application from creating child processes`

GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

Avanceret jagthandlingstype:

- AsrOffice DirekteProcessAudited
- AsrOffice DirekteProcessBlokeret

Afhængigheder: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>Bloker for at stjæle legitimationsoplysninger Windows det lokale sikkerhedscenters undersystem

Denne regel hjælper med at forhindre, at der stjæles legitimationsoplysninger, ved at låse LSASS (Local Security Authority Subsystem Service).

LSASS godkender brugere, der logger på en Windows computer. Microsoft Defender Credential Guard Windows normalt forsøge at udtrække legitimationsoplysninger fra LSASS. Nogle organisationer kan dog ikke aktivere Credential Guard på alle deres computere på grund af kompatibilitetsproblemer med brugerdefinerede chipkortdrivere eller andre programmer, der indlæses i LSA (Local Security Authority). I disse tilfælde kan hackere bruge hackværktøjer som Mimikatz til at skrabe cleartext-adgangskoder og NTLM-hashes fra LSASS.

> [!NOTE]
> I nogle apps optæller koden alle kørende processer og forsøger at åbne dem med udtømmende tilladelser. Denne regel afviser handlingen Åbn for appen og logføres oplysningerne til sikkerhedshændelsesloggen. Denne regel kan generere en masse støj. Hvis du har en app, der blot optæller LSASS, men ikke har nogen reelle konsekvenser for funktionaliteten, er der ingen grund til at føje den til udeladelseslisten. Denne hændelseslogpost angiver i sig selv ikke nødvendigvis en ondsindet trussel.
  
> [!IMPORTANT]
> Standardtilstanden for ASR-reglen (Attack Surface Reduction) "Block credential stealing from the Windows local security authority subsystem (lsass.exe)" ændres fra **Ikke** konfigureret til Konfigureret og standardtilstanden  angivet til Bloker **.** Alle andre ASR-regler forbliver i deres standardtilstand: **Ikke konfigureret**. Der er allerede indført yderligere filtreringslogik i reglen for at reducere beskeder fra slutbrugere. Kunder kan konfigurere reglen til **tilstanden Overvågning**, **Advar** eller **Deaktiveret** , som tilsidesætter standardtilstanden. Funktionaliteten for denne regel er den samme, uanset om reglen er konfigureret i standardtilstanden, eller hvis du aktiverer Bloker tilstand manuelt.  

Intune-navn: `Flag credential stealing from the Windows local security authority subsystem`

Konfigurationsstyring navn: `Block credential stealing from the Windows local security authority subsystem`

GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

Avanceret jagthandlingstype:

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

Afhængigheder: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>Bloker eksekverbart indhold fra mailklient og webmail

Denne regel blokerer følgende filtyper fra at starte fra mails, der er åbnet i Microsoft Outlook-programmet eller Outlook.com og andre populære webmailudbydere:

- Eksekverbare filer (f.eks. .exe, .dll eller .scr)
- Scriptfiler (f.eks. en PowerShell.ps- Visual Basic .vbs- eller JavaScript-.js fil)

Intune-navn: `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

Microsoft Endpoint Manager navn:`Block executable content from email client and webmail`

GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

Avanceret jagthandlingstype:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

Afhængigheder: MDAV

> [!NOTE]
> Reglen **Bloker eksekverbart indhold fra mailklienten og webmail** har følgende alternative beskrivelser, afhængigt af hvilket program du bruger:
>
> - Intune (Konfigurationsprofiler): Udførelse af eksekverbart indhold (exe, dll, ps, js, vbs osv.) er tabt fra mail (webmail/mailklient) (ingen undtagelser).
> - Endpoint Manager: Bloker hentning af eksekverbart indhold fra mail- og webmailklienter.
> - Gruppepolitik: Bloker eksekverbart indhold fra mailklient og webmail.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>Bloker eksekverbare filer fra at køre, medmindre de opfylder et alders-, alders- eller pålidelige listekriterium

Denne regel blokerer eksekverbare filer, f.eks. .exe, .dll eller .scr, i at starte. Derfor kan det være risikabelt at starte upålidelige eller ukendte eksekverbare filer, da det i første omgang ikke vil være klart, om filerne er skadelige.

> [!IMPORTANT]
> Du skal [aktivere skybaseret leveringsbeskyttelse for](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) at bruge denne regel.
>
> Reglen **Bloker eksekverbare** filer fra at køre, medmindre de opfylder et alders-, alders- eller pålidelige listekriterium med GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` , der ejes af Microsoft og ikke er angivet af administratorer. Denne regel anvender skybaseret beskyttelse til at opdatere dens liste, der er tillid til, regelmæssigt.
>
> Du kan angive individuelle filer eller mapper (ved hjælp af mappestier eller fuldt kvalificerede ressourcenavne), men du kan ikke angive, hvilke regler eller undtagelser, der gælder for.

Intune-navn: `Executables that don't meet a prevalence, age, or trusted list criteria`

Konfigurationsstyring navn: `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

Avanceret jagthandlingstype:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

Afhængigheder: MDAV, Cloud Protection

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>Bloker udførelse af potentielt slørede scripts

Denne regel registrerer mistænkelige egenskaber i et obskøn script.

Script er en almindelig teknik, som både malwareforfattere og legitime programmer bruger til at skjule intellektuel ejendom eller mindske scriptindlæsningstiderne. Malwareforfattere bruger også forvirring til at gøre skadelig kode sværere at læse, hvilket forhindrer nøje gransker i mennesker og sikkerhedssoftware.

Intune-navn: `Obfuscated js/vbs/ps/macro code`

Konfigurationsstyring navn: `Block execution of potentially obfuscated scripts`

GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

Avanceret jagthandlingstype:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

Afhængigheder: MDAV, AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>Bloker JavaScript eller VBScript fra at starte hentet eksekverbart indhold

Denne regel forhindrer scripts i at starte potentielt skadeligt hentet indhold. Malware, der er skrevet i JavaScript eller VBScript, fungerer ofte som downloader for at hente og starte anden malware fra internettet.

Selvom det ikke er almindeligt, bruger line of business-programmer nogle gange scripts til at downloade og starte installationsprogrammer.

Intune-navn: `js/vbs executing payload downloaded from Internet (no exceptions)`

Konfigurationsstyring navn: `Block JavaScript or VBScript from launching downloaded executable content`

GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

Avanceret jagthandlingstype:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

Afhængigheder: MDAV, AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>Blokere Office programmer i at oprette eksekverbart indhold

Denne regel forhindrer, at Office-apps, herunder Word, Excel og PowerPoint, kan oprette potentielt skadeligt eksekverbart indhold ved at blokere for, at der skrives skadelig kode på disken.

Malware, der misbruger Office en vektor, kan forsøge at bryde ud af Office og gemme skadelige komponenter på disken. Disse skadelige komponenter vil stadig kunne genstarte computeren og blive ved med at være i systemet. Derfor beskytter denne regel sig mod en fælles vedholdenhedsteknik.

Intune-navn: `Office apps/macros creating executable content`

SCCM-navn: `Block Office applications from creating executable content`

GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

Avanceret jagthandlingstype:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

Afhængigheder: MDAV, RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>Bloker Office programmer fra at indsætte kode i andre processer

Denne regel blokerer forsøg på indering af kode Office apps i andre processer.

Hackere kan muligvis forsøge at bruge Office-apps til at overføre skadelig kode til andre processer ved indførsel af kode, så koden kan være en masquerade som en ren proces.

Der er ingen kendte legitime forretningsformål ved indførslen af koder.

Denne regel gælder for Word, Excel og PowerPoint.

Intune-navn: `Office apps injecting code into other processes (no exceptions)`

Konfigurationsstyring navn: `Block Office applications from injecting code into other processes`

GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

Avanceret jagthandlingstype:

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

Afhængigheder: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>Bloker Office kommunikationsprogrammet i at oprette underordnede processer

Denne regel forhindrer, Outlook oprette underordnede processer, samtidig med at legitime funktioner Outlook funktioner.

Denne regel beskytter mod social engineering-angreb og forhindrer udnyttelse af kode fra misbrug af sårbarheder i Outlook. Den beskytter også mod [Outlook og](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) formularer, som hackere kan bruge, når en brugers legitimationsoplysninger er kompromitteret.

> [!NOTE]
> Denne regel blokerer tips til DLP-politikker og værktøjstip Outlook. Denne regel gælder kun for Outlook og Outlook.com.

Intune-navn: `Process creation from Office communication products (beta)`

Konfigurationsstyring navn: Ikke tilgængelig

GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

Avanceret jagthandlingstype:

- AsrOfficeCommAppProcessAudited
- AsrOfficeCommAppProcessBlocked

Afhængigheder: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>Bloker vedholdenhed gennem WMI-hændelsesabonnementet

Denne regel forhindrer malware i at misbruge WMI for at opnå vedholdenhed på en enhed.

> [!IMPORTANT]
> Udeladelse af filer og mapper gælder ikke for denne regel for reduktion af angrebsoverfladen.

Filløse trusler anvender forskellige taktikker for at forblive skjulte, for at undgå at blive set i filsystemet og for at opnå periodiske kontrolforanstaltninger. Nogle trusler kan misbruge WMI-lageret og begivenhedsmodellen for at forblive skjult.

Intune-navn: Ikke tilgængelig

Konfigurationsstyring navn: Ikke tilgængelig

GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

Avanceret jagthandlingstype:

- AsrPersistenceThroughWmiAudited
- VedholdenhedThroughWmiBlocked

Afhængigheder: MDAV, RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer

Denne regel blokerer processer, der er [oprettet via PsExec](/sysinternals/downloads/psexec) og [WMI](/windows/win32/wmisdk/about-wmi) , fra at køre. Både PsExec og WMI kan udføre kode eksternt, så der er en risiko for malware, som misbruger denne funktionalitet af kommando- og kontrolformål eller for at sprede en inficerethed i hele organisationens netværk.

> [!WARNING]
> Brug kun denne regel, hvis du administrerer dine enheder med [Intune eller](/intune) en anden MDM-løsning. Denne regel er ikke kompatibel med administration via [Microsoft Endpoint Configuration Manager](/configmgr), fordi denne regel blokerer WMI-kommandoer, som Konfigurationsstyring-klienten bruger til at fungere korrekt.

Intune-navn: `Process creation from PSExec and WMI commands`

Konfigurationsstyring navn: Ikke relevant

GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

Avanceret jagthandlingstype:

- AsrPsexecWmiProcessAudited
- AsrPsexecWmiProcessBlocked

Afhængigheder: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>Bloker upålidelige og usignerede processer, der køres fra USB

Med denne regel kan administratorer forhindre usignerede eller upålidelige eksekverbare filer i at køre fra USB-flytbare drev, herunder SD-kort. Blokerede filtyper indeholder eksekverbare filer (f.eks. .exe, .dll eller .scr)

Intune-navn: `Untrusted and unsigned processes that run from USB`

Konfigurationsstyring navn: `Block untrusted and unsigned processes that run from USB`

GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

Avanceret jagthandlingstype:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

Afhængigheder: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>Bloker Win32 API-opkald Office makroer

Denne regel forhindrer VBA-makroer i at kalde Win32-API'er.

Office VBA aktiverer Win32 API-opkald. Malware kan misbruge denne funktionalitet, f.eks. [kalde Win32-API'er](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) for at starte skadelig shellcode uden at skrive noget direkte på disken. De fleste organisationer er ikke afhængige af muligheden for at kalde Win32-API'er, når deres daglige funktioner fungerer, også selvom de bruger makroer på andre måder.

Understøttede operativsystemer:

- [Windows 10, version 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Konfigurationsstyring CB 1710](/configmgr/core/servers/manage/updates)

Intune-navn: `Win32 imports from Office macro code`

Konfigurationsstyring navn: `Block Win32 API calls from Office macros`

GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

Avanceret jagthandlingstype:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

Afhængigheder: MDAV, AMSI

### <a name="use-advanced-protection-against-ransomware"></a>Brug avanceret beskyttelse mod ransomware

Denne regel giver et ekstra lag af beskyttelse mod ransomware. Den anvender både klient- og skybaseret heuristics til at afgøre, om en fil ligner ransomware. Denne regel blokerer ikke filer, der har en eller flere af følgende egenskaber:

- Filen er allerede blevet fundet usharmbar i Microsoft-skyen.
- Filen er en gyldig signeret fil.
- Filen bruges så meget, at den ikke betragtes som ransomware.

Reglen er ofte vær forsigtig for at forhindre ransomware.

> [!NOTE]
> Du skal [aktivere skybaseret leveringsbeskyttelse for](enable-cloud-protection-microsoft-defender-antivirus.md) at bruge denne regel.

Intune-navn: `Advanced ransomware protection`

Konfigurationsstyring navn: `Use advanced protection against ransomware`

GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

Avanceret jagthandlingstype:

- AsrRansomwareAudited
- AsrRansomwareBlocked

Afhængigheder: MDAV, Cloud Protection
