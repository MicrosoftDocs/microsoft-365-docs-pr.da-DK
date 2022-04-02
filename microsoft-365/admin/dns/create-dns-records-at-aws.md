---
title: Forbind DINE DNS-poster på Amazon Web Services (AWS) for at Microsoft 365
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
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på Amazon Web Services (AWS) for Microsoft.
ms.openlocfilehash: b07ee3d44c3c36115a3ce35d4517e834f212689f
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568027"
---
# <a name="connect-your-dns-records-at-amazon-web-services-aws-to-microsoft-365"></a>Forbind DINE DNS-poster på Amazon Web Services (AWS) for at Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

Hvis AWS er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype Online for Business osv.

Når du har tilføjet disse poster på AWS, konfigureres dit domæne til at fungere med Microsoft-tjenester.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil.

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på det domæne, du vil bekræfte.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på det domæne, du vil bekræfte.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Type** **og** Routing policy på rullelisterne).

    > [!TIP]
    > Anførselstegnene, der kræves i vejledningen på skærmen, leveres automatisk. Du behøver ikke at skrive dem manuelt.

    |Postnavn|Posttype|Værdi|TTL (sekunder)|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |Lad dette felt være tomt.|TXT – bruges til at bekræfte mailafsendere|MS=*msXXXXXXXX* <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen i Microsoft 365. [Hvordan gør jeg du finde dette?](../get-help-with-domains/information-for-dns-records.md)|300|Enkel|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Vælg Opret poster.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om en søgning efter posten. Når Microsoft finder den rette TXT-post, bekræftes dit domæne.

Sådan bekræftes posten i Microsoft 365:

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du er ved at bekræfte, og vælge **Start installationen**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft-365"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft 365

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Type** **og** Routing policy på rullelisterne).

    > [!TIP]
    > Anførselstegnene, der kræves i vejledningen på skærmen, leveres automatisk. Du behøver ikke at skrive dem manuelt.

    |Postnavn|Posttype|Værdi|TTL (sekunder)|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |Lad dette felt være tomt.|MX – Angiver mailservere|0,mail.protection.outlook.com *\<domain-key\>*. <br/> 0 er MX-prioritetsværdien. Føj 0 til begyndelsen af MX-værdien, og adskid den fra resten af værdien ved hjælp af et mellemrum. <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk!** Få din \<*domain-key*\> fra din Microsoft 365 konto. [Hvordan gør jeg du finde dette?](../get-help-with-domains/information-for-dns-records.md)|300|Simpel routing|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-mx-create-records.png" alt-text="Vælg Opret poster.":::

1. Hvis der er andre MX-poster, skal du fjerne dem ved at markere posten og derefter vælge **Delete**.

## <a name="add-the-cname-record-required-for-microsoft-365"></a>Tilføj den CNAME-post, der kræves til Microsoft 365

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Type** **og** Routing policy på rullelisterne).

    |Postnavn|Posttype|Værdi|TTL|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |autodiscover|CNAME – Ruter trafik til et andet domænenavn|autodiscover.outlook.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Enkel|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Vælg Opret poster.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge sæt af værdier. Har du brug for eksempler? Se disse [eksterne DNS-poster for Microsoft](../../enterprise/external-domain-name-system-records.md). Hvis du vil validere din SPF-post, kan du bruge et af disse [SPF-valideringsværktøjer](../setup/domains-faq.yml).

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    Vælg **værdien Type** på rullelisterne.

    |Posttype|Værdi|
    |:-----|:-----|
    |TXT- Bruges til at bekræfte mailafsendere og for programspecifikke værdier|v=spf1 include:spf.protection.outlook.com -all <br/> Anførselstegnene, der kræves i vejledningen på skærmen, vises automatisk. Du behøver ikke at skrive dem manuelt.) <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.|

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-txt-create-records.png" alt-text="Vælg Opret poster.":::

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Type** **og Routing** Policy på rullelisterne).

    |Postnavn|Posttype|Værdi|TTL (sekunder)|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|SRV – Programspecifikke værdier, som id-servere|100 1 443 sipdir.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**> <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.|300|Enkel|
    |_sipfederationtls._tcp|SRV – Programspecifikke værdier, som id-servere|100 1 5061 sipfed.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.|300|Enkel|

1. Hvis du vil tilføje den anden SRV-post, skal du vælge Tilføj en anden **post, oprette** en post med værdierne fra næste række i tabellen og derefter igen **vælge Create records**.

   :::image type="content" source="../../media/dns-aws/aws-domians-srv-create-records.png" alt-text="Vælg Opret poster.":::

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Type** **og** Routing policy på rullelisterne).

    |Postnavn|Posttype|Værdi|TTL|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |sip|CNAME - Canonical name|sipdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Enkel|
    |lyncdiscover|CNAME - Canonical name|webdir.online.lync.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Enkel|

1. Hvis du vil tilføje den anden CNAME-post, skal du vælge Tilføj en anden **post, oprette** en post med værdierne fra den næste række i tabellen.

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Vælg Opret poster.":::

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Indstillingen Avanceret: Intune og mobildata Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobile Enhedshåndtering skal bruge to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to nødvendige CNAME-poster for Mobile Enhedshåndtering

1. For at komme i gang skal du gå til siden med dine domæner på AWS ved hjælp [af dette link](https://console.aws.amazon.com/route53/home). Du vil blive bedt om at logge på først.

1. På **landingssiden** skal **du under Domæner** vælge Registrerede domæner.

1. Under **Domain Name** skal du vælge det domæne, du vil konfigurere i Microsoft 365.

    **Bemærk**! Hvis du ikke har oprettet en værtsbaseret zone for dit domæne, skal du vælge Opret værtsbaseret **zone** og udføre trinnene, før du går videre til næste trin.

   :::image type="content" source="../../media/dns-aws/aws-domains-1.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **DNS-styring**.

   :::image type="content" source="../../media/dns-aws/aws-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Domænenavn skal** du vælge domænenavnet for den hostede zoneversion af det domæne, du vil bekræfte.

   :::image type="content" source="../../media/dns-aws/aws-domains-3.png" alt-text="Vælg navnet på domænet.":::

1. Vælg **Opret post**.

   :::image type="content" source="../../media/dns-aws/aws-domains-create-record.png" alt-text="Vælg Opret post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Type** **og** Routing policy på rullelisterne).

    |Postnavn|Posttype|Værdi|TTL|Routingpolitik|
    |:-----|:-----|:-----|:-----|:-----|
    |enterpriseregistration|CNAME - Canonical name|enterpriseregistration.windows.net. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Enkel|
    |enterpriseenrollment|CNAME - Canonical name|enterpriseenrollment-s.manage.microsoft.com. <br/> **Denne værdi SKAL slutte med et punktum (.)**|300|Enkel|

1. Hvis du vil tilføje den anden CNAME-post, skal du vælge Tilføj en anden **post, oprette** en post med værdierne fra den næste række i tabellen.

1. Vælg **Opret poster**.

   :::image type="content" source="../../media/dns-aws/aws-domains-cname-create-records.png" alt-text="Vælg Opret poster.":::

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
