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
description: Find ud af, hvor dine Microsoft 365 kundedata er gemt i Den Europæiske Union
ms.openlocfilehash: fa1f1548039f060ae51131fbfcbb0b6ab61c9b70
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822622"
---
# <a name="data-locations-for-the-european-union"></a>Dataplaceringer for EU

## <a name="your-data-is-your-business"></a>Dine data er din virksomhed

Microsoft anerkender vigtigheden af at opretholde beskyttelsen af personlige oplysninger og fortroligheden af dine forretningsdata. Dine data tilhører dig, og du kan til enhver tid få adgang til, redigere eller slette dem. Microsoft vil ikke bruge dine data uden dit samtykke, og når vi har dit samtykke, bruger vi dine data til kun at levere de tjenester, du har valgt. Hvis du forlader en af vores tjenester, sikrer vi, at du fortsat ejer dine data og følger strenge standarder og processer for at fjerne dataene fra vores systemer.

> [!NOTE]
> Kundedata (også kaldet "dine data" eller "dine forretningsdata") betyder alle data, herunder tekst-, lyd-, video- eller billedfiler og software, som du leverer til Microsoft, eller som leveres på dine vegne via din brug af Microsoft enterprise onlinetjenester, bortset fra Microsoft Professional Services. Det omfatter kundeindhold, som er de data, du uploader til lagring eller behandling, og apps, du uploader til distribution via en Microsoft Enterprise-cloudtjeneste. Kundeindhold omfatter f.eks. Exchange Online mails og vedhæftede filer, SharePoint onlineindhold på webstedet eller chatsamtaler.

## <a name="data-storage-and-processing"></a>Datalager og -behandling

Når du bruger Microsoft 365 tjenester, starter vi med den antagelse, at vores virksomhedskunder gerne vil have deres forretningsdata gemt og behandlet tæt på hjemmet. Så vidt det er muligt, gør vi netop det. Hvis du vil beholde dine data i datacentre, der er tættest på dig, gemmer vi dine data baseret på den forretningsplacering, du angiver, når du opretter din lejer. Hvis du vil vælge lagerplaceringer, der giver mening for din organisations virksomheder, kan du oprette lige så mange lejere til din organisation, som du vil.

### <a name="where-eu-data-is-stored"></a>Hvor EU-data gemmes

Vi har datacenter-geos i Tyskland og Frankrig, der giver dig mulighed for at gemme data i dit land, hvis din virksomhed er placeret der. Vores regionale eu-datacentre er placeret i Østrig, Finland, Frankrig, Irland og Holland. Dine data for følgende tjenester hostes på følgende placeringer, afhængigt af hvilken faktureringsadresse du vælger:

| Tjenestenavn | Placering for lejere, der er oprettet med en faktureringsadresse i Frankrig | Placering for lejere, der er oprettet med en faktureringsadresse i Tyskland | Placering for lejere, der er oprettet med en faktureringsadresse i alle andre EU-lande |
|---|---|---|---|
| Exchange Online | Frankrig | Tyskland | Eu |
| OneDrive for Business | Frankrig | Tyskland | Eu |
| SharePoint Online | Frankrig | Tyskland | Eu |
| Skype for Business | Eu | Eu | Eu |
| Microsoft Teams | Frankrig | Tyskland | Eu |
| Office Online & Mobile | Frankrig | Tyskland | Eu |
| Exchange Online Protection | Frankrig | Tyskland | Eu |
| Intune | Eu | Eu | Eu |
| MyAnalytics | Frankrig | Tyskland | Eu |
| Planner | Eu | Eu | Eu |
| Yammer | Eu | Eu | Eu |
| OneNote-tjenester | Frankrig | Tyskland | Eu |
| Stream | Eu | Eu | Eu |
| Whiteboard | Eu | Eu | Eu |
| Former | Eu | Eu | Eu |

> [!NOTE]
> Hvis du har et Office 365 Education abonnement med en faktureringsadresse i Frankrig eller Tyskland, kan dine data blive gemt i vores regionale EU-datacentre. Du kan se placeringen af lejerdata uden for EU under [Hvor dine Microsoft 365 kundedata er gemt](o365-data-locations.md).

### <a name="where-eu-data-is-computed"></a>Hvor EU-data beregnes

Når du starter brugen af en af ovenstående tjenester, udføres de beregninger, der er nødvendige for at levere tjenesten for dine data, der er gemt i et af vores regionale europæiske datacentre (eller i dit land), inden for den samme geografiske grænse, medmindre en midlertidig dataoverførsel er nødvendig for at udføre beregningen i et Microsoft-datacenter, der ligger længere væk.

Hvis en midlertidig overførsel er påkrævet, anvender vi altid den nyeste kryptering i overførslen, og vi vil altid returnere dine data til din valgte datalagerplacering umiddelbart derefter. Vi er afhængige af vores overholdelse af europæisk lovgivning gennem standardkontraktbestemmelserne for disse midlertidige overførsler sammen med vores supplerende foranstaltninger for at sikre, at dataene beskyttes.

