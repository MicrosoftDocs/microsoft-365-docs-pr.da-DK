---
title: Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: 'Microsoft 365 forebyggelse af datatab på slutpunkt udvider overvågning af filaktiviteter og beskyttende handlinger for disse filer til slutpunkter. Filer gøres synlige i løsningerne til overholdelse af regler og standarder '
ms.openlocfilehash: 83608f005b9024583142515094b2d958b8f5d915
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63590915"
---
# <a name="learn-about-microsoft-365-endpoint-data-loss-prevention"></a>Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter

Du kan bruge Microsoft 365 forebyggelse af datatab (DLP) til at overvåge de handlinger, der er foretaget på elementer, du har besluttet at være følsomme, og for at forhindre utilsigtet deling af disse elementer. Du kan finde flere oplysninger om DLP under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

**Forebyggelse af datatab** på slutpunkt (Slutpunkt DLP) udvider aktivitetsovervågnings- og beskyttelsesfunktionerne i DLP til følsomme elementer, der fysisk gemmes på Windows 10-, Windows 11- og macOS-enheder (Catalina 10.15 eller nyere). Når enheder er onboardet til løsninger til overholdelse af Microsoft 365, bliver oplysningerne om, hvad brugerne gør med følsomme elementer, synlige i Aktivitetsoversigt, og du kan gennemtvinge beskyttende handlinger for disse elementer via [DLP-politikker](create-test-tune-dlp-policy.md).[](data-classification-activity-explorer.md)

