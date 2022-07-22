---
title: Definition af virksomhedsnummerenhed i Australien
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
ms.openlocfilehash: a10addd7dee6bc481adbf9edf1380cdedf09bdd0
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944802"
---
# <a name="australia-company-number"></a>Australiens firmanummer

Denne type følsomme oplysninger er kun tilgængelig til brug i:

- politikker til forebyggelse af datatab
- politikker for overholdelse af kommunikation
- administration af datalivscyklus
- datastyring
- Microsoft Defender for Cloud Apps

## <a name="format"></a>Format

ni cifre med afgrænsere

## <a name="pattern"></a>Mønster

ni cifre med afgrænsere:

- tre cifre
- et mellemrum
- tre cifre
- et mellemrum
- tre cifre

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Australian_Company_Number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_Australian_Company_Number.

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Funktionen Func_Australian_Company_Number finder indhold, der svarer til mønsteret.

```xml
      <!-- Australia Company Number -->
      <Entity id="b1fba4f7-7b3e-4bb9-8f9a-9366df604dbb" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Func_Australian_Company_Number" />
          <Match idRef="Keyword_Australian_Company_Number" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Func_Australian_Company_Number" />
        </Pattern>
      </Entity>
```
## <a name="keywords"></a>Søgeord

### <a name="keyword_australia_company_number"></a>Keyword_australia_company_number

- Cna
- det australske firma nej
- det australske firma nej #
- det australske firmanummer
- australsk firma nr.
- australsk firma nr. #
- australsk firmanummer
