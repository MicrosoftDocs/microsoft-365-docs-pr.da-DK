---
title: Administrere opbevaringspolitikker for overvågningslogfiler
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
description: Opbevaringspolitikker for overvågningslogfiler er en del af de nye avancerede overvågningsfunktioner i Microsoft 365. Med en opbevaringspolitik for overvågningsloggen kan du angive, hvor lang tid overvågningslogfilerne skal bevares i organisationen.
ms.openlocfilehash: f8c269aa4541c438942c69831857ed531681b742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587343"
---
# <a name="manage-audit-log-retention-policies"></a>Administrere opbevaringspolitikker for overvågningslogfiler

Du kan oprette og administrere opbevaringspolitikker for overvågningslogfiler i Microsoft 365 Overholdelsescenter. Opbevaringspolitikker for overvågningslogfiler er en del af de nye avancerede overvågningsfunktioner i Microsoft 365. Med en opbevaringspolitik for overvågningsloggen kan du angive, hvor lang tid overvågningslogfilerne skal bevares i organisationen. Du kan opbevare overvågningslogfiler i op til 10 år. Du kan oprette politikker baseret på følgende kriterier:

- Alle aktiviteter i en eller flere Microsoft 365 tjenester
- Specifikke aktiviteter (i en Microsoft 365 tjeneste), der udføres af alle brugere eller af bestemte brugere
- Et prioritetsniveau, der angiver, hvilken politik der har forrang i du har flere politikker i organisationen

## <a name="default-audit-log-retention-policy"></a>Standardopbevaringspolitik for overvågningslogfiler

