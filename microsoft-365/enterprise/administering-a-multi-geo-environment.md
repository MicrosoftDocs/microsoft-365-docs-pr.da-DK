---
title: Administration af et multi-geo-miljø
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Administratorer kan få mere at vide om, hvordan de administrerer SharePoint og OneDrive tjenester i et multi-geo-miljø.
ms.openlocfilehash: 126b5de915fba7168b3895bbb05ccef6dcad749b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590312"
---
# <a name="administering-a-multi-geo-environment"></a>Administration af et multi-geo-miljø

Her er et kig på, hvordan Microsoft 365 fungerer i et multi-geo-miljø.

## <a name="administrator-experience"></a>Administratoroplevelse

Administration SharePoint har fanen <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**Geo-placeringer i venstre navigationsrude**</a>, der har et kort over geoplaceringer, hvor du kan få vist og administrere dine geoplaceringer. Brug denne side til at tilføje eller slette geoplaceringer for din lejer.

## <a name="audit-log-search"></a>Søgning i overvågningslogfil

En samlet [overvågningslog](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for alle dine satellitplaceringer er tilgængelig fra siden Microsoft 365 søgning i overvågningsloggen. Du kan se alle poster i overvågningsloggen på tværs af geografiske placeringer, f.eks. vil NAM & EUR-brugeres aktiviteter blive vist i én organisationsvisning, og derefter kan du anvende eksisterende filtre for at se bestemte brugeres aktiviteter.

> [!NOTE]
> Exchange administrator overvågningshændelser er kun tilgængelige for standardplaceringen.

## <a name="bcs-secure-store-apps"></a>BCS, Secure Store, Apps

BCS, Secure Store og Apps har alle separate forekomster i hver satellitplacering, derfor bør SharePoint Online-administratoren administrere og konfigurere disse tjenester separat fra hver satellitplacering.

## <a name="compliance-admin-center"></a>Center for overholdelse af regler og standarder

Der er ét centralt overholdelsescenter for en multi-geo-lejer: [Microsoft 365 Compliance Admin center](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>eDiscovery

Som standard vil en eDiscovery-leder eller administrator for en multi-geo-lejer kun kunne gennemføre eDiscovery på den pågældende lejers centrale placering. Den Office 365 globale administrator skal tildele eDiscovery Manager-tilladelser for at give andre tilladelse til at udføre eDiscovery og tildele et "Område"-parameter i deres gældende Overholdelsessikkerhedsfilter for at angive det område, hvor eDiscovery skal udføres som satellitplacering, ellers vil der ikke blive udført eDiscovery til satellitplaceringen. Hvis du vil konfigurere filteret til overholdelse af regler og standarder for et område, [skal Office 365 konfigurere Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Exchange postkasser

Brugernes Exchange flyttes automatisk, hvis deres PDL ændres. Når en ny postkasse oprettes, klargøres den til brugerens PDL eller til den centrale placering, hvis der ikke er angivet en værdi for brugerens PDL.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Politik til forebyggelse af datatab (DLP) i forbindelse med beskyttelse af oplysninger (IP)

Du kan angive dine IP DLP-politikker for OneDrive for Business, SharePoint og Exchange i Security and Compliance Center og angive politikker efter behov for hele lejeren eller for de relevante brugere. Eksempel: Hvis du vil vælge en politik for en bruger i en satellitplacering, skal du vælge at anvende politikken på et bestemt OneDrive og angive brugerens OneDrive URL-adresse. Se [Oversigt over politikker til forebyggelse af datatab](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for at få generel vejledning i oprettelse af DLP-politikker.

DLP-politikker synkroniseres automatisk baseret på deres anvendelighed for hver geoplacering.

Implementering af politikker til beskyttelse af oplysninger og forebyggelse af datatab for alle brugere i en geoplacering er ikke en mulighed i brugergrænsefladen, i stedet skal du vælge de relevante konti for politikken eller anvende politikken globalt på alle konti.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Power Apps oprettet til satellitplaceringen, vil bruge slutpunktet, der er placeret på lejerens centrale placering. Microsoft Power Apps ikke en multi-geo-tjeneste. 

## <a name="power-automate"></a>Power Automate

Flows, der oprettes til satellitplaceringen, vil bruge slutpunktet, der er placeret i lejerens standard-geoplacering.  Power Automate ikke en multi-geo-tjeneste. 

## <a name="sharepoint-storage-quota"></a>SharePoint lagerkvote

Som standard deler alle geoplaceringer i et multi-geo-miljø den tilgængelige lejers lagerkvote.  Du kan også administrere lagerkvoten ved at tildele en bestemt kvote for en bestemt geoplacering. Du kan finde flere oplysninger [SharePoint kvoter for lagerkvoter i multi-geo-miljøer](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Deling

Administratorer kan angive og administrere delingspolitikker for hver af deres placeringer. Den OneDrive og SharePoint websteder i hver geoplacering vil kun efterkomme de tilsvarende geo-specifikke indstillinger for deling. Du kan f.eks. tillade [ekstern deling](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for din centrale placering, men ikke for din satellitplacering eller omvendt. Bemærk, at delingsindstillingerne ikke tillader konfiguration af delingsbegrænsninger mellem geoplaceringer.

## <a name="stream"></a>Stream

Videoer, der er overført til Stream i en 1:1-chat, gemmes i OneDrive den person, der uploader. Mødeoptagelser gemmes i den OneDrive for hver deltager, der registrerer mødet.

## <a name="taxonomy"></a>Taksonomi

Vi understøtter en samlet [taksonomi](/sharepoint/managed-metadata) til virksomheds-administrerede metadata på tværs af geoplaceringer, hvor masteren hostes på den centrale placering for din virksomhed. Vi anbefaler, at du administrerer din globale taksonomi fra den centrale placering og kun føjer placeringsspecifikke udtryk til satellitplaceringens taksonomi. Globale taksonomivilkår synkroniseres med satellitplaceringerne.

Se [Administrer metadata i en multi-geo-lejer](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) for at få yderligere oplysninger og for at få udviklervejledning.

## <a name="user-profile-application"></a>Brugerprofilprogram

Der er et [brugerprofilprogram](/sharepoint/manage-user-profiles) i hver geoplacering. Hver brugers profiloplysninger hostes på deres geoplacering og er tilgængelige for administratoren for den pågældende geoplacering.

Hvis du har brugerdefinerede profilegenskaber, anbefaler vi, at du bruger det samme profilskema på tværs af geografiske områder og udfylder dine brugerdefinerede profilegenskaber enten i alle geoplaceringer eller efter behov. Du kan finde en vejledning til programmering af, hvordan du udfylder brugerprofildata i [API'en Massebrugerprofilopdatering](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Se [Arbejde med brugerprofiler i en multi-geo-lejer for at](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) få yderligere oplysninger og for at få udviklervejledning.

## <a name="yammer"></a>Yammer

Yammer er ikke en Multi-Geo-arbejdsbyrde. Yammer tråde, der er Yammer, anbringes på lejerens centrale placering. Yammer udruller en ændring i fillagring, som lagrer Yammer i SharePoint. Yammer filer, der er SharePoint i en SharePoint, anbringes det websted, der er knyttet Yammer gruppen. SharePoint gruppewebsteder er baseret på PDL-logik som beskrevet i [SharePoint websteder og grupper](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
