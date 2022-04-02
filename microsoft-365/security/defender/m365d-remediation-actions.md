---
title: Afhjælpningshandlinger i Microsoft 365 Defender
description: Få et overblik over afhjælpningshandlinger, der følger automatiserede undersøgelser i Microsoft 365 Defender
keywords: automatiseret, undersøgelse, besked, udløser, handling, afhjælpning
search.appverid: met150
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
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: c922213a262fdc9c61d6f79d0205e6ead96fd44a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63603110"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Afhjælpningshandlinger i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Under og efter en automatiseret undersøgelse af Microsoft 365 Defender identificeres afhjælpningshandlinger for skadelige eller mistænkelige elementer. Visse typer afhjælpningshandlinger bliver taget på enheder, også kaldet slutpunkter. Andre afhjælpningshandlinger, der er foretaget i forbindelse med mailindhold. Automatiserede undersøgelser er fuldført, efter afhjælpningshandlinger er blevet udført, godkendt eller afvist.

> [!IMPORTANT]
> Om afhjælpningshandlingerne skal løses automatisk eller kun efter godkendelse afhænger af bestemte indstillinger, f.eks. hvordan automatiseringsniveauer. Du kan få mere at vide i følgende artikler:
> - [Konfigurer dine automatiserede undersøgelses- og svarfunktioner Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Sådan afhjælpes trusler på enheder](../defender-endpoint/automated-investigations.md)
> - [Trusler og afhjælpningshandlinger i forbindelse med mail & samarbejdsindhold](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

Følgende tabel opsummerer afhjælpningshandlinger, der aktuelt understøttes i Microsoft 365 Defender. 

|Afhjælpningshandlinger for enhed (slutpunkt)  |Afhjælpningshandlinger for mail  |
|:---------|:---------|
|- Pakke til samlet undersøgelse <br/>- Isoler enhed (denne handling kan fortrydes)<br/>- Offboard-maskine <br/>- Udførelse af udgivelse af kode <br/>- Frigiv fra karantæne <br/>- Anmod om et eksempel <br/>- Begræns udførelse af kode (denne handling kan fortrydes) <br/>- Kør antivirus-scanning <br/>- Stop og karantæne      |- Bloker URL-adresse (kliktid)<br/>- Blød sletning af mails eller klynger<br/>- Karantæne af mail<br/>- Sætte en vedhæftet fil i karantæne<br/>- Deaktivere ekstern videresendelse af mail          |

Afhjælpningshandlinger, uanset om de afventer godkendelse eller allerede er fuldført, kan vises i [Handlingscenter](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>Afhjælpningshandlinger, der følger automatiserede undersøgelser

Når en automatiseret undersøgelse er afsluttet, opnås der en konklusion for hvert eneste involverede beviser. Afhængigt af konklusionen identificeres afhjælpningshandlinger. I nogle tilfælde løses afhjælpningshandlinger automatisk. I andre tilfælde kan afhjælpningshandlinger afventer godkendelse. Det hele afhænger af, [hvordan automatiseret undersøgelse og svar er konfigureret](m365d-configure-auto-investigation-response.md).

I følgende tabel vises mulige konklusioner og resultater:

| Konklusion    | Påvirkede enheder    | Resultater|
|------|------|------|
| Ondsindet    | Enheder (slutpunkter)    | Afhjælpningshandlingerne løses automatisk (hvis din organisations [enhedsgrupper](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) er indstillet **til Fuld – afhjulpet trusler automatisk**)|
| Ondsindet    | Mailindhold (URL-adresser eller vedhæftede filer) | Anbefalede afhjælpningshandlinger afventer godkendelse|
| Mistænkelig    | Enheder eller mailindhold | Anbefalede afhjælpningshandlinger afventer godkendelse|
| Der blev ikke fundet nogen trusler    | Enheder eller mailindhold    | Der kræves ingen afhjælpningshandlinger|


## <a name="remediation-actions-that-are-taken-manually"></a>Afhjælpningshandlinger, der er taget manuelt

Ud over afhjælpningshandlinger, der følger automatiserede undersøgelser, kan dit sikkerhedsteam foretage visse afhjælpningshandlinger manuelt. Disse omfatter følgende:

- Manuel enhedshandling, f.eks. enhedsisolation eller filkarantæne
- Manuel mailhandling, f.eks. blød sletning af mails 
- [Avanceret jagthandling](../defender-endpoint/advanced-hunting-overview.md) på enheder eller mail
- [Stifinder-handling](../office-365-security/threat-explorer.md) på mailindhold, f.eks. flytning af mails til uønsket mail, blød sletning af mail eller hård sletning af mail
- Manuel [live response-handling](/windows/security/threat-protection/microsoft-defender-atp/live-response) , f.eks. sletning af en fil, stop en proces og fjernelse af en planlagt opgave
- Live svarhandling med [Microsoft Defender til slutpunkt-API'er](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis), f.eks. at isolere en enhed, køre en antivirusscanning og få oplysninger om en fil

## <a name="next-steps"></a>Næste trin

- [Gå til handlingscenter](m365d-action-center.md)
- [Få vist og administrer afhjælpningshandlinger](m365d-autoir-actions.md)
- [Adressere falske positive eller falske negativer](m365d-autoir-report-false-positives-negatives.md)
