---
title: Rediger en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell
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
description: Få mere at vide om, hvordan du redigerer brugerdefinerede følsomme oplysninger ved hjælp af PowerShell.
ms.openlocfilehash: 2f1bc44dca9ec4a938c8cd3d4158163f9d5e2e2f
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63597993"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>Rediger en brugerdefineret type af følsomme oplysninger ved hjælp af PowerShell

I Overholdelsescenter PowerShell kræver ændring af en brugerdefineret type af følsomme oplysninger, at du:

1. Eksportér den eksisterende regelpakke, der indeholder den brugerdefinerede type af følsomme oplysninger, til en XML-fil (eller brug den eksisterende XML-fil, hvis du har den).

2. Rediger den brugerdefinerede type af følsomme oplysninger i den eksporterede XML-fil.

3. Importér den opdaterede XML-fil tilbage til den eksisterende regelpakke.

Hvis du vil oprette forbindelse til Compliance Center PowerShell, [skal du Forbind til Compliance Center PowerShell](/powershell/exchange/exchange-online-powershell).

### <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>Trin 1: Eksportér den eksisterende regelpakke til en XML-fil

> [!NOTE]
> Hvis du har en kopi af XML-filen (f.eks. du lige har oprettet og importeret den), kan du gå videre til næste trin for at redigere XML-filen.

1. Hvis du ikke allerede kender den, skal du køre [Get-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at finde navnet på den brugerdefinerede regelpakke:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Den indbyggede regelpakke, der indeholder de indbyggede typer af følsomme oplysninger, kaldes Microsoft Rule Package. Regelpakken, der indeholder de brugerdefinerede typer af følsomme oplysninger, du har oprettet i brugergrænsefladen til Overholdelsescenter, kaldes Microsoft.SCCManaged.CustomRulePack.

2. Brug [Get-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) til at gemme den brugerdefinerede regelpakke på en variabel:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Hvis navnet på regelpakken f.eks. er "Brugerdefineret regelpakke til medarbejder-id", skal du køre følgende cmdlet:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Brug følgende syntaks til at eksportere pakken med brugerdefinerede regler til en XML-fil:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   I dette eksempel eksporteres regelpakken til den filExportedRulePackage.xml der er navngivet i mappen C:\Dokumenter.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

#### <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>Trin 2: Ændre typen af følsomme oplysninger i den eksporterede XML-fil

Typer af følsomme oplysninger i XML-filen og andre elementer i filen er beskrevet tidligere i dette emne.

#### <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>Trin 3: Importér den opdaterede XML-fil tilbage til den eksisterende regelpakke

For at importere den opdaterede XML tilbage til den eksisterende regelpakke skal du bruge [Set-DlpSensitiveInformationTypeRulePackage-cmdlet'en](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) :

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)
- [Funktioner af typen Følsomme oplysninger](sit-functions.md)
