---
title: SharePoint migreringsmuligheder i 2007, som du skal overveje
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Denne artikel indeholder oplysninger til brugere, der bruger SharePoint Server 2007, for at hjælpe dem med at planlægge deres opgradering.
ms.openlocfilehash: 044bfce8ea64233950fa291c72896f36531d206e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090745"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>SharePoint migreringsmuligheder i 2007, som du skal overveje

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Support til Microsoft SharePoint 2007 og SharePoint Server 2007 er ophørt. Det er tid til at opgradere! Denne artikel indeholder oplysninger om dine overførselsmuligheder.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Almindelige opgraderingsstrategier for SharePoint

Der er flere metoder til opgradering af et SharePoint Server-miljø. Hvis du har en Microsoft Office SharePoint Server 2007-farm, er her nogle eksempler på opgraderingsmetoderne:
  
- Vedhæft database
    
- Side om side-opgradering
    
- Lokal opgradering
    
- Hybridopgradering (på stedet med fjernede databaser/separat vedhæftning af database)
    
- SharePoint hybrider (opret forbindelse online til SharePoint i det lokale miljø)
    
- Flyt data manuelt mellem grupper af websteder eller biblioteker
    
- FastTrack guideopgradering til Microsoft 365 ([SharePoint Online Deployment Advisor](https://aka.ms/spoguidance))
    
- Overførsels-API til SharePoint Online (SPO) i Microsoft 365
    
Hvad fungerer bedst for dig?
  
Din viden om, hvad din gård gør og bruges til, er en taktisk styrke, når det kommer til opgradering. Den måde, folk bruger SharePoint Farm på, hjælper dig med at vælge mellem dine muligheder.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 har også en gradvis opgradering, der ikke er beskrevet her. Hvis du vil se en liste over trinvise opgraderingsartikler, skal du se [køreplanen for ophør af support til SharePoint Server 2007](sharepoint-2007-end-of-support.md). 
  
Husk at kontrollere [produktlivscyklussen](https://support.microsoft.com/lifecycle/search) og systemkravene for den version af SharePoint, du opgraderer til. Dette er tilfældet, så du er opmærksom på, hvornår den næste opgradering er nødvendig (hvis du f.eks. sætter et ældre produkt på pause, f.eks. SharePoint Server 2010 for at planlægge flere opgraderinger, skal du være sikker på, at du kender slutdatoen for support), og at du er sikker på, at du har hardware, der understøtter din plan. 
  
Hvis du planlægger at overføre nogle eller alle dine SharePoint websteder til Microsoft 365 i cloudmiljøet, er dette et tidspunkt til at bogmærke et link til [Microsoft 365 og Office 365 tjenestebeskrivelser](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Du skal bruge tjenestebeskrivelserne for at få mere at vide om SharePoint Online-funktioner, og hvordan de kan adskille sig fra SharePoint-serveren i det lokale miljø. Opgrader funktionelle Microsoft Office SharePoint Server 2007-farme. Hvis din installation har websteder, der er brudt, skal du løse dem før opgraderingen.
  
## <a name="a-note-about-managing-risk"></a>En note om administration af risiko

Metoder som "side om side" er vigtige i forbindelse med opgraderingslogik. Når du opgraderer side om side, vedligeholder du din Microsoft Office SharePoint Server 2007-farm, men bygger en farm ud fra den næste version (SharePoint Server 2010) på ny hardware. Dette hjælper på tre måder:
  
1. Du har et sted, hvor du kan tage sikkerhedskopier af dine Microsoft Office SharePoint Server 2007-databaser for at opgradere dem separat ved hjælp af databasetilknytter.
    
2. Hvis du finder ud af, at kun nogle få vigtige dokumentbiblioteker og andre oplysninger er i brug på din Microsoft Office SharePoint Server 2007-farm, kan du vælge at flytte data manuelt fra Microsoft Office SharePoint Server 2007 til SharePoint  Server 2010, eller tag kun bestemte websteder og websteder til den næste version (hvilket kan gøre dit job nemmere).
    
3. Jo mindre du gør med serverfarmen Microsoft Office SharePoint Server 2007 direkte, jo sikrere er de data, som farmen indeholder, når du opgraderer.
    
Metoder som In-Place opgradering fungerer direkte på din Microsoft Office SharePoint Server 2007-farm, hvilket giver dig færre nemme muligheder for at opgive en sti og begynde igen med dit uberørte miljø. Så meget som muligt kan du bygge i nogle sikkerhedsforanstaltninger (f.eks. at tage og teste sikkerhedskopier af det oprindelige miljø). Hvis din Microsoft Office SharePoint Server 2007-farm f.eks. er virtuel og duplikeres med henblik på sikkerhedskopiering og gendannelse, skal du sikkerhedskopiere og gendanne de nyeste databaser før tjenestevinduet for opgraderingen. Vel vidende, at du har mulighed for at gendanne databasen sikkerhedskopier vil ikke kun give dig en failsafe, kan det give dig ro i sindet.
  
> [!TIP]
> Bedste fremgangsmåder for opgradering findes for [Microsoft Office SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc261992(v=office.12)), [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc261992(v=office.14)), [SharePoint Server 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013) og [SharePoint Server 2016](/SharePoint/upgrade-and-update/best-practices-for-upgrade). Du kan også søge efter [Microsoft-partnere](https://partnercenter.microsoft.com/pcv/search), der har erfaring med opgraderinger eller Microsoft 365 migreringer. 
  
## <a name="make-your-plan"></a>Lav din plan

Hvis du har brug for at opgradere, skal du bruge en plan, og en størrelse passer ikke alle i disse tilfælde. Din plan kan være så enkel som "Opret et Microsoft 365-abonnement med SharePoint Online, registrer et domæne, og omdiriger personer for at gemme deres filer der". Og det er det måske ikke. Denne beslutning er din, og det er ned til, hvad du og dine brugere virkelig har brug for.
  
> [!NOTE]
> Det er risikabelt at køre på software, hvis livscyklus er ophørt. Produkter, der ikke understøttes, repareres ikke længere, når der findes problemer. Det betyder også, at hvis der opstår nye sikkerhedstrusler, vil der ikke være nogen sikkerhedsrettelser eller rettelser, fordi livscyklusprodukterne ikke længere understøttes. Undgå venligst denne situation! 
  
### <a name="first-know-your-farm"></a>Først skal du kende din farm

Når du opgraderer, skal din beslutningstagning være baseret på, hvad din farm gør for din organisation. Hvad behøver det tilfredsstille? Hvad er dens rolle? Hver farm i virksomheden kan have en anden rolle. Nogle af dine SharePoint farme kan være *kritiske*, nogle kan være filarkiver – der for at sikre opbevaring. Eller hvis din farm udfylder mange roller på én gang, skal du muligvis vide, hvad grupper af websteder, websteder eller endda dokumentbiblioteker gør, eventuelle tilpasninger, og hvor vigtige de er. Det kan virke som meget arbejde at analysere dine data på dette niveau, men det sparer tid og kræfter at mestre dit domæne, før du opgraderer eller overfører dem. Når du kender alle de bevægelige dele, og de vigtigste dele, vil du også vide, hvad du har vokset og kan efterlade. Den viden vil kun gavne dig fremover. 
  
Så hvad siger brugerne, er vigtigst om din SharePoint Server-farm?
  
- Indbyggede SharePoint funktioner
    
- Det store datakorpus (f.eks. et arkiv over filer)
    
- Tilgængelighed
    
- Vigtige apps, webdele eller dokumenter i farmen (missionskritisk farm)
    
- Overholdelsesstandarderne er opfyldt
    
- Tilpasninger
    
Hvis du kører noget vigtigt for din virksomhed fra din SharePoint farm, kan du sige, at det fungerer som et stort katalog over vigtige data om kravene til klienttjenesten, du kan sætte et kryds ud for 'Kritiske apps', men også 'Tilgængelighed'. Det vil sige, at din virksomhed vil blive påvirket, hvis du ikke kunne bruge SharePoint i et stykke tid. På samme måde kan du kontrollere "Tilpasninger", fordi de vigtige tjenester, som farmen tilbyder, er baseret på brugerdefineret kode, webstedsdefinitioner eller mange tilpasninger, der arbejder sammen.
  
Hvis SharePoint opfyldt disse behov uden din involvering uden for at bruge det, der er indbygget i softwaren, og du generelt opdaterer den og udfører normal administration og vedligeholdelse, har du måske valgt "Indbygget SharePoint"- dette kan også være din grund til at sidde på en ældre version af SharePoint. Med andre ord, det allerede gør, hvad du har brug for det til, og du har ikke brug for at opgradere indtil nu, på Microsoft Office SharePoint Server 2007 ophør af support.
  
Når du angiver disse ting med punkttegn, opretter du kriterier for opgraderingen. Med andre ord, ville enhver opgradering nødt til at opfylde denne bar for at blive overvejet. Dette giver dig mulighed for at udelukke metoder, der i øjeblikket ikke passer til dine behov.
  
### <a name="a-simple-sample-plan"></a>En enkel eksempelplan

Der skal muligvis være større konsensus med ledelsen og andre administratorer om den vej, som din SharePoint Opgradering vil følge. SharePoint serveradministratorer samarbejder ofte med Microsoft SQL Server administratorer, arbejder med netværks- og sikkerhedsteams og meget mere. Hvor der er mange interessenter, skal du muligvis oprette en aftale for eller justere din opgraderings- og migreringsplan. Hvis du f.eks. overfører data, så en del af din virksomhed bruger SharePoint Online i Microsoft 365, skal der sandsynligvis foretages justering eller test af ydeevnen i dit netværk. Berørte teams bør informeres på forhånd.
  
I mit enkle eksempel viser jeg et SharePoint administratorforslag og viser derefter den plan, som alle interessenterne er enige om. Du kan få mere klarhed ved at dokumentere dine aftaler og beslutninger.
  
Planen starter efter en dybdegående analyse af en farm og forsøger at identificere farmens rolle, smertepunkter og andre vigtige oplysninger, der vil føre til, at nogle opgraderingsmuligheder indsnævres. Derefter stilles der et opgraderingsforslag af SharePoint administrator, og interessenterne bliver enige om en handlingsplan.
  
Min 'vigtigste' punktopstilling:
  
- Tilgængelighed, funktioner, der er indbygget i SharePoint, og standarder for overholdelse af angivne standarder.
    
- De fleste af dataene er på tre grupper af websteder, hvor ét mødearbejdsområde bruges af et udviklerteam, som er vigtigt og bruges hårdt i flere tidszoner over hele verden.
    
- Der er 17 andre websteder, der er udbredt.
    
- To dokumentbiblioteker (mødearbejdsområde og dokumenter i rodgruppen af websteder) er størst (mere end 8000 dokumenter hver). Vi har et stort antal arkiverede dokumenter og lister med vedhæftede regneark.
    
- Der er 14 lister over biblioteker, der har følsomme data, som SKAL overholde angivne standarder.
    
- Vi SKAL have evnen til at gøre ventepositioner og e-opdagelse, uanset hvor vi går.
    
- Nogle af disse data SKAL forblive i det lokale miljø på grund af InfoSec-regler.
    
 **Valgmuligheder for opgradering og overførsel:**
  
| Ja | Nej |
|:-----|:-----|
|Opgrader databaser med database vedhæft  <br/> |Lokal opgradering  <br/> |
|Opgrader med farme side om side  <br/> |Hybridopgradering  <br/> |
|Overførsels-API til SPO i Microsoft 365 (til personlige webstedsdata)  <br/> |SharePoint Hybrid (endnu ikke nødvendigt)  <br/> |
|Nogle manuelle dataoverførseler til SharePoint Online for vigtige data  <br/> |opgrader FastTrack guide til Microsoft 365  <br/> |
   
 **Min foreslåede plan:**
  
Opgrader i det lokale miljø med versioner af SharePoint side om side, nogle virtualiseret, så vi kan opgradere databaserne først. Gå fra SharePoint 2007 til SharePoint 2010. Administratorer og udviklere tester den resulterende farm. Brugerne tester den resulterende farm. Løs eventuelle problemer med visningsstop i denne periode. Opgrader igen SharePoint 2010-databaser til SharePoint 2013. Test. Brugertest/pilot. Løs eventuelle problemer med visningsstop i denne periode.
  
- Overvej, om en hybrid i organisationsnetværket søgning med SPO opfylder dine behov.
    
- Overvej [FastTrack hjælp](https://fasttrack.microsoft.com), hvis du vil opgradere til SharePoint Online herfra. 
    
- Find ud af, om nogen grupper af websteder kan indlæses i et Microsoft 365-abonnement. (Microsoft 365 opfylder mange [standarder for overholdelse af angivne standarder](/compliance/regulatory/offering-home). Microsoft 365 har [eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) og kan foretage [ventepositioner](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) via Overholdelsescenter. 
    
Ellers skal du fortsætte med en side om side-opgradering til SharePoint Server 2016.
  
> [!NOTE]
> Mellem anbefalinger fra administratorer, der planlægger opgraderingen, og den faktiske proces er de samtaler, der foregår med andre interessenter, som opgraderingen afhænger af. Nogle gange tvinger økonomierne f.eks. administratorer til at ændre deres planer. Uanset hvad den endelige beslutning er, bør du dokumentere, hvad den aftalte plan er, fremover. Det kan se nogenlunde sådan ud: 
  
 **Min handlingsplan:**
  
I det lokale miljø bruger vi et virtuelt miljø til at bygge standard SharePoint Server 2010 og 2013. SharePoint Server 2016 bygges på ny hardware, der opfylder systemkravene til 2016. Vi vil gøre databasen vedhæftes til opgradering af databaser fra SharePoint 2007 gennem alle versioner mellem den og SharePoint Server 2016. Kernetilpasninger genskabes for og testes i SharePoint Server 2016-miljøet på nuværende tidspunkt, hvis de oprindelige funktioner ikke allerede opfylder vores behov. Hvis vi lykkes, har vi en farm i det lokale miljø på ny hardware med opgraderede databaser og færre tilpasninger. Vi vedhæfter de opgraderede indholdsdatabaser til nye grupper af websteder i SharePoint Server 2013, test, brugertest/pilot, og udfører derefter et DNS-klip til det nye SharePoint Server 2016-miljø til livebrug.
  
- Vi overvejer ikke Organisationsnetværks hybrid mellem SharePoint Server 2016 og SharePoint Online lige nu.
    
- Anslået kan 35 % af vores websteder omdannes til nye SPO-websteder med forfængelighedsdomæner eller i sidste ende blive OneDrive for Business lager. Leder du efter andre muligheder for at konvertere websteder eller dirigere nye websteder til SPO.
    
- En del af denne del af migreringen vil være manuel ved at trække og slippe for at OneDrive for Business personlige websteder, og nogle af migrerings-API'en.
    
Mere detaljerede trin eller en række links til specifikke opgraderingsretninger skal følge en plan. MOSS 2007-computeren bør ikke tages ud af drift, og virtuelle miljøer bør bevares af sammenligningshensyn. Opgraderingen fuldføres dog, når brugerne omdirigeres til SharePoint Server 2016.
  
Ofte er store faktorer, når du vælger en metode, de samlede omkostninger ved opgraderingen og omkostningerne i tide (du kan se mere om dette i artiklen SharePoint Migration Roadmap). Men planlægning forude vil drage stor fordel af dig i at sætte forventninger, vælge klogt, og udformningen af, hvad succes vil se ud.
  
## <a name="related-links"></a>Relaterede links

[Ressourcer, der kan hjælpe dig med at opgradere fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
  
[Microsofts livscykluspolitik og livscyklussøgning](https://support.microsoft.com/lifecycle)
  
[Søg efter Microsoft-partnere, der kan hjælpe med opgradering eller overførsel](https://partnercenter.microsoft.com/pcv/search)
