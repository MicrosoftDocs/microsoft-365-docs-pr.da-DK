---
title: Partneradgang via Microsoft 365 Defender API'er
description: Få mere at vide om, hvordan du opretter en app for at få programmatisk adgang til Microsoft 365 Defender på vegne af dine brugere.
keywords: partner, adgang, API, multilejer, samtykke, adgangstoken, app
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 43bb018abe6a19464d7e52493ed1b4ccd1f15140
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102410"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>Opret en app med partneradgang til Microsoft 365 Defender API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

På denne side beskrives det, hvordan du opretter en Azure Active Directory app, der har programmatisk adgang til Microsoft 365 Defender på vegne af brugere på tværs af flere lejere. Apps med flere lejere er nyttige til at betjene store grupper af brugere.

Hvis du har brug for programmatisk adgang til Microsoft 365 Defender på vegne af en enkelt bruger, skal du se [Opret en app for at få adgang til Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md). Hvis du har brug for adgang, uden at en bruger eksplicit er defineret (f.eks. hvis du skriver en baggrundsapp eller en daemon), skal du se [Opret en app for at få adgang til Microsoft 365 Defender uden en bruger](api-create-app-web.md). Hvis du ikke er sikker på, hvilken type adgang du har brug for, skal du se [Kom i gang](api-access.md).

Microsoft 365 Defender fremviser mange af sine data og handlinger via et sæt programmatiske API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre brug af Microsoft 365 Defender funktioner. Denne API-adgang kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du gøre følgende for at bruge disse API'er:

- Opret et Azure Active Directory (Azure AD)-program.
- Hent et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang til Microsoft 365 Defender API.

Da denne app er flerlejer, skal du også have [administratorsamtykke](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) fra hver lejer på vegne af brugerne.

I denne artikel forklares det, hvordan du:

- Opret et Azure AD program med **flere lejere**
- Få godkendt samtykke fra din brugeradministrator til, at dit program kan få adgang til de Microsoft 365 Defender, som det har brug for.
- Hent et adgangstoken til Microsoft 365 Defender
- Valider tokenet

Microsoft 365 Defender fremviser mange af sine data og handlinger via et sæt programmatiske API'er. Disse API'er hjælper dig med at automatisere arbejdsflows og skabe innovation baseret på Microsoft 365 Defender funktioner. API-adgangen kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du gøre følgende for at bruge API'erne:

- Opret et Azure AD program med **flere lejere**.
- Få godkendt (samtykke) af din brugeradministrator, så dit program kan få adgang til Microsoft 365 Defender ressourcer, det har brug for.
- Hent et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang til Microsoft 365 Defender API.

Følgende trin med vejledning i, hvordan du opretter et Azure AD program med flere lejere, får et adgangstoken til Microsoft 365 Defender og validerer tokenet.

## <a name="create-the-multi-tenant-app"></a>Opret appen med flere lejere

