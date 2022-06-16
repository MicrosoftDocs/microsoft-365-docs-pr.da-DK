---
title: Opgradering fra SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Find oplysninger og ressourcer, der skal opgraderes fra SharePoint 2010 og SharePoint Server 2010. Support til begge ophører den 13. april 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: eba7c6739aef420bc90ef866dbd6f3becbccd8ff
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115955"
---
# <a name="upgrading-from-sharepoint-2010"></a>Opgradering fra SharePoint 2010

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Support til Microsoft SharePoint 2010 og SharePoint Server 2010 ophører **den 13. april 2021**. Denne artikel indeholder ressourcer, der kan hjælpe dig med at overføre dine eksisterende SharePoint Server 2010-data til SharePoint Online i Microsoft 365 eller opgradere dit lokale SharePoint Server 2010-miljø.

## <a name="what-is-end-of-support"></a>Hvad er *ophør af support*?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsrettelser osv. Efter slutdatoen for support holder produktet ikke op med at fungere, men Microsoft leverer ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser til problemer, der kan påvirke serverens stabilitet og anvendelighed.

- Sikkerhedsrettelser til sikkerhedsrisici, der kan gøre serveren sårbar over for brud på sikkerheden.

- Tidszoneopdateringer.

Det betyder, at der ikke vil være flere opdateringer, programrettelser eller rettelser til produktet (herunder sikkerhedsrettelser/rettelser). Microsoft Support har helt ændret sin supportindsats til nyere versioner.

Efterhånden som support til SharePoint Server 2010 ophører, skal du slette de data, du ikke længere har brug for, før du opgraderer produktet og overfører dine vigtige data.

