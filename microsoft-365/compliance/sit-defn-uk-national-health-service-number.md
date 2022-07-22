---
title: STORBRITANNIEN. definition af national sundhedstjenestenummerenhed
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
description: STORBRITANNIEN. nationale sundhedstjeneste nummer følsomme oplysninger type enhedsdefinition.
ms.openlocfilehash: d636be281b1652934fa7b4b83b3a4b5da7794a09
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944829"
---
# <a name="uk-national-health-service-number"></a>STORBRITANNIEN. nummer på det nationale sundhedsvæsen

## <a name="format"></a>Format

10-17 cifre adskilt af mellemrum

## <a name="pattern"></a>Mønster

10-17 cifre:

- enten 3 eller 10 cifre
- et mellemrum
- tre cifre
- et mellemrum
- fire cifre

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_uk_nhs_number` finder indhold, der svarer til mønsteret.
- Et af følgende er sandt:
    - Der blev fundet et nøgleord fra `Keyword_uk_nhs_number` .
    - Der blev fundet et nøgleord fra `Keyword_uk_nhs_number1` .
    - Der blev fundet et nøgleord fra `Keyword_uk_nhs_number_dob` .
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

## <a name="keywords"></a>Søgeord

### <a name="keyword_uk_nhs_number"></a>Keyword_uk_nhs_number

- nationale sundhedstjenester
- Nhs
- sundhedstjenestemyndighed
- sundhedsmyndighed

### <a name="keyword_uk_nhs_number1"></a>Keyword_uk_nhs_number1

- patient-id
- patientidentifikation
- patientnr.
- patientnummer

### <a name="keyword_uk_nhs_number_dob"></a>Keyword_uk_nhs_number_dob

- GP
- DOB
- D.O.B
- Fødselsdag
- Fødselsdato