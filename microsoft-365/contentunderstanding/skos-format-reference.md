---
title: SKOS-formatreference til SharePoint taksonomi
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: SKOS-formatreference til SharePoint taksonomi
ms.openlocfilehash: c9dbaae4242155522eec2fff0f7fd4d721e697cc
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139667"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>SKOS-formatreference til SharePoint taksonomi

Denne artikel indeholder RDF-ordforråd, der bruges til at repræsentere [SharePoint taksonomi](/dotnet/api/microsoft.sharepoint.taxonomy) og er baseret på [SKOS](https://www.w3.org/TR/skos-primer/). Brug RDF [TURTLE](https://www.w3.org/TR/turtle/) til serialisering af denne RDF-syntaks.

I følgende tabel vises [SKOS-ækvivalenterne](https://www.w3.org/TR/skos-primer/) for [ordforrådet for SharePoint taksonomi](/dotnet/api/microsoft.sharepoint.taxonomy). SharePoint understøtter ikke [SKOS-værdier](https://www.w3.org/TR/skos-primer/), der ikke har nogen tilsvarende SharePoint taksonomi.

|SharePoint taksonomi|Tilsvarende SKOS|
|:-----------------|:--------------|
|sharepoint-taksonomi:Ord|skos:Concept|
|sharepoint-taksonomi:TermSet|skos:ConceptScheme|
|sharepoint-taksonomi:inTermSet|skos:inScheme|
|sharepoint-taksonomi:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taksonomi:topLevelTermOf|skos:topConceptOf|
|sharepoint-taksonomi:defaultLabel|skos:prefLabel|
|sharepoint-taksonomi:termSetName|skos:prefLabel|
|sharepoint-taksonomi:propertyName|skos:prefLabel|
|sharepoint-taksonomi:otherLabel|skos:altLabel|
|sharepoint-taksonomi:beskrivelse|skos:definition|
|sharepoint-taksonomi:overordnet|skos:bredere|
|sharepoint-taksonomi:child|skos:smallere|

I følgende tabel vises enhederne for det SharePoint taksonomiforråd, der er afledt af [OWL](https://www.w3.org/TR/owl2-primer/).

|SharePoint taksonomiforråd|Afledt af OWL|
|:-----------------------------|:----------------------|
|sharepoint-taksonomi:isAvailableForTagging|ugle:datatypeegenskab|
|sharepoint-taksonomi:SharedCustomPropertyForTerm|ugle:ObjectProperty|
|sharepoint-taksonomi:LocalCustomPropertyForTerm|ugle:ObjectProperty|
|sharepoint-taksonomi:CustomPropertyForTermSet|ugle:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>SharePoint taksonomiforråd

En taksonomi er et formelt klassificeringssystem. En taksonomi grupperer de ord, navne og ord, der beskriver noget, og arrangerer derefter grupperne i et hierarki.

**sharepoint-taksonomi:Ord**

Repræsenterer et ord eller et nøgleord i et administreret metadatahierarki.

Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) er den atomiske enhed i en SharePoint [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Hvert [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) tilhører et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) , der tilhører en [ordgruppe](/dotnet/api/microsoft.sharepoint.taxonomy.group).

Syntaksen til at definere et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) er som følger:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Der [](/dotnet/api/microsoft.sharepoint.taxonomy.term) findes en ordkompulsorit i et [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel er navnet på [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term) , som det vises i den visuelle repræsentation. De obligatoriske felter til definition af et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) omfatter:

- sharepoint-taksonomi:defaultLabel
- sharepoint-taksonomi:inTermSet

Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan:

- Vær hierarkisk relateret til et andet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) , der er angivet, at begge [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) tilhører det samme [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Har flere underordnede [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term), men kun et enkelt overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).
- Der er ikke defineret et overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) , hvis det er topLevelTermOf et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Har én defaultLabel pr. [TermStore-arbejdssprog](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .
- Findes ikke, hvis det hverken indeholder et overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) eller er topLevelTermOf et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Har kun en entydig defaultLabel på samme hierarkiske niveau.

**sharepoint-taksonomi:TermSet**

Repræsenterer et hierarkisk eller fladt sæt ordobjekter, der kaldes et "Ordsæt".

Som navnet antyder, er TermSet et sæt [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term). Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) i en [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) skal tilhøre et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Intet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan eksistere uafhængigt af hinanden.

