---
title: Få vist lejerens tjenestetilstand i Microsoft 365 Fyrtårn
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: chboyd
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
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du får vist tilstanden for lejertjenesten.
ms.openlocfilehash: 53424b98dc47e16971322260a93e30eb707161a7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66007146"
---
# <a name="view-tenant-service-health-in-microsoft-365-lighthouse"></a>Få vist lejerens tjenestetilstand i Microsoft 365 Fyrtårn

Du kan få vist tjenestetilstanden for de lejere, du administrerer i Microsoft 365 Lighthouse. Tjenestetilstand omfatter hændelser og gode råd til flere tjenester, herunder Microsoft Intune, Azure Active Directory (Azure AD) identitetstjenester og MDM-cloudtjenester (Mobile Device Management). Du kan også se, hvor mange af dine administrerede lejere der påvirkes af hændelser. Hvis en af dine lejere f.eks. oplever problemer, kan du kontrollere siden Tjenestetilstand for at finde ud af, om det er et kendt problem med en igangværende løsning, eller om en nylig ændring kan påvirke dem. Det kan spare dig tid ved fejlfinding og reducere supportopkald.

Hvis du ikke kan logge på Lighthouse, kan du bruge [siden Microsoft 365 tjenestetilstandsstatus](https://status.office365.com/) til at kontrollere, om der er kendte problemer, der forhindrer dig i at logge på din partnerlejer. Du kan også tilmelde dig for at følge [@MSFT365status](https://twitter.com/MSFT365Status) på Twitter for at få vist oplysninger om specifikke tjenestehændelser.

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil have vist tjenestetilstand, skal du have en Azure AD rolle i partnerlejer med følgende **egenskabssæt: microsoft.office365.serviceHealth/allEntities/allTasks**. Du kan se en liste over Azure AD roller [under Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Vis tjenestetilstandsstatus for alle lejere

1. Vælg **Tjenestetilstand** i navigationsruden til venstre i Lighthouse.

2. Gennemse den aktuelle tjenestetilstandsstatus på siden **Tjenestetilstand**, herunder:

   - Samlet antal hændelser
   - Det samlede antal rådgivere, der påvirker nogen af de administrerede lejere
   - Antal tjenester med aktive hændelser.

3. Gennemse problemer efter tjeneste under fanen **Alle tjenester** .

4. Gennemse alle aktuelle problemer under fanen **Alle problemer** .

## <a name="review-issue-details"></a>Gennemse oplysninger om problem

1. Vælg **Tjenestetilstand** i navigationsruden til venstre i Lighthouse.

2. På siden **Tjenestetilstand** skal du vælge fanen **Alle tjenester** eller **Alle problemer**.

3. Vælg et problem på listen.

4. Gennemse detaljerede oplysninger i ruden med problemoplysninger, herunder problemtype, berørte lejere, brugerpåvirkning og problemhistorik.

Under fanen **Berørte lejere** kan du eksportere en liste over berørte lejere til en fil med kommaseparerede værdier (.csv), så du kan dele den med dine supportteams.

## <a name="related-content"></a>Relateret indhold

[Sådan kontrollerer du Microsoft 365 tjenestetilstand](/microsoft-365/enterprise/view-service-health) (artikel)\
[Kendte problemer med Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (artikel)\
[Få vist dine Azure Active Directory roller i Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (artikel)
