---
title: Vejledning til sikkerhedshandlinger for Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: En præskriptiv strategibog til SecOps-personale til administration af Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 389d48f5b7952f3d89a0bb75746babaa9430e7c5
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "66858590"
---
# <a name="microsoft-defender-for-office-365-security-operations-guide"></a>vejledning til Microsoft Defender for Office 365 sikkerhedshandlinger

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Denne artikel indeholder en oversigt over kravene og opgaverne for korrekt drift af Microsoft Defender for Office 365 i din organisation. Disse opgaver er med til at sikre, at dit SOC (Security Operations Center) leverer en pålidelig tilgang af høj kvalitet til at beskytte, registrere og reagere på mail- og samarbejdsrelaterede sikkerhedstrusler.

I resten af denne vejledning beskrives de påkrævede aktiviteter for SecOps-personale. Aktiviteterne er grupperet i præskriptive daglige, ugentlige, månedlige og ad hoc-opgaver.

En medfølgende artikel til denne vejledning indeholder en oversigt over[, hvordan du administrerer hændelser og beskeder fra Defender for Office 365 på siden Hændelser på portalen Microsoft 365 Defender](mdo-sec-ops-manage-incidents-and-alerts.md).

Vejledningen [til Microsoft 365 Defender sikkerhedshandlinger](/microsoft-365/security/defender/integrate-microsoft-365-defender-secops) indeholder yderligere oplysninger, som du kan bruge til planlægning og udvikling.

## <a name="daily-activities"></a>Daglige aktiviteter

### <a name="monitor-the-microsoft-365-defender-incidents-queue"></a>Overvåg køen Microsoft 365 Defender hændelser

Siden **Hændelser** i Microsoft 365 Defender-portalen på <https://security.microsoft.com/incidents-queue> (også kaldet _hændelseskøen_) giver dig mulighed for at administrere og overvåge hændelser fra følgende kilder i Defender for Office 365:

