---
title: Nyheder i Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers), der bruger Microsoft 365 Lighthouse, skal du se, hvad der er blevet tilføjet, ændret og løst i Microsoft 365 Lighthouse hver måned.
ms.openlocfilehash: 927e063abfb806e44c4888ee09d788cfa2bd7f5e
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66858913"
---
# <a name="whats-new-in-microsoft-365-lighthouse"></a>Nyheder i Microsoft 365 Lighthouse

Vi føjer løbende nye funktioner til [Microsoft 365 Lighthouse](m365-lighthouse-overview.md), løser problemer, vi får mere at vide om, og foretager ændringer på baggrund af din feedback. Gennemse denne artikel for at finde ud af, hvad vi har arbejdet på.

> [!NOTE]
> Nogle funktioner udrulles med forskellige hastigheder til vores kunder. Hvis du endnu ikke kan se en funktion, bør du snart se den.

## <a name="june-2022"></a>Juni 2022

### <a name="support-for-microsoft-365-e5-customers"></a>Understøttelse af Microsoft 365 E5 kunder

Vi har ændret vores onboardingkrav, så du kan onboarde Microsoft 365 E5 kunder til Microsoft 365 Lighthouse. Den udvidede liste over licenser, som Microsoft 365 Lighthouse understøtter til onboarding, omfatter Microsoft 365 Business Premium, Microsoft 365 E3, Microsoft 365 E5, Microsoft Defender til virksomheder og Windows 365 for Business. Kunder, der har mindst én af disse licenser, opfylder kravene til delegerede adgangstilladelser og ikke overstiger det maksimale antal brugere med licens, kan administreres i Microsoft 365 Lighthouse.  

Du kan se en komplet liste over krav under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

### <a name="microsoft-defender-for-business-integration"></a>Microsoft Defender til virksomheder integration

Microsoft 365 Lighthouse kan nu integreres med Microsoft Defender til virksomheder for at give dig relateret indsigt og administrationsfunktioner til alle dine kundelejere, der har Microsoft Defender til virksomheder. Hvis du vil se en liste over kundeenheder, der er blevet onboardet til Microsoft Defender til virksomheder, skal du vælge **Enheder** i navigationsruden til venstre i Microsoft 365 Lighthouse. Hvis du vil se en liste over hændelser og beskeder, der er markeret på tværs af dine kundelejere, skal du gå til **Enhedssikkerhed** >  og derefter vælge fanen **Hændelser og beskeder**.  

Vi har også føjet et trin til standardgrundlinjen for at hjælpe dig med at konfigurere Microsoft Defender til virksomheder til dine kundelejere. Hvis du vil se dette trin, skal du vælge **Oprindelige planer i venstre navigationsrude** i Microsoft 365 Lighthouse eller få vist udrulningsplanen for en af dine kundelejere.

### <a name="status-of-quarantined-email-messages"></a>Status for karantænemails

Vi har tilføjet ny funktionalitet omkring mail karantænedata for dine administrerede lejere. Denne funktion er tilgængelig ved at vælge **Databeskyttelse** i venstre navigationsrude i Microsoft 365 Lighthouse og giver dig indsigt i status for karantænemails på tværs af dine kundelejere. Du kan se samlede karantænemængder og detaljerede oplysninger for hver administreret lejer, så du kan prioritere alle lejere, der kræver handling.

### <a name="increase-in-maximum-license-limit"></a>Forøgelse af den maksimale licensgrænse

Vi gør det muligt at administrere flere af dine kunder i Microsoft 365 Lighthouse ved endnu en gang at øge den maksimale licensgrænse for onboarding af kunder. Kunder med op til 2500 brugerlicenser kan nu onboardes til Microsoft 365 Lighthouse. Vi fortsætter med at evaluere dette krav i fremtidige versioner af Microsoft 365 Lighthouse. 

Du kan få flere oplysninger under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="may-2022"></a>Maj 2022

