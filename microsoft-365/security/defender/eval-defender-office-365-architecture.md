---
title: Gennemse arkitekturkrav og planlægningskoncepter for Microsoft Defender for Office 365
description: Det tekniske diagram til Microsoft Defender for Office 365 i Microsoft 365 Defender hjælper dig med at forstå identiteten i Microsoft 365, før du bygger dit prøvelaboratorium eller pilotmiljø.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1002b03a0ebb3940d544343476045d52e8209273
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749940"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>Gennemse krav til Microsoft Defender for Office 365 arkitektur og vigtige begreber


**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 1 af 3](eval-defender-office-365-overview.md) i processen med at konfigurere evalueringsmiljøet for Microsoft Defender for Office 365. Du kan få flere oplysninger om denne proces i [oversigtsartiklen](eval-defender-office-365-overview.md).

Før du aktiverer Defender for Office 365, skal du forstå arkitekturen og opfylde kravene. I denne artikel beskrives arkitekturen, nøglebegreberne og de forudsætninger, som dit Exchange Online miljø skal opfylde.

## <a name="understand-the-architecture"></a>Forstå arkitekturen

I følgende diagram illustreres den oprindelige arkitektur for Microsoft Defender for Office, som kan omfatte en SMTP-gateway fra tredjepart eller integration i det lokale miljø. Scenarier med hybride sameksistenser (dvs. produktionspostkasser er både lokalt og online) kræver mere komplekse konfigurationer og er ikke omfattet af denne artikel eller en evalueringsvejledning.

:::image type="content" source="../../media/defender/m365-defender-office-architecture.png" alt-text="Arkitekturen for Microsoft Defender for Office 365" lightbox="../../media/defender/m365-defender-office-architecture.png":::

I følgende tabel beskrives denne illustration.

|Opkald  |Beskrivelse  |
|---------|---------|
|1     | Værtsserveren for den eksterne afsender udfører typisk et offentligt DNS-opslag for en MX-post, som gør det muligt for destinationsserveren at videresende meddelelsen.  Denne henvisning kan enten være Exchange Online (EXO) direkte eller en SMTP-gateway, der er konfigureret til at blive videresendt til EXO.  |
|2     | Exchange Online Protection forhandler og validerer den indgående forbindelse og undersøger brevhovederne og indholdet for at bestemme, hvilke ekstra politikker, mærkning eller behandling der kræves.  |
|3     | Exchange Online kan integreres med Microsoft Defender for Office 365 for at tilbyde mere avanceret trusselsbeskyttelse, afhjælpning og afhjælpning. |
|4     | En meddelelse, der ikke er skadelig, blokeret eller sat i karantæne, behandles og leveres til modtageren i EXO, hvor brugerindstillinger, der er relateret til regler for uønsket mail, postkasseregler eller andre indstillinger, evalueres og udløses. |
|5     | Integration med Active Directory i det lokale miljø kan aktiveres ved hjælp af Azure AD Opret forbindelse for at synkronisere og klargøre mailaktiverede objekter og konti til Azure Active Directory og i sidste ende Exchange Online. |
|6     | Når du integrerer et lokalt miljø, opfordres du til at bruge en Exchange-server til understøttet administration og administration af mailrelaterede attributter, indstillinger og konfigurationer |
|7     | Microsoft Defender for Office 365 deler signaler til Microsoft 365 Defender for udvidet registrering og svar (XDR).|

Integration i det lokale miljø er almindelig, men valgfri. Hvis dit miljø kun er skybaseret, fungerer denne vejledning også for dig.

## <a name="understand-key-concepts"></a>Forstå vigtige begreber

I følgende tabel identificeres vigtige begreber, der er vigtige at forstå, når du evaluerer, konfigurerer og installerer MDO.


