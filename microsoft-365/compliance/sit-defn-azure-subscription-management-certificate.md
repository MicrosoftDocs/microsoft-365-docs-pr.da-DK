---
title: Definition af certifikat til administration af Azure-abonnementer (prøveversion)
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
description: Objektdefinition af objektdefinition for certifikat til administration af Azure-abonnementsadministration.
ms.openlocfilehash: 7ce7b09fdeae6f9622a3aac4f92beb446715f8df
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944825"
---
# <a name="azure-subscription-management-certificate-preview"></a>Certifikat til administration af Azure-abonnementer (prøveversion)

## <a name="format"></a>Format

En kombination på op til 20.000 tegn bestående af bogstaver, cifre og specialtegn.

## <a name="pattern"></a>Mønster

En kombination på op til 20.000 tegn:
 
- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreg (/) eller plustegn (+)
- Op til to lighedstegn (==)

f.eks.:

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

## <a name="checksum"></a>Checksum

Ja

## <a name="definition"></a>Definition

Dette SIT er designet til at matche de sikkerhedsoplysninger, der bruges til at godkende med den [klassiske udrulningsmodel](/azure/azure-resource-manager/management/deployment-models) , der leveres af Azure. Mange programmer og værktøjer, f.eks. Visual Studio eller Azure SDK, bruger disse certifikater til at automatisere konfiguration og installation af forskellige [Azure-tjenester](/azure/azure-api-management-certs). 

Der bruges flere primære ressourcer:

- Mønstre for Base64-kodet strengkonstant.
- Mønstre for CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.

Mønstrene er designet til at matche faktiske legitimationsoplysninger med rimelig tillid. Mønstrene stemmer ikke overens med legitimationsoplysninger, der er formateret som eksempler. Mockup-værdier, redigerede værdier og pladsholdere, f.eks. legitimationsoplysningerstype eller forbrugsbeskrivelser, på den placering, hvor en faktisk hemmelig værdi skal vises, matches ikke.

## <a name="keywords"></a>Søgeord

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral:

- MII
