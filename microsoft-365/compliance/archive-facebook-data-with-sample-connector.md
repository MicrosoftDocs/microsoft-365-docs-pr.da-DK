---
title: Konfigurer en forbindelse til at arkivere Facebook-data
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
description: Se, hvordan du konfigurerer & bruger en forbindelse i Microsoft 365 Overholdelsescenter til at importere & arkivere data fra sider i Facebook Business for at Microsoft 365.
ms.openlocfilehash: f7cbc2b5a0f1ed55379224fc18b1be905e8a4cf0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588920"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Konfigurer en forbindelse til at arkivere Facebook-data (eksempel)

Brug en forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra sider med Facebook Business for at Microsoft 365. Når du konfigurerer forbindelsen, opretter den forbindelse til siden Facebook Business (efter planlagt), konverterer indholdet af Facebook-elementer til et mailformat og importerer derefter disse elementer til en postkasse i Microsoft 365.

Når Facebook-dataene er importeret, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning, In-Place Arkivering, Overvågning, Overholdelse af kommunikation og Microsoft 365-opbevaringspolitikker til Facebook-dataene. Når f.eks. en postkasse er placeret i retslig tilbageholdelse eller er tildelt en opbevaringspolitik, bevares Facebooks data. Du kan søge efter tredjepartsdata ved hjælp af indholdssøgning eller tilknytte den postkasse, hvor Facebook-dataene er gemt, med en assistent i en Advanced eDiscovery sag. Hvis du bruger en forbindelse til at importere og arkivere Facebook-data i Microsoft 365, kan det hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Forudsætninger for konfiguration af en forbindelse til sider i Facebook Business

Fuldfør følgende forudsætninger, før du kan konfigurere en forbindelse i Microsoft 365 Overholdelsescenter til at importere og arkivere data fra din organisations Facebook Business-sider. 

- Du skal bruge en Facebook-konto til din organisations virksomhedssider (du skal logge på denne konto, når du konfigurerer forbindelsen). I øjeblikket kan du kun arkivere data fra sider med Facebook Business. Du kan ikke arkivere data fra individuelle Facebook-profiler.

