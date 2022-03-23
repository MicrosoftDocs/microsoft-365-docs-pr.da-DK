---
title: Få mere at vide om typer af følsomme oplysninger
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
description: Denne artikel giver et overblik over typer af følsomme oplysninger, og hvordan de registrerer følsomme oplysninger som f.eks. CPR-numre, kreditkortnumre eller bankkontonumre for at identificere følsomme elementer
ms.openlocfilehash: fbe23bbb6c639857367cc0b8467f6084e9116af1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592575"
---
# <a name="learn-about-sensitive-information-types"></a>Få mere at vide om typer af følsomme oplysninger

At identificere og klassificere følsomme elementer, der er under din organizations kontrol, er det første trin i [informationsbeskyttelsesdisciplinen](./information-protection.md).  Microsoft 365 indeholder tre metoder til at identificere elementer, så de kan klassificeres:

- manuelt af brugere
- automatiseret mønstergenkendelse, f.eks. følsomme oplysningstyper
- [maskinlæring](classifier-learn-about.md)

Følsomme oplysningstyper (SIT) er mønsterbaserede klassificeringer. De registrerer følsomme oplysninger som f.eks. CPR-numre, kreditkortnumre eller bankkontonumre [for at](sensitive-information-type-entity-definitions.md) identificere følsomme elementer. Se enhedsdefinitioner for følsomme oplysningstyper for at få en komplet liste over alle SIT'er.

Microsoft leverer et stort antal forudkonfigurerede SIT'er, eller du kan oprette dine egne.

## <a name="sensitive-information-types-are-used-in"></a>Typer af følsomme oplysninger bruges i

