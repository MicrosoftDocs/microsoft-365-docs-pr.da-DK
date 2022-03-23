---
title: Arkitektoniske modeller til SharePoint, Exchange, Skype for Business og Lync
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Hent it-plakater, der beskriver arkitektoniske modeller, installationer og platformsmuligheder for SharePoint, Exchange, Skype for Business og Lync.
ms.openlocfilehash: 813a143d281f85e6cbc9c0456dceaf20c674d13b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590583"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>Arkitektoniske modeller til SharePoint, Exchange, Skype for Business og Lync

It-plakaterne i denne artikel beskriver de arkitektoniske modeller og installationsindstillinger for SharePoint, Exchange, Skype for Business og Lync. De indeholder også designoplysninger til installation SharePoint i Microsoft Azure.
  
Ved Microsoft 365 du levere velkendte samarbejds- og kommunikationstjenester via skyen. Med nogle få undtagelser forbliver brugeroplevelsen uændret, uanset om du vedligeholder en lokal installation eller bruger Microsoft 365. 

Denne samlede brugeroplevelse komplicerer beslutningen om, hvor du vil placere hver arbejdsbelastning. Den stiller også spørgsmål:
  
- Hvordan vælger du en platform til individuelle arbejdsbelastninger?
    
- Giver det mening at bevare en hvilken som helst tjeneste lokalt?
    
- I hvilket scenarie er en hybridinstallation relevant?
    
- Hvordan passer Azure ind i billedet?
    
- Hvilke konfigurationer af Office serverbelastninger understøtter Azure?
    
> [!TIP]
> De fleste plakater i denne artikel er tilgængelige på flere sprog. Tilgængelige sprog omfatter kinesisk, engelsk, fransk, tysk, italiensk, japansk, koreansk, portugisisk, russisk og spansk. Hvis du vil downloade en plakat på et af disse sprog, skal du vælge Flere sprog under **plakatminiaturebilledet**.
  
Fortæl os, hvad du synes! Send os en mail [på cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
Brug følgende links til at få de plakater, du skal bruge:
  
- **Arkitektoniske modeller**: Brug disse ressourcer til at bestemme din ideelle platform og konfiguration til SharePoint 2016 Skype for Business 2015.
    
  - [Arkitektoniske modeller SharePoint Microsoft 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint Server 2016-databaser](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [Arkitektoniske modeller Skype for Business Microsoft Skype for Business 2015](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **Platform**: Brug disse ressourcer til at bestemme din ideelle platform og konfiguration til SharePoint 2013, Exchange 2013 og Lync 2013.
    
  - [SharePoint 2013-platformsmuligheder](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange 2013-platformsmuligheder](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [Lync 2013-platformsmuligheder](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 i Azure**: Brug disse it-plakater til at designe og konfigurere SharePoint Server 2013-arbejdsbelastninger i Azure-infrastrukturtjenester.
    
  - [Websteder på internettet i Azure med SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [Designeksempel: Internetwebsteder i Azure til SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint genoprettelse efter nedbrud i Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>Plakater med arkitektoniske modeller

It-plakaterne til SharePoint 2016 og Skype for Business 2015 er en måde at sammenligne installationsmetoder på i et letudskrevet format. Plakaterne viser alle konfigurations- eller platformsmuligheder. De indeholder følgende oplysninger for hver indstilling:
  
- **Oversigt**: En kort oversigt over platformen, herunder et begrebsmæssigt diagram.
    
- **Velegnet til**: Almindelige scenarier, der er ideelt egnet til platformen.
    
- **Licenskrav**: De licenser, du skal bruge til udrulning.
    
- **Arkitekturopgaver**: De beslutninger, du skal træffe som arkitekt.
    
- **It-medarbejderes opgaver eller ansvarsområder**: De daglige ansvarsområder, som it-medarbejderne skal planlægge for.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>Microsoft SharePoint Server 2016 arkitektoniske modeller

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede med SharePoint 2016 Architectural Models.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=52650)    |Denne IT-plakat beskriver SharePoint Online, Azure og SharePoint lokale konfigurationer, som forretnings beslutningstagere og løsningsarkitekter skal kende til. <br/><br/> - **SharePoint Online (SaaS)**: SharePoint forbrug via en SaaS-abonnementsmodel (software as a service). <br/> - **SharePoint hybrid**: Flyt dine SharePoint websteder og apps til skyen i dit eget tempo. <br/> - **SharePoint Azure (IaaS)**: Udvid dit lokale miljø til Azure, og udrul SharePoint 2016-servere der. (Denne model anbefales til miljøer med høj tilgængelighed eller genoprettelse efter nedbrud og udviklings-/testmiljøer). <br/> - **SharePoint lokalt** miljø: Planlægge, installere, vedligeholde og tilpasse dit SharePoint i et datacenter, som du vedligeholder.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint Server 2016-databaser

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af SharePoint Server 2016-databaser.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=55041)    |Denne it-plakat er en hurtig reference til SharePoint Server 2016-databaser. Du får vist detaljer for hver database: <br/><br/> - Størrelse <br/> - Skaleringsvejledning <br/> - I/O-mønstre <br/> - Krav <br/><br/>  Den første side viser de SharePoint og de tjenesteprogrammer, der har flere databaser. Den anden side viser alle de tjenesteprogrammer, der har enkelte databaser. <br/><br/>  Du kan finde flere oplysninger [i Databasetyper og -beskrivelser SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>Arkitektoniske Microsoft Skype for Business 2015-modeller

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede med plakaten Skype for Business arkitektoniske modeller.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=55022)    |Denne plakat beskriver Skype for Business Online, lokal, hybrid og privat grensudveksling i skyen (PBX). Den beskriver også integration med Exchange og SharePoint konfigurationer, som forretnings beslutningstagere og løsningsarkitekter skal kende til. <br/><br/> Plakaten er beregnet til it-fagfolk til at skabe opmærksomhed om de grundlæggende arkitektoniske modeller, som Skype for Business online og Skype for Business i det lokale miljø kan anvendes. <br/><br/>Start med den konfiguration, der passer bedst til organisationens behov og planer. Overvej og brug andre konfigurationer efter behov. Du kan f.eks. overveje integration med Exchange og SharePoint eller en løsning, der udnytter Microsoft Cloud PBX-tilbuddet.|
   
## <a name="platform-options-posters"></a>Plakater med platformsmuligheder

It-plakaterne til SharePoint 2013, Exchange 2013 og Lync 2013 udgør en måde at sammenligne installationsmetoderne med et hurtigt øjekast. Hver plakat viser alle konfigurationer eller platformsmuligheder. Den indeholder følgende oplysninger for hver indstilling:
  
- **Oversigt**: En kort oversigt over platformen, herunder et begrebsmæssigt diagram.
    
- **Velegnet til**: Almindelige scenarier, der er ideelt egnet til platformen.
    
- **Licenskrav**: De licenser, du skal bruge til udrulning.
    
- **Arkitekturopgaver**: De beslutninger, du skal træffe som arkitekt.
    
- **It-medarbejderes opgaver eller ansvarsområder**: De daglige ansvarsområder, som it-medarbejderne skal planlægge for.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint 2013-platformsmuligheder

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af den SharePoint 2013 Platform Options poster.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=40332)    |For beslutningstagere og arkitekter viser denne plakat platformsmulighederne for SharePoint 2013, SharePoint i Microsoft 365, lokal hybridinstallation med Microsoft 365, Azure og installationer, der kun er i det lokale miljø. Den indeholder en oversigt over hver arkitektur, anbefalinger, licenskrav og lister over arkitekt- og it-professionelle opgaver for hver platform. Plakaten fremhæver flere SharePoint løsninger på Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange 2013-platformsmuligheder

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af plakaten Exchange med platformsindstillinger.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=42676)    |For forretnings beslutningstagere og arkitekter beskriver denne plakat platformsmulighederne for Exchange 2013. Kunder kan vælge mellem Exchange Online med Microsoft 365, Exchange, Exchange Server lokale miljø og værtsbaserede Exchange. Plakaten beskriver hver arkitektonisk mulighed, herunder de ideelle scenarier for hver, licenskrav og IT-ansvarsområder.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>Platformsmuligheder for Lync 2013

|Element|Beskrivelse|
|---|---|
|[![Miniaturebillede af plakaten med indstillinger for Lync 2013-platformen.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41677)    |For forretnings beslutningstagere og arkitekter beskriver denne plakat platformsmulighederne for Lync 2013. Kunder kan vælge mellem Lync Online med Microsoft 365, hybrid Lync, Lync Server i det lokale miljø og hostet Lync. IT-plakaten beskriver hver arkitektonisk mulighed, herunder de ideelle scenarier for hver, licenskrav og IT-professionelle ansvarsområder.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint i Azure-løsningsplakater

It-plakaterne til SharePoint Azure viser Azure-baserede løsninger, der bruger SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>Internetwebsteder i Microsoft Azure bruge SharePoint Server 2013

|Element|Beskrivelse|
|---|---|
|[![Billede af internetwebstederne i Azure ved hjælp SharePoint Server 2013-plakaten.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41992)    |Denne plakat skitserer vigtige designaktiviteter og anbefalede arkitektur for internetbaserede websteder i Azure.  <br/><br/> Du kan finde flere oplysninger i følgende artikler:  <br/><br/> - [Websteder på internettet i Azure med SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Azure-arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>Websteder på internettet i Azure til SharePoint 2013

|Element|Beskrivelse|
|---|---|
|[![Billede af internetwebstederne i Microsoft Azure til SharePoint Server 2013-plakat.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41991)    |Brug dette designeksempel som et udgangspunkt for din egen arkitektur af et internetsted i Azure, der bruger SharePoint Server 2013. <br/><br/> Du kan finde flere oplysninger i følgende artikler:  <br/><br/> - [Websteder på internettet i Azure med SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [Azure-arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint genoprettelse efter nedbrud til Microsoft Azure

|Element|Beskrivelse|
|---|---|
|[![Billede af plakaten for SharePoint genoprettelse efter nedbrud i Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [flere sprog](https://www.microsoft.com/download/details.aspx?id=41993)    |Denne it-plakat viser arkitektur principper for et miljø til genoprettelse efter nedbrud i Azure. <br/><br/> Du kan finde flere oplysninger i følgende artikler:  <br/><br/> - [SharePoint genoprettelse efter nedbrud på Server 2013 i Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [Azure-arkitekturer til SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>Se også

- [Microsoft 365 og arkitekturcenter](../solutions/index.yml)
  
- [Microsoft-skyarkitekturmodeller](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 testlaboratorievejledninger](m365-enterprise-test-lab-guides.md)
  
- [Hybridløsninger](hybrid-solutions.md)