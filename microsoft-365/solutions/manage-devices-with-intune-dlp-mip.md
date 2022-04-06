---
title: Trin 7. Implementer forebyggelse af datatab (DLP) med funktioner til beskyttelse af oplysninger
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
description: Implementer Slutpunkt DLP ved at arbejde sammen med dit informationsbeskyttelses- og styringsteam for at oprette DLP-politikker for din organisation.
ms.openlocfilehash: 605923c377aca77f84861116b38b6ef07f95ca4f
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651295"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>Trin 7. Implementer forebyggelse af datatab (DLP) med funktioner til beskyttelse af oplysninger


Hvis din organisation allerede har brugt tid på at forstå dine data, udvikle et datafølsomhedsskema og anvende skemaet, kan du være klar til at udvide elementer i dette skema til slutpunkter ved hjælp af DLP-politikker (forebyggelse af datatab). 

Forebyggelse af datatab i Microsoft Endpoint (Endpoint DLP) gælder i øjeblikket for:
- Windows 10, Windows 11
- Macos

DLP-politikker oprettes af dit informationsbeskyttelses- og styringsteam. Hver DLP-politik definerer, hvilke elementer i et datasæt der skal søges efter, f.eks. følsomme oplysningstyper eller mærkater, og hvordan disse data beskyttes. 

En DLP-politik kan f.eks. søge efter personlige data som et pasnummer. DLP-politikken indeholder en betingelse, der udløser politikken til at handle, f.eks. når et pasnummer deles med personer uden for organisationen. Den handling, som politikken udfører, kan også konfigureres. Mulighederne spænder fra blot at rapportere handlingen til administratorer, advare brugere eller endda forhindre, at dataene deles.

DLP-politikken angiver også den placering, politikken skal anvendes på, f.eks. Exchange mail og SharePoint websteder. En af de placeringer, der er tilgængelige for administratorer, er enheder. Hvis der er valgt enheder, kan du angive, hvilke brugere og brugergrupper politikken skal anvendes på. Du kan også angive brugere og brugergrupper, der skal udelades fra politikken.

Hvis dit informationsbeskyttelses- og styringsteam er klar til at udvide DLP-politikker til slutpunkter, skal du koordinere med dem for at aktivere enheder for Endpoint DLP, teste og justere DLP-politikker, oplære brugere og overvåge resultaterne. 

![DLP-trin for slutpunkt for enhedsadministratoren](../media/devices/endpoint-dlp-steps.png#lightbox)

Hvis du har fuldført [trin 2. Tilmeld enheder til Intune](manage-devices-with-intune-enroll.md) og [trin 6. Tilmeld enheder til Defender for Endpoint for at overvåge enhedsrisici og overholdelse af angivne standarder i forhold til grundlæggende sikkerhedsdata](manage-devices-with-intune-monitor-risk.md). Dine enheder er allerede aktiveret for Slutpunkt DLP. 


Brug følgende trin til at arbejde sammen med dit informationsbeskyttelsesteam.


|Trin  |Beskrivelse  |
|---------|---------|
|1     |  [Få mere at vide om Microsoft 365 forebyggelse af datatab i Slutpunkt](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Aktivér enheder for Slutpunkt DLP. Hvis du har onboardet enheder til Microsoft Defender for Endpoint, er dine enheder allerede aktiveret til Slutpunkt DLP. Hvis dine enheder ikke er onboardet til Defender for Endpoint, skal [du se Kom i gang med forebyggelse af datatab for at](../compliance/endpoint-dlp-getting-started.md) få instruktioner.|
|3     |   Samarbejd med dit team for beskyttelse af oplysninger og styring for at definere, teste og justere politikker. Dette omfatter overvågning af resultaterne. Se disse ressourcer:<br>- [Brug af forebyggelse af datatab for slutpunkt](../compliance/endpoint-dlp-using.md)<br>- [Få vist rapporterne til forebyggelse af datatab](../compliance/view-the-dlp-reports.md)      |
|     |         |