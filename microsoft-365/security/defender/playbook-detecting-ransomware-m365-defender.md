---
title: Registrering af menneskestyrede ransomware-angreb med Microsoft 365 Defender
description: I denne artikel beskrives proaktiv opdagelse af nye eller igangværende menneskedrevne ransomware-angreb med Microsoft 365 Defender portalen
search.appverid: MET150
author: nic-name
ms.author: noriordan
manager: dolmont
audience: ITPro
ms.topic: article
ms.date: 05/30/2022
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection: M365-security-compliance.
f1.keywords: NOCSH
ms.openlocfilehash: 3a3a1d48ab9876215e2034279d036705bf4e1972
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "66858607"
---
# <a name="detecting-human-operated-ransomware-attacks-with-microsoft-365-defender"></a>Registrering af menneskestyrede ransomware-angreb med Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Ransomware er en type extortion-angreb, der ødelægger eller krypterer filer og mapper, hvilket forhindrer adgang til kritiske data eller forstyrrer kritiske forretningssystemer. Der er to typer ransomware:

* Vare ransomware er malware, der spredes med phishing eller mellem enheder og krypterer filer, før de kræver en løsesum.
* Menneskelig drevet ransomware er et planlagt og koordineret angreb fra aktive cyberkriminelle, der anvender flere angrebsmetoder. I mange tilfælde bruges kendte teknikker og værktøjer til at infiltrere din organisation, finde de aktiver eller systemer, der er værd at afpresse, og derefter kræve en løsesum. Ved at kompromittere et netværk udfører angriberen rekognoscering af aktiver og systemer, som kan krypteres eller afpresses. Angriberne krypterer eller exfiltrerer derefter data, før de kræver en løsesum.

I denne artikel beskrives proaktiv opdagelse af nye eller igangværende menneskedrevne ransomware-angreb med Microsoft 365 Defender portalen, en XDR-løsning (extended detection and response) til følgende sikkerhedstjenester:

* Microsoft Defender for Endpoint
* Microsoft Defender for Office 365
* Microsoft Defender for Identity
* Microsoft Defender for Cloud Apps (herunder tilføjelsesprogrammet til appstyring)
* beskyttelse af identiteter Microsoft Azure AD
* Microsoft Defender til IoT
* Microsoft 365 Business Premium
* Microsoft Defender for Business

Du kan få oplysninger om forebyggelse af ransomware-angreb under [Beskyt hurtigt mod ransomware og afpresning](/security/compass/protect-against-ransomware-phase3).

## <a name="the-importance-of-proactive-detection"></a>Vigtigheden af proaktiv registrering

Fordi menneskelig drevet ransomware typisk udføres af aktive hackere, der muligvis udfører trinnene for at infiltrere og opdage dine mest værdifulde data og systemer i realtid, er den tid, det tager at opdage ransomware-angreb, afgørende.

Hvis aktiviteter før løsepenge opdages hurtigt, falder sandsynligheden for et alvorligt angreb. Fasen før løsepenge indeholder typisk følgende teknikker: indledende adgang, rekognoscering, tyveri af legitimationsoplysninger, tværgående bevægelse og vedholdenhed. Disse teknikker kan i første omgang synes ikke-relaterede og ofte flyve under radaren. Hvis disse teknikker fører til løsepenge fase, er det ofte for sent. Microsoft 365 Defender kan hjælpe med at identificere de små og tilsyneladende ikke-relaterede hændelser som muligvis en del af en større ransomware-kampagne.

* Når det registreres i fasen før løsepenge, kan mindre afhjælpninger, f.eks. isolering af inficerede enheder eller brugerkonti, bruges til at afbryde og afhjælpe angrebet.
* Hvis registrering kommer på et senere tidspunkt, f.eks. når den malware, der bruges til at kryptere filer, udrulles, skal der muligvis bruges mere aggressive afhjælpningstrin, der kan forårsage nedetid, til at afbryde og afhjælpe angrebet.

Driftsforstyrrelser er sandsynligvis, når de reagerer på et ransomware-angreb. Slutfasen af et ransomware-angreb er ofte et valg mellem nedetid forårsaget af hackere med store risici eller en kontrolleret nedetid for at sikre netværkssikkerhed og give dig tid til fuldt ud at undersøge. Vi anbefaler aldrig at betale en løsesum. Betalende cyberkriminelle for at få en ransomware-dekrypteringsnøgle giver ingen garanti for, at dine krypterede data gendannes. Se, [Ransomware-svar – Microsoft Security Blog](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/).

