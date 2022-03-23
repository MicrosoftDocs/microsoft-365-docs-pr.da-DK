---
title: Project oversigt over ophør af support til Server 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: Den 10. oktober 2017 ophørte support for Project Server 2007, Project Portfolio Server Project 2007. Brug denne artikel til at planlægge din opgradering nu.
ms.openlocfilehash: c492c7154006a139589cff1c768dd77c13804c07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589774"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project oversigt over ophør af support til Server 2007

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Support til Office 2007-servere og -programmer ophørte i 2017, og du er nødt til at planlægge overførslen. Hvis du i øjeblikket bruger Project Server 2007 og relaterede produkter, skal du bemærke følgende datoer for ophør af support:
  
|**Produkt**|**Slutdato for support**|
|:-----|:-----|
|Project Server 2007  <br/> |10. oktober 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10. oktober 2017  <br/> |
|Project 2007 Standard  <br/> |10. oktober 2017  <br/> |
|Project 2007 Professional  <br/> |10. oktober 2017  <br/> |
   
Du kan finde flere oplysninger Office 2007-servere, der går på pension, under [Opgrader fra Office 2007-servere og klientprodukter](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsopdateringer osv. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Da Project da Supporten til Server 2007 blev 10. oktober 2017, yder Microsoft ikke længere:
  
- Teknisk support til problemer, der kan opstå.
    
- Fejlrettelser af problemer, der kan påvirke stabiliteten og anvendeligheden af serveren.
    
- Sikkerhedsopdateringer til sårbarheder, der kan gøre serveren sårbar over for sikkerhedsbrister.
    
- Tidszoneopdateringer.
    
Din installation af Project Server 2007 fortsætter med at køre efter denne dato. Men på grund af de ændringer, der er angivet tidligere, anbefaler vi på det kraftigste, at du overfører fra Project Server 2007 så hurtigt som praktisk muligt.
  
## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Hvis du bruger en Project Server 2007, skal du udforske dine overførselsmuligheder, som er:
  
- Overfør til Project Online
    
- Overfør til en nyere lokal version af Project server (helst Project Server 2016)
    
|**Hvorfor skulle jeg foretrække at overføre Project Online**|**Hvorfor skulle jeg foretrække at overføre til Project Server 2016**|
|:-----|:-----|
| Jeg har mobilbrugere.  <br/> <br/>Omkostninger til overførsel er et væsentligt problem (hardware, software, timer og bestræbelser på at implementere). <br/><br/>  Efter overførslen er omkostninger til vedligeholdelse af mit miljø et vigtigt problem (f.eks. automatiske opdateringer, garanteret oppetid og så videre).  <br/> | Forretningsregler begrænser mig i at køre min virksomhed i skyen.<br/><br/>  Jeg har brug for kontrol over opdateringer af mit miljø.  |
   
> [!NOTE]
> Du kan finde flere oplysninger om muligheder for at flytte fra dine Office 2007-servere under Ressourcer, der kan hjælpe dig med [at opgradere fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md). Bemærk, Project Server ikke understøtter en hybridkonfiguration, fordi Project Server og Project Online ikke kan dele den samme ressourcepulje. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Vigtige overvejelser, når du overfører fra Project Server 2007

Overvej følgende, når du planlægger at overføre fra Project Server 2007:
  
- **Få hjælp fra en Microsoft-partner** – Opgradering fra Project Server 2007 kan være udfordrende og kræver meget forberedelse og planlægning. Det kan være særligt udfordrende, hvis du ikke var den person, der konfigurerede Project Server 2007 oprindeligt. Der er heldigvis Microsoft-partnere, der kan hjælpe, uanset om du planlægger at overføre Project Server 2016 eller for at Project Online. Søg efter en Microsoft-partner for at hjælpe med din overførsel [i Microsoft Partnercenter](https://go.microsoft.com/fwlink/p/?linkid=841249). Søg efter ordet *Gold Project portfolio management for* at få vist en liste over alle Microsoft-partnere, der har ekspertise Project. 
    
- **Planlæg dine** tilpasninger – Mange af de tilpasninger, du har foretaget i dit Project Server 2007-miljø, fungerer muligvis ikke, når du overfører til Project Server 2016 eller Project Online. Der er betydelige forskelle i Project serverarkitekturen mellem versioner. De påkrævede operativsystemer, databaseservere og klientwebbrowsere, der understøttes, varierer også. Planlæg, hvordan du tester eller genopbygger dine tilpasninger af det nye miljø. Planlægning er også en god mulighed for at overveje, om hver enkelt tilpasning stadig er nødvendig. Få mere at vide under [Opret en plan for aktuelle tilpasninger under opgradering til SharePoint 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **Tid og tålmodighed –** Planlægning, udførelse og test af opgradering kræver tid og anstrengelser, især hvis du opgraderer til Project Server 2016. Hvis du f.eks. overfører fra Project Server 2007 til Project Server 2016, skal du først overføre til Project Server 2010, kontrollere dine data og derefter gøre det samme, når du overfører til hver efterfølgende version. Det kan være en god ide at kontakte en Microsoft-partner for at få et skøn over, hvor lang tid det vil tage, og hvad det vil koste.
    
## <a name="migrate-to-project-online"></a>Overfør til Project Online

Hvis du vælger at overføre fra Project Server 2007 til Project Online, kan du gøre følgende for manuelt at overføre dine projektplandata:
  
1. Gem dine projektplaner fra Project Server 2003 i .mpp-format.
    
2. I Project Professional 2013, Project Professional 2016 eller Project Online Desktop Client skal du åbne hver .mpp-fil og derefter gemme og publicere den på Project Online.
    
Du kan manuelt oprette din Microsoft Project Web App (PWA) konfiguration i Project Online. Genskab f.eks. eventuelle nødvendige brugerdefinerede felter eller virksomhedskalendere. Microsoft-partnere kan også hjælpe med denne proces.
  
Vigtige ressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Introduktion til Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Sådan konfigurerer og bruger du Project Online <br/> |
|[Project Online tjenestebeskrivelser](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Oplysninger om de forskellige Project Online, der er tilgængelige for dig <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Overfør til en nyere lokal version af Project Server

Vi er stærkt overbeviste om, at du får den bedste værdi og brugeroplevelse ved at Project Online. Men vi forstår også, at nogle organisationer har brug for at bevare projektdata i et lokalt miljø. Hvis du vælger at bevare dine projektdata i det lokale miljø, kan du overføre dit Project Server 2007-miljø til Project Server 2010, Project Server 2013 eller Project Server 2016.
  
Hvis du ikke kan overføre til Project Online, anbefaler vi, at du overfører til Project Server 2016. Project Server 2016 indeholder alle funktionerne fra tidligere versioner af Project Server. Den passer bedst til den oplevelse, der er tilgængelig Project Online, selvom visse funktioner kun er tilgængelige i Project Online.
  
Efter hver overførsel skal du kontrollere, at dine data er overført.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Hvordan overfører jeg til Project Server 2016?

Arkitektoniske forskelle mellem Project Server 2007 og Project Server 2016 forhindrer en direkte overførselssti. Så du skal overføre dine Project Server 2007-data til hver efterfølgende version af Project Server, indtil du når Project Server 2016.
  
Følg disse trin for at Project Server 2016:
  
1. Overfør fra Project Server 2007 til Project Server 2010.
    
2. Overfør fra Project Serve 2010 til Project Server 2013.
    
3. Overfør fra Project Server 2013 til Project Server 2016.
    
Efter hver overførsel skal du sørge for, at dine data er overført.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Trin 1: Overfør fra Project Server 2007 til Project Server 2010

Hvis du vil have en detaljeret beskrivelse af, hvad du skal gøre for at opgradere fra Project Server 2007 til Project Server 2010, skal du se Opgrader til [Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Vigtige ressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Project oversigt over opgradering til Server 2010](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |En højniveauvisning af, hvad du skal gøre for at opgradere fra Project Server 2007 Project Server 2010 <br/> |
|[Planlæg at opgradere til Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2007 Project Server 2010, herunder systemkrav  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Hvordan opgraderer jeg?

Du kan få mere at [vide under Opgradere Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)). Men det er vigtigt at forstå, at der er to forskellige metoder, du kan bruge til at opgradere:
  
- **Opgradering af databasehæftning:** Denne metode opgraderer kun indholdet af dit miljø, ikke konfigurationsindstillingerne. Det er påkrævet, hvis du opgraderer fra Office Project Server 2007, der er installeret på hardware, der kun understøtter et serveroperativsystemer på 32-bit. Der findes to typer opgraderingsmetoder til databasehæftning:
    
  - Fuld opgradering af databasehæftninger – Overfører de projektdata, der er gemt i Office Project Server 2007-databaser, samt webstedsdata fra Microsoft Project Web App, der er gemt i en **SharePoint-indholdsdatabase**.
    
  - ***Kerneopgradering af databasehæftninger*** – Overfører kun de projektdata, der er gemt i Project Server-databaser.
    
- **Opgradering på stedet**: Konfigurationsdataene for farmen og alt indhold på farmen opgraderes på den eksisterende hardware i en fast rækkefølge. Når du starter opgraderingsprocessen, tager konfiguration hele farmen offline. De websteder og Microsoft Project Web App-websteder er ikke tilgængelige, før opgraderingen er færdig, og konfigurationen genstarter derefter serveren. Når du starter en direkte opgradering, kan du ikke afbryde opgraderingen eller vende tilbage til den tidligere version. Det er bedst at lave et spejlbillede af produktionsmiljøet og foretage opgraderingen i dette miljø, ikke i produktionsmiljøet. 
    
Flere ressourcer:
  
- [SuperFlow til Microsoft Project Server 2010-opgradering](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Overførsel fra Project Server 2007 til Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Overvejelser i forbindelse med opgradering Project Web App webdele](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project SDK (Software Development Kit)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>Trin 2: Overfør Project Server 2013

Når du har bekræftet, at dine data er overført, er næste trin at overføre Project Server 2013.
  
Hvis du vil have en detaljeret beskrivelse af, hvad du skal gøre for at opgradere fra Project Server 2010 til Project Server 2013, skal du se Opgrader [til Project Server 2013](/project/upgrade-to-project-server-2016). 
  
Vigtige ressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Oversigt over Project Server 2013-opgraderingsprocessen](/project/upgrade-to-project-server-2016) <br/> |Oversigt over, hvad du skal gøre for at opgradere fra Project Server 2010 Project Server 2013  <br/> |
|[Planlæg at opgradere til Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |Overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2010 til Project Server 2013, herunder systemkrav <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Værd at vide om opgradering til denne version

[Nyheder i Project Server 2013-opgraderingen](/project/what-s-new-in-project-server-2013-upgrade) beskriver vigtige ændringer i forbindelse med opgradering til denne version. De vigtigste er: 
  
- Der findes ingen direkte opgradering til Project Server 2013. Metoden til databasehæfte er den eneste understøttede metode til opgradering fra Project Server 2010 Project Server 2013.
    
- Opgraderingsprocessen konverterer ikke kun dine Project Server 2010-data til Project Server 2013-format, men konsoliderer også de fire Project Server 2010-databaser til en enkelt Project Web App-database.
    
- I 2013-versionerne blev både SharePoint Server Project Server ændret til kravbaseret godkendelse. Hvis du bruger klassisk godkendelse, skal du overveje denne faktor for din opgradering. Få mere at vide under Overfør fra klassisk tilstand til kravbaseret [godkendelse i SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
Flere ressourcer:
  
- [Oversigt over opgraderingsprocessen til Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Opgradere dine databaser og Project grupper af Websteder i Web App (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Microsoft Project diagram over opgraderingsprocessen for server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Den fantastiske databasekonsolidering, Project Server 2010 til 2013-overførsel i 8 nemme trin](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Trin 3: Overfør til Project Server 2016

Når du har bekræftet, at dine data er overført, er næste trin at overføre Project Server 2016.
  
Du kan finde en detaljeret beskrivelse af, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016, under Opgrader [til Project Server 2016](//project/upgrading-to-project-server-2016).
  
Vigtige ressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Oversigt over Project Server 2016 opgraderingsprocessen](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Oversigt over, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016 <br/> |
|[Planlæg opgradering til Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |Overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2013 til Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Værd at vide om opgradering til denne version

[Ting, du bør vide om Project Server 2016, fortæller](/project/plan-for-upgrade-to-project-server-2016) dig nogle vigtige ændringer i forbindelse med opgradering til denne version, som omfatter:
  
- Når du opretter dit Project Server 2016-miljø, som du vil overføre dine Project Server 2013-data til, inkluderes Project Server 2016-installationsfilerne i SharePoint Server 2016. Du kan finde flere oplysninger [i Project Server 2016](/project/deploy-project-server-2016).
    
- Ressourceplaner frarådes i Project Server 2016. Dine Project Server 2013-ressourceplaner overføres til Ressourceengagementer i Project Server 2016 og Project Online. Se [Oversigt: Ressourceengagementer](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) for at få flere oplysninger. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Overfør fra Portfolio Server 2007

Project Portfolio Server 2007 blev brugt sammen med Project Server 2007 til oversigtsstrategi, -prioritering og -optimering. Der blev ikke oprettet Project af Portfolio Server efter denne version. Funktioner til oversigtsadministration er dog tilgængelige i Project Server 2016 og Premium versionen af Project Online. Men data Project Portfolio Server 2007 kan ikke overføres til nogen af dem. Data som f.eks. forretningsfaktorer skal genskabes.
  
Andre ressourcer:
  
- [Project Online tjenestebeskrivelser: Se](/office365/servicedescriptions/project-online-service-description/project-online-service-description) de funktioner til oversigtsadministration, der er inkluderet Project Server 2016 og Project Online Premium.
    
- [Microsoft Office Project Portfolio Server 2007-overførselsvejledning.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Relaterede emner

[SharePoint oversigt over ophør af support til Server 2007](sharepoint-2007-end-of-support.md)
  
[Ressourcer, der kan hjælpe dig med at opgradere Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
