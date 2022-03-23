---
title: Funktioner af typen Følsomme oplysninger
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
description: Få mere at vide om, hvad funktionerne til følsomme oplysninger søger efter.
ms.openlocfilehash: d00b61aeeb435940436bd0c901edce2fef81a3e4
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63594752"
---
# <a name="sensitive-information-type-functions"></a>Funktioner af typen Følsomme oplysninger

Følsomme oplysningstyper (SIT) kan bruge funktioner som primære elementer til at identificere følsomme elementer. For eksempel bruger den følsomme oplysningstype Kreditkortnummer funktionen Func_credit_card til at registrere kreditkortnummer.

Denne artikel forklarer, hvad disse funktioner leder efter, så du kan få hjælp til at forstå, hvordan de foruddefinerede typer af følsomme oplysninger fungerer. Få mere at vide under Definitioner [af objekt af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md)

## <a name="table-of-functions"></a>Tabel over funktioner

|Funktionsnavn | Funktionshandling | Er en validator|
|---------|----------|---------|
|Func_aba_routing|registrerer ABA-registreringsnummer|Ja|
|Func_alabama_drivers_license_number|registrerer Alabama-kørekortnummeret|Nej|
|Func_alaska_delaware_oregon_drivers_license_number|detekterer Alaska, Delaware, Oregon-kørekortnummeret|Nej|
|Func_alaska_drivers_license_number|registrerer Alaska-kørekortnummer|Nej|
|Func_alberta_drivers_license_number|registrerer Alberta-kørekortnummer|Nej|
|Func_argentina_Unique_Tax_Key|registrerer og validerer Argentina Unique-skattenøgle|Nej|
|Func_Argentina_Unique_Tax_Key|registrerer Argentina Unique-skattenøgle|Nej|
|Func_arizona_drivers_license_number|registrerer Arizona-kørekortnummer|Nej|
|Func_arkansas_drivers_license_number|registrerer Arkansas-kørekortnummeret|Nej|
|Func_australian_business_number|registrerer Australiens forretningsnummer|Nej|
|Func_Australian_Company_Number|registrerer Australiens firmanummer|Nej|
|Func_australian_medical_account_number|registrerer Australiens medicinske kontonummer|Nej|
|Func_australian_tax_file_number|registrerer Australiens skattefilnummer|Ja|
|Func_austria_eu_ssn_or_equivalent|registrerer Østrigs CPR-nummer|Nej|
|Func_austria_eu_tax_file_number|registrerer Østrigs skattefilnummer|Nej|
|Func_Austria_Value_Added_Tax|registrerer Østrigs momssats|Nej|
|Func_belgium_national_number|registrerer belgiens nationalt nummer|Nej|
|Func_belgium_value_added_tax_number|registrerer belgiens momsnummer for moms|Nej|
|Func_brazil_cnpj|registrerer Brasiliens juridiske enhedsnummer (CNPJ)|Ja|
|Func_brazil_cpf|registrerer Brasiliens CPF|Ja|
|Func_brazil_rg|registrerer Brasilien RG|Nej|
|Func_british_columbia_drivers_license_number|detekterer British Columbia-kørekortnummeret|Nej|
|Func_bulgaria_eu_national_id_card|registrerer et uniformsnummer for Bulgarien|Nej|
|Func_california_drivers_license_number|registrerer Californiens kørekortnummer|Nej|
|Func_canadian_sin|registrerer Canada sin|Ja|
|Func_chile_id_card|registrerer Chile-id-kort|Nej|
|Func_china_resident_id|registrerer Kina-iboende id|Nej|
|Func_colorado_drivers_license_number|registrerer Colorado-kørekortnummer|Nej|
|Func_connecticut_drivers_license_number|registrerer Connecticut-kørekortnummeret|Nej|
|Func_credit_card|registrerer kreditkort|Ja|
|Func_croatia_id_card|registrerer Kroatisk id-kort|Nej|
|Func_croatia_oib_number|registrerer Kroatiens OIB-nummer|Nej|
|Func_cyprus_eu_tax_file_number|registrerer cyperns skattefilnummer|Nej|
|Func_czech_id_card_new_format|registrerer tjekkisk id-kort i nyt format|Nej|
|Func_czech_id_card|registrerer tjekkisk id-kort|Nej|
|Func_dea_number|registrerer DEA-nummer|Ja|
|Func_denmark_eu_tax_file_number|registrerer Danmark personligt identifikationsnummer|Nej|
|Func_district_of_columbia_drivers_license_number|registrerer District of Columbia-kørekortnummeret|Nej|
|Func_estonia_eu_national_id_card|registrerer estlands personlige identifikationskode|Nej|
|Func_eu_debit_card|registrerer EU-debetkort|Nej|
|Func_finnish_national_id|registrerer finsk national-id|Nej|
|Func_florida_drivers_license_number|registrerer Florida-kørekortnummer|Nej|
|Func_florida_maryland_michigan_minnesota_drivers_license_number|detekterer Florida, Maryland, Michigan, Minnesota kørekortnummer|Nej|
|Func_formatted_itin|registrerer formateret AMERIKANSK ITIN|Ja|
|Func_fr_insee|registrerer Frankrig INSEE|Nej|
|Func_fr_passport|registrerer Frankrigs pas|Nej|
|Func_france_eu_tax_file_number|registrerer Frankrigs skattefilnummer|Nej|
|Func_france_value_added_tax_number|registrerer Frankrigs momsnummer tilføjet|Nej|
|Func_french_drivers_license|registrerer fransk kørekort|Nej|
|Func_french_insee|registrerer fransk INSEE|Nej|
|Func_georgia_drivers_license_number|registrerer Georgia-kørekortnummer|Nej|
|Func_german_drivers_license|registrerer Tysklands kørekort|Nej|
|Func_german_passport_data|registrerer Tysklands pas|Nej|
|Func_german_passport|registrerer Tysklands pas|Nej|
|Func_germany_eu_tax_file_number|registrerer Tysklands skattefilnummer|Nej|
|Func_germany_value_added_tax_number|registrerer Tysklands momsnummer for tilføjet moms|Nej|
|Func_greece_eu_ssn|registrerer Grækenlands (AMKA)|Nej|
|Func_hawaii_drivers_license_number|registrerer Hawaii-kørekortnummer|Nej|
|Func_hong_kong_id_card|registrerer HONG Kong-id-kort|Nej|
|Func_hungarian_value_added_tax_number|registrerer Det ungarske momsnummer (tilføjet moms)|Nej|
|Func_hungary_eu_national_id_card|registrerer Ungarns personlige identifikationsnummer|Nej|
|Func_hungary_eu_ssn_or_equivalent|registrerer Ungarns CPR-nummer|Nej|
|Func_hungary_eu_tax_file_number|registrerer det ungarske skattefilnummer|Nej|
|Func_iban|registrerer IBAN|Ja|
|Func_idaho_drivers_license_number|registrerer Idaho-kørekortnummeret|Nej|
|Func_illinois_drivers_license_number|detekterer Illinois-kørekortnummeret|Nej|
|Func_india_aadhaar|registrerer Indien aadhaar|Ja|
|Func_indiana_drivers_license_number|registrerer Indiana-kørekortnummer|Nej|
|Func_iowa_drivers_license_number|registrerer Iowa-kørekortnummeret|Nej|
|Func_ireland_pps|registrerer Ireland PPS|Nej|
|Func_israeli_national_id_number|registrerer Israels nationale id-nummer|Nej|
|Func_italy_eu_national_id_card|registrerer Italiens regnskabskode|Nej|
|Func_italy_value_added_tax_number|registrerer momsnummer for værdi tilføjet moms i Italien|Nej|
|Func_japanese_my_number_corporate|detekterer mit firmanummer i Japan|Ja|
|Func_japanese_my_number_personal|registrerer Japan mit nummer personligt|Ja|
|Func_jp_bank_account_branch_code|registrerer japans bankkontogrenskode|Nej|
|Func_jp_bank_account|detekterer en japansk bankkonto|Nej|
|Func_jp_drivers_license_number|registrerer japans kørekortnummer|Nej|
|Func_jp_passport|detekterer japan pas|Nej|
|Func_jp_resident_registration_number|registrerer japan-iboende registreringsnummer|Nej|
|Func_jp_sin_pre_1997|registrerer Japans sin før 1997|Nej|
|Func_jp_sin|registrerer Japan SIN|Nej|
|Func_kansas_drivers_license_number|registrerer Kansas-kørekortnummer|Nej|
|Func_kentucky_drivers_license_number|detekterer dens kørekortnummer|Nej|
|Func_kentucky_massachusetts_virginia_drivers_license_number|detekterer Virginia, Washington, Virginia-kørekortnummeret|Nej|
|Func_latvia_eu_national_id_card|registrerer Letlands personlige kode|Nej|
|Func_lithuania_eu_tax_file_number|registrerer Litauens personlige kode|Nej|
|Func_louisiana_drivers_license_number|registrerer Louisiana-kørekortnummer|Nej|
|Func_luxemburg_eu_tax_file_number_non_natural|registrerer Luxemburgs nationale identifikationsnummer (ikke-naturlige personer)|Nej|
|Func_luxemburg_eu_tax_file_number|registrerer Luxemburgs nationale identifikationsnummer (fysiske personer)|Nej|
|Func_maine_drivers_license_number|registrerer Maine-kørekortnummeret|Nej|
|Func_manitoba_drivers_license_number|registrerer Manitoba-kørekortnummeret|Nej|
|Func_maryland_drivers_license_number|registrerer Maryland-kørekortnummer|Nej|
|Func_massachusetts_drivers_license_number|registrerer dens kørekortnummer|Nej|
|Func_mexico_population_registry_code|registrerer registreringsdatabasekoden for Mexicos population|Nej|
|Func_michigan_minnesota_drivers_license_number|detekterer Michigan, Minnesota-kørekortnummeret|Nej|
|Func_minnesota_drivers_license_number|registrerer Minnesota-kørekortnummeret|Nej|
|Func_mississippi_oklahoma_drivers_license_number|registrerer Mississippi, Oklahoma-kørekortnummeret|Nej|
|Func_missouri_drivers_license_number|registrerer Missouri-kørekortnummer|Nej|
|Func_montana_drivers_license_number|registrerer Montana-kørekortnummer|Nej|
|Func_nebraska_drivers_license_number|registrerer Nebraska-kørekortnummeret|Nej|
|Func_netherlands_bsn|registrerer nederlandsk BSN|Nej|
|Func_netherlands_eu_tax_file_number|registrerer nederlandsk momsfilnummer|Nej|
|Func_netherlands_value_added_tax_number|registrerer nederlandsk momsnummer (tilføjet moms)|Nej|
|Func_nevada_drivers_license_number|registrerer Nevada-kørekortnummer|Nej|
|Func_new_brunswick_drivers_license_number|registrerer New Brunswick-kørekortnummeret|Nej|
|Func_new_hampshire_drivers_license_number|registrerer New Serienummer-kørekortnummeret|Nej|
|Func_new_jersey_drivers_license_number|registrerer New Jersey-kørekortnummeret|Nej|
|Func_new_mexico_drivers_license_number|registrerer New Mexico-kørekortnummer|Nej|
|Func_new_york_drivers_license_number|registrerer New York-kørekortnummeret|Nej|
|Func_new_zealand_bank_account_number|registrerer New Zealands bankkontonummer|Nej|
|Func_new_zealand_inland_revenue_number|registrerer new zealandsk indtægtsnummer|Nej|
|Func_new_zealand_ministry_of_health_number|registrerer New Zealand, der er del af et sundhedsnummer|Nej|
|Func_newfoundland_labrador_drivers_license_number|registrerer Newfoundland Labradors kørekortnummer|Nej|
|Func_newzealand_driver_license_number|registrerer New Zealand-kørekortnummer|Nej|
|Func_newzealand_social_welfare_number|registrerer New Zealands sociale nummer|Nej|
|Func_north_carolina_drivers_license_number|registrerer North Carolina-kørekortnummeret|Nej|
|Func_north_dakota_drivers_license_number|registrerer North Dakota-kørekortnummeret|Nej|
|Func_norway_id_number|registrerer Norges id-nummer|Nej|
|Func_nova_scotia_drivers_license_number|registrerer Nova Scotia-kørekortnummeret|Nej|
|Func_ohio_drivers_license_number|registrerer Ohio-kørekortnummer|Nej|
|Func_ontario_drivers_license_number|registrerer Ontario-kørekortnummeret|Nej|
|Func_pennsylvania_drivers_license_number|registrerer Pennsylvania-kørekortnummer|Nej|
|Func_pesel_identification_number|registrerer Polens nationale id (PESEL)|Nej|
|Func_poland_eu_tax_file_number|registrerer Polens skattefilnummer|Nej|
|Func_polish_national_id|registrerer Polens identitetskort|Nej|
|Func_polish_passport_number|registrerer polsk pasnummer|Nej|
|Func_polish_regon_number|registrerer polsk REGON-nummer|Nej|
|Func_portugal_eu_tax_file_number|registrerer Portugals skatteidentifikationsnummer|Nej|
|Func_prince_edward_island_drivers_license_number|registrerer Prince Edward Island-kørekortnummeret|Nej|
|Func_quebec_drivers_license_number|registrerer Quebecs kørekortnummer|Nej|
|Func_randomized_formatted_ssn|registrerer vilkårligt formateret amerikansk SSN|Ja|
|Func_randomized_unformatted_ssn|registrerer vilkårligt uformateret amerikansk SSN|Ja|
|Func_rhode_island_drivers_license_number|registrerer Rhode Island-kørekortnummeret|Nej|
|Func_romania_eu_national_id_card|registrerer Rumæniens personlige numeriske kode (CNP)|Nej|
|Func_saskatchewan_drivers_license_number|registrerer Saskatchewan-kørekortnummer|Nej|
|Func_slovakia_eu_national_id_card|registrerer Slovakiets personlige nummer|Nej|
|Func_slovenia_eu_national_id_card|registrerer sloveniens entydige masternummer for borgere|Nej|
|Func_slovenia_eu_tax_file_number|registrerer sloveniens skattefilnummer|Nej|
|Func_south_africa_identification_number|registrerer id-nummer for Sydafrika|Ja|
|Func_south_carolina_drivers_license_number|registrerer South Carolina-kørekortnummeret|Nej|
|Func_south_dakota_drivers_license_number|registrerer South Dakota-kørekortnummeret|Nej|
|Func_south_korea_resident_number|registrerer Sydkoreas iboende nummer|Nej|
|Func_spain_eu_DL_and_NI_number_citizen|registrerer Spaniens DL og NI-antal borgere|Nej|
|Func_spain_eu_DL_and_NI_number_foreigner|registrerer Foreigner for Spaniens DL- og NI-nummer|Nej|
|Func_spain_eu_driver ikke s_license_number|registrerer Spaniens kørekortnummer|Nej|
|Func_spain_eu_tax_file_number|registrerer Spaniens skattefilnummer|Nej|
|Func_spanish_social_security_number|registrerer spansk CPR-nummer|Nej|
|Func_ssn|Funktion til at registrere ikke-randomiserede formaterede SSN'er (US)|Ja|
|Func_sweden_eu_tax_file_number|registrerer Sveriges skattefilnummer|Nej|
|Func_swedish_national_identifier|registrerer svensk nationalt id|Ja|
|Func_swiss_social_security_number_ahv|registrerer schweizisk CPR-nummer AHV|Nej|
|Func_taiwanese_national_id|registrerer Taiwanesisk national id|Nej|
|Func_tennessee_drivers_license_number|detekterer dens kørekortnummer|Nej|
|Func_texas_drivers_license_number|registrerer Texas-kørekortnummer|Nej|
|Func_Thai_Citizen_Id|detekterer thai-id'et for borgere|Nej|
|Func_Turkish_National_Id|registrerer tyrkisk national-id|Ja|
|Func_uk_drivers_license|registrerer storbritanniens kørekort|Nej|
|Func_uk_eu_tax_file_number|registrerer det entydige skatteydernummer i Storbritannien|Nej|
|Func_uk_nhs_number|detekterer UK NHS-nummer|Ja|
|Func_uk_nino|registrerer UK NINO|Nej|
|Func_unformatted_canadian_sin|registrerer uformateret Canadisk SIN|Nej|
|Func_unformatted_itin|registrerer uformaterede AMERIKANSKE ITIN|Ja|
|Func_unformatted_ssn|registrerer ikke-randomiserede uformaterede amerikanske SSN|Ja|
|Func_usa_uk_passport|registrerer USA- og STORBRITANNIEN-pas|Ja|
|Func_utah_drivers_license_number|registrerer Utah-kørekortnummer|Nej|
|Func_vermont_drivers_license_number|registrerer Vermont-kørekortnummer|Nej|
|Func_virginia_drivers_license_number|registrerer Virginia-kørekortnummeret|Nej|
|Func_washington_drivers_license_number|registrerer Washington-kørekortnummer|Nej|
|Func_west_virginia_drivers_license_number|registrerer West Virginia-kørekortnummeret|Nej|
|Func_wisconsin_drivers_license_number|registrerer Wisconsin-kørekortnummeret|Nej|
|Func_wyoming_drivers_license_number|detekterer Wyoming-kørekortnummeret|Nej|

