---
title: Installer konfigurerbare indstillinger i Microsoft Managed Desktop
description: Installér og spor konfigurerbare indstillingersændringer i Microsoft Managed Desktop.
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation, installation, faseudrulning, konfigurerbare indstillinger
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a52995ff9ab2f946ca11417d4ed7bfa13825353f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587468"
---
# <a name="deploy-and-track-configurable-settings---microsoft-managed-desktop"></a>Installér og spor konfigurerbare indstillinger – Microsoft Managed Desktop

Når du har foretaget ændringer i dine indstillingskategorier og faseudrulning af en installation, kan du med statussiden for Installation begynde at udrulle dine indstillinger i grupper. Denne side viser en oversigt over hver konfigurerbar indstilling. Når du åbner en indstillingskategori, kan du installere indstillinger for grupper og spore status for disse installationer.

## <a name="deployment-statuses"></a>Installationsstatusser

Følgende er de statusser, du får vist for hver installation.

Status | Forklaring
--- | ---
Installér | Din ændring venter på at blive udrullet til denne gruppe.
I gang | Ændringen anvendes på aktive enheder i denne gruppe.
Fuldført | Ændringen blev gennemført på alle aktive enheder i denne gruppe.
Mislykkedes | Ændringen mislykkedes på 10 procent af aktive enheder i gruppen. Installationen blev stoppet.<br><br> En supportanmodning åbnes automatisk med Microsoft Managed Desktop-handlinger til fejlfinding af installationen.
Gendannet | Ændringen blev gendannet til den seneste ændring, der blev installeret på alle installationsgrupper.

## <a name="deploy-changes"></a>Installér ændringer

Som et eksempel bruger vi et baggrundsbillede på skrivebordet i denne vejledning. Når du har indrullet en installation, kan du installere ændringer fra statussiden for Installation.

**Sådan installeres ændringer:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. Vælg den **indstilling** , du vil installere, i arbejdsområdet Installationsstatus. Vælg derefter den fasede installation, der skal installeres.
4. Vælg **Installer** for at installere ændringen i en af installationsgrupperne.

> [!NOTE]
> Det orange advarselsikon angiver, at en tidligere gruppe kan installeres, da det anbefales at udrulle den i rækkefølge.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Trusted sites pane on the right. In the Deployment groups section are three columns: deployment groups, devices, and status. In the status column, "deploy" is highlighted.](../../media/1deployedit.png) -->

Vi anbefaler at udrulle til installationsgrupper i denne rækkefølge: Test, Først, Hurtig og derefter Bred.

Når ændringerne er fuldført i hver gruppe, ændres status til **Fuldført**.

<!-- Needs picture updated to show MEM ![Deployment status workspace with columns for date updated, version, test, first, fast, and broad. The Proxy row is expanded, showing a dated setting flagged as "complete" in each of the four deployment groups.](../../media/2completeedit.png) -->

## <a name="revert-deployment"></a>Gendan udrulning

Når du har installeret en ændring, kan du gå tilbage fra **Installationsstatus**. Når du gendanner en ændring, der **er i gang** eller **fuldført**, stopper den aktuelle installation. Indstillingen vender tilbage til den seneste version, der blev installeret i alle grupper.

Som et eksempel vil vi gendanne baggrundsbilledet på skrivebordet.

**Sådan gendannes en ændring:**

1. Log på [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) og gå til **menuen** Enheder.
2. I sektionen Microsoft Managed Desktop skal du vælge **Indstillinger**.
3. Vælg den **indstilling** , du vil gendanne, i arbejdsområdet Installationsstatus. Vælg derefter den fasede installation for at vende tilbage.
4. Under **Skal du gendanne denne ændring? skal du** vælge **Gendan installation**.

<!-- Needs picture updated to show MEM ![Deployment status workspace. Browser start pages is selected, opening a pane on the right side with data about the submitted change and its status. At the bottom is the "need to revert this change" area where you can select "Revert deployment."](../../media/3revert.png) -->

## <a name="additional-resources"></a>Yderligere ressourcer

- [Oversigt over konfigurerbare indstillinger](config-setting-overview.md)
- [Reference til konfigurerbare indstillinger](config-setting-ref.md)
