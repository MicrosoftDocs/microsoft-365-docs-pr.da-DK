---
title: Afhjælpning af trusler i Microsoft 365 Fyrtårn med Microsoft Defender Antivirus
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: algreer
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
description: Få mere at vide om afhjælpning af trusler med Microsoft Defender Antivirus for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: 3c600c8119ba3d4a252efcf5675ab58138a69b83
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016674"
---
# <a name="mitigate-threats-in-microsoft-365-lighthouse-with-microsoft-defender-antivirus"></a>Afhjælpning af trusler i Microsoft 365 Fyrtårn med Microsoft Defender Antivirus

Microsoft 365 Lighthouse gør det muligt for partnere at undersøge og afhjælpe trusler på tværs af alle dine lejere. Du kan også starte antivirusscanninger på enheder, kontrollere, at enheder får de nyeste opdateringer til Microsoft Defender Antivirus, og gennemse ventende handlinger efter antivirusscanninger. Lighthouse understøtter kun enheder, der kører Windows 10 eller nyere.

## <a name="before-you-begin"></a>Før du begynder

- Microsoft 365 Lighthouse udrulles kun i partnerlejer – ikke i kundelejerne, men sørg for, at du og dine kundelejere opfylder de krav, der er angivet i [Microsoft 365 Lighthouse-krav](m365-lighthouse-requirements.md).

- Brugerne skal køre Microsoft Defender Antivirus (inkluderet i Windows). Lighthouse understøtter ikke antivirusprogrammer, der ikke er fra Microsoft. Du kan få flere oplysninger under [Slå Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows) til.

- Du skal være global administrator i den partnerlejer, du logger på.

## <a name="investigate-active-threats"></a>Undersøg aktive trusler

Sådan undersøges en bestemt trussel:

1. Vælg **Trusselsadministration** i venstre navigationsrude i Lighthouse.

2. Vælg fanen **Trusler** .

3. Vælg den trussel, du vil undersøge, på listen over trusler.

Ruden med trusselsoplysninger indeholder følgende oplysninger:

| Kategori                                      | Definition                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Enhed og lejer                             | Enhedsnavnet og lejeren, hvor truslen blev fundet. Vælg enhedsnavnet for at få vist flere oplysninger. |
| Trusselsstatus                                 | Truslens status.                                                                                    |
| Trusselstype                                   | Type af trussel.                                                                                              |
| Alvorsgrad af trussel                               | Alvorsgrad af trussel (alvorlig, høj, moderat, lav, ukendt)                                                    |
| Forekomster                                     | Antal forekomster af denne trussel, der findes på enheden.                                                    |
| Først registreret                                | Da truslen først blev registreret på denne enhed.                                                           |
| Dokumentation                                 | Link til yderligere oplysninger om truslen.                                                             |
| Andre enheder på denne lejer med denne trussel | En liste over andre enheder i den samme lejer med den samme aktive trussel.                                      |
| Andre lejere med denne trussel                | En liste over andre lejere med den samme aktive trussel.                                                         |

Sådan undersøges trusler på en bestemt enhed:

1. Vælg **Trusselsadministration** i venstre navigationsrude i Lighthouse.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen.

4. Vælg fanen **Aktuelle trusler** i ruden med oplysninger om enheden.

Lighthouse viser alle trusler, der findes på enheden. Hvis du vil se detaljer, skal du vælge truslen.

## <a name="scan-for-threats-on-a-device"></a>Scan efter trusler på en enhed

En hurtig scanning søger på almindelige placeringer, hvor malware kan være, f.eks. registreringsdatabasenøgler og kender startmapper. En fuld scanning søger på hele enheden. I de fleste tilfælde er en hurtig scanning tilstrækkelig og er den anbefalede mulighed for planlagte scanninger.

1. Vælg **Trusselsadministration** i venstre navigationsrude i Lighthouse.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. I ruden med enhedsoplysninger skal du vælge **Kør fuld scanning** eller **Kør hurtig scanning**.

Du kan også scanne flere enheder ved at markere afkrydsningsfeltet ud for hvert enhedsnavn på listen og derefter vælge **Kør fuld scanning** eller **Kør hurtig scanning**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Hent opdateringer til Microsoft Defender Antivirus

Sådan opdaterer du Microsoft Defender Antivirus på en enkelt enhed:

1. Vælg **Trusselsadministration** i venstre navigationsrude i Lighthouse.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. Vælg **Opdater antivirus** i ruden med enhedsoplysninger.

Du kan hente opdateringer til flere enheder ved at markere afkrydsningsfeltet ud for hvert enhedsnavn på listen og derefter vælge **Opdater antivirus**.

Hvis du har brug for at oprette en ny politik, skal du vælge **Opdater politik** i ruden med enhedsoplysninger. Lighthouse omdirigerer dig til Microsoft Endpoint Manager (MEM). Du kan få flere oplysninger om oprettelse af en politik [under Opret en politik for overholdelse af regler og standarder i Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Kontrollér ventende antivirushandlinger på en enhed

Når der anvendes fortløbende handlinger på en enhed, modtager du en meddelelse, der afventer handling. Sådan kontrollerer du, hvilke handlinger der venter på en enhed:

1. Vælg **Trusselsadministration** i venstre navigationsrude i Lighthouse.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. I ruden med enhedsdetaljer skal du vælge fanen **Statusser for enhedshandling** for at få vist ventende handlinger.

## <a name="restart-a-device"></a>Genstart en enhed

Nogle opdateringer kan kræve, at en enhed genstartes for at installere korrekt.

1. Vælg **Trusselsadministration** i venstre navigationsrude i Lighthouse.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. Vælg **Genstart enhed** i ruden med oplysninger om enheden.

Du kan også genstarte flere enheder ved at markere afkrydsningsfeltet ud for hvert enhedsnavn på listen og derefter vælge **Genstart enhed**.

## <a name="related-content"></a>Relateret indhold

[Krav til Microsoft 365 Fyrtårn](m365-lighthouse-requirements.md) (artikel)\
[Oversigt over siden Threat management i Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (artikel)\
[Opret en politik for overholdelse af regler og standarder i Microsoft Intune](/mem/intune/protect/create-compliance-policy) (artikel)\
[Slå Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows) (artikel)\ til
[Microsoft Sikkerhedsviden](https://www.microsoft.com/wdsi/threats) (webside)
