---
title: Microsoft 365 multi-geo-lejerkonfiguration
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: I denne artikel kan du lære, hvordan du tilføjer satellitplaceringer og konfigurerer din lejer Microsoft 365 Multi-Geo.
ms.openlocfilehash: 9842ff2295a64f544940f579d732c688735ae341
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601577"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 multi-geo-lejerkonfiguration

Før du konfigurerer din lejer til Microsoft 365 Multi-Geo, skal du sørge for, at du har læst [Plan for Microsoft 365 Multi-Geo](plan-for-multi-geo.md). Hvis du vil følge trinnene i denne artikel, skal du bruge en liste over de geoplaceringer, du vil aktivere som satellitplaceringer, og de testbrugere, du vil klargøre til disse placeringer.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Føj multige geografiske egenskaber i din Microsoft 365 plan til din lejer

For at Microsoft 365 multi-geo har du brug for _multi-geo-egenskaber i Microsoft 365_ plan. Arbejd med dit kontoteam for at føje denne plan til din lejer. Dit kontoteam forbinder dig med den relevante licensspecialist og får konfigureret din lejer.

Bemærk, at _multi geografiske egenskaber i Microsoft 365_ er en serviceplan på brugerniveau. Du skal have en licens til hver bruger, du vil hoste i en satellitplacering. Du kan tilføje flere licenser med tiden, efterhånden som du tilføjer brugere på satellitplaceringer.

Når din lejer er blevet klargjort med _Multi-Geo Capabilities i Microsoft 365-planen_, vil fanen **Geo-placeringer** blive tilgængelig i OneDrive og SharePoint Administration.

## <a name="add-satellite-locations-to-your-tenant"></a>Føj satellitplaceringer til din lejer

Du skal tilføje en satellitplacering for hver geoplacering, hvor du vil gemme data. Tilgængelige geoplaceringer er vist i følgende tabel:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![Skærmbillede af siden med geoplaceringer i SharePoint Administration.](../media/sharepoint-multi-geo-admin-center.png)

Sådan tilføjes en satellitplacering

1. Åbn SharePoint Administration. og gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**Geo-placeringer**</a>.

1. Vælg **Tilføj placering**.

1. Vælg den placering, du vil tilføje, og vælg derefter **Næste**.

1. Skriv det domæne, du vil bruge med geoplaceringen, og vælg derefter **Tilføj**.

1. Vælg **Luk**.

Klargøring kan tage fra et par timer op til 72 timer, afhængigt af størrelsen på din lejer. Når klargøring af en satellitplacering er fuldført, modtager du en bekræftelse via mail. Når den nye geoplacering vises med blåt på kortet under fanen **Geo-placeringer** i OneDrive Administration, kan du fortsætte med at angive brugernes foretrukne dataplacering til den pågældende geoplacering. 

> [!IMPORTANT]
> Din nye satellitplacering konfigureres med standardindstillinger. Det gør det muligt at konfigurere satellitplaceringen efter behov, der passer til dine lokale overholdelsesbehov.

## <a name="setting-users-preferred-data-location"></a>Angive brugernes foretrukne dataplacering
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Når du har aktiveret de nødvendige satellitplaceringer, kan du opdatere dine brugerkonti til at bruge den relevante foretrukne dataplacering. Vi anbefaler, at du angiver en foretrukken dataplacering for hver bruger, også selvom brugeren forbliver på den centrale placering.

> [!IMPORTANT]
> Hvis en brugers foretrukne dataplacering er angivet til en placering, der ikke er konfigureret som en satellitplacering eller den centrale placering, vil systemet som standard være den centrale placering, når OneDrive og SharePoint-websteder og gruppepostkasser klargøres.

> [!TIP]
> Vi anbefaler, at du begynder valideringer med en testbruger eller en lille gruppe af brugere, før du ruller multi-geo ud til din bredere organisation.

I Azure Active Directory (Azure AD) findes der to typer brugerobjekter: kun brugere i skyen og synkroniserede brugere. Følg de relevante instruktioner for din type bruger.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synkroniser brugerens foretrukne dataplacering ved hjælp af Azure AD-Forbind 

Hvis virksomhedens brugere synkroniseres fra et lokalt Active Directory-system til Azure AD, skal deres PreferredDataLocation udfyldes i AD og synkroniseres med Azure AD.

Følg processen i Azure Active Directory Forbind-synkronisering: Konfigurer foretrukken [dataplacering for Microsoft 365-ressourcer for](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) at konfigurere foretrukken dataplaceringssynkronisering fra din lokale Active Directory-domæneservices (AD DS) til Azure AD.

Vi anbefaler, at du medtager konfiguration af brugerens foretrukne dataplacering som en del af den almindelige arbejdsproces for oprettelse af brugere.

> [!IMPORTANT]
> For nye brugere uden OneDrive klargjort skal du licensere kontoen og vente mindst 48 timer efter, at en brugers PDL synkroniseres med Azure AD, før ændringerne overføres, før brugeren logger på OneDrive for Business. (Indstilling af den foretrukne dataplacering, før brugeren logger på for at klargøre deres OneDrive for Business sikrer, at brugerens nye OneDrive klargøres på den korrekte placering).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Indstilling af foretrukken dataplacering kun for brugere i skyen 

