---
title: Nul tillid konfigurationer af identitet og enhedsadgang – Microsoft 365 for enterprise
description: Beskriver Microsofts anbefalinger og kernekoncepter til installation af politikker og konfigurationer for sikre mails, dokumenter og apps til Nul tillid.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-overview
- m365solution-zero-trust
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: 97e81f020c18a4f51e8af99f3633c8edb2559a41
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750358"
---
# <a name="zero-trust-identity-and-device-access-configurations"></a>Konfigurationer af Nul tillid-identitet og enhedsadgang

Sikkerhedsarkitekturer, der er afhængige af netværksfirewalls og virtuelle private netværk for at isolere og begrænse adgangen til en organisations teknologiressourcer og -tjenester, er ikke længere tilstrækkelige for en arbejdsstyrke, der regelmæssigt kræver adgang til programmer og ressourcer, der findes ud over virksomhedens traditionelle netværksgrænser.

For at håndtere denne nye verden af databehandling anbefaler Microsoft på det kraftigste Nul tillid sikkerhedsmodellen, som er baseret på disse ledende principper:

- Bekræft eksplicit

  Godkend og godkend altid baseret på alle tilgængelige datapunkter. Det er her, Nul tillid politikker for identitet og enhedsadgang er afgørende for at logge på og løbende validering.

- Brug adgang med færrest rettigheder

  Begræns brugeradgang med Just-In-Time og Just-Enough-Access (JIT/JEA), risikobaserede tilpassede politikker og databeskyttelse.

- Antag brud

  Minimer eksplosionsradius og segmentadgang. Bekræft kryptering fra slutpunkt til slutpunkt, og brug analyser til at få synlighed, skabe trusselsregistrering og forbedre forsvaret.

Her er den overordnede arkitektur for Nul tillid.

:::image type="content" source="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png" alt-text="Microsoft Nul tillid-arkitekturen" lightbox="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png":::

Nul tillid politikker for identitets- og enhedsadgang omhandler det eksplicit ledende princip for **bekræft** for:

- Identiteter

  Når en identitet forsøger at få adgang til en ressource, skal du bekræfte denne identitet med stærk godkendelse og sikre, at den anmodede adgang er kompatibel og typisk.

- Enheder (også kaldet slutpunkter)

  Overvåg og gennemtving krav til enhedens tilstand og overholdelse af angivne standarder for sikker adgang.

- Programmer

  Anvend kontrolelementer og teknologier til at finde skygge-it, sikre relevante tilladelser i appen, portadgang baseret på analyse i realtid, overvåge unormal funktionsmåde, kontrollere brugerhandlinger og validere sikre konfigurationsindstillinger.

I denne artikelserie beskrives et sæt konfigurationer af forudsætninger for identitet og adgang til enheden og et sæt betinget adgang til Azure Active Directory (Azure AD), Microsoft Intune og andre politikker for Nul tillid adgang til Microsoft 365 for Enterprise-cloudapps og -tjenester, andre SaaS-tjenester og programmer i det lokale miljø, der er publiceret med Azure AD Programproxy.

Nul tillid indstillinger og politikker for identitets- og enhedsadgang anbefales på tre niveauer: udgangspunkt, virksomhedssikkerhed og specialiseret sikkerhed for miljøer med højt regulerede eller klassificerede data. Disse niveauer og deres tilsvarende konfigurationer giver ensartede niveauer af Nul tillid beskyttelse på tværs af dine data, identiteter og enheder.

Disse funktioner og deres anbefalinger:

- Understøttes i Microsoft 365 E3 og Microsoft 365 E5.
- Justeres i forhold til [Microsoft Secure Score](../defender/microsoft-secure-score.md) samt [identitetsscore i Azure AD](/azure/active-directory/fundamentals/identity-secure-score) og øger disse scorer for din organisation.
- Hjælper dig med at implementere disse [fem trin til sikring af din identitetsinfrastruktur](/azure/security/azure-ad-secure-steps).

