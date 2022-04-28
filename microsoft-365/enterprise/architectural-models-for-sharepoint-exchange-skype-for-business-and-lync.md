---
title: Arkitektoniske modeller til SharePoint, Exchange, Skype for Business og Lync
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: Hent it-plakater, der beskriver de arkitektoniske modeller, udrulningen og platformindstillingerne for SharePoint, Exchange, Skype for Business og Lync.
ms.openlocfilehash: 859d952fc9a2e4e9315c7fef3e56b4e59d0f60d6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096870"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Arkitektoniske modeller til SharePoint, Exchange, Skype for Business og Lync

I it-plakaterne i denne artikel beskrives de arkitektoniske modeller og udrulningsmuligheder for SharePoint, Exchange, Skype for Business og Lync. De indeholder også designoplysninger til installation af SharePoint i Microsoft Azure.
  
Ved hjælp af Microsoft 365 kan du levere velkendte samarbejds- og kommunikationstjenester via cloudmiljøet. Med nogle få undtagelser forbliver brugeroplevelsen den samme, uanset om du vedligeholder en udrulning i det lokale miljø eller bruger Microsoft 365. 

Denne samlede brugeroplevelse komplicerer beslutningen om, hvor hver enkelt arbejdsbelastning skal placeres. Den rejser også spørgsmål:
  
- Hvordan vælger du en platform til individuelle arbejdsbelastninger?
    
- Giver det mening at bevare en tjeneste i det lokale miljø?
    
- I hvilket scenarie er en hybridinstallation passende?
    
- Hvordan passer Azure ind i billedet?
    
- Hvilke konfigurationer af Office serverarbejdsbelastninger understøtter Azure?
    
> [!TIP]
> De fleste plakater i denne artikel er tilgængelige på flere sprog. Tilgængelige sprog omfatter kinesisk, engelsk, fransk, tysk, italiensk, japansk, koreansk, portugisisk, russisk og spansk. Hvis du vil downloade en plakat på et af disse sprog, skal du vælge **Flere sprog** under miniaturebilledet af plakaten.
  
