---
title: Definition af maltas pasnummerenhed
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
description: Definition af enhed for følsomme oplysninger for pasnummer i Malta.
ms.openlocfilehash: bd27a424f76643218f145564b18d84262ed26d3c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944821"
---
# <a name="malta-passport-number"></a>Pasnummer til Malta

## <a name="format"></a>Format

syv cifre uden mellemrum eller afgrænsere

## <a name="pattern"></a>Mønster

syv cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_malta_eu_passport_number` findes.
- Der blev fundet et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_malta_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_malta_eu_passport_number` findes.

```xml
      <!-- Malta Passport Number -->
      <Entity id="b2b21198-48f9-4d13-b2a5-03969bff0fb8" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
          <Match idRef="Keywords_eu_passport_date" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_malta_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_malta_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_eu_passport_number"></a>Keywords_eu_passport_number

- Passport #
- Passport #
- passportid
- Pas
- passportno
- pasnr.
- passportnumber
- pasnummer
- passportnumbers
- pasnumre

### <a name="keywords_malta_eu_passport_number"></a>Keywords_malta_eu_passport_number

- numru tal-passaport
- numri tal-passaport
- Nru tal-passaport

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato