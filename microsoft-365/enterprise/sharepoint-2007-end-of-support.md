---
title: køreplan for ophør af support til SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Support til SharePoint Server 2007 ophører i oktober 2017. I denne artikel kan du få mere at vide om dine muligheder for opgradering, overførsel og support.
ms.openlocfilehash: 7f98e3652e2836a0c4193efbe33147fd09ced01e
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65771947"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>køreplan for ophør af support til SharePoint Server 2007

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Den **10. oktober 2017** ophørte Microsoft Office SharePoint Server 2007 med at yde support. Hvis du ikke har overført fra SharePoint Server 2007 til Microsoft 365 eller en nyere version af SharePoint Server i det lokale miljø, er det tid til at begynde at planlægge. Denne artikel indeholder ressourcer, der kan hjælpe dig med at overføre data til SharePoint Online eller opgradere din SharePoint Server i det lokale miljø.
  
## <a name="what-does-end-of-support-mean"></a>Hvad betyder *ophør af support* ?

SharePoint Server har som de fleste Microsoft-produkter en supportlivscyklus, hvor Microsoft leverer nye funktioner, fejlrettelser, sikkerhedsrettelser osv. Denne livscyklus varer typisk 10 år efter produktets første udgivelse. Slutningen af denne livscyklus er kendt som produktets ophør af support. Efter ophør af support leverer Microsoft ikke længere:
  
- Teknisk support til problemer, der kan opstå.
    
- Fejlrettelser til problemer, der kan påvirke serverens stabilitet og anvendelighed.
    
- Sikkerhedsrettelser til sikkerhedsrisici, der kan gøre serveren sårbar over for brud på sikkerheden.
    
- Tidszoneopdateringer.
    
Farmen SharePoint Server 2007 fungerer stadig efter den 10. oktober 2017, men der udgives ikke yderligere opdateringer, programrettelser eller rettelser til produktet, herunder sikkerhedsrettelser/rettelser. Microsoft Support har fuldt ud ændret sin supportindsats til nyere versioner af produktet. Da installationen ikke længere understøttes eller repareres, skal du opgradere produktet eller overføre vigtige data.
  
