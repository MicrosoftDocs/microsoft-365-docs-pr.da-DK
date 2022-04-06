---
title: Eksterne domænenavnesystemposter for Office 365
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
description: En referenceliste over eksterne domænenavnesystemposter, der skal bruges til planlægning af en Office 365 udrulning.
ms.openlocfilehash: d2c73094da0547fbc02a4520d4361941b829619c
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651339"
---
# <a name="external-domain-name-system-records-for-office-365"></a>Eksterne domænenavnesystemposter for Office 365

![Domæne.](../media/e05b1c78-1df0-4200-ba40-6e26b7ead68f.png)

**Vil du se en brugerdefineret liste over DNS-poster for din Office 365 organisation?** Du kan [finde de oplysninger, du skal bruge for at oprette Office 365 DNS-poster](../admin/get-help-with-domains/information-for-dns-records.md) for dit domæne, i Office 365.

**Har du brug for trinvis hjælp til at tilføje disse poster på dit domænes DNS-vært, f.eks. GoDaddy eller eNom?** [Find links til trinvise instruktioner for mange populære DNS-værter](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Bliver du ved med at bruge referencelisten til din egen brugerdefinerede udrulning?** Nedenstående liste skal bruges som reference til din brugerdefinerede Office 365 udrulning. Du skal vælge, hvilke poster der skal gælde for din organisation, og udfylde de relevante værdier.

**Gå tilbage til** [Netværksplanlægning og justering af ydeevne for Office 365](./network-planning-and-performance.md).

Ofte er det svært at finde ud af, hvilke SPF- og MX-poster der er. Vi har opdateret vores vejledning til SPF-poster i slutningen af denne artikel. Det vigtigste at huske er, at _du kun kan have en enkelt SPF-post for dit domæne_. Du kan have flere MX-poster. det kan dog medføre problemer med levering af post. Hvis du har en enkelt MX-post, der sender mail til ét mailsystem, fjernes mange potentielle problemer.
  
Afsnittene nedenfor er organiseret efter tjeneste i Office 365. Hvis du vil se en brugerdefineret liste over Office 365 DNS-poster for dit domæne, skal du logge på Office 365 og [indsamle de oplysninger, du skal bruge for at oprette Office 365 DNS-poster](https://support.office.com/article/77f90d4a-dc7f-4f09-8972-c1b03ea85a67).
  
## <a name="external-dns-records-required-for-office-365-core-services"></a>Eksterne DNS-poster kræves til Office 365 (kernetjenester)
<a name="BKMK_ReqdCore"> </a>

TXT-posten er nødvendig for at bevise, at du ejer domænet og er påkrævet for alle kunder.

CNAME-posten er kun påkrævet for kunder, der bruger [Office 365, der drives af 21Vianet](/microsoft-365/admin/services-in-china/services-in-china). Det sikrer, at Office 365 kan dirigere arbejdsstationer til godkendelse med den relevante identitetsplatform. 


  
|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |**Gælder for**|
|----------|-----------|------------|------------|
|**TXT** <br/> **(Domænebekræftelse)** <br/> |Bruges af Office 365 til kun at bekræfte, at du ejer dit domæne. Det påvirker ikke noget andet.  <br/> |**Vært:** @ (eller for nogle DNS-hostingudbydere dit domænenavn)  <br/> **TXT-værdi:** _En tekststreng, der leveres af_ Office 365  <br/> **Guiden Office 365 domæneinstallation** indeholder de værdier, du bruger til at oprette denne post.  <br/> |Alle kunder|
|**CNAME** <br/> **(Suite)** <br/> |Bruges af Office 365 til at dirigere godkendelse til den korrekte identitetsplatform. [Flere oplysninger](../admin/services-in-china/purpose-of-cname.md?viewFallbackFrom=o365-worldwide) <br/> **Bemærk**, at dette CNAME kun gælder for Office 365, der drives af 21Vianet. Hvis din Office 365 ikke administreres af 21Vianet, får brugerne på dit brugerdefinerede domæne en "*brugerdefineret domæne* findes ikke i vores system" og kan ikke aktivere deres Office 365 licens. [Flere oplysninger](/office365/servicedescriptions/office-365-platform-service-description/office-365-operated-by-21vianet) |**Alias:** msoid  <br/> **Mål:** clientconfig.partner.microsoftonline-p.net.cn  <br/> | 21 KunVianet-kunder|



## <a name="external-dns-records-required-for-email-in-office-365-exchange-online"></a>Der kræves eksterne DNS-poster til mail i Office 365 (Exchange Online)
<a name="BKMK_ReqdCore"> </a>

Mail i Office 365 kræver flere forskellige poster. De tre primære poster, som alle kunder skal bruge, er posterne Autodiscover, MX og SPF.
  
- **Autodiscover-posten** gør det muligt for klientcomputere automatisk at finde Exchange og konfigurere klienten korrekt.

- **MX-posten** fortæller andre mailsystemer, hvor du kan sende mail til dit domæne. **Bemærk:** Når du ændrer din mail til Office 365 ved at opdatere dit domænes MX-post, begynder ALLE mails, der sendes til domænet, at komme til Office 365.  
Vil du blot skifte et par mailadresser til Office 365? Du kan [styre Office 365 med et par mailadresser på dit brugerdefinerede domæne](https://support.office.com/article/39cee536-6a03-40cf-b9c1-f301bb6001d7).

- **TXT-posten til SPF** bruges af modtagermailsystemer til at validere, at den server, der sender din mail, er en, du godkender. Dette hjælper med at forhindre problemer som f.eks. mailpoofing og phishing. Se de [eksterne DNS-poster, der kræves til SPF](external-domain-name-system-records.md#BKMK_SPFrecords) i denne artikel, for at hjælpe dig med at forstå, hvad du skal inkludere i din post.

Mailkunder, der bruger Exchange Federation, skal også bruge den ekstra CNAME- og TXT-post, der er angivet nederst i tabellen.
  
|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**CNAME** <br/> **(Exchange Online)** <br/> |Hjælper Outlook klienter med nemt at oprette forbindelse til Exchange Online-tjenesten ved hjælp af tjenesten Autodiscover. Autodiscover finder automatisk den korrekte Exchange Server vært og konfigurerer Outlook for brugere.  <br/> |**Alias:** Autodiscover  <br/> **Mål:** autodiscover.outlook.com  <br/> |
|**MX** <br/> **(Exchange Online)** <br/> |Sender indgående post til dit domæne til Exchange Online-tjenesten i Office 365.  <br/> **Bemærk:** Når mailen overføres til Exchange Online, skal du fjerne de MX-poster, der peger på dit gamle system.   |**Domæne:** F.eks. contoso.com  <br/> **Destinationsmailserver:**\<MX token\>. mail.protection.outlook.com  <br/> **TTL-værdi (Time To Live):** 3600 <br/> **Præference/prioritet:** Lavere end nogen anden MX-post (dette sikrer, at post leveres til Exchange Online) - f.eks. 1 eller "lav"  <br/>  Find dit \<MX token\> ved at følge disse trin:  <br/>  Log på Office 365, gå til Office 365 administratordomæner\>.  <br/>  I kolonnen Handling for dit domæne skal du vælge Løs problemer.  <br/>  I afsnittet MX-poster skal du vælge Hvad skal jeg rette?  <br/>  Følg vejledningen på denne side for at opdatere din MX-post.  <br/> [Hvad er MX-prioritet?](../admin/setup/domains-faq.yml) <br/> |
|**SPF (TXT)** <br/> **(Exchange Online)**  <br/> |Hjælper med at forhindre andre i at bruge dit domæne til at sende spam eller andre skadelige mails. SPF-poster (Sender Policy Framework) fungerer ved at identificere de servere, der er godkendt til at sende mail fra dit domæne.  <br/> |[Der kræves eksterne DNS-poster til SPF](external-domain-name-system-records.md#BKMK_SPFrecords) <br/> |
|**TXT** <br/> **(Exchange sammenslutning)** <br/> |Bruges til Exchange-samling til hybridinstallation.  <br/> |**TXT-post 1:** Det kan f.eks. være contoso.com og tilknyttet brugerdefineret genereret hash-tekst, der er bevis for domænet (f.eks. Y96nu89138789315669824)  <br/> **TXT-post 2:** Det kan f.eks. være exchangedelegation.contoso.com og tilknyttet brugerdefineret genereret hash-tekst, der er bevis for domænet (f.eks. Y3259071352452626169)  <br/> |
|**CNAME** <br/> **(Exchange sammenslutning)** <br/> |Hjælper Outlook klienter med nemt at oprette forbindelse til Exchange Online-tjenesten ved hjælp af autodiscover-tjenesten, når din virksomhed bruger Exchange sammenslutning. Automatisk søgning finder automatisk den korrekte Exchange Server vært og konfigurerer Outlook for dine brugere.  <br/> |**Alias:** F.eks. Autodiscover.service.contoso.com  <br/> **Mål:** autodiscover.outlook.com  <br/> |


## <a name="external-dns-records-required-for-skype-for-business-online"></a>Der kræves eksterne DNS-poster til Skype for Business Online
<a name="BKMK_ReqdCore"> </a>

Der er specifikke trin, du skal udføre, når du bruger [Office 365 URL-adresser og IP-adresseområder](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO) for at sikre, at netværket er konfigureret korrekt.

> [!NOTE]
> Disse DNS-poster gælder også for Teams, især i et hybrid-Teams- og Skype for Business-scenarie, hvor der kan opstå visse problemer med sammenslutning.
  
|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**SRV** <br/> **(Skype for Business Online)** <br/> |Gør det muligt for dit Office 365 domæne at dele chatfunktioner med eksterne klienter ved at aktivere SIP-sammenslutning. Læs mere om [Office 365 URL-adresser og IP-adresseområder](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |**Service:** sipfederationtls  <br/> **Protokollen:** TCP  <br/> **Prioritet:** 100  <br/> **Vægt:** 1  <br/> **Port:** 5061  <br/> **Mål:** sipfed.online.lync.com  <br/> **Bemærk:** Hvis firewallen eller proxyserveren blokerer SRV-opslag på en ekstern DNS, skal du føje denne post til den interne DNS-post.   |
|**SRV** <br/> **(Skype for Business Online)** <br/> |Bruges af Skype for Business til at koordinere informationsflowet mellem Lync-klienter.  <br/> |**Service:** sip  <br/> **Protokollen:** TLS  <br/> **Prioritet:** 100  <br/> **Vægt:** 1  <br/> **Port:** 443  <br/> **Mål:** sipdir.online.lync.com  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Bruges af Lync-klienten til at hjælpe med at finde Skype for Business Online-tjenesten og logge på.  <br/> |**Alias:** sip  <br/> **Mål:** sipdir.online.lync.com  <br/> Du kan finde flere oplysninger [under Office 365 URL-adresser og IP-adresseområder](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_LYO).  <br/> |
|**CNAME** <br/> **(Skype for Business Online)** <br/> |Bruges af Lync-mobilklienten til at hjælpe med at finde Skype for Business Online-tjenesten og logge på.  <br/> |**Alias:** lyncdiscover  <br/> **Mål:** webdir.online.lync.com  <br/> |

## <a name="external-dns-records-required-for-office-365-single-sign-on"></a>Der kræves eksterne DNS-poster til Office 365 Enkelt Sign-On
<a name="BKMK_ReqdCore"> </a>

|**DNS-post** <br/> |**Formål** <br/> |**Værdi, der skal bruges** <br/> |
|----------|-----------|------------|
|**Vært (A)** <br/> |Bruges til enkeltlogon (SSO). Det giver slutpunktet for dine brugere uden for det lokale miljø (og brugere i det lokale miljø, hvis du vil) til at oprette forbindelse til dine serverproxyer til Active Directory Federation Services (AD FS) eller belastningsafbalancerede virtuelle IP (VIP).  <br/> |**Mål:** F.eks. sts.contoso.com  <br/> |

## <a name="external-dns-records-required-for-spf"></a>Der kræves eksterne DNS-poster til SPF
<a name="BKMK_SPFrecords"> </a>

> [!IMPORTANT]
> SPF er designet til at hjælpe med at forhindre spoofing, men der er spoofing-teknikker, som SPF ikke kan beskytte mod. Når du har konfigureret SPF, skal du for at beskytte mod disse også konfigurere DKIM og DMARC til Office 365. For at komme i gang skal du se [Brug DKIM til at validere udgående mails, der er sendt fra dit domæne i Office 365](../security/office-365-security/use-dkim-to-validate-outbound-email.md). Derefter skal du se [Brug DMARC til at validere mail i Office 365](../security/office-365-security/use-dmarc-to-validate-email.md).
  
SPF-poster er TXT-poster, der hjælper med at forhindre andre i at bruge dit domæne til at sende spam eller andre skadelige mails. SPF-poster (Sender Policy Framework) fungerer ved at identificere de servere, der er godkendt til at sende mail fra dit domæne.
  
Du kan kun have én SPF-post (dvs. en TXT-post, der definerer SPF) for dit domæne. Denne enkelt post kan have nogle forskellige medtagelser, men det samlede antal DNS-opslag, der resulterer i, kan ikke være mere end 10 (dette hjælper med at forhindre denial of service-angreb). Se tabellen og andre eksempler nedenfor for at hjælpe dig med at oprette eller opdatere de rigtige SPF-postværdier for dit miljø.
  
### <a name="structure-of-an-spf-record"></a>Strukturen af en SPF-post

Alle SPF-poster indeholder tre dele: erklæringen om, at det er en SPF-post, domæner og IP-adresser, der skal sende mail, og en håndhævelsesregel. Du skal bruge alle tre i en gyldig SPF-post. Her er et eksempel på en almindelig SPF-post til Office 365, når du kun bruger Exchange Online mail:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com -all
```

Et mailsystem, der modtager en mail fra dit domæne, kigger på SPF-posten, og hvis den mailserver, der sendte meddelelsen, var en Office 365 server, accepteres meddelelsen. Hvis den server, der sendte meddelelsen, f.eks. var dit gamle postsystem eller et skadeligt system på internettet, kan SPF-kontrollen mislykkes, og meddelelsen ville ikke blive leveret. Kontroller som denne hjælper med at forhindre spoofing og phishing-meddelelser.
  
### <a name="choose-the-spf-record-structure-you-need"></a>Vælg den SPF-poststruktur, du har brug for

I scenarier, hvor du ikke kun bruger Exchange Online mail til Office 365 (f.eks. når du bruger mail, der også stammer fra SharePoint Online), skal du bruge følgende tabel til at bestemme, hvad der skal medtages i postens værdi.
  
> [!NOTE]
> Hvis du har et kompliceret scenarie, der f.eks. inkluderer edge-mailservere til administration af mailtrafik på tværs af din firewall, har du en mere detaljeret SPF-post, der skal konfigureres. Få mere at vide om, hvordan du [konfigurerer SPF-poster i Office 365 for at forhindre spoofing](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md). Du kan også få meget mere at vide om, hvordan SPF fungerer sammen med Office 365, ved [at læse Sådan bruger Office 365 SPF (Sender Policy Framework) til at forhindre spoofing](../security/office-365-security/how-office-365-uses-spf-to-prevent-spoofing.md).
  
| Antallet|Hvis du bruger...  <br/> |Formål  <br/> |Tilføj disse "include"-filer  <br/> |
|:-----|:-----|:-----|:-----|
|1  <br/> |Alle mailsystemer (påkrævet)  <br/> |Alle SPF-poster starter med denne værdi  <br/> |v=spf1  <br/> |
|2  <br/> |Exchange Online (fælles)  <br/> |Bruges kun med Exchange Online  <br/> |include:spf.protection.outlook.com  <br/> |
|3  <br/> |Mailsystem fra tredjepart (mindre almindeligt)  <br/> ||Omfatter:\<email system like mail.contoso.com\>  <br/> |
|4  <br/> |Mailsystem i det lokale miljø (mindre almindeligt)  <br/> |Bruges, hvis du bruger Exchange Online Protection eller Exchange Online plus et andet mailsystem  <br/> |ip4:\<0.0.0.0\>  <br/> ip6:\< : : \>  <br/> Omfatter:\<mail.contoso.com\>  <br/> Værdien i parenteser (\<\>) skal være andre mailsystemer, der sender mail til dit domæne.  <br/> |
|5  <br/> |Alle mailsystemer (påkrævet)  <br/> ||- alle  <br/> |

### <a name="example-adding-to-an-existing-spf-record"></a>Eksempel: Tilføjelse til en eksisterende SPF-post
<a name="bkmk_addtospf"> </a>

Hvis du allerede har en SPF-post, skal du tilføje eller opdatere værdier for Office 365. Lad os f.eks. sige, at din eksisterende SPF-post for contoso.com er følgende:
  
``` dns
TXT Name @
Values: v=spf1 ip4:60.200.100.30 include:smtp.adatum.com -all
```

Nu opdaterer du din SPF-post for Office 365. Du skal redigere den aktuelle post, så du har en SPF-post, der indeholder de værdier, du har brug for. "spf.protection.outlook.com" for Office 365.
  
Korrekte:
  
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

Hvis du bruger hele Office 365-pakken og bruger MailChimp til at sende marketingmails på dine vegne, kan din SPF-post på contoso.com se ud på følgende måde, som bruger række 1, 3 og 5 fra tabellen ovenfor. Husk, at række 1 og 5 er påkrævet.
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:servers.mcsv.net -all
```

Hvis du har en Exchange Hybrid-konfiguration, hvor mail sendes fra både Office 365 og dit lokale mailsystem, kan din SPF-post på contoso.com se sådan ud:
  
``` dns
TXT Name @
Values: v=spf1 include:spf.protection.outlook.com include:mail.contoso.com -all
```

Dette er nogle almindelige eksempler, der kan hjælpe dig med at tilpasse din eksisterende SPF-post, når du føjer dit domæne til Office 365 til mail. Hvis du har et kompliceret scenarie, der f.eks. inkluderer edge-mailservere til administration af mailtrafik på tværs af din firewall, har du en mere detaljeret SPF-post, der skal konfigureres. Få mere at vide om, hvordan du [konfigurerer SPF-poster i Office 365 for at forhindre spoofing](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  
Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365edns]()
