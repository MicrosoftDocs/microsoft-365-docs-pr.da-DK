---
title: It-katastrofeberedskab i SharePoint Server 2013 i Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
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
description: I denne artikel beskrives det, hvordan du kan bruge Azure til at oprette et miljø til genoprettelse efter nedbrud i din lokale SharePoint farm.
ms.openlocfilehash: 873d0c9ccfdc8c6a978b89416a7492a2141c825d
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569130"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>It-katastrofeberedskab i SharePoint Server 2013 i Microsoft Azure

 Med Azure kan du oprette et miljø til genoprettelse efter nedbrud til din lokale SharePoint farm. Denne artikel beskriver, hvordan du designer og implementerer denne løsning.

 **Se videoen med SharePoint, der viser genoprettelse efter nedbrud i Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]

 Når nedbrud rammer dit SharePoint lokale miljø, er din topprioritet at få systemet til at køre igen hurtigt. Genoprettelse efter nedbrud med SharePoint er hurtigere og nemmere, når du har et sikkerhedskopimiljø, der allerede kører Microsoft Azure. I denne video forklares de vigtigste begreber SharePoint et varmt failovermiljø, og den komplementerer alle de oplysninger, der er tilgængelige i denne artikel.

Brug denne artikel med følgende løsningsmodel: Genoprettelse **SharePoint efter nedbrud i Microsoft Azure**.

[![SharePoint proces til genoprettelse efter nedbrud til Azure.](../media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)

 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)

## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Brug Azure Infrastructure Services til genoprettelse efter nedbrud

Mange organisationer har ikke et miljø til genoprettelse efter nedbrud for SharePoint, som kan være dyre at opbygge og vedligeholde lokalt. Azure Infrastructure Services giver overbevisende indstillinger til miljøer til genoprettelse efter nedbrud, der er mere fleksible og billigere end de lokale alternativer.

Fordelene ved at bruge Azure-infrastrukturtjenester omfatter:

- **Færre omkostningstunge ressourcer** Vedligeholde og betale for færre ressourcer end lokale miljøer til genoprettelse efter nedbrud. Antallet af ressourcer afhænger af, hvilket miljø til genoprettelse efter nedbrud du vælger: cold standby, warm standby eller hot standby.

- **Bedre ressourcefleksibilitet** I tilfælde af nedbrud kan du let skalere din genoprettelses- SharePoint farm, så den opfylder krav til belastning. Skaler ind, når du ikke længere har brug for ressourcerne.

- **Lavere binding i datacenter** Brug Azure Infrastructure Services i stedet for at investere i et sekundært datacenter i et andet område.

Der er mindre komplekse muligheder for organisationer, der lige er startet med genoprettelse efter nedbrud og avancerede indstillinger for organisationer med krav til høj fleksibilitet. Definitionerne for kolde, varme og varme standbymiljøer er lidt anderledes, når miljøet er hostet på en skyplatform. I følgende tabel beskrives disse miljøer til at opbygge en SharePoint-genoprettelsesfarm i Azure.

**Tabel: Genoprettelsesmiljøer**

|Type af genoprettelsesmiljø|Beskrivelse|
|---|---|
|Hot|En farm i fuld størrelse klargøres, opdateres og kører på standby.|
|Varm|Farmen er bygget, og virtuelle maskiner kører og opdateres. <br/> Genoprettelse omfatter vedhæftning af indholdsdatabaser, klargøringstjenesteprogrammer og gennemsøgning af indhold. <br/> Farmen kan være en mindre version af produktionsfarmen og skaleres derefter ud til at betjene den fulde brugerbase.|
|Cold|Farmen er fuldt opbygget, men de virtuelle maskiner stoppes. <br/> Vedligeholdelse af miljøet omfatter at starte de virtuelle computere fra tid til anden, programrettelser, opdatering og bekræftelse af miljøet. <br/> Start hele miljøet i tilfælde af nedbrud.|

Det er vigtigt, at du evaluerer organisationens målsætninger for genoprettelsestid (RTOs) og målsætninger for genoprettelsespunkt (RPOs). Disse krav afgør, hvilket miljø der er den mest passende investering for organisationen.

Vejledningen i denne artikel beskriver, hvordan du implementerer et varmt standby-miljø. Du kan også tilpasse det til et miljø med iskold standby, selvom du skal følge yderligere procedurer for at understøtte denne type miljø. I denne artikel beskrives det ikke, hvordan du implementerer et hot standby-miljø.

Du kan finde flere oplysninger om løsninger til genoprettelse efter nedbrud under Begreberne Høj tilgængelighed og Genoprettelse efter nedbrud [i SharePoint 2013](/SharePoint/administration/high-availability-and-disaster-recovery-concepts) og Vælg en strategi for genoprettelse efter nedbrud [til SharePoint 2013](/SharePoint/administration/plan-for-disaster-recovery).

## <a name="solution-description"></a>Løsningsbeskrivelse

Den varme standby-løsning til genoprettelse efter nedbrud kræver følgende miljø:

- En lokal SharePoint produktionsfarm

- En genoprettelsesfarm SharePoint Azure

- En websted-til-websted-VPN-forbindelse mellem de to miljøer

Følgende figur illustrerer disse tre elementer.

**Figur: Elementer i en varm standby-løsning i Azure**

![Elementer i en SharePoint varm standby-løsning i Azure.](../media/AZarch-AZWarmStndby.png)

SQL Server med DFSR (Distributed File System Replication) bruges til at kopiere sikkerhedskopiering af databaser og transaktionslogfiler til genoprettelsesfarmen i Azure:

- DFSR overfører logfiler fra produktionsmiljøet til genoprettelsesmiljøet. I et WAN-scenarie er DFSR mere effektivt end at sende logfilerne direkte til den sekundære server i Azure.

- Logfiler genafspiles på SQL Server i genoprettelsesmiljøet i Azure.

- Du vedhæfter ikke logget indholdsdatabaser SharePoint genoprettelsesmiljøet, før der udføres en genoprettelsestræning.

Udfør følgende trin for at gendanne farmen:

1. Stop logforsendelse.

2. Stop med at acceptere trafik til den primære farm.

3. Genafspil de endelige transaktionslogfiler.

4. Vedhæft indholdsdatabaserne til farmen.

5. Gendan tjenesteprogrammer fra de replikerede tjenestedatabaser.

6. Opdater DNS-poster (Domain Name System), der peger på genoprettelsesfarmen.

7. Start en fuld gennemsøgning.

