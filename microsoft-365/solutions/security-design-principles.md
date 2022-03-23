---
title: Microsoft 365 Enterprise ressourceplanlægning – arkitektur for cybersikkerhed
description: Få mere at vide om, hvordan du kan overkomme sikkerhedsudfordringer i Microsoft Enterprise-arkitektur fra Kozeta Garrett, Cybersecurity Architect hos Microsoft.
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
ms.openlocfilehash: c580b6529a3467a08befdb07c1b0b8d516208183
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63590882"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>Sikkerhedstrusler, som du kan sejle over – én arkitekts kant

I denne artikel beskriver [Kozeta Garrett](https://www.linkedin.com/in/kozeta-garrett-53013a6/), Cybersecurity Architect hos Microsoft, de største sikkerhedsudfordringer, hun støder på i virksomhedsorganisationer, og anbefaler metoder til at håndtere disse udfordringer.

## <a name="about-the-author"></a>Om forfatteren

![Kozeta Garrett-billede.](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

I min rolle som Cloud Security Architect har jeg arbejdet sammen med flere organisationer for at yde strategisk og teknisk vejledning, hvor jeg fokuserer på design og implementering af sikkerhedsarkitektur til kunder, der overfører til Microsoft 365 og Azure, udvikler virksomhedssikkerhedsløsninger og hjælper med at transformere sikkerhedsarkitektur og kultur for virksomhedsrobusthed. Min oplevelse omfatter registrering af hændelser og svar, malwareanalyse, test af test af malware og anbefaling af forbedringer af it-sikkerhed og forsvarsmæssige indlæg. Jeg går meget op i at lede transformationer, der resulterer i sikkerhed som en aktiveringsaktivering for virksomheden, herunder bestræbelser på at modernisere.

Det har været til stor glæde at se, hvordan organisationer, der har indført en sikkerheds moderniseringstanke i løbet af de sidste par år, har en god position, der giver dem mulighed for at fortsætte med at fungere eksternt på en sikker måde på trods af den nylige COVID-19-situation. Disse forhold har desværre også fungeret som et wake-up-opkald for nogle kunder, som ikke var klar til dette øjeblikkelige behov. Mange organisationer indser, at de er nødt til at modernisere hurtigt, lade deres akkumulerede it-sikkerhedsgæld udgå og forbedre deres sikkerhedsstilling natten over, så de kan fungere under disse yderst usædvanlige omstændigheder.

Den gode nyhed er, at Microsoft har konfigureret nogle gode ressourcer, der kan hjælpe organisationer med hurtigt at øge deres sikkerhedsudseindelse. Ud over disse ressourcer vil jeg gerne dele de største udfordringer, jeg har oplevet med kunder dagligt, i forventningerne om, at du kan sejle over disse forhindringer.

Jeg bor i øjeblikket i Northern Virginia, tæt på vores lands hovedstad, Washington DC. Jeg elsker stort set alle former for udendørs aktiviteter og træning, som løber, cykler, vandre og svømme. For at imødegå disse kan jeg nyde lige så meget mad, gourmet mad og rejser.

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>Partner med sikkerhedsteamet fra starten af indføringen i skyen

Til at begynde med kan jeg ikke fremhæve nok, hvor vigtigt det er for teams i organisationen at koordinere fra begyndelsen. Sikkerhedsteams skal anvendes som kritiske partnere i de tidlige faser af skybaseret indføring og design. Det betyder, at du får sikkerhedsteams i gang med skyindføring, ikke kun for de ekstra funktioner til virksomheden (f.eks. en god brugeroplevelse fra sikre mobilenheder, programmer med fuld funktionalitet eller ved at skabe værdi for virksomhedens data ud over de begrænsede mail- og produktivitetsprogrammer med begrænset funktionalitet), men også for at udnytte lagrings-, AI- og computing-analysefunktioner, der kan hjælpe med at løse nye og gamle sikkerhedsudfordringer. Sikkerhedsteams skal medtages i administrationen af alle aspekter af denne vagt, herunder personer (kultur), processer (uddannelse) og teknologi for at blive en succes. Det betyder også, at du skal investere i moderne og løbende forbedring af Security Operations Center (SOC). Arbejd sammen om at justere din sikkerhedsstrategi med virksomhedens strategi og miljøtendenser for at sikre, at den digitale transformation udføres sikkert. Når det går godt, udvikler organisationer muligheden for at tilpasse hurtigere til ændringer, herunder ændringer af virksomheden, it og sikkerhed.

Der, hvor jeg kan se kunderne rejse mest, er, når der ikke er noget rigtigt partnerskab mellem operationerne og SOC-teams. Mens driftsteamet bliver trykket og indad med smalle deadlines for at indføre skyen, inkluderes sikkerhedsteamene ikke altid tidligt i processen for at revidere og planlægge en omfattende sikkerhedsstrategi. Dette indebærer integrering af forskellige komponenter i skyen og komponenter i det direkte miljø. Denne manglende partnerskab kan føre videre til forskellige teams, der synes at arbejde i siloer for at implementere kontrolelementer til deres specifikke komponenter, hvilket fører til den ekstra kompleksitet ved implementering, fejlfinding og integration.

Kunder, der sejles over disse forhindringer, har gode forbindelser mellem Operations and Governance og Sikkerheds- og risikostyringsteamene for at ændre sikkerhedsstrategi og krav til beskyttelse af hybride skybelastninger. De fokuserer med laser på de ultimative sikkerhedsmål og -resultater – databeskyttelse og tilgængeligheden af data og tjenester i overensstemmelse med krav til styring af cybersikkerhed, risiko og overholdelse af regler og standarder. Disse organisationer udvikler tidlige partnerskabsforhold mellem deres Operations and Governance-team og SOC, som er afgørende for tilgangen til sikkerhedsdesign og maksimerer værdien af deres investeringer.

## <a name="build-a-modern-identity-based-security-perimeter"></a>Opbyg en moderne (identitetsbaseret) sikkerhedsperimeter

Dernæst skal du indføre en nultillidsarkitektur-tilgang. Dette starter med at opbygge en moderne, identitetsbaseret sikkerhedsperimeter. Design sikkerhedsarkitekturen, hvor hvert forsøg på adgang, hvad enten det er i det offentlige eller i skyen, behandles som upålidelig, indtil det er bekræftet – "hav aldrig tillid til, bekræft altid". Denne design tilgang øger ikke kun sikkerhed og produktivitet, men giver også brugerne mulighed for at arbejde hvor som helst med en hvilken som helst enhedstype. De avancerede skykontrolelementer, der følger Microsoft 365, hjælper dig med at beskytte brugernes identiteter, mens du styrer adgangen til værdifulde ressourcer, der er baseret på brugerens risikoniveau.

Du kan finde en anbefalet konfiguration under [Konfigurationer for identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="transition-security-controls-to-the-cloud"></a>Overgangssikkerhedskontrolelementer til skyen

Mange sikkerhedsteams bruger stadig de traditionelle bedste fremgangsmåder for sikkerhed, der er bygget til en alle lokale verden, herunder vedligeholdelse af en "netværksperimetersikkerhed" og forsøg på at "gennemtvinge" sikkerhedsværktøjerne og kontrolelementerne i det lokale miljø til skyløsninger. Disse kontrolelementer er ikke designet til skyen, er effektive og forhindrer føring af moderne skyfunktioner. Processer og værktøjer, der fungerer i forbindelse med en tilgang til netværksperimetersikkerhed, har vist sig at være ineffektiv, blokerende for skyfunktioner og tillader ikke at drage fordel af moderne og automatiserede sikkerhedsfunktioner.

Du kan sejle over denne hurdle ved at skifte forsvarsstrategier til sky-administreret beskyttelse, automatiseret undersøgelse og afhjælpning, automatiseret pennetest, Defender til Office 365 og hændelsesanalyse. Kunder, der bruger moderne enhedshåndteringsløsninger, har implementeret automatiseret administration, standardiseret programrettelse, antivirus, håndhævelse af politikker og programbeskyttelse på tværs af alle enheder (en smartphone, en personlig computer, bærbar computer eller tablet). Dette fjerner behovet for et VPN, Microsoft System Center Configuration Manager (SCCM) og Active Directory-gruppepolitikker. Dette giver kombineret med politikker for betinget adgang effektiv kontrol og synlighed samt strømlinet adgang til ressourcer, uanset hvor brugerne arbejder fra.

## <a name="strive-for-best-together-security-tools"></a>Stræb efter "bedst sammen"-sikkerhedsværktøjer

En anden hurdle Jeg kan se, at kunder falder over og tager en tilgang til sikkerhedsværktøjer, der er "det bedste af det bedste". En kontinuerlig lagning af "bedste af race" punktløsninger for at imødekomme nye sikkerhedsbehov får virksomhedssikkerheden til at bryde sammen. Selv med de bedste resultater bliver værktøjerne i de fleste miljøer ikke integreret, fordi det bliver for dyrere og komplekst. Dette skaber igen mellemrum, så synligheden bliver større, da der er flere vigtige beskeder, der skal håndteres, end teamet kan håndtere. Omskoling af SecOps-teamet til nye værktøjer bliver også en konstant udfordring.

Den "simple er bedre"-tilgang fungerer også af sikkerhedsmæssige hensyn. I stedet for at gå efter "bedste af race"-værktøjer, kan du sejle over dette knyt ved at indføre en strategi for "bedst sammen" med værktøjer, der arbejder sammen som standard. Microsoft-sikkerhedsfunktioner beskytter hele organisationen med integreret trusselsbeskyttelse, der omfatter programmer, brugere og skyer. Integration gør en organisation i stand til at være mere robust og reducere risikoen ved at begrænse hackere, der kommer ind, og hurtigt rette op på angreb.

## <a name="balance-security-with-functionality"></a>Balancer sikkerhed med funktionalitet

Når jeg kommer fra en lang baggrund og erfaring med cybersikkerhed, foretrækker jeg typisk at starte med den mest sikre konfiguration og give organisationer mulighed for at slappe af sikkerhedskonfigurationer baseret på deres drifts- og sikkerhedsbehov. Dette kan dog få en stor pris på mistet funktionalitet og dårlig brugeroplevelse. Som mange organisationer har lært, kan de, hvis sikkerheden er for svær for brugerne, finde en måde at løse dig på, herunder ved hjælp af ikke-administrerede skytjenester. Så vanskeligt som det er for mig at acceptere, er jeg blevet klar over, at den følsomme funktionalitet-sikkerhedsbalance skal opnås.

Organisationer, der indser, at brugerne vil gøre alt, hvad der kræves for at få deres arbejde udført, anerkender, at "Skygge IT-striden" ikke er værd at kæmpe mod. De ved, at it-medarbejdere er de største fordele ved brugen af Shadow IT og brugen af ikke-godkendte SaaS-programmer til deres arbejde. De har ændret deres strategi for at fremme brugen af den (i stedet for at undertrykke) og fokusere på at mindske risikoen for eksponering, den kan skabe. Disse organisations sikkerhedsteams har ikke på samme måde at gøre, at alt bliver blokeret, logget og sendt via en omvendt proxy eller et VPN. I stedet for fordobler disse sikkerhedsteams deres bestræbelser på at beskytte værdifulde og følsomme data fra at blive eksponeret for de forkerte parter eller ondsindede apps. De arbejder på at beskytte integriteten af dataene. De gør fuld brug af mere avancerede funktioner til beskyttelse af skyoplysninger, herunder kryptering, sikker multifaktorgodkendelse, automatiseret risiko og overholdelse af regler og standarder og sikkerhedsmæglerfunktioner i skyen, mens du tillader og endda fremmer den beskyttede deling på tværs af flere platforme. De forvandler din skygge it til inspirerende kreativitet, produktivitet og samarbejde, som giver deres virksomhed mulighed for at bevare sin konkurrencemæssige kant.

## <a name="adopt-a-methodical-approach"></a>Brug en metodisk tilgang

De fleste af de udfordringer, jeg har oplevet med implementering af skysikkerhed i forskellige organisationer uanset branche, har været meget ens. For det første er der, selvom der er masser af god dokumentation om specifikke funktioner og funktioner, et niveau af forvirring på organisationsniveau om, hvad der gælder for dem, hvor sikkerhedsfunktioner overlapper, og hvordan funktioner skal integreres. Der er også en grad af usikkerhed om, hvilke sikkerhedsfunktioner der er konfigureret på forhånd, og som kræver konfiguration i organisationen. Desuden har SOC-grupperne desværre ikke haft den fulde eksponering, uddannelse eller det nødvendige budget til allokering for at forberede en hurtig skybaseret indføring og digital transformation, som deres organisationer allerede gennemgår.

For at hjælpe dig med at rydde disse huer har Microsoft curated several resources designed to help you take a methodical approach to your security strategy and implementation.

|Ressource   |Flere oplysninger  |
|---------|---------|
|[Vigtigste opgaver for sikkerhedsteams til at understøtte hjemmearbejde](../security/top-security-tasks-for-remote-work.md)      | Hvis du pludselig understøtter en arbejdsbaseret arbejdsstyrke, hjælper denne artikel dig med hurtigt at øge sikkerheden. Den indeholder de mest anbefalede opgaver, der er baseret på din licensplan.    |
|[Microsoft 365 security for Business Decisions Makers](../security/Microsoft-365-security-for-bdm.md)    | Når du har tid til en mere omfattende plan, indeholder denne artikel anbefalinger, der strækker Microsoft 365, som er prioriteret af angrebsoverfladen. Den leveres endda med et regneark, du kan bruge til at sortere i licenser og områder (f.eks. identitet, trusselsbeskyttelse og overvågning).  |
|[Anbefalinger til Microsoft-sikkerhedsarkitektur](/security/compass/compass)    | Hvis du er sikkerhedsarkitekt, skal du sørge for at få vist sikkerhedsanbefalinger organiseret efter disciplin, herunder identitet, netværk og sikkerhedshandlinger.   |
|[Anbefalinger til Microsoft-sikkerhedshandlinger](/security/compass/security-operations-videos-and-decks)|Få mere at vide om Microsoft-anbefalinger til konfiguration og kørsel af et Security Operations Center (SOC) |
|[Chief Information Security Officer (CISO) Workshop Training](/security/ciso-workshop/ciso-workshop)   | Hvis du er ny bruger af skysikkerhed, skal du ikke gå glip af denne serie af videoer.        |
|[docs.security.com/security](/security/)    | Teknisk vejledning på tværs af Microsoft til sikkerhedsstrategi og -arkitektur.        |
| | |

Alle disse ressourcer er designet til at blive brugt som et udgangspunkt og tilpasset organisationens behov.
