---
title: Konfigurationer af nultillidsidentitet og enhedsadgang – Microsoft 365 til virksomheder
description: Beskriver Microsoft-anbefalinger og kernekoncepter til implementering af politikker for sikker mail, dokumenter og apps samt konfigurationer for Zero Trust.
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
ms.technology: mdo
ms.openlocfilehash: 7e8fbeab380ceac3531e2a288fb5e8fb5f43e166
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682367"
---
# <a name="zero-trust-identity-and-device-access-configurations"></a>Konfigurationer for nultillidsidentitet og enhedsadgang

Sikkerhedsarkitekturer, der er afhængige af netværksfirewalls og virtuelle private netværk til at isolere og begrænse adgangen til en organisations teknologiressourcer og -tjenester, er ikke længere tilstrækkelige til en arbejdsstyrke, der jævnligt kræver adgang til programmer og ressourcer, som ligger ud over de traditionelle virksomhedsnetværksgrænser.

Hvis du vil tage hånd om denne nye verden af databehandling, anbefaler Microsoft på det kraftigste nultillidssikkerhedsmodellen, der er baseret på disse ledende principper:

- Bekræfte udtrykkeligt

  Godkend og godkend altid baseret på alle tilgængelige datapunkter. Det er her, zero trust-identitet og politikker for enhedsadgang er afgørende for logon og løbende validering.

- Brug adgang med mindst rettigheder

  Begræns brugeradgang med Just-In-Time og Just-Enough-Access (JIT/JEA), risikobaserede adaptive politikker og databeskyttelse.  

- Antag misligholdelse

  Minimer mængden af radius og segmentadgang. Bekræft kryptering fra ende til anden, og brug analyse til at få synlighed, køre trusselsregistrering og forbedre forsvar.

Her er den overordnede arkitektur for Zero Trust.

:::image type="content" source="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png" alt-text="Arkitekturen Microsoft Zero Trust" lightbox="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png":::

Politikkerne Nultillidshed og enhedsadgang adresserer **Det ledende** princip for Bekræft eksplicit for:

- Identiteter

  Når en identitet forsøger at få adgang til en ressource, skal du bekræfte denne identitet med stærk godkendelse og sikre, at den anmodede adgang er kompatibel og typisk.

- Enheder (også kaldet slutpunkter)

  Overvåg og gennemtving krav til enhedens tilstand og overholdelse af regler og standarder for sikker adgang.

- Programmer

  Anvend kontrolelementer og teknologier for at opdage skygge-it, sikre relevante apptilladelser, adgangskontrol, der er baseret på analyser i realtid, overvåge for unormal adfærd, kontrollere brugerhandlinger og validere sikre konfigurationsindstillinger.

I denne serie af artikler beskrives et sæt konfigurationer, der er nødvendige for identitet og enhedsadgang, og et sæt betinget adgang (Azure AD) Azure Active Directory, Microsoft Intune og andre politikker for adgang uden tillid til Microsoft 365  til virksomhedsskyapps og -tjenester, andre SaaS-tjenester og programmer i det lokale miljø, der er udgivet med Azure AD-programproxy.

Indstillinger for nultillids-identitet og enhedsadgang samt politikker anbefales på tre niveauer: startpunkt, virksomhed og særlig sikkerhed for miljøer med stærkt regulerede eller klassificerede data. Disse niveauer og deres tilsvarende konfigurationer giver ensartede niveauer af nultillidsbeskyttelse på tværs af dine data, identiteter og enheder.

Disse funktioner og deres anbefalinger:

- Understøttes i Microsoft 365 E3 og Microsoft 365 E5.
- Er justeret [med Microsoft Secure Score](../defender/microsoft-secure-score.md) samt [identitetsscore i Azure AD](/azure/active-directory/fundamentals/identity-secure-score), og vil øge disse pointtal for organisationen.
- Hjælper dig med at implementere disse [fem trin til sikring af din identitetsinfrastruktur](/azure/security/azure-ad-secure-steps).

