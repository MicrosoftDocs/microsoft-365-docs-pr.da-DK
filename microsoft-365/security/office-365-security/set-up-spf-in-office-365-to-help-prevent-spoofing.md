---
title: Konfigurer SPF for at forhindre spoofing
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du opdaterer en DNS-post (Domain Name Service) til at bruge SPF (Sender Policy Framework) med dit brugerdefinerede domæne Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab7bd0e579bfe26236eb009dc09689ddb90f2782
ms.sourcegitcommit: 43adb0d91af234c34e22d450a9c1d26aa745c2ca
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/19/2021
ms.locfileid: "63589180"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Konfigurer SPF for at forhindre spoofing

- [Forudsætninger](#prerequisites)
- [Opret eller opdater SPF TXT-posten](#create-or-update-your-spf-txt-record)
- [Hvordan håndteres underdomæner?](#how-to-handle-subdomains)
- [Fejlfinding af SPF](#troubleshooting-spf)

<!--
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

I denne artikel beskrives det, hvordan du opdaterer en DNS-post (Domain Name Service), så du kan bruge SPF (Sender Policy Framework)-mailgodkendelse med dit brugerdefinerede domæne i Office 365.

SPF hjælper med *at validere* udgående mails, der sendes fra dit brugerdefinerede domæne (kommer fra den, der siger det). Det er første trin i konfigurationen af de fulde anbefalede mailgodkendelsesmetoder for SPF, [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md).

- [Forudsætninger](#prerequisites)
- [Opret eller opdater SPF TXT-posten](#create-or-update-your-spf-txt-record)
  - [Hvordan håndteres underdomæner?](#how-to-handle-subdomains)
- [Hvad gør SPF-mailgodkendelse faktisk?](#what-does-spf-email-authentication-actually-do)
  - [Fejlfinding af SPF](#troubleshooting-spf)
- [Flere oplysninger om SPF](#more-information-about-spf)

## <a name="prerequisites"></a>Forudsætninger

> [!IMPORTANT]
> Hvis du er en **lille virksomhed, eller** du ikke er bekendt med IP-adresser eller DNS-konfiguration, skal du ringe til din internetdomæneegistrator (f.eks. GoDaddy, Bluehost, web.com) & bede om hjælp til *DNS-konfiguration af SPF* (og enhver anden mailgodkendelsesmetode). <p> **Hvis du** ikke bruger en brugerdefineret URL-adresse (og den URL-adresse, der bruges til Office 365 slutter med **onmicrosoft.com**), er SPF allerede blevet konfigureret for dig i Office 365 tjeneste.

Lad os komme i gang.

SPF TXT-posten for Office 365 oprettes i ekstern DNS for eventuelle brugerdefinerede domæner eller underdomæner. Du skal bruge nogle oplysninger for at lave posten. Saml disse oplysninger:

- SPF TXT-posten for dit brugerdefinerede domæne, hvis der findes et. Du kan finde en vejledning [i Indsamle de oplysninger, du skal bruge til at Office 365 DNS-poster](../../admin/get-help-with-domains/information-for-dns-records.md).

- Gå til dine meddelelsesserver(e), og find de eksterne IP-adresser (skal bruges af alle lokale meddelelsesservere). Eksempel: **131.107.2.200**.

- Domænenavne, der skal bruges til alle tredjepartsdomæner, som du skal medtage i din SPF TXT-post. Nogle massemailudbydere har konfigureret underdomæner til brug for deres kunder. Firmaet MailChimp har f.eks. konfigureret **servers.mcsv.net**.

- Find ud af, hvilken håndhævelsesregel du vil bruge til SPF TXT-posten. Reglen **-alle** anbefales. Du kan finde detaljerede oplysninger om andre syntaksindstillinger i [syntaksen for SPF TXT-post Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> For at kunne bruge et brugerdefineret domæne kræver Office 365, at du føjer en SPF (Sender Policy Framework) TXT-post til din DNS-post for at forhindre spoofing.

## <a name="create-or-update-your-spf-txt-record"></a>Opret eller opdater SPF TXT-posten

1. Sørg for, at du kender SPF-syntaksen i følgende tabel.

    <br>

    ****

    |Element|Hvis du bruger...|Er det almindeligt for kunder?|Tilføj dette...|
    |---|---|---|---|
    |1|Ethvert mailsystem (påkrævet)|Almindeligt. Alle SPF TXT-poster starter med denne værdi|`v=spf1`|
    |2|Exchange Online|Almindeligt|`include:spf.protection.outlook.com`|
    |3|Exchange Online dedikeret kun|Ikke almindeligt|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Germany, kun Microsoft Cloud Germany|Ikke almindeligt|`include:spf.protection.outlook.de`|
    |5|Tredjepartsmailsystem|Ikke almindeligt|`include:<domain_name>` <p> \<domain_name\> er domænet for tredjepartsmailsystemet.|
    |6|Lokalt mailsystem. Eksempelvis kan Exchange Online Protection plus et andet mailsystem|Ikke almindeligt|Brug en af disse til hvert ekstra mailsystem: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> og \<domain_name\> er IP-adressen og domænet for det andet mailsystem, der sender mail på vegne af dit domæne.|
    |7|Ethvert mailsystem (påkrævet)|Almindeligt. Alle SPF TXT-poster slutter med denne værdi|`<enforcement rule>` <p> Dette kan være en af flere værdier. Vi anbefaler værdien `-all`.|
    |

2. Hvis du ikke allerede har gjort det, skal du danne din SPF TXT-post ved hjælp af syntaksen fra tabellen.

   Hvis du f.eks. udelukkende er hostet i Office 365, det vil sige, at du ikke har nogen lokale mailservere, vil din SPF TXT-post indeholde række 1, 2 og 7 og vil se sådan ud:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **Eksemplet ovenfor er den mest almindelige SPF TXT-post**. Denne post fungerer for næsten alle, uanset om dit Microsoft-datacenter er placeret i USA eller i Europa (herunder Tyskland) eller et andet sted.

   Men hvis du har købt Office 365 Germany, en del af Microsoft Cloud Germany, skal du bruge medtag-sætningen fra linje 4 i stedet for linje 2. Hvis du f.eks. udelukkende er hostet i Office 365 Germany, det vil sige, at du ikke har nogen lokale mailservere, vil din SPF TXT-post indeholde række 1, 4 og 7 og vil se sådan ud:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Hvis du allerede er installeret i Office 365 og har konfigureret dine SPF TXT-poster for dit brugerdefinerede domæne, og du overfører til Office 365 Germany, skal du opdatere SPF TXT-posten. Det gør du ved at ændre til `include:spf.protection.outlook.com` `include:spf.protection.outlook.de`.

3. Når du har oprettet din SPF TXT-post, skal du opdatere posten i DNS. **Du kan kun have én SPF TXT-post for et domæne.** Hvis der findes en SPF TXT-post, skal du opdatere den eksisterende post i stedet for at tilføje en ny post. Gå til [Opret DNS-poster for Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md), og vælg derefter linket til din DNS-vært.

4. Test din SPF TXT-post.

## <a name="how-to-handle-subdomains"></a>Hvordan håndteres underdomæner?

Det er vigtigt at bemærke, at du skal oprette en separat post for hvert underdomæne, da underdomæner ikke arver *SPF-posten* for deres domæne på øverste niveau.

Der kræves en SPF-post med jokertegn (`*.`) for hvert domæne og underdomæne for at forhindre hackere i at sende mails, der hævder at være fra ikke-eksisterende underdomæner. Eksempel:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>Fejlfinding af SPF

Har du problemer med din SPF TXT-post? Læs [Fejlfinding: Bedste fremgangsmåder for SPF i Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>Hvad gør SPF-mailgodkendelse faktisk?

SPF identificerer, hvilke mailservere der har tilladelse til at sende mail på dine vegne. Grundlæggende hjælper SPF sammen med DKIM, DMARC og andre teknologier, der understøttes af Office 365, med at forhindre spoofing og phishing. SPF tilføjes som en TXT-post, der bruges af DNS til at identificere, hvilke mailservere der kan sende mail på vegne af dit brugerdefinerede domæne. Modtagermailsystemer henviser til SPF TXT-posten for at afgøre, om en meddelelse fra dit brugerdefinerede domæne kommer fra en godkendt meddelelsesserver.

Lad os f.eks. sige, at dit brugerdefinerede domæne contoso.com bruger Office 365. Du tilføjer en SPF TXT-post, der viser Office 365 som legitime mailservere for dit domæne. Når den modtagende meddelelsesserver modtager en meddelelse fra joe@contoso.com, søger serveren efter SPF TXT-posten contoso.com og finder ud af, om meddelelsen er gyldig. Hvis den modtagende server finder ud af, at meddelelsen kommer fra en anden server end de Office 365-meddelelsesservere, der er angivet i SPF-posten, kan den modtagende mailserver vælge at afvise meddelelsen som spam.

Hvis dit brugerdefinerede domæne ikke har en SPF TXT-post, kan nogle modtagende servere muligvis afvise meddelelsen direkte. Dette skyldes, at den modtagende server ikke kan validere, at meddelelsen kommer fra en godkendt meddelelsesserver.

Hvis du allerede har konfigureret mail til Office 365, har du allerede inkluderet Microsofts meddelelsesservere i DNS som en SPF TXT-post. Der er dog nogle tilfælde, hvor du muligvis skal opdatere din SPF TXT-post i DNS. Eksempel:

- Tidligere skulle du tilføje en anden SPF TXT-post til dit brugerdefinerede domæne, hvis du brugte SharePoint Online. Dette er ikke længere påkrævet. Denne ændring bør reducere risikoen for, at SharePoint Onlinemeddelelser ender i mappen Uønsket mail. Opdater din SPF TXT-post, hvis du når grænsen på 10 opslag og modtager fejl, hvor der står ting som f.eks. "overskredet opslagsgrænsen" og "for mange hop".

- Hvis du har et hybridmiljø med Office 365 Exchange lokalt miljø.

- Du har til hensigt at konfigurere DKIM og DMARC (anbefales).

## <a name="more-information-about-spf"></a>Flere oplysninger om SPF

Hvis du vil se avancerede eksempler, en mere detaljeret diskussion om understøttet SPF-syntaks, spoofing, fejlfinding, og hvordan Office 365 understøtter SPF, skal du se Sådan forhindrer [SPF spoofing og phishing i Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Næste trin: DKIM og DMARC

 SPF er udviklet til at forhindre spoofing, men der findes spoofing-teknikker, som SPF ikke kan beskytte sig mod. For at beskytte dig mod disse skal du, når du har konfigureret SPF, konfigurere DKIM og DMARC til Office 365.

[**DKIM-mailgodkendelses**](use-dkim-to-validate-outbound-email.md) mål er at bevise, at indholdet af mailen ikke er blevet ændret.

[**DMARC-mailgodkendelses**](use-dmarc-to-validate-email.md) mål er at sikre, at SPF- og DKIM-oplysninger stemmer overens med Fra-adressen.

 Du kan finde avancerede eksempler og en mere detaljeret diskussion om understøttet SPF-syntaks i Sådan virker SPF til at forhindre [spoofing og phishing i Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

*Vælg "Denne side" under "Feedback", hvis du har feedback til denne dokumentation.*
