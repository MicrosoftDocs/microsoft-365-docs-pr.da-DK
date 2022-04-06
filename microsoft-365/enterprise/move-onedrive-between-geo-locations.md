---
title: Flyt et OneDrive til en anden geoplacering
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Find oplysninger om at flytte OneDrive-websted til en anden geoplacering, herunder hvordan du planlægger flytning af websteder og kommunikerer forventninger til brugerne.
ms.openlocfilehash: f0a9e319d20c7b56701d776e85a0618ed30e5f78
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569595"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Flyt et OneDrive til en anden geoplacering

Med OneDrive geografiske flytning kan du flytte en brugers OneDrive til en anden geoplacering. OneDrive geo-flytning udføres af SharePoint Online-administratoren eller Microsoft 365 globale administrator. Før du starter et OneDrive geo-flytning, skal du sørge for at give besked til den bruger, hvis OneDrive flyttes, og anbefale, at de lukker alle filer under flytningen. (Hvis brugeren har et dokument åbent ved hjælp af Office-klienten under flytningen, skal dokumentet gemmes på den nye placering, når flytningen er fuldført). Flytningen kan planlægges til et senere tidspunkt, hvis det ønskes.

Den OneDrive tjeneste bruger Azure Blob Storage til at gemme indhold. Den Storage blob, der er knyttet til brugerens OneDrive, flyttes fra kilden til destinationens geoplacering inden for 40 dage efter OneDrive destinationen bliver tilgængelig for brugeren. Adgangen til brugerens OneDrive gendannes, så snart destinationen er OneDrive tilgængelig.

I OneDrive geo-flyttevindue (ca. 2-6 timer) er brugerens OneDrive indstillet til skrivebeskyttet. Brugeren kan stadig få adgang til deres filer via OneDrive-synkronisering appen eller deres OneDrive i SharePoint Online. Når OneDrive geografiske flytning er fuldført, bliver brugeren automatisk forbundet til sin OneDrive på destinationens geografiske placering, når brugeren navigerer til OneDrive i Microsoft 365-appstarteren. Synkroniseringsappen begynder automatisk at synkronisere fra den nye placering.

