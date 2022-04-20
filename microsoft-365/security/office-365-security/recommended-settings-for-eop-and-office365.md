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
ms.openlocfilehash: 1a5e18547a26d688238f5d4be94520d4e68c9ff4
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916331"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** er kernen i sikkerheden for Microsoft 365-abonnementer og hjælper med at forhindre ondsindede mails i at nå ud til din medarbejders indbakker. Men med nye, mere sofistikerede angreb, der opstår hver dag, er forbedret beskyttelse ofte påkrævet. **Microsoft Defender for Office 365** Plan 1 eller Plan 2 indeholder yderligere funktioner, der giver administratorer flere lag af sikkerhed, kontrol og undersøgelse.

Selvom vi gør det muligt for sikkerhedsadministratorer at tilpasse deres sikkerhedsindstillinger, er der to sikkerhedsniveauer i EOP og Microsoft Defender for Office 365, som vi anbefaler: **Standard** og **Strict**. Selvom kundemiljøer og -behov er forskellige, hjælper disse filtreringsniveauer med at forhindre uønskede mails i at nå ud til medarbejdernes indbakke i de fleste situationer.

Hvis du vil anvende Standard- eller Strict-indstillingerne automatisk på brugere, skal du se [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

I denne artikel beskrives standardindstillingerne og de anbefalede Standard- og Strict-indstillinger for at beskytte dine brugere. Tabellerne indeholder indstillingerne i Microsoft 365 Defender-portalen og PowerShell (Exchange Online PowerShell eller enkeltstående Exchange Online Protection PowerShell til organisationer uden Exchange Online postkasser).

> [!TIP]
> Du kan ikke ændre de anbefalede Standard- og Strict-indstillinger på portalen Microsoft 365 Defender. Hvis du vil ændre anbefalede værdier, f.eks **. Giv brugerne mulighed for at beskytte**, skal du bruge [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
>
> Modulet Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) til PowerShell kan hjælpe dig (administratorer) med at finde de aktuelle værdier for disse indstillinger. **Cmdlet'en Get-ORCAReport** genererer især en vurdering af indstillinger for anti-spam, anti-phishing og andre indstillinger for meddelelseshygiejne. Du kan downloade ORCA-modulet på <https://www.powershellgallery.com/packages/ORCA/>.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Anti-spam, antimalware og beskyttelse mod phishing i EOP

Anti-spam, anti-malware og anti-phishing er EOP-funktioner, der kan konfigureres af administratorer. Vi anbefaler følgende Standard- eller Strict-konfigurationer.

### <a name="eop-anti-spam-policy-settings"></a>Politikindstillinger for EOP-antispam

Hvis du vil oprette og konfigurere politikker til bekæmpelse af spam, skal du se [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for massemail & egenskaber for spam**|||||
|**Grænseværdi for massemail** <br/><br/> _BulkThreshold_|7|6|4|Du kan finde flere oplysninger [under Samlet klageniveau (BCL) i EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Denne indstilling er kun tilgængelig i PowerShell.|
|**Øg scoreindstillinger for spam**|Ud|Ud|Ud|Alle disse indstillinger er en del af Advanced Spam Filter (ASF). Du kan få flere oplysninger i afsnittet [om asf-indstillinger i politikker til bekæmpelse af spam](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Markér som spamindstillinger**|Ud|Ud|Ud|De fleste af disse indstillinger er en del af ASF. Du kan få flere oplysninger i afsnittet [om asf-indstillinger i politikker til bekæmpelse af spam](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Indeholder bestemte sprog** <br/><br/> _EnableLanguageBlockList_ <br/><br/> _Liste over sprogblokering_|**Ud** <br/><br/> `$false` <br/><br/> Tom|**Ud** <br/><br/> `$false` <br/><br/> Tom|**Ud** <br/><br/> `$false` <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser på bestemte sprog baseret på dine forretningsbehov.|
|**Fra disse lande** <br/><br/> _EnableRegionBlockList_ <br/><br/> _Områdeblokliste_|**Ud** <br/><br/> `$false` <br/><br/> Tom|**Ud** <br/><br/> `$false` <br/><br/> Tom|**Ud** <br/><br/> `$false` <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser fra bestemte lande baseret på dine forretningsmæssige behov.|
|**Testtilstand** (_TestModeAction_)|**Ingen**|**Ingen**|**Ingen**|Denne indstilling er en del af ASF. Du kan få flere oplysninger i afsnittet [om asf-indstillinger i politikker til bekæmpelse af spam](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Handlinger**||||Uanset hvor du vælger **Karantænemeddelelse**, er feltet **Vælg karantænepolitik** tilgængeligt. Karantænepolitikker definerer, hvad brugerne må gøre for at sætte meddelelser i karantæne. <br/><br/> Når du opretter en ny politik til bekæmpelse af spam, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der blev sat i karantæne af den pågældende dom (AdminOnlyAccessPolicy for **phishing med høj genkendelsessikkerhed**. DefaultFullAccessPolicy for alt andet). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Spamregistreringshandling** <br/><br/> _Spamhandling_|**Flyt meddelelse til mappen Uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelse til mappen Uønsket mail** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Registreringshandling for spam med høj genkendelsessikkerhed** <br/><br/> _HighConfidenceSpamAction_|**Karantænemeddelelse** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Phishing-registreringshandling** <br/><br/> _PhishSpamAction_|**Karantænemeddelelse** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Handling til registrering af phishing med høj genkendelsessikkerhed** <br/><br/> _HighConfidencePhishAction_|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Masseregistreringshandling** <br/><br/> _BulkSpamAction_|**Flyt meddelelse til mappen Uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelse til mappen Uønsket mail** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Behold spam i karantæne i så mange dage** <br/><br/> _QuarantineRetentionPeriod_|15 dage<sup>\*</sup>|30 dage|30 dage|<sup>\*</sup> Standardværdien er 15 dage i standardpolitikken for spam og i nye politikker mod spam, som du opretter i PowerShell. Standardværdien er 30 dage i nye politikker mod spam, som du opretter på Microsoft 365 Defender portalen. <br/><br/> Denne værdi påvirker også meddelelser, der er sat i karantæne af politikker til bekæmpelse af phishing. Du kan få flere oplysninger under [Karantænelagrede mails i EOP](quarantine-email-messages.md).|
|**Aktivér tip til spamsikkerhed** <br/><br/> _InlineSafetyTipsEnabled_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|Aktivér automatisk fjernelse på nul timer (ZAP) for phishing-meddelelser <br/><br/> _PhishZapEnabled_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|Aktivér ZAP for spammeddelelser <br/><br/> _SpamZapEnabled_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Tillad & blokliste**|||||
|Tilladte afsendere <br/><br/> _AllowedSenders_|Ingen|Ingen|Ingen||
|Tilladte afsenderdomæner <br/><br/> _AllowedSenderDomains_|Ingen|Ingen|Ingen|Tilføjelse af domæner til listen over tilladte afsendere er en meget dårlig idé. Personer med ondsindede hensigter kan sende dig en mail, der ellers ville blive filtreret væk. <br/><br/> Brug [indsigten spoof intelligence](learn-about-spoof-intelligence.md) og [listen over tilladte/blokerede lejere](tenant-allow-block-list.md) til at gennemse alle afsendere, der forfalsker afsendermailadresser i organisationens maildomæner eller spoofing-mailadresser til afsendere i eksterne domæner.|
|Blokerede afsendere <br/><br/> _BlockedSenders_|Ingen|Ingen|Ingen||
|Blokerede afsenderdomæner <br/><br/> _BlockedSenderDomains_|Ingen|Ingen|Ingen||

#### <a name="asf-settings-in-anti-spam-policies"></a>ASF-indstillinger i politikker mod spam

I tabellen i dette afsnit beskrives DEF-indstillinger (Advanced Spam Filter), der er tilgængelige i politikker til bekæmpelse af spam. Alle disse indstillinger er **Slået fra** for både **Standard** - og **Strict-niveauer** . Du kan få flere oplysninger om ASF-indstillinger under [Avancerede INDSTILLINGER for spamfilter i EOP](advanced-spam-filtering-asf-options.md).

|Navn på sikkerhedsfunktion|Kommenter|
|---|---|
|**Billedlinks til fjernwebsteder** (_IncreaseScoreWithImageLinks_)||
|**Numerisk IP-adresse i URL-adresse** (_IncreaseScoreWithNumericIps_)||
|**URL-omdirigering til anden port** (_IncreaseScoreWithRedirectToOtherPort_)||
|**Links til websteder med .biz eller .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Tomme meddelelser** (_MarkAsSpamEmptyMessages_)||
|**Integrer koder i HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript eller VBScript i HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Formularkoder i HTML** (_MarkAsSpamFormTagsInHtml_)||
|**Ramme- eller iframe-koder i HTML** (_MarkAsSpamFramesInHtml_)||
|**Webfejl i HTML** (_MarkAsSpamWebBugsInHtml_)||
|**Objektkoder i HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**Følsomme ord** (_MarkAsSpamSensitiveWordList_)||
|**SPF-post: hard fail** (_MarkAsSpamSpfRecordHardFail_)||
|**Det lykkedes ikke at filtrere afsender-id'et** (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**Testtilstand** (_TestModeAction_)|I forbindelse med ASF-indstillinger, der understøtter **Test** som en handling, kan du konfigurere testtilstandshandlingen til **Ingen**, **Tilføj standardtekst i X-header** eller **Send Bcc-meddelelse** (`None`, `AddXHeader`eller `BccMessage`). Du kan finde flere oplysninger under [Aktivér, deaktiver eller test ASF-indstillinger](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Politikindstillinger for eOP-udgående spam

Hvis du vil oprette og konfigurere politikker for udgående spam, skal du se [Konfigurer filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md).

Du kan få flere oplysninger om standardgrænserne for afsendelse i tjenesten under [Afsendelse af grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Politikker for udgående spam er ikke en del af Standard- eller Strict-forudindstillede sikkerhedspolitikker. **Værdierne Standard** og **Strict** angiver vores **anbefalede** værdier i standardpolitikken for udgående spam eller brugerdefinerede politikker for udgående spam, som du opretter.

|Navn på sikkerhedsfunktion|Standard|Anbefalede<br/>Standard|Anbefalede<br/>Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Angiv en ekstern meddelelsesgrænse** <br/><br/> _RecipientLimitExternalPerHour_|0|500|400|Standardværdien 0 betyder, at du skal bruge tjenestestandarderne.|
|**Angiv en intern meddelelsesgrænse** <br/><br/> _RecipientLimitInternalPerHour_|0|1000|800|Standardværdien 0 betyder, at du skal bruge tjenestestandarderne.|
|**Angiv en daglig meddelelsesgrænse** <br/><br/> _RecipientLimitPerDay_|0|1000|800|Standardværdien 0 betyder, at du skal bruge tjenestestandarderne.|
|**Begrænsning, der er placeret på brugere, der når meddelelsesgrænsen** <br/><br/> _ActionWhenThresholdReached_|**Begræns brugerens adgang til at sende mails indtil den følgende dag** <br/><br/> `BlockUserForToday`|**Begræns brugerens adgang til at sende mail** <br/><br/> `BlockUser`|**Begræns brugerens adgang til at sende mail** <br/><br/> `BlockUser`||
|**Regler for automatisk videresendelse** <br/><br/> _AutoForwardingMode_|**Automatisk - Systemstyret** <br/><br/> `Automatic`|**Automatisk - Systemstyret** <br/><br/> `Automatic`|**Automatisk - Systemstyret** <br/><br/> `Automatic`|
|**Send en kopi af udgående meddelelser, der overskrider disse grænser, til disse brugere og grupper** <br/><br/> _BccSuspiciousOutboundMail_ <br/><br/> _BccSuspiciousOutboundAdditionalRecipients_|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Denne indstilling fungerer kun i standardpolitikken for udgående spam. Det fungerer ikke i brugerdefinerede politikker for udgående spam, som du opretter.|
|**Giv disse brugere og grupper besked, hvis en afsender er blokeret på grund af afsendelse af udgående spam** <br/><br/> _NotifyOutboundSpam_ <br/><br/> _NotifyOutboundSpamRecipients_|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|[Standardbeskedpolitikken](../../compliance/alert-policies.md) med navnet **Bruger, der er begrænset til at sende mail**, sender allerede mailmeddelelser til medlemmer af gruppen **TenantAdmins** (**Globale administratorer**), når brugere blokeres på grund af overskridelse af grænserne i politikken. **Vi anbefaler på det kraftigste, at du bruger beskedpolitikken i stedet for denne indstilling i politikken for udgående spam til at give administratorer og andre brugere besked**. Du kan finde instruktioner under [Kontrollér beskedindstillingerne for begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Politikindstillinger for EOP-antimalware

Hvis du vil oprette og konfigurere politikker for antimalware, skal du se [Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Beskyttelsesindstillinger**|||||
|**Aktivér filteret for almindelige vedhæftede filer** <br/><br/> _EnableFileFilter_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Denne indstilling sætter meddelelser, der indeholder eksekverbare vedhæftede filer, i karantæne, afhængigt af filtypen, uanset indholdet af den vedhæftede fil.|
|**Aktivér automatisk fjernelse på nul timer for malware** <br/><br/> _ZapEnabled_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Karantænepolitik**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny antimalwarepolitik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der er sat i karantæne som malware (AdminOnlyAccessPolicy). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Modtagermeddelelser**|||||
|**Giv modtagere besked, når meddelelser er sat i karantæne som malware** <br/><br/> _Handling_|Ikke markeret <br/><br/> _Slet meddelelse_|Ikke markeret <br/><br/> _Slet meddelelse_|Ikke markeret <br/><br/> _Slet meddelelse_|Hvis der registreres malware i en vedhæftet fil, er meddelelsen sat i karantæne og kan kun frigives af en administrator.|
|**Afsendermeddelelser**|||||
|**Giv interne afsendere besked, når meddelelser er sat i karantæne som malware** <br/><br/> _EnableInternalSenderNotifications_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Giv eksterne afsendere besked, når meddelelser er sat i karantæne som malware** <br/><br/> _EnableExternalSenderNotifications_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Administratormeddelelser**|||||
|**Giv en administrator besked om ikke-leverede meddelelser fra interne afsendere** <br/><br/> _EnableInternalSenderAdminNotifications_ <br/><br/> _InternalSenderAdminAddress_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Giv en administrator besked om ikke-leverede meddelelser fra eksterne afsendere** <br/><br/> _EnableExternalSenderAdminNotifications_ <br/><br/> _ExternalSenderAdminAddress_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Tilpas meddelelser**||||Vi har ingen specifikke anbefalinger til disse indstillinger.|
|**Brug tilpasset meddelelsestekst** <br/><br/> _Brugerdefineredenotifikationer_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Fra navn** <br/><br/> _CustomFromName_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Fra adresse** <br/><br/> _CustomFromAddress_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Tilpas meddelelser for meddelelser fra interne afsendere**||||Disse indstillinger bruges kun, hvis **Giv interne afsendere besked, når meddelelser er sat i karantæne som malware** , eller **Giv en administrator besked om ikke-leverede meddelelser fra interne afsendere** er valgt.|
|**Emne** <br/><br/> _CustomInternalSubject_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Meddelelse** <br/><br/> _Brugerdefineretinternaltbody_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Tilpas meddelelser for meddelelser fra eksterne afsendere**||||Disse indstillinger bruges kun, hvis **Giv eksterne afsendere besked, når meddelelser er sat i karantæne som malware** eller **Giv en administrator besked om ikke-leverede meddelelser fra eksterne afsendere** er valgt.|
|**Emne** <br/><br/> _Brugerdefineret ekstern element_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Meddelelse** <br/><br/> _Brugerdefineret eksternbod_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Indstillinger for EOP-politik for anti-phishing

Du kan få flere oplysninger om disse indstillinger under [Spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings). Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer anti-phishing-politikker i EOP](configure-anti-phishing-policies-eop.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Tærskel for phishing & beskyttelse**|||||
|**Aktivér spoof intelligence** <br/><br/> _EnableSpoofIntelligence_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som spoof** <br/><br/> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`|Denne indstilling gælder for spoofede afsendere, der automatisk blev blokeret som vist i [indsigten spoof intelligence](learn-about-spoof-intelligence.md) eller manuelt blokeret på [listen over tilladte/blokerede lejere](tenant-allow-block-list.md). <br/><br/> Hvis du vælger **Sæt meddelelsen i karantæne**, er feltet **Anvend karantænepolitik** tilgængeligt for at vælge den karantænepolitik, der definerer, hvad brugerne må gøre med meddelelser, der er sat i karantæne som spoofing. Når du opretter en ny anti-phishing-politik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der blev sat i karantæne som spoofing (DefaultFullAccessPolicy). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Vis første kontakt sikkerhedstip** <br/><br/> _EnableFirstContactSafetyTips_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Du kan få flere oplysninger under [Første kontakt sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Vis (?) for ikke-godkendte afsendere for spoof** <br/><br/> _EnableUnauthenticatedSender_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Føjer et spørgsmålstegn (?) til afsenderens billede i Outlook for uidentificerede forfalskede afsendere. Du kan få flere oplysninger under [Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Vis mærket "via"** <br/><br/> _EnableViaTag_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Føjer en via-kode (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis den er forskellig fra domænet i **DKIM-signaturen eller MAIL FROM-adressen** . <br/><br/> Du kan få flere oplysninger under [Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender for Office 365 sikkerhed

Der følger flere sikkerhedsfordele med et Microsoft Defender for Office 365 abonnement. Du kan se de seneste nyheder og oplysninger [under Nyheder i Defender for Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Standardpolitikken mod phishing i Microsoft Defender for Office 365 giver [spoof-beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) og postkasseintelligens til alle modtagere. De andre tilgængelige [repræsentationsbeskyttelsesfunktioner](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og [avancerede indstillinger](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) er dog ikke konfigureret eller aktiveret i standardpolitikken. Hvis du vil aktivere alle beskyttelsesfunktioner, skal du ændre standardpolitikken for anti-phishing eller oprette yderligere politikker til bekæmpelse af phishing.
>
> - Selvom der ikke er nogen standardpolitik for Pengeskab vedhæftede filer eller Pengeskab **Links-politik**, indeholder den forudindstillede sikkerhedspolitik for indbygget beskyttelse Pengeskab beskyttelse af vedhæftede filer og Pengeskab linksbeskyttelse til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab politikker for vedhæftede filer eller Pengeskab  Links-politikker). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).
>
> - [Pengeskab Beskyttelse af vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md) beskyttelse og [beskyttelse af Pengeskab dokumenter](safe-docs.md) har ingen afhængigheder af politikker for Pengeskab Links.

Hvis dit abonnement omfatter Microsoft Defender for Office 365, eller hvis du har købt Defender for Office 365 som et tilføjelsesprogram, skal du angive følgende Standard- eller Strict-konfigurationer.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Politikindstillinger for anti-phishing i Microsoft Defender for Office 365

EOP-kunder får grundlæggende anti-phishing som tidligere beskrevet, men Defender for Office 365 indeholder flere funktioner og kontrol, der kan hjælpe med at forhindre, registrere og afhjælpe angreb. Hvis du vil oprette og konfigurere disse politikker, skal du se [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Avancerede indstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365

Du kan få flere oplysninger om denne indstilling under [Avancerede tærskler for phishing i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere denne indstilling, skal du se [Konfigurer politikker til anti-phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishingmail** <br/><br/> _PhishThresholdLevel_|**1 – Standard** <br/><br/> `1`|**2 - Aggressiv** <br/><br/> `2`|**3 - Mere aggressiv** <br/><br/> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365

Du kan få flere oplysninger om disse indstillinger [under Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer anti-phishing-politikker i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Tærskel for phishing & beskyttelse**|||||
|**Giv brugerne mulighed for at beskytte** (repræsenteret brugerbeskyttelse) <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|Ikke markeret <br/><br/> `$false` <br/><br/> Ingen|Valgte <br/><br/> `$true` <br/><br/> \<list of users\>|Valgte <br/><br/> `$true` <br/><br/> \<list of users\>|Vi anbefaler, at du tilføjer brugere (afsendere af meddelelser) i nøgleroller. Internt kan beskyttede afsendere være din administrerende direktør, økonomidirektør og andre overordnede ledere. Eksterne, beskyttede afsendere kan omfatte rådsmedlemmer eller din bestyrelse. <br/><br/> I forudindstillede sikkerhedspolitikker kan du ikke angive de brugere, der skal beskyttes. Du skal deaktivere de forudindstillede sikkerhedspolitikker og bruge brugerdefinerede anti-phishing-politikker til at tilføje brugere i nøgleroller som foreslået.|
|**Aktivér domæner for at beskytte** (repræsenteret domænebeskyttelse)|Ikke markeret|Valgte|Valgte||
|**Medtag domæner, jeg ejer** <br/><br/> _EnableOrganizationDomainsProtection_|Ud <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Medtag brugerdefinerede domæner** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|Ud <br/><br/> `$false` <br/><br/> Ingen|Valgte <br/><br/> `$true` <br/><br/> \<list of domains\>|Valgte <br/><br/> `$true` <br/><br/> \<list of domains\>|Vi anbefaler, at du tilføjer domæner (afsenderdomæner), som du ikke ejer, men som du ofte interagerer med. <br/><br/> I forudindstillede sikkerhedspolitikker kan du ikke angive de brugerdefinerede domæner, der skal beskyttes. Du skal deaktivere de forudindstillede sikkerhedspolitikker og bruge brugerdefinerede anti-phishing-politikker til at tilføje brugerdefinerede domæner for at beskytte som foreslået.|
|**Tilføj afsendere og domæner, der er tillid til** <br/><br/> _ExcludedSenders_ <br/><br/> _ExcludedDomains_|Ingen|Ingen|Ingen|Afhængigt af din organisation anbefaler vi, at du tilføjer afsendere eller domæner, der fejlagtigt identificeres som repræsentationsforsøg.|
|**Aktivér postkasseintelligens** <br/><br/> _EnableMailboxIntelligence_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Aktivér intelligens til repræsentationsbeskyttelse** <br/><br/> _EnableMailboxIntelligenceProtection_|Ud <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Denne indstilling tillader den angivne handling for repræsentationsregistreringer af mailbox intelligence.|
|**Handlinger**||||Uanset hvor du vælger **Sæt meddelelsen i karantæne**, er feltet **Vælg karantænepolitik** tilgængeligt. Karantænepolitikker definerer, hvad brugerne må gøre for at sætte meddelelser i karantæne. <br/><br/> Når du opretter en ny politik til bekæmpelse af phishing, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der blev sat i karantæne af den pågældende dom (DefaultFullAccessPolicy for alle repræsentationsregistreringstyper). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Hvis meddelelsen registreres som en repræsenteret bruger** <br/><br/> _TargetedUserProtectionAction_|**Anvend ikke nogen handling** <br/><br/> `NoAction`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`|Husk, at forudindstillede sikkerhedspolitikker ikke giver dig mulighed for at angive de brugere, der skal beskyttes, så denne indstilling gør intet effektivt i forudindstillede sikkerhedspolitikker.|
|**Hvis meddelelsen registreres som et repræsenterede domæne** <br/><br/> _TargetedDomainProtectionAction_|**Anvend ikke nogen handling** <br/><br/> `NoAction`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`|Husk, at forudindstillede sikkerhedspolitikker ikke giver dig mulighed for at angive de brugerdefinerede domæner, der skal beskyttes, så denne indstilling påvirker kun domæner, som du ejer, ikke brugerdefinerede domæner.|
|**Hvis postkasseintelligens registrerer og repræsenterer en bruger** <br/><br/> _MailboxIntelligenceProtectionAction_|**Anvend ikke nogen handling** <br/><br/> `NoAction`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`||
|**Vis sikkerhedstip for bruger repræsentering** <br/><br/> _EnableSimilarUsersSafetyTips_|Ud <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Vis sikkerhedstip for domæne repræsentering** <br/><br/> _EnableSimilarDomainsSafetyTips_|Ud <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Vis usædvanlige tegn sikkerhedstip** <br/><br/> _EnableUnusualCharactersSafetyTips_|Ud <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Indstillinger for EOP-politik til anti-phishing i Microsoft Defender for Office 365

Dette er de samme indstillinger, som er tilgængelige i [politikindstillinger for anti-spam i EOP](#eop-anti-spam-policy-settings).

Spoof-indstillingerne er indbyrdes relaterede, men indstillingen **Vis første kontakt sikkerhedstip** har ingen afhængighed af spoof-indstillinger.

|Navn på sikkerhedsfunktion|Standard|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|---|
|**Tærskel for phishing & beskyttelse**|||||
|**Aktivér spoof intelligence** <br/><br/> _EnableSpoofIntelligence_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som spoof** <br/><br/> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Sæt meddelelsen i karantæne** <br/><br/> `Quarantine`|Denne indstilling gælder for spoofede afsendere, der automatisk blev blokeret som vist i [indsigten spoof intelligence](learn-about-spoof-intelligence.md) eller manuelt blokeret på [listen over tilladte/blokerede lejere](tenant-allow-block-list.md). <br/><br/> Hvis du vælger **Sæt meddelelsen i karantæne**, er feltet **Anvend karantænepolitik** tilgængeligt for at vælge den karantænepolitik, der definerer, hvad brugerne har tilladelse til at gøre for karantænemeddelelser. Når du opretter en ny anti-phishing-politik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for spoof-karantænemeddelelser (DefaultFullAccessPolicy). <br/><br/> Administratorer kan oprette og vælge en brugerdefineret karantænepolitik, der definerer, hvad modtagerne har tilladelse til at gøre ved disse meddelelser i karantæne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Vis første kontakt sikkerhedstip** <br/><br/> _EnableFirstContactSafetyTips_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Du kan få flere oplysninger under [Første kontakt sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Vis (?) for ikke-godkendte afsendere for spoof** <br/><br/> _EnableUnauthenticatedSender_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Føjer et spørgsmålstegn (?) til afsenderens billede i Outlook for uidentificerede forfalskede afsendere. Du kan få flere oplysninger under [Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Vis mærket "via"** <br/><br/> _EnableViaTag_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Føjer en via-kode (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis den er forskellig fra domænet i **DKIM-signaturen eller MAIL FROM-adressen** . <br/><br/> Du kan få flere oplysninger under [Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|

### <a name="safe-attachments-settings"></a>Pengeskab indstillinger for vedhæftede filer

Pengeskab Vedhæftede filer i Microsoft Defender for Office 365 indeholder globale indstillinger, der ikke har nogen relation til Pengeskab politikker for vedhæftede filer, og indstillinger, der er specifikke for hver politik for Pengeskab links. Du kan få flere oplysninger under [Pengeskab Vedhæftede filer i Defender for Office 365](safe-attachments.md).

Selvom der ikke er nogen standardpolitik for Pengeskab Vedhæftede filer, giver den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** Pengeskab beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab politikker for vedhæftede filer). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Globale indstillinger for vedhæftede filer Pengeskab

> [!NOTE]
> De globale indstillinger for Pengeskab Vedhæftede filer angives af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse**, men ikke **af standard-** eller **strenge** forudindstillede sikkerhedspolitikker. Uanset hvad kan administratorer når som helst ændre disse globale Pengeskab indstillinger for vedhæftede filer.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den forudindstillede sikkerhedspolitik indbygget **beskyttelse** . Kolonnen **Indbygget beskyttelse** viser de værdier, der er angivet af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** , som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, skal du se [Slå Pengeskab vedhæftede filer til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) og [Pengeskab dokumenter i Microsoft 365 E5](safe-docs.md).

I PowerShell skal du bruge [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Slå Defender for Office 365 til for SharePoint, OneDrive og Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|Ud <br/><br/> `$false`|På <br/><br/> `$true`|Hvis du vil forhindre brugere i at downloade skadelige filer, skal du se [Brug SharePoint Online PowerShell til at forhindre brugere i at downloade skadelige filer](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Slå Pengeskab dokumenter til for Office klienter** <br/><br/> _EnableSafeDocs_|Ud <br/><br/> `$false`|På <br/><br/> `$true`|Denne funktion er kun tilgængelig og meningsfuld med licenser, der ikke er inkluderet i Defender for Office 365 (f.eks. Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed). Du kan få flere oplysninger [under Pengeskab dokumenter i Microsoft 365 E5](safe-docs.md).|
|**Tillad, at andre klikker gennem beskyttet visning, selvom Pengeskab dokumenter har identificeret filen som skadelig** <br/><br/> _AllowSafeDocsOpen_|Ud <br/><br/> `$false`|Ud <br/><br/> `$false`|Denne indstilling er relateret til Pengeskab dokumenter.|

#### <a name="safe-attachments-policy-settings"></a>politikindstillinger for Pengeskab vedhæftede filer

Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer politikker for vedhæftede filer Pengeskab i Defender for Office 365](set-up-safe-attachments-policies.md).

I PowerShell skal du bruge cmdlet'erne [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) og [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik for Pengeskab Vedhæftede filer, men Pengeskab Beskyttelse af vedhæftede filer tildeles til alle modtagere af den [forudindstillede sikkerhedspolitik **for indbygget beskyttelse**](preset-security-policies.md).
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i nye Pengeskab politikker for vedhæftede filer, som du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**Pengeskab vedhæftede filer ukendt malware-svar** <br/><br/> _Aktivér_ og _handling_|**Ud** <br/><br/> `-Enable $false` Og `-Action Block`|**Bloker** <br/><br/> `-Enable $true` Og `-Action Block`|**Bloker** <br/><br/> `-Enable $true` Og `-Action Block`|**Bloker** <br/><br/> `-Enable $true` Og `-Action Block`|Når parameteren _Enable_ er $false, betyder værdien af parameteren _Action_ ikke noget.|
|**Karantænepolitik** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny politik for vedhæftede filer Pengeskab, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske funktioner for meddelelser, der er sat i karantæne af Pengeskab Attachments (AdminOnlyAccessPolicy). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugerne. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).|
|**Omdiriger vedhæftet fil med registrerede vedhæftede filer** : **Aktivér omdirigering** <br/><br/> _Omdirigere_ <br/><br/> _RedirectAddress_|Ikke valgt, og der er ikke angivet nogen mailadresse. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ er tom (`$null`)|Ikke valgt, og der er ikke angivet nogen mailadresse. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ er tom (`$null`)|Valgt, og angiv en mailadresse. <br/><br/> `$true` <br/><br/> en mailadresse|Valgt, og angiv en mailadresse. <br/><br/> `$true` <br/><br/> en mailadresse|Omdiriger meddelelser til en sikkerhedsadministrator til gennemsyn. <br/><br/> **Bemærk**! Denne indstilling er ikke konfigureret i de forudindstillede sikkerhedspolitikker **Standard**, **Strict** eller **Indbygget beskyttelse** . Værdierne **Standard** og **Strict** angiver vores **anbefalede** værdier i nye Pengeskab politikker for vedhæftede filer, som du opretter.|
|**Anvend registreringssvar for Pengeskab vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout eller fejl)** <br/><br/> _ActionOnError_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||

### <a name="safe-links-settings"></a>indstillinger for Pengeskab links

Pengeskab Links i Defender for Office 365 indeholder globale indstillinger, der gælder for alle brugere, der er inkluderet i aktive Pengeskab linkspolitikker, og indstillinger, der er specifikke for hver Pengeskab Links-politik. Du kan få flere oplysninger [under Pengeskab Links i Defender for Office 365](safe-links.md).

Selvom der ikke er nogen standardpolitik for Pengeskab links, giver den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** Pengeskab Links-beskyttelse til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Links-politikker). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Globale indstillinger for Pengeskab links

> [!NOTE]
> De globale indstillinger for Pengeskab Links angives af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse**, men ikke af **standard**- eller **strenge** forudindstillede sikkerhedspolitikker. Uanset hvad kan administratorer når som helst ændre disse globale indstillinger for Pengeskab links.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den forudindstillede sikkerhedspolitik indbygget **beskyttelse** . Kolonnen **Indbygget beskyttelse** viser de værdier, der er angivet af den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** , som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer globale indstillinger for Pengeskab Links i Defender for Office 365](configure-global-settings-for-safe-links.md).

I PowerShell skal du bruge [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Bloker følgende URL-adresser** <br/><br/> _ExcludedUrls_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Du kan få flere oplysninger på [listen "Bloker følgende URL-adresser" for Pengeskab Links](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Brug Pengeskab links i Office 365 apps** <br/><br/> _EnableSafeLinksForO365Clients_|På <br/><br/> `$true`|På <br/><br/> `$true`|Brug Pengeskab Links i understøttede Office 365 skrivebords- og mobilapps (iOS og Android). Du kan få flere oplysninger [under Pengeskab Indstillinger for links til Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Spor ikke, hvornår brugere klikker på beskyttede links i Office 365 apps** <br/><br/> _TrackClicks_|På <br/><br/> `$false`|Ud <br/><br/> `$true`|Hvis du deaktiverer denne indstilling (indstilling _af TrackClicks_ til `$true`), spores brugerklik i understøttede Office 365 apps.|
|**Lad ikke brugere klikke sig igennem til den oprindelige URL-adresse i Office 365 apps** <br/><br/> _AllowClickThrough_|På <br/><br/> `$false`|På <br/><br/> `$false`|Hvis du aktiverer denne indstilling (indstilling _AllowClickThrough_ til ), forhindres det, at `$false`der klikkes videre til den oprindelige URL-adresse i understøttede Office 365 apps.|

#### <a name="safe-links-policy-settings"></a>politikindstillinger for Pengeskab links

Hvis du vil konfigurere disse indstillinger, skal du se [Konfigurer politikker for Pengeskab links i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

I PowerShell skal du bruge cmdlet'erne [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) og [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik for Pengeskab links, men Pengeskab Links-beskyttelse tildeles til alle modtagere af den [forudindstillede sikkerhedspolitik **for indbygget beskyttelse**](preset-security-policies.md).
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i nye Pengeskab Links-politikker, som du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Strenge|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**URL-adresse & klik på beskyttelsesindstillinger**||||||
|**Handling på potentielt skadelige URL-adresser i mails**||||||
|**På: Pengeskab Links kontrollerer en liste over kendte, ondsindede links, når brugerne klikker på links i mail** <br/><br/> _EnableSafeLinksForEmail_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Anvend Pengeskab links til mails, der er sendt i organisationen** <br/><br/> _EnableForInternalSenders_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer** <br/><br/> _ScanUrls_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Vent på, at scanningen af URL-adressen fuldføres, før meddelelsen leveres** <br/><br/> _DeliverMessageAfterScan_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Undlad at omskrive URL-adresser. Kontroller kun via API'en Pengeskab Links** <br/><br/> _DisableURLRewrite_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Omskriv ikke følgende URL-adresser i mail** <br/><br/> _DoNotRewriteUrls_|Ikke markeret <br/><br/> Tom|Ikke markeret <br/><br/> Tom|Ikke markeret <br/><br/> Tom|Ikke markeret <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan få flere oplysninger på [listerne "Omskriv ikke følgende URL-adresser" i politikker for Pengeskab links](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**Handling for potentielt skadelige URL-adresser i Microsoft Teams**||||||
|**On: Pengeskab Links kontrollerer en liste over kendte, ondsindede links, når brugerne klikker på links i Microsoft Teams** <br/><br/> _EnableSafeLinksForTeams_|Ikke markeret <br/><br/> `$false`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Klik på beskyttelsesindstillinger**||||||
|**Spor bruger klik** <br/><br/> _TrackUserClicks_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`||
|**Lad brugerne klikke sig videre til den oprindelige URL-adresse** <br/><br/> _AllowClickThrough_|Valgte <br/><br/> `$true`|Valgte <br/><br/> `$true`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Hvis du slår denne indstilling fra (indstilling _AllowClickThrough_ til ), forhindres det, at `$false`der klikkes videre til den oprindelige URL-adresse.|
|**Vis organisationsbranding på meddelelses- og advarselssider** <br/><br/> _EnableOrganizationBranding_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Før du aktiverer denne indstilling, skal du følge vejledningen i [Tilpas Microsoft 365 tema for din organisation for](../../admin/setup/customize-your-organization-theme.md) at uploade dit firmalogo.|
|**Anmeldelse**||||||
|**Hvordan vil du give brugerne besked?**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Du kan vælge **Brug brugerdefineret meddelelsestekst** (_CustomNotificationText_) for at angive brugerdefineret meddelelsestekst, der skal bruges. Du kan også vælge **Brug Microsoft Oversætter til automatisk lokalisering** (_UseTranslatedNotificationText_) for at oversætte den brugerdefinerede meddelelsestekst til brugerens sprog.

## <a name="related-articles"></a>Relaterede artikler

- Leder du efter bedste praksis for **Exchange regler for mailflow (også kaldet transportregler**)? Se [Bedste fremgangsmåder til konfiguration af regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorer og brugere kan sende falske positiver (god mail markeret som dårlig) og falske negativer (dårlig mail er tilladt) til Microsoft til analyse. Du kan få flere oplysninger under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

- Brug disse links til at få oplysninger om, hvordan du **konfigurerer** din [EOP-tjeneste](/exchange/standalone-eop/set-up-your-eop-service) og **konfigurerer** [Microsoft Defender for Office 365](defender-for-office-365.md). Glem ikke de nyttige retninger i "[Beskyt mod trusler i Office 365](protect-against-threats.md)".

- Du kan finde **grundlæggende sikkerhedsindstillinger for Windows** her: [Hvor kan jeg få de grundlæggende sikkerhedsindstillinger?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) for indstillinger for gruppepolitikobjekt/i det lokale miljø og [Brug grundlæggende sikkerhedsindstillinger til at konfigurere Windows enheder i Intune](/intune/protect/security-baselines) til Intune-baseret sikkerhed. Endelig kan du sammenligne Microsoft Defender for Endpoint og Microsoft Intune grundlæggende sikkerhedslinjer i [Sammenlign Microsoft Defender for Endpoint og Windows Intune sikkerhed oprindelige planer](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
