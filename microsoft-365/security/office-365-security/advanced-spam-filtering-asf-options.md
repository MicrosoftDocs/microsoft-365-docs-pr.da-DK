---
title: ASF-indstillinger i EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b286f853-b484-4af0-b01f-281fffd85e7a
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om de avancerede indstillinger for spamfilter (ASF), der er tilgængelige i politikker for uønsket post i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 71eeaec20ab64b5faa535ddb2f9e688b9b9192d9
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63589170"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Avancerede indstillinger for spamfilter (ASF) i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I alle Microsoft 365 virksomheder giver ASF-indstillingerne (Advanced Spam Filter) i antispampolitikker i EOP administratorer mulighed for at markere meddelelser som spam baseret på bestemte meddelelsesegenskaber. ASF finder specifikt disse egenskaber, fordi de ofte findes i spam. Afhængigt af egenskaben markerer ASF-registreringer enten meddelelsen som **spam eller** **spam med høj genkendelsessikkerhed**.

> [!NOTE]
> Aktivering af en eller flere af ASF-indstillingerne er en aggressive tilgang til spamfiltrering. Du kan ikke rapportere meddelelser, der er filtreret efter ASF, som falske positive. Du kan identificere meddelelser, der er filtreret efter ASF, efter:
>
> - Periodiske meddelelser i karantæne fra spam og fuld tillid til spamfilteret.
> - Tilstedeværelsen af filtrerede meddelelser i karantæne.
> - De specifikke `X-CustomSpam:` X-brevhovedfelter, der er føjet til meddelelser som beskrevet i denne artikel.

