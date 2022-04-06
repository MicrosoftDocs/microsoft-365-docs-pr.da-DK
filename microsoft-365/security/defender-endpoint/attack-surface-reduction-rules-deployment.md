---
title: Forudsætninger for udrulning af ASR-regler
description: Indeholder en oversigt over og en forudsætning for udrulning af ASR-regler (Attack Surface Reduction).
keywords: Installation af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, forebyggelsessystem for værtsindtrængen, beskyttelsesregler, regler for bekæmpelse af udnyttelse, anti-exploit, udnyttelsesregler, regler til forebyggelse af infektion, Microsoft Defender for Endpoint, konfigurer ASR-regler
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
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 0180bfcef9d478dcf8e334a180ea3df993585e00
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666410"
---
# <a name="asr-rules-deployment-prerequisites"></a>Forudsætninger for udrulning af ASR-regler

## <a name="before-you-begin"></a>Før du begynder

Angrebsoverflader er alle de steder, hvor din organisation er sårbar over for cybertrusler og angreb. Din organisations angrebsoverflader omfatter alle de steder, hvor en hacker kan kompromittere organisationens enheder eller netværk. Reduktion af angrebsoverfladen betyder beskyttelse af organisationens enheder og netværk, hvilket efterlader hackere med færre måder at angribe på. Det kan hjælpe at konfigurere ASR-regler (Attack Surface Reduction) – en af de mange sikkerhedsfunktioner, der findes i Microsoft Defender for Endpoint.

ASR-regler er målrettet bestemte softwarefunktioner, f.eks.:

- Start af eksekverbare filer og scripts, der forsøger at downloade eller køre filer
- Kørsel af slørede eller på anden måde mistænkelige scripts
- Funktionsmåder, som apps normalt ikke optræder under normalt dag-til-dag-arbejde

Ved at reducere de forskellige angrebsoverflader kan du hjælpe med at forhindre angreb i at ske i første omgang.

Under den indledende forberedelse er det vigtigt, at du forstår funktionerne i de systemer, du skal indføre. Hvis du forstår funktionerne, kan det hjælpe dig med at finde ud af, hvilke ASR-regler der er vigtigst for at beskytte din organisation. Derudover er der flere forudsætninger, som du skal være opmærksom på som forberedelse til din ASR-udrulning.

>[!IMPORTANT]
>Denne vejledning indeholder billeder og eksempler, der kan hjælpe dig med at beslutte, hvordan du konfigurerer ASR-regler. Disse billeder og eksempler afspejler muligvis ikke de bedste konfigurationsindstillinger for dit miljø.