### <a name="redesigned-left-navigation-pane"></a>Redesignet venstre navigationsrude

Vi har givet navigationsruden til venstre i Microsoft 365 Lighthouse et nyt udseende. Du vil bemærke et slankere design med noder på øverste niveau, f.eks. lejere, brugere og enheder, der udvides for at vise relaterede undernoder, f.eks. Risikable brugere, Enhedsoverholdelse og Trusselsadministration. Denne navigationsmodel er i overensstemmelse med den model, der bruges af andre Microsoft 365 Administrationer.

### <a name="enriched-user-details-pane"></a>Ruden Med forbedrede brugeroplysninger

Vi har redesignet ruden med brugeroplysninger, så den indeholder flere brugeroplysninger og flere handlinger, som du kan udføre for bedre at administrere brugere. Den har nu samme udseende og funktionalitet som ruden med brugeroplysninger i Microsoft 365 Administration. Hvis du vil have adgang til ruden med brugeroplysninger i Microsoft 365 Lighthouse, skal du vælge **Brugere** i navigationsruden til venstre og derefter vælge enten **Søg efter brugere** eller **Risikable brugere**. Vælg en vilkårlig bruger for at åbne detaljeruden.

## <a name="april-2022"></a>April 2022

### <a name="delegated-access-type-and-roles-on-tenants-page"></a>Delegerede adgangstype og roller på siden Lejere

Vi har opdateret siden **Lejere** for at få vist en liste over MSP-typen (Managed Service Provider) for den delegerede adgangstype (Ingen, DAP, GDAP eller Begge DAP-& GDAP) pr. kunde under kolonnen **Uddelegeret adgang** . Vi har også tilføjet en ny kolonne med titlen **Dine roller** , der viser DAP- og GDAP-rollerne pr. kunde for en bruger, der er logget på. Disse to forbedringer af siden **Lejere** gør det nemmere for partnerteknikere at forstå, hvilke typer delegerede administrative tilladelser der er tilgængelige for hver kunde, og hvilke delegerede roller der udtrykkeligt er tildelt dem.

