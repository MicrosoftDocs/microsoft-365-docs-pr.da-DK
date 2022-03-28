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
ms.openlocfilehash: bf0eb7b210ccb033e47b86b45a5f4dec00e9d795
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597580"
---
# <a name="microsoft-defender-security-center-security-operations-dashboard"></a>Microsoft Defender Security Center dashboard med sikkerhedshandlinger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

**Dashboardet Sikkerhedshandlinger** er det sted, slutpunktsregistrering og -svar egenskaber vises. Den giver en detaljeret oversigt over, hvor registreringer blev set, og fremhæver, hvor der er behov for svarhandlinger.

Dashboardet viser et øjebliksbillede af:

- Aktive beskeder
- Enheder, der er i fare
- Sensorens tilstand
- Tjeneste sundhed
- Rapportering af daglige enheder
- Aktive automatiserede undersøgelser
- Automatiserede undersøgelsesstatistik
- Brugere, der er i fare
- Mistænkelige aktiviteter

![Billede af dashboard for sikkerhedshandlinger.](images/atp-sec-ops-dashboard.png)

Du kan undersøge og undersøge beskeder og enheder for hurtigt at afgøre, om, hvor og hvornår mistænkelige aktiviteter forekom i dit netværk for at hjælpe dig med at forstå den kontekst, de blev vist i.

Fra **dashboardet Sikkerhedshandlinger** kan du se aggregerede hændelser for at gøre det lettere at identificere væsentlige hændelser eller funktionsmåder på en enhed. Du kan også analysere ned i detaljerede hændelser og indikatorer på lavniveau.

Den har også klikbare felter, der giver visuelle tegn på organisationens generelle tilstand. Hvert felt åbner en detaljeret visning af den tilsvarende oversigt.

## <a name="active-alerts"></a>Aktive beskeder

Du kan få vist det samlede antal aktive beskeder fra de seneste 30 dage i dit netværk fra feltet. Beskeder er grupperet ind i **Ny** og **I gang**.

![Klik på hvert udsnit eller alvorsgrad for at få vist en liste over beskeder fra de seneste 30 dage.](images/active-alerts-tile.png)

Hver gruppe under kategoriseres yderligere i deres tilsvarende alvorsgrader. Klik på antallet af beskeder i hver beskedring for at få vist en sorteret visning af den pågældende kategoris kø (**Ny** **eller I gang**).

Få mere at vide under [Oversigt over beskeder](alerts-queue.md).

Hver række indeholder en alvorsgradskategori for beskeden og en kort beskrivelse af beskeden. Du kan klikke på en besked for at få vist dens detaljerede visning. Du kan få mere at  [vide under Undersøg oversigten over Microsoft Defender for](investigate-alerts.md) [slutpunktsbeskeder og beskeder](alerts-queue.md).

## <a name="devices-at-risk"></a>Enheder, der er i fare

Dette felt viser dig en liste over enheder med det højeste antal aktive beskeder. Det samlede antal beskeder for hver enhed vises i en cirkel ud for enhedsnavnet og derefter yderligere kategoriseret efter alvorsniveauer i den anden ende af feltet (hold markøren over hver alvorsgradslinje for at se dens etiket).

![Feltet Enheder med risiko viser en liste over enheder med det højeste antal vigtige beskeder og en oversigt over beskedernes alvorlighed.](images/devices-at-risk-tile.png)

Klik på navnet på enheden for at få vist detaljer om enheden. Du kan finde flere oplysninger [under Undersøg enheder på listen Microsoft Defender for slutpunktsenheder](investigate-machines.md).

Du kan også klikke **på listen** Enheder øverst i feltet for at gå direkte til listen **Enheder sorteret** efter antallet af aktive beskeder. Du kan finde flere oplysninger [under Undersøg enheder på listen Microsoft Defender for slutpunktsenheder](investigate-machines.md).

## <a name="devices-with-sensor-issues"></a>Enheder med sensorproblemer

Feltet **Enheder med sensorproblemer** indeholder oplysninger om den enkelte enheds mulighed for at levere sensordata til Microsoft Defender for Endpoint-tjenesten. Den rapporterer, hvor mange enheder der kræver opmærksomhed, og hjælper dig med at identificere problematiske enheder.