> [!TIP]
> Hvis du ikke allerede har planlagt en opgradering eller migrering, kan du se: [SharePoint migreringsmuligheder fra 2007, hvor du kan se](sharepoint-2007-migration-options.md) nogle eksempler på, hvor du skal begynde. Du kan også søge efter [Microsoft-partnere](https://go.microsoft.com/fwlink/?linkid=841249), der kan hjælpe med opgradering eller Microsoft 365 migrering (eller begge dele).
  
Du kan finde flere oplysninger om Office 2007-servere og ophør af support under Ressourcer, der [kan hjælpe dig med at opgradere fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>Hvad er mine muligheder?

Dit første stop bør være [webstedet for produktlivscyklus](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). Hvis du har et Microsoft-produkt i det lokale miljø, der er ved at blive ældre, skal du kontrollere slutdatoen for support, så du har et år eller deromkring for at planlægge en opgradering eller migrering. Når du vælger det næste trin, skal du overveje, hvilke produktfunktioner der er gode nok, bedre og bedst. Her er et eksempel: 
  
|**God**|**Bedre**|**Bedste**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint Hybrid  <br/> |SharePoint Server 2016  <br/> |
| | |SharePoint Hybrid  <br/> |
   
Hvis du vælger en "god nok"-indstilling, skal du snart begynde at planlægge endnu en opgradering, når overførslen fra SharePoint Server 2007 er fuldført. 

>[!NOTE] 
>Datoer for ophør af support kan ændres. Kontrollér [webstedet for produktlivscyklus](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>Hvor kan jeg gå hen nu?

SharePoint Server kan installeres i det lokale miljø på dine egne servere. Eller du kan bruge SharePoint Online, som er en onlinetjeneste, der er en del af Microsoft 365. Du kan vælge mellem følgende muligheder:
  
- Overfør til SharePoint Online.
    
- Opgrader SharePoint Server i det lokale miljø.
    
- Gør begge dele af ovenstående.
    
- Implementer en [SharePoint hybridløsning](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
    
Vær opmærksom på skjulte omkostninger, der er knyttet til vedligeholdelse af en serverfarm, vedligeholdelse eller overførsel af tilpasninger og opgradering af den hardware, SharePoint Server har brug for. Det er en fordel at have en SharePoint serverfarm i det lokale miljø, hvis det er nødvendigt. Men hvis du kører din farm på ældre SharePoint servere uden omfattende tilpasning, kan du drage fordel af migrering til SharePoint Online.
  
> [!IMPORTANT]
> Der er en anden mulighed, hvis indholdet i SharePoint 2007 sjældent bruges. Nogle SharePoint administratorer vælger at oprette et Microsoft 365 abonnement, oprette et nyt SharePoint Online-websted og derefter skære væk fra SharePoint 2007 rent og kun tage vigtige dokumenter til de nye SharePoint Online-websteder. Data kan derefter drænes fra SharePoint 2007 site i arkiver. Overvej, hvordan dine brugere arbejder med data fra din SharePoint 2007-installation. Der kan være kreative måder at administrere dine behov på.
  
|**SharePoint Online (SPO)**|**SharePoint Server i det lokale miljø**|
|:-----|:-----|
|Høje omkostninger i tid (plan/udførelse/bekræftelse)  <br/> |Høje omkostninger i tid (plan/udførelse/bekræftelse)  <br/> |
|Lavere omkostninger i fonde (ingen hardwarekøb)  <br/> |Højere omkostninger i fonde (hardware + udviklere/administratorer)  <br/> |
|Engangsomkostninger ved overførsel  <br/> |Engangsomkostninger gentaget pr. fremtidig migrering  <br/> |
|Lave samlede ejeromkostninger/vedligeholdelse  <br/> |Høje samlede ejeromkostninger/vedligeholdelse  <br/> |
   
Når du migrerer til Microsoft 365, vil engangsflytningen have tungere omkostninger på forhånd, mens du organiserer data og beslutter, hvad du vil tage til cloudmiljøet, og hvad du skal efterlade. Men fremtidige opgraderinger vil være automatiske, og du behøver ikke længere at administrere hardware- og softwareopdateringer. Desuden understøttes din farms oppetid af en [Microsoft-serviceniveauaftale (SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)).
  
### <a name="migrate-to-sharepoint-online"></a>Overfør til SharePoint Online

Sørg for, at SharePoint Online har alle de funktioner, du har brug for. Se [Microsoft 365 og Office 365 tjenestebeskrivelser](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
Du kan ikke overføre direkte fra SharePoint 2007 til SharePoint Online. Din flytning til SharePoint Online ville blive udført manuelt. Hvis du opgraderer til SharePoint Server 2013 eller SharePoint Server 2016, kan du bruge API'en til SharePoint migration (f.eks. til at overføre oplysninger til OneDrive for Business).
  
|**Online pro**|**Online con**|
|:-----|:-----|
|Microsoft leverer SPO-hardware og al hardwareadministration.  <br/> |Tilgængelige funktioner kan variere mellem SharePoint Server i det lokale miljø og SPO.  <br/> |
|Du er SharePoint administrator eller global administrator af dit abonnement og kan tildele administratorer til SPO-websteder.  <br/> |Nogle handlinger, der er tilgængelige for en farmadministrator i SharePoint Server i det lokale miljø, findes ikke eller er ikke nødvendigvis inkluderet i rollen SharePoint administrator i Microsoft 365.  <br/> |
|Microsoft anvender programrettelser, rettelser og opdateringer på underliggende hardware og software. <br/> |Da der ikke er adgang til det underliggende filsystem i tjenesten, er tilpasningen begrænset.  <br/> |
|Microsoft publicerer [serviceniveauaftaler](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) og bevæger sig hurtigt for at løse hændelser på tjenesteniveau. <br/> |Backup og gendannelse og andre gendannelsesmuligheder automatiseres af tjenesten i SharePoint Online. Sikkerhedskopier overskrives, hvis de ikke bruges. <br/> |
|Sikkerhedstest og justering af serverydeevne udføres løbende i tjenesten af Microsoft. <br/> |Ændringer af brugergrænsefladen og andre SharePoint funktioner installeres af tjenesten og skal muligvis slås til eller fra. <br/> |
|Microsoft 365 overholder mange branchestandarder: [Microsofts tilbud om overholdelse af angivne standarder](/compliance/regulatory/offering-home).  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) er begrænset hjælp til migrering.  <br/> Meget af opgraderingen vil være manuel eller via SPO Migration API, der er beskrevet i [SharePoint Online and OneDrive Migration Content Roadmap](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Microsoft Support-teknikere og datacentermedarbejdere har ikke ubegrænset administratoradgang til dit abonnement. <br/> |Der kan være ekstra omkostninger, hvis hardwaren skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis der kræves en sekundær farm til opgraderingen.  <br/> |
|Partnere kan hjælpe med engangsjobbet med at overføre dine data til SharePoint Online.  <br/> ||
|Onlineprodukter opdateres automatisk. Selvom funktioner kan frarådes, er der ingen reel ophør af support. <br/> ||
   
Hvis du har besluttet at oprette et nyt Microsoft 365 websted og manuelt overfører data til det efter behov, skal du kontrollere dine [Microsoft 365 muligheder](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Opgrader SharePoint Server i det lokale miljø

Du kan ikke springe versioner over i SharePoint opgraderinger. Opgraderinger forsvinder serielt:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
At gå fra SharePoint 2007 til SharePoint Server 2016 betyder en betydelig investering i tid og vil medføre omkostninger i hardware (SQL servere skal også opgraderes), software og administration. Tilpasninger skal opgraderes eller afbrydes.
  
> [!NOTE]
> Det er muligt at vedligeholde din SharePoint 2007-farm ved at installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til download og genupload af indhold). Men pas på nogle af faldgruberne ved manuelle flytninger, f.eks flytning af dokumenter, der erstatter den senest ændrede konto med aliasset for den konto, der udfører den manuelle flytning. Overvej også det arbejde, der skal udføres på forhånd, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Overvej på forhånd, hvilke data du kan flytte ind i lageret eller slette for at reducere virkningen af migreringen.
  
Det er vigtigt at rydde op i dit miljø, før du opgraderer. Vær sikker på, at din eksisterende farm fungerer, før du opgraderer, og helt sikkert før du tager den ud af drift!
  
Husk at gennemse de *understøttede og ikke-understøttede opgraderingsstier*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Hvis du har tilpasninger, er det vigtigt at have en plan for hvert trin i overførselsstien: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Pro i det lokale miljø**|**Con i det lokale miljø**|
|:-----|:-----|
|Fuld kontrol over alle aspekter af din SharePoint Farm fra serverhardwaren op.  <br/> |Alle pauser og rettelser er virksomhedens ansvar (du kan engagere betalt Microsoft Support, hvis dit produkt ikke er ophørt med support).  <br/> |
|Komplet funktionssæt med SharePoint Server i det lokale miljø med mulighed for at forbinde din farm i det lokale miljø til et SharePoint Online-abonnement via hybrid.  <br/> |Opgradering, programrettelser, sikkerhedsrettelser og al vedligeholdelse af SharePoint Server, der administreres i det lokale miljø.  <br/> |
|Fuld adgang til større tilpasning.  <br/> |[Microsofts tilbud om overholdelse af angivne standarder skal konfigureres](/compliance/regulatory/offering-home) manuelt i det lokale miljø.  <br/> |
|Sikkerhedstest og justering af serverydeevne udføres i dit lokale miljø (under din kontrol).  <br/> |Microsoft 365 kan gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø.  <br/> |
|Partnere kan hjælpe med at overføre data til den næste version af SharePoint Server (og videre).  <br/> |Dine SharePoint Server-websteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.  <br/> |
|Fuld kontrol over navngivningskonventioner, sikkerhedskopiering og gendannelse og andre gendannelsesmuligheder i SharePoint Server i det lokale miljø.  <br/> |SharePoint Server i det lokale miljø er følsom over for produktlivscyklusser.  <br/> |
   
### <a name="upgrade-resources"></a>Opgrader ressourcer

Sørg for, at dit miljø opfylder hardware- og softwarekrav, og følg derefter understøttede opgraderingsmetoder.
  
- **Hardware-/softwarekrav til**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Softwaregrænser og grænser for**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Oversigt over opgraderingsprocessen for**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Opret en SharePoint hybridløsning mellem SharePoint Online og det lokale miljø

Hvis svaret på dine behov for migrering ligger et sted mellem den selvkontrol, der tilbydes af det lokale miljø, og de lavere ejeromkostninger, der tilbydes af SharePoint Online, kan du oprette forbindelse SharePoint Server 2013- eller 2016-farme til SharePoint Online via hybrider. [Få mere at vide om SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
Hvis du beslutter dig for, at en hybrid-SharePoint Server-farm vil være til gavn for din virksomhed, kan du blive fortrolig med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint farm og dit Microsoft 365-abonnement.
  
| Mulighed | Beskrivelse |
|:-----|:-----|
[Microsofts tilbud om overholdelse af angivne standarder](/compliance/regulatory/offering-home)  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) er begrænset hjælp til migrering.  <br/> Meget af opgraderingen vil være manuel eller via SPO Migration API, der er beskrevet i [SharePoint Online and OneDrive Migration Content Roadmap](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|Microsoft Support-teknikere og medarbejdere i datacenteret har ikke ubegrænset administratoradgang til dit abonnement.<br/> |Der kan være ekstra omkostninger, hvis hardwareinfrastrukturen skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis der kræves en sekundær farm til opgradering.  <br/> |
|Partnere kan hjælpe med engangsjobbet med at overføre dine data til SharePoint Online.  <br/> ||
|Onlineprodukter opdateres automatisk på tværs af tjenesten. Selvom funktioner kan frarådes, er der ingen reel ophør af support.<br/> ||
   
Hvis du har besluttet at oprette et nyt Microsoft 365 websted og manuelt overfører data til det efter behov, skal du kontrollere dine [Microsoft 365 muligheder](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>Opgrader SharePoint Server i det lokale miljø

Du kan ikke springe versioner over i SharePoint opgraderinger. Opgraderinger forsvinder serielt:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
Hvis du vil gå fra SharePoint 2007 til SharePoint Server 2016, vil det betyde en betydelig investering i tid og vil medføre omkostninger til hardware (SQL servere skal også opgraderes), software og administration. Tilpasninger skal opgraderes eller afbrydes.
  
> [!NOTE]
> Det er muligt at vedligeholde din SharePoint 2007-farm ved at installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til download og genupload af indhold). Men pas på potentielle faldgruber ved manuelle flytninger, f.eks. flytning af dokumenter, der erstatter den senest ændrede konto med aliasset for den konto, der udfører den manuelle flytning, og det arbejde, der skal udføres på forhånd, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Overvej, hvilke data du kan flytte ind i lageret eller slette for at reducere virkningen af migreringen.
  
Ryd dit miljø før opgraderingen. Vær sikker på, at din eksisterende gård fungerer, før du opgraderer, og helt sikkert før du tager den ud af drift! 
  
Husk at gennemse de *understøttede og ikke-understøttede opgraderingsstier*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
Hvis du har *tilpasninger*, er det vigtigt, at du har en plan for opgraderingen for hvert trin i overførselsstien: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Pro i det lokale miljø**|**Con i det lokale miljø**|
|:-----|:-----|
|Fuld kontrol over alle aspekter af din SharePoint Farm fra serverhardwaren op.  <br/> |Alle pauser og rettelser er dit firmas ansvar. (Du kan engagere betalt Microsoft-support, hvis dit produkt ikke er ophørt med support).  <br/> |
|Komplet funktionssæt med SharePoint Server i det lokale miljø med mulighed for at forbinde din farm i det lokale miljø til et SharePoint Online-abonnement via hybrid.  <br/> |Opgradering, programrettelser, sikkerhedsrettelser og al vedligeholdelse af SharePoint Server, der administreres i det lokale miljø.  <br/> |
|Fuld adgang til større tilpasning.  <br/> |[Microsofts tilbud om overholdelse af angivne standarder skal konfigureres](/compliance/regulatory/offering-home) manuelt i det lokale miljø.  <br/> |
|Sikkerhedstest og justering af serverydeevne udføres i dit lokale miljø under din kontrol.  <br/> |Microsoft 365 kan gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø  <br/> |
|Partnere kan hjælpe med at overføre data til den næste version af SharePoint Server (og meget mere).  <br/> |Dine SharePoint Server-websteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.  <br/> |
|Fuld kontrol over navngivningskonventioner, sikkerhedskopiering og gendannelse og andre gendannelsesmuligheder i SharePoint Server i det lokale miljø.  <br/> |SharePoint Server i det lokale miljø er følsom over for produktlivscyklusser.  <br/> |
   
### <a name="upgrade-resources"></a>Opgrader ressourcer

Sørg for, at dit miljø opfylder hardware- og softwarekrav. Følg derefter de understøttede opgraderingsmetoder.
  
- **Hardware-/softwarekrav til:** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **Softwaregrænser og grænser for:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **Oversigt over opgraderingsprocessen for:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Opret en SharePoint hybridløsning mellem SharePoint Online og det lokale miljø

Hvis svaret på dine behov for migrering ligger et sted mellem den selvkontrol, der tilbydes af det lokale miljø, og de lavere ejeromkostninger, der tilbydes af SharePoint Online, kan du oprette forbindelse SharePoint Server 2013- eller 2016-farme til SharePoint Online via hybrider. [Få mere at vide om SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
Hvis du beslutter dig for, at en hybrid-SharePoint Server-farm vil være til gavn for din virksomhed, kan du blive fortrolig med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint farm og dit Microsoft 365-abonnement.
  
En god måde at se, hvordan dette fungerer, er at oprette et Microsoft 365 udviklings-/testmiljø, som du kan konfigurere med [Test Lab Guides](m365-enterprise-test-lab-guides.md). Når du har fået en prøveversion eller købt Microsoft 365 abonnement, kan du oprette grupper af websteder, websteder og dokumentbiblioteker i SharePoint Online, som du kan overføre data til. Du kan overføre manuelt ved hjælp af Overførsels-API'en eller via hybridguiden, hvis du vil overføre mit webstedsindhold til OneDrive for Business.
  
> [!NOTE]
> Husk, at hvis du vil bruge hybridindstillingen, skal din SharePoint 2007-farm opgraderes i det lokale miljø til enten SharePoint Server 2013 eller SharePoint Server 2016.
  
## <a name="related-topics"></a>Relaterede emner

[Foretag fejlfinding af og fortsæt opgradering (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[Foretag fejlfinding af opgraderingsproblemer (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[Foretag fejlfinding af problemer med databaseopgradering i SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[Søg efter Microsoft-partnere for at få hjælp til opgradering](https://go.microsoft.com/fwlink/?linkid=841249)
  
[Ressourcer, der kan hjælpe dig med at opgradere fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
