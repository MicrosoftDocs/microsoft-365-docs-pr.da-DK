---
title: Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Konfigurer godkendelse med høj tilgængelighed i organisationsnetværket for dit Microsoft 365 i Microsoft Azure.'
ms.openlocfilehash: 70d597663a1920706dbab164dda05b7142f7fd04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594247"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Installér godkendelse med høj tilgængelighed i organisationsnetværket Microsoft 365 i Azure

Denne artikel indeholder links til den trinvise vejledning i installation af godkendelse i organisationsnetværk med høj tilgængelighed til Microsoft Microsoft 365 i Azure-infrastrukturtjenester med disse virtuelle computere:
  
- To webprogramproxyservere
    
- To AD FS-servere (Active Directory Federation Services)
    
- To replikeringsdomænecontrollere
    
- Én katalogsynkroniseringsserver, der kører Azure AD Forbind
    
Her er konfigurationen med pladsholdernavne for hver server.
  
**En godkendelse i organisationsnetværket med høj tilgængelighed til Microsoft 365 infrastruktur i Azure**

![Den endelige konfiguration af den høje tilgængelighed Microsoft 365 organisationsnetværksgodkendelsesinfrastruktur i Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Alle de virtuelle maskiner er i et enkelt virtuelt Azure-netværk på tværs af det lokale netværk (VNet). 
  
> [!NOTE]
> Federated Authentication for individuelle brugere er ikke afhængig af lokale ressourcer. Men hvis den lokale forbindelse bliver utilgængelig, vil domænecontrollere på VNet ikke modtage opdateringer til brugerkonti og grupper, der er foretaget i den lokale Active Directory-domæneservices (AD DS). Du kan sikre, at dette ikke sker, ved at konfigurere høj tilgængelighed for din forbindelse på tværs af lokal miljø. Du kan få mere at [vide under Meget tilgængelig på tværs af lokale netværk og VNet-til-VNet-forbindelse](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
Hvert par virtuelle maskiner til en bestemt rolle er i sit eget undernet og tilgængelighedssæt.
  
> [!NOTE]
> Da dette VNet har forbindelse til det lokale netværk, omfatter denne konfiguration ikke jumpbox eller overvågning af virtuelle maskiner på et administrationsundernet. Du kan få mere at [vide under Windows-VM'er til en arkitektur på N-niveau](/azure/guidance/guidance-compute-n-tier-vm). 
  
Resultatet af denne konfiguration er, at du får federated authentication for alle dine Microsoft 365-brugere, hvor de kan bruge deres AD DS-legitimationsoplysninger til at logge på i stedet for deres Microsoft 365-konto. Den sammensatte godkendelsesinfrastruktur anvender et redundant sæt af servere, der nemmere installeres i Azure-infrastrukturtjenester i stedet for i dit lokale grænsenetværk.
  
## <a name="bill-of-materials"></a>Materialeregning

Denne konfiguration af grundlinje kræver følgende sæt Azure-tjenester og -komponenter:
  
- Syv virtuelle maskiner
    
- Et virtuelt netværk på tværs af lokale netværk med fire undernet
    
- Fire ressourcegrupper
    
- Tre tilgængelighedssæt
    
- Ét Azure-abonnement
    
Her er de virtuelle maskiner og deres standardstørrelser for denne konfiguration.
  
|**Element**|**Beskrivelse af virtuel maskine**|**Azure-galleribillede**|**Standardstørrelse**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Første domænecontroller  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
|2.  <br/> |Anden domænecontroller  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
|3.  <br/> |Azure AD Forbind server  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
|4.  <br/> |Første AD FS-server  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
|5.  <br/> |Anden AD FS-server  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
|6.  <br/> |Første webprogramproxyserver  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
|7.  <br/> |Anden webprogramproxyserver  <br/> |Windows Server 2016-datacenter  <br/> |D2  <br/> |
   
Hvis du vil beregne de anslåede omkostninger for denne konfiguration, skal du se [Azure-prisberegner](https://azure.microsoft.com/pricing/calculator/)
  
## <a name="phases-of-deployment"></a>Implementeringsfaser

Du kan implementere denne arbejdsbelastning i følgende faser:
  
- [Fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Opret ressourcegrupper, lagerkonti, tilgængelighedssæt og et virtuelt netværk på tværs af det lokale miljø.
    
- [Fase 2: Konfigurer domænecontrollere](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Opret og konfigurer repliker AD DS domænecontrollere og katalogsynkroniseringsserveren.
    
- [Fase 3: Konfigurer AD FS-servere](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Opret og konfigurer de to AD FS-servere.
    
- [Fase 4: Konfigurer webprogram-proxyer](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Opret og konfigurer de to webprogramproxyservere.
    
- [Fase 5: Konfigurer federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Konfigurer federated authentication for dit Microsoft 365 abonnement.
    
Disse artikler indeholder en præskriptiv, fase for fase-vejledning til en foruddefineret arkitektur til at oprette en funktionel, høj tilgængeligheds- og organisationsnetværksgodkendelse til Microsoft 365 i Azure-infrastrukturtjenester. Vær opmærksom på følgende:
  
- Hvis du er en erfaren AD FS-implementer, er du velkommen til at tilpasse vejledningen i fase 3 og 4 og opbygge det sæt servere, der passer bedst til dine behov.
    
- Hvis du allerede har en eksisterende Azure-hybridskyinstallation med et eksisterende virtuelt netværk på tværs af det lokale miljø, er du velkommen til at tilpasse eller springe vejledningen over i fase 1 og 2 og placere AD FS- og webprogramproxyservere på de relevante undernet.
    
Hvis du vil bygge et udviklings-/testmiljø eller en koncepttest af denne konfiguration, skal du se Identitet i organisationsnetværk [for dit Microsoft 365 udviklings-/testmiljø](federated-identity-for-your-microsoft-365-dev-test-environment.md).
  
## <a name="next-step"></a>Næste trin

Start konfigurationen af denne arbejdsbelastning [med Fase 1: Konfigurer Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
