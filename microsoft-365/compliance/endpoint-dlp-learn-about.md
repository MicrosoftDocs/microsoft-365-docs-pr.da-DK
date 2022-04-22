---
title: Få mere at vide om forebyggelse af datatab ved slutpunkt
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
description: 'Forebyggelse af datatab for slutpunkter udvider overvågningen af filaktiviteter og beskyttende handlinger for disse filer til slutpunkter. Filer er gjort synlige i løsningerne til overholdelse af angivne standarder '
ms.openlocfilehash: 76649559b1110c02f29584afdfb7e48f57a41f1e
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023365"
---
# <a name="learn-about-endpoint-data-loss-prevention"></a>Få mere at vide om forebyggelse af datatab ved slutpunkt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge Microsoft Purview DLP (Data Loss Prevention) til at overvåge de handlinger, der udføres på elementer, du har besluttet at være følsomme, og til at forhindre utilsigtet deling af disse elementer. Du kan finde flere oplysninger om DLP under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

**Forebyggelse af datatab for slutpunkter** (Slutpunkt DLP) udvider aktivitetsovervågnings- og beskyttelsesfunktionerne i DLP til følsomme elementer, der fysisk gemmes på Windows 10, Windows 11 og macOS-enheder (Catalina 10.15 og nyere). Når enheder er onboardet i Microsoft Purview-løsninger, bliver oplysningerne om, hvad brugerne foretager sig med følsomme elementer, synlige i [Aktivitetsoversigt](data-classification-activity-explorer.md) , og du kan gennemtvinge beskyttende handlinger på disse elementer via [DLP-politikker](create-test-tune-dlp-policy.md).

