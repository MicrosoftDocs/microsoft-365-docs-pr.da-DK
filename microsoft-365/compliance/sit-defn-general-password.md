---
title: Generel definition af adgangskodeenhed (prøveversion)
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
description: Generel objektdefinition af typen af oplysninger, der er følsomme over for adgangskode.
ms.openlocfilehash: ea800d6798a2068eb90ff02e1550e48606e7b1ea
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944760"
---
# <a name="general-password-preview"></a>Generel adgangskode (prøveversion)

## <a name="format"></a>Format

Op til 20.000 tegn kombinationer af bogstaver, cifre og specialtegn.

Eller

Log på legitimationsoplysninger, der bruges på kommandolinjer

Eller

Adgangskode i almindelig tekst, der bruges i kodestykker

Eller

Almindelig tekstadgangskode, der bruges i script

Eller

Almindelig tekstadgangskode, der bruges i XML-konfigurationen

Eller

En kombination af 24 tegn, der består af bogstaver, cifre og specialtegn.

Eller

En kombination af 32 tegn bestående af bogstaver og cifre.

Eller

En kombination af 32 tegn, der består af bogstaver, cifre og specialtegn.

Eller

En kombination af 44 tegn, der består af bogstaver, cifre og specialtegn.

Eller

En kombination af bogstaver, cifre og specialtegn på 88 tegn.

## <a name="pattern"></a>Mønster

En kombination på op til 20.000 tegn bestående af:

- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/) eller plustegn (+)
- Op til to lighedstegn (=)

f.eks.:

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

Eller

Forskellige formater for kommandolinjelogon i legitimationsoplysninger, f.eks.: 

`-u username:********`

Eller

`-u username -p ********`

Eller

`/f ... /p ********`

Eller

`-Password ********`

Eller

`-U username%********`

Eller

`-secrets:********`

f.eks.:

`zDbg.DataPuller.exe -secrets:eyJ`

Eller

Forskellige adgangskodeformater i kodestykker, f.eks.:

`new X509Certificates2(`

Eller

`ConvertTo-SecureString -String ********`

Eller

`password = "********"`

Eller

`"password" : "********"`

Eller

`UserPasswordCredential(`

f.eks.:

`password = "ZYXWVU_1";`

Eller

Forskellige adgangskodeformater i scriptet, f.eks.:

`password = ********`

f.eks.:

`password=ZYXWVU_1`

Eller

Forskellige adgangskodeformater i XML, f.eks.:

```xml
<secret>********</secret>
<password>********</password>
<setting name="password" value="********" >
<setting name="password">********</setting>
<setting name="password"><value>********</value></setting>
```

f.eks.:

`<secret>ZYXWVU_1</secret>`

Eller

Enhver kombination af 22 tegn, der består af:

- a-z (skelner ikke mellem store og små bogstaver)
- cifre, skråstreger eller plustegn
- slutter med to lighedstegn (=)

f.eks.:

`abcdefgh0123456789/+AB==`

Eller

Enhver kombination af 32 tegn, der består af:

- a-f eller A-F (forskel på store og små bogstaver) eller 0-9

f.eks.:

`abcdef0123456789abcdef0123456789`

Eller

Enhver kombination af 32 tegn, der består af:

- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/) eller plustegn (+)

f.eks.:

`abcdefghijklmnopqr0123456789/+AB`

Eller

En kombination af 43 tegn, der består af:

- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/) eller plustegn (+)
- slutter med et lighedstegn (=)

f.eks.:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

Eller

En kombination af 86 tegn, der består af:

- a-z (skelner ikke mellem store og små bogstaver)
- 0-9
- skråstreger (/) eller plustegn (+)
- slutter med to lighedstegn (=)

f.eks.:

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Checksum

Ja

## <a name="description"></a>Beskrivelse

Dette SIT er designet til at matche de sikkerhedsoplysninger, der er som brugernavne og adgangskoder, der bruges i den generelle [logonproces for brugeren](/azure/key-vault/quick-create-portal). Der bruges flere primære ressourcer:

- Mønstre for Base64-kodet strengkonstant.
- Mønstre for adgangskodekontekst på kommandolinjen.
- Mønstre for adgangskodekontekst i kode.
- Mønstre for adgangskodekontekst i script.
- Mønstre for adgangskodekontekst i XML.
- Mønstre for Base64-kodet symmetrisk nøgle med 128-bit.
- Mønstre for sekskantet symmetrisk nøgle med 128-bit.
- Mønstre for base64-kodet symmetrisk nøgle med 192-bit.
- Mønstre for Base64-kodet symmetrisk nøgle med 256-bit.
- Mønstre for Base64-kodet symmetrisk nøgle med 512-bit.
- Mønstre for CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, ID, AccountName.
- Mønstre for mockup-værdier, redigeringer og pladsholdere.
- En ordbog med ordforråd.


Mønstrene er designet til at matche faktiske legitimationsoplysninger med rimelig tillid. Mønstrene stemmer ikke overens med legitimationsoplysninger, der er formateret som eksempler. Mockup-værdier, redigerede værdier og pladsholdere, f.eks. legitimationsoplysningerstype eller forbrugsbeskrivelser, på den placering, hvor en faktisk hemmelig værdi skal vises, matches ikke.

## <a name="keywords"></a>Søgeord

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral

- MII

### <a name="keyword_passwordcontextincmdline"></a>Keyword_PasswordContextInCmdLine

- certutil
- zdbg
- Hemmelige
- VSTS_TOKEN
- Krøller
- PowerShell
- ps1
- -u
- Smc
- Autologon
- ldifde
- Rclone
- --env
- SignTool
- winexe
- Nettet

## <a name="keyword_passwordcontextincode"></a>Keyword_PasswordContextInCode

- Nøglen
- x509c
- Legitimationsoplysninger
- Adgangskode
- Pw
- securestring

### <a name="keyword_passwordcontextinscript"></a>Keyword_PasswordContextInScript

- Hemmelige
- Adgangskode
- Pw

### <a name="keyword_passwordcontextinxml"></a>Keyword_PasswordContextInXml

- brugeradgangsadgang
- Adgangskode
- Pw
- Connectionstring
- Nøglen
- Legitimationsoplysninger
- Token
- Sas
- Hemmelige

### <a name="keyword_symmetrickey128"></a>Keyword_SymmetricKey128

- Hemmelige
- Nøglen
- Adgangskode
- Pw

### <a name="keyword_symmetrickey128hex"></a>Keyword_SymmetricKey128Hex

- dapi
- Nøglen
- Hemmelige
- Token
- Adgangskode
- Pw

### <a name="keyword_symmetrickey192"></a>Keyword_SymmetricKey192

- Adgangskode
- -p
- azurecr

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256

- SharedAccessKey
- Kontonøgle

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512

- SharedAccessKey
- Kontonøgle
