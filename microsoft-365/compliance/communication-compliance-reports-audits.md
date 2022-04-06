---
title: Brug rapporter og revisioner i forbindelse med overholdelse af kommunikation
description: Få mere at vide om at bruge rapporter om overholdelse af kommunikation og revisioner.
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
ms.openlocfilehash: a65a72538afa3684cf4ad9351d30313e0dc43b8d
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63606721"
---
# <a name="use-communication-compliance-reports-and-audits"></a>Brug rapporter og revisioner i forbindelse med overholdelse af kommunikation

## <a name="reports"></a>Rapporter

Det nye dashboard **Rapporter er** den centrale placering til visning af alle rapporter om overholdelse af kommunikation. Rapportwidgets giver en hurtig oversigt over de indsigter, der oftest er nødvendige for en overordnet vurdering af status for aktiviteter til overholdelse af kommunikation. Oplysningerne i rapportwidgets kan ikke eksporteres. Detaljerede rapporter giver detaljerede oplysninger om specifikke kommunikationsoverholdelsesområder og giver mulighed for at filtrere, gruppere, sortere og eksportere oplysninger under gennemsyn. 

For datoområdefilteret vises dato og klokkeslæt for begivenheder i UTC (Coordinated Universal Time). Ved filtrering af meddelelser for rapporter bestemmer den anmodende brugers lokale dato/klokkeslæt resultaterne baseret på konverteringen af brugerens lokale dato/klokkeslæt til UTC. Hvis en bruger i AMERIKANSK PACIFIC Daylight Time (PDT) filtrerer en rapport fra 30-08-2021 til 31-08-2021 kl. 00:00, indeholder rapporten meddelelser fra 30-08-2021 07:00 UTC til 31-08-2021 07:00 UTC. Hvis den samme bruger var i det amerikanske Eastern Daylight Time (EDT), når der blev filtreret kl. 00:00, medtager rapporten meddelelser fra 30-08-2021 04:00 UTC til d. 31-08-2021 04:00 UTC.

![Dashboard til rapporter om overholdelse af kommunikation.](../media/communication-compliance-reports-dashboard.png)

**Dashboardet Rapporter indeholder** følgende rapportwidgets og links til detaljerede rapporter:

### <a name="report-widgets"></a>Rapportwidgets

- **Seneste politik matches**: Viser antallet af matches af aktive politikker over tid.
- **Løste elementer efter politik**: Viser antallet af beskeder om match af politikker, som er blevet løst af politikken over tid.
- **Brugere med de fleste politikmatches**: viser brugerne (eller anonymiserede brugernavne) og antallet af politikoverensstemmelser for en given periode.
- **Politik med de fleste matches**: Viser politikkerne og antallet af matches for en given periode, rangeret fra højeste til laveste for match.
- **Eskalering efter politik**: Viser antallet af eskaleringer pr. politik i et givet tidsrum.

### <a name="detailed-reports"></a>Detaljerede rapporter

Brug indstillingen *Eksportér* til at oprette en .csv fil, der indeholder rapportdetaljerne til en hvilken som helst detaljeret rapport.

- **Politikindstillinger og -status**: giver et detaljeret kig på politikkonfiguration og indstillinger samt den generelle status for hver af politikken (matches og handlinger) for meddelelser. Omfatter politikoplysninger, og hvordan politikker er knyttet til brugere og grupper, placeringer, gennemse procentdele, korrekturlæsere, status og hvornår politikken sidst blev ændret. Brug indstillingen *Eksportér* til at oprette en .csv fil, der indeholder rapportdetaljerne.
- **Elementer og handlinger pr. politik**: Gennemse og eksportér matchende elementer og afhjælpningshandlinger pr. politik. Omfatter politikoplysninger, og hvordan politikker er knyttet til:

    - Elementer, der er matchet
    - Eskalerede elementer
    - Løste elementer
    - Mærket som kompatibel
    - Mærket som ikke-kompatibel
    - Mærket som tvivlsomme
    - Elementer, der venter på gennemsyn
    - Brugeren får besked
    - Sag oprettet

