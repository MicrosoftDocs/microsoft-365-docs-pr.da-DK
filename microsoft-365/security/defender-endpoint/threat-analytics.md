---
title: Spor og reager på nye trusler med Microsoft Defender for Endpoint trusselsanalyse
ms.reviewer: ''
description: Forstå nye trusler og angrebsteknikker, og hvordan du kan stoppe dem. Vurder deres indvirkning på din organisation, og evaluer din organisations robusthed.
keywords: trusselsanalyse, risikoevaluering, OS-afhjælpning, mikrokodemitigering, afhjælpningsstatus
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
ms.openlocfilehash: 455b80f590edf255362c7bb047c7aa1b23916666
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128560"
---
# <a name="track-and-respond-to-emerging-threats-through-threat-analytics"></a>Spor og reager på nye trusler via trusselsanalyser

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Med mere avancerede modstandere og nye trusler, der dukker op ofte og udbredt, er det vigtigt at kunne hurtigt:

- Vurder virkningen af nye trusler
- Gennemse din robusthed mod eller eksponering for truslerne
- Identificer de handlinger, du kan udføre for at stoppe eller indeholde truslerne

Trusselsanalyse er en række rapporter fra ekspertforskere inden for Sikkerhed i Microsoft, der dækker de mest relevante trusler, herunder:

- Aktive trusselsaktører og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sikkerhedsrisici
- Almindelige angrebsoverflader
- Udbredt malware

Hver betænkning indeholder en detaljeret analyse af en trussel og en omfattende vejledning i, hvordan man kan forsvare sig mod denne trussel. Den indeholder også data fra dit netværk, der angiver, om truslen er aktiv, og om du har gældende beskyttelse på plads.

Se denne korte video for at få mere at vide om, hvordan trusselsanalyser kan hjælpe dig med at spore de nyeste trusler og stoppe dem.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bw1f]

## <a name="required-roles-and-permissions"></a>Påkrævede roller og tilladelser
I følgende tabel beskrives de roller og tilladelser, der kræves for at få adgang til Threat Analytics. Roller, der er defineret i nedenstående tabel, refererer til brugerdefinerede roller på individuelle portaler og er ikke forbundet med globale roller i Azure AD, selvom de har samme navn.

| **En af følgende roller er påkrævet for Microsoft 365 Defender**  | **En af følgende roller er påkrævet for Defender for Endpoint**  | **En af følgende roller er påkrævet for Defender for Office 365** | **En af følgende roller er påkrævet for Defender for Cloud Apps** | 
|---------|---------|---------|---------|
| Threat Analytics | Beskeder og hændelsesdata: <ul><li>Få vist data – sikkerhedshandlinger</li></ul>TVM-afhjælpninger:<ul><li>Få vist data – trussel og håndtering af sikkerhedsrisici</li></ul> | Beskeder og hændelsesdata:<ul> <li>Administrer kun visningsbeskeder</li> <li>Administrer beskeder</li> <li>Organisationskonfiguration</li><li>Overvågningslogge</li> <li>Overvågningslogge kun for visning</li><li>Sikkerhedslæser</li> <li>Sikkerhedsadministrator</li><li>Kun visningsmodtagere</li> </ul> Forhindrede mailforsøg: <ul><li>Sikkerhedslæser</li> <li>Sikkerhedsadministrator</li><li>Kun visningsmodtagere</li> | Ikke tilgængelig for Defender for Cloud Apps- eller MDI-brugere |

## <a name="view-the-threat-analytics-dashboard"></a>Få vist dashboardet til trusselsanalyse

Dashboardet til trusselsanalyse er et fantastisk udgangspunkt for at få vist de rapporter, der er mest relevante for din organisation. Den opsummerer truslerne i følgende afsnit:

- **Seneste trusler**: Viser de senest publicerede trusselsrapporter sammen med antallet af enheder med aktive og løste beskeder.
- **Trusler med stor indvirkning**: Viser de trusler, der har haft den største indvirkning på organisationen. I dette afsnit rangordnes trusler efter antallet af enheder, der har aktive beskeder.
- **Trusselsoversigt**: Viser den samlede indvirkning af sporede trusler ved at vise antallet af trusler med aktive og løste beskeder.

Vælg en trussel fra dashboardet for at få vist rapporten for den pågældende trussel.

:::image type="content" source="images/ta_dashboard.png" alt-text="Dashboardet til trusselsanalyse" lightbox="images/ta_dashboard.png":::

## <a name="view-a-threat-analytics-report"></a>Få vist en rapport over trusselsanalyse

Hver rapport til trusselsanalyse indeholder oplysninger i tre afsnit: **Oversigt**, **Analytikerrapport** og **Afhjælpninger**.

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Oversigt: Forstå hurtigt truslen, vurder dens virkning og gennemgå forsvar

Afsnittet **Oversigt** indeholder et eksempel på den detaljerede analytikerrapport. Den indeholder også diagrammer, der fremhæver virkningen af truslen mod din organisation og din eksponering via forkert konfigurerede og ikke-kompatible enheder.

