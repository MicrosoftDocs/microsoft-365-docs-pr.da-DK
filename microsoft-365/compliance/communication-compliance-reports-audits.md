---
title: Brug rapporter og overvågninger for kommunikation med overholdelse af angivne standarder
description: Få mere at vide om brug af rapporter om kommunikation med overholdelse af angivne standarder og overvågninger.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: e7e26451e2cf4786f73b16f74bedd46ca764f6ed
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173736"
---
# <a name="use-communication-compliance-reports-and-audits"></a>Brug rapporter og overvågninger for kommunikation med overholdelse af angivne standarder

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="reports"></a>Rapporter

Det nye dashboard **Rapporter** er den centrale placering til visning af alle rapporter om kommunikation med overholdelse af angivne standarder. Rapportwidgets giver et hurtigt overblik over de indsigter, der oftest kræves for at få en samlet vurdering af status for aktiviteter for kommunikation med overholdelse af angivne standarder. Oplysningerne i rapportwidgets kan ikke eksporteres. Detaljerede rapporter indeholder detaljerede oplysninger, der er relateret til specifikke områder for overholdelse af kommunikation, og giver mulighed for at filtrere, gruppere, sortere og eksportere oplysninger under gennemsyn. 

For filteret for datointerval vises dato og klokkeslæt for hændelser i UTC (Coordinated Universal Time). Når meddelelser filtreres for rapporter, bestemmer den anmodende brugers lokale dato/klokkeslæt resultaterne baseret på konverteringen af brugerens lokale dato/klokkeslæt til UTC. Hvis en bruger i USA f.eks. PDT (Pacific Daylight Time) filtrerer en rapport fra 30-08-2021 til 31-08-2021 kl. 00:00, indeholder rapporten meddelelser fra 30-08-2021 07:00 UTC til 8/31/2021 07:00 UTC. Hvis den samme bruger var i U.S. Eastern Daylight Time (EDT), da der filtreres kl. 00:00, indeholder rapporten meddelelser fra 30-08-2021 04:00 UTC til 31-08-2021 04:00 UTC.

![Dashboard til rapporter om kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-reports-dashboard.png)

**Dashboardet Rapporter** indeholder følgende rapportwidgets og detaljerede rapportlinks:

### <a name="report-widgets"></a>Rapportwidgets

- **Seneste politikforekomster**: Viser antallet af matches efter aktiv politik over tid.
- **Løste elementer efter politik**: Viser antallet af beskeder om politikmatch, der er løst af politikken over tid.
- **Brugere med de fleste politikmatch**: Viser brugerne (eller anonymiserede brugernavne) og antallet af politikmatch for en given periode.
- **Politik med de fleste matches**: Viser politikkerne og antallet af matches for en given periode, rangeret højest til laveste for matches.
- **Eskaleringer efter politik**: viser antallet af eskaleringer pr. politik over en given tid.

### <a name="detailed-reports"></a>Detaljerede rapporter

Brug indstillingen *Eksportér* til at oprette en .csv fil, der indeholder rapportdetaljerne for en detaljeret rapport. Indstillingen *Eksportér* rapport understøtter filstørrelser, der downloades op til 3 MB.

- **Politikindstillinger og status**: Giver et detaljeret kig på politikkonfiguration og -indstillinger samt den generelle status for hver af politikken (matches og handlinger) i meddelelser. Indeholder politikoplysninger, og hvordan politikker er knyttet til brugere og grupper, placeringer, korrekturprocenter, korrekturlæsere, status og hvornår politikken sidst blev ændret. Brug indstillingen *Eksportér* til at oprette en .csv fil, der indeholder rapportoplysningerne.
- **Elementer og handlinger pr. politik**: Gennemse og eksportér tilsvarende elementer og afhjælpningshandlinger pr. politik. Indeholder politikoplysninger, og hvordan politikker er knyttet til:

    - Elementer, der stemmer overens
    - Eskalerede elementer
    - Løste elementer
    - Mærket som kompatibel
    - Mærket som ikke-kompatibel
    - Mærket som tvivlsom
    - Elementer, der afventer gennemsyn
    - Bruger med besked
    - Sag oprettet

- **Element og handlinger pr. placering**: Gennemse og eksportér tilsvarende elementer og afhjælpningshandlinger pr. Microsoft 365 placering. Indeholder oplysninger om, hvordan arbejdsbelastningsplatforme er knyttet til:

    - Elementer, der stemmer overens
    - Eskalerede elementer
    - Løste elementer
    - Mærket som kompatibel
    - Mærket som ikke-kompatibel
    - Mærket som tvivlsom
    - Elementer, der afventer gennemsyn
    - Bruger med besked
    - Sag oprettet

- **Aktivitet efter bruger**: Gennemse og eksportér matchende elementer og afhjælpningshandlinger pr. bruger. Indeholder oplysninger om, hvordan brugere er knyttet til:

    - Elementer, der stemmer overens
    - Eskalerede elementer
    - Løste elementer
    - Mærket som kompatibel
    - Mærket som ikke-kompatibel
    - Mærket som tvivlsom
    - Elementer, der afventer gennemsyn
    - Bruger med besked
    - Sag oprettet

