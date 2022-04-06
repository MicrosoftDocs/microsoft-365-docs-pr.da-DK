---
title: Reference til politik til forebyggelse af datatab
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 03/02/2022
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: Komponent- og konfigurationsreference for DLP-politik
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: d94277ac4ee3bd78feecf660e03d60a5720d1b43
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606692"
---
# <a name="data-loss-prevention-policy-reference"></a>Reference til politik til forebyggelse af datatab

Politikker for forebyggelse af datatab (DLP) har mange komponenter, der skal konfigureres. Hvis du vil oprette en effektiv politik, skal du forstå, hvad formålet med hver komponent er, og hvordan dens konfiguration ændrer politikkens funktionsmåde. Denne artikel indeholder en detaljeret oversigt over en DLP-politik.

## <a name="policy-templates"></a>Politikskabeloner 

DLP-politikskabeloner er sorteret på forhånd i fire kategorier:

- Dem, der kan registrere og beskytte typer **af finansielle** oplysninger.
- Dem, der kan registrere og beskytte typer **af medicinske og sundhedsoplysninger** .
- Dem, der kan registrere og beskytte **typer af personlige** oplysninger.
- En **brugerdefineret** skabelon, du kan bruge til at opbygge din egen politik, hvis en af de andre ikke opfylder behovene i din organisation.

Denne tabel viser alle politikskabeloner og de følsomme oplysningstyper (SIT), som de dækker. 

opdateret: 23-06-2021

