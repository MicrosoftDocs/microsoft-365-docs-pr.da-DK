---
title: Hvad DLP-politikskabelonerne indeholder
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
f1_keywords:
- ms.o365.cc.DLPNewPolicyFromTemplate
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Få mere at vide om, hvad politikskabelonerne til forebyggelse af datatab (DLP) i Office 365 Security & Compliance Center omfatter.
ms.openlocfilehash: cad7270fd60b0bce9febe90f25156bd27bdcee32
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63587513"
---
# <a name="what-the-dlp-policy-templates-include"></a>Hvad DLP-politikskabelonerne indeholder

Forebyggelse af datatab (DLP) i Security &amp; Compliance Center indeholder klar til brug-politikskabeloner, der adresserer almindelige overholdelseskrav, som f.eks. at hjælpe dig med at beskytte følsomme oplysninger, der er underlagt US Health Insurance Act (HIPAA), amerikansk Gramm-Leach-Bliley Act (GLBA) eller U.S. Insurance Act. I dette emne vises alle politikskabelonerne, hvilke typer af følsomme oplysninger de søger efter, og hvad standardbetingelserne og handlingerne er. Dette emne indeholder ikke alle detaljer om, hvordan hver politikskabelon er konfigureret. I stedet viser emnet dig nok oplysninger til, at du kan beslutte, hvilken skabelon der er det bedste udgangspunkt for dit scenarie. Husk, at du kan tilpasse disse politikskabeloner, så de opfylder dine specifikke krav.
  
