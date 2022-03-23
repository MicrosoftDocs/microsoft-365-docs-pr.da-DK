---
title: Konfigurer Grundlæggende overvågning i Microsoft 365
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
description: Denne artikel beskriver, hvordan du konfigurerer Grundlæggende overvågning, så du kan begynde at søge efter overvågningsaktiviteter, der udføres af brugere og administratorer i organisationen.
ms.openlocfilehash: e4ae5901c9a4f400e2a01659395d27947ad433c2
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63593276"
---
# <a name="set-up-basic-audit-in-microsoft-365"></a>Konfigurer Grundlæggende overvågning i Microsoft 365

Med Grundlæggende overvågning i Microsoft 365 kan du søge efter overvågningsposter for aktiviteter, der er udført i de Microsoft 365 tjenester af brugere og administratorer. Da Grundlæggende overvågning er aktiveret som standard for de fleste Microsoft 365- og Office 365-organisationer, er der kun nogle få ting, du skal gøre, før du og andre i organisationen kan søge i overvågningsloggen.

I denne artikel beskrives følgende nødvendige trin for at konfigurere Grundlæggende overvågning.

![Trin til at konfigurere Grundlæggende overvågning.](../media/BasicAuditingWorkflow.png)

Disse trin omfatter at sikre de korrekte organisationsabonnementer og brugerlicenser, der kræves for at oprette og bevare overvågningsposter og tildele tilladelser til teammedlemmer af dine sikkerhedshandlinger, it-, overholdelses- og juridiske teams, så de kan søge i overvågningsloggen.

Du kan finde flere oplysninger [under Grundlæggende overvågning i Microsoft 365](auditing-solutions-overview.md#basic-audit).

## <a name="step-1-verify-organization-subscription-and-user-licensing"></a>Trin 1: Bekræft organisationsabonnement og brugerlicens

Licensering til grundlæggende overvågning kræver det relevante organisationsabonnement, der giver adgang til søgeværktøjet til overvågningslogfiler og pr. bruger-licensering, der kræves for at logføre og bevare overvågningsposter.

Når en overvåget aktivitet udføres af en bruger eller administrator, genereres og gemmes en overvågningspost i overvågningsloggen for organisationen. I Grundlæggende overvågning bevares overvågningsposter, og der kan søges i overvågningsloggen i 90 dage.

Du kan finde en liste over abonnements- og licenskrav til Grundlæggende overvågning under [Revisionsløsninger Microsoft 365](auditing-solutions-overview.md#licensing-requirements).

## <a name="step-2-assign-permissions-to-search-the-audit-log"></a>Trin 2: Tildel tilladelser til at søge i overvågningsloggen

Administratorer og medlemmer af undersøgelsesteams skal have tildelt rollen View-Only overvågningslogfiler eller overvågningslogfiler i Exchange Online til at søge i overvågningsloggen. Disse roller **tildeles** som standard rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Globale administratorer i Office 365 og Microsoft 365 tilføjes automatisk som medlemmer af rollegruppen Organisationsadministration i Exchange Online. Hvis du vil give en bruger mulighed for at søge i overvågningsloggen med det mindste niveau af rettigheder, kan du oprette en brugerdefineret rollegruppe i Exchange Online, tilføje rollen View-Only-overvågningslogfiler eller Overvågningslogfiler og derefter tilføje brugeren som medlem af den nye rollegruppe. Du kan finde flere oplysninger [i Administrere rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

Følgende skærmbillede viser de to overvågningsrelaterede roller, der er tildelt rollegruppen Organisationsadministration i Exchange Administration.

![Overvågningsroller, der er tildelt rollegruppen i Exchange Online.](../media/EACAuditRoles.png)

## <a name="step-3-search-the-audit-log"></a>Trin 3: Søg i overvågningsloggen

Nu er du klar til at søge i overvågningsloggen i Microsoft 365 Overholdelsescenter.

1. Gå til <https://compliance.microsoft.com> og log på med en konto, der har fået tildelt de relevante overvågningstilladelser.

2. Klik på Vis Microsoft 365 Overholdelsescenter navigationsruden i venstre **navigationsrude**, og klik derefter på **Overvågning**.

3. På siden **Overvågning** skal du konfigurere søgningen ved at bruge følgende betingelser på **fanen** Søg. 

   ![Konfigurationsindstillinger for søgning i overvågningslogfil.](../media/AuditLogSearchToolMCCCallouts.png)

   1. **Dato- og tidsinterval**. Vælg en dato og et tidsinterval for at få vist de hændelser, der er opstået inden for den pågældende periode. Dato og klokkeslæt vises lokalt. De seneste syv dage er valgt som standard.
  
   2. **Aktiviteter**. Vælg de aktiviteter, du vil søge efter. Brug søgefeltet til at søge efter aktiviteter, der skal føjes til listen. Du kan se en delvis liste over overvågede aktiviteter [under Overvågede aktiviteter](search-the-audit-log-in-security-and-compliance.md#audited-activities). Lad dette felt være tomt for at returnere poster for alle reviderede aktiviteter.
  
   3. **Brugere**.  Klik i dette felt, og begynd at skrive navnet på de brugere, der skal vises søgeresultater for. Poster i overvågningsloggen for de markerede aktiviteter, der udføres af de brugere, du vælger i dette felt, vises på listen over resultater. Lad dette felt være tomt for at returnere poster for alle brugere (og tjenestekonti) i organisationen.
  
   4. **Fil, mappe eller websted**. Skriv en del af eller hele navnet på en fil eller mappe for at søge efter aktivitet relateret til den fil i mappen, der indeholder det angivne nøgleord. Du kan også angive en URL-adresse til en fil eller mappe. Hvis du bruger en URL-adresse til en fil eller mappe, skal du sørge for at skrive den fulde URL-sti, eller hvis du skriver en del af URL-adressen, skal du ikke medtage nogen specialtegn eller mellemrum. Lad dette felt være tomt for at returnere poster for alle filer og mapper i organisationen.

4. Klik **på** Søg for at køre søgningen.

Der vises en ny side, der viser, at søgningen i overvågningsloggen kører. Når søgningen er fuldført, vises overvågningsposterne på siden. Klik på en post for at få vist en pop op-side med detaljerede egenskaber.

Du kan finde en mere detaljeret vejledning [under Søg i overvågningsloggen i overholdelsescenteret](search-the-audit-log-in-security-and-compliance.md).
