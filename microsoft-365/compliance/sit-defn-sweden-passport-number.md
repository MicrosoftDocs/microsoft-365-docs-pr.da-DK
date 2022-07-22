---
title: Definition af den svenske pasnummerenhed
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
description: Sverige pas nummer følsomme oplysninger type enhed definition.
ms.openlocfilehash: 497965aea803a162fc97bb64fa456191f8788aab
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944743"
---
# <a name="sweden-passport-number"></a>Sveriges pasnummer

## <a name="format"></a>Format

otte cifre

## <a name="pattern"></a>Mønster

otte cifre i træk

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- det regulære udtryk Regex_sweden_passport_number finder indhold, der svarer til mønsteret.
- et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_sweden_passport` findes.
- det regulære udtryk `Regex_sweden_eu_passport_date` finder en dato i formatet DD MMM/MMM YYY (01 JAN/JAN 12), eller der findes et nøgleord fra `Keywords_eu_passport_date` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- det regulære udtryk Regex_sweden_passport_number finder indhold, der svarer til mønsteret.
- et nøgleord fra `Keywords_eu_passport_number` eller `Keyword_sweden_passport` findes.

```xml
    <!-- Sweden Passport Number -->
    <Entity id="ba4e7456-55a9-4d89-9140-c33673553526" patternsProximity="300" recommendedConfidence="75">
      <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
          </Any>
          <Any minMatches="1">
            <Match idRef="Regex_sweden_eu_passport_date" />
            <Match idRef="Keywords_eu_passport_date" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_sweden_passport_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_passport_number" />
            <Match idRef="Keyword_sweden_passport" />
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

### <a name="keyword_sweden_passport"></a>Keyword_sweden_passport

- registreringskort for fremmed person
- g3 behandlingsgebyrer
- flere indgange
- Numéro de passeport
- passeport n °
- passeport ikke
- passeport #
- passeport #
- passeportnon
- passeportn °
- passnummer
- gennemløb nr.
- schengenvisum
- schengenvisum
- enkelt post
- sverigepas
- Visumkrav
- behandling af visum
- visumtype

### <a name="keywords_eu_passport_date"></a>Keywords_eu_passport_date

- udstedelsesdato
- udløbsdato