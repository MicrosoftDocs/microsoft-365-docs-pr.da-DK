---
title: Undersøg Microsoft Defender for slutpunktsfiler
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
ms.openlocfilehash: 6f93a5ec90404ca28fd47d4115a8ebf8d488216e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63603104"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Undersøg en fil, der er knyttet til en besked om Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

![Billede af filoplysninger.](images/atp-file-information.png)

## <a name="alerts"></a>Beskeder

Fanen **Beskeder indeholder** en liste over beskeder, der er knyttet til filen. Denne liste dækker mange af de samme oplysninger som køen Beskeder med undtagelse af enhedsgruppen, hvis der er nogen, den pågældende enhed tilhører. Du kan vælge, hvilke typer oplysninger der vises, ved at vælge **Tilpas** kolonner på værktøjslinjen over kolonneoverskrifterne.

![Billede af beskeder, der er relateret til filsektionen.](images/atp-alerts-related-to-file.png)

## <a name="observed-in-organization"></a>Observeret i organisation

Fanen **Observeret i organisation gør** det muligt at angive et datointerval for at se, hvilke enheder der er blevet observeret med filen.

> [!NOTE]
> Denne fane viser et maksimalt antal af 100 enheder. Hvis du _vil se_ alle enheder med filen, skal du eksportere fanen til en CSV-fil ved  at vælge Eksportér i handlingsmenuen over fanens kolonneoverskrifter.

![Billede af den senest observerede enhed med filen.](images/atp-observed-machines.png)

Brug skyderen eller områdevælgeren til hurtigt at angive en tidsperiode, du vil kontrollere for hændelser, der involverer filen. Du kan angive et tidsvindue så lille som en enkelt dag. Dette giver dig mulighed for kun at se filer, der kommunikerede med den pågældende IP-adresse på det pågældende tidspunkt, hvilket markant reducerer unødvendig rulning og søgning.

## <a name="deep-analysis"></a>Dybdegående analyse

Fanen **Dybdegående** analyse giver dig mulighed [for](respond-file-alerts.md#deep-analysis) at sende filen til dybdegående analyse og afdække flere oplysninger om filens funktionsmåde samt den effekt, den har i din organisation. Når du har indsendt filen, vises den dybdegående analyserapport på denne fane, når resultaterne er tilgængelige. Hvis en dybdegående analyse ikke fandt noget, vil rapporten være tom, og pladsen til resultaterne forbliver tom.

![Billede af fanen dybdegående analyse.](images/submit-file.png)

## <a name="file-names"></a>Filnavne

Fanen **Filnavne** viser alle de navne, som filen er blevet observeret til brug i din organisation.

![Billede af fanen Filnavne.](images/atp-file-names.png)

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser køen for Microsoft Defender til slutpunkt](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint-beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for at få slutpunktsbeskeder](investigate-alerts.md)
- [Undersøg enhederne på listen Microsoft Defender for Slutpunktsenheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en besked om Microsoft Defender for Endpoint](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en besked om Microsoft Defender for Endpoint](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender til slutpunkt](investigate-user.md)
- [Udføre svarhandlinger på en fil](respond-file-alerts.md)
