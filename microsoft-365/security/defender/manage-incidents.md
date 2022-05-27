---
title: Administrer hændelser i Microsoft 365 Defender
description: Få mere at vide om, hvordan du tildeler, opdaterer status,
keywords: hændelse, hændelser, analysere, svar, beskeder, korrelerede beskeder, tildele, opdatere, status, administrere, klassificering, microsoft, 365, m365
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
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 9aa293a84f3bdca6988b1bf8437906f8b1cfbd39
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739987"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Administrer hændelser i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Administration af hændelser er afgørende for at sikre, at hændelser navngives, tildeles og mærkes for at optimere tiden i din hændelsesarbejdsproces og hurtigere indeholde og håndtere trusler.

Du kan administrere hændelser fra **hændelser & beskeder > Hændelser** på hurtig start af Microsoft 365 Defender-portalen ([security.microsoft.com](https://security.microsoft.com)). Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Siden Hændelser på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Her er de måder, du kan administrere dine hændelser på:

- [Rediger hændelsesnavnet](#edit-the-incident-name)
- [Tilføj hændelseskoder](#add-incident-tags)
- [Tildel hændelsen til en brugerkonto](#assign-an-incident)
- [Løs dem](#resolve-an-incident)
- [Angiv klassificeringen](#specify-the-classification)
- [Tilføj kommentarer](#add-comments)

Du kan administrere hændelser fra ruden **Administrer hændelse** for en hændelse. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Ruden Administrer hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Du kan få vist denne rude via linket **Administrer hændelse** på:

- Ruden Egenskaber for en hændelse i hændelseskøen.
- **Oversigtsside** for en hændelse.

I de tilfælde, hvor du vil flytte beskeder fra én hændelse til en anden, kan du også gøre det fra fanen **Beskeder** og dermed oprette en større eller mindre hændelse, der indeholder alle relevante beskeder.

## <a name="edit-the-incident-name"></a>Rediger hændelsesnavnet

Microsoft 365 Defender tildeler automatisk et navn baseret på beskedattributter, f.eks. antallet af berørte slutpunkter, berørte brugere, registreringskilder eller kategorier. Dette giver dig mulighed for hurtigt at forstå omfanget af hændelsen. Eksempel: *Hændelse med flere faser på flere slutpunkter rapporteret af flere kilder.*

Du kan redigere navnet på hændelsen fra feltet **Hændelsesnavn** i ruden **Administrer hændelse** .

> [!NOTE]
> Hændelser, der fandtes før udrulningen af funktionen til automatisk navngivning af hændelser, bevarer deres navn.

## <a name="add-incident-tags"></a>Tilføj hændelseskoder

Du kan føje brugerdefinerede mærker til en hændelse, f.eks. for at markere en gruppe af hændelser med en fælles egenskab. Du kan senere filtrere hændelseskøen for alle hændelser, der indeholder et bestemt mærke.

Når du begynder at skrive, har du mulighed for at vælge på en liste over tidligere anvendte og valgte mærker.

## <a name="assign-an-incident"></a>Tildel en hændelse

Hvis en hændelse endnu ikke er blevet tildelt, kan du markere afkrydsningsfeltet **Tildel til** og angive brugerkontoen. Hvis du vil tildele en hændelse igen, skal du fjerne den aktuelle tildelingskonto ved at vælge "x" ud for kontonavnet og derefter markere feltet **Tildel til** . Tildeling af ejerskab for en hændelse tildeler det samme ejerskab til alle de beskeder, der er knyttet til den.

Du kan få en liste over hændelser, der er tildelt dig, ved at filtrere hændelseskøen. 

1. Vælg **Filtre** i hændelseskøen.
2. I afsnittet **Hændelsestildeling** skal du rydde **Vælg alle** og vælge **Tildelt til mig**.
3. Vælg **Anvend**, og luk derefter ruden **Filtre** .

Du kan derefter gemme den resulterende URL-adresse i din browser som et bogmærke for hurtigt at se listen over hændelser, der er tildelt dig.

## <a name="resolve-an-incident"></a>Løs en hændelse

Hvis hændelsen er blevet afhjælpet, skal du vælge **Løs hændelse** for at flytte til/fra-knappen til højre. Bemærk, at løsning af en hændelse også løser alle linkede og aktive beskeder, der er relateret til hændelsen.

En hændelse, der ikke er løst, vises som **Aktiv**.

## <a name="specify-the-classification"></a>Angiv klassificeringen

I feltet **Klassificering** skal du angive, om hændelsen er:

- **Ikke angivet** (standard).
- **Sand positiv** med en form for trussel. Brug denne klassificering til hændelser, der nøjagtigt angiver en reel trussel. Angivelse af trusselstypen hjælper dit sikkerhedsteam med at se trusselsmønstre og reagere for at forsvare din organisation mod dem.
- **Oplysende, forventet aktivitet** med en aktivitetstype. Brug indstillingerne i denne kategori til at klassificere hændelser for sikkerhedstests, rød teamaktivitet og forventet usædvanlig funktionsmåde fra apps og brugere, der er tillid til.
- **Falsk positiv** for typer af hændelser, som du finder, kan ignoreres, fordi de teknisk set er unøjagtige eller vildledende.

Klassificering af hændelser og angivelse af deres status og type hjælper med at justere Microsoft 365 Defender for at give bedre registreringsbestemmelse over tid.

Se denne korte video for at få mere at vide om, hvordan du bruger klassificering til at øge effektiviteten af triage.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LHJq]

## <a name="add-comments"></a>Tilføj kommentarer

Du kan føje flere kommentarer til en hændelse med feltet **Kommentar** . Hver kommentar føjes til de historiske hændelser i hændelsen. Du kan se kommentarerne og historikken for en hændelse fra linket **Kommentarer og historik** på siden **Oversigt** .

## <a name="next-steps"></a>Næste trin

I forbindelse med nye hændelser skal du starte din [undersøgelse](investigate-incidents.md).

I forbindelse med igangværende hændelser skal du fortsætte din [undersøgelse](investigate-incidents.md).

Udfør en [gennemgang efter hændelsen](first-incident-post.md) for løste hændelser.

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Undersøg hændelser](investigate-incidents.md)
