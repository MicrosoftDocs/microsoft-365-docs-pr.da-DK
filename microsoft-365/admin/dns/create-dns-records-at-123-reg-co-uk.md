---
title: Forbind dine DNS-poster på 123-reg.co.uk med Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester på 123-reg.co.uk til Microsoft.
ms.openlocfilehash: 97a00c046f467dd4ced4c63a4cbfc8114d06d2dd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563401"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Forbind dine DNS-poster på 123-reg.co.uk med Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis 123-reg.co.uk er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på 123-reg.co.uk, konfigureres dit domæne til at fungere sammen med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

2. Vælg **Domæner**, og vælg navnet på det domæne, du vil bekræfte, på siden Oversigt over domænenavne, eller gå til Kontrolpanel.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg det domæne, du vil bekræfte.":::

3. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

4. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. I feltet **Type** for den nye post skal du vælge **TXT/SPF** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

    |Værtsnavn|Type|Destinations-TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|MS=ms *XXXXXXXXX* <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Vælg TXT/SPF-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Vælg Tilføj.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om en søgning efter posten. Når Microsoft finder den rigtige TXT-post, er dit domæne godkendt.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Indstillingsdomæner**</a>\>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

2. På siden Oversigt over domænenavn skal du vælge navnet på det domæne, du vil redigere.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

4. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. I feltet **Type** for den nye post skal du vælge **MX** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

    |Værtsnavn|Type|Prioritet|Destinations-MX|
    |---|---|---|---|
    |@|MX|1 <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|*\<domain-key\>*.mail.protection.outlook.com. <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk:** Få din \<domain-key\> fra din Microsoft-konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Vælg MX-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Vælg Tilføj.":::

7. Hvis der er andre MX-poster, skal du fjerne hver enkelt ved at vælge ikonet **Slet (papirkurven)** for den pågældende post.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Vælg Slet (papirkurven).":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

2. På siden Oversigt over domænenavn skal du vælge navnet på det domæne, du vil redigere.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

4. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. Tilføj CNAME-posten.

    I feltet **Type** for den nye post skal du vælge **CNAME** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

    |Værtsnavn|Type|Destinations-CNAME|
    |---|---|---|
    |Autodiscover|CNAME|autodiscover.outlook.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Vælg typen CNAME på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Vælg Tilføj.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny for Microsfot. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge værdisæt. Har du brug for eksempler? Se disse [poster i det eksterne domænenavnssystem til Microsoft](../../enterprise/external-domain-name-system-records.md). Hvis du vil validere din SPF-post, kan du bruge et af disse [SPF-valideringsværktøjer](../setup/domains-faq.yml).

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

2. På siden Oversigt over domænenavn skal du vælge navnet på det domæne, du vil redigere.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

4. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. I feltet **Type** for den nye post skal du vælge **TXT/SPF** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

    |Værtsnavn|Type|Destinations-TXT/SPF|
    |---|---|---|
    |@|TXT/SPF|v=spf1 include:spf.protection.outlook.com -all <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Vælg TXT/SPF-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

2. På siden Oversigt over domænenavn skal du vælge navnet på det domæne, du vil redigere.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

4. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. Tilføj den første af de to SRV-poster:

   I feltet **Type** for den nye post skal du vælge **SRV** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

    |Værtsnavn|Type|Prioritet|TTL|Destinations-SRV|
    |---|---|---|---|---|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Vælg TXT/SPF-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Vælg Tilføj.":::

7. Tilføj den anden SRV-post.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

1. På siden Oversigt over domænenavn skal du vælge navnet på det domæne, du vil redigere.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

1. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

1. Tilføj den første CNAME-post.

    I feltet **Type** for den nye post skal du vælge **CNAME** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

    |Værtsnavn|Type|Destinations-CNAME|
    |---|---|---|
    |Sip|CNAME|sipdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|
    |lyncdiscover|CNAME|webdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Vælg typen CNAME på rullelisten, og udfyld værdierne.":::

1. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Vælg Tilføj.":::

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden domæner på 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du bliver bedt om at logge på først.

1. På siden Oversigt over domænenavn skal du vælge navnet på det domæne, du vil redigere.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

1. På siden Administrer domæne under **Avancerede domæneindstillinger** skal du vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. På siden Administrer din DNS skal du vælge fanen **Avanceret DNS** .

   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

1. Tilføj den første CNAME-post.

    I feltet **Type** for den nye post skal du vælge **CNAME** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra følgende tabel.

   |Værtsnavn|Type|Destinations-CNAME|
   |---|---|---|
   |enterpriseregistration|CNAME|enterpriseregistration.windows.net. <br/> **Denne værdi SKAL slutte med et punktum (.)**|
   |enterpriseenrollment|CNAME|enterpriseenrollment.manage.microsoft.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Vælg typen CNAME på rullelisten, og udfyld værdierne.":::

1. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Vælg Tilføj.":::

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
