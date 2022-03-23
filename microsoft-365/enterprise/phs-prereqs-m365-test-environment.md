---
title: Forudsætninger for identitets- og enhedsadgang til synkronisering af adgangskodehash i Microsoft 365 testmiljø
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
description: Opret et Microsoft 365-miljø til at teste identitet og enhedsadgang med forudsætningerne for synkronisering af adgangskodehashgodkendelse.
ms.openlocfilehash: fc8ca3288204880810856e79d485305de75f9c27
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587260"
---
# <a name="identity-and-device-access-prerequisites-for-password-hash-synchronization-in-your-microsoft-365-test-environment"></a>Forudsætninger for identitets- og enhedsadgang til synkronisering af adgangskodehash i Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

[Konfigurationer af identitets](../security/office-365-security/microsoft-365-policies-configurations.md)- og enhedsadgang er et sæt konfigurationer og politikker for betinget adgang for at beskytte adgangen til alle tjenester i Microsoft 365 til virksomheder, der er integreret med Azure Active Directory (Azure AD).

I denne artikel beskrives det, hvordan du konfigurerer et Microsoft 365-testmiljø, der opfylder kravene for hybrid med godkendelse af synkronisering af [adgangskodehash](../security/office-365-security/identity-access-prerequisites.md#prerequisites) for konfiguration af identitets- og enhedsadgang.

Der er ti faser til konfiguration af dette testmiljø:

1. Opret en simuleret virksomhed med testmiljø til synkronisering af adgangskodehash
2. Konfigurer Azure AD seamless single sign-on
3. Konfigurere navngivne placeringer
4. Konfigurere tilbageførsel af adgangskode
5. Konfigurere nulstilling af adgangskode via selvbetjening for alle brugerkonti
6. Konfigurer multifaktorgodkendelse for alle brugerkonti
7. Aktivér automatisk enhedsregistrering for domænetilføjede Windows computere
8. Konfigurere Azure AD-adgangskodebeskyttelse 
9. Aktivér Azure AD Identity Protection
10. Aktivér moderne godkendelse for Exchange Online og Skype for Business Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-password-hash-sync-microsoft-365-test-environment"></a>Fase 1: Opbyg din simulerede virksomhed med synkronisering af adgangskodehash Microsoft 365 testmiljø

Følg instruktionerne i [vejledningen i synkronisering af adgangskodehash](password-hash-sync-m365-ent-test-environment.md) Test Lab- vejledning.
Her er den resulterende konfiguration.

![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>Fase 2: Konfigurer Azure AD – nem enkelt logon

Følg vejledningen i [Fase 2 i Azure AD Seamless Single Sign-on Test Lab-vejledningen](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>Fase 3: Konfigurer navngivne placeringer

Først skal du bestemme de offentlige IP-adresser eller adresseintervaller, der bruges af din organisation.

Følg derefter vejledningen i Konfigurere [navngivne placeringer i Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) for at tilføje adresser eller adresseintervaller som navngivne placeringer. 

## <a name="phase-4-configure-password-writeback"></a>Fase 4: Konfigurer tilbageførsel af adgangskode

Følg vejledningen i fase [2 i testlaboratorvejledningen til tilbageførsel af adgangskode](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>Fase 5: Konfigurer nulstilling af adgangskode via selvbetjening

Følg vejledningen i Fase [3 i guiden til nulstilling af adgangskode i Test Lab](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Når du aktiverer nulstilling af adgangskode for konti i en bestemt Azure AD-gruppe, skal du føje disse konti til gruppen **Nulstilling af** adgangskode:

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun nulstilling af adgangskode for Bruger 2-kontoen.

## <a name="phase-6-configure-multi-factor-authentication"></a>Fase 6: Konfigurer multifaktorgodkendelse

Følg vejledningen i [fase 2 i Test Lab-vejledningen til multifaktorgodkendelse](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) for følgende brugerkonti:

- Bruger 2
- Bruger 3
- Bruger 4
- Bruger 5

Test kun multifaktorgodkendelse for Bruger 2-kontoen.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Fase 7: Aktivér automatisk enhedsregistrering for domænetilføjede Windows computere 

Følg [disse instruktioner for](/azure/active-directory/devices/hybrid-azuread-join-plan) at aktivere automatisk enhedsregistrering for domænetilføjede Windows computere.

## <a name="phase-8-configure-azure-ad-password-protection"></a>Fase 8: Konfigurer Azure AD-adgangskodebeskyttelse 

Følg [disse instruktioner](/azure/active-directory/authentication/concept-password-ban-bad) for at blokere kendte svage adgangskoder og deres varianter.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>Fase 9: Aktivér Azure AD Identity Protection

Følg vejledningen i Fase [2 i Vejledningen til Azure AD Identity Protection Test Lab](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Fase 10: Aktivér moderne godkendelse til Exchange Online og Skype for Business Online

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

Resultatet er et testmiljø, der opfylder kravene til [Active Directory](../security/office-365-security/identity-access-prerequisites.md#prerequisites) med konfiguration af synkronisering af adgangskodehash for identitet og enhedsadgang. 

## <a name="next-step"></a>Næste trin

Brug [fælles politikker for identitet og enhedsadgang](../security/office-365-security/identity-access-policies.md) til at konfigurere de politikker, der bygger på forudsætningerne og beskytter identiteter og enheder.

## <a name="see-also"></a>Se også

[Yderligere identity Test Lab-vejledninger](m365-enterprise-test-lab-guides.md#identity)

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)
