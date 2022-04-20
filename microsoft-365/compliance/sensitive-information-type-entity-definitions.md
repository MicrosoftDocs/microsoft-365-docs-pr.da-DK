---
title: Enhedsdefinitioner for type af følsomme oplysninger
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
description: Der er mange følsomme oplysningstyper, der er klar til brug i dine DLP-politikker. I denne artikel vises alle disse typer følsomme oplysninger, og du kan se, hvad en DLP-politik søger efter, når hver type registreres.
ms.openlocfilehash: 6074082812853469e0513d67ec68519eb2a89563
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64970653"
---
# <a name="sensitive-information-type-entity-definitions"></a>Enhedsdefinitioner for type af følsomme oplysninger

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I denne artikel vises alle objektdefinitioner for følsomme oplysninger. Hver definition viser, hvad en DLP-politik søger efter for at registrere hver type. Du kan få mere at vide om typer af følsomme oplysninger under [Typer af følsomme oplysninger](sensitive-information-type-learn-about.md)

> [!NOTE]
> Tilknytning af konfidensniveau (høj/mellem/lav) med tal for nøjagtighed (numerisk værdi på 1 til 100)
>
> - Lav konfidens: 65 eller under
> - Medium konfidens: 75
> - Høj genkendelsessikkerhed: 85

## <a name="aba-routing-number"></a>ABA-routingnummer

### <a name="format"></a>Format

ni cifre, der kan være i et formateret eller uformateret mønster

### <a name="pattern"></a>Mønster

- to cifre i intervallet 00-12, 21-32, 61-72 eller 80
- to cifre
- en valgfri bindestreg
- fire cifre
- en valgfri bindestreg
- et ciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_aba_routing finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_ABA_Routing.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_aba_routing finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_aba_routing"></a>Keyword_aba_routing

- aba-nummer
- Aba #
- Aba
- abarouting #
- abaroutingnumber
- americanbankassociationrouting #
- americanbankassociationroutingnumber
- bankrouting #
- bankroutingnumber
- Routing #
- routingnr.
- routingnummer
- routing transitnummer
- Routing #
- HØJRE MOD HØJRE

## <a name="all-full-names"></a>Alle fulde navne

Alle fulde navne er et bundtet navngivet objekt. Den registrerer fulde navne for personer fra alle understøttede lande/områder, som omfatter Australien, Kina, Japan, USA og lande i EU. Brug dette SIT til at registrere alle mulige forekomster af fulde navne.

### <a name="format"></a>Format

Forskellige.

### <a name="pattern"></a>Mønster

Forskellige.

### <a name="checksum"></a>Checksum

Nej.

### <a name="description"></a>Beskrivelse

Dette navngivne objekt SIT matcher personlige navne, som et menneske ville identificere som et navn med høj genkendelsessikkerhed. Hvis der f.eks. findes en streng, der består af et givet navn og efterfølges af et familienavn, oprettes der et match med høj genkendelsessikkerhed. Der bruges tre primære ressourcer:

- En ordbog med givne navne.
- En ordbog med familienavne.
- Mønstre for, hvordan navne dannes.

De tre ressourcer er forskellige for hvert land.  Strengene *Olivia Wilson* udløser et match. Almindelige givne/familienavne får en højere genkendelsessikkerhed end sjældnere navne. Mønsteret tillader dog også delvise matches. Hvis der findes et givent navn fra ordbogen, og det efterfølges af et familienavn, der ikke findes i ordbogen, udløses der et delvist match. For eksempel ville *Tomas Richard* udløse en delvis match. Delvise matches får lavere genkendelsessikkerhed.

Hertil kommer, at mønstre, som et menneske ville se som tegn på navne, også matches med passende tillid. Som *O. Wilson*, *O.P. Wilson*, *Dr. O. P. Wilson*, *Wilson, O.P.* eller *T. Richard, Jr.* ville være kampe.

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

Alle medicinske vilkår og betingelser er en samlet navngiven enhed, der registrerer medicinske vilkår og medicinske tilstande. Den registrerer kun engelske ord. Brug dette SIT til at registrere alle mulige match af medicinske vilkår og betingelser.

### <a name="format"></a>Format

Ordbog

### <a name="pattern"></a>Mønster

Ordbog

### <a name="checksum"></a>Checksum

Nej

### <a name="description"></a>Beskrivelse

Dette bundtede navngivne objekt matcher tekst, der omtaler medicinske tilstande, som findes i udvalgte ordbøger. Der er én udvalgt ordbog pr. understøttet sprog. Ordbøgerne er fra mange internationale medicinske ressourcer. Ordbøgerne omfatter så mange medicinske tilstande som muligt uden at risikere et stort antal falske positiver. Hver post indeholder de forskellige formularer, som en enkelt betingelse ofte skrives i for at sikre dækning, f.eks.:

- *TB*
- *Tuberkulose*
- *phthisis pulmonalis*

### <a name="contains"></a>Indeholder

Dette bundtede navngivne objekt SIT indeholder disse individuelle SIT'er.

- Vilkår for blodprøve
- Typer af medicin
- Sygdomme
- Generiske medicinnavne
- Nedskrivninger er opført i USA handicap evaluering under social sikring
- Testbetingelser for laboratorie
- Livsstil, der er relateret til medicinske tilstande
- Medicinske specialiteter
- Kirurgiske procedurer
- Navne på mærkemedicin

## <a name="all-physical-addresses"></a>Alle fysiske adresser

Alle fysiske adresser er et samlet objekt SIT, som registrerer mønstre, der er relateret til fysiske adresser fra alle understøttede lande/områder.

### <a name="format"></a>Format

Forskellige

### <a name="pattern"></a>Mønster

Forskellige

### <a name="checksum"></a>Checksum

Nej

### <a name="description"></a>Beskrivelse

Matchning af gadeadresser er designet til at matche strenge, som et menneske ville identificere som en adresse. Det gør den ved at bruge flere primære ressourcer:

- En ordbog over bosættelser, amter og områder.
- En ordbog over gadesuffikser, f.eks. Road, Street eller Avenue.
- Mønstre for postnumre.
- Mønstre for adresseformater.

Ressourcerne er forskellige for hvert land. De primære ressourcer er mønstre for adresseformater, der bruges i et bestemt land. Der vælges forskellige formater for at sikre, at så mange adresser som muligt matches. Disse formater giver fleksibilitet, f.eks. kan en adresse udelade postnummeret eller udelade et bynavn eller have en gade uden gadesuffiks. I alle tilfælde bruges sådanne matches til at øge tilliden til kampen.

Mønstrene er designet til at matche individuelle adresser, ikke generiske placeringer. Så strenge som *Redmond, WA 98052* eller *Main Street, Vil Albuquerque* ikke blive matchet.

### <a name="contains"></a>Indeholder

Dette bundtede navngivne sit-objekt indeholder disse individuelle SIT'er:

- Fysiske adresser i Australien
- Fysiske adresser i Østrig
- Fysiske adresser i Belgien
- Fysiske adresser i Brasilien
- Fysiske adresser for Bulgarien
- Fysiske adresser i Canada
- Fysiske adresser for Kroatien
- Fysiske adresser for Cypern
- Fysiske adresser for Tjekkiet
- Fysiske adresser i Danmark
- Fysiske adresser i Estland
- Fysiske adresser i Finland
- Fysiske adresser i Frankrig
- Fysiske adresser i Tyskland
- Fysiske adresser for Grækenland
- Fysiske adresser til Ungarn
- Fysiske adresser på Island
- Fysiske adresser for Irland
- Fysiske adresser for Italien
- Letlands fysiske adresser
- Fysiske adresser i Liechtenstein
- Fysiske adresser for Litauen
- Fysiske adresser i Luxembourg
- Fysiske adresser på Malta
- Fysiske adresser i Nederlandene
- Fysiske adresser for New Zealand
- Fysiske adresser i Norge
- Fysiske adresser i Polen
- Fysiske adresser i Portugal
- Fysiske adresser i Rumænien
- Fysiske adresser i Slovakiet
- Fysiske adresser i Slovenien
- Fysiske adresser i Spanien
- Fysiske adresser i Sverige
- Fysiske adresser i Schweiz
- Fysiske adresser for Tyrkiet
- Fysiske adresser i Storbritannien
- USA fysiske adresser

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

## <a name="argentina-national-identity-dni-number"></a>Argentinas nationale identitet (DNI) nummer

### <a name="format"></a>Format

Otte cifre med eller uden punktummer

### <a name="pattern"></a>Mønster

Otte cifre:

- to cifre
- en valgfri periode
- tre cifre
- en valgfri periode
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
- cedula
- cédula
- Dni
- documento nacional de identidad
- documento número
- documento numero
- registro nacional de las personas
- rnp

## <a name="argentina-unique-tax-identification-key-cuitcuil"></a>Argentinas entydige skatteidentifikationsnøgle (CUIT/CUIL)

### <a name="format"></a>Format

11 cifre med bindestreg

### <a name="pattern"></a>Mønster

11 cifre med en tankestreg:

- to cifre i 20, 23, 24, 27, 30, 33 eller 34
- en bindestreg (-)
- otte cifre
- en bindestreg (-)
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_Argentina_Unique_Tax_Key` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_Argentina_Unique_Tax_Key` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_Argentina_Unique_Tax_Key` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_argentina_unique_tax_key"></a>Keyword_Argentina_Unique_Tax_Key

- Clave Unica de Identificacion Tributaria
- CUIT
- entydig kode for identifikation af arbejde
- Clave Única de Identificación Tributaria
- entydig kode til identifikation af arbejde
- CUIL
- Entydig nøgle til momsidentifikation
- Entydig nøgle til identifikation af arbejde
- Entydig nøgle til identifikation af arbejdskraft
- Entydig arbejdsidentifikationskode
- Entydig arbejdsidentifikationskode
- Entydig nøgle til arbejdsidentifikation
- Entydig nøgle til arbejdsidentifikation
- Entydig kode for momsidentifikation
- Entydig nøgle til skatteidentifikation
- Entydig arbejdsidentifikationskode
- Entydig kode for identifikation af arbejdskraft
- Entydig nøgle til identifikation af arbejdskraft
- Entydig nøgle til identifikation af arbejdskraft
- moms-id
- taxID #
- taxId
- taxidnumber
- momsnummer
- skattenr.
- Skat #
- Skat #
- skatteborger-id
- skatteborgernummer
- skatteborger ingen
- Skatteyderne #
- Skatteyderne #
- skatte-id
- momsidentifikation
- Número de Identificación Fiscal
- número de contribuyente

## <a name="australia-bank-account-number"></a>Australiens bankkontonummer

### <a name="format"></a>Format

6 til 10 cifre med eller uden et forgreningsnummer for bankstaten

### <a name="pattern"></a>Mønster

Kontonummeret er 6 til 10 cifre.

Forgreningsnummeret for den australske bankstat:

- tre cifre
- en bindestreg
- tre cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_australia_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_australia_bank_account_number.
- Det regulære udtryk Regex_australia_bank_account_number_bsb finder indhold, der svarer til mønsteret.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_australia_bank_account_number finder indhold, der svarer til mønsteret.

- Der blev fundet et nøgleord fra Keyword_australia_bank_account_number.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- swift bankkode
- korrespondentbank
- Grundvalutaen
- usa-konto
- holderadresse
- bankadresse
- informationskonto
- pengeoverførsler
- Bankgebyrer
- bankoplysninger
- bankoplysninger
- fulde navne
- Iaea

## <a name="australia-business-number"></a>Australiens forretningsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 cifre med valgfri afgrænsere

### <a name="pattern"></a>Mønster

11 cifre med valgfri afgrænsere:

- to cifre
- en valgfri bindestreg eller et mellemrum
- tre cifre
- en valgfri bindestreg eller et mellemrum
- tre cifre
- en valgfri bindestreg eller et mellemrum
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_australian_business_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_australian_business_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_australian_business_number finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australiens forretningsnr.
- forretningsnummer
- Abn #
- Businessid #
- firma-id
- Abn
- businessno #

## <a name="australia-company-number"></a>Australiens firmanummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

ni cifre med afgrænsere

### <a name="pattern"></a>Mønster

ni cifre med afgrænsere:

- tre cifre
- et mellemrum
- tre cifre
- et mellemrum
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Australian_Company_Number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Australian_Company_Number.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Australian_Company_Number finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- Cna
- det australske firma nej
- det australske firma nej #
- det australske firmanummer
- australsk firma nr.
- australsk firma nr. #
- australsk firmanummer

## <a name="australia-drivers-license-number"></a>Australiens kørekortsnummer

### <a name="format"></a>Format

ni bogstaver og cifre

### <a name="pattern"></a>Mønster

ni bogstaver og cifre:

- to cifre eller bogstaver (skelner ikke mellem store og små bogstaver)
- to cifre
- fem cifre eller bogstaver (skelner ikke mellem store og små bogstaver)

ELLER

- et til to valgfri bogstaver (skelner ikke mellem store og små bogstaver)
- fire til ni cifre

ELLER

- ni cifre eller bogstaver (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_australia_drivers_license_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_australia_drivers_license_number.
- Der blev ikke fundet et nøgleord fra Keyword_australia_drivers_license_number_exclusions.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_drivers_license_number"></a>Keyword_australia_drivers_license_number

- internationale kørekort
- australsk bil forening
- international kørekort
- DriverLicence
- DriverLicences
- Driver-Lic
- Kørekort
- Kørekort
- Drivere
- DriversLicence
- DriversLicences
- Lic-faktorer
- Lic-drivere
- Kørekort
- Kørekort til førere
- Driver'Lic
- Driver'Lics
- Driver'Licence
- Kørekort
- Driver' Lic
- Driver' Lics
- Kørekort
- Kørekort
- Driver'sLic
- Driver'sLics
- Driver'sLicence
- Driver'sLicences
- Driverens Lic
- Driver's Lics
- Kørekort
- Kørekort
- DriverLic #
- DriverLics #
- DriverLicence #
- DriverLicences #
- Driver-Lic #
- Driver-LIC'er #
- Kørekort #
- Kørekort #
- Drivere #
- DriversLics #
- DriversLicence #
- DriversLicences #
- Lic-faktorer #
- Lic-drivere #
- Kørekort #
- Kørekort til førere #
- Driver'Lic #
- Driver'Lics #
- Driver'Licence #
- Kørekort #
- Driver' Lic #
- Driver' Lics #
- Kørekort #
- Kørekort #
- Driver'sLic #
- Driver'sLics #
- Driver'sLicence #
- Driver'sLicences #
- Driverens Lic #
- Driver's Lics #
- Kørekort #
- Kørekort #

#### <a name="keyword_australia_drivers_license_number_exclusions"></a>Keyword_australia_drivers_license_number_exclusions

- Aaa
- DriverLicense
- DriverLicenses
- Driverlicens
- Driverlicenser
- DriversLicense
- DriversLicenses
- Licens til drivere
- Kørekort til drivere
- Driverlicens
- Driverlicenser
- Driverlicens
- Driverlicenser
- Driver'sLicense
- Driver'sLicenses
- Kørekort
- Driverlicenser
- DriverLicense #
- DriverLicenses #
- Driverlicens #
- Driverlicenser #
- DriversLicense #
- DriversLicenses #
- Licens til drivere #
- Kørekort til drivere #
- Driverlicens #
- Driverlicenser #
- Driverlicens #
- Driverlicenser #
- Driver'sLicense #
- Driver'sLicenses #
- Kørekort #
- Driverlicenser #

## <a name="australia-medical-account-number"></a>Medicinsk kontonummer i Australien

### <a name="format"></a>Format

10-11 cifre

### <a name="pattern"></a>Mønster

10-11 cifre:

- Det første ciffer er mellem 2 og 6
- Niende ciffer er et kontrolciffer
- Det tiende ciffer er problemcifferet
- 11. ciffer (valgfrit) er det individuelle tal

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_australian_medical_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Australia_Medical_Account_Number.
- Kontrolsummen passerer.

```xml
  <!-- Australia Medical Account Number -->
<Entity id="104a99a0-3d3b-4542-a40d-ab0b9e1efe63" recommendedConfidence="85" patternsProximity="300">
    <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_australian_medical_account_number"/>
     <Match idRef="Keyword_Australia_Medical_Account_Number"/>
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_medical_account_number"></a>Keyword_Australia_Medical_Account_Number

- bankkontooplysninger
- medicare-betalinger
- realkreditkonto
- bankbetalinger
- informationsgren
- kreditkortlån
- afdeling for menneskelige tjenester
- lokal tjeneste
- Medicare

## <a name="australia-passport-number"></a>Australiens pasnummer

### <a name="format"></a>Format

otte eller ni alfanumeriske tegn

### <a name="pattern"></a>Mønster

- et bogstav (N, E, D, F, A, C, U, X) efterfulgt af syv cifre eller
- To bogstaver (PA, PB, PC, PD, PE, PF, PU, PW, PX, PZ) efterfulgt af syv cifre.

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_australia_passport_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_australia_passport_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_passport_number"></a>Keyword_australia_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre
- pasoplysninger
- indvandring og medborgerskab
- Australiens statsforbund
- immigrationsministeriet
- nationalt identitetskort
- rejsedokument
- udstedende myndighed

## <a name="australia-physical-addresses"></a>Fysiske adresser i Australien

Ubundtet navngivet enhed registrerer mønstre, der er relateret til fysisk adresse fra Australien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau
Medium

## <a name="australia-tax-file-number"></a>Australiens skattefilnummer

### <a name="format"></a>Format

otte til ni cifre

### <a name="pattern"></a>Mønster

8-9 cifre vises typisk med mellemrum på følgende måde:

- tre cifre
- et valgfrit mellemrum
- tre cifre
- et valgfrit mellemrum
- to til tre cifre, hvor det sidste ciffer er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_australian_tax_file_number finder indhold, der svarer til mønsteret.
- Der blev ikke fundet nøgleord fra Keyword_Australia_Tax_File_Number eller Keyword_number_exclusions.
- Kontrolsummen passerer.

```xml
   <!-- Australia Tax File Number -->
    <Entity id="e29bc95f-ff70-4a37-aa01-04d17360a4c5" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_australian_tax_file_number" />
        <Match idRef="Keyword_Australia_Tax_File_Number" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_australia_tax_file_number"></a>Keyword_australia_tax_file_number

- australsk virksomhedsnummer
- marginal skattesats
- medicare-afgift
- oversigtsnummer
- serviceveteraner
- Skat
- individuel selvangivelse
- skattefilnummer
- Tfn

## <a name="austria-drivers-license-number"></a>Østrigs kørekortsnummer

### <a name="format"></a>Format

otte cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_austria_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_austria_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_austria_eu_drivers_license_number"></a>Keywords_austria_eu_driver er s_license_number

- fuhrerschein
- führerschein
- Führerscheine
- Führerscheinnummer
- Führerscheinnummern

## <a name="austria-identity-card"></a>Østrigs identitetskort

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

En kombination af bogstaver, cifre og specialtegn på 24 tegn

### <a name="pattern"></a>Mønster

24 tegn:

- 22 bogstaver (skelner ikke mellem store og små bogstaver), cifre, omvendte skråstreger, skråstreger eller plustegn

- to bogstaver (skelner ikke mellem store og små bogstaver), cifre, omvendte skråstreger, skråstreger, plustegn eller lighedstegn

### <a name="checksum"></a>Checksum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_austria_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_austria_eu_national_id_card` .

```xml
      <!-- Austria Identity Card -->
      <Entity id="5ec06c3b-007e-4820-8343-7ff73b889735" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_austria_eu_national_id_card" />
          <Match idRef="Keywords_austria_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_austria_eu_national_id_card"></a>Keywords_austria_eu_national_id_card

- id-nummer
- nationalt id
- personalausweis republik österreich

## <a name="austria-passport-number"></a>Pasnummer for Østrig

### <a name="format"></a>Format

Et bogstav efterfulgt af et valgfrit mellemrum og syv cifre

### <a name="pattern"></a>Mønster

En kombination af ét bogstav, syv cifre og ét mellemrum:

- ét bogstav (skelner ikke mellem store og små bogstaver)
- ét mellemrum (valgfrit)
- syv cifre

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_austria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_austria_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_austria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_austria_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
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

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Østrig. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="austria-social-security-number"></a>Det østrigske cpr-nummer

### <a name="format"></a>Format

10 cifre i det angivne format

### <a name="pattern"></a>Mønster

10 cifre:

- tre cifre, der svarer til et serienummer
- et kontrolciffer
- seks cifre, der svarer til fødselsdatoen (DDMMYY)

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_austria_eu_ssn_or_equivalent` finder indhold, der svarer til mønsteret.
- der findes et nøgleord fra `Keywords_austria_eu_ssn_or_equivalent` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_austria_eu_ssn_or_equivalent` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_austria_eu_ssn_or_equivalent"></a>Keywords_austria_eu_ssn_or_equivalent

- østrigske ssn
- ehic-nummer
- ehic no
- forsikringskode
- insurancecode #
- forsikringsnummer
- forsikring nr.
- krankenkassennummer
- krankenversicherung
- social sikringno
- social sikringno #
- social sikring nr.
- CPR-nummer
- kode for social sikring
- sozialversicherungsnummer
- sozialversicherungsnummer #
- soziale sicherheit kein
- sozialesicherheitkein #
- Ssn #
- Ssn
- versicherungscode
- versicherungsnummer
- zdravstveno zavarovanje

## <a name="austria-tax-identification-number"></a>Østrigs skatteidentifikationsnummer

### <a name="format"></a>Format

ni cifre med valgfri bindestreg og skråstreg

### <a name="pattern"></a>Mønster

ni cifre med valgfri bindestreg og skråstreg:

- to cifre
- en bindestreg (valgfrit)
- tre cifre
- en skråstreg (valgfrit)
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_austria_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_austria_eu_tax_file_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_austria_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_austria_eu_tax_file_number"></a>Keywords_austria_eu_tax_file_number

- Österreich
- st.nr.
- steuernummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- momsnummer

## <a name="austria-value-added-tax"></a>Moms i Østrig

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 11 tegn

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 11 tegn:

- A eller a
- T eller t
- Valgfri plads
- U eller u
- valgfri plads
- to eller tre cifre
- valgfri plads
- fire cifre
- valgfri plads
- et eller to cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Austria_Value_Added_Tax finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Austria_Value_Added_Tax.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_Austria_Value_Added_Tax finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_austria_value_added_tax"></a>Keyword_austria_value_added_tax

- momsnummer
- Moms #
- østrigsk momsnummer
- momsnr.
- vatno #
- momsnummer
- østrigsk moms
- mwst
- umsatzsteuernummer
- mwstnummer
- ust.-identifikationsnummer
- umsatzsteuer-identifikationsnummer
- moms-id-nummer
- atu-nummer
- uid-tal

## <a name="azure-documentdb-auth-key"></a>Godkendelsesnøgle til Azure DocumentDB

### <a name="format"></a>Format

Strengen "DocumentDb" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- Strengen "DocumentDb"
- Enhver kombination af mellem 3-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- Et større end-symbol (>), et lighedstegn (=), et anførselstegn (") eller en apostrof (')
- Enhver kombination af 86 små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- To lighedstegn (=)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureDocumentDBAuthKey finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

(Teknisk set identificerer denne følsomme informationstype disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste).

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Azure IAAS-databaseforbindelsesstreng og Azure SQL forbindelsesstreng

### <a name="format"></a>Format

Strengen "Server", "server" eller "datakilde" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor, herunder strengen "cloudapp.azure.<!--no-hyperlink-->com" eller "cloudapp.azure.<!--no-hyperlink-->net" eller "database.windows.<!--no-hyperlink-->net", og strengen "Password" eller "password" eller "pwd".

### <a name="pattern"></a>Mønster

- strengen "Server", "server" eller "datakilde"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- Strengen "cloudapp.azure.<!--no-hyperlink-->com", "cloudapp.azure.<!--no-hyperlink-->net" eller "database.windows.<!--no-hyperlink-->net"
- enhver kombination af mellem 1-300 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "Password", "password" eller "pwd"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- et eller flere tegn, der ikke er semikolon (;), anførselstegn (") eller apostrof (')
- et semikolon (;), anførselstegn (") eller apostrof (')

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureConnectionString finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne følsomme informationstype disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste).

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-iot-connection-string"></a>Azure IoT-forbindelsesstreng

### <a name="format"></a>Format

Strengen "HostName" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor, herunder strengene "azure-devices.<!--no-hyperlink-->net" og "SharedAccessKey".

### <a name="pattern"></a>Mønster

- strengen "HostName"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "azure-devices.<!--no-hyperlink-->net"
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "SharedAccessKey"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43 små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- et lighedstegn (=)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureIoTConnectionString finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste.

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-publish-setting-password"></a>Adgangskode til udgivelsesindstilling i Azure

### <a name="format"></a>Format

Strengen "userpwd=" efterfulgt af en alfanumerisk streng.

### <a name="pattern"></a>Mønster

- strengen "userpwd="
- en kombination af 60 små bogstaver eller cifre
- et anførselstegn (")

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzurePublishSettingPasswords finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste.

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-redis-cache-connection-string"></a>Forbindelsesstreng til Azure Redis-cache

### <a name="format"></a>Format

Strengen "redis.cache.windows.<!--no-hyperlink-->net" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor, herunder strengen "adgangskode" eller "pwd".

### <a name="pattern"></a>Mønster

- strengen "redis.cache.windows.<!--no-hyperlink-->net"
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "adgangskode" eller "pwd"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- et lighedstegn (=)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureRedisCacheConnectionString finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne følsomme informationstype disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste).

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-sas"></a>Azure SAS

### <a name="format"></a>Format

Strengen "sig" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- strengen "sig"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af mellem 43-53 tegn, der er små eller store bogstaver, cifre eller procenttegnet (%)
- strengen "%3d"
- alle tegn, der ikke er et tegn med små eller store bogstaver, tal eller procenttegn (%)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureSAS finder indhold, der svarer til mønsteret.

```xml
<!--Azure SAS-->
<Entity id="4d235014-e564-47f4-a6fb-6ebb4a826834" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureSAS" />
  </Pattern>
