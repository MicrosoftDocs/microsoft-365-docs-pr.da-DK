---
title: Konfigurer antiphishing-politikker i EOP
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
description: Administratorer kan lære, hvordan de opretter, redigerer og sletter antiphishing-politikker, der er tilgængelige i Exchange Online Protection (EOP)-organisationer med eller uden Exchange Online postkasser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6321dcb41e276ccd03d048033e063572506a3c0f
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63588408"
---
# <a name="configure-anti-phishing-policies-in-eop"></a>Konfigurer antiphishing-politikker i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser er der en standard antiphishing-politik, der indeholder et begrænset antal antispoofing-funktioner, der er aktiveret som standard. Du kan finde flere oplysninger [under Indstillinger for spoof i antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

Administratorer kan få vist, redigere og konfigurere (men ikke slette) standardpolitikken for phishing. Hvis du vil have større granularitet, kan du også oprette brugerdefinerede antiphishing-politikker, der gælder for bestemte brugere, grupper eller domæner i organisationen. Brugerdefinerede politikker tilsidesætter altid standardpolitikken, men du kan ændre prioriteten (rækkefølgen) for dine brugerdefinerede politikker.

Organisationer med Exchange Online-postkasser kan konfigurere antiphishing-politikker i Microsoft 365 Defender-portalen eller Exchange Online PowerShell. Enkeltstående EOP-organisationer kan kun bruge Microsoft 365 Defender-portalen.

Hvis du vil have mere at vide om at oprette og ændre de mere avancerede antiphishing-politikker, der er tilgængelige i Microsoft Defender til Office 365, skal du se Konfigurer [antiphishing-politikker i Microsoft Defender til Office 365](configure-mdo-anti-phishing-policies.md).

De grundlæggende elementer i en antiphishingpolitik er:

- **Antiphish-politikken**: Angiver beskyttelse mod phishing for at aktivere eller deaktivere samt de handlinger, der skal anvendes indstillinger.
- **Antiphish-reglen**: Angiver prioritets- og modtagerfiltre (hvem politikken gælder for) for en antiphish-politik.

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer antiphishing-politikker Microsoft 365 Defender-portalen:

- Når du opretter en antiphishingpolitik, opretter du faktisk en antiphish-regel og den tilknyttede antiphish-politik på samme tid med det samme navn til begge.
- Når du ændrer en antiphishingpolitik, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltrene ændrer antiphish-reglen. Alle andre indstillinger ændrer den tilknyttede antiphish-politik.
- Når du fjerner en antiphishing-politik, fjernes antiphish-reglen og den tilknyttede antiphish-politik.

