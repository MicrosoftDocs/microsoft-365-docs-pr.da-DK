---
title: Forbind dine DNS-poster på IONOS med 1&1 Microsoft 365
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
ms.assetid: 5762c3ca-1de2-4999-bfe5-4c5e25a8957e
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på 1&1 IONOS til Microsoft.
ms.openlocfilehash: 54e18972fe2d5e2ccd8c3ab266b20241e67f68a9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590108"
---
# <a name="connect-your-dns-records-at-ionos-by-11-to-microsoft-365"></a>Forbind dine DNS-poster på IONOS med 1&1 Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 

Hvis IONOS by 1&1 er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

## <a name="before-you-begin"></a>Før du begynder

Du har to muligheder for at konfigurere DNS-poster for dit domæne:

- [**Brug domæne Forbind**](#use-domain-connect-to-verify-and-set-up-your-domain) Hvis du ikke har konfigureret dit domæne med en anden mail serviceudbyder, skal du bruge trinnene til Domain Forbind til automatisk at bekræfte og konfigurere dit nye domæne til brug med Microsoft 365. 

    ELLER

- [**Brug de manuelle trin**](#create-dns-records-with-manual-setup) Bekræft dit domæne ved hjælp af de manuelle trin nedenfor, og vælg, hvornår og hvilke poster du vil føje til din domæneregistrator. Dette giver dig mulighed for at konfigurere nye MX-poster (mail), f.eks. når det passer dig. 

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Brug domæneadministrator Forbind at bekræfte og konfigurere dit domæne

Følg disse trin for automatisk at bekræfte og konfigurere dit IONOS med 1&1 domæne med Microsoft 365:

1. I dialogboksen Microsoft 365 Administration du **vælge Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> og vælge det domæne, du vil konfigurere.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-1.png" alt-text="Vælg dit domæne i Microsoft 365.":::

1. Vælg de tre > vælg **Start installationen**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. På siden Hvordan vil du forbinde dit domæne? skal du vælge **Fortsæt**.   

1. På siden Tilføj DNS-poster skal du vælge **Tilføj DNS-poster**.

1. På logonsiden IONOS by 1&1 skal du logge på din konto og **vælge Forbind** og **Tillad**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-3.png" alt-text="Vælg Forbind og derefter Tillad.":::

    Dette fuldfører domænekonfigurationen for Microsoft 365. 

## <a name="create-dns-records-with-manual-setup"></a>Oprette DNS-poster med manuel konfiguration

Når du har tilføjet disse poster på IONOS 1&1, konfigureres dit domæne til at fungere med Microsoft-tjenester.
  
> [!CAUTION]
> Bemærk, at IONOS by 1&1 ikke tillader, at et domæne både har en MX-post og en Autodiscover CNAME-post på øverste niveau. Dette begrænser den måde, hvorpå du kan konfigurere Exchange Online til Microsoft. Der findes en løsning, men vi anbefaler kun at anvende  den, hvis du allerede har erfaring med at oprette underdomæner på IONOS med 1&1.
> Hvis du trods [](../setup/domains-faq.yml) tjenestebegrænsningerne vælger at administrere dine egne Microsoft DNS-poster på IONOS med 1&1, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere dine DNS-poster til mail, Skype for Business Online osv.
  
> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil.
  
1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **TXT-sektionen** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-4.png" alt-text="Vælg TXT-sektionen.":::

1. På siden Add a DNS record skal du i felterne for den nye post skrive eller kopiere og indsætte værdierne fra den nedenstående tabel.

    |**Værtsnavn** <br/> |**Værdi** <br/> | **TTL**
    |:-----|:-----|:-----|
    |Lad dette felt være tomt  <br/> |MS=ms *XXXXXXXX*  <br/> BEMÆRK! Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          | 1 time |

1. Vælg **Gem**.
  
    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-5.png" alt-text="Vælg Gem.":::
  
    Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan blive opdateret på internettet.

Nu hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft 365 og anmode Microsoft 365 at finde posten. Når Microsoft finder den rette TXT-post, bekræftes dit domæne.

Sådan bekræftes posten i Microsoft 365:
  
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du er ved at bekræfte, og vælge **Start installationen**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.
  
1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
  
### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft
  
> [!NOTE]
> Hvis du er registreret hos en 1und1.de, skal [du logge på her](https://go.microsoft.com/fwlink/?linkid=859152). 

1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **sektionen MX** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX.png" alt-text="Vælg sektionen MX.":::
  
1. På siden Add a DNS record skal du i felterne for den nye post skrive eller kopiere og indsætte værdierne fra den nedenstående tabel.

    | **Værtsnavn**| **Peger på** |**Prioritet**| **TTL** |
    |:-----|:-----|:-----| :-----|
    |  @  | *\<domain-key\>*  .mail.protection.outlook.com  <br/>  BEMÆRK! Få din fra \<domain-key\> din Microsoft-konto. [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)          |10  <br/> Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) | 1 time |
  
1. Vælg **Gem**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-MX-Save.png" alt-text="Vælg Gem.":::

1. Hvis der allerede er angivet MX-poster, skal du slette hver af dem ved at vælge Papirkurv til **Delete-post** på **siden Tilføj** post.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Delete.png" alt-text="Vælg Slet post.":::

### <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

> [!NOTE]
> Hvis du er registreret hos en 1und1.de, skal [du logge på her](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

    Nu skal du oprette to underdomæner og angive en **Alias-værdi** for hver.<br/>(Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster).<br/>Først skal du oprette Autodiscover-underdomænet.

1. Vælg **Underdomæner**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Vælg Underdomæne.":::
  
1. Vælg **Tilføj underdomæne**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Vælg Tilføj underdomæner.":::
  
1. I feltet **Add subdomain** for det nye underdomæne skal du kun skrive eller kopiere og indsætte **Add subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere.

    |**Tilføj underdomæne**| **Alias** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |

1. Under **Actions** for **the autodiscover subdomain** that you just created, select the gear control, and then select **DNS** from the drop-down list. <br/>

1. Vælg **Tilføj post**, og vælg derefter **sektionen CNAME** .

1. I feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel. <br/>

    |**Tilføj underdomæne**| **Alias** |
    |:-----|:-----|
    |autodiscover  <br/> | autodiscover.outlook.com |
  
1. Vælg **Gem**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier. Har du brug for eksempler? Se disse [eksterne DNS-poster for Microsoft](../../enterprise/external-domain-name-system-records.md). Hvis du vil validere din SPF-post, kan du bruge et af disse [SPF-valideringsværktøjer](../setup/domains-faq.yml). 
  
> [!NOTE]
> Hvis du er registreret hos en 1und1.de, skal [du logge på her](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **sektionen SPF (TXT** ).

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT.png" alt-text="Vælg sektionen SPF (TXT).":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel. <br/>

    |**Type**|**Værtsnavn**|**Værdi**| **TTL** |
    |:-----|:-----|:-----|:-----|
    |SPF (TXT)  <br/> |Lad dette felt være tomt.  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte. | 1 time |
  
1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SPFTXT-Save.png" alt-text="Vælg Gem.":::

## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-two-additional-cname-records"></a>Tilføj to ekstra CNAME-poster
  
1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

    Nu skal du oprette to underdomæner og angive en **Alias-værdi** for hver.<br/>(Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster).<br/>Først skal du oprette lyncdiscover-underdomænet.

1. Vælg **Underdomæner**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Vælg Underdomæne.":::
  
1. Vælg **Tilføj underdomæne**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Vælg Tilføj underdomæner.":::

1. I feltet **Add subdomain** for det nye underdomæne skal du kun skrive eller kopiere og indsætte **Add subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere.<br/> 

    |**Tilføj underdomæne**|**Alias**|
    |:-----|:-----|
    |lyncdiscover   |webdir.online.lync.com  |

1. Under **Handlinger** for **det lyncdiscover-underdomæne** , du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten. <br/>

1. Vælg **Tilføj post**, og vælg derefter **sektionen CNAME** .

1. I feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel. <br/>

    |**Opret underdomæne**|**Alias**|
    |:-----|:-----|
    |lyncdiscover  <br/> |webdir.online.lync.com  <br/> |

1. Opret et andet underdomæne (SIP): <br/>Vælg **Tilføj underdomæne**.

1. I feltet **Add subdomain** for det nye underdomæne skal du kun skrive eller kopiere og indsætte **Add subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere. <br/>

    |**Tilføj underdomæne**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. Under **Handlinger** for det underdomæne, du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten. <br/>

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **sektionen CNAME** .

1. i feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel. 

    |**Opret underdomæne**|**Alias**|
    |:-----|:-----|
    |sip  <br/> |sipdir.online.lync.com  <br/> |

1. Markér afkrydsningsfeltet for **ansvarsfraskrivelsen I am aware** , og vælg derefter **Gem**.

## <a name="add-the-two-srv-records-required-for-microsoft"></a>Tilføj de to SRV-poster, der kræves til Microsoft
  
> [!NOTE]
> Hvis du er registreret hos en 1und1.de, skal [du logge på her](https://go.microsoft.com/fwlink/?linkid=859152). 
  
1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **sektionen SRV** .

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV.png" alt-text="Vælg sektionen SRV.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel. <br/>

    |**Type**|**Tjeneste**|**Protokol**|**Værtsnavn**|**Peger på**|**Prioritet**|**Vægt**|**Port**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |SRV  <br/> |_sip  <br/> |tls  <br/> |Lad dette felt være tomt.  <br/> |sipdir.online.lync.com  <br/> |100  <br/> |1  <br/> |443  <br/> |1 time  <br/> |
    |SRV  <br/> |_sipfederationtls  <br/> |tcp  <br/> |Lad dette felt være tomt.  <br/> |sipfed.online.lync.com  <br/> |100  <br/> |1  <br/> |5061  <br/> |1 time <br/> |  
  
1. Vælg **Gem**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-SRV-Save.png" alt-text="Vælg Gem.":::

1. Tilføj den anden SRV-post.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

> [!IMPORTANT]
> Følg den underdomæneprocedure, du anvendte til de andre CNAME-poster, og brug værdierne fra følgende tabel. 
  
1. For at komme i gang skal du gå til siden med dine domæner på IONOS med 1&1 ved hjælp af [dette link](https://my.1and1.com/). Du vil blive bedt om at logge på.

1. Vælg **Menu**, og vælg **derefter Domæner og SSL**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-1.png" alt-text="Vælg Domæner og SSL.":::
  
1. Under **Handlinger** for det domæne, du vil opdatere, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-2.png" alt-text="Vælg DNS på rullelisten.":::

    Nu skal du oprette to underdomæner og angive en **Alias-værdi** for hver.<br/>(Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster).<br/>Først skal du oprette lyncdiscover-underdomænet.

1. Vælg **Underdomæner**.
  
   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-Subdomains.png" alt-text="Vælg Underdomæne.":::
  
1. Vælg **Tilføj underdomæne**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-domains-add-subdomains.png" alt-text="Vælg Tilføj underdomæner.":::

1. I feltet **Add subdomain** for det nye underdomæne skal du kun skrive eller kopiere og indsætte **Add subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere.<br/> 

    |**Tilføj underdomæne**|**Alias**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. Under **Handlinger** for **underdomænet enterpriseregistration** , som du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten. <br/>

1. Vælg **Tilføj post**, og vælg derefter **sektionen CNAME** .

1. I feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel. <br/>

    |**Tilføj underdomæne**|**Alias**|
    |:-----|:-----|
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> |

1. Opret et andet underdomæne: <br/>Vælg **Tilføj underdomæne**.

1. I feltet **Add subdomain** for det nye underdomæne skal du kun skrive eller kopiere og indsætte **Add subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere. <br/>

    |**Tilføj underdomæne**|**Alias**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. Under **Handlinger** for **underdomænet enterpriseenrollment** , som du lige har oprettet, skal du vælge tandhjulskontrolelementet og derefter vælge **DNS** på rullelisten. <br/>

1. Vælg **Tilføj post**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-domains-3.png" alt-text="Vælg Tilføj post.":::

1. Vælg **sektionen CNAME** .

1. i feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel. 

    |**Opret underdomæne**|**Alias**|
    |:-----|:-----|
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> |

1. Markér afkrydsningsfeltet for **ansvarsfraskrivelsen I am aware** , og vælg derefter **Gem**.