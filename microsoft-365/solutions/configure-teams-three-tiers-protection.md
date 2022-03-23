---
title: Konfigurere Teams med tre niveauer af fildelingssikkerhed
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
- m365solution-securecollab
- m365solution-scenario
ms.custom:
- Ent_Architecture
- seo-marvel-jun2020
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
recommendations: false
description: Lær, hvordan du konfigurerer Teams for bedre sikkerhed i forbindelse med fildeling ved hjælp af tre beskyttelsesniveauer og justering af sikkerhed uden besvær.
ms.openlocfilehash: 279e338af6db4d82291209deb66e1ea1eef74630
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588223"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Konfigurere Teams med tre niveauer af beskyttelse

Artiklerne i denne serie indeholder anbefalinger til konfiguration af teams i Microsoft Teams og deres tilknyttede SharePoint-websteder til filbeskyttelse, som afbalancerer sikkerhed med øget samarbejde.

Denne artikel definerer fire forskellige konfigurationer, startende med et offentligt team med de mest åbne delingspolitikker. Hver ekstra konfiguration repræsenterer et meningsfuldt trin i beskyttelsen, mens muligheden for at få adgang til og samarbejde om filer, der er gemt i teams, reduceres til det relevante sæt teammedlemmer. 

Konfigurationerne i denne artikel er i overensstemmelse med Microsofts anbefalinger til tre niveauer af beskyttelse af data, identiteter og enheder:

- Beskyttelse af grundlinje

- følsom beskyttelse

- Meget følsom beskyttelse

Du kan finde flere oplysninger om disse niveauer og funktioner, der anbefales til hvert niveau, under [Illustrationer i Microsoft Cloud til virksomhedsarkitekter](./cloud-architecture-models.md)


## <a name="three-tiers-at-a-glance"></a>Hurtigt overblik over tre niveauer

Følgende tabel opsummerer konfigurationerne for hvert niveau. Brug disse konfigurationer som udgangspunktanbefalinger, og juster konfigurationerne, så de opfylder organisationens behov. Du behøver muligvis ikke alle niveauer.

|-|Oprindelig plan (offentlig)|Grundlinje (privat)|Følsom|Meget følsom|
|:-----|:-----|:-----|:-----|:-----|
|Privat eller offentligt team|Offentlig|Privat|Privat|Privat|
|Who har adgang?|Alle i organisationen, herunder B2B-brugere.|Kun medlemmer af teamet. Andre kan anmode om adgang til det tilknyttede websted.|Kun medlemmer af teamet.|Kun medlemmer af teamet.|
|Private kanaler|Ejere og medlemmer kan oprette private kanaler|Ejere og medlemmer kan oprette private kanaler|Kun ejere kan oprette private kanaler|Kun ejere kan oprette private kanaler|
|Gæsteadgang på webstedsniveau|**Nye og eksisterende gæster** (standard).|**Nye og eksisterende gæster** (standard).|**Nye og eksisterende gæster** eller Kun **personer i din organisation afhængigt** af teamets behov.|**Nye og eksisterende gæster** eller Kun **personer i din organisation afhængigt** af teamets behov.|
|Indstillinger for webstedsdeling|**Webstedsejere og -medlemmer og personer med redigeringstilladelser kan dele filer og mapper, men kun webstedsejere kan dele webstedet**.|**Webstedsejere og -medlemmer og personer med redigeringstilladelser kan dele filer og mapper, men kun webstedsejere kan dele webstedet**.|**Webstedsejere og -medlemmer og personer med redigeringstilladelser kan dele filer og mapper, men kun webstedsejere kan dele webstedet**.|**Kun webstedsejere kan dele filer, mapper og webstedet**.<br>Anmodninger om adgang **er slået Fra**.|
|Ikke-administreret enhedsadgang på webstedsniveau|**Fuld adgang fra skrivebordsapps, mobilapps og internettet** (standard).|**Fuld adgang fra skrivebordsapps, mobilapps og internettet** (standard).|**Tillad begrænset adgang, der kun findes på internettet**.|**Bloker adgang**.|
|Standardtype for delingslink|**Kun personer i din organisation**|**Kun personer i din organisation**|**Bestemte personer**|**Personer med eksisterende adgang**|
|Følsomhedsmærkater|Ingen|Ingen|Følsomhedsmærkat, der bruges til at klassificere teamet og kontrollere gæstedeling og ikke-administreret enhedsadgang.|Følsomhedsmærkat, der bruges til at klassificere teamet og kontrollere gæstedeling og ikke-administreret enhedsadgang. Etiketten kan også bruges på filer til at kryptere filer.|

