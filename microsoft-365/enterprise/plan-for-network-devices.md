---
title: Planlæg for netværksenheder, der opretter forbindelse til Office 365 tjenester
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: 58c4225d9d381dabedfa86d81ced7f5922932058
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100319"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a>Planlæg for netværksenheder, der opretter forbindelse til Office 365 tjenester

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*
  
Noget netværkshardware kan have begrænsninger på antallet af samtidige sessioner, der understøttes. For organisationer med mere end 2.000 brugere anbefaler vi, at de overvåger deres netværksenheder for at sikre, at de er i stand til at håndtere den ekstra Office 365 tjenestetrafik. SNMP-overvågningssoftware (Simple Network Management Protocol) kan hjælpe dig med at gøre dette.

Denne artikel er en del af [Netværksplanlægning og justering af ydeevnen for Office 365](./network-planning-and-performance.md).

Indstillingerne for udgående internetproxyer i det lokale miljø påvirker også forbindelsen til Office 365 tjenester til dine klientprogrammer. Du skal også konfigurere dine netværksproxyenheder for at tillade forbindelser til URL-adresser og programmer til Microsoft-cloudtjenester. Alle organisationer er forskellige. Hvis du vil have en idé om, hvordan Microsoft administrerer denne proces og mængden af båndbredde, vi klargør, skal du [læse casestudiet](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).
  
Følgende Skype for Business Hjælp-artikler indeholder flere oplysninger om indstillinger for Skype for Business:
  
- [Fejlfinding Skype for Business onlinelogonfejl for administratorer](/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [Du kan ikke oprette forbindelse til Skype for Business, eller visse funktioner fungerer ikke, fordi en firewall i det lokale miljø blokerer forbindelsen](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> Selvom mange af disse indstillinger er Skype for Business specifikke, er den generelle vejledning om netværkskonfiguration nyttig for alle Office 365 tjenester.
  
## <a name="determining-network-capacity"></a>Fastlæggelse af netværkskapacitet

Alle netværksenheder, der findes på en forbindelse, har en kapacitetsgrænse. Disse enheder omfatter klient- og servernetværksadaptere, routere, parametre og hubs, der forbinder dem. Tilstrækkelig netværkskapacitet betyder, at ingen af dem er mættet. Overvågning af netværksaktivitet er afgørende for at sikre, at de faktiske belastninger på alle netværksenheder er mindre end deres maksimale kapacitet. Netværkskapacitet påvirker proxyenhedens ydeevne.
  
I de fleste situationer angiver internetforbindelsesbåndbredden grænsen for mængden af trafik. Dårlig ydeevne i spidsbelastningstimer skyldes sandsynligvis overdreven brug af internetforbindelsen. Denne situation gælder også for et forgreningskontorscenarie, hvor proxyservercomputere for forgreninger er forbundet til proxyenheden i forgreningshovedkvarteret via et langsomt WAN-link (Wide Area Network).
  
Hvis du vil teste netværkskapaciteten, skal du overvåge netværksaktiviteten på proxynetværkets grænseflade. Hvis det er mere end 75 procent af den maksimale båndbredde for enhver netværksgrænseflade, kan du overveje at øge båndbredden af netværksinfrastrukturen, der er utilstrækkelig. Du kan også overveje at bruge avancerede funktioner, f.eks. HTTP-komprimering.
  
## <a name="wan-accelerators"></a>WAN-acceleratorer

Hvis din organisation bruger WAN-accelerationsproxyapparater (Wide Area Network), kan der opstå problemer, når du åbner Office 365-tjenesterne. Du skal muligvis optimere din netværksenhed eller dine enheder for at sikre, at brugerne får en ensartet oplevelse, når de får adgang til Office 365. Office 365 tjenester krypterer f.eks. noget Office 365 indhold og TCP-headeren. Enheden kan muligvis ikke håndtere denne type trafik.
  
Læs vores supporterklæring om [brug af WAN-optimeringscontroller- eller trafik-/inspektionsenheder med Office 365](https://support.microsoft.com/kb/2690045).
  
## <a name="hardware-and-software-load-balancing-devices"></a>Enheder med belastningsjustering af hardware og software

Din organisation skal bruge en HLB-løsning (Hardware Load Balancer) eller en NLB-løsning (Network Load Balancing) til at distribuere anmodninger til dine AD FS-servere (Active Directory Federation Services) og/eller dine Exchange hybridservere. Enheder med justering af belastning styrer netværkstrafikken til lokale servere. Disse servere er afgørende for at sikre tilgængeligheden af enkeltlogon og Exchange hybridinstallation.
  
Vi leverer en softwarebaseret NLB-løsning, der er indbygget i Windows Server. Office 365 understøtter denne løsning for at opnå belastningsjustering.
  
## <a name="firewalls-and-proxies"></a>Firewalls og proxyer

Du kan finde flere oplysninger om konfiguration af firewalls og proxyer for at oprette forbindelse til Office 365 ved at læse [Administration af Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Vurdering af Office 365 netværksforbindelse](assessing-network-connectivity.md) og [ofte stillede spørgsmål om Office 365 slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) for at få mere at vide om enheder og valg af kredsløb.
  
## <a name="see-also"></a>Se også

[Installationsvejledninger til Office 365 tjenester](setup-guides-for-microsoft-365.md)

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)