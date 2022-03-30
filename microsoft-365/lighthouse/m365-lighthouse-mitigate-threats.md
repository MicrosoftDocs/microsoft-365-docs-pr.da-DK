---
title: Mindske trusler med Microsoft Defender Antivirus
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få mere at vide om afhjælpning af trusler Microsoft Defender Antivirus.
ms.openlocfilehash: 297c35104ae58efb1b7c58d3d1968158d42c0fce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598580"
---
# <a name="mitigate-threats-with-microsoft-defender-antivirus"></a>Mindske trusler med Microsoft Defender Antivirus

Microsoft 365 Lighthouse giver partnere mulighed for at undersøge og afhjælpe trusler på tværs af alle dine lejere. Du kan også starte antivirusscanninger på enheder, sørge for, at enhederne henter de seneste opdateringer til Microsoft Defender Antivirus og gennemse afventende handlinger efter antivirusscanninger. Fyrtårn understøtter kun enheder, der Windows 10 eller nyere.

## <a name="before-you-begin"></a>Før du begynder

- Microsoft 365 Lighthouse kun installeret i partnerlejeren – ikke i kundelejerne, men sørg for, at du og dine kundelejere opfylder kravene i [Microsoft 365 Lighthouse-krav](m365-lighthouse-requirements.md).

- Brugere skal køre Microsoft Defender Antivirus (følger med Windows). Lighthouse understøtter ikke antivirussoftware, som ikke er Microsoft. Du kan finde flere oplysninger [under Slå Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows).

- Du skal være global administrator i partnerlejeren, som du logger på.

## <a name="investigate-active-threats"></a>Undersøg aktive trusler

Sådan undersøger du en bestemt trussel:

1. I venstre navigationsrude i Lighthouse skal du vælge **Trusselsstyring**.

2. Vælg **fanen Trusler** .

3. På trusselslisten skal du vælge den trussel, du vil undersøge.

Detaljeruden for trusler indeholder følgende oplysninger:

| Kategori                                      | Definition                                                                                                   |
|-----------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| Enhed og lejer                             | Enhedsnavnet og lejeren, hvor truslerne blev fundet. Vælg navnet på enheden for at få vist yderligere oplysninger. |
| Trusselsstatus                                 | Status for truslerne.                                                                                    |
| Trusselstype                                   | Type af trussel.                                                                                              |
| Alvorlighed af trusler                               | Alvorlighed af trussel (alvorlig, høj, moderat, lav, ukendt)                                                    |
| Forekomster                                     | Antallet af forekomster af denne trussel findes på enheden.                                                    |
| Først registreret                                | Da truslen først blev registreret på denne enhed.                                                           |
| Dokumentation                                 | Link til yderligere oplysninger om truslen.                                                             |
| Andre enheder i denne lejer med denne trussel | En liste over andre enheder i samme lejer med den samme aktive trussel.                                      |
| Andre lejere med denne trussel                | En liste over andre lejere med den samme aktive trussel.                                                         |

Sådan undersøger du trusler på en bestemt enhed:

1. I venstre navigationsrude i Lighthouse skal du vælge **Trusselsstyring**.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen.

4. Vælg fanen Aktuelle trusler i **detaljeruden for** enheden.

Fyrtårn viser alle trusler, der er fundet på enheden. Hvis du vil se detaljer, skal du vælge truslerne.

## <a name="scan-for-threats-on-a-device"></a>Søg efter trusler på en enhed

En hurtig scanning søger på almindelige steder, hvor malware kan være, f.eks registreringsdatabasenøgler og kendte startmapper. En fuld scanning søger på hele enheden. I de fleste tilfælde er en hurtig scanning tilstrækkelig og er den anbefalede indstilling for planlagte scanninger.

1. I venstre navigationsrude i Lighthouse skal du vælge **Trusselsstyring**.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. I detaljeruden for enheden skal du **vælge Kør fuld scanning** eller **Kør hurtig scanning**.

Du kan også scanne flere enheder ved at markere afkrydsningsfeltet ud for hvert enhedsnavn på listen og derefter vælge Kør fuld **scanning** eller **Kør hurtig scanning**.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>Hent opdateringer til Microsoft Defender Antivirus

Sådan opdateres Microsoft Defender Antivirus på en enkelt enhed:

1. I venstre navigationsrude i Lighthouse skal du vælge **Trusselsstyring**.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. I detaljeruden for enheden skal du vælge **Opdater antivirus**.

Du kan få opdateringer til flere enheder ved at markere afkrydsningsfeltet ud for hvert enhedsnavn på listen og derefter vælge **Opdater antivirus**.

Hvis du vil oprette en ny politik, skal du vælge **Opdater politik** fra detaljeruden på enheden. Lighthouse omdirigerer dig til Microsoft Endpoint Manager (MEM). Du kan finde flere oplysninger om at oprette en politik [under Opret en politik for overholdelse Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="check-pending-antivirus-actions-on-a-device"></a>Kontrollér afventende antivirushandlinger på en enhed

Når der fortløbende handlinger anvendes på en enhed, modtager du en afventende meddelelse. Sådan kontrollerer du, hvilke handlinger der venter på en enhed:

1. I venstre navigationsrude i Lighthouse skal du vælge **Trusselsstyring**.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. I detaljeruden for enheden skal du vælge fanen **Enhedshandlingsstatusser** for at få vist afventende handlinger.

## <a name="restart-a-device"></a>Genstart en enhed

Nogle opdateringer kræver muligvis en enhed for at genstarte for at installere korrekt.

1. I venstre navigationsrude i Lighthouse skal du vælge **Trusselsstyring**.

2. Vælg fanen **Antivirusbeskyttelse** .

3. Vælg en enhed på listen over enheder.

4. I detaljeruden for enheden skal du vælge **Genstart enhed**.

Du kan også genstarte flere enheder ved at markere afkrydsningsfeltet ud for navnet på hver enhed på listen og derefter vælge **Genstart enhed**.

## <a name="related-content"></a>Relateret indhold

[Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artikel)\
[Oversigt over siden Trusselsadministration ](m365-lighthouse-threat-management-page-overview.md) (artikel)\
[Opret en politik for overholdelse af Microsoft Intune](/mem/intune/protect/create-compliance-policy) (artikel)\
[Slå Microsoft Defender Antivirus](/mem/intune/user-help/turn-on-defender-windows) (artikel)\ til
[Microsoft Sikkerhedsviden](https://www.microsoft.com/wdsi/threats) (webside)