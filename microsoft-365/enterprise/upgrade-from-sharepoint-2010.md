---
title: Opgradering fra SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: Find oplysninger og ressourcer, der skal opgraderes SharePoint 2010 SharePoint Server 2010. Support for begge ender 13. april 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7ce6b333e39d02000514c174579a1ad0fa816771
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601558"
---
# <a name="upgrading-from-sharepoint-2010"></a>Opgradering fra SharePoint 2010

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Support til Microsoft SharePoint 2010 SharePoint Server 2010 slutter den **13. april 2021**. Denne artikel indeholder ressourcer, der kan hjælpe dig med at overføre dine eksisterende SharePoint Server 2010-data til SharePoint Online i Microsoft 365 eller opgradere dit lokale SharePoint Server 2010-miljø.

## <a name="what-is-end-of-support"></a>Hvad er *ophør af support*?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Efter datoen for ophør af support holder produktet ikke op med at fungere, men Microsoft yder ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.

- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.

- Tidszoneopdateringer.

Det betyder, at der ikke kommer nogen yderligere opdateringer, rettelser eller rettelser til produktet (herunder sikkerhedsrettelser/-rettelser). Microsoft Support vil have ændret sine supportindsatser til nyere versioner.

Efterhånden som understøttelsen af SharePoint Server 2010 nærmer sig, kan du slette data, du ikke længere har brug for, før du opgraderer produktet og overfører dine vigtige data.

