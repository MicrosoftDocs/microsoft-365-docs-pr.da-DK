---
title: Enhedsdefinitioner for følsomme oplysningstyper
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Der findes mange typer af følsomme oplysninger, der er klar til brug i dine DLP-politikker. Denne artikel indeholder alle disse typer af følsomme oplysninger og viser, hvad en DLP-politik søger efter, når den registrerer hver type.
ms.openlocfilehash: a3d2592af6b7692b5a5e634947deb811412b5650
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63599866"
---
# <a name="sensitive-information-type-entity-definitions"></a>Enhedsdefinitioner for følsomme oplysningstyper

I denne artikel vises alle definitioner af følsomme oplysningstyper. Hver definition viser, hvad en DLP-politik søger efter for at registrere hver type. Du kan få mere at vide om typer af følsomme oplysninger [under Typer af følsomme oplysninger](sensitive-information-type-learn-about.md)

> [!NOTE]
> Tilknytning af tillidsniveau (høj/mellem/lav) med nøjagtighedsnummer (numerisk værdi fra 1 til 100)
> - Lav tillid: 65 eller mindre
> - Medium confidence: 75
> - Høj tillid: 85


## <a name="aba-routing-number"></a>ABA-registreringsnummer

### <a name="format"></a>Formatér

ni cifre, der kan være i et formateret eller uformateret mønster

### <a name="pattern"></a>Mønster

- To cifre i intervallerne 00-12, 21-32, 61-72 eller 80
- to cifre
- en valgfri bindestreg
- fire cifre
- en valgfri bindestreg
- et ciffer


### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En politik har mellem tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_aba_routing, der svarer til mønsteret.
- Der er fundet Keyword_ABA_Routing nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_aba_routing, der svarer til mønsteret.

```xml
    <!-- ABA Routing Number -->
    <Entity id="cb353f78-2b72-4c3c-8827-92ebe4f69fdf" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_aba_routing" />
        <Match idRef="Keyword_ABA_Routing" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_aba_routing" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- aba-tal
- aba #
- aba
- abarouting #
- abaroutingnumber
- americanbankassociationarouting #
- americanbankassociationroutingnumber
- bankudskrift #
- banknummerering
- routing #
- routingnr.
- routingnummer
- overførselsrutenummer
- routing #
- RTN


## <a name="all-full-names"></a>Alle fulde navne

Alle fulde navne er et bundt navngivet objekt. Den registrerer fulde navne på personer fra alle understøttede lande/områder, som omfatter Australien, Kina, Japan, USA og lande i EU. Brug denne SIT til at registrere alle mulige forekomster af fulde navne.

### <a name="format"></a>Formatér

Diverse.

### <a name="pattern"></a>Mønster

Diverse.

### <a name="checksum"></a>Kontrolsum

Nej.

### <a name="description"></a>Beskrivelse

Denne navngivne enhed SIT matcher personlige navne, som et mennesker ville identificere som et navn med høj sikkerhed. Hvis der f.eks. findes en streng bestående af et givet navn og efterfølges af et familienavn, foretages der et match med høj tillid. Der bruges tre primære ressourcer:

-   En ordbog med angivne navne.
-   En ordbog med familienavne.
-   Mønstre for, hvordan navne dannes.

De tre ressourcer er forskellige for hvert land.  Strengene *, der betækkes* , udløser et match. Almindelige angivne/familienavne får en større tillid til end sjældnere navne. Men mønsteret tillader også delvise matches. Hvis der findes et givet navn fra ordbogen, og det efterfølges af et familienavn, der ikke findes i ordbogen, udløses et delvist match. For eksempel udløser *Tomas Richard* et delvist match. Delvise match får lavere tillid.

Desuden er mønstre, som et mennesker ville se som mønstre af navne, også matchet med den rette tillid. Ligesom *O.* *2016, O.P. Mrs*, *Dr. O. P. A. AR**, O.P.* eller *T. Richard, Jr.* ville være matches.

### <a name="supported-languages"></a>Understøttede sprog

- English
- Bulgarian
- Kinesisk
- Croatian
- Czech
- Danish
- Estonian
- Finnish
- French
- German
- Hungarian
- Islandsk
- Irsk
- Italian
- Japanese
- Latvian
- Lithuanian
- Maltesisk
- Dutch
- Norsk
- Polish
- Portugisisk
- Romanian
- Slovak
- Slovenian
- Spanish
- Swedish
- Turkish


## <a name="all-medical-terms-and-conditions"></a>Alle medicinske vilkår og betingelser

All medical terms and conditions is a bundled named entity that detects medical terms and medical conditions. Det registrerer kun engelske vilkår. Brug denne SIT til at registrere alle mulige forekomster af medicinske vilkår og betingelser.

### <a name="format"></a>Formatér

Ordbog

### <a name="pattern"></a>Mønster

Ordbog

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="description"></a>Beskrivelse

Denne pakkede navngivne enhed matcher tekst, der omtaler medicinske tilstande, der findes i brugerordbøger. Der er én brugerordbog pr. understøttet sprog. Ordbøgerne er fra mange internationale medicinske ressourcer. Ordbøgerne indeholder så mange medicinske tilstande som muligt uden at risikere et stort antal falske positive. Hver post indeholder de forskellige formularer, som en enkelt betingelse ofte er skrevet i for at sikre dækning, f.eks.:

- *TB*
- *kartis*
- *phthisis pulmonalis*

### <a name="contains"></a>Indeholder

Denne pakkede navngivne enhed SIT indeholder disse individuelle SIT'er.

- Termer ved test af blodsukker 
- Typer af medicin
- Værdier
- Generiske medicinnavne
- Forringelser angivet i USA Disability Evaluation Under Social Security
- Lab-testvilkår
- Livsstile, der er relateret til medicinske tilstande
- Lægespecialiteter
- Procedurer, der kan fjerne dig fra den
- Navne på medicin


## <a name="all-physical-addresses"></a>Alle fysiske adresser

Alle fysiske adresser er et samlet SÆT-sæt, der registrerer mønstre relateret til fysiske adresser fra alle understøttede lande/områder.

### <a name="format"></a>Formatér

Forskellige

### <a name="pattern"></a>Mønster

Forskellige

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="description"></a>Beskrivelse

Matchning af postadresser er beregnet til at matche strenge, som et mennesker ville identificere som en postadresse. Det gør den ved at bruge flere primære ressourcer:

-   En ordbog med afregninger, amter og områder.
-   En ordbog med gadesuffikser, f.eks. Vej, Gade eller Veje.
-   Mønstre af postnumre.
-   Mønstre for adresseformater.

Ressourcerne er forskellige for hvert land. De primære ressourcer er mønstret for adresseformater, der bruges i et givet land. Forskellige formater vælges for at sikre, at så mange adresser som muligt matches. Disse formater giver fleksibilitet, f.eks. kan en adresse udelade postnummeret eller udelade et bynavn eller have en gade uden suffiks. I alle tilfælde bruges sådanne match til at øge fortroligheden af matchet.

Mønstrene er designet til at matche individuelle enkelte adresser, ikke generiske placeringer. Så strenge som *Redmond, WA 98052* eller *Main Street matcher Albuquerque* ikke.

### <a name="contains"></a>Indeholder

Denne pakkede navngivne enheds-SIT indeholder disse individuelle SIT'er:

- Fysiske adresser i Australien
- Fysiske adresser i Østrig
- Fysiske adresser i Belgien
- Fysiske adresser i Brasilien
- Fysiske adresser i Bulgarien
- Fysiske adresser i Canada
- Kroatiens fysiske adresser
- Fysiske adresser i Cypern
- Fysiske adresser for Tjekkiet
- Fysiske adresser i Danmark
- Fysiske adresser i Estland
- Finlands fysiske adresser
- Fysiske adresser i Frankrig
- Fysiske adresser i Tyskland
- Fysiske adresser i Grækenland
- Fysiske adresser i Ungarn
- Fysiske adresser i Island
- Fysiske adresser i Irland
- Fysiske adresser i Italien
- Fysiske adresser i Letland
- Liechtenstein fysiske adresser
- Fysiske adresser i Litauen
- Fysiske adresser i Luxembourg
- Fysiske adresser på Malta
- Nederlandske fysiske adresser
- New Zealand fysiske adresser
- Fysiske adresser i Norge
- Fysiske adresser i Polen
- Fysiske adresser i Portugal
- Fysiske adresser i Rumænien
- Fysiske adresser i Slovakiet
- Fysiske adresser i Slovenien
- Fysiske adresser i Spanien
- Fysiske adresser i Sverige
- Schweiz fysiske adresser
- Tyrkiets fysiske adresser
- Fysiske adresser for Storbritannien
- USA's fysiske adresser

### <a name="supported-languages"></a>Understøttede sprog

- English
- Bulgarian
- Kinesisk
- Croatian
- Czech
- Danish
- Estonian
- Finnish
- French
- German
- Hungarian
- Islandsk
- Irsk
- Italian
- Japanese
- Latvian
- Lithuanian
- Maltesisk
- Dutch
- Norsk
- Polish
- Portugisisk
- Romanian
- Slovak
- Slovenian
- Spanish
- Swedish
- Turkish


## <a name="argentina-national-identity-dni-number"></a>Argentina national identity (DNI) number

### <a name="format"></a>Formatér

Otte cifre med eller uden punktummer

### <a name="pattern"></a>Mønster

Otte cifre:
- to cifre
- et valgfrit punktum
- Tre cifre
- et valgfrit punktum
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
- cedula
- cédula
- dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp


## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Argentina Unique Tax Identification Key (CUIT/CUIL)

### <a name="format"></a>Formatér

11 cifre med bindestreg

### <a name="pattern"></a>Mønster

11 cifre med en bindestreg:
- To cifre i 20, 23, 24, 27, 30, 33 eller 34
- en bindestreg (-)
- otte cifre
- en bindestreg (-)
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_Argentina_Unique_Tax_Key` indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_Argentina_Unique_Tax_Key` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_Argentina_Unique_Tax_Key` indhold, der svarer til mønsteret.

```xml
    <!-- Argentina Unique Tax Identification Key (CUIT/CUIL) -->
      <Entity id="98da3da1-9199-4571-b7c4-b6522980b507" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
          <Match idRef="Keyword_Argentina_Unique_Tax_Key" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Argentina_Unique_Tax_Key" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- entydig kode for identifikation af id 
- Clave Única de Identificación Tributaria
- entydig identifikationskode til identifikation af id
- CUIL
- Entydig skatteidentifikationsnøgle
- Entydig identifikationsnøgle til identifikation af id
- Entydig nøgle til identifikation af id
- Entydig arbejdsidentifikationskode
- Entydig kode for arbejdsidentifikation
- Entydig arbejdsidentifikationsnøgle
- Entydig nøgle til arbejdsidentifikation
- Entydig kode for skatteidentifikation
- Entydig nøgle til skatteidentifikation
- Unique Labor Identification Code
- Unique Code of Labor Identification
- Unique Labor Identification Key
- Unique Key of Labor Identification
- moms-id
- taxID #
- taxId
- kørenummer
- momsnummer
- momsnr.
- moms #
- moms #
- skatteyder-id
- skatteydernummer
- skatteyder nej
- skatteyder #
- skatteyder #
- skatteidentitet
- skatteidentifikation
- Número de Identificación Fiscal
- número de contribuyente


## <a name="australia-bank-account-number"></a>Australiens bankkontonummer

### <a name="format"></a>Formatér

seks til 10 cifre med eller uden et bankstatsgrensnummer

### <a name="pattern"></a>Mønster

Kontonummeret er 6 til 10 cifre.

Australiens bankstatsgrensnummer:
- Tre cifre
- en bindestreg
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_australia_bank_account_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_australia_bank_account_number nøgleord.
- Det regulære udtryk Regex_australia_bank_account_number_bsb indhold, der svarer til mønsteret.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_australia_bank_account_number indhold, der svarer til mønsteret.

- Der er fundet Keyword_australia_bank_account_number nøgleord.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- swift bankkode
- korrespondens bank
- grundvaluta
- USA-konto
- holderadresse
- bankkonto
- oplysningskonto
- fondsoverførsler
- bankgebyrer
- bankoplysninger
- bankoplysninger
- fulde navne
- ane


## <a name="australia-business-number"></a>Australiens forretningsnummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:

- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11 cifre med valgfrie afgrænsere

### <a name="pattern"></a>Mønster

11 cifre med valgfrie afgrænsere:

- to cifre
- En valgfri bindestreg eller et mellemrum
- Tre cifre
- En valgfri bindestreg eller et mellemrum
- Tre cifre
- En valgfri bindestreg eller et mellemrum
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_australian_business_number, der svarer til mønsteret.
- Der er fundet Keywords_australian_business_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_australian_business_number, der svarer til mønsteret.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australia business no
- forretningsnummer
- abn #
- forretnings-id #
- firma-id
- abn
- businessno #


## <a name="australia-company-number"></a>Australiens firmanummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:

- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

ni cifre med separatortegn

### <a name="pattern"></a>Mønster

ni cifre med separatortegn:

- Tre cifre
- et mellemrum
- Tre cifre
- et mellemrum
- Tre cifre


### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Australian_Company_Number, der svarer til mønsteret.
- Der er fundet Keyword_Australian_Company_Number nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Australian_Company_Number, der svarer til mønsteret.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- kan
- australien firmanr.
- australien firmanr. #
- Australiens firmanummer
- australske firmanr.
- australske firmanr. #
- australske firmanummer


## <a name="australia-drivers-license-number"></a>Australiens kørekortnummer

### <a name="format"></a>Formatér

ni bogstaver og cifre

### <a name="pattern"></a>Mønster

ni bogstaver og cifre:

- To cifre eller bogstaver (der er ikke store bogstaver)
- to cifre
- fem cifre eller bogstaver (der er ikke store bogstaver)

ELLER

- et til to valgfrie bogstaver (der er ikke tale om store og små bogstaver)
- fire til ni cifre

ELLER

- ni cifre eller bogstaver (der er ikke store bogstaver)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_australia_drivers_license_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_australia_drivers_license_number nøgleord.
- Der er ikke fundet Keyword_australia_drivers_license_number_exclusions nøgleord.

```xml
<!-- Australia Drivers License Number -->
<Entity id="1cbbc8f5-9216-4392-9eb5-5ac2298d1356" patternsProximity="300" recommendedConfidence="75">
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_drivers_license_number" />
        <Match idRef="Keyword_australia_drivers_license_number" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_australia_drivers_license_number_exclusions" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- internationale køretilladelser
- australsk bilsammenknytning
- international køretilladelse
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørelicenser
- Kørekort
- Kørekort
- Kørekort
- Køre Lic
- Køre kørekort
- Kørekort
- Kørelicenser
- Køre'Lic
- Kørekort
- Kørekort
- Køre'licenser
- Køre' lic
- Køre' kørekort
- Kørekort
- Køre' licenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørelicenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Køre Lic #
- Køre kørekort #
- Kørekort #
- Kørelicenser #
- Køre'Lic #
- Kørekort #
- Kørekort #
- Køre'licenser #
- Køre' lic #
- Køre' kørekort #
- Kørekort #
- Køre' licenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- aaa
- Kørekort
- Kørekort
- Kørekort
- Kørelicenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Køre'licenser
- Kørekort
- Køre' licenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort #
- Kørekort #
- Kørekort #
- Kørelicenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Køre'licenser #
- Kørekort #
- Køre' licenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #


## <a name="australia-medical-account-number"></a>Australiens medicinske kontonummer

### <a name="format"></a>Formatér

10-11 cifre

### <a name="pattern"></a>Mønster

10-11 cifre:
- Første ciffer er i området 2-6
- Niende ciffer er et kontrolcifre
- Tiende ciffer er problemcifret
- Det 11. ciffer (valgfrit) er det individuelle nummer

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_australian_medical_account_number, der svarer til mønsteret.
- Der er fundet Keyword_Australia_Medical_Account_Number nøgleord.
- Kontrolsummet overføres.


```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- bankkontooplysninger
- medaljebetalinger
- realkreditkonto
- bankbetalinger
- informationsgren
- kreditkortlån
- afdeling for HR-tjenester
- lokal tjeneste
- medicare


## <a name="australia-passport-number"></a>Australiens pasnummer

### <a name="format"></a>Formatér

otte eller ni alfanumeriske tegn

### <a name="pattern"></a>Mønster

- et bogstav (N, E, D, F, A, C, U, X) efterfulgt af syv cifre eller
- To bogstaver (PA, PB, pc, PD, PE, PF, PU, PW, PX, PZ) efterfulgt af syv cifre.

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_australia_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_australia_passport_number` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_australia_passport_number` finder indhold, der svarer til mønsteret.

```xml
    <!-- Australia Passport Number -->
    <Entity id="29869db6-602d-4853-ab93-3484f905df50" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_passport_number" />
        <Match idRef="Keyword_australia_passport_number" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_australia_passport_number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre
- pasoplysninger
- arret og ikke-fortrind
- a australien
- afdeling afgrening
- nationalt identitetskort
- rejsedokument
- udstedende myndighed


## <a name="australia-physical-addresses"></a>Fysiske adresser i Australien 

Ubundet navngivet enhed, registrerer mønstre relateret til fysiske adresser fra Australien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau
mellem


## <a name="australia-tax-file-number"></a>Australiens momsfilnummer

### <a name="format"></a>Formatér

otte til ni cifre

### <a name="pattern"></a>Mønster

otte til ni cifre præsenteres typisk med mellemrum på følgende måde:
- Tre cifre
- et valgfrit mellemrum
- Tre cifre
- et valgfrit mellemrum
- to til tre cifre, hvor det sidste ciffer er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_australian_tax_file_number, der svarer til mønsteret.
- Der er ikke Keyword_Australia_Tax_File_Number eller Keyword_number_exclusions nøgleord.
- Kontrolsummet overføres.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- australsk virksomhedsnummer
- momssats for 100 %.
- medaljevinder
- porteføljenummer
- servicemedarbejdere
- moms
- individuel selvangivelse
- momsfilnummer
- tfn


## <a name="austria-drivers-license-number"></a>Østrigs kørekortnummer

### <a name="format"></a>Formatér

Otte cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk  `Regex_austria_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_austria_eu_driver's_license_number` fra eller.

```xml
      <!-- Austria Driver's License Number -->
      <Entity id="682f18ce-44eb-482b-8198-2bcb96a0761e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_austria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver ikke s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern


## <a name="austria-identity-card"></a>Østrigs identitetskort

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

En kombination af 24 tegn, cifre og specialtegn

### <a name="pattern"></a>Mønster

24 tegn:

-  22 bogstaver (der er ikke store bogstaver), cifre, skråstreger, skråstreger eller plustegn

- To bogstaver (der er ikke store bogstaver), cifre, skråstreger, skråstreger plustegn eller lighedstegn

### <a name="checksum"></a>Kontrolsum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk  `Regex_austria_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_austria_eu_national_id_card` nøgleord fra.

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- identitetsnummer
- nationalt id
- personalausweis republik österreich


## <a name="austria-passport-number"></a>Østrigs pasnummer

### <a name="format"></a>Formatér

Et bogstav efterfulgt af et valgfrit mellemrum og syv cifre

### <a name="pattern"></a>Mønster

En kombination af et bogstav, syv cifre og ét mellemrum:

- et bogstav (der er ikke tale om store og små bogstaver)
- et mellemrum (valgfrit)
- syv cifre

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_austria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_austria_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_austria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_austria_eu_passport_number` fra eller.

```xml
      <!-- Austria Passport Number -->
      <Entity id="1c96ae4e-303b-447d-86c7-77113ac266bf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_austria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_austria_eu_passport_number"></a>Keywords_austria_eu_passport_number

- reisepassnummer
- reisepasse
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="austria-physical-addresses"></a>Fysiske adresser i Østrig

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Østrig. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="austria-social-security-number"></a>Østrigs CPR-nummer

### <a name="format"></a>Formatér

10 cifre i det angivne format

### <a name="pattern"></a>Mønster

10 cifre:

- Tre cifre, der svarer til et serienummer
- et kontrolcifre
- seks cifre, der svarer til fødselsdatoen (DDMMYY)

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_austria_eu_ssn_or_equivalent` indhold, der svarer til mønsteret.
- der er fundet et  `Keywords_austria_eu_ssn_or_equivalent` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_austria_eu_ssn_or_equivalent` indhold, der svarer til mønsteret.

```xml
      <!-- Austria Social Security Number -->
      <Entity id="6896a906-86c9-4d19-a2da-6e43ccd19b7b" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_austria_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_austria_eu_ssn_or_equivalent" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_austria_eu_telephone_number" />
            <Match idRef="Keywords_austria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- østrig ssn
- ehic-nummer
- erotisk nej
- forsikringskode
- insurancecode #
- forsikringsnummer
- forsikringsnr.
- krankenkassennummer
- krankenversicherung
- socialsecurityno
- socialsecurityno #
- cpr-nr
- CPR-nummer
- CPR-kode
- soalolversicherungsnummer
- soalolversicherungsnummer #
- soibile sicherheit kein
- sotlesicherheitkein #
- ssn #
- ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje


## <a name="austria-tax-identification-number"></a>Skatte-id-nummer for Østrig

### <a name="format"></a>Formatér

ni cifre med valgfri bindestreg og skråstreg

### <a name="pattern"></a>Mønster

ni cifre med valgfri bindestreg og skråstreg:

- to cifre
- en bindestreg (valgfrit)
- Tre cifre
- en skråstreg (valgfrit)
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_austria_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_austria_eu_tax_file_number` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_austria_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Austria Tax Identification Number -->
      <Entity id="4fd58d22-af28-4451-b18a-6f722430a56d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
          <Match idRef="Keywords_austria_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_austria_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- österreich
- st.nr.
- steuernummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- momsnummer


## <a name="austria-value-added-tax"></a>Momssats for Østrig

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11-tegns alfanumeriske mønster

### <a name="pattern"></a>Mønster

11-tegns alfanumeriske mønster:

- A eller a
- T eller t
- Valgfrit mellemrum
- U eller u
- valgfrit mellemrum
- to eller tre cifre
- valgfrit mellemrum
- fire cifre
- valgfrit mellemrum
- et eller to cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Austria_Value_Added_Tax, der svarer til mønsteret.
- Der er fundet Keyword_Austria_Value_Added_Tax nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Austria_Value_Added_Tax, der svarer til mønsteret.

```xml
      <!-- Austria Value Added Tax -->
      <Entity id="b6a3eda2-c56c-4b69-a5f7-dca34db00f48" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
          <Match idRef="Keyword_Austria_Value_Added_Tax" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_Austria_Value_Added_Tax" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- momsnummer
- moms #
- Vat-nummer for Vat i Østrig
- momsnr.
- vatno #
- momsnummer for værdi tilføjet
- Vat (Vat) i Østrig
- ater
- umsatzsteuernummer
- brasilienstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- moms-id
- atu-nummer
- uid-nummer


## <a name="azure-documentdb-auth-key"></a>Azure DocumentDB auth-nøgle

### <a name="format"></a>Formatér

Strengen "DocumentDb" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- Strengen "DocumentDb"
- Enhver kombination af mellem 3-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- Større end (>), et lighedstegn (=), et anførselstegn (") eller en apostrof (')
- En kombination af 86 små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- To lighedstegn (=)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_AzureDocumentDBAuthKey, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```xml
<!-- Azure Document DB Auth Key -->
<Entity id="0f587d92-eb28-44a9-bd1c-90f2892b47aa" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureDocumentDBAuthKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
          </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Teknisk set identificerer denne type følsomme oplysninger disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord).

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Forbindelsesstreng for Azure IAAS-database og Azure SQL forbindelsesstreng

### <a name="format"></a>Formatér

Strengen "Server", "server" eller "datakilde" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor, herunder strengen "cloudapp.azure.<!--no-hyperlink-->com" eller "cloudapp.azure.<!--no-hyperlink-->net" eller "database.windows.<!--no-hyperlink-->net", og strengen "Adgangskode" eller "adgangskode" eller "pwd".

### <a name="pattern"></a>Mønster

- strengen "Server", "server" eller "datakilde"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- Strengen "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net" eller "database.windows.<!--no-hyperlink-->net"
- en kombination af 1-300 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "Adgangskode", "adgangskode" eller "pwd"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- et eller flere tegn, der ikke er et semikolon (;), anførselstegn (") eller apostrof (')
- et semikolon (;), anførselstegn (") eller apostrof (')

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk CEP_Regex_AzureConnectionString indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne type følsomme oplysninger disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord).

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-iot-connection-string"></a>Azure IoT-forbindelsesstreng

### <a name="format"></a>Formatér

Strengen "HostName" efterfulgt af de tegn og strenge, der er beskrevet i nedenstående mønster, herunder strengene "azure-enheder.<!--no-hyperlink-->net" og "SharedAccessKey".

### <a name="pattern"></a>Mønster

- strengen "HostName"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "azure-enheder.<!--no-hyperlink-->net"
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "SharedAccessKey"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43 små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- et lighedstegn (=)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_AzureIoTConnectionString, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord.

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-publish-setting-password"></a>Azure-publiceringsindstillingsadgangskode

### <a name="format"></a>Formatér

Strengen "userpwd=" efterfulgt af en alfanumerisk streng.

### <a name="pattern"></a>Mønster

- strengen "userpwd="
- en kombination af 60 små bogstaver eller cifre
- et anførselstegn (")

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk CEP_Regex_AzurePublishSettingPasswords indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.


```xml
<!--Azure Publish Setting Password-->
<Entity id="75f4cc8a-a68e-49e5-89ce-fa8f03d286a5" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
       <IdMatch idRef="CEP_Regex_AzurePublishSettingPasswords" />
       <Any minMatches="0" maxMatches="0">
           <Match idRef="CEP_CommonExampleKeywords" />
       </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord.

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-redis-cache-connection-string"></a>Azure Redis-cacheforbindelsesstreng

### <a name="format"></a>Formatér

Strengen "redis.cache.windows.<!--no-hyperlink-->net" efterfulgt af de tegn og strenge, der er beskrevet i nedenstående mønster, herunder strengen "adgangskode" eller "pwd".

### <a name="pattern"></a>Mønster

- strengen "redis.cache.windows.<!--no-hyperlink-->net"
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "adgangskode" eller "pwd"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- et lighedstegn (=)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_AzureRedisCacheConnectionString, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```xml
<!--Azure Redis Cache Connection String-->
<Entity id="095a7e6c-efd8-46d5-af7b-5298d53a49fc" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureRedisCacheConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne type følsomme oplysninger disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord).

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Formatér

Strengen "sig" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- strengen "sig"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43-53 tegn, der er små eller store bogstaver, cifre eller procenttegn (%)
- strengen "%3d"
- alle tegn, der ikke er et lille eller stort bogstav, et tal eller et procenttegn (%)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk CEP_Regex_AzureSAS indhold, der svarer til mønsteret.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Azure service bus forbindelsesstreng

### <a name="format"></a>Formatér

Strengen "Slutpunkt" efterfulgt af de tegn og strenge, der er beskrevet i nedenstående mønster, herunder strengene "servicebus.windows.<!--no-hyperlink-->net" og "SharedAccesKey".

### <a name="pattern"></a>Mønster

- strengen "Slutpunkt"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "servicebus.windows.<!--no-hyperlink-->net"
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "SharedAccessKey"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- et lighedstegn (=)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_AzureServiceBusConnectionString, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```xml
<!--Azure Service Bus Connection String-->
<Entity id="b9a6578f-a83f-4fcd-bf44-2130bae49a6f" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureServiceBusConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne type følsomme oplysninger disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord).

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key"></a>Azure Storage-kontonøgle

