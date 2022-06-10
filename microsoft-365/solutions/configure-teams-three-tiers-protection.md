---
title: Konfigurer Teams med tre niveauer af sikkerhed for fildeling
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
description: Få mere at vide om, hvordan du konfigurerer Teams for bedre fildelingssikkerhed ved hjælp af tre beskyttelsesniveauer, der balancerer sikkerheden med nem samarbejde.
ms.openlocfilehash: 4d287d342371a8182a4c9de5742d2d45ca01a1c6
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012467"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Konfigurer Teams med tre beskyttelsesniveauer

Artiklerne i denne serie indeholder anbefalinger til konfiguration af teams i Microsoft Teams og deres tilknyttede SharePoint websteder til filbeskyttelse, der balancerer sikkerheden med let samarbejde.

Denne artikel definerer fire forskellige konfigurationer, startende med et offentligt team med de mest åbne delingspolitikker. Hver yderligere konfiguration repræsenterer et meningsfuldt trin op i beskyttelse, mens muligheden for at få adgang til og samarbejde om filer, der er gemt i teams, reduceres til det relevante sæt teammedlemmer. 

Konfigurationerne i denne artikel stemmer overens med Microsofts anbefalinger til tre niveauer af beskyttelse af data, identiteter og enheder:

- Oprindelig beskyttelse

- følsom beskyttelse

- Meget følsom beskyttelse

Du kan få flere oplysninger om disse niveauer og egenskaber, der anbefales for hvert niveau, i [Illustrationer til Microsoft Cloud for Enterprise Architects](./cloud-architecture-models.md)

## <a name="three-tiers-at-a-glance"></a>Et hurtigt overblik over tre niveauer

I følgende tabel opsummeres konfigurationerne for hvert niveau. Brug disse konfigurationer som udgangspunkt for anbefalinger, og juster konfigurationerne, så de opfylder organisationens behov. Du har muligvis ikke brug for alle niveauer.

|&nbsp;|Oprindelig plan (offentlig)|Oprindelig plan (privat)|Følsomme|Meget følsom|
|:-----|:-----|:-----|:-----|:-----|
|Privat eller offentligt team|Offentlige|Privat|Privat|Privat|
|Who har adgang?|Alle i organisationen, herunder B2B-brugere.|Kun medlemmer af teamet. Andre kan anmode om adgang til det tilknyttede websted.|Kun medlemmer af teamet.|Kun medlemmer af teamet.|
|Private kanaler|Ejere og medlemmer kan oprette private kanaler|Ejere og medlemmer kan oprette private kanaler|Det er kun ejere, der kan oprette private kanaler|Det er kun ejere, der kan oprette private kanaler|
|Delte kanaler|Ejere og medlemmer kan oprette delte kanaler|Ejere og medlemmer kan oprette delte kanaler|Det er kun ejere, der kan oprette delte kanaler|Det er kun ejere, der kan oprette delte kanaler|
|Gæsteadgang på webstedsniveau|**Nye og eksisterende gæster** (standard).|**Nye og eksisterende gæster** (standard).|**Nye og eksisterende gæster** eller **Kun personer i din organisation** , afhængigt af teambehov.|**Nye og eksisterende gæster** eller **Kun personer i din organisation** , afhængigt af teambehov.|
|Indstillinger for webstedsdeling|**Webstedsejere og -medlemmer og personer med tilladelse til at redigere kan dele filer og mapper, men det er kun webstedsejere, der kan dele webstedet**.|**Webstedsejere og -medlemmer og personer med tilladelse til at redigere kan dele filer og mapper, men det er kun webstedsejere, der kan dele webstedet**.|**Webstedsejere og -medlemmer og personer med tilladelse til at redigere kan dele filer og mapper, men det er kun webstedsejere, der kan dele webstedet**.|**Det er kun webstedsejere, der kan dele filer, mapper og webstedet**.<br>Adgangsanmodninger **slået fra**.|
|Ikke-administreret enhedsadgang på webstedsniveau|**Fuld adgang fra skrivebordsapps, mobilapps og internettet** (standard).|**Fuld adgang fra skrivebordsapps, mobilapps og internettet** (standard).|**Tillad begrænset webadgang**.|**Bloker adgang**.|
|Standardtype for delingslink|**Kun personer i din organisation**|**Kun personer i din organisation**|**Bestemte personer**|**Personer med eksisterende adgang**|
|Følsomhedsmærkater|Ingen|Ingen|Følsomhedsmærkat, der bruges til at klassificere teamet og styre gæstedeling og ikke-administreret enhedsadgang.|Følsomhedsmærkat, der bruges til at klassificere teamet og styre gæstedeling og ikke-administreret enhedsadgang. Label kan også bruges på filer til at kryptere filer.|

En variation af indstillingen Meget følsom, [Teams med sikkerhedsisolation](secure-teams-security-isolation.md), bruger en entydig følsomhedsmærkat for ét team, hvilket giver ekstra sikkerhed. Du kan bruge dette mærkat til at kryptere filer, og det er kun medlemmer af teamet, der kan læse dem.

