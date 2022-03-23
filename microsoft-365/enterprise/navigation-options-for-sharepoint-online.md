---
title: Navigationsindstillinger for SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
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
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: I denne artikel beskrives websteder til navigationsindstillinger med SharePoint Publicering aktiveret SharePoint Online.
ms.openlocfilehash: c59006db8505991bd41d29714caae144b284f07d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591015"
---
# <a name="navigation-options-for-sharepoint-online"></a>Navigationsindstillinger for SharePoint Online

I denne artikel beskrives websteder til navigationsindstillinger med SharePoint Publicering aktiveret SharePoint Online. Valg og konfiguration af navigation påvirker ydeevnen og skalerbarheden af websteder betydeligt i SharePoint Online. Skabelonen SharePoint publiceringswebsted bør kun bruges, hvis det er påkrævet til en centraliseret portal, og publiceringsfunktionen bør kun aktiveres på bestemte websteder og kun, når det er absolut påkrævet, da det kan påvirke ydeevnen, når den bruges forkert.

>[!NOTE]
>Hvis du bruger moderne navigationsindstillinger SharePoint megamenu, overlappende navigation eller hubnavigation, gælder denne artikel ikke for dit websted. Moderne SharePoint anvender et mere fladt webstedshierarki og en hub-and-eg-model. Dette gør det muligt at opnå mange scenarier, der IKKE kræver brug af SharePoint Publiceringsfunktion.

## <a name="overview-of-navigation-options"></a>Oversigt over navigationsindstillinger

Konfiguration af navigationsudbyderen kan påvirke ydeevnen betydeligt for hele webstedet, og der skal tages nøje betragtning for at vælge en navigationsudbyder og konfiguration, der skalerer effektivt til kravene til et SharePoint websted. Der er to praktiske navigationsudbydere samt brugerdefinerede implementeringer af navigation.

Den første indstilling, Strukturel [**navigation**](#using-structural-navigation-in-sharepoint-online), er den anbefalede navigationsindstilling i SharePoint Online til klassiske SharePoint-websteder, hvis du aktiverer strukturel **navigationscaching for dit websted**. Denne navigationsudbyder viser navigationselementerne under det aktuelle websted og eventuelt det aktuelle websted og dets på samme niveau. Den indeholder yderligere funktioner som f.eks. sikkerhedsrelation og optælling af webstedsstruktur. Hvis cachelagring er deaktiveret, påvirker det ydeevnen og skalerbarheden negativt og kan blive underlagt en begrænsning.

Den anden indstilling, [**Administreret (metadata)-navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), repræsenterer navigationselementer, der bruger et ordsæt med administrerede metadata. Vi anbefaler, at sikkerheds trimning deaktiveres, medmindre det er påkrævet. Sikkerheds beskæring er aktiveret som en sikker standardindstilling for denne navigationsudbyder. Mange websteder kræver dog ikke sikkerheds beskæring, da navigationselementer ofte er ensartede for alle brugere af webstedet. Med den anbefalede konfiguration til deaktivering af sikkerhedsstyring kræver denne navigationsudbyder ikke en optælling af webstedsstruktur og kan i høj grad skaleres med en acceptabel ydeevne.

Ud over de out of the box-navigationsudbydere har mange kunder implementeret alternative implementeringer af brugerdefineret navigation. Se [Søgebaseret scripting på klientsiden](#using-search-driven-client-side-scripting) i denne artikel.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Fordele og ulemper ved SharePoint onlinenavigation

Følgende tabel opsummerer fordele og ulemper ved hver indstilling.

|Strukturel navigation  |Administreret navigation  |Søgebaseret navigation  |Brugerdefineret navigationsudbyder  |
|---------|---------|---------|---------|
|Fordele:<br/><br/>Nem at vedligeholde<br/>Sikkerhed justeret<br/>Opdateres automatisk inden for 24 timer, når indhold ændres<br/>     |Fordele:<br/><br/>Nem at vedligeholde<br/>|Fordele:<br/><br/>Sikkerhed justeret<br/>Opdateres automatisk, når der tilføjes websteder<br/>Hurtig indlæsningstid og lokalt cachelagret navigationsstruktur<br/>|Fordele:<br/><br/>Bredere udvalg af tilgængelige indstillinger<br/>Hurtig indlæsning, når cachelagring bruges korrekt<br/>Mange indstillinger fungerer godt med hurtigt sidedesign<br/>|
|Ulemper:<br/><br/>**Påvirker ydeevnen, hvis cachelagring er deaktiveret**<br/>Underlagt begrænsning<br/>|Ulemper:<br/><br/>Opdateres ikke automatisk for at afspejle webstedsstruktur<br/>**Påvirker ydeevnen, hvis sikkerhedsklip er aktiveret, eller når navigationsstrukturen** er kompleks<br/>|Ulemper:<br/><br/>Ingen mulighed for nemt at bestille websteder<br/>Kræver tilpasning af mastersiden (tekniske færdigheder påkrævet)<br/>|Ulemper:<br/><br/>Brugerdefineret udvikling er påkrævet<br/>Ekstern datakilde/cachelagret er nødvendig, f.eks. Azure<br/>|

Den mest passende indstilling for dit websted afhænger af kravene til webstedet og dine tekniske funktioner. Hvis du ønsker en navigationsudbyder, der er nem at konfigurere, og som automatisk opdateres, når indholdet ændres, er [strukturel navigation med](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) cachelagring aktiveret en god mulighed.

>[!NOTE]
>At anvende det samme princip som moderne SharePoint-websteder ved at forenkle den overordnede webstedsstruktur på en flad, ikke-hierarkisk struktur forbedrer ydeevnen og forenkler flytningen til moderne SharePoint websteder. Hvad det betyder, er, at i stedet for at have en enkelt gruppe af websteder med hundredvis af websteder (underordnede websteder) er det en bedre fremgangsmåde at have mange grupper af websteder med meget få underordnede websteder (underordnede websteder).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>Analyse af navigationsydeevnen SharePoint Online

[Sidediagnosticering til SharePoint-værktøjet](./page-diagnostics-for-spo.md) er en browserudvidelse til Microsoft Edge- og Chrome-browsere, der analyserer både den moderne SharePoint Online-portal og de klassiske sider på publiceringswebstedet. Dette værktøj fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Værktøjet genererer en rapport for hver analyseret side, der viser, hvordan siden fungerer i forhold til et foruddefineret sæt regler, og viser detaljerede oplysninger, når resultaterne for en test ligger uden for den oprindelige værdi. SharePoint Online kan administratorer og designere bruge værktøjet til fejlfinding af problemer med ydeevnen for at sikre, at nye sider optimeres før publiceringen.

**SPRequestDuration** er især den tid, det tager SharePoint at behandle siden. Tung navigation (f.eks. sider i navigation), komplekse webstedshierarkier og andre konfigurations- og topologiindstillinger kan alle bidrage markant til længere varigheder.

## <a name="using-structural-navigation-in-sharepoint-online"></a>Brug af strukturel navigation i SharePoint Online

Dette er den out of the box-navigation, der bruges som standard, og det er den mest enkle løsning. Det kræver ikke nogen tilpasning, og en ikke-teknisk bruger kan også nemt tilføje elementer, skjule elementer og administrere navigationen fra siden med indstillinger. Vi anbefaler [, at du aktiverer cachelagring](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), ellers vil der være en dyr afrunding af ydeevnen.

### <a name="how-to-implement-structural-navigation-caching"></a>Sådan implementeres cachelagring af strukturel navigation

Under **Webstedsnavigation Indstillinger** >  **Look** og **FeelNavigation** >  kan du validere, om strukturel navigation er valgt til enten global navigation eller aktuel navigation. Hvis du **vælger Vis sider** , påvirker det ydeevnen negativt.

![Strukturel navigation med Vis underordnede websteder markeret.](../media/SPONavOptionsStructuredShowSubsites.png)

Cachelagring kan aktiveres eller deaktiveres på niveauet for grupper af websteder og på webstedsniveau og er aktiveret til begge som standard. Hvis du vil aktivere det på niveauet for gruppen af websteder, skal du markere **afkrydsningsfeltet for Aktivér** >  >  cachelagring under Administration af gruppe af Indstillinger webstederWebstedsnavigation.

![Aktivér cachelagring på webstedsniveau.](../media/structural-nav/structural-nav-caching-site-coll.png)

Hvis du vil aktivere det på webstedsniveau, **skal du markere Indstillinger** >  **Aktivér** cachelagring under Webstedswebstedsnavigation.

![Aktivér cachelagring på webstedsniveau.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Brug af administreret navigation og metadata i SharePoint Online

Administreret navigation er en anden direkte indstilling, du kan bruge til at genskabe de fleste af de samme funktioner som strukturel navigation. Administrerede metadata kan konfigureres til at få aktiveret eller deaktiveret sikkerheds beskæring. Når den er konfigureret med sikkerheds trimning deaktiveret, er administreret navigation forholdsvis effektivt, da den indlæser alle navigationslinks med et konstant antal serveropkald. Aktivering af sikkerheds beskæring negerer dog nogle af fordelene ved administreret navigation.

Hvis du vil aktivere sikkerheds beskæring, anbefaler vi, at du:

- Opdater alle links til brugervenlige URL-adresser til simple links
- Tilføj nødvendige sikkerhedsbeskæringsnoder som brugervenlige URL-adresser
- Begræns antallet af navigationselementer til højst 100 og højst 3 niveauer.

Mange websteder kræver ikke sikkerheds beskæring, da navigationsstrukturen ofte er ensartet for alle brugere af webstedet. Hvis sikkerhedsafskæring er deaktiveret, og der tilføjes et link til navigationen, som ikke alle brugere har adgang til, vises linket stadig, men vil føre til en meddelelse, der er nægtet adgang. Der er ingen risiko for utilsigtet adgang til indholdet.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Sådan implementeres administreret navigation og resultaterne

Der er flere artikler om docs.microsoft.com detaljer om administreret navigation. Se for eksempel Oversigt [over administreret navigation i SharePoint Server](/sharepoint/administration/overview-of-managed-navigation).

For at implementere administreret navigation skal du konfigurere ord med URL-adresser, der svarer til webstedets navigationsstruktur. Administreret navigation kan endda administreres manuelt for at erstatte strukturel navigation i mange tilfælde. Eksempel:

![SharePoint onlinewebstedsstruktur.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Brug af søgebaseret scripting på klientsiden

En af de mest almindelige klasser af brugerdefinerede navigationsimplementeringener, der gengiver designmønstre, der gengives af klienten, og som lagrer en lokal cache af navigationsnoder.

Disse navigationsudbydere har et par vigtige fordele:

- De fungerer generelt godt med effektive sidedesigns.
- De er yderst skalerbare og performant, fordi de kan gengives uden ressourceomkostninger (og opdateres i baggrunden efter en timeout).
- Disse navigationsudbydere kan hente navigationsdata ved hjælp af forskellige strategier, lige fra enkle statiske konfigurationer til forskellige dynamiske dataudbydere.

Et eksempel på en dataudbyder er at bruge en søgebaseret **navigation**, der giver fleksibilitet til optælling af navigationsnoder og effektiv håndtering af sikkerhed.

Der er andre populære muligheder for at oprette **brugerdefinerede navigationsudbydere**. Gennemse [navigationsløsninger til SharePoint Online-portaler for yderligere vejledning](/sharepoint/dev/solution-guidance/portal-navigation) til at opbygge en brugerdefineret navigationsudbyder.

Ved hjælp af søgning kan du udnytte de indekser, der er bygget i baggrunden, ved hjælp af fortløbende gennemsøgning. Søgeresultaterne hentes fra søgeindekset, og resultaterne er sikkerheds-trimmet. Dette er generelt hurtigere end out of the box-navigationsudbydere, når der kræves sikkerhedsskæring. Hvis du bruger søgning til strukturel navigation, især hvis du har en kompleks webstedsstruktur, kan det øge sideindlæsningstiden væsentligt. Den største fordel ved dette i stedet for administreret navigation er, at du har fordel af sikkerheds beskæring.

Denne fremgangsmåde indebærer oprettelse af en brugerdefineret masterside og erstatning af den indeværende navigationskode med brugerdefineret HTML. Følg denne fremgangsmåde beskrevet i følgende eksempel for at erstatte navigationskoden i filen `seattle.html`. I dette eksempel skal du åbne filen og `seattle.html` erstatte hele elementet med `id="DeltaTopNavigation"` en brugerdefineret HTML-kode.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Eksempel: Erstat den out of the box-navigationskode på en masterside

1. Gå til siden Indstillinger websteder.
2. Åbn mastersidegalleriet ved at klikke **på Mastersider**.
3. Herfra kan du navigere gennem biblioteket og downloade filen `seattle.master`.
4. Rediger koden ved hjælp af en teksteditor, og slet kodeblokken på følgende skærmbillede.<br/>![Slet den kodeblok, der vises.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Fjern koden mellem mærkerne `<SharePoint:AjaxDelta id="DeltaTopNavigation">` `<\SharePoint:AjaxDelta>` , og erstat den med følgende kodestykke:<br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. Erstat URL-adressen i begyndelsen af ankermærket for indlæsningsbilledet med et link til et indlæsningsbillede i gruppen af websteder. Når du har foretaget ændringerne, skal du omdøbe filen og derefter overføre den til mastersidegalleriet. Dette genererer en ny .master-fil.<br/>
7. Denne HTML-kode er den grundlæggende markering, der udfyldes af søgeresultaterne, som returneres fra JavaScript-kode. Du skal redigere koden for at ændre værdien for var root = "site collection URL" som vist i følgende kodestykke:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Resultaterne tildeles til matrixen self.nodes, og der bygges et hierarki ud af objekterne ved hjælp linq.js at tildele output til et self.hierarchy for matrixen. Denne matrix er det objekt, der er bundet til HTML-koden. Dette gøres i funktionen toggleView() ved at sende selvobjektet til funktionen ko.applyBinding().<br/>Dette medfører derefter, at hierarkimatrixen bindes til følgende HTML-kode:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

Hændelseshandlerne for og `mouseexit` føjes til navigationen på øverste niveau for at håndtere rullemenuerne for `mouseenter` det underordnede websted, som udføres i `addEventsToElements()` funktionen.

I vores eksempel på kompleks navigation viser en ny sideindlæsning uden den lokale cachelagring den tid, der er brugt på serveren, blevet skåret ned fra den benchmarke strukturelle navigation for at få et lignende resultat som den administrerede navigations tilgang.

### <a name="about-the-javascript-file"></a>Om JavaScript-filen...

>[!NOTE]
>Hvis du bruger brugerdefineret JavaScript, skal du sørge for, CDN offentlige indstillinger er aktiveret, og at filen er på CDN placering.

Hele JavaScript-filen er som følger:

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

For at opsummere koden, der er vist ovenfor `jQuery $(document).ready` i funktionen, er `viewModel object` der en oprettet, og derefter `loadNavigationNodes()` kaldes funktionen på det pågældende objekt. Denne funktion indlæser enten det tidligere indbyggede navigationshierarki, der er gemt i det lokale HTML5-lager i klientbrowseren, eller den kalder funktionen `queryRemoteInterface()`.

`QueryRemoteInterface()` opbygger en anmodning ved hjælp af `getRequest()` funktionen med den forespørgselsparameter, der er defineret tidligere i scriptet, og returnerer derefter data fra serveren. Disse data er i bund og grund en matrix af alle webstederne i gruppen af websteder, der er repræsenteret som dataoverførselsobjekter med forskellige egenskaber.

Disse data fortolkes `SPO.Models.NavigationNode` `Knockout.js` derefter til de tidligere definerede objekter, som bruges til at oprette observerede egenskaber til brug af data, der binder værdierne i den HTML, som vi definerede tidligere.

Objekterne sættes derefter ind i en resultatmatrix. Denne matrix fortolkes til JSON ved hjælp af Knockout og gemmes i det lokale browserlager for at forbedre ydeevnen ved fremtidige sidebelastninger.

### <a name="benefits-of-this-approach"></a>Fordele ved denne tilgang

En stor fordel ved [denne fremgangsmåde](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) er, at navigationen ved hjælp af et lokalt HTML5-lager gemmes lokalt for brugeren, næste gang de indlæser siden. Vi får større forbedringer af ydeevnen ved at bruge søge-API til strukturel navigation. det kræver dog tekniske funktioner at udføre og tilpasse denne funktionalitet.

I [eksempelimplementeringen er](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) webstederne sorteret på samme måde som den kørende strukturelle navigation. alfabetisk rækkefølge. Hvis du gerne vil afvige fra denne rækkefølge, vil det være mere kompliceret at udvikle og vedligeholde. Denne fremgangsmåde kræver også, at du afviger fra de understøttede mastersider. Hvis den brugerdefinerede masterside ikke vedligeholdes, går dit websted glip af opdateringer og forbedringer, som Microsoft foretager på mastersiderne.

Ovenstående [kode](#about-the-javascript-file) har følgende afhængigheder:

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/eller github.com/neuecc/linq.js

Den aktuelle version af LinqJS indeholder ikke metoden ByHierarchy, der bruges i ovenstående kode, og vil bryde navigationskoden. Det løser du ved at føje følgende metode til filen Linq.js før linjen `Flatten: function ()`.

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>Relaterede emner

[Oversigt over administreret navigation i SharePoint Server](/sharepoint/administration/overview-of-managed-navigation)

[Cachelagring og ydeevne i strukturel navigation](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)