---
title: DEFINITION af SWIFT-kodeenhed
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
description: ENHEDSdefinition af følsomme oplysninger for SWIFT-kode.
ms.openlocfilehash: b1bbadf8f2b56218a90eec1cfd2fac7d550efe0e
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944740"
---
# <a name="swift-code"></a>SWIFT-kode

## <a name="format"></a>Format

fire bogstaver efterfulgt af 5-31 bogstaver eller cifre

## <a name="pattern"></a>Mønster

fire bogstaver efterfulgt af 5-31 bogstaver eller cifre:

- bankkode på fire bogstaver (skelner ikke mellem store og små bogstaver)
- et valgfrit mellemrum
- 4-28 bogstaver eller cifre (det grundlæggende bankkontonummer (BBAN))
- et valgfrit mellemrum
- et til tre bogstaver eller cifre (resten af BBAN)

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_swift` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_swift` .

```xml
<Entity id="cb2ab58c-9cb8-4c81-baf8-a4e106791df4" patternsProximity="300" recommendedConfidence="75">
<Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_swift" />
        <Match idRef="Keyword_swift" />
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_swift"></a>Keyword_swift

- den internationale standardiseringsorganisation 9362
- iso 9362
- iso9362
- Swift #
- swiftcode
- swiftnumber
- swiftroutingnumber
- swift-kode
- swift tal #
- hurtigt routingnummer
- bic-tal
- bic-kode
- Bic #
- Bic #
- bank-id-kode
- Organisation international de normalisering 9362
- Rapide #
- code SWIFT
- le numéro de swift
- swift numéro d'acheminement
- le numéro BIC
- \# BIC
- code identificateur de banque
- SWIFTコード
- SWIFT番号
- BIC番号
- BICコード
- SWIFT コード
- SWIFT 番号
- BIC 番号
- BIC コード
- 金融機関識別コード
- 金融機関コード
- 銀行コード