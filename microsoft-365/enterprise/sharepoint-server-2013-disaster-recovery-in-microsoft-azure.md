---
title: It-katastrofeberedskab i SharePoint Server 2013 i Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: scotv
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Deployment
- seo-marvel-apr2020
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: I denne artikel beskrives det, hvordan du bruger Azure til at oprette et it-katastrofeberedskabsmiljø til din lokale SharePoint farm.
ms.openlocfilehash: 1b1951e70cfbecc0f6586e68d7142bc26fb6252f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077417"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>It-katastrofeberedskab i SharePoint Server 2013 i Microsoft Azure

 Ved hjælp af Azure kan du oprette et it-katastrofeberedskabsmiljø til din lokale SharePoint farm. I denne artikel beskrives det, hvordan du designer og implementerer denne løsning.

 **Se videoen SharePoint Server 2013–it-katastrofeberedskab**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]

 Når katastrofen rammer dit SharePoint lokale miljø, er din vigtigste prioritet at få systemet til at køre igen hurtigt. It-katastrofeberedskab med SharePoint er hurtigere og nemmere, når der allerede kører et sikkerhedskopieringsmiljø i Microsoft Azure. I denne video forklares de vigtigste begreber i et SharePoint varmt failovermiljø og supplerer de komplette oplysninger, der er tilgængelige i denne artikel.

Brug denne artikel med følgende løsningsmodel: **SharePoint it-katastrofeberedskab i Microsoft Azure**.

[![SharePoint it-katastrofeberedskabsproces til Azure.](../media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)

 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)

## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Brug Azure Infrastructure Services til it-katastrofeberedskab

Mange organisationer har ikke et it-katastrofeberedskabsmiljø til SharePoint, hvilket kan være dyrt at bygge og vedligeholde i det lokale miljø. Azure Infrastructure Services indeholder overbevisende muligheder for miljøer til it-katastrofeberedskab, der er mere fleksible og billigere end alternativerne i det lokale miljø.

Fordelene ved at bruge Azure Infrastructure Services omfatter:

- **Færre dyre ressourcer** Vedligehold og betal for færre ressourcer end it-katastrofeberedskabsmiljøer i det lokale miljø. Antallet af ressourcer afhænger af, hvilket katastrofeberedskabsmiljø du vælger: koldt standby, varmt standby eller varmt standby.

- **Bedre ressourcefleksibilitet** I tilfælde af en katastrofe kan du nemt skalere dit genoprettelses-SharePoint farm ud for at opfylde belastningskravene. Skaler ind, når du ikke længere har brug for ressourcerne.

- **Lavere datacenterforpligtelse** Brug Azure Infrastructure Services i stedet for at investere i et sekundært datacenter i et andet område.

Der er mindre komplekse muligheder for organisationer, der lige er startet med it-katastrofeberedskab, og avancerede muligheder for organisationer med krav til høj robusthed. Definitionerne for kolde, varme og varme standbymiljøer er lidt anderledes, når miljøet hostes på en cloudplatform. I følgende tabel beskrives disse miljøer til oprettelse af en SharePoint genoprettelsesfarm i Azure.

**Tabel: Genoprettelsesmiljøer**

|Type genoprettelsesmiljø|Beskrivelse|
|---|---|
|Hot|En farm i fuld størrelse klargøres, opdateres og kører på standby.|
|Varm|Farmen er bygget, og virtuelle maskiner kører og opdateres. <br/> Genoprettelse omfatter tilknytning af indholdsdatabaser, klargøring af tjenesteprogrammer og gennemsøgning af indhold. <br/> Farmen kan være en mindre version af produktionsfarmen og derefter skaleres ud for at betjene hele brugerbasen.|
|Kolde|Farmen er fuldt bygget, men de virtuelle maskiner stoppes. <br/> Vedligeholdelse af miljøet omfatter fra tid til anden at starte de virtuelle maskiner, reparere, opdatere og bekræfte miljøet. <br/> Start det fulde miljø i tilfælde af en katastrofe.|

Det er vigtigt at evaluere organisationens målsætninger for genoprettelsestid og målsætninger for genoprettelsespunktet. Disse krav bestemmer, hvilket miljø der er den mest passende investering for din organisation.

Vejledningen i denne artikel beskriver, hvordan du implementerer et varmt standbymiljø. Du kan også tilpasse den til et koldt standbymiljø, selvom du skal følge yderligere procedurer for at understøtte denne type miljø. I denne artikel beskrives det ikke, hvordan du implementerer et varmt standby-miljø.

Du kan finde flere oplysninger om løsninger til it-katastrofeberedskab [under Koncepter for høj tilgængelighed og it-katastrofeberedskab i SharePoint 2013](/SharePoint/administration/high-availability-and-disaster-recovery-concepts) og [Vælg en strategi for it-katastrofeberedskab for SharePoint 2013](/SharePoint/administration/plan-for-disaster-recovery).

## <a name="solution-description"></a>Beskrivelse af løsning

Den varme standby-løsning til it-katastrofeberedskab kræver følgende miljø:

- En produktionsfarm i det lokale miljø SharePoint

- En genoprettelses-SharePoint-farm i Azure

- En websted til websted-VPN-forbindelse mellem de to miljøer

Følgende figur illustrerer disse tre elementer.

**Figur: Elementer i en varm standbyløsning i Azure**

![Elementer i en SharePoint varm standbyløsning i Azure.](../media/AZarch-AZWarmStndby.png)

SQL Server logforsendelse med DFSR (Distributed File System Replication) bruges til at kopiere databasesikkerhedskopieringer og transaktionslogge til genoprettelsesfarmen i Azure:

- DFSR overfører logge fra produktionsmiljøet til genoprettelsesmiljøet. I et WAN-scenarie er DFSR mere effektiv end at sende loggene direkte til den sekundære server i Azure.

- Logge afspilles igen til SQL Server i genoprettelsesmiljøet i Azure.

- Du vedhæfter ikke SharePoint indholdsdatabaser, der er leveret logført, i genoprettelsesmiljøet, før der udføres en gendannelsesøvelse.

Udfør følgende trin for at gendanne farmen:

1. Stop logforsendelse.

2. Stop med at acceptere trafik til den primære farm.

3. Afspil de endelige transaktionslogge igen.

4. Vedhæft indholdsdatabaserne til farmen.

5. Gendan tjenesteprogrammer fra de replikerede tjenestedatabaser.

6. Opdater DNS-poster (Domain Name System), så de peger på genoprettelsesfarmen.

