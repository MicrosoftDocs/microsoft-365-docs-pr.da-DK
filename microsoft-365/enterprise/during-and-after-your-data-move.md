---
title: Under og efter flytning af dine data
ms.author: andyber
author: andybergen
manager: laurawi
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
description: Datahandlinger er back-end-handlinger, der udføres, når Microsoft flytter tjenester og tilknyttede data for din lejer til et nyt datacenters geocenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1fcb62897f1feabe0ca8c447c51e61c7d752138c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591573"
---
# <a name="during-and-after-your-data-move"></a>Under og efter flytning af dine data

Databevægelser er en back-end-handling med minimal indvirkning for slutbrugere. Der kræves ingen handling, mens Microsoft flytter hver enkelt tjeneste og tilknyttede data for din lejer til et nyt datacenters geocenter. Dataoverførsel og validering sker i baggrunden på forhånd med minimal indvirkning for brugerne.
  
> [!NOTE]
> Flytninger sker på forskellige tidspunkter for hver tjeneste. Derfor får du vist de beskrevne reducerede funktioner for hver tjeneste på et andet tidspunkt. 
  
Watch the Microsoft 365 Message Center for confirmation when moves for each Exchange Online, SharePoint Online, and Teams chat service complete. Som vist i tabellen nedenfor kan det tage op til 24 måneder efter afslutningen af tilmeldingsperioden at fuldføre kernekundedata i hvile til det nye datacenters geo.   

| Kunder med tilmeldingsland i | Alle flytninger fuldført af |
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

Da det tager tid at flytte hver enkelt bruger til det nye datacenters geo for en enkelt lejer, vil nogle brugere stadig være i det gamle datacenter geo under flytningen, mens andre vil være i det nye datacenters geocenter. Det betyder, at nogle funktioner, der involverer adgang til flere postkasser, muligvis ikke fungerer fuldt ud i løbet af en periode med flytteprocessen, hvilket kan vare uger. Disse funktioner er beskrevet i de følgende afsnit.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Åbn "Delt mappe" i Outlook Web Access

Nogle brugere åbner en delt mailmappe fra en anden postkasse (som brugeren har læse- eller skrivetilladelser til) i Outlook Web Access ved hjælp af funktionen "Delt mappe". I følgende tabel beskrives det, hvordan adgang til delte mapper fungerer under flytning af en postkasse. Bemærk, at brugere med fulde tilladelser til en delt postkasse kan åbne postkassen ved hjælp Outlook Web Access under flytningen. 
  
| Konfiguration | Beskrivelse |
|:-----|:-----|
|Brugeren har postkassemappetilladelse til en anden postkasse  <br/> |Potentielt begrænset.  <br/> Hvis bruger A og Postkasse B ikke er i det samme geo under lejerens flytning, kan bruger A ikke åbne postkasse B's mappe i Outlook Web Access, hvis Bruger A kun har tilladelse til en bestemt mappe i Postkasse B.  <br/> Hvis du vil tilføje en delt mappe, skal du højreklikke på brugernavnet i venstre navigationspanel og vælge **Tilføj delt mappe**.  <br/> |
|Bruger med fuld postkassetilladelse til en anden postkasse  <br/> |Understøttes fuldt ud.  <br/> Hvis bruger A har "Fuld adgang"-tilladelse til postkasse B, kan bruger A klikke på den delte mappe i venstre navigationspanel i Outlook Web Access for at åbne et vindue, der viser Postkasse B.  En bruger kan åbne en delt postkasse Outlook Web Access under flytningen uden nogen negativ indvirkning. Begrænsningen gælder kun for deling på mappeniveau i en postkasse.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Når SharePoint Online flyttes, flyttes data for følgende tjenester også:
  
- OneDrive for Business
    
- Microsoft 365 videotjenester
    
- Office i en browser
    
- Microsoft 365 Apps for enterprise
    
- Visio Pro til Microsoft 365
    
Når vi er færdige med at flytte SharePoint Online-data, kan du muligvis se nogle af følgende effekter.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 videotjenester

