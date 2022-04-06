---
title: Opret en app for at få adgang Microsoft Defender for Endpoint uden en bruger
ms.reviewer: ''
description: Få mere at vide om, hvordan du designer en webapp for at få programmeringsadgang Microsoft Defender for Endpoint uden en bruger.
keywords: apis, graph api, understøttede API'er, agent, beskeder, enhed, bruger, domæne, ip, fil, avanceret jagt, forespørgsel
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: c26bc9762b76deff0dddb04f98e2630e789ee6b5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474459"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Opret en app for at få adgang Microsoft Defender for Endpoint uden en bruger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Denne side beskriver, hvordan du opretter et program for at få programadgang til Defender for Endpoint uden en bruger. Hvis du har brug for programmeringsadgang til Defender for Endpoint på vegne af en bruger, skal du [se Få adgang med brugerkontekst](exposed-apis-create-app-nativeapp.md). Hvis du ikke er sikker på, hvilken adgang du skal bruge, kan du [se Introduktion](apis-intro.md).

Microsoft Defender for Endpoint blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere work flows og udvikle baseret på Defender for Endpoint-egenskaber. API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge API'er:
- Opret et Azure Active Directory (Azure AD).
- Få et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang til Defender for Endpoint API.

Denne artikel forklarer, hvordan du opretter et Azure AD-program, får et adgangstoken Microsoft Defender for Endpoint og validerer tokenet.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure med](https://portal.azure.com) en bruger, der har **rollen som global** administrator.

2. Gå til **Azure Active Directory** \> **appregistreringer** \> **Ny registrering**. 

    :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Programregistreringsruden" lightbox="images/atp-azure-new-app2.png":::

3. I registreringsformularen skal du vælge et navn til dit program og derefter vælge **Registrer**.

4. Hvis du vil aktivere din app til at få adgang til Defender for Endpoint og tildele tilladelsen "Læs alle vigtige beskeder **"**, skal du på din programside vælge **API-tilladelser** \>  \> Tilføj tilladelse API'er, som min organisation **bruger >,** skriv **WindowsDefenderATP**, og vælg **derefter WindowsDefenderATP**.

   > [!NOTE]
   > *WindowsDefenderATP* vises ikke på den oprindelige liste. Begynd at skrive navnet i tekstfeltet for at se det.

   :::image type="content" source="images/add-permission.png" alt-text="Ruden API-tilladelser" lightbox="images/add-permission.png":::

   Vælg **Programtilladelser** **Alert.Read.All**\>, og vælg **derefter Tilføj tilladelser**.

   :::image type="content" source="images/application-permissions.png" alt-text="Ruden med oplysninger om programtilladelser" lightbox="images/application-permissions.png":::

     Du skal vælge de relevante tilladelser. "Læs alle beskeder" er kun et eksempel. Eksempel:

     - Hvis [du vil køre avancerede forespørgsler](run-advanced-query-api.md), skal du vælge tilladelsen "Kør avancerede forespørgsler".
     - Hvis [du vil isolere en enhed](isolate-machine.md), skal du vælge tilladelsen "Isoler maskine".
     - Se afsnittet Tilladelser i den API, du er interesseret  i at ringe til, for at finde ud af, hvilken tilladelse du skal bruge.

5. Vælg **Giv samtykke**.

     > [!NOTE]
     > Hver gang du tilføjer en tilladelse, skal du vælge **Giv samtykke,** før den nye tilladelse træder i kraft.

    :::image type="content" source="images/grant-consent.png" alt-text="Siden til tildeling af tilladelser" lightbox="images/grant-consent.png":::

6. Hvis du vil føje en hemmelighed til programmet, **skal du vælge Certifikater & hemmeligheder**, føje en beskrivelse til hemmeligheden og derefter vælge **Tilføj**.

    > [!NOTE]
    > Når du har valgt **Tilføj**, skal du **vælge Kopiér den genererede hemmelige værdi**. Du kan ikke hente denne værdi, når du har forladet.

      :::image type="content" source="images/webapp-create-key2.png" alt-text="Indstillingen Opret program" lightbox="images/webapp-create-key2.png":::

7. Skriv dit program-id og dit lejer-id ned. På programsiden skal du gå til **Oversigt** og kopiere følgende.

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="De oprettede app- og lejer-oplysninger" lightbox="images/app-and-tenant-ids.png":::

8. **Kun Microsoft Defender for Endpoint for Partnere**. Indstil din app til at være flerlejet (tilgængelig i alle lejere efter samtykke). Dette er **påkrævet** for tredjepartsapps (f.eks. hvis du opretter en app, der er beregnet til at køre i flere kunders lejer). Dette er **ikke** påkrævet, hvis du opretter en tjeneste, som du kun vil køre i din lejer (f.eks. hvis du opretter et program til dit eget brug, der kun interagerer med dine egne data). Sådan indstiller du din app til at være flerlejet:

    - Gå til **Godkendelse**, og tilføj `https://portal.azure.com` som **Redirect URI**.

    - Nederst på siden under Understøttede **kontotyper** skal du vælge Konti i et hvilket som helst **organisationsmappeprograms** samtykke for din app med flere lejere.

    Du skal have din ansøgning godkendt i hver lejer, hvor du regner med at bruge den. Dette skyldes, at dit program interagerer med Defender for Endpoint på vegne af din kunde.

    Du (eller din kunde, hvis du skriver en app fra tredjepart) skal vælge linket til samtykke og godkende din app. Samtykket skal udføres med en bruger, der har administratorrettigheder i Active Directory.

    Samtykkelinket dannes på følgende måde: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Hvor 00000000-0000-0000-0000-0000000000000 erstattes med dit program-id.


**Udført!** Du har registreret et program! Se nedenstående eksempler for at få adgang til token og validering.

## <a name="get-an-access-token"></a>Få et adgangstoken

Du kan finde flere oplysninger om Azure AD-tokens i [Azure AD-selvstudiet](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="use-powershell"></a>Brug PowerShell

```powershell
# This script acquires the App Context Token and stores it in the variable $token for later use in the script.
# Paste your Tenant ID, App ID, and App Secret (App key) into the indicated quotes below.

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application key here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token
```

### <a name="use-c"></a>Brug C#:

Følgende kode blev testet med NuGet Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. Opret et nyt konsolprogram.
1. Installér NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Tilføj følgende:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Kopiér og indsæt følgende kode i din app (husk at opdatere de tre variabler: ```tenantId, appId, appSecret```):

    ```csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 

    const string authority = "https://login.microsoftonline.com";
    const string wdatpResourceId = "https://api.securitycenter.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```


### <a name="use-python"></a>Brug Python

Se [Få token ved hjælp af Python](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>Brug krølle

> [!NOTE]
> Følgende procedure forudsætter, at krøllet for Windows allerede er installeret på computeren.

1. Åbn en kommandoprompt, og angiv CLIENT_ID dit Azure-program-id.
1. Indstil CLIENT_SECRET til din Azure-programhemmelighed.
1. Angiv TENANT_ID Azure-lejer-id'et for den kunde, der vil bruge din app til at få adgang til Defender til slutpunktet.
1. Kør følgende kommando:

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    Du får et svar i følgende formular:
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>Valider tokenet

Sørg for, at du har fået det rigtige token:

1. Kopiér og indsæt det token, du fik i det forrige trin [, i JWT](https://jwt.ms) for at afkode den.

1. Valider, at du får et "roller"-krav med de ønskede tilladelser.

   På følgende billede kan du se et afkodet token, der er købt fra en app med tilladelser til Microsoft Defender for Endpoint rolle:

   :::image type="content" source="images/webapp-decoded-token.png" alt-text="Tokenoplysningersdelen" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

1. Vælg den API, du vil bruge. Du kan få mere at vide under [Understøttede Defender til endpoint-API'er](exposed-apis-list.md).
1. Angiv godkendelseshovedet i den http-anmodning, du sender til "Bearer {token}" (Bearer er godkendelsesskemaet).
1. Udløbsdatoen for tokenet er en time. Du kan sende mere end én anmodning med samme token.

Følgende er et eksempel på afsendelse af en anmodning om at få en liste over beskeder **ved hjælp af C#**:

```csharp
var httpClient = new HttpClient();

var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

// Do something useful with the response
```

## <a name="see-also"></a>Se også
- [Understøttede Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- [Access Microsoft Defender for Endpoint på vegne af en bruger](exposed-apis-create-app-nativeapp.md)
