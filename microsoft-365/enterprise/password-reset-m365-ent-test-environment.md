---
title: Nulstilling af adgangskode for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/13/2019
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
description: 'Oversigt: Konfigurer og test nulstilling af adgangskode for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 4e68372aee44887641d626c3e3667adbdedd5a1e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095614"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Nulstilling af adgangskode for dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Azure Active Directory (Azure AD) selvbetjent nulstilling af adgangskode (SSPR) giver brugerne mulighed for at nulstille eller låse deres adgangskoder eller konti op.

I denne artikel beskrives det, hvordan du konfigurerer og tester nulstilling af adgangskode i dit Microsoft 365 testmiljø.

Konfiguration af SSPR omfatter tre faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Aktivér tilbageførsel af adgangskode](#phase-2-enable-password-writeback)
- [Fase 3: Konfigurer og test nulstilling af adgangskode](#phase-3-configure-and-test-password-reset)
    
![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Først skal du følge vejledningen i [synkronisering af adgangskodehash](password-hash-sync-m365-ent-test-environment.md). 

Den resulterende konfiguration ser sådan ud:
  
![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- Et Microsoft 365 E5 prøveabonnement eller et betalt abonnement.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere DOMÆNET TESTLAB Active Directory-domæneservices (AD DS) til Azure AD-lejeren for dit Microsoft 365-abonnement.

## <a name="phase-2-enable-password-writeback"></a>Fase 2: Aktivér tilbageførsel af adgangskode

Følg instruktionerne i [fase 2 i testvejledningen til tilbageskrivning af adgangskode](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

Du skal have aktiveret tilbageførsel af adgangskode for at bruge nulstilling af adgangskode.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Fase 3: Konfigurer og test nulstilling af adgangskode

I denne fase skal du konfigurere nulstilling af adgangskode i Azure AD-lejeren via gruppemedlemskab og derefter bekræfte, at det fungerer.

Først skal du aktivere nulstilling af adgangskode for kontiene i en bestemt Azure AD-gruppe.

1. Åbn fra en privat forekomst af din browser, [https://portal.azure.com](https://portal.azure.com)og log derefter på med legitimationsoplysningerne for din globale administratorkonto.
2. I Azure Portal skal du vælge **Azure Active Directory** >  **GrupperNy** >  **gruppe**.
3. Angiv **Gruppetype** til **Sikkerhed**, **Gruppenavn** til **PWReset** og **Medlemskabstype** til **Tildelt**.
4. Vælg **Medlemmer**, find og vælg **Bruger 3**, vælg **Vælg**, og vælg derefter **Opret**.
5. Luk ruden **Grupper** .
6. I ruden Azure Active Directory skal du vælge **Nulstil adgangskode** i venstre navigationsrude.
7. Vælg **Valgt** under indstillingen **Selvbetjent nulstilling af adgangskode aktiveret** i ruden **Egenskaber for nulstilling** af adgangskode.
8. Vælg **Vælg gruppe**, vælg gruppen **PWReset**, og vælg derefter **VælgGem** > .
9. Luk forekomsten af den private browser.

Test derefter nulstilling af adgangskode for bruger 3-kontoen.

1. Åbn en ny privat browserforekomst, og gå til [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. Log på med legitimationsoplysningerne for bruger 3-kontoen.
1. Under **Flere oplysninger kræves** skal du vælge **Næste**. 
1. I **Tab ikke adgangen til din konto** skal du angive godkendelsestelefonen til dit mobiltelefonnummer og godkendelsesmailen til din arbejds- eller personlige mailkonto.
1. Når begge er bekræftet, skal du vælge **Ser godt ud** og derefter lukke den private forekomst af browseren.
1. I en ny privat browserforekomst skal du gå til [https://aka.ms/sspr](https://aka.ms/sspr).
1. Angiv kontonavnet Bruger 3, angiv tegnene fra CAPTCHA, og vælg derefter **Næste**.
1. For **bekræftelsestrin 1** skal du vælge **Send mail til min alternative mail** og derefter vælge **Mail**. Når du modtager mailen, skal du angive bekræftelseskoden og derefter vælge **Næste**.
1. I **Kom tilbage til din konto** skal du angive en ny adgangskode til bruger 3-kontoen og derefter vælge **Udfør**. Bemærk den ændrede adgangskode for bruger 3-kontoen, og gem den et sikkert sted.
1. Gå til [https://admin.microsoft.com](https://admin.microsoft.com)i en separat fane i den samme browser, og log derefter på med kontonavnet Bruger 3 og dens nye adgangskode. Du bør kunne se siden **Microsoft Office startside**.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)