- **Element og handlinger pr. placering**: Gennemse og eksportér matchende elementer, og afhjælpningshandlinger pr. Microsoft 365 placering. Indeholder oplysninger om, hvordan arbejdsbelastningsplatforme er knyttet til:

    - Elementer, der er matchet
    - Eskalerede elementer
    - Løste elementer
    - Mærket som kompatibel
    - Mærket som ikke-kompatibel
    - Mærket som tvivlsomme
    - Elementer, der venter på gennemsyn
    - Brugeren får besked
    - Sag oprettet

- **Aktivitet efter bruger**: Gennemse og eksportér matchende elementer samt afhjælpningshandlinger pr. bruger. Indeholder oplysninger om, hvordan brugere er knyttet til:

    - Elementer, der er matchet
    - Eskalerede elementer
    - Løste elementer
    - Mærket som kompatibel
    - Mærket som ikke-kompatibel
    - Mærket som tvivlsomme
    - Elementer, der venter på gennemsyn
    - Brugeren får besked
    - Sag oprettet

- **Type af følsomme oplysninger pr. placering** (forhåndsvisning): Gennemse og eksportér oplysninger om registrering af følsomme oplysningstyper og de tilknyttede kilder i politikker for overholdelse af kommunikation. Omfatter den samlede mængde og den specifikke opdeling af følsomme oplysningstypeforekomster i de kilder, der er konfigureret i organisationen. Værdierne for hver tredjepartskilde vises i separate kolonner i .csv fil. Her er nogle eksempler:

    - **Mail**: Følsomme oplysningstyper, der registreres Exchange e-mail-meddelelser.
    - **Teams**: Følsomme oplysningstyper, der registreres i Microsoft Teams kanaler og chatmeddelelser.
    - **Skype for Business**: Følsomme oplysningstyper, der registreres i Skype til virksomhedskommunikation.
    - **Yammer**: Typer af følsomme oplysninger, der registreres Yammer indbakker, indlæg, chats og svar.
    - **Tredjepartskilder: Følsomme** oplysningstyper registreres for aktiviteter, der er knyttet til tredjepartsforbindelser, der er konfigureret i organisationen. Hvis du vil se en opdeling af tredjepartskilder for en bestemt type af følsomme oplysninger i rapporten, skal du holde musen over værdien for typen af følsomme oplysninger i kolonnen Tredjepartskilde.
    - **Andet**: Typer af følsomme oplysninger, der bruges til intern systembehandling. Valg eller fravalg af denne kilde til rapporten påvirker ikke nogen værdier.

### <a name="message-details-report-preview"></a>Rapport med meddelelsesdetaljer (eksempel)

Opret brugerdefinerede rapporter og gennemse detaljer for meddelelser, der er indeholdt i bestemte politikker **på fanen** Politikker. Disse rapporter kan bruges til alle gennemgange af meddelelser og til at oprette et øjebliksbillede af rapporten for statussen for meddelelser i en brugerdefineret tidsperiode. Når du har oprettet en rapport, kan du få vist og downloade detaljerapporten som en .csv fil på fanen **Rapporter med meddelelsesdetaljer** .

![Detaljerapport over meddelelser om overholdelse af kommunikation.](../media/communication-compliance-message-detail-report.png)

Hvis du vil oprette en rapport med oplysninger om en ny meddelelse, skal du udføre følgende trin:

1. Log på Microsoft 365 Overholdelsescenter med en konto, der er medlem af rollegruppen *Overholdelse af regler* og standarder i kommunikation.
2. Gå til fanen **Politikker** , vælg en politik, og vælg derefter **Opret rapport med meddelelsesdetaljer**.
3. I **ruden Opret rapport med meddelelsesdetaljer** skal du angive et navn til rapporten i **feltet Rapportnavn** .
4. Vælg **en Startdato og** Slutdato for *rapporten i* *Vælg et* datointerval.
5. Vælg **Opret**.
6. Bekræftelsen af oprettelse af rapporten vises.

