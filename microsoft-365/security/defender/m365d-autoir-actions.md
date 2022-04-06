---
title: Få vist og administrer handlinger i Løsningscenter
description: Brug Løsningscenter til at få vist og administrere afhjælpningshandlinger
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
ms.openlocfilehash: 43c48081a86e33cd918bc4de8f01859bc1107583
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666828"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>Få vist og administrer handlinger i Løsningscenter

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Trusselsbeskyttelsesfunktioner i Microsoft 365 Defender kan resultere i visse afhjælpningshandlinger. Her er nogle eksempler:

- [Automatiserede undersøgelser](m365d-autoir.md) kan resultere i afhjælpningshandlinger, der udføres automatisk, eller som afventer din godkendelse.
- Antivirus, antimalware og andre trusselsbeskyttelsesfunktioner kan resultere i afhjælpningshandlinger, f.eks. blokering af en fil, URL-adresse eller proces eller afsendelse af en artefakt for at sætte en artefakt i karantæne.
- Dit team af sikkerhedshandlinger kan udføre afhjælpningshandlinger manuelt, f.eks. under [avanceret jagt](advanced-hunting-overview.md) eller under undersøgelse af [beskeder](investigate-alerts.md) eller [hændelser](investigate-incidents.md).

> [!NOTE]
> Du skal have [de nødvendige tilladelser](m365d-action-center.md#required-permissions-for-action-center-tasks) til at godkende eller afvise afhjælpningshandlinger. Du kan få flere oplysninger under [forudsætningerne](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>Gennemse ventende handlinger i Løsningscenter

Det er vigtigt at godkende (eller afvise) ventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fortsætte og fuldføres rettidigt. 

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal,</a> og log på. 

2. Vælg **Løsningscenter** i navigationsruden. 

3. Vælg et element på listen under fanen **Ventende** i Handlingscenter. Dens pop op-rude åbnes. Her er et eksempel.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Mulighederne for at godkende eller afvise en handling" lightbox="../../media/air-actioncenter-itemselected.png":::

4. Gennemse oplysningerne i pop op-ruden, og udfør derefter et af følgende trin:
   - Vælg **siden Åbn undersøgelse** for at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en ventende handling.
   - Vælg **Afvis** for at forhindre, at der udføres en ventende handling.
   - Vælg **Gå på jagt** for at gå ind i [Avanceret jagt](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>Fortryd fuldførte handlinger

Hvis du har fastslået, at en enhed eller en fil ikke er en trussel, kan du fortryde afhjælpningshandlinger, der er foretaget, uanset om disse handlinger blev udført automatisk eller manuelt. I Handlingscenter under fanen **Oversigt** kan du fortryde en af følgende handlinger:  

| Handlingskilde | Understøttede handlinger |
|:---|:---|
| - Automatiseret undersøgelse <br/>- Microsoft Defender Antivirus <br/>- Handlinger for manuelt svar | - Isoler enhed <br/>- Begræns udførelse af kode <br/>- Sæt en fil i karantæne <br/>- Fjern en registreringsdatabasenøgle <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjern en planlagt opgave |

### <a name="undo-one-remediation-action"></a>Fortryd én afhjælpningshandling

1. Gå til Løsningscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.

2. Vælg en handling, du vil fortryde, under fanen **Oversigt** .

3. Vælg **Fortryd** i ruden til højre på skærmen.

### <a name="undo-multiple-remediation-actions"></a>Fortryd flere afhjælpningshandlinger

1. Gå til Løsningscenter ( ,https://security.microsoft.com/action-center) og log på.

2. Vælg de handlinger, du vil fortryde, under fanen **Oversigt** . Sørg for at vælge elementer, der har samme handlingstype. Der åbnes en pop op-rude.

3. Vælg **Fortryd** i pop op-ruden.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>Sådan fjernes en fil fra karantæne på tværs af flere enheder 

1. Gå til Løsningscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), og log på.

2. Vælg en fil med handlingstypen **Karantæne under** fanen **Historik**.

3. I ruden til højre på skærmen skal du vælge **Anvend på X flere forekomster af denne fil** og derefter vælge **Fortryd**.

## <a name="next-steps"></a>Næste trin

- [Få vist detaljer og resultater for en automatiseret undersøgelse](m365d-autoir-results.md)
- [Adresser falske positiver eller falske negativer](m365d-autoir-report-false-positives-negatives.md)
