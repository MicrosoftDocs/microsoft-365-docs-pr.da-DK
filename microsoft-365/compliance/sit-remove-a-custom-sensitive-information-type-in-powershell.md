---
title: Fjern en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell
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
description: Få mere at vide om, hvordan du fjerner en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell
ms.openlocfilehash: e935c9340c353561e71e25fdadfec5509da041e5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014734"
---
# <a name="remove-a-custom-sensitive-information-type-using-powershell"></a>Fjern en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I PowerShell & overholdelse af angivne standarder er der to metoder til at fjerne brugerdefinerede følsomme oplysningstyper:

- **Fjern individuelle brugerdefinerede typer følsomme oplysninger**: Brug den metode, der er dokumenteret i [Rediger en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell](sit-modify-a-custom-sensitive-information-type-in-powershell.md#modify-a-custom-sensitive-information-type-using-powershell). Du eksporterer den brugerdefinerede regelpakke, der indeholder den brugerdefinerede type følsomme oplysninger, fjerner typen af følsomme oplysninger fra XML-filen og importerer den opdaterede XML-fil tilbage til den eksisterende brugerdefinerede regelpakke.

- **Fjern en brugerdefineret regelpakke og alle brugerdefinerede følsomme oplysningstyper, den indeholder**: Denne metode er dokumenteret i dette afsnit.

> [!NOTE]
> Før du fjerner en brugerdefineret type følsomme oplysninger, skal du kontrollere, at ingen DLP-politikker eller Exchange regler for mailflow (også kaldet transportregler) stadig refererer til typen af følsomme oplysninger.

1. [PowerShell til & overholdelse af angivne standarder](/powershell/exchange/exchange-online-powershell)

2. Hvis du vil fjerne en brugerdefineret regelpakke, skal du bruge cmdlet'en [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage) :

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageIdentity"
   ```

   Du kan bruge værdien Name (for et hvilket som helst sprog) eller `RulePack id` værdien (GUID) til at identificere regelpakken.

   I dette eksempel fjernes regelpakken med navnet "Employee ID Custom Rule Pack".

   ```powershell
   Remove-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

   Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/remove-dlpsensitiveinformationtyperulepackage).

3. Benyt en af følgende fremgangsmåder for at bekræfte, at du har fjernet en brugerdefineret type følsomme oplysninger:

   - Kør [Get-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) , og kontrollér, at regelpakken ikke længere er angivet:

     ```powershell
     Get-DlpSensitiveInformationTypeRulePackage
     ```

   - Kør [Cmdlet'en Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at kontrollere, at de følsomme oplysningstyper i den fjernede regelpakke ikke længere er angivet:

     ```powershell
     Get-DlpSensitiveInformationType
     ```

     I forbindelse med brugerdefinerede følsomme oplysningstyper vil egenskabsværdien for Publisher være noget andet end Microsoft Corporation.

   - Erstat \<Name\> med værdien Name for den følsomme oplysningstype (f.eks. Medarbejder-id), og kør cmdlet'en [Get-DlpSensitiveInformationType](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at kontrollere, at typen af følsomme oplysninger ikke længere er angivet:

     ```powershell
     Get-DlpSensitiveInformationType -Identity "<Name>"
     ```

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om Forebyggelse af datatab i Microsoft Purview](dlp-learn-about-dlp.md)

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)

- [Funktioner for type af følsomme oplysninger](sit-functions.md)
