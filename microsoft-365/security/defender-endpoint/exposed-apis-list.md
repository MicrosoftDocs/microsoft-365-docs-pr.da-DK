---
title: Understøttede Microsoft Defender for Endpoint API'er
ms.reviewer: ''
description: Få mere at vide om de specifikke understøttede Microsoft Defender for Endpoint objekter, hvor du kan oprette API-kald til.
keywords: apis, understøttede API'er, agent, beskeder, enhed, bruger, domæne, ip, fil, avancerede forespørgsler, avanceret jagt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fe43d4df71b0801ae89149797068873577c77c38
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174675"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>Understøttede Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> Avancerede jagtegenskaber er ikke inkluderet i Defender for Business. Se [Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>Slutpunkts-URI og versionsstyring

### <a name="endpoint-uri"></a>URI for slutpunkt

> URI'en for tjenestebasen er: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> De forespørgsler, der er baseret på OData, har præfikset '/api'. Hvis du f.eks. vil have beskeder, kan du sende GET-anmodning til [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Versionering

> API'en understøtter versionering.
>
> Den aktuelle version er **V1.0**.
>
> Hvis du vil bruge en bestemt version, skal du bruge dette format: `https://api.securitycenter.microsoft.com/api/{Version}`. For eksempel: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Hvis du ikke angiver en version (f.eks. `https://api.securitycenter.microsoft.com/api/alerts`), får du den nyeste version.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Få mere at vide om de individuelle understøttede enheder, hvor du kan køre API-kald til og detaljer, f.eks. HTTP-anmodningsværdier, anmodningsheadere og forventede svar.

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
:---|:---
[Avanceret jagt](run-advanced-query-api.md) | Kør forespørgsler fra API.<p>*Avancerede jagtegenskaber er ikke inkluderet i [Defender for Business](../defender-business/mdb-overview.md)*.
[Metoder og egenskaber for beskeder](alerts.md)  | Kør API-kald, f.eks \- . få beskeder, opret besked, opdater besked m.m.
[Eksportér vurderingsmetoder og -egenskaber pr. enhed](get-assessment-methods-properties.md) | Kør API-kald for at indsamle sårbarhedsvurderinger pr. enhed, f.eks.: \- eksport af sikker konfigurationsvurdering, vurdering af softwarelager, vurdering af sårbarheder i forbindelse med eksport af software og vurdering af sårbarheder ved deltaeksport af software.
[Metoder og egenskaber til automatiseret undersøgelse](investigation.md) | Kør API-kald, f.eks \- . hent samlingen af Investigation.
[Få domænerelaterede beskeder](get-domain-related-alerts.md) | Kør API-kald, f.eks \- . hent domænerelaterede enheder, domænestatistik m.m.
[Filmetoder og -egenskaber](files.md) | Kør API-kald, f.eks \- . hent filoplysninger, filrelaterede beskeder, filrelaterede enheder og filstatistik.
[Metoder og egenskaber for indikatorer](ti-indicator.md) | Kør API-kald, f.eks \- . hent indikatorer, opret indikator, og slet indikatorer.
[Få IP-relaterede beskeder](get-ip-related-alerts.md) | Kør API-kald, f.eks \- . hent IP-relaterede beskeder, og hent IP-statistikker.
[Metoder og egenskaber for maskiner](machine.md) | Kør API-kald, f.eks \- . hent enheder, hent enheder efter id, oplysninger om brugere, der er logget på, rediger mærker og meget mere.
[Metoder og egenskaber for maskinhandling](machineaction.md) | Kør API-kald, f.eks \- . Isolation, Kør antivirusscanning og meget mere.
[Metoder og egenskaber for anbefaling](recommendation.md) | Kør API-kald, f.eks \- . hent anbefalinger efter id.
[Metoder og -egenskaber for afhjælpningsaktivitet](get-remediation-methods-properties.md) | Kør API-kald, f.eks \- . hent alle afhjælpningsopgaver, hent de viste enheders afhjælpningsopgave, og hent én afhjælpningsopgave efter id.
[Scoremetoder og -egenskaber](score.md) | Kør API-kald, f.eks \- . få eksponeringsscore eller få en sikker score for enheden.
[Softwaremetoder og -egenskaber](software.md) | Kør API-kald, f.eks \- . sikkerhedsrisici for lister af software.
[Brugermetoder](user.md) | Kør API-kald, f.eks \- . hent brugerrelaterede beskeder og brugerrelaterede enheder.
[Metoder og egenskaber for sikkerhedsrisici](vulnerability.md) | Kør API-kald, f.eks \- . listeenheder efter sårbarhed.

## <a name="see-also"></a>Se også

- [Microsoft Defender for Endpoint API'er](apis-intro.md)

- [produktbemærkninger til Microsoft Defender for Endpoint API](api-release-notes.md)
