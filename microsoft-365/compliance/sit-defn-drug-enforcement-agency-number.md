---
title: Definition af nummerenhed for Drug Enforcement Agency (DEA)
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
description: Dea (Drug Enforcement Agency) nummer følsomme oplysninger type enhed definition.
ms.openlocfilehash: 7b1ade056621f619d8be0293708dd51cfc2e85dd
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945449"
---
# <a name="drug-enforcement-agency-dea-number"></a>Dea-nummer (Drug Enforcement Agency)

## <a name="format"></a>Format

to bogstaver efterfulgt af syv cifre

## <a name="pattern"></a>Mønster

Mønsteret skal indeholde alle følgende:

- ét bogstav (skelner ikke mellem store og små bogstaver) fra dette sæt af mulige bogstaver: A/B/F/G/M/P/R, som er en registrantkode
- ét bogstav (ikke forskel på store og små bogstaver), som er det første bogstav i registrantens efternavn eller ciffer '9'
- syv cifre, hvoraf det sidste er kontrolcifferet

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_dea_number` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_dea_number`
- Kontrolsummen passerer.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen `Func_dea_number` finder indhold, der svarer til mønsteret.
- Kontrolsummen passerer.

```xml
    <!-- DEA Number -->
    <Entity id="9a5445ad-406e-43eb-8bd7-cac17ab6d0e4" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="75">
        <IdMatch idRef="Func_dea_number" />
      </Pattern>
      <Version minEngineVersion="15.20.1207.000" maxEngineVersion="15.20.3134.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
        </Pattern>
      </Version>
      <Version minEngineVersion="15.20.3135.000">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_dea_number" />
          <Match idRef="Keyword_dea_number" />
        </Pattern>
      </Version>
    </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_dea_number"></a>Keyword_dea_number

- Dea
- Dea #
- administration af narkotikamisbrug
- drug enforcement agency