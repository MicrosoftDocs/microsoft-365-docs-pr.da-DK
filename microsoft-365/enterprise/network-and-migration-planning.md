---
title: Netværks- og overførselsplanlægning for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Denne artikel indeholder links til oplysninger om netværksplanlægning, test og overførsel til Office 365.
ms.openlocfilehash: 21bd36395f6ceb6a13b3180a26f8dbf7f197f134
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589761"
---
# <a name="network-and-migration-planning-for-office-365"></a>Netværks- og overførselsplanlægning for Office 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Denne artikel indeholder links til oplysninger om netværksplanlægning, test og overførsel til Office 365.
  
Før du installerer for første gang eller overfører til Office 365, kan du bruge oplysningerne i disse emner til at anslå den båndbredde, du skal bruge, og derefter teste og bekræfte, at du har tilstrækkelig båndbredde til at installere eller overføre til Office 365.

Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).

Du kan finde trinnene til at optimere dit netværk til Microsoft 365 og andre Microsoft-skyplatforme og -tjenester på [Microsoft Cloud Networking for Enterprise Architects](../solutions/cloud-architecture-models.md).
   
## <a name="estimate-network-bandwidth-requirements"></a>Anslå krav til netværksbåndbredde
<a name="EstimateBandwidthRequirements"> </a>

Brug Office 365 kan øge anvendelsen af organisationens internetkredsløb. Det er vigtigt at afgøre, om mængden af båndbredde, der er tilgængelig i øjeblikket, er nok til at håndtere den anslåede stigning, når Office 365 er fuldt implementeret, og der stadig er mindst 20 % kapacitet tilbage til at håndtere de travleste dage.
  
Hvis du vil anslå båndbredden, skal du følge disse trin:
  
1. Vurder antallet af klienter, der vil bruge hvert internet udgangspunkt. Lad vores multi-terabit-netværk håndtere så meget af forbindelsen som muligt. 
    
2. Afgør, Office 365 og funktioner skal være tilgængelige for klienter. Du vil sandsynligvis have grupper af personer med forskellige tjenester eller brugerprofiler.
    
3. Mål netværksbrug for en pilotgruppe af klienter. Sørg for, at pilotklienterne repræsenterer de forskellige profiler for personer i organisationen samt de forskellige geografiske placeringer. Du kan krydstjekke dine resultater med vores gamle beregningsmaskine for [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) og [Microsoft Teams](/microsoftteams/prepare-network) eller [den casestudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365), vi udførte på vores eget netværk. 
    
4. Brug målene fra pilotgruppen til at ekstrapolere hele organisationens behov, og test igen for at validere estimeringerne, før du foretager ændringer i netværket.
    
## <a name="test-your-existing-network"></a>Test dit eksisterende netværk
<a name="calculators"> </a>

 **Netværksværktøjer.** Test og valider din internetbåndbredde for at bestemme begrænsninger for hentning, overførsel og ventetid. Disse værktøjer hjælper dig med at bestemme mulighederne i dit netværk til overførsel, samt når du er fuldt implementeret. 
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tester forbindelsen i dit Exchange Online miljø.
    
