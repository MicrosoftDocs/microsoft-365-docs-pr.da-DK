---
title: Enhedsdefinition for personidentifikationskode i Estland
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
description: Enhedsdefinition af følsomme oplysninger i estlands personlige identifikationskode.
ms.openlocfilehash: 866c78a871f0d402cab49783b43e770328b32b1d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945425"
---
# <a name="estonia-personal-identification-code"></a>Estlands personlige identifikationskode

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

11 cifre uden mellemrum og afgrænsere

## <a name="pattern"></a>Mønster

11 cifre:

- et ciffer, der svarer til køn og fødsels århundrede (ulige antal mænd, lige antal kvinder, 1-2: 19. århundrede, 3-4: 20. århundrede, 5-6: 21. århundrede)
- seks cifre, der svarer til fødselsdatoen (YYMMDD)
- tre cifre, der svarer til et serienummer, der adskiller personer født på samme dato
- et kontrolciffer

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_estonia_eu_national_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_estonia_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_estonia_eu_national_id_card` finder indhold, der svarer til mønsteret.

```xml
      <!-- Estonia Personal Identification Code -->
      <Entity id="bfb26de6-dad5-4d48-ab72-4789cdd0654c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Match idRef="Keywords_estonia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_estonia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_estonia_eu_telephone_number" />
            <Match idRef="Keywords_estonia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_estonia_eu_national_id_card"></a>Keywords_estonia_eu_national_id_card

- id-kaart
- Ik
- isikukood #
- isikukood
- maksu-id
- maksukohustuslase identifitseerimisnumber
- maksunumber
- nationalt identifikationsnummer
- nationalt nummer
- personlig kode
- personligt id-nummer
- kode til personlig identifikation
- personligt identifikationsnummer
- personalidnumber #
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