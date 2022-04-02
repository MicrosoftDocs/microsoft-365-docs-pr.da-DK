---
title: Skift fra ikke-Microsoft-slutpunktsbeskyttelse til Microsoft Defender for Endpoint
description: Skift til en Microsoft Defender for Endpoint, som omfatter Microsoft Defender Antivirus til din løsning til slutpunktsbeskyttelse.
keywords: overførsel, windows defender, avanceret slutpunktsbeskyttelse, antivirus, antimalware, passiv tilstand, aktiv tilstand
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-overview
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
- m365initiative-defender-endpoint
ms.topic: overview
ms.custom: migrationguides
ms.date: 11/29/2021
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.technology: mde
ms.openlocfilehash: e93e762501b942a67cef35a95bb2a9a2b1113e3a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465855"
---
# <a name="make-the-switch-from-non-microsoft-endpoint-protection-to-microsoft-defender-for-endpoint"></a>Skift fra ikke-Microsoft-slutpunktsbeskyttelse til Microsoft Defender for Endpoint

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804) Hvis du overvejer at skifte fra en løsning, der ikke er Microsoft-slutpunktsbeskyttelse, til [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Defender til slutpunkt), eller du er i planlægningsfasen, kan du bruge denne artikel som vejledning. I denne artikel beskrives den overordnede proces med at flytte til Defender for Endpoint.

:::image type="content" source="images/nonms-mde-migration.png" alt-text="Overførselsprocessen til at skifte din slutpunktsbeskyttelsesløsning til Defender for Endpoint" lightbox="images/nonms-mde-migration.png":::

Når du skifter til Defender for Endpoint, starter du med din ikke-Microsoft-antivirus-/antimalwarebeskyttelse i aktiv tilstand. Derefter skal du konfigurere Microsoft Defender Antivirus i passiv tilstand og onboarde dine enheder til Defender til Slutpunkt. Derefter skal du konfigurere dine funktioner til slutpunktsbeskyttelse, Microsoft Defender Antivirus til aktiv tilstand, og kontrollere, at alt fungerer korrekt. Til sidst skal du fjerne den løsning, der ikke er fra Microsoft.

## <a name="the-migration-process"></a>Overførselsprocessen

Processen med at overføre til Defender til slutpunkt kan opdeles i tre faser, som beskrevet i følgende tabel:

:::image type="content" source="images/phase-diagrams/migration-phases.png" alt-text="MDE-overførselsprocessen" lightbox="images/phase-diagrams/migration-phases.png":::


<br/><br/>

|Fase|Beskrivelse|
|--|--|
|[Forberede din overførsel](switch-to-mde-phase-1.md)|Under [**klargøringsfasen**](switch-to-mde-phase-1.md): <br/>1. Opdater din organisations enheder.<br/>2. Få Defender til slutpunkt.<br/>3. Planlæg roller og tilladelser, og giv adgang til Microsoft 365 Defender portal.<br/>4. Konfigurer din enheds proxy og internetindstillinger for at aktivere kommunikation mellem din organisations enheder og Defender til slutpunkt. |
|[Konfigurer Defender til Slutpunkt](switch-to-mde-phase-2.md)|Under [**konfigurationsfasen**](switch-to-mde-phase-2.md): <br/>1. Aktivér/geninstaller Microsoft Defender Antivirus, og indstil den til passiv tilstand.<br/>2. Konfigurer Defender til slutpunkt.<br/>3. Føj Defender til slutpunkt til udeladelseslisten for din eksisterende løsning.<br/>4. Føj din eksisterende løsning til udeladelseslisten for Microsoft Defender Antivirus.<br/>5. Konfigurer dine enhedsgrupper, samlinger og organisationsenheder.<br/>6. Konfigurer dine antimalwarepolitikker og indstillinger for beskyttelse i realtid.|
|[Onboard to Defender til Slutpunkt](switch-to-mde-phase-3.md)|I [**onboard-fasen**](switch-to-mde-phase-3.md): <br/>1. Onboard dine enheder til Defender for Endpoint.<br/>2. Kør en registreringstest.<br/>3. Bekræft, Microsoft Defender Antivirus kører i passiv tilstand.<br/>4. Hent opdateringer til Microsoft Defender Antivirus.<br/>5. Fjern din eksisterende løsning til slutpunktsbeskyttelse.<br/>6. Sørg for, at Defender til Slutpunkt fungerer korrekt.|

## <a name="whats-included-in-microsoft-defender-for-endpoint"></a>Hvad er inkluderet i Microsoft Defender for Endpoint?

I denne overførselsvejledning fokuserer vi på næste [generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md) [og slutpunktsregistrering og -svar](overview-endpoint-detection-response.md) som et udgangspunkt for at flytte til Defender for Endpoint. Men Defender til Slutpunkt indeholder meget mere end antivirus- og slutpunktsbeskyttelse. Defender til Slutpunkt er en samlet platform til forebyggelse af beskyttelse, registrering efter brud, automatisk undersøgelse og svar. Følgende tabel opsummerer funktioner og egenskaber i Defender til slutpunkt.

<br/><br/>

|Funktion/funktion|Beskrivelse|
|---|---|
|[Trussels & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)|Funktionaliteter & håndtering af sikkerhedsrisici for trusler hjælper dig med at identificere, vurdere og afhjælpe problemer på tværs af dine slutpunkter (f.eks. enheder).|
|[Reduktion af angrebsoverfladen](overview-attack-surface-reduction.md)|Regler for reduktion af angrebsoverfladen hjælper med at beskytte din organisations enheder og programmer mod cybertrusler og angreb.|
|[Næste generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md)|Næste generations beskyttelse omfatter Microsoft Defender Antivirus at hjælpe med at blokere trusler og malware.|
|[Registrering af slutpunkt og svar](overview-endpoint-detection-response.md)|Funktioner til registrering af slutpunkter og svar registrerer, undersøger og reagerer på forsøg på indtrængen og aktive brud.|
|[Avanceret jagt](advanced-hunting-overview.md)|Avancerede muligheder for jagt gør det muligt for sikkerhedsteamet at finde indikatorer og enheder med kendte eller potentielle trusler.|
|[Blokering og inddæmmelse af funktionsmåder](behavioral-blocking-containment.md)|Funktionsmådeblokering og -inddæmmelse hjælper med at identificere og stoppe trusler baseret på deres funktionsmåde og procestræer, selv når truslen er begyndt at blive udført.|
|[Automatiseret undersøgelse og afhjælpning](automated-investigations.md)|Automatiserede undersøgelses- og svarmuligheder undersøger beskeder og løser straks overtrædelser.|
|[Trusselssøgningstjeneste](microsoft-threat-experts.md) (Microsoft-trusselseksperter)|Trusselsgrupper giver sikkerhedsteams mulighed for at overvåge og analysere på ekspertniveau og for at sikre, at der ikke overser vigtige trusler.|

**Vil du vide mere? Se [Defender for Endpoint](microsoft-defender-endpoint.md).**

## <a name="next-step"></a>Næste trin

- Fortsæt med [at forberede din overførsel](switch-to-mde-phase-1.md).