</Entity>
```

## <a name="azure-service-bus-connection-string"></a>Forbindelsesstreng til Azure Service Bus

### <a name="format"></a>Format

Strengen "EndPoint" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor, herunder strengene "servicebus.windows.<!--no-hyperlink-->net" og "SharedAccesKey".

### <a name="pattern"></a>Mønster

- strengen "EndPoint"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "servicebus.windows.<!--no-hyperlink-->net"
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "SharedAccessKey"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 43 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- et lighedstegn (=)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureServiceBusConnectionString finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne følsomme informationstype disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste).

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-storage-account-key"></a>Azure Storage-kontonøgle

### <a name="format"></a>Format

Strengen "DefaultEndpointsProtocol" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor, herunder strengen "AccountKey".

### <a name="pattern"></a>Mønster

- strengen "DefaultEndpointsProtocol"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "AccountKey"
- nul til to mellemrumstegn
- et lighedstegn (=)
- nul til to mellemrumstegn
- en kombination af 86 tegn, der er små eller store bogstaver, cifre, skråstreg (/) eller plustegn (+)
- to lighedstegn (=)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureStorageAccountKey finder indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_AzureEmulatorStorageAccountFilter kan ikke finde indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_azure_emulator_storage_account_filter"></a>CEP_azure_emulator_storage_account_filter

(Teknisk set identificerer denne følsomme informationstype disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste).

- Eby8vdM02xNOcqFlqUwJPLlmEtlCDXJ1OUzFT50uSRZ6IFsuFq2UVErCz4I6tq/K1SZFPTOtr/KBHBeksoGMGw==

#### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

(Teknisk set identificerer denne følsomme informationstype disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste).

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="azure-storage-account-key-generic"></a>Azure Storage kontonøgle (generisk)

### <a name="format"></a>Format

Enhver kombination af 86 små eller store bogstaver, cifre, skråstregen (/) eller plustegnet (+), foranstillet eller efterfulgt af de tegn, der er skitseret i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- nul til et af symbolet større end (>), apostrof ('), lighedstegn (=), anførselstegn (") eller taltegn (#)
- en kombination af 86 tegn, der er små eller store bogstaver, cifre, skråstregen (/) eller plustegnet (+)
- to lighedstegn (=)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_AzureStorageAccountKeyGeneric finder indhold, der svarer til mønsteret.

```xml
<!--Azure Storage Account Key (Generic)-->
<Entity id="7ff41bd0-5419-4523-91d6-383b3a37f084" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureStorageAccountKeyGeneric" />
  </Pattern>
</Entity>
```

## <a name="belgium-drivers-license-number"></a>Belgiens kørekortsnummer

### <a name="format"></a>Format

10 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_belgium_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_belgium_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_belgium_eu_drivers_license_number"></a>Keywords_belgium_eu_driver er s_license_number

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

## <a name="belgium-national-number"></a>Belgiens nationale nummer

### <a name="format"></a>Format

11 cifre plus valgfri afgrænsere

### <a name="pattern"></a>Mønster

11 cifre plus afgrænsere:

- seks cifre og to valgfrie punktummer i formatet YY. DD for fødselsdato
- En valgfri afgrænser fra punktum, tankestreg, mellemrum
- tre sekventielle cifre (ulige for hanner, selv for kvinder)
- En valgfri afgrænser fra punktum, tankestreg, mellemrum
- to kontrolcifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_belgium_national_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_belgium_national_number.
- Kontrolsummen passerer.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_belgium_national_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_belgium_national_number"></a>Keyword_belgium_national_number

- sidste aantal
- bnn #
- bnn
- carte d'identité
- identifiant national
- identifiantnational #
- identificatie
- Identifikation
- identifikation
- identifikationsnummer
- identifizierung
- identité
- identiteit
- identiteitskaart
- Identitet
- Inskription
- nationalt nummer
- nationalt register
- nationalt nummer #
- nationalt nummer
- Nif #
- Nif
- numéro d'assuré
- numéro de registre national
- numéro de sécurité
- numéro d'identification
- numéro d'immatriculation
- numéro national
- numéronational #
- personligt id-nummer
- personalausweis
- personalidnumber #
- registratie
- Registrering
- registrationsnumme
- registrierung
- CPR-nummer
- Ssn #
- Ssn
- steuernummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="belgium-passport-number"></a>Belgiens pasnummer

### <a name="format"></a>Format

to bogstaver efterfulgt af seks cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

to bogstaver og efterfulgt af seks cifre

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

 En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_belgium_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_belgium_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date2` finder dato i formatet DD MM ÅÅ eller et nøgleord fra `Keywords_eu_passport_date` eller `Keywords_belgium_eu_passport_number` findes

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_belgium_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_belgium_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_belgium_eu_passport_number"></a>Keywords_belgium_eu_passport_number

- numéro passeport
- paspoort nr.
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

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysiske adresser fra Belgien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="belgium-value-added-tax-number"></a>Belgiens momsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 12 tegn

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 12 tegn:

- et bogstav B eller b
- et bogstav E eller e
- et ciffer 0
- et ciffer fra 1 til 9
- en valgfri prik eller bindestreg eller mellemrum
- fire cifre
- en valgfri prik eller bindestreg eller mellemrum
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_belgium_value_added_tax_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_belgium_value_added_tax_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_belgium_value_added_tax_number finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_belgium_value_added_tax_number"></a>Keyword_belgium_value_added_tax_number

- nº tva
- momsnummer
- momsnr.
- numéro t.v.a
- umsatzsteuer-identifikationsnummer
- umsatzsteuernummer
- Btw
- Btw #
- Moms #

## <a name="blood-test-terms"></a>Vilkår for blodprøve

Denne ubundtede navngivne enhed registrerer termer, der er relateret til blodprøver, f.eks. *hCG*. Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="brand-medication-names"></a>Navne på mærkemedicin

Denne ubundtede navngivne enhed registrerer navne på mærkemedicin, såsom *Tylenol*. Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="brazil-cpf-number"></a>BrasilienS CPF-nummer

### <a name="format"></a>Format

11 cifre, der indeholder et kontrolciffer, og som kan formateres eller ikke formateres

### <a name="pattern"></a>Mønster

Formateret:

- tre cifre
- et punktum
- tre cifre
- et punktum
- tre cifre
- en bindestreg
- to cifre, der er kontrolcifre

Uformateret:

- 11 cifre, hvor de sidste to cifre er kontrolcifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_brazil_cpf finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_brazil_cpf.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_brazil_cpf finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

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

## <a name="brazil-legal-entity-number-cnpj"></a>Juridisk enhedsnummer for Brasilien (CNPJ)

### <a name="format"></a>Format

14 cifre, der indeholder et registreringsnummer, et forgreningsnummer og et kontrolcifre plus afgrænsere

### <a name="pattern"></a>Mønster

14 cifre plus afgrænsere:

- to cifre
- et punktum
- tre cifre
- et punktum
- tre cifre (disse første otte cifre er registreringsnummeret)
- en skråstreg
- firecifret forgreningsnummer
- en bindestreg
- to cifre, der er kontrolcifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_brazil_cnpj finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_brazil_cnpj.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_brazil_cnpj finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_brazil_cnpj"></a>Keyword_brazil_cnpj

- CNPJ
- CNPJ/MF
- CNPJ-MF
- Det nationale register over juridiske enheder
- Skatteydernes register
- Juridisk enhed
- Juridiske enheder
- Registreringsstatus
- Business
- Virksomhed
- CNPJ
- Cadastro Nacional da Pessoa Jurídica
- Cadastro Geral de Contribuintes
- CGC
- Pessoa jurídica
- Pessoas jurídicas
- Situação cadastral
- Inscrição
- Empresa

## <a name="brazil-national-identification-card-rg"></a>Nationalt id-kort for Brasilien (RG)

### <a name="format"></a>Format

Registro Geral (gammelt format): Ni cifre

Registro de Identidade (RIC) (nyt format): 11 cifre

### <a name="pattern"></a>Mønster

Registro Geral (gammelt format):

- to cifre
- et punktum
- tre cifre
- et punktum
- tre cifre
- en bindestreg
- et ciffer, der er et kontrolciffer

Registro de Identidade (RIC) (nyt format):

- 10 cifre
- en bindestreg
- et ciffer, der er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_brazil_rg finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_brazil_rg.
- Kontrolsummen passerer.

```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- Identitetskort
- nationalt id
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (dette nøgleord skelner mellem store og små bogstaver)
- RIC (dette nøgleord skelner mellem store og små bogstaver)

## <a name="brazil-physical-addresses"></a>Fysiske adresser i Brasilien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Brasilien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="bulgaria-drivers-license-number"></a>Bulgariens kørekortsnummer

### <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_bulgaria_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_bulgaria_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver er s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки

## <a name="bulgaria-passport-number"></a>Bulgariens pasnummer

### <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_bulgaria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_bulgaria_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_bulgaria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_bulgaria_eu_passport_number` findes.

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
### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт Nej

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="bulgaria-physical-addresses"></a>Fysiske adresser for Bulgarien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Bulgarien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="bulgaria-uniform-civil-number"></a>Bulgariens ensartede civilnummer
Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

10 cifre uden mellemrum og afgrænsere

- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- to cifre, der svarer til fødselsrækkefølgen
- ét ciffer, der svarer til køn: Et lige ciffer for mand og et ulige ciffer for kvinder
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_bulgaria_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_bulgaria_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_bulgaria_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinen grazhdanski nomer
- egn #
- egn
- Identifikationsnummer
- nationalt id
- nationalt nummer
- nationalt nummer #
- nationalt nummer
- personligt id
- personligt nej
- personligt nummer
- personalidnumber #
- CPR-nummer
- Ssn #
- Ssn
- ensartet civilt id
- ensartet civilt nr.
- et ensartet civilt nummer
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- entydigt statsborgerskabsnummer
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
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #

## <a name="canada-bank-account-number"></a>Canadas bankkontonummer

### <a name="format"></a>Format

7 eller 12 cifre

### <a name="pattern"></a>Mønster

Et Canada-bankkontonummer er 7 eller 12 cifre.

Et canadask bankkontotransitnummer er:

- fem cifre
- en bindestreg
- tre cifre OR
- et nul "0"
- otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_canada_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_canada_bank_account_number.
- Det regulære udtryk Regex_canada_bank_account_transit_number finder indhold, der svarer til mønsteret.

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_canada_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_canada_bank_account_number.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_canada_bank_account_number"></a>Keyword_canada_bank_account_number

- canada savings bonds
- canada revenue agency
- canadisk finansinstitut
- formular til direkte indbetaling
- canadisk statsborger
- juridisk repræsentant
- notar offentlig
- kommissær for eder
- børnepasningsydelse
- universel børnepasning
- canada child tax benefit
- indkomstskattefordel
- harmoniseret omsætningsafgift
- cpr-nummer
- refusion af indkomstskat
- skattefordele for børn
- territoriale betalinger
- institutionsnummer
- anmodning om indbetaling
- bankoplysninger
- direkte indbetaling

## <a name="canada-drivers-license-number"></a>Canadas kørekortsnummer

### <a name="format"></a>Format

Varierer efter provins

### <a name="pattern"></a>Mønster

Forskellige mønstre, der dækker:

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

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_[province_name]_drivers_license_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_[province_name]_drivers_license_name.
- Der blev fundet et nøgleord fra Keyword_canada_drivers_license.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_province_name_drivers_license_name"></a>Keyword_[province_name]_drivers_license_name

- Forkortelsen for provinsen, f.eks. AB
- Provinsnavnet, f.eks. Alberta

#### <a name="keyword_canada_drivers_license"></a>Keyword_canada_drivers_license

- DL
- DLS
- CDL
- CDLS
- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- DriverLicence
- DriverLicences
- Driver-Lic
- Driver-LIC'er
- Driverlicens
- Driverlicenser
- Kørekort
- Kørekort
- Drivere
- DriversLics
- DriversLicence
- DriversLicences
- DriversLicense
- DriversLicenses
- Lic-faktorer
- Lic-drivere
- Licens til drivere
- Kørekort til drivere
- Kørekort
- Kørekort til førere
- Driver'Lic
- Driver'Lics
- Driverlicens
- Driverlicenser
- Driver'Licence
- Kørekort
- Driver' Lic
- Driver' Lics
- Driverlicens
- Driverlicenser
- Kørekort
- Kørekort
- Driver'sLic
- Driver'sLics
- Driver'sLicense
- Driver'sLicenses
- Driver'sLicence
- Driver'sLicences
- Driverens Lic
- Driver's Lics
- Kørekort
- Driverlicenser
- Kørekort
- Kørekort
- Permis de Conduire
- Id
- Id'er
- idcard-nummer
- idcard-numre
- idcard #
- idcard-#s
- idcard-kort
- idcard-kort
- idcard
- Identifikationsnummer
- Identifikationsnumre
- Identifikation #
- identifikation #s
- identifikationskort
- id-kort
- Identifikation
- DL #
- DLS #
- CDL #
- CDLS #
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- DriverLicence #
- DriverLicences #
- Driver-Lic #
- Driver-LIC'er #
- Driverlicens #
- Driverlicenser #
- Driverlicens #
- Kørekort #
- Drivere #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- DriversLicence #
- DriversLicences #
- Lic-faktorer #
- Lic-drivere #
- Licens til drivere #
- Kørekort til drivere #
- Kørekort #
- Kørekort til førere #
- Driver'Lic #
- Driver'Lics #
- Driverlicens #
- Driverlicenser #
- Driver'Licence #
- Kørekort #
- Driver' Lic #
- Driver' Lics #
- Driverlicens #
- Driverlicenser #
- Kørekort #
- Kørekort #
- Driver'sLic #
- Driver'sLics #
- Driver'sLicense #
- Driver'sLicenses #
- Driver'sLicence #
- Driver'sLicences #
- Driverens Lic #
- Driver's Lics #
- Kørekort #
- Driverlicenser #
- Kørekort #
- Kørekort #
- Permis de Conduire #
- Id #
- Id'er #
- idcard-kort #
- idcard-kort #
- idcard #
- identifikationskort #
- id-kort #
- Identifikation #

## <a name="canada-health-service-number"></a>Nummer på sundhedstjenesten i Canada

### <a name="format"></a>Format

 10 cifre

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_canada_health_service_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_canada_health_service_number.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_canada_health_service_number"></a>Keyword_canada_health_service_number

- personnummer
- patientoplysninger
- sundhedstjenester
- specialtjenester
- bilulykke
- patienthospital
- Psykiater
- løn til arbejdstagere
- Handicap

## <a name="canada-passport-number"></a>Pasnummer til Canada

### <a name="format"></a>Format

to store bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

to store bogstaver efterfulgt af seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_canada_passport_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_canada_passport_number eller Keyword_passport.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_canada_passport_number"></a>Keyword_canada_passport_number

- canadisk statsborgerskab
- canadisk pas
- passport-program
- pasfotos
- certificeret oversætter
- canadiske statsborgere
- behandlingstider
- fornyelsesprogram

#### <a name="keyword_passport"></a>Keyword_passport

- Passport-nummer
- Passport-nr.
- Passport #
- Passport #
- PassportID
- Passportno
- passportnumber
- パスポート
- パスポート番号
- パスポートのNum
- パスポート＃
- Numéro de passeport
- Passeport n °
- Passeport ikke
- Passeport #
- Passeport #
- PasseportNon
- Passeportn °

## <a name="canada-personal-health-identification-number-phin"></a>Id-nummer for personlig sundhed i Canada (PHIN)

### <a name="format"></a>Format

ni cifre

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_canada_phin finder indhold, der svarer til mønsteret.
- Der findes mindst to nøgleord fra Keyword_canada_phin eller Keyword_canada_provinces.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_canada_phin"></a>Keyword_canada_phin

- cpr-nummer
- sundhedsoplysningshandling
- oplysninger om indkomstskat
- manitoba sundhed
- tilstandsregistrering
- receptkøb
- frynsegodeberettigelse
- personlig sundhed
- fuldmagt
- registreringsnummer
- personnummer
- henvisning til praktiserende læge
- wellness-professionel
- patienthenvisning
- sundhed og velvære

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

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Canada. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="canada-social-insurance-number"></a>Canada socialforsikringsnummer

### <a name="format"></a>Format

ni cifre med valgfri bindestreger eller mellemrum

### <a name="pattern"></a>Mønster

Formateret:

- tre cifre
- en bindestreg eller et mellemrum
- tre cifre
- en bindestreg eller et mellemrum
- tre cifre

Ikke formateret: ni cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_canadian_sin finder indhold, der svarer til mønsteret.
- Mindst to af følgende mønstre:
    - Der blev fundet et nøgleord fra Keyword_sin.
    - Der blev fundet et nøgleord fra Keyword_sin_collaborative.
    - Funktionen Func_eu_date finder en dato i det rigtige datoformat.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_unformatted_canadian_sin finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_sin.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_sin"></a>Keyword_sin

- Synd
- social sikring
- numero d'assurance sociale
- Synder
- Ssn
- ssns
- social sikring
- numero d'assurance social
- nationalt identifikationsnummer
- nationalt id
- Synd #
- soc ins
- sociale ins

#### <a name="keyword_sin_collaborative"></a>Keyword_sin_collaborative

- kørekort
- licens til drivere
- kørekort
- kørekort
- DOB
- Fødselsdato
- Fødselsdag
- Fødselsdag

## <a name="chile-identity-card-number"></a>Chiles identitetskortnummer

### <a name="format"></a>Format

syv til otte cifre plus afgrænsere et kontrolciffer eller et bogstav

### <a name="pattern"></a>Mønster

syv til otte cifre plus afgrænsere:

- et til to cifre
- en valgfri periode
- tre cifre
- en valgfri periode
- tre cifre
- en streg
- et ciffer eller bogstav (skelner ikke mellem store og små bogstaver), som er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_chile_id_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_chile_id_card.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_chile_id_card finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_chile_id_card"></a>Keyword_chile_id_card

- cédula de identidad
- identificación
- nationalt identifikation
- nationalt identifikationsnummer
- nationalt id
- número de identificación nacional
- rol único nacional
- rol único tributario
- KØRE
- SKURE
- tarjeta de identificación
- Rol Unico Nacional
- Rol Unico Tributario
- KØRE #
- SKURE #
- nationaluniqueroleID #
- nacional identidad
- número identificación
- identidad número
- numero identificacion
- identidad numero
- Chilensk identitet nr.
- Chilensk identitetsnummer
- Chilensk identitet #
- Entydigt skatteregister
- Entydig bitributrolle
- Entydig skatterolle
- Entydigt bitributnummer
- Entydigt nationalt nummer
- Entydig national rolle
- National entydig rolle
- Chiles identitet nr.
- Chiles identitetsnummer
- Chile-identitet #
- R.U.T
- R.U.N

## <a name="china-resident-identity-card-prc-number"></a>Kina resident id-kort (PRC) nummer

### <a name="format"></a>Format

18 cifre

### <a name="pattern"></a>Mønster

18 cifre:

- seks cifre, der er en adressekode
- cifre i formatet YYYYMMDD, som er fødselsdatoen
- tre cifre, der er en ordrekode
- et ciffer, der er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_china_resident_id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_china_resident_id.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_china_resident_id finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

### <a name="keyword_china_resident_id"></a>Keyword_china_resident_id

- Resident Identity Card
- KINA
- Nationalt id-kort
- 身份证
- 居民 身份证
- 居民身份证
- 鉴定
- 身分證
- 居民 身份證
- 鑑定

## <a name="credit-card-number"></a>Kreditkortnummer

### <a name="format"></a>Format

14 til 19 cifre, der kan formateres eller formateres (dddddddd), og som skal bestå Luhn-testen.

### <a name="pattern"></a>Mønster

Registrerer kort fra alle større mærker verden over, herunder Visa, MasterCard, Discover Card, JCB, American Express, gavekort, diner's kort, Rupay og China UnionPay.

### <a name="checksum"></a>Checksum

Ja, luhn-kontrollen

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_credit_card finder indhold, der svarer til mønsteret.
- En af følgende betingelser er opfyldt:
  - Der blev fundet et nøgleord fra Keyword_cc_verification.
  - Der blev fundet et nøgleord fra Keyword_cc_name.
  - Funktionen Func_expiration_date finder en dato i det rigtige datoformat.
