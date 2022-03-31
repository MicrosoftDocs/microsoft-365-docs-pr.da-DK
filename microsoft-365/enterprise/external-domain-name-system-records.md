---
title: Eksterne DNS-poster for Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/10/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c0531a6f-9e25-4f2d-ad0e-a70bfef09ac0
description: En referenceliste over eksterne Domain Name System-poster, der skal bruges, når du planlægger Office 365 installation.
ms.openlocfilehash: 39b6f093c196d8b696a8d36458d2ebc18be2a5f2
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/10/2021
ms.locfileid: "63601618"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Eksterne DNS-poster for Office 365

![Domæne.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Vil du se en brugerdefineret liste over DNS-poster for din Office 365 organisation?** Du kan [finde de oplysninger, du skal bruge til Office 365 oprette DNS-poster](../admin/get-help-with-domains/information-for-dns-records.md) for dit domæne Office 365.

**Har du brug for trinvis hjælp til at tilføje disse poster hos domænets DNS-vært, f.eks. GoDaddy eller eNom?** [Find links til trinvise instruktioner til mange populære DNS-værter](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Bliver du ved med at bruge referencelisten til dine egne brugerdefinerede installationer?** Nedenstående liste skal bruges som en reference til dine brugerdefinerede Office 365 installation. Du skal vælge, hvilke poster der gælder for din organisation, og udfylde de relevante værdier.

**Gå tilbage til** [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).

Ofte er SPF- og MX-posterne de sværeste at finde ud af. Vi har opdateret vores vejledning til SPF-poster i slutningen af denne artikel. Det er vigtigt at huske, at _du kun kan have en enkelt SPF-post for dit domæne_. Du kan have flere MX-poster. det kan dog medføre problemer med levering af mail. Hvis du har en enkelt MX-post, der dirigerer mail til ét mailsystem, fjernes mange potentielle problemer.
  
Afsnittene herunder er organiseret efter tjeneste i Office 365. Hvis du vil se en brugerdefineret liste over Office 365 DNS-posterne for dit domæne, skal du logge på Office 365 og indsamle de oplysninger, du skal bruge til [at oprette Office 365 DNS-poster](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Der kræves eksterne DNS-poster til Office 365 (kernetjenester)
<a name="BKMK_ReqdCore"> </a>

Hver Office 365 skal føje to poster til deres eksterne DNS. Den første CNAME-post sikrer, at Office 365 kan få arbejdsstationer til at godkende med den relevante identitetsplatform. Den anden påkrævede post er at bevise, at du ejer dit domænenavn.
  
|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Pakke)** <br/> |Bruges af Office 365 til at dirigere godkendelse til den korrekte identitetsplatform. [Flere oplysninger](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Bemærk!** Dette CNAME gælder kun for Office 365 drevet af 21Vianet. Hvis præsentér, og din Office 365 ikke drives af 21Vianet, får brugere på dit brugerdefinerede domæne *fejlen "* brugerdefineret domæne er ikke i vores system", og de vil ikke kunne aktivere deres Office 365-licens. [Flere oplysninger](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Alias:** msoid  <br/> **Destination:** clientconfig.partner.microsoftonline-p.net.cn  <br/> |
|**TXT** <br/> **(Domænebekræftelse)** <br/> |Bruges af Office 365 til kun at bekræfte, at du ejer dit domæne. Den har ingen anden betydning.  <br/> |**Vært:** @ (eller for nogle DNS-udbydere, dit domænenavn)  <br/> **TXT-værdi:** _En tekststreng leveret af_ Office 365  <br/> Konfigurationsguiden Office 365 **domæne indeholder** de værdier, du bruger til at oprette denne post.  <br/> |


## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Der kræves eksterne DNS-poster til mail Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Mail i Office 365 kræver flere forskellige poster. De tre primære poster, som alle kunder skal bruge, er Autodiscover-, MX- og SPF-posterne.
  
- **Med Autodiscover-posten** kan klientcomputerne automatisk finde Exchange og konfigurere klienten korrekt.

- **MX-posten fortæller** andre mailsystemer, hvor de kan sende mails for dit domæne. **Bemærk!** Når du ændrer din mail til Office 365 ved at opdatere domænets MX-post, bliver ALLE mails, der sendes til dette domæne, sendt Office 365.  
Vil du blot skifte et par mailadresser til Office 365? Du kan [prøve Office 365 med et par mailadresser på dit brugerdefinerede domæne](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **TXT-posten til SPF bruges** af modtagerens mailsystemer til at validere, at du har godkendt den mail, som serveren sender. Dette er med til at forhindre mailspoofing og phishing. Se de eksterne [DNS-poster, der kræves til SPF](external-domain-name-system-records.md#BKMK_SPFrecords) i denne artikel for at få hjælp til at forstå, hvad der skal medtages i din post.

Mailkunder, der bruger Exchange sammenslutning, skal også have den ekstra CNAME- og TXT-post angivet nederst i tabellen.
  
|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |Hjælper Outlook klienter med nemt at oprette forbindelse til Exchange Online-tjenesten ved hjælp af Autodiscover-tjenesten. Autodiscover finder automatisk den korrekte Exchange Server og konfigurerer Outlook for brugere.  <br/> |**Alias:** Autodiscover  <br/> **Destination:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Sender indgående mails for dit domæne til Exchange Online tjeneste i Office 365.  <br/> **Bemærk!** Når mail er sendt til en Exchange Online, skal du fjerne de MX-poster, der peger på dit gamle system.   |**Domæne:** For eksempel contoso.com  <br/> **Målmailserver:**\<MX token\>. mail.protection.outlook.com  <br/> **Præference/prioritet:** Lavere end nogen andre MX-poster (dette sikrer, at mail leveres til Exchange Online) – f.eks. 1 eller "lav"  <br/>  Find din \<MX token\> ved at følge disse trin:  <br/>  Log på Office 365, gå til Office 365 admin \> Domains.  <br/>  Vælg Løs problemer i kolonnen Handling for dit domæne.  <br/>  I sektionen MX-poster skal du vælge Hvad skal jeg rette?  <br/>  Følg vejledningen på denne side for at opdatere din MX-post.  <br/> [Hvad er MX-prioritet?](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Hjælper dig med at forhindre andre i at bruge dit domæne til at sende spam eller anden ondsindet mail. SPF-poster (Sender Policy Framework) registrerer arbejdet ved at identificere de servere, der er godkendt til at sende mails fra dit domæne.  <br/> |[Der kræves eksterne DNS-poster til SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange sammenslutning)** <br/> |Bruges til Exchange til hybridinstallation.  <br/> |**TXT-post 1:** Eksempel: contoso.com og tilhørende brugerdefineret hash-tekst for domænebevis (f.eks. Y96nu89138789315669824)  <br/> **TXT-post 2:** Eksempel: exchangedelegation.contoso.com tilhørende brugerdefineret hash-tekst for domænebevis (f.eks. Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange sammenslutning)** <br/> |Hjælper Outlook klienter med nemt at oprette forbindelse til Exchange Online-tjenesten ved hjælp af Autodiscover-tjenesten, når din virksomhed bruger Exchange sammenslutning. Autodiscover finder automatisk den korrekte Exchange Server vært og konfigurerer Outlook for dine brugere.  <br/> |**Alias:** Eksempelvis Autodiscover.service.contoso.com  <br/> **Destination:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Der kræves eksterne DNS-poster til Skype for Business Online
<a name="BKMK_ReqdCore"> </a>

Der er specifikke trin, du skal følge, når [du bruger Office 365 URL-adresser](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) og IP-adresseintervaller for at sikre, at dit netværk er konfigureret korrekt.

> [!NOTE]
> Disse DNS-poster gælder også for Teams, især i et Teams- Skype for Business-scenarie, hvor visse sammenslutningsproblemer kunne opstå.
  
|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype for Business Online)** <br/> |Gør det Office 365 dit domæne til at dele chatfunktioner (IM) med eksterne klienter ved at aktivere SIP-sammenslutning. Læs mere om [Office 365 URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Tjeneste:** sipfederationtls  <br/> **Protokol:** TCP  <br/> **Prioritet:** 100  <br/> **Vægt:** 1  <br/> **Port:** 5061  <br/> **Destination:** sipfed.online.lync.com  <br/> **Bemærk!** Hvis en firewall eller proxyserver blokerer SRV-opslag på en ekstern DNS, skal du føje denne post til den interne DNS-post.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Bruges af Skype for Business til at koordinere strømmen af oplysninger mellem Lync-klienter.  <br/> |**Tjeneste:** sip  <br/> **Protokol:** TLS  <br/> **Prioritet:** 100  <br/> **Vægt:** 1  <br/> **Port:** 443  <br/> **Destination:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Bruges af Lync-klienten til at finde Skype for Business onlinetjenesten og logge på.  <br/> |**Alias:** sip  <br/> **Destination:** sipdir.online.lync.com  <br/> Du kan finde flere oplysninger [Office 365 URL-adresser og IP-adresseintervaller](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Bruges af Lync-mobilklienten til at finde Skype for Business onlinetjenesten og logge på.  <br/> |**Alias:** lyncdiscover  <br/> **Destination:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Der kræves eksterne DNS-poster til Office 365 enkelt Sign-On
<a name="BKMK_ReqdCore"> </a>

|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**Vært (A)** <br/> |Bruges til enkelt logon (SSO). Det giver slutpunktet for dine lokale brugere (og lokale brugere, hvis du ønsker) til at oprette forbindelse til dine PROXY'er for din AD FS-sammenslutningsserver (Active Directory Federation Services) eller virtuelle IP (VIP) til balance mellem belastningen.  <br/> |**Destination:** Eksempelvis sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Der kræves eksterne DNS-poster til SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF er udviklet til at forhindre spoofing, men der findes spoofing-teknikker, som SPF ikke kan beskytte sig mod. For at beskytte dig mod disse skal du, når du har konfigureret SPF, også konfigurere DKIM og DMARC til Office 365. For at komme i gang skal [du se Brug DKIM til at validere udgående mails, der sendes fra dit domæne Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md). Læs derefter Brug [DMARC til at validere mail i Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).
  
SPF-poster er TXT-poster, der forhindrer andre i at bruge dit domæne til at sende spam eller anden ondsindet mail. SPF-poster (Sender Policy Framework) registrerer arbejdet ved at identificere de servere, der er godkendt til at sende mails fra dit domæne.
  
Du kan kun have én SPF-post (dvs. en TXT-post, der definerer SPF) for dit domæne. Den enkelte post kan have et par forskellige inklusioner, men det samlede antal DNS-opslag, der medfører, kan ikke være mere end 10 (dette er med til at forhindre Denial of Service-angreb). Se tabellen og andre eksempler nedenfor for at få hjælp til at oprette eller opdatere de rette SPF-postværdier for dit miljø.
  
### <a name="structure-of-an-spf-record"></a>Strukturen i en SPF-post

Alle SPF-poster indeholder tre dele: Erklæringen om, at det er en SPF-post, domæner og IP-adresser, der skal sende mails, og en håndhævelsesregel. Du skal bruge alle tre i en gyldig SPF-post. Her er et eksempel på en almindelig SPF-post til Office 365, når du kun bruger Exchange Online mail:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Et mailsystem, der modtager en mail fra dit domæne, kigger på SPF-posten, og hvis den mailserver, der sendte meddelelsen, er en Office 365-server, accepteres meddelelsen. Hvis den server, der sendte meddelelsen, f.eks. er dit gamle mailsystem eller et skadeligt system på internettet, kan SPF-kontrollerne mislykkes, og meddelelsen vil ikke blive leveret. Denne kontrol hjælper med at forhindre spoofing og phishing-meddelelser.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Vælg den SPF-poststruktur, du skal bruge

For scenarier, hvor du ikke kun bruger Exchange Online-mail til Office 365 (f.eks. når du bruger mail, der også kommer fra SharePoint Online), skal du bruge følgende tabel til at bestemme, hvad der skal medtages i postens værdi.
  
> [!NOTE]
> Hvis du har et kompliceret scenarie, der f.eks. omfatter Edge-mailservere til administration af mailtrafik på tværs af din firewall, skal du konfigurere en mere detaljeret SPF-post. Lær hvordan: [Konfigurer SPF-poster i Office 365 for at forhindre spoofing](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). Du kan også få meget mere at vide om, hvordan SPF fungerer med Office 365 ved at læse [Sådan Office 365 bruger SPF (Sender Policy Framework) for at forhindre spoofing](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md).
  
| Tal|Hvis du bruger...  <br/> |Formål  <br/> |Tilføj disse omfatter  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |Alle mailsystemer (påkrævet)  <br/> |Alle SPF-poster, der starter med denne værdi  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (fælles)  <br/> |Brug med just Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |Tredjeparts mailsystem (mindre almindeligt)  <br/> ||omfatter:\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |Lokalt mailsystem (mindre almindeligt)  <br/> |Brug, hvis du bruger en Exchange Online Protection eller Exchange Online plus et andet mailsystem  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> omfatter:\<mail.contoso.com\>  <br/> Værdien i kantede parenteser (\<\>) skal være andre mailsystemer, der sender mails for dit domæne.  <br/> |
|5  <br/> |Alle mailsystemer (påkrævet)  <br/> ||-all  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Eksempel: Føje til en eksisterende SPF-post
<a name="bkmk_addtospf"> </a>

Hvis du allerede har en SPF-post, skal du tilføje eller opdatere værdier for Office 365. Lad os f.eks. sige, at din eksisterende SPF-post for contoso.com er dette:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Nu opdaterer du SPF-posten for Office 365. Du skal redigere din aktuelle post, så du har en SPF-post, der indeholder de værdier, du skal bruge. I Office 365 skal du "spf.protection.outlook.com".
  
Korrekt:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:spf.protection.outlook.com include:smtp.adatum.com -all
```

Forkert:
  
``` dns
Record 1:
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
Record 2:
Values: v=spf1 include:spf.protection.outlook.com -all
```

### <a name="more-examples-of-common-spf-values"></a>Flere eksempler på almindelige SPF-værdier
<a name="bkmk_addtospf"> </a>

Hvis du bruger den fulde Office 365-pakke og bruger MailChimp til at sende marketingmails på dine vegne, kan din SPF-post hos contoso.com se ud som følgende, som bruger række 1, 3 og 5 i ovenstående tabel. Husk, at række 1 og 5 er påkrævede.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Hvis du har en Exchange-hybridkonfiguration, hvor mail sendes fra både Office 365 og dit lokale mailsystem, kan din SPF-post hos contoso.com se sådan ud:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

Dette er nogle almindelige eksempler, der kan hjælpe dig med at tilpasse din eksisterende SPF-post, når du føjer dit domæne Office 365 til mail. Hvis du har et kompliceret scenarie, der f.eks. omfatter Edge-mailservere til administration af mailtrafik på tværs af din firewall, skal du konfigurere en mere detaljeret SPF-post. Lær hvordan: [Konfigurer SPF-poster i Office 365 for at forhindre spoofing](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365edns]()
