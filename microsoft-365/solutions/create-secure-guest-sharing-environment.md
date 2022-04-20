---
title: Opret et sikkert gæstedelingsmiljø
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-security-compliance
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om tilgængelige muligheder for at oprette et sikkert gæstedelingsmiljø i Microsoft 365, hvilket giver gæsteadgang til forbedret samarbejde.
ms.openlocfilehash: 5b6f27bd81a47a92926cebeef89de11ed78fcd3d
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948347"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Opret et sikkert gæstedelingsmiljø

I denne artikel gennemgår vi en række forskellige muligheder for at oprette et sikkert gæstedelingsmiljø i Microsoft 365. Dette er eksempler, der giver dig en idé om de tilgængelige indstillinger. Du kan bruge disse procedurer i forskellige kombinationer for at imødekomme organisationens behov for sikkerhed og overholdelse af angivne standarder.

Denne artikel indeholder:

- Konfiguration af multifaktorgodkendelse for gæster.
- Konfiguration af vilkår for anvendelse for gæster.
- Konfiguration af kvartalsvise gæsteadgangsgennemgange for jævnligt at validere, om gæster fortsat har brug for tilladelser til teams og websteder.
- Begrænsning af gæster til webadgang for ikke-administrerede enheder.
- Konfiguration af en timeoutpolitik for session for at sikre, at gæster godkendes dagligt.
- Oprettelse af en type følsomme oplysninger for et projekt, der er meget følsomt.
- Automatisk tildeling af en følsomhedsmærkat til dokumenter, der indeholder en type følsomme oplysninger.
- Fjerner automatisk gæsteadgang fra filer med en følsomhedsmærkat.

Nogle af de muligheder, der er beskrevet i denne artikel, kræver, at gæster har en konto i Azure Active Directory. Hvis du vil sikre, at gæster er inkluderet i mappen, når du deler filer og mapper med dem, skal du bruge [SharePoint og OneDrive integration med Azure AD B2B Preview](/sharepoint/sharepoint-azureb2b-integration-preview).

Bemærk, at vi ikke diskuterer aktivering af indstillinger for gæstedeling i denne artikel. Se [Samarbejde med personer uden for din organisation](collaborate-with-people-outside-your-organization.md) for at få oplysninger om aktivering af gæstedeling i forskellige scenarier.

## <a name="set-up-multi-factor-authentication-for-guests"></a>Konfigurer multifaktorgodkendelse for gæster

Multifaktorgodkendelse reducerer i høj grad risikoen for, at en konto kompromitteres. Da gæster kan bruge personlige mailkonti, der ikke overholder nogen politikker for styring eller bedste praksis, er det især vigtigt at kræve multifaktorgodkendelse for gæster. Hvis en gæsts brugernavn og adgangskode bliver stjålet, reducerer kravet om en anden godkendelsesfaktor i høj grad risikoen for, at ukendte parter får adgang til dine websteder og filer.

I dette eksempel konfigurerer vi multifaktorgodkendelse for gæster ved hjælp af en politik for betinget adgang i Azure Active Directory.

Sådan konfigurerer du multifaktorgodkendelse for gæster

