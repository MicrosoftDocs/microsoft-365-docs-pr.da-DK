---
title: Project oversigt over ophør af support til Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 10/11/2021
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
description: Support slutter for Project Server 2013 d. 11. april 2023. Brug denne artikel som en vejledning i at opgradere Project Online eller en nyere version Project server i det lokale miljø.
ms.openlocfilehash: 5a9ae38e819dfdb8f9cc2ca3719dccea2d33fa3e
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/10/2021
ms.locfileid: "63593017"
---
# <a name="project-server-2013-end-of-support-roadmap"></a>Project oversigt over ophør af support til Server 2013

Project support til Server 2013 slutter den **11. april 2023**. Hvis du i øjeblikket bruger Project Server 2013, skal du bemærke, at Project 2013-skrivebordsappen også har de samme slutdatoer for support.

## <a name="what-does-end-of-support-mean"></a>Hvad *betyder ophør af support* ?

Næsten alle Microsoft-produkter har en supportlivscyklus, hvor de får nye funktioner, fejlrettelser og sikkerhedsopdateringer. Denne livscyklus varer typisk 10 år fra produktets første udgivelse. Slutningen af denne livscyklus kaldes for ophør af support for produktet. Når Project når Server 2013 når slutningen af supporten d. 11. april 2023, yder Microsoft ikke længere:

- Teknisk support til problemer, der kan opstå.

- Fejlrettelser af problemer, der opdages, og som kan påvirke stabiliteten og anvendeligheden af serveren.

- Sikkerhedsopdateringer til sårbarheder, der opdages, og som kan gøre serveren sårbar over for sikkerhedsbrister.

- Tidszoneopdateringer.

Din installation af Project Server 2013 fortsætter med at køre efter denne dato. På grund af de tidligere angivne ændringer anbefaler vi imidlertid på det kraftigste, at du overfører fra Project Server 2013 så tidligt som muligt.

## <a name="what-are-my-options"></a>Hvilke muligheder har jeg?

Dine overførselsmuligheder er:

- Overfør til Project Online

- Overfør til en nyere lokal version af Project Server (helst Project Server Subscription Edition)

|Hvorfor skulle jeg foretrække at overføre til Project Server 2019?|Hvorfor skal jeg foretrække at overføre Project Online?|
|---|---|
|Forretningsregler begrænser mig i at køre min virksomhed i skyen.  <br/><br/>  Jeg har brug for kontrol over opdateringer af mit miljø.|Jeg har mobil- eller fjernbrugere.<br/><br/>  Omkostninger til at overføre lokale servere er et vigtigt problem (hardware, software, tid og anstrengelser for at implementere osv.). <br/><br/>  Efter overførslen er omkostninger til vedligeholdelse af mit miljø et problem (f.eks. automatiske opdateringer, garanteret oppetid og så videre).|

> [!NOTE]
> Project Server understøtter ikke hybridkonfiguration, fordi Project Server og Project Online ikke kan dele den samme ressourcepulje.

## <a name="important-considerations-for-migrating-from-project-server-2013"></a>Vigtige overvejelser i forbindelse med overførsel Project Server 2013

Overvej følgende, når du planlægger at overføre fra Project Server 2013:

- **Få hjælp fra en Microsoft-løsningsudbyder** – Det kan være en udfordring at opgradere Project Server 2013. Det kræver meget forberedelse og planlægning. Det kan være særligt udfordrende, hvis du ikke var den person, der oprindeligt konfigurerede Project Server 2013. Microsoft-løsningsudbydere kan hjælpe, uanset om du planlægger at overføre til Project Server Subscription Edition eller til Project Online. Søg efter en løsningsudbyder i [Microsofts løsningsudbydercenter](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Tid og tålmodighed –** Planlægning, udførelse og test af opgradering vil tage lang tid og besvær, især for en opgradering til Project Server Subscription Edition. Hvis du overfører fra Project Server 2013 til Project Server Subscription Edition, skal du først overføre til Project Server 2016, kontrollere dine data og derefter til Project Server Subscription Edition. Det kan være en god ide at kontakte en Microsoft-løsningsudbyder om en tidsramme og anslåede omkostninger, som de kan hjælpe med.

## <a name="migrate-to-project-online"></a>Overfør til Project Online

Hvis du vælger at overføre fra Project Server 2013 til Project Online, kan du følge disse trin for manuelt at overføre dine projektplandata:

1. Gem dine projektplaner fra Project Server 2013 i .mpp-format.

2. Når Project Professional 2016, Project Professional 2019 eller Project Online Desktop Client, skal du åbne hver enkelt .mpp-fil og derefter gemme og publicere den Project Online.

Du kan manuelt oprette din PWA i Project Online (f.eks. genskabe eventuelle nødvendige brugerdefinerede felter eller virksomhedskalendere). Microsoft-løsningsudbydere kan også hjælpe med denne proces.

Vigtige ressourcer:

|Ressource|Beskrivelse|
|---|---|
|[Introduktion til Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Sådan konfigurerer og bruger du Project Online|
|[Project Online tjenestebeskrivelse](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Oplysninger om de forskellige Project Online tilgængelige|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Overfør til en nyere lokal version af Project Server

Vi er stærkt overbeviste om, at du får den bedste værdi og brugeroplevelse ved at Project Online. Men vi forstår også, at nogle organisationer har brug for at bevare projektdata lokalt. Hvis du vælger at beholde dine projektdata i det lokale miljø, kan du overføre dit Project Server 2013-miljø til Project Server 2016, Project Server 2019 eller Project Server Subscription Edition.

Hvis du ikke kan overføre til Project Online, anbefaler vi, at du overfører til Project Server Subscription Edition, som indeholder de fleste af de vigtigste funktioner i tidligere versioner af Project Server. Og den passer bedst til den oplevelse, der er tilgængelig Project Online, selvom visse funktioner kun er tilgængelige i Project Online. Andre faktorer, du skal overveje, er:

- Project Server Subscription Edition introducerer en fortløbende opdateringsmodel, der eliminerer behovet for at udgive nye større versioner af Project Server fremover.
- Supporten Project Server 2016 til slutningen af 2019 den 14. juli 2026. Hvis du overfører til en af versionerne, skal du planlægge en ny opgradering inden for tre år. Du kan finde flere oplysninger på siderne for supportlivscyklus for [både 2016](/lifecycle/products/project-server-2016) og [2019](/lifecycle/products/project-server-2019).

Når du har fuldført hver overførsel, skal du sørge for, at dine data er overført.

### <a name="how-do-i-migrate-to-project-server-subscription-edition"></a>Hvordan overfører jeg til Project Server Subscription Edition?

De arkitektoniske forskelle mellem Project Server 2013 og Project Server Subscription Edition forhindrer en direkte overførselssti. Så du skal overføre dine Project Server 2013-data først til Project Server 2016 og derefter til Project Server Subscription Edition. 

1. Overfør til Project Server 2016.

2. Overfør fra Project Server 2016 til Project Server Subscription Edition.

Når du har fuldført hver overførsel, skal du sørge for, at dine data er overført.

### <a name="step-1-migrate-to-project-server-2016"></a>Trin 1: Overfør til Project Server 2016

Du kan finde en lang række oplysninger om Project Server 2013 til Project Server 2016 under [Opgrader til Project Server 2016](/project/upgrade-to-project-server-2016).

Vigtige ressourcer:

- [Oversigt over Project Server 2016 opgraderingsprocessen](/project/upgrade-to-project-server-2016): Få en detaljeret oversigt over, hvordan du opgraderer fra Project Server 2013 til Project Server 2016.
- [Planlæg at opgradere til Project Server 2016](/project/plan-for-upgrade-to-project-server-2016): Se overvejelser i forbindelse med planlægning, når du opgraderer fra Project Server 2013 til Project Server 2016, herunder systemkrav.
- [Opgradering til Project Server 2016](/project/upgrading-to-project-server-2016): Se de detaljerede instruktioner om opgraderingsprocessen.

### <a name="step-2-migrate-to-project-server-subscription-edition"></a>Trin 2: Overfør til Project Server Subscription Edition

Når du går til Project Server 2016 og bekræfter, at dine data er overført, er næste trin at overføre til Project Server Subscription Edition.

Få mere at vide under [Opgrader til Project Server Subscription Edition](/project/upgrade-project-server-subscription-edition).

Vigtige ressourcer:

- [Oversigt over opgraderingsprocessen Project Server Subscription Edition](/project/overview-project-server-subscription-edition-upgrade-process): Forstå, hvad du skal gøre for at opgradere fra Project Server 2013 til Project Server 2016.
- [Planlæg opgradering til Project Server Subscription Edition](/Project/plan-upgrade-project-server-subscription-edition): Se de overvejelser, du bør gøre dig, når du planlægger at opgradere fra Project Server 2013 til Project Server 2016.
- [Opgradering til Project Server Subscription Edition](/project/how-to-upgrade-project-server-subscription-edition): Se de detaljerede instruktioner om opgraderingsprocessen.


