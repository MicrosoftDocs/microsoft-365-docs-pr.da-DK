---
title: Afhjælpningshandlinger i Microsoft 365 Defender
description: Få en oversigt over afhjælpningshandlinger, der følger automatiserede undersøgelser i Microsoft 365 Defender
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
ms.openlocfilehash: 5605678a1fcc30719d7f838a16452ba527c554b7
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847043"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Afhjælpningshandlinger i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Under og efter en automatiseret undersøgelse i Microsoft 365 Defender identificeres afhjælpningshandlinger for skadelige eller mistænkelige elementer. Nogle typer afhjælpningshandlinger udføres på enheder, også kaldet slutpunkter. Andre afhjælpningshandlinger udføres på identiteter, konti og mailindhold. Automatiserede undersøgelser fuldføres, når afhjælpningshandlinger er taget, godkendt eller afvist.

> [!IMPORTANT]
> Om afhjælpningshandlinger udføres automatisk eller kun efter godkendelse, afhænger af visse indstillinger, f.eks. automatiseringsniveauer. Du kan få mere at vide i følgende artikler:
>
> - [Konfigurer dine automatiserede undersøgelses- og svarfunktioner i Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Konfigurer handlingskonti i Microsoft Defender for Identity](/defender-for-identity/manage-action-accounts)
> - [Sådan afhjælpes trusler på enheder](../defender-endpoint/automated-investigations.md)
> - [Trusler og afhjælpningshandlinger på mail & samarbejdsindhold](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

I følgende tabel opsummeres afhjælpningshandlinger, der i øjeblikket understøttes i Microsoft 365 Defender.

|Afhjælpningshandlinger for enheden (slutpunktet)  |Handlinger til afhjælpning af mail  |Brugere (konti)  |
|:---------|:---------|----------|
|- Indsaml undersøgelsespakke <br/>- Isoler enhed (denne handling kan fortrydes)<br/>- Offboard-maskine <br/>- Frigiv kørsel af kode <br/>- Frigiv fra karantæne <br/>- Anmodningseksempel <br/>- Begræns udførelse af kode (denne handling kan fortrydes) <br/>- Kør antivirusscanning <br/>- Stop og sæt karantæne      |- Bloker URL-adresse (tidspunkt for klik)<br/>- Blød sletning af mails eller klynger<br/>- Karantænemail<br/>- Sæt en vedhæftet fil i karantæne<br/>- Slå videresendelse af eksterne mails fra          |- Deaktiver bruger<br />- Nulstil brugeradgangskode<br />- Bekræft, at brugeren er kompromitteret          |

Afhjælpningshandlinger, uanset om de afventer godkendelse eller allerede er fuldført, kan ses i [Løsningscenter](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>Afhjælpningshandlinger, der følger efter automatiserede undersøgelser

Når en automatiseret undersøgelse er afsluttet, bliver der afsagt en dom for alle involverede beviser. Afhængigt af dommen identificeres afhjælpningshandlinger. I nogle tilfælde udføres afhjælpningshandlinger automatisk. i andre tilfælde skal afhjælpningsforanstaltningerne godkendes. Det hele afhænger af, hvordan [automatiseret undersøgelse og svar er konfigureret](m365d-configure-auto-investigation-response.md).

I følgende tabel kan du se en liste over mulige domme og resultater:

| Dom    | Berørte enheder    | Resultater|
|------|------|------|
| Skadelig    | Enheder (slutpunkter)    | Afhjælpningshandlinger udføres automatisk (forudsat at organisationens [enhedsgrupper](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) er angivet til **Fuld – afhjælper trusler automatisk**)|
| Kompromitteret | Brugere | Afhjælpningshandlinger udføres automatisk |
| Skadelig    | Mailindhold (URL-adresser eller vedhæftede filer) | Anbefalede afhjælpningshandlinger afventer godkendelse|
| Mistænkelige    | Enheder eller mailindhold | Anbefalede afhjælpningshandlinger afventer godkendelse|
| Der blev ikke fundet nogen trusler    | Enheder eller mailindhold    | Der kræves ingen afhjælpningshandlinger|

## <a name="remediation-actions-that-are-taken-manually"></a>Afhjælpningshandlinger, der udføres manuelt

Ud over afhjælpningshandlinger, der følger efter automatiserede undersøgelser, kan dit sikkerhedsteam udføre visse afhjælpningshandlinger manuelt. Disse omfatter følgende:

- Manuel enhedshandling, f.eks. enhedsisolation eller fil karantæne
- Manuel mailhandling, f.eks. blød sletning af mails
- Manuel brugerhandling, f.eks. deaktiver bruger eller nulstil brugeradgangskode
- [Avanceret jagthandling](../defender-endpoint/advanced-hunting-overview.md) på enheder, brugere eller mail
- [Explorer-handling](../office-365-security/threat-explorer.md) på mailindhold, f.eks. flytning af mail til uønsket mail, blød sletning af mail eller sletning af mail
- Manuel [direkte svar-handling](/windows/security/threat-protection/microsoft-defender-atp/live-response) , f.eks. sletning af en fil, standsning af en proces og fjernelse af en planlagt opgave
- Live response-handling med [Microsoft Defender for Endpoint API'er](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis), f.eks. isolering af en enhed, kørsel af en antivirusscanning og hentning af oplysninger om en fil

## <a name="next-steps"></a>Næste trin

- [Besøg Løsningscenter](m365d-action-center.md)
- [Få vist og administrer afhjælpningshandlinger](m365d-autoir-actions.md)
- [Adresser falske positiver eller falske negativer](m365d-autoir-report-false-positives-negatives.md)
