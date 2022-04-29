---
title: SIEM-integration med Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: ''
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: Integrer din organisations SIEM-server med Microsoft Defender for Office 365 og relaterede trusselshændelser i API'en til Office 365 Activity Management.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2ffa1e59f368af4b3e99cee9939ed0ead0cc686e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130992"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>SIEM-integration med Microsoft Defender for Office 365

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Hvis din organisation bruger en SIEM-server (security information and event management), kan du integrere Microsoft Defender for Office 365 med din SIEM-server. Du kan konfigurere denne integration ved hjælp af [API'en Office 365 Activity Management](/office/office-365-management-api/office-365-management-activity-api-reference).

MED SIEM-integration kan du få vist oplysninger, f.eks. malware eller phish, der er registreret af Microsoft Defender for Office 365, i dine SIEM-serverrapporter.

- Hvis du vil se et eksempel på SIEM-integration med Microsoft Defender for Office 365, skal du se [Tech Community-bloggen: Gør din SOC mere effektiv med Defender for Office 365 og O365 Management API](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Hvis du vil vide mere om API'er til administration af Office 365, skal du se [oversigten over API'er til administration af Office 365](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>Sådan fungerer SIEM-integration

API'en til Office 365 activity management henter oplysninger om bruger-, administrator-, system- og politikhandlinger og -hændelser fra organisationens Microsoft 365 og Azure Active Directory aktivitetslogge. Hvis din organisation har Microsoft Defender for Office 365 Plan 1 eller 2 eller Office 365 E5, kan du bruge [skemaet Microsoft Defender for Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

For nylig blev hændelser fra automatiserede undersøgelses- og svarfunktioner i [Microsoft Defender for Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) føjet til API'en for Office 365 Management Activity. Ud over at inkludere data om centrale undersøgelsesoplysninger, f.eks. id, navn og status, indeholder API'en også oplysninger på højt niveau om undersøgelseshandlinger og enheder.

SIEM-serveren eller et andet lignende system forespørger **den generelle arbejdsbelastning** for at få adgang til registreringshændelser. Du kan få mere at vide under [Kom i gang med api'er til administration af Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Enum: AuditLogRecordType – Type: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

I følgende tabel opsummeres værdierne for **AuditLogRecordType**, der er relevante for Microsoft Defender for Office 365 hændelser:<br/><br/>

| Værdi | Medlemsnavn | Beskrivelse |
|---|---|---|
| 28| ThreatIntelligence | Phishing- og malwarehændelser fra Exchange Online Protection og Microsoft Defender for Office 365. |
| 41| ThreatIntelligenceUrl | Pengeskab Links blokeringstidspunkt og -blokeringshændelser fra Microsoft Defender for Office 365. |
| 47| ThreatIntelligenceAtpContent | Phishing- og malwarehændelser for filer i SharePoint Online, OneDrive for Business og Microsoft Teams fra Microsoft Defender for Office 365. |
| 64| AirInvestigation | Automatiserede undersøgelses- og svarhændelser, f.eks. undersøgelsesoplysninger og relevante artefakter, fra Microsoft Defender for Office 365 Plan 2. |

> [!IMPORTANT]
> Du skal enten have tildelt rollen global administrator eller sikkerhedsadministrator på Microsoft 365 Defender-portalen for at konfigurere SIEM-integration med Microsoft Defender for Office 365. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).
>
> Overvågningslogføring skal være aktiveret for dit Microsoft 365 miljø. Hvis du vil have hjælp til dette, skal du se [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Se også

[Office 365 trusselsundersøgelse og -reaktion](office-365-ti.md)

[Automatiseret undersøgelse og reaktion (AIR) i Office 365](automated-investigation-response-office.md)
