---
title: Identitet og enhedsadgang til dit Microsoft 365 testmiljø
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Opret et Microsoft 365 miljø for at teste identitet og enhedsadgang.
ms.openlocfilehash: 09c7bf9ecb6aaadc89cedfd881e66a5fd19f28d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091209"
---
# <a name="identity-and-device-access-for-your-microsoft-365-test-environment"></a>Identitet og enhedsadgang til dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

[Konfigurationer af identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) er et sæt anbefalede konfigurationer og politikker for betinget adgang, der beskytter adgang til alle tjenester, der er integreret med Azure Active Directory (Azure AD).

Sådan opretter du et testmiljø, der har de fælles konfigurationer for identitets- og enhedsadgang:

1. Konfigurer dit testmiljø med de påkrævede identitets- og sikkerhedsfunktioner baseret på dit valg af identitetsmodel og godkendelsesmetode:

  - [Kun cloud](cloud-only-prereqs-m365-test-environment.md)
  - [Synkronisering af adgangskodehash (PHS)](phs-prereqs-m365-test-environment.md)
  - [Pass-through-godkendelse (PTA)](pta-prereqs-m365-test-environment.md)

2. Brug [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md) til at konfigurere de politikker, der bygger på de forudsætninger, der er konfigureret for dit testmiljø, og udforsk og bekræft beskyttelse af identiteter og enheder.

## <a name="see-also"></a>Se også

[Yderligere testvejledninger til identitetstest](m365-enterprise-test-lab-guides.md#identity)

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)