1. Gå til [Politikker for betinget adgang i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. I **| Betinget adgang Bladet Politikker** , og klik på **Ny politik**.
3. Skriv et navn i feltet **Navn** .
4. Klik på **Brugere og grupper** under **Tildelinger**.
5. På bladet **Brugere og grupper** skal du vælge **Vælg brugere og grupper**, markere afkrydsningsfeltet **Alle gæster og eksterne brugere** .
6. Klik på **Cloudapps eller -handlinger** under **Tildelinger**.
7. På bladet **Cloud-apps eller -handlinger** skal du vælge **Alle cloudapps** under fanen **Medtag** .
8. Klik på **Grant (Tildel**) under **Access controls (Adgangskontrolelementer**).
9. På bladet **Grant (Tildeling** ) skal du markere afkrydsningsfeltet **Kræv multifaktorgodkendelse** og derefter klikke på **Vælg**.
10. Klik på **Til** under **Aktivér politik** på bladet **Ny**, og klik derefter på **Opret**.

Nu skal gæsten tilmelde sig multifaktorgodkendelse, før vedkommende kan få adgang til delt indhold, websteder eller teams.

### <a name="more-information"></a>Flere oplysninger

[Planlægning af en Azure AD-udrulning af multifaktorgodkendelse](/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Konfigurer vilkår for anvendelse for gæster

I nogle situationer har gæster muligvis ikke underskrevet fortrolighedsaftaler eller andre juridiske aftaler med din organisation. Du kan kræve, at gæster accepterer et vilkår for anvendelse, før de får adgang til filer, der deles med dem. Vilkår for anvendelse kan vises, første gang de forsøger at få adgang til en delt fil eller et delt websted.

Hvis du vil oprette vilkår for anvendelse, skal du først oprette dokumentet i Word eller et andet program til oprettelse og derefter gemme det som en .pdf fil. Denne fil kan derefter uploades til Azure AD.

Sådan opretter du vilkår for anvendelse af Azure AD

1. Log på Azure som global administrator, sikkerhedsadministrator eller administrator af betinget adgang.
2. Gå til [Vilkår for anvendelse](https://aka.ms/catou).
3. Klik på **Nye ord**.

   ![Skærmbillede af nye vilkår for anvendelse af Azure AD.](../media/azure-ad-guest-terms-of-use.png)

4. Skriv et **navn** og **et vist navn**.
6. Gå til den pdf-fil, du har oprettet, for **Vilkår for anvendelse af dokumentet**, og vælg den.
7. Vælg sproget for dit vilkår for anvendelse af dokumentet.
8. Angiv **Kræv, at brugere udvider vilkårene for anvendelse** til **Til**.
9. Under **Betinget adgang** skal du på listen **Gennemtving med betinget adgang politikskabelon** vælge **Opret politik for betinget adgang senere**.
10. Klik på **Opret**.

Når du har oprettet vilkårene for anvendelse, er det næste trin at oprette en politik for betinget adgang, der viser vilkår for anvendelse for gæster.

Sådan opretter du en politik for betinget adgang

1. Gå til [Politikker for betinget adgang i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. I **| Betinget adgang Bladet Politikker** , og klik på **Ny politik**.
3. Skriv et navn i feltet **Navn** .
4. Klik på **Brugere og grupper** under **Tildelinger**.
5. På bladet **Brugere og grupper** skal du vælge **Vælg brugere og grupper**, markere afkrydsningsfeltet **Alle gæster og eksterne brugere** .
6. Klik på **Cloudapps eller -handlinger** under **Tildelinger**.
7. Under fanen **Medtag** skal du vælge **Vælg apps** og derefter klikke på **Vælg**.
8. På bladet **Vælg** skal du vælge **Microsoft Teams** **Office 365 SharePoint Online** og **Outlook Grupper** og derefter klikke på **Vælg**.
9. Klik på **Grant (Tildel**) under **Access controls (Adgangskontrolelementer**).
10. På bladet **Grant** skal du vælge **Guest terms of use** og derefter klikke på **Select**.
11. Klik på **Til** under **Aktivér politik** på bladet **Ny**, og klik derefter på **Opret**.

Første gang en gæst forsøger at få adgang til indhold eller et team eller websted i din organisation, skal vedkommende acceptere vilkårene for anvendelse.

> [!NOTE]
> Brug af betinget adgang kræver en Azure AD Premium P1-licens. Du kan få flere oplysninger under [Hvad er betinget adgang](/azure/active-directory/conditional-access/overview).

### <a name="more-information"></a>Flere oplysninger

[Azure Active Directory vilkår for anvendelse](/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a>Konfigurer gæsteadgangsgennemgange

Med adgangsgennemgange i Azure AD kan du automatisere en periodisk gennemgang af brugeradgang til forskellige teams og grupper. Ved at kræve en gennemgang af adgang for gæster specifikt kan du hjælpe med at sikre, at gæster ikke bevarer adgangen til organisationens følsomme oplysninger i længere tid, end det er nødvendigt.

Sådan konfigurerer du en gennemgang af gæsteadgang

1. Klik på **Få adgang til korrekturer** i menuen til venstre på [siden Identitetsstyring](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade).
2. Klik på **Ny adgangsgennemsyn**.
3. Vælg indstillingen **Teams + grupper**.
4. Vælg indstillingen **Alle Microsoft 365 grupper med gæstebrugere**. Klik på **Vælg gruppe(er), der skal udelades** , hvis du vil udelade grupper.
5. Vælg indstillingen **Kun gæstebrugere** , og klik derefter på **Næste: Anmeldelser**.
6. Vælg **Gruppeejer(e)** under **Vælg korrekturlæsere**.
7. Klik på **Vælg reservelæsere**, vælg, hvem der skal være reservelæsere, og klik derefter på **Vælg**.
8. Under **Angiv gentagelse af gennemsyn** skal du vælge **Kvartalsvis**.
9. Vælg en startdato og en varighed.
10. Vælg **Aldrig** for **Slut**, og klik derefter på **Næste: Indstillinger**.

    ![Skærmbillede af fanen Til gennemsyn af Azure AD-adgang.](../media/azure-ad-create-access-review.png)

11. Under fanen **Indstillinger skal du** gennemse indstillingerne for overholdelse af dine forretningsregler.

    ![Skærmbillede af fanen Indstillinger for gennemsyn af Azure AD-adgang.](../media/azure-ad-create-access-review-settings.png)

12. Klik på **Næste: Gennemse + Opret**.
13. Skriv et **navn til gennemsyn** , og gennemse indstillingerne.
14. Klik på **Opret**.

Det er vigtigt at bemærke, at for SharePoint og OneDrive placeringer blokeres dokumenter proaktivt lige efter registrering af følsomme oplysninger, uanset om dokumentet er delt eller ej, for alle gæster, mens interne brugere fortsat vil have adgang til dokumentet.

### <a name="more-information"></a>Flere oplysninger

[Administrer gæsteadgang med Azure AD-adgangsgennemgange](/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Opret en gennemgang af adgang for grupper eller programmer i Azure AD-adgangsgennemgange](/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guests"></a>Konfigurer webadgang for gæster

Du kan reducere din angrebsoverflade og lette administrationen ved at kræve, at gæster kun skal have adgang til dine teams, websteder og filer ved hjælp af en webbrowser.

For Microsoft 365-grupper og Teams sker dette med en politik for betinget adgang i Azure AD. For SharePoint er dette konfigureret i SharePoint Administration. Du kan også [bruge følsomhedsmærkater til at begrænse gæster til kun at få webadgang](../compliance/sensitivity-labels-teams-groups-sites.md).

Sådan begrænser du gæster til kun at have webadgang for Grupper og Teams:

1. Gå til [Politikker for betinget adgang i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Klik på **Ny politik** på bladet **Betinget adgang – politikker**.
3. Skriv et navn i feltet **Navn** .
4. Klik på **Brugere og grupper** under **Tildelinger**.
5. På bladet **Brugere og grupper** skal du vælge **Vælg brugere og grupper**, markere afkrydsningsfeltet **Alle gæster og eksterne brugere** .
6. Klik på **Cloudapps eller -handlinger** under **Tildelinger**.
7. Under fanen **Medtag** skal du vælge **Vælg apps** og derefter klikke på **Vælg**.
8. På bladet **Vælg** skal du vælge **Microsoft Teams** og **Outlook Grupper** og derefter klikke på **Vælg**.
9. Klik på **Betingelser** under **Tildelinger**.
10. Klik på **Klientapps** på bladet **Betingelser**.
11. På bladet **Klientapps** skal du klikke på **Ja** for **Konfigurer** og derefter vælge indstillingerne **Mobilapps og desktopklienter**, **Exchange ActiveSync klienter** og **Andre klienter**. Fjern markeringen i afkrydsningsfeltet **Browser** .

    ![Skærmbillede af indstillingerne for klientapps for betinget adgang i Azure AD.](../media/azure-ad-conditional-access-client-mobile.png)

12. Klik på **Udført**.
13. Klik på **Grant (Tildel**) under **Access controls (Adgangskontrolelementer**).
14. På bladet **Grant (Tildel** ) skal du vælge **Kræv, at enheden er markeret som kompatibel** og **Kræv hybrid azure AD-tilsluttet enhed**.
15. Under **For flere kontrolelementer** skal du vælge **Kræv et af de markerede kontrolelementer** og derefter klikke på **Vælg**.
16. Klik på **Til** under **Aktivér politik** på bladet **Ny**, og klik derefter på **Opret**.

At begrænse gæster til web ony-adgang for SharePoint

1. I SharePoint Administration skal du udvide **Politikker** og vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**Adgangskontrol**</a>.
2. Vælg **Ikke-administrerede enheder**.
3. Vælg indstillingen **Tillad begrænset webadgang,** og vælg derefter **Gem**.

Bemærk, at denne indstilling i SharePoint Administration opretter en understøttende politik for betinget adgang i Azure AD.

## <a name="configure-a-session-timeout-for-guests"></a>Konfigurer timeout for session for gæster

Hvis gæster skal godkendes regelmæssigt, kan det reducere muligheden for, at ukendte brugere får adgang til organisationens indhold, hvis en gæsts enhed ikke beskyttes. Du kan konfigurere en politik for betinget adgang for sessionens timeout for gæster i Azure AD.

Sådan konfigurerer du timeoutpolitik for en gæstesession

1. Gå til [Politikker for betinget adgang i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Klik på **Ny politik** på bladet **Betinget adgang – politikker**.
3. Skriv *Timeout for gæstesession* i feltet **Navn**.
4. Klik på **Brugere og grupper** under **Tildelinger**.
5. På bladet **Brugere og grupper** skal du vælge **Vælg brugere og grupper**, markere afkrydsningsfeltet **Alle gæster og eksterne brugere** .
6. Klik på **Cloudapps eller -handlinger** under **Tildelinger**.
7. Under fanen **Medtag** skal du vælge **Vælg apps** og derefter klikke på **Vælg**.
8. På bladet **Vælg** skal du vælge **Microsoft Teams** **Office 365 SharePoint Online** og **Outlook Grupper** og derefter klikke på **Vælg**.
9. Klik på **Session** under **Adgangskontrolelementer**.
10. På bladet **Session** skal du vælge **Logonfrekvens**.
11. Vælg **1** og **Dage** for tidsperioden, og klik derefter på **Vælg**.
12. Klik på **Til** under **Aktivér politik** på bladet **Ny**, og klik derefter på **Opret**.

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a>Opret en type følsomme oplysninger for et projekt, der er meget følsomt

Følsomme oplysningstyper er foruddefinerede strenge, der kan bruges i politikarbejdsprocesser til at gennemtvinge overholdelseskrav. Microsoft Purview-overholdelsesportalen leveres med mere end hundrede følsomme oplysningstyper, herunder kørekortsnumre, kreditkortnumre, bankkontonumre osv.

Du kan oprette brugerdefinerede typer følsomme oplysninger som en hjælp til at administrere indhold, der er specifikt for din organisation. I dette eksempel opretter vi en brugerdefineret type følsomme oplysninger for et projekt, der er meget følsomt. Vi kan derefter bruge denne type følsomme oplysninger til automatisk at anvende en følsomhedsmærkat.

Sådan opretter du en type følsomme oplysninger

1. På [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) i venstre navigationsrude skal du udvide **Klassificering** og derefter klikke på **Følsomme infotyper**.
2. Klik på **Opret**.
3. Skriv **Project Saturn** for **Navn** og **Beskrivelse**, og klik derefter på **Næste**.
4. Klik på **Tilføj et element**.
5. På listen **Registrer indhold, der indeholder** skal du vælge **Nøgleord** og derefter skrive *Project Saturn* i nøgleordsfeltet.
6. Klik på **Næste**, og klik derefter på **Udfør**.
7. Hvis du bliver spurgt, om du vil teste typen af følsomme oplysninger, skal du klikke på **Nej**.

### <a name="more-information"></a>Flere oplysninger

[Brugerdefinerede typer følsomme oplysninger](/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-an-auto-labeling-policy-to-assign-a-sensitivity-label-based-on-a-sensitive-information-type"></a>Opret en politik for automatisk mærkning for at tildele en følsomhedsmærkat baseret på en type følsomme oplysninger

Hvis du bruger følsomhedsmærkater i din organisation, kan du automatisk anvende en mærkat på filer, der indeholder definerede følsomme oplysningstyper. 

Sådan opretter du en politik for automatisk mærkning

1. Åbn [Microsoft Purview Administration](https://compliance.microsoft.com).
2. Klik på **Information Protection** i venstre navigationsrude.
3. Klik på **Opret politik for automatisk mærkat** under fanen **Automatisk mærkning**.
4. Vælg **Brugerdefineret** på siden **Vælg de oplysninger, som mærkaten skal anvendes** på, og klik på **Næste**.
5. Skriv et navn og en beskrivelse til politikken, og klik på **Næste**.
6. På siden **Vælg de placeringer, hvor du vil anvende mærkaten skal du** aktivere **SharePoint websteder** og klikke på **Vælg websteder**.
7. Tilføj URL-adresserne for de websteder, hvor du vil aktivere automatisk mærkning, og klik på **Udført**.
8. Klik på **Næste**.
9. På siden **Konfigurer almindelige eller avancerede regler** skal du vælge **Fælles regler** og klikke på **Næste**.
10. Klik på **Ny regel** på siden **Definer regler for indhold på alle placeringer**.
11. På siden **Ny regel** skal du give reglen et navn, klikke på **Tilføj betingelse** og derefter klikke på **Indhold indeholder følsomme infotyper**.
12. Klik på **Tilføj**, klik på **Følsomme infotyper**, vælg de følsomme infotyper, du vil bruge, klik på **Tilføj**, og klik derefter på **Gem**.
13. Klik på **Næste**.
14. Klik på **Vælg en etiket**, vælg den etiket, du vil bruge, og klik derefter på **Tilføj**.
15. Klik på **Næste**.
16. Lad politikken være i simuleringstilstand, og klik på **Næste**.
17. Klik på **Opret politik**, og klik derefter på **Udført**.

Når politikken er på plads, anvendes den angivne mærkat automatisk, når en bruger skriver "Project Saturn" i et dokument, når den scanner filen.

### <a name="more-information"></a>Flere oplysninger

[Anvend automatisk en følsomhedsmærkat på indhold](../compliance/apply-sensitivity-label-automatically.md)

## <a name="create-a-dlp-policy-to-remove-guest-access-to-highly-sensitive-files"></a>Opret en DLP-politik for at fjerne gæsteadgang til meget følsomme filer

Du kan bruge [Microsoft Purview DLP (forebyggelse af datatab)](../compliance/dlp-learn-about-dlp.md) til at forhindre uønsket gæstedeling af følsomt indhold. Forebyggelse af datatab kan udføre handlinger på baggrund af en fils følsomhedsmærkat og fjerne gæsteadgang.

Sådan opretter du en DLP-regel

1. I Microsoft Purview Administration skal du gå til [siden til forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention).
2. Klik på **Opret politik**.
3. Vælg **Brugerdefineret,** og klik på **Næste**.
4. Skriv et navn til politikken, og klik på **Næste**.
5. Slå alle indstillinger fra på **siden Placeringer for at anvende politikken**, undtagen **SharePoint websteder** og **OneDrive konti**, og klik derefter på **Næste**.
6. Klik på **Næste** på siden **Definer politikindstillinger**.
7. På siden **Tilpas avancerede DLP-regler** skal du klikke på **Opret regel** og skrive et navn til reglen.
8. Under **Betingelser** skal du klikke på **Tilføj betingelse** og vælge **Indhold indeholder**.
9. Klik på **Tilføj**, vælg **Følsomhedsmærkater**, vælg de navne, du vil bruge, og klik på **Tilføj**.

   ![Skærmbillede af indstillinger for betingelser, typer af følsomme oplysninger, følsomhedsmærkater og opbevaringsmærkater.](../media/limit-accidental-exposure-dlp-conditions.png)

10. Klik på **Tilføj en handling** under **Handlinger**, og vælg **Begræns adgang, eller kryptér indholdet på Microsoft 365 placeringer**.
11. Markér afkrydsningsfeltet **Begræns adgang til eller kryptér indholdet på Microsoft 365 placeringer**, og vælg derefter indstillingen **Kun personer uden for organisationen**.

      ![Skærmbillede af indstillinger for DLP-regelhandlinger.](../media/dlp-remove-guest-access-sensitive-files.png)

12. Klik på **Gem** , og klik derefter på **Næste**.
13. Vælg dine testindstillinger, og klik på **Næste**.
14. Klik på **Send**, og klik derefter på **Udført**.

Det er vigtigt at bemærke, at denne politik ikke fjerner adgang, hvis gæsten er medlem af webstedet eller teamet som helhed. Hvis du planlægger at have meget følsomme dokumenter på et websted eller et team med gæstemedlemmer, skal du overveje disse muligheder:

- Brug [private kanaler](/MicrosoftTeams/private-channels) , og tillad kun medlemmer af din organisation i de private kanaler.
- Brug [delte kanaler](/MicrosoftTeams/shared-channels) til at samarbejde med personer uden for din organisation, mens du kun har personer fra din organisation i selve teamet.

## <a name="additional-options"></a>Yderligere indstillinger

Der er nogle yderligere indstillinger i Microsoft 365 og Azure Active Directory, der kan hjælpe med at sikre dit gæstedelingsmiljø.

- Du kan oprette en liste over tilladte eller afviste delingsdomæner for at begrænse, hvem brugerne kan dele med. Se [Begræns deling af SharePoint og OneDrive indhold efter domæne](/sharepoint/restricted-domains-sharing) og [Tillad eller bloker invitationer til B2B-brugere fra bestemte organisationer](/azure/active-directory/b2b/allow-deny-list) for at få flere oplysninger.
- Du kan begrænse, hvilke andre Azure Active Directory lejere dine brugere kan oprette forbindelse til. Se [Brug lejerbegrænsninger til at administrere adgang til SaaS-cloudprogrammer for at](/azure/active-directory/manage-apps/tenant-restrictions) få flere oplysninger.
- Du kan oprette et administreret miljø, hvor partnere kan hjælpe med at administrere gæstekonti. Se [Opret et B2B-ekstranet med administrerede gæster for at](/Office365/Enterprise/b2b-extranet) få flere oplysninger.

## <a name="see-also"></a>Se også

[Begræns utilsigtet eksponering for filer, når der deles med gæster](share-limit-accidental-exposure.md)

[Bedste praksis for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)

[Opret et B2B-ekstranet med administrerede gæster](b2b-extranet.md)
