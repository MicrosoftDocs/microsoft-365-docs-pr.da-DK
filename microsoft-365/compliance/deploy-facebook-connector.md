---
title: Udrul en connector for at arkivere data på Facebook-virksomhedssider
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
description: Administratorer kan konfigurere en oprindelig connector til at importere og arkivere Facebook Business-sider til Microsoft 365. Når disse data er importeret til Microsoft 365, kan du bruge funktioner til overholdelse af angivne standarder, f.eks. juridiske ventepositioner, indholdssøgning og opbevaringspolitikker til at administrere styringen af din organisations Facebook-data.
ms.openlocfilehash: 0b2d37859941cc0e1ae5c49fad6fd72312cc03cf
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632547"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Udrul en connector for at arkivere data på Facebook-virksomhedssider

Denne artikel indeholder den trinvise proces til installation af en connector, der bruger tjenesten Office 365 import til at importere data fra Facebook Business-sider til Microsoft 365. Hvis du vil have en overordnet oversigt over denne proces og en liste over forudsætninger, der kræves for at installere en Facebook-connector, skal du se [Konfigurer en connector til arkivering af Facebook-data](archive-facebook-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

1. Gå til , <https://portal.azure.com> og log på med legitimationsoplysningerne for en global administratorkonto.

    ![Opret app i AAD.](../media/FBCimage1.png)

2. Klik på **Azure Active Directory** i navigationsruden til venstre.

    ![Klik på Azure Active Directory.](../media/FBCimage2.png)

3. Klik på **Appregistreringer (prøveversion)** i navigationsruden til venstre, og klik derefter på **Ny registrering**.

    ![Klik på **Appregistreringer (prøveversion)**, og klik derefter på **Ny registrering**.](../media/FBCimage3.png)

4. Registrer programmet. Under Omdirigerings-URI skal du vælge Web på rullelisten Programtype og derefter skrive <https://portal.azure.com> i feltet for URI'en.

   ![Registrer programmet.](../media/FBCimage4.png)

5. Kopiér **program-id'et (klient-id'et)** og **mappe-id'et (lejeren),** og gem dem i en tekstfil eller et andet sikkert sted. Du bruger disse id'er i senere trin.

   ![Kopiér program-id'et og mappe-id'et, og gem dem.](../media/FBCimage5.png)

6. Gå til **Certifikater & hemmeligheder for den nye app.**

   ![Gå til Certifikater & hemmeligheder for den nye app.](../media/FBCimage6.png)

7. Klik på **Ny klienthemmelighed**

   ![Klik på Ny klienthemmelighed.](../media/FBCimage7.png)

8. Opret en ny hemmelighed. Skriv hemmeligheden i feltet Beskrivelse, og vælg derefter en udløbsperiode.

    ![Skriv hemmeligheden, og vælg derefter en udløbsperiode.](../media/FBCimage8.png)

