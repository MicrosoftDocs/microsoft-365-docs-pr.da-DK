---
title: Oversigt over siden Brugere i Microsoft 365 Fyrtårn
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Få mere at vide om siden Brugere for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: d817ab74d6dd24e644561684073189e68cf7e072
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66007278"
---
# <a name="overview-of-the-users-page-in-microsoft-365-lighthouse"></a>Oversigt over siden Brugere i Microsoft 365 Fyrtårn 

Microsoft 365 Fyrtårn kan du administrere brugere på tværs af kundelejerkonti ved at vælge **Brugere** i navigationsruden til venstre for at åbne siden Brugere. Fra denne side kan du søge efter brugere og vurdere og reagere på sikkerhedstilstanden for dine brugerkonti. Du kan også få vist indsigt i risikable brugere og status for multifaktorgodkendelse og selvbetjent nulstilling af adgangskode.  
  
## <a name="search-users-tab"></a>Fanen Søg efter brugere  
  
Under fanen Søg efter brugere kan du hurtigt søge efter bestemte brugere på tværs af lejere og udføre grundlæggende brugeradministrationshandlinger, f.eks. nulstille en kontoadgangskode.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Skærmbillede af fanen Søg efter brugere.":::

## <a name="risky-users-tab"></a>Fanen Risikable brugere

Fanen Risikable brugere viser brugerkonti på tværs af dine lejere, der er markeret med risiko for risiko. Vælg en af brugerne for at få vist flere oplysninger om en registreret risiko eller for at afhjælpe en risiko ved at nulstille en brugers adgangskode eller blokere for logon. Du kan få flere oplysninger om risikotyper og registrering under [Hvad er risikoen?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

Fanen Risikable brugere indeholder også følgende indstillinger:
- **Eksport:** Vælg at eksportere data om enhedens overholdelse af angivne standarder til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste data om enhedens overholdelse af angivne standarder.
- **Bekræft, at en eller flere brugere er kompromitteret:** Vælg for at bekræfte, at brugeren er blevet kompromitteret.
- **Afvis brugerrisici:** Vælg at afvise brugerrisikoen.  
- **Nulstil adgangskode:** Vælg at ændre eller nulstille brugerens adgangskode.
- **Bloklogon:** Vælg for at forhindre nogen i at logge på som denne bruger.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Skærmbillede af fanen Risikable brugere.":::

## <a name="multifactor-authentication-tab"></a>Fanen Godkendelse af multifaktor

Fanen Multifactor Authentication indeholder detaljerede oplysninger om status for MFA-aktivering (Multifactor Authentication) på tværs af dine lejere. Vælg en hvilken som helst lejer på listen for at få vist flere oplysninger om den pågældende lejer, herunder hvilke politikker for betinget adgang, der kræver MFA, der allerede er konfigureret, og hvilke brugere der endnu ikke har registreret sig til MFA.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Skærmbillede af fanen Godkendelse af multifaktor.":::

## <a name="password-reset-tab"></a>Fanen Nulstil adgangskode

Fanen Nulstil adgangskode viser detaljerede oplysninger om status for selvbetjent nulstilling af adgangskode på tværs af dine lejere. Den giver også indsigt i brugere, der er aktiveret, men stadig har brug for at registrere, før de selv kan nulstille deres adgangskode.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Skærmbillede af fanen Nulstil adgangskode.":::

## <a name="related-content"></a>Relateret indhold

[oversigt over Microsoft 365 siden med overholdelse af angivne standarder for lighthouse-enheder](m365-lighthouse-device-compliance-page-overview.md) (artikel)\
[ofte stillede spørgsmål om Microsoft 365 fyrtårn](m365-lighthouse-faq.yml) (artikel)
