---
title: Identitets- og enhedsadgang for dit Microsoft 365 testmiljø
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Opret et Microsoft 365-miljø for at teste identitet og enhedsadgang.
ms.openlocfilehash: 488bd22b555ab30a27e0d9c8ef662af1b6945da9
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587259"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Identitets- og enhedsadgang for dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

[Konfigurationer af identitets](../security/office-365-security/microsoft-365-policies-configurations.md)- og enhedsadgang er et sæt anbefalede konfigurationer og politikker for betinget adgang for at beskytte adgangen til alle tjenester, der er integreret med Azure Active Directory (Azure AD).

Sådan opretter du et testmiljø, der har de fælles identitets- og enhedsadgangskonfigurationer på plads:

1. Konfigurer dit testmiljø med de nødvendige identitets- og sikkerhedsfunktioner baseret på dit valg af identitetsmodel og godkendelsesmetode:

  - [Kun sky](cloud-only-prereqs-m365-test-environment.md)
  - [Synkronisering af adgangskodehash (PHS)](phs-prereqs-m365-test-environment.md)
  - [Pass-through-godkendelse (PTA)](pta-prereqs-m365-test-environment.md)

2. Brug [fælles politikker for identitet](../security/office-365-security/identity-access-policies.md) og enhedsadgang til at konfigurere de politikker, der er baseret på de forudsætninger, der er konfigureret til dit testmiljø, og udforske og bekræfte beskyttelse af identiteter og enheder.

## <a name="see-also"></a>Se også

[Yderligere identity Test Lab-vejledninger](m365-enterprise-test-lab-guides.md#identity)

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)
