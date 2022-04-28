---
title: Udrul en connector for at arkivere Twitter-data
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ROBOTS: NOINDEX, NOFOLLOW
description: Administratorer kan konfigurere en oprindelig connector til at importere og arkivere Twitter-data for at Microsoft 365. Når disse data er importeret til Microsoft 365, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridiske ventepositioner, indholdssøgning og opbevaringspolitikker til at administrere styringen af din organisations Twitter-data.
ms.openlocfilehash: a928e24c73fcbb290bde2caa0f508610fc18728d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090955"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Udrul en connector for at arkivere Twitter-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Denne artikel indeholder den trinvise proces til installation af en connector, der bruger tjenesten Office 365 Import til at importere data fra din organisations Twitter-konto til Microsoft 365. Hvis du vil have en overordnet oversigt over denne proces og en liste over forudsætninger, der kræves for at installere en Twitter-connector, skal du se [Konfigurer en connector til arkivering af Twitter-data ](archive-twitter-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

1. Gå til , <https://portal.azure.com> og log på med legitimationsoplysningerne for en global administratorkonto.

   ![Log på Azure.](../media/TCimage01.png)

2. Klik på **Azure Active Directory** i navigationsruden til venstre.

   ![Gå til Azure Active Directory.](../media/TCimage02.png)

3. Klik på **Appregistreringer (prøveversion)** i navigationsruden til venstre, og klik derefter på **Ny registrering**.

   ![Opret en ny appregistrering.](../media/TCimage03.png)

4. Registrer programmet. Under **Omdirigerings-URI (valgfrit)** skal du vælge **Web** på rullelisten Programtype og derefter skrive `https://portal.azure.com` i feltet for URI'en.

   ![Skriv https://portal.azure.com for omdirigerings-URI'en.](../media/TCimage04.png)

5. Kopiér **program-id'et (klient-id'et)** og **mappe-id'et (lejeren),** og gem dem i en tekstfil eller et andet sikkert sted. Du bruger disse id'er i senere trin.

    ![Kopiér og gem program-id'et og mappe-id'et.](../media/TCimage05.png)

6. Gå til **Certifikater & hemmeligheder for den nye app**, og klik på **Ny klienthemmelighed under Klienthemmeligheder**.

   ![Opret en ny klienthemmelighed.](../media/TCimage06.png)

7. Opret en ny hemmelighed. Skriv hemmeligheden i feltet Beskrivelse, og vælg derefter en udløbsperiode.

   ![Skriv hemmeligheden, og vælg udløbsperiode.](../media/TCimage08.png)