Du kan få mere at vide under [Eu-modelklausuler](/compliance/regulatory/offering-EU-Model-Clauses).

> [!NOTE]
> Kundedata for Sway og Workplace Analytics gemmes og beregnes i USA, hvis du vælger at bruge disse tjenester.
>
> Microsoft 365 tjenester kan forespørge på og gemme dele af lejermappen/identitetsdata i andre områder end EU, hvor det er nødvendigt for at lette visse scenarier. I scenarier med distribution af mail på tværs af regioner, opkaldsrouting og godkendelse kan Microsoft 365 systemer f.eks. få brug for nogle oplysninger om EU-modtagere for at kunne distribuere disse anmodninger korrekt. Microsoft 365 systemer afhænger også af Azure Active Directory for identitets- og godkendelsesfunktioner. Du kan få mere at vide under [Lagring af identitetsdata for europæiske kunder i Azure Active Directory](/azure/active-directory/fundamentals/active-directory-data-storage-eu).

## <a name="how-microsoft-protects-your-data"></a>Sådan beskytter Microsoft dine data

### <a name="security-measures"></a>Sikkerhedsforanstaltninger

Microsoft sikrer dine data ved hjælp af flere lag af sikkerheds- og krypteringsprotokoller. Få en oversigt over Microsofts funktioner til datasikkerhed i [artiklen om Microsoft 365 kryptering](../compliance/encryption.md).

Microsoft-administrerede nøgler beskytter som standard dine kundedata. Data, der bevares på alle fysiske medier, krypteres altid ved hjælp af FIPS 140-2-kompatible krypteringsprotokoller. Du kan også anvende kundeadministrerede nøgler (CMK), [dobbelt kryptering](../compliance/double-key-encryption.md) og/eller HSM'er (Hardware Security Modules) til øget databeskyttelse.

