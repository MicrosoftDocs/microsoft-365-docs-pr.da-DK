---
title: Få mere at vide om navngivne enheder (eksempel)
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
description: Få mere at vide om, hvordan navngivne enheder hjælper dig med at registrere følsomme elementer, der indeholder navne på personer, fysiske adresser og medicinske udtryk via politikker til forebyggelse af datatab
ms.openlocfilehash: 79f375fecf09a6f7ffe4c1a97b8d6864fbfb3e13
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63592997"
---
# <a name="learn-about-named-entities-preview"></a>Få mere at vide om navngivne enheder (eksempel)

> [!IMPORTANT]
> Den navngivne enheder-funktion udrulles og vises i din lejer, når den er tilgængelig for dig. Kontrollér for dem i indholdsstifinder og i flowet til forebyggelse af datatab (DLP)-politik. 

*Navngivne enheder* [er følsomme oplysningstyper](sensitive-information-type-learn-about.md) (SIT). De er komplekse ordbogs- og mønsterbaserede klassificeringer, som du kan bruge til at registrere personnavne, fysiske adresser og medicinske vilkår og betingelser. Du kan se dem i **overholdelsescenter til > dataklassificering > typer af følsomme oplysninger**. Her er en delvis liste over, hvor du kan bruge SIT'er:

- [Politikker til forebyggelse af datatab (DLP)](dlp-learn-about-dlp.md) 
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Insider-risikostyring](insider-risk-management-solution-overview.md)
- [Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security)

DLP gør særlig brug af navngivne enheder i udvidede politikskabeloner *, som* er forudkonfigurerede DLP-politikker, som du kan tilpasse til dine organisationers behov. Du kan også [oprette dine egne DLP-politikker](create-test-tune-dlp-policy.md) ud fra en [tom skabelon](create-a-dlp-policy-from-a-template.md) og bruge et navngivet enheds-SIT som betingelse.

<!-- There are many other SITs that detect strings like social security, credit card, or bank account numbers to identify sensitive items. For more information, see [Sensitive information types entity definitions](sensitive-information-type-entity-definitions.md).-->



## <a name="examples-of-named-entity-sits"></a>Eksempler på navngivne enheds-SIT'er

Named entity SITs come in two flavors, *bundled* and *unbundled*

Bundtede navngivne enheds-SIT'er registrerer alle mulige matches. Brug dem som generelle kriterier i dine DLP-politikker til at registrere følsomme elementer.

Ubundede navngivne enheds-SIT'er har et smallere fokus, f.eks. et enkelt land. Brug dem, når du har brug for en DLP-politik med et smallere registreringsområde.
 
Her er nogle eksempler på navngivne enheds-SIT'er. Du kan finde alle 52 af dem i **overholdelsescenter til > dataklassificering > typer af følsomme oplysninger**.

|Navngivet enhed |Beskrivelse  |Bundtet/ubundet  |
|---------|---------|---------|
|Alle fulde navne    |registrerer alle mulige forekomster af fulde navne         |   bundtet      |
|Alle fysiske adresser    |registrerer alle mulige matches af fysiske adresser     | bundtet |
|Alle medicinske vilkår og betingelser    |vil registrere alle mulige forekomster af medicinske vilkår og betingelser |bundtet |
|Fysiske adresser i Australien |  Registrerer mønstre, der er relateret til fysiske adresser fra Australien. |ubundet |
|Vilkår for test af blodsukker     |Registrerer termer, der er relateret til prøver, f.eks. 'hCG'. Kun engelske ord.      |ubundet |
|Mærke medicinnavne     |Registrerer navne på mærke medicin, f.eks. 'Tylenol'. Kun engelske ord.         |ubundet |

## <a name="examples-of-enhanced-dlp-policies"></a>Eksempler på udvidede DLP-politikker

Her er nogle eksempler på forbedrede DLP-politikker, der bruger navngivne enheds-SIT'er. Du kan finde alle 10 af dem i **Overholdelsescenter > forebyggelse af datatab > Opret politik**. Forbedrede skabeloner kan bruges i DLP og automatisk mærkning.

|Politikkategori  |Skabelon  |Beskrivelse  |
|---------|---------|---------|
|Finansiel|AMERIKANSK Gramm-Leach-Bliley Act (GLBA) Enhanced         |Hjælper med at registrere tilstedeværelsen af oplysninger, der er underlagt Gramm-Leach-Bliley Act (GLBA), herunder oplysninger som CPR-numre eller kreditkortnumre. Denne forbedrede skabelon udvider originalen ved også at registrere personers fulde navne, USA/Storbritannien pasnummer, amerikansk kørekortnummer og fysiske adresser i USA.         |
| Medicin og sundhed   |Australia Health Records Act (HRIP Act) Enhanced         |Hjælper med at registrere tilstedeværelsen af oplysninger, der normalt anses for at være underlagt sundhedsjournaler og beskyttelse af personlige oplysninger (HRIP) i Australien, f.eks. lægekontonummer og skattefilnummer. Denne forbedrede skabelon udvider originalen ved også at registrere personers fulde navne, medicinske vilkår og betingelser og Fysiske adresser i Australien.         |
|Beskyttelse af personlige oplysninger   |Generel forordning om databeskyttelse (GDPR) Enhanced         | Hjælper med at registrere forekomsten af personlige oplysninger for enkeltpersoner inden for EU (EU) for at overholde GDPR's forpligtelser i forbindelse med beskyttelse af personlige oplysninger. Denne forbedrede skabelon registrerer personers fulde navne og fysiske adresser for lande i EU.        |


## <a name="next-steps"></a>Næste trin

- [Brug navngivne enheder i dine politikker til forebyggelse af datatab (forhåndsvisning)](named-entities-use.md)


## <a name="for-further-information"></a>Du kan finde flere oplysninger
<!--- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md)
- [Oprette en brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type.md)
- [Opret en brugerdefineret type af følsomme oplysninger i PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)
- [Politikker til forebyggelse af datatab (DLP)](data-loss-prevention-policies.md) 
- [Følsomhedsmærkater](sensitivity-labels.md)
- [Opbevaringsnavne](retention.md)
- [Kommunikationsoverholdelse](communication-compliance.md)
- [Politikker for automærkning](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md) 
