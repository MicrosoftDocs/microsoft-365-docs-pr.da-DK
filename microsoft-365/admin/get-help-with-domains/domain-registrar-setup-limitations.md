---
title: Domæneregistratorer med konfigurationsbegrænsninger
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- MET150
ROBOTS: NOINDEX
description: Nogle domæneregistratorer tilbyder begrænsede tjenester, hvilket betyder, at ikke alle Microsoft-funktioner fungerer med alle domæner.
ms.openlocfilehash: 2d192f03c5a586e4355c1f9a08d312a07af3d501
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592320"
---
# <a name="domain-registrars-with-setup-limitations"></a>Domæneregistratorer med konfigurationsbegrænsninger

[Oprette DNS-poster på DNSMadeEasy for Microsoft](#create-dns-records-at-dnsmadeeasy-for-microsoft)\
[Opret DNS-poster på easyDNS for Microsoft](#create-dns-records-at-easydns-for-microsoft)\
[Opret DNS-poster hos Freenom til Microsoft](#create-dns-records-at-freenom-for-microsoft)\
[Oprette DNS-poster på MyDomain til Microsoft](#create-dns-records-at-mydomain-for-microsoft)\
[Opret DNS-poster for Microsoft ved Windows-baseret DNS](#create-dns-records-for-microsoft-using-windows-based-dns)\
[Oprette DNS-poster, når domænet administreres af Google (eNom)](#create-dns-records-when-your-domain-is-managed-by-google-enom)\
[Opret DNS-poster på 1&1 IONOS til Microsoft](#create-dns-records-at-11-ionos-for-microsoft)

Nogle domæneregistratorer har betydelige tjenestebegrænsninger, hvilket betyder, at ikke alle Microsoft-funktioner fungerer med alle domæner. Specifikke begrænsninger for nogle registratorer er identificeret i denne artikel. 

## <a name="create-dns-records-at-dnsmadeeasy-for-microsoft"></a>Oprette DNS-poster på DNSMadeEasy for Microsoft

For DNSMadeEasy-konti blev det domæne, du har tilføjet, købt hos en separat domæneregistrator. DNSMadeEasy tilbyder ikke domæneregistreringstjenester. Det at du kan logge på hos DNSMadeEasy og oprette DNS-posten, er tilstrækkeligt bevis for ejerskabet.

## <a name="create-dns-records-at-easydns-for-microsoft"></a>Opret DNS-poster på easyDNS for Microsoft

SRV-poster er i øjeblikket ikke tilgængelige under nogen easyDNS-tjenestepakke. Det kan være nødvendigt at opgradere til et højere tjenesteniveau med easyDNS for at tilføje SRV-poster, der er nødvendige for Teams.

## <a name="create-dns-records-at-freenom-for-microsoft"></a>Opret DNS-poster hos Freenom til Microsoft

Webstedet Freenom understøtter ikke tilføjelse af SRV-poster, hvilket betyder, at Teams funktioner til mail og mail ikke fungerer. Uanset hvilken Microsoft-plan du bruger, er der betydelige tjenestebegrænsninger, og det kan være en god ide at skifte til en anden DNS-udbyder.

## <a name="create-dns-records-at-mydomain-for-microsoft"></a>Oprette DNS-poster på MyDomain til Microsoft

Webstedet MyDomain understøtter ikke SRV-poster, hvilket betyder, Teams funktioner til mail og mail ikke fungerer. Uanset hvilken Microsoft-plan du bruger, er der betydelige tjenestebegrænsninger, hvis du administrerer dine DNS-poster på MyDomain, og du ønsker muligvis at skifte til en anden DNS-udbyder.

## <a name="create-dns-records-for-microsoft-using-windows-based-dns"></a>Opret DNS-poster for Microsoft ved Windows-baseret DNS

Gå til den side, der indeholder DNS-posterne for dit domæne. Hvis du arbejder i en Windows Server 2008, skal du gå til **Start**, **Kør**. Hvis du arbejder i en Windows Server 2012, skal du trykke på **Windows og** **r**. Skriv **dnsmgmnt.msc**, og vælg derefter **OK**. I DNS Manager skal du udvide **DNS-servernavn**,  **Forward Lookup Zones**. Vælg dit domæne. Du er nu klar til at oprette DNS-posterne.

## <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>Oprette DNS-poster, når domænet administreres af Google (eNom)

Hvis du har købt dit domæne via Google, da du tilmeldte dig din Google Apps for Work-konto, administreres dine DNS-poster af Google, men du er registreret hos eNom. Du kan få adgang til eNom og oprette DNS via siden Google Domains.

## <a name="create-dns-records-at-11-ionos-for-microsoft"></a>Opret DNS-poster på 1&1 IONOS til Microsoft

1&1 IONOS tillader ikke, at et domæne både har en MX-post og en Autodiscover CNAME-post på øverste niveau. Dette begrænser den måde, hvorpå du kan konfigurere Exchange Online til Microsoft. Der findes en løsning, men vi anbefaler kun at anvende den, hvis du allerede har erfaring med at oprette underdomæner på 1&1 IONOS.

Hvis du trods tjenestebegrænsningerne vælger at administrere dine egne Microsoft DNS-poster på 1&1 IONOS, skal du følge trinnene i denne artikel for at bekræfte dit domæne og konfigurere dine DNS-poster til mail, Skype for Business Online osv.

1&IONOS kræver en løsning, så du kan bruge en MX-post sammen med de CNAME-poster, der kræves til Microsoft-mailtjenester. Denne løsning kræver, at du opretter et sæt underdomæner på 1&1 IONOS og tildeler dem til CNAME-poster.

> [!NOTE]
> Sørg for, at du har mindst to tilgængelige underdomæner, før du starter denne procedure. Vi anbefaler kun denne løsning, hvis du allerede har erfaring med at oprette underdomæner på 1&1 IONOS.

### <a name="basic-cname-records"></a>Grundlæggende CNAME-poster

1.  For at komme i gang skal du gå til siden med dine domæner på 1&1 IONOS. Du vil blive bedt om at logge på.

1.  Vælg **Administrer domæner**.

1.  På siden Domain Center skal du finde det domæne, du vil opdatere, og derefter **vælge Manage Subdomains**. Nu skal du oprette to underdomæner og angive en **Alias-værdi** for hver (Dette er påkrævet, fordi 1&1 IONOS kun understøtter én CNAME-post på øverste niveau, men Microsoft kræver flere CNAME-poster).

1.  Først skal du oprette Autodiscover-underdomænet. I sektionen **Subdomain Overview** skal du vælge **Create Subdomain**.

1.  I feltet **Create Subdomain** til det nye underdomæne skal du kun skrive eller kopiere og indsætte **Create Subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere.

    |Opret underdomæne|Alias|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1.  Vælg **Opret underdomæne**.

1.  I sektionen **Subdomain Overview** skal du finde underdomænet Autodiscover, som du lige har oprettet, og derefter vælge kontrolelementet Panel (v) for det pågældende underdomæne.

1.  I området **Subdomain Indstillinger** skal du vælge **Edit DNS Indstillinger**.

1.  I sektionen **A/AAAA Records (IP Addresses)** i området **IP address (A Record)** skal du vælge **CNAME**.

1. I feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel.

    |Opret underdomæne|Alias|
    |:----|:----|
    |autodiscover|autodiscover.outlook.com|

1. Markér afkrydsningsfeltet for **ansvarsfraskrivelsen I am aware** .

1. Vælg **Gem**.

### <a name="additional-cname-records"></a>Yderligere CNAME-poster

De ekstra CNAME-poster i følgende procedure aktiverer Skype for Business onlinetjenester. Brug samme fremgangsmåde, som du brugte til de to CNAME-poster, du allerede har oprettet.

**Oprette det tredje underdomæne (Lyncdiscover)**

1.  I sektionen **Subdomain Overview** skal du vælge **Create Subdomain**.

1.  I feltet **Create Subdomain** til det nye underdomæne skal du kun skrive eller kopiere og indsætte **Create Subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere.

    |Opret underdomæne|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Vælg **Opret underdomæne**.

1.  På siden Domain Center skal du vælge **Manage Subdomains**.

1.  I sektionen **Subdomain Overview** skal du finde det lyncdiscover-underdomæne, du lige har oprettet, og derefter vælge kontrolelementet Panel (v) for det pågældende underdomæne. I området **Subdomain Indstillinger** skal du vælge **Edit DNS Indstillinger**.

1.  I sektionen **A/AAAA Records (IP Addresses)** i området **IP address (A Record)** skal du vælge **CNAME**.

1.  I feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel.

    |Opret underdomæne|Alias|
    |:----|:----|
    |lyncdiscover|webdir.online.lync.com|

1.  Markér afkrydsningsfeltet for **ansvarsfraskrivelsen I am aware** , og vælg derefter **Gem**.

1.  Vælg **Ja Indstillinger** dialogboksen Rediger DNS-poster.

**Opret det fjerde underdomæne (SIP)**

1.  I sektionen **Subdomain Overview** skal du vælge **Create Subdomain**.

1.  I feltet **Create Subdomain** til det nye underdomæne skal du kun skrive eller kopiere og indsætte **Create Subdomain-værdien** fra følgende tabel. Du skal tilføje **Alias-værdien** senere.

    |Opret underdomæne|Alias|
    |:----|:----|
    |sip|sipdir.online.lync.com|  

1.  Vælg **Opret underdomæne**.

1.  På siden Domain Center skal du vælge **Manage Subdomains**.

1.  I sektionen **Subdomain Overview** skal du finde det sip-underdomæne, du lige har oprettet, og derefter vælge kontrolelementet Panel (v) for det pågældende underdomæne. <br/> I området **Subdomain Indstillinger** skal du vælge **Edit DNS Indstillinger**.

1.  I sektionen **A/AAAA Records (IP Addresses)** i området **IP address (A Record)** skal du vælge **CNAME**.

1.  I feltet **Alias:** skal du kun skrive eller kopiere og indsætte **Alias-værdien** fra følgende tabel.

    |Opret underdomæne|Alias|
    |:----|:----|
    |sip|sipdir.online.lync.com|

1.  Markér afkrydsningsfeltet for **ansvarsfraskrivelsen I am aware** , og vælg derefter **Gem**.

1.  Vælg **Ja Indstillinger** dialogboksen Rediger DNS-poster.

### <a name="cname-records-needed-for-mdm"></a>CNAME-poster, der skal bruges til MDM

Følg fremgangsmåden, du anvendte til de fire andre CNAME-poster, men brug disse værdier:

|Opret underdomæne|Alias|
|:----|:----|
|enterpriseregistration|enterpriseregistration.windows.net|
|enterpriseenrollment|enterpriseenrollment-s.manage.microsoft.com|
