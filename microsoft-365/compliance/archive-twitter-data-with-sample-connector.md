---
title: Konfigurer en forbindelse til at arkivere Twitter-data
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
description: Få mere at vide om, hvordan administratorer kan konfigurere og bruge en indbygget forbindelse til at importere Twitter-data Microsoft 365.
ms.openlocfilehash: 959cdd49d229334f3129eb21505c4489d23ded4f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587281"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Konfigurer en Microsoft-forbindelse til at arkivere Twitter-data (forhåndsvisning)

Brug en forbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere data fra Twitter til Microsoft 365. Når du har konfigureret forbindelsen, opretter den forbindelse til din organisations Twitter-konto (efter planlagt), konverterer indholdet af et element til et mailformat og importerer derefter disse elementer til en postkasse i Microsoft 365.

Når Twitter-dataene er importeret, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning, In-Place Arkivering, Overvågning og Microsoft 365 opbevaringspolitikker for Twitter-dataene. Når f.eks. en postkasse er placeret i retslig tilbageholdelse eller tildelt en opbevaringspolitik, bevares Twitter-dataene. Du kan søge efter tredjepartsdata ved hjælp af indholdssøgning eller tilknytte postkassen, hvor Twitter-dataene er gemt, sammen med en assistent i Advanced eDiscovery sag. Hvis du bruger en forbindelse til at importere og arkivere Twitter-data Microsoft 365 din organisation med at overholde offentlige og lovmæssige politikker.

Når Twitter-data er importeret, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning, In-Place Arkivering, Overvågning, Kommunikationsoverholdelse og Microsoft 365 opbevaringspolitikker for de data, der er gemt i postkassen. Du kan f.eks. søge efter Twitter-data ved hjælp af indholdssøgning eller knytte postkassen, hvor dataene er gemt, til en assistent i Advanced eDiscovery sag. Hvis du bruger en forbindelse til at importere og arkivere Twitter-data Microsoft 365 din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

Fuldfør følgende forudsætninger, før du kan konfigurere en forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra din organisations Twitter-konto.

- Du skal bruge en Twitter-konto for din organisation; skal du logge på denne konto, når du konfigurerer forbindelsen.

