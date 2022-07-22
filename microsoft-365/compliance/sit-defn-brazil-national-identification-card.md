---
title: RG-enhedsdefinition (national identifikationskort) i Brasilien
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
description: RG(national identifikationskort) definition af følsomme oplysninger.
ms.openlocfilehash: 7f4fe7a0eda911639c0c7650d4ac71f07dfe4f3a
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944782"
---
# <a name="brazil-national-identification-card-rg"></a>Nationalt id-kort for Brasilien (RG)

## <a name="format"></a>Format

Registro Geral (gammelt format): Ni cifre

Registro de Identidade (RIC) (nyt format): 11 cifre

### <a name="pattern"></a>Mønster

Registro Geral (gammelt format):

- to cifre
- et punktum
- tre cifre
- et punktum
- tre cifre
- en bindestreg
- et ciffer, der er et kontrolciffer

Registro de Identidade (RIC) (nyt format):

- 10 cifre
- en bindestreg
- et ciffer, der er et kontrolciffer

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen `Func_brazil_rg` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_brazil_rg` .
- Kontrolsummen passerer.

```xml
      <!-- Brazil National ID Card (RG) -->
      <Entity id="486de900-db70-41b3-a886-abdf25af119c" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_brazil_rg" />
          <Match idRef="Keyword_brazil_rg" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_brazil_rg"></a>Keyword_brazil_rg

- Cédula de identidade
- Identitetskort
- nationalt id
- número de rregistro
- registro de Iidentidade
- registro geral
- RG (dette nøgleord skelner mellem store og små bogstaver)
- RIC (dette nøgleord skelner mellem store og små bogstaver)