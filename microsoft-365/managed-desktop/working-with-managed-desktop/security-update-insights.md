---
title: Windows indsigt i sikkerhedsopdateringer
description: ''
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: b3b1f43217b3be285f20925065bf9710a38f9606
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2021
ms.locfileid: "63590207"
---
# <a name="windows-security-update-insights"></a>Windows indsigt i sikkerhedsopdateringer
Denne visning giver et overblik over status for sikkerhedsopdateringer til dine Microsoft-administrerede computerenheder. 

For at få vist brugsdata skal du <strong>Windows fanen Sikkerhedsopdateringer</strong>.

![Windows rude med sikkerhedsopdateringer: søjlediagrammer over enhedsstatus og opdateringsversion i venstre kolonne, opdatering af installationsstatus over tid i midterkolonne og procentdel af aktive enheder efter installationsgruppe samt antallet af dage, det tager at nå 95 % installationsmålet i højre kolonne.](../../media/update-insights.jpg)

## <a name="device-status"></a>Enhedsstatus

For at enheder kan opdateres med Windows Update, skal de have forbindelse til internettet og ikke være i dvale i mindst seks timer, hvoraf to skal være fortløbende. Selvom det er muligt, at en enhed, der ikke opfylder disse krav, opdateres, har enheder, der opfylder dem, den højeste sandsynlighed for at blive opdateret. 

Vi kategoriserer enhedsaktivitet i forbindelse med Windows Opdater med disse udtryk:

- <strong>Aktiv:</strong> Enheder, der har opfyldt minimumskriterierne for aktivitet (seks timer, to fortløbende) for den seneste udgivelse af sikkerhedsopdateringer, og som har tjekket ind med Microsoft Intune mindst hver fem dage
- <strong>Synkroniseret:</strong> Enheder, der har tjekket ind med Intune inden for de seneste 28 dage
- <strong>Ikke synkroniseret:</strong> Enheder, der <i>ikke er</i> tjekket ind med Intune inden for de seneste 28 dage




## <a name="update-version-status"></a>Opdater versionsstatus

Microsoft udgiver sikkerhedsopdateringer hver anden tirsdag i måneden. Hver version tilføjer vigtige opdateringer til kendte sikkerhedsrisici. Microsoft Managed Desktop sikrer, at 95 % af dens administrerede enheder opdateres med den nyeste tilgængelige sikkerhedsopdatering hver måned. Sikkerhedsopdateringer frigives nogle gange andre gange for hurtigt at håndtere nye trusler. Microsoft Managed Desktop installerer disse opdateringer på lignende måde.

Vi kategoriserer status for sikkerhedsopdateringsversioner med disse udtryk:

- <strong>Aktuel:</strong> Enheder, der kører den opdatering, der er udgivet i den aktuelle måned
- <strong>Forrige:</strong> Enheder, der kører den opdatering, der blev udgivet i den forrige måned
- <strong>Ældre:</strong> Enheder, der kører en sikkerhedsopdatering, der er udgivet før den forrige måned

Du bør få vist få enheder i <strong></strong> kategorien Ældre – en stor eller voksende befolkning angiver sandsynligvis et omfattende problem, som du bør rapportere til Microsoft Managed Desktop, så vi kan undersøge det.


## <a name="deployment-progress"></a>Installation status

I starten af hver sikkerhedsopdateringsudgivelsescyklus tager Microsoft Managed Desktop et øjebliksbillede af enhedens befolkning og angiver installationsmålet for 95 % af den pågældende population. <strong>Statusområdet for Installation</strong> viser en historisk tendens, opdateres dagligt og registrerer, hvor tæt opdateringsinstallationen opfylder dette mål for hver version. Dette diagram viser kun enheder med aktiv status.

Du kan få vist disse data for tidligere opdateringscyklusser ved hjælp af rullemenuen øverst til højre. Den periode, du vælger i denne menu, gælder for alle oplysningerne på hele siden.

Området <strong>Opdaterede aktive enheder efter installationsgruppe</strong> giver en anden visning ved at vise status for opdateringsinstallationen for hver af Microsoft Managed Desktop-installationsgrupperne.

<strong>Destinationsområdet Dage, det tog</strong> at nå ud til, viser, hvor lang tid det tog for 95 % af det samlede antal enheder at blive opdateret med den aktuelle sikkerhedsopdatering. Mens udrulningen er i gang, opdateres <strong>dette område stadig</strong> , indtil 95 % af destinationen er nået for den valgte opdatering.

## <a name="device-details-area"></a>Området Detaljer om enhed

Bunden af dashboardet er en tabel, der viser detaljerede oplysninger om dine enheder, herunder [Enhedsstatus](#device-status) og [Status for opdatering af version](#update-version-status). Du kan søge i denne liste eller filtrere den efter enhver angivet værdi.


![Tabel med enhedsoplysninger, der viser kolonner for enhedsnavn, tildelt bruger, enhedsstatus, opdateringsversion, operativsystemversion og den dato, hvor enheden sidst blev synkroniseret.](../../media/security-update-insights-device-table-sterile.png)