Syntaksen til at definere et [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

[TermSets](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er logisk grupperet i [TermGroups](/dotnet/api/microsoft.sharepoint.taxonomy.group). Det obligatoriske felt til definition af et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er:

- sharepoint-taksonomi:termSetName

Hvis det angivne termSetName ikke er entydigt i [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group), tilføjer SharePoint et tal i slutningen af navnet for at bevare entydigheden af termSetName(s).

**sharepoint-taksonomi:hasTopLevelTerm**

SharePoint bruger denne egenskab til at knytte det øverste [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) i [ordsættet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), som er indgangspunktet til hierarkiet af [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) i et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Dette er en omvendt relation til sharepoint-taksonomi:topLevelTermOf.

Syntaksen til at definere dette er:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Du kan ikke definere [ordet på øverste](/dotnet/api/microsoft.sharepoint.taxonomy.term) niveau for et overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

**sharepoint-taksonomi:topLevelTermOf**

Sharepoint-taksonomi:topLevelTermOf er det omvendte af sharepoint-taksonomi:hasTopLevelTerm

Syntaksen til at definere dette er:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taksonomi:inTermSet**

Brug dette til at knytte et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) til et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan kun findes i et enkelt [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint kræver denne egenskab, når [du definerer et ord](#sharepoint-taxonomy-vocabulary).

## <a name="required-labels"></a>Obligatoriske navne

Din organisation vil måske foretage omhyggelig planlægning, før du begynder at bruge administrerede metadata. Mængden af planlægning, som du skal gøre, afhænger af, hvor formel din taksonomi er. Det afhænger også af, hvor meget kontrol du vil pålægge metadata. På hvert niveau i hierarkiet skal du konfigurere påkrævede mærkater for et ord eller et ordsæt.

Et ord kan have et eller flere navne på standardsproget og nul eller flere navne på det ikke-standardsprog. Hvis ordet har navne på et sprog, skal et af navnene være standardnavnet.

**sharepoint-taksonomi:defaultLabel**

Brug denne leksikalske standardetiket til et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) , der er en påkrævet parameter for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term). Bruges til visuelt at repræsentere [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere en defaultLabel er:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

DefaultLabel indeholder to dele til den – strengen og sprogkoden. Sproget skal være et af [TermStore-arbejdssprogene](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . DefaultLabel skal være entydig for alle [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) i det samme [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) på samme hierarkiske niveau.

**sharepoint-taksonomi:termSetName**

Henter og angiver navnet på det aktuelle TermSet-objekt.

Dette er den leksikalske mærkat for et [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) i et [arbejdssprog i TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Dette er en påkrævet parameter for et [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Bruges til visuelt at repræsentere et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

Syntaksen til at definere et termSetName er:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taksonomi:propertyName**

Henter og angiver egenskabsnavnet for det aktuelle TermSet-objekt.

Dette er den leksikalske mærkat for en sharepoint-taksonomi:SharedCustomPropertyForTerm, sharepoint-taxonomy:LocalCustomPropertyForTerm og sharepoint-taxonomy:CustomPropertyForTermSet i et [TermStore-arbejdssprog](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

Sharepoint-taksonomi:propertyName behandles som nøglen til CustomProperty.

Syntaksen til at definere et propetyName er:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>Valgfrie navne

Du kan også føje valgfrie mærkater til din taksonomi.

**sharepoint-taksonomi:otherLabel**

Dette er den alternative leksikalske mærkat for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere en otherLabel er:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Semantiske relationer

Taksonomier har hierarkiske og nogle gange et simpelt "relateret" associativt forhold, men nogle har "semantiske relationer" eller brugerdefinerede relationer.

**sharepoint-taksonomi:overordnet**

Dette hierarkisk relaterer et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) til et andet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term). Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan være et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) på øverste niveau i et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset), men hvis det ikke gør det, skal det have et overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere en overordnet er:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Det betyder, at TermA er det overordnede ord, og at TermA er underordnet.

**sharepoint-taksonomi:child**

Objektet indeholder en eller flere underordnede forekomster af TermSet, og disse kan tilgås via egenskaben TermSets. Denne klasse indeholder også metoder til oprettelse af nye underordnede TermSet-objekter. Der er angivet tilladelser til redigering af underordnede ord- og ordsætforekomster i gruppen.

Dette hierarkisk relaterer et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) til et andet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere et underordnet element er:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Det betyder, at TermA er det overordnede ord, og at TermA er underordnet.

## <a name="documentation-notes"></a>Dokumentationsnoter

I dette afsnit beskrives taksonomien, som er beskrevet i Microsoft. SharePoint. Taksonominavneområde.

**sharepoint-taksonomi:beskrivelse**

Dette er en detaljeret forklaring af alle [SharePoint taksonomiforrådsobjekt](/dotnet/api/microsoft.sharepoint.taxonomy).

Syntaksen for tilføjelse af en beskrivelse er:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Brugerdefinerede egenskaber

Henter samlingen af brugerdefinerede egenskabsobjekter for det aktuelle ordobjekt fra den skrivebeskyttede ordbog.

Brugerdefinerede egenskaber er nøgleværdipar, der kan defineres for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) eller et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) for at fremme beskrivelsen af [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term) eller et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint angiver nøglen til den brugerdefinerede egenskab ved hjælp af propertyName.

