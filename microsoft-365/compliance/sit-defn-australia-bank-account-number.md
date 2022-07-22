---
title: Objektdefinition for bankkontonummer i Australien
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
description: Objektdefinition af kontonummer i Australien for følsomme oplysninger af typen .
ms.openlocfilehash: df46075da0b85f306a52b1971db7b15c6a13028b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944805"
---
# <a name="australia-bank-account-number"></a>Australiens bankkontonummer

## <a name="format"></a>Format

6 til 10 cifre med eller uden et forgreningsnummer for bankstaten

## <a name="pattern"></a>Mønster

Kontonummeret er 6 til 10 cifre.

Forgreningsnummeret for den australske bankstat:

- tre cifre
- en bindestreg
- tre cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk Regex_australia_bank_account_number finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra Keyword_australia_bank_account_number.
- Det regulære udtryk Regex_australia_bank_account_number_bsb finder indhold, der svarer til mønsteret.

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk Regex_australia_bank_account_number finder indhold, der svarer til mønsteret.

- Der blev fundet et nøgleord fra Keyword_australia_bank_account_number.

```xml
<!-- Australia Bank Account Number -->
<Entity id="74a54de9-2a30-4aa0-a8aa-3d9327fc07c7" patternsProximity="300" recommendedConfidence="75">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
        <Match idRef="Regex_australia_bank_account_number_bsb" />
  </Pattern>
  <Pattern confidenceLevel="75">
        <IdMatch idRef="Regex_australia_bank_account_number" />
        <Match idRef="Keyword_australia_bank_account_number" />
  </Pattern>
 </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_australia_bank_account_number"></a>Keyword_australia_bank_account_number

- swift bankkode
- korrespondentbank
- Grundvalutaen
- usa-konto
- holderadresse
- bankadresse
- informationskonto
- pengeoverførsler
- Bankgebyrer
- bankoplysninger
- bankoplysninger
- fulde navne
- Iaea