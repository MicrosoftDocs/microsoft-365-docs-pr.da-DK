---
title: Forbind dine DNS-poster på web.com til Microsoft 365
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
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester på web.com til Microsoft.
ms.openlocfilehash: 621364bdc0b2e9a2868084f0cb0b8eb8ef61c5b0
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780283"
---
# <a name="connect-your-dns-records-at-webcom-to-microsoft-365"></a>Forbind dine DNS-poster på web.com til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

Hvis web.com er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på web.com, konfigureres dit domæne til at arbejde med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="change-your-domains-nameserver-ns-records"></a>Skift dit domænes navneserverposter (NS)

> [!IMPORTANT]
> Du skal udføre denne procedure hos den domæneregistrator, hvor du har købt og registreret dit domæne.

Da du tilmeldte dig web.com, tilføjede du et domæne ved hjælp af **web.com installationsprocessen** .

Hvis du vil bekræfte og oprette DNS-poster for dit domæne i Microsoft, skal du først ændre navneserverne hos din domæneregistrator, så de bruger web.com navneservere.

Hvis du selv vil ændre domænets navneservere på domæneregistratorens websted, skal du følge disse trin.

1. Find det område på domæneregistratorens websted, hvor du kan redigere navneserverne for dit domæne.

2. Opret enten to navneserverposter ved hjælp af værdierne i følgende tabel, eller rediger de eksisterende navneserverposter, så de stemmer overens med disse værdier.

    |Type|Værdi|
    |---|---|
    |Fornavnserver|Brug den nameserver-værdi, der er angivet af web.com.|
    |Anden navneserver|Brug den nameserver-værdi, der er angivet af web.com.|

    > [!TIP]
    > Du skal bruge mindst to navneserverposter. Hvis der er angivet andre navneservere, skal du slette dem.

3. Gem dine ændringer.

> [!NOTE]
> Det kan tage op til flere timer at opdatere opdateringerne af din nameserver-post på tværs af internettets DNS-system. Derefter er din Microsoft-mail og andre tjenester indstillet til at arbejde med dit domæne.

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **TXT** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Vælg TXT på rullelisten Type.":::

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Henviser|TXT-værdi|TTL|
    |---|---|:----|
    |@|MS=*msXXXXXXXXX* <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|1 time|

1. Vælg **TILFØJ**.

    Vent et par minutter, før du bekræfter din nye TXT-post, så den post, du netop har oprettet, kan opdateres via internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den korrekte TXT-post, bekræftes dit domæne.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **MX** på rullelisten.

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Refererer til|Mailserver|Prioritet|TTL|
    |---|---|---|---|
    |@|*\<domain-key\>*.mail.protection.outlook.com <br/> **Bemærk:** Få dit *\<domain-key\>* fra Microsoft Administration. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml) <br/> 1|1 time|

1. Vælg **TILFØJ**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-mx-add.png" alt-text="Vælg TILFØJ.":::

1. Hvis der er andre MX-poster, skal du slette dem alle ved at vælge redigeringsværktøjet og derefter **Slette** for hver post.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-edit.png" alt-text="Vælg Rediger.":::

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **CNAME** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Refererer til|Værtsnavn|Alias til|TTL|
    |---|---|---|---|
    |Anden vært|Autodiscover|autodiscover.outlook.com|1 time|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne i vinduet.":::

1. Vælg **TILFØJ**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en *enkelt* SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **TXT** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-TXT.png" alt-text="Vælg TXT på rullelisten Type.":::

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Refererer til|TXT-værdi|TTL|
    |---|---|---|
    |@|v=spf1 include:spf.protection.outlook.com -all <br/> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|1 time|

1. Vælg **TILFØJ**.

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **SRV** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv.png" alt-text="Vælg SRV på rullelisten Type.":::

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Type|Tjeneste|Protokollen|Vægt|Port|Mål|Prioritet|TTL|
    |---|---|---|---|---|---|---|---|
    |SRV|_sip|TLS|100|443|sipdir.online.lync.com <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1|1 time|
    |SRV|_sipfederationtls|TCP|100|5061|sipfed.online.lync.com <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1|1 time|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-srv-add.png" alt-text="Skriv eller kopiér og indsæt værdierne fra tabellen i vinduet SRV-post.":::

1. Vælg **TILFØJ**.

1. Tilføj den anden SRV-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **CNAME** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Type|Refererer til|Host Name|Alias til|TTL|
    |---|---|---|---|---|
    |CNAME|Anden vært|Sip|sipdir.online.lync.com <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|
    |CNAME|Anden vært|lyncdiscover|webdir.online.lync.com <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne i vinduet.":::

1. Vælg **TILFØJ**.

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge 2 CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden med domæner på web.com ved hjælp af [dette link](https://checkout.web.com/manage-it/index.jsp). Log først på.

1. Vælg **Domænenavne** på landingssiden.

1. Under **Handlinger** skal du vælge de tre prikker og derefter vælge **Administrer** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-1.png" alt-text="Vælg Administrer på rullelisten.":::

1. Rul ned for at vælge **Avancerede værktøjer**, og vælg **ADMINISTRER** ud for **Avancerede DNS-poster**.

    Du skal muligvis vælge **Fortsæt** for at gå til siden Administrer avancerede DNS-poster.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-2.png" alt-text="Ud for Avancerede DNS-poster skal du vælge ADMINISTRER.":::

1. På siden Administrer avancerede DNS-poster skal du vælge **+ TILFØJ POST**.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-add-record.png" alt-text="Vælg + TILFØJ POST.":::

1. Under **Type** skal du vælge **CNAME** på rullelisten.

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname.png" alt-text="Vælg CNAME på rullelisten Type.":::

1. Vælg eller kopiér og indsæt værdierne i følgende tabel.

    |Type|Refererer til|Host Name|Alias til|TTL|
    |---|---|---|---|---|
    |CNAME|Anden vært|enterpriseregistration|enterpriseregistration.windows.net <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|
    |CNAME|Anden vært|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com <br/> **Denne værdi MÅ IKKE slutte med et punktum (.)**|1 time|

    :::image type="content" source="../../media/dns-webcom/webcom-domains-cname-values.png" alt-text="Skriv eller kopiér og indsæt CNAME-værdierne fra tabellen i vinduet.":::

1. Vælg **TILFØJ**.

1. Tilføj den anden CNAME-post ved at kopiere værdierne fra den anden række i tabellen.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).
