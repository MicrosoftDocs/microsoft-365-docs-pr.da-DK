---
title: Gennemse arkitekturkrav og strukturen for Microsoft Defender for Cloud Apps
description: Microsoft Defender for Cloud Apps tekniske diagrammer forklarer arkitekturen i Microsoft 365 Defender, hvilket hjælper dig med at opbygge et pilotmiljø.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7cc147f60d3ae7ccd7014476de5c6839fa67131f
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747983"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Gennemse arkitekturkrav og nøglebegreber for Microsoft Defender for Cloud Apps


**Gælder for:**

- Microsoft 365 Defender

Denne artikel er [trin 1 af 3](eval-defender-mcas-overview.md) i processen med at oprette evalueringsmiljøet for Microsoft Defender for Cloud Apps sammen med Microsoft 365 Defender. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-identity-overview.md).

Før du aktiverer Microsoft Defender for Cloud Apps, skal du forstå arkitekturen og opfylde kravene. 

## <a name="understand-the-architecture"></a>Forstå arkitekturen

Microsoft Defender for Cloud Apps er en CASB (Cloud Access Security Broker). CASB'er fungerer som dørvogter for at formidle adgang i realtid mellem dine virksomhedsbrugere og cloudressourcer, de bruger, uanset hvor dine brugere er placeret, og uanset hvilken enhed de bruger. Microsoft Defender for Cloud Apps integreres oprindeligt med Microsofts sikkerhedsfunktioner, herunder Microsoft 365 Defender.

Uden Defender for Cloud Apps er cloudapps, der bruges af din organisation, ikke-administreret og ubeskyttet som vist.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

I illustrationen:
- En organisations brug af cloudapps er ikke overvåget og ubeskyttet. 
- Denne brug falder uden for den beskyttelse, der opnås i en administreret organisation. 

#### <a name="discovering-cloud-apps"></a>Find cloudapps

Det første skridt til at administrere brugen af cloudapps er at finde ud af, hvilke cloudapps der bruges af din organisation. I dette næste diagram illustreres det, hvordan cloudregistrering fungerer sammen med Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps i cloudregistrering" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


I denne illustration er der to metoder, der kan bruges til at overvåge netværkstrafik og finde cloudapps, der bruges af din organisation.
- A. Cloud App Discovery kan integreres med Microsoft Defender for Endpoint som standard. Defender for Endpoint-rapporter cloudapps og -tjenester, der tilgås fra it-administrerede Windows 10 og Windows 11 enheder. 
- B. For dækning på alle enheder, der er forbundet til et netværk, installeres Defender for Cloud Apps-logopsamleren på firewalls og andre proxyer for at indsamle data fra slutpunkter. Disse data sendes til Defender for Cloud Apps til analyse.

#### <a name="managing-cloud-apps"></a>Administration af cloudapps

Når du har opdaget cloudapps og analyseret, hvordan disse apps bruges af din organisation, kan du begynde at administrere de cloudapps, du vælger. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps under administration af Cloud-apps" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

I denne illustration:
- Nogle apps er sanktioneret til brug. Denne sanktion er en nem måde at begynde at administrere apps på.
- Du kan aktivere større synlighed og kontrol ved at oprette forbindelse mellem apps og app-connectors. App-connectors bruger API'er for appudbydere.


#### <a name="applying-session-controls-to-cloud-apps"></a>Anvendelse af sessionskontrolelementer på cloudapps

Microsoft Defender for Cloud Apps fungerer som en omvendt proxy, der giver proxyadgang til godkendte cloudapps. Denne klargøring gør det muligt for Defender for Cloud Apps at anvende sessionskontrolelementer, som du konfigurerer. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps – proxyadgangssessionskontrol" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

