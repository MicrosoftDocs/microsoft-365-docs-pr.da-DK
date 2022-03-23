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
ms.openlocfilehash: 412b6eb7045051c21a88c8b4b2ba5e80a06832dd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587704"
---
# <a name="how-eop-validates-the-from-address-to-prevent-phishing"></a>Sådan validerer EOP Fra-adressen for at forhindre phishing

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Phishing-angreb er en konstant trussel mod enhver mailorganisation. Ud over at bruge [falske (forfalskede)](anti-spoofing-protection.md) afsendermailadresser bruger hackere ofte værdier i Fra-adressen, der overtræder internetstandarderne. For at forhindre denne type phishing kræver Exchange Online Protection (EOP) og Outlook.com nu indgående meddelelser for at medtage en RFC-kompatibel Fra-adresse som beskrevet i denne artikel. Håndhævelsen blev aktiveret i november 2017.

**Bemærkninger**:

- Hvis du jævnligt modtager mails fra organisationer, der har forkert udformet Fra-adresser som beskrevet i denne artikel, skal du opfordre disse organisationer til at opdatere deres mailservere til at overholde moderne sikkerhedsstandarder.

- Det relaterede Afsender-felt (som bruges af Send på vegne af og adresselister) påvirkes ikke af disse krav. Du kan finde flere oplysninger i følgende blogindlæg: Hvad betyder vi, når vi henviser til ["afsenderen" af en mail?](/archive/blogs/tzink/what-do-we-mean-when-we-refer-to-the-sender-of-an-email).

## <a name="an-overview-of-email-message-standards"></a>En oversigt over mailstandarder

