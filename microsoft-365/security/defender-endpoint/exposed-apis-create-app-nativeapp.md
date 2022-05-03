---
title: Brug Microsoft Defender for Endpoint API'er
ms.reviewer: ''
description: Få mere at vide om, hvordan du designer en oprindelig Windows app for at få programmatisk adgang til Microsoft Defender for Endpoint uden en bruger.
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
ms.openlocfilehash: aec4c7bdc0da76a6a52a8b8f19d89b8b54f3df9f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173473"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Brug Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> Avancerede jagtegenskaber er ikke inkluderet i Defender for Business. Se [Sammenlign Microsoft Defender til virksomheder med Microsoft Defender for Endpoint plan 1 og 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

På denne side beskrives det, hvordan du opretter et program for at få programmatisk adgang til Defender for Endpoint på vegne af en bruger.

Hvis du har brug for programadgang Microsoft Defender for Endpoint uden en bruger, skal du se [Access Microsoft Defender for Endpoint med programkontekst](exposed-apis-create-app-webapp.md).

Hvis du ikke er sikker på, hvilken adgang du har brug for, kan du læse [siden Introduktion](apis-intro.md).

Microsoft Defender for Endpoint fremviser mange af dataene og handlingerne via et sæt programmatiske API'er. Disse API'er giver dig mulighed for at automatisere arbejdsflow og innovation baseret på Microsoft Defender for Endpoint funktioner. API-adgangen kræver OAuth2.0-godkendelse. Du kan få flere oplysninger under [OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du gøre følgende for at bruge API'erne:

- Opret et AAD program
- Hent et adgangstoken ved hjælp af dette program
- Brug tokenet til at få adgang til Defender for Endpoint API

På denne side forklares det, hvordan du opretter et AAD program, får et adgangstoken til at Microsoft Defender for Endpoint og validere tokenet.

> [!NOTE]
> Når du får adgang til Microsoft Defender for Endpoint API på vegne af en bruger, skal du have den korrekte programtilladelse og brugertilladelse.
> Hvis du ikke kender brugertilladelser til Microsoft Defender for Endpoint, skal du se [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

> [!TIP]
> Hvis du har tilladelse til at udføre en handling på portalen, har du tilladelse til at udføre handlingen i API'en.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure](https://portal.azure.com) med en brugerkonto, der har rollen **Global administrator** .

2. Gå til **Azure Active Directory** \> **Appregistreringer** \> **Ny registrering**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Siden Appregistreringer på Microsoft Azure-portalen" lightbox="images/atp-azure-new-app2.png":::

3. Når siden **Registrer et program** vises, skal du angive registreringsoplysningerne for dit program:
   - **Navn** – Angiv et sigende programnavn, der skal vises for brugerne af appen.
   - **Understøttede kontotyper** – Vælg, hvilke konti dit program skal understøtte.

     <br>

     |Understøttede kontotyper|Beskrivelse|
     |---|---|
     |**Kun konti i denne organisationsmappe**|Vælg denne indstilling, hvis du opretter et line of business-program (LOB). Denne indstilling er ikke tilgængelig, hvis du ikke registrerer programmet i en mappe. <p> Denne indstilling knyttes til Azure AD kun en enkelt lejer. <p> Dette er standardindstillingen, medmindre du registrerer appen uden for en mappe. I de tilfælde, hvor appen er registreret uden for en mappe, er standarden Azure AD microsoft-konti med flere lejere og personlige Microsoft-konti.|
     |**Konti i en hvilken som helst organisationsmappe**|Vælg denne indstilling, hvis du vil målrette mod alle forretnings- og uddannelseskunder. <p> Denne indstilling knyttes til en Azure AD kun med flere lejere. <p> Hvis du har registreret appen som Azure AD kun en enkelt lejer, kan du opdatere den, så den Azure AD multilejer og tilbage til en enkelt lejer via bladet **Godkendelse**.|
     |**Konti i en hvilken som helst organisationsmappe og personlige Microsoft-konti**|Vælg denne indstilling for at målrette det bredeste sæt kunder. <p> Denne indstilling knyttes til Azure AD Microsoft-konti med flere lejere og personlige Microsoft-konti. <p> Hvis du har registreret appen som Azure AD Microsoft-konti med flere lejere og personlige Microsoft-konti, kan du ikke ændre dette i brugergrænsefladen. Du skal i stedet bruge programmanifesteditoren til at ændre de understøttede kontotyper.|

   - **Omdiriger URI (valgfrit)** – Vælg den type app, du bygger, **webklient** eller **offentlig klient (mobil & desktop),** og angiv derefter omdirigerings-URI'en (eller svar-URL-adressen) for dit program.

     - I forbindelse med webprogrammer skal du angive den grundlæggende URL-adresse til din app. Det kan f.eks. være URL-adressen til en webapp, `http://localhost:31544` der kører på din lokale computer. Brugerne skal bruge denne URL-adresse til at logge på et webklientprogram.

     - I forbindelse med offentlige klientprogrammer skal du angive den URI, der bruges af Azure AD til at returnere tokensvar. Angiv en værdi, der er specifik for dit program, f.eks `myapp://auth`. .

     Hvis du vil se specifikke eksempler på webprogrammer eller oprindelige programmer, kan du se vores [hurtige introduktioner](/azure/active-directory/develop/#quickstarts).

     Når du er færdig, skal du vælge **Registrer**.

4. Tillad, at dit program får adgang til Microsoft Defender for Endpoint, og tildel det tilladelsen "Læs beskeder":

   - På din programside skal du vælge **API-tilladelser** \> **Tilføj** **tilladelseS-API'er**\>, som min organisation bruger, > skrive **WindowsDefenderATP** og vælge **På WindowsDefenderATP**.

     > [!NOTE]
     > *WindowsDefenderATP* vises ikke på den oprindelige liste. Begynd at skrive navnet i tekstfeltet for at se det blive vist.

     :::image type="content" alt-text="tilføje tilladelse." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Vælg **Delegerede tilladelser** \> **Alert.Read** > vælg **Tilføj tilladelser**.

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="Programtypen og tilladelsesruderne" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > Vælg de relevante tilladelser. Læs beskeder er kun et eksempel.

     Eksempel:

     - Hvis du vil [køre avancerede forespørgsler](run-advanced-query-api.md), skal du vælge Kør tilladelse til **avancerede forespørgsler** .
     - Hvis du vil [isolere en enhed](isolate-machine.md), skal du vælge **Isoler computertilladelse** .
     - Hvis du vil finde ud af, hvilken tilladelse du har brug for, skal du se afsnittet **Tilladelser** i den API, du er interesseret i at kalde.

   - Vælg **Giv samtykke**.

      > [!NOTE]
      > Hver gang du tilføjer tilladelse, skal du vælge **Giv samtykke** , for at den nye tilladelse træder i kraft.

      :::image type="content" source="images/grant-consent.png" alt-text="Indstillingen Samlet administratorsamtykke" lightbox="images/grant-consent.png":::

5. Skriv dit program-id og dit lejer-id ned.

    Gå til **Oversigt** på din programside, og kopiér følgende oplysninger:

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Det oprettede app-id"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Hent et adgangstoken

Du kan få flere oplysninger om AAD tokens [i Azure AD selvstudium](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>Brug af C\#

- Kopiér/indsæt klassen nedenfor i dit program.
- Brug **metoden AcquireUserTokenAsync** med dit program-id, lejer-id, brugernavn og adgangskode for at hente et token.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>Valider tokenet

Kontrollér, at du har fået et korrekt token:

- Kopiér/indsæt i [JWT](https://jwt.ms) det token, du fik i det forrige trin, for at afkode det.
- Valider, at du får et 'scp'-krav med de ønskede apptilladelser.
- På skærmbilledet nedenfor kan du se et afkodet token, der er hentet fra appen, i selvstudiet:

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="Siden til validering af token" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

- Vælg den API, du vil bruge – [Understøttede Microsoft Defender for Endpoint API'er](exposed-apis-list.md).
- Angiv godkendelsesheaderen i den HTTP-anmodning, du sender til "Ihændehaver {token}" (ihændehaver er autorisationsskemaet).
- Tokenets udløbstid er 1 time (du kan sende mere end én anmodning med det samme token).

- Eksempel på afsendelse af en anmodning om at få vist en liste over beskeder **ved hjælp af C#**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Se også

- [Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- [Adgang Microsoft Defender for Endpoint med programkontekst](exposed-apis-create-app-webapp.md)