Du kan få mere at vide under [Oversigt over tilladelser i Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

## <a name="march-2022"></a>Marts 2022

### <a name="windows-365-business-integration-and-management-actions"></a>Windows 365 Business integrations- og administrationsaktiviteter

Baseret på brugerfeedback har vi integreret Windows 365 Business i Microsoft 365 Lighthouse. Denne integration hjælper dig med at administrere og overvåge alle dine kunders Cloud-pc'er fra en enkelt placering. 

Ud over at integrere med Windows 365 Business Cloud-pc'er i Microsoft 365 Lighthouse kan du nu udføre følgende administrationshandlinger:

- Genstarte
- Klargøring igen
- Omdøbe
 
Du kan få mere at vide om de nye funktioner på [siden Oversigt over Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse](m365-lighthouse-win365-page-overview.md).

### <a name="microsoft-365-lighthouse-partner-amendment"></a>Microsoft 365 Lighthouse-partnerændring

Nu, hvor Microsoft 365 Lighthouse er offentligt tilgængeligt, kræver vi, at vores nuværende partnere signerer en opdateret ændring af Microsoft 365 Lighthouse-partner. Alle Microsoft 365 Lighthouse-partnere, der tilmeldte sig i prøveperioden, bliver bedt om at fuldføre denne nye aftale i de kommende uger. Fuldførelse kræver globale administratorrettigheder i partnerlejer og skal fuldføres inden for 90 dage for at fortsætte med at få adgang til Microsoft 365 Lighthouse-portalen.

## <a name="february-2022"></a>Februar 2022

### <a name="granular-delegated-access-permissions-gdap-roles"></a>GDAP-roller (Granular Delegated Access Permissions)

Microsoft 365 Lighthouse indeholder nu muligheden for, at MSP'er kan bruge GDAP-roller (Granular Delegated Administration Privileges). Med den seneste opdatering kan MSP'er udnytte GDAP-roller for deres teknikere, der muliggør princippet om mindst rettighedsadgang i Microsoft 365 Lighthouse. Denne funktion reducerer de risici, der er forbundet med de brede tilladelser for rollen Delegated Access Permissions (DAP) for Administration Agent ved at aktivere detaljerede kontrolelementer for kundernes data og indstillinger, som hver tekniker kan arbejde med.

Du kan få mere at vide om GDAP i Microsoft 365 Lighthouse under [Konfigurer sikkerhed i Microsoft 365 Lighthouse-portalen](m365-lighthouse-configure-portal-security.md).

### <a name="capability-to-notify-users-to-act-on-noncompliant-devices"></a>Mulighed for at give brugerne besked om at reagere på enheder, der ikke overholder deres regler

Som en del af det grundlæggende trin for enhedens overholdelse af angivne standarder har vi tilføjet muligheden for at give brugerne i en kundelejer besked om at handle på enheder, der ikke overholder angivne standarder. Med denne ændring sender den politik for enhedsoverholdelse, der er oprettet i lejeren, automatisk en meddelelse til brugerne, når deres enhed ikke overholder politikken for overholdelse af angivne standarder for en hvilken som helst kundelejer.

### <a name="deployment-validation-and-reporting"></a>Validering og rapportering af installation

Microsoft 365 Lighthouse kan nu teste lejerkonfigurationer for udrulningstrin med politikker for betinget adgang.  

Denne nye funktionalitet registrerer eksisterende politikker i de kundelejere, som du administrerer og sammenligner dem med din udrulningsplan. Microsoft 365 Lighthouse indeholder derefter statusangivelser for udrulningstrin og processer for udrulningstrin for at hjælpe dig med at forstå, hvilke udrulningsprocesser der allerede er fuldført, hvilke der skal håndteres, og hvor de indstillinger, der er foreskrevet i udrulningsplanen, er lig med, mangler eller er i konflikt med de indstillinger, der er inkluderet i de eksisterende politikker. Hvis du kender disse oplysninger, bliver det hurtigere, nemmere og mere effektivt at identificere, prioritere og løse politikkonflikter.

### <a name="deployment-step-to-configure-microsoft-defender-firewall"></a>Installationstrin til konfiguration af Microsoft Defender Firewall

Microsoft 365 Lighthouse har føjet trinnet Konfigurer Microsoft Defender Firewall udrulning til standardgrundlinjen. Dette trin hjælper MSP'er med at beskytte kundelejerenheder via standardfirewallkonfigurationen for Windows 10 (og nyere) enheder. Microsoft Defender Firewall blokerer uautoriseret netværkstrafik, der strømmer ind i eller ud af kundens lejerenheder, og reducerer risikoen for sikkerhedstrusler på netværket. Der er i øjeblikket en funktion til Microsoft Defender Firewall regler under udvikling.

Microsoft Defender Firewall er som standard slået til på Windows 10 (og nyere) enheder. Hvis din kundelejer ikke har konfigureret dette, skal du følge disse trin:

1. På siden **Lejere** i Microsoft 365 Lighthouse skal du vælge kundelejer for at åbne lejerens **oversigtsside** .
2. Vælg fanen **Udrulningsplan** .
3. Vælg **Konfigurer Microsoft Defender Firewall** på listen over installationstrin.
4. Vælg **Gennemse og udrul** for at installere denne konfiguration i kundelejer. 

### <a name="increase-in-maximum-license-limit"></a>Forøgelse af den maksimale licensgrænse

Vi gør det muligt at administrere flere af dine kunder i Microsoft 365 Lighthouse ved at øge den maksimale licensgrænse for onboarding af kunder. Kunder med op til 1000 brugerlicenser kan nu onboardes til Microsoft 365 Lighthouse. Vi fortsætter med at evaluere dette krav i fremtidige versioner af Microsoft 365 Lighthouse.

Du kan få flere oplysninger under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

### <a name="support-for-advisor-customers"></a>Support til rådgiverkunder

Vi har ændret vores onboardingkrav for at tillade, at eksisterende kundelejere med rådgiverrelationer onboardes til Microsoft 365 Lighthouse. Kunder med både forhandler- og rådgiverkontrakter er nu berettiget til at være i Microsoft 365 Lighthouse, hvis de opfylder kravene til delegerede adgangstilladelser, har de påkrævede licenser og ikke overstiger det maksimale antal brugere.

Du kan få flere oplysninger under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="january-2022"></a>Januar 2022

### <a name="capability-to-view-audit-logs-in-microsoft-365-lighthouse"></a>Mulighed for at få vist overvågningslogge i Microsoft 365 Lighthouse

Microsoft 365 Lighthouse indeholder nu muligheden for at få vist overvågningslogge. Du kan gennemse tidligere handlinger for at finde fejlkonfigurationer og risikable handlinger til afhjælpning, understøtte proces- og sikkerhedsundersøgelser, oplære medarbejdere og opfylde krav til overholdelse af angivne standarder og overvågning. Med den seneste opdatering kan du:

- Få vist overvågningslogge for at se alle handlinger, der er udført i Microsoft 365 Lighthouse, herunder hvad der er ændret i hvilken kundelejer, hvornår den blev ændret, og hvem der ændrede den.
- Søg efter og filtrer overvågningslogge for at finde bestemte oplysninger.
- Eksportér logge, så du kan analysere og bevare dem.
 
Vælg **Overvågningslogge** i venstre navigationsrude i Microsoft 365 Lighthouse. Du kan [også gå direkte til siden Overvågningslogge nu](https://lighthouse.microsoft.com/#blade/Microsoft_Intune_MTM/Audit.ReactView) for at tjekke det ud.

## <a name="november-2021"></a>November 2021

### <a name="microsoft-365-services-usage-data"></a>Brugsdata for Microsoft 365-tjenester

Du kan nu få vist forbrugsdata for Microsoft 365-tjenester fra Microsoft 365 Lighthouse. Det er vigtigt at forstå, hvordan kunderne bruger deres Microsoft 365-tjenester, for at hjælpe dem med at få mest muligt ud af deres it-investeringer. I stedet for at bruge flere ressourcer til at få vist oplysninger på tværs af dine kunders forskellige produktivitets-, sikkerheds- og overholdelsestjenester samler Microsoft 365 Lighthouse dem i én enkel og effektiv visning.  

Disse indsigter kan hjælpe med at informere dine kundeengagementer og levere mere værdi til dine kunder ved at give dig mulighed for at hjælpe dem med at forstå, hvilke tjenester deres brugere aktivt bruger, og hvor der kan være muligheder for at forbedre deres sikkerhed eller produktivitet. 

Du kan få flere oplysninger under [Oversigt over siden Lejere i Microsoft 365 Lighthouse: Microsoft 365-forbrugskort](m365-lighthouse-tenants-page-overview.md#microsoft-365-usage-card).

### <a name="exchange-online-protection-and-microsoft-365-defender-for-office-365-default-baseline-step"></a>Exchange Online Protection og Microsoft 365 Defender for Office 365 standardtrin for oprindelig plan

Vi har føjet et nyt trin til standardgrundlinjen for at inkludere en vejledning i aktivering af sikkerhedspolitikker for Exchange Online Protection (EOP) og Microsoft Defender for Office 365 (MDO). EOP og MDO hjælper med at beskytte brugerne mod spam-, phishing- og malware-mails ved at sende mails til brugerens karantænemappe eller mappe med uønsket mail (kommer snart). Udrulningsplanen hjælper dig med at konfigurere EOP og MDO og udvider din sikkerhedsposition yderligere under gennemgangen af din næste gennemgang af lejerinstallationsplanen for din kunde.

### <a name="default-tenant-tags"></a>Standardlejerkoder

Du kan nu angive visse lejerkoder som *standard* fra ruden **Administrer mærker** på siden **Lejere** , så næste gang du logger på Microsoft 365 Lighthouse, filtreres alle dine visninger og indsigter som standard, så kun de lejere, der har et standardmærke, vises. Standardtags kan hjælpe dig med at fokusere på indsigt for kundelejere med høj prioritet.

## <a name="october-2021"></a>Oktober 2021

### <a name="capability-to-filter-by-multiple-tenant-tags"></a>Mulighed for at filtrere efter flere lejertags

Det er nu muligt at filtrere data efter flere lejerkoder på samme tid. Denne funktionalitet kan hjælpe dig med nemmere at filtrere de eksisterende visninger og indsigter, der er tilgængelige i Microsoft 365 Lighthouse, for at vise relevante kundelejere.

### <a name="capability-to-assign-baseline-configurations-to-specific-azure-active-directory-groups"></a>Mulighed for at tildele grundlæggende konfigurationer til bestemte Azure Active Directory-grupper

Vi har tilføjet muligheden for at tildele grundlæggende konfigurationer til bestemte Azure Active Directory-grupper (Azure AD) for dine kundelejere fra Microsoft 365 Lighthouse. På alle sider med udrulningstrin skal du gennemse og vælge de specifikke Azure AD grupper, du vil inkludere eller udelade, og derefter udrulle konfigurationerne til din kundelejer.

### <a name="improvements-to-risky-users-page"></a>Siden Forbedringer til risikable brugere

Du kan nu nemt få vist og forstå årsagerne til en brugers risiko fra Microsoft 365 Lighthouse. I venstre navigationsrude i Microsoft 365 Lighthouse skal du vælge **Brugere** og derefter vælge fanen **Risikable brugere** . Vælg **Vis risikoregistreringer** i kolonnen **Detaljer** for alle brugere. Herfra kan du gennemse oplysningerne om risikoen og derefter vælge **Bekræft bruger kompromitteret** eller **Afvis brugerrisiko**. Du kan også bekræfte eller afvise en risiko for flere brugere på samme tid fra siden **Risikable brugere** . Muligheden for at afvise en brugers risiko kan være nyttig, når nulstilling af adgangskode ikke er en mulighed, eller hvis du mener, at den pågældende bruger ikke længere er i fare.

### <a name="capability-to-provide-feedback-on-microsoft-365-lighthouse"></a>Mulighed for at give feedback på Microsoft 365 Lighthouse

Din feedback er vigtig og vigtig for os, så vi har tilføjet ny feedbackfunktionalitet, der indimellem (ikke mere end én gang om måneden) beder dig om at give feedback. Du kan også give feedback når som helst ved at vælge feedbackikonet i øverste højre hjørne af Microsoft 365 Lighthouse.

## <a name="september-2021"></a>September 2021

### <a name="tenant-filter-changes"></a>Ændringer af lejerfilter

Vi har foretaget nogle ændringer af lejerfiltreringsoplevelsen for hurtigt at få vist og administrere lejere og mærker fra en hvilken som helst side i Microsoft 365 Lighthouse. Vælg **filteret Lejere** øverst på en side, og gennemse eller angiv derefter det lejer- eller mærkenavn, du vil filtrere efter.

## <a name="august-2021"></a>August 2021

### <a name="in-product-email-workflows-to-communicate-with-users"></a>Mailarbejdsprocesser i produktet for at kommunikere med brugere 

Vi har gjort det nemmere at kommunikere med brugerne i dine kundelejere om de handlinger, de skal udføre. På listen over brugere, der ikke er registreret til multifaktorgodkendelse eller selvbetjent nulstilling af adgangskode, kan du nu vælge en eller flere brugere og sende dem en mail ved hjælp af en mailskabelon, der kan downloades.

### <a name="capability-to-take-action-on-noncompliant-devices"></a>Mulighed for at udføre handlinger på enheder, der ikke overholder overensstemmelsen

Vi har introduceret muligheden for at synkronisere eller genstarte en eller flere enheder på tværs af flere kundelejere. Denne funktionalitet hjælper med at sikre, at dine kunders enheder er beskyttet mod risici. Hvis du vil se denne funktionalitet, skal du vælge **Enheder** i venstre navigationsrude i Microsoft 365 Lighthouse og derefter vælge fanen **Enheder** . Se efter indstillingerne **Synkroniser** og **Genstart** over listen over enheder. Du kan også få adgang til disse indstillinger fra ruden med enhedsoplysninger på en hvilken som helst enhed.

### <a name="capability-to-monitor-and-manage-windows-365-cloud-pcs"></a>Mulighed for at overvåge og administrere Windows 365 Cloud-pc'er

Vi har tilføjet muligheden for at overvåge forbindelser i det lokale miljø og klargøre og administrere Windows 365 Cloud-pc'er på tværs af alle dine kundelejere. Den nye **Windows 365** side indeholder detaljerede oplysninger om alle dine lejers Cloud-pc'er på én praktisk placering. 

### <a name="support-for-microsoft-365-e3-customers"></a>Understøttelse af Microsoft 365 E3 kunder

Vi har ændret vores onboardingkrav, så du kan onboarde Microsoft 365 E3 kunder til Microsoft 365 Lighthouse. For at kvalificere sig til at blive administreret i Microsoft 365 Lighthouse skal hver kunde opfylde følgende krav:

- Der skal være konfigureret uddelegeret adgang, for at MSP'en kan administrere kundelejer
- Der skal være mindst én Microsoft 365 Business Premium- eller Microsoft 365 E3 licens
- Der må ikke være mere end 500 brugere med licens

Du kan få flere oplysninger om krav under [Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="june-2021"></a>Juni 2021

### <a name="capability-to-add-custom-tags-to-customer-tenants"></a>Mulighed for at føje brugerdefinerede mærker til kundelejere

Du kan nu oprette og anvende brugerdefinerede mærker på de kundelejere, du administrerer i Microsoft 365 Lighthouse. Brug disse mærker til at hjælpe dig med at organisere dine lejere, eller brug dem til nemmere at filtrere din lejerliste for at få vist indsigt for relevante sæt kundelejere. 

### <a name="baselines-to-standardize-your-customer-tenant-deployments"></a>Grundlinjer til standardisering af udrulninger af din kundelejer

Med den nye funktion grundlinjer kan du nu udrulle standardkonfigurationer for at hjælpe med at sikre brugere, enheder og data i kundelejere. Standardgrundlinjen indeholder i øjeblikket følgende installationstrin (der kommer snart flere): 

- Kræv MFA for administratorer 
- Kræv MFA for brugere 
- Bloker ældre godkendelse 
- Tilmeld Windows-enheder i Microsoft Endpoint Manager – Azure AD Deltag 
- Konfigurer Defender AV-politik for Windows-enheder 
- Konfigurer politik for overholdelse af regler og standarder for Windows-enheder 

Hvis du vil reagere på disse udrulningstrin, skal du vælge **Lejere i venstre navigationsrude** i Microsoft 365-fyrtårnet, vælge en lejer på listen over lejere og derefter vælge fanen **Udrulningsplan** . 

## <a name="may-2021"></a>Maj 2021

### <a name="enhancements-to-tenants-page"></a>Forbedringer til siden Lejere

Vi har foretaget følgende forbedringer af siden **Lejere** :

- Der er føjet en liste over det samlede antal efter problem øverst på siden 
- Har angivet muligheden for at holde markøren over en status i kolonnen **Status** på lejerlisten for at få vist oplysninger om begrænsning 
- Forbedret statusmærkater