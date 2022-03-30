---
title: Reference til tip til politik til forebyggelse af datatab
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
description: Få mere at vide om, hvordan du føjer et politiktip til en DLP-politik (forebyggelse af datatab) giver en bruger besked om, at de arbejder med indhold, der er i konflikt med en DLP-politik.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 52bb2fba47c5588dc6a44eb5f8e1d7b745e69e70
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599376"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Reference til tip til politik til forebyggelse af datatab

Tip til DLP-politik i Outlook Web Access understøttes for alle de betingelser, undtagelser og handlinger, der gælder for Exchange-arbejdsbelastningen i en DLP-politik med undtagelse af følgende:

**Betingelser:**

- Modtageren er medlem af
- Sidehovedet indeholder ord eller udtryk
- Sidehoved matcher mønstre
- Meddelelsestype er
- Indholdstegnsæt indeholder ord
- Har afsenderen tilsidesat politiktip
- Meddelelsesstørrelse er lig med eller større end
- Attributten Afsender-AD indeholder ord eller udtryk
- Afsenderens AD-attribut svarer til mønstre
- IP-afsenderintervaller
- Modtager-AD-attributten indeholder ord eller udtryk
- Modtagerens AD-attribut svarer til mønstre
- Dokumentnavn indeholder ord eller udtryk
- Dokumentnavn matcher mønstre
- Dokumentindhold indeholder ord eller udtryk
- Dokumentindhold matcher mønstre

**Handlinger:**

- Videresende meddelelsen til godkendelse til afsenderens leder
- Videresende meddelelsen til godkendelse til bestemte godkendere
- Omdiriger meddelelsen til bestemte brugere
- Føj modtagere til feltet Til
- Føj modtagere til feltet Cc
- Føj modtagere til feltet Bcc
- Tilføj afsenderens overordnede som modtager
- Tilføj HTML-ansvarsfraskrivelse
- Forudindstillet mail-emne
- Fjern O365-meddelelseskryptering og rettighedsbeskyttelse

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 og nyere understøtter visning af politiktip til kun visse betingelser og undtagelser

Aktuelt understøtter Outlook 2013 og nyere visning af politiktip til politikker, som ikke indeholder nogen betingelser eller undtagelser, bortset fra de nedenstående betingelser og tilsvarende undtagelser:

- Indhold indeholder (fungerer kun for typer af følsomme oplysninger. Følsomhedsmærkater understøttes ikke)
- Indhold deles

Bemærk, at alle betingelserne fungerer for mails, der er Outlook i en klientapp, hvor de matcher indhold og gennemtvinger beskyttende handlinger på indhold. Men visning af politiktip til brugere understøttes ikke for eventuelle betingelser, der bruges, bortset fra dem, der er nævnt ovenfor.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Outlook 2013 og nyere og Office-apps på skrivebordssupport, der viser politiktip til nogle typer af følsomme oplysninger

Listen over følsomme oplysningstyper, der er klar til at vise tip til DLP-politik i Outlook på skrivebordet (2013 og nyere) og Office-apps (Word, Excel, PowerPoint) på skrivebordet er følgende:

