---
title: Få mere at vide om tilgængelighedsnøglen til kundenøglen
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
ms.openlocfilehash: 1fd80d23980957402ae7d5e79a91e57d28df38f9
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761831"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Få mere at vide om tilgængelighedsnøglen til kundenøglen

Tilgængelighedsnøglen er en rodnøgle, der genereres og klargøres automatisk, når du opretter en politik for kryptering af data. Microsoft 365 gemmer og beskytter tilgængelighedsnøglen. Tilgængelighedsnøglen er funktionelt som de to rodnøgler, du angiver til tjenestekryptering med kundenøgle. Tilgængelighedsnøglen ombryder nøglerne et lavere niveau i nøglehierarkiet. I modsætning til de nøgler, du angiver og administrerer i Azure Key Vault, kan du ikke få direkte adgang til tilgængelighedsnøglen. Microsoft 365 automatiserede tjenester administrerer tilgængelighedsnøglen programatisk. Disse tjenester starter automatiserede handlinger, der aldrig involverer direkte adgang til tilgængelighedsnøglen.

Det primære formål med tilgængelighedsnøglen er at levere genoprettelsesfunktionalitet fra det uventede tab af rodnøgler, som du administrerer. Tab kan skyldes dårlig ledelse eller ondsindet handling. Hvis du mister kontrollen over dine rodnøgler, skal du kontakte Microsoft Support, hvorefter Microsoft hjælper dig med genoprettelsesprocessen ved hjælp af tilgængelighedsnøglen. Du skal bruge tilgængelighedsnøglen til at overføre til en ny politik for datakryptering med nye rodnøgler, du klargør.

Storage og kontrol over tilgængelighedsnøglen er bevidst forskellig fra Azure Key Vault-nøgler af tre årsager:

- Tilgængelighedsnøglen giver en genoprettelsesfunktion med "glasskår", hvis kontrollen over begge Azure Key Vault-nøgler går tabt.
- Adskillelsen af logiske kontrolelementer og sikre lagerplaceringer giver dybdegående forsvar og beskytter mod tab af alle nøgler og dine data mod et enkelt angreb eller fejlpunkt.
- Tilgængelighedsnøglen giver mulighed for høj tilgængelighed, hvis Microsoft 365 tjenester ikke kan nå de nøgler, der hostes i Azure Key Vault på grund af midlertidige fejl. Denne regel gælder kun for Exchange Online og Skype for Business tjenestekryptering. SharePoint Online, OneDrive for Business og Teams filer bruger aldrig tilgængelighedsnøglen, medmindre du udtrykkeligt instruerer Microsoft i at starte gendannelsesprocessen.

Deling af ansvaret for at beskytte dine data ved hjælp af forskellige beskyttelser og processer til nøgleadministration reducerer i sidste ende risikoen for, at alle nøgler (og dermed dine data) mistes eller destrueres permanent. Microsoft giver dig enemyndighed over deaktivering eller ødelæggelse af tilgængelighedsnøglen, når du forlader tjenesten. Tilsigtet har ingen hos Microsoft adgang til tilgængelighedsnøglen: Den er kun tilgængelig med Microsoft 365 tjenestekode.

Se [Microsoft Center for sikkerhed og rettighedsadministration](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) for at få flere oplysninger om, hvordan vi sikrer nøgler.
  
## <a name="availability-key-uses"></a>Tilgængelighedsnøglebrug

Tilgængelighedsnøglen leverer genoprettelsesfunktion til scenarier, hvor en ekstern malefactor eller ondsindet insider stjæler kontrollen over din key vault, eller når utilsigtede dårlig ledelse resulterer i tab af rodnøgler. Denne genoprettelsesfunktion gælder for alle Microsoft 365 tjenester, der er kompatible med kundenøglen. De enkelte tjenester bruger tilgængelighedsnøglen forskelligt. Microsoft 365 bruger kun tilgængelighedsnøglen på de måder, der er beskrevet nedenfor.

### <a name="exchange-online-and-skype-for-business-uses"></a>Exchange Online og Skype for Business

