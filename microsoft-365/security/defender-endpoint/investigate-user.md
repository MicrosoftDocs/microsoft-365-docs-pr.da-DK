---
title: Undersøg en brugerkonto i Microsoft Defender for Endpoint
description: Undersøg en brugerkonto for potentielt kompromitterede legitimationsoplysninger eller pivoter den tilknyttede brugerkonto under en undersøgelse.
keywords: undersøge, konto, bruger, brugerenhed, besked, Microsoft Defender for Endpoint
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 76b0b7405c8dc1c434fbc9f991903b25d8b9d4f4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469333"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>Undersøg en brugerkonto i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatgeuser-abovefoldlink)

## <a name="investigate-user-account-entities"></a>Undersøg enheder af brugerkonti

Identificer brugerkonti med de mest aktive beskeder (vises på dashboard som "Risikobrugere") og undersøg tilfælde af potentielle kompromitterede legitimationsoplysninger, eller pivoter på den tilknyttede brugerkonto, når du undersøger en besked eller enhed for at identificere mulige senere bevægelser mellem enheder med den pågældende brugerkonto.

Du kan finde oplysninger om brugerkontoen i følgende visninger:

- Dashboard
- Beskedkø
- Siden Enhedsoplysninger

Et klikbart link til brugerkontoen er tilgængeligt i disse visninger, og du kommer til siden med oplysninger om brugerkontoen, hvor der vises flere oplysninger om brugerkontoen.

Når du undersøger en brugerkontoenhed, får du vist:

- Brugerkontooplysninger, beskeder Microsoft Defender for Identity logget på enheder, rolle, logontype og andre oplysninger
- Oversigt over hændelserne og brugerens enheder
- Beskeder, der er relateret til denne bruger
- Observeret i organisationen (enheder, der er logget på)

:::image type="content" source="images/atp-user-details-view.png" alt-text="Siden med oplysninger om brugerkontoenhed" lightbox="images/atp-user-details-view.png":::

### <a name="user-details"></a>Brugeroplysninger

Ruden  Brugeroplysninger i venstre side indeholder oplysninger om brugeren, f.eks. relaterede åbne hændelser, aktive beskeder, SAM-navn, SID, Microsoft Defender for Identity-beskeder, antal enheder, brugeren er logget på, hvornår brugeren først blev set og sidst set, rolle- og logontyper. Afhængigt af de integrationsfunktioner, du har aktiveret, får du vist andre oplysninger. Hvis du f.eks. aktiverer Skype for Business-integration, vil du kunne kontakte brugeren fra portalen. Sektionen **Azure ATP-beskeder** indeholder et link, der leder dig til Microsoft Defender for Identity-siden, hvis du har aktiveret Microsoft Defender for Identity-funktionen, og der er beskeder, der er relateret til brugeren. På Microsoft Defender for Identity side kan du finde flere oplysninger om beskederne.

> [!NOTE]
> Du skal aktivere integrationen på både Microsoft Defender for Identity Defender for Endpoint for at bruge denne funktion. I Defender til Slutpunkt kan du aktivere denne funktion i avancerede funktioner. Du kan finde flere oplysninger om, hvordan du aktiverer avancerede funktioner, [under Slå avancerede funktioner til](advanced-features.md).

Oversigten, Beskeder og Observeret i organisationen er forskellige faner, der viser forskellige attributter om brugerkontoen.


>[!NOTE]
>For Linux-enheder vises oplysninger om brugere, der er logget på, ikke.


### <a name="overview"></a>Oversigt

Fanen **Oversigt** viser hændelserne og en liste over de enheder, brugeren har logget på. Du kan udvide disse for at få vist oplysninger om log på-hændelserne for hver enhed.

### <a name="alerts"></a>Beskeder

Fanen **Beskeder indeholder** en liste over beskeder, der er knyttet til brugerkontoen. Denne liste er en filtreret visning af beskedkøen [og viser](alerts-queue.md) beskeder, hvor brugerkonteksten er den valgte brugerkonto, den dato, hvor den seneste aktivitet blev registreret, en kort beskrivelse af beskeden, den enhed, der er knyttet til beskeden, beskedens alvorsgrad, beskedens status i køen, og hvem der har fået tildelt beskeden.

### <a name="observed-in-organization"></a>Observeret i organisation

Fanen  Observeret i organisation gør det muligt at angive et datointerval for at få vist en liste over enheder, hvor denne bruger er blevet observeret logget på, den hyppigste og de mest hyppigt anvendte brugerkonto for hver af disse enheder samt det samlede antal observerede brugere på hver enhed.

Hvis du vælger et element på tabellen Observeret i organisation, udvides elementet, hvilket viser flere oplysninger om enheden. Direkte valg af et link i et element sender dig til den tilsvarende side.

## <a name="search-for-specific-user-accounts"></a>Søge efter bestemte brugerkonti

1. Vælg **Bruger** i **rullemenuen** Søgelinje.
2. Angiv brugerkontoen i **søgefeltet** .
3. Klik på søgeikonet, eller tryk på **Enter**.

Der vises en liste over brugere, der svarer til forespørgselsteksten. Du kan se brugerkontoens domæne og navn, hvornår brugerkontoen sidst blev set, og det samlede antal enheder, den er blevet observeret logget på inden for de seneste 30 dage.

Du kan filtrere resultaterne efter følgende tidsperioder:

- 1 dag
- 3 dage
- 7 dage
- 30 dage
- 6 måneder

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser Microsoft Defender for Endpoint i køen vigtige beskeder](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint vigtige beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for Endpoint vigtige beskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en Defender for Endpoint-besked](investigate-files.md)
- [Undersøg enhederne på listen Defender for Endpoint-enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Defender for Endpoint-besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Defender for Endpoint-besked](investigate-domain.md)