9. Kopiér værdien af hemmeligheden, og gem den i en tekstfil eller på en anden lagerplacering. Dette er AAD-programhemmeligheden, som du bruger i senere trin.

   ![Kopiér værdien af hemmeligheden, og gem den.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Trin 2: Udrul connectorwebtjenesten fra GitHub på din Azure-konto

1. Gå til [dette GitHub-websted,](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) og klik på **Udrul på Azure**.

    ![Klik på Udrul på Azure.](../media/FBCGithubApp.png)

2. Når du har klikket på **Udrul på Azure**, omdirigeres du til en Azure Portal med en brugerdefineret skabelonside. Udfyld de **grundlæggende** oplysninger og **indstillinger,** og klik derefter på **Køb**.

   - **Abonnement:** Vælg dit Azure-abonnement, som du vil udrulle webtjenesten for Facebook Business-sider-connectoren til.

   - **Ressourcegruppe:** Vælg eller opret en ny ressourcegruppe. En ressourcegruppe er en objektbeholder, der indeholder relaterede ressourcer til en Azure-løsning.

   - **Placering:** Vælg en placering.

   - **Navn på webapp:** Angiv et entydigt navn til connectorwebappen. Navnet skal være mellem 3 og 18 tegn langt. Dette navn bruges til at oprette URL-adressen til Azure-apptjenesten. Hvis du f.eks. angiver navnet på **webappen fbconnector** , bliver URL-adressen til Azure-apptjenesten **fbconnector.azurewebsites.net**.

   - **tenantId:** Lejer-id'et for din Microsoft 365-organisation, som du kopierede efter oprettelse af Facebook-connectorappen i Azure Active Directory i trin 1.

   - **APISecretKey:** Du kan skrive en hvilken som helst værdi som hemmeligheden. Dette bruges til at få adgang til connectorwebappen i trin 5.

     ![Klik på Opret en ressource, og skriv lagerkonto.](../media/FBCimage12.png)

3. Når installationen er fuldført, ligner siden følgende skærmbillede:

   ![Klik på Lager, og klik derefter på Lagerkonto.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>Trin 3: Registrer Facebook-appen

1. Gå til <https://developers.facebook.com>, log på ved hjælp af legitimationsoplysningerne for kontoen for din organisations Facebook Business-sider, og klik derefter på **Tilføj ny app**.

   ![Tilføj en ny app til Facebook-virksomhedssiden.](../media/FBCimage25.png)

2. Opret et nyt app-id.

   ![Opret et nyt app-id.](../media/FBCimage26.png)

3. Klik på **Tilføj produkter** i navigationsruden til venstre, og klik derefter på **Konfigurer** i feltet **Facebook-logon** .

   ![Klik på Tilføj produkter.](../media/FBCimage27.png)

4. Klik på **Web** på siden Integrer Facebook-logon.

   ![Klik på Web på siden Integrer Facebook-logon.](../media/FBCimage28.png)

5. Tilføj URL-adressen til Azure-apptjenesten. for eksempel `https://fbconnector.azurewebsites.net`.

   ![Tilføj URL-adressen til Azure-apptjenesten.](../media/FBCimage29.png)

6. Fuldfør afsnittet Hurtig start i konfigurationen af Facebook-logon.

   ![Fuldfør sektionen Hurtig start.](../media/FBCimage30.png)

7. Klik på **Indstillinger** i navigationsruden til venstre under **Facebook-logon**, og tilføj OAuth-omdirigerings-URI'en i feltet **Gyldige OAuth-omdirigerings-URI'er**. Brug formatet **\<connectorserviceuri>/Views/FacebookOAuth**, hvor værdien for connectorserviceuri er URL-adressen til Azure-apptjenesten for din organisation, `https://fbconnector.azurewebsites.net`f.eks. .

   ![Føj OAuth-omdirigerings-URI'en til feltet Gyldige OAuth-omdirigerings-URI'er.](../media/FBCimage31.png)

8. Klik på **Tilføj produkter** i navigationsruden til venstre, og klik derefter på **Webhooks.** Klik på **Side** i rullemenuen **Side**.

   ![Klik på Tilføj produkter, og klik derefter på **Webhooks.](../media/FBCimage32.png)

9. Tilføj URL-adressen til tilbagekald til Webhooks, og tilføj et bekræftelsestoken. Formatet for URL-adressen til tilbagekald skal du bruge formatet `<connectorserviceuri>/api/FbPageWebhook`, hvor værdien for connectorserviceuri er URL-adressen til Azure-apptjenesten for din organisation, f.eks `https://fbconnector.azurewebsites.net`. .

   Bekræftelsestokenet skal ligne en stærk adgangskode. Kopiér tokenet til bekræftelse til en tekstfil eller en anden lagringsplacering.

   ![Tilføj bekræftelsestokenet.](../media/FBCimage33.png)

10. Test og abonner på slutpunktet for feed.

    ![Test og abonner på slutpunktet.](../media/FBCimage34.png)

11. Tilføj en URL-adresse til beskyttelse af personlige oplysninger, et appikon og forretningsbrug. Kopiér også app-id'et og apphemmeligheden til en tekstfil eller en anden lagerplacering.

    ![Tilføj en URL-adresse til beskyttelse af personlige oplysninger, et appikon og forretningsbrug.](../media/FBCimage35.png)

12. Gør appen offentlig.

    ![Gør appen offentlig.](../media/FBCimage36.png)

13. Føj brugeren til rollen administrator eller tester.

    ![Føj brugeren til rollen administrator eller tester.](../media/FBCimage37.png)

14. Tilføj tilladelsen **Adgang til offentligt indhold på siden** .

    ![dd tilladelsen Adgang til offentligt indhold på siden.](../media/FBCimage38.png)

15. Tilføj tilladelsen Administrer sider.

    ![Tilføj tilladelsen Administrer sider.](../media/FBCimage39.png)

16. Få appen gennemgået af Facebook.

    ![Få appen gennemgået af Facebook.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>Trin 4: Konfigurer connectorwebappen

1. Gå til `https://<AzureAppResourceName>.azurewebsites.net` (hvor AzureAppResourceName er navnet på din Azure-appressource, som du har navngivet i Trin 4). Hvis navnet **fbconnector** f.eks. er , skal du gå til `https://fbconnector.azurewebsites.net`. Startsiden for appen ser ud som på følgende skærmbillede:

   ![Gå til din connectorwebapp.](../media/FBCimage41.png)

2. Klik på **Konfigurer** for at få vist en logonside.

   ![Klik på Konfigurer for at få vist en logonside.](../media/FBCimage42.png)

3. I feltet Lejer-id skal du skrive eller indsætte dit lejer-id (som du fik i trin 2). Skriv eller indsæt APISecretKey (som du fik i trin 2) i feltet adgangskode, og klik derefter på **Angiv konfigurationsindstillinger** for at få vist siden med konfigurationsoplysninger.

    ![Log på med dit lejer-id og din adgangskode, og gå til siden med konfigurationsoplysninger.](../media/FBCimage43.png)

4. Angiv følgende konfigurationsindstillinger

   - **Facebook-program-id:** App-id'et for det Facebook-program, du fik i trin 3.

   - **Facebook-programhemmelighed:** Den apphemmelighed for Facebook-programmet, som du fik i trin 3.

   - **Token til bekræftelse af facebook-webhooks:** Det bekræftelsestoken, du oprettede i trin 3.

   - **AAD-program-id:** Program-id'et for den Azure Active Directory-app, du oprettede i trin 1.

   - **AAD-programhemmelighed:** Værdien for den APISecretKey-hemmelighed, du oprettede i trin 1.

5. Klik på **Gem** for at gemme connectorindstillingerne.

## <a name="step-5-set-up-a-facebook-connector-in-the-compliance-portal"></a>Trin 5: Konfigurer en Facebook-connector på overholdelsesportalen

1. Gå til Microsoft Purview-compliance-portal, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank"> derefter **Dataconnectors**</a.

2. På siden **Dataconnectors** under **Facebook Business-sider** skal du klikke på **Vis**.

3. Klik på **Tilføj connector** på siden **Facebook-forretningssider**.

4. Klik på **Acceptér** på siden **Vilkår for tjeneste**.

5. Angiv følgende oplysninger på siden **Tilføj legitimationsoplysninger for din connectorapp** , og klik derefter på **Valider forbindelse**.

   ![Angiv legitimationsoplysninger til connectorappen.](../media/TCimage38.png)

   - Skriv et navn til connectoren i feltet **Navn** , f.eks **. Facebooks nyhedsside**.

   - I feltet **URL-adresse til forbindelse** skal du skrive eller indsætte URL-adressen til Azure-apptjenesten. for eksempel `https://fbconnector.azurewebsites.net`.

   - I feltet **Adgangskode** skal du skrive eller indsætte værdien af den APISecretKey, du tilføjede i trin 2.

   - I feltet **Azure App ID** skal du skrive eller indsætte værdien af det program-id (klient),der også kaldes som AAD-program-id, som du oprettede i trin 1.

6. Når forbindelsen er valideret, skal du klikke på **Næste**.

7. På siden **Godkend, at Microsoft 365 importerer data** skal du skrive eller indsætte APISecretKey igen og derefter klikke på **Logon-webapp**.

8. På siden **Konfigurer Facebook-connectorapp** skal du klikke på **Log på med Facebook** og logge på ved hjælp af legitimationsoplysningerne for kontoen for din organisations Facebook Business-sider. Sørg for, at den Facebook-konto, du loggede på, er tildelt administratorrollen for din organisations Facebook-virksomhedssider.

   ![Log på med Facebook.](../media/FBCimage50.png)

9. En liste over de virksomhedssider, der administreres af den Facebook-konto, du loggede på, vises. Vælg den side, der skal arkiveres, og klik derefter på **Næste**.

   ![Vælg den organisationsforretningsside, du vil arkivere.](../media/FBCimage52.png)

10. Klik på **Fortsæt** for at afslutte konfigurationen af connectortjenesteappen.

11. På siden **Angiv filtre** kan du anvende et filter til indledningsvist at importere elementer, der er af en bestemt alder. Vælg en alder, og klik derefter på **Næste**.

12. På siden **Vælg lagerplacering** skal du skrive mailadressen på den Microsoft 365-postkasse, som Facebook-elementerne importeres til, og derefter klikke på **Næste**.

13. Klik på **Næste** for at gennemse connectorindstillingerne, og klik derefter på **Udfør** for at fuldføre connectorkonfigurationen.

14. I Overholdelsescenter skal du gå til siden **Dataconnectors** og klikke på fanen **Forbindelser** for at se status for importprocessen.
