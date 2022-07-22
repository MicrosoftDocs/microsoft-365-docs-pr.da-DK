---
title: Definition af nationalt id-kort i Grækenland
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
description: Definition af enhed for følsomme oplysninger for det nationale id-kort i Grækenland.
ms.openlocfilehash: 731adcfee8c2464bd45e9324e8305a4cc813d7eb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944755"
---
# <a name="greece-national-id-card"></a>Nationalt id-kort for Grækenland

## <a name="format"></a>Format

Kombination af 7-8 bogstaver og tal plus en streg

## <a name="pattern"></a>Mønster

Syv bogstaver og tal (gammelt format):

- Et bogstav (ethvert bogstav i det græske alfabet)
- En streg
- Seks cifre

Otte bogstaver og tal (nyt format):

- To bogstaver, hvis store bogstaver forekommer i både det græske og det latinske alfabet (ABEZHIKMNOPTYX)
- En streg
- Seks cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_greece_id_card` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keyword_greece_id_card` .

En DLP-politik har lav tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_greece_id_card` finder indhold, der svarer til mønsteret.

```xml
      <!-- Greece National ID Card -->
      <Entity id="82568215-1da1-46d3-874a-d2294d81b5ac" patternsProximity="300" recommendedConfidence="85">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_greece_id_card" />
          <Match idRef="Keyword_greece_id_card" />
        </Pattern>
        <Pattern confidenceLevel="65">
          <IdMatch idRef="Regex_greece_id_card" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keyword_greece_id_card"></a>Keyword_greece_id_card

- græsk id
- græsk nationalt id
- græsk personligt id-kort
- græsk politi-id
- Identitetskort
- tautotita
- ταυτότητα
- ταυτότητας