Derudover bruger Microsoft som standard [TLS-protokollen (Transport Layer Security)](https://wikipedia.org/wiki/Transport_Layer_Security) til at kryptere data, når de kører mellem cloudtjenesterne og kunderne. Microsoft Services forhandler en TLS-forbindelse med klientsystemer, der opretter forbindelse til Microsoft 365 tjenester.

For at forhindre uautoriseret fysisk adgang til datacentre anvender vi strenge driftsmæssige kontroller og processer, der omfatter videoovervågning døgnet rundt, oplært sikkerhedspersonale og -processer samt chipkort eller biometriske multifaktoradgangskontroller. Ved afslutningen af levetiden makuleres og destrueres datadiske. Hvis et diskdrev, der bruges til lagring, lider af en hardwarefejl eller når sin levetid, slettes eller destrueres det sikkert. Dataene på drevet overskrives fuldstændigt for at sikre, at dataene ikke kan gendannes på nogen måde. Når sådanne enheder tages ud af drift, makuleres og destrueres de i overensstemmelse med NIST SP 800-88 R1, Retningslinjer for medierensning. Registreringer af ødelæggelsen opbevares og gennemses som en del af Microsofts overvågnings- og overholdelsesproces. Alle Microsoft 365 tjenester anvender godkendte tjenester til lagring og bortskaffelse af medier.

### <a name="technical-controls"></a>Tekniske kontrolelementer

Ud over den fysiske og teknologiske beskyttelse træffer Microsoft stærke foranstaltninger for at beskytte dine kundedata mod uautoriseret adgang fra Microsoft-medarbejdere og underleverandører. Microsofts handlinger og supportafdelingens adgang til kundedata nægtes som standard. Næsten alle tjenestehandlinger, der udføres af Microsoft, er fuldt automatiserede, og menneskelig involvering styres og udtrækkes i høj grad fra kundedata.

Det er kun i sjældne tilfælde, at en Microsoft-tekniker har brug for adgang til kundedata. Dette er typisk kun nødvendigt, hvis du anmoder Microsofts hjælp om at løse et kundeproblem. Adgang til kundedata begrænses i høj grad af rollebaserede adgangskontroller, multifaktorgodkendelse, dataminiimering og andre kontrolelementer. Al adgang til kundedata logføres strengt, og både Microsoft og tredjeparter udfører regelmæssig overvågning (samt eksempelrevisioner) for at bekræfte, at enhver adgang er passende.

Kunder kan bruge kundeadministrerede nøgler til yderligere at forhindre, at deres data kan læses i tilfælde af uautoriseret adgang. Kryptering på både serversiden og klientsiden kan være afhængig af kundeadministrerede nøgler eller kundeundergivne nøgler. I begge tilfælde har Microsoft ikke adgang til krypteringsnøgler og kan ikke dekryptere dataene. En SOC-revision foretaget af en AICPA-akkrediteret revisor to gange om året for at kontrollere effektiviteten af vores sikkerhedskontroller inden for revisionsområdet. Attestationsrapport for SOC 2 type 2, som er offentliggjort af revisor, forklarer under hvilke omstændigheder adgang til kundedata kan ske, og hvordan.

Ud over at gemme og behandle dine data, når du bruger onlinetjenester, genererer Microsoft tjenestedata for at overvåge systemtilstanden og udføre tjenestehandlinger som f.eks. fejlfinding. Som en beskyttende foranstaltning til beskyttelse af personlige oplysninger genererer Microsoft og er afhængig af pseudonyme identifikatorer i denne tjeneste genererede data for at kunne skelne mellem én bruger og en anden uden at identificere de faktiske brugere. Pseudonyme identifikatorer identificerer ikke en person direkte, og de oplysninger, der gør det muligt at knytte pseudonyme id'er til faktiske brugere, beskyttes som en del af dine data.

Du kan få mere at vide under [Who kan få adgang til dine data](https://www.microsoft.com/trust-center/privacy/data-access) og på hvilke vilkår og [underdatabehandlere og beskyttelse af personlige oplysninger](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4qVL2).

## <a name="how-microsoft-handles-government-requests"></a>Sådan håndterer Microsoft anmodninger fra offentlige myndigheder

Hvis en regering ønsker kundedata, skal den følge relevante juridiske processer. Microsoft skal have en kendelse eller en retskendelse for indhold eller en stævning for abonnentoplysninger eller andre ikke-indholdsdata.

- Alle anmodninger skal være målrettet bestemte konti og id'er.
- Microsofts juridiske overholdelsesteam gennemgår alle anmodninger for at sikre, at de er gyldige, afviser dem, der ikke er gyldige, og leverer kun de angivne data.
- Hvis Microsoft i henhold til loven er tvunget til at videregive kundedata, vil du straks blive underrettet om og forsynet med en kopi af anmodningen, medmindre Microsoft er juridisk forbudt at gøre det.
- Microsoft foretager en lokal juridisk gennemgang af hver anmodning, den modtager, i forhold til lokale love og standarder. Microsoft gennemgår også jævnligt sine screeningprocesser rundt om i verden for at sikre, at lokale retslige procedurer følges, og at dets globale menneskerettighedserklæring anvendes.

Du kan finde flere oplysninger om Microsofts forpligtelse til at udfordre ordrer i overensstemmelse med EU's GDPR under [Nye trin til at forsvare dine data](https://blogs.microsoft.com/on-the-issues/2020/11/19/defending-your-data-edpb-gdpr/).

Når regeringer eller retshåndhævende myndigheder foretager en lovlig anmodning om kundedata, er Microsoft forpligtet til gennemsigtighed og begrænser det, det videregiver. To gange om året udgiver vi antallet af juridiske krav om kundedata, som vi modtager fra retshåndhævende myndigheder over hele verden. Se [Rapport over retsanmodninger](https://www.microsoft.com/corporate-responsibility/law-enforcement-requests-report). Denne rapport videregiver ikke specifikationerne for en bestemt efterspørgsel, herunder den pågældende kunde. To gange om året udgiver vi også data om de juridiske krav, vi modtager fra den amerikanske regering. Se [Rapporten over nationale sikkerhedsordrer i USA](https://www.microsoft.com/corporate-responsibility/us-national-security-orders-report) for at få den seneste rapport.

Du kan få mere at vide under [Ofte stillede spørgsmål](https://blogs.microsoft.com/datalaw/our-practices/) om anmodninger fra offentlige myndigheder og retshåndhævende myndigheder, herunder spørgsmål om CLOUD-loven.

## <a name="additional-resources"></a>Flere ressourcer

- [Databeskyttelse, der er tillid til](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FhZn) , giver et overblik over, hvordan Microsoft beskytter dine data, når du bruger Microsoft Online Services og Professional Services. Det foreslås også, at du konsulterer de [Vilkår for Microsoft Online Services (OST) og DPA (Data Protection Addendum),](https://www.microsoft.com/licensing/product-licensing/products) der styrer din brug af disse tjenester.
- [Office 365 registreredes anmodninger om GDPR](/compliance/regulatory/gdpr-dsr-Office365) hjælper dig med at finde og handle på personlige data eller personlige oplysninger for at besvare DSR-anmodninger ved hjælp af Microsoft 365 produkter, tjenester og administrative værktøjer.
- [Konsekvensvurderinger af databeskyttelse: Vejledning til datacontrollere Brug af Microsoft Office 365](/compliance/regulatory/gdpr-dpia-office365) hjælper dig med at afgøre, om din organisation skal udarbejde en DPIA, indeholder "hvordan" vejledning, indeholder et DPIA-skabelondokument, der kan tilpasses, og leverer en matrix for DPIA-tjenesteelementer til mange Microsoft 365 tjenester.
- [Få mere at vide om, hvordan moduler](/learn/paths/audit-safeguard-customer-data/) er designet til personer med overvågnings-, overholdelses-, risiko- og juridiske roller, som søger en overordnet forståelse, giver en detaljeret gennemgang af, hvordan Microsoft 365 grundlæggende praksis for sikkerhed og beskyttelse af personlige oplysninger for at beskytte kundedata.
- [Microsofts tilbud om overholdelse af angivne](/compliance/regulatory/offering-home) standarder viser, hvordan Microsoft 365 tjenester hjælper din organisation med at overholde lovmæssige standarder.
