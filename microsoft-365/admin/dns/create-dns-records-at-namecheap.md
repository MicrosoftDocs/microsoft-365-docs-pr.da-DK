---
title: Forbind DNS-posterne på Namecheap for at Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på Namecheap til Microsoft.
ms.openlocfilehash: 146b76ef95a725faa3457eaf1795b153133cef92
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588062"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>Forbind DNS-posterne på Namecheap for at Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
Hvis Namecheap er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.
  
Når du har tilføjet disse poster på Namecheap, konfigureres dit domæne til at fungere med Microsoft-tjenester.
  
> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil. 
  
1. For at komme i gang skal du gå til siden med dine domæner på Namecheap ved hjælp [af dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. På landingssiden skal **du** under **Account vælge Domain List** på rullelisten. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste på rullelisten.":::

1. På siden Domain List skal du vælge det domæne, du vil redigere, og derefter vælge **Administrer**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I sektionen **HOST RECORDS** skal du vælge **ADD NEW RECORD**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. I **rullemenuen Type** skal du vælge **TXT Record**.
    
    > [!NOTE]
    > **Rullemenuen Type** vises automatisk, når du vælger **TILFØJ NY POST**. 

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="Vælg TXT-post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.
    
    Vælg **værdien TTL** på rullelisten. 
    
    |**Type**|**Vært**|**Værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/>**Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md) |30 min.  <br/> |

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer (markering). 

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.
    
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
  
1. For at komme i gang skal du gå til siden med dine domæner på Namecheap ved hjælp [af dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. På landingssiden skal **du** under **Account vælge Domain List** på rullelisten. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domain List på rullelisten.":::

1. På siden **Domain List** skal du vælge det domæne, du vil redigere, og derefter vælge **Manage**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I sektionen **MAIL SETTINGS** skal du **vælge Custom MX** **på rullelisten Email Forwarding** . 
    
    (Du skal muligvis rulle ned).

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="Vælg Custom MX."::: 

1. Vælg **Tilføj ny post**.

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="TILFØJ NY POST.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.
    
    Feltet **Prioritet** er det unavngivne felt til højre for **feltet** Værdi. Vælg **værdien TTL** på rullelisten. 
    
    |**Type**|**Vært**|**Værdi**|**Prioritet**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX-post  <br/> |@  <br/> |\<*domain-key*\>.mail.protection.outlook.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> **Bemærk!** Få din fra  *\<domain-key\>*  din Microsoft-konto.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/> |30 min.  <br/> |

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer (markering). 

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Hvis der er andre MX-poster, skal du bruge følgende proces i to trin til at fjerne hver af dem:
    
    Først skal du **vælge Slet** (papirkurven) for den post, du vil fjerne. 

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="Vælg Slet.":::

    Vælg derefter Ja **for** at bekræfte sletningen. 

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="Vælg Ja.":::

    Fjern alle MX-poster med undtagelse af den, du tilføjede tidligere i denne procedure.
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på Namecheap ved hjælp [af dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. På landingssiden skal **du** under **Account vælge Domain List** på rullelisten. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domain List** skal du vælge det domæne, du vil redigere, og derefter vælge **Manage**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I sektionen **HOST RECORDS** skal du vælge **ADD NEW RECORD**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. I **rullemenuen Type** skal du vælge **CNAME Record**.
    
    > [!NOTE]
    > **Rullemenuen Type** vises automatisk, når du vælger **TILFØJ NY POST**. 

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Vælg CNAME-post.":::

1. I de tomme felter for den nye post skal du vælge **CNAME** som **Record Type** og derefter skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.
    
    |**Type**|**Vært**|**Værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer (markering). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en *enkelt*  SPF-post, der indeholder begge sæt af værdier. 

1. For at komme i gang skal du gå til siden med dine domæner på Namecheap ved hjælp [af dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på og fortsætte.
    
1. På landingssiden skal **du** under **Account vælge Domain List** på rullelisten. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domain List** skal du vælge det domæne, du vil redigere, og derefter vælge **Manage**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I sektionen **HOST RECORDS** skal du vælge **ADD NEW RECORD**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. I **rullemenuen Type** skal du vælge **TXT Record**.
    
    > [!NOTE]
    > **Rullemenuen Type** vises automatisk, når du vælger **TILFØJ NY POST**. 

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="Vælg TXT-post.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier fra følgende tabel.
    
    Vælg **værdien TTL** på rullelisten. 
    
    |**Type**|**Vært**|**Værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte. |30 min.  <br/> |

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer (markering). 

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner på Namecheap ved hjælp [af dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. På landingssiden skal **du** under **Account vælge Domain List** på rullelisten. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domain List.":::

1. På siden **Domain List** skal du vælge det domæne, du vil redigere, og derefter vælge **Manage**.

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Avanceret DNS.":::

1. I sektionen **HOST RECORDS** skal du vælge **ADD NEW RECORD**.

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. I **rullemenuen Type** skal du vælge **SRV Record**.
    
    > [!NOTE]
    > **Rullemenuen Type** vises automatisk, når du vælger **TILFØJ NY POST**. 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Vælg typen SRV-post.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i nedenstående tabel.
    
    |**Tjeneste**|**Protokol**|**Prioritet**|**Vægt**|**Port**|**Destination**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |
       
     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer (markering). 

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Tilføj den anden SRV-post ved at vælge værdierne fra den anden række i tabellen.
    
> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster 
  
1. I sektionen **HOST RECORDS** skal du vælge **ADD NEW RECORD**.
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NYT NAVN.":::

1. I **rullemenuen Type** skal du vælge **CNAME**.
    
    > [!NOTE]
    > **Rullemenuen Type** vises automatisk, når du vælger **TILFØJ NY POST**. 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Vælg CNAME.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i tabellen.
    
    |**Type**|**Vært**|**Værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Kopiér og indsæt CNAME-værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer (markering). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Tilføj den anden CNAME-post ved at vælge værdierne fra anden række i tabellen.
    
> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på Namecheap ved hjælp [af dette link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). Du bliver bedt om at logge på.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Log på Namecheap.":::

1. På landingssiden skal **du** under **Account vælge Domain List** på rullelisten. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Vælg Domæneliste.":::

1. På siden **Domain List** skal du vælge det domæne, du vil redigere, og derefter vælge **Manage**.
    
     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Vælg Administrer.":::

1. Vælg **Avanceret DNS**.

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Vælg Manage DNS Records på rullelisten.":::

1. I sektionen **HOST RECORDS** skal du vælge **ADD NEW RECORD**.
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Vælg TILFØJ NY POST.":::

1. I **rullemenuen Type** skal du vælge **CNAME Record**.
    
    > [!NOTE]
    > **Rullemenuen Type** vises automatisk, når du vælger **TILFØJ NY POST**. 
  
     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Vælg CNAME-post.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i tabellen.
    
    |**Type**|**Vært**|**Værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |Automatisk  <br/> |
       
     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Kopiér og indsæt værdierne fra tabellen.":::

1. Vælg **kontrolelementet Gem** ændringer. 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Vælg kontrolelementet Gem ændringer.":::

1. Tilføj den anden CNAME-post ved at vælge værdierne fra anden række i tabellen.
    
> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 


