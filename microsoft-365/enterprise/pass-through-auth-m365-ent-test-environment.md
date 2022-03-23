---
title: Pass-through-godkendelse for dit Microsoft 365 testmiljø
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
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'Oversigt: Konfigurer pass-through-godkendelse for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: dcc23662683ffaf65a0ec5fa3698f729dc215af7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587249"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>Pass-through-godkendelse for dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

Organisationer, der ønsker at bruge deres lokale Active Directory-domæneservices(AD DS)-infrastruktur til godkendelse til Microsofts skybaserede tjenester og programmer, kan bruge pass-through-godkendelse. I denne artikel beskrives det, hvordan du kan konfigurere Microsoft 365 testmiljø til pass-through-godkendelse, hvilket resulterer i følgende konfiguration:
  
![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
Der er to faser i konfigurationen af dette testmiljø:

1.    Opret det Microsoft 365 simulerede virksomhedstestmiljø med synkronisering af adgangskodehash.
2.    Konfigurer Azure AD Forbind APP1 til pass-through-godkendelse.
    
![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Klik [her](../downloads/Microsoft365EnterpriseTLGStack.pdf) for at få et visuelt kort over alle artikler i Microsoft 365 for Enterprise Test Lab Guide-stak.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg vejledningen i synkronisering [af adgangskodehash for Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Her er din resulterende konfiguration.
  
![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af: 
  
- Microsoft 365 E5 prøveversion eller betalt abonnement.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk. Azure AD Forbind kører på APP1 for med jævne mellemrum at synkronisere TESTLAB AD DS-domænet med Azure AD-lejeren for dit Microsoft 365-abonnement.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>Fase 2: Konfigurer Azure AD-Forbind APP1 til pass-through-godkendelse

I denne fase skal du konfigurere Azure AD Forbind APP1 til at bruge pass-through-godkendelse og derefter kontrollere, at det virker.

### <a name="configure-azure-ad-connect-on-app1"></a>Konfigurere Azure AD Forbind på APP1

1.    Log på [med din](https://portal.azure.com) globale administratorkonto fra Azure-portalen, og opret derefter forbindelse til APP1 med TESTLAB\User1-kontoen.

2.    Fra skrivebordet i APP1 skal du køre Azure AD Forbind.

3.    Klik på **Konfigurer på** siden **Velkommen**.

4.    Klik på Skift bruger logon på **siden Yderligere opgaver**, og klik derefter på **Næste**.

5.    På siden **Forbind til Azure AD** skal du skrive legitimationsoplysningerne for din globale administratorkonto og derefter klikke på **Næste**.

6.    Klik på **Pass-through-godkendelse** på **siden Bruger login**, og klik derefter på **Næste**.

7.    Klik på **Konfigurer på siden** Klar til **konfiguration**.

8.    Klik på **Afslut på** siden **Konfigurationen er fuldført**.

9.    Fra Azure-portalen skal du i venstre rude klikke på **Azure Active Directory > Azure AD Forbind**. Kontrollér, at **Pass-through-godkendelsesfunktionen** vises som **Aktiveret**.

10.    Klik **på Pass-through-godkendelse**. **Ruden Pass-through-godkendelse** viser de servere, hvor dine godkendelsesagenter er installeret. Du bør kunne se APP1 på listen. Luk **ruden Pass-through-godkendelse** .

Dernæst skal du teste muligheden for at logge på dit abonnement med <strong>user1@testlab.</strong>\<your public domain> brugernavnet på brugerkontoen Bruger1.

1. Log af app1, og log på igen, denne gang med en anden konto.

2. Når du bliver bedt om at angive et brugernavn og en adgangskode, <strong>skal user1@testlab.</strong>\<your public domain> og brugerens1 adgangskode. Du skal logge på som Bruger1.

Bemærk, at selvom Bruger1 har domæneadministratortilladelser til TESTLAB AD DS domæne, er det ikke en global administrator. Derfor kan du ikke se **ikonet Administrator** som en mulighed.

Her er din resulterende konfiguration:

![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
Denne konfiguration består af:

- En Microsoft 365 E5 prøveversion eller betalte abonnementer med DNS-domænets testlab.\<your domain name> registreret.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk. En godkendelsesagent kører på APP1 for at håndtere anmodninger om pass-through-godkendelse fra Azure AD-lejeren i Microsoft 365 abonnement.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)