---
title: Konfigurer overvågning (Standard) i Microsoft 365
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
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MOE150
- MET150
description: I denne artikel beskrives det, hvordan du konfigurerer Overvågning (Standard), så du kan begynde at søge efter overvågningsaktiviteter, der udføres af brugere og administratorer i din organisation.
ms.openlocfilehash: 15e72d1b2899799f432cdc717352cf53a0a370e4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993726"
---
# <a name="set-up-microsoft-purview-audit-standard"></a>Konfigurer Microsoft Purview Audit (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Med Microsoft Purview Audit (Standard) i Microsoft 365 kan du søge efter overvågningsposter for aktiviteter, der udføres i de forskellige Microsoft 365 tjenester af brugere og administratorer. Da Overvågning (Standard) er aktiveret som standard for de fleste Microsoft 365 og Office 365 organisationer, er der kun nogle få ting, du skal gøre, før du og andre i din organisation kan søge i overvågningsloggen.

I denne artikel beskrives følgende trin, der er nødvendige for at konfigurere overvågning (Standard).

![Trin til konfiguration af overvågning (Standard).](../media/BasicAuditingWorkflow.png)

Disse trin omfatter sikring af de korrekte organisationsabonnementer og brugerlicenser, der kræves for at generere og bevare overvågningsposter og tildele tilladelser til teammedlemmer af dine sikkerhedshandlinger, it, overholdelse af angivne standarder og juridiske teams, så de kan søge i overvågningsloggen.

Du kan få flere oplysninger [under Overvågning (Standard) i Microsoft 365](auditing-solutions-overview.md#audit-standard).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Trin 1: Bekræft organisationsabonnement og brugerlicenser

Licenser til Overvågning (Standard) kræver det relevante organisationsabonnement, der giver adgang til søgeværktøjet til overvågningslog og licenser pr. bruger, som kræves for at logge og bevare overvågningsposter.

Når en overvåget aktivitet udføres af en bruger eller administrator, oprettes der en overvågningspost, som gemmes i overvågningsloggen for din organisation. I Overvågning (Standard) bevares overvågningsposter, og der kan søges i dem i overvågningsloggen i 90 dage.

Du kan finde en liste over abonnements- og licenskrav til Overvågning (Standard) [under Overvågning af løsninger i Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Trin 2: Tildel tilladelser til at søge i overvågningsloggen

Administratorer og medlemmer af undersøgelsesteams skal tildeles rollen View-Only Overvågningslogge eller Overvågningslogge i Exchange Online for at kunne søge i overvågningsloggen. Disse roller tildeles som standard til rollegrupperne Administration af overholdelse og Organisationsadministration på siden **Tilladelser** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Globale administratorer i Office 365 og Microsoft 365 tilføjes automatisk som medlemmer af rollegruppen Organisationsadministration i Exchange Online. Hvis du vil give en bruger mulighed for at søge i overvågningsloggen med minimumsniveauet for rettigheder, kan du oprette en brugerdefineret rollegruppe i Exchange Online, tilføje rollen View-Only Overvågningslogge eller Overvågningslogge og derefter tilføje brugeren som medlem af den nye rollegruppe. Du kan få flere oplysninger under [Administrer rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

På følgende skærmbillede kan du se de to overvågningsrelaterede roller, der er tildelt rollegruppen Organisationsadministration i Exchange Administration.

![Overvågningsroller, der er tildelt rollegruppen i Exchange Online.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Trin 3: Søg i overvågningsloggen

Nu er du klar til at søge i overvågningsloggen på Microsoft Purview-overholdelsesportalen.

1. Gå til , <https://compliance.microsoft.com> og log på med en konto, der er tildelt de relevante overvågningstilladelser.

2. Klik på **Vis alle** i navigationsruden til venstre på overholdelsesportalen, og klik derefter på **Overvågning**.

3. På siden **Overvågning** skal du konfigurere søgningen ved hjælp af følgende betingelser under fanen **Søg** . 

   ![Konfigurationsindstillinger for søgning i overvågningslog.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Dato- og tidsinterval**. Vælg et dato- og klokkeslætsinterval for at få vist de hændelser, der opstod inden for den pågældende periode. Dato og klokkeslæt vises i lokaltid. De seneste syv dage er valgt som standard.
  
   2. **Aktiviteter**. Vælg de aktiviteter, der skal søges efter. Brug søgefeltet til at søge efter aktiviteter, der skal føjes til listen. Du kan se en delvis liste over overvågede aktiviteter under [Overvågede aktiviteter](search-the-audit-log-in-security-and-compliance.md#audited-activities). Lad dette felt være tomt for at returnere poster for alle overvågede aktiviteter.
  
   3. **Brugere**.  Klik i dette felt, og begynd at skrive navnet på de brugere, der skal vises søgeresultater for. Overvågningslogposterne for de valgte aktiviteter, der er udført af de brugere, du vælger i dette felt, vises på listen over resultater. Lad dette felt være tomt for at returnere poster for alle brugere (og tjenestekonti) i din organisation.
  
   4. **Fil, mappe eller websted**. Skriv et eller hele navnet på en fil eller mappe for at søge efter aktivitet, der er relateret til filen med den mappe, der indeholder det angivne nøgleord. Du kan også angive en URL-adresse til en fil eller mappe. Hvis du bruger en URL-adresse til en fil eller mappe, skal du sørge for at skrive hele URL-stien, eller hvis du skriver en del af URL-adressen, skal du ikke inkludere specialtegn eller mellemrum. Lad dette felt være tomt for at returnere poster for alle filer og mapper i din organisation.

4. Klik på **Søg** for at køre søgningen.

Der vises en ny side, der viser, at søgningen i overvågningsloggen kører. Når søgningen er fuldført, vises overvågningsposter på siden. Klik på en post for at få vist en pop op-side med detaljerede egenskaber.

Du kan finde flere detaljerede instruktioner under [Søg i overvågningsloggen i Overholdelsescenter](search-the-audit-log-in-security-and-compliance.md).