- Flytning af data til video tager længere tid end flytningen for resten af dit indhold i SharePoint Online.
    
- Når videoen SharePoint onlineindhold er flyttet, vil der være en tidsramme, hvor videoer ikke kan afspilles.
    
- Vi fjerner de transkodede kopier fra det tidligere datacenter og omkoder dem igen i det nye datacenter.
    
### <a name="search"></a>Søg

I løbet af dine SharePoint Online-data overfører vi dit søgeindeks og dine søgeindstillinger til en ny placering. Indtil vi har fuldført **flytningen** af dine SharePoint Online-data, fortsætter vi med at betjene dine brugere fra indekset på den oprindelige placering. På den nye placering starter søgningen automatisk gennemsøgningen af dit indhold, når vi er færdige med at flytte dine SharePoint Online-data. Fra dette tidspunkt og fremover betjenes dine brugere fra det overførte indeks. Ændringer af dit indhold, der er foretaget efter overførslen, medtages ikke i det overførte indeks, før gennemsøgningen henter dem. De fleste kunder bemærker ikke, at resultaterne er mindre nye, lige efter vi er færdige med at flytte deres SharePoint Online-data, men nogle kunder kan opleve reduceret friskhed i de første 24-48 timer 
  
Følgende søgefunktioner påvirkes:
  
- Søgeresultater og søgekriterier webdele: Resultaterne omfatter ikke ændringer, der er foretaget efter overførslen, før gennemsøgningen henter dem. 
    
- Delve: Delve ikke ændringer, der er foretaget efter overførslen, før gennemsøgningen henter dem.
    
- Popularitets- og søgerapporter for webstedet: Tællere for Excel-rapporter på den nye placering omfatter kun overførte optællinger og optællinger fra brugsrapporter, der er kørt, efter vi har flyttet dine SharePoint Online-data. Alle optællinger fra den midlertidige periode går tabt og kan ikke gendannes. Denne periode er normalt et par dage. Nogle kunder kan opleve kortere eller længere tab.
    
- Videoportal: Vis optællinger og statistik for Videoportalen afhænger af statistikken for Excel-rapporter, så antallet af visninger og statistik for videoportalen går tabt i samme tidsperiode som for de Excel rapporter.
    
- eDiscovery: Elementer, der blev ændret under overførslen, vises ikke, før gennemsøgningen opfanger ændringerne.
    
- Data Loss Protection (DLP): Politikker håndhæves ikke på elementer, der ændres, indtil gennemsøgningen opfanger ændringerne.

Som en del af overførslen ændres standardområdet, og alt nyt indhold gemmes i det nye standardområde. Eksisterende indhold flyttes i baggrunden uden nogen indvirkning for dig i op til 90 dage efter den første ændring af SharePoint Online-dataplaceringen i Administration.

## <a name="microsoft-teams"></a>Microsoft Teams

### <a name="files-tab"></a>Fanen Filer

Når overførslen er fuldført, kan det tage ekstra tid (i op til syv sekunder) at indlæse fanen Filer fuldt ud, når brugeren først forsøger at bruge den. 

### <a name="read-only-period"></a>Skrivebeskyttet periode

Teams-chattjenester flytter hver tråd individuelt.  Tråden er låst i en skrivebeskyttet tilstand under flytningen, hvilket varer et par sekunder pr. tråd.  Tråde forbliver tilgængelige under overførslen.

## <a name="skype-for-business"></a>Skype for Business

Skype for Business-flytninger er ikke længere tilgængelige.  [Skype for Business Online vil udgå den](/lifecycle/announcements/skype-for-business-online-retirement) 31. juli 2021. Efter dette tidspunkt er tjenesten ikke længere tilgængelig. 
  
## <a name="related-topics"></a>Relaterede emner 
 
[Sådan anmoder du om, at dine data flyttes](request-your-data-move.md)
    
[Ofte stillede spørgsmål om flytning af data](data-move-faq.yml)
  
[Nye datacenter-geos til Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Azure-tjenester efter område](https://azure.microsoft.com/regions/)
