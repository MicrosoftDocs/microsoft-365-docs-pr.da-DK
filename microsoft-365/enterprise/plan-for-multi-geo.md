---
title: Plan for Microsoft 365 Multi-Geo
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
description: Få mere at vide om Microsoft 365 Multi-Geo, hvordan multi-geo fungerer, og hvilke geografiske placeringer der er tilgængelige til datalager.
ms.openlocfilehash: bda48f14b14840eed03d456ef66e7d86df890619
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822788"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Plan for Microsoft 365 Multi-Geo

Denne vejledning er beregnet til administratorer af multinationale virksomheder ( MNCs), der forbereder deres Microsoft 365 lejer til at blive udvidet til yderligere geografiske områder i overensstemmelse med virksomhedens tilstedeværelse for at opfylde kravene til dataopbevaring.

I en multi-geo-konfiguration består din Microsoft 365 lejer af en central placering og en eller flere satellitplaceringer. Dette er en enkelt lejer, der strækker sig over flere geografiske placeringer. Dine lejeroplysninger, herunder geografiske placeringer, mestres i Azure Active Directory (Azure AD).

Her er nogle vigtige multi-geo-begreber, der kan hjælpe dig med at forstå de grundlæggende begreber i konfigurationen:

- **Lejer** – en organisations repræsentation i Microsoft 365 som typisk har et eller flere domæner tilknyttet (f.ekshttps://contoso.sharepoint.com). .

- **Geografiske placeringer** – de geografiske placeringer, der er tilgængelige til at hoste data i en Microsoft 365 lejer.

- **Satellitplaceringer** – de ekstra geografiske placeringer, du har konfigureret til at hoste data i din Microsoft 365 lejer. Multi-Geo-lejere strækker sig over mere end én geografisk placering, f.eks. Nordamerika og Europa.

- **Foretrukken dataplacering (PDL)** – den geografiske placering, hvor en enkelt brugers Exchange og OneDrive data gemmes. Dette kan angives af administratoren til en hvilken som helst af de geografiske placeringer, der er konfigureret for lejeren. Bemærk, at hvis du ændrer PDL for en bruger, der allerede har et OneDrive websted, flyttes deres OneDrive data ikke automatisk til den nye geografiske placering. Se [Flyt et OneDrive bibliotek til en anden geografisk placering for at](move-onedrive-between-geo-locations.md) få flere oplysninger. Hvis postkassen har en Exchange postkasse, flyttes den automatisk til den nye foretrukne dataplacering.

Aktivering af Multi-Geo kræver fire vigtige trin:

1. Samarbejd med dit kontoteam for at tilføje _Multi-Geo-egenskaberne i Microsoft 365_ serviceplan.

2. Vælg den eller de ønskede satellitplaceringer, og føj dem til din lejer.

3. Angiv brugernes foretrukne dataplacering til den ønskede satellitplacering. Når der klargøres et nyt OneDrive websted eller en Exchange postkasse for en bruger, klargøres den til brugerens PDL.

4. Overfør dine brugeres eksisterende OneDrive websteder fra den centrale placering til deres foretrukne dataplacering efter behov. (Exchange postkasser overføres automatisk, når du angiver en brugers PDL.

Se [Konfigurer Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md) for at få oplysninger om hvert af disse trin.

> [!IMPORTANT]
> Bemærk, at Microsoft 365 Multi-Geo ikke er udviklet til optimering af ydeevnen, er den designet til at opfylde krav til dataopbevaring. Du kan få oplysninger om optimering af ydeevnen for Microsoft 365 under [Netværksplanlægning og justering af ydeevne for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) eller kontakt supportgruppen.

Du kan konfigurere en af følgende placeringer til at være satellitplaceringer, hvor du kan hoste OneDrive og SharePoint websteder og Exchange postkasser. Når du planlægger multi-geo, skal du oprette en liste over de placeringer, du vil føje til din Microsoft 365 lejer. Vi anbefaler, at du starter med en eller to satellitplaceringer og derefter gradvist udvider til flere geografiske placeringer, hvis det er nødvendigt.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Når du konfigurerer multi-geo, kan du overveje at benytte lejligheden til at konsolidere din infrastruktur i det lokale miljø, mens du migrerer til Microsoft 365. Hvis du f.eks. har farme i det lokale miljø i Singapore og Malaysia, kan du konsolidere dem til APC-satellitplaceringen, forudsat at dataopbevaringskrav gør det muligt for dig at gøre det.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

Vi anbefaler, at du opretter en testbruger i Microsoft 365 for at udføre nogle indledende test. Vi gennemgår nogle test- og bekræftelsestrin med denne bruger, før du fortsætter med at onboarde produktionsbrugere i Microsoft 365 Multi-Geo.

Når du er færdig med at teste med testbrugeren, skal du vælge en pilotgruppe – måske fra it-afdelingen – for at være den første til at bruge OneDrive og Exchange på en ny geografisk placering. I denne første gruppe skal du vælge brugere, der endnu ikke har en OneDrive. Vi anbefaler ikke mere end fem personer i denne indledende gruppe og udvider gradvist efter en batchindrulningstilgang.

Hver bruger skal have et *foretrukket PDL-sæt (Data Location*), så Microsoft 365 kan bestemme, på hvilken geografisk placering deres OneDrive skal klargøres. Brugerens foretrukne dataplacering skal matche en af dine valgte satellitplaceringer eller din centrale placering. Selvom feltet PDL ikke er obligatorisk, anbefaler vi, at der angives en PDL for alle brugere. Arbejdsbelastninger for en bruger uden en PDL klargøres på den centrale placering.

Opret en liste over dine brugere, og medtag brugerens hovednavn (UPN) og placeringskoden for den relevante foretrukne dataplacering. Medtag din testbruger og din indledende pilotgruppe til at starte med. Du skal bruge denne liste til konfigurationsprocedurerne.

Hvis brugerne synkroniseres fra et Active Directory i det lokale miljø system til Azure Active Directory, skal du angive den foretrukne dataplacering som en Active Directory-attribut og synkronisere den ved hjælp af Azure Active Directory Forbind. Du kan ikke konfigurere den foretrukne dataplacering direkte for synkroniserede brugere ved hjælp af Azure AD PowerShell. Trinnene til konfiguration af PDL i Active Directory og Synkroniser det beskrives i [Azure Active Directory Forbind synkronisering: Konfigurer den foretrukne dataplacering for Microsoft 365 ressourcer](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Administrationen af en multi-geo-lejer kan afvige fra en ikke-multi-geo-lejer, da mange af de SharePoint og OneDrive indstillinger og tjenester er multi-geo-opmærksomme. Vi anbefaler, at du [gennemser Administration af et multi-geo-miljø](administering-a-multi-geo-environment.md) , før du fortsætter med konfigurationen.

Læs [Brugeroplevelsen i et multi-geo-miljø](multi-geo-user-experience.md) for at få oplysninger om dine slutbrugers oplevelse i et multi-geo-miljø.

Hvis du vil i gang med at konfigurere Microsoft 365 Multi-Geo, skal du se [Konfigurer Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

Når du har fuldført konfigurationen, skal du huske at [overføre dine brugeres OneDrive biblioteker](move-onedrive-between-geo-locations.md) efter behov for at få dine brugere til at arbejde fra deres foretrukne dataplaceringer.

## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 Multi-Geo eDiscovery-konfiguration](./multi-geo-ediscovery-configuration.md)
