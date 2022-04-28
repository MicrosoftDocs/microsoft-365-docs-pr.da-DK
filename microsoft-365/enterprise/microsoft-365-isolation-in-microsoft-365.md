---
title: Isolation og Access Control i Microsoft 365
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: 'Resumé: En forklaring på isolation og adgangskontrol i de forskellige applikationer af Microsoft 365.'
ms.openlocfilehash: dbb5ceb8b0e1e4ef6bb80ba2c3c771fc6d6cac5b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099383"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Isolation og Access Control i Microsoft 365

Azure Active Directory (Azure AD) og Microsoft 365 bruge en meget kompleks datamodel, der indeholder titusindvis af tjenester, hundredvis af enheder, tusindvis af relationer og titusindvis af attributter. På et højt niveau er Azure AD og tjenestemapperne objektbeholdere for lejere og modtagere, der holdes synkroniseret ved hjælp af tilstandsbaserede replikeringsprotokoller. Ud over de katalogoplysninger, der findes i Azure AD, har hver af arbejdsbelastningerne for tjenesten deres egen infrastruktur for katalogtjenester.
 
![Microsoft 365 synkronisering af lejerdata.](../media/office-365-isolation-tenant-data-sync.png)

I denne model er der ingen enkelt kilde til katalogdata. Specifikke systemer ejer individuelle data, men intet enkelt system indeholder alle dataene. Microsoft 365-tjenester samarbejder med Azure AD i denne datamodel. Azure AD er "sandhedens system" for delte data, som typisk bruges af små og statiske data i alle tjenester. Den organisationsnetværksmodel, der bruges i Microsoft 365 og Azure AD, leverer den delte visning af dataene.

Microsoft 365 bruger både fysisk lager og Azure Cloud Storage. Exchange Online (herunder Exchange Online Protection) og Skype for Business bruge deres eget lager til kundedata. SharePoint Online bruger både SQL Server lager og Azure Storage og derfor behovet for ekstra isolation af kundedata på lagerniveau.

## <a name="exchange-online"></a>Exchange Online

Exchange Online gemmer kundedata i postkasser. Postkasser hostes i ESE-databaser (Extensible Storage Engine) kaldet postkassedatabaser. Dette omfatter brugerpostkasser, sammenkædede postkasser, delte postkasser og offentlige mappepostkasser. Brugerpostkasser omfatter gemt Skype for Business indhold, f.eks. samtaleoversigter.

Indholdet i brugerpostkassen omfatter:

- Mails og vedhæftede filer i mails
- Kalenderoplysninger og oplysninger om ledig/optaget tid
- Kontaktpersoner
- Opgaver
- Bemærkninger
- Grupper
- Data for inferens

Hver postkassedatabase i Exchange Online indeholder postkasser fra flere lejere. En godkendelseskode sikrer hver postkasse, herunder inden for en lejer. Som standard er det kun den tildelte bruger, der har adgang til en postkasse. Adgangskontrollisten (ACL), der sikrer en postkasse, indeholder en identitet, der er godkendt af Azure AD på lejerniveau. Postkasserne for hver lejer er begrænset til identiteter, der er godkendt i forhold til lejerens godkendelsesprovider, hvilket kun omfatter brugere fra den pågældende lejer. Indhold i lejer A kan på ingen måde hentes af brugere i lejer B, medmindre det udtrykkeligt er godkendt af lejer A.

## <a name="skype-for-business"></a>Skype for Business

Skype for Business gemmer data forskellige steder:

- Bruger- og kontooplysninger, som omfatter forbindelsesslutpunkter, lejer-id'er, opkaldsplaner, roamingindstillinger, tilstedeværelsestilstand, kontaktlister osv., gemmes på Skype for Business Active Directory-servere og på forskellige Skype for Business databaseservere. Lister over kontakter gemmes i brugerens Exchange Online postkasse, hvis brugeren er aktiveret for begge produkter eller på Skype for Business servere, hvis brugeren ikke er det. Skype for Business databaseservere er ikke partitioneret pr. lejer, men isolation af data med flere lejere gennemtvinges via rollebaseret adgangskontrol ( RBAC).
- Mødeindhold og overførte data gemmes på DFS-shares (Distributed File System). Dette indhold kan også arkiveres i Exchange Online, hvis det er aktiveret. DFS-shares er ikke partitioneret pr. lejer. indholdet sikres med ACL'er, og multileje gennemtvinges via RBAC.
- Poster med opkaldsoplysninger, som er aktivitetsoversigten, f.eks. opkaldsoversigt, chatsessioner, programdeling, chatoversigt osv., kan også gemmes i Exchange Online, men de fleste poster med oplysninger om opkald gemmes midlertidigt på CDR-servere (Call Detail Record). Indhold er ikke partitioneret pr. lejer, men flere lejere gennemtvinges via RBAC.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online har flere uafhængige mekanismer, der sikrer dataisolation. Den gemmer objekter som abstrakt kode i programdatabaser. Når en bruger f.eks. uploader en fil til SharePoint Online, opdeles filen, oversættes til programkode og gemmes i flere tabeller på tværs af flere databaser.

Hvis en bruger kan få direkte adgang til det lager, der indeholder dataene, kan indholdet ikke fortolkes af et menneske eller et andet system end SharePoint Online. Disse mekanismer omfatter sikkerhedsadgangskontrol og -egenskaber. Alle SharePoint Online-ressourcer sikres af godkendelseskoden og RBAC-politikken, herunder inden for en leje. Den adgangskontrolliste (ACL), der sikrer en ressource, indeholder en identitet, der er godkendt på lejerniveau. SharePoint Online-data for en lejer er begrænset til identiteter, der er godkendt af lejerens godkendelsesprovider.

