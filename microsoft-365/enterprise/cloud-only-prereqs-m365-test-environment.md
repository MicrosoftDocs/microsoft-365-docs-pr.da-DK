---
title: Forudsætninger for identitets- og enhedsadgang kun for skyen i Microsoft 365 testmiljø
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
description: Opret et Microsoft 365-miljø til at teste identitet og enhedsadgang med forudsætningerne for kun skygodkendelse.
ms.openlocfilehash: a0d9a50552b981f8595f661330a7c200e1d54f8a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63589095"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>Forudsætninger for identitets- og enhedsadgang kun for skyen i Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

[Konfigurationer af identitets](../security/office-365-security/microsoft-365-policies-configurations.md)- og enhedsadgang er et sæt anbefalede konfigurationer og politikker for betinget adgang for at beskytte adgangen til alle tjenester, der er integreret med Azure Active Directory (Azure AD).

I denne artikel beskrives det, hvordan du konfigurerer Microsoft 365 testmiljø, der kun opfylder kravene til konfiguration af skyen, der er en [forudsætning for](../security/office-365-security/identity-access-prerequisites.md#prerequisites) identitets- og enhedsadgang.

Der er otte faser til konfiguration af dette testmiljø:

1. Byg dit lette testmiljø
2. Konfigurere navngivne placeringer
3. Konfigurere nulstilling af adgangskode via selvbetjening
4. Konfigurer multifaktorgodkendelse
5. Aktivér automatisk enhedsregistrering for domænetilføjede Windows computere
6. Konfigurere Azure AD-adgangskodebeskyttelse 
7. Aktivér Azure AD Identity Protection
8. Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>Fase 1: Byg dit lette Microsoft 365 testmiljø

Følg vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
Her er den resulterende konfiguration.

![Det lette Microsoft 3656 Enterprise-testmiljø.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>Fase 2: Konfigurer navngivne placeringer

Først skal du bestemme de offentlige IP-adresser eller adresseintervaller, der bruges af din organisation.

Følg derefter vejledningen i Konfigurere [navngivne placeringer i Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) for at tilføje adresser eller adresseintervaller som navngivne placeringer. 

## <a name="phase-3-configure-self-service-password-reset"></a>Fase 3: Konfigurer nulstilling af adgangskode via selvbetjening

Følg vejledningen i Fase [3 i guiden til nulstilling af adgangskode i Test Lab](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Når du aktiverer nulstilling af adgangskode for konti i en bestemt Azure AD-gruppe, skal du føje disse konti til gruppen **Nulstilling af** adgangskode:

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun nulstilling af adgangskode for Bruger 2-kontoen.

## <a name="phase-4-configure-multi-factor-authentication"></a>Fase 4: Konfigurer multifaktorgodkendelse

Følg vejledningen i [fase 2 i Test Lab-vejledningen til multifaktorgodkendelse](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) for følgende brugerkonti:

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun multifaktorgodkendelse for Bruger 2-kontoen.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Fase 5: Aktivér automatisk enhedsregistrering for domænetilføjede Windows computere 

Følg [disse instruktioner for](/azure/active-directory/devices/hybrid-azuread-join-plan) at aktivere automatisk enhedsregistrering for domænetilføjede Windows computere.

## <a name="phase-6-configure-azure-ad-password-protection"></a>Fase 6: Konfigurer Azure AD-adgangskodebeskyttelse 

Følg [disse instruktioner](/azure/active-directory/authentication/concept-password-ban-bad) for at blokere kendte svage adgangskoder og deres varianter.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>Fase 7: Aktivér Azure AD Identity Protection

Følg vejledningen i Fase [2 i Vejledningen til Azure AD Identity Protection Test Lab](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Fase 8: Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

Følg Exchange Online vejledning for [at få flere oplysninger](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

For Skype for Business Online:

1. Forbind til [Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Kør denne kommando.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Kontrollér, at ændringen blev gennemført med denne kommando.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Resultatet er et testmiljø, der opfylder kravene til konfiguration af identitet [og](../security/office-365-security/identity-access-prerequisites.md#prerequisites) enhedsadgang, der kun er påkrævet i skyen. 

## <a name="next-step"></a>Næste trin

Brug [fælles politikker for identitet og enhedsadgang](../security/office-365-security/identity-access-policies.md) til at konfigurere de politikker, der bygger på forudsætningerne og beskytter identiteter og enheder.

## <a name="see-also"></a>Se også

[Yderligere identity Test Lab-vejledninger](m365-enterprise-test-lab-guides.md#identity)

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)
