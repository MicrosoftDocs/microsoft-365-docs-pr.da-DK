---
title: Selvstudier og simuleringer i Microsoft Defender til virksomheder
description: Få mere at vide om flere selvstudier, der kan hjælpe dig med at komme i gang med at bruge Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 029be738b8c916ec4eb16970ae2d2ff3c460f639
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66771968"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Selvstudier og simuleringer i Microsoft Defender til virksomheder

I denne artikel beskrives nogle scenarier, hvor du kan prøve flere selvstudier og simuleringer, der er tilgængelige for Defender for Business. Disse ressourcer viser, hvordan Defender for Business kan fungere for din virksomhed.


## <a name="try-these-scenarios"></a>Prøv disse scenarier

I følgende tabel opsummeres flere scenarier, som du kan prøve med Defender for Business.

| Scenario  | Beskrivelse  |
|---------|---------|
| Onboarde enheder ved hjælp af et lokalt script     | I Defender for Business kan du onboarde Windows- og Mac-enheder ved hjælp af et script, som du downloader og kører på hver enhed. Scriptet opretter et tillidsforhold til Azure Active Directory (Azure AD), hvis dette tillidsforhold ikke allerede findes. Tilmelder enheden Microsoft Intune, hvis du har Intune, og onboarder enheden til Defender for Business. Du kan få mere at vide under [Onboarder enheder til Defender for Business](mdb-onboard-devices.md).         |
| Onboarde enheder ved hjælp af Microsoft Endpoint Manager Administration     | Hvis du allerede brugte Intune, før du fik Defender for Business, kan du fortsætte med at bruge Endpoint Manager Administration til at onboarde enheder. Prøv at onboarde dine Windows-, Mac-, iOS- og Android-enheder med Microsoft Intune. Du kan få mere at vide under [Tilmelding af enhed i Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Rediger sikkerhedspolitikker     | Hvis du administrerer dine sikkerhedspolitikker i Defender for Business, skal du bruge siden **Enhedskonfiguration** til at få vist og redigere dine politikker. Defender for Business leveres med standardpolitikker, der bruger anbefalede indstillinger til at sikre din virksomheds enheder, så snart de er onboardet. Du kan beholde standardpolitikkerne, redigere dem og definere dine egne politikker, så de passer til dine forretningsbehov. Du kan få mere at vide under [Få vist eller rediger politikker i Defender for Business](mdb-view-edit-policies.md).        |
| Kør et simuleret angreb   | Flere selvstudier og simuleringer er tilgængelige i Defender for Business. Disse selvstudier og simuleringer viser, hvordan funktionerne til trusselsbeskyttelse i Defender for Business kan fungere for din virksomhed. Du kan også bruge et simuleret angreb som en træningsøvelse for dit team. Hvis du vil prøve selvstudierne, skal du se [Anbefalede selvstudier til Defender for Business](#recommended-tutorials-for-defender-for-business).         |
| Få vist hændelser i Microsoft 365 Lighthouse     | Hvis du er [Microsoft Cloud Solution Provider](/partner-center/enrolling-in-the-csp-program) ved hjælp af Microsoft 365 Lighthouse, kan du få vist hændelser på tværs af dine kunders lejere på din Microsoft 365 Lighthouse-portal. Du kan få mere at vide under [Microsoft 365 Lighthouse og Defender for Business](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Anbefalede selvstudier til Defender for Business

I følgende tabel beskrives de anbefalede selvstudier til Defender for Business-kunder.

| Tutorial  | Beskrivelse  |
|---------|---------|
| **Dokumentet falder bagdør**     | Simuler et angreb, der introducerer filbaseret malware på en testenhed. I selvstudiet beskrives det, hvordan du bruger simuleringsfilen, og hvad du skal se efter på Microsoft 365 Defender-portalen. <p>Dette selvstudium kræver, at Microsoft Word er installeret på din testenhed.   |
| **Live-svar**     | Få mere at vide om, hvordan du bruger grundlæggende og avancerede kommandoer med Live Response. Få mere at vide om, hvordan du finder en mistænkelig fil, afhjælper filen og indsamler oplysninger på en enhed.   |
| **Administration af sårbarheder i forbindelse med trussel & (kernescenarier)**     | Få mere at vide om Håndtering af trusler og sikkerhedsrisici via tre scenarier:<ol><li>Reducer din virksomheds trussel og sårbarhedseksponering.</li><li>Anmod om en afhjælpning.</li><li>Opret en undtagelse for sikkerhedsanbefalinger.</li></ol> <p> Administration af trussel & sårbarheder bruger en risikobaseret tilgang til registrering, prioritering og afhjælpning af slutpunktssårbarheder og fejlkonfigurationer.      |

Hvert selvstudium indeholder et gennemgangsdokument, der forklarer scenariet, hvordan det fungerer, og hvad du skal gøre.

> [!TIP]
> Du kan se referencer til Microsoft Defender for Endpoint i gennemgangsdokumenterne. De selvstudier, der er angivet i denne artikel, kan bruges med enten Defender for Endpoint eller Defender for Business.

## <a name="how-to-access-the-tutorials"></a>Sådan får du adgang til selvstudierne

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Selvstudier** under **Slutpunkter** i navigationsruden.

3. Vælg et af følgende selvstudier:

   - **Dokumentet falder bagdør**
   - **Live-svar**
   - **Administration af sårbarheder i forbindelse med trussel & (kernescenarier)**

## <a name="next-steps"></a>Næste trin

- [Administrer enheder i Defender for Business](mdb-manage-devices.md)
- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Reager på og afhjælp trusler i Defender for Business](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)