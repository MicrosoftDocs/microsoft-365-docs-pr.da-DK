---
title: Partneradgang via Microsoft Defender for Endpoint API'er
ms.reviewer: ''
description: Få mere at vide om, hvordan du designer en webapp for at få programmatisk adgang til Microsoft Defender for Endpoint på vegne af dine brugere.
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
ms.openlocfilehash: 7ca212cf6cdacdaf374dbe65f4fd88c74712bb34
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66101817"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Partneradgang via Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> Avancerede jagtegenskaber er ikke inkluderet i Defender for Business. Se [Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

På denne side beskrives det, hvordan du opretter et Azure Active Directory (Azure AD)-program for at få programmatisk adgang til Microsoft Defender for Endpoint på vegne af dine kunder.

Microsoft Defender for Endpoint fremviser mange af dataene og handlingerne via et sæt programmatiske API'er. Disse API'er hjælper dig med at automatisere arbejdsflows og skabe innovation baseret på Microsoft Defender for Endpoint funktioner. API-adgangen kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du gøre følgende for at bruge API'erne:

- Opret et Azure AD program med **flere lejere**.
- Få godkendt(samtykke) af din kundeadministrator, så dit program kan få adgang til Defender for Endpoint-ressourcer, det har brug for.
- Hent et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang til Microsoft Defender for Endpoint API.

Følgende trin hjælper dig med at oprette et Azure AD program, hente et adgangstoken til Microsoft Defender for Endpoint og validere tokenet.

## <a name="create-the-multi-tenant-app"></a>Opret appen med flere lejere

