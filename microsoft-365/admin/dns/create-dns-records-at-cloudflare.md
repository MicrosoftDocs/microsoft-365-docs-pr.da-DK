---
title: Forbind dine DNS-poster på Cloudflare for at Microsoft 365
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
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på Cloudflare til Microsoft.
ms.openlocfilehash: 5cf6483c7f560f5ab3ed2074dbaebf6c893dca3e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588509"
---
# <a name="connect-your-dns-records-at-cloudflare-to-microsoft-365"></a>Forbind dine DNS-poster på Cloudflare for at Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 

Hvis Cloudflare er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

## <a name="before-you-begin"></a>Før du begynder

Du har to muligheder for at konfigurere DNS-poster for dit domæne:

- [**Brug domæne Forbind**](#use-domain-connect-to-verify-and-set-up-your-domain) Hvis du ikke har konfigureret dit domæne med en anden mail serviceudbyder, skal du bruge trinnene til Domain Forbind til automatisk at bekræfte og konfigurere dit nye domæne til brug med Microsoft 365. 

    ELLER

- [**Brug de manuelle trin**](#create-dns-records-with-manual-setup) Bekræft dit domæne ved hjælp af de manuelle trin nedenfor, og vælg, hvornår og hvilke poster du vil føje til din domæneregistrator. Dette giver dig mulighed for at konfigurere nye MX-poster (mail), f.eks. når det passer dig. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Brug domæneadministrator Forbind at bekræfte og konfigurere dit domæne

Følg disse trin for automatisk at bekræfte og konfigurere dit Cloudflare-domæne med Microsoft 365:

1. I dialogboksen Microsoft 365 Administration du **vælge Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> og vælge det domæne, du vil konfigurere.

1. Vælg de tre > vælg **Start installationen**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. På siden Hvordan vil du forbinde dit domæne? skal du vælge **Fortsæt**.

1. På siden Tilføj DNS-poster skal du vælge **Tilføj DNS-poster**.

1. På Cloudflare-logonsiden skal du logge på din konto og vælge **Godkend**.

    Dette fuldfører domænekonfigurationen for Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>Oprette DNS-poster med manuel konfiguration

Når du har tilføjet disse poster på Cloudflare, konfigureres dit domæne til at fungere med Microsoft 365 tjenester.

> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
### <a name="change-your-domains-nameserver-ns-records"></a>Ændre dit domænes navneserverposter (NS)-poster

> [!IMPORTANT]
> Du skal udføre denne procedure hos domæneregistratoren, hvor du har købt og registreret dit domæne. 
  
Da du tilmeldte dig Cloudflare, tilføjede du et domæne ved hjælp af Konfigurationsprocessen for Cloudflare. 
  
Det domæne, du tilføjede, blev købt hos Cloudflare eller en separat domæneregistrator. For at bekræfte og oprette DNS-poster for dit domæne i Microsoft 365 skal du først ændre navneserverne hos din domæneregistrator, så denne benytter Cloudflare-navneserverne.
  
Hvis du selv vil ændre domænets navneservere på domæneregistratorens websted, skal du følge disse trin.
  
1. Find det område på domæneregistratorens websted, hvor du kan redigere navneserverne for dit domæne.

2. Opret enten to navneserverposter ved hjælp af værdierne i følgende tabel, eller rediger de eksisterende navneserverposter, så de matcher disse værdier.

    ||
    |:-----|:-----|
    |Første navneserver  <br/> |Brug den navneserverværdi, der leveres af Cloudflare.  <br/> |
    |Anden navneserver  <br/> |Brug den navneserverværdi, der leveres af Cloudflare.  <br/> |

    > [!TIP]
    > Du skal bruge mindst to navneserverposter. Hvis der er angivet andre navneservere, bør du slette dem. 
  
3. Gem ændringerne.

> [!NOTE]
> Det kan tage adskillige timer, før opdateringerne af navneserverposten registreres i internettets DNS-system. Derefter vil din Microsoft-mail og andre tjenester være klar til at fungere med dit domæne. 
  
### <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil. 
  
1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.
  
1. På startsiden skal du vælge det domæne, du vil opdatere. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. På siden Overview for dit domæne skal du vælge **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::
  
1. På SIDEN DNS-administration skal du vælge **+Add record**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg TXT-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel. 

    | **Type** | **Navn** | **TTL** | **Indhold** |
    |:-----|:-----|:-----|:----|
    |TXT  <br/> |@  <br/> |30 minutter  <br/> |MS=ms *XXXXXXXX*  <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)    |

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Vælg Tilføj post.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og søge efter posten. Når Microsoft finder den rette TXT-post, bekræftes dit domæne.
  
Sådan bekræftes posten i Microsoft 365:
  
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du er ved at bekræfte, og vælge **Start installationen**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.
  
1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.
  
1. På startsiden skal du vælge det domæne, du vil opdatere. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. På siden Overview for dit domæne skal du vælge **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På SIDEN DNS-administration skal du vælge **+Add record**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg MX-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel. 

   | **Type** | **Navn** | **Mailserver** |  **TTL** | **Prioritet** |
   |:-----|:-----|:-----|:-----|:-----|
   |MX  <br/> |@  <br/> |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **Bemærk!** Få din *\<domain-key\>* fra din Microsoft 365 konto.   [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md) |30 minutter  <br/> | 1  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/>|

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-save.png" alt-text="Vælg Tilføj post."::: 

1. Hvis der er angivet andre MX-poster i **sektionen MX Records** , skal du slette dem ved at vælge **Rediger** og derefter vælge **Delete**. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-mx-delete.png" alt-text="Vælg Slet.":::  

1. Vælg Slet i bekræftelsesdialogboksen **for** at bekræfte dine ændringer. 

### <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.

1. På startsiden skal du vælge det domæne, du vil opdatere. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. På siden Overview for dit domæne skal du vælge **DNS**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På **DNS-administrationssiden** skal du vælge **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg CNAME-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel. 

    | Type | Navn | Destination | TTL |
    |:-----|:-----|:-----|:-----|
    | CNAME  <br/> | autodiscover  <br/> | autodiscover.outlook.com  <br/> | Automatisk <br/> |
  
1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Vælg Gem."::: 

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny for Microsoft 365. I stedet skal du føje de Microsoft 365 værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge sæt af værdier. 
  
1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.  
  
1. På startsiden skal du vælge det domæne, du vil opdatere. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. På siden Overview for dit domæne skal du vælge **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På SIDEN DNS-administration skal du vælge **+Add record**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg TXT-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel. 

    | Type | Navn | TTL | Indhold |
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |30 minutter  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.   |

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-TXT-save.png" alt-text="Vælg Gem."::: 

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

> [!IMPORTANT]
> Husk på, at Cloudflare er ansvarlig for at gøre denne funktionalitet tilgængelig. Hvis du ser uoverensstemmelser mellem nedenstående trin og den aktuelle Cloudflare GUI (Grafisk brugergrænseflade), kan du udnytte [Cloudflare Community](https://community.cloudflare.com/). 

1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.

1. På startsiden skal du vælge det domæne, du vil opdatere. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::
  
1. På siden Overview for dit domæne skal du vælge **DNS**.
  
    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På DNS-administrationssiden skal du vælge **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg SRV-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    | **Type** | **Navn** | **Tjeneste** | **Protokol** |  **TTL** | **Prioritet** | **Vægt** | **Port** | **Destination** |
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV| Brug din *domain_name*; for eksempel contoso.com | _sip |TLS |30 minutter | 100|1 |443 |sipfed.online.lync.com  |
    |SRV|_sipfederationtls | TCP|Brug din *domain_name*; for eksempel contoso.com   |30 minutter |100 |1 |5061 | sipfed.online.lync.com |
  
1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-srv-save.png" alt-text="Vælg Gem."::: 

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen. 

> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster
  
1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.

1. På startsiden skal du vælge det domæne, du vil opdatere. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. På siden Overview for dit domæne skal du vælge **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På DNS-administrationssiden skal du vælge **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg CNAME-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |**Type**|**Navn**|**Destination**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
  
1. Vælg **Fanen Gem**. 

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Vælg Gem.":::  

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på Cloudflare ved hjælp [af dette link](https://www.cloudflare.com/a/login). Du vil blive bedt om at logge på først.

1. På startsiden skal du vælge det domæne, du vil opdatere. 

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-1.png" alt-text="Vælg det domæne, du vil opdatere.":::

1. På siden Overview for dit domæne skal du vælge **DNS**.

    :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-2.png" alt-text="Vælg DNS.":::

1. På DNS-administrationssiden skal du vælge **+Add record**

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-add-record.png" alt-text="Vælg Tilføj post.":::

1. Vælg CNAME-typen på rullelisten, og skriv eller kopiér og indsæt værdierne fra denne tabel.

    |**Type**|**Navn**|**Destination**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
  
1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-cloudflare/cloudflare-domains-cname-save.png" alt-text="Vælg Gem."::: 

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).