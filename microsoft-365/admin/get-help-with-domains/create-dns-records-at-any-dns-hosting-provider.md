---
title: Tilføj DNS-poster for at oprette forbindelse til dit domæne
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
description: Forbind et domæne hos en DNS-hostingudbyder til at Microsoft 365 ved at bekræfte dit domæne og opdatere DNS-posterne på din registrators konto.
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
- admindeeplinkMAC
ms.openlocfilehash: 08d28a5586c92d0e439170807f750150d9fbe17c
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/07/2022
ms.locfileid: "64704773"
---
# <a name="add-dns-records-to-connect-your-domain"></a>Tilføj DNS-poster for at oprette forbindelse til dit domæne

Hvis du har købt et domæne fra en tredjepartshostingudbyder, kan du knytte det til Microsoft 365 ved at opdatere DNS-posterne på din registrators konto.

I slutningen af disse trin forbliver dit domæne registreret hos den vært, du har købt domænet fra, men Microsoft 365 kan bruge det til dine mailadresser (f.eks. user@yourdomain.com) og andre tjenester.

Hvis du ikke tilføjer et domæne, bruger personer i din organisation domænet onmicrosoft.com til deres mailadresser, indtil du gør det. Det er vigtigt at tilføje dit domæne, før du tilføjer brugere, så du ikke behøver at konfigurere dem to gange.

