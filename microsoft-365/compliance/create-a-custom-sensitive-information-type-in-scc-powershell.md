---
title: Opret en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell
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
description: Få mere at vide om, hvordan du opretter og importerer en brugerdefineret type af følsomme oplysninger for politikker i Overholdelsescenter.
ms.openlocfilehash: 89c215ca52b255a6e3aed72ff032cdd2475c0d87
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63589512"
---
# <a name="create-a-custom-sensitive-information-type-using-powershell"></a>Opret en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell

I denne artikel kan du se, hvordan du opretter en *XML-regelpakkefil* , der definerer [brugerdefinerede typer af følsomme oplysninger](sensitive-information-type-entity-definitions.md). I denne artikel beskrives en brugerdefineret type af følsomme oplysninger, der identificerer et medarbejder-id. Du kan bruge XML-eksempel i denne artikel som et udgangspunkt for din egen XML-fil.

Du kan finde flere oplysninger om typer af følsomme oplysninger [under Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md).

Når du har oprettet en korrekt udformet XML-fil, kan du uploade den til en Microsoft 365 hjælp af PowerShell. Derefter er du klar til at bruge din brugerdefinerede type af følsomme oplysninger i politikker. Du kan teste dets effektivitet ved registrering af følsomme oplysninger efter hensigten.

> [!NOTE]
> Hvis du ikke har brug for det detaljerede kontrolelement, som PowerShell leverer, kan du oprette brugerdefinerede typer af følsomme oplysninger Microsoft 365 Overholdelsescenter. Få mere at vide under [Opret en brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type.md).

## <a name="important-disclaimer"></a>Vigtig ansvarsfraskrivelse

Microsoft Support kan ikke hjælpe dig med at oprette definitioner, der matcher indhold.

Til brugerdefineret udvikling af indholdsmatching, test og fejlfinding skal du bruge dine egne interne it-ressourcer eller bruge konsulenttjenester som f.eks. Microsoft Consulting Services (MCS). Microsoft-supportteknikere kan yde begrænset support til denne funktion, men de kan ikke garantere, at tilpassede forslag til indholdsmatchning fuldt ud opfylder dine behov.

MCS kan levere regulære udtryk til testformål. De kan også give hjælp til fejlfinding af et eksisterende RegEx-mønster, der ikke fungerer som forventet, med et enkelt specifikt indholdseksemem muligvis.

