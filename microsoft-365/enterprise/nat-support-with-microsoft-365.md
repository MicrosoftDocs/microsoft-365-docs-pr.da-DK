---
title: NAT-understøttelse med Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Denne artikel indeholder oplysninger om, hvordan du tilnærmer det antal klienter, du kan bruge pr. IP-adresse i din organisation, ved hjælp af NAT.
ms.openlocfilehash: 71c9d54ddf88d9b69c890609fea7ece8cac0de33
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097376"
---
# <a name="nat-support-with-office-365"></a>NAT-understøttelse med Office 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Tidligere foreslog vejledning, at det maksimale antal Exchange klienter, du skal bruge pr. IP-adresse til at oprette forbindelse til Office 365, var ca. 2.000 klienter pr. netværksport.
  
## <a name="why-use-nat"></a>Hvorfor bruge NAT?

Ved at bruge NAT kan tusindvis af personer på et virksomhedsnetværk "dele" nogle få offentligt tilgængelige IP-adresser.
  
De fleste virksomhedsnetværk bruger privat (RFC1918) IP-adresseplads. Privat adresseplads tildeles af IANA (Internet Assigned Numbers Authority) og er udelukkende beregnet til netværk, der ikke dirigeres direkte til og fra det globale internet.
  
For at give internetadgang til enheder på et privat IP-adresseområde bruger organisationer gatewayteknologier som firewalls og proxyer, der leverer NAT-tjenester (Network Address Translation) eller PAT (Port Address Translation). Disse gateways får trafik fra interne enheder til internettet (herunder Office 365) til at komme fra en eller flere offentligt tilgængelige IP-adresser. Hver udgående forbindelse fra en intern enhed oversættes til en anden TCP-kildeport på den offentlige IP-adresse. 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a>Hvorfor skal du have så mange forbindelser åbne for at Office 365 på samme tid?

Outlook kan åbne otte eller flere forbindelser (i situationer, hvor der er tilføjelsesprogrammer, delte kalendere, postkasser osv.). Da der højst er 64.000 tilgængelige porte på en Windows-baseret NAT-enhed, kan der højst være 8.000 brugere bag en IP-adresse, før portene er opbrugt. Bemærk, at hvis kunderne bruger ikke-Windows OS-baserede enheder til NAT, afhænger det samlede antal tilgængelige porte af, hvilken NAT-enhed eller -software der bruges. I dette scenarie kan det maksimale antal porte være mindre end 64.000. Tilgængeligheden af porte påvirkes også af andre faktorer, f.eks. Windows begrænsning af 4.000 porte til eget brug, hvilket reducerer det samlede antal tilgængelige porte til 60.000. Der kan være andre programmer, f.eks. Internet Explorer, der kan oprette forbindelse på samme tid, hvilket kræver yderligere porte.
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a>Beregning af det maksimale antal understøttede enheder bag en enkelt offentlig IP-adresse med Office 365

Hvis du vil bestemme det maksimale antal enheder bag en enkelt offentlig IP-adresse, skal du overvåge netværkstrafik for at bestemme det maksimale portforbrug pr. klient. Der skal også bruges en spidsbelastningsfaktor til portforbruget (minimum 4). 
  
 **Brug følgende formel til at beregne antallet af understøttede enheder pr. IP-adresse:**
  
Maksimalt understøttede enheder bag en enkelt offentlig IP-adresse = (64.000 – begrænsede porte)/(Spidsbelastning af portforbrug + spidsfaktor)
  
 **Hvis følgende f.eks. var sandt:**
  
- **Begrænsede porte:** 4.000 til operativsystemet

- **Spidsportforbrug:** 6 pr. enhed

- **Topfaktor:** 4

Derefter det maksimale antal understøttede enheder bag en enkelt offentlig IP-adresse = (64.000 - 4.000)/(6 + 4) = 6.000
  
Med udgivelsen af Office 365 hostingpakke, der er inkluderet i opdateringerne fra september 2011 for Microsoft Office Outlook 2007 eller november 2011 for Microsoft Outlook 2010 eller en senere opdatering, antallet af forbindelser fra Outlook (begge Office Outlook 2007 med Service Pack 2 og Outlook 2010) til Exchange kan være så få som 2. Du skal indregne de forskellige operativsystemer, brugeradfærd osv. for at bestemme det minimale og maksimale antal porte, som dit netværk kræver ved spidsbelastning.
  
Hvis du vil understøtte flere enheder bag en enkelt offentlig IP-adresse, skal du følge de trin, der er beskrevet, for at vurdere det maksimale antal enheder, der kan understøttes:
  
Overvåg netværkstrafik for at bestemme spidsbelastningsforbrug pr. klient. Du skal indsamle disse data:
  
- Fra flere placeringer
    
- Fra flere enheder
    
- Flere gange
    
Brug den foregående formel til at beregne det maksimale antal brugere pr. IP-adresse, der kan understøttes i deres miljø.
  
Der er forskellige metoder til distribution af klientbelastningen på tværs af flere offentlige IP-adresser. Tilgængelige strategier afhænger af funktionerne i virksomhedens gatewayløsning. Den nemmeste løsning er at segmentere din brugeradresseplads og statisk "tildele" et antal IP-adresser til hver gateway. Et andet alternativ, som mange gatewayenheder tilbyder, er muligheden for at bruge en pulje af IP-adresser. Fordelen ved adressepuljen er, at det er meget mere dynamisk og mindre sandsynligt, at det kræver justering, efterhånden som din brugerbase vokser.
  
## <a name="see-also"></a>Se også

[Administrere Office 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Ofte stillede spørgsmål om Office 365 slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