- Kontrolsummen passerer.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_credit_card finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_cc_verification"></a>Keyword_cc_verification

- kortbekræftelse
- kortidentifikationsnummer
- Cvn
- Cid
- cvc2
- cvv2
- fastgørelsesblok
- sikkerhedskode
- sikkerhedsnummer
- sikkerhed nr.
- problemnummer
- problem nr.
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
- Torsk. sicurezza
- cod sicurezza
- n autorizzazione
- código
- codigo
- Torsk. Seg
- cod seg
- código de segurança
- codigo de seguranca
- codigo de segurança
- código de seguranca
- cód. segurança
- Torsk. seguranca
- Torsk. segurança
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
- Valor
- vencimento
- Transaktion
- transaktionsnummer
- referencenummer
- セキュリティコード
- セキュリティ コード
- セキュリティナンバー
- セキュリティ ナンバー
- セキュリティ番号

#### <a name="keyword_cc_name"></a>Keyword_cc_name

- Amex
- american express
- americanexpress
- americano espresso
- Visa
- Mastercard
- masterkort
- Mc
- Mastercards
- masterkort
- diner's Club
- diners club
- dinersclub
- Oplev
- find kort
- discovercard
- find kort
- JCB
- BrandSmart
- japansk kortbureau
- carte blanche
- carteblanche
- Kreditkort
- Cc #
- cc#:

- Udløbsdato
- udløbsdato
- Udløbsdato
- dato for udløb
- dato d'exp
- udløbsdato
- bankkort
- bankkort
- kortnummer
- kortnummer
- cardnumber
- cardnumbers
- kortnumre
- Kreditkort
- Kreditkort
- kreditkort
- Ccn
- Kortholderen
- Kortindehaveren
- kortholdere
- Kortholdere
- kontrolkort
- checkcard
- tjek kort
- checkcards
- Betalingskort
- debetkort
- Betalingskort
- debetkort
- atm-kort
- atmcard
- atmkort
- atmcards
- Undervejs
- Vej
- korttype
- Cardmember Acct
- cardmember-konto
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
- N. Carta
- n carta
- nr. Carta
- nr. carta
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
- Nº. do cartão
- ingen do cartão
- ingen do cartao
- Nej. do cartão
- Nej. do cartao
- rupay
- fagforeningsløn
- unionpay
- diner's
- Diners
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

## <a name="croatia-drivers-license-number"></a>Kroatiens kørekortsnummer

### <a name="format"></a>Format

otte cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_croatia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_croatia_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_croatia_eu_drivers_license_number"></a>Keywords_croatia_eu_driver er s_license_number

- vozačka dozvola
- vozačke dozvole

## <a name="croatia-identity-card-number"></a>Kroatiens identitetskortnummer

Denne enhed er omfattet af eu's type følsomme oplysninger om nationalt identifikationsnummer. Den er tilgængelig som et separat objekt af typen af følsomme oplysninger.

### <a name="format"></a>Format

ni cifre

### <a name="pattern"></a>Mønster

ni cifre i træk

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_croatia_id_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_croatia_id_card.

```xml
<!--Croatia Identity Card Number-->
<Entity id="ff12f884-c20a-4189-b185-34c8e7258d47" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_croatia_id_card"/>
     <Match idRef="Keyword_croatia_id_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_croatia_id_card"></a>Keyword_croatia_id_card

- majstorski broj građana
- master borgernummer
- nacionalni identifikacijski broj
- nationalt identifikationsnummer
- oib #
- oib
- osobna iskaznica
- osobni-id
- osobni identifikacijski broj
- personligt identifikationsnummer
- porezni broj
- porezni identifikacijski broj
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="croatia-passport-number"></a>Kroatiens pasnummer

### <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_croatia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_croatia_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_croatia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_croatia_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_croatia_eu_passport_number"></a>Keywords_croatia_eu_passport_number

- broj putovnice
- Br. Putovnice
- br putovnice

## <a name="croatia-personal-identification-oib-number"></a>Personidentifikationsnummer for Kroatien (OIB)

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

11 cifre:

- 10 cifre
- det endelige ciffer er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_croatia_oib_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_croatia_eu_tax_file_number.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_croatia_oib_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_croatia_oib_number"></a>Keyword_croatia_oib_number

- majstorski broj građana
- master borgernummer
- nacionalni identifikacijski broj
- nationalt identifikationsnummer
- oib #
- oib
- osobna iskaznica
- osobni-id
- osobni identifikacijski broj
- personligt identifikationsnummer
- porezni broj
- porezni identifikacijski broj
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="croatia-physical-addresses"></a>Fysiske adresser for Kroatien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Kroatien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="cyprus-drivers-license-number"></a>Cyperns kørekortsnummer

### <a name="format"></a>Format

12 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

12 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_cyprus_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_cyprus_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_cyprus_eu_drivers_license_number"></a>Keywords_cyprus_eu_driver er s_license_number

- άδεια οδήγησης
- αριθμό άδειας οδήγησης
- άδειες οδήγησης

## <a name="cyprus-identity-card"></a>Cyperns identitetskort

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_cyprus_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_cyprus_eu_national_id_card` .

```xml
      <!-- Cyprus Identity Card -->
      <Entity id="3ba8afe5-7a6c-4929-8247-0001b6878438" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_cyprus_eu_national_id_card" />
          <Match idRef="Keywords_cyprus_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_cyprus_eu_national_id_card"></a>Keywords_cyprus_eu_national_id_card

- id-kortnummer
- id-kortnummer
- kimlik karti
- nationalt identifikationsnummer
- personligt id-nummer
- ταυτοτητασ

## <a name="cyprus-passport-number"></a>Cyperns pasnummer

### <a name="format"></a>Format

ét bogstav efterfulgt af 6-8 cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

ét bogstav efterfulgt af seks til otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_cyprus_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_cyprus_eu_passport_number` findes.
- Det regulære udtryk `Regex_cyprus_eu_passport_date` finder datoen i formatet DD/MM/ÅÅÅÅ, eller der findes et nøgleord fra `Keywords_cyprus_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_cyprus_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_cyprus_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_cyprus_eu_passport_number"></a>Keywords_cyprus_eu_passport_number

- αριθμό διαβατηρίου
- pasaportu
- Αριθμός Διαβατηρίου
- κυπριακό διαβατήριο
- διαβατήριο #
- διαβατήριο
- αριθμός διαβατηρίου
- Pasaport Kimliği
- pasaport numarası
- Pasaport nej.
- Αρ. Διαβατηρίου

#### <a name="keywords_cyprus_eu_passport_date"></a>Keywords_cyprus_eu_passport_date

- udløber den
- udstedt den

## <a name="cyprus-physical-addresses"></a>Fysiske adresser for Cypern

Denne ubundtede navngivne enhed registrerer mønstre relateret til fysisk adresse fra Cypern. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="cyprus-tax-identification-number"></a>Cyperns skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

otte cifre og ét bogstav i det angivne mønster

### <a name="pattern"></a>Mønster

otte cifre og ét bogstav:

- et "0" eller "9"
- syv cifre
- ét bogstav (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_cyprus_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_cyprus_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_cyprus_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_cyprus_eu_tax_file_number"></a>Keywords_cyprus_eu_tax_file_number

- moms-id
- kode til identifikation af moms
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- Tic #
- Tic
- tin-id
- tin no
- Tin #
- vergi kimlik kodu
- vergi kimlik numarası
- αριθμός φορολογικού μητρώου
- κωδικός φορολογικού μητρώου
- φορολογική ταυτότητα
- φορολογικού κωδικού

## <a name="czech-drivers-license-number"></a>Tjekkisk kørekortsnummer

### <a name="format"></a>Format

to bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

otte bogstaver og cifre:

- bogstavet 'E' (skelner ikke mellem store og små bogstaver)
- et bogstav
- et mellemrum (valgfrit)
- seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_czech_republic_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_czech_republic_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_czech_republic_eu_drivers_license_number"></a>Keywords_czech_republic_eu_driver er s_license_number

- řidičský prúkaz
- řidičské průkazy
- číslo řidičského průkazu
- čísla řidičských průkazů

## <a name="czech-passport-number"></a>Tjekkisk pasnummer

### <a name="format"></a>Format

otte cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

otte cifre uden mellemrum eller afgrænsere

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_czech_republic_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_czech_republic_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_czech_republic_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_czech_republic_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_czech_republic_eu_passport_number"></a>Keywords_czech_republic_eu_passport_number

- cestovní pas
- číslo pasu
- cestovní pasu
- passeport nej
- čísla pasu

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="czech-personal-identity-number"></a>Tjekkisk personligt id-nummer

### <a name="format"></a>Format

ni cifre med valgfri skråstreg (gammelt format)

10 cifre med valgfri skråstreg (nyt format)

### <a name="pattern"></a>Mønster

ni cifre (gammelt format):

- seks cifre, der repræsenterer fødselsdato
- en valgfri skråstreg
- tre cifre

10 cifre (nyt format):

- seks cifre, der repræsenterer fødselsdato
- en valgfri skråstreg
- fire cifre, hvor sidste ciffer er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_czech_id_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_czech_id_card.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_czech_id_card_new_format finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_czech_id_card"></a>Keyword_czech_id_card

- fødselsnummer
- tjekkiets id
- czechidno #
- daňové číslo
- identifikační číslo
- identitet nr.
- id-nummer
- identityno #
- identityno
- forsikringsnummer
- nationalt identifikationsnummer
- nationalt nummer #
- nationalt nummer
- osobní číslo
- personalidnumber #
- personligt id-nummer
- personligt identifikationsnummer
- personligt nummer
- Pid #
- Pid
- pojištění číslo
- rč
- rodne cislo
- rodné číslo
- Ssn
- Ssn #
- CPR-nummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- entydigt identifikationsnummer

## <a name="czech-republic-physical-addresses"></a>Fysiske adresser for Tjekkiet

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Tjekkiet. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="denmark-drivers-license-number"></a>Danmarks kørekortsnummer

### <a name="format"></a>Format

otte cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_denmark_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_denmark_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_denmark_eu_drivers_license_number"></a>Keywords_denmark_eu_driver er s_license_number

- kørekort
- kørekortnummer

## <a name="denmark-passport-number"></a>Danmark pasnummer

### <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_denmark_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_denmark_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date2` finder datoen i formatet DD MM ÅÅ, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_denmark_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_denmark_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_denmark_eu_passport_number"></a>Keywords_denmark_eu_passport_number

- pasnummer
- Passeport n°
- pasnumre

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="denmark-personal-identification-number"></a>Personidentifikationsnummer for Danmark

### <a name="format"></a>Format

10 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

10 cifre:

- seks cifre i formatet DDMMYY, som er fødselsdatoen
- et valgfrit mellemrum eller en bindestreg
- fire cifre, hvor det endelige ciffer er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Func_denmark_eu_tax_file_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_denmark_id.
- Kontrolsummen passerer.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Func_denmark_eu_tax_file_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_denmark_id"></a>Keyword_denmark_id

- centrale personregister
- civilt registreringssystem
- Cpr
- Cpr #
- gesundheitskarte nummer
- gesundheitsversicherungkarte nummer
- helbredskort
- sygesikringskortnummer
- sygesikringsnummer
- Identifikationsnummer
- identifikationsnummer
- identifikationsnummer #
- id-nummer
- krankenkassennummer
- nationalid #
- nationalt nummer #
- nationalt nummer
- personalidnumber #
- personalidentityno #
- personligt id-nummer
- personnummer
- personnummer #
- reisekrankenversicherungskartenummer
- rejsesygesikringskort
- Ssn
- Ssn #
- skat-id
- skat kode
- skat nummer
- skattenummer
- CPR-nummer
- sundhedsforsikringskort
- sundhedsforsikringsnummer
- sundhedskort
- sundhedskortnummer
- sygesikring
- sygesikringkortnummer
- skattekode
- rejsesund hedsforsikringskort
- uniqueidentityno #
- momsnummer
- momsregistreringsnummer
- moms-id
- moms-id-nummer
- taxid #
- momsnummer #
- skattenr.
- taxno #
- momsnummer
- momsidentifikation nr.
- Tin #
- taxidno #
- taxidnumber #
- skattenr. #
- tin-id
- tin no
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
- sygesikringsnummer

## <a name="denmark-physical-addresses"></a>Fysiske adresser i Danmark

Denne ubundtede navngivne enhed registrerer mønstre relateret til fysisk adresse fra Danmark. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="diseases"></a>Sygdomme

Denne ubundtede navngivne enhed registrerer tekst, der svarer til sygdomsnavne, f.eks. *diabetes*. Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="drug-enforcement-agency-dea-number"></a>Dea-nummer (Drug Enforcement Agency)

### <a name="format"></a>Format

to bogstaver efterfulgt af syv cifre

### <a name="pattern"></a>Mønster

Mønsteret skal indeholde alle følgende:

- ét bogstav (skelner ikke mellem store og små bogstaver) fra dette sæt af mulige bogstaver: A/B/F/G/M/P/R, som er en registrantkode
- ét bogstav (ikke forskel på store og små bogstaver), som er det første bogstav i registrantens efternavn eller ciffer '9'
- syv cifre, hvoraf det sidste er kontrolcifferet

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_dea_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_dea_number`
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_dea_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- administration af narkotikamisbrug
- drug enforcement agency

## <a name="estonia-drivers-license-number"></a>Estisk kørekortsnummer

### <a name="format"></a>Format

to bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

to bogstaver og seks cifre:

- bogstaverne "ET" (skelner ikke mellem store og små bogstaver)
- seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_estonia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_estonia_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_estonia_eu_drivers_license_number"></a>Keywords_estonia_eu_driver s_license_number

- permis de conduire
- juhilubade numbrid
- juhiloa-nummer
- juhiluba

## <a name="estonia-passport-number"></a>Estisk pasnummer

### <a name="format"></a>Format

ét bogstav efterfulgt af syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

ét bogstav efterfulgt af syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_estonia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_estonia_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_estonia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_estonia_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document no dokumendi nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="estonia-personal-identification-code"></a>Personidentifikationskode for Estland

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

11 cifre:

- et ciffer, der svarer til køn og fødsels århundrede (ulige antal mænd, lige antal kvinder, 1-2: 19. århundrede, 3-4: 20. århundrede, 5-6: 21. århundrede)
- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- tre cifre, der svarer til et serienummer, der adskiller personer født på samme dato
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_estonia_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_estonia_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_estonia_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- Ik
- isikukood #
- isikukood
- maksu-id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- nationalt identifikationsnummer
- nationalt nummer
- personlig kode
- personligt id-nummer
- kode til personlig identifikation
- personligt identifikationsnummer
- personalidnumber #
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="estonia-physical-addresses"></a>Fysiske adresser i Estland

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Estland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="eu-debit-card-number"></a>EU-betalingskortnummer

### <a name="format"></a>Format

16 cifre

### <a name="pattern"></a>Mønster

Komplekst og robust mønster

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_eu_debit_card finder indhold, der svarer til mønsteret.
- Mindst et af følgende udsagn er sandt:
    - Der blev fundet et nøgleord fra Keyword_eu_debit_card.
    - Der blev fundet et nøgleord fra Keyword_card_terms_dict.
    - Der blev fundet et nøgleord fra Keyword_card_security_terms_dict.
    - Der blev fundet et nøgleord fra Keyword_card_expiration_terms_dict.
    - Funktionen Func_expiration_date finder en dato i det rigtige datoformat.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_eu_debit_card"></a>Keyword_eu_debit_card

- kontonummer
- kortnummer
- kortnr.
- sikkerhedsnummer
- Cc #

#### <a name="keyword_card_terms_dict"></a>Keyword_card_terms_dict

- acct nbr
- acct num
- acct no
- american express
- americanexpress
- americano espresso
- Amex
- atm-kort
- atmkort
- atm kaart
- atmcard
- atmcards
- atmkaart
- atmkaarten
- bancontact
- bankkort
- bankkaart
- Kortholderen
- kortholdere
- kortnummer
- kortnummer
- kortnumre
- korttype
- cardano numerico
- Kortindehaveren
- Kortholdere
- cardnumber
- cardnumbers
- carta bianca
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
- Cb
- Ccn
- kontrolkort
- tjek kort
- checkcard
- checkcards
- checkkaart
- Cirrus
- cirrus-edc-maestro
- controlekaart
- controlekaarten
- Kreditkort
- Kreditkort
- Kreditkort
- kreditkort
- debetkaart
- debetkaarten
- Betalingskort
- Betalingskort
- debetkort
- debetkort
- debito automatico
- diners club
- dinersclub
- Oplev
- find kort
- find kort
- discovercard
- discovercards
- débito automático
- Edc
- eigentümername
- europæisk debetkort
- hoofdkaart
- hoofdkaarten
- i viaggio
- japansk kortbureau
- japanse kaartdienst
- Jcb
- kaart
- kaartnummer
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
- Maestro
- masterkort
- masterkort
- Mastercard
- Mastercards
- Mc
- mister cash
- n carta
- Carta
- no de tarjeta
- ingen do cartao
- ingen do cartão
- Nej. de tarjeta
- Nej. do cartao
- Nej. do cartão
- nr. carta
- nr. Carta
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
- Nº. do cartão
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
- Solo
- supporti di scheda
- supporto di scheda
- Skifte
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
- Visa
- visum plus
- visumelektron
- Visto
- visum
- vpay

#### <a name="keyword_card_security_terms_dict"></a>Keyword_card_security_terms_dict

- kortidentifikationsnummer
- kortbekræftelse
- cardi la verifica
- Cid
- cod seg
- cod seguranca
- cod segurança
- cod sicurezza
- Torsk. Seg
- Torsk. seguranca
- Torsk. segurança
- Torsk. sicurezza
- codice di sicurezza
- codice di verifica
- codigo
- codigo de seguranca
- codigo de segurança
- crittogramma
- Kryptogram
- cryptogramme
- cv2
- Cvc
- cvc2
- Cvn
- Cvv
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
- problem nr.
- problemnummer
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
- numero van slørigheid
- numéro de sécurité
- nº autorizzazione
- número de verificação
- perno il blocco
- fastgørelsesblok
- prufziffer
- prüfziffer
- sikkerhedskode
- sikkerhed nr.
- sikkerhedsnummer
- sicherheits kode
- sicherheitscode
- sicherheitsnummer
- speldblok
- slørigheid nr.
- slørigheidsaantal
- slørigheidscode
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
- udløbsdato
- exp datum
- Udløb
- Udløber
- Udløber
- Udløbet
- fecha de expiracion
- fecha de venc
- gultig bis
- gultigkeitsdatum
- gültig bis
- gültigkeitsdatum
- la scadenza
- scadenza
- kan værdianegnes
- validade
- valido hasta
- Valor
- venc
- vencimento
- vencimiento
- verloopt
- vervaldag
- vervaldatum
- vto
- válido hasta

## <a name="eu-drivers-license-number"></a>EU-kørekortsnummer

Disse enheder findes i EU-kørekortsnummeret og er følsomme informationstyper.

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
- [Nederlandene](#netherlands-drivers-license-number)
- [Polen](#poland-drivers-license-number)
- [Portugal](#portugal-drivers-license-number)
- [Rumænien](#romania-drivers-license-number)
- [Slovakiet](#slovakia-drivers-license-number)
- [Slovenien](#slovenia-drivers-license-number)
- [Spanien](#spain-drivers-license-number)
- [Sverige](#sweden-drivers-license-number)
- [STORBRITANNIEN.](#uk-drivers-license-number)

## <a name="eu-national-identification-number"></a>EU-nationalt identifikationsnummer

Disse enheder findes i EU's nationale identifikationsnummer og er følsomme informationstyper.

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
- [Nederlandene](#netherlands-citizens-service-bsn-number)
- [Polen](#poland-national-id-pesel)
- [Portugal](#portugal-citizen-card-number)
- [Rumænien](#romania-personal-numeric-code-cnp)
- [Slovakiet](#slovakia-personal-number)
- [Slovenien](#slovenia-unique-master-citizen-number)
- [Spanien](#spain-dni)
- [STORBRITANNIEN.](#uk-national-insurance-number-nino)

## <a name="eu-passport-number"></a>EU-pasnummer

Disse enheder findes i EU-passets nummer og er følsomme oplysningstyper. Disse enheder er i EU-pasnummerbundtet.

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
- [Nederlandene](#netherlands-passport-number)
- [Polen](#poland-passport-number)
- [Portugal](#portugal-passport-number)
- [Rumænien](#romania-passport-number)
- [Slovakiet](#slovakia-passport-number)
- [Slovenien](#slovenia-passport-number)
- [Spanien](#spain-passport-number)
- [Sverige](#sweden-passport-number)
- [Amerikansk/britisk pasnummer](#usuk-passport-number)

## <a name="eu-social-security-number-or-equivalent-identification"></a>EU-cpr-nummer eller tilsvarende identifikation

Disse enheder findes i EU's cpr-nummer eller tilsvarende identifikation og er følsomme informationstyper.

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

## <a name="eu-tax-identification-number"></a>EU-skatteidentifikationsnummer

Disse enheder er i EU's type af følsomme oplysninger om skatteidentifikationsnummer.

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
- [Nederlandene](#netherlands-tax-identification-number)
- [Polen](#poland-tax-identification-number)
- [Portugal](#portugal-tax-identification-number)
- [Rumænien](#romania-personal-numeric-code-cnp)
- [Slovakiet](#slovakia-personal-number)
- [Slovenien](#slovenia-tax-identification-number)
- [Spanien](#spain-tax-identification-number)
- [Sverige](#sweden-tax-identification-number)
- [STORBRITANNIEN.](#uk-unique-taxpayer-reference-number)

## <a name="finland-drivers-license-number"></a>Finlands kørekortsnummer

### <a name="format"></a>Format

10 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

10 cifre, der indeholder en bindestreg:

- seks cifre
- en bindestreg
- tre cifre
- et ciffer eller bogstav

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_finland_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_finland_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_finland_eu_drivers_license_number"></a>Keywords_finland_eu_driver er s_license_number

- ajokortti
- permis de conduire
- ajokortin numero
- kuljettaja lic.
- körkort
- körkortnummer
- förare lic.
- ajokortit
- ajokortin numerot

## <a name="finland-european-health-insurance-number"></a>Finland europæisk sygesikringsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

20-cifret tal

### <a name="pattern"></a>Mønster

20-cifret tal:

- 10 cifre - 8024680246
- et valgfrit mellemrum eller en bindestreg
- 10 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Regex-Regex_Finland_European_Health_Insurance_Number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Finland_European_Health_Insurance_Number.

```xml
      <!-- Finland European Health Insurance Number -->
      <Entity id="60f75aed-81bf-4625-89b0-0846b9248ee7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Finland_European_Health_Insurance_Number"/>
          <Match idRef="Keyword_Finland_European_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Søgeord

#### <a name="keyword_finland_european_health_insurance_number"></a>Keyword_finland_european_health_insurance_number

