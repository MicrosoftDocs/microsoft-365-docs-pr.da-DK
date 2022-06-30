---
title: Opret forbindelse mellem dine DNS-poster på Network Solutions og Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos Network Solutions til Microsoft.
ms.openlocfilehash: 6ebe81c17d02c0cc6126f75f3b6471e01a334db4
ms.sourcegitcommit: 8cd230e243eba452b27f725d66152becb6aff49b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66563269"
---
# <a name="connect-your-dns-records-at-network-solutions-to-microsoft-365"></a>Opret forbindelse mellem dine DNS-poster på Network Solutions og Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis Network Solutions er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på Network Solutions, konfigureres dit domæne til at fungere sammen med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **TXT** på rullelisten.

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne i følgende tabel.

   |Refererer til|TXT-værdi|TTL|
   |---|---|---|
   |@  <br/> (Systemet ændrer denne værdi til **@ (Ingen),** når du gemmer posten.|MS=ms *XXXXXXXXX*  <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her.  [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|3600|

1. Vælg **TILFØJ**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="Vælg TILFØJ.":::

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den TXT-post, du har oprettet.

   Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den rigtige TXT-post, er dit domæne godkendt.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Indstillingsdomæner**</a>\>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

   :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **MX** på rullelisten.

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   |Refererer til|Mailserver|Prioritet|TTL|
   |---|---|---|---|
   |@|*\<domain-key\>*.mail.protection.outlook.com  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)** <br/> **Bemærk:** Få din *\<domain-key\>* fra din Microsoft-konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|0  <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|1 time|

1. Vælg **TILFØJ**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-MX-add.png" alt-text="Vælg TILFØJ.":::

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den TXT-post, du har oprettet.

1. Hvis der er andre MX-poster, skal du slette dem alle ved at vælge redigeringsværktøjet og derefter **Slette** for hver post.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-edit.png" alt-text="Vælg værktøjet Rediger.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Avancerede værktøjer**, og ud for **Avancerede DNS-poster** skal du vælge **ADMINISTRER**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Vælg CNAME-type på rullelisten.":::

1. I felterne for CNAME-posten skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   |Refererer til|Værtsnavn|Alias til|TTL|
   |---|---|---|---|
   |Anden vært|Autodiscover|autodiscover.outlook.com **Denne værdi MÅ IKKE slutte med et punktum (.)** <br/> 1 time|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den post, du har oprettet.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Avancerede værktøjer**, og ud for **Avancerede DNS-poster** skal du vælge **ADMINISTRER**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **TXT** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-TXT.png" alt-text="Vælg TXT på rullelisten Type.":::

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier.

   |Refererer til|TXT-værdi|TTL
   |---|---|---|
   |@  <br/> (Systemet ændrer denne værdi til **@ (Ingen),** når du gemmer posten.|v=spf1 include:spf.protection.outlook.com -all  <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|1 time|

1. Vælg **TILFØJ**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add.png" alt-text="Vælg TILFØJ.":::

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den post, du har oprettet.

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Avancerede værktøjer**, og ud for **Avancerede DNS-poster** skal du vælge **ADMINISTRER**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **SRV** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv.png" alt-text="Vælg SRV på rullelisten Type.":::

1. I felterne for de to nye poster skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   Vælg **tjeneste-** og **protokolværdierne** på rullelisterne.

   |Type|Tjeneste|Protokollen|Vægt|Port|Mål|Prioritet|TTL|
   |---|---|---|---|---|---|---|---|
   |SRV|_sip|TLS|100|443|sipdir.online.lync.com  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1|1 time|
   |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1|1 time|

1. Vælg **TILFØJ**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-srv-add.png" alt-text="Vælg TILFØJ.":::

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den post, du har oprettet.

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Avancerede værktøjer**, og ud for **Avancerede DNS-poster** skal du vælge **ADMINISTRER**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Vælg CNAME-type på rullelisten.":::

1. I felterne for CNAME-posten skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   |Type|Refererer til|Værtsnavn|Alias til|TTL|
   |---|---|---|---|---|
   |CNAME|Anden vært|Sip|sipdir.online.lync.com  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|
   |CNAME|Anden vært|lyncdiscover|webdir.online.lync.com  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den post, du har oprettet.

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden med domæner på Netværksløsninger ved hjælp af [dette link](https://www.networksolutions.com/manage-it). Du bliver bedt om at logge på.

1. Vælg **Domænenavne** på landingssiden.

1. Markér afkrydsningsfeltet ud for det domæne, du vil ændre.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Vælg **Avancerede værktøjer**, og ud for **Avancerede DNS-poster** skal du vælge **ADMINISTRER**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

   Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+TILFØJ POST**.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-add-record.png" alt-text="Vælg +TILFØJ POST.":::

1. Under **Type** skal du vælge **CNAME** på rullelisten.

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname.png" alt-text="Vælg CNAME-type på rullelisten.":::

1. I felterne for CNAME-posten skal du skrive eller kopiere og indsætte værdierne fra følgende tabel.

   |Type|Refererer til|Værtsnavn|Alias til|TTL|
   |---|---|---|---|---|
   |CNAME|Anden vært|enterpriseregistration|enterpriseregistration.windows.net  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|
   |CNAME|Anden vært|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com  <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|

   :::image type="content" source="../../media/dns-networksolutions/networksolutions-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.

   > [!NOTE]
   > Vælg **Klassisk visning** øverst til højre for at få vist den post, du har oprettet.

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