Hvis din organisation har unikke miljøkrav eller -kompleksiteter, kan du bruge disse anbefalinger som udgangspunkt. De fleste organisationer kan dog implementere disse anbefalinger som foreskrevet.

Se denne video for at få et hurtigt overblik over konfigurationer af identitets- og enhedsadgang til Microsoft 365 for enterprise.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxEDQ]

> [!NOTE]
> Microsoft sælger også licenser til Enterprise Mobility + Security (EMS) for Office 365 abonnementer. EMS E3- og EMS E5-funktioner svarer til funktionerne i Microsoft 365 E3 og Microsoft 365 E5. Se [EMS-planer](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/compare-plans-and-pricing) for at få flere oplysninger.

## <a name="intended-audience"></a>Tiltænkt målgruppe

Disse anbefalinger er beregnet til virksomhedsarkitekter og it-teknikere, der kender Microsoft 365 Cloud produktivitet og sikkerhedstjenester, som omfatter Azure AD (identitet), Microsoft Intune (enhedshåndtering) og Microsoft Purview Information Protection (databeskyttelse).

### <a name="customer-environment"></a>Kundemiljø

De anbefalede politikker gælder for virksomhedsorganisationer, der arbejder både i Microsoft-cloudmiljøet og for kunder med hybrid identitetsinfrastruktur, som er et AD DS-område (Active Directory i det lokale miljø Domain Services), der synkroniseres med en Azure AD lejer.

Mange af de angivne anbefalinger er afhængige af tjenester, der kun er tilgængelige med Microsoft 365 E5, Microsoft 365 E3 med tilføjelsesprogrammet E5 Security, EMS E5 eller Azure AD Premium P2-licenser.

For de organisationer, der ikke har disse licenser, anbefaler Microsoft, at du i det mindste [implementerer sikkerhedsstandarder](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), som er inkluderet i alle Microsoft 365-planer.

### <a name="caveats"></a>Forbehold

Din organisation kan være underlagt lovmæssige eller andre krav til overholdelse af angivne standarder, herunder specifikke anbefalinger, der kan kræve, at du anvender politikker, der afviger fra disse anbefalede konfigurationer. Disse konfigurationer anbefaler brugskontrolelementer, der ikke historisk set har været tilgængelige. Vi anbefaler disse kontrolelementer, fordi vi mener, at de repræsenterer en balance mellem sikkerhed og produktivitet.

Vi har gjort vores bedste for at tage højde for en lang række beskyttelseskrav til organisationen, men vi kan ikke tage højde for alle de mulige krav eller for alle de unikke aspekter af din organisation.

## <a name="three-tiers-of-protection"></a>Tre beskyttelsesniveauer

De fleste organisationer har specifikke krav til sikkerhed og databeskyttelse. Disse krav varierer efter branchesegment og jobfunktioner i organisationer. Din juridiske afdeling og administratorer kan f.eks. kræve yderligere sikkerheds- og informationsbeskyttelseskontrol omkring deres mailkorrespondance, der ikke kræves til andre forretningsenheder.

Hver branche har også sit eget sæt specialiserede forskrifter. I stedet for at angive en liste over alle mulige sikkerhedsindstillinger eller en anbefaling pr. branchesegment eller jobfunktion er der givet anbefalinger til tre forskellige niveauer af sikkerhed og beskyttelse, der kan anvendes baseret på granulariteten af dine behov.