Fremgangsmåderne i denne artikel kræver, at [Microsoft Office SharePoint Online PowerShell-modul](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Kommunikere til dine brugere

Når du OneDrive mellem geografiske placeringer, er det vigtigt at kommunikere med dine brugere, hvad de kan forvente. Dette kan reducere brugerforvirring og opkald til din helpdesk. Send en mail til brugerne før flytningen, og giv dem følgende oplysninger:

- Når flytningen forventes at starte, og hvor lang tid det forventes at tage
- Hvilken geoplacering deres OneDrive flytter til, og URL-adressen for at få adgang til den nye placering
- De bør lukke deres filer og ikke foretage ændringer under flytningen.
- Filtilladelser og deling ændres ikke som følge af flytningen.
- Hvad kan du forvente fra [brugeroplevelsen i et multi-geo-miljø](multi-geo-user-experience.md)

Sørg for at sende brugerne en mail, når flytningen er fuldført, og du informerer dem om, at de kan genoptage deres OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Planlægning OneDrive flytning af websted

Du kan planlægge OneDrive flytte webstedet på forhånd (beskrevet senere i denne artikel). Vi anbefaler, at du starter med et lille antal brugere for at validere dine arbejdsprocesser og kommunikationsstrategier. Når du er blevet fortrolig med processen, kan du planlægge flytninger på følgende måde:

- Du kan planlægge op til 4.000 flytninger ad gangen.
- Når flytningen starter, kan du planlægge mere med maksimalt 4.000 ventende flytninger i køen og på et givet tidspunkt.
- Den maksimale størrelse på et OneDrive, der kan flyttes, er 1 terabyte (1 TB).

## <a name="moving-a-onedrive-site"></a>Flytning af OneDrive websted

For at udføre OneDrive geografiske flytning skal lejeradministratoren først angive brugerens foretrukne dataplacering (PDL) til den korrekte geoplacering. Når PDL'en er indstillet, skal du vente i mindst 24 timer på, at PDL-opdateringen synkroniseres på tværs af geoplaceringerne, før du starter OneDrive geografiske flytning.

Når du bruger geo-flyt-cmdlet'er, skal du oprette forbindelse til SPO-tjenesten på brugerens aktuelle OneDrive geografiske placering ved hjælp af følgende syntaks:

```powershell
Connect-SPOService -url https://<tenantName>-admin.sharepoint.com
```

Eksempel: Hvis du vil flytte OneDrive "Matt@contosoenergy.onmicrosoft.com", skal du oprette forbindelse til EUR SharePoint Administration, da brugerens OneDrive er på EUR's geoplacering:

```powershell
Connect-SPOService -url https://contosoenergyeur-admin.sharepoint.com
```

![Skærmbillede af PowerShell-vinduet, der viser forbindelsessposervice-cmdlet'en.](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Validering af miljøet

Før du starter et OneDrive geografisk flytning, anbefaler vi, at du validerer miljøet.

For at sikre at alle geoplaceringer er kompatible, skal du køre:

```powershell
Get-SPOGeoMoveCrossCompatibilityStatus
```

Du får vist en liste over dine geoplaceringer, og om indhold kan flyttes mellem, bliver angivet som "kompatibelt". Hvis kommandoen returnerer "Ikke kompatibel", skal du prøve at validere status på et senere tidspunkt.

Hvis en OneDrive indeholder et underordnet websted, kan det f.eks. ikke flyttes. Du kan bruge Start-SPOUserAndContentMove -ValidationOnly-parameteren til at validere, om OneDrive kan flyttes:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly
```

Dette returnerer Vellykket, hvis OneDrive er klar til at blive flyttet eller Mislykkes, hvis der er et retsligt venteposition eller underordnet websted, der vil forhindre flytningen. Når du har valideret, at OneDrive er klar til at blive flyttet, kan du starte flytningen.

## <a name="start-a-onedrive-geo-move"></a>Starte et OneDrive geografisk flytning

Start flytningen ved at køre:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>
```

Ved hjælp af disse parametre:

- _UserPrincipalName_ – UPN for den bruger, OneDrive flyttes til.
- _DestinationDataLocation_ – Geo-Location hvor OneDrive skal flyttes til. Dette skal være den samme som brugerens foretrukne dataplacering.

Hvis du f.eks. vil flytte OneDrive af matt@contosoenergy.onmicrosoft.com EUR til AUS, skal du køre:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS
```

![Skærmbillede af PowerShell-vinduet, der Start-SPOUserAndContentMove en cmdlet.](../media/move-onedrive-between-geo-locations-image2.png)

Hvis du vil planlægge en geo-flytning til et senere tidspunkt, skal du bruge en af følgende parametre:

- _PreferredMoveBeginDate_ – Flytningen starter sandsynligvis på dette angivne tidspunkt. Klokkeslæt skal angives i UTC (Coordinated Universal Time).
- _PreferredMoveEndDate_ – Flytningen vil sandsynligvis blive fuldført på dette angivne tidspunkt på grundlag af den bedste indsats. Klokkeslæt skal angives i UTC (Coordinated Universal Time).

## <a name="cancel-a-onedrive-geo-move"></a>Annullere et OneDrive geo-flytning

Du kan stoppe den geografiske flytning af en brugers OneDrive, hvis flytningen ikke er i gang eller fuldført ved hjælp af cmdlet'en:

```powershell
Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>
```

Hvor _UserPrincipalName_ er UPN for den bruger, hvis OneDrive flytter, du vil stoppe.

## <a name="determining-current-status"></a>Fastslå aktuel status

Du kan kontrollere status for et OneDrive geografisk flytning ind eller ud af den geo, du har forbindelse til, ved hjælp af Get-SPOUserAndContentMoveState-cmdlet'en.

Statusserne for flytningen er beskrevet i følgende tabel.

|Status|Beskrivelse|
|---|---|
|IkkeStartet|Flytningen er ikke startet|
|InProgress (*n*/4)|Flytningen er i gang i en af følgende tilstande: <ul><li>Validering (1/4)</li><li>Sikkerhedskopiering (2/4)</li><li>Gendan (3/4)</li><li>Oprydning (4/4)</li></ul>|
|Succes|Flytningen er fuldført.|
|Mislykkedes|Flytningen mislykkedes.|

For at finde status for en bestemt brugers flytning skal du bruge *parameteren UserPrincipalName* :

```powershell
Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>
```

For at finde status for alle flytninger ind eller ud af den geoplacering, du har forbindelse til, skal du bruge *MoveState-parameteren* med en af følgende værdier: NotStarted, InProgress, Success, Failed, All.

```powershell
Get-SPOUserAndContentMoveState -MoveState <value>
```

Du kan også tilføje *parameteren Detaljeret* for at få mere detaljerede beskrivelser af flyttetilstanden.

## <a name="user-experience"></a>Brugeroplevelse

Brugere af OneDrive bør opleve minimal afbrydelse, hvis deres OneDrive flyttes til en anden geoplacering. Ud over en kort skrivebeskyttet tilstand under flytningen vil eksisterende links og tilladelser fortsat fungere som forventet, når flytningen er fuldført.

### <a name="users-onedrive"></a>Brugers OneDrive

Mens flytningen er i gang, er brugerens OneDrive indstillet til skrivebeskyttet. Når flytningen er fuldført, dirigeres brugeren til sin OneDrive i den nye geoplacering, når brugeren navigerer til OneDrive Microsoft 365-appstarteren eller en webbrowser.

### <a name="permissions-on-onedrive-content"></a>Tilladelser til OneDrive indhold

Brugere med tilladelser til OneDrive indhold vil fortsat have adgang til indholdet under flytningen, og efter det er fuldført.

### <a name="onedrive-sync-app"></a>OneDrive-synkronisering app

Appen OneDrive-synkronisering automatisk registrere og problemfrit overføre synkronisering til den nye OneDrive placering, når den OneDrive geografiske flytning er fuldført. Brugeren behøver ikke at logge på igen eller gøre noget andet.  (Version 17.3.6943.0625 eller nyere af synkroniseringsappen påkrævet.)

Hvis en bruger opdaterer en fil, mens OneDrive geo-flytning er i gang, giver synkroniseringsappen dem besked om, at filoverførsler afventer, mens flytningen er i gang.

### <a name="sharing-links"></a>Deling af links

Når OneDrive fuldførelse af geo-flytning, omdirigeres de eksisterende delte links for de flyttede filer automatisk til den nye geoplacering.

### <a name="onenote-experience"></a>OneNote oplevelse

OneNote win32-klient- og UWP-appen (Universal) registrerer og synkroniserer automatisk notesbøger til den nye placering i OneDrive, når OneDrive geografiske flytning er fuldført. Brugeren behøver ikke at logge på igen eller gøre noget andet. Den eneste synlige indikator for brugeren er, at synkronisering af notesbøger mislykkes, når OneDrive geografiske flytning er i gang. Denne oplevelse er tilgængelig på følgende OneNote klientversioner:

- OneNote win32 – Version 16.0.8326.2096 (og nyere)
- OneNote UWP – Version 16.0.8431.1006 (og nyere)
- OneNote-mobilapp – Version 16.0.8431.1011 (og nyere)

### <a name="teams-app"></a>Teams app

Når OneDrive fuldførelse af geo-flytning, har brugerne adgang til deres OneDrive-filer på Teams-appen. Desuden vil filer, der deles via Teams chat fra deres OneDrive før geo flytning, fortsat fungere, når flytningen er fuldført.

### <a name="onedrive-mobile-app-ios"></a>OneDrive mobilapp (iOS)

Når OneDrive fuldførelse af geografiske flytninger, skal brugeren logge af og logge på igen på iOS-mobilappen for at synkronisere til den nye OneDrive placering.

### <a name="existing-followed-groups-and-sites"></a>Eksisterende fulgte grupper og websteder

Fulgte websteder og grupper vises på brugerens websteds OneDrive uanset brugerens geografiske placering. Websteder og grupper, der hostes på en anden geoplacering, åbnes i en separat fane.

### <a name="delve-geo-url-updates"></a>Delve-opdateringer til geo-URL-adressen

Brugerne vil først blive sendt til det Delve geo, der svarer til deres PDL, når deres OneDrive er blevet flyttet til det nye geo.
