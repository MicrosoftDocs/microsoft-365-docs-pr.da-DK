---
title: Undersøg brugere Microsoft 365 Defender
description: Undersøg brugere for en hændelse i Microsoft 365 Defender-portalen.
keywords: security, malware, Microsoft 365, M365, security center, monitor, report, identities, data, devices, apps, incident, analyze, response
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 51bb4f451329a74417c21db0a64aadae6dccbce6
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500865"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>Undersøg brugere Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

En del af din undersøgelse af hændelser kan omfatte brugerkonti. Du kan se oplysningerne om brugerkonti identificeret i beskederne om en hændelse i Microsoft 365 Defender-portalen fra hændelser **&-beskedhændelse** \> ***_ \> _* Users**. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Siden Brugere for en hændelse i Microsoft 365 Defender-portalen." lightbox="../../media/investigate-incidents/incident-users.png":::

Hvis du vil have en hurtig oversigt over en brugerkonto for hændelsen, skal du markere afkrydsningsfeltet ud for navnet på brugerkontoen. Her er et eksempel.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Fanen Brugere for en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> Brugersiden viser en Azure Active Directory (Azure AD) samt grupper, så du kan forstå de grupper og tilladelser, der er knyttet til en bruger.

I denne rude kan du gennemse oplysninger om brugertrusler, herunder aktuelle hændelser, aktive beskeder og risikoniveau samt bruger eksponering, konti, enheder og meget mere.

Desuden kan du handle direkte i Microsoft 365 Defender-portalen for at håndtere en kompromitteret bruger, f.eks. bekræfte, at brugerkontoen er kompromitteret eller kræve et nyt logon.

Herfra kan du vælge Gå **til brugerside for** at få vist detaljerne for en brugerkonto. Her er et eksempel.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Oplysningerne om brugerkontoen i Microsoft 365 Defender portal" lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

Du kan også se denne side ved at vælge navnet på brugerkontoen på listen på **siden** Brugere.

Du kan se gruppemedlemskab for brugeren ved at vælge tallet under **Grupper**.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="Oplysningerne om gruppemedlemskab for en bruger i Microsoft 365 Defender portal" lightbox="../../media/investigate-users/user-group-membership.png":::

Hvis du vælger ikonet under **Administrator**, kan du se, hvor brugeren er i organisationstræet.

Brugersiden Microsoft 365 Defender portal kombinerer oplysninger fra Microsoft Defender for Endpoint, Microsoft Defender for Identity og Microsoft Defender for Cloud Apps (afhængigt af, hvilke licenser du har).

Denne side viser oplysninger, der er specifikke for sikkerhedsrisikoen ved en brugerkonto, og som indeholder et resultat, der hjælper med at vurdere risici og de seneste hændelser og beskeder, som har bidraget til den samlede risiko.

Fra denne side kan du udføre disse yderligere handlinger:

- Markér brugerkontoen som kompromitteret
- Kræv, at brugeren logger på igen
- Suspendere brugerkontoen
- Se indstillingerne for Azure AD-brugerkontoen
- Få vist de filer, der ejes af brugerkontoen
- Få vist filer, der er delt med denne bruger.

Her er et eksempel.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Det afsnit, der beskriver handlingerne for en brugerkonto for en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>Få vist laterale bevægelsesstier

Ved at vælge fanen **Laterale bevægelsesstier** kan du få vist et fuldt dynamisk og klikbart kort, der giver dig en visuel repræsentation af de laterale bevægelsesstier til og fra denne bruger, som kan bruges til at infiltrere dit netværk.

Kortet giver dig en liste over, hvor mange hop mellem computere eller brugere en hacker vil have til og fra denne bruger for at kompromittere en følsom konto, og hvis brugeren har en følsom konto, kan du se, hvor mange ressourcer og konti der er direkte forbundet.

Hvis en potentiel lateral bevægelsessti ikke blev fundet for enheden i løbet af de seneste to dage, vises grafen ikke. Vælg en anden dato ved hjælp af Få vist en anden dato for at få vist tidligere laterale bevægelsesstier, der findes for dette objekt. Rapporten med den laterale bevægelsessti er altid tilgængelig og giver dig oplysninger om de potentielle laterale bevægelsesstier, der findes, og kan tilpasses til tiden.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="Den laterale bevægelsessti for en bruger i Microsoft 365 Defender portal" lightbox="../../media/investigate-users/lateral-movement-path.png":::

Du kan finde flere oplysninger [i Senere bevægelsesstier](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>Næste trin

Fortsæt undersøgelsen, hvis det er nødvendigt for in-processhændelser.[](investigate-incidents.md)

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Administrer hændelser](manage-incidents.md)
