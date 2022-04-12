---
title: Forbind dine DNS-poster på OVH til Microsoft 365
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
description: Få mere at vide om, hvordan du bekræfter dit domæne og konfigurerer DNS-poster for mail, Skype for Business Online og andre tjenester hos OVH til Microsoft.
ms.openlocfilehash: 3b3174860a65d13d68b2d5f7773f927dd706f1a0
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780407"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Forbind dine DNS-poster på OVH til Microsoft 365

[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) , hvis du ikke kan finde det, du leder efter.

Hvis OVH er din DNS-hostingudbyder, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere DNS-poster for mail, Skype for Business Online osv.

Når du har tilføjet disse poster på OVH, konfigureres dit domæne til at arbejde med Microsoft-tjenester.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-a-txt-record-for-verification"></a>Tilføj en TXT-post til bekræftelse

Før du bruger dit domæne med Microsoft, skal vi sikre os, at du ejer det. Din mulighed for at logge på din konto hos din domæneregistrator og oprette DNS-posten beviser for Microsoft, at du ejer domænet.

> [!NOTE]
> Denne post bruges kun til at bekræfte, at du ejer dit domæne. det påvirker ikke noget andet. Du kan slette den senere, hvis du vil.

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **TXT**

    ![OVH vælg TXT-post.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

   |Posttype|Underdomæne|TTL|Værdi|
   |---|---|---|---|
   |TXT|(lad argumentet være tomt)|3600 (sekunder)|MS=msxxxxxxxx  <br/> **Bemærk:** Dette er et eksempel. Brug din specifikke **værdi for Destination eller Adresser fra** tabellen her.  [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|

1. Vælg **Næste**.

1. Vælg **Bekræft**.

    ![OVH bekræft TXT til bekræftelse.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)

1. Vent et par minutter, før du fortsætter, så den post, du lige har oprettet, kan opdateres på tværs af internettet.

Nu, hvor du har tilføjet posten på domæneregistratorens websted, skal du gå tilbage til Microsoft og anmode om posten. Når Microsoft finder den korrekte TXT-post, bekræftes dit domæne.

Sådan bekræfter du posten i Microsoft 365:

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

1. På siden Domæner skal du vælge det domæne, du bekræfter, og vælge **Start konfiguration**.

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Vælg Start konfiguration.":::

1. Vælg **Fortsæt**.

1. På siden **Bekræft domæne** skal du vælge **Bekræft**.

> [!NOTE]
>  Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **MX**.

    ![OVH MX-posttype.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra følgende tabel. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

    > [!NOTE]
    > Som standard bruger OVH relativ notation for målet, hvilket føjer domænenavnet til slutningen af destinationsposten. Hvis du i stedet vil bruge absolut notation, skal du føje en prik til målposten som vist i nedenstående tabel.

   |Underdomæne|TTL|Prioritet|Mål|
   |---|---|---|---|
   |(lad argumentet være tomt)|3600 (sekunder)|0  <br/> Du kan få flere oplysninger om prioritet under [Hvad er MX-prioritet?](../setup/domains-faq.yml)|\<domain-key\>.mail.protection.outlook.com.  <br/> **Bemærk:** Få din *\<domain-key\>* fra din Microsoft-konto. [Hvordan gør jeg finde det her?](../get-help-with-domains/information-for-dns-records.md)|

    ![OVH MX post for post.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)

1. Vælg **Næste**.

    ![OVH MX-post vælger Næste.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)

1. Vælg **Bekræft**.

    ![OVH MX-post vælger Bekræft.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. Slet alle andre MX-poster på listen på siden **DNS-zone** . Vælg hver post, og vælg ikonet **Slet** papirkurv i kolonnen **Handlinger**.

    ![Slet MX-post i OVH.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)

1. Vælg **Bekræft**.

## <a name="add-the-cname-record-required-for-microsoft"></a>Tilføj den CNAME-post, der kræves til Microsoft

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **CNAME**.

    ![OVH Tilføj CNAME-posttype.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

   |Underdomæne|TTL|Mål|
   |---|---|---|
   |Autodiscover|3600 (sekunder)|autodiscover.outlook.com.|

    ![OVH CNAME-post.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)

1. Vælg **Næste**.

    ![OVH Tilføj CNAME-værdier, og vælg Næste.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Vælg **Bekræft**.

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Tilføj en TXT-post til SPF for at forhindre mailspam

> [!IMPORTANT]
> Du kan ikke have mere end én TXT-post til SPF for et domæne. Hvis dit domæne har mere end én SPF-post, får du problemer med mailfejl samt problemer med levering og spamklassificering. Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny til Microsoft. Føj i stedet de påkrævede Microsoft-værdier til den aktuelle post, så du har en  *enkelt*  SPF-post, der indeholder begge værdisæt.

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **TXT**.

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

   |Underdomæne|TTL|Værdi|
   |---|---|---|
   |(lad argumentet være tomt)|3600 (sekunder)|v=spf1 include:spf.protection.outlook.com -all <br/**Bemærk!** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|

    ![OVH Tilføj TXT-post for SPF.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)

1. Vælg **Næste**.

    ![OVH Tilføj TXT-post for SPF, og vælg Næste.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)

1. Vælg **Bekræft**.

    ![OVH Tilføj TXT-post for SPF og Bekræft.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)

## <a name="advanced-option-skype-for-business"></a>Avanceret indstilling: Skype for Business

Vælg kun denne indstilling, hvis din organisation bruger Skype for Business til onlinekommunikationstjenester, f.eks. chat, telefonmøder og videoopkald, ud over Microsoft Teams. Skype skal bruge 4 poster: 2 SRV-poster til bruger-til-bruger-kommunikation og 2 CNAME-poster for at logge på og oprette forbindelse mellem brugere og tjenesten.

### <a name="add-the-two-required-srv-records"></a>Tilføj de to påkrævede SRV-poster

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **SRV**.

1. I felterne for den nye post skal du skrive eller kopiere og indsætte følgende værdier. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

   |Underdomæne|TTL (sekunder)|Prioritet|Vægt|Port|Mål|
   |---|---|---|---|---|---|
   |_sip._tls|3600 (s.)|100|1|443|sipdir.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**><br> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|
   |_sipfederationtls._tcp|3600 (s.)|100|1|5061|sipfed.online.lync.com. **Denne værdi SKAL slutte med et punktum (.)**<br> **Bemærk:** Vi anbefaler, at du kopierer og indsætter denne post, så al afstand forbliver korrekt.|

1. Hvis du vil tilføje den anden SRV-post, skal du vælge **Tilføj en anden post**, oprette en post ved hjælp af værdierne fra den næste række i tabellen og derefter vælge **Opret poster**.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Find og løs problemer, når du har tilføjet dit domæne eller DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

### <a name="add-the-two-required-cname-records-for-skype-for-business"></a>Tilføj de to påkrævede CNAME-poster for Skype for Business

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **CNAME**.

    ![OVH Tilføj CNAME-posttype.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

   |Underdomæne|TTL|Mål|
   |---|---|---|
   |Sip|3600 (s.)|sipdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|
   |lyncdiscover|3600 (s.)|webdir.online.lync.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|

1. Vælg **Næste**.

    ![OVH Tilføj CNAME-værdier, og vælg Næste.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Vælg **Bekræft**.

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).

## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Avanceret indstilling: Intune og mobil Enhedshåndtering til Microsoft 365

Denne tjeneste hjælper dig med at sikre og fjernstyre mobilenheder, der opretter forbindelse til dit domæne. Mobil-Enhedshåndtering skal bruge to CNAME-poster, så brugerne kan tilmelde enheder til tjenesten.

### <a name="add-the-two-required-cname-records-for-mobile-device-management"></a>Tilføj de to påkrævede CNAME-poster for Mobile-Enhedshåndtering

1. Du kommer i gang ved at gå til siden med domæner i OVH ved hjælp af [dette link](https://www.ovh.com/manager/). Du bliver bedt om at logge på.

    ![OVH-logon.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Vælg navnet på det domæne, du vil redigere, under **Vis alle mine aktiviteter** på dashboardets landingsside.

1. Vælg **DNS-zone**.

    ![OVH Vælg DNS-zone.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)

1. Vælg **Tilføj en post**.

    ![OVH Tilføj en post.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Vælg **CNAME**.

    ![OVH Tilføj CNAME-posttype.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)

1. I felterne for den nye post skal du skrive eller kopiere og indsætte værdierne fra den første række i følgende tabel. Hvis du vil tildele en TTL-værdi, skal du vælge **Brugerdefineret** på rullelisten og derefter skrive værdien i tekstfeltet.

   |Underdomæne|TTL|Mål|
   |---|---|---|
   |enterpriseregistration  <br/>|3600 (s.)|enterpriseregistration.windows.net.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|
   |enterpriseenrollment|3600 (s.)|enterpriseenrollment-s.manage.microsoft.com.  <br/> **Denne værdi SKAL slutte med et punktum (.)**|

1. Vælg **Næste**.

    ![OVH Tilføj CNAME-værdier, og vælg Næste.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)

1. Vælg **Bekræft**.

1. Tilføj den anden CNAME-post.

> [!NOTE]
> Det tager typisk ca. 15 minutter, før DNS-ændringer træder i kraft. Det kan dog undertiden tage længere tid for en ændring, du har foretaget for at opdatere på tværs af internettets DNS-system. Hvis du har problemer med mailflow eller andre problemer, når du har tilføjet DNS-poster, skal du se [Fejlfinding af problemer, når du har ændret dit domænenavn eller dine DNS-poster](../get-help-with-domains/find-and-fix-issues.md).