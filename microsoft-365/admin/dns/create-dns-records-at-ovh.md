---
title: Forbind DINE DNS-poster på OVH til Microsoft 365
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
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på OVH til Microsoft.
ms.openlocfilehash: 9c181536c418baebd3ba8eb1929095ac2d828ef6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590766"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Forbind DINE DNS-poster på OVH til Microsoft 365

[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml) domæner, hvis du ikke kan finde det, du leder efter.
  
Hvis OVH er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på OVH, konfigureres dit domæne til at fungere med Microsoft-tjenester.

> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil. 
  
1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Vælg **TXT**

    ![OVH Vælg TXT-post.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)
  
1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 

    |**Posttype**|**Underdomæne**|**TTL**|**Værdi**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(lad feltet være tomt)  <br/> |3600 (sekunder)  <br/> |MS=msxxxxxxxx  <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          |

1. Vælg **Næste**.

1. Vælg **Bekræft**.

    ![OVH bekræft TXT til godkendelse.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)
  
1. Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den rette TXT-post, bekræftes dit domæne.

Sådan bekræftes posten i Microsoft 365:
  
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du er ved at bekræfte, og vælge **Start installationen**. 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.
  
1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Vælg **MX**.

    ![OVH MX-posttype.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)
  
1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 

    > [!NOTE]
    > Som standard bruger OVH relativ notation for destinationen, hvilket tilføjer domænenavnet i slutningen af destinationsposten. Hvis du i stedet vil bruge absolut notation, skal du føje et prik til destinationsposten som vist i tabellen nedenfor. 
  
    |**Underdomæne**|**TTL**|**Prioritet**|**Destination**|
    |:-----|:-----|:-----|:-----|
    |(lad feltet være tomt)  <br/> |3600 (sekunder)  <br/> |0  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/> |\<domain-key\>.mail.protection.outlook.com.  <br/> **Bemærk!** Få din fra  *\<domain-key\>*  din Microsoft-konto.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)  |

    ![OVH MX-post til mail.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)
  
1. Vælg **Næste**.

    ![OVH MX-post, vælg Næste.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)
  
1. Vælg **Bekræft**.

    ![OVH MX-post, vælg Bekræft.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. Slet eventuelle andre MX-poster på listen på **siden DNS-zone** . Markér hver post, og vælg **ikonet** Slet for Papirkurv i **kolonnen** Handlinger.

    ![OVH slet MX-post.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)
  
1. Vælg **Bekræft**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Vælg **CNAME**.

    ![OVH Tilføj CNAME-posttype.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 

    |**Underdomæne**|**TTL**|**Destination**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |3600 (sekunder)  <br/> |autodiscover.outlook.com.  <br/> |

    ![OVH CNAME-post.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)
  
1. Vælg **Næste**.

    ![OVH Tilføj CNAME-værdier, og vælg Næste.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Vælg **Bekræft**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier. 
  
1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Vælg **TXT**.

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 

    |**Underdomæne**|**TTL**|**Værdi**|
    |:-----|:-----|:-----|
    |(lad feltet være tomt)  <br/> |3600 (sekunder)  <br/> |v=spf1 include:spf.protection.outlook.com -all <br/**Note:** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.           |

    ![OVH Tilføj TXT-post til SPF.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)
  
1. Vælg **Næste**.

    ![OVH Tilføj TXT-post til SPF, og vælg Næste.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)
  
1. Vælg **Bekræft**.

    ![OVH Tilføj TXT-post for SPF, og bekræft.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)
  
## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **SRV**.

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 

    |**Underdomæne**|**TTL (sekunder)**| **Prioritet** | **Vægt** | **Port**|**Destination**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|3600 (s.) |100 |  1  | 443 |sipdir.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**><br> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte. | 
    |_sipfederationtls._tcp| 3600 (s.)|100 | 1 | 5061 | sipfed.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**<br> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.    | 
  
1. Hvis du vil tilføje den anden SRV-post, skal du vælge Tilføj en anden **post, oprette** en post med værdierne fra den næste række i tabellen og derefter vælge **Opret poster**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster 

1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **CNAME**.

    ![OVH Tilføj CNAME-posttype.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 

    |**Underdomæne**| **TTL** | **Destination** | 
    |:-----|:-----|:-----|
    |sip  <br/> | 3600 (s.)  <br/> |sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |
    |lyncdiscover  <br/> |3600 (s.) |webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/>  |
  
1. Vælg **Næste**.

    ![OVH Tilføj CNAME-værdier, og vælg Næste.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Vælg **Bekræft**.

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du vil blive bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Vælg navnet på det domæne, du **vil redigere**, under Vis alle mine aktiviteter på dashboardets landingsside.
  
1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Vælg **CNAME**.

    ![OVH Tilføj CNAME-posttype.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel. Hvis du vil tildele en TTL-værdi **,** skal du vælge Brugerdefineret på rullelisten og derefter skrive værdien i tekstfeltet. 
  
    |**Underdomæne**| **TTL** | **Destination** | 
    |:-----|:-----|:-----|
    |enterpriseregistration  <br/>| 3600 (s.)  <br/> |enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/> |
    |enterpriseenrollment  <br/>  |3600 (s.) |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)** <br/>|

1. Vælg **Næste**.

    ![OVH Tilføj CNAME-værdier, og vælg Næste.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Vælg **Bekræft**.

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).