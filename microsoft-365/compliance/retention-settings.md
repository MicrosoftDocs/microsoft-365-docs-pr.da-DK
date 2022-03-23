---
title: Konfigurere opbevaringsindstillinger til automatisk at bevare eller slette indhold
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
description: Forstå de indstillinger, du kan konfigurere i en opbevaringspolitik eller opbevaringsetiketpolitik for at beholde det, du ønsker, og fjerne det, du ikke ønsker.
ms.openlocfilehash: 2fd9f2655b13d8c9ac829108d3563a6a4322f3bc
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63592982"
---
# <a name="common-settings-for-retention-policies-and-retention-label-policies"></a>Almindelige indstillinger for opbevaringspolitikker og opbevaringsetiketpolitikker

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](https://aka.ms/ComplianceSD).*

Mange indstillinger for opbevaring er fælles for både opbevaringspolitikker og politikker for opbevaringsmærkater. Brug følgende oplysninger som en hjælp til at konfigurere disse indstillinger til proaktivt at bevare indhold, slette indhold eller begge dele – bevare og derefter slette indholdet.

For de scenarier, der understøtter disse politikker for opbevaring, skal du se:

- [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).
- [Opret opbevaringsnavne, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)

Indstillinger, der er specifikke for hvert scenarie, er forklaret i deres respektive dokumentation.

Du kan finde oversigtsoplysninger om politikker for opbevaring, og hvordan opbevaring fungerer i Microsoft 365, i [Få mere at vide om opbevaringspolitikker og opbevaringsetiketter](retention.md).

## <a name="scopes---adaptive-and-static"></a>Omfang – tilpasset og statisk

Hvis du ikke er bekendt med adaptive og statiske områder og til at hjælpe dig med at vælge, hvilket du skal bruge, når du konfigurerer en politik for opbevaring, skal du se Tilpasnings- eller statiske politikomfang [for opbevaring](retention.md#adaptive-or-static-policy-scopes-for-retention). 

Når du har besluttet dig for, om du vil bruge et tilpasset eller statisk omfang, kan du bruge følgende oplysninger til at konfigurere det:
- [Konfigurationsoplysninger for tilpassede områder](#configuration-information-for-adaptive-scopes)
- [Konfigurationsoplysninger for statiske områder](#configuration-information-for-static-scopes)

> [!TIP]
> Hvis du har politikker, der bruger statiske områder, og du vil konvertere dem til tilpassede områder, skal du lade dine eksisterende politikker være på plads, mens du opretter nye politikker, der bruger tilpassede områder med de samme opbevaringsindstillinger. Valider, at disse nye politikker målretter de korrekte brugere, websteder og grupper, før du deaktiverer eller sletter de gamle politikker med statiske områder.

### <a name="configuration-information-for-adaptive-scopes"></a>Konfigurationsoplysninger for tilpassede områder

Når du vælger at bruge tilpassede områder, bliver du bedt om at vælge, hvilken type tilpasset omfang du ønsker. Der findes tre forskellige typer tilpassede områder, og hver af dem understøtter forskellige attributter eller egenskaber:

| Tilpasset omfangstype | Attributter eller egenskaber, der understøttes, omfatter |
|:-----|:-----|
|**Brugere** – gælder for:  <br/> - Exchange mail <br/> - OneDrive konti <br/> - Teams chatsamtaler <br/> - Teams private kanalmeddelelser <br/> - Yammer brugermeddelelser| Fornavn <br/> Efternavn    <br/>Vist navn <br/> Stilling <br/> Afdeling <br/> Office <br/>Adresse    <br/> By <br/>Stat eller provins <br/>Postnummer <br/> Land eller område <br/> Mailadresser <br/> Alias <br/> Exchange brugerdefinerede attributter: CustomAttribute1 - CustomAttribute15|
|**SharePoint-websteder** – gælder for:  <br/> - SharePoint websteder <br/> - OneDrive konti |URL-adresse til websted <br/>Webstedets navn <br/> SharePoint brugerdefinerede egenskaber: RefinableString00 - RefinableString99 |
|**Microsoft 365-grupper** – gælder for:  <br/> - Microsoft 365 grupper <br/> - Teams kanalmeddelelser <br/> - Yammer communitymeddelelser |Navn <br/> Vist navn <br/> Beskrivelse <br/> Mailadresser <br/> Alias <br/> Exchange brugerdefinerede attributter: CustomAttribute1 - CustomAttribute15 |

Egenskabsnavnene for websteder er baseret på SharePoint websteds administrerede egenskaber. Du kan finde oplysninger om de brugerdefinerede attributter i Brug [af brugerdefinerede egenskaber SharePoint egenskaber for websted til at anvende Microsoft 365 opbevaring med tilpassede politikomfang](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

Attributnavnene for brugere og grupper er baseret på [filtrerbare modtageregenskaber,](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties) der er knyttes til Azure AD-attributter. Eksempel:

- **Alias** er kort til LDAP-navnet **mailNickname**, der vises **som Mail** i Azure AD Administration.
- **Mailadresser** er kort til LDAP-navneproxyadresser, der vises **som proxyadresse** i Azure AD Administration.

De attributter og egenskaber, der er angivet i tabellen, kan nemt angives, når du konfigurerer et tilpasset omfang ved hjælp af den enkle forespørgselsgenerator. Yderligere attributter og egenskaber understøttes med den avancerede forespørgselsgenerator, som beskrevet i følgende afsnit.

> [!TIP]
> Du kan finde flere oplysninger om brug af avanceret forespørgselsgenerator i følgende webinarer: 
> - [Opbygning af avancerede forespørgsler til brugere og grupper med tilpassede politikomfang](https://mipc.eventbuilder.com/event/52683/occurrence/49452/recording?rauth=853.3181650.1f2b6e8b4a05b4441f19b890dfeadcec24c4325e90ac492b7a58eb3045c546ea)
> - [Opbygning af avancerede forespørgsler til SharePoint-websteder med tilpassede politikområder](https://aka.ms/AdaptivePolicyScopes-AdvancedSharePoint)

En enkelt opbevaringspolitik kan have et eller flere tilpassede områder.

#### <a name="to-configure-an-adaptive-scope"></a>Sådan konfigurerer du et tilpasset omfang

Før du konfigurerer dit tilpassede omfang, skal du bruge det forrige afsnit til at identificere, hvilken type omfang der skal oprettes, og hvilke attributter og værdier du skal bruge. Du skal muligvis arbejde sammen med andre administratorer for at bekræfte disse oplysninger. 

Specifikt for SharePoint websteder kan der være yderligere konfigurationer SharePoint hvis du planlægger at bruge [brugerdefinerede egenskaber for webstedet](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com/) du gå til en af følgende placeringer:
    
    - Hvis du bruger løsningen til datastyring:
        - **Løsninger** >  **Datastyring** >  **Fanen Tilpassede områder >** + **Opret omfang**
        
    - Hvis du bruger løsningen til informationsstyring:
       - **Løsninger** >  **Styring af oplysninger** >  **Fanen Tilpassede områder >** + **Opret omfang**
    
    Kan du ikke umiddelbart se din løsning i navigationsruden? Vælg først **Vis alle**. 

2. Følg instruktionerne i konfigurationen for først at vælge omfangets type, og vælg derefter de attributter eller egenskaber, du vil bruge til at opbygge det dynamiske medlemskab, og indtast attributten eller egenskabsværdierne.
    
    Hvis du f.eks. vil konfigurere et tilpasset omfang, der skal bruges til at identificere brugere i Europa, skal du først vælge Brugere som omfangstype og  derefter vælge attributten Land eller område og skrive i **Europa**:
    
    ![Eksempel på tilpasset konfiguration af omfang.](../media/example-adaptive-scope.png)
    
    En gang om dagen kører denne forespørgsel mod Azure AD og identificerer alle brugere, som har den værdi, Europa har angivet for i deres konto for **attributten Land eller** område.
    
    > [!IMPORTANT]
    > Da forespørgslen ikke kører med det samme, er der ingen validering, som du har angivet i værdien korrekt.
    
    Vælg **Tilføj attribut** (for brugere og grupper) eller Tilføj **egenskab (for** websteder) for at bruge en hvilken som helst kombination af attributter eller egenskaber, der understøttes til deres omfangstype, sammen med logiske operatorer til at opbygge forespørgsler. De understøttede **operatorer er lig med**, **er** ikke lig med, **starter** med og starter ikke **med, og** du kan gruppere markerede attributter eller egenskaber. Eksempel:
    
    ![Eksempel på tilpasset konfiguration af omfang med gruppering af attributter.](../media/example-adaptive-scope-grouping.png)
    
    Alternativt kan du vælge Avanceret **forespørgselsgenerator** for at angive dine egne forespørgsler:
    
    - For **bruger**- **Microsoft 365 gruppeomfang** skal du bruge syntaksen [for OPATH-filtrering](/powershell/exchange/recipient-filters). Hvis du f.eks. vil oprette et brugerområde, der definerer medlemskabet efter afdeling, land og stat:
    
        ![Eksempel på tilpasset omfang med avanceret forespørgsel.](../media/example-adaptive-scope-advanced-query.png)
        
        En af fordelene ved at bruge avanceret forespørgselsgenerator til disse områder er et bredere udvalg af forespørgselsoperatorer:
        - **og**
        - **eller**
        - **ikke**
        - **eq** (er lig med)
        - **ne** (ikke lig med)
        - **lt** (mindre end)
        - **gt** (større end)
        - **Like** (strengsammenligning)
        - **notlike** (strengsammenligning)
    
    - Brug **SharePoint (** Keyword Query Language) til at finde websteder. Du er måske allerede fortrolig med at bruge KQL til at SharePoint ved hjælp af indekserede egenskaber for webstedet. For at hjælpe dig med at angive disse KQL-forespørgsler skal du se [Syntaksreference for Sprog til nøgleordsforespørgsel (KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)).
        
        Fordi områder af SharePoint-websteder f.eks. automatisk inkluderer alle SharePoint-webstedstyper, som omfatter Microsoft 365-gruppeforbundne og OneDrive-websteder, kan du bruge den indekserede webstedsegenskab **SiteTemplate** til at medtage eller udelade bestemte webstedstyper. De skabeloner, du kan angive:
        - SITEPAGEPUBLISHING til moderne kommunikationswebsteder
        - GROUP til Microsoft 365 gruppeforbundne websteder
        - TEAMCHANNEL til Microsoft Teams private kanalwebsteder
        - STS til et klassisk SharePoint teamwebsted
        - SPSPERS til OneDrive websteder
        
        Så hvis du vil skabe et tilpasset omfang, der kun omfatter moderne kommunikationswebsteder og Microsoft 365 goup-forbundne og OneDrive-websteder, skal du angive følgende KQL-forespørgsel:
        ````console
        SiteTemplate=SITEPAGEPUBLISHING
        ````
    
    Du kan [validere disse avancerede forespørgsler uafhængigt](#validating-advanced-queries) af omfanget af konfigurationen.
    
    > [!TIP]
    > Du skal bruge den avancerede forespørgselsgenerator, hvis du vil udelade inaktive postkasser. Omvendt kan du målrette kun mod inaktive postkasser. Til denne konfiguration skal du bruge OPATH-egenskaben *IsInactiveMailbox*:
    > 
    > - Hvis du vil udelade inaktive postkasser, skal du sikre dig, at forespørgslen indeholder: `(IsInactiveMailbox -eq "False")`
    > - Hvis du kun vil målrette mod inaktive postkasser, skal du angive: `(IsInactiveMailbox -eq "True")`

3. Opret så mange tilpassede områder, som du har brug for. Du kan vælge et eller flere tilpassede områder, når du opretter din opbevaringspolitik.

> [!NOTE]
> Det kan tage op til fem dage, før forespørgslerne er helt udfyldede, og ændringerne vil ikke være øjeblikkelige. Faktor i denne forsinkelse ved at vente et par dage, før du føjer et nyligt oprettet omfang til en opbevaringspolitik.

Sådan bekræftes de aktuelle medlemskabs- og medlemskabsændringer for et tilpasset omfang:

1. Dobbeltklik (eller vælg og tryk på Enter) området på **siden Tilpassede** områder

2. Vælg Detaljer om omfang **i** ruden Detaljer i **pop op-vinduet**. 
    
    Gennemgå de oplysninger, der identificerer alle de brugere, websteder eller grupper, der aktuelt er omfattet, hvis de automatisk er blevet tilføjet eller fjernet, samt dato og klokkeslæt for medlemskabet ændres.

> [!TIP]
> Brug indstillingen [for politikopslag](retention.md#policy-lookup) til at identificere de politikker, der aktuelt er tildelt til bestemte brugere, websteder og Microsoft 365 grupper.

#### <a name="validating-advanced-queries"></a>Validering af avancerede forespørgsler

Du kan validere avancerede forespørgsler manuelt ved hjælp af PowerShell og SharePoint søgning:
- Brug PowerShell til områdetyperne **Brugere** **og Microsoft 365 Grupper**
- Brug SharePoint til at søge efter områdetype **SharePoint websteder**

Sådan kører du en forespørgsel ved hjælp af PowerShell:

1. [Forbind at Exchange Online PowerShell ved](/powershell/exchange/connect-to-exchange-online-powershell) hjælp af en konto [med Exchange Online administratortilladelser](/powershell/exchange/find-exchange-cmdlet-permissions#use-powershell-to-find-the-permissions-required-to-run-a-cmdlet).

2. Brug enten [Get-Recipient eller](/powershell/module/exchange/get-recipient) [Get-Mailbox](/powershell/module/exchange/get-mailbox) med parameteren *-Filter* og din [OPATH-forespørgsel](/powershell/exchange/filter-properties) for det tilpassede omfang omsluttet af klammeparenteser (`{`,`}`). Hvis attributværdierne er strenge, skal disse værdier omsluttes af dobbelte eller enkelte anførselstegn.  

    Du kan afgøre, om du skal `Get-Mailbox` `Get-Recipient` bruge eller validere ved at identificere, hvilken cmdlet der understøttes af [den OPATH-egenskab](/powershell/exchange/filter-properties) , du vælger til forespørgslen.

    > [!IMPORTANT]
    > `Get-Mailbox` understøtter ikke *modtagertypen MailUser* , `Get-Recipient` så den skal bruges til at validere forespørgsler, der omfatter lokale postkasser i et hybridmiljø.

    Hvis du vil validere **et Brugerområde** , skal du bruge enten:
    - `Get-Mailbox` med `-RecipientTypeDetails UserMailbox` eller
    - `Get-Recipient` med `-RecipientTypeDetails UserMailbox,MailUser`
    
    Hvis du vil validere **Microsoft 365 gruppens** omfang, skal du bruge:
    - `Get-Mailbox` eller `Get-Recipient` med `-RecipientTypeDetails GroupMailbox`

    Hvis du f.eks. vil validere **et brugerområde** , kan du bruge:
    
    ````PowerShell
    Get-Recipient -RecipientTypeDetails UserMailbox,MailUser -Filter {Department -eq "Marketing"} -ResultSize Unlimited
    ````
    
    Hvis du vil validere **Microsoft 365 gruppeområde**, kan du bruge:
    
    ```PowerShell
    Get-Mailbox -RecipientTypeDetails GroupMailbox -Filter {CustomAttribute15 -eq "Marketing"} -ResultSize Unlimited
    ```

3. Kontrollér, at outputtet svarer til de forventede brugere eller grupper for dit tilpassede omfang. Hvis ikke, skal du kontrollere din forespørgsel og værdierne med den relevante administrator for Azure AD eller Exchange.
 
Sådan kører du en forespørgsel SharePoint søgefunktionen:

1. Ved hjælp af en global administratorkonto eller en konto, der SharePoint administratorrollen, skal du gå til `https://<your_tenant>.sharepoint.com/search`.

2. Brug søgelinjen til at angive din KQL-forespørgsel.

3. Kontrollér, at søgeresultaterne svarer til de forventede URL-adresser for webstedet for dit tilpassede omfang. Hvis de ikke gør det, skal du kontrollere din forespørgsel og URL-adresserne med den relevante administrator for at få SharePoint.

### <a name="configuration-information-for-static-scopes"></a>Konfigurationsoplysninger for statiske områder

Når du vælger at bruge statiske områder, skal du derefter beslutte, om du vil anvende politikken på alle forekomster for den valgte placering (hele placeringen) eller for at medtage eller udelade bestemte forekomster (bestemte inklusioner eller udeladelser).

#### <a name="a-policy-that-applies-to-entire-locations"></a>En politik, der gælder for hele placeringer

Med undtagelse af Skype for Business er standardindstillingen, at alle forekomster for de valgte placeringer automatisk medtages i politikken, uden at du behøver at angive dem som inkluderet.

For eksempel **Alle modtagere af** Exchange **mailplacering**. Med denne standardindstilling medtages alle eksisterende brugerpostkasser i politikken, og alle nye postkasser, der oprettes, når politikken anvendes, arver automatisk politikken.

#### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>En politik med specifikke inklusioner eller udeladelse

Vær opmærksom på, at hvis du bruger den valgfri konfiguration til at begrænse opbevaringsindstillingerne til bestemte brugere, bestemte Microsoft 365-grupper eller bestemte websteder, er der nogle begrænsninger pr. politik, du skal være opmærksom på. Få mere at vide under Begrænsninger [for opbevaringspolitikker og opbevaringsmærkatpolitikker](retention-limits.md). 

Hvis du vil bruge den valgfri konfiguration til at begrænse dine opbevaringsindstillinger, skal du kontrollere, at **Status** for den pågældende placering er **Til og derefter** bruge linkene til at medtage eller udelade bestemte brugere, Microsoft 365 grupper eller websteder.

> [!WARNING]
> Hvis du konfigurerer forekomster til at medtage og derefter fjerne den sidste, ændres konfigurationen **til Alle** for placeringen.  Sørg for, at dette er den konfiguration, du regner med, før du gemmer politikken.
>
> Hvis du f.eks. angiver et SharePoint-websted, der skal medtages i din opbevaringspolitik, som er konfigureret til at slette data, og derefter fjerner det enkelte websted, vil alle SharePoint-websteder som standard være underlagt opbevaringspolitikken, der sletter data permanent. Det samme gælder også for Exchange, brugere OneDrive konti, Teams og chatbrugere osv.
>
> I dette scenarie skal du slå placeringen fra, hvis indstillingen Alle ikke skal være underlagt  opbevaringspolitikken for placeringen. Alternativt kan du angive, at udelade forekomster, der skal fritages fra politikken.

## <a name="locations"></a>Placeringer

Placeringer i politikker til opbevaring identificerer bestemte Microsoft 365, der understøtter opbevaringsindstillinger, f.eks. Exchange mail og SharePoint websteder. Brug følgende afsnit til de placeringer, der har konfigurationsoplysninger og mulige undtagelser, du skal være opmærksom på, når du vælger dem til din politik.

### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>Konfigurationsoplysninger til Exchange mail og Exchange offentlige mapper

**Mailplaceringen Exchange** opbevaring af brugernes mail, kalender og andre postkasseelementer ved at anvende opbevaringsindstillinger på niveauet for en postkasse. Delte postkasser understøttes også.

Ressourcepostkasser, kontakter og Microsoft 365-gruppepostkasser understøttes ikke til Exchange mail. For Microsoft 365 gruppepostkasser skal du vælge **Microsoft 365 Gruppeplacering** i stedet. Selvom Exchange-placeringen i første omgang tillader, at en gruppepostkasse vælges til et statisk omfang, modtager du en fejlmeddelelse om, at "RemoteGroupMailbox" ikke er et gyldigt valg for denne placering, når du forsøger at gemme opbevaringspolitikken.

Afhængigt af din politikkonfiguration er [inaktive](inactive-mailboxes-in-office-365.md) postkasser muligvis inkluderet eller ej:

- Statiske politikomfang omfatter inaktive postkasser, når du bruger standardkonfigurationen Alle modtagere, men **understøttes** ikke ved [bestemte inklusioner eller udeladelse.](#a-policy-with-specific-inclusions-or-exclusions) Men hvis du medtager eller udelader en modtager, der har en aktiv postkasse på det tidspunkt, hvor politikken anvendes, og postkassen senere bliver inaktiv, vil opbevaringsindstillingerne fortsat blive anvendt eller udeladt.

- Adaptive politikomfang omfatter som standard inaktive postkasser, når de opfylder omfangets forespørgsel. Du kan udelukke dem ved hjælp af den avancerede forespørgselsgenerator og *OPATH-egenskaben IsInactiveMailbox*:
    
    ```console
    (IsInactiveMailbox -eq "False")
    ```

Hvis du bruger et statisk politikområde og vælger modtagere, der skal medtages eller udelades, kan du vælge distributionsgrupper og mailaktiverede sikkerhedsgrupper som en effektiv måde at vælge flere modtagere på i stedet for at markere dem én efter en. Når du bruger denne indstilling i baggrunden, udvides disse grupper automatisk på konfigurations tidspunktet for konfigurationen for at vælge postkasserne for brugerne i gruppen. Hvis medlemskabet af disse grupper senere ændres, opdateres din eksisterende opbevaringspolitik ikke automatisk i modsætning til tilpassede politikomfang.

Hvis du vil have detaljerede oplysninger om, hvilke postkasseelementer der medtages og udelades, når du konfigurerer opbevaringsindstillinger for Exchange, skal du se Hvad er inkluderet [for opbevaring og sletning](retention-policies-exchange.md#whats-included-for-retention-and-deletion).

Mappen **Exchange mappeplacering anvender opbevaringsindstillinger** for alle offentlige mapper og kan ikke anvendes på mappe- eller postkasseniveau.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Undtagelser for automatisk anvendelse af politikker, der er konfigureret til følsomme oplysningstyper

Når du konfigurerer en automatisk anvendelsespolitik, der bruger følsomme oplysningstyper, og vælger **Exchange på mailplaceringen**:

- Microsoft 365 gruppepostkasser er inkluderet.

- Alle postkasser inkluderes automatisk, også selvom du konfigurerer et tilpasset omfang til at identificere bestemte postkasser. Hvis du har valgt et statisk politikområde, kan du ikke angive modtagere, der skal medtages eller udelades.

### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>Konfigurationsoplysninger for SharePoint og OneDrive konti

Når du vælger **placeringen SharePoint-websteder**, kan politikken for opbevaring bevare og slette dokumenter på SharePoint-kommunikationswebsteder, teamwebsteder, der ikke er forbundet med Microsoft 365-grupper, og klassiske websteder. Medmindre du bruger tilpassede politikområder, understøttes teamwebsteder, der er forbundet af Microsoft 365-grupper, ikke med denne indstilling, og i stedet skal du bruge placeringen **Microsoft 365 Grupper**, der gælder for indhold i [gruppens](#exceptions-for-adaptive-policy-scopes) postkasse, websted og filer.

Hvis du vil have detaljerede oplysninger om, hvad der medtages og udelades, når du konfigurerer opbevaringsindstillinger for SharePoint og OneDrive, skal du se Hvad er inkluderet [for opbevaring og sletning](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion).

Når du angiver dine placeringer til SharePoint websteder eller OneDrive-konti, behøver du ikke tilladelser for at få adgang til webstederne. Ved statiske områder sker der ingen validering på det tidspunkt, du angiver URL-adressen på **siden Rediger** placeringer. Men de SharePoint, du angiver, kontrolleres, at de findes på den sidste side i konfigurationen. Hvis denne kontrol mislykkes, får du vist en meddelelse om, at valideringen mislykkedes for den URL-adresse, du angav, og opbevaringspolitikken kan ikke oprettes, før valideringskontrollen er gået. Hvis du får vist denne meddelelse, skal du gå tilbage i konfigurationsprocessen for at ændre URL-adressen eller fjerne webstedet fra opbevaringspolitikken.

Hvis du vil angive OneDrive-konti, [skal du se Få en liste over alle OneDrive-webadresser i organisationen](/onedrive/list-onedrive-urls).

> [!NOTE]
> Når du angiver individuelle OneDrive-konti, skal du være opmærksom på, at medmindre OneDrive-konti er klargjort, oprettes [URL-adressen](/onedrive/pre-provision-accounts) ikke, før en bruger har adgang til deres OneDrive for første gang.
>
> Desuden ændres OneDrive automatisk[,](/onedrive/upn-changes) hvis der er en ændring i brugerens UPN. Eksempelvis en ændring af navn, f.eks. hvad der sker, hvad der sker, eller en ændring af domænenavnet for at understøtte en organisations omdøbning eller virksomhedens navn. Hvis UPN'et ændres, skal du opdatere de OneDrive URL-adresser, du angiver for opbevaringsindstillinger.
>
> På grund af udfordringerne ved pålideligt at angive URL-adresser, som individuelle brugere kan medtage eller udelade ved statiske områder, er [adaptive](retention.md#adaptive-or-static-policy-scopes-for-retention) områder  med typen Brugerområde bedre egnet til dette formål.

#### <a name="exceptions-for-adaptive-policy-scopes"></a>Undtagelser for tilpassede politikomfang

Når du konfigurerer en politik for opbevaring, der bruger tilpassede politikområder, og vælger SharePoint **webstedsplacering**:

- OneDrive-websteder Microsoft 365 gruppeforbundne websteder er inkluderet i tillæg til SharePoint-kommunikationswebsteder, teamwebsteder, der ikke er forbundet af Microsoft 365-grupper, og klassiske websteder.

### <a name="configuration-information-for-microsoft-365-groups"></a>Konfigurationsoplysninger for Microsoft 365 grupper

Hvis du vil bevare eller slette indhold for Microsoft 365 gruppe (tidligere Office 365 gruppe), skal du **bruge Microsoft 365 gruppeplaceringen**. I forbindelse med opbevaringspolitikker omfatter denne placering gruppepostkassen og SharePoint teamwebstedet. For opbevaringsetiketter omfatter denne placering kun SharePoint teamwebsted.

> [!NOTE]
> Selvom en Microsoft 365 gruppe har en Exchange-postkasse, vil en opbevaringspolitik for Exchange-mailplaceringen  ikke indeholde indhold i Microsoft 365 gruppepostkasser.

Hvis du bruger statiske områder: Selvom Exchange-mailplaceringen for et statisk omfang indledningsvist giver dig mulighed for at angive, om en gruppepostkasse skal medtages eller udelades, når du forsøger at gemme opbevaringspolitikken, får du vist en fejlmeddelelse om, at "RemoteGroupMailbox" ikke er et gyldigt valg for Exchange-placeringen.

Som standard omfatter en opbevaringspolitik for en Microsoft 365 gruppe gruppepostkassen og SharePoint teamwebsted. Filer, der er gemt på SharePoint teams-webstedet, er dækket med denne placering, men ikke Teams-chats eller Teams-kanalmeddelelser, der har deres egne opbevaringspolitikplaceringer.

Hvis du vil ændre standardindstillingen, fordi du ønsker, at opbevaringspolitikken kun skal gælde for Microsoft 365-postkasserne eller kun de tilknyttede SharePoint-teamwebsteder, skal du bruge [Cmdlet'en Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell *med parameteren* Applications med en af følgende værdier:

- `Group:Exchange`til Microsoft 365 postkasser, der er knyttet til gruppen.
- `Group:SharePoint`til SharePoint websteder, der er knyttet til gruppen.

Hvis du vil vende tilbage til standardværdien for både postkassen og SharePoint for de valgte Microsoft 365, skal du angive `Group:Exchange,SharePoint`.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Undtagelser for automatisk anvendelse af politikker, der er konfigureret til følsomme oplysningstyper

Når du konfigurerer en automatisk anvendelsespolitik, der bruger følsomme oplysningstyper, og vælger **Microsoft 365 gruppeplacering**:

- Microsoft 365 gruppepostkasser medtages ikke. Hvis du vil medtage disse postkasser i din politik, skal Exchange **vælge mailplaceringen** i stedet.

#### <a name="what-happens-if-a-microsoft-365-group-is-deleted-after-a-policy-is-applied"></a>Hvad sker der, hvis Microsoft 365 gruppe slettes, når en politik er anvendt

Når en politik for opbevaring (statisk politikomfang eller tilpasset) anvendes på en Microsoft 365 gruppe, og den pågældende gruppe derefter slettes fra Azure Active Directory:

- Gruppetilsluttede SharePoint-websted bevares og administreres fortsat af opbevaringspolitikken med Microsoft 365 **gruppeplaceringen**. Webstedet er stadig tilgængeligt for de personer, der havde adgang til det, før gruppen blev slettet, og alle nye tilladelser skal nu administreres via SharePoint.
    
    På nuværende tidspunkt kan du ikke udelukke webstedet fra placeringen Microsoft 365 grupper, fordi du ikke kan angive den slettede gruppe. Hvis du vil frigive opbevaringspolitikken fra dette websted, skal du kontakte Microsoft Support. Du kan f.eks[. åbne en serviceanmodning i Microsoft 365 Administration Center](https://admin.microsoft.com/Adminportal/Home#/support).

- Postkassen for den slettede gruppe bliver inaktiv og vil som SharePoint websted, forbliver underlagt opbevaringsindstillinger. Du kan finde flere oplysninger [i Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md).

### <a name="configuration-information-for-skype-for-business"></a>Konfigurationsoplysninger for Skype for Business

> [!NOTE]
> Skype for Business [udgået den 31. juli 2021,](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/skype-for-business-online-to-be-retired-in-2021/ba-p/777833) og vi opfordrer kunderne til at overflytte Microsoft Teams. Opbevaringspolitikker for eksisterende Skype for Business understøttes dog fortsat for eksisterende kunder.

I modsætning Exchange anden mail kan du ikke slå status for placeringen på Skype til for automatisk at medtage alle brugere, men når du slår denne placering til, skal du derefter manuelt vælge de brugere, hvis samtaler du vil beholde:

![Vælg Skype opbevaringspolitikker.](../media/skype-location-retention-policies.png)

Når du har valgt **indstillingen** Rediger i **ruden Skype for Business**, kan du hurtigt medtage alle brugere ved at markere det skjulte felt før **kolonnen** Navn. Det er dog vigtigt at forstå, at hver enkelt bruger tæller som en bestemt medtagelse i politikken. Så hvis du medtager 1.000 brugere ved at markere dette felt, er det det samme, som hvis du manuelt valgte at medtage 1.000 brugere, hvilket er den maksimale understøttede værdi for Skype for Business.

Vær opmærksom på **, at samtaleoversigten**, en mappe i Outlook, er en funktion, der ikke har noget at gøre Skype arkivering. **Samtaleoversigten** kan deaktiveres af slutbrugeren, men arkivering for Skype udføres ved at gemme en kopi af Skype-samtaler i en skjult mappe, der er utilgængelig for brugeren, men som er tilgængelig for eDiscovery.

## <a name="settings-for-retaining-and-deleting-content"></a>Indstillinger til at bevare og slette indhold

Ved at vælge indstillingerne for at bevare og slette indhold har din politik for opbevaring en af følgende konfigurationer i en bestemt tidsperiode:

- Be behold kun

    I denne konfiguration skal du **vælge Bevar elementer for en bestemt periode** **og Ved afslutning af en opbevaringsperiode: Gør intet**. Eller vælg Behold **elementer uendeligt**.

- Behold og slet derefter

    I denne konfiguration skal du **vælge Bevar elementer for en bestemt periode** **og Ved opbevaringsperiodens afslutning: Slet elementer automatisk**.

- Kun slette

    I denne konfiguration skal du vælge **Slet kun elementer, når de når en bestemt alder**.

### <a name="retaining-content-for-a-specific-period-of-time"></a>Bevare indhold i en bestemt tidsperiode

Når du konfigurerer et opbevaringsnavn eller en politik til at bevare indhold, vælger du at bevare elementer i et bestemt antal dage, måneder eller år. Alternativt kan du bevare elementerne uendeligt. Opbevaringsperioden beregnes ikke fra det tidspunkt, politikken blev tildelt, men i henhold til starten af den opbevaringsperiode, der er angivet.

I starten af opbevaringsperioden kan du vælge, hvornår indholdet blev oprettet eller, kun understøttet for filer og SharePoint, OneDrive og Microsoft 365 Grupper, hvornår indholdet sidst blev ændret. For opbevaringsnavne kan du starte opbevaringsperioden fra indholdet blev mærket, og hvornår en hændelse forekommer.

Eksempler:

- SharePoint: Hvis du vil bevare elementer i en gruppe af websteder i syv år, efter at dette indhold senest er blevet ændret, og et dokument i den pågældende gruppe af websteder ikke er blevet ændret i seks år, bevares dokumentet kun i endnu et år, hvis det ikke ændres. Hvis dokumentet redigeres igen, beregnes alderen på dokumentet fra den nye dato for seneste ændring, og det bevares i endnu syv år.

- Exchange: Hvis du vil bevare elementer i en postkasse i syv år, og der blev sendt en meddelelse for seks år siden, bevares meddelelsen i kun ét år. For Exchange, er alderen baseret på modtagelsesdatoen for indgående mail eller den dato, der sendes til udgående mail. Bevarelse af elementer, der er baseret på, hvornår det sidst blev ændret, gælder kun for webstedsindhold i OneDrive og SharePoint.

Ved slutningen af en opbevaringsperiode skal du vælge, om du ønsker, at indholdet skal slettes permanent:

![Siden Opbevaringsindstillinger.](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

Før du konfigurerer en opbevaring, skal du først gøre dig bekendt med kapacitets- og lagergrænser for de respektive arbejdsbelastninger:

- For SharePoint og OneDrive gemmes bevarede elementer i biblioteket til opbevaring af dokumenter, som er inkluderet i webstedets lagerkvote. Få mere at vide under [Administrer lagergrænser for websteder](/sharepoint/manage-site-collection-storage-limits) i SharePoint dokumentationen.

- Du Exchange oplysninger Teams, Yammer, hvor gemte meddelelser gemmes i postkasser, under [Begrænsninger Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) aktivere automatisk [arkivering](autoexpanding-archiving.md).
    
    I ekstreme tilfælde, hvor en stor mængde mail slettes i en kort tidsperiode, enten af brugere eller automatisk fra politikindstillinger, skal du muligvis også konfigurere Exchange til oftere at flytte elementer fra mappen Genoprettelige elementer i brugerens primære postkasse til mappen Genoprettelige elementer i brugerens arkivpostkasse. Du kan finde en trinvis vejledning under Øg [kvoten for genoprettelige elementer for postkasser i venteposition](increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="deleting-content-thats-older-than-a-specific-age"></a>Sletning af indhold, der er ældre end en bestemt alder

En politik for opbevaring kan bevare og derefter slette elementer eller slette gamle elementer uden at beholde dem.

I begge tilfælde, hvis din politik sletter elementer, er det vigtigt at forstå, at den tidsperiode, du angiver, ikke beregnes fra det tidspunkt, hvor politikken blev tildelt, men i henhold til starten af den angivne opbevaringsperiode. Eksempelvis fra det tidspunkt, hvor elementet blev oprettet, ændret eller navnmærket.

Af denne grund skal du først overveje alderen på det eksisterende indhold, og hvordan politikken kan påvirke indholdet. Du kan også kommunikere den nye politik til dine brugere, før du tildeler den, for at give dem tid til at vurdere den mulige indvirkning.

### <a name="a-policy-that-applies-to-entire-locations"></a>En politik, der gælder for hele placeringer

Når du vælger placeringer, med undtagelse Skype for Business, er standardindstillingen Alle, når status for placeringen  er **Til**.

Når en opbevaringspolitik gælder for enhver kombination af hele placeringer, er der ingen begrænsninger for antallet af modtagere, websteder, konti, grupper osv., som politikken kan omfatte.

Hvis en politik f.eks. omfatter alle Exchange mail og alle SharePoint-websteder, medtages alle websteder og modtagere, uanset hvor mange. Og for Exchange, arver enhver ny postkasse, der oprettes, når politikken anvendes, automatisk politikken.

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>En politik med specifikke inklusioner eller udeladelse

Vær opmærksom på, at hvis du bruger den valgfri konfiguration til at begrænse opbevaringsindstillingerne til bestemte brugere, bestemte Microsoft 365-grupper eller bestemte websteder, er der nogle begrænsninger pr. politik, du skal være opmærksom på. Få mere at vide under Begrænsninger [for opbevaringspolitikker og opbevaringsmærkatpolitikker](retention-limits.md). 

Hvis du vil bruge den valgfri konfiguration til at begrænse dine opbevaringsindstillinger, skal du kontrollere, at **Status** for den pågældende placering er **Til og derefter** bruge linkene til at medtage eller udelade bestemte brugere, Microsoft 365 grupper eller websteder.

> [!WARNING]
> Hvis du konfigurerer omfatter og derefter fjerner den sidste, ændres konfigurationen til **Alle** for placeringen.  Sørg for, at dette er den konfiguration, du regner med, før du gemmer politikken.
>
> Hvis du f.eks. angiver et SharePoint-websted, der skal medtages i din opbevaringspolitik, som er konfigureret til at slette data, og derefter fjerner det enkelte websted, vil alle SharePoint-websteder som standard være underlagt opbevaringspolitikken, der sletter data permanent. Det samme gælder for brugere, Exchange, eksterne OneDrive, brugere Teams chatbrugere osv.
>
> I dette scenarie skal du slå placeringen fra, hvis indstillingen Alle ikke skal være underlagt  opbevaringspolitikken for placeringen. Alternativt kan du angive, at undtages fra politikken.

## <a name="updating-policies-for-retention"></a>Opdateringspolitikker for opbevaring

Nogle indstillinger kan ikke ændres, efter en opbevaringspolitik er oprettet og gemt, herunder:
- Politiknavnet og opbevaringsindstillingerne undtagen opbevaringsperioden og hvornår opbevaringsperioden skal startes.

Hvis du redigerer en opbevaringspolitik og elementer allerede er underlagt de oprindelige indstillinger i din opbevaringspolitik, dine opdaterede indstillinger vil automatisk blive anvendt på disse elementer ud over elementer, der er nyligt identificeret.

Denne opdatering er normalt ret hurtig, men kan tage flere dage. Når politikreplikeringen på tværs af dine Microsoft 365-placeringer er fuldført, får du vist status for opbevaringspolitikken i Microsoft 365 Overholdelsescenter ændres fra Til (Afventer **)** til Til **(fuldført)**.

## <a name="locking-the-policy-to-prevent-changes"></a>Låse politikken for at forhindre ændringer

Hvis du har brug for at sikre, at ingen kan deaktivere politikken, slette politikken eller gøre den mindre restriktiv, skal du se Brug Preservation Lock til at begrænse ændringer i opbevaringspolitikker og politikker for [opbevaringsmærkater](retention-preservation-lock.md).
