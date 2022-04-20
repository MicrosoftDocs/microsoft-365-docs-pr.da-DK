---
title: Funktionsreference til indholdssøgning
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MED150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Denne artikel indeholder referenceoplysninger om eDiscovery-værktøjet til indholdssøgning på Microsoft Purview-overholdelsesportalen, som kan hjælpe dig med at få mere at vide om indholdssøgning.
ms.openlocfilehash: 1e1b64583769bbfc815f6b8635e5334936a3b3b7
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64938439"
---
# <a name="feature-reference-for-content-search"></a>Funktionsreference til indholdssøgning

I denne artikel beskrives funktioner og funktionalitet i indholdssøgning.

## <a name="content-search-limits"></a>Grænser for indholdssøgning

Du kan finde en beskrivelse af de grænser, der anvendes på indholdssøgninger, under [Grænser for indholdssøgning](limits-for-content-search.md).

## <a name="building-a-search-query"></a>Oprettelse af en søgeforespørgsel

Du kan finde detaljerede oplysninger om oprettelse af en søgeforespørgsel ved hjælp af booleske søgeoperatorer og søgebetingelser og søgning efter følsomme oplysningstyper og indhold, der deles med brugere uden for din organisation, under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

Vær opmærksom på følgende, når du bruger nøgleordslisten til at oprette en søgeforespørgsel.

- Du skal markere afkrydsningsfeltet **Vis nøgleordsliste** og derefter skrive hvert nøgleord i en separat række for at oprette en søgeforespørgsel, hvor nøgleordene (eller nøgleordsudtryk) i hver række er forbundet af operatoren **OR** . Hvis du indsætter en liste over nøgleord i nøgleordsfeltet eller trykker på **Enter** , når du har skrevet et nøgleord, forbindes de ikke af operatoren **OR** . Her er forkerte og korrekte eksempler på, hvordan du tilføjer en liste over nøgleord.

    **Forkert**

    ![Den forkerte måde at formatere en nøgleordsliste på (ved at indsætte listen i nøgleordsfeltet).](../media/fb54e3df-232a-439a-b3d7-27a60ec76a4c.png)

    **Korrekte**

    ![Den korrekte måde at formatere en nøgleordsliste på (ved at markere afkrydsningsfeltet og derefter indsætte listen).](../media/5d511a7b-c1f9-499c-bffe-e075bfc9adec.png)

- Du kan også forberede en liste over nøgleord eller nøgleordsudtryk i en Excel-fil eller en almindelig tekstfil og derefter kopiere og indsætte listen på nøgleordslisten. Det gør du ved at markere afkrydsningsfeltet **Vis nøgleordsliste** . Klik derefter på den første række på nøgleordslisten, og indsæt listen. Hver linje fra Excel- eller tekstfilen indsættes i en separat række på nøgleordslisten.

- Når du har oprettet en forespørgsel ved hjælp af nøgleordslisten, er det en god idé at bekræfte søgeforespørgslens syntaks for at gøre søgeforespørgslen til det, du vil. I den søgeforespørgsel, der vises under **Forespørgsel** i detaljeruden, er nøgleordene adskilt af teksten **(c:s).** Dette angiver, at nøgleordene er forbundet af en logisk operator, der ligner **OR-operatoren** i funktionaliteten. Hvis søgeforespørgslen indeholder betingelser, er nøgleordene og betingelserne på samme måde adskilt af teksten **(c:c)**. Dette angiver, at nøgleordene er forbundet til betingelserne med en logisk operator, der ligner **AND-operatoren** i funktionaliteten. Her er et eksempel på den søgeforespørgsel (vist i ruden Detaljer), der vises, når du bruger nøgleordslisten og en betingelse.

    ![Eksempel på den forespørgsel, der oprettes, når du bruger nøgleordslisten og en betingelse.](../media/b463750c-57fa-4602-9fed-0d5a420db3ad.png)

- Når du kører en indholdssøgning, kontrollerer Microsoft 365 automatisk søgeforespørgslen efter tegn, der ikke understøttes, og for booleske operatorer, der muligvis ikke har store bogstaver. Tegn, der ikke understøttes, skjules ofte og medfører typisk en søgefejl eller returnerer utilsigtede resultater. Du kan finde flere oplysninger om de tegn, der ikke understøttes, under Kontrollér, om der er [fejl i forespørgslen til indholdssøgningen](check-your-content-search-query-for-errors.md).

