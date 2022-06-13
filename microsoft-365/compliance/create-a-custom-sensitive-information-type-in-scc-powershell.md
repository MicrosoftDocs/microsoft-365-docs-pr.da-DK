---
title: Opret en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du opretter og importerer en brugerdefineret type følsomme oplysninger for politikker i Overholdelsescenter.
ms.openlocfilehash: 8678b7c218844d9963bd610b66e8b6c2c2647dea
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014514"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>Opret en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I denne artikel kan du se, hvordan du opretter en *XML-regelpakkefil* , der definerer brugerdefinerede [følsomme oplysningstyper](sensitive-information-type-entity-definitions.md). I denne artikel beskrives en brugerdefineret type følsomme oplysninger, der identificerer et medarbejder-id. Du kan bruge XML-eksempelfilen i denne artikel som udgangspunkt for din egen XML-fil.

Du kan finde flere oplysninger om typer af følsomme oplysninger under [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md).

Når du har oprettet en korrekt udformet XML-fil, kan du uploade den til Microsoft 365 ved hjælp af PowerShell. Derefter er du klar til at bruge din brugerdefinerede type følsomme oplysninger i politikker. Du kan teste dens effektivitet ved at registrere de følsomme oplysninger, som du havde tiltænkt.

> [!NOTE]
> Hvis du ikke har brug for det detaljerede kontrolelement, som PowerShell indeholder, kan du oprette brugerdefinerede følsomme oplysningstyper på Microsoft Purview-overholdelsesportalen. Du kan få flere oplysninger under [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>Vigtig ansvarsfraskrivelse

Microsoft Support kan ikke hjælpe dig med at oprette definitioner, der stemmer overens med indholdet.

Hvis du vil matche brugerdefineret udvikling, test og fejlfinding af indhold, skal du bruge dine egne interne it-ressourcer eller bruge konsulenttjenester, f.eks. Microsoft Consulting Services (MCS). Microsofts supportteknikere kan yde begrænset support til denne funktion, men de kan ikke garantere, at brugerdefinerede forslag, der matcher indhold, fuldt ud opfylder dine behov.

MCS kan levere regulære udtryk til testformål. De kan også hjælpe med fejlfinding af et eksisterende RegEx-mønster, der ikke fungerer som forventet med et enkelt specifikt indholdseksempel.

Se [Potentielle valideringsproblemer, du skal være opmærksom på](#potential-validation-issues-to-be-aware-of) i denne artikel.

Du kan få flere oplysninger om Boost.RegEx-programmet (tidligere kaldet RegEx++), der bruges til at behandle teksten, under [Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> Hvis du bruger et &-tegn (&) som en del af et nøgleord i din brugerdefinerede følsomme oplysningstype, skal du tilføje et ekstra ord med mellemrum omkring tegnet. Brug f.eks. `L & P` _ikke_ `L&P`.

## <a name="sample-xml-of-a-rule-package"></a>Eksempel på XML-kode i en regelpakke

Her er xml-eksemplet på den regelpakke, vi opretter i denne artikel. Elementer og attributter forklares i afsnittene nedenfor.

```xml
<?xml version="1.0" encoding="UTF-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
<RulePack id="DAD86A92-AB18-43BB-AB35-96F7C594ADAA">
  <Version build="0" major="1" minor="0" revision="0"/>
  <Publisher id="619DD8C3-7B80-4998-A312-4DF0402BAC04"/>
  <Details defaultLangCode="en-us">
    <LocalizedDetails langcode="en-us">
      <PublisherName>Contoso</PublisherName>
      <Name>Employee ID Custom Rule Pack</Name>
      <Description>
      This rule package contains the custom Employee ID entity.
      </Description>
    </LocalizedDetails>
  </Details>
</RulePack>
<Rules>
<!-- Employee ID -->
  <Entity id="E1CC861E-3FE9-4A58-82DF-4BD259EAB378" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="65">
      <IdMatch idRef="Regex_employee_id"/>
    </Pattern>
    <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
    </Pattern>
    <Pattern confidenceLevel="85">
      <IdMatch idRef="Regex_employee_id"/>
      <Match idRef="Func_us_date"/>
      <Any minMatches="1">
        <Match idRef="Keyword_badge" minCount="2"/>
        <Match idRef="Keyword_employee"/>
      </Any>
      <Any minMatches="0" maxMatches="0">
        <Match idRef="Keyword_false_positives_local"/>
        <Match idRef="Keyword_false_positives_intl"/>
      </Any>
    </Pattern>
  </Entity>
  <Regex id="Regex_employee_id">(\s)(\d{9})(\s)</Regex>
  <Keyword id="Keyword_employee">
    <Group matchStyle="word">
      <Term>Identification</Term>
      <Term>Contoso Employee</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_badge">
    <Group matchStyle="string">
      <Term>card</Term>
      <Term>badge</Term>
      <Term caseSensitive="true">ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_local">
    <Group matchStyle="word">
      <Term>credit card</Term>
      <Term>national ID</Term>
    </Group>
  </Keyword>
  <Keyword id="Keyword_false_positives_intl">
    <Group matchStyle="word">
      <Term>identity card</Term>
      <Term>national ID</Term>
      <Term>EU debit card</Term>
    </Group>
  </Keyword>
  <LocalizedStrings>
    <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB378">
      <Name default="true" langcode="en-us">Employee ID</Name>
      <Description default="true" langcode="en-us">
      A custom classification for detecting Employee IDs.
      </Description>
      <Description default="false" langcode="de-de">
      Description for German locale.
      </Description>
    </Resource>
  </LocalizedStrings>
</Rules>
</RulePackage>
```

## <a name="what-are-your-key-requirements-rule-entity-pattern-elements"></a>Hvad er dine vigtigste krav? [Regel, enhed, mønsterelementer]

Det er vigtigt, at du forstår den grundlæggende struktur i XML-skemaet for en regel. Din forståelse af strukturen hjælper din brugerdefinerede type følsomme oplysninger med at identificere det rigtige indhold.

En regel definerer et eller flere enheder (også kendt som følsomme oplysningstyper). Hvert objekt definerer et eller flere mønstre. Et mønster er det, en politik søger efter, når den evaluerer indhold (f.eks. mail og dokumenter).

I XML-markering betyder "regler" de mønstre, der definerer typen af følsomme oplysninger. Knyt ikke referencer til regler i denne artikel med "betingelser" eller "handlinger", der er almindelige i andre Microsoft-funktioner.

### <a name="simplest-scenario-entity-with-one-pattern"></a>Nemmeste scenarie: enhed med ét mønster

Her er et simpelt scenarie: Politikken skal identificere indhold, der indeholder nicifrede medarbejder-id'er, som bruges i din organisation. Et mønster refererer til det regulære udtryk i reglen, der identificerer nicifrede tal. Alt indhold, der indeholder et nicifret tal, opfylder mønsteret.

![Diagram over enhed med ét mønster.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

Men dette mønster kan identificere **alle** nicifrede tal, herunder længere tal eller andre typer nicifrede tal, der ikke er medarbejder-id'er. Denne type uønskede match er kendt som et *falsk positivt*.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>Mere almindeligt scenarie: enhed med flere mønstre

På grund af risikoen for falske positiver bruger du typisk mere end ét mønster til at definere en enhed. Flere mønstre giver understøttende beviser for målenheden. Yderligere nøgleord, datoer eller anden tekst kan f.eks. hjælpe med at identificere det oprindelige objekt (f.eks. det nicifrede medarbejdernummer).

Hvis du f.eks. vil øge sandsynligheden for at identificere indhold, der indeholder et medarbejder-id, kan du definere andre mønstre, der skal søges efter:

- Et mønster, der identificerer en ansættelsesdato.
- Et mønster, der identificerer både en ansættelsesdato og nøgleordet "medarbejder-id".

![Diagram over enhed med flere mønstre.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

Der er vigtige punkter, der skal overvejes i forbindelse med flere mønsterforekomster:

- Mønstre, der kræver flere beviser, har et højere konfidensniveau. Baseret på tillidsniveauet kan du foretage følgende handlinger:
  - Brug mere restriktive handlinger (f.eks. bloker indhold) med matches med større genkendelsessikkerhed.
  - Brug mindre restriktive handlinger (f.eks. sende meddelelser) med matches med lavere genkendelsessikkerhed.

- De understøttende `IdMatch` elementer og `Match` -elementer refererer til RegExes og nøgleord, der faktisk er underordnede til elementet `Rule` , ikke `Pattern`. Disse understøttende elementer refereres til af `Pattern`, men er inkluderet i `Rule`. Denne funktionsmåde betyder, at der kan refereres til en enkelt definition af et understøttende element, f.eks. et regulært udtryk eller en nøgleordsliste, af flere objekter og mønstre.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>Hvilket objekt skal du identificere? [Enhedselement, id-attribut]

En enhed er en følsom oplysningstype, f.eks. et kreditkortnummer, der har et veldefineret mønster. Hvert objekt har et entydigt GUID som id.

### <a name="name-the-entity-and-generate-its-guid"></a>Navngiv objektet, og generér dets GUID

1. Tilføj elementerne og `Entity` i `Rules` din foretrukne XML-editor.
2. Tilføj en kommentar, der indeholder navnet på dit brugerdefinerede objekt, f.eks. Medarbejder-id. Senere skal du føje objektnavnet til afsnittet oversatte strenge, og dette navn vises i Administration, når du opretter en politik.
3. Opret et entydigt GUID for objektet. I Windows PowerShell kan du f.eks. køre kommandoen `[guid]::NewGuid()`. Senere skal du også føje GUID'et til afsnittet oversatte strenge i objektet.

![XML-markering, der viser regler og enhedselementer.](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>Hvilket mønster vil du matche? [Mønsterelement, IdMatch-element, Regex-element]

Mønsteret indeholder en liste over, hvad typen af følsomme oplysninger søger efter. Mønsteret kan omfatte RegExes, nøgleord og indbyggede funktioner. Funktioner udfører opgaver som at køre RegExes for at finde datoer eller adresser. Følsomme informationstyper kan have flere mønstre med entydige konfidenser.

I følgende diagram refererer alle mønstre til det samme regulære udtryk. Denne RegEx søger efter et nicifret tal `(\d{9})` omgivet af blanktegn `(\s) ... (\s)`. Elementet refererer til dette regulære `IdMatch` udtryk, og det er det almindelige krav for alle mønstre, der søger efter enheden Medarbejder-id. `IdMatch` er det id, som mønsteret forsøger at matche. Et `Pattern` element skal have nøjagtigt ét `IdMatch` element.

![XML-markering, der viser flere mønsterelementer, der refererer til et enkelt Regex-element.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

Et opfyldt mønstermatch returnerer et antal- og konfidensniveau, som du kan bruge i betingelserne i din politik. Når du føjer en betingelse for registrering af en følsom oplysningstype til en politik, kan du redigere optællings- og tillidsniveauet som vist i følgende diagram. Konfidensniveau (også kaldet matchnøjagtighed) forklares senere i denne artikel.

![Indstillinger for antal forekomster og match af nøjagtighed.](../media/sit-confidence-level.png)

Regulære udtryk er effektive, så der er problemer, du skal kende til. En RegEx, der identificerer for meget indhold, kan f.eks. påvirke ydeevnen. Du kan få mere at vide om disse problemer i afsnittet [Potentielle valideringsproblemer, du skal være opmærksom på](#potential-validation-issues-to-be-aware-of) senere i denne artikel.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>Vil du kræve yderligere beviser? [Match element, attribut for minCount]

Ud over `IdMatch`kan et mønster bruge -elementet `Match` til at kræve yderligere dokumentation, f.eks. et nøgleord, RegEx, en dato eller en adresse.

En `Pattern` kan indeholde flere `Match` elementer:

- Direkte i elementet `Pattern` .
- Kombineret ved hjælp af -elementet `Any` .

`Match` -elementer joinforbindes af en implicit AND-operator. Det vil sige, at alle `Match` elementer skal være opfyldt, for at mønsteret kan matches.

Du kan bruge -elementet `Any` til at introducere OPERATORerne AND eller OR. Elementet `Any` beskrives senere i denne artikel.

Du kan bruge den valgfrie `minCount` attribut til at angive, hvor mange forekomster af et match der skal findes for hvert `Match` element. Du kan f.eks. angive, at et mønster kun opfyldes, når der findes mindst to nøgleord fra en nøgleordsliste.

![XML-markering, der viser matchelementet med attributten minOccurs.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>Nøgleord [nøgleord, gruppe- og ordelementer, matchStyle- og caseSensitive-attributter]

Som beskrevet tidligere kræver identificering af følsomme oplysninger ofte yderligere nøgleord som dokumentation. Ud over at matche et nicifret tal kan du f.eks. søge efter ord som "kort", "badge" eller "ID" ved hjælp af nøgleordselementet. Elementet `Keyword` har en `ID` attribut, der kan refereres til af flere `Match` elementer i flere mønstre eller objekter.

Nøgleord medtages som en liste over `Term` elementer i et `Group` element. Elementet `Group` har en `matchStyle` attribut med to mulige værdier:

- **matchStyle="word"**: Et ordmatch identificerer hele ord omgivet af blanktegn eller andre afgrænsere. Du skal altid bruge **ordet** , medmindre du har brug for at matche dele af ord eller ord på asiatiske sprog.

- **matchStyle="string"**: Et strengmatch identificerer strenge, uanset hvad de er omgivet af. "ID" matcher f.eks. "bud" og "idé". Bruges `string` kun, når du har brug for at matche asiatiske ord, eller hvis nøgleordet kan være inkluderet i andre strenge.

Endelig kan du bruge attributten `caseSensitive` for `Term` elementet til at angive, at indholdet skal matche nøgleordet nøjagtigt, herunder små bogstaver og store bogstaver.

![XML-markering, der viser Match elementer, der refererer til nøgleord.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>Regulære udtryk [Regex-element]

I dette eksempel bruger medarbejderenheden `ID` allerede elementet `IdMatch` til at referere til et regulært udtryk for mønsteret: et nicifret tal omgivet af mellemrum. Et mønster kan desuden bruge et `Match` element til at referere til et ekstra `Regex` element til at identificere bekræftende beviser, f.eks. et femcifret eller nicifret tal i formatet af et amerikansk postnummer.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>Yderligere mønstre, f.eks. datoer eller adresser [indbyggede funktioner]

Følsomme informationstyper kan også bruge indbyggede funktioner til at identificere bekræftende beviser. Det kan f.eks. være en amerikansk dato, EU-dato, udløbsdato eller amerikansk adresse. Microsoft 365 understøtter ikke upload af dine egne brugerdefinerede funktioner. Men når du opretter en brugerdefineret type følsomme oplysninger, kan din enhed referere til indbyggede funktioner.

Et badge for medarbejder-id har f.eks. en ansættelsesdato på sig, så dette brugerdefinerede objekt kan bruge den indbyggede `Func_us_date` funktion til at identificere en dato i det format, der ofte bruges i USA.

Du kan få flere oplysninger under [Funktioner til følsomme oplysninger.](sit-functions.md)

![XML-kode, der viser Match-element, der refererer til den indbyggede funktion.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>Forskellige kombinationer af beviser [attributterne Any element, minMatches og maxMatches]

I et `Pattern` element joinforbindes alle `IdMatch` elementer og `Match` af en implicit AND-operator. Med andre ord skal alle matches opfyldes, før mønsteret kan opfyldes.

Du kan oprette mere fleksibel matchende logik ved hjælp af elementet `Any` til at gruppere `Match` elementer. Du kan f.eks. bruge elementet `Any` til at matche alle, ingen eller et nøjagtigt undersæt af dets underordnede `Match` elementer.

Elementet `Any` har valgfrie `minMatches` og `maxMatches` attributter, som du kan bruge til at definere, hvor mange af de underordnede `Match` elementer der skal opfyldes, før mønsteret matches. Disse attributter definerer *antallet* af `Match` elementer og ikke antallet af fundne forekomster af beviser for matchene. Hvis du vil definere et minimumantal forekomster for et bestemt match, f.eks. to nøgleord fra en liste, skal du bruge attributten `minCount` for et `Match` element (se ovenfor).

### <a name="match-at-least-one-child-match-element"></a>Søg efter mindst ét underordnet matchelement

Hvis du kun vil have et minimumantal `Match` elementer, kan du bruge attributten `minMatches` . Disse elementer er faktisk `Match` joinforbundet af en implicit OR-operator. Dette `Any` element opfyldes, hvis der findes en amerikansk formateret dato eller et nøgleord fra en af listerne.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>Match et nøjagtigt undersæt af underordnede elementer Match elementer

Hvis du vil kræve et nøjagtigt antal `Match` elementer, skal du angive `minMatches` og `maxMatches` til den samme værdi. Dette `Any` element opfyldes kun, hvis der findes nøjagtigt én dato eller ét nøgleord. Hvis der er flere forekomster, matches mønsteret ikke.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>Forskel på ingen underordnede elementer

Hvis du vil kræve, at fraværet af specifikke beviser for et mønster opfyldes, kan du angive både minMatches og maxMatches til 0. Dette kan være nyttigt, hvis du har en nøgleordsliste eller andre beviser, der sandsynligvis angiver en falsk positiv.

Enheden for medarbejder-id søger f.eks. efter nøgleordet "kort", fordi det muligvis refererer til et "id-kort". Men hvis kortet kun vises i udtrykket "kreditkort", er det usandsynligt, at "kort" i dette indhold betyder "ID-kort". Så du kan tilføje "kreditkort" som et nøgleord til en liste over ord, som du vil udelukke fra at opfylde mønsteret.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>Match et antal entydige ord

Hvis du vil matche et antal entydige ord, skal du bruge parameteren *uniqueResults* , angivet til *sand*, som vist i følgende eksempel:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

I dette eksempel er der defineret et mønster for lønrevision ved hjælp af mindst tre entydige matches.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>Hvor tæt på enheden skal de andre beviser være? [patternsProximity-attribut]

Din type følsomme oplysninger leder efter et mønster, der repræsenterer et medarbejder-id, og som en del af dette mønster leder den også efter bekræftende beviser som f.eks. et nøgleord som f.eks. "ID". Det giver mening, at jo tættere dette bevis er, jo mere sandsynligt er mønsteret at være et faktisk medarbejder-id. Du kan bestemme, hvor tæt andre beviser i mønsteret skal være på enheden ved hjælp af attributten PatternsProximity for elementet Entity.

![XML-markering, der viser attributten patternsProximity.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

For hvert mønster i enheden definerer attributværdien patternsProximity afstanden (i Unicode-tegn) fra idMatch-placeringen for alle andre matches, der er angivet for det pågældende mønster. Nærhedsvinduet er forankret af idMatch-placeringen, hvor vinduet udvides til venstre og højre for IdMatch.

![Diagram over nærhedsvindue.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

I nedenstående eksempel illustreres det, hvordan nærhedsvinduet påvirker det mønstermatch, hvor IdMatch-elementet for det brugerdefinerede medarbejder-id kræver mindst ét bekræftende match af nøgleord eller dato. Det er kun ID1, der stemmer overens, fordi der for ID2 og ID3 findes enten ingen eller kun delvis bekræftende beviser i nærheden af vinduet.

![Diagram over bekræftende beviser og nærhedsvindue.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Bemærk, at for mails behandles meddelelsesteksten og hver vedhæftet fil som separate elementer. Det betyder, at nærhedsvinduet ikke strækker sig ud over slutningen af hvert af disse elementer. For hvert element (vedhæftet fil eller brødtekst) skal både idMatch og bekræftende beviser være placeret i det pågældende element.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>Hvad er de rigtige tillidsniveauer til forskellige mønstre? [confidenceLevel attribut, recommendedConfidence attribute]

Jo flere beviser, som et mønster kræver, jo større tillid har du til, at der er identificeret et faktisk objekt (f.eks. medarbejder-id), når mønsteret matches. Du har f.eks. større tillid til et mønster, der kræver et nicifret id-nummer, ansættelsesdato og nøgleord i nærheden, end du gør i et mønster, der kun kræver et nicifret id-nummer.

Mønsterelementet har en påkrævet confidenceLevel-attribut. Du kan tænke på værdien af confidenceLevel (et heltal mellem 1 og 100) som et entydigt id for hvert mønster i en enhed – mønstrene i et objekt skal have forskellige tillidsniveauer, som du tildeler. Den præcise værdi af heltalet betyder ikke noget – du skal blot vælge tal, der giver mening for dit overholdelsesteam. Når du har uploadet din brugerdefinerede type følsomme oplysninger og derefter oprettet en politik, kan du referere til disse tillidsniveauer i betingelserne for de regler, du opretter.

![XML-markering, der viser mønsterelementer med forskellige værdier for attributten confidenceLevel.](../media/sit-xml-markedup-2.png)

Ud over confidenceLevel for hvert mønster har enheden en anbefalet attribut for Tillid. Den anbefalede konfidensattribut kan opfattes som standardsikkerhedsniveauet for reglen. Når du opretter en regel i en politik, og du ikke angiver et konfidensniveau for den regel, der skal bruges, vil reglen stemme overens på baggrund af det anbefalede tillidsniveau for enheden. Bemærk, at attributten recommendedConfidence er obligatorisk for hvert enheds-id i regelpakken, hvis den mangler, kan du ikke gemme politikker, der bruger typen følsomme oplysninger.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>Vil du understøtte andre sprog i brugergrænsefladen i Overholdelsescenter? [Elementet LocalizedStrings]

Hvis dit overholdelsesteam bruger Microsoft Purview-overholdelsesportalen til at oprette politikker i forskellige landestandarder og på forskellige sprog, kan du angive lokaliserede versioner af navnet og beskrivelsen af din brugerdefinerede type følsomme oplysninger. Når dit overholdelsesteam bruger Microsoft 365 på et sprog, som du understøtter, får de vist det oversatte navn i brugergrænsefladen.

![Konfiguration af forekomstantal og matchnøjagtighed.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

Elementet Rules skal indeholde elementet LocalizedStrings, som indeholder et ressourceelement, der refererer til GUID'et for dit brugerdefinerede objekt. Hvert ressourceelement indeholder til gengæld et eller flere elementer af typen Name og Description, som hver især bruger langcode-attributten til at levere en lokaliseret streng til et bestemt sprog.

![XML-markering, der viser indholdet af elementet LocalizedStrings.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

Bemærk, at du kun bruger lokaliserede strenge til, hvordan din brugerdefinerede type følsomme oplysninger vises i brugergrænsefladen i Overholdelsescenter. Du kan ikke bruge oversatte strenge til at angive forskellige oversatte versioner af en nøgleordsliste eller et regulært udtryk.

## <a name="other-rule-package-markup-rulepack-guid"></a>Anden regelpakkemarkering [RulePack GUID]

Til sidst indeholder starten af hver RulePackage nogle generelle oplysninger, som du skal udfylde. Du kan bruge følgende markering som en skabelon og erstatte ". . ." pladsholdere med dine egne oplysninger.

Vigtigst er det, at du skal generere et GUID for RulePack. Ovenfor har du genereret et GUID for objektet. dette er endnu et GUID for RulePack. Der er flere måder at generere GUID'er på, men du kan nemt gøre det i PowerShell ved at skrive [guid]::NewGuid().

Elementet Version er også vigtigt. Første gang du uploader din regelpakke, noterer Microsoft 365 versionsnummeret. Hvis du senere opdaterer regelpakken og uploader en ny version, skal du sørge for at opdatere versionsnummeret, ellers installerer Microsoft 365 ikke regelpakken.

```xml
<?xml version="1.0" encoding="utf-16"?>
<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce">
  <RulePack id=". . .">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id=". . ." />
    <Details defaultLangCode=". . .">
      <LocalizedDetails langcode=" . . . ">
         <PublisherName>. . .</PublisherName>
         <Name>. . .</Name>
         <Description>. . .</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>

 <Rules>
  . . .
 </Rules>
</RulePackage>
```

Når du er færdig, bør dit RulePack-element se sådan ud.

![XML-markering, der viser RulePack-element.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>Validatorer

Microsoft 365 fremviser funktionsprocessorer for almindeligt anvendte SIT'er som validatorer. Her er en liste over dem.

### <a name="list-of-currently-available-validators"></a>Liste over validatorer, der er tilgængelige i øjeblikket

- `Func_credit_card`
- `Func_ssn`
- `Func_unformatted_ssn`
- `Func_randomized_formatted_ssn`
- `Func_randomized_unformatted_ssn`
- `Func_aba_routing`
- `Func_south_africa_identification_number`
- `Func_brazil_cpf`
- `Func_iban`
- `Func_brazil_cnpj`
- `Func_swedish_national_identifier`
- `Func_india_aadhaar`
- `Func_uk_nhs_number`
- `Func_Turkish_National_Id`
- `Func_australian_tax_file_number`
- `Func_usa_uk_passport`
- `Func_canadian_sin`
- `Func_formatted_itin`
- `Func_unformatted_itin`
- `Func_dea_number_v2`
- `Func_dea_number`
- `Func_japanese_my_number_personal`
- `Func_japanese_my_number_corporate`

Det giver dig mulighed for at definere din egen RegEx og validere dem. Hvis du vil bruge validatorer, skal du definere din egen RegEx og bruge egenskaben `Validator` til at tilføje den valgte funktionsbehandler. Når den er defineret, kan du bruge denne RegEx i et SIT.

I eksemplet nedenfor er der defineret et regulært udtryk – Regex_credit_card_AdditionalDelimiters for kreditkort, som derefter valideres ved hjælp af kontrolsumfunktionen for kreditkortet ved hjælp af Func_credit_card som validator.

```xml
<Regex id="Regex_credit_card_AdditionalDelimiters" validators="Func_credit_card"> (?:^|[\s,;\:\(\)\[\]"'])([0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4}[ -_][0-9]{4})(?:$|[\s,;\:\(\)\[\]"'])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_credit_card_AdditionalDelimiters" />
<Any minMatches="1">
<Match idRef="Keyword_cc_verification" />
<Match idRef="Keyword_cc_name" />
<Match idRef="Func_expiration_date" />
</Any>
</Pattern>
</Entity>
```

Microsoft 365 indeholder to generiske validatorer

### <a name="checksum-validator"></a>Kontrolsumsvalidator

I dette eksempel er der defineret en kontrolsumsvalidator for medarbejder-id'et for at validere RegEx for EmployeeID.

```xml
<Validators id="EmployeeIDChecksumValidator">
<Validator type="Checksum">
<Param name="Weights">2, 2, 2, 2, 2, 1</Param>
<Param name="Mod">28</Param>
<Param name="CheckDigit">2</Param> <!-- Check 2nd digit -->
<Param name="AllowAlphabets">1</Param> <!— 0 if no Alphabets -->
</Validator>
</Validators>
<Regex id="Regex_EmployeeID" validators="ChecksumValidator">(\d{5}[A-Z])</Regex>
<Entity id="675634eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
<Pattern confidenceLevel="85">
<IdMatch idRef="Regex_EmployeeID"/>
</Pattern>
</Entity>
```

### <a name="date-validator"></a>Datovalidator

I dette eksempel er der defineret en datovalidator for en RegEx-del, hvor er dato.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>Ændringer af Exchange Online

Tidligere har du måske brugt Exchange Online PowerShell til at importere dine brugerdefinerede følsomme oplysningstyper til DLP. Nu kan dine brugerdefinerede typer følsomme oplysninger bruges i både <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> og Overholdelsescenter. Som en del af denne forbedring skal du bruge Security & Compliance PowerShell til at importere dine brugerdefinerede følsomme oplysningstyper – du kan ikke længere importere dem fra Exchange Online PowerShell. Dine brugerdefinerede typer følsomme oplysninger fungerer fortsat på samme måde som før. Det kan dog tage op til én time, før ændringer af brugerdefinerede følsomme oplysningstyper i Overholdelsescenter vises i Exchange Administration.

Bemærk, at du i Overholdelsescenter bruger **[New-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** til at uploade en regelpakke. Tidligere brugte du cmdlet'en **ClassificationRuleCollection** i Exchange Administration.

## <a name="upload-your-rule-package"></a>Upload regelpakken

Benyt følgende fremgangsmåde for at uploade regelpakken:

1. Gem den som en .xml fil med Unicode-kodning.

2. [PowerShell Forbind til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/exchange-online-powershell)

3. Brug følgende syntaks:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   I dette eksempel overføres Unicode XML-filen med navnet MyNewRulePack.xml fra C:\Mine dokumenter.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   Du kan finde detaljerede oplysninger om syntaks og parametre under [New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > Det maksimale antal understøttede regelpakker er 10, men hver pakke kan indeholde definitionen af flere følsomme informationstyper.

4. Benyt en af følgende fremgangsmåder for at bekræfte, at du har oprettet en ny type følsomme oplysninger:

   - Kør [Get-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) for at kontrollere, at den nye regelpakke er angivet:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Kør [cmdlet'en Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at kontrollere, at typen af følsomme oplysninger er angivet:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     I forbindelse med brugerdefinerede følsomme oplysningstyper vil egenskabsværdien for Publisher være noget andet end Microsoft Corporation.

   - Erstat \<Name\> med værdien Name for den følsomme oplysningstype (f.eks. Medarbejder-id), og kør cmdlet'en [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) :

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>Potentielle valideringsproblemer, du skal være opmærksom på

Når du uploader xml-filen med regelpakken, validerer systemet XML-koden og kontrollerer, om der er kendte forkerte mønstre og åbenlyse problemer med ydeevnen. Her er nogle kendte problemer, som valideringen kontrollerer for – et regulært udtryk:

- Lookbehind-antagelser i det regulære udtryk bør kun have en fast længde. Antagelser med variabel længde resulterer i fejl.

  Vil f.eks `"(?<=^|\s|_)"` . ikke bestå valideringen. Det første mønster (`^`) er nul, mens de næste to mønstre (`\s` og `_`) har en længde på et. En alternativ måde at skrive dette regulære udtryk på er `"(?:^|(?<=\s|_))"`.

- Der kan ikke startes eller sluttes med en alternativator `|`, der svarer til alt, fordi den anses for at være et tomt match.

  Det kan f.eks. være valideringen `|a` , der `b|` ikke består.

- Kan ikke starte eller slutte med et `.{0,m}` mønster, der ikke har noget funktionelt formål og kun forringer ydeevnen.

  Det kan f.eks. være valideringen `.{0,50}ASDF` , der `ASDF.{0,50}` ikke består.

- Kan ikke have `.{0,m}` eller `.{1,m}` i grupper og kan ikke have `.\*` eller `.+` i grupper.

  Vil f.eks `(.{0,50000})` . ikke bestå valideringen.

- Der kan ikke være tegn med `{0,m}` eller `{1,m}` repeatere i grupper.

  Vil f.eks `(a\*)` . ikke bestå valideringen.

- Kan ikke starte eller slutte med `.{1,m}`. Brug i stedet `.`.

  Vil f.eks `.{1,m}asdf` . ikke bestå valideringen. `.asdf`Brug i stedet .

- Der kan ikke være en ubundet repeater (f.eks `*` . eller `+`) i en gruppe.

  Og består f.eks `(xx)\*` `(xx)+` . ikke valideringen.

- Nøgleord har højst 50 tegn i længden.  Hvis du har et nøgleord i en gruppe, der overskrider dette, er en foreslået løsning at oprette ordgruppen som en [nøgleordsordbog](./create-a-keyword-dictionary.md) og referere til GUID'et for nøgleordsordbogen i XML-strukturen som en del af Entity for Match eller idMatch i filen.

- Hver brugerdefineret type følsomme oplysninger kan maksimalt have 2048 nøgleord i alt.

- Den maksimale størrelse af nøgleordsordbøger i en enkelt lejer er 480 KB komprimeret for at overholde AD-skemagrænserne. Referer til den samme ordbog så mange gange, det er nødvendigt, når du opretter brugerdefinerede følsomme oplysningstyper. Start med at oprette brugerdefinerede nøgleordslister i den følsomme oplysningstype, og brug nøgleordsordbøger, hvis du har mere end 2048 nøgleord på en nøgleordsliste, eller hvis et nøgleord er længere end 50 tegn.

- Der kan maksimalt angives 50 nøgleordsordbøger, der er baseret på følsomme oplysningstyper, i en lejer.

- Sørg for, at hvert objektelement indeholder en anbefalet attribut forConfidence.

- Når du bruger PowerShell-cmdlet'en, er der en maksimal returstørrelse på de deserialiserede data på ca. 1 megabyte.   Dette påvirker størrelsen på DIN REGELPAKKE-XML-fil. Bevar den uploadede fil med en maksimumgrænse på 770 KB som en foreslået grænse for ensartede resultater uden fejl under behandling.

- XML-strukturen kræver ikke formateringstegn, f.eks. mellemrum, faner eller vognretur/linjeskift.  Vær opmærksom på dette, når du optimerer for plads på uploads. Værktøjer som f.eks. Microsoft Visual Code indeholder joinlinjefunktioner til at komprimere XML-filen.

Hvis en brugerdefineret type følsomme oplysninger indeholder et problem, der kan påvirke ydeevnen, overføres den ikke, og du får muligvis vist en af disse fejlmeddelelser:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>Gensøg dit indhold for at identificere de følsomme oplysninger

Microsoft 365 bruger søgecrawleren til at identificere og klassificere følsomme oplysninger i webstedets indhold. Indhold på SharePoint Online- og OneDrive for Business-websteder gensøges automatisk, når det opdateres. Men hvis du vil identificere din nye brugerdefinerede type følsomme oplysninger i alt eksisterende indhold, skal dette indhold søges igen.

I Microsoft 365 kan du ikke manuelt anmode om en nycrawl af en hel organisation, men du kan manuelt anmode om en ny forespørgsel for en gruppe af websteder, en liste eller et bibliotek. Du kan få flere oplysninger under [Anmod manuelt om gennemsøgning og omformatering af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

## <a name="reference-rule-package-xml-schema-definition"></a>Reference: XML-skemadefinition for regelpakke

Du kan kopiere denne markering, gemme den som en XSD-fil og bruge den til at validere XML-filen til regelpakken.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:mce="http://schemas.microsoft.com/office/2011/mce"
           targetNamespace="http://schemas.microsoft.com/office/2011/mce"
           xmlns:xs="https://www.w3.org/2001/XMLSchema"
           elementFormDefault="qualified"
           attributeFormDefault="unqualified"
           id="RulePackageSchema">
  <!-- Use include if this schema has the same target namespace as the schema being referenced, otherwise use import -->
  <xs:element name="RulePackage" type="mce:RulePackageType"/>
  <xs:simpleType name="LangType">
    <xs:union memberTypes="xs:language">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value=""/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="GuidType" final="#all">
    <xs:restriction base="xs:token">
      <xs:pattern value="[0-9a-fA-F]{8}\-([0-9a-fA-F]{4}\-){3}[0-9a-fA-F]{12}"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulePackageType">
    <xs:sequence>
      <xs:element name="RulePack" type="mce:RulePackType"/>
      <xs:element name="Rules" type="mce:RulesType">
        <xs:key name="UniqueRuleId">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueProcessorId">
          <xs:selector xpath="mce:Regex|mce:Keyword|mce:Fingerprint"></xs:selector>
          <xs:field xpath="@id"/>
        </xs:key>
        <xs:key name="UniqueResourceIdRef">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:key>
        <xs:keyref name="ReferencedRuleMustExist" refer="mce:UniqueRuleId">
          <xs:selector xpath="mce:LocalizedStrings/mce:Resource"/>
          <xs:field xpath="@idRef"/>
        </xs:keyref>
        <xs:keyref name="RuleMustHaveResource" refer="mce:UniqueResourceIdRef">
          <xs:selector xpath="mce:Entity|mce:Affinity|mce:Version/mce:Entity|mce:Version/mce:Affinity"/>
          <xs:field xpath="@id"/>
        </xs:keyref>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="RulePackType">
    <xs:sequence>
      <xs:element name="Version" type="mce:VersionType"/>
      <xs:element name="Publisher" type="mce:PublisherType"/>
      <xs:element name="Details" type="mce:DetailsType">
        <xs:key name="UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="mce:LocalizedDetails"/>
          <xs:field xpath="@langcode"/>
        </xs:key>
        <xs:keyref name="DefaultLangCodeMustExist" refer="mce:UniqueLangCodeInLocalizedDetails">
          <xs:selector xpath="."/>
          <xs:field xpath="@defaultLangCode"/>
        </xs:keyref>
      </xs:element>
      <xs:element name="Encryption" type="mce:EncryptionType" minOccurs="0" maxOccurs="1"/>
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="VersionType">
    <xs:attribute name="major" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="minor" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="build" type="xs:unsignedShort" use="required"/>
    <xs:attribute name="revision" type="xs:unsignedShort" use="required"/>
  </xs:complexType>
  <xs:complexType name="PublisherType">
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="LocalizedDetailsType">
    <xs:sequence>
      <xs:element name="PublisherName" type="mce:NameType"/>
      <xs:element name="Name" type="mce:RulePackNameType"/>
      <xs:element name="Description" type="mce:OptionalNameType"/>
    </xs:sequence>
    <xs:attribute name="langcode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="DetailsType">
    <xs:sequence>
      <xs:element name="LocalizedDetails" type="mce:LocalizedDetailsType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="defaultLangCode" type="mce:LangType" use="required"/>
  </xs:complexType>
  <xs:complexType name="EncryptionType">
    <xs:sequence>
      <xs:element name="Key" type="xs:normalizedString"/>
      <xs:element name="IV" type="xs:normalizedString"/>
    </xs:sequence>
  </xs:complexType>
  <xs:simpleType name="RulePackNameType">
    <xs:restriction base="xs:token">
      <xs:minLength value="1"/>
      <xs:maxLength value="64"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="NameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="1"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="OptionalNameType">
    <xs:restriction base="xs:normalizedString">
      <xs:minLength value="0"/>
      <xs:maxLength value="256"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="RestrictedTermType">
    <xs:restriction base="xs:string">
      <xs:minLength value="1"/>
      <xs:maxLength value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="RulesType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Entity" type="mce:EntityType"/>
        <xs:element name="Affinity" type="mce:AffinityType"/>
        <xs:element name="Version" type="mce:VersionedRuleType"/>
      </xs:choice>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Regex" type="mce:RegexType"/>
        <xs:element name="Keyword" type="mce:KeywordType"/>
        <xs:element name="Fingerprint" type="mce:FingerprintType"/>
        <xs:element name="ExtendedKeyword" type="mce:ExtendedKeywordType"/>
      </xs:choice>
      <xs:element name="LocalizedStrings" type="mce:LocalizedStringsType"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="EntityType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedPatternType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="patternsProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="recommendedConfidence" type="mce:ProbabilityType"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="PatternType">
    <xs:sequence>
      <xs:element name="IdMatch" type="mce:IdMatchType"/>
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="AffinityType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
      <xs:element name="Version" type="mce:VersionedEvidenceType" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="id" type="mce:GuidType" use="required"/>
    <xs:attribute name="evidencesProximity" type="mce:ProximityType" use="required"/>
    <xs:attribute name="thresholdConfidenceLevel" type="mce:ProbabilityType" use="required"/>
    <xs:attribute name="workload" type="mce:WorkloadType"/>
  </xs:complexType>
  <xs:complexType name="EvidenceType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="confidenceLevel" type="mce:ProbabilityType" use="required"/>
  </xs:complexType>
  <xs:complexType name="IdMatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
  </xs:complexType>
  <xs:complexType name="MatchType">
    <xs:attribute name="idRef" type="xs:string" use="required"/>
    <xs:attribute name="minCount" type="xs:positiveInteger" use="optional"/>
    <xs:attribute name="uniqueResults" type="xs:boolean" use="optional"/>
  </xs:complexType>
  <xs:complexType name="AnyType">
    <xs:sequence>
      <xs:choice maxOccurs="unbounded">
        <xs:element name="Match" type="mce:MatchType"/>
        <xs:element name="Any" type="mce:AnyType"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="minMatches" type="xs:nonNegativeInteger" default="1"/>
    <xs:attribute name="maxMatches" type="xs:nonNegativeInteger" use="optional"/>
  </xs:complexType>
  <xs:simpleType name="ProximityType">
    <xs:union>
      <xs:simpleType>
        <xs:restriction base='xs:string'>
          <xs:enumeration value="unlimited"/>
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType>
        <xs:restriction base="xs:positiveInteger">
          <xs:minInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:union>
  </xs:simpleType>
  <xs:simpleType name="ProbabilityType">
    <xs:restriction base="xs:integer">
      <xs:minInclusive value="1"/>
      <xs:maxInclusive value="100"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="WorkloadType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Exchange"/>
      <xs:enumeration value="Outlook"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:simpleType name="EngineVersionType">
    <xs:restriction base="xs:token">
      <xs:pattern value="^\d{2}\.01?\.\d{3,4}\.\d{1,3}$"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="VersionedRuleType">
    <xs:choice maxOccurs="unbounded">
      <xs:element name="Entity" type="mce:EntityType"/>
      <xs:element name="Affinity" type="mce:AffinityType"/>
    </xs:choice>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedPatternType">
    <xs:sequence>
      <xs:element name="Pattern" type="mce:PatternType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:complexType name="VersionedEvidenceType">
    <xs:sequence>
      <xs:element name="Evidence" type="mce:EvidenceType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="minEngineVersion" type="mce:EngineVersionType" use="required" />
  </xs:complexType>
  <xs:simpleType name="FingerprintValueType">
    <xs:restriction base="xs:string">
      <xs:minLength value="2732"/>
      <xs:maxLength value="2732"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:complexType name="FingerprintType">
    <xs:simpleContent>
      <xs:extension base="mce:FingerprintValueType">
        <xs:attribute name="id" type="xs:token" use="required"/>
        <xs:attribute name="threshold" type="mce:ProbabilityType" use="required"/>
        <xs:attribute name="shingleCount" type="xs:positiveInteger" use="required"/>
        <xs:attribute name="description" type="xs:string" use="optional"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="RegexType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="KeywordType">
    <xs:sequence>
      <xs:element name="Group" type="mce:GroupType" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="id" type="xs:token" use="required"/>
  </xs:complexType>
  <xs:complexType name="GroupType">
    <xs:sequence>
      <xs:choice>
        <xs:element name="Term" type="mce:TermType" maxOccurs="unbounded"/>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="matchStyle" default="word">
      <xs:simpleType>
        <xs:restriction base="xs:NMTOKEN">
          <xs:enumeration value="word"/>
          <xs:enumeration value="string"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
  <xs:complexType name="TermType">
    <xs:simpleContent>
      <xs:extension base="mce:RestrictedTermType">
        <xs:attribute name="caseSensitive" type="xs:boolean" default="false"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="ExtendedKeywordType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="id" type="xs:token" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="LocalizedStringsType">
    <xs:sequence>
      <xs:element name="Resource" type="mce:ResourceType" maxOccurs="unbounded">
      <xs:key name="UniqueLangCodeUsedInNamePerResource">
        <xs:selector xpath="mce:Name"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
      <xs:key name="UniqueLangCodeUsedInDescriptionPerResource">
        <xs:selector xpath="mce:Description"/>
        <xs:field xpath="@langcode"/>
      </xs:key>
    </xs:element>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ResourceType">
    <xs:sequence>
      <xs:element name="Name" type="mce:ResourceNameType" maxOccurs="unbounded"/>
      <xs:element name="Description" type="mce:DescriptionType" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
    <xs:attribute name="idRef" type="mce:GuidType" use="required"/>
  </xs:complexType>
  <xs:complexType name="ResourceNameType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
  <xs:complexType name="DescriptionType">
    <xs:simpleContent>
      <xs:extension base="xs:string">
        <xs:attribute name="default" type="xs:boolean" default="false"/>
        <xs:attribute name="langcode" type="mce:LangType" use="required"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>
</xs:schema>
```

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om Forebyggelse af datatab i Microsoft Purview](dlp-learn-about-dlp.md)
- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Funktioner for type af følsomme oplysninger](sit-functions.md)