|Koncept  |Beskrivelse |Flere oplysninger  |
|---------|---------|---------|
|Exchange Online Protection      |    Exchange Online Protection (EOP) er den skybaserede filtreringstjeneste, der hjælper med at beskytte din organisation mod spam- og malwaremails. EOP er inkluderet i alle Microsoft 365-licenser, der omfatter Exchange Online.     |   [Oversigt over Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)      |
|Beskyttelse mod malware     |    Organisationer med postkasser i EXO beskyttes automatisk mod malware.     |  [Beskyttelse mod skadelig software i EOP](../office-365-security/anti-malware-protection.md)       |
|Beskyttelse mod spam     |   Organisationer med postkasser i EXO beskyttes automatisk mod politikker for uønsket mail og spam.      |  [Beskyttelse mod spam i EOP](../office-365-security/anti-spam-protection.md)       |
|Beskyttelse mod phishing |  MDO tilbyder mere avanceret anti-phishing-beskyttelse relateret til spyd phishing, hvalfangst, ransomware og andre skadelige aktiviteter.   | [Ekstra beskyttelse mod phishing i Microsoft Defender for Office 365](../office-365-security/anti-phishing-protection.md)   |
|Beskyttelse mod forfalskning     |   EOP indeholder funktioner, der hjælper med at beskytte din organisation mod forfalskede (forfalskede) afsendere.      |   [Beskyttelse mod spoofing i EOP](../office-365-security/anti-spoofing-protection.md)      |
|Sikre vedhæftede filer     |   Sikre vedhæftede filer giver et ekstra lag af beskyttelse ved hjælp af et virtuelt miljø til at kontrollere og "detonere" vedhæftede filer i mails, før de leveres.      |   [Sikre vedhæftede filer i Microsoft Defender for Office 365](../office-365-security/safe-attachments.md)      |
|Sikre vedhæftede filer til SharePoint, OneDrive og Microsoft Teams     |    Desuden tilbyder Sikre vedhæftede filer til SharePoint, OneDrive og Microsoft Teams et ekstra lag af beskyttelse af filer, der er uploadet til lagerlagre i skyen.     |  [Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)       |
|Sikre links     | Sikre links er en funktion, der leverer SCANNING og omskrivning af URL-adresser i indgående mails og tilbyder bekræftelse af disse links, før de leveres eller klikkes på.        |   [Sikre links i Microsoft Defender for Office 365](../office-365-security/safe-links.md)      |
|    |         |         |

Du kan finde flere detaljerede oplysninger om de funktioner, der er inkluderet i Microsoft Defender til Office, [i Microsoft Defender for Office 365 tjenestebeskrivelse](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="review-architecture-requirements"></a>Gennemse arkitekturkrav
Et vellykket MDO-evaluerings- eller produktionspilot forudsætter følgende forudsætninger:
- Alle dine modtagerpostkasser er i øjeblikket i Exchange Online.
- Din offentlige MX-post oversættes direkte til EOP eller en SMTP-gateway fra tredjepart, der derefter videresender indgående eksterne mails direkte til EOP.
- Dit primære maildomæne er konfigureret som *autoritativt* i Exchange Online.
- Du har installeret og konfigureret *DBEB (Directory-Based Edge Blocking* ) efter behov. Du kan få flere oplysninger under [Brug Directory-Based Edge Blocking til at afvise meddelelser, der er sendt til ugyldige modtagere](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

> [!IMPORTANT]
> Hvis disse krav ikke er gældende, eller du stadig befinder dig i et hybridt scenarie for sameksistens, kan en Microsoft Defender for Office 365 evaluering kræve mere komplekse eller avancerede konfigurationer, som ikke er fuldt dækket i denne vejledning.

## <a name="siem-integration"></a>SIEM-integration

Du kan integrere Microsoft Defender for Office 365 med Microsoft Sentinel for mere omfattende at analysere sikkerhedshændelser på tværs af din organisation og bygge playbooks, så du kan reagere effektivt og øjeblikkeligt. Du kan få flere oplysninger under [Opret forbindelse til beskeder fra Microsoft Defender for Office 365](/azure/sentinel/connect-office-365-advanced-threat-protection).

Microsoft Defender for Office 365 kan også integreres i andre SIEM-løsninger (Security Information and Event Management) ved hjælp af [API'en Office 365 Activity Management](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>Næste trin

Trin 2 af 3: [Aktivér evalueringsmiljøet Microsoft Defender for Office 365](eval-defender-office-365-enable-eval.md)

Vend tilbage til oversigten for [Evaluate Microsoft Defender for Office 365](eval-defender-office-365-overview.md)

Vend tilbage til oversigten for [Evaluate og pilot Microsoft 365 Defender](eval-overview.md) 
