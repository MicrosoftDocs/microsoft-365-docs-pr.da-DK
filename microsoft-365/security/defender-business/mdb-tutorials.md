---
title: Selvstudier og simuleringer i Microsoft Defender til virksomheder
description: Få mere at vide om flere selvstudier, der kan hjælpe dig med at komme i gang med at bruge Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 42d7acb4512928a32ac99c486a231d7891102208
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861328"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Selvstudier og simuleringer i Microsoft Defender til virksomheder

> [!IMPORTANT]
> Microsoft Defender til virksomheder fås nu som prøveversion og udrulles gradvist til kunder og [it-partnere, der tilmelder sig her](https://aka.ms/mdb-preview) for at anmode om det. Vi onboarder et indledende sæt af kunder og partnere i de kommende uger og udvider prøveversionen, så den bliver offentligt tilgængelig. Bemærk, at prøveversionen startes med et [indledende sæt scenarier](#try-these-preview-scenarios), og vi tilføjer jævnligt funktioner.
> 
> Nogle oplysninger i denne artikel er relateret til forhåndsudgivne produkter/tjenester, der kan blive ændret væsentligt, før de udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, for de oplysninger, der er angivet her. 

Hvis du lige er færdig med at konfigurere Microsoft Defender til virksomheder, undrer du dig måske over, hvor du skal begynde at få mere at vide om, hvordan Defender for Business fungerer. I denne artikel beskrives de prøveversionsscenarier, du kan prøve, og flere selvstudier og simuleringer, der er tilgængelige for Defender for Business. Disse ressourcer er designet til at hjælpe dig med at se, hvordan Defender for Business kan fungere for din virksomhed.

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="try-these-preview-scenarios"></a>Prøv disse prøveversionsscenarier

I følgende tabel opsummeres flere scenarier, som du kan prøve med Defender for Business:

| Scenario  | Beskrivelse  |
|---------|---------|
| Onboarde enheder ved hjælp af et lokalt script <br/>(*ikke til produktionsinstallation*)     | I Defender for Business kan du onboarde op til ti Windows 10 og 11 enheder ved hjælp af et script, som du downloader og kører på hver enhed. Scriptet er velegnet til evaluering af, hvordan Defender for Business fungerer i dit miljø, og scriptet opretter et tillidsforhold til Azure Active Directory (Azure AD) og tilmelder enheden med Microsoft Intune. Du kan få mere at vide under [Onboard enheder for at Microsoft Defender til virksomheder](mdb-onboard-devices.md).         |
| Onboarde enheder ved hjælp af Microsoft Intune     | Hvis du allerede brugte Microsoft Intune, før du fik Defender for Endpoint, kan du fortsætte med at bruge Microsoft Intune til at onboarde enheder. Prøv at onboarde macOS-, iOS- og Android-enheder med Microsoft Intune. Du kan få mere at vide under [Tilmelding af enhed i Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Rediger sikkerhedspolitikker     | Hvis du administrerer dine sikkerhedspolitikker i Defender for Business, skal du bruge siden **Enhedskonfiguration** til at få vist og redigere dine politikker. Du kan få mere at vide under [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md).        |
| Udfør et simuleret angreb   | Flere selvstudier og simuleringer er tilgængelige i Defender for Business. Disse selvstudier og simuleringer er designet til at vise dig, hvordan trusselsbeskyttelsesfunktionerne i Defender for Business kan fungere for din virksomhed. Hvis du vil prøve et eller flere af selvstudierne, skal du se [Anbefalede selvstudier til Microsoft Defender til virksomheder](#recommended-tutorials-for-defender-for-business).         |
| Vis hændelser i Microsoft 365 Fyrtårn     | Hvis du er [Microsoft Cloud Solution Provider](/partner-center/enrolling-in-the-csp-program) ved hjælp af Microsoft 365 Lighthouse, kan du snart få vist hændelser på tværs af dine kunders lejere på din Microsoft 365 Lighthouse-portal. Du kan få mere at vide [under Microsoft 365 Lighthouse og Microsoft Defender til virksomheder](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Anbefalede selvstudier til Defender for Business

I følgende tabel beskrives de anbefalede selvstudier til Defender for Business-kunder:

| Tutorial  | Beskrivelse  |
|---------|---------|
| **Dokumentet falder bagdør**     | Simuler et angreb, der introducerer filbaseret malware på en testenhed. I selvstudiet beskrives det, hvordan du henter og bruger simuleringsfilen, og hvad du skal holde øje med i Microsoft 365 Defender-portalen. <br/><br/>Dette selvstudium kræver, at Microsoft Word installeres på din testenhed.   |
| **Live Response-selvstudium**     | Få mere at vide om, hvordan du bruger grundlæggende og avancerede kommandoer med Live Response. Få mere at vide om, hvordan du finder en mistænkelig fil, afhjælper filen og indsamler oplysninger på en enhed.   |
| **Administration af sårbarheder i forbindelse med trussel & (kernescenarier)**     | Få mere at vide om Håndtering af trusler og sikkerhedsrisici via tre scenarier: <br/><br/>1. Reducer din virksomheds trussel og sårbarhedseksponering. <br/>2. Anmod om afhjælpning. <br/>3. Opret en undtagelse for sikkerhedsanbefalinger. <br/><br/> Threat og håndtering af sikkerhedsrisici bruger en risikobaseret tilgang til registrering, prioritering og afhjælpning af sårbarheder og fejlkonfigurationer af slutpunkter.      |

Hvert selvstudium indeholder et gennemgangsdokument, der forklarer scenariet, hvordan det fungerer, og hvad du skal gøre.

> [!TIP]
> Du kan se referencer til Microsoft Defender for Endpoint i gennemgangsdokumenterne. De selvstudier, der er angivet i denne artikel, kan bruges med enten Defender for Endpoint eller Defender for Business.

## <a name="how-to-access-the-tutorials"></a>Sådan får du adgang til selvstudierne

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Selvstudier** under **Slutpunkter** i navigationsruden.

3. Vælg et af følgende selvstudier:

   - **Dokumentet falder bagdør**
   - **Live Response-selvstudium**
   - **Administration af sårbarheder i forbindelse med trussel & (kernescenarier)**

## <a name="next-steps"></a>Næste trin

- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)