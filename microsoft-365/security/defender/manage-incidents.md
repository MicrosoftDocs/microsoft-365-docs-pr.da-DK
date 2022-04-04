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
ms.openlocfilehash: 14332b2787b59e2ef192741dc97e59a7c7cb5418
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499501"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Administrer hændelser i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Hændelsesstyring er afgørende for at sikre, at hændelser navngives, tildeles og mærkes for at optimere tiden i hændelsesarbejdsprocessen og hurtigere inddæmme og håndtere trusler.

Du kan administrere hændelser & **hændelser > hændelser** i hurtig start af Microsoft 365 Defender -[portalen (security.microsoft.com](https://security.microsoft.com)). Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Siden Hændelser i Microsoft 365 Defender portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Her er de måder, du kan administrere dine hændelser på:

- [Rediger hændelsens navn](#edit-the-incident-name)
- [Tilføje hændelsesmærker](#add-incident-tags)
- [Tildele hændelsen til en brugerkonto](#assign-an-incident)
- [Løs dem](#resolve-an-incident)
- [Angiv klassificeringen](#specify-the-classification)
- [Tilføj kommentarer](#add-comments)

Du kan administrere hændelser fra **ruden Administrer hændelse** for en hændelse. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Ruden Administrer hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Du kan få vist denne rude **via linket Administrer** hændelse på:

- Ruden Egenskaber for en hændelse i hændelseskøen.
- **Oversigtsside** for en hændelse.

I tilfælde, hvor du vil flytte beskeder fra én hændelse til en anden, kan du også gøre det fra fanen  Vigtige beskeder, hvilket opretter en større eller mindre hændelse, der omfatter alle relevante beskeder.

## <a name="edit-the-incident-name"></a>Rediger hændelsens navn

Microsoft 365 Defender tildeler automatisk et navn baseret på beskedattributter som f.eks. antallet af slutpunkter, der påvirkes, brugere, der påvirkes, registreringskilder eller kategorier. Dette giver dig mulighed for hurtigt at forstå omfanget af hændelsen. For eksempel: *Hændelser i flere faser på flere slutpunkter rapporteret af flere kilder.*

Du kan redigere hændelsens navn i **feltet Hændelsesnavn** i **ruden Administrer** hændelse.

> [!NOTE]
> Hændelser, der fandtes før rullen af den automatiske navngivningsfunktion for hændelser, bevarer deres navn.

## <a name="add-incident-tags"></a>Tilføje hændelsesmærker

Du kan føje brugerdefinerede mærker til en hændelse, f.eks. for at markere en gruppe af hændelser med en fælles egenskab. Du kan senere filtrere hændelseskøen for alle hændelser, der indeholder et bestemt mærke.

Når du begynder at skrive, har du mulighed for at vælge på en liste over tidligere anvendte og valgte mærker.

## <a name="assign-an-incident"></a>Tildel en hændelse

Hvis en hændelse endnu ikke er blevet tildelt, kan du **markere feltet** Tildel til og angive brugerkontoen. Hvis du vil tildele en hændelse igen, skal du fjerne den aktuelle opgavekonto ved at vælge "x" ud for kontonavnet og derefter markere feltet **Tildel** til. Når du tildeler ejerskabet af en hændelse, tildeles det samme ejerskab til alle de beskeder, der er knyttet til den.

Du kan få en liste over hændelser, der er tildelt dig, ved at filtrere hændelseskøen. 

1. Vælg **Filtre fra hændelseskøen**.
2. i sektionen **Hændelsestildeling** skal du fjerne **markeringen i Markér alt** og **vælge Tildelt til mig**.
3. Vælg **Anvend**, og luk derefter **ruden** Filtre.

Du kan derefter gemme den resulterende URL-adresse i din browser som et bogmærke for hurtigt at se listen over hændelser, der er tildelt dig.

## <a name="resolve-an-incident"></a>Løs en hændelse

Hvis hændelsen er løst, skal du vælge **Løs hændelse** for at flytte til/fra-knappen til højre. Bemærk, at løsning af en hændelse også løser alle sammenkædede og aktive beskeder, der er relateret til hændelsen.

En hændelse, der ikke er løst, vises som **Aktiv**.

## <a name="specify-the-classification"></a>Angiv klassificeringen

Fra feltet **Klassificering** angiver du, om hændelsen er:

- **Ikke angivet** (standard).
- **Sand positiv** med en type af trussel. Brug denne klassificering til hændelser, der præcist angiver en reel trussel. Hvis du angiver trusselstypen, kan dit sikkerhedsteam se trusselsmønstre og beskytte din organisation mod dem.
- **Informationel, forventet aktivitet** med en type aktivitet. Brug indstillingerne i denne kategori til at klassificere hændelser til sikkerhedstests, rød teamaktivitet og forventet usædvanlig adfærd fra pålidelige apps og brugere.
- **Falsk positiv for** typer hændelser, som du bestemmer, kan ignoreres, fordi de er teknisk unøjagtige eller vildledende.

Klassificering af hændelser og angivelse af deres status og type hjælper med at finjustere, Microsoft 365 Defender der med tiden kan sikre en bedre registrering.

## <a name="add-comments"></a>Tilføj kommentarer

Du kan føje flere kommentarer til en hændelse med **feltet** Kommentar. Hver kommentar bliver føjet til de historiske hændelser for hændelsen. Du kan se kommentarerne og historikken for en hændelse via **linket Kommentarer** og historik på **siden Oversigt** .

## <a name="next-steps"></a>Næste trin

Start din undersøgelse for nye [hændelser](investigate-incidents.md).

Fortsæt undersøgelsen for at få in [process-hændelser](investigate-incidents.md).

For løste hændelser skal du udføre [en gennemgang efter hændelsen](first-incident-post.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Undersøg hændelser](investigate-incidents.md)
