---
title: Netværk for Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Forstå Contoso-netværksinfrastrukturen, og hvordan virksomheden bruger sin SD-WAN-teknologi til optimal netværksydeevne til at Microsoft 365 til virksomhedscloudtjenester.
ms.openlocfilehash: f8450b63bed68de414c0ea585b6f5e199c87ad90
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093937"
---
# <a name="networking-for-the-contoso-corporation"></a>Netværk for Contoso Corporation

For at indføre en cloudbaseret infrastruktur har Contoso udtænkt et grundlæggende skift i, hvordan netværkstrafik til cloudtjenester bevæger sig. I stedet for en intern hub-and-spoke-model, der fokuserer netværksforbindelse og trafik for det næste niveau i Office-hierarkiet, tilknyttede de brugerplaceringer til lokale internetudgange og lokale forbindelser til den nærmeste Microsoft 365 netværksplacering på internettet.

## <a name="networking-infrastructure"></a>Netværksinfrastruktur

Dette er de netværkselementer, der forbinder Contoso-kontorer over hele verden:

- MPLS WAN-netværk (Multiprotocol Label Switching)

  Et MPLS WAN-netværk forbinder Paris hovedkvarter til regionale kontorer og regionale kontorer til satellitkontorer i en ege-og-hub konfiguration. Netværket giver brugerne mulighed for at få adgang til lokale servere, der udgør line-of-business applikationer i Paris hovedkvarter. Den sender også generisk internettrafik til Paris-kontoret, hvor netværkssikkerhedsenheder renser anmodningerne. Inden for hvert kontor leverer routere trafik til kablede værter eller trådløse adgangspunkter på undernet, som bruger den private IP-adresseplads.

- Lokal direkte internetadgang for Microsoft 365 trafik

  Hvert office har en softwaredefineret WAN-enhed (SD-WAN), der har et eller flere lokale INTERNET ISP-netværkskredsløb med sin egen internetforbindelse via en proxyserver. Dette implementeres typisk som et WAN-link til en lokal internetudbyder, der også leverer offentlige IP-adresser og en lokal DNS-server.

- Internet tilstedeværelse

  Contoso ejer det offentlige contosocom-domænenavn\.. Den offentlige Contoso-hjemmeside til bestilling af produkter er et sæt servere i et internetforbundet datacenter på Paris campus. Contoso bruger et /24 offentligt IP-adresseinterval på internettet.

Figur 1 viser Contoso-netværksinfrastrukturen og dens forbindelser til internettet.

