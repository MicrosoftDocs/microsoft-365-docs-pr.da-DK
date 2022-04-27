---
title: Pass-through-godkendelse for dit Microsoft 365 testmiljø
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
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Oversigt: Konfigurer pass-through-godkendelse for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: f6ad952ebde8556bd3c0c9b7e4e66c006b1c7578
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094366"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Pass-through-godkendelse for dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

Organisationer, der gerne vil bruge deres AD DS-infrastruktur (Active Directory i det lokale miljø Domain Services) direkte til godkendelse til Microsofts cloudbaserede tjenester og programmer, kan bruge pass-through-godkendelse. I denne artikel beskrives det, hvordan du kan konfigurere dit Microsoft 365 testmiljø til pass-through-godkendelse, hvilket resulterer i følgende konfiguration:
  
![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Der er to faser til konfiguration af dette testmiljø:

1.    Opret det Microsoft 365 simulerede virksomhedstestmiljø med synkronisering af adgangskodehash.
2.    Konfigurer Azure AD-Forbind på APP1 til pass-through-godkendelse.
    
![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Klik [her](../downloads/Microsoft365EnterpriseTLGStack.pdf) for at få et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg vejledningen i [synkronisering af adgangskodehash for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Her er din resulterende konfiguration.
  
![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af: 
  
- Microsoft 365 E5 prøveperiode eller betalt abonnement.
- Et forenklet organisationsintranet med forbindelse til internettet, der består af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk. Azure AD Forbind kører på APP1 for at synkronisere TESTLAB AD DS-domænet med Azure AD-lejeren for dit Microsoft 365 abonnement med jævne mellemrum.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Fase 2: Konfigurer Azure AD-Forbind på APP1 til pass-through-godkendelse

I denne fase skal du konfigurere Azure AD-Forbind på APP1 til at bruge pass-through-godkendelse og derefter kontrollere, at det fungerer.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurer Azure AD-Forbind på APP1

1.    Log på med din globale administratorkonto fra [Azure Portal](https://portal.azure.com), og opret derefter forbindelse til APP1 med TESTLAB\User1-kontoen.

2.    Kør Azure AD Forbind fra app1-skrivebordet.

3.    Klik på **Konfigurer** på **velkomstsiden**.

4.    På siden Yderligere opgaver skal du klikke på **Skift brugerlogon** og derefter klikke på **Næste**.

5.    På siden **Forbind til Azure AD** skal du skrive legitimationsoplysningerne til din globale administratorkonto og derefter klikke på **Næste**.

6.    Klik på **Pass-through-godkendelse** på siden **Brugerlogon**, og klik derefter på **Næste**.

7.    Klik på **Konfigurer** på siden **Klar til at konfigurere**.

8.    Klik på **Afslut** på siden **Konfiguration fuldført**.

9.    Klik på **Azure Active Directory > Azure AD-Forbind** i ruden til venstre i Azure Portal. Kontrollér, at funktionen **Pass-through-godkendelse** vises som **Aktiveret**.

10.    Klik på **Pass-through-godkendelse**. Ruden **Pass-through-godkendelse** viser de servere, hvor dine godkendelsesagenter er installeret. Du bør kunne se APP1 på listen. Luk ruden **Pass-through-godkendelse** .

Test derefter muligheden for at logge på dit abonnement med <strong>user1@testlab.</strong>\<your public domain> brugernavnet på user1-kontoen.

1. Fra APP1 skal du logge af og derefter logge på igen, denne gang angive en anden konto.

2. Når du bliver bedt om at angive et brugernavn og en adgangskode, skal du angive <strong>user1@testlab.</strong>\<your public domain> og bruger1-adgangskoden. Du skal logge på som User1.

Bemærk, at selvom User1 har domæneadministratortilladelser til TESTLAB AD DS-domænet, er det ikke en global administrator. Du kan derfor ikke se **administratorikonet** som en mulighed.

Her er din resulterende konfiguration:

![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Denne konfiguration består af:

- En Microsoft 365 E5 prøveperiode eller betalte abonnementer med DNS-domænetestlab.\<your domain name> Registreret.
- Et forenklet organisationsintranet med forbindelse til internettet, der består af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk. En godkendelsesagent kører på APP1 for at håndtere anmodninger om pass-through-godkendelse fra Azure AD-lejeren for dit Microsoft 365-abonnement.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)