- Hvis du har en søgeforespørgsel, der indeholder nøgleord for tegn, der ikke er engelske (f.eks. kinesiske tegn), kan du klikke på **Ikonet Forespørg sprog-land/** områdeForespørgselssprog-land![/område i Indholdssøgning.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) og vælg en kodeværdi for sprog/land-kultur til søgningen. Standardsproget/-området er neutralt. Hvordan kan du se, om du har brug for at ændre sprogindstillingen for en indholdssøgning? Hvis du er sikker på, at indholdsplaceringer indeholder de tegn, du søger efter, men søgningen ikke returnerer nogen resultater, kan sprogindstillingen være årsagen.

## <a name="partially-indexed-items"></a>Delvist indekserede elementer

- Delvist indekserede elementer i postkasser medtages i de anslåede søgeresultater. Delvist indekserede elementer fra SharePoint og OneDrive medtages ikke i de anslåede søgeresultater. Du kan finde flere oplysninger [under Delvist indekserede elementer i eDiscovery](partially-indexed-items-in-content-search.md).

## <a name="searching-onedrive-accounts"></a>Søger i OneDrive konti

- Hvis du vil indsamle en liste over URL-adresserne for de OneDrive websteder i din organisation, skal du se [Opret en liste over alle OneDrive placeringer i din organisation](/onedrive/list-onedrive-urls). Dette script i denne artikel opretter en tekstfil, der indeholder en liste over alle OneDrive websteder. Hvis du vil køre dette script, skal du installere og bruge SharePoint Online Management Shell. Sørg for at føje URL-adressen til organisationens MySite-domæne til hvert OneDrive websted, du vil søge på. Dette er det domæne, der indeholder alle dine OneDrive, `https://contoso-my.sharepoint.com`f.eks. . Her er et eksempel på en URL-adresse til en brugers OneDrive websted: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

    I det sjældne tilfælde, hvor en persons upn (user principal name) ændres, ændres URL-adressen for vedkommendes OneDrive placering for at inkorporere det nye UPN. Hvis det sker, skal du ændre en indholdssøgning ved at tilføje brugerens nye OneDrive URL-adresse og fjerne den gamle. Du kan få flere oplysninger under [Sådan påvirker UPN-ændringer OneDrive URL-adressen](/onedrive/upn-changes).

## <a name="searching-microsoft-teams-and-microsoft-365-groups"></a>Søger i Microsoft Teams og Microsoft 365-grupper

Du kan søge i den postkasse, der er knyttet til et Microsoft-team eller en Microsoft 365 gruppe. Da Microsoft Teams er baseret på Microsoft 365-grupper, er søgning i dem den samme. I begge tilfælde er det kun gruppen eller gruppepostkassen, der søges i. Der søges ikke i gruppe- eller gruppemedlemmernes postkasser. Hvis du vil søge efter dem, skal du specifikt føje dem til søgningen.

Vær opmærksom på følgende ting, når du søger efter indhold i Microsoft Teams og Microsoft 365-grupper.

- Hvis du vil søge efter indhold, der er placeret i Teams og Microsoft 365-grupper, skal du angive den postkasse og det SharePoint websted, der er knyttet til et team eller en gruppe.

- Indhold fra private kanaler gemmes i hver brugers postkasse og ikke i teampostkassen. Hvis du vil søge efter indhold i private kanaler, skal du se [eDiscovery af private og delte kanaler](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

- Kør **Cmdlet'en Get-UnifiedGroup** i Exchange Online for at få vist egenskaber for et team eller en Microsoft 365 gruppe. Dette er en god måde at få URL-adressen til det websted, der er knyttet til et team eller en gruppe. Følgende kommando viser f.eks. de valgte egenskaber for en Microsoft 365 gruppe med navnet Senior Leadership Team:

  ```text
  Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
  DisplayName            : Senior Leadership Team
  Alias                  : seniorleadershipteam
  PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
  SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
  ```

    > [!NOTE]
    > Hvis du vil køre **Cmdlet'en Get-UnifiedGroup**, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har fået tildelt rollen View-Only modtagere.

- Når der søges i en brugers postkasse, bliver der ikke søgt i team eller Microsoft 365 gruppe, som brugeren er medlem af. Når du søger i et team eller en Microsoft 365 gruppe, er det på samme måde kun gruppepostkassen og gruppewebstedet, du angiver, der søges i. Der søges ikke i gruppemedlemmernes postkasser og OneDrive for Business konti, medmindre du udtrykkeligt føjer dem til søgningen.

- Hvis du vil hente en liste over medlemmerne af et team eller en Microsoft 365 gruppe, kan du få vist egenskaberne på siden **Hjemmegrupper** \> i Microsoft 365 Administration.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> Du kan også køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
  ```

    > [!NOTE]
    > Hvis du vil køre cmdlet'en **Get-UnifiedGroupLinks**, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har tildelt rollen View-Only modtagere.

- Samtaler, der er en del af en Teams kanal, gemmes i den postkasse, der er knyttet til teamet. På samme måde gemmes filer, som teammedlemmer deler i en kanal, på teamets SharePoint websted. Derfor skal du tilføje teampostkassen og SharePoint websted som en indholdsplacering for at søge i samtaler og filer i en kanal.

- Alternativt gemmes samtaler, der er en del af chatlisten i Teams i Exchange Online postkasse for de brugere, der deltager i chatten. Og filer, som en bruger deler i Chat-samtaler, gemmes på den OneDrive for Business konto for den bruger, der deler filen. Derfor skal du tilføje de enkelte brugerpostkasser og OneDrive for Business konti som indholdsplaceringer for at søge i samtaler og filer på chatlisten.

    > [!NOTE]
    > I en Exchange hybridinstallation kan brugere med en postkasse i det lokale miljø deltage i samtaler, der er en del af chatlisten i Teams. I dette tilfælde kan der også søges i indhold fra disse samtaler, fordi det er gemt i et skybaseret lagerområde (kaldet en *cloudbaseret postkasse til brugere i det lokale miljø*) for brugere, der har en postkasse i det lokale miljø. Du kan finde flere oplysninger under [Søg efter Teams chatdata for brugere i det lokale miljø](search-cloud-based-mailboxes-for-on-premises-users.md).

- Alle team- eller teamkanaler indeholder en wiki til notetagning og samarbejde. Wikiindholdet gemmes automatisk i en fil med et .mht-format. Denne fil er gemt i dokumentbiblioteket Teams wikidata på teamets SharePoint websted. Du kan bruge værktøjet Indholdssøgning til at søge i wikien ved at angive teamets SharePoint websted som den indholdsplacering, der skal søges efter.

    > [!NOTE]
    > Muligheden for at søge i wikien efter et team eller en kanal (når du søger på teamets SharePoint websted) blev udgivet den 22. juni 2017. Wikisider, der blev gemt eller opdateret på denne dato eller efter, kan søges i. Wikisider, der senest er gemt eller opdateret før denne dato, er ikke tilgængelige til søgning.

- Oversigtsoplysninger for møder og opkald i en Teams kanal gemmes også i postkasserne for de brugere, der har ringet til mødet eller opkaldet. Det betyder, at du kan bruge indholdssøgning til at søge i disse oversigtsposter. Oversigtsoplysninger omfatter:

  - Dato, starttidspunkt, sluttidspunkt og varighed for et møde eller et opkald

  - Den dato og det klokkeslæt, hvor hver deltager deltog i eller forlod mødet eller opkaldet

  - Opkald, der er sendt til talebesked

  - Ubesvarede eller ubesvarede opkald

  - Opkaldsoverførsler, der repræsenteres som to separate opkald

  Det kan tage op til 8 timer, før der kan søges i posterne for møde- og opkaldsoversigten.

  I søgeresultaterne identificeres mødeoversigter som **Møde** i **feltet Type**, og opkaldsoversigter identificeres som **Opkald**. Samtaler, der er en del af en Teams kanal og 1xN-chats, identificeres også som **chat** i feltet **Type**.

  ![Teams møder, opkald og 1xN-chats identificeres i feltet Type.](../media/O365-ContentSearch-Teams-MessageKind.png)

   Du kan finde flere oplysninger under [Microsoft Teams starter eDiscovery til opkald og møder](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-launches-ediscovery-for-calling-and-meetings/ba-p/210947).

- Kortindhold, der genereres af apps i Teams kanaler, 1:1 chats og 1xN-chats, gemmes i postkasser og kan søges i. Et *kort* er en brugergrænsefladeobjektbeholder til korte indholdselementer. Kort kan have flere egenskaber og vedhæftede filer og kan indeholde knapper, der kan udløse korthandlinger. Du kan få flere oplysninger under [Kort](/microsoftteams/platform/task-modules-and-cards/what-are-cards)

  På samme måde som med andet Teams indhold, hvor kortindholdet gemmes, er det baseret på, hvor kortet blev brugt. Indhold for kort, der bruges i en Teams kanal, gemmes i Teams gruppepostkasse. Kortindhold for 1:1- og 1xN-chats gemmes i chatdeltagernes postkasser.

  Hvis du vil søge efter kortindhold, kan du bruge søgebetingelserne `kind:microsoftteams` eller `itemclass:IPM.SkypeTeams.Message` . Når du gennemser søgeresultater, har kortindhold, der genereres af robotter i en Teams kanal, mailegenskaben **Afsender/forfatter** som `<appname>@teams.microsoft.com`, hvor `appname` er navnet på den app, der genererede kortindholdet. Hvis kortindholdet blev genereret af en bruger, identificerer værdien afsender **/forfatter** brugeren.

  Når du får vist kortindhold i indholdssøgeresultater, vises indholdet som en vedhæftet fil til meddelelsen. Den vedhæftede fil hedder `appname.html`, hvor `appname` er navnet på den app, der genererede kortindholdet. Følgende skærmbilleder viser, hvordan kortindhold (for en app med navnet Asana) vises i Teams og i resultaterne af en søgning.

  **Kortindhold i Teams**

  ![Kortindhold i Teams kanalmeddelelse.](../media/CardContentTeams.png)

  **Kortindhold i søgeresultater**

  ![Samme kortindhold i resultaterne af en indholdssøgning.](../media/CardContentEdiscoverySearchResults.png)

  > [!NOTE]
  > Hvis du vil have vist billeder fra kortindhold i søgeresultater på nuværende tidspunkt (f.eks. markeringerne på det forrige skærmbillede), skal du være logget på Teams (på https://teams.microsoft.com) en anden fane i den samme browsersession, som du bruger til at få vist søgeresultaterne. Ellers vises billedpladsholdere.

- Du kan bruge mailegenskaben **Kind** eller søgebetingelsen **Meddelelsestype** til at søge specifikt efter indhold i Teams.

  - Hvis du vil bruge egenskaben **Kind** som en del af søgeforespørgslen med nøgleord, skal du skrive `kind:microsoftteams`i feltet **Nøgleord** i en søgeforespørgsel.

    ![Brug kind:microsoftteams i feltet Nøgleord.](../media/O365-ContentSearch-Teams-Keywords.png)

  - Hvis du vil bruge en søgebetingelse, skal du tilføje betingelsen **Meddelelsestype** og bruge værdien `microsoftteams`.

    ![Brug betingelsen Meddelelsestype sammen med værdien microsoftteams.](../media/O365-ContentSearch-Teams-MessageKindCondition.png)

   Betingelser er logisk forbundet med nøgleordsforespørgslen af OPERATOREN **AND** . Det betyder, at et element skal matche både nøgleordsforespørgslen og den søgebetingelse, der skal returneres i søgeresultaterne. Du kan finde flere oplysninger i afsnittet "Retningslinjer for brug af betingelser" i [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning.](keyword-queries-and-search-conditions.md#guidelines-for-using-conditions)

## <a name="searching-yammer-groups"></a>Søger i Yammer grupper

Du kan bruge mailegenskaben **ItemClass** eller søgebetingelsen **Type** til at søge specifikt efter samtaleelementer i Yammer Grupper.

  - Hvis du vil bruge egenskaben **ItemClass** som en del af søgeforespørgslen med nøgleord, kan du i feltet **Nøgleord** i en søgeforespørgsel skrive en (eller alle) af følgende egenskab:værdipar:

     - ItemClass:IPM.Yammer.message
     - ItemClass:IPM.Yammer.poll
     - ItemClass:IPM.Yammer.praise
     - ItemClass:IPM.Yammer.question

    Du kan f.eks. bruge følgende søgeforespørgsel til at returnere Yammer meddelelser og Yammer roselementer:

    ![Brug egenskaben ItemClass til at søge efter Yammer elementer.](../media/YammerContentSearch1.png)

  - Du kan også bruge mailbetingelsen **Type** og vælge **Yammer meddelelser** for at returnere Yammer elementer. Følgende søgeforespørgsel returnerer f.eks. alle Yammer samtaleelementer, der indeholder nøgleordet "fortroligt".

    ![Brug kortet Typebetingelse til at søge efter Yammer samtaleelementer.](../media/YammerContentSearch2.png)

## <a name="searching-inactive-mailboxes"></a>Søger i inaktive postkasser

Du kan søge i inaktive postkasser i en indholdssøgning. Hvis du vil hente en liste over de inaktive postkasser i din organisation, skal du køre kommandoen `Get-Mailbox -InactiveMailboxOnly` i Exchange Online PowerShell. Du kan også gå til **Opbevaring af** **styring af** \> oplysninger i Security & Compliance Center og derefter klikke på ellipsen **MoreNavigation**![ Bar.](../media/9723029d-e5cd-4740-b5b1-2806e4f28208.gif) \>**Inaktive postkasser**.

Her er et par ting, du skal være opmærksom på, når du søger i inaktive postkasser.

- Hvis en eksisterende indholdssøgning indeholder en brugerpostkasse, og denne postkasse gøres inaktiv, fortsætter indholdssøgningen med at søge i den inaktive postkasse, når du kører søgningen igen, når den bliver inaktiv.

- Nogle gange kan en bruger have en aktiv postkasse og en inaktiv postkasse, der har samme SMTP-adresse. I dette tilfælde er det kun den bestemte postkasse, du vælger som en placering til en indholdssøgning, der søges i. Hvis du med andre ord føjer en brugers postkasse til en søgning, kan du ikke antage, at der søges i både brugerens aktive og inaktive postkasser. Der søges kun i den postkasse, du udtrykkeligt føjer til søgningen.

- Du kan bruge Security & Compliance Center PowerShell til at oprette en indholdssøgning for at søge i en inaktiv postkasse. Hvis du vil gøre dette, skal du tilføje et punktum ( . ) til mailadressen på den inaktive postkasse. Følgende kommando opretter f.eks. en indholdssøgning, der søger i en inaktiv postkasse med mailadressen pavelb@contoso.onmicrosoft.com:

   ```powershell
   New-ComplianceSearch -Name InactiveMailboxSearch -ExchangeLocation .pavelb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true
   ```

- Det anbefales på det kraftigste, at du undgår at have en aktiv postkasse og en inaktiv postkasse med samme SMTP-adresse. Hvis du har brug for at genbruge den SMTP-adresse, der er tildelt til en inaktiv postkasse, anbefaler vi, at du gendanner den inaktive postkasse eller gendanner indholdet af en inaktiv postkasse til en aktiv postkasse (eller arkivet for en aktiv postkasse) og derefter sletter den inaktive postkasse. Du kan få flere oplysninger i et af følgende emner:

  - [Gendan en inaktiv postkasse i Office 365](recover-an-inactive-mailbox.md)

  - [Gendan en inaktiv postkasse i Office 365](restore-an-inactive-mailbox.md)

  - [Slet en inaktiv postkasse i Office 365](delete-an-inactive-mailbox.md)

## <a name="searching-disconnected-or-de-licensed-mailboxes"></a>Søgning i frakoblede postkasser eller postkasser med ikke-licenseret

Hvis den Exchange Online licens (eller hele Microsoft 365-licensen) fjernes fra en brugerkonto eller i Azure Active Directory, bliver brugerens postkasse en *frakoblet* postkasse. Det betyder, at postkassen ikke længere er knyttet til brugerkontoen. Her er, hvad der sker, når du søger i frakoblede postkasser:

- Hvis licensen fjernes fra en postkasse, kan der ikke længere søges i postkassen.

- Hvis en eksisterende indholdssøgning indeholder en postkasse, hvor licensen er fjernet, returneres der ingen søgeresultater fra den frakoblede postkasse, hvis du kører indholdssøgningen igen.

- Hvis du bruger **New-ComplianceSearch-cmdlet'en** til at oprette en indholdssøgning og angiver en afbrudt postkasse som den Exchange indholdsplacering, der skal søges i, returnerer indholdssøgningen ikke nogen søgeresultater fra den afbrudte postkasse.

Hvis du har brug for at bevare dataene i en afbrudt postkasse, så der kan søges i dem, skal du placere en venteposition på postkassen, før du fjerner licensen. Dette bevarer dataene og sørger for, at der kan søges i den frakoblede postkasse, indtil ventepositionen fjernes. Du kan finde flere oplysninger om ventepositioner under [Sådan identificeres den type venteposition, der er placeret på en Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="searching-for-content-in-a-sharepoint-multi-geo-environment"></a>Søgning efter indhold i et SharePoint Multi-Geo miljø

Hvis det er nødvendigt for en eDiscovery-administrator at søge efter indhold i SharePoint og OneDrive i forskellige områder i et [SharePoint multi-geo-miljø](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md), skal du gøre følgende for at få det til at ske:

1. Opret en separat brugerkonto for hver geografisk satellitplacering, som eDiscovery-administratoren skal søge efter. Hvis du vil søge efter indhold på websteder på den pågældende geografiske placering, skal eDiscovery-administratoren logge på den konto, du oprettede for den pågældende placering, og derefter køre en indholdssøgning.

2. Opret et filter for søgetilladelser for hver satellit-geo-placering (og tilsvarende brugerkonto), som eDiscovery-administratoren skal søge efter. Hver af disse søgetilladelser filtrerer begrænser omfanget af indholdssøgningen til en bestemt geografisk placering, når eDiscovery-administratoren er logget på den brugerkonto, der er knyttet til den pågældende placering.

> [!TIP]
> Du behøver ikke at bruge denne strategi, når du bruger søgeværktøjet i [eDiscovery (Premium)](overview-ediscovery-20.md). Det skyldes, at der søges i alle datacentre, når du søger SharePoint websteder og OneDrive konti i Microsoft Purview eDiscovery (Premium). Du skal kun bruge denne strategi for områdespecifikke brugerkonti og søgetilladelser, når du bruger værktøjet Indholdssøgning og kører søgninger, der er knyttet til [eDiscovery-sager](./get-started-core-ediscovery.md).

Lad os f.eks. sige, at en eDiscovery-leder skal søge efter SharePoint og OneDrive indhold på satellitplaceringer i Nordamerika, Europa og Asien og Stillehavsområdet. Det første trin er at oprette tre brugerkonti, én for hver placering. Det næste trin er at oprette tre filtre for søgetilladelser, ét for hver placering *og* en tilsvarende brugerkonto. Her er eksempler på de tre filtre for søgetilladelser for dette scenarie. I hvert af disse eksempler angiver **Region** den SharePoint placering af datacenteret for den pågældende geo, og parameteren **Users** angiver den tilsvarende brugerkonto.

**Nordamerika**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-NAM" -Users ediscovery-nam@contoso.com -Region NAM -Action ALL
```

**Europa**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-EUR" -Users ediscovery-eur@contoso.com -Region EUR -Action ALL
```

**Asien og Stillehavsområdet**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-APC" -Users ediscovery-apc@contoso.com -Region APC -Action ALL
```

Vær opmærksom på følgende ting, når du bruger filtre for søgetilladelser til at søge efter indhold i multi-geo-miljøer:

- Parameteren **Region** dirigerer søgninger til den angivne satellitplacering. Hvis en eDiscovery-leder kun søger SharePoint og OneDrive websteder uden for det område, der er angivet i søgetilladelsesfilteret, returneres der ingen søgeresultater.

- Parameteren **Region** styrer ikke søgninger i Exchange postkasser. Der søges i alle datacentre, når du søger i postkasser.

Du kan finde flere oplysninger om brug af filtre for søgetilladelser i et multi-geo-miljø i afsnittet "Søgning efter og eksport af indhold i Multi-Geo-miljøer" i [Konfigurer overholdelsesgrænser for eDiscovery-undersøgelser](set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).
