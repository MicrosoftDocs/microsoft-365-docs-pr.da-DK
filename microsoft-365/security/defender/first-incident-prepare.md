---
title: Forbered din sikkerhedsholdning til din første hændelse
description: Konfigurer din Microsoft 365-lejers sikkerhedsholdning for din første hændelse i Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 690e1c48a452cfa00f0ae8d4fd87849b1c2e79dc
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893513"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>Forbered din sikkerhedsholdning til din første hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Forberedelse til håndtering af hændelser omfatter konfiguration af tilstrækkelig beskyttelse af en organisations netværk mod forskellige typer sikkerhedshændelser. For at reducere risikoen for sikkerhedshændelser anbefaler NIST (National Institute of Standards and Technology) flere sikkerhedspraksisser, herunder risikovurderinger, hærdning af værtssikkerhed, konfiguration af netværk sikkert og forebyggelse af malware.

Microsoft 365 Defender kan hjælpe med at håndtere flere aspekter af forebyggelse af hændelser:

- Implementering af en [Nul tillid](/security/zero-trust/) ramme
- Fastlæggelse af din sikkerhedsholdning ved at tildele en score med [Microsoft Secure Score](microsoft-secure-score.md)
- Forebyggelse af trusler via sårbarhedsvurderinger i [administration af trusler og sårbarheder](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Forstå de nyeste sikkerhedstrusler, så du kan forberede dig på dem med [trusselsanalyser](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>Trin 1. Implementer Nul tillid

[Nul tillid](/security/zero-trust/) er en integreret sikkerhedsfilosofi og en samlet strategi, der tager højde for alle moderne miljøers komplekse karakter, herunder mobilarbejdsstyrken og brugerne, enheder, programmer og data, uanset hvor de befinder sig. Ved at levere en enkelt glasrude til at administrere alle registreringer på en ensartet måde kan Microsoft 365 Defender gøre det nemmere for dit sikkerhedsteam at implementere de [ledende principper](/security/zero-trust/#guiding-principles-of-zero-trust) for Nul tillid.

Komponenter i Microsoft 365 Defender kan vise overtrædelser af regler, der er implementeret for at oprette politikker for betinget adgang til Nul tillid ved at integrere data fra Microsoft Defender for Endpoint  eller andre leverandører af mobilsikkerhed som en informationskilde for politikker for enhedens overholdelse af angivne standarder og implementering af enhedsbaserede politikker for betinget adgang.

Enhedsrisikoen påvirker direkte, hvilke ressourcer brugeren af den pågældende enhed har adgang til. Nægtelse af adgang til ressourcer, der er baseret på bestemte kriterier, er hovedtemaet for Nul tillid, og Microsoft 365 Defender indeholder oplysninger, der er nødvendige for at bestemme kriterierne på tillidsniveau. Microsoft 365 Defender kan f.eks. levere softwareversionsniveauet for en enhed via siden Administration af trusler og sårbarheder, mens politikker for betinget adgang begrænser enheder, der har forældede eller sårbare versioner.

Automatisering er en vigtig del af implementeringen og vedligeholdelsen af et Nul tillid miljø, samtidig med at antallet af beskeder, der potentielt kan føre til hændelser med svar på hændelser med hændelsessvar , reduceres. Komponenter i Microsoft 365 Defender kan automatiseres, f.eks. [afhjælpningshandlinger](m365d-autoir.md) (kendt som undersøgelser af en hændelse på Microsoft 365 Defender portalen), meddelelseshandlinger og endda oprettelse af supportanmodninger, f.eks. i [ServiceNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>Trin 2. Bestem organisationens sikkerhedsholdning

Organisationer kan derefter bruge [Microsoft Secure Score](microsoft-secure-score.md) i Microsoft 365 Defender til at bestemme din aktuelle sikkerhedsholdning og overveje anbefalinger til, hvordan de kan forbedre den. Jo højere scoren er, jo flere sikkerhedsanbefalinger og forbedringshandlinger har organisationen taget. Secure Score-anbefalinger kan tages på tværs af forskellige produkter og give organisationer mulighed for at hæve deres scorer endnu højere.

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="Siden Microsoft Secure Score på portalen Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::

## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>Trin 3. Vurder din organisations sårbarhedseksponering

Forebyggelse af hændelser kan hjælpe med at strømline indsatsen for sikkerhedshandlinger for at fokusere på igangværende kritiske og vigtige sikkerhedshændelser. Softwaresårbarheder er ofte et forhindreligt indgangspunkt for angreb, der kan føre til datatyveri, datatab eller afbrydelse af forretningshandlinger. Hvis ingen angreb er i gang, skal sikkerhedshandlinger stræbe efter at opnå og opretholde et acceptabelt niveau af [sårbarhedseksponering](../defender-endpoint/tvm-exposure-score.md) i deres organisation.

Hvis du vil kontrollere statussen for din softwarerettelse, skal du gå til siden [Administration af trusler og sårbarheder](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) i Defender for Endpoint, som du kan få adgang til fra Microsoft 365 Defender via fanen **Flere ressourcer**.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="Siden Trussel og sårbarhed på portalen Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png":::

## <a name="4-understand-emerging-threats"></a>4. Forstå nye trusler

Brug [trusselsanalyser](threat-analytics.md) på Microsoft 365 Defender-portalen for at holde dig ajour med det aktuelle sikkerhedstrusselslandskab. Microsofts sikkerhedsforskere, der er eksperter i sikkerhed, opretter rapporter, der beskriver de nyeste cybertrusler i detaljer, så du kan forstå, hvordan de kan påvirke dit Microsoft 365-abonnement, dine enheder og dine brugere. Disse rapporter kan omfatte:

- Aktive trusselsaktører og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sikkerhedsrisici
- Almindelige angrebsoverflader
- Udbredt malware

Trusselsanalyse ser også på din konfiguration og dine beskeder for at finde ud af, hvor udsatte du er, og om der er aktive beskeder, der gælder for en rapport.

Du kan implementere anbefalingerne fra en spirende trussel for at styrke din sikkerhedsholdning og minimere dit angrebsområde.

Tag dig tid til din tidsplan, så du regelmæssigt kan se sektionen [Threat Analytics](threat-analytics.md) på Microsoft 365 Defender-portalen. Se [eksemplet på sikkerhedshandlinger for Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender) for at få flere oplysninger.

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan [du kan triage og analysere hændelser](first-incident-analyze.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