Ud over ACL'erne skrives en egenskab på lejerniveau, der angiver godkendelsesprovideren (som er den lejerspecifikke Azure AD), én gang og kan ikke ændres, når den er angivet. Når lejeregenskaben for godkendelsesprovideren er angivet for en lejer, kan den ikke ændres ved hjælp af api'er, der vises for en lejer.

Der bruges et entydigt *SubscriptionId* for hver lejer. Alle kundewebsteder ejes af en lejer og tildeles et *SubscriptionId* , der er entydigt for lejeren. Egenskaben *SubscriptionId* på et websted skrives én gang og er permanent. Når et websted er tildelt en lejer, kan det ikke flyttes til en anden lejer. *SubscriptionId* er den nøgle, der bruges til at oprette sikkerhedsområdet for godkendelsesprovideren og er knyttet til lejeren.

SharePoint Online bruger SQL Server og Azure Storage til lagring af indholdsmetadata. Partitionsnøglen for indholdslageret er *SiteId* i SQL. Når du kører en SQL forespørgsel, bruger SharePoint Online et *SiteId*, der er bekræftet som en del af en *subscriptionId-kontrol* på lejerniveau.

SharePoint Online gemmer krypteret filindhold i Microsoft Azure blobs. Hver SharePoint Online-farm har sin egen Microsoft Azure konto, og alle de blobs, der er gemt i Azure, krypteres individuelt med en nøgle, der er gemt i SQL indholdslager. Krypteringsnøglen er beskyttet i kode af godkendelseslaget og vises ikke direkte for slutbrugeren. SharePoint Online har overvågning i realtid for at registrere, hvornår en HTTP-anmodning læser eller skriver data for mere end én lejer. *Anmodnings-id'et SubscriptionId* spores i forhold til *SubscriptionId* for den ressource, der er adgang til. Anmodninger om adgang til ressourcer med mere end én lejer bør aldrig ske af slutbrugere. Tjenesteanmodninger i et miljø med flere lejere er den eneste undtagelse. Søgecrawleren henter f.eks. indholdsændringer for en hel database på én gang. Dette omfatter normalt at forespørge på websteder med mere end én lejer i en enkelt serviceanmodning, hvilket sker af effektivitetshensyn.

## <a name="teams"></a>Teams

Dine Teams data gemmes forskelligt, afhængigt af indholdstypen. 

Se [Ignite-underdybdesessionen på Microsoft Teams arkitektur](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071) for at få en dybdegående diskussion.

### <a name="core-teams-customer-data"></a>Centrale Teams kundedata

Hvis din lejer er klargjort i Australien, Canada, DEN Europæiske Union, Frankrig, Tyskland, Indien, Japan, Sydafrika, Sydkorea, Schweiz (herunder Liechtenstein), De Forenede Arabiske Emirater, Storbritannien eller USA, gemmer Microsoft kun følgende kundedata inaktivt på denne placering:

- Teams chats, team- og kanalsamtaler, billeder, talebeskeder og kontakter.
- SharePoint onlinewebstedsindhold og de filer, der er gemt på det pågældende websted.
- Filer, der er uploadet til OneDrive til arbejde eller skole.

#### <a name="chat-channel-messages-team-structure"></a>Chat, kanalmeddelelser, teamstruktur

Alle team i Teams understøttes af en Microsoft 365 gruppe og dens SharePoint websted og Exchange postkasse. Private chats (herunder gruppechats), meddelelser, der sendes som en del af en samtale i en kanal, og strukturen af teams og kanaler gemmes i en chattjeneste, der kører i Azure. Dataene gemmes også i en skjult mappe i bruger- og gruppepostkasserne for at aktivere Information Protection funktioner.

#### <a name="voicemail-and-contacts"></a>Talebesked og kontakter

Talebeskeder gemmes i Exchange. Kontakter gemmes i Exchange-baseret clouddatalager. Exchange og det Exchange cloudlager leverer allerede dataopbevaring i hvert af de globale datacenter-geos. For alle teams gemmes voicemail og kontakter i landet for Australien, Canada, Frankrig, Tyskland, Indien, Japan, De Forenede Arabiske Emirater, Storbritannien, Sydafrika, Sydkorea, Schweiz (herunder Liechtenstein) og USA. For alle andre lande gemmes filer i USA, Europa eller Asia-Pacific placering baseret på lejertilhør.

#### <a name="images-and-media"></a>Billeder og medier

Medier, der bruges i chats (med undtagelse af Giphy GIFs, der ikke er gemt, men som er et referencelink til den oprindelige URL-adresse til Giphy-tjenesten, er en tjeneste, der ikke er fra Microsoft), gemmes i en Azure-baseret medietjeneste, der udrulles på de samme placeringer som chattjenesten.

#### <a name="files"></a>Filer

Filer (herunder OneNote og wiki), som nogen deler i en kanal, gemmes på teamets SharePoint websted. Filer, der deles i en privat chat eller en chat under et møde eller et opkald, uploades og gemmes i OneDrive for arbejds- eller skolekontoen for den bruger, der deler filen. Exchange, SharePoint og OneDrive allerede levere dataopbevaring i hvert af de globale datacenter-geos. Så for eksisterende kunder gemmes alle filer, OneNote notesbøger, Teams wikiindhold og postkasser, der er en del af Teams-oplevelsen, allerede på placeringen baseret på din lejers tilhørsforhold. Filer gemmes i landet for Australien, Canada, Frankrig, Tyskland, Indien, Japan, De Forenede Arabiske Emirater, Storbritannien, Sydafrika, Sydkorea og Schweiz (herunder Liechtenstein). For alle andre lande gemmes filer i USA, Europa eller Asien og Stillehavsområdet baseret på lejertilknytning.
