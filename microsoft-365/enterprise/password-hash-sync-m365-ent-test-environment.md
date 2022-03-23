---
title: Synkronisering af adgangskodehash for dit Microsoft 365 testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Konfigurer og vis synkronisering af adgangskodehash og logon til dit Microsoft 365 testmiljø.'
ms.openlocfilehash: 746a0e1112df6ebf99569bfed58d08d0a4519d7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588889"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Synkronisering af adgangskodehash for dit Microsoft 365 testmiljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

Mange organisationer bruger Azure AD Forbind og synkronisering af adgangskodehash til at synkronisere sættet af konti i deres lokale Active Directory-domæneservices-skov (AD DS) til sættet af konti i Azure AD-lejeren for deres Microsoft 365-abonnement. 

I denne artikel beskrives det, hvordan du kan føje synkronisering af adgangskodehash Microsoft 365 dit testmiljø, hvilket resulterer i denne konfiguration:
  
![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
Konfiguration af dette testmiljø omfatter tre faser:
- [Fase 1: Opret det Microsoft 365 simulerede virksomhedstestmiljø](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [Fase 2: Opret og registrer testlab-domænet](#phase-2-create-and-register-the-testlab-domain)
- [Fase 3: Installer Azure AD Forbind på APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>Fase 1: Opret det Microsoft 365 simulerede virksomhedstestmiljø

Følg vejledningen i [simuleret virksomhedsbasekonfiguration for Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). Den resulterende konfiguration ser sådan ud:
  
![Den simulerede virksomhedsbasekonfiguration.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
Denne konfiguration består af:
  
- En Microsoft 365 E5 prøveversion eller et betalt abonnement.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere i et virtuelt Azure-netværk. DC1 er en domænecontroller til testlab.<*dit offentlige domænenavn> AD DS* domæne.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>Fase 2: Opret og registrer testlab-domænet

I denne fase skal du tilføje et offentligt DNS-domæne og derefter føje det til dit abonnement.

Du skal først samarbejde med din offentlige DNS-registreringsudbyder om at oprette et nyt offentligt DNS-domænenavn, som er baseret på dit aktuelle domænenavn, og derefter føje det til dit abonnement. Vi anbefaler, at du **bruger name testlab.<*dit offentlige domæne*>**. Hvis dit offentlige domænenavn f.eks. er **<span>contoso.com</span>**, skal du tilføje det offentlige domænenavn: **<span>testlab.contoso.com</span>**.
  
Derefter skal du føje **testlab.<>** dit offentlige domæne til dit Microsoft 365-prøveabonnement eller betalte abonnement ved at gå gennem domæneregistreringsprocessen. Denne består i at føje yderligere DNS-poster **til testlab.<*dit offentlige domæne*>** . Få mere at vide under [Føj et domæne til Microsoft 365](../admin/setup/add-domain.md).

Den resulterende konfiguration ser sådan ud:
  
![Registrering af dit testlab-domænenavn.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
Denne konfiguration består af:

- En Microsoft 365 E5 prøveversion eller et betalt abonnement med DNS domain testlab.<*dit offentlige domænenavn>* registreret.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk.

Bemærk, hvordan testlab.<*dit offentlige domænenavn>* nu:

- Understøttes af offentlige DNS-poster.
- Registreret i dine Microsoft 365-abonnementer.
- Det AD DS domæne på dit simulerede intranet.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>Fase 3: Installer Azure AD Forbind på APP1

I denne fase skal du installere og konfigurere Værktøjet Azure AD Forbind APP1 og derefter bekræfte, at det fungerer.
  
Først skal du installere og konfigurere Azure AD Forbind på APP1.

1. Log på [med din](https://portal.azure.com) globale administratorkonto fra Azure-portalen, og opret derefter forbindelse til APP1 med TESTLABUser1-kontoen\\.
    
2. På skrivebordet i APP1 skal du åbne en administratorniveau Windows PowerShell kommandoprompten og derefter køre disse kommandoer for at deaktivere Udvidet sikkerhed i Internet Explorer:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. Vælg **Internet Explorer** på proceslinjen, og gå til [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. På siden Microsoft Azure Active Directory Forbind skal du vælge **Download** og derefter vælge **Kør**.
    
5. På siden **Velkommen til Azure AD Forbind** skal du **vælge Jeg accepterer** og derefter vælge **Fortsæt**.
    
6. På siden **Express Indstillinger** skal du vælge **Brug hurtig konfiguration**.
    
7. På siden **Forbind Azure AD** skal du angive navnet på din globale administratorkonto i **Brugernavn,** angive adgangskoden i **Adgangskode og derefter** vælge **Næste**.
    
8. På siden **Forbind til AD DS** skal du skrive **TESTLABUser1\\** i **Brugernavn,** angive adgangskoden i **Adgangskode og derefter** vælge **Næste**.
    
9. På siden **Klar til at konfigurere** skal du vælge **Installér**.
    
10. På siden **Konfigurationen er** fuldført skal du vælge **Afslut**.
    
11. I Internet Explorer skal du gå til Microsoft 365 Administration ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. I venstre navigationsrude skal du **vælge Brugere > Aktive brugere**.
    
    Bemærk kontoen **Bruger1**. Denne konto er fra testlab-AD DS og er et bevis på, at katalogsynkronisering har fungeret.
    
13. Vælg **Brugerkonto1-kontoen** , og vælg derefter **Licenser og apps**.
    
14. I **Produktlicenser** skal du vælge din placering (hvis det er nødvendigt), **deaktivere Office 365 E5** licensen og derefter aktivere **Microsoft 365 E5** licens. 

15. Vælg **Gem** nederst på siden, og vælg derefter **Luk**.
    
Dernæst skal du teste muligheden for at logge på dit abonnement med **user1@testlab.<>** brugernavnet på User1-kontoen:

1. Log af app1, og log på igen, denne gang med en anden konto.

2. Når du bliver bedt om at angive et brugernavn og **en adgangskode, user1@testlab.<*dit domænenavn*>** og brugerens1-adgangskode. Du skal logge på som Bruger1.
 
Bemærk, at selvom Bruger1 har domæneadministratortilladelser til TESTLAB AD DS domæne, er det ikke en global administrator. Derfor kan du ikke se **ikonet Administrator** som en mulighed. 

Den resulterende konfiguration ser sådan ud:

![Den simulerede virksomhed med testmiljø til synkronisering af adgangskodehash.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

Denne konfiguration består af: 
  
- Microsoft 365 E5 eller Office 365 E5 eller betalte abonnementer med DNS-domænet TESTLAB.<*dit domænenavn>* registreret.
- Et forenklet intranet for organisationen, der har forbindelse til internettet, bestående af de virtuelle DC1-, APP1- og CLIENT1-computere på et undernet af et virtuelt Azure-netværk. Azure AD Forbind app1 for med jævne mellemrum at synkronisere TESTLAB AD DS-domænet med Azure AD-lejeren for dit Microsoft 365 abonnement.
- Brugerkontoen1 i TESTLAB-AD DS domæne er blevet synkroniseret med Azure AD-lejeren.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)