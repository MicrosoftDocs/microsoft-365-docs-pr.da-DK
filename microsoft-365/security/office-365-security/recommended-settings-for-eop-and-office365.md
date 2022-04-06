---
title: Microsoft-anbefalinger til EOP og Defender Office 365 sikkerhedsindstillinger
keywords: Office 365 sikkerhedsanbefalinger, Sender Policy Framework, Domain-based Message Reporting and Conformance, DomainKeys Identified Mail, trin, hvordan fungerer det, sikkerheds oprindelige planer, grundlinjer for EOP, grundlinjer for Defender til Office 365, konfigurer Defender til Office 365 , konfigurer EOP, konfigurer Defender til Office 365 , konfigurer EOP, sikkerhedskonfiguration
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
description: Hvad er bedste fremgangsmåder for Exchange Online Protection (EOP) og Defender til Office 365 for sikkerhed? Hvad er de aktuelle anbefalinger til standardbeskyttelse? Hvad skal du bruge, hvis du vil være mere restriktiv? Og hvad ekstra får du, hvis du også bruger Defender til Office 365?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 078fbe60b18c06b46c4da0935fce3c4ad867908b
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683707"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** er kernen i sikkerheden for Microsoft 365-abonnementer og hjælper med at forhindre ondsindede mails i at nå dine medarbejderes indbakker. Men med nye og mere avancerede angreb, der hver dag kommer frem, er der ofte behov for forbedret beskyttelse. **Microsoft Defender til Office 365** Plan 1 eller Plan 2 indeholder yderligere funktioner, der giver administratorer flere lag af sikkerhed, kontrol og undersøgelse.

Selvom vi giver sikkerhedsadministratorer mulighed for at tilpasse deres sikkerhedsindstillinger, er der to sikkerhedsniveauer i EOP og Microsoft Defender Office 365, som vi anbefaler: **Standard** og **Strict**. Selvom kundemiljøer og behov er forskellige, hjælper disse filtreringsniveauer med at forhindre uønskede mails i at nå dine medarbejderes indbakke i de fleste situationer.

