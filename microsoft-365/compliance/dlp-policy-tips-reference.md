---
title: Reference til politiktips til forebyggelse af datatab
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
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
description: Få mere at vide om, hvordan du føjer et politiktip til en DLP-politik (forebyggelse af datatab). Giv en bruger besked om, at brugeren arbejder med indhold, der er i konflikt med en DLP-politik.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 074283fbdf22d4a7ed645539f706a7b292c20485
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917271"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Reference til politiktips til forebyggelse af datatab

Tip til DLP-politikker i Outlook Web Access understøttes for alle de betingelser, undtagelser og handlinger, der gælder for Exchange-arbejdsbelastninger i en DLP-politik, undtagen følgende:

**Betingelser:**

- Modtageren er medlem af
- Sidehovedet indeholder ord eller udtryk
- Header matcher mønstre
- Meddelelsestypen er
- Indholdstegnsæt indeholder ord
- Har afsenderen tilsidesat politiktip
- Meddelelsesstørrelsen er lig med eller større end
- Afsender-AD-attributten indeholder ord eller udtryk
- Afsender AD-attributten matcher mønstre
- Afsenders IP-intervaller
- Modtager-AD-attributten indeholder ord eller udtryk
- Modtager-AD-attributten matcher mønstre
- Dokumentnavnet indeholder ord eller udtryk
- Dokumentnavnet stemmer overens med mønstre
- Dokumentindhold indeholder ord eller udtryk
- Dokumentindhold stemmer overens med mønstre

**Handlinger:**

- Videresend meddelelsen til godkendelse til afsenderens chef
- Videresend meddelelsen til godkendelse til bestemte godkendere
- Omdiriger meddelelsen til bestemte brugere
- Føj modtagere til feltet Til
- Føj modtagere til cc-boksen
- Føj modtagere til Bcc-boksen
- Tilføj afsenderens chef som modtager
- Tilføj HTML-ansvarsfraskrivelse
- Forudindstillet mailemne
- Fjern O365-meddelelseskryptering og rettighedsbeskyttelse

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 og nyere understøtter visning af politiktip for kun nogle betingelser og undtagelser

I øjeblikket understøtter Outlook 2013 og nyere visning af politiktip til politikker, der ikke indeholder nogen betingelse eller undtagelser bortset fra nedenstående betingelser og tilsvarende undtagelser:

- Indhold indeholder (fungerer kun for typer af følsomme oplysninger. Følsomhedsmærkater understøttes ikke)
- Indholdet er delt

Bemærk, at alle betingelser fungerer for mails, der er oprettet i Outlook-klientappen, hvor de matcher indhold og gennemtvinger beskyttende handlinger på indhold. Visning af politiktip til brugere understøttes dog ikke for nogen betingelser, der bruges ud over dem, der er nævnt ovenfor.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Understøttelse af Outlook 2013 og nyere og Office-apps på Desktop, der viser politiktip til kun nogle følsomme oplysningstyper

Listen over indbyggede følsomme oplysningstyper, der registreres til visning af tip til DLP-politik i Outlook på Desktop (2013 og nyere) og Office-apps (Word, Excel, PowerPoint) på Desktop er følgende:

- ABA-routingnummer
- Argentinas nationale identitet (DNI)-nummer
- Australiens bankkontonummer
- Nummer på medicinsk konto i Australien
- Australiens passport-nummer
- Australiens skattefilnummer
- Godkendelsesnøgle til Azure DocumentDB  
- Azure IAAS-databaseforbindelsesstreng og Azure SQL-forbindelsesstreng  
- Azure IoT-forbindelsesstreng  
- Adgangskode til indstilling for Azure Publish  
- Forbindelsesstreng til Azure Redis-cache  
- Azure SAS  
- Azure Service Bus forbindelsesstreng  
- Azure Storage-kontonøgle  
- Azure Storage-kontonøgle (generisk)  
- Belgiens nationale nummer
- BrasilienS CPF-nummer
- Juridisk enhedsnummer for Brasilien (CNPJ)
- Nationalt id-kort for Brasilien (RG)
- Canadas bankkontonummer
- Canadas kørekortsnummer
- Canada Health Service-nummer
- Canada Passport-nummer
- Canada Personal Health Identification Number (PHIN)
- Canada Social Insurance Number
- Chiles identitetskortnummer
- Kina Resident Identity Card (PRC) Number
- Kreditkortnummer
- Kroatiens identitetskortnummer  
- Personidentifikationsnummer for Kroatien (OIB)  
- Tjekkisk personligt id-nummer  
- Danmark Personidentifikationsnummer
- Nummer på drug enforcement agency (DEA)
- EU-debetkortnummer
- EU-kørekortsnummer  
- EU-nationalt identifikationsnummer  
- EU-pasnummer  
- EU-cpr-nummer (SSN) eller tilsvarende id  
- EU-skatteidentifikationsnummer (TIN)  
- Finlands nationale id
- Finlands pasnummer
- Frankrigs kørekortsnummer
- Nationalt id-kort for Frankrig (CNI)
- France Passport-nummer
- Det franske cpr-nummer (INSEE)
- Tysk kørekortsnummer
- Tysk pasnummer
- Tysklands identitetskortnummer
- Nationalt id-kort for Grækenland  
- HKID-nummer (Hong Kong Identity Card)
- Permanent kontonummer for Indien (PAN)
- Entydigt id for Indien (Aadhaar)
- Indonesiens identitetskortnummer (KTP)
- Internationalt bankkontonummer (IBAN)
- International klassificering af sygdomme (ICD-10-CM)  
- International klassificering af sygdomme (ICD-9-CM)  
- IP-adresse
- Irlands personlige offentlige tjeneste (PPS)-nummer 
- Israels bankkontonummer
- Israels nationale id
- Italiens kørekortsnummer
- Japans bankkontonummer
- Japans kørekortsnummer
- Pasnummer til Japan
- Registreringsnummer for residenter i Japan
- Japan Social Insurance Number (SIN)
- Japansk bopælskortnummer
- Malaysias identitetskortnummer
- BSN-nummer (Netherlands Citizen's Service)  
- New Zealands sundhedsministerium
- Norges identitetsnummer  
- Filippinerne Unified Multi-Purpose ID-nummer
- Polens identitetskort
- Nationalt id for Polen (PESEL)
- Polens pas
- Nummer på portugals borgerkort
- Saudi-Arabiens nationale id
- NRIC-nummer (National Registration Identity Card) for Singapore
- Sydafrikas identifikationsnummer  
- Registreringsnummer for residenter i Sydkorea
- Spanien Cpr-nummer (SSN)
- SQL Server forbindelsesstreng  
- Nationalt id for Sverige
- Sveriges pasnummer
- SWIFT-kode
- Taiwans nationale id
- Taiwans pasnummer
- Taiwan Resident Certificate (ARC/TARC)
- Thai population-id-kode
- Tyrkisk nationalt identifikationsnummer
- STORBRITANNIEN. Kørekortsnummer
- STORBRITANNIEN. Valgrullenummer
- STORBRITANNIEN. Nummer på det nationale sundhedsvæsen
- STORBRITANNIEN. NINO (National Insurance Number)
- Amerikansk/britisk Passport-nummer
- Amerikansk bankkontonummer
- Amerikansk kørekortsnummer
- Id-nummer for individuelle amerikanske skatteborgere (ITIN)
- SSN (US Social Security Number)

Bemærk, at brugerdefinerede typer af følsomme oplysninger også understøttes for tip til DLP-politikker ud over ovenstående indbyggede typer følsomme oplysninger.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>Forebyggelse af datatab på slutpunktsenheder understøtter kun politiktip til nogle følsomme oplysningstyper

Listen over indbyggede følsomme oplysningstyper, der registreres i dokumenter, der findes på slutpunktsenheder, er følgende:

- ABA-routingnummer 
- Argentinas nationale identitet (DNI)-nummer 
- Australiens bankkontonummer 
- Nummer på medicinsk konto i Australien 
- Australiens passport-nummer 
- Australiens skattefilnummer 
- Australsk virksomhedsnummer 
- Australsk firmanummer 
- Østrigs kørekortsnummer 
- Østrigs identitetskort 
- Pasnummer for Østrig 
- Det østrigske cpr-nummer 
- Østrigs skatteidentifikationsnummer 
- Momsnummer for Østrig 
- Godkendelsesnøgle til Azure DocumentDB 
- Azure IAAS-databaseforbindelsesstreng og Azure SQL-forbindelsesstreng 
- Azure IoT-forbindelsesstreng 
- Adgangskode til indstilling for Azure Publish 
- Forbindelsesstreng til Azure Redis-cache 
- Azure SAS 
- Azure Service Bus forbindelsesstreng 
- Azure Storage-kontonøgle 
- Azure Storage-kontonøgle (generisk) 
- Belgiens kørekortsnummer 
- Belgiens nationale nummer 
- Belgien Passport-nummer 
- Belgien Momsnummer 
- BrasilienS CPF-nummer 
- Juridisk enhedsnummer for Brasilien (CNPJ) 
- Nationalt id-kort for Brasilien (RG) 
- Bulgariens kørekortsnummer 
- Bulgariens pasnummer 
- Bulgariens ensartede civilnummer 
- Canadas bankkontonummer 
- Canadas kørekortsnummer 
- Canada Health Service-nummer 
- Canada Passport-nummer 
- Canada Personal Health Identification Number (PHIN) 
- Canada Social Insurance Number 
- Chiles identitetskortnummer 
- Kina Resident Identity Card (PRC) Number 
- Kreditkortnummer 
- Kroatiens kørekortsnummer 
- Kroatiens identitetskortnummer 
- Nationalt id-kortnummer for Kroatien 
- Kroatiens pasnummer 
- Personidentifikationsnummer for Kroatien (OIB) 
- CSCAN-AZURE0060 Azure Storage-konto med delt adgangssignatur 
- CSCAN-GENERAL0140 Generel symmetrisk nøgle 
- Cyperns kørekortsnummer 
- Cyperns identitetskort 
- Cyperns pasnummer 
- Cyperns skatteidentifikationsnummer 
- Tjekkisk kørekortsnummer 
- Tjekkisk personligt id-nummer 
- Pasnummer for Tjekkiet 
- Danmarks kørekortsnummer 
- Danmark Passport-nummer 
- Danmark Personidentifikationsnummer 
- Nummer på drug enforcement agency (DEA) 
- Estlands kørekortsnummer 
- Estisk pasnummer 
- Personidentifikationskode for Estland 
- EU-debetkortnummer 
- EU-kørekortsnummer 
- EU-nationalt identifikationsnummer 
- EU-pasnummer 
- EU-cpr-nummer (SSN) eller tilsvarende id 
- EU-skatteidentifikationsnummer (TIN) 
- Finlands kørekortsnummer 
- Finland Europæisk sygesikringsnummer 
- Finlands nationale id 
- Finlands pasnummer 
- Frankrigs kørekortsnummer 
- Frankrig Sygesikringsnummer 
- Nationalt id-kort for Frankrig (CNI) 
- France Passport-nummer 
- Det franske cpr-nummer (INSEE) 
- Frankrigs skatteidentifikationsnummer (numéro SPI.) 
- Momsnummer for Frankrig 
- Tysk kørekortsnummer 
- Tysk pasnummer 
- Tysklands identitetskortnummer 
- Tysklands skatteidentifikationsnummer 
- Momsnummer for Tyskland 
- Grækenlands kørekortsnummer 
- Nationalt id-kort for Grækenland 
- Grækenlands pasnummer 
- Det græske cpr-nummer (AMKA) 
- Græsk skatteidentifikationsnummer 
- HKID-nummer (Hong Kong Identity Card) 
- Ungarsk cpr-nummer (TAJ) 
- Ungarsk momsnummer 
- Ungarns kørekortsnummer 
- Ungarn Pasnummer 
- Ungarns personidentifikationsnummer 
- Ungarn Skatteidentifikationsnummer 
- Permanent kontonummer for Indien (PAN) 
- Entydigt id for Indien (Aadhaar) 
- Indonesiens identitetskortnummer (KTP) 
- Internationalt bankkontonummer (IBAN) 
- International klassificering af sygdomme (ICD-10-CM) 
- International klassificering af sygdomme (ICD-9-CM) 
- IP-adresse 
- Irlands kørekortsnummer 
- Irlands pasnummer 
- Irlands personlige offentlige tjeneste (PPS)-nummer 
- Israels bankkontonummer 
- Israels nationale id 
- Italiens kørekortsnummer 
- Italiens regnskabskode 
- Pasnummer til Italien 
- Italien Momsnummer 
- Japans bankkontonummer 
- Japans kørekortsnummer 
- Pasnummer til Japan 
- Registreringsnummer for residenter i Japan 
- Japan Social Insurance Number (SIN) 
- Japansk mit nummer firma 
- Japansk mit personlige nummer 
- Japansk bopælskortnummer 
- Letlands kørekortsnummer 
- Letlands pasnummer 
- Letlands personlige kodeks 
- Litauens kørekortsnummer 
- Litauens pasnummer 
- Litauens personlige kode 
- Luxemburg-kørekortsnummer 
- Luxembourgs nationale identifikationsnummer (fysiske personer) 
- Luxembourgs nationale identifikationsnummer (ikke-fysiske personer) 
- Luxemburg Passport-nummer 
- Malaysias identitetskortnummer 
- Maltas kørekortsnummer 
- Maltas identitetskortnummer 
- Maltas pasnummer 
- Maltas skatte-id-nummer 
- BSN-nummer (Netherlands Citizen's Service) 
- Nederlandsk kørekortsnummer 
- Nederlandsk pasnummer 
- Nederlandsk skatteidentifikationsnummer 
- Nederlandsk momsnummer 
- New Zealands bankkontonummer 
- New Zealand-driverlicensnummer 
- New Zealands omsætningsnummer 
- New Zealands sundhedsministerium 
- Velfærdsnummer for New Zealand 
- Norges identitetsnummer 
- Filippinerne Unified Multi-Purpose ID-nummer 
- Polens kørekortsnummer 
- Polens identitetskort 
- Nationalt id for Polen (PESEL) 
- Polens pas 
- Polens skatteidentifikationsnummer 
- Polsk REGON-tal 
- Nummer på portugals borgerkort 
- Portugals kørekortsnummer 
- Pasnummer til Portugal 
- Portugals skatteidentifikationsnummer 
- Rumæniens kørekortsnummer 
- Rumænien Passport-nummer 
- Rumæniens personlige numeriske kode (CNP) 
- Russisk pasnummer (indenlandsk) 
- Russisk pasnummer (international) 
- Saudi-Arabiens nationale id 
- NRIC-nummer (National Registration Identity Card) for Singapore 
- Slovakiets kørekortsnummer 
- Slovakiets pasnummer 
- Slovakiets personlige nummer 
- Sloveniens kørekortsnummer 
- Sloveniens pasnummer 
- Sloveniens skatteidentifikationsnummer 
- Sloveniens entydige masterborgernummer 
- Sydafrikas identifikationsnummer 
- Registreringsnummer for residenter i Sydkorea 
- Spanien DNI 
- Spaniens kørekortsnummer 
- Spaniens pasnummer 
- Spanien Cpr-nummer (SSN) 
- Spaniens skatteidentifikationsnummer 
- SQL Server forbindelsesstreng 
- Sveriges kørekortsnummer 
- Nationalt id for Sverige 
- Sveriges pasnummer 
- Sveriges skatteidentifikationsnummer 
- SWIFT-kode 
- Swiss Social Security Number AHV 
- Taiwans nationale id 
- Taiwans pasnummer 
- Taiwan Resident Certificate (ARC/TARC) 
- Thai population-id-kode 
- Tyrkisk nationalt identifikationsnummer 
- STORBRITANNIEN. Kørekortsnummer 
- STORBRITANNIEN. Valgrullenummer 
- STORBRITANNIEN. Nummer på det nationale sundhedsvæsen 
- STORBRITANNIEN. NINO (National Insurance Number) 
- STORBRITANNIEN. Entydigt referencenummer for skatteborger 
- Amerikansk/britisk Passport-nummer 
- Amerikansk bankkontonummer 
- Amerikansk kørekortsnummer 
- Id-nummer for individuelle amerikanske skatteborgere (ITIN) 
- SSN (US Social Security Number) 
- Ukraines pasnummer (indenlandsk) 
- Ukraines passport-nummer (international) 
 
Bemærk, at brugerdefinerede følsomme informationstyper også vil blive registreret ud over ovenstående indbyggede typer følsomme oplysninger

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Supportmatrix til tip til DLP-politik på tværs af Microsoft-apps

|**App og platform**|**Understøttelse af DLP-politiktip**|**Understøttede typer følsomme oplysninger**|**Understøttede prædikater og handlinger**|**Kommentarer**|
|:--|:--|:--|:--|:--|
|**Outlook på world wide web**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Alle|Undersæt||
|**Outlook Win32 (ver. 2105 build 14026.20000 og halvårlig kanal ver. 2102 build 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Undersæt|Undersæt|Se [Outlook 2013 og nyere understøtter visning af politiktips for kun nogle betingelser og undtagelser](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) og [Outlook 2013 og nyere og understøttelse af Office-apps på Desktop, der viser politiktips til kun nogle følsomme oplysningstyper](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) for at få oplysninger om understøttelse af følsomme oplysningstyper og DLP-betingelser og understøttede handlinger til visning af DLP-politiktip i Outlook Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Ingen|Ingen|Tip til DLP-politikker understøttes ikke på Outlook Mobile|
|**SharePoint Online/OneDrive for Business webklient**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Alle|alle SPO/ODB-prædikater og handlinger i DLP||
|**SharePoint Win32/OneDrive for Business Win32-klient**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Ingen|Ingen|Tip til DLP-politikker understøttes ikke i Klientapps til SharePoint eller OneDrive-skrivebord|
|**Word, Excel, PowerPoint-webklient**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Alle|alle SPO/ODB-prædikater og handlinger i DLP|DLP-politiktip understøttes, hvis dokumentet hostes på SPO- eller ODB-webappen, og DLP-politikken allerede er stemplet.|
|**Word, Excel PowerPoint Mobile Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Ingen|Ingen|Tip til DLP-politikker understøttes ikke i mobilapps til Office.|
|**Teams Web/Teams Desktop/Teams Mobile/Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Alle|alle Teams-prædikater i DLP-politik|Politiktips vises, når en meddelelse er markeret som "Denne meddelelse er blevet markeret med flag. Hvad kan jeg gøre?" Når brugeren klikker på linket, kan vedkommende gennemse de registrerede følsomme oplysningstyper og tilsidesætte eller rapportere et problem, hvis det er tilladt af administratoren. Bemærk, at der ikke vises nogen politiktip til filer. Når modtageren forsøger at få adgang til dokumentet, kan vedkommende blive nægtet adgang, hvis den ikke er tilladt.|
|**Win32-slutpunktsenheder**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Undersæt|alle DLP-prædikater og handlinger for slutpunkter i DLP-politikken|Se [Forebyggelse af datatab på Slutpunkt understøtter politiktip for kun nogle følsomme oplysningstyper](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**macOS-enheder**|kun standardtip|Alle|Undersæt|Politikker til forebyggelse af datatab kan gennemtvinges på macOS-enheder. Brugerdefinerede politiktip understøttes ikke.|
|**Tredjepartscloudapps**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Ingen|Ingen|Tip til politikker til forebyggelse af datatab understøttes ikke i tredjepartscloudapps|
|**I det lokale miljø**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Ingen|Ingen||
|**Word, Excel, PowerPoint Win32-klient**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Undersæt|Undersæt|Se [Support til Outlook 2013 og nyere og Office-apps på Desktop, der viser politiktips til kun nogle følsomme oplysningstyper](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) for listen over understøttede typer følsomme oplysninger</br></br>Politiktips til WXP-klientapps fungerer for dokumenter, der er gemt på SharePoint Online eller OneDrive for Business-websteder for alle DLP-politikker, som har præcis nedenstående eller et undersæt af betingelser eller handlinger i DLP-politikken:</br> <ul><li>Indhold indeholder følsomme oplysningstyper</li><li>Adgangsområde (indhold deles internt/eksternt)</li><li>Giv brugeren besked (politiktip/brugermeddelelser)</li><li>Bloker alle</li><li>Hændelsesrapporter</li></ul></br> Hvis der findes en anden betingelse eller handling, vises DLP-politiktip for den pågældende politik ikke i skrivebordsappsene i Word, Excel eller PowerPoint.</br>Se [Politiktips i Excel, PowerPoint og Word for at](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word) få flere oplysninger|
|**Power BI**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Undersæt|Undersæt|Politikker til forebyggelse af datatab i Power BI er i offentlig prøveversion. </br></br> Politiktip og administratorbeskeder understøttes. |
||||||
