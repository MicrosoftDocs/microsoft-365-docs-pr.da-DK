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
description: Få mere at vide om, hvordan du tildeler licenser til grupper til brug med enheder.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 08/27/2021
ms.openlocfilehash: fd452cb52a1c65a59e478fb80438ac95a57e8bf6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588486"
---
# <a name="manage-licenses-for-devices"></a>Administrer licenser til enheder

Hvis du har Microsoft 365 Apps for enterprise (enhed) eller Microsoft 365 Apps Education (enhed), kan du tildele licenser til enheder ved hjælp af Azure AD-grupper. Når en enhed har en licens, kan alle, der bruger enheden, Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus). Lad os f.eks. sige, at du har 20 bærbare computere og tablets, der bruges af personer i organisationen. Når du tildeler en licens til hver enhed, bruger hver person, der logger på en af enhederne, Microsoft 365 Apps for enterprise uden behov for deres egen licens.

> [!IMPORTANT]
> Enhedsbaserede licenser til Microsoft 365 Apps for enterprise fås kun som en tilføjelseslicens for nogle erhvervskunder og nogle uddannelseskunder. For kommercielle kunder er licensen *tilgængelig Microsoft 365 Apps for enterprise (enhed)* og er kun tilgængelig via Enterprise Agreement/Enterprise Agreement abonnement. For Education-kunder er licensen *Microsoft 365 Apps for Education (enhed)* og er kun tilgængelig via Enrollment for Education Solutions (EES). Du kan finde flere oplysninger i blogindlægget om [tilgængelighed af uddannelse](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). For kommerciel tilgængelighed skal du kontakte din Microsoft-kunderepræsentant.

Til at begynde med skal du oprette en gruppe Azure Active Directory Administration og derefter tildele enheder til gruppen. Du kan få mere at vide om enhedslicenser, herunder enhedskrav, hvilke typer grupper du kan bruge, og hvordan du konfigurerer Microsoft 365 Apps for enterprise til at bruge enhedslicenser, under Enhedsbaserede licenser [til Microsoft 365 Apps for enterprise](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Du skal være global administrator for at udføre opgaverne i denne artikel.

## <a name="assign-licenses-to-devices"></a>Tildel licenser til enheder

Når du tildeler licenser til en gruppe, tildeler du licenser til alle enheder inden for gruppen. Du kan kun tildele ét abonnement til en enkelt gruppe.

1. I Microsoft 365 Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > .
2. På siden **Licenser** skal du **vælge Microsoft 365 Apps for Education (enhed)** eller **Microsoft 365 Apps for enterprise (enhed)**.
3. På næste side skal du vælge et abonnement og derefter vælge **Tildel licenser**.
4. Begynd at **skrive et gruppenavn i** ruden Tildel licenser til en gruppe, og vælg det derefter blandt resultaterne for at føje det til listen.
5. Vælg **Tildel**, og vælg derefter **Luk**.

## <a name="unassign-licenses-from-devices"></a>Fjern tildeling af licenser fra enheder

Når du ophæver tildelingen af licenser fra en gruppe, fjerner du licenserne fra alle enheder i gruppen. Alle apps og deres tilknyttede data er derefter skrivebeskyttede.

1. I Administration skal du gå til **siden** <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > .
2. På siden **Licenser** skal du **vælge Microsoft 365 Apps for Education (enhed)** eller **Microsoft 365 Apps for enterprise (enhed)**.
3. På næste side skal du vælge et abonnement, vælge de tre prik (flere handlinger) og derefter vælge **Fjern tildeling af licenser**.
4. Vælg **Fjern tildeling i** dialogboksen Fjern **tildeling af licenser**.
