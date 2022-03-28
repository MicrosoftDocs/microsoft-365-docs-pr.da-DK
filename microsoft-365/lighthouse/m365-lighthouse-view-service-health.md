---
title: Få vist lejertjenestens tilstand
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du får vist lejertjenestens tilstand.
ms.openlocfilehash: 21315d0ea616fcd2865879d9d8aec66b17830208
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597007"
---
# <a name="view-tenant-service-health"></a>Få vist lejertjenestens tilstand

Du kan få vist tjenestestilstanden for de lejere, du administrerer i Microsoft 365 Lighthouse. Tjeneste sundhed omfatter hændelser og rådgivning for flere tjenester, herunder Microsoft Intune, Azure Active Directory (Azure AD) identitetstjenester og administration af mobilenheder (MDM)-skytjenester. Du kan også se, hvor mange af dine administrerede lejere, der påvirkes af hændelser. Hvis en af dine lejere f.eks. oplever problemer, kan du tjekke siden Tjeneste sundhed for at afgøre, om det er et kendt problem med en igangværende løsning, eller om en nylig ændring kan påvirke dem. Dette kan spare dig tid på fejlfinding og reducere supportopkald.

Hvis du ikke kan logge på Lighthouse, kan du bruge statussiden for [Microsoft 365-tjenestetilstand](https://status.office365.com/) til at kontrollere, om der er kendte problemer, der forhindrer dig i at logge på din partnerlejer. Du kan også tilmelde dig for [at @MSFT365status](https://twitter.com/MSFT365Status) på Twitter for at se oplysninger om bestemte tjenestehændelser.

## <a name="before-you-begin"></a>Før du begynder

For at få vist tjeneste sundhed, skal du have en Azure AD-rolle i partnerlejeren med følgende egenskabssæt: **microsoft.office365.serviceHealth/allEntities/allTasks**. Du kan finde en liste over roller i Azure [AD under Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Få vist tjenestetilstandsstatus for alle lejere

1. I venstre navigationsrude i Fyrtårn skal du vælge **Tjeneste sundhed**.

2. På siden **Tjenestetilstand** skal du gennemgå den aktuelle tjenestetilstandsstatus, herunder:

   -   Samlet antal hændelser
   -   Samlet antal råd, der påvirker nogen af de administrerede lejere
   -   Antal tjenester med aktive hændelser.

3. Gennemse problemer **efter tjeneste** under fanen Alle tjenester.

4. Gennemgå **alle aktuelle problemer** under fanen Alle problemer.

## <a name="review-issue-details"></a>Gennemse oplysninger om problem

1. I venstre navigationsrude i Fyrtårn skal du vælge **Tjeneste sundhed**.

2. På siden **Tjenestestilstand** skal du vælge **fanen Alle** tjenester **eller Alle** problemer.

3. Vælg et problem på listen.

4. I ruden med oplysninger om problemet skal du gennemgå detaljerede oplysninger, herunder problemtype, påvirkede lejere, brugerpåvirkning og problemoversigt.

På den **påvirkede** fane Lejere kan du eksportere en liste over berørte lejere til en fil med kommaseparerede værdier (.csv), så du kan dele den med dine supportteams.

## <a name="related-content"></a>Relateret indhold
[Sådan kontrolleres Microsoft 365 tjeneste sundhed](/microsoft-365/enterprise/view-service-health) (artikel)\
[Kendte problemer med Microsoft 365 fyrtårn](m365-lighthouse-known-issues.md) (artikel)