Se [Potentielle valideringsproblemer, du skal være opmærksom på](#potential-validation-issues-to-be-aware-of) i denne artikel.

Du kan finde flere oplysninger om programmet Boost.RegEx (tidligere kaldet RegEx++), der bruges til at behandle teksten, under [Boost.Regex 5.1.3](https://www.boost.org/doc/libs/1_68_0/libs/regex/doc/html/).

> [!NOTE]
> Hvis du bruger et og-tegn (&) som en del af et nøgleord i din brugerdefinerede type af følsomme oplysninger, skal du tilføje et yderligere ord med mellemrum omkring tegnet. Brug f.eks `L & P` _. ikke_ `L&P`.

## <a name="sample-xml-of-a-rule-package"></a>XML-eksempel på en regelpakke

Her er XML-eksempel på regelpakken, som vi opretter i denne artikel. Elementer og attributter er forklaret i afsnittene herunder.

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

## <a name="what-are-your-key-requirements-rule-entity-pattern-elements"></a>Hvad er de vigtigste krav? [Regel,Enhed, Mønsterelementer]

Det er vigtigt, at du forstår den grundlæggende struktur i XML-skemaet for en regel. Din forståelse af strukturen hjælper din brugerdefinerede type af følsomme oplysninger med at identificere det rigtige indhold.

En regel definerer en eller flere enheder (også kaldet typer af følsomme oplysninger). Hver enhed definerer et eller flere mønstre. Et mønster er det, en politik søger efter, når den evaluerer indhold (f.eks. mails og dokumenter).

I XML-markeringer betyder "regler" de mønstre, der definerer den følsomme oplysningstype. Tilknyt ikke referencer til regler i denne artikel med "betingelser" eller "handlinger", der er almindelige i andre Microsoft-funktioner.

### <a name="simplest-scenario-entity-with-one-pattern"></a>Mest enkle scenarie: enhed med ét mønster

Her er et simpelt scenarie: Du vil have din politik til at identificere indhold, der indeholder nicifrede medarbejder-id'er, der bruges i organisationen. Et mønster refererer til det regulære udtryk i reglen, der identificerer nicifrede tal. Alt indhold, der indeholder et nicifret tal, opfylder mønsteret.

![Diagram over enhed med ét mønster.](../media/4cc82dcf-068f-43ff-99b2-bac3892e9819.png)

Men dette mønster kan identificere et  hvilket som helst nicifret tal, herunder længere tal eller andre typer af nicifrede tal, som ikke er medarbejder-id'er. Denne type uønsket match kaldes en *falsk positiv*.

### <a name="more-common-scenario-entity-with-multiple-patterns"></a>Mere almindeligt scenarie: enhed med flere mønstre

På grund af mulighederne for falske positive bruger du typisk mere end ét mønster til at definere en enhed. Flere mønstre giver støtte til beviser for destinationsenheden. Eksempelvis kan yderligere nøgleord, datoer eller anden tekst hjælpe med at identificere den oprindelige enhed (f.eks. det nicifrede medarbejdernummer).

Hvis du f.eks. vil øge sandsynligheden for at identificere indhold, der indeholder et medarbejder-id, kan du definere andre mønstre, der skal søges efter:

- Et mønster, der identificerer en ansættelsesdato.
- Et mønster, der identificerer både en ansættelsesdato og nøgleordet "medarbejder-id".

![Diagram over enhed med flere mønstre.](../media/c8dc2c9d-00c6-4ebc-889a-53b41a90024a.png)

Der er vigtige punkter, du skal overveje for flere mønster matches:

- Mønstre, der kræver flere beviser, har et højere tillidsniveau. Baseret på tillidsniveauet kan du udføre følgende handlinger:
  - Brug mere restriktive handlinger (f.eks. blokere indhold) med resultater med større tillid.
  - Brug mindre restriktive handlinger (f.eks. send meddelelser) med mindre tillidshandlinger.

- De supplerende `IdMatch` elementer `Match` henviser til RegExes og nøgleord, der faktisk er børn af `Rule` elementet, ikke `Pattern`. Disse supplerende elementer refereres til af `Pattern`, men er inkluderet i `Rule`. Denne funktionsmåde betyder, at der kan refereres til en enkelt definition af et understøttende element, f.eks. et regulært udtryk eller en liste over nøgleord, af flere enheder og mønstre.

## <a name="what-entity-do-you-need-to-identify-entity-element-id-attribute"></a>Hvilken enhed skal du identificere? [Enhedselement, id-attribut]

En enhed er en følsom oplysningstype, f.eks. et kreditkortnummer, der har et tydeligt mønster. Hver enhed har et entydigt GUID som dets id.

### <a name="name-the-entity-and-generate-its-guid"></a>Navngive enheden og oprette dets GUID

1. Tilføj elementerne og i den valgte XML-editor `Rules` `Entity` .
2. Tilføj en kommentar, der indeholder navnet på din brugerdefinerede enhed, f.eks. Medarbejder-id. Senere skal du føje enhedsnavnet til sektionen oversatte strenge, og dette navn vises i Administration, når du opretter en politik.
3. Opret et entydigt GUID for enheden. Eksempelvis kan du i Windows PowerShell køre kommandoen `[guid]::NewGuid()`. Senere skal du også føje GUID'et til afsnittet med oversatte strenge i enheden.

![XML-markering, der viser regler og enhedselementer.](../media/c46c0209-0947-44e0-ac3a-8fd5209a81aa.png)

## <a name="what-pattern-do-you-want-to-match-pattern-element-idmatch-element-regex-element"></a>Hvilket mønster vil du matche? [Mønsterelement, IdMatch-element, Regex-element]

Mønsteret indeholder listen over, hvad den følsomme oplysningstype leder efter. Mønsteret kan indeholde RegExes, nøgleord og indbyggede funktioner. Funktioner gør opgaver på samme måde som at køre RegExes for at finde datoer eller adresser. Typer af følsomme oplysninger kan have flere mønstre med entydige tillidsmønstre.

I følgende diagram henviser alle mønstrene til det samme regulære udtryk. Denne RegEx søger efter et nicifret tal omgivet `(\d{9})` af mellemrum `(\s) ... (\s)`. Dette regulære udtryk refereres til af `IdMatch` elementet og er det almindelige krav for alle mønstre, der søger efter Medarbejder-id-enheden. `IdMatch` er den identifikator, som mønsteret skal forsøge at matche. Et `Pattern` element skal have præcis ét `IdMatch` element.

![XML-markering, der viser flere mønsterelementer, der refererer til enkelt Regex-element.](../media/8f3f497b-3b8b-4bad-9c6a-d9abf0520854.png)

Et tilfreds mønster match returnerer et antal og et tillidsniveau, som du kan bruge i betingelserne i din politik. Når du føjer en betingelse til registrering af en type af følsomme oplysninger til en politik, kan du redigere antallet og tillidsniveauet som vist i følgende diagram. Tillidsniveau (også kaldet matchnøjagtighed) forklares senere i denne artikel.

![Indstillinger for antal forekomster og matchnøjagtighed.](../media/sit-confidence-level.png)

Regulære udtryk er effektive, så der er problemer, du skal kende til. Eksempelvis kan en RegEx, der identificerer for meget indhold, påvirke ydeevnen. Du kan få mere at vide om disse problemer i [afsnittet Potentielle valideringsproblemer, du skal være opmærksom](#potential-validation-issues-to-be-aware-of) på senere i denne artikel.

## <a name="do-you-want-to-require-additional-evidence-match-element-mincount-attribute"></a>Vil du kræve yderligere beviser? [Match-element, minTæl-attribut]

Ud over , `IdMatch`kan et mønster `Match` bruge elementet til at kræve yderligere supplerende bevis, f.eks et nøgleord, RegEx, dato eller adresse.

A `Pattern` kan indeholde flere `Match` elementer:

- Direkte i `Pattern` elementet.
- Kombineret ved hjælp af `Any` elementet.

`Match` elementer sammenføjes af en implicit AND-operator. Med andre ord skal alle `Match` elementer være tilfredse, for at mønsteret kan matches.

Du kan bruge elementet til `Any` at introducere AND- eller OR-operatorer. Elementet `Any` beskrives senere i denne artikel.

Du kan bruge den valgfrie `minCount` attribut til at angive, hvor mange forekomster af et match der skal findes for hvert `Match` element. Du kan f.eks. angive, at et mønster kun er tilfreds, når der findes mindst to nøgleord fra en liste over nøgleord.

![XML-markering, der viser elementet Match med minOccurs-attributten.](../media/607f6b5e-2c7d-43a5-a131-a649f122e15a.png)

### <a name="keywords-keyword-group-and-term-elements-matchstyle-and-casesensitive-attributes"></a>Nøgleord [Nøgleord, Gruppe- og Ordelementer, matchStyle og attributter, hvor der er forskel på store og små bogstaver]

Som beskrevet tidligere kræver identificering af følsomme oplysninger ofte yderligere nøgleord som bekræftende beviser. Ud over at matche et nicifret tal kan du f.eks. se efter ord som "kort", "badge" eller "id" ved hjælp af nøgleordselementet. Elementet `Keyword` har en attribut `ID` , der kan refereres til af flere `Match` elementer i flere mønstre eller enheder.

Nøgleord er inkluderet som en liste over `Term` elementer i et `Group` element. Elementet `Group` har en `matchStyle` attribut med to mulige værdier:

- **matchStyle="word"**: Et ordmatch identificerer hele ord omgivet af blanktegn eller andre afgrænsere. Du bør altid bruge **Word,** medmindre du har brug for at matche dele af ord eller ord på asiatiske sprog.

- **matchStyle="string"**: Et strengmatch identificerer strenge, uanset hvad de er omgivet af. "Id" matcher f.eks. "bud" og "idé". Brug `string` kun, når du har brug for at matche asiatiske ord, eller hvis dit nøgleord muligvis er inkluderet i andre strenge.

Endelig kan du bruge attributten `caseSensitive` `Term` for elementet til at angive, at indholdet skal svare nøjagtigt til nøgleordet, herunder små og store bogstaver.

![XML-markering, der viser Match elementer, der refererer til nøgleord.](../media/e729ba27-dec6-46f4-9242-584c6c12fd85.png)

### <a name="regular-expressions-regex-element"></a>Regulære udtryk [Regex-element]

I dette eksempel bruger medarbejderenheden `ID` `IdMatch` allerede elementet til at referere til et regulært udtryk for mønsteret: et nicifret tal omgivet af mellemrum. `Match` Desuden kan et mønster bruge et element til at referere til et ekstra element `Regex` til at identificere bekræftende beviser, f.eks. et femcifret eller nicifret tal i formatet et amerikansk postnummer.

### <a name="additional-patterns-such-as-dates-or-addresses-built-in-functions"></a>Flere mønstre, f.eks. datoer eller adresser [indbyggede funktioner]

Følsomme oplysningstyper kan også bruge indbyggede funktioner til at identificere bekræftende beviser. Eksempelvis en dato i USA, EN EU-dato, udløbsdato eller en amerikansk adresse. Microsoft 365 understøtter ikke upload af dine egne brugerdefinerede funktioner. Men når du opretter en brugerdefineret type af følsomme oplysninger, kan enheden referere til indbyggede funktioner.

Eksempelvis har en medarbejder-id-badge en ansættelsesdato på sig, så denne brugerdefinerede enhed kan bruge den indbyggede `Func_us_date` funktion til at identificere en dato i det format, der ofte bruges i USA.

Du kan få mere at vide [under Funktioner af typen Følsomme oplysninger](sit-functions.md).

![XML-markering, der viser den indbyggede funktion Match element referencing.](../media/dac6eae3-9c52-4537-b984-f9f127cc9c33.png)

## <a name="different-combinations-of-evidence-any-element-minmatches-and-maxmatches-attributes"></a>Forskellige kombinationer af beviser [Ethvert element, minMatches og maxMatches attributter]

I et `Pattern` element er alle elementer `IdMatch` forbundet `Match` med en implicit AND-operator. Med andre ord skal alle match være opfyldt, før mønsteret kan være tilfreds.

Du kan oprette en mere fleksibel matchende logik ved at bruge elementet `Any` til at gruppere `Match` elementer. Du kan f.eks. bruge elementet `Any` til at matche alle, ingen eller et nøjagtigt undersæt af dets underordnede `Match` elementer.

Elementet `Any` har valgfrie attributter `minMatches` og `maxMatches` attributter, `Match` du kan bruge til at definere, hvor mange af de underordnede elementer, der skal være opfyldt, før mønsteret matches. Disse attributter definerer *antallet* af `Match` elementer, ikke antallet af forekomster af bevis, der blev fundet for matchene. Hvis du vil definere et minimum antal forekomster for et bestemt match, f.eks. to nøgleord på en liste, `minCount` skal du bruge attributten for `Match` et element (se ovenfor).

### <a name="match-at-least-one-child-match-element"></a>Match mindst ét underordnet Match-element

Hvis du kun vil kræve et minimum antal `Match` elementer, kan du bruge attributten `minMatches` . Disse elementer er faktisk forbundet `Match` af en implicit OR-operator. Dette `Any` element er tilfreds, hvis der findes en dato, der er formateret i USA, eller et nøgleord fra en af listerne.

```xml
<Any minMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-an-exact-subset-of-any-children-match-elements"></a>Match et nøjagtigt undersæt af underordnede Match-elementer

Hvis du vil kræve et nøjagtigt antal `Match` elementer, skal du `minMatches` angive `maxMatches` og til den samme værdi. Dette `Any` element er kun tilfreds, hvis der findes præcis én dato eller ét nøgleord. Hvis der er flere forekomster, er mønsteret ikke matchet.

```xml
<Any minMatches="1" maxMatches="1" >
     <Match idRef="Func_us_date" />
     <Match idRef="Keyword_employee" />
     <Match idRef="Keyword_badge" />
</Any>
```

### <a name="match-none-of-children-match-elements"></a>Match ingen af børn Match-elementer

Hvis du vil kræve, at der ikke er bestemte beviser for, at et mønster er tilfreds, kan du angive både minMatches og maxMatches til 0. Dette kan være nyttigt, hvis du har en nøgleordsliste eller andre beviser, der sandsynligvis indikerer en falsk positiv.

Eksempelvis søger medarbejder-id'et efter nøgleordet "kort", fordi det kan referere til et "id-kort". Men hvis kortet kun vises i sætningen "kreditkort", betyder "kort" i dette indhold sandsynligvis "Id-kort". Så du kan tilføje "kreditkort" som et nøgleord til en liste over ord, som du vil udelukke fra at opfylde mønsteret.

```xml
<Any minMatches="0" maxMatches="0" >
    <Match idRef="Keyword_false_positives_local" />
    <Match idRef="Keyword_false_positives_intl" />
</Any>
```

### <a name="match-a-number-of-unique-terms"></a>Match et antal entydige ord

Hvis du vil matche et antal entydige ord, skal du bruge det *entydigeResults-parameter* , der er indstillet til *sand*, som vist i følgende eksempel:

```xml
<Pattern confidenceLevel="75">
    <IdMatch idRef="Salary_Revision_terms" />
    <Match idRef=" Salary_Revision_ID " minCount="3" uniqueResults="true" />
</Pattern>
```

I dette eksempel er der defineret et mønster for lønrevision ved brug af mindst tre entydige match.

## <a name="how-close-to-the-entity-must-the-other-evidence-be-patternsproximity-attribute"></a>Hvor tæt på enheden skal de andre beviser være? [patternsProximity-attribut]

Typen af følsomme oplysninger leder efter et mønster, der repræsenterer et medarbejder-id, og som en del af det mønster leder den også efter bekræftende beviser som f.eks. "ID". Det giver mening, at jo nærmere sammen dette bevis er, jo mere sandsynligt er det, at mønsteret er et faktisk medarbejder-id. Du kan afgøre, hvor tæt andre beviser i mønsteret skal være på enheden ved hjælp af de nødvendige patternsProximity-attribut for Enhedselementet.

![XML-kode, der viser mønstreProximity-attributten.](../media/e97eb7dc-b897-4e11-9325-91c742d9839b.png)

For hvert mønster i enheden definerer patternsProximity-attributværdien afstanden (i Unicode-tegn) fra IdMatch-placeringen for alle andre matches, der er angivet for det pågældende mønster. Afstandsvinduet er forankret af IdMatch-placeringen, hvor vinduet går ud til venstre og højre for IdMatch.

![Diagram over afstandsvindue.](../media/b593dfd1-5eef-4d79-8726-a28923f7c31e.png)

Eksemplet nedenfor viser, hvordan afstandsvinduet påvirker matchet, hvor IdMatch-elementet for det brugerdefinerede medarbejder-id kræver mindst ét bekræftende match for nøgleord eller dato. Kun ID1 stemmer overens, fordi der for ID2 og ID3 findes enten ingen eller kun delvis bekræftende beviser inden for nærheden af vinduet.

![Diagram over bekræftende beviser og afstandsvindue.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Bemærk, at for mails behandles brødteksten og hver vedhæftet fil som separate elementer. Det betyder, at afstandsvinduet ikke går ud over slutningen af hvert af disse elementer. For hvert element (vedhæftet fil eller brødtekst) skal både idMatch og bekræftende bevis findes i det pågældende element.

## <a name="what-are-the-right-confidence-levels-for-different-patterns-confidencelevel-attribute-recommendedconfidence-attribute"></a>Hvad er de rigtige tillidsniveauer for forskellige mønstre? [attributten confidenceLevel, anbefalede attributten Konfidence]

Jo mere bevis, et mønster kræver, jo mere tillid har du til, at en faktisk enhed (f.eks. medarbejder-id) er blevet identificeret, når mønsteret er matchet. Du har f.eks. større tillid til et mønster, der kræver et nicifret id-nummer, ansættelsesdato og et nøgleord i nærheden, end du gør i et mønster, der kun kræver et nicifret id.

Mønsterelementet har en påkrævet confidenceLevel-attribut. Du kan tænke på værdien af tillidSniveau (et heltal mellem 1 og 100) som et entydigt id for hvert mønster i en enhed – mønstrene i en enhed skal have forskellige tillidsniveauer, som du tildeler. Heltals nøjagtige værdi er ligegyldig – du skal blot vælge tal, som giver mening for dit team til overholdelse af regler og standarder. Når du overfører din brugerdefinerede type af følsomme oplysninger og derefter opretter en politik, kan du referere til disse tillidsniveauer i betingelserne i de regler, du opretter.

![XML-markering, der viser mønsterelementer med forskellige værdier for attributten confidenceLevel.](../media/sit-xml-markedup-2.png)

Ud over confidenceLevel for hvert mønster har enheden en anbefaletKonfidence-attribut. Den anbefalede tillidsattribut kan bruges som standardtillidsniveauet for reglen. Når du opretter en regel i en politik, og du ikke angiver et tillidsniveau, som reglen skal bruge, matcher denne regel baseret på det anbefalede tillidsniveau for enheden. Bemærk, at den anbefalede Attribut for konfidence er obligatorisk for hvert Enheds-id i regelpakken, hvis den mangler, kan du ikke gemme politikker, der bruger typen Af følsomme oplysninger.

## <a name="do-you-want-to-support-other-languages-in-the-ui-of-the-compliance-center-localizedstrings-element"></a>Vil du understøtte andre sprog i brugergrænsefladen i Overholdelsescenter? [LocalizedStrings-element]

Hvis dit overholdelsesteam bruger Microsoft 365 Compliance Center til at oprette politikker på forskellige lande/områder og på forskellige sprog, kan du angive oversatte versioner af navnet og beskrivelsen af din brugerdefinerede type af følsomme oplysninger. Når dit overholdelsesteam bruger Microsoft 365 på et sprog, du understøtter, får de vist det oversatte navn i brugergrænsefladen.

![Konfiguration af antal forekomster og matchnøjagtighed.](../media/11d0b51e-7c3f-4cc6-96d8-b29bcdae1aeb.png)

Elementet Regler skal indeholde et LocalizedStrings-element, som indeholder et Ressource-element, der refererer til GUID'et for det brugerdefinerede objekt. Hvert Ressourceelement indeholder desuden ét eller flere Navne- og Beskrivelse-elementer, som hver bruger attributten langcode til at levere en oversatte streng til et bestemt sprog.

![XML-markering, der viser indholdet af elementet LocalizedStrings.](../media/a96fc34a-b93d-498f-8b92-285b16a7bbe6.png)

Bemærk, at du kun bruger oversatte strenge til den måde, som din brugerdefinerede type af følsomme oplysninger vises på i Brugergrænsefladen i Overholdelsescenter. Du kan ikke bruge oversatte strenge til at levere forskellige oversatte versioner af en nøgleordsliste eller et regulært udtryk.

## <a name="other-rule-package-markup-rulepack-guid"></a>Anden kode til regelpakke [RulePack GUID]

Til sidst indeholder begyndelsen af hver RulePackage nogle generelle oplysninger, som du skal udfylde. Du kan bruge følgende markering som en skabelon og erstatte ". . ." pladsholdere med dine egne oplysninger.

Det vigtigste er, at du skal generere et GUID til RulePack. Ovenfor genererede du et GUID for enheden. dette er et andet GUID for RulePack. Der er flere måder at oprette GUID'er på, men du kan nemt gøre det i PowerShell ved at skrive [guid]::NewGuid().

Elementet Version er også vigtigt. Når du overfører regelpakken for første gang, noterer Microsoft 365 versionsnummeret. Hvis du senere opdaterer regelpakken og uploader en ny version, skal du sørge for at opdatere versionsnummeret eller Microsoft 365 ikke installere regelpakken.

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

![XML-markering, der viser elementet RulePack.](../media/fd0f31a7-c3ee-43cd-a71b-6a3813b21155.png)

## <a name="validators"></a>Validatorer

Microsoft 365 viser funktionsprocessorer for ofte anvendte SIT'er som validatorer. Her er en liste over dem.

### <a name="list-of-currently-available-validators"></a>Liste over aktuelt tilgængelige validatorer

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

Dette giver dig mulighed for at definere dine egne RegEx og validere dem. Hvis du vil bruge validatorer, skal du definere din egen RegEx og `Validator` bruge egenskaben til at tilføje funktionsprocessoren efter eget valg. Når den er defineret, kan du bruge denne RegEx i et SIT.

I eksemplet nedenfor er der defineret et regulært udtryk Regex_credit_card_AdditionalDelimiters kreditkort, som derefter valideres ved hjælp af kontrolsumfunktionen for kreditkort ved hjælp af Func_credit_card som validator.

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

### <a name="checksum-validator"></a>Kontrolsums validator

I dette eksempel er der defineret en kontrolsumvalidering for medarbejder-id for at validere RegEx for EmployeeID.

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

### <a name="date-validator"></a>Dato validator

I dette eksempel defineres en dato validator for en RegEx-del, som er dato.

```xml
<Validators id="date_validator_1"> <Validator type="DateSimple"> <Param name="Pattern">DDMMYYYY</Param> <!—supported patterns DDMMYYYY, MMDDYYYY, YYYYDDMM, YYYYMMDD, DDMMYYYY, DDMMYY, MMDDYY, YYDDMM, YYMMDD --> </Validator> </Validators>
<Regex id="date_regex_1" validators="date_validator_1">\d{8}</Regex>
```

## <a name="changes-for-exchange-online"></a>Ændringer for Exchange Online

Tidligere kunne du have brugt Exchange Online PowerShell til at importere dine brugerdefinerede typer af følsomme oplysninger til DLP. Nu kan dine brugerdefinerede typer af følsomme oplysninger bruges <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">både i Exchange Administration</a> og Overholdelsescenter. Som en del af denne forbedring skal du bruge Compliance Center PowerShell til at importere dine brugerdefinerede typer af følsomme oplysninger – du kan ikke importere dem fra Exchange PowerShell længere. Dine brugerdefinerede typer af følsomme oplysninger fortsætter med at fungere som før; det kan dog tage op til en time, før ændringer af brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter vises i Exchange Administration.

Bemærk, at du i Overholdelsescenter bruger **[New-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage)** til at overføre en regelpakke. (Tidligere brugte du Exchange **ClassificationRuleCollection**' cmdlet i Administration).

## <a name="upload-your-rule-package"></a>Upload din regelpakke

Hvis du vil overføre din regelpakke, skal du gøre følgende:

1. Gem den som en .xml med Unicode-kodning.

2. [Forbind til Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell)

3. Brug følgende syntaks:

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('PathToUnicodeXMLFile'))
   ```

   I dette eksempel overføres Unicode XML-filen med navnet MyNewRulePack.xml fra C:\Dokumenter.

   ```powershell
   New-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\MyNewRulePack.xml'))
   ```

   Du kan finde detaljerede oplysninger om syntaks og parameter [i New-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/new-dlpsensitiveinformationtyperulepackage).

   > [!NOTE]
   > Det maksimale antal regelpakker, der understøttes, er 10, men hver pakke kan indeholde definitionen af flere typer af følsomme oplysninger.

4. Hvis du vil bekræfte, at du har oprettet en ny type af følsomme oplysninger, skal du gøre et af følgende:

   - Kør [cmdlet'en Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) for at bekræfte, at den nye regelpakke er angivet:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Kør [cmdlet'en Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at bekræfte, at typen af følsomme oplysninger er angivet:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     For brugerdefinerede typer af følsomme oplysninger vil Publisher være noget andet end Microsoft Corporation.

   - Erstat \<Name\> med værdien Navn på typen af følsomme oplysninger (eksempel: Medarbejder-id), og kør [cmdlet'en Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) :

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="potential-validation-issues-to-be-aware-of"></a>Potentielle valideringsproblemer at være opmærksom på

Når du overfører XML-filen med regelpakken, validerer systemet XML-koden og kontrollerer for kendte dårlige mønstre og indlysende problemer med ydeevnen. Her er nogle kendte problemer, som valideringen kontrollerer for – et regulært udtryk:

- Lookbehind assertions in the regular expression should be of fixed length only. Variable længde assertions will result in errors.

  Bestået f.eks `"(?<=^|\s|_)"` . ikke validering. Det første mønster (`^`) er nullængde, mens de næste to mønstre (`\s` og `_`) har en længde på én. Du kan også skrive dette regulære udtryk på `"(?:^|(?<=\s|_))"`.

- Kan ikke starte eller slutte med skiftende , `|`som matcher alt, fordi det betragtes som et tomt match.

  Det kan f.eks`b|`. være, `|a` at valideringen ikke bliver bestået eller ej.

- Kan ikke starte eller slutte med et `.{0,m}` mønster, som ikke har nogen funktionsformål og kun påvirker ydeevnen.

  Det kan f.eks`ASDF.{0,50}`. være, `.{0,50}ASDF` at valideringen ikke bliver bestået eller ej.

- Kan ikke have `.{0,m}` eller `.{1,m}` i grupper og kan ikke have `.\*` eller `.+` i grupper.

  Bestået f.eks `(.{0,50000})` . ikke validering.

- Må ikke have nogen tegn med `{0,m}` eller `{1,m}` repeatere i grupper.

  Bestået f.eks `(a\*)` . ikke validering.

- Kan ikke starte eller slutte med `.{1,m}`; i stedet skal du bruge `.`.

  Bestået f.eks `.{1,m}asdf` . ikke validering. I stedet skal du bruge `.asdf`.

- Der kan ikke være en ubundet gentagelse (f.eks. `*` `+`eller ) i en gruppe.

  Det kan f.eks. `(xx)+` være, `(xx)\*` og valideringen kan ikke foretages.

- Nøgleord kan maksimalt have 50 tegn.  Hvis du har et nøgleord i en gruppe, der overskrider dette, er en foreslået løsning at oprette gruppen af ord [](./create-a-keyword-dictionary.md) som en nøgleordsordbog og henvise til GUID'en for nøgleordsordbogen i XML-strukturen som en del af enheden for match eller idMatch i filen.

- Hver brugerdefineret type af følsomme oplysninger kan maksimalt have 2048 nøgleord.

- Den maksimale størrelse af nøgleordsordbøger i en enkelt lejer er 480 KB komprimeret for at overholde AD-skemagrænserne. Du kan henvise til den samme ordbog lige så mange gange, som det er nødvendigt, når du opretter brugerdefinerede typer af følsomme oplysninger. Start med at oprette lister med brugerdefinerede nøgleord i typen af følsomme oplysninger, og brug ordbøger til nøgleord, hvis du har mere end 2.048 nøgleord på en liste med nøgleord, eller hvis et nøgleord er større end 50 tegn.

- Der kan maksimalt være tilladt 50 ordbøger baseret på følsomme oplysningstyper i en lejer.

- Sørg for, at hvert Enhed-element indeholder en anbefaletConfidence-attribut.

- Når du bruger PowerShell-cmdletten, er der en maksimal returstørrelse på de data, der er deserialiserede, på ca. 1 megabyte.   Dette påvirker størrelsen på XML-filen med regelpakken. Sørg for, at den uploadede fil er begrænset til en maksimumgrænse på 770 kilobyte som en foreslået grænse for ensartede resultater uden fejl under behandlingen.

- XML-strukturen kræver ikke formateringstegn, f.eks. mellemrum, faner eller vognretur/linjefeed-indtastninger.  Vær opmærksom på dette, når du optimerer for plads på overførsler. Værktøjer som f.eks. Microsoft Visual Code giver joinlinjefunktioner til komprimering af XML-filen.

Hvis en brugerdefineret type af følsomme oplysninger indeholder et problem, der kan påvirke ydeevnen, uploades den ikke, og du får muligvis vist en af disse fejlmeddelelser:

- `Generic quantifiers which match more content than expected (e.g., '+', '*')`

- `Lookaround assertions`

- `Complex grouping in conjunction with general quantifiers`

## <a name="recrawl-your-content-to-identify-the-sensitive-information"></a>Omdæl dit indhold for at identificere følsomme oplysninger

Microsoft 365 bruger søge crawleren til at identificere og klassificere følsomme oplysninger i webstedsindhold. Indhold i SharePoint Online og OneDrive for Business automatisk sammen, når det opdateres. Men hvis du vil identificere din nye brugerdefinerede type af følsomme oplysninger i alt eksisterende indhold, skal indholdet på ny ændres.

I Microsoft 365 kan du ikke manuelt anmode om, at en hel organisation ændres manuelt, men du kan manuelt anmode om, at en gruppe af websteder, en liste eller et bibliotek ændres. Få mere at vide under [Anmod manuelt om gennemsøgning og gensøgning af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

## <a name="reference-rule-package-xml-schema-definition"></a>Reference: XML-skemadefinition for regelpakke

Du kan kopiere denne markering, gemme den som en XSD-fil og bruge den til at validere XML-filen for regelpakken.

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

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Funktioner af typen Følsomme oplysninger](sit-functions.md)
