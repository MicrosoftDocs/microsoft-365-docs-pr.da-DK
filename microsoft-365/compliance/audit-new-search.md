---
title: Overvåg ny søgning
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Audit New Search validerer ydeevneforbedringer, fuldstændighed og konsekvens i resultaterne.
ms.openlocfilehash: e24831eea8c176e8fdfa7608492a5393e786e2d3
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090590"
---
# <a name="audit-new-search-preview"></a>Overvåg ny søgning (prøveversion)

Din organisation kræver adgang til vigtige hændelsesdata i overvågningsloggen for at få indsigt og undersøge brugeraktiviteter yderligere. Tidligere var dine søgejob i den Microsoft Purview-compliance-portal brugergrænseflade begrænset i deres mulighed for at oprette samtidige overvågningssøgningsjob og gennemse historiske søgejob. Disse kritiske overvågningssøgningsjob var også afhængige af det browservindue, der stadig var åbent for at kunne fuldføres.

Audit New Search (prøveversion) bygger på de eksisterende søgefunktioner og indeholder følgende vigtige forbedringer:

- Søgejob, der er startet via brugergrænsefladen i overholdelsesportalen, kræver ikke længere, at webbrowservinduet forbliver åbent for at kunne fuldføres. Disse job vil fortsætte med at køre, selv efter browservinduet er lukket.
- Fuldførte søgejob gemmes nu, hvilket giver kunderne mulighed for at referere til historiske overvågningssøgninger. Disse søgejob vises i brugergrænsefladen med søgenavnet, søgejobstatus, status %, antal resultater, oprettelsestid og søgt efter.
- Hver administratorbruger af overvågningskontoen kan maksimalt have 10 igangværende søgejob ad gangen.

## <a name="information-to-get-started"></a>Oplysninger for at komme i gang

Få vist den tilgængelige Microsoft Purview-gennemgang dokumentation, da søgejoboprettelses- og eksportoplevelserne har mange paralleller til den aktuelle søgeoplevelse:

- [Søg i overvågningsloggen i Microsoft Purview-compliance-portal](search-the-audit-log-in-security-and-compliance.md) (bemærk, at PowerShell endnu ikke er kompatibel med Overvågningssøgning V2)
- [Detaljerede egenskaber i overvågningsloggen](detailed-properties-in-the-office-365-audit-log.md)
- [Eksportér, konfigurer og få vist data fra overvågningsloggen](export-view-audit-log-records.md)

Flere oplysninger:

- Søgning via en EXO PowerShell-session ved hjælp af Search-UnifiedAuditLog-cmdlet'en er ikke kompatibel med den nye søgning på nuværende tidspunkt.
- Søgejob kan tage følgende kriterier: Datointerval, Tidsinterval, Navn på søgejob, Aktiviteter, Brugere, Filer, Mapper og Websteder.
- Søgning og filtrering ved hjælp af dato, klokkeslæt, søgenavn, aktiviteter og brugere er alle fuldt funktionsdygtige
- Overvågningslogdata gemmes for den definerede opbevaringsperiode, uanset om et søgejob slettes
- Søgninger, der er oprettet i perioden Med privat prøveversion, bevares muligvis ikke til fremtidig reference, når funktionen Ny søgning flyttes til offentlig prøveversion.

## <a name="get-started-with-audit-new-search"></a>Kom i gang med at overvåge ny søgning

Følg nedenstående trin for at teste og validere oplevelsen Overvåg ny søgning:

1. Naviger til compliance.microsoft.com
1. Vælg fanen Overvågning i venstre panel på startsiden for at navigere til overvågningsværktøjet
1. Vælg fanen "Ny søgning (prøveversion)" øverst på siden :::image type="content" source="../media/audit-search/audit-new-search.png" alt-text="Overvåg ny søgning i Microsoft Purview":::
1. Test forskellige søgejob i værktøjet Overvåg ny søgning ved hjælp af forskellige søgekriterier.
Nogle eksempler på forskellige søgninger omfatter følgende kriterier. Udforsk disse forskellige søgemetoder, mens du udfører søgninger i overvågningsloggen.
    - Søg på tværs af forskellige tidsrammer.
      - En dag
      - Uge
      - Måned
      - Flere måneder
    - Søg på tværs af de valgte brugere
    - Omrids søgningen ved hjælp af aktivitetsfeltet
    - Tilføjelse af en bestemt fil, mappe eller websted :::image type="content" source="../media/audit-search/audit-new-search-create.png" alt-text="Indstillinger for Overvågning af ny søgning i Microsoft Purview":::