- [Politikker til forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Opbevaringsnavne](retention.md)
- [Insider-risikostyring](insider-risk-management.md)
- [Kommunikationsoverholdelse](communication-compliance.md)
- [Politikker for automatisk ydring](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Prkon](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Kategorier af typer af følsomme oplysninger

### <a name="built-in-sensitive-information-types"></a>Indbygget følsomme oplysningstyper

Disse SIT'er er oprettet af Microsoft og vises som standard i overholdelseskonsollen. Disse SIT'er kan ikke redigeres, men de kan bruges som skabeloner og kopieres til at oprette brugerdefinerede typer af følsomme oplysninger. Se [Enhedsdefinitioner af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md) for en komplet oversigt over alle SIT'er.

### <a name="named-entity-sensitive-information-types"></a>Navngivet typer af følsomme oplysninger for en enhed

Navngivne ENHEDS-SIT'er vises også som standard i overholdelseskonsollen. De registrerer personnavne, fysiske adresser og medicinske vilkår og tilstande. De kan ikke redigeres eller kopieres. Se Få [mere at vide om navngivne enheder (forhåndsvisning)](named-entities-learn.md#learn-about-named-entities-preview) for at få flere oplysninger. Navngivne enheds-SIT'er findes i to typer:

**ikke-bundtet**

Disse navngivne enheds-SIT'er har et smallere fokus, f.eks. et enkelt land eller en enkelt klasse af ord. Brug dem, når du har brug for en DLP-politik med et smallere registreringsområde. Se [Eksempler på navngivne enheds-SIT'er](named-entities-learn.md#examples-of-named-entity-sits).

**bundtet**

Bundtede navngivne enheds-SIT'er registrerer alle mulige matches i en klasse, f.eks. Alle fysiske adresser. Brug dem som generelle kriterier i dine DLP-politikker til at registrere følsomme elementer. Se [Eksempler på navngivne enheds-SIT'er](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Brugerdefinerede typer af følsomme oplysninger

Hvis de forudkonfigurerede typer af følsomme oplysninger ikke opfylder dine behov, kan du oprette dine egne brugerdefinerede typer af følsomme oplysninger, som du definerer fuldt ud, eller du kan kopiere en af de indbyggede og redigere den. Se Opret [en brugerdefineret type af følsomme oplysninger i Overholdelsescenter for at](create-a-custom-sensitive-information-type.md) få flere oplysninger.

### <a name="exact-data-match-sensitive-information-types"></a>Nøjagtige data matcher følsomme oplysningstyper

Alle EDM-baserede SIT'er oprettes fra bunden. Du bruger dem til at registrere elementer, der har nøjagtige værdier, som du definerer i en database med følsomme oplysninger. Se Få mere [at vide om nøjagtige datamatchingbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) for at få flere oplysninger.

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Grundlæggende dele af en følsom oplysningstype

Alle enheder af typen følsomme oplysninger er defineret af disse felter:

- navn: sådan henvises der til typen af følsomme oplysninger
- beskrivelse: beskriver, hvad typen af følsomme oplysninger leder efter
- mønster: Et mønster definerer, hvad en følsom oplysningstype registrerer. Den består af følgende komponenter.
    - Primært element – det vigtigste element, som typen af følsomme oplysninger er på udkig efter. Det kan være et **regulært udtryk** med eller uden kontrolsumvalidering, en liste **med nøgleord,** **en ordbog til nøgleord** eller en **funktion**.
    - Understøttende element – Elementer, der fungerer som støttedokument, der hjælper med at øge fortroligheden af matchet. Nøgleordet "SSN" er f.eks. tæt på et SSN-tal. Det kan være et regulært udtryk med eller uden kontrolsumvalidering, nøgleordsliste eller nøgleordsordbog.
    - Tillidsniveau – Tillidsniveauer (høj, mellem, lav) afspejler, hvor meget understøttende beviser der blev fundet sammen med det primære element. Jo mere støttedokumentdokument, et element indeholder, jo højere er tillid til, at et tilsvarende element indeholder de følsomme oplysninger, du leder efter.
    - Afstand – Antallet af tegn mellem primært og understøttende element.

![Diagram over bekræftende beviser og afstandsvindue.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Få mere at vide om tillidsniveauer i denne korte video.


 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]  



### <a name="example-sensitive-information-type"></a>Eksempel på typen af følsomme oplysninger


#### <a name="argentina-national-identity-dni-number"></a>Argentina national identity (DNI) number

### <a name="format"></a>Formatér

Otte cifre adskilt af punktummer

### <a name="pattern"></a>Mønster

Otte cifre:
- to cifre
- et punktum
- Tre cifre
- et punktum
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_argentina_national_id, der svarer til mønsteret.
- Der er fundet Keyword_argentina_national_id nøgleord.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentina National Identity-nummer 
- Identitet 
- Identifikation af nationalt identitetskort 
- DNI 
- NIC National Registry of Persons 
- Documento Nacional de Identidad 
- Registro Nacional de las Personas 
- Identidad 
- Identificación 

### <a name="more-on-confidence-levels"></a>Mere om tillidsniveauer

I en enhed med følsomme oplysningerstype afspejler **tillidsniveauet** , hvor meget understøttende dokumentation der findes ud over det primære element. Jo mere støttedokumentdokument, et element indeholder, jo højere er tillid til, at et tilsvarende element indeholder de følsomme oplysninger, du leder efter. Matches med et høj tillidsniveau vil f.eks. indeholde flere understøttende beviser tæt på det primære element, hvorimod match med et lav tillidsniveau ville indeholde meget lidt eller ingen understøttende beviser tæt på. 

Et højt tillidsniveau returnerer færrest falske positive, men kan resultere i flere falske negativer. Et lavt eller mellemlangt tillidsniveau returnerer flere falske positive, men fra få til nul falske negativer.

- **lav tillid**: Matchede elementer indeholder færrest falske negative, men de mest falske positive. Lav tillid returnerer alle forekomster af lav, mellem og høj tillid. Det lave tillidsniveau har en værdi på 65.
- **medium confidence**: Matchede elementer indeholder en gennemsnitlig mængde falske positive og falske negativer. Mellem tillid returnerer alle mellem og høj tillids match. Medietillidsniveauet har en værdi på 75.
- **høj tillid**: Matchede elementer indeholder færrest falske positive, men de mest falske negative. Høj tillid returnerer kun resultater med høj tillid og har en værdi på 85.  

Du skal bruge mønstre med høj tillidsniveau med lave optællinger, f.eks. fem til ti, og lav tillidsmønstre med højere antal, f.eks. 20 eller mere.

> [!NOTE]
> Hvis du har eksisterende politikker eller brugerdefinerede typer af følsomme oplysninger, der er defineret ved hjælp af talbaserede tillidsniveauer (også kendt som nøjagtighed), vil de automatisk blive knyttet til de tre diskrete tillidsniveauer. lav tillid, medium tillid og høj tillid på tværs af brugergrænsefladen i Security @ Compliance Center.
> - Alle politikker med minimumsnøjagtighed eller brugerdefinerede SIT-mønstre med et tillidsniveau på mellem 76 og 100 knyttes til høj tillid. 
> - Alle politikker med minimumsnøjagtighed eller brugerdefinerede SIT-mønstre med et tillidsniveau på mellem 66 og 75 knyttes til mellemlangt tillidsniveau.
> - Alle politikker med mindste nøjagtighed eller brugerdefinerede SIT-mønstre med tillidsniveauer, der er mindre end eller lig med 65, knyttes til lav tillid. 

## <a name="creating-custom-sensitive-information-types"></a>Oprette brugerdefinerede typer af følsomme oplysninger

Du kan vælge mellem flere muligheder for at oprette brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter.

- **Brug brugergrænsefladen** – Du kan konfigurere en brugerdefineret type af følsomme oplysninger ved hjælp af brugergrænsefladen i Overholdelsescenter. Med denne metode kan du bruge regulære udtryk, nøgleord og ordbøger til nøgleord. Du kan få mere at vide [under Opret en brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type.md).

- **Brug EDM** – Du kan konfigurere brugerdefinerede typer af følsomme oplysninger ved hjælp af nøjagtig EDM-baseret klassificering (Data Match). Denne metode gør det muligt at oprette en dynamisk følsom oplysningstype ved hjælp af en sikker database, som du kan opdatere med jævne mellemrum. Se [Få mere at vide om nøjagtige datamatchingbaserede følsomme oplysningstyper](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **Brug PowerShell** – Du kan konfigurere brugerdefinerede typer af følsomme oplysninger ved hjælp af PowerShell. Selvom denne metode er mere kompleks end at bruge brugergrænsefladen, har du flere konfigurationsindstillinger. Se [Opret en brugerdefineret type af følsomme oplysninger i Security & Compliance Center PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md).

> [!NOTE]
> Forbedrede tillidsniveauer er tilgængelige til øjeblikkelig brug i forebyggelse af datatab for Microsoft 365-tjenester, Microsoft Information Protection til Microsoft 365-tjenester, kommunikationsoverholdelse, informationsstyring og datastyring.
> Microsoft 365 Information Protection understøtter nu dobbelte byte tegnsætsprog til:
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
> 
> Denne support er tilgængelig for typer af følsomme oplysninger. Se Understøttelse af [beskyttelse af oplysninger for udgivelsesbemærkninger til dobbelte bytetegn](mip-dbcs-relnotes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du vil registrere mønstre, der indeholder kinesiske/japanske tegn og enkelte bytetegn eller til at registrere mønstre, der indeholder kinesisk/japansk og engelsk, skal du definere to varianter af nøgleordet eller regex.
> - Hvis du f.eks. vil registrere et nøgleord som "机密的dokument", skal du bruge to varianter af nøgleordet; et med et mellemrum mellem den japanske og engelske tekst og et andet uden mellemrum mellem den japanske og engelske tekst. Så de nøgleord, der skal tilføjes i SIT, bør være "机密的 dokument" og "机密的dokument". På samme måde skal der bruges to varianter til 東京オリ "東京オリンピック2020". "東京オリンピック 2020" og "東京オリンピック2020".
> 
> Sammen med kinesisk/japansk/dobbelt byte tegn, hvis listen over nøgleord/sætninger også indeholder ikke-kinesiske/japanske ord (som kun engelsk), skal du oprette to ordbøger/nøgleordslister. En til nøgleord, der indeholder kinesiske/japanske/dobbelte bytetegn og et andet til kun engelsk. 
> - Hvis du f.eks. vil oprette en ordbog/liste med nøgleord med tre udtryk "Meget fortroligt", "機密性が高い" og "机密的dokument", skal du oprette to lister med nøgleord. 
>     1. Meget fortrolig
>     2. 機密性が高い, 机密的dokument og 机密的 dokument
> 
> Mens du opretter en regex ved hjælp af en dobbelt byte bindestreg eller et dobbelt byte punktum, skal du sørge for at undgå begge tegn, som om den ene ville escape en bindestreg eller punktum i en regex. Her er en eksempelre regex til reference:
>    - (?<!\d) ([4][0-9]{3} [\-?\-\t]*[0-9]{4}
>
> Vi anbefaler, at du bruger strengmatch i stedet for ordmatch i en nøgleordsliste.

## <a name="for-further-information"></a>Du kan finde flere oplysninger
- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Oprette en brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type.md)
- [Opret en brugerdefineret type af følsomme oplysninger i PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Du kan få mere at vide om, hvordan du bruger følsomme oplysningstyper til at overholde bestemmelser om beskyttelse af data ved at se Udrul beskyttelse af data for bestemmelser om beskyttelse af personlige oplysninger [Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
