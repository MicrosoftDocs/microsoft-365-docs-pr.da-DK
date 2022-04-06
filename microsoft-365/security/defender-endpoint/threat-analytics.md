---
title: Spor og svar på nye trusler med Microsoft Defender for Endpoint trusselsanalyse
ms.reviewer: ''
description: Forstå fremspirende trusler og angrebsteknikker, og hvordan du stopper dem. Vurder deres indvirkning på din organisation, og vurder din organisatoriske fleksibilitet.
keywords: trusselsanalyse, risikoevaluering, afhjælpning af operativsystemet, afhjælpning af mikrokoder, status for afhjælpning
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0ca4aea3281d6bb375e7b5ff5223cb40e9a980ac
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471071"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Spore og reagere på nye trusler via trusselsanalyse

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Med mere avancerede adversar og nye trusler, der opstår ofte og med stor grad, er det vigtigt at kunne hurtigt:

- Vurder effekten af nye trusler
- Gennemgå din fleksibilitet over for eller eksponering for truslerne
- Identificer de handlinger, du kan udføre for at stoppe eller indeholde truslerne

Trusselsanalyse er en række rapporter fra erfarne Microsoft-sikkerhedseksperter, som dækker de mest relevante trusler, herunder:

- Aktive trusler og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sårbarheder
- Almindelige angrebsoverflader
- Mest udbredte malware

Hver rapport indeholder en detaljeret analyse af en trussel og omfattende vejledning til, hvordan du kan beskytte dig mod denne trussel. Den indeholder også data fra dit netværk, der angiver, om trussel er aktiv, og om du har gældende beskyttelse på plads.

Se denne korte video for at få mere at vide om, hvordan trusselsanalyse kan hjælpe dig med at spore de seneste trusler og stoppe dem.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="view-the-threat-analytics-dashboard"></a>Få vist dashboardet for trusselsanalyse

Dashboardet Trusselsanalyse er et godt udgangspunkt for at få adgang til de rapporter, der er mest relevante for din organisation. Den opsummerer truslerne i følgende afsnit:

- **Seneste trusler**: Viser de senest publicerede trusselsrapporter samt antallet af enheder med aktive og løste beskeder.
- **Trusler med høj effekt**: Viser de trusler, der har haft størst indvirkning på organisationen. Dette afsnit rangerer trusler efter antallet af enheder, der har aktive beskeder.
- **Trusselsoversigt**: Viser den overordnede effekt af registrerede trusler ved at vise antallet af trusler med aktive og løste beskeder.

Vælg en trussel fra dashboardet for at få vist rapporten for den pågældende trussel.

:::image type="content" source="images/ta_dashboard.png" alt-text="Dashboardet Trusselsanalyse" lightbox="images/ta_dashboard.png":::

## <a name="view-a-threat-analytics-report"></a>Få vist en rapport over trusselsanalyse

Hver trusselsanalyserapport indeholder oplysninger i tre **sektioner: Oversigt**, **Analytikerrapport** og **Afhjælpninger**.

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Oversigt: Forstå hurtigt truslen, vurder dens virkning, og gennemse forsvar

Afsnittet **Oversigt** giver et eksempel på den detaljerede analytikerrapport. Den indeholder også diagrammer, der fremhæver virkningen af trussel mod din organisation og din eksponering via forkert konfigurerede og ikke-kompatible enheder.

:::image type="content" source="images/ta-overview.png" alt-text="Afsnittet Oversigt i en rapport over trusselsanalyse" lightbox="images/ta-overview.png":::
_Afsnittet Oversigt i en rapport over trusselsanalyse_

#### <a name="assess-the-impact-to-your-organization"></a>Vurder påvirkningen af din organisation

Hver rapport indeholder diagrammer, der er udviklet til at give oplysninger om den organisatoriske indvirkning af en trussel:

- **Enheder med beskeder**: Viser det aktuelle antal forskellige enheder, der er blevet påvirket af truslen. En enhed kategoriseres som Aktiv, hvis der er mindst én besked knyttet til den pågældende trussel,  og Løst, hvis alle beskeder, der er knyttet til truslerne på enheden, er blevet løst.
- **Enheder med beskeder over tid**: Viser antallet af forskellige enheder med **aktive** og **løste** beskeder over tid. Antallet af løste beskeder angiver, hvor hurtigt organisationen reagerer på beskeder, der er knyttet til en trussel. Ideelt set bør diagrammet vise påmindelser, der er blevet løst inden for et par dage.

#### <a name="review-security-resilience-and-posture"></a>Gennemgå sikkerhedsrobusthed og -efterseelse

Hver rapport indeholder diagrammer, der giver et overblik over, hvor robust din organisation er over for en given trussel:

- **Status for sikkerhedskonfiguration**: Viser antallet af enheder, der har anvendt de anbefalede sikkerhedsindstillinger, som kan hjælpe med at reducere truslerne. Enheder betragtes som **sikre** , hvis de har _anvendt_ alle de registrerede indstillinger.
- **Status for fejlrettelse af** sikkerhedsrisiko: Viser antallet af enheder, der har anvendt sikkerhedsopdateringer eller rettelser, der adresserer sårbarheder, som udnyttes af truslen.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analytikerrapport: Få ekspertindsigt fra Microsoft-sikkerhedseksperter

Gå til sektionen **med analytikerrapporten** for at læse opskrivning af den detaljerede ekspert. De fleste rapporter giver detaljerede beskrivelser af angrebskæder, herunder taktikker og teknikker, der er knyttet til MITRE ATT&CK-rammen, udtømmende lister med anbefalinger og effektiv trusselssøgningsvejledning[.](advanced-hunting-overview.md)

[Få mere at vide om analytikerrapporten](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Afhjælpninger: Gennemgå en liste over afhjælpninger og status for dine enheder

I afsnittet **Afhjælpninger** skal du gennemgå listen over specifikke anbefalinger, der kan handles på, som kan hjælpe dig med at øge din organisatoriske fleksibilitet over for truslerne. Listen over registrerede afhjælpninger omfatter:

- **Sikkerhedsopdateringer**: Installation af sikkerhedsopdateringer eller rettelser til sårbarheder
- **Microsoft Defender Antivirus indstillinger**
  - Security intelligence-version
  - Cloud-leveret beskyttelse
  - Potentielt uønsket programbeskyttelse (PUA)
  - Beskyttelse i realtid

Oplysninger om afhjælpning i dette afsnit indeholder data [fra Håndtering af trusler og sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md), som også indeholder detaljerede oplysninger om afhjælpning fra forskellige links i rapporten.

:::image type="content" source="images/ta-mitigations.png" alt-text="Afsnittet afhjælpninger i en rapport over trusselsanalyse" lightbox="images/ta-mitigations.png":::


_Afsnittet afhjælpninger i en rapport over trusselsanalyse_

## <a name="additional-report-details-and-limitations"></a>Yderligere rapportdetaljer og -begrænsninger

Når du bruger rapporterne, skal du huske på følgende:

- Dataenes omfang er baseret på dit rollebaserede adgangskontrolområde (RBAC). Du får vist status for enheder i grupper [, som du kan få adgang til](machine-groups.md).
- Diagrammer afspejler kun afhjælpninger, der registreres. Se rapportoversigten for yderligere afhjælpninger, der ikke vises i diagrammerne.
- Afhjælpninger garanterer ikke fuldstændig fleksibilitet. Afhjælpningerne afspejler de bedst mulige foranstaltninger, der er nødvendige for at forbedre fleksibiliteten.
- Enheder tælles som "utilgængelige", hvis de ikke har overført data til tjenesten.
- Antivirusrelaterede statistikker er baseret på Microsoft Defender Antivirus indstillinger. Enheder med antivirusløsninger fra tredjepart kan vises som "eksponerede".

## <a name="related-topics"></a>Relaterede emner

- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Forstå sektionen for analytikerrapporten](threat-analytics-analyst-reports.md)
- [Vurder og løs sikkerhedsforanstaltninger og eksponeringer](next-gen-threat-and-vuln-mgt.md)
