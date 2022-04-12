---
title: Forbind dine DNS-poster på Cloudflare til Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 84acd4fc-6eec-4d00-8bed-568f036ae2af
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos Cloudflare til Microsoft.
ms.openlocfilehash: 164a681cccac3385d2ca963ac58706c8e743bc1e
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780363"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Forbind dine DNS-poster på Cloudflare til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis Cloudflare er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

## <a name="before-you-begin"></a>Før du begynder

Du har to muligheder for at konfigurere DNS-poster for dit domæne:

- [**Brug Domæne Forbind**](#use-domain-connect-to-verify-and-set-up-your-domain) Hvis du ikke har konfigureret dit domæne med en anden mailtjenesteudbyder, skal du bruge trinnene Domæne Forbind til automatisk at bekræfte og konfigurere dit nye domæne til brug sammen med Microsoft 365.

    ELLER

- [**Brug de manuelle trin**](#create-dns-records-with-manual-setup) Bekræft dit domæne ved hjælp af de manuelle trin nedenfor, og vælg, hvornår og hvilke poster der skal føjes til din domæneregistrator. Dette giver dig mulighed for at konfigurere nye MX-poster (mail), f.eks. når det passer dig.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Brug Domæne Forbind til at bekræfte og konfigurere dit domæne

Følg disse trin for automatisk at bekræfte og konfigurere dit Cloudflare-domæne med Microsoft 365:

1. Vælg **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> i Microsoft 365 Administration, og vælg det domæne, du vil konfigurere.

1. Vælg de tre prikker (flere handlinger) \> vælg **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Under Hvordan vil du oprette forbindelse til dit domæne? skal du vælge **Fortsæt**.

1. På siden Tilføj DNS-poster skal du vælge **Tilføj DNS-poster**.

1. Log på din konto på logonsiden Cloudflare, og vælg **Godkend**.

    Dette fuldfører domænekonfigurationen for Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Opret DNS-poster med manuel konfiguration

Når du har tilføjet disse poster i Cloudflare, konfigureres dit domæne til at arbejde med Microsoft 365 tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="change-your-domains-nameserver-ns-records"></a>Skift dit domænes navneserverposter (NS)

> [!IMPORTANT]
> Du skal udføre denne procedure hos den domæneregistrator, hvor du har købt og registreret dit domæne.

Da du tilmeldte dig Cloudflare, tilføjede du et domæne ved hjælp af processen til konfiguration af Cloudflare.

Det domæne, du har tilføjet, er købt hos Cloudflare eller en separat domæneregistrator. Hvis du vil bekræfte og oprette DNS-poster for dit domæne i Microsoft 365, skal du først ændre navneserverne hos domæneregistratoren, så de bruger Cloudflare-navneserverne.

Hvis du selv vil ændre domænets navneservere på domæneregistratorens websted, skal du følge disse trin.

1. Find det område på domæneregistratorens websted, hvor du kan redigere navneserverne for dit domæne.

2. Opret enten to navneserverposter ved hjælp af værdierne i følgende tabel, eller rediger de eksisterende navneserverposter, så de stemmer overens med disse værdier.

    |Type|Værdi|
    |---|---|
    |Fornavnserver|Brug den nameserver-værdi, der leveres af Cloudflare.|
    |Anden navneserver|Brug den nameserver-værdi, der leveres af Cloudflare.|

    > [!TIP]
    > Du skal bruge mindst to navneserverposter. Hvis der er angivet andre navneservere, skal du slette dem.

3. Gem dine ændringer.

> [!NOTE]
> Det kan tage op til flere timer at opdatere opdateringerne af din nameserver-post på tværs af internettets DNS-system. Derefter er din Microsoft-mail og andre tjenester indstillet til at arbejde med dit domæne.

### <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden DNS-administration skal du vælge **+Tilføj post**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg TXT-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |Type|Navn|TTL|Indhold|
    |---|---|---|:----|
    |TXT|@|30 minutter|MS=*msXXXXXXXXX* <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Vælg Tilføj post.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og søge efter posten. Når Microsoft finder den korrekte TXT-post, bekræftes dit domæne.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden DNS-administration skal du vælge **+Tilføj post**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg MX-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

   |Type|Navn|Mailserver|TTL|Prioritet|
   |---|---|---|---|---|
   |MX|@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Bemærk:** Få din *\<domain-key\>* fra din Microsoft 365 konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|30 minutter|1 <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/>|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Vælg Tilføj post.":::

1. Hvis der er andre MX-poster angivet i afsnittet **MX-poster** , skal du slette dem ved at vælge **Rediger** og derefter vælge **Slet**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Vælg Slet.":::

1. I bekræftelsesdialogboksen skal du vælge **Slet** for at bekræfte dine ændringer.

### <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden **DNS-administration** skal du vælge **+Tilføj post**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg typen CNAME på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |Type|Navn|Mål|TTL|
    |---|---|---|---|
    |CNAME|Autodiscover|autodiscover.outlook.com|Auto|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Vælg Gem.":::

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft 365. Føj i stedet de påkrævede Microsoft 365 værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden DNS-administration skal du vælge **+Tilføj post**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg TXT-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |Type|Navn|TTL|Indhold|
    |---|---|---|---|
    |TXT|@|30 minutter|v=spf1 include:spf.protection.outlook.com -all <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Vælg Gem.":::

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

> [!IMPORTANT]
> Vær opmærksom på, at Cloudflare er ansvarlig for at gøre denne funktionalitet tilgængelig. Hvis du ser uoverensstemmelser mellem nedenstående trin og den aktuelle Gui Cloudflare GUI (grafisk brugergrænseflade), skal du udnytte [Cloudflare-community'et](https://community.cloudflare.com/).

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden DNS-administration skal du vælge **+Tilføj post**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg SRV-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |Type|Navn|Tjeneste|Protokollen|TTL|Prioritet|Vægt|Port|Mål|
    |---|---|---|---|---|---|---|---|---|
    |SRV|Brug dine *domain_name*. contoso.com f.eks.|_sip|TLS|30 minutter|100|1|443|sipfed.online.lync.com|
    |SRV|_sipfederationtls|TCP|Brug dine *domain_name*. contoso.com f.eks.|30 minutter|100|1|5061|sipfed.online.lync.com|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden DNS-administration skal du vælge **+Tilføj post**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg typen CNAME på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |Type|Navn|Mål|TTL|
    |---|---|---|---|
    |CNAME|Sip|sipdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|
    |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden domæner på Cloudflare ved hjælp af [dette link](https://www.cloudflare.com/a/login). Du bliver bedt om at logge på først.

1. Vælg det domæne, du vil opdatere, på siden Startside.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. Vælg **DNS** på siden Oversigt for dit domæne.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På siden DNS-administration skal du vælge **+Tilføj post**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg typen CNAME på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |Type|Navn|Mål|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
