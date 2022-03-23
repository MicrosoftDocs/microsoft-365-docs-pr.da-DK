---
title: Nulstilling af adgangskode for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: 9aa55f42ca295577bf3b1c81ee54b1160adf3d27
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589092"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Nulstilling af adgangskode for dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Azure Active Directory (Azure AD) giver SSPR (Self-Service Password Reset) brugerne mulighed for at nulstille eller låse op for deres adgangskoder eller konti.

Denne artikel beskriver, hvordan du konfigurerer og tester nulstilling af adgangskode i dit Microsoft 365 testmiljø.

Konfiguration af SSPR omfatter tre faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Aktivér tilbageførsel af adgangskode](#phase-2-enable-password-writeback)
- [Fase 3: Konfigurer og test nulstilling af adgangskode](#phase-3-configure-and-test-password-reset)
    
![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg først vejledningen i synkronisering af [adgangskodehash](password-hash-sync-m365-ent-test-environment.md). 

Den resulterende konfiguration ser sådan ud:
  
![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- En Microsoft 365 E5 prøveversion eller et betalt abonnement.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere TESTLAB Active Directory-domæneservices-domænet (AD DS) med Azure AD-lejeren for dit Microsoft 365-abonnement.

## <a name="phase-2-enable-password-writeback"></a>Fase 2: Aktivér tilbageførsel af adgangskode

Følg vejledningen i fase [2 i testlaboratorvejledningen til tilbageførsel af adgangskode](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

Du skal have aktiveret tilbageførsel af adgangskode for at bruge nulstilling af adgangskode.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Fase 3: Konfigurer og test nulstilling af adgangskode

I denne fase skal du konfigurere nulstilling af adgangskode i Azure AD-lejeren via gruppemedlemskab og derefter kontrollere, at det fungerer.

Først skal du aktivere nulstilling af adgangskode for kontiene i en bestemt Azure AD-gruppe.

1. Fra en privat forekomst af din browser skal du [https://portal.azure.com](https://portal.azure.com)åbne og derefter logge på med legitimationsoplysningerne fra din globale administratorkonto.
2. I Azure-portalen skal du **vælge Azure Active Directory** >  **GroupsNew-gruppe** > .
3. Angiv **Gruppetype til** **Sikkerhed**, **Gruppenavn** til **PWReset** og **medlemskabstypen** **tildelt.**
4. Vælg **Medlemmer**, find og vælg **Bruger 3**, vælg **Vælg**, og vælg derefter **Opret**.
5. Luk **ruden** Grupper.
6. I ruden Azure Active Directory skal du vælge **Nulstil adgangskode** i venstre navigationsrude.
7. I **ruden Egenskaber for nulstilling af** adgangskode under indstillingen Selvbetjeningsindstillingen **Nulstilling af adgangskode aktiveret** skal du vælge **Markeret**.
8. Vælg **Vælg gruppe**, vælg **gruppen PWReset**, og vælg derefter **SelectSave** > .
9. Luk den private browserforekomst.

Dernæst skal du teste nulstilling af adgangskode for Bruger 3-kontoen.

1. Åbn en ny privat browserforekomst, og gå til [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. Log på med legitimationsoplysningerne til Bruger 3-kontoen.
1. I **Flere påkrævede oplysninger skal** du vælge **Næste**. 
1. I **Mister ikke adgang til** din konto skal du indstille godkendelsestelefonen til dit mobiltelefonnummer og godkendelsesmailen til din arbejds- eller personlige mailkonto.
1. Når begge er bekræftet, skal **du vælge Ser** godt ud og derefter lukke den private forekomst af browseren.
1. I en ny privat browserforekomst skal du gå til [https://aka.ms/sspr](https://aka.ms/sspr).
1. Angiv bruger 3-kontonavnet, indtast tegnene fra CAPTCHA, og vælg derefter **Næste**.
1. Hvis du **vil bekræfte trin 1**, skal **du vælge Send min alternative mail** via mail og derefter vælge **Mail**. Når du modtager mailen, skal du angive bekræftelseskoden og derefter vælge **Næste**.
1. Gå **tilbage til din konto**, angiv en ny adgangskode til Bruger 3-kontoen, og vælg derefter **Udfør**. Bemærk den ændrede adgangskode for Bruger 3-kontoen, og gem den et sikkert sted.
1. Gå til i en separat fane i den samme browser, [https://admin.microsoft.com](https://admin.microsoft.com)og log derefter på med bruger 3-kontonavnet og den nye adgangskode. Du bør få vist **Microsoft Office startsiden**.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)