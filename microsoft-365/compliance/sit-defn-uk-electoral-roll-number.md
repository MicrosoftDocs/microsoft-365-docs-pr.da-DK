---
title: STORBRITANNIEN. definition af valglister for nummerenhed
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
description: STORBRITANNIEN. definition af en enhedsdefinition af valglister nummerfølsom informationstype.
ms.openlocfilehash: d821878a155ec6c2393150265ddac1dc18fc5f10
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944830"
---
# <a name="uk-electoral-roll-number"></a>STORBRITANNIEN. valglister

## <a name="format"></a>Format

to bogstaver efterfulgt af 1-4 cifre

## <a name="pattern"></a>Mønster

to bogstaver (skelner ikke mellem store og små bogstaver) efterfulgt af 1-4 tal

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_uk_electoral` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_uk_electoral` .

```xml
<!-- U.K. Electoral Number -->
<Entity id="a3eea206-dc0c-4f06-9e22-aa1be3059963" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_uk_electoral" />
        <Any minMatches="1">
          <Match idRef="Keyword_uk_electoral" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_uk_electoral"></a>Keyword_uk_electoral

- nominering af råd
- nomineringsformular
- valgregister
- valglister