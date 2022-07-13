---
title: Brug identitets-, enheds- og trusselsbeskyttelse i forbindelse med lovgivning om beskyttelse af personlige oplysninger
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
description: Undgå brud på personlige data med identitets-, enheds- og trusselsbeskyttelsestjenester fra Microsoft 365.
ms.openlocfilehash: 474980e56ac79a9a24d2271f0a58729731dbc1df
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749896"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Brug identitets-, enheds- og trusselsbeskyttelse i forbindelse med lovgivning om beskyttelse af personlige oplysninger

Microsoft 365 indeholder en række identitets-, enheds- og trusselsbeskyttelsesfunktioner, som organisationer kan bruge til at overholde reglerne for beskyttelse af personlige oplysninger. I denne artikel beskrives det, hvad reglerne for beskyttelse af personlige oplysninger kræver i disse områder, og den indeholder en liste over relaterede Funktioner og tjenester i Microsoft 365 med links til flere oplysninger, der kan hjælpe dig med at håndtere implementeringskrav.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Sådan er identitets-, enheds- og trusselsbeskyttelse relateret til lovgivningen om beskyttelse af personlige oplysninger

Selv om forordningerne om beskyttelse af personlige oplysninger varierer afhængigt af deres specificitet, er kernen i det, de kræver, indeholdt i GDPR's artikel 5, stk. 1, litra f), hvori det hedder, at:

- Personoplysninger skal behandles på en måde, der sikrer passende sikkerhed for personoplysningerne, herunder beskyttelse mod uautoriseret eller ulovlig behandling og mod utilsigtet tab, ødelæggelse eller beskadigelse ved hjælp af passende tekniske eller organisatoriske foranstaltninger ("integritet og fortrolighed").

Da brud på personlige data ofte skyldes kompromitteret administrativ konto eller slutbrugerkonto og skadelig systemadgang. Et hack af en administratorkonto kan f.eks. resultere i exfiltration af kundekreditkortnumre eller andre personlige oplysninger. Al den generelt anbefalede identitets-, enheds- og trusselsbeskyttelse, der er tilgængelig med Microsoft 365, skal muligvis implementeres, hvilket afspejles i din overholdelsesscore, som findes i Overholdelsesstyring.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Brug af resultaterne af dit vurderingsarbejde og Overholdelsesstyring

Overholdelsesstyring omfatter identitets-, enheds- og trusselsbeskyttelse ved hjælp af disse kategorier:

- Identiteten svarer til kategorien **Adgangskontrol**
- Enheden svarer til kategorien **Administrer enheder**
- Trusselsbeskyttelse svarer til kategorien **Beskyt mod trusler**
 
Hvis disse vælges på tværs af vores eksempelsæt med fire overordnede regler for beskyttelse af personlige oplysninger, angiver Overholdelsesstyring 90 forbedringshandlinger, hvoraf de fleste får en score på "27". Da et så stort antal er fremhævet af Overholdelsesstyring for disse kategorier, er nogle af de mere almindelige angivet her, som reference.

Brug [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) til identitet og kategorien **Adgangskontrol**, som du kan bruge til at:

- Implementer replayresistent godkendelse (for at forhindre "Mand i midten"-angreb)
- Bloker ældre godkendelse.
- Konfigurer politikker for brugerrisiko og brugerlogonrisiko.
- Aktivér betinget adgang og multifaktorgodkendelse (MFA) for administratorer og ikke-administratorer.
- Konfigurer og gennemtving adgangskodepolitikker.
- Begræns adgangen til privilegerede konti med Azure AD Privileged Identity Management.
- Deaktiver adgang ved afslutning.
- Overvåg brugerkonti og statusændringer.
- Gennemse rollegruppen og administrative ændringer.

Brug [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) til enheder og kategorien **Administrer enheder**, som du kan bruge til at:

- Bloker ødelagte og rodfæstede mobilenheder i fængsel.
- Konfigurer Intune til administration af mobilenheder.
- Opret politikker for overholdelse af angivne standarder for Android-, iOS-, macOS- og Windows-enheder.
- Opret en enhedskonfigurationsprofil til Android-, iOS-, macOS- og Windows-enheder.
- Opret politikker for appbeskyttelse for iOS og Windows.
- Skjul oplysninger med låseskærm.
- Implementer adgangskodepolitikker for mobilenheder.
- Kræv, at mobilenheder låses ved inaktivitet.
- Kræv, at mobilenheder slettes ved flere logonfejl.

Brug [Exchange Online Protection og Microsoft Defender for Office 365](../security/office-365-security/defender-for-office-365.md) til kategorien **Beskyt mod trusler**, som du kan bruge til at:

- Aktivér godkendelse af afsender (SPF, DMARC og DKIM).
- Konfigurer Microsoft Defender for Office 365 politikker til bekæmpelse af phishing.
- Implementer sikre vedhæftede filer.
- Implementer sikre links.
- Implementer politikker for registrering af malware og svar.
- Implementer politikker for udgående og indgående spam.

### <a name="references"></a>Referencer:

- [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md)
- [Beskyt mod trusler i Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Sikre vedhæftede filer](../security/office-365-security/safe-attachments.md)
- [Sikre links](../security/office-365-security/safe-links.md)
- [Sikre dokumenter](../security/office-365-security/safe-docs.md)
