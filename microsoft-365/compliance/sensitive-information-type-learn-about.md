---
title: Få mere at vide om typer af følsomme oplysninger.
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Denne artikel indeholder en oversigt over typer af følsomme oplysninger, og hvordan de registrerer følsomme oplysninger som f.eks. social sikring, kreditkort eller bankkontonumre for at identificere følsomme elementer
ms.openlocfilehash: aef78c5ab3348b7a0b00a649f94fa5e50a99a397
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760311"
---
# <a name="learn-about-sensitive-information-types"></a>Få mere at vide om typer af følsomme oplysninger.

Identificering og klassificering af følsomme elementer, der er under din organisations kontrol, er det første skridt i [Information Protection disciplin](./information-protection.md).  Microsoft 365 giver tre måder at identificere elementer på, så de kan klassificeres:

- manuelt af brugere
- automatiseret mønstergenkendelse, f.eks. følsomme oplysningstyper
- [maskinel indlæring](classifier-learn-about.md)

FØLSOMME informationstyper (SIT) er mønsterbaserede klassificeringer. De registrerer følsomme oplysninger som f.eks. social sikring, kreditkort eller bankkontonumre for at identificere følsomme elementer. Se [Objektdefinitioner for følsomme informationstyper](sensitive-information-type-entity-definitions.md) for at få en komplet liste over alle SIT'er.

Microsoft leverer et stort antal forudkonfigurerede SIT'er, eller du kan oprette dine egne.

## <a name="sensitive-information-types-are-used-in"></a>Følsomme oplysningstyper bruges i

