---
title: Opret et sikkert miljø for gæstedeling
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
description: Få mere at vide om de tilgængelige muligheder for at oprette et sikkert miljø for gæstedeling i Microsoft 365 hvilket giver gæsteadgang til forbedret samarbejde.
ms.openlocfilehash: 13190f2dba0f2cb1f4817a1a831b8d78359e1b81
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715135"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Opret et sikkert miljø for gæstedeling

I denne artikel gennemgår vi en række forskellige muligheder for at oprette et sikkert miljø for gæstedeling Microsoft 365. Disse er eksempler, der kan give dig en ide om de tilgængelige muligheder. Du kan bruge disse procedurer i forskellige kombinationer for at opfylde organisationens behov for sikkerhed og overholdelse.

Denne artikel indeholder:

- Konfiguration af multifaktorgodkendelse for gæster.
- Konfiguration af vilkår for anvendelse for gæster.
- Konfiguration af kvartalsvise anmeldelser af gæsteadgang for jævnligt at validere, om gæster fortsat har brug for tilladelser til teams og websteder.
- Begrænsning af gæster til kun at være webadgang for enheder, der ikke er administrerede.
- Konfiguration af en timeoutpolitik for en session for at sikre, at gæster godkendes dagligt.
- Oprettelse af en følsom oplysningstype til et meget følsomt projekt.
- Automatisk tildeling af et følsomhedsmærkat til dokumenter, der indeholder en følsom oplysningstype.
- Fjerner automatisk gæsteadgang fra filer med en følsomhedsmærkat.

Nogle af de indstillinger, der er nævnt i denne artikel, kræver, at gæster har en konto Azure Active Directory. For at sikre at gæster er inkluderet i kataloget, når du deler filer og mapper med dem, skal du bruge [SharePoint og OneDrive-integration med Azure AD B2B Preview](/sharepoint/sharepoint-azureb2b-integration-preview).

Bemærk, at vi ikke diskuterer aktivering af indstillinger for gæstedeling i denne artikel. Se [Samarbejde med personer uden for organisationen for at](collaborate-with-people-outside-your-organization.md) få mere at vide om at aktivere gæstedeling for forskellige scenarier.

## <a name="set-up-multi-factor-authentication-for-guests"></a>Konfigurer multifaktorgodkendelse for gæster

Multifaktorgodkendelse reducerer risikoen for, at en konto kompromitteres væsentligt. Da gæster bruger personlige mailkonti, der ikke overholder nogen styringspolitikker eller bedste praksis, er det særligt vigtigt at kræve multifaktorgodkendelse for gæster. Hvis en gæsts brugernavn og adgangskode bliver stjålet, hvilket kræver en anden godkendelsesmetode, reduceres risikoen for, at ukendte parter får adgang til dine websteder og filer meget.

I dette eksempel konfigurerer vi multifaktorgodkendelse for gæster ved hjælp af en politik for betinget adgang i Azure Active Directory.

Sådan konfigureres multifaktorgodkendelse for gæster

