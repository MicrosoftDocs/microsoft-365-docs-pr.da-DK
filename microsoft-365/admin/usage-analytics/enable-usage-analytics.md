---
title: Aktivér Microsoft 365 til forbrugsanalyse
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
description: Få mere at vide om, hvordan du begynder at indsamle data for din lejer Microsoft 365 skabelonappen Til brugsanalyse i Power BI.
ms.openlocfilehash: b547acc5adf312458e82108a36bbd9c0cbf60f10
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63590109"
---
# <a name="enable-microsoft-365-usage-analytics"></a>Aktivér Microsoft 365 til forbrugsanalyse

Hvis du Microsoft 365 aktivere Microsoft 365 en brugerstatistik i en Microsoft 365 lejer i Government Community Cloud (GCC), skal [du Forbind til Microsoft 365 Government Community Cloud (GCC) med forbrugsanalyse](connect-to-gcc-data-with-usage-analytics.md).

## <a name="before-you-begin"></a>Før du begynder

For at komme i Microsoft 365 med forbrugsanalyse skal du først gøre dataene tilgængelige i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> og derefter starte skabelonappen i Power BI.

## <a name="get-power-bi"></a>Få Power BI

Hvis du ikke allerede har en Power BI, kan du [tilmelde dig Power BI Pro](https://go.microsoft.com/fwlink/p/?linkid=845347). Vælg **Prøv gratis** for at tilmelde dig en prøveversion, eller **Køb nu for** at få Power BI Pro.


Du kan også udvide **Produkter for** at købe en version af Power BI.

> [!NOTE]
> Du skal have Power BI Pro licens til at installere, tilpasse og distribuere en skabelonapp. Du kan finde flere oplysninger [under Forudsætninger](/power-bi/service-template-apps-install-distribute?source=docs#prerequisites).

Hvis du vil dele dine data, skal både du og de personer, du deler dataene med, have en Power BI Pro-licens, eller indholdet skal være i et arbejdsområde i [en Power BI Premium-tjeneste](/power-bi/service-premium-what-is).

## <a name="enable-the-template-app"></a>Aktivér skabelonappen

Hvis du vil aktivere skabelonappen, skal du være **global administrator**.

Se om [administratorroller for](../add-users/about-admin-roles.md) at få flere oplysninger.

1. I Administration skal du gå til fanen **Indstillinger** \> **Org settings** \> **Services**.

2. På fanen **Tjenester** skal du vælge  **Rapporter**.

3. I panelet Rapporter, der åbnes, skal du **angive Gør rapportdata tilgængelige for Microsoft 365 for** Power BI til **Ved** \> **lagring**.

Dataindsamlingen fuldføres om to til 48 timer afhængigt af størrelsen på din lejer. Knappen **Gå til Power BI-indstillinger** aktiveres (ikke længere grå), når indsamling af data er fuldført. Når det er gjort, viser appen historiske brugsdata på organisationsniveau. 

> [!NOTE]
> Dataene til fanen "Brugeraktivitet **"** opdateres kun efter den femtente dag i den aktuelle måned og den første dag i den næste måned, så den forbliver tom i første omgang, indtil den første opdatering er fuldført.

## <a name="start-the-template-app"></a>Start skabelonappen

For at starte skabelonappen skal du enten være **global administrator****,** rapportlæser, **Exchange administrator**, **Skype for Business administrator** **eller SharePoint administrator**.

1. Kopiér lejer-id'et, **og vælg Gå til Power BI**.

2. Når du får adgang til Power BI, skal du logge på. Vælg **derefter** **AppsFå**-> apps fra navigationsmenuen.

3. På fanen **Apps** skal du Microsoft 365 i søgefeltet og derefter vælge **Microsoft 365 Forbrugsanalyse Hent** \> **den nu**.

    [![Vælg Hent den nu.](../../media/78102250-9874-4a32-8365-436f13560b52.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)

4. Når appen er installeret. Markér feltet for at åbne det.

5. Vælg **Udforsk app for** at få vist appen med eksempeldata. Vælg **Forbind** at oprette forbindelse mellem appen og din organisations data.

6. Vælg **Forbind** på **skærmbilledet Forbind til Microsoft 365-forbrugsanalyse**, skriv derefter det lejer-id (uden tankestreger), du kopierede i trin (1), og vælg **Næste**.

7. På næste skærmbillede skal du **vælge OAuth2 som** **Godkendelsesmetode Log** \> **på**. Hvis du vælger en anden godkendelsesmetode, kan der ikke oprettes forbindelse til skabelonappen.

    ![Vælg Microsoft-konto som godkendelsesmetode.](../../media/ab6f0463-c3f7-4088-a605-67c699fa86adnew.png)

8. Når skabelonappen er instantieret, Microsoft 365 dashboardet for forbrugsanalyse tilgængeligt Power BI på internettet. Den indledende indlæsning af dashboardet tager mellem 2 og 30 minutter.

Aggregater på lejerniveau vil være tilgængelige i alle rapporter, når du har tilmeldt dig. **Oplysninger på brugerniveau bliver kun tilgængelige omkring den 5. i den næste kalendermåned, efter du har tilmeldt dig**. Dette påvirker alle rapporter under Brugeraktivitet (Se Naviger i og brug rapporterne [i Microsoft 365](navigate-and-utilize-reports.md) for at få tip til, hvordan du kan få vist og bruge disse rapporter).

## <a name="make-the-collected-data-anonymous"></a>Gør de indsamlede data anonyme

Rapporter indeholder oplysninger om organisationens brugsdata. Rapporter viser som standard oplysninger med identificerbare navne for brugere, grupper og websteder. Pr. 1. september 2021 skjuler vi som standard brugeroplysninger for alle rapporter som en del af vores løbende bestræbelser på at hjælpe virksomheder med at understøtte den lokale lovgivning om beskyttelse af personlige oplysninger.
  
Globale administratorer kan vende tilbage til denne ændring for deres lejer og vise identificerbare brugeroplysninger, hvis organisationens praksis for beskyttelse af personlige oplysninger tillader det. Det kan opnås i Microsoft 365 Administration ved at følge disse trin:
  
1. I Administration skal du gå til siden **Indstillinger** \> **Org Indstillinger** \> **Services**.

2. Vælg **Rapporter**. 
  
3. Fjern markeringen i **sætningen Vis ikke-identificerede navne for brugere,** grupper og websteder i alle rapporter, og gem derefter ændringerne.  
  
Det kan tage et par minutter, før ændringerne træder i kraft. Visning af identificerbare brugeroplysninger er en logført hændelse i Microsoft 365 Overholdelsescenter overvågningsloggen.   

## <a name="related-content"></a>Relateret indhold

[Om forbrugsanalyse](usage-analytics.md) (artikel)\
[Hent den nyeste version af forbrugsanalyse](get-the-latest-version-of-usage-analytics.md) (artikel)\
[Naviger i og brug rapporterne Microsoft 365 din forbrugsanalyse](navigate-and-utilize-reports.md) (artikel)
