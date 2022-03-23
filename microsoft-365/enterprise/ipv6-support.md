---
title: IPv6-understøttelse i Microsoft 365 tjenester
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Beskriver IPv6-understøttelse i Microsoft 365 og i Microsoft 365 government-tilbud.'
ms.openlocfilehash: a6a2e11ff2e312c02f10d152fe580bdead5fa7c9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63590959"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>IPv6-understøttelse i Microsoft 365 tjenester

Microsoft 365 understøtter både IPv6 og IPv4, men ikke alle Microsoft 365 er fuldt aktiveret med IPv6. Det betyder, at du skal bruge både IPv4 og IPv6 for at oprette forbindelse til Microsoft 365. Hvis du filtrerer din udgående trafik til Microsoft 365, kan du finde den komplette liste over IPv6-adresser, der understøttes af Microsoft 365, i artiklen Microsoft 365 URL-adresser og [IP-adresseintervaller](urls-and-ip-address-ranges.md). Når dit netværk er konfigureret, og de relevante IPv6-adresser er tilladt, kan du downloade Microsoft 365 [IPv6-testplanen](https://go.microsoft.com/fwlink/?LinkId=293447) fra Microsoft Download Center.

> [!NOTE]
> En giver kunderne mulighed for at opleve Microsoft 365 SaaS-tjenester fra enhver placering, og enhver enhed er en prioritet for Microsoft. Dette omfatter, at kunderne kan oprette forbindelse til og bruge Microsoft 365 IPv6-aktiveret og IPv6 kun klienter og informationssystemer. Det omfatter også, at offentlige kunder kan overholde IPv6-forpligtelser på deres netværk, mens de fortsat Microsoft 365 produktivitetsscenarier uden afbrydelser.  
> Denne artikel indeholder en liste over Microsoft 365 SaaS-tjenester, der tillader direkte IPv6-forbindelse i dag. Omfanget af tjenester, der tillader direkte IPv6-forbindelse, forventes at fortsætte med at udvide. Microsoft 365 tjenester, der ikke udtrykkeligt er nævnt med henblik på direkte IPv6-support, og hvis du vil medtage Azure Active Directory (AAD)-godkendelsestjenester, skal du anses for at kræve, at DNS64/NAT64 kun skal forbindes til fra IPv6-klienter og -miljøer.  Dette er i overensstemmelse med de formål, der aktuelt er beskrevet i eksisterende NIST USGv6-dokumentation: Krav til overgangsmekanismen i [NIST Special Publication 500-267A Revision 1](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.500-267Ar1.pdf) NAT64/DNS64 er acceptable teknologier, der kan anvendes.
> - NAT64-understøttelse af overgangsmekanisme NAT64 [RFC6146](https://datatracker.ietf.org/doc/html/rfc6146) Stateful NAT64: Netværksadresse og protokoloversættelse fra IPv6-klienter til IPv4-servere
> - DNS64-understøttelse af overgangsmekanisme DNS64. [RFC6147](https://datatracker.ietf.org/doc/html/rfc6147) DNS64: DNS-udvidelser til oversættelse af netværksadresser fra IPv6-klienter til IPv4-server

  
## <a name="ipv6-support-in-microsoft-365-subscription-service"></a>IPv6-support i Microsoft 365-abonnementstjeneste

### <a name="exchange-online-and-ipv6"></a>Exchange Online og IPv6

Hvis det program, du bruger til at oprette forbindelse til Exchange Online, understøtter IPv6, bruges IPv6 som standard på både kablede og trådløse netværk. Hvis du vil styre kommunikationen til Exchange Online, skal du bruge IP-adresseintervaller i [Microsoft 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md).
  
### <a name="sharepoint-online-and-ipv6"></a>SharePoint Online og IPv6

 **Microsoft 365 Government G1/G3/G4/K1** Hvis det program, du bruger til at oprette forbindelse til SharePoint Online, understøtter IPv6, vil det som standard forsøge at bruge IPv6.
  
 **Offentlig sky med flere lejere** Microsoft aktiverer SharePoint Online IPv6 på din anmodning. Du skal angive de CIDR-noterede IP-adresser til organisationens DNS-infrastruktur. Husk, at denne DNS-infrastruktur ikke kan deles af andre organisationer, så IPv6 er aktiveret for din lejer. Når IPv6 er aktiveret, og det program, du bruger til at oprette forbindelse til SharePoint Online, understøtter IPv6, bruges IPv6 som standard.
  
Hvis det program, du bruger til at oprette forbindelse til SharePoint Online, understøtter IPv6, bruges IPv6 som standard på både kablede og trådløse netværk. Hvis du vil styre kommunikationen til SharePoint Online, skal du bruge IP-adresseintervaller i [Microsoft 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md).
  
 
  
### <a name="skype-for-business-and-ipv6"></a>Skype for Business og IPv6

Bemærk, at IPv6 ikke understøttes i Skype for Business og kan ikke længere aktiveres.

### <a name="microsoft-teams-sip-gateway-and-ipv6"></a>Microsoft Teams, SIP Gateway og IPV6

Microsoft Teams Direct Routing og SIP Gateway understøtter kun IPv4. Tjenesten Microsoft Teams og klienten understøtter både IPv4 og IPv6. Hvis du vil styre kommunikationen til Microsoft Teams, skal du bruge IP-adresseintervaller i [Microsoft 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md).
  
### <a name="exchange-online-protection-and-ipv6"></a>Exchange Online Protection og IPv6

Exchange Online Protection (EOP) understøtter IPv6, hvis overførslen sker via Transport Layer Security Protocol. For EOP-området skal du Microsoft 365 [URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md).
  
### <a name="ipv6-support-for-microsoft-365-government-offerings"></a>IPv6-understøttelse Microsoft 365 Government-tilbud

Microsoft 365 IPv6-understøttelse af Government-tilbud er i overensstemmelse med Office OMB-protokollen (Management and Budget) for Chief Information Officers i ledelsesafdelinger og styrelser samt den føderale regerings indførelse af en internetprotokol version 6 (IPv6)-godkendelse. [Microsoft Microsoft 365 for Government er](https://go.microsoft.com/fwlink/p/?LinkId=325414) en tjeneste med flere lejere, der gemmer data fra det amerikanske offentlige i en adskilt community-sky. Som Microsoft 365 andre tilbud giver den produktivitets- og samarbejdstjenester, herunder Exchange Online, Skype for Business, SharePoint Online og Microsoft 365 Apps for enterprise. 

Microsoft Microsoft 365 government-tilbud gælder kun for 2013 og senere. Du kan finde flere oplysninger Microsoft 365 government-tilbud i [Announcing Microsoft 365 for Government: A US Government Community Cloud](https://go.microsoft.com/fwlink/p/?LinkId=325414). International Traffic in Arms Regulations (ITAR) er et sæt af amerikanske myndigheder, der styrer eksport og import af forsvarsrelaterede artikler og tjenester på [USML (United States Munitions List).](https://go.microsoft.com/fwlink/p/?LinkId=325415) 

Microsoft Microsoft 365 for Enterprises leverer dedikerede hostingtjenester til Microsofts produktivitetsløsninger, der understøtter krav til sikkerhed, beskyttelse af personlige oplysninger og lovgivning for amerikanske føderale myndigheder, der har brug for FISMA-certificering (Federal Information Security Management), og kommercielle enheder, der er underlagt ITAR.
  
## <a name="things-to-consider-when-using-ipv6-and-microsoft-365"></a>Ting, du skal overveje, når du bruger IPv6 og Microsoft 365

Vi anbefaler, at du ikke deaktiverer IPv6. Du kan finde flere oplysninger i denne [vejledningsartikel](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users). For at finde ud af, hvilke IP-versioner der bruges på dit netværk, skal du overveje følgende:
  
- Hvis visningen af **kommandoen IPConfig** ved kommandoprompten indeholder rækker med navnet "IPv6-adresse" eller "Midlertidig IPv6-adresse", har du IPv6 i dit miljø.

- Hvis alle IPv6-adresserne starter med "fe80" og svarer til rækker med navnet "Link-Local IPv6-adresse", har du ikke IPv6 i dit miljø.

Disse overvejelser kan være gældende for dit netværk:
  
- Den offentlige abonnementstjeneste understøtter ikke køb med kreditkort over IPv6. Dette gælder ikke for Government Community Cloud (GCC), fordi regeringsservere har Enterprise Agreement (EA)-licensering.

- IPv6 understøtter ikke visse RMS-scenarier (Rights Management Services).

- IPv6 understøtter ikke BlackBerry® Enterprise Server (BES), fordi BlackBerry ikke understøtter IPv6.

- Hvis du bruger Active Directory Federation Services (AD FS) med Microsoft 365, understøttes annoncering af dit AD FS-netværksslutpunkt Microsoft 365 at bruge IPv6 ikke. Du bør ikke medtage AAAA-poster i AD FS DNS-posten, når du bruger Exchange Online. 

Her er et kort link, du kan bruge til at vende tilbage: [https://aka.ms/o365ip6]()

## <a name="see-also"></a>Se også

[Oversigt over Learning for IPv6](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/gg250710(v%3dws.10))
  
[IPv6 Overlevelsesvejledning](https://social.technet.microsoft.com/wiki/contents/articles/1728.ipv6-survival-guide.aspx)