Ud over genoprettelsesfunktionen kan Exchange Online og Skype for Business bruge tilgængelighedsnøglen til at sikre datatilgængelighed under midlertidige eller periodiske driftsproblemer, der er relateret til den tjeneste, der tilgår rodnøgler. Når tjenesten ikke kan få adgang til nogen af dine kundenøgler i Azure Key Vault på grund af midlertidige fejl, bruger tjenesten automatisk tilgængelighedsnøglen. Tjenesten går ALDRIG direkte til tilgængelighedsnøglen.

Automatiserede systemer i Exchange Online og Skype for Business kan bruge tilgængelighedsnøglen under midlertidige fejl til at understøtte automatiserede back end-tjenester som f.eks. antivirus, e-søgning, forebyggelse af datatab, flytning af postkasser og dataindeksering.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>SharePoint Online-, OneDrive for Business- og Teams-filer bruger

I forbindelse med SharePoint Online-, OneDrive for Business- og Teams-filer bruges tilgængelighedsnøglen ALDRIG uden for genoprettelsesfunktionen, og kunderne skal eksplicit instruere Microsoft i at starte brugen af tilgængelighedsnøglen i et genoprettelsesscenarie. Automatiserede tjenestehandlinger er udelukkende afhængige af dine kundenøgler i Azure Key Vault. Du kan finde detaljerede oplysninger om, hvordan nøglehierarkiet fungerer for disse tjenester, under [Sådan SharePoint Online, OneDrive for Business og Teams filer bruger tilgængelighedsnøglen](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Sikkerhed for tilgængelighedsnøgle

Microsoft deler ansvaret for databeskyttelse med dig ved at instantiere tilgængelighedsnøglen og træffe omfattende foranstaltninger for at beskytte den. Microsoft fremviser ikke direkte kontrol over tilgængelighedsnøglen for kunder. Du kan f.eks. kun rulle (rotere) de nøgler, du ejer i Azure Key Vault. Du kan få flere oplysninger under [Kast eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Tilgængelighedsnøglehemmelighedslagre

Microsoft beskytter tilgængelighedsnøgler i adgangskontrollerede interne hemmelige butikker som det kundeorienterede Azure-Key Vault. Vi implementerer adgangskontroller for at forhindre Microsoft-administratorer i at få direkte adgang til hemmelighederne i. Hemmelige Store handlinger, herunder nøglerotation og sletning, sker via automatiserede kommandoer, der aldrig involverer direkte adgang til tilgængelighedsnøglen. Handlinger til administration af hemmelige lagre er begrænset til bestemte teknikere og kræver rettighedseskalering via et internt værktøj, Lockbox. Rettighedseskalering kræver administratorgodkendelse og -begrundelse, før den tildeles. Lockbox sikrer, at adgang er tidsbundet med automatisk tilbagekaldelse af adgang, når tiden udløber, eller tekniker logger af.

**Exchange Online og Skype for Business** tilgængelighedsnøgler gemmes i et Exchange Online Active Directory-hemmeligt lager. Tilgængelighedsnøgler gemmes sikkert i lejerspecifikke objektbeholdere i Active Directory-domænecontrolleren. Denne sikre lagerplacering er separat og isoleret fra SharePoint Online, OneDrive for Business og Teams filhemmelighedslageret.

**SharePoint Online, OneDrive for Business og Teams filer** tilgængelighedsnøgler gemmes i et internt hemmeligt lager, der administreres af tjenesteteamet. Denne sikre, hemmelige lagertjeneste har front end-servere med programslutpunkter og et SQL Database som back end. Tilgængelighedsnøgler gemmes i SQL Database og ombrydes (krypteres) af krypteringsnøgler til hemmelige lagre, der bruger en kombination af AES-256 og HMAC til at kryptere inaktiv tilgængelighedsnøgle. Krypteringsnøglerne til det hemmelige lager gemmes i en logisk isoleret komponent af samme SQL Database og krypteres yderligere med RSA-2048-nøgler i certifikater, der administreres af Microsoft-nøglecenteret (CA). Disse certifikater gemmes på frontendservere for det hemmelige lager, der udfører handlinger mod databasen.

### <a name="defense-in-depth"></a>Dybdegående forsvar

Microsoft anvender en dybdegående strategi til forsvar for at forhindre, at ondsindede aktører påvirker fortroligheden, integriteten eller tilgængeligheden af kundedata, der er gemt i Microsoft Cloud. Der implementeres specifikke forebyggende og detektivkontroller for at beskytte det hemmelige lager og tilgængelighedsnøglen som en del af den overordnede sikkerhedsstrategi.

Microsoft 365 er udviklet til at forhindre misbrug af tilgængelighedsnøglen. Programlaget er den eneste metode, som nøgler, herunder tilgængelighedsnøglen, kan bruges til at kryptere og dekryptere data. Kun Microsoft 365 tjenestekode har mulighed for at fortolke og gennemgå nøglehierarkiet for krypterings- og dekrypteringsaktiviteter. Der findes en logisk isolation mellem lagringsplaceringerne for kundenøgler, tilgængelighedsnøgler, andre hierarkiske nøgler og kundedata. Denne isolation afhjælper risikoen for dataeksponering, hvis en eller flere placeringer kompromitteres. Hvert lag i hierarkiet har indbygget 24 x 7 funktioner til registrering af indtrængen for at beskytte data og gemte hemmeligheder.

Adgangskontrolelementer implementeres for at forhindre uautoriseret adgang til interne systemer, herunder nøglehemmelighedslagre for tilgængelighed. Microsoft-teknikere har ikke direkte adgang til de vigtige hemmelige butikker, der er tilgængelige. Du kan finde flere oplysninger om adgangskontrolelementer ved at gennemse [Administrative adgangskontrolelementer i Microsoft 365](/compliance/assurance/assurance-administrative-access-controls-overview).

Tekniske kontrolelementer forhindrer Microsoft-medarbejdere i at logge på tjenestekonti med mange rettigheder, som ellers kan bruges af hackere til at repræsentere Microsoft-tjenester. Disse kontrolelementer forhindrer f.eks. interaktivt logon.

Sikkerhedslogførings- og overvågningskontroller er en anden dybdegående beskyttelse, der implementeres, og som reducerer risikoen for at Microsoft-tjenester og dine data. Microsoft-tjenesteteams har installeret aktive overvågningsløsninger, der genererer beskeder og overvågningslogge. Alle tjenesteteams uploader deres logge til et centralt lager, hvor loggene aggregeres og behandles. Interne værktøjer undersøger automatisk poster for at bekræfte, at tjenester fungerer i en optimal, robust og sikker tilstand. Usædvanlig aktivitet er markeret til yderligere gennemgang.

Alle loghændelser, der angiver en potentiel overtrædelse af Microsofts sikkerhedspolitik, bliver straks gjort opmærksom på Microsofts sikkerhedsteams. Microsoft 365 sikkerhed har konfigureret beskeder til at registrere forsøgte adgang til tilgængelighedsnøglehemmelighedslagre. Der genereres også beskeder, hvis Microsoft-medarbejdere forsøger at logge interaktivt på tjenestekonti, hvilket er forbudt og beskyttet af adgangskontrol. Microsoft 365 sikkerhed registrerer og giver også beskeder om afvigelser fra den Microsoft 365 tjenestes normale grundlæggende handlinger. Malefactors, der forsøger at misbruge Microsoft 365 tjenester, udløser beskeder, der medfører, at lovovertræderen fjernes fra Microsofts cloudmiljø.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Brug tilgængelighedsnøglen til at genoprette efter nøgletab

Hvis du mister kontrollen over dine kundenøgler, giver tilgængelighedsnøglen dig mulighed for at gendanne og kryptere dine data.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Inddrivelsesprocedure for Exchange Online og Skype for Business

Hvis du mister kontrollen over dine kundenøgler, giver tilgængelighedsnøglen dig mulighed for at gendanne dine data og gøre dine påvirkede Microsoft 365 ressourcer online igen. Tilgængelighedsnøglen fortsætter med at beskytte dine data, mens du gendanner. På et højt niveau skal du oprette en ny dep og flytte påvirkede ressourcer til den nye politik for at komme helt ud af nøgletabet.

Hvis du vil kryptere dine data med nye kundenøgler, skal du oprette nye nøgler i Azure Key Vault, oprette en ny forhindring af datatab ved hjælp af de nye kundenøgler og derefter tildele den nye forhindring af datatab til de postkasser, der i øjeblikket er krypteret med det forrige forhindringstidspunkt, hvor nøglerne gik tabt eller blev kompromitteret.

Denne proces til genkryptering kan tage op til 72 timer. Dette er standardvarigheden, når du ændrer en forhindring af dataaf data.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Gendannelsesprocedure for SharePoint Online-, OneDrive for Business- og Teams-filer

I forbindelse med SharePoint Online-, OneDrive for Business- og Teams-filer bruges tilgængelighedsnøglen ALDRIG uden for genoprettelsesfunktionen. Du skal eksplicit instruere Microsoft i at starte brugen af tilgængelighedsnøglen under et genoprettelsesscenarie. Hvis du vil starte genoprettelsesprocessen, skal du kontakte Microsoft for at aktivere tilgængelighedsnøglen. Når tilgængelighedsnøglen er aktiveret, bruges den automatisk til at dekryptere dine data, så du kan kryptere dataene med en nyligt oprettet forhindring af dataafgang, der er knyttet til nye kundenøgler.  

Denne handling er proportional med antallet af websteder i din organisation. Når du ringer til Microsoft for at bruge tilgængelighedsnøglen, skal du være fuldt online inden for ca. fire timer.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Sådan Exchange Online og Skype for Business bruge tilgængelighedsnøglen

Når du opretter en dep med en kundenøgle, genererer Microsoft 365 en datakrypteringspolitiknøgle, der er knyttet til denne forhindring af datakryptering. Tjenesten krypterer nøglen til forhindring af datakørsel tre gange: én gang med hver kundenøgle og én gang med tilgængelighedsnøglen. Det er kun de krypterede versioner af nøglen til forhindring af datasupport, der gemmes, og en dekrypteringsnøgle kan kun dekrypteres med kundenøglerne eller tilgængelighedsnøglen. Dep-nøglen bruges derefter til at kryptere postkassenøgler, som krypterer individuelle postkasser.
  
Microsoft 365 følger denne proces for at dekryptere og levere data, når kunderne bruger tjenesten:
  
1. Dekrypter dekrypteringsnøglen ved hjælp af kundenøglen.

2. Brug den dekrypterede DEP-nøgle til at dekryptere en postkassenøgle.

3. Brug den dekrypterede postkassenøgle til at dekryptere selve postkassen, så du kan få adgang til dataene i postkassen.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Sådan bruger SharePoint Online-, OneDrive for Business- og Teams-filer tilgængelighedsnøglen

Arkitekturen og implementeringen af SharePoint Online og OneDrive for Business for nøglen til kundenøgle og tilgængelighed adskiller sig fra Exchange Online og Skype for Business.
  
Når en organisation flytter til kundeadministrerede nøgler, opretter Microsoft 365 en organisationsspecifik mellemliggende nøgle (TIK). Microsoft 365 krypterer TIK to gange, én gang med hver kundenøgle, og gemmer de to krypterede versioner af TIK. Det er kun de krypterede versioner af TIK, der gemmes, og en TIK kan kun dekrypteres med kundenøglerne. TIK bruges derefter til at kryptere webstedsnøgler, som derefter bruges til at kryptere blob-nøgler (også kaldet filsegmentnøgler). Afhængigt af filstørrelsen kan tjenesten opdele en fil i flere filsegmenter med hver sin entydige nøgle. Selve blobs (filsegmenter) krypteres med blobnøglerne og gemmes i Microsoft Azure Blob Storage-tjenesten.
  
Microsoft 365 følger denne proces for at dekryptere og levere kundefiler, når kunderne bruger tjenesten:

1. Dekrypter TIK ved hjælp af kundenøglen.

2. Brug den dekrypterede TIK til at dekryptere en webstedsnøgle.

3. Brug den dekrypterede webstedsnøgle til at dekryptere en blob-nøgle.

4. Brug den dekrypterede blobnøgle til at dekryptere blob'en.

Microsoft 365 dekrypterer en TIK ved at udstede to dekrypteringsanmodninger til Azure Key Vault med en lille forskydning. Den første, der afslutter, giver resultatet og annullerer den anden anmodning.
  
Hvis du mister adgangen til dine kundenøgler, krypterer Microsoft 365 også TIK med en tilgængelighedsnøgle og gemmer dette sammen med DEKS, der er krypteret med hver kundenøgle. Den TIK, der er krypteret med tilgængelighedsnøglen, bruges kun, når kunden ringer til Microsoft for at tilmelde genoprettelsesstien, når de har mistet adgang til deres nøgler, ondsindet eller ved et uheld.
  
Af hensyn til tilgængelighed og skalering cachelagres dekrypterede TIKs i en tidsbegrænset hukommelsescache. To timer, før en TIK-cache er indstillet til at udløbe, forsøger Microsoft 365 at dekryptere hver TIK. Dekryptering af TIKs forlænger cachens levetid. Hvis TIK-dekryptering mislykkes i lang tid, genererer Microsoft 365 en besked om at give teknisk besked før cachens udløb. Kun hvis kunden ringer til Microsoft, Microsoft 365 starte genoprettelseshandlingen, hvilket omfatter dekryptering af TIK med tilgængelighedsnøglen gemt i Microsofts hemmelige lager og onboarding af lejeren igen ved hjælp af den dekrypterede TIK og et nyt sæt kundeangivne Azure Key Vault-nøgler.
  
Fra i dag er Customer Key involveret i krypterings- og dekrypteringskæden for SharePoint Online-fildata, der er gemt i Azure blob Store, men ikke SharePoint onlinelisteelementer eller metadata, der er gemt i SQL Database. Microsoft 365 bruger ikke tilgængelighedsnøglen til Exchange Online, Skype for Business, SharePoint Online, OneDrive for Business og Teams filer ud over det ovenfor beskrevne tilfælde, hvilket er kundeinitieret. Menneskelig adgang til kundedata er beskyttet af Customer Lockbox.

## <a name="availability-key-triggers"></a>Udløsere for tilgængelighedsnøgle

Microsoft 365 udløser kun tilgængelighedsnøglen under bestemte omstændigheder. Disse omstændigheder er forskellige fra tjeneste til tjeneste.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Udløsere for Exchange Online og Skype for Business
  
1. Microsoft 365 læser den dep, som postkassen er tildelt, for at bestemme placeringen af de to kundenøgler i Azure Key Vault.

2. Microsoft 365 tilfældigt vælger en af de to kundenøgler fra forhindring af datakontrol og sender en anmodning til Azure Key Vault om at fjerne ombrudt nøglen til forhindring af datakontrol ved hjælp af kundenøglen.

3. Hvis anmodningen om at ombryde nøglen til forhindring af dataforbrug mislykkes ved hjælp af kundenøglen, sender Microsoft 365 endnu en anmodning til Azure Key Vault, og denne gang instrueres den i at bruge den alternative (anden) kundenøgle.

4. Hvis den anden anmodning om at fjerne nøglen til forhindring af datasikkerhed ved hjælp af kundenøglen mislykkes, undersøger Microsoft 365 resultaterne af begge anmodninger.

    - Hvis undersøgelsen afgør, at anmodningerne ikke returnerede en systemFEJL:

       - Microsoft 365 udløser tilgængelighedsnøglen for at dekryptere nøglen til forhindring af dataafgang.

       - Microsoft 365 bruger derefter nøglen til forhindring af dataadgang til at dekryptere postkassenøglen og fuldføre brugeranmodningen. 

       - I dette tilfælde kan Azure Key Vault enten ikke svare eller ikke nås på grund af en forbigående FEJL.

    - Hvis undersøgelsen afgør, at anmodningerne ikke returnerede ADGANG NÆGTET:

       - Det betyder, at der er foretaget forsætlige, utilsigtede eller skadelige handlinger for at gøre kundenøglerne utilgængelige (f.eks. under datarensningsprocessen som en del af at forlade tjenesten).

       - I dette tilfælde bruges tilgængelighedsnøglen kun til systemhandlinger og ikke til brugerhandlinger, brugeranmodningen mislykkes, og brugeren får vist en fejlmeddelelse.

> [!IMPORTANT]
> Microsoft 365 tjenestekode har altid et gyldigt logontoken til at begrunde kundedata for at levere værdiskabende cloudtjenester. Indtil tilgængelighedsnøglen er blevet slettet, kan den derfor bruges som reserve for handlinger, der er startet af eller intern i Exchange Online og Skype for Business, f.eks. oprettelse af søgeindeks eller flytning af postkasser. Dette gælder både for midlertidige FEJL og ANMODNINGER OM ADGANG NÆGTET til Azure Key Vault.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>Udløsere for SharePoint Online-, OneDrive for Business- og Teams-filer

I forbindelse med SharePoint Online-, OneDrive for Business- og Teams-filer bruges tilgængelighedsnøglen ALDRIG uden for genoprettelsesfunktionen, og kunderne skal eksplicit instruere Microsoft i at starte brugen af tilgængelighedsnøglen i et genoprettelsesscenarie.

## <a name="audit-logs-and-the-availability-key"></a>Overvågningslogge og tilgængelighedsnøglen

Automatiserede systemer i Microsoft 365 behandle alle data, efterhånden som de flyder gennem systemet for at levere cloudtjenester, f.eks. antivirus, e-registrering, forebyggelse af datatab og dataindeksering. Microsoft 365 genererer ikke kunde synlige logge for denne aktivitet. Derudover har Microsoft-medarbejdere ikke adgang til dine data som en del af disse normale systemhandlinger.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>logføring af nøgle for Exchange Online og Skype for Business tilgængelighed

Når Exchange Online og Skype for Business får adgang til tilgængelighedsnøgle til at levere service, udgiver Microsoft 365 de logfiler, der er synlige for kunder, og som er tilgængelige fra Security and Compliance Center. Der genereres en overvågningslogpost for tilgængelighedsnøglehandlingen, hver gang tjenesten bruger tilgængelighedsnøglen. En ny posttype med navnet "Customer Key Service Encryption" med aktivitetstypen "Fallback to Availability Key" gør det muligt for administratorer at filtrere søgeresultaterne for [Unified Audit Log](./search-the-audit-log-in-security-and-compliance.md) for at få vist nøgleposter for tilgængelighed.

Logposter indeholder attributter som f.eks. dato, klokkeslæt, aktivitet, organisations-id og datakrypteringspolitik-id. Posten er tilgængelig som en del af Unified Audit Logs og er tilgængelig via fanen Søgning i overvågningslog i Security & Compliance Center.

![Søgning i overvågningslog for tilgængelighedsnøglehændelser](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online og Skype for Business tilgængelighedsnøgleposter bruger det [fælles skema](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) for Office 365-administrationsaktivitet med tilføjede brugerdefinerede parametre: Politik-id, versions-id for områdenøgle og anmodnings-id.

![Brugerdefinerede parametre for tilgængelighedsnøgle](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>SharePoint Online, OneDrive for Business og Teams logfiler tilgængelighed nøglelogføring

Logføring af tilgængelighedsnøgle er endnu ikke tilgængelig for disse tjenester. I forbindelse med SharePoint Online-, OneDrive for Business- og Teams-filer aktiveres tilgængelighedsnøglen kun af Microsoft, når du får besked om det, til gendannelsesformål. Derfor kender du allerede alle de begivenheder, hvor tilgængelighedsnøglen bruges til disse tjenester.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Tilgængelighedsnøgle i hierarkiet Kundenøgle
  
Microsoft 365 bruger tilgængelighedsnøglen til at ombryde nøgleniveauet lavere i det nøglehierarki, der er oprettet til kryptering af tjenesten Customer Key. Der findes forskellige nøglehierarkier mellem tjenester. Nøglealgoritmer varierer også mellem tilgængelighedsnøgler og andre nøgler i hierarkiet for hver relevant tjeneste. De tilgængelighedsnøglealgoritmer, der bruges af de forskellige tjenester, er som følger:

- De Exchange Online og Skype for Business tilgængelighedsnøgler bruger AES-256.

- Tilgængelighedsnøglerne SharePoint Online, OneDrive for Business og Teams filer bruger RSA-2048.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Krypteringsciffer, der bruges til at kryptere nøgler til Exchange Online og Skype for Business

![Krypteringsciffer for Exchange Online kundenøgle](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>Krypteringsciffer, der bruges til at kryptere nøgler til SharePoint Online og OneDrive for Business

![Krypteringsciffer til SharePoint onlinekundenøgle](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)
