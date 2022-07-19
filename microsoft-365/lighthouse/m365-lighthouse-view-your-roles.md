---
title: Få vist dine Azure Active Directory-roller i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: magarlan, chrigreen
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
description: For MSP-teknikere (Managed Service Provider) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du får vist dine Azure Active Directory-roller (Azure AD) på tværs af de forskellige kundelejere, som din organisation administrerer.
ms.openlocfilehash: 6f12bef7a1e7958b345a86dbc9d0e2ee76534885
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66858699"
---
# <a name="view-your-azure-active-directory-roles-in-microsoft-365-lighthouse"></a>Få vist dine Azure Active Directory-roller i Microsoft 365 Lighthouse

Denne artikel indeholder instruktioner til, hvordan du får vist dine Azure Active Directory-roller (Azure AD) på tværs af de forskellige kundelejere, som din organisation administrerer. Din rolle bestemmer, hvilke handlinger du kan udføre i Lighthouse.

## <a name="before-you-begin"></a>Før du begynder

Du skal have adgang til en partnerlejer, der er onboardet til Tjenesten Microsoft 365 Lighthouse.

## <a name="view-your-roles"></a>Få vist dine roller

1. Vælg **Lejere** i navigationsruden til venstre i Lighthouse.

2. Vælg et vilkårligt lejernavn på lejerlisten for at åbne lejerens **oversigtsside** .

3. Ud for **Roller** skal du vælge det link, der angiver antallet af roller, du har i lejeren. Siden **Roller** åbnes.

    Hvis du har en eller flere roller i en kundelejer, får du vist et grønt flueben i kolonnen **Aktiveret** for den pågældende lejer sammen med det antal roller, du har. Hvis du ikke har nogen roller i en lejer, får du vist et rødt **X**.
 
4. For kundelejere med et grønt flueben ud for dem skal du udvide lejeren for at se en liste over roller, du har i den pågældende lejer. Du kan få flere oplysninger om Azure AD roller og de tilladelser, de tildeler, [under Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).

    På siden **Roller** vises også eventuelle brugerdefinerede mærker, der er anvendt på dine lejere. Du kan filtrere dataene på siden efter tildelte roller eller mærker.

## <a name="next-steps"></a>Næste trin

Hvis du ikke har tilladelse til at udføre en handling, du skal udføre i Lighthouse, skal du kontakte en administrator i din partnerlejer, som kan tildele dig den relevante rolle for den handling, du forsøger at udføre.

## <a name="related-content"></a>Relateret indhold

[Oversigt over tilladelser i Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) (artikel)\
[Administrer din lejerliste i Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md) (artikel)