I denne illustration:
- Adgang til godkendte cloudapps fra brugere og enheder i din organisation dirigeres via Defender for Cloud Apps.
- Denne proxyadgang gør det muligt at anvende sessionskontrolelementer.
- Cloudapps, som du ikke har sanktioneret eller udtrykkeligt ikke harsaneret, påvirkes ikke.

Sessionskontrolelementer giver dig mulighed for at anvende parametre på, hvordan cloudapps bruges af din organisation. Hvis din organisation f.eks. bruger Salesforce, kan du konfigurere en sessionspolitik, der kun tillader administrerede enheder at få adgang til organisationens data på Salesforce. Et enklere eksempel kan være konfiguration af en politik til overvågning af trafik fra ikke-administrerede enheder, så du kan analysere risikoen for denne trafik, før du anvender strengere politikker.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Integration med Azure AD med appkontrol med betinget adgang

Du har muligvis allerede føjet SaaS-apps til din Azure AD lejer for at gennemtvinge multifaktorgodkendelse og andre politikker for betinget adgang. Microsoft Defender for Cloud Apps integreres oprindeligt med Azure AD. Det eneste, du skal gøre, er at konfigurere en politik i Azure AD at bruge Appkontrol med betinget adgang i Defender for Cloud Apps. Dette dirigerer netværkstrafik for disse administrerede SaaS-apps via Defender for Cloud Apps som proxy, hvilket gør det muligt for Defender for Cloud Apps at overvåge denne trafik og anvende sessionskontrolelementer. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps – SaaS-apps" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

I denne illustration:
- SaaS-apps er integreret med den Azure AD lejer. Denne integration gør det muligt for Azure AD at gennemtvinge politikker for betinget adgang, herunder multifaktorgodkendelse.
- Der føjes en politik til Azure Active Directory for at dirigere trafik for SaaS-apps til Defender for Cloud Apps. Politikken angiver, hvilke SaaS-apps denne politik skal anvendes på. Når Azure AD har håndhævet alle politikker for betinget adgang, der gælder for disse SaaS-apps, dirigerer Azure AD derefter sessionens trafik (proxyer) via Defender for Cloud Apps.
- Defender for Cloud Apps overvåger denne trafik og anvender alle sessionskontrolpolitikker, der er konfigureret af administratorer. 

Du har måske opdaget og sanktioneret cloudapps ved hjælp af Defender for Cloud Apps, der ikke er føjet til Azure AD. Du kan drage fordel af appkontrolelementet Betinget adgang ved at føje disse cloudapps til din Azure AD lejer og omfanget af dine regler for betinget adgang.

#### <a name="protecting-your-organization-from-hackers"></a>Beskyttelse af din organisation mod hackere

Defender for Cloud Apps giver selv effektiv beskyttelse. Når Defender for Cloud Apps kombineres med de andre funktioner i Microsoft 365 Defender, leverer den dog data til de delte signaler, som (sammen) hjælper med at stoppe angreb.

Det er værd at gentage denne illustration fra oversigten til denne Microsoft 365 Defender evaluerings- og pilotvejledning. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Sådan stopper Microsoft 365 Defender en kæde af trusler" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

Med fokus på højre side af denne illustration bemærker Microsoft Defender for Cloud Apps unormal adfærd som f.eks. umulig rejse, adgang til legitimationsoplysninger og usædvanlig download, filshare eller videresendelse af mailaktivitet og rapporterer disse funktionsmåder til sikkerhedsteamet. Derfor hjælper Defender for Cloud Apps med at forhindre tværgående flytning af hackere og exfiltration af følsomme data. Microsoft 356 Defender for Cloud korrelerer signalerne fra alle komponenterne for at levere hele angrebshistorien.

## <a name="understand-key-concepts"></a>Forstå vigtige begreber

I følgende tabel identificeres vigtige begreber, der er vigtige at forstå, når du evaluerer, konfigurerer og udruller Microsoft Defender for Cloud Apps.


