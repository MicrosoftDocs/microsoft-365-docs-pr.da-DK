---
title: Funktioner for type af følsomme oplysninger
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: low
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Få mere at vide om, hvad funktionerne til følsomme oplysninger kan se ud for.
ms.openlocfilehash: 7c2ce289cab93e4a0491cbf13379c169a01e7fbf
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760245"
---
# <a name="sensitive-information-type-functions"></a>Funktioner for type af følsomme oplysninger

FØLSOMME oplysningstyper (SIT) kan bruge funktioner som primære elementer til at identificere følsomme elementer. Typen af følsomme oplysninger for kreditkortnummer bruger f.eks. funktionen Func_credit_card til at registrere kreditkortnummer.

I denne artikel forklares det, hvad disse funktioner ser ud for, for at hjælpe dig med at forstå, hvordan de foruddefinerede typer følsomme oplysninger fungerer. Du kan få flere oplysninger under [Objektdefinitioner for følsomme oplysninger](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>Tabel over funktioner

|Funktionsnavn | Funktionshandling | Er validator|
|---------|----------|---------|
|Func_aba_routing|registrerer ABA-routingnummeret|Ja|
|Func_alabama_drivers_license_number|registrerer Alabama-driverens licensnummer|Nej|
|Func_alaska_delaware_oregon_drivers_license_number|registrerer Alaska, Delaware, Oregon kørekort nummer|Nej|
|Func_alaska_drivers_license_number|registrerer Alaska-chaufførens licensnummer|Nej|
|Func_alberta_drivers_license_number|registrerer Alberta-driverens licensnummer|Nej|
|Func_argentina_Unique_Tax_Key|registrerer og validerer Argentinas entydige skattenøgle|Nej|
|Func_Argentina_Unique_Tax_Key|registrerer Argentinas entydige skattenøgle|Nej|
|Func_arizona_drivers_license_number|registrerer Arizona-driverens licensnummer|Nej|
|Func_arkansas_drivers_license_number|registrerer Arkansas-driverens licensnummer|Nej|
|Func_australian_business_number|registrerer australiens forretningsnummer|Nej|
|Func_Australian_Company_Number|registrerer australiens firmanummer|Nej|
|Func_australian_medical_account_number|registrerer australiens medicinske kontonummer|Nej|
|Func_australian_tax_file_number|registrerer det australske skattefilnummer|Ja|
|Func_austria_eu_ssn_or_equivalent|registrerer det østrigske cpr-nummer|Nej|
|Func_austria_eu_tax_file_number|registrerer momsfilnummeret for Østrig|Nej|
|Func_Austria_Value_Added_Tax|registrerer Østrigs moms|Nej|
|Func_belgium_national_number|registrerer belgiens nationale nummer|Nej|
|Func_belgium_value_added_tax_number|registrerer det belgiske momsnummer|Nej|
|Func_brazil_cnpj|registrerer juridisk enhedsnummer for Brasilien (CNPJ)|Ja|
|Func_brazil_cpf|registrerer Brasilien CPF|Ja|
|Func_brazil_rg|registrerer Brasiliens RG|Nej|
|Func_british_columbia_drivers_license_number|registrerer British Columbia-driverens licensnummer|Nej|
|Func_bulgaria_eu_national_id_card|registrerer Bulgariens ensartede civilnummer|Nej|
|Func_california_drivers_license_number|registrerer californiens kørekortsnummer|Nej|
|Func_canadian_sin|registrerer Canadas synd|Ja|
|Func_chile_id_card|registrerer Chile-id-kort|Nej|
|Func_china_resident_id|registrerer kina-id|Nej|
|Func_colorado_drivers_license_number|registrerer Colorado-driverens licensnummer|Nej|
|Func_connecticut_drivers_license_number|registrerer Connecticut-driverens licensnummer|Nej|
|Func_credit_card|registrerer kreditkort|Ja|
|Func_croatia_id_card|registrerer Kroatiens id-kort|Nej|
|Func_croatia_oib_number|registrerer Kroatiens OIB-nummer|Nej|
|Func_cyprus_eu_tax_file_number|registrerer Cyperns skattefilnummer|Nej|
|Func_czech_id_card_new_format|registrerer tjekkisk id-kort i nyt format|Nej|
|Func_czech_id_card|registrerer tjekkisk id-kort|Nej|
|Func_dea_number|registrerer DEA-nummer|Ja|
|Func_denmark_eu_tax_file_number|registrerer Danmark personidentifikationsnummer|Nej|
|Func_district_of_columbia_drivers_license_number|registrerer District of Columbia-driverens licensnummer|Nej|
|Func_estonia_eu_national_id_card|registrerer Estlands personidentifikationskode|Nej|
|Func_eu_debit_card|registrerer EU-debetkort|Nej|
|Func_finnish_national_id|registrerer finsk nationalt id|Nej|
|Func_florida_drivers_license_number|registrerer Florida-driverens licensnummer|Nej|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|registrerer Florida, Maryland, Michigan, Minnesota kørekort nummer|Nej|
|Func_formatted_itin|registrerer formateret US ITIN|Ja|
|Func_fr_insee|registrerer France INSEE|Nej|
|Func_fr_passport|registrerer Frankrigs pas|Nej|
|Func_france_eu_tax_file_number|registrerer Frankrigs skattefilnummer|Nej|
|Func_france_value_added_tax_number|registrerer momsnummer for Frankrig|Nej|
|Func_french_drivers_license|registrerer fransk kørekort|Nej|
|Func_french_insee|registrerer fransk INSEE|Nej|
|Func_georgia_drivers_license_number|registrerer Georgia-driverens licensnummer|Nej|
|Func_german_drivers_license|registrerer Tysklands kørekort|Nej|
|Func_german_passport_data|registrerer Tysklands pas|Nej|
|Func_german_passport|registrerer Tysklands pas|Nej|
|Func_germany_eu_tax_file_number|registrerer Tysklands skattefilnummer|Nej|
|Func_germany_value_added_tax_number|registrerer Momsnummer for Tyskland|Nej|
|Func_greece_eu_ssn|registrerer Grækenlands synd (AMKA)|Nej|
|Func_hawaii_drivers_license_number|registrerer Hawaii-driverens licensnummer|Nej|
|Func_hong_kong_id_card|registrerer Id-kort for Hongkong|Nej|
|Func_hungarian_value_added_tax_number|registrerer momsnummer for Ungarn|Nej|
|Func_hungary_eu_national_id_card|registrerer Ungarns personidentifikationsnummer|Nej|
|Func_hungary_eu_ssn_or_equivalent|registrerer Ungarns cpr-nummer|Nej|
|Func_hungary_eu_tax_file_number|registrerer Ungarns skattefilnummer|Nej|
|Func_iban|registrerer IBAN|Ja|
|Func_idaho_drivers_license_number|registrerer Idaho-driverens licensnummer|Nej|
|Func_illinois_drivers_license_number|registrerer Illinois-driverens licensnummer|Nej|
|Func_india_aadhaar|registrerer Indien aadhaar|Ja|
|Func_indiana_drivers_license_number|registrerer Indiana-kørekortets nummer|Nej|
|Func_iowa_drivers_license_number|registrerer Iowa-driverens licensnummer|Nej|
|Func_ireland_pps|registrerer Irlands KKS|Nej|
|Func_israeli_national_id_number|registrerer Israels nationale id-nummer|Nej|
|Func_italy_eu_national_id_card|registrerer Italiens skattekode|Nej|
|Func_italy_value_added_tax_number|registrerer Italiens momsnummer|Nej|
|Func_japanese_my_number_corporate|registrerer Japan mit nummer corporate|Ja|
|Func_japanese_my_number_personal|registrerer Japan mit personlige nummer|Ja|
|Func_jp_bank_account_branch_code|registrerer forgreningskoden for bankkontoen i Japan|Nej|
|Func_jp_bank_account|registrerer den japanske bankkonto|Nej|
|Func_jp_drivers_license_number|registrerer Japans kørekortsnummer|Nej|
|Func_jp_passport|registrerer Japan-pas|Nej|
|Func_jp_resident_registration_number|registrerer registreringsnummer for beboere i Japan|Nej|
|Func_jp_sin_pre_1997|registrerer Japans synd før 1997|Nej|
|Func_jp_sin|registrerer Japan SIN|Nej|
|Func_kansas_drivers_license_number|registrerer Kansas-kørekortets nummer|Nej|
|Func_kentucky_drivers_license_number|registrerer Kentucky-driverens licensnummer|Nej|
|Func_kentucky_massachusetts_virginia_drivers_license_number|registrerer Kentucky, Massachusetts, Virginia-driverens licensnummer|Nej|
|Func_latvia_eu_national_id_card|registrerer Letlands personlige kode|Nej|
|Func_lithuania_eu_tax_file_number|registrerer litauens personlige kode|Nej|
|Func_louisiana_drivers_license_number|registrerer Louisiana-driverens licensnummer|Nej|
|Func_luxemburg_eu_tax_file_number_non_natural|registrerer Luxemburgs nationale identifikationsnummer (ikke-fysiske personer)|Nej|
|Func_luxemburg_eu_tax_file_number|registrerer Det nationale identifikationsnummer for Luxemburg (fysiske personer)|Nej|
|Func_maine_drivers_license_number|registrerer Maine-driverens licensnummer|Nej|
|Func_manitoba_drivers_license_number|registrerer Manitoba-kørekortets nummer|Nej|
|Func_maryland_drivers_license_number|registrerer Maryland-kørekortets nummer|Nej|
|Func_massachusetts_drivers_license_number|registrerer Massachusetts-driverens licensnummer|Nej|
|Func_mexico_population_registry_code|registrerer registreringsdatabasekoden for Mexico-populationen|Nej|
|Func_michigan_minnesota_drivers_license_number|registrerer Michigan, Minnesota kørekort nummer|Nej|
|Func_minnesota_drivers_license_number|registrerer Minnesota driverens licensnummer|Nej|
|Func_mississippi_oklahoma_drivers_license_number|registrerer Mississippi, Oklahoma-kørekortets licensnummer|Nej|
|Func_missouri_drivers_license_number|registrerer Missouri-driverens licensnummer|Nej|
|Func_montana_drivers_license_number|registrerer Montana-kørekortets nummer|Nej|
|Func_nebraska_drivers_license_number|registrerer Nebraska-driverens licensnummer|Nej|
|Func_netherlands_bsn|registrerer Hollandsk BSN|Nej|
|Func_netherlands_eu_tax_file_number|registrerer det nederlandske skattefilnummer|Nej|
|Func_netherlands_value_added_tax_number|registrerer det nederlandske momsnummer|Nej|
|Func_nevada_drivers_license_number|registrerer Nevada-driverens licensnummer|Nej|
|Func_new_brunswick_drivers_license_number|registrerer New Brunswick-kørekortets nummer|Nej|
|Func_new_hampshire_drivers_license_number|registrerer New Hampshire-driverens licensnummer|Nej|
|Func_new_jersey_drivers_license_number|registrerer New Jersey-driverens licensnummer|Nej|
|Func_new_mexico_drivers_license_number|registrerer New Mexico-kørekortets nummer|Nej|
|Func_new_york_drivers_license_number|registrerer New York-driverens licensnummer|Nej|
|Func_new_zealand_bank_account_number|registrerer newzealandsk bankkontonummer|Nej|
|Func_new_zealand_inland_revenue_number|registrerer newzealandsk omsætningsnummer|Nej|
|Func_new_zealand_ministry_of_health_number|registrerer newzealandsk ministerium for sundhedsnummer|Nej|
|Func_newfoundland_labrador_drivers_license_number|registrerer Newfoundland Labrador-kørekortets licensnummer|Nej|
|Func_newzealand_driver_license_number|registrerer newzealandsk kørekortsnummer|Nej|
|Func_newzealand_social_welfare_number|registrerer newzealandsk cpr-nummer|Nej|
|Func_north_carolina_drivers_license_number|registrerer North Carolina-driverens licensnummer|Nej|
|Func_north_dakota_drivers_license_number|registrerer North Dakota-driverens licensnummer|Nej|
|Func_norway_id_number|registrerer Norges id-nummer|Nej|
|Func_nova_scotia_drivers_license_number|registrerer Nova Scotias licensnummer|Nej|
|Func_ohio_drivers_license_number|registrerer Ohio-driverens licensnummer|Nej|
|Func_ontario_drivers_license_number|registrerer Ontario driverens licensnummer|Nej|
|Func_pennsylvania_drivers_license_number|registrerer Pennsylvania-driverens licensnummer|Nej|
|Func_pesel_identification_number|registrerer polens nationale id (PESEL)|Nej|
|Func_poland_eu_tax_file_number|registrerer Polens skattefilnummer|Nej|
|Func_polish_national_id|registrerer polens identitetskort|Nej|
|Func_polish_passport_number|registrerer polsk pasnummer|Nej|
|Func_polish_regon_number|registrerer polsk REGON-nummer|Nej|
|Func_portugal_eu_tax_file_number|registrerer Portugals skatteidentifikationsnummer|Nej|
|Func_prince_edward_island_drivers_license_number|registrerer Prince Edward Island kørekort nummer|Nej|
|Func_quebec_drivers_license_number|registrerer Quebec-driverens licensnummer|Nej|
|Func_randomized_formatted_ssn|registrerer randomiseret formateret US SSN|Ja|
|Func_randomized_unformatted_ssn|registrerer tilfældige uformaterede US SSN|Ja|
|Func_rhode_island_drivers_license_number|registrerer Rhode Island-driverens licensnummer|Nej|
|Func_romania_eu_national_id_card|registrerer Rumæniens personlige numeriske kode (CNP)|Nej|
|Func_saskatchewan_drivers_license_number|registrerer Saskatchewan-kørekortets nummer|Nej|
|Func_slovakia_eu_national_id_card|registrerer Slovakiets personlige nummer|Nej|
|Func_slovenia_eu_national_id_card|registrerer Sloveniens entydige masterborgernummer|Nej|
|Func_slovenia_eu_tax_file_number|registrerer sloveniens skattefilnummer|Nej|
|Func_south_africa_identification_number|registrerer Sydafrikas identifikationsnummer|Ja|
|Func_south_carolina_drivers_license_number|registrerer South Carolina-kørekortets nummer|Nej|
|Func_south_dakota_drivers_license_number|registrerer South Dakota-driverens licensnummer|Nej|
|Func_south_korea_resident_number|registrerer bopælsnummer for Sydkorea|Nej|
|Func_spain_eu_DL_and_NI_number_citizen|registrerer Spaniens DL- og NI-nummerborger|Nej|
|Func_spain_eu_DL_and_NI_number_foreigner|registrerer Spanien DL og NI-nummer udlænding|Nej|
|Func_spain_eu_driver er s_license_number|registrerer spaniens kørekortsnummer|Nej|
|Func_spain_eu_tax_file_number|registrerer Spaniens skattefilnummer|Nej|
|Func_spanish_social_security_number|registrerer spansk cpr-nummer|Nej|
|Func_ssn|Funktion til registrering af ikke-randomiseret formateret US SSN|Ja|
|Func_sweden_eu_tax_file_number|registrerer Sveriges skattefilnummer|Nej|
|Func_swedish_national_identifier|registrerer svensk national identifikator|Ja|
|Func_swiss_social_security_number_ahv|registrerer schweizisk cpr-nummer AHV|Nej|
|Func_taiwanese_national_id|registrerer taiwansk nationalt id|Nej|
|Func_tennessee_drivers_license_number|registrerer Tennessee-driverens licensnummer|Nej|
|Func_texas_drivers_license_number|registrerer texas driverens licensnummer|Nej|
|Func_Thai_Citizen_Id|registrerer thai statsborger-id|Nej|
|Func_Turkish_National_Id|registrerer tyrkisk nationalt id|Ja|
|Func_uk_drivers_license|registrerer det britiske kørekort|Nej|
|Func_uk_eu_tax_file_number|registrerer det entydige skattetal for Storbritannien|Nej|
|Func_uk_nhs_number|registrerer UK NHS-nummer|Ja|
|Func_uk_nino|registrerer UK NINO|Nej|
|Func_unformatted_canadian_sin|registrerer ikke-formateret canadisk SIN|Nej|
|Func_unformatted_itin|registrerer uformateret US ITIN|Ja|
|Func_unformatted_ssn|registrerer ikke-randomiserede usformaterede US SSN|Ja|
|Func_usa_uk_passport|registrerer USA- og UK-pas|Ja|
|Func_utah_drivers_license_number|registrerer Utahs kørekortsnummer|Nej|
|Func_vermont_drivers_license_number|registrerer Vermont-driverens licensnummer|Nej|
|Func_virginia_drivers_license_number|registrerer Virginia-driverens licensnummer|Nej|
|Func_washington_drivers_license_number|registrerer Washington-driverens licensnummer|Nej|
|Func_west_virginia_drivers_license_number|registrerer West Virginia-driverens licensnummer|Nej|
|Func_wisconsin_drivers_license_number|registrerer Wisconsins kørekortsnummer|Nej|
|Func_wyoming_drivers_license_number|registrerer Wyoming-driverens licensnummer|Nej|

## <a name="func_us_date"></a>Func_us_date

Func_us_date søger efter datoer i almindelige amerikanske formater. De almindelige formater er "month/day/year", "month-day-year" og "month day year". Der skelnes ikke mellem store og små bogstaver i navnene på eller forkortelserne for måneder.

Eksempler:

- 2. december 2016
- Dec 2, 2016
- dec 02 2016
- 12/2/2016
- 12/02/16
- Dec-2-2016
- 12-2-16

Accepterede månedsnavne:

- English
  - Januar, februar, marts, april, maj, juni, juli, august, september, oktober, november, december
  - Jan. feb. mar. apr. maj juli aug. sept. okt. dec.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates søger efter datoer i fælles E.U. formater (og de fleste steder uden for USA), f.eks. "day/month/year", "day-month-year" og "day month year". Der skelnes ikke mellem store og små bogstaver i navnene på eller forkortelserne for måneder.

Eksempler:

- 2. december 2016
- 02 dec 2016
- 2. december 16
- 2/12/2016
- 02/12/16
- 2. december 2016
- 2-12-16

Accepterede månedsnavne:

- English
  - Januar, februar, marts, april, maj, juni, juli, august, september, oktober, november, december
  - Jan. feb. mar. apr. maj juli aug. sept. okt. dec.
- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, september, ocktober, oktober, november, december
  - jan feb maart apr mei jun jul aug sep sept okt nov dec
- French
  - janvier, février, mars, avril, mai, juin juillet, août, septembre, octobre, novembre, décembre
  - janv. févr. mars avril mai juin juil. août sept. Oktober. November. déc.
- German
  - jänuar, februar, märz, april, mai, juni juli, august, september, oktober, november, dezember
  - Jan./Jän. Feb. März Apr. Mai Juni Juli Aug. Sept. Okt. Nov. Dez.
- Italian
  - gennaio, febbraio, marzo, aprile, maggio, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
  - Genn. febbr. Mar. Apr. magg. giugno luglio ag. sett. Ott. November. Dic.
- Portugisisk
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul siden fastsat nov dez
- Spanish
  - enero, febrero, marzo, abril, mayo, junio, julio, agosto, septiembre, octubre, noviembre, diciembre
  - enero feb. marzo abr. mayojun. jul. agosto sept./set. Oktober. November. Dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (frarådes)

> [!NOTE]
> Denne funktion frarådes, fordi den kun understøtter portugisiske månedsnavne, som nu er inkluderet i funktionen  `Func_eu_date` ovenfor.

Denne funktion søger efter en dato i det format, der ofte bruges på portugisisk. Formatet for denne funktion er det samme som  `Func_eu_date`, der kun adskiller sig fra det anvendte sprog.

Eksempler:

- 2. dez 2016
- 02 dez 2016
- 2. dez 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

Accepterede månedsnavne:

- Portugisisk
  - janeiro, fevereiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar abr mai jun jul siden fastsat nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (frarådes)

> [!NOTE]
> Denne funktion frarådes, fordi den kun understøtter hollandske månedsnavne, som nu er inkluderet i funktionen  `Func_eu_date` ovenfor.

Denne funktion søger efter en dato i det format, der ofte bruges på hollandsk. Formatet for denne funktion er det samme som  `Func_eu_date`, der kun adskiller sig fra det anvendte sprog.

Eksempler:

- 2 Mei 2016
- 02 mei 2016
- 2 Mei 16
- 2/12/2016
- 02/12/16
- 2-Mei-2016
- 2-12-16

Accepterede månedsnavne:

- Dutch
  - januari, februari, maart, April, mei, juni, juli, augustus, september, ocktober, oktober, november, december
  - jan feb maart apr mei jun jul aug sep sept out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date søger efter datoer, der er i formater, der ofte bruges af kredit- og debetkort. Denne funktion matcher datoer i formatet "måned/år", "måned-år", "[månedsnavn] år" og "[månedsforkortelse] år". Der skelnes ikke mellem store og små bogstaver i navnene på eller forkortelserne for måneder.

Eksempler:

- MM/ÅÅÅ – f.eks. 01/11 eller 1/11
- MM/ÅÅÅÅ – f.eks. 01/2011 eller 1/2011
- MM-ÅÅÅ – f.eks. 01-22 eller 1-11
- MM-ÅÅÅÅ - f.eks. 01-2000 eller 1-2000

Følgende formater understøtter YYY eller YYYY:

- Måned-ÅÅÅÅ – f.eks. jan-2010 eller januar-2010 eller jan-10 eller januar-10
- Måned ÅÅÅÅ – f.eks. 'januar 2010' eller 'Jan 2010' eller '10. januar' eller 'Jan 10'
- MonthYYYY – f.eks. 'januar 2010' eller 'Jan2010' eller 'january10' eller 'Jan10'
- Måned/ÅÅÅÅ – f.eks. 'januar/2010' eller 'Jan/2010' eller 'januar/10' eller 'Jan/10'

Accepterede månedsnavne:

- English
  - Januar, februar, marts, april, maj, juni, juli, august, september, oktober, november, december
  - Jan Feb Mar Apr maj juni juli Aug september oktober nov.

## <a name="func_us_address"></a>Func_us_address

Func_us_address søger efter et amerikansk statsnavn eller en forkortelse for postnummer efterfulgt af et gyldigt postnummer. Postnummeret skal være et af de korrekte postnumre, der er knyttet til usa's statsnavn eller forkortelse. Det amerikanske statsnavn og postnummer må ikke adskilles med tegnsætning eller bogstaver.

Eksempler:

- Washington 98052
- Washington 98052-9998
- WA 98052
- WA 98052-9998
