---
title: Forbind til Microsoft 365 Government Community Cloud (GCC) med forbrugsanalyse
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9db96e9f-a622-4d5d-b134-09dcace55b6a
description: Få mere at vide om, hvordan du opretter forbindelse til data i din Microsoft 365 Government Community Cloud-lejer (GCC) ved hjælp af Microsoft 365-skabelonappen til Power BI.
ms.openlocfilehash: 3930ffe82c998797aade84e92145adac5fa2ea98
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63592316"
---
# <a name="connect-to-microsoft-365-government-community-cloud-gcc-data-with-usage-analytics"></a>Forbind til Microsoft 365 Government Community Cloud (GCC) med forbrugsanalyse

Brug følgende procedurer til at oprette forbindelse til dine data med rapporten Microsoft 365-forbrugsanalyse i en Microsoft 365 Government Community Cloud (GCC)-lejer. 

> [!NOTE]
> Denne vejledning gælder specifikt for Microsoft 365 GCC lejere. 

## <a name="before-you-begin"></a>Før du begynder

Sådan konfigurerer du Microsoft 365 til forbrugsanalyse: 

- Du skal være global Microsoft 365 for at aktivere dataindsamling. 
- Du skal bruge [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/) for at bruge skabelonfilen. 
- Du skal bruge [Power BI Pro licens](https://go.microsoft.com/fwlink/p/?linkid=845347) eller Premium kapacitet til at publicere og få vist rapporten. 

## <a name="step-1-make-you-organizations-data-available-for-the-microsoft-365-usage-analytics-report"></a>Trin 1: Gør organisationens data tilgængelige for rapporten Microsoft 365 for brugerstatistik

1. I menuen Microsoft 365 Administration du udvide navigationsmenuen, vælge **Rapporter** og derefter vælge **Brug**. 
2. På siden **Anvendelsesrapporter** i sektionen Microsoft 365 Skal du vælge **Kom i gang.** 
3. Under **Aktivér Power BI til forbrugsanalyse** skal du vælge Gør **virksomhedsforbrugsdata tilgængelige for Microsoft-Power BI** og derefter vælge **Gem**.

    ![Gør dine lejerdata tilgængelige.](../../media/usage-analytics/make-data-available.png) 



    Dette starter en proces for at gøre dine organisationers data tilgængelige for denne rapport, og du får vist en meddelelse om, at vi gør dine **data klar til Microsoft 365 til brugsanalyse**. Bemærk, at det kan tage 24 timer at gennemføre denne proces. 

4. Når organisationens data er klar, vises der en meddelelse om, at dine data nu er tilgængelige, og du får også dit **lejer-id** ved at opdatere siden. Du skal bruge lejer-id'et senere, når du forsøger at oprette forbindelse til dine lejerdata. 
 
    ![Lejer-id.](../../media/usage-analytics/tenant-id-gcc.png) 
 
    > [!IMPORTANT]
    > Når dine data er tilgængelige, skal du ikke vælge **Gå Power BI**, hvilket vil tage dig til Power BI Marketplace.  Skabelonappen til denne rapport, der kræves af GCC lejere, er ikke tilgængelig på Power BI Marketplace.  


## <a name="step-2-download-the-power-bi-template-connect-to-your-data-and-publish-the-report"></a>Trin 2: Downloade Power BI, oprette forbindelse til dine data og publicere rapporten

Microsoft 365 GCC brugere kan downloade og bruge rapportskabelonfilen Microsoft 365 til at oprette forbindelse til deres data. Du skal Power BI Desktop at åbne og bruge skabelonfilen. 

 > [!NOTE]
 > I øjeblikket er en skabelonapp til rapporten Microsoft 365-forbrugsanalyse ikke tilgængelig for GCC lejere på Power BI Marketplace.  

1. Når du har [downloadet Power BI,](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit) skal du åbne den ved hjælp Power BI Desktop. 
2. Når du bliver bedt om **et TenantID**, skal du angive det lejer-id, du modtog, da du forberedte organisationens data til denne rapport i trin 1. Vælg derefter **Indlæs**. Det tager flere minutter, før dine data er indlæst. 

    ![Angiv lejer-id.](../../media/usage-analytics/add-tenant-id.png) 



3. Når indlæsningen er fuldført, vises rapporten, og der vises en oversigt over dine data. 

    ![Ledelsesresume.](../../media/usage-analytics/exec-summary.png) 
 

4. Gem ændringerne i rapporten. 
5. Vælg **Publicer** i Power BI Desktop for at publicere rapporten på Power BI Online, hvor den kan vises. Dette kræver enten en Power BI Pro licens eller Power BI Premium kapacitet. Som en del af [publiceringsprocessen](/power-bi/create-reports/desktop-upload-desktop-files#to-publish-a-power-bi-desktop-dataset-and-reports) skal du vælge en destination for at publicere til et tilgængeligt arbejdsområde Power BI onlinetjenesten.

## <a name="related-content"></a>Relateret indhold

[Om forbrugsanalyse](usage-analytics.md) </br>
[Hent den nyeste version af forbrugsanalyse](get-the-latest-version-of-usage-analytics.md) </br>
[Naviger i og brug rapporterne Microsoft 365 til forbrugsanalyse](navigate-and-utilize-reports.md) </br>