---
title: Nyheder i Microsoft Purview
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
description: Uanset om det er tilføjelse af nye løsninger til Overholdelsescenter, opdatering af eksisterende funktioner baseret på din feedback eller udrulning af ny og opdateret dokumentation, hjælper Microsoft 365 dig med at holde styr på det stadigt skiftende overholdelseslandskab. Find ud af, hvad vi har været op til denne måned.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b79015ce0ca55bf9a74b6acac8f38f09b9e5e984
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100523"
---
# <a name="whats-new-in-microsoft-purview"></a>Nyheder i Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Uanset om det er tilføjelse af nye løsninger til [Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center.md), opdatering af eksisterende funktioner baseret på din feedback eller udrulning af ny og opdateret dokumentation, Microsoft 365 hjælper dig med at holde dig opdateret om det stadigt foranderlige overholdelseslandskab. Se nedenfor for at se nyheder i Microsoft Purview i dag.

> [!NOTE]
> Nogle funktioner til overholdelse af angivne standarder udrulles med forskellige hastigheder til vores kunder. Hvis du endnu ikke kan se en funktion, kan du prøve at føje dig selv til [målrettet udgivelse](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> Er du interesseret i, hvad der sker i andre administrationscentre? Se disse artikler:
>
> - [Nyheder i Microsoft 365 Administration](/office365/admin/whats-new-in-preview)
> - [Nyheder i SharePoint Administration](/sharepoint/what-s-new-in-admin-center)
> - [Nyheder i Microsoft 365 Defender](../security/defender/whats-new.md)
>
> Og besøg [Microsoft 365 roadmap](https://www.microsoft.com/microsoft-365/roadmap) for at få mere at vide om Microsoft 365 funktioner, der blev startet, udrulles, er under udvikling, er blevet annulleret eller tidligere udgivet.

## <a name="april-2022"></a>April 2022

### <a name="changes-to-product-names"></a>Ændringer af produktnavne

Vi introducerer [Microsoft Purview](https://aka.ms/microsoftpurview), som er et omfattende sæt løsninger, der hjælper dig med at forstå, styre og beskytte hele dit dataområde for at imødegå udfordringerne på en decentraliseret og datarig arbejdsplads i dag. Denne nye brandfamilie kombinerer funktionerne i det tidligere Microsoft Purview Data Map og porteføljen af Microsoft 365 overholdelse af angivne standarder, som kunderne allerede er afhængige af, hvilket giver samlet datastyring og risikostyring for din organisation.

| **Tidligere navn** | **Nyt navn** | **Beskrivelse** |
|:----------------|:-------------|:----------------|
| Microsoft 365 avanceret overvågning <br><br> Microsoft 365 grundlæggende overvågning | Microsoft Purview Audit (Premium) <br><br> Microsoft Purview Audit (Standard)| Overvågningsløsninger indeholder en integreret løsning, der kan hjælpe organisationer med effektivt at reagere på sikkerhedshændelser, retsmedicinske undersøgelser, interne undersøgelser og overholdelsesforpligtelser. Du kan få mere at vide under [Microsoft Purview Advanced Audit (Premium)](advanced-audit.md) og [Microsoft Purview Advanced Audit (Standard).](set-up-basic-audit.md) |
| Microsoft 365 overholdelse af kommunikation | Kommunikationsoverholdelse i Microsoft Purview | Kommunikation med overholdelse af angivne standarder hjælper med at minimere risici ved hurtigt at registrere, registrere og håndtere afhjælpningshandlinger for virksomhedens kommunikationskanaler og politikovertrædelser. Du kan få mere at vide under [Microsoft Purview Communication Compliance](communication-compliance-solution-overview.md). |
| Microsoft Compliance Manager | Microsoft Purview Compliance Manager | Overholdelsesstyring kan hjælpe dig gennem hele overholdelsesrejsen, lige fra opgørelse af dine databeskyttelsesrisici til administration af kompleksiteten ved implementering af kontroller, overholdelse af regler og certificeringer og rapportering til auditører. Du kan få mere at vide under [Microsoft Purview Compliance Manager](compliance-manager.md). |
| Microsoft 365 kundenøgle | Microsoft Purview-kundenøgle | Kundenøglen giver ekstra beskyttelse mod visning af data af uautoriserede systemer eller medarbejdere og supplerer BitLocker-diskkryptering i Microsoft-datacentre. Du kan få mere at vide under [Microsoft Purview Customer Key](customer-key-overview.md). |
| Office 365 Kundelåseboks | Microsoft Purview Customer Lockbox | Kundelåsekasse sikrer, at Microsoft ikke kan få adgang til dit indhold for at udføre servicehandlinger uden din eksplicitte godkendelse. Customer Lockbox fører dig ind i den arbejdsproces for godkendelse, som Microsoft bruger til at sikre, at kun godkendte anmodninger giver adgang til dit indhold. Du kan få mere at vide under [Microsoft Purview Customer Lockbox](customer-lockbox-requests.md). |
| Forebyggelse af datatab | Microsoft Purview Forebyggelse af datatab | DLP hjælper med at beskytte følsomme data og reducere risikoen ved at forhindre brugerne i at dele disse data med personer, der ikke skulle have dem. Du kan få mere at vide under [Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md). |
| Kryptering med dobbelt nøgle for Microsoft 365 | Kryptering af Dobbelt nøgle i Microsoft Purview | DkE (Double Key Encryption) bruger to nøgler sammen til at få adgang til beskyttet indhold. Microsoft gemmer én nøgle i Microsoft Azure, og du holder den anden nøgle. Du kan få mere at vide under [Kryptering af dobbelt nøgle i Microsoft Purview](double-key-encryption.md) |
| Microsoft 365 informationsbarrierer | Microsoft Purview-informationsbarrierer | Informationsbarrierer er en løsning, der begrænser kommunikation og samarbejde mellem visse personer i din organisation for at beskytte interne oplysninger. Du kan få mere at vide under [Microsoft Purview Information Barriers](information-barriers-solution-overview.md). |
| Microsoft Information Protection | Microsoft Purview Information Protection | Information Protection hjælper dig med at finde, klassificere og beskytte følsomme oplysninger, uanset hvor de bor eller rejser. Du kan få mere at vide under [Microsoft Purview Information Protection](information-protection.md). |
| Microsoft Information Governance | Administration af Microsoft Purview-datalivscyklus | Administration af datalivscyklus giver dig værktøjer og funktioner til at bevare det indhold, du skal bruge for at beholde og slette det indhold, du ikke har. Du kan få mere at vide under [Administration af Microsoft Purview-datalivscyklus](data-lifecycle-management.md). |
| Microsoft 365 Styring af insiderrisiko | Styring af Insider-risiko i Microsoft Purview | Insiderrisikostyring bruger hele bredden af tjenesten og tredjepartsindikatorer til at hjælpe dig med hurtigt at identificere, triage og reagere på risikable brugeraktivitet. Du kan få mere at vide under [Microsoft Purview Insider Risk Management](insider-risk-management.md). |
| Office 365 meddelelsekryptering | Microsoft Purview-meddelelsekryptering | Med Meddelelsekryptering kan din organisation sende og modtage krypterede mails mellem personer i og uden for organisationen. Du kan få mere at vide under [Microsoft Purview-meddelelsekryptering](ome.md). |
| Privilegeret adgangsstyring i Microsoft 365 | Microsoft Purview-Privileged Access Management | Privilegeret adgangsstyring hjælper med at beskytte din organisation mod brud og hjælper med at overholde bedste praksis for overholdelse af angivne standarder ved at begrænse stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger. Du kan få mere at vide under [Privilegeret adgangsstyring i Microsoft Purview](privileged-access-management-solution-overview.md). |
| Microsoft-dataforbindelser | Microsoft Purview-dataconnectors | Microsoft 365 gør det muligt for administratorer at bruge dataconnectors til at importere og arkivere ikke-Microsoft-data fra sociale medieplatforme, chatplatforme og platforme til dokumentsamarbejde til postkasser i din Microsoft 365 organisation. Du kan få mere at vide under [Microsoft Purview-dataconnectors](compliance-extensibility.md). |
| Microsoft 365 Avanceret eDiscovery <br><br> Microsoft 365 Core eDiscovery | Microsoft Purview eDiscovery (Premium) <br><br> Microsoft Purview eDiscovery (Standard) | Elektronisk registrering eller eDiscovery er processen med at identificere og levere elektroniske oplysninger, der kan bruges som bevis i juridiske sager. Du kan få mere at vide under [Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md) og [Microsoft Purview eDiscovery (Standard).](get-started-core-ediscovery.md) |
| Microsoft 365-overholdelsescenter | Microsoft Purview-overholdelsesportal | Administrationsportal til adgang til løsninger og løsningskatalog i Microsoft 365 E5 Overholdelse-pakken. Du kan få mere at vide på [Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center.md). |

## <a name="march-2022"></a>Marts 2022

### <a name="communication-compliance"></a>Kommunikationsoverholdelse

- [Undersøg og afhjælp beskeder om kommunikation med overholdelse af angivne standarder](communication-compliance-investigate-remediate.md) – fjernede vejledningen til frarådet anmærkningsvisning.

### <a name="compliance-manager"></a>Overholdelsesstyring

- [Arbejde med forbedringshandlinger](compliance-manager-improvement-actions.md), [Kom i gang med Overholdelsesstyring](compliance-manager-setup.md) – yderligere oplysninger om flere forbedringshandlinger, der automatisk kan overvåges og testes ("løbende vurdering af overholdelse af angivne standarder"); Dette omfatter nye evner til at overordnet teststatus for en handling i forhold til en anden handling.

### <a name="data-classification"></a>Dataklassificering

- [Kom i gang med Indholdsoversigt](data-classification-content-explorer.md) – Teams tilføjede vejledning, pegede licensafsnittet på tjenestebeskrivelser.

### <a name="data-lifecycle-management-and-records-management"></a>Administration af datalivscyklus og datastyring

- [Opbevaringspolitikker for Yammer](create-retention-policies.md#retention-policy-for-yammer-locations) er nu offentligt tilgængelige.
- Understøttelse af delte kanaler, der i øjeblikket er en prøveversion. Når du konfigurerer en opbevaringspolitik for placeringen af Teams kanalmeddelelsen, nedarver alle delte kanaler opbevaringsindstillinger fra deres overordnede team.
- [Grænser pr. lejer for indholdsdisposition](retention-limits.md#maximum-number-of-items-for-disposition).

### <a name="data-loss-prevention"></a>Forebyggelse af datatab

- [Forebyggelse af datatab og Microsoft Teams](dlp-microsoft-teams.md) – Offentlig prøveversion af indhold i Share Teams Kanaler.
- [Kom i gang med Microsoft Compliance-udvidelsen](dlp-chrome-get-started.md) – offentlig prøveversion af begrænsede appgrupper, fjern instruktioner om registreringsdatabasenøgle, konfiguration er nu aktiveret som standard.
- [Konfigurer indstillinger for forebyggelse af datatab for slutpunkter](dlp-configure-endpoint-settings.md) – nyt til offentlig prøveversion af begrænsede appgrupper.
- [Reference til politik til forebyggelse af datatab](dlp-policy-reference.md) – opdateret til offentlig prøveversion af begrænsede appgrupper.
- [Kom i gang med forebyggelse af datatab for Power BI](dlp-powerbi-get-started.md) – nyt til offentlig prøveversion.

### <a name="insider-risk-management"></a>Styring af insider-risiko

- [Kom i gang med styring af insiderrisiko](insider-risk-management-configure.md) – tilføjede nye opgaver i vejledningen Anbefalede handlinger.
- [Kom i gang med indstillinger for styring af insiderrisiko](insider-risk-management-settings.md) – nye opdateringer af funktioner til meddelelser og mailbeskeder, nye opdateringer til analysemeddelelser.

### <a name="microsoft-information-protection"></a>Microsoft Information Protection

- [Understøttelse af produktbemærkninger med dobbeltbytetegnsæt](mip-dbcs-relnotes.md) – ekstra vejledning til macOS.

### <a name="microsoft-priva"></a>Microsoft Priva

- [Konfigurer Priva-indstillinger](/privacy/priva/priva-settings) – opdaterede afklaring af oplysninger om opbevaringsperioder for registreredes rettigheder. tilføjede oplysninger om administration og anvendelse af datagennemsynstags for anmodninger om emnerettigheder.
- [Opret en anmodning om emnerettigheder](/privacy/priva/subject-rights-requests-create) – tilføjede oplysninger om finjustering af søgninger og valg af betingelser og attributter. tilføjede oplysninger om ny funktionalitet, der gør det muligt for brugerne at vælge alle versioner af SharePoint elementer i deres søgning (i forhold til standardindstillingen, som kun returnerer den aktuelle version af SharePoint elementer).
- [Gennemse data for en anmodning om emnerettigheder](/privacy/priva/subject-rights-requests-data-review) – tilføjet oplysninger i trin 3 om gennemsyn af elementer i fasen til datagennemsyn, herunder markering af filer som "include/exclude", anmærkning af filer for at anvende redigeringer, anvende mærker og angive noter.
- [Generér rapporter, og indfri en anmodning om emnerettigheder](/privacy/priva/subject-rights-requests-reports) – der er tilføjet oplysninger om, hvordan du forstår rapporter. præciseres, når der genereres en eksportpakke, og hvordan du arbejder med dens indhold tilføjede oplysninger om overvågningslogge, mærkede filrapporter og opbevaringsperioder for SRR-data og -rapporter.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- [Følsomhedsmærkater for Teams](sensitivity-labels-teams-groups-sites.md):
  - Understøttelse af delte kanaler, der i øjeblikket er en prøveversion. Hvis et team har delte kanaler, arver de automatisk indstillinger for følsomhedsmærkat fra deres overordnede team, og denne mærkat kan ikke fjernes eller erstattes med en anden mærkat.
  - Understøttelse af skabeloner, der tidligere er angivet som [ikke understøttet med Teams Graph API'er og PowerShell-cmdlet'er]( /microsoftteams/sensitivity-labels#limitations).  
- I forbindelse med overvågning af Word, Excel og PowerPoint på internettet er begrundelsesteksten nu udrullet fuldt ud.
- Anvendelse af en standardetiket på eksisterende dokumenter til Word, Excel og PowerPoint på internettet er nu udrullet fuldt ud.

## <a name="february-2022"></a>Februar 2022

### <a name="ediscovery"></a>eDiscovery

- [Administrer skabeloner til tilsynsførende kommunikation i eDiscovery (Premium)](advanced-ediscovery-communications-library.md) – eDiscovery-ledere kan nu oprette skabeloner til tilsynsførende kommunikation, der kan bruges i alle eDiscovery-tilfælde (Premium) i organisationen.
- [Administrer udstedende medarbejdere i eDiscovery (Premium)](advanced-ediscovery-issuing-officers.md) – eDiscovery-ledere kan tilføje en liste over udstedende medarbejdere, der kan tildeles til tilsynsførende kommunikation i alle eDiscovery-tilfælde (Premium) i organisationen.

### <a name="data-lifecycle-management-and-records-management"></a>Administration af datalivscyklus og datastyring

- [Tilpassede områder](retention.md#adaptive-or-static-policy-scopes-for-retention) for opbevaringspolitikker og politikker for opbevaringsmærkater er nu generelt tilgængelige. Vejledningen til [konfiguration af et adaptivt område](retention-settings.md#to-configure-an-adaptive-scope) indeholder nu flere oplysninger om SharePoint områdeområder: Reference til blogindlæg til brug af brugerdefinerede webstedsegenskaber, og hvordan du bruger webstedsegenskaben SiteTemplate til at inkludere eller udelade bestemte webstedstyper med den avancerede forespørgselsgenerator.
- [Politikopslag](retention.md#policy-lookup) i løsningen til administration af datalivscyklus er nu offentligt tilgængelig (GA.
- PowerShell-alternativ til indstillingen for administration af poster, der giver brugerne mulighed for at slette navngivne elementer i SharePoint og OneDrive ved hjælp af AllowFilesWithKeepLabelToBeDeletedSPO og AllowFilesWithKeepLabelToBeDeletedODB fra [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) og [Set-PnPTenant]( /powershell/module/sharepoint-pnp/set-pnptenant).

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- Ny vejledning [Hvorfor vælge indbygget mærkning via AIP-tilføjelsesprogrammet til Office apps](sensitivity-labels-aip.md), hvis du bruger Azure Information Protection (AIP) unified labeling client til Windows computere. Denne side indeholder oplysninger om den nye private prøveversion af Office apps.
- Nye indstillinger for [politikker for automatisk mærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange):
  - Yderligere indstillinger for mail, der skal understøttes, anvender altid en matchende følsomhedsmærkat og anvender kryptering på mails, der modtages fra uden for organisationen.
  - Udeladelser for bestemte instanser (brugere, grupper, websteder) understøttes ved hjælp af den nye indstilling **Udeladt** , når standardvalget **af Alle** er angivet for **Inkluderet**.
- Nu som prøveversion: Mobilenheder (iOS og Android) understøtter [samtidig redigering](sensitivity-labels-coauthoring.md) , når du har minimumversioner og vælger denne prøveversion.
- Understøttelse af angivelse af standardlinktypen for deling udvides til individuelle dokumenter i SharePoint og OneDrive. Du kan finde flere oplysninger i den nye artikel [Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og dokumenter i SharePoint og OneDrive]( sensitivity-labels-default-sharing-link.md).
- Teams Administration understøtter nu objektbeholdermærkater (følsomhedsmærkater inden for grupper & websteder).

## <a name="january-2022"></a>Januar 2022

### <a name="microsoft-purview-data-lifecycle-management"></a>Administration af Microsoft Purview-datalivscyklus

- Dokumentationen til tidligere Microsoft Information Governance er blevet væsentligt revideret og omstruktureret, så du nemmere kan finde oplysninger, der er relateret til de løsninger, du konfigurerer på Microsoft Purview-overholdelsesportalen: Dataconnectors, Datalivscyklusstyring og Datastyring. Som en del af denne revision giver dokumentationen en tydeligere skelnen mellem opbevaringsscenarier for administration af datalivscyklus i forhold til datastyring.
- [Få mere at vide om administration af datalivscyklus](data-lifecycle-management.md) – ny for at understøtte omstruktureringen.
- [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md) – ny, der erstatter "Kom i gang med opbevaring", denne artikel indeholder introduktionstrin til alle funktioner til administration af datalivscyklusser, hvilket omfatter opbevaring.
- [Opret opbevaringsmærkater for undtagelser fra dine opbevaringspolitikker](create-retention-labels-data-lifecycle-management.md) – nyt, identificeret scenarie til brug af opbevaringsmærkater til administration af datalivscyklus i stedet for datastyring.
- [Få mere at vide om arkivpostkasser](archive-mailboxes.md) – ny, der understøtter omstruktureringen, indeholder konceptuelle oplysninger, der tidligere var indeholdt i artiklen "Aktivér arkivpostkasser".

### <a name="microsoft-priva"></a>Microsoft Priva

- [Administration af beskyttelse af personlige oplysninger er nu Microsoft Priva](/privacy/priva/priva-overview) – opdateret for at rebrande produktet og dets løsninger, Administration af risiko for beskyttelse af personlige oplysninger og Priva Subject Rights-anmodninger.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- Understøttelse af nye [rollegrupper og roller](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels), der nu er en prøveversion.
- Nye [overvågningsfunktioner](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) til politikker for automatisk mærkning.
- Udrulles nu: standardetiket for eksisterende dokumenter og justeringstekst for Office på internettet.
- Annonceret for Semi-Annual Enterprise Channel i juli med version 2202+: Samtidig redigering og overvågning af Outlook.

## <a name="december-2021"></a>December 2021

### <a name="compliance-and-service-assurance"></a>Overholdelse og tjenestesikkerhed

- [Azure, Dynamics 365 og Windows meddelelse om brud i henhold til GDPR](/compliance/regulatory/gdpr-breach-notification) – opdateret for at tydeliggøre, at kunderne ikke behøver at bruge en betalingstjeneste, f.eks. Defender for Cloud, for at modtage sikkerheds- og privatlivsmeddelelser

### <a name="ediscovery"></a>eDiscovery

- [eDiscovery-arbejdsproces (Premium) for indhold i Microsoft Teams](teams-workflow-in-advanced-ediscovery.md#reference-guide) – opdateret med en ny vejledning til hurtig reference, der kan downloades, til administration af Teams indhold i eDiscovery (Premium)

### <a name="data-lifecycle-management"></a>Administration af datalivscyklus

- [Aktivér arkivpostkasser i Overholdelsescenter](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) – tilføjet afsnit om nyt diagnosticeringsværktøj til arkivpostkasser
- [Brug netværksoverførsel til at importere din organisations PST-filer til Microsoft 365](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) – PST-import understøtter nu AzCopy v10
- [Gendan en inaktiv postkasse](restore-an-inactive-mailbox.md) – revideret procedure til gendannelse af en inaktiv postkasse ved først at føje LegacyExchangeDN for inaktiv postkasse til destinationspostkassen

### <a name="information-protection"></a>Beskyttelse af oplysninger

- [Udrul en løsning til beskyttelse af oplysninger med Microsoft Purview](information-protection-solution.md) – Ny trinvis vejledning til kunder, der leder efter en præskriptiv oversigt over installation af Microsoft Purview Information Protection

### <a name="retention-and-records-management"></a>Opbevarings- og datastyring

- Ny vejledning til [, hvor lang tid det tager, før opbevaringspolitikker træder i kraft](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- Nye lejerindstillinger udrulles: En indstilling for administration af poster, der forhindrer redigering af egenskaber for navngivne SharePoint elementer, der er markeret som en post og låst, og andre indstillinger, der forhindrer brugerne i at låse elementer, der er markeret som en post, op

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- Obligatorisk mærkning og en standardmærkat for Power BI er nu offentlig tilgængelig (GA)

## <a name="november-2021"></a>November 2021

### <a name="compliance-manager"></a>Overholdelsesstyring

Nye indholdsopdateringer kan ses i [Nyheder i Microsoft Purview Compliance Manager](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>Enheds onboarding

Følgende artikler blev tilføjet for onboarding af enheder:

- [Oversigt over onboarding af macOS-enheder i Microsoft 365 (prøveversion)](device-onboarding-macos-overview.md)
- [Onboarde og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af Intune (prøveversion)](device-onboarding-offboarding-macos-intune.md)
- [Onboard og offboard macOS-enheder i overholdelsesløsninger ved hjælp af Intune til Microsoft Defender for Endpoint-kunder (prøveversion)](device-onboarding-offboarding-macos-intune-mde.md)
- [Onboard og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF Pro (prøveversion)](device-onboarding-offboarding-macos-jamfpro.md)
- [Onboard og offboard macOS-enheder i overholdelsesløsninger ved hjælp af JAMF Pro for Microsoft Defender for Endpoint-kunder (prøveversion)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- [Brug det nye sagsformat i det nye eDiscovery-format (Premium)](advanced-ediscovery-new-case-format.md) blev udgivet til generel tilgængelighed og omdøbt fra "stort sagsformat"

### <a name="retention-and-records-management"></a>Opbevarings- og datastyring
- Udrulning: Nye indstillinger for postadministration, der styrer, om navngivne elementer i SharePoint og OneDrive kan slettes af brugere. Tidligere forhindrede opbevaringsmærkater, der var konfigureret til at bevare indhold, og som ikke mærkede elementer som poster, brugerne fra at slette mærket indhold i SharePoint, da denne handling blev tilladt i OneDrive. Du kan få flere oplysninger under [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

Følgende nye artikler er tilføjet:

- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md)
- [Kom i gang med nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-based-sits-overview.md)
- [Eksportér kildedata for at finde nøjagtigt datamatch baseret på følsom oplysningstype](sit-get-started-exact-data-match-export-data.md)
- [Opret skemaet for nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-get-started-exact-data-match-create-schema.md)
- [Hash og upload kildetabellen med følsomme oplysninger for at få nøjagtige data, der stemmer overens med typer af følsomme oplysninger](sit-get-started-exact-data-match-hash-upload.md)
- [Opret nøjagtigt datamatch for typer/regelpakker af følsomme oplysninger](sit-get-started-exact-data-match-create-rule-package.md)
- [Test et nøjagtigt datamatch for typen af følsomme oplysninger](sit-get-started-exact-data-match-test.md)
- [Administrer dit skema for nøjagtige datamatch](sit-use-exact-data-manage-schema.md)
- [Opdater kildetabelfilen for følsomme oplysninger](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>Følsomhedsmærkater
- Områdenavnet for [mærkater fra Microsoft Purview-dataoversigten](/azure/purview/create-sensitivity-label) er nu "Skematiserede dataaktiver".

## <a name="october-2021"></a>Oktober 2021

### <a name="app-governance"></a>Appstyring

- [Tilføjelsesprogrammet Appstyring til Defender for Cloud Apps er offentligt tilgængeligt](/cloud-app-security/app-governance-manage-app-governance). Dokumentation til appstyring er flyttet for at deltage i dokumentationen til Defender for Cloud Apps.

### <a name="compliance--service-assurance"></a>Overholdelse & service assurance

- [Service assurance](/compliance) – indholdsopdateringer til kvartalsvis gennemgang af certificeringer og erklæringer om anvendelighed) Administration af datacenteraktiver
  - Datacenterarkitektur og infrastruktur
  - Datacenters forretningskontinuitet og it-katastrofeberedskab
  - Miljøforanstaltninger for datacenter
  - Sikkerhed for fysisk adgang til datacenter
  - Microsoft 365 SDL-overholdelsesprogram
  - adgangskontrol til Microsoft 365 tjenestetekniker
  - Vejledning til risikovurdering for MS Cloud

### <a name="data-loss-prevention"></a>Forebyggelse af datatab

- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](endpoint-dlp-learn-about.md) blev opdateret til macOS-understøttelse og avanceret klassificering. opdateret til oprettelse af en brugerdefineret DLP-politik til overvågning af aktivitet for alle understøttede filtyper.
- [Kom i gang med Microsoft 365 Forebyggelse af datatab i Slutpunkt](endpoint-dlp-getting-started.md) blev opdateret til macOS-understøttelse og avanceret klassificering.
- [Brug af Forebyggelse af datatab for Slutpunkt](endpoint-dlp-using.md) blev opdateret til macOS-understøttelse og avanceret klassificering.
- [Referencen til politiktip til forebyggelse af datatab](dlp-policy-tips-reference.md) blev opdateret til understøttelse af macOS og avanceret klassificering.
- [Onboard macOS-enheder i Microsoft 365 (prøveversion)](device-onboarding-macos-overview.md) blev opdateret til macOS-understøttelse og avanceret klassificering.
- Følgende nye sider til onboarding af enheder er tilføjet:
  - [Onboarde og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af Intune (prøveversion)](device-onboarding-offboarding-macos-intune.md)
  - [Onboard og offboard macOS-enheder i overholdelsesløsninger ved hjælp af Intune til Microsoft Defender for Endpoint-kunder (prøveversion)](device-onboarding-offboarding-macos-intune-mde.md)
  - [Onboard og offboard macOS-enheder i Microsoft Purview-løsninger ved hjælp af JAMF Pro (prøveversion)](device-onboarding-offboarding-macos-jamfpro.md)
  - [Onboard og offboard macOS-enheder i overholdelsesløsninger ved hjælp af JAMF Pro for Microsoft Defender for Endpoint-kunder (prøveversion)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- [Indsaml vedhæftede filer i skyen i eDiscovery (Premium)](advanced-ediscovery-cloud-attachments.md) ud over at indsamle den nyeste version af en vedhæftet fil i skyen, kan du indsamle den version, der blev delt i en mail eller Teams chatsamtale. Den nye funktionalitet til automatisk anvendelse af en opbevaringsmærkat på vedhæftede filer i skyen gør det muligt at indsamle den delte version.
- [Konfigurer historiske versioner i ny funktionalitet i eDiscovery (Premium),](advanced-ediscovery-historical-versions.md) der indekserer alle versioner af dokumenter, der er gemt på et SharePoint websted til søgning. Det betyder, at dokumentversioner, der indeholder indhold, som svarer til en samlingsforespørgsel, returneres i søgeresultaterne.

### <a name="encryption"></a>Kryptering

- [Brug end-to-end-kryptering for en til en-Microsoft Teams kald (offentlig prøveversion)](/microsoftteams/teams-end-to-end-encryption) Nyt indhold til den offentlige prøveversion.

### <a name="data-lifecycle-management"></a>Administration af datalivscyklus

- [Konfigurer en connector til import af Epic EHR-overvågningsdata](import-epic-data.md) ny connector giver dig mulighed for at importere data fra Epics elektroniske system til sundhedssektoren for at understøtte et nyt scenarie for misbrug af patientdata i forbindelse med administration af insiderrisiko.
- [Konfiguration af en connector til import af ehr-overvågningsdata til sundhedssektoren](import-healthcare-data.md) ny connector giver dig mulighed for at importere data fra et elektronisk system til registrering af patientdata for at understøtte et nyt scenarie for misbrug af generelle patientdata til styring af insiderrisiko.

### <a name="retention-and-records-management"></a>Opbevarings- og datastyring
- [Områder for tilpassede politikker frigives](retention.md#adaptive-or-static-policy-scopes-for-retention) som prøveversion for opbevaringspolitikker og politikker for opbevaringsmærkater.
- Du kan nu [automatisk anvende en opbevaringsmærkat baseret på en følsomhedsmærkat](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- Filplanen har en ny [importproces](file-plan-manager.md#import-retention-labels-into-your-file-plan).
- [Almindelige indstillinger for opbevaringspolitikker og politikker for opbevaringsmærkater](retention-settings.md): Ny artikel, der indeholder detaljerede oplysninger om konfiguration af tilpassede områder og andre indstillinger i både opbevaringspolitikker og politikker for opbevaringsmærkater.

### <a name="sensitive-information-types"></a>Typer af følsomme oplysninger

- [Få mere at vide om navngivne enheder (prøveversion)](named-entities-learn.md) nyt indhold for navngivne objekter.
- [Brug navngivne objekter i dine politikker til forebyggelse af datatab (prøveversion)](named-entities-use.md) nyt indhold ved hjælp af navngivne objekter.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

- [Standardmærkater og standardpolitikker](mip-easy-trials.md) udrulles til berettigede kunder.

## <a name="september-2021"></a>September 2021

### <a name="app-governance"></a>Appstyring

- [Strømlinet appstyring – introduktionsoplysninger](app-governance-get-started.md) har en ændret arbejdsproces og tilføjet nye links til tilmelding til offentlig prøveversion
- [Ny definition af registreringsbeskeder](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) er tilføjet (opdateret; tilføjet ny definition for besked om samling)

### <a name="auditing"></a>Overvågning

- [Slå overvågning til eller fra](turn-audit-log-search-on-or-off.md) tilføjet nyt afsnit om, hvordan ændringer af overvågningsstatus i en organisation overvåges selv. Det betyder, at overvågningsposter logføres, når overvågning er slået til eller fra. du kan søge i Exchange administratorens overvågningslog for disse overvågningsposter

### <a name="communication-compliance"></a>Kommunikationsoverholdelse

- [Vejledning til kommunikation med SIEM-løsninger](communication-compliance-siem.md) til integration af kommunikationsoverholdelse med SIEM-løsninger)

### <a name="compliance-offerings"></a>Tilbud om overholdelse af angivne standarder

- [MTCS (Multi-Tier Cloud Security)](/compliance/regulatory/offering-mtcs-singapore) Standard for Singapore-opdateringer til Dynamics 365-dækning
- [Payment Card Industry (PCI)](/compliance/regulatory/offering-pci-dss) DSS-opdateringer (Data Security Standard) for SharePoint onlinedækning
- Vejledning til den nye klientsoftware [i afsnit 508](/compliance/regulatory/offering-section-508-vpats)
- [Retningslinjer for tilgængelighed af webindhold](/compliance/regulatory/offering-wcag-2-1) – vejledning til ny klientsoftware

### <a name="compliance--service-assurance"></a>Overholdelse & service assurance

- [Service assurance](/compliance/) kvartalsvise opdateringer af indholdsopdateringer for certificeringer og erklæringer om anvendelighed
  - Ødelæggelse af databærende enheder
  - DDOS-angreb

### <a name="data-connectors"></a>Dataconnectors

- [Arkivering af tredjepartsdata i Microsoft 365](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) dataconnectors fra CellTrust og 17a-4 LLC, der nu er tilgængelige i GCC organisationer i US Government-cloudmiljøet
- [Konfiguration af en connector til arkivering af YouTube-data](archive-youtube-data.md) giver ny vejledning til denne funktion i en offentlig prøveversion.

### <a name="ediscovery"></a>eDiscovery

- [Brug KQL-editoren til at oprette en offentlig prøveversion af søgeforespørgsler](ediscovery-kql-editor.md) på en ny måde at oprette søgeforespørgsler på i Indholdssøgning, eDiscovery (Standard) og eDiscovery (Premium). KQL-editoren leverer automatisk fuldførelse af understøttede søgeegenskaber og -betingelser og viser lister over understøttede værdier for standardegenskaber og -betingelser. KQL-editoren giver også fejlregistrering og forslag til rettelser af potentielle fejl i søgeforespørgsler

### <a name="information-barriers"></a>Informationsbarrierer

- [Kom i gang med informationsbarrierer](information-barriers-policies.md#step-6-information-barriers-modes) Ny prøveversionsfunktion til informationsbarrieretilstande
- [Informationsbarrierer med Microsoft Teams](/microsoftteams/information-barriers-in-teams) ny prøveversionsfunktion for informationsbarrierer
- [Informationsbarrierer med OneDrive](/onedrive/information-barriers) ny prøveversionsfunktion for informationsbarrierer
- [Informationsbarrierer med SharePoint Ny](/sharepoint/information-barriers) prøveversionsfunktion til informationsbarrierer

### <a name="insider-risk-management"></a>Styring af insider-risiko

- [Kom i gang med styring af insiderrisiko](insider-risk-management-configure.md#recommended-actions-preview) ny prøveversionsfunktion til at komme i gang med anbefalede handlinger
- [Undersøg insiderrisikoaktiviteter](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) nye afsnit "Få hjælp til at administrere din insiderrisikobeskedkø"
- [Kom i gang med indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#admin-notifications) ny prøveversionsfunktion for administratormeddelelser

### <a name="retention-and-records-management"></a>Opbevarings- og datastyring
- [Gennemgang af flere faser](disposition.md) er nu offentlig tilgængelig med nye [overvågningshændelser](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities). Gennemsyn af flere faser i dispositionen kan du angive op til fem på hinanden følgende stadier af gennemgangen af dispositionen for en opbevaringsmærkat, og korrekturlæsere kan føje andre brugere til deres dispositionsgennemgangsfase. Du kan også tilpasse mailmeddelelser og påmindelser.
- Private kanaler til [Teams opbevaringspolitikker](create-retention-policies.md#retention-policy-for-teams-locations) er nu offentligt tilgængelige.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater
- [Samtidig redigering og AutoSave](sensitivity-labels-coauthoring.md) er nu offentlig tilgængelig for Windows (minimumversion af 2107 fra Current Channel eller Monthly Enterprise Channel) og macOS (minimumversion af 16.51).
- Udrulning til Office apps, der bruger indbyggede mærkater: Standardindstillingen for mærkater understøtter nu eksisterende dokumenter samt nye dokumenter. Denne ændring i funktionsmåden giver paritet med Azure Information Protection Unified-mærkatklienten. Du kan få flere oplysninger om udrulningen pr. app og minimumversioner i [tabellen med funktioner](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) til Word, Excel og PowerPoint.
- Objektbeholdermærkater understøtter nu [standardindstillingerne for delingslinks ved hjælp af avancerede indstillinger i PowerShell](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings).
- De [kapacitetstabeller](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) , der viser de minimumversioner, der understøttes for indbygget mærkning, har nu versioner for Current Channel, Monthly Enterprise Channel og Semi-Annual Enterprise Channel.
