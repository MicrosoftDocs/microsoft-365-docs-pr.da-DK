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
description: DLP-politikkomponent og konfigurationsreference
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: ac809f5a976da1d6c83d36f24e93c3aacd997850
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66882011"
---
# <a name="data-loss-prevention-policy-reference"></a>Reference til politik til forebyggelse af datatab

Microsoft Purview Forebyggelse af datatab politikker (DLP) har mange komponenter at konfigurere. Hvis du vil oprette en effektiv politik, skal du forstå, hvad formålet med hver komponent er, og hvordan dens konfiguration ændrer politikkens funktionsmåde. Denne artikel indeholder en detaljeret beskrivelse af en DLP-politik.

## <a name="policy-templates"></a>Politikskabeloner 

DLP-politikskabeloner er forudsorteret i fire kategorier:

- Dem, der kan registrere og beskytte typer af **finansielle** oplysninger.
- Dem, der kan opdage og beskytte typer af **medicinsk og sundhedsoplysninger** .
- Dem, der kan registrere og beskytte typer af **oplysninger om beskyttelse af personlige oplysninger** .
- En **brugerdefineret** skabelon, som du kan bruge til at oprette din egen politik, hvis en af de andre ikke opfylder dine organisations behov.

I denne tabel vises alle politikskabeloner og de følsomme informationstyper (SIT), som de dækker. 

opdateret: 23-06-2021

