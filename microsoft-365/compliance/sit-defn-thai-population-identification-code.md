---
title: Enhedsdefinition for thai populationidentifikationskode
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
description: Enhedsdefinitionen for den følsomme oplysningstype for thailandsk populationidentifikationskode.
ms.openlocfilehash: ee1e4c5989a3c60ac07bf3f0fef8159413251185
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945464"
---
# <a name="thai-population-identification-code"></a>Thai population-id-kode

## <a name="format"></a>Format

13 cifre

## <a name="pattern"></a>Mønster

13 cifre:

- det første ciffer ikke er nul eller ni
- 12 cifre

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_Thai_Citizen_Id` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_Thai_Citizen_Id` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_Thai_Citizen_Id` finder indhold, der svarer til mønsteret.

```xml
<!-- Thai Citizen ID -->
-<Entity id="44ca9e86-ead7-4c5d-884a-e2eaa401515e" recommendedConfidence="75" patternsProximity="300">
   -<Pattern confidenceLevel="85">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
      <Match idRef="Keyword_Thai_Citizen_Id"/>
   </Pattern>
   -<Pattern confidenceLevel="75">
      <IdMatch idRef="Func_Thai_Citizen_Id"/>
   </Pattern>
</Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_thai_citizen_id"></a>Keyword_thai_citizen_Id

- Id-nummer
- Identifikationsnummer
- บัตรประชาชน
- รหัสบัตรประชาชน
- บัตรประชาชน
- รหัสบัตรประชาชน