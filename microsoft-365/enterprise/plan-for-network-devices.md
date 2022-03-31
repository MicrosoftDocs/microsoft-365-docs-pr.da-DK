---
title: Plan for netværksenheder, der opretter forbindelse til Office 365 tjenester
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
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
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Oversigt: Beskriver overvejelser i forbindelse med netværkskapacitet, WAN-acceleratorer og enheder til justering af belastning, der bruges til at oprette forbindelse til Office 365.'
ms.openlocfilehash: 38df9a64610c4b4d44014a142bf7d255aa0a0f46
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601586"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Plan for netværksenheder, der opretter forbindelse til Office 365 tjenester

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*
  
Noget netværkshardware kan have begrænsninger på antallet af samtidige sessioner, der understøttes. For organisationer med mere end 2.000 brugere anbefaler vi, at de overvåger deres netværksenheder for at sikre, at de kan håndtere den ekstra trafik til Office 365-tjenesten. Overvågningssoftwaren Simple Network Management Protocol (SNMP) kan hjælpe dig med dette.

Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).

Lokale indstillinger for udgående internetproxy påvirker også forbindelsen til Office 365 tjenester for dine klientprogrammer. Du skal også konfigurere dine netværksproxyenheder for at tillade forbindelser til Microsofts skytjenesters URL-adresser og programmer. Alle organisationer er forskellige. Læs casestudiet for at få en ide om, hvordan Microsoft administrerer denne proces og mængden af båndbredde, vi [klargør](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Følgende artikler Skype for Business Hjælp har flere oplysninger om Skype for Business indstillinger:
  
- [Fejlfinding Skype for Business online-logonfejl for administratorer](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Du kan ikke oprette Skype for Business, eller visse funktioner virker ikke, fordi en lokal firewall blokerer forbindelsen](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Selvom mange af disse indstillinger Skype for Business, er den generelle vejledning i netværkskonfiguration nyttig for alle Office 365 tjenester.
  
## <a name="determining-network-capacity"></a>Fastslå netværkskapacitet

Enhver netværksenhed, der findes på en forbindelse, har sin kapacitetsgrænse. Disse enheder omfatter klient- og servernetværksadapter, routere, parametre og hubs, der forbinder dem. Tilstrækkelig netværkskapacitet betyder, at ingen af dem er mættet. Overvågning af netværksaktivitet er afgørende for at sikre, at den faktiske belastning på alle netværksenheder er mindre end den maksimale kapacitet. Netværkskapaciteten påvirker proxyenhedens ydeevne.
  
I de fleste situationer indstiller internetforbindelsens båndbredde grænsen for mængden af trafik. Svag ydeevne på tiderne med spidsbelastning for trafik skyldes muligvis overdreven brug af internetlinket. Denne situation gælder også for et scenarie på et afdelingskontor, hvor afdelingens proxyservercomputere er sluttet til proxyenheden på afdelingens hovedkontor via et langsomt WAN-link (Wide Area Network).
  
Hvis du vil teste netværkskapaciteten, skal du overvåge netværksaktiviteten på proxynetværksgrænsefladen. Hvis det er mere end 75 % af den maksimale båndbredde for en netværksgrænseflade, skal du overveje at øge båndbredden for netværksinfrastrukturen, som er utilstrækkelig. Eller du kan overveje at bruge avancerede funktioner, f.eks. HTTP-komprimering.
  
## <a name="wan-accelerators"></a>WAN-acceleratorer

Hvis din organisation bruger WAN-accelerationsproxyudstyr (wide area network), kan der opstå problemer, når du får adgang til Office 365 tjenester. Det kan være nødvendigt at optimere din netværksenhed eller dine enheder for at sikre, at dine brugere har en ensartet oplevelse, når de får adgang til Office 365. Eksempelvis krypterer Office 365 nogle af Office 365 indhold og TCP-headeren. Din enhed kan muligvis ikke håndtere denne type trafik.
  
Læs vores supporterklæring om [Brug af WAN-optimeringscontroller eller Trafik-/Inspektionsenheder Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Enheder til justering af belastning af hardware og software

Din organisation skal bruge en løsning til justering af belastning af hardware (HLB) eller til justering af belastning af netværk (NLB) for at distribuere anmodninger til dine AD FS-servere (Active Directory Federation Services) og/eller dine Exchange-hybridservere. Enheder til justering af belastning styrer netværkstrafikken til de lokale servere. Disse servere er afgørende i forbindelse med at sikre tilgængeligheden af enkelt log på og Exchange hybridinstallation.
  
Vi leverer en softwarebaseret NLB-løsning, der er indbygget Windows Server. Office 365 denne løsning til at opnå belastningsjustering.
  
## <a name="firewalls-and-proxies"></a>Firewalls og proxyer

Hvis du vil have mere at vide om konfiguration af firewalls og proxyer til at oprette forbindelse til [](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)Office 365, skal du læse Administrer Office 365-slutpunkter, vurdering [af Office 365-netværksforbindelse](assessing-network-connectivity.md) og ofte stillede spørgsmål om [Office 365-slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) for at få mere at vide om enheder og valg af kredsløb.
  
## <a name="see-also"></a>Se også

[Installationsvejledninger til Office 365 tjenester](setup-guides-for-microsoft-365.md)

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)