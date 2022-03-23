---
title: Dataplaceringer for EU
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Fastlægge, hvor Microsoft 365 dine kundedata gemmes i EU
ms.openlocfilehash: 145d20cbcf80345723ad342e76048958f56a915d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590706"
---
# <a name="data-locations-for-the-european-union"></a>Dataplaceringer for EU



## <a name="your-data-is-your-business"></a>Dine data er din virksomhed

Microsoft anerkender vigtigheden af at bevare beskyttelse af personlige oplysninger og fortroligheden af dine forretningsdata. Dine data tilhører dig, og du kan til enhver tid få adgang til, ændre eller slette dem. Microsoft vil ikke bruge dine data uden dit samtykke, og når vi har dit samtykke, bruger vi dine data til kun at levere de tjenester, du har valgt. Hvis du efterlader en af vores tjenester, sikrer vi dit fortsatte ejerskab af dine data ved at følge strenge standarder og processer til at fjerne data fra vores systemer. 

>[!Note]
>Kundedata (også kaldet "dine data" eller "dine forretningsdata") betyder alle data, herunder tekst-, lyd-, video- eller billedfiler samt software, du leverer til Microsoft, eller som leveres på dine vegne via din brug af Microsofts virksomheds onlinetjenester, undtagen Microsoft Professional Services. Det omfatter kundeindhold, som er de data, du overfører til lagring eller behandling, og apps, du overfører til distribution via en skybaseret Microsoft-tjeneste til virksomheder. Kundeindhold omfatter f.eks. Exchange Online mails og vedhæftede filer, SharePoint onlinewebstedsindhold eller chatsamtaler. 
>

## <a name="data-storage-and-processing"></a>Datalagring og -behandling

Når du bruger Microsoft 365-tjenester, starter vi med den forudsætning, at vores virksomhedskunder gerne vil have deres virksomhedsdata gemt og behandlet tæt på hjemmet. Hvor det er muligt, gør vi netop det. For at bevare dine data i de datacentre, der er nærmest dig, gemmer vi dine data baseret på den virksomhedsplacering, du angiver, når du opretter din lejer. Hvis du vil vælge lagerplaceringer, der giver mening for din organisations virksomheder, kan du oprette lige så mange lejere i organisationen, som du ønsker.  

### <a name="where-eu-data-is-stored"></a>Hvor EU-data gemmes

Vi har datacenter-geos i Tyskland og Frankrig, der giver dig mulighed for at gemme data i dit land, hvis din virksomhed er placeret der. Vores regionale datacentre i EU er placeret i Østrig, Finland, Frankrig, Irland og Nederlandene. Dine data for følgende tjenester hostes på følgende placeringer, afhængigt af hvilken faktureringsadresse du vælger: 

| Tjenestenavn | Placering for lejere oprettet med en faktureringsadresse i Frankrig | Placering for lejere, der er oprettet med en faktureringsadresse i Tyskland | Placering for lejere oprettet med en faktureringsadresse i alle andre EU-lande |
|:-------|:-----|:-------|:-------|
| Exchange Online | Frankrig | Tyskland | EU |
| OneDrive for Business | Frankrig | Tyskland | EU |
| SharePoint Online | Frankrig | Tyskland | EU |
| Skype for Business | EU | EU | EU |
| Microsoft Teams | Frankrig | Tyskland | EU |
| Office Online & Mobile | Frankrig | Tyskland | EU |
| Exchange Online Protection | Frankrig | Tyskland | EU |
| Intune | EU | EU | EU |
| MyAnalytics | Frankrig | Tyskland | EU |
| Planner | EU | EU | EU |
| Yammer | EU | EU | EU |
| OneNote tjenester | Frankrig | Tyskland | EU |
| Stream | EU | EU | EU |
| Whiteboard | EU | EU | EU |
| Formularer | EU | EU | EU |
||||| 

>[!Note]
>Hvis du har et Office 365 Education-abonnement med en faktureringsadresse i Frankrig eller Tyskland, kan dine data blive gemt i vores regionale EU-datacentre. For placeringerne af lejerdata uden for EU skal du se [Hvor Microsoft 365 dine kundedata er gemt](o365-data-locations.md).
>



### <a name="where-eu-data-is-computed"></a>Hvor EU-data beregnes

Når du påbegynder brugen af nogen af de ovenstående tjenester, udføres beregningerne for at levere tjenesten til dine data, der er gemt i et af vores regionale europæiske datacentre (eller i dit land), inden for den samme geografiske grænse, medmindre en midlertidig dataoverførsel er nødvendig for at udføre beregningerne i et Microsoft-datacenter, der er placeret længere væk. 

Hvis en midlertidig overførsel er påkrævet, anvender vi altid den avancerede kryptering i overførslen, og vi vil altid returnere dine data til din valgte datalagringsplacering med det samme. Vi er afhængige af vores overholdelse af den europæiske lovgivning via standard kontraktmæssige delsætninger (SCCs) for disse midlertidige overførsler sammen med vores supplerende foranstaltninger for at sikre, at dataene er beskyttet. 