7. Start en fuld gennemsøgning.

Vi anbefaler, at du afprøver disse trin regelmæssigt og dokumenterer dem for at sikre, at din livegendannelse kører problemfrit. Det kan tage noget tid at vedhæfte indholdsdatabaser og gendanne tjenesteprogrammer og typisk foretage manuel konfiguration.

Når der er udført en gendannelse, indeholder denne løsning de elementer, der er angivet i følgende tabel.

**Tabel: Målsætninger for løsningsgendannelse**

|Element|Beskrivelse|
|---|---|
|Websteder og indhold|Websteder og indhold er tilgængelige i genoprettelsesmiljøet.|
|En ny forekomst af søgning|I denne varme standbyløsning gendannes søgningen ikke fra søgedatabaser. Søgekomponenter i genoprettelsesfarmen konfigureres på samme måde som muligt i produktionsfarmen. Når webstederne og indholdet er gendannet, startes en fuld gennemsøgning for at genopbygge søgeindekset. Du behøver ikke at vente på, at gennemsøgningen fuldføres for at gøre webstederne og indholdet tilgængeligt.|
|Tjenester|Tjenester, der lagrer data i databaser, gendannes fra de databaser, der er leveret af logfilen. Tjenester, der ikke gemmer data i databaser, startes ganske enkelt. <br/> Det er ikke alle tjenester med databaser, der skal gendannes. Følgende tjenester behøver ikke at blive gendannet fra databaser og kan blot startes efter failover: <br/> Indsamling af statistik- og tilstandsdata <br/> Tilstandstjeneste <br/> Word automation <br/> Alle andre tjenester, der ikke bruger en database|

Du kan arbejde sammen med Microsoft Consulting Services (MCS) eller en partner for at løse mere komplekse genoprettelsesmål. Disse opsummeres i følgende tabel.

**Tabel: Andre elementer, der kan håndteres af MCS eller en partner**

|Element|Beskrivelse|
|---|---|
|Synkroniserer brugerdefinerede farmløsninger|Ideelt set er konfigurationen af genoprettelsesfarmen identisk med produktionsfarmen. Du kan samarbejde med en konsulent eller partner om at evaluere, om brugerdefinerede farmløsninger replikeres, og om processen er på plads for at holde de to miljøer synkroniserede.|
|Forbindelser til datakilder i det lokale miljø|Det er muligvis ikke praktisk at replikere forbindelser til back end-datasystemer, f.eks. BDC-forbindelser (backup domænecontrollere) og søgeindholdskilder.|
|Søgegendannelsesscenarier|Da udrulninger af virksomhedssøgninger har en tendens til at være ret entydige og komplekse, kræver det en større investering at gendanne søgning fra databaser. Du kan samarbejde med en konsulent eller partner om at identificere og implementere søgegendannelsesscenarier, som din organisation kan kræve.|

I vejledningen i denne artikel forudsættes det, at farmen i det lokale miljø allerede er designet og installeret.

## <a name="detailed-architecture"></a>Detaljeret arkitektur

Ideelt set er konfigurationen af genoprettelsesfarmen i Azure identisk med produktionsfarmen i det lokale miljø, herunder følgende:

- Den samme repræsentation af serverroller

- Den samme konfiguration af tilpasninger

- Den samme konfiguration af søgekomponenter

Miljøet i Azure kan være en mindre version af produktionsfarmen. Hvis du planlægger at udskalere genoprettelsesfarmen efter failover, er det vigtigt, at hver type serverrolle repræsenteres i første omgang.

Nogle konfigurationer er muligvis ikke praktiske at replikere i failovermiljøet. Sørg for at teste failoverprocedurerne og miljøet for at sikre, at failoverfarmen leverer det forventede tjenesteniveau.

Denne løsning foreskriver ikke en bestemt topologi for en SharePoint farm. Denne løsning fokuserer på at bruge Azure til failoverfarmen og til at implementere logforsendelse og DFSR mellem de to miljøer.

### <a name="warm-standby-environments"></a>Varme standbymiljøer

I et varmt standbymiljø kører alle virtuelle maskiner i Azure-miljøet. Miljøet er klar til en failover-øvelse eller -hændelse.

Følgende figur illustrerer en løsning til it-katastrofeberedskab fra en lokal SharePoint farm til en Azure-baseret SharePoint-farm, der er konfigureret som et varmt standbymiljø.

**Figur: Topologi og vigtige elementer i en produktionsfarm og en varm standbygenvindingsfarm**

![Topologi for en SharePoint farm og en varm standby-farm.](../media/AZarch-AZWarmStndby.png)

I dette diagram:

- To miljøer er illustreret side om side: farmen i det lokale miljø SharePoint og den varme standbyfarm i Azure.

- Hvert miljø indeholder et filshare.

- Hver farm indeholder fire niveauer. For at opnå høj tilgængelighed omfatter hvert niveau to servere eller virtuelle maskiner, der er konfigureret identisk for en bestemt rolle, f.eks. front end-tjenester, distribueret cache, back end-tjenester og databaser. Det er ikke vigtigt i denne illustration at fremhæve bestemte komponenter. De to farme er konfigureret identisk.

- Det fjerde niveau er databaseniveauet. Logforsendelse bruges til at kopiere logfiler fra den sekundære databaseserver i det lokale miljø til filsharet i det samme miljø.

- DFSR kopierer filer fra filsharet i det lokale miljø til filsharet i Azure-miljøet.

- Log shipping genafspiller loggene fra filsharet i Azure-miljøet til den primære replika i tilgængelighedsgruppen SQL Server AlwaysOn i genoprettelsesmiljøet.

### <a name="cold-standby-environments"></a>Kolde standbymiljøer

I et koldt standbymiljø kan de fleste af de virtuelle maskiner på SharePoint farm lukkes. Vi anbefaler, at du af og til starter de virtuelle maskiner, f.eks. hver anden uge eller én gang om måneden, så hver virtuelle maskine kan synkronisere med domænet. Følgende virtuelle maskiner i Azure-genoprettelsesmiljøet skal forblive kørende for at sikre kontinuerlig drift af logforsendelse og DFSR:

- Filsharet

- Den primære databaseserver

- Mindst én virtuel maskine, der kører Windows Server Active Directory-domæneservices og DNS

Følgende figur viser et Azure-failovermiljø, hvor den virtuelle maskine til fildeling og den primære SharePoint virtuelle databasemaskine kører. Alle andre SharePoint virtuelle maskiner stoppes. Den virtuelle maskine, der kører Windows Server Active Directory og DNS, vises ikke.