1. Log på [Azure](https://portal.azure.com) som bruger med rollen **Global administrator** .

2. Gå til **Azure Active Directory** >  **Appregistreringer** > **Ny registrering**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Et programs registreringssektion på Microsoft 365 Defender-portalen" lightbox="../../media/atp-azure-new-app2.png":::

3. I registreringsformularen:

   - Vælg et navn til programmet.
   - Fra **Understøttede kontotyper** skal du vælge **Konti i en hvilken som helst organisationsmappe (Enhver Azure AD mappe) – Multitenant**.
   - Udfyld afsnittet **omdirigerings-URI** . Vælg skriv **Web** , og giv omdirigerings-URI'en som **https://portal.azure.com**.

   Når du er færdig med at udfylde formularen, skal du vælge **Registrer**.

   :::image type="content" source="../..//media/atp-api-new-app-partner.png" alt-text="Et programs registreringssektioner på portalen Microsoft 365 Defender" lightbox="../..//media/atp-api-new-app-partner.png":::

4. På din programside skal du vælge **API-tilladelser** > **Tilføj****tilladelseS-API'er** > , som min organisation bruger >, skrive **Microsoft Threat Protection** og vælge **Microsoft Threat Protection**. Din app kan nu få adgang til Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* er et tidligere navn på Microsoft 365 Defender og vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at se det blive vist.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Afsnittet brug af API'er på Microsoft 365 Defender-portalen" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Vælg **Programtilladelser**. Vælg de relevante tilladelser til dit scenarie (f.eks **. Incident.Read.All**), og vælg derefter **Tilføj tilladelser**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Et programs tilladelsesrude på Microsoft 365 Defender-portalen" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Du skal vælge de relevante tilladelser til dit scenarie. *Læs alle hændelser* er blot et eksempel. Hvis du vil finde ud af, hvilken tilladelse du har brug for, skal du se afsnittet **Tilladelser** i den API, du vil kalde.
    >
    > Hvis du f.eks. vil [køre avancerede forespørgsler](api-advanced-hunting.md), skal du vælge tilladelsen 'Kør avancerede forespørgsler'. Hvis du vil [isolere en enhed](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), skal du vælge tilladelsen "Isoler computer".

6. Vælg **Giv administratorsamtykke**. Hver gang du tilføjer en tilladelse, skal du vælge **Giv administratorsamtykke** , for at den kan træde i kraft.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Et afsnit, hvor du kan give administratorsamtykke på Microsoft 365 Defender-portalen" lightbox="../../media/grant-consent.PNG":::

7. Hvis du vil føje en hemmelighed til programmet, skal du vælge **Certifikater & hemmeligheder**, føje en beskrivelse til hemmeligheden og derefter vælge **Tilføj**.

    > [!TIP]
    > Når du har valgt **Tilføj**, skal du vælge **kopiér den genererede værdi for hemmelighed**. Du kan ikke hente værdien for hemmeligheden, når du er gået.

      :::image type="content" source="../../media/webapp-create-key2.png" alt-text="Afsnittet Tilføjelse af hemmelighed på Microsoft 365 Defender-portalen" lightbox="../../media/webapp-create-key2.png":::

8. Registrer dit program-id og dit lejer-id et sikkert sted. De vises under **Oversigt** på din programside.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Ruden Oversigt på Microsoft 365 Defender-portalen" lightbox="../../media/app-and-tenant-ids.png":::

9. Føj programmet til din brugers lejer.

   Da dit program interagerer med Microsoft 365 Defender på vegne af dine brugere, skal det godkendes for hver lejer, du vil bruge det på.

   En **global administrator** fra din brugers lejer skal se samtykkelinket og godkende dit program.

   Samtykkelinket er af formularen:

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Cifrene `00000000-0000-0000-0000-000000000000` skal erstattes med dit program-id.

   Når du har klikket på samtykkelinket, skal du logge på med den globale administrator af brugerens lejer og acceptere programmet.

   :::image type="content" source="../../media/app-consent-partner.png" alt-text="Siden med samtykkeprogrammet på portalen Microsoft 365 Defender" lightbox="../../media/app-consent-partner.png":::

   Du skal også bede din bruger om deres lejer-id. Lejer-id'et er et af de identifikatorer, der bruges til at hente adgangstokens.

- **Gjort!** Du har registreret et program!
- Se eksempler nedenfor for at få oplysninger om tokenanskaffelse og -validering.

## <a name="get-an-access-token"></a>Hent et adgangstoken

Du kan få flere oplysninger om Azure AD tokens i [selvstudiet Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Selvom eksemplerne i dette afsnit opfordrer dig til at indsætte hemmelige værdier til testformål, bør du **aldrig hardcode hemmeligheder** i et program, der kører i produktion. En tredjepart kan bruge din hemmelighed til at få adgang til ressourcer. Du kan hjælpe med at beskytte din apps hemmeligheder ved hjælp af [Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Hvis du vil have et praktisk eksempel på, hvordan du kan beskytte din app, skal du se [Administrer hemmeligheder i dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

> [!TIP]
> I følgende eksempler skal du bruge en brugers lejer-id til at teste, om scriptet fungerer.

### <a name="get-an-access-token-using-powershell"></a>Hent et adgangstoken ved hjælp af PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place!

$resourceAppIdUri = 'https://api.security.microsoft.com'
$oAuthUri = "https://login.windows.net/$tenantId/oauth2/token"

$authBody = [Ordered] @{
    resource = $resourceAppIdUri
    client_id = $clientId
    client_secret = $appSecret
    grant_type = 'client_credentials'
}

$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token

Out-File -FilePath "./Latest-token.txt" -InputObject $token

return $token
```

### <a name="get-an-access-token-using-c"></a>Hent et adgangstoken ved hjælp af C\#

> [!NOTE]
> Følgende kode blev testet med Nuget Microsoft.Identity.Client 3.19.8.

> [!IMPORTANT]
> [NuGet-pakken Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) og ADAL (Azure AD Authentication Library) frarådes. Der er ikke tilføjet nye funktioner siden den 30. juni 2020.   Vi opfordrer dig på det kraftigste til at opgradere, se [migreringsvejledningen](/azure/active-directory/develop/msal-migration) for at få flere oplysninger.

1. Opret et nyt konsolprogram.
1. Installér NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/).
1. Tilføj følgende linje:

    ```C#
    using Microsoft.Identity.Client;
    ```

1. Kopiér og indsæt følgende kode i din app (glem ikke at opdatere de tre variabler: `tenantId`, `clientId`, `appSecret`):

    ```C#
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

### <a name="get-an-access-token-using-python"></a>Hent et adgangstoken ved hjælp af Python

```Python
import json
import urllib.request
import urllib.parse

tenantId = '' # Paste your directory (tenant) ID here
clientId = '' # Paste your application (client) ID here
appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

url = "https://login.windows.net/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.security.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : clientId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

### <a name="get-an-access-token-using-curl"></a>Få et adgangstoken ved hjælp af krøller

> [!NOTE]
> Curl er forudinstalleret på Windows 10, version 1803 og nyere. For andre versioner af Windows, downloade og installere værktøjet direkte fra den [officielle curl hjemmeside](https://curl.haxx.se/windows/).

1. Åbn en kommandoprompt, og angiv CLIENT_ID til dit Azure-program-id.
1. Angiv CLIENT_SECRET til din Azure-programhemmelighed.
1. Angiv TENANT_ID til Azure-lejer-id'et for den bruger, der vil bruge din app til at få adgang til Microsoft 365 Defender.
1. Kør følgende kommando:

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Et vellykket svar vil se sådan ud:

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider tokenet

1. Kopiér og indsæt tokenet på [JSON-webtokenets validatorwebsted, JWT,](https://jwt.ms) for at afkode det.
1. Sørg for, at *rollekravet* i det afkodede token indeholder de ønskede tilladelser.

På følgende billede kan du se et afkodet token, der er hentet fra en app, med ```Incidents.Read.All```tilladelserne , ```Incidents.ReadWrite.All```og ```AdvancedHunting.Read.All``` :

:::image type="content" source="../../media/webapp-decoded-token.png" alt-text="Ruden Afkodet token på Microsoft 365 Defender-portalen" lightbox="../../media/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Brug tokenet til at få adgang til api'en til Microsoft 365 Defender

1. Vælg den API, du vil bruge (hændelser eller avanceret jagt). Du kan få flere oplysninger under [Understøttede Microsoft 365 Defender API'er](api-supported.md).
2. I den http-anmodning, du er ved at sende, skal du angive godkendelsesheaderen til `"Bearer" <token>`, *Ihændehaver* er godkendelsesskemaet, og *tokenet* er dit validerede token.
3. Tokenet udløber inden for en time. Du kan sende mere end én anmodning i denne periode med det samme token.

I følgende eksempel kan du se, hvordan du sender en anmodning for at få en liste over hændelser **ved hjælp af C#**.

```C#
   var httpClient = new HttpClient();
   var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

   request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

   var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over API'er Microsoft 365 Defender](api-overview.md)
- [Få adgang til de Microsoft 365 Defender API'er](api-access.md)
- [Opret et "Hello world"-program](api-hello-world.md)
- [Opret en app for at få adgang til Microsoft 365 Defender uden en bruger](api-create-app-web.md)
- [Opret en app for at få adgang til Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md)
- [Få mere at vide om API-grænser og -licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Administrer hemmeligheder i dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [OAuth 2.0-godkendelse til brugerlogon og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
