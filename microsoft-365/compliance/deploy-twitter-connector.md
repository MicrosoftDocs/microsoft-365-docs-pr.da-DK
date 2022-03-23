---
title: Installér en forbindelse for at arkivere Twitter-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Administratorer kan konfigurere en oprindelig forbindelse til at importere og arkivere Twitter-data for at Microsoft 365. Når disse data importeres til Microsoft 365, kan du bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere styringen af din organisations Twitter-data.
ms.openlocfilehash: bd0885c0b9893b79d36981d52f596d1e5d6b8396
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63588692"
---
# <a name="deploy-a-connector-to-archive-twitter-data"></a>Installér en forbindelse for at arkivere Twitter-data

Denne artikel indeholder den trinvise proces til implementering af en forbindelse, der bruger tjenesten Office 365 Import til at importere data fra din organisations Twitter-konto Microsoft 365. Hvis du vil have en detaljeret oversigt over denne proces og en liste over forudsætninger for at installere en Twitter-forbindelse, skal du se Konfigurer en forbindelse til [at arkivere Twitter-data ](archive-twitter-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

1. Gå til <https://portal.azure.com> og log på med legitimationsoplysningerne fra en global administratorkonto.

   ![Log på Azure.](../media/TCimage01.png)

2. I venstre navigationsrude skal du klikke **på Azure Active Directory**.

   ![Gå til Azure Active Directory.](../media/TCimage02.png)

3. Klik på Appregistreringer (eksempel **) i venstre navigationsrude,** og klik derefter på **Ny registrering**.

   ![Opret en ny appregistrering.](../media/TCimage03.png)

4. Registrer programmet. Under **Redirect URI (valgfrit)** skal du vælge **Web** `https://portal.azure.com` på rullelisten Programtype og derefter skrive i feltet for URI'en.

   ![Skriv https://portal.azure.com for omdirigerings-URI'en.](../media/TCimage04.png)

5. Kopiér **program-id'et (klienten)** og **mappe-id'et (lejer),** og gem dem i en tekstfil eller et andet sikkert sted. Du kan bruge disse ID'er i senere trin.

    ![Kopiér og gem program-id'et og mappe-id'et.](../media/TCimage05.png)

6. Gå til **Certifikater & hemmeligheder for den nye app,** og under **Klienthemmeligheder skal du klikke** **på Ny klienthemmelighed**.

   ![Opret en ny klienthemmelighed.](../media/TCimage06.png)

7. Opret en ny hemmelighed. Skriv hemmeligheden i feltet Beskrivelse, og vælg derefter en udløbsperiode.

   ![Skriv hemmeligheden, og vælg udløbsperiode.](../media/TCimage08.png)

8. Kopiér værdien af hemmeligheden, og gem den i en tekstfil eller en anden lagerplacering. Dette er den AAD programhemmelighed, du bruger i senere trin.

   ![Kopiér og gem hemmeligheden.](../media/TCimage09.png)


## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Trin 2: Installer forbindelsens webtjeneste fra GitHub din Azure-konto

1. Gå til [dette GitHub, og](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) klik på **Deploy to Azure**.

    ![Gå til Azure-startsiden.](../media/FBCimage11.png)

2. Når du har **klikket på Deploy to Azure**, bliver du omdirigeret til en Azure-portal med en brugerdefineret skabelonside. Udfyld Oplysningerne Grundlæggende **og Indstillinger****, og** klik derefter på **Køb**.

   ![Klik på Opret en ressource, og skriv en lagerkonto.](../media/FBCimage12.png)

    - **Abonnement:** Vælg dit Azure-abonnement, som du vil installere Twitter Connector-webtjenesten på.

    - **Ressourcegruppe:** Vælg eller opret en ny ressourcegruppe. En ressourcegruppe er en beholder, der indeholder relaterede ressourcer til en Azure-løsning.

    - **Placering:** Vælg en placering.

    - **Web App-navn:** Angiv et entydigt navn til forbindelseswebappen. Dette navn skal være på mellem 3 og 18 tegn. Dette navn bruges til at oprette AZURE-apptjenestens URL-adresse. Hvis du f.eks. angiver navnet på **twitterconnector** i webappen, bliver URL-adressen til Azure-apptjenesten **twitterconnector.azurewebsites.net**.

    - **tenantId:** Lejer-id'et for din Microsoft 365 organisation, som du kopierede efter oprettelse af Facebook-forbindelsesappen i Azure Active Directory i trin 1.

   - **APISecretKey:** Du kan skrive en hvilken som helst værdi som hemmeligheden. Dette bruges til at få adgang til forbindelseswebappen i trin 5.

3. Når installationen er fuldført, ligner siden følgende skærmbillede:

    ![Klik Storage, og klik derefter Storage konto.](../media/FBCimage13.png)

## <a name="step-3-create-the-twitter-app"></a>Trin 3: Opret Twitter-appen

1. Gå til https://developer.twitter.com, log på med legitimationsoplysningerne for organisationens udviklerkonto, og klik derefter på **Apps**.

   ![Gå til https://developer.twitter.com og log på.](../media/TCimage25-5.png)
2. Klik **på Opret en app**.

   ![Gå til siden Apps for at oprette en app.](../media/TCimage26.png)

3. Tilføj **oplysninger om** programmet under Appoplysninger.

   ![Angiv oplysninger om appen.](../media/TCimage27.png)

4. På Twitter-udviklerdashboardet skal du vælge den app, du lige har oprettet, og derefter klikke på **Detaljer**.

   ![Kopiér og gem app-id'et.](../media/TCimage28.png)

5. På fanen **Nøgler og tokens** skal du under **Forbruger-API-nøgler** kopiere både API-nøgle og API-hemmelig nøgle og gemme dem i en tekstfil eller en anden lagerplacering. Klik derefter **på Opret** for at generere et adgangstoken og få adgang til tokenhemmelighed og kopiere disse til en tekstfil eller en anden lagerplacering.

   ![Kopiér og gem til API-hemmelig nøgle.](../media/TCimage29.png)

   Klik derefter **på Opret** for at generere et adgangstoken og en adgangstokenhemme, og kopiér dem til en tekstfil eller en anden lagerplacering.

6. Klik på **fanen Tilladelser** , og konfigurer tilladelserne som vist på følgende skærmbillede:

   ![Konfigurere tilladelser.](../media/TCimage30.png)

7. Når du gemmer tilladelsesindstillingerne, skal du klikke **på fanen Appoplysninger** og derefter klikke på **Rediger > Rediger detaljer**.

   ![Rediger appdetaljerne.](../media/TCimage31.png)

8. Gør følgende:

   - Markér afkrydsningsfeltet for at tillade, at forbindelsesappen logger på Twitter.

   - Tilføj OAuth-omdirigerings-URI i følgende format: **\<connectorserviceuri>/Views/TwitterOAuth**, hvor værdien af *connectorserviceuri* er URL-adressen til Azure-apptjenesten for organisationen, f.eks https://twitterconnector.azurewebsites.net/Views/TwitterOAuth. .

    ![Tillad, at forbindelsesappen logger på Twitter og tilføjer OAuth-omdirigerings-Uri.](../media/TCimage32.png)

Twitter-udviklerappen er nu klar til brug.

## <a name="step-4-configure-the-connector-web-app"></a>Trin 4: Konfigurer forbindelseswebappen

1. Gå til https://\<AzureAppResourceName>.azurewebsites.net (hvor **AzureAppResourceName** er navnet på din Azure-appressource, som du navngav i trin 4). Hvis navnet f.eks. er **twitterconnector, skal** du gå til https://twitterconnector.azurewebsites.net. Startsiden for appen ser ud som på følgende skærmbillede:

   ![Gå til siden Azure-appressource.](../media/FBCimage41.png)

2. Klik **på Konfigurer** for at få vist en logonside.

   ![Klik på Konfigurer for at vise logonsiden.](../media/FBCimage42.png)

3. I feltet Lejer-id skal du skrive eller indsætte dit lejer-id (som du fik i trin 2). I adgangskodefeltet skal du skrive eller indsætte APISecretKey (som du fik i trin 2), og derefter skal du klikke på Angiv konfiguration **Indstillinger for** at få vist siden med konfigurationsoplysninger.

   ![Log på med lejer-id og API-hemmelig nøgle.](../media/TCimage35.png)

4. Angiv følgende konfigurationsindstillinger

   - **Twitter Api-nøgle:** API-nøglen til det Twitter-program, du oprettede i trin 3.

   - **Twitter Api Secret-nøgle:** API-hemmelighedsnøglen til Twitter-programmet, som du oprettede i trin 3.

   - **Twitter-adgangstoken:** Den adgangstoken, du oprettede i trin 3.

   - **Twitter Access Token Secret:** Den adgangstokenhemme, du oprettede i trin 3.

   - **AAD program-id: Program-id'et** for den Azure Active Directory, du oprettede i trin 1

   - **AAD Programhemmelighed:** Værdien for den APISecretKey-hemmelighed, du oprettede i trin 1.

5. Klik **på Gem** for at gemme indstillingerne for forbindelsen.

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>Trin 5: Konfigurer en Twitter-forbindelse i Microsoft 365 Overholdelsescenter

1. Gå til siden Microsoft 365 Overholdelsescenter, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**siden Dataforbindelser<** /a.

2. Klik på **Vis på** siden Dataforbindelser **under Twitter****.**

3. Klik på **Tilføj** forbindelse på **Twitter-siden**.

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for din forbindelsesapp** skal du angive følgende oplysninger og derefter klikke på **Valider forbindelse**.

   ![Angiv legitimationsoplysninger for forbindelsesappen.](../media/TCimage38.png)

    - Skriv et **navn** til forbindelsen i feltet Navn, f.eks. **Twitters hjælpehåndtag**.

    - I feltet **URL-adresse til forbindelse** skal du skrive eller indsætte AZURE-apptjenestens URL-adresse. for eksempel `https://twitterconnector.azurewebsites.net`.

    - I feltet **Adgangskode** skal du skrive eller indsætte værdien af den APISecretKey, du oprettede i trin 2.

    - I feltet **Azure App-id** skal du skrive eller indsætte værdien af Azure Application App-id'et (også kaldet klient-id'et *), som* du fik i trin 1.

6. Klik på Næste, når forbindelsen er blevet **valideret**.

7. På siden **Authorize Microsoft 365 at importere data** skal du skrive eller indsætte APISecretKey igen og derefter klikke på **Logonwebapp**.

8. Klik **på Log på med Twitter**.

9. På Twitter-logonsiden skal du logge på med legitimationsoplysningerne for din organisations Twitter-konto.

   ![Log på Twitter-konto.](../media/TCimage42.png)

   Når du er logget på, viser Twitter-siden følgende meddelelse: "Twitter Connector Job Er konfigureret."

10. Klik **på Fortsæt** for at fuldføre konfigurationen af Twitter-forbindelsen.

11. På siden **Angiv filtre** kan du anvende et filter til i første omgang at importere elementer, der er en bestemt alder. Vælg en alder, og klik derefter på **Næste**.

12. På siden **Vælg lagerplacering** skal du skrive mailadressen på Microsoft 365, som Twitter-elementerne importeres til, og derefter klikke på **Næste**.

13. Klik **på Næste** for at gennemgå forbindelsesindstillingerne, og klik derefter **på Udfør** for at fuldføre konfigurationen af forbindelsen.

14. I Overholdelsescenter skal du gå til siden **Dataforbindelser** og klikke på fanen Forbindelser for  at se status for importprocessen.
