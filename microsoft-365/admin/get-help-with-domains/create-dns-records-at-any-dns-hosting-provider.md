---
title: Tilføje DNS-poster for at forbinde dit domæne
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- MET150
description: Forbind domæne hos enhver DNS-udbyder til Microsoft 365 ved at bekræfte dit domæne og opdatere DNS-posterne i registratorens konto.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 17a3a63dfb3faedb5ff213b24dd14abd57f55bb3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589961"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Tilføje DNS-poster for at forbinde dit domæne

Hvis du har købt et domæne af en tredjepartshostingudbyder, kan du oprette forbindelse til Microsoft 365 ved at opdatere DNS-posterne i registratorens konto.

I slutningen af disse trin forbliver dit domæne registreret hos den vært, du har købt domænet hos, men Microsoft 365 kan bruge det til dine mailadresser (f.eks. user@yourdomain.com) og andre tjenester.

Hvis du ikke tilføjer et domæne, vil personer i organisationen bruge domænet onmicrosoft.com deres mailadresser, indtil du gør det. Det er vigtigt at tilføje dit domæne, før du tilføjer brugere, så du ikke behøver at konfigurere dem to gange.

[Se Ofte stillede spørgsmål om](../setup/domains-faq.yml) domæner, hvis du ikke kan finde det, du leder efter, nedenfor.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>Trin 1: Tilføj en TXT- eller MX-post for at bekræfte, at du ejer domænet

### <a name="recommended-verify-with-a-txt-record"></a>Anbefalet: Bekræft med en TXT-post

Først skal du bevise, at du ejer det domæne, du vil føje til Microsoft 365.

1. Log på fanen Microsoft 365 Administration vælg **Vis alle** >  **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.
2. Log på din DNS-udbyder på en ny browserfane eller i et nyt browservindue, og find derefter ud af, hvor du administrerer dine DNS-indstillinger (f.eks. Zone File Indstillinger, Manage Domains, Domain Manager, DNS Manager).
3. Gå til din udbyders DNS Manager-side, og føj den TXT-post, der er angivet i Administration, til dit domæne.

   Tilføjelse af denne post påvirker ikke din eksisterende mail eller andre tjenester, og du kan roligt fjerne den, når dit domæne er forbundet til Microsoft 365.

   Eksempel:

   - TXT-navn: `@`
   - TXT-værdi: MS=ms####### (entydigt id fra Administration)
   - TTL: `3600` (eller din udbyders standard)

4. Gem posten, gå tilbage til Administration, og vælg derefter **Bekræft**. Det tager som regel omkring 15 minutter, før registrering af ændringer er registreret, men nogle gange kan det tage længere tid. Giv den lidt tid, og nogle forsøg på at finde ændringen frem.

Når Microsoft finder den rette TXT-post, bekræftes dit domæne.

### <a name="verify-with-an-mx-record"></a>Bekræfte med en MX-post

Hvis din registrator ikke understøtter tilføjelse af TXT-poster, kan du bekræfte det ved at tilføje en MX-post.

1. Log på fanen Microsoft 365 Administration vælg **Vis alle** >  **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.
2. Log på din DNS-udbyder på en ny browserfane eller i et nyt browservindue, og find derefter ud af, hvor du administrerer dine DNS-indstillinger (f.eks. Zone File Indstillinger, Manage Domains, Domain Manager, DNS Manager).
3. Gå til din udbyders DNS Manager-side, og føj den MX-post, der er angivet i Administration, til dit domæne.

Prioritet for denne **MX-post** skal være den højeste af alle eksisterende MX-poster for domænet. Ellers kan det forstyrre afsendelse og modtagelse af mail. Du bør slette disse poster, så snart domænebekræftelsen er fuldført.

Sørg for, at felterne er angivet til følgende værdier:

- Record Type: `MX`
- Prioritet: Indstillet til en hvilken som helst stor værdi, der ikke allerede er brugt.
- Værtsnavn: `@`
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

Når Microsoft finder den korrekte MX-post, bekræftes dit domæne.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>Trin 2: Tilføj DNS-poster for at oprette forbindelse Microsoft-tjenester

Log på din DNS-udbyder på en ny browserfane eller i et nyt browservindue og find ud af, hvor du administrerer dine DNS-indstillinger (f.eks. Zone File Indstillinger, Manage Domains, Domain Manager, DNS Manager).

Du skal tilføje flere forskellige typer DNS-poster afhængigt af de tjenester, du vil aktivere.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>Tilføje en MX-post til mail (Outlook, Exchange Online)

