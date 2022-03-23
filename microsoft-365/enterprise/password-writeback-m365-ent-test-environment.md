---
title: Tilbageførsel af adgangskode for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/22/2019
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
description: 'Oversigt: Konfigurer tilbageførsel af adgangskode for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 0c0660008aea4a676da4be3c13e8d5c15cb3a51d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589499"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Tilbageførsel af adgangskode for dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Brugerne kan bruge tilbageførsel af adgangskode til at opdatere deres adgangskoder via Azure Active Directory (Azure AD), som derefter replikeres til din lokale Active Directory-domæneservices (AD DS). Med tilbageførsel af adgangskode behøver brugerne ikke at opdatere deres adgangskoder via det lokale AD DS hvor deres oprindelige brugerkonti er gemt. Dette hjælper roamingbrugere eller eksterne brugere, der ikke har en fjernadgangsforbindelse til deres lokale netværk.

Denne artikel beskriver, hvordan du konfigurerer dit Microsoft 365 for tilbageførsel af adgangskode.

Konfiguration af testmiljøet for tilbageførsel af adgangskode omfatter to faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Aktivér tilbageførsel af adgangskode for testLAB AD DS domæne](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Følg først vejledningen i synkronisering af [adgangskodehash](password-hash-sync-m365-ent-test-environment.md). Den resulterende konfiguration ser sådan ud:
  
![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- En Microsoft 365 E5 prøveversion eller et betalt abonnement.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk.
- Azure AD Forbind app1 for at synkronisere TESTLAB AD DS-domænet med Azure AD-lejeren for dit Microsoft 365 abonnement.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Fase 2: Aktivér tilbageførsel af adgangskode for testLAB AD DS domæne

Først skal du konfigurere Bruger 1-kontoen med den globale administratorrolle.

1. Fra [Microsoft 365 Administration skal](https://portal.microsoft.com) du logge på med din globale administratorkonto.

2. Vælg **Aktive brugere**.
 
3. På siden **Aktive brugere** skal du vælge **brugerkontoen** brugerkontoen

4. I **ruden Bruger1** skal du **vælge Rediger** ud for **Roller**.

5. I **ruden Rediger brugerroller** for bruger1 skal du **vælge Global administrator**, **vælge Gem** og derefter vælge **Luk**.

Dernæst skal du konfigurere Bruger 1-kontoen med de sikkerhedsindstillinger, der giver den mulighed for at ændre adgangskoder på vegne af andre brugere i TESTLAB AD DS domæne.

1. Log på [med din](https://portal.azure.com) globale administratorkonto fra Azure-portalen, og opret derefter forbindelse til APP1 med TESTLAB\User1-kontoen.

2. På skrivebordet i APP1 skal du vælge **Start**, angive **aktiv** og derefter vælge **Active Directory-brugere og -computere**.

3. Vælg Vis på **menulinjen**. Hvis **Avancerede funktioner ikke** er aktiveret, skal du vælge den for at aktivere den.

4. I træruden skal du vælge og holde (eller højreklikke på) dit domæne nede, vælge **Egenskaber** og derefter vælge **fanen** Sikkerhed.

5. Vælg **Avanceret**.

6. På fanen **Tilladelser** skal du vælge **Tilføj**.

7. Vælg **Vælg en hovedstol**, **angiv Bruger1**, og vælg derefter **OK**.

8. I **Gælder for skal** du vælge **Objekter, der passer til brugeren**.

9. Under **Tilladelser skal** du vælge følgende:

    - **Skift adgangskode**
    - **Nulstil adgangskode**

10. Under **Egenskaber** skal du vælge følgende:
    - **Skriv lockoutTime**
    - **Skriv pwdLastSet**

11. Vælg **OK** tre gange for at gemme ændringerne.

12. Luk **Active Directory-brugere og -computere**.

Dernæst skal du konfigurere Azure AD Forbind APP1 for tilbageførsel af adgangskode.

1. Hvis det er nødvendigt, kan du oprette forbindelse til APP1 med TESTLAB\User1-kontoen.

2. På skrivebordet i APP1 skal du dobbeltklikke på **Azure AD Forbind**.

3. På **velkomstsiden skal** du vælge **Konfigurer**.

4. På siden **Yderligere opgaver** skal du vælge **Tilpas synkroniseringsindstillinger** og derefter vælge **Næste**.

5. På siden **Forbind til Azure AD** skal du angive legitimationsoplysningerne for din globale administratorkonto og derefter vælge **Næste**.

6. På siden **Forbind domæner og** **Domæne/OU-filtreringssider** skal du vælge **Næste**.

7. På siden **Valgfrie funktioner** skal du **vælge Tilbageførsel af** adgangskode og derefter vælge **Næste**.

8. På siden **Klar til konfiguration** skal du vælge **Konfigurer** og vente på, at processen afsluttes.

9. Når du ser konfigurationen færdig, skal du vælge **Afslut**.

Du er nu klar til at teste tilbageskrivning af adgangskoder for brugere på computere, der ikke har forbindelse til det virtuelle netværk på dit simulerede intranet.

Den resulterende konfiguration ser sådan ud:

![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Denne konfiguration består af:

- En Microsoft 365 E5 prøveversion eller betalte abonnementer med DNS-domænet TESTLAB.\<*your domain name*> registreret.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere listen over konti og grupper fra Azure AD-lejeren for dit Microsoft 365-abonnement til TESTLAB AD DS domæne.
- Tilbageførsel af adgangskode er aktiveret, så brugerne kan ændre deres adgangskoder via Azure AD uden at skulle have forbindelse til det forenklede intranet.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)