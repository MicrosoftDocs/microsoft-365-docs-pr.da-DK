---
title: Slå overvågning til eller fra
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Sådan slår du søgefunktionen Overvågningslog til eller fra på Microsoft Purview-overholdelsesportalen for at aktivere eller deaktivere muligheden for, at administratorer kan søge i overvågningsloggen.
ms.openlocfilehash: 3602a35169670b61a124cda40c9ab50b481571d8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078861"
---
# <a name="turn-auditing-on-or-off"></a>Slå overvågning til eller fra

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Overvågningslogføring er som standard slået til for Microsoft 365 og Office 365 virksomhedsorganisationer. Når du konfigurerer en ny Microsoft 365 eller Office 365 organisation, skal du dog kontrollere overvågningsstatussen for din organisation. Du kan finde instruktioner i afsnittet [Kontrollér overvågningsstatus for din organisation](#verify-the-auditing-status-for-your-organization) i denne artikel. 

Når overvågning i Microsoft Purview-overholdelsesportalen er slået til, registreres bruger- og administratoraktivitet fra din organisation i overvågningsloggen og opbevares i 90 dage og op til et år afhængigt af den licens, der er tildelt til brugerne. Din organisation kan dog have grunde til ikke at ville registrere og gemme overvågningslogdata. I disse tilfælde kan en global administrator beslutte at deaktivere overvågning i Microsoft 365.

> [!IMPORTANT]
> Hvis du slår overvågning fra i Microsoft 365, kan du ikke bruge API'en Office 365 Management Activity eller Microsoft Sentinel til at få adgang til overvågningsdata for din organisation. Hvis du deaktiverer overvågning ved at følge trinnene i denne artikel, returneres der ingen resultater, når du søger i overvågningsloggen ved hjælp af overholdelsesportalen, eller når du kører cmdlet'en **Search-UnifiedAuditLog** i Exchange Online PowerShell. Det betyder også, at overvågningslogge ikke er tilgængelige via API'en til administration af Office 365 eller Microsoft Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>Før du slår overvågning til eller fra

- Du skal have tildelt rollen Overvågningslogfiler i Exchange Online for at aktivere eller deaktivere overvågning i din Microsoft 365 organisation. Denne rolle tildeles som standard til rollegrupperne Administration af overholdelse og Organisationsadministration på siden **Tilladelser** i Exchange Administration. Globale administratorer i Microsoft 365 er medlemmer af rollegruppen Organisationsadministration i Exchange Online.

    > [!NOTE]
    > Brugerne skal have tildelt tilladelser i Exchange Online for at aktivere eller deaktivere overvågning. Hvis du tildeler brugere rollen Overvågningslogge på siden **Tilladelser på overholdelsesportalen** , kan de ikke slå overvågning til eller fra. Det skyldes, at den underliggende cmdlet er en PowerShell-cmdlet Exchange Online.

- Du kan finde en trinvis vejledning i, hvordan du søger i overvågningsloggen, [under Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md). Du kan få flere oplysninger om API'en til administration af Microsoft 365 under [Kom i gang med api'er til administration af Microsoft 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="verify-the-auditing-status-for-your-organization"></a>Kontrollér overvågningsstatus for din organisation

Hvis du vil kontrollere, at overvågning er slået til for din organisation, kan du køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

En værdi for `True` egenskaben  _UnifiedAuditLogIngestionEnabled_ angiver, at overvågning er slået til. `False` Værdien angiver, at overvågning ikke er aktiveret.

> [!NOTE]
> Sørg for at køre den forrige kommando i Exchange Online PowerShell. Du kan ikke bruge Security & Compliance PowerShell til at køre denne kommando.

## <a name="turn-on-auditing"></a>Slå overvågning til

Hvis overvågning ikke er slået til for din organisation, kan du aktivere den på overholdelsesportalen eller ved hjælp af Exchange Online PowerShell. Det kan tage flere timer, efter du har aktiveret overvågning, før du kan returnere resultater, når du søger i overvågningsloggen.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>Brug Overholdelsescenter til at aktivere overvågning

1. Gå til , <https://compliance.microsoft.com> og log på.

2. Klik på **Overvåg** i navigationsruden til venstre på overholdelsesportalen.

   Hvis overvågning ikke er slået til for din organisation, vises der et banner, hvor du bliver bedt om at starte optagelsen af bruger- og administratoraktivitet.

   ![Banner på siden Overvågning.](../media/AuditingBanner.png)

3. Klik på banneret **Start optagelse af bruger- og administratoraktivitet** .

   Det kan tage op til 60 minutter, før ændringen træder i kraft.

### <a name="use-powershell-to-turn-on-auditing"></a>Brug PowerShell til at aktivere overvågning

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør følgende PowerShell-kommando for at aktivere overvågning.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Der vises en meddelelse om, at det kan tage op til 60 minutter, før ændringen træder i kraft.
  
## <a name="turn-off-auditing"></a>Deaktiver overvågning

Du skal bruge Exchange Online PowerShell til at slå overvågning fra.
  
1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør følgende PowerShell-kommando for at deaktivere overvågning.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Efter et stykke tid skal du kontrollere, at overvågning er slået fra (deaktiveret). Der er to måder at gøre dette på:

    - Kør følgende kommando i Exchange Online PowerShell:

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      Værdien for  `False` egenskaben  _UnifiedAuditLogIngestionEnabled_ angiver, at overvågning er slået fra.

    - Gå til siden **Overvågning** på overholdelsesportalen.

      Hvis overvågning ikke er slået til for din organisation, vises der et banner, hvor du bliver bedt om at starte optagelsen af bruger- og administratoraktivitet.

## <a name="audit-records-when-auditing-status-is-changed"></a>Overvåg poster, når overvågningsstatus ændres

Ændringer af overvågningsstatus i din organisation overvåges selv. Det betyder, at overvågningsposter logføres, når overvågning er slået til eller fra. Du kan søge i Exchange administratorens overvågningslog for disse overvågningsposter.

Hvis du vil søge i Exchange administratorovervågningslog for overvågningsposter, der genereres, når overvågning aktiveres eller deaktiveres, skal du køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Search-AdminAuditLog -Cmdlets Set-AdminAuditLogConfig -Parameters UnifiedAuditLogIngestionEnabled
```

Overvågningsposter for disse hændelser indeholder oplysninger om, hvornår overvågningsstatussen blev ændret, den administrator, der ændrede den, og IP-adressen på den computer, der blev brugt til at foretage ændringen. På følgende skærmbilleder vises overvågningsposter, der svarer til at ændre overvågningsstatus i din organisation.

### <a name="audit-record-for-turning-on-auditing"></a>Overvågningspost til aktivering af overvågning

![Overvågningspost til aktivering af overvågning](../media/AuditStatusAuditingEnabled.png)

Værdien af `Confirm` i egenskaben *CmdletParameters* angiver, at unified overvågningslogføring blev slået til i overholdelsescenter eller ved at køre **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true** cmdlet.

### <a name="audit-record-for-turning-off-auditing"></a>Overvågningspost til deaktivering af overvågning

![Overvågningspost til deaktivering af overvågning](../media/AuditStatusAuditingDisabled.png)

Værdien af `Confirm` er ikke inkluderet i egenskaben *CmdletParameters* . Dette angiver, at unified overvågningslogføring blev slået fra ved at køre kommandoen **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false** .

Du kan finde flere oplysninger om søgning i Exchange administratorens overvågningslog i [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog).
