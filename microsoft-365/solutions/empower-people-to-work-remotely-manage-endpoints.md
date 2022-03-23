---
title: Trin 4. Installér slutpunktsstyring til dine enheder, pc'er og andre slutpunkter
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Brug Microsoft Endpoint Manager til at administrere dine enheder, pc'er og andre slutpunkter.
ms.openlocfilehash: d18a001021486c617aaf0fa04972e9464a5c2016
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588639"
---
# <a name="step-4-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>Trin 4. Installér slutpunktsstyring til dine enheder, pc'er og andre slutpunkter

Med hybridmedarbejdere skal du understøtte et stigende antal personlige enheder. Slutpunktsstyring er en politikbaseret tilgang til sikkerhed, der kræver, at enheder overholder bestemte kriterier, før de får tildelt adgang til ressourcer. Microsoft Endpoint Manager leverer moderne administrationsfunktioner, så du kan holde dine data sikre i skyen og i det lokale miljø. 

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) indeholder tjenester og værktøjer til administration af mobilenheder, stationære computere, virtuelle computere, integrerede enheder og servere ved at kombinere følgende tjenester, som du måske allerede kender og bruger.

:::image type="content" source="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png" alt-text="Komponenterne i slutpunktsstyring for Microsoft 365" lightbox="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png":::

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune er en skybaseret tjeneste, der fokuserer på administration af mobilenheder (MDM) og administration af mobilapps (MAM), som følger med Microsoft 365. 

- **MDM:** For enheder, der ejes af organisationen, kan du have fuld kontrol, herunder indstillinger, funktioner og sikkerhed. Enheder er "tilmeldt" i Intune, hvor de modtager Intune-politikker med regler og indstillinger. Du kan f.eks. angive krav til adgangskode og pinkode, oprette en VPN-forbindelse, konfigurere trusselsbeskyttelse og meget mere.

- **MAM:** Eksterne medarbejdere ønsker muligvis ikke, at du skal have fuld kontrol over deres personlige enheder, også kaldet BYOD-enheder (Bring-your-Own Device). Du kan give dine hybridmedarbejdere valgmuligheder og stadig beskytte din organisation. Hybridmedarbejdere kan f.eks. tilmelde deres enheder, hvis de vil have fuld adgang til organisationens ressourcer. Eller, hvis disse brugere kun vil have adgang til mail eller Microsoft Teams, skal du bruge politikker for appbeskyttelse, der kræver multifaktorgodkendelse for at bruge disse apps.

Du kan finde flere oplysninger i [Administrer enheder med Intune-foundationsløsningen](manage-devices-with-intune-overview.md) .

## <a name="configuration-manager"></a>Konfigurationsstyring

Konfigurationsstyring er en løsning i det lokale miljø til administration af computere, servere og bærbare computere, som er på dit netværk eller internetbaserede. Brug Konfigurationsstyring til at installere apps, softwareopdateringer og operativsystemer. Du kan også overvåge overholdelse, forespørgsler og handle på kunder i realtid og meget mere. Du kan aktivere skyen til integration med Intune, Azure AD, Microsoft Defender til slutpunkt og andre skytjenester. 

Du kan finde flere oplysninger i [denne oversigt over Konfigurationsstyring](/mem/configmgr/core/understand/introduction).

## <a name="co-management"></a>Medadministration

Med samtidig administration kombineres din eksisterende investering i Konfigurationsstyring det lokale miljø med skyen ved hjælp af Intune og Microsoft 365 skytjenester. Du kan vælge, Konfigurationsstyring eller Intune er administrationscenteret for forskellige arbejdsbelastninger. 

Samtidig administration bruger Intune-baserede skyfunktioner, herunder Betinget adgang og gennemtvingelse af enhedsoverholdelse. Du beholder nogle opgaver lokalt, mens du kører andre opgaver i skyen.

Du kan finde flere oplysninger [i denne oversigt over samtidig administration](/mem/configmgr/comanage/overview).

## <a name="endpoint-analytics"></a>Endpoint Analytics

Slutpunktsanalyse forbedrer brugerproduktiviteten og reducerer omkostningerne til it-support ved at give indsigt i brugeroplevelsen. Indsigten gør det muligt for it-brugerne at optimere slutbrugeroplevelsen med proaktiv support og registrere regressioner i brugeroplevelsen ved at vurdere brugerpåvirkningen af konfigurationsændringer.

Få mere at vide under [denne oversigt over Endpoint Analytics](/mem/analytics/overview)

## <a name="windows-autopilot"></a>Windows Autopilot

Windows Autopilot er en selvbetjeningsplatform til selvbetjening Windows nul-touch. Den indeholder en samling af teknologier, du bruger til at konfigurere og forudkonfigurer nye enheder, så de bliver klar til produktiv brug. Du kan også bruge Windows AutoPilot til at nulstille, genkøbe og gendanne enheder. 

Windows Autopilot gør det muligt for en it-afdeling at forudkonfigurer enheder med lidt eller ingen infrastruktur at administrere, med en proces, der er nem og enkel. 

- Fra brugerens perspektiv tager det kun et par enkle handlinger at gøre enheden klar til brug. 
- Set fra it-professionelles perspektiv er den eneste interaktion, der kræves fra slutbrugeren, at oprette forbindelse til et netværk og bekræfte deres legitimationsoplysninger.

Få mere at vide under denne [oversigt over Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot).

## <a name="admin-technical-resources-for-endpoint-management"></a>Tekniske ressourcer for administration af slutpunkter

- [Roadmap til enhedshåndtering for Microsoft 365](../enterprise/device-management-roadmap-microsoft-365.md)
- [Sådan tilmelder du forskellige typer enheder til administration af mobilenheder](/mem/intune/enrollment/device-enrollment)
- [Sådan lærer du dine slutbrugere om Microsoft Intune](/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-4"></a>Resultater af trin 4

Du bruger pakken med Endpoint Manager funktioner og funktioner til administration af mobilenheder, stationære computere, virtuelle computere, integrerede enheder og servere.

## <a name="next-step"></a>Næste trin

[![Trin 5: Implementer produktivitetsapps og tjenester for fjernmedarbejdere.](../media/empower-people-to-work-remotely/remote-workers-step-grid-5.png)](empower-people-to-work-remotely-teams-productivity-apps.md)

Fortsæt med [trin 5 for](empower-people-to-work-remotely-teams-productivity-apps.md) at få dine hybridmedarbejdere ved hjælp Microsoft 365 produktivitetsapps som f.eks. Microsoft Teams.