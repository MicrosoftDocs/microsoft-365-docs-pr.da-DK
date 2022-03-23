---
title: Forbind DNS-posterne hos web.com til Microsoft 365
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
description: Lær at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online og andre tjenester på web.com til Microsoft.
ms.openlocfilehash: 88b5bbae321c25520732b9f2b903a9f29fd91a35
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590768"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Forbind DNS-posterne hos web.com til Microsoft 365

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
Hvis web.com er din DNS-udbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.
  
Når du har tilføjet disse poster web.com, konfigureres dit domæne til at fungere med Microsoft-tjenester.

> [!NOTE]
>  Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Ændre dit domænes navneserverposter (NS)-poster

> [!IMPORTANT]
> Du skal udføre denne procedure hos domæneregistratoren, hvor du har købt og registreret dit domæne. 
  
Da du tilmeldte dig web.com, tilføjede du et domæne ved hjælp web.com **konfigurationsprocessen** . 
  
For at bekræfte og oprette DNS-poster for dit domæne i Microsoft skal du først ændre navneserverne hos din domæneregistrator, så de bruger de web.com navneservere.
  
Hvis du selv vil ændre domænets navneservere på domæneregistratorens websted, skal du følge disse trin.
  
1. Find det område på domæneregistratorens websted, hvor du kan redigere navneserverne for dit domæne.

2. Opret enten to navneserverposter ved hjælp af værdierne i følgende tabel, eller rediger de eksisterende navneserverposter, så de matcher disse værdier.

    |||
    |:-----|:-----|
    |Første navneserver  <br/> |Brug den navneserverværdi, der leveres af web.com.  <br/> |
    |Anden navneserver  <br/> |Brug den navneserverværdi, der leveres af web.com.  <br/> |

    > [!TIP]
    > Du skal bruge mindst to navneserverposter. Hvis der er angivet andre navneservere, bør du slette dem. 
  
3. Gem ændringerne.

> [!NOTE]
> Det kan tage adskillige timer, før opdateringerne af navneserverposten registreres i internettets DNS-system. Derefter vil din Microsoft-mail og andre tjenester være klar til at fungere med dit domæne. 
  
## <a name="add-a-txt-record-for-verification"></a>Tilføje en TXT-post til godkendelse

Før du kan bruge dit domæne med Microsoft, skal vi være sikre på, at du ejer det. Hvis du kan logge på din konto hos din domæneregistrator og oprette DNS-posten, har Microsoft bevis for, at du ejer domænet.
  
> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. påvirker det ikke andet. Du kan slette det senere, hvis du vil. 
  
1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**.
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten."::: 
  
1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge TXT** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Vælg TXT på rullelisten Type.":::

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel.

    |**Refererer**|**TXT-værdi**|**TTL**|
    |:-----|:-----|:----|
    |@  <br/> |MS=ms *XXXXXXXX*  <br/> **Bemærk!** Dette er et eksempel. Brug din specifikke **værdi fra Destination eller** adressehensepunkter her fra tabellen.  [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md)    |1 time  <br/> |
  
1. Vælg **TILFØJ**.
  
    Vent et par minutter, før du bekræfter din nye TXT-post, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

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

1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**. 
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::
  
1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge MX** på rullelisten.

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel. 

    | **Refererer til** | **Mailserver**|**Prioritet**|**TTL**|
    |:-----|:-----|:-----|:-----| 
    | @ |*\<domain-key\>*  .mail.protection.outlook.com  <br/> **Bemærk!** Få din  *\<domain-key\>*  fra Microsoft Administration.   [Hvordan finder jeg dette?](../get-help-with-domains/information-for-dns-records.md) | Du kan finde flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/> 1| 1 time  <br/> |

1. Vælg **TILFØJ**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="Vælg TILFØJ.":::

1. Hvis der er andre MX-poster, skal du slette dem alle ved at vælge redigeringsværktøjet og derefter **Slette** for hver post. 

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Vælg Rediger.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**. 
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge CNAME** fra rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel. 

    |**Refererer til** | **Værtsnavn** | **Alias til**|**TTL**|
    |:-----|:-----|:-----|:-----|
    | Anden vært  <br/>| autodiscover  <br/>| autodiscover.outlook.com  <br/> | 1 time  <br/>  |

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne i vinduet.":::
  