## <a name="australia-financial-data"></a>Finansielle data fra Australien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Australien Financial: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Australiens skattefilnummer – Antal min. 1, maks. antal 9  <br/>  Australiens bankkontonummer – Min. antal 1, maks. antal 9  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Australien Financial: Scan indhold, der er delt uden for – high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  Australiens skattefilnummer – Antal min. 10, maks. antal 500  <br/>  Australien bankkontonummer – Min. antal 10, Maks. antal 500  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Australia Health Records Act (HRIP Act)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Australien HRIP: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – Antal min. 1, maks. antal 9  <br/>  Australia Medical Account Number – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Australien HRIP: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – Antal min. 10, maks. antal 500  <br/>  Australia Medical Account Number – Min antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Data om personlige oplysninger (PII) i Australien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Australiens PII: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – Antal min. 1, maks. antal 9  <br/>  Australien kørekortnummer – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Australien PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – Antal min. 10, maks. antal 500  <br/>  Australiens kørekortnummer – Min.t. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="australia-privacy-act"></a>Australia Privacy Act

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Beskyttelse af personlige oplysninger i Australien: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australien kørekortnummer – Min antal 1, Maks. antal 9  <br/>  Australiens pasnummer – Antal min. 1, maks. 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Beskyttelse af personlige oplysninger i Australien: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens kørekortnummer – Min.t. 10, Maks. antal 500  <br/>  Australiens pasnummer – Antal min. 10, maks. 500 <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-financial-data"></a>Finansielle data for Canada

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Finansielle data i Canada: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  Canada Bank Account Number – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Finansielle data i Canada: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  Canada Bank Account Number – Min antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Canada Health Information Act (PLATFORM)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada  SCANNER: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number – Min antal 1, Maks. antal 9  <br/>  Canada Tilstandstjeneste tal – Min.t. 1, Maks. antal 9  <br/>  Canada Personal Health Identification Number (PHIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Canada  SCANNER: Scan indhold, der er delt uden for – high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada-pasnummer – Antal min. 10, maks. 500  <br/>  Canada Social Insurance Number – Min antal 10, Maks. antal 500  <br/>  Canada Tilstandstjeneste tal – Min.t. 10, Maks. antal 500  <br/>  Canada Personal Health Identification Number (PHIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Canada Personal Health Act (PHIPA) - Ontario

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PHIPA: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number – Min antal 1, Maks. antal 9  <br/>  Canada Tilstandstjeneste tal – Min.t. 1, Maks. antal 9  <br/>  Canada Personal Health Identification Number (PHIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Canada PHIPA: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada-pasnummer – Antal min. 10, maks. 500  <br/>  Canada Social Insurance Number – Min antal 10, Maks. antal 500  <br/>  Canada Tilstandstjeneste tal – Min.t. 10, Maks. antal 500  <br/>  Canada Personal Health Identification Number (PHIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Canada Personal Health Information Act (PHIA) - Manitoba

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PHIA: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Social Insurance Number – Min antal 1, Maks. antal 9  <br/>  Canada Tilstandstjeneste tal – Min.t. 1, Maks. antal 9  <br/>  Canada Personal Health Identification Number (PHIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Canada PHIA: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Social Insurance Number – Min antal 10, Maks. antal 500  <br/>  Canada Tilstandstjeneste tal – Min.t. 10, Maks. antal 500 <br/>  Canada Personal Health Identification Number (PHIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>Canada Personal Information Protection Act (PIPA)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PIPA: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number – Min antal 1, Maks. antal 9  <br/>  Canada Tilstandstjeneste tal – Min.t. 1, Maks. antal 9  <br/>  Canada Personal Health Identification Number (PHIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Canada PIPA: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada-pasnummer – Antal min. 10, maks. 500  <br/>  Canada Social Insurance Number – Min antal 10, Maks. antal 500  <br/>  Canada Tilstandstjeneste tal – Min.t. 10, Maks. antal 500  <br/>  Canada Personal Health Identification Number (PHIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Canada Personal Information Protection Act (PIPEDA)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PIPEDA: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Kørekortnummer – Min antal 1, Maks. antal 9  <br/>  Canada Bank Account Number – Min antal 1, Maks. antal 9  <br/>  Canada Passport Number – Min antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number – Min antal 1, Maks. antal 9  <br/>  Canada Tilstandstjeneste tal – Min.t. 1, Maks. antal 9  <br/>  Canada Personal Health Identification Number (PHIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Canada PIPEDA: Scan indhold delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Kørekortnummer – Min antal 10, Maks. antal 500 <br/>  Canada Bank Account Number – Min antal 10, Maks. antal 500 <br/>  Canada-pasnummer – Antal min. 10, maks. 500  <br/>  Canada Social Insurance Number – Min antal 10, Maks. antal 500  <br/>  Canada Tilstandstjeneste tal – Min.t. 10, Maks. antal 500  <br/>  Canada Personal Health Identification Number (PHIN) – Min count 10, Max count 500 <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger (PII) i Canada

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PII: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Kørekortnummer – Min antal 1, Maks. antal 9  <br/>  Canada Bank Account Number – Min antal 1, Maks. antal 9  <br/>  Canada Passport Number – Min antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number – Min antal 1, Maks. antal 9  <br/>  Canada Tilstandstjeneste tal – Min.t. 1, Maks. antal 9  <br/>  Canada Personal Health Identification Number (PHIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Canada PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Kørekortnummer – Min antal 10, Maks. antal 500  <br/>  Canada Bank Account Number – Min antal 10, Maks. antal 500  <br/>  Canada-pasnummer – Antal min. 10, maks. 500  <br/>  Canada Social Insurance Number – Min antal 10, Maks. antal 500  <br/>  Canada Tilstandstjeneste tal – Min.t. 10, Maks. antal 500  <br/>  Canada Personal Health Identification Number (PHIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="france-data-protection-act"></a>France Data Protection Act

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Frankrigs DPA: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  France National ID Card (CNI) – Min.t. 1, Maks. antal 9  <br/>  Frankrig Cpr-nummer (INSEE) – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|France DPA: Scan indhold, der er delt uden for – high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  France National ID Card (CNI) – Min count 10, Maks. antal 500  <br/>  France Social Security Number (INSEE) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="france-financial-data"></a>France Financial Data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|France Financial: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  EU-debetkortnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|France Financial: Scan indhold delt uden for – high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  EU-debetkortnummer – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger (PII) i Frankrig

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|France PII: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Frankrig Cpr-nummer (INSEE) – Min.t. 1, Maks. antal 9  <br/>  Frankrig kørekortnummer – Min antal 1, Maks. antal 9  <br/>  Frankrigs pasnummer – Antal min. 1, maks. antal 9  <br/>  France National ID Card (CNI) – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|France PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  France Social Security Number (INSEE) – Min count 10, Max count 500  <br/>  Frankrig Kørekortnummer – Min.t. 10, Maks. antal 500  <br/>  Frankrigs pasnummer – Antal min. 10, maks. 500  <br/>  France National ID Card (CNI) – Min count 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Persondataforordningen (GDPR)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Der blev fundet EU-følsomt indhold med lav volumen  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  EU-debetkortnummer – Antal min. 1, maks. antal 9  <br/>  EU-kørekortnummer – Min. antal 1, Maks. antal 9  <br/>  EU-national identifikationsnummer – Min.t. 1, Maks. antal 9  <br/>  EU-pasnummer – Antal min. 1, maks. 9  <br/>  EU Cpr-nummer (SSN) eller tilsvarende id – Min antal 1, Maks. antal 9  <br/>  EU-skatteidentifikationsnummer (TIN) – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send hændelsesrapporter til administrator  <br/> |
|Der blev fundet en stor mængde følsomt indhold i EU  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  EU-debetkortnummer – Antal min. 10, maks. 500  <br/>  EU-kørekortnummer – Antal min. 10, Maks. antal 500  <br/>  EU-national identifikationsnummer – Min.t. 10, Maks. antal 500  <br/>  EU-pasnummer – Antal min. 10, maks. 500  <br/>  EU-CPR-nummer (SSN) eller tilsvarende id – Min.t. 10, Maks. antal 500  <br/>  EU-skatteidentifikationsnummer (TIN) – Min.t. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Begræns adgangen til indholdet for eksterne brugere  <br/>  Giv brugere besked med mail og politiktip  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapporter til administrator  <br/> |
   
## <a name="germany-financial-data"></a>Finansielle data fra Tyskland

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Finansielle data i Tyskland: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  EU-debetkortnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Finansielle data i Tyskland: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  EU-debetkortnummer – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger (PII) i Tyskland

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Germany PII: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Tysk kørekortnummer – Min. antal 1, Maks. antal 9  <br/>  Tysk pasnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Germany PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Tysk kørekortnummer – Antal min. 10, Maks. antal 500  <br/>  Tysk pasnummer – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="israel-financial-data"></a>Israels finansielle data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Israels finansielle data: Scan indhold delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels bankkontonummer – Antal min. 1, maks. antal 9  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Israels finansielle data: Scan indhold delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels bankkontonummer – Antal min. 10, maks. antal 500  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>Israel personidentificerbare oplysninger (PII)-data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Israels pii: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Israels PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="israel-protection-of-privacy"></a>Israels beskyttelse af personlige oplysninger

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Beskyttelse af personlige oplysninger i Israel: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min antal 1, Maks. antal 9  <br/>  Israels bankkontonummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Israels beskyttelse af personlige oplysninger: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min antal 10, Maks. antal 500  <br/>  Israels bankkontonummer – Antal min. 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="japan-financial-data"></a>Finansielle data for Japan

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Japan Financial: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japan Bankkontonummer – Min. antal 1, maks. antal 9  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Japan Financial: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japan Bankkontonummer – Antal min. 10, Maks. antal 500  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger (PII)-data (Japan Personally Identifiable Information)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Japan PII: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japan Resident Registration Number – Min antal 1, Maks. antal 9  <br/>  Japan Social Insurance Number (SIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Japan PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japan Resident Registration Number – Min count 10, Max count 500  <br/>  Japan Social Insurance Number (SIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Beskyttelse af personlige oplysninger i Japan

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Japansk PPI: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japan Resident Registration Number – Min antal 1, Maks. antal 9  <br/>  Japan Social Insurance Number (SIN) – Min antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Japansk PPI: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japan Resident Registration Number – Min count 10, Max count 500  <br/>  Japan Social Insurance Number (SIN) – Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>FUNKTIONER DatasikkerhedsstandardEN FOR 2010 (FUNKTIONER DSS)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|ETHERNET DSS: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|ETHERNET DSS: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Saudi-Arabien – antit cyberkriminalitetsret

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Saudi-Arabien ACC: Scan indhold delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Internationalt bankkontonummer (IBAN) – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Saudi Arabia ACC: Scan indhold delt uden for – high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  International Banking Account Number (IBAN) – Min antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Finansielle data for Saudi-Arabien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Saudi Arabia Financial: Scan indhold delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Internationalt bankkontonummer (IBAN) – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Saudi Arabia Financial: Scan indhold delt uden for – high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  International Banking Account Number (IBAN) – Min antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger (PII) i Saudi-Arabien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Saudi Arabia PII: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Saudi-Arabiens nationale id – Min antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Saudi Arabia PII: Scan indhold delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Saudi Arabiens nationale id – Min antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>Storbritannien Adgang til Medical Reports Act

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Storbritannien AMRA: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt Tilstandstjeneste – Min.t. 1, Maks. antal 9  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Storbritannien AMRA: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt Tilstandstjeneste – Min.t. 10, Maks. antal 500  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-data-protection-act"></a>Storbritannien Lov om databeskyttelse

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Storbritannien DPA: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 1, Maks. antal 9  <br/>  USA/Storbritannien Pasnummer – Antal min. 1, maks. antal 9  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Storbritannien DPA: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 10, Maks. antal 500  <br/>  USA/Storbritannien Pasnummer – Antal min. 10, maks. 500  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-financial-data"></a>Storbritannien Finansielle data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Storbritannien Finansiel: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  EU-debetkortnummer – Antal min. 1, maks. antal 9  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Storbritannien Finansiel: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  EU-debetkortnummer – Antal min. 10, maks. 500  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>Storbritannien Praksis for brug af PIOCP (Personal Information Online Code of Practice)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Storbritannien PIOCP: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 1, Maks. antal 9  <br/>  Storbritannien Nationalt Tilstandstjeneste – Min.t. 1, Maks. antal 9  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Storbritannien PIOCP: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 10, Maks. antal 500  <br/>  Storbritannien Nationalt Tilstandstjeneste – Min.t. 10, Maks. antal 500  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>Storbritannien Personidentificerbare oplysninger (PII)-data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Storbritannien PII: Scan indhold, der er delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 1, Maks. antal 9  <br/>  USA/Storbritannien Pasnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Storbritannien PII: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Storbritannien Nationalt forsikringsnummer (NINO) – Min.t. 10, Maks. antal 500  <br/>  USA/Storbritannien Pasnummer – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>Storbritannien Bestemmelser om beskyttelse af personlige oplysninger og elektronisk kommunikation

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Storbritannien PECR: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT-kode – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|Storbritannien PECR: Scan indhold, der er delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT-kode – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>Amerikanske nationale forbrugerregler (Federal Trade Commission, FTC)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|AMERIKANSKE FTC-regler: Scan indhold, der deles uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  USA Bankkontonummer – Antal min. 1, Maks. antal 9  <br/>  ABA-registreringsnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|AMERIKANSKE FTC-regler: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  USA Bankkontonummer – Min. antal 10, Maks. antal 500  <br/>  ABA-registreringsnummer – Antal min. 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-financial-data"></a>USA Finansielle data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|USA Finansiel: Scan indhold delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  USA Bankkontonummer – Antal min. 1, Maks. antal 9  <br/>  ABA-registreringsnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|USA Finansiel: Scan indhold delt uden for - high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  USA Bankkontonummer – Min. antal 10, Maks. antal 500  <br/>  ABA-registreringsnummer – Antal min. 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>USA Gramm-Leach-Bliley Act (GLBA)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|AMERIKANSK GLBA: Scan indhold delt uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  USA Bankkontonummer – Antal min. 1, Maks. antal 9  <br/>  USA Individuel skatteyders id-nummer (ITIN) – Min.t. 1, Maks. antal 9  <br/>  USA CPR-nummer – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|AMERIKANSK GLBA: Scan indhold delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  USA Bankkontonummer – Min. antal 10, Maks. antal 500  <br/>  USA Skatteyders id-nummer (ITIN) – Min.t. 10, Maks. antal 500  <br/>  USA CPR-nummer – Min.t. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>USA Health Insurance Act (HIPAA)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Indhold matcher amerikansk HIPAA  <br/> | Indeholder en af følgende følsomme oplysninger:  <br/>  USA CPR-nummer – Min.t. 1, Maks. tæller eventuelle  <br/>  Enforcement Agency (DEA) Number – Min count 1, Max count any  <br/> **AND** <br/>  Indhold indeholder et af disse vilkår:  <br/>  International klassificering af anden kategori (ICD-9-CM) – Antal min. 1, Maks. tæller alle  <br/>  International klassificering af inddelinger (ICD-10-CM) – Min antal 1, Maks. tæl eventuelle  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
   
## <a name="us-patriot-act"></a>USA Den amerikanske 2016-act

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|USA Den amerikanske act: Scan indhold, der deles uden for - low count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  USA Bankkontonummer – Antal min. 1, Maks. antal 9  <br/>  USA Individuel skatteyders id-nummer (ITIN) – Min.t. 1, Maks. antal 9  <br/>  USA CPR-nummer – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|USA Den amerikanske act: Scan indhold delt uden for - high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  USA Bankkontonummer – Min. antal 10, Maks. antal 500  <br/>  USA Skatteyders id-nummer (ITIN) – Min.t. 10, Maks. antal 500  <br/>  USA CPR-nummer – Min.t. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>USA Personidentificerbare oplysninger (PII)-data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|AMERIKANSK PII: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  USA Individuel skatteyders id-nummer (ITIN) – Min.t. 1, Maks. antal 9  <br/>  USA CPR-nummer – Min.t. 1, Maks. antal 9  <br/>  USA/Storbritannien Pasnummer – Antal min. 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|AMERIKANSK PII: Scan indhold delt uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  USA Skatteyders id-nummer (ITIN) – Min.t. 10, Maks. antal 500  <br/>  USA CPR-nummer – Min.t. 10, Maks. antal 500  <br/>  USA/Storbritannien Pasnummer – Antal min. 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>USA Statslige love om meddelelse om sikkerhedsbrud

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|USA's sikkerhedsbrud: Scan indhold, der er delt uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 1, maks. antal 9  <br/>  USA Bankkontonummer – Antal min. 1, Maks. antal 9  <br/>  USA Kørekortnummer – Antal min. 1, Maks. antal 9  <br/>  USA CPR-nummer – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|USA State Breach: Scan indhold delt uden for - high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer – Antal min. 10, Maks. antal 500  <br/>  USA Bankkontonummer – Min. antal 10, Maks. antal 500  <br/>  USA Kørekortnummer – Min.t. 10, Maks. antal 500  <br/>  USA CPR-nummer – Min.t. 10, Maks. antal 500 <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>USA Statslige love om hemmeligholdelse af CPR-nummer

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|USA's SSN-lovgivning: Scan indhold, der deles uden for – lav antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  USA CPR-nummer – Min.t. 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> |Send en meddelelse  <br/> |
|USA's SSN-lovgivning: Scan indhold, der deles uden for - high count  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  USA CPR-nummer – Min.t. 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for organisationen  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   

