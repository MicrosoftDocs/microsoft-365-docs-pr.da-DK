---
title: Microsoft Azure arkitekturer til SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
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
description: Få mere at vide om, hvilke typer af SharePoint 2013-løsninger, der kan hostes på Microsoft Azure virtuelle computere, og hvordan du konfigurerer Azure til at hoste en.
ms.openlocfilehash: 8bbaeb7a20b467625d57800cdf95f42e5b11f434
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590392"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Microsoft Azure arkitekturer til SharePoint 2013

Azure er et godt miljø til at hoste en SharePoint Server 2013-løsning. I de fleste tilfælde anbefaler vi en Microsoft 365, men en SharePoint Server-farm, der er hostet i Azure, kan være en god mulighed for bestemte løsninger. I denne artikel beskrives, hvordan du SharePoint løsninger, så de passer godt til Azure-platformen. Følgende to specifikke løsninger bruges som eksempler:
  
- [SharePoint af genoprettelse efter nedbrud på server 2013 Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Internetwebsteder i Microsoft Azure bruger SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Anbefalede SharePoint til Azure Infrastructure Services

Azure-infrastrukturtjenester er en overbevisende mulighed for at SharePoint løsninger. Nogle løsninger passer bedre til denne platform end andre. Følgende tabel viser anbefalede løsninger.
  
|**Løsning**|**Derfor anbefales denne løsning til Azure**|
|:-----|:-----|
|Udviklings- og testmiljøer  <br/> |Det er nemt at oprette og administrere disse miljøer.  <br/> |
|Genoprettelse efter nedbrud i lokale SharePoint til Azure  <br/> |**Hostet sekundært datacenter** Brug Azure i stedet for at investere i et sekundært datacenter i et andet område. <br/> **Miljø med lavere omkostninger til genoprettelse efter nedbrud** Vedligeholde og betale for færre ressourcer end et lokalt miljø til genoprettelse efter nedbrud. Antallet af ressourcer afhænger af det miljø for genoprettelse efter nedbrud, du vælger: cold standby, warm standby eller hot standby. <br/> **Mere elastic platform** I tilfælde af nedbrud kan du let skalere din genoprettelsesfarm SharePoint at opfylde krav til belastning. Skaler ind, når du ikke længere har brug for ressourcerne. <br/> Se [SharePoint Genoprettelse efter nedbrud i SharePoint i Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Internetbaserede websteder, der bruger funktioner og skalering, er ikke tilgængelige i Microsoft 365  <br/> |**Fokuser på dine bestræbelser** Koncentrer dig om at bygge et godt websted i stedet for at bygge infrastruktur. <br/> **Udnyt elasticiteten i Azure** Tilpas størrelsen på farmen til behovet ved at tilføje nye servere og kun betale for ressourcer, du har brug for. Dynamisk maskinallokering understøttes ikke (automatisk skalering). <br/> **Brug Azure Active Directory (AD)** Udnyt Azure AD til kundekonti. <br/> **Tilføj SharePoint funktionalitet, der ikke er tilgængelig Microsoft 365** Tilføj dybtgående rapportering og webanalyse. <br/> Se [Internetwebsteder i Microsoft Azure ved SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Appfarme til Microsoft 365 eller lokale miljøer  <br/> |**Byg, test og vær vært for apps** i Azure for at understøtte både lokale miljøer og skymiljøer. <br/> **Vær vært for** denne rolle i Azure i stedet for at købe ny hardware til lokale miljøer. <br/> |
   
For intranet- og samarbejdsløsninger og arbejdsbelastninger skal du overveje følgende muligheder:
  
- Afgør, Microsoft 365 opfylder virksomhedens krav eller kan være en del af løsningen. Microsoft 365 indeholder et omfattende funktionssæt, der altid er opdateret.
    
- Hvis Microsoft 365 opfylder alle virksomhedens krav, bør du overveje en standardimplementeringen af SharePoint 2013 i det lokale miljø fra Microsoft Consulting Services (MCS). En standardarkitektur kan være en hurtigere, billigere og nemmere løsning for dig at understøtte end en tilpasset løsning. 
    
- Hvis en standardimplementeringen ikke opfylder virksomhedens krav, kan du overveje en tilpasset løsning i det lokale miljø.
    
- Hvis det er vigtigt at bruge en skyplatform i overensstemmelse med virksomhedens krav, bør du overveje en standard eller tilpasset implementering af SharePoint 2013, der hostes i Azure-infrastrukturtjenester. SharePoint løsninger er meget nemmere at understøtte i Azure end andre ikke-oprindelige offentlige Microsoft-skyplatforme.
    
## <a name="before-you-design-the-azure-environment"></a>Før du designer Azure-miljøet

Mens denne artikel bruger eksempel SharePoint topologier, kan du bruge disse designkoncepter med enhver SharePoint farmtopologi. Før du designer Azure-miljøet, skal du bruge følgende topologi, arkitektur, kapacitet og ydeevnevejledning til at designe SharePoint farm:
  
- [Arkitekturdesign til SharePoint 2013 it-fagfolk](/SharePoint/technical-reference/technical-diagrams)
    
- [Planlæg ydeevne og kapacitetsstyring i SharePoint Server 2013](/SharePoint/administration/performance-planning-in-sharepoint-server-2013)
    
## <a name="determine-the-active-directory-domain-type"></a>Fastslå Active Directory-domænetypen

Hver SharePoint serverfarm er afhængig af Active Directory til at levere administrative konti til konfiguration af farmen. På nuværende tidspunkt er der to muligheder for SharePoint løsninger i Azure. Disse er beskrevet i følgende tabel.
  
|**Indstilling**|**Beskrivelse**|
|:-----|:-----|
|Dedikeret domæne  <br/> |Du kan installere et dedikeret og isoleret Active Directory-domæne i Azure for at understøtte SharePoint farm. Dette er godt for websteder, der er vendt mod offentligheden.  <br/> |
|Udvide det lokale domæne via en lokal forbindelse  <br/> |Når du udvider det lokale domæne via en lokal forbindelse, får brugerne adgang til SharePoint-farmen via dit intranet, som om den var hostet lokalt. Du kan drage fordel af din lokale Active Directory og DNS-implementering.  <br/> Der kræves en forbindelse på tværs af det lokale miljø for at skabe et miljø til genoprettelse efter nedbrud i Azure, så det mislykkes fra din lokale farm.  <br/> |
   
Denne artikel indeholder designkoncepter til udvidelse af det lokale domæne via en lokal forbindelse. Hvis din løsning bruger et dedikeret domæne, behøver du ikke en lokal forbindelse.
  
## <a name="design-the-virtual-network"></a>Design det virtuelle netværk

Du skal først bruge et virtuelt netværk i Azure, som indeholder undernet, hvor du skal placere dine virtuelle computere. Det virtuelle netværk skal have et privat IP-adresseområde, hvor du tildeler undernet.
  
Hvis du udvider dit lokale netværk til Azure via en lokal forbindelse (påkrævet til genoprettelse efter nedbrud), skal du vælge et privat adresseområde, der ikke allerede er i brug et andet sted i organisationens netværk, som kan omfatte dit lokale miljø og andre virtuelle Azure-netværk. 
  
**Figur 1: Lokalt miljø med et virtuelt netværk i Azure**

![Microsoft Azure virtuelt netværksdesign til en SharePoint løsning. Et undernet til Azure-gatewayen. Et undernet til de virtuelle computere.](../media/OPrrasconWA-AZarch.png)
  
I dette diagram:
  
- Et virtuelt netværk i Azure illustreres side om side med det lokale miljø. De to miljøer er endnu ikke forbundet med en lokal forbindelse, som kan være en websteds-til-websted-VPN-forbindelse eller ExpressRoute.
    
- På dette tidspunkt omfatter det virtuelle netværk kun undernet og ingen andre arkitektoniske elementer. Et undernet er vært for Azure-gatewayen, og andre undernet er vært for niveauerne i SharePoint-farmen med et ekstra lag for Active Directory og DNS.
    
## <a name="add-cross-premises-connectivity"></a>Tilføje forbindelse på tværs af det lokale miljø

Det næste installationstrin er at oprette en forbindelse på tværs af det lokale miljø (hvis dette gælder for din løsning). Ved forbindelser på tværs af lokale forbindelser er en Azure-gateway placeret i et separat gatewayundernet, som du skal oprette og tildele et adresseområde. 
  
Når du planlægger en forbindelse på tværs af det lokale miljø, kan du definere og oprette en Azure-gateway og forbindelse til en lokal gatewayenhed.
  
**Figur 2: Brug af en Azure-gateway og en lokal gatewayenhed til at levere forbindelse mellem websted og websted mellem det lokale miljø og Azure**

![Lokalt miljø forbundet til et virtuelt Azure-netværk via en lokal forbindelse, som kan være en websteds-til-websted-VPN-forbindelse eller ExpressRoute.](../media/AZarch-VPNgtwyconnct.png)
  
I dette diagram:
  
- Når du tilføjer til det forrige diagram, er det lokale miljø forbundet til det virtuelle Azure-netværk via en lokal forbindelse, som kan være en websteds-til-websted-VPN-forbindelse eller ExpressRoute.
    
- En Azure-gateway er på et gatewayundernet.
    
- Det lokale miljø omfatter en gatewayenhed, f.eks. en router eller VPN-server.
    
Du kan finde flere oplysninger om planlægning og oprettelse af et virtuelt netværk på tværs af lokale netværk under Forbind et lokalt netværk til et [Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Tilføj Active Directory-domæneservices (AD DS) og DNS

Ved genoprettelse efter nedbrud i Azure skal du installere Windows Server AD og DNS i et hybridscenarie, hvor Windows Server AD er installeret både lokalt og på virtuelle Azure-computere.
  
**Figur 3: Konfiguration af hybrid Active Directory-domæne**

![STwo virtual machines deployed to the Azure virtual network and the SharePoint Farm subnet are replica domain controllers and DNS servers.](../media/AZarch-HyADdomainConfig.png)
  
Dette diagram bygger på de forrige diagrammer ved at føje to virtuelle maskiner til Windows Server AD og DNS-undernet. Disse virtuelle computere er replikeringsdomænecontrollere og DNS-servere. De er en udvidelse af det lokale Windows Server AD-miljøet. 
  
Følgende tabel indeholder konfigurationsanbefalinger for disse virtuelle maskiner i Azure. Brug disse som et udgangspunkt til at designe dit eget miljø – selv for et dedikeret domæne, hvor dit Azure-miljø ikke kommunikerer med dit lokale miljø.
  
|**Element**|**Konfiguration**|
|:-----|:-----|
|Virtuel maskinestørrelse i Azure  <br/> |A1- eller A2-størrelse på standardniveau  <br/> |
|Operativsystem  <br/> |Windows Server 2012 R2  <br/> |
|Active Directory-rolle  <br/> |AD DS domænecontroller, der er angivet som en global katalogserver. Denne konfiguration reducerer udgangstrafik på tværs af den lokale forbindelse.  <br/> I et multidomænemiljø med høje ændringshastigheder (dette er ikke almindeligt) skal du konfigurere domænecontrollere lokalt til ikke at synkronisere med de globale katalogservere i Azure for at reducere replikeringstrafikken.  <br/> |
|DNS-rolle  <br/> |Installér og konfigurer DNS Server-tjenesten på domænecontrollere.  <br/> |
|Datadisks  <br/> |Placer Active Directory-databasen, logfilerne og SYSVOL på flere Azure-datadisks. Placer ikke disse på operativsystemets disk eller de midlertidige diske, der leveres af Azure.  <br/> |
|IP-adresser  <br/> |Brug statiske IP-adresser, og konfigurer det virtuelle netværk til at tildele disse adresser til de virtuelle computere i det virtuelle netværk, når domænecontrollere er blevet konfigureret.  <br/> |
   
> [!IMPORTANT]
> Før du installerer Active Directory i Azure, skal du [læse Retningslinjer for installation Windows Server Active Directory på Azure Virtual Machines](/windows-server/identity/ad-ds/introduction-to-active-directory-domain-services-ad-ds-virtualization-level-100). Disse hjælper dig med at afgøre, om der kræves en anden arkitektur eller forskellige konfigurationsindstillinger for din løsning. 
  
## <a name="add-the-sharepoint-farm"></a>Tilføje SharePoint farm

Placer de virtuelle maskiner SharePoint farmen i niveauer på de relevante undernet.
  
**Figur 4: Placering af SharePoint virtuelle maskiner**

![Databaseservere og SharePoint, der er føjet til det virtuelle Azure-netværk i SharePoint Farm-undernet.](../media/AZarch-SPVMsinCloudSer.png)
  
Dette diagram bygger på de forrige diagrammer ved at tilføje SharePoint farmserverroller i deres respektive niveauer.
  
- To virtuelle databasemaskine, der SQL Server, opretter databaseniveauet.
    
- To virtuelle maskiner, der kører SharePoint Server 2013, for hvert af følgende niveauer: front end-servere, distribuerede cacheservere og back end-servere.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Design og finjuster serverroller for tilgængelighedssæt og fejldomæner

Et fejldomæne er en gruppering af hardware, hvor rolleforekomster køres. Virtuelle maskiner inden for det samme fejldomæne kan opdateres af Azure-infrastrukturen på samme tid. Eller de kan mislykkes på samme tid, fordi de deler den samme rack. For at undgå risikoen for at have to virtuelle maskiner på det samme fejldomæne kan du konfigurere dine virtuelle computere som et tilgængelighedssæt, hvilket sikrer, at hver virtuel maskine er i et andet fejldomæne. Hvis tre virtuelle maskiner er konfigureret som et tilgængelighedssæt, garanterer Azure, at der ikke er flere end to af de virtuelle maskiner placeret i det samme fejldomæne.
  
Når du designer Azure-arkitekturen for en SharePoint, skal du konfigurere identiske serverroller, så de er en del af et tilgængelighedssæt. Dette sikrer, at dine virtuelle maskiner er spredt over flere fejldomæner.
  
**Figur 5: Brug Azure-tilgængelighedssæt til at levere høj tilgængelighed til SharePoint-farmniveauer**

![Konfiguration af tilgængelighedssæt i Azure-infrastruktur for en SharePoint 2013-løsning.](../media/AZenv-WinAzureAvailSetsHA.png)
  
I dette diagram beskrives konfigurationen af tilgængelighedssæt inden for Azure-infrastrukturen. Hver af følgende roller deler et separat tilgængelighedssæt:
  
- Active Directory og DNS
    
- Database
    
- Back End
    
- Distribuer cache
    
- Front end
    
Din SharePoint farm skal muligvis finjusteres i Azure-platformen. For at sikre høj tilgængelighed af alle komponenter skal du sikre, at serverrollerne alle er konfigureret identisk.
  
Her er et eksempel, der viser en standardarkitektur for internetwebsteder, der opfylder specifikke kapacitet- og ydeevnemål. Dette eksempel er udvalgt i følgende arkitekturmodel: [Internet sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Figur 6: Planlægningseksemp på kapacitet og mål for ydeevne i en farm på tre niveauer**

![Standard SharePoint 2013-webstedsarkitektur med komponentallokering, der opfylder specifikke kapacitet- og ydeevnemål.](../media/AZarch-CapPerfexmpArch.png)
  
I dette diagram:
  
- En farm på tre niveauer er repræsenteret: webservere, programservere og databaseservere.
    
- De tre webservere er konfigureret identisk med flere komponenter.
    
- De to databaseservere er konfigureret identisk.
    
- De tre programservere er ikke konfigureret identisk. Disse serverroller kræver finjustering for tilgængelighedssæt i Azure.
    
Lad os se nærmere på programserverniveauet.
  
**Figur 7: Programserverniveau før finjustering**

![Eksempel SharePoint Server 2013-programserverniveau før justering for Microsoft Azure tilgængelighedssæt.](../media/AZarch-AppServtierBefore.png)
  
I dette diagram:
  
- Tre servere er inkluderet i programniveauet.
    
- Den første server indeholder fire komponenter.
    
- Den anden server indeholder tre komponenter.
    
- Den tredje server indeholder to komponenter.
    
Du bestemmer antallet af komponenter ud fra ydeevnen og kapacitetsmålene for farmen. For at tilpasse denne arkitektur til Azure replikerer vi de fire komponenter på tværs af alle tre servere. Dette øger antallet af komponenter ud over, hvad der er nødvendigt for ydeevne og kapacitet. Kompromisen er, at dette design sikrer høj tilgængelighed af alle fire komponenter på Azure-platformen, når disse tre virtuelle maskiner tildeles til et tilgængelighedssæt.
  
**Figur 8: Programserverniveau efter finjustering**

![Eksempel SharePoint Server 2013-programserverniveau efter justering af Microsoft Azure for tilgængelighedssæt.](../media/AZarch-AppServtierAfter.png)
  
Dette diagram viser alle tre programservere, der er konfigureret identisk med de samme fire komponenter.
  
Når vi føjer tilgængelighedssæt til niveauerne i SharePoint, er implementeringen fuldført.
  
**Figur 9: Den SharePoint farm i Azure-infrastrukturtjenester**

![Eksempel SharePoint 2013-farm i Azure-infrastrukturtjenester med virtuelle netværk, forbindelse på tværs af det lokale miljø, undernet, VM'er og tilgængelighedssæt.](../media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Dette diagram viser den SharePoint farm, der er implementeret i Azure-infrastrukturtjenester, med tilgængelighedssæt til at levere fejldomæner til serverne på hvert niveau.
  
## <a name="see-also"></a>Se også

[Microsoft 365 og arkitekturcenter](../solutions/index.yml)
  
[Internetwebsteder i Microsoft Azure bruger SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[SharePoint af genoprettelse efter nedbrud på server 2013 Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)