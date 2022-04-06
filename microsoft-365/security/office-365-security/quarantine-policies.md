---
title: Karantænepolitikker
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
description: Administratorer kan få mere at vide om, hvordan du kan bruge karantænepolitikker til at styre, hvad brugerne kan gøre for meddelelser, der er sat i karantæne.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5133b98609c29e54361b8fe108e8810858f0d8c8
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467109"
---
# <a name="quarantine-policies"></a>Karantænepolitikker

Karantænepolitikker (tidligere kaldet karantænemærker _) i_ Exchange Online Protection (EOP) og Microsoft Defender for Office 365 giver administratorer mulighed for at styre, hvad brugerne kan gøre for at sætte meddelelser i karantæne, baseret på, hvorfor meddelelsen var i karantæne.

Traditionelt har brugere fået tilladelses- eller afvist niveauer for interaktivitet for meddelelser, der er sat i karantæne, baseret på, hvorfor meddelelsen blev sat i karantæne. Brugere kan f.eks. få vist og frigive meddelelser, der er sat i karantæne af antispamfiltrering som spam eller massemails, men de kan ikke få vist eller slippe meddelelser, der var i karantæne, så meget phishing eller malware er i karantæne.

For [understøttede beskyttelsesfunktioner](#step-2-assign-a-quarantine-policy-to-supported-features) angiver karantænepolitikker, hvad brugerne har tilladelse til at gøre med deres egne meddelelser (meddelelser, hvor de er modtager) i karantæne og i _karantænemeddelelser_. [Karantænemeddelelser](use-spam-notifications-to-release-and-report-quarantined-messages.md) er erstatningen for beskeder om spam til slutbrugeren. Disse meddelelser styres nu af karantænepolitikker og indeholder oplysninger om meddelelser, der er sat i karantæne, for alle understøttede beskyttelsesfunktioner (ikke kun antispampolitik og antiphishingpolitik).

Standardkarantænepolitikker, der gennemtvinger de historiske brugeregenskaber, tildeles automatisk til handlinger i de understøttede beskyttelsesfunktioner, der sætter meddelelser i karantæne. Eller du kan oprette brugerdefinerede karantænepolitikker og tildele dem de understøttede beskyttelsesfunktioner for at tillade eller forhindre brugere i at udføre bestemte handlinger på disse typer af meddelelser, der er sat i karantæne.

De enkelte karantænepolitiktilladelser kombineres til følgende foruddefinerede tilladelsesgrupper:

- Ingen adgang
- Begrænset adgang
- Fuld adgang

De enkelte karantænepolitiktilladelser, der er indeholdt i de foruddefinerede tilladelsesgrupper, er beskrevet i følgende tabel:

|Tilladelse|Ingen adgang|Begrænset adgang|Fuld adgang|
|---|:---:|:---:|:---:|
|**Bloker afsender** (_PermissionToBlockSender_)||![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|**Slet** (_PermissionToDelete_)||![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|**Forhåndsvisning** (_PermissionToPreview_)||![Markering.](../../media/checkmark.png)|![Markering.](../../media/checkmark.png)|
|**Tillad modtagere at frigive en meddelelse fra karantæne** (_PermissionToRelease_)|||![Markering.](../../media/checkmark.png)|
|**Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantæne** (_PermissionToRequestRelease_)||![Markering](../../media/checkmark.png)||

Standardpolitikker for karantæne, deres tilknyttede tilladelsesgrupper, og om karantænemeddelelser er aktiveret, er beskrevet i følgende tabel:

|Standardpolitik for karantæne|Brugt tilladelsesgruppe|Er karantæne for meddelelser aktiveret?|
|---|---|---|
|AdminOnlyAccessPolicy|Ingen adgang|Nej|
|DefaultFullAccessPolicy|Fuld adgang|Nej|
|NotificationEnabledPolicy<sup>\*</sup>|Fuld adgang|Ja|

Hvis du ikke kan lide standardtilladelserne i de foruddefinerede tilladelsesgrupper, eller hvis du vil aktivere meddelelser i karantæne, skal du oprette og bruge brugerdefinerede karantænepolitikker. Du kan finde flere oplysninger om, hvad hver enkelt tilladelse gør, i afsnittet Oplysninger om [tilladelse til karantænepolitik](#quarantine-policy-permission-details) senere i denne artikel.

Du opretter og tildeler karantænepolitikker i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med Exchange Online-postkasser; enkeltstående EOP PowerShell i EOP-organisationer uden Exchange Online postkasser).

> [!NOTE]
> Hvor længe meddelelser, der er sat i karantæne, før de udløber, styres af Behold spam i karantæne **for** dette antal dage (_QuarantineRetentionPeriod_) i antispampolitikker. Få mere at vide under [Konfigurer antispam-politikker i EOP](configure-your-spam-filter-policies.md).
>
> Hvis du ændrer den karantænepolitik, der er tildelt en understøttet beskyttelsesfunktion, påvirker ændringen meddelelser, der er sat i karantæne _, efter du_ har ændringen. Meddelelser, der tidligere var i karantæne af denne beskyttelsesfunktion, påvirkes ikke af indstillingerne for den nye politiktildeling i karantæne.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Meddelelser om fuld adgang og karantæne

<sup>\*</sup> Karantænepolitikken NotificationEnabledPolicy er ikke til stede i alle miljøer. Du har politikken NotificationEnabledPolicy-karantæne, hvis din organisation opfylder begge af følgende krav:

- Din organisation eksisterede, før politikken for karantæne var slået til (sidst i juli/tidligt i august 2021).
- Du havde en [eller flere](configure-your-spam-filter-policies.md) antispampolitikker (standardpolitikken for uønsket post eller brugerdefinerede politikker for uønsket post), hvor indstillingen Aktivér beskeder om **spam** til slutbrugeren var slået til.

Som beskrevet tidligere erstatter karantænemeddelelser i karantænepolitikker beskeder om spam til slutbrugeren, som du har brugt til at slå antispam til eller fra. Den indbyggede karantænepolitik, der hedder DefaultFullAccessPolicy, duplikerede de historiske _tilladelser for meddelelser_,  der er sat i karantæne, men karantænemeddelelser er ikke slået til i karantænepolitikken. Og fordi du ikke kan ændre den indbyggede politik, kan du ikke aktivere karantænemeddelelser i DefaultFullAccessPolicy.

For at give tilladelserne for DefaultFullAccessPolicy, men med meddelelser om karantæne aktiveret, har vi oprettet politikken NotificationEnabledPolicy, der skal bruges i stedet for DefaultFullAccessPolicy for de organisationer, der har brug for det (organisationer, hvor beskeder om spam til slutbrugeren er slået til).

For nye organisationer eller ældre organisationer, der aldrig har haft beskeder om spam til slutbruger aktiveret i antispampolitikker, har du ikke politikken for karantæne ved navn NotificationEnabledPolicy. Du kan slå karantænemeddelelser til ved at oprette og bruge brugerdefinerede karantænepolitikker, hvor meddelelser om karantæne er slået til.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Med karantænepolitikker** , skal du bruge <https://security.microsoft.com/quarantinePolicies>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Hvis du vil have vist, oprette, redigere eller fjerne karantænepolitikker, skal du være medlem af administratorrollerne Organisationsadministration **, Sikkerhedsadministrator** eller **Karantæneadministrator** i Microsoft 365 Defender-portalen.  Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Trin 1: Opret karantænepolitikker i Microsoft 365 Defender portal

1. I portalen [Microsoft 365 Defender skal](https://security.microsoft.com) du gå til **& politikker** \> for samarbejde **& Politikker** \>  \> for trussel mod **trusler i** **afsnittet Regler**.

2. Klik på **Ikonet Tilføj brugerdefineret** politik på ![siden Karantænepolitik.](../../media/m365-cc-sc-create-icon.png) **Tilføj brugerdefineret politik**.

3. Guiden **Ny politik** åbnes. Angiv et **kort,** men entydigt navn i feltet Politiknavn på **siden Politiknavn** . Du skal identificere og vælge karantænepolitikken ud fra navn i kommende trin. Klik på Næste, når du er **færdig**.

4. På siden **Adgang til modtagermeddelelse** skal du vælge en af følgende værdier:
   - **Begrænset adgang**: De individuelle tilladelser, der er inkluderet i denne tilladelsesgruppe, er beskrevet tidligere i denne artikel.
   - **Angiv specifik adgang (Avanceret)**: Brug denne værdi til at angive brugerdefinerede tilladelser. Konfigurer følgende indstillinger, der vises:
     - **Vælg indstilling for udgivelseshandling**: Vælg en af følgende værdier:
       - Tom: Dette er standardværdien.
       - **Tillad modtagere at frigive en meddelelse fra karantæne**
       - **Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantæne**
     - **Vælg yderligere handlinger, som modtagere kan udføre på meddelelser, der er sat** i karantæne: Markér nogle, alle eller ingen af følgende værdier:
       - **Slet**
       - **Eksempel**
       - **Bloker afsender**

   Disse tilladelser og deres virkning på meddelelser, der er sat i karantæne, og i karantænemeddelelser er beskrevet i afsnittet Detaljer om tilladelse til [karantænepolitik senere](#quarantine-policy-permission-details) i denne artikel.

   Klik på Næste, når du er **færdig**.

5. På siden **Besked om spam til slutbruger skal** du vælge **Aktivér** for at aktivere beskeder om karantæne (tidligere kaldet beskeder om spam til slutbrugeren). Klik på Næste, når du er **færdig**.

   > [!NOTE]
   > Som nævnt tidligere har de indbyggede politikker (AdminOnlyAccessPolicy eller DefaultFullAccessPolicy) ikke aktiveret meddelelser, der er sat i karantæne, og du kan ikke ændre politikkerne.

6. Gennemgå **dine indstillinger på** siden Gennemse politik. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Send, når du er **færdig**.

7. Klik på Udført på bekræftelsessiden, der **vises**.

Nu er du klar til at tildele karantænepolitikken til en karantænefunktion, sådan som det er beskrevet i [trin 2-sektionen](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>Opret karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at oprette karantænepolitikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge **New-QuarantinePolicy-cmdlet'en**.

> [!NOTE]
> Hvis du ikke bruger parameteren _ESNEnabled_ `$true`og værdien , deaktiveres beskeder i karantæne.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Brug parameteren EndUserQuarantinePermissionsValue

Hvis du vil oprette en karantænepolitik ved _hjælp af parameteren EndUserQuarantinePermissionsValue_ , skal du bruge følgende syntaks:

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

_Parameteren EndUserQuarantinePermissionsValue_ anvender en decimalværdi, der konverteres fra en binær værdi. Den binære værdi svarer til de tilgængelige tilladelser til slutbrugerkarantæne i en bestemt ordre. For hver tilladelse er værdien 1 lig med Sand, og værdien 0 er lig med Falsk.

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

<sup>\*</sup>Værdien 0 skjuler ikke knappen Vis brevhoved i  oplysningerne om den meddelelse, der er sat i karantæne (knappen er altid tilgængelig).

<sup>\*\*</sup> Denne indstilling bruges ikke (værdien 0 eller 1 gør intet).

<sup>\*\*\*</sup> Angiv ikke begge disse værdier til 1. Indstil én til 1 og den anden til 0, eller indstil begge til 0.

For tilladelser med begrænset adgang er de påkrævede værdier:

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

I dette eksempel oprettes der en ny karantænepolitik kaldet LimitedAccess, hvor karantænemeddelelser er slået til, og som tildeler tilladelserne Begrænset adgang som beskrevet i den forrige tabel.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

For brugerdefinerede tilladelser skal du bruge den forrige tabel til at få den binære værdi, der svarer til de ønskede tilladelser. Konvertér den binære værdi til en decimalværdi, og brug decimalværdien for _parameteren EndUserQuarantinePermissionsValue_ . Brug ikke den binære værdi for parameterværdien.

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>Trin 2: Tildel en karantænepolitik til understøttede funktioner

I _understøttede_ beskyttelsesfunktioner, som sætter mails i karantæne, kan du tildele en karantænepolitik til de tilgængelige karantænehandlinger. Funktioner, der karantænemeddelelser og tilgængeligheden af karantænepolitikker er beskrevet i følgende tabel:

|Funktion|Understøttes karantænepolitikker?|Standardkarantænepolitikker anvendt|
|---|:---:|---|
|[Antispampolitikker](configure-your-spam-filter-policies.md): <ul><li>**Spam** (_SpamAction_)</li><li>**Spam med høj tillid** (_HighConfidenceSpamAction_)</li><li>**Phishing** (_PhishSpamAction_)</li><li>**Phishing med høj tillid** (_HighConfidencePhishAction_)</li><li>**Masse** (_BulkSpamAction_)</li></ul>|Ja|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li><li>AdminOnlyAccessPolicy (Ingen adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li></ul>|
|Antiphishing-politikker: <ul><li>[Spoof intelligence protection](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Repræsentationsbeskyttelse i Defender for Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**Hvis meddelelsen registreres som en efterligning af en bruger** (_TargetedUserProtectionAction_)</li><li>**Hvis meddelelsen registreres som et efterligning af domæne** (_TargetedDomainProtectionAction_)</li><li>**Hvis postkasseintelligens registrerer og efterligner en bruger** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Ja|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li><li>Repræsentationsbeskyttelse:<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (Fuld adgang)</li></ul></li></ul>|
|[Antimalwarepolitikker](configure-anti-malware-policies.md): Alle registrerede meddelelser er altid i karantæne.|Ja|AdminOnlyAccessPolicy (Ingen adgang)|
|[Pengeskab beskyttelse af vedhæftede filer](safe-attachments.md): <ul><li>Mails med vedhæftede filer, der er sat i karantæne som malware Pengeskab politikker for vedhæftede filer (_Aktivér_ og _handling_)</li><li>Filer, der er sat i karantæne [som malware, Pengeskab vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>Ja</li><li>Nej</li></ul>|<ul><li>AdminOnlyAccessPolicy (Ingen adgang)</li><li>i/t</li></ul>|
|[Regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) med handlingen: **Levere meddelelsen til den tilknyttede karantæne** (_karantæne_).|Nej|i/t|

<sup>\*</sup> Som [tidligere beskrevet i denne artikel](#full-access-permissions-and-quarantine-notifications) bruger din organisation muligvis NotificationEnabledPolicy i stedet for DefaultFullAccessPolicy. Den eneste forskel mellem disse to karantænepolitikker er karantænemeddelelser, er slået til i NotificationEnabledPolicy og slået fra i DefaultFullAccessPolicy.

Standardkarantænepolitikker, foruddefinerede tilladelsesgrupper og tilladelser er beskrevet [i starten af denne artikel](#quarantine-policies) [og senere i denne artikel](#preset-permissions-groups).

> [!NOTE]
> Hvis du er tilfreds med standardtilladelserne for slutbrugeren og meddelelser i karantæne, der er angivet (eller ikke er angivet) i standardkarantænepolitikker, behøver du ikke at gøre noget. Hvis du vil tilføje eller fjerne egenskaber for slutbrugeren (de tilgængelige knapper) for meddelelser, der er sat i karantæne af brugere, eller aktivere beskeder i karantæne og tilføje eller fjerne de samme funktioner i karantænemeddelelser, kan du tildele en anden karantænepolitik til karantænehandlingen.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Tildel karantænepolitikker i understøttede politikker i Microsoft 365 Defender-portalen

### <a name="anti-spam-policies"></a>Antispampolitikker

1. I portalen [Microsoft 365 Defender skal](https://security.microsoft.com) du gå til **& politikker** \> for **samarbejde & politikker** \>  \> for trussel mod **spam** i **sektionen** Politikker.

   Eller du kan bruge for at gå **direkte til siden Ant-spam-politikker**<https://security.microsoft.com/antispam>.

2. Gør **et af følgende på** siden Antispam-politikker:
   - Find og vælg en eksisterende **indgående** antispampolitik.
   - Opret en ny **indgående** antispampolitik.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-menuen med politikoplysninger skal du gå **til sektionen** Handlinger og derefter klikke på **Rediger handlinger**.
   - **Opret ny**: I guiden Ny politik skal du gå til **siden** Handlinger.

4. På siden **Handlinger** har hver vurdering, der har meddelelseshandlingen **Karantæne** , også feltet **Vælg** karantænepolitik, hvor du kan vælge en tilsvarende karantænepolitik.

   **Bemærk**! Når du opretter en ny politik, angiver en  tom værdi for Vælg karantænepolitik standardkarantænepolitikken for den pågældende beslutning. Når du senere redigerer politikken, erstattes de tomme værdier af de faktiske standardkarantænepolitiknavne som beskrevet i den forrige tabel.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="Valg for karantænepolitik i en antispampolitik" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

Alle instruktioner til oprettelse og ændring af antispampolitikker er beskrevet i [Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>Antispam-politikker i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i antispampolitikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Bemærkninger**:

- Standardværdien for _parametrene PhishSpamAction_ og _HighConfidencePhishAction_ er Karantæne, så du behøver ikke at bruge disse parametre, når du opretter nye politikker for spamfilter i PowerShell. For _parametrene SpamAction_, _HighConfidenceSpamAction_ og _BulkSpamAction_ i nye eller eksisterende antispampolitikker gælder karantænepolitikken kun, hvis værdien er Karantæne.

  Kør følgende kommando for at få vist vigtige parameterværdier i eksisterende antispampolitikker:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Du kan finde oplysninger om standardhandlingsværdierne og de anbefalede handlingsværdier for Standard og Streng i [Politikindstillinger for EOP-antispam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Når du opretter nye antispampolitikker, betyder det, at spamfiltrering ikke har en tilsvarende karantænepolitikparameter, at der anvendes standardkarantænepolitik [for denne](#step-2-assign-a-quarantine-policy-to-supported-features) konklusion.

  Du skal kun erstatte en standardkarantænepolitik med en brugerdefineret karantænepolitik, hvis du vil ændre standardfunktionerne for slutbrugere på meddelelser, der er sat i karantæne, for den pågældende spamfiltreringsslutning.

- En ny antispampolitik i PowerShell kræver en politik for spamfilter (indstillinger), der bruger **cmdlet'en New-HostedContentFilterPolicy** og en eksklusiv regel for spamfilter (modtagerfiltre) ved hjælp af **new-HostedContentFilterRule-cmdlet'en** . Du kan finde en vejledning [under Brug PowerShell til at oprette antispampolitikker](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

I dette eksempel oprettes en ny politik for spamfilter med navnet Forskningsafdeling med følgende indstillinger:

- Handlingen for alle beskeder om spamfiltrering er indstillet til Karantæne.
- Den brugerdefinerede karantænepolitik, der hedder NoAccess, der tildeler Ingen adgangstilladelser, erstatter eventuelle standardkarantænepolitikker, der ikke allerede tildeler **Ingen** adgangstilladelser som standard.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

I dette eksempel ændres den eksisterende politik for spamfilter med navnet HUMAN Resources. Handlingen for vurdering af spamkarantæne er indstillet til Karantæne, og den brugerdefinerede karantænepolitik, der hedder NoAccess, tildeles.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Antiphishing-politikker

Efterlignet intelligens er tilgængelig i EOP og Defender for Office 365. Bruger efterligningsbeskyttelse, domæneefterligning og postkasseintelligens er kun tilgængelige i Defender for Office 365. Du kan finde flere oplysninger [i Antiphishing-politikker Microsoft 365](set-up-anti-phishing-policies.md).

1. I Microsoft 365 Defender [skal](https://security.microsoft.com) du gå til **& politikker** \> for **samarbejde & regler** \>  \> for trussel **mod phishing** i **sektionen** Politikker.

   Eller du kan bruge for at gå **direkte til siden Ant-spam-politikker**<https://security.microsoft.com/antiphishing>.

2. Gør et **af følgende** på siden Antiphishing:
   - Find og vælg en eksisterende antiphishingpolitik.
   - Opret en ny antiphishingpolitik.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-dialogboksen med politikoplysninger skal du gå **til sektionen Beskyttelsesindstillinger** og derefter klikke **på Rediger beskyttelsesindstillinger**.
   - **Opret ny**: I guiden Ny politik skal du gå til **siden** Handlinger.

4. På siden **Beskyttelsesindstillinger** skal du kontrollere, at følgende indstillinger er aktiveret og konfigureret efter behov:
   - **Aktiverede brugere til at beskytte**: Angiv brugere.
   - **Aktiverede domæner at beskytte**: Vælg **Medtag domæner, jeg ejer** og/eller **Medtag brugerdefinerede domæner** , og angiv domænerne.
   - **Aktivér postkasseintelligens**
   - **Aktivere intelligens til repræsentationsbeskyttelse**
   - **Aktivér efterlignet intelligens**

5. Udfør et af følgende trin:
   - **Rediger eksisterende**: I pop op-menuen med politikoplysninger skal du gå til **sektionen Handlinger** og derefter klikke på **Rediger handlinger**.
   - **Opret ny**: I guiden Ny politik skal du gå til **siden** Handlinger.

6. På siden **Handlinger** har hver vurdering, der har meddelelseshandlingen Karantæne, også feltet Anvend  karantænepolitik, hvor du kan vælge en tilsvarende karantænepolitik.

   **Bemærk**! Når du opretter en ny politik, angiver en  tom værdi for Anvend karantænepolitik standardkarantænepolitikken for den pågældende handling. Når du senere redigerer politikken, erstattes de tomme værdier af de faktiske standardkarantænepolitiknavne som beskrevet i den forrige tabel.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="Valg for karantænepolitik i en antiphishingpolitik" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

Du kan finde komplette instruktioner om oprettelse og ændring af antiphishing-politikker i følgende emner:

- [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md)
- [Konfigurer antiphishing-politikker i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>Antiphishing-politikker i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i antiphishing-politikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Bemærkninger**:

- _Parametrene\*_ Aktivér er nødvendige for at aktivere de specifikke beskyttelsesfunktioner. Standardværdien for _parametrene EnableMailboxIntelligence_ og _EnableSpoofIntelligence_ er $true, så du behøver ikke at bruge disse parametre, når du opretter nye antiphish-politikker i PowerShell. Alle andre _Aktivér-parametre\*_ skal have værdien $true så du kan angive værdien Karantæne _\*_ i de tilsvarende handlingsparametre for derefter at tildele en karantænepolitik. Ingen af _parametrene *\Handling_ har standardværdien Karantæne.

  Kør følgende kommando for at få vist vigtige parameterværdier i eksisterende antiphish-politikker:

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Du kan finde oplysninger om standardhandlingsværdierne og de anbefalede handlingsværdier for Standard og Streng i [Politikindstillinger for EOP-antiphishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) og Indstillinger for repræsentation i [antiphishing-politikker i Microsoft Defender for Office 365](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- Når du opretter antiphishing-politikker, betyder en antiphishing-handling uden en tilsvarende karantænepolitikparameter standardkarantænepolitikken [for denne](#step-2-assign-a-quarantine-policy-to-supported-features) konklusion.

  Du skal kun erstatte en standardkarantænepolitik med en brugerdefineret karantænepolitik, hvis du vil ændre standardfunktionerne for slutbrugere på meddelelser, der er sat i karantæne, for den pågældende beslutning.

- En ny antiphishingpolitik i PowerShell kræver en antiphish-politik (indstillinger) ved hjælp af cmdlet'en **New-AntiPhishPolicy** og en eksklusiv antiphish-regel (modtagerfiltre) ved hjælp af den nye **antiphishRule-cmdlet** . Du kan finde en vejledning i følgende emner:
  - [Brug PowerShell til at konfigurere antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Brug Exchange Online PowerShell til at konfigurere antiphishing-politikker](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

I dette eksempel oprettes en ny antiphish-politik med navnet Forskningsafdeling med følgende indstillinger:

- Handlingen for alle beskeder om spamfiltrering er indstillet til Karantæne.
- Den brugerdefinerede karantænepolitik, der hedder NoAccess, der tildeler Ingen adgangstilladelser, erstatter eventuelle standardkarantænepolitikker, der ikke allerede tildeler **Ingen** adgangstilladelser som standard.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

I dette eksempel ændres den eksisterende antiphish-politik med navnet HUMAN Resources. Handlingen for meddelelser, der registreres af bruger efterligning og domæne efterligning, er angivet til Karantæne, og den brugerdefinerede karantænepolitik NoAccess tildeles.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Antimalwarepolitikker

1. I portalen [Microsoft 365 Defender skal](https://security.microsoft.com) du gå til **& politikker** \> for **samarbejde & regler** \>  \> **for trussel mod malware** i **sektionen** Politikker.

   Eller du kan bruge for at gå **direkte til siden antimalware**<https://security.microsoft.com/antimalwarev2>.

2. Gør **et af følgende** på siden antimalware:
   - Find og vælg en eksisterende antimalwarepolitik.
   - Opret en ny antimalwarepolitik.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-dialogboksen med politikoplysninger skal du gå **til sektionen Beskyttelsesindstillinger** og derefter klikke **på Rediger beskyttelsesindstillinger**.
   - **Opret ny**: I guiden Ny politik skal du gå til **siden** Handlinger.

4. På siden **Beskyttelse skal** du vælge en karantænepolitik i **feltet Karantænepolitik** .

   **Bemærk**! Når du opretter en ny politik, angiver **en tom** politikværdi for Karantæne standardkarantænepolitikken for den, der anvendes. Når du senere redigerer politikken, erstattes den tomme værdi af det faktiske standardpolitiknavn for karantæne, sådan som det er beskrevet i den forrige tabel.

#### <a name="anti-malware-policies-in-powershell"></a>Antimalwarepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i antimalwarepolitikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Bemærkninger**:

- Når du opretter nye antimalwarepolitikker uden at bruge parameteren QuarantineTag, når du opretter en ny antimalwarepolitik, bruges standardpolitikken for malwareregistrering i karantæne (AdminOnlyAccessPolicy).

  Du skal kun erstatte standardkarantænepolitikken med en brugerdefineret karantænepolitik, hvis du vil ændre standardfunktionerne for slutbrugere på meddelelser, der er sat i karantæne som malware.

  Kør følgende kommando for at få vist vigtige parameterværdier i eksisterende antiphish-politikker:

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- En ny antimalwarepolitik i PowerShell kræver en politik for malwarefiltrering (indstillinger), der bruger **cmdlet'en New-MalwareFilterPolicy** og en eksklusiv regel for malwarefiltre (modtagerfiltre), der bruger cmdlet'en **New-MalwareFilterRule** . Du kan finde en [vejledning under Brug Exchange Online PowerShell eller den enkeltstående EOP PowerShell til at konfigurere antimalwarepolitikker](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

I dette eksempel **oprettes en** politik for malwarefilter med navnet Forskningsafdeling, som bruger den brugerdefinerede karantænepolitik NoAccess, der tildeler Ingen adgangstilladelser til meddelelser, der er sat i karantæne.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Dette eksempel ændrer den eksisterende politik for malwarefiltrering med navnet HUMAN Resources ved at tildele politikken for brugerdefinerede karantæner ved navn NoAccess, der tildeler Ingen adgangstilladelser til meddelelser, der er i karantæne.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>Pengeskab politikker for vedhæftede filer i Defender for Office 365

1. I portalen [Microsoft 365 Defender skal](https://security.microsoft.com) du gå til **Politikker for & mailsamarbejde** \> **& politikker** \>  \> for **trussel Pengeskab** Vedhæftede filer i **sektionen** Politikker.

   Du kan også gå direkte til siden **Pengeskab vedhæftede filer** ved hjælp af <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab vedhæftede** filer skal du gøre et af følgende:
   - Find og vælg en eksisterende Pengeskab politik for vedhæftede filer.
   - Opret en ny Pengeskab politik for vedhæftede filer.

3. Udfør et af følgende trin:
   - **Rediger eksisterende**: Vælg politikken ved at klikke på navnet på politikken. I pop op-menuen med politikoplysninger skal du gå **til Indstillinger** og derefter klikke på **Rediger indstillinger**.
   - **Opret ny**: I guiden Ny politik skal du gå til **Indstillinger** side.

4. På **siden Indstillinger** skal du gøre følgende:
   1. **Pengeskab ukendt malwaresvar ved vedhæftede filer**: **Vælg Bloker**, **erstat** eller **Dynamisk levering**.
   2. Vælg en karantænepolitik i **feltet Karantænepolitik** .

   **Bemærk**! Når du opretter en ny politik, angiver **en tom** politikværdi for Karantæne standardkarantænepolitikken. Når du senere redigerer politikken, erstattes den tomme værdi af det faktiske standardpolitiknavn for karantæne, sådan som det er beskrevet i den forrige tabel.

Fulde instruktioner til oprettelse og redigering Pengeskab Politikker for vedhæftede filer er beskrevet i Konfigurer [Pengeskab Politikker](set-up-safe-attachments-policies.md) for vedhæftede filer Microsoft Defender for Office 365.

#### <a name="safe-attachments-policies-in-powershell"></a>Pengeskab politikker for vedhæftede filer i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i Pengeskab Politikker for vedhæftede filer, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Bemærkninger**:

- Værdierne _for_ handlingsparameteren Bloker, Erstat eller DynamicDelivery kan resultere i meddelelser, der er sat i karantæne (værdien Tillad sætter ikke meddelelser i karantæne). Værdien af parameteren _Handling_ giver kun mening, når værdien af _parameteren Aktivér_ er `$true`.

- Når du opretter nye Pengeskab Politikker for vedhæftede filer uden at bruge parameteren QuarantineTag, bruges standardkarantænepolitikken for Pengeskab Registreringer af vedhæftede filer i mail (AdminOnlyAccessPolicy).

  Du skal kun erstatte standardkarantænepolitikken med en brugerdefineret karantænepolitik, hvis du vil ændre standardfunktionerne for slutbrugere på mails, der er sat i karantæne af Pengeskab politikker for vedhæftede filer.

  Kør følgende kommando for at få vist vigtige parameterværdier:

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- En ny Pengeskab Politik for vedhæftede filer i PowerShell kræver en sikker politik for vedhæftede filer (indstillinger), der bruger **New-SafeAttachmentPolicy-cmdlet'en** og en eksklusiv regel for sikre vedhæftede filer (modtagerfiltre) ved hjælp af den **nye SafeAttachmentRule-cmdlet**. Du kan finde en [vejledning under Brug Exchange Online PowerShell eller den enkeltstående EOP PowerShell til at konfigurere Pengeskab politikker for vedhæftede filer](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

I dette eksempel **oprettes en** politik for sikre vedhæftede filer med navnet Forskningsafdeling, som blokerer registrerede meddelelser og bruger den brugerdefinerede karantænepolitik NoAccess, der tildeler Ingen adgangstilladelser til meddelelser, der er i karantæne.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

I dette eksempel ændres den eksisterende politik for sikre vedhæftede filer med navnet HUMAN Resources ved at tildele politikken for brugerdefinerede karantæner ved navn NoAccess, der **tildeler Ingen adgangstilladelser** .

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Konfigurere indstillinger for meddelelser om global karantæne i Microsoft 365 Defender portal

De globale indstillinger for karantænepolitikker giver dig mulighed for at tilpasse de meddelelser i karantæne, der sendes til modtagere af meddelelser, der er sat i karantæne, hvis karantænemeddelelser er slået til i karantænepolitikken. Du kan finde flere oplysninger om disse meddelelser under [Karantænemeddelelser](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for samarbejde **& regler** \>  \> Om trusselspolitikker **Karantænepolitikker** i **sektionen** Regler.

2. På siden **Karantænepolitik** skal du vælge **Globale indstillinger**.

3. I pop **op-vindue med beskedindstillinger** for karantæne, der åbnes, skal du konfigurere nogle af eller alle følgende indstillinger:

   - **Visningsnavn**: Tilpas afsenderens viste navn, der bruges i karantænemeddelelser.

     For hvert sprog, du har tilføjet, skal du vælge sproget i det andet sprogfelt (klik ikke på X) og angive den ønskede tekstværdi i feltet **Vist** navn.

     Følgende skærmbillede viser det tilpassede viste navn i en besked om karantæne:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="Et tilpasset afsendernavn i en besked om karantæne" lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

   - **Ansvarsfraskrivelse**: Føj en brugerdefineret ansvarsfraskrivelse til bunden af meddelelser i karantæne. Den oversatte tekst, **En ansvarsfraskrivelse fra din organisation:** medtages altid først efterfulgt af den tekst, du angiver.

     For hvert sprog, du har tilføjet, skal du vælge sproget i feltet med det andet sprog (klik ikke på X) og angive den ønskede tekstværdi i feltet **Ansvarsfraskrivelse** .

     Følgende skærmbillede viser den tilpassede ansvarsfraskrivelse i en karantænemeddelelse:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="En brugerdefineret ansvarsfraskrivelse nederst i en besked om karantæne" lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

   - **Vælg sprog**: Meddelelser om karantæne lokaliseres allerede baseret på modtagerens sprogindstillinger. Du kan angive brugerdefineret tekst på forskellige sprog for **værdierne Vist navn** og **Ansvarsfraskrivelse** .

     Vælg mindst ét sprog fra det første sprogfelt, og klik derefter på **Tilføj**. Du kan markere flere sprog ved at klikke **på** Tilføj efter hvert sprog. Et sektionssprogfelt viser alle de sprog, du har valgt:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="De valgte sprog i det andet sprogfelt i de globale indstillinger for meddelelser om karantæne i karantænepolitikker" lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **Brug mit firmalogo**: Vælg denne indstilling for at erstatte Microsoft-standardlogoet, der bruges øverst i karantænemeddelelser. Før du gør dette, skal du følge vejledningen i Tilpasse Microsoft 365 [til organisationen for at](../../admin/setup/customize-your-organization-theme.md) overføre dit brugerdefinerede logo.

     Følgende skærmbillede viser et brugerdefineret logo i en besked om karantæne:

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="Et brugerdefineret logo i en besked om karantæne" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **Send beskeder om spam til slutbruger hver (dage)**: Vælg hyppigheden for beskeder i karantæne.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Få vist karantænepolitikker i Microsoft 365 Defender portal

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for samarbejde **& regler** \>  \> Om trusselspolitikker **Karantænepolitikker** i **sektionen** Regler.

2. Siden **for karantænepolitik** viser listen over politikker efter **navn og** **dato for seneste** opdatering.

3. Hvis du vil have vist indstillingerne for indbyggede eller brugerdefinerede karantænepolitikker, skal du vælge karantænepolitikken på listen ved at klikke på navnet.

4. Hvis du vil have vist de globale indstillinger, skal du klikke **på Globale indstillinger**

### <a name="view-quarantine-policies-in-powershell"></a>Få vist karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at få vist karantænepolitikker, skal du gøre et af følgende:

- Hvis du vil have vist en oversigtsliste over alle indbyggede eller brugerdefinerede politikker, skal du køre følgende kommando:

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Hvis du vil have vist indstillingerne for indbyggede eller brugerdefinerede karantænepolitikker, \<QuarantinePolicyName\> skal du erstatte med navnet på karantænepolitikken og køre følgende kommando:

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Kør følgende kommando for at få vist de globale indstillinger for meddelelser i karantæne:

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Rediger karantænepolitikker i Microsoft 365 Defender portal

Du kan ikke ændre de indbyggede karantænepolitikker, der hedder AdminOnlyAccessPolicy eller DefaultFullAccessPolicy. Du kan ændre den indbyggede politik med navnet NotificationEnabledPolicy (hvis [du har det](#full-access-permissions-and-quarantine-notifications)) og brugerdefinerede karantænepolitikker.

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for samarbejde **& regler** \>  \> Om trusselspolitikker **Karantænepolitikker** i **sektionen** Regler.

2. På siden **Karantænepolitikker** skal du vælge politikken ved at klikke på navnet.

3. Når du har valgt politikken, skal du klikke på ![ikonet Rediger politik.](../../media/m365-cc-sc-edit-icon.png) **Ikonet Rediger politik** , der vises.

4. Guiden **Rediger politik,** der åbnes, er næsten identisk med  guiden Ny politik som beskrevet i afsnittet Opret karantænepolitikker [i Microsoft 365 Defender-portalen](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) tidligere i denne artikel.

   Den største forskel er: Du kan ikke omdøbe en eksisterende politik.

5. Når du er færdig med at ændre politikken, skal du gå til **siden Oversigt** og klikke på **Send**.

### <a name="modify-quarantine-policies-in-powershell"></a>Rediger karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at ændre en brugerdefineret karantænepolitik, \<QuarantinePolicyName\> skal du erstatte med navnet på karantænepolitikken og bruge følgende syntaks:

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

De tilgængelige indstillinger er de samme som beskrevet for oprettelse af karantænepolitikker tidligere i denne artikel.

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Fjern karantænepolitikker i Microsoft 365 Defender-portalen

**Bemærkninger**:

- Du kan ikke fjerne de indbyggede karantænepolitikker, der hedder AdminOnlyAccessPolicy eller DefaultFullAccessPolicy. Du kan fjerne den indbyggede politik med navnet NotificationEnabledPolicy (hvis [du har det](#full-access-permissions-and-quarantine-notifications)) og brugerdefinerede karantænepolitikker.
- Før du fjerner en karantænepolitik, skal du kontrollere, at den ikke bruges. Kør f.eks. følgende kommando i PowerShell:

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Hvis karantænepolitikken bruges, skal du erstatte [den tildelte karantænepolitik,](#step-2-assign-a-quarantine-policy-to-supported-features) før du fjerner den.

1. I portalen Microsoft 365 Defender skal du gå til **& politikker** \> for samarbejde **& regler** \>  \> Om trusselspolitikker **Karantænepolitikker** i **sektionen** Regler.

2. På siden **Karantænepolitik** skal du vælge den brugerdefinerede karantænepolitik, du vil fjerne, ved at klikke på navnet.

3. Når du har valgt politikken, skal du klikke på ![ikonet Slet politik.](../../media/m365-cc-sc-delete-icon.png) **Ikonet Slet politik** , der vises.

4. Klik **på Fjern politik** i den bekræftelsesdialogboks, der vises.

### <a name="remove-quarantine-policies-in-powershell"></a>Fjern karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at fjerne en brugerdefineret karantænepolitik, \<QuarantinePolicyName\> skal du erstatte med navnet på karantænepolitikken og køre følgende kommando:

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Systembeskeder for udgivelsesanmodninger i karantæne

Som standard genererer standardpolitikken for påmindelsesbeskeder, der hedder Bruger har anmodet om at frigive en meddelelse i karantæne, automatisk en informationsbesked og sender meddelelser til medlemmer af følgende rollegrupper, når en bruger anmoder om frigivelse af en meddelelse i karantæne:

- Karantæneadministrator
- Sikkerhedsadministrator
- Organisationsadministration (global administrator)

Administratorer kan tilpasse modtagerne af mailbeskeder eller oprette en brugerdefineret beskedpolitik for at få flere valgmuligheder.

Du kan finde flere oplysninger om beskedpolitikker [under Påmindelsespolitikker i Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Oplysninger om tilladelse til karantænepolitik

I de følgende afsnit beskrives effekterne af foruddefinerede tilladelsesgrupper og individuelle tilladelser i oplysningerne om meddelelser, der er sat i karantæne, og i meddelelser om karantæne.

### <a name="preset-permissions-groups"></a>Forudindstillede tilladelsesgrupper

De individuelle tilladelser, der er inkluderet i foruddefinerede tilladelsesgrupper, vises i tabellen i starten af denne artikel.

#### <a name="no-access"></a>Ingen adgang

Hvis karantænepolitikken tildeler tilladelsen Ingen **adgang** (kun administratoradgang), kan brugerne ikke se de meddelelser, der er i karantæne:

- **Oplysninger om meddelelser i karantæne**: Der vises ingen meddelelser i slutbrugervisningen.
- **Karantænemeddelelser**: Der sendes ingen meddelelser for disse meddelelser.

#### <a name="limited-access"></a>Begrænset adgang

Hvis karantænepolitikken tildeler **tilladelsen Begrænset** adgang, får brugerne følgende egenskaber:

- **Oplysninger om meddelelser i karantæne**: Følgende knapper er tilgængelige:
  - **Anmod om frigivelse**
  - **Få vist brevhoveder for meddelelser**
  - **Forhåndsvisning af meddelelse**
  - **Fjern fra karantæne**
  - **Bloker afsender**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="De tilgængelige knapper i oplysninger om meddelelser i karantæne, hvis karantænepolitikken giver brugeren begrænsede adgangstilladelser" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **Karantænemeddelelser**: Der er følgende knapper tilgængelige:
  - **Bloker afsender**
  - **Anmod om frigivelse**
  - **Gennemse**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="De tilgængelige knapper i karantænemeddelelsen, hvis karantænepolitikken giver brugeren begrænsede adgangstilladelser" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>Fuld adgang

Hvis karantænepolitikken tildeler **tilladelsen Fuld** adgang (alle tilgængelige tilladelser), får brugerne følgende funktioner:

- **Oplysninger om meddelelser i karantæne**: Følgende knapper er tilgængelige:
  - **Udgivelsesmeddelelse**
  - **Få vist brevhoveder for meddelelser**
  - **Forhåndsvisning af meddelelse**
  - **Fjern fra karantæne**
  - **Bloker afsender**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="De tilgængelige knapper i oplysninger om meddelelser i karantæne, hvis karantænepolitikken giver brugeren fuld adgangstilladelser" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **Karantænemeddelelser**: Der er følgende knapper tilgængelige:
  - **Bloker afsender**
  - **Udgivelse**
  - **Gennemse**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="De tilgængelige knapper i karantænemeddelelsen, hvis karantænepolitikken giver brugeren fuld adgangstilladelser" lightbox="../../media/quarantine-tags-esn-full-access.png":::

### <a name="individual-permissions"></a>Individuelle tilladelser

#### <a name="block-sender-permission"></a>Blokere afsendertilladelse

Tilladelsen **Bloker afsender** (_PermissionToBlockSender_) styrer adgangen til knappen, der giver brugere mulighed for nemt at føje afsenderen, der er sat i karantæne, til deres liste over blokerede afsendere.

- **Oplysninger om meddelelser i karantæne**:
  - **Bloker afsendertilladelse** aktiveret: **Knappen Bloker** afsender er tilgængelig.
  - **Bloker afsendertilladelse** deaktiveret: **Knappen Bloker** afsender er ikke tilgængelig.

- **Karantænemeddelelser**:
  - **Bloker afsendertilladelse** aktiveret: **Knappen Bloker** afsender er tilgængelig.
  - **Bloker afsendertilladelse** deaktiveret: **Knappen Bloker** afsender er ikke tilgængelig.

Du kan finde flere oplysninger om listen over blokerede afsendere i Bloker meddelelser fra en person og [Brug Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox) til at konfigurere indsamlingen af sikre lister i en postkasse.[](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667)

#### <a name="delete-permission"></a>Slet tilladelse

Tilladelsen **Slet** (_PermissionToDelete_) styrer brugernes mulighed for at slette deres meddelelser (meddelelser, hvor brugeren er modtager) fra karantæne.

- **Oplysninger om meddelelser i karantæne**:
  - **Slet** tilladelse er aktiveret: **Knappen Fjern fra** karantæne er tilgængelig.
  - **Slet** tilladelse er deaktiveret: **Knappen Fjern fra karantæne** er ikke tilgængelig.

- **Karantænemeddelelser**: Ingen virkning.

#### <a name="preview-permission"></a>Tilladelse til forhåndsvisning

Tilladelse **til eksempelvisning** (_PermissionToPreview) styrer_ brugernes mulighed for at få vist deres meddelelser i karantæne.

- **Oplysninger om meddelelser i karantæne**:
  - **Tilladelse for** eksempel aktiveret: **Knappen Vis** meddelelse er tilgængelig.
  - **Forhåndsvisningstilladelse** deaktiveret: **Knappen Vis** meddelelse er ikke tilgængelig.

- **Karantænemeddelelser**: Ingen virkning.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Tillad, at modtagerne frigiver en meddelelse fra karantænetilladelsen

Tillad **modtagere at** frigive en meddelelse fra karantænetilladelse (_PermissionToRelease_) styrer brugernes mulighed for at frigive deres meddelelser, der er i karantæne, direkte og uden godkendelse fra en administrator.

- **Oplysninger om meddelelser i karantæne**:
  - Tilladelse aktiveret: **Knappen Udgivelsesmeddelelse** er tilgængelig.
  - Tilladelse deaktiveret: **Knappen Slip meddelelse** er ikke tilgængelig.

- **Karantænemeddelelser**:
  - Tilladelse aktiveret: **Knappen Slip** er tilgængelig.
  - Tilladelse deaktiveret: **Knappen Slip** er ikke tilgængelig.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantænetilladelse

Tillad **modtagere at** anmode om, at en meddelelse frigives fra karantænetilladelse (_PermissionToRequestRelease_) styrer brugernes mulighed for at anmode  om frigivelse af deres meddelelser, der er i karantæne. Meddelelsen frigives først, når en administrator godkender anmodningen.

- **Oplysninger om meddelelser i karantæne**:
  - Tilladelse aktiveret: Knappen **Anmod om** frigivelse er tilgængelig.
  - Tilladelse deaktiveret: Knappen **Anmod om** frigivelse er ikke tilgængelig.

- **Karantænemeddelelser**:
  - Tilladelse aktiveret: Knappen **Anmod om** frigivelse er tilgængelig.
  - Tilladelse deaktiveret: Knappen **Anmod om** frigivelse er ikke tilgængelig.
