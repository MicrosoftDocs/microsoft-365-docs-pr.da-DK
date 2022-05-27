---
title: Analysér, hvordan dine modeller bruges i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du kan finde flere oplysninger om, hvordan dine modeller til dokumentforståelse og formularbehandling klarer sig.
ms.openlocfilehash: 830a56ab4dd0145f1385d628405ee4287de19595
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754748"
---
# <a name="analyze-how-your-models-are-used-in-microsoft-sharepoint-syntex"></a>Analysér, hvordan dine modeller bruges i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


Dit SharePoint Syntex indholdscenter giver dig modelanvendelsesanalyser, så du kan få flere oplysninger om, hvordan dine modeller, der er blevet publiceret fra indholdscenteret, bruges. Afsnittet <b>Sådan klarer dine modeller sig i de sidste 30 dage i</b> indholdscentret, indeholder en 30-dages opløftet brugsanalyse, der er angivet i følgende diagrammer og lister:

- Klassificering efter model
- Klassificering efter bibliotek
- Modelanvendelse 

 ![Modelanalyse.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Opløft af modelanvendelsesdata i standardindholdscenteret

I SharePoint Syntex oprettes standardindholdscenteret under konfigurationen. Der kan også oprettes flere indholdscentre efter behov. Afdelinger kan f.eks. oprette deres egne indholdscentre for at oprette og administrere deres modeller. 

Med hensyn til brugsanalyse af modellen skal du være opmærksom på, at:

- Dit standardindholdscenter viser modelanvendelsesanalyser for alle indholdscentre og modeller i din organisation, herunder dem, der er oprettet i andre indholdscentre. Dette giver indholdsadministratorer og andre interessenter en central portal til administration og tilsyn med indholdscentrene og -modellerne på tværs af virksomheden.  
- Andre indholdscentre viser kun modelanvendelsesanalyser for de modeller, der blev oprettet i dem. Dette giver indholdsadministratorer indsigt i forbrugsdata for kun de modeller, de arbejder med.


## <a name="classification-by-model"></a>Klassificering efter model

   ![Samlet modelprocentdel.](../media/content-understanding/total-model-percentage.png) </br>

Cirkeldiagrammet **Klassificering efter model** viser, hvilke modeller der har klassificeret flest filer. Den viser hver publiceret model som en procentdel af det samlede antal filer, der behandles af alle publicerede modeller i indholdscenteret.

Hver model viser også **fuldførelseshastigheden**, procentdelen af uploadede filer, der blev analyseret af modellen. En lav fuldstændighedsrate kan betyde, at der er problemer med enten modellen eller de filer, der analyseres.

## <a name="classification-by-library"></a>Klassificering efter bibliotek

   ![Behandlede filer.](../media/content-understanding/files-processed-over-time.png) </br>

Søjlediagrammet **Klassificering efter bibliotek** hjælper dig med at bestemme effektiviteten af forståelsen af indhold i din organisation.  Det viser ikke kun antallet af filer, der behandles over tid for hver model, men ved at vælge en kolonne i diagrammet, vises også de dokumentbiblioteker, som modellen blev anvendt på.


## <a name="model-usage"></a>Modelanvendelse

På listen Modelanvendelse vises forbrugsanalyser for de modeller, der er oprettet via indholdscenteret.  

> [!NOTE]
> Hvis du befinder dig i standardindholdscenteret og har flere indholdscentre i din organisation, grupperes listen over modelanvendelser efter indholdscenter.

Hver model på listen over modelanvendelser viser forbrugsdataene:

- Antal klassificerede elementer: Antallet af filer, der behandles af modellen.
- Gennemsnitlig konfidensscore: Modellens gennemsnitlige nøjagtighedsscore, når den køres på filer.
- URL-adresse til destinationsliste: Det SharePoint dokumentbibliotek, som modellen anvendes på.



## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsfunktion](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Opret en model for formularbehandling](create-a-form-processing-model.md)  