### <a name="format"></a>Formatér

Strengen "DefaultEndpointsProtoskildpadde" efterfulgt af de tegn og strenge, der er beskrevet i nedenstående mønster, herunder strengen "AccountKey".

### <a name="pattern"></a>Mønster

- strengen "DefaultEndpointsProto hele"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "AccountKey"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 86 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- to lighedstegn (=)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_AzureStorageAccountKey, der svarer til mønsteret.
- Det regulære udtryk CEP_AzureEmulatorStorageAccountFilter ikke indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```xml
<!--Azure Storage Account Key-->
<Entity id="c7bc98e8-551a-4c35-a92d-d2c8cda714a7" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKey" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_AzureEmulatorStorageAccountFilter" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(Teknisk set identificerer denne type følsomme oplysninger disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord).

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne type følsomme oplysninger disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord).

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="azure-storage-account-key-generic"></a>Azure Storage-kontonøgle (generic)

### <a name="format"></a>Formatér

Enhver kombination af 86 små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+) indledes eller efterfølges af de tegn, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- nul til et af større end-symbolet (>), apostrof ('), lighedstegn (=), anførselstegn (") eller taltegn (#)
- en kombination af 86 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- to lighedstegn (=)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_AzureStorageAccountKeyGeneric, der svarer til mønsteret.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```


## <a name="belgium-drivers-license-number"></a>Belgiens kørekortnummer

### <a name="format"></a>Formatér

10 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_belgium_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_driver's_license_number` nøgleord `Keywords_belgium_eu_driver's_license_number` fra eller.

```xml
      <!-- Belgium Driver's License Number -->
      <Entity id="d89fd329-9324-433c-b687-2c37bd5166f3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_belgium_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver ikke s_license_number

- rijbewijs
- rijbewijsnummer
- führerschein
- führerscheinnummer
- füehrerscheinnummer
- fuhrerschein
- fuehrerschein
- fuhrerscheinnummer
- fuehrerscheinnummer
- permis de conduire
- numéro permis conduire


## <a name="belgium-national-number"></a>Nationalt Belgien-nummer

### <a name="format"></a>Formatér

11 cifre plus valgfrie afgrænsere

### <a name="pattern"></a>Mønster

11 cifre plus separatortegn:
- seks cifre og to valgfrie punktummer i formatet YY. MM.DD for fødselsdato
- En valgfri afgrænser fra prik, bindestreg, mellemrum
- tre sekventielle cifre (ulige for hanner, selv for kvinder)
- En valgfri afgrænser fra prik, bindestreg, mellemrum
- to kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_belgium_national_number, der svarer til mønsteret.
- Der er fundet Keyword_belgium_national_number nøgleord.
- Kontrolsummet overføres.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_belgium_national_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Belgium National Number -->
       <Entity id="fb969c9e-0fd1-4b18-8091-a2123c5e6a54" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_national_number" />
          <Match idRef="Keyword_belgium_national_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_belgium_national_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- lastende aantal
- bnn #
- bnn
- carte d'identité
- identifiant national
- identifiantnational #
- identificatie
- identifikation
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- identitet
- dat
- nationalt nummer
- nationalt register
- nationalnumber #
- nationalnumber
- nif #
- nif
- numéro d'assuré
- numéro de registrer nationale
- numéro de sécurité
- numéro d'identification
- numéro d'itrictriculation
- numéro national
- numéronational #
- personligt id-nummer
- personalausweis
- personalidnumber #
- registrator
- registrering
- registreringernumme
- registrierung
- CPR-nummer
- ssn #
- ssn
- steuernummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="belgium-passport-number"></a>Belgiens pasnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af seks cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver og efterfulgt af seks cifre

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

 En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_belgium_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_belgium_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date2` udtryk finder dato i formatet DD MM-JY eller et nøgleord fra `Keywords_eu_passport_date` eller `Keywords_belgium_eu_passport_number` findes

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_belgium_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_belgium_eu_passport_number` fra eller.

```xml
      <!-- Belgium Passport Number -->
      <Entity id="d7b1315b-21ca-4774-a32a-596010ff78fd" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
            <Match idRef="Keywords_belgium_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_belgium_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_belgium_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr
- paspoort-nr
- paspoortnummer
- paspoortnummers
- Passeport carte
- Passeport livre
- Pass-Nr
- Passnummer
- reisepass kein

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="belgium-physical-addresses"></a>Fysiske adresser i Belgien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Belgien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="belgium-value-added-tax-number"></a>Belgien momsnummer tilføjet moms

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

12-tegns alfanumeriske mønster

### <a name="pattern"></a>Mønster

12-tegns alfanumeriske mønster:

- a letter B or b
- et bogstav E eller e
- et ciffer 0
- et ciffer fra 1 til 9
- En valgfri prik eller bindestreg eller et mellemrum
- fire cifre
- En valgfri prik eller bindestreg eller et mellemrum
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_belgium_value_added_tax_number, der svarer til mønsteret.
- Der er fundet Keywords_belgium_value_added_tax_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_belgium_value_added_tax_number, der svarer til mønsteret.

```xml
      <!-- Belgium Value Added Tax Number -->
      <Entity id="85b5b3c3-f2de-4ae8-ac46-fd3cb38bf9ed" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
          <Match idRef="Keywords_belgium_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_belgium_value_added_tax_number" />
        </Pattern>
      </Entity>
    </Version>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- momsnummer
- momsnr.
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- ane
- ane #
- moms #


## <a name="blood-test-terms"></a>Termer ved test af blodsukker

Denne ubundede navngivne enhed registrerer ord relateret til prøver, f.eks *hCG*. Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj

## <a name="brand-medication-names"></a>Navne på medicin

This unbundled named entity detects names of brand medicin, such as *Tylenol*. Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="brazil-cpf-number"></a>Brasilien CPF-nummer

### <a name="format"></a>Formatér

11 cifre, der indeholder et kontrolcifre og kan være formateret eller uformateret

### <a name="pattern"></a>Mønster

Formateret:
- Tre cifre
- et punktum
- Tre cifre
- et punktum
- Tre cifre
- en bindestreg
- To cifre, der er kontrolcifre

Uformateret:
- 11 cifre, hvor de sidste to cifre er cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_brazil_cpf, der svarer til mønsteret.
- Der er fundet Keyword_brazil_cpf nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_brazil_cpf, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Brazil CPF Number -->
<Entity id="78e09124-f2c3-4656-b32a-c1a132cd2711" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cpf"/>
     <Match idRef="Keyword_brazil_cpf"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cpf"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_brazil_cpf"></a>Keyword_brazil_cpf

- CPF
- Identifikation
- Registrering
- Indtægter
- Cadastro de Pessoas Físicas
- Imposto
- Identificação
- Inscrição
- Receita


## <a name="brazil-legal-entity-number-cnpj"></a>Brasiliens juridiske enhedsnummer (CNPJ)

### <a name="format"></a>Formatér

14 cifre, der indeholder et registreringsnummer, et afdelingsnummer og et checkcifre samt afgrænsere

### <a name="pattern"></a>Mønster

14 cifre plus afgrænsere:

- to cifre
- et punktum
- Tre cifre
- et punktum
- Tre cifre (disse første otte cifre er registreringsnummeret)
- en skråstreg
- firecifret forgreningsnummer
- en bindestreg
- To cifre, der er kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_brazil_cnpj, der svarer til mønsteret.
- Der er fundet Keyword_brazil_cnpj nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_brazil_cnpj, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Brazil Legal Entity Number (CNPJ) -->
<Entity id="9b58b5cd-5e90-4df6-b34f-1ebcc88ceae4" recommendedConfidence="85" patternsProximity="300">
   <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_brazil_cnpj"/>
     <Match idRef="Keyword_brazil_cnpj"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_brazil_cnpj"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- Nationalt register over juridiske enheder
- Skatteregistreringsdatabase
- Juridisk enhed
- Juridiske enheder
- Registreringsstatus
- Business
- Firma
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadastral
- Inscrição
- Empresa


## <a name="brazil-national-identification-card-rg"></a>Brasiliens nationale identifikationskort (RG)

### <a name="format"></a>Formatér

Registro Geral (gammelt format): Ni cifre

Registro de Identidade (RIC) (nyt format): 11 cifre

### <a name="pattern"></a>Mønster

Registro Geral (gammelt format):
- to cifre
- et punktum
- Tre cifre
- et punktum
- Tre cifre
- en bindestreg
- et ciffer, som er et kontrolcifre

Registro de Identidade (RIC) (nyt format):
- 10 cifre
- en bindestreg
- et ciffer, som er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_brazil_rg, der svarer til mønsteret.
- Der er fundet Keyword_brazil_rg nøgleord.
- Kontrolsummet overføres.


```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- identitetskort
- nationalt id
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (der er store og små bogstaver i dette nøgleord)
- RIC (der er store og små bogstaver i dette nøgleord)


## <a name="brazil-physical-addresses"></a>Fysiske adresser i Brasilien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Brasilien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem

## <a name="bulgaria-drivers-license-number"></a>Bulgariens kørekortnummer

### <a name="format"></a>Formatér

ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_bulgaria_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_bulgaria_eu_driver's_license_number` fra eller.

```xml
      <!-- Bulgaria Driver's License Number -->
      <Entity id="66d39258-94c2-43b2-804b-aa312258e54b" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_bulgaria_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver ikke s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки


## <a name="bulgaria-passport-number"></a>Bulgariens pasnummer

### <a name="format"></a>Formatér

ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_bulgaria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_bulgaria_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_bulgaria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_bulgaria_eu_passport_number` fra eller.

```xml
      <!-- Bulgaria Passport Number -->
      <Entity id="f7172b82-c588-4216-845e-4e54e397f29a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт No

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="bulgaria-physical-addresses"></a>Fysiske adresser i Bulgarien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Bulgarien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem

## <a name="bulgaria-uniform-civil-number"></a>Bulgariens uniformsnummer
Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

10 cifre uden mellemrum og separatortegn

- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- To cifre, der svarer til fødselsrækkefølgen
- et ciffer, der svarer til køn: Et lige ciffer for mand og et ulige ciffer for kvinde
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_bulgaria_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_bulgaria_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_bulgaria_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinenhdanski nomer
- egn #
- egn
- id-nummer
- nationalt id
- nationalt nummer
- nationalnumber #
- nationalnumber
- personligt id
- personligt nej
- personligt nummer
- personalidnumber #
- CPR-nummer
- ssn #
- ssn
- Uniform civilt id
- Uniform civil no
- uniform civilnummer
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- entydigt nummer på telefonnummer
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ id
- униформ графдански id
- униформ граждански не
- униформ граждански номер
- униформграфданскиid #
- униформгражданскине. #


## <a name="canada-bank-account-number"></a>Canadas bankkontonummer

### <a name="format"></a>Formatér

7 eller 12 cifre

### <a name="pattern"></a>Mønster

Et Canada Bank Account-nummer er 7 eller 12 cifre.

Transitnummeret for en Canada-bankkonto er:
- fem cifre
- en bindestreg
- tre cifre ELLER
- et nul "0"
- otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Udtrykket for det Regex_canada_bank_account_number finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_canada_bank_account_number nøgleord.
- Det regulære udtryk Regex_canada_bank_account_transit_number indhold, der svarer til mønsteret.

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Udtrykket for det Regex_canada_bank_account_number finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_canada_bank_account_number nøgleord.

```xml
<!-- Canada Bank Account Number -->
<Entity id="552e814c-cb50-4d94-bbaa-bb1d1ffb34de" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
        <Match idRef="Regex_canada_bank_account_transit_number" />
   </Pattern>
   <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_bank_account_number" />
        <Match idRef="Keyword_canada_bank_account_number" />
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- Canada savings obligation
- Canada Revenue Agency
- canadisk finansiel institution
- formular til direkte indbetaling
- canadiske borgere
- juridisk repræsentant
- notar
- eder ud til oaths
- fordel ved pasning af børn
- universel pasning af børn
- momsfordel for canada-barn
- indtægtsafgiftsfordel
- moms
- cpr-nummer
- refusion for indtægtsafgift
- momsfordel for børn
- payments
- institutionens nummer
- anmodning om indbetaling
- bankoplysninger
- direkte indskud


## <a name="canada-drivers-license-number"></a>Canada-kørekortnummer

### <a name="format"></a>Formatér

Varierer efter provins

### <a name="pattern"></a>Mønster

Forskellige mønstre, som dækker:
- Alberta
- British Columbia
- Manitoba
- New Brunswick
- Newfoundland/Labrador
- Nova Scotia
- Ontario
- Prince Edward Island
- Quebec
- Saskatchewan

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen i Func_[province_name]_drivers_license_number finder indhold, der svarer til mønsteret.
- Der er fundet et nøgleord Keyword_[province_name]_drivers_license_name nøgleord.
- Der er fundet Keyword_canada_drivers_license nøgleord.

```xml
<!-- Canada Driver's License Number -->
    <Entity id="37186abb-8e48-4800-ad3c-e3d1610b3db0" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_alberta_drivers_license_number" />
        <Match idRef="Keyword_alberta_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_british_columbia_drivers_license_number" />
        <Match idRef="Keyword_british_columbia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_manitoba_drivers_license_number" />
        <Match idRef="Keyword_manitoba_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_brunswick_drivers_license_number" />
        <Match idRef="Keyword_new_brunswick_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_newfoundland_labrador_drivers_license_number" />
        <Match idRef="Keyword_newfoundland_labrador_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_nova_scotia_drivers_license_number" />
        <Match idRef="Keyword_nova_scotia_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_ontario_drivers_license_number" />
        <Match idRef="Keyword_ontario_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_prince_edward_island_drivers_license_number" />
        <Match idRef="Keyword_prince_edward_island_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_quebec_drivers_license_number" />
        <Match idRef="Keyword_quebec_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_saskatchewan_drivers_license_number" />
        <Match idRef="Keyword_saskatchewan_drivers_license_name" />
        <Match idRef="Keyword_canada_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- Provinsforkortelsen, f.eks. AB
- Provinsnavnet, f.eks. Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørelicenser
- Kørekort
- Kørelicenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Køre Lic
- Køre kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørelicenser
- Køre'Lic
- Kørekort
- Kørekort
- Køre'licenser
- Kørekort
- Køre'licenser
- Køre' lic
- Køre' kørekort
- Kørekort
- Køre' licenser
- Kørekort
- Køre' licenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Permis de Conduire
- id
- id'er
- idcardnummer
- idcardnumre
- idcard #
- idcard #s
- idcard-kort
- idcard-kort
- idcard
- id-nummer
- id-numre
- identifikation #
- identifikations #s
- identifikationskort
- identifikationskort
- identifikation
- DL #
- DLS #
- CDL #
- CDLS #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørelicenser #
- Kørekort #
- Kørelicenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Køre Lic #
- Køre kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørelicenser #
- Køre'Lic #
- Kørekort #
- Kørekort #
- Køre'licenser #
- Kørekort #
- Køre'licenser #
- Køre' lic #
- Køre' kørekort #
- Kørekort #
- Køre' licenser #
- Kørekort #
- Køre' licenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Permis de Conduire #
- id #
- id'er #
- idcard-kort #
- idcard-kort #
- idcard #
- identifikationskort #
- identifikationskort #
- identifikation #


## <a name="canada-health-service-number"></a>Canada health service number

### <a name="format"></a>Formatér

 10 cifre

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_canada_health_service_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_canada_health_service_number nøgleord.

```xml
<!-- Canada Health Service Number -->
<Entity id="59c0bf39-7fab-482c-af25-00faa4384c94" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_health_service_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_health_service_number" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- personligt sundhedsnummer
- patientoplysninger
- sundhedstjenester
- specialtjenester
- bilubilbil
- patient hospital
- mere end 100
- løn til medarbejdere
- handicap


## <a name="canada-passport-number"></a>Canada pasnummer

### <a name="format"></a>Formatér

To store bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

To store bogstaver efterfulgt af seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_canada_passport_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_canada_passport_number eller Keyword_passport nøgleord.

```xml
<!-- Canada Passport Number -->
<Entity id="14d0db8b-498a-43ed-9fca-f6097ae687eb" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_passport_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_canada_passport_number" />
          <Match idRef="Keyword_passport" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- canadiske canadaere
- canadisk pas
- pasprogram
- pasfotos
- certificeret oversætter
- canadiske borgere
- behandlingstider
- fornyelsesprogram

#### <a name="keyword_passport"></a>Keyword_passport

- Pasnummer
- Pasnr.
- Pas #
- Pas #
- Pas-id
- Pasnr
- pasnummer
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport Non
- Passeport #
- Passeport #
- PasseportNon
- Passeportn °


## <a name="canada-personal-health-identification-number-phin"></a>Canadas PHIN -nummer (Personal Health Identification Number)

### <a name="format"></a>Formatér

ni cifre

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_canada_phin finder indhold, der svarer til mønsteret.
- Der er fundet mindst Keyword_canada_phin eller Keyword_canada_provinces nøgleord.

```xml
<!-- Canada PHIN -->
<Entity id="722e12ac-c89a-4ec8-a1b7-fea3469f89db" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_canada_phin" />
        <Any minMatches="2">
          <Match idRef="Keyword_canada_phin" />
          <Match idRef="Keyword_canada_provinces" />
        </Any>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- cpr-nummer
- health information act
- oplysninger om indtægtsafgift
- manitoba health
- tilstandsregistrering
- køb af varer
- fordelsberettigelse
- personlig sundhed
- power of attorney
- registreringsnummer
- personligt sundhedsnummer
- henvisning til en læge
- ane professionel
- patienthenvisning
- tilstand og fitness

#### <a name="keyword_canada_provinces"></a>Keyword_canada_provinces

- Nunavut
- Quebec
- Northwest Territories
- Ontario
- British Columbia
- Alberta
- Saskatchewan
- Manitoba
- Yukon
- Newfoundland og Labrador
- New Brunswick
- Nova Scotia
- Prince Edward Island
- Canada


## <a name="canada-physical-addresses"></a>Fysiske adresser i Canada

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Canada. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="canada-social-insurance-number"></a>Canada Social Insurance Number

### <a name="format"></a>Formatér

ni cifre med valgfri bindestreger eller mellemrum

### <a name="pattern"></a>Mønster

Formateret:
- Tre cifre
- en bindestreg eller et mellemrum
- Tre cifre
- en bindestreg eller et mellemrum
- Tre cifre

Uformateret: ni cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_canadian_sin, der svarer til mønsteret.
- Mindst to af følgende mønstre:
    - Der er fundet Keyword_sin nøgleord.
    - Der er fundet Keyword_sin_collaborative nøgleord.
    - Funktionen finder Func_eu_date en dato i det rigtige datoformat.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_unformatted_canadian_sin, der svarer til mønsteret.
- Der er fundet Keyword_sin nøgleord.
- Kontrolsummet overføres.

```xml
<!-- Canada Social Insurance Number -->
<Entity id="a2f29c85-ecb8-4514-a610-364790c0773e" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_canadian_sin" />
        <Any minMatches="2">
          <Match idRef="Keyword_sin" />
          <Match idRef="Keyword_sin_collaborative" />
          <Match idRef="Func_eu_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_canadian_sin" />
        <Match idRef="Keyword_sin" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_sin"></a>Keyword_sin

- sin
- socialforsikring
- numero d'assurance sociale
- sins
- ssn
- ssn
- social sikring
- numero d'assurance social
- nationalt id-nummer
- nationalt id
- sin #
- soc ins
- sociale netværk

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- kørekort
- kørekort
- kørekort
- kørekort
- DOB
- Fødselsdato
- Fødselsdag
- Fødselsdag


## <a name="chile-identity-card-number"></a>Chiles identitetskortnummer

### <a name="format"></a>Formatér

syv til otte cifre plus afgrænsere et kontrolcifret eller bogstav

### <a name="pattern"></a>Mønster

syv til otte cifre plus afgrænsere:
- et til to cifre
- et valgfrit punktum
- Tre cifre
- et valgfrit punktum
- Tre cifre
- en bindestreg
- et ciffer eller bogstav (der er ikke mellem store og små bogstaver), som er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_chile_id_card, der svarer til mønsteret.
- Der er fundet Keyword_chile_id_card nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_chile_id_card, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Chile Identity Card Number -->
<Entity id="4e979794-49a0-407e-a0b9-2c536937b925" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_chile_id_card"/>
     <Match idRef="Keyword_chile_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_chile_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- national identifikation
- nationalt id-nummer
- nationalt id
- número de identificación nacional
- rol único nacional
- rol único tributario
- KØR
- RUT
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- KØR #
- RUT #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- Chilensk identitetsnr.
- Chilesk identitetsnummer
- Chilensk identitet #
- Entydigt skatteregistreringsdatabase
- Unique Tributary-rolle
- Entydig skatterolle
- Entydigt Tributary-nummer
- Entydigt nationalt nummer
- Entydig national rolle
- National entydig rolle
- Chile identity no.
- Chile-identitetsnummer
- Chile-identitet #
- R.U.T
- R.U.N


## <a name="china-resident-identity-card-prc-number"></a>Kinas iboende identitetskortnummer (Kina)

### <a name="format"></a>Formatér

18 cifre

### <a name="pattern"></a>Mønster

18 cifre:
- seks cifre, som er en adressekode
- Otte cifre i form af YYYYMMDD, som er fødselsdatoen
- Tre cifre, som er en ordrekode
- et ciffer, som er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_china_resident_id, der svarer til mønsteret.
- Der er fundet Keyword_china_resident_id nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_china_resident_id, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- China Resident Identity Card (PRC) Number -->
<Entity id="c92daa86-2d16-4871-901f-816b3f554fc1" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_china_resident_id"/>
     <Match idRef="Keyword_china_resident_id"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_china_resident_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Iboende identitetskort
- Kina
- Nationalt identifikationskort
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定


## <a name="credit-card-number"></a>Kreditkortnummer

### <a name="format"></a>Formatér

14 til 19 cifre, der kan formateres eller ikke-formateres (ddddddddddddd), og som skal bestå Luhn-testen.

### <a name="pattern"></a>Mønster

Det registrerer kort fra alle større mærker over hele verden, herunder Visa, MasterCard, Discover Card, JCB, American Express, gavekort, Diners kort, Rupay og China UnionPay.

### <a name="checksum"></a>Kontrolsum

Ja, Luhn-tjek

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_credit_card, der svarer til mønsteret.
- Et af følgende er sandt:
    - Der er fundet Keyword_cc_verification nøgleord.
    - Der er fundet Keyword_cc_name nøgleord.
    - Funktionen finder Func_expiration_date en dato i det rigtige datoformat.
- Kontrolsummet overføres.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_credit_card, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Credit Card Number -->
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_credit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_cc_verification" />
          <Match idRef="Keyword_cc_name" />
          <Match idRef="Func_expiration_date" />
        </Any>
  </Pattern>
  <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_credit_card" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- kortbekræftelse
- kort-id
- cvn
- cid
- cvc2
- cvv2
- fastgør blok
- sikkerhedskode
- sikkerhedsnummer
- sikkerhedsnr.
- udstedelsesnummer
- udgavenr.
- cryptogramme
- numéro de sécurité
- numero de securite
- kreditkartenprüfnummer
- kreditkartenprufnummer
- prüfziffer
- prufziffer
- sicherheits Kode
- sicherheitscode
- sicherheitsnummer
- verfalldatum
- codice di verifica
- cod. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- cod. seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- cod. seguranca
- cod. segurança
- cód. seguranca
- cód segurança
- cod seguranca
- cod segurança
- cód seguranca
- número de verificação
- numero de verificacao
- ablauf
- gültig bis
- gültigkeitsdatum
- gultig bis
- gultigkeitsdatum
- scadenza
- data scad
- fecha de expiracion
- fecha de venc
- vencimiento
- válido hasta
- valido hasta
- vto
- data de expiração
- data de expiracao
- data em que expira
- validade
- valor
- vencimento
- transaktion
- transaktionsnummer
- referencenummer
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- amex
- american express
- americanexpress
- americano afkod
- Visa
- mastercard
- master card
- mc
- mastercards
- master cards
- diner's Club
- diners club
- dinersspiste
- find
- discover card
- discovercard
- discover cards
- JCB
- BrandSmart
- japanese card bureau
- carte blanche
- carteblanche
- kreditkort
- cc #
- cc#:
- udløbsdato
- udl.dato
- udløbsdato
- date d'expiration
- date d'exp
- dato udløb
- bankkort
- bankkort
- kortnummer
- kortnr.
- kortnummer
- kortnumre
- kortnumre
- kreditkort
- kreditkort
- kreditkort
- ccn
- kortindehaver
- kortholder
- kortindehavere
- kortholdere
- check kort
- checkkort
- check kort
- checkkort
- debetkort
- debetkort
- debetkort
- debetkort
- hæve kort
- hævekort
- hæve kort
- hævekort
- undervejs
- undervejs
- korttype
- Cardmember Acct
- cardmember account
- Cardno
- Firmakort
- Firmakort
- Korttype
- kortkontonummer
- kortmedlemskonto
- Cardmember Acct.
- kortnr.
- kortnr.
- kortnummer
- carte bancaire
- carte de crédit
- carte de credit
- numéro de carte
- numero de carte
- nº de la carte
- nº de carte
- kreditkarte
- karte
- karteninhaber
- karteninhabers
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartentyp
- eigentümername
- kartennr
- kartennummer
- kreditkartennummer
- kreditkarten-nummer
- carta di credito
- carta credito
- n. carta
- n carta
- nr. carta
- nr carta
- numero carta
- numero della carta
- numero di carta
- tarjeta credito
- tarjeta de credito
- tarjeta crédito
- tarjeta de crédito
- tarjeta de atm
- tarjeta atm
- tarjeta debito
- tarjeta de debito
- tarjeta débito
- tarjeta de débito
- nº de tarjeta
- Nej. de tarjeta
- no de tarjeta
- numero de tarjeta
- número de tarjeta
- tarjeta no
- tarjetahabiente
- cartão de crédito
- cartão de credito
- cartao de crédito
- cartao de credito
- cartão de débito
- cartao de débito
- cartão de debito
- cartao de debito
- débito automático
- debito automatico
- número do cartão
- numero do cartão
- número do cartao
- numero do cartao
- número de cartão
- numero de cartão
- número de cartao
- numero de cartao
- nº do cartão
- nº do cartao
- nº. do cartão
- no do cartão
- no do cartao
- Nej. do cartão
- Nej. do cartao
- rupay
- foreningsløn
- unionpay
- diner's
- diners
- クレジットカード番号
- クレジットカードナンバー
- クレジットカード＃
- クレジットカード
- クレジット
- クレカ
- カード番号
- カードナンバー
- カード＃
- アメックス
- アメリカンエクスプレス
- アメリカン エクスプレス
- Visaカード
- Visa カード
- マスターカード
- マスター カード
- マスター
- ダイナースクラブ
- ダイナース クラブ
- ダイナース
- 有効期限
- 期限
- キャッシュカード
- キャッシュ カード
- カード名義人
- カードの名義人
- カードの名義
- デビット カード
- デビットカード
- 中国银联
- 银联


## <a name="croatia-drivers-license-number"></a>Kroatisk kørekortnummer

### <a name="format"></a>Formatér

Otte cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk  `Regex_croatia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_driver's_license_number` nøgleord `Keywords_croatia_eu_driver's_license_number` fra eller.

```xml
      <!-- Croatia Driver's License Number -->
      <Entity id="005b3ef1-47dd-4e68-bb02-c6db484d00f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_croatia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver ikke s_license_number

