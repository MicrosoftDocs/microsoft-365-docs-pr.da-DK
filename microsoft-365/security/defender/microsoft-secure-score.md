---
title: Microsoft Secure Score
description: Beskriver Microsoft Secure Score i Microsoft 365 Defender, hvordan du forbedrer din sikkerhedsstilling, og hvad sikkerhedsadministratorer kan forvente.
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
ms.openlocfilehash: d31fa35ddf84b63a115cf3128673794617fcc730
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63592889"
---
# <a name="microsoft-secure-score"></a>Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure Score er en måling af en organisations sikkerhedshold, med et højere tal, der angiver, at der er foretaget flere forbedringshandlinger. Den kan findes på https://security.microsoft.com/securescore [Microsoft 365 Defender-portalen](microsoft-365-defender.md#the-microsoft-365-defender-portal).

Hvis du følger Secure Score-anbefalingerne, kan du beskytte din organisation mod trusler. Fra et centraliseret dashboard i Microsoft 365 Defender kan organisationer overvåge og arbejde på sikkerheden for deres Microsoft 365 identiteter, apps og enheder.

Secure Score hjælper organisationer med at:  

* Rapportér om den aktuelle tilstand af organisationens sikkerhedshold.
* Forbedr deres sikkerhed ved at give synlighed, synlighed, vejledning og kontrol.  
* Sammenlign med benchmarks, og opret KPI'er (Key Performance Indicators).

Watch this video for a quick overview of Secure score.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWUPrP]

Organisationer får adgang til robuste visualiseringer af målepunkter og tendenser, integration med andre Microsoft-produkter, sammenligning af resultater med lignende organisationer og meget mere. Scoren kan også afspejles, når tredjepartsløsninger har behandlet anbefalede handlinger.

![Secure Score-startside.](../../media/secure-score/secure-score-home-page.png)

## <a name="how-it-works"></a>Sådan fungerer det

Du får point for følgende handlinger:

- Konfiguration af anbefalede sikkerhedsfunktioner
- Udføre sikkerhedsrelaterede opgaver
- Løsning af forbedringshandlingen med et program eller en software fra tredjepart eller en alternativ afhjælpning

Nogle forbedringshandlinger giver kun point, når de er fuldført. Nogle giver delvise point, hvis de er fuldført for visse enheder eller brugere. Hvis du ikke kan eller ikke vil udføre en af forbedringshandlingerne, kan du vælge at acceptere risikoen eller den resterende risiko.

Hvis du har en licens til et af de understøttede Microsoft-produkter, får du vist anbefalinger til disse produkter. Vi viser dig det fulde sæt af mulige forbedringer af et produkt, uanset licensversion, abonnement eller plan. På den måde kan du forstå de bedste fremgangsmåder for sikkerhed og forbedre dine resultater. Din absolutte sikkerhedsstilling, der repræsenteres af Secure Score, forbliver den samme, uanset hvilke licenser din organisation ejer til et bestemt produkt. Husk, at sikkerheden skal balanceres med brugervenligheden, og ikke alle anbefalinger kan fungere for dit miljø.

Dine resultater opdateres i realtid for at afspejle de oplysninger, der præsenteres på handlingssiderne for visualiseringer og forbedringer. Secure Score synkroniserer også dagligt for at modtage systemdata om dine opnået point for hver handling.

### <a name="key-scenarios"></a>Vigtige scenarier