> [!TIP]
> Hvis du leder efter enhedsstyring til flytbart lager, [skal du se Microsoft Defender for Endpoint Flytbare Storage Access Control til enhedshåndtering](../security/defender-endpoint/device-control-removable-storage-access-control.md#microsoft-defender-for-endpoint-device-control-removable-storage-access-control).

> [!NOTE]
> I Microsoft Purview forekommer DLP-politikevalueringen af følsomme elementer centralt, så der er ingen tidsforskydning for, at politikker og politikopdateringer distribueres til individuelle enheder. Når en politik opdateres i Overholdelsescenter, tager det normalt ca. en time, før disse opdateringer synkroniseres på tværs af tjenesten. Når politikopdateringer er synkroniseret, evalueres elementer på målrettede enheder automatisk igen, næste gang de tilgås eller ændres.

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>Slutpunktsaktiviteter, som du kan overvåge og udføre handlinger på

Slutpunkt DLP giver dig mulighed for at overvåge og administrere følgende typer aktiviteter, som brugere foretager på følsomme elementer, der fysisk er gemt Windows 10, Windows 11 eller macOS-enheder.

|Aktivitet |Beskrivelse  |Windows 10 1809 og nyere / Windows 11| macOS Catalina 10.15| Kan overvåges/begrænses|
|---------|---------|---------|---------|---------|
|uploade til cloudtjenesten eller få adgang fra ikke-tilladte browsere    | Registrerer, når en bruger forsøger at overføre et element til et tjenestedomæne med begrænset adgang eller få adgang til et element via en browser.  Hvis de bruger en browser, der er angivet i DLP som en ikke-tilladt browser, blokeres uploadaktiviteten, og brugeren omdirigeres til at bruge Microsoft Edge. Microsoft Edge tillader eller blokerer derefter upload eller adgang baseret på konfigurationen af DLP-politikken         |Understøttes | Understøttes|kan overvåges og begrænses|
|kopiér til en anden app    |Registrerer, når en bruger forsøger at kopiere oplysninger fra et beskyttet element og derefter indsætte dem i en anden app, i en anden proces eller et andet element. Kopiering og indsættelse af oplysninger i den samme app, proces eller element registreres ikke af denne aktivitet.|Understøttes|Understøttes         | kan overvåges og begrænses|
|kopiér til flytbart USB-medie |Registrerer, når en bruger forsøger at kopiere et element eller oplysninger til flytbare medier eller USB-enheder.|Understøttes|Understøttes         | kan overvåges og begrænses|
|kopiér til et netværksshare    |Registrerer, når en bruger forsøger at kopiere et element til et netværksshare eller et tilknyttet netværksdrev |Understøttes|Understøttes         |kan overvåges og begrænses|
|udskriv et dokument    |Registrerer, når en bruger forsøger at udskrive et beskyttet element på en lokal printer eller netværksprinter.|Understøttes|Understøttes|kan overvåges og begrænses         |
|kopiér til en fjernsession|Registrerer, når en bruger forsøger at kopiere et element til en fjernskrivebordssession |Understøttes|understøttes ikke|  kan overvåges og begrænses|
|kopiér til en Bluetooth enhed|Registrerer, når en bruger forsøger at kopiere et element til en ikke-tilladt Bluetooth app (som defineret på listen over ikke-tilladte Bluetooth aps i DLP-indstillingerne for slutpunktet).|Understøttes|understøttes ikke| kan overvåges og begrænses|
|opret et element|Registrerer, når en bruger opretter et element|Understøttes | |kan overvåges|
|omdøb et element|Registrerer, når en bruger omdøber et element|Understøttes | |kan overvåges|

## <a name="best-practice-for-endpoint-dlp-policies"></a>Bedste praksis for DLP-politikker for slutpunkter

Lad os sige, at du vil blokere alle elementer, der indeholder kreditkortnumre, fra at forlade slutpunkter for brugere af økonomiafdelingen. Vi anbefaler:

- Opret en politik, og sæt den i omfang til slutpunkter og til den pågældende gruppe af brugere.
- Opret en regel i politikken, der registrerer den type oplysninger, du vil beskytte. I dette tilfælde **indeholder indholdet** angivet til *Type af følsomme oplysninger**, og vælg **Kreditkort**.
- Angiv handlingerne for hver aktivitet til **Bloker**.

Se [Design en politik til forebyggelse af datatab](dlp-policy-design.md) for at få mere hjælp til at designe dine DLP-politikker.

## <a name="monitored-files"></a>Overvågede filer

Slutpunkt DLP understøtter overvågning af disse filtyper. DLP overvåger aktiviteterne for disse filtyper, selvom der ikke er et politikmatch. 

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
 
Hvis du kun vil have overvågningsdata fra politikforekomster, kan du slå **altid overvågning af filaktivitet for enheder** fra i de globale DLP-indstillinger for slutpunktet.

> [!NOTE]
> Hvis indstillingen **Overvåg altid filaktivitet for enheder** er slået til, overvåges aktiviteter på alle Word-, PowerPoint-, Excel-, PDF- og .csv-filer altid, selvom enheden ikke er målrettet efter nogen politik.

> [!TIP]
> Hvis du vil sikre, at aktiviteter overvåges for alle understøttede filtyper, skal du oprette en [brugerdefineret DLP-politik](create-test-tune-dlp-policy.md).

Slutpunkt DLP overvåger aktivitetsbaseret på MIME-typen, så aktiviteter registreres, selvom filtypenavnet ændres.

### <a name="file-types"></a>Filtyper

Filtyper er en gruppering af filformater, der bruges til at beskytte bestemte arbejdsprocesser eller forretningsområder. Du kan bruge en eller flere filtyper som betingelser i dine DLP-politikker.

|Filtype |App  |overvågede filtypenavne  |
|---------|---------|---------|
|Tekstbehandling |Word, PDF | .doc, .docx, .docm, .dot, .dotx, .dotm, .docb, .pdf |
|Regneark    |Excel, CSV, TSV |.xls, .xlsx, .xlt, .xlm, .xlsm, .xltx, .xltm, .xlsb, .xlw, .csv, .tsv         |
|Præsentation |PowerPoint|.ppt, .pptx, .pos, .pps, .pptm, .potx, .potm, .ppam, .ppsx|
|Arkiv  |filarkiv- og komprimeringsværktøjer | .zip, .zipx, .rar, .7z, .tar, .gz        |
|E-mail    |Outlook |.pst, .ost, .msg         |

### <a name="file-extensions"></a>Filtypenavne

Hvis filtyperne ikke dækker de filtypenavne, du skal angive som en betingelse i en politik, kan du i stedet bruge filtypenavne adskilt af komma.

> [!IMPORTANT]
> Indstillingerne for filtypenavne og filtyper kan ikke bruges som betingelser i den samme regel. Hvis du vil bruge dem som betingelser i den samme politik, skal de være i separate regler. 

> [!IMPORTANT]
> Disse Windows versioner understøtter filtyper og filtypefunktioner:
>- Windows 10 version 20H1/20H2/21H1 (KB 5006738)
>- Windows 10 version 19H1/19H2 (KB 5007189)
>- Windows 10 RS5 (KB 5006744)


## <a name="whats-different-in-endpoint-dlp"></a>Hvad er anderledes i Endpoint DLP

Der er et par ekstra begreber, som du skal være opmærksom på, før du går i dybden med Slutpunkt DLP.

### <a name="enabling-device-management"></a>Aktivering af enhedshåndtering

Enhedshåndtering er den funktionalitet, der muliggør indsamling af telemetri fra enheder og overfører den til Microsoft Purview-løsninger, f.eks. Endpoint DLP og [styring af insiderrisiko](insider-risk-management.md). Du skal onboarde alle de enheder, du vil bruge som placeringer i DLP-politikker.

> [!div class="mx-imgBorder"]
> ![aktivere enhedshåndtering.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

Onboarding og offboarding håndteres via scripts, du downloader fra Enhedshåndteringscenter. Centeret har brugerdefinerede scripts til hver af disse installationsmetoder:

- lokalt script (op til 10 computere)
- Gruppepolitik
- System Center Configuration Manager (version 1610 eller nyere)
- Mobil Enhedshåndtering/Microsoft Intune
- VDI-onboardingscripts til ikke-faste maskiner

> [!div class="mx-imgBorder"]
> ![onboardingside for enheden.](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Brug procedurerne i [Introduktion til Microsoft 365 Slutpunkt DLP](endpoint-dlp-getting-started.md) til at onboarde enheder.

Hvis du har onboardet enheder via [Microsoft Defender for Endpoint](/windows/security/threat-protection/), vises disse enheder automatisk på listen over enheder. Du kan **slå enhedsovervågning** til for at bruge slutpunktet DLP.

> [!div class="mx-imgBorder"]
> ![liste over administrerede enheder.](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Visning af DLP-data for slutpunkt

Du kan få vist beskeder, der er relateret til DLP-politikker, som gennemtvinges på slutpunktsenheder, ved at gå til [Dashboard til administration af DLP-beskeder](dlp-configure-view-alerts-policies.md).

> [!div class="mx-imgBorder"]
> ![Beskedoplysninger.](../media/Alert-info-1.png)

Du kan også få vist detaljer om den tilknyttede hændelse med omfattende metadata på det samme dashboard

> [!div class="mx-imgBorder"]
> ![hændelsesoplysninger.](../media/Event-info-1.png)

Når en enhed er onboardet, overføres oplysninger om overvågede aktiviteter til Aktivitetsoversigt, selv før du konfigurerer og installerer DLP-politikker, der har enheder som en placering.

> [!div class="mx-imgBorder"]
> ![endpoint dlp-hændelser i aktivitetsoversigten.](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Slutpunkt DLP indsamler omfattende oplysninger om overvåget aktivitet.

Hvis en fil f.eks. kopieres til et flytbart USB-medie, får du vist disse attributter i aktivitetsoplysningerne:

- aktivitetstype
- klient-IP
- sti til destinationsfil
- sket tidsstempel
- filnavn
- Bruger
- filtypenavn
- filstørrelse
- type følsomme oplysninger (hvis det er relevant)
- sha1-værdi
- sha256-værdi
- tidligere filnavn
- Placering
- Overordnede
- filsti
- kildeplaceringstype
- Platform
- enhedsnavn
- destinationsplaceringstype
- program, der udførte kopien
- Microsoft Defender for Endpoint enheds-id (hvis relevant)
- producent af flytbare medieenheder
- flytbar medieenhedsmodel
- flytbar medieenheds serienummer

> [!div class="mx-imgBorder"]
> ![kopiér til usb-aktivitetsattributter.](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Næste trin

Nu, hvor du har lært om Endpoint DLP, er dine næste trin:

1. [Oversigt over onboarding af Windows 10 eller Windows 11 enheder i Microsoft Purview](device-onboarding-overview.md)
1. [Oversigt over onboarding af macOS-enheder i Microsoft Purview](device-onboarding-macos-overview.md)
1. [Konfigurer indstillinger for forebyggelse af datatab ved slutpunkt](dlp-configure-endpoint-settings.md)
1. [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)

## <a name="see-also"></a>Se også

- [Introduktion til Forebyggelse af datatab i Microsoft Endpoint](endpoint-dlp-getting-started.md)
- [Brug af Microsoft Endpoint til forebyggelse af datatab](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Styring af insider-risiko](insider-risk-management.md)
