---
title: Installér en forbindelse til at arkivere data fra Facebook Business-sider
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
description: Administratorer kan konfigurere en oprindelig forbindelse til at importere og arkivere Facebook Business-sider for at Microsoft 365. Når disse data er importeret til Microsoft 365, kan du bruge overholdelsesfunktioner som f.eks retslig tilbageholdelse, indholdssøgning og opbevaringspolitikker til at administrere styringen af din organisations Facebook-data.
ms.openlocfilehash: 0bbe7f65ef6226386911817b40bbaaa418cdabec
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63587686"
---
# <a name="deploy-a-connector-to-archive-facebook-business-pages-data"></a>Installér en forbindelse til at arkivere data fra Facebook Business-sider

Denne artikel indeholder den trinvise proces til installation af en forbindelse, der bruger tjenesten Office 365 Import til at importere data fra sider i Facebook Business Microsoft 365. Hvis du vil have en detaljeret oversigt over denne proces og en liste over forudsætninger, der kræves for at installere en Facebook-forbindelse, skal du se Konfigurere en forbindelse til [at arkivere Facebook-data](archive-facebook-data-with-sample-connector.md).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>Trin 1: Opret en app i Azure Active Directory

1. Gå til <https://portal.azure.com> og log på med legitimationsoplysningerne fra en global administratorkonto.

    ![Opret app AAD.](../media/FBCimage1.png)

2. I venstre navigationsrude skal du klikke **på Azure Active Directory**.

    ![Klik Azure Active Directory.](../media/FBCimage2.png)

3. Klik på Appregistreringer (eksempel **) i venstre navigationsrude,** og klik derefter på **Ny registrering**.

    ![Klik på **Appregistreringer (forhåndsvisning)**, og klik derefter på **Ny registrering**.](../media/FBCimage3.png)

4. Registrer programmet. Under Redirect URI skal du vælge Web på rullelisten Programtype og derefter skrive <https://portal.azure.com> i feltet for URI'en.

   ![Registrer programmet.](../media/FBCimage4.png)

5. Kopiér **program-id'et (klienten)** og **mappe-id'et (lejer),** og gem dem i en tekstfil eller et andet sikkert sted. Du kan bruge disse ID'er i senere trin.

   ![Kopiér program-id'et og mappe-id'et, og gem dem.](../media/FBCimage5.png)

6. Gå til **Certifikater & hemmeligheder for den nye app.**

   ![Gå til Certifikater & hemmeligheder for den nye app.](../media/FBCimage6.png)

7. Klik **på Ny klienthemmelighed**

   ![Klik på Ny klienthemmelighed.](../media/FBCimage7.png)

8. Opret en ny hemmelighed. Skriv hemmeligheden i feltet Beskrivelse, og vælg derefter en udløbsperiode.

    ![Skriv hemmeligheden, og vælg derefter en udløbsperiode.](../media/FBCimage8.png)

9. Kopiér værdien af hemmeligheden, og gem den i en tekstfil eller en anden lagerplacering. Dette er den AAD programhemmelighed, du bruger i senere trin.

   ![Kopiér værdien af hemmeligheden, og gem den.](../media/FBCimage9.png)

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>Trin 2: Installer forbindelsens webtjeneste fra GitHub din Azure-konto

