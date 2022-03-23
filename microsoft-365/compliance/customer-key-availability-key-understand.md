---
title: Få mere at vide om tilgængelighedsnøglen til kundenøgle
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
description: Få mere at vide om tilgængelighedsnøglen, der bruges til at gendanne mistede kundenøgler.
ms.openlocfilehash: 72e66e9deb74400944c6ea65ea3ac167a703da26
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589590"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Få mere at vide om tilgængelighedsnøglen til kundenøgle

Tilgængelighedsnøglen er en rodnøgle, der genereres og klargøres, når du opretter en politik for datakryptering. Microsoft 365 gemmer og beskytter tilgængelighedsnøglen. Tilgængelighedsnøglen fungerer ligesom de to rodnøgler, du leverer til tjenestekryptering med kundenøgle. Tilgængelighedsnøglen ombryder tasterne ét niveau lavere i nøglehierarkiet. I modsætning til de nøgler, du angiver og administrerer i Azure Key Vault, kan du ikke få direkte adgang til tilgængelighedsnøglen. Microsoft 365 automatiserede tjenester administrerer tilgængelighed nøgle programatisk. Disse tjenester starter automatiserede handlinger, der aldrig involverer direkte adgang til tilgængelighedsnøglen.

Det primære formål med tilgængelighedsnøglen er at levere genoprettelsesfunktionalitet fra det uventede tab af rodnøgler, som du administrerer. Tab kan være et resultat af forkert administreret eller ondsindet handling. Hvis du mister styringen af rodnøglerne, skal du kontakte Microsoft Support, så vil Microsoft hjælpe dig gennem genoprettelsesprocessen ved hjælp af tilgængelighedsnøglen. Du skal bruge tilgængelighedsnøglen til at overføre til en ny datakrypteringspolitik med nye rodnøgler, du klargør.

Storage og kontrol over tilgængelighedsnøglen er bevidst forskellige fra Azure Key Vault-nøgler af tre årsager:

- Tilgængelighedsnøglen giver en genoprettelsesfunktion, "pauseglas", hvis du mister kontrollen over begge Azure-nøglenøglenøgler.
- Adskillelsen af logiske kontrolelementer og sikre lagerplaceringer giver forsvar i dybden og beskytter mod tab af alle nøgler og dine data fra et enkelt angreb eller et enkelt fejlpunkt.
- Tilgængelighedsnøglen giver mulighed for høj tilgængelighed, hvis Microsoft 365 ikke kan oprette forbindelse til nøgler, der er hostet i Azure Key Vault på grund af midlertidige fejl. Denne regel gælder kun for Exchange Online og Skype for Business tjenestekryptering. SharePoint Online-, OneDrive for Business- Teams filer bruger aldrig tilgængelighedsnøglen, medmindre du udtrykkeligt instruerer Microsoft i at starte gendannelsesprocessen.

Deling af ansvaret for at beskytte dine data ved hjælp af forskellige beskyttelser og processer til nøglestyring reducerer i sidste ende risikoen for, at alle nøgler (og derfor dine data) går permanent tabt eller ødelægges. Microsoft giver dig enekompetence til at deaktivere eller lade tilgængelighedsnøglen være tilgængelig, når du forlader tjenesten. Som design har ingen Microsoft adgang til tilgængelighedsnøglen: den er kun tilgængelig via Microsoft 365-tjenestekode.

Se [Microsoft Center for sikkerhed og beskyttelse](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) for at få flere oplysninger om, hvordan vi sikrer nøgler.
  
## <a name="availability-key-uses"></a>Anvendelse af tilgængelighedsnøgle

Tilgængelighedsnøglen giver genoprettelsesfunktionalitet til scenarier, hvor en ekstern mandlig eller ondsindet insider stjæler styringen af din nøgleboks, eller når utilsigtet fejlstyring medfører tab af rodnøgler. Denne genoprettelsesfunktion gælder for alle Microsoft 365, der er kompatible med kundenøgle. Individuelle tjenester bruger tilgængelighedsnøglen forskelligt. Microsoft 365 bruger kun tilgængelighedsnøglen på de måder, der er beskrevet nedenfor.