Hvis din organisation har unikke miljøkrav eller kompleksiteter, kan du bruge disse anbefalinger som udgangspunkt. De fleste organisationer kan dog implementere disse anbefalinger, som angivet.

Watch this video for a quick overview of identity and device access configurations for Microsoft 365 for enterprise.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxEDQ]

> [!NOTE]
> Microsoft sælger også Enterprise Mobility + Security (EMS) til Office 365-abonnementer. EMS E3- og EMS E5-egenskaber svarer til dem i Microsoft 365 E3 og Microsoft 365 E5. Se [EMS-planer](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/compare-plans-and-pricing) for at få flere oplysninger.

## <a name="intended-audience"></a>Beregnet publikum

Disse anbefalinger er beregnet til virksomhedsarkitekter og it-fagfolk, der er fortrolige med Microsoft 365-produktivitet og -sikkerhedstjenester i skyen, som omfatter Azure AD (identitet), Microsoft Intune (enhedshåndtering) og Microsoft Information Protection (databeskyttelse).

### <a name="customer-environment"></a>Kundemiljø

De anbefalede politikker er gældende for virksomhedsorganisationer, der udelukkende arbejder i Microsoft-skyen og for kunder med hybrididentitetsinfrastruktur, som er et lokalt Active Directory-domæneservices (AD DS)-område, der er synkroniseret med en Azure AD-lejer.

Mange af de medfølgende anbefalinger afhænger af tjenester, der kun er tilgængelige med Microsoft 365 E5, Microsoft 365 E3 med E5 Security-tilføjelsesprogrammet, EMS E5 eller Azure AD Premium P2-licenser.

For de organisationer, der ikke har disse licenser, anbefaler Microsoft, at du som minimum implementerer [sikkerhedsstandardindstillinger,](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) som følger med alle Microsoft 365-planer.

### <a name="caveats"></a>Advarselsbotter

Din organisation kan være underlagt lovkrav eller andre krav til overholdelse af regler og standarder, herunder specifikke anbefalinger, der kan kræve, at du anvender politikker, der afviger fra disse anbefalede konfigurationer. Disse konfigurationer anbefaler brugskontrolelementer, der ikke historisk har været tilgængelige. Vi anbefaler disse kontrolelementer, fordi vi mener, at de repræsenterer en balance mellem sikkerhed og produktivitet.

Vi har gjort vores bedste for at tage højde for en lang række krav til virksomhedsbeskyttelse, men vi kan ikke tage højde for alle de mulige krav eller for alle de unikke aspekter af din organisation.

## <a name="three-tiers-of-protection"></a>Tre niveauer af beskyttelse

De fleste organisationer har specifikke krav vedrørende sikkerhed og databeskyttelse. Disse krav varierer alt efter branchesegment og jobfunktioner inden for organisationer. Eksempelvis kan din juridiske afdeling og administratorer kræve yderligere kontrol af sikkerhed og informationsbeskyttelse omkring deres mailkorrespondance, som ikke er påkrævet for andre forretningsenheder.

Hver branche har også sit eget sæt specialiserede bestemmelser. I stedet for at oprette en liste over alle mulige sikkerhedsindstillinger eller en anbefaling pr. branche eller jobfunktion har vi leveret anbefalinger til tre forskellige niveauer af sikkerhed og beskyttelse, der kan anvendes baseret på granulariteten af dine behov.

