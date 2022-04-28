---
title: Planlægning af netværk og overførsel for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Denne artikel indeholder links til oplysninger om netværksplanlægning, -test og -overførsel til Office 365.
ms.openlocfilehash: 6288c9afae66206b7284f751f8a63381ab8451e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077470"
---
# <a name="network-and-migration-planning-for-office-365"></a>Planlægning af netværk og overførsel for Office 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Denne artikel indeholder links til oplysninger om netværksplanlægning og -test og overførsel til Office 365.
  
Før du udruller for første gang eller overfører til Office 365, kan du bruge oplysningerne i disse emner til at estimere den båndbredde, du har brug for, og derefter teste og kontrollere, at du har tilstrækkelig båndbredde til at udrulle eller overføre til Office 365.

Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).

Hvis du vil have mere at vide om, hvordan du optimerer dit netværk til Microsoft 365 og andre Microsoft-cloudplatforme og -tjenester, skal du se plakaten [Microsoft Cloud Networking for Enterprise Architects](../solutions/cloud-architecture-models.md).
   
## <a name="estimate-network-bandwidth-requirements"></a>Estimer krav til netværksbåndbredde
<a name="EstimateBandwidthRequirements"> </a>

Brug af Office 365 kan øge udnyttelsen af din organisations internetkredsløb. Det er vigtigt at afgøre, om den mængde båndbredde, der er tilgængelig i øjeblikket, er nok til at håndtere den anslåede stigning, når Office 365 er udrullet fuldt ud, samtidig med at der er mindst 20 % kapacitet til at håndtere de travleste dage.
  
Hvis du vil anslå båndbredden, skal du følge disse trin:
  
1. Vurder antallet af klienter, der vil bruge hver internet udgående. Lad vores multi-terabit netværk håndtere så meget af forbindelsen som muligt. 
    
2. Find ud af, hvilke Office 365 tjenester og funktioner der er tilgængelige for klienter at bruge. Du vil sandsynligvis have grupper af personer med forskellige tjenester eller brugerprofiler.
    
3. Mål netværksbrugen for en pilotgruppe af klienter. Sørg for, at pilotklienterne er repræsentative for de forskellige profiler af personer i organisationen samt de forskellige geografiske placeringer. Du kan krydstjekke dine resultater i forhold til vores gamle regnemaskiner for [Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/announcing-the-exchange-client-network-bandwidth-calculator-beta/ba-p/601744) og [Microsoft Teams](/microsoftteams/prepare-network) eller det [casestudie](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365), vi udførte på vores eget netværk. 
    
4. Brug målingerne fra pilotgruppen til at ekstrapolere hele organisationens behov og teste dem igen for at validere estimaterne, før du foretager ændringer af netværket.
    
## <a name="test-your-existing-network"></a>Test dit eksisterende netværk
<a name="calculators"> </a>

 **Netværksværktøjer.** Test og valider din internetbåndbredde for at bestemme begrænsninger for download, upload og ventetid. Disse værktøjer hjælper dig med at bestemme netværkets funktioner til overførsel, og når du er udrullet fuldt ud. 
    
