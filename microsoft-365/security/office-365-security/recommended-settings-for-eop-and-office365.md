---
title: Microsoft-anbefalinger til EOP og Defender for Office 365 til sikkerhedsindstillinger
keywords: Office 365 anbefalinger om sikkerhed, Framework for afsenderpolitik, domænebaseret rapportering af meddelelser og overholdelse, DomainKeys Identified Mail, trin, hvordan fungerer det, sikkerheds oprindelige planer, oprindelige planer for EOP, oprindelige planer for Defender for Office 365, konfigurer Defender for Office 365 , konfigurer EOP, konfigurer Defender for Office 365, konfigurer EOP, sikkerhedskonfiguration
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
description: Hvad er bedste fremgangsmåder for Exchange Online Protection (EOP) og Defender for Office 365 sikkerhedsindstillinger? Hvad er de aktuelle anbefalinger til standardbeskyttelse? Hvad skal du bruge, hvis du vil være mere restriktiv? Og hvad ekstra får du, hvis du også bruger Defender for Office 365?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b4b6c9df3b8c458aaf548ff9c8cfe8cc51fa5824
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507163"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** er kernen i sikkerheden for Microsoft 365-abonnementer og hjælper med at forhindre ondsindede mails i at nå dine medarbejderes indbakker. Men med nye og mere avancerede angreb, der hver dag kommer frem, er der ofte behov for forbedret beskyttelse. **Microsoft Defender for Office 365** plan 1 eller Plan 2 indeholder yderligere funktioner, der giver administratorer flere lag af sikkerhed, kontrol og undersøgelse.

Selvom vi giver sikkerhedsadministratorer mulighed for at tilpasse deres sikkerhedsindstillinger, er der to sikkerhedsniveauer i EOP og Microsoft Defender for Office 365, som vi anbefaler: **Standard** og **Streng**. Selvom kundemiljøer og behov er forskellige, hjælper disse filtreringsniveauer med at forhindre uønskede mails i at nå dine medarbejderes indbakke i de fleste situationer.

Hvis du automatisk vil anvende standardindstillingerne eller faste indstillinger for brugere, skal du [se Forudindstillede sikkerhedspolitikker i EOP Microsoft Defender for Office 365](preset-security-policies.md).

I denne artikel beskrives standardindstillingerne og også de anbefalede Standard- og Restriktive indstillinger for at beskytte dine brugere. Tabellerne indeholder indstillingerne i Microsoft 365 Defender-portalen og PowerShell (Exchange Online PowerShell eller enkeltstående Exchange Online Protection PowerShell for organisationer uden Exchange Online postkasser).

> [!TIP]
> Du kan ikke ændre de anbefalede standard- og restriktive indstillinger i Microsoft 365 Defender portal. Hvis du vil ændre anbefalede værdier som **f.eks. Aktivér** brugere at beskytte, skal [du Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
>
> I Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) til PowerShell kan det hjælpe dig (administratorer) med at finde de aktuelle værdier af disse indstillinger. Specifikt genererer **Get-ORCAReport-cmdlet'en** en vurdering af antispam, antiphishing og andre indstillinger for meddelelser. Du kan downloade ORCA-modulet på <https://www.powershellgallery.com/packages/ORCA/>.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Beskyttelse mod spam, antimalware og antiphishing i EOP

Antispam, antimalware og antiphishing er EOP-funktioner, der kan konfigureres af administratorer. Vi anbefaler følgende Standard- eller Streng-konfigurationer.

### <a name="eop-anti-spam-policy-settings"></a>Indstillinger for EOP-antispampolitik

