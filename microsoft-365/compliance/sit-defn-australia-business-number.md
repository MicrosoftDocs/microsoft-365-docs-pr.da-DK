---
title: Definition af virksomhedsnummerobjekt i Australien
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
description: Objektdefinition af virksomhedsnummerfølsom informationstype i Australien.
ms.openlocfilehash: 5d3b238dc631086be26399e3adf6c4fa2ef0cf99
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944806"
---
# <a name="australia-business-number"></a>Australiens forretningsnummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

11 cifre med valgfri afgrænsere

## <a name="pattern"></a>Mønster

11 cifre med valgfri afgrænsere:

- to cifre
- en valgfri bindestreg eller et mellemrum
- tre cifre
- en valgfri bindestreg eller et mellemrum
- tre cifre
- en valgfri bindestreg eller et mellemrum
- tre cifre

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_australian_business_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keywords_australian_business_number.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Funktionen Func_australian_business_number finder indhold, der svarer til mønsteret.

```xml
      <!-- Australia Business Number -->
      <Entity id="76e83b3b-01ee-4530-aced-e667a6609f49" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_australian_business_number" />
          <Match idRef="Keywords_australian_business_number" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Func_australian_business_number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Søgeord

### <a name="keyword_australia_business_number"></a>Keyword_australia_business_number

- australiens forretningsnr.
- forretningsnummer
- Abn #
- Businessid #
- firma-id
- Abn
- businessno #