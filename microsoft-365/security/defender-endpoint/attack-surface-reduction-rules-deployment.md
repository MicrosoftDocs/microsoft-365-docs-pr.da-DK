---
title: Forudsætninger for implementering af ASR-regler
description: Giver oversigt og nødvendige vejledning om implementering af regler for reduktion af angrebsoverfladen.
keywords: Implementering af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, beskyttelsessystem til forebyggelse af indtrængen, beskyttelsesregler, anti exploit, udnyttelsesregler, regler for forebyggelse af indtrængen, Microsoft Defender til slutpunkt, konfigurer ASR-regler
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: 7a05d2712adb37121b1e625ab5c4774a60af3e81
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63601037"
---
# <a name="asr-rules-deployment-prerequisites"></a>Forudsætninger for implementering af ASR-regler

## <a name="before-you-begin"></a>Før du begynder

Angrebsoverfladerne er alle de steder, hvor din organisation er sårbar over for cybertrusler og angreb. Din organisations angrebsoverflader omfatter alle de steder, hvor en hacker kan kompromittere din organisations enheder eller netværk. At reducere din angrebsoverflade betyder, at du beskytter din organisations enheder og netværk, hvilket efterlader hackere med færre måder at angreb på. Det kan være en hjælp at konfigurere reduktion af angrebsoverfladen – en af mange sikkerhedsfunktioner i Microsoft Defender til slutpunkt.

ASR-regler målretter visse softwarefunktionsmåder, f.eks.:

- Åbne eksekverbare filer og scripts, der forsøger at hente eller køre filer
- Kører obskøne eller på anden måde mistænkelige scripts
- Funktionsmåder, som apps normalt ikke sker under normalt arbejde fra dag til dag

Ved at reducere de forskellige angrebsoverflader kan du forhindre, at angrebene finder sted i første omgang.

Under din indledende forberedelse er det vigtigt, at du forstår funktionerne i de systemer, du får sat på plads. Når du forstår funktionerne, kan det hjælpe dig med at afgøre, hvilke ASR-regler der er de vigtigste for at beskytte din organisation. Der er desuden flere forudsætninger, som du skal være i gang med før din asr-installation.

>[!IMPORTANT]
>Denne vejledning indeholder billeder og eksempler, der kan hjælpe dig med at beslutte, hvordan du konfigurerer ASR-regler. Disse billeder og eksempler afspejler muligvis ikke de bedste konfigurationsindstillinger for dit miljø.

Før du starter, skal du [gennemgå Oversigt](overview-attack-surface-reduction.md) over reduktion af [angrebsoverfladen og Afmystificere](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) regler for reduktion af angrebsoverfladen – del 1 for at få grundlæggende oplysninger. For at forstå dækningsområder og potentielle konsekvenser skal du gøre dig bekendt med det aktuelle sæt asr-regler. Se Reference [til regel for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md).

ASR-regler er kun én funktionalitet for reduktion af angrebsoverfladen i Microsoft Defender til slutpunkt. Dette dokument vil gå mere i detaljer med implementering af ASR-regler effektivt for at stoppe avancerede trusler som f.eks. ransomware og andre trusler.  

### <a name="rules-by-category"></a>Regler efter kategori

Som beskrevet i Brug regler for reduktion af angrebsoverfladen til at forhindre [malware](attack-surface-reduction.md) inficeret er der flere regler for reduktion af angrebsoverfladen i MDE, som du kan aktivere for at beskytte din organisation. Følgende er reglerne opdelt efter kategori:

<br/>

