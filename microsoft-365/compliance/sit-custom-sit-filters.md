---
title: Reference til brugerdefinerede filtre af typen Følsomme oplysninger
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
description: I denne artikel vises en liste over de filtre, der kan kodes til brugerdefinerede typer af følsomme oplysninger.
ms.openlocfilehash: bcecc13776b20f8b4c61eaf499a99397931fe498
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63597994"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Reference til brugerdefinerede filtre af typen følsomme oplysninger

I Microsoft kan du definere filtre eller andre kontroller, mens du opretter en brugerdefineret type af følsomme oplysninger (SIT).

## <a name="list-of-supported-filters-and-use-cases"></a>Liste over understøttede filtre og use cases

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Beskrivelse: Gør det muligt at udelade matches, der har alle cifre som dublerede cifre, f.eks. 111111111 eller 111-111-111

Definere filtre
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

Brug af den i regelpakken på enhedsniveau
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

Brug af den i regelpakken på mønsterniveau
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

Beskrivelse: Gør det muligt at definere starttegnene for enheden. Den har to varianter, medtag og udelad.

Hvis du f.eks. vil udelade tallene fra 0500, 91, 091, 010 på en liste som denne:

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Du kan bruge følgende xml

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
Hvis du f.eks. vil medtage tallene fra 0500, 91, 091, 0100 på en liste som denne: 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

Du kan bruge følgende xml

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

Beskrivelse: Gør det muligt at definere sluttegnene for enheden. 

Hvis du f.eks. vil udelade tal, der slutter med 0500.91.091,0100, på en liste som denne:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Du kan bruge følgende xml

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

Hvis du f.eks. vil medtage de tal, der slutter med 0500, 91, 091, 0100, på en liste som denne:

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

Du kan bruge følgende xml

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Fuld

Beskrivelse: Gør det muligt at forbyde bestemte matches for at forhindre dem i at udløse reglen. Du kan f.eks 4111111111111111 du udelader oplysninger fra listen over gyldige kreditkorts matches.

Hvis du f.eks. vil udelade kreditkortnumre som 4111111111111111 og 3241891031113111 på en liste som denne:

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

Du kan bruge følgende xml

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

Du kan bruge følgende xml

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>TekstMatchFilterpræfiks

Beskrivelse: Gør det muligt at definere de foregående tegn, der altid skal medtages eller udelades. Hvis f.eks. kreditkortnummeret indledes med "Ordre-id:", skal du fjerne matchet fra de gyldige matches.

Hvis du f.eks. vil udelukke forekomster af telefonnumre, der har **et Telefon-nummer**, og ringe til mig i strenge før telefonnummeret på en liste som denne:

- Telefon tal 091-8974-653278
- Telefon 45-124576532-123
- 45-124576532-123

Du kan bruge følgende xml

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

Hvis du f.eks. **vil medtage forekomster**, der  har kreditkort- og kortnr. strenge før kreditkortnummeret, skal du på en liste, der ser sådan ud:

- Kreditkort 45-124576532-123 
- 45-124576532-123 (hvilket kan være telefonnummer)

Du kan bruge følgende xml

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

### <a name="textmatchfilter-suffix"></a>TextMatchFilter-suffiks

Beskrivelse: Gør det muligt at definere følgende tegn, der altid skal medtages eller udelades. Hvis f.eks. kreditkortnummer efterfølges af '/xuid', skal du fjerne matchet fra de gyldige matches.

F.eks. udelader de øverste forekomster, hvis der er yderligere fem forekomster af fire cifre som suffiks på en liste som denne:

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

Du kan bruge følgende xml

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Hvis du f.eks. vil udelade forekomster, hvis de **efterfølges af /xuidsuffiks**, f.eks. et på denne liste:

- 1234-5678-9321 /xuid
- 1234-5678-9321

Du kan bruge denne xml

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

Hvis du f.eks. kun vil medtage en forekomst, hvis den **efterfølges** af **CVV** eller udløber, f.eks. to på denne liste:

- 45-124576532-123 
- 45-124576532-123 cvv 966
- 45-124576532-123 udløber 23-03

Du kan bruge denne xml

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

### <a name="at-sensitive-information-type-level"></a>På niveauet for følsomme oplysninger

Filtre på enhed – vil dække alle underordnede mønstre

Filtrene anvendes på alle de **forekomster,** der er klassificeret af mønstrene i den pågældende enhed/følsomme type

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>På det individuelle mønster for niveauet for typen af følsomme oplysninger

Filtre kun på mønsterniveau.

Filteret anvendes på de forekomster, der matcher mønsteret.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>På niveauet for følsomme oplysninger og et ekstra filter på nogle af mønstrene i den pågældende enhed

Filtre på enhed + mønster

Filtrene anvendes på alle de **forekomster,** der er klassificeret af mønstrene i den pågældende enhed/følsomme type. Filteret på mønsterniveau filtrerer de forekomster, der passer til det pågældende mønster.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)

- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)

- [Funktioner af typen Følsomme oplysninger](sit-functions.md)
