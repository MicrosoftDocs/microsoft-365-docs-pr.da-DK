---
title: Microsoft 365 Multi-Geo
ms.reviewer: anfra
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: I denne artikel kan du få mere at vide om, hvordan du udvider din Microsoft 365-tilstedeværelse til flere geografiske områder med Microsoft 365 Multi-Geo.
ms.openlocfilehash: 154082785b71be8fbba55e00e2df8a1a3eacb500
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490204"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo

Med Microsoft 365 Multi-Geo kan din organisation udvide sin Microsoft 365-tilstedeværelse til flere geografiske områder og/eller lande i din eksisterende lejer. Kontakt dit Microsoft-kontoteam for at tilmelde dig dit multinationale firma til Microsoft 365 Multi-Geo.
  
Med Microsoft 365 Multi-Geo kan du klargøre og gemme inaktive data på de geografiske placeringer, du har valgt at opfylde kravene til dataopbevaring, og samtidig låse op for din globale udrulning af moderne produktivitetsoplevelser for din arbejdsstyrke.

Hvis du vil have en video introduktion til Microsoft 365 Multi-Geo, skal du se [SharePoint Online og OneDrive Multi-Geo til at styre, hvor dine data er placeret](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Multi-Geo-arkitektur

I et Multi-Geo-miljø består din Microsoft 365-lejer af en central placering (hvor dit Microsoft 365-abonnement oprindeligt er klargjort) og en eller flere satellitplaceringer. I en multi-geo-lejer mestres oplysningerne om geografiske placeringer, grupper og brugeroplysninger i Azure Active Directory (Azure AD). Da dine lejeroplysninger mestres centralt og synkroniseres til hver geoplacering, indeholder deling og oplevelser, der involverer alle fra din virksomhed, global opmærksomhed.

![Skærmbillede af multi-geo-kort fra SharePoint Administration.](../media/multi-geo-world-map.png)

Bemærk, at Microsoft 365 Multi-Geo ikke er udviklet til optimering af ydeevnen, men er designet til at opfylde krav til dataopbevaring. Du kan få oplysninger om optimering af ydeevnen for Microsoft 365 under [Netværksplanlægning og justering af ydeevne til Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) eller kontakte din supportgruppe.

## <a name="terminology"></a>Terminologi

Her er de vigtigste begreber, der bruges til at beskrive Microsoft 365 Multi-Geo:

- **Central placering** – den geografiske placering, hvor din lejer oprindeligt blev klargjort.
- **Geo-administrator** – En administrator, der kan administrere en eller flere angivne satellitplaceringer.
- **Geokode** – en kode på tre bogstaver for en given geografisk placering.
- **Geografisk placering** – en geografisk placering, der kan bruges i en multi-geo-lejer til at hoste data, herunder Exchange-postkasser og OneDrive- og SharePoint-websteder.
- **Preferred Data Location (PDL)** – En brugeregenskab, der er angivet af administratoren, og som angiver, hvor den geografiske placering, hvor brugernes Exchange-postkasse og OneDrive skal klargøres. PDL bestemmer også, hvor SharePoint-websteder, der er oprettet af brugeren, klargøres.
- **Satellitplacering** – de geografiske placeringer, hvor de geobevidste Microsoft 365-arbejdsbelastninger (SharePoint, OneDrive og Exchange) er aktiveret i en multi-geo-lejer.
- **Lejer** – en organisations repræsentation i Microsoft 365, som typisk har et eller flere domæner tilknyttet (f.eks. contoso.com).

## <a name="licensing"></a>Licensering

Microsoft 365 Multi-Geo er tilgængelig som et tilføjelsesprogram til følgende Microsoft 365-abonnementsplaner for Enterprise Agreement kunder med mindst 250 Microsoft 365-pladser i deres lejer og mindst 5 % af disse sæder ved hjælp af multi-geo. Brugerabonnementslicenser skal være på samme Enterprise Agreement som Multi-Geo Services-licenserne. Kontakt dit Microsoft-kontoteam for at få flere oplysninger.

- Microsoft 365 F1, F3, E3 eller E5
- Office 365 F3, E1, E3 eller E5
- Exchange Online Plan 1 eller Plan 2
- OneDrive for Business Plan 1 eller Plan 2
- SharePoint Online Plan 1 eller Plan 2

Hvis en licens tildeles til en bruger og senere fjernes, sættes Chatdata for Teams-brugere i kø for at blive flyttet tilbage til den centrale placering. SharePoint- og Exchange-data flyttes ikke.

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 Multi-Geo-tilgængelighed

Microsoft 365 Multi-Geo tilbydes i øjeblikket i disse områder og lande:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Introduktion

Følg disse trin for at komme i gang med multi-geo:

1. Samarbejd med dit kontoteam for at tilføje _Multi-Geo-egenskaberne i Microsoft 365-tjenesteplanen_ . De guider dig til at tilføje det nødvendige antal licenser. Multi-Geo-funktionen er tilgængelig for EA-kunder med mindst 250 Microsoft 365-abonnementer.

   Før du kan begynde at bruge Microsoft 365 Multi-Geo, skal Microsoft konfigurere din Exchange Online lejer til multi-geo-support. Denne engangskonfigurationsproces udløses, når du har bestilt *Multi-Geo-funktionerne i Microsoft 365-tjenesteplanen* , og licenserne vises i din lejer. Du modtager arbejdsbelastningsspecifikke meddelelser i [Meddelelsescenter i Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) , når din lejer har fuldført konfigurationsprocessen for hver arbejdsbelastning, og du kan derefter begynde at konfigurere og bruge dine Multi-Geo-funktioner i Microsoft 365. Den tid, det kræver at konfigurere en lejer til Multi-Geo-support, varierer fra lejer til lejer, men de fleste lejere slutter inden for en måned efter modtagelse af funktionslicenserne. Større eller mere komplekse lejere kan kræve mere tid til at fuldføre konfigurationsprocessen. Kontakt dit kontoteam for at få oplysninger om din specifikke lejer, hvis du har brug for det.

2. Læs [Planlæg dit multi-geo-miljø](plan-for-multi-geo.md).

3. Få mere at vide om [administration af et multi-geo-miljø](administering-a-multi-geo-environment.md)[, og hvordan dine brugere vil opleve miljøet](multi-geo-user-experience.md).

4. Når du er klar til at konfigurere Microsoft 365 Multi-Geo, skal [du konfigurere din lejer til multi-geo](multi-geo-tenant-configuration.md).

5. [Konfigurer søgning](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Se også

[Multi-Geo i Exchange Online og OneDrive](https://Aka.ms/GoMultiGeo)

[Multi-Geo-funktioner i OneDrive og SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Multi-Geo-funktioner i Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Teams-oplevelse i et multi-geo-miljø](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
