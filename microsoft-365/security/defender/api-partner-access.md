---
title: Partneradgang via Microsoft 365 Defender API'er
description: Få mere at vide om, hvordan du opretter en app for at få programmeringsadgang til Microsoft 365 Defender på vegne af dine brugere.
keywords: partner, adgang, api, multilejer, samtykke, adgangstoken, app
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
ms.openlocfilehash: f0ed889cbc0a07a1f64bc0f717fe07fe877a98b9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754682"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>Oprette en app med partneradgang til Microsoft 365 Defender API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Denne side beskriver, hvordan du opretter en Azure Active Directory-app, der har programmeringsadgang til Microsoft 365 Defender, på vegne af brugere på tværs af flere lejere. Apps med flere lejere er nyttige til at betjene store grupper af brugere.

Hvis du har brug for programmeringsadgang til Microsoft 365 Defender på vegne af en enkelt bruger, kan du se Opret en app til at få adgang [til Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md). Hvis du skal have adgang, uden at en bruger eksplicit er defineret (f.eks. hvis du skriver en baggrundsapp eller daemon), skal du se Opret en app for at Microsoft 365 Defender [adgang uden en bruger](api-create-app-web.md). Hvis du ikke er sikker på, hvilken type adgang du skal bruge, kan du se [Introduktion](api-access.md).

Microsoft 365 Defender blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre Microsoft 365 Defender af alles funktioner. Denne API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge disse API'er:

- Opret et Azure Active Directory (Azure AD).
- Få et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang Microsoft 365 Defender API.

Da denne app er flere lejere, skal du også have [administratorsamtykke](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) fra hver lejer på vegne af dens brugere.

I denne artikel forklares det, hvordan du:

- Opret et **Azure AD-program med** flere lejere
- Få autoriseret samtykke fra din brugeradministrator til din applikation for at få adgang til de Microsoft 365 Defender ressourcer, den har brug for.
- Få et adgangstoken til Microsoft 365 Defender
- Valider tokenet

Microsoft 365 Defender blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere pengestrømme og forny baseret på Microsoft 365 Defender funktioner. API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge API'er:

- Opret et **Azure AD-program med** flere lejere.
- Få tilladelse (samtykke) af din brugeradministrator til dit program for at få adgang til Microsoft 365 Defender ressourcer, det har brug for.
- Få et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang Microsoft 365 Defender API.

Følgende trin med vejledning i, hvordan du opretter et Azure AD-program med flere lejere, får et adgangstoken til at Microsoft 365 Defender og validere tokenet.

## <a name="create-the-multi-tenant-app"></a>Opret appen med flere lejere

