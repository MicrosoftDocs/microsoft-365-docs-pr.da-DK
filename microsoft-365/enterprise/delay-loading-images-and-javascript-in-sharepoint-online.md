---
title: Forsinke indlæsning af billeder og JavaScript i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du kan reducere indlæsningstiden for SharePoint Online-sider ved at bruge JavaScript til at forsinke indlæsningen af billeder og ikke-vigtige JavaScript.
ms.openlocfilehash: 6b8eb479ae33b47081e33e45338c02d46f36e055
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589746"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Forsinke indlæsning af billeder og JavaScript i SharePoint Online

I denne artikel beskrives det, hvordan du kan reducere indlæsningstiden for SharePoint Online-sider ved at bruge JavaScript til at forsinke indlæsningen af billeder og også vente med at indlæse ikke-vigtige JavaScript, indtil siden er indlæst.
  
Billeder kan påvirke hastighederne af sideindlæsning på SharePoint Online. De fleste moderne internetbrowsere henter som standard billeder automatisk, når der indlæses en HTML-side. Dette kan medføre, at indlæsningen af siden er unødvendigt langsom, hvis billederne ikke er synlige på skærmen, før brugeren ruller ned. Billederne kan forhindre browseren i at indlæse den synlige del af siden. Du kan løse dette problem ved at bruge JavaScript til at springe over først at indlæse billederne. Indlæsning af ikke-vigtige JavaScript kan også gøre downloadtiderne langsommere på SharePoint sider. I dette emne beskrives nogle metoder, du kan bruge til at forbedre sideindlæsningstider med JavaScript SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Forbedr sideindlæsningstider ved at forsinke billedindlæsning SharePoint onlinesider ved hjælp af JavaScript

Du kan bruge JavaScript til at forhindre, at en webbrowser henter billeder på forhånd. Dette øger hastigheden af den overordnede dokumentgengivelse. For at gøre dette skal du fjerne værdien af src-attributten \<img\> fra mærket og erstatte den med stien til en fil i en dataattribut, f.eks.: data-src. Eksempel:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Ved at bruge denne metode downloader browseren ikke billederne med det samme. Hvis billedet allerede er i visningporten, beder JavaScript browseren om at hente URL-adressen fra dataattributten og indsætter den som værdien for src-attributten. Billedet indlæses kun, når brugeren ruller, og det kommer ind i visningen.
  
For at få alt dette til at ske skal du bruge JavaScript.
  
I en tekstfil skal du definere **funktionen isElementInViewport()** for at kontrollere, om et element findes i den del af browseren, der er synlig for brugeren.
  
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

Brug derefter **isElementInViewport()** i funktionen **loadItemsInView(** ). Funktionen **loadItemsInView()** indlæser alle billeder, der har en værdi for data-src-attributten, hvis de findes i den del af browseren, der er synlig for brugeren. Føj følgende funktion til tekstfilen:
  
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

Kald til sidst **loadItemsInView()** fra **window.onscroll(),** som vist i følgende eksempel. Dette sikrer, at alle billeder, der findes i visningsporten, indlæses, når brugeren har brug for dem, men ikke før. Føj følgende til tekstfilen:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

For SharePoint Online skal du vedhæfte følgende funktion til rullehændelsen i mærket #s4-arbejdsområde\<div\>. Dette skyldes, at vindueshændelser tilsidesættes for at sikre, at båndet forbliver fastgjort til toppen af siden.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Gem tekstfilen som en JavaScript-fil med filtypenavnet .js f.eks. delayLoadImages.js.
  
Når du er færdig med delayLoadImages.js, kan du føje indholdet af filen til en masterside i SharePoint Online. Det gør du ved at tilføje et scriptlink til sidehovedet på mastersiden. Når det er på en masterside, anvendes JavaScript på alle sider på dit SharePoint Online-websted, der bruger det pågældende mastersidelayout. Alternativt kan du, hvis du kun vil bruge dette på én side på dit websted, bruge webdelen scripteditor til at integrere JavaScript på siden. Se disse emner for at få flere oplysninger:
  
- [Sådan gør du: Anvend en masterside på et websted SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [Sådan gør du: Opret et sidelayout i SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>Eksempel: Referering af JavaScript-delayLoadImages.js fra en masterside i SharePoint Online
  
For at dette skal fungere, skal du også henvise til jQuery på mastersiden. I følgende eksempel kan du se under den indledende sideindlæsning, at der kun er ét billede indlæst, men der er flere på siden.
  
![Skærmbillede, der viser ét billede indlæst på siden.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
Følgende skærmbillede viser resten af de billeder, der downloades, efter de rulles ind i visningen.
  
![Skærmbillede, der viser flere billeder indlæst på siden.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Forsinkelse af billedindlæsning ved hjælp af JavaScript kan være en effektiv metode til at øge ydeevnen; men hvis metoden anvendes på et offentligt websted, kan søgemaskiner ikke gennemsøge billederne på samme måde, som de gennemsøger et regelmæssigt udformet billede. Dette kan påvirke rangeringer på søgemaskiner, fordi metadata på selve billedet ikke er der, før siden indlæses. Søgemaskinesøgninger læser kun HTML-koden og kan derfor ikke se billederne som indhold på siden. Billeder er en af de faktorer, der bruges til at rangere sider i søgeresultater. En måde at løse dette på er at bruge introduktionstekst til dine billeder.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub kodeeksempel: Indsætte JavaScript for at forbedre ydeevnen

Gå ikke glip af artiklen og kodeeksempel på [JavaScript-indførslen](https://go.microsoft.com/fwlink/p/?LinkId=524759), der er angivet GitHub.
  
## <a name="see-also"></a>Se også

[Understøttede browsere i Office 2013 og Microsoft 365 Apps for enterprise](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Sådan gør du: Anvend en masterside på et websted SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[Sådan gør du: Opret et sidelayout i SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)