|Koncept  |Beskrivelse |Flere oplysninger  |
|---------|---------|---------|
| Defender for Cloud Apps-dashboard | Præsenterer en oversigt over de vigtigste oplysninger om din organisation og giver links til en dybere undersøgelse.        | [Arbejde med dashboardet ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Appkontrol med betinget adgang    | Omvendt proxyarkitektur, der integreres med din idP (Identity Provider) for at give Azure AD politikker for betinget adgang og selektivt gennemtvinge sessionskontrolelementer.        |  [Beskyt apps med Microsoft Defender for Cloud Apps appkontrol med betinget adgang](/cloud-app-security/proxy-intro-aad)       |
|  Cloud App Catalog   | Cloud App Catalog giver dig et komplet billede af Microsoft-kataloget over 16.000 cloudapps, der er rangeret og scoret på baggrund af mere end 80 risikofaktorer.    |  [Arbejde med scorer for apprisiko](/cloud-app-security/risk-score)       |
| Cloud Discovery Dashboard    | Cloud Discovery analyserer dine trafiklogge og er designet til at give mere indsigt i, hvordan cloudapps bruges i din organisation, samt give beskeder og risikoniveauer.     |  [Arbejde med fundne apps   ](/cloud-app-security/discovered-apps)    |
|Forbundne apps |Defender for Cloud Apps giver komplet beskyttelse af forbundne apps ved hjælp af cloud-til-cloud-integration, API-connectors og adgangs- og sessionskontrolelementer i realtid ved hjælp af vores kontrolelementer for betinget appadgang. |[Beskyttelse af forbundne apps](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Gennemse arkitekturkrav

### <a name="discovering-cloud-apps"></a>Find cloudapps

Hvis du vil finde cloudapps, der bruges i dit miljø, kan du implementere en eller begge af følgende metoder:

- Kom hurtigt i gang med Cloud Discovery ved at integrere med Microsoft Defender for Endpoint. Med denne oprindelige integration kan du straks begynde at indsamle data om cloudtrafik på tværs af dine Windows 11 og Windows 10 enheder, på og uden for dit netværk.
- Hvis du vil finde alle cloudapps, der tilgås af alle enheder, der har forbindelse til dit netværk, skal du installere defender for Cloud Apps-logopsamleren på dine firewalls og andre proxyer. Denne udrulning hjælper med at indsamle data fra dine slutpunkter og sender dem til Defender for Cloud Apps til analyse. Defender for Cloud Apps integreres oprindeligt med nogle proxyer fra tredjepart for at få endnu flere funktioner.

Disse indstillinger er inkluderet i [trin 2. Aktivér evalueringsmiljøet](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Anvendelse af Azure AD politikker for betinget adgang på cloudapps

Appkontrol med betinget adgang (mulighed for at anvende politikker for betinget adgang på cloudapps) kræver integration med Azure AD. Denne integration er ikke et krav for at komme i gang med Defender for Cloud Apps. Det er et trin, vi opfordrer dig til at prøve i pilotfasen – [trin 3. Pilot Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>SIEM-integration

Du kan integrere Microsoft Defender for Cloud Apps med din generiske SIEM-server eller med Microsoft Sentinel for at aktivere central overvågning af beskeder og aktiviteter fra forbundne apps. 

Derudover indeholder Microsoft Sentinel en Microsoft Defender for Cloud Apps-connector, der giver bedre integration med Microsoft Sentinel. Dette arrangement giver dig ikke kun mulighed for at få indsigt i dine cloudapps, men også få avancerede analyser til at identificere og bekæmpe cybertrusler og til at styre, hvordan dine data bevæger sig.

- [Generisk SIEM-integration](/cloud-app-security/siem)
- [Stream-beskeder og Cloud Discovery-logfiler fra Defender for Cloud Apps til Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Næste trin

Trin 2 af 3: [Aktivér evalueringsmiljøet for Microsoft Defender for Cloud Apps](eval-defender-mcas-enable-eval.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md)
