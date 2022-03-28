---
title: Konfigurer Avanceret overvågning i Microsoft 365
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
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: I denne artikel beskrives det, hvordan du kan konfigurere Avanceret overvågning, så du kan undersøge, hvornår brugerkonti kompromitteres, eller for at undersøge andre sikkerhedsrelaterede hændelser.
ms.openlocfilehash: dafe53161e04f28f2f5e4ff8dcfa71bab6c1a1f1
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754574"
---
# <a name="set-up-advanced-audit-in-microsoft-365"></a>Konfigurer Avanceret overvågning i Microsoft 365

Hvis din organisation har et abonnement og slutbrugerlicens, der understøtter Avanceret overvågning, skal du udføre følgende trin for at konfigurere og bruge de yderligere funktioner i Avanceret overvågning.

![Arbejdsproces til at konfigurere Avanceret overvågning.](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-advanced-audit-for-users"></a>Trin 1: Konfigurere Avanceret overvågning for brugere

Avancerede overvågningsfunktioner, såsom muligheden for at logføre vigtige hændelser som MailItemsAccessed og Send kræver en passende E5-licens, der er tildelt til brugere. Desuden skal avanceret overvågning af app/serviceplan være aktiveret for disse brugere. For at bekræfte at appen Avanceret overvågning er tildelt til brugere, skal du udføre følgende trin for hver bruger:

1. I Microsoft 365 Administration skal du gå **til** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users og vælge en bruger.

2. Klik på Licenser og apps på pop **op-siden med brugeregenskaber**.

3. I sektionen **Licenser** skal du bekræfte, at brugeren er tildelt en E5-licens eller er tildelt en passende tilføjelseslicens. Du kan finde en liste over licenser, der understøtter Avanceret overvågning, [under Licenskrav til avanceret overvågning](auditing-solutions-overview.md#advanced-audit-1).

4. Udvid **sektionen Apps**, og bekræft **, Microsoft 365 afkrydsningsfeltet Avanceret** overvågning er markeret.

5. Hvis afkrydsningsfeltet ikke er markeret, skal du markere det og derefter klikke på **Gem ændringer.**

   Logføringen af overvågningsposter for MailItemsAccessed og Send starter inden for 24 timer. Du skal udføre trin 3 for at starte logføring af to andre Avancerede overvågningshændelser: SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint.

Hvis du har tilpasset de postkassehandlinger, der er logget på brugerpostkasser eller delte postkasser, så bliver alle nye Avancerede overvågning-hændelser, der frigives af Microsoft, ikke automatisk overvåget for disse postkasser. Du kan finde oplysninger om, hvordan du ændrer de postkassehandlinger, der overvåges for hver logontype, i afsnittet "Rediger eller gendan postkassehandlinger, der er logført som standard" i Administrer [postkasserevision](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-advanced-audit-events"></a>Trin 2: Aktivér avancerede overvågningshændelser

Du skal aktivere to Avancerede overvågningshændelser (SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint) for at blive logført, når brugere udfører søgninger i Exchange Online og SharePoint Online. For at gøre det muligt at overvåge disse to hændelser for brugere skal du køre følgende kommando (for hver bruger) [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

I et miljø med flere geografiske områder skal du køre den forrige **Set-Mailbox-kommando** i den skov, hvor brugerens postkasse er placeret. Kør følgende kommando for at identificere brugerens postkasseplacering: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Hvis kommandoen til at aktivere overvågning af søgeforespørgsler tidligere blev kørt i et område, der er anderledes end den, brugerens postkasse er placeret i, skal du fjerne værdien SearchQueryInitiated `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` fra brugerens postkasse ved at køre og derefter føje den til brugerens postkasse i den skov, hvor brugerens postkasse er placeret.

## <a name="step-3-set-up-audit-retention-policies"></a>Trin 3: Konfigurere politikker for opbevaring af overvågning

Ud over standardpolitikken, der bevarer Exchange-, SharePoint- og Azure AD-overvågningsposter i et år, kan du oprette yderligere politikker for opbevaring af overvågningslogfiler, der opfylder kravene til organisationens sikkerhedshandlinger, IT og overholdelsesteams. Du kan få mere at vide under [Administrere opbevaringspolitikker for overvågningslogfiler](audit-log-retention-policies.md).

## <a name="step-4-search-for-advanced-audit-events"></a>Trin 4: Søg efter Avancerede overvågningshændelser

Nu hvor du har konfigureret Avanceret overvågning for din organisation, kan du søge efter vigtige Avancerede overvågningshændelser og andre aktiviteter, når du foretager omfattende undersøgelser. Når du har fuldført trin 1 og trin 2, kan du søge i overvågningsloggen efter Avancerede overvågningshændelser og andre aktiviteter under undersøgelse af kompromitterede konti og andre typer af sikkerheds- eller overholdelsesundersøgelse. Du kan finde flere oplysninger om, hvordan du undersøger kompromitterede brugerkonti ved hjælp af hændelsen MailItemsAccessed Advanced Audit under Brug Avanceret overvågning til at undersøge [kompromitterede konti](mailitemsaccessed-forensics-investigations.md).
