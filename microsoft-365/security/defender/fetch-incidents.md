---
title: Hent Microsoft 365 Defender hændelser
description: Få mere at vide om, hvordan Microsoft 365 Defender hændelser fra en kundelejer
keywords: administreret sikkerheds serviceudbyder, mssp, konfigurer, integration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 1ea39bfce5303360165a56d6361908d1014d370f
ms.sourcegitcommit: e110f00dc6949a7a1345187375547beeb64225b2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/06/2021
ms.locfileid: "63594670"
---
# <a name="fetch-microsoft-365-defender-incidents"></a>Hent Microsoft 365 Defender hændelser 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> [!NOTE]
> Denne handling er foretaget af MSSP.

Du kan hente beskeder på to måder:

- Brug af SIEM-metoden
- Brug af API'er

## <a name="fetch-incidents-into-your-siem"></a>Hent hændelser i din SIEM

Hvis du vil hente hændelser til dit SIEM-system, skal du gøre følgende:

- Trin 1: Opret et tredjepartsprogram
- Trin 2: Få adgang til og opdater tokens fra din kundes lejer
- Trin 3: Tillad dit program på Microsoft 365 Defender

### <a name="step-1-create-an-application-in-azure-active-directory-azure-ad"></a>Trin 1: Opret et program i Azure Active Directory (Azure AD)

Du skal oprette et program og give det tilladelse til at hente beskeder fra din kundes Microsoft 365 Defender lejer.

