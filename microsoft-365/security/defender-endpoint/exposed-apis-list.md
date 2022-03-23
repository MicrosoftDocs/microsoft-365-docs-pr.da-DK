---
title: Understøttede Microsoft Defender til slutpunkts-API'er
ms.reviewer: ''
description: Få mere at vide om de specifikke understøttede enheder for Microsoft Defender til slutpunkter, hvor du kan oprette API-opkald.
keywords: apis, understøttede api'er, agent, beskeder, enhed, bruger, domæne, ip, fil, avancerede forespørgsler, avanceret jagt
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
ms.openlocfilehash: 94c5698845f556936373ee4548d9aa137f03867b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592060"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>Understøttede Microsoft Defender til slutpunkts-API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>Slutpunkts-URI og versionskontrol

### <a name="endpoint-uri"></a>Slutpunkts-URI

> URI'en for tjenestebase er: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> De forespørgsler, der er baseret på OData, har præfikset '/api'. Hvis du f.eks. vil have beskeder, kan du sende GET-anmodning til [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Versionsversioner

> API'en understøtter versionsversioner.
>
> Den aktuelle version er **V1.0**.
>
> Hvis du vil bruge en bestemt version, skal du bruge dette format: `https://api.securitycenter.microsoft.com/api/{Version}`. For eksempel: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Hvis du ikke angiver nogen version (f.eks. `https://api.securitycenter.microsoft.com/api/alerts`) får du den nyeste version.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Få mere at vide om de enkelte understøttede enheder, hvor du kan køre API-opkald og oplysninger som f.eks. HTTP-anmodningsværdier, anmode om overskrifter og forventede svar.

## <a name="in-this-section"></a>I dette afsnit

Emne | Beskrivelse
:---|:---
[Avanceret jagt](run-advanced-query-api.md) | Kør forespørgsler fra API.
[Beskedmetoder og -egenskaber](alerts.md) | Kør API-opkald, f.eks \- . få beskeder, opret besked, opdater besked og meget mere.
[Eksportere vurderingsmetoder og egenskaber pr. enhed](get-assessment-methods-properties.md) | Kør API-opkald for at indsamle sårbarhedsvurderinger på pr. enhed, f.eks.: \- eksport af sikker konfigurationsvurdering, vurdering af eksport af softwarelager, vurdering af softwarerisici og vurdering af softwarerisici i deltaeksport.
[Metoder og egenskaber for automatiseret undersøgelse](investigation.md) | Kør API-opkald, f.eks \- . indsamling af undersøgelse.
[Få domænerelaterede beskeder](get-domain-related-alerts.md) | Kør API-opkald, f.eks \- . hent domænerelaterede enheder, domænestatistik og meget mere.
[Filmetoder og -egenskaber](files.md) | Kør API-opkald, f.eks \- . hent filoplysninger, filrelaterede beskeder, filrelaterede enheder og filstatistik.
[Indikatorers metoder og egenskaber](ti-indicator.md) | Kør API-opkald, f.eks \- . Hent indikatorer, opret Indikator, og slet Indikatorer.
[Få IP-relaterede beskeder](get-ip-related-alerts.md) | Kør API-opkald, f.eks \- . få IP-relaterede beskeder, og få IP-statistik.
[Maskinmetoder og -egenskaber](machine.md) | Kør API-opkald, f.eks \- . hent enheder, få enheder efter id, oplysninger om brugere, der er logget på, rediger mærker og meget mere.
[Maskinhandlingsmetoder og -egenskaber](machineaction.md) | Kør API-opkald som f.eks \- Isolation, Kør antivirus-scanning og meget mere.
[Anbefalingsmetoder og -egenskaber](recommendation.md) | Kør API-opkald, f.eks. \- få en anbefaling efter id.
[Afhjælpning af aktivitetsmetoder og -egenskaber](get-remediation-methods-properties.md) | Kør API-opkald, f.eks \- . få alle afhjælpningsopgaver, få vist afhjælpningsopgave for enheder, og få én afhjælpningsopgave med id.
[Scoremetoder og -egenskaber](score.md) | Kør API-opkald, f.eks \- . få eksponeringsscore eller få en sikker enhedsscore.
[Softwaremetoder og -egenskaber](software.md) | Kør API-opkald, f.eks. \- liste over sårbarheder efter software.
[Brugermetoder](user.md) | Kør API-opkald, \- f.eks. få brugerrelaterede beskeder og brugerrelaterede enheder.
[Sikkerhedsrisikometoder og -egenskaber](vulnerability.md) | Kør API-opkald, f.eks \- . liste over enheder af sikkerhedsrisiko.

## <a name="see-also"></a>Se også

- [Microsoft Defender til endpoint-API'er](apis-intro.md)

- [Produktbemærkninger til Microsoft Defender til Endpoint API](api-release-notes.md)