Vi anbefaler, at du øver dig regelmæssigt på disse trin og dokumenterer dem for at sikre, at din livegendannelse kører uden problemer. Det kan tage lidt tid at vedhæfte indholdsdatabaser og gendanne tjenesteprogrammer, og det indebærer typisk en del manuel konfiguration.

Når en gendannelse er udført, indeholder denne løsning de elementer, der er angivet i følgende tabel.

**Tabel: Målsætninger for løsningsgendannelse**

|Element|Beskrivelse|
|---|---|
|Websteder og indhold|Websteder og indhold er tilgængelige i genoprettelsesmiljøet.|
|En ny forekomst af søgning|I denne varme standbyløsning gendannes søgningen ikke fra søgedatabaser. Søgekomponenterne i genoprettelsesfarmen er konfigureret så på samme måde som muligt med produktionsfarmen. Når webstederne og indholdet er gendannet, startes en fuld gennemsøgning for at genopbygge søgeindekset. Du behøver ikke at vente på, at gennemsøgningen fuldføres for at gøre webstederne og indholdet tilgængelige.|
|Tjenester|Tjenester, der lagrer data i databaser, gendannes fra de logfiler, som er leveret. Tjenester, der ikke gemmer data i databaser, startes simpelthen. <br/> Det er ikke nødvendigt at gendanne alle tjenester med databaser. Følgende tjenester behøver ikke at blive gendannet fra databaser og kan blot startes efter failover: <br/> Indsamling af forbrugs- og tilstandsdata <br/> Offentlig tjeneste <br/> Automatisering af Word <br/> Enhver anden tjeneste, der ikke bruger en database|

Du kan arbejde sammen med Microsoft Consulting Services (MCS) eller en partner for at tage hånd om mere komplekse genoprettelsesmål. Disse er opsummeret i følgende tabel.

**Tabel: Andre elementer, der kan adresseres af MCS eller en partner**

|Element|Beskrivelse|
|---|---|
|Synkronisering af brugerdefinerede farmløsninger|Ideelt set er konfigurationen af genoprettelsesfarmen identisk med produktionsfarmen. Du kan arbejde sammen med en konsulent eller partner om at evaluere, om brugerdefinerede farmløsninger replikeres, og om processen er klar til at holde de to miljøer synkroniserede.|
|Forbindelser til datakilder i det lokale miljø|Det er muligvis ikke praktisk at kopiere forbindelser til back end-datasystemer, f.eks. forbindelser til backupdomænecontroller (BDC) og søge i indholdskilder.|
|Søgegendannelsesscenarier|Da virksomhedssøgningsinstallationer ofte er forholdsvis unikke og komplekse, kræver gendannelse af søgning fra databaser en større investering. Du kan arbejde sammen med en konsulent eller partner om at identificere og implementere søgegendannelsesscenarier, som din organisation kan kræve.|

Vejledningen i denne artikel forudsætter, at den lokale farm allerede er udviklet og installeret.

## <a name="detailed-architecture"></a>Detaljeret arkitektur

Ideelt set er konfigurationen af genoprettelsesfarmen i Azure identisk med produktionsfarmen i det lokale miljø, herunder følgende:

- Den samme repræsentation af serverroller

- Den samme konfiguration af tilpasninger

- Den samme konfiguration af søgekomponenter

Miljøet i Azure kan være en mindre version af produktionsfarmen. Hvis du planlægger at skalere genoprettelsesfarmen efter failover, er det vigtigt, at hver type serverrolle indledningsvist repræsenteres.

Nogle konfigurationer er muligvis ikke praktiske at replikere i failovermiljøet. Sørg for at teste failoverprocedurerne og miljøet for at sikre, at failoverfarmen leverer det forventede tjenesteniveau.

Denne løsning får ikke en bestemt topologi for en SharePoint farm. Fokus for denne løsning er at bruge Azure til failoverfarmen og implementere logforsendelse og DFSR mellem de to miljøer.

### <a name="warm-standby-environments"></a>Varme standbymiljøer

I et varmt standbymiljø kører alle virtuelle maskiner i Azure-miljøet. Miljøet er klar til en failover-øvelse eller -hændelse.

Følgende figur illustrerer en løsning til genoprettelse efter nedbrud fra en lokal SharePoint-farm til en Azure-baseret SharePoint-farm, der er konfigureret som et varmt standbymiljø.

**Figur: Topologi og nøgleelementer i en produktionsfarm og en varm standby-genoprettelsesfarm**

![Topologi for en SharePoint og en varm standby-genoprettelsesfarm.](../media/AZarch-AZWarmStndby.png)

I dette diagram:

- To miljøer vises side om side: den lokale SharePoint og den varme standbyfarm i Azure.

- Hvert miljø indeholder en filshare.

- Hver farm indeholder fire niveauer. For at opnå høj tilgængelighed omfatter hvert niveau to servere eller virtuelle computere, der er konfigureret identisk til en bestemt rolle, f.eks. front end-tjenester, distribueret cache, back end-tjenester og databaser. Det er ikke vigtigt i denne illustration at kalde bestemte komponenter op. De to farme er konfigureret identisk.

- Det fjerde niveau er databaseniveauet. Logforsendelse bruges til at kopiere logfiler fra den sekundære databaseserver i det lokale miljø til filsharen i det samme miljø.

- DFSR kopierer filer fra filsharen i det lokale miljø til filsharen i Azure-miljøet.

- Logforsendelse genafspiller logfilerne fra filsharen i Azure-miljøet til den primære replika i SQL Server AlwaysOn-tilgængelighedsgruppen i genoprettelsesmiljøet.

### <a name="cold-standby-environments"></a>Miljøer med iskold standby

I et iskoldt standbymiljø kan de SharePoint farmens virtuelle maskiner lukkes ned. (Vi anbefaler indimellem at starte de virtuelle maskiner, f.eks. hver anden uge eller én gang om måneden, så hver virtuel maskine kan synkronisere med domænet.) Følgende virtuelle maskiner i Azure-genoprettelsesmiljøet skal fortsat køre for at sikre kontinuerlige logforsendelser og DFSR:

- Filsharen

- Den primære databaseserver

- Mindst én virtuel maskine, der kører Windows Server Active Directory-domæneservices og DNS

I følgende figur vises et Azure failover-miljø, hvor den virtuelle maskine til fildeling og den primære SharePoint-database virtuel maskine kører. Alle andre SharePoint virtuelle computere stoppes. Den virtuelle maskine, der kører Windows Server Active Directory og DNS, vises ikke.

**Figur: Genoprettelsesfarm med iskold standby med kørende virtuelle maskiner**

