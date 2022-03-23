---
title: Billedoptimering til klassiske SharePoint onlinepubliceringswebsteder
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Lær at bruge gengivelser og sprites til at forbedre billedydeevnen på dine klassiske SharePoint onlinepubliceringswebsteder.
ms.openlocfilehash: fe3c698dda06559bf6e104650b6b8bb8d81172fa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591576"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>Billedoptimering til klassiske SharePoint onlinepubliceringswebsteder

Indlæsningshastigheden af en webside afhænger af den kombinerede størrelse af alle de komponenter, der kræves for at gengive siden, herunder billeder, HTML, JavaScript og CSS. Billeder er en god måde at gøre dit websted mere tiltalende på, men deres størrelse kan påvirke ydeevnen. Ved at optimere dine billeder ved hjælp af komprimering og tilpasning af størrelsen og ved hjælp af sprites kan du forskyde effekterne af meget store billeder. Ved SharePoint bruge billedgengivelser, kan du overføre et enkelt stort billede og få vist sektioner af billedet, så det kan genbruges i stedet for genindlæses.

>[!NOTE]
>Dette emne gælder for SharePoint online klassiske publiceringswebsteder, ikke moderne portalwebsteder. Du kan finde oplysninger om billedoptimering SharePoint moderne portalwebsteder i Optimer [billeder på SharePoint online moderne portalsider](modern-image-optimization.md).
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Brug af sprites til at fremskynde billedindlæsning

