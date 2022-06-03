---
title: Flytning af kernedata til nye Microsoft 365 geos for datacentre
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Få mere at vide om nye Office 365 datacenter geos, og hvordan du bruger indstillingen for dataopbevaring til at anmode om en flytning af dine kernedata til en ny geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c70d59edba9cd35710b315adc8f93d6139fd2595
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873572"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Flytning af kernedata til nye Microsoft 365 geos for datacentre

Vi fortsætter med at åbne nye datacenter-geos for Microsoft 365-tjenester. Disse nye datacenter-geos tilføjer kapacitet og beregningsressourcer for at understøtte vores løbende kundeefterspørgsel og forbrugsvækst. Derudover tilbyder det nye datacenter geos in-geo-dataopbevaring for kernekundedata.

Kernekundedata er et begreb, der refererer til et undersæt af kundedata, herunder:

- Exchange Online postkasseindhold (brødtekst, kalenderposter og indholdet af vedhæftede filer i mails)
- SharePoint onlinewebstedsindhold og de filer, der er gemt på det pågældende websted
- Filer, der er overført til OneDrive for Business
- Teams chatbeskeder, herunder private meddelelser, kanalmeddelelser og billeder, der bruges i chats
  
Eksisterende kunder, der har deres kernekundedata gemt i et allerede eksisterende datacenter geo, påvirkes ikke af lanceringen af et nyt datacenter geo. Vi introducerer ingen unikke funktioner eller certificeringer af overholdelse af angivne standarder med det nye datacenter Geo. Som kunde i et af disse to geografiske områder vil du opleve den samme kvalitet af service-, ydeevne- og sikkerhedskontroller, som du gjorde før. Vi tilbyder eksisterende kunder, der er angivet i nedenstående tabel, mulighed for at anmode om tidlig migrering af organisationens centrale kundedata som inaktive data til deres nye datacenter geo.
  
| Kunder med lande, hvor lejertilmelding er tilmeldt | Tidligere geo for datacenter | Nyt datacenter geo | Geo tilgængelig siden |
|:-----|:-----|:-----|:-----|
|**Japan**| Asien/Stillehavsområdet | Japan | December 2014 |
|**Australien, New Zealand, Fiji**| Asien/Stillehavsområdet | Australien | Marts 2015 |
|**Indien**| Asien/Stillehavsområdet | Indien | Oktober 2015 |
|**Canada**| USA | Canada | Maj 2016 |
|**Storbritannien**| Eu | Storbritannien | September 2016 |
|**Sydkorea**| Asien/Stillehavsområdet | Sydkorea | April 2017 |
|**Frankrig**| Eu | Frankrig | Marts 2018 |
|**De Forenede Arabiske Emirater**| Eu | De Forenede Arabiske Emirater | Juni 2019 |
|**Sydafrika**| Eu | Sydafrika | juli 2019 |
|**Schweiz, Liechtenstein**| Eu | Schweiz | december 2019 |
|**Tyskland**| Eu | Tyskland | december 2019 |
|**Norge**| Eu | Norge | april 2020 |
|**Brasilien**| Americas | Brasilien | november 2020 |
|**Sverige**| Eu | Sverige | November 2021 |

Fra den 1. oktober 2020 er kunder med et Office 365 Education abonnement, der er inkluderet i lejeren, ikke berettiget til overførsel.

En komplet liste over alle datacenter-geos, datacentre og placeringen af kundedata som rest er tilgængelig som en del af de [interaktive datacenterkort](https://office.com/datamaps).
  
## <a name="data-residency-option"></a>Indstillingen Dataopbevaring

Vi leverer en mulighed for dataopbevaring til berettigede Microsoft 365 kunder, der er omfattet af de geografiske datacentre, der er angivet i tabellen ovenfor. Med denne mulighed kan berettigede kunder med krav til dataopbevaring anmode om migrering af deres organisations centrale kundedata som inaktive data til deres nye datacenter geo.  Microsoft tilbyder en bindende deadline til alle berettigede kunder, der anmoder om migrering under tilmeldingsvinduet.  Gennemse siden [Sådan anmoder du om flytning af dine data for at](request-your-data-move.md) få flere oplysninger om det åbne tilmeldingsvindue for dit datacenter geo og trinnene til at tilmelde dig programmet.  Dataflytninger kan tage op til 24 måneder, efter at anmodningsperioden er afsluttet.

Vi introducerer ingen unikke funktioner eller certificeringer af overholdelse af angivne standarder med det nye datacenter Geo.

Den kompleksitet, præcision og skalering, hvor vi skal udføre dataflytninger i et globalt drevet og automatiseret miljø, forhindrer os i at dele, når en dataflytning forventes at blive fuldført for din lejer eller en anden enkelt lejer. Kunderne modtager én bekræftelse i Meddelelsescenter pr. deltagertjeneste, når dataflytningen er fuldført.

Dataflytninger er en back end-tjenestehandling, der har minimal indvirkning på slutbrugerne. De funktioner, der kan påvirkes, vises på siden [Under og efter flytning af dine data](during-and-after-your-data-move.md) . Vi overholder [Serviceniveauaftalen for Microsoft Online Services,](https://go.microsoft.com/fwlink/p/?LinkId=523897) så der ikke er noget, som kunderne behøver at forberede sig på eller overvåge under flytningen. Meddelelse om eventuel vedligeholdelse af tjenesten udføres, hvis det er nødvendigt.

Dataflytninger til det nye datacenter geo fuldføres uden yderligere omkostninger for kunden.

## <a name="related-topics"></a>Relaterede emner

[Sådan anmoder du om flytning af dine data](request-your-data-move.md)

[Generelle ofte stillede spørgsmål om dataflytning](data-move-faq.md)
  
[Nyt datacenter-geos til Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Azure-tjenester efter område](https://azure.microsoft.com/regions/)

[Teams oplevelse i en Microsoft 365 Multi-Geo-aktiveret lejer](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
