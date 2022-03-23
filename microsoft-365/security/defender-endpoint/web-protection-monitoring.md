---
title: Overvågning af sikkerhed ved webbrowsing i Microsoft Defender til Slutpunkt
description: Brug webbeskyttelse i Microsoft Defender til Slutpunkt til at overvåge sikkerheden for webbrowsing
keywords: webbeskyttelse, beskyttelse mod webtrusler, webbrowsing, overvågning, rapporter, kort, domæneliste, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Edge, Internet Explorer, Chrome, Firefox, webbrowser
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6d10354f68dd5ba26db7f4260425559167c8888c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591191"
---
# <a name="monitor-web-browsing-security"></a>Overvåge sikkerhed ved webbrowsing

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Webbeskyttelse gør det muligt at overvåge organisationens sikkerhed ved hjælp af webbrowsing via **rapporter under rapporter > Webbeskyttelse** i Microsoft 365 Defender portal. Rapporten indeholder kort, der giver statistik for registrering af webtrusler.

- **Registreringer af webtrusler over** tid – Dette mest populære kort viser antallet af webtrusler registreret efter type i den valgte tidsperiode (Seneste 30 dage, Seneste 3 måneder, Seneste 6 måneder)

  :::image type="content" alt-text="Billede af kortet, der viser registreringer af beskyttelse mod webtrusler over tid." source="images/wtp-blocks-over-time.png" lightbox="images/wtp-blocks-over-time.png":::

- **Oversigt over webtrusler** – Dette kort viser de samlede registreringer af webtrusler inden for de seneste 30 dage, som viser fordelingen på tværs af de forskellige typer webtrusler. Når du vælger et udsnit, åbnes listen over de domæner, der blev fundet med ondsindede eller uønskede websteder.

  :::image type="content" alt-text="Billede af kortet, der viser oversigt over beskyttelse mod webtrusler." source="images/wtp-summary.png" lightbox="images/wtp-summary.png":::

> [!NOTE]
> Det kan tage op til 12 timer, før en blok afspejles i kortene eller domænelisten.

## <a name="types-of-web-threats"></a>Typer af webtrusler

Webbeskyttelse kategoriserer skadelige og uønskede websteder som:

- **Phishing** – websteder, der indeholder forfalskede webformularer og andre phishingsmekanismer, der er designet til at narre brugere til at dele legitimationsoplysninger og andre følsomme oplysninger
- **Ondsindet** – websteder, der hoster malware og udnytter kode
- **Brugerdefineret** indikator – websteder, hvis URL-adresser eller domæner du har føjet til din liste med [brugerdefinerede indikator for](manage-indicators.md) blokering

## <a name="view-the-domain-list"></a>Få vist listen over domæner

Vælg en bestemt **webtrusselskategori** på **oversigtskortet for webtrusler** for at åbne siden Domæner. Denne side viser listen over domænerne under den pågældende trusselskategori. Siden indeholder følgende oplysninger for hvert domæne:

- **Adgangsantal** – antal anmodninger om URL-adresser i domænet
- **Blokke** – antallet af gange, anmodninger blev blokeret
- **Adgangstendens** – ændring i antallet af adgangsforsøg
- **Trusselskategori** – typen af webtrussel
- **Enheder** – antal enheder med adgangsforsøg

Vælg et domæne for at få vist listen over enheder, der har forsøgt at få adgang til URL-adresser for det pågældende domæne, og listen over URL-adresser.

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over webbeskyttelse](web-protection-overview.md)
- [Filtrering af webindhold](web-content-filtering.md)
- [Webtrusselsbeskyttelse](web-threat-protection.md)
- [Svar på webtrusler](web-protection-response.md)