Du kan få mere at vide [under EU-modelklausuler](/compliance/regulatory/offering-EU-Model-Clauses).

>[!Note]
>Kundedata for Sway og Workplace Analytics bliver gemt og beregnet i USA, hvis du vælger at bruge disse tjenester.
>

>[!Note]
>Microsoft 365-tjenester kan forespørge og gemme dele af dataoplysninger om lejermapper/-identiteter i andre områder end EU, hvor det er nødvendigt for at muliggøre visse scenarier. I scenarier med routing af mails på tværs af regioner, videresendelse af opkald og godkendelse kan der i Microsoft 365-systemer være brug for oplysninger om EU-modtagere for at distribuere disse anmodninger korrekt. Microsoft 365-systemer afhænger også af Azure Active Directory til identitets- og godkendelsesfunktioner. Du kan få mere at vide [under Lagring af identitetsdata for europæiske kunder Azure Active Directory](/azure/active-directory/fundamentals/active-directory-data-storage-eu).
>

## <a name="how-microsoft-protects-your-data"></a>Sådan beskytter Microsoft dine data

### <a name="security-measures"></a>Sikkerhedsforanstaltninger

Microsoft sikrer dine data ved hjælp af flere lag af sikkerheds- og krypteringsprotokoller. Få et overblik over Microsofts datasikkerhedsfunktioner i [artiklen Microsoft 365 kryptering](../compliance/encryption.md).

Microsoft Managed Keys beskytter som standard dine kundedata. Data, der bevares på fysiske medier, krypteres altid med FIPS 140-2-kompatible krypteringsprotokoller. Du kan også anvende kunde-administrerede nøgler (CMK), [dobbelt](../compliance/double-key-encryption.md) kryptering og/eller hardwaresikkerhedsmoduler (HSMs) for at øge databeskyttelsen.