[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) , hvis du ikke kan finde det, du leder efter, nedenfor.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft-specialist i mindre virksomheder](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til specialister i mindre virksomheder, efterhånden som du udvikler din virksomhed – lige fra onboarding til daglig brug.

## <a name="step-1-add-a-txt-or-mx-record-to-verify-you-own-the-domain"></a>Trin 1: Tilføj en TXT- eller MX-post for at bekræfte, at du ejer domænet

### <a name="recommended-verify-with-a-txt-record"></a>Anbefalet: Kontrollér med en TXT-post

Først skal du bevise, at du ejer det domæne, du vil føje til Microsoft 365.

1. Log på Microsoft 365 Administration, og vælg **Vis alle** >  **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.
2. Log på din DNS-hostingudbyder i en ny browserfane eller et nyt vindue, og find derefter ud af, hvor du administrerer dine DNS-indstillinger (f.eks. Zone File Indstillinger, Manage Domains, Domain Manager, DNS Manager).
3. Gå til udbyderens DNS Manager-side, og føj den TXT-post, der er angivet i Administration, til dit domæne.

   Hvis du tilføjer denne post, påvirker det ikke din eksisterende mail eller andre tjenester, og du kan trygt fjerne den, når dit domæne har forbindelse til Microsoft 365.

   Eksempel:

   - TXT-navn: `@`
   - TXT-værdi: MS=ms####### (entydigt id fra Administration)
   - TTL: `3600` (eller din udbyders standard)

4. Gem posten, gå tilbage til Administration, og vælg derefter **Bekræft**. Det tager typisk ca. 15 minutter, før postændringer registreres, men nogle gange kan det tage længere tid. Giv det lidt tid, og et par forsøger at hente ændringen.

Når Microsoft finder den korrekte TXT-post, bekræftes dit domæne.

### <a name="verify-with-an-mx-record"></a>Bekræft med en MX-post

Hvis din registrator ikke understøtter tilføjelse af TXT-poster, kan du bekræfte det ved at tilføje en MX-post.

1. Log på Microsoft 365 Administration, og vælg **Vis alle** >  **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.
2. Log på din DNS-hostingudbyder i en ny browserfane eller et nyt vindue, og find derefter ud af, hvor du administrerer dine DNS-indstillinger (f.eks. Zone File Indstillinger, Manage Domains, Domain Manager, DNS Manager).
3. Gå til udbyderens DNS Manager-side, og føj den MX-post, der er angivet i Administration, til dit domæne.

Prioriteten for denne MX-post **skal være** den højeste af alle eksisterende MX-poster for domænet. Ellers kan det forstyrre afsendelse og modtagelse af mail. Du bør slette disse poster, så snart domænebekræftelsen er fuldført.

Sørg for, at felterne er angivet til følgende værdier:

- Posttype: `MX`
- Prioritet: Angiv som en hvilken som helst stor værdi, der ikke allerede bruges.
- Værtsnavn: `@`
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

Når Microsoft finder den korrekte MX-post, bekræftes dit domæne.

## <a name="step-2-add-dns-records-to-connect-microsoft-services"></a>Trin 2: Tilføj DNS-poster for at oprette forbindelse Microsoft-tjenester

Log på din DNS-hostingudbyder i en ny browserfane eller et nyt vindue, og find ud af, hvor du administrerer dine DNS-indstillinger (f.eks. zonefil Indstillinger, Administrer domæner, Domæneadministrator, DNS Manager).

Du tilføjer flere forskellige typer DNS-poster, afhængigt af de tjenester du vil aktivere.

### <a name="add-an-mx-record-for-email-outlook-exchange-online"></a>Tilføj en MX-post for mail (Outlook, Exchange Online)

**Før du begynder:** Hvis brugerne allerede har mail med dit domæne (f.eks. user@yourdomain.com), skal du oprette deres konti i Administration, før du konfigurerer dine MX-poster. På den måde modtager de fortsat mail. Når du opdaterer dit domænes MX-post, kommer alle nye mails til alle, der bruger dit domæne, nu til Microsoft 365. Alle mails, du allerede har, forbliver hos din aktuelle mailvært, medmindre du beslutter dig for at [overføre mail og kontakter til Microsoft 365.](../setup/migrate-email-and-contacts-admin.md)

Du får oplysninger om MX-posten fra administrationsguiden til domæneinstallation.

Tilføj en ny MX-post på din hostingudbyders websted. Sørg for, at felterne er angivet til følgende værdier:

- Posttype: `MX`
- Prioritet: Angiv som regel til den højeste tilgængelige værdi.`0`
- Værtsnavn: `@`
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600`

> [!NOTE]
> Exchange Online understøtter kun TTL-værdier, der er mindre end 6 timer (21.600 sekunder).

Gem posten, og fjern derefter alle andre MX-poster.

### <a name="add-cname-records-to-connect-other-services-teams-exchange-online-aad-mdm"></a>Tilføj CNAME-poster for at oprette forbindelse til andre tjenester (Teams, Exchange Online, AAD, MDM)

Du får oplysninger om CNAME-posterne fra administrationsguiden til domæneinstallation.

På din hostingudbyders websted skal du tilføje CNAME-poster for hver tjeneste, du vil oprette forbindelse til.
Sørg for, at felterne er angivet til følgende værdier for hver enkelt:

- Posttype: `CNAME (Alias)`
- Vært: Indsæt de værdier, du kopierer fra Administration, her.
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

### <a name="add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online"></a>Tilføj eller rediger en SPF TXT-post for at forhindre mailspam (Outlook, Exchange Online)

**Før du begynder:** Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft 365. Føj i stedet de påkrævede Microsoft 365 værdier til den aktuelle post på webstedet for hostingudbydere, så du har en *enkelt* SPF-post, der indeholder begge værdisæt.

Rediger den eksisterende SPF-post på udbyderens websted, eller opret en SPF-post.
Sørg for, at felterne er angivet til følgende værdier:

- Posttype: `TXT (Text)`
- Vært: `@`
- TXT-værdi: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (eller din udbyders standard)

Gem posten.

Valider din SPF-post ved hjælp af et af disse [SPF-valideringsværktøjer](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

SPF er designet til at hjælpe med at forhindre spoofing, men der er spoofing-teknikker, som SPF ikke kan beskytte mod. Når du har konfigureret SPF, skal du også konfigurere DKIM og DMARC til Microsoft 365 for at beskytte mod disse.

For at komme i gang skal du se [Brug DKIM til at validere udgående mail, der er sendt fra dit domæne i Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) og [Brug DMARC til at validere mail i Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

### <a name="add-srv-records-for-communications-services-teams-skype-for-business"></a>Tilføj SRV-poster for kommunikationstjenester (Teams, Skype for Business)

På din hostingudbyders websted skal du tilføje SRV-poster for hver tjeneste, du vil oprette forbindelse til.
Sørg for, at felterne er angivet til følgende værdier for hver enkelt:

- Posttype: `SRV (Service)`
- Navn: `@`
- Mål: Kopiér værdien fra Administration, og indsæt den her.
- Protokol: Kopiér værdien fra Administration, og indsæt den her.
- Tjeneste: Kopiér værdien fra Administration, og indsæt den her.
- Prioritet: `100`
- Vægt: `1`
- Port: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

Gem posten.

#### <a name="srv-record-field-restrictions-and-workarounds"></a>Begrænsninger for SRV-postfelter og midlertidige løsninger

Nogle hostingudbydere pålægger feltværdier begrænsninger i SRV-poster. Her er nogle almindelige løsninger på disse begrænsninger.

##### <a name="name"></a>Navn

Hvis din hostingudbyder ikke tillader, at dette felt angives til **@**, skal du lade det være tomt. Brug *kun* denne fremgangsmåde, når din hostingudbyder har separate felter for tjeneste- og protokolværdierne. Ellers skal du se service- og protokolnoterne nedenfor.

##### <a name="service-and-protocol"></a>Tjeneste og protokol

Hvis din hostingudbyder ikke angiver disse felter for SRV-poster, skal du angive **værdierne for Tjeneste** og **Protokol** i feltet **Navn** for posten. (Bemærk! Afhængigt af din udbyder kan feltet **Navn** kaldes noget andet, f.eks.: **Vært**, **Værtsnavn** eller **Underdomæne**. Hvis du vil tilføje disse værdier, skal du oprette en enkelt streng, der adskiller værdierne med en prik.

Eksempel: `_sip._tls`

##### <a name="priority-weight-and-port"></a>Prioritet, vægt og port

Hvis din hostingudbyder ikke angiver disse felter for SRV-poster, skal du angive dem i postens **destinationsfelt** . (Bemærk! Afhængigt af din hostingudbyder kan feltet **Mål** kaldes noget andet, f.eks.: **Indhold**, **IP-adresse** eller **Destinationsvært**.

Hvis du vil tilføje disse værdier, skal du oprette en enkelt streng, der adskiller værdierne med mellemrum og *nogle gange slutter med en prik* (kontakt udbyderen, hvis du er usikker). Værdierne skal inkluderes i denne rækkefølge: Prioritet, Vægt, Port, Mål.

- Eksempel 1: `100 1 443 sipdir.online.lync.com.`
- Eksempel 2: `100 1 443 sipdir.online.lync.com`

## <a name="related-content"></a>Relateret indhold

[Skift navneservere for at konfigurere Microsoft 365 med en hvilken som helst domæneregistrator](change-nameservers-at-any-domain-registrar.md) (artikel)\
[Find og løs problemer, når du har tilføjet dine domæne- eller DNS-poster](find-and-fix-issues.md) (artikel)\
[Administrer domæner](/admin) (linkside)
