---
title: Definition af estisk pasnummerenhed
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
description: Estisk pas nummer følsomme oplysninger type enhedsdefinition.
ms.openlocfilehash: c6170540c12aca27e808ee9e5103dc45f22cbe4c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945437"
---
# <a name="estonia-passport-number"></a>Estisk pasnummer

## <a name="format"></a>Format

ét bogstav efterfulgt af syv cifre uden mellemrum eller afgrænsere

## <a name="pattern"></a>Mønster

ét bogstav efterfulgt af syv cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_estonia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_estonia_eu_passport_number` findes.
- Det regulære udtryk `Regex_eu_passport_date1` finder datoen i formatet DD.MM.YYYY, eller der findes et nøgleord fra `Keywords_eu_passport_date`

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_estonia_eu_passport_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_passport_number` eller `Keywords_estonia_eu_passport_number` findes.

```xml
      <!-- Estonia Passport Number -->
      <Entity id="61f7073a-509e-425b-a754-bc01bb5d5b8c" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_eu_passport_date1" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_estonia_eu_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keywords_estonia_eu_passport_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_eu_passport_number_common"></a>Keywords_eu_passport_number_common

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

### <a name="keywords_estonia_eu_passport_number"></a>Keywords_estonia_eu_passport_number

eesti kodaniku passi number passinumbrid document number document no dokumendi nr

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato