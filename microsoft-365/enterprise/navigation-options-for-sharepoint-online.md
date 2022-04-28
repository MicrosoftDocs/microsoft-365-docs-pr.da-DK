---
title: Navigationsindstillinger for SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel beskrives websteder med navigationsindstillinger, hvor SharePoint publicering er aktiveret i SharePoint Online.
ms.openlocfilehash: 67bf1c854d97cf254d1484151987a87853e1ae9d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101177"
---
# <a name="navigation-options-for-sharepoint-online"></a>Navigationsindstillinger for SharePoint Online

I denne artikel beskrives websteder med navigationsindstillinger, hvor SharePoint publicering er aktiveret i SharePoint Online. Valget og konfigurationen af navigationen påvirker ydeevnen og skalerbarheden af websteder i SharePoint Online. Skabelonen SharePoint udgivelseswebsted må kun bruges, hvis den kræves til en central portal, og publiceringsfunktionen bør kun aktiveres på bestemte websteder, og kun når den er absolut påkrævet, da den kan påvirke ydeevnen, når den bruges forkert.

>[!NOTE]
>Hvis du bruger moderne SharePoint navigationsindstillinger som megamenu, overlappende navigation eller hubnavigation, gælder denne artikel ikke for dit websted. Moderne SharePoint webstedsarkitekturer udnytter et mere fladt webstedshierarki og en hub-and-spoke-model. Dette gør det muligt at opnå mange scenarier, der ikke kræver brug af funktionen SharePoint udgivelse.

## <a name="overview-of-navigation-options"></a>Oversigt over navigationsindstillinger

Konfiguration af navigationsudbydere kan påvirke ydeevnen markant for hele webstedet, og du skal være opmærksom på at vælge en navigationsudbyder og en konfiguration, der skaleres effektivt i forhold til kravene på et SharePoint websted. Der er to klar til brugsnavigationsudbydere samt brugerdefinerede navigationsimplementeringer.

Den første indstilling [**, Strukturel navigation**](#using-structural-navigation-in-sharepoint-online), er den anbefalede navigationsindstilling i SharePoint Online for klassiske SharePoint websteder, **hvis du aktiverer strukturel cachelagring af navigation for dit websted**. Denne navigationsudbyder viser navigationselementerne under det aktuelle websted og eventuelt det aktuelle websted og dets sidestillede. Den indeholder yderligere funktioner, f.eks. justering af sikkerhed og optælling af webstedsstruktur. Hvis cachelagring er deaktiveret, påvirker det ydeevnen og skalerbarheden negativt, og det kan være underlagt begrænsning.

Den anden indstilling, [**Administreret (metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), repræsenterer navigationselementer ved hjælp af et ordsæt for administrerede metadata. Vi anbefaler, at justering af sikkerhed deaktiveres, medmindre det er nødvendigt. Justering af sikkerhed er aktiveret som en sikker standardindstilling for denne navigationsudbyder. Mange websteder kræver dog ikke udgifter til justering af sikkerhed, da navigationselementer ofte er konsistente for alle brugere af webstedet. Med den anbefalede konfiguration til deaktivering af justering af sikkerhed kræver denne navigationsprovider ikke optælling af webstedsstruktur og er yderst skalerbar med acceptabel påvirkning af ydeevnen.

Ud over de indbyggede navigationsudbydere har mange kunder implementeret alternative brugerdefinerede navigationsimplementeringer. Se [Søgebaseret scripting på klientsiden](#using-search-driven-client-side-scripting) i denne artikel.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Fordele og ulemper ved SharePoint indstillinger for onlinenavigation

I følgende tabel opsummeres fordele og ulemper ved hver indstilling.

|Strukturel navigation  |Administreret navigation  |Søgebaseret navigation  |Brugerdefineret navigationsprovider  |
|---------|---------|---------|---------|
|Fordele:<br/><br/>Let at vedligeholde<br/>Sikkerhed trimmet<br/>Opdateres automatisk inden for 24 timer, når indholdet ændres<br/>     |Fordele:<br/><br/>Let at vedligeholde<br/>|Fordele:<br/><br/>Sikkerhed trimmet<br/>Opdateres automatisk, når websteder tilføjes<br/>Hurtig indlæsningstid og lokalt cachelagret navigationsstruktur<br/>|Fordele:<br/><br/>Større udvalg af tilgængelige indstillinger<br/>Hurtig indlæsning ved cachelagring bruges korrekt<br/>Mange indstillinger fungerer godt med dynamisk sidedesign<br/>|
|Ulemper:<br/><br/>**Påvirker ydeevnen, hvis cachelagring er deaktiveret**<br/>Underlagt begrænsning<br/>|Ulemper:<br/><br/>Ikke automatisk opdateret for at afspejle webstedsstrukturen<br/>**Påvirker ydeevnen, hvis justering af sikkerhed er aktiveret** , eller når navigationsstrukturen er kompleks<br/>|Ulemper:<br/><br/>Ingen mulighed for nemt at bestille websteder<br/>Kræver tilpasning af mastersiden (tekniske færdigheder kræves)<br/>|Ulemper:<br/><br/>Brugerdefineret udvikling er påkrævet<br/>Der kræves en ekstern datakilde/cachelagret, f.eks. Azure<br/>|

Den mest relevante indstilling for dit websted afhænger af kravene til dit websted og af din tekniske funktionalitet. Hvis du vil have en navigationsudbyder, der er nem at konfigurere, og som automatisk opdateres, når indholdet ændres, er strukturel navigation [med cachelagring aktiveret](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) en god mulighed.

>[!NOTE]
>Anvendelse af det samme princip som moderne SharePoint websteder ved at forenkle den overordnede webstedsstruktur til en fladere, ikke-hierarkisk struktur forbedrer ydeevnen og forenkler flytningen til moderne SharePoint websteder. Det betyder, at i stedet for at have en enkelt gruppe af websteder med hundredvis af websteder (underordnede websteder), er en bedre tilgang at have mange grupper af websteder med meget få underordnede websteder (underordnede websteder).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>Analyse af navigationsydeevnen i SharePoint Online

[Værktøjet Sidediagnosticering til SharePoint](./page-diagnostics-for-spo.md) er en browserudvidelse til Microsoft Edge- og Chrome-browsere, der analyserer både SharePoint moderne portalsider online og klassiske udgivelseswebstedssider. Dette værktøj fungerer kun for SharePoint Online og kan ikke bruges på en SharePoint systemside.

Værktøjet genererer en rapport for hver analyseret side, der viser, hvordan siden klarer sig i forhold til et foruddefineret sæt regler, og viser detaljerede oplysninger, når resultaterne for en test falder uden for den oprindelige værdi. SharePoint Onlineadministratorer og -designere kan bruge værktøjet til at foretage fejlfinding af problemer med ydeevnen for at sikre, at nye sider optimeres inden publicering.

**SpRequestDuration** er især den tid, det tager for SharePoint at behandle siden. Tung navigation (f.eks. med sider i navigationen), komplekse webstedshierarkier og andre konfigurations- og topologiindstillinger kan alle dramatisk bidrage til længere varigheder.

## <a name="using-structural-navigation-in-sharepoint-online"></a>Brug af strukturel navigation i SharePoint Online

Dette er den direkte navigation, der bruges som standard, og det er den mest enkle løsning. Det kræver ingen tilpasning, og en ikke-teknisk bruger kan også nemt tilføje elementer, skjule elementer og administrere navigationen fra indstillingssiden. Vi anbefaler [, at du aktiverer cachelagring](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), ellers sker der en dyr afvejning af ydeevnen.

### <a name="how-to-implement-structural-navigation-caching"></a>Sådan implementerer du cachelagring af strukturel navigation

Under **Site Indstillinger** >  **Look og FeelNavigation** >  kan du validere, om strukturel navigation er valgt til enten global navigation eller aktuel navigation. Hvis du vælger **Vis sider** , påvirker det ydeevnen negativt.

![Strukturel navigation med Vis underordnede websteder valgt.](../media/SPONavOptionsStructuredShowSubsites.png)

Cachelagring kan aktiveres eller deaktiveres på niveauet for gruppen af websteder og på webstedsniveau og er som standard aktiveret for begge. Hvis du vil aktivere på niveauet for gruppen af websteder, skal du markere afkrydsningsfeltet **for Aktivér cachelagring** under **Websted Indstillinger** >  **Administrationsgruppe** >  af websteder.

![Aktivér cachelagring på webstedsniveau.](../media/structural-nav/structural-nav-caching-site-coll.png)

Hvis du vil aktivere på webstedsniveau, **skal du under Websted Indstillinger** >  **Navigation** markere afkrydsningsfeltet for **Aktivér cachelagring**.

![Aktivér cachelagring på webstedsniveau.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Brug af administreret navigation og metadata i SharePoint Online

Administreret navigation er endnu en køreklar indstilling, som du kan bruge til at genskabe de fleste af de samme funktioner som strukturel navigation. Administrerede metadata kan konfigureres, så justering af sikkerhed er aktiveret eller deaktiveret. Når den er konfigureret med justering af sikkerhed deaktiveret, er administreret navigation forholdsvis effektiv, da den indlæser alle navigationslinks med et konstant antal serverkald. Aktivering af justering af sikkerhed ophæver dog nogle af ydelsesfordelene ved administreret navigation.

Hvis du har brug for at aktivere justering af sikkerhed, anbefaler vi, at du:

- Opdater alle læsevenlige URL-links til enkle links
- Tilføj påkrævede justeringsnoder for sikkerhed som læsevenlige URL-adresser
- Begræns antallet af navigationselementer til højst 100 og højst tre niveauer dybt

Mange websteder kræver ikke justering af sikkerheden, da navigationsstrukturen ofte er ensartet for alle brugere af webstedet. Hvis justering af sikkerhed er deaktiveret, og der føjes et link til navigationen, som ikke alle brugere har adgang til, vises linket stadig, men det medfører en meddelelse om adgang nægtet. Der er ingen risiko for utilsigtet adgang til indholdet.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Sådan implementerer du administreret navigation og resultaterne

Der er flere artikler om docs.microsoft.com om detaljerne for administreret navigation. Du kan f.eks. se [Oversigt over administreret navigation i SharePoint Server](/sharepoint/administration/overview-of-managed-navigation).

Hvis du vil implementere administreret navigation, skal du konfigurere ord med URL-adresser, der svarer til webstedets navigationsstruktur. Administreret navigation kan endda organiseres manuelt for at erstatte strukturel navigation i mange tilfælde. Eksempel:

![SharePoint onlinewebstedsstruktur.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Brug af søgebaseret scripting på klientsiden

En almindelig klasse af brugerdefinerede navigationsimplementeringer omfatter designmønstre, der gengives af klienter, og som gemmer en lokal cache med navigationsnoder.

Disse navigationsudbydere har et par vigtige fordele:

- De fungerer generelt godt med dynamiske sidedesign.
- De er yderst skalerbare og højtydende, fordi de kan gengives uden ressourceomkostninger (og opdateres i baggrunden efter en timeout).
- Disse navigationsudbydere kan hente navigationsdata ved hjælp af forskellige strategier lige fra simple statiske konfigurationer til forskellige dynamiske dataprovidere.

Et eksempel på en dataprovider er at bruge en **søgebaseret navigation**, som giver fleksibilitet til at optæde navigationsnoder og håndtere justering af sikkerhed effektivt.

Der er andre populære muligheder for at bygge **brugerdefinerede navigationsudbydere**. Gennemse [Navigationsløsninger for SharePoint Online-portaler](/sharepoint/dev/solution-guidance/portal-navigation) for at få yderligere vejledning i, hvordan du bygger en brugerdefineret navigationsudbyder.

Ved hjælp af søgning kan du udnytte de indekser, der er bygget op i baggrunden, ved hjælp af fortløbende gennemsøgning. Søgeresultaterne hentes fra søgeindekset, og resultaterne er sikkerhedsbeskåret. Dette er generelt hurtigere end køreklare navigationsudbydere, når justering af sikkerhed er påkrævet. Hvis du bruger søgning til strukturel navigation, især hvis du har en kompleks webstedsstruktur, vil det fremskynde indlæsningstiden for sider betydeligt. Den største fordel ved dette i forhold til administreret navigation er, at du kan drage fordel af justering efter sikkerhed.

Denne fremgangsmåde omfatter oprettelse af en brugerdefineret masterside og erstatning af den indbyggede navigationskode med brugerdefineret HTML. Følg denne procedure, der er beskrevet i følgende eksempel, for at erstatte navigationskoden i filen `seattle.html`. I dette eksempel skal du åbne `seattle.html` filen og erstatte hele elementet `id="DeltaTopNavigation"` med brugerdefineret HTML-kode.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Eksempel: Erstat den indbyggede navigationskode på en masterside

1. Gå til siden Websted Indstillinger.
2. Åbn mastersidegalleriet ved at klikke på **Mastersider**.
3. Herfra kan du navigere gennem biblioteket og downloade filen `seattle.master`.
4. Rediger koden ved hjælp af en teksteditor, og slet kodeblokken i følgende skærmbillede.<br/>![Slet den viste kodeblok.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Fjern koden mellem mærkerne og `<\SharePoint:AjaxDelta>` , `<SharePoint:AjaxDelta id="DeltaTopNavigation">` og erstat den med følgende kodestykke:<br/>

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
6. Erstat URL-adressen i ankermærket til indlæsning af billeder i starten med et link til et indlæsningsbillede i din gruppe af websteder. Når du har foretaget ændringerne, skal du omdøbe filen og derefter overføre den til mastersidegalleriet. Dette genererer en ny .master-fil.<br/>
7. Denne HTML er den grundlæggende markering, der udfyldes af de søgeresultater, der returneres fra JavaScript-kode. Du skal redigere koden for at ændre værdien for var root = "URL-adresse for gruppe af websteder" som vist i følgende kodestykke:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Resultaterne tildeles til matrixen self.nodes, og et hierarki er bygget ud af objekterne ved hjælp af linq.js tildele outputtet til et matrix self.hierarchy. Denne matrix er det objekt, der er bundet til HTML-koden. Dette gøres i funktionen til/fra() ved at overføre selvobjektet til funktionen ko.applyBinding().<br/>Dette medfører derefter, at hierarkimatrixen bindes til følgende HTML:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

Hændelseshandlerne for `mouseenter` og `mouseexit` føjes til navigationen på øverste niveau for at håndtere rullemenuerne for det underordnede websted, som udføres i funktionen `addEventsToElements()` .

I vores komplekse navigationseksempel viser en ny sidebelastning uden den lokale cachelagring, at den tid, der bruges på serveren, er blevet skåret ned fra benchmarkets strukturelle navigation for at få et lignende resultat som den administrerede navigationstilgang.

### <a name="about-the-javascript-file"></a>Om JavaScript-filen...

>[!NOTE]
>Hvis du bruger brugerdefineret JavaScript, skal du kontrollere, at offentlige CDN er aktiveret, og at filen er på en CDN placering.

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

For at opsummere den kode, der vises ovenfor i funktionen `jQuery $(document).ready` , oprettes der en `viewModel object` , og derefter kaldes funktionen for `loadNavigationNodes()` det pågældende objekt. Denne funktion indlæser enten det tidligere opbyggede navigationshierarki, der er gemt i det lokale HTML5-lager i klientbrowseren, eller den kalder funktionen `queryRemoteInterface()`.

`QueryRemoteInterface()` opretter en anmodning ved hjælp af funktionen `getRequest()` med den forespørgselsparameter, der er defineret tidligere i scriptet, og returnerer derefter data fra serveren. Disse data er grundlæggende en matrix af alle de websteder i gruppen af websteder, der repræsenteres som dataoverførselsobjekter med forskellige egenskaber.

Disse data fortolkes derefter i de tidligere definerede `SPO.Models.NavigationNode` objekter, som bruger `Knockout.js` til at oprette observerede egenskaber til brug af data, der binder værdierne til den HTML, vi definerede tidligere.

Objekterne placeres derefter i en resultatmatrix. Denne matrix fortolkes i JSON ved hjælp af Knockout og gemmes i det lokale browserlager for at forbedre ydeevnen ved fremtidige sidebelastninger.

### <a name="benefits-of-this-approach"></a>Fordele ved denne fremgangsmåde

En stor fordel ved [denne fremgangsmåde](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) er, at navigationen gemmes lokalt for brugeren, næste gang siden indlæses, ved hjælp af det lokale HTML5-lager. Vi får større forbedringer af ydeevnen ved at bruge søge-API'en til strukturel navigation. Det kræver dog nogle tekniske funktioner at udføre og tilpasse denne funktionalitet.

I [eksempelimplementering](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) sorteres webstederne på samme måde som den indbyggede strukturnavigation. alfabetisk rækkefølge. Hvis du vil afvige fra denne ordre, ville det være mere kompliceret at udvikle og vedligeholde. Denne fremgangsmåde kræver også, at du afviger fra de understøttede mastersider. Hvis den brugerdefinerede masterside ikke vedligeholdes, går dit websted glip af opdateringer og forbedringer, som Microsoft foretager på mastersiderne.

[Ovenstående kode](#about-the-javascript-file) har følgende afhængigheder:

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/eller github.com/neuecc/linq.js

Den aktuelle version af LinqJS indeholder ikke metoden ByHierarchy, der bruges i ovenstående kode, og ødelægger navigationskoden. Du kan løse problemet ved at føje følgende metode til filen Linq.js før linjen `Flatten: function ()`.

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

[Oversigt over administreret navigation på SharePoint server](/sharepoint/administration/overview-of-managed-navigation)

[Cachelagring og ydeevne for strukturel navigation](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)