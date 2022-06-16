---
title: Windows- og Office 365-installationslaboratoriesæt
f1.keywords:
- NOCSH
ms.author: aaroncz
author: cdmm12
manager: dougeby
ms.reviewer: alainme
ms.date: 05/11/2022
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Få mere at vide om, hvor du kan få adgang til Windows og Office Deployment Lab Kit.
ms.openlocfilehash: 63ec41e1865647caac60aa6fe91f69ed6c878e74
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115911"
---
# <a name="windows-and-office-365-deployment-lab-kit"></a>Windows- og Office 365-installationslaboratoriesæt

Den Windows og Office 365 udrulningslaboratoriepakke er designet til at hjælpe dig med at planlægge, teste og validere din udrulning og administration af stationære computere, der kører Windows 10 Enterprise eller Windows 11 Enterprise og Microsoft 365 Apps for enterprise. Øvelserne i kittet dækker ved hjælp af Microsoft Endpoint Configuration Manager, OneDrive, Windows Autopilot og meget mere. Dette sæt anbefales på det kraftigste til organisationer, der forbereder sig på skrivebordsopgraderinger. Som et isoleret miljø er laboratoriet også ideelt til at udforske opdateringer af udrulningsværktøjet og teste din installationsrelaterede automatisering.

Der er to versioner af laboratoriet, som kan downloades gratis:  

|Windows 10-laboratorie|Windows 11-laboratorie|
|---|---|
|[Win 10 lab-miljø](https://download.microsoft.com/download/8/5/e/85e007b0-1f3e-460c-bd0a-5a8c6ec490b5/Win10_21H2_lab.zip)|[Win 11-laboratoriemiljø](https://download.microsoft.com/download/9/d/9/9d9e278e-a1ea-4704-85e1-cb24f3806f45/Win11_Lab_05.09.zip)|
|[Win 10 lab guides](https://download.microsoft.com/download/8/5/e/85e007b0-1f3e-460c-bd0a-5a8c6ec490b5/Win10_21H2_guides.zip)|[Win 11 lab guides](https://download.microsoft.com/download/9/d/9/9d9e278e-a1ea-4704-85e1-cb24f3806f45/Win11_Lab_Guides_05.09.zip)|

## <a name="a-complete-lab-environment"></a>Et komplet laboratoriemiljø

Øvelsen giver dig et automatisk klargjort virtuelt laboratoriemiljø, herunder domænetilsluttede skrivebordsklienter, en domænecontroller, en internetgateway og en fuldt konfigureret Configuration Manager forekomst. Øvelserne indeholder evalueringsversioner af følgende produkter:

|Windows 10-laboratorie|Windows 11-laboratorie|
|---|---|
|Windows 10 Enterprise, version 21H2|Windows 11 Enterprise|
|Microsoft Endpoint Configuration Manager, version 2203|Microsoft Endpoint Configuration Manager, version 2203|
|Windows vurderings- og installationspakke til Windows 10|Windows vurderings- og installationspakke til Windows 11|
|Windows Server 2019|Windows Server 2022|

Laboratorierne er også designet til at være forbundet til prøveversioner til:

- Microsoft 365 E5
- Microsoft 365 Apps for enterprise
- Office 365 E5 med Enterprise Mobility + Security (EMS)

## <a name="step-by-step-labs"></a>Trinvise øvelser

Detaljerede laboratorievejledninger fører dig gennem flere installations- og administrationsscenarier. Øvelserne er blevet opdateret til de nyeste versioner af Intune og Configuration Manager. Bemærk! Der findes nu en ny Windows 11 version af øvelsen. Øvelsesvejledningerne omfatter følgende scenarier:

### <a name="plan-and-prepare-infrastructure"></a>Planlæg og forbered infrastruktur

- Cloud Management Gateway
- Lejer vedhæft og medadministration
- Slutpunktsanalyse
- Optimer levering af opdateringer

### <a name="deploy-windows"></a>Installer Windows

- Sekvenser af installationsopgave for operativsystemet i Configuration Manager
- Windows Autopilot

### <a name="service-windows"></a>Tjeneste Windows

- Servicering Windows ved hjælp af Gruppepolitik
- Servicering Windows ved hjælp af Microsoft Intune
- Servicering Windows med Configuration Manager

### <a name="deploy-microsoft-365-apps-for-enterprise"></a>Installer Microsoft 365 Apps for enterprise

- Cloud-administreret udrulning
- Lokalt administreret udrulning
- Microsoft 365 Apps for enterprise installation på enheder, der ikke er tilsluttet AD
- Administreret udrulning i virksomheden ved hjælp af Configuration Manager
- Virksomhedsadministrerede udrulninger ved hjælp af Microsoft Intune
- Servicering Microsoft 365 Apps for enterprise ved hjælp af Configuration Manager
- Servicering Microsoft 365 Apps for enterprise ved hjælp af Intune
- LOB-installation og -administration med Microsoft Intune
- Installer Microsoft Teams
- Tildelingsfiltre

### <a name="managing-microsoft-edge"></a>Administration af Microsoft Edge

- Udrul og opdater Edge
- IE-tilstand
- Konfigurer ny faneside for virksomhed

### <a name="security-and-compliance"></a>Sikkerhed og kompatibilitet

- Bitlocker
- Microsoft Defender Antivirus
- Windows Hello til virksomheder
- Windows Defender Credential Guard       
- Microsoft Defender Application Guard     
- Windows Defender Exploit Guard             
- Windows Defender programkontrolelement   
- Microsoft Defender for Endpoint 


> [!NOTE]
> Brug en bredbåndsinternetforbindelse til at downloade dette indhold og tillade ca. 30 minutter til automatisk klargøring. Laboratoriemiljøet kræver mindst 16 GB ledig hukommelse og 150 GB ledig diskplads. For at opnå optimal ydeevne anbefales 32 GB ledig hukommelse og 300 GB ledig plads. De virtuelle klienter udløber 90 dage efter aktivering af øvelsen. De virtuelle servere udløber den 11. september 2022. Nye versioner af øvelserne publiceres før udløb. 

## <a name="additional-guidance"></a>Yderligere vejledning

- [Windows ressourcer og dokumentation til klientinstallation](/windows/deployment)
- [Videoer fra Desktop Deployment-serien fra Microsoft Mechanics](https://www.aka.ms/watchhowtoshift)
- [Microsoft Endpoint Configuration Manager installation af operativsystemet](/mem/configmgr/osd/understand/introduction-to-operating-system-deployment)
- [Opdateringsoversigt for Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps)
- [Introduktion med Intune](/intune/get-started-evaluation)

## <a name="related-resources"></a>Relaterede ressourcer

- [Introduktion til Microsoft 365](https://www.microsoft.com/microsoft-365/default.aspx)
- [Microsoft 365 til virksomheder](https://products.office.com/business/office)
- [Introduktion til Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
- [Windows til virksomheder](https://www.microsoft.com/windows/business)
