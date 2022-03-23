---
title: Hello World til Microsoft 365 Defender REST API
description: Få mere at vide om, hvordan du opretter en app og bruger et token til at få adgang Microsoft 365 Defender API'er
keywords: app, token, adgang, aad, app, programregistrering, powershell, script, global administrator, tilladelse, microsoft 365 defender
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
ms.openlocfilehash: 1c83a64c3bf1e721ea54b526c0db0c5d7c403fba
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63593522"
---
# <a name="hello-world-for-microsoft-365-defender-rest-api"></a>Hello World til Microsoft 365 Defender REST API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

## <a name="get-incidents-using-a-simple-powershell-script"></a>Få hændelser ved hjælp af et simpelt PowerShell-script

Det bør tage 5 til 10 minutter at gennemføre dette projekt. Denne anslåede tid omfatter registrering af programmet og anvendelse af koden fra PowerShell-eksempelscriptet.

### <a name="register-an-app-in-azure-active-directory"></a>Registrer en app i Azure Active Directory

1. Log på [Azure som](https://portal.azure.com) bruger med rollen **Global** administrator.

2. Gå til **Azure Active Directory** >  **App-registreringer** >  **Ny registrering**.

   ![Billede af Microsoft Azure og navigation til programregistrering.](../../media/atp-azure-new-app2.png)

3. I registreringsformularen skal du vælge et navn til dit program og derefter vælge **Registrer**. Det er valgfrit, om du vil vælge en omdirigerings-URI. Du behøver ikke en for at fuldføre dette eksempel.

4. På din programside skal du vælge **API-tilladelserFår** >  >  tilladelse API'er, som **min organisation bruger** >, skriv **Microsoft Threat Protection**, og vælg **Microsoft Threat Protection**. Din app kan nu få adgang Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* er et tidligere navn til Microsoft 365 Defender og vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at få det vist.
   ![Billede af valg af API-tilladelse.](../../media/apis-in-my-org-tab.PNG)

   - Vælg Application **permissionsIncident.Read.All** > , og **vælg Add permissions**.

   ![Billede af API-adgang og API-markering.](../../media/request-api-permissions.PNG)

5. Vælg **Giv administratorsamtykke**. Hver gang du tilføjer en tilladelse, skal du vælge **Giv administratorsamtykke** , før den træder i kraft.

    ![Billede af Giv tilladelser.](../../media/grant-consent.PNG)

6. Føj en hemmelighed til programmet. Vælg **Certifikater & hemmeligheder,** føj en beskrivelse til hemmeligheden, og vælg derefter **Tilføj**.

    > [!TIP]
    > Når du har valgt **Tilføj**, skal du **vælge Kopiér den genererede hemmelige værdi**. Du kan ikke hente den hemmelige værdi, når du har forladet.

    ![Billede af Opret appnøgle.](../../media/webapp-create-key2.png)

7. Optag dit program-id og dit lejer-id et sikkert sted. De er angivet under **Oversigt på** din programside.

   ![Billede af oprettet app-id.](../../media/app-and-tenant-ids.png)

### <a name="get-a-token-using-the-app-and-use-the-token-to-access-the-api"></a>Få et token ved hjælp af appen, og brug tokenet til at få adgang til API'en

Du kan finde flere Azure Active Directory om Azure Active Directory i [Azure AD-selvstudiet](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> Selvom eksemplet i denne demoapp opfordrer dig til at indsætte din hemmelige værdi til testformål, bør du aldrig  indkode hemmeligheder i et program, der kører i produktion. En tredjepart kan bruge din hemmelighed til at få adgang til ressourcer. Du kan hjælpe med at holde din apps hemmeligheder sikre ved hjælp [af Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). Du kan finde et praktisk eksempel på, hvordan du kan beskytte din app, under Administrer hemmeligheder i [dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

1. Kopiér scriptet nedenfor, og indsæt det i din foretrukne teksteditor. Gem som **Get-Token.ps1**. Du kan også køre koden, som den er i PowerShell ISE, men du skal gemme den, da vi er nødt til at køre den igen, når vi bruger scriptet til hentning af hændelser i næste afsnit.

    Dette script genererer et token og gemmer det i arbejdsmappen under navnet, *ogLatest-token.txt*.

    ```PowerShell
    # This script gets the app context token and saves it to a file named "Latest-token.txt" under the current directory.
    # Paste in your tenant ID, client ID and app secret (App key).

    $tenantId = '' # Paste your directory (tenant) ID here
    $clientId = '' # Paste your application (client) ID here
    $appSecret = '' # # Paste your own app secret here to test, then store it in a safe place!

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

#### <a name="validate-the-token"></a>Valider tokenet

1. Kopiér og indsæt det token, du har modtaget [, i JWT](https://jwt.ms) for at afkode den.
1. *JWT* står for *JSON Web Token*. Det afkodede token indeholder et antal JSON-formaterede elementer eller krav. Sørg for, at *rollerne* , der angives i den afkodede token, indeholder de ønskede tilladelser.

    På følgende billede kan du se et afkodet token, der er købt fra en app, ```Incidents.ReadWrite.All```med ```Incidents.Read.All```, og ```AdvancedHunting.Read.All``` tilladelser:

    ![Billede jwt.ms.](../../media/api-jwt-ms.png)

### <a name="get-a-list-of-recent-incidents"></a>Få en liste over de seneste hændelser

Scriptet nedenfor brugerGet-Token.ps1 **til** at få adgang til API'en. Den henter derefter en liste over hændelser, der senest er blevet opdateret inden for de seneste 48 timer, og gemmer listen som en JSON-fil.

> [!IMPORTANT]
> Gem dette script i den samme mappe, du gemte **Get-Token.ps1**.

```PowerShell
# This script returns incidents last updated within the past 48 hours.

$token = ./Get-Token.ps1

# Get incidents from the past 48 hours.
# The script may appear to fail if you don't have any incidents in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

# This URL contains the type of query and the time filter we created above.
# Note that `$filter` does not refer to a local variable in our script --
# it's actually an OData operator and part of the API's syntax.
$url = "https://api.security.microsoft.com/api/incidents?$filter=lastUpdateTime+ge+$dateTime"

# Set the webrequest headers
$headers = @{
    'Content-Type' = 'application/json'
    'Accept' = 'application/json'
    'Authorization' = "Bearer $token"
}

# Send the request and get the results.
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

# Extract the incidents from the results.
$incidents =  ($response | ConvertFrom-Json).value | ConvertTo-Json -Depth 99

# Get a string containing the execution time. We concatenate that string to the name 
# of the output file to avoid overwriting the file on consecutive runs of the script.
$dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

# Save the result as json
$outputJsonPath = "./Latest Incidents $dateTimeForFileName.json"

Out-File -FilePath $outputJsonPath -InputObject $incidents
```

Du er færdig! Du har:

- Et program blev oprettet og registreret.
- Tildelt tilladelse til det pågældende program til at læse beskeder.
- Forbundet til API'en.
- Et PowerShell-script blev brugt til at returnere hændelser, der er opdateret inden for de seneste 48 timer.

## <a name="related-articles"></a>Relaterede artikler

- [Microsoft 365 Defender OVERSIGT over API'er](api-overview.md)
- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Opret en app for at få adgang Microsoft 365 Defender uden en bruger](api-create-app-web.md)
- [Oprette en app til at få adgang Microsoft 365 Defender API'er på vegne af en bruger](api-create-app-user-context.md)
- [Opret en app med partneradgang til flere lejere til Microsoft 365 Defender API'er](api-partner-access.md)
- [Administrer hemmeligheder i dine serverapps med Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [OAuth 2.0 Godkendelse af brugeradgang og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)