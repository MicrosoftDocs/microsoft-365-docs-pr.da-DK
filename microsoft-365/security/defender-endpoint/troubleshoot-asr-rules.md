---
title: Rapportér og foretag fejlfinding af ASR-regler for Microsoft Defender til slutpunkter
description: I dette emne beskrives det, hvordan du rapporterer og foretager fejlfinding af Microsoft Defender for Endpoint ASR-regler
keywords: Regler for reduktion af angrebsoverfladen, asr, hips, forebyggelse af indtrængen, beskyttelsesregler, antieksploit, udnyttelse, forebyggelse af virus, microsoft defender til slutpunkt
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 63c23b0ab0188abe0fb33d27789a437e1e445a2b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592194"
---
# <a name="report-and-troubleshoot-microsoft-defender-for-endpoint-asr-rules"></a>Rapportér og foretag fejlfinding af ASR-regler for Microsoft Defender til slutpunkter

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender den</a> nye grænseflade til overvågning og administration af sikkerhed på tværs af dine Microsoft-identiteter, -data, -enheder, -apps og -infrastruktur. Her kan du nemt få vist organisationens sikkerhedstilstand, handle for at konfigurere enheder, brugere og apps og få beskeder om mistænkelig aktivitet. Portalen Microsoft 365 Defender er beregnet til sikkerhedsadministratorer og sikkerhedsteams for bedre at administrere og beskytte deres organisation. Gå til Microsoft 365 Defender portal på<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

På <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> kan vi tilbyde dig et fuldstændigt kig på de aktuelle ASR-regler for konfiguration og begivenheder i din ejendom. Bemærk, at dine enheder skal være onboardet i Microsoft Defender for Endpoint-tjenesten, for at disse rapporter kan udfyldes.
Her er et skærmbillede fra portalen Microsoft 365 Defender (under **Rapportenheder,** \> **reduktion af** \> **angrebsoverfladen**). På enhedsniveau skal du vælge **Konfiguration fra** ruden **Regler for reduktion af angrebsoverfladen** . Følgende skærmbillede vises, hvor du kan vælge en bestemt enhed og kontrollere dens individuelle konfiguration af ASR-reglen.

:::image type="content" source="images/asrrulesnew.png" lightbox="images/asrrulesnew.png" alt-text="Skærmbilledet REGLER FOR ASR.":::

## <a name="microsoft-defender-for-endpoint---advanced-hunting"></a>Microsoft Defender til slutpunkt – Avanceret jagt

En af de mest effektive funktioner i Microsoft Defender til slutpunkt er avanceret jagt. Hvis du ikke er bekendt med avanceret jagt, kan du [proaktivt lede efter trusler med avanceret jagt](advanced-hunting-overview.md).

Avanceret jagt er et forespørgselsbaseret (Kusto-forespørgselssprog) værktøj til trusselssøgning, som giver dig mulighed for at udforske op til 30 dage af de registrerede (rå) data, som Defender til slutpunkt indsamler fra dine enheder. Ved hjælp af avanceret jagt kan du proaktivt undersøge begivenheder for at finde interessante indikatorer og enheder. Den fleksible adgang til data hjælper uoverensholdet med at lede efter både kendte og potentielle trusler.

Via avanceret jagt er det muligt at udtrække oplysninger om ASR-regler, oprette rapporter og få uddybende oplysninger om konteksten for en given asr-regelrevision eller blokere hændelse.

Der kan oprettes forespørgsler om ASR-regelhændelser fra tabellen DeviceEvents i afsnittet avanceret Microsoft 365 Defender. Eksempelvis kan en simpel forespørgsel som den nedenfor rapportere alle hændelser, der har ASR-regler som datakilde for de seneste 30 dage, og opsummere dem med ActionType-antallet, som i dette tilfælde vil være det faktiske kodenavn for ASR-reglen.

:::image type="content" source="images/adv-hunt-querynew.png" alt-text="Avanceret forespørgsel om en forespørgsel.":::

:::image type="content" source="images/adv-hunt-sc-2new.png" lightbox="images/adv-hunt-sc-2new.png" alt-text="avanceret jagtskærm.":::

Med avanceret jagt kan du forme forespørgslerne efter din smag, så du kan se, hvad der sker, uanset om du vil finde noget på en enkelt maskine, eller du vil udtrække viden fra hele miljøet.

## <a name="microsoft-defender-for-endpoint-machine-timeline"></a>Tidslinje for Microsoft Defender til slutpunktsmaskine

