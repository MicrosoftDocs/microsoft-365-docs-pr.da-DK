---
title: Microsoft Defender Security Center dashboard med sikkerhedshandlinger
description: Brug dashboardet til at identificere risikoenheder, holde styr på tjenestens status og se statistik og oplysninger om enheder og beskeder.
keywords: dashboard, beskeder, ny, i gang, løst, risiko, risiko, enheder med risiko, instruktioner, rapportering, statistik, diagrammer, grafer, tilstand, aktive malwareregistreringer, trusselskategori, kategorier, adgangskodesvælger, ransomware, udnyttelse, trussel, lav alvorsgrad, aktiv malware
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c08f592ac72be10bb4b967521e7e504a9ae70a86
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472633"
---
# <a name="microsoft-defender-security-center-security-operations-dashboard"></a>Microsoft Defender Security Center dashboard med sikkerhedshandlinger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

**Dashboardet Sikkerhedshandlinger** er det sted, slutpunktsregistrering og -svar egenskaber vises. Den giver en detaljeret oversigt over, hvor registreringer blev set, og fremhæver, hvor der er behov for svarhandlinger.

Dashboardet viser et øjebliksbillede af:

- Aktive beskeder
- Enheder, der er i fare
- Sensorens tilstand
- Tjenestetilstand
- Rapportering af daglige enheder
- Aktive automatiserede undersøgelser
- Automatiserede undersøgelsesstatistik
- Brugere, der er i fare
- Mistænkelige aktiviteter

:::image type="content" source="images/atp-sec-ops-dashboard.png" alt-text="Dashboardet Sikkerhedshandlinger" lightbox="images/atp-sec-ops-dashboard.png":::

Du kan undersøge og undersøge beskeder og enheder for hurtigt at afgøre, om, hvor og hvornår mistænkelige aktiviteter forekom i dit netværk for at hjælpe dig med at forstå den kontekst, de blev vist i.

Fra **dashboardet Sikkerhedshandlinger** kan du se aggregerede hændelser for at gøre det lettere at identificere væsentlige hændelser eller funktionsmåder på en enhed. Du kan også analysere ned i detaljerede hændelser og indikatorer på lavniveau.

Den har også klikbare felter, der giver visuelle tegn på organisationens generelle tilstand. Hvert felt åbner en detaljeret visning af den tilsvarende oversigt.

## <a name="active-alerts"></a>Aktive beskeder

Du kan få vist det samlede antal aktive beskeder fra de seneste 30 dage i dit netværk fra feltet. Beskeder er grupperet ind i **Ny** og **I gang**.

:::image type="content" source="images/active-alerts-tile.png" alt-text="Siden Aktive beskeder" lightbox="images/active-alerts-tile.png":::

Hver gruppe under kategoriseres yderligere i deres tilsvarende alvorsgrader. Klik på antallet af beskeder i hver beskedring for at få vist en sorteret visning af den pågældende kategoris kø (**Ny** **eller I gang**).

Få mere at vide under [Oversigt over beskeder](alerts-queue.md).

Hver række indeholder en alvorsgradskategori for beskeden og en kort beskrivelse af beskeden. Du kan klikke på en besked for at få vist dens detaljerede visning. Få mere at vide [under Undersøg Microsoft Defender for Endpoint oversigt over](investigate-alerts.md) [vigtige beskeder og beskeder](alerts-queue.md).

## <a name="devices-at-risk"></a>Enheder, der er i fare

Dette felt viser dig en liste over enheder med det højeste antal aktive beskeder. Det samlede antal beskeder for hver enhed vises i en cirkel ud for enhedsnavnet og derefter yderligere kategoriseret efter alvorsniveauer i den anden ende af feltet (hold markøren over hver alvorsgradslinje for at se dens etiket).

:::image type="content" source="images/devices-at-risk-tile.png" alt-text="Siden Enheder, der er i fare" lightbox="images/devices-at-risk-tile.png":::

Klik på navnet på enheden for at få vist detaljer om enheden. Du kan få mere at [vide under Undersøg enheder Microsoft Defender for Endpoint listen Over enheder](investigate-machines.md).

Du kan også klikke **på listen** Enheder øverst i feltet for at gå direkte til listen **Enheder sorteret** efter antallet af aktive beskeder. Du kan få mere at [vide under Undersøg enheder Microsoft Defender for Endpoint listen Over enheder](investigate-machines.md).

## <a name="devices-with-sensor-issues"></a>Enheder med sensorproblemer

