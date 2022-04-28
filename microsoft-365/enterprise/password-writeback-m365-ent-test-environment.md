---
title: Tilbageførsel af adgangskode for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: 0477e2200db7252dcce4351b2f96298e075f3b29
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091099"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Tilbageførsel af adgangskode for dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Brugerne kan bruge tilbageførsel af adgangskoder til at opdatere deres adgangskoder via Azure Active Directory (Azure AD), som derefter replikeres til din lokale Active Directory-domæneservices (AD DS). Med tilbageførsel af adgangskode behøver brugerne ikke at opdatere deres adgangskoder via AD DS i det lokale miljø, hvor deres oprindelige brugerkonti er gemt. Dette hjælper roaming- eller fjernbrugere, der ikke har en fjernadgangsforbindelse til deres lokale netværk.

I denne artikel beskrives det, hvordan du konfigurerer dit Microsoft 365 testmiljø til tilbageførsel af adgangskode.

Konfiguration af testmiljøet til tilbageførsel af adgangskode omfatter to faser:
- [Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Fase 2: Aktivér tilbageførsel af adgangskode for TESTLAB AD DS-domænet](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Fase 1: Konfigurer synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

Først skal du følge vejledningen i [synkronisering af adgangskodehash](password-hash-sync-m365-ent-test-environment.md). Den resulterende konfiguration ser sådan ud:
  
![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- Et Microsoft 365 E5 prøveabonnement eller et betalt abonnement.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere TESTLAB AD DS-domænet med Azure AD-lejeren for dit Microsoft 365 abonnement.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Fase 2: Aktivér tilbageførsel af adgangskode for TESTLAB AD DS-domænet

Konfigurer først bruger 1-kontoen med rollen global administrator.

1. Log på med din globale administratorkonto fra [Microsoft 365 Administration](https://portal.microsoft.com).

2. Vælg **Aktive brugere**.
 
3. På siden **Aktive brugere** skal du vælge **brugerkontoen1** ,

4. I ruden **bruger1** skal du vælge **Rediger** ud for **Roller**.

5. I ruden **Rediger brugerroller** for bruger1 skal du vælge **Global administrator**, vælge **Gem** og derefter vælge **Luk**.

Konfigurer derefter bruger 1-kontoen med de sikkerhedsindstillinger, der gør det muligt for den at ændre adgangskoder på vegne af andre brugere i TESTLAB AD DS-domænet.

1. Log på med din globale administratorkonto fra [Azure Portal](https://portal.azure.com), og opret derefter forbindelse til APP1 med TESTLAB\User1-kontoen.

2. Vælg **Start** på skrivebordet i APP1, angiv **aktiv**, og vælg derefter **Active Directory-brugere og -computere**.

3. Vælg **Vis** på menulinjen. Hvis **Avancerede funktioner** ikke er aktiveret, skal du vælge den for at aktivere den.

4. I træruden skal du vælge og holde (eller højreklikke) på dit domæne, vælge **Egenskaber** og derefter vælge fanen **Sikkerhed** .

5. Vælg **Avanceret**.

6. Vælg **Tilføj** under fanen **Tilladelser**.

7. **Vælg Vælg en principal**, angiv **User1**, og vælg derefter **OK**.

8. I **Gælder for** skal du vælge **Underordnede brugerobjekter**.

9. Under **Tilladelser** skal du vælge følgende:

    - **Skift adgangskode**
    - **Nulstil adgangskode**

10. Under **Egenskaber** skal du vælge følgende:
    - **Skrivning af lockoutTime**
    - **Skriv pwdLastSet**

11. Vælg **OK** tre gange for at gemme ændringerne.

12. Luk **Active Directory-brugere og -computere**.

Konfigurer derefter Azure AD-Forbind på APP1 til tilbageførsel af adgangskode.

1. Hvis det er nødvendigt, skal du oprette forbindelse til APP1 med TESTLAB\User1-kontoen.

2. Dobbeltklik på **Azure AD Forbind** på skrivebordet i APP1.

3. Vælg **Konfigurer** på **velkomstsiden**.

4. På siden **Yderligere opgaver** skal du vælge **Tilpas synkroniseringsindstillinger** og derefter vælge **Næste**.

5. Angiv legitimationsoplysningerne for din globale administratorkonto **på siden Forbind til Azure AD**, og vælg derefter **Næste**.

6. Vælg **Næste** **på de Forbind mapper** og **domæne-/organisationsfiltreringssider**.

7. På siden **Valgfrie funktioner** skal du vælge **Tilbageførsel af adgangskode** og derefter vælge **Næste**.

8. På siden **Klar til at konfigurere** skal du vælge **Konfigurer** og vente på, at processen afsluttes.

9. Når du ser, at konfigurationen er færdig, skal du vælge **Afslut**.

Du er nu klar til at teste tilbageførsel af adgangskode for brugere på computere, der ikke har forbindelse til det virtuelle netværk på dit simulerede intranet.

Den resulterende konfiguration ser sådan ud:

![Den simulerede virksomhed med pass-through-godkendelsestestmiljø.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Denne konfiguration består af:

- En Microsoft 365 E5 prøveperiode eller betalte abonnementer med DNS-domænet TESTLAB.\<*your domain name*> Registreret.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk.
- Azure AD Forbind kører på APP1 for at synkronisere listen over konti og grupper fra Azure AD-lejeren for dit Microsoft 365 abonnement på TESTLAB AD DS-domænet.
- Tilbageførsel af adgangskode er aktiveret, så brugerne kan ændre deres adgangskoder via Azure AD uden at skulle have forbindelse til det forenklede intranet.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)