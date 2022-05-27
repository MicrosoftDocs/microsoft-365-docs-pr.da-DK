---
title: Installér synkronisering af Microsoft 365 adresseliste i Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du udruller Azure AD Forbind på en virtuel maskine i Azure for at synkronisere konti mellem din lokale mappe og den Azure AD lejer.
ms.openlocfilehash: e04a3a4e681ab50b767670cfd419d29cd95556e7
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753380"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Installér synkronisering af Microsoft 365 adresseliste i Microsoft Azure

Azure Active Directory (Azure AD) Forbind (tidligere kaldet værktøjet Katalogsynkronisering, Værktøjet Mappesynkronisering eller DirSync.exe værktøj) er et program, som du installerer på en domænetilsluttet server for at synkronisere AD DS (Active Directory i det lokale miljø Domain Services) brugere til den Azure AD lejer i dit Microsoft 365 abonnement. Microsoft 365 bruger Azure AD til katalogtjenesten. Dit Microsoft 365-abonnement indeholder en Azure AD lejer. Denne lejer kan også bruges til administration af din organisations identiteter med andre cloudarbejdsbelastninger, herunder andre SaaS-programmer og apps i Azure.

Du kan installere Azure AD Forbind på en server i det lokale miljø, men du kan også installere den på en virtuel maskine i Azure af følgende årsager:
  
- Du kan klargøre og konfigurere skybaserede servere hurtigere, hvilket gør tjenesterne tilgængelige for dine brugere hurtigere.
- Azure tilbyder bedre tilgængelighed af websteder med en mindre indsats.
- Du kan reducere antallet af lokale servere i din organisation.

