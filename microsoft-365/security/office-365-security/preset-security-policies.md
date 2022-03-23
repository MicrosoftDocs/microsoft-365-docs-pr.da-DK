---
title: Forudindstillede sikkerhedspolitikker
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
description: Administratorer kan få mere at vide om, hvordan du anvender Standard- og Strict policy-indstillinger på tværs af beskyttelsesfunktionerne i Exchange Online Protection (EOP) og Microsoft Defender Office 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ff81eea4232693662a907695ea0cef0d94941ac6
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63590302"
---
# <a name="preset-security-policies-in-eop-and-microsoft-defender-for-office-365"></a>Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Forudindstillede sikkerhedspolitikker udgør et centralt sted til at anvende alle de anbefalede politikker for spam, malware og phishing til brugere på én gang. Politikindstillingerne kan ikke konfigureres. De er i stedet fastsat af os og er baseret på vores observationer og erfaringer i datacentrene for at skabe en balance mellem at holde skadeligt indhold væk fra brugerne og undgå unødvendige afbrydelser.

I resten af denne artikel beskrives foruddefinerede sikkerhedspolitikker, og hvordan du konfigurerer dem.

## <a name="what-preset-security-policies-are-made-of"></a>Hvilke forudindstillede sikkerhedspolitikker er lavet af

Forudindstillede sikkerhedspolitikker består af følgende elementer:

- Profiler
- Politikker
- Politikindstillinger

Desuden er rækkefølgen af rangordenen vigtig, hvis flere forudindstillede sikkerhedspolitikker og andre politikker gælder for den samme person.

### <a name="profiles-in-preset-security-policies"></a>Profiler i forudindstillede sikkerhedspolitikker

En profil bestemmer beskyttelsesniveauet. Følgende profiler er tilgængelige:

- **Standardbeskyttelse**: En profil til grundlinjebeskyttelse, der passer til de fleste brugere.
- **Begrænset beskyttelse**: En mere aggressive beskyttelsesprofil for udvalgte brugere (mål med høj værdi eller prioritetsbrugere).

  For **Standardbeskyttelse** og **Streng beskyttelse skal** du bruge regler med betingelser og undtagelser, der bestemmer, hvem profilerne er eller ikke anvendes på.

  De tilgængelige betingelser og undtagelser er:

  - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter i organisationen.
  - **Grupper**: De angivne distributionsgrupper, mailaktiverede sikkerhedsgrupper eller Microsoft 365 grupper i organisationen.
  - **Domæner:** Alle modtagere på de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i organisationen.

  Du kan kun bruge en betingelse eller undtagelse én gang, men du kan angive flere værdier for betingelsen eller undtagelsen. Flere værdier af samme betingelse eller undtagelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

- **Indbygget beskyttelse** (Defender kun Office 365): En profil, der kun Pengeskab Links og Pengeskab beskyttelse af vedhæftede filer. Denne profil indeholder effektivt standardpolitikker til Pengeskab links og vedhæftede Pengeskab, som aldrig har haft standardpolitikker.

  For **indbygget beskyttelse er** den forudindstillede sikkerhedspolitik som standard indstillet for alle Defender-Office 365-kunder. Selvom vi ikke anbefaler det, kan du også konfigurere undtagelser baseret på **Brugere, Grupper** og **Domæner, så** beskyttelsen ikke anvendes på bestemte brugere.

Indtil du tildeler politikkerne til brugere, **tildeles standard** og **faste** sikkerhedspolitikker ikke til nogen. I modsætning hertil er **den indbyggede beskyttelse** foruddefinerede sikkerhedspolitik tildelt til alle modtagere som standard, men du kan konfigurere undtagelser.

### <a name="policies-in-preset-security-policies"></a>Politikker i foruddefinerede sikkerhedspolitikker

Forudindstillede sikkerhedspolitikker bruger de tilsvarende politikker fra de forskellige beskyttelsesfunktioner i EOP og Microsoft Defender Office 365. Disse politikker oprettes, _efter at_ du har tildelt **standardbeskyttelse** eller **forudindstillede** sikkerhedspolitikker af høj kvalitet til brugerne. Du kan ikke ændre indstillingerne i disse politikker.

- **Exchange Online Protection (EOP)**-politikker: Dette omfatter Microsoft 365 organisationer med Exchange Online-postkasser og enkeltstående EOP-organisationer uden Exchange Online postkasser:

  - [Antispampolitikker med](configure-your-spam-filter-policies.md) **navnet Standard forudindstillet sikkerhedspolitik** **og Streng forudindstillet sikkerhedspolitik**.
  - [Antimalwarepolitikker med](configure-anti-malware-policies.md) **navnet Standard forudindstillet sikkerhedspolitik** **og Streng forudindstillet sikkerhedspolitik**.
  - [EOP Antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings) med **navnet Standard forudindstillet** sikkerhedspolitik og **Streng forudindstillet sikkerhedspolitik** (spoof-indstillinger).