- [Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tester forbindelsen i dit Exchange Online miljø.
    
- Brug [Microsoft Support- og genoprettelsesassistent til Office 365](https://diagnostics.office.com/#/Download?env=SOC) til at løse problemer med Outlook og Office 365. 

- [Microsoft 365 testværktøj til netværksforbindelse](/microsoft-365/enterprise/office-365-network-mac-perf-onboarding-tool): Tester Microsoft 365 netværksforbindelse.
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a>Bedste praksis for netværksplanlægning og forbedring af overførselsydeevnen for Office 365
<a name="BestPractices"> </a>

Dyk lidt dybere ned i disse bedste fremgangsmåder for at få flere oplysninger om at forbedre din Office 365 oplevelse.
  
1. Vil du gerne i gang med at hjælpe dine brugere med det samme? Se [Bedste praksis for brug af Office 365 på et langsomt netværk](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for at få tip til brug af Office 365, herunder SharePoint Online, Exchange Online og Lync Online, når dit netværk ikke samarbejder. Denne artikel indeholder links til masser af indhold på TechNet og Support.office.com for at optimere din Office 365 oplevelse og indeholder oplysninger om nemme måder at tilpasse dine websider på, og hvordan du indstiller dine Indstillinger for Internet Explorer til den bedste Office 365 oplevelse. 
    
2. Læs [Office 365 Principper for netværksforbindelse](./microsoft-365-network-connectivity-principles.md) for at forstå principperne for forbindelse for sikker administration af Office 365 trafik og for at få den bedst mulige ydeevne. Denne artikel hjælper dig med at forstå den nyeste vejledning i sikker optimering af Office 365 netværksforbindelse. 
    
3. Øg ydeevnen for mailoverførsel ved omhyggeligt at administrere tidsplanen for Windows opdateringer. Du kan opdatere klientcomputerne i bundter og sikre, at alle klientcomputere opdateres, før de overføres til Office 365 for at regulere brugen af netværksbåndbredden. Du kan få flere oplysninger under [Opdater og konfigurer skriveborde manuelt for Office 365 for at få de nyeste opdateringer](https://support.microsoft.com/gp/office-2013-365-update).
    
4. Office 365 netværkstrafik fungerer bedst, når den behandles som en internettjeneste, der er tillid til, og har tilladelse til at omgå meget af den traditionelle filtrering og scanning, som nogle organisationer placerer på netværkstrafik til upålidelige internettjenester. Dette omfatter typisk fjernelse af udgående behandling, f.eks. godkendelse af proxybruger og pakkekontrol, samt sikring af lokal udgående data til internettet med den korrekte NAT (Network Address Translation) og tilstrækkelig båndbreddekapacitet til at håndtere de øgede netværksanmodninger. Se [Administration af Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a) for at få yderligere vejledning i, hvordan du konfigurerer dit netværk til at håndtere Office 365 som en internettjeneste, der er tillid til, på netværket.
    
1. Sørg for [at administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). Den ekstra trafik, der Office 365, resulterer i en stigning i udgående proxyforbindelser samt en stigning i sikker trafik over TLS/SSL.
    
2. Hvis dine udgående proxyer kræver brugergodkendelse, kan du opleve langsom forbindelse eller tab af funktionalitet. Hvis du tilsidesætter godkendelseskravet for de Office 365 domæner, kan det reducere denne belastning.
    
3. Hvis du har et stort antal delte kalendere og postkasser, kan du se en stigning i antallet af forbindelser fra Outlook til Exchange. Den Outlook klient kan f.eks. åbne op til to yderligere forbindelser for hver delt kalender, der er i brug. I denne situation skal du sikre, at udgående proxy kan håndtere forbindelserne eller tilsidesætte proxyen for forbindelser til Office 365 for Outlook.
    
4. Fastlæg det maksimale antal understøttede enheder for en offentlig IP-adresse, og hvordan der skal justeres på tværs af flere IP-adresser. Du kan få flere oplysninger under [NAT-support med Office 365](nat-support-with-microsoft-365.md).
    
5. Hvis du undersøger udgående forbindelser fra computere på netværket, vil omgåelse af denne filtrering til de Office 365 domæner forbedre forbindelsen og ydeevnen. Derudover fjerner omgåelse af udgående inspektion ofte behovet for en enkelt internetudgående data og aktiverer lokal internetudgående data for Office 365 bestemte netværksanmodninger.
    
6. Nogle kunder finder, at interne netværksindstillinger kan påvirke ydeevnen. Indstillinger f.eks. størrelsen på den maksimale transmissionsenhed (MTU), automatisk forhandling af netværk eller automatisk registrering og underoptimale ruter til internettet er almindelige steder at kigge på.
    
## <a name="network-planning-reference-for-office-365"></a>Reference til netværksplanlægning for Office 365
<a name="NetReference"> </a>

Disse emner indeholder detaljerede Office 365 oplysninger om netværksreferencer.
  
- [Administrere Office 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [Content Delivery Networks](content-delivery-networks.md)
    
- [Eksterne domænenavnesystemposter for Office 365](external-domain-name-system-records.md)
    
- [IPv6-understøttelse i Office 365-tjenester](ipv6-support.md)
    
- [principper for Office 365 netværksforbindelser](./microsoft-365-network-connectivity-principles.md)
    
- [Planlæg for netværksenheder, der opretter forbindelse til Office 365 tjenester](plan-for-network-devices.md)
    
- [Installationsvejledninger til Office 365 tjenester](setup-guides-for-microsoft-365.md)
 
## <a name="see-also"></a>Se også

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)
