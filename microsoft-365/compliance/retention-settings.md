---
title: Konfigurer opbevaringsindstillinger for automatisk at bevare eller slette indhold
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Forstå de indstillinger, du kan konfigurere i en opbevaringspolitik eller opbevaringsmærkatpolitik for at bevare det, du ønsker, og slippe af med det, du ikke ønsker.
ms.openlocfilehash: 87ecdc932932befc24441a59fb0dd8c023e982c2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639638"
---
# <a name="common-settings-for-retention-policies-and-retention-label-policies"></a>Almindelige indstillinger for opbevaringspolitikker og politikker for opbevaringsmærkater

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](https://aka.ms/ComplianceSD).*

Mange indstillinger for opbevaring er fælles for både opbevaringspolitikker og politikker for opbevaringsmærkater. Brug følgende oplysninger som en hjælp til at konfigurere disse indstillinger til proaktivt at bevare indhold, slette indhold eller begge dele – bevare og derefter slette indholdet.

Du kan se de scenarier, der understøtter disse politikker til opbevaring, under:

- [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).
- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)

Indstillinger, der er specifikke for hvert scenarie, forklares i deres respektive dokumentation.

Du kan finde oversigtsoplysninger om politikker for opbevaring, og hvordan opbevaring fungerer i Microsoft 365, under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

## <a name="scopes---adaptive-and-static"></a>Omfang – adaptive og statiske

