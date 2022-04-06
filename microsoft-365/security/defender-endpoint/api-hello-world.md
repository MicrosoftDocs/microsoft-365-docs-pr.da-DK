---
title: Hello World til Microsoft Defender for Endpoint API
ms.reviewer: ''
description: Opret et API-kald af "Hej verden"-typografi til Microsoft Defender for Endpoint API.
keywords: apis, understøttede api'er, avanceret jagt, forespørgsel, microsoft defender atp, microsoft defender til slutpunkt
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
ms.openlocfilehash: bd8f48e8396225fc03441cfc7c8ed69fa3f378bb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475603"
---
# <a name="microsoft-defender-for-endpoint-api---hello-world"></a>Microsoft Defender for Endpoint API – Hello World

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


>Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="get-alerts-using-a-simple-powershell-script"></a>Få beskeder ved hjælp af et simpelt PowerShell-script

### <a name="how-long-it-takes-to-go-through-this-example"></a>Hvor lang tid tager det at gennemgå dette eksempel?

Det tager kun 5 minutter at gøre dette i to trin:

- Programregistrering
- Brug eksempler: kræver kun kopiér/indsæt af et kort PowerShell-script

### <a name="do-i-need-a-permission-to-connect"></a>Skal jeg have tilladelse til at oprette forbindelse?

For programregistreringsfasen skal du have en Global administrator **rolle i** din Azure Active Directory (Azure AD).

### <a name="step-1---create-an-app-in-azure-active-directory"></a>Trin 1 – Opret en app i Azure Active Directory

