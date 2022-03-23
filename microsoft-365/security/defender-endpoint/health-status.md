---
title: Undersøg agentens tilstandsproblemer
description: Få mere at vide om de værdier, der returneres, når du kører kommandoen mdatp health
keywords: mdatptilstand, kommando, tilstand, status, kommando, onboardingstatus
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 13407c78f89058efe15ed0f5d8f23272716e0237
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593866"
---
# <a name="investigate-agent-health-issues"></a>Undersøg agentens tilstandsproblemer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Den følgende tabel indeholder oplysninger om de værdier, der returneres, når du kører `mdatp health` kommandoen og deres tilsvarende beskrivelser.

<br>

****

|Værdi|Beskrivelse|
|---|---|
|automatic_definition_update_enabled|Sandt, hvis automatiske opdateringer til antivirusdefinitionen er aktiveret, ellers falsk.|
|cloud_automatic_sample_submission_consent|Aktuelt prøveafsendelsesniveau. Kan være en af følgende værdier: <ul><li>**Ingen**: Der sendes ingen mistænkelige eksempler til Microsoft.</li><li>**Pengeskab**: Der sendes kun automatisk mistænkelige eksempler, der ikke indeholder personidentificerbare oplysninger (PII). Dette er standardværdien for denne indstilling.</li><li>**Alle**: Alle mistænkelige eksempler sendes til Microsoft.</li></ul>|
|cloud_diagnostic_enabled|Sand, hvis valgfri indsamling af diagnostiske data er aktiveret, ellers falsk. Du kan finde flere oplysninger om Defender til Slutpunkt og andre produkter og tjenester som f.Microsoft Defender Antivirus og Windows i Microsofts erklæring om beskyttelse af [personlige oplysninger](https://go.microsoft.com/fwlink/?linkid=827576).|
|cloud_enabled|Sandt, hvis cloud-leveret beskyttelse er aktiveret, falsk, ellers.|
|conflicting_applications|Liste over programmer, der muligvis er i konflikt med Microsoft Defender til slutpunkt. Denne liste indeholder, men er ikke begrænset til, andre sikkerhedsprodukter og andre programmer, der er kendt for at forårsage kompatibilitetsproblemer.|
|definitions_status|Status for antivirusdefinitioner.|
|definitions_updated|Dato og klokkeslæt for seneste opdatering af antivirusdefinitionen.|
|definitions_updated_minutes_ago|Antal minutter siden seneste opdatering til definition af antivirus.|
|definitions_version|Antivirusdefinitionsversion.|
|edr_client_version|Version af Slutpunktsregistrering og -svar, der kører på enheden.|
|edr_configuration_version|Slutpunktsregistrering og -svar konfigurationsversion.|
|edr_device_tags|Liste over mærker, der er knyttet til enheden.|
|edr_group_ids|Gruppe-id, som enheden er knyttet til.|
|edr_machine_id|Enheds-id, der bruges Microsoft 365 Defender.|
|engine_version|Version af antivirusprogrammet.|
|sund|Sandt, hvis produktet er sund og falsk, ellers.|
|licenseret|Sandt, hvis enheden er onboardet til en lejer, falsk ellers.|
|log_level|Aktuelt logniveau for produktet.|
|machine_guid|Entydigt computer-id, der bruges af antiviruskomponenten.|
|network_protection_status|Status for netværksbeskyttelseskomponenten (kun macOS). Kan være en af følgende værdier: <ul><li>**start** – Netværksbeskyttelse er startet</li><li>**failed_to_start** – Netværksbeskyttelse kunne ikke startes på grund af en fejl</li><li>**startet** – Netværksbeskyttelse kører i øjeblikket på enheden</li><li>**Genstart –** Netværksbeskyttelse genstarter i øjeblikket</li><li>**stopper** – Netværksbeskyttelse stopper</li><li>**stoppet** – Netværksbeskyttelse kører ikke</li></ul>|
|org_id|Organisation, som enheden er onboardet til. Hvis enheden endnu ikke er onboardet til en organisation, udskrives denne udskrift ikke tilgængelig. Du kan finde flere oplysninger om onboarding [under Onboard to Microsoft Defender for Endpoint](onboarding.md).|
|passive_mode_enabled|Sandt, hvis antiviruskomponenten er indstillet til at køre i passiv tilstand, falsk, ellers.|
|product_expiration|Dato og klokkeslæt, hvor den aktuelle produktversion når ophør af support.|
|real_time_protection_available|Sandt, hvis beskyttelseskomponenten i realtid er sund og falsk, ellers er den falsk.|
|real_time_protection_enabled|Sandt, hvis antivirusbeskyttelse i realtid er aktiveret , ellers falsk.|
|real_time_protection_subsystem|Undersystem, der bruges til at tjene beskyttelse i realtid. Hvis beskyttelse i realtid ikke fungerer som forventet, udskrives denne funktion ikke tilgængelig.|
|release_ring|Slip ringning. Få mere at vide under [Installationsringe](deployment-rings.md).|
|
