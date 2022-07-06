---
title: Reference til filtre for brugerdefinerede følsomme oplysninger
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: I denne artikel vises en liste over de filtre, der kan kodes til brugerdefinerede følsomme oplysningstyper.
ms.openlocfilehash: 79e4a2520ab922248f65adf1b0506219987fe832
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631953"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Reference til filtre for brugerdefinerede følsomme oplysninger

I Microsoft kan du definere filtre eller andre kontroller, mens du opretter brugerdefinerede typer følsomme oplysninger (SIT).

## <a name="list-of-supported-filters-and-use-cases"></a>Liste over understøttede filtre og use cases

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Beskrivelse: Giver dig mulighed for at udelade match, der har alle cifre som dublerede cifre, f.eks. 111111111 eller 111-111-111

Definition af filtre
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

Brug den i regelpakken på enhedsniveau
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

Brug den i regelpakken på mønsterniveau
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

Beskrivelse: Giver dig mulighed for at definere starttegnene for enheden. Den har to varianter, inkluder og udelad.

Hvis du f.eks. vil udelade tal, der starter med 0500, 91, 091, 010 på en liste som denne:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Du kan bruge følgende XML

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>
</Filters>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```
Hvis du f.eks. vil inkludere tal, der starter med 0500, 91, 091, 0100, på en liste som denne: 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Du kan bruge følgende XML

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter slutter Med 

Beskrivelse: Giver dig mulighed for at definere sluttegnene for enheden. 

Hvis du f.eks. vil udelade de tal, der slutter med 0500.91.091, 0100 på en liste som denne:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Du kan bruge følgende XML

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="EndsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```

Hvis du f.eks. vil medtage tal, der slutter med 0500, 91, 091, 0100, på en liste som denne:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Du kan bruge følgende XML

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Fuld

Beskrivelse: Giver dig mulighed for at forbyde visse forekomster for at forhindre dem i at udløse reglen. Udelad f.eks. 4111111111111111 fra listen over gyldige kreditkortforekomster.

Hvis du f.eks. vil udelade kreditkortnumre som 4111111111111111 og 3241891031113111 på en liste som denne:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Du kan bruge følgende XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Full" logic="Exclude" textProcessorId="Keyword_false_positives_full">
</Filter>

  <Keyword id="Keyword_false_positives_full">
    <Group matchStyle="string">
      <Term>4111111111111111</Term>
      <Term>3241891031113111</Term>
    </Group>
  </Keyword>
```

Hvis du f.eks. vil medtage kreditkortnumre som 4111111111111111 og 3241891031113111 på en liste som denne:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Du kan bruge følgende XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>Præfiks for TextMatchFilter

Beskrivelse: Giver dig mulighed for at definere de foregående tegn, der altid skal medtages eller udelades. Hvis kreditkortnummeret f.eks. har 'Order ID:' foranstillet, skal du fjerne matchet fra de gyldige matches.

Hvis du f.eks. vil udelade forekomster af telefonnumre, der har **et telefonnummer** , og **ringe til mig i** strenge før telefonnummeret, skal du på en liste som denne:

- Telefonnummer 091-8974-653278
- Telefon 45-124576532-123
- 45-124576532-123

Du kan bruge følgende XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_prefix">
</Filter>
  <Keyword id="Keyword_false_positives_prefix">
    <Group matchStyle="string">
      <Term>phone number</Term>
      <Term>call me at</Term>
    </Group>
  </Keyword>
```

Hvis du f.eks. vil medtage forekomster, der har **kreditkort-** og **kortnummerstrenge** før kreditkortnummeret, på en liste som denne:

- Kreditkort 45-124576532-123 
- 45-124576532-123 (som kan være telefonnummer)

Du kan bruge følgende XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_prefix">
</Filter>

  <Keyword id="Keyword_true_positives_prefix">
    <Group matchStyle="string">
      <Term>credit card</Term>
      <Term>card #</Term>
    </Group>
  </Keyword
```

### <a name="textmatchfilter-suffix"></a>Suffiks til TextMatchFilter

Beskrivelse: Giver dig mulighed for at definere følgende tegn, der altid skal medtages eller udelades. Hvis kreditkortnummeret f.eks. efterfølges af '/xuid', skal du fjerne matchet fra de gyldige matches.

De vigtigste ekskluderingsforekomster, hvis der f.eks. er fem forekomster af fire cifre som suffiks på en liste som denne:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

Du kan bruge følgende XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Hvis du f.eks. vil udelade forekomster, hvis de efterfølges af **/xuidsuffix**, som en på denne liste:

- 1234-5678-9321 /xuid
- 1234-5678-9321

Du kan bruge denne XML

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_suffix">
</Filter>

  <Keyword id="Keyword_false_positives_suffix">
    <Group matchStyle="string">
      <Term>/xuid</Term>
    </Group>
  </Keyword>
```

Hvis du f.eks. kun vil medtage en forekomst, hvis den **efterfølges** af **cvv** eller udløber, f.eks. to på denne liste:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123 udløber 23/03

Du kan bruge denne XML

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_suffix">
</Filter>

  <Keyword id="Keyword_true_positives_suffix">
    <Group matchStyle="string">
      <Term>cvv</Term>
      <Term>expires</Term>
    </Group>
  </Keyword>
```

## <a name="using-filters-in-rule-packages"></a>Brug af filtre i regelpakker

Filtre kan defineres på hele SIT eller på et mønster. Her er nogle eksempler på kodestykker. 

### <a name="at-sensitive-information-type-level"></a>På niveau med følsomme oplysninger

Filtre på enhed – dækker alle underordnede mønstre

Filtrene anvendes på **alle** de instanser, der er klassificeret af et af mønstrene i den pågældende enhed/følsomme type

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>På det individuelle mønster for niveauet for følsomme oplysninger

Filtrerer kun på mønsterniveau.

Filteret anvendes på de forekomster, der matches af mønsteret.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>På niveau med følsomme oplysninger og et ekstra filter på nogle af mønstrene for den pågældende enhed

Filtre ved Enhed + mønster

Filtrene anvendes på **alle** de instanser, der er klassificeret af et af mønstrene i den pågældende enhed/følsomme type. Filteret på mønsterniveau filtrerer de forekomster, der matches af mønsteret.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)

- [Funktioner for type af følsomme oplysninger](sit-functions.md)
