---
title: Netværk for Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Forstå Contoso-netværksinfrastrukturen, og hvordan virksomheden bruger sin SD-WAN-teknologi for optimal netværksydeevne til Microsoft 365 til skytjenester for virksomheder.
ms.openlocfilehash: 94c9c43e35f0f1a3d973529aa2b107cffe608693
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587857"
---
# <a name="networking-for-the-contoso-corporation"></a>Netværk for Contoso Corporation

For at indføre en skyomfattende infrastruktur, udtænkte Contoso en grundlæggende ændring af, hvordan netværkstrafik til skytjenester bevæger sig. I stedet for en intern hub-and-ege-model, der fokuserer på netværksforbindelser og trafik på næste niveau i Office-hierarkiet, har de tilknyttet brugerplaceringer til lokale internet udgangspunkter og lokale forbindelser til den nærmeste Microsoft 365-netværksplacering på internettet.

## <a name="networking-infrastructure"></a>Netværksinfrastruktur

Dette er de netværkselementer, der forbinder Contoso-kontorer i hele verden:

- WAN-netværk (Multiproto label switching) (MPLS)

  Et MPLS WAN-netværk forbinder Paris's hovedkvarter til regionale kontorer og regionale kontorer til satellitkontorer i en ege-og-hub-konfiguration. Netværket giver brugerne mulighed for at få adgang til lokale servere, der udgør line of business-programmer i Paris's hovedkvarter. Den ruter også generisk internettrafik til Paris-kontoret, hvor netværksikkerhedsenheder renser anmodningerne. I hvert kontor leverer routere trafik til kablede værter eller trådløse adgangspunkter på undernet, som bruger det private IP-adresseområde.

- Lokal direkte internetadgang til Microsoft 365 trafik

  Hvert kontor har en software defineret WAN-enhed (SD-WAN), der har en eller flere lokale internetudbyderes netværkskredsløb med sin egen internetforbindelse via en proxyserver. Dette er typisk implementeret som et WAN-link til en lokal internetudbyder, der også indeholder offentlige IP-adresser og en lokal DNS-server.

- Internet tilstedeværelse

  Contoso ejer det offentlige domænenavn for contosocom\.. Det offentlige Contoso-websted til bestilling af produkter er et sæt servere i et internettilsluttet datacenter på Paris campus. Contoso bruger et /24 offentligt IP-adresseområde på internettet.

Figur 1 viser Contoso-netværksinfrastrukturen og dens forbindelser til internettet.

![Contoso-netværket.](../media/contoso-networking/contoso-networking-fig1.png)
 
**Figur 1: Contoso-netværket**

## <a name="use-of-sd-wan-for-optimal-network-connectivity-to-microsoft"></a>Brug af SD-WAN for optimal netværksforbindelse til Microsoft

Contoso fulgte [Microsoft 365 principper for netværksforbindelse for](microsoft-365-network-connectivity-principles.md) at:

- Identificer og Microsoft 365 på netværkstrafik
- Egress netværksforbindelser lokalt
- Undgå netværks hairpins
- Tilgå dublerede netværkssikkerhedsenheder

Der er tre kategorier af netværkstrafik for Microsoft 365: *Optimer**, Tillad* og *Standard*. Optimer og Tillad trafik er pålidelig netværkstrafik, der er krypteret og sikret på slutpunkterne og er beregnet til Microsoft 365 netværket.

Contoso har besluttet at:

- Brug direkte internetud udgangspunkt til at optimere og tillade kategoritrafik og til at videresende al Standard-kategoritrafik til den Paris-baserede centrale internetforbindelse.

- Installér SD-WAN-enheder på hvert kontor som en nem måde at følge disse principper på og opnå optimal netværksydeevne for Microsoft 365 skybaserede tjenester.

  SD-WAN-enhederne har en LAN-port til det lokale kontornetværk og flere WAN-porte. En WAN-port opretter forbindelse til deres MPLS-netværk. En anden opretter forbindelse til et lokalt ISP-kredsløb. SD-WAN-enhedsruterne Optimer og Tillad kategorinetværkstrafik via isp-linket.

