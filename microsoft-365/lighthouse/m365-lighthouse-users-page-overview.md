---
title: Microsoft 365 oversigt over siden brugere i Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: Få mere at vide om siden Brugere for administrerede tjenesteudbydere ved Microsoft 365 Lighthouse.
ms.openlocfilehash: fad5ff4b41b43efb68c7e230401b80e50cea95a4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592483"
---
# <a name="microsoft-365-lighthouse-users-page-overview"></a>Microsoft 365 oversigt over siden brugere i Lighthouse 

Microsoft 365 Lighthouse giver dig mulighed for at administrere brugere på tværs af kundelejerkonti ved at vælge Brugere i venstre navigationsrude for at åbne siden Brugere. Fra denne side kan du søge efter brugere og vurdere og handle på sikkerhedstilstanden for dine brugerkonti. Du kan også få vist indsigt i risikabelt bruger og status for multifaktorgodkendelse og nulstilling af adgangskode via selvbetjening.  
  
## <a name="search-users-tab"></a>Fanen Søg efter brugere  
  
Under fanen Søg efter brugere kan du hurtigt søge på tværs af lejere efter bestemte brugere og udføre grundlæggende brugeradministrationshandlinger som f.eks. nulstilling af en adgangskode til en konto.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Skærmbillede af fanen Søg efter brugere.":::

## <a name="risky-users-tab"></a>Fanen Risikabel brugere

Fanen Risikabele brugere viser brugerkonti på tværs af dine lejere, der er markeret med flag for risikabelt adfærd. Vælg en af brugerne for at få vist flere oplysninger om en registreret risiko eller for at reducere en risiko ved at nulstille en brugers adgangskode eller blokere logon. Du kan finde flere oplysninger om risikotyper og [registrering under Hvad er risiko?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

Fanen Risikabel brugere indeholder også følgende indstillinger:
- **Eksportér:** Vælg for at eksportere data om enhedsoverholdelse til Excel fil med kommaseparerede værdier (.csv).
- **Opdater:** Vælg for at hente de mest aktuelle data om enhedsoverholdelse.
- **Bekræft, at en eller flere brugere er kompromitteret:** Vælg for at bekræfte, at brugeren er blevet kompromitteret.
- **Afvis risiko for brugere:** Vælg for at afvise brugersikkerhedsrisikoen.  
- **Nulstil adgangskode:** Vælg for at ændre eller nulstille brugerens adgangskode.
- **Bloker logon:** Vælg for at forhindre andre i at logge på som denne bruger.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="Skærmbillede af fanen Risikabele brugere.":::

## <a name="multifactor-authentication-tab"></a>Fanen Multifaktorgodkendelse

Fanen Multifaktorgodkendelse indeholder detaljerede oplysninger om status for multifaktorgodkendelse (MFA)-aktivering på tværs af dine lejere. Vælg en vilkårlig lejer på listen for at få vist flere oplysninger om den pågældende lejer, herunder hvilke betingede adgangspolitikker, der kræver MFA, der allerede er konfigureret, og hvilke brugere der endnu ikke er registreret for MFA.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="Skærmbillede af fanen Multifaktorgodkendelse.":::

## <a name="password-reset-tab"></a>Fanen Nulstilling af adgangskode

Fanen Nulstilling af adgangskode viser detaljerede oplysninger om status for aktivering af nulstilling af adgangskode via selvbetjening på tværs af dine lejere. Den giver også indsigt i brugere, der er aktiveret, men stadig skal registrere sig, før de selv kan nulstille deres adgangskode.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="Skærmbillede af fanen Nulstilling af adgangskode.":::

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 Lighthouse- enhedsoverholdelsesside](m365-lighthouse-device-compliance-page-overview.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)