- Din organisation skal have et gyldigt Azure-abonnement. Hvis du ikke har et eksisterende Azure-abonnement, kan du tilmelde dig en af disse muligheder:

    - [Tilmeld dig et gratis års Azure-abonnement](https://azure.microsoft.com/free) 

    - [Tilmeld dig et Pay-As-You-Go Azure-abonnement](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > Det [gratis Azure Active Directory abonnement](use-your-free-azure-ad-subscription-in-office-365.md), der er inkluderet i dit Microsoft 365-abonnement, understøtter ikke forbindelserne i Microsoft 365 Overholdelsescenter.

- Twitter-forbindelsen kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 Twitter-elementer på en dag, importeres ingen af disse elementer til Microsoft 365.

- Den bruger, der konfigurerer Twitter-forbindelsen i Microsoft 365 Overholdelsescenter (i trin 5), skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at registrere en ny app i Azure Active Directory (AAD). Denne app svarer til den webapp-ressource, du implementerer i trin 2 til Twitter-forbindelsen.

Du kan finde en trinvis vejledning under [Oprette en app i Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) skal du gemme følgende oplysninger i en tekstfil. Disse værdier skal bruges i senere trin i installationsprocessen.

- AAD-program-id

- AAD programhemmelighed

- Lejer-id

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>Trin 2: Installer forbindelseswebtjeneste fra GitHub lager til din Azure-konto

Næste trin er at anvende kildekoden til Twitter-forbindelsesappen, der skal bruge Twitter API til at oprette forbindelse til din Twitter-konto og udtrække data, så du kan importere dem til Microsoft 365. Den Twitter-forbindelse, du installerer for din organisation, uploader elementerne fra din organisations Twitter-konto til den placering Azure Storage, der er oprettet i dette trin. Når du har oprettet en Twitter-forbindelse i Microsoft 365 Overholdelsescenter (i trin 5), kopierer tjenesten Microsoft 365-import Twitter-data fra Azure Storage-placeringen til en postkasse i Microsoft 365. Som beskrevet tidligere i [afsnittet Før du konfigurerer](#before-you-set-up-a-connector) en forbindelse skal du have et gyldigt Azure-abonnement for at kunne oprette Azure Storage konto.

Sådan installeres kildekoden til Twitter-forbindelsesappen:

1. Gå til [dette GitHub websted](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. Klik **på Installér til Azure**.

Du kan finde en trinvis vejledning under [Installér forbindelsens webtjeneste fra GitHub din Azure-konto](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Mens du følger den trinvise vejledning for at fuldføre dette trin, skal du angive følgende oplysninger

- APISecretKey: Du opretter denne hemmelighed under fuldførelsen af dette trin. Den bruges i trin 5.

- tenantId: Lejer-id'et for din Microsoft 365 organisation, som du kopierede efter oprettelse af Twitter-appen Azure Active Directory i trin 1.

Når du har fuldført dette trin, skal du sørge for at kopiere apptjenestens URL-adresse (f.eks. `https://twitterconnector.azurewebsites.net`). Du skal bruge denne URL-adresse for at fuldføre trin 3, trin 4 og trin 5).

## <a name="step-3-create-developer-app-on-twitter"></a>Trin 3: Opret udviklerapp på Twitter

Næste trin er at oprette og konfigurere en udviklerapp på Twitter. Den brugerdefinerede forbindelse, du opretter i trin 7, bruger Twitter-appen til at interagere med Twitter API'en for at hente data fra din organisations Twitter-konto.

Du kan finde en trinvis vejledning under [Opret Twitter-appen](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) gemmer du følgende oplysninger i en tekstfil. Disse værdier skal bruges til at konfigurere Twitter-forbindelsesappen i trin 4.

- Twitter API-nøgle

- Twitter API Secret Key

- Twitter-adgangstoken

- Twitter Access Token Secret

## <a name="step-4-configure-the-twitter-connector-app"></a>Trin 4: Konfigurer Twitter-forbindelsesappen

Næste trin er at føje konfigurationsindstillinger til Twitter-forbindelsesappen, som du installerede i trin 2. Det gør du ved at gå til startsiden i forbindelsesappen og konfigurere den.

Du kan finde en trinvis vejledning under [Konfigurere forbindelseswebappen](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) skal du angive følgende oplysninger (som du har kopieret til en tekstfil, når du har udført de forrige trin):

- Twitter API-nøgle (hentet i trin 3)

- Twitter API Secret Key (hentet i trin 3)

- Twitter Access-token (hentet i trin 3)

- Twitter Access Token Secret (hentet i trin 3)

- Azure Active Directory program-id (det AAD program-id, der blev hentet i trin 1)

- Azure Active Directory programhemmelighed (den AAD programhemmelighed, der blev indhentet i trin 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Trin 5: Konfigurer en Twitter-forbindelse i Microsoft 365 Overholdelsescenter

Det sidste trin er at konfigurere Twitter-forbindelsen i Microsoft 365 Overholdelsescenter, som vil importere data fra din organisations Twitter-konto til en bestemt postkasse i Microsoft 365. Når du har udført dette trin, begynder tjenesten Microsoft 365 Importér at importere data fra din organisations Twitter-konto for at Microsoft 365.

Du kan finde en trinvis vejledning under [Konfigurer en Twitter-forbindelse i Microsoft 365 Overholdelsescenter](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center). 

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) skal du angive følgende oplysninger (som du har kopieret til en tekstfil, når du har fuldført trinnene).

- URL-adresse til Azure-apptjeneste (hentet i trin 2, f.eks. `https://twitterconnector.azurewebsites.net`)

- APISecretKey (som du oprettede i trin 2)