I Exchange Online PowerShell administrerer du politikken og reglen separat. Du kan finde flere oplysninger [i afsnittet Brug Exchange Online PowerShell til at konfigurere antiphishing-politikker](#use-exchange-online-powershell-to-configure-anti-phishing-policies) senere i denne artikel.

Hver organisation har en indbygget antiphishing-politik, der hedder Office365 AntiPhish Default, som har disse egenskaber:

- Politikken anvendes på alle modtagere i organisationen, selvom der ikke er knyttet nogen antiphish-regel (modtagerfiltre) til politikken.
- Politikken har den brugerdefinerede **prioritetsværdi Laveste** , som du ikke kan ændre (politikken anvendes altid sidst). Eventuelle brugerdefinerede politikker, du opretter, har altid en højere prioritet.
- Politikken er standardpolitikken (egenskaben **IsDefault** har værdien ), `True`og du kan ikke slette standardpolitikken.

For at øge effektiviteten af beskyttelse mod phishing kan du oprette brugerdefinerede antiphishing-politikker med mere restriktive indstillinger, der anvendes til bestemte brugere eller grupper af brugere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

  Du kan ikke administrere antiphishing-politikker i enkeltstående EOP PowerShell.

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil tilføje, redigere og slette antiphishing-politikker, skal du være medlem af **rollegrupperne** Organisationsadministration **eller Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til antiphishing-politikker, skal du være medlem af **rollegrupperne Global læser** **eller** Sikkerhedslæser.

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration [i Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen <sup>\*</sup>.

- Se vores anbefalede indstillinger for antiphishing-politikker under [Politikindstillinger for EOP-antiphishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

- Der kan gå op til 30 minutter, før den opdaterede politik anvendes.

- Du kan finde oplysninger om, hvor antiphishing-politikker anvendes i filtreringspipelinen, under Rækkefølge [og prioriteret mailbeskyttelse](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Brug portalen Microsoft 365 Defender til at oprette antiphishing-politikker

Oprettelse af en brugerdefineret antiphishingpolitik i Microsoft 365 Defender-portalen opretter antiphish-reglen og den tilknyttede antiphish-politik på samme tid med samme navn for begge.

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. Klik på **Opret ikon på** siden Antiphishing ![.](../../media/m365-cc-sc-create-icon.png) **Opret**.

3. Guiden politik åbnes. På siden **Politiknavn** skal du konfigurere disse indstillinger:
   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på Næste, når du er **færdig**.

4. På siden **Brugere, grupper og domæner, der** vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter i organisationen.
   - **Grupper**: De angivne distributionsgrupper, mailaktiverede sikkerhedsgrupper eller Microsoft 365 grupper i organisationen.
   - **Domæner:** Alle modtagere på de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i organisationen.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi i resultaterne. Gentag denne proces så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, visningsnavn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at få vist alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere, grupper** og domæner: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (undtagelser til modtagere), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på Næste, når du er **færdig**.

5. På siden **Phishing-&,** der vises, skal du bruge afkrydsningsfeltet Aktivér efterlignet intelligens til at slå efterlignet intelligens til eller fra. Standardværdien er valgt (valgt), og vi anbefaler, at du lader den være tændt. Du konfigurerer handlingen til at gøre følgende for blokerede efterlignede meddelelser på næste side.

   Hvis du vil deaktivere efterlignet intelligens, skal du fjerne markeringen i afkrydsningsfeltet.

   > [!NOTE]
   > Du behøver ikke at deaktivere beskyttelse mod spoofing, hvis din MX-post ikke peger på Microsoft 365. Du skal i stedet aktivere Udvidet filtrering for forbindelser. Du kan finde en [vejledning under Udvidet filtrering for forbindelser i Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Klik på Næste, når du er **færdig**.

6. På siden **Handlinger** , der vises, skal du konfigurere følgende indstillinger:
   - **Hvis meddelelsen registreres som efterlignet**: Denne indstilling er kun tilgængelig, hvis du har valgt **Aktivér efterlignet intelligens** på den forrige side. Vælg en af følgende handlinger på rullelisten for meddelelser fra blokerede spoof-afsendere:
     - **Flyt meddelelsen til modtagernes mapper med uønsket mail**
     - **An karantæne af meddelelsen**: Hvis du vælger denne handling,  vises et anvend karantænepolitikfelt, hvor du vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af efterlignet intelligencebeskyttelse. Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne, og om brugerne modtager beskeder om karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

       En tom **værdi for Anvend karantænepolitik** betyder, at standardpolitikken for karantæne bruges (DefaultFullAccessPolicy til oplysninger om spoof-intelligens). Når du senere redigerer antiphishing-politikken eller får vist indstillingerne, vises politikkens standardpolitiknavn i karantæne. Du kan finde flere oplysninger om standardkarantænepolitikker, der bruges til understøttet filtrering af beskyttelse, i [denne tabel](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features).

   - **Sikkerhedstip & indikatorer**:
     - **Vis første kontakt sikkerhedstip**: Du kan få mere at vide under [Første sikkerhedstip](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Vis (?) for** ikke-godkendte afsendere for spoof <sup>\*</sup>: Føjer et spørgsmålstegn (?) til afsenderens billede i feltet Fra i Outlook, hvis meddelelsen ikke passerer SPF- eller DKIM-kontroller, og meddelelsen ikke består DMARC- eller [ikke-sammensat godkendelse](email-validation-and-authentication.md#composite-authentication).
     - **Vis "via"-mærket**<sup>\*</sup>: Føjer et via-mærke (chris@contoso.com via fabrikam.com) til Fra-adressen, hvis det er forskelligt fra domænet i DKIM-signaturen eller **MAIL FRA-adressen** .

     Hvis du vil aktivere en indstilling, skal du markere afkrydsningsfeltet. Hvis du vil deaktivere den, skal du fjerne markeringen i afkrydsningsfeltet.

     <sup>\*</sup> Denne indstilling er kun tilgængelig, hvis du har **valgt Aktivér efterlignet intelligens** på den forrige side. Du kan finde flere [oplysninger under Ikke-godkendt afsender](set-up-anti-phishing-policies.md#unauthenticated-sender).

   Klik på Næste, når du er **færdig**.

7. Gennemgå dine **indstillinger** på siden Gennemse, der vises. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Send, når du er **færdig**.

8. Klik på Udført på bekræftelsessiden, der **vises**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Brug portalen Microsoft 365 Defender til at få vist antiphishing-politikker

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. På **siden Antiphishing** vises følgende egenskaber på listen over politikker:

   - **Navn**
   - **Status**
   - **Prioritet**
   - **Senest ændret**

3. Når du vælger en politik ved at klikke på navnet, vises politikindstillingerne i en pop op-meddelelse.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Brug portalen Microsoft 365 Defender til at ændre antiphishing-politikker

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Antiphishing** skal du vælge en politik på listen ved at klikke på navnet.

3. I pop op-vindue med politikoplysninger skal du **vælge Rediger** i hver sektion for at ændre indstillingerne i sektionen. Du kan finde flere oplysninger om indstillingerne i [afsnittet Brug Microsoft 365 Defender til at oprette antiphishing-politikker](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) tidligere i denne artikel.

   For standardpolitikken for phishing er afsnittet Brugere **,** grupper og domæner ikke tilgængelig (politikken gælder for alle), og du kan ikke omdøbe politikken.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikker, skal du se følgende afsnit.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Aktivere eller deaktivere brugerdefinerede antiphishing-politikker

Du kan ikke deaktivere standardpolitikken for phishing.

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Antiphishing** skal du vælge en brugerdefineret politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist en af følgende værdier:
   - **Politik deaktiveret**: Hvis du vil aktivere politikken, skal du klikke ![på ikonet Slå til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå til** .
   - **Politik slået til**: Hvis du vil deaktivere politikken, skal du klikke ![på Ikonet Slå fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå fra**.

4. I bekræftelsesdialogboksen, der vises, skal **du klikke på Aktivér** **eller Slå fra**.

5. Klik **på Luk** i pop op-menuen med politikoplysninger.

Tilbage på hovedpolitiksiden vil **politikkens statusværdi** **være Til eller** **Fra**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Angiv prioriteten af brugerdefinerede antiphishing-politikker

Antiphishing-politikker prioriteres som standard baseret på den rækkefølge, de er blevet oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et tal for lavere prioritet angiver en højere prioritet for politikken (0 er den højeste), og politikkerne behandles i prioritetsrækkefølgen (politikker med højere prioritet behandles før politikker med lavere prioritet). Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

Hvis du vil ændre prioriteten af en politik, skal du klikke  på Forøg prioritet eller Formindsk prioritet i egenskaberne for politikken (du kan ikke direkte ændre tallet prioritet i Microsoft 365 Defender portal). Det giver kun mening at ændre prioriteten af en politik, hvis du har flere politikker.

 **Bemærkninger**:

- I Microsoft 365 Defender-portalen kan du kun ændre prioriteten af antiphishing-politikken, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter antiphish-reglen (som kan påvirke prioriteten af eksisterende regler).
- Antiphishing-politikker behandles i den rækkefølge, de vises i (den første politik har **værdien Prioritet** 0). Standardpolitikken for phishing har prioritetsværdien **Laveste**, og du kan ikke ændre den.

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Antiphishing** skal du vælge en brugerdefineret politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist  Forøg  prioritet eller Formindsk prioritet baseret på den aktuelle prioritetsværdi og antallet af brugerdefinerede politikker:
   - Politikken med værdien **Prioritet** **0 har** kun indstillingen **Formindsk** prioritet tilgængelig.
   - Politikken med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg** prioritet tilgængelig.
   - Hvis du har tre eller flere politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne Forøg **prioritet** **og Formindsk** prioritet.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg** prioritet ![eller ikonet Formindsk prioritet](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at **ændre værdien** Prioritet.

4. Når du er færdig, skal du **klikke på** Luk i pop op-menuen med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Brug portalen Microsoft 365 Defender til at fjerne brugerdefinerede antiphishing-politikker

Når du bruger portalen Microsoft 365 Defender til at fjerne en brugerdefineret antiphishing-politik, slettes begge antiphish-reglen og den tilsvarende antiphish-politik. Du kan ikke fjerne standardpolitikken for phishing.

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til  & **politikker** \> for **samarbejde & Politikker** \> \> for trussel mod **phishing** i **sektionen** Politikker. For at gå direkte til **antiphishing-siden** skal du bruge <https://security.microsoft.com/antiphishing>.

2. På siden **Antiphishing** skal du vælge en brugerdefineret politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet Slet politik **Slet**](../../media/m365-cc-sc-delete-icon.png) politik.

4. Klik på Ja i bekræftelsesdialogboksen, der **vises**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Brug Exchange Online PowerShell til at konfigurere antiphishing-politikker

Som beskrevet tidligere består en antiphishingpolitik af en antiphish-politik og en antiphish-regel.

I Exchange Online PowerShell ses forskellen mellem antiphish-politikker og antiphish-regler. Du administrerer antiphish-politikker ved hjælp af cmdlet'erne -AntiPhishPolicy, og du administrerer antiphish-regler **\*** ved hjælp af cmdlet'erne -AntiPhishRule.**\***

- I PowerShell opretter du først antiphish-politikken, og derefter opretter du antiphish-reglen, der identificerer den politik, som reglen gælder for.
- I PowerShell skal du ændre indstillingerne i antiphish-politikken og antiphish-reglen separat.
- Når du fjerner en antiphish-politik fra PowerShell, fjernes den tilsvarende antiphish-regel ikke automatisk og omvendt.

> [!NOTE]
> Følgende PowerShell-procedurer er ikke tilgængelige i enkeltstående EOP-organisationer, der bruger Exchange Online Protection PowerShell.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Brug PowerShell til at oprette antiphishing-politikker

Oprettelse af en antiphishingpolitik i PowerShell er en proces i to trin:

1. Opret antiphish-politikken.
2. Opret den antiphish-regel, der angiver den antiphish-politik, som reglen gælder for.

 **Bemærkninger**:

- Du kan oprette en ny antiphish-regel og tildele den en eksisterende, ikke-tilknyttet antiphish-politik. En antiphish-regel kan ikke være knyttet til mere end én antiphish-politik.

- Du kan konfigurere følgende indstillinger for nye antiphish-politikker i PowerShell, der ikke er tilgængelige i Microsoft 365 Defender-portalen, før du har oprettet politikken:

  - Opret den nye politik som _deaktiveret (_ `$false` Aktiveret på **cmdlet'en New-AntiPhishRule** ).
  - Angiv prioriteten af politikken under oprettelsen (_Prioritet_ _\<Number\>_) på **cmdlet'en New-AntiPhishRule** ).

- En ny antiphish-politik, som du opretter i PowerShell, er ikke synlig i Microsoft 365 Defender-portalen, før du tildeler politikken til en antiphish-regel.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Trin 1: Brug PowerShell til at oprette en antiphish-politik

Hvis du vil oprette en antiphish-politik, skal du bruge denne syntaks:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSpoofIntelligence <$true | $false>] [-AuthenticationFailAction <MoveToJmf | Quarantine>] [-EnableUnauthenticatedSender <$true | $false>] [-EnableViaTag <$true | $false>] [-SpoofQuarantineTag <QuarantineTagName>]
```

I dette eksempel oprettes en antiphish-politik med navnet Research Quarantine med følgende indstillinger:

- Beskrivelsen er: Afdelingspolitik for undersøgelser.
- Ændrer standardhandlingen for spoofing-registreringer til Karantæne og bruger standardkarantænepolitikken [for meddelelser](quarantine-policies.md) , der er sat i karantæne (vi bruger ikke _parameteren SpoofQuarantineTag_ ).

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Hvis du vil have detaljeret vejledning [](quarantine-policies.md) til at angive karantænepolitikker, der skal bruges i en antiphish-politik, skal du se Brug PowerShell til at angive karantænepolitikken i [antiphishing-politikker](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Trin 2: Brug PowerShell til at oprette en antiphish-regel

Hvis du vil oprette en antiphish-regel, skal du bruge denne syntaks:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

I dette eksempel oprettes en antiphish-regel med navnet Forskningsafdeling med følgende betingelser:

- Reglen er knyttet til antiphish-politikken med navnet Research Quarantine.
- Reglen gælder for medlemmer af gruppen med navnet Forskningsafdeling.
- Da vi ikke bruger parameteren _Prioritet_ , bruges standardprioriteten.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Brug PowerShell til at få vist antiphish-politikker

Hvis du vil have vist eksisterende antiphish-politikker, skal du bruge følgende syntaks:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle antiphish-politikker sammen med de angivne egenskaber.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

I dette eksempel returneres alle egenskabsværdierne for antiphish-politikken, der hedder Direktører.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Brug PowerShell til at få vist antiphish-regler

Hvis du vil have vist eksisterende antiphish-regler, skal du bruge følgende syntaks:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigtsliste over alle antiphish-regler sammen med de angivne egenskaber.

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

I dette eksempel returneres alle egenskabsværdierne for antiphish-reglen Contoso-ledere.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Du kan finde detaljerede oplysninger om syntaks [og parameter i Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Brug PowerShell til at ændre antiphish-politikker

Ud over følgende elementer er de samme indstillinger tilgængelige, når du ændrer en antiphish-politik i PowerShell, som når du opretter en politik som beskrevet i Trin 1: Brug PowerShell til at oprette en [antiphish-politik](#step-1-use-powershell-to-create-an-anti-phish-policy) tidligere i denne artikel.

- _MakeDefault-parameteren_, der ændrer den angivne politik til standardpolitikken (gælder for alle, altid Laveste prioritet, og du kan ikke slette den) er kun tilgængelig, når du redigerer en antiphish-politik i PowerShell.
- Du kan ikke omdøbe en antiphish-politik ( **cmdlet'en Set-AntiPhishPolicy** har ingen _Navne-parameter_ ). Når du omdøber en antiphishingpolitik i Microsoft 365 Defender, omdøber du kun antiphish-reglen.

Hvis du vil ændre en antiphish-politik, skal du bruge denne syntaks:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Hvis du vil have detaljeret vejledning [](quarantine-policies.md) til at angive karantænepolitikken, der skal bruges i en antiphish-politik, skal du se Brug PowerShell til at angive karantænepolitikken i [antiphishing-politikker](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Brug PowerShell til at ændre antiphish-regler

Den eneste indstilling, der ikke er tilgængelig, når du redigerer en antiphish-regel i PowerShell, er parameteren _Enabled_ , der gør det muligt at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende antiphish-regler, skal du se næste afsnit.

Ellers er de samme indstillinger tilgængelige, når du opretter en regel som beskrevet i trin 2: Brug PowerShell til at oprette en [antiphish-regelsektion](#step-2-use-powershell-to-create-an-anti-phish-rule) tidligere i denne artikel.

Hvis du vil ændre en antiphish-regel, skal du bruge denne syntaks:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Brug PowerShell til at aktivere eller deaktivere antiphish-regler

Aktivering eller deaktivering af en antiphish-regel i PowerShell aktiverer eller deaktiverer hele antiphishing-politikken (antiphish-reglen og den tildelte antiphish-politik). Du kan ikke aktivere eller deaktivere standardpolitikken for phishing (den anvendes altid på alle modtagere).

Hvis du vil aktivere eller deaktivere en antiphish-regel i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen om antiphish med navnet Marketingafdeling.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

I dette eksempel kan du bruge den samme regel.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) [og Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Brug PowerShell til at angive prioriteten af antiphish-regler

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten af en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten af en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten af en antiphish-regel i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten af reglen Marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, formindskes med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Bemærkninger**:

- Hvis du vil angive prioriteten af en ny regel, når du opretter den, skal du bruge parameteren _Prioritet_ på **cmdlet'en New-AntiPhishRule** i stedet.
- Standardpolitikken for phish har ikke en tilsvarende antiphish-regel, og den har altid den uændrede prioritetsværdi **Laveste**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Brug PowerShell til at fjerne antiphish-politikker

Når du bruger PowerShell til at fjerne en antiphish-politik, fjernes den tilsvarende antiphish-regel ikke.

Hvis du vil fjerne en antiphish-politik i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for antiphish med navnet Marketingafdeling.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Brug PowerShell til at fjerne antiphish-regler

Når du bruger PowerShell til at fjerne en antiphish-regel, fjernes den tilsvarende antiphish-politik ikke.

Hvis du vil fjerne en antiphish-regel i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen om antiphish med navnet Marketingafdeling.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

For at bekræfte, at du har konfigureret antiphishing-politikker i EOP, skal du gøre et af følgende:

- På siden **Antiphishing** i Microsoft 365 Defender på <https://security.microsoft.com/antiphishing>, skal du bekræfte listen over politikker, deres **Statusværdier** og deres **Prioritetsværdier**. Hvis du vil have vist flere detaljer, skal du vælge politikken på listen ved at klikke på navnet og få vist oplysningerne i pop op-menuen, der vises.

- I Exchange Online PowerShell skal du \<Name\> erstatte med navnet på politikken eller reglen, køre følgende kommando og kontrollere indstillingerne:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
