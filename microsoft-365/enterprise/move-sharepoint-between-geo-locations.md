---
title: Flyt et SharePoint-websted til en anden geoplacering
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Lær at flytte et SharePoint-websted til en anden geoplacering inden for dit multi-geo-miljø og kommunikere forventninger til ændringerne til dine brugere.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9e4132b8399cc69067d24af6c3c9ec8e3baf52bd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63591552"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>Flyt et SharePoint-websted til en anden geoplacering

Med SharePoint websteds geografiske flytning kan du flytte SharePoint til andre geoplaceringer inden for dit multi-geo-miljø.

Følgende typer af websteder kan flyttes mellem geografiske placeringer:

- Microsoft 365 gruppeforbundne websteder, herunder de websteder, der er knyttet til Microsoft Teams
- Moderne websteder uden en Microsoft 365 gruppesammenknytning
- Klassiske SharePoint websteder
- Kommunikationswebsteder

Du skal være global administrator eller SharePoint administrator for at kunne flytte et websted mellem geografiske placeringer.

Der er et skrivebeskyttet vindue under SharePoint webstedets geografiske flytning på ca. 4-6 timer, afhængigt af webstedsindhold.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

- Prøv et SharePoint et websted, der flyttes til et testwebsted, for at lære proceduren at kende.
- Valider, om webstedet kan flyttes, før du planlægger eller udfører flytningen.
- Når det er muligt, flyttes kryds geografiske websteder for uden for arbejdstiden for at reducere brugerpåvirkningen.
- Kommunikere med på påvirkede brugere før flytningen af webstederne.

## <a name="communicating-to-your-users"></a>Kommunikere til dine brugere

Når du SharePoint websteder mellem geoplaceringer, er det vigtigt at kommunikere til webstedsbrugerne (generelt alle med mulighed for at redigere webstedet), hvad du kan forvente. Dette kan reducere brugerforvirring og opkald til din helpdesk. Send en mail til brugerne af dine websteder før flytningen, og giv dem følgende oplysninger:

- Når flytningen forventes at starte, og hvor lang tid det forventes at tage
- Hvilken geoplacering deres websted flyttes til, og URL-adressen for at få adgang til den nye placering
- De bør lukke deres filer og ikke foretage ændringer under flytningen.
- Filtilladelser og deling ændres ikke på grund af flytningen.
- Hvad kan du forvente fra brugeroplevelsen i et multi-geo-miljø

Sørg for at sende brugerne af dine websteder en mail, når flytningen er fuldført, og du informerer dem om, at de kan genoptage arbejdet på deres websteder.

## <a name="scheduling-sharepoint-site-moves"></a>Planlægning SharePoint flytning af websted

Du kan planlægge SharePoint flytte webstedet på forhånd (beskrevet senere i denne artikel). Du kan planlægge flytninger på følgende måde:

- Du kan planlægge op til 4.000 flytninger ad gangen.
- Når flytningen starter, kan du planlægge mere med maksimalt 4.000 ventende flytninger i køen og på et givet tidspunkt.
- Den maksimale størrelse på SharePoint websted, der kan flyttes, er 1 terabyte (1 TB).

Hvis du vil planlægge SharePoint et websteds geografiske flytning på et senere tidspunkt, skal du medtage en af følgende parametre, når du starter flytningen:

- `PreferredMoveBeginDate` – Flytningen starter sandsynligvis på dette angivne tidspunkt.
- `PreferredMoveEndDate` – Flytningen vil sandsynligvis blive fuldført på dette angivne tidspunkt og kræver den bedste indsats.

Klokkeslæt skal angives i UTC (Coordinated Universal Time) for begge parametre.

## <a name="moving-the-site"></a>Flytning af webstedet

SharePoint webstedets geografiske flytning kræver, at du opretter forbindelse og udfører flytningen fra SharePoint-administrator-URL-adressen på den geoplacering, hvor webstedet er.