En standard-SMTP-mail består af en konvolut *og* meddelelsesindhold. Konvolutten indeholder oplysninger, der er nødvendige for at sende og levere meddelelsen mellem SMTP-servere. Meddelelsesindholdet indeholder brevhovedfelter (samlet kaldet *brevhovedet*) og meddelelsens brødtekst. Konvolutten er beskrevet i [RFC 5321](https://tools.ietf.org/html/rfc5321), og brevhovedet er beskrevet i [RFC 5322](https://tools.ietf.org/html/rfc5322). Modtagerne får aldrig vist den faktiske konvolut, fordi den genereres af meddelelsesprocessen, og den er faktisk ikke en del af meddelelsen.

- Adressen `5321.MailFrom` (også kaldet **MAIL FROM-adressen** , P1-afsenderen eller konvolutafsenderen) er den mailadresse, der bruges i SMTP-afsendelsen af meddelelsen. Denne mailadresse registreres typisk i feltet Med retursti i brevhovedet (selvom afsenderen kan angive en anden  **Retursti-mailadresse**).

- (også kaldet Fra-adressen eller P2-afsenderen) er mailadressen i feltet Fra og  er afsenderens mailadresse, der vises i mailklienter.`5322.From` Fokus er på Fra-adressen i denne artikel.

Fra-adressen er defineret detaljeret på tværs af flere RFC'er (f.eks. afsnit 3.2.3, 3.4 og 3.4.1 og [RFC 3696](https://tools.ietf.org/html/rfc3696)). Der er mange variationer af adresser, og hvad der betragtes som gyldige eller ugyldige. For at gøre det enkelt anbefaler vi følgende format og definitioner:

`From: "Display Name" <EmailAddress>`

- **Vist navn**: En valgfri sætning, der beskriver ejeren af mailadressen.

  - Vi anbefaler, at du altid omgiver det viste navn med dobbelte anførselstegn (") som vist. Hvis det viste navn indeholder et komma, skal _du omslutte_ strengen med dobbelte anførselstegn pr. RFC 5322.
  - Hvis Fra-adressen indeholder et vist navn, skal værdien Mailadresse være omsluttet af vinkelparenteser (< >), som vist.
  - Microsoft anbefaler på det kraftigste, at du indsætter et mellemrum mellem det viste navn og mailadressen.

- **Mailadresse**: En mailadresse bruger formatet `local-part@domain`:

  - **lokal del**: En streng, der identificerer den postkasse, der er knyttet til adressen. Denne værdi er entydig inden for domænet. Ofte bruges postkasseejerens brugernavn eller GUID.
  - **domæne**: Det fulde domænenavn på den mailserver, der hoster postkassen, som er identificeret af den lokale del af mailadressen.

  Dette er nogle yderligere overvejelser i forbindelse med værdien EmailAddress:

  - Kun én mailadresse.
  - Vi anbefaler, at du ikke adskiller vinkelparenteserne med mellemrum.
  - Medtag ikke yderligere tekst efter mailadressen.

## <a name="examples-of-valid-and-invalid-from-addresses"></a>Eksempler på gyldige og ugyldige Fra-adresser

Følgende Fra-mailadresser er gyldige:

- `From: sender@contoso.com`

- `From: <sender@contoso.com>`

- `From: < sender@contoso.com >` (Anbefales ikke, fordi der er mellemrum mellem vinkelparenteserne og mailadressen).

- `From: "Sender, Example" <sender.example@contoso.com>`

- `From: "Microsoft 365" <sender@contoso.com>`

- `From: Microsoft 365 <sender@contoso.com>` (Det anbefales ikke, fordi det viste navn ikke er omsluttet af dobbelte anførselstegn).

Følgende Fra-mailadresser er ugyldige:

- **Nej fra-adresse**: Nogle automatiserede meddelelser indeholder ikke en Fra-adresse. Tidligere, da Microsoft 365 eller Outlook.com modtog en meddelelse uden en Fra-adresse, tilføjede tjenesten følgende standard Fra:-adresse for at gøre meddelelsen leverance:

  `From: <>`

  Meddelelser med en tom Fra-adresse accepteres ikke længere.

- `From: Microsoft 365 sender@contoso.com` Det viste navn er til stede, men mailadressen er ikke omsluttet af vinkelparenteser.

- `From: "Microsoft 365" <sender@contoso.com> (Sent by a process)` (Tekst efter mailadressen).

- `From: Sender, Example <sender.example@contoso.com>` Det viste navn indeholder et komma, men er ikke omsluttet af dobbelte anførselstegn.

- `From: "Microsoft 365 <sender@contoso.com>"` Hele værdien er fejlagtigt omsluttet af dobbelte anførselstegn.

- `From: "Microsoft 365 <sender@contoso.com>" sender@contoso.com` Det viste navn er til stede, men mailadressen er ikke omsluttet af vinkelparenteser.

- `From: Microsoft 365<sender@contoso.com>` (Der er ingen afstand mellem visningsnavnet og den venstre vinkelparentes).

- `From: "Microsoft 365"<sender@contoso.com>` (Der er ingen afstand mellem det sidste dobbelte anførselstegn og venstre vinkelparentes).

## <a name="suppress-auto-replies-to-your-custom-domain"></a>Skjule autosvar til dit brugerdefinerede domæne

Du kan ikke bruge værdien til at `From: <>` undertrykke autosvar. I stedet skal du konfigurere en null MX-post for dit brugerdefinerede domæne. Autosvar (og alle svar) er helt naturligt undertrykket, fordi der ikke er nogen publiceret adresse, som den besvarende server kan sende meddelelser til.

- Vælg et maildomæne, der ikke kan modtage mail. Hvis dit primære domæne f.eks. er contoso.com, kan du vælge noreply.contoso.com.

- Null MX-posten for dette domæne består af et enkelt punktum.

Eksempel:

```text
noreply.contoso.com IN MX .
```

Du kan finde flere oplysninger om konfiguration af MX-poster under [Oprette DNS-poster for alle DNS-udbydere Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

Du kan finde flere oplysninger om at publicere en null-MX [i RFC 7505](https://tools.ietf.org/html/rfc7505).

## <a name="override-from-address-enforcement"></a>Tilsidesæt håndhævelse af Fra-adresse

Hvis du vil tilsidesætte Fra-adressekravene for indgående mail, kan du bruge IP-tilladelseslisten (forbindelsesfiltrering) eller regler for mailflow (også kaldet transportregler), som beskrevet i Opret lister over afsendere, der er tillid til[, i Microsoft 365](create-safe-sender-lists-in-office-365.md).

Du kan ikke tilsidesætte Fra-adressekravene for udgående mails, du sender fra Microsoft 365. Desuden tillader Outlook.com ikke tilsidesættelser af nogen art, selv via support.

## <a name="other-ways-to-prevent-and-protect-against-cybercrimes-in-microsoft-365"></a>Andre måder at forebygge og beskytte mod cyberkriminiske problemer på Microsoft 365

Du kan finde flere oplysninger om, hvordan du kan styrke din organisation mod phishing, spam, databribriser og andre trusler, i [Top 10-metoder til at sikre Microsoft 365 for business-planer](../../admin/security-and-compliance/secure-your-business-data.md).