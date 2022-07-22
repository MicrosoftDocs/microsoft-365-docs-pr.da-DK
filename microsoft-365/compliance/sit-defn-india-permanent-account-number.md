---
title: Enhedsdefinition for permanent kontonummer i Indien (PAN)
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
description: Enhedsdefinition af følsomme oplysninger for indiens permanente kontonummer (PAN).
ms.openlocfilehash: bf712e0949bba5f1e5396d61ff70f41b70ba579d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945410"
---
# <a name="india-permanent-account-number-pan"></a>Permanent kontonummer for Indien (PAN)

## <a name="format"></a>Format

10 bogstaver eller cifre

## <a name="pattern"></a>Mønster

10 bogstaver eller cifre:

- Tre bogstaver (skelner ikke mellem store og små bogstaver)
- Et bogstav i C, P, H, F, A, T, B, L, J, G (ikke forskel på store og små bogstaver)
- Et bogstav
- Fire cifre
- Et bogstav, der er et alfabetisk kontrolciffer

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_india_permanent_account_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_india_permanent_account_number` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_india_permanent_account_number` finder indhold, der svarer til mønsteret.

```xml
      <!-- India Permanent Account Number -->
      <Entity id="2602bfee-9bb0-47a5-a7a6-2bf3053e2804" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_india_permanent_account_number" />
          <Match idRef="Keyword_india_permanent_account_number" />
        </Pattern>
        <Version minEngineVersion="15.20.3520.000">
          <Pattern confidenceLevel="65">
            <IdMatch idRef="Regex_india_permanent_account_number" />
          </Pattern>
        </Version>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_india_permanent_account_number"></a>Keyword_india_permanent_account_number

- Permanent kontonummer
- PAN