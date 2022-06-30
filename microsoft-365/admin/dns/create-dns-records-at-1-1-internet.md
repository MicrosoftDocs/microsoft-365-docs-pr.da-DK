---
title: Forbind dine DNS-poster på IONOS med 1&1 til Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester på 1&1 IONOS til Microsoft.
ms.openlocfilehash: b9d7474fe0c442670be961a5436558ea168626dc
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563423"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Forbind dine DNS-poster på IONOS med 1&1 til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis IONOS by 1&1 er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster til mail, Skype for Business Online osv.

## <a name="before-you-begin"></a>Før du begynder

Du har to muligheder for at konfigurere DNS-poster for dit domæne:

- [**Brug domæneforbindelse**](#use-domain-connect-to-verify-and-set-up-your-domain) Hvis du ikke har konfigureret dit domæne med en anden mailtjenesteudbyder, skal du bruge trinnene Domæneforbindelse til automatisk at bekræfte og konfigurere dit nye domæne til brug sammen med Microsoft 365.

    ELLER

- [**Brug de manuelle trin**](#create-dns-records-with-manual-setup) Bekræft dit domæne ved hjælp af de manuelle trin nedenfor, og vælg, hvornår og hvilke poster der skal føjes til din domæneregistrator. Dette giver dig mulighed for at konfigurere nye MX-poster (mail), f.eks. når det passer dig.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Brug Domæneforbindelse til at bekræfte og konfigurere dit domæne

Følg disse trin for automatisk at bekræfte og konfigurere IONOS efter 1&1-domæne med Microsoft 365:

1. Vælg **Indstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> i Microsoft 365 Administration, og vælg det domæne, du vil konfigurere.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Vælg dit domæne i Microsoft 365.":::

1. Vælg de tre prikker (flere handlinger) > vælg **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Under Hvordan vil du oprette forbindelse til dit domæne? skal du vælge **Fortsæt**.

1. På siden Tilføj DNS-poster skal du vælge **Tilføj DNS-poster**.

1. Log på din konto på IONOS by 1&1 logonside, og vælg **Opret forbindelse** og **Tillad**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Vælg Opret forbindelse og derefter Tillad.":::

    Dette fuldfører domænekonfigurationen for Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Opret DNS-poster med manuel konfiguration

Når du har tilføjet disse poster på IONOS med 1&1, konfigureres dit domæne til at fungere sammen med Microsoft-tjenester.

> [!CAUTION]
> Bemærk, at IONOS efter 1&1 ikke tillader, at et domæne har både en MX-post og en Autodiscover CNAME-post på øverste niveau. Dette begrænser de måder, hvorpå du kan konfigurere Exchange Online til Microsoft. Der er en løsning, men vi anbefaler, at du **kun** anvender den, hvis du allerede har erfaring med at oprette underdomæner på IONOS efter 1&1.
> Hvis du på trods af denne [tjenestebegrænsning](../setup/domains-faq.yml) vælger at administrere dine egne Microsoft DNS-poster på IONOS med 1&1, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster til mail, Skype for Business Online osv.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg afsnittet **TXT** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="Vælg afsnittet TXT.":::

1. På siden Tilføj en DNS-post skal du i felterne for den nye post skrive eller kopiere og indsætte værdierne fra følgende tabel.

    |Værtsnavn|Værdi|TTL|
    |---|---|---|
    |(Lad dette felt være tomt)|MS=ms *XXXXXXXXX*  <br/> BEMÆRK! Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|1 time|

1. Vælg **Gem**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Vælg Gem.":::

    Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft 365 og anmode Microsoft 365 om at søge efter posten. Når Microsoft finder den rigtige TXT-post, er dit domæne godkendt.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Indstillingsdomæner**</a>\>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

> [!NOTE]
> Hvis du har tilmeldt dig 1und1.de, [skal du logge på her](https://go.microsoft.com/fwlink/?linkid=859152).

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **MX-sektionen** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="Vælg MX-sektionen.":::

1. På siden Tilføj en DNS-post skal du i felterne for den nye post skrive eller kopiere og indsætte værdierne fra følgende tabel.

    |Værtsnavn|Peger på|Prioritet|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com  <br/>  BEMÆRK! Få din \<domain-key\> fra din Microsoft-konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|1 time|

1. Vælg **Gem**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Vælg Gem.":::

1. Hvis der allerede er angivet MX-poster, kan du slette dem alle ved at vælge papirkurven **Slet post** på siden **Tilføj post** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Vælg Slet post.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

> [!NOTE]
> Hvis du har tilmeldt dig 1und1.de, [skal du logge på her](https://go.microsoft.com/fwlink/?linkid=859152).

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

   Nu skal du oprette to underdomæner og angive en **aliasværdi** for hver.

   Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster.

   Først skal du oprette underdomænet Autodiscover.

1. Vælg **Underdomæner**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Vælg Underdomæne.":::

1. Vælg **Tilføj underdomæne**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Vælg Tilføj underdomæner.":::

1. I feltet **Tilføj underdomæne** for det nye underdomæne skal du skrive eller kopiere og kun indsætte værdien **Tilføj underdomæne** fra følgende tabel. (Du skal tilføje værdien **Alias** i et senere trin).

    |Tilføj underdomæne|Alias|
    |---|---|
    |Autodiscover|autodiscover.outlook.com|

1. Under **Handlinger** for det **underdomæne til automatisk søgning** , som du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten.

1. Vælg **Tilføj post**, og vælg derefter sektionen **CNAME** .

1. I feltet **Alias:** skal du skrive eller kopiere og kun indsætte værdien **Alias** fra følgende tabel.

    |Tilføj underdomæne|Alias|
    |---|---|
    |Autodiscover|autodiscover.outlook.com|

1. Vælg **Gem**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge værdisæt. Har du brug for eksempler? Se disse [poster i det eksterne domænenavnssystem til Microsoft](../../enterprise/external-domain-name-system-records.md). Hvis du vil validere din SPF-post, kan du bruge et af disse[SPF-valideringsværktøjer](../setup/domains-faq.yml).

> [!NOTE]
> Hvis du har tilmeldt dig 1und1.de, [skal du logge på her](https://go.microsoft.com/fwlink/?linkid=859152).

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg afsnittet **SPF (TXT).**

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="Vælg afsnittet SPF (TXT).":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    |Type|Værtsnavn|Værdi|TTL|
    |---|---|---|---|
    |SPF (TXT)|Lad feltet være tomt.|v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|1 time|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Vælg Gem.":::

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-two-additional-cname-records"></a>Tilføj to yderligere CNAME-poster

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

   Nu skal du oprette to underdomæner og angive en **aliasværdi** for hver.

   Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster.

   Først skal du oprette underdomænet lyncdiscover.

1. Vælg **Underdomæner**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Vælg Underdomæne.":::

1. Vælg **Tilføj underdomæne**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Vælg Tilføj underdomæner.":::

1. I feltet **Tilføj underdomæne** for det nye underdomæne skal du skrive eller kopiere og kun indsætte værdien **Tilføj underdomæne** fra følgende tabel. (Du skal tilføje værdien **Alias** i et senere trin).

    |Tilføj underdomæne|Alias|
    |---|---|
    |lyncdiscover   |webdir.online.lync.com  |

1. Under **Handlinger** for det **lyncdiscover-underdomæne** , du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten.

1. Vælg **Tilføj post**, og vælg derefter sektionen **CNAME** .

1. I feltet **Alias:** skal du skrive eller kopiere og kun indsætte værdien **Alias** fra følgende tabel.

    |Opret underdomæne|Alias|
    |---|---|
    |lyncdiscover|webdir.online.lync.com|

1. Opret et andet underdomæne (SIP): Vælg **Tilføj underdomæne**.

1. I feltet **Tilføj underdomæne** for det nye underdomæne skal du skrive eller kopiere og kun indsætte værdien **Tilføj underdomæne** fra følgende tabel. (Du skal tilføje værdien **Alias** i et senere trin).

    |Tilføj underdomæne|Alias|
    |---|---|
    |Sip|sipdir.online.lync.com|

1. Under **Handlinger** for det underdomæne, du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten.

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg sektionen **CNAME** .

1. I feltet **Alias:** skal du skrive eller kopiere og kun indsætte værdien **Alias** fra følgende tabel.

    |Opret underdomæne|Alias|
    |---|---|
    |Sip|sipdir.online.lync.com|

1. Markér afkrydsningsfeltet ud for ansvarsfraskrivelsen **Jeg ved,** og vælg derefter **Gem**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Tilføj de to SRV-poster, der kræves til Microsoft

> [!NOTE]
> Hvis du har tilmeldt dig 1und1.de, [skal du logge på her](https://go.microsoft.com/fwlink/?linkid=859152).

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg sektionen **SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="Vælg sektionen SRV.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    |Type|Tjeneste|Protokollen|Værtsnavn|Peger på|Prioritet|Vægt|Port|TTL|
    |---|---|---|---|---|---|---|---|---|
    |SRV|_sip|Tls|Lad feltet være tomt.|sipdir.online.lync.com|100|1|443|1 time|
    |SRV|_sipfederationtls|Tcp|Lad feltet være tomt.|sipfed.online.lync.com|100|1|5061|1 time|

1. Vælg **Gem**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden SRV-post.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to påkrævede CNAME-poster

> [!IMPORTANT]
> Følg den underdomæneprocedure, du brugte til de andre CNAME-poster, og angiv værdierne fra følgende tabel.

1. Du kommer i gang ved at gå til siden med domæner på IONOS efter 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du bliver bedt om at logge på.

1. Vælg **Menu**, og vælg derefter **Domæner og SSL**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::

1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

   Nu skal du oprette to underdomæner og angive en **aliasværdi** for hver.

   Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster.

   Først skal du oprette underdomænet lyncdiscover.

1. Vælg **Underdomæner**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Vælg Underdomæne.":::

1. Vælg **Tilføj underdomæne**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Vælg Tilføj underdomæner.":::

1. I feltet **Tilføj underdomæne** for det nye underdomæne skal du skrive eller kopiere og kun indsætte værdien **Tilføj underdomæne** fra følgende tabel. (Du skal tilføje værdien **Alias** i et senere trin).

    |Tilføj underdomæne|Alias|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Under **Handlinger** for det underdomæne af **typen enterpriseregistration** , som du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten.

1. Vælg **Tilføj post**, og vælg derefter sektionen **CNAME** .

1. I feltet **Alias:** skal du skrive eller kopiere og kun indsætte værdien **Alias** fra følgende tabel.

    |Tilføj underdomæne|Alias|
    |---|---|
    |enterpriseregistration|enterpriseregistration.windows.net|

1. Opret et andet underdomæne: Vælg **Tilføj underdomæne**.

1. I feltet **Tilføj underdomæne** for det nye underdomæne skal du skrive eller kopiere og kun indsætte værdien **Tilføj underdomæne** fra følgende tabel. (Du skal tilføje værdien **Alias** i et senere trin).

    |Tilføj underdomæne|Alias|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. Under **Handlinger** for det **underdomæne for enterpriseenrollment** , som du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten.

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg sektionen **CNAME** .

1. I feltet **Alias:** skal du skrive eller kopiere og kun indsætte værdien **Alias** fra følgende tabel.

    |Opret underdomæne|Alias|
    |---|---|
    |enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|

1. Markér afkrydsningsfeltet ud for ansvarsfraskrivelsen **Jeg ved,** og vælg derefter **Gem**.
