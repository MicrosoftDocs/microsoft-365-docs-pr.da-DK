---
title: Gennemse beskeder i Microsoft Defender for Endpoint
description: Gennemse beskedoplysninger, herunder en visualiseret historie og detaljer for hvert trin i kæden.
keywords: hændelse, hændelser, maskiner, enheder, brugere, beskeder, besked, undersøgelse, graf, beviser
ms.prod: m365-security
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.date: 5/1/2020
ms.technology: mde
ms.openlocfilehash: 91cd06188a8337f3d0df0b9c67d7c98e389e4351
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466735"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Gennemse beskeder i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Beskedsiden i Microsoft Defender for Endpoint giver fuld kontekst til beskeden ved at kombinere angrebs signaler og beskeder relateret til den valgte besked for at opbygge en detaljeret historie.

Du kan hurtigt undersøge, undersøge og reagere effektivt på vigtige beskeder, der påvirker din organisation. Forstå, hvorfor de blev udløst, og deres virkning fra ét sted. Få mere at vide i denne oversigt.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Introduktion til en besked

Hvis du vælger navnet på en besked i Defender for Endpoint, får du besked på din beskedside. På påmindelsessiden vises alle oplysninger i forbindelse med den valgte besked. Hver beskedside består af 4 sektioner:

1. **Titlen på beskeden** viser beskedens navn og minder dig om, hvilken besked der startede din aktuelle undersøgelse, uanset hvad du har valgt på siden.
2. [**Påvirkede aktiver**](#review-affected-assets) viser kort med enheder og brugere, der påvirkes af denne besked, og som du kan klikke på for at få yderligere oplysninger og handlinger.
3. **Beskedenheds tekstenhed** viser alle enheder, der er relateret til beskeden, og som er indbyrdes forbundet ved hjælp af en trævisning. Beskeden i titlen er den, der er i fokus, når du første gang lander på din valgte beskeds side. Enheder i beskedenheds tekstenhed kan udvides og klikkes for at angive yderligere oplysninger og fremskynde besvarelsen ved at gøre det muligt for dig at udføre handlinger direkte i konteksten for påmindelsessiden. Brug beskedens historie til at starte din undersøgelse. Se hvordan i [Undersøg beskeder i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. **Detaljeruden viser** oplysningerne om den valgte besked i starten med detaljer og handlinger, der er relateret til denne besked. Hvis du vælger et af de påvirkede aktiver eller enheder i beskedhistorien, ændres detaljeruden, så der angives kontekstafhængige oplysninger og handlinger for det markerede objekt.

Bemærk registreringsstatus for din besked.

- Forhindret: Den forsøgte mistænkelige handling blev undgået. Eksempelvis blev en fil enten ikke skrevet til disk eller udført.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Den side, der viser forebyggelse af en trussel" lightbox="images/detstat-prevented.png":::

- Blokeret: Mistænkelig adfærd blev udført og derefter blokeret. Eksempelvis blev en proces udført, men fordi den efterfølgende udviser mistænkelig adfærd, blev processen afsluttet.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Den side, der viser blokeringen af en trussel" lightbox="images/detstat-blocked.png":::

- Detekteret: Et angreb blev fundet og er muligvis stadig aktivt.

  :::image type="content" source="images/detstat-detected.png" alt-text="Siden, der viser registrering af en trussel" lightbox="images/detstat-detected.png":::

Du kan derefter også gennemgå oplysningerne  om den automatiske undersøgelse i detaljeruden for din besked for at se, hvilke handlinger der allerede er foretaget, samt læse beskrivelsen af beskeden for anbefalede handlinger.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Detaljeruden med beskrivelsen af beskeden og sektionerne til automatisk undersøgelse fremhævet" lightbox="images/alert-air-and-alert-description.png":::

Andre oplysninger, der er tilgængelige i detaljeruden, når beskeden åbnes, omfatter MITRE-teknikker, kilde og yderligere kontekstafhængige oplysninger.

## <a name="review-affected-assets"></a>Gennemse påvirkede aktiver

Når du vælger en enhed eller et brugerkort i sektionerne over berørte aktiver, skiftes der til oplysningerne om enheden eller brugeren i detaljeruden.

- **For enheder** viser detaljeruden oplysninger om selve enheden, f.eks. domæne, operativsystem og IP. Aktive beskeder og brugere, der er logget på på enheden, er også tilgængelige. Du kan straks udføre en handling ved at isolere enheden, begrænse udførelse af apps eller køre en antivirusscanning. Alternativt kan du indsamle en undersøgelsespakke, starte en automatisk undersøgelse eller gå til enhedssiden for at undersøge enheden ud fra enhedens synsvinkel.

   :::image type="content" source="images/device-page-details.png" alt-text="Detaljeruden, når en enhed er valgt" lightbox="images/device-page-details.png":::

- **For** brugere viser detaljeruden detaljerede brugeroplysninger, f.eks brugerens SAM-navn og SID, samt logontyper, der udføres af denne bruger, samt eventuelle beskeder og hændelser, der er relateret til den. Du kan *vælge Åbn brugerside* for at fortsætte undersøgelsen fra den pågældende brugers synsvinkel.

   :::image type="content" source="images/user-page-details.png" alt-text="Detaljeruden, når en bruger er valgt" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser køen over hændelser](view-incidents-queue.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
