---
title: Undersøg Microsoft Defender for Endpoint filer
description: Brug undersøgelsesindstillingerne til at få oplysninger om filer, der er knyttet til beskeder, funktionsmåder eller hændelser.
keywords: undersøg, undersøgelse, fil, ondsindet aktivitet, angrebsmotivation, dyb analyse, detaljeret analyserapport
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
ms.openlocfilehash: c1f6fa058715f831b1c8ba594bf1604ad92e9ed2
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669358"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Undersøg en fil, der er knyttet til en Microsoft Defender for Endpoint besked

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Undersøg detaljerne i en fil, der er knyttet til en bestemt besked, funktionsmåde eller hændelse, for at finde ud af, om filen udviser skadelige aktiviteter, identificere angrebsmotivationen og forstå det potentielle omfang af sikkerhedsbrud.

Der er mange måder at få adgang til den detaljerede profilside i en bestemt fil på. Du kan f.eks. bruge søgefunktionen, klikke på et link fra **træet for beskedproces**, **hændelsesgraf**, **artefakttidslinje** eller vælge en hændelse, der er angivet på **enhedens tidslinje**.

Når du er på den detaljerede profilside, kan du skifte mellem det nye og det gamle sidelayout ved at slå **den nye filside** til. I resten af denne artikel beskrives det nyere sidelayout.

Du kan hente oplysninger fra følgende afsnit i filvisningen:

- Filoplysninger, Registrering af malware, Filprævalens
- Fil-PE-metadata (hvis de findes)
- Dybdegående analyse
- Beskeder
- Observeret i organisationen
- Dybdegående analyse
- Filnavne

Du kan også udføre handlinger på en fil fra denne side.

## <a name="file-actions"></a>Filhandlinger

Øverst på profilsiden over filoplysningskortene. De handlinger, du kan udføre her, omfatter:

- Stop og sæt karantæne
- Tilføj/rediger indikator
- Download fil
- Kontakt en trusselsekspert
- Handlingscenter

Du kan få flere oplysninger om disse handlinger under [Udfør svarhandling på en fil](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Filoplysninger, registrering af malware og filforekomst

Fildetaljer, hændelse, registrering af malware og filprævalenskort viser forskellige attributter om filen.

Du får vist oplysninger som f.eks. filens MD5, registreringsforholdet virustotal og Microsoft Defender AV-registrering, hvis det er tilgængeligt, og filens prævalens.

Kortet til prævalens af filer viser, hvor filen blev set på enheder i organisationen og i hele verden. Du kan nemt pivotere til den første og sidste enhed, hvor filen blev set på, og fortsætte undersøgelsen på enhedens tidslinje. 

> [!NOTE]
> Forskellige brugere kan se forskellige værdier i *afsnittet enheder i organisationen* på filprævalenskortet. Det skyldes, at kortet viser oplysninger baseret på det RBAC-område, som en bruger har. Det betyder, at hvis en bruger er blevet tildelt synlighed på et bestemt sæt enheder, kan vedkommende kun se filens organisationsprævalens på disse enheder.

:::image type="content" source="images/atp-file-information.png" alt-text="Filoplysningerne" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>Beskeder

Fanen **Beskeder** indeholder en liste over beskeder, der er knyttet til filen, samt den hændelse, som beskeden er knyttet til. Denne liste dækker mange af de samme oplysninger som beskedkøen, bortset fra enhedsgruppen, hvis der er nogen, den berørte enhed tilhører. Du kan vælge, hvilken type oplysninger der skal vises, ved at vælge **Tilpas kolonner** på værktøjslinjen over kolonneoverskrifterne.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="De beskeder, der er relateret til filsektionen" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>Observeret i organisationen

Under fanen **Observeret i organisationen** kan du angive et datointerval for at se, hvilke enheder der er blevet observeret med filen.

> [!NOTE]
> Under denne fane vises der maksimalt 100 enheder. Hvis du vil se _alle_ enheder med filen, skal du eksportere fanen til en CSV-fil ved at vælge **Eksportér** i handlingsmenuen over fanens kolonneoverskrifter.

:::image type="content" source="images/atp-observed-machines.png" alt-text="De seneste observerede enheder med filen" lightbox="images/atp-observed-machines.png":::

Brug skyderen eller områdevælgeren til hurtigt at angive en tidsperiode, som du vil kontrollere for hændelser, der involverer filen. Du kan få hjælp af beskedangivelsen i hele intervallet. Du kan angive et tidsvindue, der er så lille som en enkelt dag. Dette giver dig mulighed for kun at se filer, der kommunikerede med den pågældende IP-adresse på det pågældende tidspunkt, hvilket reducerer unødvendig rulning og søgning drastisk.

## <a name="deep-analysis"></a>Dybdegående analyse

Under fanen **Detaljeret analyse** kan du [indsende filen til detaljeret analyse for](respond-file-alerts.md#deep-analysis) at få vist flere oplysninger om filens funktionsmåde samt den effekt, den har i din organisation. Når du har sendt filen, vises den detaljerede analyserapport under denne fane, når resultaterne er tilgængelige. Hvis der ikke blev fundet noget i den dybe analyse, er rapporten tom, og resultatområdet forbliver tomt.

:::image type="content" source="images/submit-file.png" alt-text="Fanen Dyb analyse" lightbox="images/submit-file.png":::

## <a name="file-names"></a>Filnavne

Under fanen **Filnavne** vises alle de navne, som filen er blevet observeret til brug i din organisation.

:::image type="content" source="images/atp-file-names.png" alt-text="Fanen Filnavne" lightbox="images/atp-file-names.png":::

## <a name="action-center"></a>Handlingscenter

**I Løsningscenter** vises handlingscenteret filtreret efter en bestemt fil, så du kan se ventende handlinger og oversigten over handlinger, der er udført på filen.

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser køen Microsoft Defender for Endpoint](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for Endpoint beskeder](investigate-alerts.md)
- [Undersøg enheder på listen over Microsoft Defender for Endpoint enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender for Endpoint](investigate-user.md)
- [Udfør svarhandlinger på en fil](respond-file-alerts.md)
