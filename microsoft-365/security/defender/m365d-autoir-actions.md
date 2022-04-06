---
title: Få vist og administrer handlinger i Handlingscenter
description: Brug handlingscenter til at få vist og administrere afhjælpningshandlinger
keywords: handling, center, autoair, automatiseret, undersøgelse, svar, afhjælpning
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
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: a77a64e2323cc836df9b19694deb5c32ee877fb8
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500799"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Få vist og administrer handlinger i Handlingscenter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Trusselsbeskyttelsesfunktioner i Microsoft 365 Defender kan resultere i visse afhjælpningshandlinger. Her er nogle eksempler:

- [Automatiserede undersøgelser kan](m365d-autoir.md) resultere i afhjælpningshandlinger, der er taget automatisk, eller som afventer din godkendelse.
- Antivirus-, antimalware- og andre funktioner til trusselsbeskyttelse kan resultere i afhjælpningshandlinger, f.eks. blokere en fil, URL-adresse eller proces eller sende en artefakt til karantæne.
- Dit sikkerhedsteam kan løse problemer manuelt, f.eks. under avanceret jagt, eller mens det undersøger [beskeder](investigate-alerts.md) [eller hændelser](investigate-incidents.md).[](advanced-hunting-overview.md)

> [!NOTE]
> Du skal have [de rette tilladelser for](m365d-action-center.md#required-permissions-for-action-center-tasks) at godkende eller afvise afhjælpningshandlinger. Du kan finde flere oplysninger under [forudsætningerne](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>Gennemse afventende handlinger i Handlingscenter

Det er vigtigt at godkende (eller afvise) afventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fortsætte og afslutte i tide. 

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på. 

2. Vælg Handlingscenter i **navigationsruden**. 

3. Vælg et element på listen **under fanen** Afventer i Handlingscenter. Pop op-ruden åbnes. Her er et eksempel.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Indstillingerne for at godkende eller afvise en handling" lightbox="../../media/air-actioncenter-itemselected.png":::

4. Gennemse oplysningerne i pop op-ruden, og gør derefter et af følgende:
   - Vælg **siden Åbn undersøgelse for** at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en afventende handling.
   - Vælg **Afvis** for at forhindre, at der tages en afventende handling.
   - Vælg **Gå på jagt** for at gå til [Avanceret jagt](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Fortryde fuldførte handlinger

Hvis du har besluttet, at en enhed eller en fil ikke er en trussel, kan du fortryde afhjælpningshandlinger, der blev foretaget, uanset om disse handlinger blev foretaget automatisk eller manuelt. I handlingscenter under fanen **Oversigt** kan du fortryde en af følgende handlinger:  

| Handlingskilde | Understøttede handlinger |
|:---|:---|
| - Automatiseret undersøgelse <br/>- Microsoft Defender Antivirus <br/>- Manuelle svarhandlinger | - Isoler enhed <br/>- Begræns udførelse af kode <br/>- Sætte en fil i karantæne <br/>- Fjerne en registreringsdatabasenøgle <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjerne en planlagt opgave |

### <a name="undo-one-remediation-action"></a>Fortryd en afhjælpningshandling

1. Gå til handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.

2. Vælg en **handling** , du vil fortryde, under fanen Oversigt.

3. I ruden i højre side af skærmen skal du vælge **Fortryd**.

### <a name="undo-multiple-remediation-actions"></a>Fortryd flere afhjælpningshandlinger

1. Gå til handlingscenter (https://security.microsoft.com/action-center) og log på.

2. Vælg **de handlinger** , du vil fortryde, under fanen Oversigt. Sørg for at markere elementer, der har samme handlingstype. Der åbnes en pop op-rude.

3. Vælg Fortryd i pop **op-ruden**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Sådan fjernes en fil fra karantæne på tværs af flere enheder 

1. Gå til handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.

2. På fanen **Oversigt skal** du vælge en fil, der har filtypen **Karantæne** .

3. I ruden i højre side af skærmen skal du vælge Anvend på **X flere forekomster** af denne fil og derefter vælge Fortryd.

## <a name="next-steps"></a>Næste trin

- [Få vist detaljer og resultater af en automatisk undersøgelse](m365d-autoir-results.md)
- [Adressere falske positive eller falske negativer](m365d-autoir-report-false-positives-negatives.md)