1. Log på din [Azure-lejer](https://portal.azure.com) med en bruger, der har rollen **Global administrator** .

2. Gå til **Azure Active Directory** \> **Appregistreringer** \> **Ny registrering**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Navigationsruden til programregistreringsruden" lightbox="images/atp-azure-new-app2.png":::

3. I registreringsformularen:

   - Vælg et navn til programmet.

   - Understøttede kontotyper – konti i en hvilken som helst organisationsmappe.

   - Omdirigerings-URI – type: Web, URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="Siden Microsoft Azure partnerprogramregistrering" lightbox="images/atp-api-new-app-partner.png":::

4. Tillad, at dit program får adgang til Microsoft Defender for Endpoint, og tildel det med det minimale sæt tilladelser, der kræves for at fuldføre integrationen.

   - På din programside skal du vælge **API-tilladelser** \> **Tilføj** **tilladelseS-API'er**\>, som min organisation bruger, > skrive **WindowsDefenderATP** og vælge **På WindowsDefenderATP**.

   - **Bemærk**! *WindowsDefenderATP* vises ikke på den oprindelige liste. Begynd at skrive navnet i tekstfeltet for at se det blive vist.

     :::image type="content" source="images/add-permission.png" alt-text="Indstillingen Tilføj en tilladelse" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>Anmod om API-tilladelser

Hvis du vil finde ud af, hvilken tilladelse du har brug for, skal du gennemse afsnittet **Tilladelser** i den API, du er interesseret i at kalde. For eksempel:

- Hvis du vil [køre avancerede forespørgsler](run-advanced-query-api.md), skal du vælge tilladelsen 'Kør avancerede forespørgsler'
- Hvis du vil [isolere en enhed](isolate-machine.md), skal du vælge tilladelsen "Isoler computer"

I følgende eksempel bruger vi tilladelsen **"Læs alle beskeder"** :

1. Vælg **Programtilladelser** \> **Alert.Read.All** > vælg **Tilføj tilladelser**

   :::image type="content" source="images/application-permissions.png" alt-text="Den indstilling, der gør det muligt at tilføje en tilladelse" lightbox="images/application-permissions.png":::

2. Vælg **Tildel samtykke**

   - **Bemærk**! Hver gang du tilføjer tilladelse, skal du vælge **Giv samtykke** , for at den nye tilladelse træder i kraft.

   :::image type="content" source="images/grant-consent.png" alt-text="Den mulighed, der tillader, at der gives samtykke" lightbox="images/grant-consent.png":::

3. Føj en hemmelighed til programmet.

   - Vælg **Certifikater & hemmeligheder**, føj en beskrivelse til hemmeligheden, og vælg **Tilføj**.

    **Vigtigt**! Når du har klikket på Tilføj, **skal du kopiere den genererede værdi for hemmeligheden**. Du vil ikke være i stand til at hente efter du forlader!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Opret app-nøglen" lightbox="images/webapp-create-key2.png":::

4. Skriv dit program-id ned:

   - Gå til **Oversigt** på din programside, og kopiér følgende oplysninger:

     :::image type="content" source="images/app-id.png" alt-text="Id'et for oprettelsesprogrammet" lightbox="images/app-id.png":::

5. Føj programmet til din kundes lejer.

   Du skal have din ansøgning godkendt i hver kundelejer, hvor du vil bruge den. Det skyldes, at dit program interagerer med Microsoft Defender for Endpoint program på vegne af din kunde.

   En bruger med **global administrator** fra din kundes lejer skal vælge samtykkelinket og godkende dit program.

   Samtykkelinket er af formularen:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Hvor 00000000-0000-0000-0000-00000000000 skal erstattes med dit program-id

   Når du har klikket på samtykkelinket, skal du logge på med den globale administrator af kundens lejer og acceptere programmet.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Knappen Acceptér" lightbox="images/app-consent-partner.png":::

   Derudover skal du bede din kunde om deres lejer-id og gemme det til fremtidig brug, når du henter tokenet.

6. **Gjort!** Du har registreret et program! Se eksempler nedenfor for at få oplysninger om tokenanskaffelse og -validering.

## <a name="get-an-access-token-example"></a>Få et eksempel på et adgangstoken

**Bemærk:** Hvis du vil hente adgangstoken på vegne af din kunde, skal du bruge kundens lejer-id på følgende tokenkøb.

Du kan få flere oplysninger om AAD-token i [AAD-selvstudium](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-powershell"></a>Brug af PowerShell

```powershell
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

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
Out-File -FilePath "./Latest-token.txt" -InputObject $token
return $token
```

### <a name="using-c"></a>Brug af C #

> Nedenstående kode blev testet med Nuget Microsoft.Identity.Client

> [!IMPORTANT]
> [NuGet-pakken Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) og ADAL (Azure AD Authentication Library) frarådes. Der er ikke tilføjet nye funktioner siden den 30. juni 2020. Vi opfordrer dig på det kraftigste til at opgradere, se [migreringsvejledningen](/azure/active-directory/develop/msal-migration) for at få flere oplysninger.

- Opret et nyt konsolprogram
- Installér NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/)
- Tilføj nedenstående ved hjælp af

    ```console
    using Microsoft.Identity.Client;
    ```

- Kopiér/indsæt nedenstående kode i dit program (glem ikke at opdatere de tre variabler: `tenantId`, `appId`og `appSecret`)

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

### <a name="using-python"></a>Brug af Python

Se [Hent token ved hjælp af Python](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>Brug af krøller

> [!NOTE]
> Nedenstående procedure formodes Curl for Windows er allerede installeret på din computer

- Åbn et kommandovindue
- Angiv CLIENT_ID til dit Azure-program-id
- Angiv CLIENT_SECRET til din Azure-programhemmelighed
- Angiv TENANT_ID til Azure-lejer-id'et for den kunde, der vil bruge dit program til at få adgang til Microsoft Defender for Endpoint program
- Kør nedenstående kommando:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Du får svar på formularen:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider tokenet

Tilregnelighedskontrol for at sikre, at du har et korrekt token:

- Kopiér/indsæt i [JWT](https://jwt.ms) det token, du får i det forrige trin, for at afkode det
- Valider, at du får et krav om "roller" med de ønskede tilladelser
- På skærmbilledet nedenfor kan du se et afkodet token, der er hentet fra et program med flere tilladelser til at Microsoft Defender for Endpoint:
- Kravet "tid" er det lejer-id, som tokenet tilhører.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Siden til validering af token" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

- Vælg den API, du vil bruge. Du kan få flere oplysninger under [Understøttede Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- Angiv godkendelsesheaderen i den Http-anmodning, du sender til "Ihændehaver {token}" (ihændehaver er autorisationsskemaet)
- Tokenets udløbstid er 1 time (du kan sende mere end én anmodning med det samme token)

- Eksempel på afsendelse af en anmodning om at få en liste over beskeder **ved hjælp af C#**

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
