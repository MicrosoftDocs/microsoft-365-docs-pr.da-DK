---
title: Forbind dine DNS-poster på GoDaddy til Microsoft 365
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
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos GoDaddy til Microsoft.
ms.openlocfilehash: 6cf110b55c76ce6c857f13dcd5b0075b309b654f
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780341"
---
# <a name="connect-your-dns-records-at-godaddy-to-microsoft-365"></a>Forbind dine DNS-poster på GoDaddy til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis GoDaddy er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

## <a name="before-you-begin"></a>Før du begynder

Du har to muligheder for at konfigurere DNS-poster for dit domæne:

- [**Brug Domæne Forbind**](#use-domain-connect-to-verify-and-set-up-your-domain) Hvis du ikke har konfigureret dit domæne med en anden mailtjenesteudbyder, skal du bruge trinnene Domæne Forbind til automatisk at bekræfte og konfigurere dit nye domæne til brug sammen med Microsoft 365.

   ELLER

- [**Brug de manuelle trin**](#create-dns-records-with-manual-setup) Bekræft dit domæne ved hjælp af de manuelle trin nedenfor, og vælg, hvornår og hvilke poster der skal føjes til din domæneregistrator. Dette giver dig mulighed for at konfigurere nye MX-poster (mail), f.eks. når det passer dig.

## <a name="use-domain-connect-to-verify-and-set-up-your-domain"></a>Brug Domæne Forbind til at bekræfte og konfigurere dit domæne

Følg disse trin for automatisk at bekræfte og konfigurere dit GoDaddy-domæne med Microsoft 365:

1. Vælg **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> i Microsoft 365 Administration, og vælg det domæne, du vil konfigurere.

1. Vælg de tre prikker (flere handlinger) > vælg **Start konfiguration**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Under Hvordan vil du oprette forbindelse til dit domæne? skal du vælge **Fortsæt**.

1. På siden Tilføj DNS-poster skal du vælge **Tilføj DNS-poster**.

1. Log på din konto på logonsiden GoDaddy, og vælg **Godkend**.

   Dette fuldfører domænekonfigurationen for Microsoft 365.

## <a name="create-dns-records-with-manual-setup"></a>Opret DNS-poster med manuel konfiguration

Når du har tilføjet disse poster på GoDaddy, konfigureres dit domæne til at arbejde med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Poster** skal du vælge **TILFØJ** (du skal muligvis rulle ned).

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **TXT** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg TXT på rullelisten Type.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra tabellen.

   |Type|Vært|TXT-værdi|TTL|
   |---|---|---|---|
   |TXT|@|MS=ms *XXXXXXXXX*<br>**Bemærk**! Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|1 time  <br>|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Udfyld værdierne fra tabellen for TXT-posten.":::

1. Vælg **Gem**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXTSave.png" alt-text="Vælg Gem.":::

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den korrekte TXT-post, bekræftes dit domæne.
  
Sådan bekræfter du posten i Microsoft 365:
  
1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.
  
1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

3. Under **Poster** skal du vælge **TILFØJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

4. Vælg **MX** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg MX på rullelisten Type.":::

5. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   Vælg **værdierne Type** og **TTL** på rullelisten.

   |Type|Vært|Peger på|Prioritet|TTL|
   |---|---|---|---|---|
   |MX|@| *\<domain-key\>*.mail.protection.outlook.com  <br/> **Bemærk:** Få din *\<domain-key\>* fra din Microsoft-konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|10  <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|1 time|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Udfyld værdierne fra tabellen for MX-posten.":::

6. Vælg **Gem**.

### <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

3. Under **Poster** skal du vælge **TILFØJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

4. Vælg **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg CNAME på rullelisten Type.":::

5. Opret CNAME-posten.

   I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

   Vælg **TTL-værdien** på rullelisten.

   |Type|Vært|Peger på|TTL|
   |---|---|---|---|
   |CNAME|Autodiscover|autodiscover.outlook.com|1 time|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Udfyld værdierne fra tabellen for CNAME-posten.":::

6. Vælg **Gem**.

### <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

2. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

3. Under **Poster** skal du vælge **TILFØJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

4. Vælg **TXT** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg TXT på rullelisten Type.":::

5. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier.

   Vælg **TTL-værdien** på rullelisterne.

   |Type|Vært|TXT-værdi|TTL|
   |---|---|---|---|
   |TXT|@|v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|1 time|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-TXT-values.png" alt-text="Udfyld værdierne fra tabellen for TXT-posten.":::

6. Vælg **Gem**.

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Poster** skal du vælge **TILFØJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **SRV** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg SRV på rullelisten Type.":::

1. Opret den første SRV-post.

   I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

   Vælg **værdierne Type** og **TTL** på rullelisterne.

   |Type|Tjeneste|Protokollen|Navn|Mål|Prioritet|Vægt|Port|TTL|
   |---|---|---|---|---|---|---|---|---|
   |SRV|_sip|_tls|@|sipdir.online.lync.com|100| 1|443|1 time|
   |SRV|_sipfederationtls|_tcp|@| sipfed.online.lync.com| 100|1|5061|1 time|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-SRV-values.png" alt-text="Udfyld værdierne fra tabellen for SRV-posten.":::

1. Vælg **Gem**.

1. Tilføj den anden SRV-post ved at vælge værdierne i den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business
  
1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Poster** skal du vælge **TILFØJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

   |Type|Vært|Peger på|TTL|
   |---|---|---|---|
   |CNAME|Sip|sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|
   |CNAME|lyncdiscover|webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Udfyld værdierne fra tabellen for CNAME-posten.":::
  
1. Vælg **Gem**.
  
1. Tilføj den anden CNAME-post ved at vælge værdierne i den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster Mobile Enhedshåndtering

1. Du kommer i gang ved at gå til siden med domæner på GoDaddy ved hjælp af [dette link](https://account.godaddy.com/products/?go_redirect=disabled).

   Hvis du bliver bedt om at logge på, skal du bruge dine legitimationsoplysninger til logon, vælge dit logonnavn øverst til højre og derefter vælge **Mine produkter**.

1. Under **Domæner** skal du vælge de tre prikker ud for det domæne, du vil bekræfte, og derefter vælge **Administrer DNS**.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-1.png" alt-text="Vælg Administrer DNS på rullelisten.":::

1. Under **Poster** skal du vælge **TILFØJ**.

   :::image type="content" source="../../media/dns/56527673-ffb3b300-651b-11e9-91c2-83dc9fe5ca30.png" alt-text="Vælg TILFØJ.":::

1. Vælg **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-Type.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. I de tomme felter for de nye poster skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel.

   |Type|Vært|Peger på|TTL|
   |---|---|---|---|
   |CNAME|enterpriseregistration|enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|
   |CNAME|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|1 time|

   :::image type="content" source="../../media/dns-godaddy/godaddy-domains-CNAME-values.png" alt-text="Udfyld værdierne fra tabellen for CNAME-posten.":::
  
1. Vælg **Gem**.
  
1. Tilføj den anden CNAME-post ved at vælge værdierne i den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
