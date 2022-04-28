---
title: Konfigurer Microsoft 365 supportintegration med Azure AD Auth-token
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Omfangsbaseret vejledning til installation og konfiguration af certificerede programmer for ServiceNow.
ms.openlocfilehash: d3991355779228cf1562e23ddd0e97cb37225a43
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093740"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Konfigurer Microsoft 365 supportintegration med Azure AD Auth-token

## <a name="prerequisites-azure-ad-auth-token"></a>Forudsætninger (Azure AD Auth Token)

Disse forudsætninger er nødvendige for at konfigurere Microsoft 365 understøtte integration.

1. \[AAD administrator\] Opret Azure AD-program til udgående data under din Microsoft 365 lejer.

    1. Log på Azure Portal med dine Microsoft 365 lejerlegitimationsoplysninger, og gå til [siden Appregistreringer](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) for at oprette et nyt program.

    2. Vælg **Kun konti i denne organisationsmappe (kun{Microsoft-365-tenant-name} – enkelt lejer),** og vælg **Registrer**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. Gå til **Godkendelse,** og vælg **Tilføj en platform**. Vælg indstillingen **Web,** og angiv URL-adressen til omdirigering: `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. Hent programklient-id'et, og opret en klienthemmelighed, og hent denne værdi.

1. \[AAD administrator\] Opret et Azure AD-program til rest-API'en under din Microsoft 365 lejer.

    1. Log på [Azure Portal](https://portal.azure.com/) med dine Microsoft 365 lejerlegitimationsoplysninger, og gå til siden Appregistreringer for at oprette et nyt program.

    1. Vælg **kun Konti i denne organisationsmappe {(kun Microsoft-365-tenant-name} – enkelt lejer).**

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. Hent programklient-id'et, og opret en klienthemmelighed, og hent denne værdi.

1. \[AAD administrator\] Opret et Azure AD-program til restbruger under din Microsoft 365 lejer.

    1. Log på [Azure Portal](https://portal.azure.com/) med dine Microsoft 365 lejerlegitimationsoplysninger, og gå til siden Appregistreringer for at oprette et nyt program.

    1. Vælg **kun Konti i denne organisationsmappe {(kun Microsoft-365-tenant-name} – enkelt lejer).**

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. Hent programklient-id'et, og opret en klienthemmelighed, og hent denne værdi.

1. \[ServiceNow Admin\] Konfigurer udgående OAuth-udbyder i ServiceNow.

    Hvis omfanget ikke er angivet til **Global**, skal du gøre det ved at gå til **Indstillinger &gt; Udviklerprogrammer &gt;** og skifte til **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafisk brugergrænseflade, tekst, program, chat eller tekstmeddelelse Beskrivelse genereret automatisk":::

1. Gå til **System OAuth &gt; Application Registry**.

1. Opret et nyt program ved hjælp af indstillingen **Forbind til en OAuth-provider fra tredjepart**, og angiv følgende værdier:

    - Klient-id: Dette er klient-id'et for det program, der er oprettet i Trin 1 for Forudsætninger (Azure AD Auth Token).\#

    - Klienthemmelighed: Dette er værdien for klienthemmeligheden for det program, der er oprettet i Trin 1 for Forudsætninger (Azure AD Auth Token).\#

    - Standardtildelingstype: Klientlegitimationsoplysninger

    - URL-adresse til token: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - URL-adresse til omdirigering: `https://{service-now-instance-name``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Hvis du vil konfigurere OIDC-udbyderen i ServiceNow, skal du se [onlinedokumentationen](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Hvis omfanget ikke er angivet til **Global**, **skal du gå til Indstillinger &gt; Udviklerprogrammer &gt;** og skifte til **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafisk brugergrænseflade, tekst, program, chat eller tekstmeddelelse Beskrivelse genereret automatisk":::

1. Gå til **System OAuth &gt; Application Registry**.

1. Vælg **Ny**, og vælg derefter **Opret nyt Open ID Forbind Provider**.

1. I **konfiguration af OAuth OIDC-provider** skal du vælge **Søg** og oprette en ny OIDC-providerkonfiguration under **oidcproviderconfiguration.list\_\_** med disse værdier:

    - OIDC-provider: **{TenantName\_} Azure** (eksempel: Contoso Azure)

    - URL-adresse til OIDC-metadata: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **Bruger-id**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Grafisk brugergrænseflade, tekst, programbeskrivelse genereret automatisk":::

