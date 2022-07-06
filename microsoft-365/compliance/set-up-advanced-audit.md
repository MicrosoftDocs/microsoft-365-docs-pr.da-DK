---
title: Konfigurer overvågning (Premium) i Microsoft 365
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
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: I denne artikel beskrives det, hvordan du konfigurerer overvågning (Premium), så du kan udføre tekniske undersøgelser, når brugerkonti kompromitteres, eller undersøge andre sikkerhedsrelaterede hændelser.
ms.openlocfilehash: adffd696a3eca2d51fb5325cd79c1ba26e58936c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639330"
---
# <a name="set-up-microsoft-purview-audit-premium"></a>Konfigurer Microsoft Purview-gennemgang (Premium)

Hvis din organisation har et abonnement og en slutbrugerlicens, der understøtter Overvågning (Premium), skal du udføre følgende trin for at konfigurere og bruge de yderligere funktioner i Overvågning (Premium).

![Arbejdsproces til konfiguration af overvågning (Premium).](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-audit-premium-for-users"></a>Trin 1: Konfigurer overvågning (Premium) for brugere

Overvågningsfunktioner (Premium), f.eks. muligheden for at logføre vigtige hændelser som MailItemsAccessed og Send, kræver en passende E5-licens, der er tildelt til brugerne. Derudover skal app-/tjenesteplanen Avanceret overvågning være aktiveret for disse brugere. Udfør følgende trin for hver bruger for at bekræfte, at appen Avanceret overvågning er tildelt til brugere:

1. I Microsoft 365 Administration skal du gå til **Brugere** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktive brugere**</a> og vælge en bruger.

2. Klik på **Licenser og apps** på siden med brugeregenskaber.

3. I afsnittet **Licenser** skal du bekræfte, at brugeren er tildelt en E5-licens eller er tildelt en passende licens til tilføjelsesprogrammet. Du kan se en liste over licenser, der understøtter Audit (Premium), under [Overvågning (Premium)-licenskrav](auditing-solutions-overview.md#audit-premium-1).

4. Udvid afsnittet **Apps** , og kontrollér, at afkrydsningsfeltet **Microsoft 365 Advanced Auditing** er markeret.

5. Hvis afkrydsningsfeltet ikke er markeret, skal du markere det og derefter klikke på **Gem ændringer.**

   Logføring af overvågningsposter for MailItemsAccessed og Send starter inden for 24 timer. Du skal udføre trin 3 for at starte logføring af to andre overvågningshændelser (Premium): SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint.

Hvis du har tilpasset de postkassehandlinger, der er logget på brugerpostkasser eller delte postkasser, overvåges alle nye Overvågningshændelser (Premium), der udgives af Microsoft, heller ikke automatisk på disse postkasser. Du kan finde oplysninger om, hvordan du ændrer de postkassehandlinger, der overvåges for hver logontype, i afsnittet "Skift eller gendan postkassehandlinger, der logføres som standard" under [Administrer overvågning af postkasse](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-audit-premium-events"></a>Trin 2: Aktivér overvågningshændelser (Premium)

Du skal aktivere to overvågningshændelser (Premium) (SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint), der skal logføres, når brugerne udfører søgninger i Exchange Online og SharePoint Online. Hvis du vil aktivere, at disse to hændelser overvåges for brugere, skal du køre følgende kommando (for hver bruger) i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

I et multi-geo-miljø skal du køre den forrige **Set-Mailbox-kommando** i det område, hvor brugerens postkasse er placeret. Kør følgende kommando for at identificere brugerens postkasseplacering: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Hvis kommandoen til at aktivere overvågning af søgeforespørgsler tidligere blev kørt i en skov, der er forskellig fra den, brugerens postkasse er placeret i, skal du fjerne værdien SearchQueryInitiated fra brugerens postkasse ved at køre `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` og derefter føje den til brugerens postkasse i det område, hvor brugerens postkasse er placeret.

## <a name="step-3-set-up-audit-retention-policies"></a>Trin 3: Konfigurer politikker for overvågningsopbevaring

Ud over standardpolitikken, der bevarer Exchange-, SharePoint- og Azure AD overvågningsposter i ét år, kan du oprette yderligere politikker for opbevaring af overvågningslog for at opfylde kravene i organisationens sikkerhedshandlinger, it og overholdelsesteams. Du kan få flere oplysninger under [Administrer opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md).

## <a name="step-4-search-for-audit-premium-events"></a>Trin 4: Søg efter overvågningshændelser (Premium)

Nu, hvor du har konfigureret Overvågning (Premium) for din organisation, kan du søge efter vigtige overvågningshændelser (Premium) og andre aktiviteter, når du udfører kriminaltekniske undersøgelser. Når du har fuldført trin 1 og trin 2, kan du søge i overvågningsloggen efter overvågningshændelser (Premium) og andre aktiviteter under retsmedicinske undersøgelser af kompromitterede konti og andre typer sikkerheds- eller overholdelsesundersøgelser. Du kan få flere oplysninger om udførelse af en kriminalteknisk undersøgelse af kompromitterede brugerkonti ved hjælp af Hændelsen MailItemsAccessed Audit (Premium) under [Brug overvågning (Premium) til at undersøge kompromitterede konti](mailitemsaccessed-forensics-investigations.md).
