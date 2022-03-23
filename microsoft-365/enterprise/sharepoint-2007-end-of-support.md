---
title: SharePoint oversigt over ophør af support til Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1.keywords:
- CSH
ms.custom:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
- seo-marvel-apr2020
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: Support til SharePoint Server 2007 sluttede i oktober 2017. I denne artikel kan du få mere at vide om dine muligheder for opgradering, overførsel og support.
ms.openlocfilehash: d09e0cf58ef814a76cdac28f6029189eaf655efc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594270"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint oversigt over ophør af support til Server 2007

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Den **10. oktober 2017** Microsoft Office SharePoint support til Server 2007 ophør af supporten. Hvis du ikke har overført fra SharePoint Server 2007 til Microsoft 365 eller en nyere version af SharePoint Server lokalt, skal du begynde planlægningen nu. Denne artikel indeholder ressourcer, der kan hjælpe dig med at overføre data SharePoint Online eller SharePoint server i det lokale miljø.
  
## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

SharePoint Server har, som de fleste Microsoft-produkter, en supportlivscyklus, hvor Microsoft leverer nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Når supporten er slut, yder Microsoft ikke længere:
  
- Teknisk support til problemer, der kan opstå.
    
- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.
    
- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.
    
- Tidszoneopdateringer.
    
Din SharePoint Server 2007-farm fungerer stadig efter d. 10. oktober 2017, men der frigives ingen yderligere opdateringer, rettelser eller rettelser til produktet, herunder sikkerhedsrettelser/-rettelser. Microsoft Support har ændret sine supportindsatser til nyere versioner af produktet. Da din installation ikke længere understøttes eller opdateres, skal du opgradere produktet eller overføre vigtige data.
  
