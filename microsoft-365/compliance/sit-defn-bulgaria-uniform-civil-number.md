---
title: Ensartet definition af civilnummerering i Bulgarien
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
description: Bulgarien ensartet definition af enhed for personnummerfølsom informationstype.
ms.openlocfilehash: 95bbe1368ca4d6d91d98d07f5cd1c48029fd8499
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944773"
---
# <a name="bulgaria-uniform-civil-number"></a>Bulgariens ensartede civilnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

10 cifre uden mellemrum og afgrænsere

## <a name="pattern"></a>Mønster

10 cifre uden mellemrum og afgrænsere

- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- to cifre, der svarer til fødselsrækkefølgen
- ét ciffer, der svarer til køn: Et lige ciffer for mand og et ulige ciffer for kvinder
- et kontrolciffer

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_bulgaria_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_bulgaria_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_bulgaria_eu_national_id_card` finder indhold, der svarer til mønsteret.

```xml
      <!-- Bulgaria Uniform Civil Number -->
      <Entity id="100d58b1-0a35-4fb1-aa89-e4a86fb53fcc" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Match idRef="Keywords_bulgaria_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_bulgaria_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_bulgaria_eu_telephone_number" />
            <Match idRef="Keywords_bulgaria_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_bulgaria_eu_national_id_card"></a>Keywords_bulgaria_eu_national_id_card

- bnn #
- bnn
- bucn #
- bucn
- edinen grazhdanski nomer
- egn #
- egn
- Identifikationsnummer
- nationalt id
- nationalt nummer
- nationalt nummer #
- nationalt nummer
- personligt id
- personligt nej
- personligt nummer
- personalidnumber #
- CPR-nummer
- Ssn #
- Ssn
- ensartet civilt id
- ensartet civilt nr.
- et ensartet civilt nummer
- uniformcivilno #
- uniformcivilno
- uniformcivilnumber #
- uniformcivilnumber
- entydigt statsborgerskabsnummer
- егн #
- егн
- единен граждански номер
- идентификационен номер
- личен номер
- лична идентификация
- лично не
- национален номер
- номер на гражданството
- униформ id
- униформ граждански id
- униформ граждански не
- униформ граждански номер
- униформгражданскиid #
- униформгражданскине. #