---
title: Project oversigt over ophør af support til Server 2010
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
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
description: Support slutter for Project Server 2010 slutter d. 13. april 2021. Brug denne artikel som en vejledning i at opgradere Project Online eller en nyere version Project server i det lokale miljø.
ms.openlocfilehash: 9d04df22af0a0614270907f4ad4026324b026211
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594281"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project oversigt over ophør af support til Server 2010

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Project support til Server 2010 slutter den **13. april 2021**. Denne dato blev forlænget fra datoen for den forrige ophør af supporten d. 13. oktober 2020. Hvis du i øjeblikket bruger Project Server 2010, skal du bemærke, at disse relaterede produkter har følgende slutdatoer for support:

|Produkt |Slutdato for support|
|---|---|
|Project 2010 Standard|13. oktober 2020|
|Project 2010 Professional|13. oktober 2020|

Du kan finde flere oplysninger om, hvordan du når ophør af [supporten, under Opgradere fra Office 2010-servere og klientprodukter](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

Næsten alle Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser og sikkerhedsopdateringer. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Når Project når Server 2010 ophør af supporten d. 13. april 2021, yder Microsoft ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser af problemer, der opdages, og som kan påvirke stabiliteten og anvendeligheden af serveren.

- Sikkerhedsopdateringer til sårbarheder, der opdages, og som kan gøre serveren sårbar over for sikkerhedsbrister.

- Tidszoneopdateringer.

Din installation af Project Server 2010 fortsætter med at køre efter denne dato. På grund af de ændringer, der tidligere er angivet, anbefaler vi imidlertid på det kraftigste, at du overfører fra Project Server 2010 så tidligt som muligt.

## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Dine overførselsmuligheder er:

- Overfør til Project Online

- Overfør til en nyere lokal version af Project Server (helst Project Server 2019)

Her er de to stier, du kan gå for at undgå ophør af support til Project Server 2010.

![Project opgraderingsstier til Server 2010.](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|Hvorfor skulle jeg foretrække at overføre til Project Server 2019?|Hvorfor skal jeg foretrække at overføre Project Online?|
|---|---|
|Forretningsregler begrænser mig i at køre min virksomhed i skyen.  <br/><br/>  Jeg har brug for kontrol over opdateringer af mit miljø.|Jeg har mobil- eller fjernbrugere.<br/><br/>  Omkostninger til at overføre lokale servere er et vigtigt problem (hardware, software, tid og anstrengelser for at implementere osv.). <br/><br/>  Efter overførslen er omkostninger til vedligeholdelse af mit miljø et problem (f.eks. automatiske opdateringer, garanteret oppetid og så videre).|

> [!NOTE]
> Du kan finde flere oplysninger om dine overførselsmuligheder under Ressourcer, der kan hjælpe dig med [at opgradere fra Office 2010-servere og -klienter](upgrade-from-office-2010-servers-and-products.md). Bemærk, Project Server ikke understøtter hybridkonfiguration, fordi Project Server og Project Online ikke kan dele den samme ressourcepulje.

### <a name="what-are-my-options-for-project-client"></a>Hvilke muligheder har jeg for Project klient?

Hvis du bruger en Project Professional 2010 eller Project Standard 2010, er indstillingerne:

- Gå til en nyere version af Project Professional eller Project Standard
- Gå til en onlineløsning, f.eks. Project Online eller Project til internettet

#### <a name="move-to-a-newer-version-of-project-client"></a>Gå til en nyere version af Project klient

Hvis du overfører fra Project Standard 2010, kan du flytte til en nyere version af Project Standard (Project Standard 2016 eller Project Standard 2019). Vi anbefaler, at du går til den nyeste version for at drage fordel af de nyeste funktioner. Overførsel til en mindre aktuel version (Project Standard 2016) betyder også, at du er nødt til at overføre igen tidligere.

På samme måde kan du, hvis du overfører fra Project Professional 2010, flytte til en nyere version (Project Professional 2019 eller Project Professional 2016). Gå igen til den nyeste version, hvis det er muligt. Hvis du bruger Project Professional til at oprette forbindelse til Project Server, skal du sikre dig, at du overfører til en version af Project Professional, der opretter forbindelse til den version af Project Server, du bruger.

Project Professional 2010 kan brugere også overføre til Project Online Desktop-klienten, som er en abonnementsbaseret version af Project Professional 2019. Det er inkluderet i Project Plan 3 og Project Plan 5 abonnementer.

#### <a name="move-to-an-online-solution"></a>Flyt til en onlineløsning

Du kan også overføre fra Project Professional 2010 eller Project Standard 2010 til en Project-baseret onlineløsning. Både Project Plan 3 og Plan 5 Project Online og det nyeste skybaserede [tilbud, Project til internettet](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). Begge har nye funktioner og fordele, der er værd at udforske.

Du kan finde flere oplysninger om funktioner og licenser [Microsoft Project beskrivelse af tjenesten](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>Vigtige overvejelser i forbindelse med overførsel fra Project Server 2010

Overvej følgende, når du planlægger at overføre fra Project Server 2010:

- **Få hjælp fra en Microsoft-løsningsudbyder** – En opgradering Project Server 2010 kan være en udfordring. Det kræver meget forberedelse og planlægning. Det kan være særligt udfordrende, hvis du ikke var den person, der oprindeligt konfigurerede Project Server 2010. Microsoft-løsningsudbydere kan hjælpe, uanset om du planlægger at overføre Project Server 2019 eller Project Online. Søg efter en løsningsudbyder i [Microsofts løsningsudbydercenter](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Planlæg dine** tilpasninger – Tilpasninger i dit Project Server 2010-miljø fungerer muligvis ikke, når du overfører til Project Server 2019 eller Project Online. Der er betydelige forskelle i Project serverarkitekturen mellem versioner. Desuden er de nødvendige operativsystemer, databaseservere og webbrowsere, der fungerer med versionerne, forskellige. Har en plan for, hvordan du tester eller genopbygger dine tilpasninger i det nye miljø. Brug denne mulighed for at afgøre, om der stadig kræves bestemte tilpasninger. Få mere at vide under [Opret en plan for aktuelle tilpasninger under opgradering til SharePoint 2013](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **Tid og tålmodighed –** Planlægning, udførelse og test af opgradering vil tage lang tid og besvær, især for en opgradering til Project Server 2019. Hvis du overfører fra Project Server 2010 til Project Server 2019, skal du først overføre til Project Server 2013, kontrollere dine data, derefter overføre til Project Server 2016 og derefter til Project Server 2019. Det kan være en god ide at kontakte en Microsoft-løsningsudbyder om en tidsramme og anslåede omkostninger, som de kan hjælpe med.

## <a name="migrate-to-project-online"></a>Overfør til Project Online

Hvis du vælger at overføre fra Project Server 2010 til Project Online, kan du følge disse trin for manuelt at overføre dine projektplandata:

1. Gem dine projektplaner fra Project Server 2010 i .mpp-format.

2. Når Project Professional 2016, Project Professional 2019 eller Project Online Desktop Client, skal du åbne hver enkelt .mpp-fil og derefter gemme og publicere den Project Online.

Du kan manuelt oprette din PWA i Project Online (f.eks. genskabe eventuelle nødvendige brugerdefinerede felter eller virksomhedskalendere). Microsoft-løsningsudbydere kan også hjælpe med denne proces.

Vigtige ressourcer:

|Ressource|Beskrivelse|
|---|---|
|[Introduktion til Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Sådan konfigurerer og bruger du Project Online|
|[Project Online tjenestebeskrivelse](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Oplysninger om de forskellige Project Online tilgængelige|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Overfør til en nyere lokal version af Project Server

Vi er stærkt overbeviste om, at du får den bedste værdi og brugeroplevelse ved at Project Online. Men vi forstår også, at nogle organisationer har brug for at bevare projektdata lokalt. Hvis du vælger at bevare dine projektdata i det lokale miljø, kan du overføre dit Project Server 2010-miljø til Project Server 2013, Project Server 2016 eller Project Server 2019.

Hvis du ikke kan overføre til Project Online, anbefaler vi, at du overfører til Project Server 2019. Project Server 2019 indeholder de fleste af de vigtigste funktioner i tidligere versioner af Project Server. Og den passer bedst til den oplevelse, der er tilgængelig Project Online, selvom visse funktioner kun er tilgængelige i Project Online.

Når du har fuldført hver overførsel, skal du sørge for, at dine data er overført.

> [!NOTE]
> Hvis du er begrænset til en løsning i det lokale miljø, og du overvejer kun at overføre til Project Server 2013, skal du være opmærksom på, at denne version kun har et par års support tilbage. Slutdato for support for Project Server 2013 med Service Pack 2. oktober 13, 2023. Du kan finde flere oplysninger om datoer for ophør af support i [Livscykluspolitik for Microsoft-produkter](/lifecycle/).

### <a name="how-do-i-migrate-to-project-server-2019"></a>Hvordan overfører jeg til Project Server 2019?

De arkitektoniske forskelle mellem Project Server 2010 og Project Server 2019 forhindrer en direkte overførselssti. Derfor skal du overføre dine Project Server 2010-data til hver efterfølgende version af Project Server, indtil du når Project Server 2019. Trin til at opgradere Project Server 2010 til Project Server 2019:

1. Overfør Project Server 2013.

2. Overfør fra Project Serve 2013 til Project Server 2016.

3. Overfør fra Project Server 2016 til Project Server 2019.

Når du har fuldført hver overførsel, skal du sørge for, at dine data er overført.

### <a name="step-1-migrate-to-project-server-2013"></a>Trin 1: Overfør til Project Server 2013

Du kan finde en lang række oplysninger om opgradering fra Project Server 2010 til Project Server 2013 under [Opgrader til Project Server 2013](/project/upgrade-to-project-server-2016).

Vigtige ressourcer:

- [Oversigt over Project Server 2013-opgraderingsprocessen](/project/upgrade-to-project-server-2016)

  Få en detaljeret oversigt over, hvordan du opgraderer fra Project Server 2010 til Project Server 2013.
- [Planlæg at opgradere til Project Server 2013](/project/plan-for-upgrade-to-project-server-2016)

  Se overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2010 til Project Server 2013, herunder systemkrav.

- [Nyheder i Project Server 2013-opgradering omfatter](/project/what-s-new-in-project-server-2013-upgrade) vigtige ændringer i denne version, herunder:

  - Der findes ingen direkte opgradering til Project Server 2013. Metoden til databasehæftering er den eneste understøttede måde at opgradere fra Project Server 2010 til Project Server 2013.

  - Opgraderingsprocessen konverterer ikke kun dine Project Server 2010-data til Project Server 2013-format, men konsoliderer også de fire Project Server 2010-databaser til en enkelt Project Web App-database.

  - Både SharePoint Server 2013 og Project Server 2013 er blevet ændret til kravbaseret godkendelse fra den tidligere version. Hvis du bruger klassisk godkendelse, skal du overveje dette, når du opgraderer. Få mere at vide under Overfør fra klassisk tilstand til kravbaseret [godkendelse i SharePoint 2013](/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).

Vigtige ressourcer:

- [Oversigt over opgraderingsprocessen til Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)

- [Opgradere dine databaser og Project grupper af Websteder i Web App (Project Server 2013)](/project/upgrading-to-project-server-2016)

- [Microsoft Project diagram over opgraderingsprocessen for server](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [Den fantastiske databasekonsolidering, Project Server 2010 til 2013-overførsel i 8 nemme trin](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>Trin 2: Overfør til Project Server 2016

Når du flytter til Project Server 2013 og bekræfter, at dine data er overført, er næste trin at overføre Project Server 2016.

Du kan få mere at vide [under Opgrader til Project Server 2016](/Project/upgrade-to-project-server-2016).

Vigtige ressourcer:

- [Oversigt over Project Server 2016 opgraderingsprocessen](/Project/overview-of-the-project-server-2016-upgrade-process)

  Forstå, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016.

- [Planlæg opgradering til Project Server 2016](/Project/plan-for-upgrade-to-project-server-2016)

  Se de overvejelser, du bør gøre, når du planlægger at opgradere fra Project Server 2013 til Project Server 2016.

[Ting, du bør vide om Project Server 2016, omhandler](/project/plan-for-upgrade-to-project-server-2016#thingknow) vigtige ændringer i forbindelse med opgradering til denne version, som omfatter:

- Når du opretter dit Project Server 2016-miljø, skal du bemærke, Project Server 2016 installationsfilerne er inkluderet i SharePoint Server 2016. Du kan finde flere oplysninger [i Project Server 2016](/project/deploy-project-server-2016).

- Ressourceplaner frarådes i Project Server 2016. Dine Project Server 2013-ressourceplaner overføres til Ressourceengagementer i Project Server 2016 og Project Online. Se [Oversigt: Ressourceengagementer](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) for at få flere oplysninger.

### <a name="step-3-migrate-to-project-server-2019"></a>Trin 3: Overfør til Project Server 2019

Når du har overført Project Server 2016 og bekræfter, at dine data er overført, er næste trin at overføre dine data Project Server 2019.

Hvis du vil vide, hvad du skal gøre for at opgradere fra Project Server 2016 til Project Server 2019, skal du se [Opgrader til Project Server 2019](/Project/upgrade-to-project-server-2016).

Vigtige ressourcer:

- [Oversigt over Project Server 2019-opgraderingsprocessen](/project/overview-of-the-project-server-2019-upgrade-process)

  Få en høj grad af forståelse for, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016.

- [Planlæg opgradering til Project Server 2019](/project/plan-for-upgrade-to-project-server-2019)

  Se de overvejelser, du bør gøre, når du planlægger Project Server 2016 fra Project server 2019.

- [Ting, du bør vide om Project Server 2019-opgradering](/project/plan-for-upgrade-to-project-server-2016)<br/><br/>Få mere at vide om vigtige ændringer i forbindelse med opgradering til denne version, som omfatter:

  - Opgraderingsprocessen vil overføre dine data fra din Project Server 2016-database til SharePoint Server 2019 Content-databasen.  Project Server 2019 opretter ikke længere sin egen Project Server-database i SharePoint Server-farm.

  - Efter opgraderingen skal du være opmærksom på flere ændringer i Project Web App.  Du kan få mere [at vide under Nyheder i Project Server 2019](/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

**Andre ressourcer**:

- [Project Online tjenestebeskrivelser](/office365/servicedescriptions/project-online-service-description/project-online-service-description): Se de funktioner til oversigtsadministration, der følger med Project Server 2016 og Project Online Premium.

- [Microsoft Office Project oversigtsserver 2010-overførselsvejledning](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Oversigt over indstillinger for Office 2010-klient og -servere Windows 7

Du kan finde en visuel oversigt over indstillingerne for opgradering, overførsel og flytning til skyen for Office 2010-klienter og -servere og Windows 7 i slutningen af [supportplakaten](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Ophør af support til Office 2010-klienter og -servere Windows 7 poster.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Denne plakat illustrerer de forskellige veje, du kan gå for at undgå ophør af understøttelse af Office 2010-klient- og serverprodukter og Windows 7, med foretrukne stier og understøttelse af indstillinger i Microsoft 365 Enterprise fremhævet.

Du kan også [downloade](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) denne plakat og udskrive den i letter-, legal- eller tabloid-format (11 x 17).

## <a name="related-topics"></a>Relaterede emner

[Opgradering fra SharePoint 2010](upgrade-from-sharepoint-2010.md)

[Opgrader fra Office 2010-servere og -klienter](upgrade-from-office-2010-servers-and-products.md)