> [!NOTE]
> En softwarelivscyklus varer typisk ti år fra den første udgivelse. [Microsoft-løsningsudbydere](https://go.microsoft.com/fwlink/?linkid=841249) kan hjælpe dig med at opgradere til den næste version af softwaren eller overføre Microsoft 365 overførsel (eller begge). Sørg for, at du også er opmærksom på datoer for ophør af support for kritiske underliggende teknologier, især for den version af Microsoft SQL Server, du bruger sammen med SharePoint. Du kan få mere at vide under [Fast politik for livscyklus](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planlæg fremad

Kontrollér de datoer, der understøtter slutdatoer, på [webstedet produktlivscyklus](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Planlæg dine opgraderinger eller migreringerne med disse datoer for øje. Husk, at produktet *ikke holder op med at fungere på* den angivne dato. Men da din installation ikke længere bliver patched efter denne dato, skal du planlægge en problemfri overgang til den næste version af produktet.

Denne matrix hjælper med at afbilde et kursus blandt overførselsindstillingerne:

|Ophør af supportprodukt|God |Bedst|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (lokalt miljø)|SharePoint Online|
||SharePoint Server 2013-hybrid med SharePoint Online|SharePoint Server 2016 (lokalt miljø)|
|||SharePoint hybridsøgning i skyen|

Hvis du vælger en indstilling i den lave ende af skalaen (god), skal du begynde at planlægge en anden opgradering, kort efter din overførsel fra SharePoint Server 2010.

Her er de tre stier, du kan gå for at undgå ophør af support til SharePoint Server 2010.

![SharePoint server 2010-opgraderingsstier.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> Ophør af support til SharePoint Server 2010 og SharePoint Foundation 2010 er planlagt til d. 13. april 2021. Men sørg for at kontrollere [webstedet for produktlivscyklussen](https://support.microsoft.com/lifecycle) for de mest aktuelle datoer.

## <a name="whats-next"></a>Hvad sker der derefter?

SharePoint Server 2013 SharePoint Foundation 2013 kan installeres lokalt på dine egne servere. Eller du kan bruge SharePoint Online, som er en onlinetjeneste, der er en del af Microsoft 365. Du kan vælge at:

- Overfør til SharePoint Online.

- Opgrader SharePoint server SharePoint Foundation i det lokale miljø.

- Gør begge dele ovenfor.

- Implementer [SharePoint hybridløsning](/sharepoint/hybrid/hybrid).

Overvej de skjulte omkostninger til vedligeholdelse af en serverfarm, herunder vedligeholdelse eller overførsel af tilpasninger og opgradering af hardware. Hvis du har taget højde for disse faktorer, vil det være nemmere at opgradere lokalt. Hvis du kører din farm på ældre SharePoint-servere uden tung tilpasning, kan du drage fordel af en planlagt overførsel til SharePoint Online. I forbindelse med et lokalt SharePoint Server-miljø kan du også overveje at flytte nogle data i SharePoint Online for at reducere spild af hardwarestyring.

> [!NOTE]
> SharePoint-administratorer kan oprette et Microsoft 365-abonnement, konfigurere nye SharePoint Online-websteder og derefter skære renskåret fra SharePoint Server 2010 og kun tage vigtige dokumenter med til de nye websteder. Derefter kan eventuelle resterende data tømmes fra SharePoint Server 2010-webstedet til lokale arkiver.

|SharePoint Online|SharePoint lokal server|
|---|---|
|Høje omkostninger i tid (plan/eksekvering/bekræftelse)|Høje omkostninger i tid (plan/eksekvering/bekræftelse)|
|Billigere (ingen hardwarekøb)|Højere omkostninger i midler (hardwarekøb)|
|Engangsomkostninger i forbindelse med overførsel|Engangsomkostning gentaget pr. fremtidig overførsel|
|Lave samlede ejerskabsomkostninger/vedligeholdelse|Høje samlede ejerskabsomkostninger/vedligeholdelse|

En engangsudløsning til Microsoft 365 har højere omkostninger, mens du organiserer data og beslutter, hvad du skal tage i skyen, og hvad du vil efterlade. Men når dine data er overført, vil fremtidige opgraderinger ske automatisk, da du ikke længere har brug for at administrere hardware- og softwareopdateringer. Og din farms oppetid understøttes af en [Microsoft-serviceaftale (SLA).](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)

### <a name="migrate-to-sharepoint-online"></a>Overfør til SharePoint Online

Sørg for, SharePoint Online tilbyder alle de funktioner, du har brug for. Se [SharePoint tjenestebeskrivelse](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

Du kan ikke overføre direkte fra SharePoint Server 2010 (eller SharePoint Foundation 2010) til SharePoint Online. Der er så meget manuelt overflytningsarbejde. Men denne fase giver dig mulighed for at beskære data og websteder, der ikke længere er nødvendige før flytningen. Du kan arkivere andre data, så de bliver lagret. 

Husk, SharePoint Server 2010 og SharePoint Foundation 2010 ikke holder op med at fungere ved ophør af supporten. Administratorer kan derfor have en periode, hvor SharePoint kører, hvis deres kunder glemmer at flytte nogle af deres data.

Hvis du opgraderer til SharePoint Server 2013 eller SharePoint Server 2016 og beslutter dig for at placere data i SharePoint Online, kan du bruge [SharePoint Migration API](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) til at overføre oplysninger til OneDrive for Business.

|SharePoint Online-fordel|SharePoint ulemper ved Online|
|---|---|
|Microsoft leverer SPO-hardware og al hardwareadministration.|Tilgængelige funktioner kan variere SharePoint lokal server og SPO.|
|Du er Sharepoint-administrator eller global administrator af dit abonnement og kan tildele administratorer til SPO-websteder.|Nogle handlinger, der er tilgængelige for en farmadministrator i SharePoint Server i det lokale miljø, findes ikke (eller er ikke nødvendige) i SharePoint-administratorrollen i Microsoft 365. Men SharePoint Administration, Administration af gruppe af websteder og Ejerskab af websted er lokalt for din organisation.|
|Microsoft anvender rettelser, rettelser og opdateringer til underliggende hardware og software, herunder SQL servere, hvor SharePoint Online kører.|Da der ikke er adgang til det underliggende filsystem i tjenesten, er tilpasningen begrænset.|
|Microsoft udgiver [serviceaftaler og](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) går hurtigt i gang med at løse problemer med hændelser på tjenesteniveau.|Sikkerhedskopiering og gendannelse og andre gendannelsesmuligheder automatiseres af tjenesten i SharePoint Online. Sikkerhedskopier overskrives, hvis de ikke bruges.|
|Sikkerhedstestning og serverydelsesjustering udføres løbende i tjenesten af Microsoft.|Ændringer i brugergrænsefladen og SharePoint funktioner installeres af tjenesten og skal muligvis være slået til eller fra.|
|Microsoft 365 opfylder mange branchestandarder: [Microsofts overholdelsestilbud](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) til overførsel er begrænset.  <br/> Meget af opgraderingen vil være manuel eller via SPO Migration API'en, der er beskrevet i SharePoint [Online og OneDrive Roadmap til overførsel af indhold](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Microsoft-supportteknikere og datacentermedarbejdere har ikke ubegrænset administratoradgang til dit abonnement.|Der kan være ekstra omkostninger, hvis hardwareinfrastrukturen skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis der kræves en sekundær farm til opgradering.|
|Løsningsudbydere kan hjælpe med engangsjobbet at overføre dine data til SharePoint Online.|Ikke alle ændringer af SharePoint Online er inden for din kontrol. Efter overførslen kan designforskelle i menuer, biblioteker og andre funktioner midlertidigt påvirke brugervenligheden.|
|Onlineprodukter opdateres automatisk på tværs af tjenesten. Funktioner frarådes muligvis, men supportlivscyklussen afsluttes ikke korrekt.|Der er en ophør af supportlivscyklus for SharePoint Server eller SharePoint Foundation samt underliggende SQL-servere.|

Hvis du har besluttet dig for at oprette et Microsoft 365 websted og manuelt overføre data til det efter behov, skal du kontrollere [dine Microsoft 365 indstillinger](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Opgradere SharePoint server i det lokale miljø

Opgraderingerne SharePoint Server 2019 *serielt*. Det er ikke muligt at opgradere fra SharePoint Server 2010 til SharePoint Server 2016 eller SharePoint 2019 direkte. Sti til seriel opgradering:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Det tager tid og planlægning at følge hele stien fra SharePoint 2010 til SharePoint Server 2016. Opgraderinger omfatter omkostninger til hardware (SQL-servere skal også opgraderes), software og administration. Desuden skal tilpasninger muligvis opgraderes eller endda blive afbrudt. Sørg for at dokumentere vigtige tilpasninger, før du opgraderer din SharePoint Server-farm.

> [!NOTE]
> Det er muligt at bevare din SharePoint 2010-farm, installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til at hente og overføre indhold igen). Men der er potentielle fejl i disse manuelle flytninger, f.eks. dokumenter, der kommer fra 2010 og har en aktuel konto, der senest er blevet ændret, med aliasset for den konto, der flytter manuelt. Og noget arbejde skal udføres i forvejen, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Sørg for at rense dit miljø, før du opgraderer. Overvej, hvilke data du kan flytte til lagerplads eller ikke længere har brug for. Dette kan reducere effekten af overførslen. Sørg for, at din eksisterende farm fungerer, før du opgraderer, og (helt sikkert) før du afvikler!

Husk at gennemgå de *understøttede og ikke-understøttede opgraderingsstier*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Hvis du har *tilpasninger*, er det vigtigt, at du planlægger for hvert trin i overførselsstien:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Lokal fordel|Ulemper ved det lokale miljø|
|---|---|
|Fuld kontrol over alle aspekter af din SharePoint Farm (og dens SQL) fra serverhardwaren og op.|Din virksomhed har ansvaret for alle pauser og rettelser. Men du kan kontakte betalt Microsoft Support, hvis dit produkt ikke har ophør af support.|
|Fuldt funktionssæt SharePoint Server i det lokale miljø med mulighed for at forbinde din lokale farm til et SharePoint Online-abonnement via hybrid.|Opgradering, rettelser, sikkerhedsopdateringer, hardwareopgradering og al vedligeholdelse af SharePoint Server og dens SQL-farm administreres lokalt.|
|Fuld adgang til større tilpasningsmuligheder end med SharePoint Online.|[Microsofts tilbud om](/compliance/regulatory/offering-home) overholdelse af regler og standarder skal konfigureres manuelt lokalt.|
|Sikkerhedstestning og serverydelsesjustering udføres i dit lokale miljø under din kontrol.|Microsoft 365 kan gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø.|
|Løsningsudbydere kan hjælpe med at overføre data til den næste version SharePoint Server (og derefter).|Dine SharePoint serverwebsteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.|
|Fuld kontrol over navngivningskonventioner, sikkerhedskopiering, gendannelse og andre gendannelsesmuligheder SharePoint server i det lokale miljø.|SharePoint server i det lokale miljø er følsom over for produktlivscyklusser.|

### <a name="upgrade-resources"></a>Opgrader ressourcer

Start med at sammenligne hardware- og softwarekrav. Hvis dit aktuelle miljø ikke opfylder de grundlæggende krav, skal du muligvis først opgradere hardwaren i farmen eller SQL serverne. 

Du beslutter dig måske for at flytte nogle af dine websteder til den "stedsegrøn" hardware SharePoint Online. Når du har foretaget din vurdering, skal du følge de understøttede opgraderingsstier og -metoder.

- *Hardware-/softwarekrav til:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Softwaregrænser og -begrænsninger for:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Oversigt over opgraderingsprocessen for:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Opret en hybridløsning med SharePoint Online SharePoint Server i det lokale miljø

En hybrid installation giver det bedste fra både lokalt og online til nogle overførselsbehov. Du kan forbinde SharePoint Server 2013-, 2016- eller 2019-farme til SharePoint Online for at oprette SharePoint hybrid: Få mere at vide [SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Hvis en SharePoint serverfarm er dit overførselsmål, skal du finde ud af, hvilke websteder og brugere der skal flyttes online, og hvilke der skal forblive i det lokale miljø. Rangering af SharePoint serverfarmindhold som høj, mellem eller lav påvirkning for din virksomhed kan hjælpe med denne beslutning. Det kan kun være nødvendigt at dele brugerkonti til logon og SharePoint Server-søgeindeks med SharePoint Online. Men denne faktor er muligvis ikke klar, før du ser på, hvordan dine websteder bruges. Hvis virksomheden senere beslutter at overføre alt dit indhold til SharePoint Online, kan du flytte alle resterende konti og data online og udgået af din lokale farm. Administration/administration af SharePoint udføres via Microsoft 365 konsoller fra det pågældende tidspunkt.

Sørg for at blive fortrolig med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint-farm og dit Microsoft 365-abonnement.

|Indstilling|Beskrivelse|
|---|---|
|[Microsofts tilbud om overholdelse af regler og standarder](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) til overførsel er begrænset.<br/><br/> Meget af opgraderingen vil være manuel eller via SPO Migration API'en, der er beskrevet i SharePoint [Online og OneDrive Roadmap til overførsel af indhold](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Microsoft-supportteknikere og datacentermedarbejdere har ikke ubegrænset administratoradgang til dit abonnement.|Der kan være ekstra omkostninger, hvis hardwareinfrastrukturen skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis en sekundær farm er påkrævet.|
|Partnere kan hjælpe med det engangsjob, som det er at overføre dine data til SharePoint Online.||
|Onlineprodukter opdateres automatisk på tværs af tjenesten. Funktioner frarådes muligvis, men supporten afsluttes ikke korrekt.||

Hvis du har besluttet dig for at oprette et nyt Microsoft 365 websted og manuelt overføre data til det efter behov, skal du [kontrollere dine Microsoft 365 indstillinger](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Opgradere SharePoint server i det lokale miljø

Det er ikke muligt at springe versioner i SharePoint opgraderinger. Det betyder, at opgraderinger bliver serielt:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Hvis du vil gå hele vejen fra SharePoint 2007 til SharePoint Server 2016 kræver det en betydelig tidsinvestering og involverer hardware (SQL-servere skal også opgraderes), omkostninger til software og administration. Tilpasninger skal opgraderes eller opgives i henhold til funktionens betydning.

> [!NOTE]
> Det er muligt at bevare slutningen af din levetid SharePoint 2007-farm, installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til at hente og overføre indhold igen). Men der er visse ulemper ved disse manuelle flytninger, f.eks. flytninger af dokumenter, der erstatter den senest ændrede konto med aliasset for den konto, der flytter manuelt. Og der skal udføres meget arbejde i forvejen, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Under alle omstændigheder skal du overveje, hvilke data du kan flytte til lagerplads eller ikke længere har brug for at reducere effekten af overførslen.

Sørg for at rense dit miljø, før du opgraderer. Sørg for, at din eksisterende farm fungerer, før du opgraderer, og helt sikkert før du afvikler!

Husk at gennemgå de *understøttede og ikke-understøttede opgraderingsstier*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Hvis du har *tilpasninger*, er det vigtigt at planlægge din opgradering for hvert trin i overførselsstien:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Professionel i det lokale miljø|Lokalt miljø|
|---|---|
|Fuld kontrol over alle aspekter af din SharePoint Farm fra serverhardwaren og op.|Din virksomhed har ansvaret for alle pauser og rettelser. (Men du kan kontakte betalt Microsoft Support, hvis dit produkt ikke har ophør af support.)|
|Fuldt funktionssæt SharePoint Server i det lokale miljø med mulighed for at forbinde din lokale farm til et SharePoint Online-abonnement via hybrid.|Opgradering, rettelser, sikkerhedsopdateringer og alt vedligeholdelse af SharePoint Server administreres lokalt.|
|Fuld adgang til større tilpasning.|[Microsofts tilbud om](/compliance/regulatory/offering-home) overholdelse af regler og standarder skal konfigureres manuelt lokalt.|
|Sikkerhedstestning og serverydelsesjustering udføres i dit lokale miljø under din kontrol.|Microsoft 365 muligvis gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø.|
|Partnere kan hjælpe med at overføre data til den næste version SharePoint Server (og derefter).|Dine SharePoint serverwebsteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.|
|Fuld kontrol over navngivningskonventioner, sikkerhedskopiering, gendannelse og andre gendannelsesmuligheder SharePoint server i det lokale miljø.|SharePoint server i det lokale miljø er følsom over for produktlivscyklusser.|

### <a name="upgrade-resources"></a>Opgrader ressourcer

Start med at vide, at du opfylder hardware- og softwarekrav, og følg derefter de understøttede opgraderingsmetoder.

- *Hardware-/softwarekrav til*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Softwaregrænser og -begrænsninger for*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *Oversigt over opgraderingsprocessen for*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Opret en SharePoint hybridløsning SharePoint online og lokalt miljø

Hvis svaret på dine overførselsbehov ligger mellem den styring, der tilbydes af det lokale miljø, og de lavere ejerskabsomkostninger i SharePoint Online, kan du forbinde SharePoint Server 2013- eller 2016-farme til SharePoint Online via hybrider. [Få mere at vide SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Hvis du beslutter, at en SharePoint Server-hybridfarm vil være en fordel for din virksomhed, skal du gøre dig bekendt med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint-farm og dit Microsoft 365-abonnement.

Det kan være en god ide Microsoft 365 et udviklings-/testmiljø, som du kan konfigurere med [Test Lab-vejledninger](m365-enterprise-test-lab-guides.md). Når du får en prøveversion eller et købt Microsoft 365-abonnement, kan du oprette grupper af websteder, websteder og dokumentbiblioteker i SharePoint Online, som du kan overføre data til. Du kan overføre manuelt, ved hjælp af overførsels-API'en, eller, hvis du vil overføre indholdet på Mit websted OneDrive for Business, via hybridguiden.

> [!NOTE]
> Hvis du vil bruge hybridindstillingen, skal din SharePoint Server 2010-farm først opgraderes lokalt til SharePoint Server 2013 eller 2016. SharePoint Foundation 2010 og SharePoint Foundation 2013 understøtter ikke hybridforbindelser med SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Oversigt over indstillinger for Office 2010-klient og -servere Windows 7

Du kan finde en visuel oversigt over indstillingerne for opgradering, overførsel og flytning til skyen for Office 2010-klienter og -servere og Windows 7 i slutningen af [supportplakaten](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Ophør af support til Office 2010-klienter og -servere Windows 7 poster.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Denne plakat illustrerer de forskellige veje, du kan gå for at undgå Office 2010-klient- og serverprodukter og Windows 7 ophør af support, med foretrukne stier og understøttelser i Microsoft 365 Enterprise fremhævet.

Du kan også [downloade](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) denne plakat og udskrive den i letter-, legal- eller tabloid-format (11 x 17).

## <a name="related-articles"></a>Relaterede artikler

[Ressourcer, der kan hjælpe dig med at opgradere Office 2007- eller 2010-servere og -klienter](upgrade-from-office-2010-servers-and-products.md)

[Oversigt over opgraderingsprocessen fra SharePoint 2010 til SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[Bedste fremgangsmåder for opgradering fra SharePoint 2010 til SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[Fejlfinding af problemer med databaseopgradering SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Søg efter Microsoft-løsningsudbydere for at få hjælp med din opgradering](https://go.microsoft.com/fwlink/?linkid=841249)

[Opdaterede politik for produktservice for SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[Opdaterede politik for produktservice for SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