Feltet **Enheder med sensorproblemer** angiver oplysninger om den enkelte enheds mulighed for at levere sensordata til Microsoft Defender for Endpoint enheden. Den rapporterer, hvor mange enheder der kræver opmærksomhed, og hjælper dig med at identificere problematiske enheder.

:::image type="content" source="images/atp-tile-sensor-health.png" alt-text="Feltet Enheder med sensorproblemer" lightbox="images/atp-tile-sensor-health.png":::

Der er to statusindikatorer, der angiver oplysninger om antallet af enheder, der ikke rapporterer korrekt til tjenesten:

- **Forkert konfigureret**: Disse enheder rapporterer muligvis delvist sensordata til Microsoft Defender for Endpoint og kan have konfigurationsfejl, der skal rettes.
- **Inaktiv**: Enheder, der er holdt op med at rapportere til Microsoft Defender for Endpoint-tjenesten i mere end syv dage i den seneste måned.

Når du klikker på en af grupperne, bliver du ført til listen over enheder, filtreret efter eget valg. Få mere at vide under [Kontrollér sensortilstand og](check-sensor-status.md) [Undersøg enheder](investigate-machines.md).

## <a name="service-health"></a>Tjenestetilstand

Feltet **Tjenestetilstand** giver dig besked, hvis tjenesten er aktiv, eller hvis der er problemer.

:::image type="content" source="images/status-tile.png" alt-text="Siden Tjenestetilstand side" lightbox="images/status-tile.png":::

Du kan finde flere oplysninger om [tjenestetjenestens tilstand under Microsoft Defender for Endpoint af tjenesten](service-status.md).

## <a name="daily-devices-reporting"></a>Rapportering af daglige enheder

**Rapporteringsfeltet Daglige enheder** viser et søjlediagram, der repræsenterer antallet af enheder, der rapporterer dagligt inden for de seneste 30 dage. Hold markøren over individuelle søjler på grafen for at få vist det nøjagtige antal enheder, der rapporterer på hver dag.

:::image type="content" source="images/atp-daily-devices-reporting.png" alt-text="Feltet til rapportering af daglige enheder" lightbox="images/atp-daily-devices-reporting.png":::

## <a name="active-automated-investigations"></a>Aktive automatiserede undersøgelser

Du kan se det samlede antal automatiserede undersøgelser fra de seneste 30 dage i dit netværk fra feltet **Aktive automatiserede** undersøgelser. Undersøgelser grupperes i **Afventende handling**, **Venter på enhed** og **Kører**.

:::image type="content" source="images/atp-active-investigations-tile.png" alt-text="De aktive automatiserede undersøgelser" lightbox="images/atp-active-investigations-tile.png":::

## <a name="automated-investigations-statistics"></a>Automatiserede undersøgelsesstatistik

Dette felt viser statistik, der er relateret til automatiserede undersøgelser i de seneste syv dage. Den viser antallet af afsluttede undersøgelser, antallet af afhjælpede undersøgelser, den gennemsnitlige ventende tid, det tager at igangsætte en undersøgelse, den gennemsnitlige tid, det tager at afhjælpe en besked, antallet af undersøgede beskeder og det antal timer automatisering, der er gemt fra en typisk manuel undersøgelse. 

:::image type="content" source="images/atp-automated-investigations-statistics.png" alt-text="Den automatiserede undersøgelsesstatistik" lightbox="images/atp-automated-investigations-statistics.png":::

Du kan klikke på **Automatiserede** **undersøgelser, Afhjælpede** undersøgelser og Vigtige beskeder, der er undersøgt, for at gå  til siden Undersøgelser, filtreret efter den relevante kategori. Dette giver dig mulighed for at få vist en detaljeret beskrivelse af undersøgelser i konteksten.

## <a name="users-at-risk"></a>Brugere, der er i fare

Feltet viser dig en liste over brugerkonti med de mest aktive beskeder og antallet af vigtige beskeder i høj, mellem eller lav. 

:::image type="content" source="images/atp-users-at-risk.png" alt-text="Siden Brugere, der er i fare" lightbox="images/atp-users-at-risk.png":::

Klik på brugerkontoen for at få vist detaljer om brugerkontoen. Få mere at vide under [Undersøg en brugerkonto](investigate-user.md).

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Forstå Microsoft Defender for Endpoint portalen](use.md)
- [Portaloversigt](portal-overview.md)
- [Se dashboardet til & mod sikkerhedsrisiko](tvm-dashboard-insights.md)
- [Få vist dashboardet for Trusselsanalyse, og tag anbefalede afhjælpningshandlinger](threat-analytics.md)
