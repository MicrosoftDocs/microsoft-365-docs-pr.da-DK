---
title: Microsofts anbefalinger til EOP og Defender for Office 365 sikkerhedsindstillinger
keywords: Office 365 sikkerhedsanbefalinger, Struktur for afsenderpolitik, domænebaseret meddelelsesrapportering og -overensstemmelse, Domænenøgler identificeret mail, trin, hvordan fungerer det, grundlæggende sikkerhedslinjer, grundlinjer for EOP, oprindelige planer for Defender for Office 365 , konfigurere Defender for Office 365 , konfigurere EOP, konfigurere Defender for Office 365, konfigurer EOP, sikkerhedskonfiguration
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Hvad er bedste praksis for Exchange Online Protection (EOP) og Defender for Office 365 sikkerhedsindstillinger? Hvad er de aktuelle anbefalinger til standardbeskyttelse? Hvad skal bruges, hvis du vil være mere streng? Og hvad ekstra får du, hvis du også bruger Defender for Office 365?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f182b27c4d50ea16a289ac05adceb22c7fc9fd8d
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770949"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** er kernen i sikkerheden for Microsoft 365-abonnementer og hjælper med at forhindre ondsindede mails i at nå ud til dine medarbejderes indbakker. Men med nye, mere sofistikerede angreb, der opstår hver dag, er forbedret beskyttelse ofte påkrævet. **Microsoft Defender for Office 365** Plan 1 eller Plan 2 indeholder yderligere funktioner, der giver administratorer flere lag af sikkerhed, kontrol og undersøgelse.

Selvom vi gør det muligt for sikkerhedsadministratorer at tilpasse deres sikkerhedsindstillinger, er der to sikkerhedsniveauer i EOP og Microsoft Defender for Office 365, som vi anbefaler: **Standard** og **Strict**. Selvom kundemiljøer og -behov er forskellige, hjælper disse filtreringsniveauer med at forhindre uønskede mails i at nå ud til medarbejdernes indbakke i de fleste situationer.

