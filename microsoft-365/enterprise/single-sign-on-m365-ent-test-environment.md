---
title: Azure AD Seamless Single Sign-on til dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Oversigt: Konfigurer og test Azure AD Seamless Single Sign-on for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 4a420da5251ecef900f2efe9573db1d51a6bd597
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589090"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Azure AD Seamless Single Sign-on til dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

Azure AD Seamless Single Sign-On (Seamless SSO) logger automatisk brugerne på, når de er på deres pc eller enheder, der har forbindelse til deres organisationsnetværk. Azure AD Seamless SSO giver brugerne nem adgang til skybaserede programmer uden brug af yderligere lokale komponenter.

I denne artikel beskrives det, hvordan du konfigurerer Microsoft 365 testmiljø til Azure AD Seamless SSO.

Konfiguration af Azure AD Seamless SSO involverer to faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Konfigurer Azure AD-Forbind APP1 til Azure AD Seamless SSO](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg vejledningen i synkronisering [af adgangskodehash for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

Den resulterende konfiguration ser sådan ud:
  
![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- En Microsoft 365 E5 prøveversion eller et betalt abonnement.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for med jævne mellemrum at synkronisere TESTLAB Active Directory-domæneservices-domænet (AD DS) med Azure AD-lejeren for dit Microsoft 365-abonnement.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Fase 2: Konfigurer Azure AD-Forbind APP1 til Azure AD Seamless SSO

I denne fase skal du konfigurere Azure AD Forbind APP1 til Azure AD Seamless SSO og derefter kontrollere, at det fungerer.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurere Azure AD Forbind på APP1

1. Log på [med din](https://portal.azure.com) globale administratorkonto fra Azure-portalen, og opret derefter forbindelse til APP1 med TESTLAB\User1-kontoen.

2. Fra skrivebordsappen i APP1 skal du køre Azure AD Forbind.

3. På **velkomstsiden skal** du vælge **Konfigurer**.

4. På siden **Yderligere opgaver** skal du **vælge Skift bruger-logon** og derefter vælge **Næste**.

5. På siden **Forbind til Azure AD** skal du angive legitimationsoplysningerne for din globale administratorkonto og derefter vælge **Næste**.

6. På siden **Bruger-logon** skal du **vælge Aktivér enkelt logon** og derefter vælge **Næste**.

7. På siden **Aktivér enkelt logon** skal du vælge **Angiv legitimationsoplysninger**.

8. I dialogboksen **Windows Sikkerhed** skal du angive **bruger1** og adgangskoden til brugerkontoen1, vælge **OK** og derefter vælge **Næste**.

9. På siden **Klar til konfiguration** skal du vælge **Konfigurer**.

10. På siden **Konfigurationen er** fuldført skal du vælge **Afslut**.

11. Fra Azure-portalen skal du i venstre rude vælge **Azure Active Directory** >  **Azure AD Forbind**. Kontrollér, at **funktionen Seamless single sign-on** vises som **Aktiveret**.

Dernæst skal du teste muligheden for at logge på dit abonnement med <strong>user1@testlab.</strong>\<*your public domain*> brugernavnet på brugerkontoen Bruger1.

1. Vælg ikonet Indstillinger i Internet Explorer på APP1, og vælg derefter **Internetindstillinger**.
 
2. Vælg **fanen Sikkerhed** under **Internetindstillinger** .

3. Vælg **Lokalt intranet**, og vælg derefter **Websteder**.

4. Vælg **Avanceret** **på lokalt** intranet.

5. I **Føj dette websted til zonen skal** du **angive https <span>://</span>autologon.microsoftazuread-sso.com** og vælge **AddCloseOKOK** >  >  > .

6. Log af, og log derefter på igen, denne gang med at angive en anden konto.

7. Når du bliver bedt om at logge på, <strong>skal du user1@testlab.</strong>\<*your public domain*> og vælg derefter **Næste**. Du skal logge på som Bruger1 uden at blive bedt om en adgangskode. Dette beviser, at Azure AD Seamless SSO fungerer.

Bemærk, at selvom User1 har domæneadministratortilladelser til TESTLAB AD DS domæne, så er det ikke en global administrator for Azure AD. Derfor kan du ikke se **ikonet Administrator** som en mulighed.

Her er din resulterende konfiguration:

![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Denne konfiguration består af:

- En Microsoft 365 E5 prøveversion eller betalte abonnementer med DNS-domænets testlab.\<*your domain name*> registreret.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere listen over konti og grupper fra Azure AD-lejeren for dit Microsoft 365-abonnement til TESTLAB AD DS domæne.
- Azure AD Seamless SSO er aktiveret, så computere på det simulerede intranet kan logge på Microsoft 365 i skyen uden at angive en adgangskode til brugerkontoen.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)