Desuden bruger Microsoft som standard [TLS-protokollen (Transport Layer Security)](https://wikipedia.org/wiki/Transport_Layer_Security) til at kryptere data, når de rejser mellem skytjenesterne og kunderne. Microsoft Services forhandler en TLS-forbindelse med klientsystemer, der opretter forbindelse Microsoft 365 tjenester. 

For at forhindre uautoriseret fysisk adgang til datacentre anvender vi omfattende driftskontroller og processer, der omfatter 24×7 videoovervågning, uddannet sikkerhedsmedarbejder og processer samt chipkort eller biometriske multifaktoradgangskontrolelementer. Når levetiden er slut, bliver datadiskssed og ødelagt. Hvis et diskdrev, der bruges til lagerplads, går ud over en hardwarefejl eller når slutningen af dens levetid, bliver den sikkert slettet eller ødelagt. Dataene på drevet overskrives fuldstændigt for at sikre, at dataene ikke kan gendannes på nogen måde. Når disse enheder udkom, frigøres og ødelægges de i overensstemmelse med NIST SP 800-88 R1, Retningslinjer for medieopdefinering. Alle talerens registreringer bevares og gennemgås som en del af Microsofts revisions- og overholdelsesproces. Alle Microsoft 365 benytte godkendte medielagrings- og -afhændelsestjenester.

### <a name="technical-controls"></a>Tekniske kontrolfunktioner

Ud over de fysiske og teknologiske beskyttelser træffer Microsoft stærke foranstaltninger for at beskytte dine kundedata mod uautoriseret adgang fra Microsoft-medarbejdere og underleverandører. Microsofts handlinger og supportmedarbejdere har som standard ikke adgang til kundedata. Næsten alle tjenestehandlinger, der udføres af Microsoft, er fuldt ud automatiseret, og menneskelig deltagelse er stærkt kontrolleret og abstrakt væk fra kundedata. 

Kun i sjældne tilfælde skal en Microsoft-tekniker have adgang til kundedata. Dette er typisk kun nødvendigt, hvis du anmoder om Microsofts hjælp til at løse et kundeproblem. Adgang til kundedata begrænses meget af rollebaserede adgangskontrolelementer, multifaktorgodkendelse, data minimering og andre kontrolelementer. Al adgang til kundedata logføres strengt, og både Microsoft og tredjeparter udfører regelmæssige revisioner (samt stikprøver) for at bekræfte, at al adgang er relevant.

Kunder kan bruge kunde-administrerede nøgler for yderligere at forhindre, at deres data kan læses i tilfælde af uautoriseret adgang. Både kryptering på serversiden og på klientsiden kan stole på kunde-administrerede nøgler eller nøgler, der leveres af kunden. I begge tilfælde har Microsoft ikke adgang til krypteringsnøgler og kan ikke dekryptere dataene. En SOC-overvågning af en AICPA-godkendt revisor to gange om året for at bekræfte effektiviteten af vores sikkerhedskontroller, som er omfattet af revision. DEN SOC 2 Type 2-undersøgelsesrapport, der er publiceret af auditoren, forklarer under hvilke omstændigheder adgang til kundedata kan forekomme og hvordan. 

Ud over at lagre og behandle dine data, når du bruger onlinetjenesterne, genererer Microsoft tjenestedata for at overvåge systemets tilstand og udføre tjenestehandlinger som f.eks. fejlfinding. Som beskyttende beskyttelse af personlige oplysninger genererer og er Microsoft afhængig af pseudonymidentifikatorer i denne tjeneste for at kunne skelne én bruger fra en anden uden at identificere de faktiske brugere. Pseudonym-identifikatorer identificerer ikke direkte en person, og de oplysninger, der gør det muligt at knytte pseudonymidentifikatorer til faktiske brugere, beskyttes som en del af dine data.

Du kan få mere at [vide Who du kan få adgang](https://www.microsoft.com/trust-center/privacy/data-access) til dine data og på hvilke vilkår og [Underbehandlere og Beskyttelse af personlige oplysninger for data](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4qVL2).

## <a name="how-microsoft-handles-government-requests"></a>Sådan håndterer Microsoft anmodninger fra offentlige myndigheder

Hvis en myndighed ønsker kundedata, skal den følge de gældende juridiske processer. Microsoft skal have en garantier eller retskendelse for indhold eller en stævning til abonnentoplysninger eller andre data, der ikke har indhold. 

- Alle anmodninger skal målrettes mod bestemte konti og identifikatorer.  
- Microsofts team til overholdelse af juridiske regler og standarder gennemser alle anmodninger for at sikre, at de er gyldige, afviser dem, der ikke er gyldige, og leverer kun de data, der er angivet.  
- Hvis Microsoft er godkendt af lovgivningen til at videregive kundedata, får du straks besked og får en kopi af anmodningen, medmindre Microsoft i henhold til lovgivningen har tilladelse til at gøre dette.
- Microsoft udfører en lokal juridisk gennemgang af hver anmodning, den modtager, i forhold til lokal lovgivning og standarder. Microsoft gennemser også jævnligt sine udvælgelsesprocesser over hele verden for at sikre, at der følges lokale retslige procedurer, og at dens globale erklæring om menneskerrettigheder anvendes.

Du kan finde flere oplysninger om Microsofts indsats i forbindelse med udfordringsordrer i overensstemmelse med EU's GDPR under Nye trin [til at beskytte dine data](https://blogs.microsoft.com/on-the-issues/2020/11/19/defending-your-data-edpb-gdpr/). 

Når stater eller håndhævende myndigheder anmoder om kundedata på lovlig vis, forpligter Microsoft sig til gennemsigtighed og begrænser, hvad det oplyser. To gange om året offentliggør vi antallet af juridiske krav til kundedata, som vi modtager fra håndhævende myndigheder i hele verden. Se [rapporten om anmodninger om håndhævelse af lovgivning](https://www.microsoft.com/corporate-responsibility/law-enforcement-requests-report). Denne rapport oplyser ikke de specifikke forhold ved et bestemt behov, herunder den pågældende kunde. To gange om året offentliggør vi også data om de juridiske krav, vi modtager fra den amerikanske stat. Se [us National Security Orders Report](https://www.microsoft.com/corporate-responsibility/us-national-security-orders-report) for den seneste rapport.  

Du kan få mere at vide [under Ofte stillede spørgsmål](https://blogs.microsoft.com/datalaw/our-practices/) om anmodninger om håndhævelse af offentlige myndigheder og loven, herunder spørgsmål om CLOUD Act.

## <a name="additional-resources"></a>Yderligere ressourcer
 
- [Beskyttelse af data, der](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FhZn) er tillid til, giver en oversigt over, hvordan Microsoft beskytter dine data, når du bruger Microsoft Online Services og Professionelle tjenester. Det foreslås også, at du rådfører dig med [Microsofts vilkår for onlinetjenester (OST) og DPA (Data Protection Addendum),](https://www.microsoft.com/licensing/product-licensing/products) der styrer din brug af disse tjenester.
- [Office 365 anmodninger fra registrerede om GDPR](/compliance/regulatory/gdpr-dsr-Office365) hjælper dig med at finde og handle på personlige data eller personlige oplysninger, så du kan svare på DSR'er ved hjælp af Microsoft 365-produkter, -tjenester og -administrationsværktøjer. 
- [Databeskyttelsesvurderinger: Vejledning til](/compliance/regulatory/gdpr-dpia-office365) dataansvarlige Brug af Microsoft Office 365 hjælper dig med at afgøre, om din organisation skal udarbejde en DPIA, giver vejledning om, hvordan du gør, omfatter et brugerdefineret DPIA-skabelondokument og leverer en DPIA-serviceelementermatrix til mange Microsoft 365-tjenester.
- Få mere at vide om, hvordan moduler er beregnet til personer i revisions-, [overholdelses](/learn/paths/audit-safeguard-customer-data/)-, risiko- og juridiske roller, som søger en overordnet forståelse, og giver en indgående gennemgang af, hvordan Microsoft 365's grundlæggende praksis for sikkerhed og beskyttelse af personlige oplysninger for at beskytte kundedata.
- [Microsofts overholdelsestilbud viser](/compliance/regulatory/offering-home), hvordan Microsoft 365-tjenester hjælper din organisation med at overholde lovmæssige overholdelsesstandarder.