- **Microsoft Defender til Office 365 politikker**: Dette omfatter organisationer med Microsoft 365 E5 eller Defender Office 365-tilføjelsesabonnementer:
  - Antiphishing-politikker i Microsoft Defender for Office 365 kaldet **Standard preset sikkerhedspolitik** og **Streng forudindstillet sikkerhedspolitik**, som omfatter:
    - De samme [spoof-indstillinger,](set-up-anti-phishing-policies.md#spoof-settings) der er tilgængelige i EOP-antiphishing-politikkerne.
    - [Indstillinger for repræsentation](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Avancerede grænseværdier for phishing](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Pengeskab links med navnet](set-up-safe-links-policies.md) **Standard forudindstillet sikkerhedspolitik**, Streng **forudindstillet sikkerhedspolitik** **og Indbygget beskyttelsespolitik**.
  - [Pengeskab politikker for vedhæftede](set-up-safe-attachments-policies.md) filer **med navnet Standard forudindstillet** sikkerhedspolitik, Streng forudindstillet sikkerhedspolitik **og Indbygget beskyttelsespolitik**. 

Du kan anvende EOP-beskyttelse til andre brugere end Microsoft Defender for Office 365 beskyttelse.

### <a name="policy-settings-in-preset-security-policies"></a>Politikindstillinger i forudindstillede sikkerhedspolitikker

Du kan ikke ændre politikindstillingerne i beskyttelsesprofilerne. Standard **-**, **Strict**- og **Built-in Protection Policy-indstillingsværdierne** er beskrevet i Anbefalede indstillinger [for EOP og Microsoft Defender Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

### <a name="order-of-precedence-for-preset-security-policies-and-other-policies"></a>Rækkefølgen for forudindstillede sikkerhedspolitikker og andre politikker

Når der anvendes flere politikker på en bruger, anvendes følgende rækkefølge fra højeste prioritet til laveste prioritet:

1. **Streng beskyttelse forudindstillet** sikkerhedspolitik
2. **Standardsikkerheds** forudindstillet sikkerhedspolitik
3. Brugerdefinerede sikkerhedspolitikker
4. **Indbygget standardsikkerhedspolitik** og standardsikkerhedspolitikker

Det vil sige, at indstillingerne i politikken  til restriktiv beskyttelse tilsidesætter indstillingerne i **standardbeskyttelsespolitikken**, der tilsidesætter indstillingerne fra en brugerdefineret politik, som tilsidesætter indstillingerne fra den **indbyggede** beskyttelsespolitik (Pengeskab Links og Pengeskab Vedhæftede filer) og standardpolitikken (antispam, antimalware og antiphishing).

Hvis der f.eks. findes en sikkerhedsindstilling i **Standardbeskyttelse**, og en administrator har aktiveret **Standardbeskyttelse** for en bruger, anvendes standardbeskyttelsesindstillingen i stedet for det, der er konfigureret for den pågældende indstilling i en brugerdefineret politik eller i standardpolitikken (for den samme bruger). Bemærk, at du muligvis har en del af organisationen, som du kun vil anvende **standardpolitikken** eller den  restriktive beskyttelsespolitik på, mens du anvender en brugerdefineret politik på andre brugere i organisationen, så den opfylder specifikke behov.

**Indbygget beskyttelse påvirker** ikke modtagere i eksisterende politikker for Pengeskab links eller Pengeskab vedhæftede filer. Hvis du allerede har konfigureret  standardbeskyttelse **, streng** beskyttelse eller brugerdefinerede Pengeskab Links eller Pengeskab-politikker for vedhæftede filer, anvendes disse politikker altid før **indbygget** beskyttelse, så det har ingen indvirkning på de modtagere, der allerede er defineret i disse eksisterende foruddefinerede eller brugerdefinerede politikker.  

## <a name="assign-preset-security-policies-to-users"></a>Tildele forudindstillede sikkerhedspolitikker til brugere

### <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til siden **Forudindstillede sikkerhedspolitikker** skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil konfigurere foruddefinerede sikkerhedspolitikker, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til forudindstillede sikkerhedspolitikker skal du være medlem af **rollegruppen Global** læser.

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærk**! Når du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre funktioner  Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

### <a name="use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users"></a>Brug portalen Microsoft 365 Defender til at tildele standard og faste sikkerhedspolitikker til brugere

1. I portalen  Microsoft 365 Defender på   <https://security.microsoft.com>skal \> du gå til &-samarbejdspolitikker **& Regler** \> \> for sikkerhedspolitikker Forudindstillede sikkerhedspolitikker i sektionen **Skabelonerede** politikker. For at gå direkte til siden **Forudindstillede sikkerhedspolitikker** skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede** sikkerhedspolitikker skal **du** klikke på Administrer **i sektionerne Standardbeskyttelse** **eller** Streng beskyttelse.

3. Guiden **Anvend standardbeskyttelse** eller **Anvend begrænset beskyttelse** starter i en pop op-pop-op-mail. På siden **EOP-beskyttelse skal du identificere** de interne modtagere, som [EOP-beskyttelse](#policies-in-preset-security-policies) gælder for (modtagerbetingelser):
   - **Brugere**
   - **Grupper**
   - **Domæner**

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi i resultaterne. Gentag denne proces så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, visningsnavn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at få vist alle tilgængelige værdier.

   - **Udelad disse brugere, grupper** og domæner: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (undtagelser til modtagere), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på Næste, når du er **færdig**.

4. I Microsoft Defender for Office 365-organisationer bliver du ført til siden **Defender for Office 365-beskyttelse for** at identificere de interne modtagere, [som Microsoft Defender for Office 365-beskyttelse](#policies-in-preset-security-policies) gælder for (modtagerbetingelser).

   Indstillingerne og funktionsmåden svarer nøjagtigt til, at **EOP-beskyttelse anvendes på** siden i forrige trin.

   Klik på Næste, når du er **færdig**.

5. På siden **Gennemse og bekræft dine ændringer** skal du bekræfte dine valg og derefter klikke på **Bekræft**.

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies"></a>Brug portalen Microsoft 365 Defender til at ændre tildelingerne af standard- og strengindstillede sikkerhedspolitikker

Trinnene til at ændre tildelingen af standardbeskyttelse  eller en forudindstillet sikkerhedspolitik for Streng beskyttelse er de samme som, når du i første omgang tildelte de foruddefinerede [sikkerhedspolitikker til brugerne](#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

Hvis du vil deaktivere  **standardbeskyttelse** eller forudindstillede sikkerhedspolitikker for restriktiv beskyttelse, mens de eksisterende betingelser og undtagelser stadig bevares, skal du skubbe til/fra-knappen **til Deaktiveret** ![Skift fra.](../../media/scc-toggle-off.png) Hvis du vil aktivere politikkerne, skal du skubbe til **/fra-knappen til** ![Aktiveret](../../media/scc-toggle-on.png).

### <a name="use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-the-built-in-protection-preset-security-policy"></a>Brug portalen Microsoft 365 Defender til at ændre tildelingerne af den indbyggede standardsikkerhedspolitik

Husk, at den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik tildeles til alle modtagere, og påvirker ikke modtagere, der er defineret i **Standardbeskyttelse** eller Strict **Protection** forudindstillede sikkerhedspolitikker, eller brugerdefinerede Pengeskab Links eller Pengeskab Vedhæftede filer politikker.

Derfor anbefaler vi typisk ikke undtagelser til den **indbyggede beskyttelse foruddefinerede** sikkerhedspolitik.

1. I portalen  Microsoft 365 Defender på   <https://security.microsoft.com>skal \> du gå til &-samarbejdspolitikker **& Regler** \> \> for sikkerhedspolitikker Forudindstillede sikkerhedspolitikker i sektionen **Skabelonerede** politikker. For at gå direkte til siden **Forudindstillede sikkerhedspolitikker** skal du bruge <https://security.microsoft.com/presetSecurityPolicies>.

2. På siden **Forudindstillede** sikkerhedspolitikker **skal du vælge Tilføj udeladelse (** anbefales ikke) **i sektionen Indbygget** beskyttelse.

3. I pop op-vindue'en Udelad fra indbygget beskyttelse, der vises, skal du identificere de interne modtagere, der er udelukket fra den **indbyggede** Pengeskab beskyttelse Pengeskab vedhæftede filer:
   - **Brugere**
   - **Grupper**
   - **Domæner**

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi i resultaterne. Gentag denne proces så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, visningsnavn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at få vist alle tilgængelige værdier.

   Klik på **Gem**, når du er færdig.

### <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

Hvis du vil bekræfte, at du har tildelt  en standardbeskyttelses- eller streng beskyttelsespolitik til en bruger, skal du bruge en indstilling for beskyttelse, hvor standardværdien er en anden end standardindstillingen for beskyttelse, som er anderledes end indstillingen **Streng beskyttelse.**  

Eksempelvis skal du for mails, der registreres som spam (ikke spam med høj sikkerhed), bekræfte, at meddelelsen leveres til mappen Uønsket mail for **brugere af Standardbeskyttelse** og er sat i karantæne for brugere med **restriktiv** beskyttelse.

Eller bekræft [, at](bulk-complaint-level-values.md) BCL-værdien 6 eller højere for masseforsendelser leverer meddelelsen til mappen Uønsket mail for **brugere med standardbeskyttelse** , og at BCL-værdien 4 eller højere er i karantæne for brugere af Streng **beskyttelse** .