- **Udgangspunkt**: Vi anbefaler, at alle kunder etablerer og bruger en minimumstandard til beskyttelse af data samt identiteter og enheder, der får adgang til dine data. Du kan følge disse anbefalinger for at give stærk standardbeskyttelse som et udgangspunkt for alle organisationer.
- **Virksomhed**: Nogle kunder har et undersæt af data, der skal være beskyttet på højere niveauer, eller de kan kræve, at alle data skal beskyttes på et højere niveau. Du kan anvende øget beskyttelse på alle eller bestemte datasæt i dit Microsoft 365 miljø. Vi anbefaler at beskytte identiteter og enheder, der får adgang til følsomme data med tilsvarende sikkerhedsniveauer.
- **Særlig sikkerhed**: Nogle få kunder har efter behov en lille mængde data, der er meget klassificeret, udgør forretninghemmeligheder eller er regulerede. Microsoft leverer funktioner, der kan hjælpe disse kunder med at opfylde disse krav, herunder ekstra beskyttelse af identiteter og enheder.

![Sikkerheds kegle – Alle kunder > Nogle kunder > Nogle få kunder](../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png)

Denne vejledning viser, hvordan du implementerer Zero Trust-beskyttelse for identiteter og enheder for hvert af disse niveauer af beskyttelse. Brug denne vejledning som minimum for din organisation, og juster politikkerne, så de opfylder din organisations specifikke krav.

Det er vigtigt at bruge ensartede niveauer af beskyttelse på tværs af dine identiteter, enheder og data. Beskyttelse af brugere med prioritetskonti, f.eks. ledere,&mdash; ledere og andre, omfatter f.eks. det samme beskyttelsesniveau for&mdash; deres identiteter, deres enheder og de data, de får adgang til. 
<!--

The **Zero Trust identity and device protection for Microsoft 365** architecture model shows you which capabilities are comparable.

[![Thumb image for Zero Trust Identity and device protection for Microsoft 365 poster.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-thumbnail.png)](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) <br> [View as a PDF](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.pdf)  \| [Download as a Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.vsdx)

--> 

Se desuden løsning til implementering af [beskyttelse af oplysninger for regler for beskyttelse](../../solutions/information-protection-deploy.md) af data for at beskytte oplysninger, der er gemt Microsoft 365.

## <a name="security-and-productivity-trade-offs"></a>Afrivninger af sikkerhed og produktivitet

Implementering af enhver sikkerhedsstrategi kræver afrivning mellem sikkerhed og produktivitet. Det er nyttigt at evaluere, hvordan hver beslutning påvirker balancen i sikkerhed, funktionalitet og brugervenlighed.

![Sikkerheds- og balancering af sikkerhed, funktionalitet og brugervenlighed.](../../media/microsoft-365-policies-configurations/security-triad.png)

De angivne anbefalinger er baseret på følgende principper:

- Kende dine brugere og være fleksible i forhold til deres sikkerheds- og funktionskrav.
- Anvend en sikkerhedspolitik lige i tide, og sørg for, at den giver mening.

## <a name="services-and-concepts-for-zero-trust-identity-and-device-access-protection"></a>Tjenester og koncepter for nultillidsidentitet og beskyttelse af enhedsadgang

Microsoft 365 til virksomheder er udviklet til store organisationer for at give alle mulighed for at være kreative og samarbejde sikkert.

Dette afsnit indeholder en oversigt over de Microsoft 365 og egenskaber, der er vigtige for nultillids-identitet og enhedsadgang.

### <a name="azure-ad"></a>Azure AD

