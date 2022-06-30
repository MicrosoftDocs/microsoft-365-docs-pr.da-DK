---
title: Forbind dine DNS-poster på Namecheap til Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos Namecheap til Microsoft.
ms.openlocfilehash: 8af8b88cc2bdd0c819f349e2820d637b99e6d730
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563335"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>Forbind dine DNS-poster på Namecheap til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis Namecheap er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på Namecheap, konfigureres dit domæne til at fungere sammen med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden domæner på Namecheap ved hjælp af [dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. Vælg **Domæneliste** på rullelisten under **Konto** på landingssiden.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste på rullelisten.":::

1. Vælg det domæne, du vil redigere, på siden Domæneliste, og vælg derefter **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I afsnittet **VÆRTSPOSTER** skal du vælge **TILFØJ NY POST**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. Vælg **TXT Record** på rullelisten **Type**.

    > [!NOTE]
    > Rullelisten **Type** vises automatisk, når du vælger **TILFØJ NY POST**.

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="Vælg TXT-post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **TTL-værdien** på rullelisten.

    |Type|Vært|Værdi|TTL|
    |---|---|---|---|
    |TXT|@|MS=ms *XXXXXXXXX*  <br/>**Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her.  [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|30 min.|

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** (flueben).

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den rigtige TXT-post, er dit domæne godkendt.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Indstillingsdomæner**</a>\>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden domæner på Namecheap ved hjælp af [dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. Vælg **Domæneliste** på rullelisten under **Konto** på landingssiden.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste på rullelisten.":::

1. På siden **Domæneliste** skal du vælge det domæne, du vil redigere, og derefter vælge **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I afsnittet **MAILINDSTILLINGER** skal du vælge **Brugerdefineret MX** på rullelisten **Videresendelse af mail** .

    (Du skal muligvis rulle ned).

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="Vælg Brugerdefineret MX.":::

1. Vælg **Tilføj ny post**.

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="TILFØJ NY POST.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Feltet **Prioritet** er det ikke-navngivne felt til højre for feltet **Værdi** . Vælg **TTL-værdien** på rullelisten.

    |Type|Vært|Værdi|Prioritet|TTL|
    |---|---|---|---|---|
    |MX-post|@|\<*domain-key*\>.mail.protection.outlook.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk:** Få din *\<domain-key\>* fra din Microsoft-konto.  [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|0  <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|30 min.|

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** (flueben).

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Hvis der er andre MX-poster, skal du bruge følgende totrinsproces til at fjerne dem alle:

    Først skal du vælge **Slet** (papirkurven) for den post, du vil fjerne.

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="Vælg Slet.":::

    For det andet skal du vælge **Ja** for at bekræfte sletningen.

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="Vælg Ja.":::

    Fjern alle MX-poster undtagen den, du tilføjede tidligere i denne procedure.

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden domæner på Namecheap ved hjælp af [dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. Vælg **Domæneliste** på rullelisten under **Konto** på landingssiden.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domæneliste** skal du vælge det domæne, du vil redigere, og derefter vælge **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I afsnittet **VÆRTSPOSTER** skal du vælge **TILFØJ NY POST**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. På rullelisten **Type** skal du vælge **CNAME Record**.

    > [!NOTE]
    > Rullelisten **Type** vises automatisk, når du vælger **TILFØJ NY POST**.

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Vælg CNAME-post.":::

1. I de tomme felter for den nye post skal du vælge **CNAME** for **Posttype** og derefter skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

    |Type|Vært|Værdi|TTL|
    |---|---|---|---|
    |CNAME|Autodiscover|autodiscover.outlook.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** (flueben).

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en *enkelt*  SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden domæner på Namecheap ved hjælp af [dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

1. Vælg **Domæneliste** på rullelisten under **Konto** på landingssiden.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domæneliste** skal du vælge det domæne, du vil redigere, og derefter vælge **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I afsnittet **VÆRTSPOSTER** skal du vælge **TILFØJ NY POST**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. Vælg **TXT Record** på rullelisten **Type**.

    > [!NOTE]
    > Rullelisten **Type** vises automatisk, når du vælger **TILFØJ NY POST**.

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="Vælg TXT-post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier fra følgende tabel.

    Vælg **TTL-værdien** på rullelisten.

    |Type|Vært|Værdi|TTL|
    |---|---|---|---|
    |TXT|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|30 min.|

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** (flueben).

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden domæner på Namecheap ved hjælp af [dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. Vælg **Domæneliste** på rullelisten under **Konto** på landingssiden.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domæneliste** skal du vælge det domæne, du vil redigere, og derefter vælge **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I afsnittet **VÆRTSPOSTER** skal du vælge **TILFØJ NY POST**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. Vælg **SRV-post** på rullelisten **Type**.

    > [!NOTE]
    > Rullelisten **Type** vises automatisk, når du vælger **TILFØJ NY POST**.

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Vælg SRV-posttypen.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

    |Tjeneste|Protokollen|Prioritet|Vægt|Port|Mål|TTL|
    |---|---|---|---|---|---|---|
    |_sip|_tls|100|1|443|sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|
    |_sipfederationtls|_tcp|100|1|5061|sipfed.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|

     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** (flueben).

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Tilføj den anden SRV-post ved at vælge værdierne i den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. I afsnittet **VÆRTSPOSTER** skal du vælge **TILFØJ NY POST**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NYT NAVN.":::

1. Vælg **CNAME** på rullelisten **Type**.

    > [!NOTE]
    > Rullelisten **Type** vises automatisk, når du vælger **TILFØJ NY POST**.

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Vælg CNAME.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i tabellen.

    |Type|Vært|Værdi|TTL|
    |---|---|---|---|
    |CNAME|Sip|sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|
    |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Kopiér og indsæt CNAME-værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** (flueben).

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Tilføj den anden CNAME-post ved at vælge værdierne i den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden domæner på Namecheap ved hjælp af [dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. Vælg **Domæneliste** på rullelisten under **Konto** på landingssiden.

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domæneliste** skal du vælge det domæne, du vil redigere, og derefter vælge **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

1. I afsnittet **VÆRTSPOSTER** skal du vælge **TILFØJ NY POST**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. På rullelisten **Type** skal du vælge **CNAME Record**.

    > [!NOTE]
    > Rullelisten **Type** vises automatisk, når du vælger **TILFØJ NY POST**.

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Vælg CNAME-post.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i tabellen.

    |Type|Vært|Værdi|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|
    |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|Automatisk|

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg kontrolelementet **Gem ændringer** .

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Tilføj den anden CNAME-post ved at vælge værdierne i den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
