---
title: Azure AD Identity Protection til din Microsoft 365 til virksomhedstestmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Konfigurer Azure AD Identity Protection, og analysér de aktuelle konti i Microsoft 365 for Enterprise Test Environment.
ms.openlocfilehash: 210736e0a950d74e0cd761463e9cc27f1dc3c721
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587862"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Azure AD Identity Protection til din Microsoft 365 til virksomhedstestmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Du kan bruge Azure Active Directory (Azure AD) Identity Protection til at registrere potentielle sårbarheder, der påvirker din organisations identiteter, konfigurere automatiserede svar og undersøge hændelser. I denne artikel beskrives det, hvordan du kan bruge Azure AD Identity Protection til at få vist analysen af dine testmiljøkonti.

Konfiguration af Azure AD Identity Protection i dit Microsoft 365 for Enterprise Test Environment omfatter to faser:

- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Brug Azure AD Identity Protection](#phase-2-use-azure-ad-identity-protection)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du let vil teste Azure AD Identity Protection på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste Azure AD Identity Protection i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af Azure AD Identity Protection kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS)-skov. Den findes her som en mulighed, så du kan teste Azure AD Identity Protection og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Fase 2: Brug Azure AD Identity Protection

1. Åbn en privat forekomst af din browser, og log på Azure-portalen [https://portal.azure.com](https://portal.azure.com) med den globale administratorkonto for din Microsoft 365 for Enterprise Test Environment.
2. I Azure-portalen skal du **skrive identitetsbeskyttelse** i søgefeltet og derefter vælge **Azure AD Identity Protection**.
3. I Identity **Protection - Overview-bladet** skal du vælge hver rapport for at se, hvad den rapporterer.
4. Under **Giv besked** skal du **vælge Brugere, der er i fare for at modtage beskeder**.
5. I **ruden Brugere med risiko for registrerede beskeder** skal du vælge **Mellem**.
6. For **mails sendes til følgende brugere skal du** vælge **Inkluderet og** bekræfte, at din globale administratorkonto er på listen over valgte medlemmer.
7. Vælg **Gem**.

Under **Beskyt skal** du vælge forskellige politikforanstaltninger for at se, hvordan du konfigurerer dem. Hvis du opretter og aktiverer en politik, skal du sikre dig, at den ikke blokerer adgangen for alle brugere, ellers kan du muligvis ikke logge på. Du kan forhindre dette ved at udelade bestemte brugerkonti, f.eks. globale administratorer.

For yderligere test og eksperimentering skal du se [Si dine risikohændelser](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)