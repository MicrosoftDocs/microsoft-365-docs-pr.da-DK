---
title: Trin 3. Planlæg Microsoft 365 Defender integration med dit SOC-katalog over tjenester
description: Grundlæggende om integrering af data Microsoft 365 Defender dit sikkerhedskatalog over tjenester.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb, secops, sikkerhedshandlinger, soc
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
ms.openlocfilehash: 45497f74db9c68959d4b23e013c6ea483e86378a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606656"
---
# <a name="step-3-plan-for-microsoft-365-defender-integration-with-your-soc-catalog-of-services"></a>Trin 3. Planlæg Microsoft 365 Defender integration med dit SOC-katalog over tjenester

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Et etableret Security Operations Center (SOC) skal have et katalog over tjenester, der kan omfatte:

- Malwareanalyse & indtrængen
- Tilskrivelse & reverse engineering
- Trusselsintelligens
- Analyse
- Undersøgelse af ræve
- Det gør du ved at se, hvad
- Hændelsessvar 
- Computer Security Incident Response Team (CSIRT) (der kan være adskilt fra SOC) 
- Test af overholdelse
- Insider-trussel & overvågning af svindel
- Sikkerhedshændelse ved & begivenhedsovervågning 
- Scanning af sikkerhedsrisiko
- Udvidet registrering og svar (XDR)/Security Automation og Response (SOAR)
- Phishing
- Forebyggelse af datatab
- Brandovervågning

Da Microsoft 365 Defender teknologier strækker sig over forskellige funktioner, skal dit SOC-team afgøre, hvilke roller og ansvarsområder der er bedst egnet til at administrere hver komponent i Microsoft 365 Defender og justere efter tjenestefunktionen.

Komponenterne i Microsoft 365 Defender er:

- **Microsoft Defender for Identity** (tidligere Azure Advanced Threat Protection, også kaldet Azure ATP) er en skybaseret sikkerhedsløsning, der bruger Active Directory-domæneservices (AD DS) signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og ondsindede Insider-handlinger henvendt til organisationer.

- **Microsoft Defender til slutpunkt** er en udbyder, som leveres af skyen til enheder med risikobaseret håndtering af sikkerhedsrisici og vurdering, reduktion af angrebsoverfladen, adfærdsbaseret og skybaseret næste generations beskyttelse, slutpunktsregistrering og -svar ( Slutpunktsregistrering og -svar), automatisk undersøgelse og afhjælpning, administrerede fangertjenester, omfattende API'er og samlet sikkerhedsadministration.

 - **Microsoft Defender for Office 365** er en skybaseret mailfiltreringstjeneste, der hjælper med at beskytte organisationer mod ukendt malware og virus ved at give robust beskyttelse på nul dage og indeholder funktioner, der beskytter organisationer mod skadelige links i realtid. Den tilbyder også en omfattende tavle af undersøgelse og jagt, svar og afhjælpning, opmærksomhed og træning samt sikre funktioner til efterstilling.

- **Microsoft Defender til skyapps** er en sikkerhedsmægler til skyadgang (CASB), der understøtter forskellige installationstilstande, herunder logsamling, API-forbindelser og omvendt proxy. Det giver stor synlighed, kontrol over datarejse og avancerede analyser til at identificere og bekæmpe cybertrusler på tværs af alle Microsoft- og tredjepartsskytjenester.

Da Microsoft 365 Defender komponenter og teknologier strækker sig over forskellige funktioner, skal dit SOC-team afgøre, hvilke roller og ansvarsområder der er bedst egnet til at administrere hver komponent i Microsoft 365 Defender og justere efter tjenestefunktionen.

Hvis du vil integrere funktionerne i Microsoft 365 Defender, skal du finjustere SOC-tjenesterne. Du kan finde flere oplysninger om Microsoft 365 Defender i følgende artikler:

- [Hvad er Microsoft Defender til slutpunkt?](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Hvad er Microsoft Defender for Identity?](/defender-for-identity/what-is)
- [Hvad er Defender for Office 365?](/office-365-security/defender-for-office-365)
- [Hvad er Microsoft Defender til skyapps?](/cloud-app-security/what-is-cloud-app-security)

## <a name="next-step"></a>Næste trin

[Trin 4. Definer Microsoft 365 Defender roller, ansvarsområder og oversigt](integrate-microsoft-365-defender-secops-roles.md)
