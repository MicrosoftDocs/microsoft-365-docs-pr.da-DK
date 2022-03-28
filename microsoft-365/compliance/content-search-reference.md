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
description: Denne artikel indeholder referenceoplysninger om værktøjet eDiscovery-indholdssøgning i værktøjet Microsoft 365 Overholdelsescenter så du kan lære de mange detaljer om indholdssøgning.
ms.openlocfilehash: 3f2918c378d94fd65d4a89afed50957a2da40a7d
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716370"
---
# <a name="feature-reference-for-content-search"></a>Funktionsreference til indholdssøgning

I denne artikel beskrives funktioner og funktionalitet ved indholdssøgning.

## <a name="content-search-limits"></a>Begrænsninger for indholdssøgning

Hvis du vil have en beskrivelse af de begrænsninger, der gælder for indholdssøgninger, skal du [se Begrænsninger for indholdssøgning](limits-for-content-search.md).

## <a name="building-a-search-query"></a>Opbygge en søgeforespørgsel

Du kan finde detaljerede oplysninger om oprettelse af en søgeforespørgsel ved hjælp af booleske søgeoperatorer og søgebetingelser og søgning efter typer af følsomme oplysninger og indhold, der deles med brugere uden for organisationen, under Nøgleordsforespørgsler og søgebetingelser [for indholdssøgning](keyword-queries-and-search-conditions.md).

Husk følgende, når du bruger listen med nøgleord til at oprette en søgeforespørgsel.

- Du skal markere afkrydsningsfeltet  Vis nøgleordsliste og derefter skrive hvert nøgleord i en separat række for at oprette en søgeforespørgsel, hvor nøgleord (eller nøgleordsfraser) i hver række forbindes af **operatoren ELLER**. Hvis du indsætter en liste over nøgleord i nøgleordsfeltet eller trykker på **Enter** efter at have skrevet et nøgleord, vil de ikke blive forbundet af **OPERATORen ELLER** . Her er forkerte og korrekte eksempler på, hvordan du tilføjer en liste over nøgleord.

    **Forkert**

    ![Den forkerte måde at formatere en liste med nøgleord på (ved at indsætte listen i nøgleordsfeltet).](../media/fb54e3df-232a-439a-b3d7-27a60ec76a4c.png)

    **Korrekt**

    ![Den korrekte måde at formatere en liste med nøgleord på (ved at markere afkrydsningsfelt og derefter indsætte liste).](../media/5d511a7b-c1f9-499c-bffe-e075bfc9adec.png)

- Du kan også forberede en liste over nøgleord eller nøgleord i en Excel-fil eller en almindelig tekstfil og derefter kopiere og indsætte listen i listen over nøgleord. For at gøre dette skal du markere **afkrydsningsfeltet Vis nøgleordsliste** . Klik derefter på den første række på listen med nøgleord, og indsæt listen. Hver linje fra Excel eller tekstfilen indsættes i separat række på listen over nøgleord.

- Når du har oprettet en forespørgsel ved hjælp af listen med nøgleord, er det en god ide at bekræfte syntaksen for søgeforespørgslen for at gøre søgeforespørgslen til det, du havde til hensigt. I den søgeforespørgsel, der **vises under Forespørgsel** i detaljeruden, adskilles nøgleordene af teksten **(c:s)**. Dette angiver, at nøgleordene er forbundet af en logisk operator, der i funktionalitet svarer til **OPERATOREN ELLER** . Hvis din søgeforespørgsel indeholder betingelser, adskilles nøgleordene og betingelserne ligeledes af teksten **(c:c)**. Dette angiver, at nøgleordene er knyttet til betingelserne med en logisk operator, der ligner funktionaliteten i forhold til **operatoren OG** . Her er et eksempel på søgeforespørgslen (vises i ruden Detaljer), der resulterer, når du bruger nøgleordslisten og en betingelse.

    ![Eksempel på den forespørgsel, der oprettes ved brug af nøgleordslisten og en betingelse.](../media/b463750c-57fa-4602-9fed-0d5a420db3ad.png)

