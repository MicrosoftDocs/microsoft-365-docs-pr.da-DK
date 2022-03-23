---
title: SharePoint overflytningsmuligheder for 2007, som du bør overveje
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Denne artikel indeholder oplysninger til brugere, der SharePoint Server 2007, for at hjælpe dem med at planlægge deres opgradering.
ms.openlocfilehash: 9c1c4c90443b632b490ac7a510394f367f688fca
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63589768"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint overflytningsmuligheder for 2007, som du bør overveje

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Supporten til Microsoft SharePoint 2007 SharePoint Server 2007 er udløbet. Nu er det tid til at opgradere! Denne artikel indeholder oplysninger om dine overførselsmuligheder.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Almindelige opgraderingsstrategier for SharePoint

Der er flere metoder til at opgradere et SharePoint Server-miljø. Hvis du har en Microsoft Office SharePoint Server 2007-farm, er her nogle eksempler på opgraderingsmetoder:
  
- Database vedhæft
    
- Side om side-opgradering
    
- Opgradering på stedet
    
- Hybrid opgradering (direkte med framonterede databaser /separat databaseatisering)
    
- SharePoint (opret forbindelse online til lokale SharePoint)
    
- Manuel flytning af data mellem grupper af websteder eller biblioteker
    
- FastTrack opgraderingsguiden til Microsoft 365 ([SharePoint Online-installationsrådgiver](https://aka.ms/spoguidance))
    
- Overførsels-API til SharePoint Online (SPO) i Microsoft 365
    
Hvad fungerer bedst for dig?
  
Dit kendskab til, hvad din farm gør og bruges til, er en taktisk fordel, når du skal opgradere. Den måde, folk bruger farmen SharePoint, kan hjælpe dig med at vælge mellem dine muligheder.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 har også en gradvis opgradering, der ikke behandles her. Hvis du vil se en liste over trinspecifikke opgraderingsartikler, [skal SharePoint end of support roadmap for Server 2007](sharepoint-2007-end-of-support.md). 
  
Husk at kontrollere [Produktlivscyklus](https://support.microsoft.com/lifecycle/search) og Systemkrav for den version SharePoint du opgraderer til. På denne måde kan du være opmærksom på, hvornår den næste opgradering er nødvendig (hvis du f.eks. holder markøren over et ældre produkt som f.eks. SharePoint Server 2010 for at planlægge flere opgraderinger, skal du sørge for, at du kender slutdatoen for support), og at du skal være sikker på, at du har hardware, der understøtter din plan. 
  
Hvis du planlægger at overgå nogle eller alle dine SharePoint-websteder til Microsoft 365 i skyen, er det tid til at bogmærke et link til Microsoft 365- og [Office 365-tjenestebeskrivelserne](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Du skal bruge Tjenestebeskrivelserne for at få mere at vide om SharePoint Online-funktioner, og hvordan de kan være forskellige fra lokale SharePoint Server. Opgrader Microsoft Office SharePoint Server 2007-farme. Hvis din installation har websteder, der er ødelagte, kan du løse dem før opgraderingen.
  
## <a name="a-note-about-managing-risk"></a>En note om risikostyring

Metoder som f.eks. "side om side" er vigtige for opgraderingslogik. Når du opgraderer side om side, vedligeholder du din Microsoft Office SharePoint Server 2007-farm, men opbygger en farm med den næste version (SharePoint Server 2010) på ny hardware. Dette hjælper på tre måder:
  
1. Du har et sted, hvor du kan tage sikkerhedskopier af dine Microsoft Office SharePoint Server 2007-databaser for at opgradere dem separat ved hjælp af databasehæftninger.
    
2. Hvis du finder ud af, at kun nogle få kritiske dokumentbiblioteker og andre oplysninger bruges på din Microsoft Office SharePoint Server 2007-farm, kan du vælge manuelt at flytte data fra Microsoft Office SharePoint Server 2007 til SharePoint  Server 2010, eller tag kun bestemte websteder og websteder til den næste version (hvilket kan gøre dit arbejde nemmere).
    
3. Jo mindre du gør med Microsoft Office SharePoint Server 2007-serverfarmen, jo mere sikre er de data, som farmen indeholder under opgraderingen.
    
Metoder som In-Place opgradering fungerer direkte på din Microsoft Office SharePoint Server 2007-farm, hvilket giver dig færre nemme muligheder for at få en sti og starte forfra med dit uberørte miljø. Så meget som muligt kan du opbygge nogle sikkerhedsforanstaltninger (f.eks. tage og teste sikkerhedskopier af det oprindelige miljø). Hvis din Microsoft Office SharePoint Server 2007-farm f.eks. er virtuel og duplikeres med henblik på sikkerhedskopiering og gendannelse, skal du sikkerhedskopiere og gendanne de nyeste databaser før tjenestevinduet for opgraderingen. Når du ved, at du har mulighed for at gendanne sikkerhedskopier af databaser, giver det dig ikke blot en failsafe, men det kan også give dig ro i sindet.
  
> [!TIP]
> Dokumenter med bedste fremgangsmåder til [opgradering findes for Microsoft Office SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc261992(v=office.12)), [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc261992(v=office.14)), [SharePoint Server 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013) [og SharePoint Server 2016](/SharePoint/upgrade-and-update/best-practices-for-upgrade). Du kan også søge efter [Microsoft-partnere](https://partnercenter.microsoft.com/pcv/search), der har erfaring med opgraderinger eller Microsoft 365 migrering. 
  
## <a name="make-your-plan"></a>Planlæg din plan

Hvis du skal opgradere, skal du have en plan, og der findes ikke én enkelt størrelse i alle disse tilfælde. Din plan kan være helt enkel: "Opret et Microsoft 365-abonnement med SharePoint Online, registrer et domæne og omdiriger personer for at gemme deres filer der'. Og det er den måske ikke. Det er din beslutning, og det er op til dig og dine brugere, hvad de har brug for.
  
> [!NOTE]
> Det er risikabelt at køre på software, hvis livscyklus er udløbet. Der bliver ikke længere fejlrettelser til produkter, der ikke længere understøttes, når der findes problemer. Det betyder også, at hvis der opstår nye sikkerhedstrusler, så er der ingen sikkerhedsrettelser, fordi produkter med udløbet livscyklus ikke længere understøttes. Undgå denne situation! 
  
### <a name="first-know-your-farm"></a>Du skal først kende din farm

Når du opgraderer, skal din beslutningstagning baseres på, hvad din farm gør for din organisation. Hvilke behov opfylder den? Hvad er dens rolle? Hver farm i din virksomhed kan have forskellige roller. Nogle af dine SharePoint farme kan *være kritiske*, nogle kan være filarkiver – sikkert opbevaring. Eller hvis din farm udfylder mange roller på én gang, skal du muligvis vide, hvad grupper af websteder, websteder eller endda dokumentbiblioteker gør, eventuelle tilpasninger, og hvor vigtige de er. Det kan virke meget arbejde at analysere dine data på dette niveau, men det sparer tid og besvær at få styr på dit domæne, før du opgraderer eller overfører det. Når du kender alle de bevægelige dele og de vigtigste elementer, kan du også se, hvad du er vokset fra og kan efterlade. Denne viden kommer dig kun til gode fremover. 
  
Så hvad siger brugerne, er det vigtigste ved din SharePoint Serverfarm?
  
- Indbyggede SharePoint funktioner
    
- Den store data mængde (f.eks. et filarkiv)
    
- Tilgængelighed
    
- Vigtige apps, webdele eller dokumenter i farmen (missionskritisk farm)
    
- Overholdelsesstandarderne er opfyldt
    
- Tilpasninger
    
Hvis du kører noget vigtigt for din virksomhed fra din SharePoint-farm, kan du f.eks. sige, at den fungerer som et stort katalog med vigtige data om krav til klienttjeneste, du kan sætte et flueben ud for "Kritiske apps", men også "Tilgængelighed", dvs. din virksomhed ville blive påvirket, hvis du ikke kunne bruge SharePoint i et stykke tid. Du kan også markere "Tilpasninger", fordi de kritiske tjenester, som din farm tilbyder, er baseret på brugerdefineret kode, webstedsdefinitioner eller mange tilpasninger, der arbejder sammen.
  
Hvis SharePoint har opfyldt disse behov uden din deltagelse uden for at bruge den indbyggede software, og du generelt opdaterer den og udfører normal administration og vedligeholdelse, kan du have valgt "Indbygget SharePoint", hvilket også kan være årsagen til, at du sidder med en ældre version af SharePoint. Med andre ord gør den allerede, hvad du har brug for, og du har ikke haft behov for at opgradere indtil nu ved Microsoft Office SharePoint Server 2007 ophør af support.
  
Når du punktopstillinger disse ting, kan du oprette kriterier for din opgradering. Enhver opgradering skal med andre ord opfylde disse krav for at blive taget i betragtning. På den måde kan du udelukke metoder, der ikke aktuelt opfylder dine behov.
  
### <a name="a-simple-sample-plan"></a>En simpel eksempelplan

Der kan være behov for en bredere enighed blandt ledelsen og andre administratorer om, hvordan din SharePoint opgraderingen skal tage. SharePoint serveradministratorer samarbejder ofte med Microsoft SQL Server administratorer, arbejder med netværks- og sikkerhedsteams og meget mere. Hvor der er mange interessenter, kan det være nødvendigt at udarbejde en aftale for eller justere din opgraderings- og overførselsplan. Overfører du f.eks. data, så en del af din virksomhed bruger SharePoint Online i Microsoft 365, skal der sandsynligvis ske justering af ydeevnen eller testning inden for dit netværk. Berørte teams skal informeres på forhånd.
  
I mit enkle eksempel viser jeg en SharePoint administratorforslag og viser derefter planen, som alle interessenter er enige om. Du kan skabe klarhed ved at dokumentere jeres aftaler og beslutninger.
  
Planen starter efter en dybdegående analyse af en farm og forsøger at identificere farmens rolle, problemer punkter og andre vigtige oplysninger, der kan føre til at indsnævre visse opgraderingsmuligheder. Herefter kommer et opgraderingsforslag fra en SharePoint, og interessenter når til enighed om en handlingsplan.
  
Min 'vigtigste' punktliste:
  
- Tilgængelighed, funktioner indbygget i SharePoint og overholdelsesstandarder.
    
- De fleste af dataene findes på tre grupper af websteder med ét mødearbejdsområde, der bruges af et udviklingsteam, vigtigt og bruges hårdt i flere tidszoner verden over.
    
- Der er 17 andre websteder, der bruges bredt.
    
- To dokumentbiblioteker (mødearbejdsområde og dokumenter på roden af gruppen af websteder) er størst (over 8000 dokumenter hver). Vi har et stort antal arkiverede dokumenter og lister med regnearks vedhæftede filer.
    
- Der findes 14 lister over biblioteker med følsomme data, der SKAL bevares i overensstemmelse med reglerne.
    
- Vi SKAL have mulighed for at holde og e-Discovery, uanset hvor vi er.
    
- Nogle af disse data SKAL bevares lokalt på grund af InfoSec-regler.
    
 **Mine opgraderings- og overførselsvalg:**
  
| Ja | Nej |
|:-----|:-----|
|Opgrader databaser med databaseathæft  <br/> |Opgradering på stedet  <br/> |
|Opgrader med farme side om side  <br/> |Hybridopgradering  <br/> |
|Overførsels-API til SPO i Microsoft 365 (for personlige webstedsdata)  <br/> |SharePoint hybrid (ikke nødvendig endnu)  <br/> |
|Nogle manuelle dataoverførsel til SharePoint Online for vigtige data  <br/> |FastTrack vil opgradere til Microsoft 365  <br/> |
   
 **Min planforslag:**
  
Opgrader lokalt med versioner af SharePoint side om side, noget virtualiseret, så vi kan opgradere databaserne først. Gå fra SharePoint 2007 til SharePoint 2010. Administratorer og udviklere tester den resulterende farm. Brugerne tester den resulterende farm. Løs eventuelle problemer, der stopper slideshowet, i dette tidsrum. Du kan også side om side opgradere SharePoint 2010-databaser SharePoint 2013. Test. Brugertest/pilot. Løs eventuelle problemer, der stopper slideshowet, i dette tidsrum.
  
- Overvej, om en hybridsøgning i organisationsnetværket med SPO opfylder dine behov.
    
- Overvej [FastTrack,](https://fasttrack.microsoft.com) hvis du vil opgradere til SharePoint Online herfra. 
    
- Afgør, om der er nogen grupper af websteder, der kan aflastes til et Microsoft 365-abonnement. (Microsoft 365 opfylder mange [overholdelsesstandarder](/compliance/regulatory/offering-home). Microsoft 365 har [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) og kan gøre [ventende mails](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) via Overholdelsescenter). 
    
Ellers skal du fortsætte med en side om side-opgradering til SharePoint Server 2016.
  
> [!NOTE]
> Der foregår samtaler med andre interessenter, som opgraderingen afhænger af, i mellem anbefalinger fra administratorer, der planlægger opgraderingen og den faktiske proces. Eksempelvis tvinges administratorer af økonomiske hensyn til at ændre deres planer. Uanset hvad den endelige beslutning bliver, så bør du dokumentere, hvad den aftalebaserede plan er fremover. Den kan se sådan ud: 
  
 **Min handlingsplan:**
  
I det lokale miljø bruger vi et virtuelt miljø til at oprette SharePoint Server 2010 og 2013. SharePoint Server 2016 bliver bygget på ny hardware, der opfylder systemkravene for 2016. Vi vedhæfter databaser for at opgradere databaser fra SharePoint 2007 til alle versioner mellem den og SharePoint Server 2016. Kernetilpasninger genoprettes for og testes i SharePoint Server 2016-miljøet på nuværende tidspunkt, hvis oprindelige funktioner ikke allerede opfylder vores behov. Hvis det lykkes, vil vi have en lokal farm på ny hardware med opgraderede databaser og færre tilpasninger. Vi vedhæfter de opgraderede indholdsdatabaser til nye grupper af websteder i SharePoint Server 2013, tester, brugertest/pilotering og klipper derefter over til det nye SharePoint Server 2016-miljø til livebrug.
  
- Vi overvejer ikke federated Hybrid mellem SharePoint Server 2016 og SharePoint Online lige nu.
    
- Anslået 35 % af vores websteder kan forvandles til nye SPO-websteder med brugerdefinerede domæner eller ultimativt blive OneDrive for Business lagerplads. Leder du efter andre muligheder for at konvertere websteder eller dirigere nye websteder til SPO.
    
- Noget af denne del af overførslen vil være manuel, ved at trække og slippe OneDrive for Business personlige websteder og nogle af via overførsels-API.
    
Mere detaljerede trin eller et antal links til bestemte opgraderingsvejledninger skal følge en plan. MOSS 2007-computeren bør ikke afvikles, og virtuelle miljøer skal bevares for at undgå sammenligning; Opgraderingen er dog fuldført, når brugere omdirigeres til SharePoint Server 2016.
  
Ofte er de vigtigste faktorer ved valg af en metode de samlede omkostninger for opgraderingen og omkostninger i tid (du kan se mere om dette i artiklen SharePoint Migration Roadmap). Men hvis du planlægger forud, kan det være en stor fordel for dig at fastsætte forventninger, vælge klogeligt og indrame, hvordan succesen vil se ud.
  
## <a name="related-links"></a>Relaterede links

[Ressourcer, der kan hjælpe dig med at opgradere Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
  
[Microsofts livscykluspolitik og livscyklussøgning](https://support.microsoft.com/lifecycle)
  
[Søg efter Microsoft-partnere, der kan hjælpe med opgradering eller overførsel](https://partnercenter.microsoft.com/pcv/search)