1. Opret et nyt program ved at vælge **Konfigurer en OIDC-provider for at bekræfte id-tokens** med disse værdier:

    - Navn: **{TenantName\_}\_applicationinboundapi\_\_** (f.eks. contosoapplicationinboundapi\_\_\_)

    - Klient-id: Klient-id'et for det program, der er oprettet i Trin 3 for Forudsætninger (Azure AD Auth Token).\#

    - Klienthemmelighed: Apphemmeligheden for det program, der er oprettet i forudsætningerne (Azure AD Auth Token) trin \#3.

    - Konfiguration af OAuth OIDC-provider: Den OIDC-provider, der blev oprettet i det forrige trin

    - URL-adresse til omdirigering: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Opret integrationsbrugere.

    Du skal angive en integrationsbruger. Hvis du ikke har en eksisterende integrationsbruger, eller hvis du vil oprette en specifikt til denne integration, skal du gå til **Organisationsbrugere &gt;** for at oprette en ny bruger. Værdien af **bruger-id'et** er det programklient-id, der er oprettet i [Forudsætninger (Azure AD Auth Token)](#prerequisites-azure-ad-auth-token).

    Hvis du opretter en ny integrationsbruger, skal du markere indstillingen **Kun adgang til webtjenesten** . Du skal også tildele denne bruger rollen **incidentmanager\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereret automatisk":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[VALGFRI Tillad\], at tjenestens IP-adresser Microsoft 365 supportintegration

Hvis din virksomhed begrænser internetadgangen med dine egne politikker, skal du aktivere netværksadgang for tjenesten Microsoft 365 understøtte integration ved at tillade IP-adresserne nedenfor for både indgående og udgående API-adgang.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Denne terminalkommando viser alle aktive IP-adresser for tjenesten til Microsoft 365 supportintegration:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Konfigurer programmet til understøttelse af Microsoft 365

Programmet til understøttelse af Microsoft 365 kan konfigureres under Microsoft 365 support.

Disse trin er påkrævet for at konfigurere integrationen mellem din ServiceNow-forekomst og Microsoft 365 support.

