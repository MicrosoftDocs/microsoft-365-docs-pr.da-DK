---
title: Brug navngivne enheder i dine politikker til forebyggelse af datatab (prøveversion)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Brug disse procedurer til at drage fordel af navngivne enheder i dine politikker til forebyggelse af datatab
ms.openlocfilehash: 9b3a8899ef4b64c682289e29df19648a00d4f048
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665156"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Brug navngivne enheder i dine politikker til forebyggelse af datatab (prøveversion)

> [!IMPORTANT]
> Funktionen navngivne enheder udrulles og vises i din lejer, når den er tilgængelig for dig. Kontrollér, om de er i Indholdsoversigt og i DLP-flowet (forebyggelse af datatab). 

Læs [mere om navngivne enheder (prøveversion),](named-entities-learn.md) før du begynder at bruge dem.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Du skal have et af disse abonnementer

- Information Protection og styring
- Microsoft 365 E5 Overholdelse
- Office 365 E5
- Microsoft 365 E5

Du kan finde alle licensoplysninger [i tjenestebeskrivelsen](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Tilladelser

Den konto, du bruger til at oprette og redigere DLP-politikker (forebyggelse af datatab), skal have rolletilladelserne **DLP Compliance Management** . Du kan få flere oplysninger under [Giv brugere adgang til Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Understøttede placeringer

Du kan bruge navngivne objekt-SIT'er og forbedrede politikker til at registrere og beskytte følsomme elementer på disse placeringer:

- SharePoint websteder
- OneDrive konti
- Teams chat- og kanalmeddelelser
- Enheder (Windows 10 slutpunktsenheder)

Navngivne objekt-SIT'er og forbedrede politikker understøttes ikke for:


- Lagre i det lokale miljø
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Opret og rediger forbedrede politikker

Hvis du vil oprette eller redigere en DLP-politik, skal du bruge procedurerne i [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Arbejdsbelastninger og tjenester, der understøtter navngivne enheder


- **Microsoft 3655 eDiscovery** understøtter brugen af navngivne enheder i Substrate-tjenester.
- **Microsoft Defender for Cloud Apps** understøtter brugen af navngivne objekter i Defender for Cloud Apps-politikker.
- **Insider Risk Management** understøtter brugen af navngivne objekter i Substrate-tjenester.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Unified DLP

|Arbejdsbelastning/tjenester  |Understøttelse af offentlig prøveversion af navngivne enheder  |
|---------|---------|
|politiktip til Office Win32-klienter    |understøttes ikke  |
|politiktip til Office WAC-klienter    |Understøttes         |
|Tip til OWA-politik     |understøttes ikke         |
|Outlook politiktip     |understøttes ikke |
|Slutpunkter (Windows 10 enheder)     |Understøttes  |
|Exchange transportregler     |understøttes ikke |
|OneDrive for Business hviledata     |Understøttes         |
|SharePoint Online-data-at-rest     |Understøttes         |
|Teams hviledata     |Understøttes         |
|Data-at-rest i mails     |understøttes ikke         |
|Microsoft Defender for Cloud Apps     |Understøttes         |

### <a name="autolabeling"></a>Automatisk navngivning

|Arbejdsbelastning/tjenester |Understøttelse af offentlig prøveversion af navngivne enheder  |
|---------|---------|
|Office Win32-klienter offline   |understøttes, skal brugeren vælge mærkat og anvende det manuelt |
|Online Office Win32-klienter online|understøttet med gamle tillidsskemaer |
|Outlook online   |understøttet med gamle tillidsskemaer  |
|Office WAC-klient     |Understøttes |
|OWA     |Understøttes |
|Exchange transport     |understøttes ikke |
|OneDrive for Business hviledata     |Understøttes |
|SharePoint Online-data-at-rest|Understøttes|
|AIP-scanner (Azure Information Protection)|understøttes ikke|

## <a name="known-issues"></a>Kendte problemer

|Spørgsmål  |Indvirkning  |
|---------|---------|
|Tip til DLP-politik (OWA, Outlook, Office Win32-klienter)     |   Politiktip med objektbetingelse resulterer i "intet match"      |
| Understøttelse af asiatisk sprog for personnavn (kinesisk, japansk, koreansk)    | Navngivne enheder, der kun understøttes for latinsk baserede tegnsæt (dvs. kanji understøttes ikke) for personnavn        |
|Lagre i det lokale miljø    | Understøttes ikke som en arbejdsbelastning|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Yderligere oplysninger
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Få mere at vide om navngivne enheder (prøveversion).](named-entities-learn.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
