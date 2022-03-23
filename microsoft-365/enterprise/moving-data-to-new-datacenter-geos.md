---
title: Flytning af kernedata til det nye Microsoft 365-datacenter geos
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 11/16/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
f1.keywords:
- NOCSH
description: Få mere at vide om nye Office 365-datacentres geocentre, og hvordan du kan bruge indstillingen for dataopbevaring til at anmode om en flytning af dine kernedata til et nyt geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 590d1b7e72f79e0e6cfd4e29a0a78560f6c13433
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63594208"
---
# <a name="moving-core-data-to-new-microsoft-365-datacenter-geos"></a>Flytning af kernedata til det nye Microsoft 365-datacenter geos

Vi fortsætter med at åbne nye datacenter-geos for Microsoft 365-tjenester. Disse nye datacentre tilføjer kapacitet og beregner ressourcer for at understøtte vores fortsatte kundebehov og forbrugsvækst. Desuden tilbyder det nye datacenter geos in-geo-dataopbevaring for kernekundedata. 

Kerne kundedata er et udtryk, der refererer til et undersæt af kundedata, herunder: 
- Exchange Online-postkasseindhold (brødtekst, kalenderposter og indholdet af vedhæftede filer i mails)
- SharePoint Online-webstedsindhold og de filer, der er gemt på det pågældende websted
- Filer uploadet til OneDrive for Business
- Teams-chatmeddelelser, herunder private beskeder, kanalmeddelelser og billeder, der bruges i chats
  
Eksisterende kunder, der har deres kernekundedata gemt i et allerede eksisterende datacenters geo, påvirkes ikke af lanceringen af et nyt datacenters geocenter. Vi introducerer ingen unikke egenskaber, funktioner eller overholdelsescertificeringer med det nye datacenter geo. Som kunde i et af disse to geos vil du opleve den samme tjenestekvalitet, ydeevne og sikkerhedskontrolelementer, som du havde før. Vi tilbyder eksisterende kunder, der er angivet i tabellen nedenfor, mulighed for at anmode om tidlig overførsel af deres organisations kerne kundedata in rest-to-their nye datacenter geo.
  
| Kunder med lejerens tilmeldingsland i | Forrige datacenter geo | Nyt datacenter geo | Geo tilgængelig siden |
|:-----|:-----|:-----|:-----|
|**Japan**| Asien/Stillehavsområdet | Japan | December 2014 |
|**Australien, New Zealand, Fiji**| Asien/Stillehavsområdet | Australien | Marts 2015 |
|**Indien**| Asien/Stillehavsområdet | Indien | Oktober 2015 |
|**Canada**| USA | Canada | Maj 2016 |
|**Storbritannien**| EU | Storbritannien | September 2016 |
|**Sydkorea**| Asien/Stillehavsområdet | Sydkorea | April 2017 |
|**Frankrig**| EU | Frankrig | Marts 2018 |
|**De Forenede Arabiske Emirater**| EU | De Forenede Arabiske Emirater | Juni 2019 |
|**Sydafrika**| EU | Sydafrika | juli 2019 |
|**Schweiz, Liechtenstein**| EU | Schweiz | december 2019 |
|**Tyskland**| EU | Tyskland | december 2019 |
|**Norge**| EU | Norge | april 2020 |
|**Brasilien**| Nord-, Mellem- og Mellemamerika | Brasilien | november 2020 |
|**Sverige**| EU | Sverige | November 2021 |

Pr. 1. oktober 2020 er kunder med et Office 365 Education-abonnement inkluderet i lejeren ikke berettiget til overførsel.

En komplet liste over alle datacenter geografiske datacentre, datacentre og placeringen af kundens data i hvile er tilgængelig som en del af de interaktive [datacenterkort](https://office.com/datamaps). 
  
## <a name="data-residency-option"></a>Indstillingen Dataopbevaring

Vi giver dig en mulighed for dataopbevaring for berettigede Microsoft 365-kunder, der er dækket af de datacenter-geos, der er angivet i tabellen ovenfor. Med denne indstilling kan berettigede kunder med krav til dataopbevaring anmode om overførsel af deres organisations kernekundedata in rest-data til deres nye datacenters geocenter.  Microsoft vil tilbyde en bindende deadline til alle berettigede kunder, der anmoder om overførsel i tilmeldingsvinduet.  Gennemgå siden [Sådan anmoder](request-your-data-move.md) du om flytning af dine data for at få mere at vide om det åbne tilmeldingsvindue for dit datacenters geo og trinnene til at tilmelde dig programmet.  Databevægelser kan tage op til 24 måneder, efter anmodningens periode udløber.

Vi introducerer ingen unikke egenskaber, funktioner eller overholdelsescertificeringer med det nye datacenter geo.
    
Den kompleksitet, præcision og skalering, hvorpå vi skal udføre databevægelser i et globalt styret og automatiseret miljø, forhindrer os i at dele, når der forventes at blive udført en data flytte for din lejer eller en anden enkelt lejer. Kunder modtager én bekræftelse i Meddelelsescenter pr. deltagende tjeneste, når dataover flytningen er fuldført. 
    
Databevægelser er en back-end-tjenestehandling med minimal indvirkning for slutbrugere. Funktioner, der kan påvirkes, er angivet på [siden Under og efter, dine data flyttes](during-and-after-your-data-move.md) . Vi overholder [Serviceaftale (Service Level Agreement) for Microsoft Online Services for](https://go.microsoft.com/fwlink/p/?LinkId=523897) tilgængelighed, så der er intet, kunderne skal forberede sig på eller overvåge under flytningen. Meddelelse om eventuel servicevedligeholdelse udføres, hvis det er nødvendigt. 

Data flyttes til det nye datacenters geocenter uden yderligere omkostninger for kunden.
    
## <a name="related-topics"></a>Relaterede emner 
 
[Sådan anmoder du om, at dine data flyttes](request-your-data-move.md)
    
[Ofte stillede spørgsmål om flytning af data](data-move-faq.yml)
  
[Nye datacenter-geos til Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)
  
[Azure-tjenester efter område](https://azure.microsoft.com/regions/)

[Teams-oplevelse i et Microsoft 365-multi-geo-aktiveret leje](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