### <a name="exchange-online-and-skype-for-business-uses"></a>Exchange Online og Skype for Business bruger

Ud over genoprettelsesfunktionaliteten bruger Exchange Online og Skype for Business tilgængelighedsnøglen til at sikre datatilgængelighed under midlertidige eller forbigående driftsproblemer i forbindelse med den tjeneste, der får adgang til rodnøgler. Når en af dine kundenøgler ikke kan nås i Azure Key Vault på grund af midlertidige fejl, bruger tjenesten automatisk tilgængelighedsnøglen. Tjenesten går ALDRIG direkte til tilgængelighedsnøglen.

Automatiserede systemer i Exchange Online og Skype for Business kan bruge tilgængelighedsnøglen under midlertidige fejl til at understøtte automatiserede back end-tjenester som f.eks. antivirus, e-discovery, forebyggelse af datatab, postkassebevægelser og dataindeksering.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>SharePoint online-, OneDrive for Business og Teams, som filer bruger

For SharePoint Online-, OneDrive for Business- og Teams-filer bruges tilgængelighedsnøglen ALDRIG uden for genoprettelsesfunktionaliteten, og kunder skal udtrykkeligt instruere Microsoft i at starte brugen af tilgængelighedsnøglen under et genoprettelsesscenarie. Automatiserede servicehandlinger afhænger udelukkende af dine kundenøgler i Azure Key-boks. Du kan finde detaljerede oplysninger om, hvordan nøglehierarkiet fungerer for disse tjenester, under Sådan [SharePoint Online-, OneDrive for Business- Teams-filer bruger tilgængelighedsnøglen](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Tilgængelighedsnøglesikkerhed

Microsoft deler ansvaret for databeskyttelse med dig ved at instantiere tilgængelighedsnøglen og tage omfattende forholdsregler for at beskytte den. Microsoft viser ikke direkte kontrol over tilgængelighedsnøglen til kunderne. Du kan f.eks. kun rulle (rotere) de taster, du ejer i Azure Key Vault. Få mere at vide under [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Tilgængelighed vigtige hemmelige butikker

Microsoft beskytter tilgængelighedsnøgler i adgangskontrollerede, interne hemmelige butikker, f.eks. den Azure Key Vault, der er vendt mod kunden. Vi implementerer adgangskontrolelementer for at forhindre Microsoft-administratorer i at få direkte adgang til de hemmeligheder, der er indeholdt i. Hemmelige Store handlinger, herunder tasterotation og sletning, sker via automatiserede kommandoer, der aldrig involverer direkte adgang til tilgængelighedsnøglen. Administration af hemmelige lagre er begrænset til bestemte teknikere og kræver rettighedseskalering via et internt værktøj, Lockbox. Rettighedseskalering kræver ledergodkendelse og begrundelse, før de tildeles. Lockbox sikrer, at adgangen er tid bundet med automatisk tilbagekaldelse af adgang, når tiden udløber, eller at teknikeren logger af.

**Exchange Online og Skype for Business** for tilgængelighed gemmes i et Exchange Online Active Directory Secret Store. Tilgængelighedstaster gemmes sikkert i lejerspecifikke beholdere i Active Directory-domænecontroller. Denne sikre lagerplacering er separat og isoleret fra SharePoint Online, OneDrive for Business og Teams det hemmelige lager.

**SharePoint Online, OneDrive for Business og Teams filers** tilgængelighedsnøgler gemmes i et internt hemmeligt lager, der administreres af tjenesteteamet. Denne sikrede, hemmelige lagertjeneste har front end-servere med programslutpunkter og en SQL Database som back-end. Tilgængelighedsnøgler gemmes i SQL Database og ombrudt (krypteret) af krypteringsnøgler fra hemmelige lagre, der bruger en kombination af AES-256 og HMAC til at kryptere in tilgængelighedsnøglen. Krypteringsnøglerne til det hemmelige lager gemmes i en logisk isoleret komponent af samme SQL Database og krypteres yderligere med RSA-2048-nøgler, der er indeholdt i certifikater, som administreres af Microsoft-nøglecenteret. Disse certifikater gemmes i front end-serverne i det hemmelige lager, der udfører handlinger mod databasen.

### <a name="defense-in-depth"></a>Forsvars-i-dybde

Microsoft anvender en forsvarsbaseret dybdegående strategi for at forhindre ondsindede aktører i at påvirke fortroligheden, integriteten eller tilgængeligheden af kundedata, der er gemt i Microsoft Cloud. Specifikke sikkerheds- og sikkerhedskontroller er implementeret for at beskytte det hemmelige lager og tilgængelighedsnøglen som en del af den overordnede sikkerhedsstrategi.

Microsoft 365 er udviklet til at forhindre misbrug af tilgængelighedsnøglen. Programlaget er den eneste metode, hvorfra nøgler, herunder tilgængelighedsnøglen, kan bruges til at kryptere og dekryptere data. Kun Microsoft 365 tjenestekode kan fortolke og krydse nøglehierarkiet for krypterings- og dekrypteringsaktiviteter. Der findes logisk isolation mellem lagerplaceringerne for kundenøgler, tilgængelighedstaster, andre hierarkiske nøgler og kundedata. Denne isolation reducerer risikoen for data eksponering i tilfælde af, at en eller flere placeringer kompromitteres. Hvert lag i hierarkiet har indbyggede registreringsfunktioner til registrering af indtrængen 24x7 for at beskytte data og hemmeligheder, der er gemt.

Adgangskontrolelementer implementeres for at forhindre uautoriseret adgang til interne systemer, herunder adgangsnøgler til hemmelige butikker. Microsoft-teknikere har ikke direkte adgang til de vigtigste sikkerhedslagre. Hvis du vil have flere oplysninger om adgangskontrolelementer, [skal du gennemse Administrative Access-kontrolelementer Microsoft 365](/compliance/assurance/assurance-administrative-access-controls-overview).

Tekniske kontroller forhindrer Microsoft-medarbejdere i at logge på tjenestekonti med de højpriviligerede rettigheder, som ellers ville blive brugt af hackere til at udgive sig for at Microsoft-tjenester. Disse kontrolelementer forhindrer f.eks. interaktiv logon.

Sikkerhedslogføring og overvågningskontroller er en anden dybdegående sikkerhedsforanstaltning, der er implementeret for at reducere risikoen Microsoft-tjenester og dine data. Microsoft-tjenesteteams har implementeret aktive overvågningsløsninger, der genererer beskeder og overvågningslogfiler. Alle tjenesteteams uploader deres logfiler til et centralt lager, hvor logfilerne samles og behandles. Interne værktøjer undersøger automatisk data for at bekræfte, at tjenesterne fungerer i en optimal, robust og sikker tilstand. Usædvanlig aktivitet markeres til yderligere gennemgang.

Alle loghændelser, der angiver en potentiel overtrædelse af Microsofts sikkerhedspolitik, bliver straks gjort opmærksom på Microsofts sikkerhedsteams. Microsoft 365 har konfigureret beskeder til at registrere forsøgt adgang til tilgængelighed vigtige hemmelige butikker. Beskeder genereres også, hvis Microsoft-medarbejdere forsøger interaktiv logon på tjenestekonti, som er forbudt og beskyttet af adgangskontrol. Microsoft 365 registrerer og advarer også ved afvigelser fra Microsoft 365 fra de normale oprindelige handlinger. Malefactors, der forsøger at misbruge Microsoft 365-tjenester, udløser advarsler, hvilket medfører, at alle disse personer modtages fra Microsofts skymiljø.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Brug tilgængelighedsnøglen til at gendanne efter tab af nøgler

Hvis du mister kontrollen over dine kundenøgler, giver tilgængelighedsnøglen dig mulighed for at gendanne og kryptere dine data igen.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Genoprettelsesprocedure for Exchange Online og Skype for Business

Hvis du mister kontrollen over dine kundenøgler, giver tilgængelighedsnøglen dig mulighed for at gendanne dine data og gøre dine Microsoft 365 ressourcer online igen. Tilgængelighedsnøglen beskytter fortsat dine data, mens du gendanner. På et højt niveau skal du oprette en ny dep og flytte påtrykte ressourcer til den nye politik for fuldt ud at komme i gang med nøgletab.

Hvis du vil kryptere dine data med nye kundenøgler, skal du oprette nye nøgler i Azure Key Vault, oprette en ny dep ved hjælp af de nye kundenøgler og derefter tildele den nye dep til de postkasser, der aktuelt er krypteret med den tidligere dep, hvor tasterne gik tabt eller blev kompromitteret.

Denne genkrypteringsproces kan tage op til 72 timer. Dette er standardvarigheden, når du ændrer en dep.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Genoprettelsesprocedure for SharePoint Online-, OneDrive for Business- og Teams filer

For SharePoint Online-, OneDrive for Business- Teams-filer bruges tilgængelighedsnøglen ALDRIG uden for genoprettelsesfunktionaliteten. Du skal udtrykkeligt instruere Microsoft i at starte brugen af tilgængelighedsnøglen under et genoprettelsesscenarie. Kontakt Microsoft for at aktivere tilgængelighedsnøglen for at starte gendannelsesprocessen. Når tilgængelighedsnøglen er aktiveret, bruges den automatisk til at dekryptere dine data, så du kan kryptere dataene med en nyoprettet dep, der er knyttet til nye kundenøgler.  

Denne handling er i forhold til antallet af websteder i organisationen. Når du ringer til Microsoft for at bruge tilgængelighedsnøglen, bør du være helt online inden for ca. fire timer.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Sådan Exchange Online og Skype for Business bruge tilgængelighedsnøglen

Når du opretter en dep med kundenøgle, Microsoft 365 genererer en datakrypteringspolitiknøgle (DEP-nøgle), der er knyttet til den pågældende dep. Tjenesten krypterer DEP-nøglen tre gange: én gang med hver af kundens nøgler og én gang med tilgængelighedsnøglen. Kun de krypterede versioner af DEP-nøglen gemmes, og en DEP-nøgle kan kun dekrypteres med kundenøglerne eller tilgængelighedsnøglen. DEP-nøglen bruges derefter til at kryptere postkassenøgler, som krypterer individuelle postkasser.
  
Microsoft 365 denne proces til at dekryptere og levere data, når kunderne bruger tjenesten:
  
1. Dekrypter DEP-nøglen ved hjælp af kundenøglen.

2. Brug den dekrypterede DEP-nøgle til at dekryptere en postkassenøgle.

3. Brug den dekrypterede postkassenøgle til at dekryptere selve postkassen, så du kan få adgang til dataene i postkassen.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Sådan SharePoint Online-, OneDrive for Business og Teams filer tilgængelighedsnøglen

Den SharePoint online og OneDrive for Business arkitektur og implementering til kundenøgle og tilgængelighedsnøgle er forskellige fra Exchange Online og Skype for Business.
  
Når en organisation flytter til kunde-administrerede nøgler, opretter Microsoft 365 en organisationsspecifik mellemliggende nøgle (TIK). Microsoft 365 krypterer TIK to gange, én gang med hver af kundenøglerne, og gemmer de to krypterede versioner af TIK. Kun de krypterede versioner af TIK gemmes, og et TIK kan kun dekrypteres med kundenøglerne. TIK bruges derefter til at kryptere webstedstaster, som derefter bruges til at kryptere blob-nøgler (også kaldet filtaster). Afhængigt af filstørrelsen kan tjenesten opdele en fil i flere filsegmenter hver med en entydig nøgle. Selve blobs (filsegmenterne) krypteres med blob-tasterne og gemmes i Microsoft Azure Blob-lagertjeneste.
  
Microsoft 365 denne proces til at dekryptere og levere kundefiler, når kunderne bruger tjenesten:

1. Dekryptere TIK ved hjælp af kundenøglen.

2. Brug den dekrypterede TIK til at dekryptere en webstedsnøgle.

3. Brug den dekrypterede webstedsnøgle til at dekryptere en blob-nøgle.

4. Brug den dekrypterede blob-nøgle til at dekryptere bloben.

Microsoft 365 dekrypterer en TIK ved at udstede to dekrypteringsanmodninger til Azure Key Vault med en lille forskydning. Den første, der er færdig, viser resultatet og annullerer den anden anmodning.
  
Hvis du mister adgang til dine kundenøgler, krypterer Microsoft 365 også TIK med en tilgængelighedsnøgle og gemmer dette sammen med de TIKs, der er krypteret med hver kundenøgle. TIK-krypteret med tilgængelighedsnøglen bruges kun, når kunden ringer til Microsoft for at få vist genoprettelsesstien, når de har mistet adgangen til deres nøgler med ondsindet eller utilsigtet fejl.
  
Af hensyn til tilgængelighed og skalering cachelagres dekrypterede TIKs i en tidsgrænset hukommelsescache. To timer før en TIK-cache er indstillet til at udløbe, Microsoft 365 at dekryptere hver TIK. Dekryptering af tiks forlænger cachens levetid. Hvis TIK-dekryptering mislykkes i et betydeligt tidsrum, Microsoft 365 genererer en besked, der skal underrettes, før cachen udløber. Kun hvis kunden ringer, vil Microsoft Microsoft 365 starte genoprettelsen, hvilket indebærer dekryptering af TIK med tilgængelighedsnøglen gemt i Microsofts hemmelige butik og onboarding af lejeren igen ved hjælp af det dekrypterede TIK og et nyt sæt af Azure Key Vault-nøgler, der leveres af kunden.
  
Fra og med i dag er Kundenøgle involveret i kryptering og dekryptering af kæde til SharePoint Online-fildata, der er gemt i Azure Blob Store, men ikke i SharePoint Online-listeelementer eller metadata, der er gemt i SQL Database. Microsoft 365 bruger ikke tilgængelighedsnøglen til Exchange Online-, Skype for Business-, SharePoint Online-, OneDrive for Business- og Teams-filer ud over det tilfælde, der er beskrevet ovenfor, som er startet af kunden. Menneskelig adgang til kundedata er beskyttet af kunde lockbox.

## <a name="availability-key-triggers"></a>Udløsere af tilgængelighedsnøgler

Microsoft 365 udløser kun tilgængelighedsnøglen under bestemte omstændigheder. Disse omstændigheder er forskellige efter tjeneste.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Udløsere til Exchange Online og Skype for Business
  
1. Microsoft 365 læser den dep, som postkassen er tildelt, for at bestemme placeringen af de to kundenøgler i Azure Key Vault.

2. Microsoft 365 vælger tilfældigt en af de to kundenøgler fra dataudbyderen og sender en anmodning til Azure Key Vault om at fjerne afrapning af DEP-nøglen ved hjælp af kundenøglen.

3. Hvis anmodningen om at fjerne afrapning af DEP-nøglen med kundenøglen mislykkes, sender Microsoft 365 endnu en anmodning til Azure Key Vault og instruerer denne gang i at bruge den alternative (anden) kundenøgle.

4. Hvis den anden anmodning om at fjerne afrapning af deP-nøglen ved hjælp af kundenøglen mislykkes, Microsoft 365 undersøgelse af resultaterne af begge anmodninger.

    - Hvis undersøgelsen afgør, at anmodningerne ikke kunne returnere en systemFEJL:

       - Microsoft 365 udløser tilgængelighedsnøglen til at dekryptere DEP-nøglen.

       - Microsoft 365 bruger derefter dekrypteringsnøglen til at dekryptere postkassenøglen og fuldføre brugeranmodningen. 

       - I dette tilfælde kan Azure Key Vault enten ikke svare eller er ikke tilgængelig på grund af en midlertidig FEJL.

    - Hvis undersøgelsen afgør, at anmodningerne ikke kunne returnere ACCESS DENIED:

       - Det betyder, at der er taget velovervejede, utilsigtede eller skadelige handlinger for at gøre kundens nøgler utilgængelige (f.eks. under dataudrømningsprocessen som en del af at forlade tjenesten).

       - I dette tilfælde bruges tilgængelighedsnøglen kun til systemhandlinger og ikke til brugerhandlinger, brugeranmodningen mislykkes, og brugeren modtager en fejlmeddelelse.

> [!IMPORTANT]
> Microsoft 365 tjenestekode har altid et gyldigt logontoken som begrundelse frem for kundedata for at levere værditil tilføjelse af skytjenester. Indtil tilgængelighedsnøglen er blevet slettet, kan den derfor bruges som reserve for handlinger, der er startet af eller internt i Exchange Online og Skype for Business f.eks. oprettelse af søgeindeks eller flytning af postkasser. Dette gælder både midlertidige FEJL og ANMODNINGER OM ADGANG NÆGTET til Azure Key Vault.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Udløsere til SharePoint Online-, OneDrive for Business- og Teams filer

For SharePoint Online-, OneDrive for Business- og Teams-filer bruges tilgængelighedsnøglen ALDRIG uden for genoprettelsesfunktionaliteten, og kunder skal udtrykkeligt instruere Microsoft i at starte brugen af tilgængelighedsnøglen under et genoprettelsesscenarie.

## <a name="audit-logs-and-the-availability-key"></a>Overvågningslogfiler og tilgængelighedsnøglen

Automatiserede systemer i Microsoft 365 behandler alle data, efterhånden som de flyder gennem systemet for at levere skytjenester, f.eks. antivirus, e-discovery, forebyggelse af datatab og dataindeksering. Microsoft 365 genererer ikke kunde synlige logfiler for denne aktivitet. Desuden får Microsoft-medarbejdere ikke adgang til dine data som en del af disse normale systemhandlinger.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>Exchange Online og Skype for Business logføring af tilgængelighedsnøgler

Når Exchange Online og Skype for Business adgangsnøgle til at levere tjenester, udgiver Microsoft 365 kunde synlige logfiler, der er tilgængelige fra Security and Compliance Center. Der genereres en overvågningslogpost for handlingen tilgængelighedsnøgle, hver gang tjenesten bruger tilgængelighedsnøglen. En ny posttype kaldet "Kryptering af kundeservice" med aktivitetstypen "Fallback til tilgængelighedsnøgle" gør det muligt for [](./search-the-audit-log-in-security-and-compliance.md) administratorer at filtrere søgeresultaterne for den samlede overvågningslog for at få vist tilgængelighedsnøgleposter.

Logposter omfatter attributter som f.eks. dato, klokkeslæt, aktivitet, organisations-id og id for datakrypteringspolitik. Posten er tilgængelig som en del af Unified Audit Logs og er tilgængelig fra fanen Security & Compliance Center Audit Log Search.

![Søgning i overvågningslogfil for tilgængelighedsnøglehændelser](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online og Skype for Business for tilgængelighed bruger det fælles skema Office 365 [Management Activity med](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) tilføjede brugerdefinerede parametre: Politik-id, Versions-id for omfangsnøgle og Anmodnings-id.

![Tilgængelighedsnøgler, brugerdefinerede parametre](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>SharePoint online,OneDrive for Business og Teams af filers tilgængelighed

Registrering af tilgængelighedsnøgler er endnu ikke tilgængelig for disse tjenester. For SharePoint Online-, OneDrive for Business- Teams-filer aktiveres tilgængelighedsnøglen kun af Microsoft, når du har fået besked, med henblik på gendannelse. Derfor kender du allerede alle begivenheder, hvor tilgængelighedsnøglen bruges til disse tjenester.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Tilgængelighedsnøgle i kundenøglehierarkiet
  
Microsoft 365 bruger tilgængelighedsnøglen til at ombryde nøgleniveauet lavere i nøglehierarkiet, der er fastlagt til kryptering af kundeservice. Der findes forskellige nøglehierarkier mellem tjenester. Nøglealgoritmer varierer også mellem tilgængelighedsnøgler og andre nøgler i hierarkiet for hver gældende tjeneste. Algoritmerne for tilgængelighedsnøgler, der bruges af de forskellige tjenester, er som følger:

- De Exchange Online og Skype for Business bruger AES-256.

- Filerne SharePoint online, OneDrive for Business og Teams bruger RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Krypteringskryptering, der bruges til at kryptere nøgler for Exchange Online og Skype for Business

![Krypteringskryptering til Exchange Online kundenøgle](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Krypteringskryptering, der bruges til at kryptere nøgler for SharePoint Online og OneDrive for Business

![Krypteringskryptering til SharePoint Online-kundenøgle](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)