Et alternativ til avanceret jagt, men med et smallere omfang, er Tidslinjen i Microsoft Defender til slutpunktsmaskine. Du kan se alle de indsamlede begivenheder for en enhed i Microsoft 365 Defender for de seneste seks måneder ved at gå til listen Maskiner, vælge en bestemt maskine og derefter klikke på fanen Tidslinje.

Billedet nedenfor er et skærmbillede af Tidslinjevisningen af disse hændelser på et givet slutpunkt. Fra denne visning kan du filtrere listen over begivenheder baseret på en hvilken som helst begivenhedsgrupper langs ruden til højre. Du kan også aktivere eller deaktivere hændelser markeret med flag og detaljeret visning, mens du får vist beskeder og ruller gennem den historiske tidslinje.

:::image type="content" source="images/mic-sec-def-timelinenew.png" lightbox="images/mic-sec-def-timelinenew.png" alt-text="Microsoft 365 Defender tidslinje.":::

## <a name="how-to-troubleshoot-asr-rules"></a>Sådan foretager du fejlfinding af ASR-regler?

Den første og mest øjeblikkelige måde er at kontrollere lokalt på en Windows-enhed, hvilke asr-regler er aktiveret (og deres konfiguration) ved hjælp af PowerShell-cmdlet'er.

Her er et par andre kilder til oplysninger, Windows tilbyder, til fejlfinding af ASR-reglers virkning og drift.

### <a name="querying-which-rules-are-active"></a>Forespørgsel om, hvilke regler der er aktive

En af de nemmeste måder at afgøre, om ASR-regler allerede er aktiveret, er via en PowerShell-cmdlet, Get-MpPreference.

Her er et eksempel:

:::image type="content" source="images/getmpreferencescriptnew.png" lightbox="images/getmpreferencescriptnew.png" alt-text="hent mppreference-script.":::

Der er flere aktive ASR-regler med forskellige konfigurerede handlinger.

Hvis du vil udvide ovenstående oplysninger om ASR-regler, kan du bruge **egenskaberne AttackSurfaceReductionRules_Ids** /eller **AttackSurfaceReductionRules_Actions**.

Eksempel:

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Ids
```

:::image type="content" source="images/getmpref-examplenew.png" alt-text="få mpreference-eksempel.":::

Ovenstående viser alle de IDs for ASR-regler, der har en anden indstilling end 0 (ikke konfigureret).

Næste trin er derefter at få vist de faktiske handlinger (Bloker eller Overhold), som hver regel er konfigureret med.

```powershell
Get-MPPreference | Select-Object -ExpandProperty**AttackSurfaceReductionRules_Actions
```

:::image type="content" source="images/getmpref-example2new.png" alt-text="hent mppreference example2.":::

### <a name="querying-blocking-and-auditing-events"></a>Forespørgselsblokerings- og overvågningshændelser

Asr rule events can be viewed within the Windows Defender log.

Du får adgang til den ved Windows Logbog,  \> og gå til Program- og tjenestelogfiler **, som Microsoft** \> **Windows** \> **Windows Defender** \> **Drift.**

:::image type="content" source="images/eventviewerscrnew.png" lightbox="images/eventviewerscrnew.png" alt-text="hændelsesvisning scr.":::

## <a name="microsoft-defender-antimalware-protection-logs"></a>Microsoft Defender Antimalware Protection Logs

Du kan også få vist regelhændelser via Microsoft Defender Antivirus dedikerede kommandolinjeværktøj, `*mpcmdrun.exe*`kaldet , der kan bruges til at administrere og konfigurere og automatisere opgaver, hvis det er nødvendigt.

Du kan finde dette værktøj i *%ProgramFiles%\Windows Defender\MpCmdRun.exe*. Du skal køre den fra en kommandoprompt med administratorrettigheder (kør den som administrator).

Hvis du vil generere supportoplysningerne, skal *duMpCmdRun.exe -getfiles*. Efter et stykke tid pakkes flere logfiler i et arkiv (MpSupportFiles.cab) og gøres tilgængelige i *C:\ProgramData\Microsoft\Windows Defender\Support*.

:::image type="content" source="images/malware-prot-logsnew.png" alt-text="malwarebeskyttelseslogfiler.":::

Udtræk dette arkiv, og du har adgang til mange filer til fejlfindingsformål.

De mest relevante filer er som følger:

- **MPOperationalEvents.txt**: Denne fil indeholder samme niveau af oplysninger, der findes i Logbog Windows Defender i driftsloggen.
- **MPRegistry.txt**: I denne fil kan du analysere alle de aktuelle Windows Defender konfigurationer fra det tidspunkt, hvor supportlogfilerne blev registreret.
- **MPLog.txt**: Denne log indeholder flere detaljerede oplysninger om alle handlinger/handlinger for Windows Defender.