|Kategori| Skabelon | SIDDE |
|---------|---------|---------|
|Finansielle| Økonomiske data i Australien| - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Australiens skattefilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Australiens bankkontonummer](sensitive-information-type-entity-definitions.md#australia-bank-account-number) </br> - [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansielle| Finansielle data for Canada |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Canadas bankkontonummer](sensitive-information-type-entity-definitions.md#canada-bank-account-number)|
|Finansielle| Frankrig Finansielle data |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [EU-betalingskortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansielle| Finansielle data for Tyskland |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [EU-betalingskortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number)|
|Finansielle| Økonomiske data for Israel |- [Israels bankkontonummer](sensitive-information-type-entity-definitions.md#israel-bank-account-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansielle| Økonomiske data for Japan |- [Japans bankkontonummer](sensitive-information-type-entity-definitions.md#japan-bank-account-number) </br> - [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansielle| PCI Data Security Standard (PCI DSS)|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number)|
|Finansielle| Saudi-Arabiens lov om bekæmpelse af cyberkriminalitet|- [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Internationalt bankkontonummer (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban) |
|Finansielle| Saudi-Arabiens finansielle data |- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code) </br> - [Internationalt bankkontonummer (IBAN)](sensitive-information-type-entity-definitions.md#international-banking-account-number-iban)|
|Finansielle| Finansielle data for Storbritannien|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [EU-betalingskortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Finansielle| Finansielle data for USA|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA-routingnummer](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansielle| FTC-forbrugerregler (U.S. Federal Trade Commission)|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [ABA-routingnummer](sensitive-information-type-entity-definitions.md#aba-routing-number)|
|Finansielle| U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Id-nummer for individuelle amerikanske skatteborgere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Amerikansk/britisk pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> -[Amerikansk kørekortsnummer](sensitive-information-type-entity-definitions.md#us-drivers-license-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Finansielle| U.S. Gramm-Leach-Bliley Act (GLBA)|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Id-nummer for individuelle amerikanske skatteborgere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Medicinsk og sundhed| Australia Health Records Act (HRIP Act) Enhanced |- [Australiens skattefilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Medicinsk kontonummer i Australien](sensitive-information-type-entity-definitions.md#australia-medical-account-number) </br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Fysiske adresser i Australien](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Medicinsk og sundhed| Australia Health Records Act (HRIP Act)|- [Australiens skattefilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Medicinsk kontonummer i Australien](sensitive-information-type-entity-definitions.md#australia-medical-account-number)|
|Medicinsk og sundhed| Canada Health Information Act (HIA) |- [Pasnummer til Canada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada socialforsikringsnummer](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Nummer på sundhedstjenesten i Canada](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canadas personidentifikationsnummer](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medicinsk og sundhed| Canada Personal Health Information Act (PHIA) Manitoba|- [Canada socialforsikringsnummer](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Nummer på sundhedstjenesten i Canada](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canadas personidentifikationsnummer](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medicinsk og sundhed| Canada Personal Health Act (PHIPA) Ontario |- [Pasnummer til Canada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada socialforsikringsnummer](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Nummer på sundhedstjenesten i Canada](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canadas personidentifikationsnummer](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Medicinsk og sundhed| STORBRITANNIEN. Lov om adgang til lægerapporter|- [Det britiske nationale sundhedstjenestenummer](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [Det britiske nationalforsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino)|
|Medicinsk og sundhed| HIPAA (U.S. Health Insurance Act) Enhanced|</br> - [International klassificering af sygdomme (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [International klassificering af sygdomme (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm) </br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Medicinsk og sundhed| HIPAA (U.S. Health Insurance Act)| - [International klassificering af sygdomme (ICD-9-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-9-cm) </br> - [International klassificering af sygdomme (ICD-10-CM)](sensitive-information-type-entity-definitions.md#international-classification-of-diseases-icd-10-cm)|
|Beskyttelse af personlige oplysninger| Udvidet lov om beskyttelse af personlige oplysninger i Australien|- [Australiens kørekortsnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Australiens pasnummer](sensitive-information-type-entity-definitions.md#australia-passport-number) </br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions) </br> - [Fysiske adresser i Australien](sensitive-information-type-entity-definitions.md#australia-physical-addresses)|
|Beskyttelse af personlige oplysninger| Australiens lov om beskyttelse af personlige oplysninger|- [Australiens kørekortsnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) </br> - [Australiens pasnummer](sensitive-information-type-entity-definitions.md#australia-passport-number)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger i Australien|- [Australiens skattefilnummer](sensitive-information-type-entity-definitions.md#australia-tax-file-number) </br> - [Australiens kørekortsnummer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger om Canada|- [Canadas kørekortsnummer](sensitive-information-type-entity-definitions.md#canada-drivers-license-number)</br> - [Canadas bankkontonummer](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Pasnummer til Canada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada socialforsikringsnummer](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Nummer på sundhedstjenesten i Canada](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canadas personidentifikationsnummer](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Beskyttelse af personlige oplysninger| PIPA (Canada Personal Information Protection Act)|- [Pasnummer til Canada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada socialforsikringsnummer](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Nummer på sundhedstjenesten i Canada](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canadas personidentifikationsnummer](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Beskyttelse af personlige oplysninger| Pipeda (Canada Personal Information Protection Act)|- [Canadas kørekortsnummer](sensitive-information-type-entity-definitions.md#canada-drivers-license-number) </br> - [Canadas bankkontonummer](sensitive-information-type-entity-definitions.md#canada-bank-account-number) </br> - [Pasnummer til Canada](sensitive-information-type-entity-definitions.md#canada-passport-number)</br> - [Canada socialforsikringsnummer](sensitive-information-type-entity-definitions.md#canada-social-insurance-number) </br> - [Nummer på sundhedstjenesten i Canada](sensitive-information-type-entity-definitions.md#canada-health-service-number) </br> - [Canadas personidentifikationsnummer](sensitive-information-type-entity-definitions.md#canada-personal-health-identification-number-phin)|
|Beskyttelse af personlige oplysninger| Den franske lov om databeskyttelse|- [Nationalt id-kort for Frankrig (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni) </br> - [Det sociale sikringsnummer i Frankrig (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger i Frankrig|- [Det sociale sikringsnummer i Frankrig (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee) </br> - [Frankrigs kørekortsnummer](sensitive-information-type-entity-definitions.md#france-drivers-license-number) </br> - [Pasnummer for Frankrig](sensitive-information-type-entity-definitions.md#france-passport-number) </br> - [Nationalt id-kort for Frankrig (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)|
|Beskyttelse af personlige oplysninger| Generel forordning om databeskyttelse (GDPR) forbedret|- [Fysiske adresser i Østrig](sensitive-information-type-entity-definitions.md#austria-physical-addresses) </br> - [Fysiske adresser for Belgien](sensitive-information-type-entity-definitions.md#belgium-physical-addresses)</br> - [Fysiske adresser for Bulgarien](sensitive-information-type-entity-definitions.md#bulgaria-physical-addresses)</br> - [Fysiske adresser for Kroatien](sensitive-information-type-entity-definitions.md#croatia-physical-addresses)</br> - [Fysiske adresser for Cypern](sensitive-information-type-entity-definitions.md#cyprus-physical-addresses)</br> - [Fysiske adresser for Tjekkiet](sensitive-information-type-entity-definitions.md#czech-republic-physical-addresses)</br> - [Fysiske adresser i Danmark](sensitive-information-type-entity-definitions.md#denmark-physical-addresses)</br> - [Fysiske adresser i Estland](sensitive-information-type-entity-definitions.md#estonia-physical-addresses)</br> - [Fysiske adresser for Finland](sensitive-information-type-entity-definitions.md#finland-physical-addresses)</br> - [Fysiske adresser i Frankrig](sensitive-information-type-entity-definitions.md#france-physical-addresses)</br> - [Fysiske adresser i Tyskland](sensitive-information-type-entity-definitions.md#germany-physical-addresses)</br> - [Fysiske adresser for Grækenland](sensitive-information-type-entity-definitions.md#greece-physical-addresses)</br> - [Fysiske adresser til Ungarn](sensitive-information-type-entity-definitions.md#hungary-physical-addresses)</br> - [Fysiske adresser for Irland](sensitive-information-type-entity-definitions.md#ireland-physical-addresses)</br> - [Fysiske adresser for Italien](sensitive-information-type-entity-definitions.md#italy-physical-addresses)</br> - [Fysiske adresser i Letland](sensitive-information-type-entity-definitions.md#latvia-physical-addresses)</br> - [Fysiske adresser for Litauen](sensitive-information-type-entity-definitions.md#lithuania-physical-addresses)</br> - [Fysiske adresser i Luxembourg](sensitive-information-type-entity-definitions.md#luxemburg-physical-addresses)</br> - [Fysiske adresser på Malta](sensitive-information-type-entity-definitions.md#malta-physical-addresses)</br> - [Fysiske adresser i Nederlandene](sensitive-information-type-entity-definitions.md#netherlands-physical-addresses)</br> - [Fysiske adresser i Polen](sensitive-information-type-entity-definitions.md#poland-physical-addresses)</br> - [Portugisiske fysiske adresser](sensitive-information-type-entity-definitions.md#portugal-physical-addresses)</br> - [Fysiske adresser i Rumænien](sensitive-information-type-entity-definitions.md#romania-physical-addresses)</br> - [Fysiske adresser i Slovakiet](sensitive-information-type-entity-definitions.md#slovakia-physical-addresses)</br> - [Fysiske adresser i Slovenien](sensitive-information-type-entity-definitions.md#slovenia-physical-addresses)</br> - [Fysiske adresser i Spanien](sensitive-information-type-entity-definitions.md#spain-physical-addresses)</br> - [Fysiske adresser i Sverige](sensitive-information-type-entity-definitions.md#sweden-physical-addresses)</br> - [Det østrigske cpr-nummer](sensitive-information-type-entity-definitions.md#austria-social-security-number)</br> - [Det franske cpr-nummer (INSEE)](sensitive-information-type-entity-definitions.md#france-social-security-number-insee)</br> - [Det græske cpr-nummer (AMKA)](sensitive-information-type-entity-definitions.md#greece-social-security-number-amka)</br> - [Ungarsk cpr-nummer (TAJ)](sensitive-information-type-entity-definitions.md#hungary-social-security-number-taj)</br> - [Spanien Cpr-nummer (SSN)](sensitive-information-type-entity-definitions.md#spain-social-security-number-ssn)</br> - [Østrigs identitetskort](sensitive-information-type-entity-definitions.md#austria-identity-card)</br> - [Cyperns identitetskort](sensitive-information-type-entity-definitions.md#cyprus-identity-card)</br> - [Tysklands identitetskortnummer](sensitive-information-type-entity-definitions.md#germany-identity-card-number)</br> - [Maltas identitetskortnummer](sensitive-information-type-entity-definitions.md#malta-identity-card-number)</br> - [Nationalt id-kort for Frankrig (CNI)](sensitive-information-type-entity-definitions.md#france-national-id-card-cni)</br> - [Nationalt id-kort for Grækenland](sensitive-information-type-entity-definitions.md#greece-national-id-card)</br> - [Finlands nationale id](sensitive-information-type-entity-definitions.md#finland-national-id)</br> - [Nationalt id for Polen (PESEL)](sensitive-information-type-entity-definitions.md#poland-national-id-pesel)</br> - [Nationalt id for Sverige](sensitive-information-type-entity-definitions.md#sweden-national-id)</br> - [Personidentifikationsnummer for Kroatien (OIB)](sensitive-information-type-entity-definitions.md#croatia-personal-identification-oib-number)</br> - [Tjekkisk personligt id-nummer](sensitive-information-type-entity-definitions.md#czech-personal-identity-number)</br> - [Danmark Personidentifikationsnummer](sensitive-information-type-entity-definitions.md#denmark-personal-identification-number)</br> - [Personidentifikationskode for Estland](sensitive-information-type-entity-definitions.md#estonia-personal-identification-code)</br> - [Ungarns personidentifikationsnummer](sensitive-information-type-entity-definitions.md#hungary-personal-identification-number)</br> - [Luxembourgs nationale identifikationsnummer (fysiske personer)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-natural-persons)</br> - [Luxembourgs nationale identifikationsnummer (ikke-fysiske personer)](sensitive-information-type-entity-definitions.md#luxemburg-national-identification-number-non-natural-persons)</br> - [Italiens regnskabskode](sensitive-information-type-entity-definitions.md#italy-fiscal-code)</br> - [Letlands personlige kodeks](sensitive-information-type-entity-definitions.md#latvia-personal-code)</br> - [Litauens personlige kode](sensitive-information-type-entity-definitions.md#lithuania-personal-code)</br> - [Rumæniens personlige numeriske kode (CNP)](sensitive-information-type-entity-definitions.md#romania-personal-numeric-code-cnp)</br> - [BSN-nummer (Netherlands Citizen's Service)](sensitive-information-type-entity-definitions.md#netherlands-citizens-service-bsn-number)</br> - [Irlands personlige offentlige tjeneste (PPS)-nummer](sensitive-information-type-entity-definitions.md#ireland-personal-public-service-pps-number)</br> - [Bulgariens ensartede civilnummer](sensitive-information-type-entity-definitions.md#bulgaria-uniform-civil-number)</br> - [Belgiens nationale nummer](sensitive-information-type-entity-definitions.md#belgium-national-number)</br> - [Spanien DNI](sensitive-information-type-entity-definitions.md#spain-dni)</br> - [Sloveniens entydige masterborgernummer](sensitive-information-type-entity-definitions.md#slovenia-unique-master-citizen-number)</br> - [Slovakiets personlige nummer](sensitive-information-type-entity-definitions.md#slovakia-personal-number)</br> - [Nummer på portugals borgerkort](sensitive-information-type-entity-definitions.md#portugal-citizen-card-number)</br> - [Maltas skatte-id-nummer](sensitive-information-type-entity-definitions.md#malta-tax-identification-number)</br> - [Østrigs skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#austria-tax-identification-number)</br> - [Cyperns skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#cyprus-tax-identification-number)</br> - [Frankrigs skatteidentifikationsnummer (numéro SPI.)](sensitive-information-type-entity-definitions.md#france-tax-identification-number)</br> - [Tysklands skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#germany-tax-identification-number)</br> - [Græsk skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#greece-tax-identification-number)</br> - [Ungarn Skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#hungary-tax-identification-number)</br> - [Nederlandsk skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#netherlands-tax-identification-number)</br> - [Polens skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#poland-tax-identification-number)</br> - [Portugals skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#portugal-tax-identification-number)</br> - [Sloveniens skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#slovenia-tax-identification-number)</br> - [Spaniens skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#spain-tax-identification-number)</br> - [Sveriges skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#sweden-tax-identification-number)</br> - [Østrigs kørekort](sensitive-information-type-entity-definitions.md#austria-drivers-license-number)</br> - [Belgiens kørekortsnummer](sensitive-information-type-entity-definitions.md#belgium-drivers-license-number)</br> - [Bulgariens kørekortsnummer](sensitive-information-type-entity-definitions.md#bulgaria-drivers-license-number)</br> - [Kroatiens kørekortsnummer](sensitive-information-type-entity-definitions.md#croatia-drivers-license-number)</br> - [Cyperns kørekortsnummer](sensitive-information-type-entity-definitions.md#cyprus-drivers-license-number)</br> - [Tjekkisk kørekortsnummer](sensitive-information-type-entity-definitions.md#czech-drivers-license-number)</br> - [Danmarks kørekortsnummer](sensitive-information-type-entity-definitions.md#denmark-drivers-license-number)</br> - [Estlands kørekortsnummer](sensitive-information-type-entity-definitions.md#estonia-drivers-license-number)</br> - [Finlands kørekortsnummer](sensitive-information-type-entity-definitions.md#finland-drivers-license-number)</br> - [Frankrigs kørekortsnummer](sensitive-information-type-entity-definitions.md#france-drivers-license-number)</br> - [Tysk kørekortsnummer](sensitive-information-type-entity-definitions.md#germany-drivers-license-number)</br> - [Grækenlands kørekortsnummer](sensitive-information-type-entity-definitions.md#greece-drivers-license-number)</br> - [Ungarns kørekortsnummer](sensitive-information-type-entity-definitions.md#hungary-drivers-license-number)</br> - [Irlands kørekortsnummer](sensitive-information-type-entity-definitions.md#ireland-drivers-license-number)</br> - [Italiens kørekortsnummer](sensitive-information-type-entity-definitions.md#italy-drivers-license-number)</br> - [Letlands kørekortsnummer](sensitive-information-type-entity-definitions.md#latvia-drivers-license-number)</br> - [Litauens kørekortsnummer](sensitive-information-type-entity-definitions.md#lithuania-drivers-license-number)</br> - [Luxemburg-kørekortsnummer](sensitive-information-type-entity-definitions.md#luxemburg-drivers-license-number)</br> - [Maltas kørekortsnummer](sensitive-information-type-entity-definitions.md#malta-drivers-license-number)</br> - [Nederlandsk kørekortsnummer](sensitive-information-type-entity-definitions.md#netherlands-drivers-license-number)</br> - [Polens kørekortsnummer](sensitive-information-type-entity-definitions.md#poland-drivers-license-number)</br> - [Portugals kørekortsnummer](sensitive-information-type-entity-definitions.md#portugal-drivers-license-number)</br> - [Rumæniens kørekortsnummer](sensitive-information-type-entity-definitions.md#romania-drivers-license-number)</br> - [Slovakiets kørekortsnummer](sensitive-information-type-entity-definitions.md#slovakia-drivers-license-number)</br> - [Sloveniens kørekortsnummer](sensitive-information-type-entity-definitions.md#slovenia-drivers-license-number)</br> - [Spaniens kørekortsnummer](sensitive-information-type-entity-definitions.md#spain-drivers-license-number)</br> - [Sveriges kørekortsnummer](sensitive-information-type-entity-definitions.md#sweden-drivers-license-number)</br> - [Pasnummer for Østrig](sensitive-information-type-entity-definitions.md#austria-passport-number)</br> - [Belgien Passport-nummer](sensitive-information-type-entity-definitions.md#belgium-passport-number)</br> - [Bulgariens pasnummer](sensitive-information-type-entity-definitions.md#bulgaria-passport-number)</br> - [Kroatiens pasnummer](sensitive-information-type-entity-definitions.md#croatia-passport-number)</br> - [Cyperns pasnummer](sensitive-information-type-entity-definitions.md#cyprus-passport-number)</br> - [Pasnummer for Tjekkiet](sensitive-information-type-entity-definitions.md#czech-passport-number)</br> - [Danmark Passport-nummer](sensitive-information-type-entity-definitions.md#denmark-passport-number)</br> - [Estisk pasnummer](sensitive-information-type-entity-definitions.md#estonia-passport-number)</br> - [Finlands pasnummer](sensitive-information-type-entity-definitions.md#finland-passport-number)</br> - [France Passport-nummer](sensitive-information-type-entity-definitions.md#france-passport-number)</br> - [Tysk pasnummer](sensitive-information-type-entity-definitions.md#germany-passport-number)</br> - [Grækenlands pasnummer](sensitive-information-type-entity-definitions.md#greece-passport-number)</br> - [Ungarn Pasnummer](sensitive-information-type-entity-definitions.md#hungary-passport-number)</br> - [Irlands pasnummer](sensitive-information-type-entity-definitions.md#ireland-passport-number)</br> - [Pasnummer til Italien](sensitive-information-type-entity-definitions.md#italy-passport-number)</br> - [Letlands pasnummer](sensitive-information-type-entity-definitions.md#latvia-passport-number)</br> - [Litauens pasnummer](sensitive-information-type-entity-definitions.md#lithuania-passport-number)</br> - [Luxemburg Passport-nummer](sensitive-information-type-entity-definitions.md#luxemburg-passport-number)</br> - [Maltas pasnummer](sensitive-information-type-entity-definitions.md#malta-passport-number)</br> - [Nederlandsk pasnummer](sensitive-information-type-entity-definitions.md#netherlands-passport-number)</br> - [Polens pas](sensitive-information-type-entity-definitions.md#poland-passport-number)</br> - [Pasnummer til Portugal](sensitive-information-type-entity-definitions.md#portugal-passport-number)</br> - [Rumænien Passport-nummer](sensitive-information-type-entity-definitions.md#romania-passport-number)</br> - [Slovakiets pasnummer](sensitive-information-type-entity-definitions.md#slovakia-passport-number)</br> - [Sloveniens pasnummer](sensitive-information-type-entity-definitions.md#slovenia-passport-number)</br> - [Spaniens pasnummer](sensitive-information-type-entity-definitions.md#spain-passport-number)</br> - [Sveriges pasnummer](sensitive-information-type-entity-definitions.md#sweden-passport-number)</br> - [EU-debetkortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)|
|Beskyttelse af personlige oplysninger| Generel forordning om databeskyttelse (GDPR)|- [EU-betalingskortnummer](sensitive-information-type-entity-definitions.md#eu-debit-card-number) </br> - [EU-kørekortsnummer](sensitive-information-type-entity-definitions.md#eu-drivers-license-number) </br> - [EU-nationalt identifikationsnummer](sensitive-information-type-entity-definitions.md#eu-national-identification-number)</br> - [EU-pasnummer](sensitive-information-type-entity-definitions.md#eu-passport-number) </br> - [EU-cpr-nummer eller tilsvarende identifikation](sensitive-information-type-entity-definitions.md#eu-social-security-number-or-equivalent-identification)</br> - [EU-skatteidentifikationsnummer](sensitive-information-type-entity-definitions.md#eu-tax-identification-number)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger i Tyskland|- [Tysklands kørekortsnummer](sensitive-information-type-entity-definitions.md#germany-drivers-license-number) </br> - [Tysklands pasnummer](sensitive-information-type-entity-definitions.md#germany-passport-number)| 
|Beskyttelse af personlige oplysninger| Personidentificerbare israelsk-oplysninger|- [Israels nationale identifikationsnummer](sensitive-information-type-entity-definitions.md#israel-national-identification-number)| 
|Beskyttelse af personlige oplysninger| Israel beskyttelse af privatlivets fred|- [Israels nationale identifikationsnummer](sensitive-information-type-entity-definitions.md#israel-national-identification-number)</br> - [Israels bankkontonummer](sensitive-information-type-entity-definitions.md#israel-bank-account-number)|
|Beskyttelse af personlige oplysninger| Forbedrede pii-data (Personligt identificerbare oplysninger) i Japan|- [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)</br> - [Japan Mit nummer - personlig](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Pasnummer til Japan](sensitive-information-type-entity-definitions.md#japan-passport-number)</br> - [Japans kørekortsnummer](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Fysiske adresser i Japan](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Beskyttelse af personlige oplysninger| Personidentificerbare oplysninger i Japan|- [Registreringsnummer for beboere i Japan](sensitive-information-type-entity-definitions.md#japan-resident-registration-number) </br> - [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Beskyttelse af personlige oplysninger| Forbedret beskyttelse af personlige oplysninger i Japan|- [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin) </br> - [Japan Mit nummer - personlig](sensitive-information-type-entity-definitions.md#japan-my-number---personal)</br> - [Pasnummer til Japan](sensitive-information-type-entity-definitions.md#japan-passport-number) </br> - [Japans kørekortsnummer](sensitive-information-type-entity-definitions.md#japan-drivers-license-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Fysiske adresser i Japan](sensitive-information-type-entity-definitions.md#all-physical-addresses)|
|Beskyttelse af personlige oplysninger| Japan Beskyttelse af personlige oplysninger|- [Registreringsnummer for beboere i Japan](sensitive-information-type-entity-definitions.md#japan-resident-registration-number)</br> - [Japan Social Insurance Number (SIN)](sensitive-information-type-entity-definitions.md#japan-social-insurance-number-sin)|
|Beskyttelse af personlige oplysninger| Personidentificerbare Saudi-Arabien-data|- [Saudi-Arabiens nationale id](sensitive-information-type-entity-definitions.md#saudi-arabia-national-id)|
|Beskyttelse af personlige oplysninger| STORBRITANNIEN. Databeskyttelseslov|- [Det britiske nationalforsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Amerikansk/britisk pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Beskyttelse af personlige oplysninger| STORBRITANNIEN. Bestemmelser om beskyttelse af personlige oplysninger og elektronisk kommunikation|- [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Beskyttelse af personlige oplysninger| STORBRITANNIEN. Personidentificerbare oplysninger|- [Det britiske nationalforsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Amerikansk/britisk pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Beskyttelse af personlige oplysninger| STORBRITANNIEN. Piocp (Personal Information Online Code of Practice)|- [Det britiske nationalforsikringsnummer (NINO)](sensitive-information-type-entity-definitions.md#uk-national-insurance-number-nino) </br> - [Det britiske nationale sundhedstjenestenummer](sensitive-information-type-entity-definitions.md#uk-national-health-service-number) </br> - [SWIFT-kode](sensitive-information-type-entity-definitions.md#swift-code)|
|Beskyttelse af personlige oplysninger| U.S Patriot Act Enhanced|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Id-nummer for individuelle amerikanske skatteborgere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Beskyttelse af personlige oplysninger| U.S. Patriot Act|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> - [Id-nummer for individuelle amerikanske skatteborgere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Beskyttelse af personlige oplysninger| Udvidede personidentificerbare oplysninger (PII)-data (U.S. Personligt identificerbart)|- [Id-nummer for individuelle amerikanske skatteborgere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Amerikansk/britisk pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names)</br> - [Amerikanske fysiske adresser](sensitive-information-type-entity-definitions.md#us-physical-addresses)|
|Beskyttelse af personlige oplysninger| Amerikanske personidentificerbare oplysninger (PII-data)|- [Id-nummer for individuelle amerikanske skatteborgere (ITIN)](sensitive-information-type-entity-definitions.md#us-individual-taxpayer-identification-number-itin)  </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Amerikansk/britisk pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)|
|Beskyttelse af personlige oplysninger| Udvidede love om anmeldelse af brud på amerikanske stater|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[Amerikansk kørekortsnummer](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)</br> - [Alle fulde navne](sensitive-information-type-entity-definitions.md#all-full-names) </br> - [Amerikansk/britisk pasnummer](sensitive-information-type-entity-definitions.md#usuk-passport-number)</br> - [Alle medicinske vilkår og betingelser](sensitive-information-type-entity-definitions.md#all-medical-terms-and-conditions)|
|Beskyttelse af personlige oplysninger| U.S. State Breach Notification Laws|- [Kreditkortnummer](sensitive-information-type-entity-definitions.md#credit-card-number) </br> - [Amerikansk bankkontonummer](sensitive-information-type-entity-definitions.md#us-bank-account-number)</br> -[Amerikansk kørekortsnummer](sensitive-information-type-entity-definitions.md#us-drivers-license-number) </br> - [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|
|Beskyttelse af personlige oplysninger| Den amerikanske stat Love om fortrolighed af cpr-nummer|- [AMERIKANSK CPR-nummer (SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn)|

## <a name="locations"></a>Steder

En DLP-politik kan finde og beskytte elementer, der indeholder følsomme oplysninger på tværs af flere placeringer.

|Placering  |Medtag/udelad område  |Datatilstand  |Yderligere forudsætninger |
|---------|---------|---------|---------|
|Exchange-mail online |distributionsgruppe | data i bevægelse| Nej |
|SharePoint-onlinewebsteder   |Websteder       | data-at-rest </br> data i brug | Nej|
|OneDrive for Business konti| konto eller distributionsgruppe |data-at-rest </br> data i brug|Nej|
|Teams-chat- og kanalmeddelelser     | konto eller distributionsgruppe |data i bevægelse </br> data i brug |  Nej       |
|Microsoft Defender for Cloud Apps   | forekomst af cloudapp       |data-at-rest         | - [Brug politikker til forebyggelse af datatab til cloudapps, der ikke er fra Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)        |
|Enheder  |bruger eller gruppe         |data-at-rest </br>  data i brug </br>  data i bevægelse         |- [Få mere at vide om forebyggelse af datatab for Slutpunkt](endpoint-dlp-learn-about.md) </br>- [Kom i gang med forebyggelse af datatab i Slutpunkt](endpoint-dlp-getting-started.md) </br>- [Konfigurer indstillingerne for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) |
|Lagre i det lokale miljø (filshares og SharePoint)    |Repository         | data-at-rest         | - [Få mere at vide om forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-learn.md) </br> - [Kom i gang med forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)         |
|PowerBI| Arbejdsområder | data i brug | Nej|

Hvis du vælger at inkludere bestemte distributionsgrupper i Exchange, begrænses DLP-politikken kun til medlemmerne af den pågældende gruppe. På samme måde udelukker udeladelse af en distributionsgruppe alle medlemmer af den pågældende distributionsgruppe fra politikevaluering. Du kan vælge at tilpasse en politik til medlemmer af distributionslister, dynamiske distributionsgrupper og sikkerhedsgrupper. En DLP-politik kan ikke indeholde mere end 50 sådanne medtagelser og udeladelser.

Hvis du vælger at inkludere eller udelade bestemte SharePoint-websteder eller OneDrive-konti, kan en DLP-politik ikke indeholde mere end 100 sådanne medtagelser og udeladelser. Selvom denne grænse findes, kan du overskride denne grænse ved at anvende enten en politik for hele organisationen eller en politik, der gælder for hele placeringer.

Hvis du vælger at inkludere eller udelade bestemte OneDrive-konti eller -grupper, kan en DLP-politik ikke indeholde mere end 100 brugerkonti eller 50 grupper som medtagelse eller udeladelse.

### <a name="location-support-for-how-content-can-be-defined"></a>Understøttelse af placering for, hvordan indhold kan defineres

DLP-politikker registrerer følsomme elementer ved at matche dem med en følsom informationstype (SIT) eller med en følsomhedsmærkat eller en opbevaringsmærkat. Hver placering understøtter forskellige metoder til definition af følsomt indhold. Når du kombinerer placeringer i en politik, kan den måde, indholdet kan defineres på, ændres, fra hvordan det kan defineres af en enkelt placering. 

> [!IMPORTANT]
> Når du vælger flere placeringer for en politik, har en "nej"-værdi for en indholdsdefinitionskategori højere prioritet end værdien "ja". Når du f.eks. kun vælger SharePoint-websteder, understøtter politikken registrering af følsomme elementer af et eller flere SIT, af følsomhedsmærkat eller af opbevaringsmærkat. Men når du vælger SharePoint-websteder ***og*** Teams-chat- og kanalbeskedplaceringer, understøtter politikken kun registrering af følsomme elementer af SIT.

|Placering| Indhold kan defineres af SIT| Indhold kan defineres som følsomhedsmærkat| Indhold kan defineres af opbevaringsmærkat|
|---------|---------|---------|---------|
|Exchange-mail online|Ja| Ja| Nej|
|SharePoint-onlinewebsteder| Ja| Ja| Ja|
|OneDrive for Business konti| Ja| Ja| Ja|
|Teams-chat- og kanalmeddelelser | Ja| Nej| Nej|
|Enheder |Ja | Ja|  Nej|
|Microsoft Defender for Cloud Apps | Ja| Ja| Ja|
|Lagre i det lokale miljø| Ja| Ja| Nej|
|PowerBI|Ja | Ja| Nej|

> [!NOTE]
> DLP understøtter registrering af følsomhedsmærkater på mails og vedhæftede filer Se [Brug følsomhedsmærkater som betingelser i DLP-politikker](dlp-sensitivity-label-as-condition.md#use-sensitivity-labels-as-conditions-in-dlp-policies).

## <a name="rules"></a>Regler

<!--This section introduces the classifications of content that, when detected, can be protected. Link out to [Learn about sensitive information types]() and [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) as well as labels (cross referenced by supporting workload). It will touch on the purpose of multiple conditions, confidence levels (link out to [more on confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels)) and confidence levels video. How to use the confidence level to change the behavior of a policy in conjunction with the instance count.  eg. if you want your policy to trigger when it encounters situation DEF, set your conditions like HIJ.-->
<!--
- What is a rule in the context of a Policy?
- when and why should I have more than one rule?
- The purpose of rule groups
- How do I tune the behavior of a Policy through the tuning of rules
- what's in a rule-->

Regler er forretningslogikken i DLP-politikker. De består af:

- [**Betingelser**](#conditions) , der udløser politikken, når den matches
- [**Undtagelser**](#exceptions) fra betingelserne
- [**Handlinger**](#actions) , der skal udføres, når politikken udløses
- [**Brugermeddelelser**](#user-notifications-and-policy-tips) , der informerer dine brugere, når de foretager sig noget, der udløser en politik, og hjælper med at oplære dem i, hvordan din organisation ønsker følsomme oplysninger behandlet
- [**Bruger tilsidesætter**](#user-overrides) , når den er konfigureret af en administrator, og giver brugerne mulighed for selektivt at tilsidesætte en blokeringshandling
- [**Hændelsesrapporter**](#incident-reports) , der giver administratorer og andre vigtige interessenter besked, når der opstår et regelmatch
- [**Yderligere indstillinger**](#additional-options) , der definerer prioriteten for regelevaluering og kan stoppe yderligere behandling af regler og politikker.

 En politik indeholder en eller flere regler. Regler udføres sekventielt, startende med den højeste prioritetsregel i hver politik.

### <a name="the-priority-by-which-rules-are-processed"></a>Den prioritet, som regler behandles efter

#### <a name="hosted-service-workloads"></a>Hostede tjenestearbejdsbelastninger

For de hostede tjenestearbejdsbelastninger, f.eks. Exchange Online, SharePoint Online og OneDrive for Business, tildeles hver regel en prioritet i den rækkefølge, den oprettes i. Det betyder, at den regel, der oprettes først, har første prioritet, den regel, der er oprettet i den anden, har anden prioritet osv. 
  
![Regler i prioriteret rækkefølge](../media/dlp-rules-in-priority-order.png)

Når indhold evalueres i forhold til regler, behandles reglerne i prioriteret rækkefølge. Hvis indhold stemmer overens med flere regler, gennemtvinges den første regel, der evalueres, og som har den *mest* restriktive handling. Hvis indhold f.eks. stemmer overens med alle følgende regler, gennemtvinges *regel 3* , fordi det har den højeste prioritet, mest restriktive regel:
  
- Regel 1: Giver kun brugere besked
- Regel 2: Giver brugerne besked, begrænser adgangen og tillader brugertilsidesættelser
- *Regel 3: Giver brugerne besked, begrænser adgangen og tillader ikke brugertilsidesættelser*
- Regel 4: Begrænser adgangen

Regel 1, 2 og 4 ville blive evalueret, men ikke anvendt. I dette eksempel registreres matches for alle reglerne i overvågningsloggene og vises i DLP-rapporterne, selvom det kun er den mest restriktive regel, der anvendes.

Du kan bruge en regel til at opfylde et specifikt beskyttelseskrav og derefter bruge en DLP-politik til at gruppere fælles beskyttelseskrav, f.eks. alle de regler, der er nødvendige for at overholde en bestemt forordning.
  
Du kan f.eks. have en DLP-politik, der hjælper dig med at registrere tilstedeværelsen af oplysninger, der er underlagt HIPAA (Health Insurance Portability and Accountability Act). Denne DLP-politik kan hjælpe med at beskytte HIPAA-data (hvad) på tværs af alle SharePoint Online-websteder og alle OneDrive for Business websteder (hvor) ved at finde et hvilket som helst dokument, der indeholder disse følsomme oplysninger, som deles med personer uden for din organisation (betingelserne) og derefter blokere adgangen til dokumentet og sende en meddelelse (handlingerne). Disse krav gemmes som individuelle regler og grupperes som en DLP-politik for at forenkle administration og rapportering.
  
![Diagram, der viser, at DLP-politikken indeholder placeringer og regler](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png)

#### <a name="for-endpoints"></a>For slutpunkter

Prioriteten for regler for slutpunkter tildeles også i henhold til den rækkefølge, som det er oprettet i. Det betyder, at den regel, der oprettes først, har første prioritet, den regel, der er oprettet i den anden, har anden prioritet osv. 

Når en fil på et slutpunkt stemmer overens med flere DLP-politikker, er den første regel, der aktiveres med mest restriktiv håndhævelse af [slutpunktsaktiviteterne](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on) , den, der gennemtvinges for indholdet. Hvis indhold f.eks. stemmer overens med alle følgende regler, så har regel 2 forrang over de andre regler, da det er den mest restriktive.

- Regel 1: Kun overvågning af alle aktiviteter 
- *Regel 2: blokerer for al aktivitet*
- Regel 3: Blokerer alle aktiviteter med mulighed for, at slutbrugeren kan tilsidesætte

I eksemplet nedenfor har regel 1 forrang frem for de andre matchende regler, da det er den mest restriktive.

- *Regel 1: Blokerer aktivitet og tillader ikke brugertilsidesættelse*
- Regel 2: Blokerer aktivitet og tillader brugertilsidesættelser
- Regel 3: Overvåger kun alle aktiviteter
- Regel 4: Ingen håndhævelse

Alle de andre regler evalueres, men deres handlinger gennemtvinges ikke. Overvågningslogge viser den mest restriktive regel, der anvendes på filen. Hvis der er mere end én regel, der stemmer overens, og de er lige restriktive, styrer politik- og regelprioritet, hvilken regel der anvendes på filen.

### <a name="conditions"></a>Betingelser

Betingelser er inklusive, og det er her, du definerer, hvad reglen skal søge efter, og hvilken kontekst disse elementer bruges i. De fortæller reglen &#8212;, når du finder et element, der ser ud som *dette* og bruges på den måde *,* &#8212; er det et match, og resten af handlingerne i politikken skal udføres på det. Du kan bruge betingelser til at tildele forskellige handlinger til forskellige risikoniveauer. Følsomt indhold, der f.eks. deles internt, kan være lavere risiko og kræve færre handlinger end følsomt indhold, der deles med personer uden for organisationen.

> [!NOTE]
> Brugere, der har ikke-gæstekonti i en værtsorganisations Active Directory- eller Azure Active Directory-lejer, betragtes som personer i organisationen. 

#### <a name="content-contains"></a>Indholdet indeholder

 Alle placeringer understøtter, at **indholdet indeholder** en betingelse. Du kan vælge flere forekomster af hver indholdstype og yderligere tilpasse betingelserne ved hjælp af operatorerne **En af disse** (logisk OR) eller **Alle disse** (logiske AND):

- [følsomme oplysningstyper](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [følsomhedsmærkater](sensitivity-labels.md)
- [opbevaringsmærkater](retention.md#using-a-retention-label-as-a-condition-in-a-dlp-policy)

afhængigt af den [eller de placeringer](#location-support-for-how-content-can-be-defined) , du vælger at anvende politikken på. 

Reglen søger kun efter tilstedeværelsen af eventuelle **følsomhedsmærkater** og **opbevaringsmærkater** , du vælger. 

SIT'er har et foruddefineret [**konfidensniveau**](https://www.microsoft.com/videoplayer/embed/RE4Hx60) , som du kan ændre, hvis det er nødvendigt. Du kan få flere oplysninger under [Mere om tillidsniveauer](sensitive-information-type-learn-about.md#more-on-confidence-levels). 

> [!IMPORTANT]
> SIT'er har to forskellige måder at definere de maksimale antal parametre for entydige forekomster på. Hvis du vil vide mere, skal du se [Antal understøttede værdier for SIT.](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit)

#### <a name="condition-context"></a>Betingelseskontekst

De tilgængelige kontekstindstillinger ændres, afhængigt af hvilken placering du vælger. Hvis du vælger flere placeringer, er det kun de betingelser, som placeringerne har til fælles, der er tilgængelige.

##### <a name="conditions-exchange-supports"></a>Betingelser, som Exchange understøtter

- Indholdet indeholder
- Indhold deles fra Microsoft 365
- Indhold modtages fra
- Afsenderens IP-adresse er
- Har afsenderen tilsidesat politiktip
- Afsenderen er
- Afsenderdomænet er
- Afsenderadressen indeholder ord
- Afsenderadressen indeholder mønstre
- Afsender-AD-attribut indeholder ord eller udtryk
- Afsender-AD-attributten matcher mønstre
- Afsenderen er medlem af
- Indhold fra en vedhæftet fil kunne ikke scannes
- Indholdet af en vedhæftet fil i en hvilken som helst mail blev ikke scannet
- Den vedhæftede fil er beskyttet med adgangskode
- Filtypenavnet er
- Modtageren er medlem af
- Modtagerdomænet er
- Modtageren er
- Modtageradressen indeholder ord
- Modtageradressen stemmer overens med mønstre
- Modtager-AD-attributten indeholder ord eller udtryk
- Modtager-AD-attributten matcher mønstre
- Dokumentnavnet indeholder ord eller udtryk
- Dokumentnavnet stemmer overens med mønstre
- Dokumentegenskaben er
- Dokumentstørrelsen er lig med eller større end
- Dokumentindhold indeholder ord eller udtryk
- Dokumentindhold stemmer overens med mønstre
- Emne indeholder ord eller udtryk
- Emne matcher mønstre
- Emne eller brødtekst indeholder ord eller udtryk
- Mønstre for match af emne eller brødtekst
- Indholdstegnsæt indeholder ord
- Sidehovedet indeholder ord eller udtryk
- Header matcher mønstre
- Meddelelsesstørrelsen er lig med eller større end
- Meddelelsestypen er
- Meddelelsens prioritet er

##### <a name="conditions-sharepoint-supports"></a>Betingelser, som SharePoint understøtter
 
- Indholdet indeholder
- Indhold deles fra Microsoft 365
- Dokument oprettet af
- Dokument oprettet af medlem af
- Dokumentnavnet indeholder ord eller udtryk
- Dokumentnavnet stemmer overens med mønstre
- Dokumentstørrelse over
- Dokumentegenskaben er
- Filtypenavnet er

##### <a name="conditions-onedrive-accounts-supports"></a>Betingelser, som OneDrive-konti understøtter

- Indholdet indeholder
- Indhold deles fra Microsoft 365
- Dokument oprettet af
- Dokument oprettet af medlem af
- Dokumentnavnet indeholder ord eller udtryk
- Dokumentnavnet stemmer overens med mønstre
- Dokumentstørrelse over
- Dokumentegenskaben er
- Filtypenavnet er

##### <a name="conditions-teams-chat-and-channel-messages-supports"></a>Betingelser Teams-chat- og kanalmeddelelser understøtter

- Indholdet indeholder
- Indhold deles fra Microsoft 365
- Afsenderen er 
- Afsenderdomænet er 
- Modtagerdomænet er 
- Modtageren er 

##### <a name="conditions-devices-supports"></a>Betingelser, enheder understøtter

- Indholdet indeholder
- (eksempelvisning) Brugeren tilgåde et følsomt websted fra Edge. Se [Scenarie 6 Overvåg eller begræns brugeraktiviteter på følsomme tjenestedomæner (prøveversion)](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains-preview) for at få flere oplysninger.
- Filtypenavnet er
- Filtypen er
- Se [Slutpunktsaktiviteter, som du kan overvåge og udføre handlinger på](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on)

##### <a name="conditions-microsoft-defender-for-cloud-apps-supports"></a>Betingelser Microsoft Defender for Cloud Apps understøtter

- Indholdet indeholder
- Indhold deles fra Microsoft 365

##### <a name="conditions-on-premises-repositories-supports"></a>Betingelser, som lagre i det lokale miljø understøtter

- Indholdet indeholder
- Filtypenavnet er
- Dokumentegenskaben er

##### <a name="conditions-powerbi-supports"></a>Betingelser, som PowerBI understøtter

- Indholdet indeholder

#### <a name="condition-groups"></a>Betingelsesgrupper

Nogle gange har du brug for en regel for kun at identificere én ting, f.eks. alt indhold, der indeholder et AMERIKANSK CPR-nummer, som er defineret af et enkelt SIT. Men i mange scenarier, hvor de typer elementer, du forsøger at identificere, er mere komplekse og derfor sværere at definere, kræves der større fleksibilitet i definitionen af betingelser.

Hvis du f.eks. vil identificere indhold, der er underlagt DEN AMERIKANSKE sundhedsforsikringslov (HIPAA), skal du søge efter:
  
- Indhold, der indeholder bestemte typer følsomme oplysninger, f.eks. et CPR-nummer eller ETA-nummer (Drug Enforcement Agency).
    
    OG
    
- Indhold, der er vanskeligere at identificere, f.eks. kommunikation om en patients pleje eller beskrivelser af de leverede medicinske tjenester. Identificering af dette indhold kræver matchende nøgleord fra store nøgleordslister, f.eks. INTERNATIONAL Classification of Diseases (ICD-9-CM eller ICD-10-CM).
    
Du kan identificere denne type data ved at gruppere betingelser og bruge logiske operatorer (AND, OR) mellem grupperne.
    
For **U.S. Health Insurance Act (HIPPA)**, er betingelserne grupperet som dette:

![HIPPA-politikbetingelser](../media/dlp-rules-condition-groups-booleans.png)

Den første gruppe indeholder de SIT'er, der identificerer og individuelle, og den anden gruppe indeholder de SIT'er, der identificerer medicinsk diagnosticering.

### <a name="exceptions"></a>Undtagelser

I regler definerer undtagelser betingelser, der bruges til at udelade et element fra politikken. Logisk set er eksklusive betingelser, der evalueres efter de inkluderende betingelser og konteksten. De fortæller reglen &#8212; når du finder et element, der *ser sådan ud* , og som bruges, som om det er et match *,* og resten af handlingerne i politikken skal udføres på det ***, medmindre***... &#8212; 

I overensstemmelse med HIPPA-politikken kan vi f.eks. ændre reglen, så alle elementer, der indeholder et belgisk kørekortsnummer, udelades, f.eks.:

![HIPPA-politik med udeladelser](../media/dlp-rule-exceptions.png)

De undtagelser, der understøttes af placering, er identiske med alle medtagelsesbetingelserne, hvor den eneste forskel er præpendingen af "Except if" til hver understøttet betingelse. Hvis en regel kun indeholder undtagelser, gælder den for alle mails eller filer, der ikke opfylder kriterierne for udelukkelse.

På samme måde som alle placeringer understøtter den inkluderende betingelse:

- Indholdet indeholder

undtagelsen ville være:

- **Undtagen, hvis** indholdet indeholder 

### <a name="actions"></a>Handlinger 

Alle elementer, der foretager det via de inklusive ***betingelser** _ og eksklusive _*_undtagelser_*_ , har alle _*_handlinger_*_ , der er defineret i reglen, anvendt på det. Du skal konfigurere de påkrævede indstillinger for at understøtte handlingen. Hvis du f.eks. vælger Exchange med handlingen _ *Begræns adgang eller krypterer indholdet på Microsoft 365-placeringer**, skal du vælge mellem følgende indstillinger:

- Bloker brugere, så de ikke kan få adgang til delt SharePoint-, OneDrive- og Teams-indhold
    - Bloker alle. Det er kun indholdsejeren, den sidste ændringsadministrator og webstedsadministratoren, der fortsat har adgang
    - Bloker kun personer uden for din organisation. Brugere i organisationen vil fortsat have adgang.
- Kryptér mails (gælder kun for indhold i Exchange)

De handlinger, der er tilgængelige i en regel, afhænger af de valgte placeringer. Hvis du kun vælger én placering for den politik, der skal anvendes på, vises de tilgængelige handlinger nedenfor.

> [!IMPORTANT]
> For SharePoint Online og OneDrive for Business blokeres dokumenter proaktivt lige efter registrering af følsomme oplysninger, uanset om dokumentet er delt eller ej, for alle eksterne brugere, mens interne brugere fortsat vil have adgang til dokumentet.

#### <a name="exchange-location-actions"></a>Exchange-placeringshandlinger

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer
- Angiv overskrifter
- Fjern sidehoved
- Omdiriger meddelelsen til bestemte brugere
- Videresend meddelelsen til godkendelse til afsenderens chef
- Videresend meddelelsen til godkendelse til bestemte godkendere
- Føj modtageren til feltet Til
- Føj modtageren til feltet Cc
- Føj modtageren til feltet Bcc
- Tilføj afsenderens chef som modtager
- Fjernede O365-meddelelseskryptering og rettighedsbeskyttelse
- Forudindstillet mailemne
- Rediger emne i mail
- Tilføj HTML-ansvarsfraskrivelse

#### <a name="sharepoint-sites-location-actions"></a>Handlinger for placering af SharePoint-websteder

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer

#### <a name="onedrive-account-location-actions"></a>Handlinger for Placering af OneDrive-konto

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer

#### <a name="teams-chat-and-channel-messages-actions"></a>Handlinger for Teams-chat- og kanalmeddelelser

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer

#### <a name="devices-actions"></a>Enhedshandlinger

<!-- - Restrict access or encrypt the content in Microsoft 365 locations-->
- (eksempelvisning) Overvåg eller begrænsede aktiviteter, når brugerne tilgår følsomme websteder i Microsoft Edge-browseren på Windows-enheder. Se [Scenarie 6 Overvåg eller begræns brugeraktiviteter på følsomme tjenestedomæner (prøveversion)](endpoint-dlp-using.md#scenario-6-monitor-or-restrict-user-activities-on-sensitive-service-domains-preview) for at få flere oplysninger.
- Overvåg eller begræns aktiviteter på Windows-enheder

Hvis du vil bruge `Audit or restrict activities on Windows devices`, skal du konfigurere indstillinger i **DLP-indstillinger** og i den politik, du vil bruge dem i. Se [Begrænsede apps og appgrupper](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) for at få flere oplysninger.

Enhedens placering indeholder mange underaktiviteter (betingelser) og handlinger. Du kan få mere at vide under [Slutpunktsaktiviteter, som du kan overvåge og udføre handlinger på](endpoint-dlp-learn-about.md#endpoint-activities-you-can-monitor-and-take-action-on).

Når du vælger **Overvåg eller begræns aktiviteter på Windows-enheder**, kan du begrænse brugeraktiviteterne efter tjenestedomæne eller browser og begrænse de handlinger, som DLP udfører, ved at:

- Alle apps
- Af en liste over begrænsede apps, som du definerer
- En begrænset appgruppe (prøveversion), som du definerer.

##### <a name="service-domain-and-browser-activities"></a>Tjenestedomæne- og browseraktiviteter

Når du konfigurerer **domæner for Tillad/Bloker cloudtjenester** og listen **Over ikke-tilladte browsere** (se [Browser- og domænebegrænsninger for følsomme data](dlp-configure-endpoint-settings.md#browser-and-domain-restrictions-to-sensitive-data)), og en bruger forsøger at overføre en beskyttet fil til et cloudtjenestedomæne eller få adgang til den fra en ikke-tilladt browser, kan du konfigurere politikhandlingen til `Audit only`, `Block with override`eller `Block` aktiviteten.

##### <a name="file-activities-for-all-apps"></a>Filaktiviteter for alle apps

Med indstillingen **Filaktiviteter for alle apps** vælger du enten **Begræns ikke filaktiviteter** eller **Anvend begrænsninger på bestemte aktiviteter**. Når du vælger at anvende begrænsninger på bestemte aktiviteter, anvendes de handlinger, du vælger her, når en bruger har åbnet et DLP-beskyttet element. Du kan fortælle DLP til `Audit only`, `Block with override`, `Block` (handlingerne) for disse brugeraktiviteter:

- **Kopiér til Udklipsholder**
- **Kopiér til et flytbart USB-drev** 
- **Kopiér til et netværksshare**
- **Udskrive**
- **Kopiér eller flyt ved hjælp af en Bluetooth-app, der ikke er tilladt**
- **Fjernskrivebord-tjenester**


##### <a name="restricted-app-activities"></a>Begrænsede appaktiviteter  

Du har tidligere kaldt Ikke-tilladte apps og definerer en liste over apps i DLP-indstillinger for slutpunkt, som du vil angive begrænsninger for. Når en bruger forsøger at få adgang til en DLP-beskyttet fil ved hjælp af en app, der findes på listen, kan du enten `Audit only`, `Block with override`eller `Block` aktiviteten. DLP-handlinger, der er defineret i **Begrænsede appaktiviteter** , tilsidesættes, hvis appen er medlem af en begrænset appgruppe. Derefter anvendes de handlinger, der er defineret i den begrænsede appgruppe.

##### <a name="file-activities-for-apps-in-restricted-app-groups-preview"></a>Filaktiviteter for apps i begrænsede appgrupper (prøveversion)

Du definerer dine begrænsede appgrupper under DLP-indstillinger for slutpunkter og føjer begrænsede appgrupper til dine politikker. Når du føjer en begrænset appgruppe til en politik, skal du vælge en af disse indstillinger:

- Begræns ikke filaktivitet
- Anvend begrænsninger på alle aktiviteter
- Anvend begrænsninger på bestemte aktiviteter

Når du vælger en af indstillingerne *for Anvend begrænsninger* , og en bruger forsøger at få adgang til en DLP-beskyttet fil ved hjælp af en app, der er i den begrænsede appgruppe, kan du enten `Audit only`, `Block with override`eller `Block` efter aktivitet. DLP-handlinger, som du definerer her, tilsidesætter de handlinger, der er defineret i **Begrænsede appaktiviteter** og **Filaktiviteter for alle apps** for appen.

Se [Begrænsede apps og appgrupper](dlp-configure-endpoint-settings.md#restricted-apps-and-app-groups) for at få flere oplysninger. 

#### <a name="microsoft-defender-for-cloud-apps-actions"></a>Microsoft Defender for Cloud Apps handlinger

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer
- Begræns tredjepartsapps

#### <a name="on-premises-repositories-actions"></a>Handlinger for lagre i det lokale miljø

- Begræns adgang til eller fjern filer i det lokale miljø

#### <a name="powerbi-actions"></a>PowerBI-handlinger

- Giv brugerne besked med mail- og politiktips
- Send beskeder til administrator

#### <a name="actions-available-when-you-combine-locations"></a>Handlinger, der er tilgængelige, når du kombinerer placeringer

Hvis du vælger Exchange og en anden enkelt placering for den politik, der skal anvendes på,

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer

Og

- alle handlinger for den ikke-Exchange-placering

handlinger vil være tilgængelige.

Hvis du vælger to eller flere ikke-Exchange-placeringer for den politik, der skal anvendes på,

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer

OG

- alle handlinger for ikke-Exchange-placeringer 

handlinger vil være tilgængelige.

Hvis du f.eks. vælger Exchange og Enheder som placeringer, vil disse handlinger være tilgængelige:

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer
- Overvåg eller begræns aktiviteter på Windows-enheder

Hvis du vælger Enheder og Microsoft Defender for Cloud Apps, vil disse handlinger være tilgængelige:

- Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer
- Overvåg eller begræns aktiviteter på Windows-enheder
- Begræns tredjepartsapps

Om en handling træder i kraft eller ej, afhænger af, hvordan du konfigurerer politikkens tilstand. Du kan vælge at køre politikken i testtilstand med eller uden at vise politiktip ved at vælge indstillingen **Test den først** . Du vælger at køre politikken, så snart en time efter den er oprettet, ved at vælge indstillingen **Slå den til med det samme** , eller du kan vælge blot at gemme den og vende tilbage til den senere ved at vælge indstillingen **Hold den fra** . 


<!-- This section needs to explain that the actions available depend on the locations selected AND that the observed behavior of a policy is produced through an interaction of the configured actions AND the configured status (off, test, apply) of a policy. It will detail the purpose of each of the available actions and the location/desired outcome interaction and provide examples eg. how to use the Restrict Third Party apps in the context of a policy that is applied to endpoints so that users can't use a upload content to a third party site or the interaction of on-premises scanner with restrict access or remove on-premises files.  Also what happens when I select multiple locations? provide abundant examples for most common scenarios-->


### <a name="user-notifications-and-policy-tips"></a>Brugermeddelelser og politiktip

<!--This section introduces the business need for user notifications, what they are, their benefit, how to use them, how to customize them, and links out to 

- https://docs.microsoft.com/en-us/microsoft-365/compliance/use-notifications-and-policy-tips?view=o365-worldwide
- https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-policy-tips-reference?view=o365-worldwide

for where they are used/expected behavior-->

<!--You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.-->

Når en bruger forsøger at udføre en handling på et følsomt element i en kontekst, der opfylder betingelserne og undtagelserne for en regel, kan du fortælle brugeren om det via mail med brugermeddelelser og i pop op-vinduet med kontekstpolitiktip. Disse meddelelser er nyttige, fordi de øger bevidstheden og hjælper med at uddanne personer i organisationens DLP-politikker.

Indhold som f.eks. en Excel-projektmappe på et OneDrive for Business websted, der indeholder personlige oplysninger og deles med en gæst.

![Meddelelseslinjen viser politiktip i Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)

> [!IMPORTANT]
> - Meddelelsesmails sendes ubeskyttet.
> - Mailmeddelelser understøttes kun for Microsoft 365-tjenesterne.

#### <a name="email-notifications-support-by-selected-location"></a>Understøttelse af mailmeddelelser efter valgt placering

|Valgt placering  |Mailmeddelelser understøttes  |
|---------|---------|
|Enheder     |- Understøttes ikke         |
|Exchange + enheder     |– Understøttes til Exchange </br>- Ikke understøttet for enheder  |
|Exchange    |- Understøttet        |
|SharePoint + enheder  |- Understøttes for SharePoint </br>- Ikke understøttet for enheder         |
|SharePoint    |- Understøttet |
|Exchange + SharePoint    |– Understøttes til Exchange </br>- Understøttes for SharePoint  |
|Enheder + SharePoint + Exchange    |- Ikke understøttet for enheder </br>- Understøttes for SharePoint </br> Understøttes for Exchange |
|Teams    |- Understøttes ikke |
|OneDrive for Business   |- Understøttet         |
|OneDrive for Business + enheder     |- Understøttes for OneDrive for Business </br>- Ikke understøttet for enheder         |
|Power-BI|- Understøttes ikke|
|Microsoft Defender for Cloud Apps|- Understøttes ikke|
|Lagre i det lokale miljø|- Understøttes ikke|

Du kan også give personer mulighed for at [tilsidesætte politikken](#user-overrides), så de ikke blokeres, hvis de har et gyldigt forretningsbehov, eller hvis politikken registrerer et falsk positivt.

Konfigurationsindstillinger for brugermeddelelser og politiktip varierer afhængigt af de valgte overvågningsplaceringer. Hvis du har valgt:

- Exchange
- SharePoint
- OneDrive
- Teams-chat og -kanal
- Defender for Cloud Apps





Du kan aktivere/deaktivere brugermeddelelser for forskellige Microsoft-apps. [Se reference til tip til forebyggelse af datatab](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)

- Du kan aktivere/deaktivere meddelelser med et politiktip.
    - mailmeddelelser til den bruger, der har sendt, delt eller senest ændret indholdet ELLER
    - giv bestemte personer besked

og tilpas mailteksten, emnet og teksten til politiktip.

![Konfigurationsindstillinger for brugermeddelelser og politiktip, der er tilgængelige for Exchange, SharePoint, OneDrive, Teams-chat og -kanal og Defender for Cloud Apps](../media/dlp-user-notification-non-devices.png)

Hvis du kun har valgt Enheder, får du alle de samme indstillinger, der er tilgængelige for Exchange, SharePoint, OneDrive, Teams Chat og Kanal og Defender for Cloud Apps, samt muligheden for at tilpasse meddelelsestitel og indhold, der vises på den Windows 10 enhed.

![Konfigurationsindstillinger for brugermeddelelser og politiktip, der er tilgængelige for enheder](../media/dlp-user-notification-devices.png)  

Du kan tilpasse tekstens titel og brødtekst ved hjælp af disse parametre. Brødteksten understøtter disse:

|Almindeligt navn  |Parameter  |Eksempel
|---------|---------|---------|
|filnavn     |%%Filnavn%% | Contoso-dokument 1 |
|procesnavn     |%%ProcessName%% | Word |
|politiknavn     |%%PolicyName%%| Contoso meget fortroligt |
|Handling | %%AppliedActions%% | indsætter dokumentindhold fra Udklipsholder i en anden app |

**%%AppliedActions%%** erstatter disse værdier i meddelelsens brødtekst:


|fælles handlingsnavn |værdi, der erstattes med parameteren %%AppliedActions%% |
|---------|---------|
|kopiér til lager, der kan fjernes    |*skriver til flytbart lager*         |
|kopiér til netværksshare     |*skriver til et netværksshare*         |
|Udskrive     |*Udskrivning*         |
|indsæt fra Udklipsholder  |*indsætte fra Udklipsholder*         |
|kopiér via bluetooth   |*overfører via Bluetooth*         |
|åbn med en ikke-tilladt app     |*åbner med denne app*         |
|kopiér til et fjernskrivebord (RDP)     |*overfører til fjernskrivebord*         |
|uploader til et websted, der ikke er tilladt     |*uploader til dette websted*         |
|adgang til elementet via en ikke-tilladt browser     |*åbner med denne browser*         |

Brug af denne brugerdefinerede tekst

*%%AppliedActions%% Filnavn %%FileName%% via %%ProcessName%% er ikke tilladt af din organisation. Klik på 'Tillad', hvis du vil tilsidesætte politikken %%PolicyName%%* 

opretter denne tekst i den brugerdefinerede meddelelse:

*Indsætning fra udklipsholderens filnavn: Contoso-dokument 1 via WINWORD.EXE er ikke tilladt af din organisation. Klik på knappen 'Tillad', hvis du vil tilsidesætte politikken Contoso meget fortroligt*
 

> [!NOTE]
> Brugermeddelelser og politiktip er ikke tilgængelige for placeringen i det lokale miljø

> [!NOTE]
> Kun politiktip fra den højeste prioritet, mest restriktive regel vises. Et politiktip fra en regel, der blokerer adgang til indhold, vises f.eks. via et politiktip fra en regel, der blot sender en meddelelse. Dette forhindrer folk i at se en overlappende række af politiktips.

Hvis du vil vide mere om konfiguration og brug af brugermeddelelser og politiktip, herunder hvordan du tilpasser meddelelsen og tipteksten, skal du se 
- [Send mailmeddelelser, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies).
  
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

#### <a name="blocking-and-notifications-in-sharepoint-online-and-onedrive-for-business"></a>Blokering og meddelelser i SharePoint Online og OneDrive for Business

I denne tabel vises DLP-blokerings- og meddelelsesfunktionsmåden for politikker, der er begrænset til SharePoint Online og OneDrive for Business.

|Betingelser  |Konfiguration af handlinger |Konfiguration af brugermeddelelse|Konfiguration af hændelsesrapporter |Funktionsmåde for blokering og meddelelse|
|---------|---------|---------|---------|---------|
|- **Indhold deles fra Microsoft 365** </br>- **med personer uden for min organisation**     |Der er ikke konfigureret nogen handlinger         |- **Brugermeddelelser**, **der er slået** til </br>- **Giv brugerne i Office 365-tjenesten besked med et politiktip** valgt </br>- **Giv den bruger, der har sendt, delt eller senest ændret indholdet, besked om, at indholdet** er valgt         |- **Send en besked til administratorer, når et regelmatch forekommer** angivet til **Til** </br>- **Send en besked, hver gang en aktivitet stemmer overens med den regel** , der er angivet til **Til** </br>- **Brug rapporter over mailhændelser til at give dig besked, når et politikmatch er** angivet til **Til**         |– Meddelelser sendes kun, når en fil deles med en ekstern bruger, og en ekstern bruger får adgang til filen.  |
|- **Indhold deles fra Microsoft 365** </br>- **kun med personer i min organisation**        | Der er ikke konfigureret nogen handlinger         |-  **Brugermeddelelser**, **der er slået** til   </br>- **Giv brugerne i Office 365-tjenesten besked med et politiktip** valgt  </br>- **Giv den bruger, der har sendt, delt eller senest ændret indholdet, besked om, at indholdet** er valgt    |  - **Send en besked til administratorer, når et regelmatch forekommer** angivet til **Til** </br>- **Send besked, hver gang en aktivitet stemmer overens med reglen** </br>- **Brug rapporter over mailhændelser til at give dig besked, når et politikmatch er** angivet til **Til**       |– Meddelelser sendes, når en fil uploades |
|- **Indhold deles fra Microsoft 365** </br>- **med personer uden for min organisation**    | - **Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer** er valgt </br>- **Bloker brugere fra at modtage mail eller få adgang til delte SharePoint-, OndeDrive- og Teams-filer** er valgt </br>- **Bloker kun personer uden for din organisation** er valgt          |- **Brugermeddelelser**, **der er slået** til </br>- **Giv brugerne i Office 365-tjenesten besked med et politiktip** valgt </br>- **Giv den bruger, der har sendt, delt eller senest ændret indholdet, besked om, at indholdet** er valgt  |  - **Send en besked til administratorer, når et regelmatch forekommer** angivet til **Til** </br>- **Send besked, hver gang en aktivitet stemmer overens med reglen** </br>- **Brug rapporter over mailhændelser til at give dig besked, når et politikmatch er** angivet til **Til**             | – Adgangen til en følsom fil blokeres, så snart den uploades </br>– Meddelelser, der sendes, når indhold deles fra Microsoft 365 med personer uden for organisationen         |
|- **Indhold deles fra Microsoft 365** </br>- **med personer uden for min organisation** |  - **Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer** er valgt </br>- **Bloker brugere fra at modtage mail eller få adgang til delte SharePoint-, OndeDrive- og Teams-filer** er valgt </br>- **Bloker alle** er markeret        | - **Brugermeddelelser**, **der er slået** til </br>- **Giv brugerne i Office 365-tjenesten besked med et politiktip** valgt </br>- **Giv den bruger, der har sendt, delt eller senest ændret indholdet, besked om, at indholdet** er valgt         | - **Send en besked til administratorer, når et regelmatch forekommer** angivet til **Til** </br>- **Send besked, hver gang en aktivitet stemmer overens med reglen** </br>- **Brug rapporter over mailhændelser til at give dig besked, når et politikmatch er** angivet til **Til**        |Der sendes meddelelser, når en fil deles med en ekstern bruger, og en ekstern bruger får adgang til filen.         |
|- **Indhold deles fra Microsoft 365** </br>- **med personer uden for min organisation**     |- **Begræns adgang til eller kryptér indholdet på Microsoft 365-placeringer** er valgt </br>- **Bloker kun personer, der har fået adgang til indholdet, via indstillingen "Alle med linket"** er valgt.         |  - **Brugermeddelelser**, **der er slået** til </br>- **Giv brugere i Office 365 tjeneste besked med et politiktip** valgt.  </br>- **Giv den bruger, der har sendt, delt eller senest ændret indholdet, besked om, at indholdet** er valgt     |- **Send en besked til administratorer, når et regelmatch forekommer** angivet til **Til**   </br>- **Send besked, hver gang en aktivitet stemmer overens med reglen** </br>- **Brug rapporter over mailhændelser til at give dig besked, når et politikmatch er** angivet til **Til**       |Meddelelser sendes, så snart en fil uploades         |


### <a name="user-overrides"></a>Bruger tilsidesætter

Hensigten med **brugertilsidesættelser** er at give brugerne mulighed for med begrundelse at tilsidesætte DLP-politikblokeringshandlinger på følsomme elementer i Exchange, SharePoint, OneDrive eller Teams, så de kan fortsætte deres arbejde. Brugertilsidesættelser er kun aktiveret, når **Giv brugere i Office 365 tjenester med et politiktip** er aktiveret, så brugertilsidesættelser går hånd i hånd med meddelelser og politiktips. 

![Indstillinger for brugertilsidesættelse for en DLP-politik](../media/dlp-user-overrides.png)

> [!NOTE]
> Brugertilsidesættelser er ikke tilgængelige for lagerplaceringen i det lokale miljø.

Brugertilsidesættelser er typisk nyttige, når din organisation udruller en politik første gang. Den feedback, du får fra eventuelle tilsidesættelsesberettigelser og identificering af falske positiver, hjælper med at justere politikken. 

<!-- This section covers what they are and how to best use them in conjunction with Test/Turn it on right away and link out to where to find the business justification for the override (DLP reports?  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide)  https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide#view-the-justification-submitted-by-a-user-for-an-override-->

- Hvis politiktips i den mest restriktive regel tillader, at andre tilsidesætter reglen, tilsidesætter tilsidesættelse af denne regel også andre regler, som indholdet matchede.
 
<!--![User notifications and user overrides sections of DLP rule editor](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)-->
 
Hvis du vil vide mere om brugertilsidesættelser, skal du se:

- [Få vist den begrundelse, der er sendt af en bruger for en tilsidesættelse](view-the-dlp-reports.md#view-the-justification-submitted-by-a-user-for-an-override)

### <a name="incident-reports"></a>Hændelsesrapporter

<!--DLP interacts with other M365 information protection services, like IR. Link this to a process outline for triaging/managing/resolving DLP incidents


https://docs.microsoft.com/en-us/microsoft-365/compliance/view-the-dlp-reports?view=o365-worldwide
https://docs.microsoft.com/en-us/microsoft-365/compliance/dlp-configure-view-alerts-policies?view=o365-worldwide-->

Når en regel matches, kan du sende en hændelsesrapport til din overholdelsesansvarlige (eller alle personer, du vælger) med oplysninger om hændelsen. Rapporten indeholder oplysninger om det element, der blev matchet, det faktiske indhold, der matchede reglen, og navnet på den person, der senest ændrede indholdet. I forbindelse med mails inkluderer rapporten også den oprindelige meddelelse, der svarer til en DLP-politik, som en vedhæftet fil.

DLP sender hændelsesoplysninger til andre Microsoft Purview-information protection-tjenester, f.eks [. styring af insiderrisiko](insider-risk-management.md). Hvis du vil have oplysninger om hændelser til styring af insiderrisiko, skal du angive alvorsgraden af **hændelsesrapporterne** til **Høj**.

<!--![Page for configuring incident reports](../media/31c6da0e-981c-415e-91bf-d94ca391a893.png)-->

Beskeder kan sendes, hver gang en aktivitet stemmer overens med en regel, hvilket kan være støjende, eller de kan samles i færre beskeder baseret på antallet af matches eller mængden af elementer over en bestemt tidsperiode.

![send en besked, hver gang en regel stemmer overens eller samles over tid i færre rapporter](../media/dlp-incident-reports-aggregation.png)

DLP scanner mail på en anden måde end SharePoint Online eller OneDrive for Business elementer. I SharePoint Online og OneDrive for Business scanner DLP eksisterende elementer samt nye og genererer en hændelsesrapport, når der findes et match. I Exchange Online scanner DLP kun nye mails og genererer en rapport, hvis der er et politikmatch. DLP scanner eller matcher ***ikke*** tidligere eksisterende mailelementer, der er gemt i en postkasse eller et arkiv.

### <a name="additional-options"></a>Yderligere indstillinger

Hvis du har flere regler i en politik, kan du bruge **Yderligere indstillinger** til at styre yderligere behandling af regler, hvis der er et match til den regel, du redigerer, samt angive prioriteten for evaluering af reglen.

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Plan for forebyggelse af datatab (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md#create-a-dlp-policy-from-a-template)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
