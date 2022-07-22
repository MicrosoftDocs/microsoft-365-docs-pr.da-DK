---
title: Definition af momsidentifikationsnummerenhed i Sverige
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
description: Sverige skatteidentifikationsnummer følsomme oplysninger type enhedsdefinition.
ms.openlocfilehash: 872d7d5ca1dd42f7db0861a5dd789a7cce707f86
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944744"
---
# <a name="sweden-tax-identification-number"></a>Sveriges skatteidentifikationsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

10 cifre og et symbol i det angivne mønster

## <a name="pattern"></a>Mønster

10 cifre og et symbol:

- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- et plustegn eller minustegn
- tre cifre, der gør identifikationsnummeret entydigt, hvor:
  - for numre, der er udstedt før 1990, identificerer det syvende og ottende ciffer fødsels amtet eller udenlandske fødte
  - tallet i niende position angiver køn med enten ulige for mand eller endda for kvinde
- et kontrolciffer

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

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

## <a name="keywords"></a>Søgeord

### <a name="keywords_sweden_eu_tax_file_number"></a>Keywords_sweden_eu_tax_file_number

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