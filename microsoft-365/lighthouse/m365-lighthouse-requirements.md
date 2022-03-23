---
title: Krav til Microsoft 365 fyrtårn
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere skal du få en liste over krav til brug af Microsoft 365 fyrtårn.
ms.openlocfilehash: 51dd2404f03dc58d5975a37c386ba9c8f1333763
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592280"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>Krav til Microsoft 365 fyrtårn

Microsoft 365 Lighthouse er en administrationsportal, der hjælper administrerede tjenesteudbydere med at sikre og administrere enheder, data og brugere på skala for kunder i små og mellemstore virksomheder (SMB).  

MSP'er skal være tilmeldt Cloud Solution Provider (CSP)-programmet som en indirekte forhandler eller direkte fakturapartner for at bruge Lighthouse.  

Desuden skal hver MSP-kundelejer være kvalificeret til Lighthouse ved at opfylde følgende krav: 
 
- Delegerede administratorrettigheder (DAP) eller detaljeret delegerede administratorrettigheder (GDAP) for MSP'en 
- Mindst én Microsoft 365 Business Premium eller Microsoft 365 E3 licens 
- Færre end 1000 brugere med licens  

## <a name="requirements-for-enablingdevice-management"></a>Krav til aktivering af enhedshåndtering

Hvis du vil have vist kundelejerenheder på siderne til enhedsstyring, skal en MSP:

- Tilmeld alle kundeenheder i Microsoft Endpoint Manager (MEM).Få mere at vide under [Tilmeld enheder i Microsoft Intune](/mem/intune/enrollment/).
- Tildel overholdelsespolitikker til alle kundeenheder.Få mere at vide under [Opret en politik for overholdelse af regler og Microsoft Intune](/mem/intune/protect/create-compliance-policy). 

## <a name="requirements-for-enabling-usermanagement"></a>Krav til aktivering af brugeradministration 

For at kundedata kan vises i rapporter på brugeradministrationssider, herunder risikabelt brugere, multifaktorgodkendelse og nulstilling af adgangskode, skal kundelejere have licenser til Azure Active Directory Premium P1 eller nyere. Azure AD Premium P1 er inkluderet i Microsoft 365 Business Premium og Microsoft 365 E3.   

## <a name="requirements-for-enablingthreat-management"></a>Krav til aktivering af administration af trusler 

Hvis du vil have vist enheder og trusler for kundelejeren på siderne til administration af trusler, skal du tilmelde alle kundelejerenheder i Microsoft Endpoint Manager (MEM) og beskytte dem ved at køre Microsoft Defender Antivirus.  

Få mere at vide under [Tilmeld enheder i Microsoft Intune](/mem/intune/enrollment/).  

Microsoft Defender Antivirus er en del af Windows og er som standard aktiveret på enheder, der kører Windows 10.  

> [!NOTE] 
> Hvis du bruger en antivirusløsning, der ikke er Microsoft, og ikke Microsoft Defender Antivirus, Microsoft Defender Antivirus automatisk deaktiveret. Når du fjerner den ikke-Microsoft-antivirusløsning, Microsoft Defender Antivirus automatisk for at beskytte dine Windows mod trusler.    

## <a name="related-content"></a>Relateret indhold

[Konfigurer Microsoft 365 Lighthouse Portal Security](m365-lighthouse-configure-portal-security.md) (artikel)\
[Microsoft 365 oversigt over siden til overholdelse af fyrtårnsenhed](m365-lighthouse-device-compliance-page-overview.md) (artikel)\
[Microsoft 365 oversigt over lighthousebrugere](m365-lighthouse-users-page-overview.md) (artikel)\
[Microsoft 365 oversigt over siden til administration af fyrtårne](m365-lighthouse-threat-management-page-overview.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om](m365-lighthouse-faq.yml)  fyrtårn(artikel)