- vozačka dozvola
- vozačke dozvole


## <a name="croatia-identity-card-number"></a>Kroatiens identitetskortnummer
Denne enhed er inkluderet i typen af følsomme oplysninger om EU-national identifikationsnummer. Den fås som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

ni cifre

### <a name="pattern"></a>Mønster

ni fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_croatia_id_card, der svarer til mønsteret.
- Der er fundet Keyword_croatia_id_card nøgleord.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj graðana
- masternummer for borgere
- nacionalni identifikacijski broj
- nationalt id-nummer
- oib #
- oib
- osobna iskaznica
- osobni-id
- osobni identifikacijski broj
- personligt id-nummer
- porezni broj
- porezni identifikacijski broj
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="croatia-passport-number"></a>Kroatiens pasnummer

### <a name="format"></a>Formatér

ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_croatia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_croatia_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_croatia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_croatia_eu_passport_number` fra eller.

```xml
      <!-- Croatia Passport Number -->
      <Entity id="7d7a729d-32d8-4204-8d01-d5e6a6c25581" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_croatia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_croatia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Kroatiens personlige identifikationsnummer (OIB)

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

11 cifre:
- 10 cifre
- det sidste ciffer er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_croatia_oib_number, der svarer til mønsteret.
- Der er fundet Keywords_croatia_eu_tax_file_number nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_croatia_oib_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
      <!-- Croatia Personal Identification (OIB) Number -->
      <Entity id="31983b6d-db95-4eb2-a630-b44bd091968d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_croatia_oib_number" />
          <Match idRef="Keywords_croatia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_croatia_oib_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj graðana
- masternummer for borgere
- nacionalni identifikacijski broj
- nationalt id-nummer
- oib #
- oib
- osobna iskaznica
- osobni-id
- osobni identifikacijski broj
- personligt id-nummer
- porezni broj
- porezni identifikacijski broj
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="croatia-physical-addresses"></a>Kroatiens fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Kroatien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="cyprus-drivers-license-number"></a>Kørekortnummer til Cypern

### <a name="format"></a>Formatér

12 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

12 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_cyprus_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_cyprus_eu_driver's_license_number` fra eller.

```xml
      <!-- Cyprus Driver's License Number -->
      <Entity id="356fa104-f9ac-4aff-a0e4-2e6e65ea06c4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_cyprus_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver ikke s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης


## <a name="cyprus-identity-card"></a>Identitetskort for Cypern

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_cyprus_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_cyprus_eu_national_id_card` nøgleord fra.

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- id-kortnummer
- identitetskortnummer
- kimlik karti
- nationalt id-nummer
- personligt id-nummer
- ταυτοτητασ


## <a name="cyprus-passport-number"></a>Cyperns pasnummer

### <a name="format"></a>Formatér

et bogstav efterfulgt af 6-8 cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

et bogstav efterfulgt af seks til otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_cyprus_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_cyprus_eu_passport_number` fra eller.
- Det regulære `Regex_cyprus_eu_passport_date` udtryk finder dato i formatet DD/MM/YYY, eller der er fundet et nøgleord `Keywords_cyprus_eu_passport_date` fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_cyprus_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_cyprus_eu_passport_number` fra eller.

```xml
      <!-- Cyprus Passport Number -->
      <Entity id="9193e2e8-7f8c-43c1-a274-ac40d651936f" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_cyprus_eu_passport_date" />
            <Match idRef="Keywords_cyprus_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_cyprus_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- pasaportu
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pasaport Kimliíi
- pasaport numarası
- Pasaport no.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- udløber den
- udstedt den


## <a name="cyprus-physical-addresses"></a>Fysiske adresser i Cypern

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Cypern. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem

## <a name="cyprus-tax-identification-number"></a>Cyperns skatte-id
Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

otte cifre og et bogstav i det angivne mønster

### <a name="pattern"></a>Mønster

otte cifre og ét bogstav:

- et "0" eller "9"
- syv cifre
- et bogstav (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_cyprus_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_cyprus_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_cyprus_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Cyprus Tax Identification Number -->
      <Entity id="40e64bd9-55f3-4a09-9bd6-1db18dced9dd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
          <Match idRef="Keywords_cyprus_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_cyprus_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- moms-id
- moms-id-kode
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tic #
- tic
- tin-id
- tinnr
- tin #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού


## <a name="czech-drivers-license-number"></a>Tjekkisk kørekortnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

otte bogstaver og cifre:

- bogstavet "E" (der er ikke tale om store og små bogstaver)
- et bogstav
- et mellemrum (valgfrit)
- seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_czech_republic_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_czech_republic_eu_driver's_license_number` fra eller.

```xml
      <Entity id="86b40d3b-d8ea-4c36-aab0-ef9416a6769c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_czech_republic_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver ikke s_license_number

- úidičskú prúkaz
- čidičské príkač
- číslo čidičského príkazu
- čísla čidičskčch príkazč


## <a name="czech-passport-number"></a>Tjekkisk pasnummer

### <a name="format"></a>Formatér

otte cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

otte cifre uden mellemrum eller separatortegn

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_czech_republic_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_czech_republic_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_czech_republic_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_czech_republic_eu_passport_number` fra eller.

```xml
      <!-- Czech Republic Passport Number -->
      <Entity id="7bcd8ce8-5e92-4bbe-bc92-fa669f0369fa" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_czech_republic_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_czech_republic_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cesí pas
- číslo pasu
- cesí pasu
- passeport no
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="czech-personal-identity-number"></a>Tjekkisk personligt identitetsnummer

### <a name="format"></a>Formatér

ni cifre med valgfri skråstreg (gammelt format) 10 cifre med valgfri skråstreg (nyt format)

### <a name="pattern"></a>Mønster

ni cifre (gammelt format):
- Seks cifre, der repræsenterer fødselsdato
- en valgfri skråstreg
- Tre cifre

10 cifre (nyt format):
- Seks cifre, der repræsenterer fødselsdato
- en valgfri skråstreg
- fire cifre, hvor sidste ciffer er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder Func_czech_id_card, der svarer til mønsteret.
- Der er fundet Keyword_czech_id_card nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder Func_czech_id_card_new_format, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Czech Personal Identity Number -->
      <!-- Czech Personal Identity Number -->
      <Entity id="60c0725a-4eb6-455b-9dda-05d8a7396497" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_czech_id_card" />
          <Match idRef="Keyword_czech_id_card" />
        </Pattern>
        <Version minEngineVersion="15.20.3000.000">
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Func_czech_id_card_new_format" />
          </Pattern>
        </Version>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- fødselsnummer
- tjekkisk id
- czechidno #
- daňové číslo
- identifikační číslo
- identitet nej
- identitetsnummer
- identityno #
- identityno
- forsikringsnummer
- nationalt id-nummer
- nationalnumber #
- nationalt nummer
- osobní číslo
- personalidnumber #
- personligt id-nummer
- personligt id-nummer
- personligt nummer
- pid #
- pid
- pojištšní číslo
- rč
- rodne cislo
- rodné číslo
- ssn
- ssn #
- CPR-nummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- entydigt id-nummer


## <a name="czech-republic-physical-addresses"></a>Fysiske adresser for Tjekkiet

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Tjekkiet. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem

## <a name="denmark-drivers-license-number"></a>Danmark kørekortnummer

### <a name="format"></a>Formatér

Otte cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_denmark_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_denmark_eu_driver's_license_number` fra eller.

```xml
      <!-- Denmark Driver's License Number -->
      <Entity id="98a95812-6203-451a-a220-d39870ebef0e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_denmark_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver ikke s_license_number

- kørekort
- kørekortnummer


## <a name="denmark-passport-number"></a>Danmark pasnummer

### <a name="format"></a>Formatér

ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_denmark_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_denmark_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date2` udtryk finder dato i formatet DD MM-JY, eller der findes et nøgleord `Keywords_eu_passport_date` fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_denmark_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_denmark_eu_passport_number` fra eller.

```xml
      <!-- Denmark Passport Number -->
      <Entity id="25e8c47e-e6fe-4884-a211-74898f8c0196" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date2" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_denmark_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_denmark_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="denmark-personal-identification-number"></a>Danmark personligt id-nummer

### <a name="format"></a>Formatér

10 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

10 cifre:
- seks cifre i formatet DDMMYY, som er fødselsdatoen
- et valgfrit mellemrum eller en bindestreg
- fire cifre, hvor det sidste ciffer er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Func_denmark_eu_tax_file_number, der svarer til mønsteret.
- Der er fundet Keyword_denmark_id nøgleord.
- Kontrolsummet overføres.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Func_denmark_eu_tax_file_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Denmark Personal Identification Number -->
    <!-- Denmark Personal Identification Number -->
      <Entity id="6c4f2fef-56e1-4c00-8093-88d7a01cf460" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
          <Match idRef="Keyword_denmark_id" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_denmark_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- cpr
- cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- tilstandskort
- health insurance card number
- health insurance number
- id-nummer
- identifikationsnummer
- identifikationsnummer #
- identitetsnummer
- krankenkassennummer
- nationalid #
- nationalnumber #
- nationalt nummer
- personalidnumber #
- personalidentityno #
- personligt id-nummer
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesikringskort
- ssn
- ssn #
- skat id
- skat kode
- skat nummer
- skattenummer
- CPR-nummer
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- inddr ind
- inddnr.
- momskode
- rejse health insurance card
- uniqueidentityno #
- momsnummer
- momsregistreringsnummer
- moms-id
- moms-id
- taxd #
- momsnummer #
- momsnr.
- taxno #
- momsnummer
- momsidentifikation
- tin #
- taxdno #
- kørenummer #
- momsnr. #
- tin-id
- tinnr
- cpr.nr
- cprnr
- cprnummer
- personnr
- personregister
- sygesikringsbevis
- sygesikringsbevisnr
- sygesikringsbevisnummer
- sygesikringskort
- sygesikringskortnr
- sygesikringskortnummer
- sygesikringsnr
- inddr ind/


## <a name="denmark-physical-addresses"></a>Fysiske adresser i Danmark

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Danmark. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="diseases"></a>Værdier

Denne ubundede navngivne enhed registrerer tekst, der svarer til navne på navne, der kaldes *navne, f.eks*. Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="drug-enforcement-agency-dea-number"></a>Håndhævelsesorgan (DEA)

### <a name="format"></a>Formatér

To bogstaver efterfulgt af syv cifre

### <a name="pattern"></a>Mønster

Mønsteret skal omfatte alle følgende:
- et bogstav (der er ikke tale om store og små bogstaver) fra dette sæt af mulige bogstaver: abcdefghjklmnprstux, som er en kode for ord
- et bogstav (der er ikke tale om store og små bogstaver), som er det første bogstav i efternavnet eller cifret '9'
- syv cifre, hvoraf det sidste er kontrolcifret

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_dea_number, der svarer til mønsteret.
- Der er fundet et `Keyword_dea_number` nøgleord fra
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_dea_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- dea
- dea #
- håndhævelsesadministration af udskik
- enforcement agency


## <a name="estonia-drivers-license-number"></a>Estlands kørekortnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

to bogstaver og seks cifre:

- bogstaverne "ET" (der er ikke tale om store og små bogstaver)
- seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_estonia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_estonia_eu_driver's_license_number` fra eller.

```xml
      <!-- Estonia Driver's License Number -->
      <Entity id="51da8171-da70-4cc1-9d65-055a59ca4f83" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_estonia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver ikke s_license_number

- permis de conduire
- juhilubade numbrid
- juhiloa number
- juhiluba


## <a name="estonia-passport-number"></a>Estlands pasnummer

### <a name="format"></a>Formatér

et bogstav efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

et bogstav efterfulgt af syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_estonia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_estonia_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_estonia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_estonia_eu_passport_number` fra eller.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="estonia-personal-identification-code"></a>Estlands personlige identifikationskode

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

11 cifre:

- et ciffer, der svarer til køn og fødselstal (ulige hankøn, lige antal kvinder; 1-2: 19. århundrede; 3-4: 20. århundrede; 5-6: 21st århundrede)
- seks cifre, der svarer til fødselsdato (YYMMDD)
- Tre cifre, der svarer til et serienummer, der adskiller personer, der fødes på samme dato
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_estonia_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_estonia_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_estonia_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- ik
- isikukood #
- isikukood
- maksu-id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- nationalt id-nummer
- nationalt nummer
- personlig kode
- personligt id-nummer
- personlig identifikationskode
- personligt id-nummer
- personalidnumber #
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="estonia-physical-addresses"></a>Fysiske adresser i Estland

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Estland. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="eu-debit-card-number"></a>EU-debetkortnummer

### <a name="format"></a>Formatér

16 cifre

### <a name="pattern"></a>Mønster

Komplekst og robust mønster

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_eu_debit_card, der svarer til mønsteret.
- Mindst ét af følgende gælder:
    - Der er fundet Keyword_eu_debit_card nøgleord.
    - Der er fundet Keyword_card_terms_dict nøgleord.
    - Der er fundet Keyword_card_security_terms_dict nøgleord.
    - Der er fundet Keyword_card_expiration_terms_dict nøgleord.
    - Funktionen finder Func_expiration_date en dato i det rigtige datoformat.
- Kontrolsummet overføres.

```xml
    <!-- EU Debit Card Number -->
    <Entity id="0e9b3178-9678-47dd-a509-37222ca96b42" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_eu_debit_card" />
        <Any minMatches="1">
          <Match idRef="Keyword_eu_debit_card" />
          <Match idRef="Keyword_card_terms_dict" />
          <Match idRef="Keyword_card_security_terms_dict" />
          <Match idRef="Keyword_card_expiration_terms_dict" />
          <Match idRef="Func_expiration_date" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- kontonummer
- kortnummer
- kortnr.
- sikkerhedsnummer
- cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- kontonr
- kontonr
- kontonr
- american express
- americanexpress
- americano afkod
- amex
- hæve kort
- hæve kort
- atm kaart
- hævekort
- hævekort
- atmkaart
- atmkaarten
- bancontact
- bankkort
- bankkaart
- kortindehaver
- kortindehavere
- kortnr.
- kortnummer
- kortnumre
- korttype
- cardano numerico
- kortholder
- kortholdere
- kortnummer
- kortnumre
- carta carta
- carta credito
- carta di credito
- cartao de credito
- cartao de crédito
- cartao de debito
- cartao de débito
- carte bancaire
- carte blanche
- carte bleue
- carte de credit
- carte de crédit
- carte di credito
- carteblanche
- cartão de credito
- cartão de crédito
- cartão de debito
- cartão de débito
- cb
- ccn
- check kort
- check kort
- checkkort
- checkkort
- checkskaart
- cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- kreditkort
- kreditkort
- kreditkort
- kreditkort
- debetkaart
- debetkaarten
- debetkort
- debetkort
- debetkort
- debetkort
- debito automatico
- diners club
- dinersspiste
- find
- discover card
- discover cards
- discovercard
- discovercards
- débito automático
- edc
- eigentümername
- europæisk debetkort
- hoofdkaart
- hoofdkaarten
- i viglasset
- japanese card bureau
- japanse kaartdienst
- jcb
- kaart
- kaart num
- kaartaantal
- kaartaantallen
- kaarthouder
- kaarthouders
- karte
- karteninhaber
- karteninhabers
- kartennr
- kartennummer
- kreditkarte
- kreditkarten-nummer
- kreditkarteninhaber
- kreditkarteninstitut
- kreditkartennummer
- kreditkartentyp
- maestro
- master card
- master cards
- mastercard
- mastercards
- mc
- mister cash
- n carta
- carta
- no de tarjeta
- no do cartao
- no do cartão
- Nej. de tarjeta
- Nej. do cartao
- Nej. do cartão
- nr carta
- nr. carta
- numeri di scheda
- numero carta
- numero de cartao
- numero de carte
- numero de cartão
- numero de tarjeta
- numero della carta
- numero di carta
- numero di scheda
- numero do cartao
- numero do cartão
- numéro de carte
- nº carta
- nº de carte
- nº de la carte
- nº de tarjeta
- nº do cartao
- nº do cartão
- nº. do cartão
- número de cartao
- número de cartão
- número de tarjeta
- número do cartao
- scheda dell'assegno
- scheda dell'atmosfera
- scheda dell'atmosfera
- scheda della banca
- scheda di controllo
- scheda di debito
- scheda matrice
- schede dell'atmosfera
- schede di controllo
- schede di debito
- schede matrici
- scoprono la scheda
- scoprono le schede
- solo
- supporti di scheda
- supporto di scheda
- skift
- tarjeta atm
- tarjeta credito
- tarjeta de atm
- tarjeta de credito
- tarjeta de debito
- tarjeta debito
- tarjeta no
- tarjetahabiente
- tipo della scheda
- ufficio giapponese della
- scheda
- v pay
- v-pay
- visa
- visa plus
- visa electron
- visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- kort-id
- kortbekræftelse
- cardi la verifica
- cid
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- cod. seg
- cod. seguranca
- cod. segurança
- cod. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- cryptogram
- cryptogramme
- cv2
- cvc
- cvc2
- cvn
- cvv
- cvv2
- cód seguranca
- cód segurança
- cód. seguranca
- cód. segurança
- código
- código de seguranca
- código de segurança
- de kaart controle
- geeft nr uit
- udgavenr.
- udstedelsesnummer
- kaartidentificatienummer
- kreditkartenprufnummer
- kreditkartenprüfnummer
- kwestieaantal
- Nej. dell'edizione
- Nej. di sicurezza
- numero de securite
- numero de verificacao
- numero dell'edizione
- numero di identificazione della
- scheda
- numero di sicurezza
- numero van veiligheid
- numéro de sécurité
- nº autorizzazione
- número de verificação
- perno il il ilco
- fastgør blok
- prufziffer
- prüfziffer
- sikkerhedskode
- sikkerhedsnr.
- sikkerhedsnummer
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
- veiligheid nr
- veiligheidsaantal
- veiligheidscode
- veiligheidsnummer
- verfalldatum

#### <a name="keyword_card_expiration_terms_dict"></a>Keyword_card_expiration_terms_dict

- ablauf
- data de expiracao
- data de expiração
- data del exp
- data di exp
- data di scadenza
- data em que expira
- data scad
- data scadenza
- date de validité
- datum afloop
- datum van exp
- de afloop
- espira
- espira
- udl.dato
- udk datum
- udløb
- udløber
- udløber
- udløb
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- valable
- validade
- valido hasta
- valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta


## <a name="eu-drivers-license-number"></a>EU-kørekortnummer

Disse enheder findes i EU-kørekortnummeret og er følsomme oplysningstyper.

- [Østrig](#austria-drivers-license-number)
- [Belgien](#belgium-drivers-license-number)
- [Bulgarien](#bulgaria-drivers-license-number)
- [Kroatien](#croatia-drivers-license-number)
- [Cypern](#cyprus-drivers-license-number)
- [Czech](#czech-drivers-license-number)
- [Danmark](#denmark-drivers-license-number)
- [Estland](#estonia-drivers-license-number)
- [Finland](#finland-drivers-license-number)
- [Frankrig](#france-drivers-license-number)
- [Tyskland](#germany-drivers-license-number)
- [Grækenland](#greece-drivers-license-number)
- [Ungarn](#hungary-drivers-license-number)
- [Irland](#ireland-drivers-license-number)
- [Italien](#italy-drivers-license-number)
- [Letland](#latvia-drivers-license-number)
- [Litauen](#lithuania-drivers-license-number)
- [Luxemburg](#luxemburg-drivers-license-number)
- [Malta](#malta-drivers-license-number)
- [Holland](#netherlands-drivers-license-number)
- [Polen](#poland-drivers-license-number)
- [Portugal](#portugal-drivers-license-number)
- [Rumænien](#romania-drivers-license-number)
- [Slovakiet](#slovakia-drivers-license-number)
- [Slovenien](#slovenia-drivers-license-number)
- [Spanien](#spain-drivers-license-number)
- [Sverige](#sweden-drivers-license-number)
- [Storbritannien](#uk-drivers-license-number)


## <a name="eu-national-identification-number"></a>EU-national identifikationsnummer

Disse enheder findes i EU's nationale identifikationsnummer og er følsomme oplysningstyper.

- [Østrig](#austria-identity-card)
- [Belgien](#belgium-national-number)
- [Bulgarien](#bulgaria-uniform-civil-number)
- [Kroatien](#croatia-identity-card-number)
- [Cypern](#cyprus-identity-card)
- [Czech](#czech-personal-identity-number)
- [Danmark](#denmark-personal-identification-number)
- [Estland](#estonia-personal-identification-code)
- [Finland](#finland-national-id)
- [Frankrig](#france-national-id-card-cni)
- [Tyskland](#germany-identity-card-number)
- [Grækenland](#greece-national-id-card)
- [Ungarn](#hungary-personal-identification-number)
- [Irland](#ireland-personal-public-service-pps-number)
- [Italien](#italy-fiscal-code)
- [Letland](#latvia-personal-code)
- [Litauen](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-natural-persons)
- [Malta](#malta-identity-card-number)
- [Holland](#netherlands-citizens-service-bsn-number)
- [Polen](#poland-national-id-pesel)
- [Portugal](#portugal-citizen-card-number)
- [Rumænien](#romania-personal-numeric-code-cnp)
- [Slovakiet](#slovakia-personal-number)
- [Slovenien](#slovenia-unique-master-citizen-number)
- [Spanien](#spain-dni)
- [Storbritannien](#uk-national-insurance-number-nino)


## <a name="eu-passport-number"></a>EU-pasnummer

Disse enheder er i EU-pasnummeret og er følsomme oplysningstyper. Disse enheder findes i EU-pasnummerpakken.

- [Østrig](#austria-passport-number)
- [Belgien](#belgium-passport-number)
- [Bulgarien](#bulgaria-passport-number)
- [Kroatien](#croatia-passport-number)
- [Cypern](#cyprus-passport-number)
- [Czech](#czech-passport-number)
- [Danmark](#denmark-passport-number)
- [Estland](#estonia-passport-number)
- [Finland](#finland-passport-number)
- [Frankrig](#france-passport-number)
- [Tyskland](#germany-passport-number)
- [Grækenland](#greece-passport-number)
- [Ungarn](#hungary-passport-number)
- [Irland](#ireland-passport-number)
- [Italien](#italy-passport-number)
- [Letland](#latvia-passport-number)
- [Litauen](#lithuania-passport-number)
- [Luxemburg](#luxemburg-passport-number)
- [Malta](#malta-passport-number)
- [Holland](#netherlands-passport-number)
- [Polen](#poland-passport-number)
- [Portugal](#portugal-passport-number)
- [Rumænien](#romania-passport-number)
- [Slovakiet](#slovakia-passport-number)
- [Slovenien](#slovenia-passport-number)
- [Spanien](#spain-passport-number)
- [Sverige](#sweden-passport-number)
- [USA/Storbritannien pasnummer](#usuk-passport-number)


## <a name="eu-social-security-number-or-equivalent-identification"></a>EU-nummer til personnummer eller tilsvarende identifikation

Dette er de enheder, der findes i EU's CPR-nummer eller tilsvarende identifikation, og som er følsomme oplysningstyper.

- [Østrig](#austria-social-security-number)
- [Belgien](#belgium-national-number)
- [Kroatien](#croatia-personal-identification-oib-number)
- [Czech](#czech-personal-identity-number)
- [Danmark](#denmark-personal-identification-number)
- [Finland](#finland-national-id)
- [Frankrig](#france-social-security-number-insee)
- [Tyskland](#germany-identity-card-number)
- [Grækenland](#greece-national-id-card)
- [Ungarn](#hungary-social-security-number-taj)
- [Portugal](#portugal-citizen-card-number)
- [Spanien](#spain-social-security-number-ssn)
- [Sverige](#sweden-national-id)


## <a name="eu-tax-identification-number"></a>EU-skatte-id

Disse enheder findes i følsom informationstypen EU-skatteidentifikationsnummer.

- [Østrig](#austria-tax-identification-number)
- [Belgien](#belgium-national-number)
- [Bulgarien](#bulgaria-uniform-civil-number)
- [Kroatien](#croatia-identity-card-number)
- [Cypern](#cyprus-tax-identification-number)
- [Czech](#czech-personal-identity-number)
- [Danmark](#denmark-personal-identification-number)
- [Estland](#estonia-personal-identification-code)
- [Finland](#finland-national-id)
- [Frankrig](#france-tax-identification-number)
- [Tyskland](#germany-tax-identification-number)
- [Grækenland](#greece-tax-identification-number)
- [Ungarn](#hungary-tax-identification-number)
- [Irland](#ireland-personal-public-service-pps-number)
- [Italien](#italy-fiscal-code)
- [Letland](#latvia-personal-code)
- [Litauen](#lithuania-personal-code)
- [Luxemburg](#luxemburg-national-identification-number-non-natural-persons)
- [Malta](#malta-tax-identification-number)
- [Holland](#netherlands-tax-identification-number)
- [Polen](#poland-tax-identification-number)
- [Portugal](#portugal-tax-identification-number)
- [Rumænien](#romania-personal-numeric-code-cnp)
- [Slovakiet](#slovakia-personal-number)
- [Slovenien](#slovenia-tax-identification-number)
- [Spanien](#spain-tax-identification-number)
- [Sverige](#sweden-tax-identification-number)
- [Storbritannien](#uk-unique-taxpayer-reference-number)


## <a name="finland-drivers-license-number"></a>Finlands kørekortnummer

### <a name="format"></a>Formatér

10 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

10 cifre, der indeholder en bindestreg:

- seks cifre
- en bindestreg
- Tre cifre
- et ciffer eller bogstav

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_finland_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_finland_eu_driver's_license_number` fra eller.

