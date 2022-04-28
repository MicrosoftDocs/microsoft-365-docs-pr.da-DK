---
title: Forudsætninger for identitets- og enhedsadgang for skyen i dit Microsoft 365 testmiljø
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
description: Opret et Microsoft 365 miljø for at teste identitets- og enhedsadgang med forudsætningerne for godkendelse kun i skyen.
ms.openlocfilehash: 88138600e516412b74c38234647147197742f2de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097508"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>Forudsætninger for identitets- og enhedsadgang for skyen i dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

[Konfigurationer af identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) er et sæt anbefalede konfigurationer og politikker for betinget adgang, der beskytter adgang til alle tjenester, der er integreret med Azure Active Directory (Azure AD).

I denne artikel beskrives det, hvordan du konfigurerer et Microsoft 365 testmiljø, der opfylder kravene i [cloudmiljøet, som kun er en forudsætning for konfiguration](../security/office-365-security/identity-access-prerequisites.md#prerequisites) af identitet og enhedsadgang.

Der er otte faser til konfiguration af dette testmiljø:

1. Udarbejd dit letvægtstestmiljø
2. Konfigurer navngivne placeringer
3. Konfigurer selvbetjent nulstilling af adgangskode
4. Konfigurer multifaktorgodkendelse
5. Aktivér automatisk enhedsregistrering på domænetilsluttede Windows computere
6. Konfigurer Adgangskodebeskyttelse i Azure AD 
7. Aktivér Azure AD Identity Protection
8. Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>Fase 1: Udarbejd dit letvægts-Microsoft 365 testmiljø

Følg vejledningen i [Konfiguration af letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
Her er den resulterende konfiguration.

![Det lette Microsoft 3656 Enterprise-testmiljø.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>Fase 2: Konfigurer navngivne placeringer

Først skal du bestemme de offentlige IP-adresser eller adresseområder, der bruges af din organisation.

Følg derefter vejledningen i [Konfigurer navngivne placeringer i Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) for at tilføje adresser eller adresseområder som navngivne placeringer. 

## <a name="phase-3-configure-self-service-password-reset"></a>Fase 3: Konfigurer selvbetjent nulstilling af adgangskode

Følg vejledningen i [fase 3 i testvejledningen til nulstilling af adgangskode](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Når du aktiverer nulstilling af adgangskode for kontiene i en bestemt Azure AD-gruppe, skal du føje disse konti til gruppen **Nulstil adgangskode** :

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun nulstilling af adgangskode for bruger 2-kontoen.

## <a name="phase-4-configure-multi-factor-authentication"></a>Fase 4: Konfigurer multifaktorgodkendelse

Følg vejledningen i [fase 2 i testlaboratorievejledningen til multifaktorgodkendelse](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) for følgende brugerkonti:

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun multifaktorgodkendelse for bruger 2-kontoen.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Fase 5: Aktivér automatisk enhedsregistrering på domænetilsluttede Windows computere 

Følg [disse instruktioner](/azure/active-directory/devices/hybrid-azuread-join-plan) for at aktivere automatisk enhedsregistrering af domænetilsluttede Windows computere.

## <a name="phase-6-configure-azure-ad-password-protection"></a>Fase 6: Konfigurer Adgangskodebeskyttelse i Azure AD 

Følg [disse instruktioner](/azure/active-directory/authentication/concept-password-ban-bad) for at blokere kendte svage adgangskoder og deres varianter.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>Fase 7: Aktivér Azure AD Identity Protection

Følg instruktionerne i [fase 2 i Azure AD Identity Protection Test Lab Guide](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Fase 8: Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

Følg [disse instruktioner](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later) for at få Exchange Online. 

For Skype for Business Online:

1. Forbind til [Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Kør denne kommando.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Kontrollér, at ændringen lykkedes med denne kommando.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Resultatet er et testmiljø, der opfylder kravene til den [forudsætningskonfiguration](../security/office-365-security/identity-access-prerequisites.md#prerequisites) , der kun gælder for cloudmiljøet, for identitet og enhedsadgang. 

## <a name="next-step"></a>Næste trin

Brug [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md) til at konfigurere de politikker, der bygger på forudsætningerne, og beskytte identiteter og enheder.

## <a name="see-also"></a>Se også

[Yderligere testvejledninger til identitetstest](m365-enterprise-test-lab-guides.md#identity)

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)
