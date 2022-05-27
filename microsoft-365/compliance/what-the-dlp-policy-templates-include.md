---
title: Hvilke DLP-politikskabeloner omfatter
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
description: Få mere at vide om, hvad DLP-politikskabelonerne (forebyggelse af datatab) Microsoft Purview-compliance-portal omfatter.
ms.openlocfilehash: 145f5b2a180023811afa8b5795bfa8b9d24f82f5
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753492"
---
# <a name="what-the-dlp-policy-templates-include"></a>Hvad inkluderes i DLP-politikskabelonerne

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Forebyggelse af datatab (DLP) i Microsoft Purview-compliance-portal indeholder brugsklare politikskabeloner, der løser almindelige krav til overholdelse af angivne standarder, f.eks. at hjælpe dig med at beskytte følsomme oplysninger, der er underlagt HIPAA (U.S. Health Insurance Act), USA. Gramm-Leach-Bliley Act (GLBA) eller U.S. Patriot Act. Denne artikel indeholder en liste over alle politikskabeloner, hvilke typer følsomme oplysninger de søger efter, og hvilke standardbetingelser og handlinger der er. Denne artikel indeholder ikke alle detaljer om, hvordan hver politikskabelon er konfigureret. Artiklen indeholder i stedet tilstrækkelige oplysninger til at hjælpe dig med at beslutte, hvilken skabelon der er det bedste udgangspunkt for dit scenarie. Husk, at du kan tilpasse disse politikskabeloner, så de opfylder dine specifikke krav.
  
