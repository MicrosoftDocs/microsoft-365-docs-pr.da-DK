---
title: Svar på webtrusler i Microsoft Defender for Endpoint
description: Svar på beskeder, der er relateret til skadelige og uønskede websteder. Forstå, hvordan beskyttelse mod webtrusler giver slutbrugerne besked via deres webbrowsere, og Windows meddelelser
keywords: webbeskyttelse, beskyttelse mod webtrusler, webbrowsing, beskeder, svar, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Edge, Internet Explorer, Chrome, Firefox, webbrowser, meddelelser, slutbrugere, Windows-beskeder, blokeringsside,
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
ms.openlocfilehash: 3a7202c6e522441ecbbfd738d3533a242c966f8c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467527"
---
# <a name="respond-to-web-threats"></a>Svar på webtrusler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Webbeskyttelse i Microsoft Defender for Endpoint giver dig mulighed for effektivt at undersøge og reagere på beskeder, der er relateret til ondsindede websteder og websteder i din liste over brugerdefinerede indikatore.

## <a name="view-web-threat-alerts"></a>Få vist beskeder om webtrusler

Microsoft Defender for Endpoint genererer følgende beskeder [om ondsindet](manage-alerts.md) eller mistænkelig webaktivitet:

- **Mistænkelig forbindelse** blokeret af netværksbeskyttelse: Denne advarsel genereres, når et forsøg på at få adgang til et skadeligt websted eller et websted på  din liste over brugerdefinerede indikatorer stoppes af netværksbeskyttelse i *blokeringstilstand*
- **Mistænkelig forbindelse, der registreres** af netværksbeskyttelse: Denne advarsel genereres, når et forsøg på at få adgang til et skadeligt websted eller et websted på listen over brugerdefinerede indikatore registreres af netværksbeskyttelse i *overvågningstilstand*

Hver besked indeholder følgende oplysninger:

- Enhed, der forsøgte at få adgang til det blokerede websted
- Program, der bruges til at sende webanmodningen
- Ondsindet URL-adresse eller URL-adresse på listen over brugerdefinerede indikatorer
- Anbefalede handlinger for svarere

:::image type="content" source="images/wtp-alert.png" alt-text="Beskeden, der er relateret til beskyttelse mod webtrusler" lightbox="images/wtp-alert.png":::

> [!NOTE]
> For at reducere mængden af beskeder konsoliderer Microsoft Defender for Endpoint webtrusselsregistreringer for det samme domæne på den samme enhed hver dag til en enkelt besked. Der genereres kun én besked, som tælles med [i rapporten om webbeskyttelse](web-protection-monitoring.md).

## <a name="inspect-website-details"></a>Undersøg webstedsoplysninger

Du kan dykke dybere ved at vælge URL-adressen eller domænet for webstedet i beskeden. Dette åbner en side om den pågældende URL-adresse eller det pågældende domæne med forskellige oplysninger, herunder:

- Enheder, der har forsøgt at få adgang til webstedet
- Hændelser og beskeder, der er relateret til webstedet
- Hvor ofte webstedet blev set under begivenheder i organisationen

  :::image type="content" source="images/wtp-website-details.png" alt-text="Detaljesiden for domæne- eller URL-enhed" lightbox="images/wtp-website-details.png":::

[Få mere at vide om URL-adresser eller domæneenhedssider](investigate-domain.md)

## <a name="inspect-the-device"></a>Undersøg enheden

Du kan også kontrollere den enhed, der forsøgte at få adgang til en blokeret URL-adresse. Hvis du vælger navnet på enheden på påmindelsessiden, åbnes en side med omfattende oplysninger om enheden.

[Få mere at vide om enhedsenhedssider](investigate-machines.md)

## <a name="web-browser-and-windows-notifications-for-end-users"></a>Webbrowser og meddelelser Windows til slutbrugere

Med webbeskyttelse i Microsoft Defender for Endpoint, vil dine slutbrugere blive forhindret i at besøge ondsindede eller uønskede websteder Microsoft Edge andre browsere. Da blokering udføres af [netværksbeskyttelse](network-protection.md), vises der en generisk fejl fra webbrowseren. De vil også se en meddelelse fra Windows.

:::image type="content" source="images/wtp-browser-blocking-page.png" alt-text="Meddelelsen Microsoft Edge en 403-fejl, og meddelelsen Windows besked" lightbox="images/wtp-browser-blocking-page.png":::

*Webtrusler blokeret på Microsoft Edge*

:::image type="content" source="images/wtp-chrome-browser-blocking-page.png" alt-text="Chrome-webbrowseren viser en advarsel om sikker forbindelse, og meddelelsen Windows meddelelse" lightbox="images/wtp-chrome-browser-blocking-page.png":::
*Webtrussel blokeret i Chrome*

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over webbeskyttelse](web-protection-overview.md)
- [Filtrering af webindhold](web-content-filtering.md)
- [Webtrusselsbeskyttelse](web-threat-protection.md)
- [Overvåge websikkerhed](web-protection-monitoring.md)
