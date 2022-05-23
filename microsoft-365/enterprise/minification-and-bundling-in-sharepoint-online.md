---
title: Minification og bundling i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Få mere at vide om, hvordan du bruger teknikker til minificering og bundtning med Web Essentials for at reducere HTTP-anmodninger og den tid, det tager at indlæse sider i SharePoint Online.
ms.openlocfilehash: b02cf095b1d7f05a82df1cf98a590ff762453f8a
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637621"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minification og bundling i SharePoint Online

I denne artikel beskrives det, hvordan du bruger minification- og bundlingteknikker med Web Essentials til at reducere antallet af HTTP-anmodninger og reducere den tid, det tager at indlæse sider i SharePoint Online.
  
Når du tilpasser dit websted, kan du ende med at føje et stort antal ekstra filer til serveren for at understøtte tilpasningen. Tilføjelse af ekstra JavaScript, CSS og billeder øger antallet af HTTP-anmodninger til serveren, hvilket igen øger den tid, det tager at vise en webside. Hvis du har flere filer af samme type, kan du bundte disse filer for at gøre download af disse filer hurtigere.
  
I forbindelse med JavaScript- og CSS-filer kan du også bruge en tilgang, der kaldes minification, hvor du reducerer den samlede størrelse af filer ved at fjerne mellemrum og andre tegn, der ikke er nødvendige.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minification og bundling Af JavaScript- og CSS-filer med Web Essentials

Du kan bruge tredjepartssoftware, f.eks. Web Essentials, til at bundte CSS- og JavaScript-filer.
  
> [!IMPORTANT]
> Web Essentials er et tredjepartsprojekt, der er baseret på åben kildekode. Softwaren er en udvidelse til Visual Studio 2012 og Visual Studio 2013 og understøttes ikke af Microsoft. Hvis du vil hente Web Essentials, skal du besøge webstedet på [Web Essentials 2012](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebEssentials2012).
  
Web Essentials tilbyder to former for bundtning:
 
- .bundle: til CSS- og JavaScript-filer
- .sprite: for billeder (kun tilgængelig i Visual Studio 2013)

Du kan bruge Web Essentials, hvis du har en eksisterende funktion med nogle brandingelementer, der refereres til på en brugerdefineret masterside, f.eks.:
  
![Skærmbillede af brandelement på brugerdefineret masterside.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Sådan opretter du et TE000127218- og CSS-bundt i Web Essentials
  
1. Vælg de filer, du vil medtage i pakken, i Løsningsoversigt i Visual Studio.
2. Højreklik på de markerede filer, og vælg derefter **Web Essentials** \> **Opret JavaScript-bundtfil** i genvejsmenuen. Eksempel:

    ![Skærmbillede, der viser menupunkterne for Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Visning af resultaterne af bundtning af JavaScript- og CSS-filer

Når du opretter et JavaScript- og CSS-bundt, opretter Web Essentials en XML-fil, der kaldes en opskriftsfil, der identificerer JavaScript- og CSS-filerne samt nogle andre konfigurationsoplysninger:
  
![Skærmbillede af JavaScript- og CSS-opskriftsfilen.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Hvis minify-flaget er angivet til true i bundlingopskriften, reduceres filerne desuden i størrelse og bundtet sammen. Det betyder, at der blev oprettet nye, minificerede versioner af JavaScript-filerne, som du kan referere til på mastersiden.
  
![Skærmbillede af flaget Minify, der er angivet til sand.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Når du indlæser en side fra dit websted, kan du bruge udviklerværktøjerne fra din webbrowser, f.eks. Internet Explorer 11, til at se antallet af anmodninger, der er sendt til serveren, og hvor lang tid hver fil tog at indlæse.
  
Følgende figur er resultatet af indlæsning af JavaScript- og CSS-filerne før minification.
  
![Skærmbillede, der viser 80 elementer, der downloades.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Efter at have samlet CSS- og JavaScript-filerne samlet, tog antallet af anmodninger, der blev droppet til 74, og hver fil kun lidt længere tid end de oprindelige filer at downloade individuelt:
  
![Skærmbillede, der viser 74 elementer, der downloades.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Efter bundtning reduceres JavaScript-bundtfilen markant fra 815 KB til 365 KB:
  
![Skærmbillede, der viser reduceret downloadstørrelse.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Bundtning af billeder ved at oprette en billedprite

På samme måde som du bundter JavaScript- og CSS-filer, kan du kombinere mange små ikoner og andre almindelige billeder i et større sprite-ark og derefter bruge CSS til at afsløre de enkelte billeder. I stedet for at downloade hvert enkelt billede downloader brugerens webbrowser sprite-arket én gang og cachelagrer det derefter på den lokale computer. Dette forbedrer sidebelastningens ydeevne ved at skære ned på antallet af downloads og rundture til webserveren.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Sådan opretter du en billedsprite i Web Essentials**
  
1. Vælg de filer, du vil medtage i pakken, i Løsningsoversigt i Visual Studio.
2. Højreklik på de markerede filer, og vælg derefter **Web Essentials** \> **Opret billede i** genvejsmenuen. Eksempel:

    ![Skærmbillede, der viser, hvordan du opretter en billedprite.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Vælg en placering, hvor filen sprite skal gemmes. .sprite-filen er en XML-fil, der beskriver indstillingerne og filerne i sprite. Følgende tal viser et eksempel på en Sprite PNG-fil og dens tilsvarende .sprite XML-fil.

    ![Skærmbillede af en sprite-fil.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Skærmbillede af XML-filen sprite.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
