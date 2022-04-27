---
title: Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Oversigt: Konfigurer organisationsnetværksgodkendelse med høj tilgængelighed for dit Microsoft 365-abonnement i Microsoft Azure.'
ms.openlocfilehash: 64fc02e6ecaa400da6d6130cb9ae630279102fcc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093410"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Udrul organisationsnetværksgodkendelse med høj tilgængelighed for Microsoft 365 i Azure

Denne artikel indeholder links til den trinvise vejledning i installation af samlet godkendelse med høj tilgængelighed til Microsoft Microsoft 365 i Azure-infrastrukturtjenester med disse virtuelle maskiner:
  
- To webprogramproxyservere
    
- To AD FS-servere (Active Directory Federation Services)
    
- To replikadomænecontrollere
    
- En katalogsynkroniseringsserver, der kører Azure AD Forbind
    
Her er konfigurationen med pladsholdernavne for hver server.
  
**En samlet godkendelse med høj tilgængelighed for Microsoft 365 infrastruktur i Azure**

![Den endelige konfiguration af den høje tilgængelighed Microsoft 365 godkendelsesinfrastruktur i organisationsnetværket i Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Alle de virtuelle maskiner befinder sig i et enkelt virtuelt Azure-netværk på tværs af det lokale miljø (VNet). 
  
> [!NOTE]
> Godkendelse i organisationsnetværket af individuelle brugere er ikke afhængig af ressourcer i det lokale miljø. Men hvis forbindelsen på tværs af det lokale miljø bliver utilgængelig, modtager domænecontrollerne i VNet ikke opdateringer til brugerkonti og grupper, der er oprettet i AD DS (Active Directory i det lokale miljø Domain Services). Hvis du vil sikre, at dette ikke sker, kan du konfigurere høj tilgængelighed for din forbindelse i det lokale miljø. Du kan få flere oplysninger under [Yderst tilgængelig på tværs af det lokale miljø og VNet-til-VNet-forbindelse](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Hvert par af virtuelle maskiner for en bestemt rolle er i sit eget undernet og tilgængelighedssæt.
  
> [!NOTE]
> Da denne VNet er forbundet til netværket i det lokale miljø, omfatter denne konfiguration ikke jumpbox eller overvågning af virtuelle maskiner på et administrationsundernet. Du kan få flere oplysninger under [Kørsel Windows VM'er for en N-niveau-arkitektur](/azure/guidance/guidance-compute-n-tier-vm). 
  
Resultatet af denne konfiguration er, at du har organisationsnetværksgodkendelse for alle dine Microsoft 365 brugere, hvor de kan bruge deres AD DS-legitimationsoplysninger til at logge på i stedet for deres Microsoft 365 konto. Den sammenkædede godkendelsesinfrastruktur bruger et redundant sæt servere, der nemmere kan udrulles i Azure-infrastrukturtjenester i stedet for i dit edge-netværk i det lokale miljø.
  
## <a name="bill-of-materials"></a>Materialefortegnelse

Denne grundlæggende konfiguration kræver følgende sæt Azure-tjenester og -komponenter:
  
- Syv virtuelle maskiner
    
- Ét virtuelt netværk på tværs af det lokale miljø med fire undernet
    
- Fire ressourcegrupper
    
- Tre tilgængelighedssæt
    
- Ét Azure-abonnement
    
Her er de virtuelle maskiner og deres standardstørrelser for denne konfiguration.
  
|**Element**|**Beskrivelse af virtuel maskine**|**Billede af Azure-galleri**|**Standardstørrelse**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Første domænecontroller  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Anden domænecontroller  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Forbind-server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Første AD FS-server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Anden AD FS-server  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Første proxyserver for webprogram  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Anden webprogramproxyserver  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Hvis du vil beregne de anslåede omkostninger for denne konfiguration, skal du se [Azure-prisberegneren](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Udrulningsfaser

Du udruller denne arbejdsbelastning i følgende faser:
  
- [Fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Opret ressourcegrupper, lagerkonti, tilgængelighedssæt og et virtuelt netværk på tværs af det lokale miljø.
    
- [Fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Opret og konfigurer replika AD DS-domænecontrollere og katalogsynkroniseringsserveren.
    
- [Fase 3: Konfigurer AD FS-servere](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Opret og konfigurer de to AD FS-servere.
    
- [Fase 4: Konfigurer proxyer for webprogrammer](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Opret og konfigurer de to webprogramproxyservere.
    
- [Fase 5: Konfigurer godkendelse i organisationsnetværket for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Konfigurer godkendelse i organisationsnetværket for dit Microsoft 365 abonnement.
    
Disse artikler indeholder en præskriptiv trinvis vejledning til en foruddefineret arkitektur for at oprette en funktionel, sammenkædet godkendelse med høj tilgængelighed for Microsoft 365 i Azure-infrastrukturtjenester. Vær opmærksom på følgende:
  
- Hvis du er en erfaren AD FS-implementer, er du velkommen til at tilpasse vejledningen i fase 3 og 4 og bygge det sæt servere, der passer bedst til dine behov.
    
- Hvis du allerede har en eksisterende Azure Hybrid Cloud-udrulning med et eksisterende virtuelt netværk på tværs af det lokale miljø, er du velkommen til at tilpasse eller springe vejledningen over i fase 1 og 2 og placere AD FS- og webprogramproxyserverne på de relevante undernet.
    
Hvis du vil oprette et udviklings-/testmiljø eller en blåstempling af denne konfiguration, skal du se [Organisationsnetværksidentitet for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md).
  
## <a name="next-step"></a>Næste trin

Start konfigurationen af denne arbejdsbelastning med [fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