Afhængigt af antallet af elementer i rapporten kan det tage et par minutter til timer, før rapporten er klar til at blive downloadet. Du kan kontrollere status under fanen Rapporter med meddelelsesdetaljer. Status for rapporten *er i gang* eller *Klar til at blive downloadet*. Du kan have op til 15 separate rapporter, der behandles samtidigt. Hvis du vil downloade en rapport, skal du vælge en rapport *i tilstanden Klar til at downloade* og vælge **Download rapport**.

> [!NOTE]
> Hvis den valgte tidsperiode ikke returnerer nogen meddelelsesresultater i rapporten, var der ikke nogen meddelelser for den valgte tidsperiode. Rapporten vil være tom.

Rapporter med meddelelsesdetaljer indeholder følgende oplysninger for hvert meddelelseselement i politikken:

- **Match-id**: Entydigt id for meddelelsen i politikken.
- **Afsender**: afsenderen af meddelelsen.
- **Modtagere**: Modtagerne af meddelelsen.
- **Dato sendt**: den dato, hvor meddelelsen blev sendt.
- **Matchdato**: den dato, hvor meddelelsen opfylder politikbetingelserne.
- **Emne**: meddelelsens emne.
- **Indeholder vedhæftede** filer: status for eventuelle vedhæftede filer i meddelelsen. Værdierne er enten Ja eller Nej.
- **Politiknavn**: navnet på den politik, der er knyttet til meddelelsen. Denne værdi er den samme for alle meddelelser i rapporten.
- **Elementstatus**: status for meddelelseselementet i politikken. Værdierne er Afventende eller Løst.
- **Mærker**: de mærker, der er tildelt til meddelelsen. Værdier er tvivlsomme, kompatible eller ikke-kompatible.
- **Nøgleordet matcher**: nøgleordet matcher for meddelelsen.
- **Korrekturlæsere**: Korrekturlæsere tildelt meddelelsen.
- **Afventer i (dage)**: antallet af dage, meddelelsen har været i en ventende tilstand. For løste meddelelser er værdien 0.
- **Kommentar til løst**: kommentarerne til den meddelelse, der blev angivet, da den blev løst.
- **Løst dato**: den dato og det klokkeslæt, hvor meddelelsen blev løst.
- **Senest opdateret af**: brugernavnet til den seneste opdatering.
- **Senest opdateret den**: den dato og det klokkeslæt, hvor meddelelsen sidst blev opdateret.
- **Oversigt over kommentarer**: liste over alle kommentarer til beskeden, herunder kommentarforfatter og dato/klokkeslæt for kommentaren.

## <a name="audit"></a>Overvågning

I nogle tilfælde skal du give oplysninger til lovgivningsmæssige revisorer eller revisionsrevisorer for at bevise overvågning af brugeraktiviteter og kommunikation. Disse oplysninger kan være en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når en politik for overholdelse af kommunikation ændres. Politikker for overholdelse af kommunikation har indbyggede revisionsspor for komplet parathed til interne eller eksterne revisioner. Detaljerede revisionshistorikker for hver handling, du opretter, redigerer og sletter, registreres af dine kommunikationspolitikker for at levere dokumentation for kontrolprocedurer.