8. Kopiér værdien af hemmeligheden, og gem den i en tekstfil eller på en anden lagerplacering. Dette er den AAD programhemmelighed, du bruger i senere trin.

   ![Kopiér og gem hemmeligheden.](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Trin 2: Udrul connectorwebtjenesten fra GitHub til din Azure-konto

1. Gå til [dette GitHub websted](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet), og klik på **Udrul på Azure**.

    ![Gå til startsiden for Azure.](../media/FBCimage11.png)

2. Når du har klikket på **Udrul på Azure**, omdirigeres du til en Azure Portal med en brugerdefineret skabelonside. Udfyld de **grundlæggende** oplysninger og **Indstillinger** oplysninger, og klik derefter på **Køb**.

   ![Klik på Opret en ressource, og skriv lagerkonto.](../media/FBCimage12.png)

    - **Abonnement:** Vælg dit Azure-abonnement, som du vil installere webtjenesten til Twitter-connectoren til.

    - **Ressourcegruppe:** Vælg eller opret en ny ressourcegruppe. En ressourcegruppe er en objektbeholder, der indeholder relaterede ressourcer til en Azure-løsning.

    - **Placering:** Vælg en placering.

    - **Navn på webapp:** Angiv et entydigt navn til connectorwebappen. Navnet skal være mellem 3 og 18 tegn langt. Dette navn bruges til at oprette URL-adressen til Azure-apptjenesten. Hvis du f.eks. angiver navnet på webappen på **twitterconnectoren** , bliver URL-adressen til Azure-apptjenesten **twitterconnector.azurewebsites.net**.

    - **tenantId:** Lejer-id'et for din Microsoft 365 organisation, som du kopierede efter oprettelse af Facebook-connectorappen i Azure Active Directory i trin 1.

   - **APISecretKey:** Du kan skrive en hvilken som helst værdi som hemmeligheden. Dette bruges til at få adgang til connectorwebappen i trin 5.

3. Når installationen er fuldført, ligner siden følgende skærmbillede:

    ![Klik på Storage, og klik derefter på Storage konto.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>Trin 3: Opret Twitter-appen

1. Gå til https://developer.twitter.com, log på ved hjælp af legitimationsoplysningerne for udviklerkontoen for din organisation, og klik derefter på **Apps**.

   ![Gå til , https://developer.twitter.com og log på.](../media/TCimage25-5.png)
2. Klik på **Opret en app**.

   ![Gå til siden Apps for at oprette en app.](../media/TCimage26.png)

3. Under **Appdetaljer** skal du tilføje oplysninger om programmet.

   ![Angiv oplysninger om appen.](../media/TCimage27.png)

4. Vælg den app, du lige har oprettet, på Twitter-udviklerdashboardet, og klik derefter på **Detaljer**.

   ![Kopiér og gem app-id'et.](../media/TCimage28.png)

5. Under fanen **Nøgler og tokens** under **Forbruger-API-nøgler** skal du kopiere både API-nøglen og API-hemmelighedsnøglen og gemme dem i en tekstfil eller på en anden lagringsplacering. Klik derefter på **Opret** for at generere en adgangstoken- og adgangstokenhemmelighed og kopiere dem til en tekstfil eller en anden lagerplacering.

   ![Kopiér og gem til API-hemmelig nøgle.](../media/TCimage29.png)

   Klik derefter på **Opret** for at generere et adgangstoken og en adgangstokenhemmelighed, og kopiér dem til en tekstfil eller en anden lagerplacering.

6. Klik på fanen **Tilladelser,** og konfigurer tilladelserne som vist på følgende skærmbillede:

   ![Konfigurer tilladelser.](../media/TCimage30.png)

7. Når du har gemt tilladelsesindstillingerne, skal du klikke på fanen **Appdetaljer** og derefter klikke på **Rediger > Rediger detaljer**.

   ![Rediger appdetaljerne.](../media/TCimage31.png)

8. Gør følgende opgaver:

   - Markér afkrydsningsfeltet for at tillade, at connectorappen logger på Twitter.

   - Tilføj OAuth-omdirigerings-URI'en i følgende format: **\<connectorserviceuri>/Views/TwitterOAuth**, hvor værdien af *connectorserviceuri* er URL-adressen til Azure-apptjenesten for din organisation, https://twitterconnector.azurewebsites.net/Views/TwitterOAuthf.eks. .

    ![Tillad, at connectorappen logger på Twitter, og tilføj OAuth-omdirigerings-URI'en.](../media/TCimage32.png)

Udviklerappen Twitter er nu klar til brug.

## <a name="step-4-configure-the-connector-web-app"></a>Trin 4: Konfigurer connectorwebappen

1. Gå til https://\<AzureAppResourceName>.azurewebsites.net (hvor **AzureAppResourceName** er navnet på din Azure-appressource, som du har navngivet i trin 4). Hvis navnet f.eks. er **twitterconnector**, skal du gå til https://twitterconnector.azurewebsites.net. Startsiden for appen ser ud som på følgende skærmbillede:

   ![Gå til ressourcesiden for Azure-appen.](../media/FBCimage41.png)

2. Klik på **Konfigurer** for at få vist en logonside.

   ![Klik på Konfigurer for at få vist logonsiden.](../media/FBCimage42.png)

3. I feltet Lejer-id skal du skrive eller indsætte dit lejer-id (som du fik i trin 2). Skriv eller indsæt APISecretKey (som du fik i trin 2) i feltet adgangskode, og klik derefter på **Angiv konfiguration Indstillinger** for at få vist siden med konfigurationsoplysninger.

   ![Log på med lejer-id og API-hemmelig nøgle.](../media/TCimage35.png)

4. Angiv følgende konfigurationsindstillinger

   - **Api-nøgle til Twitter:** API-nøglen til det Twitter-program, du oprettede i trin 3.

   - **Hemmelig nøgle til Twitter-API:** Den HEMMELIGE API-nøgle for det Twitter-program, du oprettede i trin 3.

   - **Adgangstoken til Twitter:** Det adgangstoken, du oprettede i trin 3.

   - **Twitter-adgangstokenhemmelighed:** Den adgangstokenhemmelighed, du oprettede i Trin 3.

   - **AAD program-id:** Program-id'et for den Azure Active Directory app, du oprettede i trin 1

   - **AAD Programhemmelighed:** Værdien for den APISecretKey-hemmelighed, du oprettede i trin 1.

5. Klik på **Gem** for at gemme connectorindstillingerne.

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>Trin 5: Konfigurer en Twitter-connector på overholdelsesportalen

1. Gå til Microsoft Purview-overholdelsesportalen, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank"> siden **Dataconnectors**</a.

2. Klik på **Vis** på siden **Dataconnectors** under **Twitter**.

3. Klik på **Tilføj connector** på **Twitter-siden**.

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. Angiv følgende oplysninger på siden **Tilføj legitimationsoplysninger for din connectorapp** , og klik derefter på **Valider forbindelse**.

   ![Angiv legitimationsoplysninger til connectorappen.](../media/TCimage38.png)

    - Skriv et navn til connectoren i feltet **Navn** , f.eks **. Hjælp-håndtag til Twitter**.

    - I feltet **URL-adresse til connector** skal du skrive eller indsætte URL-adressen til Azure-apptjenesten. for eksempel `https://twitterconnector.azurewebsites.net`.

    - I feltet **Adgangskode** skal du skrive eller indsætte værdien af den APISecretKey, du oprettede i trin 2.

    - I feltet **Azure App ID** skal du skrive eller indsætte værdien af det Azure Application App Id (også kaldet *klient-id),* du fik i trin 1.

6. Når forbindelsen er valideret, skal du klikke på **Næste**.

7. På siden **Godkend Microsoft 365 at importere data** skal du skrive eller indsætte APISecretKey igen og derefter klikke på **Logonwebapp**.

8. Klik på **Log på med Twitter**.

9. Log på ved hjælp af legitimationsoplysningerne for din organisations Twitter-konto på logonsiden til Twitter.

   ![Log på En Twitter-konto.](../media/TCimage42.png)

   Når du har logget på, vises følgende meddelelse på Twitter-siden om, at Jobbet til Twitter-connectoren er konfigureret korrekt.

10. Klik på **Fortsæt** for at fuldføre indstillingerne af Twitter-connectoren.

11. På siden **Angiv filtre** kan du anvende et filter til indledningsvist at importere elementer, der er af en bestemt alder. Vælg en alder, og klik derefter på **Næste**.

12. På siden **Vælg lagerplacering** skal du skrive mailadressen på Microsoft 365 postkasse, som Twitter-elementerne importeres til, og derefter klikke på **Næste**.

13. Klik på **Næste** for at gennemse connectorindstillingerne, og klik derefter på **Udfør** for at fuldføre connectorkonfigurationen.

14. I Overholdelsescenter skal du gå til siden **Dataconnectors** og klikke på fanen **Forbindelser** for at se status for importprocessen.
