---
title: Azure AD Identity Protection til dine Microsoft 365 til virksomhedstestmiljøer
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Konfigurer Azure AD Identity Protection, og analysér de aktuelle konti i dit Microsoft 365 til virksomhedstestmiljø.
ms.openlocfilehash: 1f947f9b74b1909aa1e6451ec835a2ad78964f75
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078751"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>Azure AD Identity Protection til dine Microsoft 365 til virksomhedstestmiljøer

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Du kan bruge Azure Active Directory (Azure AD) Identity Protection til at registrere potentielle sikkerhedsrisici, der påvirker din organisations identiteter, konfigurere automatiserede svar og undersøge hændelser. I denne artikel beskrives det, hvordan du bruger Azure AD Identity Protection til at få vist analysen af dine testmiljøkonti.

Konfiguration af Azure AD Identity Protection i dit Microsoft 365 til virksomhedstestmiljø omfatter to faser:

- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Brug Azure AD Identity Protection](#phase-2-use-azure-ad-identity-protection)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du kun vil teste Azure AD Identity Protection på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af Letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste Azure AD Identity Protection i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af Azure AD Identity Protection kræver ikke det simulerede virksomhedstestmiljø, som omfatter et simuleret intranet, der er forbundet med internet- og katalogsynkronisering for et AD DS-område (Active Directory-domæneservices). Den leveres her som en mulighed, så du kan teste Azure AD Identity Protection og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>Fase 2: Brug Azure AD Identity Protection

1. Åbn en privat forekomst af din browser, og log på Azure Portal på [https://portal.azure.com](https://portal.azure.com) med den globale administratorkonto for dit Microsoft 365 for virksomhedstestmiljø.
2. I Azure Portal skal du skrive **identitetsbeskyttelse** i søgefeltet og derefter vælge **Azure AD Identity Protection**.
3. På bladet **Identitetsbeskyttelse – Oversigt** skal du vælge hver rapport for at se, hvad den rapporterer.
4. Under **Giv besked** skal du vælge **Brugere med risiko for registrerede beskeder**.
5. Vælg **Mellem** i ruden Brugere, der **er i fare for at registrere beskeder**.
6. Hvis **mails sendes til følgende brugere**, skal du vælge **Inkluderet** og bekræfte, at din globale administratorkonto er på listen over valgte medlemmer.
7. Vælg **Gem**.

Under **Beskyt** skal du vælge forskellige politifolk for at se, hvordan du konfigurerer dem. Hvis du opretter og aktiverer en politik, skal du sørge for, at den ikke blokerer adgang for alle brugere, eller at du muligvis ikke kan logge på. Du kan forhindre dette ved at udelade bestemte brugerkonti, f.eks. globale administratorer.

Du kan finde flere test og eksperimenter under [Simulerede risikohændelser](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)