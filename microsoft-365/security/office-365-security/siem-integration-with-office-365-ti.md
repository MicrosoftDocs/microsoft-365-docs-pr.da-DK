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
description: Integrer din organisations SIEM-server med Microsoft Defender Office 365 og relaterede trusselshændelser i Office 365 API'en Activity Management.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3dbb175ba169c9bb8f4d7240d59d9886391167c3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587326"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>SIEM-integration med Microsoft Defender for Office 365

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Hvis din organisation bruger en sikkerhedsoplysninger og begivenhedsstyringsserver (SIEM), kan du integrere Microsoft Defender for Office 365 med din SIEM-server. Du kan konfigurere denne integration ved hjælp af Office 365 [API'en Aktivitetsstyring](/office/office-365-management-api/office-365-management-activity-api-reference).

SIEM-integration giver dig mulighed for at få vist oplysninger, f.eks malware eller phish, der er registreret af Microsoft Defender Office 365, i dine SIEM-serverrapporter.

- Hvis du vil se et eksempel på SIEM-integration med Microsoft Defender for Office 365, skal du se Tech Community-bloggen: Forbedr effektiviteten af din [SOC med Defender til Office 365 og O365 Management API](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Du kan få mere at vide Office 365 administrations-API'er i [Oversigt Office 365 Administrations-API'er](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>Sådan fungerer SIEM-integration

Den Office 365 API til aktivitetsstyring henter oplysninger om bruger-, administrator-, system- og politikhandlinger og -hændelser fra organisationens Microsoft 365 og Azure Active Directory aktivitetslogfiler. Hvis din organisation har Microsoft Defender Office 365 Plan 1 eller 2 eller Office 365 E5, kan du bruge [microsoft Defender Office 365 skema.](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema)

For nylig blev hændelser fra automatiseret undersøgelse og svarfunktioner i [Microsoft Defender Office 365 Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) føjet til Office 365 Management Activity API. Ud over at inkludere data om centrale undersøgelsesoplysninger som id, navn og status indeholder API'en også omfattende oplysninger om undersøgelseshandlinger og enheder.

SIEM-serveren eller et andet lignende system forespørger arbejdsmængden **audit.general** for at få adgang til registreringshændelser. Du kan få mere at vide [under Introduktion til Office 365 administrations-API'er](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Enum: AuditLogRecordType - Type: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

Følgende tabel opsummerer værdierne for **AuditLogRecordType**, der er relevante for Microsoft Defender Office 365 hændelser:<br/><br/>

| Værdi | Medlemsnavn | Beskrivelse |
|---|---|---|
| 28| ThreatIntelligence | Phishing- og malwarehændelser fra Exchange Online Protection og Microsoft Defender til Office 365. |
| 41| ThreatIntelligenceUrl | Pengeskab Links's time of block og bloker tilsidesættelseshændelser fra Microsoft Defender Office 365. |
| 47| ThreatIntelligenceAtpContent | Phishing- og malwarehændelser for filer i SharePoint Online, OneDrive for Business og Microsoft Teams fra Microsoft Defender til Office 365. |
| 64| AirInvestigation | Automatiserede undersøgelses- og svarhændelser, f.eks. undersøgelsesoplysninger og relevante artefakter, fra Microsoft Defender Office 365 Plan 2. |

> [!IMPORTANT]
> Du skal have enten den globale administrator- eller sikkerhedsadministratorrolle tildelt på Microsoft 365 Defender-portalen for at konfigurere SIEM-integration med Microsoft Defender Office 365. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).
>
> Overvågningslogføring skal være aktiveret for dit Microsoft 365 miljø. Se Slå søgning i overvågningslog til [eller fra for at få hjælp til dette](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Se også

[Office 365 trusselsundersøgelse og -svar](office-365-ti.md)

[Automatiseret undersøgelse og svar (AIR) i Office 365](automated-investigation-response-office.md)