## <a name="func_us_date"></a>Func_us_date

Func_us_date søger efter datoer i almindelige amerikanske formater. De almindelige formater er "måned/dag/år", "måned-dag-år" og "månedsdag år". Navnene eller forkortelserne for måneder tager ikke hensyn til store og små bogstaver.

Eksempler:

- 2. december 2016
- 2. dec 2016
- dec 02 2016
- 12/2/2016
- 12/02/16
- 2. december 2016
- 12-2-16

Accepterede månedsnavne:

- English
  - Januar, februar, marts, april, maj, juni, juli, august, september, oktober, november, december
  - Jan. Feb. Mar. Apr. Maj juli 18. august. September. Nov. Dec.

## <a name="func_eu_date"></a>Func_eu_date

Fund_eu_dates søger efter datoer i fælles e.Kr. formater (og de fleste steder uden for USA), f.eks. "dag/måned/år", "dag-måned-år" og "dag måned år". Navnene eller forkortelserne for måneder tager ikke hensyn til store og små bogstaver.

Eksempler:

- 2. dec 2016
- 02. dec 2016
- 2. dec 16
- 2/12/2016
- 02/12/16
- 2- dec-2016
- 2-12-16

Accepterede månedsnavne:

- English
  - Januar, februar, marts, april, maj, juni, juli, august, september, oktober, november, december
  - Jan. Feb. Mar. Apr. Maj juli 18. august. September. Nov. Dec.
