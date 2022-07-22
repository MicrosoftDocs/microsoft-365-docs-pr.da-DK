---
title: Objektdefinition af legitimationsoplysninger til brugerlogon (prøveversion)
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
description: Brugerlogon legitimationsoplysninger objektdefinition af følsomme oplysninger.
ms.openlocfilehash: d75fcb7069e8393b5b03ce08071057ff503a4bfb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944761"
---
# <a name="user-login-credentials-preview"></a>Legitimationsoplysninger til brugerlogon (prøveversion)

## <a name="format"></a>Format

Et parvis brugernavn og en adgangskode, der bruges i den generelle godkendelsesproces.

Eller

Et parvis brugernavn og en adgangskode, der bruges i PuTTY-forbindelsesstyring.

Eller

Adgangskode til almindelig tekst, der bruges i kodestykker.

Eller

En kombination af 88 tegn, der består af bogstaver, cifre og specialtegn.

## <a name="pattern"></a>Mønster

Forskellige formater for brugernavn og adgangskode, f.eks.:
 
`username=...;password=********;` <br>
`user id=...;password=********;` <br>
`uid=...;pwd=********;` <br>
`DB_USER=...;DB_PASS=********;` <br>
`Service Account=...;Password=********;` <br>

Eller

```xml
An XML element <login>
An embeded XML element <login>
Inner XML content
An embeded XML element </login>
An embeded XML element <password>
Inner XML content
An embeded XML element </password>
An XML element </login>
```

f.eks.

`<login> <login>ZYXWVU_1</login> <password>ZY…`

Eller

Forskellige adgangskodeformater i kodestykker, f.eks.:

`new X509Certificates2(` <br>
`ConvertTo-SecureString -String ********` <br>
`password = "********"` <br>
`"password" : "********"`<br>
`UserPasswordCredential(` <br>

Eller

En kombination af 86 tegn:

- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/)
- eller plustegn (+)
- slutter med to lighedstegn (=)

f.eks.:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

Dette SIT er designet til at matche de sikkerhedsoplysninger, der bruges i den generelle [brugerlogonproces](/azure/key-vault/quick-create-portal). 

Der bruges flere primære ressourcer:

- Mønstre for brugernavn og adgangskode i almindelig tekst.
- Mønstre for brugernavn og adgangskode i almindelig tekst i PuTTYcm-databasefilen.
- Mønstre for adgangskodekontekst i kode.
- Mønstre for Base64-kodet symmetrisk nøgle på 512 bit.
- Mønstre for CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, Id, AccountName.
- Mønstre for mockup-værdier, redigeringer og pladsholdere.
- En ordbog med ordforråd.

Mønstrene er designet til at matche faktiske legitimationsoplysninger med rimelig tillid. Mønstrene stemmer ikke overens med legitimationsoplysninger, der er formateret som eksempler. Mockup-værdier, redigerede værdier og pladsholdere, f.eks. legitimationsoplysningerstype eller forbrugsbeskrivelser, på den placering, hvor en faktisk hemmelig værdi skal vises, matches ikke.

## <a name="keywords"></a>Søgeord

### <a name="keyword_logincredentials"></a>Keyword_LoginCredentials:

- Adgangskode
- Pw
- DB_

### <a name="keyword_logincredentialsputty"></a>Keyword_LoginCredentialsPutty:

- Login

### <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode:

- Nøglen
- x509c
- Legitimationsoplysninger
- Adgangskode
- Pw
- securestring

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512:

- SharedAccessKey
- Kontonøgle
