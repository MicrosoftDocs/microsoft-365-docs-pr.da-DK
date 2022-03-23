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
description: Få mere at vide om, hvordan du får mere at vide om, hvordan dine modeller til dokumentforståelse og formularbehandling fungerer.
ms.openlocfilehash: ddd4d602deae0fb871989e4739470a19b97b0238
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63594341"
---
# <a name="analyze-how-your-models-are-used-in-microsoft-sharepoint-syntex"></a>Analysér, hvordan dine modeller bruges i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GnhX]  

</br>


Dit SharePoint Syntex-indholdscenter giver dig model for forbrugsanalyser for at få flere oplysninger om, hvordan dine modeller, der er blevet publiceret fra indholdscenter, bruges. Sektionen Sådan fungerer dine modeller inden for de seneste <b>30</b> dage i indholdscenteret omfatter en 30 dages opsvulning af forbrugsanalysedata, der er angivet i følgende diagrammer og lister:

- Klassificering efter model
- Klassificering efter bibliotek
- Modelforbrug 

 ![Modelanalyse.](../media/content-understanding/model-analytics.png) </br>

### <a name="roll-up-of-model-usage-data-in-the-default-content-center"></a>Opsnulning af modelforbrugsdata i standardindholdscenteret

I SharePoint Syntex oprettes standardindholdscenteret under installationen. Yderligere indholdscentre kan også oprettes efter behov. Afdelinger kan f.eks. oprette deres egne indholdscentre for at oprette og administrere deres modeller. 

Hvad angår modelforbrugsanalyse, skal du bemærke, at:

- Dit standardindholdscenter viser modelforbrugsanalyser for alle indholdscentre og -modeller i din organisation, herunder dem, der er oprettet i yderligere indholdscentre. Dette giver indholdsledere og andre interessenter en centraliseret portal til at administrere og overvåge indholdscentre og modeller i hele virksomheden.  
- Andre indholdscenter viser kun modelforbrugsanalyser for de modeller, der blev oprettet i dem. Dette giver indholdsledere indsigt i brugsdata kun for de modeller, de vedrører.


## <a name="classification-by-model"></a>Klassificering efter model

   ![Samlet modelprocent.](../media/content-understanding/total-model-percentage.png) </br>

**Cirkeldiagrammet Klassificering efter model** viser, hvilke modeller der har klassificeret de fleste filer. Den viser hver publiceret model som en procentdel af de samlede filer, der behandles af alle publicerede modeller i indholdscenteret.

Hver model viser også **fuldstændighedshastigheden**, procentdelen af uploadede filer, der blev analyseret af modellen. En lav fuldstændighedshastighed kan betyde, at der er problemer med enten modellen eller de filer, der analyseres.

## <a name="classification-by-library"></a>Klassificering efter bibliotek

   ![Filer, der behandles.](../media/content-understanding/files-processed-over-time.png) </br>

Det **liggende søjlediagram** Klassificering efter bibliotek hjælper dig med at bestemme effektiviteten af indholdsforståelse i organisationen.  Den viser dig ikke kun antallet af filer, der er blevet behandlet over tid for hver model, men ved at vælge en kolonne i diagrammet viser den dig også de dokumentbiblioteker, som modellen blev anvendt på.


## <a name="model-usage"></a>Modelforbrug

Listen Modelforbrug viser forbrugsanalyser for de modeller, der er oprettet via indholdscenter.  

> [!NOTE]
> Hvis du er i standardindholdscenteret og har flere indholdscentre i organisationen, grupperes modellens brugsliste efter indholdscenter.

Hver model på listen over modelforbrug viser forbrugsdataene:

- Klassificeret elementantal: Antal filer, der behandles af modellen.
- Gennemsnitlig nøjagtighedsscore: Gennemsnitlig nøjagtighed for modellen, når den køres mod filer.
- URL-adresse til målliste: SharePoint dokumentbibliotek, som modellen er anvendt på.



## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en extractor](create-an-extractor.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Oprette en formularbehandlingsmodel](create-a-form-processing-model.md)  
