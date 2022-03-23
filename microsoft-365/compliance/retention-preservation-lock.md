---
title: Brug Preservation Lock til at begrænse ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater
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
description: Brug Preservation Lock med opbevaringspolitikker og opbevaringspolitikker for at hjælpe dig med at opfylde lovmæssige krav og beskytte administratorer.
ms.openlocfilehash: 64c2bb8f2718ce0da9d638b5b8b6bd4f89d33668
ms.sourcegitcommit: f6fff04431d632db02e7bdbf12f691091a30efad
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/18/2021
ms.locfileid: "63594362"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Brug Preservation Lock til at begrænse ændringer i opbevaringspolitikker og politikker for opbevaringsmærkater

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!IMPORTANT]
> Aktuelt [understøtter adaptive politikomfang ikke Bevarelseslås](retention.md#adaptive-or-static-policy-scopes-for-retention) .

Preservation Lock låser en opbevaringspolitik eller opbevaringsmærkatpolitik, så ingen – herunder en global administrator – kan deaktivere politikken, slette politikken eller gøre den mindre restriktiv. Denne konfiguration kan være nødvendig i forbindelse med lovmæssige krav og kan hjælpe med at beskytte mod administratorer.

Når en opbevaringspolitik er låst:

- Ingen kan deaktivere politikken eller slette den
- Placeringer kan tilføjes, men ikke fjernes
- Du kan udvide opbevaringsperioden, men ikke mindske den

Når en opbevaringspolitik for navne er låst:

- Ingen kan deaktivere politikken eller slette den
- Placeringer kan tilføjes, men ikke fjernes
- Etiketter kan tilføjes, men ikke fjernes

Kort sagt kan en låst politik øges eller udvides, men den kan ikke reduceres eller deaktiveres.

> [!IMPORTANT]
> Før du låser en opbevaringspolitik eller opbevaringsmærkatpolitik, er det vigtigt, at du forstår påvirkningen og bekræfter, om det er påkrævet for din organisation. Det kan f.eks. være nødvendigt at opfylde lovmæssige krav. Administratorer kan ikke deaktivere eller slette disse politikker, når opbevaringslåsen er anvendt.

Konfigurer Bevarelseslås, når du har [oprettet en](create-retention-policies.md) opbevaringspolitik eller en opbevaringsmærkatpolitik, [som du](create-apply-retention-labels.md) publicerer [eller anvender automatisk](apply-retention-labels-automatically.md).

> [!NOTE]
> Låsning af en etiketpolitik forhindrer ikke en administrator i at reducere opbevaringsperioden i en etiket, der er inkluderet i den låste politik. Dette krav med andre begrænsninger kan opfyldes, når du konfigurerer en etiket til at markere elementer som en [lovgivningsmæssig post](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Sådan låser du en opbevaringspolitik eller en opbevaringsetiketpolitik

Du skal bruge PowerShell, hvis du skal bruge Preservation Lock. Fordi administratorer ikke kan deaktivere eller slette en opbevaringspolitik, efter denne lås er anvendt, er aktivering af denne funktion ikke tilgængelig i brugergrænsefladen for at beskytte dig mod utilsigtet konfiguration.

Alle politikker for opbevaring og med enhver konfiguration understøtter Preservation Lock.

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Find navnet på den politik, du vil låse, ved at køre [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). Eksempel:
    
   ![Liste over opbevaringspolitikker i PowerShell.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. Hvis du vil placere en Bevarelseslås på din politik, skal du køre [Set-RetentionCompliancePolicy-cmdlet'en](/powershell/module/exchange/set-retentioncompliancepolicy) med navnet på politikken og parameteren *RestrictiveRetention* angivet til sand:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" –RestrictiveRetention $true
    ```
    
    Eksempel:
    
    ![RestrictiveRetention-parameter i PowerShell.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     Når du bliver bedt om det, skal du læse og bekræfte de begrænsninger, der er forbundet med denne konfiguration, ved **at indtaste Y**:
    
   ![Spørg, om du vil bekræfte, at du vil låse en opbevaringspolitik i PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

En bevarelseslås er nu placeret på politikken. For at bekræfte skal du `Get-RetentionCompliancePolicy` køre igen, men angive politikkens navn og vise politikparametrene:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

Du bør få **vist RestrictiveRetention** er angivet til **Sand**. Eksempel:

![Låst politik med alle parametre vist i PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Se også

[Ressourcer, der kan hjælpe dig med at opfylde lovmæssige krav til informationsstyring og datastyring](retention-regulatory-requirements.md)