- Sygesikringsbeviset #
- Sygesikringsbeviset
- finlandehicnumber #
- finska sjukförsäkringskort
- helbredskort
- Sygesikringskort
- sygesikringsnummer
- hälsokort
- sairaanhoitokortin
- sairausvakuutuskortti
- sairausvakuutusnumero
- sjukförsäkring nummer
- sjukförsäkringskort
- suomen sairausvakuutuskortti
- terveyskortti

## <a name="finland-national-id"></a>Finlands nationale id

### <a name="format"></a>Format

seks cifre plus et tegn, der angiver et århundrede plus tre cifre plus et kontrolciffer

### <a name="pattern"></a>Mønster

Mønsteret skal indeholde alle følgende:

- seks cifre i formatet DDMMYY, som er en fødselsdato
- century-mærke (enten '-', '+' eller 'a')
- trecifret personligt id-nummer
- et ciffer eller et bogstav (skelner ikke mellem store og små bogstaver), som er et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- funktionen Func_finnish_national_id finder indhold, der svarer til mønsteret
- der blev fundet et nøgleord fra Keyword_finnish_national_id
- kontrolsummen passerer

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- funktionen Func_finnish_national_id finder indhold, der svarer til mønsteret
- kontrolsummen passerer

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

### <a name="keywords"></a>Søgeord

- ainutlaatuinen henkilökohtainen tunnus
- henkilökohtainen tunnus
- henkilötunnus
- henkilötunnusnumero #
- henkilötunnusnumero
- hetu
- id nej
- id-nummer
- Identifikationsnummer
- identiteetti numero
- id-nummer
- idnumber
- kansallinen henkilötunnus
- kansallisen henkilökortin
- nationalt id-kort
- nationalt id-nr.
- personligt id
- kode for personlig identitet
- personalidnumber #
- personbeteckning
- personnummer
- CPR-nummer
- sosiaaliturvatunnus
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- tunnistenumero
- tunnus numero
- tunnusluku
- tunnusnumero
- verokortti
- veronumero
- verotunniste
- verotunnus

## <a name="finland-passport-number"></a>Finlands pasnummer

Denne enhed er tilgængelig i den følsomme informationstype for EU-pasnummer og er tilgængelig som en separat enhed med følsomme oplysninger.

### <a name="format"></a>Format
kombination af ni bogstaver og cifre

### <a name="pattern"></a>Mønster

kombination af ni bogstaver og cifre:

- to bogstaver (skelner ikke mellem store og små bogstaver)
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_finland_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_finland_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_finland_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_finland_passport_number` findes.

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
### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keyword_finland_passport_number"></a>Keyword_finland_passport_number

- suomalainen passi
- passin numero
- passin numero. #
- passin numero #
- passin numero.
- passi #
- passi-tal

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="finland-physical-addresses"></a>Fysiske adresser i Finland

Denne ubundtede navngivne enhed registrerer mønstre relateret til fysisk adresse fra Finland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="france-drivers-license-number"></a>Frankrigs kørekortsnummer

Denne enhed er tilgængelig i den følsomme informationstype for EU-kørekortsnummer og er tilgængelig som en separat enhed med følsomme oplysninger.

### <a name="format"></a>Format

12 cifre

### <a name="pattern"></a>Mønster

12 cifre med validering til rabat på lignende mønstre, f.eks. franske telefonnumre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- funktionen Func_french_drivers_license finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_french_drivers_license.

```xml
    <!-- France Driver's License Number -->
    <Entity id="18e55a36-a01b-4b0f-943d-dc10282a1824" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_french_drivers_license" />
        <Match idRef="Keyword_french_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_french_drivers_license"></a>Keyword_french_drivers_license

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer
- permis de conduire
- licensnummer
- licensnummer
- licensnumre
- licensnumre
- numéros de licence

## <a name="france-health-insurance-number"></a>Frankrig sygesikringsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

21-cifret tal

### <a name="pattern"></a>Mønster

21-cifret tal:

- 10 cifre
- et valgfrit mellemrum
- 10 cifre
- et valgfrit mellemrum
- et ciffer

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- regex-Regex_France_Health_Insurance_Number finder indhold, der svarer til mønsteret.
- der blev fundet et nøgleord fra Keyword_France_Health_Insurance_Number.

```xml
      <!-- France Health Insurance Number -->
      <Entity id="9bc2069e-76df-4ff9-ac02-2f519469e236" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_France_Health_Insurance_Number"/>
          <Match idRef="Keyword_France_Health_Insurance_Number"/>
        </Pattern>
      </Entity>
```
### <a name="keywords"></a>Søgeord

#### <a name="keyword_france_health_insurance_number"></a>Keyword_France_health_insurance_number

- forsikringskort
- carte vitale
- carte d'assuré social

## <a name="france-national-id-card-cni"></a>Nationalt id-kort for Frankrig (CNI)

### <a name="format"></a>Format

12 cifre

### <a name="pattern"></a>Mønster

12 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_france_cni finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_france_eu_national_id_card.

```xml
    <!-- France CNI -->
    <Entity id="f741ac74-1bc0-4665-b69b-f0c7f927c0c4" patternsProximity="300" recommendedConfidence="65">
      <Pattern confidenceLevel="65">
        <IdMatch idRef="Regex_france_cni" />
        <Match idRef="Keywords_france_eu_national_id_card" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_france_eu_national_id_card"></a>Keywords_france_eu_national_id_card

- kortnummer
- carte nationale d'identité
- carte nationale d'idenite no
- Cni #
- Cni
- compte bancaire
- nationalt identifikationsnummer
- national identitet
- nationalidno #
- numéro d'assurance maladie
- numéro de carte vitale

## <a name="france-passport-number"></a>Pasnummer for Frankrig

Denne enhed er tilgængelig i EU Passport Number følsomme oplysninger type. Den er også tilgængelig som et separat objekt af typen følsomme oplysninger.

### <a name="format"></a>Format

ni cifre og bogstaver

### <a name="pattern"></a>Mønster

ni cifre og bogstaver:

- to cifre
- to bogstaver (skelner ikke mellem store og små bogstaver)
- fem cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_fr_passport` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_france_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date3` finder datoen i formatet DD MM ÅÅÅÅ, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_fr_passport` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_france_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_france_eu_passport_number"></a>Keywords_france_eu_passport_number

- numéro de passeport
- passeport n °
- passeport ikke
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

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Frankrig. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="france-social-security-number-insee"></a>Det sociale sikringsnummer i Frankrig (INSEE)

### <a name="format"></a>Format

15 cifre

### <a name="pattern"></a>Mønster

Skal matche et af to mønstre:

- 13 cifre efterfulgt af et mellemrum efterfulgt af to cifre

  Eller

- 15 cifre i træk

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_french_insee` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_fr_insee.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_french_insee eller Func_fr_insee finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_fr_insee"></a>Keyword_fr_insee

- code sécu
- d'identité nationale
- Insee
- fssn #
- le numéro d'identification nationale
- le code de la sécurité sociale
- nationalt id
- nationalt identifikation
- no d'identité
- Nej. d'identité
- numéro d'assurance
- numéro d'identité
- numero d'identite
- numéro de sécu
- numéro de sécurité sociale
- ingen d'identite
- Nej. d'identite
- Ssn
- Ssn #
- sécurité sociale
- securité sociale
- securite sociale
- social sikringsnummer
- CPR-nummer
- kode for social sikring
- cpr-nummer

## <a name="france-tax-identification-number"></a>Frankrigs skatteidentifikationsnummer

### <a name="format"></a>Format

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

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_france_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_france_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_france_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_france_eu_tax_file_number"></a>Keywords_france_eu_tax_file_number

- numéro d'identification fiscale
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="france-value-added-tax-number"></a>Momsnummer for Frankrig

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 13 tegn

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 13 tegn:

- to bogstaver – FR (skelner ikke mellem store og små bogstaver)
- et valgfrit mellemrum eller en bindestreg
- to bogstaver eller cifre
- et valgfrit mellemrum, punktum, bindestreg eller komma
- tre cifre
- et valgfrit mellemrum, punktum, bindestreg eller komma
- tre cifre
- et valgfrit mellemrum, punktum, bindestreg eller komma
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_france_value_added_tax_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_france_value_added_tax_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_france_value_added_tax_number finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_france_value_added_tax_number"></a>Keyword_France_value_added_tax_number

- momsnummer
- momsnr.
- Moms #
- moms
- siren identifikation no numéro d'identification taxe sur valeur ajoutée
- taxe valeur ajoutée
- taxe sur la valeur ajoutée
- n° tva
- numéro de tva
- numéro d'identification sirene

## <a name="generic-medication-names"></a>Generiske medicinnavne

Denne ubundtede navngivne enhed registrerer navne på generiske lægemidler, f.eks *acetaminophen*. Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="germany-drivers-license-number"></a>Tysklands kørekortsnummer

Denne enhed af typen af følsomme oplysninger er inkluderet i den følsomme informationstype for EU-kørekortsnummer. Den er også tilgængelig som et separat objekt af typen følsomme oplysninger.

### <a name="format"></a>Format

kombination af 11 cifre og bogstaver

### <a name="pattern"></a>Mønster

11 cifre og bogstaver (skelner ikke mellem store og små bogstaver):

- et ciffer eller bogstav
- to cifre
- seks cifre eller bogstaver
- et ciffer
- et ciffer eller bogstav

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_german_drivers_license finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_german_drivers_license_number.
- Kontrolsummen passerer.

```xml
    <!-- German Driver's License Number -->
    <Entity id="91da9335-1edb-45b7-a95f-5fe41a16c63c" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_german_drivers_license" />
        <Match idRef="Keyword_german_drivers_license" />
      </Pattern>
    </Entity>
```

### <a name="keywords"></a>Søgeord

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
- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dlno

## <a name="germany-identity-card-number"></a>Tysklands identitetskortnummer

### <a name="format"></a>Format

siden 1. november 2010: Ni til 11 bogstaver og cifre

fra 1. april 1987 til 31. oktober 2010: 10 cifre

### <a name="pattern"></a>Mønster

siden 1. november 2010: 9 til 11 tegn alfanumerisk mønster
- en L, M, N, P, R, T, V, W, X, Y (skelner ikke mellem store og små bogstaver)
- otte cifre eller bogstaver i C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y og Z (uden forskel på store og små bogstaver)
- valgfri kontrolciffer
- Valgfri d/D

fra 1. april 1987 til 31. oktober 2010:

- 10 cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_german_id_card_with_check` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_germany_id_card` .
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_germany_id_card` finder indhold, der svarer til mønsteret (9 tegn uden kontrolciffer udstedt før 2010 eller 10 cifre udstedt i 2010).
- Der blev fundet et nøgleord fra Keyword_germany_id_card.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_german_id_card_with_check` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_germany_id_card"></a>Keyword_germany_id_card

- ausweis
- gpid
- Identifikation
- identifikation
- identifizierungsnummer
- Identitetskort
- id-nummer
- id-nummer
- personligt id
- personalausweis
- persönliche id nummer
- persönliche identifikationsnummer
- persönliche-id-nummer

## <a name="germany-passport-number"></a>Tysklands pasnummer

### <a name="format"></a>Format

9 til 11 tegn

### <a name="pattern"></a>Mønster

- ét bogstav i C, F, G, H, J, K (forskel på store og små bogstaver)
- otte cifre eller bogstaver i C, F, G, H, J, K, L, M, N, P, R, T, V, W, X, Y og Z (uden forskel på store og små bogstaver)
- valgfri kontrolciffer
- Valgfri d/D

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_german_passport_checksum` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keyword_german_passport` eller `Keywords_eu_passport_number_common` findes.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_german_passport` finder indhold, der svarer til mønsteret på ni tegn (uden kontrolcifre og valgfri d/D).
- Et nøgleord fra `Keyword_german_passport` eller `Keywords_eu_passport_number_common` findes.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_german_passport_checksum` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_german_passport"></a>Keyword_german_passport

- reisepasse
- reisepassnummer
- No-Reisepass
- Nr-Reisepass
- Reisepass-Nr
- Passnummer
- reisepässe
- passeportnr.
- passeport nej

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

## <a name="germany-physical-addresses"></a>Fysiske adresser i Tyskland

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Tyskland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="germany-tax-identification-number"></a>Tysklands skatteidentifikationsnummer

### <a name="format"></a>Format

11 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

11 cifre

- To cifre
- Et valgfrit mellemrum
- Tre cifre
- Et valgfrit mellemrum
- Tre cifre
- Et valgfrit mellemrum
- To cifre
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_germany_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_germany_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_germany_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- steuer-id
- steueridentifikationsnummer
- steuernummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- Zinn #
- Zinn
- zinnnummer

## <a name="germany-value-added-tax-number"></a>Momsnummer for Tyskland

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 11 tegn

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 11 tegn:

- et D eller d
- et bogstav E eller e
- et valgfrit mellemrum
- tre cifre
- et valgfrit mellemrum eller komma
- tre cifre
- et valgfrit mellemrum eller komma
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_germany_value_added_tax_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_germany_value_added_tax_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_germany_value_added_tax_number finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_germany_value_added_tax_number"></a>Keyword_germany_value_added_tax_number

- momsnummer
- momsnr.
- Moms #
- vat# mehrwertsteuer
- mwst
- mehrwertsteuer identifikationsnummer
- mehrwertsteuer nummer

## <a name="greece-drivers-license-number"></a>Grækenlands kørekortsnummer

Denne enhed er inkluderet i den følsomme informationstype for EU-kørekortsnummer. Den er også tilgængelig som et separat objekt af typen følsomme oplysninger.

### <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_greece_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_greece_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_greece_eu_drivers_license_number"></a>Keywords_greece_eu_driver er s_license_number

- δεια οδήγησης
- Adeia odigisis
- Άδεια οδήγησης
- Δίπλωμα οδήγησης

## <a name="greece-national-id-card"></a>Nationalt id-kort for Grækenland

### <a name="format"></a>Format

Kombination af 7-8 bogstaver og tal plus en streg

### <a name="pattern"></a>Mønster

Syv bogstaver og tal (gammelt format):

- Et bogstav (ethvert bogstav i det græske alfabet)
- En streg
- Seks cifre

Otte bogstaver og tal (nyt format):

- To bogstaver, hvis store bogstaver forekommer i både det græske og det latinske alfabet (ABEZHIKMNOPTYX)
- En streg
- Seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_greece_id_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_greece_id_card.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_greece_id_card finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- græsk id
- græsk nationalt id
- græsk personligt id-kort
- græsk politi-id
- Identitetskort
- tautotita
- ταυτότητα
- ταυτότητας

## <a name="greece-passport-number"></a>Pasnummer for Grækenland

### <a name="format"></a>Format

To bogstaver efterfulgt af syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

To bogstaver efterfulgt af syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_greece_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_greece_eu_passport_number` findes.
- Det regulære udtryk `Regex_greece_eu_passport_date` finder dato i formatet DD MMM YY (f.eks. 28. august 19), eller der findes et nøgleord fra `Keywords_greece_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_greece_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_greece_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_greece_eu_passport_number"></a>Keywords_greece_eu_passport_number

- αριθμός διαβατηρίου
- αριθμούς διαβατηρίου
- αριθμός διαβατηριο

## <a name="greece-physical-addresses"></a>Fysiske adresser for Grækenland

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Grækenland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="greece-social-security-number-amka"></a>Det græske cpr-nummer (AMKA)

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

- Seks cifre som fødselsdato YYMMDD
- Fire cifre
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_greece_eu_ssn` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_greece_eu_ssn_or_equivalent` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_greece_eu_ssn` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_greece_eu_ssn_or_equivalent"></a>Keywords_greece_eu_ssn_or_equivalent

- Ssn
- Ssn #
- social sikring nr.
- social sikringno #
- CPR-nummer
- amka
- a.m.k.a.
- Αριθμού Μητρώου Κοινωνικής Ασφάλισης

## <a name="greece-tax-identification-number"></a>Grækenlands skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

Ni cifre

### <a name="checksum"></a>Checksum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_greece_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_greece_eu_tax_file_number` .

```xml
      <!-- Greek Tax Identification Number -->
      <Entity id="15a54a5a-53d4-4080-ad43-a2a4fe1d3bf7" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_greece_eu_tax_file_number" />
          <Match idRef="Keywords_greece_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_greece_eu_tax_file_number"></a>Keywords_greece_eu_tax_file_number

- Afm #
- Afm
- aφμ|aφμ αριθμός
- aφμ
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- skatteregistreringsnr.
- skatteregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- taxregistryno #
- tin-id
- tin no
- Tin #
- αριθμός φορολογικού μητρώου
- τον αριθμό φορολογικού μητρώου
- φορολογικού μητρώου νο

## <a name="hong-kong-identity-card-hkid-number"></a>HONGKONG-id-nummer (HKID)

### <a name="format"></a>Format

Kombination af 8-9 bogstaver og tal plus valgfri parenteser omkring det endelige tegn

### <a name="pattern"></a>Mønster

Kombination af 8-9 bogstaver:

- 1-2 bogstaver (skelner ikke mellem store og små bogstaver)
- Seks cifre
- valgfri plads
- et kontroltegn (et vilkårligt ciffer eller bogstavet A), som eventuelt er omsluttet af parenteser

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_hong_kong_id_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_hong_kong_id_card.
- Kontrolsummen passerer.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_hong_kong_id_card finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_hong_kong_id_card"></a>Keyword_hong_kong_id_card

- hkid
- hongkong-id-kort
- HKIDC
- id-kort
- Identitetskort
- hk-id-kort
- hongkong-id
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

## <a name="hungary-drivers-license-number"></a>Ungarns kørekortsnummer

### <a name="format"></a>Format

To bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

To bogstaver og seks cifre:

- To bogstaver (skelner ikke mellem store og små bogstaver)
- Seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_hungary_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_hungary_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_hungary_eu_drivers_license_number"></a>Keywords_hungary_eu_driver s_license_number

- vezetoi engedely
- vezetői engedély
- vezetői engedélyek

## <a name="hungary-passport-number"></a>Pasnummer til Ungarn

### <a name="format"></a>Format

To bogstaver efterfulgt af seks eller syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

To bogstaver efterfulgt af seks eller syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_hungary_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_hungary_eu_passport_number` findes.
- Det regulære udtryk `Regex_hungary_eu_passport_date` finder dato i formatet DD MMM/MMM YYY (f.eks. 01 MÁR/MAR 12), eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_hungary_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_hungary_eu_passport_number` findes.

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
### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_hungary_eu_passport_number"></a>Keywords_hungary_eu_passport_number

- útlevél száma
- Útlevelek száma
- útlevél szám

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="hungary-personal-identification-number"></a>Ungarns personidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

11 cifre:

- Et ciffer, der svarer til køn, 1 for mand, 2 for kvinder. Andre tal er også mulige for borgere født før 1900 eller borgere med dobbelt statsborgerskab.
- Seks cifre, der svarer til fødselsdatoen (YYMMDD)
- Tre cifre, der svarer til et serienummer
- Et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_hungary_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_hungary_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_hungary_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_hungary_eu_national_id_card"></a>Keywords_hungary_eu_national_id_card

- id-nummer
- Identifikationsnummer
- sz ig
- Sz. Ig.
- sz.ig.
- személyazonosító igazolvány
- személyi igazolvány

## <a name="hungary-physical-addresses"></a>Fysiske adresser til Ungarn

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Ungarn. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="hungary-social-security-number-taj"></a>Ungarn cpr-nummer (TAJ)

### <a name="format"></a>Format

Ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

Ni cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_hungary_eu_ssn_or_equivalent` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_hungary_eu_ssn_or_equivalent` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_hungary_eu_ssn_or_equivalent` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_hungary_eu_ssn_or_equivalent"></a>Keywords_hungary_eu_ssn_or_equivalent

- ungarsk cpr-nummer
- CPR-nummer
- social sikringsnummer #
- hssn #
- social sikringn
- hssn
- Taj
- Taj #
- Ssn
- Ssn #
- social sikring nr.
- áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám
- magyar áfa szám

## <a name="hungary-tax-identification-number"></a>Ungarns skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

10 cifre:

- Et ciffer, der skal være "8"
- Otte cifre
- Et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_hungary_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_hungary_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_hungary_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_hungary_eu_tax_file_number"></a>Keywords_hungary_eu_tax_file_number

- adóazonosító szám
- adóhatóság szám
- adószám
- ungarsk tin
- hungatiantin #
- skattemyndighed nr.
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- momsnummer

## <a name="hungary-value-added-tax-number"></a>Momsnummer for Ungarn

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 10 tegn

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 10 tegn:

- to bogstaver – HU eller hu
- valgfri plads
- otte cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_hungarian_value_added_tax_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_hungarian_value_added_tax_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_hungarian_value_added_tax_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_hungary_value_added_tax_number"></a>Keyword_Hungary_value_added_tax_number

- Moms
- momsnummer
- Moms #
- vatno #
- ungarskvatno #
- skattenr.
- value added tax áfa
- közösségi adószám
- általános forgalmi adó szám
- hozzáadottérték adó
- áfa szám

## <a name="iceland-physical-addresses"></a>Fysiske adresser på Island

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Island. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="impairments-listed-in-the-us-disability-evaluation-under-social-security"></a>Nedskrivninger opført i USA handicap evaluering under social sikring

Denne ubundtede navngivne enhed registrerer navne på handicap, der er opført i USA handicap evaluering under social sikring, såsom *muskuløs dystrofi*. Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="india-drivers-license-number"></a>Indiens kørekortsnummer

### <a name="format"></a>Format

Alfanumerisk mønster på 15 tegn

### <a name="pattern"></a>Mønster

15 bogstaver eller cifre:

- to bogstaver, der angiver statskode
- valgfri mellemrum eller tankestreg
- to cifre, der angiver bykode
- valgfri mellemrum eller tankestreg
- fire cifre, der angiver udstedelsesår
- valgfri mellemrum eller tankestreg
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_india_driving_license` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_eu_driver's_license_number_common` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver s_license_number_common

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

## <a name="india-gst-number"></a>IndienST-nummer

### <a name="format"></a>Format

Alfanumerisk mønster på 15 tegn

### <a name="pattern"></a>Mønster

15 bogstaver eller cifre:

- to cifre, der repræsenterer gyldig tilstandskode
- et valgfrit mellemrum eller en streg
- ti tegn, der repræsenterer permanent kontonummer (PAN)
- et bogstav eller et ciffer
- et valgfrit mellemrum eller en streg
- et bogstav 'z' eller 'Z'
- et valgfrit mellemrum eller en streg
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_india_gst_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_india_gst_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_india_gst_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Gst
- gstin
- skat på varer og tjenesteydelser
- vare- og tjenesteskat

## <a name="india-permanent-account-number-pan"></a>Permanent kontonummer for Indien (PAN)

### <a name="format"></a>Format

10 bogstaver eller cifre

### <a name="pattern"></a>Mønster

10 bogstaver eller cifre:

- Tre bogstaver (skelner ikke mellem store og små bogstaver)
- Et bogstav i C, P, H, F, A, T, B, L, J, G (ikke forskel på store og små bogstaver)
- Et bogstav
- Fire cifre
- Et bogstav, der er et alfabetisk kontrolciffer

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_india_permanent_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_india_permanent_account_number.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_india_permanent_account_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent kontonummer
- PAN