**Figur: Kold standby-genoprettelsesfarm med kørende virtuelle maskiner**

![Elementer i en SharePoint kold standbyløsning i Azure.](../media/AZarch-AZColdStndby.png)

Efter failover til et koldt standbymiljø startes alle virtuelle maskiner, og metoden for at opnå høj tilgængelighed af databaseserverne skal konfigureres, f.eks. SQL Server AlwaysOn-tilgængelighedsgrupper.

Hvis der implementeres flere lagergrupper (databaser er fordelt på mere end ét SQL Server sæt med høj tilgængelighed), skal den primære database for hver lagergruppe køre for at acceptere de logge, der er knyttet til dens lagergruppe.

### <a name="skills-and-experience"></a>Færdigheder og erfaring

Der bruges flere teknologier i denne løsning til it-katastrofeberedskab. For at sikre at disse teknologier interagerer som forventet, skal hver komponent i det lokale miljø og Azure-miljøet installeres og konfigureres korrekt. Vi anbefaler, at den person eller det team, der konfigurerer denne løsning, har en stærk arbejdsviden om og praktiske færdigheder med de teknologier, der er beskrevet i følgende artikler:

- [DFS-replikeringstjenester (Distributed File System)](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))

- [WSFC (Windows Server Failover Clustering) med SQL Server](/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)

- [AlwaysOn-tilgængelighedsgrupper (SQL Server)](/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)

- [Sikkerhedskopiér og gendan SQL Server databaser](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)

- [SharePoint Server 2013-installation og -farminstallation](/SharePoint/install/installation-and-configuration-overview)

- [Microsoft Azure](/azure/)

Endelig anbefaler vi scriptingfærdigheder, som du kan bruge til at automatisere opgaver, der er knyttet til disse teknologier. Det er muligt at bruge de tilgængelige brugergrænseflader til at udføre alle de opgaver, der er beskrevet i denne løsning. En manuel tilgang kan dog være tidskrævende, og der kan opstå fejl, og den giver uoverensstemmende resultater.

Ud over Windows PowerShell findes der også Windows PowerShell biblioteker til SQL Server, SharePoint Server og Azure. Glem ikke T-SQL, hvilket også kan hjælpe med at reducere den tid, det tager at konfigurere og vedligeholde dit it-katastrofeberedskabsmiljø.

## <a name="disaster-recovery-roadmap"></a>Oversigt over it-katastrofeberedskab

![Visuel repræsentation af køreplanen for SharePoint it-katastrofeberedskab.](../media/Azure-DRroadmap.png)

Denne oversigt forudsætter, at du allerede har en SharePoint Server 2013-farm, der er udrullet i produktionen.

**Tabel: Oversigt over it-katastrofeberedskab**

|Fase|Beskrivelse|
|---|---|
|Fase 1|Design it-katastrofeberedskabsmiljøet.|
|Fase 2|Opret det virtuelle Azure-netværk og VPN-forbindelsen.|
|Fase 3|Udrul Windows Active Directory og Domænenavnstjenester til det virtuelle Azure-netværk.|
|Fase 4|Udrul den SharePoint genoprettelsesfarm i Azure.|
|Fase 5|Konfigurer DFSR mellem farmene.|
|Fase 6|Konfigurer logforsendelse til genoprettelsesfarmen.|
|Fase 7|Valider løsninger til failover og genoprettelse. Dette omfatter følgende procedurer og teknologier: <br/> Stop logforsendelse. <br/> Gendan sikkerhedskopierne. <br/> Gennemsøg indhold. <br/> Gendan tjenester. <br/> Administrer DNS-poster.|

## <a name="phase-1-design-the-disaster-recovery-environment"></a>Fase 1: Design it-katastrofeberedskabsmiljøet