1. Log på [Azure](https://portal.azure.com) med din **Global administrator** bruger.

2. Gå til **Azure Active Directory** \> **appregistreringer** \> **Ny registrering**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Indstillingen Appregistreringer under ruden Administrer i Azure Active Directory portal"  lightbox="images/atp-azure-new-app2.png":::

3. I registreringsformularen skal du vælge et navn til dit program og derefter klikke på **Registrer**.

4. Giv dit program adgang til Defender til Slutpunkt, og tildel **tilladelse til at "Læse alle vigtige beskeder** ":

   - På  programsiden skal du klikke på API-tilladelser Tilføj **tilladelses-API'er**  \> \>, som min organisation bruger > type **WindowsDefenderATP**, og klik på **WindowsDefenderATP**.

     > [!NOTE]
     > WindowsDefenderATP vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at få det vist.

     :::image type="content" source="images/add-permission.png" alt-text="Indstillingen API-tilladelser under ruden Administrer i Azure Active Directory portal" lightbox="images/add-permission.png":::

   - Vælg **Application permissions** \> **Alert.Read.All** > Klik **på Tilføj tilladelser**.

     :::image type="content" source="images/application-permissions.png" alt-text="Ruder for tilladelsestype og indstillinger på siden Med anmodnings-API-tilladelser" lightbox="images/application-permissions.png":::

     > [!IMPORTANT]
     > Du skal vælge de relevante tilladelser. "Læs alle beskeder" er kun et eksempel!

     Eksempel:

     - Hvis [du vil køre avancerede forespørgsler](run-advanced-query-api.md), skal du vælge tilladelsen "Kør avancerede forespørgsler".
     - Hvis du [vil isolere en maskine](isolate-machine.md), skal du vælge tilladelse som "Isoler maskine".
     - Se afsnittet Tilladelser i den API, du er interesseret i  at ringe til, for at finde ud af, hvilken tilladelse du skal bruge.

5. Klik **på Giv samtykke**.

   > [!NOTE]
   > Hver gang du tilføjer tilladelse, skal du klikke på **Giv samtykke,** før den nye tilladelse træder i kraft.

   :::image type="content" source="images/grant-consent.png" alt-text="Indstillingen til samtykke med tilladelse i Azure Active Directory portal" lightbox="images/grant-consent.png":::

6. Føj en hemmelighed til programmet.

    Klik **på Certifikater &, føj** en beskrivelse til hemmeligheden, og klik på **Tilføj**.

    > [!IMPORTANT]
    > Når du har klikket på **Tilføj, skal du kopiere den genererede hemmelige værdi**. Du kan ikke hente noget, når du er væk!

    :::image type="content" source="images/webapp-create-key2.png" alt-text="Menupunktet Certifikater & hemmeligholde i ruden Administrer i Azure Active Directory portal" lightbox="images/webapp-create-key2.png":::

7. Skriv dit program-id og dit lejer-id ned.

   På programsiden skal du gå **til Oversigt** og kopiere følgende:

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Detaljeruden for programmet under menuelementet Oversigt i Azure Active Directory portal" lightbox="images/app-and-tenant-ids.png":::

Udført! Du har registreret et program!

### <a name="step-2---get-a-token-using-the-app-and-use-this-token-to-access-the-api"></a>Trin 2 – Få et token ved hjælp af appen, og brug denne token til at få adgang til API'en.

- Kopiér scriptet nedenfor til PowerShell ISE eller til en teksteditor, og gem det som **Get-Token.ps1**.
- Kørsel af dette script genererer et token og gemmer det i arbejdsmappen under **navnetLatest-token.txt**.

   ```powershell
   # That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
   # Paste below your Tenant ID, App ID and App Secret (App key).

   $tenantId = '' ### Paste your tenant ID here
   $appId = '' ### Paste your Application ID here
   $appSecret = '' ### Paste your Application secret here

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

- Sanity Check:
  - Kør scriptet.
  - I din browser skal du gå til: <https://jwt.ms/>.
  - Kopiér tokenet (indholdet af Latest-token.txt fil).
  - Indsætte i feltet øverst.
  - Se efter afsnittet "Roller". Find rollen _Alert.Read.All_ .

  :::image type="content" source="images/api-jwt-ms.png" alt-text="Ruden Afkodet token for jwt.ms" lightbox="images/api-jwt-ms.png":::

### <a name="lets-get-the-alerts"></a>Lad os få beskederne!

- Scriptet nedenfor brugerGet-Token.ps1 **til** at få adgang til API'en og får de seneste 48 timer beskeder.
- Gem dette script i samme mappe, som du gemte det **forrigeGet-Token.ps1**.
- Scriptet opretter to filer (json og CSV) med dataene i samme mappe som scripterne.

  ```powershell
  # Returns Alerts created in the past 48 hours.

  $token = ./Get-Token.ps1       #run the script Get-Token.ps1  - make sure you are running this script from the same folder of Get-Token.ps1

  # Get Alert from the last 48 hours. Make sure you have alerts in that time frame.
  $dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

  # The URL contains the type of query and the time filter we create above
  # Read more about other query options and filters at   Https://TBD- add the documentation link
  $url = "https://api.securitycenter.microsoft.com/api/alerts?`$filter=alertCreationTime ge $dateTime"

  # Set the WebRequest headers
  $headers = @{
      'Content-Type' = 'application/json'
      Accept = 'application/json'
      Authorization = "Bearer $token"
  }

  # Send the webrequest and get the results.
  $response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

  # Extract the alerts from the results.
  $alerts =  ($response | ConvertFrom-Json).value | ConvertTo-Json

  # Get string with the execution time. We concatenate that string to the output file to avoid overwrite the file
  $dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

  # Save the result as json and as csv
  $outputJsonPath = "./Latest Alerts $dateTimeForFileName.json"
  $outputCsvPath = "./Latest Alerts $dateTimeForFileName.csv"

  Out-File -FilePath $outputJsonPath -InputObject $alerts
  ($alerts | ConvertFrom-Json) | Export-CSV $outputCsvPath -NoTypeInformation
  ```

Du er færdig! Du har lige fået:

- Oprettet og registreret og program
- Tildelt tilladelse til det pågældende program til at læse beskeder
- Api'en blev forbundet
- Et PowerShell-script blev brugt til at returnere beskeder, der er oprettet inden for de seneste 48 timer

## <a name="related-topic"></a>Relateret emne

- [Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- [Access Microsoft Defender for Endpoint med programkontekst](exposed-apis-create-app-webapp.md)
- [Access Microsoft Defender for Endpoint med brugerkontekst](exposed-apis-create-app-nativeapp.md)
