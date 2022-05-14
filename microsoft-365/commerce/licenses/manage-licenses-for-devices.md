---
title: Administrer licenser til enheder
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
description: Få mere at vide om, hvordan du tildeler licenser til grupper til brug sammen med enheder.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 05/12/2022
ms.openlocfilehash: 5603fd947abdfbc6bede01fe7545a5a0fa99a67d
ms.sourcegitcommit: 4e7ff69f4d7d27c2d419f763cfcb069e3b0d0d9f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65403266"
---
# <a name="manage-licenses-for-devices"></a>Administrer licenser til enheder

Hvis du har Microsoft 365 Apps for enterprise (enhed) eller Microsoft 365 Apps for Education (enhed), kan du tildele licenser til enheder ved hjælp af Azure AD grupper. Når en enhed har en licens, kan alle, der bruger den pågældende enhed, bruge Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus). Lad os f.eks. sige, at du har 20 bærbare computere og tablets, der bruges af personer i din organisation. Når du tildeler en licens til hver enhed, bruger hver person, der logger på en af enhederne, Microsoft 365 Apps for enterprise uden behov for deres egen licens.

> [!IMPORTANT]
> Enhedsbaserede licenser til Microsoft 365 Apps for enterprise er kun tilgængelige som en tilføjelseslicens til nogle kommercielle kunder og nogle uddannelseskunder. For kommercielle kunder er licensen *Microsoft 365 Apps for enterprise (enhed)* og er kun tilgængelig via abonnementet på Enterprise Agreement/Enterprise Agreement. For uddannelseskunder er licensen *Microsoft 365 Apps for Education (enhed)* og er kun tilgængelig via EES (Enrollment for Education Solutions). Du kan få flere oplysninger ved at læse blogindlægget om [tilgængelighed af uddannelse](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). Kontakt din Microsoft-kontorepræsentant for at få kommerciel tilgængelighed.

Du skal først oprette en gruppe i Azure Active Directory Administration og derefter tildele enheder til gruppen. Hvis du vil vide mere om enhedslicensering, herunder enhedskrav, hvilke typer grupper du kan bruge, og hvordan du konfigurerer Microsoft 365 Apps for enterprise til at bruge enhedslicenser, skal du se [Enhedsbaserede licenser for Microsoft 365 Apps for enterprise](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Du skal være global administrator for at kunne udføre opgaverne i denne artikel.

## <a name="assign-licenses-to-devices"></a>Tildel licenser til enheder

Når du tildeler licenser til en gruppe, tildeler du licenser til alle enheder i gruppen. Du kan kun tildele ét abonnement til en enkelt gruppe.

1. I Microsoft 365 Administration skal du gå til siden **FaktureringLicenser** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Vælg **Microsoft 365 Apps for Education (enhed)** eller **Microsoft 365 Apps for enterprise (enhed)** på siden **Licenser**.
3. Vælg et abonnement på næste side, og vælg derefter **Tildel licenser**.
4. I ruden **Tildel licenser til en gruppe** skal du begynde at skrive et gruppenavn og derefter vælge det fra resultaterne for at føje det til listen.
5. Vælg **Tildel**, og vælg derefter **Luk**.

## <a name="unassign-licenses-from-devices"></a>Fjern tildeling af licenser fra enheder

Når du fjerner tildelingen af licenser fra en gruppe, fjerner du licenserne fra alle enheder i gruppen. Alle apps og deres tilknyttede data er derefter skrivebeskyttede.

1. I Administration skal du gå til siden **FaktureringLicenser** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. Vælg **Microsoft 365 Apps for Education (enhed)** eller **Microsoft 365 Apps for enterprise (enhed)** på siden **Licenser**.
3. Vælg et abonnement på næste side, vælg de tre prikker (flere handlinger), og vælg derefter **Fjern tildeling af licenser**.
4. I dialogboksen **Fjern tildeling af licenser** skal du vælge **Fjern tildeling**.
