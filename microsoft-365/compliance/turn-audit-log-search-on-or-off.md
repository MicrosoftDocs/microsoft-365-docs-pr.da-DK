---
title: Slå overvågning til eller fra
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
ms.custom: seo-marvel-apr2020
description: Sådan aktiveres eller deaktiveres søgefunktionen Overvågningslog i Microsoft 365 Overholdelsescenter for at aktivere eller deaktivere administratorens mulighed for at søge i overvågningsloggen.
ms.openlocfilehash: e36fe410ed75522b0d531f2f9f7901b78f4974eb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587536"
---
# <a name="turn-auditing-on-or-off"></a>Slå overvågning til eller fra

Overvågningslogføring er som standard slået til for Microsoft 365 og Office 365 virksomheder. Men når du konfigurerer en ny Microsoft 365 eller Office 365, skal du kontrollere status for overvågning for organisationen. Du kan finde en vejledning [i afsnittet Bekræfte overvågningsstatus for din](#verify-the-auditing-status-for-your-organization) organisation i denne artikel. 

Når overvågning i Microsoft 365 Overholdelsescenter er slået til, registreres bruger- og administratoraktivitet fra din organisation i overvågningsloggen og bevares i 90 dage og op til et år afhængigt af den licens, der er tildelt til brugerne. Din organisation kan dog have grunde til ikke at ønske at registrere og bevare data i overvågningsloggen. I disse tilfælde kan en global administrator beslutte at deaktivere overvågning i Microsoft 365.

> [!IMPORTANT]
> Hvis du deaktiverer overvågning i Microsoft 365, kan du ikke bruge Office 365 Management Activity API eller Microsoft Sentinel til at få adgang til overvågningsdata for organisationen. Hvis du slår overvågning fra ved at følge trinnene i denne artikel, betyder det, at der ikke returneres nogen resultater, når du søger i overvågningsloggen ved hjælp af Microsoft 365 Overholdelsescenter, eller når du kører **Search-UnifiedAuditLog-cmdlet'en** i Exchange Online PowerShell. Det betyder også, at overvågningslogfiler ikke er tilgængelige via Office 365 Management Activity API eller Microsoft Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>Før du slår overvågning til eller fra

- Du skal være tildelt rollen Overvågningslogfiler i Exchange Online at slå overvågning til eller fra i din Microsoft 365 organisation. Denne rolle er som standard tildelt rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser  i Exchange Administration. Globale administratorer i Microsoft 365 er medlemmer af rollegruppen Organisationsadministration i Exchange Online.

    > [!NOTE]
    > Brugere skal have tildelt tilladelser i en Exchange Online at slå overvågning til eller fra. Hvis du tildeler brugere rollen Overvågningslogfiler på siden  Tilladelser i Microsoft 365 Overholdelsescenter, kan de ikke slå overvågning til eller fra. Dette skyldes, at den underliggende cmdlet er en Exchange Online PowerShell-cmdlet.

- Du kan finde en trinvis vejledning til søgning i overvågningsloggen i [Søge i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md). Du kan finde flere oplysninger Microsoft 365 Management Activity API i Introduktion til [Microsoft 365 Administrations-API'er](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="verify-the-auditing-status-for-your-organization"></a>Bekræfte overvågningsstatus for organisationen

Hvis du vil kontrollere, at overvågning er aktiveret for din organisation, kan du køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

En værdi for `True` egenskaben  _UnifiedAuditLogIngestionEnabled_ angiver, at overvågning er aktiveret. En værdi af `False` angiver, at overvågning ikke er aktiveret.

> [!NOTE]
> Sørg for at køre den forrige kommando i Exchange Online PowerShell. Du kan ikke bruge Security & Compliance PowerShell til at køre denne kommando.

## <a name="turn-on-auditing"></a>Aktivere overvågning

Hvis overvågning ikke er aktiveret for din organisation, kan du aktivere det i programmet Microsoft 365 Overholdelsescenter ved hjælp af Exchange Online PowerShell. Det kan tage flere timer, efter du har aktiveret overvågning, før du kan returnere resultater, når du søger i overvågningsloggen.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>Brug overholdelsescenteret til at aktivere overvågning

1. Gå til <https://compliance.microsoft.com> , og log på.

2. Klik på Overvågning i venstre navigationsrude Microsoft 365 Overholdelsescenter **navigationsruden**.

   Hvis overvågning ikke er aktiveret for din organisation, vises der et banner, der beder dig om at starte optagelse af bruger- og administratoraktivitet.

   ![Banner på siden Overvågning.](../media/AuditingBanner.png)

3. Klik på **banneret Start optagelse af bruger- og administratoraktivitet** .

   Det kan tage op til 60 minutter, før ændringen træder i kraft.

### <a name="use-powershell-to-turn-on-auditing"></a>Brug PowerShell til at aktivere overvågning

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør følgende PowerShell-kommando for at aktivere overvågning.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Der vises en meddelelse om, at det kan tage op til 60 minutter, før ændringen træder i kraft.
  
## <a name="turn-off-auditing"></a>Slå overvågning fra

Du skal bruge Exchange Online PowerShell til at deaktivere overvågning.
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør følgende PowerShell-kommando for at deaktivere overvågning.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Kontrollér efter et stykke tid, at overvågning er slået fra (deaktiveret). Der er to måder at gøre dette på:

    - I Exchange Online PowerShell skal du køre følgende kommando:

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      Værdien af egenskaben  `False`  _UnifiedAuditLogIngestionEnabled_ angiver, at overvågning er slået fra.

    - Gå til **siden** Overvågning i Microsoft 365 Overholdelsescenter.

      Hvis overvågning ikke er aktiveret for din organisation, vises der et banner, der beder dig om at starte optagelse af bruger- og administratoraktivitet.

## <a name="audit-records-when-auditing-status-is-changed"></a>Overvåge poster, når overvågningsstatussen ændres

Ændringer af overvågningsstatus i organisationen overvåges selv. Det betyder, at overvågningsposter logføres, når overvågning er aktiveret eller deaktiveret. Du kan søge i Exchange efter disse overvågningsposter.

Hvis du vil søge Exchange overvågningslog efter overvågningsposter, der genereres, når du slår overvågning til eller fra, skal du køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Search-AdminAuditLog -Cmdlets Set-AdminAuditLogConfig -Parameters UnifiedAuditLogIngestionEnabled
```

Overvågningsposter for disse hændelser indeholder oplysninger om, hvornår overvågningsstatussen blev ændret, den administrator, der har ændret den, og IP-adressen på den computer, der blev brugt til at foretage ændringen. Følgende skærmbilleder viser overvågningsposter, der svarer til at ændre status for overvågning i organisationen.

### <a name="audit-record-for-turning-on-auditing"></a>Overvågningspost til aktivering af overvågning

![Overvågningspost til aktivering af overvågning](../media/AuditStatusAuditingEnabled.png)

`Confirm` Værdien af egenskaben *CmdletParameters* angiver, at samlet overvågningslogføring er aktiveret i overholdelsescenteret eller ved at køre **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true** cmdlet.

### <a name="audit-record-for-turning-off-auditing"></a>Overvågningspost til de slå overvågning fra

![Overvågningspost til de slå overvågning fra](../media/AuditStatusAuditingDisabled.png)

Værdien af `Confirm` er ikke medtaget i *egenskaben Cmdlet-parameterer* . Dette angiver, at samlet overvågningslogføring blev deaktiveret ved at køre **kommandoen Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false** Konfiguration.

Du kan finde flere oplysninger Exchange søge i overvågningsloggen for administratorer [under Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog).
