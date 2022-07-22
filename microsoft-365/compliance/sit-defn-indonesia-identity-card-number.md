---
title: Definition af nummerenhed for Indonesiens identitetskort (KTP)
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
description: Id-kort (KTP) nummerfølsom definition af typen af følsomme oplysninger i Indonesien.
ms.openlocfilehash: d70e6ca902c6246e6faa67a91c5b52ae65e4fd47
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944756"
---
# <a name="indonesia-identity-card-ktp-number"></a>Indonesiens identitetskortnummer (KTP)

## <a name="format"></a>Format

16 cifre, der indeholder valgfrie punktummer

## <a name="pattern"></a>Mønster

16 cifre:

- Tocifret provinskode
- Et punktum (valgfrit)
- Tocifret regency eller bykode
- Tocifret underdistriktkode
- Et punktum (valgfrit)
- Seks cifre i formatet DDMMYY, som er fødselsdato
- Et punktum (valgfrit)
- Fire cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_indonesia_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_indonesia_id_card` .

```xml
<!-- Indonesia Identity Card (KTP) Number -->
<Entity id="da68fdb0-f383-4981-8c86-82689d3b7d55" recommendedConfidence="85" patternsProximity="300">
  <Pattern confidenceLevel="85">
     <IdMatch idRef="Regex_indonesia_id_card"/>
     <Match idRef="Keyword_indonesia_id_card"/>
</Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_indonesia_id_card"></a>Keyword_indonesia_id_card

- KTP
- Kartu Tanda Penduduk
- Nomor Induk Kependudukan