---
title: Generel symmetrisk nøgleenhedsdefinition (prøveversion)
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
description: Generel objektdefinition for følsomme oplysninger af typen af symmetrisk nøgle.
ms.openlocfilehash: 539fe92e769442de430252d7d14b5fc1e5febfb8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944759"
---
# <a name="general-symmetric-key-preview"></a>Generel symmetrisk nøgle (prøveversion)

## <a name="format"></a>Format

En kombination af 44 tegn, der består af bogstaver, cifre og specialtegn.

Eller

En kombination af 88 tegn, der består af bogstaver, cifre og specialtegn.

## <a name="pattern"></a>Mønster

En kombination af 43 tegn:
 
- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/) eller plustegn (+)
- slutter med et lighedstegn (=)

f.eks.:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

Eller

En kombination af 86 tegn:
 
- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/) eller plustegn (+)
- slutter med to lighedstegn (=)

f.eks.:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

Dette SIT er designet til at matche de sikkerhedsoplysninger, der bruges i [den generelle godkendelsesproces.](/dotnet/api/system.security.cryptography.aes?view=net-5.0) 

Der bruges flere primære ressourcer:

- Mønstre for Base64-kodet symmetrisk nøgle på 256 bit.
- Mønstre for Base64-kodet symmetrisk nøgle på 512 bit.
- Mønstre for CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, Id, AccountName.
- Mønstre for mockup-værdier, redigeringer og pladsholdere.
- En ordbog med ordforråd.

Mønstrene er designet til at matche faktiske legitimationsoplysninger med rimelig tillid. Mønstrene stemmer ikke overens med legitimationsoplysninger, der er formateret som eksempler. Mockup-værdier, redigerede værdier og pladsholdere, f.eks. legitimationsoplysningerstype eller forbrugsbeskrivelser, på den placering, hvor en faktisk hemmelig værdi skal vises, matches ikke.

## <a name="keywords"></a>Søgeord

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256:

- SharedAccessKey
- Kontonøgle

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512:

- SharedAccessKey
- Kontonøgle
