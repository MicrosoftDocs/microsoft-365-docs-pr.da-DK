---
title: Køreplan for ophør af support til Project Server 2007
ms.author: deniseb
author: denisebmsft
manager: dansimp
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
description: Den 10. oktober 2017 ophører supporten til Project Server 2007, Project Portfolio Server og Project 2007. Brug denne artikel til at planlægge opgraderingen nu.
ms.openlocfilehash: c072daf811ec8e175c830aaa95b2163c80fa2b6f
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487310"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Køreplan for ophør af support til Project Server 2007

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Support til Office 2007-servere og -programmer ophørte i 2017, og du skal overveje planer for migrering. Hvis du i øjeblikket bruger Project Server 2007 og relaterede produkter, skal du bemærke følgende slutdatoer for support:
  
|**Produkt**|**Slutdato for support**|
|:-----|:-----|
|Project Server 2007  <br/> |10. oktober 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10. oktober 2017  <br/> |
|Project 2007 Standard  <br/> |10. oktober 2017  <br/> |
|Project 2007 Professional  <br/> |10. oktober 2017  <br/> |
   
Du kan finde flere oplysninger om, at Office 2007-servere når ud, under [Opgrader fra Office 2007-servere og klientprodukter](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Hvad betyder *ophør af support* ?

De fleste Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser, sikkerhedsrettelser osv. Denne livscyklus varer typisk 10 år efter produktets første udgivelse. Slutningen af denne livscyklus er kendt som produktets ophør af support. Da support til Project Server 2007 ophørte den 10. oktober 2017, leverer Microsoft ikke længere:
  
- Teknisk support til problemer, der kan opstå.
    
- Fejlrettelser til problemer, der kan påvirke serverens stabilitet og anvendelighed.
    
- Sikkerhedsrettelser til sikkerhedsrisici, der kan gøre serveren sårbar over for brud på sikkerheden.
    
- Tidszoneopdateringer.
    
Installationen af Project Server 2007 vil fortsat køre efter denne dato. Men på grund af de ændringer, der er angivet tidligere, anbefaler vi på det kraftigste, at du overfører fra Project Server 2007, så snart det er praktisk.
  
## <a name="what-are-my-options"></a>Hvad er mine muligheder?

Hvis du bruger Project Server 2007, skal du udforske dine overførselsmuligheder, som er:
  
- Overfør til Project Online
    
- Overfør til en nyere version af Project Server i det lokale miljø (helst Project Server 2016)
    
|**Hvorfor ville jeg foretrække at migrere til Project Online**|**Hvorfor skulle jeg foretrække at migrere til Project Server 2016**|
|:-----|:-----|
| Jeg har mobilbrugere.  <br/> <br/>Omkostninger til migrering er et vigtigt problem (hardware, software, timer og indsats for at implementere). <br/><br/>  Efter migreringen er omkostninger til vedligeholdelse af mit miljø et stort problem (f.eks. automatiske opdateringer, garanteret oppetid osv.).  <br/> | Forretningsregler begrænser mig fra at drive min virksomhed i cloudmiljøet.<br/><br/>  Jeg har brug for kontrol over opdateringer til mit miljø.  |
   
> [!NOTE]
> Du kan finde flere oplysninger om indstillinger for flytning fra dine Office 2007-servere under Ressourcer, der [kan hjælpe dig med at opgradere fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md). Bemærk, at Project Server ikke understøtter en hybridkonfiguration, fordi Project Server og Project Online ikke kan dele den samme ressourcepulje. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Vigtige overvejelser ved overførsel fra Project Server 2007

Overvej følgende, når du planlægger at overføre fra Project Server 2007:
  
- Det kan være en udfordring at **få hjælp fra en Microsoft-partner** – Opgradering fra Project Server 2007 kan være udfordrende og kræver megen forberedelse og planlægning. Det kan være særligt udfordrende, hvis du ikke var den person, der konfigurerede Project Server 2007 oprindeligt. Heldigvis er der Microsoft-partnere, der kan hjælpe, uanset om du planlægger at migrere til Project Server 2016 eller til Project Online. Søg efter en Microsoft-partner for at få hjælp til din migrering i [Microsoft Partnercenter](https://go.microsoft.com/fwlink/p/?linkid=841249). Søg efter begrebet  *Guldprojekt og Porteføljestyring* for at få vist en liste over alle Microsoft-partnere, der har ekspertise inden for Project. 
    
- **Planlæg dine tilpasninger** – Mange af de tilpasninger, du har foretaget i dit Project Server 2007-miljø, fungerer muligvis ikke, når du migrerer til Project Server 2016 eller Project Online. Der er betydelige forskelle i Project Server-arkitekturen mellem versioner. De påkrævede operativsystemer, databaseservere og klientwebbrowsere, der understøttes, er også forskellige. Planlæg, hvordan du tester eller genopbygger dine tilpasninger til det nye miljø. Planlægning giver også en god mulighed for at overveje, om hver tilpasning stadig er nødvendig. Du kan finde flere oplysninger under [Opret en plan for aktuelle tilpasninger under opgraderingen til SharePoint 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **Tid og tålmodighed** – Opgraderingsplanlægning, udførelse og test tager tid og kræfter, især hvis du opgraderer til Project Server 2016. Hvis du f.eks. overfører fra Project Server 2007 til Project Server 2016, skal du først overføre til Project Server 2010, kontrollere dine data og derefter gøre det samme, når du overfører til hver efterfølgende version. Det kan være en god idé at kontakte en Microsoft-partner for at få et skøn over, hvor lang tid det vil tage, og hvad det vil koste.
    
## <a name="migrate-to-project-online"></a>Overfør til Project Online

Hvis du vælger at overføre fra Project Server 2007 til Project Online, kan du gøre følgende for at overføre dine projektplandata manuelt:
  
1. Gem dine projektplaner fra Project Server 2003 i .mpp-format.
    
2. I Project Professional 2013 skal du Project Professional 2016 eller Project Online Desktop Client åbne hver .mpp-fil og derefter gemme og publicere den til Project Online.
    
Du kan oprette din PWA-konfiguration (Microsoft Project Web App) manuelt i Project Online. Du kan f.eks. genskabe de nødvendige brugerdefinerede felter eller virksomhedskalendere. Microsoft-partnere kan også hjælpe med denne proces.
  
Nøgleressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Kom i gang med Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Sådan konfigurerer og bruger du Project Online <br/> |
|[Project Online tjenestebeskrivelser](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Oplysninger om de forskellige Project Online planer, der er tilgængelige for dig <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Overfør til en nyere version af Project Server i det lokale miljø

Vi er overbeviste om, at du får den bedste værdi og brugeroplevelse ved at migrere til Project Online. Men vi forstår også, at nogle organisationer skal opbevare projektdata i et lokalt miljø. Hvis du vælger at beholde dine projektdata i det lokale miljø, kan du overføre Project Server 2007-miljøet til Project Server 2010, Project Server 2013 eller Project Server 2016.
  
Hvis du ikke kan overføre til Project Online, anbefaler vi, at du overfører til Project Server 2016. Project Server 2016 indeholder alle funktionerne i tidligere versioner af Project Server. Den passer bedst til den oplevelse, der er tilgængelig med Project Online, selvom nogle funktioner kun er tilgængelige i Project Online.
  
Efter hver overførsel skal du kontrollere, at dine data er migreret korrekt.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Hvordan gør jeg migrere til Project Server 2016?

Arkitektoniske forskelle mellem Project Server 2007 og Project Server 2016 forhindre en direkte overførselssti. Så du skal overføre dine Project Server 2007-data til hver efterfølgende version af Project Server, indtil du når Project Server 2016.
  
Følg disse trin for at Project Server 2016:
  
1. Overfør fra Project Server 2007 til Project Server 2010.
    
2. Overfør fra Project Serve 2010 til Project Server 2013.
    
3. Overfør fra Project Server 2013 til Project Server 2016.
    
Efter hver overførsel skal du sørge for, at dine data er migreret korrekt.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Trin 1: Overfør fra Project Server 2007 til Project Server 2010

Du kan få en omfattende beskrivelse af, hvad du skal gøre for at opgradere fra Project Server 2007 til Project Server 2010, under [Opgrader til Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Nøgleressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Oversigt over opgradering af Project Server 2010](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |En overordnet visning af, hvad du skal gøre for at opgradere fra Project Server 2007 til Project Server 2010 <br/> |
|[Planlæg opgradering til Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2007 til Project Server 2010, herunder systemkrav  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Hvordan gør jeg opgradering?

Du kan finde flere oplysninger under [Opgrader til Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)). Men det er vigtigt at forstå, at der er to forskellige metoder, du kan bruge til at opgradere:
  
- **Opgradering af database vedhæft:** Denne metode opgraderer kun indholdet til dit miljø og ikke konfigurationsindstillingerne. Det er påkrævet, hvis du opgraderer fra Office Project Server 2007 installeret på hardware, der kun understøtter et 32-bit serveroperativsystem. Der findes to typer opgraderingsmetoder til database vedhæfting:
    
  - **Fuldstændig *opgradering vedhæftning*** af database – overfører de projektdata, der er gemt i Office Project Server 2007-databaser, samt de Microsoft Project Web App-webstedsdata, der er gemt i en SharePoint-indholdsdatabase.
    
  - **Databasetilknyt *kerneopgradering*** – overfører kun de projektdata, der er gemt i Project Server-databaserne.
    
- **Lokal opgradering**: Konfigurationsdataene for farmen og alt indhold på farmen opgraderes på den eksisterende hardware i en fast rækkefølge. Når du starter opgraderingsprocessen, tager installationsprogrammet hele farmen offline. Webstederne og Microsoft Project Web App-webstederne er ikke tilgængelige, før opgraderingen er fuldført, og installationsprogrammet genstarter derefter serveren. Når du har påbegyndt en lokal opgradering, kan du ikke afbryde opgraderingen midlertidigt eller vende tilbage til den tidligere version. Det er bedst at oprette et spejlvendt billede af dit produktionsmiljø og foretage den direkte opgradering til dette miljø og ikke i dit produktionsmiljø. 
    
Flere ressourcer:
  
- [Opgradering af SuperFlow til Microsoft Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Overførsel fra Project Server 2007 til Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Overvejelser i forbindelse med opgradering af Project Web App-webdele](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project Software Development Kit (SDK)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>Trin 2: Migrer til Project Server 2013

Når du har bekræftet, at dine data er migreret korrekt, er næste trin at migrere til Project Server 2013.
  
Du kan få en omfattende beskrivelse af, hvad du skal gøre for at opgradere fra Project Server 2010 til Project Server 2013, under [Opgrader til Project Server 2013](/project/upgrade-to-project-server-2016). 
  
Nøgleressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Oversigt over Project Server 2013-opgraderingsprocessen](/project/upgrade-to-project-server-2016) <br/> |Oversigt over, hvad du skal gøre for at opgradere fra Project Server 2010 til Project Server 2013  <br/> |
|[Planlæg at opgradere til Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |Overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2010 til Project Server 2013, herunder systemkrav <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Ting, du skal vide om opgradering til denne version

[Nyheder i Project Server 2013-opgraderingen](/project/what-s-new-in-project-server-2013-upgrade) beskriver vigtige ændringer til opgradering af denne version. De mest bemærkelsesværdige er: 
  
- Der er ingen lokal opgradering til Project Server 2013. Metoden til database vedhæfting er den eneste understøttede metode til opgradering fra Project Server 2010 til Project Server 2013.
    
- Opgraderingsprocessen konverterer ikke kun dine Project Server 2010-data til Project Server 2013-format, men konsoliderer også de fire Project Server 2010-databaser til en enkelt Project Web App-database.
    
- I 2013-versionerne ændrede både SharePoint Server og Project Server sig til kravbaseret godkendelse. Hvis du bruger klassisk godkendelse, skal du overveje denne faktor for din opgradering. Du kan finde flere oplysninger under [Overfør fra klassisk tilstand til kravbaseret godkendelse i SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
Flere ressourcer:
  
- [Oversigt over opgraderingsprocessen til Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Opgrader dine databaser og grupper af Project Web App-websteder (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Procesdiagram til opgradering af Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [Den store databasekonsolidering, Project Server 2010-2013- migrering i 8 enkle trin](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Trin 3: Overfør til Project Server 2016

Når du har bekræftet, at dine data er migreret korrekt, er næste trin at migrere til Project Server 2016.
  
Du kan få en omfattende beskrivelse af, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016, under [Opgrader til Project Server 2016](/project/upgrading-to-project-server-2016).
  
Nøgleressourcer:
  
|**Ressource**|**Beskrivelse**|
|:-----|:-----|
|[Oversigt over Project Server 2016 opgraderingsprocessen](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Oversigt over, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016 <br/> |
|[Planlæg opgradering til Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |Planlægningsovervejelser, du opgraderer fra Project Server 2013 til Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Ting, du skal vide om opgradering til denne version

[Ting, du har brug for at vide om Project Server 2016 opgradering](/project/plan-for-upgrade-to-project-server-2016), fortæller dig nogle vigtige ændringer til opgradering af denne version, som omfatter:
  
- Når du opretter dit Project Server 2016 miljø, som du vil overføre dine Project Server 2013-data til, medtages de Project Server 2016 installationsfiler i SharePoint Server 2016. Du kan få flere oplysninger under [Installér Project Server 2016](/project/deploy-project-server-2016).
    
- Ressourceplaner frarådes i Project Server 2016. Dine Project Server 2013-ressourceplaner overføres til Ressourceengagementer i Project Server 2016 og i Project Online. Se [Oversigt: Ressourceengagementer](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) for at få flere oplysninger. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Overfør fra Portfolio Server 2007

Project Portfolio Server 2007 blev brugt sammen med Project Server 2007 til oversigtsstrategi, prioritering og optimering. Der blev ikke oprettet flere versioner af Project Portfolio Server efter denne version. Funktioner til oversigtsadministration er dog tilgængelige i Project Server 2016 og Premium-versionen af Project Online. Men data fra Project Portfolio Server 2007 kan ikke overføres til nogen af delene. Data som f.eks. forretningsfaktorer skal oprettes igen.
  
Andre ressourcer:
  
- [Project Online tjenestebeskrivelser:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) Se de funktioner til oversigtsadministration, der er inkluderet i Project Server 2016 og Project Online Premium.
    
- [Overførselsvejledning til Microsoft Office Project Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Relaterede emner

[Køreplan for ophør af support til SharePoint Server 2007](sharepoint-2007-end-of-support.md)
  
[Ressourcer, der kan hjælpe dig med at opgradere fra Office 2007-servere og -klienter](upgrade-from-office-2007-servers-and-products.md)