1. Start yderligere 2-9 søgninger på overholdelsesportalen. Der kan maksimalt køres 10 søgejob parallelt på én konto.
1. Udforsk søgejobhistorikken, og vælg forskellige søgejob for at få deres tilsvarende data fra søgejobresultaterne. Resultaterne kan sorteres efter oprettelsestidspunktet ved at vælge den tilsvarende knap øverst i tabellen.
      :::image type="content" source="../media/audit-search/audit-new-search-columns.png" alt-text="Overvåg sorteringsindstillinger for nye søgeresultatkolonner i Microsoft Purview":::
1. Vælg et søgejob for at få vist resultaterne af jobbet i linjeelementformat. Udforsk de forskellige funktioner i brugergrænsefladen, herunder:
    - Referer til den komplette søgeforespørgsel øverst på siden, som indeholder alle de søgekriterier, der blev angivet, da den oprindelige søgning blev fuldført
    - Hvis du klikker på forskellige resultater for at få flere oplysninger i fly-out-vinduet
    - Filtrering på tværs af søgejobbet ved hjælp af IP-adresse, Bruger, Aktivitet, Dato, Element og Detaljer.
    - Eksport af både ufiltrerede og filtrerede søgninger
    - Sortering af resultaterne ved at klikke på de tilsvarende knapper øverst i tabellen, herunder Dato, IP-adresse (når det er relevant), Bruger, Aktivitet, Element og Detaljer (når det er relevant).
      :::image type="content" source="../media/audit-search/audit-new-search-result-details.png" alt-text="Overvåg oplysninger om nyt søgeresultat i Microsoft Purview":::

## <a name="audit-search-job-overview"></a>Oversigt over søgejob

- Søgejob kan tage følgende kriterier: Datointerval, Tidsinterval, Navn på søgejob, Aktiviteter, Brugere, Filer, Mapper og Websteder.
- Tekstfeltet fil,mappe eller webstedssøgning returnerer alle relaterede resultater for tilsvarende filer, mapper og websteder
- Søgejobbene køres nederst på søgesiden.
  - Søgejob kan være "Sat i kø", "Igangværende" og "Fuldført"
  - Der kan maksimalt udføres 10 "igangværende" søgejob samtidigt pr. bruger
- Fulde søgenavne for job kan ses ved at holde markøren over søgejobbet
- Søgejob viser søgenavn, status, status %, antal resultater, oprettelsestid og søgning efter

Figur 1.1 Værktøjet Til overvågning & søgejoboversigter

## <a name="audit-search-results-overview"></a>Oversigt over overvågningssøgningsresultater

- Søgeresultater vises i et linjeelement, når et søgejob er valgt
- Søgeforespørgslen vises øverst på siden med søgeresultater for reference og det samlede antal elementer
  > [!NOTE]
  > Det samlede resultattal trækker dubletter fra, og det kan derfor være mindre end antallet af elementer i hovedvinduet Til overvågning.
- Oplysninger om dato, IP-adresse, bruger, aktivitet og element findes på siden med søgeresultater for hvert element
- Vælg en aktivitet for at se et fly-out-vindue med flere oplysninger om aktiviteten
- Filtreringsfunktionen til søgeresultater kan hjælpe med at fortolke resultaterne.
- Eksport er fuldt funktionsdygtig og eksporterer alle søgejobelementer til en .csv fil. Eksport understøtter resultater op til 50 K. Figur 2.1 – Søgejobresultater Figur 2.2 – Søgejobfiltreringspanel Figur 2.3 – eksportknap

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

- **Er der et maksimalt antal søgejob pr. bruger?**
  Der er maksimalt 10 "igangværende" søgejob pr. bruger. Hvis en bruger kræver mere end 10 søgejob, skal vedkommende vente på, at et job i gang afsluttes eller slettes. Vi vil sætte pris på din feedback om denne grænse.
- **Sletter sletning af et søgejob back end-dataene?**
  Nej, sletningen af søgejobbet sletter kun søgejobdefinitionen og det tilknyttede søgeresultat.