Hvis du vil oprette og konfigurere antispam-politikker, skal [du se Konfigurer politikker for uønsket post i EOP](configure-your-spam-filter-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for massemail & egenskaber for uønsket post**|||||
|**Grænseværdi for massemail** <br/><br/> _BulkThreshold_|7|6|4|Du kan få mere at [vide under Masser af klageniveau (BCL) i EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Denne indstilling er kun tilgængelig i PowerShell.|
|**Forøg indstillinger for spamscore**|Fra|Fra|Fra|Alle disse indstillinger er en del af ASF(Advanced Spam Filter). Du kan finde flere oplysninger i [afsnittet ASF-indstillinger i antispampolitikker](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Markér som spamindstillinger**|Fra|Fra|Fra|De fleste af disse indstillinger er en del af ASF. Du kan finde flere oplysninger i [afsnittet ASF-indstillinger i antispampolitikker](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Indeholder bestemte sprog** <br/><br/> _EnableLanguageBlockList_ <br/><br/> _LanguageBlockList_|**Fra** <br/><br/> `$false` <br/><br/> Tom|**Fra** <br/><br/> `$false` <br/><br/> Tom|**Fra** <br/><br/> `$false` <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser på bestemte sprog ud fra virksomhedens behov.|
|**Fra disse lande** <br/><br/> _EnableRegionBlockList_ <br/><br/> _RegionBlockList_|**Fra** <br/><br/> `$false` <br/><br/> Tom|**Fra** <br/><br/> `$false` <br/><br/> Tom|**Fra** <br/><br/> `$false` <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser fra bestemte lande baseret på virksomhedens behov.|
|**Testtilstand** (_TestModeAction_)|**Ingen**|**Ingen**|**Ingen**|Denne indstilling er en del af ASF. Du kan finde flere oplysninger i [afsnittet ASF-indstillinger i antispampolitikker](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Handlinger**||||Uanset hvor du vælger **karantænemeddelelse**, vil **et felt afkrydsningsfeltet Vælg** karantæne være tilgængeligt. Karantænepolitikker definerer, hvad brugere har tilladelse til at gøre for meddelelser, der er sat i karantæne. <br/><br/> Når du opretter en ny antispampolitik, betyder en tom værdi standardkarantænepolitikken, der bruges til at definere de historiske egenskaber for meddelelser, der var i karantæne efter denne bestemte konklusion (AdminOnlyAccessPolicy for **Phishing med** høj tillid; DefaultFullAccessPolicy til alt andet). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Handling til** registrering af spam <br/><br/> _SpamAction_|**Flyt meddelelsen til mappen uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelsen til mappen uønsket mail** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Handling til registrering af spam** med høj genkendelse af tillid <br/><br/> _HighConfidenceSpamAction_|**Karantænemeddelelse** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Handling til** registrering af phishing <br/><br/> _PhishSpamAction_|**Karantænemeddelelse** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Handlingen Registrering af phishing med** høj tillid <br/><br/> _HighConfidencePhishAction_|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Masseregistreringshandling** <br/><br/> _BulkSpamAction_|**Flyt meddelelsen til mappen uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelsen til mappen uønsket mail** <br/><br/> `MoveToJmf`|**Karantænemeddelelse** <br/><br/> `Quarantine`||
|**Behold spam i karantæne i dette antal dage** <br/><br/> _KarantæneRetentionPeriod_|15 dage<sup>\*</sup>|30 dage|30 dage|<sup>\*</sup> Standardværdien er 15 dage i standardpolitikken for uønsket post og i nye politikker for uønsket post, som du opretter i PowerShell. Standardværdien er 30 dage i nye antispampolitikker, som du opretter i Microsoft 365 Defender-portalen. <br/><br/> Denne værdi påvirker også meddelelser, der er sat i karantæne af antiphishing-politikker. Du kan få mere at vide [under Meddelelser, der er sat i karantæne i EOP](quarantine-email-messages.md).|
|**Aktivér tip til spamsikkerhed** <br/><br/> _InlineSafetyTipsEnabled_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|Aktivere automatisk tømning (ZAP) uden time for phishingmeddelelser <br/><br/> _PhishZapEnabled_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|Aktivere ZAP for spammeddelelser <br/><br/> _SpamZapEnabled_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Tillad & blokliste**|||||
|Tilladte afsendere <br/><br/> _AllowedSenders_|Ingen|Ingen|Ingen||
|Tilladte afsenderdomæner <br/><br/> _AllowedSenderDomains_|Ingen|Ingen|Ingen|Det er en meget dårlig ide at føje domæner til listen over tilladte afsendere. Hackere vil kunne sende dig mails, som ellers ville blive frafiltreret. <br/><br/> Brug efterlignet intelligensindsigt og lejerens tilladelses[-/](tenant-allow-block-list.md)blokeringsliste til at gennemse alle afsendere, der efterligner afsendermailadresser i din organisations maildomæner eller efterligner afsendermailadresser i eksterne domæner.[](learn-about-spoof-intelligence.md)|
|Blokerede afsendere <br/><br/> _BlockedSenders_|Ingen|Ingen|Ingen||
|Blokerede afsenderdomæner <br/><br/> _BlockedSenderDomains_|Ingen|Ingen|Ingen||

#### <a name="asf-settings-in-anti-spam-policies"></a>ASF-indstillinger i politikker for uønsket post

Tabellen i dette afsnit beskriver de avancerede asf-indstillinger for spamfilter, der er tilgængelige i antispampolitikker. Alle disse indstillinger er slået **Fra** for både **Standard** og **Strenge** niveauer. Du kan finde flere oplysninger om ASF-indstillinger [under Avancerede indstillinger for spamfilter (ASF) i EOP](advanced-spam-filtering-asf-options.md).

|Navn på sikkerhedsfunktion|Kommenter|
|---|---|
|**Billedlinks til eksterne** websteder (_IncreaseScoreWithImageLinks_)||
|**Numerisk IP-adresse i URL** (_IncreaseScoreWithNumericIps_)||
|**URL redirect to other port** (_IncreaseScoreWithRedirectToOtherPort_)||
|**Links til .biz- eller .info-websteder** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Tomme meddelelser** (_MarkAsSpamEmptyMessages_)||
|**Integrer koder i HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript eller VBScript i HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Formularmærker i HTML** (_MarkAsSpamFormTagsInHtml_)||
|**Ramme- eller iframe-koder i HTML** (_MarkAsSpamFramesInHtml_)||
|**Webfejl i HTML** (_MarkAsSpamWebBugsInHtml_)||
|**Objektmærker i HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**Følsomme ord** (_MarkAsSpamSensitiveWordList_)||
|**SPF-post: hard fail** (_MarkAsSpamSpfRecordHardFail_)||
|**Filtrering af afsender-id mislykkes** (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**Testtilstand** (_TestModeAction_)|For ASF-indstillinger, der understøtter **Test** som en handling, kan du konfigurere handlingen for testtilstand til **Ingen**, Tilføj standardtekst i X-brevhoved eller **Send Bcc-meddelelse** (`None`, `AddXHeader`eller ). `BccMessage` Få mere at vide under [Aktivér, deaktiver eller test ASF-indstillinger](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Indstillinger for EOP-politik for udgående spam

Hvis du vil oprette og konfigurere politikker for udgående spam, skal [du se Konfigurere filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md).

Du kan finde flere oplysninger om standardgrænserne for afsendelse i tjenesten under [Grænser for afsendelse](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Politikker for udgående spam er ikke en del af Standard eller Faste forudindstillede sikkerhedspolitikker. Standard **-** og **Strict-værdierne** angiver vores anbefalede **værdier i** standardpolitikken for udgående spam eller brugerdefinerede politikker, du opretter.

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Angiv en ekstern meddelelsesgrænse** <br/><br/> _RecipientLimitExternalPerHour_|0|500|400|Standardværdien 0 betyder, at du bruger tjenestens standardindstillinger.|
|**Angiv en intern meddelelsesgrænse** <br/><br/> _RecipientLimitInternalPerHour_|0|1000|800|Standardværdien 0 betyder, at du bruger tjenestens standardindstillinger.|
|**Angiv en daglig meddelelsesgrænse** <br/><br/> _RecipientLimitPerDay_|0|1000|800|Standardværdien 0 betyder, at du bruger tjenestens standardindstillinger.|
|**Begrænsning for brugere, der når meddelelsesgrænsen** <br/><br/> _ActionWhenThresholdReached_|**Begrænse brugerens mulighed for at sende mail til den følgende dag** <br/><br/> `BlockUserForToday`|**Begræns brugerens mulighed for at sende mail** <br/><br/> `BlockUser`|**Begræns brugerens mulighed for at sende mail** <br/><br/> `BlockUser`||
|**Regler for automatisk videresendelse** <br/><br/> _AutoForwardingMode_|**Automatisk – systemkontrolleret** <br/><br/> `Automatic`|**Automatisk – systemkontrolleret** <br/><br/> `Automatic`|**Automatisk – systemkontrolleret** <br/><br/> `Automatic`|
|**Sende en kopi af udgående meddelelser, der overskrider disse begrænsninger for disse brugere og grupper** <br/><br/> _BccSuspiciousOutboundMail_ <br/><br/> _BccSuspiciousOutboundAdditionalRecipients_|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Denne indstilling fungerer kun i standardpolitikken for udgående spam. Det fungerer ikke i brugerdefinerede politikker for udgående spam, som du opretter.|
|**Giv disse brugere og grupper besked, hvis en afsender blokeres på grund af afsendelse af udgående spam** <br/><br/> _NotifyOutboundSpam_ <br/><br/> _NotifyOutboundSpamRecipients_|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Ikke markeret <br/><br/> `$false` <br/><br/> Tom|Standardpolitikken [for påmindelse](../../compliance/alert-policies.md),  der hedder Bruger er begrænset til at sende mail, sender allerede mailbeskeder til medlemmer af **gruppen TenantAdmins** (globale administratorer), når brugere **blokeres** pga. overskrider begrænsningerne i politikken. **Vi anbefaler på det kraftigste, at du bruger** påmindelsespolitikken i stedet for denne indstilling i politikken for udgående spam til at underrette administratorer og andre brugere. Du kan finde en vejledning [i Bekræfte indstillingerne for påmindelse for brugere med begrænset adgang](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Politikindstillinger for EOP-antimalware

Hvis du vil oprette og konfigurere antimalwarepolitikker, skal [du se Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Beskyttelsesindstillinger**|||||
|**Aktivere filteret for almindelige vedhæftede filer** <br/><br/> _EnableFileFilter_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Denne indstilling sætter meddelelser i karantæne, der indeholder eksekverbare vedhæftede filer baseret på filtype, uanset det vedhæftede indhold.|
|**Aktivér automatisk tømning uden time for malware** <br/><br/> _ZapEnabled_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Karantænepolitik**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny antimalwarepolitik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske egenskaber for meddelelser, der var sat i karantæne, som malware (AdminOnlyAccessPolicy). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugere. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Modtagerbeskeder**|||||
|**Giv modtagerne besked, når meddelelser er i karantæne som malware** <br/><br/> _Handling_|Ikke markeret <br/><br/> _DeleteMessage_|Ikke markeret <br/><br/> _DeleteMessage_|Ikke markeret <br/><br/> _DeleteMessage_|Hvis der registreres malware i en vedhæftet fil i en mail, er meddelelsen i karantæne og kan kun frigives af en administrator.|
|**Afsenderbeskeder**|||||
|**In oplyse interne afsendere, når meddelelser er i karantæne som malware** <br/><br/> _EnableInternalSenderNotifications_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Underret eksterne afsendere, når meddelelser er i karantæne som malware** <br/><br/> _EnableExternalSenderNotifications_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Administratormeddelelser**|||||
|**Giv en administrator besked om meddelelser, der ikke blev leveret fra interne afsendere** <br/><br/> _EnableInternalSenderAdminNotifications_ <br/><br/> _InternalSenderAdminAddress_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Giv en administrator besked om meddelelser, der ikke blev leveret fra eksterne afsendere** <br/><br/> _EnableExternalSenderAdminNotifications_ <br/><br/> _ExternalSenderAdminAddress_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Tilpas meddelelser**||||Vi har ingen specifikke anbefalinger til disse indstillinger.|
|**Brug tilpasset meddelelsestekst** <br/><br/> _CustomNotifications_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Fra navn** <br/><br/> _CustomFromName_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Fra adresse** <br/><br/> _CustomFromAddress_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Tilpasse meddelelser til meddelelser fra interne afsendere**||||Disse indstillinger bruges kun, hvis **Giv** interne afsendere besked, når meddelelser er i karantæne som malware eller Giv besked til en administrator om ikke-leveret meddelelser fra interne afsendere **er markeret** .|
|**Emne** <br/><br/> _CustomInternalSubject_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Meddelelse** <br/><br/> _CustomInternalPatiy_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Tilpasse meddelelser for meddelelser fra eksterne afsendere**||||Disse indstillinger bruges kun, hvis **Giv** eksterne afsendere besked, når meddelelser er i karantæne som malware, eller Giv besked til en administrator om ikke-leveret meddelelser fra eksterne afsendere **er markeret** .|
|**Emne** <br/><br/> _CustomExternalSubject_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||
|**Meddelelse** <br/><br/> _CustomExternalTilpasset_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Politikindstillinger for EOP-antiphishing

Du kan finde flere oplysninger om disse indstillinger [under Spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings). Se Konfigurer [antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md) for at konfigurere disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishing & beskyttelse**|||||
|**Aktivér efterlignet intelligens** <br/><br/> _EnableSpoofIntelligence_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som efterlignet** <br/><br/> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`|Denne indstilling gælder for efterlignede afsendere, der blev blokeret automatisk, sådan som det er vist i [efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt eller manuelt blokeret på lejerens tilladelses [-/blokeringsliste](tenant-allow-block-list.md). <br/><br/> Hvis du vælger Karantæne **for** meddelelsen, er  der et politikfelt Anvend karantæne tilgængeligt, hvor du kan vælge den karantænepolitik, der definerer, hvad brugere har tilladelse til at gøre på meddelelser, der er i karantæne som spoofing. Når du opretter en ny antiphishing-politik, betyder en tom værdi, at standardpolitikken for karantæne bruges til at definere de historiske egenskaber for meddelelser, der var i karantæne, som spoofing (DefaultFullAccessPolicy). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Vis første sikkerhedstip** <br/><br/> _EnableFirstContactSafetyTips_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Du kan få mere at vide [under Første sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Show (?) for ikke-godkendte afsendere for spoof** <br/><br/> _EnableUnauthenticatedSender_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Føjer et spørgsmålstegn (?) til afsenderens billede i Outlook for uidentificeret spoof afsendere. Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Vis mærket "via"** <br/><br/> _EnableViaTag_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Føjer et via-mærke (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis det er forskelligt fra domænet i DKIM-signaturen eller **MAIL FRA-adressen** . <br/><br/> Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender for Office 365 sikkerhed

Der med sig yderligere sikkerhedsfordele Microsoft Defender for Office 365 abonnementet. Du kan finde de seneste nyheder og oplysninger [under Nyheder i Defender for Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Standardpolitikken for phishing i Microsoft Defender for Office 365 [spoof-beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) og postkasseintelligens til alle modtagere. Men de andre tilgængelige funktioner [til repræsentationsbeskyttelse](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og [avancerede indstillinger](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) er ikke konfigureret eller aktiveret i standardpolitikken. Hvis du vil aktivere alle beskyttelsesfunktioner, skal du ændre standardpolitikken for phishing eller oprette flere antiphishing-politikker.
>
> - Selvom der ikke er nogen standardpolitik Pengeskab Vedhæftede filer eller Pengeskab Links-politik, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab beskyttelse af vedhæftede filer og Pengeskab **Links-beskyttelse** til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Politikker for vedhæftede filer eller Pengeskab  Politikker for links). Få mere at vide under [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).
>
> - [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md) og Pengeskab-dokumentbeskyttelse er ikke afhængige af Pengeskab politikker for links[](safe-docs.md).

Hvis dit abonnement Microsoft Defender for Office 365, eller hvis du har købt Defender for Office 365 som et tilføjelsesprogrammet, skal du angive følgende Standard- eller Restriktive konfigurationer.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Politikindstillinger for phishing i Microsoft Defender for Office 365

EOP-kunder får grundlæggende antiphishing som beskrevet tidligere, men Defender for Office 365 indeholder flere funktioner og kontrol, der kan hjælpe med at forhindre, registrere og afhjælpe mod angreb. Hvis du vil oprette og konfigurere disse politikker, [skal du se Konfigurer antiphishing-politikker Defender for Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Avancerede indstillinger i antiphishing-politikker i Microsoft Defender for Office 365

Du kan få mere at vide om denne [indstilling under Avancerede grænseværdier for phishing i antiphishing-politikker Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere denne indstilling, [skal du se Konfigurer antiphishing-politikker Defender for Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishingmail** <br/><br/> _PhishThresholdLevel_|**1 – Standard** <br/><br/> `1`|**2 – Aggressive** <br/><br/> `2`|**3 – mere aggressive** <br/><br/> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Indstillinger for repræsentation i antiphishing-politikker i Microsoft Defender for Office 365

Du kan finde flere oplysninger om disse indstillinger [under Indstillinger for repræsentation i antiphishing-politikker Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer antiphishing-politikker Defender for Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishing & beskyttelse**|||||
|**Gøre det muligt for brugerne** at beskytte (efterligning af brugerbeskyttelse) <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|Ikke markeret <br/><br/> `$false` <br/><br/> ingen|Markeret <br/><br/> `$true` <br/><br/> \<list of users\>|Markeret <br/><br/> `$true` <br/><br/> \<list of users\>|Vi anbefaler, at du tilføjer brugere (meddelelsesafsendere) i vigtige roller. Internt kan beskyttede afsendere være din administrerende direktør, CFO og andre seniorledere. Eksternt kan beskyttede afsendere omfatte rådmedlemmer eller din bestyrelse. <br/><br/> I forudindstillede sikkerhedspolitikker kan du ikke angive, hvilke brugere der skal beskyttes. Du skal deaktivere de foruddefinerede sikkerhedspolitikker og bruge brugerdefinerede antiphishing-politikker til at tilføje brugere i nøgleroller, som foreslået.|
|**Aktivér domæner for at beskytte** (efterligning af domænebeskyttelse)|Ikke markeret|Markeret|Markeret||
|**Medtag domæner, jeg ejer** <br/><br/> _EnableOrganizationDomainsProtection_|Fra <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Medtag brugerdefinerede domæner** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|Fra <br/><br/> `$false` <br/><br/> ingen|Markeret <br/><br/> `$true` <br/><br/> \<list of domains\>|Markeret <br/><br/> `$true` <br/><br/> \<list of domains\>|Vi anbefaler, at du tilføjer domæner (afsenderdomæner), som du ikke ejer, men du ofte interagerer med. <br/><br/> I foruddefinerede sikkerhedspolitikker kan du ikke angive de brugerdefinerede domæner, der skal beskyttes. Du skal deaktivere de foruddefinerede sikkerhedspolitikker og bruge brugerdefinerede antiphishing-politikker for at tilføje brugerdefinerede domæner, der skal beskyttes, som foreslået.|
|**Tilføj afsendere og domæner, der er tillid til** <br/><br/> _ExcludedSenders_ <br/><br/> _ExcludedDomains_|Ingen|Ingen|Ingen|Afhængigt af din organisation anbefaler vi, at du tilføjer afsendere eller domæner, der fejlagtigt er identificeret som forsøg på efterligning.|
|**Aktivér postkasseintelligens** <br/><br/> _EnableMailboxIntelligence_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Aktivere intelligens til repræsentationsbeskyttelse** <br/><br/> _EnableMailboxIntelligenceProtection_|Fra <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Denne indstilling tillader den angivne handling til repræsentationsregistreringer ved hjælp af postkasseintelligens.|
|**Handlinger**||||Uanset hvor du vælger **Karantæne i meddelelsen**, vil et **af politikfeltet Vælg** karantæne være tilgængeligt. Karantænepolitikker definerer, hvad brugere har tilladelse til at gøre for meddelelser, der er sat i karantæne. <br/><br/> Når du opretter en ny antiphishing-politik, betyder en tom værdi, at standardpolitikken for karantæne bruges til at definere de historiske egenskaber for meddelelser, der er sat i karantæne efter denne vurdering (DefaultFullAccessPolicy for alle registreringstyper for efterligninger). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Hvis meddelelsen registreres som en efterligning af en bruger** <br/><br/> _TargetedUserProtectionAction_|**Anvend ikke nogen handling** <br/><br/> `NoAction`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`|Husk, at forudindstillede sikkerhedspolitikker ikke tillader dig at angive, hvilke brugere der skal beskyttes, så denne indstilling gør effektivt intet i forudindstillede sikkerhedspolitikker.|
|**Hvis meddelelsen registreres som et efterligning af domæne** <br/><br/> _TargetedDomainProtectionAction_|**Anvend ikke nogen handling** <br/><br/> `NoAction`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`|Husk, at forudindstillede sikkerhedspolitikker ikke tillader dig at angive de brugerdefinerede domæner, der skal beskyttes, så denne indstilling påvirker kun domæner, som du ejer, ikke brugerdefinerede domæner.|
|**Hvis postkasseintelligens registrerer og efterligner bruger** <br/><br/> _MailboxIntelligenceProtectionAction_|**Anvend ikke nogen handling** <br/><br/> `NoAction`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`||
|**Vis sikkerhedstip** <br/><br/> _EnableSimilarUsersSafetyTips_|Fra <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Vis sikkerhedstip** <br/><br/> _EnableSimilarDomainsSafetyTips_|Fra <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Vis bruger efterligning af usædvanlige tegn sikkerhedstip** <br/><br/> _EnableUnusualCharactersSafetyTips_|Fra <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Politikindstillinger for EOP-antiphishing i Microsoft Defender for Office 365

Disse er de samme indstillinger, der er tilgængelige i [politikindstillinger for uønsket post i EOP](#eop-anti-spam-policy-settings).

Indstillingerne for spoof er indbyrdes forbundne, men indstillingen Vis første **kontakt sikkerhedstip** ikke afhængighed af spoof-indstillinger.

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishing & beskyttelse**|||||
|**Aktivér efterlignet intelligens** <br/><br/> _EnableSpoofIntelligence_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som efterlignet** <br/><br/> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <br/><br/> `MoveToJmf`|**Sætte meddelelsen i karantæne** <br/><br/> `Quarantine`|Denne indstilling gælder for efterlignede afsendere, der blev blokeret automatisk, sådan som det er vist i [efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt eller manuelt blokeret på lejerens tilladelses [-/blokeringsliste](tenant-allow-block-list.md). <br/><br/> Hvis du vælger **Karantæne for** meddelelsen, er  et anvend karantænepolitikfelt tilgængeligt for at vælge den karantænepolitik, der definerer, hvad brugerne har tilladelse til at gøre for meddelelser, der er sat i karantæne. Når du opretter en ny antiphishing-politik, betyder en tom værdi, at standardpolitikken for karantæne bruges til at definere de historiske egenskaber for spoof meddelelser, der er sat i karantæne (DefaultFullAccessPolicy). <br/><br/> Administratorer kan oprette og vælge en brugerdefineret karantænepolitik, der definerer, hvad modtagere har tilladelse til at gøre ved disse meddelelser i karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Vis første sikkerhedstip** <br/><br/> _EnableFirstContactSafetyTips_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Du kan få mere at vide [under Første sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Show (?) for ikke-godkendte afsendere for spoof** <br/><br/> _EnableUnauthenticatedSender_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Føjer et spørgsmålstegn (?) til afsenderens billede i Outlook for uidentificeret spoof afsendere. Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Vis mærket "via"** <br/><br/> _EnableViaTag_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Føjer et via-mærke (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis det er forskelligt fra domænet i DKIM-signaturen eller **MAIL FRA-adressen** . <br/><br/> Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|

### <a name="safe-attachments-settings"></a>Pengeskab indstillinger for vedhæftede filer

Pengeskab Vedhæftede filer i Microsoft Defender for Office 365 inkluderer globale indstillinger, der ikke har nogen relation til Pengeskab Politikker for vedhæftede filer og indstillinger, der er specifikke for hver Pengeskab Links-politik. Du kan finde flere oplysninger [under Pengeskab Vedhæftede filer i Defender for Office 365](safe-attachments.md).

Selvom der ikke er nogen standardpolitik Pengeskab Vedhæftede filer, giver den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Politikker for vedhæftede filer). Få mere at vide under [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Globale indstillinger for Pengeskab vedhæftede filer

> [!NOTE]
> De globale indstillinger for Pengeskab Vedhæftede filer er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, men ikke af **Standard** eller **Faste** forudindstillede sikkerhedspolitikker. Uanset hvad kan administratorer til enhver tid ændre disse globale Pengeskab indstillinger for vedhæftede filer.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den **indbyggede beskyttelse** foruddefinerede sikkerhedspolitik. Kolonnen **Indbyggede beskyttelse** viser de værdier, der er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, skal du se Pengeskab Vedhæftede [filer for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) og [Pengeskab Dokumenter i Microsoft 365 E5](safe-docs.md).

I PowerShell bruger du [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Slå Defender for Office 365 til for SharePoint, OneDrive og Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|Fra <br/><br/> `$false`|Til <br/><br/> `$true`|Hvis du vil forhindre brugere i at hente skadelige filer, [skal du se Brug SharePoint Online PowerShell til at forhindre brugere i at hente skadelige filer](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Slå Pengeskab Dokumenter til for Office klienter** <br/><br/> _EnableSafeDocs_|Fra <br/><br/> `$false`|Til <br/><br/> `$true`|Denne funktion er kun tilgængelig og giver mening med licenser, der ikke er inkluderet Defender for Office 365 (f.eks. Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed). Du kan finde flere oplysninger [Pengeskab Dokumenter i Microsoft 365 E5](safe-docs.md).|
|**Tillad brugere at klikke gennem Beskyttet visning, selvom Pengeskab dokumenter identificeret filen som skadelige** <br/><br/> _AllowSafeDocsOpen_|Fra <br/><br/> `$false`|Fra <br/><br/> `$false`|Denne indstilling er relateret til Pengeskab Dokumenter.|

#### <a name="safe-attachments-policy-settings"></a>Pengeskab indstillinger for politik for vedhæftede filer

Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurere Pengeskab Politikker for vedhæftede filer Defender for Office 365](set-up-safe-attachments-policies.md).

I PowerShell bruger du [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) - og [Set-SafeAttachmentPolicy-cmdlet'er](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik Pengeskab Vedhæftede filer, men Pengeskab Beskyttelse af vedhæftede filer tildeles til alle modtagere af den [**indbyggede**](preset-security-policies.md) beskyttelse foruddefinerede sikkerhedspolitik.
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i den nye Pengeskab politikker for vedhæftede filer, du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**Pengeskab ukendt malwaresvar ved vedhæftede filer** <br/><br/> _Aktivér_ og _handling_|**Fra** <br/><br/> `-Enable $false` og `-Action Block`|**Bloker** <br/><br/> `-Enable $true` og `-Action Block`|**Bloker** <br/><br/> `-Enable $true` og `-Action Block`|**Bloker** <br/><br/> `-Enable $true` og `-Action Block`|Når _parameteren_ Aktivér er $false, betyder værdien for handlingsparameteren ikke noget.|
|**Karantænepolitik** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny Pengeskab Politik for vedhæftede filer, betyder en tom værdi standardkarantænepolitikken, der bruges til at definere de historiske egenskaber for meddelelser, der var i karantæne af Pengeskab Vedhæftede filer (AdminOnlyAccessPolicy). <br/><br/> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugere. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Omdiriger vedhæftet fil med registrerede vedhæftede filer** : **Aktivér omdirigering** <br/><br/> _Omdiriger_ <br/><br/> _RedirectAddress_|Ikke markeret, og der er ikke angivet en mailadresse. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ er tom (`$null`)|Ikke markeret, og der er ikke angivet en mailadresse. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ er tom (`$null`)|Markeret, og angiv en mailadresse. <br/><br/> `$true` <br/><br/> en mailadresse|Markeret, og angiv en mailadresse. <br/><br/> `$true` <br/><br/> en mailadresse|Omdirigere meddelelser til en sikkerhedsadministrator til gennemsyn. <br/><br/> **Bemærk**! Denne indstilling er ikke konfigureret **i standard,** **streng eller** **indbyggede sikkerhedspolitikker.** Standard **-** og **Strict-værdierne** angiver vores **anbefalede værdier** i den nye Pengeskab vedhæftede filer-politikker, du opretter.|
|**Anvend søges Pengeskab registreringssvar for vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout eller fejl)** <br/><br/> _ActionOnError_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||

### <a name="safe-links-settings"></a>Pengeskab links

Pengeskab links i Defender for Office 365 omfatter globale indstillinger, der gælder for alle brugere, som er inkluderet i aktive Pengeskab-links-politikker, og indstillinger, der er specifikke for hver Pengeskab Links-politik. Du kan finde flere oplysninger [Pengeskab Links i Defender for Office 365](safe-links.md).

Selvom der ikke er nogen standardpolitik for Pengeskab Links, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab **Kæder-politikker**). Få mere at vide under [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Globale indstillinger for Pengeskab links

> [!NOTE]
> De globale indstillinger for Pengeskab links er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, men ikke af **Standard** eller **Faste forudindstillede** sikkerhedspolitikker. Uanset hvad kan administratorer ændre disse globale indstillinger Pengeskab links når som helst.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den **indbyggede beskyttelse** foruddefinerede sikkerhedspolitik. Kolonnen **Indbyggede beskyttelse** viser de værdier, der er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer globale indstillinger for Pengeskab Links i Defender for Office 365](configure-global-settings-for-safe-links.md).

I PowerShell bruger du [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Blokere følgende URL-adresser** <br/><br/> _ExcludedUrls_|Tom <br/><br/> `$null`|Tom <br/><br/> `$null`|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Du kan finde flere oplysninger [på listen "Bloker følgende URL-adresser" for Pengeskab Links](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Brug Pengeskab Links i Office 365 apps** <br/><br/> _EnableSafeLinksForO365Clients_|Til <br/><br/> `$true`|Til <br/><br/> `$true`|Brug Pengeskab Links i understøttede Office 365 og mobilapps (iOS og Android). Du kan finde flere oplysninger [Pengeskab Indstillinger for links til Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Registrer ikke, når brugere klikker på beskyttede links i Office 365 apps** <br/><br/> _TrackClicks_|Til <br/><br/> `$false`|Fra <br/><br/> `$true`|Hvis du deaktiverer denne indstilling (_indstilling af TrackClicks_ til `$true`), registreres brugerklik i understøttede Office 365 apps.|
|**Lad ikke brugere klikke igennem til den oprindelige URL-adresse i Office 365 apps** <br/><br/> _TilladKlikThrough_|Til <br/><br/> `$false`|Til <br/><br/> `$false`|Aktivering af denne indstilling (indstilling _af TilladKlikThrough_ til `$false`) forhindrer klik til den oprindelige URL-adresse i understøttede Office 365 apps.|

#### <a name="safe-links-policy-settings"></a>Pengeskab links til politikindstillinger

Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer Pengeskab Links-politikker i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

I PowerShell bruger du [cmdlet'erne New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) og [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik Pengeskab Links, men beskyttelse af Pengeskab Links tildeles til alle modtagere af den [**indbyggede**](preset-security-policies.md) beskyttelse foruddefinerede sikkerhedspolitik.
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i den nye Pengeskab Links-politikker, du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**Url-& på beskyttelsesindstillinger**||||||
|**Handling på potentielt skadelige URL-adresser i mails**||||||
|**Til: Pengeskab kontrollerer en liste over kendte, skadelige links, når brugere klikker på links i en mail** <br/><br/> _EnableSafeLinksForEmail_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Anvend Pengeskab links til mails, der er sendt i organisationen** <br/><br/> _EnableForInternalSenders_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Anvend URL-scanning i realtid for mistænkelige links og links, der peger på filer** <br/><br/> _ScanUrls_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Vent på, at URL-adressen scannes, før meddelelsen leveres** <br/><br/> _DeliverMessageAfterScan_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Undlad at omskrive URL-adresser, kontroller kun via Pengeskab Links API** <br/><br/> _DisableURLRewrite_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`||
|**Undlad at omskrive følgende URL-adresser i en mail** <br/><br/> _DoNotRewriteUrls_|Ikke markeret <br/><br/> tom|Ikke markeret <br/><br/> tom|Ikke markeret <br/><br/> tom|Ikke markeret <br/><br/> tom|Vi har ingen specifik anbefaling til denne indstilling. Få mere at vide under ["Omse ikke følgende URL-adresser"-lister i Pengeskab Links-politikker](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**Handling til potentielt skadelige URL-adresser i Microsoft Teams**||||||
|**Til: Pengeskab kontrollerer en liste over kendte, skadelige links, når brugere klikker på links Microsoft Teams** <br/><br/> _EnableSafeLinksForTeams_|Ikke markeret <br/><br/> `$false`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Klik på beskyttelsesindstillinger**||||||
|**Registrere brugerklik** <br/><br/> _TrackUserClicks_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`||
|**Lad brugere klikke igennem til den oprindelige URL-adresse** <br/><br/> _TilladKlikThrough_|Markeret <br/><br/> `$true`|Markeret <br/><br/> `$true`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Hvis du slår denne indstilling fra ( _indstilling TilladKlikThrough_ til `$false`), forhindres det, at du kan klikke dig igennem til den oprindelige URL-adresse.|
|**Vise organisationens branding på meddelelses- og advarselssider** <br/><br/> _EnableOrganizationBranding_|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Ikke markeret <br/><br/> `$false`|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Før du slår denne indstilling til, skal du følge vejledningen i Tilpas [Microsoft 365-temaet for din organisation for](../../admin/setup/customize-your-organization-theme.md) at overføre dit firmalogo.|
|**Meddelelse**||||||
|**Hvordan vil du give dine brugere besked?**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|Vi har ingen specifik anbefaling til denne indstilling. <br/><br/> Du kan vælge **Brug brugerdefineret meddelelsestekst** (_CustomNotificationText_) for at angive tilpasset meddelelsestekst, der skal bruges. Du kan også vælge **Brug Microsoft Oversætter til** automatisk lokalisering (_UseTranslatedNotificationText_) for at oversætte den brugerdefinerede meddelelsestekst til brugerens sprog.

## <a name="related-articles"></a>Relaterede artikler

- Leder du efter bedste fremgangsmåder til **Exchange regler for mailflow (også kaldet transportregler**)? Se [Bedste fremgangsmåder til konfiguration af regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorer og brugere kan sende falske positive (god mail markeret som dårlig) og falske negativer (ugyldig mail tilladt) til analyse hos Microsoft. Få mere at vide under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

- Brug disse links til at få oplysninger om **, hvordan du konfigurerer** [din EOP-tjeneste](/exchange/standalone-eop/set-up-your-eop-service) **og konfigurerer** [Microsoft Defender for Office 365](defender-for-office-365.md). Glem ikke de nyttige anvisninger i "[Beskyt mod trusler i Office 365](protect-against-threats.md)".

- Sikkerheds oprindelige planer **for Windows** kan findes her: Hvor kan jeg få de oprindelige planer for sikkerhed [?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) for gruppepolitikobjekt/lokalt miljø og Brug oprindelige planer for sikkerhed til at konfigurere [Windows-enheder i Intune](/intune/protect/security-baselines) til Intune-baseret sikkerhed. Til sidst kan du finde en Microsoft Defender for Endpoint og Microsoft Intune oprindelige planer i Sammenligning [af Microsoft Defender for Endpoint og Windows Intune sikkerhed oprindelige planer](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
