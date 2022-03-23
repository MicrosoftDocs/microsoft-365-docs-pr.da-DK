---
title: Plan for Microsoft 365 multi-geo
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
description: Få mere Microsoft 365 om Multi-Geo, hvordan multi-geo fungerer, og hvilke geoplaceringer der er tilgængelige til datalagring.
ms.openlocfilehash: 5c079d5cf5f093be2c942a53468494044913fbd7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590565"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Plan for Microsoft 365 multi-geo

Denne vejledning er beregnet til administratorer af multilandsvirksomheder, der forbereder deres Microsoft 365-lejer til at blive udvidet til yderligere områder i overensstemmelse med virksomhedens tilstedeværelse, så de opfylder kravene til dataopbevaring.

I en multi-geo-konfiguration består Microsoft 365 af en central placering og en eller flere satellitplaceringer. Dette er en enkelt lejer, der strækker sig over flere geografiske placeringer. Dine lejeroplysninger, herunder geoplaceringer, administreres i Azure Active Directory (Azure AD).

Her er nogle vigtige multi-geo termer, der kan hjælpe dig med at forstå de grundlæggende begreber i konfigurationen:

-   **Lejer** – En organisations repræsentation i en Microsoft 365 som typisk har et eller flere domæner tilknyttet (f.ekshttps://contoso.sharepoint.com). . 

-   **Geografiske placeringer –** de geografiske placeringer, der er tilgængelige til at hoste data i en Microsoft 365 lejer.

-   **Satellitplaceringer** – de ekstra geoplaceringer, som du har konfigureret til at hoste data i din Microsoft 365 lejer. Multi-geo lejere strækker sig over mere end ét geoplacering, f.eks. Nordamerika og Europa.

-   **Foretrukken dataplacering (PDL)** – den geoplacering, hvor en enkelt brugers Exchange og OneDrive data gemmes. Administratoren kan angive dette til en hvilken som helst af de geoplaceringer, der er konfigureret for lejeren. Bemærk, at hvis du ændrer PDL for en bruger, der allerede har et OneDrive-websted, flyttes deres OneDrive-data ikke automatisk til den nye geoplacering. Se [Flyt et OneDrive til en anden geoplacering for at](move-onedrive-between-geo-locations.md) få flere oplysninger. Hvis de har Exchange postkasse, flyttes postkassen automatisk til den nye foretrukne dataplacering.

Aktivering af multi-geo kræver fire vigtige trin:

1.  Arbejd med dit kontoteam for at _tilføje Multi-Geo Capabilities i Microsoft 365_ serviceabonnement.

2.  Vælg den eller de ønskede satellitplaceringer, og føj dem til din lejer.

3.  Angiv dine brugeres foretrukne dataplacering til den ønskede satellitplacering. Når en ny OneDrive eller Exchange postkasse er klargjort til en bruger, klargøres den til brugerens PDL.

4.  Overfør dine brugeres eksisterende OneDrive fra den centrale placering til deres foretrukne dataplacering efter behov. (Exchange postkasser overføres automatisk, når du angiver en brugers PDL).

Se [Konfigurer Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md) for at få mere at vide om hvert af disse trin.

> [!IMPORTANT]
> Bemærk, Microsoft 365 Multi-Geo ikke er designet til optimering af ydeevnen, er den designet til at opfylde krav til dataopbevaring. Du kan finde oplysninger om optimering af Microsoft 365 i [Netværksplanlægning og justering af ydeevnen for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) eller ved at kontakte din supportgruppe.

Du kan konfigurere en af følgende placeringer til at være satellitplaceringer, hvor du kan hoste OneDrive og SharePoint websteder samt Exchange postkasser. Når du planlægger multi-geo, skal du lave en liste over de placeringer, du vil føje til din Microsoft 365 lejer. Vi anbefaler, at du starter med en eller to satellitplaceringer og derefter gradvist udvider til flere geoplaceringer, hvis det er nødvendigt.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Når du konfigurerer multi-geo, kan du overveje at benytte muligheden for at konsolidere din lokale infrastruktur, mens du overfører til Microsoft 365. Hvis du f.eks. har lokale farme i Singapore og Malaysia, kan du konsolidere dem til APC-satellitplaceringen, forudsat at du har krav til dataopbevaring, så du kan gøre det.

## <a name="best-practices"></a>Anbefalede fremgangsmåder

Vi anbefaler, at du opretter en testbruger i Microsoft 365 at udføre nogle indledende test. Vi gennemgår nogle test- og bekræftelsestrin med denne bruger, før du går videre til at onboarde produktionsbrugere Microsoft 365 Multi-Geo.

Når du har afsluttet testen med testbrugeren, skal du vælge en pilotgruppe – måske fra din it-afdeling – som skal være den første til at bruge OneDrive og Exchange på en ny geoplacering. For denne første gruppe skal du vælge brugere, der endnu ikke har OneDrive. Vi anbefaler, at der ikke er mere end fem personer i denne indledende gruppe og gradvist udvider efter en batched rollout-tilgang.

Hver bruger skal have et *foretrukket dataplaceringssæt* (PDL), så Microsoft 365 kan afgøre, hvilken geoplacering der skal klargøre deres OneDrive. Brugerens foretrukne dataplacering skal svare til en af dine valgte satellitplaceringer eller din centrale placering. Mens PDL-feltet ikke er obligatorisk, anbefaler vi, at der angives en PDL for alle brugere. Arbejdsbelastninger for en bruger uden PDL klargøres på den centrale placering.

Opret en liste over dine brugere, og medtag brugerens hovednavn (UPN) og placeringskoden for den relevante foretrukne dataplacering. Medtag din testbruger og din indledende pilotgruppe til at starte med. Du skal bruge denne liste til konfigurationsprocedurer.

Hvis dine brugere synkroniseres fra et lokalt Active Directory-system til Azure Active Directory, skal du angive den foretrukne dataplacering som en Active Directory-attribut og synkronisere den ved hjælp af Azure Active Directory Forbind. Du kan ikke direkte konfigurere den foretrukne dataplacering for synkroniserede brugere ved hjælp af Azure AD PowerShell. Trinnene til at konfigurere PDL i Active Directory og Synkroniser det er dækket [Azure Active Directory Forbind synkronisering: Konfigurer foretrukken dataplacering for Microsoft 365 ressourcer](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

Administrationen af en multi-geo-lejer kan afvige fra en ikke-multi-geo-lejer, da mange af SharePoint- og OneDrive-indstillingerne og -tjenesterne er multi-geo-bevidste. Vi anbefaler, at du [gennemgår Administration af et multi-geo-miljø,](administering-a-multi-geo-environment.md) før du fortsætter med din konfiguration.

Læs [Brugeroplevelse i et multi-geo-miljø](multi-geo-user-experience.md) for at få mere at vide om dine slutbrugeres oplevelse i et multi-geo-miljø.

Se Konfigurer multi-geo Microsoft 365 at komme i gang med [Microsoft 365 konfiguration af Multi-Geo](multi-geo-tenant-configuration.md).

Når du har gennemført konfigurationen, skal du huske at overføre dine [brugeres OneDrive biblioteker](move-onedrive-between-geo-locations.md) efter behov for at få dine brugere til at arbejde fra deres foretrukne dataplaceringer.

## <a name="related-topics"></a>Relaterede emner

[Microsoft 365 fler geo eDiscovery-konfiguration](./multi-geo-ediscovery-configuration.md)