- **Type af følsomme oplysninger pr. placering** (prøveversion): Gennemse og eksportér oplysninger om registrering af følsomme oplysningstyper og de tilknyttede kilder i politikker for kommunikation med overholdelse af angivne standarder. Omfatter den samlede total og den specifikke opdeling af forekomster af følsomme oplysninger i de kilder, der er konfigureret i din organisation. Værdierne for hver tredjepartskilde vises i separate kolonner i .csv-filen. Eksempler er:

    - **Mail**: Følsomme oplysningstyper, der er registreret i Exchange mails.
    - **Teams**: Følsomme informationstyper, der registreres i Microsoft Teams kanaler og chatbeskeder.
    - **Skype for Business**: Følsomme informationstyper, der registreres i Skype til forretningskommunikation.
    - **Yammer**: Typer af følsomme oplysninger, der registreres i Yammer indbakker, indlæg, chats og svar.
    - **Tredjepartskilder**: Følsomme oplysningstyper, der registreres for aktiviteter, der er knyttet til tredjepartsconnectors, som er konfigureret i din organisation. Hvis du vil se opdelingen af tredjepartskilder for en bestemt følsom oplysningstype i rapporten, skal du holde musen over værdien for typen af følsomme oplysninger i kildekolonnen fra tredjepart.
    - **Andet**: Følsomme informationstyper, der bruges til intern systembehandling. Valg eller fravalg af denne kilde til rapporten påvirker ikke nogen værdier.

### <a name="message-details-report-preview"></a>Rapport med meddelelsesoplysninger (prøveversion)

Opret brugerdefinerede rapporter, og gennemse detaljer for meddelelser i bestemte politikker under fanen **Politikker** . Disse rapporter kan bruges til samlet gennemgang af meddelelser og til at oprette et snapshot af rapporten for status for meddelelser i en tidsperiode, der kan tilpasses. Når du har oprettet en rapport, kan du få vist og downloade detaljerapporten som en .csv-fil under fanen **Rapporter med meddelelsesoplysninger** .

![Detaljeret rapport over meddelelse om kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-message-detail-report.png)

Hvis du vil oprette en ny rapport med meddelelsesoplysninger, skal du udføre følgende trin:

1. Log på Microsoft Purview-overholdelsesportalen med en konto, der er medlem af rollegruppen *Communication Compliance Investigators* .
2. Gå til fanen **Politikker** , vælg en politik, og vælg derefter **Opret rapport med meddelelsesoplysninger**.
3. I ruden **Opret rapport med meddelelsesoplysninger** skal du angive et navn til rapporten i feltet **Rapportnavn** .
4. Vælg en *startdato* og *en slutdato* for rapporten i **Vælg et datointerval**.
5. Vælg **Opret**.
6. Bekræftelsen på oprettelse af rapporten vises.

Afhængigt af antallet af elementer i rapporten kan det tage et par minutter til timer, før rapporten er klar til at blive downloadet. Du kan kontrollere status under fanen Meddelelsesdetaljer om rapporter. Rapportstatus er *i gang* eller *Klar til download*. Du kan have op til 15 separate rapporter, der behandles samtidigt. Hvis du vil downloade en rapport, skal du vælge en rapport i tilstanden *Klar til at downloade* og vælge **Download rapport**.

> [!NOTE]
> Hvis den valgte tidsperiode ikke returnerer nogen meddelelsesresultater i rapporten, var der ikke nogen meddelelser for den valgte tidsperiode. Rapporten er tom.

Rapporter med meddelelsesoplysninger indeholder følgende oplysninger for hvert meddelelseselement i politikken:

- **Match-id**: entydigt id for meddelelsen i politikken.
- **Afsender**: meddelelsens afsender.
- **Modtagere**: de modtagere, der er inkluderet i meddelelsen.
- **Dato for afsendelse**: Den dato, hvor meddelelsen blev sendt.
- **Matchdato**: Den dato, hvor meddelelsen var et match for politikbetingelserne.
- **Om**: Meddelelsens emne.
- **Indeholder vedhæftede filer**: status for eventuelle vedhæftede filer i meddelelsen. Værdier er enten Ja eller Nej.
- **Politiknavn**: Navnet på den politik, der er knyttet til meddelelsen. Denne værdi vil være den samme for alle meddelelser i rapporten.
- **Elementstatus**: Status for meddelelseselementet i politikken. Værdier afventer eller løses.
- **Tags**: de mærker, der er tildelt meddelelsen. Værdier er tvivlsomme, kompatible eller ikke-kompatible.
- **Nøgleordsforekomster**: Nøgleordsforekomster for meddelelsen.
- **Korrekturlæsere: Korrekturlæsere** er tildelt til meddelelsen.
- **Ventende i (dage)**: det antal dage, meddelelsen har været i ventende tilstand. Værdien er 0 for løste meddelelser.
- **Kommentar til løst**: kommentarerne til den meddelelse, der blev angivet, da den blev løst.
- **Løst dato**: den dato og det klokkeslæt, hvor meddelelsen blev løst.
- **Senest opdateret af**: brugernavnet på den seneste opdatering.
- **Senest opdateret** den: den dato og det klokkeslæt, hvor meddelelsen sidst blev opdateret.
- **Oversigt over kommentarer**: liste over alle kommentarer til meddelelsen, herunder kommentarforfatter og dato/klokkeslæt for kommentaren.

