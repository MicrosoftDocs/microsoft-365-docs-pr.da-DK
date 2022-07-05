---
title: Microsoft Secure Score
description: Beskriver Microsoft Secure Score på Microsoft 365 Defender-portalen, hvordan du forbedrer din sikkerhedsholdning, og hvad sikkerhedsadministratorer kan forvente.
keywords: microsoft secure score, secure score, office 365 secure score, microsoft security score, Microsoft 365 Defender portal, forbedringshandlinger
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- Adm_TOC
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 33e4ae46c6ec75d615cf64efe93d7b5bd8a77905
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66616971"
---
# <a name="microsoft-secure-score"></a>Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure Score er en måling af en organisations sikkerhedsholdning, hvor et højere antal angiver, at der er foretaget flere forbedringshandlinger. Du kan finde den på https://security.microsoft.com/securescore [Microsoft 365 Defender-portalen](microsoft-365-defender-portal.md).

Hvis du følger secure score-anbefalingerne, kan det beskytte din organisation mod trusler. Organisationer kan overvåge og arbejde med sikkerheden af deres Microsoft 365-identiteter, apps og enheder fra et centraliseret dashboard på Microsoft 365 Defender portalen.

Secure Score hjælper organisationer med at:  

* Rapportér om den aktuelle tilstand af organisationens sikkerhedsholdning.
* Forbedre deres sikkerhedsholdning ved at levere registrering, synlighed, vejledning og kontrol.  
* Sammenlign med benchmarks, og fastlæg KPI'er (key performance indicators).

Se denne video for at få et hurtigt overblik over Sikker score.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWUPrP]

Organisationer får adgang til robuste visualiseringer af målepunkter og tendenser, integration med andre Microsoft-produkter, sammenligning af resultater med lignende organisationer og meget mere. Scoren kan også afspejle, når tredjepartsløsninger har håndteret anbefalede handlinger.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="Startsiden for Microsoft Secure Score på Microsoft 365 Defender-portalen" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="how-it-works"></a>Sådan fungerer det

Du får point for følgende handlinger:

- Konfiguration af anbefalede sikkerhedsfunktioner
- Udfører sikkerhedsrelaterede opgaver
- Løsning af forbedringshandlingen med et tredjepartsprogram eller en software eller en alternativ afhjælpning

Nogle forbedringshandlinger giver kun point, når de er fuldført. Nogle giver delvise punkter, hvis de er fuldført for nogle enheder eller brugere. Hvis du ikke kan eller ikke vil gennemføre en af forbedringshandlingerne, kan du vælge at acceptere risikoen eller den resterende risiko.

Hvis du har en licens til et af de understøttede Microsoft-produkter, får du vist anbefalinger til disse produkter. Vi viser dig det fulde sæt af mulige forbedringer for et produkt, uanset licensversion, abonnement eller plan. På denne måde kan du forstå bedste praksis for sikkerhed og forbedre din score. Din absolutte sikkerhedsholdning, repræsenteret ved Secure Score, forbliver den samme, uanset hvilke licenser din organisation ejer for et bestemt produkt. Vær opmærksom på, at sikkerheden skal afbalanceres med anvendelighed, og det er ikke alle anbefalinger, der kan fungere for dit miljø.

Din score opdateres i realtid for at afspejle de oplysninger, der vises på siderne med visualiseringer og forbedringer. Secure Score synkroniseres også dagligt for at modtage systemdata om dine opnåede point for hver handling.

### <a name="key-scenarios"></a>Vigtige scenarier