![Elementer i en SharePoint i Azure.](../media/AZarch-AZColdStndby.png)

Når failover er indstillet til et cold standby-miljø, startes alle virtuelle maskiner, og metoden til at opnå høj tilgængelighed af databaseserverne skal konfigureres, f.eks. SQL Server AlwaysOn-tilgængelighedsgrupper.

Hvis der implementeres flere lagergrupper (databaser er spredt over mere end ét SQL Server sæt med høj tilgængelighed), skal den primære database for hver lagergruppe køre for at acceptere de logfiler, der er knyttet til dens lagergruppe.

### <a name="skills-and-experience"></a>Færdigheder og erfaring

Der bruges flere teknologier i denne løsning til genoprettelse efter nedbrud. For at sikre at disse teknologier interagerer som forventet, skal hver komponent i det lokale miljø og Azure-miljøet være installeret og konfigureret korrekt. Vi anbefaler, at den person eller det team, der konfigurerer denne løsning, har en stærk arbejdsviden om og praktiske færdigheder med de teknologier, der er beskrevet i følgende artikler:

- [Distributed File System (DFS) Replication Services](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj127250(v=ws.11))

- [Windows WSFC (Server Failover Clustering) med SQL Server](/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server)

- [AlwaysOn-tilgængelighedsgrupper (SQL Server)](/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server)

- [Sikkerhedskopiering og gendannelse af SQL Server databaser](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)

- [SharePoint Server 2013-installation og farminstallation](/SharePoint/install/installation-and-configuration-overview)

- [Microsoft Azure](/azure/)

Endelig anbefaler vi scripting-færdigheder, som du kan bruge til at automatisere opgaver, der er knyttet til disse teknologier. Det er muligt at bruge de tilgængelige brugergrænseflader til at udføre alle de opgaver, der er beskrevet i denne løsning. En manuel tilgang kan dog være tidskrævende, og der kan være fejl, og der leveres inkonsekvente resultater.

Ud over Windows PowerShell findes der også Windows PowerShell til SQL Server, SharePoint Server og Azure. Glem ikke T-SQL, som også kan hjælpe med at reducere tiden til konfiguration og vedligeholdelse af dit miljø til genoprettelse efter nedbrud.

## <a name="disaster-recovery-roadmap"></a>Roadmap til genoprettelse efter nedbrud

![Visuel repræsentation af SharePoint for genoprettelse efter nedbrud.](../media/Azure-DRroadmap.png)

Denne oversigt forudsætter, at du allerede har en SharePoint Server 2013-farm, der er implementeret i produktion.

**Tabel: Oversigt over genoprettelse efter nedbrud**

|Fase|Beskrivelse|
|---|---|
|Fase 1|Design genoprettelsesmiljøet efter nedbrud.|
|Fase 2|Opret Azures virtuelle netværk og VPN-forbindelse.|
|Fase 3|Installér Windows Active Directory og Domain Name Services til det virtuelle Azure-netværk.|
|Fase 4|Installér SharePoint-genoprettelsesfarmen i Azure.|
|Fase 5|Konfigurer DFSR mellem farmene.|
|Fase 6|Konfigurer logfilforsendelse til genoprettelsesfarmen.|
|Fase 7|Valider failover- og genoprettelsesløsninger. Dette omfatter følgende procedurer og teknologier: <br/> Stop logforsendelse. <br/> Gendan sikkerhedskopierne. <br/> Gennemsøg indhold. <br/> Gendan tjenester. <br/> Administrere DNS-poster.|

## <a name="phase-1-design-the-disaster-recovery-environment"></a>Fase 1: Design genoprettelsesmiljøet efter nedbrud