1. Gå til [politikker for betinget adgang til Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. På **siden Betinget adgang | Politikker skal** du klikke på **Ny politik**.
3. Skriv **et** navn i feltet Navn.
4. Under **Opgaver skal du** klikke **på Brugere og grupper**.
5. På **bladet Brugere og** grupper skal **du vælge Vælg brugere og** grupper og **markere afkrydsningsfeltet Alle gæster og** eksterne brugere.
6. Under **Opgaver skal du** klikke på **Skyapps eller -handlinger**.
7. På **skyapps eller handlingsbladet** skal **du vælge Alle skyapps** på **fanen** Medtag.
8. Under **Access-kontrolelementer** skal du klikke på **Tilgå**.
9. På **tildelings** bladet skal du **markere afkrydsningsfeltet Kræv multifaktorgodkendelse** og derefter klikke på **Vælg**.
10. Klik på **Til** under **Aktivér politik på siden Ny** **blade, og** klik derefter på **Opret**.

Nu skal gæster tilmeldes multifaktorgodkendelse, før de kan få adgang til delt indhold, websteder eller teams.

### <a name="more-information"></a>Flere oplysninger

[Planlægning af en Azure AD-installation med multifaktorgodkendelse](/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Konfigurer en vilkår for anvendelse for gæster

I nogle situationer har gæster muligvis ikke signeret fortrolighedsaftaler eller andre juridiske aftaler med din organisation. Du kan kræve, at gæster accepterer en vilkår for anvendelse, før de får adgang til filer, der deles med dem. Vilkårene for anvendelse kan vises, første gang de forsøger at få adgang til en delt fil eller et delt websted.

Hvis du vil oprette en vilkår for anvendelse, skal du først oprette dokumentet i Word eller et andet oprettelsesprogram og derefter gemme det som en .pdf fil. Denne fil kan derefter uploades til Azure AD.

Sådan oprettes en Azure AD-vilkår for anvendelse

1. Log på Azure som global administrator, sikkerhedsadministrator eller betinget adgangsadministrator.
2. Gå til [Vilkår for anvendelse](https://aka.ms/catou).
3. Klik **på Nye ord**.

   ![Skærmbillede af de nye vilkår for anvendelse i Azure AD.](../media/azure-ad-guest-terms-of-use.png)

4. Skriv et **Navn** og **Vist navn**.
6. For **Vilkår for anvendelse af dokument skal** du gå til den pdf-fil, du har oprettet, og vælge den.
7. Vælg sproget for dine vilkår for anvendelse af dokumentet.
8. Angiv **Kræv, at brugere udvider vilkårene for anvendelse** til **Til**.
9. Under **Betinget adgang på** listen **Gennemtving med betinget adgang-politikskabelon** skal du **vælge Opret politik for betinget adgang senere**.
10. Klik **på Opret**.

Når du har oprettet vilkårene for anvendelse, er næste trin at oprette en politik for betinget adgang, der viser vilkårene for anvendelse for gæster.

Sådan oprettes en politik for betinget adgang

1. Gå til [politikker for betinget adgang til Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. På **siden Betinget adgang | Politikker skal** du klikke på **Ny politik**.
3. Skriv **et** navn i feltet Navn.
4. Under **Opgaver skal du** klikke **på Brugere og grupper**.
5. På **bladet Brugere og** grupper skal **du vælge Vælg brugere og** grupper og **markere afkrydsningsfeltet Alle gæster og** eksterne brugere.
6. Under **Opgaver skal du** klikke på **Skyapps eller -handlinger**.
7. På fanen **Medtag** skal du vælge **Vælg apps** og derefter klikke på **Vælg**.
8. På siden **Vælg** blade skal du **vælge Microsoft Teams**, **Office 365 SharePoint Online** og **Outlook Grupper** og derefter klikke på **Vælg**.
9. Under **Access-kontrolelementer** skal du klikke på **Tilgå**.
10. På **tildelingsbladet** skal du **vælge Gæstevilkår for anvendelse** og derefter klikke på **Vælg**.
11. Klik på **Til** under **Aktivér politik på siden Ny** **blade, og** klik derefter på **Opret**.

Første gang gæster forsøger at få adgang til indhold eller et team eller websted i organisationen, skal de acceptere vilkårene for anvendelse.

> [!NOTE]
> Brug af Betinget adgang kræver en Azure AD Premium P1-licens. Du kan finde flere oplysninger [under Hvad er Betinget adgang](/azure/active-directory/conditional-access/overview).

### <a name="more-information"></a>Flere oplysninger

[Azure Active Directory vilkår for anvendelse](/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a>Konfigurer anmeldelser af gæsteadgang

Med access-anmeldelser i Azure AD kan du automatisere en periodisk gennemgang af brugeradgang til forskellige teams og grupper. Ved at kræve en adgangsvurdering for gæster specifikt kan du hjælpe med at sikre, at gæster ikke bevarer adgangen til din organisations følsomme oplysninger i længere tid end nødvendigt.

Sådan konfigurerer du en gæsteadgangsgennemgang

1. Klik på [Access-anmeldelser](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) i menuen til venstre på siden **Identitetsstyring**.
2. Klik **på Ny adgangsgennemsyn**.
3. Vælg indstillingen **Teams +** Grupper.
4. Vælg indstillingen **Alle Microsoft 365 med gæstebrugere**. Klik **på Vælg grupper, der skal udelades** , hvis du vil udelade nogen grupper.
5. Vælg indstillingen **Kun gæstebrugere** , og klik derefter på **Næste: Anmeldelser**.
6. Vælg **Gruppeejer(er**) **under Vælg korrekturlæsere**.
7. Klik **på Vælg korrekturlæsere,** vælg, hvem der skal være reserverevisionerne, og klik derefter på **Vælg**.
8. Under **Angiv gentagelse af gennemsyn skal** du vælge **Kvartalsvis**.
9. Vælg en startdato og varighed.
10. Vælg **Aldrig** **under End,** og klik derefter på **Næste: Indstillinger**.

    ![Skærmbillede af fanen til gennemgang af Azure AD-adgang.](../media/azure-ad-create-access-review.png)

11. På fanen **Indstillinger** skal du gennemgå indstillingerne for overholdelse af dine forretningsregler.

    ![Skærmbillede af fanen med indstillinger for Gennemgang af Azure AD-adgang.](../media/azure-ad-create-access-review-settings.png)

12. Klik **på Næste: Gennemse + Opret**.
13. Skriv et **Navn på Gennemse** , og gennemse indstillingerne.
14. Klik **på Opret**.

Det er vigtigt at bemærke, at for SharePoint- og OneDrive-placeringer blokeres dokumenter proaktivt lige efter registrering af følsomme oplysninger, uanset om dokumentet deles eller ej, for alle gæster, mens interne brugere fortsat har adgang til dokumentet.

### <a name="more-information"></a>Flere oplysninger

[Administrer gæsteadgang med Azure AD-adgangsvurderinger](/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Opret en adgangsgennemsyn af grupper eller programmer i Azure AD-adgangsgennemgange](/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guests"></a>Konfigurer kun webadgang for gæster

Du kan reducere din angrebsoverflade og gøre administrationen nemmere ved at kræve, at gæster kun har adgang til dine teams, websteder og filer ved hjælp af en webbrowser.

For Microsoft 365 Gruppe og Teams udføres dette med en politik for betinget adgang i Azure AD. Dette SharePoint konfigureret i SharePoint Administration. (Du kan også [bruge følsomhedsmærkater til at begrænse gæster til kun at være webadgang](../compliance/sensitivity-labels-teams-groups-sites.md)).

Sådan begrænser du gæster til kun at have adgang til internettet for grupper Teams:

1. Gå til [politikker for betinget adgang til Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Klik på **Ny politik i bladet** Betinget adgang – **Politikker**.
3. Skriv **et** navn i feltet Navn.
4. Under **Opgaver skal du** klikke **på Brugere og grupper**.
5. På **bladet Brugere og** grupper skal **du vælge Vælg brugere og** grupper og **markere afkrydsningsfeltet Alle gæster og** eksterne brugere.
6. Under **Opgaver skal du** klikke på **Skyapps eller -handlinger**.
7. På fanen **Medtag** skal du vælge **Vælg apps** og derefter klikke på **Vælg**.
8. På siden **Vælg** blade skal du **vælge Microsoft Teams** og **Outlook,** og derefter skal du klikke på **Vælg**.
9. Under **Opgaver skal du** klikke på **Betingelser**.
10. Klik på **Klientapps** i **bladet Betingelser**.
11. På **klientapps** bladet skal du klikke på **Ja for** **Konfigurer** og derefter vælge indstillingerne **Mobilapps** og skrivebordskienter, **Exchange ActiveSync-klienter** **og Andre klienter**. Fjern markeringen **i afkrydsningsfeltet** Browser.

    ![Skærmbillede af indstillinger for betinget adgang til Azure AD-klientapps.](../media/azure-ad-conditional-access-client-mobile.png)

12. Klik **på Udført**.
13. Under **Access-kontrolelementer** skal du klikke på **Tilgå**.
14. På **Grant-bladet** skal du vælge **Kræv, at enheden er markeret som kompatibel og** **Kræv hybrid Azure AD-enhed sammenføjet**.
15. Under **For flere kontrolelementer skal** du **vælge Kræv et af de markerede kontrolelementer** og derefter klikke på **Vælg**.
16. Klik på **Til** under **Aktivér politik på siden Ny** **blade, og** klik derefter på **Opret**.

Sådan begrænser du gæsters adgang til web-ony for SharePoint

1. I administration SharePoint skal du udvide **Politikker og** vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**Adgangskontrol**</a>.
2. Vælg **Ikke-administrerede enheder**.
3. Vælg indstillingen **Tillad kun begrænset adgang via internettet** , og vælg derefter **Gem**.

Bemærk, at denne indstilling i SharePoint Administration opretter en understøttende politik for betinget adgang i Azure AD.

## <a name="configure-a-session-timeout-for-guests"></a>Konfigurere en sessionstimeout for gæster

Hvis du kræver, at gæster godkendes regelmæssigt, kan det reducere risikoen for, at ukendte brugere får adgang til organisationens indhold, hvis en gæsts enhed ikke holdes sikker. Du kan konfigurere en politik for betinget adgang for gæster i Azure AD via timeout for en session.

Sådan konfigureres en timeoutpolitik for en gæstesession

1. Gå til [politikker for betinget adgang til Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Klik på **Ny politik i bladet** Betinget adgang – **Politikker**.
3. Skriv **timeout** for *gæstesession i feltet Navn*.
4. Under **Opgaver skal du** klikke **på Brugere og grupper**.
5. På **bladet Brugere og** grupper skal **du vælge Vælg brugere og** grupper og **markere afkrydsningsfeltet Alle gæster og** eksterne brugere.
6. Under **Opgaver skal du** klikke på **Skyapps eller -handlinger**.
7. På fanen **Medtag** skal du vælge **Vælg apps** og derefter klikke på **Vælg**.
8. På siden **Vælg** blade skal du **vælge Microsoft Teams**, **Office 365 SharePoint Online** og **Outlook Grupper** og derefter klikke på **Vælg**.
9. Klik **på Session under Access-kontrolelementer**.
10. På **sessionsbladet** skal du **vælge Logonfrekvens**.
11. Vælg **1** og **Dage** for perioden, og klik derefter på **Vælg**.
12. Klik på **Til** under **Aktivér politik på siden Ny** **blade, og** klik derefter på **Opret**.

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a>Oprette en følsom oplysningstype til et meget følsomt projekt

Typer af følsomme oplysninger er foruddefinerede strenge, der kan bruges i politikarbejdsprocesser til at håndhæve krav til overholdelse af regler og standarder. The Microsoft 365 Compliance Center leveres med over et hundrede følsomme oplysningstyper, herunder kørekortnumre, kreditkortnumre, bankkontonumre osv.

Du kan oprette brugerdefinerede typer af følsomme oplysninger som hjælp til at administrere indhold, der er specifikt for din organisation. I dette eksempel opretter vi en brugerdefineret type af følsomme oplysninger til et meget følsomt projekt. Vi kan derefter bruge denne type følsomme oplysninger til automatisk at anvende en følsomhedsmærkat.

Sådan oprettes en type af følsomme oplysninger

1. På siden [Microsoft 365 til overholdelse af](https://compliance.microsoft.com) regler og standarder skal du i venstre **navigationsrude** udvide Klassificering og derefter klikke **på Følsomme oplysningstyper**.
2. Klik **på Opret**.
3. Ud **for** Navn **og beskrivelse** skal **du Project Saturn** og derefter klikke på **Næste**.
4. Klik **på Tilføj et element**.
5. På listen **Find indhold, der** indeholder skal **du vælge** Nøgleord og derefter *skrive Project Saturn* i nøgleordsfeltet.
6. Klik **på Næste**, og klik derefter på **Udfør**.
7. Hvis du bliver spurgt, om du vil teste typen af følsomme oplysninger, skal du klikke på **Nej**.

### <a name="more-information"></a>Flere oplysninger

[Brugerdefinerede typer af følsomme oplysninger](/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-an-auto-labeling-policy-to-assign-a-sensitivity-label-based-on-a-sensitive-information-type"></a>Opret en automatisk etiketpolitik for at tildele en følsomhedsmærkat baseret på en følsom oplysningstype

Hvis du bruger følsomhedsmærkater i din organisation, kan du automatisk anvende en etiket på filer, der indeholder definerede typer af følsomme oplysninger. 

Sådan oprettes en politik for automatisk mærkater

1. Åbn Microsoft 365 [Administration for overholdelse af regler og standarder](https://compliance.microsoft.com).
2. Klik på Beskyttelse af oplysninger i **venstre navigationsrude**.
3. Klik på **Opret politik for automatisk** **mærkater under fanen Automatisk mærkat.**
4. På siden **Vælg oplysninger, som denne etiket skal anvendes på** skal du vælge **Brugerdefineret og** klikke på **Næste**.
5. Skriv et navn og en beskrivelse af politikken, og klik på **Næste**.
6. På siden **Vælg placeringer, hvor du vil anvende etiketsiden** skal du aktivere Websteder **SharePoint klikke** på **Vælg websteder**.
7. Tilføj URL-adresserne for de websteder, hvor du vil aktivere automatisk mærkning, og klik på **Udført**.
8. Klik på **Næste**.
9. På siden **Konfigurer almindelige eller avancerede regler skal du** vælge **Almindelige regler og** klikke på **Næste**.
10. Klik på **Ny regel på siden Definer regler for** indhold på **alle placeringer**.
11. På siden **Ny regel skal** du give reglen et navn, klikke på **Tilføj betingelse** og derefter klikke på **Indhold indeholder følsomme oplysningstyper**.
12. Klik **på** Tilføj, **klik på Typer af følsomme** oplysninger, vælg de typer af følsomme oplysninger, du vil bruge, klik **på Tilføj**, og klik derefter på **Gem**.
13. Klik på **Næste**.
14. Klik **på Vælg en etiket**, vælg den etiket, du vil bruge, og klik derefter på **Tilføj**.
15. Klik på **Næste**.
16. Lad politikken være i simuleringstilstand, og klik **på Næste**.
17. Klik **på Opret politik**, og klik derefter på **Udført**.

Når politikken er på plads, når en bruger skriver "Project Saturn" i et dokument, vil politikken for automatisk mærkning automatisk anvende den angivne etiket, når den scanner filen.

### <a name="more-information"></a>Flere oplysninger

[Anvend en følsomhedsmærkat på indhold automatisk](../compliance/apply-sensitivity-label-automatically.md)

## <a name="create-a-dlp-policy-to-remove-guest-access-to-highly-sensitive-files"></a>Opret en DLP-politik for at fjerne gæsteadgang til meget følsomme filer

Du kan bruge [forebyggelse af datatab (DLP) til at](../compliance/dlp-learn-about-dlp.md) forhindre uønsket gæstedeling af følsomt indhold. Forebyggelse af datatab kan handle baseret på en fils følsomhedsmærkat og fjerne gæsteadgang.

Sådan oprettes en DLP-regel

1. I Microsoft 365 administration af overholdelse skal du gå til siden [til forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention).
2. Klik **på Opret politik**.
3. Vælg **Brugerdefineret** , og klik **på Næste**.
4. Skriv et navn til politikken, og klik på **Næste**.
5. På siden **Placeringer for at anvende** politik deaktiveres alle indstillinger undtagen SharePoint **websteder** og **OneDrive konti**, og klik derefter på **Næste**.
6. Klik på **Næste på siden** Definer **politikindstillinger**.
7. På siden **Tilpas avancerede DLP-regler** skal du **klikke på Opret** regel og skrive et navn til reglen.
8. Under **Betingelser** skal du klikke **på Tilføj** betingelse og vælge **Indhold indeholder**.
9. Klik **på Tilføj**, **vælg Følsomhedsmærkater**, vælg de etiketter, du vil bruge, og klik på **Tilføj**.

   ![Skærmbillede af indstillinger for betingelser, følsomme oplysningstyper, følsomhedsmærkater og opbevaringsmærkater.](../media/limit-accidental-exposure-dlp-conditions.png)

10. Under **Handlinger** skal **du klikke på Tilføj** en **handling og vælge Begræns adgang eller kryptere indholdet Microsoft 365 placeringer**.
11. Markér **afkrydsningsfeltet Begræns adgang eller kryptér indholdet Microsoft 365 placeringerne**, og vælg **derefter indstillingen Kun personer uden for** organisationen.

      ![Skærmbillede af handlingsindstillinger for DLP-regel.](../media/dlp-remove-guest-access-sensitive-files.png)

12. Klik **på Gem** , og klik derefter **på Næste**.
13. Vælg dine testindstillinger, og klik på **Næste**.
14. Klik **på Send**, og klik derefter på **Udført**.

Det er vigtigt at bemærke, at denne politik ikke fjerner adgangen, hvis gæsten er medlem af webstedet eller teamet som en helhed. Hvis du planlægger at have meget følsomme dokumenter på et websted eller team med gæstemedlemmer, skal du overveje disse muligheder:

- Brug [private kanaler](/MicrosoftTeams/private-channels) , og kun tillade medlemmer af organisationen i de private kanaler.
- Brug [delte kanaler](/MicrosoftTeams/shared-channels) til at samarbejde med personer uden for organisationen, mens du kun har personer fra din organisation i selve teamet.

## <a name="additional-options"></a>Yderligere indstillinger

Der er nogle flere muligheder i Microsoft 365 og Azure Active Directory, der kan hjælpe med at sikre dit miljø for gæstedeling.

- Du kan oprette en liste over tilladte eller nægtet deling af domæner for at begrænse, hvem brugere kan dele med. Se [Begræns deling af indhold SharePoint indhold OneDrive](/sharepoint/restricted-domains-sharing) domæne og Tillad eller bloker [invitationer til B2B-brugere](/azure/active-directory/b2b/allow-deny-list) fra bestemte organisationer for at få flere oplysninger.
- Du kan begrænse, hvilke andre Azure Active Directory som dine brugere kan oprette forbindelse til. Se [Brug lejerbegrænsninger til at administrere adgang til SaaS-skyprogrammer](/azure/active-directory/manage-apps/tenant-restrictions) for at få flere oplysninger.
- Du kan oprette et administreret miljø, hvor partnere kan hjælpe med at administrere gæstekonti. Se [Opret et B2B-ekstranet med administrerede gæster](/Office365/Enterprise/b2b-extranet) for at få flere oplysninger.

## <a name="see-also"></a>Se også

[Begræns utilsigtet eksponering af filer, når du deler med gæster](share-limit-accidental-exposure.md)

[Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)

[Opret et B2B-ekstranet med administrerede gæster](b2b-extranet.md)
