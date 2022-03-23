---
title: Vurdering Microsoft 365 af netværksforbindelsen
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Microsoft 365 er udviklet til at give kunder over hele verden mulighed for at oprette forbindelse til tjenesten ved hjælp af en internetforbindelse. Efterhånden som tjenesten udvikles, forbedres sikkerheden, ydeevnen og pålideligheden Microsoft 365 kunder, der bruger internettet til at oprette en forbindelse til tjenesten.
ms.openlocfilehash: 2f982bbce4786c69034560276e5aceebaa575a00
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590981"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Vurdering Microsoft 365 af netværksforbindelsen

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 er udviklet til at give kunder over hele verden mulighed for at oprette forbindelse til tjenesten ved hjælp af en internetforbindelse. Efterhånden som tjenesten udvikles, forbedres sikkerheden, ydeevnen og pålideligheden Microsoft 365 kunder, der bruger internettet til at oprette en forbindelse til tjenesten.
  
Kunder, der planlægger at Microsoft 365 internetforbindelse, skal vurdere deres eksisterende og forventede behov for internetforbindelse som en del af installationsprojektet. Med hensyn til installationer i virksomhedsklassen er en pålidelig og passende størrelse internetforbindelse en vigtig del af Microsoft 365 funktioner og scenarier.
  
Netværksevalueringer kan udføres af mange forskellige personer og organisationer afhængigt af din størrelse og dine præferencer. Netværksomfanget af vurderingen kan også variere, afhængigt af hvor du er i installationsprocessen. For at hjælpe dig med at få en bedre forståelse af, hvad der kræves for at udføre en netværksvurdering, har vi lavet en netværksvurderingsvejledning for at hjælpe dig med at forstå de muligheder, der er tilgængelige for dig. Denne vurdering vil afgøre, hvilke trin og ressourcer der skal føjes til installationsprojektet for at kunne indføre en Microsoft 365.
  
En omfattende netværksvurdering vil give mulige løsninger på designudfordringer for netværket sammen med implementeringsdetaljer. Nogle netværksvurderinger viser, at optimal netværksforbindelse til Microsoft 365 kan tilpasses med mindre konfigurations- eller designændringer i den eksisterende udgangsinfrastruktur for netværk og internet.

