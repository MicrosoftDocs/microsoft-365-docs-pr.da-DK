---
title: Konfigurer Pengeskab Links-politikker i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan du får vist, opretter, redigerer og sletter Pengeskab Links-politikker og globale Pengeskab Links-indstillinger i Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7d4cbaccab3eca371114eec92fe1bf89b2c0e353
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63595869"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Konfigurer Pengeskab Links-politikker i Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til virksomhedskunder, der [har Microsoft Defender Office 365](defender-for-office-365.md). Hvis du er privat bruger og leder efter oplysninger om Safelinks i Outlook, skal du [se Avanceret Outlook.com-sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Pengeskab Links i [Microsoft Defender til Office 365](defender-for-office-365.md) giver URL-scanning af indgående mails i mailflow og tidspunkt for klikbekræftelse af URL-adresser og links i mails og på andre placeringer. Du kan finde flere oplysninger [Pengeskab Links i Microsoft Defender for Office 365](safe-links.md).

Selvom der ikke er nogen standardpolitik for Pengeskab Links, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab **Kæder-politikker**). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md).

Du kan også bruge procedurerne i denne artikel til at oprette Pengeskab links-politikker, der gælder for bestemte brugere, grupper eller domæner.

> [!NOTE]
>
> Du skal konfigurere de globale indstillinger for Pengeskab links uden for **Pengeskab** Links-politikker. Du kan finde en [vejledning i Konfigurere globale indstillinger for Pengeskab Links i Microsoft Defender Office 365](configure-global-settings-for-safe-links.md).
>
> Administratorer bør overveje de forskellige konfigurationsindstillinger for Pengeskab links. En af de tilgængelige muligheder er at medtage brugeridentificerbare oplysninger i Pengeskab links. Denne funktion gør det *muligt for Security Ops-teams* at undersøge potentielle brugerforlig, afhjælpe og begrænse dyrere overtrædelser.

Du kan konfigurere Pengeskab Links-politikker i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell for berettigede Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser, men med Microsoft Defender Office 365 til tilføjelsesabonnementer).

De grundlæggende elementer i en Pengeskab links-politik er:

- Politikken for sikre **links: Slå** beskyttelse af Pengeskab Links til, slå scanning af URL-adresser i realtid til, angiv, om der skal ventes på scanning i realtid, før meddelelsen leveres, slå scanning til for interne meddelelser, angiv, om der skal registreres brugerklik på URL-adresser, og angiv, om brugerne skal kunne klikke på den oprindelige URL-adresse.
- **Reglen om sikre links**: Angiver prioritets- og modtagerfiltre (hvem politikken gælder for).

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer Pengeskab Links-politikker i Microsoft 365 Defender portal:

