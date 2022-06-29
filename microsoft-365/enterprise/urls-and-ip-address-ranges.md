---
title: Office 365-URL-adresser og IP-adresseintervaller
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/01/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Regering: Office 365 kræver forbindelse til internettet. Nedenstående slutpunkter skal være tilgængelige for kunder, der bruger Office 365-abonnementer, herunder GCC (Government Community Cloud).'
hideEdit: true
ms.openlocfilehash: 8a878d9be63411d891f0f42e9c9a0df722317666
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493758"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365-URL-adresser og IP-adresseintervaller

Office 365 kræver forbindelse til internettet. Nedenstående slutpunkter skal være tilgængelige for kunder, der bruger Office 365-abonnementer, herunder Government Community Cloud (GCC).
  
*Office 365 Worldwide (+GCC)*\|[Office 365 drevet af 21 Vianet](urls-and-ip-address-ranges-21vianet.md)\|[Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md)\|[Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)\|

|Bemærkninger|Download|Brug|
|---|---|---|
|**Senest opdateret:** 01-06-2022 – ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement på ændringslog](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Download:** alle påkrævede og valgfrie destinationer på én [JSON-formateret](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) liste.|**Brug:** vores proxy [PAC-filer](managing-office-365-endpoints.md#pacfiles)|
|

Start med [Administration af Office 365-slutpunkter](managing-office-365-endpoints.md) for at forstå vores anbefalinger til administration af netværksforbindelse ved hjælp af disse data. Slutpunktsdata opdateres efter behov i begyndelsen af hver måned med nye IP-adresser og URL-adresser, der er publiceret 30 dage før, de er aktive. Denne kadence giver kunder, der endnu ikke har automatiserede opdateringer, mulighed for at fuldføre deres processer, før der kræves ny forbindelse. Slutpunkter kan også opdateres i løbet af måneden, hvis det er nødvendigt for at håndtere supporteskaleringer, sikkerhedshændelser eller andre øjeblikkelige driftskrav. De data, der vises på denne side nedenfor, er alle genereret fra de REST-baserede webtjenester. Hvis du bruger et script eller en netværksenhed til at få adgang til disse data, skal du gå direkte til [Webtjenesten](microsoft-365-ip-web-service.md).

Slutpunktsdata nedenfor viser krav til forbindelse fra en brugers computer til Office 365. Du kan finde flere oplysninger om IP-adresser, der bruges til netværksforbindelser fra Microsoft til et kundenetværk, også kaldet hybride eller indgående netværksforbindelser, under [Flere slutpunkter](additional-office365-ip-addresses-and-urls.md) for at få flere oplysninger.

Slutpunkterne er grupperet i fire tjenesteområder, der repræsenterer de tre primære arbejdsbelastninger og et sæt fælles ressourcer. Grupperne kan bruges til at knytte trafikstrøm til et bestemt program, men da funktioner ofte forbruger slutpunkter på tværs af flere arbejdsbelastninger, kan disse grupper ikke effektivt bruges til at begrænse adgangen.

De viste datakolonner er:

- **ID**: Rækkens id-nummer, også kaldet et slutpunktssæt. Dette id er det samme som det, der returneres af webtjenesten for slutpunktssættet.

- **Kategori**: Viser, om slutpunktssættet er kategoriseret som **Optimer**, **Tillad**, eller **Standard**. Denne kolonne viser også, hvilke slutpunktssæt der kræves for at have netværksforbindelse. For slutpunktssæt, der ikke er nødvendige for at have netværksforbindelse, angiver vi noter i dette felt for at angive, hvilken funktionalitet der mangler, hvis slutpunktssættet blokeres. Hvis du udelader et helt tjenesteområde, kræver de angivne slutpunktssæt ikke forbindelse.

   Du kan læse om disse kategorier og vejledning til deres administration i [Nye kategorier af Office 365-slutpunkter](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

- **ER**: Dette er **Ja**, hvis slutpunktssættet understøttes over Azure ExpressRoute med Office 365-rutepræfikser. BGP-community'et, der indeholder de viste rutepræfikser, justeres i forhold til det angivne tjenesteområde. Når ER er **NEJ**, betyder det, at ExpressRoute ikke understøttes for dette slutpunktssæt.

   Nogle ruter kan annonceres i mere end ét BGP-community, hvilket gør det muligt for slutpunkter inden for et bestemt IP-område at gennemgå ER-kredsløbet, men de understøttes stadig ikke. I alle tilfælde skal værdien af et givet slutpunktssæts ER-kolonne respekteres. Du kan få mere at vide om BGP-communities under [Brug af BGP-communities i ExpressRoute til Office 365-scenarier](bgp-communities-in-expressroute.md#key-planning-considerations-to-using-bgp-communities).

- **Adresser**: Viser FQDN'er eller jokertegn for domænenavne og IP-adresseområder for slutpunktssættet. Bemærk, at et IP-adresseområde er i CIDR-format og kan indeholde mange individuelle IP-adresser i det angivne netværk.

- **Porte**: Viser de TCP- eller UDP-porte, der kombineres med adresserne for at danne netværksslutpunktet. Du bemærker muligvis nogle duplikeringer i IP-adresseområder, hvor der er angivet forskellige porte.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> Du kan få anbefalinger om Yammer-IP-adresser og URL-adresser under [Brug af hard-coded IP-adresser til Yammer anbefales ikke](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) på Yammer-bloggen.

## <a name="related-topics"></a>Relaterede emner

[Yderligere slutpunkter, der ikke er inkluderet i Office 365 IP-adressen og URL-adressewebtjenesten](additional-office365-ip-addresses-and-urls.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Generelle Microsoft Stream-slutpunkter](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Overvåg Microsoft 365-forbindelse](./monitor-connectivity.md)

[Root CA og Intermediate CA-bundt på tredjeparts applikationssystemet](../compliance/encryption-office-365-certificate-chains.md)
  
[Klientforbindelse](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Content Delivery Networks](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure IP-intervaller og tjenestetags – Offentlig sky](https://www.microsoft.com/download/details.aspx?id=56519)

[Microsoft Azure IP-intervaller og tjenestetags – Den amerikanske regerings sky](https://www.microsoft.com/download/details.aspx?id=57063)

[Microsoft Azure IP-intervaller og tjenestetags – Kinas sky](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Offentlige IP fra Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

[Tjenestenavn og transportprotokolportnummerregister](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
