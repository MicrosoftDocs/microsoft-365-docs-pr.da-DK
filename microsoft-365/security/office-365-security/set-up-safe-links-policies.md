---
title: Konfigurer politikker for sikre links i Microsoft Defender for Office 365
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
description: Administratorer kan få mere at vide om, hvordan de kan få vist, oprette, redigere og slette politikker for sikre links og globale indstillinger for Sikre links i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2d006cd49392b80c826e23ef0d63f954d81249c0
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487021"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Konfigurer politikker for sikre links i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til erhvervskunder, der har [Microsoft Defender for Office 365](defender-for-office-365.md). Hvis du er hjemmebruger og leder efter oplysninger om Safelinks i Outlook, skal du se [Avanceret Outlook.com sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sikre links i [Microsoft Defender for Office 365](defender-for-office-365.md) indeholder URL-scanning af indgående mails i et mailflow og tidspunktet for klikbekræftelse af URL-adresser og links i mails og andre steder. Du kan få flere oplysninger [under Sikre links i Microsoft Defender for Office 365](safe-links.md).

Selvom der ikke er nogen standardpolitik for Sikre links, giver den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** beskyttelse af sikre links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede politikker for sikre links). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

Du kan også bruge procedurerne i denne artikel til at oprette politikker for sikre links, der gælder for bestemte brugere, grupper eller domæner.

> [!NOTE]
>
> Du kan konfigurere de globale indstillinger for beskyttelse af sikre links **uden for** politikkerne for sikre links. Du kan finde instruktioner under [Konfigurer globale indstillinger for Sikre links i Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md).
>
> Administratorer bør overveje de forskellige konfigurationsindstillinger for Sikre links. En af de tilgængelige muligheder er at inkludere brugeridentificerbare oplysninger i Sikre links. Denne funktion gør det muligt for sikkerhedshandlinger (SecOps)-teams at undersøge potentielle bruger kompromitterer, foretage korrigerende handlinger og begrænse dyre brud.

Du kan konfigurere politikker for sikre links på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til berettigede Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser, men Microsoft Defender for Office 365 abonnementer på tilføjelsesprogrammer).

De grundlæggende elementer i en politik for sikre links er:

- **Politikken for sikre links**: Slå beskyttelse af sikre links til, slå scanning af URL-adresser i realtid til, angiv, om der skal ventes på, at scanning i realtid fuldføres, før meddelelsen leveres, slå søgning efter interne meddelelser til, angiv, om brugerklik skal spores på URL-adresser, og angiv, om brugerne skal have tilladelse til at klikke på gennemløb til den oprindelige URL-adresse.
- **Reglen for sikre links**: Angiver prioritets- og modtagerfiltrene (hvem politikken gælder for).

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer politikker for sikre links på Microsoft 365 Defender portalen:

- Når du opretter en politik for sikre links, opretter du faktisk en regel for sikre links og den tilknyttede politik for sikre links på samme tid ved hjælp af det samme navn for begge.
- Når du ændrer en politik for sikre links, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltre reglen for sikre links. Alle andre indstillinger ændrer den tilknyttede politik for sikre links.
- Når du fjerner en politik for sikre links, fjernes reglen for sikre links og den tilknyttede politik for sikre links.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell kan du administrere politikken og reglen separat. Du kan få flere oplysninger i afsnittet [Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for sikre links](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) senere i denne artikel.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, skal du se [Opret forbindelse til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere og slette politikker for sikre links, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** i Microsoft 365 Defender portalen **og** medlem af rollegruppen **Organisationsadministration** i Exchange Online.
  - Hvis du vil have skrivebeskyttet adgang til politikker for sikre links, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md) og [Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  . – Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Du kan se vores anbefalede indstillinger for politikker for sikre links under [Politikindstillinger for sikre links](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Der kan gå op til 6 timer, før en ny eller opdateret politik anvendes.

- [Nye funktioner føjes løbende til Microsoft Defender for Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Efterhånden som der tilføjes nye funktioner, skal du muligvis foretage justeringer af dine eksisterende politikker for sikre links.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Brug Microsoft 365 Defender-portalen til at oprette politikker for sikre links

Når du opretter en brugerdefineret politik for sikre links på Microsoft 365 Defender-portalen, oprettes reglen for sikre links og den tilknyttede politik for sikre links samtidig med det samme navn for begge.

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

2. Klik på Ikonet Opret på ![siden **Sikre links**.](../../media/m365-cc-sc-create-icon.png) **Opret**.

3. Guiden **Ny politik for sikre links** åbnes. Konfigurer følgende indstillinger på siden **Navngiv din politik** :

   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på **Næste**, når du er færdig.

4. På siden **Brugere og domæner** , der vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter.
   - **Grupper**:
     - Medlemmer af de angivne distributionsgrupper eller mailaktiverede sikkerhedsgrupper.
     - Den angivne Microsoft 365-grupper.
   - **Domæner**: Alle modtagere i de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i din organisation.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi fra resultaterne. Gentag denne proces så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, vist navn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at se alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger OR-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere, grupper og domæner**: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (modtagerundtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   > [!IMPORTANT]
   > Flere forskellige betingelser eller undtagelser er ikke additive; de er inkluderende. Politikken anvendes _kun_ på de modtagere, der stemmer overens med _alle_ de angivne modtagerfiltre. Du kan f.eks. konfigurere en modtagerfilterbetingelse i politikken med følgende værdier:
   >
   > - Modtageren er: romain@contoso.com
   > - Modtageren er medlem af: Direktører
   >
   > Politikken anvendes _kun_ på romain@contoso.com, hvis han også er medlem af koncernerne Direktører. Hvis han ikke er medlem af gruppen, anvendes politikken ikke på ham.
   >
   > Hvis du på samme måde bruger det samme modtagerfilter som en undtagelse til politikken, anvendes politikken ikke _kun_ på romain@contoso.com, hvis han også er medlem af grupperne Direktører. Hvis han ikke er medlem af gruppen, gælder politikken stadig for ham.

   Klik på **Næste**, når du er færdig.

5. Konfigurer følgende indstillinger på siden **Beskyttelsesindstillinger** , der vises:
   - **Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser**: Vælg **Til** for at aktivere beskyttelse af sikre links for links i mails. Hvis du slår denne indstilling til, er følgende indstillinger tilgængelige:
     - **Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer**: Vælg denne indstilling for at aktivere scanning i realtid af links i mails. Hvis du slår denne indstilling til, er følgende indstilling tilgængelig:
       - **Vent på, at scanningen af URL-adressen fuldføres, før meddelelsen leveres**: Vælg denne indstilling for at vente på, at scanningen af URL-adresser i realtid fuldføres, før meddelelsen leveres.
     - **Anvend sikre links på mails, der er sendt i organisationen**: Vælg denne indstilling for at anvende politikken Sikre links på meddelelser mellem interne afsendere og interne modtagere.
   - **Vælg handlingen for ukendte eller potentielt skadelige URL-adresser i Microsoft Teams**: Vælg **Til** for at aktivere beskyttelse af sikre links for links i Teams. Bemærk, at det kan tage op til 24 timer, før denne indstilling træder i kraft.

     > [!NOTE]
     > Beskyttelse af Sikre links til Microsoft Teams er i øjeblikket ikke tilgængelig i Microsoft 365 GCC High eller Microsoft 365 DoD.

   - **Spor bruger clicks**: Lad denne indstilling være markeret for at aktivere sporing af brugerens klik på URL-adresser i mails.
   - **Lad brugerne klikke sig videre til den oprindelige URL-adresse**: Fjern markeringen i denne indstilling for at forhindre brugere i at klikke sig videre til den oprindelige URL-adresse på [advarselssider](safe-links.md#warning-pages-from-safe-links).
   - **Undlad at omskrive følgende URL-adresser**: Giver adgang til de angivne URL-adresser, der ellers ville blive blokeret af Sikre links.

     > [!NOTE]
     > Formålet med listen "Omskriv ikke følgende URL-adresser" er at springe ombrydningen Af sikre links over for de angivne URL-adresser. I stedet for at bruge denne liste kan du nu [oprette tilladte URL-adresser på listen over tilladte/blokerede lejere](allow-block-urls.md#create-allow-url-entries).

     Skriv den ønskede URL-adresse eller værdi i feltet, og klik derefter på **Tilføj**. Gentag dette trin så mange gange, det er nødvendigt.

     Hvis du vil fjerne en eksisterende post, skal du klikke på ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for posten.

     Du kan få mere at vide om syntaksen under [Postsyntaks for listen "Omskriv ikke følgende URL-adresser"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Du kan finde detaljerede oplysninger om disse indstillinger under [Indstillinger for sikre links for mails](safe-links.md#safe-links-settings-for-email-messages) og [Indstillinger for Sikre links til Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   Du kan få mere at vide om de anbefalede værdier for Standard- og Strict-politikindstillinger under [Politikindstillinger for sikre links](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Klik på **Næste**, når du er færdig.

6. På siden **Meddelelse** , der vises, skal du vælge en af følgende værdier for **Hvordan vil du give brugerne besked?**:
   - **Brug standardmeddelelsesteksten**
   - **Brug brugerdefineret meddelelsestekst**: Hvis du vælger denne værdi (længden må ikke overstige 200 tegn), vises følgende indstillinger:
     - **Brug Microsoft Translator til automatisk lokalisering**
     - **Brugerdefineret meddelelsestekst**: Angiv den brugerdefinerede meddelelsestekst i dette felt.

   Klik på **Næste**, når du er færdig.

7. Gennemse dine indstillinger på siden **Gennemse** , der vises. Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

8. Klik på **Udført** på den bekræftelsesside, der vises.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Brug Microsoft 365 Defender-portalen til at få vist politikker for sikre links

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Sikre links** vises følgende egenskaber på listen over politikker for sikre links:
   - **Navn**
   - **Status**
   - **Prioritet**

3. Når du vælger en politik ved at klikke på navnet, vises politikindstillingerne i et pop op-vindue.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Brug Microsoft 365 Defender-portalen til at redigere politikker for sikre links

1. På Microsoft 365 Defender-portalen skal du gå til afsnittet **Politikker & regler** \> **Trusselspolitikker politikker** \> afsnittet  \> **Sikre links**.

2. På siden **Sikre links** skal du vælge en politik på listen ved at klikke på navnet.

3. I det pop op-vindue med politikoplysninger, der vises, skal du vælge **Rediger** i hvert afsnit for at redigere indstillingerne i sektionen. Du kan få flere oplysninger om indstillingerne i det forrige afsnit [Brug Microsoft 365 Defender-portalen til at oprette politikker for sikre links](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) i denne artikel.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikken, skal du se følgende afsnit.

### <a name="enable-or-disable-safe-links-policies"></a>Aktivér eller deaktiver politikker for sikre links

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Sikre links** skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se en af følgende værdier:
   - **Politik slået fra**: Hvis du vil aktivere politikken, skal du klikke på ![Slå ikonet til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** .
   - **Politik slået** til: Hvis du vil slå politikken fra, skal du klikke på ![Slå ikonet fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Sluk for den**.

4. I den bekræftelsesdialogboks, der vises, skal du klikke **på Slå til** eller **Slå fra**.

5. Klik på **Luk** i pop op-vinduet med politikoplysninger.

Tilbage på hovedpolitiksiden **vil statusværdien** for politikken være **Til** eller **Fra**.

### <a name="set-the-priority-of-safe-links-policies"></a>Angiv prioriteten for politikker for sikre links

Som standard får Sikre links en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et lavere prioritetsnummer angiver en højere prioritet for politikken (0 er den højeste), og politikker behandles i prioriteret rækkefølge (politikker med højere prioritet behandles før politikker med lavere prioritet). Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten for en politik, skal du klikke på **Forøg prioritet** eller **Formindsk prioritet** i egenskaberne for politikken (du kan ikke direkte ændre **prioritetsnummeret** på portalen Microsoft 365 Defender). Det giver kun mening at ændre prioriteten for en politik, hvis du har flere politikker.

**Bemærk**!

- På Microsoft 365 Defender-portalen kan du kun ændre prioriteten for politikken Sikre links, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen for sikre links (hvilket kan påvirke prioriteten af eksisterende regler).
- Politikker for sikre links behandles i den rækkefølge, de vises i (den første politik har **prioritetsværdien** 0). Du kan finde flere oplysninger om prioritetsrækkefølgen, og hvordan flere politikker evalueres og anvendes, under [Beskyttelse af mailrækkefølge og prioritet](how-policies-and-protections-are-combined.md).

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Sikre links** skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se **Forøg prioritet** eller **Formindsk prioritet** baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken med **prioritetsværdien** **0** har kun indstillingen **Formindsk prioritet** tilgængelig.
   - Politikken med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg prioritet** tilgængelig.
   - Hvis du har tre eller flere politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne **Forøg prioritet** og **Formindsk prioritet** tilgængelige.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg prioritet** eller ![formindsk prioritetsikon](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at ændre **prioritetsværdien** .

4. Når du er færdig, skal du klikke på **Luk** i pop op-vinduet med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Brug Microsoft 365 Defender-portalen til at fjerne politikker for sikre links

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**.

2. På siden **Sikre links** skal du vælge en politik på listen ved at klikke på navnet. Øverst i pop op-vinduet med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet](../../media/m365-cc-sc-delete-icon.png) Slet politik **Slet politik**.

3. Klik på **Ja** i den bekræftelsesdialogboks, der vises.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for sikre links

Som tidligere beskrevet består en politik for sikre links af en politik for sikre links og en regel for sikre links.

I PowerShell er forskellen mellem politikker for sikre links og regler for sikre links synlig. Du administrerer politikker for sikre links ved hjælp **\*af cmdlet'erne -SafeLinksPolicy** , og du administrerer regler for sikre links ved hjælp **\*af -SafeLinksRule-cmdlet'erne** .

- I PowerShell skal du først oprette politikken for sikre links og derefter oprette reglen for sikre links, der identificerer den politik, som reglen gælder for.
- I PowerShell kan du ændre indstillingerne i politikken for sikre links og reglen for sikre links separat.
- Når du fjerner en politik for sikre links fra PowerShell, fjernes den tilsvarende regel for sikre links ikke automatisk og omvendt.

### <a name="use-powershell-to-create-safe-links-policies"></a>Brug PowerShell til at oprette politikker for sikre links

Oprettelse af en politik for sikre links i PowerShell er en proces med to trin:

1. Opret politikken for sikre links.
2. Opret reglen for sikre links, der angiver politikken for sikre links, som reglen gælder for.

> [!NOTE]
>
> - Du kan oprette en ny regel for sikre links og tildele den en eksisterende politik for sikre links, der ikke er tilknyttet. En regel for sikre links kan ikke knyttes til mere end én politik for sikre links.
>
> - Du kan konfigurere følgende indstillinger for nye politikker for sikre links i PowerShell, der ikke er tilgængelige på Microsoft 365 Defender-portalen, før du har oprettet politikken:
>   - Opret den nye politik som deaktiveret (_aktiveret_ `$false` på **New-SafeLinksRule-cmdlet'en** ).
>   - Angiv prioriteten for politikken under oprettelse (_prioritet_ _\<Number\>_) på **New-SafeLinksRule-cmdlet'en** ).
>
> - En ny politik for sikre links, som du opretter i PowerShell, er ikke synlig på Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for sikre links.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Trin 1: Brug PowerShell til at oprette en politik for sikre links

Brug denne syntaks til at oprette en politik for sikre links:

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSafeLinksForEmail <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-AllowClickThrough <$true | $false>] [-TrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - Du kan finde flere oplysninger om den postsyntaks, der skal bruges til parameteren _DoNotRewriteUrls_ , under [Postsyntaks for listen "Omskriv ikke følgende URL-adresser"](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).
>
> - Hvis du vil have mere syntaks, som du kan bruge til parameteren _DoNotRewriteUrls_ , når du ændrer eksisterende politikker for sikre links ved hjælp af cmdlet'en **Set-SafeLinksPolicy** , skal du se afsnittet [Brug PowerShell til at ændre politikker for sikre links](#use-powershell-to-modify-safe-links-policies) senere i denne artikel.

I dette eksempel oprettes en politik for sikre links med navnet Contoso All med følgende værdier:

- Slå scanning af URL-adresser til og omskrivning i mails.
- Slå scanning af URL-adresser til i Teams.
- Slå scanning i realtid af url-adresser, der klikkes på, til, herunder links, der peger på filer.
- Vent på, at scanningen af URL-adressen fuldføres, før meddelelsen leveres.
- Slå scanning af URL-adresser til og omskrivning af interne meddelelser.
- Spor brugerklik, der er relateret til beskyttelse af sikre links (vi bruger ikke parameteren _TrackUserClicks_ , og standardværdien er $true).
- Tillad ikke, at brugerne klikker sig igennem til den oprindelige URL-adresse.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -EnableSafeLinksForEmail $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -AllowClickThrough $false
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for sikre links

Hvis du vil oprette en regel for sikre links, skal du bruge denne syntaks:

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

I dette eksempel oprettes en regel for sikre links med navnet Contoso All med følgende betingelser:

- Reglen er knyttet til politikken for sikre links med navnet Contoso All.
- Reglen gælder for alle modtagere i det contoso.com domæne.
- Da vi ikke bruger parameteren _Prioritet_ , bruges standardprioriteten.
- Reglen er aktiveret (vi bruger ikke parameteren _Enabled_ , og standardværdien er `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

I dette eksempel oprettes en regel for sikre links, der ligner det forrige eksempel, men i dette eksempel gælder reglen for modtagere i alle accepterede domæner i organisationen.

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

I dette eksempel oprettes en regel for sikre links, der ligner de tidligere eksempler, men i dette eksempel gælder reglen for modtagere på de domæner, der er angivet i en .csv fil.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs $SLDomains
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Brug PowerShell til at få vist politikker for sikre links

Hvis du vil have vist eksisterende politikker for sikre links, skal du bruge følgende syntaks:

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle politikker for sikre links.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

I dette eksempel returneres detaljerede oplysninger om politikken for sikre links med navnet Contoso Executives.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Brug PowerShell til at få vist regler for sikre links

Hvis du vil have vist eksisterende regler for sikre links, skal du bruge følgende syntaks:

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle regler for sikre links.

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

I dette eksempel returneres detaljerede oplysninger om reglen for sikre links med navnet Contoso Executives.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Brug PowerShell til at ændre politikker for sikre links

Du kan ikke omdøbe en politik for sikre links i PowerShell ( **Set-SafeLinksPolicy-cmdlet'en** har ingen _navneparameter_ ). Når du omdøber en politik for sikre links på Microsoft 365 Defender-portalen, omdøber du kun _reglen_ for sikre links.

Den eneste yderligere overvejelse i forbindelse med ændring af politikker for sikre links i PowerShell er den tilgængelige syntaks for parameteren _DoNotRewriteUrls_ ( [listen "Omskriv ikke følgende URL-adresser](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)"):

- Hvis du vil tilføje værdier, der erstatter eksisterende poster, skal du bruge følgende syntaks: `"Entry1","Entry2,..."EntryN"`.
- Hvis du vil tilføje eller fjerne værdier, uden at det påvirker andre eksisterende poster, skal du bruge følgende syntaks: `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

Ellers er de samme indstillinger tilgængelige, når du opretter en politik for sikre links, som beskrevet i [trin 1: Brug PowerShell til at oprette en politik for sikre links](#step-1-use-powershell-to-create-a-safe-links-policy) tidligere i denne artikel.

Hvis du vil ændre en politik for sikre links, skal du bruge denne syntaks:

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Brug PowerShell til at ændre regler for sikre links

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for sikre links i PowerShell, er parameteren _Enabled_ , der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for sikre links, skal du se næste afsnit.

Ellers er de samme indstillinger tilgængelige, når du opretter en regel som beskrevet i [trin 2: Brug PowerShell til at oprette et regelafsnit for sikre links](#step-2-use-powershell-to-create-a-safe-links-rule) tidligere i denne artikel.

Hvis du vil ændre en regel for sikre links, skal du bruge denne syntaks:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

I dette eksempel føjes alle accepterede domæner i organisationen som en betingelse til reglen for sikre links med navnet Contoso All.

```powershell
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

I dette eksempel føjes domæner fra den angivne .csv som en betingelse til reglen for sikre links med navnet Contoso All.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs $SLDomains
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for sikre links

Aktivering eller deaktivering af en regel for sikre links i PowerShell aktiverer eller deaktiverer hele politikken For sikre links (reglen for sikre links og politikken for tildelte sikre links).

Hvis du vil aktivere eller deaktivere en regel for sikre links i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen for sikre links med navnet Marketingafdeling.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

I dette eksempel aktiveres samme regel.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) og [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Brug PowerShell til at angive prioriteten for regler for sikre links

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten for en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten for en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten for en regel for sikre links i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten for reglen marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, reduceres med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Hvis du vil angive prioriteten for en ny regel, når du opretter den, skal du i stedet bruge parameteren _Priority_ på **New-SafeLinksRule-cmdlet'en** .

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

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

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Brug PowerShell til at fjerne regler for sikre links

Når du bruger PowerShell til at fjerne en regel for sikre links, fjernes den tilsvarende politik for sikre links ikke.

Hvis du vil fjerne en regel for sikre links i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for sikre links med navnet Marketingafdeling.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Hvis du vil kontrollere, at Safe Links scanner meddelelser, skal du kontrollere de tilgængelige Microsoft Defender for Office 365 rapporter. Du kan få flere oplysninger under [Få vist rapporter for Defender for Office 365](view-reports-for-mdo.md) og [Brug Stifinder på Microsoft 365 Defender-portalen](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har oprettet, ændret eller fjernet politikker for sikre links:

- Kontrollér listen over politikker, deres **statusværdier** og deres **prioritetsværdier** på siden **Sikre links** på Microsoft 365 Defender-portalen på <https://security.microsoft.com/safelinksv2>. Hvis du vil have vist flere oplysninger, skal du vælge politikken på listen og få vist detaljerne i vinduet.

- I Exchange Online PowerShell eller Exchange Online Protection PowerShell skal du erstatte \<Name\> med navnet på politikken eller reglen, køre følgende kommando og kontrollere indstillingerne:

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