Før du starter, skal du gennemse [Oversigt over reduktion af angrebsoverflade](overview-attack-surface-reduction.md) og [Afmystificerende regler for reduktion af angrebsoverfladen – del 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) for grundlæggende oplysninger. Hvis du vil vide mere om dækningsområder og potentielle indvirkninger, skal du sætte dig ind i det aktuelle sæt ASR-regler. se [Reference til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md).  Når du bliver fortrolig med de ASR-regler, der er angivet, skal du notere dig GUID-tilknytningerne pr. regel. se: [MATRIX FOR ASR-regler og GUID'er](attack-surface-reduction-rules-reference.md#asr-rules-and-guids-matrix).

ASR-regler er kun én egenskab i funktionerne til reduktion af angrebsoverfladen i Microsoft Defender for Endpoint. Dette dokument vil gå mere i detaljer om at installere ASR-regler effektivt for at stoppe avancerede trusler som menneskeligt drevet ransomware og andre trusler.  

### <a name="rules-by-category"></a>Regler efter kategori

Som beskrevet i [Brug regler for reduktion af angrebsoverfladen for at forhindre malware-infektion](attack-surface-reduction.md), er der flere regler for reduktion af angrebsoverfladen i MDE, som du kan aktivere for at beskytte din organisation. Følgende er reglerne opdelt efter kategori:

<br/>

| Polymorfe trusler | Tværgående flytning & tyveri af legitimationsoplysninger | Regler for produktivitetsapps |  Mailregler | Scriptregler | Regler for diverse |
|:---|:---|:---|:---|:---|:---|
| Bloker eksekverbare filer fra at køre, medmindre de opfylder en prævalens (1000 maskiner), alder (24 timer) eller listekriterier, der er tillid til | Bloker procesoprettelser, der stammer fra kommandoerne PSExec og WMI | Bloker Office apps fra oprettelse af eksekverbart indhold | Bloker eksekverbart indhold fra mailklient og webmail | Bloker sløret JS/VBS/PS/makrokode | Bloker misbrug af udnyttede sårbare underskrevne førere <sup>[[1](#fn1)]<sup></sup>  |
| Bloker processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB | Bloker tyveri af legitimationsoplysninger fra delsystemet Windows lokale sikkerhedsmyndigheder (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Bloker Office apps fra oprettelse af underordnede processer |  Bloker kun Office kommunikationsprogrammer fra oprettelse af underordnede processer | Bloker JS/VBS fra start af downloadet eksekverbart indhold | |
| Brug avanceret beskyttelse mod ransomware | Bloker vedholdenhed via WMI-hændelsesabonnement | Bloker Office apps fra at indsætte kode i andre processer | Bloker Office kommunikationsapps fra oprettelse af underordnede processer | | |
| | | Bloker Adobe Reader fra at oprette underordnede processer | | | |

(<a id="fn1">1</a>) _Bloker misbrug af udnyttede sårbare signerede drivere_ er i øjeblikket ikke tilgængelig i MEM Endpoint-sikkerhed. Du kan konfigurere denne regel ved hjælp af [MEM OMA-URI](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Nogle ASR-regler genererer betydelig støj, men blokerer ikke funktionalitet. Hvis du f.eks. opdaterer Chrome. Chrome får adgang til lsass.exe. adgangskoder gemmes i lsass på enheden. Chrome bør dog ikke få adgang til lokale lsass.exe. Hvis du aktiverer reglen for at blokere adgang til lsass, genereres der mange hændelser. Disse hændelser er gode hændelser, fordi softwareopdateringsprocessen ikke skal have adgang til lsass.exe. Aktivering af denne regel blokerer Chrome-opdateringer fra at få adgang til lsass, men blokerer ikke Chrome fra at opdatere. Dette gælder også for andre programmer, der foretager unødvendige kald for at lsass.exe. _Bloker adgang til lsass-reglen_ blokerer unødvendige kald til lsass, men blokerer ikke programmet fra at køre.

### <a name="infrastructure-requirements"></a>Infrastrukturkrav

Selvom der kan anvendes flere metoder til implementering af ASR-regler, er denne vejledning baseret på en infrastruktur, der består af:

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- Windows 10 og Windows 11 enheder
- Microsoft Defender for Endpoint E5- eller Windows E5-licenser

Hvis du vil drage fuld fordel af ASR-regler og -rapportering, anbefaler vi, at du bruger en Microsoft 365 Defender E5- eller Windows E5-licens og A5. Få mere at vide: [Minimumkrav til Microsoft Defender for Endpoint](minimum-requirements.md).

>[!Note]
>Der er flere metoder til konfiguration af ASR-regler. ASR-regler kan konfigureres ved hjælp af: Microsoft Endpoint Manager (MEM), PowerShell, Gruppepolitik, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Hvis du bruger en anden infrastrukturkonfiguration end den, der er angivet for _infrastrukturkrav_ (ovenfor), kan du få mere at vide om installation af regler for reduktion af angrebsoverfladen ved hjælp af andre konfigurationer her: [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>ASR-regelafhængigheder

Microsoft Defender Antivirus skal være aktiveret og konfigureret som primær antivirusløsning og skal være i følgende tilstand:

- Primær antivirus-/antimalwareløsning  
- Tilstand: Aktiv tilstand

Microsoft Defender Antivirus må ikke være i nogen af følgende tilstande:

- Passiv
- Passiv tilstand med slutpunktsregistrering og svar (Slutpunktsregistrering og -svar) i bloktilstand
- Begrænset periodisk scanning (LPS)
- Ud

Se: [Skybaseret beskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>Cloud Protection (MAPS) skal være aktiveret

Microsoft Defender Antivirus fungerer problemfrit sammen med Microsofts cloudtjenester. Disse cloudbeskyttelsestjenester, også kaldet Microsoft Advanced Protection Service (MAPS), forbedrer standardbeskyttelse i realtid og giver muligvis det bedste antivirusforsvar. Cloudbeskyttelse er afgørende for at forhindre brud på malware og en vigtig komponent i ASR-regler.
[Slå skybaseret beskyttelse til i Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Microsoft Defender Antivirus komponenter skal være aktuelle versioner

Følgende Microsoft Defender Antivirus komponentversioner må ikke være mere end to versioner, der er ældre end den version, der er mest tilgængelig i øjeblikket:

- **Microsoft Defender Antivirus platformsopdateringsversion** – Microsoft Defender Antivirus platform opdateres månedligt.
- **Microsoft Defender Antivirus programversion** – Microsoft Defender Antivirus opdateres månedligt.
- **Microsoft Defender Antivirus sikkerhedsintelligens** – Microsoft opdaterer løbende Microsoft Defender Security Intelligence (også kendt som, definition og signatur) for at håndtere de nyeste trusler og for at tilpasse registreringslogikken.

Hvis du bevarer Microsoft Defender Antivirus aktuelle versioner, hjælper det med at reducere asr-reglerne for falske positive resultater og forbedrer Microsoft Defender Antivirus registreringsfunktioner. Du kan finde flere oplysninger om de aktuelle versioner, og hvordan du opdaterer de forskellige Microsoft Defender Antivirus komponenter, [ved at besøge support til Microsoft Defender Antivirus platform](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>Advarsel

Nogle regler fungerer ikke godt, hvis ikke-signerede internt udviklede programmer og scripts er i høj brug. Det er sværere at installere ASR-regler, hvis kodesignering ikke gennemtvinges.

## <a name="asr-rules-deployment-steps"></a>Trin til installation af ASR-regler

Som med enhver ny implementering i stor skala, der potentielt kan påvirke din line of business-drift, er det vigtigt at være metodisk i din planlægning og implementering. På grund af de effektive funktioner i ASR-regler til forebyggelse af malware er omhyggelig planlægning og installation af disse regler nødvendig for at sikre, at de fungerer bedst for dine unikke kundearbejdsprocesser. Hvis du vil arbejde i dit miljø, skal du planlægge, teste, implementere og anvende ASR-regler omhyggeligt.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="Udrulningsfaserne for ASR-regler" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>For kunder, der bruger en HIPS, der ikke er Microsoft, og som skifter til Microsoft Defender for Endpoint regler for reduktion af angrebsoverfladen: Microsoft råder kunderne til at køre deres HIPS-løsning side om side med installation af deres ASR-regler, indtil det øjeblik, du skifter fra overvågning til bloktilstand. Vær opmærksom på, at du skal kontakte tredjepartsleverandøren af antivirusprogrammet for at få anbefalinger til udelukkelse.  

## <a name="additional-topics-in-this-deployment-collection"></a>Yderligere emner i denne installationssamling

[Fase 1: Plan](attack-surface-reduction-rules-deployment-plan.md)

[Fase 2: Test](attack-surface-reduction-rules-deployment-test.md)

[Fase 3: Implementer](attack-surface-reduction-rules-deployment-implement.md)

[Fase 4: Operationaliser](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="reference"></a>Reference

### <a name="blogs"></a>Blogs

[Afmystificerende regler for reduktion af angrebsoverfladen – del 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Afmystificerende regler for reduktion af angrebsoverfladen – del 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Afmystificerende regler for reduktion af angrebsoverfladen – del 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Afmystificerende regler for reduktion af angrebsoverfladen – del 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>ASR-samling

[Oversigt over reduktion af angrebsoverflade](overview-attack-surface-reduction.md)

[Brug regler for reduktion af angrebsoverfladen for at forhindre malware-infektion](attack-surface-reduction.md)

[Aktivér regler for reduktion af angrebsoverflade](enable-attack-surface-reduction.md)

[Reference til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md)

[Ofte stillede spørgsmål om reduktion af angrebsoverflade](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Adresser falske positive/negativer i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)

[Skybaseret beskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)

[Slå skybaseret beskyttelse til i Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md)

[Konfigurer og valider udeladelser baseret på filtypenavn, navn eller placering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[understøttelse af Microsoft Defender Antivirus platform](manage-updates-baselines-microsoft-defender-antivirus.md)

[Oversigt over lagerbeholdning i Microsoft 365 Apps Administration](/deployoffice/admincenter/inventory)

[Opret en udrulningsplan for Windows](/windows/deployment/update/create-deployment-plan)

[Brug rollebaseret adgangskontrol og områdekoder til distribueret it i Intune](/mem/intune/fundamentals/scope-tags)

[Tildel enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Administrationswebsteder

[Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/#home)

[Reduktion af angrebsoverfladen](https://security.microsoft.com/asr?viewid=detections)

[Konfigurationer af ASR-regler](https://security.microsoft.com/asr?viewid=configuration)

[Undtagelser for ASR-regler](https://security.microsoft.com/asr?viewid=exclusions)
