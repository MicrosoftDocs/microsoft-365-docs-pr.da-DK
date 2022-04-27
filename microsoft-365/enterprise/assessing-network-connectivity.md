---
title: Vurderer Microsoft 365 netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 er designet til at gøre det muligt for kunder over hele verden at oprette forbindelse til tjenesten via en internetforbindelse. Efterhånden som tjenesten udvikler sig, forbedres sikkerheden, ydeevnen og pålideligheden af Microsoft 365 baseret på kunder, der bruger internettet til at oprette forbindelse til tjenesten.
ms.openlocfilehash: 88664966a7451f342a140feb2ff31186cfc3c818
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099427"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Vurderer Microsoft 365 netværksforbindelse

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 er designet til at gøre det muligt for kunder over hele verden at oprette forbindelse til tjenesten via en internetforbindelse. Efterhånden som tjenesten udvikler sig, forbedres sikkerheden, ydeevnen og pålideligheden af Microsoft 365 baseret på kunder, der bruger internettet til at oprette forbindelse til tjenesten.
  
Kunder, der planlægger at bruge Microsoft 365, bør vurdere deres eksisterende og forventede behov for internetforbindelse som en del af udrulningsprojektet. I forbindelse med udrulninger i virksomhedsklassen er pålidelig og korrekt størrelse internetforbindelse en vigtig del af at bruge Microsoft 365 funktioner og scenarier.
  
Netværksevalueringer kan udføres af mange forskellige personer og organisationer, afhængigt af din størrelse og dine præferencer. Netværksomfanget for vurderingen kan også variere, afhængigt af hvor du er i din udrulningsproces. For at hjælpe dig med at få en bedre forståelse af, hvad der kræves for at udføre en netværksvurdering, har vi udarbejdet en netværksvurderingsvejledning, der kan hjælpe dig med at forstå de muligheder, der er tilgængelige for dig. Denne vurdering bestemmer, hvilke trin og ressourcer der skal føjes til udrulningsprojektet, så du kan anvende Microsoft 365.
  
En omfattende netværksvurdering vil give mulige løsninger på netværksdesignudfordringer sammen med implementeringsdetaljer. Nogle netværksvurderinger viser, at den optimale netværksforbindelse til Microsoft 365 kan imødekommes med mindre konfiguration eller designændringer af den eksisterende netværks- og internetudgående infrastruktur.