```xml
      <!-- Finland Driver's License Number -->
      <Entity id="bb3b27a3-79bd-4ac4-81a7-f9fca3c7d1a7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_finland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver ikke s_license_number

- ajokortti
- permis de conduire
- ajokortin numero
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot


## <a name="finland-european-health-insurance-number"></a>Finland European Health Insurance Number

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

20-cifret tal

### <a name="pattern"></a>Mønster

20-cifret tal:

- 10 cifre – 8024680246
- et valgfrit mellemrum eller en bindestreg
- 10 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex-Regex_Finland_European_Health_Insurance_Number finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_Finland_European_Health_Insurance_Number nøgleord.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- emoral #
- emoral
- Finlandehicnumber #
- finska sjukförsäkringskort
- tilstandskort
- sundhedsforsikringskort
- health insurance number
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumlar
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti


## <a name="finland-national-id"></a>Finlands nationale id

### <a name="format"></a>Formatér

seks cifre plus et tegn, der angiver et århundrede plus tre cifre plus et kontrolcifre

### <a name="pattern"></a>Mønster

Mønsteret skal omfatte alle følgende:
- seks cifre i formatet DDMMYY, som er en fødselsdato
- århundredemarkør (enten '-', '+' eller 'a')
- trecifret personligt identifikationsnummer
- et ciffer eller bogstav (der ikke kan skrives mellem store og små bogstaver), som er et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- funktionen finder Func_finnish_national_id indhold, der svarer til mønsteret
- der er fundet et nøgleord Keyword_finnish_national_id ord
- kontrolsummet overføres

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- funktionen finder Func_finnish_national_id indhold, der svarer til mønsteret
- kontrolsummet overføres

```xml
      <!-- Finnish National ID-->
      <Entity id="338FD995-4CB5-4F87-AD35-79BD1DD926C1" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_finnish_national_id" />
          <Match idRef="Keyword_finnish_national_id" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_finnish_national_id" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumhorn #
- henkilötunnusnumhorn
- hetu
- id nej
- id-nummer
- id-nummer
- identiteetti numero
- identitetsnummer
- id-nummer
- kansallinen henkilötunnus
- kansallisen henkilökortin
- nationalt id-kort
- nationalt id.nr.
- personligt id
- personlig identitetskode
- personalidnumber #
- personbeteckning
- personnummer
- CPR-nummer
- sosiaaliturvatunnus
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- tunnistenumjusteret
- tunnus numero
- tunnusluku
- tunnusnumjusteret
- verokortti
- veronum kryptor
- verotunniste
- verotunnus


## <a name="finland-passport-number"></a>Finlands pasnummer

Denne enhed er tilgængelig i typen af følsomme oplysninger om EU-pasnummer og er tilgængelig som et enkeltstående objekt af typen af følsomme oplysninger.

### <a name="format"></a>Formatér
kombination af ni bogstaver og cifre

### <a name="pattern"></a>Mønster
kombination af ni bogstaver og cifre:
- To bogstaver (der er ikke tale om store og små bogstaver)
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_finland_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keyword_finland_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_finland_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keyword_finland_passport_number` fra eller.

```xml
      <!-- Finland Passport Number -->
      <Entity id="d1685ac3-1d3a-40f8-8198-32ef5669c7a5" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_finland_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_finland_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- passin numero. #
- passin numero #
- passin numero.
- passi #
- passi-nummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="finland-physical-addresses"></a>Finlands fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Finland. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="france-drivers-license-number"></a>Frankrigs kørekortnummer

Denne enhed er tilgængelig i typen af følsomme oplysninger om EU-kørekortnummer og er tilgængelig som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

12 cifre

### <a name="pattern"></a>Mønster

12 cifre med validering for at få rabat på ensartede mønstre som f.eks. franske telefonnumre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- funktionen finder Func_french_drivers_license, der svarer til mønsteret.
- der er fundet Keyword_french_drivers_license nøgleord.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer
- permis de conduire
- licensnummer
- licensnummer
- licensnumre
- licensnumre
- numéros de licence


## <a name="france-health-insurance-number"></a>Frankrigs sundhedsforsikringsnummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

21-cifret tal

### <a name="pattern"></a>Mønster

21-cifret tal:

- 10 cifre
- et valgfrit mellemrum
- 10 cifre
- et valgfrit mellemrum
- et ciffer


### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- regex-Regex_France_Health_Insurance_Number finder indhold, der svarer til mønsteret.
- der er fundet Keyword_France_Health_Insurance_Number nøgleord.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- forsikringskort
- carte vitale
- carte d'assuré social


## <a name="france-national-id-card-cni"></a>Frankrigs nationale id-kort (CNI)

### <a name="format"></a>Formatér

12 cifre

### <a name="pattern"></a>Mønster

12 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_france_cni, der svarer til mønsteret.
- Der er fundet Keywords_france_eu_national_id_card nøgleord.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- kortnummer
- carte nationale d'identité
- carte nationale d'idenite no
- cni #
- cni
- compte bancaire
- nationalt id-nummer
- national identitet
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale


## <a name="france-passport-number"></a>Frankrigs pasnummer

Denne enhed er tilgængelig i typen af følsomme oplysninger om EU-pasnummer. Den fås også som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

ni cifre og bogstaver

### <a name="pattern"></a>Mønster

ni cifre og bogstaver:
- to cifre
- To bogstaver (der er ikke tale om store og små bogstaver)
- fem cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_fr_passport` indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keywords_france_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date3` udtryk finder dato i formatet DD MMYYY, eller der bliver fundet et nøgleord `Keywords_eu_passport_date` fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_fr_passport` indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keywords_france_eu_passport_number` fra eller.


```xml
    <!-- France Passport Number -->
    <Entity id="3008b884-8c8c-4cd8-a289-99f34fc7ff5d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_fr_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_france_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passeport français
- passeport livre
- passeport carte
- numéro passeport
- passeport n°
- n° du passeport
- n° passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="france-physical-addresses"></a>Fysiske adresser i Frankrig

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Frankrig. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="france-social-security-number-insee"></a>Frankrigs CPR-nummer (INSEE)

### <a name="format"></a>Formatér

15 cifre

### <a name="pattern"></a>Mønster

Skal matche et af to mønstre:
- 13 cifre efterfulgt af et mellemrum efterfulgt af to cifre<br/>
eller
- 15 fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_french_insee` indhold, der svarer til mønsteret.
- Der er fundet Keyword_fr_insee nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen findes Func_french_insee eller Func_fr_insee finder indhold, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
    <!-- France INSEE -->
    <Entity id="71f62b97-efe0-4aa1-aa49-e14de253619d" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_insee" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_fr_insee" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_french_insee" />
        <Match idRef="Keyword_fr_insee" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d'identité nationale
- insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- nationalt id
- national identifikation
- no d'identité
- Nej. d'identité
- numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- no d'identite
- Nej. d'identite
- ssn
- ssn #
- sécurité sociale
- securité sociale
- securite social
- cpr-nummer
- CPR-nummer
- CPR-kode
- cpr-nummer


## <a name="france-tax-identification-number"></a>Frankrigs skatte-id

### <a name="format"></a>Formatér

13 cifre

### <a name="pattern"></a>Mønster

13 cifre

- Et ciffer, der skal være 0, 1, 2 eller 3
- Et ciffer
- Et mellemrum (valgfrit)
- To cifre
- Et mellemrum (valgfrit)
- Tre cifre
- Et mellemrum (valgfrit)
- Tre cifre
- Et mellemrum (valgfrit)
- Tre kontrolcifre


### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_france_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_france_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_france_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- France Tax Identification Number (numéro SPI.) -->
      <Entity id="ed59e77e-171d-442c-9ec1-88e2ebcb5b0a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Match idRef="Keywords_france_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_france_eu_telephone_number" />
            <Match idRef="Keywords_france_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="france-value-added-tax-number"></a>Momsnummer tilføjet i Frankrig

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13 tegn alfanumeriske mønster

### <a name="pattern"></a>Mønster

13 tegn alfanumeriske mønster:

- To bogstaver - FR (der kan ikkeføles store bogstaver)
- et valgfrit mellemrum eller en bindestreg
- to bogstaver eller tal
- et valgfrit mellemrum, en prik, en bindestreg eller et komma
- Tre cifre
- et valgfrit mellemrum, en prik, en bindestreg eller et komma
- Tre cifre
- et valgfrit mellemrum, en prik, en bindestreg eller et komma
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_france_value_added_tax_number, der svarer til mønsteret.
- Der er fundet Keywords_france_value_added_tax_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_france_value_added_tax_number, der svarer til mønsteret.

```xml
      <!-- France Value Added Tax Number -->
      <Entity id="949121e6-ad9f-4379-8731-710342baea78" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_france_value_added_tax_number" />
          <Match idRef="Keywords_france_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_france_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- momsnummer
- momsnr.
- moms #
- moms
- siren-identifikation ingen numéro d'identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification siren


## <a name="generic-medication-names"></a>Generiske medicinnavne

Denne ubundede navngivne enhed registrerer navne på generisk medicin, f.eks *acetophophen*. Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="germany-drivers-license-number"></a>Tysklands kørekortnummer

Denne følsomme oplysningstype er inkluderet i den følsomme oplysningstype EU-kørekortnummer. Den fås også som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

kombination af 11 cifre og bogstaver

### <a name="pattern"></a>Mønster

11 cifre og bogstaver (der er ikke store bogstaver):
- et ciffer eller bogstav
- to cifre
- seks cifre eller bogstaver
- et ciffer
- et ciffer eller bogstav

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_german_drivers_license, der svarer til mønsteret.
- Der er fundet Keyword_german_drivers_license_number nøgleord.
- Kontrolsummet overføres.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_german_drivers_license_number"></a>Keyword_german_drivers_license_number

- ausstellungsdatum
- ausstellungsort
- ausstellende behöde
- ausstellende behorde
- ausstellende behoerde
- führerschein
- fuhrerschein
- fuehrerschein
- führerscheinnummer
- fuhrerscheinnummer
- fuehrerscheinnummer
- führerschein- 
- fuhrerschein- 
- fuehrerschein- 
- führerscheinnummernr
- fuhrerscheinnummernr
- fuehrerscheinnummernr
- führerscheinnummerklasse
- fuhrerscheinnummerklasse
- fuehrerscheinnummerklasse
- nr-führerschein
- nr-fuhrerschein
- nr-fuehrerschein
- no-führerschein
- no-fuhrerschein
- no-fuehrerschein
- n-führerschein
- n-fuhrerschein
- n-fuehrerschein
- permis de conduire
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dlno


## <a name="germany-identity-card-number"></a>Tysklands identitetskortnummer

### <a name="format"></a>Formatér

siden 1. november 2010: Ni til 11 bogstaver og cifre

fra 1. april 1987 til 31. oktober 2010: 10 cifre

### <a name="pattern"></a>Mønster

siden 1. november 2010: 9 til 11 tegn alfanumeriske mønster
- en L, M, N, P, R, T, V, W, X, Y (der kan ikke tales om store og små bogstaver)
- otte cifre eller bogstaver i C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y og Z (der kan ikke tales om store og små bogstaver)
- valgfrit kontrolcifre
- Valgfrit d/d

fra d. 1. april 1987 til d. 31. oktober 2010:
- 10 cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_german_id_card_with_check` indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_germany_id_card` nøgleord fra.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære `Regex_germany_id_card` udtryk finder indhold, der svarer til mønsteret (9 tegn uden et kontrolleret ciffer udstedt før 2010 eller 10 cifres mønster udstedt posy 2010).
- Der er fundet Keyword_germany_id_card nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_german_id_card_with_check` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.


```xml
      <!-- Germany Identity Card Number -->
      <Entity id="e577372f-c42e-47a0-9d85-bebed1c237d4" patternsProximity="300" recommendedConfidence="75"> 
        <Pattern confidenceLevel="75">
         <IdMatch idRef="Regex_germany_id_card" /> 
         <Match idRef="Keyword_germany_id_card" /> 
        </Pattern>
        <Version minEngineVersion="15.20.4545.000"> 
          <Pattern confidenceLevel="85">
           <IdMatch idRef="Func_german_id_card_with_check" />
            <Match idRef="Keyword_germany_id_card" /> 
          </Pattern> 
          <Pattern confidenceLevel="65">
           <IdMatch idRef="Func_german_id_card_with_check" /> 
          </Pattern> 
        </Version>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- identifikation
- identifikation
- identifizierungsnummer
- identitetskort
- identitetsnummer
- id-nummer
- personligt id
- personalausweis
- persöniche id nummer
- persöniche identifikationsnummer
- persöniche-id-nummer


## <a name="germany-passport-number"></a>Tysklands pasnummer

### <a name="format"></a>Formatér

9 til 11 tegn

### <a name="pattern"></a>Mønster

- et bogstav i C, F, G, H, J, K (der kan ikke tales om store og små bogstaver)
- otte cifre eller bogstaver i C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y og Z (der kan ikke tales om store og små bogstaver)
- valgfrit kontrolcifre
- Valgfrit d/d

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_german_passport_checksum` indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_german_passport` nøgleord `Keywords_eu_passport_number_common` fra eller.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_german_passport` indhold, der svarer til mønsteret med ni tegn (uden kontrolcifre og valgfrit d/D).
- Der er fundet et `Keyword_german_passport` nøgleord `Keywords_eu_passport_number_common` fra eller.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_german_passport_checksum` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
    <!-- German Passport Number -->
    <Entity id="2e3da144-d42b-47ed-b123-fbf78604e52c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_passport" />
        <Any minMatches="1">
          <Match idRef="Keyword_german_passport" />
          <Match idRef="Keywords_eu_passport_number_common" />
        </Any>
      </Pattern>
      <Version minEngineVersion="15.20.4570.0">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_german_passport_checksum" />
          <Any minMatches="1">
            <Match idRef="Keyword_german_passport" />
            <Match idRef="Keywords_eu_passport_number_common" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_german_passport_checksum" />
        </Pattern>
      </Version>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeport no.
- passeport no

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre


## <a name="germany-physical-addresses"></a>Fysiske adresser i Tyskland

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Tyskland. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="germany-tax-identification-number"></a>Tysklands skatte-id

### <a name="format"></a>Formatér

11 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

11 cifre

- To cifre
- Et valgfrit mellemrum
- Tre cifre
- Et valgfrit mellemrum
- Tre cifre
- Et valgfrit mellemrum
- To cifre
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_germany_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_germany_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_germany_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Germany Tax Identification Number -->
      <Entity id="43316a89-9880-40cf-b980-04bc7eefcec5" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
          <Match idRef="Keywords_germany_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- steuer-id
- steueridentifikationsnummer
- steuernummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- zinn #
- zinn
- zinnnummer


## <a name="germany-value-added-tax-number"></a>Momsnummer for moms i Tyskland

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11-tegns alfanumeriske mønster

### <a name="pattern"></a>Mønster

11-tegns alfanumeriske mønster:

- et bogstav D eller d
- et bogstav E eller e
- et valgfrit mellemrum
- Tre cifre
- et valgfrit mellemrum eller komma
- Tre cifre
- et valgfrit mellemrum eller komma
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_germany_value_added_tax_number, der svarer til mønsteret.
- Der er fundet Keywords_germany_value_added_tax_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_germany_value_added_tax_number, der svarer til mønsteret.

```xml
      <!-- Germany Value Added Tax Number -->
      <Entity id="db177eb2-8811-4842-bffc-128c14aa219f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
          <Match idRef="Keywords_germany_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_value_added_tax_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- momsnummer
- momsnr.
- moms #
- vat# mehrwertsteuer
- ater
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer


## <a name="greece-drivers-license-number"></a>Grækenlands kørekortnummer

Denne enhed er inkluderet i den følsomme oplysningstype EU-kørekortnummer. Det fås også som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_greece_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_greece_eu_driver's_license_number` fra eller.

```xml
      <!-- Greece Driver's License Number -->
      <Entity id="7a2200b5-aacf-4e3c-ab36-136d3e68b7da" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_greece_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver er s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης


## <a name="greece-national-id-card"></a>National ID-kort for Grækenland

### <a name="format"></a>Formatér

Kombination af 7-8 bogstaver og tal plus en bindestreg

### <a name="pattern"></a>Mønster

Syv bogstaver og tal (gammelt format):
- Et bogstav (ethvert bogstav i det græske alfabet)
- En bindestreg
- Seks cifre

Otte bogstaver og tal (nyt format):
- To bogstaver, hvis store tegn optræder i både det græske og latinske alfabet (ABEZHIKMNOPTYX)
- En bindestreg
- Seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_greece_id_card indhold, der svarer til mønsteret.
- Der er fundet Keyword_greece_id_card nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_greece_id_card indhold, der svarer til mønsteret.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- græsk id
- græsk national id
- græsk personligt id-kort
- græsk indent-id
- identitetskort
- tautotita
- ταυτότητα
- ταυτότητας


## <a name="greece-passport-number"></a>Grækenlands pasnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver efterfulgt af syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_greece_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_greece_eu_passport_number` fra eller.
- Det regulære `Regex_greece_eu_passport_date` udtryk finder dato i formatet DD MMM JY (eksempel - 28. august 19), `Keywords_greece_eu_passport_date` eller der er fundet et nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_greece_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_greece_eu_passport_number` fra eller.

```xml
      <!-- Greece Passport Number -->
      <Entity id="7e65eb47-cdf9-4f52-8f90-2a27d5ee67e3" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_greece_eu_passport_date" />
            <Match idRef="Keywords_greece_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_greece_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο


## <a name="greece-physical-addresses"></a>Fysiske adresser i Grækenland

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Grækenland. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem

## <a name="greece-social-security-number-amka"></a>Grækenlands CPR-nummer (AMKA)

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

- Seks cifre som fødselsdato YYMMDD
- Fire cifre
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_greece_eu_ssn` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_greece_eu_ssn_or_equivalent` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_greece_eu_ssn` indhold, der svarer til mønsteret.

```xml
      <!-- Greece Social Security Number (AMKA) -->
      <Entity id="e39b03f4-50ea-41ae-af7a-a4b9539596ad" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_greece_eu_ssn" />
          <Match idRef="Keywords_greece_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_greece_eu_ssn" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- ssn
- ssn #
- cpr-nr
- socialsecurityno #
- CPR-nummer
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης


## <a name="greece-tax-identification-number"></a>Moms-id for Grækenland

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

Ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

Ni cifre

### <a name="checksum"></a>Kontrolsum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk  `Regex_greece_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_greece_eu_tax_file_number` nøgleord fra.

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- afm #
- afm
- aμμ|aμ αεεμμμμ
- aμμ
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- momsregistreringsdatabasenr
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- taxregistryno #
- tin-id
- tinnr
- tin #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο


## <a name="hong-kong-identity-card-hkid-number"></a>Hongkong-identitetskortnummer

### <a name="format"></a>Formatér

Kombination af 8-9 bogstaver og tal plus valgfri parenteser omkring det endelige tegn

### <a name="pattern"></a>Mønster

Kombination af 8-9 bogstaver:
- 1-2 bogstaver (der er ikke store bogstaver)
- Seks cifre
- Det sidste tegn (et ciffer eller bogstavet A), som er det kontrollerende ciffer og eventuelt omsluttet af parenteser.

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_hong_kong_id_card, der svarer til mønsteret.
- Der er fundet Keyword_hong_kong_id_card nøgleord.
- Kontrolsummet overføres.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_hong_kong_id_card, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Hong Kong Identity Card (HKID) number -->
<Entity id="e63c28a7-ad29-4c17-a41a-3d2a0b70fd9c" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_hong_kong_id_card"/>
     <Match idRef="Keyword_hong_kong_id_card"/>
  </Pattern>
  <Pattern confidenceLevel="65">
     <IdMatch idRef="Func_hong_kong_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- HONGKONG-identitetskort
- HKIDC
- id-kort
- identitetskort
- hk-identitetskort
- hong kong id
- 香港身份證
- 香港永久性居民身份證
- 身份證
- 身份証
- 身分證
- 身分証
- 香港身份証
- 香港身分證
- 香港身分証
- 香港身份證
- 香港居民身份證
- 香港居民身份証
- 香港居民身分證
- 香港居民身分証
- 香港永久性居民身份証
- 香港永久性居民身分證
- 香港永久性居民身分証
- 香港永久性居民身份證
- 香港非永久性居民身份證
- 香港非永久性居民身份証
- 香港非永久性居民身分證
- 香港非永久性居民身分証
- 香港特別行政區永久性居民身份證
- 香港特別行政區永久性居民身份証
- 香港特別行政區永久性居民身分證
- 香港特別行政區永久性居民身分証
- 香港特別行政區非永久性居民身份證
- 香港特別行政區非永久性居民身份証
- 香港特別行政區非永久性居民身分證
- 香港特別行政區非永久性居民身分証


## <a name="hungary-drivers-license-number"></a>Ungarns kørekortnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

To bogstaver og seks cifre:

- To bogstaver (der er ikke tale om store og små bogstaver)
- Seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk  `Regex_hungary_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_hungary_eu_driver's_license_number` fra eller.

```xml
      <Entity id="9d31c46b-6e6b-444c-aeb1-6dd7e604bb24" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_hungary_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver ikke s_license_number

- vezetoi engedely
- vezetèi engedély
- vezetèi engedélyek


## <a name="hungary-passport-number"></a>Ungarns pasnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af seks eller syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver efterfulgt af seks eller syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_hungary_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_hungary_eu_passport_number` fra eller.
- Det regulære `Regex_hungary_eu_passport_date` udtryk finder dato i formatet DD MMM/MMM JY (eksempel - 01 MÁR/MAR 12), `Keywords_eu_passport_date` eller der er fundet et nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_hungary_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_hungary_eu_passport_number` fra eller.

```xml
      <!-- Hungary Passport Number -->
      <Entity id="5b483910-9aa7-4c99-9917-f4001464bda7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_hungary_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_hungary_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_hungary_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="hungary-personal-identification-number"></a>Ungarns personlige identifikationsnummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

11 cifre:

- Et ciffer, der svarer til køn, 1 for mand, 2 for kvinde. Andre tal er også muligt for borgere, der er født før 1900, eller som har dobbelt så mange mennesker som mennesker.
- Seks cifre, der svarer til fødselsdato (YYMMDD)
- Tre cifre, der svarer til et serienummer
- Et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder  `Func_hungary_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_hungary_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder  `Func_hungary_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Hungary Personal Identification Number -->
      <Entity id="7b5cc218-7046-47d9-80c9-f325b50896ca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Match idRef="Keywords_hungary_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- id-nummer
- id-nummer
- sz ig
- sz. ig.
- sz.ig.
- személyazonosító ig manuelvány
- személyi iguzvány


## <a name="hungary-physical-addresses"></a>Fysiske adresser i Ungarn

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Ungarn. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="hungary-social-security-number-taj"></a>Ungarns CPR-nummer (FUNKTIONER)

### <a name="format"></a>Formatér

Ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

Ni cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder  `Func_hungary_eu_ssn_or_equivalent` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_hungary_eu_ssn_or_equivalent` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder  `Func_hungary_eu_ssn_or_equivalent` indhold, der svarer til mønsteret.

```xml
      <!-- Hungarian Social Security Number (TAJ) -->
      <Entity id="0de78315-9537-47f5-95ab-b3e77eba3993" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
          <Match idRef="Keywords_hungary_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_ssn_or_equivalent" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- ungarsk CPR-nummer
- CPR-nummer
- cpr-nummer #
- hssn #
- socialsecuritynno
- hssn
- ternet
- ternet #
- ssn
- ssn #
- cpr-nr
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám


## <a name="hungary-tax-identification-number"></a>Det ungarske skatte-id

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10 cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

10 cifre:

- Et ciffer, der skal være "8"
- Otte cifre
- Et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder  `Func_hungary_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_hungary_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder  `Func_hungary_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Hungary Tax Identification Number -->
      <Entity id="ede42eb4-59d9-49eb-9603-d7853fbda91d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Match idRef="Keywords_hungary_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungary_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_hungary_eu_telephone_number" />
            <Match idRef="Keywords_hungary_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- ungarsk tin
- hangatiantin #
- skattemyndighed ingen
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- momsnummer


## <a name="hungary-value-added-tax-number"></a>Ungarns momsnummer tilføjet

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10-tegns alfanumeriske mønster

### <a name="pattern"></a>Mønster

10-tegns alfanumeriske mønster:

- to bogstaver - HU eller hu
- valgfrit mellemrum
- otte cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder Func_hungarian_value_added_tax_number, der svarer til mønsteret.
- Der er fundet Keywords_hungarian_value_added_tax_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder Func_hungarian_value_added_tax_number, der svarer til mønsteret.

```xml
      <!-- Hungarian Value Added Tax Number -->
      <Entity id="976349a0-683b-477a-90f8-ff0a220d5592" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
          <Match idRef="Keywords_hungarian_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_hungarian_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- moms
- momsnummer for værdi tilføjet
- moms #
- vatno #
- ungarskvatno #
- momsnr.
- værdi tilføjet moms áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám


## <a name="iceland-physical-addresses"></a>Fysiske adresser i Island

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Island. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>Funktionsvanskeligheder, der er angivet i USA Disability Evaluation under Social Security

Denne ubundede navngivne enhed registrerer navne på forringelser, der er angivet i DEN amerikanske Disability Evaluation Under Social Security, f.eks. social *svindler*. Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="india-drivers-license-number"></a>Indien Kørekortnummer

### <a name="format"></a>Formatér

15 tegn alfanumeriske mønster

### <a name="pattern"></a>Mønster

15 bogstaver eller tal:
- To bogstaver, der angiver statskode
- Valgfrit mellemrum eller bindestreg
- To cifre, der angiver bykode
- Valgfrit mellemrum eller bindestreg
- fire cifre, der angiver udstedelsesåret
- Valgfrit mellemrum eller bindestreg
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_india_driving_license` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_driver's_license_number_common` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_india_driving_license` finder indhold, der svarer til mønsteret.