- [Politikker til forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Opbevaringsmærkater](retention.md)
- [Styring af insider-risiko](insider-risk-management.md)
- [Kommunikationsoverholdelse](communication-compliance.md)
- [Politikker for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Kategorier af følsomme informationstyper

### <a name="built-in-sensitive-information-types"></a>Indbyggede typer følsomme oplysninger

Disse SIT'er oprettes af Microsoft vises som standard i overholdelseskonsollen. Disse SIT'er kan ikke redigeres, men de kan bruges som skabeloner og kopieres til at oprette brugerdefinerede følsomme oplysningstyper. Se [Objektdefinitioner for følsomme oplysninger for](sensitive-information-type-entity-definitions.md) at få en komplet liste over alle SIT'er.

### <a name="named-entity-sensitive-information-types"></a>Navngivne objektfølsomme oplysningstyper

Navngivne objekt-SIT'er vises også som standard i overholdelseskonsollen. De registrerer personnavne, fysiske adresser og medicinske vilkår og betingelser. De kan ikke redigeres eller kopieres. Se [Få mere at vide om navngivne enheder (prøveversion)](named-entities-learn.md#learn-about-named-entities-preview) for at få flere oplysninger. Navngivne objekt-SIT'er findes i to typer:

**ikke-bundtet**

Disse navngivne objekt-SIT'er har et smallere fokus, f.eks. et enkelt land eller en enkelt klasse af ord. Brug dem, når du har brug for en DLP-politik med et smallere registreringsområde. Se [Eksempler på navngivne objekt-SIT'er](named-entities-learn.md#examples-of-named-entity-sits).

**Bundtet**

Bundtede navngivne enheds-SIT'er registrerer alle mulige match i en klasse, f.eks. Alle fysiske adresser. Brug dem som brede kriterier i dine DLP-politikker til registrering af følsomme elementer. Se [Eksempler på navngivne objekt-SIT'er](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Brugerdefinerede typer følsomme oplysninger

Hvis de forudkonfigurerede typer af følsomme oplysninger ikke opfylder dine behov, kan du oprette dine egne brugerdefinerede typer følsomme oplysninger, som du definerer fuldt ud, eller du kan kopiere en af de indbyggede typer og redigere den. Se [Opret en brugerdefineret type følsomme oplysninger i Overholdelsescenter for at](create-a-custom-sensitive-information-type.md) få flere oplysninger.

### <a name="exact-data-match-sensitive-information-types"></a>Nøjagtige data stemmer overens med følsomme oplysningstyper

Alle EDM-baserede SIT'er oprettes fra bunden. Du kan bruge dem til at registrere elementer, der har nøjagtige værdier, som du definerer i en database med følsomme oplysninger. Se Få [mere at vide om præcise datamatchbaserede følsomme oplysningstyper](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) for at få flere oplysninger.

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Grundlæggende dele af en type følsomme oplysninger

Alle objekter af typen følsomme oplysninger er defineret af disse felter:

- name: hvordan der refereres til typen af følsomme oplysninger
- description: Beskriver, hvad typen af følsomme oplysninger søger efter
- pattern: Et mønster definerer, hvad en følsom oplysningstype registrerer. Den består af følgende komponenter.
  - Primært element – det primære element, som den følsomme oplysningstype leder efter. Det kan være et **regulært udtryk** med eller uden en kontrolsumsvalidering, en **nøgleordsliste**, en **nøgleordsordbog** eller en **funktion**.
  - Understøttende element – elementer, der fungerer som understøttende beviser, der hjælper med at øge tilliden til kampen. Nøgleordet "SSN" i nærheden af et SSN-tal. Det kan være et regulært udtryk med eller uden kontrolsum, nøgleordsliste, nøgleordsordbog.
  - Konfidensniveau – Konfidensniveauer (høj, mellem, lav) afspejler, hvor mange understøttende beviser der blev registreret sammen med det primære element. Jo flere beviser et element indeholder, jo større er tilliden til, at et matchende element indeholder de følsomme oplysninger, du leder efter.
  - Proximity – antallet af tegn mellem det primære og det understøttende element.

![Diagram over bekræftende beviser og nærhedsvindue.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Få mere at vide om tillidsniveauer i denne korte video.

 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]

### <a name="example-sensitive-information-type"></a>Eksempel på type af følsomme oplysninger

#### <a name="argentina-national-identity-dni-number"></a>Argentinas nationale identitet (DNI) nummer

### <a name="format"></a>Format

Otte cifre adskilt af punktummer

### <a name="pattern"></a>Mønster

Otte cifre:

- to cifre
- et punktum
- tre cifre
- et punktum
- tre cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_argentina_national_id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_argentina_national_id.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentinas nationale identitetsnummer
- Identitet
- Nationalt id-kort til identifikation
- DNI
- NIC National Register of Persons
- Documento Nacional de Identidad
- Registro Nacional de las Personas
- Identidad
- Identificación

### <a name="more-on-confidence-levels"></a>Mere om tillidsniveauer

I en objektdefinition af en følsom informationstype afspejler **tillidsniveauet** , hvor meget understøttende beviser der registreres ud over det primære element. Jo flere beviser et element indeholder, jo større er tilliden til, at et matchende element indeholder de følsomme oplysninger, du leder efter. Matches med et højt konfidensniveau vil f.eks. indeholde flere understøttende beviser i nærheden af det primære element, mens matches med et lavt konfidensniveau ville indeholde meget lidt eller ingen understøttende beviser i nærheden.

Et højt konfidensniveau returnerer færrest falske positiver, men kan resultere i flere falske negativer. Lave eller mellemstore konfidensniveauer returnerer flere falske positiver, men få til nul falske negativer.

- **lav genkendelsessikkerhed**: Matchende elementer indeholder færrest falske negative, men de mest falske positiver. Lav genkendelsessikkerhed returnerer alle matches med lav, mellem og høj genkendelsessikkerhed. Det lave konfidensniveau har en værdi på 65.
- **medium konfidens**: Matchende elementer indeholder en gennemsnitlig mængde falske positive og falske negativer. Medium genkendelsessikkerhed returnerer alle forekomster af mellemstor og høj genkendelsessikkerhed. Det mellemste konfidensniveau har en værdi på 75.
- **høj genkendelsessikkerhed**: Matchende elementer indeholder færrest falske positiver, men de mest falske negativer. Høj genkendelsessikkerhed returnerer kun resultater med høj genkendelsessikkerhed og har en værdi på 85.

Du bør bruge mønstre med højt genkendelsesniveau med lave antal, f.eks. fem til ti og lave tillidsmønstre med højere antal, f.eks. 20 eller mere.

> [!NOTE]
> Hvis du har eksisterende politikker eller brugerdefinerede følsomme informationstyper (SIT'er), der er defineret ved hjælp af talbaserede tillidsniveauer (også kaldet nøjagtighed), knyttes de automatisk til de tre diskrete konfidensniveauer. lav tillid, mellem tillid og høj tillid på tværs af brugergrænsefladen i Security @ Compliance Center.
>
> - Alle politikker med minimal nøjagtighed eller brugerdefinerede SIT-mønstre med tillidsniveauer på mellem 76 og 100 knyttes til høj tillid.
> - Alle politikker med minimal nøjagtighed eller brugerdefinerede SIT-mønstre med tillidsniveauer på mellem 66 og 75 knyttes til medium tillid.
> - Alle politikker med minimumnøjagtighed eller brugerdefinerede SIT-mønstre med tillidsniveauer, der er mindre end eller lig med 65, knyttes til lav tillid.

## <a name="creating-custom-sensitive-information-types"></a>Oprettelse af brugerdefinerede typer følsomme oplysninger

Du kan vælge mellem flere muligheder for at oprette brugerdefinerede typer følsomme oplysninger i Overholdelsescenter.

- **Brug brugergrænsefladen** – Du kan konfigurere en brugerdefineret type følsomme oplysninger ved hjælp af brugergrænsefladen i Compliance Center. Med denne metode kan du bruge regulære udtryk, nøgleord og nøgleordsordbøger. Du kan få mere at vide under [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md).

- **Brug EDM** – Du kan konfigurere brugerdefinerede følsomme informationstyper ved hjælp af EDM-baseret klassificering (Exact Data Match). Med denne metode kan du oprette en dynamisk følsom oplysningstype ved hjælp af en sikker database, som du kan opdatere med jævne mellemrum. Se [Få mere at vide om præcise datamatchbaserede følsomme oplysningstyper](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **Brug PowerShell** – Du kan konfigurere brugerdefinerede typer følsomme oplysninger ved hjælp af PowerShell. Selvom denne metode er mere kompleks end at bruge brugergrænsefladen, har du flere konfigurationsindstillinger. Se [Opret en brugerdefineret type følsomme oplysninger i Security & Compliance Center PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md).

> [!NOTE]
> Forbedrede tillidsniveauer er tilgængelige til øjeblikkelig brug inden for forebyggelse af datatab for Microsoft 365 tjenester, Microsoft Information Protection til Microsoft 365 tjenester, kommunikation med overholdelse af angivne standarder, styring af oplysninger og datastyring.
> Microsoft 365 Information Protection understøtter nu sprog med dobbeltbytetegnsæt for:
>
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
> Denne understøttelse er tilgængelig for typer af følsomme oplysninger. Se [Produktbemærkninger til beskyttelse af oplysninger for dobbeltbytetegnsæt](mip-dbcs-relnotes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du vil registrere mønstre, der indeholder kinesiske/japanske tegn og enkeltbytetegn, eller for at registrere mønstre, der indeholder kinesisk/japansk og engelsk, skal du definere to varianter af nøgleordet eller regex.
>
> - Hvis du f.eks. vil registrere et nøgleord som "机密的dokument", skal du bruge to varianter af nøgleordet. en med et mellemrum mellem japansk og engelsk tekst og en anden uden et mellemrum mellem japansk og engelsk tekst. De nøgleord, der skal tilføjes i SIT, skal derfor være "机密的 document" og "机密的document". På samme måde bør der bruges to varianter for at registrere udtrykket "東京オリンピック2020". "東京オリンピック 2020" og "東京オリンピック2020".
>
> Sammen med kinesisk/japansk/dobbeltbytetegn skal du oprette to ordbøger/nøgleordslister, hvis listen over nøgleord/udtryk også indeholder ikke-kinesiske/japanske ord (f.eks. kun engelsk). Et til nøgleord, der indeholder kinesiske/japanske/dobbelte bytetegn, og et til kun engelsk.
>
> - Hvis du f.eks. vil oprette en nøgleordsordbog/liste med tre udtryk "Meget fortroligt", "機密性が高い" og "机密的dokument", skal du oprette to nøgleordslister.
>     1. Meget fortroligt
>     2. 機密性が高い, 机密的document og 机密的 dokument
>
> Mens du opretter en regex ved hjælp af en dobbelt byte bindestreg eller et dobbelt byte punktum, skal du sørge for at undslippe begge tegn, som man ville undslippe en bindestreg eller et punktum i en regex. Her er et eksempel på et regex som reference:
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Vi anbefaler, at du bruger strengmatch i stedet for ordmatch på en nøgleordsliste.

## <a name="for-further-information"></a>Yderligere oplysninger

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md)
- [Opret en brugerdefineret type følsomme oplysninger i PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Hvis du vil vide mere om, hvordan du bruger følsomme informationstyper til at overholde regler om beskyttelse af personlige oplysninger, skal du se [Udrul regler om beskyttelse af personlige oplysninger for Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
