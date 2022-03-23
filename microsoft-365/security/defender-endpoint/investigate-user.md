---
title: Undersøg en brugerkonto i Microsoft Defender til slutpunkt
description: Undersøg en brugerkonto for potentielt kompromitterede legitimationsoplysninger eller pivoter den tilknyttede brugerkonto under en undersøgelse.
keywords: undersøge, konto, bruger, brugerenhed, besked, Microsoft Defender til slutpunkt
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
ms.openlocfilehash: feebff9361f1504e94069e82a3de87a2e1d95c0c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592697"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>Undersøg en brugerkonto i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

- Brugerkontooplysninger, Microsoft Defender til identitetsbeskeder og enheder, rolle, logontype og andre oplysninger
- Oversigt over hændelserne og brugerens enheder
- Beskeder, der er relateret til denne bruger
- Observeret i organisationen (enheder, der er logget på)

![Billede af siden med oplysninger om brugerkontoenhed.](images/atp-user-details-view.png)

### <a name="user-details"></a>Brugeroplysninger

Ruden  Brugeroplysninger i venstre side indeholder oplysninger om brugeren, f.eks. relaterede åbne hændelser, aktive beskeder, SAM-navn, SID, Microsoft Defender til identitetsbeskeder, antal enheder, brugeren er logget på, hvornår brugeren først og sidst blev set, rolle- og logontyper. Afhængigt af de integrationsfunktioner, du har aktiveret, får du vist andre oplysninger. Hvis du f.eks. aktiverer Skype for Business-integration, vil du kunne kontakte brugeren fra portalen. Sektionen **Azure ATP-beskeder** indeholder et link, der gør det muligt at gå til siden Microsoft Defender for Identity, hvis du har aktiveret funktionen Microsoft Defender for Identity, og der er beskeder, der er relateret til brugeren. Siden Microsoft Defender for Identity giver flere oplysninger om beskederne.

> [!NOTE]
> Du skal aktivere integration på både Microsoft Defender for Identity og Defender for Endpoint for at bruge denne funktion. I Defender til Slutpunkt kan du aktivere denne funktion i avancerede funktioner. Du kan finde flere oplysninger om, hvordan du aktiverer avancerede funktioner, [under Slå avancerede funktioner til](advanced-features.md).

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

- [Få vist og organiser køen for Microsoft Defender for Endpoint Alerts](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint-beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for at få slutpunktsbeskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en Defender for Endpoint-besked](investigate-files.md)
- [Undersøg enhederne på listen Defender for Endpoint-enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Defender for Endpoint-besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Defender for Endpoint-besked](investigate-domain.md)