- ABA-registreringsnummer
- Argentina National Identity (DNI) Number
- Australiens bankkontonummer
- Australia Medical Account-nummer
- Australiens pasnummer
- Australiens skattefilnummer
- Azure DocumentDB Auth-nøgle  
- Forbindelsesstreng for Azure IAAS-database og Azure SQL forbindelsesstreng  
- Azure IoT-forbindelsesstreng  
- Indstillingsadgangskode til Azure-publicering  
- Azure Redis Cache Connection String  
- Azure SAS  
- Azure Service Bus forbindelsesstreng  
- Azure Storage kontonøgle  
- Azure Storage kontonøgle (Generic)  
- Belgiens nationale nummer
- Brasiliens CPF-nummer
- Brasiliens juridiske enhedsnummer (CNPJ)
- Brasiliens nationale id-kort (RG)
- Canadas bankkontonummer
- Canada Kørekortnummer
- Canada Tilstandstjeneste tal
- Canada Passport-nummer
- Canada Personal Health Identification Number (PHIN)
- Canada Social Insurance Number
- Chile Identity Card Number
- Kinas iboende identitetskort (Folkerepublikken Kina)
- Kreditkortnummer
- Kroatiens identitetskortnummer  
- OIB-nummer (Croatia Personal Identification)  
- Tjekkisk personligt identitetsnummer  
- Danmark Personligt identifikationsnummer
- Drug Enforcement Agency (DEA) Number
- EU-debetkortnummer
- EU-kørekortnummer  
- EU-national identifikationsnummer  
- EU-pasnummer  
- EU Cpr-nummer (SSN) eller tilsvarende id  
- EU-skatteidentifikationsnummer (TIN)  
- Finlands nationale id
- Finland-pasnummer
- Frankrigs kørekortnummer
- France National ID Card (CNI)
- Frankrigs pasnummer
- France Social Security Number (INSEE)
- Tysk kørekortnummer
- Tysk pasnummer
- Tysklands identitetskortnummer
- Grækenlands nationale id-kort  
- Hong Kong Identity Card (HKID) Number
- India Permanent Account Number (PAN)
- Indiens entydige identifikationsnummer (Aadhaar)
- Indonesia Identity Card (KTP) Number
- International Banking Account Number (IBAN)
- International klassificering af klassifikationer (ICD-10-CM)  
- International klassificering af klassifikationer (ICD-9-CM)  
- IP-adresse
- Ireland Personal Public Service-nummer (PPS) 
- Israels bankkontonummer
- Israels nationale id
- Italiens kørekortnummer
- Japans bankkontonummer
- Japan Kørekortnummer
- Japan-pasnummer
- Japan Resident Registration Number
- Japan Social Insurance Number (SIN)
- Japansk bopælskortnummer
- Malaysia Identity Card-nummer
- Nederlandske borgeres servicenummer  
- New Zealand Det sundhedstilstandsnummer, der er gerningsnummeret
- Norges identitetsnummer  
- Philippines Unified Multi-Purpose ID Number
- Polens identitetskort
- Polens nationale id (PESEL)
- Polens pas
- Portugals borgeres kortnummer
- Saudi-Arabiens nationale id
- Singapores nationale registreringsidentitetskort (NRIC)-nummer
- Sydafrikas identifikationsnummer  
- South Korea Resident Registration Number
- CPR-nummer (Spain Social Security Number)
- SQL Server forbindelsesstreng  
- Sveriges nationale id
- Sveriges pasnummer
- SWIFT-kode
- Taiwans nationale id
- Taiwan-pasnummer
- Taiwan Resident Certificate (ARC/TARC)
- Identifikationskode for den thailandske befolkning
- Tyrkisk nationalt identifikationsnummer
- Storbritannien Kørekortnummer
- Storbritannien Tilvalgsrullenummer
- Storbritannien Nationalt Tilstandstjeneste nummer
- Storbritannien Nationalt forsikringsnummer (NINO)
- USA/Storbritannien Pasnummer
- USA Bankkontonummer
- USA Kørekortnummer
- USA Id-nummer for individuelle skatteydere (ITIN)
- USA CPR-nummer (SSN)

Bemærk, at brugerdefinerede typer af følsomme oplysninger også understøttes til tip til DLP-politikker ud over de ovenstående typer af følsomme oplysninger, der er klar til brug.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>Forebyggelse af datatab på slutpunktsenheder understøtter politiktip til kun visse typer af følsomme oplysninger

Listen over følsomme oplysningstyper, der er klar til brug i dokumenter, der er bosiddende på slutpunktsenheder, er følgende:

- ABA-registreringsnummer 
- Argentina National Identity (DNI) Number 
- Australiens bankkontonummer 
- Australia Medical Account-nummer 
- Australiens pasnummer 
- Australiens skattefilnummer 
- Australske forretningsnummer 
- Australske firmanummer 
- Østrigs kørekortnummer 
- Østrigs identitetskort 
- Østrigs pasnummer 
- Østrigs CPR-nummer 
- Skatte-id for Østrig 
- Momsnummer (moms) i Østrig 
- Azure DocumentDB Auth-nøgle 
- Forbindelsesstreng for Azure IAAS-database og Azure SQL forbindelsesstreng 
- Azure IoT-forbindelsesstreng 
- Indstillingsadgangskode til Azure-publicering 
- Azure Redis Cache Connection String 
- Azure SAS 
- Azure Service Bus forbindelsesstreng 
- Azure Storage kontonøgle 
- Azure Storage kontonøgle (Generic) 
- Belgiens kørekortnummer 
- Belgiens nationale nummer 
- Belgiens pasnummer 
- Belgiens momsnummer for moms 
- Brasiliens CPF-nummer 
- Brasiliens juridiske enhedsnummer (CNPJ) 
- Brasiliens nationale id-kort (RG) 
- Bulgariens kørekortnummer 
- Bulgariens pasnummer 
- Bulgariens uniformsnummer 
- Canadas bankkontonummer 
- Canada Kørekortnummer 
- Canada Tilstandstjeneste tal 
- Canada Passport-nummer 
- Canada Personal Health Identification Number (PHIN) 
- Canada Social Insurance Number 
- Chile Identity Card Number 
- Kinas iboende identitetskort (Folkerepublikken Kina) 
- Kreditkortnummer 
- Kroatiens kørekortnummer 
- Kroatiens identitetskortnummer 
- Kroatiens nationale id-kortnummer 
- Kroatiens pasnummer 
- OIB-nummer (Croatia Personal Identification) 
- CSCAN-AZURE0060 Azure Storage-kontos delte adgangssignatur 
- CSCAN-GENERAL0140 Generel symmetrisk nøgle 
- Cyperns kørekortnummer 
- Cypernsidentitetskort 
- Cyperns pasnummer 
- Cyperns skatte-id 
- Tjekkisk kørekortnummer 
- Tjekkisk personligt identitetsnummer 
- Tjekkisk pasnummer 
- Danmark Kørekortnummer 
- Danmark pasnummer 
- Danmark Personligt identifikationsnummer 
- Drug Enforcement Agency (DEA) Number 
- Estlands kørekortnummer 
- Estlands pasnummer 
- Estlands personlige identifikationskode 
- EU-debetkortnummer 
- EU-kørekortnummer 
- EU-national identifikationsnummer 
- EU-pasnummer 
- EU Cpr-nummer (SSN) eller tilsvarende id 
- EU-skatteidentifikationsnummer (TIN) 
- Finlands kørekortnummer 
- Finland European Health Insurance Number 
- Finlands nationale id 
- Finland-pasnummer 
- Frankrigs kørekortnummer 
- France Health Insurance Number 
- France National ID Card (CNI) 
- Frankrigs pasnummer 
- France Social Security Number (INSEE) 
- France Tax Identification Number (numéro SPI.) 
- Momsnummer for Frankrigs momsnummer 
- Tysk kørekortnummer 
- Tysk pasnummer 
- Tysklands identitetskortnummer 
- Tysklands skatte-id 
- Tysklands momsnummer (moms) 
- Grækenlands kørekortnummer 
- Grækenlands nationale id-kort 
- Grækenlands pasnummer 
- Grækenlands CPR-nummer (AMKA) 
- Græsk skatte-id 
- Hong Kong Identity Card (HKID) Number 
- Ungarsk CPR-nummer (DEN UNGARSKE CPR-NUMMER) 
- Ungarsk værdi tilføjet momsnummer 
- Ungarns kørekortnummer 
- Ungarns pasnummer 
- Ungarns personlige identifikationsnummer 
- Ungarns skatteidentifikationsnummer 
- India Permanent Account Number (PAN) 
- Indiens entydige identifikationsnummer (Aadhaar) 
- Indonesia Identity Card (KTP) Number 
- International Banking Account Number (IBAN) 
- International klassificering af klassifikationer (ICD-10-CM) 
- International klassificering af klassifikationer (ICD-9-CM) 
- IP-adresse 
- Irlands kørekortnummer 
- Irlands pasnummer 
- Ireland Personal Public Service-nummer (PPS) 
- Israels bankkontonummer 
- Israels nationale id 
- Italiens kørekortnummer 
- Italiens regnskabskode 
- Italiens pasnummer 
- Momsnummer for italiener tilføjet moms 
- Japans bankkontonummer 
- Japan Kørekortnummer 
- Japan-pasnummer 
- Japan Resident Registration Number 
- Japan Social Insurance Number (SIN) 
- Japanese My Number Corporate 
- Japansk Mit nummer Personligt 
- Japansk bopælskortnummer 
- Letland Kørekortnummer 
- Letlands pasnummer 
- Letlands personlige kode 
- Litauens kørekortnummer 
- Litauens pasnummer 
- Litauens personlige kode 
- Luxemburg kørekortnummer 
- Luxemburgs nationale identifikationsnummer (fysiske personer) 
- Luxemburgs nationale identifikationsnummer (ikke-naturlige personer) 
- Luxemburg pasnummer 
- Malaysia Identity Card-nummer 
- Maltas kørekortnummer 
- Maltas identitetskortnummer 
- Maltas pasnummer 
- Maltas skatte-id 
- Nederlandske borgeres servicenummer 
- Nederlandsk kørekortnummer 
- Nederlandsk pasnummer 
- Nederlandsk skatte-id 
- Nederlandsk momsnummer (moms) 
- New Zealand bankkontonummer 
- New Zealand-kørekortnummer 
- New Zealand Inland Revenue-nummer 
- New Zealand Det sundhedstilstandsnummer, der er gerningsnummeret 
- New Zealand Social Integration Number 
- Norges identitetsnummer 
- Philippines Unified Multi-Purpose ID Number 
- Polens kørekortnummer 
- Polens identitetskort 
- Polens nationale id (PESEL) 
- Polens pas 
- Polens skatte-id 
- Polsk REGON-nummer 
- Portugals borgeres kortnummer 
- Portugal Kørekortnummer 
- Portugal-pasnummer 
- Portugals skatte-id 
- Rumæniens kørekortnummer 
- Rumæniens pasnummer 
- Rumæniens personlige numeriske kode (CNP) 
- Russisk pasnummer (indenrigs) 
- Russisk pasnummer (international) 
- Saudi-Arabiens nationale id 
- Singapores nationale registreringsidentitetskort (NRIC)-nummer 
- Slovakiets kørekortnummer 
- Slovakiets pasnummer 
- Slovakiets personlige nummer 
- Sloveniens kørekortnummer 
- Sloveniens pasnummer 
- Sloveniens skatte-id 
- Sloveniens entydige masternummer for borgere 
- Sydafrikas identifikationsnummer 
- South Korea Resident Registration Number 
- Spain DNI 
- Spanien-kørekortnummer 
- Spaniens pasnummer 
- CPR-nummer (Spain Social Security Number) 
- Spaniens skatte-id 
- SQL Server forbindelsesstreng 
- Sveriges kørekortnummer 
- Sveriges nationale id 
- Sveriges pasnummer 
- Sveriges skatte-id 
- SWIFT-kode 
- Schweizisk CPR-nummer AHV 
- Taiwans nationale id 
- Taiwan-pasnummer 
- Taiwan Resident Certificate (ARC/TARC) 
- Identifikationskode for den thailandske befolkning 
- Tyrkisk nationalt identifikationsnummer 
- Storbritannien Kørekortnummer 
- Storbritannien Tilvalgsrullenummer 
- Storbritannien Nationalt Tilstandstjeneste nummer 
- Storbritannien Nationalt forsikringsnummer (NINO) 
- Storbritannien Entydigt skatteyders referencenummer 
- USA/Storbritannien Pasnummer 
- USA Bankkontonummer 
- USA Kørekortnummer 
- USA Id-nummer for individuelle skatteydere (ITIN) 
- USA CPR-nummer (SSN) 
- Ukraines pasnummer (indenrigs) 
- Ukraines pasnummer (internationale) 
 
