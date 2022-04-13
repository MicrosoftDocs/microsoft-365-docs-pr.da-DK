---
title: Trin 1. Konfigurer grundlæggende sikkerhedsoplysninger
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
keywords: ransomware, menneskelig drevet ransomware, menneskelig drevet ransomware, HumOR, extortion attack, ransomware angreb, kryptering, kryptovirologi, nul tillid
description: Brug sikkerhedsbasepunkter til at beskytte dine Microsoft 365 ressourcer mod ransomware-angreb.
ms.openlocfilehash: 925a64e1d7852aeed6f596e99b20dbff8b34d1be
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825096"
---
# <a name="step-1-configure-security-baselines"></a>Trin 1. Konfigurer grundlæggende sikkerhedsoplysninger

Som et første skridt til at imødegå ransomware angribere, skal du konfigurere følgende Microsoft-definerede sikkerhedsbase baselines:

- [Microsoft 365-sikkerhed](#microsoft-365-security-baseline)
- [Exchange mailadministration](#exchange-email-management-baseline)
- [Yderligere grundlinjer for Windows enheder og klientsoftware](#additional-baselines)

Disse grundlinjer indeholder konfigurationsindstillinger og regler, der er velkendte for personer med ondsindede hensigter, hvis fravær opdages hurtigt og ofte udnyttes.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 grundlæggende sikkerhedsplan

Først skal du vurdere og måle din sikkerhedsholdning ved hjælp af [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score) og følge vejledningen for at forbedre den efter behov.

Derefter skal du bruge [regler for reduktion af angrebsoverfladen](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) som en hjælp til at blokere mistænkelig aktivitet og sårbart indhold. Disse regler omfatter forebyggelse af:

- Alle Office programmer fra oprettelse af underordnede processer
- Eksekverbart indhold fra mailklient og webmail
- Eksekverbare filer kører, medmindre de opfylder et prævalens-, alders- eller listekriterium, der er tillid til
- Udførelse af potentielt slørede scripts
- JavaScript eller VBScript fra start af downloadet eksekverbart indhold
- Office programmer fra oprettelse af eksekverbart indhold
- Office programmer fra indsprøjtning af kode i andre processer
- Office kommunikationsprogram fra oprettelse af underordnede processer
- Processer, der ikke er tillid til, og som ikke er signeret, og som kører fra USB
- Fastholdelse via WMI-hændelsesabonnement (Windows Management Interface)
- Legitimationsoplysninger, der stjæles fra delsystemet Windows lokale sikkerhedsmyndighed (lsass.exe)
- Behandl oprettelser, der stammer fra kommandoerne PSExec og WMI

## <a name="exchange-email-management-baseline"></a>Exchange baseline for mailadministration

Hjælp med at forhindre indledende adgang til din lejer fra et mailbaseret angreb med disse Exchange grundlæggende indstillinger for mail:

- Aktivér [Microsoft Defender Antivirus mailscanning](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- Brug Microsoft Defender for Office 365 til [forbedret phishing-beskyttelse](/microsoft-365/security/office-365-security/anti-phishing-protection) og -dækning mod nye trusler og polymorfe varianter.
- Kontrollér dine Office 365 indstillinger for filtrering af mails for at sikre, at du blokerer forfalskede mails, spam og mails med malware. Brug Defender for Office 365 til forbedret phishing-beskyttelse og -dækning mod nye trusler og polymorfe varianter. Konfigurer Defender for Office 365 til at [kontrollere links igen ved klik](/microsoft-365/security/office-365-security/atp-safe-links) og [slet leverede mails](/microsoft-365/security/office-365-security/zero-hour-auto-purge) som svar på nyerhvervede trusselsintelligens.
- Gennemse og opdater de seneste [anbefalede indstillinger for EOP og Defender for Office 365 sikkerhed](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp).
- Konfigurer Defender for Office 365 til at [kontrollere links igen, når du klikker og](/microsoft-365/security/office-365-security/set-up-safe-links-policies) sletter leverede mails som svar på nyerhvervede trusselsintelligens.

## <a name="additional-baselines"></a>Yderligere oprindelige planer

Anvend [sikkerhedsgrundlinjer](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) for:

- Microsoft Windows 11 eller 10
- Microsoft 365 Apps for Enterprise
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og ændringsstyring

Som bedste praksis for en regel for reduktion af angrebsoverfladen skal du vurdere, hvordan en regel kan påvirke dit netværk, ved at åbne sikkerhedsanbefalingerne for den pågældende regel i Håndtering af trusler og sikkerhedsrisici. Ruden med anbefalinger beskriver brugerpåvirkningen, som du kan bruge til at bestemme, hvilken procentdel af dine enheder der kan acceptere en ny politik, der aktiverer reglen i blokeringstilstand, uden at det påvirker brugerproduktiviteten negativt.

Derudover kan Exchange indstillinger for baseline for mail blokere indgående mail og forhindre afsendelse af mail eller klik på links i mail. Oplær dine medarbejdere i denne adfærd og årsagen til, at disse forholdsregler træffes.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er ransomware beskyttelse for din lejer efter dette trin.

![Ransomware-beskyttelse til din Microsoft 365 lejer efter Trin 1](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)

## <a name="next-step"></a>Næste trin

[![Trin 2 til beskyttelse af ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

Fortsæt med [trin 2](ransomware-protection-microsoft-365-attack-detection-response.md) for at installere funktioner til registrering af angreb og svar for din Microsoft 365 lejer.