Nogle bedømmelser vil indikere, at netværksforbindelse til Microsoft 365 kræver yderligere investeringer i netværkskomponenter. Virksomhedsnetværk, der strækker sig over afdelingskontorer og flere geografiske områder, kan f.eks. kræve investering i SD-WAN-løsninger eller optimeret routinginfrastruktur for at understøtte internetforbindelse til Microsoft 365. Nogle gange vil en vurdering indikere, at netværksforbindelsen til Microsoft 365 påvirkes af bestemmelser eller krav til ydeevne for scenarier som [f.eks. Skype for Business online-mediekvaliteten](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Disse yderligere krav kan føre til investeringer i internetforbindelsesinfrastruktur, routingoptimering og særlig direkte forbindelse.

Nogle ressourcer, der kan hjælpe dig med at vurdere dit netværk:

- Se [Microsoft 365 over netværksforbindelse for grundlæggende](microsoft-365-networking-overview.md) oplysninger om Microsoft 365 netværk.
- Se [Microsoft 365 principper for netværksforbindelse](./microsoft-365-network-connectivity-principles.md) for at forstå principperne for netværksforbindelse, der ligger bag sikker styring af Microsoft 365 og for at få den bedst mulige ydeevne.
- Tilmeld dig [Microsoft FastTrack](https://www.microsoft.com/fasttrack) få hjælp til Microsoft 365 med planlægning, design og installation. 
- Se afsnittet [Microsoft 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) forbindelse nedenfor for at køre grundlæggende forbindelsestests, som giver specifik vejledning om forbedringer af netværksforbindelsen, der kan foretages mellem en given brugerplacering og Microsoft 365.

> [!NOTE]
> Microsoft-autorisation er påkrævet for at bruge ExpressRoute til Office 365. Microsoft gennemser alle kundeanmodninger og godkender kun ExpressRoute til Office 365 brug, når en kundes lovmæssige krav godkender direkte forbindelse. Hvis du har sådanne krav, skal du angive tekstuddraget og weblinket til den forordning, som du fortolker til at betyde, at direkte forbindelse er påkrævet i [ExpressRoute til Office 365-anmodningsformularen for](https://aka.ms/O365ERReview) at starte en Microsoft-gennemgang. Uautoriserede abonnementer, der forsøger at oprette rutefiltre til Office 365, modtager [en fejlmeddelelse](https://support.microsoft.com/kb/3181709).
  
Hovedpunkter du bør overveje, når du planlægger din netværksvurdering for Microsoft 365:
  
- Microsoft 365 er en sikker, pålidelig, højtydende tjeneste, der kører via det offentlige internet. Vi investerer til videre for at forbedre disse aspekter af tjenesten. Alle Microsoft 365-tjenester er tilgængelige via internetforbindelse.

- Vi optimerer kontinuerligt de grundlæggende aspekter af Microsoft 365 f.eks. tilgængelighed, global rækkevidde og ydeevne for internetbaserede forbindelser. For example, many Microsoft 365 services leverage an expanding set of internet facing edge nodes. Dette grænsenetværk giver den bedste afstand og ydeevne til forbindelser, der kommer via internettet.

- Når du overvejer at bruge Microsoft 365 til nogen af de inkluderede tjenester som f.eks. Teams eller Skype for Business Online tale-, video- eller mødefunktioner, skal kunder fuldføre en netværksvurdering fra ende til anden og opfylde forbindelseskrav ved hjælp [af Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Hvis du evaluerer din Microsoft 365 og er i tvivl om, hvor du skal starte din netværksvurdering, eller har fundet designudfordringer for netværket, som du har brug for hjælp til at overvinde, skal du arbejde med dit Microsoft-kontoteam.

## <a name="the-microsoft-365-connectivity-test"></a>Den Microsoft 365 forbindelsestest

Testen [Microsoft 365](https://aka.ms/netonboard) forbindelse er en koncepttest for netværkvurderingsværktøjet (POC), der kører grundlæggende forbindelsestests mod din Microsoft 365-lejer og laver specifikke anbefalinger til netværksdesign for optimal Microsoft 365 ydeevne. Værktøjet fremhæver almindelige valgmuligheder for perimeterdesign for store virksomhedsnetværk, som er nyttige for internetbrowsing, men påvirker ydeevnen i store SaaS-programmer som f.eks. Microsoft 365.

Værktøjet Netværks onboarding gør følgende:

- Registrerer din placering, eller du kan angive en placering, der skal testes
- Kontrollerer placeringen af dit netværks udgangspunkt
- Tester netværksstien til den nærmeste Microsoft 365 servicesideport
- Leverer avancerede test ved hjælp af et Windows 10 program, der kan downloades, og som laver anbefalinger til perimeternetværksdesign, der er relateret til proxyservere, firewalls og DNS. Værktøjet kører også ydeevnetests for Skype for Business Online, Microsoft Teams, SharePoint Online og Exchange Online.

Værktøjet har to komponenter: en browserbaseret brugergrænseflade, der indsamler grundlæggende forbindelsesoplysninger, og et Windows 10-program, der kan downloades, og som kører avancerede test og returnerer yderligere vurderingsdata.

Det browserbaserede værktøj viser følgende oplysninger:

- Fanen Resultater og virkning
  - Placeringen på et kort over den in use service front door
  - Placeringen på et kort over andre forside døre, som giver optimal forbindelse
  - Relativ ydeevne sammenlignet med andre Microsoft 365 i nærheden af dig
- Fanen Detaljer og løsninger
  - Brugerplacering efter by og land
  - Netværks udgangspunkt efter by, stat og land
  - Bruger til at netværk udgangsafstand
  - Microsoft 365 Exchange Online placering af servicefronten
  - Optimal Microsoft 365 Exchange Online servicefrontporte til brugerplacering
  - Kunder i dit metroområde med bedre ydeevne

Programmet Advanced Tests, der kan downloades, indeholder følgende yderligere oplysninger:

- Fanen Detaljer og løsninger (tilføjet)
  - Brugerens standardgateway
  - Client DNS Server
  - Client DNS Recursive Resolver
  - Exchange Online DNS-server
  - SharePoint ONLINE DNS-server
  - Identifikation af proxyserver
  - Kontrol af medieforbindelse
  - Pakketab af mediekvalitet
  - Ventetid for mediekvalitet
  - Jitter i mediekvalitet
  - Omarranger mediekvalitetspakke
- Forbindelsestest til flere funktionsspecifikke slutpunkter
- Netværksstidiagnosticering, der omfatter sporings- og ventetidsdata for Exchange Online, SharePoint online og Teams tjenester

Du kan læse om Microsoft 365-forbindelsestesten og give feedback i blogindlægget Opdaterede [Microsoft 365-forbindelsestest med](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) nye anbefalinger til netværksdesign. Oplysninger om fremtidige opdateringer til dette værktøj og Microsoft 365-netværksopdateringer sendes til Office 365 [Networking blog](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking).
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365networkconnectivity.](./microsoft-365-network-connectivity-principles.md)
  
## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 over netværksforbindelse](microsoft-365-networking-overview.md)

[Microsoft 365 principper for netværksforbindelse](./microsoft-365-network-connectivity-principles.md)

[Administrere Office 365 slutpunkter](managing-office-365-endpoints.md)

[Office 365-URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md)

[Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md)

[Microsoft 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)