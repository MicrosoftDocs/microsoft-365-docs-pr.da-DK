---
title: Definition af adgangsnøgleenhed for Amazon S3-klienthemmelighed (prøveversion)
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
description: Objektdefinition af objekt af typen følsomme oplysninger for Amazon S3-klienthemmelighed.
ms.openlocfilehash: c3026beae856097e221063732f65b805a3fd05c2
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945461"
---
# <a name="amazon-s3-client-secret-access-key-preview"></a>Adgangsnøgle til Amazon S3-klienthemmelighed (prøveversion)

## <a name="format"></a>Format

En kombination af 40 tegn, der består af bogstaver, cifre og specialtegn. 

## <a name="pattern"></a>Mønster

13-cifret tal:

En kombination af 40 tegn, der består af: 

- a-z (skelner ikke mellem store og små bogstaver) 
- 0-9 
- skråstreg (/) eller plustegn (+) 

f.eks.: 

`abcdefghijklmnopqrst0123456789/+ABCDEFGH`

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

Dette SIT er designet til at matche de sikkerhedsoplysninger, der bruges til at få adgang til [Amazon Web Services.](/toolkit-for-eclipse/v1/user-guide/setup-credentials.html)


Der bruges flere primære ressourcer: 
 
- Mønstre for Base64-kodet symmetrisk nøgle med 240-bit. 
- Mønstre for CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName. 
- Mønstre for mockup-værdier, redigeringer og pladsholdere. 
- En ordbog med ordforråd.

Mønstrene er designet til at matche faktiske legitimationsoplysninger med rimelig tillid. Mønstrene stemmer ikke overens med legitimationsoplysninger, der er formateret som eksempler. Mockup-værdier, redigerede værdier og pladsholdere, f.eks. legitimationsoplysningerstype eller forbrugsbeskrivelser, på den placering, hvor en faktisk hemmelig værdi skal vises, matches ikke. 

## <a name="keywords"></a>Søgeord

### <a name="keyword_symmetrickey240"></a>Keyword_SymmetricKey240: 

- Hemmelige 
- Nøglen 