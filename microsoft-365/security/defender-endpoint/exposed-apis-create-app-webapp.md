---
title: Opret en app for at få adgang til Microsoft Defender for Endpoint uden en bruger
ms.reviewer: ''
description: Få mere at vide om, hvordan du designer en webapp for at få programmatisk adgang til Microsoft Defender for Endpoint uden en bruger.
keywords: apis, graf-API, understøttede API'er, agent, beskeder, enhed, bruger, domæne, ip, fil, avanceret jagt, forespørgsel
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
ms.openlocfilehash: 4a0387eac18152599cfd08ba75893f3eae248431
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102608"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>Opret en app for at få adgang til Microsoft Defender for Endpoint uden en bruger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> Avancerede jagtegenskaber er ikke inkluderet i Defender for Business. Se [Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

På denne side beskrives det, hvordan du opretter et program for at få programmatisk adgang til Defender for Endpoint uden en bruger. Hvis du har brug for programmatisk adgang til Defender for Endpoint på vegne af en bruger, skal du se [Få adgang med brugerkontekst](exposed-apis-create-app-nativeapp.md). Hvis du ikke er sikker på, hvilken adgang du har brug for, skal du se [Kom i gang](apis-intro.md).

Microsoft Defender for Endpoint fremviser mange af dataene og handlingerne via et sæt programmatiske API'er. Disse API'er hjælper dig med at automatisere arbejdsflow og skabe innovation baseret på funktionerne i Defender for Endpoint. API-adgangen kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du gøre følgende for at bruge API'erne:
- Opret et Azure Active Directory (Azure AD)-program.
- Hent et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang til Defender for Endpoint API.

