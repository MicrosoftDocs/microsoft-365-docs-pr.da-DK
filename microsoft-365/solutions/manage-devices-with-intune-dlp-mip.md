---
title: Trin 7. Implementere forebyggelse af datatab (DLP) med funktioner til beskyttelse af oplysninger
ms.author: bcarter
author: brendacarter
f1.keywords:
- Endpoint dlp
- data loss prevention
- dlp policies
manager: dougeby
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- endpoint dlp
- data loss prevention
- dlp policies
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
description: Implementer Slutpunkt DLP ved at arbejde med dit team til beskyttelse af oplysninger og ledelse for at oprette DLP-politikker for organisationen.
ms.openlocfilehash: c38171d790ffd376c7886da0547345cf7e74e36c
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63594093"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>Trin 7. Implementere forebyggelse af datatab (DLP) med funktioner til beskyttelse af oplysninger


Hvis din organisation allerede har brugt tid på at forstå dine data, udvikle et datafølsomhedsskema og anvende skemaet, er du muligvis klar til at udvide elementer i dette skema til slutpunkter ved hjælp af politikker til forebyggelse af datatab (DLP). 

Microsoft Endpoint forebyggelse af datatab (Endpoint DLP) gælder i øjeblikket for:
- Windows 10, Windows 11
- macOS

DLP-politikker oprettes af dit team til beskyttelse af oplysninger og styring. Hver DLP-politik definerer, hvilke elementer i et datasæt, der skal søges efter, f.eks. typer af følsomme oplysninger eller navne, og hvordan du beskytter disse data. 

En DLP-politik kan f.eks. søge efter personlige data som et pasnummer. DLP-politikken indeholder en betingelse, der udløser, at politikken kan handle, f.eks. når et pasnummer deles med personer uden for organisationen. Den handling, som politikken skal tage, kan også konfigureres. Indstillingerne går fra blot at rapportere handlingen til administratorer, advare brugere eller endda forhindre data i at blive delt.

DLP-politikken angiver også placeringen, politikken skal anvendes på, f.eks. til Exchange og SharePoint websteder. En af de placeringer, der er tilgængelige for administratorer, er enheder. Hvis enheder vælges, kan du angive, hvilke brugere og brugergrupper politikken skal anvendes på. Du kan også angive brugere og brugergrupper, der skal udelukkes fra politikken.

Hvis dit team til beskyttelse af oplysninger og ledelse er klar til at udvide DLP-politikker til slutpunkter, skal du koordinere med dem for at aktivere enheder for Slutpunkt DLP, teste og finjustere DLP-politikker, oplære brugere og overvåge resultaterne. 

![Slutpunkt-DLP-trin for enhedsadministratoren](../media/devices/endpoint-dlp-steps.png#lightbox)

Hvis du har fuldført [trin 2. Tilmeld enheder til administration og](manage-devices-with-intune-enroll.md) [Trin 6. Tilmeld enheder til Defender til Slutpunkt for at overvåge enheders](manage-devices-with-intune-monitor-risk.md) risiko og overholdelse af grundlinjer for sikkerhed. Dine enheder er allerede aktiveret for Endpoint DLP. 


Brug følgende trin til at samarbejde med dit team til beskyttelse af oplysninger.


|Trin  |Beskrivelse  |
|---------|---------|
|1     |  [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Aktivér enheder for Endpoint DLP. Hvis du onboardede enheder til Microsoft Defender til Slutpunkt, er dine enheder allerede aktiveret for Endpoint DLP. Hvis dine enheder ikke er onboardet til Defender til Slutpunkt, skal du se [Introduktion til forebyggelse af datatab i Slutpunkt for at](../compliance/endpoint-dlp-getting-started.md) få vejledning.|
|3     |   Arbejd med dit team til beskyttelse af oplysninger og styring for at definere, teste og finjustere politikker. Dette omfatter overvågning af resultaterne. Se disse ressourcer:<br>- [Brug af forebyggelse af datatab på slutpunkt](../compliance/endpoint-dlp-using.md)<br>- [Få vist rapporter til forebyggelse af datatab](../compliance/view-the-dlp-reports.md)      |
|     |         |