Hvis virksomhedens brugere ikke synkroniseres fra et lokalt Active Directory-system til Azure AD, hvilket betyder, at de er oprettet i Microsoft 365 eller Azure AD, skal PDL'en konfigureres ved hjælp af Microsoft Azure Active Directory-modulet til Windows PowerShell.

Fremgangsmåderne i dette afsnit kræver, [at Microsoft Azure Active Directory-modul til Windows PowerShell modul](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Hvis du allerede har dette modul installeret, skal du sørge for at opdatere til den nyeste version.

1.  [Forbind og logge på](/powershell/connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) med et sæt globale administratorlegitimationsoplysninger for din lejer.

2.  Brug [Cmdlet'en Set-MsolUser](/powershell/msonline/v1/set-msoluser) til at angive den foretrukne dataplacering for hver af dine brugere. Eksempel:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Du kan kontrollere, at den foretrukne dataplacering er blevet opdateret korrekt ved hjælp af Get-MsolUser cmdlet. Eksempel:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Skærmbillede af PowerShell-vinduet, der viser set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

Vi anbefaler, at du medtager konfiguration af brugerens foretrukne dataplacering som en del af den almindelige arbejdsproces for oprettelse af brugere.

> [!IMPORTANT]
> For nye brugere uden OneDrive klargjort skal du licensere kontoen og vente mindst 48 timer efter, at en brugers PDL er indstillet til, at ændringerne skal overføres, før brugeren logger på for at OneDrive. (Indstilling af den foretrukne dataplacering, før brugeren logger på for at klargøre deres OneDrive for Business sikrer, at brugerens nye OneDrive klargøres på den korrekte placering).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive klargøring og effekten af PDL

Hvis brugeren allerede har et OneDrive websted oprettet i lejeren, flytter angivelse af deres PDL ikke automatisk deres eksisterende OneDrive. Hvis du vil flytte en OneDrive, skal du [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online flytter automatisk brugerens postkasse, hvis PLD'en ændres, og MailboxRegion ikke længere svarer til koden for postkassedatabasens geoplacering. Få mere at vide under [Administration Exchange Online postkasser i et miljø med flere geografiske oplysninger](./administering-exchange-online-multi-geo.md).

Hvis brugeren ikke har et OneDrive-websted inden for lejeren, bliver OneDrive klargjort til dem i overensstemmelse deres PDL-værdi, hvis PDL for brugeren matcher en af firmaets satellitplaceringer.

## <a name="configuring-multi-geo-search"></a>Konfiguration af Multi-Geo-søgning

Din multi-geo-lejer har samlede søgefunktioner, så en søgeforespørgsel kan returnere resultater fra et vilkårligt sted i lejeren.

Som standard returnerer søgninger fra disse indgangspunkter aggregatresultater, selvom hvert søgeindeks er placeret inden for dets relevante geoplacering:

- OneDrive for Business

- Delve

- SharePoint startside

- Søgecenter

Desuden kan søgning i flere geografiske områder konfigureres til dine brugerdefinerede søgeprogrammer, der bruger søge-SharePoint-søge-API.

Gennemse Konfigurer [søgning efter OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for vejledning, herunder eventuelle begrænsninger og forskelle.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Validering af Microsoft 365 multi-geo-konfiguration

Nedenfor er nogle eksempler på grundlæggende use cases, som du kan medtage i din valideringsplan, før det Microsoft 365 udrulles Multi-Geo til din virksomhed. Når du har gennemført disse test og eventuelle yderligere use cases, der er relevante for din virksomhed, kan du vælge at gå videre til at tilføje brugerne i din indledende pilotgruppe.

**OneDrive for Business**

Vælg OneDrive fra Microsoft 365-appstarteren, og bekræft, at du automatisk bliver omdirigeret til den relevante geoplacering for brugeren baseret på brugerens PDL. OneDrive for Business nu begynde klargøring på den pågældende placering. Når nogle dokumenter er klargjort, kan du prøve at overføre og hente dem.

**OneDrive mobilapp**

Log på din OneDrive-mobilapp med dine legitimationsoplysninger til testkontoen. Bekræft, at du kan se OneDrive for Business filer og kan interagere med dem fra din mobilenhed.

**OneDrive-synkronisering klient**

Bekræft, at OneDrive-synkronisering-klienten automatisk registrerer din OneDrive for Business geografiske placering ved logon. Hvis du vil downloade synkroniseringsklienten, kan du klikke på **Synkroniser** i OneDrive bibliotek.

**Office programmer**

Bekræft, at du kan OneDrive for Business adgang ved at logge på fra Office, f.eks. Word. Åbn Office, og vælg "OneDrive – <TenantName>". Office registrerer din OneDrive placering og viser dig de filer, som du kan åbne.

**Deling**

Prøv at OneDrive filer. Bekræft, at vælgeren personer viser dig alle dine SharePoint onlinebrugere uanset deres geografiske placering.