## <a name="australia-financial-data"></a>Økonomiske data i Australien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Financial i Australien: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Australiens skattefilnummer – min. antal 1, maks. antal 9  <br/>  Australiens bankkontonummer – min. antal 1, maks. antal 9  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Financial i Australien: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Australiens skattefilnummer – min. antal 10, maks. antal 500  <br/>  Australiens bankkontonummer – min. antal 10, maks. antal 500  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Australia Health Records Act (HRIP Act)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|AUSTRALIEN HRIP: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – min. antal 1, maks. antal 9  <br/>  Medicinsk kontonummer i Australien - min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|HRIP i Australien: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – min. antal 10, maks. antal 500  <br/>  Medicinsk kontonummer i Australien - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger i Australien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Australsk pii: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – min. antal 1, maks. antal 9  <br/>  Australiens kørekortsnummer – min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Australsk pii: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens skattefilnummer – min. antal 10, maks. antal 500  <br/>  Australiens kørekortsnummer – min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="australia-privacy-act"></a>Australiens lov om beskyttelse af personlige oplysninger

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Beskyttelse af personlige oplysninger i Australien: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens kørekortsnummer – min. antal 1, maks. antal 9  <br/>  Australia Passport Number – Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Beskyttelse af personlige oplysninger i Australien: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Australiens kørekortsnummer – min. antal 10, maks. antal 500  <br/>  Australia Passport Number – Min. antal 10, Maks. antal 500 <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-financial-data"></a>Finansielle data for Canada

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Finansielle data for Canada: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Canadas bankkontonummer – min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Finansielle data for Canada: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Canadas bankkontonummer – min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Canada Health Information Act (HIA)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada HIA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min. antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number - Min count 1, Max count 9  <br/>  Canada Tilstandstjeneste number – Min. antal 1, maks. antal 9  <br/>  PhIN (Canada Personal Health Identification Number) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Canada HIA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min. antal 10, Maks. antal 500  <br/>  Canada Social Insurance Number - Min count 10, Max count 500  <br/>  Canada Tilstandstjeneste number – Min. antal 10, maks. antal 500  <br/>  Phin (Personal Health Identification Number– Canada Personal Health Identification Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Canada Personal Health Act (PHIPA) – Ontario

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PHIPA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min. antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number - Min count 1, Max count 9  <br/>  Canada Tilstandstjeneste number – Min. antal 1, maks. antal 9  <br/>  PhIN (Canada Personal Health Identification Number) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Canada PHIPA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min. antal 10, Maks. antal 500  <br/>  Canada Social Insurance Number - Min count 10, Max count 500  <br/>  Canada Tilstandstjeneste number – Min. antal 10, maks. antal 500  <br/>  Phin (Personal Health Identification Number– Canada Personal Health Identification Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Canada Personal Health Information Act (PHIA) – Manitoba

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PHIA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Social Insurance Number - Min count 1, Max count 9  <br/>  Canada Tilstandstjeneste number – Min. antal 1, maks. antal 9  <br/>  PhIN (Canada Personal Health Identification Number) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Canada PHIA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Social Insurance Number - Min count 10, Max count 500  <br/>  Canada Tilstandstjeneste number – Min. antal 10, maks. antal 500 <br/>  Phin (Personal Health Identification Number– Canada Personal Health Identification Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>PIPA (Canada Personal Information Protection Act)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PIPA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min. antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number - Min count 1, Max count 9  <br/>  Canada Tilstandstjeneste number – Min. antal 1, maks. antal 9  <br/>  PhIN (Canada Personal Health Identification Number) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Canada PIPA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Passport Number – Min. antal 10, Maks. antal 500  <br/>  Canada Social Insurance Number - Min count 10, Max count 500  <br/>  Canada Tilstandstjeneste number – Min. antal 10, maks. antal 500  <br/>  Phin (Personal Health Identification Number– Canada Personal Health Identification Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Pipeda (Canada Personal Information Protection Act)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PIPEDA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Driver's License Number - Min count 1, Max count 9  <br/>  Canadas bankkontonummer – min. antal 1, maks. antal 9  <br/>  Canada Passport Number – Min. antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number - Min count 1, Max count 9  <br/>  Canada Tilstandstjeneste number – Min. antal 1, maks. antal 9  <br/>  PhIN (Canada Personal Health Identification Number) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Canada PIPEDA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Driver's License Number - Min count 10, Max count 500 <br/>  Canadas bankkontonummer – min. antal 10, maks. antal 500 <br/>  Canada Passport Number – Min. antal 10, Maks. antal 500  <br/>  Canada Social Insurance Number - Min count 10, Max count 500  <br/>  Canada Tilstandstjeneste number – Min. antal 10, maks. antal 500  <br/>  Phin (Personal Health Identification Number– Canada Personal Health Identification Number) – Min. antal 10, maks. antal 500 <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger om Canada

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Canada PII: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Driver's License Number - Min count 1, Max count 9  <br/>  Canadas bankkontonummer – min. antal 1, maks. antal 9  <br/>  Canada Passport Number – Min. antal 1, Maks. antal 9  <br/>  Canada Social Insurance Number - Min count 1, Max count 9  <br/>  Canada Tilstandstjeneste number – Min. antal 1, maks. antal 9  <br/>  PhIN (Canada Personal Health Identification Number) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Canada PII: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Canada Driver's License Number - Min count 10, Max count 500  <br/>  Canadas bankkontonummer – min. antal 10, maks. antal 500  <br/>  Canada Passport Number – Min. antal 10, Maks. antal 500  <br/>  Canada Social Insurance Number - Min count 10, Max count 500  <br/>  Canada Tilstandstjeneste number – Min. antal 10, maks. antal 500  <br/>  Phin (Personal Health Identification Number– Canada Personal Health Identification Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="france-data-protection-act"></a>Den franske lov om databeskyttelse

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|DPA i Frankrig: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Nationalt id-kort for Frankrig (CNI) – min. antal 1, maks. antal 9  <br/>  Frankrigs cpr-nummer (INSEE) – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|DPA i Frankrig: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Nationalt id-kort for Frankrig (CNI) – min. antal 10, maks. antal 500  <br/>  Frankrig Cpr-nummer (INSEE) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="france-financial-data"></a>Finansielle data for Frankrig

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|France Financial: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  EU-debetkortnummer – min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|France Financial: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  EU-debetkortnummer – min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger i Frankrig

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|France PII: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Frankrigs cpr-nummer (INSEE) – Min. antal 1, maks. antal 9  <br/>  France Driver's License Number – Min count 1, Max count 9  <br/>  France Passport Number – Min. antal 1, Maks. antal 9  <br/>  Nationalt id-kort for Frankrig (CNI) – min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|France PII: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Frankrig Cpr-nummer (INSEE) – Min. antal 10, maks. antal 500  <br/>  France Driver's License Number – Min count 10, Max count 500  <br/>  France Passport Number – Min. antal 10, Maks. antal 500  <br/>  Nationalt id-kort for Frankrig (CNI) – min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Generel forordning om databeskyttelse (GDPR)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Der blev fundet lavt indhold, der er følsomt for EU  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  EU-debetkortnummer – min. antal 1, maks. antal 9  <br/>  EU-kørekortsnummer – Min. antal 1, maks. antal 9  <br/>  EU-nationalt identifikationsnummer - Minimumantal 1, Maks. antal 9  <br/>  EU-pasnummer - Min. antal 1, Maks. antal 9  <br/>  EU-cpr-nummer (SSN) eller tilsvarende id – Min. antal 1, Maks. antal 9  <br/>  EU-skatteidentifikationsnummer (TIN) – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send hændelsesrapporter til administrator  <br/> |
|Stor mængde følsomt INDHOLD fra EU blev fundet  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  EU-debetkortnummer – min. antal 10, maks. antal 500  <br/>  EU-kørekortsnummer – Min. antal 10, maks. antal 500  <br/>  EU-nationalt identifikationsnummer – Minimumantal 10, Maks. antal 500  <br/>  EU-pasnummer – Minimumantal 10, Maks. antal 500  <br/>  EU-cpr-nummer (SSN) eller tilsvarende id – Min. antal 10, maks. antal 500  <br/>  EU-skatteidentifikationsnummer (TIN) – Minimumantal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Begræns adgang til indholdet for eksterne brugere  <br/>  Giv brugerne besked med mail- og politiktips  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapporter til administrator  <br/> |
   
## <a name="germany-financial-data"></a>Finansielle data for Tyskland

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Finansielle data i Tyskland: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  EU-debetkortnummer – min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Germany Financial Data: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  EU-debetkortnummer – min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger i Tyskland

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Germany PII: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Tysk kørekortsnummer - min. antal 1, maks. antal 9  <br/>  Tysk Pasnummer - Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Germany PII: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Tysk kørekortsnummer - min. antal 10, maks. antal 500  <br/>  Tysk Pasnummer - Min. antal 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="israel-financial-data"></a>Økonomiske data for Israel

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Økonomiske data for Israel: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels bankkontonummer - min. antal 1, maks. antal 9  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Økonomiske data for Israel: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels bankkontonummer – min. antal 10, maks. antal 500  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>Personidentificerbare israelsk-oplysninger

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Israelsk pii: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min. antal 1, Maks. 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Israelsk pii: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min. antal 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="israel-protection-of-privacy"></a>Israel beskyttelse af privatlivets fred

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Israels beskyttelse af personlige oplysninger: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min. antal 1, Maks. 9  <br/>  Israels bankkontonummer - min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Israels beskyttelse af personlige oplysninger: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Israels nationale id – Min. antal 10, maks. 500  <br/>  Israels bankkontonummer – min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="japan-financial-data"></a>Økonomiske data for Japan

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Japan Financial: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japans bankkontonummer - min. antal 1, maks. antal 9  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Japan Financial: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Japans bankkontonummer - min. antal 10, maks. antal 500  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger i Japan

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Japan PII: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Registreringsnummer for beboere i Japan - Min. antal 1, Maks. antal 9  <br/>  Japan Social Insurance Number (SIN) - Min count 1, Max count 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Japan PII: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Registreringsnummer for beboere i Japan - Min. antal 10, maks. antal 500  <br/>  Japan Social Insurance Number (SIN) - Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Japan Beskyttelse af personlige oplysninger

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Japan PPI: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Registreringsnummer for beboere i Japan - Min. antal 1, Maks. antal 9  <br/>  Japan Social Insurance Number (SIN) - Min count 1, Max count 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Japan PPI: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Registreringsnummer for beboere i Japan - Min. antal 10, maks. antal 500  <br/>  Japan Social Insurance Number (SIN) - Min count 10, Max count 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>PCI Data Security Standard (PCI DSS)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|PCI DSS: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|PCI DSS: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Saudi-Arabien – lov om bekæmpelse af cyberkriminalitet

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Saudi-Arabien ACC: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Internationalt bankkontonummer (IBAN) – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Saudi-Arabien ACC: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Internationalt bankkontonummer (IBAN) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Saudi-Arabiens finansielle data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Saudi Arabia Financial: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Internationalt bankkontonummer (IBAN) – Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Saudi-Arabien Financial: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Internationalt bankkontonummer (IBAN) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Personidentificerbare oplysninger i Saudi-Arabien

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Saudi-Arabien-pii: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Saudi-Arabiens nationale id – Min. antal 1, Maks. 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Saudi-Arabien-pii: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Saudi-Arabiens nationale id – Min. antal 10, maks. 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>STORBRITANNIEN. Lov om adgang til lægerapporter

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|STORBRITANNIEN. AMRA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. Nationalt Tilstandstjeneste tal – Min. antal 1, maks. antal 9  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|STORBRITANNIEN. AMRA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. Nationalt Tilstandstjeneste nummer – Min. antal 10, maks. antal 500  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 10, Maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-data-protection-act"></a>STORBRITANNIEN. Databeskyttelseslov

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|STORBRITANNIEN. DPA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 1, Maks. antal 9  <br/>  Amerikansk/britisk Passport-nummer - Min. antal 1, Maks. antal 9  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|STORBRITANNIEN. DPA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 10, Maks. antal 500  <br/>  Amerikansk/britisk Passport-nummer - Min. antal 10, maks. antal 500  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-financial-data"></a>STORBRITANNIEN. Finansielle data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|STORBRITANNIEN. Økonomisk: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  EU-debetkortnummer – min. antal 1, maks. antal 9  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|STORBRITANNIEN. Økonomisk: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  EU-debetkortnummer – min. antal 10, maks. antal 500  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>STORBRITANNIEN. Piocp (Personal Information Online Code of Practice)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|STORBRITANNIEN. PIOCP: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 1, Maks. antal 9  <br/>  STORBRITANNIEN. Nationalt Tilstandstjeneste tal – Min. antal 1, maks. antal 9  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|STORBRITANNIEN. PIOCP: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 10, Maks. antal 500  <br/>  STORBRITANNIEN. Nationalt Tilstandstjeneste nummer – Min. antal 10, maks. antal 500  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>STORBRITANNIEN. Personidentificerbare oplysninger

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|STORBRITANNIEN. PII: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 1, Maks. antal 9  <br/>  Amerikansk/britisk Passport-nummer - Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|STORBRITANNIEN. PII: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  STORBRITANNIEN. NINO (National Insurance Number) - Min count 10, Maks. antal 500  <br/>  Amerikansk/britisk Passport-nummer - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>STORBRITANNIEN. Bestemmelser om beskyttelse af personlige oplysninger og elektronisk kommunikation

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|STORBRITANNIEN. PECR: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT Code – Minimumantal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|STORBRITANNIEN. PECR: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SWIFT Code – Minimumantal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>FTC-forbrugerregler (U.S. Federal Trade Commission)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Amerikanske FTC-regler: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Amerikansk bankkontonummer – Min. antal 1, maks. antal 9  <br/>  ABA-routingnummer - Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Amerikanske FTC-regler: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Amerikansk bankkontonummer – min. antal 10, maks. antal 500  <br/>  ABA-routingnummer – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-financial-data"></a>Amerikanske finansielle data

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Amerikansk økonomi: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Amerikansk bankkontonummer – Min. antal 1, maks. antal 9  <br/>  ABA-routingnummer - Min. antal 1, maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Amerikansk økonomi: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Amerikansk bankkontonummer – min. antal 10, maks. antal 500  <br/>  ABA-routingnummer – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>U.S. Gramm-Leach-Bliley Act (GLBA)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|AMERIKANSK GLBA: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Amerikansk bankkontonummer – Min. antal 1, maks. antal 9  <br/>  Id-nummer for individuelle amerikanske skatteborgere (ITIN) – Minimumantal 1, Maks. antal 9  <br/>  SSN (US Social Security Number) – Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|AMERIKANSK GLBA: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Amerikansk bankkontonummer – min. antal 10, maks. antal 500  <br/>  Id-nummer for individuelle amerikanske skatteborgere (ITIN) – Minimumantal 10, Maks. antal 500  <br/>  SSN (US Social Security Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>HIPAA (U.S. Health Insurance Act)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Indhold svarer til USA's HIPAA  <br/> | Indeholder en af følgende følsomme oplysninger:  <br/>  SSN (U.S. Social Security Number) – Min. antal 1, Maks. antal alle  <br/>  Drug Enforcement Agency (DEA) Number – Min count 1, Max count any  <br/> **OG** <br/>  Indhold indeholder et af disse ord:  <br/>  International klassificering af sygdomme (ICD-9-CM) - Min. antal 1, Maks. antal alle  <br/>  International klassificering af sygdomme (ICD-10-CM) - Min. antal 1, Maks. antal alle  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
   
## <a name="us-patriot-act"></a>U.S. Patriot Act

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|U.S. Patriot Act: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Amerikansk bankkontonummer – Min. antal 1, maks. antal 9  <br/>  Id-nummer for individuelle amerikanske skatteborgere (ITIN) – Minimumantal 1, Maks. antal 9  <br/>  SSN (US Social Security Number) – Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|U.S. Patriot Act: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Amerikansk bankkontonummer – min. antal 10, maks. antal 500  <br/>  Id-nummer for individuelle amerikanske skatteborgere (ITIN) – Minimumantal 10, Maks. antal 500  <br/>  SSN (US Social Security Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>Amerikanske personidentificerbare oplysninger (PII-data)

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Amerikansk pii: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Id-nummer for individuelle amerikanske skatteborgere (ITIN) – Minimumantal 1, Maks. antal 9  <br/>  SSN (US Social Security Number) – Min. antal 1, Maks. antal 9  <br/>  Amerikansk/britisk Passport-nummer - Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Amerikansk pii: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Id-nummer for individuelle amerikanske skatteborgere (ITIN) – Minimumantal 10, Maks. antal 500  <br/>  SSN (US Social Security Number) – Min. antal 10, maks. antal 500  <br/>  Amerikansk/britisk Passport-nummer - Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>U.S. State Breach Notification Laws

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Brud på amerikanske stater: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 1, maks. antal 9  <br/>  Amerikansk bankkontonummer – Min. antal 1, maks. antal 9  <br/>  Amerikansk kørekortsnummer – min. antal 1, maks. antal 9  <br/>  SSN (US Social Security Number) – Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Brud på amerikanske stater: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  Kreditkortnummer - Min. antal 10, maks. antal 500  <br/>  Amerikansk bankkontonummer – min. antal 10, maks. antal 500  <br/>  Amerikansk kørekortsnummer – Min. antal 10, maks. antal 500  <br/>  SSN (US Social Security Number) – Min. antal 10, maks. antal 500 <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>Den amerikanske stat Love om fortrolighed af cpr-nummer

|**Regelnavn**|**Betingelser  <br/> (herunder typer af følsomme oplysninger)**|**Handlinger**|
|:-----|:-----|:-----|
|Amerikanske SSN-love: Scan indhold, der deles uden for – lavt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SSN (US Social Security Number) – Min. antal 1, Maks. antal 9  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> |Send en meddelelse  <br/> |
|Amerikanske SSN-love: Scan indhold, der deles uden for – højt antal  <br/> | Indhold indeholder følsomme oplysninger:  <br/>  SSN (US Social Security Number) – Min. antal 10, maks. antal 500  <br/>  Indhold deles med:  <br/>  Personer uden for min organisation  <br/> | Bloker adgang til indhold  <br/>  Send en meddelelse  <br/>  Tillad tilsidesættelse  <br/>  Kræv forretningsberettigelse  <br/>  Send hændelsesrapport  <br/> |
   

