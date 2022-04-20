---
title: Administrer opbevaringspolitikker for overvågningslog
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Opbevaringspolitikker for overvågningslog er en del af de nye funktioner i Microsoft Purview Audit (Premium). En opbevaringspolitik for overvågningslog giver dig mulighed for at angive, hvor længe overvågningslogge skal bevares i din organisation.
ms.openlocfilehash: 7f745baa78ebf61c0d32d39c49e3158b2418553f
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934857"
---
# <a name="manage-audit-log-retention-policies"></a>Administrer opbevaringspolitikker for overvågningslog

Du kan oprette og administrere opbevaringspolitikker for overvågningslog på Microsoft Purview-overholdelsesportalen. Opbevaringspolitikker for overvågningslog er en del af de nye funktioner i Microsoft Purview Audit (Premium). En opbevaringspolitik for overvågningslog giver dig mulighed for at angive, hvor længe overvågningslogge skal bevares i din organisation. Du kan bevare overvågningslogge i op til 10 år. Du kan oprette politikker baseret på følgende kriterier:

- Alle aktiviteter i en eller flere Microsoft 365 tjenester
- Specifikke aktiviteter (i en Microsoft 365 tjeneste), der udføres af alle brugere eller bestemte brugere
- Et prioritetsniveau, der angiver, hvilken politik der har forrang i du har flere politikker i din organisation

## <a name="default-audit-log-retention-policy"></a>Standard opbevaringspolitik for overvågningslog

