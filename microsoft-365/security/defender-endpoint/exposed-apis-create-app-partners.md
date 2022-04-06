---
title: Oprette et program til at få adgang Microsoft Defender for Endpoint uden en bruger
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
ms.openlocfilehash: 454d385c66a0019ba6059a2b8038907dd630b443
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469861"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>Partneradgang via Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:** 
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Denne side beskriver, hvordan du opretter et Azure Active Directory (Azure AD)-program for at få programadgang til Microsoft Defender for Endpoint på vegne af dine kunder.

Microsoft Defender for Endpoint blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere pengestrømme og forny baseret på Microsoft Defender for Endpoint funktioner. API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge API'er:

- Opret et **Azure AD-program med** flere lejere.
- Få tilladelse(samtykke) af din kundeadministrator til at få adgang til Defender for de slutpunktsressourcer, der er brug for.
- Få et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang Microsoft Defender for Endpoint API.

Følgende trin hjælper dig med at oprette et Azure AD-program, få et adgangstoken til at Microsoft Defender for Endpoint og validere tokenet.

## <a name="create-the-multi-tenant-app"></a>Opret appen med flere lejere

1. Log på din [Azure-lejer med](https://portal.azure.com) en bruger, der **har rollen som global** administrator.

2. Gå til **Azure Active Directory** \> **appregistreringer** \> **Ny registrering**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Navigation til programregistreringsruden" lightbox="images/atp-azure-new-app2.png":::

3. I registreringsformularen:

   - Vælg et navn til dit program.

   - Understøttede kontotyper – konti i ethvert organisationskatalog.

   - Omdiriger URI – type: Web, URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="Tilmeldingssiden Microsoft Azure partnerprogrammet" lightbox="images/atp-api-new-app-partner.png":::

4. Giv dit program adgang til Microsoft Defender for Endpoint og tildele det med det minimale sæt tilladelser, der kræves for at fuldføre integrationen.

   - På programsiden skal  du vælge **API-tilladelser** Tilføj **tilladelses-API'er** \> \>, som min organisation bruger > type **WindowsDefenderATP** og vælge **på WindowsDefenderATP**.

   - **Bemærk**! *WindowsDefenderATP* vises ikke på den oprindelige liste. Begynd at skrive navnet i tekstfeltet for at se det.

     :::image type="content" source="images/add-permission.png" alt-text="Indstillingen Tilføj en tilladelse" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>Anmod om API-tilladelser

Se afsnittet Tilladelser i den API, du er  interesseret i at ringe til, for at finde ud af, hvilken tilladelse du skal bruge. For eksempel:

- Hvis [du vil køre avancerede forespørgsler](run-advanced-query-api.md), skal du vælge tilladelsen "Kør avancerede forespørgsler"
- Hvis du [vil isolere en enhed](isolate-machine.md), skal du vælge "Isoler maskine"-tilladelse

I følgende eksempel bruger vi tilladelsen **"Læs alle vigtige** beskeder":

1. Vælg **Application permissions** \> **Alert.Read.All** > vælg **på Tilføj tilladelser**

   :::image type="content" source="images/application-permissions.png" alt-text="Den indstilling, der gør det muligt at tilføje en tilladelse" lightbox="images/application-permissions.png":::

2. Vælg **Giv samtykke**

   - **Bemærk**! Hver gang du tilføjer tilladelse, skal du vælge **Giv samtykke,** før den nye tilladelse træder i kraft.

   :::image type="content" source="images/grant-consent.png" alt-text="Den indstilling, der tillader, at der gives samtykke" lightbox="images/grant-consent.png":::

3. Føj en hemmelighed til programmet.

   - Vælg **Certifikater & hemmeligheder,** føj beskrivelse til hemmeligheden, og vælg **Tilføj**.

    **Vigtigt**! Når du har klikket på Tilføj, **skal du kopiere den genererede hemmelige værdi**. Du kan ikke hente noget, når du er væk!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="Opret appnøglen" lightbox="images/webapp-create-key2.png":::

4. Skriv dit program-id ned:

   - På programsiden skal du gå **til Oversigt** og kopiere følgende oplysninger:

     :::image type="content" source="images/app-id.png" alt-text="Opret programmets id" lightbox="images/app-id.png":::

5. Føj programmet til din kundes lejer.

   Du skal have din ansøgning godkendt i hver kundelejer, hvor du vil bruge den. Dette skyldes, at dit program interagerer Microsoft Defender for Endpoint program på vegne af din kunde.

   En bruger med **global administrator** fra din kundes lejer skal vælge linket til samtykke og godkende dit program.

   Linket Samtykke er i formularen:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Hvor 00000000-0000-0000-0000-000000000000 skal erstattes med dit program-id

   Når du har klikket på linket til samtykke, skal du logge på med den globale administrator for kundens lejer og give samtykke til programmet.

   :::image type="content" source="images/app-consent-partner.png" alt-text="Knappen Acceptér" lightbox="images/app-consent-partner.png":::

   Desuden skal du bede din kunde om deres lejer-id og gemme det til senere brug, når du køber tokenet.

6. **Udført!** Du har registreret et program! Se nedenstående eksempler for at få adgang til token og validering.

## <a name="get-an-access-token-example"></a>Få et eksempel på et adgangstoken

**Bemærk!** Hvis du vil have adgangstoken på vegne af din kunde, skal du bruge kundens lejer-id på følgende tokenkøb.

Du kan finde flere oplysninger AAD om token under [AAD selvstudium](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

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

> Nedenstående kode blev testet med Nuget Microsoft.IdentityModel.Clients.ActiveDirectory

- Opret et nyt konsolprogram
- Installér NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- Tilføj nedenstående ved hjælp af

    ```console
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- Kopiér/Indsæt nedenstående kode i dit program (husk at opdatere de tre variabler: `tenantId`, `appId`og `appSecret`)

    ```console
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

### <a name="using-python"></a>Brug af Python

Henvis til [Hent token ved hjælp af Python](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>Brug af krøller

> [!NOTE]
> Nedenstående procedure forestiller, at krølle Windows allerede er installeret på din computer

- Åbne et kommandovindue
- Angiv CLIENT_ID dit Azure-program-id
- Angiv CLIENT_SECRET din Azure-programhemmelighed
- Angiv TENANT_ID Azure-lejer-id'et for den kunde, der vil bruge dit program til at få adgang Microsoft Defender for Endpoint program
- Kør nedenstående kommando:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Du får svar på formularen:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider tokenet

Sanity-tjek for at sikre, at du har et korrekt token:

- Kopiér/indsæt [i JWT](https://jwt.ms) den token, du får i forrige trin for at afkode den
- Valider, at du får et "roller"-krav med de ønskede tilladelser
- I skærmbilledet nedenfor kan du se et afkodet token, der er erhvervet fra et program med flere tilladelser til at Microsoft Defender for Endpoint:
- "tid"-kravet er det lejer-id, som tokenet tilhører.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="Siden til validering af token" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

- Vælg den API, du vil bruge, hvis du vil have mere at vide, under [Understøttede Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- Angiv godkendelseshovedet i den Http-anmodning, du sender til "Bearer {token}" (Bearer er godkendelsesskemaet)
- Udløbsdatoen for tokenet er 1 time (du kan sende mere end én anmodning med samme token)

- Eksempel på afsendelse af en anmodning om at få en liste over beskeder ved **hjælp af C#**

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
