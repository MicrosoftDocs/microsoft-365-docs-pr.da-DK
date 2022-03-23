---
title: Grundlæggende om DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
- GEA150
- BSA160
ms.assetid: 854b6b2b-0255-4089-8019-b765cff70377
ROBOTS: NOINDEX
description: Domænenavnssystemet knytter computerværtsnavne til IP-adresser og forstå DNS og grundlæggende oplysninger om domæneregistrator kan hjælpe dig med at administrere domæner.
ms.openlocfilehash: efe5c8b4a043c3a8f4bdf49da85201ab0cbae7c9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590775"
---
# <a name="dns-basics"></a>Grundlæggende om DNS

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
::: moniker range="o365-worldwide"

Domænenavne som f.contoso.com administreres ved hjælp af et verdensomspændende system af domæneregistratorer og databaser. DNS (Domain Name System) indeholder en tilknytning mellem læsbare computerværtsnavne og de IP-adresser, der bruges af netværksudstyret. En forståelse af DNS og grundlæggende viden om domæneregistratorer kan hjælpe dig med at administrere domæner.

## <a name="watch-domains--dns-an-overview"></a>Se: Domæner & DNS: En oversigt
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/c005f2a4-90ad-46fe-b1ab-90f41f2a9d53?autoplay=false]
  
::: moniker-end

::: moniker range="o365-21vianet"

Domænenavne som f.contoso.com administreres ved hjælp af et verdensomspændende system af domæneregistratorer og databaser. DNS (Domain Name System) indeholder en tilknytning mellem læsbare computerværtsnavne og de IP-adresser, der bruges af netværksudstyret. En forståelse af DNS og grundlæggende viden om domæneregistratorer kan hjælpe administratorer med at administrere domæner.
  
::: moniker-end

## <a name="what-are-domain-names"></a>Hvad er domænenavne?

Domænenavne bruges i URL-adresser og mailadresser, og de har forskellige niveauer. Eksempelvis er mail.contoso.com et domænenavn med følgende tre niveauer:
  
- **.com** er det øverste domæneniveau 
    
- **contoso** er det andet domæneniveau 
    
- **mail** er det tredje domæneniveau 
    
Hvorfor bruge et tredje domæneniveau? Det kan være en god ide at have forskellige domænenavne til marketing eller en blog. For eksempel blog.contoso.com. Du tilføjer typisk et domæne på andet niveau, f.eks. contoso.com, til brug sammen med Microsoft, men du kan også bruge domæner på tredje niveau, hvis du vil.
  
Få mere at vide om, hvad du kan gøre med domæner for hver type tilbud i [Microsoft 365 og Office 365 platformstjenestebeskrivelse](/office365/servicedescriptions/office-365-platform-service-description/domains).
  
## <a name="understand-dns-record-types"></a>Forstå DNS-posttyper

DNS-poster, der er gemt på en DNS-vært for dit domæne, bruges til at dirigere trafik til dit domæne. I følgende tabel beskrives ofte benyttede DNS-poster, og hvordan de bruges.
  
|**NS-post (navneserver)**|**Identificerer de navneservere, der er de "autoritative navneservere" for et domæne. Når du ændrer navneserverne for dit domæne, ændrer du, hvor dine DNS-poster administreres, og hvor DNS-systemet søger efter oplysninger om mailservere osv. Microsoft har sine egne navneservere, eller du kan vælge at fortsætte med at bruge de navneservere, der allerede er konfigureret med dit domæne.**|
|:-----|:-----|
|En post (adressepost)  <br/> |Knytter et domænenavn til en IP-adresse.  <br/> |
|CNAME-post (alias eller ved navn)  <br/> |Omdirigerer et domæne til et andet i DNS-systemet. Når en navneserver søger efter et domæne og finder ud af, at den har en CNAME-post, erstatter serveren det første domænenavn med CNAME og søger derefter efter det nye navn.  <br/> |
|MX-post (mailudveksling)  <br/> |Peger på det sted, hvor din mail skal sendes til. Den har også et prioritetsfelt, så du kan sende mails til forskellige servere i prioriteret rækkefølge.  <br/> |
|SPF-post (Sender Policy Framework)  <br/> |En TXT-post, der hjælper med at forhindre mailspoofing og phishing.  <br/> |
|SRV-post (tjeneste)  <br/> |Bruges af Skype for Business Online og Exchange Online til at koordinere strømmen af oplysninger mellem Microsoft-tjenester. SRV-posterne er f.eks. nødvendige for at kunne se tilstedeværelse i Outlook Web App og for at kunne bruge Skype for Business Online, Skype eller andre chatværktøjer med personer i andre virksomheder.  <br/> |
|TTL (tid til live)  <br/> |Den tid, som en navneserver bevarer en DNS-post, før serveren søger efter en opdateret version.  <br/> |
   
## <a name="how-does-dns-work"></a>Hvordan fungerer DNS?

