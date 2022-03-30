---
title: Trin 2. Udrul registrering af angreb og svar
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
description: Brug Microsoft 365 Defender og dens sikkerhedssignalkilder til at beskytte dine Microsoft 365 mod ransomware-angreb.
ms.openlocfilehash: bf365693505b658dc61ab349c86541cfb9543de9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598491"
---
# <a name="step-2-deploy-attack-detection-and-response"></a>Trin 2. Udrul registrering af angreb og svar

Som et kraftigt anbefalet indledende trin til registrering af ransomware-angreb og svar i din Microsoft 365-lejer [skal du](/microsoft-365/security/defender/eval-overview) konfigurere et prøvemiljø til at evaluere funktionerne og egenskaberne for Microsoft 365 Defender.

Du kan finde flere oplysninger i disse ressourcer.

| Funktion | Beskrivelse | Her kan du starte | Sådan bruges den til registrering og svar |
|:-------|:-----|:-------|:-------|
| [Microsoft 365 Defender](/microsoft-365/security/defender) | Kombinerer signaler og signalmuligheder til en enkelt løsning. <br><br> Gør det muligt for sikkerhedsmedarbejdere at samle trusselssignaler og fastslå det fulde omfang og den fulde virkning af en trussel. <br><br> Automatiserer handlinger til at forhindre eller stoppe angreb og selv samme postkasser, slutpunkter og brugeridentiteter. | [Introduktion](/microsoft-365/security/defender/get-started) | [Hændelsessvar](/microsoft-365/security/defender/incidents-overview) |
| [Microsoft Defender for Identity](/defender-for-identity/what-is) |  Identificerer, registrerer og undersøger avancerede trusler, kompromitterede identiteter og skadelige Insider-handlinger, der er rettet mod din organisation via en skybaseret sikkerhedsgrænseflade, bruger dine lokale Active Directory-domæneservices (AD DS)-signaler. | [Oversigt](/defender-for-identity/what-is) | [Arbejde med Microsoft Defender for Identity-portalen](/defender-for-identity/workspace-portal) |
| [Microsoft Defender til Office 365](/microsoft-365/security/office-365-security) | Beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. <br><br> Beskytter mod malware, phishing, spoofing og andre typer angreb. | [Oversigt](/microsoft-365/security/office-365-security/overview) | [Trusselssøgning](/microsoft-365/security/office-365-security/threat-hunting-in-threat-explorer) |
| [Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint) | Aktiverer registrering og svar på avancerede trusler på tværs af slutpunkter (enheder). | [Oversigt](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)  | [Registrering af slutpunkt og svar](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) |
| [Azure Active Directory (Azure AD) Identity Protection](/azure/active-directory/identity-protection/) | Dette automatiserer registrering og afhjælpning af identitetsbaserede risici og undersøgelse af disse risici. | [Oversigt](/azure/active-directory/identity-protection/overview-identity-protection) | [Undersøg risikoen](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk) |
| [Microsoft Defender til skyapps](/cloud-app-security) | En sikkerhedsmægler til skyadgang til opdagelse, undersøgelse og styring på tværs af alle dine Microsoft- og tredjepartsskytjenester. | [Oversigt](/cloud-app-security/what-is-cloud-app-security) | [Undersøg](/cloud-app-security/investigate) |

>[!Note]
>Alle disse tjenester kræver Microsoft 365 E5 eller Microsoft 365 E3 sammen med Microsoft 365 E5 Sikkerhed-tilføjelsesprogrammet.
>

Brug disse tjenester til at registrere og reagere på følgende almindelige trusler fra ransomware hackere:

- Tyveri af legitimationsoplysninger

   - Azure AD Identity Protection
   - Defender for Identity
   - Defender til Office 365

- Kompromis af enhed

   - Defender til Slutpunkt
   - Defender til Office 365

- Eskalering af rettigheder

   - Azure AD Identity Protection
   - Defender til skyapps

- Ondsindet appfunktionsmåde

   - Defender til skyapps

- Dataudfyldning, sletning eller overførsel

   - Defender til Office 365
   - Defender til skyapps [med politikker til registrering af anorm](/cloud-app-security/anomaly-detection-policy#ransomware-activity)

Følgende tjenester bruger Microsoft 365 Defender dens portal (https://security.microsoft.com)som et almindeligt trusselssamlings- og analysepunkt:

- Defender for Identity
- Defender til Office 365
- Defender til Slutpunkt
- Defender til skyapps

Microsoft 365 Defender kombinerer trusselssignaler i beskeder og tilknyttede beskeder til en hændelse, så dine sikkerhedsanalytikere hurtigere kan finde, undersøge og afhjælpe faserne i en ransomware-angreb.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er beskyttelse mod ransomware for din lejer for trin 1 og 2.

![Beskyttelse mod ransomware for din Microsoft 365 lejer efter trin 2](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step2.png)

## <a name="next-step"></a>Næste trin

[![Trin 3 for beskyttelse mod ransomware med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step3.png)](ransomware-protection-microsoft-365-identities.md)

Fortsæt med [trin 3](ransomware-protection-microsoft-365-identities.md) for at beskytte identiteter i din Microsoft 365 lejer.