> [!TIP]
> Hvis du leder efter enhedsstyring til flytbart lager, skal du se [Flytbare enheder i Microsoft Defender til Storage Adgangskontrol](../security/defender-endpoint/device-control-removable-storage-access-control.md#microsoft-defender-for-endpoint-device-control-removable-storage-access-control).

> [!NOTE]
> I Microsoft 365 regeloverholdelse sker DLP-politikevaluering af følsomme elementer centralt, så der er ingen tidsforsinkelse for, at politikker og politikopdateringer distribueres til individuelle enheder. Når en politik opdateres i overholdelsescenter, tager det normalt ca. en time, før disse opdateringer synkroniseres på tværs af tjenesten. Når politikopdateringer synkroniseres, evalueres elementer på målrettede enheder automatisk, næste gang de åbnes eller ændres.

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>Slutpunktsaktiviteter, du kan overvåge og handle på

Microsoft Endpoint DLP gør det muligt at overvåge og administrere følgende typer af aktiviteter, som brugere tager på følsomme elementer, der fysisk gemmes Windows 10, Windows 11- eller macOS-enheder.

|Aktivitet |Beskrivelse  |Windows 10 1809 og nyere/ Windows 11| macOS Catalina 10.15 (forhåndsvisning) | Auditable/restrictable|
|---------|---------|---------|---------|---------|
|uploade til skytjeneste eller få adgang fra ikke-tilladte browsere    | Registrerer, når en bruger forsøger at overføre et element til et begrænset tjenestedomæne eller få adgang til et element via en browser.  Hvis de bruger en browser, der er angivet i DLP som en ikke-tilladt browser, blokeres uploadaktiviteten, og brugeren omdirigeres til at bruge Microsoft Edge . Microsoft Edge tillader eller blokerer derefter overførslen eller adgangen baseret på DLP-politikkonfigurationen         |understøttet | understøttet|kan overvåges og begrænses|
|kopiér til en anden app    |Registrerer, når en bruger forsøger at kopiere oplysninger fra et beskyttet element og derefter indsætter dem i en anden app, proces eller et andet element. Kopiering og ind indsætter oplysninger i den samme app, proces eller det samme element registreres ikke af denne aktivitet.|understøttet|understøttet         | kan overvåges og begrænses|
|kopiér til flytbare USB-medier |Registrerer, når en bruger forsøger at kopiere et element eller oplysninger til flytbare medier eller USB-enheder.|understøttet|understøttet         | kan overvåges og begrænses|
|kopiér til et netværksshare    |Registrerer, når en bruger forsøger at kopiere et element til et netværksshare eller tilknyttet netværksdrev |understøttet|understøttet         |kan overvåges og begrænses|
|udskrive et dokument    |Registrerer, når en bruger forsøger at udskrive et beskyttet element til en lokal printer eller netværksprinter.|understøttet|understøttet|kan overvåges og begrænses         |
|kopiér til en fjernsession|Registrerer, når en bruger forsøger at kopiere et element til en fjernskrivebord-session |understøttet|understøttes ikke|  kan overvåges og begrænses|
|kopiér til Bluetooth enhed|Registrerer, når en bruger forsøger at kopiere et element til en ikke-tilladt Bluetooth-app (som defineret på listen over tilladte Bluetooth aps i Slutpunkt DLP-indstillinger).|understøttet|understøttes ikke| kan overvåges og begrænses|
|oprette et element|Registrerer, når en bruger opretter et element|understøttet | |kan overvåges|
|omdøbe et element|Registrerer, når en bruger omdøber et element|understøttet | |kan overvåges|

## <a name="monitored-files"></a>Overvågede filer

Slutpunkt DLP understøtter overvågning af disse filtyper. DLP audits the activities for these file types, even if there isn't a policy match. 

- Word-filer
- PowerPoint filer
- Excel filer
- PDF-filer
- .csv filer
- .tsv-filer
- .txt filer
- .rtf-filer
- .c-filer
- .class-filer
- .cpp-filer
- .cs-filer
- .h-filer
- .java-filer
 
Hvis du kun vil overvåge data fra politik matches, kan du deaktivere altid **overvågningsfilaktiviteten for** enheder i slutpunktet DLP globale indstillinger.

> [!NOTE]
> Hvis indstillingen Altid overvågningsfilaktivitet **for** enheder er indstillet, overvåges aktiviteter på alle Word-, PowerPoint-, Excel-, PDF- og .csv-filer altid, selvom enheden ikke er målrettet af nogen politik.

> [!TIP]
> Opret en brugerdefineret DLP-politik for at sikre, at aktiviteter overvåges for [alle understøttede filtyper](create-test-tune-dlp-policy.md).

Slutpunktet DLP overvåger aktivitet baseret på MIME-type, så aktiviteter registreres, selvom filtypenavnet ændres.

### <a name="file-types-preview"></a>Filtyper (eksempel)

Filtyper er en gruppering af filformater, der bruges til at beskytte bestemte arbejdsprocesser eller forretningsområder. Du kan bruge en eller flere filtyper som betingelser i dine DLP-politikker.

|Filtype |App  |overvågede filtypenavne  |
|---------|---------|---------|
|tekstbehandling |Word, PDF | .doc, .docx, .docm, .dot, .dotx, .dotm, .docb, .pdf |
|regneark    |Excel, CSV, TSV |.xls, .xlsx, .xlt, .xlm, .xlsm, .xltx, .xltm, .xlsb, .xlw, .csv, .tsv         |
|præsentation |PowerPoint|.ppt, .pptx, .pos, .pps, .pptm, .potx, .potm, .ppam, .ppsx|
|arkivér  |Filarkiverings- og komprimeringsværktøjer | .zip, .zipx, .rar, .7z, .tar, .gz        |
|mail    |Outlook |.pst, .ost, .msg         |

### <a name="file-extensions-preview"></a>Filtypenavne (forhåndsvisning)

Hvis filtyperne ikke dækker de filtypenavne, du har brug for at vise som en betingelse i en politik, kan du i stedet bruge filtypenavne adskilt af komma.

> [!IMPORTANT]
> Indstillingerne filtypenavne og filtyper kan ikke bruges som betingelser i den samme regel. Hvis du vil bruge dem som betingelser i samme politik, skal de være i separate regler. 

> [!IMPORTANT]
> Disse Windows versioner understøtter filtyper og filtypenavnsfunktioner:
>- Windows 10 20H1/20H2/21H1 (KB 5006738)
>- Windows 10 version 19H1/19H2 (KB 5007189)
>- Windows 10 RS5 (KB 5006744)


## <a name="whats-different-in-endpoint-dlp"></a>Hvad er anderledes i Slutpunkt DLP

Der er et par ekstra begreber, du skal være opmærksom på, før du graver dig ind i Slutpunkt DLP.

### <a name="enabling-device-management"></a>Aktivering af enhedshåndtering

Enhedshåndtering er den funktionalitet, der gør det muligt at indsamle telemetri fra enheder og bringe den ind i Microsoft 365 løsninger til overholdelse af regler og standarder som f.eks. Endpoint DLP og [Insider Risk management](insider-risk-management.md). Du skal onboarde alle enheder, du vil bruge som placeringer i DLP-politikker.

> [!div class="mx-imgBorder"]
> ![skal du aktivere enhedshåndtering.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

Onboarding og offboarding håndteres via scripts, du downloader fra Enhedens administrationscenter. Centeret har brugerdefinerede scripts til hver af disse installationsmetoder:

- lokalt script (op til 10 computere)
- Gruppepolitik
- System Center Configuration Manager (version 1610 eller nyere)
- Administration af mobilenheder/Microsoft Intune
- VDI-onboardingscripts til ikke-permanente computere

> [!div class="mx-imgBorder"]
> ![onboardingside for enheder.](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Brug fremgangsmåderne i [Introduktion til Microsoft 365 slutpunkt DLP til](endpoint-dlp-getting-started.md) onboard-enheder.

Hvis du har onboardede enheder [via Microsoft Defender til Slutpunkt](/windows/security/threat-protection/), vises disse enheder automatisk på listen over enheder. Du kan **aktivere enhedsovervågning for** at bruge slutpunkt DLP.

> [!div class="mx-imgBorder"]
> ![administrerede enheder.](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Visning af slutpunkt-DLP-data

Du kan få vist beskeder, der er relateret til DLP-politikker, der håndhæves på slutpunktsenheder, ved at gå til [administrationsdashboardet for DLP-beskeder](dlp-configure-view-alerts-policies.md).

> [!div class="mx-imgBorder"]
> ![Beskedoplysninger.](../media/Alert-info-1.png)

Du kan også få vist oplysninger om den tilknyttede begivenhed med omfattende metadata i det samme dashboard

> [!div class="mx-imgBorder"]
> ![oplysninger om begivenhed.](../media/Event-info-1.png)

Når en enhed er implementeret, flyder oplysninger om overvågede aktiviteter over i Aktivitetsstifinder, selv før du konfigurerer og implementerer eventuelle DLP-politikker, der har enheder som en placering.

> [!div class="mx-imgBorder"]
> ![slutpunkt-dlp-begivenheder i Aktivitetsstifinder.](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Slutpunktet DLP indsamler omfattende oplysninger om den reviderede aktivitet.

Hvis en fil f.eks. kopieres til flytbare USB-medier, vil du se disse attributter i aktivitetsdetaljerne:

- aktivitetstype
- klient-IP
- målfilsti
- er sket med tidsstempel
- filnavn
- bruger
- filtypenavn
- filstørrelse
- type af følsomme oplysninger (hvis relevant)
- sha1-værdi
- sha256-værdi
- tidligere filnavn
- placering
- forælder
- filepath
- kildeplaceringstype
- platform
- enhedsnavn
- destinationsplaceringstype
- program, der udførte kopien
- Microsoft Defender til slutpunktsenheds-id (hvis relevant)
- producent af flytbare medier
- model for flytbare medier
- flytbare mediers serienummer

> [!div class="mx-imgBorder"]
> ![kopiér til USB-aktivitetsattributter.](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Næste trin

Nu hvor du har lært om Slutpunkt DLP, er de næste trin:

1. [Onboard Windows 10 eller Windows 11 enheder i Microsoft 365 oversigt](device-onboarding-overview.md)
1. [Onboard macOS-enheder Microsoft 365 oversigt (forhåndsvisning)](device-onboarding-macos-overview.md#onboard-macos-devices-into-microsoft-365-overview-preview)
1. [Brug af forebyggelse af datatab i Microsoft Endpoint](endpoint-dlp-using.md)

## <a name="see-also"></a>Se også

- [Introduktion til forebyggelse af datatab i Microsoft Endpoint](endpoint-dlp-getting-started.md)
- [Brug af forebyggelse af datatab i Microsoft Endpoint](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/)
- [Insider-risikostyring](insider-risk-management.md)
