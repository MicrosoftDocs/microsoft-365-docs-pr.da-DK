---
title: Forbind dine DNS-poster på Wix til Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos Wix til Microsoft.
ms.openlocfilehash: 9ae245481173b99a9cb1221ed0650dc0b91feecd
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563181"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Forbind dine DNS-poster på Wix til Microsoft 365

**[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis Wix er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på Wix, konfigureres dit domæne til at fungere sammen med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sørge for, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

> [!NOTE]
> WIX understøtter ikke DNS-poster for underdomæner.

1. Du kommer i gang ved at gå til siden med domæner på Wix ved hjælp af [dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du bliver bedt om at logge på først.

2. Vælg **Domæner** \> **...**, og vælg derefter **Administrer DNS-poster** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

3. Vælg **+ Tilføj post** i rækken **TXT (Text)** i DNS-editoren.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Vælg Tilføj post.":::

4. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   |Værtsnavn|TXT-værdi|TTL|
   |---|---|---|
   |Udfyldes automatisk (lad argumentet være tomt)|MS=ms *XXXXXXXXX* <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|1 time|

5. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.


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

1. Du kommer i gang ved at gå til siden med domæner på Wix ved hjælp af [dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du bliver bedt om at logge på først.

1. Vælg **Domæner** \> **...**, og vælg derefter **Administrer DNS-poster** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

1. Under **MX (Mailudveksling)** skal du vælge **Rediger MX-poster**.

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="Vælg Rediger MX-poster.":::

1. Vælg **Andet** på rullelisten, og vælg **+ Tilføj post**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Vælg Andet på rullelisten.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel:

   |Værtsnavn|Peger på|Prioritet|TTL|
   |---|---|---|---|
   |Udfyldt automatisk|*\<domain-key\>*.mail.protection.outlook.com <br/> **Bemærk:** Få din *\<domain-key\>* fra din Microsoft-konto.  [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|0 <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|1 time|

1. Hvis der er andre MX-poster på listen, skal du slette dem alle.

  :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Vælg Slet.":::

1. Vælg **Gem**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på Wix ved hjælp af [dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du bliver bedt om at logge på først.

2. Vælg **Domæner** \> **...**, og vælg derefter **Administrer DNS-poster** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

3. Vælg **+ Tilføj post** i rækken **CNAME (Aliasser)** i DNS-editoren for CNAME-posten.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Vælg + Tilføj post.":::

4. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel:

   |Værtsnavn|Værdi|TTL|
   |---|---|---|
   |Autodiscover|autodiscover.outlook.com|1 time|

5. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden med domæner på Wix ved hjælp af [dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du bliver bedt om at logge på først.

2. Vælg **Domæner** \> **...**, og vælg derefter **Administrer DNS-poster** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

3. Vælg **+ Tilføj post** i rækken **TXT (Text)** i DNS-editoren.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Vælg + Tilføj post.":::

   **Bemærk**! Wix indeholder en SPF-række i DNS-editoren. Ignorer rækken, og brug rækken **TXT (Text)** til at angive SPF-værdierne nedenfor.

4. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel:

   |Værtsnavn|Værdi|TTL|
   |---|---|---|
   |[Lad dette være tomt]|v=spf1 include:spf.protection.outlook.com -all <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|1 time|

5. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge fire poster: to SRV-poster til bruger-til-bruger-kommunikation og to CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden med domæner på Wix ved hjælp af [dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du bliver bedt om at logge på først.

1. Vælg **Domæner** \> **...**, og vælg derefter **Administrer DNS-poster** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

1. Vælg **+ Tilføj post** i rækken **SRV** i DNS-editoren.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="Vælg + Tilføj post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i tabellen:

   |Tjeneste|Protokollen|Værtsnavn|Vægt|Port|Mål|Prioritet|TTL|
   |---|---|---|---|---|---|---|---|
   |Sip|Tls|Udfyldt automatisk|1|443|sipdir.online.lync.com|100|1 time|
   |sipfed|Tcp|Udfyldt automatisk|1|5061|sipfed.online.lync.com|100|1 time|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Vælg **+ Tilføj en anden** i rækken **CNAME (Aliasser)** i DNS-editoren, og angiv værdierne fra den første række i følgende tabel.

   |Type|Vært|Værdi|TTL|
   |---|---|---|---|
   |CNAME|Sip|sipdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|
   |CNAME|lyncdiscover|webdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden med domæner på Wix ved hjælp af [dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du bliver bedt om at logge på først.

1. Vælg **Domæner** \> **...**, og vælg derefter **Administrer DNS-poster** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Administrer DNS-poster på rullelisten.":::

1. Vælg **+ Tilføj post** i rækken **CNAME (Aliasser)** i DNS-editoren for CNAME-posten.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Vælg + Tilføj post.":::

1. Angiv værdierne fra den første række i følgende tabel.

    |Type|Vært|Værdi|TTL|
    |---|---|---|---|
    |CNAME|enterpriseregistration|enterpriseregistration.windows.net. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|
    |CNAME|enterpriseenrollment|enterpriseenrollment.manage.microsoft.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
