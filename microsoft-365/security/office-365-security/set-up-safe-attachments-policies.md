---
title: Konfigurer politikker for vedhæftede filer, der er tillid til, i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan du definerer politikker for vedhæftede filer, der er tillid til, for at beskytte din organisation mod skadelige filer i mails.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f93f264ac22be594bfb34601c3f243a2c7c145b4
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66773153"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Konfigurer politikker for vedhæftede filer, der er tillid til, i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til erhvervskunder, der har [Microsoft Defender for Office 365](whats-new-in-defender-for-office-365.md). Hvis du er privat bruger og leder efter oplysninger om scanning af vedhæftede filer i Outlook, skal du se [Avanceret Outlook.com sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sikre vedhæftede filer er en funktion i [Microsoft Defender for Office 365](whats-new-in-defender-for-office-365.md), der bruger et virtuelt miljø til at kontrollere vedhæftede filer i indgående mails, når de er blevet scannet af [antimalwarebeskyttelse i Exchange Online Protection (EOP),](anti-malware-protection.md) men før de leveres til modtagere. Du kan få flere oplysninger [under Sikre vedhæftede filer i Microsoft Defender for Office 365](safe-attachments.md).

Selvom der ikke er nogen standardpolitik for vedhæftede filer, giver den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede politikker for vedhæftede filer, der er tillid til). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md). Du kan også bruge procedurerne i denne artikel til at oprette politikker for vedhæftede filer, der er tillid til, og som gælder for bestemte brugere, grupper eller domæner.

Du kan konfigurere politikker for vedhæftede filer, der er tillid til, på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til berettigede Microsoft 365-organisationer med postkasser i Exchange Online; separat EOP PowerShell til organisationer uden Exchange Online postkasser , men med Defender for Office 365 abonnementer på tilføjelsesprogrammer).

De grundlæggende elementer i en politik for sikre vedhæftede filer er:

- **Politikken for sikre vedhæftede filer**: Angiver handlingerne for ukendte malwareregistreringer, om der skal sendes meddelelser med vedhæftede filer med malware til en angivet mailadresse, og om der skal leveres meddelelser, hvis scanningen af sikre vedhæftede filer ikke kan fuldføres.
- **Reglen for sikker vedhæftet fil**: Angiver prioritets- og modtagerfiltrene (hvem politikken gælder for).

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer politikker for vedhæftede filer i Microsoft 365 Defender portalen:

- Når du opretter en politik for sikre vedhæftede filer, opretter du faktisk en regel for sikre vedhæftede filer og den tilknyttede politik for sikre vedhæftede filer samtidig med det samme navn for begge.
- Når du ændrer en politik for vedhæftede filer, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltre reglen for sikre vedhæftede filer. Alle andre indstillinger ændrer den tilknyttede politik for sikre vedhæftede filer.
- Når du fjerner en politik for sikre vedhæftede filer, fjernes reglen for sikre vedhæftede filer og den tilknyttede politik for sikre vedhæftede filer.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell kan du administrere politikken og reglen separat. Du kan få flere oplysninger i afsnittet [Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for vedhæftede filer, der er tillid til](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) senere i denne artikel.

