---
title: Forbind DINE DNS-poster hos GoDaddy til Microsoft 365
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f40a9185-b6d5-4a80-bb31-aa3bb0cab48a
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på GoDaddy til Microsoft.
ms.openlocfilehash: 728fd6cc34517213b338e3da07e6a275a1a727d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587439"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Forbind DINE DNS-poster hos GoDaddy til Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

Hvis GoDaddy er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

## <a name="before-you-begin"></a>Før du begynder

Du har to muligheder for at konfigurere DNS-poster for dit domæne:

- [**Brug domæne Forbind**](#use-domain-connect-to-verify-and-set-up-your-domain) Hvis du ikke har konfigureret dit domæne med en anden mail serviceudbyder, skal du bruge trinnene til Domain Forbind til automatisk at bekræfte og konfigurere dit nye domæne til brug med Microsoft 365.

   ELLER

- [**Brug de manuelle trin**](#create-dns-records-with-manual-setup) Bekræft dit domæne ved hjælp af de manuelle trin nedenfor, og vælg, hvornår og hvilke poster du vil føje til din domæneregistrator. Dette giver dig mulighed for at konfigurere nye MX-poster (mail), f.eks. når det passer dig.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Brug domæneadministrator Forbind at bekræfte og konfigurere dit domæne

Følg disse trin for automatisk at bekræfte og konfigurere dit GoDaddy-domæne med Microsoft 365:

1. I dialogboksen Microsoft 365 Administration du **vælge Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> og vælge det domæne, du vil konfigurere.

1. Vælg de tre > vælg **Start installationen**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. På siden Hvordan vil du forbinde dit domæne? skal du vælge **Fortsæt**.

1. På siden Tilføj DNS-poster skal du vælge **Tilføj DNS-poster**.

1. På GoDaddy-logonsiden skal du logge på din konto og vælge **Godkend**.

    Dette fuldfører domænekonfigurationen for Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Oprette DNS-poster med manuel konfiguration

Når du har tilføjet disse poster hos GoDaddy, konfigureres dit domæne til at fungere med Microsoft-tjenester.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil.

1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Poster** skal du **vælge TILFØJ** (du skal muligvis rulle ned).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **TXT** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg TXT på rullelisten Type.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra tabellen.

   |**Type** |**Vært**|**TXT-værdi**|**TTL** |
   |:-----|:-----|:-----|:-----|
   |TXT |@|MS=ms *XXXXXXXX*<br>**Bemærk**! Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)|1 time  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Udfyld værdierne fra tabellen for TXT-posten.":::

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Vælg Gem.":::

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

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

3. Under **Poster skal** du vælge **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

4. Vælg **MX** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg MX på rullelisten Type.":::

5. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne** **for Type og TTL** på rullelisten).

    |**Type**|**Vært**|**Peger på**|**Prioritet**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX  <br/> |@  <br/> | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Bemærk!** Få din fra  *\<domain-key\>*  din Microsoft-konto.           [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/> |1 time  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Udfyld værdierne fra tabellen for MX-posten.":::

6. Vælg **Gem**.

### <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

3. Under **Poster skal** du vælge **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

4. Vælg **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg CNAME på rullelisten Type.":::

5. Opret CNAME-posten.

    I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

    Vælg **værdien TTL** på rullelisten.

    |**Type**|**Vært**|**Peger på**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover <br/> |autodiscover.outlook.com  <br/> |1 time  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Udfyld værdierne fra tabellen for CNAME-posten.":::

6. Vælg **Gem**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier.

1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

3. Under **Poster skal** du vælge **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

4. Vælg **TXT** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg TXT på rullelisten Type.":::

5. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier.

    Vælg **værdien TTL** på rullelisterne.

    |**Type**|**Vært**|**TXT-værdi**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte. |1 time  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Udfyld værdierne fra tabellen for TXT-posten.":::

6. Vælg **Gem**.

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Poster skal** du vælge **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **SRV** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg SRV på rullelisten Type.":::

1. Opret den første SRV-post.

    I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

    (Vælg **værdierne for Type** **og TTL** på rullelisterne).

    |**Type**|**Tjeneste**|**Protokol**| **Navn** | **Destination**|**Prioritet**|**Vægt**|**Port**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV   <br/> |_sip  <br/> |_tls  <br/> |@  <br/> |sipdir.online.lync.com  <br/> |100 <br/> | 1  <br/> |443  <br/> |1 time  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |_tcp  <br/> |@  <br/> | sipfed.online.lync.com  <br/> | 100  <br/> |1  <br/> |5061  <br/> |1 time  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="Udfyld værdierne fra tabellen for SRV-posten.":::

1. Vælg **Gem**.

1. Tilføj den anden SRV-post ved at vælge værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster
  
1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Poster skal** du vælge **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i nedenstående tabel.

    |**Type**|**Vært**|**Peger på**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Udfyld værdierne fra tabellen for CNAME-posten.":::
  
1. Vælg **Gem**.
  
1. Tilføj den anden CNAME-post ved at vælge værdierne fra anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på GoDaddy ved hjælp [af dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine logonoplysninger, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner skal** du vælge de tre prik ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg DNS-styring på rullelisten.":::

1. Under **Poster skal** du vælge **ADD**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i nedenstående tabel.

    |**Type**|**Vært**|**Peger på**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |1 time  <br/> |

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Udfyld værdierne fra tabellen for CNAME-posten.":::
  
1. Vælg **Gem**.
  
1. Tilføj den anden CNAME-post ved at vælge værdierne fra anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