- Din organisation skal have et gyldigt Azure-abonnement. Hvis du ikke har et eksisterende Azure-abonnement, kan du tilmelde dig en af disse muligheder:

    - [Tilmeld dig et gratis års Azure-abonnement](https://azure.microsoft.com/free)

    - [Tilmeld dig et Pay-As-You-Go Azure-abonnement](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > Det [gratis Azure Active Directory abonnement](use-your-free-azure-ad-subscription-in-office-365.md), der er inkluderet i dit Microsoft 365-abonnement, understøtter ikke forbindelserne i Microsoft 365 Overholdelsescenter.

- Forbindelsessider til Facebook Business kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 Facebook Business-elementer på en dag, importeres ingen af disse elementer til Microsoft 365.

- Den bruger, der konfigurerer den brugerdefinerede forbindelse i Microsoft 365 Overholdelsescenter (i trin 5), skal være tildelt rollen Dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

Det første trin er at registrere en ny app i Azure Active Directory (AAD). Denne app svarer til den webapp-ressource, du implementerer i trin 4 og trin 5 for Facebook-forbindelsen. 

Du kan finde en trinvis vejledning under [Oprette en app i Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Under fuldførelsen af dette trin (ved hjælp af den forrige trinvise vejledning) skal du gemme følgende oplysninger i en tekstfil. Disse værdier bruges i senere trin i installationsprocessen.

- AAD-program-id

- AAD programhemmelighed

- Lejer-id

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Trin 2: Installer forbindelsens webtjeneste fra GitHub din Azure-konto

Næste trin er at installere kildekoden til forbindelsesappen til Facebook Business-sider, der skal bruge Facebook API til at oprette forbindelse til din Facebook-konto og udtrække data, så du kan importere dem til Microsoft 365. Den Facebook-forbindelse, du installerer for din organisation, overfører elementerne fra dine sider med Facebook Business til den placering Azure Storage, der er oprettet i dette trin. Når du har oprettet en forbindelseskomponent til Facebook-virksomhedssider i Microsoft 365 Overholdelsescenter (i trin 5), kopierer tjenesten Importér dataene fra virksomhedens Facebook-sider fra Azure Storage-placeringen til en postkasse i Microsoft 365 organisation. Som beskrevet tidligere i [afsnittet Forudsætninger skal](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) du have et gyldigt Azure-abonnement for at kunne oprette Azure Storage konto.

Du kan finde en trinvis vejledning under [Installér forbindelsens webtjeneste fra GitHub din Azure-konto](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

I den trinvise vejledning til at fuldføre dette trin skal du angive følgende oplysninger:

- APISecretKey: Du opretter denne hemmelighed under fuldførelsen af dette trin. Den bruges i trin 5.

- TenantId: Lejer-id'et for din Microsoft 365 organisation, som du kopierede efter oprettelse af Facebook-forbindelsesappen Azure Active Directory i trin 1.

Når du har fuldført dette trin, skal du sørge for at kopiere Azure-apptjenestens URL-adresse (f.eks. https://fbconnector.azurewebsites.net). Du skal bruge denne URL-adresse for at fuldføre trin 3, trin 4 og trin 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>Trin 3: Registrer webappen på Facebook

Næste trin er at oprette og konfigurere en ny app på Facebook. Den forbindelseskomponent til Facebook-virksomhedssider, som du opretter i trin 5, bruger Facebook-webappen til at interagere med Facebook-API'en for at hente data fra din organisations Facebook-virksomhedssider.

Du kan finde en trinvis vejledning under [Registrer Facebook-appen](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) gemmer du følgende oplysninger i en tekstfil. Disse værdier bruges til at konfigurere appen Facebook-forbindelse i trin 4.

- Facebook-program-id

- Facebook-programhemmelighed

- Facebooks webhooks bekræft token

## <a name="step-4-configure-the-facebook-connector-app"></a>Trin 4: Konfigurer Facebook-forbindelsesappen

Næste trin er at føje konfigurationsindstillinger til Facebook-forbindelsesappen, som du overførte, da du oprettede Azure-webappressourcen i trin 1. Det gør du ved at gå til startsiden i forbindelsesappen og konfigurere den.

Du kan finde en trinvis vejledning under Konfigurer [appen til Facebook-forbindelse](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) angiver du følgende oplysninger (som du har kopieret til en tekstfil efter at have udført de forrige trin):

- Facebook-program-id (hentet i trin 3)

- Facebook-programhemmelighed (hentet i trin 3)

- Facebooks webhooks bekræfter token (hentet i trin 3)

- Azure Active Directory program-id (det AAD program-id, der blev hentet i trin 1)

- Azure Active Directory programhemmelighed (den AAD programhemmelighed, der blev indhentet i trin 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-microsoft-365-compliance-center"></a>Trin 5: Konfigurer en forbindelseskomponent til Facebook Business-sider i Microsoft 365 Overholdelsescenter

Det sidste trin er at konfigurere forbindelsen i Microsoft 365 Overholdelsescenter, der importerer data fra dine Facebook Business-sider til en bestemt postkasse i Microsoft 365. Når du har udført dette trin, begynder Microsoft 365 Importér at importere data fra dine Facebook Business-sider for at Microsoft 365.

Du kan finde en trinvis vejledning i [Trin 5: Konfigurer en Facebook-forbindelse i Microsoft 365 Overholdelsescenter](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center). 

Under fuldførelsen af dette trin (ved at følge den trinvise vejledning) angiver du følgende oplysninger (som du har kopieret til en tekstfil, når du har fuldført trinnene).

- AAD program-id (hentet i trin 1)

- URL-adresse til Azure-apptjeneste (hentet i trin 1, f.eks. https://fbconnector.azurewebsites.net)

- APISecretKey (som du oprettede i trin 2)