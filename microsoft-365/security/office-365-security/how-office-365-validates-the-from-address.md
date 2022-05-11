---
title: Sådan validerer EOP Fra-adressen for at forhindre phishing
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- OWC150
- MET150
ms.assetid: eef8408b-54d3-4d7d-9cf7-ad2af10b2e0e
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om de typer mailadresser, der accepteres eller afvises af Exchange Online Protection (EOP) og Outlook.com for at forhindre phishing.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c8b9fb5c9e2b67a656948684838b61b4a9c33a8d
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319544"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Sådan validerer EOP Fra-adressen for at forhindre phishing

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Phishingangreb er en konstant trussel mod enhver mailorganisation. Ud over at bruge [forfalskede (forfalskede) afsendermailadresser](anti-spoofing-protection.md) bruger hackere ofte værdier i fra-adressen, der overtræder internetstandarderne. For at forhindre denne type phishing kræver Exchange Online Protection (EOP) og Outlook.com nu indgående meddelelser at inkludere en RFC-kompatibel From-adresse, som beskrevet i denne artikel. Denne håndhævelse blev aktiveret i november 2017.

**Noter**:

- Hvis du jævnligt modtager mail fra organisationer, der har forkert udformet Fra-adresser som beskrevet i denne artikel, skal du opfordre disse organisationer til at opdatere deres mailservere for at overholde moderne sikkerhedsstandarder.

- Det relaterede felt Afsender (bruges af Send på vegne og adresselister) påvirkes ikke af disse krav. Du kan finde flere oplysninger i følgende blogindlæg: [Hvad mener vi, når vi refererer til "afsenderen" af en mail?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email).

## <a name="an-overview-of-email-message-standards"></a>En oversigt over standarder for mails

En standard-SMTP-mail består af en *meddelelseskonvolut* og meddelelsesindhold. Meddelelseskonvolutten indeholder oplysninger, der kræves for at sende og levere meddelelsen mellem SMTP-servere. Meddelelsesindholdet indeholder brevhovedfelter (samlet kaldet *meddelelsesoverskriften*) og meddelelsens brødtekst. Meddelelseskonvolutten er beskrevet i [RFC 5321](https://tools.ietf.org/html/rfc5321), og brevhovedet er beskrevet i [RFC 5322](https://tools.ietf.org/html/rfc5322). Modtagerne får aldrig vist den faktiske meddelelseskonvolut, fordi den genereres af meddelelsesoverførselsprocessen, og den er faktisk ikke en del af meddelelsen.

- Adressen `5321.MailFrom` (også kendt som **MAIL FROM-adresse** , P1-afsender eller konvolut afsender) er den mailadresse, der bruges i SMTP-overførslen af meddelelsen. Denne mailadresse registreres typisk i headerfeltet **Return-Path** i meddelelsesoverskriften (selvom det er muligt for afsenderen at angive en anden mailadresse for **returstien** ).

- `5322.From` (også kendt som Fra-adressen eller P2-afsenderen) er mailadressen i headerfeltet **Fra** og er afsenderens mailadresse, der vises i mailklienter. Fra-adressen er i fokus i kravene i denne artikel.

Fra-adressen er defineret detaljeret på tværs af flere RFC'er (f.eks. RFC 5322 afsnit 3.2.3, 3.4 og 3.4.1 og [RFC 3696](https://tools.ietf.org/html/rfc3696)). Der er mange variationer af adressering, og hvad der anses for at være gyldigt eller ugyldigt. For at gøre det enkelt anbefaler vi følgende format og definitioner:

`From: "Display Name" <EmailAddress>`

- **Vist navn**: Et valgfrit udtryk, der beskriver ejeren af mailadressen.

  - Vi anbefaler, at du altid omslutter det viste navn med dobbelte anførselstegn (") som vist. Hvis det viste navn indeholder et komma, _skal_ du omslutte strengen med dobbelte anførselstegn pr. RFC 5322.
  - Hvis Fra-adressen indeholder et vist navn, skal værdien EmailAddress være omsluttet af vinkelparenteser (< >) som vist.
  - Microsoft anbefaler på det kraftigste, at du indsætter et mellemrum mellem det viste navn og mailadressen.

- **EmailAddress**: En mailadresse bruger formatet `local-part@domain`:

  - **local-part**: En streng, der identificerer den postkasse, der er knyttet til adressen. Denne værdi er entydig i domænet. Postkasseejerens brugernavn eller GUID bruges ofte.
  - **domain**: Det fuldt kvalificerede domænenavn (FQDN) for den mailserver, der hoster den postkasse, der er identificeret af den lokale del af mailadressen.

  Dette er nogle yderligere overvejelser i forbindelse med værdien EmailAddress:

  - Kun én mailadresse.
  - Det anbefales, at du ikke adskiller vinkelparenteser med mellemrum.
  - Medtag ikke yderligere tekst efter mailadressen.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Eksempler på gyldige og ugyldige From-adresser

Følgende fra mailadresser er gyldige:

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Anbefales ikke, fordi der er mellemrum mellem vinkelparenteserne og mailadressen).

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Anbefales ikke, fordi det viste navn ikke er omsluttet af dobbelte anførselstegn).

