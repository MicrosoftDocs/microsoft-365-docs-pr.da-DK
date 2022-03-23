---
title: Karantænepolitikker
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Administratorer kan få mere at vide om, hvordan du kan bruge karantænepolitikker til at styre, hvad brugerne kan gøre ved deres meddelelser, der er i karantæne.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96dc1e2158787457884ca6a3c6f27bf76e83a369
ms.sourcegitcommit: b3c4816b55657b87ed4a5f6a4abe3d505392218e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 08/04/2021
ms.locfileid: "63590464"
---
# <a name="quarantine-policies"></a>Karantænepolitikker

> [!NOTE]
> De funktioner, der er beskrevet i denne artikel, er i forhåndsvisning, er ikke tilgængelige for alle og kan ændres uden forbehold.

Karantænepolitikker (tidligere kaldet karantænemærker) i Exchange Online Protection (EOP) giver administratorer mulighed for at styre, hvad brugerne kan gøre til deres meddelelser, der er i karantæne, baseret på, hvordan meddelelsen er kommet i karantæne.

EOP har traditionelt tilladt eller forhindret visse niveauer af interaktivitet for meddelelser i [karantæne](find-and-release-quarantined-messages-as-a-user.md) og i [beskeder om spam til slutbrugeren](use-spam-notifications-to-release-and-report-quarantined-messages.md). Brugere kan f.eks. få vist og frigive meddelelser, der er sat i karantæne af filtrering af uønsket post som spam eller flere, men de kan ikke få vist eller frigive meddelelser, der er blevet sat i karantæne, så meget phishing er i karantæne (det er kun administratorer, der kan gøre det).

