---
title: Oversigt over siden Brugere i Microsoft 365 Lighthouse
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
ms.openlocfilehash: 05c889167cc7359900c0dea3396e657c0aa93fba
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717538"
---
# <a name="overview-of-the-users-page-in-microsoft-365-lighthouse"></a>Oversigt over siden Brugere i Microsoft 365 Lighthouse 

Med Microsoft 365 Lighthouse kan du administrere brugere på tværs af kundelejerkonti ved at vælge et af linkene under **Brugere** i venstre navigationsrude. Fra siden Brugere kan du søge efter brugere og vurdere og reagere på sikkerhedstilstanden for dine brugerkonti. Du kan også få vist indsigt i risikable brugere og status for multifaktorgodkendelse og selvbetjent nulstilling af adgangskode.  
  
## <a name="search-users-tab"></a>Fanen Søg efter brugere  
  
Under fanen Søg efter brugere kan du hurtigt søge efter bestemte brugere på tværs af lejere og udføre almindelige brugeradministrationsopgaver, f.eks. opdatere brugerkontooplysninger, nulstille adgangskoder, tildele licenser og administrere en brugers grupper, postkasse eller OneDrive.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Skærmbillede af fanen Søg efter brugere.":::

## <a name="risky-users-tab"></a>Fanen Risikable brugere

Fanen Risikable brugere viser brugerkonti på tværs af dine lejere, der er markeret med risiko for risiko. Vælg en af brugerne for at få vist flere oplysninger om en registreret risiko eller for at afhjælpe en risiko ved at nulstille en brugers adgangskode eller blokere for logon. Du kan få flere oplysninger om risikotyper og registrering under [Hvad er risikoen?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

Fanen Risikable brugere indeholder også følgende indstillinger:
- **Eksport:** Vælg at eksportere data om enhedens overholdelse af angivne standarder til en Excel-fil med kommaseparerede værdier (.csv).
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

[Oversigt over siden med overholdelse af angivne standarder for Microsoft 365 Lighthouse-enhed](m365-lighthouse-device-compliance-page-overview.md) (artikel)\
[Ofte stillede spørgsmål om Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (artikel)