Hvis webstedets URL f.eks. er <https://contosohealthcare.sharepoint.com/sites/Turbines>, skal du oprette SharePoint administrator-URL-adressen på <https://contosohealthcare-admin.sharepoint.com>:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![SharePoint Online Management Shell, der viser Connect-SPOService kommando.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>Validering af miljøet

Vi anbefaler, at du udfører en validering for at sikre, at webstedet kan flyttes, før du planlægger en flytning af webstedet.

Vi understøtter ikke flytning af websteder med:

- Business Connectivity Services
- InfoPath-formularer
- IRM-skabeloner (Information Rights Management) er anvendt

For at sikre at alle geoplaceringer er kompatible, skal du køre `Get-SPOGeoMoveCrossCompatibilityStatus`. Dette viser alle dine geoplaceringer, og om miljøet er kompatibelt med destinationens geoplacering.

Hvis du vil udføre en kontrol, der kun gælder for validering, på dit websted, `Start-SPOSiteContentMove` `-ValidationOnly` skal du bruge parameteren til at validere, om webstedet kan flyttes. Eksempel:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Dette returnerer Vellykket *,* hvis webstedet er klar til at blive flyttet eller Mislykkes *,* hvis der findes nogen af blokerede betingelser.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>Starte et SharePoint websteds geografiske flytning for et websted uden nogen tilknyttet Microsoft 365 gruppe

Som standard ændres den indledende URL-adresse for webstedet til URL-adressen for destinationens geoplacering. Eksempel:

<https://Contoso.sharepoint.com/sites/projectx> til <https://ContosoEUR.sharepoint.com/sites/projectx>

For websteder uden Microsoft 365 gruppesammenknytning kan du også omdøbe webstedet ved hjælp af `-DestinationUrl` parameteren. Eksempel:

<https://Contoso.sharepoint.com/sites/projectx> til <https://ContosoEUR.sharepoint.com/sites/projecty>

