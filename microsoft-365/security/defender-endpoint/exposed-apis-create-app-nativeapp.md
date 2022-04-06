---
title: Brug Microsoft Defender for Endpoint API'er
ms.reviewer: ''
description: Lær at designe en indbygget Windows app for at få programmeringsadgang til Microsoft Defender for Endpoint uden en bruger.
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
ms.openlocfilehash: 752e08d3fddb28b7d30122281009e54fc235b129
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471203"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>Brug Microsoft Defender for Endpoint API'er

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

Denne side beskriver, hvordan du opretter et program for at få programadgang til Defender for Endpoint på vegne af en bruger.

Hvis du har brug for programmeringsadgang Microsoft Defender for Endpoint en bruger, skal du [se Access Microsoft Defender for Endpoint med programkontekst](exposed-apis-create-app-webapp.md).

Hvis du ikke er sikker på, hvilken adgang du skal bruge, kan du læse [siden Introduktion](apis-intro.md).

Microsoft Defender for Endpoint blotlægger mange af sine data og handlinger via et sæt programmerings-API'er. Disse API'er gør det muligt at automatisere pengestrømme og forny baseret på Microsoft Defender for Endpoint funktioner. API-adgang kræver OAuth2.0-godkendelse. Du kan finde flere oplysninger [under OAuth 2.0-godkendelseskode Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Generelt skal du følge disse trin for at bruge API'er:

- Opret et AAD program
- Få et adgangstoken ved hjælp af dette program
- Brug tokenet til at få adgang til Defender for Endpoint API

Denne side forklarer, hvordan du opretter AAD et program, får et adgangstoken til at Microsoft Defender for Endpoint og validere tokenet.

> [!NOTE]
> Når du Microsoft Defender for Endpoint api'en på vegne af en bruger, skal du have de korrekte programtilladelser og brugertilladelser.
> Hvis du ikke har kendskab til brugertilladelser på Microsoft Defender for Endpoint, skal du se [Administrere portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

> [!TIP]
> Hvis du har tilladelse til at udføre en handling på portalen, har du tilladelse til at udføre handlingen i API'en.

## <a name="create-an-app"></a>Opret en app

1. Log på [Azure med](https://portal.azure.com) en brugerkonto, der har rollen **som global** administrator.

2. Gå til **Azure Active Directory** \> **appregistreringer** \> **Ny registrering**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="Siden Appregistreringer i Microsoft Azure portal" lightbox="images/atp-azure-new-app2.png":::

3. Når siden **Registrer et** program vises, skal du angive registreringsoplysningerne for dit program:
   - **Navn** – Angiv et beskrivende programnavn, der vises for brugere af appen.
   - **Understøttede kontotyper** – Vælg, hvilke konti du vil have dit program til at understøtte.

     <br>

     |Understøttede kontotyper|Beskrivelse|
     |---|---|
     |**Kun konti i denne organisationsmappe**|Vælg denne indstilling, hvis du opbygger et line of business -program (LOB). Denne indstilling er ikke tilgængelig, hvis du ikke registrerer programmet i en mappe. <p> Denne indstilling er kun en enkelt lejer i Azure AD. <p> Dette er standardindstillingen, medmindre du registrerer appen uden for en mappe. I tilfælde, hvor appen er registreret uden for en mappe, er standarden Azure AD-konti med flere lejere og personlige Microsoft-konti.|
     |**Konti i ethvert organisationskatalog**|Vælg denne indstilling, hvis du gerne vil målrette alle erhvervs- og uddannelseskunder. <p> Denne indstilling er kun tilgængelig for flere lejere i Azure AD. <p> Hvis du har registreret appen som en enkelt lejer i Azure AD, kan du opdatere den til at være Azure AD med flere lejere og tilbage til enkelt lejer via **godkendelses bladet** .|
     |**Konti i ethvert organisationskatalog og personlige Microsoft-konti**|Vælg denne indstilling for at målrette det bredeste sæt af kunder. <p> Denne indstilling er kort til Azure AD-konti med flere lejere og personlige Microsoft-konti. <p> Hvis du har registreret appen som Azure AD-konti med flere lejere og personlige Microsoft-konti, kan du ikke ændre dette i brugergrænsefladen. I stedet skal du bruge program manifesteditoren til at ændre de understøttede kontotyper.|

   - **Omdiriger URI (** valgfrit) – Vælg den type app, du bygger, **Web** - eller **Offentlig klient (mobil & desktop),** og angiv derefter URI'en til omdirigering (eller svar-URL) til dit program.

     - For webprogrammer skal du angive den grundlæggende URL-adresse til din app. Det kan f.eks. være URL-adressen til en webapp, `http://localhost:31544` der kører på din lokale computer. Brugerne skal bruge denne URL-adresse til at logge på et webklientprogram.

     - Til offentlige klientprogrammer skal du angive den URI, der bruges af Azure AD til at returnere tokensvar. Angiv en værdi, der er specifik for dit program, f.eks `myapp://auth`. .

     Hvis du vil se specifikke eksempler for webprogrammer eller oprindelige programmer, kan du se [vores hurtigstarter](/azure/active-directory/develop/#quickstarts).

     Når du er færdig, skal du **vælge Registrer**.

4. Giv dit program adgang til Microsoft Defender for Endpoint og tildel "Læse vigtige beskeder"-tilladelse:

   - På programsiden skal  du vælge **API-tilladelser** Tilføj **tilladelses-API'er** \> \>, som min organisation bruger > type **WindowsDefenderATP** og vælge **på WindowsDefenderATP**.

     > [!NOTE]
     > *WindowsDefenderATP* vises ikke på den oprindelige liste. Begynd at skrive navnet i tekstfeltet for at se det.

     :::image type="content" alt-text="tilføj tilladelse." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - Vælg **Delegated permissions** \> **Alert.Read** > **vælg Add permissions**.

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="Ruder for programtype og tilladelser" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > Vælg de relevante tilladelser. Vigtige beskeder om læsning er kun et eksempel.

     Eksempel:

     - Hvis [du vil køre avancerede forespørgsler](run-advanced-query-api.md), skal du **vælge Tilladelsen Kør avancerede** forespørgsler.
     - Vælg [Isoler computertilladelse](isolate-machine.md) for at **isolere en** enhed.
     - Se afsnittet Tilladelser i den API, du er  interesseret i at ringe til, for at finde ud af, hvilken tilladelse du skal bruge.

   - Vælg **Giv samtykke**.

      > [!NOTE]
      > Hver gang du tilføjer tilladelse, skal du vælge Giv **samtykke,** før den nye tilladelse træder i kraft.

      :::image type="content" source="images/grant-consent.png" alt-text="Indstillingen Godkendelse af hovedadministrator" lightbox="images/grant-consent.png":::

5. Skriv dit program-id og dit lejer-id ned.

    På programsiden skal du gå **til Oversigt** og kopiere følgende oplysninger:

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="Det oprettede app-id"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>Få et adgangstoken

Du kan finde flere AAD om AAD i [Azure AD- selvstudium](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>Brug af C\#

- Kopiér/Indsæt nedenstående klasse i dit program.
- Brug **metoden AcquireUserTokenAsync** med dit program-id, lejer-id, brugernavn og adgangskode til at få et token.

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

- Kopiér/indsæt [i JWT](https://jwt.ms) den token, du fik i forrige trin for at afkode den.
- Valider, at du får et "scp"-krav med de ønskede apptilladelser.
- I skærmbilledet nedenfor kan du se et afkodet token, der er erhvervet fra appen, i selvstudiet:

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="Siden til validering af token" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>Brug tokenet til at få adgang til Microsoft Defender for Endpoint API

- Vælg den API, du vil bruge – [understøttes Microsoft Defender for Endpoint API'er](exposed-apis-list.md).
- Angiv godkendelseshovedet i DEN HTTP-anmodning, du sender til "Bearer {token}" (Bearer er godkendelsesskemaet).
- Udløbsdatoen for tokenet er 1 time (du kan sende mere end én anmodning med samme token).

- Eksempel på afsendelse af en anmodning om at få en liste over beskeder **ved hjælp af C#**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>Se også

- [Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
- [Access Microsoft Defender for Endpoint med programkontekst](exposed-apis-create-app-webapp.md)