- **Udgangspunkt**: Vi anbefaler, at alle kunder etablerer og bruger en minimumstandard til beskyttelse af data samt de identiteter og enheder, der har adgang til dine data. Du kan følge disse anbefalinger for at give en stærk standardbeskyttelse som udgangspunkt for alle organisationer.
- **Virksomhed**: Nogle kunder har et undersæt af data, der skal beskyttes på højere niveauer, eller de kan kræve, at alle data er beskyttet på et højere niveau. Du kan anvende øget beskyttelse på alle eller bestemte datasæt i dit Microsoft 365-miljø. Vi anbefaler, at du beskytter identiteter og enheder, der har adgang til følsomme data med sammenlignelige sikkerhedsniveau.
- **Specialiseret sikkerhed**: Efter behov har nogle få kunder en lille mængde data, der er højt klassificeret, udgør forretningshemmeligheder eller er reguleret. Microsoft leverer funktioner, der kan hjælpe disse kunder med at opfylde disse krav, herunder yderligere beskyttelse af identiteter og enheder.

:::image type="content" source="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png" alt-text="Security-keglen" lightbox="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png":::

I denne vejledning kan du se, hvordan du implementerer Nul tillid beskyttelse af identiteter og enheder for hvert af disse beskyttelsesniveauer. Brug denne vejledning som minimum for din organisation, og tilpas politikkerne, så de opfylder organisationens specifikke krav.

Det er vigtigt at bruge ensartede beskyttelsesniveauer på tværs af dine identiteter, enheder og data. Beskyttelse af brugere med prioritetskonti&mdash;, f.eks. direktører, ledere, ledere og andre&mdash;, bør f.eks. omfatte det samme niveau af beskyttelse af deres identiteter, deres enheder og de data, de har adgang til. 
<!--

The **Zero Trust identity and device protection for Microsoft 365** architecture model shows you which capabilities are comparable.

[![Thumb image for Zero Trust Identity and device protection for Microsoft 365 poster.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-thumbnail.png)](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) <br> [View as a PDF](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.pdf)  \| [Download as a Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.vsdx)

--> 

Derudover skal du se løsningen [Installér information Protection for data privacy regulations](../../solutions/information-protection-deploy.md) for protect information lagret i Microsoft 365.

## <a name="security-and-productivity-trade-offs"></a>Afvejninger af sikkerhed og produktivitet

Implementering af en hvilken som helst sikkerhedsstrategi kræver afvejninger mellem sikkerhed og produktivitet. Det er nyttigt at evaluere, hvordan hver enkelt beslutning påvirker balancen mellem sikkerhed, funktionalitet og brugervenlighed.

:::image type="content" source="../../media/microsoft-365-policies-configurations/security-triad.png" alt-text="Sikkerhedstrianaden, der balancerer sikkerhed, funktionalitet og brugervenlighed" lightbox="../../media/microsoft-365-policies-configurations/security-triad.png":::

Anbefalingerne er baseret på følgende principper:

- Kend dine brugere, og vær fleksibel i forhold til deres krav til sikkerhed og funktionalitet.
- Anvend en sikkerhedspolitik lige i tide, og sørg for, at den giver mening.

## <a name="services-and-concepts-for-zero-trust-identity-and-device-access-protection"></a>Tjenester og begreber for Nul tillid identitets- og beskyttelse af enhedsadgang

Microsoft 365 til virksomheder er udviklet til store organisationer, så alle kan være kreative og arbejde sikkert sammen.

Dette afsnit indeholder en oversigt over de Microsoft 365-tjenester og -funktioner, der er vigtige for Nul tillid identitets- og enhedsadgang.

### <a name="azure-ad"></a>Azure AD

