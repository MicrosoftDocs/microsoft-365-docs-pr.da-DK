---
title: Avanceret jagteksemem på Microsoft Defender Office 365
description: Kom i gang med at søge efter mailtrusler ved hjælp af avanceret jagt
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 04e4fd2267cc3774e9a816539f0de044ae988dfb
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/30/2021
ms.locfileid: "63606589"
---
# <a name="advanced-hunting-example-for-microsoft-defender-for-office-365"></a>Avanceret jagteksemem på Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Vil du i gang med at søge efter mailtrusler ved hjælp af avanceret jagt? Prøv dette:

Afsnittet [Introduktion i](/microsoft-365/security/office-365-security/defender-for-office-365#getting-started) artiklen [Microsoft Defender for Office 365 tidligere konfiguration](/microsoft-365/security/office-365-security/defender-for-office-365) har logiske dele af den tidlige konfiguration, der ser sådan ud:

1. Konfigurer alt med "Anti" i navnet.
   - Antimalware
   - Antiphishing
   - Antispam
2. Konfigurer alt med "Pengeskab" i navnet.
   - Sikre links
   - Pengeskab vedhæftede filer
3. Forsvar arbejdsbelastningerne (f.eks. SharePoint Online, OneDrive og Teams).
4. Beskyt med automatisk tømning uden time.

Sammen med et [link til](../office-365-security/protect-against-threats.md) at hoppe lige ind og komme i gang med konfigurationen på Dag 1.

Det sidste trin i **Introduktionen er** at beskytte brugere med automatisk **tømning** uden time (også kaldet ZAP). Det kan være meget vigtigt at vide, om dine bestræbelser på at ZAP en mistænkelig eller ondsindet mail efter levering er lykkedes.

Hurtig navigation til Kusto-forespørgselssprog for at lede efter problemer er en fordel ved at konvergere disse to sikkerhedscentre. Sikkerhedsteams kan overvåge ZAP-misser ved at tage deres næste [skridt her](https://security.microsoft.com/advanced-hunting) under **Jagt på** \> **avanceret jagt**.

1. Klik på Forespørgsel på siden Avanceret **jagt**.
1. Kopiér forespørgslen nedenfor til forespørgselsvinduet.
1. Vælg **Kør forespørgsel**.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfullyconverge-2-endpoints-new.png
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

:::image type="content" source="../../media/ah-query-example-new.png" alt-text="The Advanced hunting page (under Hunting) with Query selected at the top of the query panel, and running a Kusto query to capture ZAP actions over the last 7 days." lightbox="../../media/ah-query-example-new.png":::

Dataene fra denne forespørgsel vises i resultatpanelet under selve forespørgslen. Resultaterne indeholder oplysninger som f.eks. 'DeviceName', 'AccountDisplayName' og 'ZapTime' i et resultatsæt, der kan tilpasses. Resultaterne kan også eksporteres for dine poster. Hvis forespørgslen er en, du skal bruge igen, skal du vælge **Gem** >  Gem som og føje forespørgslen til din liste over forespørgsler, delte forespørgsler eller communityforespørgsler.

## <a name="related-information"></a>Relaterede oplysninger
- [Avancerede bedste fremgangsmåder på jagt](advanced-hunting-best-practices.md)
- [Oversigt – Avanceret jagt](advanced-hunting-overview.md)