- Dutch
  - januari, februari, maart, april, mei, juni, juli, augustus, September, ocktober, oktober, november, december
  - jan feb maart apr mei jun aug sep sept oct okt nov dec
- French
  - janvier, février, mars, avril, mai, juin juillet, aoút, septembre, octobre, novembre, décembre
  - janv. févr. mars avril mai juin juil. aoút sept. okt. nov. déc.
- German
  - jänuar, februar, märz, april, mai, juni juli, august, september, oktober, november, dezember
  - Jan./Jän. Feb. März Apr. Mai Juni Juli Aug. Sept. Okt. Nov. Dez.
- Italian
  - gennaio, febbraio, marzo, aprile, motto, giugno, luglio, agosto, settembre, ottobre, novembre, dicembre
  - genn. feb br. mar. apr. magg. giugno luglio ag. . ott. nov. dic.
- Portugisisk
  - Janeiro, janeiroeiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar a br mai jun jul ago set out nov dez
- Spanish
  - eneo, febrologi, marzo, abril, mayo, junio, julio, agosto, seakaembre, octubre, noviembre, diciembre
  - dat feb. marzo a br. mayo jun. jul. agosto sept./set. okt. nov. dic.

## <a name="func_eu_date1-deprecated"></a>Func_eu_date1 (forældet)