Hvis du ikke er fortrolig med tilpassede og statiske områder, og for at hjælpe dig med at vælge, hvilken der skal bruges, når du konfigurerer en politik for opbevaring, skal du se [Tilpassede eller statiske politikområder for opbevaring](retention.md#adaptive-or-static-policy-scopes-for-retention). 

Når du har besluttet, om du vil bruge et adaptivt eller statisk område, kan du bruge følgende oplysninger som en hjælp til at konfigurere det:
- [Konfigurationsoplysninger for tilpassede områder](#configuration-information-for-adaptive-scopes)
- [Konfigurationsoplysninger for statiske områder](#configuration-information-for-static-scopes)

> [!TIP]
> Hvis du har politikker, der bruger statiske områder, og du vil konvertere dem til tilpassede områder, skal du lade dine eksisterende politikker være på plads, mens du opretter nye politikker, der bruger tilpassede områder med de samme opbevaringsindstillinger. Valider, at disse nye politikker er målrettet de korrekte brugere, websteder og grupper, før du deaktiverer eller sletter de gamle politikker med statiske områder.

### <a name="configuration-information-for-adaptive-scopes"></a>Konfigurationsoplysninger for tilpassede områder

Når du vælger at bruge tilpassede områder, bliver du bedt om at vælge, hvilken type tilpasset område du vil have. Der er tre forskellige typer adaptive områder, og hver enkelt understøtter forskellige attributter eller egenskaber:

| Type af tilpasset område | Attributter eller egenskaber, der understøttes, omfatter |
|:-----|:-----|
|**Brugere** – gælder for:  <br/> - Exchange-mail <br/> - OneDrive-konti <br/> - Teams-chats <br/> – Teams-meddelelser om privat kanal <br/> - Yammer-brugermeddelelser| Fornavn <br/> Efternavn    <br/>Vist navn <br/> Stilling <br/> Institut <br/> Office <br/>Adresse    <br/> Byen <br/>Stat eller provins <br/>Postnummer <br/> Land eller område <br/> Mailadresser <br/> Alias <br/> Brugerdefinerede Exchange-attributter: CustomAttribute1 – CustomAttribute15|
|**SharePoint-websteder** – gælder for:  <br/> - SharePoint-websteder <br/> - OneDrive-konti |URL-adresse til websted <br/>Navn på websted <br/> Brugerdefinerede Egenskaber for SharePoint: RefinableString00 – RefinableString99 |
|**Microsoft 365-grupper** – gælder for:  <br/> - Microsoft 365-grupper <br/> - Teams-kanalmeddelelser (standard og delte) <br/> - Yammer-communitymeddelelser |Navn <br/> Vist navn <br/> Beskrivelse <br/> Mailadresser <br/> Alias <br/> Brugerdefinerede Exchange-attributter: CustomAttribute1 – CustomAttribute15 |

Egenskabsnavnene for websteder er baseret på administrerede egenskaber for SharePoint-webstedet. Du kan finde oplysninger om de brugerdefinerede attributter under [Brug af brugerdefinerede egenskaber for SharePoint-websteder til at anvende Microsoft 365-opbevaring med tilpassede politikområder](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

Attributnavnene for brugere og grupper er baseret på [de modtageregenskaber, der kan filtreres](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties), og som knyttes til Azure AD attributter. Eksempel:

- **Alias** knyttes til LDAP-navnet **mailNickname**, der vises som **Mail** i Azure AD Administration.
- **Mailadresser** knyttes til LDAP-navneproxyAdresser, der vises som **proxyadresse** i Azure AD Administration.

De attributter og egenskaber, der er angivet i tabellen, kan nemt angives, når du konfigurerer et adaptivt omfang ved hjælp af den enkle forespørgselsgenerator. Yderligere attributter og egenskaber understøttes med den avancerede forespørgselsgenerator, som beskrevet i følgende afsnit.

> [!TIP]
> Du kan få flere oplysninger om brug af den avancerede forespørgselsgenerator i følgende webinarer: 
> - [Oprettelse af avancerede forespørgsler til brugere og grupper med tilpassede politikområder](https://mipc.eventbuilder.com/event/52683/occurrence/49452/recording?rauth=853.3181650.1f2b6e8b4a05b4441f19b890dfeadcec24c4325e90ac492b7a58eb3045c546ea)
> - [Oprettelse af avancerede forespørgsler til SharePoint-websteder med tilpassede politikområder](https://aka.ms/AdaptivePolicyScopes-AdvancedSharePoint)

En enkelt politik for opbevaring kan have et eller mange tilpassede områder.

#### <a name="to-configure-an-adaptive-scope"></a>Sådan konfigurerer du et adaptivt omfang

Før du konfigurerer dit tilpassede område, skal du bruge det forrige afsnit til at identificere, hvilken type område du skal oprette, og hvilke attributter og værdier du skal bruge. Du skal muligvis samarbejde med andre administratorer om at bekræfte disse oplysninger. 

Specifikt til SharePoint-websteder kan der være behov for yderligere SharePoint-konfiguration, hvis du planlægger at bruge [brugerdefinerede webstedsegenskaber](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/) skal du navigere til en af følgende placeringer:
    
    - Hvis du bruger løsningen til datastyring:
        - **Løsninger** >  **Datastyring** >  Fanen **Tilpassede områder** > + **Opret område**
        
    - Hvis du bruger løsningen til administration af datalivscyklus:
       - **Løsninger** >  Administration af  >  **datalivscyklus** Fanen **Tilpassede områder** > + **Opret område**
    
    Kan du ikke se din løsning i navigationsruden med det samme? Vælg først **Vis alle**. 

2. Følg prompterne i konfigurationen for først at vælge områdetypen, og vælg derefter de attributter eller egenskaber, du vil bruge til at oprette det dynamiske medlemskab, og skriv attributten eller egenskabsværdierne.
    
    Hvis du f.eks. vil konfigurere et adaptivt omfang, der skal bruges til at identificere brugere i Europa, skal du først vælge **Brugere** som områdetype og derefter vælge attributten **Land eller område** og skrive i **Europa**:
    
    ![Eksempel på konfiguration af tilpasset omfang.](../media/example-adaptive-scope.png)
    
    En gang om dagen kører denne forespørgsel mod Azure AD og identificerer alle brugere, der har den værdi **i Europa**, der er angivet for på deres konto for attributten **Land eller område**.
    
    > [!IMPORTANT]
    > Da forespørgslen ikke kører med det samme, er der ingen validering, som du har indtastet korrekt i værdien.
    
    Vælg **Tilføj attribut** (for brugere og grupper) eller **Tilføj egenskab** (for websteder) for at bruge en kombination af attributter eller egenskaber, der understøttes for deres områdetype, sammen med logiske operatorer til at oprette forespørgsler. De understøttede operatorer **er lig med**, **er ikke lig med**, **starter med** og **starter ikke med**, og du kan gruppere de valgte attributter eller egenskaber. Eksempel:
    
    ![Eksempel på konfiguration af tilpasset omfang med grupperinger af attributter.](../media/example-adaptive-scope-grouping.png)
    
    Du kan også vælge **Avanceret forespørgselsgenerator** for at angive dine egne forespørgsler:
    
    - I forbindelse **med bruger**- og **Microsoft 365-gruppeområder** skal du bruge [OPATH-filtreringssyntaks.](/powershell/exchange/recipient-filters) Hvis du f.eks. vil oprette et brugerområde, der definerer medlemskabet efter afdeling, land og stat:
    
        ![Eksempel på tilpasset omfang med avanceret forespørgsel.](../media/example-adaptive-scope-advanced-query.png)
        
        En af fordelene ved at bruge den avancerede forespørgselsgenerator til disse områder er et større udvalg af forespørgselsoperatorer:
        - **Og**
        - **Eller**
        - **Ikke**
        - **eq** (er lig med)
        - **ne** (ikke lig med)
        - **lt** (mindre end)
        - **gt** (større end)
        - **synes godt om** (strengsammenligning)
        - **notlike** (strengsammenligning)
    
    - Brug KQL (Keyword Query Language) for **områder af SharePoint-websteder** . Du kender måske allerede KQL til at søge i SharePoint ved hjælp af indekserede webstedsegenskaber. Du kan få hjælp til at angive disse KQL-forespørgsler under [Reference til nøgleordsforespørgselssprog (KQL).](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)
        
        Da områder for SharePoint-websteder f.eks. automatisk omfatter alle SharePoint-webstedstyper, som omfatter Microsoft 365-gruppetilsluttede websteder og OneDrive-websteder, kan du bruge den indekserede webstedsegenskab **SiteTemplate** til at inkludere eller udelade bestemte webstedstyper. De skabeloner, du kan angive:
        - `SITEPAGEPUBLISHING` til moderne kommunikationswebsteder
        - `GROUP` til Gruppeforbundne Microsoft 365-websteder
        - `TEAMCHANNEL` til websteder for private Microsoft Teams-kanaler
        - `STS` til et klassisk SharePoint-teamwebsted
        - `SPSPERS` for OneDrive-websteder
        
        Så hvis du vil oprette et adaptivt omfang, der kun indeholder moderne kommunikationswebsteder og udelukker Microsoft 365-goup-forbundne websteder og OneDrive-websteder, skal du angive følgende KQL-forespørgsel:
        ````console
        SiteTemplate=SITEPAGEPUBLISHING
        ````
    
    Du kan [validere disse avancerede forespørgsler](#validating-advanced-queries) uafhængigt af områdekonfigurationen.
    
    > [!TIP]
    > Du skal bruge den avancerede forespørgselsgenerator, hvis du vil udelade inaktive postkasser. Eller omvendt skal du kun målrette mod inaktive postkasser. Til denne konfiguration skal du bruge OPATH-egenskaben *IsInactiveMailbox*:
    > 
    > - Hvis du vil udelade inaktive postkasser, skal du sørge for, at forespørgslen indeholder: `(IsInactiveMailbox -eq "False")`
    > - Hvis du kun vil målrette inaktive postkasser, skal du angive: `(IsInactiveMailbox -eq "True")`

3. Opret lige så mange tilpassede områder, som du har brug for. Du kan vælge et eller flere tilpassede områder, når du opretter din politik for opbevaring.

> [!NOTE]
> Det kan tage op til fem dage, før forespørgslerne er udfyldt fuldt ud, og ændringerne vil ikke være øjeblikkelige. Medregn denne forsinkelse ved at vente et par dage, før du føjer et nyligt oprettet område til en politik for opbevaring.

Sådan bekræfter du de aktuelle ændringer af medlemskab og medlemskab for et tilpasset omfang:

1. Dobbeltklik (eller vælg og tryk på Enter) for området på siden **Tilpassede områder**

2. Vælg **Områdeoplysninger** i ruden Detaljer i pop **op-vinduet**. 
    
    Gennemse de oplysninger, der identificerer alle de brugere, websteder eller grupper, der aktuelt er i området, hvis de automatisk blev tilføjet eller fjernet, og datoen og klokkeslættet for medlemskabet ændres.

> [!TIP]
> Brug [politikopslagsindstillingen](retention.md#policy-lookup) til at hjælpe dig med at identificere de politikker, der i øjeblikket er tildelt bestemte brugere, websteder og Microsoft 365-grupper.

#### <a name="validating-advanced-queries"></a>Validering af avancerede forespørgsler

Du kan validere avancerede forespørgsler manuelt ved hjælp af PowerShell og SharePoint-søgning:
- Brug PowerShell til områdetyperne **Brugere** og **Microsoft 365-grupper**
- Brug SharePoint-søgning til områdetypen **SharePoint-websteder**

Sådan kører du en forespørgsel ved hjælp af PowerShell:

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en konto med [de relevante Exchange Online administratortilladelser](/powershell/exchange/find-exchange-cmdlet-permissions#use-powershell-to-find-the-permissions-required-to-run-a-cmdlet).

2. Brug enten [Get-Recipient](/powershell/module/exchange/get-recipient), [Get-Mailbox](/powershell/module/exchange/get-mailbox) eller [Get-User](/powershell/module/exchange/get-user) med parameteren *-Filter* og din [OPATH-forespørgsel](/powershell/exchange/filter-properties) til det tilpassede område, der er omsluttet af krøllede parenteser (`{`,`}`). Hvis dine attributværdier er strenge, skal du omslutte disse værdier i dobbelte eller enkelte anførselstegn.

    Du kan bestemme, om du vil bruge Get-Mailbox, Get-Recipient eller Get-User til validering ved at identificere, hvilken cmdlet der understøttes af den [OPATH-egenskab](/powershell/exchange/filter-properties) , du vælger til din forespørgsel.

    > [!IMPORTANT]
    > Get-Mailbox understøtter ikke *modtagertypen MailUser* , så Get-Recipient eller Get-User skal bruges til at validere forespørgsler, der omfatter postkasser i det lokale miljø i et hybridmiljø.

    Hvis du vil validere et **brugerområde** , skal du bruge den relevante kommando:
    - `Get-Mailbox` with *–RecipientTypeDetails UserMailbox,SharedMailbox,RoomMailbox,EquipmentMailbox*
    - `Get-Recipient` with *–RecipientTypeDetails UserMailbox,MailUser,SharedMailbox,RoomMailbox,EquipmentMailbox*
    
    Hvis du vil validere et **Microsoft 365-gruppeområde** , skal du bruge:
    - `Get-Mailbox` with *-GroupMailbox* eller `Get-Recipient` with *-RecipientTypeDetails GroupMailbox*

    Hvis du f.eks. vil validere et **brugerområde** , kan du bruge:
    
    ````PowerShell
    Get-Recipient -RecipientTypeDetails UserMailbox,MailUser -Filter {Department -eq "Marketing"} -ResultSize Unlimited
    ````
    
    Hvis du vil validere et **Microsoft 365-gruppeområde** , kan du bruge:
    
    ```PowerShell
    Get-Mailbox -RecipientTypeDetails GroupMailbox -Filter {CustomAttribute15 -eq "Marketing"} -ResultSize Unlimited
    ```
    
    > [!TIP]
    > Når du bruger disse kommandoer til at validere et brugerområde, kan det skyldes, at det omfatter brugere, der ikke har en gyldig licens til tilpassede områder, hvis antallet af returnerede modtagere er højere end forventet. Disse brugere vil ikke have anvendt opbevaringsindstillingerne på dem.
    > 
    > I et hybridmiljø kan du f.eks. have synkroniserede brugerkonti uden licens uden en Exchange-postkasse i det lokale miljø eller i Exchange Online. Du kan identificere disse brugere ved at køre følgende kommando: `Get-User -RecipientTypeDetails User`

3. Kontrollér, at outputtet stemmer overens med de forventede brugere eller grupper for dit tilpassede omfang. Hvis den ikke gør det, skal du kontrollere din forespørgsel og værdierne hos den relevante administrator for Azure AD eller Exchange.
 
Sådan kører du en forespørgsel ved hjælp af SharePoint-søgning:

1. Hvis du bruger en global administratorkonto eller en konto, der har SharePoint-administratorrollen, skal du gå til `https://<your_tenant>.sharepoint.com/search`.

2. Brug søgelinjen til at angive din KQL-forespørgsel.

3. Kontrollér, at søgeresultaterne stemmer overens med de forventede URL-adresser for dit tilpassede område. Hvis de ikke gør det, skal du kontrollere din forespørgsel og URL-adresserne med den relevante administrator for SharePoint.

### <a name="configuration-information-for-static-scopes"></a>Konfigurationsoplysninger for statiske områder

Når du vælger at bruge statiske områder, skal du derefter beslutte, om du vil anvende politikken på alle instanser for den valgte placering (hele placeringen), eller om du vil inkludere eller udelade bestemte instanser (bestemte medtagelser eller udeladelser).

#### <a name="a-policy-that-applies-to-entire-locations"></a>En politik, der gælder for hele placeringer

Med undtagelse af Skype for Business er standarden, at alle forekomster for de valgte placeringer automatisk medtages i politikken, uden at du behøver at angive dem som inkluderet.

F.eks. **Alle modtagere** for **Exchange-mailplaceringen** . Med denne standardindstilling medtages alle eksisterende brugerpostkasser i politikken, og alle nye postkasser, der oprettes efter politikkens anvendelse, nedarver automatisk politikken.

#### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>En politik med specifikke medtagelser eller udeladelser

Vær opmærksom på, at hvis du bruger den valgfri konfiguration til at begrænse dine opbevaringsindstillinger til bestemte brugere, bestemte Microsoft 365-grupper eller bestemte websteder, er der nogle grænser pr. politik, du skal være opmærksom på. Du kan få flere oplysninger under [Begrænsninger for opbevaringspolitikker og politikker for opbevaringsmærkater](retention-limits.md). 

Hvis du vil bruge den valgfri konfiguration til at omfatte dine opbevaringsindstillinger, skal du kontrollere **, at Status** for den pågældende placering er **Slået** til, og derefter bruge linkene til at inkludere eller udelade bestemte brugere, Microsoft 365-grupper eller websteder.

> [!WARNING]
> Hvis du konfigurerer instanser til at inkludere og derefter fjerner den sidste, vender konfigurationen tilbage til **Alle** for placeringen.  Sørg for, at det er den konfiguration, du har til hensigt, før du gemmer politikken.
>
> Hvis du f.eks. angiver et SharePoint-websted, der skal medtages i din opbevaringspolitik, som er konfigureret til at slette data, og derefter fjerner det enkelte websted, vil alle SharePoint-websteder som standard være underlagt opbevaringspolitikken, der sletter data permanent. Det samme gælder for Exchange-modtagere, OneDrive-konti, Teams-chatbrugere osv.
>
> I dette scenarie skal du slå placeringen fra, hvis du ikke ønsker, at indstillingen **Alle** for placeringen skal være underlagt opbevaringspolitikken. Du kan også angive de udeladelsesforekomster, der skal være undtaget fra politikken.

## <a name="locations"></a>Steder

Placeringer i politikker for opbevaring identificerer specifikke Microsoft 365-tjenester, der understøtter opbevaringsindstillinger, f.eks. Exchange-mail og SharePoint-websteder. Brug følgende afsnit til de placeringer, der har konfigurationsoplysninger og mulige undtagelser, som du skal være opmærksom på, når du vælger dem til din politik.

### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>Konfigurationsoplysninger for offentlige Exchange-mailmapper og Exchange-mapper

Både **Exchange-mailplaceringen** og placeringen af de **offentlige Exchange-mapper** kræver, at postkasser har mindst 10 MB data, før opbevaringsindstillingerne gælder for dem.

**Exchange-mailplaceringen** understøtter opbevaring af brugernes mail, kalender og andre postkasseelementer ved at anvende opbevaringsindstillinger på niveauet for en postkasse. Delte postkasser og ressourcepostkasser til udstyr og lokaler understøttes også.

Mailkontakter og Microsoft 365-gruppepostkasser understøttes ikke for Exchange-mail. For Microsoft 365-gruppepostkasser skal du i stedet vælge **placeringen Microsoft 365-grupper**. Selvom Exchange-placeringen til at starte med tillader, at en gruppepostkasse vælges til et statisk område, får du vist en fejl om, at "RemoteGroupMailbox" ikke er et gyldigt valg for denne placering, når du forsøger at gemme opbevaringspolitikken.

Afhængigt af din politikkonfiguration kan [inaktive postkasser](inactive-mailboxes-in-office-365.md) være inkluderet eller ej:

- Statiske politikområder omfatter inaktive postkasser, når du bruger standardkonfigurationen **Alle modtagere** , men ikke understøttes for [bestemte medtagelser eller udeladelser](#a-policy-with-specific-inclusions-or-exclusions). Men hvis du medtager eller udelukker en modtager, der har en aktiv postkasse på det tidspunkt, hvor politikken anvendes, og postkassen senere bliver inaktiv, anvendes eller udelades opbevaringsindstillingerne fortsat.

- Tilpassede politikområder omfatter som standard inaktive postkasser, når de opfylder områdets forespørgsel. Du kan udelade dem ved hjælp af den avancerede forespørgselsgenerator og OPATH-egenskaben *IsInactiveMailbox*:
    
    ```console
    (IsInactiveMailbox -eq "False")
    ```

Hvis du bruger et statisk politikområde og vælger modtagere, der skal medtages eller udelades, kan du vælge distributionsgrupper og mailaktiverede sikkerhedsgrupper som en effektiv måde at vælge flere modtagere i stedet for at vælge dem én for én. Når du bruger denne indstilling bag kulisserne, udvides disse grupper automatisk på tidspunktet for konfigurationen for at vælge postkasserne for brugerne i gruppen. Hvis medlemskabet af disse grupper ændres senere, opdateres din eksisterende opbevaringspolitik ikke automatisk i modsætning til tilpassede politikområder.

Du kan finde detaljerede oplysninger om, hvilke postkasseelementer der er inkluderet og udeladt, når du konfigurerer opbevaringsindstillinger for Exchange, under [Hvad er inkluderet i forbindelse med opbevaring og sletning](retention-policies-exchange.md#whats-included-for-retention-and-deletion).

Placeringen af **de offentlige Exchange-mapper** anvender opbevaringsindstillinger for alle offentlige mapper og kan ikke anvendes på mappe- eller postkasseniveau.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Undtagelser for politikker, der er konfigureret automatisk for følsomme oplysningstyper

Når du konfigurerer en politik, der automatisk anvender følsomme oplysningstyper, og vælger **Exchange-mailplaceringen** :

- Microsoft 365-gruppepostkasser er inkluderet.

- Alle postkasser medtages automatisk, også selvom du konfigurerer et adaptivt omfang for at identificere bestemte postkasser. Hvis du har valgt et statisk politikområde, kan du ikke angive modtagere, der skal medtages eller udelades.

### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>Konfigurationsoplysninger for SharePoint-websteder og OneDrive-konti

Når du vælger placeringen af **SharePoint-websteder** , kan politikken for opbevaring bevare og slette dokumenter på SharePoint-kommunikationswebsteder, teamwebsteder, der ikke er forbundet af Microsoft 365-grupper, og klassiske websteder. Medmindre du bruger [tilpassede politikområder](#exceptions-for-adaptive-policy-scopes), understøttes teamwebsteder, der er forbundet af Microsoft 365-grupper, ikke med denne indstilling og i stedet bruge den **Microsoft 365-grupper** placering, der gælder for indhold i gruppens postkasse, websted og filer.

> [!TIP]
> Du kan bruge et [filter i SharePoint Administration](/sharepoint/customize-admin-center-site-list) eller en [SharePoint PowerShell-kommando](/powershell/module/sharepoint-online/get-sposite#example-10) til at bekræfte, om et websted er gruppeforbundet. I forbindelse med statiske områder understøttes disse websteder med **den Microsoft 365-grupper** placering.

Du kan finde detaljerede oplysninger om, hvad der er inkluderet og udeladt, når du konfigurerer opbevaringsindstillinger for SharePoint og OneDrive, under [Hvad er inkluderet til opbevaring og sletning](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion).

Når du angiver dine placeringer for SharePoint-websteder eller OneDrive-konti, behøver du ikke tilladelser for at få adgang til webstederne. I forbindelse med statiske områder udføres der ingen validering på det tidspunkt, hvor du angiver URL-adressen på siden **Rediger placeringer** . De SharePoint-websteder, du angiver, kontrolleres dog, at de findes på den sidste side i konfigurationen. Hvis denne kontrol mislykkes, får du vist en meddelelse om, at valideringen mislykkedes for den ANGIVNE URL-adresse, og opbevaringspolitikken kan ikke oprettes, før valideringskontrollen er bestået. Hvis du får vist denne meddelelse, skal du gå tilbage i konfigurationsprocessen for at ændre URL-adressen eller fjerne webstedet fra opbevaringspolitikken.

Hvis du vil angive individuelle OneDrive-konti, skal du se [Hent en liste over alle OneDrive-URL-adresser for brugere i din organisation](/onedrive/list-onedrive-urls).

> [!NOTE]
> Når du angiver individuelle OneDrive-konti, skal du være opmærksom på, at medmindre [OneDrive-konti er klargjort på forhånd](/onedrive/pre-provision-accounts), oprettes URL-adressen ikke, før en bruger får adgang til deres OneDrive for første gang.
>
> Url-adressen til OneDrive [ændres også automatisk](/onedrive/upn-changes) , hvis der er en ændring i brugerens UPN. F.eks. en begivenhed, der ændrer navn, f.eks. ægteskab eller ændring af domænenavn for at understøtte en organisations omdøbning eller forretningsomstrukturering. Hvis UPN ændres, skal du opdatere de OneDrive-URL-adresser, du angiver for opbevaringsindstillinger.
>
> På grund af udfordringerne ved pålideligt at angive URL-adresser, så individuelle brugere kan inkludere eller udelade for statiske områder, er [tilpassede områder](retention.md#adaptive-or-static-policy-scopes-for-retention) **med** brugeromfangstypen bedre egnet til dette formål.

#### <a name="exceptions-for-adaptive-policy-scopes"></a>Undtagelser for tilpassede politikområder

Når du konfigurerer en politik for opbevaring, der bruger tilpassede politikområder og vælger placeringen af **SharePoint-websteder** :

- OneDrive-websteder og Microsoft 365-gruppetilsluttede websteder er inkluderet ud over SharePoint-kommunikationswebsteder, teamwebsteder, der ikke er forbundet af Microsoft 365-grupper, og klassiske websteder.

### <a name="configuration-information-for-microsoft-365-groups"></a>Konfigurationsoplysninger for Microsoft 365-grupper

Hvis du vil bevare eller slette indhold for en Microsoft 365-gruppe (tidligere Office 365 gruppe), skal du bruge **den Microsoft 365-grupper** placering. For opbevaringspolitikker omfatter denne placering gruppepostkassen og SharePoint-teams-webstedet. Denne placering omfatter kun SharePoint-teams-webstedet for opbevaringsmærkater.

Postkasser, som du målretter med denne politikplacering, kræver mindst 10 MB data, før opbevaringsindstillingerne gælder for dem.

> [!NOTE]
> Selvom en Microsoft 365-gruppe har en Exchange-postkasse, indeholder en opbevaringspolitik for **Exchange-mailplaceringen** ikke indhold i Microsoft 365-gruppepostkasser.

Hvis du bruger statiske områder: Selvom **Exchange-mailplaceringen** for et statisk område til at starte med giver dig mulighed for at angive en gruppepostkasse, der skal medtages eller udelades, får du vist en fejl om, at "RemoteGroupMailbox" ikke er et gyldigt valg for Exchange-placeringen, når du forsøger at gemme opbevaringspolitikken.

En opbevaringspolitik, der anvendes på en Microsoft 365-gruppe, omfatter som standard gruppepostkassen og SharePoint-teams-webstedet. Filer, der er gemt på SharePoint-teams-webstedet, er dækket med denne placering, men ikke Teams-chats eller Teams-kanalmeddelelser, der har deres egne placeringer for opbevaringspolitik.

Hvis du vil ændre standarden, fordi opbevaringspolitikken skal gælde for enten Microsoft 365-postkasser eller blot de forbundne SharePoint-teamswebsteder, skal du bruge [PowerShell-cmdlet'en Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) og parameteren *Applications* med en af følgende værdier:

- `Group:Exchange` kun for Microsoft 365-postkasser, der er forbundet til gruppen.
- `Group:SharePoint` kun for SharePoint-websteder, der er forbundet til gruppen.

Hvis du vil vende tilbage til standardværdien for både postkassen og SharePoint-webstedet for de valgte Microsoft 365-grupper, skal du angive `Group:Exchange,SharePoint`.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Undtagelser for politikker, der er konfigureret automatisk for følsomme oplysningstyper

Når du konfigurerer en politik, der automatisk anvender følsomme oplysningstyper, og vælger **den Microsoft 365-grupper** placering:

- Microsoft 365-gruppepostkasser er ikke inkluderet. Hvis du vil medtage disse postkasser i din politik, skal du i stedet vælge **Exchange-mailplaceringen** .

#### <a name="what-happens-if-a-microsoft-365-group-is-deleted-after-a-policy-is-applied"></a>Hvad sker der, hvis en Microsoft 365-gruppe slettes, når en politik er anvendt

Når der anvendes en politik for opbevaring (statisk politikomfang eller adaptiv) på en Microsoft 365-gruppe, og den pågældende gruppe slettes derefter fra Azure Active Directory:

- Det gruppetilsluttede SharePoint-websted bevares og administreres fortsat af opbevaringspolitikken med **den Microsoft 365-grupper** placering. Webstedet er stadig tilgængeligt for de personer, der havde adgang til det, før gruppen blev slettet, og eventuelle nye tilladelser skal nu administreres via SharePoint.
    
    På nuværende tidspunkt kan du ikke udelade webstedet fra den Microsoft 365-grupper placering, fordi du ikke kan angive den slettede gruppe. Hvis du har brug for at frigive opbevaringspolitikken fra dette websted, skal du kontakte Microsoft Support. Åbn f.eks. [en supportanmodning i Microsoft 365 Administration Center](/microsoft-365/admin/get-help-support#online-support).

- Postkassen for den slettede gruppe bliver inaktiv, og ligesom SharePoint-webstedet er den stadig underlagt opbevaringsindstillinger. Du kan få flere oplysninger under [Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md).

### <a name="configuration-information-for-skype-for-business"></a>Konfigurationsoplysninger for Skype for Business

> [!NOTE]
> Skype for Business blev [udgået den 31. juli 2021,](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/skype-for-business-online-to-be-retired-in-2021/ba-p/777833) og vi opfordrer kunderne til at migrere til Microsoft Teams. Opbevaringspolitikker for Skype for Business understøttes dog fortsat for eksisterende kunder.

I modsætning til Exchange-mail kan du ikke slå status for Skype-placeringen til for automatisk at inkludere alle brugere, men når du slår denne placering til, skal du manuelt vælge de brugere, hvis samtaler du vil bevare:

![Vælg Skype-placering for opbevaringspolitikker.](../media/skype-location-retention-policies.png)

Når du har valgt denne indstilling **Rediger**, kan du hurtigt inkludere alle brugere i ruden **Skype for Business** ved at vælge det skjulte felt før kolonnen **Navn**. Det er dog vigtigt at forstå, at hver bruger tæller som en bestemt medtagelse i politikken. Så hvis du inkluderer 1.000 brugere ved at markere dette felt, er det det samme, som hvis du manuelt valgte 1.000 brugere at inkludere, hvilket er det maksimale, der understøttes for Skype for Business.

Vær opmærksom på, at **Samtaleoversigt**, en mappe i Outlook, er en funktion, der ikke har noget med Skype-arkivering at gøre. **Samtaleoversigten** kan slås fra af slutbrugeren, men arkivering til Skype udføres ved at gemme en kopi af Skype-samtaler i en skjult mappe, der ikke er tilgængelig for brugeren, men som er tilgængelig for eDiscovery.

## <a name="settings-for-retaining-and-deleting-content"></a>Indstillinger for opbevaring og sletning af indhold

Når du vælger indstillingerne for opbevaring og sletning af indhold, har din politik for opbevaring en af følgende konfigurationer i et angivet tidsrum:

- Bevar kun
    
    Vælg følgende indstillinger for denne konfiguration:
    
    - For opbevaringspolitikker: På siden **Beslut, om du vil bevare indhold, slette det eller begge** sider, skal du vælge **Bevar elementer for en bestemt periode**, angive opbevaringsperioden og derefter for **Ved slutningen af opbevaringsperioden** vælge **Gør intet** for at fjerne opbevaringsindstillingerne.  Eller hvis du vil bevare uden en slutdato, skal du vælge **Bevar elementer for evigt** på denne side.
    
    - For opbevaringsmærkater: På **siden Definer etiketindstillinger** skal du vælge **Bevar elementer på ubestemt tid eller for en bestemt periode** og derefter:
        - Hvis opbevaringsindstillingerne ikke længere skal være i kraft på det navngivne indhold efter et bestemt tidspunkt: Angiv tidsperioden for **Bevar elementer for** på siden **Definer opbevaringsperioden**. Vælg derefter **Deaktiver opbevaringsindstillinger** på siden **Vælg, hvad der sker efter opbevaringsperioden**. Etiketten forbliver på indholdet, men uden begrænsninger, som om det er en [mærkat, der bare klassificeres](retention.md#classifying-content-without-applying-any-actions).
        - Sådan bevares uden en slutdato: Vælg **En ubestemt periode** for **Bevar elementer på** siden **Definer opbevaringsperioden**. Etiketten forbliver på indholdet med eventuelle [eksisterende begrænsninger](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked ).

- Bevar og slet derefter

    Vælg følgende indstillinger for denne konfiguration:
    
    - For opbevaringspolitikker: På siden **Beslut, om du vil bevare indhold, slette det eller begge** sider, skal du vælge **Bevar elementer for en bestemt periode**, angive opbevaringsperioden og derefter vælge **Slet elementer automatisk** i **slutningen af opbevaringsperioden**.
    
    - For opbevaringsmærkater: På siden **Definer etiketindstillinger** skal du vælge **Bevar elementer på ubestemt tid eller i en bestemt periode**, angive opbevaringsperioden og derefter for **Vælg, hvad der sker efter opbevaringsperioden**, vælge enten **Slet elementer automatisk** eller **Start en dispositionsgennemgang**. Du kan få oplysninger om dispositionsgennemgange under [Dispositionsgennemgang](disposition.md#disposition-reviews).

- Kun sletning

    Vælg følgende indstillinger for denne konfiguration:
    
    - For opbevaringspolitikker: På siden **Beslut, om du vil bevare indhold, slette det eller begge** sider, skal du vælge **Slet kun elementer, når de når en bestemt alder**, og angiv tidsperioden.
    
    - For opbevaringsmærkater: På siden **Definer mærkatindstillinger** skal du vælge **Gennemtving handlinger efter en bestemt periode** og angive tidsperioden, der stadig kaldes opbevaringsperioden. Indstillingen **Vælg, hvad der sker, når perioden** automatisk er angivet til **Slet elementer automatisk**.

### <a name="retaining-content-for-a-specific-period-of-time"></a>Bevarelse af indhold i et bestemt tidsrum

Når du konfigurerer en opbevaringsmærkat eller politik for at bevare indhold, vælger du at bevare elementer i et bestemt antal dage, måneder (forudsætter 30 dage for en måned) eller år. Eller du kan også bevare elementerne for evigt. Opbevaringsperioden beregnes ikke ud fra det tidspunkt, hvor politikken blev tildelt, men i henhold til starten af den angivne opbevaringsperiode.

I starten af opbevaringsperioden kan du vælge, hvornår indholdet blev oprettet, eller kun understøttes for filer og SharePoint, OneDrive og Microsoft 365-grupper, hvornår indholdet sidst blev ændret. I forbindelse med opbevaringsmærkater kan du starte opbevaringsperioden fra det indhold, der er mærket, og når der opstår en hændelse.

Eksempler:

- SharePoint: Hvis du vil bevare elementer i en gruppe af websteder i syv år, efter at dette indhold senest er ændret, og et dokument i den pågældende gruppe af websteder ikke er blevet ændret i seks år, bevares dokumentet kun i endnu et år, hvis det ikke ændres. Hvis dokumentet redigeres igen, beregnes dokumentets alder fra den nye dato for seneste ændring, og det bevares i yderligere syv år.

- Exchange: Hvis du vil gemme elementer i en postkasse i syv år, og der blev sendt en meddelelse for seks år siden, bevares meddelelsen kun i ét år. For Exchange-elementer er alderen baseret på den dato, der blev modtaget for indgående mail, eller den dato, der blev sendt for udgående mail. Bevarelse af elementer, der er baseret på, hvornår de senest blev ændret, gælder kun for webstedsindhold i OneDrive og SharePoint.

I slutningen af opbevaringsperioden vælger du, om indholdet skal slettes permanent. For opbevaringspolitikker:

![Siden Med indstillinger for opbevaring.](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

Som forklaret i næste afsnit har opbevaringsmærkater en anden mulighed. for at anvende en anden opbevaringsmærkat med sin egen opbevaringsperiode.

Før du konfigurerer opbevaring, skal du først blive fortrolig med kapacitets- og lagergrænser for de respektive arbejdsbelastninger:

- For SharePoint og OneDrive gemmes bevarede elementer i webstedets bibliotek for bevarelse af venteposition, som er inkluderet i webstedets lagerkvote. Du kan finde flere oplysninger i [Administrer grænser for webstedslager](/sharepoint/manage-site-collection-storage-limits) i Dokumentationen til SharePoint.

- For Exchange, Teams og Yammer, hvor gemte meddelelser gemmes i postkasser, [skal du se Exchange Online grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) og aktivere [automatisk udvidelse af arkivering](autoexpanding-archiving.md).
    
    I ekstreme tilfælde, hvor en stor mængde mails slettes inden for en kort periode, enten af brugere eller automatisk fra politikindstillinger, kan det også være nødvendigt at konfigurere Exchange til oftere at flytte elementer fra mappen Gendanbare elementer i brugerens primære postkasse til mappen Gendanbare elementer i deres arkivpostkasse. Du kan finde en trinvis vejledning under [Forøg kvoten for genoprettelige elementer for postkasser i venteposition](increase-the-recoverable-quota-for-mailboxes-on-hold.md).

#### <a name="relabeling-at-the-end-of-the-retention-period"></a>Genmærkning ved slutningen af opbevaringsperioden

> [!NOTE]
> Denne indstilling udrulles i øjeblikket som prøveversion og kan ændres.

Når du konfigurerer en opbevaringsmærkat til automatisk at anvende en anden opbevaringsmærkat i slutningen af opbevaringsperioden, er elementet underlagt opbevaringsindstillingerne for det nyligt valgte opbevaringsmærkat. Med denne indstilling kan du automatisk ændre opbevaringsindstillingerne for elementet.

Du kan ændre erstatningsmærkaten, når du har oprettet og gemt den primære opbevaringsmærkat. For elementer, der allerede har den primære opbevaringsmærkat anvendt og inden for den konfigurerede opbevaringsperiode, synkroniseres ændringen af erstatningsmærkaten med disse elementer. Som med andre navneændringer kan der gå op til 7 dage for denne synkroniseringsperiode.

For erstatningsmærkaten vælger du typisk en etiket, der har en længere opbevaringsperiode end den primære opbevaringsmærkat. Det er dog ikke nødvendigvis tilfældet på grund af mærkatindstillingen, hvornår opbevaringsperioden skal starte. Den primære opbevaringsmærkat er f.eks. konfigureret til at starte opbevaringsperioden, når elementet oprettes, og erstatningsmærkaten starter opbevaringsperioden, når den er mærket, eller når der opstår en hændelse.

Hvis der også er en ændring i, om etiketten [markerer elementet som en post eller en regelmæssigt post](declare-records.md), kan erstatningsopbevaringsmærkaten også ændre [begrænsningerne for, hvilken handling der er tilladt eller blokeret](records-management.md#records) for det pågældende element.

##### <a name="relabeling-example-configuration"></a>Eksempel på konfiguration med genmærkning

Du kan oprette og konfigurere en opbevaringsmærkat for et krav til overholdelse af branchereglerne for at bevare indhold i tre år, efter at det er oprettet, og markere elementet som en post. Når denne mærkat anvendes, kan brugerne ikke slette elementet fra deres app, fordi det er en af begrænsningerne for en post.

I slutningen af de tre år vil du automatisk bevare indholdet i to år mere på grund af interne politikker for overholdelse af angivne standarder, men det er ikke nødvendigt at markere det som en post med de begrænsninger, som denne konfiguration gælder for.

Hvis du vil fuldføre konfigurationen, skal du vælge etiketindstillingen for at ændre mærkaten i slutningen af opbevaringsperioden og vælge en etiket, der bevarer indhold i fem år, efter at indholdet blev oprettet, og som ikke markerer elementet som en post. 

Med disse sammenkædede indstillinger kan brugerne slette elementet fra deres app efter tre år, men det forbliver tilgængeligt for eDiscovery-søgninger i fem år.

##### <a name="considerations-for-the-relabeling-option"></a>Overvejelser i forbindelse med indstillingen til genmærkning

- Du kan ikke angive en lovmæssig post igen, men erstatningsmærkaten kan konfigureres til at markere indholdet som en lovmæssig post.

- Du kan ikke slette en opbevaringsmærkat, der er valgt som erstatningsmærkat.

- Du kan vælge en erstatningsmærkat, der er konfigureret til at anvende en anden erstatningsmærkat. Der er ingen grænse for, hvor mange erstatningsnavne et element kan have.

- Hvis erstatningsmærkaten markerer elementet som en post eller lovmæssig post, men ikke kan anvendes, fordi filen i øjeblikket er tjekket ud, gøres der en ny prøve på relabelprocessen, når filen tjekkes ind igen, eller udtjekningen kasseres.

- Som et kendt problem i denne prøveversion er en erstatningsmærkat kun synlig for brugere i Outlook, når denne mærkat er inkluderet i en publiceret etiketpolitik for den samme placering, eller den er konfigureret til kun at blive slettet.

##### <a name="configuration-paths-for-relabeling"></a>Konfigurationsstier til genmærkning

Indstillingen til genmærkning i slutningen af opbevaringsperioden har to konfigurationsstier, når du opretter en opbevaringsmærkat:

- Hvis du først har brug for at bevare indhold med den primære etiket (mest almindelige): På siden **Definer etiketindstillinger** skal du vælge **Bevar elementer på ubestemt tid eller for en bestemt periode** og angive opbevaringsperioden. På siden **Vælg, hvad der sker efter opbevaringsperioden** skal du derefter vælge **Skift mærkat** > **Vælg en erstatningsmærkat**.

- Hvis du ikke behøver først at bevare indhold med den primære etiket: På siden **Definer etiketindstillinger** skal du vælge **Gennemtving handlinger efter en bestemt periode**, angive opbevaringsperioden og derefter vælge **Skift mærkat** > **Vælg en erstatningsmærkat**.

I begge tilfælde skal erstatningsmærkaten allerede oprettes, men den skal ikke medtages i en eksisterende mærkatpolitik.

![Skift etiketindstillingen efter opbevaringsperioden.](../media/change-label-option.png)

Alternativt kan dispositionslæsere manuelt vælge en erstatningsmærkat som en del af [processen til gennemgang af fordeling](disposition.md#disposition-reviews) , hvis etiketindstillingen **Start en dispositionsgennemsyn** er valgt på siden **Vælg, hvad der sker efter opbevaringsperioden** .

### <a name="deleting-content-thats-older-than-a-specific-age"></a>Sletning af indhold, der er ældre end en bestemt alder

Opbevaringsindstillinger kan bevare og derefter slette elementer eller slette gamle elementer uden at bevare dem.

Hvis dine opbevaringsindstillinger sletter elementer i begge tilfælde, er det vigtigt at forstå, at den angivne tidsperiode ikke beregnes fra det tidspunkt, hvor politikken blev tildelt, men i henhold til starten af den angivne opbevaringsperiode. Det kan f.eks. være fra det tidspunkt, hvor elementet blev oprettet, ændret eller navngivet.

Derfor skal du først overveje alderen på det eksisterende indhold, og hvordan indstillingerne kan påvirke det pågældende indhold. Overvej at kommunikere dine valgte indstillinger til dine brugere og helpdesk, før indstillingerne anvendes på indhold, hvilket giver dem tid til at vurdere den mulige indvirkning.

### <a name="a-policy-that-applies-to-entire-locations"></a>En politik, der gælder for hele placeringer

Når du vælger placeringer med undtagelse af Skype for Business, er standardindstillingen **Alle**, når status for placeringen er **Slået til**.

Når en opbevaringspolitik gælder for en kombination af hele placeringer, er der ingen grænse for det antal modtagere, websteder, konti, grupper osv., som politikken kan indeholde.

Hvis en politik f.eks. indeholder alle Exchange-mails og alle SharePoint-websteder, medtages alle websteder og modtagere, uanset hvor mange der er. Og for Exchange nedarver alle nye postkasser, der er oprettet efter politikkens anvendelse, automatisk politikken.

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>En politik med specifikke medtagelser eller udeladelser

Vær opmærksom på, at hvis du bruger den valgfri konfiguration til at begrænse dine opbevaringsindstillinger til bestemte brugere, bestemte Microsoft 365-grupper eller bestemte websteder, er der nogle grænser pr. politik, du skal være opmærksom på. Du kan få flere oplysninger under [Begrænsninger for opbevaringspolitikker og politikker for opbevaringsmærkater](retention-limits.md). 

Hvis du vil bruge den valgfri konfiguration til at omfatte dine opbevaringsindstillinger, skal du kontrollere **, at Status** for den pågældende placering er **Slået** til, og derefter bruge linkene til at inkludere eller udelade bestemte brugere, Microsoft 365-grupper eller websteder.

> [!WARNING]
> Hvis du konfigurerer "include"-filer og derefter fjerner den sidste, vender konfigurationen tilbage til **Alle** for placeringen.  Sørg for, at det er den konfiguration, du har til hensigt, før du gemmer politikken.
>
> Hvis du f.eks. angiver et SharePoint-websted, der skal medtages i din opbevaringspolitik, som er konfigureret til at slette data, og derefter fjerner det enkelte websted, vil alle SharePoint-websteder som standard være underlagt opbevaringspolitikken, der sletter data permanent. Det samme gælder for exchange-modtagere, OneDrive-konti, Teams-chatbrugere osv.
>
> I dette scenarie skal du slå placeringen fra, hvis du ikke ønsker, at indstillingen **Alle** for placeringen skal være underlagt opbevaringspolitikken. Du kan også angive de udeladelser, der skal fritages fra politikken.

## <a name="updating-policies-for-retention"></a>Opdaterer politikker for opbevaring

Nogle indstillinger kan ikke ændres, når en politik for opbevaring er oprettet og gemt, som omfatter:
- Politiknavnet og opbevaringsindstillingerne undtagen opbevaringsperioden, og hvornår opbevaringsperioden skal starte.

Hvis du redigerer en opbevaringspolitik, og elementer allerede er underlagt de oprindelige indstillinger i din opbevaringspolitik, anvendes dine opdaterede indstillinger automatisk på disse elementer ud over elementer, der er nyligt identificeret.

Normalt er denne opdatering forholdsvis hurtig, men kan tage flere dage. Når politikreplikeringen på tværs af dine Microsoft 365-placeringer er fuldført, kan du se status for opbevaringspolitikken i Microsoft Purview-compliance-portal ændres fra **Ved (Afventer)** til **Til (udført)**.

## <a name="locking-the-policy-to-prevent-changes"></a>Låsning af politikken for at forhindre ændringer

Hvis du har brug for at sikre, at ingen kan slå politikken fra, slette politikken eller gøre den mindre restriktiv, skal du se [Brug bevarelseslås til at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).