**sharepoint-taksonomi:CustomPropertyForTermSet**

Syntaksen til at definere dette er:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taksonomi:SharedCustomPropertyForTerm**

Hvis den brugerdefinerede egenskab for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) skal overføres sammen med [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term), skal du definere det under SharedCustomPropertyForTerm, når du genbruger [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term) et andet sted.

Syntaksen til at definere dette er:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taksonomi:LocalCustomPropertyForTerm**

Hvis den brugerdefinerede egenskab for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) ikke behøver at blive overført sammen med [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term), skal du definere det under LocalCustomPropertyForTerm, når du genbruger [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term) et andet sted.

Syntaksen til at definere dette er:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Dataegenskaber

På hvert niveau i hierarkiet kan du konfigurere specifikke dataegenskaber for et ord eller et ordsæt.

**sharepoint-taksonomi:isAvailableForTagging**

Brug denne til at angive, om et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) eller et [ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er tilgængeligt i SharePoint lister og biblioteker.

Syntaksen for dette er:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Domæne og område

I nedenstående tabel beskrives domænet og området for SharePoint taksonomiforråd.

|Prædikater/verbum|Betydning|Domæne|Vifte|
|:--------------|:------|:-----|:----|
inTermSet|I ordsæt|Udtrykket|Ordsæt|
inTermGroup|I ordgruppe|Ordsæt|Ordgruppe|
topLevelTermOf|Er ord på øverste niveau for|Udtrykket|Ordsæt|
hasTopLevelTerm|Har ord på øverste niveau|Ordsæt|Udtrykket|
termSetName|Ordsættet har navn|Udtrykket|Almindelig konstant|
defaultLabel|Ordet har en standardetiket|Udtrykket|Almindelig konstant|
otherLabel|Ordet har en anden etiket|Udtrykket|Almindelig konstant|
Propertyname|Har egenskabsetiket|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Boolesk, streng, heltal, decimal, dobbelt|
|Beskrivelse|Indeholder en beskrivelse|Alle|Almindelig konstant|
|Overordnede|Har overordnet|Udtrykket|Udtrykket|
|Barn|Har underordnet|Udtrykket|Udtrykket|
|isAvailableForTagging|Er tilgængelig til mærkning|Ord, ordsæt|Boolesk |
|SharedCustomPropertyForTerm|Har delt brugerdefineret egenskab|Udtrykket|Boolesk, streng, heltal, decimal, dobbelt|
|LocalCustomPropertyForTerm|Har lokal brugerdefineret egenskab|Udtrykket|Boolesk, streng, heltal, decimal, dobbelt|
|CustomPropertyForTermSet|Har brugerdefineret egenskab|Ordsæt|Boolesk, streng, heltal, decimal, dobbelt|

[SKOS](https://www.w3.org/TR/skos-primer/) gyldige scenarier, der [SharePoint taksonomi](/dotnet/api/microsoft.sharepoint.taxonomy) ikke tillader:

- Hierarkisk redundans – Et [SKOS-koncept](https://www.w3.org/TR/skos-primer/) kan knyttes til flere bredere begreber på samme tid, men en sharepoint-taksonomi:Term kan kun have én sharepoint-taksonomi:parent, og derfor cyklisk afhængighed, af Vilkår er heller ikke tilladt.
- Mistede ord er ikke tilladt i SharePoint taksonomi. Alle sharepoint-taksonomi:Term skal enten have en sharepoint-taksonomi:parent, eller det skal være sharepoint-taksonomi:topLevelTermOf et TermSet.
- SharePoint taksonomi understøtter ikke associative relationer.
- SharePoint taksonomi tillader kun to typer hierarkiske relationer – sharepoint-taksonomi:parent og sharepoint-Taxonomy:child.
- I modsætning til [SKOS](https://www.w3.org/TR/skos-primer/) kan den hierarkiske relation i SharePoint taksonomiforråd kun oprettes med ord i det samme ordsæt.

## <a name="see-also"></a>Se også

[Importér et ordsæt ved hjælp af et SKOS-baseret format](import-term-set-skos.md)
