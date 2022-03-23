---
title: NAT-understøttelse med Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: Denne artikel indeholder oplysninger om, hvordan du omtrentlig ser det antal klienter, du kan bruge pr. IP-adresse i organisationen ved hjælp af NAT.
ms.openlocfilehash: 5335ac87bb579b6cb00e1387da97dd5a1d4f6c7f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594210"
---
# <a name="nat-support-with-office-365"></a>NAT-understøttelse med Office 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Tidligere anbefalede vejledningen, at det maksimale antal Exchange-klienter, du skal bruge pr. IP-adresse for at oprette forbindelse til Office 365, var omkring 2.000 klienter pr. netværksport.
  
## <a name="why-use-nat"></a>Hvorfor bruge NAT?

Ved hjælp af NAT kan tusindvis af personer på et virksomhedsnetværk "dele" nogle enkelte offentlige IP-adresser, der kan roustable.
  
De fleste virksomhedsnetværk bruger private (RFC1918) IP-adresserum. Private adresserum allokeres af Internet Assigned Numbers Authority (IANA) og er udelukkende beregnet til netværk, der ikke dirigerer direkte til og fra det globale internet.
  
For at give internetadgang til enheder på et privat IP-adresseområde bruger organisationer gatewayteknologier som firewalls og proxyer, der leverer oversættelse af netværksadresse (NAT) eller PORT Address Translation-tjenester (PAT). Disse gateways får trafik fra interne enheder til internettet (herunder Office 365) til at komme fra en eller flere offentligt tilgængelige IP-adresser. Hver udgående forbindelse fra en intern enhed omsættes til en anden kilde-TCP-port på den offentlige IP-adresse. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Hvorfor skal du have så mange forbindelser åbne for at Office 365 på samme tid?

Outlook kan åbne otte eller flere forbindelser (i situationer, hvor der er tilføjelsesprogrammet, delte kalendere, postkasser osv.). Da der maksimalt er 64.000 porte tilgængelige på en Windows-baseret NAT-enhed, kan der maksimalt være 8.000 brugere bag en IP-adresse, før portene opbrugte. Bemærk, at hvis kunder bruger ikke-Windows OS-baserede enheder til NAT, er det samlede antal tilgængelige porte afhængigt af, hvilken NAT-enhed eller software der bruges. I dette scenarie kan det maksimale antal porte være mindre end 64.000. Tilgængeligheden af porte påvirkes også af andre faktorer, f.eks. Windows begrænsning af 4.000 porte til eget brug, hvilket reducerer det samlede antal tilgængelige porte til 60.000. Der kan være andre programmer, f.eks. Internet Explorer, som kan oprette forbindelse samtidigt, hvilket kræver yderligere porte.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Beregne det maksimale antal understøttede enheder bag en enkelt offentlig IP-adresse med Office 365

For at bestemme det maksimale antal enheder bag en enkelt offentlig IP-adresse skal du overvåge netværkstrafikken for at bestemme portforbruget ved spidsbelastning pr. klient. En spidsbelastningsfaktor skal også bruges til portforbrug (minimum 4). 
  
 **Brug følgende formel til at beregne antallet af understøttede enheder pr. IP-adresse:**
  
Maksimum antal understøttede enheder bag en enkelt offentlig IP-adresse = (64.000 - begrænsede porte)/(Portforbrug ved spidsbelastning + spidsbelastningsfaktor)
  
 **Hvis f.eks. følgende var sandt:**
  
- **Begrænsede porte:** 4.000 til operativsystemet

- **Portforbrug ved spidsbelastning:** 6 pr. enhed

- **Spidsbelastningsfaktor:** 4

Derefter er det maksimale antal understøttede enheder bag en enkelt offentlig IP-adresse = (64.000 - 4.000)/(6 + 4) = 6.000
  
Med udgivelsen af Office 365-hostingpakken, der er inkluderet i opdateringerne fra september 2011 til Microsoft Office Outlook 2007 eller november 2011 til Microsoft Outlook 2010 eller en nyere opdatering, antallet af forbindelser fra Outlook (begge Office Outlook 2007 med Service Pack 2 og Outlook 2010) til Exchange kan være op til 2. Du skal tage faktorer i de forskellige operativsystemer, brugeradfærd osv. for at bestemme det mindste og maksimale antal porte, som dit netværk kræver ved spidsbelastning.
  
Hvis du vil understøtte flere enheder bag en enkelt offentlig IP-adresse, skal du følge trinnene beskrevet for at vurdere det maksimale antal enheder, der kan understøttes:
  
Overvåg netværkstrafikken for at bestemme portforbruget pr. klient ved spidsbelastning. Du skal indsamle disse data:
  
- Fra flere forskellige steder
    
- Fra flere enheder
    
- På flere tidspunkter
    
Brug den foregående formel til at beregne det maksimale antal brugere pr. IP-adresse, der kan understøttes i deres miljø.
  
Der er forskellige metoder til at distribuere klientbelastning på tværs af flere offentlige IP-adresser. Tilgængelige strategier afhænger af funktionerne i virksomhedens gatewayløsning. Den nemmeste løsning er at inddele brugerens adresseområde og "tildele" et antal IP-adresser til hver gateway. En anden mulighed er, at mange gatewayenheder giver mulighed for at bruge en gruppe af IP-adresser. Fordelen ved adressepuljen er, at det er meget mere dynamisk og mindre tilbøjelig til at kræve justering, efterhånden som brugerbasen vokser.
  
## <a name="see-also"></a>Se også

[Administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Office 365 ofte stillede spørgsmål om slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
