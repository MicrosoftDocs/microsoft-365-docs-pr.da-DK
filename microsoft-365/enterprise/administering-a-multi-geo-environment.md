---
title: Administration af et multigeografisk miljø
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
ms.openlocfilehash: 155eea030cfa700a009805fb66aeb74eaae617d3
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949073"
---
# <a name="administering-a-multi-geo-environment"></a>Administration af et multigeografisk miljø

Her kan du se, hvordan Microsoft 365-tjenester fungerer i et multi-geo-miljø.

## <a name="administrator-experience"></a>Administratoroplevelse

SharePoint Administration har <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">fanen **Geo-placeringer i den venstre navigationsrude**</a>, der indeholder et kort over geografiske placeringer, hvor du kan få vist og administrere dine geografiske placeringer. Brug denne side til at tilføje eller slette geografiske placeringer for din lejer.

## <a name="audit-log-search"></a>Søgning i overvågningslog

En samlet [overvågningslog](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for alle dine satellitplaceringer er tilgængelig fra søgesiden for Microsoft 365 overvågningslog. Du kan se alle overvågningslogposter på tværs af geografiske placeringer, f.eks. NAM-& EUR-brugernes aktiviteter vises i én organisationsvisning, og derefter kan du anvende eksisterende filtre til at se bestemte brugeres aktiviteter.

> [!NOTE]
> Exchange administrationsovervågningshændelser er kun tilgængelige for standardplaceringen.

## <a name="bcs-secure-store-apps"></a>BCS, Secure Store, Apps

BCS, Secure Store og Apps har alle separate instanser på hver satellitplacering, og derfor skal SharePoint Online-administratoren administrere og konfigurere disse tjenester separat fra hver satellitplacering.

## <a name="compliance-admin-center"></a>Administration af overholdelse

Der er ét centralt overholdelsescenter for en multi-geo-lejer: [Microsoft Purview Administration](https://compliance.microsoft.com/).

## <a name="ediscovery"></a>eDiscovery

En eDiscovery-administrator eller administrator af en multi-geo-lejer kan som standard kun udføre eDiscovery på den centrale placering af lejeren. Den Office 365 globale administrator skal tildele eDiscovery Manager-tilladelser for at give andre tilladelse til at udføre eDiscovery og tildele en "Område"-parameter i deres relevante overholdelsessikkerhedsfilter for at angive området til udførelse af eDiscovery som satellitplacering, ellers udføres der ingen eDiscovery for satellitplaceringen. Hvis du vil konfigurere sikkerhedsfilteret for overholdelse af angivne standarder for et område, skal du se [Konfigurer Office 365 Multi-Geo eDiscovery](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Exchange postkasser

Brugernes Exchange postkasser flyttes automatisk, hvis deres PDL ændres. Når der oprettes en ny postkasse, klargøres den til brugerens PDL eller til den centrale placering, hvis der ikke er angivet nogen værdi for brugerens PDL.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Information Protection(IP) DLP-politik (Forebyggelse af datatab)

Du kan angive dine IP DLP-politikker for OneDrive for Business, SharePoint og Exchange i Security and Compliance Center og tilpasse politikker efter behov til hele lejeren eller relevante brugere. Eksempel: Hvis du vil vælge en politik for en bruger på en satellitplacering, skal du vælge at anvende politikken på et bestemt OneDrive og angive brugerens OneDrive URL-adresse. Se [Oversigt over politikker til forebyggelse af datatab](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for at få generel vejledning i oprettelse af DLP-politikker.

DLP-politikkerne synkroniseres automatisk på baggrund af deres anvendelighed på hver geografisk placering.

Implementering af Information Protection- og Microsoft Purview-politikker til forebyggelse af datatab for alle brugere på en geografisk placering er ikke en mulighed, der er tilgængelig i brugergrænsefladen. I stedet skal du vælge de relevante konti for politikken eller anvende politikken globalt på alle konti.

## <a name="microsoft-power-apps"></a>Microsoft Power Apps

Power Apps, der er oprettet for satellitplaceringen, bruger slutpunktet, der er placeret på lejerens centrale placering. Microsoft Power Apps er ikke en Multi-Geo-tjeneste. 

## <a name="power-automate"></a>Power Automate

Flow, der er oprettet for satellitplaceringen, bruger slutpunktet, der er placeret i lejerens standardplacering for geo.  Power Automate er ikke en Multi-Geo-tjeneste. 

## <a name="sharepoint-storage-quota"></a>kvote for SharePoint lager

Som standard deler alle geografiske placeringer i et multi-geo-miljø den tilgængelige kvote for lejerlager.  Du kan også administrere lagerkvoten ved at tildele en bestemt kvote for en bestemt geografisk placering. Du kan få flere oplysninger under [SharePoint lagerkvoter i multi-geo-miljøer](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Deling

Administratorer kan angive og administrere delingspolitikker for hver af deres placeringer. De OneDrive og SharePoint websteder på de enkelte geografiske placeringer vil kun overholde de tilsvarende geospecifikke delingsindstillinger. (Du kan f.eks. tillade [ekstern deling](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for din centrale placering, men ikke for din satellitplacering eller omvendt). Bemærk, at delingsindstillingerne ikke tillader konfiguration af delingsbegrænsninger mellem geografiske placeringer.

## <a name="stream"></a>Stream

Videoer, der uploades til Stream i en 1:1-chat, gemmes i OneDrive af den person, der uploader. Mødeoptagelser gemmes i OneDrive for hver deltager, der registrerer mødet.

## <a name="taxonomy"></a>Taksonomi

Vi understøtter en samlet [taksonomi](/sharepoint/managed-metadata) for virksomhedsadministrerede metadata på tværs af geografiske placeringer, hvor masteren hostes på den centrale placering for din virksomhed. Vi anbefaler, at du administrerer din globale taksonomi fra den centrale placering og kun føjer placeringsspecifikke vilkår til satellitplaceringens taksonomi. Globale taksonomibegreber synkroniseres til satellitplaceringerne.

Se [Administrer metadata i en multi-geo-lejer](/sharepoint/dev/solution-guidance/multigeo-managedmetadata) for at få flere oplysninger og for at få vejledning til udviklere.

## <a name="user-profile-application"></a>Brugerprofilprogram

Der er et [brugerprofilprogram](/sharepoint/manage-user-profiles) på hver geo-placering. Hver brugers profiloplysninger hostes på deres geografiske placering og er tilgængelige for administratoren for den pågældende geografiske placering.

Hvis du har brugerdefinerede profilegenskaber, anbefaler vi, at du bruger det samme profilskema på tværs af geografiske områder og udfylder egenskaberne for din brugerdefinerede profil enten på alle geografiske placeringer, eller hvor det er nødvendigt. Hvis du vil have hjælp til, hvordan du udfylder brugerprofildata programmatisk, skal du se [API'en til opdatering af massebrugerprofil](/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Se [Arbejd med brugerprofiler i en multi-geo-lejer](/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) for at få flere oplysninger og for at få vejledning til udviklere.

## <a name="yammer"></a>Yammer

Yammer er ikke en Multi-Geo-arbejdsbelastning. Yammer tråde, der er gemt i Yammer, placeres på lejerens centrale placering. Yammer udruller en ændring af fillageret, som gemmer Yammer filer i SharePoint. Yammer filer, der er gemt i SharePoint, placeres det SharePoint websted, der er knyttet til gruppen Yammer. SharePoint gruppewebsteder er baseret på PDL-logik som beskrevet i [SharePoint websteder og grupper](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md#sharepoint-sites-and-groups).
