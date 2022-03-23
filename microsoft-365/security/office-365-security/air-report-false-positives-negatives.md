---
title: Sådan rapporterer du falske positive eller falske negativer efter automatiseret undersøgelse i Microsoft Defender for Office 365
description: Blev noget overset eller fejlagtigt registreret af AIR i Microsoft Defender for Office 365? Få mere at vide om, hvordan du sender falske positive eller falske negativer til analyse hos Microsoft.
keywords: automatiseret, undersøgelse, besked, udløser, handling, afhjælpning, falsk positiv, falsk negativ
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
ms.prod: m365-security
ms.date: 01/29/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.technology: mdo
ms.openlocfilehash: 98164fd42a0ed2e2d79e2319823363057d15e7d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588648"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>Sådan rapporterer du falske positive/negativer i automatiseret undersøgelse og svarmuligheder

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis [automatiserede undersøgelses](automated-investigation-response-office.md)- og svarfunktioner (AIR) i Office 365 mistet eller fejlagtigt registreret noget, er der trin, som dit sikkerhedsteam kan udføre for at løse det. Disse handlinger omfatter:

- [Rapportering af en falsk positiv/negativ til Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis);
- [Justere beskeder (hvis](#adjust-an-alert-to-prevent-false-positives-from-recurring) det er nødvendigt). og
- [Fortryd afhjælpningshandlinger, der er blevet foretaget](#undo-a-remediation-action).

Brug denne artikel som vejledning.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Rapportér en falsk positiv/negativ til Microsoft til analyse

Hvis AIR i Microsoft Defender til Office 365 har mistet en mail, en vedhæftet fil i en mail, en URL-adresse i en mail eller en URL-adresse i en Office-fil, kan du sende [mistænkeligt spam, phish,](admin-submission.md) URL-adresser og filer til Microsoft til Office 365 scanning.

Du kan også [Sende en fil til Microsoft til analyse af malware](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Justere en besked for at forhindre falske positive i at blive gentaget

Hvis en besked udløses af legitim brug, eller beskeden er unøjagtig, kan du Administrere vigtige beskeder [på Defender for Cloud Apps-portalen](/cloud-app-security/managing-alerts).

Hvis din organisation bruger [Microsoft Defender til](/windows/security/threat-protection) slutpunkt ud over Office 365, og en fil, IP-adresse, URL-adresse eller domæne behandles som malware på en enhed, selvom det er sikkert, kan du oprette en brugerdefineret indikator med en ["Tillad"](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators)-handling for din enhed.

## <a name="undo-a-remediation-action"></a>Fortryde en afhjælpningshandling

Hvis der i de fleste tilfælde er blevet foretaget en afhjælpningshandling på en mail, en vedhæftet fil i en mail eller en URL-adresse, og elementet faktisk ikke er en trussel, kan dit sikkerhedsteam fortryde afhjælpningshandlingen og tage skridt til at forhindre den falske positive i at gentages. Du kan enten bruge [Trusselsstifinder](#undo-an-action-using-threat-explorer) eller [fanen Handlinger til at fortryde](#undo-an-action-in-the-action-center) en handling.

> [!IMPORTANT]
> Sørg for, at du har de nødvendige tilladelser, før du forsøger at udføre følgende opgaver.

### <a name="undo-an-action-using-threat-explorer"></a>Fortryde en handling ved hjælp af Threat Explorer

Med Threat Explorer kan dit sikkerhedsteam finde en mail, der påvirkes af en handling, og potentielt fortryde handlingen.

<br>

****

|Scenarie|Fortryd indstillinger|Lær mere|
|---|---|---|
|En mail blev distribueret til en brugers mappe med uønsket mail|<ul><li>Flytte meddelelsen til brugerens mappe Slettet post</li><li>Flytte meddelelsen til brugerens indbakke</li><li>Slet meddelelsen</li></ul>|[Find og undersøg ondsindede mails, der blev leveret i Office 365](investigate-malicious-email-that-was-delivered.md)|
|En mail eller en fil blev sat i karantæne|<ul><li>Slip mailen eller filen</li><li> Slet mailen eller filen</li></ul>|[Administrere meddelelser, der er sat i karantæne, som administrator](manage-quarantined-messages-and-files.md)|
|

### <a name="undo-an-action-in-the-action-center"></a>Fortryde en handling i Handlingscenter

I Handlingscenter kan du se afhjælpningshandlinger, der er blevet taget, og som potentielt kan fortryde handlingen.

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til Handlingscenter ved at vælge **Handlingscenter**. Hvis du vil gå direkte til Handlingscenter, skal du bruge <https://security.microsoft.com/action-center/>.
2. I Handlingscenter skal du vælge fanen **Oversigt** for at få vist listen over fuldførte handlinger.
3. Vælg et element. Pop op-ruden åbnes.
4. Vælg Fortryd i pop **op-ruden**. Det er kun handlinger, der kan fortrydes, der har en **Fortryd-knap** .

## <a name="see-also"></a>Se også

- [Microsoft Defender til Office 365](defender-for-office-365.md)
- [Automatiserede undersøgelser i Microsoft Defender til Office 365](office-365-air.md)
