---
title: Konfigurer SPF for at forhindre forfalskning
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
description: Få mere at vide om, hvordan du opdaterer en DNS-post (Domain Name Service), så den bruger SPF (Sender Policy Framework) sammen med dit brugerdefinerede domæne i Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d29175c471e076b1f69e1edb6da3c005d3857f8f
ms.sourcegitcommit: c4924bcad6648fae279076cafa505fae1194924a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/21/2022
ms.locfileid: "65626035"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>Konfigurer SPF for at forhindre forfalskning

- [Forudsætninger](#prerequisites)
- [Opret eller opdater SPF TXT-posten](#create-or-update-your-spf-txt-record)
- [Hvordan håndterer du underdomæner?](#how-to-handle-subdomains)
- [Fejlfinding af SPF](#troubleshooting-spf)

<!--
[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

I denne artikel beskrives det, hvordan du opdaterer en DNS-post (Domain Name Service), så du kan bruge SPF-mailgodkendelse (Sender Policy Framework) med dit brugerdefinerede domæne i Office 365.

SPF hjælper med at *validere* udgående mail, der er sendt fra dit brugerdefinerede domæne (kommer fra den, den siger, den er). Det er et første trin til at konfigurere de fulde anbefalede metoder til godkendelse af mail for SPF, [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md).

- [Forudsætninger](#prerequisites)
- [Opret eller opdater SPF TXT-posten](#create-or-update-your-spf-txt-record)
  - [Hvordan håndterer du underdomæner?](#how-to-handle-subdomains)
- [Hvad gør SPF-mailgodkendelse egentlig?](#what-does-spf-email-authentication-actually-do)
  - [Fejlfinding af SPF](#troubleshooting-spf)
- [Flere oplysninger om SPF](#more-information-about-spf)

## <a name="prerequisites"></a>Forudsætninger

> [!IMPORTANT]
> Hvis du er **en mindre virksomhed**, eller du ikke kender IP-adresser eller DNS-konfiguration, skal du ringe til din internetdomæneregistrator (f.eks. GoDaddy, Bluehost, web.com) & bede om hjælp til *DNS-konfigurationen af SPF* (og enhver anden godkendelsesmetode for mail). <p> **Hvis du ikke bruger en brugerdefineret URL-adresse** (og den URL-adresse, der bruges til Office 365 ender i **onmicrosoft.com**), er SPF allerede konfigureret for dig i Office 365-tjenesten.

Lad os komme i gang.

SPF TXT-posten for Office 365 oprettes i ekstern DNS for alle brugerdefinerede domæner eller underdomæner. Du skal bruge nogle oplysninger for at oprette posten. Indsaml disse oplysninger:

- SPF TXT-posten for dit brugerdefinerede domæne, hvis der findes et. Du kan finde instruktioner under [Indsaml de oplysninger, du skal bruge for at oprette Office 365 DNS-poster](../../admin/get-help-with-domains/information-for-dns-records.md).

- Gå til din eller dine meddelelsesservere, og find ud af de eksterne IP-adresser (skal bruges af alle meddelelsesservere i det lokale miljø). For eksempel **131.107.2.200**.

- Domænenavne, der skal bruges til alle tredjepartsdomæner, som du skal medtage i din SPF TXT-post. Nogle massemailudbydere har konfigureret underdomæner, der skal bruges til deres kunder. Virksomheden MailChimp har f.eks. konfigureret **servers.mcsv.net**.

- Find ud af, hvilken håndhævelsesregel du vil bruge til SPF TXT-posten. Reglen **-all** anbefales. Du kan finde flere oplysninger om andre syntaksindstillinger under [SPF TXT-postsyntaks for Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> Hvis du vil bruge et brugerdefineret domæne, kræver Office 365, at du føjer en SPF TXT-post (Sender Policy Framework) til din DNS-post for at forhindre spoofing.

## <a name="create-or-update-your-spf-txt-record"></a>Opret eller opdater SPF TXT-posten

1. Sørg for, at du kender SPF-syntaksen i følgende tabel.

    |Element|Hvis du bruger...|Fælles for kunder?|Tilføj denne...|
    |---|---|---|---|
    |1|Et hvilket som helst mailsystem (påkrævet)|Fælles. Alle SPF TXT-poster starter med denne værdi|`v=spf1`|
    |2|Exchange Online|Fælles|`include:spf.protection.outlook.com`|
    |3|Exchange Online kun dedikeret|Ikke almindelig|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 Germany, kun Microsoft Cloud Germany|Ikke almindelig|`include:spf.protection.outlook.de`|
    |5|Tredjepartsmailsystem|Ikke almindelig|`include:<domain_name>` <p> \<domain_name\> er domænet for tredjepartsmailsystemet.|
    |6|Mailsystem i det lokale miljø. For eksempel Exchange Online Protection plus et andet mailsystem|Ikke almindelig|Brug en af disse til hvert ekstra postsystem: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> og \<domain_name\> er IP-adressen og domænet for det andet mailsystem, der sender mail på vegne af dit domæne.|
    |7|Et hvilket som helst mailsystem (påkrævet)|Fælles. Alle SPF TXT-poster slutter med denne værdi|`<enforcement rule>` <p> Dette kan være en af flere værdier. Vi anbefaler værdien `-all`.|

2. Hvis du ikke allerede har gjort det, kan du danne SPF TXT-posten ved hjælp af syntaksen fra tabellen .

   Hvis du f.eks. udelukkende hostes i Office 365, dvs. at du ikke har nogen lokale mailservere, indeholder SPF TXT-posten række 1, 2 og 7 og ser sådan ud:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **Ovenstående eksempel er den mest almindelige SPF TXT-post**. Denne post fungerer for næsten alle, uanset om dit Microsoft-datacenter er placeret i USA, i Europa (herunder Tyskland) eller på en anden placering.

   Men hvis du har købt Office 365 Germany, som er en del af Microsoft Cloud Germany, skal du bruge "include"-sætningen fra linje 4 i stedet for linje 2. Hvis du f.eks. udelukkende hostes i Office 365 Tyskland, dvs. at du ikke har nogen lokale mailservere, indeholder SPF TXT-posten række 1, 4 og 7 og ser sådan ud:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   Hvis du allerede er udrullet i Office 365 og har konfigureret SPF TXT-posterne for dit brugerdefinerede domæne, og du overfører til Office 365 Tyskland, skal du opdatere din SPF TXT-post. Det gør du ved at skifte `include:spf.protection.outlook.com` til `include:spf.protection.outlook.de`.

3. Når du har dannet din SPF TXT-post, skal du opdatere posten i DNS. **Du kan kun have én SPF TXT-post for et domæne.** Hvis der findes en SPF TXT-post, skal du opdatere den eksisterende post i stedet for at tilføje en ny post. Gå til [Opret DNS-poster for Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md), og vælg derefter linket til din DNS-vært.

4. Test SPF TXT-posten.

## <a name="how-to-handle-subdomains"></a>Hvordan håndterer du underdomæner?

Det er vigtigt at bemærke, at *du skal oprette en separat post for hvert underdomæne, da underdomæner ikke nedarver SPF-posten for deres domæne på øverste niveau*.

Der kræves en SPF-jokerpost (`*.`) for hvert domæne og underdomæne for at forhindre hackere i at sende mails, der hævder at være fra ikke-eksisterende underdomæner. Eksempel:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>Fejlfinding af SPF

Har du problemer med SPF TXT-posten? Læs [Fejlfinding: Bedste praksis for SPF i Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>Hvad gør SPF-mailgodkendelse egentlig?

SPF identificerer, hvilke mailservere der har tilladelse til at sende mail på dine vegne. Grundlæggende hjælper SPF sammen med DKIM, DMARC og andre teknologier, der understøttes af Office 365, med at forhindre spoofing og phishing. SPF tilføjes som en TXT-post, der bruges af DNS til at identificere, hvilke mailservere der kan sende mail på vegne af dit brugerdefinerede domæne. Modtagermailsystemer refererer til SPF TXT-posten for at afgøre, om en meddelelse fra dit brugerdefinerede domæne kommer fra en godkendt meddelelsesserver.

Lad os f.eks. sige, at dit brugerdefinerede domæne contoso.com bruger Office 365. Du tilføjer en SPF TXT-post, der viser de Office 365 meddelelsesservere som legitime mailservere for dit domæne. Når modtagermeddelelsesserveren modtager en meddelelse fra joe@contoso.com, søger serveren efter SPF TXT-posten for contoso.com og finder ud af, om meddelelsen er gyldig. Hvis modtagerserveren finder ud af, at meddelelsen kommer fra en anden server end de Office 365 meddelelsesservere, der er angivet i SPF-posten, kan den modtagende mailserver vælge at afvise meddelelsen som spam.

Hvis dit brugerdefinerede domæne ikke har en SPF TXT-post, kan nogle modtagende servere afvise meddelelsen direkte. Det skyldes, at modtagerserveren ikke kan validere, at meddelelsen kommer fra en godkendt meddelelsesserver.

Hvis du allerede har konfigureret mail til Office 365, har du allerede inkluderet Microsofts meddelelsesservere i DNS som en SPF TXT-post. Der er dog nogle tilfælde, hvor du muligvis skal opdatere din SPF TXT-post i DNS. Eksempel:

- Tidligere skulle du føje en anden SPF TXT-post til dit brugerdefinerede domæne, hvis du brugte SharePoint Online. Dette er ikke længere påkrævet. Denne ændring bør reducere risikoen for, at SharePoint onlinemeddelelsesmeddelelser ender i mappen Uønsket mail. Opdater din SPF TXT-post, hvis du har nået grænsen på 10 opslag og modtager fejl, der f.eks. "overskred grænsen for opslag" og "for mange hop".

- Hvis du har et hybridmiljø med Office 365 og Exchange i det lokale miljø.

- Du har til hensigt at konfigurere DKIM og DMARC (anbefales).

## <a name="more-information-about-spf"></a>Flere oplysninger om SPF

I forbindelse med avancerede eksempler kan du se en mere detaljeret beskrivelse af understøttet SPF-syntaks, spoofing, fejlfinding, og hvordan Office 365 understøtter [SPF, under Sådan fungerer SPF for at forhindre spoofing og phishing i Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>Næste trin: DKIM og DMARC

 SPF er designet til at hjælpe med at forhindre spoofing, men der er spoofing-teknikker, som SPF ikke kan beskytte mod. Når du har konfigureret SPF, skal du konfigurere DKIM og DMARC til Office 365 for at forsvare dig mod disse.

[**DKIM-mailgodkendelsens**](use-dkim-to-validate-outbound-email.md) mål er at bevise, at indholdet af mailen ikke er blevet pillet ved.

[**DMARC-mailgodkendelsens**](use-dmarc-to-validate-email.md) mål er at sikre, at SPF- og DKIM-oplysningerne stemmer overens med Fra-adressen.

 Du kan finde avancerede eksempler og en mere detaljeret beskrivelse af understøttet SPF-syntaks [under Sådan fungerer SPF for at forhindre spoofing og phishing i Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

*Vælg 'Denne side' under 'Feedback', hvis du har feedback på denne dokumentation.*
