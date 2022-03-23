---
title: Forbind dine DNS-poster på Wix for at Microsoft 365
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
ms.assetid: 7173c635-58b3-400f-95e0-97abe915565e
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på Wix til Microsoft.
ms.openlocfilehash: 9a9e230a46967ab6c012199e7f4fc6426fdc67bf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588063"
---
# <a name="connect-your-dns-records-at-wix-to-microsoft-365"></a>Forbind dine DNS-poster på Wix for at Microsoft 365

**[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
Hvis Wix er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster hos Wix, konfigureres dit domæne til at fungere med Microsoft-tjenester.
  
> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette den senere, hvis du vil. 

> [!NOTE]
> WIX understøtter ikke DNS-poster for underdomæner.
  
1. For at komme i gang skal du gå til siden med dine domæner på Wix ved hjælp [af dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du vil blive bedt om at logge på først.

2. Vælg **Domains** > **...**, og vælg **derefter Manage DNS Records** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

3. Vælg **+ Tilføj post** i **rækken TXT (tekst)** i DNS-editoren.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Vælg Tilføj post.":::

4. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   ||||
   |:-----|:-----|:-----|
   | **Værtsnavn **<br/> | **TXT-værdi** <br/> | **TTL** <br/> |
   |Udfyldes automatisk (lad feltet være tomt)  <br/> |MS=ms *XXXXXXXX*  <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)|1 time <br/> |          |

5. **VælgSave**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.


Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den rette TXT-post, bekræftes dit domæne. 

Sådan bekræftes posten i Microsoft 365:
  
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du er ved at bekræfte, og vælge **Start installationen**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.
  
1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på Wix ved hjælp [af dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du vil blive bedt om at logge på først.

1. Vælg **Domains** > **...**, og vælg **derefter Manage DNS Records** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

1. Under **MX (Mail exchange) skal** du vælge **Edit MX Records**. 

   :::image type="content" source="../../media/dns-wix/wix-domains-edit-mx-records.png" alt-text="Vælg Rediger MX-poster.":::

1. Vælg **Andet** på rullelisten, og vælg **+ Tilføj post**.

   :::image type="content" source="../../media/dns-wix/wix-domains-other.png" alt-text="Vælg Andet på rullelisten.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel:

   | **Host Name** | **Peger på** | **Prioritet** | **TTL** |
   |:-----|:-----|:-----|:-----|
   |Udfyldes automatisk <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Bemærk!** Få din fra  *\<domain-key\>*  din Microsoft-konto.   [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md) |0  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) | 1 time|

1. Hvis der er angivet andre MX-poster, skal du slette hver af dem.

   :::image type="content" source="../../media/dns-wix/wix-domains-mx-delete.png" alt-text="Vælg Slet.":::

1. Vælg **Gem**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på Wix ved hjælp [af dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du vil blive bedt om at logge på først.

2. Vælg **Domains** > **...**, og vælg **derefter Manage DNS Records** på rullelisten. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

3. Vælg **+ Tilføj post** i **rækken CNAME (aliasser)** i DNS-editoren for CNAME-posten.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Vælg + Tilføj post.":::

4. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel:

   | **Host Name** | **Værdi** | **TTL** |
   |:-----|:-----|:-----|
   |autodiscover  <br/> |autodiscover.outlook.com  <br/> |1 time  <br/> |

5. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier.  
  
1. For at komme i gang skal du gå til siden med dine domæner på Wix ved hjælp [af dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du vil blive bedt om at logge på først.

2. Vælg **Domains** > **...**, og vælg **derefter Manage DNS Records** på rullelisten. 

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

3. Vælg **+ Tilføj post** i **rækken TXT (tekst)** i DNS-editoren.

   :::image type="content" source="../../media/dns-wix/wix-domains-TXT-add-record.png" alt-text="Vælg + Tilføj post.":::

   **Bemærk**! Wix indeholder en SPF-række i DNS-editoren. Ignorer denne række, og **brug rækken TXT (tekst)** til at angive nedenstående SPF-værdier. 

4. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel:

   | **Host Name** | **Værdi** | **TTL** |
   |:-----|:-----|:-----|
   |[lad dette stå tomt]  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.<br/> | 1 time |

5. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-txt-save.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge fire poster: to SRV-poster til bruger-til-bruger-kommunikation og to CNAME-poster til at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner på Wix ved hjælp [af dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du vil blive bedt om at logge på først.

1. Vælg **Domains** > **...**, og vælg **derefter Manage DNS Records** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

1. Vælg **+ Tilføj post** i rækken **SRV** i DNS-editoren.

   :::image type="content" source="../../media/dns-wix/wix-domains-srv-add-record.png" alt-text="Vælg + Tilføj post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i tabellen:

   | **Tjeneste** | **Protokol** | **Værtsnavn** | **Vægt** | **Port** | **Destination** | **Prioritet** | **TTL** |
   |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
   |sip  |tls  |Udfyldes automatisk |1  |443   |sipdir.online.lync.com |100 |1 time |
   |sipfed|tcp |Udfyldes automatisk|1 |5061 |sipfed.online.lync.com|100 | 1 time |

1. Vælg **Gem**.
  
   :::image type="content" source="../../media/dns-wix/wix-domains-srv-save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. Vælg **+ Tilføj en** anden i **rækken CNAME (Aliasser)** i DNS-editoren, og angiv værdierne fra den første række i nedenstående tabel.

   |**Type**|**Vært**|**Værdi**|**TTL**|
   |:-----|:-----|:-----|:-----|
   |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
   |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
  
1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Vælg Gem.":::
  
1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på Wix ved hjælp [af dette link](https://premium.wix.com/wix/api/mpContainerStaticController#/domains?referralAdditionalInfo=account). Du vil blive bedt om at logge på først.

1. Vælg **Domains** > **...**, og vælg **derefter Manage DNS Records** på rullelisten.

   :::image type="content" source="../../media/dns-wix/wix-domains-1.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

1. Vælg **+ Tilføj post** i **rækken CNAME (aliasser)** i DNS-editoren for CNAME-posten.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-add-record.png" alt-text="Vælg + Tilføj post.":::

1. Angiv værdierne fra den første række i nedenstående tabel.

    |**Type**|**Vært**|**Værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration <br/> |enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
  
1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-wix/wix-domains-cname-save.png" alt-text="Vælg Gem.":::
  
1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).