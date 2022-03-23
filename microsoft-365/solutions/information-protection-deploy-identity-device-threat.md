---
title: Brug identitet, enhed og trusselsbeskyttelse til databeskyttelse for databeskyttelse
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
ms.custom: ''
description: Undgå brud på personlige data med identitet, enhed og trusselsbeskyttelse af Microsoft 365.
ms.openlocfilehash: a5aa97637b0d44b762d1a1146effdefb932ab47d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588432"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Brug identitet, enhed og trusselsbeskyttelse til databeskyttelse for databeskyttelse

Microsoft 365 indeholder en række funktioner til identitet, enhed og trusselsbeskyttelse, som organisationer kan anvende for at overholde regler om beskyttelse af personlige oplysninger. I denne artikel beskrives det, hvad reglerne om beskyttelse af personlige oplysninger kræver på disse områder, og den indeholder en liste over relaterede Microsoft 365-funktioner og -tjenester med links til flere oplysninger, der kan hjælpe dig med at tage hånd om kravene til implementering.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Sådan er identitet, enhed og trusselsbeskyttelse relateret til persondataforordningen

Reglerne for beskyttelse af data varierer i forhold til deres specificitet, men essensen af det, de kræver, findes i GDPR's artikel 5(1)(f), som meddeler, at:

- Personlige data skal behandles på en måde, der sikrer passende sikkerhed for personlige data, herunder beskyttelse mod uautoriseret eller ulovlig behandling og mod utilsigtet tab, tilsigtet eller skade, ved hjælp af relevante tekniske eller organisatoriske foranstaltninger ('integritet og fortrolighed').

Brud på personlige data er ofte forårsaget af administrativ eller slutbrugeradgang og ondsindet adgang til systemet. Eksempelvis kan et administratorkonto hacke resultere i eksfiltrering af kundens kreditkortnumre eller andre personlige oplysninger. Alle de generelt kan anbefales identitet, enhed og trusselsbeskyttelse, der er tilgængelige med Microsoft 365, bør potentielt gennemføres, hvilket afspejles i dit overholdelsesresultat, som findes i Overholdelsesstyring.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Brug af resultaterne af dit bedømmelsesarbejde og Compliance Manager

Overholdelsesstyring omfatter identitet, enhed og trusselsbeskyttelse ved hjælp af disse kategorier:

- Identitet svarer til kategorien **Kontrolelementadgang**
- Enheden svarer til **kategorien Administrer** enheder
- **Trusselsbeskyttelse svarer til kategorien Beskyt mod** trusler
 
Hvis disse er valgt på tværs af vores eksempelsæt med fire overordnede regler for beskyttelse af personlige oplysninger, angiver Overholdelsesstyring 90 forbedringshandlinger, hvoraf de fleste får "27". Da et så stort antal omtales af Overholdelsesstyring for disse kategorier, er nogle af de mest almindelige angivet her som reference.

Brug [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) til identitet og kategorien **Kontroladgang**, hvor du kan:

- Implementere godkendelse med godkendelse med genafspilning (for at forhindre "Mand i midten"-angreb)
- Bloker ældre godkendelse.
- Konfigurer politikker for brugerrisici og risiko ved logon.
- Aktivér Betinget adgang og Multi-Factor Authentication (MFA) for administratorer og ikke-administratorer.
- Konfigurer og gennemtving adgangskodepolitikker.
- Begræns adgangen til privilegerede konti med Azure AD Privileged Identity Management.
- Deaktiver adgang ved afslutning.
- Overse brugerkonti og statusændringer.
- Gennemse rollegruppe og administrative ændringer.

Brug [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) til enheder og **kategorien Administrer** enheder, hvor du kan:

- Bloker jail broken and rooted mobile devices.
- Konfigurer Intune til administration af mobilenheder.
- Opret overholdelsespolitikker til Android-, iOS-, macOS- og Windows enheder.
- Opret en enhedskonfigurationsprofil til Android-, iOS-, macOS- og Windows enheder.
- Opret politikker for appbeskyttelse til iOS og Windows.
- Skjul oplysninger med låseskærmen.
- Implementer adgangskodepolitikker for mobilenheder.
- Kræv, at mobilenheder låses ved inaktivitet.
- Kræv, at mobilenheder fuldstændigt slettes ved flere logonfejl.

Brug [Exchange Online Protection og Microsoft Defender til Office 365](../security/office-365-security/defender-for-office-365.md) kategorien **Beskyt mod trusler**, hvor du kan:

- Aktivér afsendergodkendelse (SPF, DMARC og DKIM).
- Konfigurer Microsoft Defender til Office 365 antiphishing-politikker.
- Implementer Pengeskab vedhæftede filer.
- Implementer Pengeskab Links.
- Implementer politikker for registrering af malware og svar.
- Implementer politikker for udgående og indgående spam.

### <a name="references"></a>Referencer:

- [Fælles identitets- og enhedsadgangspolitikker](../security/office-365-security/identity-access-policies.md)
- [Beskyt dig mod trusler i Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Pengeskab vedhæftede filer](../security/office-365-security/safe-attachments.md)
- [Sikre links](../security/office-365-security/safe-links.md)
- [Sikre dokumenter](../security/office-365-security/safe-docs.md)
