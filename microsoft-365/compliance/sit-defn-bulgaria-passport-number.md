---
title: Definition af pasnummerenhed for Bulgarien
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
description: Bulgarien passport nummer følsomme oplysninger type enhed definition.
ms.openlocfilehash: 7300b34ee9e550293764a58fe7a3e401ae5e86d3
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944774"
---
# <a name="bulgaria-passport-number"></a>Bulgariens pasnummer

## <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

## <a name="pattern"></a>Mønster

ni cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_bulgaria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_bulgaria_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_bulgaria_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_bulgaria_eu_passport_number` findes.

```xml
      <!-- Bulgaria Passport Number -->
      <Entity id="f7172b82-c588-4216-845e-4e54e397f29a" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_bulgaria_eu_passport_number" />
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

### <a name="keywords_bulgaria_eu_passport_number"></a>Keywords_bulgaria_eu_passport_number

- номер на паспорта
- номер на паспорт
- паспорт Nej

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato