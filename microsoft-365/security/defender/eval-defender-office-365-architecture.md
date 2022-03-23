---
title: Gennemse arkitekturkrav og planlægningskoncepter for Microsoft Defender til Office 365
description: Det tekniske diagram for Microsoft Defender til Office 365 i Microsoft 365 Defender hjælper dig med at forstå identiteten i Microsoft 365 før du opbygger dit prøvelaboratorium eller pilotmiljø.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 49acb346be872c870f1ae52024963680e6631363
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63592291"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>Gennemse Microsoft Defender for Office 365 arkitekturkrav og nøglekoncepter


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 1 af 3](eval-defender-office-365-overview.md) i oprettelsen af evalueringsmiljøet for Microsoft Defender til Office 365. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-office-365-overview.md).

Før du aktiverer Defender for Office 365, skal du sørge for, at du forstår arkitekturen og kan opfylde kravene. I denne artikel beskrives arkitekturen, nøglekoncepterne og forudsætningerne for, at Exchange Online-miljøet skal opfylde.

## <a name="understand-the-architecture"></a>Forstå arkitekturen

Følgende diagram illustrerer grundlinjearkitekturen for Microsoft Defender til Office, som kan omfatte en SMTP-gateway fra en tredjepart eller integration i det lokale miljø. Scenarier for hybrid sameksistens (dvs. produktionspostkasser er både lokale og online) kræver mere komplekse konfigurationer og er ikke dækket af denne artikel eller evalueringsvejledning.

![Arkitektur for Microsoft Defender for Office 365.](../../media/defender/m365-defender-office-architecture.png)

I følgende tabel beskrives denne illustration.

|Call-out  |Beskrivelse  |
|---------|---------|
|1     | Værtsserveren for den eksterne afsender udfører typisk et offentligt DNS-opslag for en MX-post, som giver destinationsserveren til videresendelse af meddelelsen.  Denne henvisning kan enten være en Exchange Online (EXO) direkte eller en SMTP-gateway, der er konfigureret til at videresende mod EXO.  |
|2     | Exchange Online Protection forhandler og validerer den indgående forbindelse og undersøger brevhoveder og indhold for at afgøre, hvilke yderligere politikker, mærkning eller behandling er påkrævet.  |
|3     | Exchange Online med Microsoft Defender til Office 365 tilbyde mere avanceret trusselsbeskyttelse, afhjælpning og afhjælpning. |
|4     | En meddelelse, der ikke er skadelig, blokeret eller i karantæne, behandles og leveres til modtageren i EXO, hvor brugerindstillinger relateret til uønsket mail, postkasseregler eller andre indstillinger evalueres og udløses. |
|5     | Integration med Active Directory i det lokale miljø kan aktiveres ved hjælp af Azure AD Forbind til at synkronisere og klargøre mailaktiverede objekter og konti til Azure Active Directory og i sidste ende Exchange Online. |
|6     | Når du integrerer et lokalt miljø, anbefales det på det kraftigste at bruge en Exchange-server til understøttet administration og administration af mailrelaterede attributter, indstillinger og konfigurationer |
|7     | Microsoft Defender til Office 365 deler signaler Microsoft 365 Defender til udvidet registrering og svar (XDR).|

Integration i det lokale miljø er almindeligt, men valgfrit. Hvis dit miljø kun findes i skyen, fungerer denne vejledning også for dig.

## <a name="understand-key-concepts"></a>Forstå nøglekoncepter

I følgende tabel identificeres nøglekoncepter, som er vigtige at forstå, når MDO evalueres, konfigureres og implementeres.


|Koncept  |Beskrivelse |Flere oplysninger  |
|---------|---------|---------|
|Exchange Online Protection      |    Exchange Online Protection (EOP) er den skybaserede filtreringstjeneste, der hjælper med at beskytte din organisation mod spam- og malwaremails. EOP er inkluderet i alle Microsoft 365, som omfatter Exchange Online.     |   [Exchange Online Protection oversigt](../office-365-security/exchange-online-protection-overview.md)      |
|Beskyttelse mod malware     |    Organisationer med postkasser i EXO er automatisk beskyttet mod malware.     |  [Beskyttelse mod malware i EOP](../office-365-security/anti-malware-protection.md)       |
|Beskyttelse mod uønsket post     |   Organisationer med postkasser i EXO er automatisk beskyttet mod uønsket mail og spampolitikker.      |  [Beskyttelse mod spam i EOP](../office-365-security/anti-spam-protection.md)       |
|Beskyttelse mod phishing |  MDO tilbyder mere avanceret beskyttelse mod phishing relateret til phishing, whaling, ransomware og andre ondsindede aktiviteter.   | [Yderligere beskyttelse mod phishing i Microsoft Defender til Office 365](../office-365-security/anti-phishing-protection.md)   |
|Beskyttelse mod spoofing     |   EOP indeholder funktioner, der beskytter din organisation mod forfalskede afsendere.      |   [Beskyttelse mod spoofing i EOP](../office-365-security/anti-spoofing-protection.md)      |
|Pengeskab vedhæftede filer     |   Pengeskab vedhæftede filer giver et ekstra lag af beskyttelse ved at bruge et virtuelt miljø til at kontrollere og "detonere" vedhæftede filer i mails, før de leveres.      |   [Pengeskab vedhæftede filer i Microsoft Defender til Office 365](../office-365-security/safe-attachments.md)      |
|Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams     |    Desuden giver Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams et ekstra lag af beskyttelse til filer, der er blevet overført til skylager.     |  [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)       |
|Sikre links     | Pengeskab Links er en funktion, der giver URL-scanning og -omskrivning i indgående mails og tilbyder godkendelse af disse links, før de leveres eller klikkes på.        |   [Pengeskab Links i Microsoft Defender til Office 365](../office-365-security/safe-links.md)      |
|    |         |         |

Du kan finde flere oplysninger om de funktioner, der følger med Microsoft Defender Office, under [Beskrivelse Office 365 Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="review-architecture-requirements"></a>Gennemgå arkitekturkrav
En vellykket MDO-evaluering eller produktionspilot forudsætter følgende forudsætninger:
- Alle dine modtagerpostkasser befinder sig i øjeblikket i Exchange Online.
- Din offentlige MX-post sendes direkte til EOP eller en TREDJEPARTS SMTP-gateway, som derefter videresender indgående eksterne mails direkte til EOP.
- Dit primære maildomæne er konfigureret *som autoritativt* i Exchange Online.
- Du har installeret og konfigureret *mappebaseret blokering af kanter* (DBEB) efter behov. Du kan få mere at vide [under Brug blokering Directory-Based Edge til at afvise meddelelser, der sendes til ugyldige modtagere](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

> [!IMPORTANT]
> Hvis disse krav ikke er gældende, eller hvis du stadig er i et scenarie med hybrid sameksistens, kan en Microsoft Defender til Office 365-evaluering kræve mere komplekse eller avancerede konfigurationer, som ikke er fuldt dækket af denne vejledning.

## <a name="siem-integration"></a>SIEM-integration

Du kan integrere Microsoft Defender for Office 365 med Microsoft Sentinel for mere omfattende analyse af sikkerhedshændelser på tværs af organisationen og opbygge strategibøger, så du kan få et effektivt og øjeblikkeligt svar. Du kan finde flere [oplysninger Forbind beskeder fra Microsoft Defender for Office 365](/azure/sentinel/connect-office-365-advanced-threat-protection).

Microsoft Defender til Office 365 kan også integreres i andre sikkerhedsoplysninger og løsninger til begivenhedsstyring (SIEM) ved hjælp [Office 365 API'en Aktivitetsstyring](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>Næste trin

Trin 2 af 3: [Aktivér evalueringsmiljøet Microsoft Defender Office 365](eval-defender-office-365-enable-eval.md)

Gå tilbage til oversigten for [Evaluer Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Gå tilbage til oversigten for [Evaluer og Microsoft 365 Defender](eval-overview.md) 
