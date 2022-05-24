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
description: Administratorer kan få mere at vide om DEF-indstillinger (Advanced Spam Filter), der er tilgængelige i politikker til bekæmpelse af spam i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 75fca937049e71576e1dd599b4cc0f7fba2a2211
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647661"
---
# <a name="advanced-spam-filter-asf-settings-in-eop"></a>Avancerede indstillinger for spamfilter i EOP

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I alle Microsoft 365 organisationer giver ASF-indstillingerne (Advanced Spam Filter) i politikker til bekæmpelse af spam i EOP administratorer mulighed for at markere meddelelser som spam baseret på specifikke meddelelsesegenskaber. ASF er specifikt målrettet disse egenskaber, fordi de ofte findes i spam. Afhængigt af egenskaben markerer ASF-registreringer enten meddelelsen som **spam** eller **spam med høj genkendelsessikkerhed**.

> [!NOTE]
> Aktivering af en eller flere af ASF-indstillingerne er en aggressiv tilgang til filtrering af spam. Du kan ikke rapportere meddelelser, der er filtreret efter ASF som falske positiver. Du kan identificere meddelelser, der er filtreret efter ASF, ved at:
>
> - Periodiske karantænemeddelelser fra spam og dom over spamfilter med høj genkendelsessikkerhed.
> - Tilstedeværelsen af filtrerede meddelelser i karantæne.
> - De specifikke `X-CustomSpam:` X-headerfelter, der føjes til meddelelser som beskrevet i denne artikel.

I de følgende afsnit beskrives de INDSTILLINGER og indstillinger for asf-filer, der er tilgængelige i politikker til bekæmpelse af spam på Microsoft 365 Defender-portalen og i Exchange Online PowerShell eller enkeltstående EOP PowerShell ([New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy) og [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy)). Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).

## <a name="enable-disable-or-test-asf-settings"></a>Aktivér, deaktiver eller test asf-indstillinger

For hver ASF-indstilling er følgende indstillinger tilgængelige i politikker til bekæmpelse af spam:

