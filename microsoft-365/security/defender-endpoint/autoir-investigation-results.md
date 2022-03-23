---
title: Få vist detaljer og resultater af en automatisk undersøgelse
description: Under og efter en automatiseret undersøgelse kan du få vist resultaterne og de vigtigste resultater
keywords: automatiseret, undersøgelse, resultater, analysér, detaljer, afhjælpning, autokorrektion
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
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
ms.openlocfilehash: 294722f3f79172e06752c5318bfef21dfc640eed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591276"
---
# <a name="view-the-details-and-results-of-an-automated-investigation"></a>Få vist detaljer og resultater af en automatisk undersøgelse

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Når en automatiseret undersøgelse køres med Microsoft [](automated-investigations.md) Defender for Endpoint, er oplysninger om undersøgelsen tilgængelige både under og efter den automatiske undersøgelsesproces. Hvis du har de nødvendige tilladelser, kan du få vist disse oplysninger i en undersøgelsesvisning. Visningen Undersøgelsesdetaljer giver dig opdateret status og mulighed for at godkende eventuelle afventende handlinger.

## <a name="new-unified-investigation-page"></a>(NY!) Siden Samlet undersøgelse

Undersøgelsessiden er for nylig blevet opdateret til at omfatte oplysninger på tværs af dine enheder, mails og samarbejdsindhold. Den nye, samlede undersøgelsesside definerer et fælles sprog og giver en samlet oplevelse af automatiske undersøgelser på tværs af [Microsoft Defender til Endpoint](microsoft-defender-endpoint.md) og [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp).

> [!TIP]
> Du kan få mere at vide om, hvad der ændres, under [(NYT!) Siden Samlet undersøgelse](/microsoft-365/security/mtp/mtp-autoir-results).

## <a name="open-the-investigation-details-view"></a>Åbn undersøgelsesdetaljerne

Du kan åbne undersøgelsens detaljevisning ved hjælp af en af følgende metoder:

- [Vælg et element i Handlingscenter](#select-an-item-in-the-action-center)
- [Vælg en undersøgelse fra en side med oplysninger om hændelsen](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Vælg et element i Handlingscenter

Det forbedrede [handlingscenter](auto-investigation-action-center.md) samler [afhjælpningshandlinger på tværs](manage-auto-investigation.md#remediation-actions) af dine enheder, & indhold til samarbejde og identiteter. Angivne handlinger omfatter afhjælpningshandlinger, der er blevet foretaget automatisk eller manuelt. I Handlingscenter kan du få vist handlinger, der afventer godkendelse, og handlinger, der allerede er godkendt eller fuldført. Du kan også gå til flere detaljer, f.eks. en undersøgelsesside.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> og log på.
2. Vælg Handlingscenter i **navigationsruden**.
3. Vælg et element **under** **fanen Ventende** eller Oversigt. Pop op-ruden åbnes.
4. Gennemse oplysningerne i pop op-ruden, og gør derefter et af følgende:
   - Vælg **siden Åbn undersøgelse for** at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en afventende handling.
   - Vælg **Afvis** for at forhindre, at der tages en afventende handling.
   - Vælg **Gå på jagt** for at gå til [Avanceret jagt](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Åbn en undersøgelse fra siden med oplysninger om hændelsen

Brug en side med oplysninger om hændelser til at få vist detaljerede oplysninger om en hændelse, herunder beskeder, der blev udløst oplysninger om påvirkede enheder, brugerkonti eller postkasser.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> og log på.
2. I **navigationsruden skal du vælge Hændelser & hændelser** \> **.**
3. Vælg et element på listen, og vælg derefter **Åbn hændelsesside**.
4. Vælg **fanen Undersøgelser** , og vælg derefter en undersøgelse på listen. Pop op-ruden åbnes.
5. Vælg **siden Åbn undersøgelse**.

## <a name="investigation-details"></a>Undersøgelsesoplysninger

Brug visningen undersøgelsesdetaljer til at se tidligere, aktuelle og afventende aktiviteter i forbindelse med en undersøgelse. Visningen med undersøgelsesdetaljer ligner følgende billede:

I  visningen **Undersøgelsesdetaljer** kan du se oplysninger på fanerne Undersøgelse, **Beskeder, Enheder****, Identiteter**, Nøgle **fund, Enheder**, **Log** og Ventende handlinger, der er beskrevet i følgende tabel. 

> [!NOTE]
> De specifikke faner, du ser på siden med undersøgelsesoplysninger, afhænger af, hvad dit abonnement omfatter. Hvis dit abonnement f.eks. ikke omfatter Microsoft Defender Office 365 Plan 2, kan du ikke se **fanen Postkasser**.

|Tabulator|Beskrivelse|
|---|---|
|**Graf for undersøgelse**|Giver en visuel repræsentation af undersøgelsen. Afbilder enheder og viser fundne trusler samt beskeder, og om der er handlinger, der afventer godkendelse. <p> Du kan vælge et element på grafen for at få vist flere detaljer. Hvis du f.eks. **vælger ikonet** Beviser, kommer du  til fanen Beviser, hvor du kan se registrerede enheder og deres konklusion.|
|**Beskeder**|Viser beskeder, der er knyttet til undersøgelsen. Beskeder kan komme fra funktioner til trusselsbeskyttelse på en brugers enhed, i Office apps, Defender til skyapps og andre Microsoft 365 Defender funktioner.|
|**Enheder**|Viser de enheder, der er medtaget i undersøgelsen, samt afhjælpningsniveauet. (Afhjælpningsniveauer svarer til [automatiseringsniveauet for enhedsgrupper](automation-levels.md)).|
|**Postkasser**|Viser postkasser, der er påvirket af registrerede trusler.|
|**Brugere**|Viser brugerkonti, der er påvirket af registrerede trusler.|
|**Beviser**|Oplister beviser, der er taget i forbindelse med beskeder/undersøgelser. Omfatter konklusion (*ondsindede*, *mistænkelige* eller *ingen trusler fundet*) og afhjælpningsstatus.|
|**Enheder**|Indeholder oplysninger om hver analyseret enhed, herunder en konklusion for hver enhedstype (*ondsindede**,* mistænkelige eller *ingen trusler fundet*).|
|**Log**|Giver en kronologisk og detaljeret visning af alle undersøgelseshandlinger, der er foretaget, efter at der blev udløst en besked.|
|**Ventende handlinger**|Viser elementer, der kræver godkendelse for at fortsætte. Gå til Handlingscenter (<https://security.microsoft.com/action-center>) for at godkende afventende handlinger.|

## <a name="see-also"></a>Se også

- [Gennemse afhjælpningshandlinger efter en automatisk undersøgelse](manage-auto-investigation.md)
- [Få vist og organiser køen for Microsoft Defender til slutpunktshændelser](view-incidents-queue.md)