## <a name="audit"></a>Revision

I nogle tilfælde skal du give oplysninger til revisorer for lovgivning eller overholdelse af angivne standarder for at bevise overvågning af brugeraktiviteter og kommunikation. Disse oplysninger kan være en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når en politik for kommunikation med overholdelse af angivne standarder ændres. Politikker for kommunikation med overholdelse af angivne standarder har indbyggede overvågningsspor til komplet parathed til interne eller eksterne revisioner. Detaljerede overvågningshistorikker for hver oprettelses-, redigerings- og sletningshandling registreres af dine kommunikationspolitikker for at give bevis for tilsynsprocedurer.

> [!IMPORTANT]
> Overvågning skal være aktiveret for din organisation, før hændelser for overholdelse af angivne standarder registreres. Hvis du vil aktivere overvågning, skal du se [Aktivér overvågningsloggen](communication-compliance-configure.md#step-2-required-enable-the-audit-log). Når aktiviteter udløser hændelser, der registreres i Microsoft 365 overvågningslog, kan det tage op til 48 timer, før disse hændelser kan ses i politikker for kommunikation med overholdelse af angivne standarder.

Hvis du vil have vist opdateringsaktiviteter for politikken for kommunikation, skal du vælge kontrolelementet **Eksportér politikopdateringer** på hovedsiden for en hvilken som helst politik. Du skal være tildelt rollerne *Global administrator* eller *Administrator af kommunikationsoverholdelse* for at eksportere opdateringsaktiviteter. Denne handling genererer en overvågningsfil i .csv-format, der indeholder følgende oplysninger:

|**Feltet**|**Detaljer**|
|:-----|:-----|
| **Oprettelsesdato** | Den dato, hvor opdateringsaktiviteten blev udført i en politik. |
| **UserIds** | Den bruger, der udførte opdateringsaktiviteten i en politik. |
| **Operationer** | De opdateringshandlinger, der udføres på politikken. |
| **Overvågningsdata** | Dette felt er den primære datakilde for alle politikopdateringsaktiviteter. Alle opdateringsaktiviteter registreres og adskilles af kommaafgrænsere. |

Hvis du vil have vist aktiviteter til gennemgang af overholdelse af angivne standarder for en politik, skal du vælge kontrolelementet **Eksportér aktiviteter til gennemsyn** på siden **Oversigt** for en bestemt politik. Du skal være tildelt rollerne *Global administrator* eller *Administrator af kommunikationsoverholdelse* for at kunne eksportere korrekturaktiviteter. Denne handling genererer en overvågningsfil i .csv-format, der indeholder følgende oplysninger:

|**Feltet**|**Detaljer**|
|:-----|:-----|
| **Oprettelsesdato** | Den dato, hvor korrekturaktiviteten blev udført i en politik. |
| **UserIds** | Den bruger, der udførte gennemsynsaktiviteten i en politik. |
| **Operationer** | De korrekturhandlinger, der er udført på politikken. |
| **Overvågningsdata** | Dette felt er den primære datakilde for alle aktiviteter til gennemsyn af politikker. Alle korrekturaktiviteter registreres og adskilles af kommaafgrænsere. |

Du kan også få vist overvågningsaktiviteter i den samlede overvågningslog eller med PowerShell-cmdlet'en [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) . Du kan få mere at vide om politikker for opbevaring af overvågningslog under [Administrer opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md).

Følgende eksempel returnerer f.eks. aktiviteterne for alle overvågningsaktiviteter (politikker og regler):

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

I dette eksempel returneres opdateringsaktiviteterne for politikkerne for kommunikation med overholdelse af angivne standarder:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

I dette eksempel returneres aktiviteter, der stemmer overens med dine aktuelle politikker for overholdelse af angivne standarder for kommunikation:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

Overholdelsespolitik for kommunikation gemmes i en overvågningspostkasse for hver politik. I nogle tilfælde skal du muligvis kontrollere størrelsen på din overvågningspostkasse for en politik for at sikre, at du ikke nærmer dig den aktuelle lagerstørrelse på 100 GB eller 1 million meddelelser. Hvis grænsen for postkassen nås, registreres politikforekomster ikke, og du skal oprette en ny politik (med de samme indstillinger) for at fortsætte med at hente match for de samme aktiviteter.

Hvis du vil kontrollere størrelsen på en tilsynspostkasse for en politik, skal du udføre følgende trin:

1. Brug [cmdlet'en Forbind-ExchangeOnline](/powershell/module/exchange/connect-exchangeonline) i Exchange Online PowerShell V2-modulet til at oprette forbindelse til Exchange Online PowerShell ved hjælp af moderne godkendelse.
2. Kør følgende kommando i PowerShell:

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```