**Før du går i gang:** Hvis brugerne allerede har mail med dit domæne (f.eks. user@yourdomain.com), skal du oprette deres konti i Administration, før du konfigurerer dine MX-poster. På den måde fortsætter de med at modtage mail. Når du opdaterer dit domænes MX-post, vil alle nye mails til alle, der bruger dit domæne, nu komme Microsoft 365. Alle mails, du allerede har, forbliver hos din aktuelle mailvært, medmindre du beslutter at overføre [mails og kontakter Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

Du får oplysningerne om MX-posten fra konfigurationsguiden for domæner i Administration.

Tilføj en ny MX-post på din udbyders websted.
Sørg for, at felterne er angivet til følgende værdier:

- Record Type: `MX`
- Prioritet: Indstillet til den højeste tilgængelige værdi, typisk `0`.
- Værtsnavn: `@`
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

Gem posten, og fjern derefter eventuelle andre MX-poster.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Tilføje CNAME-poster for at forbinde andre tjenester (Teams, Exchange Online, AAD, MDM)

Du får oplysningerne om CNAME-posterne fra konfigurationsguiden for domæner i Administration.

Tilføj CNAME-poster for hver tjeneste, du vil oprette forbindelse til, på din udbyders websted.
Sørg for, at felterne er indstillet til følgende værdier for hver:

- Record Type: `CNAME (Alias)`
- Vært: Indsæt de værdier, du kopierer fra Administration, her.
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>Tilføj eller rediger en SPF TXT-post for at forhindre mailspam (Outlook, Exchange Online)

**Før du går i gang:** Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny for Microsoft 365. I stedet skal du føje de påkrævede Microsoft 365-værdier til den aktuelle post på hostingudbydernes websted, så du har en *enkelt* SPF-post, der indeholder begge sæt af værdier.

Rediger den eksisterende SPF-post på din udbyders websted, eller opret en SPF-post.
Sørg for, at felterne er angivet til følgende værdier:

- Record Type: `TXT (Text)`
- Vært: `@`
- TXT-værdi: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (eller din udbyders standard)

Gem posten.

Valider din SPF-post ved hjælp af et af disse [SPF-valideringsværktøjer](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

SPF er udviklet til at forhindre spoofing, men der findes spoofing-teknikker, som SPF ikke kan beskytte sig mod. For at beskytte dig mod disse skal du, når du har konfigureret SPF, også konfigurere DKIM og DMARC til Microsoft 365.

For at komme i gang skal du se Brug DKIM til at validere udgående mails, der sendes fra dit domæne [i Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) og [Brug DMARC til at validere mail i Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>Tilføje SRV-poster for kommunikationstjenester (Teams, Skype for Business)

Tilføj SRV-poster for hver tjeneste, du vil oprette forbindelse til, på din udbyders websted.
Sørg for, at felterne er indstillet til følgende værdier for hver:

- Record Type: `SRV (Service)`
- Navn: `@`
- Destination: Kopiér værdien fra Administration, og sæt den ind her.
- Protokol: Kopiér værdien fra Administration, og sæt den ind her.
- Tjeneste: Kopiér værdien fra Administration, og sæt den ind her.
- Prioritet: `100`
- Tykkelse: `1`
- Port: Kopiér værdien fra Administration, og sæt den ind her.
- TTL: `3600` (eller din udbyders standard)

Gem posten.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>Begrænsninger og løsninger for SRV-postfelt

Nogle værtsudbydere pålægger begrænsninger for feltværdier i SRV-poster. Her er nogle almindelige løsninger på disse begrænsninger.

##### <a name="name"></a>Navn

Hvis din udbyder ikke tillader, at dette felt angives til **@**, skal du lade feltet være tomt. Brug kun denne *fremgangsmåde* , når din udbyder har separate felter for værdierne Service og Protocol. Ellers skal du se noterne til Service og Protocol nedenfor.

##### <a name="service-and-protocol"></a>Tjeneste og protokol

Hvis din udbyder ikke leverer disse felter til SRV-poster, skal du angive værdierne **for Service** og **Protocol** i postens **Navn-felt** . (Bemærk! Afhængigt af din udbyder kan feltet  Navn hedde noget andet, f.eks.: **Host**, **Hostname** eller **Subdomain**). Hvis du vil tilføje disse værdier, skal du oprette en enkelt streng og adskille værdierne med en prik.

Eksempel: `_sip._tls`

##### <a name="priority-weight-and-port"></a>Prioritet, Vægt og Port

Hvis din udbyder ikke leverer disse felter for SRV-poster, skal du angive dem i postens **Target-felt** . (Bemærk: Afhængigt af din udbyder kan feltet  Destination hedde noget andet, f.eks.: **Indhold**, **IP-adresse** eller **Destinationsvært**).

For at tilføje disse værdier skal du oprette en enkelt streng, der adskiller værdierne med mellemrum og nogle gange slutter med en *prik (spørg* din udbyder, hvis du er i tvivl). Værdierne skal inkluderes i denne rækkefølge: Prioritet, Vægt, Port, Destination.

- Eksempel 1: `100 1 443 sipdir.online.lync.com.`
- Eksempel 2: `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>Relateret indhold

[Rediger navneservere for at konfigurere Microsoft 365 med en domæneregistrator](change-nameservers-at-any-domain-registrar.md) (artikel)\
[Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster](find-and-fix-issues.md) (artikel)\
[Administrer domæner](/admin) (linkside)