Grundlæggende beskyttelse omfatter offentlige og private teams. Offentlige teams kan registreres og tilgås af alle i organisationen. Private teams kan kun registreres og tilgås af teamets medlemmer. Begge disse konfigurationer begrænser deling af det tilknyttede SharePoint websted til teamejere for at hjælpe med administration af tilladelser.

Teams til følsom og meget følsom beskyttelse er private teams, hvor deling og anmodning om adgang for det tilknyttede websted er begrænset, og følsomhedsmærkater bruges til at angive politikker for gæstedeling, enhedsadgang og indholdkryptering.

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

De følsomme og meget følsomme niveauer bruger følsomhedsmærkater som en hjælp til at beskytte teamet og dets filer. Hvis du vil implementere disse niveauer, skal du aktivere [følsomhedsmærkater for at beskytte indhold på Microsoft Teams, Office 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

Selvom det oprindelige niveau ikke kræver følsomhedsmærkater, kan du overveje at oprette en "generel" mærkat og derefter kræve, at alle teams mærkes. Dette hjælper med at sikre, at brugerne foretager et bevidst valg om følsomhed, når de opretter et team. Hvis du planlægger at udrulle de følsomme eller meget følsomme niveauer, anbefaler vi, at du opretter en "generel" mærkat, som du kan bruge til grundlæggende teams og til filer, der ikke er følsomme.

Hvis du ikke kender til at bruge følsomhedsmærkater, anbefaler vi, at du læser [Kom i gang med følsomhedsmærkater](../compliance/get-started-with-sensitivity-labels.md) for at komme i gang. 

Hvis du allerede har udrullet følsomhedsmærkater i din organisation, skal du overveje, hvordan de mærkater, der bruges på de følsomme og meget følsomme niveauer, passer til din overordnede etiketstrategi. 

## <a name="sharing-the-sharepoint-site"></a>Deling af det SharePoint websted

Hvert team har et tilknyttet SharePoint websted, hvor dokumenter gemmes. (Dette er fanen **Filer** i en teams-kanal). Det SharePoint websted bevarer sin egen administration af tilladelser, men er sammenkædet med teamtilladelser. Teamejere er inkluderet som webstedsejere, og teammedlemmer medtages som webstedsmedlemmer på det tilknyttede websted.

De resulterende tilladelser tillader:

- Teamejere skal administrere webstedet og have fuld kontrol over webstedets indhold.
- Gruppemedlemmer til at oprette og redigere filer på webstedet. 

Teamejere og -medlemmer kan som standard dele selve webstedet med personer uden for teamet uden rent faktisk at føje dem til teamet. Vi anbefaler dette, da det komplicerer brugeradministrationen og kan medføre, at personer, der ikke er teammedlemmer, har adgang til teamfiler, uden at teamejere er sig det klart. For at forhindre dette anbefaler vi, at det kun er ejere, der har tilladelse til at dele webstedet direkte, fra det oprindelige beskyttelsesniveau.

Selvom teams ikke har en skrivebeskyttet tilladelsesindstilling, er det SharePoint websted. Hvis du har interessenter fra partnergrupper, der har brug for at kunne få vist teamfiler, men ikke redigere dem, kan du overveje at føje dem direkte til det SharePoint websted med læserettigheder.

## <a name="sharing-files-and-folders"></a>Deling af filer og mapper

Som standard kan både ejere og medlemmer af teamet dele filer og mapper med personer uden for teamet. Dette kan omfatte personer uden for din organisation, hvis du har tilladt gæstedeling. På alle tre niveauer opdaterer vi standardlinktypen for deling for at undgå utilsigtet overdeling. På det meget følsomme niveau begrænser vi denne deling til teamejere.

## <a name="sharing-with-people-outside-your-organization"></a>Deling med personer uden for din organisation

Hvis du har brug for at dele Teams indhold med personer uden for din organisation, er der to muligheder:

- **Gæstedeling** – Gæstedeling bruger Azure AD B2B-samarbejde, som giver brugerne mulighed for at dele filer, mapper, websteder, grupper og teams med personer uden for din organisation. Disse personer får adgang til delte ressourcer ved hjælp af gæstekonti i din mappe.
- **Delte kanaler** – Delte kanaler bruger Azure AD direkte B2B-forbindelse, som giver brugerne mulighed for at dele ressourcer i din organisation med personer fra andre Azure AD organisationer. Disse personer får adgang til de delte kanaler i Teams ved hjælp af deres egen arbejds- eller skolekonto. Der oprettes ingen gæstekonto i din organisation.

Både gæstedelings- og delte kanaler er nyttige, afhængigt af situationen. Se [Planlæg eksternt samarbejde](plan-external-collaboration.md) for at få oplysninger om hver enkelt, og hvordan du beslutter, hvilken der skal bruges til et bestemt scenarie.

Hvis du planlægger at bruge gæstedeling, anbefaler vi, at du konfigurerer [SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) for at få den bedste delings- og administrationsoplevelse.

Teams gæstedeling er som standard slået til, men du kan slå den fra, hvis det er nødvendigt på de følsomme og meget følsomme niveauer ved hjælp af en følsomhedsmærkat. Delte kanaler er som standard slået til, men kræver, at du konfigurerer relationer på tværs af organisationer for hver organisation, du vil samarbejde med. Se [Samarbejd med eksterne deltagere i en kanal](collaborate-teams-direct-connect.md) for at få flere oplysninger.

På det meget følsomme niveau konfigurerer vi følsomhedsmærkaten til at kryptere de filer, som det er anvendt på. Hvis du har brug for, at gæster skal have adgang til disse filer, skal du give dem tilladelser, når du opretter mærkaten. Eksterne deltagere i delte kanaler kan ikke tildeles tilladelser til følsomhedsmærkater og kan ikke få adgang til indhold, der er krypteret af en følsomhedsmærkat.

Vi anbefaler på det kraftigste, at du lader gæstedeling være aktiveret for det oprindelige niveau og for de følsomme eller meget følsomme niveauer, hvis du har brug for at samarbejde med personer uden for din organisation. Gæstedelingsfunktionerne i Microsoft 365 give en meget mere sikker og styrelig delingsoplevelse end at sende filer som vedhæftede filer i mails. Det reducerer også risikoen for skygge-it, hvor brugerne bruger uovertrøvede forbrugerprodukter til at dele med legitime eksterne samarbejdspartnere.

Hvis du jævnligt samarbejder med andre organisationer, der bruger Azure AD, kan delte kanaler være en god mulighed. Delte kanaler vises problemfrit i den anden organisations Teams klient og gør det muligt for eksterne deltagere at bruge deres almindelige brugerkonto til deres organisation i stedet for at skulle logge på separat ved hjælp af en gæstekonto.

Se følgende referencer for at oprette et sikkert og produktivt gæstedelingsmiljø for din organisation:

- [Bedste praksis for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)
- [Begræns utilsigtet eksponering af filer, når der deles med personer uden for din organisation](share-limit-accidental-exposure.md)
- [Opret et sikkert gæstedelingsmiljø](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Adgang fra ikke-administrerede enheder

For de følsomme og meget følsomme niveauer begrænser vi adgangen til SharePoint indhold med følsomhedsmærkater. Azure AD betinget adgang giver mange muligheder for at bestemme, hvordan personer får adgang Microsoft 365, herunder begrænsninger baseret på placering, risiko, enhedsoverholdelse og andre faktorer. Vi anbefaler, at du læser [Hvad er betinget adgang?](/azure/active-directory/conditional-access/overview) og overvejer, hvilke yderligere politikker der kan være relevante for din organisation.

Bemærk, at gæster ofte ikke har enheder, der administreres af din organisation. Hvis du tillader gæster på et af niveauerne, skal du overveje, hvilke typer enheder de bruger til at få adgang til teams og websteder og angive dine ikke-administrerede enhedspolitikker i overensstemmelse hermed.

### <a name="control-device-access-across-microsoft-365"></a>Kontrollér enhedsadgang på tværs af Microsoft 365

Indstillingen for ikke-administrerede enheder i følsomhedsmærkater påvirker kun SharePoint adgang. Hvis du vil udvide kontrollen over ikke-administrerede enheder ud over SharePoint, kan du [i stedet oprette en politik for betinget adgang Azure Active Directory for alle apps og tjenester i din organisation](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). Hvis du vil konfigurere denne politik specifikt til [Microsoft 365-tjenester](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365), skal du vælge **Office 365** cloudapp under **Cloudapps eller -handlinger**.

![Skærmbillede af Office 365 cloudappen i en Azure Active Directory politik for betinget adgang.](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

Brug af en politik, der påvirker alle Microsoft 365 tjenester, kan føre til bedre sikkerhed og en bedre oplevelse for dine brugere. Når du f.eks. kun blokerer adgang til ikke-administrerede enheder i SharePoint, kan brugerne få adgang til chatten i et team med en ikke-administreret enhed, men mister adgangen, når de forsøger at få adgang til fanen **Filer**. Brug af Office 365 cloudappen hjælper med at undgå problemer med [tjenesteafhængigheder](/azure/active-directory/conditional-access/service-dependencies).

## <a name="next-step"></a>Næste trin

Start med [at konfigurere det oprindelige beskyttelsesniveau](configure-teams-baseline-protection.md). Hvis det er nødvendigt, kan du tilføje [følsom beskyttelse](configure-teams-sensitive-protection.md) og [meget følsom beskyttelse](configure-teams-highly-sensitive-protection.md) oven på grundlinjen.

## <a name="see-also"></a>Se også

[Sikkerhed og overholdelse af angivne standarder i Microsoft Teams](/microsoftteams/security-compliance-overview)

[Underretningspolitikker](../compliance/alert-policies.md)
