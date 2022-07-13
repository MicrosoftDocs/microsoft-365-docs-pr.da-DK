---
title: Konfigurer politikker for antiphishing i EOP
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
description: Administratorer kan få mere at vide om, hvordan de opretter, redigerer og sletter de politikker til bekæmpelse af phishing, der er tilgængelige i Exchange Online Protection organisationer (EOP) med eller uden Exchange Online postkasser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8545eed078a676055206870e5c55ed3ca2e82a9a
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66773229"
---
# <a name="configure-anti-phishing-policies-in-eop"></a>Konfigurer politikker for antiphishing i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)

I Microsoft 365-organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser er der en standardpolitik for anti-phishing, der indeholder et begrænset antal anti-spoofing-funktioner, der er aktiveret som standard. Du kan få flere oplysninger under [Spoof-indstillinger i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#spoof-settings).

Administratorer kan få vist, redigere og konfigurere (men ikke slette) standardpolitikken til bekæmpelse af phishing. For at opnå større granularitet kan du også oprette brugerdefinerede anti-phishing-politikker, der gælder for bestemte brugere, grupper eller domæner i din organisation. Brugerdefinerede politikker har altid forrang frem for standardpolitikken, men du kan ændre prioriteten (kører rækkefølge) for dine brugerdefinerede politikker.

Organisationer med Exchange Online postkasser kan konfigurere politikker til bekæmpelse af phishing på Microsoft 365 Defender-portalen eller i Exchange Online PowerShell. Separate EOP-organisationer kan kun bruge portalen Microsoft 365 Defender.

Du kan få oplysninger om, hvordan du opretter og ændrer de mere avancerede politikker til bekæmpelse af phishing, der er tilgængelige i Microsoft Defender for Office 365, [under Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

De grundlæggende elementer i en anti-phishing-politik er:

- **Politikken til anti-phish**: Angiver den phishing-beskyttelse, der skal aktiveres eller deaktiveres, og de handlinger, der skal anvendes indstillinger.
- **Anti-phish-reglen**: Angiver prioritets- og modtagerfiltrene (hvem politikken gælder for) for en anti-phish-politik.

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer politikker til bekæmpelse af phishing på Microsoft 365 Defender portalen:

- Når du opretter en anti-phishing-politik, opretter du faktisk en anti-phish-regel og den tilknyttede anti-phish-politik på samme tid ved hjælp af det samme navn for begge.
- Når du ændrer en politik til bekæmpelse af phishing, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltre anti-phish-reglen. Alle andre indstillinger ændrer den tilknyttede anti-phish-politik.
- Når du fjerner en anti-phishing-politik, fjernes reglen for anti-phish og den tilknyttede anti-phish-politik.

I Exchange Online PowerShell kan du administrere politikken og reglen separat. Du kan få flere oplysninger i afsnittet [Brug Exchange Online PowerShell til at konfigurere politikker til anti-phishing](#use-exchange-online-powershell-to-configure-anti-phishing-policies) senere i denne artikel.

Alle organisationer har en indbygget anti-phishing-politik med navnet Office365 Antiphish Default, der har disse egenskaber:

- Politikken anvendes på alle modtagere i organisationen, selvom der ikke er knyttet nogen anti-phish-regel (modtagerfiltre) til politikken.
- Politikken har den brugerdefinerede prioritetsværdi **Laveste** , som du ikke kan ændre (politikken anvendes altid sidst). Alle brugerdefinerede politikker, du opretter, har altid en højere prioritet.
- Politikken er standardpolitikken (egenskaben **IsDefault** har værdien `True`), og du kan ikke slette standardpolitikken.

Hvis du vil øge effektiviteten af beskyttelse mod phishing, kan du oprette brugerdefinerede politikker til bekæmpelse af phishing med strengere indstillinger, der anvendes på bestemte brugere eller grupper af brugere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

  Du kan ikke administrere anti-phishing-politikker i enkeltstående EOP PowerShell.

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje, redigere og slette anti-phishing-politikker, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til anti-phishing-politikker, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen <sup>\*</sup>.

- Du kan se vores anbefalede indstillinger for politikker til anti-phishing under [Politikindstillinger for EOP til anti-phishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

- Der kan gå op til 30 minutter, før den opdaterede politik anvendes.

- Du kan finde oplysninger om, hvor anti-phishing-politikker anvendes i filtreringspipelinen, under [Rækkefølge af og prioritet for mailbeskyttelse](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Brug Microsoft 365 Defender-portalen til at oprette politikker til bekæmpelse af phishing

Når du opretter en brugerdefineret anti-phishing-politik på Microsoft 365 Defender-portalen, oprettes reglen for anti-phish og den tilknyttede anti-phish-politik samtidig med det samme navn for begge.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. Klik på Ikonet Opret på ![siden **Anti-phishing**.](../../media/m365-cc-sc-create-icon.png) **Opret**.

3. Politikguiden åbnes. Konfigurer disse indstillinger på siden **Politiknavn** :
   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på **Næste**, når du er færdig.

4. På siden **Brugere, grupper og domæner** , der vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
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

5. På **tærsklen for phishing & beskyttelsesside** , der vises, skal du bruge afkrydsningsfeltet **Aktivér spoof intelligence** til at slå spoof intelligence til eller fra. Standardværdien er slået til (valgt), og vi anbefaler, at du lader den være slået til. Du kan konfigurere den handling, der skal udføres på blokerede spoofede meddelelser på næste side.

   Hvis du vil slå spoof intelligence fra, skal du fjerne markeringen i afkrydsningsfeltet.

   > [!NOTE]
   > Du behøver ikke at slå beskyttelse mod spoofing fra, hvis din MX-post ikke peger på Microsoft 365. du aktiverer forbedret filtrering for forbindelser i stedet. Du kan finde instruktioner [under Udvidet filtrering for forbindelser i Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Klik på **Næste**, når du er færdig.

6. Konfigurer følgende indstillinger på siden **Handlinger** , der vises:
   - **Hvis meddelelsen registreres som spoof**: Denne indstilling er kun tilgængelig, hvis du har valgt **Aktivér spoof intelligence** på den forrige side. Vælg en af følgende handlinger på rullelisten for meddelelser fra blokerede spoofede afsendere:
     - **Flyt meddelelsen til modtagernes mapper med uønsket mail**
     - **Sæt meddelelsen i karantæne**: Hvis du vælger denne handling, vises feltet **Anvend karantænepolitik** , hvor du vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af spoof intelligence-beskyttelse. Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne, og om brugerne modtager karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).

       En tom værdi for **Anvend karantænepolitik** betyder, at standardkarantænepolitikken bruges (DefaultFullAccessPolicy for spoof intelligence-registreringer). Når du senere redigerer politikken til bekæmpelse af phishing eller får vist indstillingerne, vises standardnavnet for karantænepolitikken. Du kan få flere oplysninger om standard karantænepolitikker, der bruges til understøttede beskyttelsesfiltreringssigelser, i [denne tabel](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Sikkerhedstips & indikatorer**:
     - **Vis sikkerhedstip til første kontakt**: Du kan få flere oplysninger under [Første kontaktsikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Vis (?) for ikke-godkendte afsendere til spoof**<sup>\*</sup>: Føjer et spørgsmålstegn (?) til afsenderens foto i feltet Fra i Outlook, hvis meddelelsen ikke sender SPF- eller DKIM-kontroller, **og** meddelelsen ikke består DMARC- eller [sammensat godkendelse](email-validation-and-authentication.md#composite-authentication).
     - **Vis "via"-mærket**<sup>\*</sup>: Føjer en via-kode (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis den er forskellig fra domænet i **DKIM-signaturen eller MAIL FROM-adressen** .

     Hvis du vil aktivere en indstilling, skal du markere afkrydsningsfeltet. Hvis du vil slå den fra, skal du fjerne markeringen i afkrydsningsfeltet.

     <sup>\*</sup> Denne indstilling er kun tilgængelig, hvis du har valgt **Aktivér spoof intelligence** på den forrige side. Du kan få flere oplysninger under [Ikke-godkendte afsenderindikatorer](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).

   Klik på **Næste**, når du er færdig.

7. Gennemse dine indstillinger på siden **Gennemse** , der vises. Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

8. Klik på **Udført** på den bekræftelsesside, der vises.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Brug Microsoft 365 Defender-portalen til at få vist politikker til bekæmpelse af phishing

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** vises følgende egenskaber på listen over politikker:

   - **Navn**
   - **Status**
   - **Prioritet**
   - **Senest ændret**

3. Når du vælger en politik ved at klikke på navnet, vises politikindstillingerne i et pop op-vindue.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Brug Microsoft 365 Defender-portalen til at ændre politikker til bekæmpelse af phishing

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** skal du vælge en politik på listen ved at klikke på navnet.

3. I det pop op-vindue med politikoplysninger, der vises, skal du vælge **Rediger** i hvert afsnit for at redigere indstillingerne i sektionen. Du kan få flere oplysninger om indstillingerne i afsnittet [Brug portalen Microsoft 365 Defender til at oprette politikker til bekæmpelse af phishing](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) tidligere i denne artikel.

   I forbindelse med standardpolitikken til bekæmpelse af phishing er sektionen **Brugere, grupper og domæner** ikke tilgængelig (politikken gælder for alle), og du kan ikke omdøbe politikken.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikken, skal du se følgende afsnit.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Aktivér eller deaktiver brugerdefinerede anti-phishing-politikker

Du kan ikke deaktivere standardpolitikken til anti-phishing.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** skal du vælge en brugerdefineret politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se en af følgende værdier:
   - **Politik slået fra**: Hvis du vil aktivere politikken, skal du klikke på ![Slå ikonet til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Aktivér** .
   - **Politik slået** til: Hvis du vil slå politikken fra, skal du klikke på ![Slå ikonet fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Sluk for den**.

4. I den bekræftelsesdialogboks, der vises, skal du klikke **på Slå til** eller **Slå fra**.

5. Klik på **Luk** i pop op-vinduet med politikoplysninger.

Tilbage på hovedpolitiksiden **vil statusværdien** for politikken være **Til** eller **Fra**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Angiv prioriteten for brugerdefinerede anti-phishing-politikker

Som standard får anti-phishing-politikker en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et lavere prioritetsnummer angiver en højere prioritet for politikken (0 er den højeste), og politikker behandles i prioriteret rækkefølge (politikker med højere prioritet behandles før politikker med lavere prioritet). Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten for en politik, skal du klikke på **Forøg prioritet** eller **Formindsk prioritet** i egenskaberne for politikken (du kan ikke direkte ændre **prioritetsnummeret** på portalen Microsoft 365 Defender). Det giver kun mening at ændre prioriteten for en politik, hvis du har flere politikker.

 **Noter**:

- På Microsoft 365 Defender-portalen kan du kun ændre prioriteten for politikken til bekæmpelse af phishing, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter anti-phish-reglen (hvilket kan påvirke prioriteten af eksisterende regler).
- Politikker til bekæmpelse af phishing behandles i den rækkefølge, de vises i (den første politik har **prioritetsværdien** 0). Standardpolitikken mod phishing har prioritetsværdien **Laveste**, og du kan ikke ændre den.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** skal du vælge en brugerdefineret politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, kan du se **Forøg prioritet** eller **Formindsk prioritet** baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken med **prioritetsværdien** **0** har kun indstillingen **Formindsk prioritet** tilgængelig.
   - Politikken med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg prioritet** tilgængelig.
   - Hvis du har tre eller flere politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne **Forøg prioritet** og **Formindsk prioritet** tilgængelige.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg prioritet** eller ![formindsk prioritetsikon](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at ændre **prioritetsværdien** .

4. Når du er færdig, skal du klikke på **Luk** i pop op-vinduet med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Brug Microsoft 365 Defender-portalen til at fjerne brugerdefinerede politikker mod phishing

Når du bruger Microsoft 365 Defender-portalen til at fjerne en brugerdefineret anti-phishing-politik, slettes begge reglen om anti-phish og den tilsvarende anti-phish-politik. Du kan ikke fjerne standardpolitikken til anti-phishing.

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Anti-phishing** , skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** skal du vælge en brugerdefineret politik på listen ved at klikke på navnet.

3. Øverst i pop op-vinduet med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet](../../media/m365-cc-sc-delete-icon.png) Slet politik **Slet politik**.

4. Klik på **Ja** i den bekræftelsesdialogboks, der vises.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Brug Exchange Online PowerShell til at konfigurere politikker til bekæmpelse af phishing

Som tidligere beskrevet består en anti-phishing-politik af en anti-phish-politik og en anti-phish-regel.

I Exchange Online PowerShell er forskellen mellem anti-phish-politikker og anti-phish-regler synlig. Du administrerer anti-phish-politikker ved hjælp **\*af -AntiPhishPolicy-cmdlet'er** , og du administrerer anti-phish-regler ved hjælp **\*af -AntiPhishRule-cmdlet'erne** .

- I PowerShell skal du først oprette politikken for anti-phish og derefter oprette den anti-phish-regel, der identificerer den politik, som reglen gælder for.
- I PowerShell kan du ændre indstillingerne i politikken for anti-phish og anti-phish-reglen separat.
- Når du fjerner en anti-phish-politik fra PowerShell, fjernes den tilsvarende anti-phish-regel ikke automatisk og omvendt.

> [!NOTE]
> Følgende PowerShell-procedurer er ikke tilgængelige i separate EOP-organisationer, der bruger Exchange Online Protection PowerShell.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Brug PowerShell til at oprette politikker mod phishing

Oprettelse af en politik til bekæmpelse af phishing i PowerShell er en proces med to trin:

1. Opret politikken for anti-phish.
2. Opret den anti-phish-regel, der angiver den anti-phish-politik, som reglen gælder for.

 **Noter**:

- Du kan oprette en ny anti-phish-regel og tildele den en eksisterende, ikke-tilknyttet anti-phish-politik. Et anti-phish-regel kan ikke knyttes til mere end én anti-phish-politik.

- Du kan konfigurere følgende indstillinger for nye anti-phish-politikker i PowerShell, der ikke er tilgængelige på Microsoft 365 Defender-portalen, før du har oprettet politikken:

  - Opret den nye politik som deaktiveret (_aktiveret_ `$false` på **cmdlet'en New-AntiPhishRule** ).
  - Angiv prioriteten for politikken under oprettelse (_prioritet_ _\<Number\>_) på **cmdlet'en New-AntiPhishRule** .

- En ny anti-phish-politik, som du opretter i PowerShell, er ikke synlig på Microsoft 365 Defender-portalen, før du tildeler politikken til en anti-phish-regel.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Trin 1: Brug PowerShell til at oprette en anti-phish-politik

Hvis du vil oprette en anti-phish-politik, skal du bruge denne syntaks:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSpoofIntelligence <$true | $false>] [-AuthenticationFailAction <MoveToJmf | Quarantine>] [-EnableUnauthenticatedSender <$true | $false>] [-EnableViaTag <$true | $false>] [-SpoofQuarantineTag <QuarantineTagName>]
```

I dette eksempel oprettes en anti-phish-politik med navnet Research Quarantine med følgende indstillinger:

- Beskrivelsen er: Politik for forskningsafdeling.
- Ændrer standardhandlingen for spoofing-registreringer til Karantæne og bruger standard [karantænepolitikken](quarantine-policies.md) for de karantænede meddelelser (vi bruger ikke parameteren _SpoofQuarantineTag_ ).

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Du kan finde detaljerede instruktioner til, hvordan du angiver de [karantænepolitikker](quarantine-policies.md) , der skal bruges i en anti-phish-politik, under [Brug PowerShell til at angive karantænepolitikken i politikker til bekæmpelse af phishing](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Trin 2: Brug PowerShell til at oprette en anti-phish-regel

Brug denne syntaks til at oprette en anti-phish-regel:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

I dette eksempel oprettes en anti-phish-regel med navnet Forskningsafdeling med følgende betingelser:

- Reglen er knyttet til politikken for anti-phish med navnet Research Quarantine.
- Reglen gælder for medlemmer af gruppen med navnet Forskningsafdeling.
- Da vi ikke bruger parameteren _Prioritet_ , bruges standardprioriteten.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-AntiphishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Brug PowerShell til at få vist anti-phish-politikker

Hvis du vil have vist eksisterende anti-phish-politikker, skal du bruge følgende syntaks:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle anti-phish-politikker sammen med de angivne egenskaber.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

I dette eksempel returneres alle egenskabsværdierne for den anti-phish-politik med navnet Direktører.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Brug PowerShell til at få vist anti-phish-regler

Hvis du vil have vist eksisterende anti-phish-regler, skal du bruge følgende syntaks:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle anti-phish-regler sammen med de angivne egenskaber.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Hvis du vil filtrere listen efter aktiverede eller deaktiverede regler, skal du køre følgende kommandoer:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

I dette eksempel returneres alle egenskabsværdierne for anti-phish-reglen med navnet Contoso Executives.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-AntiphishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Brug PowerShell til at ændre anti-phish-politikker

Ud over følgende elementer er de samme indstillinger tilgængelige, når du ændrer en anti-phish-politik i PowerShell, som når du opretter en politik som beskrevet i [trin 1: Brug PowerShell til at oprette en anti-phish-politik](#step-1-use-powershell-to-create-an-anti-phish-policy) tidligere i denne artikel.

- Parameteren _MakeDefault_ , der ændrer den angivne politik til standardpolitikken (anvendt på alle, altid **laveste** prioritet, og du kan ikke slette den), er kun tilgængelig, når du ændrer en anti-phish-politik i PowerShell.
- Du kan ikke omdøbe en anti-phish-politik ( **Set-AntiPhishPolicy-cmdlet'en** har ingen _navneparameter_ ). Når du omdøber en politik til anti-phishing på Microsoft 365 Defender-portalen, omdøber du kun _anti-phish-reglen_.

Hvis du vil ændre en anti-phish-politik, skal du bruge denne syntaks:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Du kan finde detaljerede instruktioner til, hvordan du angiver den [karantænepolitik](quarantine-policies.md) , der skal bruges i en anti-phish-politik, under [Brug PowerShell til at angive karantænepolitikken i politikker til bekæmpelse af phishing](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Brug PowerShell til at ændre anti-phish-regler

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en anti-phish-regel i PowerShell, er den _aktiverede_ parameter, der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende anti-phish-regler, skal du se næste afsnit.

Ellers er de samme indstillinger tilgængelige, når du opretter en regel som beskrevet i [Trin 2: Brug PowerShell til at oprette en anti-phish-regelsektion](#step-2-use-powershell-to-create-an-anti-phish-rule) tidligere i denne artikel.

Hvis du vil ændre en anti-phish-regel, skal du bruge denne syntaks:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-AntiphishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Brug PowerShell til at aktivere eller deaktivere anti-phish-regler

Aktivering eller deaktivering af en anti-phish-regel i PowerShell aktiverer eller deaktiverer hele politikken til anti-phishing (anti-phish-reglen og den tildelte anti-phish-politik). Du kan ikke aktivere eller deaktivere standardpolitikken til anti-phishing (den anvendes altid på alle modtagere).

Hvis du vil aktivere eller deaktivere en anti-phish-regel i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen for anti-phish med navnet Marketing Department.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

I dette eksempel aktiveres samme regel.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) og [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Brug PowerShell til at angive prioriteten for anti-phish-regler

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten for en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten for en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten for en anti-phish-regel i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten for reglen marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, reduceres med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Noter**:

- Hvis du vil angive prioriteten for en ny regel, når du opretter den, skal du i stedet bruge parameteren _Priority_ på **cmdlet'en New-AntiPhishRule** .
- Standardpolitikken for anti-phish har ikke en tilsvarende anti-phish-regel, og den har altid den ikke-redigerbare prioritetsværdi **Laveste**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Brug PowerShell til at fjerne anti-phish-politikker

Når du bruger PowerShell til at fjerne en anti-phish-politik, fjernes den tilsvarende anti-phish-regel ikke.

Hvis du vil fjerne en anti-phish-politik i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for anti-phish med navnet Marketing Department.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Brug PowerShell til at fjerne anti-phish-regler

Når du bruger PowerShell til at fjerne en anti-phish-regel, fjernes den tilsvarende anti-phish-politik ikke.

Hvis du vil fjerne en anti-phish-regel i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for anti-phish med navnet Marketing Department.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-AntiphishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har konfigureret politikker til bekæmpelse af phishing i EOP:

- Kontrollér listen over politikker, deres **statusværdier** og **deres prioritetsværdier** på siden **Anti-phishing** på portalen Microsoft 365 Defender på <https://security.microsoft.com/antiphishing>. Hvis du vil have vist flere oplysninger, skal du vælge politikken på listen ved at klikke på navnet og få vist detaljerne i det pop op-vindue, der vises.

- I Exchange Online PowerShell skal du erstatte \<Name\> med navnet på politikken eller reglen, køre følgende kommando og kontrollere indstillingerne:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
