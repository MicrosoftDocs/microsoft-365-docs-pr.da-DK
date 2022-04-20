---
title: Eksportér og download indhold fra en eDiscovery-sag (Standard)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom: admindeeplinkCOMPLIANCE
description: Beskriver, hvordan du eksporterer og downloader indhold fra en eDiscovery -sag (Standard) i Microsoft 365.
ms.openlocfilehash: a0ea33d599ed609c24cf63f1df4c68b882364b1b
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937955"
---
# <a name="export-content-from-a-ediscovery-standard-case"></a>Eksportér indhold fra en eDiscovery-sag (Standard)

Når en søgning, der er knyttet til en eDiscovery-sag (Standard), er blevet kørt, kan du eksportere søgeresultaterne. Når du eksporterer søgeresultater, downloades postkasseelementer i PST-filer eller som individuelle meddelelser. Når du eksporterer indhold fra SharePoint og OneDrive for Business websteder, eksporteres der kopier af oprindelige Office dokumenter og andre dokumenter. En Results.csv fil, der indeholder oplysninger om hvert element, der eksporteres, og en manifestfil (i XML-format), der indeholder oplysninger om hvert søgeresultat, eksporteres også.
  
## <a name="export-search-results"></a>Eksportér søgeresultater

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a> , og log på med legitimationsoplysningerne for den brugerkonto, der er tildelt de relevante eDiscovery-tilladelser.

2. I venstre navigationsrude i overholdelsesportalen skal du vælge **Vis alle** og derefter vælge **eDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. Klik på navnet på den sag, du vil oprette venteposition for, på siden **eDiscovery (Standard** ).

4. Klik **på fanen** **Søgninger** på startsiden for sagen.

5. Klik på **Eksportér resultater** i menuen **Handlinger** nederst på pop op-siden.

   ![Indstillingen Eksportér resultater i menuen Handlinger.](../media/ActionMenuExportResults.png)

   Den arbejdsproces, der skal eksportere resultaterne af en søgning, der er knyttet til en eDiscovery-sag (Standard), er den samme som eksport af søgeresultaterne for en søgning på siden **indholdssøgning** . Du kan finde en trinvis vejledning under [Eksportér resultater af indholdssøgning](export-search-results.md).

   > [!NOTE]
   > Når du eksporterer søgeresultater, har du mulighed for at aktivere deduplikering, så der kun eksporteres én kopi af en mail, selvom der er fundet flere forekomster af den samme meddelelse i de postkasser, der blev søgt i. Du kan finde flere oplysninger om deduplikering, og hvordan dubletter identificeres, [under De-duplikering i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).

   Når du starter eksporten, er søgeresultaterne forberedt til download, hvilket betyder, at de overføres til en Azure Storage placering, der leveres af Microsoft, i Microsoft-cloudmiljøet.
  
6. Klik på fanen **Eksporter** i sagen for at få vist listen over eksportjob.
  
   ![Eksportér job under fanen Eksportér i eDiscovery(Standard) sag.](../media/CoreeDiscoveryExport.png)

   Du skal muligvis klikke på **Opdater** for at opdatere listen over eksportjob, så den viser det eksportjob, du har oprettet. Eksportjob har samme navn som den tilsvarende søgning med **_Export** føjet til søgenavnet.

7. Klik på det eksportjob, du har oprettet, for at få vist statusoplysninger på pop op-siden. Disse oplysninger omfatter procentdelen af elementer, der er overført til den Azure Storage placering.

8. Når alle elementer er blevet overført, skal du klikke på **Download resultater** for at downloade søgeresultaterne til din lokale computer. Du kan finde flere oplysninger om hentning af søgeresultater under Trin 2 i [Eksportér søgeresultater for indhold](export-search-results.md#step-2-download-the-search-results)

> [!NOTE]
> De eksporterede søgeresultater skal hentes inden for 14 dage, efter at du har oprettet eksportjobbet.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Flere oplysninger om eksport af søgninger fra en sag

- Du kan finde flere oplysninger om de eksportfiler, der er inkluderet, når du eksporterer søgeresultater, i [Eksportér en rapport til indholdssøgning](export-a-content-search-report.md#whats-included-in-the-report).

- Hvis du genstarter eksporten, påvirker eventuelle ændringer af forespørgslerne for de søgninger, der udgør eksportjobbet, ikke de søgeresultater, der hentes. Når du genstarter en eksport, køres det samme kombinerede søgeforespørgselsjob, som blev kørt, da eksportjobbet blev oprettet, igen.

- Hvis du genstarter en eksport, overskriver de søgeresultater, der kopieres til den Azure Storage placering, også de forrige resultater. De tidligere resultater, der blev kopieret, kan ikke hentes.
