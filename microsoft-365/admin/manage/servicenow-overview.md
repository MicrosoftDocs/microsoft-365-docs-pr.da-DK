---
title: Microsoft 365 supportintegration med ServiceNow-konfigurationsoversigt
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Omfangsstyret certificeret programinstallation og konfigurationsvejledning for ServiceNow.
ms.openlocfilehash: dc69f6210eda4ba04dfd0aecf9795bfcba2efe22
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594050"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Microsoft 365 supportintegration med ServiceNow-konfigurationsoversigt

Følgende indhold gælder for appen Microsoft 365 med en minimumversion **af 1.0.7**.

**Microsoft 365 med support kan** du integrere Microsoft 365 hjælp, support og tjenestestilstand med dine ServiceNow-forekomster. Du kan undersøge Microsofts kendte og rapporterede problemer, løse hændelser, udføre opgaver ved hjælp af anbefalede Microsoft-løsninger og, hvis det er nødvendigt, eskalere til Microsofts human-assisterede support.

Hvis du **Microsoft 365 appen til supportintegration** fra ServiceNow Store, skal du [gå til ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Vigtige funktioner

Dette er de vigtigste funktioner, du får med appen Microsoft 365 supportintegration i din ServiceNow-forekomst:

- Tjenestetilstandshændelser: Oplysninger om kendte Microsoft-tjenestetilstandshændelser, herunder brugerpåvirkning, omfang, aktuel status og næste forventede opdatering. Med maskinlæring passer ServiceNow-hændelser til Microsoft-tjenestestilstandshændelser baseret på feltet Kort beskrivelse.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="Beskrivelsesfeltet Tjenestestilstandshændelser.":::

- Anbefalede løsninger: Beskrivelser af opgaver og hændelser bruges til at anbefale præcise målrettede løsninger og relevante artikler fra Microsoft, der drives af maskinlæring. Du kan også bruge Søg til at finde andre løsninger, hvis det er nødvendigt.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="Beskrivelsesfelt for anbefalede løsninger.":::

- Microsoft-serviceanmodning: Eskaler problemer til Microsoft-supportmedarbejdere, og modtag statusopdateringer til din sag.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="Serviceanmodningsformular.":::

## <a name="prerequisites"></a>Forudsætninger

### <a name="permissions-requirements"></a>Tilladelseskrav

Hvis du vil fortsætte med denne vejledning, skal du sørge for, at følgende tilladelser er tilgængelige og konfigureret for dine miljøer under hele processen:

- Azure Active Directory (AAD), der kan oprette Azure AD-programmer

- ServiceNow-administrator

- Microsoft 365 lejeradministrator

### <a name="configuration-highlights"></a>De vigtigste punkter i konfigurationen

Sådan konfigurerer **du Microsoft 365 supportintegration**:

- Registrer programmer Microsoft Azure Active Directory (AAD) til godkendelse af både udgående og indgående API-opkald.

- Opret ServiceNow-enheder med Microsoft Azure AD program til både udgående og indgående dataflow.

- Integrer ServiceNow-forekomst med Microsoft-support via Microsoft 365-administrationsportalen.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="ServiceNow-integrationsdiagram.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>Programafhængigheder i dine ServiceNow-miljøer

Der kræves tilladelser:

- oauthentity\_

- oauthentityprofile\_\_

Når appen Microsoft 365 for supportintegration er blevet installeret, oprettes der to programadgange på tværs af områder. Hvis de ikke er oprettet, skal du oprette dem manuelt.

## <a name="setup-the-integration"></a>Konfiguration af integration

Når du har downloadet appen, skal du gå til Microsoft 365 konfigurationsguiden i dit SNOW-miljø for at fuldføre konfigurationen.
:::image type="content" source="../../media/154124985-76e13e7d-b32e-4741-830b-bbb110d3ecbf.png" alt-text="Guiden Konfiguration af sne":::

Du kan få mere at vide om fremgangsmåden ved at besøge følgende sider:
- Hvis dit ServiceNow-miljø tillader basisgodkendelse (adgang med ServiceNow-brugerlegitimationsoplysninger) for indgående webtjenesteopkald, skal du følge vejledningen i Konfigurere [Microsoft 365-supportintegration med ServiceNow Basic Authentication](servicenow-basic-authentication.md).
- Hvis dit ServiceNow-miljø IKKE tillader basisgodkendelse (adgang med ServiceNow-brugerlegitimationsoplysninger) for indgående webtjenesteopkald, skal du følge instruktionerne i Konfigurere [Microsoft 365-supportintegration med Azure AD Auth-token](servicenow-aad-oauth-token.md).
  - Denne konfiguration kræver en SSO-lejer, for at den AAD godkendelsestoken fungerer korrekt.

For at forstå hver enkelt funktion skal [du Microsoft 365 integration af support](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

> [!NOTE]
> Denne app understøttes ikke i regulerede eller begrænsede miljøer.