| Polymorphic threats | Efterfølgende bevægelse & legitimationstyveri | Produktivitetsappregler |  Mailregler | Scriptregler | Misc-regler |
|:---|:---|:---|:---|:---|:---|
| Bloker eksekverbare filer, så de ikke kan køre, medmindre de opfylder bestemte kriterier (1000 computere), alder (24 timer) eller pålidelige listekriterier | Bloker procesoprettelser, der stammer fra PSExec- og WMI-kommandoer | Bloker Office apps i at oprette eksekverbart indhold | Bloker eksekverbart indhold fra mailklient og webmail | Bloker uskadelig JS/VBS/PS/makrokode | Bloker misbrug af udnyttet sårbar signerede drivere <sup>[[1](#fn1)]<sup></sup>  |
| Bloker upålidelige og usignerede processer, der køres fra USB | Bloker for at stjæle legitimationsoplysninger Windows det lokale sikkerhedscenters undersystem (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Bloker Office apps i at oprette underordnede processer |  Bloker kun Office kommunikationsprogrammer i at oprette underordnede processer | Bloker JS/VBS i at starte hentet eksekverbart indhold | |
| Brug avanceret beskyttelse mod ransomware | Bloker vedholdenhed gennem WMI-hændelsesabonnementet | Bloker Office apps fra at indsætte kode i andre processer | Bloker Office kommunikationsapps i at oprette underordnede processer | | |
| | | Bloker Adobe Reader i at oprette underordnede processer | | | |

(<a id="fn1">1</a>) _Bloker misbrug af udnyttet sårbar signerede drivere_ er i øjeblikket ikke tilgængelig i MEM-slutpunktssikkerhed. Du kan konfigurere denne regel ved hjælp [af MEM OMA-URI](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Nogle AA-regler genererer betydelig støj, men blokerer ikke funktionalitet. Hvis du f.eks. opdaterer Chrome; Chrome får adgang lsass.exe; adgangskoder gemmes i lsass på enheden. Chrome bør dog ikke have adgang til lokale enheder lsass.exe. Hvis du aktiverer reglen til at blokere adgang til lsas, genererer den en masse hændelser. Disse hændelser er gode begivenheder, fordi softwareopdateringsprocessen ikke bør have adgang til lsass.exe. Aktivering af denne regel blokerer for Chrome-opdateringer i at få adgang til lsass, men blokerer ikke Chrome fra opdatering. det gælder også andre programmer, der foretager unødvendige opkald for at lsass.exe. Reglen _Bloker adgang til lsass_ blokerer unødvendige opkald til lsass, men blokerer ikke programmet fra at køre.

### <a name="infrastructure-requirements"></a>Krav til infrastruktur

Selvom der er mulighed for flere metoder til implementering af ASR-regler, er denne vejledning baseret på en infrastruktur bestående af:

- Azure Active Directory
- Microsofts slutpunktsadministration (MEM)
- Windows 10 og Windows 11 enheder
- Microsoft Defender til Endpoint E5 eller Windows E5-licenser

Hvis du vil drage fuld fordel af regler og rapporter om a heltal, anbefaler vi, at du bruger en Microsoft 365 Defender E5 eller Windows E5-licens og A5. Få mere at vide: [Minimumskrav til Microsoft Defender til slutpunkt](minimum-requirements.md).

>[!Note]
>Der er flere metoder til at konfigurere ASR-regler. ASR-regler kan konfigureres ved hjælp af: Microsoft Endpoint Manager (MEM), PowerShell, Gruppepolitik, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Hvis du bruger en anden infrastrukturkonfiguration, end den, der er _angivet for Krav_ til infrastruktur (ovenfor), kan du få mere at vide om regler for reduktion af angrebsoverfladen ved hjælp af andre konfigurationer her: Aktivér regler for reduktion af angrebsoverfladen. [](enable-attack-surface-reduction.md)  

### <a name="asr-rules-dependencies"></a>Afhængigheder af ASR-regler

Microsoft Defender Antivirus skal være aktiveret og konfigureret som primær antivirusløsning og skal være i følgende tilstand:

- Primær antivirus-/antimalwareløsning  
- Tilstand: Aktiv tilstand

Microsoft Defender Antivirus må ikke være i nogen af følgende tilstande:

- Passiv
- Passiv tilstand med slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) i bloktilstand
- Begrænset periodisk scanning (LPS)
- Fra

Se: [Cloud-leveret beskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>Cloud Protection (MAPS) skal være aktiveret

Microsoft Defender Antivirus problemfrit med Microsofts skytjenester. Disse skybeskyttelsestjenester, der også kaldes Microsoft Advanced Protection Service (MAPS), forbedrer standard beskyttelse i realtid og giver dig det bedste antivirusbeskyttelse. Skybeskyttelse er afgørende for at forhindre brud på malware og en vigtig komponent i ASR-regler.
[Slå skybaseret beskyttelse til i Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Microsoft Defender Antivirus komponenter skal være aktuelle versioner

Følgende Microsoft Defender Antivirus-komponentversioner må højst være to versioner ældre end den mest tilgængelige version:

- **Microsoft Defender Antivirus platformopdateringsversion** – Microsoft Defender Antivirus-platformen opdateres hver måned.
- **Microsoft Defender Antivirus - programmet** Microsoft Defender Antivirus opdateret hver måned.
- **Microsoft Defender Antivirus sikkerhedsintelligens** – Microsoft opdaterer kontinuerligt Microsoft Defender-sikkerhedsintelligens (også kendt som definition og signatur) for at håndtere de seneste trusler og for at forbedre registreringslogik.

At Microsoft Defender Antivirus aktuelle versioner hjælper med at reducere ASR-regler for falske positive resultater og Microsoft Defender Antivirus registreringsfunktioner. Hvis du vil have mere at vide om de aktuelle versioner, og hvordan du opdaterer de Microsoft Defender Antivirus forskellige komponenter, [skal Microsoft Defender Antivirus-platformens support.](manage-updates-baselines-microsoft-defender-antivirus.md)

### <a name="caveat"></a>Advarsel

Nogle regler fungerer ikke godt, hvis ikke-signerede, internt udviklet program og scripts er i høj brug. Det er sværere at installere ASR-regler, hvis signering af kode ikke gennemtvinges.

## <a name="asr-rules-deployment-steps"></a>Installationstrin for ASR-regler

Som med alle nye, brede implementeringer, der potentielt kan påvirke dine line of business-handlinger, er det vigtigt at være metodisk i din planlægning og implementering. På grund af de effektive funktioner i asr-regler til forebyggelse af malware er nøje planlægning og installation af disse regler nødvendig for at sikre, at de fungerer bedst i forhold til dine unikke kundearbejdsprocesser. For at arbejde i dit miljø skal du planlægge, teste, implementere og drifte ASR-regler omhyggeligt.  

> [!div class="mx-imgBorder"]
> ![ASR-regler for installationsfaser](images/asr-rules-deployment-phases.png)

>[!Note]
>Til kunder, der bruger en ikke-Microsoft HIPS og skifter til Microsoft Defender til reduktionsregler for angrebsoverfladen for Slutpunkt: Microsoft anbefaler kunder at køre deres HIPS-løsning side om side med deres implementering af ASR-regler, indtil det øjeblik, du skifter fra Audit til bloktilstand. Husk, at du skal kontakte din tredjepartsleverandør af antivirus for at få anbefalinger om udelukkelse.  

## <a name="additional-topics-in-this-deployment-collection"></a>Flere emner i denne installationssamling

[Fase 1: Plan](attack-surface-reduction-rules-deployment-plan.md)

[Fase 2: Test](attack-surface-reduction-rules-deployment-test.md)

[Fase 3: Implementer](attack-surface-reduction-rules-deployment-implement.md)

[Fase 4: Drift](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="reference"></a>Reference

### <a name="blogs"></a>Blogs

[Afmystificering af reduktionsregler for angrebsoverfladen – Del 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Afmystificering af reduktionsregler for angrebsoverfladen – Del 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Afmystificering af reduktionsregler for angrebsoverfladen – Del 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Afmystificering af reduktionsregler for angrebsoverfladen – Del 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>ASR-samling

[Oversigt over reduktion af angrebsoverfladen](overview-attack-surface-reduction.md)

[Brug regler for reduktion af angrebsoverfladen til at forhindre malware inficeret](attack-surface-reduction.md)

[Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md)

[Reference til begrænsningsregler for angrebsoverfladen](attack-surface-reduction-rules-reference.md)

[Ofte stillede spørgsmål om reduktion af angrebsoverfladen](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Adressere falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)

[Cloud-leveret beskyttelse og -Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)

[Slå skybaseret beskyttelse til i Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md)

[Konfigurere og validere udeladelse baseret på udvidelse, navn eller placering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[Microsoft Defender Antivirus-platform](manage-updates-baselines-microsoft-defender-antivirus.md)

[Oversigt over lageret Microsoft 365 Apps Administration](/deployoffice/admincenter/inventory)

[Opret en installationsplan for Windows](/windows/deployment/update/create-deployment-plan)

[Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT i Intune](/mem/intune/fundamentals/scope-tags)

[Tildel enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Administrationswebsteder

[Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/#home)

[Reduktion af angrebsoverfladen](https://security.microsoft.com/asr?viewid=detections)

[ASR-regler Konfigurationer](https://security.microsoft.com/asr?viewid=configuration)

[Udeladelse af ASR-regler](https://security.microsoft.com/asr?viewid=exclusions)