Overvågning (Premium) i Microsoft 365 indeholder en standardopbevaringspolitik for overvågningslog for alle organisationer. Denne politik bevarer alle Exchange Online, SharePoint Online, OneDrive for Business og Azure Active Directory overvågningsposter i ét år. Denne standardpolitik bevarer overvågningsposter, der indeholder værdien **af Exchange**, **SharePoint**, **OneDrive**, **AzureActiveDirectory** for egenskaben **Arbejdsbelastning** (som er den tjeneste, aktiviteten fandt sted i). Standardpolitikken kan ikke ændres. Se afsnittet [Flere oplysninger](#more-information) i denne artikel for at få en liste over posttyper for hver arbejdsbelastning, der er inkluderet i standardpolitikken.

> [!NOTE]
> Standard opbevaringspolitikken for overvågningsloggen gælder kun for overvågningsposter for aktivitet, der udføres af brugere, der har fået tildelt en Office 365 eller Microsoft 365 E5 licens eller har en Microsoft 365 E5 Overholdelse eller E5 eDiscovery- og overvågningstilføjelsesprogramlicens. Hvis du har ikke-E5-brugere eller gæstebrugere i din organisation, bevares deres tilsvarende overvågningsposter i 90 dage.

## <a name="before-you-create-an-audit-log-retention-policy"></a>Før du opretter en opbevaringspolitik for overvågningslog

- Du skal have tildelt rollen Organisationskonfiguration på overholdelsesportalen for at oprette eller redigere en politik for overvågningsopbevaring.

- Du kan maksimalt have 50 opbevaringspolitikker for overvågningslog i din organisation.

- Hvis du vil bevare en overvågningslog i mere end 90 dage (og op til 1 år), skal den bruger, der genererer overvågningsloggen (ved at udføre en overvåget aktivitet), tildeles en Office 365 E5 eller en Microsoft 365 E5 licens eller have en Microsoft 365 E5 Overholdelse- eller E5 eDiscovery- og audit-licens. Hvis du vil bevare overvågningslogge i 10 år, skal den bruger, der genererer overvågningsloggen, også tildeles en tiårig licens til tilføjelsesprogrammet til opbevaring af overvågningslog ud over en E5-licens.

- Alle brugerdefinerede opbevaringspolitikker for overvågningslog (oprettet af din organisation) har forrang frem for standardopbevaringspolitikken. Hvis du f.eks. opretter en opbevaringspolitik for overvågningsloggen for Exchange postkasseaktivitet, der har en opbevaringsperiode, der er kortere end ét år, bevares overvågningsposter for Exchange postkasseaktiviteter i den kortere varighed, der er angivet i den brugerdefinerede politik.

## <a name="create-an-audit-log-retention-policy"></a>Opret en opbevaringspolitik for overvågningslog

1. Gå til , <https://compliance.microsoft.com> og log på med en brugerkonto, der har fået tildelt rollen Organisationskonfiguration på siden Tilladelser på overholdelsesportalen.

2. Klik på **Overvågning** i venstre rude på overholdelsesportalen.

3. Klik på fanen **Overvågning af opbevaringspolitikker** .

4. Klik på **Opret opbevaringspolitik for overvågning**, og udfyld derefter følgende felter på pop op-siden:

   ![Ny overvågningsopbevaringspolitikside.](../media/CreateAuditLogRetentionPolicy.png)

   1. **Politiknavn:** Navnet på opbevaringspolitikken for overvågningsloggen. Dette navn skal være entydigt i din organisation, og det kan ikke ændres, når politikken er oprettet.

   2. **Beskrivelse:** Valgfrit, men nyttigt til at angive oplysninger om politikken, f.eks. posttypen eller arbejdsbelastningen, de brugere, der er angivet i politikken, og varigheden.

   3. **Brugere:** Vælg en eller flere brugere, politikken skal anvendes på. Hvis du lader feltet være tomt, gælder politikken for alle brugere. Hvis du lader **Posttype** være tom, skal du vælge en bruger.

   4. **Posttype:** Den overvågningsposttype, som politikken gælder for. Hvis du lader denne egenskab være tom, skal du vælge en bruger i feltet **Brugere** . Du kan vælge en enkelt posttype eller flere posttyper:
      - Hvis du vælger en enkelt posttype, vises feltet **Aktiviteter** dynamisk. Du kan bruge rullelisten til at vælge aktiviteter fra den valgte posttype, som politikken skal anvendes på. Hvis du ikke vælger bestemte aktiviteter, gælder politikken for alle aktiviteter med den valgte posttype.
      - Hvis du vælger flere posttyper, har du ikke mulighed for at vælge aktiviteter. Politikken gælder for alle aktiviteter for de valgte posttyper.

   5. **Varighed:** Den mængde tid, det har brugt på at bevare de overvågningslogge, der opfylder kriterierne i politikken.

   6. **Prioritet:** Denne værdi bestemmer den rækkefølge, som politikker for opbevaring af overvågningslog i din organisation behandles i. En lavere værdi angiver en højere prioritet. Gyldige prioriteter er numeriske værdier mellem **1** og **10000**. En værdi på **1** er den højeste prioritet, og en værdi på **10000** er den laveste prioritet. En politik med værdien **5** prioriteres f.eks. over en politik med værdien **10**. Som tidligere forklaret har enhver brugerdefineret opbevaringspolitik for overvågningslog prioriteret frem for standardpolitikken for din organisation.

5. Klik på **Gem** for at oprette den nye opbevaringspolitik for overvågningsloggen.

Den nye politik vises på listen under fanen **Overvågning af opbevaringspolitikker** .

## <a name="manage-audit-log-retention-policies-in-the-compliance-portal"></a>Administrer opbevaringspolitikker for overvågningslog på overholdelsesportalen

Opbevaringspolitikker for overvågningslog vises under fanen **Overvågning af opbevaringspolitikker** (også kaldet *dashboardet*). Du kan bruge dashboardet til at få vist, redigere og slette politikker for overvågningsopbevaring.

### <a name="view-policies-in-the-dashboard"></a>Få vist politikker på dashboardet

Opbevaringspolitikker for overvågningslog vises i dashboardet. En fordel ved at få vist politikker på dashboardet er, at du kan klikke på kolonnen **Prioritet** for at få vist politikkerne i den prioritet, de anvendes i. Som tidligere forklaret angiver en lavere værdi en højere prioritet.

![Prioritetskolonne i dashboardet Overvågning af opbevaringspolitikker.](../media/AuditLogRetentionDashboardPriority.png)

Du kan også vælge en politik for at få vist dens indstillinger på pop op-siden.

> [!NOTE]
> Standard opbevaringspolitikken for overvågningsloggen for din organisation vises ikke i dashboardet.

### <a name="edit-policies-in-the-dashboard"></a>Rediger politikker i dashboardet

Hvis du vil redigere en politik, skal du vælge den for at få vist pop op-siden. Du kan ændre en eller flere indstillinger og derefter gemme dine ændringer.

> [!IMPORTANT]
>
> Hvis du bruger **Cmdlet'en New-UnifiedAuditLogRetentionPolicy** , er det muligt at oprette en opbevaringspolitik for overvågningslog for posttyper eller aktiviteter, der ikke er tilgængelige i værktøjet **Opret overvågningspolitik** på dashboardet. I dette tilfælde kan du ikke redigere politikken (f.eks. ændre opbevaringsvarigheden eller tilføje og fjerne aktiviteter) fra dashboardet **Overvågning af opbevaringspolitikker** . Du kan kun få vist og slette politikken i Overholdelsescenter. Hvis du vil redigere politikken, skal du bruge Cmdlet'en [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell.>
>
> **Tip:** Der vises en meddelelse øverst på pop op-siden for politikker, der skal redigeres ved hjælp af PowerShell.

### <a name="delete-policies-in-the-dashboard"></a>Slet politikker på dashboardet

Hvis du vil slette en politik, skal du klikke **på sletteikonet**![.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) og derefter bekræfte, at du vil slette politikken. Politikken fjernes fra dashboardet, men det kan tage op til 30 minutter, før politikken fjernes fra din organisation.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>Opret og administrer opbevaringspolitikker for overvågningslog i PowerShell

Du kan også bruge Security & Compliance Center PowerShell til at oprette og administrere opbevaringspolitikker for overvågningslog. En af grundene til at bruge PowerShell er at oprette en politik for en posttype eller aktivitet, der ikke er tilgængelig i brugergrænsefladen.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>Opret en opbevaringspolitik for overvågningslog i PowerShell

Følg disse trin for at oprette en opbevaringspolitik for overvågningslog i PowerShell:

1. [Forbind til PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende kommando for at oprette en opbevaringspolitik for overvågningslog:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   I dette eksempel oprettes der en opbevaringspolitik for overvågningsloggen med navnet "Microsoft Teams Overvågningspolitik" med disse indstillinger:

   - En beskrivelse af politikken.
   - Bevarer alle Microsoft Teams aktiviteter (som defineret af parameteren *RecordType*).
   - Bevarer Microsoft Teams overvågningslogge i 10 år.
   - En prioritet på 100.

Her er et andet eksempel på oprettelse af en opbevaringspolitik for overvågningslog. Denne politik bevarer overvågningslogge for aktiviteten "Bruger, der er logget på" i seks måneder for brugerens admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Du kan få flere oplysninger under [New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>Få vist politikker i PowerShell

Brug [Cmdlet'en Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell til at få vist politikker for opbevaring af overvågningslog.

Her er et eksempel på en kommando, der viser indstillingerne for alle politikker for opbevaring af overvågningslog i din organisation. Denne kommando sorterer politikkerne fra højeste til laveste prioritet.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> **Cmdlet'en Get-UnifiedAuditLogRetentionPolicy** returnerer ikke standardpolitikken for opbevaring af overvågningslog for din organisation.

### <a name="edit-policies-in-powershell"></a>Rediger politikker i PowerShell

Brug [Set-UnifiedAuditLogRetentionPolicy-cmdlet'en](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell til at redigere en eksisterende opbevaringspolitik for overvågningslog.

### <a name="delete-policies-in-powershell"></a>Slet politikker i PowerShell

Brug cmdlet'en [Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell til at slette en opbevaringspolitik for overvågningslog. Det kan tage op til 30 minutter, før politikken fjernes fra din organisation.

## <a name="more-information"></a>Flere oplysninger

Som tidligere angivet bevares overvågningsposter for handlinger i Azure Active Directory, Exchange Online, SharePoint Online og OneDrive for Business som standard i et år. I følgende tabel vises alle de posttyper (for hver af disse tjenester), der er inkluderet i standardpolitikken for opbevaring af overvågningslog. Det betyder, at overvågningslogge for alle handlinger med denne posttype bevares i ét år, medmindre en brugerdefineret opbevaringspolitik for overvågningslogge har forrang for en bestemt posttype, handling eller bruger. Enum-værdien (der vises som værdien for egenskaben RecordType i en overvågningspost) for hver posttype vises i parentes.

<br>

****

|AzureActiveDirectory|Exchange |SharePoint eller OneDrive|
|---|---|---|
|AzureActiveDirectory (8)|ExchangeAdmin (1)|ComplianceDLPSharePoint (11)|
|AzureActiveDirectoryAccountLogon (9)|ExchangeItem (2)|ComplianceDLPSharePointClassification (33)|
|AzureActiveDirectoryStsLogon (15)|Kampagne (62)|Project (35)|
||ComplianceDLPExchange (13)|SharePoint (4)|
||ComplianceSupervisionExchange (68)|SharePointCommentOperation (37)|
||CustomerKeyServiceEncryption (69)|SharePointContentTypeOperation (55)|
||ExchangeAggregatedOperation (19)|SharePointFieldOperation (56)|
||ExchangeItemAggregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
