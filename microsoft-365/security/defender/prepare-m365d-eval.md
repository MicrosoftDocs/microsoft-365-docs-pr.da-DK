---
title: Forbered dit Microsoft 365 Defender prøveversionslaboratormiljø
description: Forbered interessenternes logon, tidslinjer, miljøovervejelser og indføringsrækkefølge, når du konfigurerer dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø
keywords: Microsoft 365 Defender prøveabonnement, Microsoft 365 Defender en pilotversion, klar til at køre Microsoft 365 Defender et pilotprojekt, køre et Microsoft 365 Defender  project, deploy, prepare, stakeholder, timeline, environment, endpoint, server, management, adoption
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 7ebb7074b0e06eda96d21142044bd8b9997e094b
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63603155"
---
# <a name="prepare-your-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Forbered dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Oprettelse af Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø, og udrulning af det er en trefaset proces:

|![Fase 1: Forbered](../../media/phase-diagrams/prepare.png)<br/>Fase 1: Forbered |[![Fase 2: Konfigurer](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Fase 2: Konfigurer](setup-m365deval.md) |[![Fase 3: Onboard](../../media/phase-diagrams/onboard.png)](config-m365d-eval.md)<br/>[Fase 3: Onboard](config-m365d-eval.md) | [![Tilbage til pilotprojekt](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Tilbage til pilotspilbog](m365d-pilot.md) |
|--|--|--|--|
|*Du er her!* | || |

Du er i øjeblikket i forberedelsesfasen.


Forberedelse er nøglen til en vellykket installation. Dette afsnit fører dig gennem det, du skal overveje, når du forbereder dig på at oprette et prøvelaboratorium eller pilotmiljø til din Microsoft 365 Defender installation.

## <a name="prerequisites"></a>Forudsætninger
Få mere at vide om licenser, hardware- og softwarekrav og andre konfigurationsindstillinger for at klargøre og bruge Microsoft 365 Defender. Se minimumskravene til [Microsoft 365 Defender](/microsoft-365/security/defender/prerequisites), [Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements), [Microsoft Defender Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description), [Microsoft Defender til identity](/azure-advanced-threat-protection/atp-prerequisites) [Microsoft Cloud App Security](/azure-advanced-threat-protection/atp-prerequisites).

## <a name="stakeholders-and-sign-off"></a>Interessenter og logon
Identificer alle de interessenter, der er involveret i projektet, og som kan være nødt til at logge af, gennemgå eller holde sig opdateret, uanset om de skal evalueres eller køre et pilotprojekt.

>[!NOTE]
>Ikke alle organisationer har måske den pågældende sikkerhedsorganisations udløbsdato for at have sådanne roller. I så fald skal du rådføre dig med dit ledelsesteam vedrørende gennemgang og godkendelse af kontoegenskaber.

Føj interessenter til tabellen nedenfor efter behov for din organisation.

-   SO = Sign-off på dette projekt

-   R = Gennemse dette projekt, og angiv input

-   I = Informeret om dette projekt

| Navn                 | Rolle                                                                                                                                                                                                          | Handling |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|
| Angiv navn og mail | **Chief Information Security Officer (CISO) En** *lederrepræsentant, der fungerer som sponsor i organisationen for udrulningen af den nye teknologi.*                                                  | SO     |
| Angiv navn og mail | **Head of Cyber Defense Operations Center (CDOC) En** repræsentant fra CDOC-teamet, der har ansvaret for at definere, hvordan denne ændring er justeret med processerne i *kundens sikkerhedsteam.*       | SO     |
| Angiv navn og mail | **Sikkerhedsarkitekt** En repræsentant fra sikkerhedsteamet, der har ansvaret for at definere, hvordan denne ændring er *justeret med den grundlæggende sikkerhedsarkitektur i organisationen.*                         | R      |
| Angiv navn og mail | **Workplace Architect** *En repræsentant fra it-teamet, der har* ansvaret for at definere, hvordan denne ændring er justeret med den centrale arkitektur på arbejdspladsen i organisationen.                             | R      |
| Angiv navn og mail | **Sikkerhedsanalytiker** *En repræsentant fra CDOC-teamet*, der kan give feedback om registreringsfunktionerne, brugeroplevelsen og den overordnede anvendelighed af denne ændring set fra et sikkerheds operationsperspektiv. | I      |

## <a name="prepare-your-azure-active-directory"></a>Forbered dine Azure Active Directory
Spring dette trin over, hvis du allerede har aktiveret synkronisering mellem Active Directory Azure Active Directory lokale miljø. Gennemse eksisterende dokumentation om bedste fremgangsmåder fra Azure Active Directory. Følgende trin er optimeret til at evaluere eller køre et Microsoft 365 Defender projekt.

1. Gå til [Azure Active Directory-portalen](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade) > **Azure AD Forbind**. 
![Billede af Azure Active Directory portalside](../../media/mtp-eval-1.png) <br> 

2. Klik **på Download** **Microsoft Azure Active Directory Forbind** og overfør den til domænecontroller.
![Billede af Azure Active Directoru Forbind downloadside](../../media/mtp-eval-2.png) <br>

3. På domænecontrolleren skal du Azure Active Directory Forbind guiden. Læs licensvilkårene og meddelelsen om beskyttelse af personlige oplysninger, og markér afkrydsningsfeltet, hvis du accepterer. Klik på **Fortsæt**.
![Billede af velkomstsiden for Azure AD Forbind Azure AD](../../media/mtp-eval-3.png) <br>

4. Naviger **til Express Indstillinger**.
![Billede af siden hurtig Indstillinger udtryk](../../media/mtp-eval-4.png) <br>

5. Angiv dine globale administratorlegitimationsoplysninger. Klik på **Næste**.
![Billede af Forbind til Azure AD-siden, hvor du skal angive dine globale administratorlegitimationsoplysninger](../../media/mtp-eval-5.png) <br>

6. Angiv dine Active Directory-domæneservices legitimationsoplysninger som virksomhedsadministrator. Klik på **Næste**.
![Billede af Forbind til AD DS side, hvor du skal angive dine legitimationsoplysninger](../../media/mtp-eval-6.png) <br>

7. Klik **på Installér** for at bekræfte konfigurationen.
![Billede af bekræftelsesside for konfiguration](../../media/mtp-eval-7.png) <br>

8. Tillykke, du har konfigureret Azure Active Directory Forbind.
![Billede af en korrekt konfigureret Azure Active Directory Forbind side](../../media/mtp-eval-8.png) <br>

Du kan nu [føje brugere og grupper til Active Directory](/azure-advanced-threat-protection/atp-playbook-setup-lab#bkmk_hydrate) og [konfigurere en SAM-R-politik](/azure-advanced-threat-protection/atp-playbook-setup-lab#configure-sam-r-capabilities-from-contosodc).  


## <a name="configuration-order"></a>Konfigurationsrækkefølge
Følgende tabel angiver den rækkefølge, microsoft anbefaler til konfiguration af de Microsoft 365 Defender komponenter til din prøvelaborator eller din pilotmiljøinstallation.

| Komponent                               | Beskrivelse                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Konfigurationsrækkefølge |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
|Microsoft Defender til Office 365|Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. <br> [Lær mere.](/microsoft-365/security/office-365-security/defender-for-office-365)                                                                                                                                                                                                                                             | 1                   |
|Microsoft Defender for Identity|Microsoft Defender for Identity bruger Active Directory-signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og ondsindede Insider-handlinger rettet mod din organisation. <br> [Få mere at vide](/azure-advanced-threat-protection/).| 2 |
|Microsoft Cloud App Security| Microsoft Cloud App Security er en cloud access-sikkerhedsmægler (CASB), der arbejder på flere skyer. Det giver stor synlighed, kontrol over datarejse og avancerede analyser til at identificere og bekæmpe cybertrusler på tværs af alle dine skytjenester. <br> [Få mere at vide](/cloud-app-security/).                                                                                                                                                                                                                                                                                                                                                                       |3                   |
|Microsoft Defender til Slutpunkt | Egenskaberne for Microsoft Defender slutpunktsregistrering og -svar slutpunkt giver avancerede registreringer af angreb, der er næsten i realtid og kan handles på. Sikkerhedsanalytikere kan prioritere beskeder effektivt, få overblik over det fulde omfang af en overtrædelse og reagere på handlinger for at løse trusler. <br> [Lær mere.](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)                                     |4                   |                                                                                                                                                                                                                                    

## <a name="next-step"></a>Næste trin
|![Fase 2: Konfiguration](../../media/setup.png) <br>[Fase 2: Konfiguration](setup-m365deval.md) | Konfigurer dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø
|:-------|:-----|
