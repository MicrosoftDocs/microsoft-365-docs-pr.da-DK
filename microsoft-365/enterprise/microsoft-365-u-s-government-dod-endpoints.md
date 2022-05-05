---
title: Office 365 US Government DOD-slutpunkter
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
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: Office 365 kræver forbindelse til internettet. Slutpunkterne nedenfor skal være tilgængelige for kunder, der kun bruger Office 365 amerikanske offentlige dod-planer.
hideEdit: true
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f380ab128861b9846a15be675745da0b6c1eb51e
ms.sourcegitcommit: b3f5fe84a319741583954ef8ff2ec9ec6da69bcf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/05/2022
ms.locfileid: "65217492"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 dod-slutpunkter for offentlige myndigheder i USA

*Gælder for: Office 365 Admin*

Office 365 kræver forbindelse til internettet. Slutpunkterne nedenfor skal være tilgængelige for kunder, der kun bruger Office 365 amerikanske offentlige dod-planer.
  
**Office 365 slutpunkter:** [Verdensomspændende (herunder GCC)](urls-and-ip-address-ranges.md) \| [Office 365 drevet af 21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| *Office 365 den amerikanske regering DoD* \| [Office 365 den amerikanske regering GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)

<br>
****

|Bemærkninger|Download|
|---|---|
|**Senest opdateret:** 28-04-2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement på ændringslog](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Download:** den komplette liste i [JSON-format](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

Start med [Administration af Office 365-slutpunkter](managing-office-365-endpoints.md) for at forstå vores anbefalinger til administration af netværksforbindelse ved hjælp af disse data. Slutpunktsdata opdateres efter behov i begyndelsen af hver måned med nye IP-adresser og URL-adresser, der er publiceret 30 dage før, de er aktive. Dette giver kunder, der endnu ikke har automatiserede opdateringer, mulighed for at fuldføre deres processer, før der kræves ny forbindelse. Slutpunkter kan også opdateres i løbet af måneden, hvis det er nødvendigt for at håndtere supporteskaleringer, sikkerhedshændelser eller andre øjeblikkelige driftskrav. De data, der vises på denne side nedenfor, er alle genereret fra de REST-baserede webtjenester. Hvis du bruger et script eller en netværksenhed til at få adgang til disse data, skal du gå direkte til [webtjenesten](microsoft-365-ip-web-service.md) .

Slutpunktsdata nedenfor viser krav til forbindelse fra en brugers computer til Office 365. Det omfatter ikke netværksforbindelser fra Microsoft til et kundenetværk, også kaldet hybride eller indgående netværksforbindelser. Du kan finde flere oplysninger under [Flere slutpunkter, der ikke er inkluderet i webtjenesten](additional-office365-ip-addresses-and-urls.md).

Slutpunkterne er grupperet i fire tjenesteområder. De første tre tjenesteområder kan vælges uafhængigt af hinanden for at oprette forbindelse. Det fjerde tjenesteområde er en almindelig afhængighed (kaldet Microsoft 365 Common og Office) og skal altid have netværksforbindelse.

De viste datakolonner er:

- **ID**: Rækkens id-nummer, også kaldet et slutpunktssæt. Dette id er det samme som det, der returneres af webtjenesten for slutpunktssættet.

- **Kategori**: Viser, om slutpunktssættet er kategoriseret som "Optimer", "Tillad" eller "Standard". Du kan læse om disse kategorier og vejledning til administration af dem på [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Denne kolonne viser også, hvilke slutpunktssæt der kræves for at have netværksforbindelse. I forbindelse med slutpunktssæt, der ikke kræves for at have netværksforbindelse, angiver vi noter i dette felt for at angive, hvilken funktionalitet der mangler, hvis slutpunktet blokeres. Hvis du udelader et helt tjenesteområde, kræver de slutpunktssæt, der er angivet som påkrævet, ikke forbindelse.

- **ER**: Dette er **Ja**, hvis slutpunktssættet understøttes over Azure ExpressRoute med Office 365-rutepræfikser. BGP-community'et, der indeholder de viste rutepræfikser, justeres i forhold til det angivne tjenesteområde. Når ER er **NEJ**, betyder det, at ExpressRoute ikke understøttes for dette slutpunktssæt. Det må dog ikke antages, at der ikke annonceres nogen ruter for et slutpunktssæt, hvor ER er **Nej**. Hvis du planlægger at bruge Azure AD Forbind, skal du læse [afsnittet Særlige overvejelser](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) for at sikre, at du har den relevante Azure AD Forbind konfiguration.

- **Adresser**: Viser FQDN'er eller jokertegn for domænenavne og IP-adresseområder for slutpunktssættet. Bemærk, at et IP-adresseområde er i CIDR-format og kan indeholde mange individuelle IP-adresser i det angivne netværk.

- **Porte**: Viser de TCP- eller UDP-porte, der kombineres med adresserne for at danne netværksslutpunktet. Du bemærker muligvis nogle duplikeringer i IP-adresseområder, hvor der er angivet forskellige porte.

[!INCLUDE [Office 365 U.S. Government DoD endpoints](../includes/office-365-u.s.-government-dod-endpoints.md)]
  
Noter til denne tabel:

- Security and Compliance Center (SCC) understøtter Azure ExpressRoute til Office 365. Det samme gælder for mange funktioner, der vises via SCC, f.eks. Rapportering, Overvågning, eDiscovery (Premium), Unified DLP og Datastyring. To specifikke funktioner, PST Import og eDiscovery Export, understøtter i øjeblikket ikke Azure ExpressRoute med kun Office 365 rutefiltre på grund af deres afhængighed af Azure Blob Storage. Hvis du vil bruge disse funktioner, skal du have separat forbindelse for at Azure Blob Storage ved hjælp af eventuelle understøttede Azure-forbindelsesmuligheder, som omfatter internetforbindelse eller Azure ExpressRoute med Azure Public Route-filtre. Du skal evaluere, om en sådan forbindelse er etableret for begge disse funktioner. Det Office 365 Information Protection team er opmærksom på denne begrænsning og arbejder aktivt på at give understøttelse af Azure ExpressRoute til Office 365 begrænset til Office 365 rutefiltre for begge disse funktioner.

- Der er yderligere valgfrie slutpunkter for Microsoft 365 Apps for enterprise, der ikke er angivet, og som ikke er påkrævet, for at brugerne kan starte Microsoft 365 Apps for enterprise programmer og redigere dokumenter. Valgfrie slutpunkter hostes i Microsoft-datacentre og behandler, overfører eller gemmer ikke kundedata. Vi anbefaler, at brugerforbindelser til disse slutpunkter dirigeres til standardafslutningsperimeteren for internet.
