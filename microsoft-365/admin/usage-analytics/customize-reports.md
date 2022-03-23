---
title: Tilpasse rapporterne i Microsoft 365 til forbrugsanalyse
f1.keywords:
- NOCSH
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9b76065f-29b9-4b89-8059-c5f9db9ddbf6
description: Lær at tilpasse rapporter i browseren og Power BI Desktop.
ms.openlocfilehash: 32cf44c8d72160a583a841e26c2ad6934bd7eef2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588082"
---
# <a name="customize-the-reports-in-microsoft-365-usage-analytics"></a>Tilpasse rapporterne i Microsoft 365 til forbrugsanalyse

Microsoft 365-forbrugsanalyse giver et dashboard i Power BI, der giver indsigt i, hvordan brugerne adopterer og bruger Microsoft 365. Dashboardet er blot et udgangspunkt for at interagere med forbrugsdataene. Rapporterne kan tilpasses, så du får mere personligt tilpassede indsigter.

Du kan også bruge skrivebordsversionen Power BI til yderligere at tilpasse dine rapporter ved at forbinde dem med andre datakilder for at få større indsigt i din virksomhed.

## <a name="customizing-reports-in-the-browser"></a>Tilpasning af rapporter i browseren

Følgende to eksempler viser, hvordan du redigerer et eksisterende visuelt element, og hvordan du opretter et nyt visuelt element.

### <a name="modify-an-existing-visual"></a>Rediger et eksisterende visuelt element

