---
title: Opret en app for at få adgang Microsoft 365 Defender uden en bruger
description: Få mere at vide om, hvordan du opretter en app for at Microsoft 365 Defender uden en bruger.
keywords: app, adgang, api, opret
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
ms.openlocfilehash: 8cbf6d8b69d9fbc8d8b083bf11e455a74b636af1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63592123"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>Opret en app for at få adgang Microsoft 365 Defender uden en bruger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Denne side beskriver, hvordan du opretter et program for at få programmeringsmæssig adgang til Microsoft 365 Defender uden en defineret bruger – f.eks. hvis du opretter en daemon- eller baggrundstjeneste.

Hvis du har brug for programmeringsadgang til Microsoft 365 Defender på vegne af en eller flere brugere, skal du se Opret en app til at få adgang til [Microsoft 365 Defender-API'er](api-create-app-user-context.md) på vegne af en bruger og Opret en [app med partneradgang til Microsoft 365 Defender API'er](api-partner-access.md). Hvis du ikke er sikker på, hvilken type adgang du skal bruge, kan du se [Introduktion](api-access.md).

Microsoft 365 Defender blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre Microsoft 365 Defender af alles funktioner. Denne API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge disse API'er:

- Opret et Azure Active Directory (Azure AD).
- Få et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang Microsoft 365 Defender API.

I denne artikel forklares det, hvordan du:

- Opret et Azure AD-program
- Få et adgangstoken til Microsoft 365 Defender
- Valider tokenet.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure som](https://portal.azure.com) en bruger med rollen **Global** administrator.

2. Gå til **Azure Active Directory** >  **App-registreringer** >  **Ny registrering**.

   ![Billede af Microsoft Azure og navigation til programregistrering.](../../media/atp-azure-new-app2.png)

3. I formularen skal du vælge et navn til dit program og derefter vælge **Registrer**.

4. På din programside skal du vælge **API-tilladelserFår** >  >  tilladelse API'er, som **min organisation bruger** >, skriv **Microsoft Threat Protection**, og vælg **Microsoft Threat Protection**. Din app kan nu få adgang Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* er et tidligere navn til Microsoft 365 Defender og vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at få det vist.

   ![Billede af valg af API-tilladelse.](../../media/apis-in-my-org-tab.PNG)

5. Vælg **Programtilladelser**. Vælg de relevante tilladelser til scenariet ( **f.eks. Incident.Read.All**), og vælg **derefter Tilføj tilladelser**.

   ![Billede af API-adgang og API-markering.](../../media/request-api-permissions.PNG)

    > [!NOTE]
    > Du skal vælge de relevante tilladelser til scenariet. *Læs alle hændelser er* blot et eksempel. Se afsnittet Tilladelser i den API, du vil ringe til **, for at** finde ud af, hvilken tilladelse du skal bruge.
    >
    > Hvis du f.eks [. vil køre avancerede forespørgsler](api-advanced-hunting.md), skal du vælge tilladelsen "Kør avancerede forespørgsler". Hvis [du vil isolere en enhed](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), skal du vælge tilladelsen "Isoler maskine".

6. Vælg **Giv administratorsamtykke**. Hver gang du tilføjer en tilladelse, skal du vælge **Giv administratorsamtykke** , før den træder i kraft.

    ![Billede af Giv tilladelser.](../../media/grant-consent.PNG)

7. Hvis du vil føje en hemmelighed til programmet, **skal du & Certifikater** og hemmeligheder, føje en beskrivelse til hemmeligheden og derefter vælge **Tilføj**.

    > [!TIP]
    > Når du har valgt **Tilføj**, skal du **vælge Kopiér den genererede hemmelige værdi**. Du kan ikke hente den hemmelige værdi, når du har forladet.

    ![Billede af Opret appnøgle.](../../media/webapp-create-key2.png)

8. Optag dit program-id og dit lejer-id et sikkert sted. De er angivet under **Oversigt på** din programside.

   ![Billede af oprettet app-id.](../../media/app-and-tenant-ids.png)

9. **Kun Microsoft 365 Defender-partnere**[: Følg](./api-partner-access.md) disse instruktioner for at få partneradgang via MICROSOFT 365 DEFENDER-API'er, indstil din app til at være flerlejer, så den kan være tilgængelig for alle lejere, når du modtager administratorsamtykke. Partneradgang er **påkrævet** til tredjepartsapps – f.eks. hvis du opretter en app, der er beregnet til at køre i flere kunders lejere. Det er **ikke påkrævet** , hvis du opretter en tjeneste, som du kun vil køre i din lejer, f.eks. et program til dit eget brug, der kun interagerer med dine egne data. Sådan angiver du din app til at være flere lejere:

    - Gå til **Godkendelse**, og tilføj https://portal.azure.com som **Redirect URI**.

    - Nederst på siden under Understøttede **kontotyper** skal du vælge Konti i et hvilket som helst **organisationsmappeprograms** samtykke for din app med flere lejere.

    Da dit program interagerer med Microsoft 365 Defender på vegne af dine brugere, skal det godkendes for hver lejer, som du regner med at bruge det på.

    Den globale Active Directory-administrator for hver lejer skal vælge linket til samtykke og godkende din app.

    Samtykkelinket har følgende struktur:

    ```http
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=<00000000-0000-0000-0000-000000000000>&response_type=code&sso_reload=true
    ```

    Cifrene `00000000-0000-0000-0000-000000000000` skal erstattes med dit program-id.  

**Udført!** Du har registreret et program! Se nedenstående eksempler for at få adgang til token og validering.

## <a name="get-an-access-token"></a>Få et adgangstoken

Du kan finde flere Azure Active Directory om Azure Active Directory i [Azure AD-selvstudiet](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Selvom eksemplerne i dette afsnit opfordrer dig til at indsætte hemmelige værdier til testformål, bør du aldrig indkode hemmeligheder i et program, der kører i produktion. En tredjepart kan bruge din hemmelighed til at få adgang til ressourcer. Du kan hjælpe med at holde din apps hemmeligheder sikre ved hjælp [af Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Du kan finde et praktisk eksempel på, hvordan du kan beskytte din app, under Administrer hemmeligheder i [dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

### <a name="get-an-access-token-using-powershell"></a>Få et adgangstoken ved hjælp af PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

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

1. Angiv TENANT_ID Azure-lejer-id'et for den kunde, der vil bruge din app til at få adgang Microsoft 365 Defender.

1. Kør følgende kommando:

   ```bash
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.security.microsoft.com/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```

   Et vellykket svar vil se sådan ud:

   ```bash
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## <a name="validate-the-token"></a>Valider tokenet

1. Kopiér og indsæt tokenet på [JSON's websted for webtoken, JWT,](https://jwt.ms) for at afkode den.

1. Sørg for, at *rollerne* , der angives i den afkodede token, indeholder de ønskede tilladelser.

   På følgende billede kan du se et afkodet token, der er købt fra en app, `Incidents.ReadWrite.All`med `Incidents.Read.All`, og `AdvancedHunting.Read.All` tilladelser:

   ![Billede af tokenvalidering.](../../media/webapp-decoded-token.png)

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
- [Oprette en app til at få adgang Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md)
- [Opret en app med partneradgang til flere lejere til Microsoft 365 Defender API'er](api-partner-access.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Administrer hemmeligheder i dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [OAuth 2.0-godkendelse til brugeradgang og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)