I denne artikel forklares det, hvordan du opretter et Azure AD program, henter et adgangstoken til Microsoft Defender for Endpoint og validerer tokenet.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure](https://portal.azure.com) med en bruger, der har rollen **Global administrator** .

2. Gå til **Azure Active Directory** \> **Appregistreringer** \> **Ny registrering**. 

    :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Ruden Programregistrering" lightbox="images/atp-azure-new-app2.png":::

3. Vælg et navn til din ansøgning i registreringsformularen, og vælg derefter **Registrer**.

4. Hvis du vil give din app adgang til Defender for Endpoint og tildele den tilladelsen **"Læs alle beskeder"** , skal du vælge **API-tilladelser** \> **Tilføj tilladelse** \> **API'er, som min organisation bruger** >, skrive **WindowsDefenderATP** og derefter vælge **WindowsDefenderATP**.

   > [!NOTE]
   > *WindowsDefenderATP* vises ikke på den oprindelige liste. Begynd at skrive navnet i tekstfeltet for at se det blive vist.

   :::image type="content" source="images/add-permission.png" alt-text="Ruden API-tilladelser" lightbox="images/add-permission.png":::

   Vælg **Programtilladelser** \> **Alert.Read.All**, og vælg derefter **Tilføj tilladelser**.

   :::image type="content" source="images/application-permissions.png" alt-text="Ruden med oplysninger om programtilladelser" lightbox="images/application-permissions.png":::

     Du skal vælge de relevante tilladelser. 'Læs alle beskeder' er kun et eksempel. Eksempel:

     - Hvis du vil [køre avancerede forespørgsler](run-advanced-query-api.md), skal du vælge tilladelsen 'Kør avancerede forespørgsler'.
     - Hvis du vil [isolere en enhed](isolate-machine.md), skal du vælge tilladelsen "Isoler computer".
     - Hvis du vil finde ud af, hvilken tilladelse du har brug for, skal du se afsnittet **Tilladelser** i den API, du er interesseret i at kalde.

5. Vælg **Giv samtykke**.

     > [!NOTE]
     > Hver gang du tilføjer en tilladelse, skal du vælge **Giv samtykke** , for at den nye tilladelse træder i kraft.

    :::image type="content" source="images/grant-consent.png" alt-text="Siden Tildel tilladelser" lightbox="images/grant-consent.png":::

6. Hvis du vil føje en hemmelighed til programmet, skal du vælge **Certifikater & hemmeligheder**, føje en beskrivelse til hemmeligheden og derefter vælge **Tilføj**.

    > [!NOTE]
    > Når du har valgt **Tilføj**, skal du vælge **kopiér den genererede værdi for hemmelighed**. Du kan ikke hente denne værdi, når du er gået.

      :::image type="content" source="images/webapp-create-key2.png" alt-text="Indstillingen Opret program" lightbox="images/webapp-create-key2.png":::

7. Skriv dit program-id og dit lejer-id ned. Gå til **Oversigt** på din programside, og kopiér følgende.

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="De oprettede app- og lejer-id'er" lightbox="images/app-and-tenant-ids.png":::

8. **Kun for Microsoft Defender for Endpoint partnere**. Angiv, at din app skal have flere lejere (tilgængelig i alle lejere efter samtykke). Dette er **påkrævet** for tredjepartsapps (hvis du f.eks. opretter en app, der er beregnet til at køre i flere kunders lejer). Dette er **ikke påkrævet** , hvis du opretter en tjeneste, som du kun vil køre i din lejer (hvis du f.eks. opretter et program til dit eget forbrug, der kun interagerer med dine egne data). Sådan angiver du, at din app skal have flere lejere:

    - Gå til **Godkendelse**, og tilføj `https://portal.azure.com` som **omdirigerings-URI'en**.

    - Nederst på siden under **Understøttede kontotyper** skal du vælge **Konti i alle organisationsmappeprogrammers** samtykke til din app med flere lejere.

    Du skal have dit program godkendt i hver lejer, hvor du vil bruge det. Det skyldes, at dit program interagerer med Defender for Endpoint på vegne af din kunde.

    Du (eller din kunde, hvis du skriver en tredjepartsapp), skal vælge samtykkelinket og godkende din app. Samtykket skal udføres med en bruger, der har administrative rettigheder i Active Directory.

    Samtykkelinket er udformet på følgende måde: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    Hvor 00000000-0000-0000-0000-00000000000 erstattes med dit program-id.


**Gjort!** Du har registreret et program! Se eksempler nedenfor for at få oplysninger om tokenanskaffelse og -validering.

## <a name="get-an-access-token"></a>Hent et adgangstoken

Du kan få flere oplysninger om Azure AD tokens i [selvstudiet Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

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
$token
```

### <a name="use-c"></a>Brug C#:

Følgende kode blev testet med NuGet Microsoft.Identity.Client 3.19.8.

> [!IMPORTANT]
> [NuGet-pakken Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) og ADAL (Azure AD Authentication Library) frarådes. Der er ikke tilføjet nye funktioner siden den 30. juni 2020.   Vi opfordrer dig på det kraftigste til at opgradere, se [migreringsvejledningen](/azure/active-directory/develop/msal-migration) for at få flere oplysninger.

1. Opret et nyt konsolprogram.
1. Installér NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/).
1. Tilføj følgende:

    ```csharp
    using Microsoft.Identity.Client;
    ```

1. Kopiér og indsæt følgende kode i din app (glem ikke at opdatere de tre variabler: ```tenantId, appId, appSecret```):

    ```csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 
    const string authority = https://login.microsoftonline.com;
    const string audience = https://api.securitycenter.microsoft.com;

    IConfidentialClientApplication myApp = ConfidentialClientApplicationBuilder.Create(appId).WithClientSecret(appSecret).WithAuthority($"{authority}/{tenantId}").Build();

    List<string> scopes = new List<string>() { $"{audience}/.default" };

    AuthenticationResult authResult = myApp.AcquireTokenForClient(scopes).ExecuteAsync().GetAwaiter().GetResult();

    string token = authResult.AccessToken;
    ```
### <a name="use-python"></a>Brug Python

Se [Hent token ved hjælp af Python](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>Brug krøllede

> [!NOTE]
> I følgende procedure antages det, at Curl til Windows allerede er installeret på computeren.

1. Åbn en kommandoprompt, og angiv CLIENT_ID til dit Azure-program-id.
1. Angiv CLIENT_SECRET til din Azure-programhemmelighed.
1. Angiv TENANT_ID til Azure-lejer-id'et for den kunde, der vil bruge din app til at få adgang til Defender for Endpoint.
1. Kør følgende kommando:

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    Du får et svar i følgende form:
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>Valider tokenet

Sørg for, at du har det korrekte token:

1. Kopiér og indsæt det token, du fik i det forrige trin, i [JWT](https://jwt.ms) for at afkode det.

1. Valider, at du får et krav om "roller" med de ønskede tilladelser.

   På følgende billede kan du se et afkodet token, der er hentet fra en app med tilladelser til alle Microsoft Defender for Endpoint roller:

   :::image type="content" source="images/webapp-decoded-token.png" alt-text="Detaljedelen for tokenet" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

1. Vælg den API, du vil bruge. Du kan finde flere oplysninger under [Understøttet Defender for Endpoint-API'er](exposed-apis-list.md).
1. Angiv godkendelsesheaderen i den http-anmodning, du sender til "Ihændehaver {token}" (Ihændehaver er godkendelsesskemaet).
1. Tokenets udløbstid er én time. Du kan sende mere end én anmodning med det samme token.

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
- [Adgang Microsoft Defender for Endpoint på vegne af en bruger](exposed-apis-create-app-nativeapp.md)
