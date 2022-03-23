---
title: Office 365 us Government DOD-slutpunkter
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/28/2022
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
description: Office 365 kræver forbindelse til internettet. Nedenstående slutpunkter skal kun være tilgængelige for kunder, der Office 365 amerikanske Government DoD-planer.
hideEdit: true
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 000ae3590b0c99b59f557e6b70deaa60649054a6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591414"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 amerikanske Government DoD-slutpunkter

*Gælder for: Office 365 Admin*

Office 365 kræver forbindelse til internettet. Nedenstående slutpunkter skal kun være tilgængelige for kunder, der Office 365 amerikanske Government DoD-planer.
  
Office 365 slutpunkter **:** [Worldwide (herunder GCC)](urls-and-ip-address-ranges.md) \| [Office 365 drevet af 21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| *Office 365 U.S. Government DoD* \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)

<br>

****

|Bemærkninger|Download|
|---|---|
|**Senest opdateret:** 28-02-2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Skift log-abonnement](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Download:** den komplette liste i [JSON-format](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

Start med [at administrere Office 365 for at forstå vores anbefalinger](managing-office-365-endpoints.md) til administration af netværksforbindelse ved hjælp af disse data. Slutpunktsdata opdateres efter behov i begyndelsen af hver måned med nye IP-adresser og URL-adresser publiceret 30 dage før de er aktive. Det giver kunder, der endnu ikke har automatiserede opdateringer, mulighed for at fuldføre deres processer, før der kræves en ny forbindelse. Slutpunkter kan også opdateres i løbet af måneden, hvis det er nødvendigt for at håndtere supporteskaleringer, sikkerhedshændelser eller andre øjeblikkelige driftskrav. De data, der vises på denne side nedenfor, genereres alle fra DE REST-baserede webtjenester. Hvis du bruger et script eller en netværksenhed til at få adgang til disse data, skal du gå direkte [til webtjenesten](microsoft-365-ip-web-service.md) .

Slutpunktsdata nedenfor viser krav til tilslutning fra en brugers computer til en Office 365. Det omfatter ikke netværksforbindelser fra Microsoft til et kundenetværk, nogle gange kaldet hybride eller indgående netværksforbindelser. Du kan finde flere oplysninger [under Yderligere slutpunkter, der ikke er inkluderet i webtjenesten](additional-office365-ip-addresses-and-urls.md).

Slutpunkterne er grupperet i fire tjenesteområder. De første tre tjenesteområder kan vælges uafhængigt af forbindelsen. Det fjerde tjenesteområde er en almindelig afhængighed (kaldet fælles Microsoft 365 og Office), og det skal altid have netværksforbindelse.

De datakolonner, der vises, er:

- **Id**: Rækkens id-nummer, også kaldet et slutpunktssæt. Dette id er det samme som det, der returneres af webtjenesten for slutpunktssættet.

- **Kategori**: Viser, om slutpunktssættet er kategoriseret som "Optimer", "Tillad" eller "Standard". Du kan læse om disse kategorier og vejledning til administration af dem på [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Denne kolonne viser også, hvilke slutpunktssæt der kræves for at have netværksforbindelse. For slutpunktssæt, som ikke er nødvendige for at have netværksforbindelse, angiver vi noter i dette felt for at angive, hvilken funktionalitet der mangler, hvis slutpunktssættet er blokeret. Hvis du udelukker et helt tjenesteområde, kræver de slutpunktssæt, der er angivet som påkrævet, ikke forbindelse.

- **ER**: Dette er **Ja**, hvis slutpunktssættet understøttes over Azure ExpressRoute med Office 365 rutepræfikser. BGP-community'et, der omfatter de viste rutepræfikser, passer til det angivne tjenesteområde. Når ER er **Nej**, betyder det, at ExpressRoute ikke understøttes for dette slutpunktssæt. Det bør dog ikke antages, at der ikke annonceres nogen ruter for et slutpunktssæt, hvor ER er **Nej**. Hvis du planlægger at bruge Azure AD Forbind, skal du læse afsnittet [særlige](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) overvejelser for at sikre, at du har de relevante Azure AD-Forbind konfiguration.

- **Adresser**: Viser FQDN'er eller domænenavne med jokertegn og IP-adresseintervaller for slutpunktssættet. Bemærk, at et IP-adresseområde er i CIDR-format og kan indeholde mange individuelle IP-adresser i det angivne netværk.

- **Porte**: Viser de TCP- eller UDP-porte, der kombineres med adresserne for at danne netværksslutpunktet. Du vil muligvis bemærke duplikering i IP-adresseintervaller, hvor der er angivet forskellige porte.

[!INCLUDE [Office 365 U.S. Government DoD endpoints](../includes/office-365-u.s.-government-dod-endpoints.md)]
  
Bemærkninger til denne tabel:

- Security and Compliance Center (SCC) understøtter Azure ExpressRoute til Office 365. Det samme gælder for mange funktioner, der vises via SCC, f.eks. rapportering, overvågning, Advanced eDiscovery, samlet DLP og datastyring. To specifikke funktioner, PST-import og eDiscovery-eksport, understøtter i øjeblikket ikke Azure ExpressRoute kun med Office 365-rutefiltre på grund af deres afhængighed af Azure Blob Storage. Hvis du vil bruge disse funktioner, skal du oprette en separat forbindelse til Azure Blob Storage ved hjælp af alle understøttede Azure-forbindelsesmuligheder, som omfatter internetforbindelse eller Azure ExpressRoute med offentlige Azure-rutefiltre. Du skal evaluere oprettelse af en sådan forbindelse for begge disse funktioner. Information Protection Office 365-teamet er opmærksom på denne begrænsning og arbejder aktivt på at bringe support til Azure ExpressRoute til Office 365 så begrænset til Office 365-rutefiltre for begge disse funktioner.

- Der er flere valgfri slutpunkter for Microsoft 365 Apps for enterprise, der ikke er angivet, og som ikke er påkrævet, for at brugerne kan starte Microsoft 365 Apps for enterprise programmer og redigere dokumenter. Valgfri slutpunkter er hostet i Microsoft-datacentre og behandler, overfører eller gemmer ikke kundedata. Vi anbefaler, at brugerforbindelser til disse slutpunkter bliver ført til den standardperimeter for internetud udgangspunktet.