Avanceret overvågning i Microsoft 365 en standardopbevaringspolitik for overvågningsloggen for alle organisationer. Denne politik bevarer alle Exchange Online, SharePoint Online, OneDrive for Business og Azure Active Directory overvågningsposter i et år. Denne standardpolitik bevarer overvågningsposter, der indeholder værdien af **Exchange**, **SharePoint**, **OneDrive**, **AzureActiveDirectory** for egenskaben Arbejdsbyrde (som er den tjeneste, hvor  aktiviteten forekom). Standardpolitikken kan ikke ændres. Se afsnittet [Flere oplysninger i](#more-information) denne artikel for at få en liste over posttyper for hver arbejdsmængde, der er inkluderet i standardpolitikken.

> [!NOTE]
> Standardopbevaringspolitikken for overvågningslogfiler gælder kun for overvågningsposter for aktivitet, der udføres af brugere, som er tildelt en Office 365- eller Microsoft 365 E5-licens eller har en licens til Microsoft 365 E5 Overholdelse eller E5 eDiscovery og Overvågning af tilføjelsesprogrammet. Hvis du har ikke-E5-brugere eller gæstebrugere i organisationen, bevares deres tilsvarende overvågningsposter i 90 dage.

## <a name="before-you-create-an-audit-log-retention-policy"></a>Før du opretter en opbevaringspolitik for overvågningsloggen

- Du skal have tildelt rollen Organisationskonfiguration i organisationens Microsoft 365 Overholdelsescenter at oprette eller ændre en opbevaringspolitik for overvågning.

- Du kan maksimalt have 50 opbevaringspolitikker for overvågningslogfiler i organisationen.

- Hvis du vil bevare en overvågningslog i mere end 90 dage (og op til 1 år), skal den bruger, der genererer overvågningsloggen (ved at udføre en overvåget aktivitet), være tildelt en Office 365 E5- eller Microsoft 365 E5-licens eller have en licens til Microsoft 365 E5 Overholdelse eller E5 eDiscovery og Overvågning. Hvis du vil bevare overvågningslogfiler i ti år, skal den bruger, der genererer overvågningsloggen, også have tildelt en 10-års opbevaringslicens til overvågningsloggen ud over en E5-licens.

- Alle brugerdefinerede opbevaringspolitikker til overvågningslogfiler (oprettet af din organisation) prioriteres højere end standardopbevaringspolitikken. Hvis du f.eks. opretter en opbevaringspolitik for Exchange-postkasseaktivitet i Exchange, der har en opbevaringsperiode, der er kortere end et år, bevares overvågningsposter for Exchange-postkasseaktiviteter i den kortere varighed, der er angivet af den brugerdefinerede politik.

## <a name="create-an-audit-log-retention-policy"></a>Opret en opbevaringspolitik for overvågningslogfiler

1. Gå til <https://compliance.microsoft.com> og log på med en brugerkonto, der er tildelt rollen Organisationskonfiguration på siden Tilladelser i Microsoft 365 Overholdelsescenter.

2. Klik på Overvågning i venstre rude Microsoft 365 Overholdelsescenter **navigationsruden**.

3. Klik på fanen **Overvågningsopbevaringspolitikker** .

4. Klik **på Opret overvågningsopbevaringspolitik**, og udfyld derefter følgende felter på pop op-siden:

   ![Pop op-siden Ny overvågningsopbevaringspolitik.](../media/CreateAuditLogRetentionPolicy.png)

   1. **Politiknavn:** Navnet på opbevaringspolitikken for overvågningsloggen. Dette navn skal være entydigt i organisationen, og det kan ikke ændres, når politikken er oprettet.

   2. **Beskrivelse:** Valgfrit, men praktisk til at give oplysninger om politikken, f.eks. posttypen eller arbejdsmængden, brugere, der er angivet i politikken, og varigheden.

   3. **Brugere:** Vælg en eller flere brugere, som politikken skal anvendes på. Hvis du lader dette felt være tomt, gælder politikken for alle brugere. Hvis du lader **Posttype være tom** , skal du vælge en bruger.

   4. **Posttype:** Den type overvågningspost, som politikken gælder for. Hvis du lader denne egenskab være tom, skal du vælge en bruger i **feltet** Brugere. Du kan vælge en enkelt posttype eller flere posttyper:
      - Hvis du vælger en enkelt posttype, **vises** feltet Aktiviteter dynamisk. Du kan bruge rullelisten til at vælge aktiviteter fra den valgte posttype, som politikken skal anvendes på. Hvis du ikke vælger bestemte aktiviteter, gælder politikken for alle aktiviteter for den valgte posttype.
      - Hvis du vælger flere posttyper, har du ikke mulighed for at vælge aktiviteter. Politikken gælder for alle aktiviteter for de valgte posttyper.

   5. **Varighed:** Den tid, som overvågningslogfilerne skal bevares, som opfylder kriterierne i politikken.

   6. **Prioritet:** Denne værdi bestemmer den rækkefølge, som opbevaringspolitikkerne for overvågningsloggen behandles i i organisationen. En lavere værdi angiver en højere prioritet. Gyldige prioriteter er numeriske værdier mellem **1** og **10000**. En værdi på **1** er højeste prioritet, og en værdi på **10000 er** den laveste prioritet. En politik med en værdi på **5** prioriteres f.eks. højere end en politik med en værdi på **10**. Som tidligere nævnt har opbevaringspolitik for brugerdefinerede overvågningslogfiler forrang over standardpolitikken for organisationen.

5. Klik **på Gem** for at oprette den nye opbevaringspolitik for overvågningsloggen.

Den nye politik vises på listen på fanen **Opbevaringspolitikker for** overvågning.

## <a name="manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center"></a>Administrer opbevaringspolitikker for overvågningslogfiler i Microsoft 365 Overholdelsescenter

Opbevaringspolitikker for overvågningsloggen er angivet på **fanen Overvågningsopbevaringspolitikker** (også kaldet *dashboardet*). Du kan bruge dashboardet til at få vist, redigere og slette opbevaringspolitikker for overvågning.

### <a name="view-policies-in-the-dashboard"></a>Vis politikker i dashboardet

Opbevaringspolitikker for overvågningslogfiler vises på dashboardet. En af fordelene ved at få vist politikker i dashboardet er, at  du kan klikke på kolonnen Prioritet for at få vist politikkerne i den prioritet, de anvendes i. Som tidligere nævnt angiver en lavere værdi en højere prioritet.

![Kolonnen Prioritet i dashboardet for opbevaringspolitikker til overvågning.](../media/AuditLogRetentionDashboardPriority.png)

Du kan også vælge en politik for at få vist dens indstillinger på pop op-siden.

> [!NOTE]
> Standardopbevaringspolitikken for overvågningsloggen for organisationen vises ikke i dashboardet.

### <a name="edit-policies-in-the-dashboard"></a>Rediger politikker i dashboardet

Hvis du vil redigere en politik, skal du markere den for at få vist pop op-siden. Du kan ændre en eller flere indstillinger og derefter gemme ændringerne.

> [!IMPORTANT]
>
> Hvis du bruger **New-UnifiedAuditLogRetentionPolicy-cmdlet'en**, er det muligt at oprette en opbevaringspolitik for overvågningsloggen for posttyper eller aktiviteter, der ikke er  tilgængelige i værktøjet Opret opbevaringspolitik for overvågning i dashboardet. I dette tilfælde kan du ikke redigere politikken (f.eks. ændre opbevaringsvarighed eller tilføje og fjerne aktiviteter) fra dashboardet for opbevaringspolitikker **til overvågning** . Du kan kun se og slette politikken i overholdelsescenter. For at redigere politikken skal du bruge [Set-UnifiedAuditLogRetentionPolicy-cmdlet'en](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell.>
>
> **Tip!** Der vises en meddelelse øverst på pop op-siden for politikker, der skal redigeres ved hjælp af PowerShell.

### <a name="delete-policies-in-the-dashboard"></a>Slet politikker i dashboardet

Hvis du vil slette en politik, skal du **klikke på ikonet** ![Slet Slet.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) og bekræft derefter, at du vil slette politikken. Politikken fjernes fra dashboardet, men det kan tage op til 30 minutter, før politikken fjernes fra organisationen.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>Opret og administrer opbevaringspolitikker for overvågningslogfiler i PowerShell

Du kan også bruge Security & Compliance Center PowerShell til at oprette og administrere politikker for opbevaring af overvågningslogfiler. En grund til at bruge PowerShell er at oprette en politik for en posttype eller aktivitet, der ikke er tilgængelig i brugergrænsefladen.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>Opret en opbevaringspolitik for overvågningsloggen i PowerShell

Følg disse trin for at oprette en opbevaringspolitik for overvågningsloggen i PowerShell:

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende kommando for at oprette en opbevaringspolitik for overvågningsloggen:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   I dette eksempel oprettes en opbevaringspolitik for overvågningsloggen med navnet "Microsoft Teams overvågningspolitik" med disse indstillinger:

   - En beskrivelse af politikken.
   - Bevarer alle Microsoft Teams (som defineret af *RecordType-parameteren*).
   - Bevarer Microsoft Teams i 10 år.
   - En prioritet på 100.

Her er et andet eksempel på oprettelse af en opbevaringspolitik for overvågningsloggen. Denne politik bevarer overvågningslogfilerne for aktiviteten "Bruger, der er logget på" i seks måneder for admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Du kan finde flere oplysninger [i New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>Vis politikker i PowerShell

Brug [Get-UnifiedAuditLogRetentionPolicy-cmdlet'en](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell til at få vist opbevaringspolitikker for overvågningslogfiler.

Her er en eksempelkommando, der viser indstillingerne for alle opbevaringspolitikker for overvågningslogfiler i organisationen. Denne kommando sorterer politikkerne fra højeste til laveste prioritet.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> **Get-UnifiedAuditLogRetentionPolicy-cmdlet'en** returnerer ikke standardopbevaringspolitikken for overvågningsloggen for organisationen.

### <a name="edit-policies-in-powershell"></a>Rediger politikker i PowerShell

Brug [Set-UnifiedAuditLogRetentionPolicy-cmdlet'en](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell til at redigere en eksisterende opbevaringspolitik for overvågningsloggen.

### <a name="delete-policies-in-powershell"></a>Slet politikker i PowerShell

Brug [af Remove-UnifiedAuditLogRetentionPolicy-cmdlet'en](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) i Security & Compliance Center PowerShell til at slette en opbevaringspolitik for overvågningsloggen. Det kan tage op til 30 minutter, før politikken fjernes fra organisationen.

## <a name="more-information"></a>Flere oplysninger

Som nævnt tidligere bevares overvågningsposter for handlinger i Azure Active Directory, Exchange Online, SharePoint Online og OneDrive for Business som standard i ét år. I følgende tabel vises alle posttyperne (for hver af disse tjenester), der er inkluderet i standardopbevaringspolitikken for overvågningslogfiler. Det betyder, at overvågningslogfiler for alle operationer med denne posttype bevares i et år, medmindre en brugerdefineret opbevaringspolitik for overvågningsloggen har forrang for en bestemt posttype, handling eller bruger. Værdien Enum (der vises som værdien for egenskaben RecordType i en overvågningspost) for hver posttype, vises i parenteser.

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
