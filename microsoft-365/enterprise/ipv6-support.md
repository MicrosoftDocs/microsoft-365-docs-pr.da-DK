---
title: IPv6-understøttelse i Microsoft 365-tjenester
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'Resumé: Beskriver IPv6-understøttelse i Microsoft 365 komponenter og i Microsoft 365 offentlige tilbud.'
ms.openlocfilehash: 6cd53b71c6e15346d4940c539eea4aff0e5a613e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096474"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>IPv6-understøttelse i Microsoft 365-tjenester

Microsoft 365 understøtter både IPv6 og IPv4, men ikke alle Microsoft 365 funktioner er fuldt aktiveret med IPv6. Det betyder, at du skal bruge både IPv4 og IPv6 til at oprette forbindelse til Microsoft 365. Hvis du filtrerer din udgående trafik til Microsoft 365, kan du finde den komplette liste over IPv6-adresser, der understøttes af Microsoft 365, i artiklen [Microsoft 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md). Når netværket er konfigureret, og de relevante IPv6-adresser er tilladt, kan du downloade [Microsoft 365 IPv6-testplan](https://go.microsoft.com/fwlink/?LinkId=293447) fra Microsoft Download Center.

> [!NOTE]
> Det er en prioritet for Microsoft at give kunderne mulighed for at opleve Microsoft 365 SaaS-tjenester fra enhver placering og enhver enhed. Dette omfatter, at kunderne kan oprette forbindelse til og forbruge Microsoft 365 fra klienter og informationssystemer, der kun er IPv6-aktiverede, og IPv6. Det omfatter også at gøre det muligt for offentlige kunder at opfylde IPv6-forpligtelser på deres netværk, samtidig med at de fortsætter med at forbruge Microsoft 365 produktivitetsscenarier uden afbrydelser.  
> Denne artikel indeholder en liste over Microsoft 365 SaaS-tjenester, der tillader direkte IPv6-forbindelse i dag. Omfanget af tjenester, der tillader direkte IPv6-forbindelse, forventes fortsat at blive udvidet. Microsoft 365 tjenester, der ikke udtrykkeligt er nævnt til direkte IPv6-support, for at inkludere Azure Active Directory (AAD) godkendelsestjenester, bør anses for at kræve, at DNS64/NAT64 kun skal have forbindelse til fra klienter og miljøer i IPv6.  Dette er i overensstemmelse med den hensigt, der i øjeblikket er beskrevet i den eksisterende NIST USGv6-dokumentation: Transition Mechanism Capability Requirements in [NIST Special Publication 500-267A Revision 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 er acceptable teknologier at anvende.
> - NAT64-understøttelse af overgangsmekanismen NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stateful NAT64: Netværksadresse og protokoloversættelse fra IPv6-klienter til IPv4-servere
> - DNS64-understøttelse af overgangsmekanismen DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: DNS-udvidelser til netværksadresseoversættelse fra IPv6-klienter til IPv4-server

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>IPv6-understøttelse i Microsoft 365-abonnementstjeneste

### <a name="exchange-online-and-ipv6"></a>Exchange Online og IPv6

Hvis det program, du bruger til at oprette forbindelse til Exchange Online understøtter IPv6, bruger det som standard IPv6 på både kablede og trådløse netværk. Hvis du vil styre kommunikationen til Exchange Online, skal du bruge IP-adresseintervaller i [Microsoft 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online og IPv6

 **Microsoft 365 Government G1/G3/G4/K1** Hvis det program, du bruger til at oprette forbindelse til SharePoint Online, understøtter IPv6, vil det som standard forsøge at bruge IPv6.
  
 **Offentlig cloud med flere lejere** Microsoft aktiverer SharePoint Online IPv6 på din anmodning. Du skal angive de CIDR-noterede IP-adresser for din organisations DNS-infrastruktur. Vær opmærksom på, at denne DNS-infrastruktur ikke kan deles af andre organisationer, for at IPv6 kan aktiveres for din lejer. Når IPv6 er aktiveret, bruger programmet som standard IPv6, hvis det program, du bruger til at oprette forbindelse til SharePoint Online, understøtter IPv6.
  
Hvis det program, du bruger til at oprette forbindelse til SharePoint Online, understøtter IPv6, bruger det som standard IPv6 på både kablede og trådløse netværk. Hvis du vil styre kommunikationen til SharePoint Online, skal du bruge IP-adresseintervaller i [Microsoft 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business og IPv6

Vær opmærksom på, at IPv6 ikke understøttes i Skype for Business og ikke længere kan aktiveres.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, SIP Gateway og IPV6

Microsoft Teams Direct Routing og SIP Gateway understøtter kun IPv4. Tjenesten Microsoft Teams og klienten understøtter både IPv4 og IPv6. Hvis du vil styre kommunikationen til Microsoft Teams, skal du bruge IP-adresseintervaller i [Microsoft 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection og IPv6

Exchange Online Protection (EOP) understøtter IPv6, hvis overførslen sker via Transport Layer Security Protocol. I EOP-området skal du bruge [Microsoft 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>IPv6-understøttelse af Microsoft 365 offentlige tilbud

Microsoft 365 IPv6-støtte til offentlige udbud er i overensstemmelse med omB-memorandummet (Office of Management and Budget) for ledende informationschefer i administrationer og agenturer samt det amerikanske memorandum om indførelse af internetprotokol version 6 (IPv6). [Microsoft Microsoft 365 til offentlige myndigheder](https://go.microsoft.com/fwlink/p/?LinkId=325414) er en tjeneste med flere lejere, der gemmer US Government-data i en adskilt communitysky. Ligesom andre Microsoft 365 tilbud leverer den produktivitets- og samarbejdstjenester, herunder Exchange Online, Skype for Business, SharePoint Online og Microsoft 365 Apps for enterprise. 

Microsoft Microsoft 365 Government-tilbud gælder kun for 2013 og nyere. Du kan få flere oplysninger om Microsoft 365 offentlige tilbud under [Meddelelse om Microsoft 365 til offentlige myndigheder: En amerikansk Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). ITAR (International Traffic in Arms Regulations) er et sæt amerikanske regeringsbestemmelser, der styrer eksport og import af forsvarsrelaterede artikler og tjenester på [USML-listen (USA Munitions List).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Microsoft Microsoft 365 til virksomheder leverer dedikerede hostingtjenester til Microsofts produktivitetsløsninger, der understøtter kravene til sikkerhed, beskyttelse af personlige oplysninger og lovmæssig overholdelse af angivne standarder for amerikanske føderale myndigheder, der kræver FISMA-certificering (Federal Information Security Management) og kommercielle enheder, der er underlagt ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>Ting, du skal overveje, når du bruger IPv6 og Microsoft 365

Vi anbefaler, at du ikke deaktiverer IPv6. Du kan finde flere oplysninger i denne [vejledningsartikel](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). Hvis du vil finde ud af, hvilke IP-versioner der bruges på dit netværk, skal du overveje følgende:
  
- Hvis visningen af **IPConfig-kommandoen** ved kommandoprompten indeholder rækker med navnet "IPv6 Address" eller "Temporary IPv6 Address", har du IPv6 i dit miljø.

- Hvis alle IPv6-adresserne begynder med "fe80" og svarer til rækker med navnet "Link-Local IPv6-adresse", har du ikke IPv6 i dit miljø.

Disse overvejelser kan være gældende for dit netværk:
  
- Den offentlige abonnementstjeneste understøtter ikke køb med kreditkort over IPv6. Dette gælder ikke for Government Community Cloud (GCC), fordi regeringer har Enterprise Agreement (EA)-licenser.

- IPv6 understøtter ikke visse RMS-scenarier (Rights Management Services).

- IPv6 understøtter ikke BlackBerry® Enterprise Server (BES), fordi BlackBerry ikke understøtter IPv6.

- Hvis du bruger Active Directory Federation Services (AD FS) sammen med Microsoft 365, understøttes annoncering af dit AD FS-netværksslutpunkt til Microsoft 365 ved hjælp af IPv6 ikke. Du bør ikke inkludere AAAA-poster i AD FS DNS-posten, når du bruger Exchange Online. 

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Se også

[Oversigt over IPv6-Learning](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 Survival Guide](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
