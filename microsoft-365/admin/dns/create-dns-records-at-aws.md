---
title: Forbind dine DNS-poster på Amazon Web Services (AWS) for at Microsoft 365
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
ms.assetid: 7a2efd75-0771-4897-ba7b-082fe5bfa9da
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos Amazon Web Services (AWS) til Microsoft.
ms.openlocfilehash: d194e425485a45d2c3dc949fc85e74bc957932fb
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780649"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Forbind dine DNS-poster på Amazon Web Services (AWS) for at Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis AWS er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype Online for Business osv.

Når du har tilføjet disse poster i AWS, konfigureres dit domæne til at arbejde med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på det domæne, du vil bekræfte.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på det domæne, du vil bekræfte.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **politikværdierne** **Type** og Routing på rullelisten.

    > [!TIP]
    > De anførselstegn, der kræves i vejledningen på skærmen, angives automatisk. Du behøver ikke skrive dem manuelt.

    |Postnavn|Posttype|Værdi|TTL (sekunder)|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |Lad feltet være tomt.|TXT – Bruges til at bekræfte afsendere af mails|MS=*msXXXXXXXXX* <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke værdi **for Destination eller Adressepunkter** her fra tabellen i Microsoft 365. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|300|Simpel|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Vælg Opret poster.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om en søgning efter posten. Når Microsoft finder den korrekte TXT-post, bekræftes dit domæne.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft 365

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg domænets navn.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg domænets navn.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **politikværdierne** **Type** og Routing på rullelisten.

    > [!TIP]
    > De anførselstegn, der kræves i vejledningen på skærmen, angives automatisk. Du behøver ikke skrive dem manuelt.

    |Postnavn|Posttype|Værdi|TTL (sekunder)|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |Lad feltet være tomt.|MX – angiver mailservere|0 *\<domain-key\>*.mail.protection.outlook.com. <br/> 0 er MX-prioritetsværdien. Føj den til begyndelsen af MX-værdien adskilt fra resten af værdien med et mellemrum. <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk:** Få din \<*domain-key*\> fra din Microsoft 365 konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|300|Enkel routing|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-mx-create-records.png" alt-text="Vælg Opret poster.":::

1. Hvis der er andre MX-poster, skal du fjerne dem ved at vælge posten og derefter vælge **Slet**.

## <a name="add-the-cname-record-required-for-microsoft-365"></a>Tilføj den CNAME-post, der kræves til Microsoft 365

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg domænets navn.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg domænets navn.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **politikværdierne** **Type** og Routing på rullelisten.

    |Postnavn|Posttype|Værdi|TTL|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |Autodiscover|CNAME – Dirigerer trafik til et andet domænenavn|autodiscover.outlook.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Simpel|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Vælg Opret poster.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge værdisæt. Har du brug for eksempler? Se disse [poster i det eksterne domænenavnssystem til Microsoft](../../enterprise/external-domain-name-system-records.md). Hvis du vil validere din SPF-post, kan du bruge et af [disseSPF-valideringsværktøjer](../setup/domains-faq.yml).

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg domænets navn.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg domænets navn.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg værdien **Type** på rullelisterne.

    |Posttype|Værdi|
    |:-----|:-----|
    |TXT– Bruges til at bekræfte afsendere af mails og til programspecifikke værdier|v=spf1 include:spf.protection.outlook.com -all <br/> (De anførselstegn, der kræves i vejledningen på skærmen, angives automatisk. Du behøver ikke skrive dem manuelt. <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Vælg Opret poster.":::

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg domænets navn.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg domænets navn.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg værdierne **Type** og **Routing Policy** på rullelisten.

    |Postnavn|Posttype|Værdi|TTL (sekunder)|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV – Programspecifikke værdier, der id-servere|100 1 443 sipdir.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**> <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|300|Simpel|
    |_sipfederationtls._tcp|SRV – Programspecifikke værdier, der id-servere|100 1 5061 sipfed.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|300|Simpel|

1. Hvis du vil tilføje den anden SRV-post, skal du vælge **Tilføj en anden post**, oprette en post ved hjælp af værdierne fra den næste række i tabellen og derefter igen vælge **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domians-srv-create-records.png" alt-text="Vælg Opret poster.":::

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg domænets navn.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg domænets navn.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **politikværdierne** **Type** og Routing på rullelisten.

    |Postnavn|Posttype|Værdi|TTL|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |Sip|CNAME – Vedtaget navn|sipdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Simpel|
    |lyncdiscover|CNAME – Vedtaget navn|webdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Simpel|

1. Hvis du vil tilføje den anden CNAME-post, skal du vælge **Tilføj en anden post**, oprette en post ved hjælp af værdierne fra den næste række i tabellen.

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Vælg Opret poster.":::

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden med domæner på AWS ved hjælp af [dette link](https://console.aws.amazon.com/route53/home). Du bliver bedt om at logge på først.

1. Vælg Registrerede domæner under **Domæner** på **landingssiden**.

1. Under **Domænenavn** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en hostet zone for dit domæne, skal du vælge **Opret hostet zone** og fuldføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg domænets navn.":::

1. Vælg **Administrer DNS**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Domænenavn** skal du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg domænets navn.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **politikværdierne** **Type** og Routing på rullelisten.

    |Postnavn|Posttype|Værdi|TTL|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration|CNAME – Vedtaget navn|enterpriseregistration.windows.net. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Simpel|
    |enterpriseenrollment|CNAME – Vedtaget navn|enterpriseenrollment-s.manage.microsoft.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Simpel|

1. Hvis du vil tilføje den anden CNAME-post, skal du vælge **Tilføj en anden post**, oprette en post ved hjælp af værdierne fra den næste række i tabellen.

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Vælg Opret poster.":::

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
