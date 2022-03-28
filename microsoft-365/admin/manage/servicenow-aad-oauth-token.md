---
title: Konfigurere Microsoft 365 supportintegration med Azure AD Auth-token
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
description: Omfangsstyret certificeret programinstallation og konfigurationsvejledning for ServiceNow.
ms.openlocfilehash: 9f9985e07989f168f9b27dde1c1d574813c3f349
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596916"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>Konfigurere Microsoft 365 supportintegration med Azure AD Auth-token

## <a name="prerequisites-azure-ad-auth-token"></a>Forudsætninger (Azure AD-godkendelsestoken)

Disse forudsætninger er nødvendige for at konfigurere Microsoft 365 supportintegration.

1. \[AAD administrator\] Opret Azure AD-programmet til udgående under Microsoft 365 lejer.

    1. Log på Azure-portalen med dine Microsoft 365 lejerlegitimationsoplysninger, og gå til [siden Appregistreringer](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) for at oprette et nyt program.

    2. Vælg **Konti kun i denne organisationsmappe (kun{Microsoft-365-tenant-name} – enkelt lejer),** og vælg **Registrer**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. Gå til **Godkendelse,** og vælg **Tilføj en platform**. Vælg **webindstillingen** , og angiv URL-adressen til omdirigeringen: `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. Hent Programklient-id'et, og opret en klienthemmelighed, og få denne værdi.

1. \[AAD administrator\] Opret et Azure AD-program til Rest API under Microsoft 365 lejer.

    1. Log på [Azure-portalen med](https://portal.azure.com/) dine Microsoft 365-lejerlegitimationsoplysninger, og gå til siden Appregistreringer for at oprette et nyt program.

    1. Vælg **kun Konti i denne organisationsmappe {(kun Microsoft-365-tenant-name} – Enkelt lejer)**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. Hent Programklient-id'et, og opret en klienthemmelighed, og få denne værdi.

1. \[AAD administrator\] Opret et Azure AD-program til restbruger under Microsoft 365 lejer.

    1. Log på [Azure-portalen med](https://portal.azure.com/) dine Microsoft 365-lejerlegitimationsoplysninger, og gå til siden Appregistreringer for at oprette et nyt program.

    1. Vælg **kun Konti i denne organisationsmappe {(kun Microsoft-365-tenant-name} – Enkelt lejer)**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. Hent Programklient-id'et, og opret en klienthemmelighed, og få denne værdi.

1. \[ServiceNow-administrator\] Konfigurer den udgående OAuth-udbyder i ServiceNow.

    Hvis omfanget ikke er angivet til **Global**, kan du gøre det ved at navigere **Indstillinger udviklerprogrammer &gt; &gt;** og skifte til **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafisk brugergrænseflade, tekst, program, chat eller sms-beskrivelse genereres automatisk":::

1. Gå til **System OAuth-programregistreringsdatabasen&gt;**.

1. Opret et nyt program ved hjælp **Forbind til en tredjeparts OAuth-udbyder**, og indtastning af disse værdier:

    - Klient-id: Dette er klient-id'et for programmet, der er oprettet i Forudsætninger (Azure AD Auth-token) trin \#1.

    - Klienthemmelighed: Dette er værdien Klienthemmelighed for programmet, der er oprettet i Forudsætninger (Azure AD Auth-token) trin \#1.

    - Standardtype for tildeling: klientlegitimationsoplysninger

    - Url-adresse til token: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - Omdiriger URL-adresse: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereres automatisk":::

1. \[ServiceNow-administrator\] Hvis du vil konfigurere OIDC-udbyderen i ServiceNow, skal du se [onlinedokumentationen](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    Hvis omfanget ikke er angivet til **Global**, skal du gå **til Indstillinger &gt; Udviklerprogrammer &gt; og** skifte til **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="Grafisk brugergrænseflade, tekst, program, chat eller sms-beskrivelse genereres automatisk":::

1. Gå til **System OAuth-programregistreringsdatabasen&gt;**.

1. Vælg **Ny**, og vælg derefter **Opret nyt Open ID Forbind Provider**.

1. I **OAuth OIDC-providerkonfiguration** skal du  vælge Søg og oprette en ny OIDC-providerkonfiguration under **oidcproviderconfiguration.list\_\_** med disse værdier:

    - OIDC-udbyder: **{TenantName\_} Azure** (eksempel: Contoso Azure)

    - URL-adresse til OIDC-metadata: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **Bruger-id**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="Grafisk brugergrænseflade, tekst, programBeskrivelse genereres automatisk":::

1. Opret et nyt program ved at vælge **Konfigurer en OIDC-udbyder for at bekræfte id-tokens** med disse værdier:

    - Navn: **{TenantName\_}\_applicationinboundapi\_\_** (eksempel: contosoapplicationinboundapi\_\_\_)

    - Klient-id: Klient-id'et for det program, der er oprettet i Forudsætninger (Azure AD Auth Token) trin \#2.

    - Klienthemmelighed: Apphemmelighed for programmet oprettet i Forudsætninger (Azure AD Auth Token) trin \#2.

    - OAuth OIDC-providerkonfiguration: OIDC-provideren, der blev oprettet i det forrige trin

    - Omdiriger URL-adresse: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereres automatisk":::

1. \[ServiceNow Administrator Opret\] integrationsbrugere.

    Du skal angive en integrationsbruger. Hvis du ikke har en eksisterende integrationsbruger, eller hvis du vil oprette en, der specifikt er til denne integration, skal du gå til **Organisationsbrugere &gt;** for at oprette en ny bruger. Værdien af **bruger-id'et er** det programklient-id, der er oprettet [i Forudsætninger (Azure AD Auth-token)](#prerequisites-azure-ad-auth-token).

    Hvis du opretter en ny integrationsbruger, skal du kontrollere **indstillingen Kun adgang til webtjeneste** . Du skal også tildele denne bruger med rollen **Hændelsesmanager\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereres automatisk":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[VALGFRIt\] Tillad tjenestens IP-adresser at understøtte Microsoft 365 supportintegration

Hvis din virksomhed begrænser internetadgang med dine egne politikker, skal du aktivere netværksadgang for tjenesten for Microsoft 365-supportintegration ved at tillade IP-adresserne nedenfor for både indgående og udgående API-adgang.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> Denne terminalkommando viser alle aktive IP'er for tjenesten til Microsoft 365 supportintegration:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>Konfigurere Microsoft 365 til supportintegration

Support Microsoft 365 program til support kan konfigureres under Microsoft 365 support.

Disse trin er nødvendige for at konfigurere integrationen mellem din ServiceNow-forekomst og Microsoft 365 support.

1. \[ServiceNow Administrator\] Skift omfanget til at **Microsoft 365 supportintegration**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="Grafisk brugergrænseflade, tabelbeskrivelse genereres automatisk":::

1. \[ServiceNow Administrator Gå\] til konfiguration **Microsoft 365 support for at &gt;** åbne integrationsarbejdsprocessen.

    > [!NOTE]
    > Hvis du får vist fejlen "Læsehandlingen mod "oauthentity\_" fra området "xmiomsm365assis\_\_" er blevet afvist på grund af tabellens adgangspolitik for alle områder", så skyldes det din tabels\_ adgangspolitik. Du skal sørge for **, at Alle programomfanget &gt;** Kan læse er markeret for tabellens oauthentity\_.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[ServiceNow-administrator\] Vælg **Accepter** samtykkeprompten for at fortsætte.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[ServiceNow-administrator\] Konfigurer miljøet og konfigurationstypen.
    Hvis denne installation er i et testmiljø, skal du vælge indstillingen Dette er et testmiljø. Du vil hurtigt kunne deaktivere denne indstilling, når konfigurationen er fuldført, og alle dine test er fuldført på et senere tidspunkt.
    Hvis din forekomst tillader basisgodkendelse for indgående forbindelser, skal du vælge Ja og se [konfigurationsprocessen Grundlæggende godkendelse](servicenow-basic-authentication.md). Ellers skal du **vælge Nej** og klikke **på Start installationen**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[ServiceNow Administrator\] Angiv dit Microsoft 365 lejerdomæne.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[ServiceNow-administrator\] Konfigurer udgående OAuth-udbyder.
    1. Konfigurere udgående OAuth-udbyder.
    1. Når du har fuldført vejledningen i afsnittet forudsætninger, skal du klikke på Udført. Ellers skal du følge vejledningen i guiden for at oprette den nødvendige programregistrering AAD.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::
    1. Registrer ServiceNow OAuth-appen.
    1. Når du har fuldført vejledningen i afsnittet forudsætninger, skal du markere den nyoprettede OAuth-programregistrering og klikke på Næste. Ellers skal du følge vejledningen for at oprette enheden i ServiceNow og derefter vælge den nye programregistrering.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[ServiceNow-administrator\] Konfigurer indgående indstillinger.
    1. Konfigurere den indgående AAD app.
    1. Når du har udført vejledningen i afsnittet forudsætninger, skal du klikke på Udført for at gå til næste trin. Ellers skal du følge vejledningen for at oprette AAD appregistrering for indgående forbindelse.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::
    1. Konfigurere ServiceNow External OpenID Forbind Provider (OIDC-udbyder).
    1. Når du har fuldført vejledningen i afsnittet Forudsætninger, skal du vælge den nyoprettede enhed og klikke på Udført. Ellers skal du følge vejledningen for at oprette enheden i ServiceNow og derefter vælge den nye registrering for den eksterne OIDC-udbyderapp.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::
    1. Konfigurer appregistreringen AAD for indgående integrationsbruger.
    1. Når du har udført vejledningen i afsnittet forudsætninger, skal du klikke på Udført for at gå til næste trin. Ellers skal du følge vejledningen for at oprette AAD appregistrering for indgående REST-bruger (integrationsbruger).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::
    1. Konfigurere integrationsbrugeren.
    1. Når du har fuldført vejledningen i afsnittet Forudsætninger, skal du vælge den nyoprettede enhed og klikke på Næste. Ellers skal du følge vejledningen for at oprette integrationsbrugeren i ServiceNow og derefter vælge enheden.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[Microsoft 365 lejeradministrator\] Fuldfør integrationen.

    Kontrollér, at nedenstående oplysninger er korrekte. Vælg IKKE Næste **på** nuværende tidspunkt.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

    1. Gå til **Microsoft 365 Administration Portal &gt; Indstillinger &gt; Organisationsindstillinger &gt; Organisationsprofiler**.

    1. Konfigurer indstillingerne for supportintegration:

    Vælg fanen **Grundlæggende oplysninger** > **værktøjet Intern** **supportServiceNow** > , og angiv værdien for Udgående **app-id** i feltet Program-id til udstedelse af **godkendelsestoken**. Dette udgående app-id er på trin 6 – Fuldfør integrationen, som blev oprettet i Forudsætninger [(Azure AD Auth-token)](#prerequisites-azure-ad-auth-token).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

    1. På fanen **Lager skal** du vælge **Nyt lager og** opdatere det med følgende indstillinger:

    - Lager: Værdien **for lager-id'et** fra "Trin 6 – Fuldfør integrationen".

    - Slutpunkt: **Slutpunktsværdien** fra "Trin 6 – Fuldfør integrationen".

    - Godkendelsestype: **Vælg AAD Auth**.

    - Klient-id: **Værdien for** klient-id'et fra trin 6 – fuldfør integrationen.

    - Klienthemmelighed: Hemmeligheden bag den indgående OAuth-udbyder, der blev oprettet i Forudsætninger (Azure AD Auth Token) trin \#2.

    - Resten brugernavn: Værdien  brugernavn fra trin 6 – Fuldfør integrationen, som er klient-id'et for programmet, der er oprettet i Forudsætninger (Azure AD Auth-token) trin  \#3.

    - Resten af brugeradgangskoden: Apphemmelighed for det program, der blev oprettet i Forudsætninger (Azure AD Auth-token) trin \#3.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="Grafisk brugergrænseflade, programbeskrivelse genereres automatisk":::

    1. Gå tilbage til ServiceNow.

    1. Vælg **Næste** for at fuldføre integrationen.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::
    Appen Microsoft 365-supportintegration udfører tests for at sikre, at integrationen fungerer. Hvis der er et problem med konfigurationen, forklarer en fejlmeddelelse, hvad der skal rettes. Ellers er programmet klar.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="Grafisk brugergrænseflade, tekst, program, mailBeskrivelse genereres automatisk":::

1. \[ServiceNow-administrator\] Aktivér Microsoft-supportintegration for en eksisterende bruger.

    Microsoft 365 er aktiveret for den bruger, der har en af disse roller:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[VALGFRI\] \[Brugeren med rolle xmiomsm365assis.administrator\_\_\_ link link\] Microsoft 365 administratorkonto.

    Hvis en bruger har rollen xmiomsm365assis.administrator\_\_\_ og bruger forskellige Microsoft 365-konti til at administrere en Microsoft 365-supportsag, skal de gå til Microsoft 365-supportlinkkonto &gt; for at konfigurere deres Microsoft 365-administratormail.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="Grafisk brugergrænseflade, tekst, programBeskrivelse genereres automatisk":::
