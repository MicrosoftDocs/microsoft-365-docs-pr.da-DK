---
title: Trin 5. Installér enhedsprofiler i Microsoft Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: Kom i gang med konfigurationsprofiler for at gennemtvinge sikre indstillinger på enheder med Intune for at overgå disse sikkerhedskontrolelementer til skyen.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: d44d70c50db5c086e24af575677d5d51e1b33357
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63593031"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>Trin 5. Installér enhedsprofiler i Microsoft Intune

Microsoft Intune indeholder indstillinger og funktioner, du kan aktivere eller deaktivere på forskellige enheder i organisationen. Disse indstillinger og funktioner føjes til "konfigurationsprofiler". Du kan oprette profiler til forskellige enheder og forskellige platforme, herunder iOS/iPadOS, Android-enhedsadministrator, Android Enterprise og Windows. Brug derefter Intune til at anvende eller "tildele" profilen til enhederne.

Denne artikel indeholder vejledning til at komme i gang med konfigurationsprofiler. 


![Trin til administration af enheder](../media/devices/intune-mdm-step-4.png#lightbox)

Konfigurationsprofiler giver dig mulighed for at konfigurere vigtig beskyttelse og bringe enheder i overholdelse af regler og standarder, så de kan få adgang til dine ressourcer. Tidligere blev disse typer konfigurationsændringer konfigureret ved hjælp Gruppepolitik indstillingerne i Active Directory-domæneservices. En moderne sikkerhedsstrategi omfatter flytning af sikkerhedskontrolelementer til skyen, hvor håndhævelsen af disse kontrolelementer ikke er afhængig af lokale ressourcer og adgang. Intune-konfigurationsprofiler er den måde, hvorpå disse sikkerhedskontrolelementer kan overgå til skyen. 

Hvis du vil give dig en ide om den type konfigurationsprofiler, du kan oprette, skal du se Anvend funktioner og indstillinger på dine enheder ved hjælp af [enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>Installér Windows for Intune

Hvis du som udgangspunkt vil justere dine enhedskonfigurationer efter Microsofts sikkerheds oprindelige planer, anbefaler vi, at grundlinjerne for sikkerheden er inden for Microsoft Endpoint Manager. Fordelen ved denne fremgangsmåde er, at du kan stole på, at Microsoft holder grundlinjerne opdateret, så der Windows 10 og 11 funktioner udgives. 

For at installere Windows for Intune, der er tilgængelige for Windows 10 og Windows 11. Se [Brug oprindelige planer for sikkerhed til at konfigurere Windows i Intune for](/mem/intune/protect/security-baselines) at få mere at vide om de tilgængelige grundlinjer.

Lige nu skal du blot installere den mest relevante mdm-sikkerhedslinje. Se [Administrere profiler for oprindelige planer for sikkerhed Microsoft Intune ](/mem/intune/protect/security-baselines-configure)at oprette profilen og vælge den oprindelige version.

Senere, når Microsoft Defender til slutpunkt er konfigureret, og du har forbindelse til Intune, skal du udrulle grundlinjerne for Defender til slutpunkter. Dette emne er dækket i den næste artikel i denne serie: [Trin 6. Overvåg enhedsrisici og overholdelse af sikkerheds oprindelige planer](manage-devices-with-intune-monitor-risk.md).

Det er vigtigt at forstå, at disse grundlinjer for sikkerhed ikke overholder CIS eller NIST, men afspejler deres anbefalinger nøje. Du kan finde flere oplysninger [i Er INS- eller NIST-standarderne for Intune-sikkerhedsmæssige grundlinjer kompatible](/mem/intune/protect/security-baselines)?

## <a name="customize-configuration-profiles-for-your-organization"></a>Tilpasse konfigurationsprofiler for din organisation

Ud over at installere de forudkonfigurerede grundlinjer implementerer mange virksomhedsorganisationer konfigurationsprofiler for at få mere detaljeret kontrol. Denne konfiguration er med til at reducere afhængigheden af Gruppepolitik objekter i det lokale Active Directory-miljø og flytte sikkerhedskontrolelementer til skyen. 

De mange indstillinger, du kan konfigurere ved hjælp af konfigurationsprofiler, kan grupperes i fire kategorier, som vist nedenfor.

![Profilkategorier for Intune-enhed](../media/devices/intune-device-profile-categories.png#lightbox)

I følgende tabel beskrives illustrationen.


|Kategori |Beskrivelse |Eksempler  |
|---------|---------|---------|
|Enhedsfunktioner     | Kontrolelementer på enheden. Denne kategori gælder kun for iOS-/iPadOS- og macOS-enheder.        | Airprint, meddelelser, låseskærmmeddelelser        |
|Enhedsbegrænsninger     | Styrer sikkerhed, hardware, datadeling og flere indstillinger på enhederne        | Kræve en pinkode, datakryptering        |
|Access-konfiguration     |  Konfigurerer en enhed til at få adgang til organisationens ressourcer        | Mailprofiler, VPN-profiler, Wi-Fi indstillinger, certifikater        |
|Brugerdefineret     | Angive brugerdefineret konfiguration eller udføre brugerdefinerede konfigurationshandlinger       | Angiv OEM-indstillinger, udfør PowerShell-scripts        |
|    |         |         |

Når du tilpasser konfigurationsprofiler for organisationen, skal du bruge følgende vejledning:
- Forenkificer din strategi for sikkerhedsstyring ved at holde det overordnede antal politikker små.
- Gruppeindstillinger i de kategorier, der er angivet ovenfor, eller kategorier, der giver mening for din organisation.
- Når du flytter sikkerhedskontrolelementer fra Gruppepolitik-objekter til Intune-konfigurationsprofiler, skal du overveje, om de indstillinger, der er konfigureret af hvert gruppepolitikobjekt, stadig er relevante og nødvendige for at bidrage til din overordnede skysikkerhedsstrategi. Betinget adgang og de mange politikker, der kan konfigureres på tværs af skytjenester, herunder Intune, giver mere avanceret beskyttelse, end der kunne konfigureres i et lokalt miljø, hvor brugerdefinerede GPOs oprindeligt blev udviklet.
- Brug Gruppepolitik Analytics til at sammenligne og knytte dine aktuelle gruppepolitikobjektindstillinger til funktioner inden for Microsoft Endpoint Manager. Se [Analysér dine objekter for gruppepolitik i det lokale miljø ved hjælp Gruppepolitik analyser](/mem/intune/configuration/group-policy-analytics) i Microsoft Endpoint Manager.
- Når du bruger brugerdefinerede konfigurationsprofiler, skal du sørge for at bruge vejledningen her: [Opret en profil med brugerdefinerede indstillinger i Intune](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>Yderligere ressourcer

Hvis du ikke er sikker på, hvor du skal starte med enhedsprofiler, kan følgende hjælpe:

- [Guidede scenarier](/mem/intune/fundamentals/guided-scenarios-overview) 
- [Grundlinjer for sikkerhed](/mem/intune/protect/security-baselines)

Hvis dit miljø indeholder gpos i det direkte miljø, er følgende funktioner en god overgang til skyen:

- [Gruppepolitik analyser](/mem/intune/configuration/group-policy-analytics)
- [Administratorskabeloner (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [Indstillinger katalog](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>Næste trin
Gå til [Trin 6. Overvåg enhedsrisici og overholdelse af sikkerheds oprindelige planer](manage-devices-with-intune-monitor-risk.md).