- Brug [Microsofts Support- og genoprettelsesassistent til Office 365 at](https://diagnostics.office.com/#/Download?env=SOC) løse Outlook og Office 365 problemer. 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Bedste fremgangsmåder for netværksplanlægning og forbedring af ydeevnen for overførsel til Office 365
<a name="BestPractices"> </a>

Grave lidt dybere ned i disse bedste fremgangsmåder for at få flere oplysninger om, hvordan du Office 365 oplevelse.
  
1. Vil du i gang med at hjælpe dine brugere med det samme? Se Bedste [fremgangsmåder for](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) brug af Office 365 på et langsomt netværk for at få tip til brug af Office 365, herunder SharePoint Online, Exchange Online og Lync Online, når dit netværk bare ikke vil samarbejde. Denne artikel indeholder links til masser af indhold på TechNet og Support.office.com til optimering af din Office 365-oplevelse og indeholder oplysninger om nemme metoder til at tilpasse dine websider, og hvordan du kan angive dine Internet Explorer-indstillinger for at få den bedste Office 365 oplevelse. 
    
2. Læs [Office 365 principper for netværksforbindelse](./microsoft-365-network-connectivity-principles.md) for at forstå principperne for netværksforbindelse, der ligger bag sikker styring af Office 365 og for at få den bedst mulige ydeevne. Denne artikel hjælper dig med at forstå den seneste vejledning i sikker optimering af Office 365 netværksforbindelsen. 
    
3. Forbedr ydeevnen for mailoverførsel ved grundig administration af tidsplanen for Windows opdateringer. Du kan opdatere dine klientcomputere i batches og sikre, at alle klientcomputere opdateres før overførsel til Office 365 for at regulere brugen af netværksbåndbredde. Du kan finde flere oplysninger [i Opdatere og konfigurere skriveborde manuelt for Office 365 for de seneste opdateringer](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365-netværkstrafik fungerer bedst, når den behandles som en pålidelig internettjeneste og får tilladelse til at tilsidesætte meget af den traditionelle filtrering og scanning, som nogle organisationer placerer på netværkstrafik til upålidelige internettjenester. Dette omfatter typisk fjernelse af udgående behandling, f.eks. proxybrugergodkendelse og pakkeinspektion, samt at sikre lokale udgangspunkter til internettet med den korrekte netværksadresseoversættelse (NAT) og tilstrækkelig båndbreddekapacitet til at håndtere de øgede netværksanmodninger. Se Administration [af Office 365 slutpunkterfor](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) yderligere vejledning til konfiguration af dit netværk til at håndtere Office 365 som en pålidelig internettjeneste på dit netværk.
    
1. Sørg [for at Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Den ekstra trafik, der Office 365, medfører en større antal udgående proxy-forbindelser samt øget sikker trafik over TLS/SSL.
    
2. Hvis dine udgående proxyer kræver brugergodkendelse, kan forbindelsen blive langsom, eller funktionalitet kan gå tabt. Hvis du tilsidesætter godkendelseskravet for Office 365 domæner, kan det reducere denne overforbrug.
    
3. Hvis du har et stort antal delte kalendere og postkasser, kan du opleve en stigning i antallet af forbindelser fra Outlook til Exchange. For eksempel kan Outlook åbne op til to yderligere forbindelser for hver delt kalender, der er i brug. I denne situation skal du sikre dig, at udgangsproxyen kan håndtere forbindelserne eller tilsidesætte proxyen for forbindelser til Office 365 til Outlook.
    
4. Faststem det maksimale antal understøttede enheder til en offentlig IP-adresse, og hvordan du balancerer belastningen på tværs af flere IP-adresser. Få mere at vide under [NAT-understøttelse med Office 365](nat-support-with-microsoft-365.md).
    
5. Hvis du undersøger udgående forbindelser fra computere på netværket, vil en tilsidesætte denne filtrering til Office 365-domæner forbedre forbindelsen og ydeevnen. Desuden fjerner en tilsidesættelse af udgående inspektion ofte behovet for et enkelt internet udgangspunkt og aktiverer lokale internet udgangspunkter for Office 365 netværksanmodninger, der er bestemt.
    
6. Nogle kunder oplever, at interne netværksindstillinger kan påvirke ydeevnen. Indstillinger, f.eks. MTU (maksimal størrelse for overførselsenhed), automatisk forhandlinger eller automatisk registrering af netværk og ruter til internettet, der ikke er optimale, er almindelige steder at lede.
    
## <a name="network-planning-reference-for-office-365"></a>Netværksplanlægningsreference for Office 365
<a name="NetReference"> </a>

Disse emner indeholder detaljerede Office 365 om netværksreferencer.
  
- [Administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Netværk, der kan levere indhold](content-delivery-networks.md)
    
- [Eksterne DNS-poster for Office 365](external-domain-name-system-records.md)
    
- [IPv6-understøttelse i Office 365 tjenester](ipv6-support.md)
    
- [Office 365 principper for netværksforbindelse](./microsoft-365-network-connectivity-principles.md)
    
- [Plan for netværksenheder, der opretter forbindelse til Office 365 tjenester](plan-for-network-devices.md)
    
- [Installationsvejledninger til Office 365 tjenester](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Se også

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)