De følgende afsnit beskriver ASF-indstillingerne og -indstillinger, der er tilgængelige i antispampolitikker på Microsoft 365 Defender-portalen og i Exchange Online PowerShell eller enkeltstående EOP PowerShell ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) og [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)). Få mere at vide under [Konfigurer antispam-politikker i EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Aktivér, deaktiver eller test ASF-indstillinger

For hver ASF-indstilling er følgende indstillinger tilgængelige i antispampolitikker:

- **Til**: ASF føjer det tilsvarende X-brevhovedfelt til meddelelsen og markerer enten meddelelsen som **Spam** (SCL 5 eller 6 for Øg [indstillinger for spamscore](#increase-spam-score-settings)) eller SCL **9 for Markér** som [spamindstillinger](#mark-as-spam-settings).
- **Fra**: Asf-indstillingen er deaktiveret. Dette er standardværdien, og vi anbefaler, at du ikke ændrer den.
- **Test**: ASF føjer det tilsvarende X-brevhovedfelt til meddelelsen. Hvad sker der med meddelelsen, bestemmes af **værdien Testtilstand** (*TestModeAction*):
  - **Ingen**: Leveringen af meddelelser påvirkes ikke af asf-registrering. Meddelelsen er stadig underlagt andre typer filtrering og regler i EOP.
  - **Tilføj standardtekst i X-brevhoved (*AddXHeader*)**: Værdien for X-brevhovedet `X-CustomSpam: This message was filtered by the custom spam filter option` føjes til meddelelsen. Du kan bruge denne værdi i indbakkeregler eller regler for mailflow (også kaldet transportregler) til at påvirke leveringen af meddelelsen.
  - **Send Bcc-meddelelse (*BccMessage*)**: De angivne mailadresser ( *parameterværdien TestModeBccToRecipients* i PowerShell) føjes til feltet Bcc i meddelelsen, og meddelelsen leveres til de ekstra Bcc-modtagere. I Microsoft 365 Defender skal du adskille flere mailadresser med semikolon (;). I PowerShell adskiller du flere mailadresser med kommaer.

  **Bemærkninger**:

  - Testtilstand er ikke tilgængelig for følgende ASF-indstillinger:
    - **Filtrering af betinget afsender-id: mislykkes** (*MarkAsSpamFromAddressAuthFail*)
    - **NDR backscatter**(*MarkAsSpamNdrBackscatter*)
    - **SPF-post: hard fail** (*MarkAsSpamSpfRecordHardFail*)
  - Den samme testtilstandshandling anvendes *på alle* ASF-indstillinger, der er indstillet til **Test**. Du kan ikke konfigurere forskellige testtilstandshandlinger for forskellige asf-indstillinger.

## <a name="increase-spam-score-settings"></a>Forøg indstillinger for spamscore

Følgende **forøg spamscore** ASF-indstillinger angiver spamtillidsniveauet (SCL) for registrerede meddelelser til 5 eller 6, hvilket svarer til en vurdering af **spamfilteret** og den tilsvarende handling i antispampolitikker.

<br>

****

|Indstilling for antispampolitik|Beskrivelse|X-sidehoved tilføjet|
|---|---|---|
|**Billedlinks til eksterne websteder** <p> *IncreaseScoreWithImageLinks*|Meddelelser, der indeholder `<Img>` HTML-kodelinks til eksterne websteder (f.eks. ved hjælp af http), markeres som spam.|`X-CustomSpam: Image links to remote sites`|
|**Numerisk IP-adresse i URL-adresse** <p> *IncreaseScoreWithNumericIps*|Meddelelser, der indeholder numeriske URL-adresser (typisk IP-adresser), markeres som spam.|`X-CustomSpam: Numeric IP in URL`|
|**URL-adresse, der omdirigeres til en anden port** <p> *IncreaseScoreWithRedirectToOtherPort*|Meddelelse, der indeholder links, der omdirigerer til andre TCP-porte end 80 (HTTP), 8080 (alternativt HTTP) eller 443 (HTTPS), markeres som spam.|`X-CustomSpam: URL redirect to other port`|
|**Links til .biz- eller .info-websteder** <p> *IncreaseScoreWithBizOrInfoUrls*|Meddelelser, der `.biz` indeholder eller `.info` links i meddelelsens brødtekst, markeres som spam.|`X-CustomSpam: URL to .biz or .info websites`|
|

## <a name="mark-as-spam-settings"></a>Markér som spamindstillinger

Følgende indstillinger **for Markér som spam** ASF indstiller SCL for registrerede meddelelser til 9, hvilket svarer til en vurdering af **spamfilteret** med høj tillid og den tilsvarende handling i antispampolitikker.

<br>

****

|Indstilling for antispampolitik|Beskrivelse|X-sidehoved tilføjet|
|---|---|---|
|**Tomme meddelelser** <p> *MarkAsSpamEmptyMessages*|Meddelelser uden emne, intet indhold i brødteksten og ingen vedhæftede filer markeres som spam med høj tillid.|`X-CustomSpam: Empty Message`|
|**Integrerede koder i HTML** <p> *MarkAsSpamEmbedTagsInHtml*|Meddelelse, der indeholder `<embed>` HTML-koder, er markeret som spam med høj tillid. <p> Dette mærke gør det muligt at integrere forskellige typer dokumenter i et HTML-dokument (f.eks. lyde, videoer eller billeder).|`X-CustomSpam: Embed tag in html`|
|**JavaScript eller VBScript i HTML** <p> *MarkAsSpamJavaScriptInHtml*|Meddelelser, der bruger JavaScript eller Visual Basic Script Edition i HTML, markeres som spam med høj tillid. <p> Disse scriptsprog bruges i mails til at forårsage, at bestemte handlinger automatisk udføres.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Formularkoder i HTML** <p> *MarkAsSpamFormTagsInHtml*|Meddelelser, der indeholder `<form>` HTML-koder, er markeret som spam med høj tillid. <p> Dette mærke bruges til at oprette webstedsformularer. Mailannoncering omfatter ofte dette mærke for at anmode om oplysninger fra modtageren.|`X-CustomSpam: Form tag in html`|
|**Ramme- eller iframe-koder i HTML** <p> *MarkAsSpamFramesInHtml*|Meddelelser, der indeholder `<frame>` eller `<iframe>` HTML-koder, er markeret som spam med høj tillid. <p> Disse mærker bruges i mails til at formatere siden til visning af tekst eller grafik.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Webfejl i HTML** <p> *MarkAsSpamWebBugsInHtml*|En *webfejl* (også kaldet en *web-beacon*) er et grafisk element (ofte så lille som én pixel med én pixel), der bruges i mails til at afgøre, om meddelelsen blev læst af modtageren. <p> Meddelelser, der indeholder webfejl, er markeret som spam med høj tillid. <p> Legitime nyhedsbreve kan anvende webfejl, selvom mange mener, at dette er en krænkelse af personlige oplysninger. |`X-CustomSpam: Web bug`|
|**Objektkoder i HTML** <p> *MarkAsSpamObjectTagsInHtml*|Meddelelser, der indeholder `<object>` HTML-koder, er markeret som spam med høj tillid. <p> Dette mærke gør det muligt for plug-ins eller programmer at køre i et HTML-vindue.|`X-CustomSpam: Object tag in html`|
|**Følsomme ord** <p> *MarkAsSpamSensitiveWordList*|Microsoft vedligeholder en dynamisk, men ikke-redigerbar liste over ord, der er knyttet til potentielt stødende meddelelser. <p> Meddelelser, der indeholder ord fra listen over følsomme ord i emnet eller meddelelsesteksten, markeres som spam med høj tillid.|`X-CustomSpam: Sensitive word in subject/body`|
|**SPF-post: Hard Fail** <p> *MarkAsSpamSpfRecordHardFail*|Meddelelser, der sendes fra en IP-adresse, der ikke er angivet i SPF SPF(Sender Policy Framework)-posten (SPF) i DNS for kildemaildomænet, markeres som spam med høj overensstemmelse. <p> Testtilstand er ikke tilgængelig for denne indstilling.|`X-CustomSpam: SPF Record Fail`|
|

Følgende indstillinger **for Markér som spam** ASF indstiller SCL for registrerede meddelelser til 6, hvilket svarer til en **spamfilters** konklusion og den tilsvarende handling i politikker for uønsket post.

<br>

****

|Indstilling for antispampolitik|Beskrivelse|X-sidehoved tilføjet|
|---|---|---|
|**Filtrering af afsender-id mislykkedes** <p> *MarkAsSpamFromAddressAuthFail*|Meddelelser, der ikke kan kontrolleres via betinget afsender-id, markeres som spam. <p> Denne indstilling kombinerer en SPF-kontrol med en Afsender-id-kontrol for at beskytte mod brevhoveder, der indeholder forfalskede afsendere. <p> Testtilstand er ikke tilgængelig for denne indstilling.|`X-CustomSpam: SPF From Record Fail`|
|**Backscatter** <p> *MarkAsSpamNdrBackscatter*|*Backscatter er* ubrugelige rapporter om manglende levering (også kaldet NDR'er eller meddelelser om ikke-leveret post), der er forårsaget af forfalskede afsendere i mails. Du kan finde flere oplysninger [i Backscatter-meddelelser og EOP](backscatter-messages-and-eop.md). <p> Du behøver ikke at konfigurere denne indstilling i følgende miljøer, da legitime NDR'er leveres, og backscatter markeres som spam: <ul><li>Microsoft 365 med Exchange Online postkasser.</li><li>Lokale mailorganisationer, hvor du distribuerer *udgående mail* via EOP.</li></ul> <p> I enkeltstående EOP-miljøer, der beskytter indgående mail til lokale postkasser, har følgende resultat, hvis du slår denne indstilling til eller fra: <ul><li> **Til**: Legitime NDR'er leveres, og backscatter markeres som spam.</li><li>**Fra**: Legitime NDR'er og backscatter gennemgår normal spamfiltrering. De mest legitime NDR'er vil blive leveret til den oprindelige meddelelsesafsender. Nogle, men ikke alle, backscatter er markeret som spam. Backscatter kan pr. definition kun leveres til den spoofed afsender, ikke til den oprindelige afsender.</li></ul> <p> Testtilstand er ikke tilgængelig for denne indstilling.|`X-CustomSpam: Backscatter NDR`|
|
