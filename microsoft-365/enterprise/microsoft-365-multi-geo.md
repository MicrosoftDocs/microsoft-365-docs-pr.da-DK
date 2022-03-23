---
title: Microsoft 365 Multi-Geo
ms.reviewer: adwood
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
description: I denne artikel kan du lære, hvordan du udvider Microsoft 365 din tilstedeværelse til flere geografiske områder med Microsoft 365 Multi-Geo.
ms.openlocfilehash: 5122979fc79ce9aebe542a80ed614e7dcad70d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589750"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo

Med Microsoft 365 Multi-Geo kan din organisation udvide sin tilstedeværelse Microsoft 365 til flere geografiske områder og/eller lande i din eksisterende lejer. Kontakt dit Microsoft-kontoteam for at tilmelde dig dit multi nationale firma til Microsoft 365 multi-geo.
  
Med Microsoft 365 Multi-Geo kan du klargøre og gemme data på et andet sted på de geoplaceringer, du har valgt at opfylde kravene til dataopbevaring, og på samme tid låse din globale udrulning af moderne produktivitetsoplevelser op for dine medarbejdere.

Du kan finde en videointro Microsoft 365 multi-geo i [SharePoint Online og OneDrive Multi-Geo at kontrollere, hvor dine data befinder sig](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Multi-Geo-arkitektur

I et Multi-Geo-miljø består din Microsoft 365-lejer af en central placering (hvor dit Microsoft 365-abonnement oprindeligt blev klargjort) og en eller flere satellitplaceringer. I en multi-geo-lejer, masteres oplysningerne om geoplaceringer, grupper og brugeroplysninger i Azure Active Directory (Azure AD). Da dine lejeroplysninger masteres centralt og synkroniseres til hver geoplacering, vil deling og oplevelser, der involverer alle fra din virksomhed, indeholde global opmærksomhed.

![Skærmbillede af multi-geo-kort fra SharePoint Administration.](../media/multi-geo-world-map.png)

Bemærk, Microsoft 365 Multi-Geo ikke er designet til optimering af ydeevnen, er den designet til at opfylde krav til dataopbevaring. Du kan finde oplysninger om optimering af Microsoft 365 i [Netværksplanlægning og justering af ydeevnen for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) eller ved at kontakte din supportgruppe.

## <a name="terminology"></a>Terminologi

Her er de vigtigste ord, der bruges til at beskrive Microsoft 365 Multi-Geo:

- **Central placering** – den geoplacering, hvor din lejer oprindeligt blev klargjort.
- **Geoadministrator** – En administrator, der kan administrere en eller flere angivne satellitplaceringer.
- **Geokode** – en kode på tre bogstaver for en given geoplacering.
- **Geoplacering** – en geografisk placering, der kan bruges i en multi-geo-lejer til at hoste data, herunder Exchange-postkasser og OneDrive og SharePoint websteder.
- **Foretrukken dataplacering (PDL)** – En brugeregenskab, der er angivet af administratoren, og som angiver, hvor den geoplacering, hvor brugerne Exchange postkassen og OneDrive skal klargøres. PDL'en bestemmer også, SharePoint websteder, der oprettes af brugeren, klargøres.
- **Satellitplacering** – De geoplaceringer, hvor de geo-bevidste Microsoft 365 (SharePoint, OneDrive og Exchange) er aktiveret i en multi-geo-lejer.
- **Lejer** – En organisations repræsentation i en Microsoft 365 som typisk har et eller flere domæner knyttet til den (f.eks. contoso.com).

## <a name="licensing"></a>Licensering

Microsoft 365 Multi-Geo er tilgængelig som et tilføjelsesabonnement til følgende Microsoft 365-abonnementsplaner til Enterprise Agreement-kunder med mindst 250 Microsoft 365 pladser i deres lejer og mindst 5 % af disse pladser ved hjælp af multi-geo. Brugerabonnementslicenser skal være på samme Enterprise Agreement som Multi-Geo Services-licenser. Kontakt dit Microsoft-kontoteam for at få flere oplysninger.

- Microsoft 365 F1, F3, E3 eller E5
- Office 365 F3, E1, E3 eller E5
- Exchange Online Plan 1 eller Plan 2
- OneDrive for Business plan 1 eller Plan 2
- SharePoint Online Plan 1 eller Plan 2

Hvis en licens er tildelt en bruger og senere fjernes, Teams i kø til at blive flyttet tilbage til den centrale placering. SharePoint og Exchange flyttes ikke.

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 multi-geo tilgængelighed

Microsoft 365 multi-geo tilbydes i øjeblikket i disse områder og lande:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Introduktion

Følg disse trin for at komme i gang med multi-geo:

1. Arbejd med dit kontoteam for at _tilføje Multi-Geo Capabilities i Microsoft 365_ serviceabonnement. De hjælper dig med at tilføje det nødvendige antal licenser. Multi-Geo-funktionen er tilgængelig for EA-kunder med mindst 250 Microsoft 365-abonnementer.

   Før du kan begynde at Microsoft 365 Multi-Geo, skal Microsoft konfigurere din Exchange Online-lejer til multi-geo-support. Denne engangskonfigurationsproces udløses, når du bestiller *Multi-Geo Capabilities i Microsoft 365-serviceplanen*, og licenserne vises i din lejer. Du får arbejdsbelastningsspecifikke beskeder i [meddelelsescenteret](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) Microsoft 365, når din lejer har fuldført konfigurationsprocessen for hver arbejdsbelastning, og du kan derefter begynde at konfigurere og bruge dine Microsoft 365 Multi-Geo-funktioner. Den tid, det kræves at konfigurere en lejer til multi-geo-support varierer fra lejer til lejer, men de fleste lejere slutter inden for en måned efter modtagelse af funktionslicenserne. Større eller mere komplekse lejere kan kræve mere tid til at fuldføre konfigurationsprocessen. Kontakt dit kontoteam for at få oplysninger om din specifikke lejer, hvis du har brug for det.

2. Læs [Planlæg dit multige geografiske miljø](plan-for-multi-geo.md).

3. Få mere [at vide om administration af et multi-geo-miljø](administering-a-multi-geo-environment.md)[, og hvordan brugerne vil opleve miljøet](multi-geo-user-experience.md).

4. Når du er klar til at konfigurere Microsoft 365 Multi-Geo, skal [du konfigurere din lejer til multi-geo](multi-geo-tenant-configuration.md).

5. [Konfigurer søgning](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Se også

[Multi-Geo i Exchange Online og OneDrive](https://Aka.ms/GoMultiGeo)

[Multi-Geo Capabilities in OneDrive and SharePoint Online](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Multi-Geo Capabilities in Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Teams oplevelse i et multi-geo-miljø](/microsoftteams/teams-experience-o365odb-spo-multi-geo)