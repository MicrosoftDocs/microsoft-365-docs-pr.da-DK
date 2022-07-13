---
title: Microsoft 365-tilstandsdashboard
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
description: Få et overblik over Microsoft 365 Health-dashboardet og dets rolle i at holde dig opdateret om tilstanden af din Microsoft 365-organisation.
ms.openlocfilehash: 8ee088f2611cf57576897dc4553ac3f21076f922
ms.sourcegitcommit: aa9e1bceb661df894f66d5dd5f4ab692c870fc71
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66756845"
---
# <a name="microsoft-365-health-dashboard"></a>Microsoft 365 Health-dashboard

Som administrator af din organisation skal du holde mange apps og tjenester kørende uden problemer med en begrænset mængde tid. Vi har oprettet Microsoft 365 Health-dashboardet for at hjælpe dig med at forstå, hvor godt apps og tjenester kører i din organisation.

Dashboardet Tilstand er designet til at give dig et øjebliksbillede af den overordnede tilstand af dit miljø. Du kan se, hvor godt din organisation holder skrivebordssoftwaren opdateret, følge bedste praksis for sikkerhed og bruge de produkter og tjenester, du har betalt for.

> [!NOTE]
> Microsoft 365 Health-dashboard er en offentlig prøveversion og er muligvis ikke tilgængeligt for alle kunder.

## <a name="health-dashboard-in-the-microsoft-365-admin-center"></a>Tilstandsdashboard i Microsoft 365 Administration

1. Log på Administration, og gå derefter til denne URL-adresse: https://admin.microsoft.com/AdminPortal/Home?#/healthoverview.

Du skal være medlem af rollen som global administrator eller global læser for at få adgang til tilstandsdashboardet.

:::image type="content" source="../../media/health-dashboard-view.png" alt-text="Tilstandsdashboard":::

Øverst på dashboardet kan du se vigtige beskeder om eventuelle problemer, der kræver din opmærksomhed.  Der vises to typer meddelelser her:

- Generelle tjenestehændelser.

- Faktureringsproblemer, der kan medføre fremtidige problemer, f.eks. et udløbet abonnement.

Hvis der ikke er nogen beskeder, giver et grønt banner dig besked om, at tilstandsdashboardet ikke fandt nogen problemer.

### <a name="service-health-and-usage"></a>Tjenestetilstand og brug

I midten af siden kan du se den aktuelle tjenestetilstandsstatus for dine mest populære apps og tjenester. Dette er en valgt visning af de mest populære produkter. Hvis du vil se listen over alle dine produkter, kan du følge linket for at se den komplette liste. I dette afsnit kan du også se det gennemsnitlige daglige forbrug og en visning af licensudnyttelsen. Dette hjælper dig med at forstå, hvordan produkter bruges i din organisation.

:::image type="content" source="../../media/service-health-usage.png" alt-text="Skærmbillede: Tilstandsdashboardtjenestetilstand og -forbrug":::

### <a name="microsoft-365-app-updates"></a>Opdateringer til Microsoft 365-apps

For at hjælpe dig med at holde dig ajour med softwareopdateringer giver dette afsnit af dashboardet et hurtigt overblik over, om Microsoft 365-skrivebordsapps som Word, Excel og PowerPoint er opdaterede. Hvis nogle enheder er bagud, får du vist en liste over enheder og sårbarheder, der kan hjælpe dig med at forstå risikoen. Disse oplysninger er baseret på siden Software Opdateringer, som du kan få adgang til for at få flere oplysninger.

:::image type="content" source="../../media/app-updates.png" alt-text="Skærmbillede: Opdateringsoplysninger om tilstandsdashboardapp":::

### <a name="recommended-actions"></a>Anbefalede handlinger

Nederst på dashboardet kan du se anbefalinger til, hvad du kan gøre for at forbedre organisationens tilstand:

- **Slå multifaktorgodkendelse** til: Se en oversigt over, hvor mange konti der i øjeblikket er aktiveret til multifaktorgodkendelse og et link til guiden konfiguration af MFA.

- **Slå månedlige opdateringer til for Office**: Se, om din organisations Office-opdateringshyppighed er angivet, så du modtager opdateringer mere end én gang hver sjette måned.

- **Del OneDrive-træning**: Tilskynd brugerne til at gemme filer i OneDrive for at hjælpe med genoprettelse mod ransomware eller enhedsfejl. Send dem en videooversigt for at hjælpe dem med at konfigurere og bruge OneDrive.

## <a name="note-for-microsoft-enterprise-customers"></a>Note til Microsoft Enterprise-kunder

I den første version af dashboardet Tilstand fokuseres der på mindre it-teams, hvor det er almindeligt, at én person administrerer Microsoft 365. Vi har til hensigt at udvikle dashboardet, så det imødekommer behovet for flere it-roller og større organisationer over tid.
