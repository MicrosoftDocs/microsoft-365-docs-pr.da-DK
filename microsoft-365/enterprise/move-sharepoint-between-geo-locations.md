---
title: Flyt et SharePoint-websted til en anden geografisk placering
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
description: Få mere at vide om, hvordan du flytter et SharePoint-websted til en anden geografisk placering i dit multi-geo-miljø og kommunikerer forventningerne til ændringerne til dine brugere.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0b388b3fa869e6207c72f62aa2f50b832acab43a
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940816"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>Flyt et SharePoint-websted til en anden geografisk placering

Med Geo-flytning af SharePoint-websted kan du flytte SharePoint-websteder til andre geografiske placeringer i dit multi-geo-miljø.

Følgende webstedstyper kan flyttes mellem geografiske placeringer:

- Gruppetilsluttede Microsoft 365-websteder, herunder de websteder, der er knyttet til Microsoft Teams
- Moderne websteder uden en Microsoft 365-gruppetilknytning
- Klassiske SharePoint-websteder
- Kommunikationswebsteder

Du skal være global administrator eller SharePoint-administrator for at flytte et websted mellem geografiske placeringer.

Der er et skrivebeskyttet vindue under den geografiske flytning af SharePoint-webstedet på ca. 4-6 timer, afhængigt af webstedets indhold.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

- Prøv at flytte et SharePoint-websted på et testwebsted for at blive fortrolig med proceduren.
- Valider, om webstedet kan flyttes før planlægning eller udførelse af flytningen.
- Når det er muligt, flyttes websteder på tværs af geografiske områder uden for arbejdstiden for at reducere brugerpåvirkningen.
- Kommuniker med berørte brugere, før webstederne flyttes.

## <a name="communicating-to-your-users"></a>Kommunikation med dine brugere

Når du flytter SharePoint-websteder mellem geografiske placeringer, er det vigtigt at kommunikere med brugerne af webstederne (generelt alle med mulighed for at redigere webstedet), hvad de kan forvente. Dette kan hjælpe med at reducere bruger forvirring og opkald til din helpdesk. Send dine websteders brugere en mail før flytningen, og giv dem følgende oplysninger:

- Når flytningen forventes at starte, og hvor lang tid det forventes at tage
- Hvilken geografisk placering deres websted flyttes til, og URL-adressen for at få adgang til den nye placering
- De bør lukke deres filer og ikke foretage ændringer under flytningen.
- Filtilladelser og deling ændres ikke på grund af flytningen.
- Hvad kan man forvente af brugeroplevelsen i et multi-geo-miljø?

Sørg for at sende brugerne af dine websteder en mail, når flytningen er fuldført, og informere dem om, at de kan fortsætte med at arbejde på deres websteder.

## <a name="scheduling-sharepoint-site-moves"></a>Flytning af SharePoint-websted i planlægning

Du kan planlægge flytninger af SharePoint-webstedet på forhånd (beskrevet senere i denne artikel). Du kan planlægge flytninger på følgende måde:

- Du kan planlægge op til 4.000 flytninger ad gangen.
- Når flytningerne begynder, kan du planlægge mere med maksimalt 4.000 ventende flytninger i køen og en given tid.
- Den maksimale størrelse på et SharePoint-websted, der kan flyttes, er 1 terabyte (1 TB).

Hvis du vil planlægge en geografisk flytning af et SharePoint-websted et senere tidspunkt, skal du inkludere en af følgende parametre, når du starter flytningen:

- `PreferredMoveBeginDate` – Flytningen vil sandsynligvis begynde på dette angivne tidspunkt.
- `PreferredMoveEndDate` – Flytningen vil sandsynligvis være fuldført på dette angivne tidspunkt efter bedste evne.

Tid skal angives i UTC (Coordinated Universal Time) for begge parametre.

## <a name="moving-the-site"></a>Flytter webstedet

Geoflytning af SharePoint-websted kræver, at du opretter forbindelse og udfører flytningen fra URL-adressen til SharePoint-administratorer på den geografiske placering, hvor webstedet er.

