---
title: Trin 1. Konfigurere grundlinjer for sikkerhed
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: ransomware, ransomware drevet af mennesker, ransomware drevet af mennesker, HumOR, extortionsangreb, ransomware-angreb, kryptering, cryptovirologi, nultillids
description: Brug grundlinjer med sikkerhed til at beskytte dine Microsoft 365 mod ransomware-angreb.
ms.openlocfilehash: 22092994765e9015421c21f2ee057c63463d594d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598493"
---
# <a name="step-1-configure-security-baselines"></a>Trin 1. Konfigurere grundlinjer for sikkerhed

Som det første trin til at forhindre ransomware-hackere skal du konfigurere følgende Microsoft-definerede sikkerhedsscenarier:

- [Microsoft 365 sikkerhed](#microsoft-365-security-baseline)
- [Exchange af mail](#exchange-email-management-baseline)
- [Yderligere grundlinjer for Windows-enheder og klientsoftware](#additional-baselines)

Disse grundlinjer indeholder konfigurationsindstillinger og regler, som er kendt af hackere, og hvis fravær hurtigt opdages og udnyttes ofte.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 grundlinje over sikkerhed

Først skal du vurdere og måle din sikkerhedsstilling ved hjælp [af Microsoft Secure Score og](/microsoft-365/security/defender/microsoft-secure-score) følge vejledningen for at forbedre den efter behov.

Dernæst skal du bruge [regler for reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) til at blokere mistænkelig aktivitet og sårbar indhold. Disse regler omfatter at forhindre:

- Alle Office programmer fra oprettelse af underordnede processer
- Eksekverbart indhold fra mailklient og webmail
- Eksekverbare filer fra at køre, medmindre de opfylder et alders- eller pålidelige listekriterium
- Udførelse af potentielt slørede scripts
- JavaScript eller VBScript fra at starte hentet eksekverbart indhold
- Office programmer ved oprettelse af eksekverbart indhold
- Office programmer fra indsætte kode i andre processer
- Office af oprettelse af børneprocesser
- Upålidelige og usignerede processer, der kører fra USB
- Vedholdenhed gennem Windows WMI -hændelsesabonnement (Management Interface)
- Legitimationstyveri fra Windows det lokale sikkerhedscenter (lsass.exe)
- Procesoprettelser, der stammer fra PSExec- og WMI-kommandoer

## <a name="exchange-email-management-baseline"></a>Exchange oprindelig plan for administration af mail 

Hjælp med at forhindre indledende adgang til din lejer fra et mailbaseret angreb med disse Exchange oprindelige indstillinger for mail:

- [Aktivér Microsoft Defender Antivirus scanning af mails](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- Brug Microsoft Defender til Office 365 beskyttelse [mod phishing](/microsoft-365/security/office-365-security/anti-phishing-protection) og dækning mod nye trusler og polymorphicvarianter.
- Kontrollér dine Office 365 for mailfiltrering for at sikre, at du blokerer falske mails, spam og mails med malware. Brug Defender til Office 365 for forbedret beskyttelse mod phishing og dækning mod nye trusler og polymorphicvarianter. Konfigurer Defender for Office 365 at kontrollere links igen, når du [klikker](/microsoft-365/security/office-365-security/atp-safe-links) på og [sletter sendte mails](/microsoft-365/security/office-365-security/zero-hour-auto-purge) som svar på nyligt erhvervet trusselsintelligens.
- Gennemse og opdater de  [senesteankomprimerede indstillinger for EOP og Defender for Office 365 sikkerhed](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp).
- Konfigurer Defender for Office 365 at kontrollere [links igen](/microsoft-365/security/office-365-security/set-up-safe-links-policies), når du klikker på og sletter sendte mails som svar på nyligt erhvervet trusselsintelligens.

## <a name="additional-baselines"></a>Yderligere oprindelige planer

Anvend [grundlinjer for sikkerheden](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) for:

- Microsoft Windows 11 eller 10
- Microsoft 365 Apps til store virksomheder
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og administration af ændringer

Som en bedste fremgangsmåde for en reduktionsregel for angrebsoverfladen skal du vurdere, hvordan en regel kan påvirke dit netværk ved at åbne sikkerhedsanbefalingen for den pågældende regel Håndtering af trusler og sikkerhedsrisici. Detaljeruden til anbefaling beskriver brugerpåvirkningen, som du kan bruge til at bestemme, hvilken procentdel af dine enheder, der kan acceptere en ny politik, der aktiverer reglen i blokeringstilstand uden at påvirke brugernes produktivitet negativt.

Desuden kan Exchange oprindelige indstillinger for mail blokere indgående mail og forhindre afsendelse af mail eller klik på links i mail. Underdan dine medarbejdere denne adfærd og årsagen til, at disse forholdsregler bliver taget.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er beskyttelse mod ransomware for din lejer efter dette trin.

![Beskyttelse mod ransomware for din Microsoft 365 lejer efter trin 1](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)


## <a name="next-step"></a>Næste trin

[![Trin 2 for ransomware-beskyttelse med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

Fortsæt med [trin 2](ransomware-protection-microsoft-365-attack-detection-response.md) for at implementere registrering af angreb og svarfunktioner for din Microsoft 365 lejer.
