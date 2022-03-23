---
title: Microsoft 365 virksomhedsressourceplanlægning – sikkerhedsarkitektur
description: Få mere at vide om de vigtigste designstrategier for Microsoft Enterprise-arkitektur fra Alex Shteynberg, Technical Principal Architect hos Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: 8e24242639362bddca7540cd8dfb390b0edb5e8c
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588225"
---
# <a name="to-identity-and-beyondone-architects-viewpoint"></a>Identitet og mere – én arkitekts alle sammen

I denne artikel diskuterer [Alex Shteynberg](https://www.linkedin.com/in/alex-shteynberg/), Principal Technical Architect hos Microsoft, de vigtigste designstrategier for virksomhedsorganisationer, der Microsoft 365 og andre Microsoft-skytjenester.

## <a name="about-the-author"></a>Om forfatteren

![Alex Shteynberg-foto.](../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg)

Jeg er Principal Technical Architect hos New York [Microsoft Technology Center](https://www.microsoft.com/mtc?rtc=1). Jeg arbejder mest med store kunder og komplekse krav. Mine venner og meninger er baseret på disse interaktioner og gælder muligvis ikke for alle situationer. Men hvis vi i min oplevelse kan hjælpe kunder med de mest komplekse udfordringer, kan vi hjælpe alle kunder.

Jeg arbejder typisk sammen med mere end 100 kunder hvert år. Selvom alle organisationer har unikke karakteristika, er det interessant at se tendenser og typiske tendenser. En tendens er f.eks. interesse på tværs af branche for mange kunder. Når alt kommer til alt, kan en bankgren også være en café og et fælleshus.

I min rolle fokuserer jeg på at hjælpe kunderne med at opnå den bedste tekniske løsning til at tage hånd om deres unikke sæt af forretningsmål. Officielt fokuserer jeg på identitet, sikkerhed, beskyttelse af personlige oplysninger og overholdelse af regler og standarder. Jeg er vild med, at disse rører ved alt det, vi gør. Det giver mig mulighed for at blive involveret i de fleste projekter. Det holder mig optaget og nyder denne rolle.

Jeg bor i New York City (det bedste!) og nyder virkelig mangfoldigheden af kultur, mad og mennesker (ikke trafik). Jeg elsker at rejse, når jeg kan og håber at se det meste af verden i mit liv. Jeg er i øjeblikket ved at undersøge en rejse til Afrika for at få mere at vide om wildlife.

## <a name="guiding-principles"></a>Styrende principper

- **Simpelt er ofte bedre**: Du kan gøre (næsten) alt med teknologi, men det betyder ikke, at du skal gøre det. Især i sikkerhedsrummet er der mange kunder, der overengineer-løsninger. Jeg kan [godt lide denne video](https://www.youtube.com/watch?v=SOQgABDSYZE) fra Googles Stripe-konference for at understrege dette punkt.
- **Personer, proces, teknologi**: [Design, så folk kan](https://en.wikipedia.org/wiki/Human-centered_design) forbedre processen, ikke teknisk først. Der er ingen "perfekte" løsninger. Vi er nødt til at balancere forskellige faktorer og beslutninger vil være forskellige for hver virksomhed. For mange kunder designer en tilgang, som deres brugere senere undgår.
- **Fokuser på "hvorfor" først og "hvordan"** senere: Vær den irriterende 7-yr gamle barn med en million spørgsmål. Vi kan ikke finde det rigtige svar, hvis vi ikke kender de rigtige spørgsmål at stille. Masser af kunder gør forudsætninger for, hvordan tingene skal fungere, i stedet for at definere forretningsproblemet. Der er altid flere stier, der kan tages.
- **Lang side af tidligere bedste fremgangsmåder**: Anerkend, at de bedste fremgangsmåder ændres ved lys hastighed. Hvis du har kigget på Azure AD for mere end tre måneder siden, er du sandsynligvis forældet. Alt her kan ændres efter publicering. Indstillingen "Bedst" i dag er muligvis ikke den samme seks måneder fra nu.

## <a name="baseline-concepts"></a>Grundlinjekoncepter

Spring ikke dette afsnit over. Jeg synes ofte, at jeg skal gå tilbage til disse emner, selv for kunder, der har brugt skytjenester i flere år.
Desværre er sprog ikke et præcist værktøj. Vi bruger ofte det samme ord til at have forskellige koncepter eller forskellige ord til at betyde det samme koncept. Jeg bruger ofte dette diagram nedenfor til at etablere noget grundlinjeterminologi og "hierarkimodel".
<br><br>

![Illustration af lejer, abonnement, tjeneste og data.](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)

<br>

Når du lærer at svømme, er det bedre at starte i puljen og ikke midt i havet. Jeg forsøger ikke at være teknisk nøjagtig med dette diagram. Det er en model, der skal diskutere nogle grundlæggende begreber.

I diagrammet:

- Lejer = en forekomst af Azure AD. Det er øverst i et hierarki eller på niveau 1 i diagrammet. Vi kan betragte dette som den "grænse[",](/azure/active-directory/users-groups-roles/licensing-directory-independence) hvor alt andet sker ([azure AD B2B](/azure/active-directory/b2b/what-is-b2b) til side). Alle Microsoft Enterprise-skytjenester er en del af en af disse lejere. Forbrugertjenester er adskilte. "Lejer" vises i dokumentationen Office 365 lejer, Azure-lejer, WVD-lejer osv. Jeg finder ofte, at disse variationer kan skabe forvirring for kunderne.
- Tjenester/abonnementer, niveau 2 i diagrammet, tilhører én og kun én lejer. De fleste SaaS-tjenester er 1:1 og kan ikke flyttes uden overførsel. Azure er anderledes, du kan [flytte fakturering og](/azure/cost-management-billing/manage/billing-subscription-transfer) /eller et abonnement [til en](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) anden lejer. Der er mange kunder, der skal flytte Azure-abonnementer. Dette har forskellige konsekvenser. Objekter, der findes uden for abonnementet, flyttes ikke (f.eks. rollebaseret adgangskontrol eller Azure RBAC og Azure AD-objekter, herunder grupper, apps, politikker og så videre). Desuden er der nogle tjenester (f.eks. Azure Key Vault, Data-teglsten, og så videre). Overfør ikke tjenester uden et godt forretningsmæssige behov. Nogle scripts, der kan være nyttige ved overførsel[, deles GitHub](https://github.com/lwajswaj/azure-tenant-migration).
- En given tjeneste har normalt en form for "underniveau"-grænse eller niveau 3 (L3). Dette er nyttigt at forstå i forbindelse med opdeling af sikkerhed, politikker, styring osv. Jeg kender desværre ikke noget uniformnavn. Eksempler på navne til L3 er: Azure-abonnement = [ressource](/azure/azure-resource-manager/management/manage-resources-portal); Dynamics 365 CE = [instance](/dynamics365/admin/new-instance-management); Power BI = [arbejdsområde](/power-bi/service-create-the-new-workspaces); Power Apps = [miljø](/power-platform/admin/environments-overview), osv.
- Niveau 4 er der, hvor de faktiske data findes. Dette "dataplan" er et komplekst emne. Nogle tjenester bruger Azure AD til RBAC, andre gør ikke. Jeg vil diskutere det lidt, når vi kommer til delegeringsemner.

Nogle yderligere begreber, som jeg finder mange kunder (og Microsoft-medarbejdere) forvirrede med eller har spørgsmål om, omfatter følgende:

- Alle kan [oprette](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) mange lejere [uden omkostninger](https://azure.microsoft.com/pricing/details/active-directory/). Du behøver ikke en tjeneste der er klargjort inden for den. Jeg har masser. Hvert lejernavn er entydigt i Microsofts verdensomspændende skytjeneste (med andre ord kan ikke to lejere have samme navn). De er alle i formatet TenantName.onmicrosoft.com. Der findes også processer, der opretter lejere automatisk ([ikke-administrerede lejere](/azure/active-directory/users-groups-roles/directory-self-service-signup)). Dette kan f.eks. ske, når en bruger tilmelder sig en virksomhedstjeneste med et maildomæne, der ikke findes i nogen anden lejer.
- I en administreret lejer [kan mange DNS-domæner registreres](/azure/active-directory/fundamentals/add-custom-domain) i den. Dette ændrer ikke det oprindelige lejernavn. Det er i øjeblikket ikke nemt at omdøbe en lejer (bortset fra overførsel). Selvom lejernavnet teknisk set ikke er kritisk i disse dage, kan nogle opleve, at dette begrænser sig.
- Du bør reservere et lejernavn til organisationen, selvom du endnu ikke planlægger at installere nogen tjenester. Ellers kan nogen tage det fra dig, og der er ingen simpel proces til at tage den tilbage (samme problem som DNS-navne). Jeg hører denne måde for ofte fra kunder. Det, som dit lejernavn skal være, er også et emne, hvor du kan diskutere emner.
- Hvis du ejer DNS-navneområde(er), skal du tilføje alle disse til din lejer/dine lejere. Ellers kan man oprette en [ikke-administreret lejer](/azure/active-directory/users-groups-roles/directory-self-service-signup) med dette navn, hvilket derefter medfører afbrydelser i [deres administrerede lejer](/azure/active-directory/users-groups-roles/domains-admin-takeover).
- DNS namespace (f.eks. contoso.com) kan tilhøre én og kun én lejer. Dette har konsekvenser for forskellige scenarier (f.eks. deling af et maildomæne under en fusion eller overtagelse, og så videre). Der findes en metode til at registrere en DNS-under (f.eks div.contoso.com) i en anden lejer, men det skal undgås. Ved at registrere et domænenavn på øverste niveau antages alle underdomæner at tilhøre den samme lejer. I scenarier med flere lejere (se nedenfor) vil jeg normalt anbefale brug af et andet domænenavn på øverste niveau (f.eks. et contoso.ch eller ch-contoso.com).
- Who skal "eje" en lejer? Jeg ser ofte kunder, der ikke ved, hvem der i øjeblikket ejer deres lejer. Dette er et stort rødt flag. Ring til Microsoft support hurtigst muligt. Lige så problematisk er det, når en tjenesteejer (ofte Exchange administrator) er udpeget til at administrere en lejer. Lejeren indeholder alle de tjenester, du vil have på et senere tidspunkt. Lejerejeren skal være en gruppe, der kan tage beslutningen om aktivering af alle skytjenester i en organisation. Et andet problem er, når en lejerejergruppe bliver bedt om at administrere alle tjenester. Dette skaleres ikke til store organisationer.
- Der er ikke noget koncept for en under-/superlejer. Af en eller anden grund bliver denne myte ved med at gentage sig selv. Dette gælder også [for Azure AD B2C-lejere](/azure/active-directory-b2c/) . Jeg hører for mange gange: "Mit B2C-miljø er i min XYZ-lejer" eller "Hvordan flytter jeg min Azure-lejer til min Office 365 lejer?"
- Dette dokument fokuserer primært på den kommercielle sky over hele verden, da det er det, som de fleste kunder bruger. Nogle gange er det nyttigt at vide [om suveræne skyer](/azure/active-directory/develop/authentication-national-cloud). Suveræne skyer har yderligere konsekvenser for at diskutere, hvilke der er uden for området for denne diskussion.

## <a name="baseline-identity-topics"></a>Emner om oprindelig identitet

Der er meget dokumentation om Microsofts identitetsplatform – Azure Active Directory (Azure AD). For dem, der er ved at starte, føles det ofte overvældende. Selv når du har lært det, kan det være en udfordring at holde styr på konstant innovation og ændringer. I mine kundeinteraktioner fungerer jeg ofte som "oversætter" mellem forretningsmål og "Godt, bedre, Bedst" tilgange til disse (og mennesker "klippenoter" for disse emner). Der findes sjældent et perfekt svar, og den "rigtige" beslutning er en balance mellem forskellige faktorer. Nedenfor finder du nogle af de mest almindelige spørgsmål og forvirringsområder, jeg har tendens til at diskutere med kunder.

### <a name="provisioning"></a>Klargøring

Azure AD løser ikke på grund af manglende styring i din identitetsverden! [Identitetsstyring](/azure/active-directory/governance/identity-governance-overview) bør være et vigtigt element uafhængigt af eventuelle skybeslutninger. Styringskravet ændres over tid, hvilket er grunden til, at det er et program og ikke et værktøj.

[Azure AD Forbind](/azure/active-directory/hybrid/whatis-azure-ad-connect) vs. [Microsoft Identity Manager](/microsoft-identity-manager/microsoft-identity-manager-2016) (MIM) vs. noget andet (tredjepart eller brugerdefineret)? Spar dig selv en masse problemer nu og i fremtiden, og gå med Azure AD Forbind. Der er alle typer smarts i dette værktøj til at håndtere aktuelle kundekonfigurationer og igangværende innovationer.

Nogle kanttilfælde, der kan føre til en mere kompleks arkitektur:

- Jeg har flere AD-skove uden netværksforbindelse mellem disse. Der er en ny indstilling kaldet [Klargøring i skyen](/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning).
- Jeg har ikke Active Directory, og jeg vil heller ikke installere det. Azure AD Forbind konfigureres til at synkronisere [fra LDAP](/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (partner kan være påkrævet).
- Jeg har brug for at klargøre de samme objekter til flere lejere. Dette understøttes ikke teknisk, men afhænger af definitionen af "samme".

Skal jeg tilpasse standardsynkroniseringsregler ([filtrere objekter](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering), [ændre attributter](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized)[, alternativt](/azure/active-directory/hybrid/plan-connect-userprincipalname) logon-id og så videre)? Undgå det! En identitetsplatform er kun lige så værdifuld som de tjenester, der bruger den. Selvom du kan udføre alle slags nutty-konfigurationer, skal du se på indvirkningen på programmer for at besvare dette spørgsmål. Hvis du filtrerer mailaktiverede objekter, vil den globale adresseliste til onlinetjenester være ufuldstændig. hvis programmet afhænger af bestemte attributter, vil filtrering af disse have uforudsete konsekvenser; og så videre. Det er ikke et identitetsteams beslutning.

XYZ SaaS understøtter JUST-in-Time (JIT) klargøring, hvorfor kræver du, at jeg synkroniserer? Se ovenfor. Mange programmer har brug for "profiloplysninger" for at kunne bruge funktioner. Du kan ikke have en GAL, hvis alle mailaktiverede objekter ikke er tilgængelige. Det samme gælder for [bruger klargøring](/azure/active-directory/app-provisioning/user-provisioning) i programmer, der er integreret med Azure AD.

### <a name="authentication"></a>Godkendelse

[Synkronisering af adgangskodehash](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) (PHS) [vs. pass-through-godkendelse](/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) (PTA) vs. [sammenslutning](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

Som regel er der en [engageret diskussion](/azure/active-directory/hybrid/choose-ad-authn) om sammenslutning. Enklere er som regel bedre og bruger derfor PHS, medmindre du har en god grund til ikke at gøre det. Det er også muligt at konfigurere forskellige godkendelsesmetoder for forskellige DNS-domæner i samme lejer.

Nogle kunder aktiverer sammenslutning + PHS hovedsageligt for:

- En mulighed for [at vende tilbage](/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) til (ved genoprettelse efter nedbrud), hvis sammenslutningstjenesten ikke er tilgængelig.
- Yderligere funktioner (f.eks.: [Azure AD DS](/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)) og sikkerhedstjenester (f.eks.: [lækerede legitimationsoplysninger](/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials))
- Understøttelse af tjenester i Azure, der ikke forstår federated authentication (f.eks. [Azure-filer](/azure/storage/files/storage-files-active-directory-overview)).

Jeg fører ofte kunder gennem klientgodkendelsesflowet for at tydeliggøre nogle uoverensstemmelser. Resultatet ligner billedet nedenfor, som ikke er så godt som den interaktive proces med at komme dertil.

![Eksempel på whiteboardsamtale.](../media/solutions-architecture-center/identity-beyond-whiteboard-example.png)

Denne type whiteboardtegning illustrerer, hvor sikkerhedspolitikker anvendes i flowet af en godkendelsesanmodning. I dette eksempel anvendes politikker, der håndhæves via Active Directory Federation Service (AD FS), på den første serviceanmodning, men ikke på efterfølgende serviceanmodninger. Dette er mindst én grund til at flytte sikkerhedskontrolelementer til skyen så meget som muligt.

Vi har været på jagt efter en [enkelt logon](/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO), så længe jeg kan huske. Nogle kunder mener, at de kan gøre dette ved at vælge den "rigtige" sammenslutningsudbyder (STS). Azure AD kan hjælpe markant med at [aktivere SSO-funktioner](/azure/active-directory/manage-apps/plan-sso-deployment) , men ingen STS er magisk. Der er for mange "ældre" godkendelsesmetoder, der stadig bruges til vigtige programmer. Udvidelse af Azure AD [med partnerløsninger](/azure/active-directory/saas-apps/tutorial-list) kan håndtere mange af disse scenarier. SSO er en strategi og en rejse. Du kan ikke komme dertil uden at gå i retning [af standarder for programmer](/azure/active-directory/develop/v2-app-types). Relateret til dette emne er en rejse [mod adgangskodefri](/azure/active-directory/authentication/concept-authentication-passwordless) godkendelse, som heller ikke har et magisk svar.

[Multifaktorgodkendelse](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) er afgørende i dag ([her](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) for at få mere). Føj analyser af [brugeradfærd til det,](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) så har du en løsning, der forhindrer de mest almindelige cyberangreb. Selv forbrugertjenester flytter til at kræve MFA. Jeg mødes stadig med mange kunder, der ikke ønsker at skifte til moderne [godkendelsesmetoder](../enterprise/hybrid-modern-auth-overview.md) . Det største argument, jeg hører, er, at det påvirker brugere og ældre programmer. Nogle gange kan et godt kick hjælpe kunderne med at komme videre – Exchange Online [annoncerede ændringer](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282). Der findes nu masser [af](/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) Azure AD-rapporter, som kan hjælpe kunder med denne overgang.

### <a name="authorization"></a>Godkendelse

Ifølge [Wikipedia](https://en.wikipedia.org/wiki/Authorization) er "at godkende" at definere en adgangspolitik. Mange ser det som muligheden for at definere adgangskontrolelementer til et objekt (fil, tjeneste, og så videre). I den aktuelle verden af cybertrusler udvikler dette koncept sig hurtigt til en dynamisk politik, der kan reagere på forskellige trusselsvektorer og hurtigt justere adgangskontrol som reaktion på disse. Hvis jeg f.eks. får adgang til min bankkonto fra en usædvanlig placering, får jeg yderligere bekræftelsestrin. For at komme i gang med dette skal vi ikke kun overveje selve politikken, men også økosystemet med trusselsregistrering og signalrelationsmetoder.

Politikprogrammet i Azure AD implementeres ved hjælp af [Betingede access-politikker](/azure/active-directory/conditional-access/overview). Dette system afhænger af oplysninger fra en række andre systemer til trusselsregistrering for at kunne træffe dynamiske beslutninger. En simpel visning ville være noget i den følgende illustration:

![Politikprogram i Azure AD.](../media/solutions-architecture-center/identity-and-beyond-illustration-3.png)

Når alle disse signaler kombineres, er det muligt at bruge dynamiske politikker som disse:

- Hvis der registreres en trussel på din enhed, vil din adgang til data kun blive reduceret til internettet uden muligheden for at downloade.
- Hvis du downloader en usædvanlig stor mængde data, krypteres og begrænses alt, hvad du har downloadet.
- Hvis du får adgang til en tjeneste fra en ikke-administreret enhed, vil du blive blokeret fra meget følsomme data, men har tilladelse til at få adgang til ikke-begrænsede data uden mulighed for at kopiere dem til en anden placering.

Hvis du er enig i denne udvidede godkendelsesdefinition, skal du implementere yderligere løsninger. Hvilke løsninger, du implementerer, afhænger af, hvor dynamisk du ønsker, at politikken skal være, og hvilke trusler du vil prioritere. Eksempler på sådanne systemer er:

- [Azure AD Identity Protection](/azure/active-directory/identity-protection/)
- [Microsoft Defender for Identity](/azure-advanced-threat-protection/)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Microsoft Defender til Office 365](../security/office-365-security/defender-for-office-365.md)
- [Microsoft Defender til skyapps](/cloud-app-security/) (Defender til skyapps)
- [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md)
- [Microsoft Intune](/mem/intune/)
- [Microsoft Information Protection](../compliance/information-protection.md) (MIP)
- [Microsoft Sentinel](/azure/sentinel/)

Ud over Azure AD har forskellige tjenester og programmer deres egne specifikke godkendelsesmodeller. Nogle af disse gennemgås senere i afsnittet om delegering.

### <a name="audit"></a>Overvågning

Azure AD har detaljerede [overvågnings- og rapporteringsfunktioner](/azure/active-directory/reports-monitoring/) . Dette er dog normalt ikke den eneste kilde til oplysninger, der er nødvendige for at træffe sikkerhedsbeslutninger. Se flere diskussioner om dette i afsnittet om delegering.

## <a name="theres-no-exchange"></a>Der er ingen Exchange

Gå ikke i panik! Det betyder ikke, Exchange bliver udskrevet (eller SharePoint og så videre). Det er stadig en central tjeneste. Hvad jeg mener er, at teknologiudbydere i nogen tid har ændret brugeroplevelsen (UX) for at omfatte komponenter af flere tjenester. I Microsoft 365 er et enkelt eksempel "moderne [vedhæftede](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC) filer", hvor vedhæftede filer i mails gemmes i SharePoint Online eller OneDrive for Business.

![Vedhæftning af en fil til en mail.](../media/solutions-architecture-center/modern-attachments.png)

Når du kigger på Outlook, kan du se mange tjenester, der er "forbundne" som en del af denne oplevelse, ikke kun Exchange. Dette omfatter Azure AD, Microsoft Søg, apps, profil, overholdelse og Office 365 grupper.

![Outlook grænseflade med uddelingskopier.](../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png)

Læs om [Microsoft Fluid Framework](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) for forhåndsvisning af kommende funktioner. I forhåndsvisning nu kan jeg læse og svare på Teams samtaler direkte i Outlook. Faktisk er Teams [et](https://products.office.com/microsoft-teams/download-app) af de mere fremtrædende eksempler på denne strategi.

Generelt bliver det sværere at tegne en klar streg mellem Office 365 og andre tjenester i Microsoft-skyer. Jeg ser det som en stor fordel for kunderne, da de kan drage fordel af total innovation på tværs af alt, hvad vi gør, selvom de bruger én komponent. Ret smart og har meget omfattende konsekvenser for mange kunder.

I dag synes jeg, at mange kunde-it-grupper er struktureret omkring "produkter". Det er logisk for en lokal verden, da du har brug for en ekspert i hvert enkelt produkt. Men jeg er helt tilfreds med, at jeg ikke behøver at fejlfinde i en Active Directory- eller Exchange-database på noget tid siden disse tjenester er flyttet til skyen. Automatisering (hvilken slags skybaseret løsning er) fjerner visse gentagne manuelle opgaver (se, hvad der er sket med faktorer). Disse erstattes dog af mere komplekse krav for at forstå interaktion mellem tjenester, virkning, forretningsmæssige behov osv. Hvis du er villig til at [lære det](/learn/), er der gode muligheder, som er blevet aktiveret med cloudtransformation. Før jeg springer til teknologi, taler jeg ofte med kunder om administration af ændringer i IT-færdigheder og teamstrukturer.

Til alle SharePoint faner og udviklere skal du holde op med at spørge "Hvordan kan jeg gøre XYZ SharePoint online?" Brug [Power Automate](/power-automate/) (eller Flow) til arbejdsprocesser, er det en meget mere effektiv platform. Brug [Azure Bot Framework til](/azure/bot-service/) at skabe en bedre brugeroplevelse til din liste med 500 K-elementer. Begynd at [bruge Microsoft Graph](https://developer.microsoft.com/graph/) i stedet for CSOM. [Microsoft Teams](/MicrosoftTeams/Teams-overview) indeholder SharePoint men også en verden mere. Der er mange andre eksempler, jeg kan liste. Der er et enormt og fantastisk univers derude. Åbn døren, [og begynd at udforske den]().

De andre almindelige konsekvenser er på området for overholdelse af regler og standarder. Denne tilgang på tværs af tjenester lader til at forveksle mange politikker for overholdelse af regler og standarder fuldstændigt. Jeg bliver ved med at se organisationer med denne tilstand "Jeg har brug for at journal føre al mailkommunikation til et eDiscovery-system". Hvad betyder det i virkeligheden, når mail ikke længere blot er mail, men et vindue til andre tjenester? Office 365 har en omfattende tilgang til [overholdelse](../compliance/index.yml), men ændring af personer og processer er ofte meget sværere end teknologi.

Der er mange andre personer og proces konsekvenser. Efter min mening er dette et kritisk og under diskuteret område. Måske mere i en anden artikel.

## <a name="tenant-structure-options"></a>Indstillinger for lejerstruktur

### <a name="single-tenant-vs-multi-tenant"></a>Enkelt lejer vs. flere lejere

Generelt bør de fleste kunder kun have én produktionslejer. Der er mange årsager til, at flere lejere er udfordrende (giv [det en Bing søgning](https://www.bing.com/search?q=office%20365%20multiple%20tenants)) eller læse [denne hvidbog](https://aka.ms/multi-tenant-user). På samme tid har mange virksomhedskunder, jeg arbejder sammen med, en anden (lille) lejer til it-læring, test og eksperimentering. Azure-adgang på tværs af lejere er gjort nemmere [med Azure Lighthouse](https://azure.microsoft.com/services/azure-lighthouse/). Office 365 og mange andre SaaS-tjenester har begrænsninger for scenarier på tværs af lejere. Der er meget at overveje i [Azure AD B2B-scenarier](/azure/active-directory/b2b/what-is-b2b) .

Mange kunder ender med flere produktionslejere efter en fusion og overtagelse (M&A) og ønsker at konsolidere. I dag er det ikke enkelt og kræver Microsoft Consulting Services (MCS) eller en partner plus tredjepartssoftware. Der er igangværende teknisk arbejde til at håndtere forskellige scenarier med kunder med flere lejere i fremtiden.

Nogle kunder vælger at gå med mere end én lejer. Dette bør være en meget forsigtig beslutning og næsten altid forretningsårsagensbaseret! Her er nogle eksempler:

- En holdingstype for firmastruktur, hvor nemt samarbejde mellem forskellige enheder ikke er påkrævet, og der er stærke administrative og andre isolationsbehov.
- Efter en overtagelse træffes der en forretningsmæssig beslutning om at holde to enheder adskilt.
- Simulering af en kundes miljø, der ikke ændrer kundens produktionsmiljø.
- Udvikling af software til kunder.

I disse scenarier med flere lejere vil kunderne ofte beholde en konfiguration på samme måde på tværs af lejere eller rapportere om konfigurationsændringer og driftsscenarier. Dette betyder ofte, at du skifter fra manuelle ændringer til konfiguration som kode. Microsoft Premier-support tilbyder et workshop for disse typer af krav, der er baseret på denne offentlige IP: <https://Microsoft365dsc.com>.

### <a name="multi-geo"></a>Multi-Geo

For [Multi-Geo](../enterprise/microsoft-365-multi-geo.md) eller ikke for Multi-Geo, er det spørgsmålet. Med Office 365 multi-geo kan du klargøre og gemme data i hvile på de geoplaceringer, du har valgt at opfylde krav til dataopbevaring.[](../enterprise/o365-data-locations.md) Der er mange uoverensstemmelser omkring denne funktion. Vær opmærksom på følgende:

- Det giver ikke ydelsesfordele. Det kan gøre ydeevnen værre, hvis [netværksdesignet](https://aka.ms/office365networking) ikke er korrekt. Få enheder "tæt" på Microsoft-netværket, ikke nødvendigvis til dine data.
- Det er ikke en løsning i forhold til [OVERHOLDELSE AF GDPR](https://www.microsoft.com/trust-center/privacy/gdpr-overview). GDPR fokuserer ikke på data, der er på overdrindt eller på lagerplaceringer. Det er der andre rammer for overholdelse af regler og standarder i.
- Det løser ikke delegering af administration (se nedenfor) eller [informationsbarrierer](../compliance/information-barriers.md).
- Det er ikke det samme som flere lejere og kræver yderligere arbejdsprocesser for [klargøring af](https://github.com/MicrosoftDocs/azure-docs-pr/blob/master/articles/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation.md) brugere.
- Det flytter ikke [din lejer](../enterprise/moving-data-to-new-datacenter-geos.md) (dit Azure AD) til en anden geografi.

## <a name="delegation-of-administration"></a>Delegering af administration

I de fleste store organisationer er adskillelse af pligter og rollebaseret adgangskontrol den nødvendige virkelighed. Jeg vil beklager i forvejen. Dette er ikke så enkelt, som nogle kunder ønsker det skal være. Kunde-, juridiske krav, overholdelseskrav og andre krav er forskellige og nogle gange modstridende over hele verden. Enkelhed og fleksibilitet er ofte på hver sin side af hinanden. Det skal ikke gå galt. Vi kan gøre et bedre stykke arbejde på dette. Der har været (og vil være) betydelige forbedringer over tid. Besøg dit lokale [Microsoft Technology Center for at](https://www.microsoft.com/mtc) finde den model, der passer til virksomhedens behov, uden at læse 379230-dokumenter! Her vil jeg fokusere på, hvad du skal tænke på, og ikke hvorfor det er på denne måde. Nedenfor er der fem forskellige områder at planlægge for og nogle af de mest almindelige spørgsmål, jeg har oplevet.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>Azure AD og Microsoft 365 Administration

Der findes en lang og voksende liste over [indbyggede roller](/azure/active-directory/roles/permissions-reference). Hver rolle består af en liste over rolletilladelser, der er grupperet sammen for at tillade, at bestemte handlinger kan udføres. Du kan se disse tilladelser under fanen "Beskrivelse" inde i hver rolle. Alternativt kan du se en mere læsbar version af disse i Microsoft 365 Administration Center. Definitionerne for indbyggede roller kan ikke ændres. Indgrupper disse i tre kategorier generelt:

- **Global administrator**: Denne "alle effektive" rolle skal være [meget beskyttet](../enterprise/protect-your-global-administrator-accounts.md) , ligesom du ville gøre i andre systemer. Typiske anbefalinger omfatter: ingen permanent tildeling og brug Azure AD Privileged Identity Management (PIM), stærk godkendelse osv. Denne rolle giver dig interessant set ikke adgang til alt som standard. Normalt kan jeg se forvirring om adgang til overholdelse og Azure-adgang, som gennemgås senere. Denne rolle kan dog altid tildele adgang til andre tjenester i lejeren.
- **Bestemte tjenesteadministratorer**: Nogle tjenester (Exchange, SharePoint, Power BI osv.) bruger administratorroller på højt niveau fra Azure AD. Dette er ikke ensartet på tværs af alle tjenester, og der diskuteres flere tjenestespecifikke roller senere.
- **Funktionelt**: Der er en lang (og voksende) liste over roller, der fokuserer på bestemte handlinger (gæsteindvitator, og så videre). Med jævne mellemrum tilføjes flere af disse ud fra kundernes behov.

Det er ikke muligt at uddelegere alt (selvom mellemrummet er faldende), hvilket betyder, at den globale administratorrolle nogle gange skulle bruges. Konfiguration som kode og automatisering bør tages i betragtning i stedet for personer, der er medlem af denne rolle.

**Bemærk**! Microsoft 365 Administration har en mere brugervenlig grænseflade, men har undersæt af funktioner sammenlignet med Azure AD-administratoroplevelsen. Begge portaler bruger de samme Azure AD-roller, så der sker ændringer det samme sted. Tip: Hvis du vil have en identitetsstyringsfokuseret administratorbrugergrænseflade uden alt Azure Clutter, skal du bruge <https://aad.portal.azure.com>.

Hvad er der i navnet? Du må ikke tage forudsætninger ud fra navnet på rollen. Sprog er ikke et meget præcist værktøj. Målet bør være at definere handlinger, der skal uddelegeres, før du ser på, hvilke roller der er nødvendige. Når du føjer nogen til rollen "Sikkerhedslæser", får de ikke vist sikkerhedsindstillinger på tværs af alt.

Muligheden for at oprette [brugerdefinerede roller](/azure/active-directory/users-groups-roles/roles-custom-overview) er et almindeligt spørgsmål. Dette er begrænset i Azure AD i dag (se nedenfor), men vil vokse i egenskaber over tid. Jeg tror, at disse er relevante for funktioner i Azure AD og strækker sig muligvis ikke over "ned" hierarkimodellen (nævnt ovenfor). Når jeg håndterer "brugerdefineret", går jeg typisk tilbage til min hovedstol om "enkel er bedre".

Et andet almindeligt spørgsmål er muligheden for at begrænse roller til et undersæt af en mappe. Et eksempel er noget i f.eks. "Helpdesk-administrator kun for brugere i EU". [Administrative enheder](/azure/active-directory/users-groups-roles/directory-administrative-units) (AU) er beregnet til at løse dette. Som ovenfor tænker jeg på disse som relevante for funktioner i Azure AD og strækker sig muligvis ikke over "ned". Visse roller giver naturligvis ikke mening i forhold til omfang (globale administratorer, tjenesteadministratorer og så videre).

I dag kræver alle disse roller direkte medlemskab (eller dynamisk opgave, hvis du bruger [Azure AD PIM](/azure/active-directory/privileged-identity-management/)). Det betyder, at kunderne skal administrere disse direkte i Azure AD, og disse kan ikke være baseret på et sikkerhedsgruppemedlemskab. Jeg er ikke fan af at oprette scripts til at administrere disse, da det ville være nødvendigt at køre med administratorrettigheder. Jeg anbefaler generelt API-integration med processystemer som ServiceNow eller brug af partnerstyringsværktøjer som f.eks. Saviynt. Der er i gang teknikerarbejde for at løse dette i en periode.

Jeg har [nævnt Azure AD PIM](/azure/active-directory/privileged-identity-management/) et par gange. Der er en tilsvarende Microsoft Identity Manager (MIM) [løsning](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services) til administration af adgang med rettigheder (PAM) for lokale kontrolelementer. Du kan også se på styring af [privilegeret adgang til arbejdsstationer](/windows-server/identity/securing-privileged-access/privileged-access-workstations) (PAWs) og [Azure AD Identity Governance](/azure/active-directory/governance/identity-governance-overview). Der er også forskellige tredjepartsværktøjer, som kan aktivere just-in-time, just-enough, og dynamisk rolle elevation. Dette er normalt en del af en større diskussion om sikring af et miljø.

Nogle gange kræver scenarier, at du føjer en ekstern bruger til en rolle (se afsnittet med flere lejere ovenfor). Det fungerer fint. [Azure AD B2B er](/azure/active-directory/b2b/) et andet stort og sjovt emne, som kunderne kan gennemgå, måske i en anden artikel.

### <a name="security-and-compliance-center-scc"></a>Security and Compliance Center (SCC)

[Tilladelser i Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md) er en samling af "rollegrupper", som er adskilte og adskiller sig fra Azure AD-roller. Det kan være forvirrende, fordi nogle af disse rollegrupper har samme navn som Azure AD-roller (f.eks. Sikkerhedslæser), men de kan have forskellige medlemskaber. Jeg foretrækker at bruge Azure AD-roller. Hver rollegruppe består af en eller flere "roller" (se hvad jeg mener om at genbruge det samme ord?) og har medlemmer fra Azure AD, som er mailaktiverede objekter. Du kan også oprette en rollegruppe med samme navn som en rolle, som muligvis eller ikke indeholder den pågældende rolle (undgå denne forvirring).

På en måde er disse en udvikling af Exchange rollegruppemodellen. Dog har Exchange Online sin egen grænseflade til [rollegruppeadministration](/exchange/permissions-exo). Nogle rollegrupper i Exchange Online er låst og administreres fra Azure AD eller Security & Compliance Center, men andre kan have de samme eller lignende navne og administreres i Exchange Online (hvilket gør forvirringen mere forvirrende). Jeg anbefaler, at du undgår Exchange Online brugergrænsefladen, medmindre du har brug for områder til Exchange administration.

Du kan ikke oprette brugerdefinerede roller. Roller defineres af tjenester, der er oprettet af Microsoft, og de vokser i efterhånden som nye tjenester introduceres. Dette er i koncept svarende til [roller defineret af programmer](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) i Azure AD. Når nye tjenester aktiveres, skal der ofte oprettes nye rollegrupper for at give eller uddelegere adgang til disse (f.eks. [insider-risikostyring](../compliance/insider-risk-management-configure.md)).

Disse rollegrupper kræver også direkte medlemskab og kan ikke indeholde Azure AD-grupper. Desværre understøttes disse rollegrupper i dag ikke af Azure AD PIM. Ligesom Azure AD-roller vil jeg typisk anbefale administration af disse via API'er eller et partnerstyringsprodukt som f.eks. Saviynt eller andre.

Sikkerheds- & overholdelsescenter strækker sig Microsoft 365 og du kan ikke begrænse disse rollegrupper til et undersæt af miljøet (som du kan med administrative enheder i Azure AD). Mange kunder spørger, hvordan de kan subdelegate. "Opret f.eks. kun en DLP-politik for EU-brugere". Hvis du i dag har rettigheder til en bestemt funktion i Security & Compliance Center, har du rettigheder til alt, der er dækket af denne funktion i lejeren. Mange politikker har dog funktioner til at målrette et undersæt af miljøet (f.eks. "gør disse [etiketter](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) kun tilgængelige for disse brugere"). Korrekt styring og kommunikation er et vigtigt element for at undgå konflikter. Nogle kunder vælger at implementere en "konfiguration som kode"-metode for at løse problemer med underdelegering i Security & Compliance Center. Nogle bestemte tjenester understøtter underdelegering (se nedenfor).

Det er værd at bemærke, at kontrolelementer, der i øjeblikket administreres via Security & Compliance Center (protection.office.com), er ved at blive overført til to separate administrationsportaler: security.microsoft.com og compliance.microsoft.com. Ændring er den eneste konstant!

### <a name="service-specific"></a>Tjenestespecifik

Som nævnt tidligere ønsker mange kunder at opnå en mere detaljeret delegeringsmodel. Et almindeligt eksempel: "Administrer kun XYZ-tjeneste for Division X-brugere og -placeringer" (eller en anden dimension). Muligheden for at gøre dette afhænger af hver enkelt tjeneste og er ikke ensartet på tværs af tjenester og egenskaber. Desuden kan hver tjeneste have en separat og entydig RBAC-model. I stedet for at diskutere alle disse (det tager uendelig lang tid), tilføjer jeg relevante links for hver tjeneste. Dette er ikke en komplet liste, men det kan hjælpe dig i gang.

- **Exchange Online** - (/exchange/permissions-exo/permissions-exo)
- **SharePoint Online** - (/sharepoint/manage-site-collection-administrators)
- **Microsoft Teams** - (/microsoftteams/itadmin-readiness)
- **eDiscovery** - (.. /compliance/index.yml)
  - **Tilladelsesfiltrering** - (.. /compliance/index.yml)
  - **Overensstemmelsesgrænser** - (.. /compliance/set-up-compliance-boundaries.md)
  - **Advanced eDiscovery** - (.. /compliance/overview-ediscovery-20.md)
- **Yammer** - (/yammer/manage-yammer-users/manage-yammer-admins)
- **Multi-geo** - (.. /enterprise/add-a-sharepoint-geo-admin.md)
- **Dynamics 365** – (/dynamics365/)

  Bemærk! Dette link er roden for dokumentationen. Der findes flere typer tjenester med variationer i administrator-/delegeringsmodellen.

- **Power Platform** - (/power-platform/admin/admin-documentation)
  - **Power Apps** - (/power-platform/admin/wp-security)

    Bemærk! Der er flere typer med variationer af administrator-/delegeringsmodeller.

  - **Power Automate** - (/power-automate/environments-overview-admin)
  - **Power BI** - (/power-bi/service-admin-governance)

    Bemærk! Dataplatformsikkerhed og uddelegering (som Power BI er en komponent) er et komplekst område.

- **MEM/Intune** - (/mem/intune/fundamentals/role-based-access-control)
- **Microsoft Defender til Slutpunkt** - (/windows/security/threat-protection/microsoft-defender-atp/user-roles)
- **Microsoft 365 Defender** - (.. /security/defender/m365d-permissions.md)
- **Microsoft Defender til skyapps** - (/cloud-app-security/manage-admins)
- **Stream** - (/stream/assign-administrator-user-role)
- **Informationsbarrierer** - (.. /compliance/information-barriers.md)

### <a name="activity-logs"></a>Aktivitetslogfiler

Office 365 har en [samlet overvågningslog](../compliance/search-the-audit-log-in-security-and-compliance.md). Det er en meget [detaljeret log](/office/office-365-management-api/office-365-management-activity-api-schema), men læs ikke for meget i navnet. Den indeholder muligvis ikke alt det, du ønsker eller har brug for til dine sikkerheds- og overholdelsesbehov. Desuden er nogle kunder virkelig interesseret i [Avanceret overvågning](../compliance/advanced-audit.md).

Eksempler på Microsoft 365, der tilgås via andre API'er, omfatter følgende:

- [Azure AD](/azure/azure-monitor/platform/diagnostic-settings) (aktiviteter, der ikke er relateret Office 365)
- [Exchange meddelelsessporing](/powershell/module/exchange/get-messagetrace)
- Threat/UEBA Systems discussed above (for example, Azure AD Identity Protection, Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint, and so on)
- [Microsoft-beskyttelse af oplysninger](../compliance/data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Det er vigtigt først at identificere alle de logfiler, der skal bruges til et sikkerheds- og overholdelsesprogram. Bemærk også, at forskellige logfiler har forskellige begrænsninger for opbevaring online.

Set fra administratordelegeringsperspektiv har Microsoft 365 aktivitetslogfiler ikke en indbygget RBAC-model. Hvis du har tilladelse til at se en logfil, kan du se alt i den. Et almindeligt eksempel på et kundekrav er: "Jeg vil kun kunne forespørge på aktiviteter for EU-brugere" (eller en anden dimension). For at opfylde dette krav skal vi overføre logfiler til en anden tjeneste. I Microsoft-skyen anbefaler vi, at du overfører den til [enten Microsoft Sentinel](/azure/sentinel/overview) eller [Log Analytics](/azure/azure-monitor/learn/quick-create-workspace).

Diagram på højt niveau:

![Diagram over logkilder til et program til sikkerhed og overholdelse af regler og standarder.](../media/solutions-architecture-center/identity-beyond-illustration-4.png)

Diagrammet ovenfor repræsenterer indbyggede funktioner til at sende logfiler til Hændelseshub og/eller Azure Storage og/eller Azure Log Analytics. Det er endnu ikke alle systemer, der har denne out of the box. Men der er andre metoder til at sende disse logfiler til det samme lager. Se f.eks[. Beskyttelse af Teams med Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

Kombinationen af alle logfilerne på én lagerplacering omfatter ekstra fordele, f.eks. krydskorrelation, brugerdefinerede opbevaringstider, udvidelsen med de data, der skal bruges til at understøtte RBAC-modellen osv. Når dataene er i dette lagersystem, kan du oprette et Power BI dashboard (eller en anden type visualisering) med en passende RBAC-model.

Logfiler behøver ikke at blive omdirigeret til ét sted. Det kan også være nyttigt at integrere [Office 365 med Microsoft Defender til skyapps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) eller en brugerdefineret RBAC-model [Power BI](../admin/usage-analytics/usage-analytics.md). Forskellige lagre har forskellige fordele og målgrupper.

Det er værd at nævne, at der er et meget omfattende indbygget analysesystem til sikkerhed, trusler, sårbarheder og så videre i en tjeneste kaldet [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md).

Mange store kunder ønsker at overføre disse logdata til et tredjepartssystem (f.eks. SIEM). Der er forskellige metoder til dette, men generelt [er Azure Event Hub](/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) [og Graph](/graph/security-integration) gode udgangspunkter.

### <a name="azure"></a>Azure

Jeg bliver ofte spurgt, om der er en metode til at adskille roller med høj rettighed mellem Azure AD, Azure og SaaS (f.eks.: Global administrator for Office 365, men ikke Azure).  Det er ikke rigtigt.  Arkitektur med flere lejere er nødvendig, hvis en komplet administrativ adskillelse er påkrævet, men det tilføjer [betydelig kompleksitet](https://aka.ms/multi-tenant-user) (se ovenfor). Alle disse tjenester er en del af den samme sikkerheds-/identitetsgrænse (se på hierarkimodellen ovenfor).

Det er vigtigt at forstå relationer mellem forskellige tjenester i samme lejer. Jeg arbejder sammen med mange kunder, der bygger virksomhedsløsninger, der strækker sig over Azure, Office 365 og Power Platform (og ofte også skytjenester i det lokale miljø og tredjepartstjenester). Et almindeligt eksempel:

1. Jeg vil gerne samarbejde om et sæt dokumenter/billeder osv(Office 365)
2. Send hver enkelt af dem via en godkendelsesproces (Power Platform)
3. Når alle komponenter er godkendt, kan du samle disse i en samlet leverance (Azure) [Microsoft Graph API](/azure/active-directory/develop/microsoft-graph-intro) er din bedste ven for disse.  Ikke umuligt, men markant mere komplekst at designe en løsning, der strækker sig [over flere lejere](/azure/active-directory/develop/single-and-multi-tenant-apps).

Azure Role-Based Access Control (RBAC) giver mulighed for finjusteret adgangsstyring for Azure. Med RBAC kan du administrere adgangen til ressourcer ved at give brugerne færrest tilladelser til at udføre deres opgaver. Detaljer er ikke omfattet af dette dokument, men du kan finde flere oplysninger om RBAC i Hvad er rollebaseret [adgangskontrol i Azure?](/azure/role-based-access-control/overview) RBAC er vigtig, men kun en del af overvejelserne vedrørende styring af Azure. [Cloud Adoption Framework er](/azure/cloud-adoption-framework/govern/) et godt udgangspunkt for at få mere at vide. Jeg kan godt lide, hvordan [min ven, AndresTrininet, trinvist](https://www.linkedin.com/in/andres-ravinet/) går kunderne gennem forskellige komponenter for at beslutte tilgangen. Visning på højt niveau for forskellige elementer (ikke så god som processen med at få adgang til den faktiske kundemodel) er noget i denne stand:

![Visning på højt niveau af Azure-komponenter til delegeret administration.](../media/solutions-architecture-center/identity-beyond-illustration-5.png)

Som du kan se ovenfra, bør mange andre tjenester betragtes som en del af designet (f.eks. [Azure-politikker](/azure/governance/policy/overview), [Azure Blueprints](/azure/governance/blueprints/overview)[,](/azure/governance/management-groups/) administrationsgrupper osv.).

## <a name="conclusion"></a>Konklusion

Startet som en kort oversigt, men er længere end forventet.  Jeg håber, at du nu er klar til at gå i gang med at oprette en delegeringsmodel for organisationen.  Denne samtale er meget almindelig for kunder. Der er ingen model, der fungerer for alle. Venter på et par planlagte forbedringer fra Microsofts tekniker, før du dokumenterer almindelige mønstre, som vi ser på tværs af kunderne. I mellemtiden kan du arbejde sammen med dit Microsoft-kontoteam om at arrangere et besøg i det nærmeste [Microsoft Technology Center](https://www.microsoft.com/mtc).  Vi ses her!
