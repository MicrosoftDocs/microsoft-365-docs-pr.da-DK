---
title: Funktionstest på Test base
description: Detaljer om, hvordan du tester dit program med dine eksisterende automatiserede funktionstests
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: f64480d66cd91dc4b08f9694331cfe0d9c130ee4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592473"
---
# <a name="functional-testing"></a>Funktionstest

Som softwareleverandør kan du nu udføre brugerdefinerede funktionelle test ved hjælp af din foretrukne teststruktur – via selvbetjeningstestbasen til M365-portalen. 

Da vi indledningsvist lancerede tjenesten, tilbydes der Out of box-tests, som er et foruddefineret sæt test, der drives via standardiseret scripting. Dette kunne dog ikke sikre fuld testdækning for mange uafhængige softwareleverandører. 

Derfor giver vi som svar på din feedback vores isv-filer mulighed for at uploade automatiserede funktionstests.

Hvis du vil bruge denne funktion, skal du følge trinnene nedenfor:

1. Upload filer (binære, afhængigheder og scripts) som en enkelt .zip pakke.
2. Vælg, om du vil genstarte test af virtuelle maskiner (VMs) på forskellige eksekveringspunkter.
3. Administrer tilgængelige indstillinger for dine scripts.
4. Vælg, hvornår du vil anvende Windows på VM under udførelse.

Detaljerede beskrivelser af ovenstående trin er fremhævet nedenfor:

**Upload en funktionel testpakke**

For at komme i gang skal du gå til Upload-siden og vælge Upload nyt program under Programkatalog i navigationsmenuen i venstre side på Test Base til M365-portalen i Azure. Derfra:

Fane 1 – Angiv grundlæggende oplysninger. Angiv navn og version af dit program. I indstillingen Testtype skal du vælge ```Functional tests```. 

*Bemærk, at OOB (Out of Box) er påkrævet som standard.*


![Vælg fanen funktionstest.](Media/functional_testing_tab1.png)

Tab 2 – Upload komponenterne i pakken ved at uploade en zip-fil med hele testen (binære, afhængigheder, scripts osv.). 

Se aka.ms/usl-package-outline, hvis du vil have mere at vide. (Bemærk: Både out of box-testscripts og indholdet af funktionelle test skal placeres i den samme zip-fil). I øjeblikket er filstørrelsen begrænset til 2 GB.

Fane 3 – Konfigurer de kørende og funktionelle testopgaver. Her skal du vælge stien til de PowerShell-scripts, der vil installere, starte, lukke og fjerne dit program (for Out of Box) samt stien(e) til alle dine brugerdefinerede scripts for at udføre din funktionelle test. **(Bemærk! Et script til at fjerne dit program er valgfrit).**

I øjeblikket kan du overføre mellem 1 og 8 scripts til dine funktionelle test. (Skriv en kommentar til dette indlæg, hvis du har brug for flere scripts!)

![Upload op til 8 scripts med funktionstest.](Media/functional_testing_tab3.png)

(Valgfrit) Konfigurer en genstart efter installationen. Nogle programmer kræver en genstart efter installationen. 

Vælg ```Reboot After Execution``` det specifikke script på fanen Opgaver, hvis du vil have en genstart udført efter udførelse af det pågældende script.

Fane 4 – Vælg, hvornår Windows installeres: Programmet for Windows-opdateringsrettelse udføres før et script efter eget valg. Det anbefales, at du installerer Windows opdatering efter programmets installation for at efterligne dine virkelige scenarier for anvendelse af programmer tæt.

![Opdateringen Windows blive installeret efter et bestemt script.](Media/functional_testing_tab4.png)

Fane 5 – Gennemse og opret pakken. Når du har gennemført ovenstående trin, skal du vælge ```Create``` for at afslutte overførselsprocessen.

Når pakken er blevet oprettet, kan du kontrollere bekræftelsesstatus for din pakke.

Vi kører en indledende test for at installere, starte, lukke og fjerne dit program. Dette giver os mulighed for at bekræfte, at din pakke kan installere på vores tjeneste uden fejl.

Bekræftelsesprocessen kan tage op til 24 timer. Når bekræftelsen er fuldført, kan du se status i ```Manage packages``` menuen, som ville være en af to poster:

1. Bekræftelse lykkes: Pakken testes automatisk i forhold til foreløbige opdateringer Windows de os-builds, du har valgt.
eller
2. Bekræftelsen mislykkes: Du skal undersøge årsagerne til fejlen, løse problemet og overføre pakken igen.

Du får også besked om et resultat via meddelelsesikonet på Azure-portalen.