> [!NOTE]
> En softwarelivscyklus varer typisk i ti år fra den første udgivelse. [Microsoft-løsningsudbydere](https://go.microsoft.com/fwlink/?linkid=841249) kan hjælpe dig med at opgradere til den næste version af softwaren eller migrere til Microsoft 365 migrering (eller begge dele). Sørg for, at du også er opmærksom på slutdatoer for support til vigtige underliggende teknologier, især for den version af Microsoft SQL Server du bruger med SharePoint. Du kan få flere oplysninger under [Fast livscykluspolitik](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>Planlægge

Kontrollér de datoer, der understøttes, slutter på [webstedet Produktlivscyklus](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). Planlæg dine opgraderinger eller migreringer med disse datoer i tankerne. Husk, at dit produkt *ikke holder op med at fungere* på den angivne dato. Men da installationen ikke længere repareres efter denne dato, skal du planlægge en problemfri overgang til den næste version af produktet.

Denne matrix hjælper med at afbilde et kursus blandt overførselsindstillinger:

|Ophør af supportprodukt|God |Bedste|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (i det lokale miljø)|SharePoint Online|
||hybrid af SharePoint Server 2013 med SharePoint Online|SharePoint Server 2016 (i det lokale miljø)|
|||SharePoint Cloud Hybrid Search|

Hvis du vælger en indstilling i den lave ende af skalaen (god), skal du begynde at planlægge endnu en opgradering kort efter overførslen fra SharePoint Server 2010.

Her er de tre veje, du kan gå for at undgå ophør af support til SharePoint Server 2010.

![SharePoint Server 2010-opgraderingsstier.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> Ophør af support til SharePoint Server 2010 og SharePoint Foundation 2010 er i øjeblikket planlagt til den 13. april 2021. Men sørg for at kontrollere [webstedet for produktlivscyklus](https://support.microsoft.com/lifecycle) for de mest aktuelle datoer.

## <a name="whats-next"></a>Hvad sker der derefter?

SharePoint Server 2013 og SharePoint Foundation 2013 kan installeres lokalt på dine egne servere. Eller du kan bruge SharePoint Online, som er en onlinetjeneste, der er en del af Microsoft 365. Du kan vælge at:

- Overfør til SharePoint Online.

- Opgrader SharePoint Server eller SharePoint Foundation i det lokale miljø.

- Gør begge dele af ovenstående.

- Implementer en [SharePoint hybridløsning](/sharepoint/hybrid/hybrid).

Overvej de skjulte omkostninger ved at vedligeholde en serverfarm, herunder vedligeholdelse eller overførsel af tilpasninger og opgradering af hardware. Hvis du har taget højde for disse faktorer, er det nemmere at opgradere i det lokale miljø. Hvis du kører din farm på ældre SharePoint servere uden omfattende tilpasning, kan du drage fordel af en planlagt migrering til SharePoint Online. I forbindelse med et SharePoint servermiljø i det lokale miljø kan du også overveje at flytte nogle data i SharePoint Online for at reducere administrationsomkostningerne for hardware.

> [!NOTE]
> SharePoint administratorer kan oprette et Microsoft 365 abonnement, oprette nye SharePoint onlinewebsteder og derefter fjerne SharePoint Server 2010 på en ren måde, så de kun henter vigtige dokumenter til de nye websteder. Derefter kan eventuelle resterende data tømmes fra webstedet SharePoint Server 2010 til arkiver i det lokale miljø.

|SharePoint Online|SharePoint Server i det lokale miljø|
|---|---|
|Høje omkostninger i tid (plan/udførelse/bekræftelse)|Høje omkostninger i tid (plan/udførelse/bekræftelse)|
|Lavere omkostninger i fonde (ingen hardwarekøb)|Højere omkostninger i fonde (hardwarekøb)|
|Engangsomkostninger ved overførsel|Engangsomkostninger gentaget pr. fremtidig migrering|
|Lave samlede ejeromkostninger/vedligeholdelse|Høje samlede ejeromkostninger/vedligeholdelse|

En engangsflytning til Microsoft 365 vil have en højere pris, mens du organiserer data og beslutter, hvad der skal sendes til cloudmiljøet, og hvad du skal efterlade. Men når dine data er migreret, vil fremtidige opgraderinger være automatiske, da du ikke længere behøver at administrere hardware- og softwareopdateringer. Og tidspunktet for farmens opdatering understøttes af en [Microsoft-serviceniveauaftale (SLA).](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)

### <a name="migrate-to-sharepoint-online"></a>Overfør til SharePoint Online

Sørg for, at SharePoint Online tilbyder alle de funktioner, du har brug for. Se [SharePoint tjenestebeskrivelse](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

Du kan ikke overføre direkte fra SharePoint Server 2010 (eller SharePoint Foundation 2010) til SharePoint Online. Så meget af migreringsarbejdet er manuelt. Men denne fase giver dig mulighed for at beskære data og websteder, der ikke længere er nødvendige før flytningen. Du kan arkivere andre data i lageret. 

Husk, at SharePoint Server 2010 og SharePoint Foundation 2010 ikke holder op med at arbejde, når supporten ophører. Administratorer kan derfor have en periode, hvor SharePoint stadig kører, hvis deres kunder glemmer at flytte nogle af deres data.

Hvis du opgraderer til SharePoint Server 2013 eller SharePoint Server 2016 og beslutter at overføre data til SharePoint Online, kan du bruge [API'en SharePoint migration](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) til at overføre oplysninger til OneDrive for Business.

|SharePoint Online-fordel|SharePoint Online ulempe|
|---|---|
|Microsoft leverer SPO-hardware og al hardwareadministration.|Tilgængelige funktioner kan variere mellem SharePoint Server i det lokale miljø og SPO.|
|Du er SharePoint administrator eller global administrator af dit abonnement og kan tildele administratorer til SPO-websteder.|Nogle handlinger, der er tilgængelige for en farmadministrator i SharePoint Server i det lokale miljø, findes ikke (eller er ikke nødvendige) i rollen SharePoint administrator i Microsoft 365. Men SharePoint administration, administration af gruppe af websteder og ejerskab af websteder er lokale for din organisation.|
|Microsoft anvender programrettelser, rettelser og opdateringer på underliggende hardware og software, herunder SQL servere, som SharePoint Online kører på.|Da der ikke er adgang til det underliggende filsystem i tjenesten, er tilpasningen begrænset.|
|Microsoft publicerer [serviceniveauaftaler](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) og bevæger sig hurtigt for at løse hændelser på tjenesteniveau.|Backup og gendannelse og andre gendannelsesmuligheder automatiseres af tjenesten i SharePoint Online. Sikkerhedskopier overskrives, hvis de ikke bruges.|
|Sikkerhedstest og justering af serverens ydeevne udføres løbende i tjenesten af Microsoft.|Ændringer af brugergrænsefladen og andre SharePoint funktioner installeres af tjenesten og skal muligvis slås til eller fra.|
|Microsoft 365 overholder mange branchestandarder: [Microsofts tilbud om overholdelse af angivne standarder](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) er begrænset hjælp til migrering.  <br/> Meget af opgraderingen vil være manuel eller via SPO Migration API, der er beskrevet i [SharePoint Online and OneDrive Migration Content Roadmap](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Microsoft Support-teknikere og medarbejdere i datacentre har ikke ubegrænset administratoradgang til dit abonnement.|Der kan være ekstra omkostninger, hvis hardwareinfrastrukturen skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis en sekundær farm er påkrævet til opgradering.|
|Løsningsudbydere kan hjælpe med engangsjobbet med at overføre dine data til SharePoint Online.|Det er ikke alle ændringer af SharePoint Online, der er inden for din kontrol. Efter migreringen kan designforskelle i menuer, biblioteker og andre funktioner midlertidigt påvirke anvendeligheden.|
|Onlineprodukter opdateres automatisk på tværs af tjenesten. Funktioner frarådes muligvis, men supportlivscyklussen ophører ikke.|Der er en livscyklus for ophør af support til SharePoint Server eller SharePoint Foundation samt underliggende SQL servere.|

Hvis du har besluttet at oprette et nyt Microsoft 365 websted og manuelt overfører data til det efter behov, skal du kontrollere dine [Microsoft 365 muligheder](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Opgrader SharePoint Server i det lokale miljø

Fra og med SharePoint Server 2019 skal opgraderinger gå *serielt*. Der er ingen måde at opgradere fra SharePoint Server 2010 til SharePoint Server 2016 eller til SharePoint 2019 direkte. Sti til seriel opgradering:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Det tager tid og planlægger at følge hele stien fra SharePoint 2010 til SharePoint Server 2016. Opgraderinger omfatter omkostninger til hardware (SQL servere skal også opgraderes), software og administration. Tilpasninger skal muligvis også opgraderes eller endda afbrydes. Sørg for at dokumentere vigtige tilpasninger, før du opgraderer din SharePoint Server-farm.

> [!NOTE]
> Det er muligt at vedligeholde din end-of-support-farm SharePoint 2010-farmen, installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til download og overførsel af indhold). Men der er potentielle faldgruber til disse manuelle flytninger, f.eks. dokumenter, der kommer fra 2010 med en aktuel senest ændret konto med aliasset for den konto, der foretager den manuelle flytning. Og noget arbejde skal udføres på forhånd, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Sørg for at rense dit miljø, før du opgraderer. Overvej, hvilke data du kan flytte til lager eller ikke længere har brug for. Dette kan reducere virkningen af migrering. Vær sikker på, at din eksisterende farm fungerer, før du opgraderer, og (helt sikkert), før du tager ud af drift!

Husk at gennemse de *understøttede og ikke-understøttede opgraderingsstier*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Hvis du har *tilpasninger*, er det vigtigt, at du planlægger for hvert trin i overførselsstien:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Fordel i det lokale miljø|Ulempe i det lokale miljø|
|---|---|
|Fuld kontrol over alle aspekter af din SharePoint Farm (og dens SQL) fra serverhardwaren op.|Alle pauser og rettelser er dit firmas ansvar. Men du kan engagere betalt Microsoft Support, hvis dit produkt ikke er ophørt med support.|
|Komplet funktionssæt med SharePoint Server i det lokale miljø med mulighed for at forbinde din farm i det lokale miljø til et SharePoint Online-abonnement via hybrid.|Opgradering, programrettelser, sikkerhedsrettelser, hardwareopgraderinger og al vedligeholdelse af SharePoint Server og dens SQL farm administreres i det lokale miljø.|
|Fuld adgang for at få større tilpasningsmuligheder end med SharePoint Online.|[Microsofts tilbud om overholdelse af angivne standarder skal konfigureres](/compliance/regulatory/offering-home) manuelt i det lokale miljø.|
|Sikkerhedstest og justering af serverydeevne udføres i dit lokale miljø under din kontrol.|Microsoft 365 kan gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server lokalt.|
|Løsningsudbydere kan hjælpe med at overføre data til den næste version af SharePoint Server (og nyere).|Dine SharePoint Server-websteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.|
|Fuld kontrol over navngivningskonventioner og sikkerhedskopiering og gendannelse samt andre gendannelsesmuligheder i SharePoint Server i det lokale miljø.|SharePoint Server i det lokale miljø er følsom over for produktlivscyklusser.|

### <a name="upgrade-resources"></a>Opgrader ressourcer

Begynd med at sammenligne hardware- og softwarekrav. Hvis dit aktuelle miljø ikke opfylder de grundlæggende krav, skal du muligvis opgradere hardwaren i farmen eller de SQL servere først. 

Du kan beslutte at flytte nogle af dine websteder til "evergreen" hardware SharePoint Online. Når du har foretaget din vurdering, skal du følge understøttede opgraderingsstier og -metoder.

- *Hardware-/softwarekrav til:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Softwaregrænser og grænser for:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)

- *Oversigt over opgraderingsprocessen for:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>Opret en hybridløsning med SharePoint Online og SharePoint Server i det lokale miljø

En hybridinstallation giver det bedste fra både det lokale miljø og online til nogle overførselsbehov. Du kan oprette forbindelse SharePoint Server 2013-, 2016- eller 2019-farme med SharePoint Online for at oprette en SharePoint hybrid: [Få mere at vide om SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

Hvis en hybrid SharePoint Server-farm er dit mål for migrering, skal du finde ud af, hvilke websteder og brugere der skal flytte online, og hvilke der skal forblive i det lokale miljø. Denne beslutning kan hjælpe dig med at rangere indholdet af din SharePoint serverfarm som høj, mellem eller lav indvirkning på din virksomhed. Du skal muligvis kun dele brugerkonti til logon og SharePoint Server-søgeindekset med SharePoint Online. Men denne faktor er muligvis ikke klar, før du ser på, hvordan dine websteder bruges. Hvis din virksomhed på et senere tidspunkt beslutter at overføre alt dit indhold til SharePoint Online, kan du flytte alle resterende konti og data online og tage farmen i det lokale miljø ud af drift. Administrationen/administrationen af den SharePoint farm sker via Microsoft 365 konsoller fra dette tidspunkt.

Sørg for at blive fortrolig med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint farm og dit Microsoft 365-abonnement.

|Mulighed|Beskrivelse|
|---|---|
|[Microsofts tilbud om overholdelse af angivne standarder](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) er begrænset hjælp til migrering.<br/><br/> Meget af opgraderingen vil være manuel eller via SPO Migration API, der er beskrevet i [SharePoint Online and OneDrive Migration Content Roadmap](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|Microsoft Support-teknikere og medarbejdere i datacentre har ikke ubegrænset administratoradgang til dit abonnement.|Der kan være yderligere omkostninger, hvis hardwareinfrastrukturen skal opgraderes for at understøtte den nyere version af SharePoint, eller hvis en sekundær farm er påkrævet.|
|Partnere kan hjælpe med engangsjobbet med at overføre dine data til SharePoint Online.||
|Onlineprodukter opdateres automatisk på tværs af tjenesten. Funktioner frarådes muligvis, men der er ingen reel ophør af support.||

Hvis du har besluttet at oprette et nyt Microsoft 365 websted og manuelt overføre data til det efter behov, skal du kontrollere dine [Microsoft 365 muligheder](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>Opgrader SharePoint Server i det lokale miljø

Du kan ikke springe versioner over i SharePoint opgraderinger. Det betyder, at opgraderinger går serielt:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

Hvis du vil tage hele vejen fra SharePoint 2007 til SharePoint Server 2016, vil det betyde en betydelig investering i tid og vil omfatte hardware (SQL servere skal også opgraderes), software og administrationsomkostninger. Tilpasninger skal opgraderes eller afbrydes i henhold til funktionens kritiskhed.

> [!NOTE]
> Det er muligt at vedligeholde din SharePoint 2007-farm ved at installere en SharePoint Server 2016-farm på ny hardware (så de separate farme kører side om side) og derefter planlægge og udføre en manuel overførsel af indhold (f.eks. til download og genupload af indhold). Men der er nogle ulemper ved disse manuelle flytninger, f.eks. flytning af dokumenter, der erstatter den senest ændrede konto med aliasset for den konto, der foretager den manuelle flytning. Og meget arbejde skal udføres på forhånd, f.eks. genskabe websteder, underordnede websteder, tilladelser og listestrukturer. Under alle omstændigheder skal du overveje, hvilke data du kan flytte ind i lageret eller ikke længere har brug for for at reducere virkningen af migreringen.

Sørg for at rense dit miljø før opgraderingen. Vær sikker på, at din eksisterende farm fungerer, før du opgraderer, og helt sikkert før du tager den ud af drift!

Husk at gennemse de *understøttede og ikke-understøttede opgraderingsstier*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

Hvis du har *tilpasninger*, er det vigtigt at planlægge opgraderingen for hvert trin i overførselsstien:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|Pro i det lokale miljø|Con i det lokale miljø|
|---|---|
|Fuld kontrol over alle aspekter af din SharePoint Farm fra serverhardwaren op.|Alle pauser og rettelser er dit firmas ansvar. Men du kan engagere betalt Microsoft Support, hvis dit produkt ikke er ophørt med support.|
|Komplet funktionssæt med SharePoint Server i det lokale miljø med mulighed for at forbinde din farm i det lokale miljø til et SharePoint Online-abonnement via hybrid.|Opgradering, programrettelser, sikkerhedsrettelser og al vedligeholdelse af SharePoint Server, der administreres i det lokale miljø.|
|Fuld adgang til større tilpasning.|[Microsofts tilbud om overholdelse af angivne standarder skal konfigureres](/compliance/regulatory/offering-home) manuelt i det lokale miljø.|
|Sikkerhedstest og justering af serverydeevnen udføres i dit lokale miljø under din kontrol.|Microsoft 365 kan gøre funktioner tilgængelige for SharePoint Online, der ikke fungerer sammen med SharePoint Server i det lokale miljø.|
|Partnere kan hjælpe med at overføre data til den næste version af SharePoint Server (og meget mere).|Dine SharePoint Server-websteder bruger ikke automatisk [SSL/TLS-certifikater](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016), som det ses i SharePoint Online.|
|Fuld kontrol over navngivningskonventioner og sikkerhedskopiering og gendannelse samt andre gendannelsesmuligheder i SharePoint Server i det lokale miljø.|SharePoint Server i det lokale miljø er følsom over for produktlivscyklusser.|

### <a name="upgrade-resources"></a>Opgrader ressourcer

Begynd med at vide, at du opfylder hardware- og softwarekrav, og følg derefter understøttede opgraderingsmetoder.

- *Hardware-/softwarekrav til*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *Softwaregrænser og grænser for*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)

- *Oversigt over opgraderingsprocessen for*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>Opret en SharePoint hybridløsning mellem SharePoint Online og det lokale miljø

Hvis svaret på dine behov for migrering ligger et sted mellem det kontrolelement, der tilbydes af det lokale miljø, og de lavere ejeromkostninger, der tilbydes af SharePoint Online, kan du oprette forbindelse mellem SharePoint Server 2013- eller 2016-farme og SharePoint Online via hybrider. [Få mere at vide om SharePoint hybridløsninger](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

Hvis du beslutter dig for, at en hybrid-SharePoint Server-farm vil være til gavn for din virksomhed, kan du blive fortrolig med de eksisterende typer hybrider, og hvordan du konfigurerer forbindelsen mellem din lokale SharePoint farm og dit Microsoft 365-abonnement.

Det kan være en god idé at oprette et Microsoft 365 udviklings-/testmiljø, som du kan konfigurere med [Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md). Når du har fået en prøveversion eller købt Microsoft 365 abonnement, kan du oprette grupper af websteder, websteder og dokumentbiblioteker i SharePoint Online, som du kan overføre data til. Du kan overføre manuelt ved hjælp af Overførsels-API'en eller via hybridguiden, hvis du vil overføre mit webstedsindhold til OneDrive for Business.

> [!NOTE]
> Hvis du vil bruge hybridindstillingen, skal din SharePoint Server 2010-farm først opgraderes i det lokale miljø til SharePoint Server 2013 eller 2016. SharePoint Foundation 2010 og SharePoint Foundation 2013 understøtter ikke hybride forbindelser med SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Oversigt over indstillinger for Office 2010-klient og -servere og Windows 7

Du kan se en visuel oversigt over indstillingerne for opgradering, migrering og flytning til cloudmiljøet for Office 2010-klienter og -servere og Windows 7 i [slutningen af supportplakaten](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Ophør af support til Office 2010 klienter og servere og Windows 7 plakat.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Denne plakat illustrerer de forskellige veje, du kan gå for at undgå Office 2010 klient- og serverprodukter og Windows 7 ophør af support, med foretrukne stier og indstillingsunderstøttelser i Microsoft 365 Enterprise fremhævet.

Du kan også [downloade](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) denne plakat og udskrive den i letter-, legal- eller tabloid-format (11 x 17).

## <a name="related-articles"></a>Relaterede artikler

[Ressourcer, der kan hjælpe dig med at opgradere fra Office 2007- eller 2010-servere og -klienter](upgrade-from-office-2010-servers-and-products.md)

[Oversigt over opgraderingsprocessen fra SharePoint 2010 til SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[Bedste praksis for opgradering fra SharePoint 2010 til SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[Foretag fejlfinding af problemer med databaseopgradering i SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[Søg efter Microsoft-løsningsudbydere for at få hjælp til opgraderingen](https://go.microsoft.com/fwlink/?linkid=841249)

[Opdateret politik for produktservicering for SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[Opdateret politik for produktservicering for SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