> [!NOTE]
> Denne funktion frarådes, fordi den kun understøtter portugisiske månedsnavne, som nu er inkluderet i  `Func_eu_date` funktionen ovenfor.

Denne funktion søger efter en dato i det format, der ofte bruges på portugisisk. Formatet for denne funktion er det samme som  `Func_eu_date`, og det varierer kun i det anvendte sprog.

Eksempler:

- 2 Dez 2016
- 02 dez 2016
- 2 Dez 16
- 2/12/2016
- 02/12/16
- 2-Dez-2016
- 2-12-16

Accepterede månedsnavne:

- Portugisisk
  - Janeiro, janeiroeiro, março, marco, abril, maio, junho, julho, agosto, setembro, outubro, novembro, dezembro
  - jan fev mar a br mai jun jul ago set out nov dez

## <a name="func_eu_date2-deprecated"></a>Func_eu_date2 (forældet)

> [!NOTE]
> Denne funktion frarådes, fordi den kun understøtter nederlandske månedsnavne, som nu er inkluderet i  `Func_eu_date` funktionen ovenfor.

Denne funktion søger efter en dato i det format, der ofte bruges på hollandsk. Formatet for denne funktion er det samme som  `Func_eu_date`, og det varierer kun i det anvendte sprog.

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
  - januari, februari, maart, april, mei, juni, juli, augustus, September, ocktober, oktober, november, december
  - jan feb maart apr mei jun jul aug sep sept out okt nov dec

