---
title: Forbind DINE DNS-poster 123-reg.co.uk at Microsoft 365
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
ms.assetid: 1f2d08c9-2a88-4d2f-ae1f-e39f9e358b17
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på 123-reg.co.uk til Microsoft.
ms.openlocfilehash: 050aad4ca3e0e768b160a7ba210a93e163d72fe7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588275"
---
# <a name="connect-your-dns-records-at-123-regcouk-to-microsoft-365"></a>Forbind DINE DNS-poster 123-reg.co.uk at Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
Hvis 123-reg.co.uk er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.
  
Når du har tilføjet disse poster 123-reg.co.uk, konfigureres dit domæne til at fungere med Microsoft-tjenester. 
  
> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil. 
  
1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

2. Vælg **Domæner**, og på siden Domain name overview skal du vælge navnet på det domæne, du vil bekræfte, eller gå til Kontrolpanel.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg det domæne, du vil bekræfte.":::

3. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
4. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::
  
5. I feltet **Type** for den nye post skal du vælge **TXT/SPF** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel. 

    ||||
    |:-----|:-----|:-----|
    |**Værtsnavn** <br/> |**Type** <br/> |**Destinations-TXT/-SPF** <br/> |
    |@  <br/> |TXT/SPF  <br/> |MS=ms *XXXXXXXX*  <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Vælg TXT-/SPF-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Vælg Tilføj.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om en søgning efter posten. Når Microsoft finder den rette TXT-post, bekræftes dit domæne.
  
Sådan bekræftes posten i Microsoft 365:
  
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du er ved at bekræfte, og vælge **Start installationen**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.
  
1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

2. På siden Domain name overview skal du vælge navnet på det domæne, du vil redigere. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
4. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. I feltet **Type** for den nye post skal du vælge **MX** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel.

    |**Værtsnavn**|**Type**|**Prioritet**|**Destinations-MX**|
    |:-----|:-----|:-----|:-----|
    |@  <br/> |MX  <br/> |1  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/> | *\<domain-key\>*  .mail.protection.outlook.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk!** Få din fra \<domain-key\> din Microsoft-konto. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX.png" alt-text="Vælg MX-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-Add.png" alt-text="Vælg Tilføj.":::

7. Hvis der er andre MX-poster, skal du fjerne hver af dem ved at vælge **ikonet Delete (papirkurv)** for den pågældende post.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-MX-delete.png" alt-text="Vælg Slet (papirkurv).":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

2. På siden Domain name overview skal du vælge navnet på det domæne, du vil redigere. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
4. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. Tilføj CNAME-posten.

    I feltet **Type** for den nye post skal du vælge **CNAME** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel.

    |**Værtsnavn**|**Type**|**Destinations-CNAME**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |CNAME  <br/> |autodiscover.outlook.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Vælg CNAME-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Vælg Tilføj.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsfot. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier. Har du brug for eksempler? Se disse [eksterne DNS-poster for Microsoft](../../enterprise/external-domain-name-system-records.md). Hvis du vil validere din SPF-post, kan du bruge et af disse [SPF-valideringsværktøjer](../setup/domains-faq.yml). 
  
1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

2. På siden Domain name overview skal du vælge navnet på det domæne, du vil redigere. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
4. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. I feltet **Type** for den nye post skal du vælge **TXT/SPF** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel.

    |**Værtsnavn**|**Type**|**Destinations-TXT/-SPF**|
    |:-----|:-----|:-----|
    |@  <br/> |TXT/SPF  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.           |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Vælg TXT-/SPF-typen på rullelisten, og udfyld værdierne.":::
  
6. Vælg **Tilføj**.

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

2. På siden Domain name overview skal du vælge navnet på det domæne, du vil redigere. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

3. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
4. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

5. Tilføj den første af de to SRV-poster:

   I feltet **Type** for den nye post skal du vælge **SRV** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel.

    ||||||
    |:-----|:-----|:-----|:-----|:-----|
    |**Værtsnavn**|**Type**|**Prioritet**|**TTL**|**Destinations-SRV**|
    |_sip._tls|SRV|100|3600|1 443 sipdir.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**<br> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.           |
    |_sipfederationtls._tcp|SRV|100|3600|1 5061 sipfed.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)** <br> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.           |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TypeTXTSPF.png" alt-text="Vælg TXT-/SPF-typen på rullelisten, og udfyld værdierne.":::

6. Vælg **Tilføj**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-TXTSPF-Add.png" alt-text="Vælg Tilføj.":::

7. Tilføj den anden SRV-post.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster 

1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

1. På siden Domain name overview skal du vælge navnet på det domæne, du vil redigere. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

1. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
1. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

1. Tilføj den første CNAME-post.

    I feltet **Type** for den nye post skal du vælge **CNAME** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel.

    | **Værtsnavn** |**Type**|**Destinations-CNAME**|
    |:-----|:-----|:-----|
    |sip  <br/>|CNAME  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |
    |lyncdiscover  <br/>|CNAME  <br/> |webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Vælg CNAME-typen på rullelisten, og udfyld værdierne.":::

1. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Vælg Tilføj.":::
  
1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner 123-reg.co.uk ved hjælp af [dette link](https://www.123-reg.co.uk/secure/cpanel/domain/overview). Du vil blive bedt om at logge på først.

1. På siden Domain name overview skal du vælge navnet på det domæne, du vil redigere. 

   :::image type="content" source="../../media/dns-123reg/123reg-domains-1.png" alt-text="Vælg navnet på det domæne, du vil redigere.":::

1. På siden Manage domain under **Advanced domain settings skal du** vælge **Manage DNS**.
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-2.png" alt-text="Vælg DNS-styring på rullelisten.":::
  
1. På siden Manage your DNS skal du vælge **fanen Advanced DNS** . 
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-3.png" alt-text="Vælg fanen Avanceret DNS.":::

1. Tilføj den første CNAME-post.

    I feltet **Type** for den nye post skal du vælge **CNAME** på rullelisten og derefter skrive eller kopiere og indsætte de andre værdier fra den nedenstående tabel.

   | **Værtsnavn**|**Type**|**Destinations-CNAME**|
   |:-----|:-----|:-----|
   | enterpriseregistration <br/> | CNAME  <br/> |enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |
   |enterpriseenrollment  <br/> | CNAME  <br/> |enterpriseenrollment.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |
  
   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME.png" alt-text="Vælg CNAME-typen på rullelisten, og udfyld værdierne.":::

1. Vælg **Tilføj**.

   :::image type="content" source="../../media/dns-123reg/123reg-domains-CNAME-Add.png" alt-text="Vælg Tilføj.":::

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).