- **On**: ASF føjer det tilsvarende X-headerfelt til meddelelsen og markerer enten meddelelsen som **Spam** (SCL 5 eller 6 for [Øg scoreindstillinger for spam](#increase-spam-score-settings)) eller **Høj tillid til spam** (SCL 9 for [Markér som spamindstillinger](#mark-as-spam-settings)).
- **Fra**: INDSTILLINGEN ASF er deaktiveret. Dette er standardværdien, og vi anbefaler, at du ikke ændrer den.
- **Test**: ASF føjer det tilsvarende X-headerfelt til meddelelsen. Det, der sker med meddelelsen, bestemmes af værdien **testtilstand** (*TestModeAction*):
  - **Ingen**: Levering af meddelelser påvirkes ikke af ASF-registreringen. Meddelelsen er stadig underlagt andre typer filtrering og regler i EOP.
  - **Tilføj standardteksten i X-headeren (*AddXHeader*):** X-headerværdien `X-CustomSpam: This message was filtered by the custom spam filter option` føjes til meddelelsen. Du kan bruge denne værdi i indbakkeregler eller regler for mailflow (også kaldet transportregler) til at påvirke leveringen af meddelelsen.
  - **Send Bcc-meddelelse (*BccMessage*)**: De angivne mailadresser (parameterværdien *TestModeBccToRecipients* i PowerShell) føjes til Bcc-feltet i meddelelsen, og meddelelsen leveres til de ekstra Bcc-modtagere. På Microsoft 365 Defender-portalen kan du adskille flere mailadresser med semikolon (;). I PowerShell kan du adskille flere mailadresser med kommaer.

  **Noter**:

  - Testtilstanden er ikke tilgængelig for følgende ASF-indstillinger:
    - **Betinget filtrering af afsender-id: mislykket** (*MarkAsSpamFromAddressAuthFail*)
    - **NDR backscatter**(*MarkAsSpamNdrBackscatter*)
    - **SPF-post: hard fail** (*MarkAsSpamSpfRecordHardFail*)
  - Den samme testtilstandshandling anvendes på *alle* ASF-indstillinger, der er angivet til **Test**. Du kan ikke konfigurere forskellige testtilstandshandlinger for forskellige ASF-indstillinger.

## <a name="increase-spam-score-settings"></a>Øg scoreindstillinger for spam

Følgende **Øg spam score** ASF indstillinger indstille spam konfidensniveau (SCL) for registrerede meddelelser til 5 eller 6, hvilket svarer til en **spam** filter dom og den tilsvarende handling i anti-spam politikker.

|Politikindstilling for bekæmpelse af spam|Beskrivelse|X-header tilføjet|
|---|---|---|
|**Billedlinks til eksterne websteder** <p> *IncreaseScoreWithImageLinks*|Meddelelser, der indeholder `<Img>` HTML-kodelinks til fjernwebsteder (f.eks. ved hjælp af http), markeres som spam.|`X-CustomSpam: Image links to remote sites`|
|**Numerisk IP-adresse i URL-adresse** <p> *IncreaseScoreWithNumericIps*|Meddelelser, der indeholder numeriske URL-adresser (typisk IP-adresser), markeres som spam.|`X-CustomSpam: Numeric IP in URL`|
|**OMdirigering af URL-adresse til en anden port** <p> *IncreaseScoreWithRedirecttoOtherPort*|Meddelelse, der indeholder links, der omdirigerer til andre TCP-porte end 80 (HTTP), 8080 (alternativ HTTP) eller 443 (HTTPS), er markeret som spam.|`X-CustomSpam: URL redirect to other port`|
|**Links til .biz- eller .info-websteder** <p> *IncreaseScoreWithBizOrInfoUrls*|Meddelelser, der indeholder `.biz` eller `.info` links i meddelelsens brødtekst, markeres som spam.|`X-CustomSpam: URL to .biz or .info websites`|

## <a name="mark-as-spam-settings"></a>Markér som spamindstillinger

Følgende **Mark as spam** ASF indstillinger indstille SCL af registrerede meddelelser til 9, hvilket svarer til en **Høj tillid spam** filter dom og den tilsvarende handling i anti-spam politikker.

|Politikindstilling for bekæmpelse af spam|Beskrivelse|X-header tilføjet|
|---|---|---|
|**Tomme meddelelser** <p> *MarkAsSpamEmptyMessages*|Meddelelser uden emne, intet indhold i meddelelsens brødtekst og ingen vedhæftede filer er markeret som spam med høj tillid.|`X-CustomSpam: Empty Message`|
|**Integrerede koder i HTML** <p> *MarkAsSpamEmbedTagsInHtml*|Meddelelse, der indeholder `<embed>` HTML-koder, er markeret som spam med høj genkendelsessikkerhed. <p> Dette mærke gør det muligt at integrere forskellige typer dokumenter i et HTML-dokument (f.eks. lyde, videoer eller billeder).|`X-CustomSpam: Embed tag in html`|
|**JavaScript eller VBScript i HTML** <p> *MarkAsSpamJavaScriptInHtml*|Meddelelser, der bruger JavaScript eller Visual Basic Script Edition i HTML, markeres som spam med høj genkendelsessikkerhed. <p> Disse scriptsprog bruges i mails til at forårsage, at bestemte handlinger automatisk forekommer.|`X-CustomSpam: Javascript or VBscript tags in HTML`|
|**Formularkoder i HTML** <p> *MarkAsSpamFormTagsInHtml*|Meddelelser, der indeholder `<form>` HTML-koder, markeres som spam med høj genkendelsessikkerhed. <p> Dette mærke bruges til at oprette webstedsformularer. Mailreklamer inkluderer ofte dette mærke for at hente oplysninger fra modtageren.|`X-CustomSpam: Form tag in html`|
|**Ramme- eller iframe-koder i HTML** <p> *MarkAsSpamFramesInHtml*|Meddelelser, der indeholder `<frame>` eller `<iframe>` HTML-koder, markeres som spam med høj genkendelsessikkerhed. <p> Disse mærker bruges i mails til at formatere siden til visning af tekst eller grafik.|`X-CustomSpam: IFRAME or FRAME in HTML`|
|**Webfejl i HTML** <p> *MarkAsSpamWebBugsInHtml*|En *webfejl* (også kendt som et *webfyr*) er et grafisk element (ofte så lille som en pixel gange en pixel), der bruges i mails til at bestemme, om meddelelsen blev læst af modtageren. <p> Meddelelser, der indeholder webfejl, markeres som spam med høj genkendelsessikkerhed. <p> Legitime nyhedsbreve kan bruge web bugs, selv om mange anser dette for en invasion af privatlivets fred. |`X-CustomSpam: Web bug`|
|**Objektkoder i HTML** <p> *MarkAsSpamObjectTagsInHtml*|Meddelelser, der indeholder `<object>` HTML-koder, markeres som spam med høj genkendelsessikkerhed. <p> Dette mærke gør det muligt for plug-ins eller programmer at køre i et HTML-vindue.|`X-CustomSpam: Object tag in html`|
|**Følsomme ord** <p> *MarkAsSpamSensitiveWordList*|Microsoft vedligeholder en dynamisk, men ikke-redigerbar liste over ord, der er knyttet til potentielt stødende meddelelser. <p> Meddelelser, der indeholder ord fra listen over følsomme ord i emnet eller meddelelsesteksten, markeres som spam med høj tillid.|`X-CustomSpam: Sensitive word in subject/body`|
|**SPF-post: hard fail** <p> *MarkAsSpamSpfRecordHardFail*|Meddelelser, der sendes fra en IP-adresse, som ikke er angivet i SPF's SPF-post (Sender Policy Framework) i DNS for kildemaildomænet, markeres som spam med høj tillid. <p> Testtilstanden er ikke tilgængelig for denne indstilling.|`X-CustomSpam: SPF Record Fail`|

Følgende **Markér som spam** ASF indstillinger indstille SCL af registrerede meddelelser til 6, hvilket svarer til en **Spam** filter dom og den tilsvarende handling i anti-spam politikker.

|Politikindstilling for bekæmpelse af spam|Beskrivelse|X-header tilføjet|
|---|---|---|
|**Det lykkedes ikke at filtrere afsender-id'et** <p> *MarkAsSpamFromAddressAuthFail*|Meddelelser, der mislykkes hårdt, er markeret som spam for en betinget afsender-id-kontrol. <p> Denne indstilling kombinerer en SPF-kontrol med en kontrol af afsender-id for at beskytte mod brevhoveder, der indeholder forfalskede afsendere. <p> Testtilstanden er ikke tilgængelig for denne indstilling.|`X-CustomSpam: SPF From Record Fail`|
|**Tilbagekastning** <p> *MarkAsSpamNdrBackscatter*|*Backscatter* er ubrugelige rapporter om manglende levering (også kendt som NDRs eller bounce-meddelelser) forårsaget af forfalskede afsendere i mails. Du kan få flere oplysninger under [Backscatter-meddelelser og EOP](backscatter-messages-and-eop.md). <p> Du behøver ikke at konfigurere denne indstilling i følgende miljøer, fordi der leveres legitime NDR'er, og backscatter er markeret som spam: <ul><li>Microsoft 365 organisationer med Exchange Online postkasser.</li><li>Mailorganisationer i det lokale miljø, hvor du distribuerer *udgående* mail via EOP.</li></ul> <p> I separate EOP-miljøer, der beskytter indgående mail til postkasser i det lokale miljø, har aktivering eller deaktivering af denne indstilling følgende resultat: <ul><li> **Til**: Legitime NDR'er leveres, og backscatter er markeret som spam.</li><li>**Fra**: Legitime NDRs og backscatter gennemgår normal spamfiltrering. De mest legitime NDR'er leveres til den oprindelige meddelelses afsender. Nogle, men ikke alle, backscatter er markeret som spam. Pr. definition kan backscatter kun leveres til den misvisende afsender og ikke til den oprindelige afsender.</li></ul> <p> Testtilstanden er ikke tilgængelig for denne indstilling.|`X-CustomSpam: Backscatter NDR`|