:::image type="content" source="images/ta-overview.png" alt-text="Afsnittet Oversigt i en rapport til trusselsanalyse" lightbox="images/ta-overview.png":::
_Oversigtssektion i en rapport til trusselsanalyse_

#### <a name="assess-the-impact-to-your-organization"></a>Vurder indvirkningen på din organisation

Hver rapport indeholder diagrammer, der er designet til at give oplysninger om en trussels organisatoriske indvirkning:

- **Enheder med beskeder**: Viser det aktuelle antal forskellige enheder, der er blevet påvirket af truslen. En enhed er kategoriseret som **Aktiv** , hvis der er mindst én besked knyttet til denne trussel og **Løst** , hvis *alle* beskeder, der er knyttet til truslen på enheden, er blevet løst.
- **Enheder med beskeder over tid**: Viser antallet af forskellige enheder med **aktive** og **løste** beskeder over tid. Antallet af løste beskeder angiver, hvor hurtigt din organisation reagerer på beskeder, der er knyttet til en trussel. Ideelt set skal diagrammet vise beskeder, der er løst inden for nogle få dage.

#### <a name="review-security-resilience-and-posture"></a>Gennemse robusthed og arbejdsholdning for sikkerhed

Hver rapport indeholder diagrammer, der giver et overblik over, hvor modstandsdygtig din organisation er mod en given trussel:

- **Status for sikkerhedskonfiguration**: Viser antallet af enheder, der har anvendt de anbefalede sikkerhedsindstillinger, som kan hjælpe med at afhjælpe truslen. Enheder betragtes som **sikre** , hvis de har anvendt _alle_ de sporede indstillinger.
- **Status for programrettelse af sårbarheder**: Viser antallet af enheder, der har anvendt sikkerhedsopdateringer eller programrettelser, der løser sårbarheder, der udnyttes af truslen.

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analytikerrapport: Få ekspertindsigt fra Microsofts sikkerhedsforskere

Gå til afsnittet **Analytikerrapport** for at læse den detaljerede ekspertudskrivning. De fleste rapporter indeholder detaljerede beskrivelser af angrebskæder, herunder taktikker og teknikker, der er knyttet til MITRE ATT-&CK-strukturen, udtømmende lister over anbefalinger og effektiv vejledning [til trusselsjagt](advanced-hunting-overview.md) .

[Få mere at vide om analytikerrapporten](threat-analytics-analyst-reports.md)

### <a name="mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Afhjælpninger: Gennemse listen over afhjælpninger og status for dine enheder

I afsnittet **Afhjælpninger** skal du gennemse listen over specifikke anbefalinger, der kan handles på, som kan hjælpe dig med at øge din organisations robusthed mod truslen. Listen over sporede afhjælpninger omfatter:

- **Sikkerhedsopdateringer**: Installation af sikkerhedsopdateringer eller programrettelser for sikkerhedsrisici
- **indstillinger for Microsoft Defender Antivirus**
  - Version af Sikkerhedsintelligens
  - Skybaseret beskyttelse
  - Potentielt uønsket programbeskyttelse (PUA)
  - Beskyttelse i realtid

Afhjælpningsoplysninger i dette afsnit omfatter data fra [Håndtering af trusler og sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md), som også indeholder detaljerede oplysninger om detailudledning fra forskellige links i rapporten.

:::image type="content" source="images/ta-mitigations.png" alt-text="Afsnittet Afhjælpninger i en rapport over trusselsanalyse" lightbox="images/ta-mitigations.png":::


_Afsnittet Afhjælpninger i en rapport over trusselsanalyse_

## <a name="additional-report-details-and-limitations"></a>Yderligere rapportoplysninger og -begrænsninger

Når du bruger rapporterne, skal du være opmærksom på følgende:

- Data er beregnet på baggrund af dit rollebaserede adgangskontrolområde (RBAC). Du får vist status for enheder i [grupper, som du har adgang til](machine-groups.md).
- Diagrammer afspejler kun afhjælpninger, der spores. Se rapportens oversigt for yderligere afhjælpninger, der ikke vises i diagrammerne.
- Afhjælpninger garanterer ikke fuldstændig robusthed. De angivne afhjælpninger afspejler de bedst mulige handlinger, der er nødvendige for at forbedre robusthed.
- Enheder tælles som "utilgængelige", hvis de ikke har overført data til tjenesten.
- Antivirusrelaterede statistikker er baseret på Microsoft Defender Antivirus indstillinger. Enheder med antivirusløsninger fra tredjepart kan vises som "eksponeret".

## <a name="related-topics"></a>Relaterede emner

- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Forstå afsnittet om analytikerrapport](threat-analytics-analyst-reports.md)
- [Vurder og løs sikkerhedsmæssige svagheder og eksponeringer](next-gen-threat-and-vuln-mgt.md)