For [understøttede beskyttelsesfunktioner](#step-2-assign-a-quarantine-policy-to-supported-features) angiver karantænepolitikker, hvad brugerne har tilladelse til at gøre i beskeder om spam til slutbrugeren og i deres meddelelser i karantæne (meddelelser, hvor brugeren er modtager). Standardkarantænepolitikker tildeles automatisk til at gennemtvinge de historiske funktioner for brugere i meddelelser, der er sat i karantæne. Eller du kan oprette og tildele brugerdefinerede karantænepolitikker for at tillade eller forhindre slutbrugere i at udføre bestemte handlinger på meddelelser, der er sat i karantæne.

De individuelle tilladelser kombineres til følgende foruddefinerede tilladelsesgrupper:

- Ingen adgang
- Begrænset adgang
- Fuld adgang

De tilgængelige individuelle tilladelser, og hvad der er inkluderet i eller ikke er medtaget i de foruddefinerede tilladelsesgrupper, er beskrevet i følgende tabel:

<br>

****

|Tilladelse|Ingen adgang|Begrænset adgang|Fuld adgang|
|---|:---:|:---:|:---:|
|**Tillad afsender** (_PermissionToAllowSender_)|||![Markering](../../media/checkmark.png)|
|**Bloker afsender** (_PermissionToBlockSender_)||![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|
|**Slet** (_PermissionToDelete_)||![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|
|**Forhåndsvisning** (_PermissionToPreview_)||![Markering](../../media/checkmark.png)|![Markering](../../media/checkmark.png)|
|**Tillad modtagere at frigive en meddelelse fra karantæne** (_PermissionToRelease_)|||![Markering](../../media/checkmark.png)|
|**Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantæne** (_PermissionToRequestRelease_)||![Markering](../../media/checkmark.png)||
|

Hvis du ikke kan lide standardtilladelserne i de foruddefinerede tilladelsesgrupper, kan du bruge brugerdefinerede tilladelser, når du opretter eller ændrer brugerdefinerede karantænepolitikker. Du kan finde flere oplysninger om, hvad hver enkelt tilladelse gør, i afsnittet Oplysninger om [tilladelse til karantænepolitik](#quarantine-policy-permission-details) senere i denne artikel.

Du opretter og tildeler karantænepolitikker i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med Exchange Online-postkasser; enkeltstående EOP PowerShell i EOP-organisationer uden Exchange Online postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. Eller hvis du vil gå direkte til siden **Med karantænepolitikker** , skal du åbne <https://security.microsoft.com/quarantineTags>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Hvis du vil have vist, oprette, ændre eller fjerne karantænepolitikker, skal du være medlem af rollerne Organisationsadministration  eller Sikkerhedsadministrator i Microsoft 365 Defender portalen. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Trin 1: Opret karantænepolitikker i Microsoft 365 Defender portal

1. I portalen Microsoft 365 Defender  skal du gå til **Mail & regler** \> for samarbejde **Om** \>  \> sikkerhedspolitikker og derefter vælge **Karantænepolitikker**.

2. På siden **Karantænepolitik skal** du klikke på Ikonet ![Tilføj brugerdefineret politik **Tilføj**](../../media/m365-cc-sc-create-icon.png) brugerdefineret politik.

3. Guiden **Ny politik** åbnes. Angiv et **kort,** men entydigt navn i feltet Politiknavn på **siden Politiknavn** . Du skal identificere og vælge karantænepolitikken ud fra navn i kommende trin. Klik på Næste, når du er **færdig**.

4. På siden **Adgang til modtagermeddelelse** skal du vælge en af følgende værdier:
   - **Ingen adgang**
   - **Begrænset adgang**
   - **Fuld adgang**

   De individuelle tilladelser, der er inkluderet i disse tilladelsesgrupper, er beskrevet tidligere i denne artikel.

   Hvis du vil angive brugerdefinerede tilladelser, skal **du vælge Angiv specifik adgang (Avanceret)** og konfigurere følgende indstillinger, der vises:

     - **Vælg indstilling for udgivelseshandling**: Vælg en af følgende værdier:
       - **Ingen udgivelseshandling**: Dette er standardværdien.
       - **Tillad modtagere at frigive en meddelelse fra karantæne**
       - **Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantæne**
     - **Vælg yderligere handlinger, som modtagere kan udføre på meddelelser, der er sat** i karantæne: Markér nogle, alle eller ingen af følgende værdier:
       - **Slet**
       - **Eksempel**
       - **Bloker afsender**

   Disse tilladelser og deres virkning på meddelelser, der er sat i karantæne, og i beskeder om spam til slutbrugere er beskrevet i afsnittet Oplysninger om tilladelse til [karantænepolitik senere](#quarantine-policy-permission-details) i denne artikel.

   Klik på Næste, når du er **færdig**.

5. Gennemgå **dine indstillinger på** siden Gennemse politik, der vises. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Send, når du er **færdig**.

6. Klik på Udført på bekræftelsessiden, der **vises**.

Nu er du klar til at tildele karantænepolitikken til en karantænefunktion, sådan som det er beskrevet i [trin 2-sektionen](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>Opret karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at oprette karantænepolitikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge **New-QuarantineTag-cmdlet'en**. Du kan vælge mellem to forskellige metoder:

- Brug _parameteren EndUserQuarantinePermissionsValue_ .
- Brug _parameteren EndUserQuarantinePermissions_ .

Disse metoder er beskrevet i de følgende afsnit.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Brug parameteren EndUserQuarantinePermissionsValue

Hvis du vil oprette en karantænepolitik ved _hjælp af parameteren EndUserQuarantinePermissionsValue_ , skal du bruge følgende syntaks:

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236>
```

_Parameteren EndUserQuarantinePermissionsValue_ anvender en decimalværdi, der konverteres fra en binær værdi. Den binære værdi svarer til de tilgængelige tilladelser til slutbrugerkarantæne i en bestemt ordre. For hver tilladelse er værdien 1 lig med Sand, og værdien 0 er lig med Falsk.

Rækkefølgen og værdierne for hver enkelt tilladelse i foruddefinerede tilladelsesgrupper er beskrevet i følgende tabel:

<br>

****

|Tilladelse|Ingen adgang|Begrænset adgang|Fuld adgang|
|---|:---:|:---:|:---:|
|PermissionToAllowSender|0|0|1|
|PermissionToBlockSender|0|1|1|
|PermissionToDelete|0|1|1|
|PermissionToDownload<sup>\*</sup>|0|0|0|
|PermissionToPreview|0|1|1|
|PermissionToRelease<sup>\*\*</sup>|0|0|1|
|PermissionToRequestRelease<sup>\*\*</sup>|0|1|0|
|PermissionToViewHeader<sup>\*</sup>|0|0|0|
|Binær værdi|00000000|01101010|11101100|
|Decimalværdi, der skal bruges|0|106|236|
|

<sup>\*</sup> Denne værdi er i øjeblikket altid 0. For PermissionToViewHeader skjuler værdien 0 ikke knappen Vis brevhoved i detaljerne  i den meddelelse, der er sat i karantæne (knappen er altid tilgængelig).

<sup>\*\*</sup> Angiv ikke begge disse værdier til 1. Indstil én til 1 og den anden til 0, eller indstil begge til 0.

I dette eksempel oprettes der et nyt navn på en karantænepolitik, NoAccess, der tildeler tilladelserne Ingen adgang som beskrevet i den forrige tabel.

```powershell
New-QuarantineTag -Name NoAccess -EndUserQuarantinePermissionsValue 0
```

For Begrænsede adgangstilladelser skal du bruge værdien 106. Hvis du vil have tilladelsen Fuld adgang, skal du bruge værdien 236.

For brugerdefinerede tilladelser skal du bruge den forrige tabel til at få den binære værdi, der svarer til de ønskede tilladelser. Konvertér den binære værdi til en decimalværdi, og brug decimalværdien for _parameteren EndUserQuarantinePermissionsValue_ .

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-QuarantineTag](/powershell/module/exchange/new-quarantinetag).

#### <a name="use-the-enduserquarantinepermissions-parameter"></a>Brug parameteren EndUserQuarantinePermissions

Hvis du vil oprette en karantænepolitik ved _hjælp af parameteren EndUserQuarantinePermissionsValue_ , skal du gøre følgende:

A. Store et tilladelsesobjekt i karantæne i en variabel ved hjælp af **cmdlet'en New-QuarantinePermissions**.

<p>

B. Brug variablen som _værdien EndUserQuarantinePermissions_ i **kommandoen New-QuarantineTag** .

##### <a name="step-a-store-a-quarantine-permissions-object-in-a-variable"></a>Trin A: Store et tilladelsesobjekt i karantæne i en variabel

Brug følgende syntaks:

```powershell
$<VariableName> = New-QuarantinePermissions [-PermissionToAllowSender <$true | $False>] [-PermissionToBlockSender <$true | $False>] [-PermissionToDelete <$true | $False>] [-PermissionToPreview <$true | $False>] [-PermissionToRelease <$true | $False>] [-PermissionToRequestRelease <$true | $False>]
```

Standardværdien for ubrugte parametre er `$false`, så du behøver kun at bruge de parametre, hvor du vil angive værdien til `$true`.

Følgende eksempler viser, hvordan du opretter tilladelsesobjekter, der svarer til de forudindstillede tilladelsesgrupper:

- **Ingen adgang**:

  ```powershell
  $NoAccess = New-QuarantinePermissions
  ```

- **Begrænset adgang**:

  ```powershell
  $LimitedAccess = New-QuarantinePermissions -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRequestRelease $true
  ```

- **Fuld adgang**:

  ```powershell
  $FullAccess = New-QuarantinePermissions -PermissionToAllowSender $true -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRelease $true
  ```

Hvis du vil se de værdier, du har angivet, skal du køre variabelnavnet som en kommando (f.eks. køre kommandoen `$NoAccess`).

For brugerdefinerede tilladelser skal du ikke angive både _parametrene PermissionToRelease_ og _PermissionToRequestRelease_ til `$true`. Indstil den ene til `$true` , og lad den anden være som `$false`, eller lad begge som `$false`.

Du kan også ændre en eksisterende tilladelsesobjektvariabel, efter du har oprettet, men før du bruger den, ved hjælp af **cmdlet'en Set-QuarantinePermissions** .

Du kan finde detaljerede oplysninger om syntaks [og parameter i New-QuarantinePermissions](/powershell/module/exchange/new-quarantinepermissions) og [Set-QuarantinePermissions](/powershell/module/exchange/set-quarantinepermissions).

##### <a name="step-b-use-the-variable-in-the-new-quarantinetag-command"></a>Trin B: Brug variablen i New-QuarantineTag kommando

Når du har oprettet og gemt tilladelsesobjektet i en variabel, skal du bruge variablen for parameterværdien _EndUserQuarantinePermission_ i følgende **New-QuarantineTag-kommando** :

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissions $<VariableName>
```

I dette eksempel oprettes en ny karantænepolitik med navnet LimitedAccess `$LimitedAccess` ved hjælp af det tilladelsesobjekt, der blev beskrevet og oprettet i forrige trin.

```powershell
New-QuarantineTag -Name LimitedAccess -EndUserQuarantinePermissions $LimitedAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-QuarantineTag](/powershell/module/exchange/new-quarantinetag).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>Trin 2: Tildel en karantænepolitik til understøttede funktioner

I _understøttede_ beskyttelsesfunktioner, der sætter meddelelser eller filer i karantæne (automatisk eller som en konfigurerbar handling), kan du tildele en karantænepolitik til de tilgængelige karantænehandlinger. Funktioner, der karantænemeddelelser og tilgængeligheden af karantænepolitikker er beskrevet i følgende tabel:

<br>

****

|Funktion|Understøttes karantænepolitikker?|Standardkarantænepolitikker anvendt|
|---|:---:|---|
|[Antispampolitikker](configure-your-spam-filter-policies.md): <ul><li>**Spam** (_SpamAction_)</li><li>**Spam med høj tillid** (_HighConfidenceSpamAction_)</li><li>**Phishing** (_PhishSpamAction_)</li><li>**Phishing med høj tillid** (_HighConfidencePhishAction_)</li><li>**Masse** (_BulkSpamAction_)</li></ul>|Ja|<ul><li>DefaultSpamTag (Fuld adgang)</li><li>DefaultHighConfSpamTag (Fuld adgang)</li><li>DefaultPhishTag (Fuld adgang)</li><li>DefaultHighConfPhishTag (Ingen adgang)</li><li>DefaultBulkTag (Fuld adgang)</li></ul>
|Antiphishing-politikker: <ul><li>[Spoof intelligence protection](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Repræsentationsbeskyttelse](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<sup>\*</sup> <ul><li>**Hvis meddelelsen registreres som en efterligning af en bruger** (_TargetedUserProtectionAction_)</li><li>**Hvis meddelelsen registreres som et efterligning af domæne** (_TargetedDomainProtectionAction_)</li><li>**Hvis postkasseintelligens registrerer og efterligner en bruger** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul></ul>|Nej|i/t|
|[Antimalwarepolitikker](configure-anti-malware-policies.md): Alle registrerede meddelelser er altid i karantæne.|Nej|i/t|
|[Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)|Nej|i/t|
|[Regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) med handlingen: **Levere meddelelsen til den tilknyttede karantæne** (_karantæne_).|Nej|i/t|
|

<sup>\*</sup>Indstillinger for repræsentationsbeskyttelse er kun tilgængelige i antiphishing-politikker i Microsoft Defender Office 365.

Hvis du er tilfreds med slutbrugerens tilladelser, der er angivet i standardkarantænepolitikker, behøver du ikke at gøre noget. Hvis du vil tilpasse slutbrugerens funktioner (tilgængelige knapper) i beskeder om spam til slutbrugeren eller i oplysninger om meddelelser, der er sat i karantæne, kan du tildele en brugerdefineret karantænepolitik.

### <a name="assign-quarantine-policies-in-anti-spam-policies-in-the-microsoft-365-defender-portal"></a>Tildel karantænepolitikker i antispampolitikker i Microsoft 365 Defender-portalen

Alle instruktioner til oprettelse og ændring af antispampolitikker er beskrevet i [Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md).

1. I portalen Microsoft 365 Defender skal du gå til & **politikker** \> for **& regler** \> **under** \> **Politikker for uønsket post**. Eller åbn <https://security.microsoft.com/antispam>.

2. Gør **et af følgende på** siden Antispam-politikker:
   - Find og vælg en eksisterende **indgående** antispampolitik.
   - Opret en ny **indgående** antispampolitik.

3. Udfør et af følgende trin:
   - **Rediger eksisterende antispampolitik**: I pop op-menuen med politikoplysninger skal du gå til **sektionen Handlinger** og derefter klikke på **Rediger handlinger**.
   - **Opret ny antispampolitik**: I guiden ny politik skal du gå til **siden** Handlinger.

4. På **siden** Handlinger. Hver konklusion, der har **meddelelseshandlingen** Karantæne, har også **feltet Vælg karantænepolitik** , hvor du kan vælge en tilsvarende karantænepolitik.

   **Bemærk**! Når du opretter en ny politik, angiver en  tom værdi for Vælg karantænepolitik standardkarantænepolitikken for den pågældende beslutning. Når du senere redigerer politikken, erstattes de tomme værdier af de faktiske standardkarantænepolitiknavne som beskrevet i den forrige tabel.

   ![Valg af karantænepolitik i en antispampolitik](../../media/quarantine-tags-in-anti-spam-policies.png)

5. Klik på **Gem**, når du er færdig.

#### <a name="assign-quarantine-policies-in-anti-spam-policies-in-powershell"></a>Tildel karantænepolitikker i antispam-politikker i PowerShell

Hvis du hellere vil bruge PowerShell til at tildele karantænepolitikker i antispampolitikker, skal du oprette forbindelse til Exchange Online PowerShell eller Exchange Online Protection PowerShell og bruge følgende syntaks:

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>">  [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Bemærkninger**:

- Standardværdien for _parameteren HighConfidencePhishAction_ er Karantæne, så du behøver ikke at angive handlingen Karantæne for at aktivere phishing-registreringer med høj tillid i nye antispampolitikker. For alle andre meddelelser om spamfiltrering i nye eller eksisterende antispampolitikker er karantænepolitikken kun effektiv, hvis handlingsværdien er Karantæne. Kør følgende kommando for at få vist handlingsværdierne i eksisterende antispampolitikker:

  ```powershell
  Get-HostedContentFilterPolicy | Format-Table Name,*SpamAction,HighConfidencePhishAction
  ```

  Du kan finde oplysninger om standardhandlingsværdierne og de anbefalede handlingsværdier for Standard og Streng i [Politikindstillinger for EOP-antispam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- En vurdering af spamfiltrering uden en tilsvarende politikparameter i karantæne betyder [,](#step-2-assign-a-quarantine-policy-to-supported-features) at der anvendes standardkarantænepolitik for den pågældende konklusion.

  Du skal kun erstatte en standardkarantænepolitik med en brugerdefineret karantænepolitik, hvis du vil ændre standardfunktionerne for slutbrugere på meddelelser, der er sat i karantæne.

- En ny antispampolitik i PowerShell kræver en politik for spamfilter (indstillinger), der bruger **cmdlet'en New-HostedContentFilterPolicy** og en ny regel for spamfilter (modtagerfiltre) ved hjælp af **cmdlet'en New-HostedContentFilterRule** . Du kan finde en vejledning [under Brug PowerShell til at oprette antispampolitikker](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

I dette eksempel oprettes en ny politik for spamfilter med navnet Forskningsafdeling med følgende indstillinger:

- Handlingen for alle beskeder om spamfiltrering er indstillet til Karantæne.
- Den brugerdefinerede karantænepolitik, der hedder NoAccess, der tildeler Ingen adgangstilladelser, erstatter eventuelle standardkarantænepolitikker, der ikke allerede tildeler **Ingen** adgangstilladelser som standard.

```powershell
New-HostedContentFilterPolicy -Name Research Department -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

I dette eksempel ændres den eksisterende politik for spamfilter med navnet HUMAN Resources. Handlingen for vurdering af spamkarantæne er indstillet til Karantæne, og den brugerdefinerede karantænepolitik, der hedder NoAccess, tildeles.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Konfigurere indstillinger for meddelelser om global karantæne i Microsoft 365 Defender portal

De globale indstillinger for karantænepolitikker giver dig mulighed for at tilpasse de beskeder om spam til slutbrugeren, der sendes til modtagere af meddelelser, der var i karantæne. Du kan finde flere oplysninger om disse meddelelser [under Beskeder om spam til slutbruger.](use-spam-notifications-to-release-and-report-quarantined-messages.md)

1. I portalen Microsoft 365 Defender  skal du gå til **Mail & regler** \> for samarbejde **Om** \>  \> sikkerhedspolitikker og derefter vælge **Karantænepolitikker**.

2. På siden **Karantænepolitik** skal du vælge **Globale indstillinger**.

3. I pop **op-vindue med beskedindstillinger** for karantæne, der åbnes, skal du konfigurere nogle af eller alle følgende indstillinger:

   - **Visningsnavn**: Tilpas afsenderens viste navn, der bruges i beskeder om spam til slutbrugeren.

     For hvert sprog, du har tilføjet, skal du vælge sproget i det andet sprogfelt (klik ikke på X) og angive den ønskede tekstværdi i feltet **Vist** navn.

     Følgende skærmbillede viser det tilpassede viste navn i en besked om spam til slutbrugeren:

     ![Et tilpasset vist navn for afsender i en besked om spam til slutbrugeren](../../media/quarantine-tags-esn-customization-display-name.png)

   - **Ansvarsfraskrivelse**: Føj en brugerdefineret ansvarsfraskrivelse til bunden af beskeder om spam til slutbrugeren. Den oversatte tekst, **En ansvarsfraskrivelse fra din organisation:** medtages altid først efterfulgt af den tekst, du angiver.

     For hvert sprog, du har tilføjet, skal du vælge sproget i feltet med det andet sprog (klik ikke på X) og angive den ønskede tekstværdi i feltet **Ansvarsfraskrivelse** .

     Følgende skærmbillede viser den tilpassede ansvarsfraskrivelse i en beskeder om spam til slutbrugeren:

     ![En brugerdefineret ansvarsfraskrivelse nederst i en besked om spam til slutbrugeren](../../media/quarantine-tags-esn-customization-disclaimer.png)

   - **Vælg sprog**: Beskeder om spam til slutbrugeren er allerede oversatte baseret på modtagerens sprogindstillinger. Du kan angive brugerdefineret tekst på forskellige sprog for **værdierne Vist navn** og **Ansvarsfraskrivelse** .

     Vælg mindst ét sprog fra det første sprogfelt, og klik derefter på **Tilføj**. Du kan markere flere sprog ved at klikke **på** Tilføj efter hvert sprog. Et sektionssprogfelt viser alle de sprog, du har valgt:

     ![Valgte sprog i det andet sprogfelt i de globale indstillinger for meddelelser om karantæne i karantænepolitikker](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **Brug mit firmalogo**: Vælg denne indstilling for at erstatte Microsoft-standardlogoet, der bruges øverst i beskeder om spam til slutbrugere. Før du gør dette, skal du følge vejledningen i Tilpasse Microsoft 365 [til organisationen for at](../../admin/setup/customize-your-organization-theme.md) overføre dit brugerdefinerede logo.

     Følgende skærmbillede viser et brugerdefineret logo i beskeder om spam til slutbrugeren:

     ![Et brugerdefineret logo i beskeder om spam til slutbrugeren](../../media/quarantine-tags-esn-customization-logo.png)

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Få vist karantænepolitikker i Microsoft 365 Defender portal

1. I portalen Microsoft 365 Defender  skal du gå til **Mail & regler** \> for samarbejde **Om** \>  \> sikkerhedspolitikker og derefter vælge **Karantænepolitikker**.

2. Siden **for karantænepolitik** viser listen over politikker efter **navn og** **dato for seneste** opdatering.

3. Hvis du vil have vist indstillingerne for indbyggede eller brugerdefinerede karantænepolitikker, skal du vælge karantænepolitikken på listen ved at klikke på navnet.

4. Hvis du vil have vist de globale indstillinger, skal du klikke **på Globale indstillinger**

### <a name="view-quarantine-policies-in-powershell"></a>Få vist karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at få vist karantænepolitikker, skal du gøre et af følgende:

- Hvis du vil have vist en oversigtsliste over alle indbyggede eller brugerdefinerede politikker, skal du køre følgende kommando:

  ```powershell
  Get-QuarantineTag | Format-Table Name
  ```

- Hvis du vil have vist indstillingerne for indbyggede eller brugerdefinerede karantænepolitikker, \<QuarantinePolicyName\> skal du erstatte med navnet på karantænepolitikken og køre følgende kommando:

  ```powershell
  Get-QuarantineTag -Identity "<QuarantinePolicyName>"
  ```

- Kør følgende kommando for at få vist de globale indstillinger:

  ```powershell
  Get-QuarantineTag -QuarantineTagType GlobalQuarantineTag
  ```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Rediger karantænepolitikker i Microsoft 365 Defender portal

1. I portalen Microsoft 365 Defender  skal du gå til **Mail & regler** \> for samarbejde **Om** \>  \> sikkerhedspolitikker og derefter vælge **Karantænepolitikker**.

2. På siden **Karantænepolitikker** skal du vælge politikken ved at klikke på navnet.

3. Når du har valgt politikken, skal du klikke på ikonet ![Rediger politik ikonet](../../media/m365-cc-sc-edit-icon.png) **Rediger politik** , der vises.

4. Guiden **Rediger politik,** der åbnes, er næsten identisk med  guiden Ny politik som beskrevet i afsnittet Opret karantænepolitikker [i Microsoft 365 Defender-portalen](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) tidligere i denne artikel.

   Den største forskel er: Du kan ikke omdøbe en eksisterende politik.

5. Når du er færdig med at ændre politikken, skal du gå til **siden Oversigt** og klikke på **Send**.

### <a name="modify-quarantine-policies-in-powershell"></a>Rediger karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at ændre en brugerdefineret karantænepolitik, \<QuarantinePolicyName\> skal du erstatte med navnet på karantænepolitikken og bruge følgende syntaks:

```powershell
Set-QuarantineTag -Identity "<QuarantinePolicyName>" [Settings]
```

De tilgængelige indstillinger er de samme som beskrevet for oprettelse af karantænepolitikker tidligere i denne artikel.

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-QuarantineTag](/powershell/module/exchange/set-quarantinetag).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Fjern karantænepolitikker i Microsoft 365 Defender-portalen

**Bemærkninger**:

- Du kan ikke fjerne indbyggede karantænepolitikker.
- Før du fjerner en brugerdefineret karantænepolitik, skal du kontrollere, at den ikke bruges. Kør f.eks. følgende kommando i PowerShell:

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag
  ```

  Hvis karantænepolitikken bruges, skal du erstatte [den tildelte karantænepolitik,](#step-2-assign-a-quarantine-policy-to-supported-features) før du fjerner den.

1. I portalen Microsoft 365 Defender  skal du gå til **Mail & regler** \> for samarbejde **Om** \>  \> sikkerhedspolitikker og derefter vælge **Karantænepolitikker**.

2. På siden **Karantænepolitik** skal du vælge den brugerdefinerede karantænepolitik, du vil fjerne, ved at klikke på navnet.

3. Når du har valgt politikken, skal du klikke på ikonet ![Slet **politikikonet**](../../media/m365-cc-sc-delete-icon.png) Slet politik, der vises.

4. Klik **på Fjern politik** i den bekræftelsesdialogboks, der vises.

### <a name="remove-quarantine-policies-in-powershell"></a>Fjern karantænepolitikker i PowerShell

Hvis du hellere vil bruge PowerShell til at fjerne en brugerdefineret karantænepolitik, \<QuarantinePolicyName\> skal du erstatte med navnet på karantænepolitikken og køre følgende kommando:

```powershell
Remove-QuarantineTag -Identity "<QuarantinePolicyName>"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-QuarantineTag](/powershell/module/exchange/remove-quarantinetag).

## <a name="quarantine-policy-permission-details"></a>Oplysninger om tilladelse til karantænepolitik

I de følgende afsnit beskrives effekterne af foruddefinerede tilladelsesgrupper og individuelle tilladelser i oplysningerne om meddelelser, der er sat i karantæne, og i beskeder om spam til slutbrugeren.

### <a name="preset-permissions-groups"></a>Forudindstillede tilladelsesgrupper

De individuelle tilladelser, der er inkluderet i foruddefinerede tilladelsesgrupper, vises i tabellen i starten af denne artikel.

#### <a name="no-access"></a>Ingen adgang

Hvis karantænepolitikken tildeler ingen **adgangstilladelser** (ingen tilladelser), får brugerne stadig nogle oprindelige funktioner:

- **Oplysninger om meddelelser i karantæne**: Knappen **Vis brevhoved** er altid tilgængelig.

  ![Tilgængelige knapper i oplysningerne om meddelelser i karantæne, hvis karantænepolitikken giver brugeren Ingen adgangstilladelser](../../media/quarantine-tags-quarantined-message-details-no-access.png)

- **Beskeder om spam til slutbruger**: Knappen **Gennemse** , der fører brugeren til meddelelsen i karantæne, er altid tilgængelig.

  ![Tilgængelige knapper i beskeder om spam til slutbrugeren, hvis karantænepolitikken giver brugeren Ingen adgangstilladelser](../../media/quarantine-tags-esn-no-access.png)

#### <a name="limited-access"></a>Begrænset adgang

Hvis karantænepolitikken tildeler **tilladelsen Begrænset** adgang, får brugerne følgende egenskaber:

- **Oplysninger om meddelelser i karantæne**: Følgende knapper er tilgængelige:
  - **Anmod om frigivelse**
  - **Vis brevhoved**
  - **Forhåndsvisning af meddelelse**
  - **Bloker afsender**
  - **Fjern fra karantæne**

  ![Tilgængelige knapper i oplysningerne om meddelelser, der er sat i karantæne, hvis karantænepolitikken giver brugeren tilladelsen Begrænset adgang](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **Beskeder om spam til slutbruger**: Følgende knapper er tilgængelige:
  - **Bloker afsender**
  - **Gennemse**

  ![Tilgængelige knapper i beskeder om spam til slutbrugeren, hvis karantænepolitikken giver brugeren tilladelsen Begrænset adgang](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>Fuld adgang

Hvis karantænepolitikken tildeler **tilladelsen Fuld** adgang (alle tilgængelige tilladelser), får brugerne følgende funktioner:

- **Oplysninger om meddelelser i karantæne**: Følgende knapper er tilgængelige:
  - **Udgivelsesmeddelelse**
  - **Vis brevhoved**
  - **Forhåndsvisning af meddelelse**
  - **Bloker afsender**
  - **Tillad afsender**
  - **Fjern fra karantæne**

  ![Tilgængelige knapper i oplysningerne om meddelelser i karantæne, hvis karantænepolitikken giver brugeren tilladelsen Fuld adgang](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **Beskeder om spam til slutbruger**: Følgende knapper er tilgængelige:
  - **Bloker afsender**
  - **Udgivelse**
  - **Gennemse**

  ![Tilgængelige knapper i beskeder om spam til slutbrugeren, hvis karantænepolitikken giver brugeren tilladelsen Fuld adgang](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>Individuelle tilladelser

> [!NOTE]
> Husk, at brugerne altid får de knapper, der er beskrevet i [sektionen Ingen](#no-access) adgang. Disse knapper er ikke inkluderet i de enkelte tilladelsesbeskrivelser.

#### <a name="allow-sender-permission"></a>Tillad afsendertilladelse

Tilladelsen **Tillad afsender** (_PermissionToAllowSender_) styrer adgangen til knappen, der giver brugerne mulighed for nemt at føje afsenderen, der er i karantæne, til deres Pengeskab afsendere.

- **Oplysninger om meddelelser i karantæne**:
  - **Tillad afsendertilladelse** aktiveret: **Knappen Tillad afsender** er tilgængelig.
  - **Tillad deaktiveret** afsendertilladelse: **Knappen Tillad afsender** er ikke tilgængelig.

- **Beskeder om spam til slutbruger**: Ingen virkning.

Du kan finde flere oplysninger om listen Pengeskab-afsendere i Undgå, at afsendere, der er tillid til, [blokeres](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379666) og Brug Exchange Online PowerShell til at konfigurere indsamlingen af sikre lister [i en postkasse](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="block-sender-permission"></a>Blokere afsendertilladelse

Tilladelsen **Bloker afsender** (_PermissionToBlockSender_) styrer adgangen til knappen, der giver brugere mulighed for nemt at føje afsenderen, der er sat i karantæne, til deres liste over blokerede afsendere.

- **Oplysninger om meddelelser i karantæne**:
  - **Bloker afsendertilladelse** aktiveret: **Knappen Bloker** afsender er tilgængelig.
  - **Bloker afsendertilladelse** deaktiveret: **Knappen Bloker** afsender er ikke tilgængelig.

- **Beskeder om spam til slutbruger:**
  - **Bloker afsendertilladelse** deaktiveret: **Knappen Bloker** afsender er ikke tilgængelig.
  - **Bloker afsendertilladelse** aktiveret: **Knappen Bloker** afsender er tilgængelig.

Du kan finde flere oplysninger om listen over blokerede afsendere i Bloker meddelelser fra en person og [Brug Exchange Online PowerShell](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox) til at konfigurere indsamlingen af sikre lister i en postkasse.[](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667)

#### <a name="delete-permission"></a>Slet tilladelse

Tilladelsen **Slet** (_PermissionToDelete_) styrer brugernes mulighed for at slette deres meddelelser (meddelelser, hvor brugeren er modtager) fra karantæne.

- **Oplysninger om meddelelser i karantæne**:
  - **Slet** tilladelse er aktiveret: **Knappen Fjern fra** karantæne er tilgængelig.
  - **Slet** tilladelse er deaktiveret: **Knappen Fjern fra karantæne** er ikke tilgængelig.

- **Beskeder om spam til slutbruger**: Ingen virkning.

#### <a name="preview-permission"></a>Tilladelse til forhåndsvisning

Tilladelse **til eksempelvisning** (_PermissionToPreview) styrer_ brugernes mulighed for at få vist deres meddelelser i karantæne.

- **Oplysninger om meddelelser i karantæne**:
  - **Tilladelse for** eksempel aktiveret: **Knappen Vis** meddelelse er tilgængelig.
  - **Forhåndsvisningstilladelse** deaktiveret: **Knappen Vis** meddelelse er ikke tilgængelig.

- **Beskeder om spam til slutbruger**: Ingen virkning.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Tillad, at modtagerne frigiver en meddelelse fra karantænetilladelsen

Tillad **modtagere at** frigive en meddelelse fra karantænetilladelse (_PermissionToRelease_) styrer brugernes mulighed for at frigive deres meddelelser, der er i karantæne, direkte og uden godkendelse fra en administrator.

- **Oplysninger om meddelelser i karantæne**:
  - Tilladelse aktiveret: **Knappen Udgivelsesmeddelelse** er tilgængelig.
  - Tilladelse deaktiveret: **Knappen Slip meddelelse** er ikke tilgængelig.

- **Beskeder om spam til slutbruger:**
  - Tilladelse aktiveret: **Knappen Slip** er tilgængelig.
  - Tilladelse deaktiveret: **Knappen Slip** er ikke tilgængelig.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantænetilladelse

Tillad **modtagere at** anmode om, at en meddelelse frigives fra karantænetilladelse (_PermissionToRequestRelease_) styrer brugernes mulighed for at anmode  om frigivelse af deres meddelelser, der er i karantæne. Meddelelsen frigives først, når en administrator godkender anmodningen.

- **Oplysninger om meddelelser i karantæne**:
  - Tilladelse aktiveret: Knappen **Anmod om** frigivelse er tilgængelig.
  - Tilladelse deaktiveret: Knappen **Anmod om** frigivelse er ikke tilgængelig.

- **Beskeder om spam til slutbruger**: **Knappen Udgivelse** er ikke tilgængelig.
