---
title: Azure AD Seamless Single Sign-on til dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Oversigt: Konfigurer og test Azure AD Problemfri enkeltlogon til dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 2d6af0600044dea59cbcdd9ee51f76c061e3dcd7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093322"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>Azure AD Seamless Single Sign-on til dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

Azure AD Seamless Single Sign-On (Seamless SSO) logger automatisk på brugere, når de er på deres pc'er eller enheder, der har forbindelse til deres organisationsnetværk. Azure AD Seamless SSO giver brugerne nem adgang til cloudbaserede programmer, uden at de har brug for yderligere komponenter i det lokale miljø.

I denne artikel beskrives det, hvordan du konfigurerer dit Microsoft 365 testmiljø til Azure AD Seamless SSO.

Konfiguration af Azure AD Seamless SSO omfatter to faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Konfigurer Azure AD-Forbind på APP1 til Azure AD Seamless SSO](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg vejledningen i [synkronisering af adgangskodehash for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

Den resulterende konfiguration ser sådan ud:
  
![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- Et Microsoft 365 E5 prøveabonnement eller et betalt abonnement.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for jævnligt at synkronisere DOMÆNET TESTLAB Active Directory-domæneservices (AD DS) til Azure AD-lejeren for dit Microsoft 365 abonnement.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>Fase 2: Konfigurer Azure AD-Forbind på APP1 til Azure AD Seamless SSO

I denne fase skal du konfigurere Azure AD-Forbind på APP1 til Azure AD Seamless SSO og derefter kontrollere, at det fungerer.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurer Azure AD-Forbind på APP1

1. Log på med din globale administratorkonto fra [Azure Portal](https://portal.azure.com), og opret derefter forbindelse til APP1 med TESTLAB\User1-kontoen.

2. Kør Azure AD Forbind fra APP1-skrivebordet.

3. Vælg **Konfigurer** på **velkomstsiden**.

4. På siden **Yderligere opgaver** skal du vælge **Skift brugerlogon** og derefter vælge **Næste**.

5. Angiv legitimationsoplysningerne for din globale administratorkonto **på siden Forbind til Azure AD**, og vælg derefter **Næste**.

6. På siden **Brugerlogon** skal du vælge **Aktivér enkeltlogon** og derefter vælge **Næste**.

7. På siden **Aktivér enkeltlogon** skal du vælge **Angiv legitimationsoplysninger**.

8. I dialogboksen **Windows Sikkerhed** skal du angive **user1** og adgangskoden for brugerkontoen, vælge **OK** og derefter vælge **Næste**.

9. På siden **Klar til konfiguration** skal du vælge **Konfigurer**.

10. På siden **Konfiguration fuldført** skal du vælge **Afslut**.

11. Vælg **Azure Active Directory** **Azure AD-Forbind** >  i ruden til venstre i Azure Portal. Kontrollér, at funktionen **Problemfri enkeltlogon** vises som **Aktiveret**.

Test derefter muligheden for at logge på dit abonnement med <strong>user1@testlab.</strong>\<*your public domain*> brugernavnet på user1-kontoen.

1. Fra Internet Explorer på APP1 skal du vælge ikonet Indstillinger og derefter vælge **Internetindstillinger**.
 
2. Under **Internetindstillinger** skal du vælge fanen **Sikkerhed** .

3. Vælg **Lokalt intranet**, og vælg derefter **Websteder**.

4. Vælg **Avanceret** på **Lokalt intranet**.

5. I **Føj dette websted til zonen** skal du angive **https <span>://</span>autologon.microsoftazuread-sso.com** og vælge **TilføjCloseOKOK** >  >  > .

6. Log af, og log derefter på igen. Denne gang skal du angive en anden konto.

7. Når du bliver bedt om at logge på, skal <strong>du angive user1@testlab.</strong>\<*your public domain*> navn, og vælg derefter **Næste**. Du skal logge på som User1 uden at blive bedt om at angive en adgangskode. Dette beviser, at Azure AD Seamless SSO fungerer.

Bemærk, at selvom User1 har domæneadministratortilladelser til TESTLAB AD DS-domænet, er det ikke en global administrator for Azure AD. Du kan derfor ikke se **administratorikonet** som en mulighed.

Her er din resulterende konfiguration:

![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Denne konfiguration består af:

- En Microsoft 365 E5 prøveperiode eller betalte abonnementer med DNS-domænetestlab.\<*your domain name*> Registreret.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere listen over konti og grupper fra Azure AD-lejeren for dit Microsoft 365 abonnement på TESTLAB AD DS-domænet.
- Azure AD Seamless SSO er aktiveret, så computere på det simulerede intranet kan logge på Microsoft 365 cloudressourcer uden at angive en adgangskode til en brugerkonto.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)