---
title: Konfiguration af Microsoft 365 Multi-Geo-lejer
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
description: I denne artikel kan du få mere at vide om, hvordan du tilføjer satellitplaceringer og konfigurerer din lejer til Microsoft 365 Multi-Geo.
ms.openlocfilehash: 2a82872e7c917421c0eb418cf0582eb33d2a53c9
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941190"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Konfiguration af Microsoft 365 Multi-Geo-lejer

Før du konfigurerer din lejer til Microsoft 365 Multi-Geo, skal du sørge for, at du har læst [Plan for Microsoft 365 Multi-Geo](plan-for-multi-geo.md). Hvis du vil følge trinnene i denne artikel, skal du bruge en liste over de geografiske placeringer, du vil aktivere som satellitplaceringer, og de testbrugere, du vil klargøre for disse placeringer.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Føj Multi-Geo-funktionerne i din Microsoft 365-plan til din lejer

Hvis du vil bruge Microsoft 365 Multi-Geo, skal du bruge _Multi-Geo-funktionerne i Microsoft 365-planen_ . Samarbejd med dit kontoteam for at føje denne plan til din lejer. Dit kontoteam forbinder dig med den relevante licensspecialist og får din lejer konfigureret.

Bemærk, at _Multi-Geo-funktionerne i Microsoft 365-planen_ er en tjenesteplan på brugerniveau. Du skal have en licens til hver bruger, som du vil hoste på en satellitplacering. Du kan tilføje flere licenser over tid, når du tilføjer brugere på satellitplaceringer.

Når din lejer er klargjort med  _Multi-Geo-funktionerne i Microsoft 365-planen_ , bliver fanen **Geo-placeringer** tilgængelig i OneDrive- og SharePoint-administrationscentrene.

## <a name="add-satellite-locations-to-your-tenant"></a>Føj satellitplaceringer til din lejer

Du skal tilføje en satellitplacering for hver geografisk placering, hvor du vil gemme data. Tilgængelige geografiske placeringer vises i følgende tabel:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![Skærmbillede af siden med geografiske placeringer i SharePoint Administration.](../media/sharepoint-multi-geo-admin-center.png)

Sådan tilføjer du en satellitplacering

1. Åbn SharePoint Administration. og gå til <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**Geo-placeringer**</a>.

1. Vælg **Tilføj placering**.

1. Vælg den placering, du vil tilføje, og vælg derefter **Næste**.

1. Skriv det domæne, du vil bruge med den geografiske placering, og vælg derefter **Tilføj**.

1. Vælg **Luk**.

Klargøring kan tage fra et par timer op til 72 timer, afhængigt af størrelsen på din lejer. Når klargøringen af en satellitplacering er fuldført, modtager du en bekræftelse via mail. Når den nye geografiske placering vises med blåt på kortet under fanen **Geoplaceringer** i OneDrive Administration, kan du fortsætte med at angive brugernes foretrukne dataplacering til den pågældende geografiske placering.

> [!IMPORTANT]
> Din nye satellitplacering konfigureres med standardindstillinger. Dette giver dig mulighed for at konfigurere denne satellitplacering, som passer til dine lokale behov for overholdelse af angivne standarder.

## <a name="setting-users-preferred-data-location"></a>Angivelse af brugernes foretrukne dataplacering
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span>

Når du aktiverer de nødvendige satellitplaceringer, kan du opdatere dine brugerkonti til at bruge den relevante foretrukne dataplacering. Vi anbefaler, at du angiver en foretrukken dataplacering for hver bruger, selvom den pågældende bruger bor på den centrale placering.

> [!IMPORTANT]
> Hvis en brugers foretrukne dataplacering er angivet til en placering, der ikke er konfigureret som en satellitplacering eller den centrale placering, vil systemet som standard være den centrale placering, når OneDrive- og SharePoint-websteder og gruppepostkasser klargøres.

> [!TIP]
> Vi anbefaler, at du starter valideringer med en testbruger eller en lille gruppe brugere, før du udruller multi-geo til din bredere organisation.

I Azure Active Directory (Azure AD) er der to typer brugerobjekter: kun cloudbrugere og synkroniserede brugere. Følg de relevante instruktioner for din type bruger.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synkroniser brugerens foretrukne dataplacering ved hjælp af Azure AD Connect

Hvis din virksomheds brugere synkroniseres fra et Active Directory-system i det lokale miljø til Azure AD, skal deres PreferredDataLocation udfyldes i AD og synkroniseres med Azure AD.

Følg processen i [Azure Active Directory Connect-synkronisering: Konfigurer den foretrukne dataplacering for Microsoft 365-ressourcer for](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) at konfigurere synkronisering af foretrukken dataplacering fra dit lokale Active Directory-domænetjenester (AD DS) til Azure AD.

Vi anbefaler, at du inkluderer angivelse af brugerens foretrukne dataplacering som en del af din standardarbejdsproces for brugeroprettelse.

> [!IMPORTANT]
> For nye brugere uden klargjort OneDrive skal du licensere kontoen og vente mindst 48 timer, efter at en brugers PDL synkroniseres med Azure AD, for at ændringerne kan overføres, før brugeren logger på OneDrive for Business. Indstilling af den foretrukne dataplacering, før brugeren logger på for at klargøre deres OneDrive for Business, sikrer, at brugerens nye OneDrive klargøres på den korrekte placering.

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Angivelse af foretrukken dataplacering kun for brugere i skyen