## <a name="the-contoso-line-of-business-app-infrastructure"></a>Line of business-appinfrastrukturen i Contoso

Contoso har tegnet sin line of business-applikation og server intranetinfrastrukturen til følgende:

- Satellitkontorer bruger lokale cacheservere til at lagre dokumenter og interne websteder, der tilgås ofte.
- Regionale hubs bruger regionale programservere til de regionale og satellitbaserede kontorer. Disse servere synkroniseres med servere i Paris's hovedkvarter.
- Paris campus-datacentrene indeholder centraliseret programservere, der betjene hele organisationen.

Figur 2 viser procentdelen af netværkskapaciteten, der bruges ved åbning af servere på tværs af Contoso-intranettet.

![Contoso-infrastrukturen til interne programmer.](../media/contoso-networking/contoso-networking-fig2.png)
 
**Figur 2: Contoso-infrastruktur til interne programmer**

For satellit- eller regionale hubkontorer kan 60 % af de ressourcer, medarbejderne skal bruge, betjenes af satellit- og regionale hubkontorservere. De yderligere 40 procent af ressourceanmodninger skal gå over WAN-linket til Paris campus.

## <a name="network-analysis-and-preparation-for-microsoft-365-for-enterprise"></a>Netværksanalyse og forberedelse til Microsoft 365 til virksomheder

En vellykket indførelse Microsoft 365 virksomhedstjenester af Contoso-brugere afhænger af den meget tilgængelige og performant forbindelse til internettet eller direkte til Microsofts skytjenester. Contoso har taget disse trin for at planlægge og implementere optimeret forbindelse til Microsoft 365 til skytjenester for virksomheder:

1. Opret et firma-WAN-netværksdiagram for at hjælpe med planlægningen

   For at starte deres netværksplanlægning oprettede Contoso et diagram, der viser deres kontorplaceringer, eksisterende netværksforbindelse, eksisterende perimeterenheder på netværket og tjenesteklasser, der administreres på netværket. De brugte dette diagram til hvert efterfølgende trin i planlægningen og implementeringen af netværksforbindelsen.

2. Oprette en plan for Microsoft 365 for virksomhedens netværksforbindelse

   Contoso brugte [Microsoft 365-principperne](microsoft-365-network-connectivity-principles.md) for netværksforbindelse og eksempler på referencenetværksarkitekturer til at identificere SD-WAN som deres foretrukne topologi til Microsoft 365 forbindelse.

3. Analysér anvendelsen af internetforbindelse og MPLS-WAN-båndbredde på hvert kontor, og øg båndbredden efter behov

   Hvert kontors aktuelle forbrug blev analyseret, og kredsløbene blev øget, så forudsagte Microsoft 365 skybaseret trafik ville fungere med et gennemsnit af 20 procent ubrugt kapacitet.

4. Optimer ydeevnen til Microsoft-netværkstjenester

   Contoso bestemte Office 365-, Intune- og Azure-slutpunkter og konfigurerede firewalls, sikkerhedsenheder og andre systemer i internetstien for at opnå optimal ydeevne. Slutpunkter for Office 365 og Tillad kategoritrafik blev konfigureret i SD-WAN-enheder til routing via ISP-kredsløbet.

5. Konfigurere intern DNS

   DNS skal være funktionel og skal opslags lokalt for at kunne Microsoft 365 trafik.

6. Valider netværksslutpunkt og portforbindelse

   Contoso kørte Testværktøjer til Microsoft-netværksforbindelse for at validere forbindelsen Microsoft 365 virksomhedens skytjenester.

7. Optimer medarbejdercomputere til netværksforbindelse

   Der blev kontrolleret individuelle computere for at sikre, at de nyeste opdateringer til operativsystemet blev installeret, og at sikkerhedsovervågningen på slutpunktet var aktiv på alle klienter.

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso udnytter sine lokale [Active Directory-domæneservices i](contoso-identity.md) skyen til medarbejdere og federating-godkendelse til kunder og forretningspartnere.

## <a name="see-also"></a>Se også

[Netværksoversigt for Microsoft 365](networking-roadmap-microsoft-365.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)
