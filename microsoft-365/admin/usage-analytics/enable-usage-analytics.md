---
title: Aktivér Microsoft 365 brugsanalyse
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Få mere at vide om, hvordan du begynder at indsamle data for din lejer ved hjælp af skabelonappen Microsoft 365 Usage Analytics i Power BI.
ms.openlocfilehash: cc2b74696dbdab416493be1909f1781b31f201a6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946940"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Aktivér Microsoft 365 brugsanalyse

Hvis du vil aktivere Microsoft 365 forbrugsanalyse i en lejer af Government Community Cloud (GCC) i Microsoft 365 USA, skal du se [Forbind til Microsoft 365 Government Community Cloud (GCC) data med Besøgsanalyse](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil i gang med Microsoft 365 forbrugsanalyse, skal du først gøre dataene tilgængelige i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> og derefter starte skabelonappen i Power BI.

## <a name="get-power-bi"></a>Hent Power BI

Hvis du ikke allerede har Power BI, kan du [tilmelde dig Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Vælg **Prøv gratis** for at tilmelde dig en prøveversion eller **Køb nu** for at få Power BI Pro.


Du kan også udvide **Produkter** for at købe en version af Power BI.

> [!NOTE]
> Du skal have en Power BI Pro licens for at installere, tilpasse og distribuere et skabelonprogram. Du kan få flere oplysninger under [Forudsætninger](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Hvis du vil dele dine data, skal både du og de personer, du deler dataene med, have en Power BI Pro licens, eller indholdet skal være i et arbejdsområde i en [Power BI Premium-tjeneste](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Aktivér skabelonappen

Hvis du vil aktivere skabelonappen, skal du være en **Global administrator**.

Se [om administratorroller](../add-users/about-admin-roles.md) for at få flere oplysninger.

1. I Administration skal du gå til fanen **Indstillinger** \> **Organisationsindstillinger** \> **Tjenester**.

2. Vælg **Rapporter** under fanen **Tjenester**.

3. I panelet Rapporter, der åbnes, skal du angive **Gør rapportdata tilgængelige for Microsoft 365 forbrugsanalyse for Power BI** til **Ved** \> **Lagring**.

Dataindsamlingsprocessen fuldføres om to til 48 timer afhængigt af størrelsen på din lejer. Knappen **Gå til Power BI** aktiveres (ikke længere grå), når dataindsamlingen er fuldført. Når det er gjort, leverer appen historiske forbrugsdata på organisationsniveau. 

> [!NOTE]
> Dataene til fanen **"Brugeraktivitet"** opdateres kun efter den 15. dag i den aktuelle måned og den første dag i den næste måned, så de forbliver tomme i starten, indtil den første opdatering er fuldført.

## <a name="start-the-template-app"></a>Start skabelonappen

Hvis du vil starte skabelonappen, skal du enten være **global administrator**, **rapportlæser**, **Exchange administrator**, **Skype for Business administrator** eller **SharePoint administrator**.

1. Kopiér lejer-id'et, og vælg **Gå til Power BI**.

2. Når du kommer til Power BI, skal du logge på. Vælg derefter **AppsHent** -> apps i navigationsmenuen.

3. Under fanen **Apps** skal du skrive Microsoft 365 i søgefeltet og derefter vælge **Microsoft 365 forbrugsanalyse** \> **Hent den nu**.

    [![Vælg Hent nu.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Når appen er installeret. Vælg feltet for at åbne det.

5. Vælg **Udforsk app** for at få vist appen med eksempeldata. Vælg **Forbind** for at oprette forbindelse mellem appen og organisationens data.

6. Vælg **Forbind**. På **skærmen Forbind til Microsoft 365 brugsanalyse** skal du skrive lejer-id'et (uden tankestreger), du kopierede i trin (1), og vælge **Næste**.

7. På det næste skærmbillede skal du vælge **OAuth2** som **godkendelsesmetode** \> **Log på**. Hvis du vælger en anden godkendelsesmetode, mislykkes forbindelsen til skabelonappen.

    ![Vælg Microsoft-konto som godkendelsesmetode.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Når skabelonappen er instantieret, vil dashboardet til Microsoft 365 forbrugsanalyse være tilgængeligt i Power BI på internettet. Den indledende indlæsning af dashboardet tager mellem 2 og 30 minutter.

Aggregeringer på lejerniveau vil være tilgængelige i alle rapporter, når du har tilvalgt. **Oplysninger på brugerniveau bliver kun tilgængelige omkring den 5. i den næste kalendermåned, efter at du har tilvalgt**. Dette påvirker alle rapporter under Brugeraktivitet (se [Naviger, og anvend rapporterne i Microsoft 365 forbrugsanalyse](navigate-and-utilize-reports.md) for at få tip til, hvordan du får vist og bruger disse rapporter).

## <a name="make-the-collected-data-anonymous"></a>Gør de indsamlede data anonyme

Rapporter indeholder oplysninger om din organisations forbrugsdata. Rapporter viser som standard oplysninger med identificerbare navne for brugere, grupper og websteder. Fra og med den 1. september 2021 skjuler vi brugeroplysninger som standard for alle rapporter som en del af vores løbende forpligtelse til at hjælpe virksomheder med at understøtte deres lokale love om beskyttelse af personlige oplysninger.
  
Globale administratorer kan gendanne denne ændring for deres lejer og vise identificerbare brugeroplysninger, hvis organisationens praksis for beskyttelse af personlige oplysninger tillader det. Det kan opnås i Microsoft 365 Administration ved at følge disse trin:
  
1. I Administration skal du gå til siden **Indstillinger** \> **Org Indstillinger** \> **Services**.

2. Vælg **Rapporter**. 
  
3. Fjern markeringen af sætningen **Vis de identificerede navne for brugere, grupper og websteder i alle rapporter,** og gem derefter dine ændringer.  
  
Det tager et par minutter, før ændringerne træder i kraft. Visning af identificerbare brugeroplysninger er en logført hændelse i overvågningsloggen til Microsoft Purview-overholdelsesportalen.   

## <a name="related-content"></a>Relateret indhold

[Om forbrugsanalyse](usage-analytics.md) (artikel)\
[Hent den nyeste version af besøgsanalysen](get-the-latest-version-of-usage-analytics.md) (artikel)\
[Naviger til og anvend rapporterne i Microsoft 365 brugsanalyse](navigate-and-utilize-reports.md) (artikel)