Her er den kvalitative relation af virkningen af et ransomware-angreb og din tid til at reagere på ingen opdagelse vs. proaktiv opdagelse og svar.

![Den kvalitative relation af virkningen af et ransomware-angreb og din tid til at reagere på ingen registrering vs. proaktiv opdagelse og reaktion, der viser effekten på din virksomhed reducerer, jo hurtigere du reagerer.](../../media/defender/playbook-detecting-ransomware-m365-defender-qualitative-diagram.png)

### <a name="proactive-detection-via-common-malware-tools-and-techniques"></a>Proaktiv registrering via almindelige malwareværktøjer og -teknikker

I mange tilfælde bruger menneskedrevne ransomware-hackere velkendte og felttestede malwaretaktik, teknikker, værktøjer og procedurer, herunder phishing, BEC (Business Email Compromise) og tyveri af legitimationsoplysninger. Dine sikkerhedsanalytikere skal være opmærksomme på og have kendskab til, hvordan hackere bruger almindelige malware- og cyberangrebsmetoder til at få fodfæste i din organisation.

Hvis du vil se eksempler på, hvordan ransomware-angreb kommer i gang med almindelig malware, skal du se disse ressourcer:

* [Menneskedrevne ransomware-angreb: En katastrofe, der kan forebygges](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)
* [Ransomware-trusselsanalyserapporter på Microsoft 365 Defender-portalen](https://sip.security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,exposureLevel,MisconfiguredDevices,VulnerableDevices,reportType,createdOn,lastUpdatedOn,tags,flag)

At være fortrolig med malware, nyttedata og aktiviteter før løsepenge hjælper dine analytikere med at vide, hvad de skal kigge efter for at forhindre de senere faser af et angreb.

## <a name="human-operated-ransomware-attack-tactics"></a>Menneskeligt opereret ransomware angreb taktik

Fordi menneskeligt drevet ransomware kan bruge kendte angrebsteknikker og -værktøjer, vil dine analytikeres forståelse og erfaring med eksisterende angrebsteknikker og -værktøjer være et værdifuldt aktiv, når du forbereder dit SecOps-team til fokuserede praksisser for ransomware-opdagelse.

### <a name="attack-tactics-and-methods"></a>Angreb taktik og metoder

Her er nogle typiske teknikker og værktøjer, der bruges af ransomware hackere til følgende [MITRE ATT&CK](https://attack.mitre.org/tactics/enterprise/) taktik:

Indledende adgang:

* RDP brute force
* Sårbart internetbaseret system
* Svage programindstillinger
* Phishing-mail

Tyveri af legitimationsoplysninger:

* Mimikatz
* LSA-hemmeligheder
* Samling af legitimationsoplysninger
* Legitimationsoplysninger i almindelig tekst
* Misbrug af tjenestekonti

Tværgående bevægelse:

* Coboltstreg
* WMI
* Misbrug af ledelsesværktøjer
* PsExec

Persistens:

* Nye konti
* Ændringer i gruppepolitikobjekt
* Skygge-it-værktøjer
* Planlæg opgaver
* Tjenesteregistrering

Forsvarsunddragelse:

* Deaktivering af sikkerhedsfunktioner
* Rydder logfiler
* Sletning af angrebsartefaktfiler
* Nulstilling af tidsstempler på ændrede filer

Eksfiltration:

* Eksfiltration af følsomme data Impact (økonomisk udnyttelse):
* Kryptering af data på plads og i sikkerhedskopier
* Sletning af data på plads og sikkerhedskopier, som kan kombineres med en tidligere eksfiltration
* Trussel om offentlig lækage af exfiltrerede, følsomme data

### <a name="what-to-look-for"></a>Hvad skal du søge efter?

Udfordringen for sikkerhedsanalytikere er at genkende, når en besked er en del af en større angrebskæde med det formål at afpresse dine følsomme data eller vigtige systemer. Et registreret phishingangreb kan f.eks. være:

* Et engangsangreb for at overvåge mails fra en person i økonomiafdelingen i en organisation.
* Pre-ransom del af et angreb kæde til at bruge kompromitteret brugerkonto legitimationsoplysninger til at finde de ressourcer, der er tilgængelige for brugerkontoen og til at kompromittere andre brugerkonti med højere niveauer af rettigheder og adgang.

Dette afsnit indeholder almindelige angrebsfaser og -metoder og de signalkilder, der overføres til den centrale Microsoft 365 Defender portal, som opretter beskeder og hændelser, der består af flere relaterede beskeder til sikkerhedsanalyse. I nogle tilfælde er der alternative sikkerhedsportaler til at få vist angrebsdataene.

#### <a name="initial-attacks-to-gain-entry"></a>Indledende angreb for at få adgang

Hackeren forsøger at kompromittere en brugerkonto, enhed eller app.

Angrebsmetode |Signalkilde |Alternative sikkerhedsportaler
|:---|:---|:---
RDP brute force|Defender for Endpoint|Defender for Cloud Apps
Sårbart internetbaseret system|Windows-sikkerhedsfunktioner, Microsoft Defender for Servers|
Svage programindstillinger      |Defender for Cloud Apps, Defender for Cloud Apps med tilføjelsesprogrammet appstyring|Defender for Cloud Apps |
Aktivitet i skadelig app      |Defender for Cloud Apps, Defender for Cloud Apps med tilføjelsesprogrammet appstyring|Defender for Cloud Apps |
Phishing-mail        |Defender for Office 365
Adgangskodespray mod Azure AD konti |Azure AD identitetsbeskyttelse via Defender for Cloud Apps      |Defender for Cloud Apps
Adgangskodespray mod konti i det lokale miljø |Microsoft Defender for Identity
Kompromitteret enhed       |Defender for Endpoint
Tyveri af legitimationsoplysninger       |Microsoft Defender for Identity
Eskalering af rettigheder      |Microsoft Defender for Identity

#### <a name="recent-spike-in-otherwise-typical-behavior"></a>Nylig stigning i ellers typisk adfærd

Hackeren forsøger at undersøge, om yderligere enheder kan kompromitteres.

Kategorien Spidsbelastning        |Signalkilde                 |Alternative sikkerhedsportaler
|:---                    |:---                              |:---
Logon: Flere mislykkede forsøg, forsøg på at logge på flere enheder på kort tid, flere logon første gang osv. |Azure AD identitetsbeskyttelse via Defender for Cloud Apps Microsoft Defender for Identity |Defender for Cloud Apps
Seneste aktive brugerkonto, gruppe, computerkonto, app |Azure AD identitetsbeskyttelse via Defender for Cloud Apps (Azure AD), Defender for Identity (Active Directory-domæneservices [AD DS]) |Defender for Cloud Apps
Seneste appaktivitet, f.eks. dataadgang |Apps med Defender for Cloud Apps med tilføjelsesprogrammet appstyring |Defender for Cloud Apps

#### <a name="new-activity"></a>Ny aktivitet

Hackeren opretter nye enheder for at fremme deres rækkevidde, installere malwareagenter eller undgå registrering.

Aktivitet     |Signalkilde           |Alternativ sikkerhedsportal
|:---                |:---                        |:---
Nye apps, der er installeret |Defender for Cloud Apps med tilføjelsesprogrammet appstyring |Defender for Cloud Apps
Nye brugerkonti    |Azure Identity Protection         |Defender for Cloud Apps
Rolleændringer      |Azure Identity Protection        |Defender for Cloud Apps

#### <a name="suspicious-behavior"></a>Mistænkelig funktionsmåde

Hackeren downloader følsomme oplysninger, krypterer filer eller på anden måde indsamler eller beskadiger organisationens aktiver.

Funktionsmåde       |Signalkilde
|:---                  |:---
Malware spredes til flere enheder |Defender for Endpoint
Ressourcescanning     |Defender for Endpoint, Defender for Identity
Ændringer i reglerne for videresendelse af postkasse |Defender for Office 365
Dataudfiltrering og kryptering |Defender for Office 365

**Overvåg for annoncedeaktivering af sikkerhed** – da dette ofte er en del af den menneskelige drevne ransomware -angrebskæde (HumOR)

* **Rydning af hændelseslogge** – især logfiler for sikkerhedshændelser og PowerShell-handlingslogge
* **Deaktivering af sikkerhedsværktøjer/kontrolelementer** (knyttet til nogle grupper)

## <a name="detect-ransomware-attacks-with-the-microsoft-365-defender-portal"></a>Registrer ransomware-angreb med Microsoft 365 Defender-portalen

Portalen Microsoft 365 Defender indeholder en central visning af oplysninger om registreringer, påvirkede aktiver, automatiserede handlinger og relaterede beviser en kombination af:

* En hændelseskø, som grupperer relaterede beskeder for et angreb for at give det fulde angrebsomfang, påvirkede aktiver og automatiserede afhjælpningshandlinger.
* En beskedkø, som viser alle de beskeder, der spores af Microsoft 365 Defender.

### <a name="incident-and-alert-sources"></a>Kilder til hændelser og beskeder

Microsoft 365 Defender portal centraliserer signaler fra:

* Microsoft Defender for Endpoint
* Microsoft Defender for Office 365
* Microsoft Defender for Identity
* Microsoft Defender for Cloud Apps (herunder tilføjelsesprogrammet til appstyring)
* Microsoft Azure AD Identity Protection
* Microsoft Defender til IoT

I denne tabel vises nogle typiske angreb og deres tilsvarende signalkilde for Microsoft 365 Defender.

Angreb og hændelser           |Signalkilde
|:---                         |:---
Cloud-identitet: Adgangskodespray, adskillige mislykkede forsøg, forsøg på at logge på flere enheder på kort tid, flere førstegangslogon, seneste aktive brugerkonti |Azure AD Identity Protection
AD DS (On-Premises Identity) kompromitterer       |Defender for Identity
Phishing              |Defender for Office 365
Skadelige apps             |Defender for Cloud Apps eller Defender for Cloud Apps med tilføjelsesprogrammet appstyring
Kompromitteret slutpunkt (enhed)         |Defender for Endpoint
IoT-kompatibel enhed kompromitterer          |Defender for IoT

### <a name="filtering-ransomware-identified-incidents"></a>Filtrering af ransomware-identificerede hændelser

Du kan nemt filtrere hændelseskøen for hændelser, der er kategoriseret af Microsoft 365 Defender som ransomware.

1. I navigationsruden Microsoft 365 Defender portalen skal du gå til hændelseskøen ved at vælge **Hændelser og beskeder > Hændelser**.
2. Vælg **Filtre**.
3. Under **Kategorier** skal du vælge **Ransomware**, vælge **Anvend** og derefter lukke ruden **Filtre** .

Hver filterindstilling for hændelseskøen opretter en URL-adresse, som du kan gemme og få adgang til senere som et link. Disse URL-adresser kan bogmærkes eller på anden måde gemmes og bruges, når det er nødvendigt med et enkelt klik. Du kan f.eks. oprette bogmærker for:

* Hændelser, der indeholder kategorien "ransomware". Her er det tilsvarende [link](https://security.microsoft.com/incidents?filters=AlertStatus%3DNew%257CInProgress,category%3Dransomware&page_size=30&fields=expand,name,tags,severity,investigationStates,category,impactedEntities,alertCount,serviceSource,detectionSource,firstEventTime,lastEventTime,sensitivity,status,incidentAssignment,classification,determination,rbacGroup).
* Hændelser med et angivet **agentnavn** , der er kendt for at udføre ransomware-angreb.
* Hændelser med et angivet **Associated threat-navn** , der er kendt for at blive brugt i ransomware-angreb.
* Hændelser, der indeholder et brugerdefineret tag, som dit SecOps-team bruger til hændelser, der er kendt for at være en del af et større, koordineret ransomware-angreb.

### <a name="filtering-ransomware-identified-threat-analytics-reports"></a>Filtrering af ransomware-identificerede trusselsanalyserapporter

På samme måde som med filtrering af hændelser i hændelseskøen kan du filtrere trusselsanalyserapporter for rapporter, der omfatter ransomware.

1. Vælg **Trusselsanalyse** i navigationsruden.
2. Vælg **Filtre**.
3. Under **Trusselstags** skal du vælge **Ransomware**, vælge **Anvend** og derefter lukke ruden **Filtre** .

Du kan også klikke på dette link.

I afsnittet **Oplysninger om registrering** i mange rapporter om trusselsanalyse kan du se en liste over beskednavne, der er oprettet for truslen.

### <a name="microsoft-365-defender-apis"></a>Microsoft 365 Defender API'er

Du kan også bruge Microsoft 365 Defender API'er til at forespørge om Microsoft 365 Defender hændelser og beskeder i din lejer. En brugerdefineret app kan filtrere dataene, filtrere dem baseret på brugerdefinerede indstillinger og derefter angive en filtreret liste over links til beskeder og hændelser, som du nemt kan vælge for at gå direkte til den pågældende besked eller hændelse. Se [Liste over HÆNDELSES-API'er i Microsoft 365 Defender | Microsoft Docs](/api-list-incidents.md). Du kan også integrere din SIEM med Microsoft Defender under [Integrer dine SIEM-værktøjer med Microsoft 365 Defender](/configure-siem-defender.md).

### <a name="microsoft-365-defender-sentinel-integration"></a>Microsoft 365 Defender Sentinel-integration

Microsoft Sentinels Microsoft 365 Defender hændelsesintegration giver dig mulighed for at streame alle Microsoft 365 Defender hændelser til Microsoft Sentinel og holde dem synkroniseret mellem begge portaler. Hændelser omfatter alle tilknyttede beskeder, enheder og relevante oplysninger. Når du er i Sentinel, forbliver hændelser synkroniseret tovejs med Microsoft 365 Defender, så du kan drage fordel af fordelene ved begge portaler i din hændelsesundersøgelse. Se[, Microsoft 365 Defender integration med Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

### <a name="proactive-scanning-with-advanced-hunting"></a>Proaktiv scanning med avanceret jagt

[Avanceret jagt](/advanced-hunting-overview.md) er et forespørgselsbaseret trusselsjagtværktøj, der giver dig mulighed for at udforske og inspicere hændelser i dit netværk for at finde trusselsindikatorer og enheder. Dette fleksible analyseværktøj, der kan tilpasses, gør det muligt at jagte både kendte og potentielle trusler uden begrænsninger. Microsoft 365 Defender understøtter også brug af en brugerdefineret forespørgsel til at oprette [regler for brugerdefineret registrering](/custom-detections-overview.md), som opretter beskeder, der er baseret på en forespørgsel, og som kan planlægges til at køre automatisk.

For proaktiv scanning af ransomware-aktiviteter, bør du samle et katalog over avancerede jagtforespørgsler for almindeligt anvendte ransomware-angrebsmetoder til identiteter, slutpunkter, apps og data. Her er nogle vigtige kilder til brugsklare avancerede jagtforespørgsler:

* Artiklen [Hunt for ransomware](/advanced-hunting-find-ransomware.md)
* GitHub-lager til avancerede jagtforespørgsler:
  * [Ransomware-specifikke](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/tree/master/Ransomware) forespørgsler
  * [Alle kategorier](https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/tree/master/Ransomware) af forespørgsler
* Rapporter over trusselsanalyse
  * Avanceret jagtsektion af [Ransomware: En gennemtrængende og løbende trusselsanalytikerrapport](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/analystreport)
  * Afsnittet Avanceret jagt i andre analytikerrapporter

### <a name="automated-hunting"></a>Automatiseret jagt

Avancerede jagtforespørgsler kan også bruges til at oprette brugerdefinerede regler og handlinger for registrering baseret på kendte elementer af en ransomware-angrebsmetode (for eksempel brugen af usædvanlige PowerShell-kommandoer). Brugerdefinerede registreringsregler opretter beskeder, der kan ses og håndteres af dine sikkerhedsanalytikere.

Hvis du vil oprette en regel for brugerdefineret registrering, skal du vælge Opret regel for **brugerdefineret registrering** på siden i en avanceret jagtforespørgsel. Når du har oprettet, kan du angive:

* Hvor ofte reglen for brugerdefineret registrering skal køres
* Alvorsgraden af den besked, der er oprettet af reglen
* MITRE-angrebsfasen for den oprettede besked
* Påvirkede enheder
* Handlinger, der skal udføres på påvirkede enheder

## <a name="prepare-your-secops-team-for-focused-ransomware-detection"></a>Forbered dit SecOps-team til fokuseret ransomware-registrering

Forberedelse af dit SecOps-team til proaktiv ransomware-registrering kræver:

* Førarbejde for dit SecOps-team og din organisation
* Oplæring af sikkerhedsanalytiker efter behov
* Løbende operationelt arbejde med at inkorporere de nyeste angreb og registreringsoplevelser fra dine sikkerhedsanalytikere

### <a name="pre-work-for-your-secops-team-and-organization"></a>Førarbejde for dit SecOps-team og din organisation

Overvej disse trin for at gøre dit SecOps-team og din organisation klar til fokuseret forebyggelse af ransomware-angreb:

1. Konfigurer din it- og cloudinfrastruktur til ransomware-forebyggelse med vejledning til [hurtig beskyttelse mod ransomware og afpresning](/security/compass/protect-against-ransomware-phase3) . Faserne og opgaverne i denne vejledning kan udføres parallelt med følgende trin.
2. Hent de relevante licenser til Defender for Endpoint, Defender for Office 365, Defender for Identity, Defender for Cloud Apps, tilføjelsesprogrammet til appstyring, Defender for IoT og tjenester til identitetsbeskyttelse Azure AD.
3. Saml et katalog over avancerede jagtforespørgsler, der er tilpasset kendte ransomware-angrebsmetoder eller angrebsfaser.
4. Opret sættet af brugerdefinerede opdagelsesregler for specifikke avancerede jagtforespørgsler, der opretter beskeder om kendte ransomware-angrebsmetoder, herunder deres tidsplan, navngivning af beskeder og automatiserede handlinger.
5. Bestem [sættet af brugerdefinerede tags](/manage-incidents.md) eller standarder for at oprette nye for at identificere hændelser, der er kendt for at være en del af et større, koordineret ransomware-angreb
6. Bestem sættet af driftsopgaver for ransomware-hændelses- og advarselsstyring. Eksempel:

* Processer for niveau 1-analytikerscanning af indgående hændelser og beskeder og tildeling til niveau 2-analytikere med henblik på undersøgelse.
* Manuelt kørsel af avancerede jagtforespørgsler og deres tidsplan (dagligt, ugentligt, månedligt).
* Igangværende ændringer baseret på ransomware-angrebsundersøgelse og afhjælpningsoplevelser.

### <a name="security-analyst-training"></a>Oplæring af sikkerhedsanalytikere

Efter behov kan du give dine sikkerhedsanalytikere intern træning i:

* Almindelige ransomware-angrebskæder (MITRE-angrebstaktik og almindelige trusselsteknikker og malware)
* Hændelser og beskeder, og hvordan du finder og analyserer dem på Microsoft 365 Defender portalen ved hjælp af:
  * Beskeder og hændelser, der allerede er oprettet af Microsoft 365 Defender
  * Forudscannede URL-baserede filtre for Microsoft 365 Defender-portalen
  * Programmatisk via HÆNDELSES-API'en
* Avancerede jagtforespørgsler, der skal bruges, og deres manuelle tidsplan (dagligt, ugentligt, månedligt)
* Brugerdefinerede registreringsregler, der skal bruges, og deres indstillinger
* Brugerdefinerede hændelseskoder
* De seneste [trusselsanalyserapporter for ransomware-angreb](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) på Microsoft 365 Defender-portalen

### <a name="ongoing-work-based-on-operational-learning-and-new-threats"></a>Løbende arbejde baseret på operationel læring og nye trusler

Som en del af dit SecOps-teams løbende værktøjs- og proces bedste fremgangsmåder og sikkerhedsanalytikernes oplevelser bør du:

* Opdater dit katalog over avancerede jagtforespørgsler med:
  * Nye forespørgsler baseret på de nyeste rapporter om trusselsanalyser på Microsoft 365 Defender-portalen eller [GitHub-lageret for avanceret jagt](<https://github.com/microsoft/Microsoft-365-Defender-Hunting-Queries/tree/master/Ransomware>).
  * Ændringer af eksisterende ændringer for at optimere til trusselsidentifikation eller for at få en bedre beskedkvalitet.
* Opdater regler for brugerdefineret registrering baseret på nye eller ændrede avancerede jagtforespørgsler.
* Opdater sættet af driftsopgaver til ransomware-registrering.
