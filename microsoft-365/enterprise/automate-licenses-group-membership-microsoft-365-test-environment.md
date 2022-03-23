---
title: Automatiser licensering og gruppemedlemskab for Microsoft 365 for Enterprise Test Environment
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Konfigurer gruppebaseret licensering og dynamisk gruppemedlemskab i Microsoft 365 for Enterprise Test Environment.
ms.openlocfilehash: cbf10436ded2fbdcbe34c2a0bfa15b0a70a30eeb
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587666"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatiser licensering og gruppemedlemskab for Microsoft 365 for Enterprise Test Environment

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Gruppebaserede licenser tildeler eller fjerner automatisk licenser for en brugerkonto baseret på gruppemedlemskab. Dynamisk gruppemedlemskab tilføjer eller fjerner medlemmer til en gruppe baseret på egenskaber for brugerkontoen, f.eks **. Afdeling** eller **Land**. I denne artikel bliver du vejlet gennem demonstrationer af både at tilføje og fjerne gruppemedlemmer Microsoft 365 for Enterprise Test Environment.

Konfiguration af automatisk licensering og dynamisk gruppemedlemskab til dit Microsoft 365 testmiljø omfatter to faser:

- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Konfigurer og test dynamisk gruppemedlemskab og automatisk licensering](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du kun vil teste automatiserede licenser og gruppemedlemskab på en let måde sammen med minimumskravene, skal du følge vejledningen i [Lightweight base-konfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste automatiseret licensering og gruppemedlemskab i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af automatiseret licensering og gruppemedlemskab kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS)-skov. Den findes her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskaber og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Fase 2: Konfigurer og test dynamisk gruppemedlemskab og automatisk licensering

Først skal du oprette en ny gruppe med navnet Salg og tilføje en dynamisk gruppemedlemskabsregel, så brugerkonti med afdelingen, der er angivet til **Salg, automatisk** tilmelder sig gruppen Salg.

1. I en privat forekomst af din internetbrowser skal du logge på [Microsoft 365 Administration med den](https://admin.microsoft.com) globale administratorkonto for dit Microsoft 365 E5 test lab-abonnement.
2. På en separat fane i browseren skal du gå til Azure-portalen på [https://portal.azure.com](https://portal.azure.com).
3. I Azure-portalen skal du **angive** grupper i søgefeltet og derefter vælge **Grupper**.
4. I **ruden Alle grupper** skal du vælge **Ny gruppe**.
5. I **Gruppetype** skal du **vælge Microsoft 365**.
6. I **Gruppenavn skal** du angive **Salg**.
7. Vælg **Dynamisk bruger** under **Medlemskabstype**.
8. Vælg **Dynamiske brugermedlemmer**.
9. I **ruden Dynamiske regler for** medlemskab: 
   - Vælg **afdelingsegenskaben** .
   - Vælg **operatoren Er lig** med.
   - I feltet **Værdi** skal du angive **Salg**.
10. Vælg **Gem**.
11. Vælg **Opret**.

Dernæst skal du konfigurere gruppen Salg, så medlemmerne automatisk får tildelt den Microsoft 365 E5 licens.

1. Vælg gruppen **Salg** , og vælg derefter **Licenser**.
2. I **ruden Opdater licenstildelinger** skal du **vælge Microsoft 365 E5** og derefter vælge **Gem**.
3. Luk Fanen Azure-portal i din browser.

Dernæst skal du teste dynamisk gruppemedlemskab og automatisk licensering på bruger 4-kontoen:

1. Vælg **administrator Microsoft Office** fanen Hjem i **din browser**.
2. På fanen **Microsoft 365 Administration** skal du vælge **Aktive brugere**.
3. På siden **Aktive brugere** skal du vælge **bruger 4-kontoen** .
4. I **ruden Bruger 4** skal du vælge **Rediger** for **produktlicenser**.
5. I **ruden Produktlicenser** skal du **deaktivere Microsoft 365 E5** licensen og derefter vælge **GemLuk** > .
6. I egenskaberne for Bruger 4-kontoen skal du bekræfte, at der ikke er tildelt nogen produktlicenser, og at der ikke er nogen gruppemedlemskaber.
7. Vælg **Rediger for** at få **kontaktoplysninger**.
8. I **ruden Rediger kontaktoplysninger** skal du vælge **Kontaktoplysninger**.
9. I feltet **Afdeling** skal du **angive Salg** og derefter **vælge** **GemLuk** > .
10. Vent et par minutter, og vælg derefter **med jævne mellemrum** ikonet Opdater øverst til højre i ruden Bruger 4-konto.

Til tiden vil du kunne se følgende:

- **Egenskaben Gruppemedlemskaber** er opdateret med **gruppen** Salg.
- **Egenskaben Produktlicenser** er **opdateret Microsoft 365 E5** produktlicensen.

Se følgende artikler for at installere dynamisk gruppemedlemskab og automatisk licensering i produktion:

- [Gruppebaserede licenser i Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Dynamiske grupper i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)