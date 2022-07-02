---
title: Gennemse beskeder i Microsoft Defender for Endpoint
description: Gennemse beskedoplysninger, herunder en visualiseret beskedhistorie og detaljer for hvert trin i kæden.
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
ms.openlocfilehash: 76503c180dfdd2314254efc9315235c0802ab7f8
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607521"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Gennemse beskeder i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Beskedsiden i Microsoft Defender for Endpoint giver fuld kontekst for beskeden ved at kombinere angrebssignaler og beskeder, der er relateret til den valgte besked, for at oprette en detaljeret beskedhistorie.

Du kan hurtigt gennemgå, undersøge og udføre effektive handlinger på vigtige beskeder, der påvirker din organisation. Forstå, hvorfor de blev udløst, og deres indvirkning fra ét sted. Få mere at vide i denne oversigt.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Introduktion til en besked

Hvis du vælger en beskeds navn i Defender for Endpoint, lander du på dens beskedside. På beskedsiden vises alle oplysningerne i forbindelse med den valgte besked. Hver beskedside består af 4 afsnit:

1. **Beskedens titel** viser beskedens navn og er der for at minde dig om, hvilken besked der startede din aktuelle undersøgelse, uanset hvad du har valgt på siden.
2. [**Berørte aktiver**](#review-affected-assets) viser kort over enheder og brugere, der er berørt af denne besked, og som kan klikkes på for at få yderligere oplysninger og handlinger.
3. **Beskedhistorien** viser alle enheder, der er relateret til beskeden, og som er forbundet af en trævisning. Beskeden i titlen er i fokus, første gang du lander på den valgte beskeds side. Objekter i beskedhistorien kan udvides og klikkes for at give yderligere oplysninger og fremskynde svar ved at give dig mulighed for at udføre handlinger direkte i forbindelse med beskedsiden. Brug beskedhistorien til at starte din undersøgelse. Få mere at vide under [Undersøg beskeder i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. **Detaljeruden** viser først detaljerne for den valgte besked med oplysninger og handlinger, der er relateret til denne besked. Hvis du vælger en af de berørte aktiver eller objekter i beskedhistorien, ændres detaljeruden for at angive kontekstafhængige oplysninger og handlinger for det valgte objekt.

Bemærk registreringsstatus for din besked.

- Forhindret: Den forsøgte mistænkelige handling blev undgået. En fil blev f.eks. enten ikke skrevet på disken eller udført.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Siden, der viser forebyggelsen af en trussel" lightbox="images/detstat-prevented.png":::

- Blokeret: Mistænkelig funktionsmåde blev udført og derefter blokeret. En proces blev f.eks. udført, men fordi den efterfølgende udviste mistænkelig adfærd, blev processen afsluttet.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Den side, der viser blokeringen af en trussel" lightbox="images/detstat-blocked.png":::

- Registreret: Der blev registreret et angreb, som muligvis stadig er aktivt.

  :::image type="content" source="images/detstat-detected.png" alt-text="Den side, der viser opdagelsen af en trussel" lightbox="images/detstat-detected.png":::

Du kan derefter også gennemse oplysningerne *om den automatiserede undersøgelse* i detaljeruden for din besked for at se, hvilke handlinger der allerede er foretaget, samt læse beskrivelsen af beskeden for anbefalede handlinger.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Detaljeruden med afsnittene beskrivelse af besked og automatisk undersøgelse fremhævet" lightbox="images/alert-air-and-alert-description.png":::

Andre oplysninger, der er tilgængelige i detaljeruden, når beskeden åbnes, omfatter MITRE-teknikker, kilde og yderligere kontekstafhængige oplysninger.

> [!NOTE]
> Hvis du får vist beskedstatus for *ikke-understøttet beskedtype* , betyder det, at automatiserede undersøgelsesfunktioner ikke kan hente beskeden for at køre en automatisk undersøgelse. Du kan dog [undersøge disse beskeder manuelt](../defender/investigate-incidents.md#alerts).

## <a name="review-affected-assets"></a>Gennemse berørte aktiver

Hvis du vælger en enhed eller et brugerkort i afsnittene for de berørte aktiver, skifter du til oplysningerne om enheden eller brugeren i detaljeruden.

- **For enheder** vises der oplysninger om selve enheden i detaljeruden, f.eks. domæne, operativsystem og IP. Aktive beskeder og de brugere, der er logget på den pågældende enhed, er også tilgængelige. Du kan handle øjeblikkeligt ved at isolere enheden, begrænse udførelsen af appen eller køre en antivirusscanning. Du kan også indsamle en undersøgelsespakke, starte en automatiseret undersøgelse eller gå til enhedssiden for at undersøge det fra enhedens synspunkt.

   :::image type="content" source="images/device-page-details.png" alt-text="Detaljeruden, når en enhed vælges" lightbox="images/device-page-details.png":::

- **For brugere** vises detaljerede brugeroplysninger i detaljeruden, f.eks. brugerens SAM-navn og SID samt logontyper, der udføres af denne bruger, og eventuelle beskeder og hændelser, der er relateret til den. Du kan vælge *Åbn brugerside* for at fortsætte undersøgelsen fra den pågældende brugers synspunkt.

   :::image type="content" source="images/user-page-details.png" alt-text="Detaljeruden, når en bruger vælges" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser hændelseskøen](view-incidents-queue.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
