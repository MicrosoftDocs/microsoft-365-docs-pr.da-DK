---
title: Udskyd indlæsning af billeder og JavaScript i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
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
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Få mere at vide om, hvordan du reducerer indlæsningstiden for SharePoint Online-sider ved at bruge JavaScript til at forsinke indlæsning af billeder og ikke-essentiel JavaScript.
ms.openlocfilehash: 8252e169e36dc6976a7be0b4815915ee72283eff
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754726"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Udskyd indlæsning af billeder og JavaScript i SharePoint Online

I denne artikel beskrives det, hvordan du kan reducere indlæsningstiden for SharePoint Online-sider ved at bruge JavaScript til at forsinke indlæsningen af billeder og også ved at vente med at indlæse ikke-essentiel JavaScript, indtil siden indlæses.
  
Billeder kan påvirke sideindlæsningshastighederne negativt på SharePoint Online. Som standard henter de fleste moderne internetbrowsere billeder på forhånd, når en HTML-side indlæses. Dette kan medføre, at siden bliver unødvendigt langsom at indlæse, hvis billederne ikke er synlige på skærmen, før brugeren ruller ned. Billederne kan forhindre browseren i at indlæse den synlige del af siden. Du kan løse dette problem ved at bruge JavaScript til at springe indlæsningen af billederne over først. Indlæsning af ikke-essentiel JavaScript kan også gøre downloadtiderne langsomme på dine SharePoint sider. I dette emne beskrives nogle metoder, du kan bruge til at forbedre indlæsningstiden for sider med JavaScript i SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Gør indlæsningstider for sider bedre ved at forsinke indlæsningen af billeder på SharePoint Online-sider ved hjælp af JavaScript

Du kan bruge JavaScript til at forhindre, at en webbrowser henter billeder på forhånd. Dette fremskynder den overordnede dokumentgengivelse. Det gør du ved at fjerne værdien af attributten src fra \<img\> -koden og erstatte den med stien til en fil i en dataattribut, f.eks.: data-src. Eksempel:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Ved hjælp af denne metode downloader browseren ikke billederne med det samme. Hvis billedet allerede er i visningsporten, beder JavaScript browseren om at hente URL-adressen fra dataattributten og indsætte den som værdien for src-attributten. Billedet indlæses kun, når brugeren ruller, og det vises.
  
Hvis du vil have alt dette til at ske, skal du bruge JavaScript.
  
I en tekstfil skal du definere funktionen **isElementInViewport()** for at kontrollere, om et element er i den del af browseren, der er synlig for brugeren.
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

Derefter skal du bruge **isElementInViewport()** i funktionen **loadItemsInView().** Funktionen **loadItemsInView()** indlæser alle billeder, der har en værdi for attributten data-src, hvis de findes i den del af browseren, der er synlig for brugeren. Føj følgende funktion til tekstfilen:
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

Kald til sidst **loadItemsInView()** inde fra **window.onscroll()** som vist i følgende eksempel. Dette sikrer, at alle billeder, der er i visningsporten, indlæses, når brugeren har brug for dem, men ikke før. Føj følgende til tekstfilen:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

For SharePoint Online skal du knytte følgende funktion til rullehændelsen på mærket #s4-arbejdsområde\<div\>. Dette skyldes, at vindueshændelserne tilsidesættes for at sikre, at båndet forbliver knyttet til toppen af siden.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Gem tekstfilen som en JavaScript-fil med filtypenavnet .js, f.eks. delayLoadImages.js.
  
Når du er færdig med at skrive delayLoadImages.js, kan du føje indholdet af filen til en masterside i SharePoint Online. Det gør du ved at føje et scriptlink til overskriften på mastersiden. Når javascriptet er på en masterside, anvendes det på alle sider på dit SharePoint Online-websted, der bruger dette mastersidelayout. Hvis du kun vil bruge denne på én side på dit websted, kan du også bruge scripteditorwebdelen til at integrere JavaScript på siden. Se disse emner for at få flere oplysninger:
  
- [Sådan anvender du en masterside på et websted i SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [Sådan opretter du et sidelayout i SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>Eksempel: Referer til JavaScript delayLoadImages.js-filen fra en masterside i SharePoint Online
  
Hvis dette skal fungere, skal du også referere til jQuery på mastersiden. I følgende eksempel kan du se i den indledende sideindlæsning, at der kun er indlæst ét billede, men der er flere på siden.
  
![Skærmbillede, der viser ét billede, der er indlæst på siden.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
På følgende skærmbillede kan du se resten af de billeder, der downloades, når de ruller ind i visningen.
  
![Skærmbillede, der viser flere billeder, der er indlæst på siden.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Forsinkelse af billedindlæsning ved hjælp af JavaScript kan være en effektiv teknik til at øge ydeevnen. Men hvis teknikken anvendes på et offentligt websted, så søgemaskinerne ikke er i stand til at gennemsøge billederne på samme måde, de ville gennemsøge en regelmæssigt dannede billede. Dette kan påvirke rangeringerne på søgemaskiner, fordi metadataene på selve billedet ikke er der, før siden indlæses. Søgemaskiner læser kun HTML-koden og kan derfor ikke se billederne som indhold på siden. Billeder er en af de faktorer, der bruges til at rangere sider i søgeresultater. En måde at løse problemet på er ved at bruge introduktionstekst til dine billeder.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub kodeeksempel: Indsprøjtning af JavaScript for at forbedre ydeevnen

Gå ikke glip af artiklen og kodeeksemplet på [JavaScript-injektionen](https://go.microsoft.com/fwlink/p/?LinkId=524759) på GitHub.
  
## <a name="see-also"></a>Se også

[Understøttede browsere i Office 2013 og Microsoft 365 Apps for enterprise](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Sådan anvender du en masterside på et websted i SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[Sådan opretter du et sidelayout i SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)