Brug vejledningen i [Microsoft Azure Arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) til at designe it-katastrofeberedskabsmiljøet, herunder SharePoint-farmen. Du kan bruge grafikken i [SharePoint It-løsning til it-katastrofeberedskab i Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio-filen til at starte designprocessen. Vi anbefaler, at du designer hele miljøet, før du begynder at arbejde i Azure-miljøet.

Ud over vejledningen i [Microsoft Azure Arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) til design af det virtuelle netværk, VPN-forbindelse, Active Directory og SharePoint farm, skal du sørge for at føje en fildelingsrolle til Azure-miljøet.

For at understøtte logforsendelse i en løsning til it-katastrofeberedskab føjes der en virtuel maskine til fildeling til det undernet, hvor databaserollerne er placeret. Filsharet fungerer også som den tredje node i et node flertal for SQL Server AlwaysOn-tilgængelighedsgruppen. Dette er den anbefalede konfiguration for en standardfarm SharePoint, der bruger SQL Server AlwaysOn-tilgængelighedsgrupper.

> [!NOTE]
> Det er vigtigt at gennemse forudsætningerne for, at en database kan deltage i en SQL Server AlwaysOn-tilgængelighedsgruppe. Du kan få flere oplysninger under [Forudsætninger, begrænsninger og Anbefalinger for AlwaysOn-tilgængelighedsgrupper](/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability).

**Figur: Placering af en filserver, der bruges til en løsning til it-katastrofeberedskab**

![Viser en VM til fildeling, der er føjet til den samme cloudtjeneste, som indeholder SharePoint databaseserverrollerne.](../media/AZenv-FSforDFSRandWSFC.png)

I dette diagram føjes en virtuel maskine til fildeling til det samme undernet i Azure, der indeholder databaseserverrollerne. Føj ikke den virtuelle maskine til fildeling til et tilgængelighedssæt med andre serverroller, f.eks. rollerne SQL Server.

Hvis du er bekymret for den høje tilgængelighed af loggene, kan du overveje at benytte en anden fremgangsmåde ved at bruge [SQL Server sikkerhedskopiering og gendannelse med Azure Blob Storage Service](/sql/relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service). Dette er en ny funktion i Azure, der gemmer logge direkte på en Blob Storage URL-adresse. Denne løsning indeholder ikke vejledning i brug af denne funktion.

Når du designer genoprettelsesfarmen, skal du huske på, at et vellykket it-katastrofeberedskabsmiljø nøjagtigt afspejler den produktionsfarm, du vil genoprette. Størrelsen på genoprettelsesfarmen er ikke det vigtigste i genoprettelsesfarmens design, udrulning og test. Skalering af farmen varierer fra organisation til organisation baseret på forretningskrav. Det kan være muligt at bruge en nedskaleret farm til en kort afbrydelse, eller indtil ydeevnen og kapaciteten kræver, at du skalerer farmen.

Konfigurer genoprettelsesfarmen så identisk som muligt i forhold til produktionsfarmen, så den opfylder dine serviceniveauaftalekrav og leverer den funktionalitet, du har brug for til at understøtte din virksomhed. Når du designer it-katastrofeberedskabsmiljøet, skal du også se på din proces til administration af ændringer for dit produktionsmiljø. Vi anbefaler, at du udvider ændringsstyringsprocessen til genoprettelsesmiljøet ved at opdatere genoprettelsesmiljøet med samme interval som produktionsmiljøet. Som en del af processen til administration af ændringer anbefaler vi, at du vedligeholder en detaljeret oversigt over farmens konfiguration, programmer og brugere.

## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Fase 2: Opret det virtuelle Azure-netværk og vpn-forbindelsen

[Forbind et netværk i det lokale miljø til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) viser dig, hvordan du planlægger og installerer det virtuelle netværk i Azure, og hvordan du opretter VPN-forbindelsen. Følg vejledningen i emnet for at fuldføre følgende procedurer:

- Planlæg det private IP-adresseområde for Virtual Network.

- Planlæg ændringer af distributionsinfrastrukturen for Virtual Network.

- Planlæg firewallregler for trafik til og fra VPN-enheden i det lokale miljø.

- Opret det virtuelle netværk på tværs af det lokale miljø i Azure.

- Konfigurer distribution mellem netværket i det lokale miljø og Virtual Network.

## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Fase 3: Udrul Active Directory- og Domænenavnstjenester til det virtuelle Azure-netværk

Denne fase omfatter udrulning af både Windows Server Active Directory og DNS til Virtual Network i et hybridscenarie som beskrevet i [Microsoft Azure Arkitekturer for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) og som vist i følgende figur.

**Figur: Konfiguration af Hybrid Active Directory-domæne**

![To virtuelle maskiner, der er installeret på det virtuelle Azure-netværk, og undernettet SharePoint Farm er replikadomænecontrollere og DNS-servere.](../media/AZarch-HyADdomainConfig.png)

I illustrationen udrulles to virtuelle maskiner på det samme undernet. Disse virtuelle maskiner er hver især vært for to roller: Active Directory og DNS.

Før du installerer Active Directory i Azure, skal du læse [Retningslinjer for installation af Windows Server Active Directory på Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Disse retningslinjer hjælper dig med at afgøre, om du har brug for en anden arkitektur eller forskellige konfigurationsindstillinger til din løsning.

Du kan finde en detaljeret vejledning i, hvordan du konfigurerer en domænecontroller i Azure, under [Installér en Replika Active Directory-domænecontroller i Azure Virtual Networks](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).

Før denne fase udrullede du ikke virtuelle maskiner til Virtual Network. De virtuelle maskiner til hosting af Active Directory og DNS er sandsynligvis ikke de største virtuelle maskiner, du har brug for til løsningen. Før du udruller disse virtuelle maskiner, skal du først oprette den største virtuelle maskine, som du planlægger at bruge i din Virtual Network. Dette hjælper med at sikre, at din løsning lander på et tag i Azure, der giver den største størrelse, du har brug for. Du behøver ikke at konfigurere denne virtuelle maskine på nuværende tidspunkt. Du skal blot oprette den og lægge den til side. Hvis du ikke gør dette, kan du støde på en begrænsning, når du forsøger at oprette større virtuelle maskiner senere, hvilket var et problem på det tidspunkt, denne artikel blev skrevet.

## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Fase 4: Udrul genoprettelsesfarmen SharePoint i Azure

Udrul den SharePoint farm i din Virtual Network i henhold til dine designplaner. Det kan være nyttigt at gennemse [Planlægning af SharePoint 2013 på Azure Infrastructure Services](/previous-versions/azure/dn275958(v=azure.100)), før du udruller SharePoint roller i Azure.

Overvej følgende fremgangsmåder, som vi har lært ved at oprette vores blåstemplingsmiljø:

- Opret virtuelle maskiner ved hjælp af Azure Portal eller PowerShell.

- Azure og Hyper-V understøtter ikke dynamisk hukommelse. Sørg for, at dette er indregnet i dine planer for ydeevne og kapacitet.

- Genstart virtuelle maskiner via Azure-grænsefladen, ikke fra selve logon til den virtuelle maskine. Brug af Azure-grænsefladen fungerer bedre og er mere forudsigeligt.

- Hvis du vil lukke en virtuel maskine for at spare omkostninger, skal du bruge Azure-grænsefladen. Hvis du lukker ned fra logon til den virtuelle maskine, påløber gebyrerne fortsat.

- Brug en navngivningskonvention for de virtuelle maskiner.

- Vær opmærksom på, hvilken datacenterplacering de virtuelle maskiner udrulles på.

- Funktionen til automatisk skalering i Azure understøttes ikke for SharePoint roller.

- Konfigurer ikke elementer i farmen, der skal gendannes, f.eks. grupper af websteder.

## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Fase 5: Konfigurer DFSR mellem farmene

Hvis du vil konfigurere filreplikering ved hjælp af DFSR, skal du bruge snap-in'en DNS Management. Før DFSR-installationen skal du dog logge på din lokale filserver og Azure-filserver og aktivere tjenesten i Windows.

Gennemfør følgende trin fra dashboardet Serverstyring:

- Konfigurer den lokale server.

- Start **guiden Tilføj roller og funktioner**.

- Åbn noden **File og Storage Services**.

- Vælg **DFS-navneområder** og **DFS-replikering**.

- Klik på **Næste** for at fuldføre trinnene i guiden.

Følgende tabel indeholder links til DFSR-referenceartikler og blogindlæg.

**Tabel: Referenceartikler om DFSR**

|Titel|Beskrivelse|
|---|---|
|[Replikering](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11))|TechNet-emnet DFS Management med links til replikering|
|[DFS-replikering: Overlevelsesvejledning](https://go.microsoft.com/fwlink/p/?LinkId=392737)|Wiki med links til DFS-oplysninger|
|[DFS-replikering: Ofte stillede spørgsmål](/previous-versions/windows/it-pro/windows-server-2003/cc773238(v=ws.10))|TechNet-emne om DFS-replikering|
|[Jose Barretos blog](/archive/blogs/josebda/)|Blog skrevet af en Principal Program Manager på filserverteamet hos Microsoft|
|[Det Storage team hos Microsoft - File Cabinet Blog](https://go.microsoft.com/fwlink/p/?LinkId=392740)|Blog om filtjenester og lagerfunktioner i Windows Server|

## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Fase 6: Konfigurer logforsendelse til genoprettelsesfarmen

Logforsendelse er den kritiske komponent til konfiguration af it-katastrofeberedskab i dette miljø. Du kan bruge logforsendelse til automatisk at sende transaktionslogfiler til databaser fra en primær databaseserverforekomst til en sekundær databaseserverforekomst. Hvis du vil konfigurere logforsendelse, skal du se [Konfigurer logforsendelse i SharePoint 2013](/sharepoint/administration/configure-log-shipping).

> [!IMPORTANT]
> Logforsendelsessupport i SharePoint Server er begrænset til visse databaser. Du kan få flere oplysninger under [Understøttede muligheder for høj tilgængelighed og it-katastrofeberedskab for SharePoint databaser (SharePoint 2013)](/SharePoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas).

## <a name="phase-7-validate-failover-and-recovery"></a>Fase 7: Valider failover og genoprettelse

Målet med denne sidste fase er at bekræfte, at løsningen til it-katastrofeberedskab fungerer som planlagt. Det gør du ved at oprette en failoverhændelse, der lukker produktionsfarmen og starter genoprettelsesfarmen som en erstatning. Du kan starte et failover-scenarie manuelt eller ved hjælp af scripts.

Det første trin er at stoppe indgående brugeranmodninger for farmtjenester eller indhold. Det kan du gøre ved at deaktivere DNS-poster eller ved at lukke frontendwebserverne. Når farmen er "nede", kan du failover til genoprettelsesfarmen.

### <a name="stop-log-shipping"></a>Stop logforsendelse

Du skal stoppe logføringen, før farmen genoprettes. Stop logføring på den sekundære server i Azure først, og stop den derefter på den primære server i det lokale miljø. Brug følgende script til at stoppe logfilen med levering på den sekundære server først og derefter på den primære server. Databasenavnene i scriptet kan være forskellige, afhængigt af dit miljø.

```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')
```

### <a name="restore-the-backups"></a>Gendan sikkerhedskopierne

Sikkerhedskopier skal gendannes i den rækkefølge, de blev oprettet i. Før du kan gendanne en bestemt sikkerhedskopiering af transaktionsloggen, skal du først gendanne følgende tidligere sikkerhedskopieringer uden at annullere ikke-gemte transaktioner (dvs. ved hjælp  `WITH NORECOVERY`af ):

- Den fulde databasesikkerhedskopiering og den sidste differentielle sikkerhedskopiering – Gendan eventuelle sikkerhedskopier, der er taget før sikkerhedskopieringen af transaktionsloggen. Før den seneste sikkerhedskopiering af fuld eller differentieret database blev oprettet, brugte databasen den fulde genoprettelsesmodel eller den masselogførte genoprettelsesmodel.

- Alle sikkerhedskopieringer af transaktionslogfiler – Gendan alle sikkerhedskopieringer af transaktionslogfiler, der er taget efter den fulde sikkerhedskopiering af databasen eller den differentielle sikkerhedskopiering (hvis du gendanner en), og før den pågældende sikkerhedskopiering af transaktionsloggen. Logsikkerhedskopieringer skal anvendes i den rækkefølge, de blev oprettet i, uden nogen huller i logkæden.

Hvis du vil gendanne indholdsdatabasen på den sekundære server, så webstederne gengives, skal du fjerne alle databaseforbindelser før gendannelsen. Kør følgende SQL sætning for at gendanne databasen.

```SQL
restore database WSS_Content with recovery
```

> [!IMPORTANT]
> Når du bruger T-SQL eksplicit, skal du angive enten **WITH NORECOVERY** eller **WITH RECOVERY** i hver RESTORE-sætning for at fjerne flertydighed – dette er meget vigtigt, når du skriver scripts. Når de fulde og differentielle sikkerhedskopieringer er gendannet, kan transaktionslogfilerne gendannes i SQL Server Management Studio. Da logfilen allerede er stoppet, er indholdsdatabasen i standbytilstand, så du skal ændre tilstanden til fuld adgang.

I SQL Server Management Studio skal du højreklikke på **databasen WSS_Content**, pege på **TasksRestore** >  og derefter klikke på **Transaktionslog** (hvis du ikke har gendannet den fulde sikkerhedskopi, er den ikke tilgængelig). Du kan få flere oplysninger [underStore a Transaction Log Backup (SQL Server)](/sql/relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server).

### <a name="crawl-the-content-source"></a>Gennemsøg indholdskilden

Du skal starte en fuld gennemsøgning for hver indholdskilde for at gendanne søgetjenesten. Bemærk, at du mister nogle analyseoplysninger fra farmen i det lokale miljø, f.eks. søgeanbefalinger. Før du starter de komplette gennemsøgninger, skal du bruge Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** og angive den logsendte og replikerede database til administration af søgning **, Search_Service__DB_\<GUID\>**. Denne cmdlet giver søgekonfigurationen, skemaet, administrerede egenskaber, regler og kilder og opretter et standardsæt af de andre komponenter.

Hvis du vil starte en fuld gennemsøgning, skal du udføre følgende trin:

1. I den SharePoint 2013 Central administration skal du gå til **Application ManagementService** >  **ApplicationsAdministrer** >  tjenesteprogrammer og derefter klikke på det søgetjenesteprogram, du vil gennemsøge.

2. Klik på **Indholdskilder** på siden **Administration af søgning**, peg på den ønskede indholdskilde, klik på pilen, og klik derefter på **Start fuld gennemsøgning**.

### <a name="recover-farm-services"></a>Gendan farmtjenester

I følgende tabel kan du se, hvordan du gendanner tjenester, der har databaser, der er leveret af log, de tjenester, der har databaser, men som ikke anbefales at gendanne med logforsendelse, og de tjenester, der ikke har databaser.

> [!IMPORTANT]
> Hvis du gendanner en database i det lokale miljø SharePoint i Azure-miljøet, gendannes ingen SharePoint tjenester, som du ikke allerede har installeret i Azure manuelt.

**Tabel: Reference til tjenesteprogramdatabase**

|Gendan disse tjenester fra databaser, der er leveret i logfilen|Disse tjenester har databaser, men vi anbefaler, at du starter disse tjenester uden at gendanne deres databaser|Disse tjenester gemmer ikke data i databaser. starte disse tjenester efter failover|
|---|---|---|
|Maskinoversættelsestjeneste <br/> Administreret metadatatjeneste <br/> Sikker Store tjeneste <br/> Brugerprofil. (Det er kun databaserne Profil og Social Mærkning, der understøttes. Synkroniseringsdatabasen understøttes ikke.) <br/> Microsoft SharePoint Foundation Subscription Indstillinger Service|Indsamling af statistik- og tilstandsdata <br/> Tilstandstjeneste <br/> Word automation|Excel-tjenester <br/> PerformancePoint Services <br/> konvertering af PowerPoint <br/> tjenesten Visio Grafik <br/> Styring af arbejde|

I følgende eksempel kan du se, hvordan du gendanner tjenesten administrerede metadata fra en database.

Dette bruger den eksisterende Managed_Metadata_DB database. Denne database er sendt i en log, men der er ikke noget aktivt tjenesteprogram på den sekundære farm, så den skal have forbindelse, når tjenesteprogrammet er på plads.

`New-SPMetadataServiceApplication`Brug først , og angiv `DatabaseName` parameteren med navnet på den gendannede database.

Konfigurer derefter det nye administrerede metadatatjenesteprogram på den sekundære server på følgende måde:

- Navn: Administreret metadatatjeneste

- Databaseserver: Databasenavnet fra den afsendte transaktionslogfil

- Databasenavn: Managed_Metadata_DB

- Programgruppe: SharePoint tjenesteprogrammer

### <a name="manage-dns-records"></a>Administrer DNS-poster

Du skal manuelt oprette DNS-poster for at pege på din SharePoint farm.

I de fleste tilfælde, hvor du har flere frontendwebservere, giver det mening at drage fordel af funktionen Network Load Balancing i Windows Server 2012 eller en hardware belastningsjustering til at distribuere anmodninger mellem webfrontendserverne i farmen. Justering af netværksbelastning kan også hjælpe med at reducere risikoen ved at distribuere anmodninger til de andre servere, hvis en af dine webfrontendservere mislykkes.

Når du konfigurerer justering af netværksbelastning, tildeles din klynge typisk en enkelt IP-adresse. Du opretter derefter en DNS-værtspost i DNS-udbyderen for dit netværk, der peger på klyngen. (I dette projekt placerer vi en DNS-server i Azure for robusthed i tilfælde af en fejl i et datacenter i det lokale miljø). Du kan f.eks. oprette en DNS-post i DNS Manager i Active Directory, f.eks. kaldet  `https://sharepoint.contoso.com`, der peger på IP-adressen for din belastningsbalancerede klynge.

Hvis du vil have ekstern adgang til din SharePoint farm, kan du oprette en værtspost på en ekstern DNS-server med den samme URL-adresse, som klienterne bruger på intranettet (f.eks. `https://sharepoint.contoso.com`), som peger på en ekstern IP-adresse i firewallen. (I dette eksempel er det bedste praksis at konfigurere opdelt DNS, så den interne DNS-server er autoritativ for `contoso.com` og dirigerer anmodninger direkte til SharePoint farmklynge i stedet for at dirigere DNS-anmodninger til din eksterne DNS-server). Du kan derefter knytte den eksterne IP-adresse til den interne IP-adresse for din lokale klynge, så klienterne finder de ressourcer, de leder efter.

Herfra kan du støde på et par forskellige scenarier for it-katastrofeberedskab:

 **Eksempelscenarie: Den lokale SharePoint farm er ikke tilgængelig på grund af hardwarefejl i den lokale SharePoint farm.** Når du har fuldført trinnene for failover til Azure SharePoint-farmen, kan du i dette tilfælde konfigurere justering af netværksbelastningen på genoprettelses- SharePoint farmens webfrontendservere på samme måde, som du gjorde med farmen i det lokale miljø. Du kan derefter omdirigere værtsposten i din interne DNS-udbyder, så den peger på genoprettelsesfarmens KLYNGE-IP-adresse. Bemærk, at det kan tage et stykke tid, før cachelagrede DNS-poster på klienter opdateres og peger på genoprettelsesfarmen.

 **Eksempelscenarie: Datacenteret i det lokale miljø går helt tabt.** Dette scenarie kan opstå på grund af en naturkatastrofe, f.eks. en brand eller oversvømmelse. I dette tilfælde vil du for en virksomhed sandsynligvis have et sekundært datacenter, der hostes i et andet område, samt dit Azure-undernet, der har sine egne katalogtjenester og DNS. Som i det forrige katastrofescenarie kan du omdirigere dine interne og eksterne DNS-poster, så de peger på Azure SharePoint-farmen. Igen skal du være opmærksom på, at overførsel af DNS-poster kan tage noget tid.

Hvis du bruger grupper af websteder med værtsnavn, som anbefalet i [arkitekturen og installationen af grupper af websteder med værtsnavn (SharePoint 2013),](/SharePoint/administration/host-named-site-collection-architecture-and-deployment) kan du have flere grupper af websteder, der hostes af det samme webprogram i din SharePoint farm, med entydige DNS-navne (f.eks`https://sales.contoso.com`. og `https://marketing.contoso.com`). I dette tilfælde kan du oprette DNS-poster for hver gruppe af websteder, der peger på din klynges IP-adresse. Når en anmodning når SharePoint webfrontendservere, håndterer de routing af hver anmodning til den relevante gruppe af websteder.

## <a name="microsoft-proof-of-concept-environment"></a>Microsofts proof-of-concept-miljø

Vi har designet og testet et proof-of-concept-miljø til denne løsning. Designmålet for vores testmiljø var at udrulle og gendanne en SharePoint farm, som vi måske finder i et kundemiljø. Vi har foretaget flere forudsætninger, men vi vidste, at farmen var nødvendig for at levere alle de indbyggede funktioner uden nogen tilpasninger. Topologien er designet til høj tilgængelighed ved hjælp af vejledning til bedste praksis fra feltet og produktgruppen.

I følgende tabel beskrives de virtuelle Hyper-V-maskiner, som vi har oprettet og konfigureret til testmiljøet i det lokale miljø.

**Tabel: Virtuelle maskiner til test i det lokale miljø**

|Servernavn|Rolle|Konfiguration|
|---|---|---|
|DC1|Domænecontroller med Active Directory.|To processorer <br/> Fra 512 MB til 4 GB RAM <br/> 1 x 127 GB harddisk|
|RRAS|Server konfigureret med rollen Routing and Remote Access Service (RRAS).|To processorer <br/> 2-8 GB RAM <br/> 1 x 127 GB harddisk|
|FS1|Filserver med shares til sikkerhedskopier og et slutpunkt for DFSR.|Fire processorer <br/> 2-12 GB RAM <br/> 1 x 127 GB harddisk <br/> 1 x 1 TB harddisk (SAN) <br/> 1 x 750 GB harddisk|
|SP-WFE1, SP-WFE2|Frontendwebservere.|Fire processorer <br/> 16 GB RAM|
|SP-APP1, SP-APP2, SP-APP3|Programservere.|Fire processorer <br/> 2-16 GB RAM|
|SP-SQL-HA1, SP-SQL-HA2|Databaseservere, der er konfigureret med SQL Server 2012 AlwaysOn-tilgængelighedsgrupper for at give høj tilgængelighed. Denne konfiguration bruger SP-SQL-HA1 og SP-SQL-HA2 som primære og sekundære replikaer.|Fire processorer <br/> 2-16 GB RAM|

I følgende tabel beskrives drevkonfigurationer for de virtuelle Hyper-V-maskiner, som vi har oprettet og konfigureret for frontendweb- og programservere for testmiljøet i det lokale miljø.

**Tabel: Krav til virtuelle maskiners drev til Front End-web- og programservere til test i det lokale miljø**

|Drevbogstav|Størrelse|Mappenavn|Sti|
|---|---|---|---|
|C|80|Systemdrev|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\|
|E|80|Logdrev (40 GB)|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|80|Side (36 GB)|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\ MSSQLDATA\\|

I følgende tabel beskrives drevkonfigurationer for de virtuelle Hyper-V-maskiner, der er oprettet og konfigureret til at fungere som databaseservere i det lokale miljø. På siden **Konfiguration af databaseprogram** skal du få adgang til fanen **Datamapper** for at angive og bekræfte de indstillinger, der vises i følgende tabel.

**Tabel: Krav til drev på virtuel maskine for databaseserveren til test i det lokale miljø**

|Drevbogstav|Størrelse|Mappenavn|Sti|
|---|---|---|---|
|C|80|Datarodmappe|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\|
|E|500|Brugerdatabasemappe|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|500|Logmappe til brugerdatabase|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|G|500|Temp DB-mappe|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|H|500|Temp DB-logmappe|\<DriveLetter\>:\\Programmer\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|

### <a name="setting-up-the-test-environment"></a>Konfiguration af testmiljøet

Under de forskellige udrulningsfaser arbejdede testteamet typisk først på arkitekturen i det lokale miljø og derefter på det tilsvarende Azure-miljø. Dette afspejler de tilfælde i den virkelige verden, hvor in-house-landbrugsbedrifter allerede kører. Endnu vigtigere er, at du kender den aktuelle produktionsarbejdsbelastning, kapacitet og typiske ydeevne. Ud over at bygge en model til it-katastrofeberedskab, der kan opfylde forretningskrav, skal du tilpasse størrelsen på genoprettelsesfarmserverne for at levere et minimumsniveau af service. I et koldt eller varmt standbymiljø er en genoprettelsesfarm typisk mindre end en produktionsfarm. Når genoprettelsesfarmen er stabil og i produktion, kan den skaleres op og ud, så den opfylder arbejdsbelastningskravene.

Vi udrullede vores testmiljø i følgende tre faser:

- Konfigurer hybridinfrastrukturen

- Klargør serverne

- Udrul de SharePoint farme

#### <a name="set-up-the-hybrid-infrastructure"></a>Konfigurer hybridinfrastrukturen

Denne fase omfattede konfiguration af et domænemiljø for farmen i det lokale miljø og for genoprettelsesfarmen i Azure. Ud over de normale opgaver, der er knyttet til konfiguration af Active Directory, implementerede testteamet en routingløsning og en VPN-forbindelse mellem de to miljøer.

#### <a name="provision-the-servers"></a>Klargør serverne

Ud over farmserverne var det nødvendigt at klargøre servere til domænecontrollerne og konfigurere en server til at håndtere RRAS og VPN-webstedet. Der blev klargjort to filservere til DFSR-tjenesten, og flere klientcomputere blev klargjort til testere.

#### <a name="deploy-the-sharepoint-farms"></a>Udrul de SharePoint farme

De SharePoint farme blev udrullet i to faser for at forenkle miljøstabilisering og fejlfinding, hvis det er nødvendigt. I den første fase blev hver farm udrullet på det mindste antal servere for hvert niveau i topologien for at understøtte den påkrævede funktionalitet.

Vi har oprettet databaseserverne med SQL Server installeret, før du opretter SharePoint 2013-servere. Da dette var en ny udrulning, oprettede vi tilgængelighedsgrupperne, før vi udrullede SharePoint. Vi har oprettet tre grupper baseret på MCS's vejledning til bedste praksis.

> [!NOTE]
> Opret pladsholderdatabaser, så du kan oprette tilgængelighedsgrupper før installationen af SharePoint. Du kan få flere oplysninger under [Konfigurer SQL Server 2012 AlwaysOn-tilgængelighedsgrupper for SharePoint 2013](/SharePoint/administration/configure-an-alwayson-availability-group)

Vi har oprettet farmen og tilsluttet flere servere i følgende rækkefølge:

- Klargør SP-SQL-HA1 og SP-SQL-HA2.

- Konfigurer AlwaysOn, og opret de tre tilgængelighedsgrupper for farmen.

- Klargør SP-APP1 som vært for Central administration.

- Klargør SP-WFE1 og SP-WFE2 som vært for den distribuerede cache.

Vi brugte parameteren  _skipRegisterAsDistributedCachehost_ , da vi kørte **psconfig.exe** på kommandolinjen. Du kan få flere oplysninger under [Plan for feeds og tjenesten Distributed Cache i SharePoint Server 2013](/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service).

Vi har gentaget følgende trin i genoprettelsesmiljøet:

- Klargør AZ-SQL-HA1 og AZ-SQL-HA2.

- Konfigurer AlwaysOn, og opret de tre tilgængelighedsgrupper for farmen.

- Klargør AZ-APP1 som vært for Central administration.

- Klargør AZ-WFE1 og AZ-WFE2 som vært for den distribuerede cache.

Når vi har konfigureret den distribuerede cache og tilføjet testbrugere og testindhold, startede vi fase 2 i udrulningen. Dette krævede udskalering af niveauerne og konfiguration af farmserverne for at understøtte topologien med høj tilgængelighed, der er beskrevet i farmarkitekturen.

I følgende tabel beskrives de virtuelle maskiner, undernet og tilgængelighedssæt, vi har konfigureret til vores genoprettelsesfarm.

**Tabel: Infrastruktur for genoprettelsesfarme**

|Servernavn|Rolle|Konfiguration|Undernet|Tilgængelighedssæt|
|---|---|---|---|---|
|spDRAD|Domænecontroller med Active Directory|To processorer <br/> Fra 512 MB til 4 GB RAM <br/> 1 x 127 GB harddisk|sp-ADservers||
|AZ-SP-FS|Filserver med shares til sikkerhedskopier og et slutpunkt for DFSR|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM <br/> 1 x 127 GB harddisk <br/> 1 x 135 GB harddisk <br/> 1 x 127 GB harddisk <br/> 1 x 150 GB harddisk|sp-databaseservere|DATA_SET|
|AZ-WFE1, AZ -WFE2|Front End-webservere|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM <br/> 1 x 127 GB harddisk|sp-webservere|WFE_SET|
|AZ -APP1, AZ -APP2, AZ -APP3|Programservere|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM <br/> 1 x 127 GB harddisk|sp-applicationservers|APP_SET|
|AZ -SQL-HA1, AZ -SQL-HA2|Databaseservere og primære og sekundære replikaer for AlwaysOn-tilgængelighedsgrupper|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM|sp-databaseservere|DATA_SET|

### <a name="operations"></a>Operationer

Efter at testteamet har stabiliseret farmmiljøerne og fuldført funktionel test, startede de følgende handlingsopgaver, der kræves for at konfigurere genoprettelsesmiljøet i det lokale miljø:

- Konfigurer komplette og differentielle sikkerhedskopier.

- Konfigurer DFSR på de filservere, der overfører transaktionslogge mellem det lokale miljø og Azure-miljøet.

- Konfigurer logforsendelse på den primære databaseserver.

- Stabiliser, valider og foretag fejlfinding af logforsendelse efter behov. Dette omfattede identificering og dokumentation af enhver funktionsmåde, der kan medføre problemer, f.eks. netværksventetid, hvilket ville medføre fejl under levering af logfiler eller DFSR-filsynkronisering.

### <a name="databases"></a>Databaser

Vores failovertest omfattede følgende databaser:

- WSS_Content

- ManagedMetadata

- Profildatabase

- Synkroniser database

- Social DB

- Indholdstypehub (en database for en dedikeret indholdstypesyndikeringshub)

## <a name="troubleshooting-tips"></a>Fejlfindingstip

I afsnittet forklares de problemer, vi oplevede under vores test, og deres løsninger.

### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Brugen af værktøjet til administration af ord Store forårsagede fejlen "De administrerede metadata Store eller forbindelsen er i øjeblikket ikke tilgængelige".

Kontrollér, at den programgruppekonto, der bruges af webprogrammet, har tilladelsen Læseadgang til ord Store.

### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Brugerdefinerede ordsæt er ikke tilgængelige i gruppen af websteder

Kontrollér, om der mangler en tjenesteprogramtilknytning mellem din gruppe af indholdswebsteder og din indholdstypehub. Under skærmen **Administrerede metadata – \<site collection name\> forbindelsesegenskaber** skal du desuden sørge for, at denne indstilling er aktiveret: **Dette tjenesteprogram er standardlagerplaceringen for kolonnespecifikke ordsæt.**

### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Kommandoen Get-ADForest Windows PowerShell genererer fejlen "Get-ADForest" genkendes ikke som navnet på en cmdlet, funktion, scriptfil eller driftsklart program."

Når du konfigurerer brugerprofiler, skal du bruge Active Directory-områdenavnet. I guiden Tilføj roller og funktioner skal du kontrollere, at du har aktiveret Active Directory-modulet for Windows PowerShell (under afsnittet **Administrationsværktøjer til fjernserver>rolleadministrationsværktøjer>AD DS- og AD LDS-værktøjer**). Du skal desuden køre følgende kommandoer, før du bruger **Get-ADForest** , for at sikre, at dine softwareafhængigheder indlæses.

```powershell
Import-Module ServerManager
Import-Module ActiveDirectory
```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Oprettelse af tilgængelighedsgruppe mislykkes ved start af XEvent-sessionen 'AlwaysOn_health' på '\<server name\>'

Sørg for, at begge noder i failoverklynge er i status "Up" og ikke "Afbrudt midlertidigt" eller "Stoppet".

### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server logfilens afsendelsesjob mislykkes, og adgang nægtet fejl under forsøg på at oprette forbindelse til filsharet

Sørg for, at din SQL Server Agent kører under legitimationsoplysninger til netværket i stedet for standardlegitimationsoplysninger.

### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server logforsendelsesjob angiver, at det lykkedes, men der kopieres ingen filer

Dette sker, fordi standardindstillingen for sikkerhedskopiering for en tilgængelighedsgruppe er **Foretrukket sekundær**. Sørg for, at du kører logforsendelsesjobbet fra den sekundære server for tilgængelighedsgruppen i stedet for den primære. Ellers mislykkes jobbet automatisk.

### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Den administrerede metadatatjeneste (eller en anden SharePoint tjeneste) kan ikke starte automatisk efter installationen

Det kan tage flere minutter at starte tjenester, afhængigt af ydeevnen og den aktuelle belastning af din SharePoint Server. Klik manuelt på **Start** for tjenesten, og giv tilstrækkelig tid til start, mens skærmen Tjenester på server indimellem opdateres for at overvåge dens status. Hvis tjenesten forbliver stoppet, skal du aktivere SharePoint logføring af diagnosticering, forsøge at starte tjenesten igen og derefter kontrollere, om der er fejl i logfilen. Du kan få flere oplysninger under [Konfigurer logføring af diagnosticering i SharePoint 2013](/sharepoint/administration/configure-diagnostic-logging)

### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Når du har ændret DNS til Azure-failovermiljøet, fortsætter klientbrowsere med at bruge den gamle IP-adresse for det SharePoint websted

Din DNS-ændring er muligvis ikke synlig for alle klienter med det samme. Udfør følgende kommando fra en kommandoprompt med administratorrettigheder på en testklient, og forsøg at få adgang til webstedet igen.

```DOS
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Yderligere ressourcer

[Understøttede muligheder for høj tilgængelighed og it-katastrofeberedskab for SharePoint databaser](/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)

[Konfigurer SQL Server 2012 AltidTil tilgængelighedsgrupper for SharePoint 2013](/SharePoint/administration/configure-an-alwayson-availability-group)

## <a name="see-also"></a>Se også

[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)