1. Vælg **TILFØJ**.
  
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du mailfejl samt problemer med levering og spamklassifikation. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. I stedet skal du føje de nødvendige Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge sæt af værdier. 
  
1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**. 
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::
  
1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge TXT** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Vælg TXT på rullelisten Type.":::

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel. 

    |**Refererer til**|**TXT-værdi**|**TTL**|
    |:-----|:-----|:-----|
    |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk!** Vi anbefaler, at du kopierer og indsætter denne indtastning, så alle mellemrum forbliver korrekte.  | 1 time  <br/> 

1. Vælg **TILFØJ**.
  
## <a name="advanced-option-skype-for-business"></a>Indstillingen Avanceret: Skype for Business

Vælg kun denne indstilling, hvis din organisation Skype for Business til onlinekommunikationstjenester som chat, telefonmøde og videoopkald ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og forbinde brugere til tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to nødvendige SRV-poster

1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**. 
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::
  
1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge SRV** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Vælg SRV på rullelisten Type.":::

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel.

    | **Type** |**Tjeneste**|**Protokol**|**Vægt**|**Port**|**Destination**|**Prioritet**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    | SRV |_sip  <br/> |TLS  <br/> |100  <br/> |443  <br/> |sipdir.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> | 1  <br/> | 1 time  <br/> |
    | SRV |_sipfederationtls  <br/> |TCP <br/> |100  <br/> |5061  <br/> |sipfed.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> |1  <br/> | 1 time  <br/> |

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Skriv eller kopiér og indsæt værdierne fra tabellen i vinduet SRV-post.":::

1. Vælg **TILFØJ**.
  
1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Finde og rette problemer efter at have [tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**.

1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge CNAME** fra rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel. 

    | **Type**|**Refererer til | Værtsnavn**|**Alias til**| **TTL** |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Anden vært | sip  <br/> |sipdir.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> |1 time  <br/> |
    | CNAME| Anden vært | lyncdiscover  <br/> |webdir.online.lync.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> | 1 time  <br/> |
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne i vinduet.":::

1. Vælg **TILFØJ**.
  
1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Administration af Intune og mobilenheder til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Administration af mobilenheder kræver 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records"></a>Tilføj de to nødvendige CNAME-poster

1. For at komme i gang skal du gå til siden med dine domæner web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log på først.
  
1. På landingssiden skal du **vælge Domænenavne**.
  
1. Under **Handlinger** skal du vælge de tre prik og derefter **vælge** Administrer på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at **vælge Avancerede værktøjer**, og vælg **MANAGE ud for Avancerede DNS-poster**.

    Du skal muligvis vælge Fortsæt **for** at komme til siden Administrer avancerede DNS-poster.
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge MANAGE.":::

1. På siden Manage Advanced DNS Records skal du vælge **+ ADD RECORD**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + ADD RECORD.":::

1. Under **Type** skal **du vælge CNAME** fra rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. Vælg, eller kopiér og indsæt værdierne fra følgende tabel.

    | **Type**|**Refererer til | Værtsnavn**|**Alias til**| **TTL** |
    |:-----|:-----|:-----|:-----|:-----|
    | CNAME | Anden vært | enterpriseregistration  <br/> |enterpriseregistration.windows.net  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> | 1 time  <br/> |
    | CNAME | Anden vært |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com  <br/> **Denne værdi KAN IKKE slutte med et punktum (.)** <br/> | 1 time  <br/> |
  
    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.
  
1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager som regel ca. 15 minutter, før ÆNDRINGERNE I DNS træder i kraft. Det kan dog tage længere tid for en ændring, du har foretaget, at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer efter at have tilføjet DNS-poster, skal du se Foretage fejlfinding efter ændring [af dit domænenavn eller DINE DNS-poster](../get-help-with-domains/find-and-fix-issues.md).