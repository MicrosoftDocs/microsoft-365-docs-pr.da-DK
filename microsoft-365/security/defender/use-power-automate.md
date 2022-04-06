---
title: Brug Power Automate
description: Få mere at vide om Power Automate Microsoft 365 Defender, og hvordan du bruger dem.
keywords: avanceret jagt, trusselssporing, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kopikopier
search.product: eADQiWindows 10XVcnh
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
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a707de259897080f8e726aed70618ea6505bdea6
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63606685"
---
# <a name="use-power-automate-in-microsoft-365-defender"></a>Brug Power Automate i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

Moderne sikkerhedsteams (SecOps) skal bruge automatisering for at kunne fungere effektivt. Hvis du vil fokusere på at lede efter og undersøge reelle trusler, skal SecOps-teams bruge Power Automate til at gennemgå listen over vigtige beskeder og fjerne dem, der ikke er trusler.  

## <a name="criteria-for-resolving-alerts"></a>Kriterier for løsning af beskeder

- Bruger har Ikke til tilstede-meddelelse aktiveret

- Brugeren er ikke mærket som høj risiko

Hvis begge er sande, markerer SecOps beskeden som legitim rejse og løser den. Der sendes en meddelelse i Microsoft Teams, når beskeden er løst. 

## <a name="connect-power-automate-to-microsoft-cloud-app-security"></a>Forbind Power Automate til Microsoft Cloud App Security

Hvis du vil oprette automatiseringen, skal du bruge et API-token, før du kan Power Automate til Microsoft Cloud App Security (MCAS). 

1. Klik **Indstillinger**, vælg **Sikkerhedsudvidelser**, og klik derefter **på Tilføj token** på **fanen API-tokens**. 

2. Angiv et navn til din token, og klik derefter på **Generér**. Gem tokenet, som du skal bruge det senere.

## <a name="create-an-automated-flow"></a>Opret et automatiseret flow

Du kan se den detaljerede trinvise proces i videoen [her](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn). 

Denne video beskriver også, hvordan du forbinder power automate til MCAS. 

## <a name="related-information"></a>Relaterede oplysninger

- [Integrer Power Automate med Microsoft Cloud App Security](/cloud-app-security/flow-integration)

- [Microsoft Power Automate dokumentation](/power-automate)