En variant af indstillingen Meget følsom, [Teams med sikkerhedsisolation](secure-teams-security-isolation.md), bruger et entydigt følsomhedsmærkat for ét team, hvilket giver ekstra sikkerhed. Du kan bruge denne etiket til at kryptere filer, og kun medlemmer af det pågældende team vil kunne læse dem.

Beskyttelse af grundlinjer omfatter offentlige og private teams. Offentlige teams kan findes og tilgås af alle i organisationen. Private teams kan kun findes og tilgås af medlemmer af teamet. Begge disse konfigurationer begrænser deling af det tilknyttede websted SharePoint teamejere for at hjælpe med administrationen af tilladelser.

Teams til følsom og meget følsom beskyttelse er private teams, hvor deling og anmodning om adgang til det tilknyttede websted er begrænset, og følsomhedsetiketter bruges til at angive politikker vedrørende gæstedeling, enhedsadgang og indholdskryptering.

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

De følsomme og meget følsomme niveauer bruger følsomhedsmærkater til at sikre teamet og dets filer. For at implementere disse niveauer skal du aktivere følsomhedsetiketter for at beskytte indhold [i Microsoft Teams, Office 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

Selvom niveauet for den oprindelige plan ikke kræver følsomhedsmærkater, kan du overveje at oprette en "generel" etiket og derefter kræve, at alle teams mærkes. Dette er med til at sikre, at brugerne foretager et bevidst valg om følsomhed, når de opretter et team. Hvis du planlægger at installere de følsomme eller meget følsomme niveauer, anbefaler vi, at du opretter en "generel" etiket, som du kan bruge til oprindelige teams og til filer, der ikke er følsomme.

Hvis du er ny bruger af følsomhedsmærkater, anbefaler vi, at du læser [Kom i gang med følsomhedsmærkater for](../compliance/get-started-with-sensitivity-labels.md) at komme i gang. 

Hvis du allerede har udrullet følsomhedsmærkater i din organisation, kan du overveje, hvordan de etiketter, der bruges i de følsomme og meget følsomme niveauer, passer med din overordnede etiketstrategi. 

## <a name="sharing-the-sharepoint-site"></a>Deling af SharePoint websted

Hvert team har en tilknyttet SharePoint, hvor dokumenter er gemt. (Dette er fanen **Filer** i en teams-kanal.) Webstedet SharePoint sin egen administration af tilladelser, men er knyttet til teamtilladelser. Teamejere er inkluderet som webstedsejere, og teammedlemmer medtages som webstedsmedlemmer på det tilknyttede websted.

De resulterende tilladelser tillader:

- Teamejere administrerer webstedet og har fuld kontrol over webstedets indhold.
- Teammedlemmer kan oprette og redigere filer på webstedet. 

Som standard kan teamejere og medlemmer dele selve webstedet med personer uden for teamet uden rent faktisk at føje dem til teamet. Vi anbefaler mod dette, da det komplicerer brugeradministrationen og kan føre til personer, der ikke er teammedlemmer, der har adgang til teamfiler, uden teamejere ved det. For at forhindre dette anbefaler vi, at det kun er ejere, der har tilladelse til at dele webstedet direkte, da de starter på det oprindelige beskyttelsesniveau.

Teams har ikke en skrivebeskyttet tilladelse, men det har SharePoint websted. Hvis du har interessenter for partnergrupper, der skal kunne se teamfiler, men ikke redigere dem, bør du overveje at føje dem direkte til SharePoint-webstedet med læsetilladelser.

## <a name="sharing-files-and-folders"></a>Deling af filer og mapper

Som standard kan både ejere og medlemmer af teamet dele filer og mapper med personer uden for teamet. Dette kan omfatte personer uden for organisationen, hvis du har tilladt gæstedeling. På alle tre niveauer opdaterer vi standardlinktypen for deling for at undgå utilsigtet overdeling. På det meget følsomme niveau begrænser vi denne deling til kun teamejere.

## <a name="guest-sharing"></a>Gæstedeling

Hvis du har brug for at samarbejde med personer uden for organisationen, anbefaler vi, at du konfigurerer [SharePoint og OneDrive-integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) for at få den bedste delings- og administrationsoplevelse.

Teams er som standard slået til, men du kan slå det fra, hvis det er nødvendigt i de følsomme og meget følsomme niveauer, ved hjælp af en følsomhedsmærkat.

I det meget følsomme niveau, konfigurerer vi følsomhedsmærkaten til at kryptere filer, som den er anvendt på. Hvis du har brug for, at gæster skal have adgang til disse filer, skal du give dem tilladelser, når du opretter etiketten.

Vi anbefaler på det kraftigste, at du lader gæstedeling være på grundniveau og på følsomme eller meget følsomme niveauer, hvis du har brug for at samarbejde med personer uden for organisationen. Funktionerne til gæstedeling i Microsoft 365 giver en meget mere sikker og styret delingsoplevelse end at sende filer som vedhæftede filer i mails. Det reducerer også risikoen for skygge-it, hvor brugerne bruger forbrugerprodukter, der ikke er rettigheder til, til at dele med legitime eksterne samarbejdspartnere.

Se følgende referencer for at oprette et sikkert og produktivt miljø for gæstedeling i organisationen:

- [Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)
- [Begræns utilsigtet eksponering af filer ved deling med personer uden for organisationen](share-limit-accidental-exposure.md)
- [Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Adgang fra ikke-administrerede enheder

For følsomme og meget følsomme niveauer begrænser vi adgangen til SharePoint med følsomhedsmærkater. Betinget adgang til Azure AD indeholder mange muligheder for at afgøre, hvordan folk får adgang til Microsoft 365, herunder begrænsninger, der er baseret på placering, risiko, enhedsoverholdelse og andre faktorer. Vi anbefaler, at du [læser Hvad er Betinget adgang?](/azure/active-directory/conditional-access/overview) og overvejer, hvilke yderligere politikker der kan være relevante for din organisation.

Bemærk, at gæster ofte ikke har enheder, der administreres af din organisation. Hvis du tillader gæster på et niveau, skal du overveje, hvilke typer enheder de skal bruge til at få adgang til teams og websteder og angive politikker for enheder, der ikke er administrerede.

### <a name="control-device-access-across-microsoft-365"></a>Styre enhedsadgang på tværs af Microsoft 365

Indstillingen ikke-administrerede enheder i følsomhedsmærkater påvirker kun SharePoint adgang. Hvis du vil udvide kontrollen over ikke-administrerede enheder ud over SharePoint, kan du oprette en [Azure Active Directory-politik for](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) betinget adgang for alle apps og tjenester i organisationen i stedet. Hvis du vil konfigurere denne politik specifikt for [Microsoft 365,](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365) skal du vælge **Office 365** skyappen under **Skyapps eller -handlinger**.

![Skærmbillede af Office 365 i en politik for betinget Azure Active Directory adgang.](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

Brug af en politik, der påvirker alle Microsoft 365-tjenester, kan føre til bedre sikkerhed og en bedre oplevelse for dine brugere. Når du f.eks. blokerer adgangen til enheder, der ikke er administrerede, kun i SharePoint, kan brugerne få adgang til chatten i et team med en ikke-administreret enhed, men de mister adgangen, når  de forsøger at få adgang til fanen Filer. Brug af Office 365-skyappen hjælper med at undgå problemer med [tjenesteafhængigheder](/azure/active-directory/conditional-access/service-dependencies).

## <a name="next-step"></a>Næste trin

Start med [at konfigurere det oprindelige beskyttelsesniveau](configure-teams-baseline-protection.md). Hvis det er nødvendigt, kan [du tilføje følsom](configure-teams-sensitive-protection.md) [beskyttelse og meget](configure-teams-highly-sensitive-protection.md) følsom beskyttelse oven på den oprindelige plan.

## <a name="see-also"></a>Se også

[Sikkerhed og overholdelse i Microsoft Teams](/microsoftteams/security-compliance-overview)

[Beskedpolitikker i Sikkerheds- og overholdelsescenter](../compliance/alert-policies.md)
