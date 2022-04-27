---
title: Under og efter flytningen af dine data
ms.author: andyber
author: andybergen
manager: scotv
ms.date: 09/22/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
ms.localizationpriority: medium
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
f1.keywords:
- NOCSH
description: Dataflytninger er back end-handlinger, der opstår, når Microsoft flytter tjenester og tilknyttede data for din lejer til et nyt datacenter geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e9b4a7e7be30920853318adf4015541b077b6cc1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099141"
---
# <a name="during-and-after-your-data-move"></a>Under og efter flytningen af dine data

Dataflytninger er en back end-handling, der har minimal indvirkning på slutbrugerne. Der kræves ingen handling, mens Microsoft flytter hver tjeneste og tilknyttede data for din lejer til et nyt datacenter geo. Dataoverførsel og -validering sker i baggrunden på forhånd med minimal indvirkning på brugerne.
  
> [!NOTE]
> Flytninger sker på forskellige tidspunkter for hver tjeneste. Derfor får du vist den beskrevne reducerede funktionalitet for hver tjeneste på et andet tidspunkt. 
  
Se Microsoft 365 Meddelelsescenter for at få bekræftelse, når flytningen for hver af Exchange Online, SharePoint Online og Teams chattjeneste er fuldført. Som vist i nedenstående tabel kan det tage op til 24 måneder efter afslutningen af tilmeldingsperioden at fuldføre centrale kundedata som inaktive flytninger til det nye datacenter geo.   

| Kunder med lande, der tilmelder sig | Alle flytninger er fuldført af |
|:-----|:-----|
|Australien, New Zealand, Fiji  <br/> |1. juli 2022  <br/> |
|Japan  <br/> |1. juli 2022  <br/> |
|Indien  <br/> |1. juli 2022  <br/> |
|Canada  <br/> |1. juli 2022  <br/> |
|Sydkorea  <br/> |1. juli 2022  <br/> |
|Storbritannien  <br/> |1. juli 2022  <br/> |
|Frankrig  <br/> |1. juli 2022  <br/> |
|De Forenede Arabiske Emirater  <br/> |1. juli 2022  <br/> |
|Sydafrika  <br/> |1. juli 2022  <br/> |
|Schweiz, Liechtenstein  <br/> |1. juli 2022  <br/> |
|Norge  <br/> |1. november 2022  <br/> |
|Tyskland  <br/> |1. maj 2023  <br/> |
|Brasilien  <br/> |1. juni 2023  <br/> |
|Sverige  <br/> |1. juni 2024  <br/> |

## <a name="exchange-online"></a>Exchange Online

Da det tager tid at flytte hver bruger til det nye datacenter geo for en enkelt lejer, vil nogle brugere stadig være i det gamle datacenter geo under flytningen, mens andre vil være i det nye datacenter geo. Det betyder, at nogle funktioner, der involverer adgang til flere postkasser, muligvis ikke fungerer fuldt ud i løbet af flytteprocessen, hvilket kan vare uger. Disse funktioner er beskrevet i følgende afsnit.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Åbn "Delt mappe" i Outlook Web Access

Nogle brugere åbner en delt mailmappe fra en anden postkasse (som brugeren har læse- eller skriverettigheder til) i Outlook Web Access ved hjælp af funktionen "Delt mappe". I følgende tabel beskrives det, hvordan adgang til delte mapper fungerer under flytning af en postkasse. Bemærk, at brugere med fulde tilladelser til en delt postkasse kan åbne postkassen ved hjælp af Outlook Web Access under flytningen. 
  
| Konfiguration | Beskrivelse |
|:-----|:-----|
|Brugeren har tilladelse til at oprette en postkassemappe til en anden postkasse  <br/> |Potentielt begrænset.  <br/> Hvis Bruger A og Postkasse B ikke er i samme geografiske område under flytningen af lejeren, kan Bruger A ikke åbne postkasse B's mappe i Outlook Web Access, hvis bruger A kun har tilladelse til en bestemt mappe i Postkasse B.  <br/> Hvis du vil tilføje en delt mappe, skal du højreklikke på brugernavnet i venstre navigationspanel og vælge **Tilføj delt mappe**.  <br/> |
|Bruger med tilladelsen Fuld postkasse til en anden postkasse  <br/> |Understøttes fuldt ud.  <br/> Hvis Bruger A har tilladelsen "Fuld adgang" til Postkasse B, kan bruger A klikke på den delte mappe i navigationspanelet til venstre i Outlook Web Access for at åbne et vindue, der viser Postkasse B.  En bruger kan åbne en delt postkasse ved hjælp af Outlook Web Access under flytningen uden nogen negativ indvirkning. Begrænsningen gælder kun for deling på mappeniveau i en postkasse.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Når SharePoint Online flyttes, flyttes data for følgende tjenester også:
  
