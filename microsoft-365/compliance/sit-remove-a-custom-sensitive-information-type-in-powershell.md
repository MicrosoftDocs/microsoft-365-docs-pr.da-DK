---
title: Fjern en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du fjerner en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell
ms.openlocfilehash: 852f9987b072f05dcf4f322f600bed23bcce7ef2
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63592265"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>Fjern en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell

I Compliance Center PowerShell er der to metoder til at fjerne brugerdefinerede typer af følsomme oplysninger:

- **Fjern individuelle brugerdefinerede typer af følsomme oplysninger**: Brug metoden, der er dokumenteret i [Rediger en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). Du kan eksportere den brugerdefinerede regelpakke, der indeholder den brugerdefinerede type af følsomme oplysninger, fjerne typen af følsomme oplysninger fra XML-filen og importere den opdaterede XML-fil tilbage til den eksisterende brugerdefinerede regelpakke.

- **Fjern en brugerdefineret regelpakke og alle typer af følsomme oplysninger, som** den indeholder: Denne metode er dokumenteret i dette afsnit.

> [!NOTE]
> Før du fjerner en brugerdefineret type af følsomme oplysninger, skal du kontrollere, at ingen DLP-politikker eller Exchange regler for mailflow (også kaldet transportregler) stadig henviser til typen af følsomme oplysninger.

1. [Forbind til Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell)

2. Hvis du vil fjerne en brugerdefineret regelpakke, skal [du bruge cmdlet'en Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) :

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Du kan bruge værdien Name (for et hvilket som helst sprog) eller `RulePack id` værdien (GUID) til at identificere regelpakken.

   I dette eksempel fjernes regelpakken med navnet "Brugerdefineret regelpakke til medarbejder-id".

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. For at bekræfte, at du har fjernet en brugerdefineret type af følsomme oplysninger, skal du gøre et af følgende:

   - Kør [cmdlet'en Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) , og bekræft, at regelpakken ikke længere er angivet:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Kør [cmdlet'en Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at bekræfte, at typerne af følsomme oplysninger i den fjernede regelpakke ikke længere vises:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     For brugerdefinerede typer af følsomme oplysninger vil Publisher være noget andet end Microsoft Corporation.

   - Erstat \<Name\> med værdien Navn på typen af følsomme oplysninger (f.eks. [Medarbejder-id), og kør Cmdlet'en Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at bekræfte, at typen af følsomme oplysninger ikke længere er angivet:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)

- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)

- [Funktioner af typen Følsomme oplysninger](sit-functions.md)
