---
title: Udvid avanceret jagtdækning med de rigtige indstillinger
description: Kontrollér overvågningsindstillingerne på dine Windows og andre indstillinger for at sikre, at du får de mest omfattende data i avanceret jagt
keywords: avanceret jagt, hændelse, pivot, enhed, overvågningsindstillinger, administration af brugerkonti, administration af sikkerhedsgrupper, trusselssøgning, cybertrusel, søgning, forespørgsel, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dd61fa434eaf2130f0fcb0f28df9a20d696e04ec
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/02/2021
ms.locfileid: "63597505"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Udvid avanceret jagtdækning med de rigtige indstillinger

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

[Avanceret](advanced-hunting-overview.md) jagt afhænger af data, der kommer fra forskellige kilder, herunder dine enheder, Office 365 arbejdsområder, Azure AD og Microsoft Defender til identitet. For at få så mange data som muligt skal du sørge for, at du har de korrekte indstillinger i de tilsvarende datakilder.

## <a name="advanced-security-auditing-on-windows-devices"></a>Avanceret sikkerhedsrevision på Windows enheder
Slå disse avancerede overvågningsindstillinger til for at sikre, at du får data om aktiviteter på dine enheder, herunder administration af lokale konti, lokal administration af sikkerhedsgrupper og oprettelse af tjenester.

| Data | Beskrivelse | Skematabel | Sådan konfigurerer du |
| --- | --- | --- | --- |
| Kontostyring | Begivenheder registreret som forskellige værdier `ActionType` , der angiver oprettelse, sletning og andre kontorelaterede aktiviteter | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Installere en avanceret politik for sikkerhedskontrol: [Overvågning af administration af brugerkonti](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [Få mere at vide om avancerede politikker for sikkerhedskontrol](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Administration af sikkerhedsgrupper | Hændelser registreret som forskellige værdier `ActionType` , der angiver oprettelse af lokale sikkerhedsgrupper og andre lokale gruppeadministrationsaktiviteter | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Installere en avanceret politik for sikkerhedskontrol: [Administration af sikkerhedsgruppeadministration](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [Få mere at vide om avancerede politikker for sikkerhedskontrol](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Tjenesteinstallation | Hændelser, der er registreret med `ActionType` værdien `ServiceInstalled`, der angiver, at en tjeneste er blevet oprettet | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Installere en avanceret sikkerhedspolitik: [Udvidelsen Overvågningssystem](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [Få mere at vide om avancerede politikker for sikkerhedskontrol](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>Microsoft Defender for Identity-sensor på domænecontrolleren
Hvis du kører Active Directory lokalt, skal du installere Microsoft Defender for Identity-sensoren på domænecontrolleren for at få data til Microsoft Defender for Identity. Når disse data er installeret og konfigureret korrekt, kan de også forsynes med avanceret jagt via Microsoft Defender for Identity og giver et mere gyldigt billede af identitetsoplysninger og hændelser i dit netværk. Disse data forbedrer også muligheden for, at Microsoft Defender for Identity genererer relevante beskeder, som også er dækket af avanceret jagt. 

| Data | Beskrivelse | Skematabel | Sådan konfigurerer du |
| --- | --- | --- | --- |
| Domænecontroller | Data fra Active Directory i det lokale miljø, der er sendt til Microsoft Defender for Identity, og som forbedrer identitetsrelaterede oplysninger, f.eks. kontooplysninger, logonaktivitet og Active Directory-forespørgsler | Flere tabeller, herunder [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) og [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)  | - [Installer Microsoft Defender for Identity-sensoren](/azure-advanced-threat-protection/install-atp-step4)<br>- [Slå relevante Windows begivenheder til](/azure-advanced-threat-protection/configure-event-collection) |

>[!NOTE]
>Nogle tabeller i denne artikel er muligvis ikke tilgængelige i Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)