## <a name="func_expiration_date"></a>Func_expiration_date

Func_expiration_date søger efter datoer, der er i formater, der ofte bruges af kredit- og debetkort. Denne funktion matcher datoer i formatet "måned/år", "måned-år", "[månedsnavn] år" og "[månedsforkortelse] år". Navnene eller forkortelserne for måneder tager ikke hensyn til store og små bogstaver.

Eksempler:

- MM/YY – f.eks. 01/11 eller 1/11
- MM/YYYY – f.eks. 01-2011 eller 1/2011
- MM-YY – f.eks. 01-22 eller 1-11
- MM-YYYY – f.eks. 01-2000 eller 1-2000

Følgende formater understøtter YY eller YYYY:

- Måned-YYYY – f.eks. jan-2010 eller januar-2010 eller jan-10 eller januar-10
- Måned YYYY – f.eks. "januar 2010" eller "januar 2010" eller "10. januar" eller "10. januar"
- MonthYYY – f.eks. 'januar2010' eller 'jan2010' eller 'januar10' eller 'jan10'
- Måned/YYYY – f.eks. 'januar/2010' eller 'jan/2010' eller 'januar/10' eller 'jan/10'

Accepterede månedsnavne:

- English
  - Januar, februar, marts, april, maj, juni, juli, august, september, oktober, november, december
  - Jan feb. mar apr. juni, juli 1. september september d. 1. nov. dec

## <a name="func_us_address"></a>Func_us_address

Func_us_address søger efter et gyldigt postnummer efterfulgt af et gyldigt postnummer. Postnummeret skal være et af de korrekte postnumre, der er knyttet til det amerikanske statsnavn eller forkortelse. Usa's navn og postnummer kan ikke adskilles med tegnsætning eller bogstaver.

Eksempler:

- Washington 98052
- Washington 98052-9998
- WA 98052
- WA 98052-9998