Azure AD indeholder en komplet pakke med funktioner til identitetsadministration. Vi anbefaler, at du bruger disse funktioner til at sikre adgang.

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|[MFA (Multi-Factor Authentication)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA kræver, at brugerne angiver to former for bekræftelse, f.eks. en brugeradgangskode plus en meddelelse fra Microsoft Authenticator-appen eller et telefonopkald. MFA reducerer kraftigt risikoen for, at stjålet legitimationsoplysninger kan bruges til at få adgang til dit miljø. Microsoft 365 bruger Azure AD Multi-Factor Authentication-tjenesten til MFA-baserede logons.|Microsoft 365 E3 eller E5|
|[Betinget adgang](/azure/active-directory/conditional-access/overview)|Azure AD evaluerer betingelserne for brugerens logon og bruger politikker for betinget adgang til at bestemme den tilladte adgang. I denne vejledning viser vi dig f.eks., hvordan du opretter en Betinget adgang-politik for at kræve enhedsoverholdelse for at få adgang til følsomme data. Dette reducerer risikoen for, at en hacker med sin egen enhed og stjålne legitimationsoplysninger kan få adgang til dine følsomme data. Den beskytter også følsomme data på enhederne, fordi enhederne skal opfylde specifikke krav til tilstand og sikkerhed.|Microsoft 365 E3 eller E5|
|[Azure AD-grupper](/azure/active-directory/fundamentals/active-directory-manage-groups)|Politikker for betinget adgang, enhedshåndtering med Intune og endda tilladelser til filer og websteder i organisationen afhænger af tildeling til brugerkonti eller Azure AD-grupper. Vi anbefaler, at du opretter Azure AD-grupper, der svarer til de niveauer af beskyttelse, du implementerer. Eksempelvis er dine ledere sandsynligvis bedre mål for hackere. Derfor giver det mening at føje brugerkontiene for disse medarbejdere til en Azure AD-gruppe og tildele denne gruppe til politikker for betinget adgang og andre politikker, der gennemtvinger et højere niveau af beskyttelse af adgang.|Microsoft 365 E3 eller E5|
|[Tilmelding af enhed](/azure/active-directory/devices/overview)|Du tilmelder en enhed til Azure AD for at oprette en identitet for enheden. Denne identitet bruges til at godkende enheden, når en bruger logger på, og til at anvende politikker for betinget adgang, der kræver domænefortegnende eller kompatible pc'er. Til denne vejledning bruger vi enhedsregistrering til automatisk at tilmelde domænet sammen med Windows computere. Tilmelding af enheder er en forudsætning for administration af enheder med Intune.|Microsoft 365 E3 eller E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Gør det muligt at registrere potentielle sårbarheder, der påvirker organisationens identiteter, og konfigurere automatiseret afhjælpningspolitik til lav, mellem og høj logon-risiko og brugerrisici. Denne vejledning afhænger af denne risikoevaluering for at anvende betingede Access-politikker til multifaktorgodkendelse. Denne vejledning indeholder også en politik for betinget adgang, der kræver, at brugerne ændrer deres adgangskode, hvis der registreres aktivitet med høj risiko for deres konto.|Microsoft 365 E5, Microsoft 365 E3 med E5 Security-tilføjelsesprogrammet, EMS E5 eller Azure AD Premium P2-licenser|
|[Selvbetjeningstjenesten til nulstilling af adgangskode (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Giv dine brugere mulighed for at nulstille deres adgangskoder sikkert og uden helpdesk-handling ved at levere bekræftelse af flere godkendelsesmetoder, som administratoren kan styre.|Microsoft 365 E3 eller E5|
|[Azure AD-adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad)|Find og bloker kendte svage adgangskoder og deres varianter og yderligere svage ord, der er specifikke for din organisation. Standard globale lister over forbudte adgangskoder anvendes automatisk for alle brugere i en Azure AD-lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugere ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at håndhæve brugen af stærke adgangskoder.|Microsoft 365 E3 eller E5|

Her er komponenterne for Zero Trust-identitet og enhedsadgang, herunder Intune- og Azure AD-objekter, indstillinger og undertjenester.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-components.png" alt-text="Komponenter af nultillidsidentitet og enhedsadgang." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-components.png":::

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](/intune/introduction-intune) er Microsofts skybaserede administrationstjeneste til mobilenheder. Denne vejledning anbefaler enhedshåndtering af Windows pc'er med Intune og anbefaler konfigurationer af politikker for enhedsoverholdelse. Intune afgør, om enhederne er kompatible og sender disse data til Azure AD til brug, når du anvender politikker for betinget adgang.

#### <a name="intune-app-protection"></a>Intune-appbeskyttelse

[Intune-politikker](/intune/app-protection-policy) for appbeskyttelse kan bruges til at beskytte din organisations data i mobilapps med eller uden at tilmelde enheder til administration. Intune hjælper med at beskytte oplysninger, sikre, at dine medarbejdere stadig kan være produktive, og forhindrer tab af data. Ved at implementere politikker på appniveau kan du begrænse adgangen til virksomhedens ressourcer og holde data inden for it-afdelingens kontrol.

Denne vejledning viser, hvordan du opretter anbefalede politikker til at håndhæve brugen af godkendte apps og til at bestemme, hvordan disse apps kan bruges sammen med dine virksomhedsdata.

### <a name="microsoft-365"></a>Microsoft 365

Denne vejledning viser, hvordan du implementerer et sæt politikker for at beskytte adgangen til Microsoft 365-skytjenester, herunder Microsoft Teams, Exchange, SharePoint og OneDrive. Ud over at implementere disse politikker anbefaler vi, at du også øger beskyttelsesniveauet for din lejer ved hjælp af disse ressourcer:

- [Konfigurer din lejer for øget sikkerhed](tenant-wide-setup-for-increased-security.md)

  Anbefalinger, der gælder for startpunktsikkerhed for din lejer.

- [Sikkerhedsoversigt: Topprioriteter for de første 30 dage, 90 dage og derefter](security-roadmap.md)

  Anbefalinger, der omfatter logføring, datastyring, administratoradgang og trusselsbeskyttelse.

### <a name="windows-11-or-windows-10-with-microsoft-365-apps-for-enterprise"></a>Windows 11 eller Windows 10 med Microsoft 365 Apps for enterprise

Windows 11 eller Windows 10 med Microsoft 365 Apps for enterprise er det anbefalede klientmiljø til pc'er. Vi anbefaler Windows 11 eller Windows 10, da Azure er designet til at give den bedst mulige oplevelse for både det lokale miljø og Azure AD. Windows 11 eller Windows 10 indeholder også avancerede sikkerhedsfunktioner, der kan administreres via Intune. Microsoft 365 Apps for enterprise indeholder de nyeste versioner af Office programmer. Disse bruger moderne godkendelse, hvilket er mere sikkert og et krav til Betinget adgang. Disse apps indeholder også udvidede værktøjer til overholdelse af regler og standarder og sikkerhed.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Anvendelse af disse funktioner på tværs af de tre niveauer af beskyttelse

Den følgende tabel opsummerer vores anbefalinger til brug af disse funktioner på tværs af de tre niveauer af beskyttelse.

|Beskyttelsesmekanisme|Udgangspunkt|Enterprise|Speciel sikkerhed|
|---|---|---|---|
|**Gennemtving MFA**|På mellemstor eller over login-risiko|Ved lav eller over logonrisici|På alle nye sessioner|
|**Gennemtving ændring af adgangskode**|For brugere med høj risiko|For brugere med høj risiko|For brugere med høj risiko|
|**Gennemtving Intune-programbeskyttelse**|Ja|Ja|Ja|
|**Gennemtving Intune-registrering for organisationejede enheder**|Kræve en kompatibel eller domæne-forbundet pc, men tillade BYOD-telefoner og -tablets (bring-your-own devices)|Kræve en kompatibel eller domæneforenet enhed|Kræve en kompatibel eller domæneforenet enhed|

## <a name="device-ownership"></a>Ejerskab af enhed

Ovenstående tabel afspejler tendensen for mange organisationer til at understøtte en blanding af enheder, der ejes af organisationen, samt personlige eller BYOD'er for at aktivere mobilproduktivitet på tværs af medarbejderne. Intune-politikker for appbeskyttelse sikrer, at mail er beskyttet mod at blive eksfiltreret fra Outlook-mobilappen og andre Office-mobilapps – både på organisationsejede enheder og BYOD'er.

Vi anbefaler, at enheder, der ejes af organisationen, administreres af Intune eller er domænet sammenføjet for at anvende yderligere beskyttelse og kontrol. Afhængigt af datafølsomhed kan din organisation vælge ikke at tillade BYOD'er for bestemte brugergrupper eller bestemte apps.

## <a name="deployment-and-your-apps"></a>Installation og dine apps

Før du konfigurerer og udruller konfigurationen af Zero Trust-identitet og enhedsadgang til dine Azure AD-integrerede apps, skal du:

- Beslut, hvilke apps der bruges i din organisation, du vil beskytte.
- Analysér denne liste over apps for at bestemme de sæt af politikker, der giver passende beskyttelsesniveauer.

  Du bør ikke oprette separate sæt af politikker hver for app, da det kan blive besværligt at holde administrationen af dem. Microsoft anbefaler, at du grupperer dine apps, der har de samme beskyttelseskrav til de samme brugere.

  Du kan f.eks. have ét sæt politikker, der indeholder alle Microsoft 365-apps til alle dine brugere til beskyttelse af udgangspunktet og et andet sæt politikker for alle følsomme apps, f.eks. dem, der bruges af HR eller økonomiafdelinger, og anvende dem på disse grupper.

Når du har fastlagt sættet af politikker for de apps, du vil sikre, skal du rulle politikkerne gradvist ud til dine brugere og tage hånd om problemer undervejs.

Du kan f.eks. konfigurere de politikker, der skal bruges til alle dine Microsoft 365-apps til Exchange sammen med de yderligere ændringer for Exchange. Rul disse politikker ud til dine brugere, og arbejd dig igennem eventuelle problemer. Tilføj derefter en Teams dens yderligere ændringer, og udrul den til dine brugere. Tilføj derefter SharePoint dens yderligere ændringer. Fortsæt med at tilføje resten af dine apps, indtil du kan konfigurere disse startpolitikker sikkert til at omfatte alle Microsoft 365 apps.

På samme måde kan du for dine følsomme apps oprette sættet af politikker og tilføje én app ad gangen og løse eventuelle problemer, indtil de alle er inkluderet i politiksættet for følsomme apps.

Microsoft anbefaler, at du ikke opretter politiksæt, der gælder for alle apps, fordi det kan medføre utilsigtede konfigurationer. Politikker, der blokerer alle apps, kan f.eks. låse dine administratorer ude af Azure-portalen, og udeladelse kan ikke konfigureres til vigtige slutpunkter som f.eks. Microsoft Graph.

## <a name="steps-to-configure-zero-trust-identity-and-device-access"></a>Trin til konfiguration af nultillidsidentitet og enhedsadgang

![Trin til at konfigurere nultillidsidentitet og enhedsadgang.](../../media/microsoft-365-policies-configurations/identity-device-access-steps.png)

1. Konfigurere nødvendige identitetsfunktioner og deres indstillinger.
2. Konfigurer de fælles identitets- og adgangspolitikker for Betinget adgang.
3. Konfigurer Betingede adgangspolitikker for gæster og eksterne brugere.
4. Konfigurer betingede Access-politikker for Microsoft 365 apps&mdash;, f.eks. Microsoft Teams, Exchange og SharePoint&mdash; og politikker for Microsoft Defender til skyapps.

Når du har konfigureret nultillidsidentitet og enhedsadgang, skal du se [Installationsvejledningen til Azure AD-funktioner](/azure/active-directory/fundamentals/active-directory-deployment-checklist-p2) for at få en trinvis tjekliste over yderligere funktioner, du skal overveje, og [Azure AD-identitetsstyring](/azure/active-directory/governance/) for at beskytte, overvåge og overvåge adgang.

## <a name="next-step"></a>Næste trin

[Påkrævet arbejde til implementering af nultillidsidentitet og politikker for enhedsadgang](identity-access-prerequisites.md)