Hvis du vil anvende Standard- eller Strict-indstillingerne automatisk på brugere, skal du se [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

I denne artikel beskrives standardindstillingerne og de anbefalede Standard- og Strict-indstillinger for at beskytte dine brugere. Tabellerne indeholder indstillingerne i Microsoft 365 Defender-portalen og PowerShell (Exchange Online PowerShell eller enkeltstående Exchange Online Protection PowerShell til organisationer uden Exchange Online postkasser).

> [!NOTE]
> Modulet Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) til PowerShell kan hjælpe dig (administratorer) med at finde de aktuelle værdier for disse indstillinger. **Cmdlet'en Get-ORCAReport** genererer især en vurdering af indstillinger for anti-spam, anti-phishing og andre indstillinger for meddelelseshygiejne. Du kan downloade ORCA-modulet på <https://www.powershellgallery.com/packages/ORCA/>.
>
> I Microsoft 365-organisationer anbefaler vi, at du lader filteret for uønsket mail i Outlook være angivet til **Ingen automatisk filtrering** for at forhindre unødvendige konflikter (både positive og negative) med spamfiltreringsdomme fra EOP. Du kan finde flere oplysninger i følgende artikler:
>
> - [Konfigurer indstillinger for uønsket mail i Exchange Online-postkasser](configure-junk-email-settings-on-exo-mailboxes.md)
> - [Om indstillinger for uønsket mail i Outlook](configure-junk-email-settings-on-exo-mailboxes.md#about-junk-email-settings-in-outlook)
> - [Skift beskyttelsesniveauet i filteret for uønsket mail](https://support.microsoft.com/en-us/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b)
> - [Opret lister over sikre afsendere i EOP](create-safe-sender-lists-in-office-365.md)
> - [Opret lister over blokerede afsendere i EOP](create-block-sender-lists-in-office-365.md)

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Anti-spam, antimalware og beskyttelse mod phishing i EOP

Anti-spam, anti-malware og anti-phishing er EOP-funktioner, der kan konfigureres af administratorer. Vi anbefaler følgende Standard- eller Strict-konfigurationer.

### <a name="eop-anti-spam-policy-settings"></a>Politikindstillinger for EOP-antispam

Hvis du vil oprette og konfigurere politikker til bekæmpelse af spam, skal du se [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for massemail & egenskaber for spam**|||||
|**Grænseværdi for massemail** <p> _BulkThreshold_|7|6|4|Du kan finde flere oplysninger [under Samlet klageniveau (BCL) i EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Denne indstilling er kun tilgængelig i PowerShell.|
|**Øg scoreindstillinger for spam**|Ud|Ud|Ud|Alle disse indstillinger er en del af Advanced Spam Filter (ASF). Du kan få flere oplysninger i afsnittet [om asf-indstillinger i politikker til bekæmpelse af spam](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Markér som spamindstillinger**|Ud|Ud|Ud|De fleste af disse indstillinger er en del af ASF. Du kan få flere oplysninger i afsnittet [om asf-indstillinger i politikker til bekæmpelse af spam](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Indeholder bestemte sprog** <p> _EnableLanguageBlockList_ <p> _Liste over sprogblokering_|**Ud** <p> `$false` <p> Tom|**Ud** <p> `$false` <p> Tom|**Ud** <p> `$false` <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser på bestemte sprog baseret på dine forretningsbehov.|
|**Fra disse lande** <p> _EnableRegionBlockList_ <p> _Områdeblokliste_|**Ud** <p> `$false` <p> Tom|**Ud** <p> `$false` <p> Tom|**Ud** <p> `$false` <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser fra bestemte lande baseret på dine forretningsmæssige behov.|
|**Testtilstand** (_TestModeAction_)|**Ingen**|**Ingen**|**Ingen**|Denne indstilling er en del af ASF. Du kan få flere oplysninger i afsnittet [om asf-indstillinger i politikker til bekæmpelse af spam](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Handlinger**||||Uanset hvor du vælger **Karantænemeddelelse**, er feltet **Vælg karantænepolitik** tilgængeligt. Karantænepolitikker definerer, hvad brugerne må gøre for at sætte meddelelser i karantæne. <p> Standard- og Strict-forudindstillede sikkerhedspolitikker bruger standard karantænepolitikkerne (AdminOnlyAccessPolicy eller DefaultFullAccessPolicy uden karantænemeddelelser), som beskrevet i tabellen [her](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Når du opretter en ny politik til bekæmpelse af spam, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der blev sat i karantæne af den pågældende dom (AdminOnlyAccessPolicy uden karantænemeddelelser for **phishing med høj tillid**. DefaultFullAccessPolicy uden karantænemeddelelser for alt andet). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugere i standardpolitikkerne eller brugerdefinerede politikker mod spam. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Spamregistreringshandling** <p> _Spamhandling_|**Flyt meddelelse til mappen Uønsket mail** <p> `MoveToJmf`|**Flyt meddelelse til mappen Uønsket mail** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`||
|**Registreringshandling for spam med høj genkendelsessikkerhed** <p> _HighConfidenceSpamAction_|**Flyt meddelelse til mappen Uønsket mail** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`||
|**Phishing-registreringshandling** <p> _PhishSpamAction_|**Flyt meddelelse til mappen Uønsket mail**<sup>\*</sup> <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`|<sup>\*</sup> Standardværdien er **Flyt meddelelse til mappen Uønsket mail** i standardpolitikken for spam og i nye politikker til bekæmpelse af spam, som du opretter i PowerShell. Standardværdien er **Karantænemeddelelse** i nye politikker til bekæmpelse af spam, som du opretter på Microsoft 365 Defender portalen.|
|**Handling til registrering af phishing med høj genkendelsessikkerhed** <p> _HighConfidencePhishAction_|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`||
|**Masseregistreringshandling** <p> _BulkSpamAction_|**Flyt meddelelse til mappen Uønsket mail** <p> `MoveToJmf`|**Flyt meddelelse til mappen Uønsket mail** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`||
|**Behold spam i karantæne i så mange dage** <p> _QuarantineRetentionPeriod_|15 dage<sup>\*</sup>|30 dage|30 dage|<sup>\*</sup> Standardværdien er 15 dage i standardpolitikken for spam og i nye politikker mod spam, som du opretter i PowerShell. Standardværdien er 30 dage i nye politikker mod spam, som du opretter på Microsoft 365 Defender portalen. <p> Denne værdi påvirker også meddelelser, der er sat i karantæne af politikker til bekæmpelse af phishing. Du kan få flere oplysninger under [Karantænelagrede mails i EOP](quarantine-email-messages.md).|
|**Aktivér tip til spamsikkerhed** <p> _InlineSafetyTipsEnabled_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|Aktivér automatisk fjernelse på nul timer (ZAP) for phishing-meddelelser <p> _PhishZapEnabled_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|Aktivér ZAP for spammeddelelser <p> _SpamZapEnabled_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Tillad & blokliste**|||||
|Tilladte afsendere <p> _AllowedSenders_|Ingen|Ingen|Ingen||
|Tilladte afsenderdomæner <p> _AllowedSenderDomains_|Ingen|Ingen|Ingen|Tilføjelse af domæner til listen over tilladte afsendere er en meget dårlig idé. Personer med ondsindede hensigter kan sende dig en mail, der ellers ville blive filtreret væk. <p> Brug [indsigten spoof intelligence](learn-about-spoof-intelligence.md) og [listen over tilladte/blokerede lejere](tenant-allow-block-list.md) til at gennemse alle afsendere, der forfalsker afsendermailadresser i organisationens maildomæner eller spoofing-mailadresser til afsendere i eksterne domæner.|
|Blokerede afsendere <p> _BlockedSenders_|Ingen|Ingen|Ingen||
|Blokerede afsenderdomæner <p> _BlockedSenderDomains_|Ingen|Ingen|Ingen||

#### <a name="asf-settings-in-anti-spam-policies"></a>ASF-indstillinger i politikker mod spam

Du kan få flere oplysninger om avancerede indstillinger for spamfilter i politikker til bekæmpelse af spam under [Avancerede indstillinger for spamfilter i EOP](advanced-spam-filtering-asf-options.md).

|Navn på sikkerhedsfunktion|Standard|Anbefalede<br/>Standard|Anbefalede<br/>Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Billedlinks til fjernwebsteder** <p> _IncreaseScoreWithImageLinks_|Ud|Ud|Ud||
|**Numerisk IP-adresse i URL-adresse** <p> _IncreaseScoreWithNumericIps_|Ud|Ud|Ud||
|**OMdirigering af URL-adresse til en anden port** <p> _IncreaseScoreWithRedirecttoOtherPort_|Ud|Ud|Ud||
|**Links til .biz- eller .info-websteder** <p> _IncreaseScoreWithBizOrInfoUrls_|Ud|Ud|Ud||
|**Tomme meddelelser** <p> _MarkAsSpamEmptyMessages_|Ud|Ud|Ud||
|**Integrer koder i HTML** <p> _MarkAsSpamEmbedTagsInHtml_|Ud|Ud|Ud||
|**JavaScript eller VBScript i HTML** <p> _MarkAsSpamJavaScriptInHtml_|Ud|Ud|Ud||
|**Formularkoder i HTML** <p> _MarkAsSpamFormTagsInHtml_|Ud|Ud|Ud||
|**Ramme- eller iframe-koder i HTML** <p> _MarkAsSpamFramesInHtml_|Ud|Ud|Ud||
|**Webfejl i HTML** <p> _MarkAsSpamWebBugsInHtml_|Ud|Ud|Ud||
|**Objektkoder i HTML** <p> _MarkAsSpamObjectTagsInHtml_|Ud|Ud|Ud||
|**Følsomme ord** <p> _MarkAsSpamSensitiveWordList_|Ud|Ud|Ud||
|**SPF-post: hard fail** <p> _MarkAsSpamSpfRecordHardFail_|Ud|Ud|Ud||
|**Det lykkedes ikke at filtrere afsender-id'et** <p> _MarkAsSpamFromAddressAuthFail_|Ud|Ud|Ud||
|**Tilbagekastning** <p> _MarkAsSpamNdrBackscatter_|Ud|Ud|Ud||
|**Testtilstand** <p> _TestModeAction_)|Ingen|Ingen|Ingen|I forbindelse med ASF-indstillinger, der understøtter **Test** som en handling, kan du konfigurere testtilstandshandlingen til **Ingen**, **Tilføj standardtekst i X-header** eller **Send Bcc-meddelelse** (`None`, `AddXHeader`eller `BccMessage`). Du kan finde flere oplysninger under [Aktivér, deaktiver eller test ASF-indstillinger](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Politikindstillinger for eOP-udgående spam

Hvis du vil oprette og konfigurere politikker for udgående spam, skal du se [Konfigurer filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md).

Du kan få flere oplysninger om standardgrænserne for afsendelse i tjenesten under [Afsendelse af grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Politikker for udgående spam er ikke en del af Standard- eller Strict-forudindstillede sikkerhedspolitikker. **Værdierne Standard** og **Strict** angiver vores **anbefalede** værdier i standardpolitikken for udgående spam eller brugerdefinerede politikker for udgående spam, som du opretter.

|Navn på sikkerhedsfunktion|Standard|Anbefalede<br/>Standard|Anbefalede<br/>Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Angiv en ekstern meddelelsesgrænse** <p> _RecipientLimitExternalPerHour_|0|500|400|Standardværdien 0 betyder, at du skal bruge tjenestestandarderne.|
|**Angiv en intern meddelelsesgrænse** <p> _RecipientLimitInternalPerHour_|0|1000|800|Standardværdien 0 betyder, at du skal bruge tjenestestandarderne.|
|**Angiv en daglig meddelelsesgrænse** <p> _RecipientLimitPerDay_|0|1000|800|Standardværdien 0 betyder, at du skal bruge tjenestestandarderne.|
|**Begrænsning, der er placeret på brugere, der når meddelelsesgrænsen** <p> _ActionWhenThresholdReached_|**Begræns brugerens adgang til at sende mails indtil den følgende dag** <p> `BlockUserForToday`|**Begræns brugerens adgang til at sende mail** <p> `BlockUser`|**Begræns brugerens adgang til at sende mail** <p> `BlockUser`||
|**Regler for automatisk videresendelse** <p> _AutoForwardingMode_|**Automatisk - Systemstyret** <p> `Automatic`|**Automatisk - Systemstyret** <p> `Automatic`|**Automatisk - Systemstyret** <p> `Automatic`|
|**Send en kopi af udgående meddelelser, der overskrider disse grænser, til disse brugere og grupper** <p> _BccSuspiciousOutboundMail_ <p> _BccSuspiciousOutboundAdditionalRecipients_|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. <p> Denne indstilling fungerer kun i standardpolitikken for udgående spam. Det fungerer ikke i brugerdefinerede politikker for udgående spam, som du opretter.|
|**Giv disse brugere og grupper besked, hvis en afsender er blokeret på grund af afsendelse af udgående spam** <p> _NotifyOutboundSpam_ <p> _NotifyOutboundSpamRecipients_|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|[Standardbeskedpolitikken](../../compliance/alert-policies.md) med navnet **Bruger, der er begrænset til at sende mail**, sender allerede mailmeddelelser til medlemmer af gruppen **TenantAdmins** (**Globale administratorer**), når brugere blokeres på grund af overskridelse af grænserne i politikken. **Vi anbefaler på det kraftigste, at du bruger beskedpolitikken i stedet for denne indstilling i politikken for udgående spam til at give administratorer og andre brugere besked**. Du kan finde instruktioner under [Kontrollér beskedindstillingerne for begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Politikindstillinger for EOP-antimalware

Hvis du vil oprette og konfigurere politikker for antimalware, skal du se [Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Beskyttelsesindstillinger**|||||
|**Aktivér filteret for almindelige vedhæftede filer** <p> _EnableFileFilter_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Denne indstilling sætter meddelelser, der indeholder vedhæftede filer, i karantæne, afhængigt af filtypen, uanset indholdet af den vedhæftede fil. Du kan se en liste over filtyper under [Politikker for antimalware](anti-malware-protection.md#anti-malware-policies).|
|**Aktivér automatisk fjernelse på nul timer for malware** <p> _ZapEnabled_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Karantænepolitik**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny antimalwarepolitik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der er sat i karantæne som malware (AdminOnlyAccessPolicy uden karantænemeddelelser). <p> Standard- og Strict-forudindstillede sikkerhedspolitikker bruger standard karantænepolitikken (AdminOnlyAccessPolicy uden karantænemeddelelser), som beskrevet i tabellen [her](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugere i standardpolitikkerne eller brugerdefinerede politikker for antimalware. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Administration meddelelser**|||||
|**Giv en administrator besked om ikke-leverede meddelelser fra interne afsendere** <p> _EnableInternalSenderAdminNotifications_ <p> _InternalSenderAdminAddress_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Giv en administrator besked om ikke-leverede meddelelser fra eksterne afsendere** <p> _EnableExternalSenderAdminNotifications_ <p> _ExternalSenderAdminAddress_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Tilpas meddelelser**||||Vi har ingen specifikke anbefalinger til disse indstillinger.|
|**Brug tilpasset meddelelsestekst** <p> _Brugerdefineredenotifikationer_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`||
|**Fra navn** <p> _CustomFromName_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Fra adresse** <p> _CustomFromAddress_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Tilpas meddelelser for meddelelser fra interne afsendere**||||Disse indstillinger bruges kun, hvis **Giv en administrator besked om ikke-leverede meddelelser fra interne afsendere** er valgt.|
|**Emne** <p> _CustomInternalSubject_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Meddelelse** <p> _Brugerdefineretinternaltbody_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Tilpas meddelelser for meddelelser fra eksterne afsendere**||||Disse indstillinger bruges kun, hvis **Giv en administrator besked om ikke-leverede meddelelser fra eksterne afsendere** er valgt.|
|**Emne** <p> _Brugerdefineret ekstern element_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Meddelelse** <p> _Brugerdefineret eksternbod_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Indstillinger for EOP-politik for anti-phishing

Du kan få flere oplysninger om disse indstillinger under [Spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings). Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer anti-phishing-politikker i EOP](configure-anti-phishing-policies-eop.md).

Spoof-indstillingerne er indbyrdes relaterede, men indstillingen **Vis sikkerhedstip til første kontakt** er ikke afhængig af spoof-indstillinger.

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Tærskel for phishing & beskyttelse**|||||
|**Aktivér spoof intelligence** <p> _EnableSpoofIntelligence_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som spoof** <p> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Sæt meddelelsen i karantæne** <p> `Quarantine`|Denne indstilling gælder for spoofede afsendere, der automatisk blev blokeret som vist i [indsigten spoof intelligence](learn-about-spoof-intelligence.md) eller manuelt blokeret på [listen over tilladte/blokerede lejere](tenant-allow-block-list.md). <p> Hvis du vælger **Sæt meddelelsen i karantæne**, er feltet **Anvend karantænepolitik** tilgængeligt for at vælge den karantænepolitik, der definerer, hvad brugerne må gøre med meddelelser, der er sat i karantæne som spoofing. Når du opretter en ny anti-phishing-politik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der er sat i karantæne som spoofing (DefaultFullAccessPolicy uden karantænemeddelelser). <p> Standard- og Strict-forudindstillede sikkerhedspolitikker bruger standardkarantænepolitikken (DefaultFullAccessPolicy uden karantænemeddelelser), som beskrevet i tabellen [her](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugere i standardpolitikkerne eller brugerdefinerede politikker til bekæmpelse af phishing. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Vis sikkerhedstip til første kontakt** <p> _EnableFirstContactSafetyTips_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Du kan få flere oplysninger under [Første kontaktsikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Vis (?) for ikke-godkendte afsendere for spoof** <p> _EnableUnauthenticatedSender_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`|Føjer et spørgsmålstegn (?) til afsenderens foto i Outlook for uidentificerede upooferede afsendere. Du kan få flere oplysninger under [Ikke-godkendte afsenderindikatorer](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|
|**Vis mærket "via"** <p> _EnableViaTag_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`|Føjer en via-kode (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis den er forskellig fra domænet i **DKIM-signaturen eller MAIL FROM-adressen** . <p> Du kan få flere oplysninger under [Ikke-godkendte afsenderindikatorer](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender for Office 365 sikkerhed

Der følger flere sikkerhedsfordele med et Microsoft Defender for Office 365 abonnement. Du kan se de seneste nyheder og oplysninger [under Nyheder i Defender for Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Standardpolitikken mod phishing i Microsoft Defender for Office 365 giver [spoof-beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) og postkasseintelligens til alle modtagere. De andre tilgængelige [repræsentationsbeskyttelsesfunktioner](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og [avancerede indstillinger](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) er dog ikke konfigureret eller aktiveret i standardpolitikken. Hvis du vil aktivere alle beskyttelsesfunktioner, skal du ændre standardpolitikken for anti-phishing eller oprette yderligere politikker til bekæmpelse af phishing.
>
> - Selvom der ikke er nogen standardpolitik for vedhæftede filer i sikkerhed eller politik for sikre links, giver den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** beskyttelse af vedhæftede filer og beskyttelse af sikre links til modtagere, der ikke allerede er inkluderet i brugerdefinerede politikker for vedhæftede filer eller Sikre links. Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).
>
> - [Sikre vedhæftede filer til SharePoint, OneDrive og Microsoft Teams-beskyttelse](mdo-for-spo-odb-and-teams.md) og beskyttelse af [sikre dokumenter](safe-docs.md) har ingen afhængigheder af politikker for sikre links.

Hvis dit abonnement omfatter Microsoft Defender for Office 365, eller hvis du har købt Defender for Office 365 som et tilføjelsesprogram, skal du angive følgende Standard- eller Strict-konfigurationer.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Politikindstillinger for anti-phishing i Microsoft Defender for Office 365

EOP-kunder får grundlæggende anti-phishing som tidligere beskrevet, men Defender for Office 365 indeholder flere funktioner og kontrol, der kan hjælpe med at forhindre, registrere og afhjælpe angreb. Hvis du vil oprette og konfigurere disse politikker, skal du se [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Avancerede indstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365

Du kan få flere oplysninger om denne indstilling under [Avancerede tærskler for phishing i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere denne indstilling, skal du se [Konfigurer politikker til anti-phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishingmail** <p> _PhishThresholdLevel_|**1 – Standard** <p> `1`|**2 - Aggressiv** <p> `2`|**3 - Mere aggressiv** <p> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365

Du kan få flere oplysninger om disse indstillinger [under Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer anti-phishing-politikker i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Tærskel for phishing & beskyttelse**|||||
|**Giv brugerne mulighed for at beskytte** (repræsenteret brugerbeskyttelse) <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Ikke markeret <p> `$false` <p> Ingen|Valgte <p> `$true` <p> \<list of users\>|Valgte <p> `$true` <p> \<list of users\>|Vi anbefaler, at du tilføjer brugere (afsendere af meddelelser) i nøgleroller. Internt kan beskyttede afsendere være din administrerende direktør, økonomidirektør og andre overordnede ledere. Eksterne, beskyttede afsendere kan omfatte rådsmedlemmer eller din bestyrelse.|
|**Aktivér domæner for at beskytte** (repræsenteret domænebeskyttelse)|Ikke markeret|Valgte|Valgte||
|**Medtag domæner, jeg ejer** <p> _EnableOrganizationDomainsProtection_|Ud <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Medtag brugerdefinerede domæner** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Ud <p> `$false` <p> Ingen|Valgte <p> `$true` <p> \<list of domains\>|Valgte <p> `$true` <p> \<list of domains\>|Vi anbefaler, at du tilføjer domæner (afsenderdomæner), som du ikke ejer, men som du ofte interagerer med.|
|**Tilføj afsendere og domæner, der er tillid til** <p> _ExcludedSenders_ <p> _ExcludedDomains_|Ingen|Ingen|Ingen|Afhængigt af din organisation anbefaler vi, at du tilføjer afsendere eller domæner, der fejlagtigt identificeres som repræsentationsforsøg.|
|**Aktivér postkasseintelligens** <p> _EnableMailboxIntelligence_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Aktivér intelligens til repræsentationsbeskyttelse** <p> _EnableMailboxIntelligenceProtection_|Ud <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Denne indstilling tillader den angivne handling for repræsentationsregistreringer af mailbox intelligence.|
|**Handlinger**||||Uanset hvor du vælger **Sæt meddelelsen i karantæne**, er feltet **Vælg karantænepolitik** tilgængeligt. Karantænepolitikker definerer, hvad brugerne må gøre for at sætte meddelelser i karantæne. <p> Standard- og Strict-forudindstillede sikkerhedspolitikker bruger standardkarantænepolitikken (DefaultFullAccessPolicy uden karantænemeddelelser), som beskrevet i tabellen [her](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Når du opretter en ny politik til bekæmpelse af phishing, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der blev sat i karantæne af den pågældende dom (DefaultFullAccessPolicy for alle repræsentationsregistreringstyper). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugere i standardpolitikkerne eller brugerdefinerede politikker til bekæmpelse af phishing. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Hvis meddelelsen registreres som en repræsenteret bruger** <p> _TargetedUserProtectionAction_|**Anvend ikke nogen handling** <p> `NoAction`|**Sæt meddelelsen i karantæne** <p> `Quarantine`|**Sæt meddelelsen i karantæne** <p> `Quarantine`||
|**Hvis meddelelsen registreres som et repræsenterede domæne** <p> _TargetedDomainProtectionAction_|**Anvend ikke nogen handling** <p> `NoAction`|**Sæt meddelelsen i karantæne** <p> `Quarantine`|**Sæt meddelelsen i karantæne** <p> `Quarantine`||
|**Hvis postkasseintelligens registrerer og repræsenterer en bruger** <p> _MailboxIntelligenceProtectionAction_|**Anvend ikke nogen handling** <p> `NoAction`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Sæt meddelelsen i karantæne** <p> `Quarantine`||
|**Vis sikkerhedstip til brugeridentificeret repræsentation** <p> _EnableSimilarUsersSafetyTips_|Ud <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Vis sikkerhedstip til repræsentation af domæne** <p> _EnableSimilarDomainsSafetyTips_|Ud <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Vis sikkerhedstip til usædvanlige tegn i brugeridentificeret repræsentation** <p> _EnableUnusualCharactersSafetyTips_|Ud <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Indstillinger for EOP-politik til anti-phishing i Microsoft Defender for Office 365

Dette er de samme indstillinger, som er tilgængelige i [politikindstillinger for anti-spam i EOP](#eop-anti-spam-policy-settings).

### <a name="safe-attachments-settings"></a>Indstillinger for vedhæftede filer, der er tillid til

Sikre vedhæftede filer i Microsoft Defender for Office 365 indeholder globale indstillinger, der ikke har nogen relation til politikker for vedhæftede filer, der er tillid til, og indstillinger, der er specifikke for hver politik for Sikre links. Du kan få flere oplysninger [under Vedhæftede filer, der er tillid til i Defender for Office 365](safe-attachments.md).

Selvom der ikke er nogen standardpolitik for vedhæftede filer, giver den forudindstillede sikkerhedspolitik **for indbygget beskyttelse** beskyttelse af vedhæftede filer til alle modtagere, der ikke allerede er inkluderet i brugerdefinerede politikker for vedhæftede filer, der er tillid til. Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Globale indstillinger for sikre vedhæftede filer

> [!NOTE]
> De globale indstillinger for Sikre vedhæftede filer angives af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** , men ikke **af standard-** eller **strenge** forudindstillede sikkerhedspolitikker. Uanset hvad kan administratorer når som helst ændre disse globale indstillinger for vedhæftede filer, der er tillid til.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den forudindstillede sikkerhedspolitik indbygget **beskyttelse** . Kolonnen **Indbygget beskyttelse** viser de værdier, der er angivet af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** , som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, skal du se [Slå vedhæftede filer, der er tillid til, til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) og [sikre dokumenter i Microsoft 365 E5](safe-docs.md).

I PowerShell skal du bruge [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Slå Defender for Office 365 til for SharePoint, OneDrive og Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Ud <p> `$false`|På <p> `$true`|Hvis du vil forhindre brugere i at downloade skadelige filer, skal du se [Brug SharePoint Online PowerShell til at forhindre brugere i at downloade skadelige filer](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Slå Sikre dokumenter til for Office-klienter** <p> _EnableSafeDocs_|Ud <p> `$false`|På <p> `$true`|Denne funktion er kun tilgængelig og meningsfuld med licenser, der ikke er inkluderet i Defender for Office 365 (f.eks. Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed). Du kan få flere oplysninger [under Sikre dokumenter i Microsoft 365 E5](safe-docs.md).|
|**Tillad, at personer klikker gennem beskyttet visning, selvom sikre dokumenter har identificeret filen som skadelig** <p> _AllowSafeDocsOpen_|Ud <p> `$false`|Ud <p> `$false`|Denne indstilling er relateret til sikre dokumenter.|

#### <a name="safe-attachments-policy-settings"></a>Politikindstillinger for vedhæftede filer, der er tillid til

Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer politikker for vedhæftede filer, der er tillid til i Defender for Office 365](set-up-safe-attachments-policies.md).

I PowerShell skal du bruge cmdlet'erne [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) og [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik for vedhæftede filer, men beskyttelse mod vedhæftede filer tildeles til alle modtagere af den [forudindstillede sikkerhedspolitik **indbygget beskyttelse**](preset-security-policies.md).
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i de nye politikker for vedhæftede filer, du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**Sikre vedhæftede filer ukendt malware-svar** <p> _Aktivér_ og _handling_|**Ud** <p> `-Enable $false` Og `-Action Block`|**Bloker** <p> `-Enable $true` Og `-Action Block`|**Bloker** <p> `-Enable $true` Og `-Action Block`|**Bloker** <p> `-Enable $true` Og `-Action Block`|Når parameteren _Enable_ er $false, betyder værdien af parameteren _Action_ ikke noget.|
|**Karantænepolitik** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy| <p> Standard- og Strict-forudindstillede sikkerhedspolitikker bruger standard karantænepolitikken (AdminOnlyAccessPolicy uden karantænemeddelelser), som beskrevet i tabellen [her](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <p> Når du opretter en ny politik for sikre vedhæftede filer, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der er sat i karantæne af Sikre vedhæftede filer (AdminOnlyAccessPolicy uden karantænemeddelelser). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Omdiriger vedhæftet fil med registrerede vedhæftede filer** : **Aktivér omdirigering** <p> _Omdirigere_ <p> _RedirectAddress_|Ikke valgt, og der er ikke angivet nogen mailadresse. <p> `-Redirect $false` <p> _RedirectAddress_ er tom (`$null`)|Ikke valgt, og der er ikke angivet nogen mailadresse. <p> `-Redirect $false` <p> _RedirectAddress_ er tom (`$null`)|Valgt, og angiv en mailadresse. <p> `$true` <p> en mailadresse|Valgt, og angiv en mailadresse. <p> `$true` <p> en mailadresse|Omdiriger meddelelser til en sikkerhedsadministrator til gennemsyn. <p> **Bemærk**! Denne indstilling er ikke konfigureret i de forudindstillede sikkerhedspolitikker **Standard**, **Strict** eller **Indbygget beskyttelse** . Værdierne **Standard** og **Strict** angiver vores **anbefalede** værdier i de nye politikker for vedhæftede filer, du opretter.|
|**Anvend registreringssvaret Sikre vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout eller fejl)** <p> _ActionOnError_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||

### <a name="safe-links-settings"></a>Indstillinger for Sikre links

Sikre links i Defender for Office 365 indeholder globale indstillinger, der gælder for alle brugere, der er inkluderet i aktive politikker for sikre links, og indstillinger, der er specifikke for hver politik for Sikre links. Du kan få flere oplysninger under [Sikre links i Defender for Office 365](safe-links.md).

Selvom der ikke er nogen standardpolitik for Sikre links, giver den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** beskyttelse af sikre links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede politikker for Sikre links eller Standard eller Strenge forudindstillede sikkerhedspolitikker). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Globale indstillinger for sikre links

> [!NOTE]
> De globale indstillinger for Sikre links angives af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** , men ikke **af standard-** eller **strenge** forudindstillede sikkerhedspolitikker. Uanset hvad kan administratorer når som helst ændre disse globale indstillinger for Sikre links.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den forudindstillede sikkerhedspolitik indbygget **beskyttelse** . Kolonnen **Indbygget beskyttelse** viser de værdier, der er angivet af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** , som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer globale indstillinger for Sikre links i Defender for Office 365](configure-global-settings-for-safe-links.md).

I PowerShell skal du bruge [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Bloker følgende URL-adresser** <p> _ExcludedUrls_|Tom <p> `$null`|Tom <p> `$null`|Vi har ingen specifik anbefaling til denne indstilling. <p> Du kan få flere oplysninger på [listen "Bloker følgende URL-adresser" for Sikre links](safe-links.md#block-the-following-urls-list-for-safe-links). <p> **Bemærk**! Du kan nu administrere blokerings-URL-adresser på [listen over tilladte/blokerede lejere](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). Listen "Bloker følgende URL-adresser" frarådes. Vi forsøger at overføre eksisterende poster fra listen "Bloker følgende URL-adresser" for at blokere URL-adresser på listen over tilladte/blokerede lejere. Meddelelser, der indeholder den blokerede URL-adresse, sættes i karantæne.|

#### <a name="safe-links-policy-settings"></a>Politikindstillinger for sikre links

Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer politikker for sikre links i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

I PowerShell skal du bruge cmdlet'erne [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) og [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik for Sikre links, men Beskyttelse af sikre links tildeles til alle modtagere af den [forudindstillede sikkerhedspolitik **indbygget beskyttelse**](preset-security-policies.md).
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i de nye politikker for sikre links, som du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**URL-adresse & klik på beskyttelsesindstillinger**||||||
|**Handling på potentielt skadelige URL-adresser i mails**||||||
|**On: Safe Links kontrollerer en liste over kendte, ondsindede links, når brugerne klikker på links i mail** <p> _EnableSafeLinksForEmail_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Anvend sikre links på mails, der er sendt i organisationen** <p> _EnableForInternalSenders_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer** <p> _ScanUrls_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Vent på, at scanningen af URL-adressen fuldføres, før meddelelsen leveres** <p> _DeliverMessageAfterScan_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Undlad at omskrive URL-adresser. Kontroller kun via API'en til sikre links** <p> _DisableURLRewrite_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`||
|**Omskriv ikke følgende URL-adresser i mail** <p> _DoNotRewriteUrls_|Ikke markeret <p> Tom|Ikke markeret <p> Tom|Ikke markeret <p> Tom|Ikke markeret <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. <p> **Bemærk**! Formålet med listen "Omskriv ikke følgende URL-adresser" er at springe ombrydningen Af sikre links over for de angivne URL-adresser. I stedet for at bruge denne liste kan du nu [oprette tilladte URL-adresser på listen over tilladte/blokerede lejere](allow-block-urls.md#create-allow-url-entries).|
|**Handling for potentielt skadelige URL-adresser i Microsoft Teams**||||||
|**Om: Sikre links kontrollerer en liste over kendte, skadelige links, når brugerne klikker på links i Microsoft Teams** <p> _EnableSafeLinksForTeams_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Handling for potentielt skadelige URL-adresser i Microsoft Office-apps**||||||
|**På: Sikre links kontrollerer en liste over kendte, skadelige links, når brugerne klikker på links i Microsoft Office-apps** <p> _EnableSafeLinksForO365Clients_|Ikke markeret <p> `$false`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`|Brug Sikre links i understøttede Office 365 skrivebords- og mobilapps (iOS og Android). Du kan få flere oplysninger under [Indstillinger for sikre links til Office-apps](safe-links.md#safe-links-settings-for-office-apps).|
|**Klik på beskyttelsesindstillinger**||||||
|**Spor bruger klik** <p> _TrackUserClicks_|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`|Valgte <p> `$true`||
|**Lad brugerne klikke sig videre til den oprindelige URL-adresse** <p> _AllowClickThrough_|Valgte <p> `$true`|Valgte <p> `$true`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Hvis du slår denne indstilling fra (indstilling _AllowClickThrough_ til ), forhindres det, at `$false`der klikkes videre til den oprindelige URL-adresse.|
|**Vis organisationsbranding på meddelelses- og advarselssider** <p> _EnableOrganizationBranding_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Vi har ingen specifik anbefaling til denne indstilling. <p> Før du slår denne indstilling til, skal du følge vejledningen i [Tilpas Microsoft 365-temaet for din organisation for](../../admin/setup/customize-your-organization-theme.md) at uploade dit virksomhedslogo.|
|**Anmeldelse**||||||
|**Hvordan vil du give brugerne besked?**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|Vi har ingen specifik anbefaling til denne indstilling. <p> Du kan vælge **Brug brugerdefineret meddelelsestekst** (_CustomNotificationText_) for at angive brugerdefineret meddelelsestekst, der skal bruges. Du kan også vælge **Brug Microsoft Translator til automatisk lokalisering** (_UseTranslatedNotificationText_) for at oversætte den brugerdefinerede meddelelsestekst til brugerens sprog.

## <a name="related-articles"></a>Relaterede artikler

- Leder du efter bedste praksis for **regler for Exchange-mailflow (også kaldet transportregler**)? Se [Bedste fremgangsmåder til konfiguration af regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorer og brugere kan sende falske positiver (god mail markeret som dårlig) og falske negativer (dårlig mail er tilladt) til Microsoft til analyse. Du kan få flere oplysninger under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

- Brug disse links til at få oplysninger om, hvordan du **konfigurerer** din [EOP-tjeneste](/exchange/standalone-eop/set-up-your-eop-service) og **konfigurerer** [Microsoft Defender for Office 365](defender-for-office-365.md). Glem ikke de nyttige retninger i "[Beskyt mod trusler i Office 365](protect-against-threats.md)".

- Du kan finde **grundlæggende sikkerhedsindstillinger for Windows** her: [Hvor kan jeg få de grundlæggende sikkerhedsindstillinger?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) for indstillinger for gruppepolitikobjekt/i det lokale miljø og [Brug grundlæggende sikkerhedsindstillinger til at konfigurere Windows-enheder i Intune](/intune/protect/security-baselines) til Intune-baseret sikkerhed. Til sidst kan du sammenligne Microsoft Defender for Endpoint og Microsoft Intune grundlæggende sikkerhedslinjer i [Sammenlign Microsoft Defender for Endpoint og Windows Intune grundlæggende sikkerhedslinjer](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
