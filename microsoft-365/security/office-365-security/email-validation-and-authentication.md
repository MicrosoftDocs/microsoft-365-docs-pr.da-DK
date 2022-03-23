---
title: Mailgodkendelse i Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- Strat_O365_IP
ms.custom: TopSMBIssues
ms.localizationpriority: high
description: Administratorer kan se, hvordan EOP bruger mailgodkendelse (SPF, DKIM og DMARC) til at forhindre spoofing, phishing og spam.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c0e7bc2ddd620b454979418735fb6982b71501c3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63588406"
---
# <a name="email-authentication-in-eop"></a>Mailgodkendelse i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


Mailgodkendelse (også kaldet mailvalidering) er en gruppe af standarder, der forsøger at stoppe spoofing (mails fra forfalskede afsendere). I alle Microsoft 365 bruger EOP disse standarder til at bekræfte indgående mail:

- [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
- [DKIM](use-dkim-to-validate-outbound-email.md)
- [DMARC](use-dmarc-to-validate-email.md)

Mailgodkendelse bekræfter, at mails fra en afsender (f.eks. laura@contoso.com) er legitime og kommer fra forventede kilder for det pågældende maildomæne (f.eks. contoso.com).

I resten af denne artikel forklares det, hvordan disse teknologier fungerer, og hvordan EOP bruger dem til at kontrollere indgående mail.

## <a name="use-email-authentication-to-help-prevent-spoofing"></a>Brug mailgodkendelse til at forhindre spoofing

DMARC forhindrer spoofing ved at undersøge **Fra-adressen** i meddelelser. **Fra-adressen** er afsenderens mailadresse, som brugere kan se i deres mailklient. Destinationens mailorganisationer kan også bekræfte, at maildomænet har bestået SPF eller DKIM. Med andre ord er domænet blevet godkendt, og derfor er afsenderens mailadresse ikke efterlignet.

Dns-poster for SPF, DKIM og DMARC (samlet kaldet mailgodkendelsespolitikker) er dog valgfrie. Domæner med stærke mailgodkendelsespolitikker som f.microsoft.com og skype.com er beskyttet mod spoofing. Men domæner med svage politikker for mailgodkendelse eller slet ingen politik er primære mål for at blive efterlignet.

Pr. marts 2018 publicerer kun 9 % af domænerne for virksomheder i Fortune 500 stærke mailgodkendelsespolitikker. De resterende 91 % af virksomheder kan være efterlignet af en hacker. Medmindre der findes en anden mekanisme til filtrering af mail, kan mails fra efterlignede afsendere på disse domæner blive leveret til brugerne.

![DMARC-politikker for Fortune 500-virksomheder.](../../media/84e77d34-2073-4a8e-9f39-f109b32d06df.jpg)

Forholdet mellem små og mellemstore virksomheder, der publicerer stærke mailgodkendelsespolitikker, er mindre. Og tallet er endnu mindre for maildomæner uden for Nordamerika og Vesteuropa.

Manglende stærke mailgodkendelsespolitikker er et stort problem. Organisationer forstår muligvis ikke, hvordan mailgodkendelse fungerer, men hackere forstår det fuldt ud, og de udnytter dem. På grund af problemer med phishing og den begrænsede anvendelse af stærke politikker for mailgodkendelse bruger Microsoft *implicit mailgodkendelse* til at kontrollere indgående mail.

Implicit mailgodkendelse er en udvidelse af almindelige politikker for mailgodkendelse. Disse udvidelser omfatter: afsenders ry, afsenderhistorik, modtagerhistorik, adfærdsanalyse og andre avancerede teknikker. I fravær af andre signaler fra disse udvidelser markeres meddelelser, der sendes fra domæner, der ikke bruger mailgodkendelsespolitikker, som spoof.

Hvis du vil se Microsofts generelle meddelelse, skal du se [A Sea of Phish Part 2 - Enhanced Anti-spoofing Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Schooling-A-Sea-of-Phish-Part-2-Enhanced-Anti-spoofing/ba-p/176209).

## <a name="composite-authentication"></a>Ikke-farvesepareret godkendelse

Hvis et domæne ikke har traditionelle SPF-, DKIM- og DMARC-poster, kommunikerer disse postkontroller ikke nok godkendelsesstatusoplysninger. Derfor har Microsoft udviklet en algoritme til implicit mailgodkendelse. Denne algoritme kombinerer flere signaler til en enkelt værdi, der _kaldes sammensat godkendelse_, eller `compauth` kort sagt. Værdien `compauth` er stemplet ind i **brevhovedet godkendelse-resultater** i brevhovederne.

```text
Authentication-Results:
   compauth=<fail | pass | softpass | none> reason=<yyy>
```

Disse værdier er forklaret i [brevhovedet med godkendelsesresultater](anti-spam-message-headers.md#authentication-results-message-header).

Ved at undersøge brevhovederne kan administratorer eller endda slutbrugere afgøre, Microsoft 365, om afsenderen er efterlignet.

## <a name="why-email-authentication-is-not-always-enough-to-stop-spoofing"></a>Derfor er mailgodkendelse ikke altid nok til at stoppe spoofing

Hvis du kun er afhængig af mailgodkendelsesposter for at afgøre, om en indgående meddelelse er efterlignet, har følgende begrænsninger:

- Det afsendende domæne mangler muligvis de nødvendige DNS-poster, eller også er posterne konfigureret forkert.

- Kildedomænet har korrekt konfigurerede DNS-poster, men domænet stemmer ikke overens med domænet i Fra-adressen. SPF og DKIM kræver ikke, at domænet bruges i Fra-adressen. Hackere eller legitime tjenester kan registrere et domæne, konfigurere SPF og DKIM for domænet og bruge et helt andet domæne i Fra-adressen. Meddelelser fra afsendere på dette domæne passerer SPF og DKIM.

Sammensat godkendelse kan løse disse begrænsninger ved at sende meddelelser, som ellers ikke ville have kontrolleret mailgodkendelsen.

Følgende eksempler fokuserer på resultater af mailgodkendelse for enkelhed. Andre back-end intelligence-faktorer kan identificere meddelelser, der består mailgodkendelse som efterlignet, eller meddelelser, der mislykkes med mailgodkendelse, som legitime.

Eksempelvis har domænet fabrikam.com SPF, DKIM eller DMARC-poster. Meddelelser fra afsendere i fabrikam.com ikke-sammensat godkendelse (bemærk værdien `compauth` og årsagen):

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=none
  action=none header.from=fabrikam.com; compauth=fail reason=001
From: chris@fabrikam.com
To: michelle@contoso.com
```

Hvis fabrikam.com konfigurerer en SPF uden en DKIM-post, kan meddelelsen bestå ikke-farvesepareret godkendelse. Det domæne, der bestod SPF-kontroller, er justeret med domænet i Fra-adressen:

```text
Authentication-Results: spf=pass (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=bestguesspass
  action=none header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Hvis fabrikam.com konfigurerer en DKIM-post uden en SPF-post, kan meddelelsen bestå sammensat godkendelse. Domænet i DKIM-signaturen er justeret med domænet i Fra-adressen:

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=pass
  (signature was verified) header.d=outbound.fabrikam.com;
  contoso.com; dmarc=bestguesspass action=none
  header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Hvis domænet i SPF eller DKIM-signaturen ikke er justeret efter domænet i Fra-adressen, kan meddelelsen mislykkes sammensat godkendelse:

```text
Authentication-Results: spf=none (sender IP is 192.168.1.8)
  smtp.mailfrom=maliciousdomain.com; contoso.com; dkim=pass
  (signature was verified) header.d=maliciousdomain.com;
  contoso.com; dmarc=none action=none header.from=contoso.com;
  compauth=fail reason=001
From: chris@contoso.com
To: michelle@fabrikam.com
```

## <a name="solutions-for-legitimate-senders-who-are-sending-unauthenticated-email"></a>Løsninger til legitime afsendere, der sender ikke-godkendt mail

Microsoft 365 holder styr på, hvem der sender ikke-godkendte mails til din organisation. Hvis tjenesten mener, at afsenderen ikke er legitim, markeres meddelelser fra denne afsender som en ikke-sammensat godkendelsesfejl. For at undgå denne vurdering kan du bruge anbefalingerne i dette afsnit.

### <a name="configure-email-authentication-for-domains-you-own"></a>Konfigurere mailgodkendelse for domæner, du ejer

Du kan bruge denne metode til at løse spoofing og spoofing på tværs af domæner i tilfælde, hvor du ejer eller interagerer med flere lejere. It also helps resolve cross-domain spoofing where you send to other customers within Microsoft 365 or third parties that are hosted by other providers.

- [Konfigurer SPF-poster](set-up-spf-in-office-365-to-help-prevent-spoofing.md) for dine domæner.
- [Konfigurer DKIM-poster](use-dkim-to-validate-outbound-email.md) for dine primære domæner.
- [Overvej at konfigurere DMARC-poster](use-dmarc-to-validate-email.md) for dit domæne for at fastslå dine legitime afsendere.

Microsoft giver ikke detaljerede retningslinjer for implementering af SPF, DKIM og DMARC-poster. Der er dog mange tilgængelige oplysninger online. Der er også tredjepartsvirksomheder, der er dedikeret til at hjælpe din organisation med at konfigurere mailgodkendelsesposter.

#### <a name="you-dont-know-all-sources-for-your-email"></a>Du kender ikke alle kilder til din mail

Mange domæner publicerer ikke SPF-poster, fordi de ikke kender alle mailkilder for meddelelser på deres domæne. Start med at publicere en SPF-post, der indeholder alle de mailkilder, du kender til (især hvor din virksomheds trafik er placeret), og udgiv den neutrale SPF-politik `?all`. Eksempel:

```text
fabrikam.com IN TXT "v=spf1 include:spf.fabrikam.com ?all"
```

Dette eksempel betyder, at mail fra din virksomheds infrastruktur passerer mailgodkendelse, men mails fra ukendte kilder vil blive neutrale.

Microsoft 365 behandler indgående mail fra virksomhedens infrastruktur som godkendt. Mails fra uidentificerede kilder kan stadig være markeret som spoof, hvis det ikke lykkes med implicit godkendelse. Dette er dog stadig en forbedring i forhold til, at alle mails markeres som spoof af Microsoft 365.

Når du er begyndt at bruge en SPF fallback-politik `?all`for , kan du gradvist finde og medtage flere mailkilder til dine meddelelser og derefter opdatere SPF-posten med en mere restriktiv politik.

### <a name="configure-permitted-senders-of-unauthenticated-email"></a>Konfigurer tilladte afsendere af ikke-godkendt mail

Du kan også bruge [efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt og lejerens tilladelses [-/](tenant-allow-block-list.md) blokeringsliste til at tillade afsendere at sende ikke-godkendte meddelelser til din organisation.

For eksterne domæner er den efterlignede bruger domænet i Fra-adressen, mens den afsendende infrastruktur er enten kilde-IP-adressen (opdelt i /24 CIDR-områder) eller det organisatoriske domæne for den omvendte DNS-post (PTR).

### <a name="create-an-allow-entry-for-the-senderrecipient-pair"></a>Oprette en tilladt post for afsender-/modtagerparret

Hvis du vil omgå spamfiltrering, skal du se nogle dele af filtrering efter phishing, men ikke malwarefiltrering for bestemte afsendere, under Opret lister over afsendere, der er tillid til[, Microsoft 365](create-safe-sender-lists-in-office-365.md).

### <a name="ask-the-sender-to-configure-email-authentication-for-domains-you-dont-own"></a>Bed afsenderen om at konfigurere mailgodkendelse for domæner, du ikke ejer

På grund af problemet med spam og phishing anbefaler Microsoft mailgodkendelse for alle mailorganisationer. I stedet for at konfigurere manuelle tilsidesættelser i din organisation kan du bede en administrator i afsendelsesdomænet om at konfigurere deres mailgodkendelsesposter.

- Selvom de ikke tidligere har brug for at publicere mailgodkendelsesposter, skal de gøre det, hvis de sender mails til Microsoft.

- Konfigurer SPF til at publicere domænets AFSendende IP-adresser, og konfigurer DKIM (hvis det er tilgængeligt) til digitalt at signere meddelelser. De bør også overveje at konfigurere DMARC-poster.

- Hvis de bruger masseafsendere til at sende mail på deres vegne, skal du bekræfte, at domænet i Fra-adressen (hvis det tilhører dem) er justeret efter det domæne, der videregiver SPF eller DMARC.

- Bekræft, at følgende placeringer (hvis de bruger dem) er inkluderet i SPF-posten:

  - Lokale mailservere.
  - Mail sendt fra en Software-as-a-service-udbyder (SaaS).
  - Mail sendt fra en skybaseret værtstjeneste (Microsoft Azure, GoDaddy, Rackspace, Amazon Web Services osv.).

- For mindre domæner, der er hostet af en internetudbyder, skal du konfigurere SPF-posten i overensstemmelse med instruktionerne fra internetudbyderen.

Selvom det kan være svært i første omgang at få afsendelse af domæner til godkendelse, imens flere og flere mailfiltre begynder at uønsket mail eller endda afvise deres mail, medfører det, at de konfigurerer de korrekte poster for at sikre en bedre levering. Deres deltagelse kan også hjælpe i kampen mod phishing, og det kan reducere risikoen for phishing i deres organisation eller organisationer, som de sender mails til.

#### <a name="information-for-infrastructure-providers-isps-esps-or-cloud-hosting-services"></a>Oplysninger til infrastrukturudbydere (internetudbydere, ESP'er eller skyhostingtjenester)

Hvis du hoster et domænes mail eller angiver hostinginfrastruktur, der kan sende mail, skal du gøre følgende:

- Sørg for, at dine kunder har dokumentation, der forklarer, hvordan dine kunder skal konfigurere deres SPF-poster

- Overvej at signere DKIM-signaturer på udgående mails, selvom kunden ikke eksplicit konfigurerer den (signer med et standarddomæne). Du kan endda dobbelttegne mailen med DKIM-signaturer (én gang med kundens domæne, hvis kunden har konfigureret den, og en gang til med din virksomheds DKIM-signatur)

Leverance til Microsoft er ikke garanteret, selvom du godkender mails, der stammer fra din platform, men i det mindste sikrer det, at Microsoft ikke uønsker din mail, fordi den ikke er godkendt.

## <a name="related-links"></a>Relaterede links

Du kan finde flere oplysninger om bedste fremgangsmåder for tjenesteudbydere i [Bedste fremgangsmåder for mobilmeddelelser i M3AAWG for tjenesteudbydere](https://www.m3aawg.org/sites/default/files/m3aawg-mobile-messaging-best-practices-service-providers-2015-08_0.pdf).

Lær, hvordan Office 365 bruger SPF og understøtter DKIM-validering:

- [Mere om SPF](how-office-365-uses-spf-to-prevent-spoofing.md)

- [Mere om DKIM](support-for-validation-of-dkim-signed-messages.md)
