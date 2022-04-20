---
title: Konfigurer en connector til arkivering af Facebook-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan du konfigurerer & bruger en connector på Microsoft Purview-overholdelsesportalen til at importere & arkivere data fra Facebook Business-sider for at Microsoft 365.
ms.openlocfilehash: 6db2bd474cd2920b4b067563377bbe85084aeeaf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947225"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Konfigurer en connector til arkivering af Facebook-data (prøveversion)

Brug en connector på Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra Facebook Business-sider for at Microsoft 365. Når du har konfigureret connectoren, opretter den forbindelse til Facebook Business-siden (efter en tidsplan), konverterer indholdet af Facebook-elementer til et mailformat og importerer derefter disse elementer til en postkasse i Microsoft 365.

Når Facebook-dataene er importeret, kan du anvende Microsoft Purview-funktioner som Litigation Hold, Content Search, In-Place Archiving, Auditing, Communication compliance og Microsoft 365 opbevaringspolitikker på Facebook-dataene. Når en postkasse f.eks. er sat i venteposition for procesførelse eller er tildelt en opbevaringspolitik, bevares Facebook-dataene. Du kan søge i tredjepartsdata ved hjælp af indholdssøgning eller knytte den postkasse, hvor Facebook-dataene er gemt, til en tilsynsførende i en Microsoft Purview eDiscovery-sag (Premium). Brug af en connector til at importere og arkivere Facebook-data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Forudsætninger for konfiguration af en connector til Facebook Business-sider

Fuldfør følgende forudsætninger, før du kan konfigurere en connector på overholdelsesportalen for at importere og arkivere data fra din organisations Facebook-virksomhedssider. 

- Du skal bruge en Facebook-konto til din organisations virksomhedssider (du skal logge på denne konto, når du konfigurerer connectoren). I øjeblikket kan du kun arkivere data fra Facebook Business-sider. du kan ikke arkivere data fra individuelle Facebook-profiler.

- Din organisation skal have et gyldigt Azure-abonnement. Hvis du ikke har et eksisterende Azure-abonnement, kan du tilmelde dig en af disse muligheder:

    - [Tilmeld dig et gratis Azure-abonnement på ét år](https://azure.microsoft.com/free)

    - [Tilmeld dig et Azure-abonnement, der betales efter forbrug](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > Det [gratis Azure Active Directory abonnement](use-your-free-azure-ad-subscription-in-office-365.md), der er inkluderet i dit Microsoft 365-abonnement, understøtter ikke connectorerne på overholdelsesportalen.

- Connectoren til Facebook Business-sider kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 Facebook Business-elementer på én dag, importeres ingen af disse elementer til Microsoft 365.

- Den bruger, der konfigurerer den brugerdefinerede connector på overholdelsesportalen (i trin 5), skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at registrere en ny app i Azure Active Directory (AAD). Denne app svarer til den webappressource, du implementerer i trin 4 og trin 5 for Facebook-connectoren.

Du kan finde en trinvis vejledning [under Opret en app i Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Når du har fuldført dette trin (ved hjælp af de forrige trinvise instruktioner), skal du gemme følgende oplysninger i en tekstfil. Disse værdier bruges i senere trin i installationsprocessen.

- AAD program-id

- AAD programhemmelighed

- Lejer-id

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Trin 2: Udrul connectorwebtjenesten fra GitHub til din Azure-konto

Det næste trin er at installere kildekoden for connectorappen Facebook Business Pages, der bruger Facebook-API'en til at oprette forbindelse til din Facebook-konto og udtrække data, så du kan importere dem for at Microsoft 365. Den Facebook-connector, du installerer for din organisation, uploader elementerne fra dine Facebook-virksomhedssider til den Azure Storage placering, der oprettes i dette trin. Når du har oprettet en connector til Facebook-virksomhedssider i overholdelsesportalen (i trin 5), kopierer importtjenesten dataene på Facebook-virksomhedssiderne fra den Azure Storage placering til en postkasse i din Microsoft 365 organisation. Som tidligere forklaret i afsnittet [Forudsætninger](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) skal du have et gyldigt Azure-abonnement for at oprette en Azure Storage konto.

Du kan finde en trinvis vejledning under [Installér connectorwebtjenesten fra GitHub på din Azure-konto](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

I den trinvise vejledning til fuldførelse af dette trin skal du angive følgende oplysninger:

- APISecretKey: Du opretter denne hemmelighed under fuldførelsen af dette trin. Den bruges i trin 5.

- TenantId: Lejer-id'et for din Microsoft 365 organisation, som du kopierede, efter at du oprettede Facebook-connectorappen i Azure Active Directory i trin 1.

Når du har fuldført dette trin, skal du sørge for at kopiere URL-adressen til Azure-apptjenesten (f.eks. https://fbconnector.azurewebsites.net). Du skal bruge denne URL-adresse for at fuldføre trin 3, trin 4 og trin 5.

## <a name="step-3-register-the-web-app-on-facebook"></a>Trin 3: Registrer webappen på Facebook

Det næste trin er at oprette og konfigurere en ny app på Facebook. Connectoren Facebook-virksomhedssider, som du opretter i trin 5, bruger Facebook-webappen til at interagere med Facebook-API'en for at hente data fra din organisations Facebook-virksomhedssider.

Du kan finde en trinvis vejledning under [Registrer Facebook-appen](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du gemme følgende oplysninger i en tekstfil. Disse værdier bruges til at konfigurere Facebook-connectorappen i trin 4.

- Facebook-program-id

- Facebook-programhemmelighed

- Token til bekræftelse af facebook-webhooks

## <a name="step-4-configure-the-facebook-connector-app"></a>Trin 4: Konfigurer Facebook-connectorappen

Det næste trin er at føje konfigurationsindstillinger til den Facebook-connectorapp, du uploadede, da du oprettede Azure-webappressourcen i trin 1. Det gør du ved at gå til startsiden for din connectorapp og konfigurere den.

Du kan finde en trinvis vejledning under [Konfigurer Appen Facebook-connector](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du angive følgende oplysninger (som du har kopieret til en tekstfil, når du har fuldført de forrige trin):

- Facebook-program-id (hentet i trin 3)

- Facebook-programhemmelighed (hentet i trin 3)

- Facebooks webhooks bekræfter token (hentet i Trin 3)

- Azure Active Directory program-id (det AAD program-id, der blev hentet i trin 1)

- Azure Active Directory programhemmelighed (den AAD programhemmelighed, der blev hentet i trin 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>Trin 5: Konfigurer en connector til Facebook-virksomhedssider på overholdelsesportalen

Det sidste trin er at konfigurere connectoren i overholdelsesportalen, der importerer data fra dine Facebook Business-sider til en angivet postkasse i Microsoft 365. Når du har fuldført dette trin, begynder tjenesten Microsoft 365 import at importere data fra dine Facebook-virksomhedssider til Microsoft 365.

Du kan finde en trinvis vejledning under [Trin 5: Konfigurer en Facebook-connector på overholdelsesportalen](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

Når du har fuldført dette trin (ved at følge den trinvise vejledning), skal du angive følgende oplysninger (som du har kopieret til en tekstfil, når du har fuldført trinnene).

- AAD program-id (hentet i trin 1)

- URL-adresse til Azure-apptjeneste (hentet i trin 1, f.eks. https://fbconnector.azurewebsites.net)

- APISecretKey (som du oprettede i trin 2)
