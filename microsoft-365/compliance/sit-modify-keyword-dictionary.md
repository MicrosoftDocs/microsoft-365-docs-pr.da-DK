---
title: Rediger en ordbog over nøgleord
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du ændrer en nøgleordsordbog i Microsoft Purview-compliance-portal.
ms.openlocfilehash: 8b2f2256be506f0ba01dc059bf0ac54e84c481c9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621705"
---
# <a name="modify-a-keyword-dictionary"></a>Rediger en ordbog over nøgleord

Du skal muligvis ændre nøgleord i en af dine søgeordsordbøger eller ændre en af de indbyggede ordbøger. Du kan gøre dette via PowerShell eller via Overholdelsescenter.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Rediger en nøgleordsordbog i Overholdelsescenter

Nøgleordsordbøger kan bruges som `Primary elements` eller `Supporting elements` i SIT-mønstre (følsomme oplysninger). Du kan redigere en nøgleordsordbog, mens du opretter et SIT eller i et eksisterende SIT. Du kan f.eks. redigere en eksisterende nøgleordsordbog:

1. Åbn mønsteret med den nøgleordsordbog, du vil opdatere.
2. Find den nøgleordsordbog, du vil opdatere, og vælg Rediger.
3. Foretag dine ændringer ved hjælp af ét nøgleord pr. linje.

   ![skærmbillede redigere nøgleord.](../media/edit-keyword-dictionary.png)

4. Vælg `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>Rediger en nøgleordsordbog ved hjælp af PowerShell

Vi ændrer f.eks. nogle ord i PowerShell, gemmer vilkårene lokalt, hvor du kan ændre dem i en editor, og opdaterer derefter de forrige ord på plads.

Først skal du hente ordbogsobjektet:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

Udskrivning `$dict` viser de forskellige egenskaber. Nøgleordene gemmes i et objekt i backend, men `$dict.KeywordDictionary` indeholder en strengrepræsentation af dem, som du skal bruge til at ændre ordbogen.

Før du ændrer ordbogen, skal du ændre ordstrengen til en matrix igen ved hjælp af `.split(',')` metoden . Derefter rydder du op i uønskede mellemrum mellem nøgleordene med `.trim()` metoden og lader kun nøgleordene arbejde med.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Nu skal du fjerne nogle ord fra ordbogen. Da eksempelordbogen kun indeholder nogle få nøgleord, kan du lige så godt springe over til at eksportere ordbogen og redigere den i Notesblok, men ordbøger indeholder generelt en stor mængde tekst, så du lærer først på denne måde, så du nemt kan redigere dem i PowerShell.

I det sidste trin har du gemt nøgleordene i en matrix. Der er flere måder at [fjerne elementer fra en matrix](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)) på, men som en enkel tilgang skal du oprette en matrix af de ord, du vil fjerne fra ordbogen, og derefter kun kopiere de ord, der ikke findes på listen over ord, der skal fjernes.

Kør kommandoen `$terms` for at få vist den aktuelle liste over ord. Outputtet af kommandoen ser ud som følger:

```powershell
aarskog's syndrome
abandonment
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablatio
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Kør denne kommando for at angive de ord, du vil fjerne:

```powershell
$termsToRemove = @('abandonment','ablatio')
```

Kør denne kommando for rent faktisk at fjerne ordene fra listen:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

Kør kommandoen `$updatedTerms` for at få vist den opdaterede liste over ord. Outputtet fra kommandoen ser sådan ud (de angivne ord er fjernet):

```powershell
aarskog's syndrome
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Gem nu ordbogen lokalt, og tilføj nogle flere ord. Du kan tilføje vilkårene lige her i PowerShell, men du skal stadig eksportere filen lokalt for at sikre, at den gemmes med Unicode-kodning og indeholder styklisten.

Gem ordbogen lokalt ved at køre følgende:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

Åbn nu filen, tilføj dine andre ord, og gem med Unicode-kodning (UTF-16). Nu skal du uploade de opdaterede ord og opdatere ordbogen på plads.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Nu er ordbogen blevet opdateret på plads. Feltet `Identity` har navnet på ordbogen. Hvis du også vil ændre navnet på din ordbog ved hjælp af cmdlet'en `Set-` , skal du blot føje `-Name` parameteren til ovenstående med navnet på din nye ordbog.

## <a name="see-also"></a>Se også

- [Opret en ordbog over nøgleord](create-a-keyword-dictionary.md)
- [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md)
