---
title: Rediger en ordbog til nøgleord
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
description: Lær, hvordan du redigerer en ordbog til nøgleord i Microsoft 365 Compliance Center.
ms.openlocfilehash: acdf8b24aced21ed2f576fd57a3c685ef14debea
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63592432"
---
# <a name="modify-a-keyword-dictionary"></a>Rediger en ordbog til nøgleord

Du skal muligvis redigere nøgleord i en af dine nøgleordsordbøger eller redigere en af de indbyggede ordbøger. Du kan gøre dette via PowerShell eller via Overholdelsescenter.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Rediger en ordbog til nøgleord i Overholdelsescenter

Nøgleordsordbøger kan bruges som `Primary elements` eller `Supporting elements` i MØNSTRE (sensitive information type). Du kan redigere en ordbog til nøgleord, mens du opretter et SIT eller i et eksisterende SIT. Sådan redigerer du en eksisterende ordbog til nøgleord:

1. Åbn det mønster, der indeholder den ordbog til nøgleord, du vil opdatere.
2. Find den ordbog til nøgleord, du vil opdatere, og vælg rediger.
3. Foretag dine redigeringer med ét nøgleord pr. linje.

   ![skærmbillede, hvor du redigerer nøgleord.](../media/edit-keyword-dictionary.png)

4. Vælg `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>Rediger en ordbog til nøgleord ved hjælp af PowerShell

Vi vil f.eks. ændre nogle ord i PowerShell, gemme betingelserne lokalt, hvor du kan ændre dem i en editor, og derefter opdatere de tidligere ord på plads.

Hent først ordbogsobjektet:

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

Udskrivning `$dict` viser de forskellige egenskaber. Selve nøgleordene gemmes i et objekt i backend'en, `$dict.KeywordDictionary` men indeholder en strengrepræsentation af dem, som du skal bruge til at redigere ordbogen.

Før du redigerer ordbogen, skal du ændre strengen af ord tilbage til en matrix ved hjælp af `.split(',')` metoden. Derefter rydder du op i de uønskede mellemrum mellem nøgleordene med metoden `.trim()` , så kun nøgleordene kan arbejde med dem.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Nu fjerner du nogle ord fra ordbogen. Da eksempelordbogen kun indeholder nogle få nøgleord, kan du lige så nemt gå til at eksportere ordbogen og redigere den i Notesblok, men ordbøger indeholder generelt en stor mængde tekst, så du lærer først på denne måde, at redigere dem nemt i PowerShell.

I det sidste trin gemte du nøgleordene i en matrix. Der er flere måder at fjerne elementer fra en [matrix på,](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)) men som en simpel fremgangsmåde skal du oprette en matrix med de ord, du vil fjerne fra ordbogen, og derefter kun kopiere ordbogsordet til den, som ikke findes på listen over ord, der skal fjernes.

Kør kommandoen for `$terms` at få vist den aktuelle liste over ord. Outputtet for kommandoen ser sådan ud:

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

Kør denne kommando for rent faktisk at fjerne betingelserne fra listen:

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

Kør kommandoen for `$updatedTerms` at vise den opdaterede liste over ord. Outputtet for kommandoen ser sådan ud (de angivne vilkår er blevet fjernet):

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

Gem ordbogen lokalt, og tilføj et par ord mere. Du kan tilføje betingelserne lige her i PowerShell, men du skal stadig eksportere filen lokalt for at sikre, at den gemmes med Unicode-kodning og indeholder AFSER.

Gem ordbogen lokalt ved at køre følgende:

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

Nu skal du åbne filen, tilføje dine andre ord og gemme med Unicode-kodning (UTF-16). Nu skal du uploade de opdaterede ord og opdatere ordbogen.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Nu er ordbogen blevet opdateret på plads. Feltet `Identity` tager navnet på ordbogen. Hvis du også vil `Set-` ændre navnet på din ordbog ved hjælp af cmdlet'en, `-Name` skal du blot føje parameteren til det, der er ovenfor, med navnet på den nye ordbog.

## <a name="see-also"></a>Se også

- [Opret en ordbog til nøgleord](create-a-keyword-dictionary.md)
- [Oprette en brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type.md)
