---
title: Definition af registreringsnummerenhed for residenter i Sydkorea
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
description: Enhedsdefinitionen for den følsomme informationstype for residenter i Sydkorea.
ms.openlocfilehash: 94de2ebb31e8bd7a0d9c175e318e166da691bbca
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944745"
---
# <a name="south-korea-resident-registration-number"></a>Registreringsnummer for beboere i Sydkorea

## <a name="format"></a>Format

13 cifre, der indeholder en bindestreg

## <a name="pattern"></a>Mønster

13 cifre:

- seks cifre i formatet YYMMDD, som er fødselsdatoen
- en bindestreg
- ét ciffer bestemt af århundredet og køn
- firecifret fødselskode for område
- et ciffer, der bruges til at differentiere personer, for hvem de foregående tal er identiske
- et kontrolciffer.

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_south_korea_resident_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_south_korea_resident_number` .
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_south_korea_resident_number` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

```xml
<!-- South Korea Resident Registration Number -->
<Entity id="5b802e18-ba80-44c4-bc83-bf2ad36ae36a" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Func_south_korea_resident_number"/>
     <Match idRef="Keyword_south_korea_resident_number"/>
  </Pattern>
  <Pattern confidenceLevel="75">
     <IdMatch idRef="Func_south_korea_resident_number"/>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_south_korea_resident_number"></a>Keyword_south_korea_resident_number

- Nationalt id-kort
- Borgerregistreringsnummer
- Jumin deungnok beonho
- RRN
- 주민등록번호