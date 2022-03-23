---
title: Sådan fungerer DLP med Security & Compliance Center & Exchange Administration
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a7e4342a-a0a1-4b43-b166-3d7eecf5d2fd
description: Få mere at vide om, hvordan DLP i Security & Compliance Center fungerer sammen med DLP- og mailflowregler (transportregler) Exchange Administration.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 90706b3dad55ff84d274656673f9a60dbd71e35f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63587491"
---
# <a name="how-dlp-works-between-the-microsoft-365-compliance-center-and-exchange-admin-center"></a>Sådan fungerer DLP Microsoft 365 Compliance Center Exchange Administration

I Microsoft 365 kan du oprette en politik til forebyggelse af datatab (DLP) i to forskellige administrationscentre:
  
- I **Microsoft 365 Compliance Center** kan du oprette en enkelt DLP-politik for at beskytte indhold i SharePoint, OneDrive, Exchange, Teams og nu slutpunktsenheder. Vi anbefaler, at du opretter en DLP-politik her. Du kan finde flere oplysninger [under Reference til forebyggelse af datatab](data-loss-prevention-policies.md).
    
- I <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">administrationen Exchange kan</a> du oprette en DLP-politik for kun at beskytte indhold Exchange. Denne politik kan Exchange regler for mailflow (også kaldet transportregler), så den har flere specifikke muligheder for at håndtere mail. Du kan få mere [at vide under DLP Exchange Administration](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
DLP-politik, der er oprettet i disse administrationscentre, arbejder side om side – i dette emne forklares det hvordan.
  
![DLP-sider i Security and Compliance Center Exchange Administration.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Sådan fungerer DLP i & Compliance Center med DLP og regler for mailflow Exchange Administration

Når du har oprettet en DLP-politik i Security & Compliance Center, installeres politikken på alle de placeringer, der er inkluderet i politikken. Hvis politikken omfatter Exchange Online, synkroniseres politikken der og håndhæves på præcis samme måde som en DLP-politik, der er oprettet <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. 
  
Hvis du har oprettet DLP-politikker i Exchange Administration, vil disse politikker fortsat fungere side om side med eventuelle politikker for mails, som du opretter i Security & Compliance Center. Men bemærk, at regler, der er oprettet Exchange Administration, har forrang. Alle Exchange regler for mailflow behandles først, og derefter behandles DLP-reglerne fra Security & Compliance Center.
  
Det betyder, at:
  
- Meddelelser, der er blokeret Exchange regler for mailflow, bliver ikke scannet af DLP-regler, der er oprettet i Security & Compliance Center.

- Meddelelser, der er sat i karantæne Exchange regler for mailflow, eller andre filtre, der køres før DLP, scannes ikke af DLP.
    
- Hvis en regel for Exchange-mailflow ændrer en meddelelse på en måde, der får den til at matche en DLP-politik i Security & Compliance Center – f.eks. tilføjelse af eksterne brugere – registrerer DLP-reglerne dette og håndhæver politikken efter behov.
    
Bemærk også, Exchange regler for mailflow, der bruger handlingen "stands behandling", ikke påvirker behandlingen af DLP-regler i Security & Compliance Center – de behandles stadig.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Politiktip i Sikkerheds- & i forhold Exchange Administration

Politiktip kan enten fungere med DLP-politikker og regler for mailflow, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> Administration, eller med DLP-politikker, der er oprettet i Security & Compliance Center, men ikke begge dele. Dette skyldes, at disse politikker er gemt på forskellige placeringer, men politiktip kan kun trækkes fra en enkelt placering.
  
Hvis du har konfigureret politiktip i Exchange Administration, vises politiktip, som du konfigurerer i Security & Compliance Center, ikke for brugere i Outlook på internettet og Outlook 2013 og senere, før du deaktiverer tip i Exchange Administration. Dette sikrer, at dine Exchange regler for mailflow fortsat fungerer, indtil du vælger at skifte til Security & Compliance Center.
  
Bemærk, at mens politiktip kun kan trækkes fra et enkelt sted, sendes der altid mailbeskeder, også selvom du bruger DLP-politikker i både Security & Compliance Center og Exchange Administration.