```xml
      <!-- India Driver's License Number -->
        <Entity id="680788a3-53b6-455a-b891-c38cd76dc917" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_india_driving_license" />
            <Match idRef="Keywords_eu_driver's_license_number_common" />
          </Pattern>
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_india_driving_license" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver ikke s_license_number_common

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer



## <a name="india-gst-number"></a>India GST Number

### <a name="format"></a>Formatér

15 tegn alfanumeriske mønster

### <a name="pattern"></a>Mønster

15 bogstaver eller tal:
- To cifre, der repræsenterer gyldig tilstandskode
- et valgfrit mellemrum eller bindestreg
- ti tegn, der repræsenterer et permanent kontonummer (PAN) 
- et bogstav eller et tal
- et valgfrit mellemrum eller bindestreg
- et bogstav 'z' eller 'Z'
- et valgfrit mellemrum eller bindestreg
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_india_gst_number` indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_india_gst_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_india_gst_number` indhold, der svarer til mønsteret.


```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- gst
- gstin
- vare- og tjenesteafgift
- vare- og tjenesteafgift


## <a name="india-permanent-account-number-pan"></a>Indiens permanente kontonummer (PAN)

### <a name="format"></a>Formatér

10 bogstaver eller tal

### <a name="pattern"></a>Mønster

10 bogstaver eller tal:
- Tre bogstaver (der er ikke tale om store og små bogstaver)
- Et bogstav i C, P, H, F, A, T, B, L, J, G (der er ikke store og små bogstaver)
- Et bogstav
- Fire cifre
- Et bogstav, der er et alfabetisk kontrolcifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_india_permanent_account_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_india_permanent_account_number nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_india_permanent_account_number indhold, der svarer til mønsteret.


```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent kontonummer
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Indiens entydige identifikationsnummer (Aadhaar)

### <a name="format"></a>Formatér

12 cifre, der indeholder valgfrie mellemrum eller tankestreger

### <a name="pattern"></a>Mønster

12 cifre:
- Et ciffer, der ikke er 0 eller 1
- Tre cifre
- Et valgfrit mellemrum eller bindestreg
- Fire cifre
- Et valgfrit mellemrum eller bindestreg
- Det sidste ciffer, som er kontrolcifret

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_india_aadhaar, der svarer til mønsteret.
- Der er fundet Keyword_india_aadhar nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder Func_india_aadhaar, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- India Unique Identification (Aadhaar) number -->
<Entity id="1ca46b29-76f5-4f46-9383-cfa15e91048f" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_india_aadhaar"/>
     <Match idRef="Keyword_india_aadhar"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_india_aadhaar"/>
  </Pattern>
</Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- uid
- आधार
- uidai


## <a name="india-voter-id-card"></a>Indien- og id-kort

### <a name="format"></a>Formatér

10-tegns alfanumeriske mønster

### <a name="pattern"></a>Mønster

10 bogstaver eller tal:
- tre bogstaver
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_india_voter_id_card` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_india_voter_id_card` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_india_voter_id_card` finder indhold, der svarer til mønsteret.


```xml
      <!-- India Voter Id Card  -->
        <Entity id="646d643f-5228-4408-acc8-f2e81a6df897" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
           <Pattern confidenceLevel="75">
             <IdMatch idRef="Regex_india_voter_id_card" />
             <Match idRef="Keyword_india_voter_id_card" />
            </Pattern>
           <Pattern confidenceLevel="65">
              <IdMatch idRef="Regex_india_voter_id_card" />
            </Pattern>
        </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- dat
- voterid
- chipkort
- stemmekort
- billedidentitetskort for udfald
- EPISK
- ECI
- valg commmision


## <a name="indonesia-identity-card-ktp-number"></a>Indonesia identity card (KTP) number

### <a name="format"></a>Formatér

16 cifre, der indeholder valgfrie punktummer

### <a name="pattern"></a>Mønster

16 cifre:
- Tocifret områdekode
- Et punktum (valgfrit)
- Tocifret regency eller bykode
- Tocifret underdistrictkode
- Et punktum (valgfrit)
- Seks cifre i formatet DDMMYY, som er fødselsdatoen
- Et punktum (valgfrit)
- Fire cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk Regex_indonesia_id_card finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_indonesia_id_card nøgleord.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>Nummer på international bankkonto (IBAN)

### <a name="format"></a>Formatér

Landekode (to bogstaver) plus checkcifre (to cifre) plus bban-tal (op til 30 tegn)

### <a name="pattern"></a>Mønster

Mønsteret skal omfatte alle følgende:

- Landekode på to bogstaver
- To kontrolcifre (efterfulgt af et valgfrit mellemrum)
- 1-7 grupper af fire bogstaver eller cifre (kan adskilles med mellemrum)
- 1-3 bogstaver eller tal

Formatet for hvert land er en smule anderledes. Typen af IBAN-følsomme oplysninger dækker disse 60 lande:

- annonce
- ae
- al
- på
- az
- ba
- be
- bg
- 2016
- ch
- cr
- cy
- cz
- de
- dk
- skal du
- ee
- es
- fi
- fo
- fr
- gb
- ge
- gi
- gl
- gr
- hr
- hu
- ie
- il
- er
- det
- kw
- kz
- lb
- li
- lt
- lu
- lv
- mc
- md
- mig
- mk
- mr
- mt
- mu
- nl
- Nej
- pl
- pt
- ro
- rs
- sa
- se
- si
- sk
- sm
- tn
- tr
- vg

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Funktionen finder Func_iban, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

Ingen


## <a name="international-classification-of-diseases-icd-10-cm"></a>International klassificering af klassifikationer (ICD-10-CM)

### <a name="format"></a>Formatér

Ordbog

### <a name="pattern"></a>Mønster

Nøgleord

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Der er fundet Dictionary_icd_10_updated nøgleord.
- Der er fundet Dictionary_icd_10_codes nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Der er fundet et nøgleord Dictionary_icd_10_ opdateret.

```xml
      <!-- ICD-10 CM -->
      <Entity id="3356946c-6bb7-449b-b253-6ffa419c0ce7" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_10_updated" />
          <Match idRef="Dictionary_icd_10_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_10_updated" />
        </Pattern>

```

### <a name="keywords"></a>Nøgleord

Et hvilket som helst udtryk Dictionary_icd_10_updated nøgleordsordbogen, som er baseret på den internationale klassificering af sårbarheder, tiende revision [, 10. ændring af skrivning (ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604). Denne type søger kun efter ordet, ikke forsikringskoderne.

Et hvilket som helst udtryk fra nøgleordsordbogen Dictionary_icd_10_codes, som er baseret på den internationale klassificering af nr. [10, 10, 10, revision og skrivning (ICD-10-CM).](https://go.microsoft.com/fwlink/?linkid=852604). Denne type søger kun efter forsikringskoder, ikke beskrivelsen.


## <a name="international-classification-of-diseases-icd-9-cm"></a>International klassificering af klassifikationer (ICD-9-CM)

### <a name="format"></a>Formatér

Ordbog

### <a name="pattern"></a>Mønster

Nøgleord

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Der er fundet Dictionary_icd_9_updated nøgleord.
- Der er fundet Dictionary_icd_9_codes nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Der er fundet Dictionary_icd_9_updated nøgleord.

```xml
    <Entity id="fa3f9c74-ee07-4c52-b5f2-085d6b2c0ec4" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Dictionary_icd_9_updated" />
          <Match idRef="Dictionary_icd_9_codes" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Dictionary_icd_9_updated" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

