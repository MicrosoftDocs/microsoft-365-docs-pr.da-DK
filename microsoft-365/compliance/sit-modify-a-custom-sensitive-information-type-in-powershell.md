---
title: Rediger en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell
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
ms.openlocfilehash: 639a52526924d3068ce2d1cd38006a1773b6d098
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621953"
---
# <a name="modify-a-custom-sensitive-information-type-using-powershell"></a>Rediger en brugerdefineret type følsomme oplysninger ved hjælp af PowerShell

I PowerShell til & overholdelse af angivne standarder kræver ændring af en brugerdefineret type følsomme oplysninger, at du:

1. Eksportér den eksisterende regelpakke, der indeholder den brugerdefinerede type følsomme oplysninger, til en XML-fil (eller brug den eksisterende XML-fil, hvis du har den).

2. Rediger typen af brugerdefinerede følsomme oplysninger i den eksporterede XML-fil.

3. Importér den opdaterede XML-fil tilbage til den eksisterende regelpakke.

Hvis du vil oprette forbindelse til PowerShell til & overholdelse af angivne standarder, skal du se [Sikkerhed & Overholdelse af PowerShell](/powershell/exchange/exchange-online-powershell).

## <a name="step-1-export-the-existing-rule-package-to-an-xml-file"></a>Trin 1: Eksportér den eksisterende regelpakke til en XML-fil

> [!NOTE]
> Hvis du har en kopi af XML-filen (f.eks. du lige har oprettet og importeret den), kan du gå til næste trin for at redigere XML-filen.

1. Hvis du ikke allerede ved det, skal du køre [Cmdlet'en Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtype) for at finde navnet på den brugerdefinerede regelpakke:

   ```powershell
   Get-DlpSensitiveInformationTypeRulePackage
   ```

   > [!NOTE]
   > Den indbyggede regelpakke, der indeholder de indbyggede følsomme oplysningstyper, kaldes Microsoft Rule Package. Den regelpakke, der indeholder de brugerdefinerede følsomme oplysningstyper, som du oprettede i brugergrænsefladen i Compliance Center, kaldes Microsoft.SCCManaged.CustomRulePack.

2. Brug [Cmdlet'en Get-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/get-dlpsensitiveinformationtyperulepackage) til at gemme den brugerdefinerede regelpakke i en variabel:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "RulePackageName"
   ```

   Hvis navnet på regelpakken f.eks. er "Employee ID Custom Rule Pack", skal du køre følgende cmdlet:

   ```powershell
   $rulepak = Get-DlpSensitiveInformationTypeRulePackage -Identity "Employee ID Custom Rule Pack"
   ```

3. Brug følgende syntaks til at eksportere den brugerdefinerede regelpakke til en XML-fil:

   ```powershell
   [System.IO.File]::WriteAllBytes('XMLFileAndPath', $rulepak.SerializedClassificationRuleCollection)
   ```

   I dette eksempel eksporteres regelpakken til den fil, der hedder ExportedRulePackage.xml i mappen C:\Dokumenter.

   ```powershell
   [System.IO.File]::WriteAllBytes('C:\My Documents\ExportedRulePackage.xml', $rulepak.SerializedClassificationRuleCollection)
   ```

## <a name="step-2-modify-the-sensitive-information-type-in-the-exported-xml-file"></a>Trin 2: Rediger typen af følsomme oplysninger i den eksporterede XML-fil

Typer af følsomme oplysninger i XML-filen og andre elementer i filen er beskrevet tidligere i dette emne.

## <a name="step-3-import-the-updated-xml-file-back-into-the-existing-rule-package"></a>Trin 3: Importér den opdaterede XML-fil tilbage til den eksisterende regelpakke

Hvis du vil importere den opdaterede XML tilbage til den eksisterende regelpakke, skal du bruge Cmdlet'en [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage) :

```powershell
Set-DlpSensitiveInformationTypeRulePackage -FileData ([System.IO.File]::ReadAllBytes('C:\My Documents\External Sensitive Info Type Rule Collection.xml'))
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-DlpSensitiveInformationTypeRulePackage](/powershell/module/exchange/set-dlpsensitiveinformationtyperulepackage).

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Funktioner for type af følsomme oplysninger](sit-functions.md)