En del af konfigurationen af dit domæne med en skytjeneste som Microsoft 365 omfatter ændring eller tilføjelse af [DNS-poster](dns-basics.md) for domænet. Disse ændringer er nødvendige på grund af, hvordan internettet fungerer med DNS, Domain Name System og domænenavne for at vide, hvor du skal sende eller finde ting, f.eks. mail og websteder. 
  
Internettet er konfigureret til at bruge DNS eller Domain Name System, hvilket giver os mulighed for at bruge velkendte navne, f.eks. contoso.com, til at finde bestemte internetplaceringer, der faktisk er forbundet med numre, der er svære at huske (IP-adresser (Internet Protocol). IP-adresser ligner 70.42.241.42, så du kan se, at det er meget nemmere at bruge et domænenavn til at identificere placeringer som f.eks. mailværter og websteder.
  
Så det er det korte svar: DNS-poster fortæller internettet, hvor mail (f.eks. joe@contoso.com) skal sendes hen, eller websteder (f.eks. www.contoso.com), der bruger dit domænenavn. Når du sender de rigtige oplysninger til de rigtige DNS-poster for dit domæne, routes DNS-systemet alt korrekt, så dine mails f.eks. ankommer i Microsoft 365 i stedet for et andet sted.
  
Et domænes DNS-poster kan også være nyttige på andre måder. Eksempelvis kontrollerer Exchange EN DNS-post, der gør det muligt Outlook konfigurere en forbindelse til højre Exchange serveren.
  
### <a name="dns-records-help-the-internet-send-email-to-the-right-place"></a>DNS-poster hjælper internettet med at sende mails til det rigtige sted

Som nævnt ovenfor dirigerer DNS dybest set trafikken rundt på internettet ved at knytte læsevenlige domænenavne til disse IP-adresser, der er svære at huske. En DNS-post, der kaldes MX-posten, er specifikt til at sende mail til den rigtige vært.
  
DNS-poster er ligesom en database med oplysninger om dit domæne. Posterne og deres værdier opbevares i en zonefil, som indeholder en liste over hver post for dit domæne, og hvad deres værdi er. Domæneregistratorer og andre DNS-firmaer har en brugergrænseflade på deres websteder, så du kan redigere posterne i domænets zonefil. Det er også her, du kan opdatere MX-posten for dit domæne for at sende mails til Microsoft 365.
  
 *Når du ændrer din mail til Microsoft 365 ved at opdatere domænets MX-post i næste trin, bliver ALLE mails, der sendes til dette domæne, sendt Microsoft 365.*  Hvis andre bruger dit domæne til mail, skal du konfigurere Microsoft 365 postkasser for hver af disse personer. 
  
Lyder det kompliceret? Det kan det være, men vi gennemgår hvert trin i konfigurationen af Microsoft-domænet.
  
### <a name="dns-tells-the-internet-where-to-look-for-websites-too"></a>DNS fortæller internettet, hvor der skal søges efter websteder

Når du skriver en webadresse, f.eks. www.contoso.com, kontrollerer internettet først med en af DNS-serverne efter noget, der kaldes en navneserverpost (NS) for (i dette tilfælde) contoso.com. NS-posten fortæller internettet, hvor den skal lede efter zonefilen, der har alle de andre DNS-postværdier for det domæne. Der er mange DNS-servere, der alle er forbundet til hinanden. Serverne arbejder sammen for at holde styr på alle registrerede domænenavne, som skal være entydige, og hvor domænets zonefiler er.
  
::: moniker range="o365-worldwide"

Lad os sige, at NS-posten for contoso.com siger "godaddy.com." Nu ved internettet, at GoDaddy.com er det sted, hvor man skal lede efter zonefilen med alle de andre DNS-poster for contoso.com. Disse DNS-poster omfatter den MX-post, hvor der står, hvor mails til contoso.com og andre poster skal sendes hen. Hvis MX-posten har en værdi, hvor der står (men teknisk set) "send mails til Microsoft 365", er det stedet, hvor alle mails, der sendes til en contoso.com-mailadresse (f.eks. joe@contoso.com), sendes. Så længe der er en postkasse kaldet "joe" på den pågældende placering, vil mailen blive leveret.

::: moniker-end

::: moniker range="o365-21vianet"

Lad os sige, at NS-posten for contoso.com siger "hichina.com." Nu ved internettet, at hichina.com er det sted, hvor man skal lede efter zonefilen med alle de andre DNS-poster contoso.com. Disse DNS-poster omfatter den MX-post, hvor der står, hvor mails til contoso.com og andre poster skal sendes hen. Hvis MX-posten har en værdi, hvor der står (men teknisk set) "send mails til Microsoft 365", er det stedet, hvor alle mails, der sendes til en contoso.com-mailadresse (f.eks. joe@contoso.com), sendes. Så længe der er en postkasse kaldet "joe" på den pågældende placering, vil mailen blive leveret.

::: moniker-end

De faktiske værdier, du skal angive for at få alt dette til at fungere sammen med Microsoft 365, vises for dig, når du konfigurerer dit domæne, i trinnene til domænekonfiguration. Hvis du udfører konfigurationen manuelt, skal du kopiere og indsætte værdierne i de korrekte DNS-poster (MX-post, CNAME-poster osv.) hos din DNS-vært, som kan være din domæneregistrator, men det er ikke nødvendigt.
  
::: moniker range="o365-worldwide"

Hvorfor kan domænets zonefil være et andet sted end hos din domæneregistrator? Du kan registrere dit domænenavn hos en domæneregistrator som GoDaddy, men dine DNS-poster kan være administreret et andet sted, hos en separat DNS-vært eller et webhostingfirma. NS-posterne for dit domæne gemmer disse oplysninger, så alle DNS-serverne ved, hvor de skal kigge.

::: moniker-end

::: moniker range="o365-21vianet"

Hvorfor kan domænets zonefil være et andet sted end hos din domæneregistrator? Du kan registrere dit domænenavn hos en domæneregistrator som HiChina, men dine DNS-poster kan være administreret et andet sted, hos en separat DNS-vært eller et webhostingfirma. NS-posterne for dit domæne gemmer disse oplysninger, så alle DNS-serverne ved, hvor de skal kigge.

::: moniker-end

::: moniker range="o365-worldwide"
## <a name="why-add-a-domain-in-microsoft-365"></a>Hvorfor tilføje et domæne Microsoft 365?


Hvis du føjer et brugerdefineret domæne, fourthcoffee.com til Microsoft 365, kan du bruge en kortere, mere velkendt mailadresse og bruger-id til tjenesten. Du får et [domæne til at bruge,](../setup/domains-faq.yml) når du tilmelder dig en Microsoft 365 konto, men det indeholder "onmicrosoft.com." Mange foretrækker at tilføje deres organisations- eller virksomhedsdomæne, hvis de planlægger at bruge Microsoft 365 til mail. 
  
> [!NOTE]
> Hvis du blot ønsker at downloade og bruge Microsoft-apps, f.eks. Outlook eller Word, behøver du ikke at tilføje et domæne: [Installer Office på din pc eller Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658). 
  
Du kan bruge dit domænenavn Microsoft 365 din mail, dit offentlige websted og din chatadresse.
  
- **Mail:** Med dit domænenavn kan du tilpasse din mail, så du kan bruge en kortere adresse, der er nemmere at huske end den oprindelige [onmicrosoft.com](../setup/domains-faq.yml) mailadresse, der følger med din konto. Så i stedet joe@contoso.onmicrosoft.com mailadressen (som også er den arbejdskonto, du bruger til at logge på Microsoft 365) være joe@contoso.com. 
    
- **Websted:** Hvis du har et Microsoft 365-abonnement, der indeholder et offentligt SharePoint-onlinewebsted (kan ikke længere købes), leveres dit offentlige websted med en oprindelig adresse som denne: contoso-public.sharepoint.com. Hvis du konfigurerer dit websted til din virksomhed, kan du bruge et brugerdefineret domænenavn til at omdøbe webadressen til noget i www.contoso.com. 
    
- **Chat:** Din Skype for Business Online-adresse kan også tilpasses til at bruge dit domænenavn, så personer i organisationen kan oprette forbindelse til hinanden på Skype for Business Online ved hjælp af en kortere adresse, der er nemmere at huske (f.eks. joe@contoso.com). 
    
::: moniker-end

## <a name="the-dns-records-required-for-microsoft-365"></a>De DNS-poster, der kræves til Microsoft 365

Der kræves en række DNS-poster, for Microsoft 365 du kan arbejde med dit domæne. Ud over at konfigurere dit domænes MX-post, så mail sendes til Microsoft 365, er der poster, der kan hjælpe med opgaver som f.eks. at sikre, at Outlook automatisk kan oprette forbindelse til den rigtige Exchange-server, konfigurere chat og hjælpe med at forhindre spammail.
  
Du kan [finde en liste over værdier til](information-for-dns-records.md) at konfigurere dit domæne. De er inkluderet direkte i <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Microsoft 365 Administration</a>. 
  
Eller hvis du planlægger en installation, kan du gennemse en liste over alle de DNS-poster, der kræves til Microsoft 365, hvad deres funktion er, og eksempelværdier. Se eksterne [DNS-poster for Microsoft 365](../../enterprise/external-domain-name-system-records.md).
  
## <a name="next-steps"></a>Næste trin

Se et af følgende: 
  
- Er du ikke sikker på, hvor dit domæne er registreret? [Få hjælp til at finde din domæneregistrator.](find-your-domain-registrar.md)
- Find ud [af, hvorfor du skal udføre trinnene i guiden,](../setup/add-domain.md) før du kan bruge dit domæne med Microsoft 365.

## <a name="related-content"></a>Relateret indhold

[Ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) (artikel)\
[Find og løs problemer efter at have tilføjet dit domæne eller DNS-poster](find-and-fix-issues.md) (artikel)\
[Administrer domæner](/admin) (linkside)