Bemærk, at brugerdefinerede typer af følsomme oplysninger også registreres ud over de ovenstående typer af følsomme oplysninger

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Supportmatrix til DLP-politiktips på tværs af Microsoft-apps

|**App og platform**|**Understøttelse af DLP-politiktip**|**Typer af følsomme oplysninger understøttes**|**Understøttede prædikater og handlinger**|**Kommentarer**|
|:--|:--|:--|:--|:--|
|**Outlook på internettet**|:::image type="icon" source="../media/rightmrk.png" border="false":::|alle|delmængde||
|**Outlook Win32 (ver. 2105 build 14026.20000 og halvårlige kanal ver. 2102 build 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|delmængde|delmængde|Se [Outlook 2013](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) og nyere understøtter visning af politiktip til kun visse betingelser og undtagelser og [Outlook 2013 og nyere og Office-apps](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) på skrivebordssupport, der viser politiktip til nogle typer af følsomme oplysninger for at få mere at vide om understøttelse af typer af følsomme oplysninger og DLP-betingelser og handlinger, der understøttes til at vise tips til DLP-politikker på Outlook  Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|ingen|ingen|Tips til DLP-politik understøttes ikke på Outlook mobile|
|**SharePoint Online/OneDrive for Business-webklient**|:::image type="icon" source="../media/rightmrk.png" border="false":::|alle|alle SPO-/ODB-prædikater og handlinger i DLP||
|**SharePoint Win32/OneDrive for Business Win32-klient**|:::image type="icon" source="../media/crsmrk.png" border="false":::|ingen|ingen|Tip til DLP-politik understøttes ikke SharePoint eller OneDrive-klientprogrammer på computeren|
|**Word-, Excel-, PowerPoint-webklient**|:::image type="icon" source="../media/rightmrk.png" border="false":::|alle|alle SPO-/ODB-prædikater og handlinger i DLP|Tip til DLP-politik understøttes, hvis dokumentet er hostet på SPO- eller ODB-webappen, og DLP-politikken allerede er stemplet.|
|**Word-, Excel-, PowerPoint Mobile klient**|:::image type="icon" source="../media/crsmrk.png" border="false":::|ingen|ingen|Tip til DLP-politik understøttes ikke i mobilapps til Office.|
|**Teams Web/ Teams-computer/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|alle|alle Teams prædikater i DLP-politik|Politiktip vises, når en meddelelse er markeret med flag som "Denne meddelelse er blevet markeret med flag. Hvad kan jeg gøre?" Når brugeren klikker på linket, kan brugeren gennemse de følsomme oplysningstyper, der registreres og tilsidesættes, eller rapportere et problem, hvis administratoren tillader det. Bemærk, at der ikke vises politiktip for filer. Når modtageren forsøger at få adgang til dokumentet, får de muligvis nægtet adgang, hvis det ikke er tilladt.|
|**Win32-slutpunktsenheder**|:::image type="icon" source="../media/rightmrk.png" border="false":::|delmængde|alle slutpunkts-DLP-prædikater og handlinger i DLP-politik|Se [Forebyggelse af datatab på slutpunkt understøtter politiktip til kun nogle typer af følsomme oplysninger](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**macOS-enheder (forhåndsvisning)**|kun standardtip|alle|delmængde|Politikker til forebyggelse af datatab kan håndhæves på macOS-enheder. Brugerdefinerede politiktip understøttes ikke.|
|**Tredjepartsskyapps**|:::image type="icon" source="../media/crsmrk.png" border="false":::|ingen|ingen|Tip til politik til forebyggelse af datatab understøttes ikke i tredjepartsskyapps|
|**On-prem**|:::image type="icon" source="../media/crsmrk.png" border="false":::|ingen|ingen||
|**Word-, Excel-, PowerPoint Win32-klient**|:::image type="icon" source="../media/crsmrk.png" border="false":::|delmængde|delmængde|Se en [Outlook 2013 og nyere og Office-apps](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) på skrivebordssupport, der viser politiktip til kun nogle typer af følsomme oplysninger for listen over typer af følsomme oplysninger, der understøttes</br></br>Politiktip til WXP-klientapps fungerer for dokumenter, der er gemt på SharePoint Online- eller OneDrive for Business-websteder for alle DLP-politikker, som har nøjagtigt nedenstående eller et undersæt af betingelser eller handlinger i DLP-politikken:</br> <ul><li>Indhold indeholder følsomme oplysningstyper</li><li>Adgangsomfang (indhold deles internt/eksternt)</li><li>Giv bruger besked (politiktip/brugermeddelelser)</li><li>Bloker alle</li><li>Hændelsesrapporter</li></ul></br> Hvis en anden betingelse eller handling er til stede, vises DLP-politiktip for den pågældende politik ikke i skrivebordsappsene i Word, Excel eller PowerPoint.</br>Se [Politiktip i Excel, PowerPoint og Word for at](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word) få mere at vide|
||||||