Hvis du automatisk vil anvende standardindstillingerne eller faste indstillinger for brugere, skal du se Forudindstillede [sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md).

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
|**Grænseværdi for massemail** <p> _BulkThreshold_|7|6|4|Du kan få mere at [vide under Masser af klageniveau (BCL) i EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Denne indstilling er kun tilgængelig i PowerShell.|
|**Forøg indstillinger for spamscore**|Fra|Fra|Fra|Alle disse indstillinger er en del af ASF(Advanced Spam Filter). Du kan finde flere oplysninger i [afsnittet ASF-indstillinger i antispampolitikker](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Markér som spamindstillinger**|Fra|Fra|Fra|De fleste af disse indstillinger er en del af ASF. Du kan finde flere oplysninger i [afsnittet ASF-indstillinger i antispampolitikker](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Indeholder bestemte sprog** <p> _EnableLanguageBlockList_ <p> _LanguageBlockList_|**Fra** <p> `$false` <p> Tom|**Fra** <p> `$false` <p> Tom|**Fra** <p> `$false` <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser på bestemte sprog ud fra virksomhedens behov.|
|**Fra disse lande** <p> _EnableRegionBlockList_ <p> _RegionBlockList_|**Fra** <p> `$false` <p> Tom|**Fra** <p> `$false` <p> Tom|**Fra** <p> `$false` <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. Du kan blokere meddelelser fra bestemte lande baseret på virksomhedens behov.|
|**Testtilstand** (_TestModeAction_)|**Ingen**|**Ingen**|**Ingen**|Denne indstilling er en del af ASF. Du kan finde flere oplysninger i [afsnittet ASF-indstillinger i antispampolitikker](#asf-settings-in-anti-spam-policies) i denne artikel.|
|**Handlinger**||||Uanset hvor du vælger **karantænemeddelelse**, vil **et felt afkrydsningsfeltet Vælg** karantæne være tilgængeligt. Karantænepolitikker definerer, hvad brugere har tilladelse til at gøre for meddelelser, der er sat i karantæne. <p> Når du opretter en ny antispampolitik, betyder en tom værdi standardkarantænepolitikken, der bruges til at definere de historiske egenskaber for meddelelser, der var i karantæne efter denne bestemte konklusion (AdminOnlyAccessPolicy for **Phishing med** høj tillid; DefaultFullAccessPolicy til alt andet). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Handling til** registrering af spam <p> _SpamAction_|**Flyt meddelelsen til mappen uønsket mail** <p> `MoveToJmf`|**Flyt meddelelsen til mappen uønsket mail** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`||
|**Handling til registrering af spam** med høj genkendelse af tillid <p> _HighConfidenceSpamAction_|**Karantænemeddelelse** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`||
|**Handling til** registrering af phishing <p> _PhishSpamAction_|**Karantænemeddelelse** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`||
|**Handlingen Registrering af phishing med** høj tillid <p> _HighConfidencePhishAction_|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`|**Karantænemeddelelse** <p> `Quarantine`||
|**Masseregistreringshandling** <p> _BulkSpamAction_|**Flyt meddelelsen til mappen uønsket mail** <p> `MoveToJmf`|**Flyt meddelelsen til mappen uønsket mail** <p> `MoveToJmf`|**Karantænemeddelelse** <p> `Quarantine`||
|**Behold spam i karantæne i dette antal dage** <p> _KarantæneRetentionPeriod_|15 dage<sup>\*</sup>|30 dage|30 dage|<sup>\*</sup> Standardværdien er 15 dage i standardpolitikken for uønsket post og i nye politikker for uønsket post, som du opretter i PowerShell. Standardværdien er 30 dage i nye antispampolitikker, som du opretter i Microsoft 365 Defender-portalen. <p> Denne værdi påvirker også meddelelser, der er sat i karantæne af antiphishing-politikker. Du kan få mere at vide [under Meddelelser, der er sat i karantæne i EOP](quarantine-email-messages.md).|
|**Aktivér tip til spamsikkerhed** <p> _InlineSafetyTipsEnabled_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|Aktivere automatisk tømning (ZAP) uden time for phishingmeddelelser <p> _PhishZapEnabled_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|Aktivere ZAP for spammeddelelser <p> _SpamZapEnabled_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Tillad & blokliste**|||||
|Tilladte afsendere <p> _AllowedSenders_|Ingen|Ingen|Ingen||
|Tilladte afsenderdomæner <p> _AllowedSenderDomains_|Ingen|Ingen|Ingen|Det er en meget dårlig ide at føje domæner til listen over tilladte afsendere. Hackere vil kunne sende dig mails, som ellers ville blive frafiltreret. <p> Brug efterlignet intelligensindsigt og lejerens tilladelses[-/](tenant-allow-block-list.md)blokeringsliste til at gennemse alle afsendere, der efterligner afsendermailadresser i din organisations maildomæner eller efterligner afsendermailadresser i eksterne domæner.[](learn-about-spoof-intelligence.md)|
|Blokerede afsendere <p> _BlockedSenders_|Ingen|Ingen|Ingen||
|Blokerede afsenderdomæner <p> _BlockedSenderDomains_|Ingen|Ingen|Ingen||

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
|**Angiv en ekstern meddelelsesgrænse** <p> _RecipientLimitExternalPerHour_|0|500|400|Standardværdien 0 betyder, at du bruger tjenestens standardindstillinger.|
|**Angiv en intern meddelelsesgrænse** <p> _RecipientLimitInternalPerHour_|0|1000|800|Standardværdien 0 betyder, at du bruger tjenestens standardindstillinger.|
|**Angiv en daglig meddelelsesgrænse** <p> _RecipientLimitPerDay_|0|1000|800|Standardværdien 0 betyder, at du bruger tjenestens standardindstillinger.|
|**Begrænsning for brugere, der når meddelelsesgrænsen** <p> _ActionWhenThresholdReached_|**Begrænse brugerens mulighed for at sende mail til den følgende dag** <p> `BlockUserForToday`|**Begræns brugerens mulighed for at sende mail** <p> `BlockUser`|**Begræns brugerens mulighed for at sende mail** <p> `BlockUser`||
|**Regler for automatisk videresendelse** <p> _AutoForwardingMode_|**Automatisk – systemkontrolleret** <p> `Automatic`|**Automatisk – systemkontrolleret** <p> `Automatic`|**Automatisk – systemkontrolleret** <p> `Automatic`|
|**Sende en kopi af udgående meddelelser, der overskrider disse begrænsninger for disse brugere og grupper** <p> _BccSuspiciousOutboundMail_ <p> _BccSuspiciousOutboundAdditionalRecipients_|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Vi har ingen specifik anbefaling til denne indstilling. <p> Denne indstilling fungerer kun i standardpolitikken for udgående spam. Det fungerer ikke i brugerdefinerede politikker for udgående spam, som du opretter.|
|**Giv disse brugere og grupper besked, hvis en afsender blokeres på grund af afsendelse af udgående spam** <p> _NotifyOutboundSpam_ <p> _NotifyOutboundSpamRecipients_|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Ikke markeret <p> `$false` <p> Tom|Standardpolitikken [for påmindelse](../../compliance/alert-policies.md),  der hedder Bruger er begrænset til at sende mail, sender allerede mailbeskeder til medlemmer af **gruppen TenantAdmins** (globale administratorer), når brugere **blokeres** pga. overskrider begrænsningerne i politikken. **Vi anbefaler på det kraftigste, at du bruger** påmindelsespolitikken i stedet for denne indstilling i politikken for udgående spam til at underrette administratorer og andre brugere. Du kan finde en vejledning [i Bekræfte indstillingerne for påmindelse for brugere med begrænset adgang](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Politikindstillinger for EOP-antimalware

Hvis du vil oprette og konfigurere antimalwarepolitikker, skal [du se Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Beskyttelsesindstillinger**|||||
|**Aktivere filteret for almindelige vedhæftede filer** <p> _EnableFileFilter_|Ikke markeret <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Denne indstilling sætter meddelelser i karantæne, der indeholder eksekverbare vedhæftede filer baseret på filtype, uanset det vedhæftede indhold.|
|**Aktivér automatisk tømning uden time for malware** <p> _ZapEnabled_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Karantænepolitik**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny antimalwarepolitik, betyder en tom værdi, at standardkarantænepolitikken bruges til at definere de historiske egenskaber for meddelelser, der var sat i karantæne, som malware (AdminOnlyAccessPolicy). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugere. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Modtagerbeskeder**|||||
|**Giv modtagerne besked, når meddelelser er i karantæne som malware** <p> _Handling_|Ikke markeret <p> _DeleteMessage_|Ikke markeret <p> _DeleteMessage_|Ikke markeret <p> _DeleteMessage_|Hvis der registreres malware i en vedhæftet fil i en mail, er meddelelsen i karantæne og kan kun frigives af en administrator.|
|**Afsenderbeskeder**|||||
|**In oplyse interne afsendere, når meddelelser er i karantæne som malware** <p> _EnableInternalSenderNotifications_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`||
|**Underret eksterne afsendere, når meddelelser er i karantæne som malware** <p> _EnableExternalSenderNotifications_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`||
|**Administratormeddelelser**|||||
|**Giv en administrator besked om meddelelser, der ikke blev leveret fra interne afsendere** <p> _EnableInternalSenderAdminNotifications_ <p> _InternalSenderAdminAddress_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Giv en administrator besked om meddelelser, der ikke blev leveret fra eksterne afsendere** <p> _EnableExternalSenderAdminNotifications_ <p> _ExternalSenderAdminAddress_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Vi har ingen specifik anbefaling til denne indstilling.|
|**Tilpas meddelelser**||||Vi har ingen specifikke anbefalinger til disse indstillinger.|
|**Brug tilpasset meddelelsestekst** <p> _CustomNotifications_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`||
|**Fra navn** <p> _CustomFromName_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Fra adresse** <p> _CustomFromAddress_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Tilpasse meddelelser til meddelelser fra interne afsendere**||||Disse indstillinger bruges kun, hvis **Giv** interne afsendere besked, når meddelelser er i karantæne som malware eller Giv besked til en administrator om ikke-leveret meddelelser fra interne afsendere **er markeret** .|
|**Emne** <p> _CustomInternalSubject_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Meddelelse** <p> _CustomInternalPatiy_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Tilpasse meddelelser for meddelelser fra eksterne afsendere**||||Disse indstillinger bruges kun, hvis **Giv** eksterne afsendere besked, når meddelelser er i karantæne som malware, eller Giv besked til en administrator om ikke-leveret meddelelser fra eksterne afsendere **er markeret** .|
|**Emne** <p> _CustomExternalSubject_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||
|**Meddelelse** <p> _CustomExternalTilpasset_|Tom <p> `$null`|Tom <p> `$null`|Tom <p> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Politikindstillinger for EOP-antiphishing

Du kan finde flere oplysninger om disse indstillinger [under Spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings). Se Konfigurer [antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md) for at konfigurere disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishing & beskyttelse**|||||
|**Aktivér efterlignet intelligens** <p> _EnableSpoofIntelligence_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som efterlignet** <p> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Sætte meddelelsen i karantæne** <p> `Quarantine`|Denne indstilling gælder for efterlignede afsendere, der blev blokeret automatisk, sådan som det er vist i [efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt eller manuelt blokeret på lejerens tilladelses [-/blokeringsliste](tenant-allow-block-list.md). <p> Hvis du vælger Karantæne **for** meddelelsen, er  der et politikfelt Anvend karantæne tilgængeligt, hvor du kan vælge den karantænepolitik, der definerer, hvad brugere har tilladelse til at gøre på meddelelser, der er i karantæne som spoofing. Når du opretter en ny antiphishing-politik, betyder en tom værdi, at standardpolitikken for karantæne bruges til at definere de historiske egenskaber for meddelelser, der var i karantæne, som spoofing (DefaultFullAccessPolicy). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mere restriktive eller mindre restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Vis første sikkerhedstip** <p> _EnableFirstContactSafetyTips_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Du kan få mere at vide [under Første sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Show (?) for ikke-godkendte afsendere for spoof** <p> _EnableUnauthenticatedSender_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`|Føjer et spørgsmålstegn (?) til afsenderens billede i Outlook for uidentificeret spoof afsendere. Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Vis mærket "via"** <p> _EnableViaTag_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`|Føjer et via-mærke (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis det er forskelligt fra domænet i DKIM-signaturen eller **MAIL FRA-adressen** . <p> Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender for Office 365 sikkerhed

Der med fås yderligere sikkerhedsfordele med et Microsoft Defender til Office 365 abonnement. Du kan finde de seneste nyheder og oplysninger [under Nyheder i Defender til Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - Standardpolitikken for phishing i Microsoft Defender til Office 365 giver [efterlignet beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) og postkasseintelligens til alle modtagere. Men de andre tilgængelige funktioner [til repræsentationsbeskyttelse](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og [avancerede indstillinger](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) er ikke konfigureret eller aktiveret i standardpolitikken. Hvis du vil aktivere alle beskyttelsesfunktioner, skal du ændre standardpolitikken for phishing eller oprette flere antiphishing-politikker.
>
> - Selvom der ikke er nogen standardpolitik Pengeskab Vedhæftede filer eller Pengeskab Links-politik, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab beskyttelse af vedhæftede filer og Pengeskab **Links-beskyttelse** til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Politikker for vedhæftede filer eller Pengeskab  Politikker for links). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md).
>
> - [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md) og Pengeskab-dokumentbeskyttelse er ikke afhængige af Pengeskab politikker for links[](safe-docs.md).

Hvis dit abonnement omfatter Microsoft Defender til Office 365, eller hvis du har købt Defender Office 365 som et tilføjelsesprogrammet, skal du angive følgende Standard- eller Streng-konfigurationer.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Politikindstillinger for phishing i Microsoft Defender til Office 365

EOP-kunder får grundlæggende antiphishing som beskrevet tidligere, men Defender til Office 365 indeholder flere funktioner og kontrol, der kan hjælpe med at forhindre, registrere og afhjælpe mod angreb. Hvis du vil oprette og konfigurere disse politikker, [skal du se Konfigurer antiphishing-politikker i Defender Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Avancerede indstillinger i antiphishing-politikker i Microsoft Defender Office 365

Du kan finde flere oplysninger om denne indstilling [i Avancerede phishingtærskler i antiphishing-politikker i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere denne indstilling, [skal du se Konfigurer antiphishing-politikker i Defender Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishingmail** <p> _PhishThresholdLevel_|**1 – Standard** <p> `1`|**2 – Aggressive** <p> `2`|**3 – mere aggressive** <p> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Indstillinger for efterligning i antiphishing-politikker i Microsoft Defender Office 365

Du kan finde flere oplysninger om disse indstillinger [under Indstillinger for repræsentation i antiphishing-politikker i Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer antiphishing-politikker i Defender Office 365](configure-mdo-anti-phishing-policies.md).

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishing & beskyttelse**|||||
|**Gøre det muligt for brugerne** at beskytte (efterligning af brugerbeskyttelse) <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Ikke markeret <p> `$false` <p> ingen|Markeret <p> `$true` <p> \<list of users\>|Markeret <p> `$true` <p> \<list of users\>|Vi anbefaler, at du tilføjer brugere (meddelelsesafsendere) i vigtige roller. Internt kan beskyttede afsendere være din administrerende direktør, CFO og andre seniorledere. Eksternt kan beskyttede afsendere omfatte rådmedlemmer eller din bestyrelse. <p> I forudindstillede sikkerhedspolitikker kan du ikke angive, hvilke brugere der skal beskyttes. Du skal deaktivere de foruddefinerede sikkerhedspolitikker og bruge brugerdefinerede antiphishing-politikker til at tilføje brugere i nøgleroller, som foreslået.|
|**Aktivér domæner for at beskytte** (efterligning af domænebeskyttelse)|Ikke markeret|Markeret|Markeret||
|**Medtag domæner, jeg ejer** <p> _EnableOrganizationDomainsProtection_|Fra <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Medtag brugerdefinerede domæner** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Fra <p> `$false` <p> ingen|Markeret <p> `$true` <p> \<list of domains\>|Markeret <p> `$true` <p> \<list of domains\>|Vi anbefaler, at du tilføjer domæner (afsenderdomæner), som du ikke ejer, men du ofte interagerer med. <p> I foruddefinerede sikkerhedspolitikker kan du ikke angive de brugerdefinerede domæner, der skal beskyttes. Du skal deaktivere de foruddefinerede sikkerhedspolitikker og bruge brugerdefinerede antiphishing-politikker for at tilføje brugerdefinerede domæner, der skal beskyttes, som foreslået.|
|**Tilføj afsendere og domæner, der er tillid til** <p> _ExcludedSenders_ <p> _ExcludedDomains_|Ingen|Ingen|Ingen|Afhængigt af din organisation anbefaler vi, at du tilføjer afsendere eller domæner, der fejlagtigt er identificeret som forsøg på efterligning.|
|**Aktivér postkasseintelligens** <p> _EnableMailboxIntelligence_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Aktivere intelligens til repræsentationsbeskyttelse** <p> _EnableMailboxIntelligenceProtection_|Fra <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Denne indstilling tillader den angivne handling til repræsentationsregistreringer ved hjælp af postkasseintelligens.|
|**Handlinger**||||Uanset hvor du vælger **Karantæne i meddelelsen**, vil et **af politikfeltet Vælg** karantæne være tilgængeligt. Karantænepolitikker definerer, hvad brugere har tilladelse til at gøre for meddelelser, der er sat i karantæne. <p> Når du opretter en ny antiphishing-politik, betyder en tom værdi, at standardpolitikken for karantæne bruges til at definere de historiske egenskaber for meddelelser, der er sat i karantæne efter denne vurdering (DefaultFullAccessPolicy for alle registreringstyper for efterligninger). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer mindre restriktive eller mere restriktive funktioner for brugerne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Hvis meddelelsen registreres som en efterligning af en bruger** <p> _TargetedUserProtectionAction_|**Anvend ikke nogen handling** <p> `NoAction`|**Sætte meddelelsen i karantæne** <p> `Quarantine`|**Sætte meddelelsen i karantæne** <p> `Quarantine`|Husk, at forudindstillede sikkerhedspolitikker ikke tillader dig at angive, hvilke brugere der skal beskyttes, så denne indstilling gør effektivt intet i forudindstillede sikkerhedspolitikker.|
|**Hvis meddelelsen registreres som et efterligning af domæne** <p> _TargetedDomainProtectionAction_|**Anvend ikke nogen handling** <p> `NoAction`|**Sætte meddelelsen i karantæne** <p> `Quarantine`|**Sætte meddelelsen i karantæne** <p> `Quarantine`|Husk, at forudindstillede sikkerhedspolitikker ikke tillader dig at angive de brugerdefinerede domæner, der skal beskyttes, så denne indstilling påvirker kun domæner, som du ejer, ikke brugerdefinerede domæner.|
|**Hvis postkasseintelligens registrerer og efterligner bruger** <p> _MailboxIntelligenceProtectionAction_|**Anvend ikke nogen handling** <p> `NoAction`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Sætte meddelelsen i karantæne** <p> `Quarantine`||
|**Vis sikkerhedstip** <p> _EnableSimilarUsersSafetyTips_|Fra <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Vis sikkerhedstip** <p> _EnableSimilarDomainsSafetyTips_|Fra <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Vis bruger efterligning af usædvanlige tegn sikkerhedstip** <p> _EnableUnusualCharactersSafetyTips_|Fra <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Politikindstillinger for EOP-antiphishing i Microsoft Defender Office 365

Disse er de samme indstillinger, der er tilgængelige i [politikindstillinger for uønsket post i EOP](#eop-anti-spam-policy-settings).

Indstillingerne for spoof er indbyrdes forbundne, men indstillingen Vis første **kontakt sikkerhedstip** ikke afhængighed af spoof-indstillinger.

|Navn på sikkerhedsfunktion|Standard|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|---|
|**Grænseværdi for phishing & beskyttelse**|||||
|**Aktivér efterlignet intelligens** <p> _EnableSpoofIntelligence_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Handlinger**|||||
|**Hvis meddelelsen registreres som efterlignet** <p> _AuthenticationFailAction_|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Flyt meddelelsen til modtagernes mapper med uønsket mail** <p> `MoveToJmf`|**Sætte meddelelsen i karantæne** <p> `Quarantine`|Denne indstilling gælder for efterlignede afsendere, der blev blokeret automatisk, sådan som det er vist i [efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt eller manuelt blokeret på lejerens tilladelses [-/blokeringsliste](tenant-allow-block-list.md). <p> Hvis du vælger **Karantæne for** meddelelsen, er  et anvend karantænepolitikfelt tilgængeligt for at vælge den karantænepolitik, der definerer, hvad brugerne har tilladelse til at gøre for meddelelser, der er sat i karantæne. Når du opretter en ny antiphishing-politik, betyder en tom værdi, at standardpolitikken for karantæne bruges til at definere de historiske egenskaber for spoof meddelelser, der er sat i karantæne (DefaultFullAccessPolicy). <p> Administratorer kan oprette og vælge en brugerdefineret karantænepolitik, der definerer, hvad modtagere har tilladelse til at gøre ved disse meddelelser i karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Vis første sikkerhedstip** <p> _EnableFirstContactSafetyTips_|Ikke markeret <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Du kan få mere at vide [under Første sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Show (?) for ikke-godkendte afsendere for spoof** <p> _EnableUnauthenticatedSender_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`|Føjer et spørgsmålstegn (?) til afsenderens billede i Outlook for uidentificeret spoof afsendere. Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Vis mærket "via"** <p> _EnableViaTag_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`|Føjer et via-mærke (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis det er forskelligt fra domænet i DKIM-signaturen eller **MAIL FRA-adressen** . <p> Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).|

### <a name="safe-attachments-settings"></a>Pengeskab indstillinger for vedhæftede filer

Pengeskab Vedhæftede filer i Microsoft Defender for Office 365 omfatter globale indstillinger, der ikke har nogen relation til Pengeskab Politikker for vedhæftede filer og indstillinger, der er specifikke for hver Pengeskab Links-politik. Du kan finde flere oplysninger [Pengeskab Vedhæftede filer i Defender Office 365](safe-attachments.md).

Selvom der ikke er nogen standardpolitik Pengeskab Vedhæftede filer, giver den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Politikker for vedhæftede filer). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Globale indstillinger for Pengeskab vedhæftede filer

> [!NOTE]
> De globale indstillinger for Pengeskab Vedhæftede filer er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, men ikke af **Standard** eller **Faste** forudindstillede sikkerhedspolitikker. Uanset hvad kan administratorer til enhver tid ændre disse globale Pengeskab indstillinger for vedhæftede filer.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den **indbyggede beskyttelse** foruddefinerede sikkerhedspolitik. Kolonnen **Indbyggede beskyttelse** viser de værdier, der er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, skal du se Pengeskab Vedhæftede [filer for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) og [Pengeskab Dokumenter i Microsoft 365 E5](safe-docs.md).

I PowerShell bruger du [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Slå Defender til for Office 365 for SharePoint, OneDrive og Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Fra <p> `$false`|Til <p> `$true`|Hvis du vil forhindre brugere i at hente skadelige filer, [skal du se Brug SharePoint Online PowerShell til at forhindre brugere i at hente skadelige filer](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Slå Pengeskab Dokumenter til for Office klienter** <p> _EnableSafeDocs_|Fra <p> `$false`|Til <p> `$true`|Denne funktion er kun tilgængelig og giver mening med licenser, der ikke er inkluderet i Defender Office 365 (f.eks Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed). Du kan finde flere oplysninger [Pengeskab Dokumenter i Microsoft 365 E5](safe-docs.md).|
|**Tillad brugere at klikke gennem Beskyttet visning, selvom Pengeskab dokumenter identificeret filen som skadelige** <p> _AllowSafeDocsOpen_|Fra <p> `$false`|Fra <p> `$false`|Denne indstilling er relateret til Pengeskab Dokumenter.|

#### <a name="safe-attachments-policy-settings"></a>Pengeskab indstillinger for politik for vedhæftede filer

Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer Pengeskab politikker for vedhæftede filer i Defender Office 365](set-up-safe-attachments-policies.md).

I PowerShell bruger du [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) - og [Set-SafeAttachmentPolicy-cmdlet'er](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik Pengeskab Vedhæftede filer, men Pengeskab Beskyttelse af vedhæftede filer tildeles til alle modtagere af den [**indbyggede**](preset-security-policies.md) beskyttelse foruddefinerede sikkerhedspolitik.
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i den nye Pengeskab politikker for vedhæftede filer, du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**Pengeskab ukendt malwaresvar ved vedhæftede filer** <p> _Aktivér_ og _handling_|**Fra** <p> `-Enable $false` og `-Action Block`|**Bloker** <p> `-Enable $true` og `-Action Block`|**Bloker** <p> `-Enable $true` og `-Action Block`|**Bloker** <p> `-Enable $true` og `-Action Block`|Når _parameteren_ Aktivér er $false, betyder værdien for handlingsparameteren ikke noget.|
|**Karantænepolitik** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Når du opretter en ny Pengeskab Politik for vedhæftede filer, betyder en tom værdi standardkarantænepolitikken, der bruges til at definere de historiske egenskaber for meddelelser, der var i karantæne af Pengeskab Vedhæftede filer (AdminOnlyAccessPolicy). <p> Administratorer kan oprette og vælge brugerdefinerede karantænepolitikker, der definerer flere funktioner for brugere. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).|
|**Omdiriger vedhæftet fil med registrerede vedhæftede filer** : **Aktivér omdirigering** <p> _Omdiriger_ <p> _RedirectAddress_|Ikke markeret, og der er ikke angivet en mailadresse. <p> `-Redirect $false` <p> _RedirectAddress_ er tom (`$null`)|Ikke markeret, og der er ikke angivet en mailadresse. <p> `-Redirect $false` <p> _RedirectAddress_ er tom (`$null`)|Markeret, og angiv en mailadresse. <p> `$true` <p> en mailadresse|Markeret, og angiv en mailadresse. <p> `$true` <p> en mailadresse|Omdirigere meddelelser til en sikkerhedsadministrator til gennemsyn. <p> **Bemærk**! Denne indstilling er ikke konfigureret **i standard,** **streng eller** **indbyggede sikkerhedspolitikker.** Standard **-** og **Strict-værdierne** angiver vores **anbefalede værdier** i den nye Pengeskab vedhæftede filer-politikker, du opretter.|
|**Anvend søges Pengeskab registreringssvar for vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout eller fejl)** <p> _ActionOnError_|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||

### <a name="safe-links-settings"></a>Pengeskab links

Pengeskab Links i Defender til Office 365 omfatter globale indstillinger, der gælder for alle brugere, som er inkluderet i aktive Pengeskab Links-politikker, og indstillinger, der er specifikke for hver Pengeskab Links-politik. Du kan finde flere oplysninger [Pengeskab Links i Defender for Office 365](safe-links.md).

Selvom der ikke er nogen standardpolitik for Pengeskab Links, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab **Kæder-politikker**). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Globale indstillinger for Pengeskab links

> [!NOTE]
> De globale indstillinger for Pengeskab links er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, men ikke af **Standard** eller **Faste forudindstillede** sikkerhedspolitikker. Uanset hvad kan administratorer ændre disse globale indstillinger Pengeskab links når som helst.
>
> Kolonnen **Standard** viser værdierne før eksistensen af den **indbyggede beskyttelse** foruddefinerede sikkerhedspolitik. Kolonnen **Indbyggede beskyttelse** viser de værdier, der er angivet af den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik, som også er vores anbefalede værdier.

Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer globale indstillinger for Pengeskab Links i Defender for Office 365](configure-global-settings-for-safe-links.md).

I PowerShell bruger du [Set-AtpPolicyForO365-cmdlet'en](/powershell/module/exchange/set-atppolicyforo365) til disse indstillinger.

|Navn på sikkerhedsfunktion|Standard|Indbygget beskyttelse|Kommenter|
|---|:---:|:---:|---|
|**Blokere følgende URL-adresser** <p> _ExcludedUrls_|Tom <p> `$null`|Tom <p> `$null`|Vi har ingen specifik anbefaling til denne indstilling. <p> Du kan finde flere oplysninger [på listen "Bloker følgende URL-adresser" for Pengeskab Links](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Brug Pengeskab Links i Office 365 apps** <p> _EnableSafeLinksForO365Clients_|Til <p> `$true`|Til <p> `$true`|Brug Pengeskab Links i understøttede Office 365 og mobilapps (iOS og Android). Du kan finde flere oplysninger [Pengeskab Indstillinger for links til Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).|
|**Registrer ikke, når brugere klikker på beskyttede links i Office 365 apps** <p> _TrackClicks_|Til <p> `$false`|Fra <p> `$true`|Hvis du deaktiverer denne indstilling (_indstilling af TrackClicks_ til `$true`), registreres brugerklik i understøttede Office 365 apps.|
|**Lad ikke brugere klikke igennem til den oprindelige URL-adresse i Office 365 apps** <p> _TilladKlikThrough_|Til <p> `$false`|Til <p> `$false`|Aktivering af denne indstilling (indstilling _af TilladKlikThrough_ til `$false`) forhindrer klik til den oprindelige URL-adresse i understøttede Office 365 apps.|

#### <a name="safe-links-policy-settings"></a>Pengeskab links til politikindstillinger

Hvis du vil konfigurere disse indstillinger, [skal du se Konfigurer Pengeskab Links-politikker i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

I PowerShell bruger du [cmdlet'erne New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) og [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) til disse indstillinger.

> [!NOTE]
> Som beskrevet tidligere er der ingen standardpolitik Pengeskab Links, men beskyttelse af Pengeskab Links tildeles til alle modtagere af den [**indbyggede**](preset-security-policies.md) beskyttelse foruddefinerede sikkerhedspolitik.
>
> **Standarden i den brugerdefinerede** kolonne refererer til standardværdierne i den nye Pengeskab Links-politikker, du opretter. De resterende kolonner angiver (medmindre andet er angivet) de værdier, der er konfigureret i de tilsvarende forudindstillede sikkerhedspolitikker.

|Navn på sikkerhedsfunktion|Standard i brugerdefineret|Indbygget beskyttelse|Standard|Begrænset|Kommenter|
|---|:---:|:---:|:---:|:---:|---|
|**Beskyttelsesindstillinger**||||||
|**Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser** <p> _IsEnabled_|**Fra** <p> `$false`|**Til** <p> `$true`|**Til** <p> `$true`|**Til** <p> `$true`||
|**Vælg handlingen for ukendte eller potentielt skadelige URL-adresser i Microsoft Teams** <p> _EnableSafeLinksForTeams_|**Fra** <p> `$false`|**Til** <p> `$true`|**Til** <p> `$true`|**Til** <p> `$true`||
|**Anvend URL-scanning i realtid for mistænkelige links og links, der peger på filer** <p> _ScanUrls_|Ikke markeret <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Vent på, at URL-adressen scannes, før meddelelsen leveres** <p> _DeliverMessageAfterScan_|Ikke markeret <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Anvend Pengeskab links til mails, der er sendt i organisationen** <p> _EnableForInternalSenders_|Ikke markeret <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Markeret <p> `$true`||
|**Registrer ikke brugerklik** <p> _DoNotTrackUserClicks_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Hvis du slår denne indstilling fra ( _indstilling DoNotTrackUserClicks_ til `$false`), spores brugeres klik.|
|**Lad ikke brugere klikke igennem til den oprindelige URL-adresse** <p> _DoNotAllowClickThrough_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Markeret <p> `$true`|Markeret <p> `$true`|Aktivering af denne indstilling (indstilling _DoNotAllowClickThrough_ til `$true`) forhindrer klik igennem til den oprindelige URL-adresse.|
|**Vise organisationens branding på meddelelses- og advarselssider** <p> _EnableOrganizationBranding_|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`|Vi har ingen specifik anbefaling til denne indstilling. <p> Før du slår denne indstilling til, skal du følge vejledningen i Tilpas [Microsoft 365-temaet for din organisation for](../../admin/setup/customize-your-organization-theme.md) at overføre dit firmalogo.|
|**Undlad at omskrive URL-adresser, kontroller kun via Pengeskab Links API** <p> _DisableURLRewrite_|Ikke markeret <p> `$false`|Markeret <p> `$true`|Ikke markeret <p> `$false`|Ikke markeret <p> `$false`||
|**Undlad at omskrive følgende URL-adresser** <p> _DoNotRewriteUrls_|Ikke markeret <p> tom|Ikke markeret <p> tom|Ikke markeret <p> tom|Ikke markeret <p> tom|Vi har ingen specifik anbefaling til denne indstilling. Få mere at vide under ["Omse ikke følgende URL-adresser"-lister i Pengeskab Links-politikker](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**Meddelelse**||||||
|**Hvordan vil du give dine brugere besked?**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|**Brug standardmeddelelsesteksten**|Vi har ingen specifik anbefaling til denne indstilling. <p> Du kan vælge **Brug brugerdefineret meddelelsestekst** (_CustomNotificationText_) for at angive tilpasset meddelelsestekst, der skal bruges. Du kan også vælge **Brug Microsoft Oversætter til** automatisk lokalisering (_UseTranslatedNotificationText_) for at oversætte den brugerdefinerede meddelelsestekst til brugerens sprog.

## <a name="related-articles"></a>Relaterede artikler

- Leder du efter bedste fremgangsmåder til **Exchange regler for mailflow (også kaldet transportregler**)? Se [Bedste fremgangsmåder til konfiguration af regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Administratorer og brugere kan sende falske positive (god mail markeret som dårlig) og falske negativer (ugyldig mail tilladt) til analyse hos Microsoft. Få mere at vide under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

- Brug disse links for at få oplysninger om **, hvordan du** [konfigurerer din EOP-tjeneste](/exchange/standalone-eop/set-up-your-eop-service) og **konfigurerer** [Microsoft Defender Office 365](defender-for-office-365.md). Glem ikke de nyttige anvisninger i "[Beskyt mod trusler i Office 365](protect-against-threats.md)".

- Sikkerheds oprindelige planer **for Windows** kan findes her: Hvor kan jeg få de oprindelige sikkerhedsscenarier [?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) for gruppepolitikobjekt/lokale indstillinger og Brug oprindelige planer for sikkerhed til at konfigurere [Windows-enheder i Intune](/intune/protect/security-baselines) for Intune-baseret sikkerhed. Endelig findes en sammenligning mellem Microsoft Defender for Slutpunkt og Microsoft Intune-sikkerheds baselines i [Compare the Microsoft Defender for Endpoint og Windows Intune security baselines](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