Denne løsning kræver forbindelse mellem dit lokale netværk og dit virtuelle Azure-netværk. Du kan få flere oplysninger under [Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> I denne artikel beskrives synkronisering af et enkelt domæne i en enkelt skov. Azure AD Forbind synkroniserer alle AD DS-domæner i Active Directory-området med Microsoft 365. Hvis du har flere Active Directory-områder, der skal synkroniseres med Microsoft 365, skal du se [Synkroniser mappe med flere områder med enkelt Sign-On scenarie](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Oversigt over installation af Microsoft 365 katalogsynkronisering i Azure

I følgende diagram vises Azure AD Forbind, der kører på en virtuel maskine i Azure (mappesynkroniseringsserveren), der synkroniserer et AD DS-område i det lokale miljø til et Microsoft 365-abonnement.
  
![Azure AD Forbind værktøj på en virtuel maskine i Azure, der synkroniserer konti i det lokale miljø til den Azure AD lejer for et Microsoft 365 abonnement med trafikflow.](../media/CP-DirSyncOverview.png)
  
I diagrammet er der to netværk, der er forbundet via en websted til websted-VPN- eller ExpressRoute-forbindelse. Der er et netværk i det lokale miljø, hvor AD DS-domænecontrollere er placeret, og der er et virtuelt Azure-netværk med en katalogsynkroniseringsserver, som er en virtuel maskine, der kører [Azure AD Forbind](https://www.microsoft.com/download/details.aspx?id=47594). Der er to primære trafikflow, der stammer fra katalogsynkroniseringsserveren:
  
-  Azure AD Forbind forespørger en domænecontroller på netværket i det lokale miljø om ændringer af konti og adgangskoder.
-  Azure AD Forbind sender ændringerne af konti og adgangskoder til den Azure AD forekomst af dit Microsoft 365 abonnement. Da katalogsynkroniseringsserveren er i en udvidet del af dit lokale netværk, sendes disse ændringer via proxyserveren for det lokale netværk.
    
> [!NOTE]
> Denne løsning beskriver synkronisering af et enkelt Active Directory-domæne i et enkelt Active Directory-område. Azure AD Forbind synkroniserer alle Active Directory-domæner i Active Directory-området med Microsoft 365. Hvis du har flere Active Directory-områder, der skal synkroniseres med Microsoft 365, skal du se [Synkroniser mappe med flere områder med enkelt Sign-On scenarie](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
Der er to overordnede trin, når du installerer denne løsning:
  
1. Opret et virtuelt Azure-netværk, og opret en websted til websted-VPN-forbindelse til dit lokale netværk. Du kan få flere oplysninger under [Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Installér [Azure AD Forbind](https://www.microsoft.com/download/details.aspx?id=47594) på en domænetilsluttet virtuel maskine i Azure, og synkroniser derefter AD DS i det lokale miljø for at Microsoft 365. Dette omfatter:
    
    Oprettelse af en Virtuel Azure-maskine til kørsel af Azure AD Forbind.
    
    Installation og konfiguration af [Azure AD Forbind](https://www.microsoft.com/download/details.aspx?id=47594).
    
    Konfiguration af Azure AD Forbind kræver legitimationsoplysningerne (brugernavn og adgangskode) for en Azure AD administratorkonto og en AD DS-virksomhedsadministratorkonto. Azure AD Forbind kører med det samme og løbende for at synkronisere AD DS-skoven i det lokale miljø til Microsoft 365.
    
Før du installerer denne løsning i produktion, kan du bruge instruktionerne i [Den simulerede virksomhedsbasiskonfiguration](simulated-ent-base-configuration-microsoft-365-enterprise.md) til at konfigurere denne konfiguration som blåstempling, til demonstrationer eller til eksperimentering.
  
> [!IMPORTANT]
> Når Azure AD Forbind konfiguration er fuldført, gemmes legitimationsoplysningerne for AD DS-virksomhedsadministratoren ikke. 
  
> [!NOTE]
> I denne løsning beskrives synkronisering af en enkelt AD DS-skov for at Microsoft 365. Topologien, der er beskrevet i denne artikel, repræsenterer kun én måde at implementere denne løsning på. Organisationens topologi kan variere afhængigt af dine entydige netværkskrav og sikkerhedsovervejelser. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Planlæg, hvordan du hoster en katalogsynkroniseringsserver for Microsoft 365 i Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Forudsætninger

Før du begynder, skal du gennemse følgende forudsætninger for denne løsning:
  
- Gennemse det relaterede planlægningsindhold i [Planlæg dit virtuelle Azure-netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network).
    
- Sørg for, at du opfylder alle [forudsætninger](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) for at konfigurere det virtuelle Azure-netværk.
    
- Hav et Microsoft 365 abonnement, der indeholder Active Directory-integrationsfunktionen. Du kan få oplysninger om Microsoft 365 abonnementer på [siden Microsoft 365 abonnement](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- Klargør en Azure Virtual Machine, der kører Azure AD Forbind for at synkronisere AD DS-skoven i det lokale miljø med Microsoft 365.
    
    Du skal have legitimationsoplysningerne (navne og adgangskoder) for en AD DS-virksomhedsadministratorkonto og en Azure AD administratorkonto.
    
### <a name="solution-architecture-design-assumptions"></a>Antagelser i forbindelse med løsningsarkitekturdesign

På følgende liste beskrives de designvalg, der er foretaget for denne løsning.
  
- Denne løsning bruger et enkelt virtuelt Azure-netværk med en VPN-forbindelse fra websted til websted. Det virtuelle Azure-netværk hoster et enkelt undernet, der har én server, nemlig den mappesynkroniseringsserver, der kører Azure AD Forbind. 
    
- På netværket i det lokale miljø findes der en domænecontroller og DNS-servere.
    
- Azure AD Forbind udfører synkronisering af adgangskodehash i stedet for enkeltlogon. Du behøver ikke at udrulle en AD FS-infrastruktur (Active Directory Federation Services). Hvis du vil vide mere om synkronisering af adgangskodehash og indstillinger for enkeltlogon, skal [du se Vælge den rette godkendelsesmetode til din Azure Active Directory hybrididentitetsløsning](/azure/active-directory/hybrid/choose-ad-authn).
    
Der er andre designvalg, som du kan overveje, når du installerer denne løsning i dit miljø. Disse omfatter følgende:
  
- Hvis der er eksisterende DNS-servere i et eksisterende virtuelt Azure-netværk, skal du afgøre, om din mappesynkroniseringsserver skal bruge dem til navneopløsning i stedet for DNS-servere på netværket i det lokale miljø.
    
- Hvis der er domænecontrollere i et eksisterende virtuelt Azure-netværk, skal du afgøre, om konfiguration af Active Directory-websteder og -tjenester kan være en bedre mulighed for dig. Katalogsynkroniseringsserveren kan forespørge domænecontrollerne på det virtuelle Azure-netværk om ændringer i konti og adgangskoder i stedet for domænecontrollere på netværket i det lokale miljø.
    
## <a name="deployment-roadmap"></a>Oversigt over udrulning

Udrulning af Azure AD Forbind på en virtuel maskine i Azure består af tre faser:
  
- Fase 1: Opret og konfigurer det virtuelle Azure-netværk
    
- Fase 2: Opret og konfigurer den virtuelle Azure-maskine
    
- Fase 3: Installér og konfigurer Azure AD Forbind
    
Efter udrulningen skal du også tildele placeringer og licenser til de nye brugerkonti i Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Fase 1: Opret og konfigurer det virtuelle Azure-netværk

Hvis du vil oprette og konfigurere det virtuelle Azure-netværk, skal du fuldføre [fase 1: Forbered dit lokale netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) og [fase 2: Opret det virtuelle netværk i det lokale miljø i Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) i udrulningsoversigten [over Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Dette er din resulterende konfiguration.
  
![Fase 1 af katalogsynkroniseringsserveren for Microsoft 365, der hostes i Azure.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Denne figur viser et netværk i det lokale miljø, der er forbundet til et virtuelt Azure-netværk via en websted til websted-VPN- eller ExpressRoute-forbindelse.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Fase 2: Opret og konfigurer den virtuelle Azure-maskine

Opret den virtuelle maskine i Azure ved hjælp af vejledningen [Opret din første Windows virtuelle maskine i Azure Portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Brug følgende indstillinger:
  
- I ruden **Grundlæggende** skal du vælge det samme abonnement, den samme placering og den samme ressourcegruppe som dit virtuelle netværk. Registrer brugernavnet og adgangskoden på en sikker placering. Du skal bruge disse senere for at oprette forbindelse til den virtuelle maskine.
    
- Vælg **A2 Standardstørrelse** i ruden **Vælg en størrelse**.
    
- Vælg **Standardlagertype** i sektionen Storage **i ruden** **Indstillinger**. I afsnittet **Netværk** skal du vælge navnet på dit virtuelle netværk og undernettet til hosting af katalogsynkroniseringsserveren (ikke GatewaySubnet). Lad alle andre indstillinger være på deres standardværdier.
    
Kontrollér, at katalogsynkroniseringsserveren bruger DNS korrekt, ved at kontrollere din interne DNS for at sikre, at der blev tilføjet en adressepost (A) for den virtuelle maskine med dens IP-adresse. 
  
Brug vejledningen i [Forbind til den virtuelle maskine, og log på](/azure/virtual-machines/windows/connect-logon) for at oprette forbindelse til katalogsynkroniseringsserveren med en forbindelse til Fjernskrivebord. Når du er logget på, skal du slutte den virtuelle maskine til AD DS-domænet i det lokale miljø.
  
Hvis Azure AD Forbind skal have adgang til internetressourcer, skal du konfigurere katalogsynkroniseringsserveren til at bruge proxyserveren på netværket i det lokale miljø. Du skal kontakte netværksadministratoren for at få yderligere konfigurationstrin at udføre.
  
Dette er din resulterende konfiguration.
  
![Fase 2 af katalogsynkroniseringsserveren for Microsoft 365, der hostes i Azure.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
I denne figur vises den virtuelle maskine til katalogsynkroniseringsserver på det virtuelle Azure-netværk på tværs af det lokale miljø.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Fase 3: Installér og konfigurer Azure AD Forbind

Fuldfør følgende procedure:
  
1. Forbind til katalogsynkroniseringsserveren ved hjælp af en Fjernskrivebord-forbindelse med en AD DS-domænekonto, der har lokale administratorrettigheder. Se [Forbind til den virtuelle maskine, og log på](/azure/virtual-machines/windows/connect-logon).
    
2. Åbn artiklen [Konfigurer katalogsynkronisering for Microsoft 365](set-up-directory-synchronization.md) fra katalogsynkroniseringsserveren, og følg vejledningen i katalogsynkronisering med synkronisering af adgangskodehash.
    
> [!CAUTION]
> Installationsprogrammet opretter den **AAD_xxxxxxxxxxxx** konto i organisationsenheden Lokale brugere. Undlad at flytte eller fjerne denne konto, da synkroniseringen mislykkes.
  
Dette er din resulterende konfiguration.
  
![Fase 3 af katalogsynkroniseringsserveren for Microsoft 365, der hostes i Azure.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
I denne figur vises katalogsynkroniseringsserveren med Azure AD Forbind i det virtuelle Azure-netværk på tværs af det lokale miljø.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Tildel placeringer og licenser til brugere i Microsoft 365

Azure AD Forbind føjer konti til dit Microsoft 365-abonnement fra AD DS i det lokale miljø, men for at brugerne kan logge på Microsoft 365 og bruge deres tjenester, skal kontiene konfigureres med en placering og licenser. Brug disse trin til at tilføje placeringen og aktivere licenser for de relevante brugerkonti:
  
1. Log på [Microsoft 365 Administration](https://admin.microsoft.com), og klik derefter på **Administration**.
    
2. Klik på **Aktive** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**brugere**</a> i venstre navigationsrude.
3. På listen over brugerkonti skal du markere afkrydsningsfeltet ud for den bruger, du vil aktivere.
    
4. Klik på **Rediger** for **produktlicenser på brugerens** side.
    
5. På siden **Produktlicenser** skal du vælge en placering for brugeren for **Placering** og derefter aktivere de relevante licenser for brugeren.
    
6. Når du er færdig, skal du klikke på **Gem** og derefter klikke på **Luk** to gange.
    
7. Gå tilbage til trin 3 for yderligere brugere.
    
## <a name="see-also"></a>Se også

[Microsoft 365-løsnings- og arkitekturcenter](../solutions/index.yml)
  
[Forbind et lokalt netværk til et Microsoft Azure virtuelt netværk](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Download Azure AD Forbind](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Konfigurer katalogsynkronisering for Microsoft 365](set-up-directory-synchronization.md)
