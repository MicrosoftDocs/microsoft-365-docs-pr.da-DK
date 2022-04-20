---
title: Konfigurer en connector til arkivering af Twitter-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan administratorer kan konfigurere og bruge en oprindelig connector til at importere Twitter-data til Microsoft 365.
ms.openlocfilehash: d025de04060184a6bd39fcef5ab68acdde65bc01
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940549"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Konfigurer en Microsoft-connector til arkivering af Twitter-data (prøveversion)

Brug en connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Twitter til Microsoft 365. Når du har konfigureret connectoren, opretter den forbindelse til din organisations Twitter-konto (efter en tidsplan), konverterer indholdet af et element til et mailformat og importerer derefter disse elementer til en postkasse i Microsoft 365.

Når Twitter-dataene er importeret, kan du anvende Microsoft Purview-funktioner som Litigation Hold, Content Search, In-Place Archiving, Auditing og Microsoft 365 opbevaringspolitikker på Twitter-dataene. Når en postkasse f.eks. er sat i venteposition for procesførelse eller er tildelt en opbevaringspolitik, bevares Twitter-dataene. Du kan søge i tredjepartsdata ved hjælp af indholdssøgning eller knytte postkassen, hvor Twitter-dataene er gemt, til en tilsynsførende i en Microsoft Purview eDiscovery-sag (Premium). Brug af en connector til at importere og arkivere Twitter-data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

Når Twitter-data er importeret, kan du anvende Microsoft Purview-funktioner, f.eks. litigation venteposition, indholdssøgning, In-Place arkivering, overvågning, kommunikation og Microsoft 365 opbevaringspolitikker, på de data, der er gemt i postkassen. Du kan f.eks. søge efter Twitter-data ved hjælp af indholdssøgning eller knytte den postkasse, hvor dataene er gemt, til en tilsynsførende i en eDiscovery-sag (Premium). Brug af en connector til at importere og arkivere Twitter-data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

Fuldfør følgende forudsætninger, før du kan konfigurere en connector på overholdelsesportalen for at importere og arkivere data fra din organisations Twitter-konto.

- Du skal bruge en Twitter-konto til din organisation. du skal logge på denne konto, når du konfigurerer connectoren.

- Din organisation skal have et gyldigt Azure-abonnement. Hvis du ikke har et eksisterende Azure-abonnement, kan du tilmelde dig en af disse muligheder:

    - [Tilmeld dig et gratis Azure-abonnement på ét år](https://azure.microsoft.com/free) 

    - [Tilmeld dig et Azure-abonnement, der betales efter forbrug](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > Det [gratis Azure Active Directory abonnement](use-your-free-azure-ad-subscription-in-office-365.md), der er inkluderet i dit Microsoft 365-abonnement, understøtter ikke connectorerne på overholdelsesportalen.

- Twitter-connectoren kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 Twitter-elementer på én dag, importeres ingen af disse elementer til Microsoft 365.

- Den bruger, der konfigurerer Twitter-connectoren på overholdelsesportalen (i trin 5), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at registrere en ny app i Azure Active Directory (AAD). Denne app svarer til den webappressource, du implementerer i trin 2 for Twitter-connectoren.

Du kan finde en trinvis vejledning [under Opret en app i Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du gemme følgende oplysninger i en tekstfil. Disse værdier bruges i senere trin i installationsprocessen.

- AAD program-id

- AAD programhemmelighed

- Lejer-id

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Trin 2: Udrul connectorwebtjeneste fra GitHub lager på din Azure-konto

Det næste trin er at installere kildekoden til Twitter-connectorappen, der bruger Twitter-API'en til at oprette forbindelse til din Twitter-konto og udtrække data, så du kan importere dem til Microsoft 365. Den Twitter-connector, du installerer for din organisation, uploader elementerne fra din organisations Twitter-konto til den Azure Storage placering, der oprettes i dette trin. Når du har oprettet en Twitter-connector på overholdelsesportalen (i trin 5), kopierer tjenesten Microsoft 365 import Twitter-dataene fra den Azure Storage placering til en postkasse i Microsoft 365. Som tidligere forklaret i afsnittet [Før du konfigurerer en connector](#before-you-set-up-a-connector), skal du have et gyldigt Azure-abonnement for at oprette en Azure Storage konto.

Sådan installerer du kildekoden til Twitter-connectorappen:

1. Gå til [dette GitHub websted](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Klik på **Udrul på Azure**.

Du kan finde en trinvis vejledning under [Installér connectorwebtjenesten fra GitHub på din Azure-konto](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Mens du følger den trinvise vejledning for at fuldføre dette trin, skal du angive følgende oplysninger

- APISecretKey: Du opretter denne hemmelighed under fuldførelsen af dette trin. Den bruges i trin 5.

- tenantId: Lejer-id'et for din Microsoft 365 organisation, som du kopierede, da du oprettede Twitter-appen i Azure Active Directory i trin 1.

Når du har fuldført dette trin, skal du sørge for at kopiere URL-adressen til apptjenesten (f.eks. `https://twitterconnector.azurewebsites.net`). Du skal bruge denne URL-adresse for at fuldføre trin 3, trin 4 og trin 5.

## <a name="step-3-create-developer-app-on-twitter"></a>Trin 3: Opret udviklerapp på Twitter

Det næste trin er at oprette og konfigurere en udviklerapp på Twitter. Den brugerdefinerede connector, du opretter i trin 7, bruger Twitter-appen til at interagere med Twitter-API'en for at hente data fra din organisations Twitter-konto.

Du kan finde en trinvis vejledning under [Opret Twitter-appen](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du gemme følgende oplysninger i en tekstfil. Disse værdier bruges til at konfigurere Twitter-connectorappen i trin 4.

- Api-nøgle til Twitter

- Hemmelig nøgle til Twitter-API

- Adgangstoken til Twitter

- Twitter-adgangstokenhemmelighed

## <a name="step-4-configure-the-twitter-connector-app"></a>Trin 4: Konfigurer Twitter-connectorappen

Det næste trin er at føje konfigurationsindstillinger til den Twitter-connectorapp, du installerede i trin 2. Det gør du ved at gå til startsiden for din connectorapp og konfigurere den.

Du kan finde en trinvis vejledning under [Konfigurer connectorwebappen](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du angive følgende oplysninger (som du har kopieret til en tekstfil, når du har fuldført de forrige trin):

- Api-nøgle til Twitter (hentet i trin 3)

- Hemmelig Twitter-API-nøgle (hentet i trin 3)

- Adgangstoken til Twitter (hentet i trin 3)

- Twitter Access Token Secret (hentet i Trin 3)

- Azure Active Directory program-id (det AAD program-id, der blev hentet i trin 1)

- Azure Active Directory programhemmelighed (den AAD programhemmelighed, der blev hentet i trin 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>Trin 5: Konfigurer en Twitter-connector på overholdelsesportalen

Det sidste trin er at konfigurere Twitter-connectoren på overholdelsesportalen, der importerer data fra din organisations Twitter-konto til en angivet postkasse i Microsoft 365. Når du har fuldført dette trin, begynder tjenesten Microsoft 365 import at importere data fra din organisations Twitter-konto til Microsoft 365.

Du kan finde en trinvis vejledning under [Konfigurer en Twitter-connector på Microsoft Purview-overholdelsesportalen](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-compliance-portal).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du angive følgende oplysninger (som du har kopieret til en tekstfil, når du har fuldført trinnene).

- URL-adresse til Azure-apptjeneste (hentet i trin 2, `https://twitterconnector.azurewebsites.net`f.eks. )

- APISecretKey (som du oprettede i trin 2)