- Når du kører en indholdssøgning, kontrollerer Microsoft 365 automatisk din søgeforespørgsel for ikke-understøttede tegn og for booleske operatorer, der muligvis ikke kan have store bogstaver. Ikke-understøttede tegn er ofte skjulte og medfører typisk en søgefejl eller returnerer utilsigtede resultater. Du kan finde flere oplysninger om de ikke-understøttede tegn, der er markeret, [under Kontrollere din indholdssøgningsforespørgsel for fejl](check-your-content-search-query-for-errors.md).

- Hvis du har en søgeforespørgsel, der indeholder nøgleord for **ikke-engelske** tegn (f.eks. kinesiske tegn), kan du klikke på ikonet Forespørgselssprog-land/områdeForespørgselssprog-land![/område i Indholdssøgning.](../media/8d4b60c8-e1f1-40f9-88ae-ee2a7eca0886.png) og vælg en sprog-land-kulturkodeværdi for søgningen. Standardsproget/området er neutralt. Hvordan kan du se, om du har brug for at ændre sprogindstillingen for en indholdssøgning? Hvis du er sikker på, at indholdsplaceringer indeholder de ikke-engelske tegn, du søger efter, men søgningen ikke returnerer nogen resultater, kan sprogindstillingen være årsagen.

## <a name="partially-indexed-items"></a>Delvist indekserede elementer

- Delvist indekserede elementer i postkasser medtages i de anslåede søgeresultater. Delvist indekserede elementer fra SharePoint OneDrive ikke medtages i de anslåede søgeresultater. Få mere at vide under [Delvist indekserede elementer i eDiscovery](partially-indexed-items-in-content-search.md).

## <a name="searching-onedrive-accounts"></a>Søgning OneDrive konti

- Hvis du vil indsamle en liste over URL-adresser OneDrive websteder i organisationen, skal du se Oprette en liste [OneDrive alle placeringer i organisationen](/onedrive/list-onedrive-urls). Dette script i denne artikel opretter en tekstfil, der indeholder en liste over alle OneDrive websteder. For at køre dette script skal du installere og bruge SharePoint Online Management Shell. Sørg for at føje URL-adressen til organisationens domæne for Mit websted til hver af de OneDrive, du vil søge efter. Dette er det domæne, der indeholder alle dine OneDrive, f.eks. `https://contoso-my.sharepoint.com`. Her er et eksempel på en URL-adresse til en brugers websted OneDrive: `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft.com`.

    I tilfælde af at en persons hovednavn (UPN) ændres, ændres URL-adressen for brugerens placering OneDrive at inkorporere det nye UPN. Hvis dette sker, skal du redigere en indholdssøgning ved at tilføje brugerens nye webadresse OneDrive fjerne den gamle. Du kan finde flere oplysninger [under Sådan påvirker UPN OneDrive URL-adressen](/onedrive/upn-changes).

## <a name="searching-microsoft-teams-and-microsoft-365-groups"></a>Søgning Microsoft Teams og Microsoft 365 grupper

Du kan søge i den postkasse, der er knyttet til et Microsoft Team eller Microsoft 365 Gruppe. Da Microsoft Teams er bygget på Microsoft 365 grupper, minder søgning om dem. I begge tilfælde er det kun gruppen eller teampostkassen, der søges i. Der søges ikke i gruppens eller teammedlemmers postkasser. Hvis du vil søge efter dem, skal du føje dem til søgningen.

Husk følgende, når du søger efter indhold i Microsoft Teams og Microsoft 365 Grupper.

- Hvis du vil søge efter indhold, der er placeret i Teams og Microsoft 365 Grupper, skal du angive den postkasse og det SharePoint-websted, der er knyttet til et team eller en gruppe.

