---
title: Gennemgå arkitekturkrav og strukturen for Microsoft Defender for Cloud Apps
description: Microsoft Defender for Cloud Apps tekniske diagrammer forklarer arkitekturen i Microsoft 365 Defender, som kan hjælpe dig med at opbygge et pilotmiljø.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6547c1b269ede9385b384ca18fe6f2ca34d35109
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500315"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>Gennemgå arkitekturkrav og nøglekoncepter for Microsoft Defender for Cloud Apps


**Gælder for:**

- Microsoft 365 Defender

Denne artikel er [trin 1 af 3 i](eval-defender-mcas-overview.md) oprettelsen af evalueringsmiljøet for Microsoft Defender for Cloud Apps sammen Microsoft 365 Defender. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-identity-overview.md).

Før du aktiverer Microsoft Defender for Cloud Apps, skal du sørge for, at du forstår arkitekturen og kan opfylde kravene. 

## <a name="understand-the-architecture"></a>Forstå arkitekturen

Microsoft Defender for Cloud Apps er en sikkerhedsmægler til skyadgang (CASB). CASBs fungerer som gatekeeper to broker access in real time between your enterprise users and cloud resources they use, wherever your users are located and regardless of the device they are using. Microsoft Defender for Cloud Apps integreret med Microsofts sikkerhedsfunktioner, herunder Microsoft 365 Defender.

Uden Defender til skyapps er skyapps, der bruges af din organisation, ikke administreret og ubeskyttet, som det fremgår af det.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

I illustrationen:
- En organisations brug af skyapps bliver ikke overvåget og ubeskyttet. 
- Denne brug falder uden for de beskyttelser, der er opnået i en administreret organisation. 

#### <a name="discovering-cloud-apps"></a>Opdage skyapps

Det første trin til at administrere brugen af skyapps er at finde ud af, hvilke skyapps der bruges af din organisation. Dette næste diagram illustrerer, hvordan opdagelse i skyen fungerer med Defender til skyapps.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps i Cloud Discovery" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


I denne illustration er der to metoder, der kan bruges til at overvåge netværkstrafik og opdage skyapps, der bruges af din organisation.
- A. Cloud App Discovery integreres med Microsoft Defender for Endpoint oprindelige. Defender for Endpoint rapporterer, at der tilgås skyapps og -tjenester fra it-administrerede Windows 10 og Windows 11 enheder. 
- B. For dækning på alle enheder, der har forbindelse til et netværk, er Defender for Cloud Apps log-logindsamleren installeret på firewalls og andre proxyer til at indsamle data fra slutpunkter. Disse data sendes til Defender til skyapps til analyse.

#### <a name="managing-cloud-apps"></a>Administration af skyapps

Når du har opdaget skyapps og analyserer, hvordan disse apps bruges af din organisation, kan du begynde at administrere apps i skyen, som du vælger. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps mens administrationen af skyappsene" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

I denne illustration:
- Nogle apps er godkendt til brug. Denne mulighed er en simpel måde at begynde at administrere apps på.
- Du kan aktivere større synlighed og kontrol ved at forbinde apps med appforbindelser. App-forbindelser bruger API'er fra appudbydere.


#### <a name="applying-session-controls-to-cloud-apps"></a>Anvende sessionskontrolelementer til skyapps

Microsoft Defender for Cloud Apps fungerer som en omvendt proxy, hvilket giver proxyadgang til godkendt skyapps. Denne klargøring giver Defender til skyapps mulighed for at anvende sessionskontrolelementer, som du konfigurerer. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps – adgangssession for proxy" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

I denne illustration:
- Adgang til tilladte skyapps fra brugere og enheder i din organisation dirigeres gennem Defender til skyapps.
- Denne proxyadgang gør det muligt at anvende sessionskontrolelementer.
- Skyapps, som du ikke har tilladt eller udtrykkeligt ikke-godkendt, påvirkes ikke.

Sessionskontrolelementer giver dig mulighed at anvende parametre for, hvordan skyapps bruges af din organisation. Hvis din organisation f.eks. bruger Salesforce, kan du konfigurere en sessionspolitik, der kun tillader administrerede enheder at få adgang til din organisations data hos Salesforce. Et enklere eksempel kunne være at konfigurere en politik til at overvåge trafik fra enheder, der ikke er administrerede, så du kan analysere risikoen for denne trafik, før du anvender mere restriktive politikker.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>Integration med Azure AD med betinget adgang til appkontrol

Du har måske allerede SaaS-apps føjet til din Azure AD-lejer for at gennemtvinge multifaktorgodkendelse og andre politikker for betinget adgang. Microsoft Defender for Cloud Apps integreret med Azure AD. Det eneste, du skal gøre, er at konfigurere en politik i Azure AD til at bruge Betinget adgang-appkontrol i Defender til skyapps. Dette ruter netværkstrafik for disse administrerede SaaS-apps via Defender til skyapps som en proxy, hvilket giver Defender til skyapps mulighed for at overvåge denne trafik og anvende sessionskontrolelementer. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="Arkitekturen for Microsoft Defender for Cloud Apps - SaaS-apps" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

I denne illustration:
- SaaS-apps er integreret med Azure AD-lejeren. Denne integration gør det muligt for Azure AD at gennemtvinge betingede adgangspolitikker, herunder multifaktorgodkendelse.
- En politik føjes til Azure Active Directory til direkte trafik til SaaS-apps til Defender til skyapps. Politikken angiver, hvilke SaaS-apps denne politik skal anvendes på. Når Azure AD gennemtvinger eventuelle politikker for betinget adgang, der gælder for disse SaaS-apps, dirigerer Azure AD derefter (proxyer) sessionstrafik via Defender til skyapps.
- Defender til skyapps overvåger denne trafik og anvender alle politikker for sessionsstyring, der er konfigureret af administratorer. 

Du har muligvis opdaget og tilladte skyapps ved hjælp af Defender til skyapps, der ikke er blevet føjet til Azure AD. Du kan drage fordel af Betinget adgang-appkontrol ved at føje disse skyapps til din Azure AD-lejer og omfanget af dine regler for betinget adgang.

#### <a name="protecting-your-organization-from-hackers"></a>Beskyttelse af din organisation mod hackere

Defender til skyapps giver selv effektiv beskyttelse. Men når det kombineres med de andre funktioner i Microsoft 365 Defender, leverer Defender til skyapps data i de delte signaler, som (sammen) hjælper med at stoppe angreb.

Det er værd at gentage denne illustration fra oversigten til denne Microsoft 365 Defender evaluerings- og pilotvejledning. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="Sådan Microsoft 365 Defender en kæde af trusler" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

Fokuserer på højre side af denne illustration, bemærker Microsoft Defender for Cloud Apps unormal adfærd som umulig rejse, adgang til legitimationsoplysninger og usædvanlig download, fildeling eller videresendelse af mail og rapporterer disse funktionsmåder til sikkerhedsteamet. Derfor hjælper Defender til skyapps med at forhindre lateral bevægelse af hackere og udfyldning af følsomme data. Microsoft 356 Defender til cloud korrelerer signaler fra alle komponenter for at levere den fulde angrebshistorie.

## <a name="understand-key-concepts"></a>Forstå nøglekoncepter

I følgende tabel identificeres nøglekoncepter, som er vigtige at forstå, når evaluering, konfiguration og implementering af Microsoft Defender for Cloud Apps.


|Koncept  |Beskrivelse |Flere oplysninger  |
|---------|---------|---------|
| Dashboard for Defender til skyapps | Giver en oversigt over de vigtigste oplysninger om din organisation og giver links til en dybere undersøgelse.        | [Arbejde med dashboardet ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| Betinget adgang til appkontrol    | Omvendt proxyarkitektur, der integreres med din identitetsudbyder for at give politikker for betinget adgang til Azure AD og selektivt gennemtvinge sessionskontrolelementer.        |  [Beskyt apps med Microsoft Defender for Cloud Apps Access-appkontrol](/cloud-app-security/proxy-intro-aad)       |
|  Appkatalog i skyen   | Cloud App-kataloget giver dig et fuldt billede af Microsoft-katalog med mere end 16.000 skyapps, der er rangeret og scored baseret på mere end 80 risikofaktorer.    |  [Arbejde med app-risikoresultater](/cloud-app-security/risk-score)       |
| Cloud Discovery-dashboard    | Cloud Discovery analyserer dine trafiklogfiler og er designet til at give mere indsigt i, hvordan skyapps bruges i din organisation, samt give beskeder og risikoniveauer.     |  [Arbejde med fundne apps   ](/cloud-app-security/discovered-apps)    |
|Forbundne apps |Defender til skyapps giver en ende-til-ende-beskyttelse til tilknyttede apps ved hjælp af sky-til-sky-integration, API-forbindelser og adgangskontrolelementer i realtid og sessionskontrolelementer ved hjælp af vores betingede adgangskontrolelementer til apps. |[Beskyttelse af forbundne apps](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>Gennemgå arkitekturkrav

### <a name="discovering-cloud-apps"></a>Opdage skyapps

Hvis du vil finde skyapps, der bruges i dit miljø, kan du implementere en eller begge af følgende metoder:

- Kom hurtigt i gang med Cloud Discovery ved at integrere med Microsoft Defender for Endpoint. Denne oprindelige integration giver dig mulighed for straks at begynde at indsamle data på skytrafik på tværs Windows 11 og Windows 10-enheder, på og fra dit netværk.
- Hvis du vil finde alle skyapps, der tilgås af alle enheder, der har forbindelse til dit netværk, skal du installere Logindsamler til Defender for Cloud Apps på dine firewalls og andre proxyer. Denne installation hjælper med at indsamle data fra dine slutpunkter og sender dem til Defender til skyapps til analyse. Defender til skyapps integreres oprindeligt med nogle tredjeparts-proxyer for at få endnu flere egenskaber.

Disse indstillinger er inkluderet [i trin 2. Aktivér evalueringsmiljøet](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>Anvendelse af Politikker for betinget adgang i Azure AD til skyapps

Betinget adgang til appkontrol (muligheden for at anvende Betinget adgang-politikker på skyapps) kræver integration med Azure AD. Denne integration er ikke et krav for at komme i gang med Defender til skyapps. Det er et trin, vi opfordrer dig til at prøve i pilotfasen – [trin 3. Pilot Microsoft Defender for Cloud Apps](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>SIEM-integration

Du kan integrere Microsoft Defender for Cloud Apps med din generiske SIEM-server eller med Microsoft Sentinel for at aktivere centraliseret overvågning af beskeder og aktiviteter fra tilknyttede apps. 

Desuden indeholder Microsoft Sentinel en Microsoft Defender for Cloud Apps forbindelse, som kan sikre en dybere integration med Microsoft Sentinel. Med dette arrangement kan du både få indsigt i dine skyapps, men også få avancerede analyser til at identificere og bekæmpe cybertrusler og styre, hvordan dine data bevæger sig.

- [Generisk SIEM-integration](/cloud-app-security/siem)
- [Stream beskeder og skyregistreringslogfiler fra Defender for Cloud Apps til Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>Næste trin

Trin 2 af 3: [Aktivér evalueringsmiljøet for Microsoft Defender for Cloud Apps](eval-defender-mcas-enable-eval.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md)
