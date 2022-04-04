---
title: Undersøg Microsoft Defender for Endpoint filer
description: Brug undersøgelsesmulighederne til at få oplysninger om filer, der er knyttet til beskeder, funktionsmåder eller hændelser.
keywords: undersøgelse, undersøgelse, fil, ondsindet aktivitet, angrebsmotation, dybdegående analyse, dybdegående analyserapport
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
ms.openlocfilehash: 0cb7523036d6660d4b5556fdfd07e443a359b208
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466229"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Undersøg en fil, der er knyttet Microsoft Defender for Endpoint besked

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Undersøg oplysningerne om en fil, der er knyttet til en bestemt besked, funktionsmåde eller hændelse for at finde ud af, om filen udviser ondsindede aktiviteter, identificer angrebsmotationen og forstå det potentielle omfang af misligholdelsen.

Der er mange måder, hvorpå du kan få adgang til den detaljerede profilside for en bestemt fil. Du kan f.eks. bruge søgefunktionen, klikke på et link fra beskedprocestræet **,** hændelsesdiagrammet **,** tidslinjen for artefakter eller vælge en begivenhed, der er angivet på **enhedens tidslinje**.

Når du er på den detaljerede profilside, kan du skifte mellem de nye og gamle sidelayout ved at slå **ny filside til**. I resten af denne artikel beskrives det nyere sidelayout.

Du kan få oplysninger fra de følgende afsnit i filvisningen:

- Filoplysninger, registrering af malware, filer, der fungerer som filer
- Dybdegående analyse
- Beskeder
- Observeret i organisation
- Dybdegående analyse
- Filnavne

Du kan også gøre noget på en fil fra denne side.

## <a name="file-actions"></a>Filhandlinger

Langs toppen af profilsiden over filinformationskortene. Handlinger, du kan udføre her, omfatter:

- Stop og karantæne
- Indikator for tilføj/rediger
- Download fil
- Kontakt en trusselsekspert
- Handlingscenter

Du kan finde flere oplysninger om disse handlinger [under Reagere på en fil](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Filoplysninger, registrering af malware og filer, der er ved at blive fjernet

Filoplysninger, hændelse, registrering af malware og filnetværkskort viser forskellige attributter om filen.

Du får vist oplysninger som f.eks filens MD5, det samlede antal virusregistreringsforhold og registrering af Microsoft Defender-AV, hvis det er tilgængeligt, og filens funktioner.

Kortet med filen blev vist, hvor filen blev set på enheder i organisationen og i hele verden.

> [!NOTE]
> Forskellige brugere kan se forskellige værdier i enhederne *i organisationen på* filens skærmkort. Dette skyldes, at kortet viser oplysninger, der er baseret på det RBAC-omfang, en bruger har. Det vil sige, at hvis en bruger har fået tildelt synlighed på et bestemt sæt enheder, vil brugeren kun kunne se filens organisatoriske hjælpemidler på disse enheder.

:::image type="content" source="images/atp-file-information.png" alt-text="Filoplysningerne" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>Beskeder

Fanen **Beskeder indeholder** en liste over beskeder, der er knyttet til filen. Denne liste dækker mange af de samme oplysninger som køen Beskeder med undtagelse af enhedsgruppen, hvis der er nogen, den pågældende enhed tilhører. Du kan vælge, hvilke typer oplysninger der vises, ved at vælge **Tilpas** kolonner på værktøjslinjen over kolonneoverskrifterne.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="Beskederne, der er relateret til filsektionen" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>Observeret i organisation

Fanen **Observeret i organisation gør** det muligt at angive et datointerval for at se, hvilke enheder der er blevet observeret med filen.

> [!NOTE]
> Denne fane viser et maksimalt antal af 100 enheder. Hvis du _vil se_ alle enheder med filen, skal du eksportere fanen til en CSV-fil ved  at vælge Eksportér i handlingsmenuen over fanens kolonneoverskrifter.

:::image type="content" source="images/atp-observed-machines.png" alt-text="De seneste observerede enheder med filen" lightbox="images/atp-observed-machines.png":::

Brug skyderen eller områdevælgeren til hurtigt at angive en tidsperiode, du vil kontrollere for hændelser, der involverer filen. Du kan angive et tidsvindue så lille som en enkelt dag. Dette giver dig mulighed for kun at se filer, der kommunikerede med den pågældende IP-adresse på det pågældende tidspunkt, hvilket markant reducerer unødvendig rulning og søgning.

## <a name="deep-analysis"></a>Dybdegående analyse

Fanen **Dybdegående** analyse giver dig mulighed [for](respond-file-alerts.md#deep-analysis) at sende filen til dybdegående analyse og afdække flere oplysninger om filens funktionsmåde samt den effekt, den har i din organisation. Når du har indsendt filen, vises den dybdegående analyserapport på denne fane, når resultaterne er tilgængelige. Hvis en dybdegående analyse ikke fandt noget, vil rapporten være tom, og pladsen til resultaterne forbliver tom.

:::image type="content" source="images/submit-file.png" alt-text="Fanen Dybdegående analyse" lightbox="images/submit-file.png":::

## <a name="file-names"></a>Filnavne

Fanen **Filnavne** viser alle de navne, som filen er blevet observeret til brug i din organisation.

:::image type="content" source="images/atp-file-names.png" alt-text="Fanen Filnavne" lightbox="images/atp-file-names.png":::

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser Microsoft Defender for Endpoint køen](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint vigtige beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for Endpoint vigtige beskeder](investigate-alerts.md)
- [Undersøg enhederne Microsoft Defender for Endpoint listen Over enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet Microsoft Defender for Endpoint besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet Microsoft Defender for Endpoint besked](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender for Endpoint](investigate-user.md)
- [Udføre svarhandlinger på en fil](respond-file-alerts.md)
