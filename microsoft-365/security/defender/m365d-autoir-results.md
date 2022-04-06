---
title: Detaljer og resultater af en automatisk undersøgelse
description: Se resultaterne og de vigtigste resultater af automatiseret undersøgelse i Microsoft 365 Defender
keywords: automatiseret, undersøgelse, resultater, analysér, detaljer, afhjælpning, autokorrektion
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
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
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 5a95980147c66fa8655f5c1b2ebe8adfff9e87c0
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501261"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Detaljer og resultater af en automatisk undersøgelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Det Microsoft 365 Defender muligt at få oplysninger [om undersøgelsen](m365d-autoir.md), når en automatisk undersøgelse køres, både under og efter den automatiske undersøgelsesproces. Hvis du har de nødvendige tilladelser, kan du få vist disse oplysninger i en [undersøgelsesdetaljeringsvisning](m365d-action-center.md#required-permissions-for-action-center-tasks), der giver dig opdateret status og mulighed for at godkende eventuelle ventende handlinger. 

## <a name="new-unified-investigation-page"></a>(NY) Siden Samlet undersøgelse

Undersøgelsessiden er for nylig blevet opdateret til at omfatte oplysninger på tværs af dine enheder, mails og samarbejdsindhold. Den nye, samlede undersøgelsesside definerer et fælles sprog og giver en samlet oplevelse for automatiske undersøgelser på [tværs Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) og [Microsoft Defender for Office 365](../office-365-security/defender-for-office-365.md). For at få adgang til den samlede undersøgelsesside skal du vælge linket i det gule banner, du ser på:

- En side i Office 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Security & Compliance Center</a>
- En undersøgelsesside på Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com))
- Enhver hændelse eller handlingscenteroplevelse i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>

## <a name="open-the-investigation-details-view"></a>Åbn undersøgelsesdetaljerne

Du kan åbne undersøgelsens detaljevisning ved hjælp af en af følgende metoder:

- [Vælg et element i Handlingscenter](#select-an-item-in-the-action-center)
- [Vælg en undersøgelse fra en side med oplysninger om hændelsen](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Vælg et element i Handlingscenter

Det forbedrede [handlingscenter](m365d-action-center.md) ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) samler [afhjælpningshandlinger på tværs](m365d-remediation-actions.md) af dine enheder, mail & indhold til samarbejde og identiteter. Angivne handlinger omfatter afhjælpningshandlinger, der er blevet foretaget automatisk eller manuelt. I Handlingscenter kan du få vist handlinger, der afventer godkendelse, og handlinger, der allerede er godkendt eller fuldført. Du kan også gå til flere detaljer, f.eks. en undersøgelsesside.

> [!TIP]
> Du skal have [visse tilladelser for](m365d-action-center.md#required-permissions-for-action-center-tasks) at godkende, afvise eller fortryde handlinger.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på. 

2. Vælg Handlingscenter i **navigationsruden**. 

3. Vælg et element **under** **fanen Ventende** eller Oversigt. Pop op-ruden åbnes.

4. Gennemse oplysningerne i pop op-ruden, og gør derefter et af følgende:
   - Vælg **siden Åbn undersøgelse for** at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en afventende handling.
   - Vælg **Afvis** for at forhindre, at der tages en afventende handling.
   - Vælg **Gå på jagt** for at gå til [Avanceret jagt](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Åbn en undersøgelse fra siden med oplysninger om hændelsen

Brug en side med oplysninger om hændelser til at få vist detaljerede oplysninger om en hændelse, herunder beskeder, der blev udløst oplysninger om påvirkede enheder, brugerkonti eller postkasser.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på. 

2. I **navigationsruden skal du vælge Hændelser &** **beskederIncidents** > . 

3. Vælg et element på listen, og vælg derefter **Åbn hændelsesside**.

4. Vælg **fanen Undersøgelser** , og vælg derefter en undersøgelse på listen. Pop op-ruden åbnes.

5. Vælg **siden Åbn undersøgelse**. 

Her er et eksempel.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Undersøgelsessiden på Microsoft 365 Defender portalen" lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>Undersøgelsesoplysninger

Brug visningen undersøgelsesdetaljer til at se tidligere, aktuelle og afventende aktiviteter i forbindelse med en undersøgelse. Her er et eksempel.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Siden med undersøgelsesoplysninger i Microsoft 365 Defender portalen" lightbox="../../media/mtp-air-investdetails.png":::

I  visningen **Undersøgelsesdetaljer** kan du se oplysninger på fanerne Undersøgelse, **Beskeder, Enheder****, Identiteter**, Nøgle **fund, Enheder**, **Log** og Ventende handlinger, der er beskrevet i følgende tabel. 

> [!NOTE]
> De specifikke faner, du ser på siden med undersøgelsesoplysninger, afhænger af, hvad dit abonnement omfatter. Hvis dit abonnement f.eks. ikke Microsoft Defender for Office 365 plan 2, kan du ikke se fanen **Postkasser**.

| Tabulator | Beskrivelse |
|:--------|:--------|
| **Graf for undersøgelse** | Giver en visuel repræsentation af undersøgelsen. Afbilder enheder og viser fundne trusler samt beskeder, og om der er handlinger, der afventer godkendelse.<br/>Du kan vælge et element på grafen for at få vist flere detaljer. Hvis du f.eks. **vælger ikonet** Beviser, kommer du  til fanen Beviser, hvor du kan se registrerede enheder og deres konklusion. |
| **Beskeder** | Viser beskeder, der er knyttet til undersøgelsen. Beskeder kan komme fra funktioner til trusselsbeskyttelse på en brugers enhed, i Office, Microsoft Defender for Cloud Apps og andre Microsoft 365 Defender funktioner.|
| **Enheder** | Viser de enheder, der er medtaget i undersøgelsen, samt afhjælpningsniveauet. (Afhjælpningsniveauer svarer til [automatiseringsniveauet for enhedsgrupper](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups)). |
| **Postkasser** |Viser postkasser, der er påvirket af registrerede trusler.  |
| **Brugere**  | Viser brugerkonti, der er påvirket af registrerede trusler. |
| **Beviser** | Oplister beviser, der er taget i forbindelse med beskeder eller undersøgelser. Omfatter konklusion (*ondsindede*, *mistænkelige**, ukendte* eller *ingen trusler fundet*) og afhjælpningsstatus. |
| **Enheder** | Indeholder oplysninger om hver analyseret enhed, herunder en konklusion for hver enhedstype (*ondsindede**,* mistænkelige eller *ingen trusler fundet*).|
|**Log** | Giver en kronologisk og detaljeret visning af alle undersøgelseshandlinger, der er foretaget, efter at der blev udløst en besked.|
| **Ventende handlingsoversigt** | Viser elementer, der kræver godkendelse for at fortsætte. Gå til Handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) for at godkende afventende handlinger. |

## <a name="next-steps"></a>Næste trin

- [Få vist og administrer afhjælpningshandlinger](m365d-autoir-actions.md)
- [Få mere at vide om afhjælpningshandlinger](m365d-remediation-actions.md)