Et hvilket som helst udtryk Dictionary_icd_9_updated nøgleordsordbogen, som er baseret på den internationale klassificering af sårbarheder, niende revision [, skrivning (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Denne type søger kun efter ordet, ikke forsikringskoderne.

Et hvilket som helst udtryk Dictionary_icd_9_codes nøgleordsordbogen, som er baseret på den internationale klassificering af sårbarheder [, niende revision, kliniske ændringer (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Denne type søger kun efter forsikringskoder, ikke beskrivelsen.

## <a name="ip-address"></a>IP-adresse

### <a name="format"></a>Formatér

#### <a name="ipv4"></a>IPv4:
Komplekst mønster, der tager højde for formaterede (perioder) og ikke-formaterede (ingen perioder) versioner af IPv4-adresserne

#### <a name="ipv6"></a>IPv6:
Komplekst mønster, der tager hensyn til formaterede IPv6-tal (som indeholder kolon)

### <a name="pattern"></a>Mønster

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

For IPv6 har en DLP-politik høj tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_ipv6_address, der svarer til mønsteret.
- Der er ikke fundet Keyword_ipaddress nøgleord.

For IPv4 har en DLP-politik høj tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_ipv4_address, der svarer til mønsteret.
- Der er fundet Keyword_ipaddress nøgleord.

For IPv6 har en DLP-politik høj tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_ipv6_address, der svarer til mønsteret.
- Der er ikke fundet Keyword_ipaddress nøgleord.

```xml
    <!-- IP Address --> 
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (der er store og små bogstaver i dette nøgleord)
- ip-adresse
- ip-adresser
- internetprotokol
- IP-כתובת ã


## <a name="ip-address-v4"></a>IP-adresse v4

### <a name="format"></a>Formatér

Komplekst mønster, der tager højde for formaterede (perioder) og ikke-formaterede (ingen perioder) versioner af IPv4-adresserne

### <a name="pattern"></a>Mønster


### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_ipv4_address` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_ipaddress` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_ipv4_address` finder indhold, der svarer til mønsteret.


```xml
      <!-- IP Address v4--> 
      <Entity id="a7dd5e5f-e7f9-4626-a2c6-86a8cb6830d2" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv4_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv4_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (store og små bogstaver)
- ip-adresse
- ip-adresser
- internetprotokol
- IP-כתובת ã


## <a name="ip-address-v6"></a>IP-adresse v6

### <a name="format"></a>Formatér

Komplekst mønster, der tager hensyn til formaterede IPv6-tal (som indeholder kolon)

### <a name="pattern"></a>Mønster


### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_ipv6_address` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_ipaddress` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_ipv6_address` finder indhold, der svarer til mønsteret.


```xml
      <!-- IP Address v6-->
      <Entity id="3f691089-7413-4926-ab3b-3c5ea8a1c17e" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv6_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv6_address" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (store og små bogstaver)
- ip-adresse
- ip-adresser
- internetprotokol
- IP-כתובת ã


## <a name="ireland-drivers-license-number"></a>Irlands kørekortnummer

### <a name="format"></a>Formatér

Seks cifre efterfulgt af fire bogstaver

### <a name="pattern"></a>Mønster

Seks cifre og fire bogstaver:

- Seks cifre
- Fire bogstaver (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:

- Det regulære udtryk  `Regex_ireland_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_ireland_eu_driver's_license_number` fra eller.

```xml
      <!-- Ireland Driver's License Number -->
      <Entity id="e01bccd9-eb4d-414f-ace1-e9b6a4c4a2ca" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_ireland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver ikke s_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>Irlands pasnummer

### <a name="format"></a>Formatér

To bogstaver eller cifre efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver eller cifre efterfulgt af syv cifre:

- To cifre eller bogstaver (der er ikke store bogstaver)
- Syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_ireland_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_ireland_eu_passport_number` fra eller.
- Det regulære `Regex_ireland_eu_passport_date` udtryk finder dato i formatet DD MMM/MMMYYY (Eksempel - 01 BEA/MAJ 1988), `Keywords_eu_passport_date` eller der er fundet et nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_ireland_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_ireland_eu_passport_number` fra eller.

```xml
      <!-- Ireland Passport Number -->
      <Entity id="a2130f27-9ee2-4103-84f9-a6b1ee7d0cbf" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_ireland_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ireland_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_ireland_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhchacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="ireland-personal-public-service-pps-number"></a>Irlands personnummer for offentlig tjeneste (PPS)

### <a name="format"></a>Formatér

Gammelt format (indtil 31. december 2012):
- syv cifre efterfulgt af 1-2 bogstaver

Nyt format (1. januar 2013 og efter):
- syv cifre efterfulgt af to bogstaver

### <a name="pattern"></a>Mønster

Gammelt format (indtil 31. december 2012):
- syv cifre
- et til to bogstaver (der er ikke store bogstaver)

Nyt format (1. januar 2013 og efter):
- syv cifre
- Et bogstav (der er ikke tale om store og små bogstaver), som er et alfabetisk kontrolcifre
- Et valgfrit bogstav i området A-I eller "W"

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_ireland_pps, der svarer til mønsteret.
- Der er fundet Keywords_ireland_eu_national_id_card nøgleord.
- Kontrolsummet overføres.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_ireland_pps, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
      <!-- Ireland Personal Public Service (PPS) Number -->
      <Entity id="1cdb674d-c19a-4fcf-9f4b-7f56cc87345a" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_ireland_pps" />
          <Match idRef="Keywords_ireland_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_ireland_pps" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- klientidentitetstjeneste
- id-nummer
- personligt id-nummer
- nummer på personlig offentlig tjeneste
- personlig tjeneste nej
- phearsanta seirbhíse poiblí
- pps no
- pps-nummer
- pps num
- pps-tjenestenr.
- ppsn
- ppsno #
- ppsno
- psp
- offentlig tjenestenr.
- publicserviceno #
- publicserviceno
- indtægts- og socialforsikringsnummer
- rsi no
- rsi-nummer
- rsin
- seirbhís aitheantais-klient
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="ireland-physical-addresses"></a>Fysiske adresser i Irland

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Irland. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="israel-bank-account-number"></a>Israels bankkontonummer

### <a name="format"></a>Formatér

13 cifre

### <a name="pattern"></a>Mønster

Formateret:
- to cifre
- en bindestreg
- Tre cifre
- en bindestreg
- otte cifre

Uformateret:
- 13 fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_israel_bank_account_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_israel_bank_account_number nøgleord.

```xml
<!-- Israel Bank Account Number -->
<Entity id="7d08b2ff-a0b9-437f-957c-aeddbf9b2b25" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_israel_bank_account_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_israel_bank_account_number" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Bankkontonummer
- Bankkonto
- Kontonummer
- מספר חשבון בנק


## <a name="israel-national-identification-number"></a>Israels nationale identifikationsnummer

### <a name="format"></a>Formatér

ni cifre

### <a name="pattern"></a>Mønster

ni fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_israeli_national_id_number, der svarer til mønsteret.
- Der er fundet Keyword_Israel_National_ID nøgleord.
- Kontrolsummet overføres.

```xml
<!-- Israel National ID Number -->
<Entity id="e05881f5-1db1-418c-89aa-a3ac5c5277ee" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_israeli_national_id_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_Israel_National_ID" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

-   מספר זהות
-   מספר זיה וי
-   מספר זיהוי ישר אלי      
-   זהותישר אלית
-   هو ية اسرائيل ية عدد
-   هوية إسرائ يلية
-   رقم الهوية
-   عدد هوية فريدة من نوعها
-   id-nummer #
-   id-nummer
-   identitet nej        
-   identitetsnummer #
-   identitetsnummer
-   israelskeidentitynumber       
-   personligt id
-   entydigt id  


## <a name="italy-drivers-license-number"></a>Italiens kørekortnummer

Denne type enhed er inkluderet i den følsomme oplysningstype EU-kørekortnummer. Det fås også som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

en kombination af 10 bogstaver og cifre

### <a name="pattern"></a>Mønster

en kombination af 10 bogstaver og cifre:
- et bogstav (der er ikke tale om store og små bogstaver)
- bogstavet "A" eller "V" (der er ikke tale om store og små bogstaver)
- syv cifre
- et bogstav (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk `Regex_italy_drivers_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_driver's_license_number` nøgleord `Keyword_italy_drivers_license_number` fra eller.

```xml
    <!-- Italy Driver's license Number -->
    <Entity id="97d6244f-9157-41bd-8e0c-9d669a5c4d71" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_italy_drivers_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keyword_italy_drivers_license_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente
- patente di guida
- patente guida
- patenti di guida
- patenti guida


## <a name="italy-fiscal-code"></a>Italiens regnskabskode
Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

en kombination af 16 tegn og bogstaver og cifre i det angivne mønster

### <a name="pattern"></a>Mønster

En kombination af 16 tegn og bogstaver og cifre:
- Tre bogstaver, der svarer til de første tre konsonanter i familienavnet
- Tre bogstaver, der svarer til den første, tredje og fjerde konsonant i fornavnet
- To cifre, der svarer til de sidste cifre i fødselsår
- et bogstav, der svarer til bogstavet for fødselsmåneden – bogstaver bruges i alfabetisk rækkefølge, men kun bogstaverne A til E, H, L, M, P, R til T bruges (så januar er A, og oktober er R)
- To cifre, der svarer til fødselsdatoen for at kunne skelne mellem køn, føjes 40 til fødselsdatoen for kvinder
- fire cifre, der svarer til områdekoden for det sted, hvor personen er født (landekode bruges til fremmede lande)
- et paritetscifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_italy_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_italy_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_italy_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Italy Fiscal Code -->
      <Entity id="4cd79172-8da9-4ff5-9188-98b1e7e2eca6" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
          <Match idRef="Keywords_italy_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice-regnskab
- codice fiscale
- codice id personale
- codice personale
- regnskabskode
- numero certificato personale
- numero di identificazione fiscale
- numero id personale
- numero personale
- personligt certifikatnummer
- personlig kode
- personlig id-kode
- personligt id-nummer
- personalcodeno #
- momskode
- moms-id
- momsidentifikation
- moms-id
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="italy-passport-number"></a>Italiens pasnummer

### <a name="format"></a>Formatér

To bogstaver eller tal efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver eller cifre efterfulgt af syv cifre:

- To cifre eller bogstaver (der er ikke store bogstaver)
- syv cifre

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_italy_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_italy_eu_passport_number` fra eller.
- Det regulære `Regex_italy_eu_passport_date` udtryk finder dato i formatet DD MMM/MMMYYY (Eksempel - 01 GEN/JAN 1988), `Keywords_eu_passport_date` eller der er fundet et nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_italy_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_italy_eu_passport_number` fra eller.

```xml
      <!-- Italy Passport Number -->
      <Entity id="39811019-4750-445f-b26d-4c0e6c431544" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_italy_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_italy_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_italy_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- numéro passeport
- numero di passaporto
- numeri del passaporto
- passeport Italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="italy-physical-addresses"></a>Fysiske adresser i Italien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Italien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="italy-value-added-tax-number"></a>Momsnummer tilføjet i Italien

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13 tegn alfanumeriske mønster med valgfrie afgrænsere

### <a name="pattern"></a>Mønster

13 tegn alfanumeriske mønster med valgfrie afgrænsere:

- I or i
- T eller t
- Valgfrit mellemrum, prik, bindestreg eller komma
- 11 cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_italy_value_added_tax_number, der svarer til mønsteret.
- Der er fundet Keywords_italy_value_added_tax_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_italy_value_added_tax_number, der svarer til mønsteret.

```xml
      <!-- Italy Value Added Tax -->
      <Entity id="26a8cc07-2283-4a2a-ab1d-4ab643c4c67f" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
          <Match idRef="Keywords_italy_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_italy_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- momsnummer
- momsnr.
- moms #
- iva
- iva #


## <a name="japan-bank-account-number"></a>Japans bankkontonummer

### <a name="format"></a>Formatér

syv eller otte cifre

### <a name="pattern"></a>Mønster

bankkontonummer:
- syv eller otte cifre
- bankkontogrenskode:
- fire cifre
- et mellemrum eller en bindestreg (valgfrit)
- Tre cifre

Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_bank_account, der svarer til mønsteret.
- Der er fundet Keyword_jp_bank_account nøgleord.
- Et af følgende er sandt:
- Funktionen finder Func_jp_bank_account_branch_code, der svarer til mønsteret.
- Der er fundet Keyword_jp_bank_branch_code nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_bank_account, der svarer til mønsteret.
- Der er fundet Keyword_jp_bank_account nøgleord.

```xml
<!-- Japan Bank Account Number -->
<Entity id="d354f95b-96ee-4b80-80bc-4377312b55bc" patternsProximity="300" recommendedConfidence="75">
  <Version minEngineVersion="15.01.0131.000">
    <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_jp_bank_account" />
          <Match idRef="Keyword_jp_bank_account" />
          <Any minMatches="1">
            <Match idRef="Func_jp_bank_account_branch_code" />
            <Match idRef="Keyword_jp_bank_branch_code" />
          </Any>
      </Pattern>
  </Version>
     <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_bank_account" />
        <Match idRef="Keyword_jp_bank_account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Checkkontonummer
- Checkkonto
- Checkkonto #
- Checkkontonummer
- Checkkonto #
- Checkkontonr.
- Checkkontonr.
- Bankkontonummer
- Bankkonto
- Bankkonto #
- Bankkontonummer
- Bankkonto #
- Bankkontonr.
- Bankkontonr.
- Opsparingskontonummer
- Opsparingskonto
- Opsparingskonto #
- Opsparingskontonummer
- Opsparingskonto #
- Opsparingskontonr.
- Opsparingskontonr.
- Debetkontonummer
- Debetkonto
- Debetkonto #
- Debetkontonummer
- Debetkonto #
- Debetkontonr.
- Debetkontonr.
- 口座番号
- 銀行口座
- 銀行口座番号
- 総合口座
- 普通預金口座
- 普通口座
- 当座預金口座
- 当座口座
- 預金口座
- 振替口座
- 銀行
- バンク

#### <a name="keyword_jp_bank_branch_code"></a>Keyword_jp_bank_branch_code

- 支店番号
- 支店コード
- 店番号

## <a name="japan-drivers-license-number"></a>Japansk kørekortnummer

### <a name="format"></a>Formatér

12 cifre

### <a name="pattern"></a>Mønster

12 fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_drivers_license_number, der svarer til mønsteret.
- Der er fundet Keyword_jp_drivers_license_number nøgleord.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- lic #
- lics #
- 運転免許証
- 運転免許
- 免許証
- 免許
- 運転免許証番号
- 運転免許番号
- 免許証番号
- 免許番号
- 運転免許証ナンバー
- 運転免許ナンバー
- 免許証ナンバー
- 運転免許証no
- 運転免許no
- 免許証no
- 免許no
- 運転経歴証明書番号
- 運転経歴証明書
- 運転免許証No.
- 運転免許No.
- 免許証No.
- 免許Nø.
- 運転免許証 #
- 運転免許 #
- 免許証 #
- 免許 #


## <a name="japan-my-number---corporate"></a>Japan My Number – Corporate

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13-cifret tal

### <a name="pattern"></a>Mønster

13-cifret tal:

- et ciffer fra ét til ni
- 12 cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_japanese_my_number_corporate, der svarer til mønsteret.
- Der er fundet Keywords_japanese_my_number_corporate nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_japanese_my_number_corporate, der svarer til mønsteret.

```xml
      <!-- Japanese My Number – Corporate -->
      <Entity id="9e0eaf79-ff20-4ffb-b3e4-e7368d5db6ff" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
          <Match idRef="Keywords_japanese_my_number_corporate" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_japanese_my_number_corporate" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_japan_my_number_corporate"></a>Keyword_japan_my_number_corporate

- firmanummer
- マイナンバー
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 法人番号
- 指定通知書


## <a name="japan-my-number---personal"></a>Mit nummer i Japan – personlig

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

12-cifret tal

### <a name="pattern"></a>Mønster

12-cifret tal:

- fire cifre
- et valgfrit mellemrum, en prik eller en bindestreg
- fire cifre
- et valgfrit mellemrum, en prik eller en bindestreg
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_japanese_my_number_personal, der svarer til mønsteret.
- Der er fundet Keywords_japanese_my_number_personal nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_japanese_my_number_personal, der svarer til mønsteret.

```xml
      <!-- Japanese My Number – Personal -->
      <Entity id="98da8e66-7299-4ebd-9f82-c871ab37d3ef" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_japanese_my_number_personal" />
          <Match idRef="Keywords_japanese_my_number_personal" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_japanese_my_number_personal" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_japan_my_number_personal"></a>Keyword_japan_my_number_personal

- mit nummer
- マイナンバー
- 個人番号
- 共通番号
- マイナンバーカード
- マイナンバーカード番号
- 個人番号カード
- 個人識別番号
- 個人識別ナンバー
- 通知カード


## <a name="japan-passport-number"></a>Japan pasnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af syv cifre

### <a name="pattern"></a>Mønster

To bogstaver (der er ikke tale om store og små bogstaver) efterfulgt af syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_passport, der svarer til mønsteret.
- Der er fundet Keyword_jp_passport nøgleord.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Pas
- Pasnummer
- Pasnr.
- Pas #
- パスポート
- パスポート番号
- パスポートナンバー
- パスポート＃
- パスポート #
- パスポートNo.
- 旅券番号
- 旅券番号＃
- 旅券番号♯
- 旅券ナンバー


## <a name="japan-residence-card-number"></a>Japans kortnummer til bopælsland

### <a name="format"></a>Formatér

12 bogstaver og tal

### <a name="pattern"></a>Mønster

12 bogstaver og tal:
- To bogstaver (der er ikke tale om store og små bogstaver)
- otte cifre
- To bogstaver (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_jp_residence_card_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_jp_residence_card_number nøgleord.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- Bopælskortnummer
- Kort til bopælsland, nej
- Bopælskort #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Japans registreringsnummer for iboende

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

11 fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_resident_registration_number, der svarer til mønsteret.
- Der er fundet Keyword_jp_resident_registration_number nøgleord.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Bopælsregistreringsnummer
- Personer, der er bosiddende i det grundlæggende registreringsdatabasenummer
- Registreringsnr. iboende
- Resident Register No.
- Residents Basic Registry No.
- Basisregistreringsregistreringsnr.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証


## <a name="japan-social-insurance-number-sin"></a>Japan Social Insurance Number (SIN)

### <a name="format"></a>Formatér

7-12 cifre

### <a name="pattern"></a>Mønster

7-12 cifre:
- fire cifre
- en bindestreg (valgfrit)
- seks cifre ELLER
- 7-12 fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_sin, der svarer til mønsteret.
- Der er fundet Keyword_jp_sin nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_jp_sin_pre_1997, der svarer til mønsteret.
- Der er fundet Keyword_jp_sin nøgleord.

```xml
<!-- Japan Social Insurance Number -->
<Entity id="c840e719-0896-45bb-84fd-1ed5c95e45ff" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_jp_sin" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_sin_pre_1997" />
        <Match idRef="Keyword_jp_sin" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- Socialforsikringsnr.
- Cpr-antal
- Cpr-nummer
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険Nø.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号


## <a name="lab-test-terms"></a>Lab-testvilkår

Denne ubundede navngivne enhed registrerer ord, der er relateret til labtests, *f.eks. peptids for 2010*. Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="latvia-drivers-license-number"></a>Letlands kørekortnummer

### <a name="format"></a>Formatér

Tre bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

tre bogstaver og seks cifre:

- Tre bogstaver (der er ikke store bogstaver)
- seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_latvia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_latvia_eu_driver's_license_number` fra eller.

```xml
      <!-- Latvia Driver's License Number -->
      <Entity id="ec996de0-30f2-46b1-b192-4d2ff8805fa7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_latvia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver ikke s_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība


## <a name="latvia-passport-number"></a>Letlands pasnummer

### <a name="format"></a>Formatér

To bogstaver eller tal efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver eller cifre efterfulgt af syv cifre:

- To cifre eller bogstaver (der er ikke store bogstaver)
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_latvia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_latvia_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_latvia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_latvia_eu_passport_number` fra eller.

```xml
      <!-- Latvia Passport Number -->
      <Entity id="23ae25ec-cc28-421b-b77a-3054eadf1ede" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_latvia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurs
- pase numur
- pases numuri
- pases nr
- passeport no
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="latvia-personal-code"></a>Letlands personlige kode

### <a name="format"></a>Formatér

11 cifre og en valgfri bindestreg

### <a name="pattern"></a>Mønster

Gammelt format

11 cifre og en bindestreg:

- seks cifre, der svarer til fødselsdatoen (DDMMYY)
- en bindestreg
- et ciffer, der svarer til det 1. århundrede ("0" for det 19. århundrede, "1" for det 20. århundrede og "2" for det 21. århundrede)
- fire cifre, tilfældigt genereret

Nyt format

11 cifre

- To cifre "32"
- Ni cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_latvia_eu_national_id_card` regex'en finder `Regex_latvia_eu_national_id_card_new_format` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_latvia_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_latvia_eu_national_id_card` regex'en finder `Regex_latvia_eu_national_id_card_new_format` indhold, der svarer til mønsteret.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- administrativt nummer
- aēs nē
- fødselsnummer
- nummer for borgere
- civilt nummer
- elektronisk elektronisk nummer
- elektronisk nummer
- regnskabskode
- brugernummer i sundhedssektoren
- id #
- id-kode
- id-nummer
- identifikācijas numurs
- id-nummer
- individuelt nummer
- latvtvtvtv alejlighed
- nacionālais-id
- nationalt id
- nationalt identifikationsnummer
- nationalt identitetsnummer
- nationalt forsikringsnummer
- nationalt registernummer
- nodok genera numurs
- nodokúu id
- nodokúu identifikācija numurs
- personligt certifikatnummer
- personlig kode
- personlig id-kode
- personligt id-nummer
- personlig identifikationskode
- personligt id
- personligt identitetsnummer
- personligt nummer
- personlig numerisk kode
- personalcodeno #
- personas kods
- populationsidentifikationskode
- offentligt tjenestenummer
- registreringsnummer
- indtægtsnummer
- cpr-nummer
- CPR-nummer
- delstatsafgiftskode
- momsfilnummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- snyes nummer


## <a name="latvia-physical-addresses"></a>Fysiske adresser i Letland

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Letland. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="liechtenstein-physical-addresses"></a>Liechtenstein fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Liechtenstein. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT. 

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="lifestyles-that-relate-to-medical-conditions"></a>Livsstile, der er relateret til medicinske tilstande

Denne ubundede navngivne enhed registrerer vilkår relateret til livsstil, der kan resultere i en medicinsk tilstand, f.eks. *yd.* Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="lithuania-drivers-license-number"></a>Litauens kørekortnummer

### <a name="format"></a>Formatér

Otte cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_lithuania_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_lithuania_eu_driver's_license_number` fra eller.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver ikke s_license_number

- vairuotojo paibleymjimas
- vairuotojo paëymjimo numeris
- vairuotojo paëymjimo numeriai


## <a name="lithuania-personal-code"></a>Litauens personlige kode

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

11 cifre uden mellemrum og separatortegn:

- et ciffer (1-6), der svarer til personens køn og fødselstal
- seks cifre, der svarer til fødselsdato (YYMMDD)
- Tre cifre, der svarer til serienummeret for fødselsdatoen
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_lithuania_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_lithuania_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_lithuania_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Lithuania Personal Code -->
      <Entity id="cd6d3786-8ec3-4524-a2cf-1e0095379171" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Match idRef="Keywords_lithuania_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_lithuania_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_lithuania_eu_telephone_number" />
            <Match idRef="Keywords_lithuania_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- servicenummer for borgere
- mokesčič id
- mokesčič identifikavimas numeris
- mokesčič identifikavimo numeris
- mokesčič numeris
- nationalt id-nummer
- personlig kode
- personlig numerisk kode
- piliečio paslaugos numeris
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- unikglos identifikavimo kodas
- unikgnos identifikavimo numeris
- entydigt id-nummer
- entydigt identitetsnummer
- uniqueidentityno #


## <a name="lithuania-physical-addresses"></a>Fysiske adresser i Litauen

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Litauen. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="lithuania-passport-number"></a>Litauens pasnummer

### <a name="format"></a>Formatér

otte cifre eller bogstaver uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

otte cifre eller bogstaver (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_lithuania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_lithuania_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date3` udtryk finder dato i formatet DD MMYYY, eller der bliver fundet et nøgleord `Keywords_eu_passport_date` fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_lithuania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_lithuania_eu_passport_number` fra eller.

```xml
      <!-- Lithuania Passport Number -->
      <Entity id="1b79900f-047b-4c3f-846f-7d73b5534bce" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_lithuania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- paso numeris
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="luxemburg-drivers-license-number"></a>Luxemburgs kørekortnummer

### <a name="format"></a>Formatér

seks cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_luxemburg_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_luxemburg_eu_driver's_license_number` fra eller.

```xml
      <!-- Luxemburg Driver's License Number -->
      <Entity id="89daf717-1544-4860-9a2e-fc9166dd8852" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_luxemburg_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver ikke s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Luxemburgs nationale identifikationsnummer (fysiske personer)

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13 cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

13 cifre:

- 11 cifre
- to kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_luxemburg_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_luxemburg_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_luxemburg_eu_tax_file_number` indhold, der svarer til mønsteret.


```xml
      <!-- Luxemburg National Identification Number (Natural persons) -->
      <Entity id="aaf661ed-29ec-426d-8bf9-880cad298ebb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Match idRef="Keywords_luxemburg_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- id-personale
- idpersonnelle #
- idpersonnelle
- individuel kode
- individuelt id
- individuel identifikation
- individuel identitet
- numéro d'identification-medarbejder
- personligt id
- personlig identifikation
- personlig identitet
- personalidno #
- personalidnumber #
- persöniche identifikationsnummer
- entydigt id
- entydig identitet
- uniqueidkey #


## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Luxemburgs nationale identifikationsnummer (ikke-naturlige personer)

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

11 cifre

- to cifre
- et valgfrit mellemrum
- Tre cifre
- et valgfrit mellemrum
- Tre cifre
- et valgfrit mellemrum
- to cifre
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_luxemburg_eu_tax_file_number_non_natural` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_luxemburg_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_luxemburg_eu_tax_file_number_non_natural` indhold, der svarer til mønsteret.

```xml
      <!-- Luxemburg National Identification Number (Non-natural persons) -->
      <Entity id="84bffa3a-d805-4788-a613-b1e4df3804cf" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Match idRef="Keywords_luxemburg_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_luxemburg_eu_tax_file_number_non_natural" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_luxemburg_eu_telephone_number" />
            <Match idRef="Keywords_luxemburg_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_luxemburg_eu_tax_file_number"></a>Keywords_luxemburg_eu_tax_file_number

- carte de sécurité sociale
- étain non
- étain #
- identifiant d'impôt
- luxembourg tax identifikatiounsnummer
- numéro d'étain
- numéro d'identification fiscal luxembourgeois
- numéro d'identification fiscale
- social sikring
- sozialunterstützung
- soasilversécherung
- soalolversicherungsausweis
- Steier-id
- steier identifikatiounsnummer
- steier nummer
- steuer-id
- steueridentifikationsnummer
- steuernummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- zinn #
- zinn
- zinnzzinzin


## <a name="luxemburg-passport-number"></a>Luxemburgsk pasnummer

### <a name="format"></a>Formatér

otte cifre eller bogstaver uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

otte cifre eller bogstaver (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_luxemburg_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_luxemburg_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date3` udtryk finder dato i formatet DD MMYYY, eller der bliver fundet et nøgleord `Keywords_eu_passport_date` fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_luxemburg_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_luxemburg_eu_passport_number` fra eller.

```xml
      <!-- Luxemburg Passport Number -->
      <Entity id="81d5c027-bed9-4421-91a0-3b2e55b3eb85" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date3" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_luxemburg_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_luxemburg_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- luxembourgsk pas
- luxembourg passeport
- luxembourgsk pas
- no de passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- pass net
- bestået nr
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="luxemburg-physical-addresses"></a>luxemburgske fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Luxemburg. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="malaysia-identification-card-number"></a>Malaysia-id-nummer

### <a name="format"></a>Formatér

12 cifre, der indeholder valgfri bindestreger

### <a name="pattern"></a>Mønster

12 cifre:
- seks cifre i formatet YYMMDD, som er fødselsdatoen
- en bindestreg (valgfrit)
- To bogstavers sted-til-fødselskode
- en bindestreg (valgfrit)
- tre tilfældige cifre
- Étcifret kønskode

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_malaysia_id_card_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_malaysia_id_card_number nøgleord.

```xml
<!-- Malaysia ID Card Number -->
</Entity>
      <Entity id="7f0e921c-9677-435b-aba2-bb8f1013c749" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_malaysia_id_card_number" />
            <Match idRef="Keyword_malaysia_id_card_number" />
        </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- digitalt programkort
- i/c
- i/c nej
- ic
- ic no
- id-kort
- identifikationskort
- identitetskort
- k/p
- k/p nej
- akuan diri
- kad aplikasi digital
- kad pengenalan malaysia
- kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- malaysia identity card
- malaysisk identitetskort
- nric
- personligt identifikationskort


## <a name="malta-drivers-license-number"></a>Maltas kørekortnummer

### <a name="format"></a>Formatér

Kombination af to tegn og seks cifre i det angivne mønster

### <a name="pattern"></a>Mønster

kombination af to tegn og seks cifre:

- To tegn (cifre eller bogstaver, der ikke store og små bogstaver)
- et mellemrum (valgfrit)
- Tre cifre
- et mellemrum (valgfrit)
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_malta_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_malta_eu_driver's_license_number` fra eller.

```xml
      <!-- Malta Driver's License Number -->
      <Entity id="a3bdaa4a-8371-4735-8fa5-56ee0fb4afc4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_malta_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver ikke s_license_number

- liċenzja tas-deanan
- liċenzji tas-wieq


## <a name="malta-identity-card-number"></a>Maltas identitetskortnummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

syv cifre efterfulgt af ét bogstav

### <a name="pattern"></a>Mønster

syv cifre efterfulgt af ét bogstav:

- syv cifre
- et bogstav i "M, G, A, P, L, H, B, Z" (der kan ikke tales om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_malta_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_malta_eu_national_id_card` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_malta_eu_national_id_card` finder indhold, der svarer til mønsteret.

```xml
      <!-- Malta Identity Card Number -->
      <Entity id="854b36b3-a388-4ac8-a4ec-677c2b5e4356" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
          <Match idRef="Keywords_malta_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- servicenummer for borgere
- id tata-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tata-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tataxa
- personlig numerisk kode
- entydigt id-nummer
- entydigt identitetsnummer
- uniqueidentityno #


## <a name="malta-passport-number"></a>Maltas pasnummer

### <a name="format"></a>Formatér

syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_malta_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_malta_eu_passport_number` fra eller.
- Der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_malta_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_malta_eu_passport_number` fra eller.

```xml
      <!-- Malta Passport Number -->
      <Entity id="b2b21198-48f9-4d13-b2a5-03969bff0fb8" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
          <Match idRef="Keywords_eu_passport_date" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="malta-physical-addresses"></a>Fysiske adresser på Malta

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Malta. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="malta-tax-identification-number"></a>Maltas skatte-id

### <a name="format"></a>Formatér

Til Maltesisk alle sammen:
- syv cifre og et bogstav i det angivne mønster

Ikke-maltesisk and maltesiske enheder:
- ni cifre

### <a name="pattern"></a>Mønster

Maltesisk som det hele: syv cifre og ét bogstav

- syv cifre
- et bogstav (der er ikke tale om store og små bogstaver)

Ikke-maltesisk og maltesisk enheder: ni cifre

- ni cifre

### <a name="checksum"></a>Kontrolsum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex eller  `Regex_malta_eu_tax_file_number`  finder indhold `Regex_malta_eu_tax_file_number_non_maltese_national` , der svarer til mønsteret.
- Der er fundet et  `Keywords_malta_eu_tax_file_number` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex eller  `Regex_malta_eu_tax_file_number` finder indhold `Regex_malta_eu_tax_file_number_non_maltese_national` , der svarer til mønsteret.

```xml
      <!-- Malta Tax ID Number -->
      <Entity id="ec830c63-65f4-45d0-9d8c-910dc8334b20" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
          <Match idRef="Keywords_malta_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_malta_eu_tax_file_number_non_maltese_national" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- servicenummer for borgere
- id tata-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tata-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tataxa
- personlig numerisk kode
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- entydigt id-nummer
- entydigt identitetsnummer
- uniqueidentityno #

## <a name="medical-specialities"></a>Medicinske noget at se på

Denne ubundede navngivne enhed registrerer ord, der er relateret til medicinske specialiteter, f.eks *dermatologi*.  Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj

## <a name="medicare-beneficiary-identifier-mbi-card"></a>MBI-kort (Medicare Identifier)

### <a name="format"></a>Formatér

11-tegns alfanumeriske mønster

### <a name="pattern"></a>Mønster

- et ciffer mellem 1 og 9
- ét bogstav undtagen S, L, O, I, B, Z
- et ciffer eller bogstav undtagen S, L, O, I, B, Z
- ét ciffer
- en valgfri bindestreg
- ét bogstav undtagen S, L, O, I, B, Z
- et ciffer eller bogstav undtagen S, L, O, I, B, Z
- ét ciffer
- en valgfri bindestreg
- to bogstaver undtagen S, L, O, I, B, Z
- to cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_mbi_card` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keyword_mbi_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_mbi_card` finder indhold, der svarer til mønsteret.

```xml
    <!-- Medicare Beneficiary Identifier (MBI) card -->
      <Entity id="f753a286-f5cc-47e6-a592-4be25fd02591" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_mbi_card" />
          <Match idRef="Keyword_mbi_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_mbi_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- mbi
- mbi #
- medaljevinder #
- medicare identifier (modtagende)
- medicare, modtager ingen
- medicare- modtagernummer
- medaljevinder #


## <a name="mexico-unique-population-registry-code-curp"></a>Mexico Unique Population Registry Code (CURP)

### <a name="format"></a>Formatér

18 tegn alfanumeriske mønster

### <a name="pattern"></a>Mønster

- fire bogstaver (der er ingen tegn på store og små bogstaver)
- Seks cifre, der angiver en gyldig dato
- et bogstav - T/t eller M/m
- To bogstaver, der angiver en gyldig mexicansk statskode
- tre bogstaver
- et bogstav eller et tal
- ét ciffer

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_mexico_population_registry_code` indhold, der svarer til mønsteret.
- Der er fundet et  `Keyword_mexico_population_registry_code` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_mexico_population_registry_code` indhold, der svarer til mønsteret.

```xml
    <!-- Mexico Unique Population Registry Code (CURP) -->
      <Entity id="e905ad4d-5a74-406d-bf36-b1efca798af4" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_mexico_population_registry_code" />
          <Match idRef="Keyword_mexico_population_registry_code" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_mexico_population_registry_code" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Entydige registreringsdatabasekode for populationer 
- entydige populationskode
- CURP
- Personligt id
- Entydigt id
- personalid
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- clave unica
- clave personal Identidad
- personal Identidad Clave
- ClaveÚnica
- claveunica
- clavepersonalIdentidad


## <a name="netherlands-citizens-service-bsn-number"></a>Nederlandske borgeres servicenummer

### <a name="format"></a>Formatér

otte eller ni cifre, der indeholder valgfrie mellemrum

### <a name="pattern"></a>Mønster

otte ni cifre:
- Tre cifre
- et mellemrum (valgfrit)
- Tre cifre
- et mellemrum (valgfrit)
- to-tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_netherlands_bsn, der svarer til mønsteret.
- Der er fundet Keyword_netherlands_bsn nøgleord.
- Kontrolsummet overføres.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- bsn #
- bsn
- hamburgerservicenummer
- servicenummer for borgere
- personnummer
- personligt nummer
- personlig numerisk kode
- personrelateret nummer
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- cpr-nummer
- sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- entydigt id-nummer
- entydigt identitetsnummer
- uniqueidentityno #


## <a name="netherlands-drivers-license-number"></a>Nederlandsk kørekortnummer

### <a name="format"></a>Formatér

10 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_netherlands_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_netherlands_eu_driver's_license_number` fra eller.

```xml
      <!-- Netherlands Driver's License Number -->
      <Entity id="6247fbea-ab80-4be5-8233-308b7c031401" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_netherlands_eu_driver's_license_number" />
            </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver ikke s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers


## <a name="netherlands-passport-number"></a>Nederlandsk pasnummer

### <a name="format"></a>Formatér

ni bogstaver eller tal uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

ni bogstaver eller tal

### <a name="checksum"></a>Kontrolsum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_netherlands_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_netherlands_eu_passport_number` fra eller.
- Det regulære `Regex_netherlands_eu_passport_date` udtryk finder dato i formatet DD MMM/MMMYYY (Eksempel - 26 DENA/MAR 2012)

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_netherlands_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_netherlands_eu_passport_number` fra eller.

```xml
      <!-- Netherlands Passport Number -->
      <Entity id="61786727-bafd-45f6-94d9-888d815e228e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Match idRef="Regex_netherlands_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_netherlands_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_netherlands_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr


## <a name="netherlands-physical-addresses"></a>Nederlandske fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre, der er relateret til fysiske adresser fra Nederlandene. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="netherlands-tax-identification-number"></a>Nederlandsk skatte-id

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

ni cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_netherlands_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_netherlands_eu_tax_file_number` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_netherlands_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Netherlands Tax Identification Number -->
      <Entity id="01f42a64-eba7-4892-a67b-398237e4ade2" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
          <Match idRef="Keywords_netherlands_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_netherlands_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- nummer i en 2010
- hollânske skatteidentifikation
- hulandes impuesto id-nummer
- hulandes impuesto identification
- identificatienummer belasting
- identificatienummer van belasting
- impuesto-id
- impuesto-nummer
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- nederlandsk skatteidentifikation
- netherlands skatteidentifikation
- netherlands tin
- netherlands tin
- moms-id
- momsidentifikation
- moms-id
- moms-id-tal
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- momstal
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="netherlands-value-added-tax-number"></a>Nederlandsk momsnummer tilføjet

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

14 alfanumeriske mønster

### <a name="pattern"></a>Mønster

14-tegns alfanumeriske mønster:

- N eller n
- L eller l
- Valgfrit mellemrum, prik eller bindestreg
- ni cifre
- Valgfrit mellemrum, prik eller bindestreg
- B eller b
- to cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_netherlands_value_added_tax_number, der svarer til mønsteret.
- Der er fundet Keywords_netherlands_value_added_tax_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_netherlands_value_added_tax_number, der svarer til mønsteret.

```xml
      <!-- Netherlands Value Added Tax Number -->
      <Entity id="4f320d9b-4972-41ae-b337-88d499bb1ade" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
          <Match idRef="Keywords_netherlands_value_added_tax_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_netherlands_value_added_tax_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- momsnummer
- momsnr.
- moms #
- Wearde tafoege tax getal
- trane númer
- alt-nummer


## <a name="new-zealand-bank-account-number"></a>New Zealand bankkontonummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

14-cifret til 16-cifret mønster med valgfri afgrænser

### <a name="pattern"></a>Mønster

14-cifret til 16-cifret mønster med valgfri afgrænser:

- to cifre
- En valgfri bindestreg eller et mellemrum
- tre til fire cifre
- En valgfri bindestreg eller et mellemrum
- syv cifre
- En valgfri bindestreg eller et mellemrum
- to til tre cifre
- En bindestreg eller et mellemrum for indstillinger

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_zealand_bank_account_number, der svarer til mønsteret.
- Der er fundet Keywords_new_zealand_bank_account_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_zealand_bank_account_number, der svarer til mønsteret.

```xml
      <!-- New Zealand Bank Account Number -->
      <Entity id="1a97fc2b-dd2f-48f1-bc4e-2ddf25813956" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
          <Match idRef="Keywords_new_zFealand_bank_account_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_bank_account_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- kontonummer
- bankkonto
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr


## <a name="new-zealand-drivers-license-number"></a>New Zealand-kørekortnummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

otte alfanumeriske tegnmønster

### <a name="pattern"></a>Mønster

otte alfanumeriske tegnmønster

- to bogstaver
- seks cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_newzealand_driver_license_number, der svarer til mønsteret.
- Der er fundet Keywords_newzealand_driver_license_number nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_newzealand_driver_license_number, der svarer til mønsteret.

```xml
      <!-- New Zealand Driver License Number -->
      <Entity id="1924b377-d287-49c9-a737-cfe7a8a2615a" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
          <Match idRef="Keywords_newzealand_driver_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_driver_license_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- kørekort
- kørekort
- køre lic
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- international køretilladelse
- internationale køretilladelser
- nz automobile association
- new zealand automobile association


## <a name="new-zealand-inland-revenue-number"></a>New Zealand inland revenue number

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

otte eller ni cifre med valgfrie afgrænsere

### <a name="pattern"></a>Mønster

otte eller ni cifre med valgfrie afgrænsere

- to eller tre cifre
- et valgfrit mellemrum eller en bindestreg
- Tre cifre
- et valgfrit mellemrum eller en bindestreg
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_zealand_inland_revenue_number, der svarer til mønsteret.
- Der er fundet Keywords_new_zealand_inland_revenue_number nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_zealand_inland_revenue_number, der svarer til mønsteret.

```xml
      <!-- New Zealand Inland Revenue Number -->
      <Entity id="dd0fe2bc-7bcf-455f-bac1-83b1e3eb25fd" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
          <Match idRef="Keywords_new_zealand_inland_revenue_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_inland_revenue_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird no.
- ird no #
- nz ird
- new zealand ird
- ird number
- Indlands omsætningsnummer


## <a name="new-zealand-ministry-of-health-number"></a>New Zealand, der er del af et sundhedsnummer

### <a name="format"></a>Formatér

Tre bogstaver og fire cifre

### <a name="pattern"></a>Mønster

- Tre bogstaver (der er ikke tale om store og små bogstaver), bortset fra "I" og "O"
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_zealand_ministry_of_health_number, der svarer til mønsteret.
- Der er fundet Keyword_nz_terms nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_zealand_ministry_of_health_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
    <!-- New Zealand Health Number -->
    <Entity id="2b71c1c8-d14e-4430-82dc-fd1ed6bf05c7" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
          <Match idRef="Keyword_nz_terms" />
      </Pattern>
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_new_zealand_ministry_of_health_number" />
       </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- New Zealand
- National Health Index
- NHI #
- National Health Index #


## <a name="new-zealand-physical-addresses"></a>New Zealand fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra New Zealand. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="new-zealand-social-welfare-number"></a>New Zealand social cpr-nummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

ni cifre

### <a name="pattern"></a>Mønster

ni cifre

- Tre cifre
- en valgfri bindestreg
- Tre cifre
- en valgfri bindestreg
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_newzealand_social_welfare_number, der svarer til mønsteret.
- Der er fundet Keywords_newzealand_social_welfare_number nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_newzealand_social_welfare_number, der svarer til mønsteret.

```xml
      <!-- Newzealand Social Welfare Number -->
      <Entity id="20f3c48d-4ac1-4cd2-86bd-34ecc1826e9d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
          <Match idRef="Keywords_newzealand_social_welfare_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_newzealand_social_welfare_number" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- sociale ydelser #
- sociale ydelser #
- social integration Nej.
- socialt nummer
- swn #


## <a name="norway-identification-number"></a>Norges identifikationsnummer

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

11 cifre:
- seks cifre i formatet DDMMYY, som er fødselsdatoen
- trecifret individuelt tal
- to kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_norway_id_number, der svarer til mønsteret.
- Der er fundet Keyword_norway_id_number nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_norway_id_numbe, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Norway Identification Number -->
<Entity id="d4c8a798-e9f2-4bd3-9652-500d24080fc3" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_norway_id_number"/>
     <Match idRef="Keyword_norway_id_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_norway_id_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Personligt id-nummer
- Norsk id-nummer
- Id-nummer
- Identifikation
- Personnummer
- Fødselsnummer


## <a name="norway-physical-addresses"></a>Fysiske adresser i Norge

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Norge. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="philippines-unified-multi-purpose-identification-number"></a>Philippines unified multi-purpose IDENTIFICATION number

### <a name="format"></a>Formatér

12 cifre adskilt af bindestreger

### <a name="pattern"></a>Mønster

12 cifre:
- fire cifre
- en bindestreg
- syv cifre
- en bindestreg
- ét ciffer

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_philippines_unified_id, der svarer til mønsteret.
- Der er fundet Keyword_philippines_id nøgleord.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Samlet multifunktions-id
- UMID
- Identitetskort
- Pinag-isang ID med flere layunin


## <a name="poland-drivers-license-number"></a>Polens kørekortnummer

### <a name="format"></a>Formatér

14 cifre, der indeholder to skråstreger

### <a name="pattern"></a>Mønster

14 cifre og to skråstreger:

- fem cifre
- en skråstreg
- to cifre
- en skråstreg
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_poland_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_poland_eu_driver's_license_number` fra eller.

```xml
      <!-- Poland Driver's License Number -->
      <Entity id="24d51f99-ee9e-4060-a077-cae58cab1ee4" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_poland_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_poland_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver ikke s_license_number

- Prawo jazdy
- prawa jazdy


## <a name="poland-identity-card"></a>Polens identitetskort

### <a name="format"></a>Formatér

Tre bogstaver og seks cifre

### <a name="pattern"></a>Mønster

Tre bogstaver (der er ikke tale om store og små bogstaver) efterfulgt af seks cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_polish_national_id, der svarer til mønsteret.
- Der er fundet Keyword_polish_national_id_passport_number nøgleord.
- Kontrolsummet overføres.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu to mamsamoóci
- Dowód Tomossamoóci
- dow. os.


## <a name="poland-national-id-pesel"></a>Polens nationale id (PESEL)

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

- Seks cifre, der repræsenterer fødselsdato i formatet YYMMDD
- fire cifre
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_pesel_identification_number, der svarer til mønsteret.
- Der er fundet Keyword_pesel_identification_number nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_pesel_identification_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
      <!-- Poland National ID (PESEL) -->
      <Entity id="E3AAF206-4297-412F-9E06-BA8487E22456" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_pesel_identification_number" />
          <Match idRef="Keyword_pesel_identification_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_pesel_identification_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- to mamsamoóci narodowej


## <a name="poland-passport-number"></a>Polens pasnummer

Denne enhed med følsomme oplysninger er medtaget i typen af følsomme oplysninger om EU-pasnummer. Den fås også som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

To bogstaver og syv cifre

### <a name="pattern"></a>Mønster

To bogstaver (der er ikke tale om store og små bogstaver) efterfulgt af syv cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_polish_passport_number_v2` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keyword_polish_national_passport_number` fra eller.
- Der er fundet et `Keywords_eu_passport_date` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_polish_passport_number_v2` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keyword_polish_national_passport_number` fra eller.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_polish_passport_number_v2` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
      <!-- Poland Passport Number -->
      <Entity id="03937FB5-D2B6-4487-B61F-0F8BFF7C3517" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_polish_passport_number_v2" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_polish_national_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_passport_number_v2" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keyword_polish_national_passport_number"></a>Keyword_polish_national_passport_number

- numer paszportu
- numery paszportów
- numery paszportowe
- nr paszportu
- nr. paszportu
- nr paszportów
- n° passeport
- passeport n°

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="poland-physical-addresses"></a>Fysiske adresser i Polen

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Polen. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="poland-regon-number"></a>Polens REGON-nummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

9-cifret eller 14-cifret tal

### <a name="pattern"></a>Mønster

nicifret eller 14-cifret tal:

- ni cifre eller
- ni cifre
- bindestreg
- fem cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_polish_regon_number, der svarer til mønsteret.
- Der er fundet Keywords_polish_regon_number nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_polish_regon_number, der svarer til mønsteret.

```xml
      <!-- Polish REGON Number  -->
      <Entity id="fc87b421-f437-4f8b-b739-29a735ead0d9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_regon_number" />
          <Match idRef="Keywords_polish_regon_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_polish_regon_number" />
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Nøgleord

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon-id
- statistisk tal
- statistisk id
- statistisk nej
- regon-nummer
- regonid #
- regonno #
- firma-id
- firma-id #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #


## <a name="poland-tax-identification-number"></a>Polens skatte-id

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

11 cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

11 cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_poland_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_poland_eu_tax_file_number` nøgleord fra.


```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- nip #
- nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- moms-id #
- moms-id
- momsnr.
- momsnummer
- moms-id #
- moms-id
- vatno #


## <a name="portugal-citizen-card-number"></a>Portugals visitkortnummer for borgere

### <a name="format"></a>Formatér

otte cifre

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Udtrykket for det Regex_portugal_citizen_card finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_portugal_citizen_card nøgleord.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- visitkort for borgere
- dokumentnummer
- documento de identificação
- id-nummer
- identifikationsnr.
- id-nummer
- identitetskort nej
- identitetskortnummer
- nationalt id-kort
- NIC
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- portugal bi-nummer


## <a name="portugal-drivers-license-number"></a>Portugals kørekortnummer

### <a name="format"></a>Formatér

To mønstre – to bogstaver efterfulgt af 5-8 cifre med specialtegn

### <a name="pattern"></a>Mønster

Mønster 1: To bogstaver efterfulgt af 5/6 med specialtegn:
- To bogstaver (der er ikke tale om store og små bogstaver)
- En bindestreg
- Fem eller seks cifre
- Et mellemrum
- Et ciffer

Mønster 2: Et bogstav efterfulgt af 6/8 cifre med specialtegn:
- Et bogstav (der er ikke tale om store og små bogstaver)
- En bindestreg
- Seks eller otte cifre
- Et mellemrum
- Et ciffer


### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_portugal_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_portugal_eu_driver's_license_number` fra eller.

```xml
      <!-- Portugal Driver's License Number -->
      <Entity id="977f1e5a-2c33-4bcc-b516-95bb275cff23" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_portugal_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver ikke s_license_number

- carteira de motorista
- carteira motorista
- carteira de habilitação
- carteira habilitação
- número de licença
- número licença
- permissão de condução
- permissão condução
- Licença condução Portugal
- carta de condução


## <a name="portugal-passport-number"></a>Portugal pasnummer

### <a name="format"></a>Formatér

et bogstav efterfulgt af seks cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

et bogstav efterfulgt af seks cifre:

- et bogstav (der er ikke tale om store og små bogstaver)
- seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_portugal_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_portugal_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_portugal_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_portugal_eu_passport_number` fra eller.

```xml
      <!-- Portugal Passport Number -->
      <Entity id="080a52fd-a7bc-431e-b54d-51f08f59db11" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_portugal_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_portugal_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_portugal_eu_passport_number"></a>Keywords_portugal_eu_passport_number

- número do passaporte
- portugisisk pas
- portugisisk passeport
- portugisisk passaporte
- passaporte nº
- passeport nº
- números de passaporte
- portugisiske pas
- número passaporte
- números passaporte

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="portugal-physical-addresses"></a>Fysiske adresser i Portugal

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Portugal. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="portugal-tax-identification-number"></a>Moms-id for Portugal

### <a name="format"></a>Formatér

ni cifre med valgfrie mellemrum

### <a name="pattern"></a>Mønster

- Tre cifre
- et valgfrit mellemrum
- Tre cifre
- et valgfrit mellemrum
- Tre cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_portugal_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_portugal_eu_tax_file_number` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_portugal_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Portugal Tax Identification Number -->
      <Entity id="65372402-3131-4f1e-9983-4439841d1f15" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
          <Match idRef="Keywords_portugal_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_portugal_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- cpf #
- cpf
- nif #
- nif
- número de identificação fisca
- numero-regnskab
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="romania-drivers-license-number"></a>Rumæniens kørekortnummer

### <a name="format"></a>Formatér

et tegn efterfulgt af otte cifre

### <a name="pattern"></a>Mønster

et tegn efterfulgt af otte cifre:
- et bogstav (der er ikke tale om store og små bogstaver) eller et ciffer
- otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_romania_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_romania_eu_driver's_license_number` fra eller.

```xml
      <!-- Romania Driver's License Number -->
      <Entity id="b5511ace-2fd8-4ae4-b6fc-c7c6e4689e3c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_romania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver ikke s_license_number

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- permisele conducere
- permis conducere


## <a name="romania-passport-number"></a>Rumæniens pasnummer

### <a name="format"></a>Formatér

otte eller ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

otte eller ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_romania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_romania_eu_passport_number` fra eller.
- Det regulære `Regex_romania_eu_passport_date` udtryk finder dato i formatet DD MMM/MMM JY (eksempel- 01 FEB/FEB 10), `Keywords_eu_passport_date` eller der er fundet et nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_romania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_romania_eu_passport_number` fra eller.

```xml
      <!-- Romania Passport Number -->
      <Entity id="5d31b90c-7fe2-4a76-a14b-767b8fd19d6c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_romania_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_romania_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_romania_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numşrul paşaportului numarul pasaportului numerele paşaportului Paşaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="romania-personal-numeric-code-cnp"></a>Rumæniens personlige numeriske kode (CNP)

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13 cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

- et ciffer fra 1-9
- Seks cifre, der repræsenterer fødselsdato (YYMMDD)
- to cifre, som kan være 01-52 eller 99
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_romania_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_romania_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_romania_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Romania Personal Numerical Code (CNP) -->
      <Entity id="eb5fa399-fe28-4c67-8188-d63a616ed89c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
          <Match idRef="Keywords_romania_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_romania_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- cnp #
- cnp
- cod identificare personal
- cod numeric personal
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscal nr #
- id-ul taxei
- forsikringsnummer
- forsikringsnummer #
- nationalt id #
- nationalt id
- nationalt id-nummer
- num gener identificare personal
- num gener identitate
- numãr personal unic
- numãridentitate #
- numãridentitate
- num generpersonnic #
- num generpersonnic
- numãru de identificare fiscalã
- num generul de identificare fiscalã
- personlig numerisk kode
- fastgør #
- fastgør
- momsfil nej
- momsfilnummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #
- entydigt id-nummer
- entydigt identitetsnummer
- uniqueidentityno #
- uniqueidentityno


## <a name="romania-physical-addresses"></a>Fysiske adresser i Rumænien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Rumænien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="russia-passport-number-domestic"></a>Russisk pasnummer (nationale pasnummer)

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10-cifret tal

### <a name="pattern"></a>Mønster

10-cifret tal:

- to cifre
- et valgfrit mellemrum eller en bindestreg
- to cifre
- et valgfrit mellemrum
- seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex-Regex_Russian_Passport_Number_Domestic finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_Russian_Passport_Number nøgleord.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- pasnummer
- pasnr.
- pas #
- pas-id
- pasnr #
- pasnummer #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="russia-passport-number-international"></a>Russisk pasnummer internationalt

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

nicifret tal

### <a name="pattern"></a>Mønster

nicifret tal:

- to cifre
- et valgfrit mellemrum eller en bindestreg
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex-Regex_Russian_Passport_Number_International finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_Russian_Passport_Number nøgleord.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- pasnummer
- pasnr.
- pas #
- pas-id
- pasnr #
- pasnummer #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #


## <a name="saudi-arabia-national-id"></a>Saudi-Arabiens nationale id

### <a name="format"></a>Formatér

10 cifre

### <a name="pattern"></a>Mønster

Ti fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_saudi_arabia_national_id indhold, der svarer til mønsteret.
- Der er fundet Keyword_saudi_arabia_national_id nøgleord.

```xml
<!-- Saudi Arabia National ID -->
<Entity id="8c5a0ba8-404a-41a3-8871-746aa21ee6c0" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_saudi_arabia_national_id" />
        <Any minMatches="1">
          <Match idRef="Keyword_saudi_arabia_national_id" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Identifikationskort
- I kortnummer
- Id-nummer
- الوطنية الهوية بطاقة رقم


## <a name="singapore-national-registration-identity-card-nric-number"></a>Singapore-nummer til national registreringsidentitetskort (NRIC)

### <a name="format"></a>Formatér

ni bogstaver og cifre

### <a name="pattern"></a>Mønster

- ni bogstaver og cifre:
- bogstavet "F", "G", "S" eller "T" (der er ikke tale om store og små bogstaver)
- syv cifre
- et alfabetisk kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_singapore_nric finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_singapore_nric nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_singapore_nric finder indhold, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Singapore National Registration Identity Card (NRIC) Number -->
<Entity id="cead390a-dd83-4856-9751-fb6dc98c34da" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_singapore_nric"/>
     <Match idRef="Keyword_singapore_nric"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_singapore_nric"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- Nationalt registreringsidentitetskort
- Identitetskortnummer
- NRIC
- IC
- Fremmed identifikationsnummer
- FIN
- 身份证
- 身份證


## <a name="slovakia-drivers-license-number"></a>Slovakiets kørekortnummer

### <a name="format"></a>Formatér

et tegn efterfulgt af syv cifre

### <a name="pattern"></a>Mønster

et tegn efterfulgt af syv cifre

- et bogstav (der er ikke tale om store og små bogstaver) eller et ciffer
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_slovakia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_slovakia_eu_driver's_license_number` fra eller.

```xml
      <!-- Slovakia Driver's License Number -->
      <Entity id="14240c22-b6de-4ce5-a90b-137f74252513" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovakia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver ikke s_license_number

- vodičskč pre gauz
- vodičské pre gaulesk
- vodičského prezu
- vodičskčch pre gauzov


## <a name="slovakia-passport-number"></a>Slovakiets pasnummer

### <a name="format"></a>Formatér

et ciffer eller bogstav efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

et ciffer eller bogstav (der er ikke tale om store og små bogstaver) efterfulgt af syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_slovakia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_slovakia_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_slovakia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_slovakia_eu_passport_number` fra eller.

```xml
      <!-- Slovakia Passport Number -->
      <Entity id="238e1f08-d80e-4793-af33-9b57918335b7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovakia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovakia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_slovakia_eu_passport_number"></a>Keywords_slovakia_eu_passport_number

- číslo pasu
- čísla pasov
- pas č.
- Passeport n°
- n° Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="slovakia-personal-number"></a>Slovakiets personlige nummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

ni eller 10 cifre, der indeholder valgfri skråstreg

### <a name="pattern"></a>Mønster

- Seks cifre, der repræsenterer fødselsdato
- valgfri skråstreg (/)
- Tre cifre
- et valgfrit kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_slovakia_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_slovakia_eu_national_id_card` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_slovakia_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Slovakia Personal Number -->
      <Entity id="951c26b7-3b35-4f73-924b-15dd599cb9ab" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
          <Match idRef="Keywords_slovakia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovakia_eu_national_id_card" />
        </Pattern>
      </Entity>
    </Version>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- aíosító szám
- fødselsnummer
- číslo národnej identifikačnej karty
- číslo občianského prezu
- daňové číslo
- id-nummer
- identifikationsnr.
- id-nummer
- identifikačná karta č
- identifikačné číslo
- identitetskort nej
- identitetskortnummer
- národná identifikačná značka č
- nationalt nummer
- nationalnumber #
- nemzeti személyazonosító ig rudevány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- CPR-nummer
- ssn #
- ssn
- személyi iguzvány szám
- személyi iguzvány száma
- személyig manueltvány szám
- momsfil nej
- momsfilnummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="slovakia-physical-addresses"></a>Fysiske adresser i Slovakiet

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Slovakiet. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="slovenia-drivers-license-number"></a>Sloveniens kørekortnummer

### <a name="format"></a>Formatér

ni cifre uden mellemrum og separatortegn

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_slovenia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_slovenia_eu_driver's_license_number` fra eller.

```xml
      <!-- Slovenia Driver's License Number -->
      <Entity id="d5bc089a-f2ee-433d-a6b1-5c253051d6f2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_slovenia_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver ikke s_license_number

- vozniško dovoljenje
- vozniška številka-licens
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj


## <a name="slovenia-passport-number"></a>Sloveniens pasnummer

### <a name="format"></a>Formatér

To bogstaver efterfulgt af syv cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

To bogstaver efterfulgt af syv cifre:

- bogstavet "P"
- et stort bogstav
- syv cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_slovenia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_slovenia_eu_passport_number` fra eller.
- Det regulære `Regex_eu_passport_date1` udtryk finder dato i formatet DD.MM.YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_slovenia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_slovenia_eu_passport_number` fra eller.

```xml
      <!-- Slovenia Passport Number -->
      <Entity id="235b7976-7bbe-4df5-bb40-08678e749d1a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_slovenia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_slovenia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- potniliste #
- datum rojstva
- potniliste
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="slovenia-physical-addresses"></a>Fysiske adresser i Slovenien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Slovenien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="slovenia-tax-identification-number"></a>Skatteidentifikationsnummer for Slovenien

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

Otte cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

- et ciffer fra 1-9
- seks cifre
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_slovenia_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_slovenia_eu_tax_file_number` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_slovenia_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Slovenia Tax Identification Number -->
      <Entity id="e47b071e-c352-4d70-8241-8c215ad65505" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
          <Match idRef="Keywords_slovenia_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_slovenia_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- momsfil nej
- momsfilnummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="slovenia-unique-master-citizen-number"></a>Sloveniens entydige masternummer for borgere

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13 cifre uden mellemrum eller separatortegn

### <a name="pattern"></a>Mønster

13 cifre i det angivne mønster:

- syv cifre, der svarer til fødselsdatoen (DDMMLLL), hvor "LLL" svarer til de sidste tre cifre i fødselsåret
- to cifre, der svarer til fødselsområdet "50"
- Tre cifre svarer til en kombination af køn og serienummer for personer, der fødes på samme dag. 000-499 for mand og 500-999 for kvinde.
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_slovenia_eu_national_id_card` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_slovenia_eu_national_id_card` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_slovenia_eu_national_id_card` indhold, der svarer til mønsteret.

```xml
      <!-- Slovenia Unique Master Citizen Number -->
      <Entity id="68948b27-803d-41e4-adf1-13e05eb541bb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
          <Match idRef="Keywords_slovenia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_slovenia_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega dršfarvejana
- emšo
- enotna maticna številka obcana
- id-kort
- id-nummer
- identifikacijska številka
- identitetskort
- nacionalna id
- nacionalni potni-liste
- nationalt id
- osebna izkaznica
- osebni koda
- osebni-ne
- osebni številka
- personlig kode
- personligt nummer
- personlig numerisk kode
- številka drššjana
- entydigt tal for borgere
- entydigt id-nummer
- entydigt identitetsnummer
- entydigt masternummer for borgere
- entydigt registreringsnummer
- uniqueidentityno #
- uniqueidentityno #


## <a name="south-africa-identification-number"></a>Sydafrikas identifikationsnummer

### <a name="format"></a>Formatér

13 cifre, der kan indeholde mellemrum

### <a name="pattern"></a>Mønster

13 cifre:
- seks cifre i formatet YYMMDD, som er fødselsdatoen
- fire cifre
- en étcifret indikator for indikatoren
- cifret "8" eller "9"
- et ciffer, som er et kontrolsumcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_south_africa_identification_number, der svarer til mønsteret.
- Der er fundet Keyword_south_africa_identification_number nøgleord.
- Kontrolsummet overføres.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identitetskort
- Id
- Identifikation


## <a name="south-korea-resident-registration-number"></a>Sydkoreanske iboende registreringsnummer

### <a name="format"></a>Formatér

13 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

13 cifre:
- seks cifre i formatet YYMMDD, som er fødselsdatoen
- en bindestreg
- et ciffer bestemt efter århundredet og køn
- firecifret fødselsdato
- et ciffer, der bruges til at skelne mellem personer, som de foregående tal er identiske med
- et kontrolcifre.

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_south_korea_resident_number, der svarer til mønsteret.
- Der er fundet Keyword_south_korea_resident_number nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_south_korea_resident_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- Nationalt id-kort
- Borgeres registreringsnummer
- Jumin deungnok beonho
- RRN
- 주민등록번호


## <a name="spain-dni"></a>Spain DNI

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

Otte cifre efterfulgt af ét tegn

### <a name="pattern"></a>Mønster

syv cifre efterfulgt af ét tegn

- otte cifre
- Et valgfrit mellemrum eller en bindestreg
- et checkbogstav (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_spain_eu_DL_and_NI_number_citizen` finder indhold `Func_spain_eu_DL_and_NI_number_foreigner` , der svarer til mønsteret.
- Der er fundet et  `Keywords_spain_eu_national_id_card"` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_spain_eu_DL_and_NI_number_citizen` finder indhold `Func_spain_eu_DL_and_NI_number_foreigner` , der svarer til mønsteret.


```xml
      <!-- Spain DNI -->
      <Entity id="8e6251b9-47b4-40e8-a42b-0f80876be192" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Match idRef="Keywords_spain_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- dni #
- dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- forsikringsnummer
- nationalt id-nummer
- national identitet
- nationalid #
- nationalidno #
- nie #
- nie
- nienúmero #
- número de identificación
- número nacional identidad
- personligt id-nummer
- personlig identitet nej
- entydigt identitetsnummer
- uniqueid #


## <a name="spain-drivers-license-number"></a>Spanien-kørekortnummer

### <a name="format"></a>Formatér

Otte cifre efterfulgt af ét tegn

### <a name="pattern"></a>Mønster

Otte cifre efterfulgt af ét tegn:

- otte cifre
- et ciffer eller bogstav (der er ikke tale om store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_spain_eu_DL_and_NI_number_citizen` finder indhold `Func_spain_eu_DL_and_NI_number_foreigner` , der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_spain_eu_driver's_license_number` fra eller.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_spain_eu_DL_and_NI_number_citizen` finder indhold `Func_spain_eu_DL_and_NI_number_foreigner` , der svarer til mønsteret.

```xml
      <!-- Spain Driver's License Number -->
      <Entity id="d5a82922-b501-4f40-8868-341321146aa2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_spain_eu_driver's_license_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_foreigner" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver ikke s_license_number

- permiso de conducción
- permiso conducción
- licencia de conducir
- licencia conducir
- permiso conducir
- permiso de conducir
- permisos de conducir
- permisos conducir
- carnet conducir
- carnet de conducir
- licencia de manejo
- licencia manejo


## <a name="spain-passport-number"></a>Spaniens pasnummer

### <a name="format"></a>Formatér

en kombination af otte eller ni tegns kombination af bogstaver og tal uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

en kombination af bogstaver og tal på otte eller ni tegn:

- to cifre eller bogstaver
- et ciffer eller bogstav (valgfrit)
- seks cifre

### <a name="checksum"></a>Kontrolsum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_spain_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_spain_eu_passport_number` fra eller.
- Det regulære `Regex_spain_eu_passport_date` udtryk finder dato i formatet DD-MM-YYYY, eller der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_spain_eu_passport_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_passport_number` nøgleord `Keywords_spain_eu_passport_number` fra eller.

```xml
      <!-- Spain Passport Number -->
      <Entity id="d17a57de-9fa5-4e9f-85d3-85c26d89686e" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_spain_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_spain_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_spain_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- libreta pasaporte
- número pasaporte
- españa pasaporte
- números de pasaporte
- número de pasaporte
- números pasaporte
- pasaporte no
- Passeport n°
- n° Passeport
- pasaporte no.
- pasaporte n°
- spain passport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="spain-physical-addresses"></a>Fysiske adresser i Spanien

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Spanien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="spain-social-security-number-ssn"></a>Cpr-nummer (SSN) i Spanien


### <a name="format"></a>Formatér

11-12 cifre

### <a name="pattern"></a>Mønster

11-12 cifre:
- to cifre
- en skråstreg (valgfrit)
- syv til otte cifre
- en skråstreg (valgfrit)
- to cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_spanish_social_security_number, der svarer til mønsteret.
- Kontrolsummet overføres.
- - Der er fundet et  `Keywords_spain_eu_ssn_or_equivalent` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_spanish_social_security_number, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
    <!-- Spain SSN -->
    <Entity id="5df987c0-8eae-4bce-ace7-b316347f3070" patternsProximity="300" recommendedConfidence="85" relaxProximity="true" >
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spanish_social_security_number" />
          <Match idRef="Keywords_spain_eu_ssn_or_equivalent" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spanish_social_security_number" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- ssn
- ssn #
- socialsecurityno
- cpr-nr
- CPR-nummer
- número de la seguridad social


## <a name="spain-tax-identification-number"></a>Moms-id for Spanien

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

syv eller otte cifre og et eller to bogstaver i det angivne mønster

### <a name="pattern"></a>Mønster

Spanske fysiske personer med et spaniens identitetskort:

- otte cifre
- et stort bogstav (store og små bogstaver)

Ikke-boende spaniere uden et spaniens nationalt identitetskort

- et stort bogstav "L" (store og små bogstaver)
- syv cifre
- et stort bogstav (store og små bogstaver)

iboende spaniarder under 14 år uden et spaniens nationalt identitetskort:

- et stort bogstav "K" (store og små bogstaver)
- syv cifre
- et stort bogstav (store og små bogstaver)

En fremmedmands id-nummer

- et stort bogstav , der er "X", "Y" eller "Z" (der er store bogstaver)
- syv cifre
- et stort bogstav (store og små bogstaver)

En fremmed kant uden en fremmeds identifikationsnummer

- et stort bogstav i "M" (store og små bogstaver)
- syv cifre
- et stort bogstav (store og små bogstaver)

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_spain_eu_tax_file_number` finder indhold `Func_spain_eu_DL_and_NI_number_citizen` , der svarer til mønsteret.
- Der er fundet et  `Keywords_spain_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller  `Func_spain_eu_tax_file_number` finder indhold `Func_spain_eu_DL_and_NI_number_citizen` , der svarer til mønsteret.

```xml
      <!-- Spain Tax Identification Number -->
      <Entity id="10f0d113-b0e1-47dc-872a-a4f45b9376a3" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
          <Match idRef="Keywords_spain_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_spain_eu_DL_and_NI_number_citizen" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- cif
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- momsfil nej
- momsfilnummer
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="sql-server-connection-string"></a>SQL Server forbindelsesstreng

### <a name="format"></a>Formatér

Strengen "Bruger-id", "Bruger-id", "uid" eller "UserId" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- strengen "Bruger-id", "Bruger-id", "uid" eller "UserId"
- enhver kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "Adgangskode" eller "pwd", hvor "pwd" ikke indledes med et lille bogstav
- et lighedstegn (=)
- alle tegn, der ikke er et dollartegn ($), procentsymbol (%), større end symbol (>) ved symbol (@), anførselstegn ("), semikolon (;), venstre klammeparentes([) eller venstre kantparentes ({)
- en kombination af 7-128 tegn, der ikke er et semikolon (;), skråstreg (/) eller anførselstegn (")
- et semikolon (;) eller anførselstegn (")

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder CEP_Regex_SQLServerConnectionString, der svarer til mønsteret.
- Der blev CEP_GlobalFilter nøgleord fra denne.
- Det regulære udtryk CEP_PasswordPlaceHolder ikke indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords ikke indhold, der svarer til mønsteret.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- some-password
- somepassword
- secretPassword
- eksempel

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord.

- Adgangskode eller pwd efterfulgt af 0-2 mellemrum, et lighedstegn (=), 0-2 mellemrum og en stjerne (*) -ELLER-
- Adgangskode eller pwd efterfulgt af:
    - Lighedstegn (=)
    - Mindre end (<)
    - Enhver kombination af 1-200 tegn, der er store eller små bogstaver, cifre, en stjerne (*), bindestreg (-), understregning (_) eller mellemrumstegn
    - Større end (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en liste med nøgleord.

- contoso
- fabrikam
- northwind
- sandkasse
- onebox
- localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->com
- s-int.<!--no-hyperlink-->net


## <a name="surgical-procedures"></a>Procedurer, der kan fjerne dig fra den

Denne ubundede navngivne enhed registrerer udtryk, der er relateret til procedurer, som f.eks. *appendectomy*.  Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="sweden-drivers-license-number"></a>Sveriges kørekortnummer

### <a name="format"></a>Formatér

10 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

10 cifre, der indeholder en bindestreg:

- seks cifre
- en bindestreg
- fire cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk  `Regex_sweden_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_eu_driver's_license_number` nøgleord `Keywords_sweden_eu_driver's_license_number` fra eller.

```xml
      <!-- Sweden Driver's License Number -->
      <Entity id="70088720-90dd-47f5-805e-5525f3567391" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_sweden_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver ikke s_license_number

- ajokortti
- permis de conducere
- ajokortin numero
- kuljettajat lic.
- drivere lic.
- körkort
- numèrul permisului de conducere
-  שאָפער דערלויבעניש נומער
- förare lic.
-  דריווערס דערלויבעניש
- körkortsnummer


## <a name="sweden-national-id"></a>Sveriges nationale id

### <a name="format"></a>Formatér

10 eller 12 cifre og en valgfri afgrænser

### <a name="pattern"></a>Mønster

10 eller 12 cifre og en valgfri afgrænser:
- To cifre (valgfrit)
- Seks cifre i datoformatet YYMMDD
- afgrænser for "-" eller "+" (valgfrit)
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_swedish_national_identifier` indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_swedish_national_identifier` nøgleord fra
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_swedish_national_identifier` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.


```xml
    <!-- Sweden National ID -->
    <Entity id="f69aaf40-79be-4fac-8f05-fd1910d272c8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_swedish_national_identifier" />
        <Match idRef="Keywords_swedish_national_identifier" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_swedish_national_identifier" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id nej
- id-nummer
- id #
- identifikationsnr.
- id-nummer
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- identitetsdokument
- identitet nej
- identitetsnummer
- id-nummer
- personligt id
- personnummer #
- personnummer
- skatteidentifikationsnummer


## <a name="sweden-passport-number"></a>Sveriges pasnummer

### <a name="format"></a>Formatér

otte cifre

### <a name="pattern"></a>Mønster

otte fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- det regulære udtryk Regex_sweden_passport_number indhold, der svarer til mønsteret.
- et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_sweden_passport` bliver fundet.
- Det regulære `Regex_sweden_eu_passport_date` udtryk finder en dato i formatet DD MMM/MMM JY (01 JAN/JAN 12), `Keywords_eu_passport_date` eller der er fundet et nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- det regulære udtryk Regex_sweden_passport_number indhold, der svarer til mønsteret.
- et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_sweden_passport` bliver fundet.


```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- registreringskort for hele din tilmelding
- g3-behandlingsgebyrer
- flere indtastning
- Numéro de passeport
- passeport n °
- passeport non
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- bestået nr
- visa visa
- visa visas
- enkelt indtastning
- sverige pass
- visa-krav
- visa processing
- visa-type

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato


## <a name="sweden-physical-addresses"></a>Fysiske adresser i Sverige

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Sverige. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="sweden-tax-identification-number"></a>Moms-id i Sverige

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10 cifre og et symbol i det angivne mønster

### <a name="pattern"></a>Mønster

10 cifre og et symbol:

- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- et plustegn eller minustegn
- Tre cifre, der gør identifikationsnummeret entydigt, hvor:
  - for de tal, der er udstedt før 1990, skal det syvende og ottende ciffer identificere fødselsland eller fødeland
  - Cifret i niende position angiver køn efter enten ulige for mand eller endda for kvinde
- et kontrolcifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_sweden_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_sweden_eu_tax_file_number` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_sweden_eu_tax_file_number` indhold, der svarer til mønsteret.

```xml
      <!-- Sweden Tax Identification Number -->
      <Entity id="139acba0-a5bc-4fbb-876d-f7a493ae8a40" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Match idRef="Keywords_sweden_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_sweden_eu_tax_file_number" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_sweden_eu_telephone_number" />
            <Match idRef="Keywords_sweden_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- personligt id-nummer
- personnummer
- skatt id nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- Sverige tin
- momsfil
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsnummer
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="swift-code"></a>SWIFT-kode

### <a name="format"></a>Formatér

fire bogstaver efterfulgt af 5-31 bogstaver eller tal

### <a name="pattern"></a>Mønster

fire bogstaver efterfulgt af 5-31 bogstaver eller tal:
- Bankkode på fire bogstaver (der er ikke store og små bogstaver)
- et valgfrit mellemrum
- 4-28 bogstaver eller cifre (Basic Bank Account Number (BBAN))
- et valgfrit mellemrum
- et til tre bogstaver eller tal (resten af BBAN)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_swift, der svarer til mønsteret.
- Der er fundet Keyword_swift nøgleord.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_swift"></a>Keyword_swift

- den internationale standardiseringsorganisation 9362
- iso 9362
- iso9362
- swift #
- swiftkode
- swiftnummer
- swiftroutingnumber
- swift-kode
- swift-nummer #
- swift-registreringsnummer
- bic-nummer
- bic-kode
- bic #
- bic #
- bank-id-kode
- Organisation internationale de normalisation 9362
- rapide #
- code SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- # <a name="bic"></a>BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT-番号
- BIC-番号
- BIC-コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード


## <a name="switzerland-physical-addresses"></a>Schweiz fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Schweiz. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="switzerland-ssn-ahv-number"></a>Schweiz SSN AHV-nummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

13-cifret tal

### <a name="pattern"></a>Mønster

13-cifret tal:

- Tre cifre – 756
- en valgfri prik
- fire cifre
- en valgfri prik
- fire cifre
- en valgfri prik
- to cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_swiss_social_security_number_ahv, der svarer til mønsteret.
- Der er fundet Keywords_swiss_social_security_number_ahv nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_swiss_social_security_number_ahv, der svarer til mønsteret.

```xml
      <!-- Swiss SSN AHV Number -->
      <Entity id="277cfa4b-6eaa-4a1b-9492-099dec849971" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
          <Match idRef="Keywords_swiss_social_security_number_ahv" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_swiss_social_security_number_ahv" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- ahv
- ssn
- pid
- forsikringsnummer
- personalidno #
- CPR-nummer
- personligt id-nummer
- nej til personlig identifikation.
- insuranceno #
- uniqueidno #
- entydig identifikationsnr.
- serienummer
- personlig identitet, ingen versicherungsnummer
- identifikationsnummer
- einzigartige identität nifarvet
- soalolversicherungsnummer
- id for identifikation af personale
- numéro de sécurité sociale


## <a name="taiwan-national-identification-number"></a>Taiwansk nationalt identifikationsnummer

### <a name="format"></a>Formatér

et bogstav (på engelsk) efterfulgt af ni cifre

### <a name="pattern"></a>Mønster

et bogstav (på engelsk) efterfulgt af ni cifre:
- et bogstav (på engelsk, der er ikke tale om store og små bogstaver)
- cifferet "1" eller "2"
- otte cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_taiwanese_national_id, der svarer til mønsteret.
- Der er fundet Keyword_taiwanese_national_id nøgleord.
- Kontrolsummet overføres.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_taiwanese_national_id, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
<!-- Taiwanese National ID -->
<Entity id="4C7BFC34-8DD1-421D-8FB7-6C6182C2AF03" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_taiwanese_national_id" />
          <Match idRef="Keyword_taiwanese_national_id" />
      </Pattern>
       <Pattern confidenceLevel="75">
         <IdMatch idRef="Func_taiwanese_national_id" />
       </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_taiwan_national_id"></a>Keyword_taiwan_national_id

- 身份證字號
- 身份證
- 身份證號碼
- 身份證號
- 身分證字號
- 身分證
- 身分證號碼
- 身份證號
- 身分證統一編號
- 國民身分證統一編號
- 簽名
- 蓋章
- 簽名或蓋章
- 簽章


## <a name="taiwan-passport-number"></a>Taiwan-pasnummer

### <a name="format"></a>Formatér

- biometrisk pasnummer: ni cifre
- ikke-biometrisk pasnummer: ni cifre

### <a name="pattern"></a>Mønster
biometrisk pasnummer:
- tegnet "3"
- otte cifre

ikke-biometrisk pasnummer:
- ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_taiwan_passport finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_taiwan_passport nøgleord.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC-pasnummer
- Pasnummer
- Pasnr.
- Pasnr
- Pas #
- 护照
- 中華民國護照
- Zhōnghuá Mínguó hùzhào


## <a name="taiwan-resident-certificate-arctarc-number"></a>Taiwan-iboende certifikat (ARC/TARC) nummer

### <a name="format"></a>Formatér

10 bogstaver og tal

### <a name="pattern"></a>Mønster

10 bogstaver og tal:
- To bogstaver (der er ikke tale om store og små bogstaver)
- otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Udtrykket for det Regex_taiwan_resident_certificate finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_taiwan_resident_certificate nøgleord.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Iboende certifikat
- Resident Cert
- Resident Cert.
- Identifikationskort
- Udboende certifikat
- ARC
- Taiwan Area Resident Certificate
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證


## <a name="thai-population-identification-code"></a>Identifikationskode for den thailandske befolkning

### <a name="format"></a>Formatér

13 cifre

### <a name="pattern"></a>Mønster

13 cifre:
- første ciffer er ikke nul eller ni
- 12 cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Thai_Citizen_Id, der svarer til mønsteret.
- Der er fundet Keyword_Thai_Citizen_Id nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Thai_Citizen_Id, der svarer til mønsteret.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- Id-nummer
- Id-nummer
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>Tyrkiets nationale identifikationsnummer

### <a name="format"></a>Formatér

11 cifre

### <a name="pattern"></a>Mønster

11 cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Turkish_National_Id, der svarer til mønsteret.
- Der er fundet Keyword_Turkish_National_Id nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_Turkish_National_Id, der svarer til mønsteret.

```xml
<!-- Turkish National Identity -->
-<Entity id="fb621f20-3876-4cfc-acec-8c8e73ca32c7" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Turkish_National_Id"/>
      <Match idRef="Keyword_Turkish_National_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Turkish_National_Id"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık no


## <a name="turkey-physical-addresses"></a>Tyrkiets fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra Tyrkiet. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="types-of-medication"></a>Typer af medicin

Denne ubundede navngivne enhed registrerer medicinnavne, *f.eks.*  Det understøtter kun engelske vilkår. Det er også inkluderet i [Alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) bundtet navngivet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Høj


## <a name="uk-drivers-license-number"></a>Storbritannien kørekortnummer

### <a name="format"></a>Formatér

Kombination af 18 bogstaver og cifre i det angivne format

### <a name="pattern"></a>Mønster

18 bogstaver og tal:
- Fem bogstaver (der er ikke tale om store og små bogstaver) eller cifret "9" i stedet for et bogstav.
- Et ciffer.
- Fem cifre i datoformatet MMDDY for fødselsdato. Det syvende tegn stiger med 50, hvis driveren er kvinde; for eksempel 51 til 62 i stedet for 01 til 12.
- To bogstaver (der er ikke store bogstaver) eller cifret "9" i stedet for et bogstav.
- Fem cifre.

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_uk_drivers_license` indhold, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_driver's_license_number` nøgleord fra.
- Kontrolsummet overføres.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_uk_drivers_license` indhold, der svarer til mønsteret.
- Kontrolsummet overføres.

```xml
    <!-- U.K. Driver's License Number -->
    <Entity id="f93de4be-d94c-40df-a8be-461738047551" patternsProximity="300" recommendedConfidence="75" relaxProximity="true" >
      <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_uk_drivers_license" />
          <Match idRef="Keywords_eu_driver's_license_number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_uk_drivers_license" />
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver ikke s_license_number

- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- kørekort
- køre licens
- køre licenser
- kørekort
- driverlicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- køre lic
- køre på
- kørekort
- køre licenser
- kørekort
- kørelicenser
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driver'licenser
- køre' lic
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- driverens udsnitsrækkefølge
- driverens udsnit
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- kørekort
- dl #
- dls #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- kørekort #
- køre licens #
- køre licenser #
- driverlicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- køre lic #
- køre på #
- kørekort #
- køre licenser #
- kørekort #
- kørelicenser #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driver'licenser #
- køre' lic #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- driverens udsnitsrækkefølge #
- driverens udsnit #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørekort #
- kørelicens 
- køre licens
- dlno #
- ler lic
- ler licen
- køre licens
- inddel licenser
- licens til 1. licens
- 3655-licenser
- driver
- køre på
- kørekort
- kørende lic
- kørende kørekort
- køre licenser
- kørelicens
- køre licenser
- køretilladelse
- dl no
- dlno
- dl-nummer


## <a name="uk-electoral-roll-number"></a>Storbritannien roll number (udrullet)

### <a name="format"></a>Formatér

To bogstaver efterfulgt af 1-4 cifre

### <a name="pattern"></a>Mønster

To bogstaver (der er ikke store bogstaver) efterfulgt af 1-4 tal

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regulære udtryk finder Regex_uk_electoral, der svarer til mønsteret.
- Der er fundet Keyword_uk_electoral nøgleord.

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- byrådsmøde
- skema
- register over tilmelding
- roll til udrulning


## <a name="uk-national-health-service-number"></a>Storbritannien nationalt sundhedstjenestenummer

### <a name="format"></a>Formatér

10-17 cifre adskilt af mellemrum

### <a name="pattern"></a>Mønster

10-17 cifre:
- enten 3 eller 10 cifre
- et mellemrum
- Tre cifre
- et mellemrum
- fire cifre

### <a name="checksum"></a>Kontrolsum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_uk_nhs_number, der svarer til mønsteret.
- Et af følgende er sandt:
    - Der er fundet Keyword_uk_nhs_number nøgleord.
    - Der er fundet Keyword_uk_nhs_number1 nøgleord.
    - Der er fundet Keyword_uk_nhs_number_dob nøgleord.
- Kontrolsummet overføres.

```xml
<!-- U.K. NHS Number -->
<Entity id="3192014e-2a16-44e9-aa69-4b20375c9a78" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nhs_number" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_nhs_number" />
          <Match idRef="Keyword_uk_nhs_number1" />
          <Match idRef="Keyword_uk_nhs_number_dob" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- national sundhedstjeneste
- nhs
- health services authority
- sundhedscenter

#### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- patient-id
- patientidentifikation
- patientnr.
- patientnummer

#### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Fødselsdag
- Fødselsdato


## <a name="uk-national-insurance-number-nino"></a>Storbritannien nationalt forsikringsnummer (NINO)

Denne følsomme oplysningstype er medtaget i den følsomme type af EU-national identifikationsnummer. Den fås også som et enkeltstående objekt af typen følsomme oplysninger.

### <a name="format"></a>Formatér

syv tegn eller ni tegn adskilt af mellemrum eller tankestreger

### <a name="pattern"></a>Mønster

to mulige mønstre:

- to bogstaver (gyldige NINOer bruger kun visse tegn i dette præfiks, som dette mønster validerer. Der anvendes ikke store og små bogstaver)
- seks cifre
- enten 'A', 'B', 'C' eller 'D' (ligesom præfikset er det kun visse tegn, der er tilladt i suffikset; ikke mellem store og små bogstaver)

ELLER

- to bogstaver
- et mellemrum eller bindestreg
- to cifre
- et mellemrum eller bindestreg
- to cifre
- et mellemrum eller bindestreg
- to cifre
- et mellemrum eller bindestreg
- enten 'A', 'B', 'C' eller 'D'

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_uk_nino, der svarer til mønsteret.
- Der er fundet Keyword_uk_nino nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_uk_nino, der svarer til mønsteret.

```xml
    <!-- U.K. NINO -->
    <Entity id="16c07343-c26f-49d2-a987-3daf717e94cc" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_uk_nino" />
        <Match idRef="Keyword_uk_nino" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_uk_nino" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- nationalt forsikringsnummer
- nationalt forsikringsbidrag
- lov om beskyttelse
- forsikring
- CPR-nummer
- forsikringsprogram
- medicinsk anvendelse
- socialforsikring
- lægeundersøgelse
- social sikring
- Storbritannien
- NI-nummer
- NI-nej.
- NI #
- NI #
- forsikring #
- forsikringsnummer
- nationalinsurance #
- nationalinsurancenumber


## <a name="uk-physical-addresses"></a>Storbritannien fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre, der er relateret til fysiske adresser fra Storbritannien. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem



## <a name="uk-unique-taxpayer-reference-number"></a>Storbritannien Entydigt skatteyders referencenummer

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

10 cifre uden mellemrum og separatortegn


### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder  `Func_uk_eu_tax_file_number` indhold, der svarer til mønsteret.
- Der er fundet et  `Keywords_uk_eu_tax_file_number` nøgleord fra.

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- momsnummer
- momsfil
- moms-id
- momsidentifikation
- moms-id
- momsnr. #
- momsnr.
- momsregistreringsnummer
- taxd #
- taxdno #
- kørenummer #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tinnr
- tin #


## <a name="us-bank-account-number"></a>AMERIKANSK bankkontonummer

### <a name="format"></a>Formatér

6-17 cifre

### <a name="pattern"></a>Mønster

6-17 fortløbende cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Det regulære udtryk Regex_usa_bank_account_number indhold, der svarer til mønsteret.
- Der er fundet Keyword_usa_Bank_Account nøgleord.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Checkkontonummer
- Checkkonto
- Checkkonto #
- Checkkontonummer
- Checkkonto #
- Checkkontonr.
- Checkkontonr.
- Bankkontonummer
- Bankkonto #
- Bankkontonummer
- Bankkonto #
- Bankkontonr.
- Bankkontonr.
- Opsparingskontonummer
- Opsparingskonto.
- Opsparingskonto #
- Opsparingskontonummer
- Opsparingskonto #
- Opsparingskontonr.
- Opsparingskontonr.
- Debetkontonummer
- Debetkonto
- Debetkonto #
- Debetkontonummer
- Debetkonto #
- Debetkontonr.
- Debetkontonr.


## <a name="us-drivers-license-number"></a>USA kørekortnummer

### <a name="format"></a>Formatér

Afhænger af staten

### <a name="pattern"></a>Mønster

afhænger af staten, f.eks. New York:
- ni cifre formateret som ddd ddd ddd matcher.
- ni cifre som ddddddddd stemmer ikke overens.

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_york_drivers_license_number, der svarer til mønsteret.
- Der er fundet et nøgleord Keyword_[state_name]_drivers_license_name nøgleord.
- Der er fundet Keyword_us_drivers_license nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_new_york_drivers_license_number, der svarer til mønsteret.
- Der er fundet et nøgleord Keyword_[state_name]_drivers_license_name nøgleord.
- Der er fundet Keyword_us_drivers_license_abbreviations nøgleord.
- Der er ikke fundet Keyword_us_drivers_license nøgleord.

```xml
<Entity id="dfeb356f-61cd-459e-bf0f-7c6d28b458c6 patternsProximity="300">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license" />
    </Pattern>
    <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_new_york_drivers_license_number" />
        <Match idRef="Keyword_new_york_drivers_license_name" />
        <Match idRef="Keyword_us_drivers_license_abbreviations" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_us_drivers_license" />
        </Any>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- Id
- ID'er
- DL #
- DLS #
- CDL #
- CDLS #
- Id #
- ID'er #
- Id-nummer
- Id-numre
- LIC
- LIC #

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørelicenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Køre Lic
- Køre kørekort
- Kørekort
- Kørekort
- Køre'Lic
- Kørekort
- Kørekort
- Køre'licenser
- Køre' lic
- Køre' kørekort
- Kørekort
- Køre' licenser
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- Kørekort
- id-nummer
- id-numre
- identifikation #
- id-kort
- id-kort
- identifikationskort
- identifikationskort
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørelicenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Køre Lic #
- Køre kørekort #
- Kørekort #
- Kørekort #
- Køre'Lic #
- Kørekort #
- Kørekort #
- Køre'licenser #
- Køre' lic #
- Køre' kørekort #
- Kørekort #
- Køre' licenser #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- Kørekort #
- id-kort #
- id-kort #
- identifikationskort #
- identifikationskort #


#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- forkortelse for stat (f.eks. "NY")
- statens navn (f.eks. "New York")


## <a name="us-individual-taxpayer-identification-number-itin"></a>USA's skatteyders id-nummer (ITIN)

### <a name="format"></a>Formatér

ni cifre, der starter med et "9" og indeholder et "7" eller "8" som det fjerde ciffer, eventuelt formateret med mellemrum eller tankestreger

### <a name="pattern"></a>Mønster

formateret:
- cifret "9"
- to cifre
- et mellemrum eller bindestreg
- et "7" eller "8"
- et ciffer
- et mellemrum eller bindestreg
- fire cifre

uformateret:
- cifret "9"
- to cifre
- et "7" eller "8"
- fem cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_formatted_itin, der svarer til mønsteret.
- Der er fundet Keyword_itin nøgleord.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_unformatted_itin, der svarer til mønsteret.
- Der er fundet Keyword_itin nøgleord.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_formatted_itin eller Func_unformatted_itin, der svarer til mønsteret.

```xml
    <!-- U.S. Individual Taxpayer Identification Number (ITIN) -->
    <Entity id="e55e2a32-f92d-4985-a35d-a0b269eb687b" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_formatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_itin" />
        <Match idRef="Keyword_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_formatted_itin" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_unformatted_itin" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_itin"></a>Keyword_itin

- skatteyder
- moms-id
- skatteidentifikation
- itin
- i.t.i.n.
- ssn
- tin
- social sikring
- skatte betalende
- itins
- taxd
- individuel skatteyder


## <a name="us-physical-addresses"></a>Amerikanske fysiske adresser

Denne ubundede navngivne enhed registrerer mønstre relateret til fysiske adresser fra USA. Den er også inkluderet i alle [fysiske adresser, der er](#all-physical-addresses) bundtet med navnet enhed SIT.

### <a name="confidence-level"></a>Tillidsniveau

Mellem


## <a name="us-social-security-number-ssn"></a>USA CPR-nummer (SSN)

### <a name="format"></a>Formatér

ni cifre, som kan være i et formateret eller uformateret mønster

> [!NOTE]
> Hvis SSN er udstedt før midten af 2011, har det en stærk formatering, hvor visse dele af tallet skal falde inden for visse områder for at være gyldigt (men der er ingen kontrolsum).

### <a name="pattern"></a>Mønster

fire funktioner ser efter SSN'er i fire forskellige mønstre:
- Func_ssn finder SSN'er med en stærk formatering før 2011, der er formateret med stiplede tankestreger eller mellemrum (ddd-dd-dddd ELLER ddd dd dddd)
- Func_unformatted_ssn finder SSN'er med en stærk formatering (før 2011), der er formateret som ni fortløbende cifre (ddddddddd)
- Func_randomized_formatted_ssn finder SSN'er efter 2011, der er formateret med tankestreger eller mellemrum (ddd-dd-dddd ELLER ddd dd dddd)
- Func_randomized_unformatted_ssn finder SSN'er efter 2011, der er formateret som ni fortløbende cifre (ddddddddd)

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder `Func_ssn` indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_ssn` nøgleord fra.

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen "Func_unformatted_ssn" finder indhold, der svarer til mønsteret.
- Der er fundet et `Keyword_ssn` nøgleord fra.

En DLP-politik har lav tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen eller `Func_randomized_formatted_ssn` finder indhold `Func_randomized_unformatted_ssn` , der svarer til mønsteret.
- Der er fundet et `Keyword_ssn` nøgleord fra.


```xml
<!-- U.S. Social Security Number (SSN) -->
  <Entity id="a44669fe-0d48-453d-a9b1-2cc83f2cba77" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Func_randomized_formatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
      <Pattern confidenceLevel="55">
        <IdMatch idRef="Func_randomized_unformatted_ssn" />
        <Match idRef="Keyword_ssn" />
      </Pattern>
  </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_ssn"></a>Keyword_ssn

- SSA-nummer
- CPR-nummer
- social sikring #
- social sikring #
- cpr-nr
- Cpr-sikkerhed #
- Soc Sec
- SSN
- SSNS
- SSN #
- SS #
- SSID


## <a name="usuk-passport-number"></a>USA/Storbritannien pasnummer

### <a name="format"></a>Formatér

ni cifre

### <a name="pattern"></a>Mønster

- et bogstav eller et tal
- otte cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_usa_uk_passport, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keywords_uk_eu_passport_number` fra eller.
- Der er fundet et `Keywords_eu_passport_date` nøgleord fra

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Funktionen finder Func_usa_uk_passport, der svarer til mønsteret.
- Der er fundet et `Keywords_eu_passport_number` nøgleord `Keywords_uk_eu_passport_number` fra eller.

```xml
    <!-- U.S. / U.K. Passport Number -->
    <Entity id="178ec42a-18b4-47cc-85c7-d62c92fd67f8" patternsProximity="300" recommendedConfidence="75">
       <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Match idRef="Keywords_eu_passport_date" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_usa_uk_passport" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_uk_eu_passport_number" />
          </Any>
        </Pattern>
    </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- pas #
- pas #
- pas-id
- pas
- pasnr
- pasnr.
- pasnummer
- pasnummer
- pasnumre
- pasnumre

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- britisk pas
- uk passport


## <a name="ukraine-passport-domestic"></a>Ukraines pasland

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

ni cifre

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex-Regex_Ukraine_Passport_Domestic finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_Ukraine_Passport_Domestic nøgleord.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- ukraine pas
- pasnummer
- pasnr.
- паспорт України
- номер паспорта
- персональний


## <a name="ukraine-passport-international"></a>Ukraines pas (internationale pas)

Denne type af følsomme oplysninger er kun tilgængelig til brug i:
- Politikker til forebyggelse af datatab
- politikker for overholdelse af regler og standarder i kommunikation
- informationsstyring
- datastyring
- Microsoft Defender til skyapps

### <a name="format"></a>Formatér

alfanumerisk mønster på otte tegn

### <a name="pattern"></a>Mønster

otte-tegns alfanumeriske mønster:
- to bogstaver eller tal
- seks cifre

### <a name="checksum"></a>Kontrolsum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellemlangt tillid til, at den har registreret denne type af følsomme oplysninger, inden for en afstand af 300 tegn:
- Regex-Regex_Ukraine_Passport_International finder indhold, der svarer til mønsteret.
- Der er fundet Keyword_Ukraine_Passport_International nøgleord.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Nøgleord

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- ukraine pas
- pasnummer
- pasnr.
- паспорт України
- номер паспорта


