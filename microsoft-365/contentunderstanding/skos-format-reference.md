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
ms.openlocfilehash: 95183b64d76a70f69d08cd5a3c9dcf76f4e83bce
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63591684"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>SKOS-formatreference til SharePoint taksonomi

Denne artikel indeholder RDF-terminologi, der bruges [til SharePoint taksonomi](/dotnet/api/microsoft.sharepoint.taxonomy) og er baseret på [SKOS](https://www.w3.org/TR/skos-primer/). Brug RDF SKILDPADDE til serialisering af denne [RDF-syntaks](https://www.w3.org/TR/turtle/).

I følgende tabel vises [de tilsvarende SKOS-værdier](https://www.w3.org/TR/skos-primer/) for [SharePoint terminologi](/dotnet/api/microsoft.sharepoint.taxonomy). SharePoint understøtter ikke [SKOS-værdier](https://www.w3.org/TR/skos-primer/), der ikke SharePoint ens taksonomi.

|SharePoint taksonomi|SKOS-ækvivalent|
|:-----------------|:--------------|
|sharepoint-taxonomy:Term|skos:Concept|
|sharepoint-taksonomi:TermSet|skos:ConceptScheme|
|sharepoint-taksonomi:inTermSet|skos:inScheme|
|sharepoint-taksonomi:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taksonomi:topLevelTermOf|skos:topConceptOf|
|sharepoint-taxonomy:defaultLabel|skos:prefLabel|
|sharepoint-taxonomy:termSetName|skos:prefLabel|
|sharepoint-taxonomy:propertyName|skos:prefLabel|
|sharepoint-taxonomy:otherLabel|skos:altLabel|
|sharepoint-taxonomy:description|skos:definition|
|sharepoint-taksonomi:overordnet|skos:broader|
|sharepoint-taxonomy:child|skos:narrower|

I følgende tabel vises de enheder af SharePoint terminologi, der er afledt af [OWL](https://www.w3.org/TR/owl2-primer/).

|SharePoint terminologi|Afledt af OWL|
|:-----------------------------|:----------------------|
|sharepoint-taxonomy:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-taxonomy:SharedCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomi:LocalCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taksonomi:CustomPropertyForTermSet|owl:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>SharePoint terminologi

Et taksonomi er et formelt klassificeringssystem. En taksonomi grupperer de ord, etiketter og ord, der beskriver noget, og arrangerer derefter grupperne i et hierarki.

**sharepoint-taxonomy:Term**

Repræsenterer et Ord eller et Nøgleord i et administreret metadatahierarki.

Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) er atomenheden i en SharePoint [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Hvert [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) tilhører et [TermSet,](/dotnet/api/microsoft.sharepoint.taxonomy.termset) der tilhører en [Ordgruppe](/dotnet/api/microsoft.sharepoint.taxonomy.group).

Syntaksen til at definere [et ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) er som følger:

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Et [Udtryk, der](/dotnet/api/microsoft.sharepoint.taxonomy.term) er ily, findes [inden for et TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel er navnet på ordet [, som](/dotnet/api/microsoft.sharepoint.taxonomy.term) det vises i den visuelle repræsentation. De påkrævede felter til definition af et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) omfatter:

- sharepoint-taxonomy:defaultLabel
- sharepoint-taksonomi:inTermSet

Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan:

- Være hierarkisk relateret til et [andet ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) , der er angivet [, og begge](/dotnet/api/microsoft.sharepoint.taxonomy.term) vilkår tilhører det samme [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Have flere underordnede [vilkår](/dotnet/api/microsoft.sharepoint.taxonomy.term), men kun en enkelt overordnet [periode](/dotnet/api/microsoft.sharepoint.taxonomy.term).
- Der er ikke defineret [et overordnet](/dotnet/api/microsoft.sharepoint.taxonomy.term) ord, hvis det er en topLevelTermOf a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Har ét defaultLabel pr. [TermStore-arbejdssprog](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .
- Findes ikke, hvis den ikke indeholder et [overordnet ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) og heller ikke er topLevelTermOf a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Have kun et entydigt standardmærkat på samme hierarkiske niveau.

**sharepoint-taksonomi:TermSet**

Repræsenterer et hierarkisk eller fladt sæt af Ord-objekter kaldet "TermSet".

Som navnet antyder, er TermSet et sæt [vilkår](/dotnet/api/microsoft.sharepoint.taxonomy.term). Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) i en [Ordstore skal](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) høre til et [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Intet [ord kan](/dotnet/api/microsoft.sharepoint.taxonomy.term) findes uafhængigt af hinanden.

Syntaksen til at definere [et Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er:

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

[Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er logisk grupperet sammen i [Ordgrupper](/dotnet/api/microsoft.sharepoint.taxonomy.group). Det felt, der skal bruges til at definere [et Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) , er:

- sharepoint-taxonomy:termSetName

Med det angivne ordSetName er ikke entydigt i [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group), tilføjer SharePoint et tal i slutningen af navnet for at bevare entydigheden for termSetName(s).

**sharepoint-taksonomi:hasTopLevelTerm**

SharePoint denne egenskab til at tilknytte det mest ord i [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset), som er indgangspunktet til hierarkiet af [Ord i et](/dotnet/api/microsoft.sharepoint.taxonomy.term) [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).[](/dotnet/api/microsoft.sharepoint.taxonomy.term) Dette er en invers relation til sharepoint-taksonomi:topLevelTermOf.

Syntaksen til at definere dette er:

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Du kan ikke definere ordet på øverste [niveau](/dotnet/api/microsoft.sharepoint.taxonomy.term) for et overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

**sharepoint-taksonomi:topLevelTermOf**

Sharepoint-taksonomi:topLevelTermOf er den inverse af sharepoint-taksonomi:hasTopLevelTerm

Syntaksen til at definere dette er:

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taksonomi:inTermSet**

Brug dette til at knytte [et ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) til et [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan kun findes i et enkelt [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint kræver denne egenskab, når du [definerer et ord](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/blob/3a3cd54dd076b18bdff1d43b3e342897f8704c23/microsoft-365/contentunderstanding/skos-format-reference.md#term).

## <a name="required-labels"></a>Påkrævede etiketter

Det kan være en god ide for din organisation at planlægge nøje, før du begynder at bruge administrerede metadata. Hvor meget planlægning du skal udføre, afhænger af, hvor formel din taksonomi er. Det afhænger også af, hvor meget kontrol du vil påtvinge metadata. På hvert niveau i hierarkiet skal du konfigurere nødvendige navne for et ord eller et Ordsæt.

Et ord kan have en eller flere etiketter på standardsproget, og der kan være nul eller flere etiketter på det sprog, der ikke er standard. Hvis ordet har etiketter på et sprog, skal en af etiketterne være standardetiketten.

**sharepoint-taxonomy:defaultLabel**

Brug dette standardleksiket for et [ord,](/dotnet/api/microsoft.sharepoint.taxonomy.term) der er en påkrævet parameter for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term). Bruges til visuelt at repræsentere [ordet](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere et defaultLabel er:

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

DefaultLabel indeholder to dele – strengen og sprogkoden. Sproget skal være et af [TermStore-arbejdssprogene](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . DefaultLabel skal være entydigt for [alle vilkår](/dotnet/api/microsoft.sharepoint.taxonomy.term) i samme [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) på det samme hierarkiske niveau.

**sharepoint-taxonomy:termSetName**

Henter og angiver navnet på det aktuelle TermSet-objekt.

Dette er den lexiske etiket for [et TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) i et [TermStore-arbejdssprog](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Dette er en påkrævet parameter for et [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Bruges til visuelt at repræsentere et [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

Syntaksen til at definere et ordNavn er:

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taxonomy:propertyName**

Henter og angiver egenskabsnavnet for det aktuelle TermSet-objekt.

Dette er den lexical etiket for en sharepoint-taksonomi:SharedCustomPropertyForTerm, sharepoint-taxonomy:LocalCustomPropertyForTerm og sharepoint-taxonomy:CustomPropertyForTermSet på et [TermStore-arbejdssprog](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

Sharepoint-taksonomi:egenskabNavn behandles som nøglen til CustomProperty.

Syntaksen til at definere et propetyName er:

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>Valgfrie etiketter

Du kan også føje valgfrie etiketter til din taksonomi.

**sharepoint-taxonomy:otherLabel**

Dette er den alternative eksikale etiket for et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere et andetLabel er:

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Semantiske relationer

Taksonomier har hierarkiske og nogle gange et simpelt "relateret udtryk" tilknytningsrelation, men nogle har "semantiske relationer" eller brugerdefinerede relationer.

**sharepoint-taksonomi:overordnet**

Dette hierarkisk relaterer et [ord til](/dotnet/api/microsoft.sharepoint.taxonomy.term) et andet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term). Et [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) kan være et ord på [øverste niveau Ord](/dotnet/api/microsoft.sharepoint.taxonomy.term) for et [Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset), men i tilfælde af at det ikke skal have et overordnet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere en overordnet er:

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Det betyder, at TermA er forælder, og TermA er det underordnede ord.

**sharepoint-taxonomy:child**

Objektet indeholder en eller flere underordnede TermSet-forekomster, og disse kan åbnes via egenskaben Ordsæt. Denne klasse indeholder også metoder til at oprette nye underordnede TermSet-objekter. Tilladelser til redigering af underordnede forekomster af Ord og Ordsæt er angivet på gruppen.

Dette hierarkisk relaterer et [ord til](/dotnet/api/microsoft.sharepoint.taxonomy.term) et andet [ord](/dotnet/api/microsoft.sharepoint.taxonomy.term).

Syntaksen til at definere et underordnet barn er:

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Det betyder, at TermA er forælder, og TermA er det underordnede ord.

## <a name="documentation-notes"></a>Dokumentationsnoter

I dette afsnit beskrives den taksonomi, der er beskrevet i Microsoft. SharePoint. Navneområde for taksonomi.

**sharepoint-taxonomy:description**

Dette er en detaljeret forklaring af [SharePoint terminologi-enhed](/dotnet/api/microsoft.sharepoint.taxonomy).

Syntaksen for at tilføje en beskrivelse er:

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Brugerdefinerede egenskaber

Henter samlingen af brugerdefinerede egenskabsobjekter for det aktuelle Ord-objekt fra den skrivebeskyttede ordbog.

Brugerdefinerede egenskaber er nøgleværdipar, der kan defineres for et ord [](/dotnet/api/microsoft.sharepoint.taxonomy.term) eller et [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) for yderligere at få en beskrivelse af [ordet eller et](/dotnet/api/microsoft.sharepoint.taxonomy.term) [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint angiver nøglen til den brugerdefinerede egenskab ved hjælp af propertyName.

**sharepoint-taksonomi:CustomPropertyForTermSet**

Syntaksen til at definere dette er:

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taxonomy:SharedCustomPropertyForTerm**

Hvis den brugerdefinerede egenskab for [](/dotnet/api/microsoft.sharepoint.taxonomy.term) et ord skal udføres sammen med [ordet, skal](/dotnet/api/microsoft.sharepoint.taxonomy.term) du definere den under SharedCustomPropertyForTerm, når du genbruger ordet et andet sted.[](/dotnet/api/microsoft.sharepoint.taxonomy.term)

Syntaksen til at definere dette er:

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taksonomi:LocalCustomPropertyForTerm**

Hvis den brugerdefinerede egenskab for [](/dotnet/api/microsoft.sharepoint.taxonomy.term) et ord ikke behøver at være med sammen med [ordet, når](/dotnet/api/microsoft.sharepoint.taxonomy.term) du genbruger ordet [](/dotnet/api/microsoft.sharepoint.taxonomy.term) et andet sted, skal du definere den under LocalCustomPropertyForTerm.

Syntaksen til at definere dette er:

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Dataegenskaber

På hvert niveau i hierarkiet kan du konfigurere bestemte dataegenskaber for et ord eller et Ordsæt.

**sharepoint-taxonomy:isAvailableForTagging**

Brug dette til at angive, [om et](/dotnet/api/microsoft.sharepoint.taxonomy.term) ord [eller et Ordsæt](/dotnet/api/microsoft.sharepoint.taxonomy.termset) er tilgængeligt SharePoint Lister og biblioteker.

Syntaksen for dette er:

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Domæne og område

Nedenstående tabel beskriver domænet og området af SharePoint terminologi.

|Prædikater/verber|Betydning|Domæne|Område|
|:--------------|:------|:-----|:----|
inTermSet|I ordsæt|Ord|Ordsæt|
inTermGroup|I ordgruppe|TermSet|Ordgruppe|
topLevelTermOf|Is Top Level Term Of|Ord|TermSet|
hasTopLevelTerm|Har ordet på øverste niveau|Ordsæt|Ord|
termSetName|Ordsæt har Navn|Ord|Almindelig konstant|
defaultLabel|Ord har standardetiket|Ord|Almindelig konstant|
otherLabel|Ordet har en anden etiket|Ord|Almindelig konstant|
propertyName|Har egenskabsnavn|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Boolesk, Streng, Heltal, Decimal, Dobbelt|
|beskrivelse|Har Beskrivelse|Alle|Almindelig konstant|
|forælder|Har forældre|Ord|Ord|
|barn|Har barn|Ord|Ord|
|isAvailableForTagging|Er tilgængelig til mærkning|Ord, ordsæt|Boolesk |
|SharedCustomPropertyForTerm|Har en delt brugerdefineret egenskab|Ord|Boolesk, streng, heltal, decimal, dobbelt|
|LocalCustomPropertyForTerm|Har en lokal brugerdefineret egenskab|Ord|Boolesk, Streng, Heltal, Decimal, Dobbelt|
|CustomPropertyForTermSet|Egenskaben Har brugerdefineret|TermSet|Boolesk, Streng, Heltal, Decimal, Dobbelt|

[SKOS](https://www.w3.org/TR/skos-primer/) gyldige scenarier, [SharePoint taksonomi](/dotnet/api/microsoft.sharepoint.taxonomy) ikke tillader:

- Hierarkisk redundans – Et [SKOS-koncept](https://www.w3.org/TR/skos-primer/) kan knyttes til flere bredere begreber på samme tid, men en sharepoint-taksonomi:Ord kan kun have én sharepoint-taksonomi:overordnet, og derfor er cyklisk afhængighed af vilkår heller ikke tilladt.
- Uafhængige ord er ikke tilladt i SharePoint taksonomi. Hver sharepoint-taksonomi:Ord skal enten have en sharepoint-taksonomi:overordnet, eller det skal være sharepoint-taksonomi:topLevelTermAf et TermSet.
- SharePoint taksonomi understøtter ikke tilknytningsrelationer.
- SharePoint taksonomi tillader kun to typer hierarkiske relationer – sharepoint-taksonomi:overordnet og sharepoint-taksonomi:underordnet.
- I [modsætning til SKOS](https://www.w3.org/TR/skos-primer/) kan den hierarkiske relation SharePoint terminologi kun etableres med Vilkår inden for samme TermSet.

## <a name="see-also"></a>Se også

[Importere et ordsæt ved hjælp af et SKOS-baseret format](import-term-set-skos.md)