---
title: Oprette en app til at få adgang Microsoft 365 Defender API'er på vegne af en bruger
description: Lær, hvordan du får Microsoft 365 Defender-API'er på vegne af en bruger.
keywords: adgang, på vegne af bruger, api, program, bruger, adgangstoken, token,
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
ms.openlocfilehash: fdba7ee1b1cf2f46bd17c648c7cda48f1ca65490
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755213"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>Oprette en app til at få adgang Microsoft 365 Defender API'er på vegne af en bruger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Denne side beskriver, hvordan du opretter et program for at få programmeringsadgang til Microsoft 365 Defender på vegne af en enkelt bruger.

Hvis du har brug for programmeringsmæssig adgang til Microsoft 365 Defender uden en defineret bruger (f.eks. hvis du skriver en baggrundsapp eller daemon), skal du se Opret en app for at [få adgang til Microsoft 365 Defender uden](api-create-app-web.md) en bruger. Hvis du skal give adgang for flere lejere – f.eks. hvis du betjenes af en stor organisation eller en gruppe af kunder – skal du se Opret en [app med partneradgang til Microsoft 365 Defender API'er](api-partner-access.md). Hvis du ikke er sikker på, hvilken type adgang du skal bruge, kan du se [Introduktion](api-access.md).

Microsoft 365 Defender blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre Microsoft 365 Defender af alles funktioner. Denne API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge disse API'er:

- Opret et Azure Active Directory (Azure AD).
- Få et adgangstoken ved hjælp af dette program.
- Brug tokenet til at få adgang Microsoft 365 Defender API.

I denne artikel forklares det, hvordan du:

- Opret et Azure AD-program
- Få et adgangstoken til Microsoft 365 Defender
- Valider tokenet

> [!NOTE]
> Når du Microsoft 365 Defender API'en på vegne af en bruger, skal du have de korrekte programtilladelser og brugertilladelser.

> [!TIP]
> Hvis du har tilladelse til at udføre en handling på portalen, har du tilladelse til at udføre handlingen i API'en.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure som](https://portal.azure.com) en bruger med rollen **Global** administrator.

2. Gå til **Azure Active Directory** >  **App-registreringer** >  **Ny registrering**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="Indstillingen Ny registrering i ruden Administrer i Azure-portalen" lightbox="../../media/atp-azure-new-app2.png":::

3. Vælg et navn til programmet i formularen, og angiv følgende oplysninger for omdirigerings-URI'en, og vælg derefter **Registrer**.

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="Programregistreringsruden i Azure-portalen" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **Programtype:** Offentlig klient
   - **Omdiriger URI:** https://portal.azure.com

4. På din programside skal du vælge **API-tilladelserFår** >  >  tilladelse API'er, som **min organisation bruger** >, skriv **Microsoft Threat Protection**, og vælg **Microsoft Threat Protection**. Din app kan nu få adgang Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* er et tidligere navn til Microsoft 365 Defender og vises ikke på den oprindelige liste. Du skal begynde at skrive navnet i tekstfeltet for at få det vist.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="Ruden Din organisations API'er i Microsoft 365 Defender portal" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - Vælg **Delegerede tilladelser**. Vælg de relevante tilladelser for dit scenarie ( **f.eks. Hændelse.Læs**), og vælg **derefter Tilføj tilladelser**.

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="Ruden Delegerede tilladelser i Microsoft 365 Defender portal" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > Du skal vælge de relevante tilladelser til scenariet. *Læs alle hændelser er* blot et eksempel. Se afsnittet Tilladelser i den API, du vil ringe til **, for at** finde ud af, hvilken tilladelse du skal bruge.
    >
    > Hvis du f.eks [. vil køre avancerede forespørgsler](api-advanced-hunting.md), skal du vælge tilladelsen "Kør avancerede forespørgsler". Hvis [du vil isolere en enhed](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), skal du vælge tilladelsen "Isoler maskine".

5. Vælg **Giv administratorsamtykke**. Hver gang du tilføjer en tilladelse, skal du vælge **Giv administratorsamtykke** , før den træder i kraft.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="Ruden til godkendelse af administrator i Microsoft 365 Defender portal" lightbox="../../media/grant-consent-delegated.PNG":::

6. Optag dit program-id og dit lejer-id et sikkert sted. De er angivet under **Oversigt på** din programside.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="Ruden Oversigt i Microsoft 365 Defender portal" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Få et adgangstoken

Du kan finde flere Azure Active Directory om Azure Active Directory i [Azure AD-selvstudiet](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-using-powershell"></a>Få et adgangstoken ved hjælp af PowerShell

```PowerShell
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps } # Install the ADAL.PS package in case it's not already present

$tenantId = '' # Paste your directory (tenant) ID here.
$clientId = '' # Paste your application (client) ID here.
$redirectUri = '' # Paste your app's redirection URI

$authority = "https://login.windows.net/$tenantId"
$resourceUrl = 'https://api.security.microsoft.com'

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip

$response.AccessToken
```

## <a name="validate-the-token"></a>Valider tokenet

1. Kopiér og indsæt tokenet i [JWT for](https://jwt.ms) at afkode det.
1. Sørg for, at *rollerne* , der angives i den afkodede token, indeholder de ønskede tilladelser.

På følgende billede kan du se et afkodet token, der er købt fra en app, ```Incidents.ReadWrite.All```med ```Incidents.Read.All```, og ```AdvancedHunting.Read.All``` tilladelser:

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="Afsnittet tilladelser i ruden Afkodet token i Microsoft 365 Defender portal" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

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
- [Opret en "Hej verden"-app](api-hello-world.md)
- [Opret en app for at få adgang Microsoft 365 Defender uden en bruger](api-create-app-web.md)
- [Opret en app med partneradgang til flere lejere til Microsoft 365 Defender API'er](api-partner-access.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [OAuth 2.0-godkendelse til brugeradgang og API-adgang](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