1. Log på [Azure som](https://portal.azure.com) en bruger med rollen **Global** administrator.

2. Gå til **Azure Active Directory** >  **App-registreringer** >  **Ny registrering**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Et programs registreringssektion i Microsoft 365 Defender-portalen" lightbox="../../media/atp-azure-new-app2.png":::

3. I registreringsformularen:

   - Vælg et navn til dit program.
   - Fra **Understøttede kontotyper** skal du **vælge Konti i enhver organisationsmappe (Enhver Azure AD-mappe) – Multitenant**.
   - Udfyld afsnittet **Redirect URI** . Vælg Type **Web,** og giv URI'en til omdirigering som **https://portal.azure.com**.

   Når du er færdig med at udfylde formularen, skal du vælge **Registrer**.

   :::image type="content" source="../..//media/atp-api-new-app-partner.png" alt-text="Et programs registreringssnit i Microsoft 365 Defender-portalen" lightbox="../..//media/atp-api-new-app-partner.png":::

4. På din programside skal du vælge **API-tilladelserFår** >  >  tilladelse API'er, som **min organisation bruger** >, skriv **Microsoft Threat Protection**, og vælg **Microsoft Threat Protection**. Din app kan nu få adgang Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* er et tidligere navn til Microsoft 365 Defender og vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at få det vist.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Afsnittet Brug af API'er i Microsoft 365 Defender portal" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. Vælg **Programtilladelser**. Vælg de relevante tilladelser til scenariet ( **f.eks. Incident.Read.All**), og vælg **derefter Tilføj tilladelser**.

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="Ruden med tilladelser for et program i Microsoft 365 Defender portalen" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > Du skal vælge de relevante tilladelser til scenariet. *Læs alle hændelser er* blot et eksempel. Se afsnittet Tilladelser i den API, du vil ringe til **, for at** finde ud af, hvilken tilladelse du skal bruge.
    >
    > Hvis du f.eks [. vil køre avancerede forespørgsler](api-advanced-hunting.md), skal du vælge tilladelsen "Kør avancerede forespørgsler". Hvis [du vil isolere en enhed](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), skal du vælge tilladelsen "Isoler maskine".

6. Vælg **Giv administratorsamtykke**. Hver gang du tilføjer en tilladelse, skal du vælge **Giv administratorsamtykke** , før den træder i kraft.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="Et afsnit til at give administratorsamtykke i Microsoft 365 Defender portal" lightbox="../../media/grant-consent.PNG":::

7. Hvis du vil føje en hemmelighed til programmet, **skal du & Certifikater** og hemmeligheder, føje en beskrivelse til hemmeligheden og derefter vælge **Tilføj**.

    > [!TIP]
    > Når du har valgt **Tilføj**, skal du **vælge Kopiér den genererede hemmelige værdi**. Du kan ikke hente den hemmelige værdi, når du har forladet.

      :::image type="content" source="../../media/webapp-create-key2.png" alt-text="Sektionen Hemmelig tilføjelse i Microsoft 365 Defender portal" lightbox="../../media/webapp-create-key2.png":::

8. Optag dit program-id og dit lejer-id et sikkert sted. De er angivet under **Oversigt på** din programside.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Ruden Oversigt i Microsoft 365 Defender portal" lightbox="../../media/app-and-tenant-ids.png":::

9. Føj programmet til din brugers lejer.

   Da dit program interagerer med Microsoft 365 Defender på vegne af dine brugere, skal det godkendes for hver lejer, som du regner med at bruge det på.

   En **global administrator** fra din brugers lejer skal se linket til samtykke og godkende dit program.

   Linket Samtykke er i formularen:

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   Cifrene `00000000-0000-0000-0000-000000000000` skal erstattes med dit program-id.

   Når du har klikket på linket til samtykke, skal du logge på med den globale administrator for brugerens lejer og give samtykke til programmet.

   :::image type="content" source="../../media/app-consent-partner.png" alt-text="Siden for samtykkeprogrammet i Microsoft 365 Defender portal" lightbox="../../media/app-consent-partner.png":::

   Du skal også bede din bruger om deres lejer-id. Lejer-id'et er et af de identifikatorer, der bruges til at hente adgangstokens.

- **Udført!** Du har registreret et program!
- Se nedenstående eksempler for at få adgang til token og validering.

## <a name="get-an-access-token"></a>Få et adgangstoken

Du kan finde flere oplysninger om Azure AD-tokens i [Azure AD-selvstudiet](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Selvom eksemplerne i dette afsnit opfordrer dig til at indsætte hemmelige værdier til testformål, bør du aldrig indkode hemmeligheder i et program, der kører i produktion. En tredjepart kan bruge din hemmelighed til at få adgang til ressourcer. Du kan hjælpe med at holde din apps hemmeligheder sikre ved hjælp [af Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Du kan finde et praktisk eksempel på, hvordan du kan beskytte din app, under Administrer hemmeligheder i [dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

> [!TIP]
> I følgende eksempler skal du bruge en brugers lejer-id til at teste, at scriptet fungerer.

### <a name="get-an-access-token-using-powershell"></a>Få et adgangstoken ved hjælp af PowerShell

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

### <a name="get-an-access-token-using-c"></a>Få et adgangstoken ved hjælp af C\#

> [!NOTE]
> Følgende kode blev testet med Nuget Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. Opret et nyt konsolprogram.
1. Installér NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. Tilføj følgende linje:

    ```C#
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. Kopiér og indsæt følgende kode i din app (husk at opdatere de tre variabler: `tenantId`, , `clientId``appSecret`):

    ```C#
    string tenantId = ""; // Paste your directory (tenant) ID here
    string clientId = ""; // Paste your application (client) ID here
    string appSecret = ""; // Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

    const string authority = "https://login.windows.net";
    const string wdatpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(clientId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```

### <a name="get-an-access-token-using-python"></a>Få et adgangstoken ved hjælp af Python

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

### <a name="get-an-access-token-using-curl"></a>Få et adgangstoken med krøllet

> [!NOTE]
> Krølle er forudinstalleret på Windows 10 version 1803 og nyere. For andre versioner af Windows du downloade og installere værktøjet direkte fra det [officielle krøllede websted](https://curl.haxx.se/windows/).

1. Åbn en kommandoprompt, og angiv CLIENT_ID dit Azure-program-id.
1. Indstil CLIENT_SECRET til din Azure-programhemmelighed.
1. Angiv TENANT_ID Azure-lejer-id'et for den bruger, der vil bruge din app til at få adgang Microsoft 365 Defender.
1. Kør følgende kommando:

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

Et vellykket svar vil se sådan ud:

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>Valider tokenet

1. Kopiér og indsæt tokenet på [JSON's websted for webtoken, JWT,](https://jwt.ms) for at afkode den.
1. Sørg for, at *rollerne* , der angives i den afkodede token, indeholder de ønskede tilladelser.

På følgende billede kan du se et afkodet token, der er købt fra en app, ```Incidents.ReadWrite.All```med ```Incidents.Read.All```, og ```AdvancedHunting.Read.All``` tilladelser:

:::image type="content" source="../../media/webapp-decoded-token.png" alt-text="Ruden Afkodet token i Microsoft 365 Defender portal" lightbox="../../media/webapp-decoded-token.png":::


## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>Brug tokenet til at få adgang til Microsoft 365 Defender API

1. Vælg den API, du vil bruge (hændelser eller avanceret jagt). Du kan finde flere oplysninger under [Understøttede Microsoft 365 Defender API'er](api-supported.md).
2. I http-anmodningen, du er ved at sende, `"Bearer" <token>`skal du angive godkendelsesoverskriften til , *Bearer* er godkendelsesskemaet, og *token* bliver din validerede token.
3. Tokenet udløber inden for en time. Du kan sende mere end én anmodning i dette tidsrum med samme token.

I følgende eksempel vises det, hvordan du sender en anmodning om at få en liste over hændelser **ved hjælp af C#**.

```C#
   var httpClient = new HttpClient();
   var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

   request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

   var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft 365 Defender OVERSIGT over API'er](api-overview.md)
- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Opret et "Hej verden"-program](api-hello-world.md)
- [Opret en app for at få adgang Microsoft 365 Defender uden en bruger](api-create-app-web.md)
- [Oprette en app til at få adgang Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Administrer hemmeligheder i dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [OAuth 2.0-godkendelse til brugeradgang og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
