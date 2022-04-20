---
title: Få mere at vide om navngivne enheder
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan navngivne enheder hjælper dig med at registrere følsomme elementer, der indeholder navne på personer, fysiske adresser og medicinske vilkår, via politikker til forebyggelse af datatab
ms.openlocfilehash: 6c20932216953d64abe4515b529bba66b2561647
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973195"
---
# <a name="learn-about-named-entities"></a>Få mere at vide om navngivne enheder

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

*Navngivne enheder* er [følsomme informationstyper](sensitive-information-type-learn-about.md) (SIT). De er komplekse ordbogs- og mønsterbaserede klassificeringer, som du kan bruge til at registrere personnavne, fysiske adresser og medicinske vilkår og betingelser. Du kan se dem på **Microsoft Purview-overholdelsesportalen > Dataklassificering > Typer af følsomme oplysninger**. Her er en delvis liste over, hvor du kan bruge SIT'er:


- [Politikker til forebyggelse af datatab i Microsoft Purview (DLP)](dlp-learn-about-dlp.md) 
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Styring af insider-risiko](insider-risk-management-solution-overview.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Microsoft Purview Information Protection](apply-sensitivity-label-automatically.md)
- [Administration af datalivscyklus](information-governance.md)
- [Datastyring](records-management.md)
- [Microsoft Purview eDiscovery](ediscovery.md)
- [Microsoft Priva](/privacy/priva/priva-overview.md)
- [Nøjagtige data stemmer overens med følsomme oplysningstyper](sit-learn-about-exact-data-match-based-sits.md)

DLP gør særlig brug af navngivne objekter i *udvidede politikskabeloner*, som er forudkonfigurerede DLP-politikker, som du kan tilpasse til dine organisationers behov. Du kan også [oprette dine egne DLP-politikker](create-test-tune-dlp-policy.md) ud fra en [tom skabelon](create-a-dlp-policy-from-a-template.md) og bruge et navngivet objekt SIT som en betingelse.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Eksempler på navngivne objekt-SIT'er

Navngivne enheds-SIT'er fås i to varianter, *bundtede* og *ubundtede*

Bundtede navngivne enheds-SIT'er registrerer alle mulige match. Brug dem som brede kriterier i dine DLP-politikker til registrering af følsomme elementer.

Ubundtede navngivne SIT'er har et smallere fokus, f.eks. et enkelt land. Brug dem, når du har brug for en DLP-politik med et smallere registreringsområde.
 
Her er nogle eksempler på navngivne objekt-SIT'er. Du kan finde dem alle i [objektdefinitioner for følsomme oplysninger.](sensitive-information-type-entity-definitions.md)

|Navngivet enhed |Beskrivelse  |Bundtede/ubundtede  |
|---------|---------|---------|
|Alle fulde navne    |registrerer alle mulige forekomster af fulde navne         |   Bundtet      |
|Alle fysiske adresser    |registrerer alle mulige forekomster af fysiske adresser     | Bundtet |
|Alle medicinske vilkår og betingelser    |vil detektere alle mulige match af medicinske vilkår og betingelser |Bundtet |
|Fysiske adresser i Australien |  Registrerer mønstre, der er relateret til fysiske adresser fra Australien. Inkluderet i Alle fysiske adresser SIT. |Ubundtet |
|Vilkår for blodprøve     |Detekterer termer, der er relateret til blodprøver, såsom "hCG". Kun engelske ord. Inkluderet i alle medicinske vilkår og betingelser SIT      |Ubundtet |
|Navne på mærkemedicin     |Registrerer navne på mærkemedicin, f.eks. "Tylenol". Kun engelske ord. Inkluderet i alle medicinske vilkår og betingelser.         |Ubundtet |

## <a name="examples-of-enhanced-dlp-policies"></a>Eksempler på forbedrede DLP-politikker

Her er nogle eksempler på forbedrede DLP-politikker, der bruger navngivne objekt-SIT'er. Du kan finde alle 10 af dem på **Microsoft Purview-overholdelsesportalen > Forebyggelse af datatab > Opret politik**. Forbedrede skabeloner kan bruges i DLP og automatisk mærkning.

|Politikkategori  |Skabelon  |Beskrivelse  |
|---------|---------|---------|
|Finansielle|U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced         |Hjælper med at registrere tilstedeværelsen af oplysninger, der er underlagt Gramm-Leach-Bliley Act (GLBA), herunder oplysninger som cpr-numre eller kreditkortnumre. Denne udvidede skabelon udvider originalen ved også at registrere personers fulde navne, USA/Storbritannien. pasnummer, amerikansk kørekortsnummer og amerikanske fysiske adresser.         |
| Medicinsk og sundhed   |Australia Health Records Act (HRIP Act) Enhanced         |Hjælper med at registrere tilstedeværelsen af oplysninger, der ofte anses for at være underlagt HRIP-handlingen (Health Records and Information Privacy) i Australien, f.eks. lægekontonummer og skattefilnummer. Denne forbedrede skabelon udvider originalen ved også at registrere personers fulde navne, medicinske vilkår og betingelser samt fysiske adresser i Australien.         |
|Beskyttelse af personlige oplysninger   |Generel forordning om databeskyttelse (GDPR) forbedret         | Hjælper med at registrere tilstedeværelsen af personlige oplysninger for enkeltpersoner inden for DEN Europæiske Union (EU) for at hjælpe med at opfylde GDPR's forpligtelser til beskyttelse af personlige oplysninger. Denne forbedrede skabelon registrerer folks fulde navne og fysiske adresser for lande i EU.        |


## <a name="next-steps"></a>Næste trin

- [Brug navngivne enheder i dine politikker til forebyggelse af datatab](named-entities-use.md)


## <a name="for-further-information"></a>Yderligere oplysninger

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md)
- [Opret en brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type.md)
- [Opret en brugerdefineret type følsomme oplysninger i PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [DLP (Forebyggelse af datatab)](data-loss-prevention-policies.md) 
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Opbevaringsmærkater](retention.md)
- [Kommunikationsoverholdelse](communication-compliance.md)
- [Politikker for automatisk navngivning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md) 
