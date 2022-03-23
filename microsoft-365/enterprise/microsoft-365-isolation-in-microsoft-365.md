---
title: Isolation og adgangskontrol i Microsoft 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
description: 'Oversigt: En forklaring på isolation og adgangskontrol i de forskellige programmer Microsoft 365.'
ms.openlocfilehash: 65845a8d6c8e6be578e997fa1455aa280c787897
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591586"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Isolation og adgangskontrol i Microsoft 365

Azure Active Directory (Azure AD) og Microsoft 365 bruger en meget kompleks datamodel, der indeholder hundredvis af tjenester, hundredvis af enheder, tusindvis af relationer og titusindvis af attributter. På et højt niveau er Azure AD og tjenestemapperne beholdere for lejere og modtagere synkroniseret ved hjælp af tilstandsbaserede replikeringsprotokoller. Ud over de mappeoplysninger, der opbevares i Azure AD, har hver af tjenestens arbejdsbelastninger deres egen infrastruktur til adresselistetjenester.
 
![Microsoft 365 synkronisering af lejerdata.](../media/office-365-isolation-tenant-data-sync.png)

I denne model findes der ingen enkelt kilde til katalogdata. Specifikke systemer ejer individuelle datastykker, men intet enkelt system indeholder alle dataene. Microsoft 365-tjenesterne i forbindelse med Azure AD i denne datamodel. Azure AD er "sandhedssystemet" for delte data, som typisk er små og statiske data, der bruges af hver enkelt tjeneste. Den organisationsnetværksmodel, der bruges i Microsoft 365 og Azure AD, giver den delte visning af dataene.

Microsoft 365 anvender både fysisk lager og Azure-skylager. Exchange Online (herunder Exchange Online Protection) og Skype for Business bruge deres egen lagerplads til kundedata. SharePoint Online anvender både SQL Server lagerplads og Azure Storage og dermed behov for ekstra isolation af kundedata på lagerniveau.

## <a name="exchange-online"></a>Exchange Online

Exchange Online gemmer kundedata i postkasser. Postkasser er hostet i Extensible Storage Engine-databaser (ESE), der kaldes postkassedatabaser. Dette omfatter brugerpostkasser, sammenkædede postkasser, delte postkasser og postkasser i offentlige mapper. Brugerpostkasser indeholder gemte Skype for Business, f.eks. samtaleoversigter.

Brugerpostkassens indhold omfatter:

- Mails og vedhæftede filer i mails
- Kalenderoplysninger og oplysninger om ledig/optaget tid
- Kontaktpersoner
- Opgaver
- Bemærkninger
- Grupper
- Afledningsdata

Hver postkassedatabase inden for Exchange Online indeholder postkasser fra flere lejere. En godkendelseskode sikrer hver postkasse, herunder inden for et leje. Som standard er det kun den tildelte bruger, der har adgang til en postkasse. Adgangskontrollisten (ACL), der sikrer en postkasse, indeholder en identitet, der er godkendt af Azure AD på lejerniveau. Postkasserne for hver lejer er begrænset til identiteter, der er godkendt af lejerens godkendelsesudbyder, hvilket kun omfatter brugere fra den pågældende lejer. Indhold i lejer A kan på ingen måde hentes af brugere i lejer B, medmindre de udtrykkeligt er godkendt af lejer A.

## <a name="skype-for-business"></a>Skype for Business

Skype for Business gemmer data forskellige steder:

- Bruger- og kontooplysninger, som omfatter forbindelsesslutpunkter, lejer-id'er, opkaldsplaner, roamingindstillinger, tilstedeværelsestilstand, lister over kontakter osv., gemmes på Skype for Business Active Directory-servere og på forskellige Skype for Business-databaseservere. Lister over kontakter gemmes i brugerens Exchange Online-postkasse, hvis brugeren er aktiveret for begge produkter, eller på Skype for Business-servere, hvis brugeren ikke er. Skype for Business databaseservere er ikke partitioneret pr. lejer, men dataisolation af flere arkitekturer gennemtvinges via rollebaseret adgangskontrol (RBAC).
- Mødeindhold og overførte data gemmes på DFS-shares (Distributed File System). Dette indhold kan også arkiveres i en Exchange Online hvis det er aktiveret. DFS-shares er ikke partitioneret pr. lejer. indholdet er sikret med ACL'er, og flere lejemål håndhæves via RBAC.
- Poster med opkaldsdetaljer, som er aktivitetsoversigten, f.eks. opkaldsoversigt, chatsessioner, programdeling, chatoversigt osv., kan også gemmes i Exchange Online, men de fleste poster med opkaldsdetaljer gemmes midlertidigt på CDR-servere (Call Detail Record). Indhold er ikke partitioneret pr. lejer, men flere lejere håndhæves via RBAC.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online har flere uafhængige mekanismer, der giver dataisolation. Den gemmer objekter som abstrakt kode i programdatabaser. Når en bruger f.eks. overfører en fil til SharePoint Online, er filen disassembleret, oversat til programkode og gemt i flere tabeller på tværs af flere databaser.

Hvis en bruger kan få direkte adgang til den lagerplads, der indeholder dataene, er indholdet ikke fortolket for et mennesker eller andre systemer end SharePoint Online. Disse mekanismer omfatter sikkerhedsadgangskontrol og egenskaber. Alle SharePoint Online-ressourcer er sikret af godkendelseskoden og RBAC-politikken, herunder inden for et leje. Adgangskontrollisten (ACL), der sikrer, at en ressource indeholder en identitet, der er godkendt på lejerniveau. SharePoint Onlinedata for en lejer er begrænset til identiteter, der er godkendt af godkendelsesudbyderen for lejeren.