Hvis din virksomheds brugere ikke synkroniseres fra et Active Directory-system i det lokale miljø til Azure AD, hvilket betyder, at de er oprettet i Microsoft 365 eller Azure AD, skal PDL angives ved hjælp af Microsoft Azure Active Directory-modulet til Windows PowerShell.

Procedurerne i dette afsnit kræver [Microsoft Azure Active Directory Module til Windows PowerShell-modulet](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Hvis du allerede har installeret dette modul, skal du sørge for at opdatere til den nyeste version.

1. [Opret forbindelse, og log på](/connect-to-microsoft-365-powershell?view=o365-worldwide#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell&preserve-view=true) med et sæt globale administratorlegitimationsoplysninger for din lejer.

2. Brug [Set-MsolUser-cmdlet'en](/powershell/module/msonline/set-msoluser?view=azureadps-1.0&preserve-view=true) til at angive den foretrukne dataplacering for hver af dine brugere. Eksempel:

   ```powershell
   Set-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR
   ```

    Du kan kontrollere, at den foretrukne dataplacering blev opdateret korrekt, ved hjælp af cmdlet'en Get-MsolUser. Eksempel:

   ```powershell
   (Get-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation
   ```

![Skærmbillede af PowerShell-vinduet, der viser set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

Vi anbefaler, at du inkluderer angivelse af brugerens foretrukne dataplacering som en del af din standardarbejdsproces for brugeroprettelse.

> [!IMPORTANT]
> For nye brugere uden klargjort OneDrive skal du licensere kontoen og vente mindst 48 timer, efter at en brugers PDL er angivet, for at ændringerne kan overføres, før brugeren logger på OneDrive. Indstilling af den foretrukne dataplacering, før brugeren logger på for at klargøre deres OneDrive for Business, sikrer, at brugerens nye OneDrive klargøres på den korrekte placering.

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Klargøring af OneDrive og effekten af PDL

Hvis brugeren allerede har et OneDrive-websted, der er oprettet i lejeren, flyttes deres eksisterende OneDrive ikke automatisk ved angivelse af deres PDL. Hvis du vil flytte en brugers OneDrive, skal du se [Flytning af OneDrive for Business Geo](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online flytter automatisk brugerens postkasse, hvis PLD ændres, og MailboxRegion ikke længere svarer til geoplaceringskoden for postkassedatabasen. Du kan få flere oplysninger under [Administration af Exchange Online-postkasser i et multi-geo-miljø](./administering-exchange-online-multi-geo.md).

Hvis brugeren ikke har et OneDrive-websted i lejeren, klargøres OneDrive for vedkommende i overensstemmelse med deres PDL-værdi, idet det antages, at PDL for brugeren stemmer overens med en af virksomhedens satellitplaceringer.

## <a name="configuring-multi-geo-search"></a>Konfiguration af Multi-Geo-søgning

Din multi-geo-lejer har samlede søgefunktioner, der gør det muligt for en søgeforespørgsel at returnere resultater overalt i lejeren.

Søgninger fra disse indgangspunkter returnerer som standard samlede resultater, selvom hvert søgeindeks er placeret inden for den relevante geografiske placering:

- OneDrive for Business
- Dykke
- SharePoint-startside
- Søgecenter

Derudover kan multi-geo-søgefunktioner konfigureres for dine brugerdefinerede søgeprogrammer, der bruger SharePoint-søge-API'en.

Gennemse [Konfigurer søgning efter OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for at få instruktioner, herunder eventuelle begrænsninger og forskelle.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Validering af Microsoft 365 Multi-Geo-konfigurationen

Nedenfor er nogle grundlæggende use cases, som du måske vil inkludere i din valideringsplan, før du udruller Microsoft 365 Multi-Geo til din virksomhed bredt. Når du har fuldført disse test og eventuelle yderligere use cases, der er relevante for din virksomhed, kan du vælge at gå videre til at tilføje brugerne i din indledende pilotgruppe.

**OneDrive for Business**:

Vælg OneDrive fra Microsoft 365-appstarteren, og bekræft, at du automatisk dirigeres til den relevante geoplacering for brugeren baseret på brugerens PDL. OneDrive for Business bør nu begynde at klargøre på den pågældende placering. Når det er klargjort, kan du prøve at overføre og downloade nogle dokumenter.

**OneDrive-mobilapp**:

Log på din OneDrive-mobilapp med dine legitimationsoplysninger til din testkonto. Bekræft, at du kan se dine OneDrive for Business-filer og kan interagere med dem fra din mobilenhed.

**OneDrive-synkroniseringsklient**:

Bekræft, at OneDrive-synkroniseringsklienten automatisk registrerer din geoplacering for OneDrive for Business ved logon. Hvis du har brug for at downloade synkroniseringsklienten, kan du klikke på **Synkroniser** i OneDrive-biblioteket.

**Office-programmer**:

Bekræft, at du kan få adgang til OneDrive for Business ved at logge på fra et Office-program, f.eks. Word. Åbn Office-programmet, og vælg "OneDrive – \<TenantName\>". Office registrerer din OneDrive-placering og viser dig de filer, du kan åbne.

**Deling**:

Prøv at dele OneDrive-filer. Bekræft, at personvælgeren viser dig alle dine SharePoint Online-brugere, uanset deres geografiske placering.
