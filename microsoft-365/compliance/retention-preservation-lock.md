---
title: Brug bevarelseslås til at begrænse ændringer af opbevaringspolitikker
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Brug bevarelseslås med politikker for opbevaring og politikker for opbevaringsmærkat for at hjælpe dig med at opfylde lovmæssige krav og beskytte mod rogue-administratorer.
ms.openlocfilehash: 88f875b201dbfdb633985506aee29acf99e2adb7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622607"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Brug Bevarelseslås til at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!IMPORTANT]
> I øjeblikket understøtter [tilpassede politikområder](retention.md#adaptive-or-static-policy-scopes-for-retention) ikke Bevarelseslås.

Bevarelseslås låser en opbevaringspolitik eller opbevaringsmærkatpolitik, så ingen – herunder en global administrator – kan slå politikken fra, slette politikken eller gøre den mindre restriktiv. Denne konfiguration kan være nødvendig i forbindelse med lovmæssige krav og kan hjælpe med at beskytte mod rogue-administratorer.

Når en opbevaringspolitik er låst:

- Ingen kan deaktivere politikken eller slette den
- Placeringer kan tilføjes, men ikke fjernes
- Du kan forlænge opbevaringsperioden, men ikke mindske den

Når en politik for opbevaringsmærkat er låst:

- Ingen kan deaktivere politikken eller slette den
- Placeringer kan tilføjes, men ikke fjernes
- Navne kan tilføjes, men ikke fjernes

En låst politik kan kort sagt øges eller udvides, men den kan ikke reduceres eller deaktiveres.

> [!IMPORTANT]
> Før du låser en politik for opbevaring eller opbevaringsmærkat, er det vigtigt, at du forstår virkningen og bekræfter, om den er påkrævet for din organisation. Det kan f.eks. være nødvendigt for at opfylde lovmæssige krav. Administratorer kan ikke deaktivere eller slette disse politikker, når bevarelseslåsen er anvendt.

Konfigurer bevarelseslås, når du har oprettet en [opbevaringspolitik](create-retention-policies.md), eller en politik for opbevaringsmærkat, som du [publicerer](create-apply-retention-labels.md) og kun indeholder etiketter, der [markerer elementer som lovmæssige poster](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Sådan låser du en opbevaringspolitik eller en politik for opbevaringsmærkat

Du skal bruge PowerShell, hvis du har brug for bevarelseslås. Da administratorer ikke kan deaktivere eller slette en politik for opbevaring, når denne lås er anvendt, er aktivering af denne funktion ikke tilgængelig i brugergrænsefladen for at sikre mod utilsigtet konfiguration.

Alle opbevaringspolitikker med en hvilken som helst konfiguration understøtter Bevarelseslås. Hvis du vil anvende bevarelseslås på en politik for opbevaringsmærkater, må den kun indeholde etiketter, der markerer elementer som lovmæssige poster.

1. [Opret forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Find navnet på den politik, du vil låse, ved at køre [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). Eksempel:
    
   ![Liste over opbevaringspolitikker i PowerShell.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. Hvis du vil placere en bevarelseslås på din politik, skal du køre [Set-RetentionCompliancePolicy-cmdlet'en](/powershell/module/exchange/set-retentioncompliancepolicy) med navnet på politikken, og parameteren *RestrictiveRetention* er angivet til sand:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" -RestrictiveRetention $true
    ```
    
    Eksempel:
    
    ![RestrictiveRetention-parameter i PowerShell.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     Når du bliver bedt om det, skal du læse og bekræfte de begrænsninger, der følger med denne konfiguration, ved at angive **Y**:
    
   ![Bed om at bekræfte, at du vil låse en opbevaringspolitik i PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Der er nu placeret en bevarelseslås på politikken. Hvis du vil bekræfte, skal du køre `Get-RetentionCompliancePolicy` igen, men angive politiknavnet og vise politikparametrene:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

Du bør se **, at RestrictiveRetention** er angivet til **Sand**. Eksempel:

![Låst politik med alle parametre, der vises i PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Se også

[Ressourcer, der kan hjælpe dig med at opfylde lovmæssige krav til administration af datalivscyklus og datastyring](retention-regulatory-requirements.md)