## <a name="india-unique-identification-aadhaar-number"></a>Entydigt id for Indien (Aadhaar)

### <a name="format"></a>Format

12 cifre, der indeholder valgfri mellemrum eller tankestreger

### <a name="pattern"></a>Mønster

12 cifre:

- Et ciffer, der ikke er 0 eller 1
- Tre cifre
- Et valgfrit mellemrum eller en streg
- Fire cifre
- Et valgfrit mellemrum eller en streg
- Det endelige ciffer, som er kontrolcifferet

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_india_aadhaar finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_india_aadhar.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_india_aadhaar finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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
### <a name="keywords"></a>Søgeord

#### <a name="keyword_india_aadhar"></a>Keyword_india_aadhar
- aadhaar
- aadhar
- aadhar #
- Uid
- आधार
- uidai

## <a name="india-voter-id-card"></a>Vælger-id-kort til Indien

### <a name="format"></a>Format

Alfanumerisk mønster på 10 tegn

### <a name="pattern"></a>Mønster

10 bogstaver eller cifre:

- tre bogstaver
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_india_voter_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_india_voter_id_card` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_india_voter_id_card"></a>Keyword_india_voter_id_card

- Vælgere
- voterid
- vælgerkort
- voteridcard
- valgfoto-id-kort
- EPISKE
- HEV
- valgkommission

## <a name="indonesia-identity-card-ktp-number"></a>Indonesiens identitetskortnummer (KTP)

### <a name="format"></a>Format

16 cifre, der indeholder valgfrie punktummer

### <a name="pattern"></a>Mønster

16 cifre:

- Tocifret provinskode
- Et punktum (valgfrit)
- Tocifret regency eller bykode
- Tocifret underdistriktkode
- Et punktum (valgfrit)
- Seks cifre i formatet DDMMYY, som er fødselsdato
- Et punktum (valgfrit)
- Fire cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_indonesia_id_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_indonesia_id_card.

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan

## <a name="international-banking-account-number-iban"></a>Internationalt bankkontonummer (IBAN)

### <a name="format"></a>Format

Landekode (to bogstaver) plus kontrolcifre (to cifre) plus bban-tal (op til 30 tegn)

### <a name="pattern"></a>Mønster

Mønsteret skal indeholde alle følgende:

- Landekode på to bogstaver
- To kontrolcifre (efterfulgt af et valgfrit mellemrum)
- 1-7 grupper af fire bogstaver eller cifre (kan adskilles af mellemrum)
- 1-3 bogstaver eller cifre

Formatet for hvert land er lidt forskelligt. IBAN-typen af følsomme oplysninger dækker disse 60 lande:

- Ad
- Ae
- Al
- På
- Az
- Ba
- Være
- Bg
- bh
- Ch
- Cr
- Cy
- Cz
- de
- Dk
- Gør
- Ee
- Es
- Fi
- fo
- Fr
- Gb
- Ge
- Gi
- Gl
- Gr
- Hr
- Hu
- Dvs
- Il
- Er
- Det
- Kw
- Kz
- Lb
- Li
- Lt
- Lu
- Lv
- Mc
- Md
- Mig
- Mark
- Mr
- Mt
- Mu
- Nl
- Nej
- Pl
- Pt
- Ro
- rs
- Sa
- se
- Si
- Sk
- Sm
- Tn
- Tr
- Vg

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_iban finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

```xml
<Entity id="e7dc4711-11b7-4cb0-b88b-2c394a771f0e" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_iban" />
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

Ingen

## <a name="international-classification-of-diseases-icd-10-cm"></a>International klassificering af sygdomme (ICD-10-CM)

### <a name="format"></a>Format

Ordbog

### <a name="pattern"></a>Mønster

Søgeord

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Der blev fundet et nøgleord fra Dictionary_icd_10_updated.
- Der blev fundet et nøgleord fra Dictionary_icd_10_codes.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Der blev fundet et nøgleord fra Dictionary_icd_10_ opdaterede.

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

### <a name="keywords"></a>Søgeord