Ud over ACL'er er en egenskab på lejerniveau, der angiver godkendelsesudbyderen (som er den lejerspecifikke Azure AD), skrevet én gang og kan ikke ændres, når den er angivet. Når godkendelsesudbyderens lejeregenskab er blevet angivet for en lejer, kan den ikke ændres ved hjælp af nogen API'er, der er eksponeret for en lejer.

Der bruges *et entydigt* Abonnements-id for hver lejer. Alle kundewebsteder ejes af en lejer og tildeles et *Abonnement-id, der* er entydigt for lejeren. Egenskaben *SubscriptionId* på et websted skrives én gang og er permanent. Når det er tildelt en lejer, kan et websted ikke flyttes til en anden lejer. *Abonnements-id'et* er nøglen, der bruges til at oprette sikkerhedsområdet for godkendelsesudbyderen og er knyttet til lejeren.

SharePoint Online bruger SQL Server og Azure Storage til lagring af indholdsmetadata. Partitionsnøglen for indholdslageret er *SiteId* i SQL. Når du kører en SQL, bruger SharePoint Online et Websteds-id, der  er bekræftet som en del af en kontrol af *abonnements-id på lejerniveau*.

SharePoint Online gemmer krypteret filindhold i Microsoft Azure blobs. Hver SharePoint Online-farm har sin egen Microsoft Azure-konto, og alle blobs, der er gemt i Azure, krypteres individuelt med en nøgle, der er gemt i SQL indholdslager. Den krypteringsnøgle, der er beskyttet i kode af godkendelseslaget og ikke er eksponeret direkte for slutbrugeren. SharePoint Online har realtidsovervågning til at registrere, når en HTTP-anmodning læser eller skriver data for mere end én lejer. *Anmodningsidentiteten SubscriptionId* registreres i den *tilgåede ressources SubscriptionId*. Anmodninger om at få adgang til ressourcer fra mere end én lejer bør aldrig ske af slutbrugere. Serviceanmodninger i et miljø med flere lejere er den eneste undtagelse. For eksempel trækker søge crawleren indholdsændringer for en hel database på én gang. Dette omfatter som regel forespørgsler om websteder med mere end én lejer i en enkelt serviceanmodning, som udføres af effektivitetsmæssige årsager.

## <a name="teams"></a>Teams

Dine Teams gemmes forskelligt, afhængigt af indholdstypen. 

Se ignite [breakout-sessionen om Microsoft Teams arkitektur](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071) for at få en dybdegående diskussion.

### <a name="core-teams-customer-data"></a>Kerne Teams kundedata

Hvis din lejer er klargjort i Australien, Canada, DEN Europæiske Union, Frankrig, Indien, Japan, Sydafrika, Sydkorea, Schweiz (som omfatter Liechtenstein), De Forenede Arabiske Emirater, Storbritannien eller USA, gemmer Microsoft kun følgende kundedata inden for denne placering:

- Teams chats, team- og kanalsamtaler, billeder, voicemail-beskeder og kontakter.
- SharePoint onlinewebstedsindhold og de filer, der er gemt på webstedet.
- Filer, der er OneDrive til arbejde eller skole.

#### <a name="chat-channel-messages-team-structure"></a>Chat, kanalmeddelelser, teamstruktur

Alle teams i Teams understøttes af en Microsoft 365-gruppe og dens SharePoint og Exchange postkasse. Private chats (herunder gruppechats), meddelelser, der sendes som en del af en samtale i en kanal, og strukturen i teams og kanaler gemmes i en chattjeneste, der kører i Azure. Dataene gemmes også i en skjult mappe i bruger- og gruppepostkasser for at aktivere funktioner til beskyttelse af oplysninger.

#### <a name="voicemail-and-contacts"></a>Telefonsvarer og kontakter

Voicemails gemmes i Exchange. Kontakter gemmes i Exchange skybaseret datalager. Exchange og det Exchange skybaserede lager giver allerede dataopbevaring i hvert af de verdensomspændende datacenters geos. For alle teams gemmes voicemail og kontakter i landet for Australien, Canada, Frankrig, Indien, Japan, De Forenede Arabiske Emirater, Storbritannien, Sydafrika, Sydkorea, Schweiz (som omfatter Liechtenstein) og USA. For alle andre lande gemmes filer i USA, Europa eller Asia-Pacific baseret på lejerens affinitet.

#### <a name="images-and-media"></a>Billeder og medier

Medier, der bruges i chatsamtaler (med undtagelse af Giphy GIF-filer, der ikke er gemt, men er et referencelink til den oprindelige URL-adresse til Giphy-tjenesten, Giphy er en tjeneste, der ikke er Microsoft) gemmes i en Azure-baseret medietjeneste, der er installeret på de samme placeringer som chattjenesten.

#### <a name="files"></a>Filer

Filer (herunder OneNote og Wiki), som nogen deler i en kanal, gemmes i teamets SharePoint websted. Filer, der deles i en privat chat eller i en chat under et møde eller et opkald, uploades og gemmes i OneDrive for den bruger, der deler filen. Exchange, SharePoint og OneDrive allerede dataopbevaring i hvert af de verdensomspændende datacenters geos. Så for eksisterende kunder er alle filer, OneNote-notesbøger, Teams wiki-indhold og postkasser, som er en del af Teams-oplevelsen, allerede gemt på placeringen baseret på din lejers affinitet. Filer gemmes i landet for Australien, Canada, Frankrig, Tyskland, Indien, Japan, De Forenede Arabiske Emirater, Storbritannien, Sydafrika, Sydkorea og Schweiz (som omfatter Liechtenstein). For alle andre lande gemmes filer i USA, Europa eller Asien/Stillehavsområdet baseret på lejerens affinitet.