I dette eksempel vises det, hvordan du **ændrer fanen** Aktivering i **rapporten Aktivering/** licensering.

1. I rapporten **Aktivering/licensering** skal du vælge **fanen** Aktivering.

2. Angiv redigeringstilstand ved at vælge **knappen** Rediger øverst via knappen ![Mere side i Power BI.](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) .

    ![Klik på Rediger rapport i navigationen øverst til højre.](../../media/e2c16663-1fbd-4d7f-887c-0cbb891d3b3d.png)

3. Øverst til højre skal du vælge **Dupliker denne side**.

    ![Vælg Dupliker denne side.](../../media/b2d18dcd-6b82-4ce7-ab79-1b24e3721309.png)

4. Nederst til højre skal du vælge et af de liggende søjlediagrammer, der viser antallet af brugere, der aktiverer baseret på operativsystem som Android, iOS, Mac osv.

5. Hvis du **vil fjerne** **Mac** Count fra det visuelle element, skal du markere **X** ud for området Visualiseringer til højre.

    ![Fjern Antal Mac-computere.](../../media/ce3d8358-df57-4f64-bd25-ac5be7fc8713.png)

### <a name="create-a-new-visual"></a>Opret et nyt visuelt element

I følgende eksempel vises det, hvordan du kan oprette et nyt visuelt element til Yammer brugere på månedsbasis.

1. Gå til rapporten **Produktforbrug** ved hjælp af den venstre navigation, og **vælg Yammer** Fane.

2. Skift til redigeringstilstand ved at vælge ![knappen Flere sider i Power BI.](../../media/d8da3c19-3f2d-4bf6-811e-faa804f74770.png) og **Rediger**.

3. Nederst på siden skal du vælge fanen ![Knappen Tilføj side i Power BI.](../../media/d3b8c117-17d4-4f53-b078-8fefc2155b24.png) for at oprette en ny side.

4. I området **Visualiseringer** til højre skal du vælge **stablet liggende søjlediagram** (øverste række, først fra venstre).

    ![Vælg Liggende søjlediagram.](../../media/214c3fed-6eae-43e6-83fb-708a2d74406e.png)

5. Vælg nederst til højre i visualiseringen, og træk for at gøre den større.

6. I **området Felter** til højre skal du udvide **tabellen** Kalender.

7. Træk **MonthName** til området Felter direkte under overskriften **Akse** i **området Visualiseringer** .

    ![Træk Månedsnavn.](../../media/bff99987-8c4b-4618-89fd-47df557b0ed7.png)

8. I området **Felter** til højre skal du udvide tabellen **TenantProductUsage** .

9. Træk **FirstTimeUsers** til området Felter direkte under **overskriften** Værdi.

10. Træk **Produkt** til **området Filtre** direkte under overskriften **Filtre på visuelt** niveau.

11. I området **Filtertype**, der vises, skal du **markere Yammer** afkrydsningsfeltet.

    ![Markér Yammer afkrydsningsfelt.](../../media/82e99730-0de9-42da-928a-76aab0c3e609.png)

12. Lige under listen over visualiseringer skal du vælge **ikonet Formatér** ![i Power BI Visualizaions](../../media/ee0602f3-3df5-4930-b862-db1d90ae4ae2.png).

13. Udvid Titel, og **rediger værdien Titeltekst** **til Første gang Yammer Brugere efter måned**.

14. Rediger værdien **Tekststørrelse** til **12**.

15. Skift titlen på den nye side ved at redigere navnet på siden nederst til højre.

16. Gem rapporten ved at klikke på **Læsevisning** øverst og derefter **Gem**.

## <a name="customizing-the-reports-in-power-bi-desktop"></a>Tilpasning af rapporter i Power BI Desktop

For de fleste kunder, der redigerer rapporter og diagramvisavis i Power BI web, vil det være tilstrækkeligt. For nogle kan der dog være behov for at joinforbindelse disse data med andre datakilder for at få større indsigt i konteksten til deres egen virksomhed, i hvilket tilfælde de kan tilpasse og opbygge yderligere rapporter ved hjælp af Power BI Desktop. Du kan [downloade Power BI Desktop](https://go.microsoft.com/fwlink/p/?linkid=849797) gratis.

### <a name="use-the-reporting-apis"></a>Brug API'erne til rapportering

Du kan starte med at oprette direkte forbindelse til ODATA-API'er til rapportering fra Microsoft 365, der opretter forbindelse til disse rapporter.

1. Gå til **at hente data** \> **Andre** \> **ODATA-Forbind**\>.

2. I URL-vinduet skal du skrive "https://<i></i> reports.office.com/pbi/v1.0/\<tenantid\>"

    **BEMÆRK!** API'erne til rapportering vises i forhåndsvisning og kan blive ændret, indtil de går i produktion.

    ![URL-adresse til OData-feed Power BI skrivebord.](../../media/c0ef967e-a454-4eba-bc8e-61e113170053.png)

3. Angiv dine Microsoft 365 (organisation eller skole) administratorlegitimationsoplysninger for at godkende til Microsoft 365, når du bliver bedt om det.

    Se ofte [stillede spørgsmål](usage-analytics.md#faq) for at få flere oplysninger om, hvem der har tilladelse til at få adgang Microsoft 365 rapporter over anvendelsesskabelonappen.

4. Når forbindelsen er godkendt, får du vist vinduet Navigator, der viser de datasæt, der er tilgængelige til at oprette forbindelse til.

    Markér alle, og vælg **Indlæs**.

    Dette downloader dataene til din Power BI Desktop. Gem denne fil, og begynd derefter at oprette de rapporter, du skal bruge.

    ![ODATA-værdier, der er tilgængelige i rapporterings-API'en.](../../media/545b4d17-dbbd-4cfc-b75a-a8b27283d438.png)

### <a name="use-the-microsoft-365-usage-analytics-template"></a>Brug Microsoft 365 til forbrugsanalyse

Du kan også bruge den Power BI skabelonfil, der svarer til rapporterne Microsoft 365 for forbrugsanalyse, som et udgangspunkt til at oprette forbindelse til dataene. Fordelen ved at bruge pbit-filen er, at forbindelsesstrengen allerede er etableret for den. Du kan også drage fordel af alle de brugerdefinerede mål, der oprettes, oven i de data, som basisskemaet returnerer, og bygge videre på det.

Du kan downloade Power BI fra [Microsoft Download Center](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). Når du har downloadet Power BI, skal du følge disse trin for at komme i gang:

1. Åbn pbit-filen.

2. Angiv din lejer-id-værdi i dialogboksen.

    ![Angiv dit lejer-id for at åbne pbit-filen.](../../media/071ed0bf-8b9d-49c6-81fc-fd4c6cc85bd3.png)

3. Angiv dine administratorlegitimationsoplysninger for at godkende Microsoft 365, når du bliver bedt om det.

     for at få flere oplysninger om, hvem der har tilladelse til at Microsoft 365 rapporter over forbrugsanalyse.

    Når du har tilladelse, opdateres dataene i den Power BI fil.

    Dataindlæsning kan tage lidt tid. Når den er færdig, kan du gemme filen som en .pbix-fil og fortsætte med at tilpasse rapporterne eller hente en ekstra datakilde til denne rapport.

4. Følg [Introduktion til dokumentationen Power BI](/power-bi/fundamentals/desktop-getting-started) at forstå, hvordan du opbygger rapporter, publicerer dem på Power BI og deler med din organisation. Hvis du følger denne sti til tilpasning og deling, kan det kræve yderligere Power BI licenser. Se Power BI [for at få](https://go.microsoft.com/fwlink/p/?linkid=849803) mere at vide.
