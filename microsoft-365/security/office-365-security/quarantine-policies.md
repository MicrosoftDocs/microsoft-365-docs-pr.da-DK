---
title: Karantænepolitik
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan de bruger karantænepolitikker til at styre, hvad brugerne kan gøre for at sætte meddelelser i karantæne.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2f24592460daa4f476e969069d0c1b7636f6a23e
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285538"
---
# <a name="quarantine-policies"></a>Karantænepolitik

Karantænepolitikker (tidligere kaldet _karantænetags_) i Exchange Online Protection (EOP) og Microsoft Defender for Office 365 gør det muligt for administratorer at styre, hvad brugerne kan gøre for at sætte meddelelser i karantæne baseret på, hvorfor meddelelsen blev sat i karantæne.

Brugere har traditionelt fået tilladelse til eller nægtet niveauer af interaktivitet for karantænemeddelelser baseret på, hvorfor meddelelsen blev sat i karantæne. Brugerne kan f.eks. få vist og frigive meddelelser, der er sat i karantæne af filtrering mod spam som spam eller masse, men de kan ikke få vist eller frigive meddelelser, der er sat i karantæne som phishing eller malware med høj sikkerhed.

I forbindelse med [understøttede beskyttelsesfunktioner](#step-2-assign-a-quarantine-policy-to-supported-features) angiver karantænepolitikker, hvad brugerne har tilladelse til at gøre med deres egne meddelelser (meddelelser, hvor de er modtager) i karantæne og i _karantænemeddelelser_. [Karantænemeddelelser](use-spam-notifications-to-release-and-report-quarantined-messages.md) er erstatning for spammeddelelser fra slutbrugere. Disse meddelelser styres nu af karantænepolitikker og indeholder oplysninger om karantænemeddelelser for alle understøttede beskyttelsesfunktioner (ikke kun anti-spam-politik og dom over phishing-politik).

Standard karantænepolitikker, der gennemtvinger de historiske brugeregenskaber, tildeles automatisk til handlinger i de understøttede beskyttelsesfunktioner, der sætter meddelelser i karantæne. Du kan også oprette brugerdefinerede karantænepolitikker og tildele dem til de understøttede beskyttelsesfunktioner for at tillade eller forhindre brugerne i at udføre bestemte handlinger på disse typer af karantænemeddelelser.

De individuelle tilladelser til karantænepolitik kombineres i følgende forudindstillede tilladelsesgrupper:

- Ingen adgang
- Begrænset adgang
- Fuld adgang

De individuelle karantænepolitiktilladelser, der findes i de forudindstillede tilladelsesgrupper, er beskrevet i følgende tabel:

|Tilladelse|Ingen adgang|Begrænset adgang|Fuld adgang|
|---|:---:|:---:|:---:|
|**Bloker afsender** (_PermissionToBlockSender_)||![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|**Slet** (_PermissionToDelete_)||![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|**Eksempelvisning** (_PermissionToPreview_)||![Markeret.](../../media/checkmark.png)|![Markeret.](../../media/checkmark.png)|
|**Tillad, at modtagere frigiver en meddelelse fra karantæne** (_PermissionToRelease_)|||![Markeret.](../../media/checkmark.png)|
|**Tillad, at modtagere anmoder om, at en meddelelse frigives fra karantæne** (_PermissionToRequestRelease_)||![Markeret](../../media/checkmark.png)||

Standardpolitikkerne for karantæne, deres tilknyttede tilladelsesgrupper, og om karantænemeddelelser er aktiveret, er beskrevet i følgende tabel:

|Standard karantænepolitik|Tilladelsesgruppe brugt|Er karantænemeddelelser aktiveret?|
|---|---|---|
|AdminOnlyAccessPolicy|Ingen adgang|Nej|
|DefaultFullAccessPolicy|Fuld adgang|Nej|
|NotificationEnabledPolicy<sup>\*</sup>|Fuld adgang|Ja|

Hvis du ikke kan lide standardtilladelserne i de forudindstillede tilladelsesgrupper, eller hvis du vil aktivere karantænemeddelelser, skal du oprette og bruge brugerdefinerede karantænepolitikker. Du kan finde flere oplysninger om, hvad hver tilladelse gør, i afsnittet [Oplysninger om tilladelse til karantænepolitik](#quarantine-policy-permission-details) senere i denne artikel.

Du opretter og tildeler karantænepolitikker på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med Exchange Online postkasser; enkeltstående EOP PowerShell i EOP-organisationer uden Exchange Online postkasser).

> [!NOTE]
> Hvor længe karantænemeddelelser opbevares i karantæne, før de udløber, kontrolleres af **Bevar spam i karantæne i dette antal dage** (_QuarantineRetentionPeriod_) i politikker for bekæmpelse af spam. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).
>
> Hvis du ændrer den karantænepolitik, der er tildelt til en understøttet beskyttelsesfunktion, påvirker ændringen meddelelser, der er sat i karantæne, _når_ du har foretaget ændringen. Meddelelser, der tidligere er sat i karantæne af denne beskyttelsesfunktion, påvirkes ikke af indstillingerne for den nye karantænepolitiktildeling.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Fuld adgangstilladelser og karantænemeddelelser

<sup>\*</sup> Karantænepolitikken med navnet NotificationEnabledPolicy findes ikke i alle miljøer. Du har karantænepolitikken NotificationEnabledPolicy, hvis din organisation opfylder begge følgende krav:

- Din organisation fandtes, før funktionen til karantænepolitik blev aktiveret (sent i juli/begyndelsen af august 2021).
- Du havde en eller flere [politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md) (standardpolitikken for spam eller brugerdefinerede politikker mod spam), hvor indstillingen **Aktivér slutbrugermeddelelser om spam** er slået til.

Som beskrevet tidligere erstatter karantænemeddelelser i karantænepolitikker slutbrugerens spammeddelelser, som du brugte til at aktivere eller deaktivere i politikker mod spam. Den indbyggede karantænepolitik med navnet DefaultFullAccessPolicy duplikerer de historiske _tilladelser_ til karantænemeddelelser, men _karantænemeddelelser_ er ikke slået til i karantænepolitikken. Og da du ikke kan ændre den indbyggede politik, kan du ikke aktivere karantænemeddelelser i DefaultFullAccessPolicy.

For at give tilladelserne til DefaultFullAccessPolicy, men med karantænemeddelelser slået til, har vi oprettet politikken med navnet NotificationEnabledPolicy, der skal bruges i stedet for DefaultFullAccessPolicy for de organisationer, der har brug for den (organisationer, hvor slutbrugerens spammeddelelser er slået til).

For nye organisationer eller ældre organisationer, der aldrig har haft meddelelser om uønsket post fra slutbrugere aktiveret i politikker for spam, har du ikke karantænepolitikken med navnet NotificationEnabledPolicy. Den måde, du kan aktivere karantænemeddelelser på, er ved at oprette og bruge brugerdefinerede karantænepolitikker, hvor karantænemeddelelser er slået til.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Karantænepolitikker** , skal du bruge <https://security.microsoft.com/quarantinePolicies>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Hvis du vil have vist, oprette, redigere eller fjerne karantænepolitikker, skal du være medlem af rollerne **Organisationsadministration**, **Sikkerhedsadministrator** eller **Karantæneadministrator** på Microsoft 365 Defender portalen. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Trin 1: Opret karantænepolitikker på Microsoft 365 Defender-portalen

1. På [Microsoft 365 Defender portal skal](https://security.microsoft.com) du gå til **Mail & samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Karantænepolitikker** i afsnittet **Regler**. Du kan også gå direkte til siden **Karantænepolitikker** ved at bruge <https://security.microsoft.com/quarantinePolicies>.

2. Klik på Ikonet Tilføj brugerdefineret politik på ![siden **Karantænepolitikker**.](../../media/m365-cc-sc-create-icon.png) **Tilføj brugerdefineret politik**.

3. Guiden **Ny politik** åbnes. Angiv et kort, men entydigt navn i feltet **Politiknavn** på siden **Politiknavn** . Du skal identificere og vælge karantænepolitikken efter navn i kommende trin. Klik på **Næste**, når du er færdig.

4. Vælg en af følgende værdier på **adgangssiden for modtagermeddelelsen** :
   - **Begrænset adgang**: De individuelle tilladelser, der er inkluderet i denne tilladelsesgruppe, beskrives tidligere i denne artikel.
   - **Angiv specifik adgang (avanceret):** Brug denne værdi til at angive brugerdefinerede tilladelser. Konfigurer følgende indstillinger, der vises:
     - **Vælg indstillinger for udgivelseshandling**: Vælg en af følgende værdier:
       - Tom: Dette er standardværdien.
       - **Tillad, at modtagere frigiver en meddelelse fra karantæne**
       - **Tillad, at modtagere anmoder om, at en meddelelse frigives fra karantæne**
     - **Vælg yderligere handlinger, som modtagere kan foretage i karantænemeddelelser**: Vælg nogle, alle eller ingen af følgende værdier:
       - **Slette**
       - **Preview**
       - **Afsender af blok**

   Disse tilladelser og deres virkning på karantænemeddelelser og i karantænemeddelelser er beskrevet i afsnittet [Oplysninger om tilladelse til karantænepolitik](#quarantine-policy-permission-details) senere i denne artikel.

   Klik på **Næste**, når du er færdig.

5. På siden **Med slutbrugerens spammeddelelse** skal du vælge **Aktivér** for at aktivere karantænemeddelelser (tidligere kaldet meddelelser om uønsket post fra slutbrugere). Klik på **Næste**, når du er færdig.

   > [!NOTE]
   > Som beskrevet tidligere har de indbyggede politikker (AdminOnlyAccessPolicy eller DefaultFullAccessPolicy) ikke aktiveret karantænemeddelelser, og du kan ikke ændre politikkerne.

6. Gennemse dine indstillinger på siden **Gennemse politik** . Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

7. Klik på **Udført** på den bekræftelsesside, der vises.

Nu er du klar til at tildele karantænepolitikken til en karantænefunktion som beskrevet i [afsnittet Trin 2](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>Opret karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at oprette karantænepolitikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge cmdlet'en **New-QuarantinePolicy**.

> [!NOTE]
> Hvis du ikke bruger parameteren _ESNEnabled_ og værdien `$true`, deaktiveres karantænemeddelelser.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Brug parameteren EndUserQuarantinePermissionsValue

Hvis du vil oprette en karantænepolitik ved hjælp af parameteren _EndUserQuarantinePermissionsValue_ , skal du bruge følgende syntaks:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

Parameteren _EndUserQuarantinePermissionsValue_ bruger en decimalværdi, der konverteres fra en binær værdi. Den binære værdi svarer til de tilgængelige tilladelser til slutbrugerens karantæne i en bestemt rækkefølge. For hver tilladelse er værdien 1 lig med True, og værdien 0 er lig med False.

Den påkrævede rækkefølge og de påkrævede værdier for hver enkelt tilladelse er beskrevet i følgende tabel:

|Tilladelse|Decimalværdi|Binær værdi|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlockSender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8|00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|

<sup>\*</sup> Værdien 0 skjuler ikke knappen **Vis meddelelsesoverskrift** i detaljerne for den karantænerede meddelelse (knappen er altid tilgængelig).

<sup>\*\*</sup> Denne indstilling bruges ikke (værdien 0 eller 1 gør ingenting).

<sup>\*\*\*</sup> Angiv ikke begge disse værdier til 1. Angiv den ene til 1 og den anden til 0, eller angiv begge til 0.

For begrænsede adgangstilladelser er de påkrævede værdier:

|Tilladelse|Begrænset adgang|
|---|:--:|
|PermissionToViewHeader|0|
|PermissionToDownload|0|
|PermissionToAllowSender|0|
|PermissionToBlockSender|1|
|PermissionToRequestRelease|1|
|PermissionToRelease|0|
|PermissionToPreview|1|
|PermissionToDelete|1|
|Binær værdi|00011011|
|Decimalværdi, der skal bruges|27|

I dette eksempel oprettes der en ny karantænepolitik med navnet LimitedAccess, hvor karantænemeddelelser er slået til, og som tildeler tilladelserne begrænset adgang som beskrevet i den forrige tabel.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

I forbindelse med brugerdefinerede tilladelser skal du bruge den forrige tabel til at få den binære værdi, der svarer til de ønskede tilladelser. Konvertér den binære værdi til en decimalværdi, og brug decimalværdien for parameteren _EndUserQuarantinePermissionsValue_ . Brug ikke den binære værdi til parameterværdien.

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>Trin 2: Tildel en karantænepolitik til understøttede funktioner

I _understøttede_ beskyttelsesfunktioner, der sætter mails i karantæne, kan du tildele en karantænepolitik til de tilgængelige karantænehandlinger. Funktioner, der sætter meddelelser i karantæne og tilgængeligheden af karantænepolitikker, er beskrevet i følgende tabel:

|Funktion|Understøttes karantænepolitikker?|Standard karantænepolitikker, der bruges|
|---|:---:|---|
|[Politikker mod spam](configure-your-spam-filter-policies.md): <ul><li>**Spam** (_SpamAction_)</li><li>**Spam med høj genkendelsessikkerhed** (_HighConfidenceSpamAction_)</li><li>**Phishing** (_PhishSpamAction_)</li><li>**Phishing med høj genkendelsessikkerhed** (_HighConfidencePhishAction_)</li><li>**Masse** (_BulkSpamAction_)</li></ul>|Ja|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li><li>AdminOnlyAccessPolicy (ingen adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li></ul>|
|Politikker til bekæmpelse af phishing: <ul><li>[Spoof intelligence-beskyttelse](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Repræsentationsbeskyttelse i Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**Hvis meddelelsen registreres som en repræsenteret bruger** (_TargetedUserProtectionAction_)</li><li>**Hvis meddelelsen registreres som et repræsenterede domæne** (_TargetedDomainProtectionAction_)</li><li>**Hvis mailbox intelligence registrerer og repræsenterer en bruger** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Ja|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li><li>Repræsentationsbeskyttelse:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (fuld adgang)</li></ul></li></ul>|
|[Politikker for antimalware](configure-anti-malware-policies.md): Alle registrerede meddelelser er altid sat i karantæne.|Ja|AdminOnlyAccessPolicy (ingen adgang)|
|[beskyttelse Pengeskab vedhæftede filer](safe-attachments.md): <ul><li>Mails med vedhæftede filer, der er sat i karantæne som malware af Pengeskab politikker for vedhæftede filer (_aktivér_ og _handling_)</li><li>Filer, der er sat i karantæne som malware af [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>Ja</li><li>Nej</li></ul>|<ul><li>AdminOnlyAccessPolicy (ingen adgang)</li><li>Nielsen</li></ul>|
|[Regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kendt som transportregler) med handlingen: **Levér meddelelsen til den hostede karantæne** (_karantæne_).|Nej|Nielsen|

<sup>\*</sup> Som [tidligere beskrevet i denne artikel](#full-access-permissions-and-quarantine-notifications) bruger din organisation muligvis NotificationEnabledPolicy i stedet for DefaultFullAccessPolicy. Den eneste forskel mellem disse to karantænepolitikker er, at karantænemeddelelser er slået til i NotificationEnabledPolicy og slået fra i DefaultFullAccessPolicy.

Standard karantænepolitikker, forudindstillede tilladelsesgrupper og tilladelser beskrives i [starten af denne artikel](#quarantine-policies) og [senere i denne artikel](#preset-permissions-groups).

> [!NOTE]
> Hvis du er tilfreds med standardtilladelserne for slutbrugere og karantænemeddelelser, der leveres (eller ikke er angivet) af standardkarantænepolitikkerne, behøver du ikke at foretage dig noget. Hvis du vil tilføje eller fjerne slutbrugerfunktioner (de tilgængelige knapper) for meddelelser i karantæne for brugere eller aktivere karantænemeddelelser og tilføje eller fjerne de samme funktioner i karantænemeddelelser, kan du tildele en anden karantænepolitik til karantænehandlingen.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Tildel karantænepolitikker i understøttede politikker på portalen Microsoft 365 Defender

### <a name="anti-spam-policies"></a>Politikker til bekæmpelse af spam

1. På [Microsoft 365 Defender-portalen](https://security.microsoft.com) skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**.

   Du kan også gå direkte til siden **Ant-spam policies** ved at bruge <https://security.microsoft.com/antispam>.

2. Benyt en af følgende fremgangsmåder på siden **Politikker til bekæmpelse af spam** :
   - Find og vælg en eksisterende **politik for indgående** spam.
   - Opret en ny **politik for indgående** spam.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-vinduet med politikoplysninger skal du gå til afsnittet **Handlinger** og derefter klikke på **Rediger handlinger**.
   - **Opret ny**: I den nye politikguide skal du gå til siden **Handlinger** .

4. På siden **Handlinger** vil alle domme, der har handlingen **Karantænemeddelelse** , også have feltet **Vælg karantænepolitik** , så du kan vælge en tilsvarende karantænepolitik.

   **Bemærk**! Når du opretter en ny politik, angiver en tom værdi for **Vælg karantænepolitik** standardkarantænepolitikken for den pågældende dom. Når du senere redigerer politikken, erstattes de tomme værdier af de faktiske standardkarantatpolitiknavne, som beskrevet i den forrige tabel.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="Valg af karantænepolitik i en politik mod spam" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

Komplette instruktioner til oprettelse og ændring af politikker til bekæmpelse af spam er beskrevet i [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>Politikker mod spam i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i politikker til bekæmpelse af spam, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Noter**:

- Standardværdien for parametrene _PhishSpamAction_ og _HighConfidencePhishAction_ er Karantæne, så du behøver ikke at bruge disse parametre, når du opretter nye politikker for spamfilter i PowerShell. For parametrene _SpamAction_, _HighConfidenceSpamAction_ og _BulkSpamAction_ i nye eller eksisterende politikker til bekæmpelse af spam er karantænepolitikken kun effektiv, hvis værdien er Quarantine.

  Hvis du vil se de vigtige parameterværdier i eksisterende politikker mod spam, skal du køre følgende kommando:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Du kan få oplysninger om standardværdierne for handlingen og de anbefalede handlingsværdier for Standard og Strict under [Politikindstillinger for EOP-antispam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Når du opretter nye politikker mod spam, betyder en dom for spamfiltrering uden en tilsvarende karantænepolitikparameter [standardkarantatpolitikken](#step-2-assign-a-quarantine-policy-to-supported-features) for den pågældende dom.

  Du skal kun erstatte en standard karantænepolitik med en brugerdefineret karantænepolitik, hvis du vil ændre standardegenskaberne for slutbrugere i karantænemeddelelser for den bestemte dom for filtrering af spam.

- En ny politik til bekæmpelse af spam i PowerShell kræver en politik for spamfilter (indstillinger) ved hjælp af cmdlet'en **New-HostedContentFilterPolicy** og en eksklusiv regel for spamfilter (modtagerfiltre) ved hjælp af cmdlet'en **New-HostedContentFilterRule** . Du kan finde instruktioner under [Brug PowerShell til at oprette politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

I dette eksempel oprettes en ny politik for spamfilter med navnet Forskningsafdeling med følgende indstillinger:

- Handlingen for alle spamfiltreringsdomme er indstillet til Karantæne.
- Den brugerdefinerede karantænepolitik med navnet NoAccess, der tildeler **ingen adgangstilladelser** , erstatter alle standard karantænepolitikker, der ikke allerede tildeler **ingen adgangstilladelser** som standard.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

I dette eksempel ændres den eksisterende politik for spamfilter med navnet HR. Handlingen for dom for spamkarantæne er angivet til Karantæne, og den brugerdefinerede karantænepolitik med navnet NoAccess er tildelt.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Politikker for antiphishing

Spoof intelligence er tilgængelig i EOP og Defender for Office 365. Beskyttelse mod repræsentation af brugere, beskyttelse mod repræsentation af domæner og postkasseintelligens er kun tilgængelige i Defender for Office 365. Du kan få flere oplysninger [under Politikker til bekæmpelse af phishing i Microsoft 365](set-up-anti-phishing-policies.md).

1. I [Microsoft 365 Defender-portalen](https://security.microsoft.com) skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker**.

   Du kan også gå direkte til siden **Ant-spam policies** ved at bruge <https://security.microsoft.com/antiphishing>.

2. Benyt en af følgende fremgangsmåder på siden **Anti-phishing** :
   - Find og vælg en eksisterende politik til bekæmpelse af phishing.
   - Opret en ny politik til bekæmpelse af phishing.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-vinduet med politikoplysninger skal du gå til afsnittet **Beskyttelsesindstillinger** og derefter klikke på **Rediger beskyttelsesindstillinger**.
   - **Opret ny**: I den nye politikguide skal du gå til siden **Handlinger** .

4. På siden **Beskyttelsesindstillinger** skal du kontrollere, at følgende indstillinger er slået til og konfigureret efter behov:
   - **Aktiverede brugere til at beskytte**: Angiv brugere.
   - **Aktiverede domæner, der skal beskyttes**: Vælg **Medtag domæner, jeg ejer** og/eller **Medtag brugerdefinerede domæner** , og angiv domænerne.
   - **Aktivér postkasseintelligens**
   - **Aktivér intelligens til repræsentationsbeskyttelse**
   - **Aktivér spoof intelligence**

5. Udfør et af følgende trin:
   - **Rediger eksisterende**: I pop op-vinduet med politikoplysninger skal du gå til afsnittet **Handlinger** og derefter klikke på **Rediger handlinger**.
   - **Opret ny**: I den nye politikguide skal du gå til siden **Handlinger** .

6. På siden **Handlinger** vil alle domme, der har **handlingen Sæt meddelelsen i karantæne** , også have feltet **Anvend karantænepolitik** , så du kan vælge en tilsvarende karantænepolitik.

   **Bemærk**! Når du opretter en ny politik, angiver en tom værdi for **Anvend karantænepolitik** standardkarantænepolitikken for den pågældende handling. Når du senere redigerer politikken, erstattes de tomme værdier af de faktiske standardkarantatpolitiknavne, som beskrevet i den forrige tabel.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="Valg af karantænepolitik i en anti-phishing-politik" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

Du kan finde en komplet vejledning i, hvordan du opretter og ændrer politikker til bekæmpelse af phishing, i følgende emner:

- [Konfigurer politikker for antiphishing i EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>Anti-phishing-politikker i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i politikker til bekæmpelse af phishing, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Noter**:

- _Aktivér\*_ parametre er påkrævet for at aktivere de specifikke beskyttelsesfunktioner. Standardværdien for parametrene _EnableMailboxIntelligence_ og _EnableSpoofIntelligence_ er $true, så du behøver ikke at bruge disse parametre, når du opretter nye anti-phish-politikker i PowerShell. Alle andre _Aktivér\*_ parametre skal have værdien $true, så du kan angive værdien Karantæne i de tilsvarende _\*handlingsparametre_ for derefter at tildele en karantænepolitik. Ingen af parametrene _for *\Action_ har standardværdien Quarantine.

  Hvis du vil se de vigtige parameterværdier i eksisterende anti-phish-politikker, skal du køre følgende kommando:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Du kan få oplysninger om standardværdierne og de anbefalede handlingsværdier for Standard og Strict under [EOP-politikindstillinger for anti-phishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) og [Repræsentationsindstillinger i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- Når du opretter politikker til anti-phishing, betyder en anti-phishing-handling uden en tilsvarende karantænepolitikparameter [standardkarantatpolitikken](#step-2-assign-a-quarantine-policy-to-supported-features) for den pågældende dom.

  Du skal kun erstatte en standard karantænepolitik med en brugerdefineret karantænepolitik, hvis du vil ændre standardegenskaberne for slutbrugere i karantænemeddelelser for den pågældende dom.

- En ny anti-phishing-politik i PowerShell kræver en anti-phish-politik (indstillinger) ved hjælp af cmdlet'en **New-AntiPhishPolicy** og en eksklusiv anti-phish-regel (modtagerfiltre) ved hjælp af cmdlet'en **New-AntiPhishRule** . Du kan finde instruktioner i følgende emner:
  - [Brug PowerShell til at konfigurere anti-phishing-politikker i EOP](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Brug Exchange Online PowerShell til at konfigurere politikker til bekæmpelse af phishing](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

I dette eksempel oprettes en ny anti-phish-politik med navnet Forskningsafdeling med følgende indstillinger:

- Handlingen for alle spamfiltreringsdomme er indstillet til Karantæne.
- Den brugerdefinerede karantænepolitik med navnet NoAccess, der tildeler **ingen adgangstilladelser** , erstatter alle standard karantænepolitikker, der ikke allerede tildeler **ingen adgangstilladelser** som standard.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

I dette eksempel ændres den eksisterende anti-phish-politik med navnet Human Resources. Handlingen for meddelelser, der registreres af bruger repræsentation og domæne repræsentation, er angivet til Karantæne, og den brugerdefinerede karantænepolitik med navnet NoAccess tildeles.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Politikker for antimalware

1. I [Microsoft 365 Defender-portalen](https://security.microsoft.com) skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Antimalware** i afsnittet **Politikker**.

   Du kan også gå direkte til siden **Anti-malware** ved at bruge <https://security.microsoft.com/antimalwarev2>.

2. Benyt en af følgende fremgangsmåder på siden **Antimalware** :
   - Find og vælg en eksisterende politik for antimalware.
   - Opret en ny antimalwarepolitik.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-vinduet med politikoplysninger skal du gå til afsnittet **Beskyttelsesindstillinger** og derefter klikke på **Rediger beskyttelsesindstillinger**.
   - **Opret ny**: I den nye politikguide skal du gå til siden **Handlinger** .

4. På siden **Beskyttelsesindstillinger** skal du vælge en karantænepolitik i feltet **Karantænepolitik** .

   **Bemærk**! Når du opretter en ny politik, angiver en tom værdi for **karantænepolitik** standardkartantaetpolitikken for den, der bruges. Når du senere redigerer politikken, erstattes den tomme værdi af det faktiske standardnavn for karantænepolitikken, som beskrevet i den forrige tabel.

#### <a name="anti-malware-policies-in-powershell"></a>Antimalwarepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i politikker til antimalware, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Noter**:

- Når du opretter nye politikker for antimalware uden at bruge parameteren QuarantineTag, når du opretter en ny politik for antimalware, bruges standard karantænepolitikken for malwareregistreringer (AdminOnlyAccessPolicy).

  Du skal kun erstatte standard karantænepolitikken med en brugerdefineret karantænepolitik, hvis du vil ændre standardegenskaberne for slutbrugere i meddelelser, der er sat i karantæne som malware.

  Hvis du vil se de vigtige parameterværdier i eksisterende anti-phish-politikker, skal du køre følgende kommando:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- En ny antimalwarepolitik i PowerShell kræver en politik for malwarefilter (indstillinger) ved hjælp af cmdlet'en **New-MalwareFilterPolicy** og en eksklusiv regel for malwarefilter (modtagerfiltre) ved hjælp af cmdlet'en **New-MalwareFilterRule** . Du kan finde instruktioner under [Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for antimalware](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

I dette eksempel oprettes der en politik for malwarefilter med navnet Research Department, der bruger den brugerdefinerede karantænepolitik med navnet NoAccess, som tildeler **ingen adgangstilladelser** til de karantænerede meddelelser.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

I dette eksempel ændres den eksisterende politik for malwarefilter med navnet HR ved at tildele den brugerdefinerede karantænepolitik med navnet NoAccess, der tildeler **ingen adgangstilladelser** til de karantænerede meddelelser.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>Pengeskab politikker for vedhæftede filer i Defender for Office 365

1. På [Microsoft 365 Defender-portalen](https://security.microsoft.com) skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Pengeskab Vedhæftede filer** i afsnittet **Politikker**.

   Du kan også gå direkte til siden **Pengeskab Vedhæftede filer** ved at bruge <https://security.microsoft.com/safeattachmentv2>.

2. Benyt en af følgende fremgangsmåder på siden **Pengeskab vedhæftede filer**:
   - Find og vælg en eksisterende politik for Pengeskab Vedhæftede filer.
   - Opret en ny politik for vedhæftede filer Pengeskab.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-vinduet med politikoplysninger skal du gå til afsnittet **Indstillinger** og derefter klikke på **Rediger indstillinger**.
   - **Opret ny**: Gå til siden **Indstillinger** i den nye politikguide.

4. Benyt følgende fremgangsmåde på siden **Indstillinger**:
   1. **Pengeskab Vedhæftede filer ukendt malware-svar**: Vælg **Bloker**, **Erstat** eller **Dynamisk levering**.
   2. Vælg en karantænepolitik i feltet **Karantænepolitik** .

   **Bemærk**! Når du opretter en ny politik, angiver en tom værdi for **karantænepolitikken** , at standardkarantænepolitikken bruges. Når du senere redigerer politikken, erstattes den tomme værdi af det faktiske standardnavn for karantænepolitikken, som beskrevet i den forrige tabel.

Komplette instruktioner til oprettelse og ændring af politikker for vedhæftede filer Pengeskab er beskrevet i [Konfigurer politikker for Pengeskab vedhæftede filer i Microsoft Defender for Office 365](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>Pengeskab politikker for vedhæftede filer i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i Pengeskab politikker for vedhæftede filer, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Noter**:

- _Parameterværdierne_ Bloker, Erstat eller DynamicDelivery kan resultere i karantænemeddelelser (værdien Tillad sætter ikke meddelelser i karantæne). Værdien af _handlingsparameteren_ giver kun mening, når værdien af parameteren _Enable_ er `$true`.

- Når du opretter nye Pengeskab politikker for vedhæftede filer uden at bruge parameteren QuarantineTag, bruges standardkarantænepolitikken for Pengeskab registreringer af vedhæftede filer i mail (AdminOnlyAccessPolicy).

  Du skal kun erstatte standard karantænepolitikken med en brugerdefineret karantænepolitik, hvis du vil ændre standardegenskaberne for slutbrugere i mails, der er sat i karantæne af Pengeskab politikker for vedhæftede filer.

  Kør følgende kommando for at se de vigtige parameterværdier:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- En ny politik for vedhæftede filer Pengeskab i PowerShell kræver en politik for sikker vedhæftede filer (indstillinger) ved hjælp af **Cmdlet'en New-SafeAttachmentPolicy** og en eksklusiv regel for sikre vedhæftede filer (modtagerfiltre) ved hjælp af **New-SafeAttachmentRule-cmdlet'en**. Du kan finde instruktioner under [Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at konfigurere politikker for vedhæftede filer Pengeskab](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

I dette eksempel oprettes der en politik for sikker vedhæftede filer med navnet Research Department, der blokerer registrerede meddelelser og bruger den brugerdefinerede karantænepolitik med navnet NoAccess, der tildeler **ingen adgangstilladelser** til de karantænelagrede meddelelser.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

I dette eksempel ændres den eksisterende politik for sikre vedhæftede filer med navnet HR ved at tildele den brugerdefinerede karantænepolitik med navnet NoAccess, der tildeler **ingen adgangstilladelser** .

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Konfigurer globale indstillinger for karantænebeskeder på Microsoft 365 Defender-portalen

De globale indstillinger for karantænepolitikker giver dig mulighed for at tilpasse de karantænemeddelelser, der sendes til modtagere af karantænemeddelelser, hvis karantænemeddelelser er slået til i karantænepolitikken. Du kan få flere oplysninger om disse meddelelser under [Karantænemeddelelser](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Karantænepolitikker** i afsnittet **Regler**. Du kan også gå direkte til siden **Karantænepolitikker** ved at bruge <https://security.microsoft.com/quarantinePolicies>.

2. På siden **Karantænepolitikker** skal du vælge **Globale indstillinger**.

3. I pop op-vinduet **Indstillinger for karantænemeddelelse** , der åbnes, skal du konfigurere følgende indstillinger:

   - Tilpas karantænemeddelelser baseret på modtagerens sprog:

     - **Vist navn på** den afsender, der bruges i karantænemeddelelser som vist på følgende skærmbillede.

       :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="Et brugerdefineret afsendervisningsnavn i en karantænemeddelelse." lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

     - Teksten **Ansvarsfraskrivelse** , der er føjet til bunden af karantænemeddelelser. Den lokaliserede tekst **, En ansvarsfraskrivelse fra din organisation:** inkluderes altid først efterfulgt af den tekst, du angiver som vist på følgende skærmbillede:

       :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="En brugerdefineret ansvarsfraskrivelse nederst i en karantænemeddelelse." lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

     - Sprog-id'et for værdierne **Vist navn** og **Ansvarsfraskrivelse** . Karantænemeddelelser er allerede lokaliseret på baggrund af modtagerens sprogindstillinger. Værdierne **Vist navn** og **Ansvarsfraskrivelse** bruges i karantænemeddelelser, der gælder for modtagerens sprog.

       Vælg sproget i feltet **Vælg sprog** , _før_ du angiver værdier i felterne **Vist navn** og **Ansvarsfraskrivelse** . Når du ændrer værdien i feltet **Vælg sprog** , tømmes værdierne i felterne **Vist navn** og **Ansvarsfraskrivelse** .

     Følg disse trin for at tilpasse karantænemeddelelser baseret på modtagerens sprog:

     1. Vælg sproget i feltet **Vælg sprog** . Standardværdien er **Default**, hvilket betyder engelsk.
     2. Angiv værdier for **Vist navn** og **Ansvarsfraskrivelse**. Værdierne skal være entydige for hvert sprog. Hvis du forsøger at genbruge værdien **Vist navn** eller **Ansvarsfraskrivelse** for flere sprog, får du vist en fejl, når du klikker på **Gem**.
     3. Klik på knappen **Tilføj** .
     4. Gentag de forrige trin for at oprette maksimalt tre tilpassede karantænemeddelelser baseret på modtagerens sprog. Et felt uden mærkat viser de sprog, du har konfigureret:

        :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="De valgte sprog i de globale indstillinger for karantænebeskeder for karantænepolitikker." lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **Brug mit firmalogo**: Vælg denne indstilling for at erstatte det Microsoft-standardlogo, der bruges øverst i karantænemeddelelser. Før du udfører dette trin, skal du følge vejledningen i [Tilpas det Microsoft 365 tema for din organisation for](../../admin/setup/customize-your-organization-theme.md) at uploade dit brugerdefinerede logo.

     På følgende skærmbillede vises et brugerdefineret logo i en karantænemeddelelse:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="Et brugerdefineret logo i en karantænemeddelelse" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **Send slutbrugerens spammeddelelse hver (dag)**: Vælg hyppigheden for karantænemeddelelser. Standardværdien er 3 dage, men du kan vælge 1 til 15 dage.

4. Klik på **Gem**, når du er færdig.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Få vist karantænepolitikker på Microsoft 365 Defender-portalen

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Karantænepolitikker** i afsnittet **Regler**. Du kan også gå direkte til siden **Karantænepolitikker** ved at bruge <https://security.microsoft.com/quarantinePolicies>.

2. På siden **Karantænepolitikker** vises en liste over politikker efter **navn** og **dato for seneste opdatering** .

3. Hvis du vil have vist indstillingerne for indbyggede eller brugerdefinerede karantænepolitikker, skal du vælge karantænepolitikken på listen ved at klikke på navnet.

4. Klik på **Globale indstillinger** for at få vist de globale indstillinger

### <a name="view-quarantine-policies-in-powershell"></a>Få vist karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at få vist karantænepolitikker, skal du gøre et af følgende trin:

- Kør følgende kommando for at få vist en oversigtsliste over alle indbyggede eller brugerdefinerede politikker:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Hvis du vil have vist indstillingerne for indbyggede eller brugerdefinerede karantænepolitikker, skal du erstatte \<QuarantinePolicyName\> med navnet på karantænepolitikken og køre følgende kommando:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Kør følgende kommando for at få vist de globale indstillinger for karantænemeddelelser:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Rediger karantænepolitikker på Microsoft 365 Defender-portalen

Du kan ikke ændre de indbyggede karantænepolitikker med navnet AdminOnlyAccessPolicy eller DefaultFullAccessPolicy. Du kan ændre den indbyggede politik med navnet NotificationEnabledPolicy ([hvis du har den](#full-access-permissions-and-quarantine-notifications)) og brugerdefinerede karantænepolitikker.

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Karantænepolitikker** i afsnittet **Regler**. Du kan også gå direkte til siden **Karantænepolitikker** ved at bruge <https://security.microsoft.com/quarantinePolicies>.

2. På siden **Karantænepolitikker** skal du vælge politikken ved at klikke på navnet.

3. Når du har valgt politikken, skal du klikke på ikonet ![Rediger politik.](../../media/m365-cc-sc-edit-icon.png) **Rediger politikikon** , der vises.

4. Guiden **Rediger politik**, der åbnes, er stort set identisk med guiden **Ny politik**, som beskrevet i afsnittet [Opret karantænepolitikker i afsnittet Microsoft 365 Defender portal](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) tidligere i denne artikel.

   Den største forskel er: Du kan ikke omdøbe en eksisterende politik.

5. Når du er færdig med at redigere politikken, skal du gå til siden **Oversigt** og klikke på **Send**.

### <a name="modify-quarantine-policies-in-powershell"></a>Rediger karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at ændre en brugerdefineret karantænepolitik, skal du erstatte \<QuarantinePolicyName\> med navnet på karantænepolitikken og bruge følgende syntaks:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

De tilgængelige indstillinger er de samme som beskrevet for oprettelse af karantænepolitikker tidligere i denne artikel.

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Fjern karantænepolitikker på Microsoft 365 Defender-portalen

**Noter**:

- Du kan ikke fjerne de indbyggede karantænepolitikker med navnet AdminOnlyAccessPolicy eller DefaultFullAccessPolicy. Du kan fjerne den indbyggede politik med navnet NotificationEnabledPolicy ([hvis du har den](#full-access-permissions-and-quarantine-notifications)) og brugerdefinerede karantænepolitikker.
- Før du fjerner en karantænepolitik, skal du kontrollere, at den ikke bruges. Kør f.eks. følgende kommando i PowerShell:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Hvis karantænepolitikken bruges, skal du [erstatte den tildelte karantænepolitik](#step-2-assign-a-quarantine-policy-to-supported-features) , før du fjerner den.

1. På Microsoft 365 Defender-portalen skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Karantænepolitikker** i afsnittet **Regler**. Du kan også gå direkte til siden **Karantænepolitikker** ved at bruge <https://security.microsoft.com/quarantinePolicies>.

2. På siden **Karantænepolitikker** skal du vælge den brugerdefinerede karantænepolitik, du vil fjerne, ved at klikke på navnet.

3. Når du har valgt politikken, skal du klikke på ikonet ![Slet politik.](../../media/m365-cc-sc-delete-icon.png) **Ikonet Slet politik** , der vises.

4. Klik på **Fjern politik** i den bekræftelsesdialogboks, der vises.

### <a name="remove-quarantine-policies-in-powershell"></a>Fjern karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at fjerne en brugerdefineret karantænepolitik, skal du erstatte \<QuarantinePolicyName\> med navnet på karantænepolitikken og køre følgende kommando:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Systembeskeder for anmodninger om karantænefrigivelse

Standardbeskedpolitikken med navnet **Bruger anmodede som standard om at frigive en karantænemeddelelse** og genererer automatisk en informationsbesked og sender meddelelsesmeddelelser til medlemmer af følgende rollegrupper, når en bruger anmoder om frigivelse af en karantænemeddelelse:

- Karantæneadministrator
- Sikkerhedsadministrator
- Organisationsadministration (global administrator)

Administratorer kan tilpasse modtagerne af mailmeddelelser eller oprette en brugerdefineret beskedpolitik for at få flere indstillinger.

Du kan få flere oplysninger om politikker for beskeder [under Beskedpolitikker i Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Oplysninger om tilladelse til karantænepolitik

I følgende afsnit beskrives effekten af forudindstillede tilladelsesgrupper og individuelle tilladelser i detaljerne om karantænemeddelelser og i karantænemeddelelser.

### <a name="preset-permissions-groups"></a>Forudindstillede tilladelsesgrupper

De individuelle tilladelser, der er inkluderet i forudindstillede tilladelsesgrupper, vises i tabellen i starten af denne artikel.

#### <a name="no-access"></a>Ingen adgang

Hvis karantænepolitikken tildeler tilladelserne **Ingen adgang** (kun administratoradgang), kan brugerne ikke se de meddelelser, der er sat i karantæne:

- **Oplysninger om karantænemeddelelser**: Der vises ingen meddelelser i slutbrugervisningen.
- **Karantænemeddelelser**: Der sendes ingen meddelelser for disse meddelelser.

#### <a name="limited-access"></a>Begrænset adgang

Hvis karantænepolitikken tildeler tilladelserne **Begrænset adgang** , får brugerne følgende funktioner:

- **Oplysninger om karantænemeddelelse**: Følgende knapper er tilgængelige:
  - **Anmodning om udgivelse**
  - **Vis brevhoveder**
  - **Vis meddelelse**
  - **Fjern fra karantæne**
  - **Afsender af blok**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="De tilgængelige knapper i den karantænede meddelelse indeholder oplysninger, hvis karantænepolitikken giver brugeren begrænsede adgangstilladelser" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **Karantænemeddelelser**: Følgende knapper er tilgængelige:
  - **Afsender af blok**
  - **Anmodning om udgivelse**
  - **Vurder**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="De tilgængelige knapper i karantænemeddelelsen, hvis karantænepolitikken giver brugeren begrænsede adgangstilladelser" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>Fuld adgang

Hvis karantænepolitikken tildeler tilladelserne **Fuld adgang** (alle tilgængelige tilladelser), får brugerne følgende funktioner:

- **Oplysninger om karantænemeddelelse**: Følgende knapper er tilgængelige:
  - **Frigiv meddelelse**
  - **Vis brevhoveder**
  - **Vis meddelelse**
  - **Fjern fra karantæne**
  - **Afsender af blok**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="De tilgængelige knapper i den karantænede meddelelse indeholder oplysninger om, om karantænepolitikken giver brugeren fuld adgangstilladelser" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **Karantænemeddelelser**: Følgende knapper er tilgængelige:
  - **Afsender af blok**
  - **Udgivelse**
  - **Vurder**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="De tilgængelige knapper i karantænemeddelelsen, hvis karantænepolitikken giver brugeren fuld adgangstilladelser" lightbox="../../media/quarantine-tags-esn-full-access.png":::

### <a name="individual-permissions"></a>Individuelle tilladelser

#### <a name="block-sender-permission"></a>Bloker afsendertilladelse

Tilladelsen **Block sender** (_PermissionToBlockSender_) styrer adgangen til den knap, der gør det nemt for brugerne at føje afsender af meddelelser i karantæne til deres liste over blokerede afsendere.

- **Oplysninger om karantænemeddelelse**:
  - **Tilladelsen Bloker afsender** er aktiveret: Knappen **Bloker afsender** er tilgængelig.
  - **Tilladelsen Bloker afsender** er deaktiveret: Knappen **Bloker afsender** er ikke tilgængelig.

- **Karantænemeddelelser**:
  - **Tilladelsen Bloker afsender** er aktiveret: Knappen **Bloker afsender** er tilgængelig.
  - **Tilladelsen Bloker afsender** er deaktiveret: Knappen **Bloker afsender** er ikke tilgængelig.

Du kan finde flere oplysninger om listen over blokerede afsendere under [Bloker meddelelser fra en person](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) og [Brug Exchange Online PowerShell til at konfigurere samlingen af sikre lister i en postkasse](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>Slet tilladelse

Tilladelsen **Delete** (_PermissionToDelete_) styrer brugernes mulighed for at slette deres meddelelser (meddelelser, hvor brugeren er modtager) fra karantæne.

- **Oplysninger om karantænemeddelelse**:
  - **Tilladelsen Slet** er aktiveret: Knappen **Fjern fra karantæne** er tilgængelig.
  - **Slet** tilladelse er deaktiveret: Knappen **Fjern fra karantæne** er ikke tilgængelig.

- **Karantænemeddelelser**: Ingen effekt.

#### <a name="preview-permission"></a>Tilladelse til eksempelvisning

Tilladelsen **Eksempel** (_PermissionToPreview_) styrer brugernes mulighed for at få vist deres meddelelser i karantæne.

- **Oplysninger om karantænemeddelelse**:
  - **Tilladelse til forhåndsvisning** er aktiveret: Knappen **Vis meddelelse** er tilgængelig.
  - **Tilladelse til eksempelvisning** er deaktiveret: Knappen **Vis meddelelse** er ikke tilgængelig.

- **Karantænemeddelelser**: Ingen effekt.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Tillad, at modtagere frigiver en meddelelse fra karantænetilladelsen

**Tillad, at modtagerne frigiver en meddelelse fra karantænetilladelsen** (_PermissionToRelease_) styrer brugernes mulighed for at frigive deres karantænemeddelelser direkte og uden godkendelse fra en administrator.

- **Oplysninger om karantænemeddelelse**:
  - Tilladelse er aktiveret: Knappen **Udgivelsesmeddelelse** er tilgængelig.
  - Tilladelse er deaktiveret: Knappen **Udgivelsesmeddelelse** er ikke tilgængelig.

- **Karantænemeddelelser**:
  - Tilladelse er aktiveret: Knappen **Udgivelse** er tilgængelig.
  - Tilladelse er deaktiveret: Knappen **Udgivelse** er ikke tilgængelig.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Tillad, at modtagere anmoder om, at en meddelelse frigives fra karantænetilladelse

**Tillad, at modtagerne anmoder om en meddelelse, der skal frigives fra karantænetilladelsen** (_PermissionToRequestRelease_), styrer brugernes mulighed for at _anmode om_ frigivelse af deres karantænemeddelelser. Meddelelsen udgives kun, når en administrator har godkendt anmodningen.

- **Oplysninger om karantænemeddelelse**:
  - Tilladelse aktiveret: Knappen **Anmodningsfrigivelse** er tilgængelig.
  - Tilladelse er deaktiveret: Knappen **Anmod om udgivelse** er ikke tilgængelig.

- **Karantænemeddelelser**:
  - Tilladelse aktiveret: Knappen **Anmodningsfrigivelse** er tilgængelig.
  - Tilladelse er deaktiveret: Knappen **Anmod om udgivelse** er ikke tilgængelig.
