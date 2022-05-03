---
title: Reager på en kompromitteret connector i Microsoft 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Få mere at vide om, hvordan du genkender og reagerer på en kompromitteret connector i Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 50caf98bec9d918dd3ff1bcb076a080b123a357a
ms.sourcegitcommit: 4d6a8e9d69a421d6c293b2485a8aa5e806b71616
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65182639"
---
# <a name="respond-to-a-compromised-connector"></a>Besvar en kompromitteret forbindelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**

- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Forbindelser bruges til at aktivere mailflow mellem Microsoft 365- eller Office 365- og mailservere, som du har i dit lokale miljø. Du kan få flere oplysninger under [Konfigurer mailflow ved hjælp af connectors i Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

En kompromitteret indgående connector defineres som når en uautoriseret person enten anvender ændringer på en eksisterende indgående connector eller opretter en ny indgående connector i en Microsoft 365 lejer med det formål at sende spam eller phish-mails.  

## <a name="detect-a-compromised-connector"></a>Registrer en kompromitteret connector

Her er nogle af egenskaberne for en kompromitteret connector:

- Pludselig stigning i mængden af udgående post. 

- Der er uoverensstemmelse mellem P1- og P2-afsendere i udgående mails. Du kan finde flere oplysninger om afsendere af P1 og P2 under [Sådan validerer EOP fra-adressen for at forhindre phishing](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

- Udgående mails, der er sendt fra et domæne, som ikke er klargjort eller registreret. 

- Connectoren er blokeret, så der ikke kan sendes videresendelsesmails. 

- Tilstedeværelsen af en indgående connector blev ikke oprettet af den ønskede bruger eller administratoren. 

- Uautoriserede ændringer i eksisterende connectorkonfiguration, f.eks. navn, domænenavn og IP-adresse. 

- En nyligt kompromitteret administratorkonto. Bemærk, at du kun kan redigere connectorkonfigurationen, hvis du har administrativ adgang. 

## <a name="secure-and-restore-email-function-to-a-suspected-compromised-connector"></a>Sikker og gendan mailfunktion til en formodet kompromitteret connector

Du skal fuldføre alle følgende trin for at få adgang til connectoren igen. Disse trin hjælper dig med at fjerne eventuelle bagdørsposter, der kan være blevet føjet til din connector.

### <a name="step-1-identify-if-an-inbound-connector-has-been-compromised"></a>Trin 1: Identificer, om en indgående connector er blevet kompromitteret 

#### <a name="review-recent-suspicious-connector-traffic-or-related-messages"></a>Gennemse den seneste mistænkelige connectortrafik eller relaterede meddelelser

Hvis du har [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md), skal du gå direkte til https://security.microsoft.com/threatexplorer. 

1. Vælg **Connector**, indsæt **Forbindelsesnavn**, vælg datointerval, og klik derefter på **Opdater**. 

    :::image type="content" source="../../media/connector-compromise-explorer.png" alt-text="Visning af indgående connectoroversigt" lightbox="../../media/connector-compromise-explorer.png":::

2. Identificer, om der er en unormal stigning eller et fald i mailtrafikken.

    :::image type="content" source="../../media/connector-compromise-abnormal-spike.png" alt-text="Antal mails, der er leveret til mappen Uønsket mail" lightbox="../../media/connector-compromise-abnormal-spike.png":::

3. Identificere: 

    - Hvis **Afsenders IP** stemmer overens med din organisations ip-adresse i det lokale miljø. 

    - Hvis der for nylig blev sendt et betydeligt antal mails til mappen **Uønsket mail** . Dette er en god indikator for, at en kompromitteret connector bruges til at sende spam. 

    - Hvis modtagerne er dem, som din organisation normalt forbliver i kontakt med. 

    :::image type="content" source="../../media/connector-compromise-sender-ip.png" alt-text="Afsender-IP og organisationens IP-adresse i det lokale miljø" lightbox="../../media/connector-compromise-sender-ip.png":::

Hvis du har [Microsoft Defender for Office 365 Plan 1](defender-for-office-365.md) eller [Exchange Online Protection](exchange-online-protection-overview.md), skal du gå til https://admin.exchange.microsoft.com/#/messagetrace. 

1. Åbn beskeden **om mistænkelig forbindelsesaktivitet** i https://security.microsoft.com/alerts.  

2. Vælg en aktivitet under **Aktivitetsliste**, og kopiér mistænkeligt **connectordomæne** og **IP-adresse** , der er registreret i beskeden.

    :::image type="content" source="../../media/connector-compromise-outbound-email-details.png" alt-text="Connector kompromitterer oplysninger om udgående mail" lightbox="../../media/connector-compromise-outbound-email-details.png":::
    
3. Søg ved hjælp af **connectordomæne** og **IP-adresse** i [**Meddelelsessporing**](https://admin.exchange.microsoft.com/#/messagetrace). 

    :::image type="content" source="../../media/connector-compromise-new-message-trace.png" alt-text="Nyt pop op-vindue til meddelelsessporing" lightbox="../../media/connector-compromise-new-message-trace.png":::
    
4. Identificer følgende i søgeresultaterne **for meddelelsessporing** : 

    - Hvis et betydeligt antal mails for nylig blev markeret som **FilteredAsSpam**. Dette er en god indikator for, at en kompromitteret connector bruges til at sende spam. 

    - Hvis modtagerne er dem, som din organisation normalt forbliver i kontakt med. 

    :::image type="content" source="../../media/connector-compromise-message-trace-results.png" alt-text="Nye søgeresultater for meddelelsessporing" lightbox="../../media/connector-compromise-message-trace-results.png":::

#### <a name="investigate-and-validate-connector-related-activity"></a>Undersøg og valider forbindelsesrelateret aktivitet 

Brug følgende kommandolinje i PowerShell til at undersøge og validere forbindelsesrelateret aktivitet af en bruger i overvågningsloggen. Du kan finde flere oplysninger under [Brug et PowerShell-script til at søge i overvågningsloggen](/compliance/audit-log-search-script). 

```powershell
Search-UnifiedAuditLog -StartDate "<ExDateTime>" -EndDate "<ExDateTime>" -Operations "New-InboundConnector", "Set-InboundConnector", "Remove-InboundConnector
```

### <a name="step-2-review-and-revert-unauthorized-changes-in-a-connector"></a>Trin 2: Gennemse og gendan uautoriserede ændringer i en connector 

1. https://admin.exchange.microsoft.com/Log på . 

2. Gennemse og gendan uautoriserede connector-ændringer. 

### <a name="step-3-unblock-the-connector-to-re-enable-mail-flow"></a>Trin 3: Fjern blokeringen af connectoren for at aktivere mailflowet igen 

1. https://security.microsoft.com/restrictedentitiesLog på . 

2. Vælg den begrænsede connector for at fjerne blokeringen af forbindelsen. 

### <a name="step-4-investigate-and-remediate-potentially-compromised-administrative-user-account"></a>Trin 4: Undersøg og afhjælp potentielt kompromitteret administrativ brugerkonto

Hvis en bruger med en uautoriseret forbindelsesaktivitet identificeres, kan du undersøge denne bruger for potentielt kompromitteret. Du kan få flere oplysninger under [Besvarelse af en kompromitteret mailkonto](responding-to-a-compromised-email-account.md).

## <a name="more-information"></a>Flere oplysninger

- [Fjern blokerede forbindelser](remove-blocked-connectors.md)
- [Fjern blokerede brugere](removing-user-from-restricted-users-portal-after-spam.md)