1. Log på [Azure AD-portalen](https://aad.portal.azure.com/).

2. Vælg **Azure Active Directory** \> **appregistreringer**.

3. Klik **på Ny registrering**.

4. Angiv følgende værdier:

    - Navn: \<Tenant_name\> SIEM MSSP-forbindelse (Tenant_name med lejerens viste navn)

    - Understøttede kontotyper: Kun konto i denne organisationsmappe
    - Omdiriger URI: Vælg Web `https://<domain_name>/SiemMsspConnector`, og skriv (<domain_name> med lejernavnet)

5. Klik **på Registrer**. Programmet vises på listen over programmer, du ejer.

6. Vælg programmet, og klik derefter på **Oversigt**.

7. Kopiér værdien fra **feltet Program-id (klient)** til et sikkert sted, og brug det i næste trin.

8. Vælg **Certifikat & i** det nye programpanel.

9. Klik **på Ny klienthemmelighed**.

    - Beskrivelse: Angiv en beskrivelse af nøglen.
    - Udløber: Vælg **Om 1 år**

10. Klik **på** Tilføj, kopiér værdien af klienthemmelighed til et sikkert sted, du skal bruge dette i næste trin.

### <a name="step-2-get-access-and-refresh-tokens-from-your-customers-tenant"></a>Trin 2: Få adgang til og opdater tokens fra din kundes lejer

Dette afsnit guider dig til, hvordan du bruger et PowerShell-script til at hente tokens fra din kundes lejer. Dette script bruger programmet fra det forrige trin til at få adgangs- og opdateringstokens ved hjælp af OAuth-godkendelseskoden Flow.

Når du har givet dine legitimationsoplysninger, skal du give samtykke til programmet, så programmet er klargjort i kundens lejer.

1. Opret en ny mappe, og navngive den: `MsspTokensAcquisition`.

2. Download [loginBrowser.psm1-modulet](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) , og gem det i `MsspTokensAcquisition` mappen.

    > [!NOTE]
    > Erstat med i linje `authorzationUrl` `authorizationUrl`30.

3. Opret en fil med følgende indhold, og gem den med navnet `MsspTokensAcquisition.ps1` i mappen:

    ```powershell
    param (
        [Parameter(Mandatory=$true)][string]$clientId,
        [Parameter(Mandatory=$true)][string]$secret,
        [Parameter(Mandatory=$true)][string]$tenantId
    )
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

    # Load our Login Browser Function
    Import-Module .\LoginBrowser.psm1

    # Configuration parameters
    $login = "https://login.microsoftonline.com"
    $redirectUri = "https://SiemMsspConnector"
    $resourceId = "https://graph.windows.net"

    Write-Host 'Prompt the user for his credentials, to get an authorization code'
    $authorizationUrl = ("{0}/{1}/oauth2/authorize?prompt=select_account&response_type=code&client_id={2}&redirect_uri={3}&resource={4}" -f
                        $login, $tenantId, $clientId, $redirectUri, $resourceId)
    Write-Host "authorzationUrl: $authorizationUrl"

    # Fake a proper endpoint for the Redirect URI
    $code = LoginBrowser $authorizationUrl $redirectUri

    # Acquire token using the authorization code

    $Body = @{
        grant_type = 'authorization_code'
        client_id = $clientId
        code = $code
        redirect_uri = $redirectUri
        resource = $resourceId
        client_secret = $secret
    }

    $tokenEndpoint = "$login/$tenantId/oauth2/token?"
    $Response = Invoke-RestMethod -Method Post -Uri $tokenEndpoint -Body $Body
    $token = $Response.access_token
    $refreshToken= $Response.refresh_token

    Write-Host " ----------------------------------- TOKEN ---------------------------------- "
    Write-Host $token

    Write-Host " ----------------------------------- REFRESH TOKEN ---------------------------------- "
    Write-Host $refreshToken
    ```
4. Åbn en kommandoprompt med administratorerne i PowerShell i `MsspTokensAcquisition` mappen.

5. Kør følgende kommando: `Set-ExecutionPolicy -ExecutionPolicy Bypass`

6. Angiv følgende kommandoer: `.\MsspTokensAcquisition.ps1 -clientId <client_id> -secret <app_key> -tenantId <customer_tenant_id>`

    - Erstat \<client_id\> med det **program-id (klient), du** fik fra det forrige trin.
    - Erstat \<app_key\> med den **Klienthemmelighed** , du oprettede fra det forrige trin.
    - Erstat \<customer_tenant_id\> med din kundes **Lejer-id**.

7. Du vil blive bedt om at angive dine legitimationsoplysninger og dit samtykke. Ignorer sidens omdirigering.

8. I Vinduet PowerShell modtager du et adgangstoken og en opdateringstoken. Gem opdateringstokenet til konfiguration af SIEM-forbindelsen.

### <a name="step-3-allow-your-application-on-microsoft-365-defender"></a>Trin 3: Tillad dit program på Microsoft 365 Defender

Du skal tillade det program, du oprettede i Microsoft 365 Defender.

Du skal have tilladelse til **at administrere portalsystemindstillinger** for at tillade programmet. Ellers skal du anmode din kunde om at tillade programmet for dig.

1. Gå til `https://security.microsoft.com?tid=<customer_tenant_id>` (erstat \<customer_tenant_id\> med kundens lejer-id.

2. Klik **Indstillinger** \> **SLUTPUNKTS-API'er** \>  \> **SIEM**.

3. Vælg **fanen MSSP** .

4. Angiv **program-id'et** fra det første trin og dit **lejer-id**.

5. Klik på **Godkend program**.

Nu kan du downloade den relevante konfigurationsfil til din SIEM og oprette forbindelse til Microsoft 365 Defender API. Du kan få mere at vide [under Trække beskeder til dine SIEM-værktøjer](../defender-endpoint/configure-siem.md).

- I ArcSight-konfigurationsfilen / Splunk Authentication Properties-filen skal du skrive din programnøgle manuelt ved at angive den hemmelige værdi.
- I stedet for at hente et opdateringstoken i portalen kan du bruge scriptet fra det forrige trin til at hente et opdateringstoken (eller hente det på anden måde).

## <a name="fetch-alerts-from-mssp-customers-tenant-using-apis"></a>Hent beskeder fra MSSP-kundes lejer ved hjælp af API'er

Du kan finde oplysninger om, hvordan du henter beskeder ved hjælp af REST-API, [under Trække beskeder ved hjælp af REST-API](../defender-endpoint/pull-alerts-using-rest-api.md).