|Kategori| Skabelon | SIT |
|---------|---------|---------|
|Finansiel| Finansielle data fra Australien| - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Australiens momsfilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Australiens bankkontonummer](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansiel| Finansielle data for Canada |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Canadas bankkontonummer](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|Finansiel| Finansielle data for Frankrig |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [EU-debetkortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansiel| Finansielle data fra Tyskland |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [EU-debetkortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansiel| Israels finansielle data |- [Israels bankkontonummer](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansiel| Finansielle data for Japan |- [Japans bankkontonummer](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansiel| FUNKTIONER DatasikkerhedsstandardEN FOR 2010 (FUNKTIONER DSS)|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansiel| Anti cyberkriminsk lov i Saudi-Arabien|- [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Nummer på international bankkonto (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|Finansiel| Finansielle data for Saudi-Arabien |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Nummer på international bankkonto (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|Finansiel| Finansielle data i Storbritannien|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [EU-debetkortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Finansiel| Amerikanske finansielle data|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA-registreringsnummer](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansiel| Amerikanske nationale forbrugerregler (Federal Trade Commission, FTC)|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA-registreringsnummer](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansiel| AMERIKANSK Gramm-Leach-Bliley Act (GLBA) Enhanced|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [USA Id-nummer for individuelle skatteydere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [USA/Storbritannien pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[USA kørekortnummer](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Finansiel| USA Gramm-Leach-Bliley Act (GLBA)|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [USA Id-nummer for individuelle skatteydere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Medicin og sundhed| Australia Health Records Act (HRIP Act) Enhanced |- [Australiens momsfilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Australiens medicinske kontonummer](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Fysiske adresser i Australien](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Medicin og sundhed| Australia Health Records Act (HRIP Act)|- [Australiens momsfilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Australiens medicinske kontonummer](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|Medicin og sundhed| Canada Health Information Act (PLATFORM) |- [Canada pasnummer](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada Social Insurance Number](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Canada health service number](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canada Personal Health Identification Number](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medicin og sundhed| Canada Personal Health Information Act (PHIA) Manitoba|- [Canada Social Insurance Number](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Canada health service number](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canada Personal Health Identification Number](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medicin og sundhed| Canada Personal Health Act (PHIPA) Ontario |- [Canada pasnummer](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada Social Insurance Number](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Canada health service number](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canada Personal Health Identification Number](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medicin og sundhed| Storbritannien Adgang til Medical Reports Act|- [Storbritannien Nationalt sundhedstjenestenummer](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [Storbritannien Nationalt forsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|Medicin og sundhed| USA Health Insurance Act (HIPAA) Enhanced|</br> - [International klassificering af klassifikationer (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [International klassificering af klassifikationer (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Medicin og sundhed| USA Health Insurance Act (HIPAA)| - [International klassificering af klassifikationer (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [International klassificering af klassifikationer (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|Beskyttelse af personlige oplysninger| Australia Privacy Act Enhanced|- [Australiens kørekortnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Australiens pasnummer](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Fysiske adresser i Australien](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Beskyttelse af personlige oplysninger| Australia Privacy Act|- [Australiens kørekortnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Australiens pasnummer](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|Beskyttelse af personlige oplysninger| Data om personlige oplysninger (PII) i Australien|- [Australiens momsfilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Australiens kørekortnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger (PII) i Canada|- [Canada-kørekortnummer](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [Canadas bankkontonummer](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Canada pasnummer](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada Social Insurance Number](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Canada health service number](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canada Personal Health Identification Number](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Beskyttelse af personlige oplysninger| Canada Personal Information Protection Act (PIPA)|- [Canada pasnummer](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada Social Insurance Number](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Canada health service number](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canada Personal Health Identification Number](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Beskyttelse af personlige oplysninger| Canada Personal Information Protection Act (PIPEDA)|- [Canada-kørekortnummer](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [Canadas bankkontonummer](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Canada pasnummer](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada Social Insurance Number](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Canada health service number](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canada Personal Health Identification Number](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Beskyttelse af personlige oplysninger| France Data Protection Act|- [Frankrigs nationale id-kort (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [Frankrigs CPR-nummer (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger (PII) i Frankrig|- [Frankrigs CPR-nummer (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [Frankrigs kørekortnummer](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [Frankrigs pasnummer](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [Frankrigs nationale id-kort (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|Beskyttelse af personlige oplysninger| Generel forordning om databeskyttelse (GDPR) Enhanced|- [Fysiske adresser i Østrig](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [Fysiske adresser i Belgien](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [Fysiske adresser i Bulgarien](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [Fysiske adresser i Kroatien](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [Fysiske adresser i Cypern](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [Fysiske adresser for Tjekkiet](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [Fysiske adresser for Danmark](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [Fysiske adresser i Estland](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [Finlands fysiske adresser](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [Fysiske adresser i Frankrig](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [Fysiske adresser i Tyskland](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [Fysiske adresser i Grækenland](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [Fysiske adresser i Ungarn](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [Fysiske adresser i Irland](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [Fysiske adresser i Italien](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [Fysiske adresser i Letland](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [Fysiske adresser i Litauen](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [Fysiske adresser i Luxembourg](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [Fysiske adresser i Malta](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [Nederlandske fysiske adresser](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [Polens fysiske adresser](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [Fysiske portugisiske adresser](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [Fysiske adresser i Rumænien](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [Fysiske adresser i Slovakiet](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [Fysiske adresser i Slovenien](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [Fysiske adresser i Spanien](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [Fysiske adresser i Sverige](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [Østrigs CPR-nummer](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [France Social Security Number (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [Grækenlands CPR-nummer (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [Ungarsk CPR-nummer (DEN UNGARSKE CPR-NUMMER)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [CPR-nummer (Spain Social Security Number)](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [Østrigs identitetskort](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [Cypernsidentitetskort](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [Tysklands identitetskortnummer](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [Maltas identitetskortnummer](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [France National ID Card (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [Grækenlands nationale id-kort](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [Finlands nationale id](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [Polens nationale id (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [Sveriges nationale id](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [OIB-nummer (Croatia Personal Identification)](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [Tjekkisk personligt identitetsnummer](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [Danmark Personligt identifikationsnummer](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [Estlands personlige identifikationskode](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [Ungarns personlige identifikationsnummer](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [Luxemburgs nationale identifikationsnummer (fysiske personer)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [Luxemburgs nationale identifikationsnummer (ikke-naturlige personer)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [Italiens regnskabskode](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [Letlands personlige kode](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [Litauens personlige kode](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [Rumæniens personlige numeriske kode (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [Nederlandske borgeres servicenummer](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [Ireland Personal Public Service-nummer (PPS)](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [Bulgariens uniformsnummer](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [Belgiens nationale nummer](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [Spain DNI](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [Sloveniens entydige masternummer for borgere](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [Slovakiets personlige nummer](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [Portugals borgeres kortnummer](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [Maltas skatte-id](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [Skatte-id for Østrig](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [Cyperns skatte-id](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [France Tax Identification Number (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [Tysklands skatte-id](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [Græsk skatte-id](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [Ungarns skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [Nederlandsk skatte-id](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [Polens skatte-id](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [Portugals skatte-id](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [Sloveniens skatte-id](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [Spaniens skatte-id](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [Sveriges skatte-id](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [Østrigs kørekort](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [Belgiens kørekortnummer](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [Bulgariens kørekortnummer](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [Kroatiens kørekortnummer](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [Cyperns kørekortnummer](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [Tjekkisk kørekortnummer](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [Danmark Kørekortnummer](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [Estlands kørekortnummer](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [Finlands kørekortnummer](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [Frankrigs kørekortnummer](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [Tysk kørekortnummer](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [Grækenlands kørekortnummer](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [Ungarns kørekortnummer](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [Irlands kørekortnummer](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [Italiens kørekortnummer](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [Letland Kørekortnummer](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [Litauens kørekortnummer](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [Luxemburg kørekortnummer](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [Maltas kørekortnummer](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [Nederlandsk kørekortnummer](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [Polens kørekortnummer](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [Portugal Kørekortnummer](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [Rumæniens kørekortnummer](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [Slovakiets kørekortnummer](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [Sloveniens kørekortnummer](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [Spanien-kørekortnummer](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [Sveriges kørekortnummer](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [Østrigs pasnummer](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [Belgiens pasnummer](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [Bulgariens pasnummer](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [Kroatiens pasnummer](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [Cyperns pasnummer](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [Tjekkisk pasnummer](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [Danmark pasnummer](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [Estlands pasnummer](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [Finland-pasnummer](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [Frankrigs pasnummer](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [Tysk pasnummer](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [Grækenlands pasnummer](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [Ungarns pasnummer](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [Irlands pasnummer](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [Italiens pasnummer](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [Letlands pasnummer](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [Litauens pasnummer](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [Luxemburg pasnummer](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [Maltas pasnummer](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [Nederlandsk pasnummer](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [Polens pas](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [Portugal-pasnummer](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [Rumæniens pasnummer](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [Slovakiets pasnummer](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [Sloveniens pasnummer](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [Spaniens pasnummer](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [Sveriges pasnummer](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [EU-debetkortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)|
|Beskyttelse af personlige oplysninger| Persondataforordningen (GDPR)|- [EU-debetkortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [EU-kørekortnummer](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [EU-national identifikationsnummer](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [EU-pasnummer](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [EU-nummer til personnummer eller tilsvarende identifikation](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [EU-skatte-id](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger (PII) i Tyskland|- [Tysklands kørekortnummer](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [Tysklands pasnummer](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|Beskyttelse af personlige oplysninger| Israel personidentificerbare oplysninger (PII)-data|- [Israels nationale identifikationsnummer](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|Beskyttelse af personlige oplysninger| Israels beskyttelse af personlige oplysninger|- [Israels nationale identifikationsnummer](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [Israels bankkontonummer](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|Beskyttelse af personlige oplysninger| Data, der er forbedret af personlige oplysninger (Japan Personally Identifiable Information)|- [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [Mit nummer i Japan – personlig](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Japan pasnummer](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [Japansk kørekortnummer](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Fysiske adresser i Japan](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger (PII)-data (Japan Personally Identifiable Information)|- [Japans registreringsnummer for iboende](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Beskyttelse af personlige oplysninger| Forbedret beskyttelse af personlige oplysninger i Japan|- [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [Mit nummer i Japan – personlig](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Japan pasnummer](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [Japansk kørekortnummer](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Fysiske adresser i Japan](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Beskyttelse af personlige oplysninger| Beskyttelse af personlige oplysninger i Japan|- [Japans registreringsnummer for iboende](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger (PII) i Saudi-Arabien|- [Saudi-Arabiens nationale id](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|Beskyttelse af personlige oplysninger| Storbritannien Lov om databeskyttelse|- [Storbritannien Nationalt forsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [USA/Storbritannien pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Beskyttelse af personlige oplysninger| Storbritannien Bestemmelser om beskyttelse af personlige oplysninger og elektronisk kommunikation|- [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Beskyttelse af personlige oplysninger| Storbritannien Personidentificerbare oplysninger (PII)-data|- [Storbritannien Nationalt forsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [USA/Storbritannien pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Beskyttelse af personlige oplysninger| Storbritannien Praksis for brug af PIOCP (Personal Information Online Code of Practice)|- [Storbritannien Nationalt forsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Storbritannien Nationalt sundhedstjenestenummer](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Beskyttelse af personlige oplysninger| USA Act Enhanced|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [USA Id-nummer for individuelle skatteydere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Beskyttelse af personlige oplysninger| USA Den amerikanske 2016-act|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [USA Id-nummer for individuelle skatteydere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Beskyttelse af personlige oplysninger| USA Personidentificerbare oplysninger (PII)-data forbedret|- [USA Id-nummer for individuelle skatteydere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [USA/Storbritannien pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Beskyttelse af personlige oplysninger| USA Personidentificerbare oplysninger (PII)-data|- [USA Id-nummer for individuelle skatteydere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [USA/Storbritannien pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Beskyttelse af personlige oplysninger| USA Statslige love om meddelelse om sikkerhedsbrud er blevet udvidet|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[USA kørekortnummer](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [USA/Storbritannien pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|Beskyttelse af personlige oplysninger| USA Statslige love om meddelelse om sikkerhedsbrud|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [AMERIKANSK bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[USA kørekortnummer](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Beskyttelse af personlige oplysninger| USA Statslige love om hemmeligholdelse af CPR-nummer|- [USA CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>Placeringer

En DLP-politik kan finde og beskytte elementer, der indeholder følsomme oplysninger på tværs af flere placeringer.

|Placering  |Medtag/udelad omfang  |Datatilstand  |Yderligere forudsætninger |
|---------|---------|---------|---------|
|Exchange mail online |distributionsgruppe | data i bevægelse| Nej |
|SharePoint onlinewebsteder   |websteder       | data-at-rest </br> data i brug | Nej|
|OneDrive for Business konti| konto eller distributionsgruppe |data-at-rest </br> data i brug|Nej|
|Teams chat og kanalmeddelelser     | konto eller distributionsgruppe |data i bevægelse </br> data i brug |  Nej       |
|Microsoft Defender til skyapps   | forekomst af skyapp       |data-at-rest         | - [Brug politikker til forebyggelse af datatab til ikke-Microsoft-skyapps](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|Enheder  |bruger eller gruppe         |data-at-rest </br>  data i brug </br>  data i bevægelse         |- [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention) </br>- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention) </br>- [Konfigurere indstillinger for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|Lokale lager (filshares og SharePoint)    |lager         | data-at-rest         | - [Få mere at vide Microsoft 365 lokal scanner til forebyggelse af datatab](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner) </br> - [Kom i gang med den lokale scanner til forebyggelse af datatab](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| arbejdsområder | data i brug | Nej|

Hvis du vælger at medtage bestemte distributionsgrupper i Exchange, begrænses DLP-politikken kun til medlemmer af den pågældende gruppe. På samme måde udelukker en distributionsgruppe alle medlemmer af den pågældende distributionsgruppe fra evaluering af politikker. Du kan vælge at begrænse en politik til medlemmer af distributionslister, dynamiske distributionsgrupper og sikkerhedsgrupper. En DLP-politik kan højst indeholde 50 af sådanne medtagelser og udeladelse.

Hvis du vælger at medtage eller udelade bestemte SharePoint-websteder eller OneDrive-konti, kan en DLP-politik højst indeholde 100 f.eks. inklusioner og udeladelse. Selvom denne grænse findes, kan du overskride denne grænse ved enten at anvende en politik for hele organisationen eller en politik, der gælder for hele placeringer.

Hvis du vælger at medtage eller udelade bestemte OneDrive-konti eller grupper, kan en DLP-politik højst indeholde 100 brugerkonti eller 50 grupper som inklusion eller udelukkelse.

### <a name="location-support-for-how-content-can-be-defined"></a>Placeringssupport til, hvordan indhold kan defineres

DLP-politikker registrerer følsomme elementer ved at matche dem med en følsom oplysningstype (SIT), eller til en følsomhedsmærkat eller et opbevaringsnavn. Hver placering understøtter forskellige metoder til at definere følsomt indhold. Når du kombinerer placeringer i en politik, kan den måde, som indholdet kan defineres på, ændres fra den måde, det kan defineres på af en enkelt placering. 

> [!IMPORTANT]
> Når du vælger flere placeringer for en politik, tilsidesætter en "nej"-værdi for en indholdsdefinitionskategori "ja"-værdi. Når du f.eks. vælger SharePoint websteder, understøtter politikken registrering af følsomme elementer efter en eller flere SIT-elementer, efter følsomhedsmærkat eller efter opbevaringsmærkat. Men når du vælger ***SharePoint websteder og*** Teams chat- og kanalbeskedplaceringer, understøtter politikken kun registrering af følsomme elementer efter SIT.

|Placering| Indhold kan defineres af SIT| Indhold kan defineres som følsomhedsmærkat| Indhold kan defineres ved hjælp af en opbevaringsetiket|
|---------|---------|---------|---------|
|Exchange mail online|Ja| Ja| Nej|
|SharePoint onlinewebsteder| Ja| Ja| Ja|
|OneDrive for Business konti| Ja| Ja| Ja|
|Teams chat- og kanalmeddelelser | Ja| Nej| Nej|
|Enheder |Ja | Ja|  Nej|
|Microsoft Defender til skyapps | Ja| Ja| Ja|
|Lokale lagre| Ja| Ja| Nej|
|PowerBI|Ja | Ja| Nej|

> [!NOTE]
> DLP understøtter registrering af følsomhedsetiketter på mails og vedhæftede filer Se Brug [følsomhedsmærkater som betingelser i DLP-politikker](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>Regler

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

Regler er forretningslogik i DLP-politikker. De består af:

- [**Betingelser,**](#conditions) der udløser politikken, når de matches
- [**Undtagelser**](#exceptions) til betingelserne
- [**Handlinger**](#actions) , der skal udføres, når politikken udløses
- [**Brugerbeskeder**](#user-notifications-and-policy-tips) til at informere brugerne, når de gør noget, der udløser en politik, og som hjælper med at informere dem om, hvordan din organisation ønsker, at følsomme oplysninger behandles
- [**Bruger tilsidesætter,**](#user-overrides) når den konfigureres af en administrator, kan brugerne vælge at tilsidesætte en blokeringshandling
- [**Hændelsesrapporter**](#incident-reports) , der giver administratorer og andre vigtige interessenter besked, når der opstår et regelmatch
- [**Flere indstillinger**](#additional-options) , som definerer prioriteten for regelevaluering og kan stoppe yderligere behandling af regler og politikker.

 En politik indeholder en eller flere regler. Regler udføres sekventielt, startende med reglen med højeste prioritet i hver politik.

### <a name="the-priority-by-which-rules-are-processed"></a>Den prioritet, som regler behandles efter

#### <a name="hosted-service-workloads"></a>Arbejdsbelastninger for hostede tjenester

For de tilknyttede tjenestebelastninger, f.eks. Exchange Online, SharePoint Online og OneDrive for Business, tildeles hver regel en prioritet i den rækkefølge, som den oprettes i. Det betyder, at den regel, der oprettes først, har førsteprioritet, den regel, der blev oprettet som den anden, har en anden prioritet osv. 
  
![Regler i prioritetsrækkefølge](../media/dlp-rules-in-priority-order.png)

Når indhold evalueres i forhold til regler, behandles reglerne i prioritetsrækkefølgen. Hvis indhold matcher flere regler, evalueres den første regel, der har den *mest restriktive* handling. Hvis indhold f.eks. svarer til alle følgende regler, håndhæves regel *3* , fordi det er den højeste, mest restriktive regel:
  
- Regel 1: giver kun brugerne besked
- Regel 2: giver brugerne besked, begrænser adgang og tillader brugertilsidesættelser
- *Regel 3: giver brugere besked, begrænser adgang og tillader ikke, at brugeren tilsidesætter*
- Regel 4: Begrænser adgangen

Regler 1, 2 og 4 evalueres, men anvendes ikke. I dette eksempel registreres match for alle reglerne i overvågningslogfilerne og vises i DLP-rapporterne, selvom kun den mest restriktive regel anvendes.

Du kan bruge en regel til at opfylde et bestemt beskyttelseskrav og derefter bruge en DLP-politik til at samle fælles beskyttelseskrav, f.eks. alle de regler, der er nødvendige for at overholde en bestemt lovgivning.
  
Du kan f.eks. have en DLP-politik, der hjælper dig med at registrere tilstedeværelse af oplysninger, der er underlagt HIPAA (Health Insurance Portability and Accountability Act). Denne DLP-politik kan hjælpe med at beskytte HIPAA-data (hvad) på tværs af alle SharePoint-onlinewebsteder og alle OneDrive for Business-websteder (hvor) ved at finde et dokument, der indeholder disse følsomme oplysninger, som deles med personer uden for organisationen (betingelserne), og derefter blokere adgangen til dokumentet og sende en meddelelse (handlingerne). Disse krav gemmes som individuelle regler og grupperes som en DLP-politik for at forenkle administration og rapportering.
  
![Diagrammet viser, at DLP-politikken indeholder placeringer og regler](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>For slutpunkter

Prioritet for regler på slutpunkter tildeles også i overensstemmelse med den rækkefølge, reglerne er oprettet i. Det betyder, at den regel, der oprettes først, har førsteprioritet, den regel, der blev oprettet som den anden, har en anden prioritet osv. 

Når en fil på et slutpunkt svarer til flere DLP-politikker, er den første regel, der er aktiveret med begrænsninger, den, der håndhæves på indholdet. Hvis indhold f.eks. opfylder alle følgende regler, gennemtvinges regel 2, fordi det er reglen med højeste prioritet, der er konfigureret *med en begrænsning*.
  
- Regel 1: giver kun brugerne besked
- *Regel 2: giver brugerne besked, begrænser adgang og tillader brugertilsidesættelser*
- Regel 3: giver brugere besked, begrænser adgang og tillader ikke, at brugeren tilsidesætter
- Regel 4: Begrænser adgangen

Regler 1, 3 og 4 evalueres, men anvendes ikke. I dette eksempel registreres match for alle reglerne i overvågningslogfilerne og vises i DLP-rapporterne, selvom kun den første regel med en begrænsning anvendes.

For regler, der anvendes på slutpunkter, kan du udnytte muligheden for at ændre rækkefølgen af reglens prioritet for at sikre, at de ønskede begrænsninger anvendes.

### <a name="conditions"></a>Betingelser

Betingelser er inkluderende og er det sted, hvor du definerer, hvad reglen skal søge efter, og den kontekst, hvori disse elementer bruges. De fortæller reglen &#8212;, når du finder et element, der ser sådan her ud, og som bruges *sådan &#8212; er* det et match, og resten af handlingerne i politikken bør blive anvendt på det. Du kan bruge betingelser til at tildele forskellige handlinger til forskellige risikoniveauer. Eksempelvis kan følsomt indhold, der deles internt, være lavere risiko og kræve færre handlinger end følsomt indhold, der deles med personer uden for organisationen.

> [!NOTE]
> Brugere, der har konti uden gæster i en værtsorganisations Active Directory- eller Azure Active Directory-lejer, behandles som personer i organisationen. 

#### <a name="content-contains"></a>Indhold indeholder

 Alle placeringer understøtter indholdet **indeholder** betingelse. Du kan vælge flere forekomster af hver indholdstype og yderligere indskrænke betingelserne ved hjælp af Alle **disse (logiske** ELLER) eller **Alle** disse (logiske OG) operatorer:

- [typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [følsomhedsmærkater](sensitivity-labels.md)
- [opbevaringsetiketter](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

afhængigt af [den eller de placeringer](#location-support-for-how-content-can-be-defined) , du vælger at anvende politikken på. 

Reglen søger kun efter tilstedeværelsen af følsomhedsmærkater **og** opbevaringsetiketter **, du** vælger. 

SIT'er har et foruddefineret [**tillidsniveau, som**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) du kan ændre, hvis det er nødvendigt. Få mere at vide under [Mere om tillidsniveauer](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> SIT'er har to forskellige metoder til at definere parametrene for det maksimale antal entydige forekomster. Du kan få mere at vide under [Forekomstantal understøttede værdier for SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

#### <a name="condition-context"></a>Betingelseskontekst

De tilgængelige kontekstindstillinger ændrer sig, afhængigt af hvilken placering du vælger. Hvis du vælger flere placeringer, er kun de betingelser, som placeringerne har til fælles, tilgængelige.

##### <a name="conditions-exchange-supports"></a>Betingelser, Exchange understøtter

- Indhold indeholder
- Indhold deles fra Microsoft 365
- Indhold modtages fra
- Afsenders IP-adresse er
- Har afsenderen tilsidesat politiktip
- Afsenderen er
- Afsenderdomæne er
- Afsenderadresse indeholder ord
- Afsenderadresse indeholder mønstre
- Attributten Afsender-AD indeholder ord eller udtryk
- Afsenderens AD-attribut matcher mønstre
- Afsenderen er medlem af
- Indholdet af vedhæftede filer i mails kan ikke scannes
- Scanningen af eventuelle vedhæftede filers indhold blev ikke fuldført
- Vedhæftet fil er beskyttet med adgangskode
- Filtypenavnet er
- Modtageren er medlem af
- Modtagerdomæne er
- Modtageren er
- Modtageradresse indeholder ord
- Modtageradresse matcher mønstre
- Modtager-AD-attribut indeholder ord eller udtryk
- Modtagerens AD-attribut matcher mønstre
- Dokumentnavn indeholder ord eller udtryk
- Dokumentnavn matcher mønstre
- Dokumentegenskab er
- Dokumentstørrelse er lig med eller større end
- Dokumentindhold indeholder ord eller udtryk
- Dokumentindhold matcher mønstre
- Emnet indeholder ord eller udtryk
- Emnet matcher mønstre
- Emne eller Brødtekst indeholder ord eller udtryk
- Emne eller brødtekst svarer til mønstre
- Indholdstegnsæt indeholder ord
- Sidehovedet indeholder ord eller udtryk
- Sidehoved matcher mønstre
- Meddelelsesstørrelse er lig med eller større end
- Meddelelsestype er
- Meddelelsens prioritet er

##### <a name="conditions-sharepoint-supports"></a>Betingelser, SharePoint understøtter
 
- Indhold indeholder
- Indhold deles fra Microsoft 365
- Filtypenavnet er
- Dokumentegenskab er

##### <a name="conditions-onedrive-accounts-supports"></a>Betingelser, OneDrive konti understøtter

- Indhold indeholder
- Indhold deles fra Microsoft 365
- Filtypenavnet er
- Dokumentegenskab er

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>Betingelser, Teams chat- og kanalmeddelelser understøtter

- Indhold indeholder
- Indhold deles fra Microsoft 365
- Afsenderen er (eksempel)
- Afsenderdomæne er (forhåndsvisning)
- Modtagerdomæne er (forhåndsvisning)
- Modtageren er (forhåndsvisning)

##### <a name="conditions-devices-supports"></a>Betingelser Enheder understøtter

- Indhold indeholder
- Se [Slutpunktsaktiviteter, du kan overvåge og handle på](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>Betingelser, som Microsoft Defender til skyapps understøtter

- Indhold indeholder
- Indhold deles fra Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>Betingelser i lokale lagre understøtter

- Indhold indeholder
- Filtypenavnet er
- Dokumentegenskab er

##### <a name="conditions-powerbi-supports"></a>Betingelser, som PowerBI understøtter

- Indhold indeholder

#### <a name="condition-groups"></a>Betingelsesgrupper

Nogle gange har du brug for en regel til kun at identificere én ting, f.eks. alt indhold, der indeholder et amerikansk CPR-nummer, som er defineret af et enkelt SIT. Men i mange scenarier, hvor de typer elementer, du forsøger at identificere, er mere komplekse og derfor sværere at definere, kræves der mere fleksibilitet til at definere betingelser.

Hvis du f.eks. vil identificere indhold, der er underlagt DEN amerikanske HEALTH Insurance Act (HIPAA), skal du kigge efter:
  
- Indhold, der indeholder bestemte typer af følsomme oplysninger, f.eks. et amerikansk CPR-nummer eller cpr-nummer.
    
    AND
    
- Indhold, der er sværere at identificere, f.eks. kommunikation om en patients pasning eller beskrivelser af den lægepleje, der gives. Identificering af dette indhold kræver matchende nøgleord fra lister med store nøgleord, f.eks. International klassificering af indhold (ICD-9-CM eller ICD-10-CM).
    
Du kan identificere denne type data ved at gruppere betingelser og bruge logiske operatorer (AND, OR) mellem grupperne.
    
For USA **Health Insurance Act (HIPPA)** grupperes betingelserne sådan her:

![HIPPA-politikbetingelser](../media/dlp-rules-condition-groups-booleans.png)

Den første gruppe indeholder de SIT'er, der identificerer og individuelle, og den anden gruppe indeholder de SIT'er, der identificerer medicinsk diagnose.

### <a name="exceptions"></a>Undtagelser

I regler definerer undtagelser betingelser, der bruges til at udelukke et element fra politikken. Logisk set eksklusive betingelser, der evalueres efter de inkluderende betingelser og konteksten. De fortæller reglen &#8212;, når du finder et element, der ser således ud,  og som bruges sådan, at  det er et match, og resten af handlingerne i politikken bør anvendes på det, undtagen ***hvis ... &#8212;*** 

I tråd med HIPPA-politikken kan vi f.eks. ændre reglen, så et element, der indeholder et Belgien-kørekortnummer, udelades, således:

![HIPPA-politik med udeladelse](../media/dlp-rule-exceptions.png)

De undtagelser, der understøttes af placering, er identiske med alle inklusionsbetingelserne, hvor den eneste forskel er den foreløbige af "Undtagen hvis" for hver understøttet betingelse. Hvis en regel kun indeholder undtagelser, gælder den for alle mails eller filer, der ikke opfylder udelukkelseskriterierne.

På samme måde som alle placeringer understøtter den inkluderende betingelse:

- Indhold indeholder

undtagelsen ville være:

- **Undtagen hvis indhold** indeholder 

### <a name="actions"></a>Handlinger 

Ethvert element, der gør det gennem de inkluderende ***betingelser** _ _**_ og eksklusive undtagelser, vil _**_ have de handlinger, der er defineret i den regel, der anvendes på det. Du skal konfigurere de påkrævede indstillinger for at understøtte handlingen. Hvis du f.eks. vælger Exchange med handlingen _ *Begræns adgang eller kryptere indholdet i Microsoft 365-placeringer**, skal du vælge mellem disse indstillinger:

- Bloker brugere i at få adgang til SharePoint, OneDrive og Teams indhold
    - Bloker alle. Kun ejeren af indholdet, den sidste ændring og webstedsadministratoren vil fortsat have adgang
    - Bloker kun personer uden for organisationen. Brugere inden for organisationen vil fortsat have adgang.
- Kryptér mails (gælder kun for indhold i Exchange)

De handlinger, der er tilgængelige i en regel, afhænger af de placeringer, der er markeret. Hvis du kun vælger én placering, som politikken skal anvendes på, vises de tilgængelige handlinger nedenfor.

> [!IMPORTANT]
> For SharePoint Online- og OneDrive for Business-placeringer blokeres dokumenter proaktivt lige efter registrering af følsomme oplysninger, uanset om dokumentet er delt eller ej, for alle eksterne brugere, mens interne brugere fortsat har adgang til dokumentet.

#### <a name="exchange-location-actions"></a>Exchange placeringshandlinger

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer
- Angive sidehoveder
- Fjern sidehoved
- Omdiriger meddelelsen til bestemte brugere
- Videresende meddelelsen til godkendelse til afsenderens leder
- Videresende meddelelsen til godkendelse til bestemte godkendere
- Føj modtager til feltet Til
- Føj modtager til feltet Cc
- Føj modtager til feltet Bcc
- Tilføj afsenderens overordnede som modtager
- O365-meddelelseskryptering og rettighedsbeskyttelse er blevet fjernet
- Forudindstillet mail-emne
- Rediger mailens emne
- Tilføj HTML-ansvarsfraskrivelse

#### <a name="sharepoint-sites-location-actions"></a>SharePoint handlinger for placering af websteder

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer

#### <a name="onedrive-account-location-actions"></a>OneDrive handlinger for kontoplacering

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer

#### <a name="teams-chat-and-channel-messages-actions"></a>Teams for chat og kanalmeddelelser

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer

#### <a name="devices-actions"></a>Enheders handlinger

- Overvågning eller begræns aktiviteter på Windows enheder

> [!NOTE]
> Enheder giver mulighed for at **Overvåge** en aktivitet, **Blokere** en aktivitet eller Blokere **med tilsidesættelse af** en aktivitet.

Placeringen af enhederne indeholder mange underaktiver (betingelser) og handlinger. Du kan få mere at vide [under Slutpunktsaktiviteter, du kan overvåge og handle på](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on). 

#### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender til skyapps

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer
- Begræns tredjepartsapps

#### <a name="on-premises-repositories"></a>Lokale lagre

- Begræns adgang eller fjern lokale filer

#### <a name="powerbi-actions"></a>PowerBI-handlinger

- Giv brugere besked med mail og politiktip
- Send beskeder til administrator

#### <a name="actions-available-when-you-combine-locations"></a>Handlinger, der er tilgængelige, når du kombinerer placeringer

Hvis du vælger Exchange og en anden enkelt placering for politikken, der skal anvendes på, vil

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer

og

- Alle handlinger for den ikke-Exchange placering

handlinger vil være tilgængelige.

Hvis du vælger to eller flere ikke-Exchange placeringer, som politikken skal anvendes på, vil

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer

AND

- Alle handlinger for ikke-Exchange placeringer 

handlinger vil være tilgængelige.

Hvis du f.eks. Exchange enheder som placeringer, vil disse handlinger være tilgængelige:

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer
- Overvågning eller begræns aktiviteter på Windows enheder

Hvis du vælger Enheder og Microsoft Defender til skyapps, vil disse handlinger være tilgængelige:

- Begræns adgang, eller kryptér indholdet Microsoft 365 placeringer
- Overvågning eller begræns aktiviteter på Windows enheder
- Begræns tredjepartsapps

Om en handling træder i kraft eller ej, afhænger af, hvordan du konfigurerer politikkens tilstand. Du kan vælge at køre politikken i testtilstand med eller uden at vise politiktip ved at **vælge indstillingen Test det først** . Du vælger at køre politikken så snart som en time efter, den er oprettet, ved at vælge  indstillingen Slå den til med det samme, eller du kan vælge blot at gemme den og vende tilbage til den senere ved at vælge **indstillingen** Slå den fra. 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>Tip til brugerbeskeder og politikker

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

Når en bruger forsøger en handling på et følsomt element i en kontekst, der opfylder betingelserne og undtagelserne for en regel, kan du fortælle vedkommende om det via mail om brugerbeskeder og i pop op-vindue med kontekstpolitiktip. Disse meddelelser er nyttige, fordi de øger folks opmærksomhed og hjælper med at informere personer om organisationens DLP-politikker.

Indhold som f.eks. Excel projektmappe på et OneDrive for Business websted, der indeholder personlige id-oplysninger (PII), og som deles med en gæst.

![Meddelelseslinjen viser politiktip i Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!NOTE]
> Meddelelsesmails sendes ubeskyttet.

Du kan også give personer mulighed for at tilsidesætte [politikken, så](#user-overrides) de ikke blokeres, hvis de har et gyldigt forretnings behov, eller hvis politikken registrerer en falsk positiv.

Konfigurationsindstillingerne for brugerbeskeder og politiktip varierer afhængigt af de overvågningsplaceringer, du har valgt. Hvis du har valgt:

- Exchange
- SharePoint
- OneDrive
- Teams chat og kanal
- Defender til skyapps


Du kan aktivere/deaktivere brugerbeskeder for forskellige Microsoft-apps under Reference [til politiktip til forebyggelse af datatab](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- Du kan aktivere/deaktivere **Underrette brugere i Office 365 med** et politiktip.
    - mailbeskeder til den bruger, der har sendt, delt eller senest ændret indholdet ELLER
    - underrette bestemte personer

og tilpasse mailteksten, emnet og politiktipteksten.

![Konfigurationsindstillinger for brugerbeskeder og politiktip, der er tilgængelige for Exchange, SharePoint, OneDrive, Teams Chat og Kanal og Defender til skyapps](../media/dlp-user-notification-non-devices.png)

Hvis du valgte Kun enheder, får du alle de samme indstillinger, der er tilgængelige for Exchange, SharePoint, OneDrive, Teams Chat og Kanal og Defender til skyapps samt muligheden for at tilpasse meddelelsens titel og indhold, der vises på Windows 10-enheden.

![Konfigurationsindstillinger for brugerbeskeder og politiktip, der er tilgængelige for enheder](../media/dlp-user-notification-devices.png)  

Du kan tilpasse titlen og brødteksten ved hjælp af disse parametre. Brødteksten understøtter følgende:

|Almindeligt navn  |Parameter  |Eksempel
|---------|---------|---------|
|filnavn     |%%FileName%% | Contoso doc 1 |
|procesnavn     |%%ProcessName%% | Word |
|politiknavn     |%%PolicyName%%| Contoso meget fortrolig |
|handling | %%AppliedActions%% | Indsætte dokumentindhold fra Udklipsholder i en anden app |

**%%AppliedActions%%** erstatter disse værdier i meddelelsesteksten:


|almindeligt handlingsnavn |værdi erstattet af %%AppliedActions%%-parameteren |
|---------|---------|
|kopiér til lager, der kan fjernes    |*skrivning til flytbart lager*         |
|kopiér til netværksshare     |*skrive til et netværksshare*         |
|udskriv     |*udskrivning*         |
|Indsæt fra Udklipsholder  |*Indsætte fra Udklipsholder*         |
|kopiér via bluetooth   |*overførsel via Bluetooth*         |
|åbn med en app, der ikke er tilladt     |*åbne med denne app*         |
|kopiér til en fjernskrivebord (RDP)     |*overførsel til fjernskrivebord*         |
|overførsel til et websted, der ikke er tilladt     |*uploader til dette websted*         |
|få adgang til elementet via en ikke-tilladt browser     |*åbne med denne browser*         |

Brug af denne brugerdefinerede tekst

*%%AppliedActions%% Filnavn %%FileName%% via %%ProcessName%% er ikke tilladt af din organisation. Klik på "Tillad", hvis du vil springe politikken %%PolicyName%% over* 

producerer denne tekst i den tilpassede meddelelse:

*indsætte fra udklipsholderens filnavn: Contoso-dokument 1 via WINWORD.EXE er ikke tilladt af din organisation. Klik på knappen "Tillad", hvis du vil tilsidesætte politikken Contoso meget fortrolig*
 

> [!NOTE]
> Brugerbeskeder og politiktip er ikke tilgængelige for placeringen i det lokale miljø

> [!NOTE]
> Kun politiktip fra den højeste, mest restriktive regel vises. Eksempelvis vises et politiktip fra en regel, der blokerer adgang til indhold, over et politiktip fra en regel, der blot sender en meddelelse. Dette forhindrer brugere i at se en kaskade af politiktip.

Hvis du vil have mere at vide om konfiguration og brug af politiktip, herunder hvordan du tilpasser meddelelsen og tipteksten, skal du se 
- [Send mailbeskeder, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
<!--The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.
  
In addition to sending an email notification, a user notification displays a policy tip:
  
- In Outlook and Outlook on the web.
    
- For the document on a SharePoint Online or OneDrive for Business site.
    
- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.
    
The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.
  
Here's what a policy tip looks like in a OneDrive for Business account.
  
![Policy tip for a document in a OneDrive account](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.
-->

### <a name="user-overrides"></a>Bruger tilsidesætter

Formålet med brugerens  tilsidesættelse er at give brugerne en metode til at tilsidesætte, med begrundelse, DLP-politikblokeringshandlinger for følsomme elementer i Exchange, SharePoint, OneDrive eller Teams, så de kan fortsætte deres arbejde. Brugertilsidesættelser aktiveres kun, når Giv brugere besked i **Office 365-tjenester** med et politiktip er aktiveret, så brugertilsidesættelser går hånd i hånd med tip til meddelelser og politikker. 

![Indstillinger for brugertilsidesættelse for en DLP-politik](../media/dlp-user-overrides.png)

> [!NOTE]
> Brugertilsidesættelser er ikke tilgængelige for placeringen af det lokale lager.

Brugertilsidesættelser er typisk nyttige, når organisationen først udruller en politik. Den feedback, du får fra eventuelle tilsidesættelsesberettigelser og identificerer falske positive, hjælper med at justere politikken. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- Hvis politiktip i den mest restriktive regel tillader brugere at tilsidesætte reglen, tilsidesætter tilsidesættelsen af denne regel også andre regler, som indholdet har matchet.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
Du kan få mere at vide om brugertilsidesættelser under:

- [Få vist den begrundelse, der er indsendt af en bruger for en tilsidesættelse](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>Hændelsesrapporter

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

Når en regel matches, kan du sende en hændelsesrapport til din compliance officer (eller personer, du vælger) med oplysninger om begivenheden. Rapporten indeholder oplysninger om det element, der blev matchet, det faktiske indhold, der matchede reglen, og navnet på den person, der senest har ændret indholdet. For mails indeholder rapporten også som en vedhæftet fil den oprindelige meddelelse, der svarer til en DLP-politik.

Oplysninger om DLP-feeds med andre Microsoft 365 inden for beskyttelse af oplysninger, f.eks. [Insider Risk management Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365). For at få oplysninger om hændelser til Insider Risk Management skal du angive alvorsniveauet **for hændelsesrapporter** til **Høj**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

Beskeder kan sendes, hver gang en aktivitet svarer til en regel, som kan være støjende, eller de kan aggregeres til færre beskeder baseret på antallet af matches eller mængden af elementer i en bestemt tidsperiode.

![send en besked, hver gang en regel stemmer overens med eller sammenlægges over tid, i færre rapporter](../media/dlp-incident-reports-aggregation.png)

DLP scanner mails anderledes, end det gør SharePoint Online eller OneDrive for Business elementer. I SharePoint Online og OneDrive for Business scanner DLP eksisterende elementer samt nye og genererer en hændelsesrapport, når der findes et match. I Exchange Online scanner DLP kun nye mails og genererer en rapport, hvis der er et match for politikken. DLP ***scanner eller matcher*** ikke tidligere eksisterende mailelementer, der er gemt i en postkasse eller et arkiv.

### <a name="additional-options"></a>Yderligere indstillinger

Hvis du har flere regler i en politik, kan du bruge flere  indstillinger til at styre den videre behandling af regler, hvis der er et match til den regel, du redigerer, samt angive prioriteten for evaluering af reglen.

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