Hvis du vil starte flytningen af webstedet, skal du køre:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![Skærmbillede af PowerShell-vinduet, der Start-SPOSiteContentMove en cmdlet.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>Starte et SharePoint websteds geografiske flytning for Microsoft 365 gruppeforbundet websted

Hvis du Microsoft 365 et gruppeforbundet websted, skal den globale administrator eller SharePoint-administratoren først ændre attributten Foretrukken dataplacering (PDL) for Microsoft 365 gruppe.

Sådan angives PDF-filen for Microsoft 365 gruppe:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

Når du har opdateret PDL'en, kan du starte flytningen af webstedet:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>Annullere et SharePoint webstedets geografiske flytning

Du kan stoppe en SharePoint webstedets geografiske flytning, hvis flytningen ikke er i gang eller fuldført ved hjælp af `Stop-SPOSiteContentMove` cmdlet'en.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>Fastslå status for et SharePoint websteds geografiske flytning

Du kan bestemme status for et websteds flytning ud af det geo, du har forbindelse til, ved hjælp af følgende cmdlet'er:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (ikke-Gruppeforbundne websteder)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (Group-connected sites)

Brug parameteren `-SourceSiteUrl` til at angive det websted, du vil have vist flyttestatus for.

Statusserne for flytningen er beskrevet i følgende tabel.

****

|Status|Beskrivelse|
|---|---|
|Klar til udløser|Flytningen er ikke startet.|
|Planlagt|Flytningen er i kø, men er endnu ikke startet.|
|InProgress (n/4)|Flytningen er i gang i en af følgende tilstande: Validering (1/4), Sikkerhedskopiering (2/4), Gendan (3/4), Oprydning (4/4).|
|Succes|Flytningen er fuldført.|
|Mislykkedes|Flytningen mislykkedes.|
|

Du kan også anvende indstillingen `-Verbose` for at få vist yderligere oplysninger om flytningen.

## <a name="user-experience"></a>Brugeroplevelse

Webstedets brugere bør opleve minimal afbrydelse, når deres websted flyttes til en anden geoplacering. Ud over en kort skrivebeskyttet tilstand under flytningen vil eksisterende links og tilladelser fortsat fungere som forventet, når flytningen er fuldført.

### <a name="site"></a>Websted

Mens flytningen er i gang, er webstedet indstillet til skrivebeskyttet. Når flytningen er fuldført, dirigeres brugeren til det nye websted i den nye geoplacering, når de klikker på bogmærker eller andre links til webstedet.

### <a name="permissions"></a>Tilladelser

Brugere med tilladelser til webstedet vil fortsat have adgang til webstedet under flytningen, og efter at det er fuldført.

### <a name="sync-app"></a>Synkroniser app

Synkroniseringsappen registrerer og overfører automatisk synkronisering til den nye webstedsplacering, når flytningen af webstedet er fuldført. Brugeren behøver ikke at logge på igen eller gøre noget andet. (Version 17.3.6943.0625 eller nyere af synkroniseringsappen påkrævet.)

Hvis en bruger opdaterer en fil, mens flytningen er i gang, giver synkroniseringsappen dem besked om, at filoverførsler afventer, mens flytningen er i gang.

### <a name="sharing-links"></a>Deling af links

Når webstedets SharePoint er fuldført, omdirigeres de eksisterende delte links for de filer, der er blevet flyttet, automatisk til den nye geoplacering.

### <a name="most-recently-used-files-in-office-mru"></a>Senest anvendte filer i Office (MRU)

MRU-tjenesten opdateres med webstedets URL-adresse og dets URL-adresser til indhold, når flytningen er fuldført. Dette gælder for Word, Excel og PowerPoint.

### <a name="onenote-experience"></a>OneNote oplevelse

OneNote win32-klienten og UWP-appen (Universal) registrerer og synkroniserer automatisk notesbøger til den nye placering på webstedet, når flytningen af webstedet er fuldført. Brugeren behøver ikke at logge på igen eller gøre noget andet. Den eneste synlige indikator for brugeren er synkronisering af notesbøger kunne ikke udføres, når flytningen af webstedet er i gang. Denne oplevelse er tilgængelig på følgende OneNote klientversioner:

- OneNote win32 – Version 16.0.8326.2096 (og nyere)
- OneNote UWP – Version 16.0.8431.1006 (og nyere)
- OneNote-mobilapp – Version 16.0.8431.1011 (og nyere)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (gældende for Microsoft 365 forbundne websteder)

Når webstedets SharePoint er fuldført, har brugerne adgang til deres Microsoft 365-gruppewebstedsfiler Teams appen. Desuden vil filer, der deles via Teams chat fra deres websted før geo-flytning, fortsat fungere, når flytningen er fuldført.

SharePoint webstedets geografiske flytning understøtter ikke flytning af private kanaler fra ét geo til et andet. Private kanaler forbliver i det oprindelige geo.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint mobilapp (iOS/Android)

Appen SharePoint-mobilappen er kryds geokompatibel og i stand til at registrere webstedets nye geoplacering.

### <a name="sharepoint-workflows"></a>SharePoint arbejdsprocesser

SharePoint 2013-arbejdsprocesser skal genudgives, efter webstedet er flyttet. SharePoint 2010-arbejdsprocesser bør fortsat fungere normalt.

### <a name="apps"></a>Apps

Hvis du flytter et websted med apps, skal du oprette appen igen i webstedets nye geoplacering som appen, og dens forbindelser er muligvis ikke tilgængelige på destinationens geoplacering.

### <a name="flow"></a>Flow

I de fleste tilfælde vil Flows fortsat fungere efter et SharePoint webstedets geografiske flytning. Vi anbefaler, at du tester dem, når flytningen er fuldført.

### <a name="power-apps"></a>Power Apps

Power Apps skal genskabes på destinationsplaceringen.

### <a name="data-movement-between-geo-locations"></a>Databevægelse mellem geoplaceringer

SharePoint azure Blob-lagerplads til indholdet, mens de metadata, der er knyttet til webstederne og dets filer, gemmes i SharePoint. Når webstedet er flyttet fra dets kilde geografiske placering til destinationens geografiske placering, flytter tjenesten også dens tilknyttede Blob-Storage. Blob Storage fuldføres om ca. 40 dage.
