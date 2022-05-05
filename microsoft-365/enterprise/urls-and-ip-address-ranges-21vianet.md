---
title: URL-adresser og IP-adresseintervaller for Office 365, der drives af 21Vianet
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/28/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
description: I denne artikel vises URL-adresserne og IP-adresseintervaller for Office 365, når de drives af 21Vianet i Kina.
hideEdit: true
ms.openlocfilehash: 4c91505c0a83408e435879e718901d949e5eba26
ms.sourcegitcommit: b3f5fe84a319741583954ef8ff2ec9ec6da69bcf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/05/2022
ms.locfileid: "65217514"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>URL-adresser og IP-adresseintervaller for Office 365, der drives af 21Vianet

 *Gælder for: Office 365, der drives af 21Vianet – Small Business Admin, Office 365 drevet af 21Vianet – Administrator*

**Oversigt**: Følgende slutpunkter (FQDN'er, porte, URL-adresser, IPv4- og IPv6-præfikser) gælder for Office 365, der drives af 21 Vianet, og er designet til at levere produktivitetstjenester til organisationer, der kun bruger disse planer.
  
 **Office 365 slutpunkter:** [Verdensomspændende (herunder GCC)](urls-and-ip-address-ranges.md)  | *Office 365 drevet af 21 Vianet* |  [Office 365 US Government DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 US Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**Senest opdateret:** 28-04-2021 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement på ændringslog](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**Download:** alle påkrævede og valgfrie destinationer på én [JSON-formateret](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) liste.

Start med [Administration af Office 365-slutpunkter](managing-office-365-endpoints.md) for at forstå vores anbefalinger til administration af netværksforbindelse ved hjælp af disse data. Slutpunktsdata opdateres efter behov i begyndelsen af hver måned med nye IP-adresser og URL-adresser, der er publiceret 30 dage før, de er aktive. Dette giver kunder, der endnu ikke har automatiserede opdateringer, mulighed for at fuldføre deres processer, før der kræves ny forbindelse. Slutpunkter kan også opdateres i løbet af måneden, hvis det er nødvendigt for at håndtere supporteskaleringer, sikkerhedshændelser eller andre øjeblikkelige driftskrav. De data, der vises på denne side nedenfor, er alle genereret fra de REST-baserede webtjenester. Hvis du bruger et script eller en netværksenhed til at få adgang til disse data, skal du gå direkte til den [Webtjeneste](microsoft-365-ip-web-service.md).

Slutpunktsdata nedenfor viser en liste over krav til forbindelse fra en brugers computer til Office 365. Den omfatter ikke netværksforbindelser fra Microsoft til et kundenetværk, også kaldet hybride eller indgående netværksforbindelser.

Slutpunkterne er grupperet i fire tjenesteområder. De første tre tjenesteområder kan vælges uafhængigt af hinanden for at oprette forbindelse. Det fjerde tjenesteområde er en almindelig afhængighed (kaldet Microsoft 365 Common og Office) og skal altid have netværksforbindelse.

De viste datakolonner er:

- **ID**: Rækkens id-nummer, også kaldet et slutpunktssæt. Dette id er det samme som det, der returneres af webtjenesten for slutpunktssættet.

- **Kategori**: Viser, om slutpunktssættet er kategoriseret som "Optimer", "Tillad" eller "Standard". Du kan læse om disse kategorier og vejledning til administration af dem på [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Denne kolonne viser også, hvilke slutpunktssæt der kræves for at have netværksforbindelse. For slutpunktssæt, der ikke er nødvendige for at have netværksforbindelse, angiver vi noter i dette felt for at angive, hvilken funktionalitet der mangler, hvis slutpunktssættet blokeres. Hvis du udelader et helt tjenesteområde, kræver de angivne slutpunktssæt ikke forbindelse.

- **ER**: Dette er **Ja**, hvis slutpunktssættet understøttes over Azure ExpressRoute med Office 365-rutepræfikser. BGP-community'et, der indeholder de viste rutepræfikser, justeres i forhold til det angivne tjenesteområde. Når ER er **NEJ**, betyder det, at ExpressRoute ikke understøttes for dette slutpunktssæt. Det må dog ikke antages, at der ikke annonceres nogen ruter for et slutpunktssæt, hvor ER er **Nej**.

- **Adresser**: Viser FQDN'er eller jokertegn for domænenavne og IP-adresseområder for slutpunktssættet. Bemærk, at et IP-adresseområde er i CIDR-format og kan indeholde mange individuelle IP-adresser i det angivne netværk.
 
- **Porte**: Viser de TCP- eller UDP-porte, der kombineres med adresserne for at danne netværksslutpunktet. Du bemærker muligvis nogle duplikeringer i IP-adresseområder, hvor der er angivet forskellige porte.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]