---
title: Få vist en mislykket netværksforbindelse for en cloud-pc i virksomheden i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
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
description: For MSP'er (Managed Service Providers), der bruger Microsoft 365 Lighthouse, kan du få mere at vide om, hvordan du får vist en netværksforbindelse, der mislykkedes på en cloud-pc i virksomheden.
ms.openlocfilehash: 273e0737cbe59d9ecae40fad0c114f58881a5d05
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859110"
---
# <a name="view-an-enterprise-cloud-pc-failed-network-connection-in-microsoft-365-lighthouse"></a>Få vist en mislykket netværksforbindelse for en cloud-pc i virksomheden i Microsoft 365 Lighthouse

Microsoft 365 Lighthouse leverer forbindelsesstatussen mellem dine kundelejere og Azure Active Directory (Azure AD). Når en Cloud-pc har en mislykket netværksforbindelse, kan du få vist detaljerede oplysninger i Microsoft Endpoint Manager Administration.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være global administrator i partnerlejer.
- Du skal have cloud-pc-administrator eller Cloud PC Reader-adgang for at få vist forbindelsesproblemer.

## <a name="view-a-failed-network-connection"></a>Få vist en mislykket netværksforbindelse

1. Vælg **Enheder** >  i venstre navigationsrude i Lighthouse **Windows 365**.

2. Vælg fanen **Azure-netværksforbindelser** .

3. I afsnittet **forbindelsesoversigt** skal du vælge Mislykkede forbindelser.

4. På den filtrerede liste skal du vælge **Få vist forbindelsesoplysninger i Microsoft Endpoint Manager** ud for den forbindelse, du vil undersøge.

5. I Microsoft Endpoint Manager Administration skal du vælge **Få vist detaljer** for at få mere at vide om fejlen.

## <a name="next-steps"></a>Næste trin

Hvis du vil foretage fejlfinding af forbindelsesproblemer, skal [du se Fejlfinding af netværksforbindelse i det lokale miljø](/windows-365/enterprise/troubleshoot-on-premises-network-connection).

## <a name="related-content"></a>Relateret indhold

[Rollebaseret adgangskontrol i cloud-pc ](/windows-365/enterprise/role-based-access)(artikel)\
[Active Directory-domænejoinforbindelse](/windows-365/enterprise/troubleshoot-on-premises-network-connection#active-directory-domain-join) (artikel)\
[Synkronisering af Azure Active Directory-enhed](/windows-365/enterprise/troubleshoot-on-premises-network-connection#azure-active-directory-device-sync) (artikel)