> [!NOTE]
> I området med globale indstillinger under indstillinger for sikre vedhæftede filer kan du konfigurere funktioner, der ikke er afhængige af politikker for vedhæftede filer, der er tillid til. Du kan finde instruktioner under [Slå sikre vedhæftede filer til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) og [Sikre dokumenter i Microsoft 365 E5](safe-docs.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Vedhæftede filer, der er tillid** til, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, skal du se [Opret forbindelse til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tilladelser, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere og slette politikker for vedhæftede filer, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** på Microsoft 365 Defender portalen **og** medlem af rollegruppen **Organisationsadministration** i Exchange Online.
  - Hvis du vil have skrivebeskyttet adgang til politikker for sikre vedhæftede filer, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** på Microsoft 365 Defender-portalen.

  Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md) og [Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Du kan se vores anbefalede indstillinger for politikker for sikre [vedhæftede filer under Indstillinger for vedhæftede filer, der er tillid](recommended-settings-for-eop-and-office365.md#safe-attachments-settings) til.

- Der kan gå op til 30 minutter, før en ny eller opdateret politik anvendes.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Brug Microsoft 365 Defender-portalen til at oprette politikker for vedhæftede filer, der er tillid til

Når du opretter en brugerdefineret politik for vedhæftede filer, der er tillid til, på portalen Microsoft 365 Defender oprettes reglen for sikker vedhæftede filer og den tilknyttede politik for sikre vedhæftede filer samtidig med det samme navn for begge.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Vedhæftede filer, der er tillid** til, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. Klik på Ikonet Opret på ![siden **Vedhæftede filer, der er tillid** til.](../../media/m365-cc-sc-create-icon.png) **Opret**.

3. Politikguiden åbnes. Konfigurer følgende indstillinger på siden **Navngiv din politik** :
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
   > Politikken anvendes _kun_ på romain@contoso.com, hvis han også er medlem af gruppen Direktører. Hvis han ikke er medlem af gruppen, anvendes politikken ikke på ham.
   >
   > Hvis du på samme måde bruger det samme modtagerfilter som en undtagelse til politikken, anvendes politikken ikke _på romain@contoso.com kun_ , hvis han også er medlem af gruppen Direktører. Hvis han ikke er medlem af gruppen, gælder politikken stadig for ham.

   Klik på **Næste**, når du er færdig.

5. Konfigurer følgende indstillinger på siden **Indstillinger** :

   - **Ukendte malwaresvar for vedhæftede filer, der er tillid** til: Vælg en af følgende værdier:
     - **Fra**: Vi anbefaler normalt ikke denne værdi.
     - **Skærm**
     - **Blok**: Dette er standardværdien og den anbefalede værdi i standard- og [strenge forudindstillede sikkerhedspolitikker](preset-security-policies.md).
     - **Erstatte**
     - **Dynamisk levering (prøveversion)**

     Disse værdier er forklaret i [politikindstillingerne for vedhæftede filer, der er tillid til](safe-attachments.md#safe-attachments-policy-settings).

   - **Karantænepolitik**: Vælg den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af Sikre vedhæftede filer (**Bloker**, **Erstat** eller **Dynamisk levering**). Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne, og om brugerne modtager karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

     En tom værdi betyder, at standard karantænepolitikken bruges (AdminOnlyAccessPolicy til mailregistreringer af sikre vedhæftede filer). Når du senere redigerer politikken for vedhæftede filer, eller du får vist indstillingerne, vises standardnavnet for karantænepolitikken.

   - **Omdiriger meddelelser med registrerede vedhæftede filer**: Hvis du vælger **Aktivér omdirigering**, kan du angive en mailadresse i feltet **Send meddelelser, der indeholder blokerede, overvågede eller erstattede vedhæftede filer til den angivne mailadresse** for at sende meddelelser, der indeholder vedhæftede malwarefiler, til analyse og undersøgelse.

     Anbefalingen for Standard- og Strict-politikindstillinger er at aktivere omdirigering. Du kan få flere oplysninger under [Indstillinger for vedhæftede filer, der er tillid til](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - **Anvend registreringssvaret Sikre vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout eller fejl)**: Den handling, der er angivet af **Sikre vedhæftede filer, ukendt malwaresvar** , udføres på meddelelser, selvom scanningen af sikre vedhæftede filer ikke kan fuldføres. Hvis du har valgt denne indstilling, skal du altid vælge **Aktivér omdirigering** og angive en mailadresse for at sende meddelelser, der indeholder vedhæftede filer med skadelig software. Ellers kan meddelelser gå tabt.

   Klik på **Næste**, når du er færdig.

6. Gennemse dine indstillinger på siden **Gennemse** , der vises. Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

7. Klik på **Udført** på den bekræftelsesside, der vises.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Brug Microsoft 365 Defender-portalen til at få vist politikker for vedhæftede filer, der er tillid til

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Vedhæftede filer, der er tillid** til, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Vedhæftede filer** , der er tillid til vises følgende egenskaber på listen over politikker:
   - **Navn**
   - **Status**
   - **Prioritet**

3. Når du vælger en politik ved at klikke på navnet, vises politikindstillingerne i et pop op-vindue.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Brug Microsoft 365 Defender-portalen til at redigere politikker for vedhæftede filer, der er tillid til

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Vedhæftede filer, der er tillid** til, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Vedhæftede filer, der er tillid til** skal du vælge en politik på listen ved at klikke på navnet.

3. I det pop op-vindue med politikoplysninger, der vises, skal du vælge **Rediger** i hvert afsnit for at redigere indstillingerne i sektionen. Du kan få flere oplysninger om indstillingerne i afsnittet [Brug portalen Microsoft 365 Defender til at oprette politikker for vedhæftede filer, der er tillid til](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) tidligere i denne artikel.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikken, skal du se følgende afsnit.

### <a name="enable-or-disable-safe-attachments-policies"></a>Aktivér eller deaktiver politikker for vedhæftede filer, der er tillid til

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Vedhæftede filer, der er tillid** til, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Vedhæftede filer, der er tillid til** skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se en af følgende værdier:
   - **Politik slået fra**: Hvis du vil aktivere politikken, skal du klikke på ![Slå ikonet til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** .
   - **Politik slået** til: Hvis du vil slå politikken fra, skal du klikke på ![Slå ikonet fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Sluk for den**.

4. I den bekræftelsesdialogboks, der vises, skal du klikke **på Slå til** eller **Slå fra**.

5. Klik på **Luk** i pop op-vinduet med politikoplysninger.

Tilbage på hovedpolitiksiden **vil statusværdien** for politikken være **Til** eller **Fra**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Angiv prioriteten for politikker for sikre vedhæftede filer

Politikker for sikre vedhæftede filer får som standard en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et lavere prioritetsnummer angiver en højere prioritet for politikken (0 er den højeste), og politikker behandles i prioriteret rækkefølge (politikker med højere prioritet behandles før politikker med lavere prioritet). Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

Du kan finde flere oplysninger om prioritetsrækkefølgen, og hvordan flere politikker evalueres og anvendes, under [Beskyttelse af mailrækkefølge og prioritet](how-policies-and-protections-are-combined.md).

Politikker for vedhæftede filer, der er tillid til, vises i den rækkefølge, de behandles (den første politik har **prioritetsværdien** 0).

**Bemærk**! På Microsoft 365 Defender-portalen kan du kun ændre prioriteten for politikken Vedhæftede filer, der er tillid til, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen for sikker vedhæftede filer (hvilket kan påvirke prioriteten af eksisterende regler).

Hvis du vil ændre prioriteten for en politik, skal du klikke på **Forøg prioritet** eller **Formindsk prioritet** i egenskaberne for politikken (du kan ikke direkte ændre **prioritetsnummeret** på portalen Microsoft 365 Defender). Det giver kun mening at ændre prioriteten for en politik, hvis du har flere politikker.

1. I Microsoft 365 Defender-portalen skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre vedhæftede filer** i afsnittet **Politikker**.

2. På siden **Vedhæftede filer, der er tillid til** skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se **Forøg prioritet** eller **Formindsk prioritet** baseret på den aktuelle prioritetsværdi og antallet af politikker:
   - Politikken med **prioritetsværdien** **0** har kun indstillingen **Formindsk prioritet** tilgængelig.
   - Politikken med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg prioritet** tilgængelig.
   - Hvis du har tre eller flere politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne **Forøg prioritet** og **Formindsk prioritet** tilgængelige.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg prioritet** eller ![formindsk prioritetsikon](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at ændre **prioritetsværdien** .

4. Når du er færdig, skal du klikke på **Luk** i pop op-vinduet med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Brug Microsoft 365 Defender-portalen til at fjerne politikker for vedhæftede filer, der er tillid til

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Vedhæftede filer, der er tillid** til, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Vedhæftede filer, der er tillid** til skal du vælge en brugerdefineret politik på listen ved at klikke på navnet på politikken.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet](../../media/m365-cc-sc-delete-icon.png) Slet politik **Slet politik**.

4. Klik på **Ja** i den bekræftelsesdialogboks, der vises.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for sikre vedhæftede filer

Som tidligere beskrevet består en politik for sikre vedhæftede filer af en politik for sikker vedhæftede filer og en regel for sikker vedhæftede filer.

I PowerShell er forskellen mellem politikker for sikre vedhæftede filer og regler for sikker vedhæftede filer synlig. Du administrerer politikker for sikre vedhæftede filer ved hjælp **\*af cmdlet'erne -SafeAttachmentPolicy** , og du administrerer regler for sikre vedhæftede filer ved hjælp **\*af -SafeAttachmentRule-cmdlet'erne** .

- I PowerShell skal du først oprette politikken for sikker vedhæftede filer og derefter oprette reglen for sikker vedhæftede filer, der identificerer den politik, som reglen gælder for.
- I PowerShell kan du ændre indstillingerne i politikken for sikker vedhæftede filer og reglen for sikker vedhæftet fil separat.
- Når du fjerner en politik for sikker vedhæftede filer fra PowerShell, fjernes den tilsvarende regel for sikre vedhæftede filer ikke automatisk og omvendt.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Brug PowerShell til at oprette politikker for sikre vedhæftede filer

Oprettelse af en politik for sikre vedhæftede filer i PowerShell er en proces med to trin:

1. Opret politikken for sikker vedhæftede filer.
2. Opret reglen for sikker vedhæftet fil, der angiver politikken for sikker vedhæftet fil, som reglen gælder for.

 **Noter**:

- Du kan oprette en ny regel for sikre vedhæftede filer og tildele den en eksisterende politik for ikke-tilknyttet sikker vedhæftet fil. En regel for sikre vedhæftede filer kan ikke knyttes til mere end én politik for sikker vedhæftede filer.

- Du kan konfigurere følgende indstillinger for nye politikker for sikre vedhæftede filer i PowerShell, der ikke er tilgængelige på Microsoft 365 Defender-portalen, før du har oprettet politikken:
  - Opret den nye politik som deaktiveret (_aktiveret_ `$false` på Cmdlet'en **New-SafeAttachmentRule** ).
  - Angiv prioriteten for politikken under oprettelse (_prioritet_ _\<Number\>_) på cmdlet'en **New-SafeAttachmentRule** .

- En ny politik for sikre vedhæftede filer, som du opretter i PowerShell, er ikke synlig på Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for sikker vedhæftet fil.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Trin 1: Brug PowerShell til at oprette en politik for sikker vedhæftede filer

Hvis du vil oprette en politik for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

I dette eksempel oprettes en politik for sikre vedhæftede filer med navnet Contoso All med følgende værdier:

- Bloker meddelelser, der findes at indeholde malware ved scanning af sikre dokumenter (vi bruger ikke parameteren _Action_ , og standardværdien er `Block`).
- Standard [karantænepolitikken](quarantine-policies.md) bruges (AdminOnlyAccessPolicy), fordi vi ikke bruger parameteren _QuarantineTag_ .
- Omdirigering er aktiveret, og meddelelser, der indeholder malware, sendes til sec-ops@contoso.com til analyse og undersøgelse.
- Hvis scanning af vedhæftede filer, der er tillid til, ikke er tilgængelig eller støder på fejl, skal du ikke levere meddelelsen (vi bruger ikke parameteren _ActionOnError_ , og standardværdien er `$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Du kan finde detaljerede instruktioner til, hvordan du angiver den [karantænepolitik](quarantine-policies.md) , der skal bruges i en politik for sikre vedhæftede filer, under [Brug PowerShell til at angive karantænepolitikken i Politikker for vedhæftede filer, der er tillid til](quarantine-policies.md#safe-attachments-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>Trin 2: Brug PowerShell til at oprette en sikker regel for vedhæftede filer

Hvis du vil oprette en regel for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

I dette eksempel oprettes en regel for sikre vedhæftede filer med navnet Contoso All med følgende betingelser:

- Reglen er knyttet til politikken for sikker vedhæftet fil med navnet Contoso All.
- Reglen gælder for alle modtagere i det contoso.com domæne.
- Da vi ikke bruger parameteren _Prioritet_ , bruges standardprioriteten.
- Reglen er aktiveret (vi bruger ikke parameteren _Enabled_ , og standardværdien er `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Brug PowerShell til at få vist politikker for sikre vedhæftede filer

Hvis du vil have vist eksisterende politikker for sikre vedhæftede filer, skal du bruge følgende syntaks:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle politikker for sikre vedhæftede filer.

```PowerShell
Get-SafeAttachmentPolicy
```

I dette eksempel returneres detaljerede oplysninger om politikken for sikker vedhæftede filer med navnet Contoso Executives.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Brug PowerShell til at få vist regler for sikre vedhæftede filer

Hvis du vil have vist eksisterende regler for sikre vedhæftede filer, skal du bruge følgende syntaks:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle regler for sikre vedhæftede filer.

```PowerShell
Get-SafeAttachmentRule
```

Hvis du vil filtrere listen efter aktiverede eller deaktiverede regler, skal du køre følgende kommandoer:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

I dette eksempel returneres detaljerede oplysninger om reglen for sikker vedhæftet fil med navnet Contoso Executives.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Brug PowerShell til at ændre politikker for sikre vedhæftede filer

Du kan ikke omdøbe en politik for sikre vedhæftede filer i PowerShell ( **Cmdlet'en Set-SafeAttachmentPolicy** har ingen _navneparameter_ ). Når du omdøber en politik for sikre vedhæftede filer på Microsoft 365 Defender-portalen, omdøber du kun _reglen_ for sikre vedhæftede filer.

Ellers er de samme indstillinger tilgængelige, når du opretter en politik for sikker vedhæftede filer, som beskrevet i [trin 1: Brug PowerShell til at oprette en politik for sikker vedhæftede filer](#step-1-use-powershell-to-create-a-safe-attachment-policy) tidligere i denne artikel.

Hvis du vil ændre en politik for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Du kan finde detaljerede instruktioner til, hvordan du angiver den [karantænepolitik](quarantine-policies.md) , der skal bruges i en politik for sikre vedhæftede filer, under [Brug PowerShell til at angive karantænepolitikken i Politikker for vedhæftede filer, der er tillid til](quarantine-policies.md#safe-attachments-policies-in-powershell).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Brug PowerShell til at ændre regler for sikre vedhæftede filer

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en regel for sikker vedhæftet fil i PowerShell, er parameteren _Enabled_ , der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for sikre vedhæftede filer, skal du se næste afsnit.

Ellers er de samme indstillinger tilgængelige, når du opretter en regel som beskrevet i [trin 2: Brug PowerShell til at oprette en regel for sikker vedhæftede filer](#step-2-use-powershell-to-create-a-safe-attachment-rule) tidligere i denne artikel.

Hvis du vil ændre en regel for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for sikre vedhæftede filer

Aktivering eller deaktivering af en regel for sikre vedhæftede filer i PowerShell aktiverer eller deaktiverer hele politikken for vedhæftede filer, der er tillid til (reglen for sikker vedhæftede filer og den tildelte politik for sikker vedhæftede filer).

Hvis du vil aktivere eller deaktivere en regel for sikre vedhæftede filer i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen for sikre vedhæftede filer med navnet Marketingafdeling.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

I dette eksempel aktiveres samme regel.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) og [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Brug PowerShell til at angive prioriteten for regler for sikre vedhæftede filer

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten for en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten for en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten for en regel for sikre vedhæftede filer i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten for reglen marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, reduceres med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Bemærk**! Hvis du vil angive prioriteten for en ny regel, når du opretter den, skal du i stedet bruge parameteren _Priority_ på cmdlet'en **New-SafeAttachmentRule** .

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Brug PowerShell til at fjerne politikker for sikre vedhæftede filer

Når du bruger PowerShell til at fjerne en politik for sikker vedhæftet fil, fjernes den tilsvarende regel for sikre vedhæftede filer ikke.

Hvis du vil fjerne en politik for sikre vedhæftede filer i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for sikre vedhæftede filer med navnet Marketingafdeling.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Brug PowerShell til at fjerne regler for sikre vedhæftede filer

Når du bruger PowerShell til at fjerne en regel for sikker vedhæftet fil, fjernes den tilsvarende politik for sikre vedhæftede filer ikke.

Hvis du vil fjerne en regel for sikre vedhæftede filer i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for sikre vedhæftede filer med navnet Marketingafdeling.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har oprettet, ændret eller fjernet politikker for vedhæftede filer, der er tillid til:

- Kontrollér listen over politikker, deres **Statusværdier** og deres **prioritetsværdier** på siden **Vedhæftede filer, der er tillid** til på portalen Microsoft 365 Defender på <https://security.microsoft.com/safeattachmentv2>. Hvis du vil have vist flere oplysninger, skal du vælge politikken på listen ved at klikke på navnet og få vist detaljerne i fluesedlen.

- I Exchange Online PowerShell eller Exchange Online Protection PowerShell skal du erstatte \<Name\> med navnet på politikken eller reglen, køre følgende kommando og kontrollere indstillingerne:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Hvis du vil kontrollere, at Sikre vedhæftede filer scanner meddelelser, skal du kontrollere de tilgængelige Defender for Office 365 rapporter. Du kan få flere oplysninger under [Få vist rapporter for Defender for Office 365](view-reports-for-mdo.md) og [Brug Stifinder på Microsoft 365 Defender-portalen](threat-explorer.md).
