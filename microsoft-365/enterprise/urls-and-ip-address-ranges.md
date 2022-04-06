---
title: Office 365-URL-adresser og IP-adresseintervaller
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/28/2022
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
description: 'Oversigt: Office 365 kræver forbindelse til internettet. Nedenstående slutpunkter skal være tilgængelige for kunder, der bruger Office 365, herunder Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 04522b211056b1d7c6feba08dd97fc3a2d33451a
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634861"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Office 365-URL-adresser og IP-adresseintervaller

Office 365 kræver forbindelse til internettet. Nedenstående slutpunkter skal være tilgængelige for kunder, der bruger Office 365, herunder Government Community Cloud (GCC).
  
*Office 365 Worldwide (+GCC)* \| Office 365 drevet af [21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|Bemærkninger|Download|Brug|
|---|---|---|
|**Senest opdateret:** 28-03-2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Skift log-abonnement](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Download:** alle påkrævede og valgfrie destinationer i én [JSON-formateret](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) liste.|**Brug:** vores [proxy-PAC-filer](managing-office-365-endpoints.md#pacfiles)|
|

Start med [at administrere Office 365 for at forstå vores anbefalinger](managing-office-365-endpoints.md) til administration af netværksforbindelse ved hjælp af disse data. Slutpunktsdata opdateres efter behov i begyndelsen af hver måned med nye IP-adresser og URL-adresser publiceret 30 dage før de er aktive. Dette giver kunder, der endnu ikke har automatiserede opdateringer, mulighed for at fuldføre deres processer, før der kræves ny forbindelse. Slutpunkter kan også opdateres i løbet af måneden, hvis det er nødvendigt for at håndtere supporteskaleringer, sikkerhedshændelser eller andre øjeblikkelige driftskrav. De data, der vises på denne side nedenfor, genereres alle fra DE REST-baserede webtjenester. Hvis du bruger et script eller en netværksenhed til at få adgang til disse data, skal du gå direkte [til webtjenesten](microsoft-365-ip-web-service.md) .

Slutpunktsdata nedenfor viser krav til tilslutning fra en brugers computer til en Office 365. Du kan finde flere oplysninger om IP-adresser, der bruges til netværksforbindelser fra Microsoft til et kundenetværk, nogle gange kaldet hybride eller indgående netværksforbindelser, under Yderligere [slutpunkter](additional-office365-ip-addresses-and-urls.md) for at få flere oplysninger.

Slutpunkterne er grupperet i fire tjenesteområder, der repræsenterer de tre primære arbejdsbelastninger og et sæt fælles ressourcer. Grupperne kan bruges til at knytte trafikflows til et bestemt program, men hvis funktioner ofte forbruger slutpunkter på tværs af flere arbejdsbelastninger, kan disse grupper ikke effektivt bruges til at begrænse adgangen.

De datakolonner, der vises, er:

- **Id**: Rækkens id-nummer, også kaldet et slutpunktssæt. Dette id er det samme som det, der returneres af webtjenesten for slutpunktssættet.

- **Kategori**: Viser, om slutpunktssættet er kategoriseret som "Optimer", "Tillad" eller "Standard". Du kan læse om disse kategorier og vejledning til administration af dem [i Office 365 kategorier for slutpunkter](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories). Denne kolonne viser også, hvilke slutpunktssæt der kræves for at have netværksforbindelse. For slutpunktssæt, som ikke er nødvendige for at have netværksforbindelse, angiver vi noter i dette felt for at angive, hvilken funktionalitet der mangler, hvis slutpunktssættet er blokeret. Hvis du udelukker et helt tjenesteområde, kræver de slutpunktssæt, der er angivet som påkrævet, ikke forbindelse.

- **ER**: Dette er **Ja**, hvis slutpunktssættet understøttes over Azure ExpressRoute med Office 365 rutepræfikser. BGP-community'et, der omfatter de viste rutepræfikser, passer til det angivne tjenesteområde. Når ER er **Nej**, betyder det, at ExpressRoute ikke understøttes for dette slutpunktssæt. Det bør dog ikke antages, at der ikke annonceres nogen ruter for et slutpunktssæt, hvor ER er **Nej**.

- **Adresser**: Viser FQDN'er eller domænenavne med jokertegn og IP-adresseintervaller for slutpunktssættet. Bemærk, at et IP-adresseområde er i CIDR-format og kan indeholde mange individuelle IP-adresser i det angivne netværk.

- **Porte**: Viser de TCP- eller UDP-porte, der kombineres med adresserne for at danne netværksslutpunktet. Du vil muligvis bemærke duplikering i IP-adresseintervaller, hvor der er angivet forskellige porte.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> Du kan finde Yammer om [IP-adresser og URL-adresser i Brug af hard-coded IP-adresser til Yammer anbefales](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592) ikke på den Yammer blog.

## <a name="related-topics"></a>Relaterede emner

[Yderligere slutpunkter er ikke inkluderet i Office 365 IP-adresse og URL-webtjeneste](additional-office365-ip-addresses-and-urls.md)

[Administrere Office 365-slutpunkter](managing-office-365-endpoints.md)

[Generelle Microsoft Stream slutpunkter](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Overvåg Microsoft 365 forbindelse](./monitor-connectivity.md)

[Rodnøglecenter og bundlet mellemliggende nøglecenter på tredjepartsprogramsystemet](../compliance/encryption-office-365-certificate-chains.md)
  
[Klientforbindelse](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Content Delivery Networks](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Microsoft Azure IP-områder og tjenestemærker – Offentlig sky](https://www.microsoft.com/download/details.aspx?id=56519)

[Microsoft Azure IP-områder og tjenestemærker – den amerikanske regerings sky](https://www.microsoft.com/download/details.aspx?id=57063)

[Microsoft Azure IP-områder og servicemærker – China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602)

[Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
