---
title: Definition af tysklands momsidentifikationsnummerenhed
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
description: Definition af en enhed til registrering af skatteidentifikationsnummer i Tyskland.
ms.openlocfilehash: 38dd5c85e052d0a42886c80eff35dd5e391020b0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944757"
---
# <a name="germany-tax-identification-number"></a>Tysklands skatteidentifikationsnummer

## <a name="format"></a>Format

11 cifre uden mellemrum og afgrænsere

## <a name="pattern"></a>Mønster

11 cifre

- To cifre
- Et valgfrit mellemrum
- Tre cifre
- Et valgfrit mellemrum
- Tre cifre
- Et valgfrit mellemrum
- To cifre
- et kontrolciffer

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_germany_eu_tax_file_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_germany_eu_tax_file_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_germany_eu_tax_file_number` finder indhold, der svarer til mønsteret.

```xml
      <!-- Germany Tax Identification Number -->
      <Entity id="43316a89-9880-40cf-b980-04bc7eefcec5" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
          <Match idRef="Keywords_germany_eu_tax_file_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_germany_eu_tax_file_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_germany_eu_tax_file_number"></a>Keywords_germany_eu_tax_file_number

- identifikationsnummer
- steuer-id
- steueridentifikationsnummer
- steuernummer
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
- Zinn #
- Zinn
- zinnnummer