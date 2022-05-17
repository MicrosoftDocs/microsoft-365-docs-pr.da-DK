---
title: Trin 3. Planlæg Microsoft 365 Defender integration med dit SOC-katalog over tjenester
description: Det grundlæggende ved integration af Microsoft 365 Defender i kataloget over sikkerhedshandlinger for tjenester.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb, secops, sikkerhedshandlinger, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: f6cab6be7d41f1d71a6ccf69fbedfa616694ee78
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438482"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Trin 3. Planlæg Microsoft 365 Defender integration med dit SOC-katalog over tjenester

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Et etableret SOC (Security Operations Center) skal have et katalog over tjenester, der kan omfatte:

- Intrusion & analyse af malware
- Tilskrivning & reverse engineering
- Trusselsintelligens
- Analytics
- Jagtundersøgelse
- Forensics
- Svar på hændelse 
- CSIRT (Computer Security Incident Response Team) (der kan adskilles fra SOC) 
- Test af overholdelse af angivne standarder
- Insidertrussel & overvågning af svig
- Overvågning af sikkerhedshændelser & hændelse 
- Scanning af sårbarheder
- XDR (Extended Detection and Response)/Security Orchestration, Automation og Response (SOAR)
- Phishing
- Forebyggelse af datatab
- Brandovervågning

Da Microsoft 365 Defender teknologier spænder over forskellige funktioner, skal SOC-teamet bestemme, hvilke roller og ansvarsområder der er bedst egnet til at administrere hver enkelt komponent i Microsoft 365 Defender og tilpasse sig tjenestefunktionen.

Komponenterne i Microsoft 365 Defender er:

- **Microsoft Defender for Identity** (tidligere Azure Advanced Threat Protection, også kendt som Azure ATP) er en cloudbaseret sikkerhedsløsning, der bruger AD DS-signaler (Active Directory-domæneservices) til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod Organisationer.

- **Microsoft Defender for Endpoint** er en holistisk, cloudbaseret sikkerhedsløsning til slutpunkter til enheder, der omfatter risikobaseret håndtering af sikkerhedsrisici og vurdering, reduktion af angrebsoverfladen, adfærdsbaseret og clouddrevet næste generations beskyttelse, slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar), automatisk undersøgelse og afhjælpning, administrerede jagttjenester, omfattende API'er og samlet sikkerhedsadministration.

 - **Microsoft Defender for Office 365** er en cloudbaseret filtreringstjeneste til mail, der hjælper med at beskytte organisationer mod ukendt malware og virus ved at levere robust nuldagsbeskyttelse og indeholder funktioner, der beskytter organisationer mod skadelige links i realtid. Det tilbyder også en omfattende skifer af undersøgelse og jagt, reaktion og afhjælpning, opmærksomhed og uddannelse, og sikre kropsholdning funktioner.

- **Microsoft Defender for Cloud Apps** er en CASB (Cloud Access Security Broker), der understøtter forskellige udrulningstilstande, herunder logindsamling, API-connectors og omvendt proxy. Det giver omfattende synlighed, kontrol over datarejser og avancerede analyser til at identificere og bekæmpe cybertrusler på tværs af alle Microsoft- og tredjepartscloudtjenester.

Da Microsoft 365 Defender komponenter og teknologier strækker sig over forskellige funktioner, skal SOC-teamet bestemme, hvilke roller og ansvarsområder der er bedst egnet til at administrere hver enkelt komponent i Microsoft 365 Defender og tilpasse sig servicefunktion.

Hvis du vil integrere funktionerne i Microsoft 365 Defender, skal du tilpasse SOC-tjenesterne. Du kan få flere oplysninger om funktionerne i Microsoft 365 Defender i følgende artikler:

- [Hvad er Microsoft Defender for Endpoint?](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Hvad er Microsoft Defender for Identity?](/defender-for-identity/what-is)
- [Hvad er Defender for Office 365?](/microsoft-365/security/defender/microsoft-365-defender)
- [Hvad er Microsoft Defender for Cloudapps](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Næste trin

[Trin 4. Definer Microsoft 365 Defender roller, ansvarsområder og tilsyn](integrate-microsoft-365-defender-secops-roles.md)