Azure AD indeholder en komplet pakke med funktioner til administration af identiteter. Vi anbefaler, at du bruger disse funktioner til at sikre adgang.

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|[Multifaktorgodkendelse (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA kræver, at brugerne angiver to former for bekræftelse, f.eks. en brugeradgangskode plus en meddelelse fra Appen Microsoft Authenticator eller et telefonopkald. MFA reducerer i høj grad risikoen for, at stjålne legitimationsoplysninger kan bruges til at få adgang til dit miljø. Microsoft 365 bruger tjenesten Azure AD multifaktorgodkendelse til MFA-baserede logons.|Microsoft 365 E3 eller E5|
|[Betinget adgang](/azure/active-directory/conditional-access/overview)|Azure AD evaluerer betingelserne for brugerens logon og bruger politikker for betinget adgang til at bestemme den tilladte adgang. I denne vejledning viser vi f.eks., hvordan du opretter en politik for betinget adgang for at kræve overholdelse af angivne standarder for enheden for at få adgang til følsomme data. Dette reducerer i høj grad risikoen for, at en hacker med deres egen enhed og stjålne legitimationsoplysninger kan få adgang til dine følsomme data. Den beskytter også følsomme data på enhederne, fordi enhederne skal opfylde specifikke krav til tilstand og sikkerhed.|Microsoft 365 E3 eller E5|
|[Azure AD grupper](/azure/active-directory/fundamentals/active-directory-manage-groups)|Politikker for betinget adgang, enhedshåndtering med Intune og endda tilladelser til filer og websteder i din organisation er afhængige af tildelingen til brugerkonti eller Azure AD grupper. Vi anbefaler, at du opretter Azure AD grupper, der svarer til de beskyttelsesniveauer, du implementerer. For eksempel er dine chefmedarbejdere sandsynligvis højere værdimål for hackere. Det giver derfor mening at føje disse medarbejderes brugerkonti til en Azure AD gruppe og tildele denne gruppe til politikker for betinget adgang og andre politikker, der gennemtvinger et højere beskyttelsesniveau for adgang.|Microsoft 365 E3 eller E5|
|[Tilmelding af enhed](/azure/active-directory/devices/overview)|Du tilmelder en enhed til Azure AD for at oprette en identitet for enheden. Denne identitet bruges til at godkende enheden, når en bruger logger på, og til at anvende politikker for betinget adgang, der kræver domænetilsluttede eller kompatible pc'er. I denne vejledning bruger vi enhedsregistrering til automatisk at tilmelde domænetilsluttede Windows-computere. Tilmelding af enheder er en forudsætning for administration af enheder med Intune.|Microsoft 365 E3 eller E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Giver dig mulighed for at registrere potentielle sikkerhedsrisici, der påvirker din organisations identiteter, og konfigurere politikken for automatisk afhjælpning til lav, mellem og høj logonrisiko og brugerrisiko. Denne vejledning er afhængig af denne risikoevaluering for at anvende politikker for betinget adgang til multifaktorgodkendelse. Denne vejledning indeholder også en politik for betinget adgang, der kræver, at brugerne ændrer deres adgangskode, hvis der registreres højrisikoaktivitet for deres konto.|Microsoft 365 E5, Microsoft 365 E3 med tilføjelsesprogrammet E5 Security, EMS E5 eller Azure AD Premium P2-licenser|
|[Selvbetjeningstjenesten til nulstilling af adgangskode (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Tillad, at brugerne nulstiller deres adgangskoder sikkert og uden indgriben fra helpdesk ved at kontrollere flere godkendelsesmetoder, som administratoren kan kontrollere.|Microsoft 365 E3 eller E5|
|[Azure AD adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad)|Registrer og bloker kendte svage adgangskoder og deres varianter og yderligere svage ord, der er specifikke for din organisation. Standardlister over globale forbudte adgangskoder anvendes automatisk på alle brugere i en Azure AD lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugerne ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at gennemtvinge brugen af stærke adgangskoder.|Microsoft 365 E3 eller E5|

Her er komponenterne i Nul tillid identitet og enhedsadgang, herunder Intune og Azure AD objekter, indstillinger og undertjenester.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-components.png" alt-text="Komponenterne i Nul tillid identitet og enhedsadgang" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-components.png":::

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](/intune/introduction-intune) er Microsofts cloudbaserede tjeneste til administration af mobilenheder. Denne vejledning anbefaler enhedsadministration af Windows-pc'er med Intune og anbefaler konfigurationer af politikken for enhedsoverholdelse. Intune bestemmer, om enheder overholder angivne standarder, og sender disse data til Azure AD, der skal bruges, når politikker for betinget adgang anvendes.

#### <a name="intune-app-protection"></a>Intune appbeskyttelse

[Intune politikker for appbeskyttelse](/intune/app-protection-policy) kan bruges til at beskytte din organisations data i mobilapps med eller uden at tilmelde enheder til administration. Intune hjælper med at beskytte oplysninger, sikre, at dine medarbejdere stadig kan være produktive og forhindre tab af data. Når du implementerer politikker på appniveau, kan du begrænse adgangen til virksomhedens ressourcer og holde data inden for it-afdelingens kontrol.

Denne vejledning viser dig, hvordan du opretter anbefalede politikker for at gennemtvinge brugen af godkendte apps og for at bestemme, hvordan disse apps kan bruges sammen med dine forretningsdata.

### <a name="microsoft-365"></a>Microsoft 365

Denne vejledning viser dig, hvordan du implementerer et sæt politikker for at beskytte adgangen til Microsoft 365-cloudtjenester, herunder Microsoft Teams, Exchange, SharePoint og OneDrive. Ud over at implementere disse politikker anbefaler vi, at du også øger beskyttelsesniveauet for din lejer ved hjælp af disse ressourcer:

- [Konfigurer din lejer for at øge sikkerheden](tenant-wide-setup-for-increased-security.md)

  Anbefalinger, der gælder for startpunktsikkerhed for din lejer.

- [Oversigt over sikkerhed: Topprioriteter for de første 30 dage, 90 dage og derefter](security-roadmap.md)

  Anbefalinger, der omfatter logføring, datastyring, administratoradgang og trusselsbeskyttelse.

### <a name="windows-11-or-windows-10-with-microsoft-365-apps-for-enterprise"></a>Windows 11 eller Windows 10 med Microsoft 365 Apps for enterprise

Windows 11 eller Windows 10 med Microsoft 365 Apps for enterprise er det anbefalede klientmiljø til pc'er. Vi anbefaler Windows 11 eller Windows 10, fordi Azure er designet til at give den mest problemfri oplevelse i både det lokale miljø og Azure AD. Windows 11 eller Windows 10 indeholder også avancerede sikkerhedsfunktioner, der kan administreres via Intune. Microsoft 365 Apps for enterprise indeholder de nyeste versioner af Office-programmer. Disse bruger moderne godkendelse, som er mere sikker og et krav til betinget adgang. Disse apps omfatter også forbedrede værktøjer til overholdelse af angivne standarder og sikkerhed.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Anvendelse af disse funktioner på tværs af de tre beskyttelsesniveauer

I følgende tabel opsummeres vores anbefalinger til brug af disse funktioner på tværs af de tre beskyttelsesniveauer.

|Beskyttelsesmekanisme|Udgangspunkt|Enterprise|Specialiseret sikkerhed|
|---|---|---|---|
|**Gennemtving MFA**|På mellemstor eller over logonrisiko|Ved lav eller over logonrisiko|Ved alle nye sessioner|
|**Gennemtving ændring af adgangskode**|For brugere med høj risiko|For brugere med høj risiko|For brugere med høj risiko|
|**Gennemtving Intune programbeskyttelse**|Ja|Ja|Ja|
|**Gennemtving Intune tilmelding til organisationsejet enhed**|Kræv en kompatibel eller domænetilsluttet pc, men tillad BYOD-telefoner og -tablets (Bring Your Own Devices)|Kræv en kompatibel eller domænetilsluttet enhed|Kræv en kompatibel eller domænetilsluttet enhed|

## <a name="device-ownership"></a>Enhedsejerskab

Ovenstående tabel afspejler tendensen for mange organisationer til at understøtte en blanding af organisationsejede enheder samt personlige eller BYID'er for at muliggøre mobil produktivitet på tværs af arbejdsstyrken. Intune politikker for appbeskyttelse sikrer, at mail er beskyttet mod udfyldning af Outlook-mobilappen og andre Office-mobilapps på både organisationsejede enheder og BYOD'er.

Vi anbefaler, at enheder, der ejes af organisationen, administreres af Intune eller domænetilsluttede for at anvende yderligere beskyttelse og kontrol. Afhængigt af datafølsomhed kan din organisation vælge ikke at tillade BYID'er for bestemte brugerpopulationer eller bestemte apps.

## <a name="deployment-and-your-apps"></a>Installation og dine apps

Før du konfigurerer og udruller Nul tillid konfiguration af identitets- og enhedsadgang til dine Azure AD-integrerede apps, skal du:

- Beslut, hvilke apps der skal bruges i din organisation, som du vil beskytte.
- Analysér denne liste over apps for at bestemme de sæt politikker, der giver passende beskyttelsesniveauer.

  Du bør ikke oprette separate sæt politikker for hver app, da administration af dem kan blive besværlig. Microsoft anbefaler, at du grupperer dine apps, der har de samme beskyttelseskrav til de samme brugere.

  Du kan f.eks. have ét sæt politikker, der omfatter alle Microsoft 365-apps til alle dine brugere til startpunktbeskyttelse og et andet sæt politikker for alle følsomme apps, f.eks. dem, der bruges af HR- eller økonomiafdelinger, og anvende dem på disse grupper.

Når du har bestemt sættet af politikker for de apps, du vil sikre, skal du rulle politikkerne ud til dine brugere trinvist og løse problemer undervejs.

Du kan f.eks. konfigurere de politikker, der skal bruges til alle dine Microsoft 365-apps til Exchange, med de yderligere ændringer til Exchange. Udrul disse politikker til dine brugere, og gennemgå eventuelle problemer. Tilføj derefter Teams med de tilhørende yderligere ændringer, og udrul det til dine brugere. Tilføj derefter SharePoint med de tilhørende yderligere ændringer. Fortsæt med at tilføje resten af dine apps, indtil du med sikkerhed kan konfigurere disse startpunktspolitikker til at omfatte alle Microsoft 365-apps.

På samme måde kan du for dine følsomme apps oprette sættet af politikker og tilføje én app ad gangen og gennemgå eventuelle problemer, indtil de alle er inkluderet i det følsomme app-politiksæt.

Microsoft anbefaler, at du ikke opretter politiksæt, der gælder for alle apps, da det kan resultere i utilsigtede konfigurationer. Politikker, der blokerer alle apps, kan f.eks. låse dine administratorer ude af Azure Portal, og udeladelser kan ikke konfigureres for vigtige slutpunkter, f.eks. Microsoft Graph.

## <a name="steps-to-configure-zero-trust-identity-and-device-access"></a>Trin til at konfigurere Nul tillid identitet og enhedsadgang

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png" alt-text="Trinnene til konfiguration af Nul tillid identitet og enhedsadgang" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png":::

1. Konfigurer de nødvendige identitetsfunktioner og deres indstillinger.
2. Konfigurer de almindelige politikker for betinget adgang og identitet.
3. Konfigurer politikker for betinget adgang for gæstebrugere og eksterne brugere.
4. Konfigurer politikker for betinget adgang for Microsoft 365-cloudapps&mdash;, f.eks. Microsoft Teams, Exchange og SharePoint&mdash;og Microsoft Defender for Cloud Apps politikker.

Når du har konfigureret Nul tillid identitets- og enhedsadgang, skal du se [Azure AD funktionsinstallationsvejledning](/azure/active-directory/fundamentals/active-directory-deployment-checklist-p2) for at få en faseinddelt tjekliste over yderligere funktioner, der skal overvejes og [Azure AD Identitetsstyring](/azure/active-directory/governance/) for at beskytte, overvåge og overvåge adgang.

## <a name="next-step"></a>Næste trin

[Forudsætning for arbejde med implementering af Nul tillid politikker for identitets- og enhedsadgang](identity-access-prerequisites.md)