Fortæl os, hvad du synes! Send os en mail på [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Brug følgende links til at få de plakater, du har brug for:
  
- **Arkitektoniske modeller**: Brug disse ressourcer til at bestemme din ideelle platform og konfiguration for SharePoint 2016 og Skype for Business 2015.
    
  - [Microsoft SharePoint 2016-arkitektoniske modeller](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Server 2016-databaser](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Microsoft Skype for Business 2015-arkitektoniske modeller](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Platform**: Brug disse ressourcer til at bestemme din ideelle platform og konfiguration til SharePoint 2013, Exchange 2013 og Lync 2013.
    
  - [SharePoint platformsmuligheder i 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange platformsmuligheder i 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Indstillinger for Lync 2013-platform](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 i Azure**: Brug disse it-plakater til at designe og konfigurere SharePoint Server 2013-arbejdsbelastninger i Azure-infrastrukturtjenester.
    
  - [Internetsider i Azure ved hjælp af SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Designeksempel: Internetwebsteder i Azure til SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint it-katastrofeberedskab til Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Plakater med arkitektoniske modeller

It-plakaterne til SharePoint 2016 og Skype for Business 2015 gør det nemt at sammenligne udrulningsmetoder i et format, der er let at udskrive. Plakaterne indeholder en liste over alle konfigurationer eller platformsindstillinger. De indeholder følgende oplysninger for hver indstilling:
  
- **Oversigt**: En kort oversigt over platformen, herunder et konceptuelt diagram.
    
- **Bedst til**: Almindelige scenarier, der er ideelt egnet til platformen.
    
- **Licenskrav**: De licenser, du skal bruge til installation.
    
- **Arkitekturopgaver**: De beslutninger, du skal træffe som arkitekt.
    
- **It-opgaver eller -ansvarsområder**: Det daglige ansvar, som it-medarbejderne skal planlægge.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Microsoft SharePoint Server 2016 Arkitektoniske modeller

|Element|Beskrivelse|
|---|---|
|[![Miniature af plakaten SharePoint Server 2016 Architectural Models.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=52650)    |I denne it-plakat beskrives SharePoint Online, Azure og SharePoint konfigurationer i det lokale miljø, som beslutningstagere og løsningsarkitekter skal kende til. <br/><br/> - **SharePoint Online (SaaS):** Forbrug SharePoint via en SaaS-abonnementsmodel (Software as a Service). <br/> - **SharePoint hybrid**: Flyt dine SharePoint websteder og apps til clouden i dit eget tempo. <br/> - **SharePoint i Azure (IaaS):** Udvid dit lokale miljø til Azure, og udrul SharePoint 2016-servere der. Denne model anbefales til miljøer med høj tilgængelighed eller it-katastrofeberedskab og udviklings-/testmiljøer. <br/> - **SharePoint i det lokale miljø**: Planlæg, udrul, vedligehold og tilpas dit SharePoint miljø i et datacenter, som du vedligeholder.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016-databaser

|Element|Beskrivelse|
|---|---|
|[![Miniature af plakaten SharePoint Server 2016-databaser.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=55041)    |Denne it-plakat er en hurtig reference til SharePoint Server 2016-databaser. Du får vist oplysninger om hver database: <br/><br/> - Størrelse <br/> – Skaleringsvejledning <br/> - I/O-mønstre <br/> - Krav <br/><br/>  På den første side vises de SharePoint systemdatabaser og tjenesteprogrammer, der har flere databaser. På den anden side vises alle de tjenesteprogrammer, der har enkelte databaser. <br/><br/>  Du kan få flere oplysninger [under Databasetyper og -beskrivelser i SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Microsoft Skype for Business 2015 Architectural Models

|Element|Beskrivelse|
|---|---|
|[![Miniature af plakaten Skype for Business arkitektoniske modeller.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=55022)    |I denne plakat beskrives Skype for Business Online, i det lokale miljø, PBX (Hybrid og Cloud Private Branch Exchange). Den beskriver også integration med Exchange og SharePoint konfigurationer, som beslutningstagere og løsningsarkitekter skal kende til. <br/><br/> Plakaten er beregnet til it-fagfolk til at øge kendskabet til de grundlæggende arkitektoniske modeller, gennem hvilke Skype for Business Online og Skype for Business i det lokale miljø kan forbruges. <br/><br/>Start med den konfiguration, der passer bedst til organisationens behov og planer. Overvej og brug andre konfigurationer efter behov. Det kan f.eks. være, at du vil overveje integration med Exchange og SharePoint eller en løsning, der udnytter Microsofts cloud-PBX-tilbud.|
   
## <a name="platform-options-posters"></a>Plakater med platformindstillinger

It-plakaterne til SharePoint 2013, Exchange 2013 og Lync 2013 gør det nemt at sammenligne udrulningsmetoderne på et øjeblik. Hver plakat viser alle konfigurationer eller platformindstillinger. Den indeholder følgende oplysninger for hver indstilling:
  
- **Oversigt**: En kort oversigt over platformen, herunder et konceptuelt diagram.
    
- **Bedst til**: Almindelige scenarier, der er ideelt egnet til platformen.
    
- **Licenskrav**: De licenser, du skal bruge til installation.
    
- **Arkitekturopgaver**: De beslutninger, du skal træffe som arkitekt.
    
- **It-opgaver eller -ansvarsområder**: Det daglige ansvar, som it-medarbejderne skal planlægge.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013 Platformindstillinger

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af plakaten SharePoint 2013 Platformindstillinger.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=40332)    |For beslutningstagere og arkitekter i virksomheden viser denne plakat platformsmulighederne for SharePoint 2013, SharePoint i Microsoft 365, hybrid i det lokale miljø med Microsoft 365, Azure og udrulninger, der kun er i det lokale miljø. Den indeholder en oversigt over hver arkitektur, anbefalinger, licenskrav og lister over arkitekt- og it-pro-opgaver for hver platform. Plakaten fremhæver flere SharePoint løsninger på Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013 Platformindstillinger

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af plakaten Exchange Platformindstillinger.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=42676)    |For beslutningstagere og arkitekter beskriver denne plakat platformsmulighederne for Exchange 2013. Kunderne kan vælge mellem Exchange Online med Microsoft 365, hybride Exchange, Exchange Server i det lokale miljø og hostede Exchange. Plakaten beskriver hver arkitektoniske mulighed, herunder de ideelle scenarier for hver enkelt, licenskravene og it-ansvarsområderne.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Indstillinger for Lync 2013-platform

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af plakaten Med indstillinger for Lync 2013-platform.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41677)    |Denne plakat beskriver platformmulighederne for Lync 2013 for beslutningstagere og arkitekter i virksomheden. Kunderne kan vælge mellem Lync Online med Microsoft 365, hybrid Lync, Lync Server i det lokale miljø og hostet Lync. It-plakaten beskriver hver arkitektoniske mulighed, herunder de ideelle scenarier for hver enkelt, licenskravene og it-ansvarsområderne.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint på plakater med Azure-løsninger

It-plakaterne til SharePoint i Azure viser Azure-baserede løsninger, der bruger SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Internet Sites in Microsoft Azure Using SharePoint Server 2013

|Element|Beskrivelse|
|---|---|
|[![Billede af internetwebstederne i Azure ved hjælp af plakaten SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41992)    |Denne plakat beskriver vigtige designaktiviteter og anbefalet arkitektur for websteder på internettet i Azure.  <br/><br/> Du kan finde flere oplysninger i følgende artikler:  <br/><br/> - [Internetsider i Azure ved hjælp af SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Azure-arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>Internetsider i Azure til SharePoint 2013

|Element|Beskrivelse|
|---|---|
|[![Billede af internetwebstederne i Microsoft Azure til plakaten SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41991)    |Brug dette designeksempel som udgangspunkt for din egen arkitektur for et websted på internettet i Azure ved hjælp af SharePoint Server 2013. <br/><br/> Du kan finde flere oplysninger i følgende artikler:  <br/><br/> - [Internetsider i Azure ved hjælp af SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Azure-arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint it-katastrofeberedskab til Microsoft Azure

|Element|Beskrivelse|
|---|---|
|[![Billede af plakaten for SharePoint it-katastrofeberedskab til Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41993)    |Denne it-plakat viser arkitekturprincipper for et it-katastrofeberedskabsmiljø i Azure. <br/><br/> Du kan finde flere oplysninger i følgende artikler:  <br/><br/> - [SharePoint Server 2013-it-katastrofeberedskab i Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Azure-arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Se også

- [Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)
  
- [Microsoft-skyarkitekturmodeller](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)
  
- [Hybridløsninger](hybrid-solutions.md)