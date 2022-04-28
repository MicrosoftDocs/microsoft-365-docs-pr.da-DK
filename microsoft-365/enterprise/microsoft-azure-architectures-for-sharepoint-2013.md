---
title: Microsoft Azure arkitekturer for SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: scotv
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
- seo-marvel-apr2020
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: Få mere at vide om, hvilke typer SharePoint 2013-løsninger der kan hostes i Microsoft Azure virtuelle maskiner, og hvordan du konfigurerer Azure til at hoste en.
ms.openlocfilehash: 7761eb9b62000c03b2983bc5ed56a62e20981db7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097398"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Microsoft Azure arkitekturer for SharePoint 2013

Azure er et godt miljø til hosting af en SharePoint Server 2013-løsning. I de fleste tilfælde anbefaler vi Microsoft 365, men en SharePoint Server-farm, der hostes i Azure, kan være en god mulighed for bestemte løsninger. I denne artikel beskrives det, hvordan du bygger SharePoint løsninger, så de passer godt til Azure-platformen. Følgende to specifikke løsninger bruges som eksempler:
  
- [It-katastrofeberedskab i SharePoint Server 2013 i Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Anbefalede SharePoint løsninger til Azure Infrastructure Services

Azure-infrastrukturtjenester er en overbevisende mulighed for at hoste SharePoint-løsninger. Nogle løsninger passer bedre til denne platform end andre. I følgende tabel vises anbefalede løsninger.
  
|**Løsning**|**Hvorfor denne løsning anbefales til Azure**|
|:-----|:-----|
|Udviklings- og testmiljøer  <br/> |Det er nemt at oprette og administrere disse miljøer.  <br/> |
|It-katastrofeberedskab af SharePoint farme i det lokale miljø til Azure  <br/> |**Hostet sekundært datacenter** Brug Azure i stedet for at investere i et sekundært datacenter i et andet område. <br/> **Miljøer til it-katastrofeberedskab med lavere omkostninger** Vedligehold og betal for færre ressourcer end et it-katastrofeberedskabsmiljø i det lokale miljø. Antallet af ressourcer afhænger af det it-katastrofeberedskabsmiljø, du vælger: koldt standby, varmt standby eller varmt standby. <br/> **Mere elastisk platform** I tilfælde af en katastrofe kan du nemt skalere dit genoprettelses-SharePoint farm ud, så den opfylder belastningskravene. Skaler ind, når du ikke længere har brug for ressourcerne. <br/> Se [SharePoint Server 2013 Disaster Recovery i Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Internetbaserede websteder, der bruger funktioner og skalerer, er ikke tilgængelige i Microsoft 365  <br/> |**Fokuser din indsats** Koncentrer dig om at bygge et fantastisk sted i stedet for at bygge infrastruktur. <br/> **Udnyt elasticiteten i Azure** Tilpas farmens størrelse efter behov ved at tilføje nye servere, og betal kun for de ressourcer, du har brug for. Dynamisk maskinallokering understøttes ikke (automatisk skalering). <br/> **Brug Azure Active Directory (AD)** Udnyt Azure AD til kundekonti. <br/> **Tilføj SharePoint funktionalitet, der ikke er tilgængelig i Microsoft 365** Tilføj detaljeret rapportering og webanalyse. <br/> Se [Internet Sites in Microsoft Azure using SharePoint Server 2013( Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)).  <br/> |
|Appfarme til understøttelse af Microsoft 365 eller lokale miljøer  <br/> |**Byg, test og vær vært for apps** i Azure for at understøtte både lokale miljøer og cloudmiljøer. <br/> **Vær vært for denne rolle** i Azure i stedet for at købe ny hardware til lokale miljøer. <br/> |
   
Overvej følgende muligheder for intranet- og samarbejdsløsninger og arbejdsbelastninger:
  
- Find ud af, om Microsoft 365 opfylder dine forretningskrav eller kan være en del af løsningen. Microsoft 365 indeholder et omfattende funktionssæt, der altid er opdateret.
    
- Hvis Microsoft 365 ikke opfylder alle dine forretningsmæssige krav, kan du overveje en standardimplementering af SharePoint 2013 i det lokale miljø fra Microsoft Consulting Services (MCS). En standardarkitektur kan være en hurtigere, billigere og nemmere løsning, som du kan understøtte end en tilpasset. 
    
- Hvis en standardimplementering ikke opfylder dine forretningskrav, kan du overveje en tilpasset løsning i det lokale miljø.
    
- Hvis det er vigtigt for din virksomhed at bruge en cloudplatform, kan du overveje en standardimplementering eller en tilpasset implementering af SharePoint 2013, der hostes i Azure-infrastrukturtjenester. SharePoint løsninger er meget nemmere at understøtte i Azure end andre ikke-oprindelige Microsoft-offentlige cloudplatforme.
    
## <a name="before-you-design-the-azure-environment"></a>Før du designer Azure-miljøet

I denne artikel bruges eksempel SharePoint topologier, men du kan bruge disse designbegreber sammen med en hvilken som helst SharePoint farmtopologi. Før du designer Azure-miljøet, skal du bruge følgende topologi, arkitektur, kapacitet og ydeevnevejledning til at designe SharePoint farmen:
  
- [Arkitekturdesign til SharePoint 2013-it-teknikere](/SharePoint/technical-reference/technical-diagrams)
    
- [Planlæg administration af ydeevne og kapacitet i SharePoint Server 2013](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a>Bestem Active Directory-domænetypen

Hver SharePoint Server-farm er afhængig af Active Directory til at levere administrative konti til farmkonfiguration. På nuværende tidspunkt er der to muligheder for SharePoint løsninger i Azure. Disse er beskrevet i følgende tabel.
  
|**Mulighed**|**Beskrivelse**|
|:-----|:-----|
|Dedikeret domæne  <br/> |Du kan udrulle et dedikeret og isoleret Active Directory-domæne på Azure for at understøtte din SharePoint farm. Dette er et godt valg for offentlige internetsider.  <br/> |
|Udvid domænet i det lokale miljø via en forbindelse på tværs af det lokale miljø  <br/> |Når du udvider domænet i det lokale miljø via en forbindelse på tværs af det lokale miljø, får brugerne adgang til den SharePoint farm via intranettet, som om den var hostet i det lokale miljø. Du kan drage fordel af din Active Directory i det lokale miljø og DNS-implementering.  <br/> Der kræves en forbindelse på tværs af det lokale miljø, for at der kan oprettes et it-katastrofeberedskabsmiljø i Azure, som du kan skifte til fra din farm i det lokale miljø.  <br/> |
   
Denne artikel indeholder designkoncepter til udvidelse af domænet i det lokale miljø via en forbindelse på tværs af det lokale miljø. Hvis din løsning bruger et dedikeret domæne, behøver du ikke en forbindelse på tværs af det lokale miljø.
  
## <a name="design-the-virtual-network"></a>Design det virtuelle netværk

Først skal du bruge et virtuelt netværk i Azure, som omfatter undernet, hvor du placerer dine virtuelle maskiner. Det virtuelle netværk skal bruge et privat IP-adresseområde, hvoraf dele du tildeler til undernet.
  
Hvis du udvider dit lokale netværk til Azure via en forbindelse på tværs af det lokale miljø (kræves til et it-katastrofeberedskabsmiljø), skal du vælge et privat adresseområde, der ikke allerede bruges et andet sted i organisationens netværk, hvilket kan omfatte dit lokale miljø og andre virtuelle Azure-netværk. 
  
**Figur 1: Lokalt miljø med et virtuelt netværk i Azure**

![Microsoft Azure virtuelt netværksdesign til en SharePoint løsning. Ét undernet til Azure-gatewayen. Ét undernet til de virtuelle maskiner.](../media/OPrrasconWA-AZarch.png)
  
I dette diagram:
  
- Et virtuelt netværk i Azure illustreres side om side med det lokale miljø. De to miljøer er endnu ikke forbundet via en forbindelse på tværs af det lokale miljø, som kan være en VPN-forbindelse fra websted til websted eller ExpressRoute.
    
- På nuværende tidspunkt omfatter det virtuelle netværk kun undernet og ingen andre arkitektoniske elementer. Ét undernet hoster Azure-gatewayen, og andre undernet hoster niveauerne for SharePoint farmen med et ekstra til Active Directory og DNS.
    
## <a name="add-cross-premises-connectivity"></a>Tilføj forbindelse på tværs af det lokale miljø

Det næste udrulningstrin er at oprette forbindelsen på tværs af det lokale miljø (hvis dette gælder for din løsning). I forbindelse med forbindelser på tværs af det lokale miljø er en Azure-gateway placeret i et separat gatewayundernet, som du skal oprette og tildele et adresseområde. 
  
Når du planlægger en forbindelse på tværs af det lokale miljø, definerer og opretter du en Azure-gateway og en forbindelse til en gatewayenhed i det lokale miljø.
  
**Figur 2: Brug af en Azure-gateway og en gatewayenhed i det lokale miljø til at sikre forbindelse mellem det lokale miljø og Azure**

![I det lokale miljø, der er forbundet til et virtuelt Azure-netværk via en forbindelse på tværs af det lokale miljø, som kan være en VPN-forbindelse fra websted til websted eller ExpressRoute.](../media/AZarch-VPNgtwyconnct.png)
  
I dette diagram:
  
- Hvis du føjer til det forrige diagram, er miljøet i det lokale miljø forbundet til det virtuelle Azure-netværk via en forbindelse på tværs af det lokale miljø, hvilket kan være en VPN-forbindelse fra websted til websted eller ExpressRoute.
    
- En Azure-gateway er på et gatewayundernet.
    
- Miljøet i det lokale miljø indeholder en gatewayenhed, f.eks. en router eller en VPN-server.
    
Du kan finde flere oplysninger om, hvordan du planlægger og opretter et virtuelt netværk på tværs af det lokale miljø, under [Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Tilføj Active Directory-domæneservices (AD DS) og DNS

I forbindelse med it-katastrofeberedskab i Azure installerer du Windows Server AD og DNS i et hybridt scenarie, hvor Windows Server AD udrulles både i det lokale miljø og på virtuelle Azure-maskiner.
  
**Figur 3: Konfiguration af Hybrid Active Directory-domæne**

![STwo virtuelle maskiner, der er installeret på det virtuelle Azure-netværk, og undernettet SharePoint Farm er replikadomænecontrollere og DNS-servere.](../media/AZarch-HyADdomainConfig.png)
  
Dette diagram bygger på de forrige diagrammer ved at føje to virtuelle maskiner til et Windows Server AD- og DNS-undernet. Disse virtuelle maskiner er replikadomænecontrollere og DNS-servere. De er en udvidelse af Windows Server AD-miljøet i det lokale miljø. 
  
Følgende tabel indeholder konfigurationsanbefalinger til disse virtuelle maskiner i Azure. Brug disse som udgangspunkt for at designe dit eget miljø – selv for et dedikeret domæne, hvor dit Azure-miljø ikke kommunikerer med dit lokale miljø.
  
|**Element**|**Konfiguration**|
|:-----|:-----|
|Størrelse på virtuel maskine i Azure  <br/> |A1- eller A2-størrelse på standardniveauet  <br/> |
|Operativsystem  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory-rolle  <br/> |AD DS-domænecontroller, der er angivet som en global katalogserver. Denne konfiguration reducerer udgående trafik på tværs af forbindelsen på tværs af det lokale miljø.  <br/> I et miljø med flere domæner med høje ændringshastigheder (dette er ikke almindeligt) skal du konfigurere domænecontrollere i det lokale miljø til ikke at synkronisere med de globale katalogservere i Azure for at reducere replikeringstrafikken.  <br/> |
|DNS-rolle  <br/> |Installér og konfigurer DNS-servertjenesten på domænecontrollerne.  <br/> |
|Datadisketter  <br/> |Placer Active Directory-databasen, logfilerne og SYSVOL på yderligere Azure-datadisketter. Placer ikke disse på operativsystemets disk eller de midlertidige diske, der leveres af Azure.  <br/> |
|IP-adresser  <br/> |Brug statiske IP-adresser, og konfigurer det virtuelle netværk for at tildele disse adresser til de virtuelle maskiner i det virtuelle netværk, når domænecontrollerne er konfigureret.  <br/> |
   
> [!IMPORTANT]
> Før du installerer Active Directory i Azure, skal du læse [Retningslinjer for installation af Windows Server Active Directory på Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Disse hjælper dig med at finde ud af, om der er brug for en anden arkitektur eller forskellige konfigurationsindstillinger til din løsning. 
  
## <a name="add-the-sharepoint-farm"></a>Tilføj den SharePoint farm

Placer de virtuelle maskiner på den SharePoint farm på niveauer på de relevante undernet.
  
**Figur 4: Placering af SharePoint virtuelle maskiner**

![Databaseservere og SharePoint serverroller, der er føjet til det virtuelle Azure-netværk i undernettet SharePoint Farm.](../media/AZarch-SPVMsinCloudSer.png)
  
Dette diagram bygger på de forrige diagrammer ved at tilføje SharePoint farmserverroller på deres respektive niveauer.
  
- To virtuelle databasemaskiner, der kører SQL Server oprette databaseniveauet.
    
- To virtuelle maskiner, der kører SharePoint Server 2013 for hvert af følgende niveauer: front end-servere, distribuerede cacheservere og back end-servere.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Design og finjuster serverroller for tilgængelighedssæt og fejldomæner

Et fejldomæne er en gruppering af hardware, hvor rolleforekomster kører. Virtuelle maskiner inden for det samme fejldomæne kan opdateres af Azure-infrastrukturen på samme tid. Eller de kan mislykkes på samme tid, fordi de deler den samme rack. Hvis du vil undgå risikoen for at have to virtuelle maskiner på det samme fejldomæne, kan du konfigurere dine virtuelle maskiner som et tilgængelighedssæt, der sikrer, at hver virtuelle maskine er i et andet fejldomæne. Hvis tre virtuelle maskiner er konfigureret som et tilgængelighedssæt, garanterer Azure, at ikke mere end to af de virtuelle maskiner er placeret i det samme fejldomæne.
  
Når du designer Azure-arkitekturen for en SharePoint farm, skal du konfigurere identiske serverroller, så de er en del af et tilgængelighedssæt. Dette sikrer, at dine virtuelle maskiner spredes på tværs af flere fejldomæner.
  
**Figur 5: Brug Azure-tilgængelighedssæt til at give høj tilgængelighed for de SharePoint farmniveauer**

![Konfiguration af tilgængelighedssæt i Azure-infrastrukturen for en SharePoint 2013-løsning.](../media/AZenv-WinAzureAvailSetsHA.png)
  
I dette diagram beskrives konfigurationen af tilgængelighedssæt i Azure-infrastrukturen. Hver af følgende roller deler et separat tilgængelighedssæt:
  
- Active Directory og DNS
    
- Database
    
- Back end
    
- Distribuer cache
    
- Frontend
    
Den SharePoint farm skal muligvis finjusteres på Azure-platformen. Hvis du vil sikre høj tilgængelighed af alle komponenter, skal du sikre, at alle serverrollerne er konfigureret identisk.
  
Her er et eksempel, der viser en standardarkitektur for Internet Sites, der opfylder specifikke kapacitets- og ydeevnemål. Dette eksempel er fremhævet i følgende arkitekturmodel: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Figur 6: Planlægningseksempel for kapacitet og ydeevnemål på en farm med tre niveauer**

![Standard SharePoint 2013 Internet Sites-arkitektur med komponenttildelinger, der opfylder specifikke kapacitets- og ydeevnemål.](../media/AZarch-CapPerfexmpArch.png)
  
I dette diagram:
  
- En farm med tre niveauer er repræsenteret: webservere, programservere og databaseservere.
    
- De tre webservere er konfigureret identisk med flere komponenter.
    
- De to databaseservere er konfigureret på samme måde.
    
- De tre programservere er ikke konfigureret identisk. Disse serverroller kræver finjustering af tilgængelighedssæt i Azure.
    
Lad os se nærmere på programserverniveauet.
  
**Figur 7: Programserverniveau før finjustering**

![Eksempel SharePoint Server 2013-programserverniveau, før der justeres efter Microsoft Azure tilgængelighedssæt.](../media/AZarch-AppServtierBefore.png)
  
I dette diagram:
  
- Der er tre servere inkluderet i programniveauet.
    
- Den første server indeholder fire komponenter.
    
- Den anden server indeholder tre komponenter.
    
- Den tredje server indeholder to komponenter.
    
Du bestemmer antallet af komponenter efter farmens ydeevne og kapacitetsmål. Hvis du vil tilpasse denne arkitektur til Azure, replikerer vi de fire komponenter på tværs af alle tre servere. Dette øger antallet af komponenter ud over det, der er nødvendigt for ydeevne og kapacitet. Konsekvensen er, at dette design sikrer høj tilgængelighed af alle fire komponenter på Azure-platformen, når disse tre virtuelle maskiner tildeles et tilgængelighedssæt.
  
**Figur 8: Programserverniveau efter finjustering**

![Eksempel SharePoint Server 2013-programserverniveau efter justering efter Microsoft Azure tilgængelighedssæt.](../media/AZarch-AppServtierAfter.png)
  
I dette diagram vises alle tre programservere, der er konfigureret identisk med de samme fire komponenter.
  
Når vi føjer tilgængelighedssæt til niveauerne i den SharePoint farm, er implementeringen fuldført.
  
**Figur 9: Den fuldførte SharePoint farm i Azure-infrastrukturtjenester**

![Eksempel SharePoint 2013-farm i Azure-infrastrukturtjenester med virtuelt netværk, forbindelse på tværs af det lokale miljø, undernet, VM'er og tilgængelighedssæt.](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
I dette diagram vises den SharePoint farm, der er implementeret i Azure-infrastrukturtjenester, med tilgængelighedssæt til at levere fejldomæner til serverne på hvert niveau.
  
## <a name="see-also"></a>Se også

[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)
  
[Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[It-katastrofeberedskab i SharePoint Server 2013 i Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)