Nogle vurderinger vil indikere, at netværksforbindelsen til Microsoft 365 vil kræve yderligere investeringer i netværkskomponenter. Virksomhedsnetværk, der strækker sig over forgreninger og flere geografiske områder, kan f.eks. kræve investeringer i SD-WAN-løsninger eller optimeret routinginfrastruktur for at understøtte internetforbindelsen til Microsoft 365. I nogle tilfælde vil en vurdering indikere, at netværksforbindelsen til Microsoft 365 er påvirket af regulerings- eller ydeevnekrav i scenarier som [f.eks. Skype for Business onlinemediekvalitet](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Disse yderligere krav kan føre til investeringer i infrastruktur til internetforbindelse, routingoptimering og specialiseret direkte forbindelse.

Nogle ressourcer, der kan hjælpe dig med at vurdere dit netværk:

- Se [Microsoft 365 oversigt over netværksforbindelser](microsoft-365-networking-overview.md) for at få grundlæggende oplysninger om Microsoft 365 netværk.
- Se [principper for Microsoft 365 Network Connectivity](./microsoft-365-network-connectivity-principles.md) for at forstå forbindelsesprincipperne for sikker administration Microsoft 365 trafik og opnå den bedst mulige ydeevne.
- Tilmeld dig [Microsoft FastTrack](https://www.microsoft.com/fasttrack) for at få hjælp til Microsoft 365 planlægning, design og udrulning. 
- Se afsnittet [Microsoft 365 forbindelsestest](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) nedenfor for at køre grundlæggende forbindelsestest, der giver specifik vejledning om forbedringer af netværksforbindelsen, der kan foretages mellem en given brugerplacering og Microsoft 365.

> [!NOTE]
> Microsoft-autorisation er påkrævet for at bruge ExpressRoute til Office 365. Microsoft gennemgår alle kundeanmodninger og godkender kun ExpressRoute for Office 365 brug, når en kundes lovmæssige krav giver mulighed for direkte forbindelse. Hvis du har sådanne krav, skal du angive tekstuddraget og weblinket til den forordning, som du fortolker, så det betyder, at der kræves direkte forbindelse i [ExpressRoute for Office 365 anmodningsformular](https://aka.ms/O365ERReview) for at starte en Microsoft-gennemgang. Der vises en [fejlmeddelelse](https://support.microsoft.com/kb/3181709) for uautoriserede abonnementer, der forsøger at oprette rutefiltre for Office 365.
  
Vigtige punkter, du skal overveje, når du planlægger din netværksvurdering for Microsoft 365:
  
- Microsoft 365 er en sikker, pålidelig tjeneste med høj ydeevne, der kører over det offentlige internet. Vi fortsætter med at investere for at forbedre disse aspekter af tjenesten. Alle Microsoft 365 tjenester er tilgængelige via internetforbindelse.

- Vi optimerer løbende kerneaspekter af Microsoft 365 f.eks. tilgængelighed, global rækkevidde og ydeevne for internetbaseret forbindelse. Mange Microsoft 365 tjenester udnytter f.eks. et voksende sæt grænsenoder på internettet. Dette edge-netværk giver den bedste nærhed og ydeevne til forbindelser, der kommer over internettet.

- Når kunderne overvejer at bruge Microsoft 365 til nogen af de inkluderede tjenester, f.eks. Teams eller Skype for Business Online-tale-, video- eller mødefunktioner, bør de fuldføre en komplet netværksvurdering og opfylde forbindelseskravene ved hjælp af [Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Hvis du evaluerer Microsoft 365 og ikke er sikker på, hvor du skal begynde med din netværksvurdering, eller har fundet udfordringer med netværksdesign, som du har brug for hjælp til at overvinde, skal du arbejde sammen med dit Microsoft-kontoteam.

## <a name="the-microsoft-365-connectivity-test"></a>Microsoft 365 forbindelsestest

[Microsoft 365-forbindelsestesten](https://aka.ms/netonboard) er et blåstemplingsværktøj til netværksvurdering, der kører grundlæggende forbindelsestest i forhold til din Microsoft 365 lejer og giver specifikke anbefalinger til netværksdesign for at opnå optimal Microsoft 365 ydeevne. Værktøjet fremhæver almindelige designvalg for store virksomhedsnetværksperimetre, som er nyttige til internetbrowsing, men som påvirker ydeevnen af store SaaS-programmer, f.eks. Microsoft 365.

Værktøjet Network Onboarding gør følgende:

- Registrerer din placering, eller du kan angive en placering, der skal testes
- Kontrollerer placeringen af din netværksudgående
- Tester netværksstien til den nærmeste Microsoft 365 hoveddøren til tjenesten
- Leverer avancerede test ved hjælp af et Windows 10 program, der kan downloades, og som giver anbefalinger til perimeternetværksdesign, der er relateret til proxyservere, firewalls og DNS. Værktøjet kører også test af ydeevnen for Skype for Business Online, Microsoft Teams, SharePoint Online og Exchange Online.

Værktøjet har to komponenter: en browserbaseret brugergrænseflade, der indsamler grundlæggende forbindelsesoplysninger, og et Windows 10 program, der kan downloades, og som kører avancerede test og returnerer yderligere vurderingsdata.

Det browserbaserede værktøj viser følgende oplysninger:

- Fanen Resultater og indvirkning
  - Placeringen på et kort over hoveddøren til brugstjenesten
  - Placeringen på et kort over andre tjenestefrontdøre, der giver optimal forbindelse
  - Relativ ydeevne sammenlignet med andre Microsoft 365 kunder i nærheden af dig
- Fanen Detaljer og løsninger
  - Brugerplacering efter by og land
  - Netværks udgangsplacering efter by, stat og land
  - Udgangsafstand fra bruger til netværk
  - Microsoft 365 Exchange Online placering af hoveddøren til tjenesten
  - Optimal Microsoft 365 Exchange Online hoveddør(e) til service til brugerens placering
  - Kunder i metroområdet med bedre ydeevne

Det program, der kan downloades til avancerede test, indeholder følgende yderligere oplysninger:

- Fanen Detaljer og løsninger (tilføjet)
  - Brugerens standardgateway
  - Klient-DNS-server
  - Klient-DNS-rekursiv fortolker
  - Exchange Online DNS-server
  - SharePoint Online DNS-server
  - Proxyserveridentifikation
  - Kontrol af medieforbindelse
  - Mediekvalitet pakketab
  - Ventetid for mediekvalitet
  - Jitter for mediekvalitet
  - Omarranger pakke med mediekvalitet
- Forbindelsestest til flere funktionsspecifikke slutpunkter
- Diagnosticering af netværksstier, der omfatter sporings- og ventetidsdata for Exchange Online, SharePoint Online- og Teams-tjenester

Du kan læse om Microsoft 365 forbindelsestest og give feedback på [blogindlægget Opdateret Microsoft 365 forbindelsestest med nye anbefalinger til netværksdesign](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130). Oplysninger om fremtidige opdateringer til dette værktøj og andre Microsoft 365 netværksopdateringer vil blive sendt til [Office 365 Networking-bloggen](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking).
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365networkconnectivity.](./microsoft-365-network-connectivity-principles.md)
  
## <a name="related-topics"></a>Relaterede emner

[oversigt over Microsoft 365 Netværksforbindelse](microsoft-365-networking-overview.md)

[principper for Microsoft 365 netværksforbindelser](./microsoft-365-network-connectivity-principles.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-adressewebtjeneste](microsoft-365-ip-web-service.md)

[Microsoft 365 netværk og justering af ydeevne](network-planning-and-performance.md)

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)