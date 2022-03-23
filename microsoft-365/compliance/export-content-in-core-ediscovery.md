---
title: Eksportér og download indhold fra en Core eDiscovery-sag
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
description: Beskriver, hvordan du eksporterer og henter indhold fra en Core eDiscovery-sag Microsoft 365.
ms.openlocfilehash: 1d998a4b1eb540a1d96afc3acd3518d0c604a7e9
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63588624"
---
# <a name="export-content-from-a-core-ediscovery-case"></a>Eksportere indhold fra en Core eDiscovery-sag

Når en søgning, der er knyttet til en core eDiscovery-sag, er blevet kørt, kan du eksportere søgeresultaterne. Når du eksporterer søgeresultater, hentes postkasseelementer i PST-filer eller som individuelle meddelelser. Når du eksporterer indhold SharePoint og OneDrive for Business websteder, eksporteres kopier Office oprindelige dokumenter og andre dokumenter. En Results.csv fil, der indeholder oplysninger om hvert element, der eksporteres, og et manifestfil (i XML-format), der indeholder oplysninger om hvert søgeresultat, eksporteres også.
  
## <a name="export-search-results"></a>Eksportér søgeresultater

1. Gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter og</a> log på med legitimationsoplysningerne for den brugerkonto, der har fået tildelt de relevante eDiscovery-tilladelser.

2. I venstre navigationsrude i Microsoft 365 Overholdelsescenter vælge **Vis alle** og derefter vælge **eDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. På core **eDiscovery-siden** skal du klikke på navnet på den sag, du vil oprette ventepositionen i.

4. Klik **på** fanen Søgninger på startsiden **for sagen** .

5. Klik på **Eksportér** resultater i menuen Handlinger nederst på pop **op-siden**.

   ![Indstillingen Eksportér resultater i menuen Handlinger.](../media/ActionMenuExportResults.png)

   Arbejdsprocessen for at eksportere resultaterne af en søgning, der er knyttet til en Core eDiscovery-sag, er det samme som at eksportere søgeresultaterne for en søgning på **siden Indholdssøgning** . Du kan finde en trinvis vejledning under [Eksportér resultater fra indholdssøgning](export-search-results.md).

   > [!NOTE]
   > Når du eksporterer søgeresultater, har du mulighed for at aktivere duplikering, så der kun eksporteres én kopi af en mail, selvom der kan være fundet flere forekomster af den samme meddelelse i de postkasser, der blev søgt i. Du kan finde flere oplysninger om afplikering, og hvordan duplikerede elementer identificeres, under [Afplikning i eDiscovery-søgeresultater](de-duplication-in-ediscovery-search-results.md).

   Når du starter eksporten, forberedes søgeresultaterne til at downloade, hvilket betyder, at de overføres til en Microsoft-leveret Azure Storage i Microsoft-skyen.
  
6. Klik på **fanen** Eksporter for at få vist listen over eksportjob.
  
   ![Eksportér jobs på fanen Eksportér i Core eDiscovery-sag.](../media/CoreeDiscoveryExport.png)

   Du skal muligvis klikke på Opdater **for** at opdatere listen over eksportjob, så den viser det eksportjob, du har oprettet. Eksportjob har samme navn som den tilsvarende søgning **, _Export** er føjet til søgenavnet.

7. Klik på det eksportjob, du har oprettet, for at få vist statusoplysninger på pop op-siden. Disse oplysninger omfatter procentdelen af elementer, der er blevet overført til Azure Storage placering.

8. Når alle elementer er blevet overført, skal du **klikke på Hent** resultater for at hente søgeresultaterne til din lokale computer. Du kan finde flere oplysninger om at hente søgeresultater under Trin 2 i [Eksportér resultater fra indholdssøgning](export-search-results.md#step-2-download-the-search-results)

> [!NOTE]
> De eksporterede søgeresultater skal downloades inden for 14 dage, efter du har oprettet eksportjobbet.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Flere oplysninger om eksport af søgninger fra en sag

- Du kan finde flere oplysninger om de eksportfiler, der medtages, når du eksporterer søgeresultater, under [Eksportere en rapport for indholdssøgning](export-a-content-search-report.md#whats-included-in-the-report).

- Hvis du genstarter eksporten, påvirker eventuelle ændringer af forespørgslerne i de søgninger, der udgør eksportjobbet, ikke de søgeresultater, der hentes. Når du genstarter en eksport, vil det samme kombinerede søgeforespørgselsjob, der blev kørt, da eksportjobbet blev oprettet, blive kørt igen.

- Hvis du genstarter en eksport, overskriver de søgeresultater, der kopieres Azure Storage placering, de tidligere resultater. De tidligere resultater, som blev kopieret, kan ikke downloades.
