---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: 9be6e2c31177d0fbfe2b896aa5e346d2aafc3aea
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823882"
---
Hvis du vil fuldføre trinnene i denne artikel, skal du være global administrator af Microsoft 365 eller administrator af Shifts-connectoren.

 Rollen Shifts-connectoradministrator er en brugerdefineret rolle, som du opretter i Azure AD og tildeler til en bruger. Navnet på rollen skal være "Skifts connector-administrator". Rollen behøver ikke at have nogen specifikke tilladelser, selvom der skal angives mindst én tilladelse, når du opretter den. Tjenesten er afhængig af tilstedeværelsen af rollen på brugeren og ikke dens tilladelser.  Du kan få mere at vide under [Opret og tildel en brugerdefineret rolle i Azure AD](/azure/active-directory/roles/custom-create) og [Tildel Azure AD roller til brugere](/azure/active-directory/roles/manage-roles-portal). Vær opmærksom på, at det kan tage op til 24 timer, før rollen oprettes og anvendes på en bruger.