- Indhold fra private kanaler gemmes i hver brugers postkasse, ikke i teampostkassen. Hvis du vil søge efter indhold i private kanaler, skal [du se eDiscovery af private og delte kanaler](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

- Kør **cmdlet'en Get-UnifiedGroup** i Exchange Online for at få vist egenskaber for et team eller en Microsoft 365 gruppe. Dette er en god måde at hente URL-adressen til det websted, der er knyttet til et team eller en gruppe. Eksempelvis viser følgende kommando de valgte egenskaber for en gruppe Microsoft 365 seniorledelse:

  ```text
  Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
  DisplayName            : Senior Leadership Team
  Alias                  : seniorleadershipteam
  PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
  SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
  ```

    > [!NOTE]
    > For at køre cmdlet'en **Get-UnifiedGroup** skal du være tildelt rollen View-Only Modtagere i Exchange Online eller være medlem af en rollegruppe, der er tildelt rollen View-Only Modtagere.

- Når der søges i en brugers postkasse, søges der ikke i teams eller Microsoft 365 grupper, som brugeren er medlem af. På samme måde gælder det, at når du søger efter et team eller Microsoft 365 gruppe, søges der kun i den gruppepostkasse og det gruppewebsted, du angiver. Der søges ikke i OneDrive for Business postkasser og konti for gruppemedlemmer, medmindre du eksplicit føjer dem til søgningen.

- Hvis du vil have en liste over medlemmer af et team eller en Microsoft 365-gruppe,  \> kan du få vist egenskaberne på siden Startsidegrupper i Microsoft 365 Administration.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a> Alternativt kan du køre følgende kommando i Exchange Online PowerShell:

  ```powershell
  Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
  ```

    > [!NOTE]
    > For at køre cmdlet'en **Get-UnifiedGroupLinks** skal du være tildelt rollen View-Only-modtagere i Exchange Online eller være medlem af en rollegruppe, der er tildelt rollen View-Only Modtagere.

- Samtaler, der er en del af Teams kanal, gemmes i den postkasse, der er knyttet til teamet. Ligeledes gemmes filer, som teammedlemmer deler i en kanal, på teamets websted SharePoint webstedet. Derfor skal du tilføje teampostkassen og teamwebstedet SharePoint en indholdsplacering for at søge i samtaler og filer i en kanal.

- Alternativt gemmes samtaler, der er en del af chatlisten i Teams, i Exchange Online for de brugere, der deltager i chatten. Og filer, som en bruger deler i chatsamtaler, gemmes i OneDrive for Business for den bruger, der deler filen. Derfor skal du tilføje de enkelte brugerpostkasser og OneDrive for Business konti som indholdsplaceringer for at søge i samtaler og filer på chatlisten.

    > [!NOTE]
    > I en Exchange-hybridinstallation kan brugere med en lokal postkasse deltage i samtaler, der er en del af chatlisten i Teams. I dette tilfælde kan der også søges i indhold fra disse samtaler, fordi det gemmes i et skybaseret lagringsområde (kaldet en skybaseret postkasse *for* lokale brugere) for brugere, der har en lokal postkasse. Du kan finde flere [oplysninger i Teams oplysninger om chatsamtaler for lokale brugere](search-cloud-based-mailboxes-for-on-premises-users.md).

- Alle teams eller teamkanaler indeholder en Wiki til notetagning og samarbejde. Wiki-indholdet gemmes automatisk i en fil med .mht-format. Denne fil er gemt i Teams wikidatadokumentbiblioteket på teamets websted SharePoint websted. Du kan bruge værktøjet Indholdssøgning til at søge i wikien ved at angive teamets websted SharePoint som den indholdsplacering, der skal søges efter.

    > [!NOTE]
    > Muligheden for at søge på Wiki efter et team eller en kanal (når du søger på teamets websted SharePoint) blev udgivet d. 22. juni 2017. Der kan søges i wiki-sider, der er gemt eller opdateret på denne dato eller efter. Wikisider, der sidst er gemt eller opdateret før denne dato, er ikke tilgængelige til søgning.

- Oversigtsoplysninger om møder og opkald i en Teams kanal gemmes også i postkasserne for brugere, der ringede til mødet eller opkaldet. Det betyder, at du kan bruge indholdssøgning til at søge i disse oversigtsposter. Oversigtsoplysninger omfatter:

  - Dato, start- og sluttidspunktet og varigheden af et møde eller et opkald

  - Dato og klokkeslæt for, hvornår hver deltager har tilsluttet sig eller har forladt mødet eller opkaldet

  - Opkald sendt til telefonsvarer

  - Mistede eller ubesvarede opkald

  - Opkaldsoverførsler, der er repræsenteret som to separate opkald

  Det kan tage op til 8 timer, før der kan søges i poster med oversigt over møder og opkald.

  I søgeresultaterne identificeres mødeoversigter som Møder i feltet  **Type**, og oversigter over opkald identificeres som **Opkald**. Samtaler, der er en del af en Teams-kanal og 1xN-chatsamtaler, identificeres også **som chat i** **feltet Type**.

  ![Teams møder, opkald og 1xN-chats identificeres i feltet Type.](../media/O365-ContentSearch-Teams-MessageKind.png)

   Få mere at vide under [Microsoft Teams eDiscovery til opkald og møder](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-launches-ediscovery-for-calling-and-meetings/ba-p/210947).

- Kortindhold, der genereres af apps i Teams-kanaler, 1:1-chats og 1xN-chats, gemmes i postkasser og kan søges i. Et *kort* er en brugergrænsefladebeholder til korte dele af indholdet. Kort kan have flere egenskaber og vedhæftede filer og kan indeholde knapper, der kan udløse korthandlinger. Du kan finde flere oplysninger under [Kort](/microsoftteams/platform/task-modules-and-cards/what-are-cards)

  Ligesom andre Teams indhold, hvor kortindhold lagres, er det baseret på, hvor kortet blev brugt. Indhold til kort, der bruges Teams en anden kanal, gemmes i Teams gruppepostkassen. Kortindhold til 1:1- og 1xN-chats gemmes i chatdeltagernes postkasser.

  Hvis du vil søge efter kortindhold, kan du bruge `kind:microsoftteams` betingelserne eller `itemclass:IPM.SkypeTeams.Message` søgekriterier. Når du gennemser søgeresultater, har kortindhold genereret af botter i en Teams-kanal mailegenskaben **Afsender/**`<appname>@teams.microsoft.com`Forfatter som , `appname` hvor er navnet på den app, der genererede kortets indhold. Hvis kortindhold blev genereret af en bruger, **identificerer værdien** af Afsender/forfatter brugeren.

  Når du får vist kortindhold i søgeresultater for indhold, vises indholdet som en vedhæftet fil i meddelelsen. Den vedhæftede fil hedder `appname.html`, hvor `appname` er navnet på den app, der genererede kortindholdet. Følgende skærmbilleder viser, hvordan kortindhold (for en app med navnet Asana) vises i Teams i resultaterne af en søgning.

  **Kortindhold i Teams**

  ![Kortindhold i Teams kanalmeddelelse.](../media/CardContentTeams.png)

  **Kortindhold i søgeresultater**

  ![Samme kortindhold i resultaterne af en indholdssøgning.](../media/CardContentEdiscoverySearchResults.png)

  > [!NOTE]
  > Hvis du vil have vist billeder fra kortindhold i søgeresultater på nuværende tidspunkt (f.eks. markeringerne i det forrige skærmbillede), skal du være logget på Teams (under en anden fane i samme browsersession, som du bruger til at https://teams.microsoft.com) få vist søgeresultaterne. Ellers vises billedpladsholdere.

- Du kan bruge egenskaben **Type mail** eller **søgebetingelsesbetingelse for** Meddelelsestype til at søge specifikt efter indhold Teams.

  - Hvis du vil bruge **egenskaben Type** som en del af søgeordssøgningsforespørgslen, **skal** du skrive i feltet Nøgleord i en søgeforespørgsel `kind:microsoftteams`.

    ![Brug type:microsoftteams i feltet Nøgleord.](../media/O365-ContentSearch-Teams-Keywords.png)

  - Hvis du vil bruge en søgebetingelse, skal **du tilføje betingelsen** Meddelelsesbetingelse og bruge værdien `microsoftteams`.

    ![Brug betingelsen Meddelelses type med værdien microsoftteams.](../media/O365-ContentSearch-Teams-MessageKindCondition.png)

   Betingelser er logisk forbundet med nøgleordsforespørgslen af **operatoren AND** . Det betyder, at et element skal svare til både nøgleordsforespørgslen og den søgebetingelse, der skal returneres i søgeresultaterne. Du kan finde flere oplysninger i afsnittet "Retningslinjer for brug af betingelser" i [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning.](keyword-queries-and-search-conditions.md#guidelines-for-using-conditions)

## <a name="searching-yammer-groups"></a>Søgning Yammer grupper

Du kan bruge **mailegenskaben ItemClass** eller søgebetingelsestypen **Type** til at søge specifikt efter samtaleelementer Yammer Grupper.

  - Hvis du vil bruge **egenskaben Elementklasse** som en del af søgeordssøgningsforespørgslen, kan du i feltet Nøgleord i en søgeforespørgsel skrive et (eller alle) af følgende egenskab:værdipar:

     - ItemClass:IPM.Yammer.message
     - ItemClass:IPM.Yammer.poll
     - ItemClass:IPM.Yammer.praise
     - ItemClass:IPM.Yammer.question

    Du kan f.eks. bruge følgende søgeforespørgsel til at returnere Yammer og Yammer ros elementer:

    ![Brug egenskaben ItemClass til at søge efter Yammer elementer.](../media/YammerContentSearch1.png)

  - Alternativt kan du bruge betingelsen **Skriv mail** og vælge at Yammer **for** at returnere Yammer elementer. Den følgende søgeforespørgsel returnerer f.eks. Yammer alle samtaleelementer, der indeholder nøgleordet "fortroligt".

    ![Brug betingelseskortet Type til at søge efter Yammer samtaleelementer.](../media/YammerContentSearch2.png)

## <a name="searching-inactive-mailboxes"></a>Søgning i inaktive postkasser

Du kan søge i inaktive postkasser i en indholdssøgning. Hvis du vil have en liste over de inaktive postkasser i organisationen, skal du køre kommandoen `Get-Mailbox -InactiveMailboxOnly` i Exchange Online PowerShell. Alternativt kan du gå  \> til Opbevaring af oplysninger i Security & Compliance Center og derefter klikke på ellipserne på **MoreNavigation**![ Bar.](../media/9723029d-e5cd-4740-b5b1-2806e4f28208.gif) \>**Inaktive postkasser**.

Her er nogle ting, du skal huske på, når du søger i inaktive postkasser.

- Hvis en eksisterende indholdssøgning omfatter en brugerpostkasse, og den pågældende postkasse gøres inaktiv, fortsætter indholdssøgningen med at søge i den inaktive postkasse, når du kører søgningen igen, efter at den bliver inaktiv.

- Nogle gange kan en bruger have en aktiv postkasse og en inaktiv postkasse, der har samme SMTP-adresse. I dette tilfælde søges der kun i den specifikke postkasse, som du vælger som en placering til en indholdssøgning. Med andre ord, hvis du føjer en brugers postkasse til en søgning, kan du ikke antage, at der søges i både deres aktive og inaktive postkasser. Der søges kun i den postkasse, du eksplicit føjer til søgningen.

- Du kan bruge Security & Compliance Center PowerShell til at oprette en indholdssøgning for at søge i en inaktiv postkasse. Hvis du vil gøre dette, skal du tilføje et punktum på forhånd ( . ) til mailadressen på den inaktive postkasse. Eksempelvis opretter følgende kommando en indholdssøgning, der søger i en inaktiv postkasse med mailadressen pavelb@contoso.onmicrosoft.com:

   ```powershell
   New-ComplianceSearch -Name InactiveMailboxSearch -ExchangeLocation .pavelb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true
   ```

- Vi anbefaler på det kraftigste, at du undgår at have en aktiv postkasse og en inaktiv postkasse med den samme SMTP-adresse. Hvis du har brug for at genbruge SMTP-adressen, der er tildelt en inaktiv postkasse, anbefaler vi, at du gendanner den inaktive postkasse eller gendanner indholdet i en inaktiv postkasse til en aktiv postkasse (eller arkivet for en aktiv postkasse) og derefter sletter den inaktive postkasse. Du kan finde flere oplysninger i et af følgende emner:

  - [Gendan en inaktiv postkasse i Office 365](recover-an-inactive-mailbox.md)

  - [Gendan en inaktiv postkasse i Office 365](restore-an-inactive-mailbox.md)

  - [Slet en inaktiv postkasse i Office 365](delete-an-inactive-mailbox.md)

## <a name="searching-disconnected-or-de-licensed-mailboxes"></a>Søgning i frakoblede eller licenserede postkasser

Hvis Exchange Online licensen (eller hele Microsoft 365-licensen) fjernes fra en brugerkonto eller i Azure Active Directory, bliver brugerens postkasse til en *afbrudt postkasse.* Det betyder, at postkassen ikke længere er knyttet til brugerkontoen. Her er, hvad der sker, når du søger i frakoblede postkasser:

- Hvis licensen fjernes fra en postkasse, er postkassen ikke længere søgbar.

- Hvis en eksisterende indholdssøgning omfatter en postkasse, hvor licensen fjernes, returneres der ingen søgeresultater fra den frakoblede postkasse, hvis du kører indholdssøgningen igen.

- Hvis du bruger **cmdlet'en New-ComplianceSearch** til at oprette en indholdssøgning og angiver en afbrudt postkasse som Exchange-indholdsplaceringen til søgning, returnerer indholdssøgningen ikke nogen søgeresultater fra den frakoblede postkasse.

Hvis du har brug for at bevare dataene i en afbrudt postkasse, så der kan søges i den, skal du placere en venteposition i postkassen, før du fjerner licensen. Dette bevarer dataene og holder den frakoblede postkasse søgbar, indtil ventepositionen fjernes. Du kan finde flere oplysninger om [ventepositioner under Sådan identificeres den type venteposition, der er sat på Exchange Online postkasse](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="searching-for-content-in-a-sharepoint-multi-geo-environment"></a>Søge efter indhold i et SharePoint Multi-Geo miljø

Hvis det er nødvendigt, at en eDiscovery-leder søger efter indhold i SharePoint og OneDrive i forskellige områder i et [SharePoint-multi-geo-miljø](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md), skal du gøre følgende for at få det til at ske:

1. Opret en separat brugerkonto til hver satellits geoplacering, som eDiscovery-chefen skal søge efter. Hvis du vil søge efter indhold på websteder i den pågældende geoplacering, skal eDiscovery-chefen logge på den konto, du har oprettet for den pågældende placering, og derefter køre en indholdssøgning.

2. Opret et søgetilladelsesfilter for hver satellits geoplacering (og tilsvarende brugerkonto), som eDiscovery-lederen skal søge efter. Hver af disse søgetilladelser begrænser omfanget af indholdssøgning til en bestemt geoplacering, når eDiscovery-chefen er logget på den brugerkonto, der er knyttet til den pågældende placering.

> [!TIP]
> Du behøver ikke at bruge denne strategi, når du bruger søgeværktøjet [i Advanced eDiscovery](overview-ediscovery-20.md). Det skyldes, at der søges i alle datacentre, når du SharePoint på websteder og OneDrive konti Advanced eDiscovery. Du skal kun bruge denne strategi for områdespecifikke brugerkonti, og søgetilladelser filtreres, når du bruger værktøjet Indholdssøgning og kører søgninger, der er knyttet til [eDiscovery-sager](./get-started-core-ediscovery.md).

Lad os f.eks. sige, at en eDiscovery-leder skal søge efter SharePoint- og OneDrive-indhold på satellitplaceringer i Nordamerika, Europa og Asien/Stillehavsområdet. Det første trin er at oprette tre brugerkonti, én for hver placering. Det næste trin er at oprette tre søgetilladelsesfiltre: ét for hver *placering og* en tilsvarende brugerkonto. Her er eksempler på de tre søgetilladelsesfiltre for dette scenarie. I hvert af disse eksempler angiver **området** SharePoint datacenterplaceringen for den pågældende geo, og **Users-parameteren** angiver den tilsvarende brugerkonto.

**Nordamerika**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-NAM" -Users ediscovery-nam@contoso.com -Region NAM -Action ALL
```

**Europa**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-EUR" -Users ediscovery-eur@contoso.com -Region EUR -Action ALL
```

**Asien/Stillehavsområdet**

```powershell
New-ComplianceSecurityFilter -FilterName "SPMultiGeo-APC" -Users ediscovery-apc@contoso.com -Region APC -Action ALL
```

Husk følgende, når du bruger søgetilladelsesfiltre til at søge efter indhold i multi-geo-miljøer:

- **Områdeparameteren** leder søgninger til den angivne satellitplacering. Hvis en eDiscovery-leder kun SharePoint og OneDrive websteder uden for det område, der er angivet i filteret for søgetilladelser, returneres der ingen søgeresultater.

- **Parameteren** Område styrer ikke søgninger i Exchange postkasser. Der søges i alle datacentre, når du søger i postkasser.

Du kan finde flere oplysninger om brug af søgetilladelsesfiltre i et multi-geo-miljø i afsnittet "Søgning og eksport af indhold i Multi-Geo-miljøer" i Konfigurere [overholdelsesgrænser for eDiscovery-undersøgelser](set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).