- [Beskeder](../../compliance/alert-policies.md#default-alert-policies).
- [Automatiseret undersøgelse og svar (AIR)](automated-investigation-response-office.md).

Du kan få flere oplysninger om køen Hændelser under [Prioriter hændelser i Microsoft 365 Defender](../defender/incident-queue.md).

Din triageplan til overvågning af hændelseskøen skal bruge følgende rækkefølge for hændelser:

1. **Der blev fundet en potentielt skadelig URL-adresse**.
2. **Brugeren er begrænset til at sende mail**.
3. **Mistænkelige mail afsendelse mønstre opdaget**.
4. **Mail, der er rapporteret af brugeren som malware eller phish**, og **Flere brugere rapporterede mail som malware eller phish**.
5. **Mails, der indeholder skadelig fil, som er fjernet efter levering**, **Mails, der indeholder skadelig URL-adresse fjernet efter levering**, og **Mails fra en kampagne, der er fjernet efter levering**.
6. **Phish leveret på grund af en TILSIDESÆTTELSE AF ETR**, **Phish leveret, fordi en brugers mappe med uønsket mail er deaktiveret**, og **Phish leveres på grund af en politik for ip-tilladelse**
7. **Malware ikke zapped fordi ZAP er deaktiveret** og **Phish ikke zapped fordi ZAP er deaktiveret**.

Administration af hændelseskøen og de ansvarlige personer er beskrevet i følgende tabel:

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Triage hændelser i køen Hændelser på <https://security.microsoft.com/incidents-queue>.|Daglige|Bekræft, at alle hændelser med **mellemstor** og **høj** alvorsgrad fra Defender for Office 365 er triaged.|Team til sikkerhedshandlinger|
|Undersøg og udfør svarhandlinger på hændelser.|Daglige|Undersøg alle hændelser, og udfør aktivt de anbefalede eller manuelle svarhandlinger.|Team til sikkerhedshandlinger|
|Løs hændelser.|Daglige|Hvis hændelsen er blevet afhjælpet, skal du løse hændelsen. Løsning af hændelsen løser alle sammenkædede og relaterede aktive beskeder.|Team til sikkerhedshandlinger|
|Klassificer hændelser.|Daglige|Klassificer hændelser som true eller false. Angiv trusselstypen for true-beskeder. Denne klassificering hjælper dit sikkerhedsteam med at se trusselsmønstre og forsvare din organisation mod dem.|Team til sikkerhedshandlinger|

### <a name="manage-false-positive-and-false-negative-detections"></a>Administrer registreringer af falske positive og falske negative

I Defender for Office 365 kan du administrere falske positiver (god post markeret som dårlig) og falske negativer (dårlig post er tilladt) på følgende placeringer:

- [Portalen Indsendelser (administratorindsendelser).](admin-submission.md).
- Listen [over tilladte/blokerede lejere](tenant-allow-block-list.md)
- [Trusselsoversigt](threat-explorer.md)

Du kan få flere oplysninger i afsnittet [Administrer falske positive og falske negative registreringer](#manage-false-positive-and-false-negative-detections) senere i denne artikel.

Falsk positiv og falsk negativ administration og de ansvarlige personer er beskrevet i følgende tabel:

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Send falske positiver og falske negativer til Microsoft på <https://security.microsoft.com/reportsubmission>.|Daglige|Angiv signaler til Microsoft ved at rapportere forkerte mails, URL-adresser og filregistreringer.|Team til sikkerhedshandlinger|
|Analysér oplysninger om indsendelse af administrator.|Daglige|Forstå følgende faktorer for de indsendelser, du indsender til Microsoft: <ul><li>Det, der forårsagede falsk positiv eller falsk negativ.</li><li>Tilstanden for din Defender for Office 365 konfiguration på tidspunktet for indsendelsen.</li><li>Uanset om du har brug for at foretage ændringer i Defender for Office 365 konfiguration.</li></ul>|Team til sikkerhedshandlinger <br/><br/> Sikkerhedsadministration|
|Tilføj blokposter på listen over tilladte/blokerede lejere på <https://security.microsoft.com/tenantAllowBlockList>.|Daglige|Brug listen over tilladte/blokerede lejere til at tilføje blokposter for registreringer af falske negative URL-adresser, filer eller afsendere efter behov.|Team til sikkerhedshandlinger|
|Frigiv falske negativer fra karantæne.|Daglige|Når modtageren har bekræftet, at meddelelsen er sat i karantæne forkert, kan du frigive eller godkende anmodninger om frigivelse for brugere. <br/><br/> Hvis du vil styre, hvad brugerne kan gøre med deres egne karantænemeddelelser (herunder frigivelse eller anmodning om frigivelse), skal du se [Karantænepolitikker](quarantine-policies.md).|Team til sikkerhedshandlinger <br/><br/> Meddelelsesteam|

### <a name="review-phishing-and-malware-campaigns-that-resulted-in-delivered-mail"></a>Gennemse phishing- og malwarekampagner, der resulterede i leverede mails

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse mailkampagner.|Daglige|[Gennemse mailkampagner](campaigns.md) , der er målrettet din organisation på <https://security.microsoft.com/campaigns>. Fokuser på kampagner, der resulterede i, at meddelelser blev leveret til modtagere. <br/><br/> Fjern meddelelser fra kampagner, der findes i brugerpostkasser. Denne handling er kun påkrævet, når en kampagne indeholder mail, der ikke allerede er blevet afhjælpet af handlinger fra hændelser, [automatisk sletning på nul timer (ZAP)](zero-hour-auto-purge.md) eller manuel afhjælpning.|Team til sikkerhedshandlinger|

## <a name="weekly-activities"></a>Ugentlige aktiviteter

### <a name="review-email-detection-trends-in-defender-for-office-365-reports"></a>Gennemse tendenser for registrering af mail i Defender for Office 365 rapporter

I Defender for Office 365 kan du bruge følgende rapporter til at gennemse tendenser for registrering af mails i din organisation:

- [Statusrapporten Mailflow](view-mail-flow-reports.md#mailflow-status-report)
- [Statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse rapporter til registrering af mail på: <ul><li><https://security.microsoft.com/reports/TPSAggregateReportATP></li><li><https://security.microsoft.com/mailflowStatusReport?viewid=type></li></ul>|Ugentlige|Gennemse tendenser for registrering af mail for malware, phishing og spam sammenlignet med god mail. Observation over tid giver dig mulighed for at se trusselsmønstre og afgøre, om du har brug for at justere dine Defender for Office 365 politikker.|Sikkerhedsadministration <br/><br/> Team til sikkerhedshandlinger|

### <a name="track-and-respond-to-emerging-threats-using-threat-analytics"></a>Spor og reager på nye trusler ved hjælp af Threat-analyse

Brug [Threat Analytics](/microsoft-365/security/defender-endpoint/threat-analytics) til at gennemse aktive, mest populære trusler.

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse trusler i Threat Analytics på <https://security.microsoft.com/threatanalytics3>.|Ugentlige|Trusselsanalyse giver detaljeret analyse, herunder følgende elementer: <ul><li>IOCs.</li><li>Jagtforespørgsler om aktive trusselsaktører og deres kampagner.</li><li>Populære og nye angrebsteknikker.</li><li>Kritiske sikkerhedsrisici.</li><li>Almindelige angrebsoverflader.</li><li>Udbredt malware.</li></ul>|Team til sikkerhedshandlinger <br/><br/> Trusselsjagtteam|

### <a name="review-top-targeted-users-for-malware-and-phishing"></a>Gennemse de mest målrettede brugere for malware og phishing

Brug fanen **[Topmålbrugere](threat-explorer.md#top-targeted-users)** i Threat Explorer til at finde eller bekræfte de brugere, der er de vigtigste mål for malware og phishing-mail.

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse fanen **Topmålbrugere** i Threat Explorer på <https://security.microsoft.com/threatexplorer>.|Ugentlige|Brug oplysningerne til at beslutte, om du har brug for at justere politikker eller beskyttelse for disse brugere. Føj de berørte brugere til [prioritetskonti](/microsoft-365/admin/setup/priority-accounts) for at få følgende fordele: <ul><li>Yderligere synlighed, når hændelser påvirker dem.</li><li>Skræddersyet heuristik til mønstre for administration af mailflow (prioriteret kontobeskyttelse).</li><li>[Rapport over mailproblemer for prioritetskonti](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)</li></ul>|Sikkerhedsadministration <br/><br/> Team til sikkerhedshandlinger|

### <a name="review-top-malware-and-phishing-campaigns-that-target-your-organization"></a>Gennemse de mest populære malware- og phishing-kampagner, der er målrettet din organisation

Kampagnevisninger viser malware- og phishingangreb mod din organisation. Du kan få flere oplysninger [under Kampagnevisninger i Microsoft Defender for Office 365](campaigns.md).

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Brug **Kampagnevisninger** på <https://security.microsoft.com/campaigns> til at gennemse malware- og phishing-angreb, der påvirker dig.|Ugentlige|Få mere at vide om angreb og teknikker, og hvad Defender for Office 365 var i stand til at identificere og blokere. <br/><br/> Brug **Download trusselsrapport** i kampagnevisninger for at få detaljerede oplysninger om en kampagne.|Team til sikkerhedshandlinger|

## <a name="ad-hoc-activities"></a>Ad hoc-aktiviteter

### <a name="manual-investigation-and-removal-of-email"></a>Manuel undersøgelse og fjernelse af mail

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Undersøg og fjern dårlig mail i Threat Explorer på baseret på <https://security.microsoft.com/threatexplorer> brugeranmodninger.|Ad hoc|Brug handlingen **Trigger investigation** i Threat Explorer til at starte en automatiseret undersøgelses- og svarlegebog for alle mails fra de sidste 30 dage. Manuel udløsning af en undersøgelse sparer tid og kræfter ved centralt at inkludere: <ul><li>En rodundersøgelse.</li><li>Trin til at identificere og korrelere trusler.</li><li>Anbefalede handlinger til at afhjælpe disse trusler.</li></ul> <br/> Du kan få flere oplysninger under [Eksempel: En brugerrapporteret phishmeddelelse starter en undersøgelseslogbog](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) <br/><br/> Eller du kan bruge Threat Explorer til [manuelt at undersøge mail](investigate-malicious-email-that-was-delivered.md) med effektive søge- og filtreringsfunktioner og [udføre manuel svarhandling](remediate-malicious-email-delivered-office-365.md) direkte fra det samme sted. Tilgængelige manuelle handlinger: <ul><li>Flyt til Indbakke</li><li>Flyt til uønsket mail</li><li>Flyt til Slettede elementer</li><li>Blød sletning</li><li>Slet hårdt.</li></ul>|Team til sikkerhedshandlinger|

### <a name="proactively-hunt-for-threats"></a>Proaktiv jagt på trusler

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Regelmæssig, proaktiv jagt på trusler på: <ul><li><https://security.microsoft.com/threatexplorer></li><li><https://security.microsoft.com/v2/advanced-hunting></li></ul>.|Ad hoc|Søg efter trusler ved hjælp af [Threat Explorer](threat-explorer.md) og [avanceret jagt](../defender-endpoint/advanced-hunting-overview.md).|Team til sikkerhedshandlinger <br/><br/> Trusselsjagtteam|
|Del jagtforespørgsler.|Ad hoc|Del aktivt ofte anvendte, nyttige forespørgsler i sikkerhedsteamet for at få hurtigere manuel trusselsjagt og -afhjælpning. <br/><br/> Brug [Trusselssporing og](threat-trackers.md) [delte forespørgsler i Avanceret jagt](/microsoft-365/security/defender/advanced-hunting-shared-queries).|Team til sikkerhedshandlinger <br/><br/> Trusselsjagtteam|
|Opret brugerdefinerede regler for registrering på <https://security.microsoft.com/custom_detection>.|Ad hoc|[Opret brugerdefinerede regler for registrering](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting) for proaktivt at overvåge hændelser, mønstre og trusler baseret på Defender for Office 365 data i Advance Hunting. Registreringsregler indeholder avancerede jagtforespørgsler, der genererer beskeder baseret på de matchende kriterier.|Team til sikkerhedshandlinger <br/><br/> Trusselsjagtteam|

### <a name="review-defender-for-office-365-policy-configurations"></a>Gennemse Defender for Office 365 politikkonfigurationer

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse konfigurationen af Defender for Office 365 politikker på <https://security.microsoft.com/configurationAnalyzer>.|Ad hoc <br/><br/> Månedlige|Brug [Konfigurationsanalyse](configuration-analyzer-for-security-policies.md) til at sammenligne dine eksisterende politikindstillinger med de [anbefalede Standard- eller Strict-værdier for Defender for Office 365](recommended-settings-for-eop-and-office365.md). Konfigurationsanalysen identificerer utilsigtede eller skadelige ændringer, der kan reducere din organisations sikkerhedsholdning. <br/><br/> Eller du kan bruge det PowerShell-baserede [ORCA-værktøj](https://aka.ms/getorca).|Sikkerhedsadministration <br/><br/> Meddelelsesteam|
|Gennemse tilsidesættelser af registrering i Defender for Office 365 kl.<https://security.microsoft.com/reports/TPSMessageOverrideReportATP>|Ad hoc <br/><br/> Månedlige|Brug [Vis data efter system til at tilsidesætte \> diagramopdeling efter årsagsvisning](view-email-security-reports.md#view-data-by-system-override-and-chart-breakdown-by-reason) i **statusrapporten Trusselsbeskyttelse** til at gennemse mails, der blev registreret som phishing, men leveret på grund af indstillinger for tilsidesættelse af politik eller bruger. <br/><br/> Undersøg, fjern eller finjuster tilsidesættelser aktivt for at undgå levering af mails, der blev bestemt til at være skadelige.|Sikkerhedsadministration <br/><br/> Meddelelsesteam|

### <a name="review-spoof-and-impersonation-detections"></a>Gennemse registreringer af spoof og repræsentation

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse **Spoof Intelligence-indsigten** og **indsigten Repræsentationsregistrering** på <ul><li><<https://security.microsoft.com/spoofintelligence>></li><li><https://security.microsoft.com/impersonationinsight></li></ul>.|Ad hoc <br/><br/> Månedlige|Brug [indsigt i spoof intelligence](learn-about-spoof-intelligence.md) og [repræsentationsindsigt](impersonation-insight.md) til at justere filtrering for spoof- og repræsentationsregistreringer.|Sikkerhedsadministration <br/><br/> Meddelelsesteam|

### <a name="review-priority-account-membership"></a>Gennemse medlemskab af prioritetskonto

|Aktivitet|Kadence|Beskrivelse|Persona|
|---|---|---|---|
|Gennemse, hvem der er defineret som en prioritetskonto på <https://security.microsoft.com/securitysettings/userTags>.|Ad hoc|Hold medlemskabet af [prioriterede konti](/microsoft-365/admin/setup/priority-accounts) opdateret med organisatoriske ændringer for at få følgende fordele for disse brugere: <ul><li>Bedre synlighed i rapporter.</li><li>Filtrering i hændelser og beskeder.</li><li>Skræddersyet heuristik til mønstre for administration af mailflow (prioriteret kontobeskyttelse).</li></ul> <br/> Brug brugerdefinerede [brugerkoder](user-tags.md) til andre brugere for at få: <ul><li>Bedre synlighed i rapporter.</li><li>Filtrering i hændelser og beskeder.</li></ul>|Team til sikkerhedshandlinger|

## <a name="appendix"></a>Tillæg

### <a name="learn-about-microsoft-defender-for-office-365-tools-and-processes"></a>Få mere at vide om Microsoft Defender for Office 365 værktøjer og processer

Medlemmer af sikkerhedshandlinger og svarteam skal integrere Defender for Office 365 værktøjer og funktioner i eksisterende undersøgelser og svarprocesser. Det kan tage tid at lære om nye værktøjer og funktioner, men det er en vigtig del af ombordstigningsprocessen. Den nemmeste måde for medlemmer af SecOps og mailsikkerhedsteamet at lære om Defender for Office 365 på er at bruge det træningsindhold, der er tilgængeligt som en del af Ninja-træningsindholdet på <https://aka.ms/mdoninja>.

Indholdet er struktureret til forskellige videnniveauer (Grundlæggende, Mellemliggende og Avanceret) med flere moduler pr. niveau.

Korte videoer til bestemte opgaver er også tilgængelige i [Microsoft Defender for Office 365 YouTube-kanalen](https://www.youtube.com/playlist?list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf).

### <a name="permissions-for-defender-for-office-365-activities-and-tasks"></a>Tilladelser til Defender for Office 365 aktiviteter og opgaver

Tilladelser til administration af Defender for Office 365 i Microsoft 365 Defender-portalen og PowerShell er baseret på RBAC-tilladelsesmodellen (Role Based Access Control). RBAC er den samme tilladelsesmodel, der bruges af de fleste Microsoft 365-tjenester. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

> [!NOTE]
> Privileged Identity Management (PIM) i Azure AD er også en måde at tildele påkrævede tilladelser til SecOps-personale. Du kan få flere oplysninger under [Privileged Identity Management (PIM), og hvorfor du skal bruge den sammen med Microsoft Defender for Office 365](use-privileged-identity-management-in-defender-for-office-365.md).

Følgende tilladelser (roller og rollegrupper) er tilgængelige i Defender for Office 365 og kan bruges til at give adgang til medlemmer af sikkerhedsteamet:

- **Azure AD roller**: Centraliserede roller, der tildeler tilladelser til _alle_ Microsoft 365-tjenester, herunder Defender for Office 365. Du kan få vist de Azure AD roller og tildelte brugere på Microsoft 365 Defender-portalen, men du kan ikke administrere dem direkte der. Du kan i stedet administrere Azure AD roller og medlemmer på <https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RolesAndAdministrators>. De hyppigste roller, der bruges af sikkerhedsteams, er:
  - **Sikkerhedsadministrator**
  - **Sikkerhedsoperator**
  - **Sikkerhedslæser**

- **Mail & samarbejdsroller**: Roller og rollegrupper, der giver tilladelse, der er specifikke for Microsoft Defender for Office 365. Følgende roller er ikke tilgængelige i Azure AD, men kan være vigtige for sikkerhedsteams:

  - **Eksempelrolle** : Tildel denne rolle til teammedlemmer, der skal have vist eller downloade mails som en del af undersøgelsesaktiviteterne. Giver brugerne mulighed for at [få vist og downloade](investigate-malicious-email-that-was-delivered.md#preview-role-permissions) mails i cloudpostkasser ved hjælp af [mailobjektsiden](mdo-email-entity-page.md#email-preview-for-cloud-mailboxes).

    Denne rolle tildeles som standard kun til følgende rollegrupper:

    - Datadetektiv
    - eDiscovery Manager

    Hvis du vil tildele denne rolle til en ny eller eksisterende rollegruppe, skal du se [Rediger mail & medlemskab af samarbejdsrolle på portalen Microsoft 365 Defender](permissions-microsoft-365-security-center.md#modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal).

  - **Søg og fjern** rolle: Godkend sletning af skadelige meddelelser som anbefalet af AIR, eller udfør en manuel handling på meddelelser i jagtoplevelser som Threat Explorer.

    Denne rolle tildeles som standard kun til følgende rollegrupper:

    - Datadetektiv
    - Organisationsadministration

    Hvis du vil tildele denne rolle til en ny eller eksisterende rollegruppe, skal du se [Rediger mail & medlemskab af samarbejdsrolle på portalen Microsoft 365 Defender](permissions-microsoft-365-security-center.md#modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal).

  - **Lejer allowBlockList Manager**: Administrer tilladte og blokerede poster på [lejerlisten Tillad/Bloker](tenant-allow-block-list.md). Blokering af URL-adresser, filer (ved hjælp af filhash) eller afsendere er en nyttig svarhandling, der skal udføres, når du undersøger skadelige mails, der blev leveret.

    Denne rolle tildeles som standard kun til rollegruppen **Sikkerhedsoperator** . Men medlemmer af **rollegrupperne Sikkerhedsadministratorer** og **Organisationsadministration** kan også administrere poster på listen over tilladte/blokerede lejere.

### <a name="siemsoar-integration"></a>SIEM-/SOAR-integration

Defender for Office 365 fremviser de fleste af dataene via et sæt programmatiske API'er. Disse API'er hjælper dig med at automatisere arbejdsprocesser og gøre fuld brug af Defender for Office 365 funktioner. Data er tilgængelige via [Microsoft 365 Defender API'er](/microsoft-365/security/defender/api-overview) og kan bruges til at integrere Defender for Office 365 i eksisterende SIEM/SOAR-løsninger.

- [Hændelses-API](/microsoft-365/security/defender/api-incident): Defender for Office 365 beskeder og automatiserede undersøgelser er aktive dele af hændelser i Microsoft 365 Defender. Sikkerhedsteams kan fokusere på det, der er vigtigt, ved at gruppere det fulde angrebsomfang og alle berørte aktiver samlet.

- [API til hændelsesstreaming](/microsoft-365/security/defender/streaming-api): Gør det muligt at sende hændelser og beskeder i realtid til en enkelt datastream, efterhånden som de sker. Understøttede Defender for Office 365 hændelsestyper omfatter:
  - [EmailEvents](/microsoft-365/security/defender/advanced-hunting-emailevents-table)
  - [EmailUrlInfo](/microsoft-365/security/defender/advanced-hunting-emailurlinfo-table)
  - [EmailAttachmentInfo](/microsoft-365/security/defender/advanced-hunting-emailattachmentinfo-table)
  - [EmailPostDeliveryEvents](/microsoft-365/security/defender/advanced-hunting-emailpostdeliveryevents-table)

  Hændelserne indeholder data fra behandling af alle mails (herunder meddelelser inden for organisationen) inden for de sidste 30 dage.

- [Advance Hunting API](/microsoft-365/security/defender/api-advanced-hunting): Tillader trusselsjagt på tværs af produkter.

- [Threat Assessment API](/graph/api/resources/threatassessment-api-overview): Kan bruges til at rapportere spam, phishing-URL-adresser eller vedhæftede filer til malware direkte til Microsoft.

Hvis du vil oprette forbindelse Defender for Office 365 hændelser og rådata med Microsoft Sentinel, kan du bruge [connectoren Microsoft 365 Defender (M365D)](/azure/sentinel/connect-microsoft-365-defender?tabs=MDO)

Du kan bruge dette enkle "Hello World"-eksempel til at teste API-adgang til Microsoft Defender-API'er: [Hello World for Microsoft 365 Defender REST API](/microsoft-365/security/defender/api-hello-world).

Du kan finde flere oplysninger om integration af SIEM-værktøjer under [Integrer dine SIEM-værktøjer med Microsoft 365 Defender](/microsoft-365/security/defender/configure-siem-defender).

## <a name="address-false-positives-and-false-negatives-in-defender-for-office-365"></a>Adresser falske positiver og falske negativer i Defender for Office 365

Brugerindsendelse og administratorindsendelser af mails er vigtige positive signalforstærkningssignaler til vores systemer til registrering af maskinel indlæring. Indsendelser hjælper os med at gennemse, triage, lære hurtigt og afhjælpe angreb. Aktiv rapportering af falske positiver og falske negativer er en vigtig aktivitet, der giver feedback til Defender for Office 365, når der opstår fejl under registreringen.

Organisationer har flere muligheder for at konfigurere brugerindsendelser. Afhængigt af konfigurationen kan sikkerhedsteams have mere aktiv involvering, når brugerne sender falske positiver eller falske negativer til Microsoft:

- Brugerindsendelser sendes til Microsoft til analyse, når [den bruger rapporterede meddelelsesindstillinger](user-submission.md) er konfigureret med en af følgende indstillinger:
  - Send de rapporterede meddelelser til: Microsoft.
  - Send de rapporterede meddelelser til: Microsoft og min organisations postkasse.

  Medlemmer af sikkerhedsteams skal indsende [tilføjelsesadministratorer](admin-submission.md) , når falske positiver eller falske negativer, der ikke blev rapporteret af brugerne, blev registreret af handlingsteamene.

- Når brugerrapporterede meddelelser er konfigureret til kun at sende meddelelser til organisationens postkasse, skal sikkerhedsteams aktivt sende brugerrapporterede falske positiver og falske negativer til Microsoft via administratorindsendelser.

Når en bruger rapporterer en meddelelse som phishing, genererer Defender for Office 365 en besked, og beskeden udløser en AIR-playbook. Hændelseslogik korrelerer disse oplysninger med andre beskeder og hændelser, hvor det er muligt. Denne konsolidering af oplysninger hjælper sikkerhedsteams med at granske, undersøge og besvare brugerrapporterede mails.

Brugerindsendelser og administratorindsendelser håndteres af indsendelsespipelinen af Microsoft, som følger en tæt integreret proces. Denne proces omfatter:

- Støjreduktion.
- Automatiseret triage.
- Klassificering af sikkerhedsanalytikere og løsninger baseret på maskinel indlæring baseret på menneskeskabte partnere.

Du kan få flere oplysninger under [Rapportering af en mail i Defender for Office 365 – Microsoft Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/reporting-an-email-in-microsoft-defender-for-office-365/ba-p/2870231).

Medlemmer af sikkerhedsteamet kan foretage indsendelser fra flere placeringer på Microsoft 365 Defender-portalen på <https://security.microsoft.com>:

- [Administration indsendelse](admin-submission.md): Brug portalen Indsendelser til at sende mistanke om spam, phishing, URL-adresser og filer til Microsoft.
- Direkte fra Threat Explorer ved hjælp af en af følgende meddelelseshandlinger:
  - Rapport ren
  - Rapport phishing
  - Rapportér malware
  - Rapportér spam

  Du kan vælge op til 10 meddelelser for at udføre en masseindsendelse. Administration indsendelser, der er oprettet på denne måde, er også synlige på indsendelsesportalen.

Hvis du vil afhjælpe falske negative på kort sigt, kan sikkerhedsteams administrere [blokeringsposter](manage-tenant-blocks.md) direkte for filer, URL-adresser og afsendere på [listen over tilladte/blokerede lejere](tenant-allow-block-list.md).

For den kortfristede afhjælpning af falske positiver kan sikkerhedsteams ikke direkte administrere [tilladte poster](manage-tenant-allows.md) på listen over tilladte lejere/blokeringer. De skal i stedet bruge [administratorindsendelser](admin-submission.md) og indstillingen **Tillad meddelelser som denne** .

[Karantæne](manage-quarantined-messages-and-files.md) i Defender for Office 365 indeholder potentielt farlige eller uønskede meddelelser og filer. Sikkerhedsteams kan få vist, frigive og slette alle typer af karantænemeddelelser for alle brugere. Denne funktion gør det muligt for sikkerhedsteams at reagere effektivt, når en falsk positiv meddelelse eller fil er sat i karantæne.

## <a name="integrate-third-party-reporting-tools-with-defender-for-office-365-user-submission"></a>Integrer rapporteringsværktøjer fra tredjepart med Defender for Office 365 indsendelse af bruger

Hvis din organisation bruger et rapporteringsværktøj fra tredjepart, der giver brugerne mulighed for internt at rapportere mistænkelige mails, kan du integrere værktøjet med funktionerne til brugerindsendelse i Defender for Office 365. Denne integration giver følgende fordele for sikkerhedsteams:

- Integration med AIR-funktionerne i Defender for Office 365.
- Forenklet triage.
- Reduceret undersøgelses- og svartid.

Angiv den brugerdefinerede postkasse, hvor brugerrapporterede meddelelser sendes på siden **Brugerindsendelser** på portalen Microsoft 365 Defender på <https://security.microsoft.com/userSubmissionsReportMessage>. Du kan få flere oplysninger under [Indstillinger for brugerrapporterede meddelelser](user-submission.md).

> [!NOTE]
>
> - Den brugerdefinerede postkasse er en Exchange Online postkasse.
> - Rapporteringsværktøjet fra tredjepart skal indeholde den oprindeligt rapporterede meddelelse som en dekomprimeret . EML eller . Den vedhæftede MSG-fil i den meddelelse, der sendes til den brugerdefinerede postkasse (videresend ikke kun den oprindelige meddelelse til den brugerdefinerede postkasse).
> - Den brugerdefinerede postkasse kræver specifikke forudsætninger for at tillade levering af potentielt forkerte meddelelser. Du kan få flere oplysninger under [Forudsætninger for brugerdefineret postkasse](user-submission.md#custom-mailbox-prerequisites).

Når der modtages brugerrapporterede mails i den brugerdefinerede postkasse, genererer Defender for Office 365 automatisk beskeden med navnet **Mail rapporteret af brugeren som malware eller phish**. Denne besked starter en [air playbook](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook). Playbooken udfører en række automatiserede undersøgelsestrin:

- Indsaml data om den angivne mail.
- Indsaml data om de trusler og enheder, der er relateret til den pågældende mail. Objekter kan omfatte filer, URL-adresser og modtagere.
- Angiv anbefalede handlinger, som SecOps-teamet skal udføre på baggrund af undersøgelsesresultaterne.

**Mail, der er rapporteret af brugeren som malware- eller phishbeskeder**, automatiserede undersøgelser og deres anbefalede handlinger, korreleres automatisk til hændelser i Microsoft 365 Defender. Denne korrelation forenkler yderligere triage- og svarprocessen for sikkerhedsteams. Hvis flere brugere rapporterer de samme eller lignende meddelelser, korreleres alle brugere og meddelelser til den samme hændelse.

Data fra beskeder og undersøgelser i Defender for Office 365 sammenlignes automatisk med beskeder og undersøgelser i andre Microsoft 365 Defender produkter:

- Microsoft Defender for Endpoint
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

Hvis der opdages en relation, opretter systemet en hændelse, der giver synlighed for hele angrebet.