![Skærmbillede af spcommon.](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

Et billedsprite indeholder mange mindre billeder. Ved hjælp af CSS markerer du en del af det sammensatte billede, der skal vises på en bestemt del af siden med absolut placering. Grundlæggende flytter du et enkelt billede rundt på siden i stedet for at indlæse flere billeder og gør en lille del af billedet synligt gennem et lille vindue, hvor den nødvendige del af spritebilledet vises til slutbrugeren. SharePoint Online bruger sprites til at vise dets forskellige ikoner i spritefilen spcommon.png fil.

Dette behandles her:
- Billedkomprimering
- Billedoptimering
- SharePoint af billedgengivelser
   
Dette kan øge ydeevnen, fordi du kun downloader ét billede i stedet for flere og derefter cachelagrer og genbruger billedet. Selvom billedet ikke forbliver cachelagret, ved at have et enkelt billede i stedet for flere billeder, reducerer denne metode det samlede antal HTTP-anmodninger til serveren, hvilket vil reducere sideindlæsningstiderne. Dette er i virkeligheden en form for bundtning af billeder. Dette er en meget nyttig metode, hvis billederne ikke ændres særlig ofte, f.eks. ikoner, som vist i SharePoint vist ovenfor. Du kan se, hvordan du bruger [Web Essentials](https://vswebessentials.com/), et open source-projekt fra en tredjepart, der er communitybaseret, til nemt at opnå dette i Microsoft Visual Studio. Få mere at vide under [Minification og bundtning i SharePoint Online](./minification-and-bundling-in-sharepoint-online.md).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Brug af billedkomprimering og optimering til at fremskynde sideindlæsning

Billedkomprimering og optimering handler om at reducere filstørrelsen på de billeder, du bruger på dit websted. Den bedste metode til at reducere størrelsen på et billede er ofte at ændre størrelsen på billedet til de største dimensioner, som det kan ses på webstedet. Der er ingen mening i at have et billede, der er større end det, som nogensinde vil blive vist. At sikre, at billeder har de rigtige dimensioner ved hjælp af et billedredigeringsprogram, er en hurtig og nem måde at reducere størrelsen på din side.
  
Når billederne har den rigtige størrelse, er næste trin at optimere komprimeringen af disse billeder. Der findes forskellige værktøjer, der kan bruges til komprimering og optimering, herunder Photo Gallery og tredjepartsværktøjer. Nøglen til komprimering er at reducere filstørrelsen så meget som muligt uden at miste nogen mærkbar kvalitet for slutbrugerne. Sørg for, at du tester dine komprimerede filer på en skærm med høj opløsning for at sikre, at de stadig ser godt ud.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Gør download af sider hurtigere ved SharePoint af billedgengivelser

Billedgengivelser er en funktion i SharePoint Online, der gør det muligt at betjene forskellige versioner af billeder baseret på foruddefinerede billeddimensioner. Dette er især vigtigt, når der er brugergenereret billedindhold, eller billedets dimensioner såsom bredde og højde er fastsat af CSS på webstedet. Selvom et billede er rettet af CSS, er billedet stadig indlæst i fuld opløsning. I dette tilfælde kan filstørrelsen reduceres ved hjælp af billedgengivelser.
  
> [!NOTE]
> Gengivelser er kun tilgængelige for de gengivelser, der SharePoint, når publicering er aktiveret. Du kan aktivere publicering under Indstillinger \> Websted Indstillinger Administrer \> webstedsfunktioner SharePoint \> Serverpublicering. Indstillingen vises ikke på anden måde.
  
Billedgengivelsesgengivelsesstørrelse fungerer ved at tage den mindste dimension, du definerer, enten bredde eller højde, og derefter ændre størrelsen på billedet, så størrelsen på den anden dimension automatisk tilpasses baseret på det låste højde-breddeforhold. Som standard beskærer programmet billedet fra midten med de resterende dimensioner. Hvis du f.eks. definerer en gengivelse af 100px bred og 50px høj, og dit oprindelige billede er 1000px bred og 800px høj, ændres størrelsen, så 800px-dimensionen nu er 50px, og 1000px-dimensionen (nu 62.5px) er beskåret fra midten af billedet.
  
Trinnene er relativt simple, men for at billeder kan bruge gengivelserne, skal gengivelserne være på webstedet SharePoint før du tilføjer billederne. Desuden skal du også have SharePoint Server-publiceringsinfrastrukturen (niveau for gruppe af websteder) og SharePoint Serverpublicering (niveau af websted) slået til.
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Tilføje en billedgengivelse for at fremskynde indlæsningen af siden
  
1. Kontrollér, at den brugerkonto, der udfører denne procedure, som minimum har designtilladelser til webstedet på øverste niveau i gruppen af websteder, og at webstedet publiceres på en webside.

2. Gå til webstedet på øverste niveau i gruppen af publiceringswebsteder i en webbrowser.

3. Vælg **Indstillinger** ikon.

4. På siden **Webstedsgengivelser** Indstillinger du i sektionen  Udseende og brug de indbyggede billedgengivelser.

    Du kan bruge gengivelserne uden for boksen eller vælge **Billedgengivelser for** at oprette en ny.

    ![Skærmbillede af billedgengivelse.](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. På siden **Billedgengivelser** skal du vælge **Tilføj nyt element**.

    ![Skærmbillede af Tilføj nyt element.](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Skriv **et navn til gengivelsen** i **feltet Navn** på siden Ny billedgengivelse.

7. I **tekstfelterne** **Bredde** og Højde skal du skrive bredde og højde i pixel, gengivelsen og derefter vælge **Gem**.

    ![Skærmbillede af navn på billedgengivelse.](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Brugerdefineret beskæring med billedgengivelser

Som standard genereres en billedgengivelse fra midten af billedet. Du kan justere billedgengivelse for individuelle billeder ved at beskære den del af billedet, du vil bruge. Du kan beskære billederne på individuel basis pr. gengivelse. Beskæring af billeder fremskynder indlæsningen af siden ved SharePoint din blob-cache til at oprette en version af billedet for hver gengivelse. På denne måde reduceres serverbelastningen, fordi billedets størrelse kun tilpasses én gang og derefter er klar til at servicere slutbrugere flere gange. Du kan finde flere oplysninger om, hvordan du beskærer en billedgengivelse, [under Beskær en billedgengivelse](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels).