1. \[ServiceNow Admin\] Skift området til **Microsoft 365 supportintegration**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Grafisk brugergrænseflade, tabelbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Gå til **Microsoft 365 Support &gt; setup** for at åbne integrationsarbejdsprocessen.

    > [!NOTE]
    > Hvis du får vist fejlen "Læs handling mod "oauthentity\_" fra området 'xmiomsm365assis\_\_\_' er blevet afvist på grund af tabellens adgangspolitik på tværs af områder," skyldes det din tabeladgangspolitik. Du skal sørge for, at **Alle programområder &gt; Kan læse** er markeret for tabellens\_ godkendelse.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Vælg **Acceptér** samtykkeprompten for at fortsætte.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Konfigurer miljø- og installationstypen.
    Hvis denne installation er på et testmiljø, skal du vælge indstillingen Dette er et testmiljø. Du kan hurtigt deaktivere denne indstilling, når installationen er fuldført, og alle dine test er fuldført senere.
    Hvis din forekomst tillader basisgodkendelse for indgående forbindelser, skal du vælge Ja og se [den grundlæggende godkendelsesproces](servicenow-basic-authentication.md). Ellers skal du vælge **Nej** og klikke på **Start installation**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Angiv dit Microsoft 365 lejerdomæne.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Konfigurer udgående OAuth-provider.
    1. Konfigurer udgående OAuth-provider.
    1. Når du har fuldført instruktionerne i afsnittet Forudsætninger, skal du klikke på Udført. Ellers skal du følge vejledningen i guiden for at oprette den nødvendige programregistrering i AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::
    1. Registrer ServiceNow OAuth-appen.
    1. Når du har fuldført instruktionerne i afsnittet Forudsætninger, skal du vælge den nyoprettede OAuth-programregistrering og klikke på Næste. Ellers skal du følge instruktionerne for at oprette enheden i ServiceNow og derefter vælge den nye programregistrering.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Konfigurer indgående indstillinger.
    1. Konfigurer appen Indgående AAD.
    1. Når du har fuldført instruktionerne i afsnittet Forudsætninger, skal du klikke på Udført for at gå til næste trin. Ellers skal du følge vejledningen for at oprette AAD appregistrering til indgående forbindelse.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::
    1. Konfigurer ServiceNow External OpenID Forbind Provider (OIDC Provider).
    1. Når du har fuldført instruktionerne i afsnittet Forudsætninger, skal du vælge det nyoprettede objekt og klikke på Udført. Ellers skal du følge vejledningen for at oprette enheden i ServiceNow og derefter vælge den nye appregistrering for ekstern OIDC-provider.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::
    1. Konfigurer AAD appregistrering for indgående integrationsbruger.
    1. Når du har fuldført instruktionerne i afsnittet Forudsætninger, skal du klikke på Udført for at gå til næste trin. Ellers skal du følge vejledningen for at oprette AAD appregistrering for indgående REST-bruger (integrationsbruger).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::
    1. Konfigurer integrationsbrugeren.
    1. Når du har fuldført instruktionerne i afsnittet Forudsætninger, skal du vælge det nyoprettede objekt og klikke på Næste. Ellers skal du følge vejledningen for at oprette integrationsbrugeren i ServiceNow og derefter vælge enheden.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[Microsoft 365 lejeradministrator\] Fuldfør integrationen.

    Kontrollér, at oplysningerne nedenfor er korrekte. Undlad at vælge **Næste** på nuværende tidspunkt.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

    1. Gå til **Microsoft 365 Administration Portal &gt; Indstillinger &gt; Organisationsindstillinger &gt; Organisationsprofiler**.

    1. Konfigurer indstillingerne for supportintegration:

    Vælg fanen **Grundlæggende oplysninger** > **Intern supportværktøjTjeneste** > **,** og angiv værdien **for udgående app-id** i feltet **Program-id for at udstede godkendelsestoken** . Dette udgående app-id er på trin 6 – fuldfør integrationen, som blev oprettet i [Forudsætninger (Azure AD Auth Token)](#prerequisites-azure-ad-auth-token).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

    1. På fanen **Lagre** skal du vælge **Nyt lager** og opdatere det med følgende indstillinger:

    - Lager: Værdien for **lager-id'et** fra "Trin 6 – Fuldfør integrationen".

    - Slutpunkt: **Slutpunktsværdien** fra "Trin 6 – Fuldfør integrationen".

    - Godkendelsestype: Vælg **AAD Godkendelse**.

    - Klient-id: Værdien **for klient-id'et** fra trin 6 – fuldfør integrationen.

    - Klienthemmelighed: Hemmeligheden for den indgående OAuth-provider, der blev oprettet i forudsætningerne (Azure AD Auth Token) trin \#2.

    - Rest username: Værdien **for Brugernavn** fra Trin 6 – Fuldfør integrationen, som er **klient-id'et** for det program, der er oprettet i Trin 3 (Azure AD Auth Token).\#

    - Adgangskode for restbruger: App-hemmeligheden for det program, der blev oprettet i Trin 3 (Azure AD Auth Token).\#

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereret automatisk":::

    1. Gå tilbage til ServiceNow.

    1. Vælg **Næste** for at fuldføre integrationen.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::
    Den Microsoft 365 supportintegrationsapp udfører test for at sikre, at integrationen fungerer. Hvis der er problemer med konfigurationen, forklares det, hvad der skal løses, i en fejlmeddelelse. Ellers er programmet klar.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailbeskrivelse genereret automatisk":::

1. \[ServiceNow Admin\] Aktivér Microsoft-supportintegration for en eksisterende bruger.

    Microsoft 365 supportintegration er aktiveret for brugeren med en af disse roller:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[VALGFRI\] Linket Brugeren med rollen xmiomsm365assis.administrator\_\_\]\_ link Microsoft 365 administratorkonto.\[

    Hvis en bruger har rollen xmiomsm365assis.administrator\_\_\_ og bruger forskellige Microsoft 365 konti til at administrere en Microsoft 365 supportsag, skal vedkommende gå til Microsoft 365 supportlinkkonto &gt; for at konfigurere deres Microsoft 365 administratormail.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Grafisk brugergrænseflade, tekst, programbeskrivelse genereret automatisk":::
