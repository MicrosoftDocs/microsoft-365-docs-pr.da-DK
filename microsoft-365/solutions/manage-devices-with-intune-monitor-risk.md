---
title: Trin 6. Overvåg enhedens risiko og overholdelse af regler og standarder i forhold til sikkerhedsbaseline
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: Få mere at vide om, hvordan du opretter forbindelse Microsoft Intune til Defender for Endpoint og overvåger enhedsrisici som en betingelse for adgang.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: af165f3565e3601ac4e8118535af3913c2cb2af8
ms.sourcegitcommit: 6fefc15dd78139316597083b702286097d45d4dd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737445"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>Trin 6. Overvåg enhedens risiko og overholdelse af regler og standarder i forhold til sikkerhedsbaseline

Når din organisation har udrullet Microsoft Defender for Endpoint, kan du få større indsigt i og beskyttelse af dine enheder ved at integrere Microsoft Intune med Defender for Endpoint. For mobilenheder omfatter dette muligheden for at overvåge enhedsrisikoen som en betingelse for adgang. For Windows enheder kan du overvåge disse enheders overholdelse af grundlæggende sikkerhedsgrundlinjer. 

Udrulning af Microsoft Defender for Endpoint omfatter onboarding af slutpunkter. Hvis du har brugt Intune til at onboarde slutpunkter (anbefales), har du allerede oprettet forbindelse Microsoft Intune til Defender for Endpoint. Hvis du har brugt en anden metode til at onboarde slutpunkter til Defender for Endpoint, skal du se [Konfigurer Microsoft Defender for Endpoint i Intune](/mem/intune/protect/advanced-threat-protection-configure) for at sikre, at du har konfigureret service til tjeneste-forbindelsen mellem Intune og Microsoft Defender for Endpoint. 


![Illustration af integration af Defender for Endpoint og Microsoft Intune](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

I denne illustration:
- Microsoft Defender for Endpoint øger i høj grad den sofistikerede trusselsbeskyttelse for enheder. 
- Selvom Microsoft Intune giver dig mulighed for at angive politikker for appbeskyttelse og administrere enheder (herunder konfigurationsændringer), overvåger Defender for Endpoint løbende dine enheder for trusler og kan udføre automatiserede handlinger for at afhjælpe angreb. 
- Du kan oprette forbindelse Microsoft Intune til Defender for Endpoint for at overvåge enhedens risiko og overholdelse af sikkerhedsgrundlinjer.

Denne artikel indeholder følgende trin:
- Overvåg enhedsrisiko
- Overvåg overholdelse af sikkerhedsgrundlinjer

Hvis Defender for Endpoint ikke allerede er konfigureret, kan du samarbejde med administratoren af trusselsbeskyttelse om at [konfigurere evaluerings- og pilotmiljøet](../security/defender/eval-defender-endpoint-overview.md). Du kan samarbejde med pilotgruppen om at afprøve funktionerne i denne artikel.

## <a name="monitor-device-risk-as-a-condition-for-access"></a>Overvåg enhedsrisiko som en betingelse for adgang

Når Microsoft Defender for Endpoint er installeret, kan du drage fordel af trusselsrisikosignaler. Dette giver dig mulighed for at blokere adgang til enheder baseret på deres risikoscore. Microsoft anbefaler, at du tillader adgang til enheder med en risikoscore på mellem eller under.

Til Android og iOS/iPadOS kan trusselssignaler bruges i dine appbeskyttelsespolitikker (APP). Du kan få oplysninger om, hvordan du konfigurerer dette, under [Opret og tildel beskyttelsespolitik for apps for at angive niveauet for enhedsrisiko](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level).

For alle platforme kan du angive risikoniveauet i de eksisterende politikker for enhedsoverholdelse. Se [Opret en politik for betinget adgang](https://docs.microsoft.com/mem/intune/protect/advanced-threat-protection-configure#create-a-conditional-access-policy). 

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>Udrul grundlæggende sikkerhedsindstillinger, og overvåg overholdelse af disse indstillinger

Gælder for: Windows 10, Windows 11

Artiklen Trin [5. Udrul konfigurationsprofiler](manage-devices-with-intune-configuration-profiles.md), anbefaler, at du kommer i gang med konfigurationsprofiler ved hjælp af de grundlæggende sikkerhedsdata, der er tilgængelige for Windows 10 og Windows 11. Microsoft Defender for Endpoint indeholder også grundlæggende sikkerhedsindstillinger, der indeholder indstillinger, der optimerer alle sikkerhedskontrolelementer i Defender for Endpoint-stakken, herunder indstillinger for slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar). Disse installeres også ved hjælp af Microsoft Intune.

Ideelt set udrulles enheder, der er onboardet til Defender for Endpoint, begge grundlinjer: den Windows Intune sikkerhedsbaselinje til at starte med sikre Windows og derefter defender for Endpoint-sikkerhedsbasebaselinjen øverst for at konfigurere sikkerhedskontrolelementerne for Defender for Endpoint optimalt.

Hvis du vil drage fordel af de nyeste data om risici og trusler og for at minimere konflikter i takt med, at grundlinjerne udvikler sig, skal du altid anvende de nyeste versioner af grundlinjerne på tværs af alle produkter, så snart de udgives. 

Ved hjælp af Defender for Endpoint kan du overvåge overholdelse af disse grundlinjer. 

![Kortet til overvågning af overholdelse af sikkerhedsgrundlinjer](../media/devices/secconmgmt-baseline-card.png#lightbox)

Hvis du vil installere grundlæggende sikkerhedsindstillinger og overvåge overholdelse af disse indstillinger, skal du bruge trinnene i denne tabel.


|Trin  |Beskrivelse  |
|---------|---------|
|1     |Gennemse vigtige begreber, og sammenlign Microsoft Defender for Endpoint og Windows Intune grundlæggende sikkerhedsbegreber. <br><br>Se [Øg overholdelse af Microsoft Defender for Endpoint sikkerhedsbaselinje](../security/defender-endpoint/configure-machines-security-baseline.md) for at få anbefalinger.<br><br>Se [Brug grundlæggende sikkerhedstilgange til at konfigurere Windows enheder i Intune ](/mem/intune/protect/security-baselines) for at gennemse listen over tilgængelige grundlæggende sikkerhedsgrundlinjer, og hvordan du undgår konflikter.         |
|2     |  Installer Windows indstillinger for grundlæggende sikkerhedsindstillinger for Intune. Du har muligvis allerede gennemført dette, hvis du har fulgt vejledningen i [trin 5. Udrul konfigurationsprofiler](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  Installer defender for Endpoint baseline settings for Intune. Se [Administrer profiler for grundlæggende sikkerhedsgrundlinjer i Microsoft Intune](/mem/intune/protect/security-baselines-configure) for at oprette profilen og vælge den oprindelige version.<br><br>Du kan også følge vejledningen her: [Gennemse, og tildel Microsoft Defender for Endpoint grundlæggende sikkerhedsplan](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | I Defender for Endpoint skal du gennemse [kortet Security baseline i administration af enhedskonfiguration](../security/defender-endpoint/configure-machines.md).          |


## <a name="next-steps"></a>Næste trin
Gå til [trin 7. Implementer DLP med funktioner til beskyttelse af oplysninger på slutpunkter](manage-devices-with-intune-dlp-mip.md).