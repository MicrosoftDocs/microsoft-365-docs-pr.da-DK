---
title: Synkronisering af adgangskodehash for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/26/2020
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
- seo-marvel-apr2020
ms.assetid: ''
description: 'Oversigt: Konfigurer og demonstrer synkronisering af adgangskodehash, og log på for dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 91d4de08382149b5089f0c06295e77965ea022cf
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093805"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

Mange organisationer bruger Synkronisering af Azure AD-Forbind og adgangskodehash til at synkronisere kontosættet i deres AD DS-område (Active Directory i det lokale miljø Domain Services) til sættet af konti i Azure AD-lejeren for deres Microsoft 365-abonnement. 

I denne artikel beskrives det, hvordan du kan føje synkronisering af adgangskodehash til dit Microsoft 365 testmiljø, hvilket resulterer i denne konfiguration:
  
![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
Konfiguration af dette testmiljø omfatter tre faser:
- [Fase 1: Opret det Microsoft 365 simulerede virksomhedstestmiljø](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Fase 2: Opret og registrer testlab-domænet](#phase-2-create-and-register-the-testlab-domain)
- [Fase 3: Installér Azure AD-Forbind på APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Fase 1: Opret det Microsoft 365 simulerede virksomhedstestmiljø

Følg vejledningen i [simuleret basiskonfiguration for Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). Den resulterende konfiguration ser sådan ud:
  
![Den simulerede grundlæggende konfiguration af virksomheden.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- Et Microsoft 365 E5 prøveabonnement eller et betalt abonnement.
- Et forenklet organisationsintranet, der er forbundet til internettet, som består af de virtuelle DC1-, APP1- og CLIENT1-maskiner i et virtuelt Azure-netværk. DC1 er domænecontroller for testlab.<*dit offentlige domænenavn*> AD DS-domænet.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Fase 2: Opret og registrer testlab-domænet

I denne fase skal du tilføje et offentligt DNS-domæne og derefter føje det til dit abonnement.

Først skal du samarbejde med din offentlige DNS-registreringsudbyder om at oprette et nyt offentligt DNS-domænenavn, der er baseret på dit aktuelle domænenavn, og derefter føje det til dit abonnement. Vi anbefaler, at du bruger navnet **testlab.<*dit offentlige domæne*>**. Hvis dit offentlige domænenavn **f.eks. er <span>contoso.com</span>**, skal du tilføje det offentlige domænenavn: **<span>testlab.contoso.com</span>**.
  
Derefter skal du føje **testlab.<*dit offentlige domæne*>** til din Microsoft 365 prøveperiode eller dit betalte abonnement ved at gennemgå domæneregistreringsprocessen. Dette består i at føje yderligere DNS-poster til **testlab.<*dit offentlige domæne*>** . Du kan få flere oplysninger under [Føj et domæne til Microsoft 365](../admin/setup/add-domain.md).

Den resulterende konfiguration ser sådan ud:
  
![Registreringen af dit testlab-domænenavn.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Denne konfiguration består af:

- Et Microsoft 365 E5 prøveabonnement eller et betalt abonnement med DNS-domænet testlab.<*dit offentlige domænenavn*> registreret.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk.

Bemærk, hvordan testlab.<*dit offentlige domænenavn*> nu er:

- Understøttes af offentlige DNS-poster.
- Registreret i dine Microsoft 365 abonnementer.
- AD DS-domænet på det simulerede intranet.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>Fase 3: Installér Azure AD-Forbind på APP1

I denne fase skal du installere og konfigurere Azure AD Forbind-værktøjet på APP1 og derefter kontrollere, at det fungerer.
  
Først skal du installere og konfigurere Azure AD-Forbind på APP1.

1. Log på med din globale administratorkonto fra [Azure Portal](https://portal.azure.com), og opret derefter forbindelse til APP1 med kontoen TESTLABUser1\\.
    
2. Åbn en kommandoprompt på administratorniveau Windows PowerShell fra APP1-skrivebordet, og kør derefter disse kommandoer for at deaktivere Udvidet sikkerhed i Internet Explorer:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Vælg **Internet Explorer** på proceslinjen, og gå til [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. På siden Microsoft Azure Active Directory Forbind skal du vælge **Download** og derefter vælge **Kør**.
    
5. På siden **Velkommen til Azure AD Forbind** skal du vælge **Jeg accepterer** og derefter vælge **Fortsæt**.
    
6. På siden **Express Indstillinger** skal du vælge **Brug hurtigindstillinger**.
    
7. På siden **Forbind til Azure AD** skal du angive navnet på din globale administratorkonto i **Brugernavn,** angive adgangskoden i **Adgangskode** og derefter vælge **Næste**.
    
8. På siden **Forbind til AD DS** skal du angive **TESTLABUser1\\** i **Brugernavn,** angive adgangskoden i **Adgangskode** og derefter vælge **Næste**.
    
9. Vælg **Installér** på siden **Klar til at konfigurere**.
    
10. På siden **Konfiguration fuldført** skal du vælge **Afslut**.
    
11. I Internet Explorer skal du gå til Microsoft 365 Administration ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. Vælg **Brugere > Aktive brugere** i navigationsruden til venstre.
    
    Bemærk kontoen med navnet **User1**. Denne konto er fra domænet TESTLAB AD DS og er et bevis på, at katalogsynkronisering har fungeret.
    
13. Vælg **brugerkontoen User1** , og vælg derefter **Licenser og apps**.
    
14. I **Produktlicenser** skal du vælge din placering (hvis det er nødvendigt), deaktivere **Office 365 E5-licensen** og derefter aktivere **Microsoft 365 E5-licensen**. 

15. Vælg **Gem** nederst på siden, og vælg derefter **Luk**.
    
Test derefter muligheden for at logge på dit abonnement med **user1@testlab.<*brugernavnet til*> dit domænenavn** for brugerkontoen:

1. Fra APP1 skal du logge af og derefter logge på igen, denne gang angive en anden konto.

2. Når du bliver bedt om at angive et brugernavn og en adgangskode, skal **du angive user1@testlab.<*dit domænenavn*>** og adgangskoden user1. Du skal logge på som User1.
 
Bemærk, at selvom User1 har domæneadministratortilladelser til TESTLAB AD DS-domænet, er det ikke en global administrator. Du kan derfor ikke se **administratorikonet** som en mulighed. 

Den resulterende konfiguration ser sådan ud:

![Det simulerede virksomhedsmiljø med testmiljøet til synkronisering af adgangskodehash.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Denne konfiguration består af: 
  
- Microsoft 365 E5 eller Office 365 E5 prøveperiode eller betalte abonnementer med DNS-domænet TESTLAB.<*dit domænenavn*> registreret.
- Et forenklet organisationsintranet, der er forbundet til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-maskiner på et undernet i et virtuelt Azure-netværk. Azure AD Forbind kører på APP1 for jævnligt at synkronisere TESTLAB AD DS-domænet med Azure AD-lejeren for dit Microsoft 365 abonnement.
- User1-kontoen i DOMÆNET TESTLAB AD DS er blevet synkroniseret med Azure AD-lejeren.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)