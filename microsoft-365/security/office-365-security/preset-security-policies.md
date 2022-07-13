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
ms.openlocfilehash: ce4113b06c27cb288bcecce6a668a7da4bd46615
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772056"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

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

  > [!IMPORTANT]
  > Flere forskellige betingelser eller undtagelser er ikke additive; de er inkluderende. Politikken anvendes _kun_ på de modtagere, der stemmer overens med _alle_ de angivne modtagerfiltre. Du kan f.eks. konfigurere en modtagerfilterbetingelse i politikken med følgende værdier:
  >
  > - Modtageren er: romain@contoso.com
  > - Modtageren er medlem af: Direktører
  >
  > Politikken anvendes _kun_ på romain@contoso.com, hvis han også er medlem af gruppen Direktører. Hvis han ikke er medlem af gruppen, anvendes politikken ikke på ham.
  >
  > Hvis du på samme måde bruger det samme modtagerfilter som en undtagelse til politikken, anvendes politikken ikke _på romain@contoso.com kun_ , hvis han også er medlem af gruppen Direktører. Hvis han ikke er medlem af gruppen, gælder politikken stadig for ham.

- **Indbygget beskyttelse** (kun Defender for Office 365): En profil, der kun aktiverer beskyttelse af sikre links og vedhæftede filer. Denne profil indeholder effektivt standardpolitikker for Sikre links og Vedhæftede filer, som aldrig har haft standardpolitikker.

  For **indbygget beskyttelse** er den forudindstillede sikkerhedspolitik som standard slået til for alle Defender for Office 365 kunder. Selvom vi ikke anbefaler det, kan du også konfigurere undtagelser, der er baseret på **brugere**, **grupper** og **domæner** , så beskyttelsen ikke anvendes på bestemte brugere.

Indtil du tildeler politikkerne til brugere, tildeles de forudindstillede **standard** - og **strenge** sikkerhedspolitikker ikke til nogen. I modsætning hertil tildeles den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** til alle modtagere som standard, men du kan konfigurere undtagelser.

### <a name="policies-in-preset-security-policies"></a>Politikker i forudindstillede sikkerhedspolitikker

Forudindstillede sikkerhedspolitikker bruger de tilsvarende politikker fra de forskellige beskyttelsesfunktioner i EOP og Microsoft Defender for Office 365. Disse politikker oprettes, _når_ du har tildelt **standardbeskyttelse** eller forudindstillede sikkerhedspolitikker for **streng beskyttelse** til brugere. Du kan ikke ændre indstillingerne i disse politikker.

