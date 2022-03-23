---
title: Brug navngivne enheder i dine politikker til forebyggelse af datatab (forhåndsvisning)
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
description: Brug disse procedurer til at drage fordel af navngivne enheder i politikkerne til forebyggelse af datatab
ms.openlocfilehash: 5adb410689e597395f1b13152ed62af75fa111d6
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594647"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>Brug navngivne enheder i dine politikker til forebyggelse af datatab (forhåndsvisning)

> [!IMPORTANT]
> Den navngivne enheder-funktion udrulles og vises i din lejer, når den er tilgængelig for dig. Kontrollér for dem i indholdsstifinder og i flowet til forebyggelse af datatab (DLP)-politik. 

Læs Få [mere at vide om navngivne enheder (eksempel),](named-entities-learn.md) før du begynder at bruge dem.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>SKU/abonnementslicenser

Du skal have et af disse abonnementer

- Beskyttelse og styring af oplysninger
- Microsoft 365 E5 Overholdelse
- Office 365 E5
- Microsoft 365 E5

Se tjenestebeskrivelsen for at [få flere licensoplysninger](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Tilladelser

Den konto, du bruger til at oprette og redigere politikker til forebyggelse af datatab (DLP), skal have **tilladelsen DLP Compliance Management** . Få mere at vide under [Giv brugere adgang til Office 365 Overholdelsescenter](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Understøttede placeringer

Du kan bruge navngivne enheds-SIT'er og forbedrede politikker til at registrere og beskytte følsomme elementer på disse placeringer:

- SharePoint websteder
- OneDrive konti
- Teams chat og kanalmeddelelser
- Enheder (Windows 10 slutpunktsenheder)

Navngivne ENHEDS-SIT'er og forbedrede politikker understøttes ikke for:


- Lokale lagre
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Oprette og redigere udvidede politikker

Hvis du vil oprette eller redigere en DLP-politik, skal du bruge fremgangsmåderne i [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Arbejdsbelastninger og tjenester, der understøtter navngivne enheder


- **Microsoft 3655 eDiscovery** understøtter brug af navngivne enheder i Understrate-tjenester.
- **Microsoft Defender til skyapps** understøtter brug af navngivne enheder i politikkerne for Defender til skyapps.
- **Insider Risk Management** understøtter brug af navngivne enheder i Understrate-tjenester.
- **Kommunikationsoverholdelse** understøtter ikke brugen af navngivne enheder Exchange transportregler og data-at-rest.
- **Microsofts styring** af oplysninger (MIG) understøtter ikke brugen af navngivne enheder i Exchange-transportregler og data-at-rest.
 
### <a name="unified-dlp"></a>Samlet DLP

|Arbejdsbelastning/tjenester  |Understøttelse af offentlig eksempelvisning for navngivne enheder  |
|---------|---------|
|Office tip til politik for Win32-klienter    |understøttes ikke  |
|Office til WAC-klienter    |understøttet         |
|Tip til OWA-politik     |understøttes ikke         |
|Outlook politiktip     |understøttes ikke |
|Slutpunkter (Windows 10 enheder)     |understøttet  |
|Exchange transportregler     |understøttes ikke |
|OneDrive for Business data-at-rest     |understøttet         |
|SharePoint Online data-at-rest     |understøttet         |
|Teams data-at-rest     |understøttet         |
|E-mail-data-at-rest     |understøttes ikke         |
|Microsoft Defender til skyapps     |understøttet         |

### <a name="autolabeling"></a>Automatisk mærkning

|Arbejdsbelastning/tjenester |Understøttelse af offentlig eksempelvisning for navngivne enheder  |
|---------|---------|
|Office Win32-klienter offline   |understøttet, skal brugeren vælge etiket og anvende manuelt |
|Online Office Win32-klienter online|understøttet med gammel tillidsplan |
|Outlook online   |understøttet med gammel tillidsplan  |
|Office WAC-klient     |understøttet |
|OWA     |understøttet |
|Exchange transport     |understøttes ikke |
|OneDrive for Business data-at-rest     |understøttet |
|SharePoint Online data-at-rest|understøttet|
|Azure Information Protection -scanner (AIP)|understøttes ikke|

## <a name="known-issues"></a>Kendte problemer

|Problem  |Virkning  |
|---------|---------|
|Tip til DLP-politik (OWA-, Outlook-, Office Win32-klienter)     |   Politiktip med enhedsbetingelse resulterer i "intet match"      |
| Understøttelse af asiatiske sprog for personnavn (kinesisk, japansk, koreansk)    | Navngivne enheder, der kun understøttes til latinske tegnsæt (det vil sige, at kanji ikke understøttes) til personens navn        |
|Lokale lagre    | Understøttes ikke som en arbejdsbelastning|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>Du kan finde flere oplysninger
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Få mere at vide om navngivne enheder (eksempel)](named-entities-learn.md).
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