- OneDrive for Business
    
- Microsoft 365 videotjenester
    
- Office i en browser
    
- Microsoft 365 Apps for enterprise
    
- Visio Pro til Microsoft 365
    
Når vi er færdig med at flytte dine SharePoint Online-data, kan du se nogle af følgende effekter.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 videotjenester

- Dataflytningen for video tager længere tid end flytningerne for resten af dit indhold i SharePoint Online.
    
- Når SharePoint Online-indhold er flyttet, vil der være en tidsramme, når videoer ikke kan afspilles.
    
- Vi fjerner de transkodede kopier fra det forrige datacenter og omkodning af dem igen i det nye datacenter.
    
### <a name="search"></a>Søg

Når du flytter dine SharePoint Online-data, overfører vi søgeindekset og søgeindstillingerne til en ny placering. Indtil vi har **fuldført** flytningen af dine SharePoint Online-data, servicerer vi fortsat dine brugere fra indekset på den oprindelige placering. På den nye placering starter søgningen automatisk gennemsøgningen af dit indhold, når vi er færdig med at flytte dine SharePoint Online-data. Fra dette tidspunkt og frem betjener vi dine brugere fra det migrerede indeks. Ændringer af dit indhold, der opstod efter migreringen, medtages ikke i det migrerede indeks, før gennemsøgningen henter dem. De fleste kunder bemærker ikke, at resultaterne er mindre friske, lige efter at vi er færdige med at flytte deres SharePoint Online-data, men nogle kunder oplever muligvis reduceret friskhed i løbet af de første 24-48 timer 
  
Følgende søgefunktioner påvirkes:
  
- Søgeresultater og webdele: Resultaterne omfatter ikke ændringer, der opstod efter migreringen, før gennemsøgningen henter dem. 
    
- Delve: Delve indeholder ikke ændringer, der opstod efter migreringen, før gennemsøgningen henter dem.
    
- Popularitets- og søgerapporter for webstedet: Antallet af Excel rapporter på den nye placering omfatter kun migrerede antal og antal fra forbrugsrapporter, der er kørt, efter at vi har flyttet dine SharePoint Online-data. Alle optællinger fra overgangsperioden går tabt og kan ikke gendannes. Denne periode er typisk et par dage. Nogle kunder kan opleve kortere eller længere tab.
    
- Videoportal: Visning af antal og statistik for videoportalen afhænger af statistikkerne for Excel rapporter, så visningsantal og statistikker for videoportalen går tabt i samme tidsperiode som for de Excel rapporter.
    
- eDiscovery: Elementer, der blev ændret under migreringen, vises ikke, før gennemsøgningen registrerer ændringerne.
    
- DLP (Data Loss Protection): Politikker gennemtvinges ikke for elementer, der ændres, før gennemsøgningen registrerer ændringerne.

Som en del af migreringen ændres standardområdet, og alt nyt indhold gemmes som inaktivt i det nye standardområde. Eksisterende indhold flyttes i baggrunden uden indvirkning for dig i op til 90 dage efter den første ændring af dataplaceringen SharePoint Online i Administration.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Fanen Filer

Når overførslen er fuldført, kan fanen Filer tage yderligere tid (op til 7 sekunder) til fuld indlæsning, når brugeren forsøger at bruge den første gang. 

### <a name="read-only-period"></a>Skrivebeskyttet periode

Teams chattjenester flyttes hver tråd individuelt.  Tråden er låst i skrivebeskyttet tilstand under flytningen, hvilket varer et par sekunder pr. tråd.  Tråde forbliver tilgængelige under migreringen.

## <a name="skype-for-business"></a>Skype for Business

Skype for Business flytninger er ikke længere tilgængelige.  [Skype for Business Online udgår](/lifecycle/announcements/skype-for-business-online-retirement) den 31. juli 2021. Efter dette tidspunkt er tjenesten ikke længere tilgængelig. 
  
## <a name="related-topics"></a>Relaterede emner 
 
[Sådan anmoder du om flytning af dine data](request-your-data-move.md)
    
[Generelle ofte stillede spørgsmål om dataflytning](data-move-faq.yml)
  
[Nyt datacenter-geos til Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Azure-tjenester efter område](https://azure.microsoft.com/regions/)
