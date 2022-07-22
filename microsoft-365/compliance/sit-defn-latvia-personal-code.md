---
title: Definition af personligt kodeobjekt i Letland
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
description: Definition af enhed for følsomme oplysninger i letlands personlige kode.
ms.openlocfilehash: 16e736220fa402df6ebcb87e947e75090b4a0f57
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944741"
---
# <a name="latvia-personal-code"></a>Letlands personlige kode

## <a name="format"></a>Format

11 cifre og en valgfri bindestreg

## <a name="pattern"></a>Mønster

Gammelt format

11 cifre og en bindestreg:

- seks cifre, der svarer til fødselsdatoen (DDMMYY)
- en bindestreg
- et ciffer, der svarer til fødselstallet ("0" for det 19. århundrede, "1" for det 20. århundrede og "2" for det 21. århundrede)
- fire cifre, tilfældigt genereret

Nyt format

11 cifre

- To cifre "32"
- Ni cifre

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_latvia_eu_national_id_card` eller regex `Regex_latvia_eu_national_id_card_new_format` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_latvia_eu_national_id_card` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_latvia_eu_national_id_card` eller regex `Regex_latvia_eu_national_id_card_new_format` finder indhold, der svarer til mønsteret.

```xml
      <!-- Latvia Personal Code -->
      <Entity id="03fcf763-27c2-49ed-9422-2641c6c895c9" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_latvia_eu_national_id_card" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Match idRef="Keywords_latvia_eu_national_id_card" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_latvia_eu_national_id_card_new_format" />
          <Any minMatches="0" maxMatches="0">
            <Match idRef="Keywords_latvia_eu_telephone_number" />
            <Match idRef="Keywords_latvia_eu_mobile_number" />
          </Any>
        </Pattern>
      </Entity>

```

## <a name="keywords"></a>Søgeord

### <a name="keywords_latvia_eu_national_id_card"></a>Keywords_latvia_eu_national_id_card

- administrativt nummer
- alvas nē
- fødselsnummer
- borgernummer
- civilt nummer
- elektronisk census-nummer
- elektronisk nummer
- regnskabskode
- sundhedssektorens brugernummer
- Id #
- id-kode
- Identifikationsnummer
- identifikācijas numurs
- id-nummer
- individuelt tal
- latvija alva
- nacionālais-id
- nationalt id
- nationalt identifikationsnummer
- nationalt id-nummer
- det nationale forsikringsnummer
- nationalt registernummer
- nodokļa numurs
- nodokļu id
- nodokļu identifikācija numurs
- personligt certifikatnummer
- personlig kode
- personlig id-kode
- personligt id-nummer
- kode til personlig identifikation
- personligt id
- personligt id-nummer
- personligt nummer
- personlig numerisk kode
- personalcodeno #
- personas kods
- populationsidentifikationskode
- public service-nummer
- registreringsnummer
- omsætningsnummer
- cpr-nummer
- CPR-nummer
- statsskattekode
- skattefilnummer
- moms-id
- momsidentifikation nr.
- moms-id-nummer
- skattenr. #
- skattenr.
- momsnummer
- taxid #
- taxidno #
- taxidnumber #
- taxno #
- momsnummer #
- momsnummer
- tin-id
- tin no
- Tin #
- vælgerens nummer