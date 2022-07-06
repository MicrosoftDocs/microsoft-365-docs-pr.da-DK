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
description: Få mere at vide om, hvordan DLP i Security & Compliance Center fungerer sammen med DLP- og mailflowregler (transportregler) i Exchange Administration.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: fa77bf84ff8ef2b4f194f45b9a29b49f6b662a70
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641400"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>Sådan fungerer DLP mellem Compliance Center og Exchange Administration

I Microsoft Purview kan du oprette en DLP-politik (forebyggelse af datatab) i to forskellige administrationer:
  
- I **Microsoft Purview-compliance-portal** kan du oprette en enkelt DLP-politik for at beskytte indhold i SharePoint, OneDrive, Exchange, Teams og nu Slutpunktsenheder. Vi anbefaler, at du opretter en DLP-politik her. Du kan få flere oplysninger under [Reference til forebyggelse af datatab](data-loss-prevention-policies.md).
    
- I <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> kan du oprette en DLP-politik for kun at beskytte indhold i Exchange. Denne politik kan bruge Regler for Exchange-mailflow (også kaldet transportregler), så den har flere indstillinger, der er specifikke for håndtering af mail. Du kan få flere oplysninger under [DLP i Exchange Administration](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
DLP-politikker, der oprettes i disse administrationscentre, arbejder side om side – i denne artikel forklares det, hvordan.
 
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Sådan fungerer DLP i Security & Compliance Center med regler for DLP og mailflow i Exchange Administration

Når du har oprettet en DLP-politik i Security & Compliance Center, installeres politikken på alle de placeringer, der er inkluderet i politikken. Hvis politikken indeholder Exchange Online, synkroniseres politikken der og gennemtvinges på præcis samme måde som en DLP-politik, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. 
  
Hvis du har oprettet DLP-politikker i Exchange Administration, vil disse politikker fortsat fungere side om side med alle politikker for mail, som du opretter i Security & Compliance Center. Men bemærk, at regler, der er oprettet i Exchange Administration, har forrang. Alle exchange-regler for mailflow behandles først, og derefter behandles DLP-reglerne fra Security & Compliance Center.
  
Det betyder:
  
- Meddelelser, der er blokeret af exchange-regler for mailflow, bliver ikke scannet af DLP-regler, der er oprettet i Security & Compliance Center.
- Meddelelser, der er sat i karantæne af Exchange-regler for mailflow, eller andre filtre, der kører før DLP, scannes ikke af DLP. 
- Hvis en regel for Et Exchange-mailflow ændrer en meddelelse på en måde, der får den til at stemme overens med en DLP-politik i Security & Compliance Center, f.eks. tilføjelse af eksterne brugere, registrerer DLP-reglerne den og gennemtvinger politikken efter behov.
    
Bemærk også, at regler for Exchange-mailflow, der bruger handlingen "stop behandling", ikke påvirker behandlingen af DLP-regler i Security & Compliance Center – de behandles stadig.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Tip til politikker i Security & Compliance Center vs. Exchange Administration

Politiktips kan enten fungere med DLP-politikker og regler for mailflow, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>, eller med DLP-politikker, der er oprettet i Security & Compliance Center, men ikke begge dele. Det skyldes, at disse politikker er gemt forskellige steder, men politiktips kan kun hentes fra en enkelt placering.
  
Hvis du har konfigureret politiktips i Exchange Administration, vises de politiktip, du konfigurerer i Security & Compliance Center, ikke for brugere i Outlook på internettet og Outlook 2013 og nyere, før du deaktiverer tipene i Exchange Administration. Dette sikrer, at dine aktuelle regler for Exchange-mailflow fortsat fungerer, indtil du vælger at skifte til Security & Compliance Center.
  
>[!Note]
>Selvom politiktips kun kan hentes fra en enkelt placering, sendes der altid mailmeddelelser, selvom du bruger DLP-politikker i både Security & Compliance Center og Exchange Administration.