> [!IMPORTANT]
> Overvågning skal være aktiveret for din organisation, før hændelser i forbindelse med overholdelse af kommunikation registreres. Se Aktivér overvågningsloggen for [at aktivere overvågning](communication-compliance-configure.md#step-2-required-enable-the-audit-log). Når aktiviteter udløser hændelser, der registreres i Microsoft 365-overvågningsloggen, kan der gå op til 48 timer, før disse hændelser kan ses i politikker for overholdelse af kommunikation.

Hvis du vil have vist opdateringsaktiviteter for politikker til overholdelse af kommunikation, **skal** du vælge kontrolelementet Eksportér politikopdateringer på hovedsiden for enhver politik. Du skal have tildelt *rollerne Global administrator eller* *Kommunikationsoverholdelsesadministrator* for at eksportere opdateringsaktiviteter. Denne handling genererer en overvågningsfil i det .csv, der indeholder følgende oplysninger:

|**Felt**|**Detaljer**|
|:-----|:-----|
| **CreationDate** | Den dato, hvor opdateringsaktiviteten blev udført i en politik. |
| **UserIds** | Den bruger, der udførte opdateringsaktiviteten i en politik. |
| **Handlinger** | Opdateringshandlingerne, der udføres på politikken. |
| **AuditData** | Dette felt er den primære datakilde for alle politikopdateringsaktiviteter. Alle opdateringsaktiviteter registreres og adskilles af kommaseparatorer. |

Hvis du vil have vist aktiviteter til gennemsyn af overholdelse af  kommunikation for en politik, skal du vælge kontrolelementet Eksportér gennemsyn-aktiviteter **på** siden Oversigt for en bestemt politik. Du skal have tildelt *rollerne Global administrator eller* *Kommunikationsoverholdelsesadministrator* for at eksportere gennemsynsaktiviteter. Denne handling genererer en overvågningsfil i det .csv, der indeholder følgende oplysninger:

|**Felt**|**Detaljer**|
|:-----|:-----|
| **CreationDate** | Den dato, hvor gennemsynsaktiviteten blev udført i en politik. |
| **UserIds** | Den bruger, der udførte gennemsynsaktiviteten i en politik. |
| **Handlinger** | De gennemsynshandlinger, der udføres på politikken. |
| **AuditData** | Dette felt er den vigtigste datakilde for alle politikgennemsynsaktiviteter. Alle gennemsynsaktiviteter registreres og adskilles af kommaseparatorer. |

Du kan også få vist overvågningsaktiviteter i den samlede overvågningslog eller med [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell-cmdlet'en. Du kan få mere at vide om opbevaringspolitikker for overvågningslogfiler under [Administrere opbevaringspolitikker for overvågningslogfiler](audit-log-retention-policies.md).

I følgende eksempel returneres aktiviteterne for alle aktiviteter til kontrolvurdering (politikker og regler):

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

I dette eksempel returneres opdateringsaktiviteterne for dine politikker for overholdelse af regler og standarder i kommunikation:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

I dette eksempel returneres aktiviteter, der svarer til dine aktuelle politikker for overholdelse af regler og standarder i kommunikation:

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch
```

Matches af kommunikationspolitik gemmes i en postkasse til overvågning for hver politik. I nogle tilfælde kan det være nødvendigt at kontrollere størrelsen på din postkasse til overvågning for en politik for at sikre, at du ikke nærmer dig den aktuelle 100 GB-lagerstørrelse eller 1 million meddelelsesgrænse. Hvis postkassegrænsen er nået, registreres politikoverensstemmelse ikke, og du skal oprette en ny politik (med de samme indstillinger) for at fortsætte med at registrere matches for de samme aktiviteter.

Hvis du vil kontrollere størrelsen på en postkasse til overvågning for en politik, skal du udføre følgende trin:

1. Brug [Forbind-ExchangeOnline-cmdlet'en](/powershell/module/exchange/connect-exchangeonline) i Exchange Online PowerShell V2-modulet til at oprette forbindelse til Exchange Online PowerShell ved hjælp af moderne godkendelse.
2. Kør følgende kommando i PowerShell:

    ```PowerShell
    ForEach ($p in Get-SupervisoryReviewPolicyV2 | Sort-Object Name)
    {
       "<Name of your communication compliance policy>: " + $p.Name
       Get-MailboxStatistics $p.ReviewMailbox | ft ItemCount,TotalItemSize
    }
    ```
