---
title: Forudindstil sikkerhedspolitikker
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan de anvender Standard- og Strict-politikindstillinger på tværs af beskyttelsesfunktionerne i Exchange Online Protection (EOP) og Microsoft Defender for Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 01fd969461b47b0208dcfd20ff608e829b6a3336
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64915967"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Forudindstillede sikkerhedspolitikker giver brugerne en central placering, hvor de kan anvende alle de anbefalede politikker for spam, malware og phishing på én gang. Politikindstillingerne kan ikke konfigureres. De er i stedet indstillet af os og er baseret på vores observationer og oplevelser i datacentrene for at skabe balance mellem at holde skadeligt indhold væk fra brugerne og undgå unødvendige afbrydelser.

I resten af denne artikel beskrives forudindstillede sikkerhedspolitikker, og hvordan du konfigurerer dem.

## <a name="what-preset-security-policies-are-made-of"></a>Hvilke forudindstillede sikkerhedspolitikker er lavet af

Forudindstillede sikkerhedspolitikker består af følgende elementer:

- Profiler
- Politikker
- Politikindstillinger

Desuden er rækkefølgen vigtig, hvis flere forudindstillede sikkerhedspolitikker og andre politikker gælder for den samme person.

### <a name="profiles-in-preset-security-policies"></a>Profiler i forudindstillede sikkerhedspolitikker

En profil bestemmer beskyttelsesniveauet. Følgende profiler er tilgængelige:

- **Standardbeskyttelse**: En profil for grundlæggende beskyttelse, der passer til de fleste brugere.
- **Streng beskyttelse**: En mere aggressiv beskyttelsesprofil for udvalgte brugere (mål med høj værdi eller prioriterede brugere).

  I **forbindelse med Standardbeskyttelse** og **Streng beskyttelse** kan du bruge regler med betingelser og undtagelser til at bestemme de interne modtagere, som politikken gælder for (modtagerbetingelser).

  De tilgængelige betingelser og undtagelser er:

  - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter.
  - **Grupper**:
    - Medlemmer af de angivne distributionsgrupper eller mailaktiverede sikkerhedsgrupper.
    - Den angivne Microsoft 365-grupper.
  - **Domæner**: Alle modtagere i de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i din organisation.

  Du kan kun bruge en betingelse eller undtagelse én gang, men du kan angive flere værdier for betingelsen eller undtagelsen. Flere værdier med samme betingelse eller undtagelse bruger OR-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

- **Indbygget beskyttelse** (kun Defender for Office 365): En profil, der kun aktiverer beskyttelse af Pengeskab links og Pengeskab vedhæftede filer. Denne profil indeholder effektivt standardpolitikker for Pengeskab links og Pengeskab vedhæftede filer, som aldrig har haft standardpolitikker.

  For **indbygget beskyttelse** er den forudindstillede sikkerhedspolitik som standard slået til for alle Defender for Office 365 kunder. Selvom vi ikke anbefaler det, kan du også konfigurere undtagelser, der er baseret på **brugere**, **grupper** og **domæner** , så beskyttelsen ikke anvendes på bestemte brugere.

Indtil du tildeler politikkerne til brugere, tildeles de forudindstillede **standard** - og **strenge** sikkerhedspolitikker ikke til nogen. I modsætning hertil tildeles den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** til alle modtagere som standard, men du kan konfigurere undtagelser.

### <a name="policies-in-preset-security-policies"></a>Politikker i forudindstillede sikkerhedspolitikker

Forudindstillede sikkerhedspolitikker bruger de tilsvarende politikker fra de forskellige beskyttelsesfunktioner i EOP og Microsoft Defender for Office 365. Disse politikker oprettes, _når_ du har tildelt **standardbeskyttelse** eller forudindstillede sikkerhedspolitikker for **streng beskyttelse** til brugere. Du kan ikke ændre indstillingerne i disse politikker.

