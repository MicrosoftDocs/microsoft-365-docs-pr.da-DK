---
title: Opret en app for at få adgang til Microsoft 365 Defender API'er på vegne af en bruger
description: Få mere at vide om, hvordan du får adgang til Microsoft 365 Defender API'er på vegne af en bruger.
keywords: adgang, på vegne af bruger, API, program, bruger, adgangstoken, token,
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
ms.openlocfilehash: 41f2763d73bbb9ed0b7ae32dce431cb2c1a4d71f
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102586"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Opret en app for at få adgang til Microsoft 365 Defender API'er på vegne af en bruger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

På denne side beskrives det, hvordan du opretter et program for at få programmatisk adgang til Microsoft 365 Defender på vegne af en enkelt bruger.

Hvis du har brug for programmatisk adgang til Microsoft 365 Defender uden en defineret bruger (f.eks. hvis du skriver en baggrundsapp eller -daemon), skal du se [Opret en app for at få adgang til Microsoft 365 Defender uden en bruger](api-create-app-web.md). Hvis du har brug for at give adgang til flere lejere – f.eks. hvis du betjener en stor organisation eller en gruppe kunder – skal du se [Opret en app med partneradgang til Microsoft 365 Defender API'er](api-partner-access.md). Hvis du ikke er sikker på, hvilken type adgang du har brug for, skal du se [Kom i gang](api-access.md).

Microsoft 365 Defender fremviser mange af sine data og handlinger via et sæt programmatiske API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre brug af Microsoft 365 Defender funktioner. Denne API-adgang kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du gøre følgende for at bruge disse API'er:

- Opret et Azure Active Directory (Azure AD)-program.
- Hent et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang til Microsoft 365 Defender API.

I denne artikel forklares det, hvordan du:

- Opret et Azure AD program
- Hent et adgangstoken til Microsoft 365 Defender
- Valider tokenet

> [!NOTE]
> Når du får adgang til Microsoft 365 Defender API på vegne af en bruger, skal du have de korrekte programtilladelser og brugertilladelser.

> [!TIP]
> Hvis du har tilladelse til at udføre en handling på portalen, har du tilladelse til at udføre handlingen i API'en.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure](https://portal.azure.com) som bruger med rollen **Global administrator** .

2. Gå til **Azure Active Directory** >  **Appregistreringer** > **Ny registrering**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Indstillingen Ny registrering i ruden Administrer i Azure Portal" lightbox="../../media/atp-azure-new-app2.png":::

3. I formularen skal du vælge et navn til dit program og angive følgende oplysninger for omdirigerings-URI'en og derefter vælge **Registrer**.

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="Ruden programregistrering i Azure Portal" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **Programtype:** Offentlig klient
   - **Omdirigerings-URI:** https://portal.azure.com

4. På din programside skal du vælge **API-tilladelser** > **Tilføj****tilladelseS-API'er** > , som min organisation bruger >, skrive **Microsoft Threat Protection** og vælge **Microsoft Threat Protection**. Din app kan nu få adgang til Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* er et tidligere navn på Microsoft 365 Defender og vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at se det blive vist.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Ruden API'er for din organisation på Microsoft 365 Defender-portalen" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - Vælg **Delegerede tilladelser**. Vælg de relevante tilladelser til dit scenarie ( **f.eks. Incident.Read**), og vælg derefter **Tilføj tilladelser**.

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="Ruden Delegerede tilladelser på portalen Microsoft 365 Defender" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > Du skal vælge de relevante tilladelser til dit scenarie. *Læs alle hændelser* er blot et eksempel. Hvis du vil finde ud af, hvilken tilladelse du har brug for, skal du se afsnittet **Tilladelser** i den API, du vil kalde.
    >
    > Hvis du f.eks. vil [køre avancerede forespørgsler](api-advanced-hunting.md), skal du vælge tilladelsen 'Kør avancerede forespørgsler'. Hvis du vil [isolere en enhed](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), skal du vælge tilladelsen "Isoler computer".

5. Vælg **Giv administratorsamtykke**. Hver gang du tilføjer en tilladelse, skal du vælge **Giv administratorsamtykke** , for at den kan træde i kraft.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="Ruden til tildeling af administratorsamtykke på portalen Microsoft 365 Defender" lightbox="../../media/grant-consent-delegated.PNG":::

6. Registrer dit program-id og dit lejer-id et sikkert sted. De vises under **Oversigt** på din programside.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Ruden Oversigt på Microsoft 365 Defender-portalen" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Hent et adgangstoken

Du kan få flere oplysninger om Azure Active Directory tokens i [selvstudiet Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-on-behalf-of-a-user-using-powershell"></a>Få et adgangstoken på vegne af en bruger ved hjælp af PowerShell

Brug biblioteket MSAL.PS til at hente adgangstokens med delegerede tilladelser. Kør følgende kommandoer for at få adgangstoken på vegne af en bruger:

```PowerShell
Install-Module -Name MSAL.PS # Install the MSAL.PS module from PowerShell Gallery

$TenantId = " " # Paste your directory (tenant) ID here.
$AppClientId="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" # Paste your application (client) ID here.

$MsalParams = @{
   ClientId = $AppClientId
   TenantId = $TenantId
   Scopes   = 'https://graph.microsoft.com/User.Read.All','https://graph.microsoft.com/Files.ReadWrite'
}

$MsalResponse = Get-MsalToken @MsalParams
$AccessToken  = $MsalResponse.AccessToken
 
$AccessToken # Display the token in PS console
```
## <a name="validate-the-token"></a>Valider tokenet

1. Kopiér og indsæt tokenet i [JWT](https://jwt.ms) for at afkode det.
2. Sørg for, at *rollekravet* i det afkodede token indeholder de ønskede tilladelser.

På følgende billede kan du se et afkodet token, der er hentet fra en app, med ```Incidents.Read.All```tilladelserne , ```Incidents.ReadWrite.All```og ```AdvancedHunting.Read.All``` :

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Afsnittet om tilladelser i ruden Afkodet token på portalen Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

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
- [Opret en 'Hello world'-app](api-hello-world.md)
- [Opret en app for at få adgang til Microsoft 365 Defender uden en bruger](api-create-app-web.md)
- [Opret en app med partneradgang med flere lejere til Microsoft 365 Defender API'er](api-partner-access.md)
- [Få mere at vide om API-grænser og -licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [OAuth 2.0-godkendelse til brugerlogon og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