> [!TIP]
> Hvis du ikke allerede har tilrettelagt opgradering eller overførsel, skal du se: [SharePoint 2007-overførselsmuligheder](sharepoint-2007-migration-options.md), som du bør overveje for at få nogle eksempler på, hvor du kan begynde. Du kan også søge efter [Microsoft-partnere](https://go.microsoft.com/fwlink/?linkid=841249), der kan hjælpe med opgradering eller Microsoft 365 overførsel (eller begge dele).
  
Du kan finde flere oplysninger Office 2007-servere og ophør af support under Ressourcer, der kan hjælpe dig med at opgradere [fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Dit første stop bør være webstedet [produktlivscyklus](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). Hvis du har et lokalt Microsoft-produkt, der er ved at være forældet, skal du kontrollere datoen for slutdatoen for support, så du har et år eller deromkring for at planlægge en opgradering eller overførsel. Når du vælger det næste trin, skal du overveje, hvilke produktfunktioner der er gode nok, bedre og bedst. Her er et eksempel: 
  
|**God**|**Bedre**|**Bedst**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint Hybrid  <br/> |SharePoint Server 2016  <br/> |
| | |SharePoint Hybrid  <br/> |
   
Hvis du vælger en "god nok"-mulighed, skal du snart begynde at planlægge en anden opgradering, når overførslen SharePoint Server 2007 er fuldført. 

>[!NOTE] 
>Datoer for ophør af support kan blive ændret. Kontrollér webstedet [produktlivscyklus](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>Hvor kan jeg gå næste gang?

SharePoint Server kan installeres lokalt på dine egne servere. Eller du kan bruge SharePoint Online, som er en onlinetjeneste, der er en del af Microsoft 365. Du har følgende muligheder:
  
- Overfør til SharePoint Online.
    
- Opgrader SharePoint server i det lokale miljø.
    
- Gør begge dele ovenfor.
    
- Implementer [SharePoint hybridløsning](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
    
Vær opmærksom på, at der er knyttet skjulte omkostninger til vedligeholdelse af en serverfarm, vedligeholdelse eller overførsel af tilpasninger og opgradering af den hardware, SharePoint serverbehov. Du kan få fordel af SharePoint lokal serverfarm, hvis det er nødvendigt. Men hvis du kører din farm på ældre SharePoint Servere uden tung tilpasning, kan du drage fordel af overførslen til SharePoint Online.
  
> [!IMPORTANT]
> Der er en anden mulighed, hvis indholdet i SharePoint 2007 sjældent bruges. Nogle SharePoint-administratorer vælger at oprette et Microsoft 365-abonnement, konfigurere et nyt SharePoint Online-websted og derefter skære renskåret fra SharePoint 2007 og kun tage vigtige dokumenter med til de nye SharePoint Online-websteder. Data kan derefter tømmes fra det SharePoint 2007-websted og arkiveres. Overvej, hvordan brugerne arbejder med data fra din SharePoint 2007-installation. Der kan være kreative måder at administrere dine behov på.
  
|**SharePoint Online (SPO)**|**SharePoint lokal server**|
|:-----|:-----|
|Høje omkostninger i tid (planlæg /eksekvering/bekræftelse)  <br/> |Høje omkostninger i tid (planlæg /eksekvering/bekræftelse)  <br/> |
|Billigere (ingen hardwarekøb)  <br/> |Højere omkostninger i midler (hardware + udviklere/administratorer)  <br/> |
|Engangsomkostninger i forbindelse med overførsel  <br/> |Engangsomkostning gentaget pr. fremtidig overførsel  <br/> |
|Lave samlede ejerskabsomkostninger/vedligeholdelse  <br/> |Høje samlede ejerskabsomkostninger/vedligeholdelse  <br/> |
   
Når du overfører til Microsoft 365, har engangsflytningen en større omkostning, mens du organiserer data og beslutter, hvad du skal tage med i skyen, og hvad du skal efterlade. Men fremtidige opgraderinger vil være automatiske, og du behøver ikke længere at administrere hardware- og softwareopdateringer. Desuden understøttes din farms oppetid af en Microsoft Service Level Agreement ([SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)).
  
### <a name="migrate-to-sharepoint-online"></a>Overfør til SharePoint Online

Sørg for, SharePoint Online har alle de funktioner, du skal bruge. Se [Microsoft 365 og Office 365 tjenestebeskrivelser](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Du kan ikke overføre direkte fra SharePoint 2007 til SharePoint Online. Din flytning til SharePoint Online blev udført manuelt. Hvis du opgraderer til SharePoint Server 2013 eller SharePoint Server 2016, kan du f.eks. bruge SharePoint Migration API (til at overføre oplysninger til OneDrive for Business).
  
|**Online pro**|**Online con**|
|:-----|:-----|
|Microsoft leverer SPO-hardware og al hardwareadministration.  <br/> |Tilgængelige funktioner kan variere SharePoint lokal server og SPO.  <br/> |
|Du er Sharepoint-administrator eller global administrator af dit abonnement og kan tildele administratorer til SPO-websteder.  <br/> |Nogle handlinger, der er tilgængelige for en farmadministrator i SharePoint Server i det lokale miljø, findes ikke eller er ikke nødvendigvis inkluderet i SharePoint-administratorrollen i Microsoft 365.  <br/> |
|Microsoft anvender rettelser, rettelser og opdateringer på underliggende hardware og software. <br/> |Da der ikke er adgang til det underliggende filsystem i tjenesten, er tilpasningen begrænset.  <br/> |
|Microsoft udgiver [serviceaftaler og](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) går hurtigt i gang med at løse problemer med hændelser på tjenesteniveau. <br/> |Sikkerhedskopiering og gendannelse og andre gendannelsesmuligheder automatiseres af tjenesten i SharePoint Online. Sikkerhedskopier overskrives, hvis de ikke bruges. <br/> |
|Sikkerhedstestning og serverydelsesjustering udføres løbende i tjenesten af Microsoft. <br/> |Ændringer i brugergrænsefladen og SharePoint funktioner installeres af tjenesten og skal muligvis være slået til eller fra. <br/> |
|Microsoft 365 opfylder mange branchestandarder: [Microsofts overholdelsestilbud](/compliance/regulatory/offering-home).  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) til overførsel er begrænset.  <br/> Meget af opgraderingen vil være manuel eller via SPO Migration API'en, der er beskrevet i SharePoint [Online og OneDrive Roadmap til overførsel af indhold](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Microsoft-supportteknikere og datacentermedarbejdere har ikke ubegrænset administratoradgang til dit abonnement. <br/> |Der kan være ekstra omkostninger, hvis hardware skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis der kræves en sekundær farm til opgradering.  <br/> |
|Partnere kan hjælpe med det engangsjob, som det er at overføre dine data til SharePoint Online.  <br/> ||
|Onlineprodukter opdateres automatisk. Selvom funktioner muligvis frarådes, er der ingen rigtig ophør af support. <br/> ||
   
Hvis du har besluttet dig for at oprette et Microsoft 365 websted og manuelt overføre data til det efter behov, skal du kontrollere [dine Microsoft 365 indstillinger](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Opgradere SharePoint server i det lokale miljø

Det er ikke muligt at springe versioner i SharePoint opgraderinger. Opgraderinger går serielt:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Hvis du vil gå fra SharePoint 2007 til SharePoint Server 2016, betyder det en betydelig investering af tid og involverer omkostninger i hardware (SQL-servere skal også opgraderes), software og administration. Tilpasninger skal opgraderes eller opgives.
  
> [!NOTE]
> Det er muligt at bevare slutningen af din levetid SharePoint 2007-farm, installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til at hente og overføre indhold igen). Men pas på nogle af faldgruberne ved manuelle flytninger, f.eks. flytninger af dokumenter, der erstatter den senest ændrede konto med aliasset for den konto, der udfører den manuelle flytning. Overvej også det arbejde, der skal udføres i forvejen, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Overvej på forhånd, hvilke data du kan flytte til lagerplads eller slette for at reducere effekten af overførslen.
  
Det er vigtigt at rydde op i dit miljø, før du opgraderer. Sørg for, at din eksisterende farm fungerer, før du opgraderer, og helt sikkert før du afvikler!
  
Husk at gennemgå de *understøttede og ikke-understøttede opgraderingsstier*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Hvis du har tilpasninger, er det vigtigt at have en plan for hvert trin i overførselsstien: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Professionel i det lokale miljø**|**Lokalt miljø**|
|:-----|:-----|
|Fuld kontrol over alle aspekter af din SharePoint Farm fra serverhardwaren og op.  <br/> |Alle afbrydelser og rettelser er din virksomheds ansvar (du kan deltage i betalt Microsoft Support, hvis dit produkt ikke er udløbet af supporten).  <br/> |
|Fuldt funktionssæt SharePoint Server i det lokale miljø med mulighed for at forbinde din lokale farm til et SharePoint Online-abonnement via hybrid.  <br/> |Opgradering, rettelser, sikkerhedsopdateringer og alt vedligeholdelse af SharePoint Server administreres lokalt.  <br/> |
|Fuld adgang til større tilpasning.  <br/> |[Microsofts tilbud om](/compliance/regulatory/offering-home) overholdelse af regler og standarder skal konfigureres manuelt lokalt.  <br/> |
|Sikkerhedstestning og serverydelsesjustering udføres i dit lokale miljø (under din kontrol).  <br/> |Microsoft 365 muligvis gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø.  <br/> |
|Partnere kan hjælpe med at overføre data til den næste version af SharePoint Server (og derefter).  <br/> |Dine SharePoint Server-websteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.  <br/> |
|Fuld kontrol over navngivningskonventioner, sikkerhedskopiering og gendannelse og andre indstillinger for gendannelse SharePoint server i det lokale miljø.  <br/> |SharePoint server i det lokale miljø er følsom over for produktlivscyklusser.  <br/> |
   
### <a name="upgrade-resources"></a>Opgrader ressourcer

Sørg for, at dit miljø opfylder hardware- og softwarekrav, og følg derefter de understøttede opgraderingsmetoder.
  
- **Hardware-/softwarekrav til**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Softwaregrænser og -begrænsninger for**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Oversigt over opgraderingsprocessen for**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Opret en SharePoint hybridløsning SharePoint online og lokalt miljø

Hvis svaret på dine overførselsbehov ligger mellem den selvkontrol, der tilbydes af det lokale miljø, og de lavere ejerskabsomkostninger i SharePoint Online, kan du forbinde SharePoint Server 2013- eller 2016-farme til SharePoint Online via hybrider. [Få mere SharePoint om hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Hvis du beslutter, at en SharePoint Server-hybridfarm vil være en fordel for din virksomhed, skal du gøre dig bekendt med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint-farm og dit Microsoft 365-abonnement.
  
| Indstilling | Beskrivelse |
|:-----|:-----|
[Microsofts tilbud om overholdelse af regler og standarder](/compliance/regulatory/offering-home)  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) til overførsel er begrænset.  <br/> Meget af opgraderingen vil være manuel eller via SPO Migration API'en, der er beskrevet i SharePoint [Online og OneDrive Roadmap til overførsel af indhold](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Microsoft-supportteknikere og datacentermedarbejdere har ikke ubegrænset administratoradgang til dit abonnement.<br/> |Der kan være ekstra omkostninger, hvis hardwareinfrastrukturen skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis der kræves en sekundær farm til opgradering.  <br/> |
|Partnere kan hjælpe med det engangsjob, som det er at overføre dine data til SharePoint Online.  <br/> ||
|Onlineprodukter opdateres automatisk på tværs af tjenesten. Selvom funktioner muligvis frarådes, er der ingen egentlig ophør af support.<br/> ||
   
Hvis du har besluttet dig for at oprette et Microsoft 365 websted og manuelt overføre data til det efter behov, skal du kontrollere [dine Microsoft 365 indstillinger](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Opgradere SharePoint server i det lokale miljø

Det er ikke muligt at springe versioner i SharePoint opgraderinger. Opgraderinger går serielt:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Hvis du vil gå fra SharePoint 2007 til SharePoint Server 2016 kræver det en betydelig tidsinvestering og er forbundet med omkostninger til hardware (SQL-servere skal også opgraderes), software og administration. Tilpasninger skal opgraderes eller opgives.
  
> [!NOTE]
> Det er muligt at bevare slutningen af din levetid SharePoint 2007-farm, installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til at hente og overføre indhold igen). Men pas på potentielle fejl i forbindelse med manuel flytning, f.eks. flytninger af dokumenter, der erstatter den senest ændrede konto med aliasset for den konto, der udfører den manuelle flytning, og det arbejde, der skal udføres i forvejen, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Overvej, hvilke data du kan flytte til lagerplads eller slette for at reducere effekten af overførslen.
  
Rengør dit miljø før opgraderingen. Sørg for, at din eksisterende farm fungerer, før du opgraderer, og helt sikkert før du afvikler! 
  
Husk at gennemgå de *understøttede og ikke-understøttede opgraderingsstier*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Hvis du har *tilpasninger*, er det vigtigt, at du har en plan for opgraderingen for hvert trin i overførselsstien: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Lokale Pro**|**Con i det lokale miljø**|
|:-----|:-----|
|Fuld kontrol over alle aspekter af din SharePoint Farm fra serverhardwaren og op.  <br/> |Din virksomhed har ansvaret for alle pauser og rettelser. (Du kan kontakte betalt Microsoft Support, hvis dit produkt ikke er slut på support.)  <br/> |
|Fuldt funktionssæt SharePoint Server i det lokale miljø med mulighed for at forbinde din lokale farm til et SharePoint Online-abonnement via hybrid.  <br/> |Opgradering, rettelser, sikkerhedsopdateringer og alt vedligeholdelse af SharePoint Server administreres lokalt.  <br/> |
|Fuld adgang til større tilpasning.  <br/> |[Microsofts tilbud om](/compliance/regulatory/offering-home) overholdelse af regler og standarder skal konfigureres manuelt lokalt.  <br/> |
|Sikkerhedstestning og serverydelsesjustering udføres i dit lokale miljø under din kontrol.  <br/> |Microsoft 365 kan gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø  <br/> |
|Partnere kan hjælpe med at overføre data til den næste version SharePoint Server (og derefter).  <br/> |Dine SharePoint serverwebsteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.  <br/> |
|Fuld kontrol over navngivningskonventioner, sikkerhedskopiering og gendannelse og andre indstillinger for gendannelse SharePoint server i det lokale miljø.  <br/> |SharePoint server i det lokale miljø er følsom over for produktlivscyklusser.  <br/> |
   
### <a name="upgrade-resources"></a>Opgrader ressourcer

Sørg for, at dit miljø opfylder hardware- og softwarekravene. Følg derefter de understøttede opgraderingsmetoder.
  
- **Hardware-/softwarekrav til:** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Softwaregrænser og -begrænsninger for:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Oversigt over opgraderingsprocessen for:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Opret en SharePoint hybridløsning SharePoint online og lokalt miljø

Hvis svaret på dine overførselsbehov ligger mellem den selvkontrol, der tilbydes af det lokale miljø, og de lavere ejerskabsomkostninger i SharePoint Online, kan du forbinde SharePoint Server 2013- eller 2016-farme til SharePoint Online via hybrider. [Få mere at vide SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Hvis du beslutter, at en SharePoint Server-hybridfarm vil være en fordel for din virksomhed, skal du gøre dig bekendt med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint-farm og dit Microsoft 365-abonnement.
  
En god måde at se, hvordan det fungerer, er at oprette et Microsoft 365 udviklings-/testmiljø, som du kan konfigurere med [Test Lab-vejledninger](m365-enterprise-test-lab-guides.md). Når du får en prøveversion eller et købt Microsoft 365-abonnement, kan du oprette grupper af websteder, websteder og dokumentbiblioteker i SharePoint Online, som du kan overføre data til. Du kan overføre manuelt, ved hjælp af overførsels-API'en, eller, hvis du vil overføre indholdet på Mit websted OneDrive for Business, via hybridguiden.
  
> [!NOTE]
> Husk, at hvis du vil bruge hybridindstillingen, skal din SharePoint 2007-farm opgraderes i det lokale miljø til enten SharePoint Server 2013 eller SharePoint Server 2016.
  
## <a name="related-topics"></a>Relaterede emner

[Fejlfinding og genoptag opgradering (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[Fejlfinding af problemer med opgradering (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[Fejlfinding af problemer med databaseopgradering SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[Søg efter Microsoft-partnere for at hjælpe med opgraderingen](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressourcer, der kan hjælpe dig med at opgradere Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