![Contoso-netværket.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Figur 1: Contoso-netværket**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Brug af SD-WAN for at få optimal netværksforbindelse til Microsoft

Contoso fulgte [principperne for Microsoft 365 netværksforbindelse](microsoft-365-network-connectivity-principles.md) for at:

- Identificer og differentiere Microsoft 365 netværkstrafik
- Egress netværksforbindelser lokalt
- Undgå netværkshårnåle
- Tilsidestil duplikerede netværkssikkerhedsenheder

Der er tre kategorier af netværkstrafik til Microsoft 365: *Optimer*, *Tillad* og *Standard*. Optimer og tillad trafik er netværkstrafik, der er tillid til, og som er krypteret og sikret på slutpunkterne og er beregnet til det Microsoft 365 netværk.

Contoso besluttede at:

- Brug direkte internet udgang for Optimer og Tillad kategoritrafik og til at videresende al Standardkategoritrafik til den centrale internetforbindelse i Paris.

- Udrul SD-WAN-enheder på hvert kontor som en nem måde at følge disse principper på og opnå optimal netværksydeevne for Microsoft 365 cloudbaserede tjenester.

  SD-WAN-enhederne har en LAN-port til det lokale Office-netværk og flere WAN-porte. En WAN-port opretter forbindelse til deres MPLS-netværk. En anden opretter forbindelse til et lokalt ISP-kredsløb. SD-WAN-enhedsruterne Optimer og Tillad kategorinetværkstrafik via ISP-linket.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Contoso-infrastrukturen for line of business-apps

Contoso har udviklet sin line of business-program- og serverintranetinfrastruktur til følgende:

- Satellitkontorer bruger lokale cachelagringsservere til at gemme ofte tilgåede dokumenter og interne websteder.
- Regionale hubs bruger regionale programservere til regionale kontorer og satellitkontorer. Disse servere synkroniseres med servere i Hovedkvarteret i Paris.
- Campusdatacentrene i Paris indeholder centraliserede programservere, der betjener hele organisationen.

Figur 2 viser den procentdel af netværkstrafikkapaciteten, der bruges til at få adgang til servere på tværs af Contoso-intranettet.

![Contoso-infrastrukturen til interne programmer.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Figur 2: Contoso-infrastrukturen til interne programmer**

For satellit- eller regionale hubkontorer kan 60 procent af de ressourcer, der kræves af medarbejdere, betjenes af satellit- og regionale hub office-servere. De yderligere 40 procent af ressourceanmodninger skal gå over WAN-linket til Paris campus.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Netværksanalyse og forberedelse til Microsoft 365 for virksomheder

Contoso-brugeres vellykkede indførelse af Microsoft 365 til virksomhedstjenester afhænger af, at der er høj tilgængelig og effektiv forbindelse til internettet eller direkte til Microsoft-cloudtjenester. Contoso tog disse trin for at planlægge og implementere optimeret forbindelse for at Microsoft 365 til cloudtjenester i virksomheder:

1. Opret et WAN-netværksdiagram for virksomheden for at hjælpe med planlægningen

   For at starte netværksplanlægningen oprettede Contoso et diagram, der viser deres kontorplaceringer, eksisterende netværksforbindelse, eksisterende netværksperimeterenheder og tjenesteklasser, der administreres på netværket. De brugte dette diagram til hvert efterfølgende trin i planlægningen og implementeringen af netværksforbindelsen.

2. Opret en plan for Microsoft 365 til virksomhedsnetværksforbindelse

   Contoso brugte [principperne for Microsoft 365 netværksforbindelse](microsoft-365-network-connectivity-principles.md) og eksempler på netværksarkitekturer for at identificere SD-WAN som deres foretrukne topologi for Microsoft 365 forbindelse.

3. Analysér udnyttelse af internetforbindelse og MPLS-WAN-båndbredde på hvert kontor, og øg båndbredden efter behov

   Hvert kontors aktuelle forbrug blev analyseret, og kredsløbene blev forøget, så forudsagt Microsoft 365 cloudbaseret trafik ville fungere med gennemsnitligt 20 % ubrugt kapacitet.

4. Optimer ydeevnen til Microsoft-netværkstjenester

   Contoso bestemte sættet af Office 365, Intune og Azure-slutpunkter og konfigurerede firewalls, sikkerhedsenheder og andre systemer i internetstien for at opnå optimal ydeevne. Slutpunkter for Office 365 Optimere og Tillad kategoritrafik blev konfigureret til SD-WAN-enheder til routing over INTERNETUDBYDERens kredsløb.

5. Konfigurer intern DNS

   DNS skal være funktionel og søges lokalt for Microsoft 365 trafik.

6. Valider netværksslutpunkt og portforbindelse

   Contoso kørte testværktøjerne til Microsofts netværksforbindelse for at validere forbindelsen til Microsoft 365 til cloudtjenester i virksomheder.

7. Optimer medarbejdercomputere til netværksforbindelse

   De enkelte computere blev kontrolleret for at sikre, at de nyeste opdateringer af operativsystemet blev installeret, og at overvågning af slutpunktets sikkerhed var aktiv på alle klienter.

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso [udnytter sine Active Directory i det lokale miljø Domænetjenester i skyen](contoso-identity.md) til medarbejdere og føderering af godkendelse for kunder og forretningspartnere.

## <a name="see-also"></a>Se også

[Oversigt over netværk for Microsoft 365](networking-roadmap-microsoft-365.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)