- Når du opretter en politik for Pengeskab-links, opretter du faktisk en regel for sikre links og den tilknyttede politik for sikre links på samme tid med det samme navn for begge.
- Når du ændrer en Pengeskab sammenkædede politik, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltrene ændrer reglen for sikre links. Alle andre indstillinger ændrer den tilknyttede politik for sikre links.
- Når du fjerner en politik Pengeskab links, fjernes reglen for sikre links og politikken for tilknyttede sikre links.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell administrerer du politikken og reglen separat. Du kan finde flere oplysninger i [afsnittet Brug Exchange Online PowerShell eller den enkeltstående EOP PowerShell til at konfigurere Pengeskab Links-politikker](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) senere i denne artikel.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere og slette Pengeskab Links-politikker, skal du være medlem af rollegrupperne  Organisationsadministration eller  Sikkerhedsadministrator på Microsoft 365 Defender-portalen **og** være medlem af rollegruppen Organisationsadministration i Exchange Online.
  - For skrivebeskyttet adgang til Pengeskab Links-politikker skal du være medlem af rollegrupperne **Global læser** **eller Sikkerhedslæser**.

  Du kan finde flere [oplysninger under Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md) [og tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Når du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  . - **Rollegruppen Skrivebeskyttet** organisationsadministration [i Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- For vores anbefalede indstillinger for Pengeskab Links-politikker skal du [Pengeskab politikindstillinger for links](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Der kan gå op til 6 timer, før en ny eller opdateret politik anvendes.

- [Nye funktioner bliver løbende føjet til Microsoft Defender for Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Når der tilføjes nye funktioner, kan det være nødvendigt at foretage justeringer af dine eksisterende Pengeskab politikker for links.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Brug Microsoft 365 Defender portalen til at oprette Pengeskab links-politikker

Når du opretter en brugerdefineret Pengeskab Links-politik i Microsoft 365 Defender-portalen, oprettes reglen for sikre links og politikken for tilknyttede sikre links på samme tid med det samme navn for begge.

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til & **politikker** \> for samarbejde **& Regler** \>  \> Pengeskab **Links** i **sektionen** Politikker. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links** skal du klikke på ![Opret ikon.](../../media/m365-cc-sc-create-icon.png) **Opret**.

3. **Politikguiden Pengeskab Nye sammenkæder** åbnes. På siden **Navngive din** politik skal du konfigurere følgende indstillinger:

   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på Næste, når du er **færdig**.

4. På siden **Brugere og domæner, der** vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter i organisationen.
   - **Grupper**: De angivne distributionsgrupper, mailaktiverede sikkerhedsgrupper eller Microsoft 365 grupper i organisationen.
   - **Domæner:** Alle modtagere på de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i organisationen.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi i resultaterne. Gentag denne proces så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, visningsnavn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at få vist alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere, grupper** og domæner: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (undtagelser til modtagere), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på Næste, når du er **færdig**.

5. På siden **med indstillinger for** Beskyttelse, der vises, skal du konfigurere følgende indstillinger:
   - **Vælg handlingen for ukendte potentielt skadelige URL-adresser** i meddelelser: Vælg Til  for Pengeskab aktivere beskyttelse af links i mails. Hvis du slår denne indstilling til, er følgende indstillinger tilgængelige:
     - **Anvend URL-adressescanning** i realtid for mistænkelige links og links, der peger på filer: Vælg denne indstilling for at aktivere scanning i realtid af links i mails. Hvis du slår denne indstilling til, er følgende tilgængelig:
       - **Vent på, at URL-adressen** scannes, før meddelelsen leveres: Vælg denne indstilling for at vente på, at URL-adressen scannes i realtid, før meddelelsen leveres.
     - **Anvend Pengeskab links** til mails, der sendes i organisationen: Vælg denne indstilling for at anvende politikken Pengeskab Links på meddelelser mellem interne afsendere og interne modtagere.
   - **Vælg handlingen for ukendte eller potentielt skadelige** URL-adresser i Microsoft Teams: Vælg Til for Pengeskab aktivere  beskyttelse af links i Teams. Bemærk, at det kan tage op til 24 timer, før denne indstilling træder i kraft.
   - **Registrer ikke brugerklik**: Lad denne indstilling være fravalgt for at aktivere registrering af brugerklik på URL-adresser i mails.
   - **Tillad ikke, at brugerne klikker sig til** den oprindelige URL-adresse: Vælg denne indstilling for at forhindre brugere i at klikke igennem til den oprindelige URL-adresse på [advarselssider](safe-links.md#warning-pages-from-safe-links).
   - **Undlad at omskrive følgende URL-adresser**: Tillader adgang til de angivne URL-adresser, som ellers ville være blokeret af Pengeskab links.

     Skriv den ønskede URL-adresse eller værdi i feltet, og klik derefter på **Tilføj**. Gentag dette trin så mange gange, det er nødvendigt.

     Hvis du vil fjerne en eksisterende post, skal du klikke på ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for posten.

     Du kan finde oplysninger om [indgangssyntaksen i Postsyntaksen for listen "Omstøt ikke følgende URL-adresser"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Du kan finde detaljerede oplysninger om [disse indstillinger Pengeskab Indstillinger for links til](safe-links.md#safe-links-settings-for-email-messages) mails [og Pengeskab Links for Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   Du kan finde flere anbefalede værdier for Standard- og Restriktive politikindstillinger under [Pengeskab Links-politikindstillinger](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Klik på Næste, når du er **færdig**.

6. På siden **Meddelelse** , der vises, skal du vælge en af følgende værdier for **Hvordan vil du give dine brugere besked?**:
   - **Brug standardmeddelelsesteksten**
   - **Brug brugerdefineret meddelelsestekst**: Hvis du vælger denne værdi (længden må ikke overstige 200 tegn), vises følgende indstillinger:
     - **Brug Microsoft Oversætter til automatisk lokalisering**
     - **Brugerdefineret meddelelsestekst**: Skriv den brugerdefinerede meddelelsestekst i dette felt.

   Klik på Næste, når du er **færdig**.

7. Gennemgå dine **indstillinger** på siden Gennemse, der vises. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Send, når du er **færdig**.

8. Klik på Udført på bekræftelsessiden, der **vises**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Brug portalen Microsoft 365 Defender til at få vist Pengeskab links-politikker

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til & **politikker** \> for samarbejde **& Regler** \>  \> Pengeskab **Links** i **sektionen** Politikker. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links** vises følgende egenskaber på listen over Pengeskab Links:
   - **Navn**
   - **Status**
   - **Prioritet**

3. Når du vælger en politik ved at klikke på navnet, vises politikindstillingerne i en pop op-meddelelse.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Brug portalen Microsoft 365 Defender til at ændre Pengeskab for links

1. I portalen Microsoft 365 Defender skal du gå til **afsnittet Politikker & Politikker** \>  \> for **trusselspolitikker** \> **Pengeskab Links**.

2. På siden **Pengeskab Links** skal du vælge en politik på listen ved at klikke på navnet.

3. I pop op-vindue med politikoplysninger skal du **vælge Rediger** i hver sektion for at ændre indstillingerne i sektionen. Du kan finde flere oplysninger om indstillingerne i det forrige [Afsnit Microsoft 365 Defender-portalen til Pengeskab politikker for links](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) i denne artikel.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikker, skal du se følgende afsnit.

### <a name="enable-or-disable-safe-links-policies"></a>Aktivere eller deaktivere Pengeskab links-politikker

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til & **politikker** \> for samarbejde **& Regler** \>  \> Pengeskab **Links** i **sektionen** Politikker. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links** skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist en af følgende værdier:
   - **Politik deaktiveret**: Hvis du vil aktivere politikken, skal du klikke ![på ikonet Slå til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå til** .
   - **Politik slået til**: Hvis du vil deaktivere politikken, skal du klikke ![på Ikonet Slå fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå fra**.

4. I bekræftelsesdialogboksen, der vises, skal **du klikke på Aktivér** **eller Slå fra**.

5. Klik **på Luk** i pop op-menuen med politikoplysninger.

Tilbage på hovedpolitiksiden vil **politikkens statusværdi** **være Til eller** **Fra**.

### <a name="set-the-priority-of-safe-links-policies"></a>Angiv prioriteten af Pengeskab Links

Links får som Pengeskab en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et tal for lavere prioritet angiver en højere prioritet for politikken (0 er den højeste), og politikkerne behandles i prioritetsrækkefølgen (politikker med højere prioritet behandles før politikker med lavere prioritet). Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten af en politik, skal du klikke  på Forøg prioritet eller Formindsk prioritet i egenskaberne for politikken (du kan ikke direkte ændre tallet prioritet i Microsoft 365 Defender portal). Det giver kun mening at ændre prioriteten af en politik, hvis du har flere politikker.

**Bemærk**!

- I Microsoft 365 Defender-portalen kan du kun ændre prioriteten af politikken Pengeskab Links, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen om sikre links (hvilket kan påvirke prioriteten af eksisterende regler).
- Pengeskab sammenkædede politikker behandles i den rækkefølge, de vises i (den første politik har **værdien Prioritet** 0). Du kan finde flere oplysninger om rangordenen, og hvordan flere politikker evalueres og anvendes, i Rækkefølge [og prioriteret mailbeskyttelse](how-policies-and-protections-are-combined.md).

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til & **politikker** \> for samarbejde **& Regler** \>  \> Pengeskab **Links** i **sektionen** Politikker. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links** skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist  Forøg  prioritet eller Formindsk prioritet baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken med værdien **Prioritet** **0 har** kun indstillingen **Formindsk** prioritet tilgængelig.
   - Politikken med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg** prioritet tilgængelig.
   - Hvis du har tre eller flere politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne Forøg **prioritet** **og Formindsk** prioritet.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg** prioritet ![eller ikonet Formindsk prioritet](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at **ændre værdien** Prioritet.

4. Når du er færdig, skal du **klikke på** Luk i pop op-menuen med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Brug portalen Microsoft 365 Defender til at fjerne Pengeskab links-politikker

1. I portalen Microsoft 365 Defender skal du gå til **mail & politikker** \> for **samarbejde & politikker** \>  \> for **trussel mod regler Pengeskab Links** i **sektionen** Politikker.

2. På siden **Pengeskab Links** skal du vælge en politik på listen ved at klikke på navnet. Øverst i pop op-vindue med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet Slet politik **Slet**](../../media/m365-cc-sc-delete-icon.png) politik.

3. Klik på Ja i bekræftelsesdialogboksen, der **vises**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere Pengeskab Links-politikker

Som beskrevet tidligere består en politik Pengeskab links af en politik for sikre links og en regel for sikre links.

I PowerShell fremgår forskellen mellem politikker for sikre links og regler for sikre links. Du administrerer politikker for sikre links **\*** ved hjælp af cmdlet'erne -SafeLinksPolicy, **\*og du administrerer** regler for sikre links ved hjælp af cmdlet'erne -SafeLinksRule.

- I PowerShell opretter du først politikken for sikre links, og derefter opretter du reglen for sikre links, der identificerer den politik, som reglen gælder for.
- I PowerShell ændrer du indstillingerne i politikken for sikre links og reglen for sikre links separat.
- Når du fjerner en politik for sikre links fra PowerShell, fjernes den tilsvarende regel for sikre links ikke automatisk og omvendt.

### <a name="use-powershell-to-create-safe-links-policies"></a>Brug PowerShell til at oprette Pengeskab links-politikker

Oprettelse af Pengeskab links-politik i PowerShell er en proces i to trin:

1. Opret politikken for sikre links.
2. Opret reglen for sikre kæder, der angiver politikken for sikre kæder, som reglen gælder for.

> [!NOTE]
>
> - Du kan oprette en ny regel for sikre links og tildele en eksisterende, ikke-tilknyttet politik for sikre links til den. En regel for sikre links kan ikke knyttes til mere end én politik for sikre links.
>
> - Du kan konfigurere følgende indstillinger for nye politikker for sikre links i PowerShell, der ikke er tilgængelige i Microsoft 365 Defender-portalen, før du har oprettet politikken:
>   - Opret den nye politik som deaktiveret (_Aktiveret_ `$false` på **cmdlet'en New-SafeLinksRule** ).
>   - Angiv prioriteten af politikken under oprettelsen (_Prioritet_ _\<Number\>_) på **den nye SafeLinksRule-cmdlet** ).
>
> - En ny politik for sikre links, som du opretter i PowerShell, er ikke synlig i Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for sikre links.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Trin 1: Brug PowerShell til at oprette en politik for sikre links

Hvis du vil oprette en politik for sikre links, skal du bruge denne syntaks:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-IsEnabled <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-DoNotAllowClickThrough <$true | $false>] [-DoNotTrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - Hvis du vil have mere at vide om den postsyntaksen, der skal bruges til parameteren _DoNotRewriteUrls_ , skal du se Syntaksen for indtastning på listen "Undlad at omskrive følgende [URL-adresser"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).
>
> - Du kan finde yderligere syntaks, du kan bruge til parameteren _DoNotRewriteUrls_ , når du ændrer eksisterende politikker for sikre links ved hjælp af **cmdlet'en Set-SafeLinksPolicy** , i afsnittet [Brug PowerShell](#use-powershell-to-modify-safe-links-policies) til at redigere politikker for sikre links senere i denne artikel.

I dette eksempel oprettes en politik for sikre links med navnet Contoso All med følgende værdier:

- Slå URL-scanning og omskrivning til i mails.
- Slå URL-scanning til Teams.
- Slå scanning af URL-adresser, der er klikket på, til i realtid, herunder links, der peger på filer.
- Vent på, at URL-adressen scannes, før meddelelsen leveres.
- Slå URL-scanning og -omskrivning til for interne meddelelser.
- Spor brugerklik, der er relateret til beskyttelse af Pengeskab Links (vi bruger ikke _parameteren DoNotTrackUserClicks_, og standardværdien er $false, hvilket betyder, at brugerklik registreres).
- Tillad ikke, at brugerne klikker sig til den oprindelige URL-adresse.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -IsEnabled $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -DoNotAllowClickThrough $true
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for sikre links

Hvis du vil oprette en regel for sikre kæder, skal du bruge denne syntaks:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

I dette eksempel oprettes en regel for sikre links med navnet Contoso Alle med følgende betingelser:

- Reglen er knyttet til politikken for sikre links med navnet Contoso All.
- Reglen gælder for alle modtagere i contoso.com domæne.
- Da vi ikke bruger parameteren _Prioritet_ , bruges standardprioriteten.
- Reglen er aktiveret (vi bruger ikke parameteren _Aktiveret_ , og standardværdien er `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Brug PowerShell til at få vist politikker for sikre links

Hvis du vil have vist eksisterende politikker for sikre links, skal du bruge følgende syntaks:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigt over alle politikker for sikre links.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

I dette eksempel returneres detaljerede oplysninger om politikken for sikre links med navnet Contoso-ledere.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Brug PowerShell til at få vist regler for sikre links

Hvis du vil have vist eksisterende regler for sikre links, skal du bruge følgende syntaks:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigt over alle regler for sikre links.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Hvis du vil filtrere listen efter aktiverede eller deaktiverede regler, skal du køre følgende kommandoer:

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

I dette eksempel returneres detaljerede oplysninger om reglen for sikre links med navnet Contoso-ledere.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Brug PowerShell til at ændre politikker for sikre links

Du kan ikke omdøbe en politik for sikre links i PowerShell ( **cmdlet'en Set-SafeLinksPolicy** har ingen _Name-parameter_ ). Når du omdøber Pengeskab politik for links i Microsoft 365 Defender, omdøber du kun reglen _om sikre links_.

Den eneste yderligere overvejelse for at ændre politikker for sikre links i PowerShell er den tilgængelige syntaks for _parameteren DoNotRewriteUrls_ (listen "Omselg ikke følgende [URL-adresser](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)":

- Hvis du vil tilføje værdier, der erstatter eksisterende poster, skal du bruge følgende syntaks: `"Entry1","Entry2,..."EntryN"`.
- Hvis du vil tilføje eller fjerne værdier uden at påvirke andre eksisterende poster, skal du bruge følgende syntaks: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

Ellers er de samme indstillinger tilgængelige, når du opretter en politik for sikre links som beskrevet i Trin [1: Brug PowerShell](#step-1-use-powershell-to-create-a-safe-links-policy) til at oprette en politik for sikre links tidligere i denne artikel.

Hvis du vil ændre en politik for sikre links, skal du bruge denne syntaks:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Brug PowerShell til at ændre regler for sikre links

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for sikre links i PowerShell, er parameteren Enabled, der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for sikre links, skal du se næste afsnit.

Ellers er de samme indstillinger tilgængelige, når du opretter en regel som beskrevet i trin [2: Brug PowerShell](#step-2-use-powershell-to-create-a-safe-links-rule) til at oprette en regel for sikre links tidligere i denne artikel.

Hvis du vil ændre en regel for sikre links, skal du bruge denne syntaks:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for sikre links

Aktivering eller deaktivering af en regel for sikre links i PowerShell aktiverer eller deaktiverer hele politikken for Pengeskab Links (reglen om sikre links og den tildelte politik for sikre links).

Hvis du vil aktivere eller deaktivere en regel for sikre links i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen om sikre links med navnet Marketingafdeling.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

I dette eksempel kan du bruge den samme regel.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) [og Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Brug PowerShell til at angive prioriteten af regler for sikre links

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten af en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten af en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten af en regel for sikre links i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten af reglen Marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, formindskes med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Hvis du vil angive prioriteten af en ny regel, når du opretter den, skal du bruge parameteren _Prioritet_ på **new-SafeLinksRule-cmdlet'en** i stedet.

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Brug PowerShell til at fjerne politikker for sikre links

Når du bruger PowerShell til at fjerne en politik for sikre links, fjernes den tilsvarende regel for sikre links ikke.

Hvis du vil fjerne en politik for sikre links i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for sikre links med navnet Marketingafdeling.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Brug PowerShell til at fjerne regler for sikre links

Når du bruger PowerShell til at fjerne en regel for sikre links, fjernes den tilsvarende politik for sikre links ikke.

Hvis du vil fjerne en regel for sikre links i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen om sikre links med navnet Marketingafdeling.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Kontrollér, at Pengeskab Links scanner meddelelser, ved at kontrollere den tilgængelige Microsoft Defender for Office 365 rapporter. Få mere at vide under [Få vist rapporter for Defender Office 365](view-reports-for-mdo.md) [og Brug Stifinder Microsoft 365 Defender-portalen](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

Hvis du vil bekræfte, at du har oprettet, ændret eller fjernet Pengeskab politikker for links, skal du gøre et af følgende:

- På siden **Pengeskab Links** i Microsoft 365 Defender på <https://security.microsoft.com/safelinksv2>skal du bekræfte listen over politikker, deres **Statusværdier** og **deres Prioritetsværdier**. Hvis du vil have vist flere detaljer, skal du vælge politikken på listen og få vist detaljerne i pop op-dialogboksen.

- I Exchange Online PowerShell eller Exchange Online Protection PowerShell \<Name\> skal du erstatte med navnet på politikken eller reglen, køre følgende kommando og kontrollere indstillingerne:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
