---
title: Definition af indiens GST-nummerobjekt
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
description: Objektdefinitionen for den indiske GST-nummerfølsom informationstype.
ms.openlocfilehash: 19d51294b8ff53b53bceba1a047976802359f09e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945413"
---
# <a name="india-gst-number"></a>IndienST-nummer

## <a name="format"></a>Format

Alfanumerisk mønster på 15 tegn

## <a name="pattern"></a>Mønster

15 bogstaver eller cifre:

- to cifre, der repræsenterer gyldig tilstandskode
- et valgfrit mellemrum eller en streg
- ti tegn, der repræsenterer permanent kontonummer (PAN)
- et bogstav eller et ciffer
- et valgfrit mellemrum eller en streg
- et bogstav 'z' eller 'Z'
- et valgfrit mellemrum eller en streg
- et kontrolciffer

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_india_gst_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_india_gst_number` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_india_gst_number` finder indhold, der svarer til mønsteret.

```xml
    <!-- India GST number  -->
      <Entity id="9f5a721c-2fd2-446a-a27e-0c02fbe4630c" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_india_gst_number" />
          <Match idRef="Keyword_india_gst_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_india_gst_number" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_india_gst_number"></a>Keyword_india_gst_number

- Gst
- gstin
- skat på varer og tjenesteydelser
- vare- og tjenesteskat