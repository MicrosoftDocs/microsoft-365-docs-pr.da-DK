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
description: Administratorer kan få mere at vide om, hvordan EOP bruger mailgodkendelse (SPF, DKIM og DMARC) til at forhindre spoofing, phishing og spam.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2b0a1f1bec76a8dd22bc04502ea7ca09f2c7af66
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772768"
---
# <a name="email-authentication-in-eop"></a>Mailgodkendelse i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Mailgodkendelse (også kendt som mailvalidering) er en gruppe standarder, der forsøger at stoppe spoofing (mailmeddelelser fra forfalskede afsendere). I alle Microsoft 365 organisationer bruger EOP disse standarder til at bekræfte indgående mail:

- [SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md)
- [DKIM](use-dkim-to-validate-outbound-email.md)
- [DMARC](use-dmarc-to-validate-email.md)

Godkendelse via mail kontrollerer, at mails fra en afsender (f.eks. laura@contoso.com) er legitime og kommer fra forventede kilder for det pågældende maildomæne (f.eks. contoso.com).)

I resten af denne artikel forklares det, hvordan disse teknologier fungerer, og hvordan EOP bruger dem til at tjekke indgående mail.

## <a name="use-email-authentication-to-help-prevent-spoofing"></a>Brug mailgodkendelse som en hjælp til at forhindre spoofing

DMARC forhindrer spoofing ved at undersøge **Fra-adressen** i meddelelser. **Fra-adressen** er afsenderens mailadresse, som brugerne får vist i deres mailklient. Organisationer, der modtager mail, kan også bekræfte, at maildomænet har bestået SPF eller DKIM. Med andre ord er domænet godkendt, og afsenderens mailadresse er derfor ikke spoofed.

DNS-poster for SPF, DKIM og DMARC (samlet kaldet politikker for mailgodkendelse) er dog valgfrie. Domæner med stærke politikker til godkendelse af mail, f.eks. microsoft.com og skype.com, er beskyttet mod spoofing. Men domæner med svagere politikker til godkendelse af mail eller slet ingen politik er primære mål for spoofed.

Fra marts 2018 publicerer kun 9 % af domænerne i virksomheder i Fortune 500 stærke politikker for mailgodkendelse. De resterende 91 % af virksomhederne kan blive misvisende af en hacker. Medmindre en anden mekanisme til filtrering af mail er på stedet, kan mail fra forfalskede afsendere i disse domæner blive leveret til brugerne.

![DMARC politikker fortune 500 virksomheder.](../../media/84e77d34-2073-4a8e-9f39-f109b32d06df.jpg)

Andelen af små til mellemstore virksomheder, der publicerer stærke politikker for mailgodkendelse, er mindre. Og antallet er endnu mindre for maildomæner uden for Nordamerika og Vesteuropa.

Mangel på stærke politikker til godkendelse af mail er et stort problem. Organisationer forstår muligvis ikke, hvordan mailgodkendelse fungerer, men personer med ondsindede hensigter forstår det fuldt ud, og de drager fordel af det. På grund af phishing-bekymringer og den begrænsede indførelse af stærke politikker for godkendelse af mail bruger Microsoft *implicit mailgodkendelse* til at kontrollere indgående mail.

Implicit mailgodkendelse er en udvidelse af almindelige politikker for godkendelse af mail. Disse udvidelser omfatter: afsenderens omdømme, afsenderhistorik, modtagerhistorik, adfærdsanalyse og andre avancerede teknikker. Hvis der ikke er andre signaler fra disse udvidelser, markeres meddelelser, der sendes fra domæner, der ikke bruger politikker for godkendelse af mail, som spoof.

Hvis du vil se Microsofts generelle meddelelse, skal du se [Et hav af Phish Part 2 – Enhanced Anti-spoofing i Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Schooling-A-Sea-of-Phish-Part-2-Enhanced-Anti-spoofing/ba-p/176209).

## <a name="composite-authentication"></a>Sammensat godkendelse

