---
title: Trin 5. Udrul enhedsprofiler i Microsoft Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: Kom i gang med konfigurationsprofiler for at gennemtvinge sikre indstillinger på enheder ved hjælp af Intune til at overføre disse sikkerhedskontroller til cloudmiljøet.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: fe137e626d5199f1709504d025411586965ae9fd
ms.sourcegitcommit: 6fefc15dd78139316597083b702286097d45d4dd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737415"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Trin 5. Udrul enhedsprofiler i Microsoft Intune

Microsoft Intune indeholder indstillinger og funktioner, du kan aktivere eller deaktivere på forskellige enheder i organisationen. Disse indstillinger og funktioner føjes til "konfigurationsprofiler". Du kan oprette profiler til forskellige enheder og forskellige platforme, herunder iOS/iPadOS, Android-enhedsadministrator, Android Enterprise og Windows. Brug derefter Intune til at anvende eller "tildele" profilen til enhederne.

Denne artikel indeholder en vejledning i at komme i gang med konfigurationsprofiler. 


![Trin til administration af enheder](../media/devices/intune-mdm-step-4.png#lightbox)

Konfigurationsprofiler giver dig mulighed for at konfigurere vigtig beskyttelse og sikre overholdelse af angivne standarder for enheder, så de kan få adgang til dine ressourcer. Tidligere blev disse konfigurationsændringer konfigureret ved hjælp af Gruppepolitik indstillinger i Active Directory-domæneservices. En moderne sikkerhedsstrategi omfatter flytning af sikkerhedskontroller til cloudmiljøet, hvor håndhævelse af disse kontrolelementer ikke er afhængig af ressourcer og adgang i det lokale miljø. Intune konfigurationsprofiler er den måde, hvorpå du kan overføre disse sikkerhedskontroller til cloudmiljøet. 

Hvis du vil have en idé om, hvilken type konfigurationsprofiler du kan oprette, skal du se [Anvend funktioner og indstillinger på dine enheder ved hjælp af enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Installer Windows grundlæggende sikkerhedsgrundlinjer for Intune

Hvis du vil justere dine enhedskonfigurationer i forhold til Microsofts grundlinjer for sikkerhed, anbefaler vi som udgangspunkt de grundlæggende sikkerhedslinjer inden for Microsoft Endpoint Manager. Fordelen ved denne fremgangsmåde er, at du kan stole på, at Microsoft holder grundlinjerne opdateret, efterhånden som Windows 10 og 11 funktioner udgives. 

Hvis du vil udrulle de Windows grundlæggende sikkerhedsgrundlinjer for Intune, skal du være tilgængelig for Windows 10 og Windows 11. Se [Brug grundlæggende sikkerhedslinjer til at konfigurere Windows enheder i Intune](/mem/intune/protect/security-baselines) for at få mere at vide om de tilgængelige grundlinjer.

I øjeblikket skal du blot installere den mest relevante MDM-sikkerhedsbaselinje. Se [Administrer profiler for grundlæggende sikkerhedsgrundlinjer i Microsoft Intune ](/mem/intune/protect/security-baselines-configure)for at oprette profilen og vælge den oprindelige version.

Når Microsoft Defender for Endpoint er konfigureret senere, og du har oprettet forbindelse Intune, skal du installere Defender for Endpoint baselines. Dette emne behandles i den næste artikel i denne serie: [Trin 6. Overvåg enhedsrisici og overholdelse af angivne standarder i forhold til grundlæggende sikkerhedslinjer](manage-devices-with-intune-monitor-risk.md).

Det er vigtigt at forstå, at disse sikkerhedsbaser ikke er CIS- eller NIST-kompatible, men nøje afspejler deres anbefalinger. Du kan få flere oplysninger under [Er cis- eller NIST-Intune-sikkerhedsbaser kompatible?](https://docs.microsoft.com/mem/intune/protect/security-baselines#are-the-intune-security-baselines-cis-or-nist-compliant)

## <a name="customize-configuration-profiles-for-your-organization"></a>Tilpas konfigurationsprofiler for din organisation

Ud over at udrulle de forudkonfigurerede grundlinjer implementerer mange virksomheder konfigurationsprofiler for at få mere detaljeret kontrol. Denne konfiguration hjælper med at reducere afhængigheden af Gruppepolitik objekter i det Active Directory i det lokale miljø miljø og flytte sikkerhedskontroller til cloudmiljøet. 

De mange indstillinger, du kan konfigurere ved hjælp af konfigurationsprofiler, kan grupperes i fire kategorier, som vist nedenfor.

![Intune enhedsprofilkategorier](../media/devices/intune-device-profile-categories.png#lightbox)

I følgende tabel beskrives illustrationen.


|Kategori |Beskrivelse |Eksempler  |
|---------|---------|---------|
|Enhedsfunktioner     | Styrer funktioner på enheden. Denne kategori gælder kun for iOS-/iPadOS- og macOS-enheder.        | Lufttryk, meddelelser, låseskærmsmeddelelser        |
|Enhedsbegrænsninger     | Styrer sikkerhed, hardware, datadeling og flere indstillinger på enhederne        | Kræv en pinkode, datakryptering        |
|Adgangskonfiguration     |  Konfigurerer en enhed til at få adgang til organisationens ressourcer        | Mailprofiler, VPN-profiler, Wi-Fi indstillinger, certifikater        |
|Brugerdefinerede     | Angiv brugerdefineret konfiguration, eller udfør brugerdefinerede konfigurationshandlinger       | Angiv OEM-indstillinger, udfør PowerShell-scripts        |
|    |         |         |

Når du tilpasser konfigurationsprofiler for din organisation, skal du bruge følgende vejledning:
- Gør din strategi for styring af sikkerhed mere enkel ved at begrænse det samlede antal politikker.
- Gruppér indstillinger i de kategorier, der er angivet ovenfor, eller kategorier, der giver mening for din organisation.
- Når du flytter sikkerhedskontrolelementer fra Gruppepolitik Objekter til Intune konfigurationsprofiler, skal du overveje, om de indstillinger, der er konfigureret af hvert gruppepolitikobjekt, stadig er relevante og nødvendige for at bidrage til din overordnede cloudsikkerhedsstrategi. Betinget adgang og de mange politikker, der kan konfigureres på tværs af cloudtjenester, herunder Intune, giver mere avanceret beskyttelse, end det kunne konfigureres i et lokalt miljø, hvor brugerdefinerede gruppepolitikobjekter oprindeligt blev designet.
- Brug Gruppepolitik Analytics til at sammenligne og knytte dine aktuelle GPO-indstillinger til funktioner i Microsoft Endpoint Manager. Se [Analysér dine gruppepolitikobjekter i det lokale miljø ved hjælp af Gruppepolitik analyser](/mem/intune/configuration/group-policy-analytics) i Microsoft Endpoint Manager.
- Når du bruger brugerdefinerede konfigurationsprofiler, skal du bruge vejledningen her: [Opret en profil med brugerdefinerede indstillinger i Intune](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Flere ressourcer

Hvis du ikke er sikker på, hvor du skal starte med enhedsprofiler, kan følgende hjælpe:

- [Automatiserede scenarier](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Grundlæggende sikkerhedslinjer](/mem/intune/protect/security-baselines)

Hvis dit miljø indeholder gruppepolitikobjekter i det lokale miljø, er følgende funktioner en god overgang til cloudmiljøet:

- [Gruppepolitik analyse](/mem/intune/configuration/group-policy-analytics)
- [Administratorskabeloner (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [Indstillinger katalog](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Næste trin
Gå til [trin 6. Overvåg enhedsrisici og overholdelse af angivne standarder i forhold til grundlæggende sikkerhedslinjer](manage-devices-with-intune-monitor-risk.md).
