---
title: Brug navngivne enheder i DLP-politikker
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
ms.openlocfilehash: 0cdf544eddf873f3bbf761bd613641433dd2da6b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623695"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies"></a>Brug navngivne enheder i dine politikker til forebyggelse af datatab

Læs [Mere om navngivne objekter](named-entities-learn.md) , før du begynder at bruge dem.

## <a name="before-you-begin"></a>Før du begynder

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Du kan finde alle licensoplysninger [i tjenestebeskrivelsen](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>Tilladelser

Den konto, du bruger til at oprette og redigere DLP-politikker (forebyggelse af datatab), skal have rolletilladelserne **DLP Compliance Management** . Du kan få flere oplysninger under [Giv brugere adgang til Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>Understøttede placeringer

Du kan bruge navngivne objekt-SIT'er og forbedrede politikker til at registrere og beskytte følsomme elementer på disse placeringer:

- SharePoint-websteder
- OneDrive-konti
- Teams-chat- og kanalmeddelelser
- Enheder (Windows 10 og 11 slutpunktsenheder)
- Exchange-postkasser
- Microsoft Defender for Cloud Apps

Navngivne objekt-SIT'er og forbedrede politikker understøttes ikke for:

- Lagre i det lokale miljø
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>Opret og rediger forbedrede politikker

Hvis du vil oprette eller redigere en DLP-politik, skal du bruge procedurerne i [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>Arbejdsbelastninger og tjenester, der understøtter navngivne enheder

- **Microsoft 365 eDiscovery** understøtter brugen af navngivne enheder i Substrate-tjenester.
- **Microsoft Defender for Cloud Apps** understøtter brugen af navngivne objekter i Defender for Cloud Apps-politikker på Defender for Cloud Apps-portalen.
- **Insider Risk Management** understøtter brugen af navngivne objekter i Substrate-tjenester.
- **Datastyring** understøtter brugen af navngivne objekter.
- **Præcise datamatch følsomme oplysningstyper** understøtter brugen af navngivne objekter.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>Unified DLP

|Arbejdsbelastning/tjenester  |Understøttelse af navngivne enheder  |
|---------|---------|
|Politiktip til Office Win32-klienter    |Understøttes ikke  |
|Politiktip til Office WAC-klienter    |Understøttes         |
|Tip til OWA-politik     |Understøttes ikke         |
|Tip til Outlook-politik     |Understøttes ikke |
|Slutpunkter (Windows 10 og 11 enheder)     |Understøttes  |
|Exchange-transportregler     |Understøttes |
|OneDrive for Business hviledata     |Understøttes         |
|SharePoint Online-data-at-rest     |Understøttes         |
|Teams-data-at-rest     |Understøttes         |
|Data-at-rest i mails     |Understøttes for lejere med Plan for beskyttelse af personlige oplysninger         |
|Microsoft Defender for Cloud Apps     |Understøttes         |

### <a name="autolabeling"></a>Automatisk navngivning

|Arbejdsbelastning/tjenester |Understøttelse af navngivne enheder  |
|---------|---------|
|Office Win32-klienter offline   |Understøttet. Brugeren skal vælge mærkat og anvende det manuelt |
|Online Office Win32-klienter online|Understøttes med gammel tillidsskema |
|Outlook Online   |Understøttes med gammel tillidsskema  |
|Office WAC-klient     |Understøttes |
|OWA     |Understøttes |
|Exchange-transport     |Understøttes |
|OneDrive for Business hviledata     |Understøttes |
|SharePoint Online-data-at-rest|Understøttes|
|AIP-scanner (Azure Information Protection)|Understøttes ikke|

## <a name="known-issues"></a>Kendte problemer

|Problem  |Indvirkning  |
|---------|---------|
|Tip til DLP-politik (OWA, Outlook, Office Win32-klienter)     |   Politiktip med objektbetingelse resulterer i "intet match"      |
| Understøttelse af asiatisk sprog for personnavn (kinesisk, japansk, koreansk)    | Navngivne enheder, der kun understøttes for latinsk baserede tegnsæt (dvs. kanji understøttes ikke) for personnavn        |
|Lagre i det lokale miljø    | Understøttes ikke som en arbejdsbelastning|
|Power BI (prøveversion) | Understøttes ikke

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="best-practices-for-using-named-entity-sits"></a>Bedste praksis for brug af navngivne objekt-SIT'er

Her er nogle fremgangsmåder, du kan bruge, når du opretter eller redigerer en politik, der bruger et navngivet objekt SIT.

- Brug lave antal instanser (tre til fem), når du søger efter data i et regneark, og det nøgleord, der kræves af SIT for de pågældende data, findes kun i kolonneoverskriften. Lad os f.eks. sige, at du leder efter CPR-numre i USA, og at nøgleordet `Social Security Number` kun forekommer i kolonneoverskriften. Da værdierne (det bekræftende bevis) er i cellerne nedenfor, er det sandsynligt, at kun de første få forekomster vil være så tæt på nøgleordet, at det kan registreres.  

- Hvis du bruger et navngivet objekt SIT, f.eks. Alle fulde navne, til at finde amerikanske cpr-numre, skal du bruge større antal forekomster, f.eks. 10 eller 50. Når både personnavnene og SSN'erne derefter registreres sammen, er der større sandsynlighed for, at du får ægte positiver.

- Du kan bruge [simuleringer med automatisk mærkat](apply-sensitivity-label-automatically.md#learn-about-simulation-mode) til at teste nøjagtigheden af navngivne objekt-SIT'er. Kør en simulering ved hjælp af et navngivet objekt SIT for at se, hvilke elementer der stemmer overens med politikken. Med disse oplysninger kan du finjustere nøjagtigheden ved at justere antallet af forekomster og tillidsniveauer i dine brugerdefinerede politikker eller de forbedrede skabelonbetingelser. Du kan gentage simuleringer, indtil nøjagtigheden er, hvor du ønsker det, før du udruller en DLP- eller politik for automatisk mærkning, der indeholder navngivne enheder i produktionen. Her er en oversigt over flowet:

1. Identificer DEN SIT eller kombination af SIT'er, du vil teste i simuleringstilstand, enten brugerdefineret eller klonet og redigeret.
1. Identificer eller opret en følsomhedsmærkat, der skal anvendes, når politikken for automatisk mærkning finder et match i Exchange-, SharePoint-websteder eller OneDrive-konti.
1. Opret en politik for automatisk følsomhedsmærkater, der bruger SIT fra trin 1 og med de samme betingelser og undtagelser, som bruges i din DLP-politik
1. Kør simulering af politik
1. Få vist resultaterne
1. Juster SIT- eller politikken og forekomstantallet og tillidsniveauerne for at reducere falske positiver.
1. Gentag, indtil du får de ønskede resultater for nøjagtighed.


## <a name="for-further-information"></a>Yderligere oplysninger
- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Få mere at vide om navngivne enheder](named-entities-learn.md).
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
