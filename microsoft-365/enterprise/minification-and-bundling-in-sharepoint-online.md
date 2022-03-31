---
title: Minification og bundtning i SharePoint Online
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
description: Få mere at vide om, hvordan du bruger minification- og bundtningsteknikker med Web Essentials til at reducere HTTP-anmodninger og den tid, det tager at indlæse sider SharePoint Online.
ms.openlocfilehash: fabf690f523cabf67fe775bbd1a10251a477f633
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63601562"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minification og bundtning i SharePoint Online

I denne artikel beskrives det, hvordan du bruger minification- og bundtningsteknikker med Web Essentials til at reducere antallet af HTTP-anmodninger og reducere den tid, det tager at indlæse sider i SharePoint Online.
  
Når du tilpasser dit websted, kan ender med at tilføje et stort antal ekstra filer til serveren for at understøtte tilpasningen. Hvis du tilføjer ekstra JavaScript, CSS og billeder, øges antallet af HTTP-anmodninger til serveren, hvilket igen øger den tid, det tager at få vist en webside. Hvis du har flere filer af samme type, kan du bundte disse filer for at gøre det hurtigere at hente disse filer.
  
For JavaScript- og CSS-filer kan du også bruge en tilgang, der kaldes minification, hvor du reducerer den samlede størrelse af filer ved at fjerne mellemrum og andre tegn, der ikke er nødvendige.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minification og bundtning af JavaScript- og CSS-filer med Web Essentials

Du kan bruge tredjepartssoftware som f.eks. Web Essentials til at bundte CSS- og JavaScript-filer.
  
> [!IMPORTANT]
> Web Essentials er et open source-projekt fra tredjepart, som er communitybaseret. Softwaren er en udvidelse til Visual Studio 2012 og Visual Studio 2013 og understøttes ikke af Microsoft. Hvis du vil downloade Web Essentials, skal du gå til webstedet på [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).
  
Web Essentials tilbyder to former for bundtning:
  
- .bundle: til CSS- og JavaScript-filer
- .sprite: til billeder (kun tilgængelig i Visual Studio 2013)

Du kan bruge Web Essentials, hvis du har en eksisterende funktion med nogle brandingelementer, der refereres til i en brugerdefineret masterside, f.eks.:
  
![Skærmbillede af brand-element i brugerdefineret masterside.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Sådan opretter du et TE000127218- og CSS-bundt i Web Essentials
  
1. I Visual Studio i Løsningsoversigt skal du markere de filer, du vil medtage i bundtet.
2. Højreklik på de markerede filer, og vælg derefter **Web Essentials** \> **Opret JavaScript-bundtfil** i genvejsmenuen. Eksempel:

    ![Skærmbillede, der viser menuindstillingerne i Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Visning af resultaterne af bundtning af JavaScript- og CSS-filer

Når du opretter et JavaScript- og CSS-bundt, opretter Web Essentials en XML-fil, der kaldes en opskriftsfil, der identificerer JavaScript- og CSS-filerne samt nogle andre konfigurationsoplysninger:
  
![Skærmbillede af JavaScript- og CSS-opskriftfil.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Desuden, hvis flaget for minify er angivet til sand i bundtningens opskrift, reduceres filernes størrelse og bundtes sammen. Det betyder, at der er oprettet nye minificerede versioner af JavaScript-filerne, som du kan henvise til på din masterside.
  
![Skærmbillede af minify flag indstillet til sand.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Når du indlæser en side fra dit websted, kan du bruge udviklerværktøjerne fra din webbrowser, f.eks. Internet Explorer 11, til at se antallet af anmodninger, der er sendt til serveren, og hvor lang tid det har taget at indlæse hver fil.
  
Følgende figur er resultatet af indlæsningen af JavaScript- og CSS-filerne før minification.
  
![Skærmbillede, der viser 80 elementer, der hentes.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Efter bundtningen af CSS- og JavaScript-filer sammen, faldt antallet af anmodninger til 74, og det tog kun lidt længere tid end for de oprindelige filer at downloade hver fil enkeltvis:
  
![Skærmbillede, der viser 74 elementer, der hentes.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Efter bundtning reduceres JavaScript-bundtfilen betydeligt fra 815 KB til 365 KB:
  
![Skærmbillede, der viser reduceret downloadstørrelse.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Bundtning af billeder ved at oprette et billedsprite

Ligesom du kan bundte JavaScript- og CSS-filer, kan du kombinere mange små ikoner og andre almindelige billeder i et større sprite-ark og derefter bruge CSS til at få vist de enkelte billeder. I stedet for at downloade hvert enkelt billede, downloader brugerens webbrowser sprite-arket én gang og cachelagrer det på den lokale computer. Dette forbedrer sideindlæsningsydeevnen ved at skære ned på antallet af downloads og ture til webserveren.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Sådan opretter du et billedsprite i Web Essentials**
  
1. I Visual Studio i Løsningsoversigt skal du markere de filer, du vil medtage i bundtet.
2. Højreklik på de markerede filer, og vælg derefter **Web Essentials** \> **Create image sprite** i genvejsmenuen. Eksempel:

    ![Skærmbillede, der viser, hvordan du opretter et billedsprite.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Vælg en placering, hvor du vil gemme spritefilen. .sprite-filen er en XML-fil, der beskriver indstillingerne og filerne i spriten. De følgende figurer viser et eksempel på en PNG-spritefil og dens tilsvarende .sprite-XML-fil.

    ![Skærmbillede af en spritefil.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Skærmbillede af sprite-XML-fil.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