- [Kontrollér din aktuelle score](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Sammenlign din score med organisationer som din](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Få vist forbedringshandlinger, og beslut en handlingsplan](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Start arbejdsflow for at undersøge eller implementere](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Sådan scores forbedringshandlinger

Hver forbedringshandling er 10 point eller mindre værd, og de fleste scores binært. Hvis du implementerer forbedringshandlingen, f.eks. opretter en ny politik eller aktiverer en bestemt indstilling, får du 100 % af punkterne. I forbindelse med andre forbedringshandlinger angives punkter som en procentdel af den samlede konfiguration.

En forbedringshandling angiver f.eks., at du får 10 punkter ved at beskytte alle dine brugere med multifaktorgodkendelse. Du har kun 50 af 100 brugere i alt beskyttet, så du får en delvis score på 5 point (50 beskyttet / 100 i alt * maks. 10 pkt. = 5 pkt.).

### <a name="products-included-in-secure-score"></a>Produkter, der er inkluderet i Secure Score

Der er i øjeblikket anbefalinger til følgende produkter:

- Microsoft 365 (herunder Exchange Online)
- Azure Active Directory
- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Defender for Cloud Apps
- Microsoft Teams

Anbefalinger til andre sikkerhedsprodukter kommer snart. Anbefalingerne dækker ikke alle de angrebsoverflader, der er knyttet til hvert produkt, men de er en god baseline. Du kan også markere forbedringshandlingerne som dækket af en tredjepart eller en alternativ afhjælpning.

### <a name="security-defaults"></a>Sikkerhedsstandarder

Microsoft Secure Score har opdaterede [forbedringshandlinger, der understøtter sikkerhedsstandarder i Azure Active Directory](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), hvilket gør det nemmere at beskytte din organisation med forudkonfigurerede sikkerhedsindstillinger for almindelige angreb.

Hvis du slår sikkerhedsstandarder til, får du tildelt komplette point for følgende forbedringshandlinger:

- Sørg for, at alle brugere kan fuldføre multifaktorgodkendelse for sikker adgang (9 punkter)
- Kræv MFA for administrative roller (10 point)
- Aktivér politik for at blokere ældre godkendelse (7 punkter)

>[!IMPORTANT]
>Sikkerhedsstandarder omfatter sikkerhedsfunktioner, der giver samme sikkerhed som forbedringshandlinger for "logonrisikopolitik" og "politik for brugerrisiko". I stedet for at konfigurere disse politikker oven på sikkerhedsstandarderne anbefaler vi, at du opdaterer deres status til "Løst via alternativ afhjælpning".

## <a name="required-permissions"></a>Påkrævede tilladelser

Hvis du vil have tilladelse til at få adgang til Microsoft Secure Score, skal du være tildelt en af følgende roller i Azure Active Directory.

### <a name="read-and-write-roles"></a>Læse- og skriveroller

Med læse- og skriveadgang kan du foretage ændringer og interagere direkte med Secure Score. Du kan også tildele skrivebeskyttet adgang til andre brugere.

* Global administrator
* Sikkerhedsadministrator
* Exchange-administrator
* SharePoint-administrator

### <a name="read-only-roles"></a>Skrivebeskyttede roller

Med skrivebeskyttet adgang kan du ikke redigere status eller noter for en forbedringshandling, redigere scorezoner eller redigere brugerdefinerede sammenligninger.

* Helpdesk-administrator
* Brugeradministrator
* Tjenestesupportadministrator
* Sikkerhedslæser
* Sikkerhedsoperator
* Global læser

## <a name="risk-awareness"></a>Risikobevidsthed

Microsoft Secure Score er en numerisk oversigt over din sikkerhedsholdning baseret på systemkonfigurationer, brugeradfærd og andre sikkerhedsrelaterede målinger. Det er ikke en absolut måling af, hvor sandsynligt dit system eller dine data vil blive overtrådt. Det repræsenterer i stedet det omfang, du har indført sikkerhedskontroller i dit Microsoft-miljø, som kan hjælpe med at opveje risikoen for brud på sikkerheden. Ingen onlinetjeneste er immun over for sikkerhedsbrud, og sikker score bør ikke fortolkes som en garanti mod sikkerhedsbrud på nogen måde.

## <a name="we-want-to-hear-from-you"></a>Vi vil gerne høre fra dig

Hvis du har problemer, kan du fortælle os det ved at slå op i community'et [Sikkerhed, Beskyttelse af personlige oplysninger & Overholdelse.](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) Vi overvåger community'et og yder hjælp.

## <a name="related-resources"></a>Relaterede ressourcer

- [Vurder dit sikkerhedsniveau](microsoft-secure-score-improvement-actions.md)
- [Spor din Microsoft Secure Score-historik, og opdr. mål](microsoft-secure-score-history-metrics-trends.md)
- [Hvad kommer der](microsoft-secure-score-whats-coming.md)
- [Nyheder](microsoft-secure-score-whats-new.md)