![Enheder med flise med sensorproblemer.](images/atp-tile-sensor-health.png)

Der er to statusindikatorer, der angiver oplysninger om antallet af enheder, der ikke rapporterer korrekt til tjenesten:

- **Forkert konfigureret**: Disse enheder rapporterer muligvis delvist sensordata til tjenesten Microsoft Defender til slutpunkt og kan have konfigurationsfejl, der skal rettes.
- **Inaktiv**: Enheder, der er holdt op med at rapportere til Microsoft Defender for Endpoint-tjenesten i mere end syv dage i den seneste måned.

Når du klikker på en af grupperne, bliver du ført til listen over enheder, filtreret efter eget valg. Få mere at vide under [Kontrollér sensortilstand og](check-sensor-status.md) [Undersøg enheder](investigate-machines.md).

## <a name="service-health"></a>Tjeneste sundhed

Feltet **Tjeneste sundhed** giver dig besked, hvis tjenesten er aktiv, eller hvis der er problemer.

![Feltet Tjeneste sundhed viser en overordnet indikator for tjenesten.](images/status-tile.png)

Du kan finde flere oplysninger om tjenestestilstanden [under Kontrollér tjenestestilstanden for Microsoft Defender for Endpoint](service-status.md).

## <a name="daily-devices-reporting"></a>Rapportering af daglige enheder

**Rapporteringsfeltet Daglige enheder** viser et søjlediagram, der repræsenterer antallet af enheder, der rapporterer dagligt inden for de seneste 30 dage. Hold markøren over individuelle søjler på grafen for at få vist det nøjagtige antal enheder, der rapporterer på hver dag.

![Billede af feltet til rapportering af daglige enheder.](images/atp-daily-devices-reporting.png)

## <a name="active-automated-investigations"></a>Aktive automatiserede undersøgelser

Du kan se det samlede antal automatiserede undersøgelser fra de seneste 30 dage i dit netværk fra feltet **Aktive automatiserede** undersøgelser. Undersøgelser grupperes i **Afventende handling**, **Venter på enhed** og **Kører**.

![Inmage af aktive automatiserede undersøgelser.](images/atp-active-investigations-tile.png)

## <a name="automated-investigations-statistics"></a>Automatiserede undersøgelsesstatistik

Dette felt viser statistik, der er relateret til automatiserede undersøgelser i de seneste syv dage. Den viser antallet af afsluttede undersøgelser, antallet af afhjælpede undersøgelser, den gennemsnitlige ventende tid, det tager at igangsætte en undersøgelse, den gennemsnitlige tid, det tager at afhjælpe en besked, antallet af undersøgede beskeder og det antal timer automatisering, der er gemt fra en typisk manuel undersøgelse. 

![Billede af automatiseret undersøgelsesstatistik.](images/atp-automated-investigations-statistics.png)

Du kan klikke på **Automatiserede** **undersøgelser, Afhjælpede** undersøgelser og Vigtige beskeder, der er undersøgt, for at gå  til siden Undersøgelser, filtreret efter den relevante kategori. Dette giver dig mulighed for at få vist en detaljeret beskrivelse af undersøgelser i konteksten.

## <a name="users-at-risk"></a>Brugere, der er i fare

Feltet viser dig en liste over brugerkonti med de mest aktive beskeder og antallet af vigtige beskeder i høj, mellem eller lav. 

![Feltet Brugerkonti med risiko viser en liste over brugerkonti med det højeste antal vigtige beskeder og en opdeling af beskedernes alvorlighed.](images/atp-users-at-risk.png)

Klik på brugerkontoen for at få vist detaljer om brugerkontoen. Få mere at vide under [Undersøg en brugerkonto](investigate-user.md).

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-belowfoldlink)

## <a name="related-topics"></a>Relaterede emner

- [Forstå Microsoft Defender for Endpoint-portalen](use.md)
- [Portaloversigt](portal-overview.md)
- [Se dashboardet til & mod sikkerhedsrisiko](tvm-dashboard-insights.md)
- [Få vist dashboardet for Trusselsanalyse, og tag anbefalede afhjælpningshandlinger](threat-analytics.md)