Følgende fra mailadresser er ugyldige:

- **Ingen fra-adresse**: Nogle automatiserede meddelelser indeholder ikke en Fra-adresse. Når Microsoft 365 eller Outlook.com tidligere modtog en meddelelse uden en Fra-adresse, tilføjede tjenesten følgende standard fra: adresse for at gøre meddelelsen leverancen:

  `From: <>`

  Nu accepteres meddelelser med en tom From-adresse ikke længere.

- `From: Microsoft 365 sender@contoso.com` (Det viste navn findes, men mailadressen er ikke omsluttet af vinkelparenteser).

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (Tekst efter mailadressen).

- `From: Sender, Example <sender.example@contoso.com>` Det viste navn indeholder et komma, men er ikke omsluttet af dobbelte anførselstegn.

- `From: "Microsoft 365 <sender@contoso.com>"` (Hele værdien er forkert omsluttet af dobbelte anførselstegn).

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` (Det viste navn findes, men mailadressen er ikke omsluttet af vinkelparenteser).

- `From: Microsoft 365<sender@contoso.com>` (Der er ikke mellemrum mellem det viste navn og den venstre vinkelparentes).

- `From: "Microsoft 365"<sender@contoso.com>` (Der er ikke mellemrum mellem det afsluttende dobbelte anførselstegn og den venstre vinkelparentes).

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Ignorer autosvar til dit brugerdefinerede domæne

Du kan ikke bruge værdien `From: <>` til at undertrykke autosvar. Du skal i stedet konfigurere en MX-post, der er null, for dit brugerdefinerede domæne. Autosvar (og alle svar) undertrykkes naturligt, fordi der ikke er nogen publiceret adresse, som den besvarende server kan sende meddelelser til.

- Vælg et maildomæne, der ikke kan modtage mail. Hvis dit primære domæne f.eks. er contoso.com, kan du vælge noreply.contoso.com.

- MX-posten, der er null for dette domæne, består af en enkelt periode.

Eksempel:

```text
noreply.contoso.com IN MX .
```

Du kan få flere oplysninger om konfiguration af [MX-poster under Opret DNS-poster hos enhver DNS-hostingudbyder for Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Du kan få flere oplysninger om publicering af en MX-null-værdi under [RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Tilsidesæt fra håndhævelse af adresse

Hvis du vil tilsidesætte fra-adressekravene for indgående mail, kan du bruge IP-tilladelseslisten (forbindelsesfiltrering) eller regler for mailflow (også kaldet transportregler) som beskrevet i [Opret sikre afsenderlister i Microsoft 365](create-safe-sender-lists-in-office-365.md).

Du kan ikke tilsidesætte fra-adressekravene for udgående mails, som du sender fra Microsoft 365. Derudover tillader Outlook.com ikke tilsidesættelser af nogen art, heller ikke via support.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Andre måder at forebygge og beskytte mod cyberkriminelle på i Microsoft 365

Du kan finde flere oplysninger om, hvordan du kan styrke din organisation mod phishing, spam, brud på datasikkerheden og andre trusler, i [Bedste praksis for sikring af Microsoft 365 til virksomhedsplaner](../../admin/security-and-compliance/secure-your-business-data.md).