1. Gå til [dette GitHub, og](https://github.com/microsoft/m365-sample-connector-csharp-aspnet) klik på **Deploy to Azure**.

    ![Klik på Installér til Azure.](../media/FBCGithubApp.png)

2. Når du har **klikket på Deploy to Azure**, bliver du omdirigeret til en Azure-portal med en brugerdefineret skabelonside. Udfyld Oplysningerne Grundlæggende **og Indstillinger****, og** klik derefter på **Køb**.

   - **Abonnement:** Vælg det Azure-abonnement, du vil installere forbindelsestjenesten til Facebook Business-sider.

   - **Ressourcegruppe:** Vælg eller opret en ny ressourcegruppe. En ressourcegruppe er en beholder, der indeholder relaterede ressourcer til en Azure-løsning.

   - **Placering:** Vælg en placering.

   - **Web App-navn:** Angiv et entydigt navn til forbindelseswebappen. Dette navn skal være på mellem 3 og 18 tegn. Dette navn bruges til at oprette AZURE-apptjenestens URL-adresse. Hvis du f.eks. angiver navnet på **webappen på fbconnector** , bliver Azure-apptjenestens **URL-adresse fbconnector.azurewebsites.net**.

   - **tenantId:** Lejer-id'et for Microsoft 365 organisation, som du kopierede efter oprettelse af Facebook-forbindelsesappen i Azure Active Directory trin 1.

   - **APISecretKey:** Du kan skrive en hvilken som helst værdi som hemmeligheden. Dette bruges til at få adgang til forbindelseswebappen i trin 5.

     ![Klik på Opret en ressource, og skriv en lagerkonto.](../media/FBCimage12.png)

3. Når installationen er fuldført, ligner siden følgende skærmbillede:

   ![Klik Storage, og klik derefter Storage konto.](../media/FBCimage13.png)

## <a name="step-3-register-the-facebook-app"></a>Trin 3: Registrer Facebook-appen

1. Gå til <https://developers.facebook.com>, log på med legitimationsoplysningerne til kontoen for din organisations Facebook Business-sider, og klik derefter på **Tilføj ny app**.

   ![Tilføj en ny app til Din Facebook-virksomhedsside.](../media/FBCimage25.png)

2. Opret et nyt app-id.

   ![Opret et nyt app-id.](../media/FBCimage26.png)

3. I venstre navigationsrude skal du klikke **på Tilføj produkter** og derefter **klikke på Konfigurer** **i feltet Facebook-logon** .

   ![Klik på Tilføj produkter.](../media/FBCimage27.png)

4. Klik på Web på siden Integrer **Facebook-logon**.

   ![Klik på Web på logonsiden til Integrer Facebook.](../media/FBCimage28.png)

5. Tilføj Azure-apptjenestens URL-adresse. for eksempel `https://fbconnector.azurewebsites.net`.

   ![Tilføj Azure-apptjenestens URL-adresse.](../media/FBCimage29.png)

6. Fuldfør sektionen Hurtig start i logonkonfigurationen til Facebook.

   ![Fuldfør sektionen Hurtig start.](../media/FBCimage30.png)

7. I venstre navigationsrude under **Facebook-logon** skal du klikke **på Indstillinger** og tilføje OAuth-omdirigerings-URI'en i feltet **Gyldige OAuth-omdirigerings-URI'er**. Brug formatet **\<connectorserviceuri>/Views/FacebookOAuth**, hvor værdien for connectorserviceuri er URL-adressen til Azure-apptjenesten for organisationen, f.eks. `https://fbconnector.azurewebsites.net`.

   ![Føj OAuth-omdirigerings-URI'en til feltet Gyldige OAuth-omdirigerings-URI'er.](../media/FBCimage31.png)

8. I venstre navigationsrude skal du **klikke på Tilføj** produkter og derefter **klikke på Webhooks.** Klik **på Side** i rullemenuen **Side**.

   ![Klik på Tilføj produkter, og klik derefter på **Webhooks.](../media/FBCimage32.png)

9. Tilføj URL-adresse på Webhooks Callback, og tilføj en bekræftelsestoken. Formatet af URL-adressen til tilbagekald, `<connectorserviceuri>/api/FbPageWebhook`skal du bruge formatet , hvor værdien for connectorserviceuri er URL-adressen til Azure-apptjenesten for organisationen, f.eks `https://fbconnector.azurewebsites.net`. .

   Bekræftelsestokenet bør ligne en stærk adgangskode. Kopiér bekræftelsestokenet til en tekstfil eller en anden lagerplacering.

   ![Tilføj bekræftelsestokenet.](../media/FBCimage33.png)

10. Test og abonner på slutpunktet for feedet.

    ![Test og abonner på slutpunktet.](../media/FBCimage34.png)

11. Tilføj en URL-adresse til beskyttelse af personlige oplysninger, appikon og virksomhedsbrug. Kopiér også app-id'et og apphemmelighederne til en tekstfil eller en anden lagerplacering.

    ![Tilføj en URL-adresse til beskyttelse af personlige oplysninger, appikon og virksomhedsbrug.](../media/FBCimage35.png)

12. Gør appen offentlig.

    ![Gør appen offentlig.](../media/FBCimage36.png)

13. Føj bruger til administrator- eller testrollen.

    ![Føj bruger til administrator- eller testrollen.](../media/FBCimage37.png)

14. Tilføj tilladelsen **Side offentlig adgang til** indhold.

    ![dd tilladelsen Side offentlig adgang til indhold.](../media/FBCimage38.png)

15. Tilføj tilladelsen Administrer sider.

    ![Tilføj tilladelsen Administrer sider.](../media/FBCimage39.png)

16. Få programmet gennemgået af Facebook.

    ![Få programmet gennemgået af Facebook.](../media/FBCimage40.png)

## <a name="step-4-configure-the-connector-web-app"></a>Trin 4: Konfigurer forbindelseswebappen

1. Gå til `https://<AzureAppResourceName>.azurewebsites.net` (hvor AzureAppResourceName er navnet på din Azure-appressource, du har navngivet i trin 4). Hvis f.eks. navnet er **fbconnector, skal** du gå til `https://fbconnector.azurewebsites.net`. Startsiden for appen ser ud som på følgende skærmbillede:

   ![Gå til forbindelseswebappen for dig.](../media/FBCimage41.png)

2. Klik **på Konfigurer** for at få vist en logonside.

   ![Klik på Konfigurer for at få vist en logonside.](../media/FBCimage42.png)

3. I feltet Lejer-id skal du skrive eller indsætte dit lejer-id (som du fik i trin 2). I adgangskodefeltet skal du skrive eller indsætte APISecretKey (som du fik i trin 2), og derefter skal du klikke på Angiv konfiguration **Indstillinger for** at få vist siden med konfigurationsoplysninger.

    ![Log på med dit lejer-id og din adgangskode, og gå til siden med konfigurationsoplysninger.](../media/FBCimage43.png)

4. Angiv følgende konfigurationsindstillinger

   - **Facebook-program-id:** App-id'et for det Facebook-program, du har fået i trin 3.

   - **Facebook-programhemmelighed:** Apphemmelighederne for det Facebook-program, du har fået i trin 3.

   - **Facebooks webhooks bekræft token:** Den bekræftelsestoken, du oprettede i trin 3.

   - **AAD program-id:** Program-id'et for den Azure Active Directory, du oprettede i trin 1.

   - **AAD programhemmelighed:** Værdien for den APISecretKey-hemmelighed, du oprettede i trin 1.

5. Klik **på Gem** for at gemme indstillingerne for forbindelsen.

## <a name="step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center"></a>Trin 5: Konfigurer en Facebook-forbindelse i Microsoft 365 Overholdelsescenter

1. Gå til Microsoft 365 Overholdelsescenter, og vælg derefter <a href="https://go.microsoft.com/fwlink/p/?linkid=2173865" target="_blank">**Dataforbindelser<** /a.

2. Klik på **Vis på siden** **Dataforbindelser under Facebook Business-sider**.

3. Klik på **Tilføj forbindelse på** siden Med **Facebook-virksomheder**.

4. Klik **på Acceptér på** siden **Servicebetingelser**.

5. På siden **Tilføj legitimationsoplysninger for din forbindelsesapp** skal du angive følgende oplysninger og derefter klikke på **Valider forbindelse**.

   ![Angiv legitimationsoplysninger for forbindelsesappen.](../media/TCimage38.png)

   - Skriv et **navn** på forbindelsen i feltet Navn, f.eks. **Nyhedsside på Facebook**.

   - I feltet **Url-adresse til** forbindelse skal du skrive eller indsætte URL-adressen til Azure-apptjenesten. for eksempel `https://fbconnector.azurewebsites.net`.

   - I feltet **Adgangskode** skal du skrive eller indsætte værdien af den APISecretKey, du tilføjede i trin 2.

   - I feltet **Azure App-id** skal du skrive eller indsætte værdien af program-id'et (klient), også kaldet AAD-program-id, som du oprettede i trin 1.

6. Klik på Næste, når forbindelsen er blevet **valideret**.

7. På siden **Authorize Microsoft 365 at importere data** skal du skrive eller indsætte APISecretKey igen og derefter klikke på **Logonwebapp**.

8. På siden **Konfigurer forbindelsesapp til Facebook** skal du klikke på Log på med **Facebook** og logge på ved hjælp af legitimationsoplysningerne til kontoen for din organisations Facebook Business-sider. Sørg for, at den Facebook-konto, du er logget på, er tildelt administratorrollen for din organisations Facebook Business-sider.

   ![Log på med Facebook.](../media/FBCimage50.png)

9. Der vises en liste over de virksomhedssider, der administreres af den Facebook-konto, du er logget på. Vælg den side, der skal arkiveres, og klik derefter på **Næste**.

   ![Vælg den virksomhedsside, du vil arkivere.](../media/FBCimage52.png)

10. Klik **på** Fortsæt for at afslutte konfigurationen af forbindelsestjenesteappen.

11. På siden **Angiv filtre** kan du anvende et filter til i første omgang at importere elementer, der er en bestemt alder. Vælg en alder, og klik derefter på **Næste**.

12. På siden **Vælg lagerplacering** skal du skrive mailadressen på Microsoft 365, som Facebook-elementerne importeres til, og derefter klikke på **Næste**.

13. Klik **på Næste** for at gennemgå forbindelsesindstillingerne, og klik derefter **på Udfør** for at fuldføre konfigurationen af forbindelsen.

14. I Overholdelsescenter skal du gå til siden **Dataforbindelser** og klikke på fanen Forbindelser for  at se status for importprocessen.