- [Kontrollér din aktuelle score](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Sammenlign dine resultater med organisationer som din](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Få vist forbedringshandlinger, og beslut en handlingsplan](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Initier arbejdsflows for at undersøge eller implementere](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Sådan scores forbedringshandlinger

Hver forbedringshandling er 10 point værd eller mindre, og de fleste scores på binær vis. Hvis du implementerer forbedringshandlingen, f.eks. oprette en ny politik eller aktivere en bestemt indstilling, får du 100 % af punkterne. Ved andre forbedringshandlinger, er point angivet som en procentdel af den samlede konfiguration.

En forbedring viser f.eks., at du får 10 point ved at beskytte alle dine brugere med multifaktorgodkendelse. Du har kun 50 af 100 brugere beskyttet i alt, så du får en delvis score på 5 point (50 beskyttet /100 i alt * 10 maks. pts = 5 pkt.).

### <a name="products-included-in-secure-score"></a>Produkter inkluderet i Secure Score

Der er i øjeblikket anbefalinger til følgende produkter:

- Microsoft 365 (herunder Exchange Online)
- Azure Active Directory
- Microsoft Defender til Slutpunkt
- Microsoft Defender for Identity
- Defender til skyapps
- Microsoft Teams

Anbefalinger til andre sikkerhedsprodukter kommer snart. Anbefalingerne dækker ikke alle de angrebsoverflader, der er knyttet til hvert produkt, men de er en god grundlinje. Du kan også markere forbedringshandlingerne som dækket af en tredjepart eller alternativ afhjælpning.

### <a name="security-defaults"></a>Sikkerhedsstandardindstillinger

Microsoft Secure Score har opdateret [forbedringshandlinger](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) for at understøtte sikkerhedsstandardindstillinger i Azure Active Directory, som gør det nemmere at beskytte din organisation med forudkonfigurerede sikkerhedsindstillinger til almindelige angreb.

Hvis du slår sikkerhedsstandardindstillinger til, får du tildelt alle point for følgende forbedringshandlinger:

- Sørg for, at alle brugere kan udføre multifaktorgodkendelse for sikker adgang (9 punkter)
- Kræv MFA for administrative roller (10 point)
- Aktivér politik for at blokere ældre godkendelse (7 punkter)

>[!IMPORTANT]
>Sikkerhedsstandarden omfatter sikkerhedsfunktioner, der giver samme sikkerhed som forbedringshandlingerne "politik for logonrisici" og "politik om brugerrisici". I stedet for at konfigurere disse politikker oven i sikkerhedsstandardindstillingerne anbefaler vi, at deres status opdateres til "Løst via alternativ afhjælpning".

## <a name="required-permissions"></a>Påkrævede tilladelser

Hvis du vil have tilladelse til at få adgang til Microsoft Secure Score, skal du have tildelt en af følgende roller Azure Active Directory.

### <a name="read-and-write-roles"></a>Læse- og skriveroller

Med læse- og skriveadgang kan du foretage ændringer og interagere direkte med Secure Score. Du kan også tildele skrivebeskyttet adgang til andre brugere.

* Global administrator
* Sikkerhedsadministrator
* Exchange administrator
* SharePoint administrator

### <a name="read-only-roles"></a>Skrivebeskyttede roller

Med skrivebeskyttet adgang kan du ikke redigere status eller noter for en forbedringshandling, redigere scorezoner eller redigere brugerdefinerede sammenligninger.

* Helpdesk-administrator
* Brugeradministrator
* Tjenestesupportadministrator
* Sikkerhedslæser
* Sikkerhedsoperatør
* Global læser

## <a name="risk-awareness"></a>Risiko/opmærksomhed

Microsoft Secure Score er en numerisk oversigt over din sikkerhedsovergang baseret på systemkonfigurationer, brugeradfærd og andre sikkerhedsrelaterede målinger. Det er ikke en absolut måling af, hvor sandsynligt dit system eller dine data vil blive brudt. I stedet repræsenterer den det omfang, i hvilket du har indført sikkerhedskontrolelementer i dit Microsoft-miljø, der kan hjælpe med at forskyde risikoen for at blive brudt. Ingen onlinetjeneste er beskyttet mod sikkerhedsbribrider, og sikre scorer bør ikke fortolkes som en garanti mod sikkerhedsbrud på nogen måde.

## <a name="we-want-to-hear-from-you"></a>Vi vil gerne høre fra dig

Hvis du har problemer, kan du fortælle os om det ved at slå et indlæg op i [community'et Sikkerhed, & Privacy Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Vi overvåger communityet og yder hjælp.

## <a name="related-resources"></a>Relaterede ressourcer

- [Vurder din sikkerhedsstilling](microsoft-secure-score-improvement-actions.md)
- [Spor din Microsoft Secure Score-historik, og opfylder mål](microsoft-secure-score-history-metrics-trends.md)
- [Hvad der kommer](microsoft-secure-score-whats-coming.md)
- [Nyheder](microsoft-secure-score-whats-new.md)
