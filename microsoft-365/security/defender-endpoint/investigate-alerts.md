---
title: Undersøg Microsoft Defender for Endpoint beskeder
description: Brug undersøgelsesmulighederne til at få oplysninger om vigtige beskeder, der påvirker dit netværk, hvad de betyder, og hvordan du løser dem.
keywords: undersøg, undersøgelse, enheder, enhed, beskedkø, dashboard, IP-adresse, fil, indsende, indsendelser, detaljeret analyse, tidslinje, søgning, domæne, URL-adresse, IP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: e4d379ee476276d24b683878bc4978addf220ced
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665794"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Undersøg beskeder i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Undersøg vigtige beskeder, der påvirker dit netværk, forstå, hvad de betyder, og hvordan du løser dem.

Vælg en besked fra beskedkøen for at gå til siden med beskeder. Denne visning indeholder beskedens titel, de berørte aktiver, detaljesidens rude og beskedhistorien.

Start din undersøgelse på beskedsiden ved at vælge de berørte aktiver eller en hvilken som helst af enhederne under trævisningen af beskedhistorien. Detaljeruden udfyldes automatisk med yderligere oplysninger om det, du har valgt. Hvis du vil se, hvilken type oplysninger du kan få vist her, skal du læse [Gennemse beskeder i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>Undersøg, hvordan du bruger beskedhistorien

Beskedhistorien indeholder oplysninger om, hvorfor beskeden blev udløst, relaterede hændelser, der skete før og efter, samt andre relaterede objekter.

Objekter kan klikkes på, og alle objekter, der ikke er en besked, kan udvides ved hjælp af udvidelsesikonet i højre side af objektets kort. Den enhed, der er i fokus, angives med en blå stribe til venstre for enhedens kort, hvor beskeden i titlen først er i fokus.

Udvid objekter for at få vist detaljer på et øjeblik. Hvis du vælger et objekt, ændres konteksten for detaljeruden til denne enhed, og du kan gennemse yderligere oplysninger samt administrere objektet. Hvis du vælger *...* til højre for objektkortet, vises alle de handlinger, der er tilgængelige for det pågældende objekt. De samme handlinger vises i detaljeruden, når objektet er i fokus.

> [!NOTE]
> Afsnittet med beskedhistorien kan indeholde mere end én besked, hvor yderligere beskeder, der er relateret til det samme udførelsestræ, vises før eller efter den besked, du har valgt.

:::image type="content" source="images/alert-story-tree.png" alt-text="en beskedhistorie med en besked i fokus og nogle udvidede kort" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>Udfør en handling fra detaljeruden

Når du har valgt et objekt af interesse, ændres detaljeruden, så der vises oplysninger om den valgte objekttype, historikoplysninger, når den er tilgængelig, og der tilbydes kontrolelementer til at **udføre handlinger** på dette objekt direkte fra beskedsiden.

Når du er færdig med at undersøge, skal du gå tilbage til den besked, du startede med, markere beskedens status som **Løst** og klassificere den som enten **falsk eller** **sand besked**. Klassificering af beskeder hjælper med at tilpasse denne funktion, så du får flere sande beskeder og færre falske beskeder.

Hvis du klassificerer den som en sand besked, kan du også vælge en bestemmelse, som vist på billedet nedenfor.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="Detaljeruden med en løst besked og rullelisten til bestemmelse udvidet" lightbox="images/alert-details-resolved-true.png":::

Hvis du oplever en falsk besked med et line-of-business-program, skal du oprette en regel for undertrykkelse for at undgå denne type besked i fremtiden.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="Handlingerne og klassificeringen i detaljeruden med undertrykkelsesreglen fremhævet" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> Hvis du oplever problemer, der ikke er beskrevet ovenfor, kan du bruge knappen 🙂 til at give feedback eller åbne en supportanmodning.

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser køen Microsoft Defender for Endpoint beskeder](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint beskeder](manage-alerts.md)
- [Undersøg en fil, der er knyttet til en defender for endpoint-besked](investigate-files.md)
- [Undersøg enheder på listen Defender for Endpoint Devices](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Defender for Endpoint-besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Defender for Endpoint-besked](investigate-domain.md)
- [Undersøg en brugerkonto i Defender for Endpoint](investigate-user.md)
