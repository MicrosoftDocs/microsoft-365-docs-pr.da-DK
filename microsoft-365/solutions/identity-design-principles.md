---
title: Til identitet og videre – en arkitekts synspunkt
description: Få mere at vide om de vigtigste designstrategier for Microsoft Enterprise-arkitektur fra Alex Shteynberg, Teknisk Principal Architect hos Microsoft.
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
ms.openlocfilehash: 065e9a124deb7c064b31666d96a11f076d65abdd
ms.sourcegitcommit: 52e2a67a1badd7faaabbcf99c65f464e23a47805
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/14/2022
ms.locfileid: "66060955"
---
# <a name="to-identity-and-beyondone-architects-viewpoint"></a>Til identitet og videre – en arkitekts synspunkt

I denne artikel drøfter [Alex Shteynberg](https://www.linkedin.com/in/alex-shteynberg/), Principal Technical Architect hos Microsoft, de vigtigste designstrategier for virksomhedsorganisationer, der anvender Microsoft 365 og andre Microsoft-cloudtjenester.

## <a name="about-the-author"></a>Om forfatteren

![Alex Shteynberg foto.](../media/solutions-architecture-center/identity-and-beyond-alex-shteynberg.jpg)

Jeg er Principal Technical Architect i [Microsoft Technology Center](https://www.microsoft.com/mtc?rtc=1) i New York. Jeg arbejder hovedsageligt med store kunder og komplekse krav. Mit synspunkt og meninger er baseret på disse interaktioner og kan ikke gælde for enhver situation. Men hvis vi efter min erfaring kan hjælpe kunder med de mest komplekse udfordringer, kan vi hjælpe alle kunder.

Jeg arbejder typisk med mere end 100 kunder hvert år. Hver organisation har unikke egenskaber, men det er interessant at se tendenser og fællestræk. En tendens er f.eks. interesse på tværs af brancher for mange kunder. Når alt kommer til alt kan en bankgren også være en kaffebar og et fællescenter.

I min rolle fokuserer jeg på at hjælpe kunderne med at nå frem til den bedste tekniske løsning til at løse deres unikke sæt forretningsmål. Officielt fokuserer jeg på identitet, sikkerhed, beskyttelse af personlige oplysninger og overholdelse af angivne standarder. Jeg elsker det faktum, at disse rører alt, hvad vi gør. Det giver mig mulighed for at blive involveret i de fleste projekter. Denne aktivitet holder mig travlt og nyder denne rolle.

Jeg bor i New York City (den bedste!) og nyder virkelig mangfoldigheden af dens kultur, mad og mennesker (ikke trafik). Jeg elsker at rejse, når jeg kan og håber at se det meste af verden i min levetid. Jeg er i øjeblikket forsker en tur til Afrika for at lære om dyrelivet.

## <a name="guiding-principles"></a>Ledende principper

- **Enkelt er ofte bedre**: Du kan gøre (næsten) alt med teknologi, men det betyder ikke, at du skal. Især i sikkerhedsområdet overengineer mange kunder løsninger. Jeg kan godt lide [denne video](https://www.youtube.com/watch?v=SOQgABDSYZE) fra Googles Stripe-konference for at understrege dette punkt.
- **Personer, proces, teknologi**: [Design, så folk](https://en.wikipedia.org/wiki/Human-centered_design) kan forbedre processen, ikke teknologien først. Der er ingen "perfekte" løsninger. Vi er nødt til at afbalancere forskellige risikofaktorer, og beslutninger vil være forskellige for hver virksomhed. For mange kunder designer en tilgang, som brugerne senere undgår.
- **Fokuser på 'hvorfor' først og 'hvordan' senere**: Vær det irriterende 7-yr gamle barn med en million spørgsmål. Vi kan ikke nå frem til det rigtige svar, hvis vi ikke kender de rigtige spørgsmål at stille. Mange kunder antager, hvordan tingene skal fungere i stedet for at definere forretningsproblemet. Der er altid flere stier, der kan udføres.
- **Lange haler af tidligere bedste praksisser**: Anerkender, at de bedste fremgangsmåder ændres med let hastighed. Hvis du har set på Azure AD for mere end tre måneder siden, er du sandsynligvis forældet. Alt her kan ændres efter udgivelsen. "Bedste" mulighed i dag er muligvis ikke det samme seks måneder fra nu.

## <a name="baseline-concepts"></a>Koncepter for oprindelig plan

Spring ikke denne sektion over. Jeg oplever ofte, at jeg skal gå tilbage til disse artikler, selv for kunder, der har brugt cloudtjenester i årevis.
Desværre er sprog ikke et præcist værktøj. Vi bruger ofte det samme ord til at betyde forskellige begreber eller forskellige ord til at betyde det samme begreb. Jeg bruger ofte dette diagram nedenfor til at etablere nogle grundlæggende terminologi og "hierarkimodel".
<br><br>

![Illustration af lejer, abonnement, tjeneste og data.](../media/solutions-architecture-center/Identity-and-beyond-tenant-level.png)

<br>

Når du lærer at svømme, er det bedre at starte i poolen og ikke midt i havet. Jeg forsøger ikke at være teknisk korrekt med dette diagram. Det er en model til at diskutere nogle grundlæggende begreber.

I diagrammet:

- Tenant = en forekomst af Azure AD. Det er øverst i et hierarki eller niveau 1 i diagrammet. Vi kan betragte dette niveau som "[grænsen](/azure/active-directory/users-groups-roles/licensing-directory-independence)", hvor alt andet forekommer ([Azure AD B2B](/azure/active-directory/b2b/what-is-b2b) til side). Alle Microsoft Enterprise-cloudtjenester er en del af en af disse lejere. Forbrugertjenester er separate. "Lejer" vises i dokumentationen som Office 365 lejer, Azure-lejer, WVD-lejer osv. Jeg oplever ofte, at disse variationer skaber forvirring hos kunderne.
- Tjenester/abonnementer, niveau 2 i diagrammet, tilhører én og kun én lejer. De fleste SaaS-tjenester er 1:1 og kan ikke flyttes uden migrering. Azure er anderledes. Du kan [flytte fakturering](/azure/cost-management-billing/manage/billing-subscription-transfer) og/eller et [abonnement](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory) til en anden lejer. Der er mange kunder, der skal flytte Azure-abonnementer. Dette scenarie har forskellige konsekvenser. Objekter, der findes uden for abonnementet, flyttes ikke. Eksempelvis rollebaseret adgangskontrol (Azure RBAC), Azure AD objekter (grupper, apps, politikker osv.) og nogle tjenester (Azure Key Vault, Data Bricks osv.). Overfør ikke tjenester uden et godt forretningsbehov. Nogle scripts, der kan være nyttige i forbindelse med overførsel, [deles på GitHub](https://github.com/lwajswaj/azure-tenant-migration).
- En given tjeneste har normalt en form for "grænse under niveau" eller niveau 3 (L3). Denne grænse er nyttig til at forstå for adskillelse af sikkerhed, politikker, styring osv. Desværre er der ikke noget ensartet navn, som jeg kender til. Nogle eksempler på navne på L3 er: Azure Subscription = [resource](/azure/azure-resource-manager/management/manage-resources-portal); Dynamics 365 CE = [instans](/dynamics365/admin/new-instance-management); Power BI = [arbejdsområde](/power-bi/service-create-the-new-workspaces); Power Apps = [miljø](/power-platform/admin/environments-overview) osv.
- Niveau 4 er stedet, hvor de faktiske data findes. Dette "datafly" er en kompleks artikel. Nogle tjenester bruger Azure AD til RBAC, andre ikke. Jeg vil diskutere det lidt, når vi kommer til delegering artikler.

Nogle yderligere begreber, som jeg finder, at mange kunder (og Microsoft-medarbejdere) er forvirrede over eller har spørgsmål om, omfatter følgende problemer:

- Alle kan [oprette](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant) mange lejere [uden omkostninger](https://azure.microsoft.com/pricing/details/active-directory/). Du behøver ikke at have en klargjort tjeneste i den. Jeg har mange. Hvert lejernavn er entydigt i Microsofts verdensomspændende cloudtjeneste (med andre ord kan ikke to lejere have det samme navn). De har alle formatet TenantName.onmicrosoft.com. Der er også processer, der opretter lejere automatisk ([ikke-administrerede lejere](/azure/active-directory/users-groups-roles/directory-self-service-signup)). Dette kan f.eks. ske, når en bruger tilmelder sig en virksomhedstjeneste med et maildomæne, der ikke findes i nogen anden lejer.
- I en administreret lejer kan mange [DNS-domæner](/azure/active-directory/fundamentals/add-custom-domain) registreres i den. Dette ændrer ikke det oprindelige lejernavn. Der er i øjeblikket ingen nem måde at omdøbe en lejer på (bortset fra overførsel). Selvom lejernavnet teknisk set ikke er kritisk i disse dage, kan nogle finde det begrænsende.
- Du skal reservere et lejernavn til din organisation, selvom du endnu ikke har planer om at udrulle nogen tjenester. Ellers kan nogen tage det fra dig, og der er ingen enkel proces til at tage det tilbage (samme problem som DNS-navne). Jeg hører denne måde alt for ofte fra kunder. Det, dit lejernavn skal være, er også en debatartikel.
- Hvis du ejer DNS-navneområder, skal du føje alle disse til dine lejere. Ellers kan man oprette en [ikke-administreret lejer](/azure/active-directory/users-groups-roles/directory-self-service-signup) med dette navn, hvilket derefter medfører afbrydelse for at [få den administreret](/azure/active-directory/users-groups-roles/domains-admin-takeover).
- DNS-navneområdet (f.eks. contoso.com) kan tilhøre én og kun én lejer. Dette har konsekvenser for forskellige scenarier (f.eks. deling af et maildomæne under en fusion eller overtagelse osv.). Det er muligt at registrere et DNS-under (f.eks. div.contoso.com) i en anden lejer, men det bør undgås. Ved at registrere et domænenavn på øverste niveau antages det, at alle underdomæner tilhører den samme lejer. I scenarier med flere lejere (se nedenfor) vil jeg normalt anbefale at bruge et andet domænenavn på øverste niveau (f.eks. contoso.ch eller ch-contoso.com).
- Who skal "eje" en lejer? Jeg ser ofte kunder, der ikke ved, hvem der i øjeblikket ejer deres lejer. Denne mangel på viden er et stort rødt flag. Ring til Microsoft Support HURTIGST MULIGT. Ligesom det er problematisk, når en tjenesteejer (ofte en Exchange administrator) er udpeget til at administrere en lejer. Lejeren indeholder alle de tjenester, du eventuelt vil have i fremtiden. Lejerejeren skal være en gruppe, der kan træffe beslutning om aktivering af alle cloudtjenester i en organisation. Et andet problem er, når en lejerejergruppe bliver bedt om at administrere alle tjenester. Dette skaleres ikke til store organisationer.
- Der findes ingen sub/super-lejer. Af en eller anden grund bliver denne myte ved at gentage sig selv. Dette gælder også for [Azure AD B2C-lejere](/azure/active-directory-b2c/). Jeg hører for mange gange, "Mit B2C-miljø er i min XYZ-lejer" eller "Hvordan gør jeg flytte min Azure-lejer til min Office 365 lejer?"
- I dette dokument fokuseres der hovedsageligt på det kommercielle verdensomspændende cloudmiljø, da det er det, de fleste kunder bruger. Det kan nogle gange være nyttigt at vide om [nationale cloudmiljøer](/azure/active-directory/develop/authentication-national-cloud). Nationale cloudmiljøer har yderligere konsekvenser for at diskutere, hvilke der ikke er omfattet af denne diskussion.

## <a name="baseline-identity-articles"></a>Artikler om oprindelig identitet

Der er meget dokumentation om Microsofts identitetsplatform – Azure Active Directory (Azure AD). For dem, der lige er begyndt, det ofte føles overvældende. Selv efter at du har lært om det, kan det være en udfordring at holde dig opdateret med konstant innovation og forandring. I mine kundeinteraktioner fungerer jeg ofte som "oversætter" mellem forretningsmål og "God, Bedre, Bedste" tilgange til at håndtere disse (og menneskelige "klippenoter" for disse artikler). Der er sjældent et perfekt svar, og den "rigtige" beslutning er en balance mellem forskellige risikofaktorer. Nedenfor er nogle af de almindelige spørgsmål og forvirring områder, jeg har en tendens til at diskutere med kunder.

### <a name="provisioning"></a>Klargøring

Azure AD løser ikke mangel på styring i din identitetsverden! [Identitetsstyring](/azure/active-directory/governance/identity-governance-overview) bør være et kritisk element uafhængigt af alle cloudbeslutninger. Kravene til styring ændres over tid, og derfor er det et program og ikke et værktøj.

[Azure AD Forbind](/azure/active-directory/hybrid/whatis-azure-ad-connect) vs. [Microsoft Identity Manager](/microsoft-identity-manager/microsoft-identity-manager-2016) (MIM) vs. noget andet (tredjepart eller brugerdefineret)? Spar dig selv en masse hovedpine nu og i fremtiden og gå med Azure AD Forbind. Der er alle mulige former for smarts i dette værktøj til at håndtere særlige kundekonfigurationer og igangværende innovationer.

Nogle edge cases, der kan drive mod en mere kompleks arkitektur:

- Jeg har flere AD skove uden netværksforbindelse mellem disse. Der er en ny indstilling kaldet [Klargøring i cloudmiljøet](/azure/active-directory/cloud-provisioning/what-is-cloud-provisioning).
- Jeg har ikke Active Directory, og jeg vil heller ikke installere det. Azure AD Forbind kan konfigureres til at [synkronisere fra LDAP](/azure/active-directory/hybrid/plan-hybrid-identity-design-considerations-tools-comparison) (partner kan være påkrævet).
- Jeg skal klargøre de samme objekter til flere lejere. Dette scenarie understøttes ikke teknisk, men afhænger af definitionen af "samme".

Skal jeg tilpasse standardsynkroniseringsregler ([filterobjekter](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering), [ændre attributter](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), [alternativt logon-id osv.](/azure/active-directory/hybrid/plan-connect-userprincipalname))? Undgå det! En identitetsplatform er kun lige så værdifuld som de tjenester, der bruger den. Selvom du kan udføre alle slags nøddeagtig konfigurationer, skal du se på indvirkningen på programmer for at besvare dette spørgsmål. Hvis du filtrerer mailaktiverede objekter, vil den globale adresseliste for onlinetjenester være ufuldstændig. Hvis programmet er baseret på bestemte attributter, vil filtrering af disse have uforudsigelig indvirkning osv. Det er ikke en beslutning for identitetsteamet.

XYZ SaaS understøtter JIT-klargøring (Just-in-Time), hvorfor skal jeg synkronisere? Se ovenfor. Mange programmer har brug for "profiloplysninger" for at kunne bruges. Du kan ikke have en global adresseliste, hvis alle mailaktiverede objekter ikke er tilgængelige. Det samme gælder for [brugerklargøring](/azure/active-directory/app-provisioning/user-provisioning) i programmer, der er integreret med Azure AD.

### <a name="authentication"></a>Godkendelse

[Synkronisering af adgangskodehash](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization) (PHS) vs. [pass-through authentication](/azure/active-directory/hybrid/how-to-connect-pta-how-it-works) (PTA) vs. [federation](/azure/active-directory/hybrid/how-to-connect-fed-compatibility).

Normalt er der en lidenskabelig [debat](/azure/active-directory/hybrid/choose-ad-authn) omkring forbundet. Enklere er normalt bedre og derfor bruge PHS, medmindre du har en god grund til ikke at. Det er også muligt at konfigurere forskellige godkendelsesmetoder for forskellige DNS-domæner i den samme lejer.

Nogle kunder muliggør sammenslutning + PHS primært for:

- En mulighed for at [gå tilbage](/azure/active-directory/hybrid/plan-migrate-adfs-password-hash-sync) til (for it-katastrofeberedskab), hvis federationtjenesten ikke er tilgængelig.
- Yderligere funktioner (f.eks. [Azure AD DS](/azure/active-directory-domain-services/tutorial-configure-password-hash-sync)) og sikkerhedstjenester (f.eks. [lækkede legitimationsoplysninger](/azure/active-directory/reports-monitoring/concept-risk-events#leaked-credentials))
- Understøttelse af tjenester i Azure, der ikke forstår godkendelse i organisationsnetværket (f.eks. [Azure Files](/azure/storage/files/storage-files-active-directory-overview)).

Jeg fører ofte kunderne gennem klientgodkendelsesflowet for at tydeliggøre nogle misforståelser. Resultatet ligner billedet nedenfor, som ikke er så godt som den interaktive proces med at komme dertil.

![Eksempel på whiteboardsamtale.](../media/solutions-architecture-center/identity-beyond-whiteboard-example.png)

Denne type whiteboardtegning illustrerer, hvor sikkerhedspolitikker anvendes i flowet for en godkendelsesanmodning. I dette eksempel anvendes politikker, der gennemtvinges via AD FS (Active Directory Federation Service), på den første serviceanmodning, men ikke på efterfølgende tjenesteanmodninger. Denne funktionsmåde er mindst én grund til at flytte sikkerhedskontrolelementer til cloudmiljøet så meget som muligt.

Vi har jagtet drømmen om [enkeltlogon](/azure/active-directory/manage-apps/what-is-single-sign-on) (SSO) så længe jeg kan huske. Nogle kunder mener, at de kan opnå dette ved at vælge den "rigtige" SAMMENSLUTNING (STS) udbyder. Azure AD kan hjælpe betydeligt med at [aktivere SSO-egenskaber](/azure/active-directory/manage-apps/plan-sso-deployment), men ingen STS er magisk. Der er for mange "ældre" godkendelsesmetoder, der stadig bruges til kritiske programmer. Udvidelse af Azure AD med [partnerløsninger](/azure/active-directory/saas-apps/tutorial-list) kan håndtere mange af disse scenarier. SSO er en strategi og en rejse. Du kan ikke komme dertil uden at gå i retning af [standarder for applikationer](/azure/active-directory/develop/v2-app-types). Relateret til denne artikel er en rejse til [adgangskodeløs](/azure/active-directory/authentication/concept-authentication-passwordless) godkendelse, som heller ikke har et magisk svar.

[Multifaktorgodkendelse](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) er vigtig i dag ([her](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) for mere). Føj til [it-analyse af brugeradfærd](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) , og du har en løsning, der forhindrer de mest almindelige cyberangreb. Selv forbrugertjenester flytter sig for at kræve MFA. Alligevel mødes jeg stadig med mange kunder, der ikke ønsker at flytte til [moderne godkendelsesmetoder](../enterprise/hybrid-modern-auth-overview.md) . Det største argument, jeg hører, er, at det vil påvirke brugere og ældre programmer. Nogle gange kan et godt kick hjælpe kunderne med at komme videre – Exchange Online [annoncerede ændringer](https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-auth-and-exchange-online-february-2020-update/ba-p/1191282). Der er nu mange Azure AD [rapporter](/azure/active-directory/fundamentals/concept-fundamentals-block-legacy-authentication) tilgængelige, som kan hjælpe kunder med denne overgang.

### <a name="authorization"></a>Tilladelse

Per [Wikipedia](https://en.wikipedia.org/wiki/Authorization) er "at godkende" at definere en adgangspolitik. Mange ser på det som muligheden for at definere adgangskontrolelementer til et objekt (fil, tjeneste osv.). I den nuværende verden af cybertrusler udvikler dette koncept sig hurtigt til en dynamisk politik, der kan reagere på forskellige trusselsvektorer og hurtigt justere adgangskontrol som svar på disse. Hvis jeg f.eks. får adgang til min bankkonto fra en usædvanlig placering, får jeg yderligere bekræftelsestrin. For at gribe dette an skal vi ikke kun overveje selve politikken, men økosystemet for trusselsregistrering og signalsammenhængsmetodologier.

Politikprogrammet for Azure AD implementeres ved hjælp af [politikker for betinget adgang](/azure/active-directory/conditional-access/overview). Dette system afhænger af oplysninger fra en række andre trusselsregistreringssystemer for at kunne træffe dynamiske beslutninger. En simpel visning kan f.eks. være følgende illustration:

![Politikprogram i Azure AD.](../media/solutions-architecture-center/identity-and-beyond-illustration-3.png)

Hvis du kombinerer alle disse signaler, kan du bruge dynamiske politikker som disse:

- Hvis der registreres en trussel på din enhed, reduceres din adgang til data kun til internettet, uden at du har mulighed for at downloade.
- Hvis du downloader en usædvanlig stor mængde data, krypteres og begrænses alt, hvad du downloader.
- Hvis du tilgår en tjeneste fra en ikke-administreret enhed, bliver du blokeret fra meget følsomme data, men har tilladelse til at få adgang til ikke-begrænsede data, uden at du har mulighed for at kopiere dem til en anden placering.

Hvis du er enig i denne udvidede definition af autorisation, skal du implementere yderligere løsninger. Hvilke løsninger, du implementerer, afhænger af, hvor dynamisk politikken skal være, og hvilke trusler du vil prioritere. Eksempler på sådanne systemer er:

- [Azure AD Identity Protection](/azure/active-directory/identity-protection/)
- [Microsoft Defender for Identity](/azure-advanced-threat-protection/)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)
- [Microsoft Defender for Office 365](../security/office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) (Defender for Cloud Apps)
- [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md)
- [Microsoft Intune](/mem/intune/)
- [Microsoft Purview Information Protection](../compliance/information-protection.md)
- [Microsoft Sentinel](/azure/sentinel/)

Ud over Azure AD har forskellige tjenester og applikationer naturligvis deres egne specifikke godkendelsesmodeller. Nogle af disse gennemgås senere i afsnittet om delegering.

### <a name="audit"></a>Revision

Azure AD har detaljerede [overvågnings- og rapporteringsfunktioner](/azure/active-directory/reports-monitoring/). Disse rapporter er dog normalt ikke den eneste kilde til oplysninger, der er nødvendige for at træffe sikkerhedsmæssige beslutninger. Se mere diskussion om dette i afsnittet om delegering.

## <a name="theres-no-exchange"></a>Der er ingen Exchange

Gå ikke i panik! Det betyder ikke, at Exchange frarådes (eller SharePoint osv.). Det er stadig en kernetjeneste. Hvad jeg mener er, at teknologiudbydere i lang tid nu har overgået brugeroplevelser (UX) til at omfatte komponenter i flere tjenester. I Microsoft 365 er et simpelt eksempel "[moderne vedhæftede filer](https://support.office.com/article/Attach-files-or-insert-pictures-in-Outlook-email-messages-BDFAFEF5-792A-42B1-9A7B-84512D7DE7FC)", hvor vedhæftede filer i mails gemmes i SharePoint Online eller OneDrive for Business.

![Vedhæfter en fil til en mail.](../media/solutions-architecture-center/modern-attachments.png)

Når du ser på den Outlook klient, kan du se mange tjenester, der er "forbundet" som en del af denne oplevelse, ikke kun Exchange. Dette omfatter Azure AD, Microsoft Søg, apps, profil, overholdelse af angivne standarder og Office 365 grupper.

![Outlook grænseflade med billedforklatter.](../media/solutions-architecture-center/identity-and-beyond-conceptual-screenshot.png)

Læs om [Microsoft Fluid Framework](https://techcommunity.microsoft.com/t5/microsoft-365-blog/microsoft-ignite-blog-microsoft-fluid-framework-preview/ba-p/978268) for at få vist en prøveversion af kommende funktioner. Som prøveversion nu kan jeg læse og besvare Teams samtaler direkte i Outlook. Faktisk er den [Teams klient](https://products.office.com/microsoft-teams/download-app) et af de mere fremtrædende eksempler på denne strategi.

Samlet set bliver det sværere at tegne en klar linje mellem Office 365 og andre tjenester i Microsoft-cloudmiljøer. Jeg ser det som en stor fordel for kunderne, da de kan drage fordel af total innovation på tværs af alt, hvad vi gør, selvom de bruger én komponent. Ret cool og har vidtrækkende konsekvenser for mange kunder.

I dag oplever jeg, at mange kunde-it-grupper er struktureret omkring "produkter". Det er logisk for en verden i det lokale miljø, da du har brug for en ekspert for hvert enkelt produkt. Men jeg er helt glad for, at jeg ikke behøver at foretage fejlfinding af et Active Directory eller Exchange database igen, da disse tjenester er flyttet til cloudmiljøet. Automatisering (som cloud-type er) fjerner visse gentagne manuelle job (se, hvad der skete med fabrikker). Disse opgaver erstattes dog af mere komplekse krav til forståelse af interaktion på tværs af tjenester, indvirkning, forretningsbehov osv. Hvis du er villig til at [lære](/learn/), er der fantastiske muligheder, der aktiveres af cloudtransformation. Før jeg går i teknologi, taler jeg ofte med kunderne om administration af ændringer i it-færdigheder og teamstrukturer.

Til alle SharePoint fans og udviklere skal du holde op med at spørge "Hvordan kan jeg gøre XYZ i SharePoint online?" Brug [Power Automate](/power-automate/) (eller Flow) til arbejdsprocesser. Det er en meget mere effektiv platform. Brug [Azure Bot Framework](/azure/bot-service/) til at oprette en bedre UX til din liste over 500-K-elementer. Begynd at bruge [Microsoft Graph](https://developer.microsoft.com/graph/) i stedet for CSOM. [Microsoft Teams](/MicrosoftTeams/Teams-overview) omfatter SharePoint, men også en verden mere. Der er mange andre eksempler, jeg kan liste. Der er et stort og vidunderligt univers derude. Åbn døren, og [begynd at udforske]().

Den anden almindelige indvirkning er på overholdelsesområdet. Denne tilgang på tværs af tjenester ser ud til at forvirre mange politikker for overholdelse af angivne standarder. Jeg ser hele tiden organisationer med teksten "Jeg skal journale al mailkommunikation til et eDiscovery-system". Hvad betyder det egentlig, når mail ikke længere blot er en mail, men et vindue til andre tjenester? Office 365 har en omfattende tilgang til [overholdelse af angivne standarder](../compliance/index.yml), men ændring af personer og processer er ofte meget vanskeligere end teknologi.

Der er mange andre mennesker og proceskonsekvenser. Efter min mening er denne faktor et kritisk og underdiskuteret område. Måske mere i en anden artikel.

## <a name="tenant-structure-options"></a>Indstillinger for lejerstruktur

### <a name="single-tenant-vs-multi-tenant"></a>Enkelt lejer i forhold til flere lejere

Generelt bør de fleste kunder kun have én produktionslejer. Der er mange grunde til, at flere lejere er udfordrende (giv det en [Bing søgning](https://www.bing.com/search?q=office%20365%20multiple%20tenants)) eller læse dette [whitepaper](https://aka.ms/multi-tenant-user). Samtidig har mange virksomhedskunder, jeg arbejder med, en anden (lille) lejer til it-læring, test og eksperimentering. Azure [Lighthouse](https://azure.microsoft.com/services/azure-lighthouse/) gør det nemmere at få adgang til Azure på tværs af lejere. Office 365 og mange andre SaaS-tjenester har grænser for scenarier på tværs af lejere. Der er meget at overveje i [Azure AD B2B-scenarier](/azure/active-directory/b2b/what-is-b2b).

Mange kunder ender med flere produktionslejere efter en fusion og overtagelse (M&A) og ønsker at konsolidere. I dag er det ikke enkelt og kræver Microsoft Consulting Services (MCS) eller en partner plus tredjepartssoftware. Der er løbende teknisk arbejde med at håndtere forskellige scenarier med kunder med flere lejere i fremtiden.

Nogle kunder vælger at gå med mere end én lejer. Dette bør være en meget omhyggelig beslutning og næsten altid forretningsårsag drevet! Nogle eksempler omfatter følgende årsager:

- En holdingtypevirksomhedsstruktur, hvor der ikke kræves nemt samarbejde mellem forskellige enheder, og der er stærke administrative og andre isolationsbehov.
- Efter en overtagelse træffes der en forretningsbeslutning om at adskille to enheder.
- Simulering af en kundes miljø, der ikke ændrer kundens produktionsmiljø.
- Udvikling af software til kunder.

I disse scenarier med flere lejere vil kunder ofte bevare en eller anden konfiguration på tværs af lejere eller rapportere om konfigurationsændringer og drifts. Det betyder ofte, at du skal flytte fra manuelle ændringer til konfiguration som kode. Microsoft Premiere support tilbyder en workshop for disse typer af krav baseret på denne offentlige IP: <https://Microsoft365dsc.com>.

### <a name="multi-geo"></a>Multi-Geo

Til [Multi-Geo](../enterprise/microsoft-365-multi-geo.md) eller ikke til Multi-Geo, er det spørgsmålet. Med Office 365 Multi-Geo kan du klargøre og gemme inaktive data på de geografiske placeringer, du har valgt at opfylde kravene til [dataopbevaring](../enterprise/o365-data-locations.md). Der er mange misforståelser om denne funktion. Vær opmærksom på følgende:

- Det giver ikke ydeevnefordele. Det kan gøre ydeevnen dårligere, hvis [netværksdesignet](https://aka.ms/office365networking) ikke er korrekt. Få enheder "tæt" på Microsoft-netværket, ikke nødvendigvis på dine data.
- Det er ikke en løsning til [overholdelse af GDPR](https://www.microsoft.com/trust-center/privacy/gdpr-overview). GDPR fokuserer ikke på datasuverænitet eller lagerplaceringer. Der er andre overholdelsesrammer for dette.
- Det løser ikke delegering af administration (se nedenfor) eller [informationsbarrierer](../compliance/information-barriers.md).
- Det er ikke det samme som flerlejer og kræver yderligere arbejdsprocesser [til klargøring af brugere](https://github.com/MicrosoftDocs/azure-docs-pr/blob/master/articles/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation.md) .
- Den [flytter ikke din lejer](../enterprise/moving-data-to-new-datacenter-geos.md) (din Azure AD) til et andet geografisk område.

## <a name="delegation-of-administration"></a>Delegering af administration

I de fleste store organisationer er adskillelse af opgaver og rollebaseret adgangskontrol en nødvendig realitet. Jeg undskylder i forvejen. Denne aktivitet er ikke så enkel, som nogle kunder ønsker. Kunder, juridiske krav, overholdelse af angivne standarder og andre krav er forskellige og ofte modstridende over hele verden. Enkelhed og fleksibilitet er ofte på modsatte sider af hinanden. Må ikke få mig forkert, kan vi gøre et bedre job på dette. Der har været (og vil være) betydelige forbedringer over tid. Besøg dit lokale [Microsoft Technology Center](https://www.microsoft.com/mtc) for at finde ud af, hvilken model der passer til dine forretningsbehov, uden at læse 379230-dokumenter! Her vil jeg fokusere på, hvad du skal tænke om, og ikke hvorfor det er på denne måde. Nedenfor er fem forskellige områder at planlægge og nogle af de almindelige spørgsmål, jeg har mødt.

### <a name="azure-ad-and-microsoft-365-admin-centers"></a>administrationscentre for Azure AD og Microsoft 365

Der er en lang og voksende liste over [indbyggede roller](/azure/active-directory/roles/permissions-reference). Hver rolle består af en liste over rolletilladelser, der er grupperet for at tillade, at bestemte handlinger kan udføres. Du kan se disse tilladelser under fanen "Beskrivelse" i hver rolle. Du kan også se en mere læsevenlig version af disse tilladelser i Microsoft 365 Administration Center. Definitionerne for indbyggede roller kan ikke ændres. Generelt grupperer jeg disse roller i tre kategorier:

- **Global administrator**: Denne "alle effektive" rolle skal være [meget beskyttet](../enterprise/protect-your-global-administrator-accounts.md), ligesom du ville gøre i andre systemer. Typiske anbefalinger omfatter: ingen permanent tildeling og brug Azure AD Privileged Identity Management (PIM), stærk godkendelse osv. Interessant nok giver denne rolle dig ikke adgang til alt som standard. Jeg oplever typisk forvirring om adgang til overholdelse og Azure-adgang, som drøftes senere. Denne rolle kan dog altid tildele adgang til andre tjenester i lejeren.
- **Specifikke tjenesteadministratorer**: Nogle tjenester (Exchange, SharePoint, Power BI osv.) bruger administrationsroller på højt niveau fra Azure AD. Denne funktionsmåde er ikke ensartet på tværs af alle tjenester, og der er flere tjenestespecifikke roller, der beskrives senere.
- **Funktionel**: Der er en lang (og voksende) liste over roller, der fokuserer på bestemte handlinger (gæsteinvitation osv.). Med jævne mellemrum tilføjes flere af disse roller baseret på kundernes behov.

Det er ikke muligt at delegere alt (selvom afstanden mindskes), hvilket betyder, at rollen Global administrator nogle gange skal bruges. Konfiguration som kode og automatisering bør overvejes i stedet for personmedlemskab af denne rolle.

**Bemærk**! Microsoft 365 Administration har en mere brugervenlig grænseflade, men har en delmængde af funktioner sammenlignet med den Azure AD administratoroplevelse. Begge portaler bruger de samme Azure AD roller, så ændringer sker på samme sted. Tip! Hvis du vil have en administrationsfokuseret brugergrænseflade til administration af identiteter uden alt Azure-rod, skal du bruge <https://aad.portal.azure.com>.

Hvad er der i navnet? Angiv ikke forudsætninger ud fra navnet på rollen. Sprog er ikke et særligt præcist værktøj. Målet bør være at definere handlinger, der skal delegeres, før du ser på, hvilke roller der er behov for. Tilføjelse af en person til rollen "Sikkerhedslæser" får dem ikke til at se sikkerhedsindstillinger på tværs af alt.

Muligheden for at oprette [brugerdefinerede roller](/azure/active-directory/users-groups-roles/roles-custom-overview) er et almindeligt spørgsmål. Denne funktion er begrænset i Azure AD i dag (se nedenfor), men den vil vokse i egenskaber over tid. Jeg tænker på disse brugerdefinerede roller, som gælder for funktioner i Azure AD og strækker sig muligvis ikke over "down" hierarkimodellen (beskrevet ovenfor). Når jeg beskæftiger mig med "brugerdefineret", jeg har tendens til at gå tilbage til min principale for "enkel er bedre."

Et andet almindeligt spørgsmål er muligheden for at udvide roller til et undersæt af en mappe. Et eksempel er f.eks. "Helpdesk-administrator kun for brugere i EU". Det er meningen, at [administrative enheder](/azure/active-directory/users-groups-roles/directory-administrative-units) (AU) skal løse dette. Ligesom ovenfor tænker jeg på disse områder, som gælder for funktioner i Azure AD og kan ikke spænde "ned". Visse roller giver naturligvis ikke mening at omfatte (globale administratorer, tjenesteadministratorer osv.).

I dag kræver alle disse roller direkte medlemskab (eller dynamisk tildeling, hvis du bruger [Azure AD PIM](/azure/active-directory/privileged-identity-management/)). Det betyder, at kunderne skal administrere disse direkte i Azure AD, og disse roller kan ikke være baseret på et medlemskab af en sikkerhedsgruppe. Jeg er ikke fan af at oprette scripts til at administrere disse roller, da det ville være nødvendigt at køre med øgede rettigheder. Jeg anbefaler generelt API-integration med processystemer som ServiceNow eller brug af partnerstyringsværktøjer som F.eks. Saviynt. Der er tekniske arbejde i gang med at løse dette over tid.

Jeg nævnte [Azure AD PIM](/azure/active-directory/privileged-identity-management/) et par gange. Der er en tilsvarende Microsoft Identity Manager(MIM) [PAM-løsning (Privileged Access Management](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services)) til kontrolelementer i det lokale miljø. Det kan også være en god idé at se på [PAWs (Privileged Access Workstations](/windows-server/identity/securing-privileged-access/privileged-access-workstations)) og [Azure AD Identity Governance](/azure/active-directory/governance/identity-governance-overview). Der er også forskellige tredjepartsværktøjer, som kan muliggøre just-in-time, just-enough og dynamisk rolle udvidede. Denne funktion er normalt en del af en større diskussion om sikring af et miljø.

Nogle gange kræver scenarier tilføjelse af en ekstern bruger til en rolle (se afsnittet med flere lejere ovenfor). Det her fungerer fint. [Azure AD B2B](/azure/active-directory/b2b/) er en anden stor og sjov artikel at gennemgå, måske i en anden artikel.

### <a name="microsoft-365-defender-and-microsoft-365-purview-compliance-portals"></a>Microsoft 365 Defender og Microsoft 365 Purview-overholdelsesportaler

**Mail & samarbejdsroller** på [Microsoft 365 Defender-portalen](../security/office-365-security/permissions-microsoft-365-security-center.md) og **_Rollegrupper til Microsoft Purview-løsninger_* i [Microsoft 365 Purview-overholdelsesportalen](../compliance/microsoft-365-compliance-center-permissions.md) er en samling af "rollegrupper", som er separate og adskiller sig fra Azure AD roller. Det kan være forvirrende, fordi nogle af disse rollegrupper har samme navn som Azure AD roller (f.eks. Sikkerhedslæser), men de kan have forskellige medlemskaber. Jeg foretrækker at bruge Azure AD roller. Hver rollegruppe består af en eller flere "roller" (se, hvad jeg mener om genbrug af det samme ord?) og har medlemmer fra Azure AD, som er mailaktiverede objekter. Du kan også oprette en rollegruppe med samme navn som en rolle, som måske eller måske ikke indeholder rollen (undgå denne forvirring).

På en måde er disse tilladelser en udvikling af modellen for Exchange rollegrupper. Exchange Online har dog sin egen grænseflade [til administration af rollegrupper](/exchange/permissions-exo). Nogle rollegrupper i Exchange Online er låst og administreret fra Azure AD eller Microsoft 365 Defender og Microsoft 365 Purview-overholdelsesportaler, men andre kan have de samme eller lignende navne og administreres i Exchange Online (føjer til forvirring). Jeg anbefaler, at du undgår at bruge Exchange Online brugergrænseflade, medmindre du har brug for områder til Exchange administration.

Du kan ikke oprette brugerdefinerede roller. Roller defineres af tjenester, der er oprettet af Microsoft, og vokser, efterhånden som nye tjenester introduceres. Denne funktionsmåde svarer i konceptet til [roller, der er defineret af programmer](/azure/active-directory/develop/howto-add-app-roles-in-azure-ad-apps) i Azure AD. Når nye tjenester er aktiveret, skal der ofte oprettes nye rollegrupper for at give eller delegere adgang til disse (f.eks. [styring af insiderrisiko](../compliance/insider-risk-management-configure.md).

Disse rollegrupper kræver også direkte medlemskab og må ikke indeholde Azure AD grupper. I dag understøttes disse rollegrupper desværre ikke af Azure AD PIM. Ligesom Azure AD roller har jeg en tendens til at anbefale administration af disse rollegrupper via API'er eller et produkt til partnerstyring som F.eks. Saviynt eller andre.

Microsoft 365 Defender portal og Microsoft 365 roller i Purview-overholdelsesportalen strækker sig over Microsoft 365, og du kan ikke afgrænse disse rollegrupper til et undersæt af miljøet (f.eks. med administrative enheder i Azure AD). Mange kunder spørger, hvordan de kan subdelegate. Det kan f.eks. være "kun at oprette en DLP-politik for EU-brugere". Hvis du i dag har rettigheder til en bestemt funktion på Microsoft 365 Defender- og Microsoft 365 Purview-overholdelsesportalerne, har du rettigheder til alt, der er omfattet af denne funktion i lejeren. Mange politikker har dog egenskaber til at målrette et undersæt af miljøet (f.eks. "gør disse [mærkater](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) kun tilgængelige for disse brugere"). Korrekt styring og kommunikation er en vigtig komponent til at undgå konflikter. Nogle kunder vælger at implementere en "konfiguration som kode"-tilgang for at håndtere underdelegering i Microsoft 365 Defender og Microsoft 365 Purview-overholdelsesportaler. Nogle specifikke tjenester understøtter underdelegering (se nedenfor).

### <a name="service-specific"></a>Tjenestespecifik

Som tidligere nævnt ønsker mange kunder at opnå en mere detaljeret delegeringsmodel. Et almindeligt eksempel: "Administrer kun XYZ-tjenesten for division X-brugere og -placeringer" (eller en anden dimension). Muligheden for at gøre dette afhænger af hver enkelt tjeneste og er ikke ensartet på tværs af tjenester og funktioner. Desuden kan hver tjeneste have en separat og entydig RBAC-model. I stedet for at diskutere alle disse modeller (det vil tage evigt), tilføjer jeg relevante links for hver tjeneste. Denne liste er ikke komplet, men den vil hjælpe dig i gang.

- **Exchange Online** – (/exchange/permissions-exo/permissions-exo)
- **SharePoint Online** – (/sharepoint/manage-site-collection-administrators)
- **Microsoft Teams** - (/microsoftteams/itadmin-readiness)
- **eDiscovery** – (.. /compliance/index.yml)
  - **Tilladelsesfiltrering** – (.. /compliance/index.yml)
  - **Overholdelsesgrænser** - (.. /compliance/set-up-compliance-boundaries.md)
  - **eDiscovery (Premium)** - (.. /compliance/overview-ediscovery-20.md)
- **Yammer** - (/yammer/manage-yammer-users/manage-yammer-admins)
- **Multi-Geo** – (.. /enterprise/add-a-sharepoint-geo-admin.md)
- **Dynamics 365** – (/dynamics365/)

  Bemærk! Dette link er til roden af dokumentationen. Der er flere typer tjenester med variationer i administrations-/delegeringsmodellen.

- **Power Platform** – (/power-platform/admin/admin-documentation)
  - **Power Apps** – (/power-platform/admin/wp-security)

    Bemærk! Der er flere typer med variationer i administrations-/delegeringsmodellerne.

  - **Power Automate** – (/power-automate/environments-overview-admin)
  - **Power BI** – (/power-bi/service-admin-governance)

    Bemærk! Sikkerhed og delegering af dataplatforme (som Power BI er en komponent) er et komplekst område.

- **MEM/Intune** - (/mem/intune/fundamentals/role-based-access-control)
- **Microsoft Defender for Endpoint** – (/windows/security/threat-protection/microsoft-defender-atp/user-roles)
- **Microsoft 365 Defender** - (.. /security/defender/m365d-permissions.md)
- **Microsoft Defender for Cloud Apps** – (/cloud-app-security/manage-admins)
- **Stream** – (/stream/assign-administrator-user-role)
- **Informationsbarrierer** - (.. /compliance/information-barriers.md)

### <a name="activity-logs"></a>Aktivitetslogge

Office 365 har en [samlet overvågningslog](../compliance/search-the-audit-log-in-security-and-compliance.md). Det er en meget [detaljeret log](/office/office-365-management-api/office-365-management-activity-api-schema), men læs ikke for meget ind i navnet. Den indeholder muligvis ikke alt, hvad du ønsker eller har brug for til dine behov for sikkerhed og overholdelse af angivne standarder. Nogle kunder er også meget interesseret i [Audit (Premium)](../compliance/advanced-audit.md).

Eksempler på Microsoft 365 logfiler, der tilgås via andre API'er, omfatter følgende funktioner:

- [Azure AD](/azure/azure-monitor/platform/diagnostic-settings) (aktiviteter, der ikke er relateret til Office 365)
- [Exchange meddelelsessporing](/powershell/module/exchange/get-messagetrace)
- Threat/UEBA Systems beskrevet ovenfor (f.eks. Azure AD Identity Protection, Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint osv.)
- [Microsoft Purview Information Protection](../compliance/data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/api-power-bi)
- [Microsoft Graph](https://graph.microsoft.com)

Det er vigtigt først at identificere alle de logkilder, der er nødvendige for et program til sikkerhed og overholdelse af angivne standarder. Bemærk også, at forskellige logge har forskellige opbevaringsgrænser på stedet.

Fra administrationsdelegeringsperspektivet har de fleste Microsoft 365 aktivitetslogge ikke en indbygget RBAC-model. Hvis du har tilladelse til at se en log, kan du se alt i den. Et almindeligt eksempel på et kundekrav er: "Jeg vil kun kunne forespørge om aktivitet for EU-brugere" (eller en anden dimension). For at opnå dette krav skal vi overføre logge til en anden tjeneste. I Microsoft-clouden anbefaler vi, at du overfører den til enten [Microsoft Sentinel](/azure/sentinel/overview) eller [Log Analytics](/azure/azure-monitor/learn/quick-create-workspace).

Diagram på højt niveau:

![diagram over logkilder for et sikkerheds- og overholdelsesprogram.](../media/solutions-architecture-center/identity-beyond-illustration-4.png)

Diagrammet ovenfor repræsenterer indbyggede funktioner til at sende logge til Event Hub og/eller Azure Storage og/eller Azure Log Analytics. Det er endnu ikke alle systemer, der er klar til brug. Men der er andre metoder til at sende disse logge til det samme lager. Du kan f.eks. se [Beskyttelse af dine Teams med Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/protecting-your-teams-with-azure-sentinel/ba-p/1265761).

Kombination af alle loggene på én lagerplacering omfatter en ekstra fordel, f.eks. tværgående korrelation, brugerdefinerede opbevaringstider, tilføjelse af data, der er nødvendige for at understøtte RBAC-modellen osv. Når dataene er i dette lagersystem, kan du oprette et Power BI dashboard (eller en anden type visualisering) med en passende RBAC-model.

Logfiler behøver ikke kun at blive dirigeret til ét sted. Det kan også være en fordel at integrere [Office 365 logfiler med Microsoft Defender for Cloud Apps](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) eller en brugerdefineret RBAC-model i [Power BI](../admin/usage-analytics/usage-analytics.md). Forskellige lagre har forskellige fordele og målgrupper.

Det er værd at nævne, at der er et meget omfattende indbygget analysesystem til sikkerhed, trusler, sårbarheder osv. i en tjeneste kaldet [Microsoft 365 Defender](../security/defender/microsoft-365-defender.md).

Mange store kunder vil overføre disse logdata til et tredjepartssystem (f.eks. SIEM). Der er forskellige tilgange til dette, men generelt er [Azure Event Hub](/azure/azure-monitor/platform/stream-monitoring-data-event-hubs) og [Graph](/graph/security-integration) gode udgangspunkter.

### <a name="azure"></a>Azure

Jeg bliver ofte spurgt, om der er en måde at adskille roller med mange rettigheder mellem Azure AD, Azure og SaaS (f.eks. global administrator for Office 365 men ikke Azure). Ikke rigtig. Arkitektur med flere lejere er nødvendig, hvis fuldstændig administrativ adskillelse er påkrævet, men det medfører betydelig [kompleksitet](https://aka.ms/multi-tenant-user) (se ovenfor). Alle disse tjenester er en del af den samme sikkerheds-/identitetsgrænse (se hierarkimodellen ovenfor).

Det er vigtigt at forstå relationer mellem forskellige tjenester i den samme lejer. Jeg arbejder sammen med mange kunder, der bygger forretningsløsninger, der spænder over Azure, Office 365 og Power Platform (og ofte også cloudtjenester i det lokale miljø og tredjepartscloudtjenester). Et almindeligt eksempel:

1. Jeg vil gerne samarbejde om et sæt dokumenter/billeder/osv. (Office 365)
2. Send hver enkelt af dem gennem en godkendelsesproces (Power Platform)
3. Når alle komponenter er godkendt, skal du samle disse elementer i en samlet eller samlet leverance (Azure) [Microsoft Graph API](/azure/active-directory/develop/microsoft-graph-intro) er din bedste ven her. Ikke umuligt, men betydeligt mere komplekst at designe en løsning, der strækker sig over [flere lejere](/azure/active-directory/develop/single-and-multi-tenant-apps).

Azure Role-Based Access Control (RBAC) muliggør detaljeret adgangsstyring for Azure. Ved hjælp af RBAC kan du administrere adgang til ressourcer ved at tildele brugerne færrest tilladelser til at udføre deres job. Detaljer er ikke omfattet af dette dokument, men du kan finde flere oplysninger om RBAC under [Hvad er rollebaseret adgangskontrol i Azure?](/azure/role-based-access-control/overview) RBAC er vigtig, men kun en del af overvejelserne om styring af Azure. [Cloud Adoption Framework](/azure/cloud-adoption-framework/govern/) er et godt udgangspunkt for at få mere at vide. Jeg kan godt lide, hvordan min ven, [Andres Ravinet, guider](https://www.linkedin.com/in/andres-ravinet/) kunderne trin for trin gennem forskellige komponenter for at beslutte sig for tilgangen. Visning på højt niveau for forskellige elementer (ikke så god som processen til at få vist den faktiske kundemodel) er noget i stil med dette:

![Overordnet visning af Azure-komponenter til uddelegeret administration.](../media/solutions-architecture-center/identity-beyond-illustration-5.png)

Som du kan se ovenfor, bør mange andre tjenester betragtes som en del af designet (f.eks. [Azure-politikker](/azure/governance/policy/overview), [Azure Blueprints](/azure/governance/blueprints/overview), [administrationsgrupper](/azure/governance/management-groups/) osv.).

## <a name="conclusion"></a>Konklusion

Startede som en kort oversigt, endte længere end forventet. Jeg håber, at du nu er klar til at gå i dybden med at oprette delegeringsmodel for din organisation. Denne samtale er meget almindelig med kunder. Der er ingen model, der fungerer for alle. Venter på et par planlagte forbedringer fra Microsoft-teknikere, før vi dokumenterer almindelige mønstre, som vi ser på tværs af kunder. I mellemtiden kan du samarbejde med dit Microsoft-kontoteam om at arrangere et besøg i det nærmeste [Microsoft Technology Center](https://www.microsoft.com/mtc). Vi ses der!
