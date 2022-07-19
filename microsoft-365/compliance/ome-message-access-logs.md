---
title: Krypteret aktivitetslog for meddelelsesportal
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Adgangslogge er tilgængelige for krypterede meddelelser, der hentes via den krypterede meddelelsesportal.
ms.openlocfilehash: 50656d1695d8fc3d6e81de6afc03b3f4e3c5ccee
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "66858515"
---
# <a name="encrypted-message-portal-activity-log-by-microsoft-purview-advanced-message-encryption-preview"></a>Aktivitetslog for krypteret meddelelsesportal af Avanceret meddelelseskryptering i Microsoft Purview (prøveversion)

Adgangslogge er tilgængelige for krypterede meddelelser via den krypterede meddelelsesportal, der gør det muligt for din organisation at bestemme, hvornår meddelelser læses og videresendes af dine eksterne modtagere. Hvis du vil sikre, at logfiler er tilgængelige for eksterne modtagere, skal du anvende en brugerdefineret brandingskabelon på beskyttede mails, der sendes af din organisation til eksterne modtagere, som gennemtvinger en portaloplevelse. Se [Føj organisationens brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md).

## <a name="enabling-message-access-audit-logs-in-powershell"></a>Aktivering af overvågningslogge for meddelelsesadgang i PowerShell

Adgangsloggen kan aktiveres ved hjælp af Exchange Online PowerShell. Parameteren *-EnablePortalTrackingLogs* for Set-IrmConfiguration angiver, om overvågningslogge for at få adgang til den krypterede meddelelsesportal skal aktiveres. Gyldige værdier er:

- $true: Slå overvågningsfunktionen til.
- $false: Slå overvågningsfunktion fra

Eksempel: Set-IrmConfiguration -EnablePortalTrackingLogs-$true

Du kan få mere at vide under [Set-IRMConfiguration (ExchangePowerShell)](/powershell/module/exchange/set-irmconfiguration).

## <a name="message-access-audit-information"></a>Overvågningsoplysninger om meddelelsesadgang

Adgangsloggen indeholder poster for meddelelser, der er sendt via den krypterede meddelelsesportal for følgende aktivitetstyper:

- Tidsstempel og godkendelsesmetode for ekstern brugerlogon
- Eksterne brugere læser meddelelser eller vedhæftede filer
- Download af vedhæftet fil
- mailsvar og videresendelse

Du kan finde flere oplysninger om skemaet for meddelelsesadgangsloggen under [Søg i overvågningsloggen på portalen til overholdelse af angivne standarder](search-the-audit-log-in-security-and-compliance.md#encrypted-message-portal-activities).

## <a name="search-for-events-in-the-message-access-logs"></a>Søg efter hændelser i logfilerne for meddelelsesadgang

Sådan får du vist de hændelser, der registreres i loggene for meddelelsesadgang:

1. I Microsoft Purview-compliance-portal under **Løsninger** skal du vælge **Overvågning**.
1. Under **Søg** skal du klikke på rullelisten for **Aktiviteter** og skrive krypterede aktiviteter på meddelelsesportalen.
1. Under aktiviteter på krypterede meddelelsesportaler skal du vælge de hændelsestyper, der skal bruges i søgningen. Angiv datointervallet for søgningen (standarden er den forrige uge), og du kan eventuelt tilføje en bestemt bruger i din organisation til søgningen. Når du er klar, skal du vælge **Søg**.
1. Vælg en hændelse på listen for at få vist overvågningsegenskaberne.