- **politikker for Exchange Online Protection (EOP**): Dette omfatter Microsoft 365 organisationer med Exchange Online postkasser og separate EOP-organisationer uden Exchange Online postkasser:

  - [Anti-spam-politikker](configure-your-spam-filter-policies.md) med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy**.
  - [Antimalwarepolitikker](configure-anti-malware-policies.md) med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy**.
  - [EOP Anti-phishing-politikker](set-up-anti-phishing-policies.md#spoof-settings) med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy** (spoof settings).

  > [!NOTE]
  > Politikker for udgående spam er ikke en del af forudindstillede sikkerhedspolitikker. Standardpolitikken for udgående spam beskytter automatisk medlemmer af forudindstillede sikkerhedspolitikker. Du kan også oprette brugerdefinerede politikker for udgående spam for at tilpasse beskyttelsen for medlemmer af forudindstillede sikkerhedspolitikker. Du kan få flere oplysninger under [Konfigurer filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md).

- **Microsoft Defender for Office 365 politikker**: Dette omfatter organisationer med abonnementer på Microsoft 365 E5 eller Defender for Office 365 tilføjelsesprogrammer:
  - Anti-phishing-politikker i Microsoft Defender for Office 365 med navnet **Standard Forudindstillet sikkerhedspolitik** og **Strict Preset Security Policy**, som omfatter:
    - De samme [spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings) , der er tilgængelige i EOP's anti-phishing-politikker.
    - [Repræsentationsindstillinger](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Avancerede tærskler for phishing](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Pengeskab Links-politikker](set-up-safe-links-policies.md) med navnet **Standard preset Security Policy**, **Strict Preset Security Policy** og **Indbygget beskyttelsespolitik**.
  - [Pengeskab politikker for vedhæftede filer](set-up-safe-attachments-policies.md) med navnet **Standardforudsenet sikkerhedspolitik**, **Streng forudindstillet sikkerhedspolitik** og **indbygget beskyttelsespolitik**.

Du kan anvende EOP-beskyttelse på andre brugere end Microsoft Defender for Office 365 beskyttelse.

### <a name="policy-settings-in-preset-security-policies"></a>Politikindstillinger i forudindstillede sikkerhedspolitikker

Du kan ikke ændre politikindstillingerne i beskyttelsesprofilerne. De angivne værdier for **standard**-, **strict****- og indbyggede beskyttelsespolitikindstillinger** er beskrevet i [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Rangorden for forudindstillede sikkerhedspolitikker og andre politikker

Når der anvendes flere politikker for en bruger, anvendes følgende rækkefølge fra højeste prioritet til laveste prioritet:

1. **Streng sikkerhedspolitisk** forudindstillet beskyttelse
2. Forudindstillet sikkerhedspolitik for **standardbeskyttelse**
3. Brugerdefinerede sikkerhedspolitikker
4. **Indbygget beskyttelse** forudindstillet sikkerhedspolitik og standardsikkerhedspolitikker

Med andre ord tilsidesætter indstillingerne for den **strenge beskyttelsespolitik** indstillingerne for **standardbeskyttelsespolitikken**, som tilsidesætter indstillingerne fra en brugerdefineret politik, som tilsidesætter indstillingerne fra den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** (Pengeskab Links og Pengeskab Vedhæftede filer) og standardpolitikken (spam, anti-malware og anti-phishing).

Hvis der f.eks. findes en sikkerhedsindstilling i **Standardbeskyttelse** , og en administrator har aktiveret **Standardbeskyttelse** for en bruger, anvendes indstillingen **Standardbeskyttelse** i stedet for det, der er konfigureret for den pågældende indstilling i en brugerdefineret politik eller i standardpolitikken (for den samme bruger). Bemærk, at du kan have en del af din organisation, som du kun vil anvende **Standard** - eller **Strict-beskyttelsespolitikken** på, mens du anvender en brugerdefineret politik på andre brugere i din organisation for at opfylde bestemte behov.

**Indbygget beskyttelse** påvirker ikke modtagere i eksisterende politikker for Pengeskab links eller Pengeskab vedhæftede filer. Hvis du allerede har konfigureret **standardbeskyttelse**, **streng beskyttelse** eller brugerdefineret Pengeskab links eller Pengeskab politikker for vedhæftede filer, anvendes disse politikker _altid_ _før_ **indbygget beskyttelse**, så der er ingen indvirkning på de modtagere, der allerede er defineret i disse eksisterende forudindstillede eller brugerdefinerede politikker.

## <a name="assign-preset-security-policies-to-users"></a>Tildel forudindstillede sikkerhedspolitikker til brugere

### <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil konfigurere forudindstillede sikkerhedspolitikker, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til forudindstillede sikkerhedspolitikker, skal du være medlem af rollegruppen **Global læser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærk**! Hvis du føjer brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration får brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Brug Microsoft 365 Defender-portalen til at tildele standard- og strenge forudindstillede sikkerhedspolitikker til brugere

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Forudindstillede sikkerhedspolitikker** i afsnittet **Skabelonpolitikker**. Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede sikkerhedspolitikker** skal du klikke på **Administrer** i afsnittene **Standardbeskyttelse** eller **Streng beskyttelse** .

3. Guiden **Anvend standardbeskyttelse** eller **Anvend streng beskyttelse** starter i et pop op-vindue. På **EOP-beskyttelserne gælder for siden skal** du identificere de interne modtagere, som [EOP-beskyttelsen](#policies-in-preset-security-policies) gælder for (modtagerbetingelser):
   - **Brugere**
   - **Grupper**
   - **Domæner**

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   - **Udelad disse brugere, grupper og domæner**: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (modtagerundtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på **Næste**, når du er færdig.

4. I Microsoft Defender for Office 365 organisationer føres du til **den Defender for Office 365 beskyttelse gælder for** siden for at identificere de interne modtagere, som [den Microsoft Defender for Office 365 beskyttelse](#policies-in-preset-security-policies) gælder for ( modtagerbetingelser).

   Indstillingerne og funktionsmåden er præcis som **EOP-beskyttelserne gælder for** siden i det forrige trin.

   Klik på **Næste**, når du er færdig.

5. Kontrollér dine valg på siden **Gennemse og bekræft dine ændringer** , og klik derefter på **Bekræft**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Brug Microsoft 365 Defender-portalen til at ændre tildelingerne af standard- og strenge forudindstillede sikkerhedspolitikker

Trinnene til at ændre tildelingen af den forudindstillede sikkerhedspolitik **Standardbeskyttelse** eller **Streng beskyttelse** er de samme, som da du oprindeligt [tildelte de forudindstillede sikkerhedspolitikker til brugere](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Hvis du vil deaktivere **standardbeskyttelse** eller forudindstillede sikkerhedspolitikker for **streng beskyttelse** , samtidig med at de eksisterende betingelser og undtagelser bevares, skal du skubbe til/fra-knappen til **Deaktiveret** ![til/fra.](../../media/scc-toggle-off.png). Hvis du vil aktivere politikkerne, skal du skubbe til/fra-knappen til **Aktiveret** ![](../../media/scc-toggle-on.png)til.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Brug Microsoft 365 Defender-portalen til at ændre tildelingerne af den forudindstillede sikkerhedspolitik for indbygget beskyttelse

Husk, at den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** tildeles til alle modtagere og ikke påvirker modtagere, der er defineret i de forudindstillede sikkerhedspolitikker **Standardbeskyttelse** eller **Streng beskyttelse**, eller brugerdefinerede Pengeskab links eller Pengeskab vedhæftede filer-politikker.

Derfor anbefaler vi normalt ikke undtagelser fra den **indbyggede sikkerhedspolitik** , der er forudindstillet i beskyttelse.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Forudindstillede sikkerhedspolitikker** i afsnittet **Skabelonpolitikker**. Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede sikkerhedspolitikker** skal du vælge **Tilføj udeladelser (anbefales ikke)** **i afsnittet Indbygget beskyttelse** .

3. På pop **op-vinduet Udelad fra indbygget beskyttelse**, der vises, skal du identificere de interne modtagere, der er udelukket fra den indbyggede beskyttelse af Pengeskab links og Pengeskab vedhæftede filer:
   - **Brugere**
   - **Grupper**
   - **Domæner**

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   Klik på **Gem**, når du er færdig.

### <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Hvis du vil bekræfte, at du har tildelt **sikkerhedspolitikken Standardbeskyttelse** eller **Streng beskyttelse** til en bruger, skal du bruge en beskyttelsesindstilling, hvor standardværdien er forskellig fra indstillingen **Standardbeskyttelse** , hvilket er anderledes end indstillingen **Streng beskyttelse** .

For mails, der registreres som spam (ikke spam med høj sikkerhed), skal du f.eks. bekræfte, at meddelelsen leveres til mappen Uønsket mail for **standardbeskyttelsesbrugere** og er sat i karantæne for **brugere med streng beskyttelse** .

Eller du kan [kontrollere, at](bulk-complaint-level-values.md) BCL-værdien 6 eller højere leverer meddelelsen til mappen Uønsket mail til **standardbeskyttelsesbrugere** , og at BCL-værdien 4 eller højere sætter meddelelsen i karantæne for brugere med **streng beskyttelse** .
