---
title: Installér Microsoft 365 katalogsynkronisering i Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Få mere at vide om, hvordan du installerer Azure AD Forbind på en virtuel maskine i Azure for at synkronisere konti mellem dit lokale katalog og Azure AD-lejeren.
ms.openlocfilehash: 6535b46fb360cf326d8daf07662cb7fa366ae6c2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590354"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Installér Microsoft 365 katalogsynkronisering i Microsoft Azure

Azure Active Directory (Azure AD) Forbind (tidligere kendt som værktøjet Katalogsynkronisering, Katalogsynkronisering eller DirSync.exe-værktøjet) er et program, som du installerer på en domæneforenet server til synkronisering af dine lokale Active Directory-domæneservices-brugere (AD DS) med Azure AD-lejeren for dit Microsoft 365-abonnement. Microsoft 365 bruger Azure AD som katalogtjeneste. Dit Microsoft 365-abonnement omfatter en Azure AD-lejer. Denne lejer kan også bruges til administration af organisationens identiteter med andre skyarbejdsbelastninger, herunder andre SaaS-programmer og -apps i Azure.

Du kan installere Azure AD Forbind på en lokal server, men du kan også installere det på en virtuel maskine i Azure af følgende årsager:
  
- Du kan klargøre og konfigurere skybaserede servere hurtigere, hvilket gør tjenesterne hurtigere tilgængelige for dine brugere.
- Azure tilbyder bedre tilgængelighed af websteder med mindre indsats.
- Du kan reducere antallet af lokale servere i organisationen.