Brug vejledningen i [Microsoft Azure Architectures til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) til at designe miljøet for genoprettelse efter nedbrud, herunder SharePoint-genoprettelsesfarm. Du kan bruge grafikken i SharePoint [genoprettelse efter nedbrud i Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio til at starte designprocessen. Vi anbefaler, at du designer hele miljøet, før du påbegynder arbejdet i Azure-miljøet.

Ud over vejledningen i [Microsoft Azure Architectures til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) til design af det virtuelle netværk, VPN-forbindelsen, Active Directory og SharePoint-farmen, skal du sørge for at føje en filsharerolle til Azure-miljøet.

For at understøtte logfil-levering i en løsning til genoprettelse efter nedbrud føjes en virtuel maskine til fildeling til det undernet, hvor databaserollerne er placeret. Filsharen fungerer også som den tredje node af et Node-flertal for SQL Server AlwaysOn-tilgængelighedsgruppe. Dette er den anbefalede konfiguration for en standard SharePoint farm, der bruger SQL Server AlwaysOn-tilgængelighedsgrupper.

> [!NOTE]
> Det er vigtigt at gennemgå forudsætningerne for, at en database kan deltage i en SQL Server AlwaysOn-tilgængelighedsgruppe. Du kan finde flere [oplysninger under Forudsætninger, Begrænsninger og Anbefalinger til AlwaysOn-tilgængelighedsgrupper](/sql/database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability).

**Figur: Placeringen af en filserver, der bruges til en løsning til genoprettelse efter nedbrud**

![Viser et filshare VM, der er føjet til den samme skybaserede tjeneste, som indeholder SharePoint databaseserverroller.](../media/AZenv-FSforDFSRandWSFC.png)

I dette diagram føjes en virtuel maskine til filshare til det samme undernet i Azure, der indeholder databaseserverrollerne. Undlad at føje fildelings virtuel maskine til et tilgængelighedssæt med andre serverroller, f.eks. SQL Server roller.

Hvis du er bekymret over den høje tilgængelighed af logfilerne, kan du overveje at tage en anden tilgang ved [at bruge SQL Server sikkerhedskopiering og gendannelse med Azure Blob Storage service](/sql/relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service). Dette er en ny funktion i Azure, der gemmer logfiler direkte i en URL-adresse til blob-lagerplads. Denne løsning omfatter ikke vejledning i brug af denne funktion.

Når du designer genoprettelsesfarmen, skal du huske på, at et vellykket genoprettelsesmiljø efter nedbrud nøjagtigt afspejler den produktionsfarm, du vil gendanne. Størrelsen på genoprettelsesfarmen er ikke det vigtigste i genoprettelsesfarmens design, installation og test. Farmskalaen varierer fra organisation til organisation baseret på forretningskrav. Det kan være muligt at bruge en nedskaleret farm til en kort nedetid, eller indtil ydeevne- og kapacitetsbehov kræver, at du skalerer farmen.

Konfigurer genoprettelsesfarmen så identisk som muligt med produktionsfarmen, så den opfylder serviceaftalekravene (SLA) og giver den funktionalitet, du skal bruge til at understøtte din virksomhed. Når du designer genoprettelsesmiljøet efter nedbrud, skal du også se på processen for administration af ændringer i produktionsmiljøet. Vi anbefaler, at du udvider ændringsprocessen til genoprettelsesmiljøet ved at opdatere genoprettelsesmiljøet med samme interval som produktionsmiljøet. Som en del af processen til styring af ændringer anbefaler vi, at du vedligeholder en detaljeret oversigt over din farmkonfiguration, dine programmer og dine brugere.

## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Fase 2: Opret det virtuelle Azure-netværk og VPN-forbindelsen

[Forbind et lokalt netværk til et virtuelt Microsoft Azure-netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) viser, hvordan du planlægger og installerer det virtuelle netværk i Azure, og hvordan du opretter VPN-forbindelsen. Følg vejledningen i emnet for at fuldføre følgende procedurer:

- Planlæg det private IP-adresseområde for Virtual Network.

- Planlæg ændringer af routinginfrastrukturen for Virtual Network.

- Planlæg firewallregler for trafik til og fra den lokale VPN-enhed.

- Opret det virtuelle netværk på tværs af det lokale miljø i Azure.

- Konfigurer routing mellem dit lokale netværk og Virtual Network.

## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Fase 3: Udrul Active Directory og Domain Name Services til Det virtuelle Azure-netværk

Denne fase omfatter implementering af både Windows Server Active Directory og DNS til Virtual Network i et hybridscenarie som beskrevet i [Microsoft Azure Architectures for SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) og som vist i følgende figur.

**Figur: Hybrid Active Directory-domænekonfiguration**

![To virtuelle maskiner, der er installeret på det virtuelle Azure-netværk, og SharePoint Farm-undernettet er replikeringsdomænecontrollere og DNS-servere.](../media/AZarch-HyADdomainConfig.png)

I illustrationen installeres to virtuelle maskiner på det samme undernet. Disse virtuelle maskiner er hver vært for to roller: Active Directory og DNS.

Før du installerer Active Directory i Azure, skal [du læse Retningslinjer for Windows Server Active Directory på Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Disse retningslinjer hjælper dig med at afgøre, om du har brug for en anden arkitektur eller forskellige konfigurationsindstillinger for din løsning.

Du kan finde en detaljeret vejledning til konfiguration af en domænecontroller i Azure under [Installere en Replica Active Directory domænecontroller i Azure Virtual Networks](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100).

Før denne fase installerede du ikke virtuelle maskiner på Virtual Network. De virtuelle maskiner til at hoste Active Directory og DNS er sandsynligvis ikke de største virtuelle computere, du skal bruge til løsningen. Før du installerer disse virtuelle maskiner, skal du først oprette den største virtuelle maskine, du vil bruge i din Virtual Network. Dette er med til at sikre, at din løsning lander på et mærke i Azure, der giver den største størrelse, du har brug for. Du behøver ikke at konfigurere denne virtuelle maskine på nuværende tidspunkt. Bare opret den, og sæt den til side. Hvis du ikke gør dette, kan du løbe ind i en begrænsning, når du forsøger at oprette større virtuelle computere senere, hvilket var et problem på det tidspunkt, hvor denne artikel blev skrevet.

## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Fase 4: Installer SharePoint-genoprettelsesfarm i Azure

Installér SharePoint-farmen i Virtual Network i henhold til dine designplaner. Det kan være nyttigt at gennemgå [Planlægning af SharePoint 2013 på Azure Infrastructure Services](/previous-versions/azure/dn275958(v=azure.100)), før du installerer SharePoint roller i Azure.

Overvej følgende fremgangsmåder, som vi har lært, ved at bygge vores konceptbevismiljø:

- Opret virtuelle maskiner ved hjælp Azure Portal eller PowerShell.

- Azure og Hyper-V understøtter ikke dynamisk hukommelse. Sørg for, at dette er med i dine ydeevne- og kapacitetsplaner.

- Genstart virtuelle computere via Azure-grænsefladen, ikke fra logon til den virtuelle maskine. Brug af Azure-grænsefladen fungerer bedre og er mere forudsigeligt.

- Hvis du vil lukke en virtuel maskine for at spare omkostninger, skal du bruge Azure-grænsefladen. Hvis du lukker fra virtual machine-logon, periodiseres gebyrer fortsat.

- Brug en navngivningskonvention for de virtuelle computere.

- Vær opmærksom på, hvilken datacenterplacering de virtuelle computere installeres på.

- Funktionen til automatisk skalering i Azure understøttes ikke for SharePoint roller.

- Konfigurer ikke elementer i den farm, der skal gendannes, f.eks. grupper af websteder.

## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Fase 5: Konfigurer DFSR mellem farmene

Hvis du vil konfigurere filreplikering ved hjælp af DFSR, skal du bruge snap-in'en DNS-administration. Før DFSR-konfigurationen skal du dog logge på din lokale filserver og Azure-filserver og aktivere tjenesten Windows.

Fra Dashboard til Serverstyring skal du udføre følgende trin:

- Konfigurere den lokale server.

- Start guiden **Tilføj roller og funktioner**.

- Åbn **noden Filer Storage Services**.

- Vælg **DFS-navneområder og** **DFS-replikering**.

- Klik **på Næste** for at afslutte trinnene i guiden.

Den følgende tabel indeholder links til DFSR-referenceartikler og blogindlæg.

**Tabel: Referenceartikler til DFSR**

|Titel|Beskrivelse|
|---|---|
|[Replikering](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770278(v=ws.11))|TechNet-emne for DFS-administration med links til replikering|
|[DFS-replikering: Overlevelsesvejledning](https://go.microsoft.com/fwlink/p/?LinkId=392737)|Wiki med links til DFS-oplysninger|
|[DFS-replikering: Ofte stillede spørgsmål](/previous-versions/windows/it-pro/windows-server-2003/cc773238(v=ws.10))|TechNet-emne for DFS-replikering|
|[Blogs Barreto's Blog](/archive/blogs/josebda/)|Blog skrevet af en Principal Program Manager på File Server-teamet hos Microsoft|
|[The Storage team at Microsoft - File Cabinet Blog](https://go.microsoft.com/fwlink/p/?LinkId=392740)|Blog om filtjenester og lagringsfunktioner i Windows Server|

## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Fase 6: Konfigurer logforsendelse til genoprettelsesfarmen

Logforsendelse er den vigtige komponent til konfiguration af genoprettelse efter nedbrud i dette miljø. Du kan bruge logforsendelse til automatisk at sende transaktionslogfiler til databaser fra en primær databaseserverforekomst til en sekundær databaseserverforekomst. Hvis du vil konfigurere logforsendelse, [skal du se Konfigurer logforsendelse SharePoint 2013](/sharepoint/administration/configure-log-shipping).

> [!IMPORTANT]
> Understøttelse af logforsendelse SharePoint server er begrænset til visse databaser. Du kan finde flere oplysninger [under Understøttet høj tilgængelighed og muligheder for gendannelse efter nedbrud SharePoint databaser (SharePoint 2013)](/SharePoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas).

## <a name="phase-7-validate-failover-and-recovery"></a>Fase 7: Valider failover og genoprettelse

Målet for denne sidste fase er at bekræfte, at genoprettelse efter nedbrud fungerer som planlagt. For at gøre dette skal du oprette en failoverhændelse, der lukker produktionsfarmen og starter genoprettelsesfarmen som en erstatning. Du kan starte et failoverscenarie manuelt eller ved hjælp af scripts.

Det første trin er at stoppe indgående brugeranmodninger om farmtjenester eller indhold. Det kan du gøre ved at deaktivere DNS-poster eller ved at lukke front end-webservere. Når farmen er "nede", kan du mislykkes til genoprettelsesfarmen.

### <a name="stop-log-shipping"></a>Stop logforsendelse

Du skal stoppe logforsendelse før farmgendannelse. Stop logforsendelsen på den sekundære server i Azure først, og stop den derefter på den primære server i det lokale miljø. Brug følgende script til at stoppe logforsendelsen på den sekundære server først og derefter på den primære server. Databasenavnene i scriptet kan være forskellige afhængigt af dit miljø.

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

Sikkerhedskopier skal gendannes i den rækkefølge, de blev oprettet i. Før du kan gendanne en bestemt sikkerhedskopi af en transaktionslog, skal du først gendanne de følgende tidligere sikkerhedskopieringer uden at tilbageføre ikke-bekræftede transaktioner (det vil sige ved hjælp af  `WITH NORECOVERY`):

- Sikkerhedskopiering af hele databasen og den sidste difference sikkerhedskopi – Gendan disse sikkerhedskopier, hvis der findes nogen, som er taget før den pågældende sikkerhedskopiering af transaktionsloggen. Før den seneste sikkerhedskopiering af fuld eller forskellig database blev oprettet, brugte databasen den fulde gendannelsesmodel eller masseloggendannelsesmodel.

- Alle sikkerhedskopier af transaktionslogfiler – Gendan alle sikkerhedskopier af transaktionslogfiler, der er taget efter den fulde sikkerhedskopiering af databasen eller den anden sikkerhedskopiering (hvis du gendanner en) og før den pågældende sikkerhedskopiering af transaktionsloggen. Sikkerhedskopier af logge skal anvendes i den rækkefølge, de blev oprettet i, uden mellemrum i logkæden.

Hvis du vil gendanne indholdsdatabasen på den sekundære server, så webstederne gengives, skal du fjerne alle databaseforbindelser før gendannelse. Hvis du vil gendanne databasen, skal du køre følgende SQL sætning.

```SQL
restore database WSS_Content with recovery
```

> [!IMPORTANT]
> Når du bruger T-SQL eksplicit, skal du angive enten MED **NORECOVERY** eller **MED** GENDANNELSE i hver GENDANNELSE-sætning for at fjerne tvetydighed – dette er meget vigtigt, når du skriver scripts. Når de fulde og differencede sikkerhedskopier er gendannet, kan transaktionslogfilerne gendannes SQL Server Management Studio. Fordi logforsendelse allerede er stoppet, er indholdsdatabasen i standby, så du skal ændre tilstanden til fuld adgang.

I SQL Server Management Studio skal du højreklikke på **WSS_Content-databasen**, pege på **TasksRestore** >  og derefter klikke på Transaktionslog **(hvis** du ikke har gendannet den fulde sikkerhedskopi, er dette ikke tilgængeligt). Du kan finde flere oplysninger [underGenopret en sikkerhedskopiering af transaktionslogfil (SQL Server)](/sql/relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server).

### <a name="crawl-the-content-source"></a>Gennemsøg indholdskilden

Du skal starte en fuld gennemsøgning for hver indholdskilde for at gendanne søgetjenesten. Bemærk, at du mister nogle analyseoplysninger fra den lokale farm, f.eks. søgeanbefalinger. Før du starter den fulde gennemsøgning, skal du bruge Windows PowerShell-cmdlet'en **Restore-SPEnterpriseSearchServiceApplication** og angive den logsendte og replikerede søgeadministrationsdatabase **, Search_Service__DB_\<GUID\>**. Denne cmdlet giver søgekonfigurationen, skemaet, administrerede egenskaber, regler og kilder og opretter et standardsæt af de andre komponenter.

Hvis du vil starte en fuld gennemsøgning, skal du udføre følgende trin:

1. I dialogboksen SharePoint 2013 Central administration skal du gå til **Application ManagementService** >  **ApplicationsManage-tjenesteprogrammer** >  og derefter klikke på det søgetjenesteprogram, du vil gennemsøge.

2. På siden **Administration af søgning** skal du klikke på Indholdskilder **, pege** på den ønskede indholdskilde, klikke på pilen og derefter klikke på **Start fuld gennemsøgning**.

### <a name="recover-farm-services"></a>Gendan farmtjenester

Følgende tabel viser, hvordan du gendanner tjenester, der har logfiler over databaser, de tjenester, der har databaser, men som ikke anbefales at gendanne med logforsendelse, og de tjenester, der ikke har databaser.

> [!IMPORTANT]
> Gendannelse af en lokal SharePoint-database i Azure-miljøet gendanner ikke nogen SharePoint-tjenester, du ikke allerede har installeret i Azure manuelt.

**Tabel: Databasereference for tjenesteprogram**

|Gendan disse tjenester fra logfiler|Disse tjenester har databaser, men vi anbefaler, at du starter disse tjenester uden at gendanne deres databaser|Disse tjenester lagrer ikke data i databaser; start disse tjenester efter failover|
|---|---|---|
|Maskinoversættelsestjeneste <br/> Administreret Metadata Service <br/> Sikker Store tjeneste <br/> Brugerprofil. Det er kun profildatabaser og databaser til mærkning af sociale medier, der understøttes. Synkroniseringsdatabasen understøttes ikke. <br/> Microsoft SharePoint Foundation-abonnement Indstillinger tjeneste|Indsamling af forbrugs- og tilstandsdata <br/> Offentlig tjeneste <br/> Automatisering af Word|Excel-tjenester <br/> PerformancePoint Services <br/> PowerPoint konvertering <br/> Visio Graphics Service <br/> Arbejdsstyring|

I følgende eksempel vises det, hvordan du gendanner tjenesten Administrerede metadata fra en database.

Dette bruger den eksisterende Managed_Metadata_DB-database. Denne database er afsendt, men der er ikke noget aktivt tjenesteprogram på den sekundære farm, så den skal oprettes forbindelse, når tjenesteprogrammet er på plads.

Først skal du bruge  `New-SPMetadataServiceApplication`, og angive parameteren  `DatabaseName` med navnet på den gendannede database.

Derefter skal du konfigurere det nye administrerede Metadata Service-program på den sekundære server på følgende måde:

- Navn: Administreret Metadata Service

- Databaseserver: Databasenavnet fra den afsendte transaktionslog

- Databasenavn: Managed_Metadata_DB

- Programgruppe: SharePoint-tjenesteprogrammer

### <a name="manage-dns-records"></a>Administrere DNS-poster

Du skal oprette DNS-poster manuelt, så de peger på SharePoint farm.

I de fleste tilfælde, hvor du har flere front end-webservere, giver det mening at drage fordel af funktionen justering af belastning af netværk i Windows Server 2012 eller en hardwarebelastningsbalancer for at distribuere anmodninger mellem web-front end-serverne i din farm. Justering af belastning af netværk kan også hjælpe med at reducere risikoen ved at distribuere anmodninger til de andre servere, hvis en af dine web-front end-servere mislykkes.

Når du konfigurerer justering af belastning af netværk, tildeles din klynge typisk en enkelt IP-adresse. Du opretter derefter en DNS-værtspost i DNS-udbyderen for dit netværk, der peger på klyngen. (I dette projekt sætter vi en DNS-server i Azure for fleksibilitet i tilfælde af fejl i et lokalt datacenter.) Du kan f.eks. oprette en DNS-post i DNS Manager i Active Directory,  `https://sharepoint.contoso.com`f.eks. kaldet , der peger på IP-adressen for din indlæsningsbalancerede klynge.

For ekstern adgang til din SharePoint-farm kan du oprette en værtspost på en ekstern DNS-server med samme URL-adresse, `https://sharepoint.contoso.com`som klienter bruger på dit intranet (f.eks. ), der peger på en ekstern IP-adresse i din firewall. (Den bedste fremgangsmåde, når du bruger dette eksempel, er at konfigurere opdelt DNS, så den interne DNS-server er autoritativ i forbindelse med og dirigerer anmodninger direkte til SharePoint-farmklyngen i stedet for `contoso.com` at dirigere DNS-anmodninger til din eksterne DNS-server). Du kan derefter knytte den eksterne IP-adresse til den interne IP-adresse for din lokale klynge, så klienter finder de ressourcer, de leder efter.

Herfra kan du løbe ind i et par forskellige scenarier for gendannelse efter nedbrud:

 **Eksempelscenarie: Den lokale SharePoint farm er ikke tilgængelig på grund af hardwarefejl i den lokale SharePoint farm.** I dette tilfælde kan du, når du har fuldført trinnene for failover til Azure SharePoint-farmen SharePoint, konfigurere justering af belastning af netværk på genoprettelsesfarmens web front end-servere på samme måde, som du gjorde med den lokale farm. Du kan derefter omdirigere værtsposten i din interne DNS-udbyder, så den peger på genoprettelsesfarmens klynge-IP-adresse. Bemærk, at det kan tage lidt tid, før cachelagrede DNS-poster på klienter opdateres og peger på genoprettelsesfarmen.

 **Eksempelscenarie: Det lokale datacenter går helt tabt.** Dette scenarie kan forekomme på grund af naturlige nedbrud, f.eks. en brand eller vand. I dette tilfælde vil du for en virksomhed sandsynligvis have et sekundært datacenter, der er hostet i et andet område, samt dit Azure-undernet, der har sine egne katalogtjenester og DNS. Som i det forrige scenarie kan du omdirigere dine interne og eksterne DNS-poster, så de peger på Azure SharePoint-farmen. Igen skal du bemærke, at overførsel af DNS-poster kan tage noget tid.

Hvis du bruger værtsnavngivet grupper af websteder som anbefalet i værtsnavngivet arkitektur og installation af grupper af websteder [(SharePoint 2013),](/SharePoint/administration/host-named-site-collection-architecture-and-deployment) har du muligvis flere grupper af websteder hostet af det samme webprogram i din SharePoint-farm med entydige DNS-navne (f.eks. `https://sales.contoso.com` og `https://marketing.contoso.com`). I dette tilfælde kan du oprette DNS-poster for hver gruppe af websteder, der peger på DIN klynges IP-adresse. Når en anmodning når frem SharePoint-front end-web-end-servere, håndterer de routing af hver anmodning til den relevante gruppe af websteder.

## <a name="microsoft-proof-of-concept-environment"></a>Microsofts koncept-proof-of-concept-miljø

Vi har designet og testet et koncepttestmiljø for denne løsning. Designmålet for vores testmiljø var at installere og gendanne en SharePoint farm, som vi kunne finde i et kundemiljø. Vi har lavet flere forudsætninger, men vi vidste, at farmen var nødvendig for at levere alle de avancerede funktioner uden nogen tilpasninger. Topologien er udviklet til høj tilgængelighed ved hjælp af vejledning i bedste praksis fra feltet og produktgruppen.

I følgende tabel beskrives de virtuelle Hyper-V-computere, som vi har oprettet og konfigureret for det lokale testmiljø.

**Tabel: Virtuelle maskiner til test i det lokale miljø**

|Servernavn|Rolle|Konfiguration|
|---|---|---|
|DC1|Domænecontroller med Active Directory.|To processorer <br/> Fra 512 MB til 4 GB RAM <br/> 1 x 127-GB harddisk|
|RRAS|Server konfigureret med rollen Routing and Remote Access Service (RRAS).|To processorer <br/> 2-8 GB RAM <br/> 1 x 127-GB harddisk|
|FS1|Filserver med shares til sikkerhedskopiering og et slutpunkt for DFSR.|Fire processorer <br/> 2-12 GB RAM <br/> 1 x 127-GB harddisk <br/> 1 x 1-TB harddisk (SAN) <br/> 1 x 750 GB harddisk|
|SP-WFE1, SP-WFE2|Front end-webservere.|Fire processorer <br/> 16 GB RAM|
|SP-APP1, SP-APP2, SP-APP3|Programservere.|Fire processorer <br/> 2-16 GB RAM|
|SP-SQL-HA1, SP-SQL-HA2|Databaseservere, konfigureret med SQL Server 2012 AlwaysOn-tilgængelighedsgrupper for at give høj tilgængelighed. Denne konfiguration bruger SP-SQL-HA1 og SP-SQL-HA2 som de primære og sekundære replikaer.|Fire processorer <br/> 2-16 GB RAM|

I følgende tabel beskrives drevkonfigurationer til de virtuelle Hyper-V-computere, som vi har oprettet og konfigureret til front end web- og programservere til det lokale testmiljø.

**Tabel: Krav til virtuel maskine drev til Front End Web- og Programservere til test i det lokale miljø**

|Drevbogstav|Størrelse|Mappenavn|Sti|
|---|---|---|---|
|C|80|Systemdrev|\<DriveLetter\>:\\Programfiler\\ Microsoft SQL Server\\|
|E|80|Logdrev (40 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|80|Side (36 GB)|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQLDATA\\|

I følgende tabel beskrives drevkonfigurationer til de virtuelle Hyper-V-computere, der er oprettet og konfigureret til at fungere som de lokale databaseservere. På siden **Konfiguration af databaseprogram** skal du åbne fanen **Datamapper** for at angive og bekræfte de indstillinger, der er vist i følgende tabel.

**Tabel: Krav til virtuel maskine-drev til databaseserveren for den lokale test**

|Drevbogstav|Størrelse|Mappenavn|Sti|
|---|---|---|---|
|C|80|Datarodsmappe|\<DriveLetter\>:\\Programfiler\\ Microsoft SQL Server\\|
|E|500|Brugerdatabasemappe|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|F|500|Logfilmappe for brugerdatabase|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|G|500|Temp DB-mappe|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|
|H|500|Temp DB-logmappe|\<DriveLetter\>:\\Program Files\\ Microsoft SQL Server\\ MSSQL10_50.MSSQLSERVERMSSQLDATA\\\\|

### <a name="setting-up-the-test-environment"></a>Konfiguration af testmiljøet

I løbet af de forskellige installationsfaser har testteamet typisk arbejdet på den lokale arkitektur først og derefter på det tilsvarende Azure-miljø. Dette afspejler de generelle virkelige tilfælde, hvor lokale produktionsfarme allerede kører. Hvad der er endnu mere vigtigt er, at du skal kende den aktuelle produktionsbelastning, kapacitet og den typiske ydeevne. Ud over at opbygge en model for genoprettelse efter nedbrud, der kan opfylde forretningskravene, skal du ændre størrelsen på genoprettelsesfarmserverne, så de leverer et minimum af serviceniveau. I et iskoldt eller varmt standbymiljø er en genoprettelsesfarm typisk mindre end en produktionsfarm. Når genoprettelsesfarmen er stabil og i produktion, kan farmen skaleres op og ud for at opfylde krav til arbejdsbelastning.

Vi har implementeret vores testmiljø i følgende tre faser:

- Konfigurer hybridinfrastrukturen

- Klargør serverne

- Installér SharePoint farme

#### <a name="set-up-the-hybrid-infrastructure"></a>Konfigurer hybridinfrastrukturen

Denne fase omfattede konfiguration af et domænemiljø til den lokale farm og til genoprettelsesfarmen i Azure. Ud over de normale opgaver, der er knyttet til konfiguration af Active Directory, implementerede testteamet en routingløsning og en VPN-forbindelse mellem de to miljøer.

#### <a name="provision-the-servers"></a>Klargør serverne

Ud over farmserverne var det nødvendigt at klargøre servere til domænecontrollere og konfigurere en server til at håndtere RRAS samt site-to-site VPN. To filservere blev klargjort til DFSR-tjenesten, og flere klientcomputere blev klargjort til testerne.

#### <a name="deploy-the-sharepoint-farms"></a>Installér SharePoint farme

Farmene SharePoint to faser for at forenkle miljøstabilisering og fejlfinding, hvis det er nødvendigt. I første fase blev hver farm installeret på det mindste antal servere for hvert niveau af topologien for at understøtte den nødvendige funktionalitet.

Vi oprettede databaseserverne med SQL Server installeret, før vi oprettede de SharePoint 2013-servere. Da dette var en ny installation, oprettede vi tilgængelighedsgrupperne, før vi SharePoint. Vi har oprettet tre grupper baseret på vejledning i bedste praksis for MCS.

> [!NOTE]
> Opret pladsholderdatabaser, så du kan oprette tilgængelighedsgrupper, SharePoint installationen. Få mere at vide under [Konfigurer SQL Server 2012 AlwaysOn-tilgængelighedsgrupper for SharePoint 2013](/SharePoint/administration/configure-an-alwayson-availability-group)

Vi oprettede farmen og sammenføjede yderligere servere i følgende rækkefølge:

- Klargør SP-SQL-HA1 og SP-SQL-HA2.

- Konfigurer AlwaysOn, og opret de tre tilgængelighedsgrupper for farmen.

- Klargør SP-APP1 som vært for Central administration.

- Klargør SP-WFE1 og SP-WFE2 til at hoste den distribuerede cache.

Vi brugte  _parameteren skipRegisterAsDistributedCachehost_ , da **vipsconfig.exe** på kommandolinjen. Få mere at vide under [Planlægning af feeds og tjenesten Distribueret cache i SharePoint Server 2013](/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service).

Vi har gentaget følgende trin i genoprettelsesmiljøet:

- Klargør AZ-SQL-HA1 og AZ-SQL-HA2.

- Konfigurer AlwaysOn, og opret de tre tilgængelighedsgrupper for farmen.

- Klargør AZ-APP1 som vært for central administration.

- Klargør AZ-WFE1 og AZ-WFE2 til at hoste den distribuerede cache.

Når vi har konfigureret den distribuerede cache og tilføjet testbrugere og testindhold, startede vi fase to af installationen. Dette kræver skalering af niveauerne og konfiguration af farmservere for at understøtte den topologi med høj tilgængelighed, der er beskrevet i farmarkitekturen.

I følgende tabel beskrives de virtuelle maskiner, undernet og tilgængelighedssæt, vi har konfigureret til vores genoprettelsesfarm.

**Tabel: Genoprettelsesfarminfrastruktur**

|Servernavn|Rolle|Konfiguration|Undernet|Tilgængelighedssæt|
|---|---|---|---|---|
|spDRAD|Domænecontroller med Active Directory|To processorer <br/> Fra 512 MB til 4 GB RAM <br/> 1 x 127-GB harddisk|sp-ADservers||
|AZ-SP-FS|Filserver med shares til sikkerhedskopier og et slutpunkt til DFSR|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM <br/> 1 x 127-GB harddisk <br/> 1 x 135 GB harddisk <br/> 1 x 127-GB harddisk <br/> 1 x 150 GB harddisk|sp-databaseservere|DATA_SET|
|AZ-WFE1, AZ-WFE2|Front End Web-servere|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM <br/> 1 x 127-GB harddisk|sp-webservere|WFE_SET|
|AZ-APP1, AZ -APP2, AZ-APP3|Programservere|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM <br/> 1 x 127-GB harddisk|sp-applicationservers|APP_SET|
|AZ-SQL-HA1, AZ-SQL-HA2|Databaseservere og primære og sekundære replikaer for AlwaysOn-tilgængelighedsgrupper|A5-konfiguration: <br/> To processorer <br/> 14 GB RAM|sp-databaseservere|DATA_SET|

### <a name="operations"></a>Handlinger

Når testteamet har stabilt farmmiljøerne og fuldført funktionstests, startede de følgende handlingsopgaver, der er påkrævet for at konfigurere det lokale genoprettelsesmiljø:

- Konfigurer fulde og differencede sikkerhedskopier.

- Konfigurer DFSR på de filservere, der overfører transaktionslogfiler mellem det lokale miljø og Azure-miljøet.

- Konfigurer logforsendelse på den primære databaseserver.

- Stabilisering, validering og fejlfinding af logforsendelse efter behov. Dette omfatter identificering og dokumentation af enhver funktionsmåde, der kan medføre problemer, f.eks. netværksventetid, hvilket ville medføre logforsendelse eller DFSR-filsynkroniseringsfejl.

### <a name="databases"></a>Databaser

Vores failovertests involverede følgende databaser:

- WSS_Content

- ManagedMetadata

- Profile DB

- Synkroniser DB

- Social DB

- Hub af indholdstype (en database til en dedikeret syndikeringshub for indholdstype)

## <a name="troubleshooting-tips"></a>Tip til fejlfinding

I afsnittet beskrives de problemer, vi stødte på under vores test og deres løsninger.

### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Brugen af værktøjet Store ordadministration forårsagede fejlen "Administrerede metadatadata eller Store er ikke tilgængelig i øjeblikket."

Sørg for, at den programgruppekonto, der bruges af webprogrammet, har læseadgangstilladelse Store ord.

### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Brugerdefinerede ordsæt er ikke tilgængelige i gruppen af websteder

Kontrollér, om der mangler en tilknytning til tjenesteprogrammet mellem din gruppe af indholdswebsteder og din indholdstypehub. Desuden skal du under **skærmbilledet Administrerede metadata – \<site collection name\>** forbindelsesegenskaber sikre dig, at denne indstilling er aktiveret: Dette **tjenesteprogram er standardlagerplaceringen for kolonnespecifikke ordsæt.**

### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>Kommandoen Get-ADForest Windows PowerShell opretter fejlen, "Ordet "Get-ADForest" genkendes ikke som navnet på en cmdlet, funktion, scriptfil eller et operandeprogram."

Når du konfigurerer brugerprofiler, skal du bruge Active Directory-skovens navn. I guiden Tilføj roller og funktioner skal du sikre dig, at du har aktiveret Active Directory-modulet til Windows PowerShell (i sektionen Værktøjer til administration af **fjernservere>rolleadministrationsværktøjer>AD DS og AD LDS-værktøjer**). Kør desuden følgende kommandoer, før du bruger **Get-ADForest for** at sikre, at dine softwareafhængigheder indlæses.

```powershell
Import-Module ServerManager
Import-Module ActiveDirectory
```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Oprettelse af tilgængelighedsgrupper mislykkes ved at starte "AlwaysOn_health" XEvent-sessionen på '\<server name\>'

Sørg for, at begge noder i din failoverklynge er i Status "Op" og ikke "Afbrudt" eller "Stoppet".

### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>SQL Server med datalogforsendelsesjobbet mislykkes med fejl af dataadgang nægtet ved forsøg på at oprette forbindelse til filsharen

Kontrollér, at SQL Server Agent kører under netværkslegitimationsoplysninger i stedet for standardlegitimationsoplysninger.

### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>SQL Server logforsendelsesjob angiver succes, men ingen filer kopieres

Dette sker, fordi standardindstillingen for sikkerhedskopiering for en tilgængelighedsgruppe **foretrækker Sekundær**. Sørg for at køre logforsendelsesjobbet fra den sekundære server for tilgængelighedsgruppen i stedet for den primære; Ellers mislykkes jobbet automatisk.

### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>Administrerede metadatatjeneste (eller SharePoint tjeneste) kan ikke starte automatisk efter installation

Det kan tage flere minutter at starte tjenester, afhængigt af ydeevnen og den aktuelle belastning af SharePoint Server. Klik manuelt **på Start** for tjenesten, og angiv tilstrækkelig tid til start, mens du lejlighedsvist opdaterer skærmbilledet Tjenester på serveren for at overvåge dens status. Hvis tjenesten stoppes, skal du SharePoint logføring af diagnostik, forsøge at starte tjenesten igen og derefter kontrollere, om der er fejl i loggen. Du kan finde flere oplysninger [under Konfigurere logføring af diagnostik i SharePoint 2013](/sharepoint/administration/configure-diagnostic-logging)

### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Når DNS er blevet ændret til Azure failover-miljøet, fortsætter klientbrowsere med at bruge den gamle IP-adresse SharePoint webstedet

Din DNS-ændring er muligvis ikke synlig for alle klienter med det samme. På en testklient skal du udføre følgende kommando fra en kommandoprompt med administrator administratoradgang og forsøge at få adgang til webstedet igen.

```DOS
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Yderligere ressourcer

[Understøttede muligheder for høj tilgængelighed og genoprettelse efter nedbrud i SharePoint databaser](/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)

[Konfigurere SQL Server 2012 AlwaysOn-tilgængelighedsgrupper for SharePoint 2013](/SharePoint/administration/configure-an-alwayson-availability-group)

## <a name="see-also"></a>Se også

[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)
