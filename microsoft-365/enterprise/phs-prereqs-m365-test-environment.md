---
title: Forudsætninger for identitets- og enhedsadgang til synkronisering af adgangskodehash i dit Microsoft 365 testmiljø
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
description: Opret et Microsoft 365 miljø for at teste identitet og enhedsadgang med forudsætningerne for godkendelse af synkronisering af adgangskodehash.
ms.openlocfilehash: af357a477ea0aa66881b546d6cefbd517e453e80
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100363"
---
# <a name="identity-and-device-access-prerequisites-for-password-hash-synchronization-in-your-microsoft-365-test-environment"></a>Forudsætninger for identitets- og enhedsadgang til synkronisering af adgangskodehash i dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

[Konfigurationer af identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) er et sæt konfigurationer og politikker for betinget adgang, der beskytter adgangen til alle tjenester i Microsoft 365 til virksomheder, der er integreret med Azure Active Directory (Azure AD).

I denne artikel beskrives det, hvordan du konfigurerer et Microsoft 365 testmiljø, der opfylder kravene til [hybriden med godkendelse af godkendelse af adgangskodehashsynkronisering](../security/office-365-security/identity-access-prerequisites.md#prerequisites) for at give identitets- og enhedsadgang.

Der er ti faser til konfiguration af dette testmiljø:

1. Opret en simuleret virksomhed med testmiljøet til synkronisering af adgangskodehash
2. Konfigurer Azure AD uden problemer med enkeltlogon
3. Konfigurer navngivne placeringer
4. Konfigurer tilbageførsel af adgangskode
5. Konfigurer selvbetjent nulstilling af adgangskode for alle brugerkonti
6. Konfigurer multifaktorgodkendelse for alle brugerkonti
7. Aktivér automatisk enhedsregistrering på domænetilsluttede Windows computere
8. Konfigurer Adgangskodebeskyttelse i Azure AD 
9. Aktivér Azure AD Identity Protection
10. Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-password-hash-sync-microsoft-365-test-environment"></a>Fase 1: Udarbejd din simulerede virksomhed med synkronisering af adgangskodehash Microsoft 365 testmiljø

Følg vejledningen i [testlaboratorievejledningen til synkronisering af adgangskodehash](password-hash-sync-m365-ent-test-environment.md) .
Her er den resulterende konfiguration.

![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>Fase 2: Konfigurer Azure AD uden problemer med enkeltlogon

Følg vejledningen i [fase 2 i Azure AD Seamless Single Sign-on Test Lab Guide](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>Fase 3: Konfigurer navngivne placeringer

Først skal du bestemme de offentlige IP-adresser eller adresseområder, der bruges af din organisation.

Følg derefter vejledningen i [Konfigurer navngivne placeringer i Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) for at tilføje adresser eller adresseområder som navngivne placeringer. 

## <a name="phase-4-configure-password-writeback"></a>Fase 4: Konfigurer tilbageførsel af adgangskode

Følg instruktionerne i [fase 2 i testvejledningen til tilbageskrivning af adgangskode](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>Fase 5: Konfigurer selvbetjent nulstilling af adgangskode

Følg vejledningen i [fase 3 i testvejledningen til nulstilling af adgangskode](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Når du aktiverer nulstilling af adgangskode for kontiene i en bestemt Azure AD-gruppe, skal du føje disse konti til gruppen **Nulstil adgangskode** :

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun nulstilling af adgangskode for bruger 2-kontoen.

## <a name="phase-6-configure-multi-factor-authentication"></a>Fase 6: Konfigurer multifaktorgodkendelse

Følg vejledningen i [fase 2 i testlaboratorievejledningen til multifaktorgodkendelse](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) for følgende brugerkonti:

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun multifaktorgodkendelse for bruger 2-kontoen.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Fase 7: Aktivér automatisk enhedsregistrering på domænetilsluttede Windows computere 

Følg [disse instruktioner](/azure/active-directory/devices/hybrid-azuread-join-plan) for at aktivere automatisk enhedsregistrering af domænetilsluttede Windows computere.

## <a name="phase-8-configure-azure-ad-password-protection"></a>Fase 8: Konfigurer Adgangskodebeskyttelse i Azure AD 

Følg [disse instruktioner](/azure/active-directory/authentication/concept-password-ban-bad) for at blokere kendte svage adgangskoder og deres varianter.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>Fase 9: Aktivér Azure AD Identity Protection

Følg instruktionerne i [fase 2 i Azure AD Identity Protection Test Lab Guide](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Fase 10: Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

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

Resultatet er et testmiljø, der opfylder kravene i [Active Directory med konfiguration af adgangskodehashsynkronisering](../security/office-365-security/identity-access-prerequisites.md#prerequisites) for identitet og enhedsadgang. 

## <a name="next-step"></a>Næste trin

Brug [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md) til at konfigurere de politikker, der bygger på forudsætningerne, og beskytte identiteter og enheder.

## <a name="see-also"></a>Se også

[Yderligere testvejledninger til identitetstest](m365-enterprise-test-lab-guides.md#identity)

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)