- **Exchange Online Protection politikker (EOP**): Disse politikker findes i alle Microsoft 365-organisationer med Exchange Online postkasser og separate EOP-organisationer uden Exchange Online postkasser:

  - [Anti-spam-politikker](configure-your-spam-filter-policies.md) med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy**.
  - [Antimalwarepolitikker](configure-anti-malware-policies.md) med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy**.
  - [Anti-phishing-politikker (spoofing protection)](set-up-anti-phishing-policies.md#spoof-settings) med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy** (spoof settings).

  > [!NOTE]
  > Politikker for udgående spam er ikke en del af forudindstillede sikkerhedspolitikker. Standardpolitikken for udgående spam beskytter automatisk medlemmer af forudindstillede sikkerhedspolitikker. Du kan også oprette brugerdefinerede politikker for udgående spam for at tilpasse beskyttelsen for medlemmer af forudindstillede sikkerhedspolitikker. Du kan få flere oplysninger under [Konfigurer filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md).

- **Microsoft Defender for Office 365 politikker**: Disse politikker er i organisationer med abonnementer på Microsoft 365 E5 eller Defender for Office 365 tilføjelsesprogrammer:
  - Anti-phishing-politikker i Defender for Office 365 med navnet **Standard Preset Security Policy** og **Strict Preset Security Policy**, som omfatter:
    - De samme [spoof-indstillinger](set-up-anti-phishing-policies.md#spoof-settings) , der er tilgængelige i EOP's anti-phishing-politikker.
    - [Repræsentationsindstillinger](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Avancerede tærskler for phishing](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Safe Links-politikker](set-up-safe-links-policies.md) med navnet **Standard-forudindstillet sikkerhedspolitik**, **Streng forudindstillet sikkerhedspolitik** og **indbygget beskyttelsespolitik**.
  - [Politikker for vedhæftede filer, der er tillid](set-up-safe-attachments-policies.md) til, med navnet **Standardforudstillet sikkerhedspolitik**, **Streng forudindstillet sikkerhedspolitik** og **indbygget beskyttelsespolitik**.

Du kan anvende EOP-beskyttelse på andre brugere end Defender for Office 365 beskyttelse, eller du kan anvende EOP og Defender for Office 365 på de samme modtagere.

### <a name="policy-settings-in-preset-security-policies"></a>Politikindstillinger i forudindstillede sikkerhedspolitikker

Du kan ikke ændre politikindstillingerne i beskyttelsesprofilerne. De angivne værdier for **standard**-, **strict****- og indbyggede beskyttelsespolitikindstillinger** er beskrevet i [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

> [!NOTE]
> I Defender for Office 365 beskyttelse skal du identificere afsenderne til [beskyttelse af brugerrepræsentation](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) og de interne eller eksterne domæner til [beskyttelse af domænerepræsentation](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).
>
> Alle domæner, som du ejer ([accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)), modtager automatisk beskyttelse mod repræsentation af domæner i forudindstillede sikkerhedspolitikker.
>
> Alle modtagere modtager automatisk repræsentationsbeskyttelse fra [postkasseintelligens](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i forudindstillede sikkerhedspolitikker.

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Rangorden for forudindstillede sikkerhedspolitikker og andre politikker

Når der anvendes flere politikker for en bruger, anvendes følgende rækkefølge fra højeste prioritet til laveste prioritet:

1. **Streng sikkerhedspolitisk** forudindstillet beskyttelse
2. Forudindstillet sikkerhedspolitik for **standardbeskyttelse**
3. Brugerdefinerede sikkerhedspolitikker
4. **Indbygget beskyttelse** forudindstillet sikkerhedspolitik for sikre links og vedhæftede filer og standardpolitikker for antimalware, spam og anti-phishing.

Med andre ord tilsidesætter indstillingerne for den **strenge beskyttelsespolitik** indstillingerne for **standardbeskyttelsespolitikken** , som tilsidesætter indstillingerne fra en brugerdefineret politik, som tilsidesætter indstillingerne fra den forudindstillede sikkerhedspolitik indbygget **beskyttelse** (Sikre links og sikre vedhæftede filer) og standardpolitikken (spam, anti-malware og anti-phishing).

Hvis der f.eks. findes en sikkerhedsindstilling i **Standardbeskyttelse** , og en administrator har aktiveret **Standardbeskyttelse** for en bruger, anvendes indstillingen **Standardbeskyttelse** i stedet for det, der er konfigureret for den pågældende indstilling i en brugerdefineret politik eller i standardpolitikken (for den samme bruger). Bemærk, at du kan have en del af din organisation, som du kun vil anvende **Standard** - eller **Strict-beskyttelsespolitikken** på, mens du anvender en brugerdefineret politik på andre brugere i din organisation for at opfylde bestemte behov.

**Indbygget beskyttelse** påvirker ikke modtagere i eksisterende politikker for sikre links eller vedhæftede filer. Hvis du allerede har konfigureret **standardbeskyttelse**, **streng beskyttelse** eller brugerdefinerede politikker for sikre links eller vedhæftede filer, anvendes disse politikker _altid_ _før_ **indbygget beskyttelse**, så der er ingen indvirkning på de modtagere, der allerede er defineret i disse eksisterende forudindstillede eller brugerdefinerede politikker.

## <a name="assign-preset-security-policies-to-users"></a>Tildel forudindstillede sikkerhedspolitikker til brugere

### <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil konfigurere forudindstillede sikkerhedspolitikker, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til forudindstillede sikkerhedspolitikker, skal du være medlem af rollegruppen **Global læser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærk**! Tilføjelse af brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Brug Microsoft 365 Defender-portalen til at tildele standard- og strenge forudindstillede sikkerhedspolitikker til brugere

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Forudindstillede sikkerhedspolitikker** i afsnittet **Skabelonpolitikker**. Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede sikkerhedspolitikker** skal du klikke på **Administrer** i afsnittene **Standardbeskyttelse** eller **Streng beskyttelse** .

3. Guiden **Anvend standardbeskyttelse** eller **Anvend streng beskyttelse** starter i et pop op-vindue.

   På siden **Anvend Exchange Online Protection skal du** identificere de interne modtagere, som [EOP-beskyttelsen](#policies-in-preset-security-policies) gælder for (modtagerbetingelser):
   - **Alle modtagere**
   - **Specifikke modtagere**:
     - **Brugere**
     - **Grupper**
     - **Domæner**

     Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

     For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   - **Ingen**

   - **Udelad disse modtagere**: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (modtagerundtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på **Næste**, når du er færdig.

   > [!NOTE]
   > I organisationer uden Defender for Office 365 kommer du til siden **Gennemse**, når du klikker på **Næste**. De resterende trin/sider før siden **Gennemse** er kun tilgængelige i organisationer med Defender for Office 365.

4. På siden **Anvend Defender for Office 365 beskyttelse** skal du identificere de interne modtagere, som [Defender for Office 365 beskyttelse gælder](#policies-in-preset-security-policies) for (modtagerbetingelser).

   Indstillingerne og funktionsmåden er præcis som **EOP-beskyttelserne gælder for** siden i det forrige trin.

   Du kan også vælge **Tidligere valgte modtagere** for at bruge de samme modtagere, som du valgte til EOP-beskyttelse på den forrige side.

   Klik på **Næste**, når du er færdig.

5. Klik på **Næste** på siden **Repræsentationsbeskyttelse**.

6. På siden **Føj mailadresser til flag, når de repræsenteres af personer med ondsindede hensigter** , skal du tilføje interne og eksterne afsendere, der er beskyttet af [beskyttelse mod brugerrepræsentation](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > Alle modtagere modtager automatisk repræsentationsbeskyttelse fra [postkasseintelligens](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) i forudindstillede sikkerhedspolitikker.

   Hver post består af et vist navn og en mailadresse. Angiv hver værdi i boksene, og klik derefter på **Tilføj**. Gentag dette trin så mange gange, det er nødvendigt.

   Du kan maksimalt angive 350 brugere, og du kan ikke angive den samme bruger i beskyttelsesindstillinger for brugeridentificeret i flere politikker.

   Hvis du vil fjerne et eksisterende element fra listen, skal du klikke på ![Fjern brugeren fra repræsentationsbeskyttelsesikonet.](../../media/m365-cc-sc-remove.png).

   Klik på **Næste**, når du er færdig.

7. På siden **Føj domæner til flag, når de repræsenteres af personer med ondsindede hensigter** , skal du tilføje interne og eksterne domæner, der er beskyttet af [beskyttelse mod repræsentation af domæner](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   > [!NOTE]
   > Alle domæner, som du ejer ([accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)), modtager automatisk beskyttelse mod repræsentation af domæner i forudindstillede sikkerhedspolitikker.

   Alle afsendere i de angivne domæner er beskyttet af beskyttelse mod repræsentation af domæner.

   Angiv domænet i feltet, og klik derefter på **Tilføj**. Gentag dette trin så mange gange, det er nødvendigt.

   Hvis du vil fjerne en eksisterende post fra listen, skal du markere posten og derefter klikke på ![Fjern domæne fra repræsentationsbeskyttelsesikonet.](../../media/m365-cc-sc-remove.png).

   Det maksimale antal domæner, du kan angive for beskyttelse mod identitet af domæner i alle politikker til bekæmpelse af phishing, er 50.

   Klik på **Næste**, når du er færdig.

8. På siden **Føj mailadresser og domæner, der er tillid til, til ikke at markere som repræsentation** skal du angive afsendermailadresser og domæner, der skal udelukkes fra repræsentationsbeskyttelse. Meddelelser fra disse afsendere vil aldrig blive markeret som et repræsentationsangreb, men afsenderne bliver stadig scannet af andre filtre i EOP og Defender for Office 365.

   Angiv mailadressen eller domænet i feltet, og klik derefter på **Tilføj**. Gentag dette trin så mange gange, det er nødvendigt.

   Hvis du vil fjerne en eksisterende post fra listen, skal du markere posten og derefter klikke på ![Fjern undtagelser fra repræsentationsbeskyttelsesikonet.](../../media/m365-cc-sc-remove.png).

   Klik på **Næste**, når du er færdig.

9. Kontrollér dine valg på siden **Gennemse og bekræft denne politik** , og klik derefter på **Bekræft**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Brug Microsoft 365 Defender-portalen til at ændre tildelingerne af standard- og strenge forudindstillede sikkerhedspolitikker

Trinnene til at ændre tildelingen af den forudindstillede sikkerhedspolitik **Standardbeskyttelse** eller **Streng beskyttelse** er de samme, som da du oprindeligt [tildelte de forudindstillede sikkerhedspolitikker til brugere](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Hvis du vil deaktivere **standardbeskyttelse** eller forudindstillede sikkerhedspolitikker for **streng beskyttelse** , samtidig med at de eksisterende betingelser og undtagelser bevares, skal du skubbe til/fra-knappen til **Deaktiveret** ![til/fra.](../../media/scc-toggle-off.png). Hvis du vil aktivere politikkerne, skal du skubbe til/fra-knappen til **Aktiveret** ![](../../media/scc-toggle-on.png)til.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Brug Microsoft 365 Defender-portalen til at ændre tildelingerne af den forudindstillede sikkerhedspolitik for indbygget beskyttelse

Husk, at den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** tildeles til alle modtagere og ikke påvirker modtagere, der er defineret i de forudindstillede sikkerhedspolitikker **Standardbeskyttelse** eller **Streng beskyttelse** , eller brugerdefinerede politikker for Sikre links eller Vedhæftede filer.

Derfor anbefaler vi normalt ikke undtagelser fra den **indbyggede sikkerhedspolitik** , der er forudindstillet i beskyttelse.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Forudindstillede sikkerhedspolitikker** i afsnittet **Skabelonpolitikker**. Hvis du vil gå direkte til siden **Forudindstillede sikkerhedspolitikker** , skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede sikkerhedspolitikker** skal du vælge **Tilføj udeladelser (anbefales ikke)** **i afsnittet Indbygget beskyttelse** .

3. På pop **op-vinduet Udelad fra indbygget beskyttelse** , der vises, skal du identificere de interne modtagere, der er udelukket fra den indbyggede beskyttelse Af sikre links og Sikre vedhæftede filer:
   - **Brugere**
   - **Grupper**
   - **Domæner**

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern udeladelser fra ikonet indbygget beskyttelse.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   Klik på **Gem**, når du er færdig.

### <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Hvis du vil bekræfte, at du har tildelt **sikkerhedspolitikken Standardbeskyttelse** eller **Streng beskyttelse** til en bruger, skal du bruge en beskyttelsesindstilling, hvor standardværdien er forskellig fra indstillingen **Standardbeskyttelse** , hvilket er anderledes end indstillingen **Streng beskyttelse** .

For mails, der registreres som spam (ikke spam med høj sikkerhed), skal du f.eks. bekræfte, at meddelelsen leveres til mappen Uønsket mail for **standardbeskyttelsesbrugere** og er sat i karantæne for **brugere med streng beskyttelse** .

Eller du kan [kontrollere, at](bulk-complaint-level-values.md) BCL-værdien 6 eller højere leverer meddelelsen til mappen Uønsket mail til **standardbeskyttelsesbrugere** , og at BCL-værdien 4 eller højere sætter meddelelsen i karantæne for brugere med **streng beskyttelse** .