Denne løsning kræver forbindelse mellem dit lokale netværk og dit virtuelle Azure-netværk. Du kan finde flere [oplysninger Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> I denne artikel beskrives synkronisering af et enkelt domæne i en enkelt skov. Azure AD Forbind synkroniserer alle AD DS domæner i dit Active Directory-område med Microsoft 365. Hvis du har flere Active [Directory-skove](/azure/active-directory/hybrid/whatis-hybrid-identity), der skal synkroniseres Microsoft 365, skal du se Katalogsynkronisering med flere skove Sign-On scenarie. 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Oversigt over installation Microsoft 365 katalogsynkronisering i Azure

Følgende diagram viser Azure AD-Forbind der kører på en virtuel maskine i Azure (katalogsynkroniseringsserveren), der synkroniserer et lokalt AD DS til et Microsoft 365 abonnement.
  
![Azure AD Forbind på en virtuel maskine i Azure synkroniserer lokale konti til Azure AD-lejeren for et Microsoft 365-abonnement med trafikflow.](../media/CP-DirSyncOverview.png)
  
I diagrammet er der to netværk, der er forbundet via et websted-til-websted-VPN eller ExpressRoute-forbindelse. Der er et lokalt netværk, hvor AD DS-domænecontrollere er placeret, og der er et virtuelt Azure-netværk med en katalogsynkroniseringsserver, som er en virtuel maskine, der kører [Azure AD Forbind](https://www.microsoft.com/download/details.aspx?id=47594). Der er to primære trafikflows, der stammer fra katalogsynkroniseringsserveren:
  
-  Azure AD Forbind en domænecontroller på det lokale netværk for ændringer af konti og adgangskoder.
-  Azure AD Forbind sender ændringerne til konti og adgangskoder til Azure AD-forekomsten af dit Microsoft 365 abonnement. Da katalogsynkroniseringsserveren findes i en udvidet del af dit lokale netværk, sendes disse ændringer via det lokale netværks proxyserver.
    
> [!NOTE]
> Denne løsning beskriver synkronisering af et enkelt Active Directory-domæne i et enkelt Active Directory-område. Azure AD Forbind synkroniserer alle Active Directory-domæner i dit Active Directory-område med Microsoft 365. Hvis du har flere Active [Directory-skove](/azure/active-directory/hybrid/whatis-hybrid-identity), der skal synkroniseres Microsoft 365, skal du se Katalogsynkronisering med flere skove Sign-On scenarie. 
  
Der er to overordnede trin, når du installerer denne løsning:
  
1. Opret et virtuelt Azure-netværk, og opret en websted-til-websted-VPN-forbindelse til dit lokale netværk. Du kan finde flere [oplysninger Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. [Installér Azure AD Forbind](https://www.microsoft.com/download/details.aspx?id=47594) på en domæne forbundet virtuel maskine i Azure, og synkroniser derefter de lokale AD DS for at Microsoft 365. Dette omfatter:
    
    Oprettelse af en Virtuel Azure-maskine til at køre Azure AD Forbind.
    
    Installation og konfiguration af [Azure AD-Forbind](https://www.microsoft.com/download/details.aspx?id=47594).
    
    Konfiguration af Azure AD Forbind kræver legitimationsoplysninger (brugernavn og adgangskode) for en Azure AD-administratorkonto og en AD DS virksomhedsadministratorkonto. Azure AD Forbind køre med det samme og løbende for at synkronisere de lokale AD DS til Microsoft 365.
    
Før du installerer denne løsning i produktion, kan du bruge instruktionerne i Den simulerede [virksomhedsbasekonfiguration](simulated-ent-base-configuration-microsoft-365-enterprise.md) til at konfigurere denne konfiguration som en koncept proof of concept, til demonstrationer eller til at eksperimentere.
  
> [!IMPORTANT]
> Når Azure AD Forbind konfigurationen er fuldført, gemmes legitimationsoplysningerne AD DS virksomhedens administratorkonto ikke. 
  
> [!NOTE]
> Denne løsning beskriver synkronisering af en enkelt AD DS til Microsoft 365. Den topologi, der er nævnt i denne artikel, repræsenterer kun én måde at implementere denne løsning på. Din organisations topologi kan variere afhængigt af dine unikke netværkskrav og sikkerhedsovervejelser. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Planlæg at hoste en katalogsynkroniseringsserver til Microsoft 365 i Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Forudsætninger

Før du begynder, skal du gennemgå følgende forudsætninger for denne løsning:
  
- Gennemgå det relaterede planlægningsindhold i [Planlæg dit virtuelle Azure-netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- Sørg for, at du [opfylder alle forudsætninger](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for konfiguration af det virtuelle Azure-netværk.
    
- Har et Microsoft 365, der omfatter Active Directory-integrationsfunktionen. Du kan finde Microsoft 365 om abonnementer på siden [Microsoft 365 abonnement](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- Klargør én Azure Virtual Machine, der kører Azure AD Forbind til at synkronisere din lokale AD DS med Microsoft 365.
    
    Du skal have legitimationsoplysningerne (navne og adgangskoder) til en AD DS virksomhedsadministratorkonto og en Azure AD Administrator-konto.
    
### <a name="solution-architecture-design-assumptions"></a>Forudsætninger for løsningsarkitekturdesign

Følgende liste beskriver de designvalg, der foretages for denne løsning.
  
- Denne løsning bruger et enkelt virtuelt Azure-netværk med en websted-til-websted-VPN-forbindelse. Azure Virtual Network hoster et enkelt undernet, der har én server, den katalogsynkroniseringsserver, der kører Azure AD, Forbind. 
    
- På det lokale netværk findes der en domænecontroller og DNS-servere.
    
- Azure AD Forbind udfører synkronisering af adgangskodehash i stedet for enkelt logon. Du behøver ikke at installere en AD FS-infrastruktur (Active Directory Federation Services). Du kan få mere at vide om synkronisering af adgangskodehash og indstillinger for enkelt logon under Valg af den rigtige godkendelsesmetode [til din Azure Active Directory-hybrididentitetsløsning](/azure/active-directory/hybrid/choose-ad-authn).
    
Der er flere designmuligheder, som du kan overveje, når du installerer denne løsning i dit miljø. Disse omfatter følgende:
  
- Hvis der er eksisterende DNS-servere i et eksisterende virtuelt Azure-netværk, skal du afgøre, om du ønsker, at din katalogsynkroniseringsserver skal bruge dem til navneopløsning i stedet for DNS-servere på det lokale netværk.
    
- Hvis der er domænecontrollere i et eksisterende virtuelt Azure-netværk, skal du afgøre, om det kan være en bedre mulighed for dig at konfigurere Active Directory-websteder og -tjenester. Katalogsynkroniseringsserveren kan forespørge domænecontrollere i det virtuelle Azure-netværk efter ændringer i konti og adgangskoder i stedet for domænecontrollere på det lokale netværk.
    
## <a name="deployment-roadmap"></a>Installationsoversigt

Installation af Azure AD Forbind på en virtuel maskine i Azure består af tre faser:
  
- Fase 1: Opret og konfigurer Det virtuelle Azure-netværk
    
- Fase 2: Opret og konfigurer den virtuelle Azure-maskine
    
- Fase 3: Installer og konfigurer Azure AD-Forbind
    
Efter installationen skal du også tildele placeringer og licenser til de nye brugerkonti i Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Opret og konfigurer Det virtuelle Azure-netværk

For at oprette og konfigurere [Azure-virtuelt](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) netværk skal du fuldføre Fase 1: Forbered dit lokale netværk og [Fase 2:](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) Opret det virtuelle netværk på tværs af det lokale miljø i Azure i installationsoversigten for Forbind et lokalt netværk til et [virtuelt Microsoft Azure-netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Dette er din resulterende konfiguration.
  
![Fase 1 af katalogsynkroniseringsserveren for Microsoft 365 hostet i Azure.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Figuren her viser et lokalt netværk, der er forbundet til et virtuelt Azure-netværk via et websted-til-websted-VPN eller ExpressRoute-forbindelse.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Opret og konfigurer den virtuelle Azure-maskine

Opret den virtuelle maskine i Azure ved hjælp af [vejledningen Opret din første Windows virtuel maskine i Azure-portalen](https://go.microsoft.com/fwlink/p/?LinkId=393098). Brug følgende indstillinger:
  
- I **ruden Grundlæggende** skal du vælge det samme abonnement, den samme placering og ressourcegruppe som dit virtuelle netværk. Optag brugernavnet og adgangskoden på et sikkert sted. Du skal bruge disse senere for at oprette forbindelse til den virtuelle maskine.
    
- I **ruden Vælg en størrelse** skal du vælge **A2 Standardstørrelse** .
    
- Vælg **Indstillinger** **standardlagertype i Storage** **under fanen Egenskaber**. I sektionen **Netværk** skal du vælge navnet på dit virtuelle netværk og undernettet til at hoste katalogsynkroniseringsserveren (ikke Gatewaysubnet). Lad alle andre indstillinger være ved deres standardværdier.
    
Kontrollér, at din katalogsynkroniseringsserver bruger DNS korrekt, ved at kontrollere din interne DNS for at sikre, at en Adresse (A)-post blev føjet til den virtuelle maskine med dens IP-adresse. 
  
Brug vejledningen i [Fjernskrivebord Forbind den virtuelle maskine](/azure/virtual-machines/windows/connect-logon), og log på for at oprette forbindelse til katalogsynkroniseringsserveren med en forbindelse til Fjernskrivebord. Når du er logget på, kan du slutte den virtuelle maskine til det lokale AD DS domæne.
  
For at Azure AD Forbind få adgang til internetressourcer, skal du konfigurere katalogsynkroniseringsserveren til at bruge det lokale netværks proxyserver. Du skal kontakte din netværksadministrator for eventuelle yderligere konfigurationstrin, der skal udføres.
  
Dette er din resulterende konfiguration.
  
![Fase 2 af katalogsynkroniseringsserveren for Microsoft 365 hostet i Azure.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Figuren her viser den virtuelle computer til katalogsynkroniseringsserver i det virtuelle Azure-netværk på tværs af det lokale miljø.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Installer og konfigurer Azure AD-Forbind

Gør følgende:
  
1. Forbind til katalogsynkroniseringsserveren ved hjælp af en forbindelse til Fjernskrivebord med AD DS-domænekonto, der har lokale administratorrettigheder. Se [Forbind på den virtuelle maskine, og log på](/azure/virtual-machines/windows/connect-logon).
    
2. Åbn artiklen Konfigurer katalogsynkronisering til [](set-up-directory-synchronization.md) Microsoft 365 fra katalogsynkroniseringsserveren, og følg vejledningen for katalogsynkronisering med synkronisering af adgangskodehash.
    
> [!CAUTION]
> Konfiguration opretter **kontoen AAD_xxxxxxxxxxxx** i organisationsenheden Lokale brugere (OU). Flyt eller fjern ikke denne konto, da synkronisering mislykkes.
  
Dette er din resulterende konfiguration.
  
![Fase 3 af katalogsynkroniseringsserveren for Microsoft 365 hostet i Azure.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Figuren her viser katalogsynkroniseringsserveren med Azure AD Forbind på det lokale Virtuelle Azure-netværk.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Tildel placeringer og licenser til brugere i Microsoft 365

Azure AD Forbind føjer konti til dit Microsoft 365-abonnement fra den lokale AD DS, men for at brugerne kan logge på Microsoft 365 og bruge tjenesterne, skal kontiene være konfigureret med en placering og licenser. Brug disse trin til at tilføje placeringen og aktivere licenser til de relevante brugerkonti:
  
1. Log på [Microsoft 365 Administration, og](https://admin.microsoft.com) klik derefter på **Administrator**.
    
2. I venstre navigationsrude skal du klikke **på** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**BrugereAktivér**</a> >  brugere.
3. Markér afkrydsningsfeltet ud for den bruger, du vil aktivere, på listen over brugerkonti.
    
4. Klik på Rediger for produktlicenser **på siden** for **brugeren**.
    
5. På siden **Produktlicenser** skal du vælge en placering for **brugeren til Placering** og derefter aktivere de relevante licenser for brugeren.
    
6. Når du er færdig, skal **du klikke** på Gem og derefter klikke **to gange på** Luk.
    
7. Gå tilbage til trin 3 for flere brugere.
    
## <a name="see-also"></a>Se også

[Microsoft 365 og arkitekturcenter](../solutions/index.yml)
  
[Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Download Azure AD-Forbind](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Konfigurer katalogsynkronisering for Microsoft 365](set-up-directory-synchronization.md)
