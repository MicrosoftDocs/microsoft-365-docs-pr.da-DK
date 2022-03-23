---
title: Nyheder i Microsoft 365 overholdelse af regler og standarder
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Uanset om det er tilføjelse af nye løsninger til overholdelsescenter, opdatering af eksisterende funktioner baseret på din feedback eller udrulning af ny og opdateret dokumentation, hjælper Microsoft 365 dig med at holde dig opdateret om de skiftende overholdelsesmuligheder. Find ud af, hvad vi har lavet i denne måned.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 15a97fc419bc6e4264f3c3cd0bbe389b79e5c2f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587512"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>Nyheder i Microsoft 365 overholdelse af regler og standarder

Uanset om det er tilføjelse af nye løsninger til [Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center.md), opdatering af eksisterende funktioner baseret på din feedback eller udrulning af ny og opdateret dokumentation, hjælper Microsoft 365 dig med at holde dig opdateret om de skiftende overholdelsesmuligheder. Nedenfor kan du se nyhederne i Microsoft 365 overholdelse af regler og standarder.

> [!NOTE]
> Nogle funktioner til overholdelse rulles ud med forskellige hastigheder til vores kunder. Hvis du ikke kan se en funktion endnu, kan du prøve at føje dig selv til [den målrettede udgivelsesversion](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Er du interesseret i, hvad der sker i andre administrationer? Se følgende artikler:
>
> - [Nyheder i Microsoft 365 Administration](/office365/admin/whats-new-in-preview)
> - [Nyheder i SharePoint Administration](/sharepoint/what-s-new-in-admin-center)
> - [Nyheder i Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Og besøg [Roadmap til Microsoft 365 for](https://www.microsoft.com/microsoft-365/roadmap) at få mere at vide om Microsoft 365-funktioner, der er blevet lanceret, er ved at blive rullet ud, er under udvikling, er blevet annulleret eller tidligere har udgivet.

## <a name="february-2022"></a>Februar 2022

### <a name="ediscovery"></a>eDiscovery

- [Administrere håndterende kommunikationsskabeloner i Advanced eDiscovery](advanced-ediscovery-communications-library.md) – eDiscovery-ledere kan nu oprette skabeloner tiliansk kommunikation, der kan bruges i alle Advanced eDiscovery-sager i organisationen.
- [Administrer udstedelsesmedarbejdere i Advanced eDiscovery](advanced-ediscovery-issuing-officers.md) – eDiscovery-ledere kan tilføje en liste over udstederofficer, der kan tildeles til kommunikation af kontaktpersoner i alle Advanced eDiscovery-sager i organisationen.

### <a name="information-governance-and-records-management"></a>Styring af oplysninger og datastyring

- [Tilpassede områder til opbevaringspolitikker](retention.md#adaptive-or-static-policy-scopes-for-retention) og opbevaringsetiketpolitikker er nu generelt tilgængelige (GA). Vejledningen til konfiguration [](retention-settings.md#to-configure-an-adaptive-scope) af et tilpasset omfang omfatter nu flere oplysninger om SharePoint-webstedsomfang: Reference til blogindlæg til brug af brugerdefinerede egenskaber for webstedet, og hvordan du bruger webstedsegenskaben SiteTemplate til at medtage eller udelade bestemte webstedstyper med den avancerede forespørgselsgenerator.
- [Opslag til politikker](retention.md#policy-lookup) i løsningen til styring af oplysninger er nu generelt tilgængelig (GA).
- PowerShell-alternativ til indstillingen til datastyring, der giver brugerne mulighed for at slette navnede elementer i SharePoint og OneDrive ved hjælp af AllowFilesWithKeepLabelToBeDeletedSPO og AllowFilesWithKeepLabelToBeDeletedODB fra [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) og [Set-PnPTenant]( /powershell/module/sharepoint-pnp/set-pnptenant).

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- Ny vejledning Hvorfor vælge Indbygget [MIP-mærkning over AIP-tilføjelsesprogrammet til Office-apps](sensitivity-labels-aip.md), hvis du bruger den samlede AIP-klient (Azure Information Protection) til Windows computere. Denne side indeholder oplysninger om den nye private forhåndsvisning af Office apps.
- Nye indstillinger for [politikker for automatisk mærkatering](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange):
  - Yderligere indstillinger for mail til altid at understøtte anvendelse af en tilsvarende følsomhedsmærkat og til at anvende kryptering på mails, der modtages fra uden for organisationen.
  - Udeladelse for bestemte forekomster (brugere, grupper, websteder) understøttes ved hjælp af den  nye indstilling Udeladt, når standardvalget af **Alle** er angivet for **Inkluderet**.
- Nu i eksempelvisning: Mobilenheder (iOS og Android) [](sensitivity-labels-coauthoring.md) understøtter samtidig redigering, når du har minimumsversioner og tilmelder dig denne forhåndsvisning.
- Understøttelse af indstilling af standardlinktypen for deling udvides til individuelle dokumenter i SharePoint og OneDrive. Du kan finde flere oplysninger i den nye artikel Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter [SharePoint og OneDrive]( sensitivity-labels-default-sharing-link.md).
- Teams Administration understøtter nu objektbeholderetiketter (følsomhedsmærkater med omfanget af Grupper & websteder).

## <a name="january-2022"></a>Januar 2022

### <a name="microsoft-information-governance"></a>Microsoft Information Governance

- Siden [og sektionen Microsoft Information Governance i Microsoft 365](manage-information-governance.md) i dokumentationen revideres og ændres væsentligt for at gøre det lettere for dig at finde oplysninger, der relaterer til de løsninger, du konfigurerer i Microsoft 365 Overholdelsescenter: Dataforbindelser, Information Governance og Datastyring. Som en del af denne revision skelner dokumentationen tydeligere mellem opbevaringsscenarier for informationsstyring vs. datastyring.
- [Få mere at vide om informationsstyring](information-governance.md) – nyt for at understøtte strukturomlægningen.
- [Kom i gang med informationsstyring](get-started-with-information-governance.md) – som en ny artikel, der skal erstatte "Introduktion til opbevaring", omfatter denne artikel introduktion til alle funktioner til styring af oplysninger, som omfatter opbevaring.
- [Opret opbevaringsnavne for undtagelser til dine opbevaringspolitikker](create-retention-labels-information-governance.md) – nyt, identificeret scenarie for brug af opbevaringsnavne til informationsstyring i stedet for datastyring.
- [Få mere at vide om arkivpostkasser](archive-mailboxes.md) – nye, som understøtter restrukturering, indeholder grundlæggende oplysninger, der tidligere var i Aktivér arkivpostkasser.

### <a name="microsoft-priva"></a>Microsoft Prkon

- [Administration af beskyttelse af personlige oplysninger er nu Microsoft Priveret](/privacy/priva/priva-overview) – opdateret til at omdøbe produktet og dets løsninger, Pr brians risk management og Pr oversigtsanmodninger om emnerettigheder.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- Understøttelse af de nye [MIP-rollegrupper og -roller](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels), nu i forhåndsvisning.
- Nye [overvågningsegenskaber](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) for politikker for automatisk mærkning.
- Nu udrullet: Standardetiket til eksisterende dokumenter i Aktuel kanal (forhåndsvisning) og justeringstekst Office på internettet.
- Annonceret for virksomhedskanalen Semi-Annual juli med version 2202+: Samtidig redigering og overvågning for Outlook.

## <a name="december-2021"></a>December 2021

### <a name="compliance-and-service-assurance"></a>Overholdelse og tjenestesikring

- [Azure, Dynamics 365 og Windows](/compliance/regulatory/gdpr-breach-notification) meddelelse om brud i henhold til GDPR – opdateret for at tydeliggøre, at kunder ikke behøver at bruge en betalingstjeneste som Defender for Cloud for at modtage meddelelser om sikkerhed og beskyttelse af personlige oplysninger

### <a name="ediscovery"></a>eDiscovery

- [Advanced eDiscovery arbejdsproces for indhold i Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) – opdateret med en ny oversigtsvejledning, der kan downloades, til Teams administrere indhold Advanced eDiscovery

### <a name="information-governance"></a>Styring af oplysninger

- [Aktivér arkivpostkasser i Overholdelsescenter –](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) tilføjet afsnit om nyt diagnosticeringsværktøj til arkivpostkasser
- [Brug netværksupload til at importere din organisations PST-filer til Microsoft 365](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) – PST-import understøtter nu AzCopy v10
- [Gendan en inaktiv postkasse](restore-an-inactive-mailbox.md) – revideret fremgangsmåde til gendannelse af en inaktiv postkasse ved først at tilføje LegacyExchangeDN for inaktiv postkasse til destinationspostkassen

### <a name="information-protection"></a>Beskyttelse af oplysninger

- [Installér en MIP-løsning](information-protection-solution.md) – Ny trinvis vejledning til kunder, der leder efter enscriptiv oversigt, der kan installere Microsoft Information Protection (MIP)

### <a name="retention-and-records-management"></a>Opbevaring og datastyring

- Ny vejledning i [Hvor lang tid det tager at en opbevaringspolitik træder i kraft](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Nye lejerindstillinger udrulles: En indstilling for datastyring, der forhindrer redigering af egenskaber for mærket SharePoint-elementer, der er markeret som en post og låst, og andre indstillinger, der forhindrer brugere i at låse elementer op, der er markeret som en post

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- Obligatorisk mærkning og et standardnavn til Power BI er nu generelt tilgængelige (GA)

## <a name="november-2021"></a>November 2021

### <a name="compliance-manager"></a>Overholdelsesstyring

Nye indholdsopdateringer kan ses [i Nyheder i Microsoft Compliance Manager](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>Onboarding af enhed

Følgende artikler blev føjet til onboarding af enheder:

- [Onboard macOS-enheder Microsoft 365 oversigt (forhåndsvisning)](device-onboarding-macos-overview.md)
- [Onboard and offboard macOS devices into Microsoft 365 Compliance solutions using Intune (preview)](device-onboarding-offboarding-macos-intune.md)
- [Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af Intune til Microsoft Defender til Endpoint-kunder (preview)](device-onboarding-offboarding-macos-intune-mde.md)
- [Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp af SYLF Pro (preview)](device-onboarding-offboarding-macos-jamfpro.md)
- [Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af SYLF Pro til Microsoft Defender til Slutpunkt-kunder (prøveversion)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- [Brug det nye sagsformat i Advanced eDiscovery](advanced-ediscovery-new-case-format.md), der er udgivet til generel tilgængelighed, og omdøbt fra "stort format"

### <a name="retention-and-records-management"></a>Opbevaring og datastyring
- Udrulning: Nye indstillinger for poststyring, der styrer, om mærkede elementer i SharePoint og OneDrive kan slettes af brugere. Tidligere var opbevaringsetiketter konfigureret til at bevare indhold, og som ikke markerede elementer som poster, forhindrede brugere i at slette mærket indhold i SharePoint når denne handling blev tilladt i OneDrive. Få mere at vide under [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

Følgende nye artikler er tilføjet:

- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md)
- [Introduktion til nøjagtige datamatchingsbaserede typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md)
- [Eksportér kildedata for en nøjagtig dataoverensstemmelsesbaseret type af følsomme oplysninger](sit-get-started-exact-data-match-export-data.md)
- [Opret skemaet for nøjagtige datamatchingsbaserede følsomme oplysningstyper](sit-get-started-exact-data-match-create-schema.md)
- [Hashtag og upload kildetabellen for følsomme oplysninger for at få nøjagtige data, der matcher følsomme oplysningstyper](sit-get-started-exact-data-match-hash-upload.md)
- [Oprette en nøjagtig dataoverensstemmelse mellem følsomme oplysningstype/regelpakke](sit-get-started-exact-data-match-create-rule-package.md)
- [Teste en nøjagtig datatype, der matcher følsomme oplysninger](sit-get-started-exact-data-match-test.md)
- [Administrer det nøjagtige skema for datamatching](sit-use-exact-data-manage-schema.md)
- [Opdatere kildetabelfilen med følsomme oplysninger](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Følsomhedsmærkater
- Navnet på området for [Azure-navne til visning](/azure/purview/create-sensitivity-label) er nu "Skemalagte dataaktiver".

## <a name="october-2021"></a>Oktober 2021

### <a name="app-governance"></a>Appstyring

- [Tilføjelsesprogrammet Appstyring for Defender til skyapps har udgivet til generel tilgængelighed](/cloud-app-security/app-governance-manage-app-governance). Dokumentation til appstyring er flyttet til at blive en del af dokumentationen til Defender for Cloud Apps.

### <a name="compliance--service-assurance"></a>Tjenestesikring & overholdelse af regler og standarder

- [Tjenestesikring](/compliance) – kvartalsvis gennemgang af indholdsopdateringer til certificeringer og erklæringer om anvendelse) Administration af aktiver i datacenteret
  - Datacenterarkitektur og infrastruktur
  - Forretningskontinuitet og gendannelse efter nedbrud i datacenteret
  - Miljøbeskyttelse af datacenteret
  - Sikkerhed for fysisk adgang til datacenter
  - Microsoft 365 SDL-overholdelsesprogram
  - Microsoft 365 tjenesteteknikeradgangskontrol
  - Vejledning til risikovurdering af MS Cloud

### <a name="data-loss-prevention"></a>Forebyggelse af datatab

- [Få mere at vide om forebyggelse af](endpoint-dlp-learn-about.md) datatab er blevet opdateret til understøttelse af macOS og avanceret klassificering; opdateret til oprettelse af en brugerdefineret DLP-politik til overvågning af aktivitet for alle understøttede filtyper.
- [Introduktion til Microsoft 365 forebyggelse af datatab på slutpunkter blev](endpoint-dlp-getting-started.md) opdateret til understøttelse af macOS og avanceret klassificering.
- [Brugen af forebyggelse af datatab i slutpunkter](endpoint-dlp-using.md) er blevet opdateret til understøttelse af macOS og avanceret klassificering.
- [Reference til tip til forebyggelse af datatab](dlp-policy-tips-reference.md) er blevet opdateret til understøttelse af macOS og avanceret klassificering.
- [Onboard macOS-enheder i Microsoft 365 (forhåndsvisning)](device-onboarding-macos-overview.md) blev opdateret til macOS-support og avanceret klassificering.
- Følgende nye sider til onboardingenheder er tilføjet:
  - [Onboard and offboard macOS devices into Microsoft 365 Compliance solutions using Intune (preview)](device-onboarding-offboarding-macos-intune.md)
  - [Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af Intune til Microsoft Defender til Endpoint-kunder (preview)](device-onboarding-offboarding-macos-intune-mde.md)
  - [Onboard og offboard macOS-enheder i Microsoft 365 overholdelsesløsninger ved hjælp af SYLF Pro (preview)](device-onboarding-offboarding-macos-jamfpro.md)
  - [Onboard og offboard macOS-enheder i Overholdelsesløsninger ved hjælp af SYLF Pro til Microsoft Defender til Slutpunkt-kunder (prøveversion)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- Indsaml vedhæftede filer fra skyen i Advanced eDiscovery Ud over at indsamle den nyeste version af en vedhæftet skybaseret fil kan du indsamle den version, der blev delt i en mail eller Teams-chatsamtale. Ved hjælp af den nye funktion til automatisk at anvende en [opbevaringsmærkat](advanced-ediscovery-cloud-attachments.md) på vedhæftede filer i skyen er indsamling af den delte version muligt.
- Konfigurer tidligere versioner i [Advanced eDiscovery](advanced-ediscovery-historical-versions.md) nye funktioner, der indekserer alle versioner af dokumenter, der er gemt på et SharePoint-websted, til søgning. Det betyder, at dokumentversioner, der indeholder indhold, der svarer til en samlingsforespørgsel, returneres i søgeresultaterne.

### <a name="encryption"></a>Kryptering

- [Brug en-til-en-kryptering til en-til-en-Microsoft Teams opkald (offentlig prøveversion)](/microsoftteams/teams-end-to-end-encryption) Nyt indhold til den offentlige prøveversion.

### <a name="information-governance"></a>Styring af oplysninger

- [Konfigurer en forbindelse til at importere episk EHR-overvågningsdata](import-epic-data.md) ny forbindelse, gør det muligt at importere data fra Episk elektroniske sundhedsjournaler for at understøtte det nye generelle scenarie for misbrug af patientdata til insider-risikostyring.
- [Konfigurer en forbindelseskomponent](import-healthcare-data.md) til at importere den nye forbindelseskomponent ehr-overvågningsdata til sundhedssektoren, så du kan importere data fra et elektronisk sundhedsdatasystem for at understøtte det nye generelle scenarie for misbrug af patientdata i forbindelse med insider-risikostyring.

### <a name="retention-and-records-management"></a>Opbevaring og datastyring
- [Tilpassede politikomfang frigives i forhåndsvisning](retention.md#adaptive-or-static-policy-scopes-for-retention) for opbevaringspolitikker og opbevaringsmærkatpolitikker.
- Nu kan du [automatisk anvende en opbevaringsmærkat, der er baseret på en følsomhedsmærkat](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- Filplan har en ny [importproces](file-plan-manager.md#import-retention-labels-into-your-file-plan).
- [Almindelige indstillinger for opbevaringspolitikker](retention-settings.md) og opbevaringsetiketpolitikker: Ny artikel for at få detaljerede oplysninger om konfiguration af tilpassede områder og andre indstillinger i både opbevaringspolitikker og opbevaringsetiketpolitikker.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

- [Få mere at vide om navngivne enheder (forhåndsvisning)](named-entities-learn.md) nyt indhold for navngivne enheder.
- [Brug navngivne enheder i dine politikker til forebyggelse af datatab (forhåndsvisning) nyt](named-entities-use.md) indhold om brug af navngivne enheder.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- [Standardnavne og standardpolitikker udrulles](mip-easy-trials.md) til berettigede kunder.

## <a name="september-2021"></a>September 2021

### <a name="app-governance"></a>Appstyring

- [Strømlinet appstyring for at komme i gang-oplysninger](app-governance-get-started.md) har ændret arbejdsprocessen og tilføjet nye links til tilmelding til offentlig forhåndsvisning
- [Definition af nye registreringsbeskeder](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) tilføjet (opdateret; tilføjet ny definition for indsamling af beskeder)

### <a name="auditing"></a>Overvågning

- [Slå overvågning til eller fra tilføjet](turn-audit-log-search-on-or-off.md) nyt afsnit om, hvordan ændringer i overvågningsstatus i en organisation selv overvåges. det betyder, at overvågningsposter logføres, når overvågning er aktiveret eller deaktiveret. kan du søge i Exchange efter disse overvågningsposter i overvågningsloggen

### <a name="communication-compliance"></a>Kommunikationsoverholdelse

- [Kommunikationsoverholdelse med SIEM-løsningsvejledning](communication-compliance-siem.md) til integration af kommunikationsoverholdelse med SIEM-løsninger)

### <a name="compliance-offerings"></a>Tilbud om overholdelse af regler og standarder

- [Skysikkerhed på flere niveauer (MTCS)](/compliance/regulatory/offering-mtcs-singapore) Standard for Singapore-opdateringer til Dynamics 365-dækning
- [Payment Card Industry (IBM)](/compliance/regulatory/offering-pci-dss) DSS-opdateringer (Data Security Standard) til SharePoint Online-dækning
- [USA Afsnit 508 ny vejledning](/compliance/regulatory/offering-section-508-vpats) til klientsoftware
- [Retningslinjer for tilgængelighed i webindhold Ny](/compliance/regulatory/offering-wcag-2-1) vejledning til klientsoftware

### <a name="compliance--service-assurance"></a>Tjenestesikring & overholdelse af regler og standarder

- [Kvartalsvis](/compliance/) gennemgang af indholdsopdateringer til certificeringer og udsagn om anvendelsesmuligheder for tjenestesikring
  - Datalejende enhed, der fungerer som enheder
  - DDOS-angreb

### <a name="data-connectors"></a>Dataforbindelser

- [Arkivering af tredjepartsdata i Microsoft 365-dataforbindelser](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) fra CellTrust og 17a-4 LLC er nu tilgængelig i GCC organisationer i den amerikanske regerings sky
- [Konfigurer en forbindelseskomponent til at arkivere YouTube-data](archive-youtube-data.md) giver ny vejledning til denne funktion i offentlig forhåndsvisning.

### <a name="ediscovery"></a>eDiscovery

- Brug [KQL-editoren](ediscovery-kql-editor.md) til at opbygge søgeforespørgsler med offentlig prøveversion af en ny måde at oprette søgeforespørgsler på i Indholdssøgning, Core eDiscovery og Advanced eDiscovery. KQL-editoren giver autofuldførelse af understøttede søgbare egenskaber og betingelser og viser lister over understøttede værdier for standardegenskaber og -betingelser. KQL-editoren leverer også fejlregistrering og forslag til løsninger af potentielle fejl i søgeforespørgsler

### <a name="information-barriers"></a>Informationsbarrierer

- [Introduktion til informationsbarrierer Ny](information-barriers-policies.md#step-6-information-barriers-modes) forhåndsvisningsfunktion for informationsbarrieretilstande
- [Informationsbarrierer med Microsoft Teams](/microsoftteams/information-barriers-in-teams) forhåndsvisningsfunktion for informationsbarrieretilstande
- [Informationsbarrierer med OneDrive preview-funktion](/onedrive/information-barriers) til informationsbarrieretilstande
- [Informationsbarrierer med SharePoint online-](/sharepoint/information-barriers) og forhåndsvisningsfunktion for informationsbarrieretilstande

### <a name="insider-risk-management"></a>Insider-risikostyring

- [Kom i gang med den nye Preview-funktion Insider](insider-risk-management-configure.md#recommended-actions-preview) Risk Management for at komme i gang med anbefalede handlinger
- [Undersøg insider-risikoaktiviteter](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) nyt 'Få hjælp til at administrere din insider-risikoadvarselskø'-vejledningssektion
- [Introduktion til insider-indstillinger for risikostyring den nye funktion](insider-risk-management-settings.md#admin-notifications) til forhåndsvisning af indstillinger for administratormeddelelser

### <a name="retention-and-records-management"></a>Opbevaring og datastyring
- [Gennemgang af flere faser er](disposition.md) nu generelt tilgængelig med nye [revisionshændelser](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities). Med gennemgang af flere faser kan du angive op til fem på hinanden følgende trin i dispositionsgennemsyn for et opbevaringsnavn, og korrekturlæsere kan føje andre brugere til deres dispositionsgennemsynsfase. Du kan også tilpasse mailbeskeder og påmindelser.
- Private kanaler til [Teams opbevaringspolitikker](create-retention-policies.md#retention-policy-for-teams-locations) er nu generelt tilgængelig (GA).

### <a name="sensitivity-labels"></a>Følsomhedsmærkater
- [Samtidig](sensitivity-labels-coauthoring.md) redigering og automatisk lagring er nu generelt tilgængelig for Windows (minimumversion 2107 fra Aktuel kanal eller Månedlig virksomhedskanal) og macOS (minimumversion 16.51).
- Udrulning Office apps, der bruger indbyggede etiketter: Standardindstillingen for navne understøtter nu eksisterende dokumenter samt nye dokumenter. Denne ændring giver paritet med den samlede Azure Information Protection-etiketklient. Du kan finde flere oplysninger om udrulning pr. app og minimumsversioner i tabellen med [egenskaber for Word](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint), Excel og PowerPoint.
- Objektbeholdernavne understøtter nu [standardindstillingerne for delingslink ved hjælp af avancerede indstillinger i PowerShell](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings).
- De [funktionalitetstabeller](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) , der viser de mindst understøttede versioner til indbygget mærkning, har nu versioner til Aktuel kanal, Månedlig virksomhedskanal og Semi-Annual Enterprise-kanal.
