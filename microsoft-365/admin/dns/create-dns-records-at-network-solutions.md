---
title: Forbind DINE DNS-poster hos Network Solutions for at Microsoft 365
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
ms.assetid: 1dc55f9f-5309-450f-acc3-b2b4119c8be3
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på Network Solutions til Microsoft.
ms.openlocfilehash: a15b6ec2f06b08a32c0cf03bbc030731b91ea925
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599748"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>Forbind DINE DNS-poster hos Network Solutions for at Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
Hvis Network Solutions er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på Network Solutions, konfigureres dit domæne til at fungere med Microsoft-tjenester.
  
> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil. 
  
1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::
  
1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
1. På siden Manage Advanced DNS Records skal du vælge **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::

1. Under **Type** skal **du vælge TXT** på rullelisten.
  
1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne i følgende tabel.
    
    | Refererer til | TXT-værdi | TTL |
    |:-----|:-----|:-----|
    |@  <br/> Systemet ændrer denne værdi til **@ (Ingen),** når du gemmer posten.  |MS=ms *XXXXXXXX*  <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md) |3600  <br/>    | 

1. Vælg **TILFØJ**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="Vælg TILFØJ.":::

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den TXT-post, du har oprettet.   
  
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
  
1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::
  
1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::

1. Under **Type** skal **du vælge MX** på rullelisten.
  


1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.
    
    | Refererer til | Mailserver | Prioritet | TTL |
    |:-----|:-----|:-----|:-----|
    | @ | *\<domain-key\>*  .mail.protection.outlook.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> **Bemærk!** Få din fra  *\<domain-key\>*  din Microsoft-konto. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md) | 0  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) | 1 time  |  
  
1. Vælg **TILFØJ**.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-MX-add.png" alt-text="Vælg TILFØJ.":::

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den TXT-post, du har oprettet.  

1. Hvis der er andre MX-poster, skal du slette dem alle ved at vælge redigeringsværktøjet og derefter **Slette** for hver post.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-edit.png" alt-text="Vælg værktøjet Rediger.":::
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::
  
1. Vælg **Advanced Tools**, og ud for **Advanced DNS Records skal** du vælge **MANAGE**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::

1. Under **Type** skal **du vælge CNAME** fra rullelisten.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Vælg CNAME-type på rullelisten.":::
 
1. I felterne for CNAME-posten skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.
    
    | Refererer til | Host Name | Alias til | TTL |
    |:-----|:-----|:-----|:-----|
    |Anden vært| autodiscover  | autodiscover.outlook.com **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> 1 time  |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::
  
1. Vælg **TILFØJ**.

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den post, du har oprettet.  
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier. 
  
1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Advanced Tools**, og ud for **Advanced DNS Records skal** du vælge **MANAGE**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::

1. Under **Type** skal **du vælge TXT** på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-TXT.png" alt-text="Vælg TXT på rullelisten Type.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier.
    
    | Refererer til | TXT-værdi | TTL
    |:-----|:-----|:-----|
    |@  <br/> Systemet ændrer denne værdi til **@ (Ingen),** når du gemmer posten.  |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte. | 1 time  |
       
1. Vælg **TILFØJ**.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="Vælg TILFØJ.":::

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den post, du har oprettet.  
  
## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.
  
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Advanced Tools**, og ud for **Advanced DNS Records skal** du vælge **MANAGE**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::

1. Under **Type** skal **du vælge SRV** på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv.png" alt-text="Vælg SRV på rullelisten Type.":::

1. I felterne for de to nye poster skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    (Vælg **værdierne Service** **og Protocol** på rullelisterne). 
    
    | Type | Tjeneste | Protokol | Vægt | Port | Destination | Prioritet | TTL |
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    | SRV |_sip  |TLS  |100  |443  |sipdir.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** | 1  | 1 time  |
    | SRV |_sipfederationtls  |TCP  |100  |5061  |sipfed.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** |1  | 1 time  |
  
1. Vælg **TILFØJ**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv-add.png" alt-text="Vælg TILFØJ.":::

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den post, du har oprettet.  

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Advanced Tools**, og ud for **Advanced DNS Records skal** du vælge **MANAGE**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::

1. Under **Type** skal **du vælge CNAME** fra rullelisten.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Vælg CNAME-type på rullelisten.":::
 
1. I felterne for CNAME-posten skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    | Type | Refererer til | Host Name | Alias til | TTL |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Anden vært | sip  <br/> |sipdir.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** |1 time |
    | CNAME| Anden vært | lyncdiscover  <br/> |webdir.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** | 1 time |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den post, du har oprettet.  

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner på Network Solutions ved hjælp [af dette link](https://www.networksolutions.com/manage-it). Du vil blive bedt om at logge på.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Advanced Tools**, og ud for **Advanced DNS Records skal** du vælge **MANAGE**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ADD RECORD**.

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +ADD RECORD.":::
  
1. Under **Type** skal **du vælge CNAME** fra rullelisten.
 
    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Vælg CNAME-type på rullelisten.":::
 
1. I felterne for CNAME-posten skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

    | Type | Refererer til | Host Name | Alias til | TTL |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Anden vært | enterpriseregistration |enterpriseregistration.windows.net  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** | 1 time |
    | CNAME | Anden vært |enterpriseenrollment |enterpriseenrollment-s.manage.microsoft.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** | 1 time |

    :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.

    > [!NOTE]
    > Vælg **Klassisk visning øverst** til højre for at få vist den post, du har oprettet.  

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