Ethvert ord fra nøgleordsordbogen for Dictionary_icd_10_updated, som er baseret på [International Classification of Diseases, Tenth Revision, Clinical Modification (ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604). Denne type søger kun efter ordet og ikke forsikringskoderne.

Ethvert ord fra nøgleordsordbogen for Dictionary_icd_10_codes, som er baseret på [International Classification of Diseases, Tenth Revision, Clinical Modification (ICD-10-CM)](https://go.microsoft.com/fwlink/?linkid=852604). Denne type søger kun efter forsikringskoder og ikke beskrivelsen.

## <a name="international-classification-of-diseases-icd-9-cm"></a>International klassificering af sygdomme (ICD-9-CM)

### <a name="format"></a>Format

Ordbog

### <a name="pattern"></a>Mønster

Søgeord

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Der blev fundet et nøgleord fra Dictionary_icd_9_updated.
- Der blev fundet et nøgleord fra Dictionary_icd_9_codes.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Der blev fundet et nøgleord fra Dictionary_icd_9_updated.

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

### <a name="keywords"></a>Søgeord

Ethvert udtryk fra nøgleordsordbogen for Dictionary_icd_9_updated, som er baseret på [International Classification of Diseases,Niende Revision, Klinisk Modifikation (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Denne type søger kun efter ordet og ikke forsikringskoderne.

Ethvert ord fra den Dictionary_icd_9_codes nøgleordsordbog, som er baseret på [International Classification of Diseases,Niende Revision, Klinisk Modifikation (ICD-9-CM)](https://go.microsoft.com/fwlink/?linkid=852605). Denne type søger kun efter forsikringskoder og ikke beskrivelsen.

## <a name="ip-address"></a>IP-adresse

### <a name="format"></a>Format

#### <a name="ipv4"></a>IPv4:
Komplekst mønster, der står for formaterede (punktummer) og ikke-formaterede (ingen punktummer) versioner af IPv4-adresserne

#### <a name="ipv6"></a>IPv6:
Komplekst mønster, der står for formaterede IPv6-tal (herunder kolon)

### <a name="pattern"></a>Mønster

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

For IPv6 har en DLP-politik stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger på 300 tegn:

- Det regulære udtryk Regex_ipv6_address finder indhold, der svarer til mønsteret.
- Der blev ikke fundet et nøgleord fra Keyword_ipaddress.

For IPv4 har en DLP-politik stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_ipv4_address finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_ipaddress.

For IPv6 har en DLP-politik stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger på 300 tegn:

- Det regulære udtryk Regex_ipv6_address finder indhold, der svarer til mønsteret.
- Der blev ikke fundet et nøgleord fra Keyword_ipaddress.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (dette nøgleord skelner mellem store og små bogstaver)
- ip-adresse
- ip-adresser
- internetprotokol
- IP-כתובת ה

## <a name="ip-address-v4"></a>IP-adresse v4

### <a name="format"></a>Format

Komplekst mønster, der står for formaterede (punktummer) og ikke-formaterede (ingen punktummer) versioner af IPv4-adresserne

### <a name="pattern"></a>Mønster

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_ipv4_address` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_ipaddress` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (forskel på store og små bogstaver)
- ip-adresse
- ip-adresser
- internetprotokol
- IP-כתובת ה

## <a name="ip-address-v6"></a>IP-adresse v6

### <a name="format"></a>Format

Komplekst mønster, der står for formaterede IPv6-tal (herunder kolon)

### <a name="pattern"></a>Mønster

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_ipv6_address` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_ipaddress` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (forskel på store og små bogstaver)
- ip-adresse
- ip-adresser
- internetprotokol
- IP-כתובת ה

## <a name="ireland-drivers-license-number"></a>Irlands kørekortsnummer

### <a name="format"></a>Format

Seks cifre efterfulgt af fire bogstaver

### <a name="pattern"></a>Mønster

Seks cifre og fire bogstaver:

- Seks cifre
- Fire bogstaver (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_ireland_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_ireland_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_ireland_eu_drivers_license_number"></a>Keywords_ireland_eu_driver er s_license_number

- ceadúnas tiomána
- ceadúnais tiomána

## <a name="ireland-passport-number"></a>Irlands pasnummer

### <a name="format"></a>Format

To bogstaver eller cifre efterfulgt af syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

To bogstaver eller cifre efterfulgt af syv cifre:

- To cifre eller bogstaver (skelner ikke mellem store og små bogstaver)
- Syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_ireland_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_ireland_eu_passport_number` findes.
- Det regulære udtryk `Regex_ireland_eu_passport_date` finder dato i formatet DD MMM/MMM YYYY (f.eks. 01 BEA/MAJ 1988), eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_ireland_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_ireland_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_ireland_eu_passport_number"></a>Keywords_ireland_eu_passport_number

- passeport numero
- uimhreacha pasanna
- uimhir pas
- uimhir phas
- uimhreacha pas
- uimhir cárta
- uimhir chárta

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="ireland-personal-public-service-pps-number"></a>Irlands personlige offentlige tjeneste (PPS)

### <a name="format"></a>Format

Gammelt format (indtil 31. december 2012):

- syv cifre efterfulgt af 1-2 bogstaver

Nyt format (1. januar 2013 og efter):

- syv cifre efterfulgt af to bogstaver

### <a name="pattern"></a>Mønster

Gammelt format (indtil 31. december 2012):

- syv cifre
- et til to bogstaver (skelner ikke mellem store og små bogstaver)

Nyt format (1. januar 2013 og efter):

- syv cifre
- et bogstav (ikke forskel på store og små bogstaver), som er et alfabetisk kontrolciffer
- Et valgfrit bogstav i området A-I eller "W"

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_ireland_pps finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_ireland_eu_national_id_card.
- Kontrolsummen passerer.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_ireland_pps finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_ireland_eu_national_id_card"></a>Keywords_ireland_eu_national_id_card

- klientidentitetstjeneste
- Identifikationsnummer
- personligt id-nummer
- personligt nummer på offentlig tjeneste
- personlig tjeneste nr.
- phearsanta seirbhíse poiblí
- pps no
- pps-nummer
- pps num
- pps-tjenestenr.
- ppsn
- ppsno #
- ppsno
- Psp
- public service-nr.
- offentlig tjenesteno #
- offentlig tjenesteno
- indtægt og cpr-nummer
- rsi no
- rsi-nummer
- rsin
- seirbhís aitheantais client
- uimh
- uimhir aitheantais chánach
- uimhir aitheantais phearsanta
- uimhir phearsanta seirbhíse poiblí
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="ireland-physical-addresses"></a>Fysiske adresser for Irland

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Irland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="israel-bank-account-number"></a>Israels bankkontonummer

### <a name="format"></a>Format

13 cifre

### <a name="pattern"></a>Mønster

Formateret:

- to cifre
- en streg
- tre cifre
- en streg
- otte cifre

Uformateret:

- 13 cifre i træk

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_israel_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_israel_bank_account_number.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_israel_bank_account_number"></a>Keyword_israel_bank_account_number

- Bankkontonummer
- Bankkonto
- Kontonummer
- מספר חשבון בנק

## <a name="israel-national-identification-number"></a>Israels nationale identifikationsnummer

### <a name="format"></a>Format

ni cifre

### <a name="pattern"></a>Mønster

ni cifre i træk

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_israeli_national_id_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Israel_National_ID.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_israel_national_id"></a>Keyword_Israel_National_ID

- מספר זהות
- מספר זיה וי
- מספר זיהוי ישר אלי
- זהותישר אלית
- هو ية اسرائيل ية عدد
- هوية إسرائ يلية
- رقم الهوية
- عدد هوية فريدة من نوعها
- idnumber #
- id-nummer
- identitet nr.
- identitynumber #
- id-nummer
- israeliidentitynumber
- personligt id
- entydigt id

## <a name="italy-drivers-license-number"></a>Italiens kørekortsnummer

Denne type enhed er inkluderet i den følsomme informationstype for EU-kørekortsnummer. Den er også tilgængelig som et separat objekt af typen følsomme oplysninger.

### <a name="format"></a>Format

en kombination af 10 bogstaver og cifre

### <a name="pattern"></a>Mønster

en kombination af 10 bogstaver og cifre:

- ét bogstav (skelner ikke mellem store og små bogstaver)
- bogstavet "A" eller "V" (skelner ikke mellem store og små bogstaver)
- syv cifre
- ét bogstav (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_italy_drivers_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keyword_italy_drivers_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keyword_italy_drivers_license_number"></a>Keyword_italy_drivers_license_number

- numero di patente
- patente di guida
- patente guida
- patenti di guida
- patenti guida

## <a name="italy-fiscal-code"></a>Regnskabskode for Italien
Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

en kombination af bogstaver og cifre på 16 tegn i det angivne mønster

### <a name="pattern"></a>Mønster

En kombination af bogstaver og cifre på 16 tegn:

- tre bogstaver, der svarer til de første tre konsonanter i familiens navn
- tre bogstaver, der svarer til første, tredje og fjerde konsonanter i fornavnet
- to cifre, der svarer til de sidste cifre i fødselsåret
- ét bogstav, der svarer til fødselsmåneden – bogstaver bruges i alfabetisk rækkefølge, men kun bogstaverne A til E, H, L, M, P, R til T bruges (så januar er A og oktober er R)
- to cifre, der svarer til fødselsdagen for at skelne mellem køn, lægges 40 til fødselsdagen for kvinder
- fire cifre, der svarer til den områdekode, der er specifik for den kommune, hvor personen er født (landsdækkende koder bruges til udlandet)
- et paritetsciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_italy_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_italy_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_italy_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_italy_eu_national_id_card"></a>Keywords_italy_eu_national_id_card

- codice fiscal
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
- skattekode
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="italy-passport-number"></a>Pasnummer for Italien

### <a name="format"></a>Format

to bogstaver eller cifre efterfulgt af syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

to bogstaver eller cifre efterfulgt af syv cifre:

- to cifre eller bogstaver (skelner ikke mellem store og små bogstaver)
- syv cifre

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_italy_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_italy_eu_passport_number` findes.
- Det regulære udtryk `Regex_italy_eu_passport_date` finder dato i formatet DD MMM/MMM YYYY (f.eks. 01 GEN/JAN 1988), eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_italy_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_italy_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_italy_eu_passport_number"></a>Keywords_italy_eu_passport_number

- italiana passaporto
- passaporto italiana
- passaporto numero
- numéro passeport
- numero di passaporto
- numeri del passaporto
- passeport italien

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="italy-physical-addresses"></a>Fysiske adresser for Italien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Italien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="italy-value-added-tax-number"></a>Italien momsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 13 tegn med valgfri afgrænsere

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 13 tegn med valgfri afgrænsere:

- I eller i
- T eller t
- valgfrit mellemrum, punktum, bindestreg eller komma
- 11 cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_italy_value_added_tax_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_italy_value_added_tax_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_italy_value_added_tax_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_italy_value_added_tax_number"></a>Keyword_italy_value_added_tax_number

- momsnummer
- momsnr.
- Moms #
- Iva
- Iva #

## <a name="japan-bank-account-number"></a>Japans bankkontonummer

### <a name="format"></a>Format

syv eller otte cifre

### <a name="pattern"></a>Mønster

bankkontonummer:

- syv eller otte cifre
- forgreningskode for bankkonto:

- fire cifre
- et mellemrum eller en streg (valgfrit)
- tre cifre

Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_jp_bank_account finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_bank_account.
- Et af følgende er sandt:

- Funktionen Func_jp_bank_account_branch_code finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_bank_branch_code.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_jp_bank_account finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_bank_account.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_jp_bank_account"></a>Keyword_jp_bank_account

- Kontrol af kontonummer
- Kontrol af konto
- Kontrol af konto #
- Kontrollerer tilgængelighedsnummer
- Kontrollerer tilgængelighed #
- Kontrollerer tilgængelighedsnr.
- Kontrollerer kontonr.
- Bankkontonummer
- Bankkonto
- Bankkonto #
- Kontonummer for bank
- Bankkonto #
- Kontonr.
- Bankkontonr.
- Opsparingskontonummer
- Opsparingskonto
- Opsparingskonto #
- Opsparingsacctnummer
- Opsparingsacct #
- Opsparingskontonr.
- Opsparingskontonr.
- Debetkontonummer
- Debetkonto
- Debetkonto #
- Debiteringskontonummer
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

## <a name="japan-drivers-license-number"></a>Japans kørekortsnummer

### <a name="format"></a>Format

12 cifre

### <a name="pattern"></a>Mønster

12 cifre efter hinanden

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_jp_drivers_license_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_drivers_license_number.

```xml
<!-- Japan Driver's License Number -->
<Entity id="c6011143-d087-451c-8313-7f6d4aed2270" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_drivers_license_number" />
        <Match idRef ="Keyword_jp_drivers_license_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_jp_drivers_license_number"></a>Keyword_jp_drivers_license_number

- driverlicense
- driverslicense
- kørekort
- driverslicenses
- kørekort
- driverlicenses
- Dl #
- Dls #
- Lic #
- Lic'er #
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
- 免許No.
- 運転免許証 #
- 運転免許 #
- 免許証 #
- 免許 #

## <a name="japan-my-number---corporate"></a>Japan Mit nummer - Firma

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13-cifret tal

### <a name="pattern"></a>Mønster

13-cifret tal:

- et ciffer fra et til ni
- 12 cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_japanese_my_number_corporate finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_japanese_my_number_corporate.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_japanese_my_number_corporate finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

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

## <a name="japan-my-number---personal"></a>Japan Mit nummer - personlig

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

12-cifret tal

### <a name="pattern"></a>Mønster

12-cifret tal:

- fire cifre
- et valgfrit mellemrum, en prik eller en bindestreg
- fire cifre
- et valgfrit mellemrum, en prik eller en bindestreg
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_japanese_my_number_personal finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_japanese_my_number_personal.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_japanese_my_number_personal finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

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

## <a name="japan-passport-number"></a>Pasnummer til Japan

### <a name="format"></a>Format

to bogstaver efterfulgt af syv cifre

### <a name="pattern"></a>Mønster

to bogstaver (skelner ikke mellem store og små bogstaver) efterfulgt af syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_jp_passport finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_passport.

```xml
<!-- Japan Passport Number -->
<Entity id="75177310-1a09-4613-bf6d-833aae3743f8" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_passport" />
        <Match idRef="Keyword_jp_passport" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_jp_passport"></a>Keyword_jp_passport

- Passport
- Passport-nummer
- Pas nr.
- Passport #
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

## <a name="japan-residence-card-number"></a>Opholdskortnummer for Japan

### <a name="format"></a>Format

12 bogstaver og cifre

### <a name="pattern"></a>Mønster

12 bogstaver og cifre:

- to bogstaver (skelner ikke mellem store og små bogstaver)
- otte cifre
- to bogstaver (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_jp_residence_card_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_residence_card_number.

```xml
<!--Japan Residence Card Number-->
-<Entity id="ac36fef2-a289-4e2c-bb48-b02366e89fc0" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_jp_residence_card_number"/>
      <Match idRef="Keyword_jp_residence_card_number"/>
   </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_jp_residence_card_number"></a>Keyword_jp_residence_card_number

- Bopælskortnummer
- Bopælskort nr.
- Bopælskort #
- 在留カード番号
- 在留カード
- 在留番号

## <a name="japan-resident-registration-number"></a>Registreringsnummer for beboere i Japan

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

11 cifre efter hinanden

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_jp_resident_registration_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_resident_registration_number.

```xml
<!-- Japan Resident Registration Number -->
<Entity id="01c1209b-6389-4faf-a5f8-3f7e13899652" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_jp_resident_registration_number" />
        <Match idRef ="Keyword_jp_resident_registration_number" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_jp_resident_registration_number"></a>Keyword_jp_resident_registration_number

- Resident Registration Number
- Resident Basic Registry Number
- Resident Registration No.
- Resident Register No.
- Resident Basic Registry No.
- Standardregisternr.
- 外国人登録証明書番号
- 証明書番号
- 登録番号
- 外国人登録証

## <a name="japan-social-insurance-number-sin"></a>Japan socialforsikring nummer (SIN)

### <a name="format"></a>Format

7-12 cifre

### <a name="pattern"></a>Mønster

7-12 cifre:

- fire cifre
- en bindestreg (valgfrit)
- seks cifre ELLER
- 7-12 cifre i træk

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_jp_sin finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_sin.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_jp_sin_pre_1997 finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_jp_sin.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_jp_sin"></a>Keyword_jp_sin

- Socialforsikringsnr.
- Antal socialforsikringer
- Cpr-nummer
- 健康保険被保険者番号
- 健保番号
- 基礎年金番号
- 雇用保険被保険者番号
- 雇用保険番号
- 保険証番号
- 社会保険番号
- 社会保険No.
- 社会保険
- 介護保険
- 介護保険被保険者番号
- 健康保険被保険者整理番号
- 雇用保険被保険者整理番号
- 厚生年金
- 厚生年金被保険者整理番号

## <a name="lab-test-terms"></a>Testbetingelser for laboratorie

Denne ubundtede navngivne enhed registrerer begreber, der er relateret til laboratorietests, f.eks *. Insulin C-peptid.* Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="latvia-drivers-license-number"></a>Letlands kørekortsnummer

### <a name="format"></a>Format

tre bogstaver efterfulgt af seks cifre

### <a name="pattern"></a>Mønster

tre bogstaver og seks cifre:

- tre bogstaver (skelner ikke mellem store og små bogstaver)
- seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_latvia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_latvia_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_latvia_eu_drivers_license_number"></a>Keywords_latvia_eu_driver er s_license_number

- autovadītāja apliecība
- autovadītāja apliecības
- vadītāja apliecība

## <a name="latvia-passport-number"></a>Letlands pasnummer

### <a name="format"></a>Format

to bogstaver eller cifre efterfulgt af syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

to bogstaver eller cifre efterfulgt af syv cifre:

- to cifre eller bogstaver (skelner ikke mellem store og små bogstaver)
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_latvia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_latvia_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_latvia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_latvia_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_latvia_eu_passport_number"></a>Keywords_latvia_eu_passport_number

- pase numurs
- pase numur
- pases numuri
- pases nr
- passeport nej
- n° du Passeport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="latvia-personal-code"></a>Letlands personlige kode

### <a name="format"></a>Format

11 cifre og en valgfri bindestreg

### <a name="pattern"></a>Mønster

Gammelt format

11 cifre og en bindestreg:

- seks cifre, der svarer til fødselsdatoen (DDMMYY)
- en bindestreg
- et ciffer, der svarer til fødselstallet ("0" for det 19. århundrede, "1" for det 20. århundrede og "2" for det 21. århundrede)
- fire cifre, tilfældigt genereret

Nyt format

11 cifre

- To cifre "32"
- Ni cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_latvia_eu_national_id_card` eller regex `Regex_latvia_eu_national_id_card_new_format` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_latvia_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_latvia_eu_national_id_card` eller regex `Regex_latvia_eu_national_id_card_new_format` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- administrativt nummer
- alvas nē
- fødselsnummer
- borgernummer
- civilt nummer
- elektronisk census-nummer
- elektronisk nummer
- regnskabskode
- sundhedssektorens brugernummer
- Id #
- id-kode
- Identifikationsnummer
- identifikācijas numurs
- id-nummer
- individuelt tal
- latvija alva
- nacionālais-id
- nationalt id
- nationalt identifikationsnummer
- nationalt id-nummer
- det nationale forsikringsnummer
- nationalt registernummer
- nodokļa numurs
- nodokļu id
- nodokļu identifikācija numurs
- personligt certifikatnummer
- personlig kode
- personlig id-kode
- personligt id-nummer
- kode til personlig identifikation
- personligt id
- personligt id-nummer
- personligt nummer
- personlig numerisk kode
- personalcodeno #
- personas kods
- populationsidentifikationskode
- public service-nummer
- registreringsnummer
- omsætningsnummer
- cpr-nummer
- CPR-nummer
- statsskattekode
- skattefilnummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- vælgerens nummer

## <a name="latvia-physical-addresses"></a>Letlands fysiske adresser

Denne ubundtede navngivne enhed registrerer mønstre relateret til fysisk adresse fra Letland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="liechtenstein-physical-addresses"></a>Fysiske adresser i Liechtenstein

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Liechtenstein. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="lifestyles-that-relate-to-medical-conditions"></a>Livsstil, der er relateret til medicinske tilstande

Denne ubundtede navngivne enhed registrerer begreber relateret til livsstile, der kan resultere i en medicinsk tilstand, såsom *rygning*. Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="lithuania-drivers-license-number"></a>Litauens kørekortsnummer

### <a name="format"></a>Format

otte cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_lithuania_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_lithuania_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver er s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai

## <a name="lithuania-personal-code"></a>Personlig kode for Litauen

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

11 cifre uden mellemrum og afgrænsere:

- et ciffer (1-6), der svarer til personens køn og fødselsår
- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- tre cifre, der svarer til fødselsdatoens serienummer
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_lithuania_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_lithuania_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_lithuania_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_lithuania_eu_national_id_card"></a>Keywords_lithuania_eu_national_id_card

- asmeninis skaitmeninis kodas
- asmens kodas
- borger servicenummer
- mokesčių id
- mokesčių identifikavimas numeris
- mokesčių identifikavimo numeris
- mokesčių numeris
- nationalt identifikationsnummer
- personlig kode
- personlig numerisk kode
- piliečio paslaugos numeris
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- unikalus identifikavimo kodas
- unikalus identifikavimo numeris
- entydigt identifikationsnummer
- entydigt id-nummer
- uniqueidentityno #

## <a name="lithuania-physical-addresses"></a>Fysiske adresser for Litauen

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Litauen. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="lithuania-passport-number"></a>Litauens pasnummer

### <a name="format"></a>Format

otte cifre eller bogstaver uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

otte cifre eller bogstaver (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_lithuania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_lithuania_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date3` finder datoen i formatet DD MM ÅÅÅÅ, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_lithuania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_lithuania_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_lithuania_eu_passport_number"></a>Keywords_lithuania_eu_passport_number

- paso numeris
- paso numeriai
- paso nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="luxemburg-drivers-license-number"></a>Luxemburg-kørekortsnummer

### <a name="format"></a>Format

seks cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_luxemburg_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_luxemburg_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_luxemburg_eu_drivers_license_number"></a>Keywords_luxemburg_eu_driver er s_license_number

- fahrerlaubnis
- Führerschäin

## <a name="luxemburg-national-identification-number-natural-persons"></a>Det nationale identifikationsnummer for Luxembourg (fysiske personer)

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13 cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

13 cifre:

- 11 cifre
- to kontrolcifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_luxemburg_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_luxemburg_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_luxemburg_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_luxemburg_eu_national_id_card"></a>Keywords_luxemburg_eu_national_id_card

- eindeutige id
- eindeutige id-nummer
- eindeutigeid #
- id-personaleel
- idpersonnelle #
- idpersonnelle
- individuel kode
- individuelt id
- individuel identifikation
- individuel identitet
- numéro d'identification personale
- personligt id
- personligt id
- personlig identitet
- personalidno #
- personalidnumber #
- persönliche identifikationsnummer
- entydigt id
- entydig identitet
- uniqueidkey #

## <a name="luxemburg-national-identification-number-non-natural-persons"></a>Luxembourgs nationale identifikationsnummer (ikke-fysiske personer)

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

11 cifre

- to cifre
- et valgfrit mellemrum
- tre cifre
- et valgfrit mellemrum
- tre cifre
- et valgfrit mellemrum
- to cifre
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_luxemburg_eu_tax_file_number_non_natural` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_luxemburg_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_luxemburg_eu_tax_file_number_non_natural` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

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
- sozialversécherung
- sozialversicherungsausweis
- steier-id
- steier identifikatiounsnummer
- steier nummer
- steuer-id
- steueridentifikationsnummer
- steuernummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- Zinn #
- Zinn
- zinnzahl

## <a name="luxemburg-passport-number"></a>Luxemburg pasnummer

### <a name="format"></a>Format

otte cifre eller bogstaver uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

otte cifre eller bogstaver (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_luxemburg_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_luxemburg_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date3` finder datoen i formatet DD MM ÅÅÅÅ, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_luxemburg_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_luxemburg_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_luxemburg_eu_passport_number"></a>Keywords_luxemburg_eu_passport_number
- ausweisnummer
- luxembourg-gennemløb
- luxembourg passeport
- luxembourg pas
- ingen de-passeport
- no-reisepass
- nr-reisepass
- numéro de passeport
- pass net
- gennemløb nr.
- passnummer
- passeport nombre
- reisepässe
- reisepass-nr
- reisepassnummer

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="luxemburg-physical-addresses"></a>Fysiske adresser til Luxemburg

Denne ubundtede navngivne enhed registrerer mønstre relateret til fysisk adresse fra Luxemburg. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="malaysia-identification-card-number"></a>Malaysias id-kortnummer

### <a name="format"></a>Format

12 cifre, der indeholder valgfri bindestreger

### <a name="pattern"></a>Mønster

12 cifre:

- seks cifre i formatet YYMMDD, som er fødselsdatoen
- en streg (valgfrit)
- fødselskode på to bogstaver
- en streg (valgfrit)
- tre tilfældige cifre
- encifret kønskode

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_malaysia_id_card_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_malaysia_id_card_number.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_malaysia_id_card_number"></a>Keyword_malaysia_id_card_number

- digitalt programkort
- i/c
- i/c nej
- Ic
- ic no
- id-kort
- id-kort
- Identitetskort
- k/p
- k/p no
- kad akuan diri
- kad aplikasi digital
- kad pengenalan malaysia
- Kp
- kp no
- mykad
- mykas
- mykid
- mypr
- mytentera
- Malaysia-identitetskort
- malaysisk identitetskort
- nric
- personligt id-kort

## <a name="malta-drivers-license-number"></a>Maltas kørekortsnummer

### <a name="format"></a>Format

Kombination af to tegn og seks cifre i det angivne mønster

### <a name="pattern"></a>Mønster

kombination af to tegn og seks cifre:

- to tegn (cifre eller bogstaver, ikke forskel på store og små bogstaver)
- et mellemrum (valgfrit)
- tre cifre
- et mellemrum (valgfrit)
- tre cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_malta_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_malta_eu_drivers_license_number"></a>Keywords_malta_eu_driver er s_license_number

- liċenzja tas-sewqan
- liċenzji tas-sewwieq

## <a name="malta-identity-card-number"></a>Maltas identitetskortnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

syv cifre efterfulgt af et bogstav

### <a name="pattern"></a>Mønster

syv cifre efterfulgt af ét bogstav:

- syv cifre
- ét bogstav i "M, G, A, P, L, H, B, Z" (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_malta_eu_national_id_card` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_malta_eu_national_id_card"></a>Keywords_malta_eu_national_id_card

- borger servicenummer
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- personlig numerisk kode
- entydigt identifikationsnummer
- entydigt id-nummer
- uniqueidentityno #

## <a name="malta-passport-number"></a>Pasnummer til Malta

### <a name="format"></a>Format

syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_malta_eu_passport_number` findes.
- Der blev fundet et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_malta_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="malta-physical-addresses"></a>Fysiske adresser på Malta

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Malta. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="malta-tax-identification-number"></a>Maltas skatteidentifikationsnummer

### <a name="format"></a>Format

For maltesiske statsborgere:

- syv cifre og ét bogstav i det angivne mønster

Ikke maltesiske statsborgere og maltesiske enheder:

- ni cifre

### <a name="pattern"></a>Mønster

Maltesiske statsborgere: syv cifre og ét bogstav

- syv cifre
- ét bogstav (skelner ikke mellem store og små bogstaver)

Ikke maltesiske statsborgere og maltesiske enheder: ni cifre

- ni cifre

### <a name="checksum"></a>Checksum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Regex `Regex_malta_eu_tax_file_number`  eller `Regex_malta_eu_tax_file_number_non_maltese_national` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_malta_eu_tax_file_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Regex `Regex_malta_eu_tax_file_number` eller `Regex_malta_eu_tax_file_number_non_maltese_national` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_malta_eu_tax_file_number"></a>Keywords_malta_eu_tax_file_number

- borger servicenummer
- id tat-taxxa
- identifika numru tal-biljett
- kodiċi numerali personali
- numru ta 'identifikazzjoni personali
- numru ta 'identifikazzjoni tat-taxxa
- numru ta 'identifikazzjoni uniku
- numru ta' identità uniku
- numru tas-servizz taċ-ċittadin
- numru tat-taxxa
- personlig numerisk kode
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- entydigt identifikationsnummer
- entydigt id-nummer
- uniqueidentityno #

## <a name="medical-specialities"></a>Medicinske specialiteter

Denne ubundtede navngivne enhed registrerer begreber, der er relateret til medicinske specialiteter, f.eks *. dermatologi*.  Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="medicare-beneficiary-identifier-mbi-card"></a>MBI-kort (Modtageridentifikator) medicare

### <a name="format"></a>Format

Alfanumerisk mønster på 11 tegn

### <a name="pattern"></a>Mønster

- ét ciffer mellem 1 og 9
- ét bogstav eksklusive S, L, O, I, B, Z
- et ciffer eller bogstav undtagen S, L, O, I, B, Z
- ét ciffer
- en valgfri bindestreg
- ét bogstav eksklusive S, L, O, I, B, Z
- et ciffer eller bogstav undtagen S, L, O, I, B, Z
- ét ciffer
- en valgfri bindestreg
- to bogstaver eksklusive S, L, O, I, B, Z
- to cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_mbi_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_mbi_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_mbi_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_mbi_card"></a>Keyword_mbi_card

- Mbi
- Mbi #
- medicare-modtager #
- medicare-modtageridentifikator
- medicare-modtagernr.
- medicare modtagernummer
- medicare-modtager #

## <a name="mexico-unique-population-registry-code-curp"></a>Curp (Mexico Unique Population Registry Code)

### <a name="format"></a>Format

Alfanumerisk mønster på 18 tegn

### <a name="pattern"></a>Mønster

- fire bogstaver (skelner ikke mellem store og små bogstaver)
- seks cifre, der angiver en gyldig dato
- et bogstav - h/t eller M/m
- to bogstaver, der angiver en gyldig mexicansk statskode
- tre bogstaver
- et bogstav eller et ciffer
- ét ciffer

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_mexico_population_registry_code` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_mexico_population_registry_code` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_mexico_population_registry_code` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_mexico_population_registry_code"></a>Keyword_mexico_population_registry_code

- Clave Única de Registro de Población
- Clave Unica de Registro de Poblacion
- Entydig population-registreringsdatabasekode
- entydig populationskode
- CURP
- Personligt id
- Entydigt id
- personalid
- personalidnumber
- uniqueidkey
- uniqueidnumber
- clave única
- clave unica
- clave personlig Identidad
- personlig Identidad Clave
- ClaveÚnica
- claveunica
- clavepersonalIdentidad

## <a name="netherlands-citizens-service-bsn-number"></a>Nederlandsk borgerservicenummer (BSN)

### <a name="format"></a>Format

otte eller ni cifre, der indeholder valgfrie mellemrum

### <a name="pattern"></a>Mønster

otte-ni cifre:

- tre cifre
- et mellemrum (valgfrit)
- tre cifre
- et mellemrum (valgfrit)
- to-tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_netherlands_bsn finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_netherlands_bsn.
- Kontrolsummen passerer.

```xml
      <!-- Netherlands Citizen's Service (BSN) Number -->
      <Entity id="c5f54253-ef7e-44f6-a578-440ed67e946d" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_netherlands_bsn" />
          <Match idRef="Keywords_netherlands_eu_national_id_card" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_netherlands_eu_national_id_card"></a>Keywords_netherlands_eu_national_id_card

- Bsn #
- Bsn
- burgerservicenummer
- borger servicenummer
- personnummer
- personligt nummer
- personlig numerisk kode
- personrelateret nummer
- persoonlijk nummer
- persoonlijke numerieke code
- persoonsgebonden
- persoonsnummer
- sociaal-fiscaal nummer
- social-fiscal number
- Sofi
- sofinummer
- uniek identificatienummer
- uniek identiteitsnummer
- entydigt identifikationsnummer
- entydigt id-nummer
- uniqueidentityno #

## <a name="netherlands-drivers-license-number"></a>Nederlandsk kørekortsnummer

### <a name="format"></a>Format

10 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_netherlands_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_netherlands_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_netherlands_eu_drivers_license_number"></a>Keywords_netherlands_eu_driver er s_license_number

- permis de conduire
- rijbewijs
- rijbewijsnummer
- rijbewijzen
- rijbewijs nummer
- rijbewijsnummers

## <a name="netherlands-passport-number"></a>Nederlandsk pasnummer

### <a name="format"></a>Format

ni bogstaver eller cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

ni bogstaver eller cifre

### <a name="checksum"></a>Checksum

ikke tilgængelig

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_netherlands_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_netherlands_eu_passport_number` findes.
- Det regulære udtryk `Regex_netherlands_eu_passport_date` finder dato i formatet DD MMM/MMM ÅÅÅÅ (eksempel - 26 MAA/MAR 2012)

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_netherlands_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_netherlands_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_netherlands_eu_passport_number"></a>Keywords_netherlands_eu_passport_number

- paspoort nummer
- paspoortnummers
- paspoortnummer
- paspoort nr.

## <a name="netherlands-physical-addresses"></a>Fysiske adresser i Nederlandene

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Holland. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="netherlands-tax-identification-number"></a>Nederlandsk skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

ni cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_netherlands_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_netherlands_eu_tax_file_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_netherlands_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_netherlands_eu_tax_file_number"></a>Keywords_netherlands_eu_tax_file_number

- btw nummer
- hollânske skatteidentifikation
- hulandes impuesto id-nummer
- hulandes impuesto identifikation
- identificatienummer belasting
- identificatienummer van belasting
- impuesto identifikationsnummer
- impuesto tal
- nederlands belasting id nummer
- nederlands belasting identificatie
- nederlands belasting identificatienummer
- nederlands belastingnummer
- nederlandse belasting identificatie
- nederlandsk skatteidentifikation
- netherlands skatteidentifikation
- hollandsk tin
- netherlands tin
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- momsidentifikationsnummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- tax tal
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="netherlands-value-added-tax-number"></a>Nederlandsk momsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

Alfanumerisk mønster på 14 tegn

### <a name="pattern"></a>Mønster

Alfanumerisk mønster på 14 tegn:

- N eller n
- L eller l
- valgfri mellemrum, prik eller bindestreg
- ni cifre
- valgfri mellemrum, prik eller bindestreg
- B eller b
- to cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_netherlands_value_added_tax_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_netherlands_value_added_tax_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_netherlands_value_added_tax_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_netherlands_value_added_tax_number"></a>Keyword_netherlands_value_added_tax_number

- momsnummer
- momsnr.
- Moms #
- wearde tafoege skat getal
- btw nûmer
- btw-nummer

## <a name="new-zealand-bank-account-number"></a>New Zealands bankkontonummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

14-cifret til 16-cifret mønster med valgfri afgrænser

### <a name="pattern"></a>Mønster

14-cifret til 16-cifret mønster med valgfri afgrænser:

- to cifre
- en valgfri bindestreg eller et mellemrum
- tre til fire cifre
- en valgfri bindestreg eller et mellemrum
- syv cifre
- en valgfri bindestreg eller et mellemrum
- to til tre cifre
- en indstillingsstreg eller et mellemrum

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_new_zealand_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_new_zealand_bank_account_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_new_zealand_bank_account_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_new_zealand_bank_account_number"></a>Keyword_new_zealand_bank_account_number

- kontonummer
- Bankkonto
- bank_acct_id
- bank_acct_branch
- bank_acct_nbr

## <a name="new-zealand-drivers-license-number"></a>New Zealands kørekortsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

alfanumerisk mønster på otte tegn

### <a name="pattern"></a>Mønster

alfanumerisk mønster på otte tegn

- to bogstaver
- seks cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_newzealand_driver_license_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_newzealand_driver_license_number.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_newzealand_driver_license_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_new_zealand_drivers_license_number"></a>Keyword_new_zealand_drivers_license_number

- driverlicence
- driverlicences
- driver lic
- kørekort
- kørekort
- driverslic
- driverslicence
- driverslicences
- drivere lic
- drivere lics
- kørekort
- kørekort
- driver'lic
- driver'lics
- kørekort
- kørekort
- driver' lic
- driver'lics
- kørekort
- kørekort
- driverens slic
- driver'slics
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- kørekort
- driverlic #
- driverlics #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- kørekort #
- kørekort #
- driverslic #
- drivere #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- kørekort #
- international kørekort
- internationale kørekort
- nz bil forening
- new zealandsk bil forening

## <a name="new-zealand-inland-revenue-number"></a>Indtaegter for New Zealand

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

otte eller ni cifre med valgfri afgrænsere

### <a name="pattern"></a>Mønster

otte eller ni cifre med valgfri afgrænsere

- to eller tre cifre
- et valgfrit mellemrum eller en bindestreg
- tre cifre
- et valgfrit mellemrum eller en bindestreg
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_new_zealand_inland_revenue_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_new_zealand_inland_revenue_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_new_zealand_inland_revenue_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_new_zealand_inland_revenue_number"></a>Keyword_new_zealand_inland_revenue_number

- ird no.
- ird no #
- nz ird
- new zealandsk ird
- ird-nummer
- indlandsomsætningsnummer

## <a name="new-zealand-ministry-of-health-number"></a>New Zealands sundhedsministerium nummer

### <a name="format"></a>Format

tre bogstaver og fire cifre

### <a name="pattern"></a>Mønster

- tre bogstaver (skelner ikke mellem store og små bogstaver), undtagen 'I' og 'O'
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_new_zealand_ministry_of_health_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_nz_terms.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_new_zealand_ministry_of_health_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_nz_terms"></a>Keyword_nz_terms

- NHI
- New Zealand
- Nationalt sundhedsindeks
- NHI #
- Nationalt sundhedsindeks #

## <a name="new-zealand-physical-addresses"></a>Fysiske adresser for New Zealand

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra New Zealand. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="new-zealand-social-welfare-number"></a>Velfærdsnummer for New Zealand

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

ni cifre

### <a name="pattern"></a>Mønster

ni cifre

- tre cifre
- en valgfri bindestreg
- tre cifre
- en valgfri bindestreg
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_newzealand_social_welfare_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_newzealand_social_welfare_number.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_newzealand_social_welfare_number finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_new_zealand_social_welfare_number"></a>Keyword_new_zealand_social_welfare_number

- social sikring #
- social sikring #
- social sikring Nr.
- cpr-nummer
- swn #

## <a name="norway-identification-number"></a>Norges identifikationsnummer

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

11 cifre:

- seks cifre i formatet DDMMYY, som er fødselsdatoen
- trecifret individuelt tal
- to kontrolcifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_norway_id_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_norway_id_number.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_norway_id_numbe finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_norway_id_number"></a>Keyword_norway_id_number

- Personidentifikationsnummer
- Norsk id-nummer
- Id-nummer
- Identifikation
- Personnummer
- Fødselsnummer

## <a name="norway-physical-addresses"></a>Fysiske adresser i Norge

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Norge. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="philippines-unified-multi-purpose-identification-number"></a>Filippinerne unified multi-purpose identifikationsnummer

### <a name="format"></a>Format

12 cifre adskilt af bindestreger

### <a name="pattern"></a>Mønster

12 cifre:

- fire cifre
- en bindestreg
- syv cifre
- en bindestreg
- ét ciffer

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_philippines_unified_id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_philippines_id.

```xml
<!-- Philippines Unified Multi-Purpose ID number -->
<Entity id="019b39dd-8c25-4765-91a3-d9c6baf3c3b3" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_philippines_unified_id"/>
     <Match idRef="Keyword_philippines_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_philippines_id"></a>Keyword_philippines_id

- Samlet flerformåls-id
- UMID
- Identitetskort
- Pinag-isang Multi-Layunin ID

## <a name="poland-drivers-license-number"></a>Polens kørekortsnummer

### <a name="format"></a>Format

14 cifre, der indeholder to skråstreger

### <a name="pattern"></a>Mønster

14 cifre og to skråstreger:

- fem cifre
- en skråstreg
- to cifre
- en skråstreg
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_poland_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_poland_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_poland_eu_drivers_license_number"></a>Keywords_poland_eu_driver er s_license_number

- prawo jazdy
- prawa jazdy

## <a name="poland-identity-card"></a>Polens identitetskort

### <a name="format"></a>Format

tre bogstaver og seks cifre

### <a name="pattern"></a>Mønster

tre bogstaver (skelner ikke mellem store og små bogstaver) efterfulgt af seks cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_polish_national_id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_polish_national_id_passport_number.
- Kontrolsummen passerer.

```xml
<!-- Poland Identity Card-->
<Entity id="25E64989-ED5D-40CA-A939-6C14183BB7BF" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_polish_national_id" />
          <Match idRef="Keyword_polish_national_id_passport_number" />
      </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_poland_national_id_passport_number"></a>Keyword_poland_national_id_passport_number

- Dowód osobisty
- Numer dowodu osobistego
- Nazwa i numer dowodu osobistego
- Nazwa i nr dowodu osobistego
- Nazwa i nr dowodu tożsamości
- Dowód Tożsamości
- Dow. os.

## <a name="poland-national-id-pesel"></a>Nationalt id for Polen (PESEL)

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

- seks cifre, der repræsenterer fødselsdato i formatet YYMMDD
- fire cifre
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_pesel_identification_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_pesel_identification_number.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_pesel_identification_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_pesel_identification_number"></a>Keyword_pesel_identification_number

- dowód osobisty
- dowódosobisty
- niepowtarzalny numer
- niepowtarzalnynumer
- nr.-pesel
- nr-pesel
- numer identyfikacyjny
- pesel
- tożsamości narodowej

## <a name="poland-passport-number"></a>Polens pasnummer

Denne enhed af typen følsomme oplysninger er inkluderet i eu-passportnummer-typen med følsomme oplysninger. Den er også tilgængelig som et separat objekt af typen følsomme oplysninger.

### <a name="format"></a>Format

to bogstaver og syv cifre

### <a name="pattern"></a>Mønster

To bogstaver (skelner ikke mellem store og små bogstaver) efterfulgt af syv cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_polish_passport_number_v2` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_polish_national_passport_number` findes.
- Der blev fundet et nøgleord fra `Keywords_eu_passport_date` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_polish_passport_number_v2` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_polish_national_passport_number` findes.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_polish_passport_number_v2` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
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

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Polen. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="poland-regon-number"></a>Polens REGON-nummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

9-cifret eller 14-cifret tal

### <a name="pattern"></a>Mønster

nicifret eller 14-cifret tal:

- ni cifre eller
- ni cifre
- Bindestreg
- fem cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_polish_regon_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_polish_regon_number.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_polish_regon_number finder indhold, der svarer til mønsteret.

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
### <a name="keywords"></a>Søgeord

#### <a name="keywords_poland_regon_number"></a>Keywords_poland_regon_number

- regon-id
- statistisk nummer
- statistisk id
- statistisk nej
- regonnummer
- regonid #
- regonno #
- firma-id
- firma-id #
- companyidno #
- numer statystyczny
- numeru regon
- numerstatystyczny #
- numeruregon #

## <a name="poland-tax-identification-number"></a>Polens skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

11 cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

11 cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_poland_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_poland_eu_tax_file_number` .

```xml
      <!-- Poland Tax Identification Number -->
      <Entity id="1ff28b4d-40f2-49e9-b677-9606a88e2bca" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_poland_eu_tax_file_number" />
          <Match idRef="Keywords_poland_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_poland_eu_tax_file_number"></a>Keywords_poland_eu_tax_file_number

- Nip #
- Nip
- numer identyfikacji podatkowej
- numeridentyfikacjipodatkowej #
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- moms-id #
- moms-id
- momsnr.
- momsnummer
- vatid #
- vatid
- vatno #

## <a name="portugal-citizen-card-number"></a>Kortnummer for portugalsborger

### <a name="format"></a>Format

otte cifre

### <a name="pattern"></a>Mønster

otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_portugal_citizen_card finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_portugal_citizen_card.

```xml
<!-- Portugal Citizen Card Number -->
<Entity id="91a7ece2-add4-4986-9a15-c84544d81ecd" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_portugal_citizen_card"/>
     <Match idRef="Keyword_portugal_citizen_card"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_portugal_citizen_card"></a>Keyword_portugal_citizen_card

- bilhete de identidade
- cartão de cidadão
- borgerkort
- dokumentnummer
- documento de identificação
- id-nummer
- identifikationsnr.
- Identifikationsnummer
- id-kort nr.
- id-kortnummer
- nationalt id-kort
- Nic
- número bi de portugal
- número de identificação civil
- número de identificação fiscal
- número do documento
- portugal bi-nummer

## <a name="portugal-drivers-license-number"></a>Portugals kørekortsnummer

### <a name="format"></a>Format

to mønstre – to bogstaver efterfulgt af 5-8 cifre med specialtegn

### <a name="pattern"></a>Mønster

Mønster 1: To bogstaver efterfulgt af 5/6 med specialtegn:

- To bogstaver (skelner ikke mellem store og små bogstaver)
- En bindestreg
- Fem eller seks cifre
- Et mellemrum
- Et ciffer

Mønster 2: Ét bogstav efterfulgt af 6/8 cifre med specialtegn:

- Ét bogstav (skelner ikke mellem store og små bogstaver)
- En bindestreg
- Seks eller otte cifre
- Et mellemrum
- Et ciffer

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_portugal_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_portugal_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_portugal_eu_drivers_license_number"></a>Keywords_portugal_eu_driver er s_license_number

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

## <a name="portugal-passport-number"></a>Pasnummer for Portugal

### <a name="format"></a>Format

ét bogstav efterfulgt af seks cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

ét bogstav efterfulgt af seks cifre:

- ét bogstav (skelner ikke mellem store og små bogstaver)
- seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_portugal_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_portugal_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_portugal_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_portugal_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
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

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Portugal. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="portugal-tax-identification-number"></a>Portugals skatteidentifikationsnummer

### <a name="format"></a>Format

ni cifre med valgfri mellemrum

### <a name="pattern"></a>Mønster

- tre cifre
- et valgfrit mellemrum
- tre cifre
- et valgfrit mellemrum
- tre cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_portugal_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_portugal_eu_tax_file_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_portugal_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_portugal_eu_tax_file_number"></a>Keywords_portugal_eu_tax_file_number

- Cpf #
- Cpf
- Nif #
- Nif
- número de identificação fisca
- numero fiscal
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="romania-drivers-license-number"></a>Rumæniens kørekortsnummer

### <a name="format"></a>Format

ét tegn efterfulgt af otte cifre

### <a name="pattern"></a>Mønster

ét tegn efterfulgt af otte cifre:

- et bogstav (skelner ikke mellem store og små bogstaver) eller et ciffer
- otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_romania_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_romania_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_romania_eu_drivers_license_number"></a>Keywords_romania_eu_driver er s_license_number

- permis de conducere
- permisului de conducere
- permisului conducere
- permisele de conducere
- permisele conducere
- permis conducere

## <a name="romania-passport-number"></a>Pasnummer til Rumænien

### <a name="format"></a>Format

otte eller ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

otte eller ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_romania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_romania_eu_passport_number` findes.
- Det regulære udtryk `Regex_romania_eu_passport_date` finder dato i formatet DD MMM/MMM YYY (f.eks. 01 FEB/FEB 10), eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_romania_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_romania_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_romania_eu_passport_number"></a>Keywords_romania_eu_passport_number

numărul pașaportului numarul pasaportului numerele pașaportului Pașaport nr

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="romania-personal-numeric-code-cnp"></a>Rumæniens personlige numeriske kode (CNP)

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

- ét ciffer fra 1-9
- seks cifre, der repræsenterer fødselsdato (YYMMDD)
- to cifre, som kan være 01-52 eller 99
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_romania_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_romania_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_romania_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_romania_eu_national_id_card"></a>Keywords_romania_eu_national_id_card

- Cnp #
- Cnp
- cod identificare personal
- cod numerisk personlig
- cod unic identificare
- codnumericpersonal #
- codul fiscal nr.
- identificarea fiscală nr #
- id-ul taxei
- forsikringsnummer
- forsikringsnummer #
- nationalt id #
- nationalt id
- nationalt identifikationsnummer
- număr identificare personal
- număr identitate
- număr personlig unic
- număridentitate #
- număridentitate
- numărpersonalunic #
- numărpersonalunic
- număru de identificare fiscală
- numărul de identificare fiscală
- personlig numerisk kode
- Pin #
- Pin
- skattefil nr.
- skattefilnummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- entydigt identifikationsnummer
- entydigt id-nummer
- uniqueidentityno #
- uniqueidentityno

## <a name="romania-physical-addresses"></a>Fysiske adresser i Rumænien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Rumænien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="russia-passport-number-domestic"></a>Rusland pasnummer indenlandsk

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10-cifret tal

### <a name="pattern"></a>Mønster

10-cifret tal:

- to cifre
- et valgfrit mellemrum eller en bindestreg
- to cifre
- et valgfrit mellemrum
- seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Regex-Regex_Russian_Passport_Number_Domestic finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Russian_Passport_Number.

```xml
      <!-- Russian Passport Number Domestic -->
      <Entity id="76ec2f5d-cedb-48e1-8070-1998794af445" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_Domestic" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_russia_passport_number_domestic"></a>Keyword_russia_passport_number_domestic

- pasnummer
- pasnr.
- Passport #
- pas-id
- passportno #
- passportnumber #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="russia-passport-number-international"></a>Rusland pasnummer international

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

nicifret tal

### <a name="pattern"></a>Mønster

nicifret tal:

- to cifre
- et valgfrit mellemrum eller en bindestreg
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Regex-Regex_Russian_Passport_Number_International finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Russian_Passport_Number.

```xml
      <!-- Russian Passport Number International -->
      <Entity id="ac5f4878-75e4-4b82-af2d-02e13ea9f411" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Russian_Passport_Number_International" />
          <Match idRef="Keyword_Russian_Passport_Number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_russia_passport_number_international"></a>Keywords_russia_passport_number_international

- pasnummer
- pasnr.
- Passport #
- pas-id
- passportno #
- passportnumber #
- паспорт нет
- паспорт id
- pоссийской паспорт
- pусский номер паспорта
- паспорт #
- паспортid #
- номер паспорта
- номерпаспорта #

## <a name="saudi-arabia-national-id"></a>Saudi-Arabiens nationale id

### <a name="format"></a>Format

10 cifre

### <a name="pattern"></a>Mønster

10 cifre i træk

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_saudi_arabia_national_id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_saudi_arabia_national_id.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_saudi_arabia_national_id"></a>Keyword_saudi_arabia_national_id

- Id-kort
- I-kortnummer
- Id-nummer
- الوطنية الهوية بطاقة رقم

## <a name="singapore-national-registration-identity-card-nric-number"></a>Nric-nummer (national registration identity card) for Singapore

### <a name="format"></a>Format

ni bogstaver og cifre

### <a name="pattern"></a>Mønster

- ni bogstaver og cifre:

- bogstavet "F", "G", "M", "S" eller "T" (skelner ikke mellem store og små bogstaver)
- syv cifre
- et alfabetisk kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_singapore_nric finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_singapore_nric.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_singapore_nric finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_singapore_nric"></a>Keyword_singapore_nric

- Nationalt registrerings-id-kort
- Id-kortnummer
- NRIC
- IC
- Fremmed identifikationsnummer
- FIN
- 身份证
- 身份證

## <a name="slovakia-drivers-license-number"></a>Slovakiets kørekortsnummer

### <a name="format"></a>Format

ét tegn efterfulgt af syv cifre

### <a name="pattern"></a>Mønster

ét tegn efterfulgt af syv cifre

- et bogstav (skelner ikke mellem store og små bogstaver) eller et ciffer
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_slovakia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_slovakia_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_slovakia_eu_drivers_license_number"></a>Keywords_slovakia_eu_driver er s_license_number

- vodičský preukaz
- vodičské preukazy
- vodičského preukazu
- vodičských preukazov

## <a name="slovakia-passport-number"></a>Slovakiets pasnummer

### <a name="format"></a>Format

alfanumerisk mønster på otte eller ni tegn

### <a name="pattern"></a>Mønster

ét bogstav (skelner ikke mellem store og små bogstaver) efterfulgt af syv cifre eller to bogstaver (skelner ikke mellem store og små bogstaver) efterfulgt af seks eller syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_slovakia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_slovakia_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_slovakia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_slovakia_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
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

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

ni eller 10 cifre, der indeholder valgfri omvendt skråstreg

### <a name="pattern"></a>Mønster

- seks cifre, der repræsenterer fødselsdato
- valgfri skråstreg (/)
- tre cifre
- et valgfrit kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_slovakia_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_slovakia_eu_national_id_card` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_slovakia_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_slovakia_eu_national_id_card"></a>Keywords_slovakia_eu_national_id_card

- azonosító szám
- fødselsnummer
- číslo národnej identifikačnej karty
- číslo občianského preukazu
- daňové číslo
- id-nummer
- identifikationsnr.
- Identifikationsnummer
- identifikačná karta č
- identifikačné číslo
- id-kort nr.
- id-kortnummer
- národná identifikačná značka č
- nationalt nummer
- nationalt nummer #
- nemzeti személyazonosító igazolvány
- personalidnumber #
- rč
- rodne cislo
- rodné číslo
- CPR-nummer
- Ssn #
- Ssn
- személyi igazolvány szám
- személyi igazolvány száma
- személyigazolvány szám
- skattefil nr.
- skattefilnummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="slovakia-physical-addresses"></a>Fysiske adresser i Slovakiet

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Slovakiet. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="slovenia-drivers-license-number"></a>Sloveniens kørekortsnummer

### <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_slovenia_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_slovenia_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_slovenia_eu_drivers_license_number"></a>Keywords_slovenia_eu_driver s_license_number

- vozniško dovoljenje
- vozniška številka licence
- vozniških dovoljenj
- številka vozniškega dovoljenja
- številke vozniških dovoljenj

## <a name="slovenia-passport-number"></a>Pasnummer for Slovenien

### <a name="format"></a>Format

to bogstaver efterfulgt af syv cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

to bogstaver efterfulgt af syv cifre:

- bogstavet "P"
- et stort bogstav
- syv cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_slovenia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_slovenia_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_slovenia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_slovenia_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_slovenia_eu_passport_number"></a>Keywords_slovenia_eu_passport_number

- številka potnega lista
- potek veljavnosti
- potni-liste #
- datum rojstva
- potni-liste
- številke potnih listov

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="slovenia-physical-addresses"></a>Fysiske adresser i Slovenien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Slovenien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="slovenia-tax-identification-number"></a>Sloveniens skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

otte cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

- ét ciffer fra 1-9
- seks cifre
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_slovenia_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_slovenia_eu_tax_file_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_slovenia_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_slovenia_eu_tax_file_number"></a>Keywords_slovenia_eu_tax_file_number

- davčna številka
- identifikacijska številka davka
- številka davčne datoteke
- skattefil nr.
- skattefilnummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="slovenia-unique-master-citizen-number"></a>Sloveniens entydige masterborgernummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13 cifre uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

13 cifre i det angivne mønster:

- syv cifre, der svarer til fødselsdatoen (DDMMLLL), hvor "LLL" svarer til de sidste tre cifre i fødselsåret
- to cifre, der svarer til fødselsområdet "50"
- tre cifre, der svarer til en kombination af køn og serienummer for personer født samme dag. 000-499 for mænd og 500-999 for kvinder.
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_slovenia_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_slovenia_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_slovenia_eu_national_id_card` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_slovenia_eu_national_id_card"></a>Keywords_slovenia_eu_national_id_card

- edinstvena številka glavnega državljana
- emšo
- enotna maticna številka obcana
- id-kort
- Identifikationsnummer
- identifikacijska številka
- Identitetskort
- nacionalna id
- nacionalni potni liste
- nationalt id
- osebna izkaznica
- osebni koda
- osebni ne
- osebni številka
- personlig kode
- personligt nummer
- personlig numerisk kode
- številka državljana
- entydigt borgernummer
- entydigt id-nummer
- entydigt id-nummer
- entydigt masterborgernummer
- entydigt registreringsnummer
- uniqueidentityno #
- uniqueidentityno #

## <a name="south-africa-identification-number"></a>Sydafrikas identifikationsnummer

### <a name="format"></a>Format

13 cifre, der kan indeholde mellemrum

### <a name="pattern"></a>Mønster

13 cifre:

- seks cifre i formatet YYMMDD, som er fødselsdatoen
- fire cifre
- en encifret indikator for medborgerskab
- cifferet "8" eller "9"
- et ciffer, som er et kontrolsumtal

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_south_africa_identification_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_south_africa_identification_number.
- Kontrolsummen passerer.

```xml
<!-- South Africa Identification Number -->
<Entity id="e2adf7cb-8ea6-4048-a2ed-d89eb65f2780" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_africa_identification_number"/>
     <Match idRef="Keyword_south_africa_identification_number"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_south_africa_identification_number"></a>Keyword_south_africa_identification_number

- Identitetskort
- ID
- Identifikation

## <a name="south-korea-resident-registration-number"></a>Registreringsnummer for beboere i Sydkorea

### <a name="format"></a>Format

13 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

13 cifre:

- seks cifre i formatet YYMMDD, som er fødselsdatoen
- en bindestreg
- ét ciffer bestemt af århundredet og køn
- firecifret fødselskode for område
- et ciffer, der bruges til at differentiere personer, for hvem de foregående tal er identiske
- et kontrolciffer.

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_south_korea_resident_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_south_korea_resident_number.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_south_korea_resident_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- Nationalt id-kort
- Borgerregistreringsnummer
- Jumin deungnok beonho
- RRN
- 주민등록번호

## <a name="spain-dni"></a>Spanien DNI

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

otte cifre efterfulgt af et tegn

### <a name="pattern"></a>Mønster

syv cifre efterfulgt af ét tegn

- otte cifre
- Et valgfrit mellemrum eller en bindestreg
- ét kontrolbogstav (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_spain_eu_DL_and_NI_number_citizen` eller `Func_spain_eu_DL_and_NI_number_foreigner` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_spain_eu_national_id_card"` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_spain_eu_DL_and_NI_number_citizen` eller `Func_spain_eu_DL_and_NI_number_foreigner` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_spain_eu_national_id_card"></a>Keywords_spain_eu_national_id_card

- carné de identidad
- Dni #
- Dni
- dninúmero #
- documento nacional de identidad
- identidad único
- identidadúnico #
- forsikringsnummer
- nationalt identifikationsnummer
- national identitet
- nationalid #
- nationalidno #
- Nie #
- Nie
- nienúmero #
- número de identificación
- número nacional identidad
- personligt identifikationsnummer
- personlig identitet nr.
- entydigt id-nummer
- uniqueid #

## <a name="spain-drivers-license-number"></a>Spaniens kørekortsnummer

### <a name="format"></a>Format

otte cifre efterfulgt af et tegn

### <a name="pattern"></a>Mønster

otte cifre efterfulgt af ét tegn:

- otte cifre
- et ciffer eller bogstav (skelner ikke mellem store og små bogstaver)

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_spain_eu_DL_and_NI_number_citizen` eller `Func_spain_eu_DL_and_NI_number_foreigner` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_spain_eu_driver's_license_number` findes.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_spain_eu_DL_and_NI_number_citizen` eller `Func_spain_eu_DL_and_NI_number_foreigner` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_spain_eu_drivers_license_number"></a>Keywords_spain_eu_driver s_license_number

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

### <a name="format"></a>Format

en kombination af bogstaver og tal på otte eller ni tegn uden mellemrum eller afgrænsere

### <a name="pattern"></a>Mønster

en kombination af bogstaver og tal på otte eller ni tegn:

- to cifre eller bogstaver
- et ciffer eller bogstav (valgfrit)
- seks cifre

### <a name="checksum"></a>Checksum

Ikke relevant

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_spain_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_spain_eu_passport_number` findes.
- Det regulære udtryk `Regex_spain_eu_passport_date` finder datoen i formatet DD-MM-ÅÅÅÅ, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_spain_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_spain_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
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
- pasaporte nej.
- pasaporte n°
- spanien pas

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="spain-physical-addresses"></a>Fysiske adresser i Spanien

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Spanien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="spain-social-security-number-ssn"></a>Spanien cpr-nummer (SSN)

### <a name="format"></a>Format

11-12 cifre

### <a name="pattern"></a>Mønster

11-12 cifre:

- to cifre
- en skråstreg (valgfrit)
- syv til otte cifre
- en skråstreg (valgfrit)
- to cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_spanish_social_security_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.
- - Der blev fundet et nøgleord fra `Keywords_spain_eu_ssn_or_equivalent` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_spanish_social_security_number finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_spain_eu_passport_number"></a>Keywords_spain_eu_passport_number

- Ssn
- Ssn #
- social sikringno
- social sikring nr.
- CPR-nummer
- número de la seguridad social

## <a name="spain-tax-identification-number"></a>Skatteidentifikationsnummer for Spanien

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

syv eller otte cifre og et eller to bogstaver i det angivne mønster

### <a name="pattern"></a>Mønster

Spanske fysiske personer med nationalt id-kort i Spanien:

- otte cifre
- et stort bogstav (forskel på store og små bogstaver)

Ikke-bosiddende spaniere uden nationalt id-kort fra Spanien

- et stort bogstav "L" (forskel på store og små bogstaver)
- syv cifre
- et stort bogstav (forskel på store og små bogstaver)

Spaniere med bopæl under 14 år uden nationalt id-kort i Spanien:

- et stort bogstav "K" (forskel på store og små bogstaver)
- syv cifre
- et stort bogstav (forskel på store og små bogstaver)

Udlændinge med en udlændings identifikationsnummer

- et stort bogstav, der er "X", "Y" eller "Z" (forskel på store og små bogstaver)
- syv cifre
- et stort bogstav (forskel på store og små bogstaver)

Udlændinge uden udlændings identifikationsnummer

- et stort bogstav, der er "M" (forskel på store og små bogstaver)
- syv cifre
- et stort bogstav (forskel på store og små bogstaver)

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_spain_eu_tax_file_number` eller `Func_spain_eu_DL_and_NI_number_citizen` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_spain_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_spain_eu_tax_file_number` eller `Func_spain_eu_DL_and_NI_number_citizen` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_spain_eu_tax_file_number"></a>Keywords_spain_eu_tax_file_number

- Cif
- cifid #
- cifnúmero #
- número de contribuyente
- número de identificación fiscal
- número de impuesto corporativo
- spanishcifid #
- spanishcifid
- spanishcifno #
- spanishcifno
- skattefil nr.
- skattefilnummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="sql-server-connection-string"></a>SQL Server forbindelsesstreng

### <a name="format"></a>Format

Strengen "User Id", "User ID", "uid" eller "UserId" efterfulgt af de tegn og strenge, der er beskrevet i mønsteret nedenfor.

### <a name="pattern"></a>Mønster

- strengen "Bruger-id", "Bruger-id", "uid" eller "UserId"
- en kombination af mellem 1-200 små eller store bogstaver, cifre, symboler, specialtegn eller mellemrum
- strengen "Password" eller "pwd", hvor "pwd" ikke har et lille bogstav foranstillet
- et lighedstegn (=)
- alle tegn, der ikke er et dollartegn ($), procentsymbol (%), større end symbol (>), ved symbol (@), anførselstegn ("), semikolon (;), venstre klammeparentes([) eller venstre kantede parenteser ({)
- en kombination af 7-128 tegn, der ikke er et semikolon (;), skråstreg (/) eller anførselstegn (")
- et semikolon (;) eller anførselstegn (")

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk CEP_Regex_SQLServerConnectionString finder indhold, der svarer til mønsteret.
- Der blev ikke fundet et nøgleord fra CEP_GlobalFilter.
- Det regulære udtryk CEP_PasswordPlaceHolder kan ikke finde indhold, der svarer til mønsteret.
- Det regulære udtryk CEP_CommonExampleKeywords kan ikke finde indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- some-password
- somepassword
- secretPassword
- Prøve

#### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste.

- Adgangskode eller pwd efterfulgt af 0-2 mellemrum, et lighedstegn (=), 0-2 mellemrum og en stjerne (*) -OR-
- Adgangskode eller pwd efterfulgt af:
    - Lighedstegn (=)
    - Mindre end symbol (<)
    - Enhver kombination af 1-200 tegn, der er store eller små bogstaver, cifre, en stjerne (*), bindestreg (-), understregning (_) eller mellemrumstegn
    - Større end symbol (>)

#### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

Denne type følsomme oplysninger identificerer disse nøgleord ved hjælp af et regulært udtryk og ikke en nøgleordsliste.

- Contoso
- Fabrikam
- Northwind
- Sandkasse
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Nettet

## <a name="surgical-procedures"></a>Kirurgiske procedurer

Denne ubundtede navngivne enhed registrerer begreber, der er relateret til kirurgiske procedurer, f.eks *. appendectomy*.  Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="sweden-drivers-license-number"></a>Sveriges kørekortsnummer

### <a name="format"></a>Format

10 cifre, der indeholder en bindestreg

### <a name="pattern"></a>Mønster

10 cifre, der indeholder en bindestreg:

- seks cifre
- en bindestreg
- fire cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_sweden_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_sweden_eu_driver's_license_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

#### <a name="keywords_sweden_eu_drivers_license_number"></a>Keywords_sweden_eu_driver er s_license_number

- ajokortti
- permis de conducere
- ajokortin numero
- kuljettajat lic.
- drivere lic.
- körkort
- numărul permisului de conducere
- שאָפער דערלויבעניש נומער
- förare lic.
- דריווערס דערלויבעניש
- körkortsnummer

## <a name="sweden-national-id"></a>Nationalt id for Sverige

### <a name="format"></a>Format

10 eller 12 cifre og en valgfri afgrænser

### <a name="pattern"></a>Mønster

10 eller 12 cifre og en valgfri afgrænser:

- to cifre (valgfrit)
- Seks cifre i datoformat YYYMMDD
- afgrænser for "-" eller "+" (valgfrit)
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_swedish_national_identifier` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_swedish_national_identifier`
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_swedish_national_identifier` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_swedish_national_identifier"></a>Keywords_swedish_national_identifier

- id nej
- id-nummer
- Id #
- identifikationsnr.
- Identifikationsnummer
- identifikationsnumret #
- identifikationsnumret
- identitetshandling
- identitetsdokument
- identitet nr.
- id-nummer
- id-nummer
- personligt id
- personnummer #
- personnummer
- skatteidentifikationsnummer

## <a name="sweden-passport-number"></a>Sveriges pasnummer

### <a name="format"></a>Format

otte cifre

### <a name="pattern"></a>Mønster

otte cifre i træk

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- det regulære udtryk Regex_sweden_passport_number finder indhold, der svarer til mønsteret.
- et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_sweden_passport` findes.
- det regulære udtryk `Regex_sweden_eu_passport_date` finder en dato i formatet DD MMM/MMM YYY (01 JAN/JAN 12), eller der findes et nøgleord fra `Keywords_eu_passport_date` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- det regulære udtryk Regex_sweden_passport_number finder indhold, der svarer til mønsteret.
- et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_sweden_passport` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- registreringskort for fremmed person
- g3 behandlingsgebyrer
- flere indgange
- Numéro de passeport
- passeport n °
- passeport ikke
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- gennemløb nr.
- schengenvisum
- schengenvisum
- enkelt post
- sverigepas
- Visumkrav
- behandling af visum
- visumtype

#### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato

## <a name="sweden-physical-addresses"></a>Fysiske adresser i Sverige

Denne ubundtede navngivne enhed registrerer mønstre relateret til fysisk adresse fra Sverige. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="sweden-tax-identification-number"></a>Sveriges skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 cifre og et symbol i det angivne mønster

### <a name="pattern"></a>Mønster

10 cifre og et symbol:

- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- et plustegn eller minustegn
- tre cifre, der gør identifikationsnummeret entydigt, hvor:
  - for numre, der er udstedt før 1990, identificerer det syvende og ottende ciffer fødsels amtet eller udenlandske fødte
  - tallet i niende position angiver køn med enten ulige for mand eller endda for kvinde
- et kontrolciffer

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_sweden_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_sweden_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_sweden_eu_tax_file_number` finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

- personligt id-nummer
- personnummer
- skatt id nummer
- skatt identifikation
- skattebetalarens identifikationsnummer
- sverige tin
- skattefil
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="swift-code"></a>SWIFT-kode

### <a name="format"></a>Format

fire bogstaver efterfulgt af 5-31 bogstaver eller cifre

### <a name="pattern"></a>Mønster

fire bogstaver efterfulgt af 5-31 bogstaver eller cifre:

- bankkode på fire bogstaver (skelner ikke mellem store og små bogstaver)
- et valgfrit mellemrum
- 4-28 bogstaver eller cifre (det grundlæggende bankkontonummer (BBAN))
- et valgfrit mellemrum
- et til tre bogstaver eller cifre (resten af BBAN)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_swift finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_swift.

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_swift"></a>Keyword_swift

- den internationale standardiseringsorganisation 9362
- iso 9362
- iso9362
- Swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- swift-kode
- swift tal #
- hurtigt routingnummer
- bic-tal
- bic-kode
- Bic #
- Bic #
- bank-id-kode
- Organisation international de normalisering 9362
- Rapide #
- code SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- \# BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード

## <a name="switzerland-physical-addresses"></a>Fysiske adresser i Schweiz

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Schweiz. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="switzerland-ssn-ahv-number"></a>Schweiz SSN AHV-nummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

13-cifret tal

### <a name="pattern"></a>Mønster

13-cifret tal:

- tre cifre - 756
- en valgfri prik
- fire cifre
- en valgfri prik
- fire cifre
- en valgfri prik
- to cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_swiss_social_security_number_ahv finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_swiss_social_security_number_ahv.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_swiss_social_security_number_ahv finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_swiss_ssn_ahv_number"></a>Keyword_swiss_ssn_AHV_number

- Ahv
- Ssn
- Pid
- forsikringsnummer
- personalidno #
- CPR-nummer
- personligt id-nummer
- personidentifikationsnummer.
- insuranceno #
- uniqueidno #
- entydigt identifikationsnr.
- avs-nummer
- personlig identitet no versicherungsnummer
- identifikationsnummer
- einzigartige identität nicht
- sozialversicherungsnummer
- identifikationspersonale-id
- numéro de sécurité sociale

## <a name="taiwan-national-identification-number"></a>Taiwans nationale identifikationsnummer

### <a name="format"></a>Format

ét bogstav (på engelsk) efterfulgt af ni cifre

### <a name="pattern"></a>Mønster

ét bogstav (på engelsk) efterfulgt af ni cifre:

- ét bogstav (på engelsk, ikke forskel på store og små bogstaver)
- cifferet "1" eller "2"
- otte cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_taiwanese_national_id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_taiwanese_national_id.
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_taiwanese_national_id finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

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

## <a name="taiwan-passport-number"></a>Pasnummer til Taiwan

### <a name="format"></a>Format

- biometrisk pasnummer: ni cifre
- ikke-biometrisk pasnummer: ni cifre

### <a name="pattern"></a>Mønster
biometrisk pasnummer:

- tegnet "3"
- otte cifre

ikke-biometrisk pasnummer:

- ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_taiwan_passport finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_taiwan_passport.

```xml
<!-- Taiwan Passport Number -->
<Entity id="e7251cb4-4c2c-41df-963e-924eb3dae04a" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_passport"/>
     <Match idRef="Keyword_taiwan_passport"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_taiwan_passport"></a>Keyword_taiwan_passport

- ROC-pasnummer
- Passport-nummer
- Passport-nr.
- Passport Num
- Passport #
- 护照
- 中華民國護照
- Zhzhnghuá Mínguó hùzhào

## <a name="taiwan-resident-certificate-arctarc-number"></a>Taiwan-resident certificate (ARC/TARC) nummer

### <a name="format"></a>Format

10 bogstaver og cifre

### <a name="pattern"></a>Mønster

10 bogstaver og cifre:

- to bogstaver (skelner ikke mellem store og små bogstaver)
- otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_taiwan_resident_certificate finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_taiwan_resident_certificate.

```xml
<!-- Taiwan Resident Certificate (ARC/TARC) -->
<Entity id="48269fec-05ea-46ea-b326-f5623a58c6e9" recommendedConfidence="75" patternsProximity="300">
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Regex_taiwan_resident_certificate"/>
     <Match idRef="Keyword_taiwan_resident_certificate"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_taiwan_resident_certificate"></a>Keyword_taiwan_resident_certificate

- Resident Certificate
- Resident Cert
- Resident Cert.
- Id-kort
- Certifikat for udlændingsboer
- ARC
- Certifikat for fastboende i Taiwan
- TARC
- 居留證
- 外僑居留證
- 台灣地區居留證

## <a name="thai-population-identification-code"></a>Thai population-id-kode

### <a name="format"></a>Format

13 cifre

### <a name="pattern"></a>Mønster

13 cifre:

- det første ciffer ikke er nul eller ni
- 12 cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Thai_Citizen_Id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Thai_Citizen_Id.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_Thai_Citizen_Id finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- Id-nummer
- Identifikationsnummer
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน

## <a name="turkey-national-identification-number"></a>Tyrkiets nationale identifikationsnummer

### <a name="format"></a>Format

11 cifre

### <a name="pattern"></a>Mønster

11 cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Turkish_National_Id finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Turkish_National_Id.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_Turkish_National_Id finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_turkish_national_id"></a>Keyword_turkish_national_id

- TC Kimlik No
- TC Kimlik numarası
- Vatandaşlık numarası
- Vatandaşlık nej

## <a name="turkey-physical-addresses"></a>Fysiske adresser for Tyrkiet

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Tyrkiet. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="types-of-medication"></a>Typer af medicin

Denne ubundtede navngivne enhed registrerer medicinnavne, f.eks. *insulin*.  Det understøtter kun engelske ord. Det er også inkluderet i [alle medicinske vilkår og betingelser](#all-medical-terms-and-conditions) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Høj

## <a name="uk-drivers-license-number"></a>STORBRITANNIEN. kørekortsnummer

### <a name="format"></a>Format

Kombination af 18 bogstaver og cifre i det angivne format

### <a name="pattern"></a>Mønster

18 bogstaver og cifre:

- Fem bogstaver (skelner ikke mellem store og små bogstaver) eller cifferet "9" i stedet for et bogstav.
- Et ciffer.
- Fem cifre i datoformatet MMDDY for fødselsdato. Det syvende tegn forøges med 50, hvis faktoren er kvindelig. f.eks. 51 til 62 i stedet for 01 til 12.
- To bogstaver (skelner ikke mellem store og små bogstaver) eller cifferet "9" i stedet for et bogstav.
- Fem cifre.

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_uk_drivers_license` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_eu_driver's_license_number` .
- Kontrolsummen passerer.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_uk_drivers_license` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

## <a name="uk-electoral-roll-number"></a>STORBRITANNIEN. valglister

### <a name="format"></a>Format

to bogstaver efterfulgt af 1-4 cifre

### <a name="pattern"></a>Mønster

to bogstaver (skelner ikke mellem store og små bogstaver) efterfulgt af 1-4 tal

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_uk_electoral finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_uk_electoral.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- nominering af råd
- nomineringsformular
- valgregister
- valglister

## <a name="uk-national-health-service-number"></a>STORBRITANNIEN. nummer på det nationale sundhedsvæsen

### <a name="format"></a>Format

10-17 cifre adskilt af mellemrum

### <a name="pattern"></a>Mønster

10-17 cifre:

- enten 3 eller 10 cifre
- et mellemrum
- tre cifre
- et mellemrum
- fire cifre

### <a name="checksum"></a>Checksum

Ja

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_uk_nhs_number finder indhold, der svarer til mønsteret.
- Et af følgende er sandt:
    - Der blev fundet et nøgleord fra Keyword_uk_nhs_number.
    - Der blev fundet et nøgleord fra Keyword_uk_nhs_number1.
    - Der blev fundet et nøgleord fra Keyword_uk_nhs_number_dob.
- Kontrolsummen passerer.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- nationale sundhedstjenester
- Nhs
- sundhedstjenestemyndighed
- sundhedsmyndighed

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

## <a name="uk-national-insurance-number-nino"></a>STORBRITANNIEN. det nationale forsikringsnummer (NINO)

Denne enhed af typen af følsomme oplysninger er omfattet af eu's nationale identifikationsnummer med følsomme oplysninger. Den er også tilgængelig som et separat objekt af typen følsomme oplysninger.

### <a name="format"></a>Format

syv tegn eller ni tegn adskilt af mellemrum eller tankestreger

### <a name="pattern"></a>Mønster

to mulige mønstre:

- to bogstaver (gyldige NINO'er bruger kun visse tegn i dette præfiks, som dette mønster validerer, ikke forskel på store og små bogstaver)
- seks cifre
- enten 'A', 'B', 'C' eller 'D' (ligesom præfikset er det kun visse tegn, der er tilladt i suffikset, og der skelnes ikke mellem store og små bogstaver)

ELLER

- to bogstaver
- et mellemrum eller en streg
- to cifre
- et mellemrum eller en streg
- to cifre
- et mellemrum eller en streg
- to cifre
- et mellemrum eller en streg
- enten 'A', 'B', 'C' eller 'D'

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_uk_nino finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_uk_nino.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_uk_nino finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_uk_nino"></a>Keyword_uk_nino

- det nationale forsikringsnummer
- bidrag til de nationale forsikringsselskaber
- beskyttelseshandling
- Forsikring
- CPR-nummer
- forsikringsprogram
- medicinsk anvendelse
- social sikring
- Lægehjælp
- social sikring
- Storbritannien
- NI-nummer
- NI-nr.
- NI #
- NI #
- Forsikring #
- forsikringsnummer
- national forsikring #
- det nationale forsikringsnummer

## <a name="uk-physical-addresses"></a>STORBRITANNIEN. fysiske adresser

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra Storbritannien. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="uk-unique-taxpayer-reference-number"></a>STORBRITANNIEN. Entydigt referencenummer for skatteborger

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

10 cifre uden mellemrum og afgrænsere

### <a name="pattern"></a>Mønster

10 cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_uk_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_uk_eu_tax_file_number` .

```xml
      <!-- U.K. Unique Taxpayer Reference Number -->
      <Entity id="ad4a8116-0db8-439a-b545-6d967642f0ec" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_uk_eu_tax_file_number" />
          <Match idRef="Keywords_uk_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keywords_uk_eu_tax_file_number"></a>Keywords_uk_eu_tax_file_number

- momsnummer
- skattefil
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsregistreringsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #

## <a name="us-bank-account-number"></a>Amerikansk bankkontonummer

### <a name="format"></a>Format

6-17 cifre

### <a name="pattern"></a>Mønster

6-17 cifre i træk

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_usa_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_usa_Bank_Account.

```xml
<!-- U.S. Bank Account Number -->
<Entity id="a2ce32a8-f935-4bb6-8e96-2a5157672e2c" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_usa_bank_account_number" />
        <Match idRef="Keyword_usa_Bank_Account" />
    </Pattern>
</Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_usa_bank_account"></a>Keyword_usa_Bank_Account

- Kontrol af kontonummer
- Kontrol af konto
- Kontrol af konto #
- Kontrollerer tilgængelighedsnummer
- Kontrollerer tilgængelighed #
- Kontrollerer tilgængelighedsnr.
- Kontrollerer kontonr.
- Bankkontonummer
- Bankkonto #
- Kontonummer for bank
- Bankkonto #
- Kontonr.
- Bankkontonr.
- Opsparingskontonummer
- Opsparingskonto.
- Opsparingskonto #
- Opsparingsacctnummer
- Opsparingsacct #
- Opsparingskontonr.
- Opsparingskontonr.
- Debetkontonummer
- Debetkonto
- Debetkonto #
- Debiteringskontonummer
- Debetkonto #
- Debetkontonr.
- Debetkontonr.

## <a name="us-drivers-license-number"></a>Amerikansk kørekortsnummer

### <a name="format"></a>Format

Afhænger af staten

### <a name="pattern"></a>Mønster

afhænger af staten – f.eks. New York:

- ni cifre formateret som ddd ddd ddd vil matche.
- ni cifre som ddddddddd matcher ikke.

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_new_york_drivers_license_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_[state_name]_drivers_license_name.
- Der blev fundet et nøgleord fra Keyword_us_drivers_license.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_new_york_drivers_license_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_[state_name]_drivers_license_name.
- Der blev fundet et nøgleord fra Keyword_us_drivers_license_abbreviations.
- Der blev ikke fundet et nøgleord fra Keyword_us_drivers_license.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_us_drivers_license_abbreviations"></a>Keyword_us_drivers_license_abbreviations

- DL
- DLS
- CDL
- CDLS
- ID
- Id'er
- DL #
- DLS #
- CDL #
- CDLS #
- ID #
- Id'er #
- Id-nummer
- Id-numre
- LIC
- LIC #
- DLN

#### <a name="keyword_us_drivers_license"></a>Keyword_us_drivers_license

- DriverLic
- DriverLics
- DriverLicense
- DriverLicenses
- Driver-Lic
- Driver-LIC'er
- Driverlicens
- Driverlicenser
- Drivere
- DriversLics
- DriversLicense
- DriversLicenses
- Lic-faktorer
- Lic-drivere
- Licens til drivere
- Kørekort til drivere
- Driver'Lic
- Driver'Lics
- Driverlicens
- Driverlicenser
- Driver' Lic
- Driver' Lics
- Driverlicens
- Driverlicenser
- Driver'sLic
- Driver'sLics
- Driver'sLicense
- Driver'sLicenses
- Driverens Lic
- Driver's Lics
- Kørekort
- Driverlicenser
- Identifikationsnummer
- Identifikationsnumre
- Identifikation #
- id-kort
- id-kort
- identifikationskort
- id-kort
- DriverLic #
- DriverLics #
- DriverLicense #
- DriverLicenses #
- Driver-Lic #
- Driver-LIC'er #
- Driverlicens #
- Driverlicenser #
- Drivere #
- DriversLics #
- DriversLicense #
- DriversLicenses #
- Lic-faktorer #
- Lic-drivere #
- Licens til drivere #
- Kørekort til drivere #
- Driver'Lic #
- Driver'Lics #
- Driverlicens #
- Driverlicenser #
- Driver' Lic #
- Driver' Lics #
- Driverlicens #
- Driverlicenser #
- Driver'sLic #
- Driver'sLics #
- Driver'sLicense #
- Driver'sLicenses #
- Driverens Lic #
- Driver's Lics #
- Kørekort #
- Driverlicenser #
- id-kort #
- id-kort #
- identifikationskort #
- id-kort #

#### <a name="keyword_state_name_drivers_license_name"></a>Keyword_[state_name]_drivers_license_name

- forkortelse for stater (f.eks. "NY")
- state name (f.eks. "New York")

## <a name="us-individual-taxpayer-identification-number-itin"></a>Id-nummer for individuelle skatteborgere i USA (ITIN)

### <a name="format"></a>Format

ni cifre, der starter med et "9" og indeholder et "7" eller "8" som det fjerde ciffer, eventuelt formateret med mellemrum eller tankestreger

### <a name="pattern"></a>Mønster

Formateret:

- cifferet "9"
- to cifre
- et mellemrum eller en streg
- en "7" eller "8"
- et ciffer
- et mellemrum eller en streg
- fire cifre

Uformateret:

- cifferet "9"
- to cifre
- en "7" eller "8"
- fem cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_formatted_itin finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_itin.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_unformatted_itin finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_itin.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_formatted_itin eller Func_unformatted_itin finder indhold, der svarer til mønsteret.

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_itin"></a>Keyword_itin

- Skatteyderne
- moms-id
- momsidentifikation
- itin
- i.t.i.n.
- Ssn
- Tin
- social sikring
- betaler af moms
- itins
- taxid
- individuel skatteborger

## <a name="us-physical-addresses"></a>Amerikanske fysiske adresser

Denne ubundtede navngivne enhed registrerer mønstre, der er relateret til fysisk adresse fra USA. Den er også inkluderet i [alle fysiske adresser](#all-physical-addresses) , der er bundtet med navnet entity SIT.

### <a name="confidence-level"></a>Konfidensniveau

Medium

## <a name="us-social-security-number-ssn"></a>AMERIKANSK CPR-nummer (SSN)

### <a name="format"></a>Format

ni cifre, som kan være i et formateret eller uformateret mønster

> [!NOTE]
> Hvis den udstedes før midten af 2011, har et SSN stærk formatering, hvor visse dele af tallet skal falde inden for visse områder for at være gyldige (men der er ingen kontrolsum).

### <a name="pattern"></a>Mønster

fire funktioner søger efter SSN'er i fire forskellige mønstre:

- Func_ssn finder SSN'er med stærk formatering fra før 2011, der er formateret med tankestreger eller mellemrum (ddd-dd-dddd ELLER ddd dd dddd)
- Func_unformatted_ssn finder SSN'er med stærk formatering fra før 2011, der ikke er formateret som ni cifre efter hinanden (ddddddddd)
- Func_randomized_formatted_ssn finder SSN'er efter 2011, der er formateret med tankestreger eller mellemrum (ddd-dd-dddd ELLER ddd dd dddd)
- Func_randomized_unformatted_ssn finder SSN'er efter 2011, der ikke er formateret som ni cifre efter hinanden (ddddddddd)

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_ssn` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_ssn` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_unformatted_ssn' finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_ssn` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_randomized_formatted_ssn` eller `Func_randomized_unformatted_ssn` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_ssn` .

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

### <a name="keywords"></a>Søgeord

#### <a name="keyword_ssn"></a>Keyword_ssn

- SSA-nummer
- CPR-nummer
- social sikring #
- social sikring #
- social sikring nr.
- Social sikring #
- Soc sek.
- SSN
- SSNS
- SSN #
- SS #
- SSID

## <a name="usuk-passport-number"></a>Storbritannien pasnummer

### <a name="format"></a>Format

ni cifre

### <a name="pattern"></a>Mønster

- et bogstav eller et ciffer
- otte cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_usa_uk_passport finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_uk_eu_passport_number` findes.
- Der blev fundet et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_usa_uk_passport finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_uk_eu_passport_number` findes.

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

### <a name="keywords"></a>Søgeord

#### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

#### <a name="keywords_uk_eu_passport_number"></a>Keywords_uk_eu_passport_number

- britisk pas
- britisk pas

## <a name="ukraine-passport-domestic"></a>Ukraine pas indland

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

ni cifre

### <a name="pattern"></a>Mønster

ni cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Regex-Regex_Ukraine_Passport_Domestic finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Ukraine_Passport_Domestic.

```xml
      <!-- Ukraine Passport Domestic -->
      <Entity id="1817a540-221f-4459-9202-3bd78b81d803" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_Ukraine_Passport_Domestic"/>
          <Match idRef="Keyword_Ukraine_Passport_Domestic"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_ukraine_passport_domestic"></a>Keyword_ukraine_passport_domestic

- ukraine pas
- pasnummer
- pasnr.
- паспорт України
- номер паспорта
- персональний

## <a name="ukraine-passport-international"></a>Ukraine passport international

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

### <a name="format"></a>Format

alfanumerisk mønster med otte tegn

### <a name="pattern"></a>Mønster

alfanumerisk mønster med otte tegn:

- to bogstaver eller cifre
- seks cifre

### <a name="checksum"></a>Checksum

Nej

### <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Regex-Regex_Ukraine_Passport_International finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Ukraine_Passport_International.

```xml
      <!-- Ukraine Passport International -->
      <Entity id="cfbe032d-22e0-4f28-ab68-d66e9641f1e2" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_Ukraine_Passport_International"/>
          <Match idRef="Keyword_Ukraine_Passport_International"/>
        </Pattern>
      </Entity>
```

### <a name="keywords"></a>Søgeord

#### <a name="keyword_ukraine_passport_international"></a>Keyword_ukraine_passport_international

- ukraine pas
- pasnummer
- pasnr.
- паспорт України
- номер паспорта