Hvis et domæne ikke har traditionelle SPF-, DKIM- og DMARC-poster, kommunikerer disse kontrol af poster ikke tilstrækkelige oplysninger om godkendelsesstatus. Derfor har Microsoft udviklet en algoritme til implicit mailgodkendelse. Denne algoritme kombinerer flere signaler til en enkelt værdi kaldet _sammensat godkendelse_ eller `compauth` kort sagt. Værdien `compauth` stemples i headeren **Authentication-Results** i brevhovederne.

```text
Authentication-Results:
   compauth=<fail | pass | softpass | none> reason=<yyy>
```

Disse værdier er forklaret i [meddelelsens overskrift med godkendelsesresultater](anti-spam-message-headers.md#authentication-results-message-header).

Ved at undersøge brevhovederne kan administratorer eller endda slutbrugere afgøre, hvordan Microsoft 365 fastslået, at afsenderen er spoofed.

## <a name="why-email-authentication-is-not-always-enough-to-stop-spoofing"></a>Hvorfor mailgodkendelse ikke altid er nok til at stoppe spoofing

Der er følgende begrænsninger, hvis du kun er afhængig af mailgodkendelsesposter for at afgøre, om en indgående meddelelse er forfalsket:

- Det afsendende domæne mangler muligvis de påkrævede DNS-poster, eller posterne er konfigureret forkert.

- Kildedomænet har konfigureret DNS-poster korrekt, men det pågældende domæne stemmer ikke overens med domænet i fra-adressen. SPF og DKIM kræver ikke, at domænet bruges i Fra-adressen. Personer med ondsindede hensigter eller legitime tjenester kan registrere et domæne, konfigurere SPF og DKIM for domænet og bruge et helt andet domæne i fra-adressen. Meddelelser fra afsendere i dette domæne overføres til SPF og DKIM.

Sammensat godkendelse kan løse disse begrænsninger ved at sende meddelelser, der ellers ikke kan godkende mailgodkendelse.

For nemheds skyld koncentrerer følgende eksempler sig om resultater af mailgodkendelse. Andre back end-intelligensfaktorer kan identificere meddelelser, der sender mailgodkendelse som spoofed, eller meddelelser, der ikke kan godkende via mail, som legitime.

Det fabrikam.com domæne har f.eks. ingen SPF-, DKIM- eller DMARC-poster. Meddelelser fra afsendere i det fabrikam.com domæne kan mislykkes med sammensat godkendelse (bemærk `compauth` værdien og årsagen):

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=none
  action=none header.from=fabrikam.com; compauth=fail reason=001
From: chris@fabrikam.com
To: michelle@contoso.com
```

Hvis fabrikam.com konfigurerer en SPF uden en DKIM-post, kan meddelelsen bestå sammensat godkendelse. Det domæne, der har bestået SPF-kontroller, er justeret i forhold til domænet i fra-adressen:

```text
Authentication-Results: spf=pass (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=none
  (message not signed) header.d=none; contoso.com; dmarc=bestguesspass
  action=none header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Hvis fabrikam.com konfigurerer en DKIM-post uden en SPF-post, kan meddelelsen bestå sammensat godkendelse. Domænet i DKIM-signaturen er justeret i forhold til domænet i Fra-adressen:

```text
Authentication-Results: spf=none (sender IP is 10.2.3.4)
  smtp.mailfrom=fabrikam.com; contoso.com; dkim=pass
  (signature was verified) header.d=outbound.fabrikam.com;
  contoso.com; dmarc=bestguesspass action=none
  header.from=fabrikam.com; compauth=pass reason=109
From: chris@fabrikam.com
To: michelle@contoso.com
```

Hvis domænet i SPF eller DKIM-signaturen ikke stemmer overens med domænet i fra-adressen, kan meddelelsen mislykkes med sammensat godkendelse:

```text
Authentication-Results: spf=none (sender IP is 192.168.1.8)
  smtp.mailfrom=maliciousdomain.com; contoso.com; dkim=pass
  (signature was verified) header.d=maliciousdomain.com;
  contoso.com; dmarc=none action=none header.from=contoso.com;
  compauth=fail reason=001
From: chris@contoso.com
To: michelle@fabrikam.com
```

## <a name="solutions-for-legitimate-senders-who-are-sending-unauthenticated-email"></a>Løsninger til legitime afsendere, der sender ikke-godkendte mails

Microsoft 365 holder styr på, hvem der sender ikke-godkendte mails til din organisation. Hvis tjenesten mener, at afsenderen ikke er gyldig, markeres meddelelser fra denne afsender som en sammensat godkendelsesfejl. For at undgå denne dom kan du bruge anbefalingerne i dette afsnit.

### <a name="configure-email-authentication-for-domains-you-own"></a>Konfigurer mailgodkendelse for domæner, du ejer

Du kan bruge denne metode til at løse spoofing inden for organisationen og spoofing på tværs af domæner i tilfælde, hvor du ejer eller interagerer med flere lejere. Det hjælper også med at løse spoofing på tværs af domæner, hvor du sender til andre kunder i Microsoft 365 eller tredjeparter, der hostes af andre udbydere.

- [Konfigurer SPF-poster](set-up-spf-in-office-365-to-help-prevent-spoofing.md) for dine domæner.
- [Konfigurer DKIM-poster](use-dkim-to-validate-outbound-email.md) for dine primære domæner.
- [Overvej at konfigurere DMARC-poster](use-dmarc-to-validate-email.md) for dit domæne for at bestemme dine legitime afsendere.

Microsoft giver ikke detaljerede retningslinjer for implementering af SPF-, DKIM- og DMARC-poster. Der er dog mange tilgængelige oplysninger online. Der er også tredjepartsfirmaer, der er dedikeret til at hjælpe din organisation med at konfigurere godkendelsesposter via mail.

#### <a name="you-dont-know-all-sources-for-your-email"></a>Du kender ikke alle kilder til din mail

Mange domæner publicerer ikke SPF-poster, fordi de ikke kender alle mailkilderne til meddelelser i deres domæne. Start med at publicere en SPF-post, der indeholder alle de mailkilder, du kender til (især hvor din virksomhedstrafik er placeret), og publicer den neutrale SPF-politik `?all`. Eksempel:

```text
fabrikam.com IN TXT "v=spf1 include:spf.fabrikam.com ?all"
```

Dette eksempel betyder, at mail fra din virksomheds infrastruktur vil bestå mailgodkendelse, men mail fra ukendte kilder går tilbage til neutral.

Microsoft 365 behandler indgående mail fra virksomhedens infrastruktur som godkendt. Mail fra uidentificerede kilder kan stadig være markeret som spoof, hvis det mislykkes implicit godkendelse. Dette er dog stadig en forbedring i forhold til alle mails, der markeres som spoof af Microsoft 365.

Når du er kommet i gang med en FALLBACK-politik for `?all`SPF, kan du gradvist finde og inkludere flere mailkilder til dine meddelelser og derefter opdatere din SPF-post med en strengere politik.

### <a name="configure-permitted-senders-of-unauthenticated-email"></a>Konfigurer tilladte afsendere af ikke-godkendte mails

Du kan også bruge [indsigt i spoof intelligence](learn-about-spoof-intelligence.md) og [lejerens tilladelses-/blokliste](tenant-allow-block-list.md) til at give afsendere tilladelse til at sende ikke-godkendte meddelelser til din organisation.

For eksterne domæner er den spoofede bruger domænet i fra-adressen, mens den afsendende infrastruktur er en af følgende værdier:

- Kildens IP-adresse (opdelt i /24 CIDR-intervaller)
- Organisationsdomænet for den omvendte DNS-post (PTR).
- Et bekræftet DKIM-domæne.

### <a name="create-an-allow-entry-for-the-senderrecipient-pair"></a>Opret en tilladelsesindtastning for afsender-/modtagerparret

Hvis du vil omgå filtrering af spam, kan du se nogle dele af filtrering til phishing, men ikke malwarefiltrering for bestemte afsendere, under [Opret lister over sikre afsendere i Microsoft 365](create-safe-sender-lists-in-office-365.md).

### <a name="ask-the-sender-to-configure-email-authentication-for-domains-you-dont-own"></a>Bed afsenderen om at konfigurere mailgodkendelse for domæner, du ikke ejer

På grund af problemet med spam og phishing anbefaler Microsoft godkendelse af mail for alle mailorganisationer. I stedet for at konfigurere manuelle tilsidesættelser i din organisation kan du bede en administrator i det sendende domæne om at konfigurere deres mailgodkendelsesposter.

- Selvom de ikke tidligere har brug for at publicere godkendelsesposter for mail, skal de gøre det, hvis de sender mail til Microsoft.

- Konfigurer SPF til at publicere domænets afsendende IP-adresser, og konfigurer DKIM (hvis det er muligt) til digitalt at signere meddelelser. De bør også overveje at oprette DMARC-poster.

- Hvis de bruger masseafsendere til at sende mail på deres vegne, skal du bekræfte, at domænet i fra-adressen (hvis det tilhører dem) er i overensstemmelse med det domæne, der passerer SPF eller DMARC.

- Kontrollér, at følgende placeringer (hvis de bruger dem) er inkluderet i SPF-posten:

  - Mailservere i det lokale miljø.
  - Mail sendt fra en SaaS-udbyder (software-as-a-service).
  - Mail sendt fra en cloudhostingtjeneste (Microsoft Azure, GoDaddy, Rackspace, Amazon Web Services osv.).

- For små domæner, der hostes af en internetudbyder, skal du konfigurere SPF-posten i henhold til instruktionerne fra internetudbyderen.

Selvom det kan være svært i første omgang at få afsendelse af domæner til at godkende, vil det med tiden, efterhånden som flere og flere mailfiltre begynder at junke eller endda afvise deres e-mail, få dem til at konfigurere de korrekte poster for at sikre bedre levering. Deres deltagelse kan også hjælpe med at bekæmpe phishing og kan reducere muligheden for phishing i deres organisation eller organisationer, som de sender mail til.

#### <a name="information-for-infrastructure-providers-isps-esps-or-cloud-hosting-services"></a>Oplysninger til infrastrukturudbydere (internetudbydere, ESP'er eller cloudhostingtjenester)

Hvis du hoster et domænes mail eller leverer hostinginfrastruktur, der kan sende mail, skal du gøre følgende:

- Sørg for, at dine kunder har dokumentation, der forklarer, hvordan dine kunder skal konfigurere deres SPF-poster

- Overvej at signere DKIM-signaturer på udgående mail, selvom kunden ikke eksplicit konfigurerer den (tilmeld dig med et standarddomæne). Du kan endda dobbelttegne mailen med DKIM-signaturer (én gang med kundens domæne, hvis kunden har sat det op, og en anden gang med din virksomheds DKIM-signatur)

Levering til Microsoft garanteres ikke, selvom du godkender mail, der stammer fra din platform, men det sikrer i det mindste, at Microsoft ikke uønsket mail, fordi den ikke er godkendt.

## <a name="related-links"></a>Relaterede links

Du kan få flere oplysninger om bedste praksis for tjenesteudbydere under [Bedste praksis for M3AAWG-mobilbeskeder for tjenesteudbydere](https://www.m3aawg.org/sites/default/files/m3aawg-mobile-messaging-best-practices-service-providers-2015-08_0.pdf).

Få mere at vide om, hvordan Office 365 bruger SPF og understøtter DKIM-validering:

- [Mere om SPF](how-office-365-uses-spf-to-prevent-spoofing.md)

- [Mere om DKIM](support-for-validation-of-dkim-signed-messages.md)
