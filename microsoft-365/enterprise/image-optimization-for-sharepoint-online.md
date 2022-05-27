---
title: Billedoptimering for SharePoint klassiske udgivelseswebsteder online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Få mere at vide om, hvordan du bruger gengivelser og sprites til at forbedre billedydeevnen på dine SharePoint online klassiske udgivelseswebsteder.
ms.openlocfilehash: 39d0e4c26339ecf70c922636f82dcef82dd4b13e
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754416"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>Billedoptimering for SharePoint klassiske udgivelseswebsteder online

Indlæsningshastigheden for en webside afhænger af den kombinerede størrelse af alle de komponenter, der kræves for at gengive siden, herunder billeder, HTML, JavaScript og CSS. Billeder er en fantastisk måde at gøre dit websted mere tiltalende på, men deres størrelse kan påvirke ydeevnen. Ved at optimere dine billeder med komprimering og tilpasning af størrelsen og ved hjælp af sprites kan du forskyde effekten af store billeder. Ved hjælp af SharePoint billedgengivelser kan du uploade et enkelt stort billede og få vist dele af billedet, så det kan genbruges i stedet for genindlæses.

>[!NOTE]
>Dette emne gælder for SharePoint online klassiske udgivelseswebsteder og ikke moderne portalwebsteder. Du kan finde oplysninger om billedoptimering på SharePoint online moderne [portalwebsteder under Optimer billeder på SharePoint Online moderne portalsider](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Brug af sprites til at fremskynde indlæsningen af billeder

![Skærmbillede af spcommon.](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

En billedsprite indeholder mange mindre billeder. Ved hjælp af CSS vælger du en del af det sammensatte billede, der skal vises på en bestemt del af siden med absolut placering. Grundlæggende flytter du et enkelt billede rundt på siden i stedet for at indlæse flere billeder og gør en lille del af dette billede synligt gennem et lille vindue, hvor den påkrævede del af sprite-billedet vises for slutbrugeren. SharePoint Online bruger sprites til at vise de forskellige ikoner i filen sprite spcommon.png.

Hvad er beskrevet her:
- Billedkomprimering
- Billedoptimering
- SharePoint billedgengivelser
   
Dette kan øge ydeevnen, fordi du kun downloader ét billede i stedet for flere og derefter cachelagrer og genbruger billedet. Selvom billedet ikke forbliver cachelagret ved at have et enkelt billede i stedet for flere billeder, reducerer denne metode det samlede antal HTTP-anmodninger til serveren, hvilket reducerer sideindlæsningstiden. Dette er virkelig en form for billed bundling. Dette er en nyttig teknik, hvis billederne ikke ændres ofte, f.eks. ikoner, som vist i det SharePoint eksempel, der er angivet ovenfor. Du kan se, hvordan du nemt kan bruge [Web Essentials](https://vswebessentials.com/), der er et communitybaseret tredjepartsprojekt med åben kildekode, til at opnå dette i Microsoft Visual Studio. Du kan få flere oplysninger under [Minification and bundling in SharePoint Online](./minification-and-bundling-in-sharepoint-online.md).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Brug af billedkomprimering og -optimering til at fremskynde sideindlæsning

Billedkomprimering og -optimering handler om at reducere filstørrelsen på de billeder, du bruger på dit websted. Den bedste teknik til at reducere størrelsen på et billede er ofte at tilpasse størrelsen på billedet til de maksimale dimensioner, som det kan ses på webstedet. Der er ingen mening i at have et billede større end det nogensinde vil blive vist. At sikre, at billeder har de korrekte dimensioner ved hjælp af en billededitor, er en hurtig og nem måde at reducere størrelsen på din side på.
  
Når billederne har den rigtige størrelse, er det næste trin at optimere komprimeringen af disse billeder. Der findes forskellige værktøjer til komprimering og optimering, herunder Photo Gallery og tredjepartsværktøjer. Nøglen til komprimering er at reducere filstørrelsen så meget som muligt uden at miste nogen mærkbar kvalitet for slutbrugerne. Sørg for at teste dine komprimerede filer på en high-definition-skærm for at sikre, at de stadig ser godt ud.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Gør downloads af sider hurtigere ved hjælp af SharePoint billedgengivelser

Billedgengivelser er en funktion i SharePoint Online, der giver dig mulighed for at levere forskellige versioner af billeder, der er baseret på foruddefinerede billeddimensioner. Dette er især vigtigt, når der er brugergenereret billedindhold, eller billeddimensionerne, f.eks. bredde og højde, er fastsat af CSS på webstedet. Selvom et billede er fastgjort af CSS, indlæses billedet i fuld opløsning stadig. I dette tilfælde kan filstørrelsen reduceres ved hjælp af billedgengivelser.
  
> [!NOTE]
> Gengivelser er kun tilgængelige for SharePoint, når publicering er aktiveret. Du kan aktivere publicering under Indstillinger \> Websted Indstillinger \> Administrer webstedsfunktioner \> SharePoint Serverpublicering. Ellers vises indstillingen ikke.
  
Tilpasningen af størrelsen på billedgengivelsen fungerer ved at tage den mindste dimension, du definerer, enten bredde eller højde, og derefter tilpasse billedets størrelse, så den anden dimension automatisk tilpasses på baggrund af det låste højde-bredde-forhold. Som standard beskæres billedet fra midten af de resterende dimensioner. Hvis du f.eks. definerer en gengivelse på 100px bred og 50px høj, og dit oprindelige billede er 1000 pixel bredt og 800 pixel højt, tilpasses størrelsen, så dimensionen 800px nu er 50px, og dimensionen 1000px (nu 62,5px) beskæres fra midten af billedet.
  
Trinnene er relativt enkle, men hvis billederne skal bruge gengivelserne, skal gengivelserne være på det SharePoint websted, før du tilføjer billederne. Derudover skal du også have SharePoint Server Publishing Infrastructure (niveau for gruppe af websteder) og SharePoint serverudgivelsesfunktioner (webstedsniveau) aktiveret.
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Tilføj en billedgengivelse for at fremskynde sideindlæsningen
  
1. Kontrollér, at den brugerkonto, der udfører denne procedure, som minimum har designtilladelser til webstedet på øverste niveau for gruppen af websteder, og at webstedet publiceres på en webside.

2. Gå til webstedet på øverste niveau i gruppen af udgivelseswebsteder i en webbrowser.

3. Vælg ikonet **Indstillinger**.

4. På siden **Site Indstillinger** i afsnittet **Udseende og funktionalitet** kan du se de indbyggede billedgengivelser.

    Du kan bruge de køreklare gengivelser eller vælge **Billedgengivelser** for at oprette en ny.

    ![Skærmbillede af billedgengivelse.](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Vælg **Tilføj nyt element** på siden **Billedgengivelser**.

    ![Skærmbillede af Tilføj nyt element.](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Angiv et navn til gengivelsen i feltet **Navn** på siden **Ny billedgengivelse**.

7. I tekstfelterne **Bredde** og **Højde** skal du angive bredden og højden i pixel for gengivelsen og derefter vælge **Gem**.

    ![Skærmbillede af navn på billedgengivelse.](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Brugerdefineret beskæring med billedgengivelser

Der genereres som standard en billedgengivelse fra midten af billedet. Du kan justere billedgengivelsen for individuelle billeder ved at beskære den del af billedet, du vil bruge. Du kan beskære billederne individuelt pr. gengivelse. Hvis du beskærer billederne, fremskyndes sideindlæsningen ved hjælp af SharePoint blobcache til at oprette en version af billedet for hver gengivelse. På denne måde reduceres serverbelastningen, fordi billedet kun tilpasses én gang og derefter er klar til at betjene slutbrugerne flere gange. Du kan få flere oplysninger om, hvordan du beskærer en billedgengivelse, under [Beskær en billedgengivelse](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels).