Hvis webstedets URL-adresse f.eks. er `https://contosohealthcare.sharepoint.com/sites/Turbines`, skal du oprette forbindelse til URL-adressen til SharePoint-administratoren på `https://contosohealthcare-admin.sharepoint.com`:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![SharePoint Online Management Shell-vindue, der viser kommandoen Connect-SPOService.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>Validering af miljøet

Vi anbefaler, at du udfører en validering, før du planlægger flytning af et websted, for at sikre, at webstedet kan flyttes.

Vi understøtter ikke flytning af websteder med:

- Business Connectivity Services
- InfoPath-formularer
- IRM-skabeloner (Information Rights Management) er anvendt

Kør for at sikre, `Get-SPOGeoMoveCrossCompatibilityStatus`at alle geografiske placeringer er kompatible. Dette viser alle dine geografiske placeringer, og om miljøet er kompatibelt med destinationens geografiske placering.

Hvis du vil udføre en kontrol, der kun består af validering, på dit websted, skal du bruge `Start-SPOSiteContentMove` parameteren `-ValidationOnly` til at validere, om webstedet kan flyttes. Eksempel:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Dette returnerer *Udført* , hvis webstedet er klar til at blive flyttet, eller *Mislykket* , hvis nogle af blokerede betingelser er til stede.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>Start en geografisk flytning af et SharePoint-websted for et websted uden en tilknyttet Microsoft 365-gruppe

Den oprindelige URL-adresse for webstedet ændres som standard til URL-adressen for den geografiske placering for destinationen. Eksempel:

`https://Contoso.sharepoint.com/sites/projectx` Til `https://ContosoEUR.sharepoint.com/sites/projectx`

For websteder uden microsoft 365-gruppetilknytning kan du også omdøbe webstedet ved hjælp `-DestinationUrl` af parameteren . Eksempel:

<https://Contoso.sharepoint.com/sites/projectx> Til `https://ContosoEUR.sharepoint.com/sites/projecty`

Hvis du vil starte flytningen af webstedet, skal du køre:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![Skærmbillede af PowerShell-vinduet, der viser Start-SPOSiteContentMove cmdlet.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>Start en geografisk flytning af et SharePoint-websted for et Microsoft 365-gruppeforbundet websted

Hvis du vil flytte et Microsoft 365-gruppeforbundet websted, skal den globale administrator eller SharePoint-administratoren først ændre attributten Foretrukket dataplacering (PDL) for Microsoft 365-gruppen.

Sådan angiver du PDL for en Microsoft 365-gruppe:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

Når du har opdateret PDL,kan du starte flytningen af webstedet:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>Annuller en geografisk flytning af et SharePoint-websted

Du kan stoppe en geografisk flytning af et SharePoint-websted, forudsat at flytningen ikke er i gang eller er fuldført ved hjælp af cmdlet'en `Stop-SPOSiteContentMove` .

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>Fastlæggelse af status for en geografisk flytning af et SharePoint-websted

Du kan bestemme status for et websted, der flyttes ind fra det geografiske område, som du har forbindelse til, ved hjælp af følgende cmdlet'er:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (websteder, der ikke er forbundet med gruppe)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (gruppetilsluttede websteder)

`-SourceSiteUrl` Brug parameteren til at angive det websted, du vil have vist flyttestatus for.

Flyttestatusserne er beskrevet i følgende tabel.

****

|Status|Beskrivelse|
|---|---|
|Klar til udløser|Flytningen er ikke startet.|
|Planlagt|Flytningen er i kø, men er endnu ikke startet.|
|Indgående data (n/4)|Flytningen er i gang i en af følgende tilstande: Validering (1/4), Sikkerhedskopiér (2/4), Gendan (3/4), Oprydning (4/4).|
|Succes|Flytningen er fuldført.|
|Mislykkedes|Flytningen mislykkedes.|
|

Du kan også anvende indstillingen `-Verbose` for at få vist flere oplysninger om flytningen.

## <a name="user-experience"></a>Brugeroplevelse

Webstedsbrugere bør bemærke minimal afbrydelse, når deres websted flyttes til en anden geografisk placering. Ud over en kort skrivebeskyttet tilstand under flytningen vil eksisterende links og tilladelser fortsat fungere som forventet, når flytningen er fuldført.

### <a name="site"></a>Websted

Mens flytningen er i gang, er webstedet angivet til skrivebeskyttet. Når flytningen er fuldført, dirigeres brugeren til det nye websted på den nye geografiske placering, når vedkommende klikker på bogmærker eller andre links til webstedet.

### <a name="permissions"></a>Tilladelser

Brugere med tilladelser til webstedet vil fortsat have adgang til webstedet under flytningen, og når det er fuldført.

### <a name="sync-app"></a>Synkroniser app

Synkroniseringsappen registrerer automatisk og overfører automatisk synkronisering til den nye webstedsplacering, når flytningen af webstedet er fuldført. Brugeren behøver ikke at logge på igen eller udføre andre handlinger. (Version 17.3.6943.0625 eller nyere af synkroniseringsappen er påkrævet).

Hvis en bruger opdaterer en fil, mens flytningen er i gang, giver synkroniseringsappen dem besked om, at filoverførsler venter, mens flytningen er i gang.

### <a name="sharing-links"></a>Deling af links

Når flytningen af det geografiske SharePoint-websted er fuldført, omdirigerer de eksisterende delte links for de filer, der blev flyttet, automatisk til den nye geografiske placering.

### <a name="most-recently-used-files-in-office-mru"></a>Senest anvendte filer i Office (MRU)

MRU-tjenesten opdateres med URL-adressen til webstedet og url-adresserne til dets indhold, når flytningen er fuldført. Dette gælder for Word, Excel og PowerPoint.

### <a name="onenote-experience"></a>OneNote-oplevelse

OneNote win32-klient- og UWP-app (Universal) registrerer automatisk og synkroniserer automatisk notesbøger til den nye webstedsplacering, når flytningen af webstedet er fuldført. Brugeren behøver ikke at logge på igen eller udføre andre handlinger. Den eneste synlige indikator for brugeren er, at synkroniseringen af notesbogen mislykkes, når flytningen af webstedet er i gang. Denne oplevelse er tilgængelig i følgende OneNote-klientversioner:

- OneNote win32 – version 16.0.8326.2096 (og nyere)
- OneNote UWP – version 16.0.8431.1006 (og nyere)
- OneNote-mobilapp – version 16.0.8431.1011 (og nyere)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (gælder for websteder, der er forbundet med Microsoft 365-grupper)

Når flytningen af det geografiske SharePoint-websted er fuldført, har brugerne adgang til deres Microsoft 365-gruppewebstedsfiler i Teams-appen. Derudover vil filer, der deles via Teams-chat fra deres websted før geoflytning, fortsat fungere, når flytningen er fuldført.

Geoflytning af SharePoint-websted understøtter ikke flytning af private kanaler fra ét geografisk område til et andet. Private kanaler forbliver i den oprindelige geo.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint-mobilapp (iOS/Android)

SharePoint-mobilappen er kompatibel på tværs af geografiske områder og kan registrere webstedets nye geoplacering.

### <a name="sharepoint-workflows"></a>SharePoint-arbejdsprocesser

SharePoint 2013-arbejdsprocesser skal publiceres igen, når webstedet er flyttet. SharePoint 2010-arbejdsprocesser bør fortsat fungere normalt.

### <a name="apps"></a>Apps

Hvis du flytter et websted med apps, skal du genindsætte appen på webstedets nye geoplacering, da appen og dens forbindelser muligvis ikke er tilgængelige på destinationens geografiske placering.

### <a name="flow"></a>Flow

I de fleste tilfælde fungerer flow fortsat, efter at et geografisk SharePoint-websted er flyttet. Vi anbefaler, at du tester dem, når flytningen er fuldført.

### <a name="power-apps"></a>Power Apps

Power Apps skal oprettes igen på destinationsplaceringen.

### <a name="data-movement-between-geo-locations"></a>Dataflytning mellem geografiske placeringer

SharePoint bruger Azure Blob Storage til indholdet, mens de metadata, der er knyttet til websteder og filer, gemmes i SharePoint. Når webstedet er flyttet fra dets geografiske kildeplacering til destinationens geografiske placering, flytter tjenesten også dets tilknyttede Blob Storage. Blob Storage flyttes inden for ca. 40 dage.
