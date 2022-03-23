---
title: Opret et indholdscenter i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.custom: admindeeplinkSPO
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du opretter et indholdscenter i Microsoft SharePoint Syntex.
ms.openlocfilehash: 0bab102ae440b8cf2c797458e7602c61794d0d06
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588263"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>Opret et indholdscenter i Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

Hvis du vil oprette og administrere dokumentforståelsesmodeller, skal du først have et indholdscenter. Indholdscenter er grænsefladen til oprettelse af modeller og indeholder også oplysninger om, hvilke dokumentbiblioteker publicerede modeller er blevet anvendt på.

   ![Vælg et dokumentbibliotek.](../media/content-understanding/content-center-page.png)

Du opretter et standardindholdscenter under [installationen](set-up-content-understanding.md). Men en SharePoint administrator kan også vælge at oprette flere centre efter behov. Mens et enkelt indholdscenter kan være fint for miljøer, hvor du vil have en opsnulning af alle modelaktiviteter, kan det være en god ide at have flere centre for flere afdelinger i organisationen, som kan have forskellige behov og tilladelseskrav til deres modeller.

Hvis du vil prøve en SharePoint Syntex, kan du desuden oprette et indholdscenter ved hjælp af instruktionerne i denne artikel uden at købe licenser. Brugere uden licens kan oprette dokumentforståelse for modeller, men de kan ikke anvende dem i et dokumentbibliotek.

> [!NOTE]
> Hvis du Microsoft 365 standardindholdscenter på din centrale placering i et Microsoft 365 [Multi-Geo-miljø](../enterprise/microsoft-365-multi-geo.md), kan du kun give en opsnulning af modelaktivitet fra den pågældende placering. Du kan i øjeblikket ikke få en opslulning af modelaktivitet på tværs af farmgrænser i multi-geo-miljø. 

## <a name="create-a-content-center"></a>Opret et indholdscenter

En SharePoint administrator kan oprette et indholdscenterwebsted, ligesom de opretter et hvilket som [SharePoint websted](/sharepoint/create-site-collection) via administrationscenterets panel for klargøring af websteder.

Sådan opretter du et nyt indholdscenter:

1. På Microsoft 365 Administration skal du gå <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">til SharePoint Administration > **Aktive websteder**</a>.

2. Klik på **Opret på** **siden Aktive websteder**, og vælg derefter **Andre indstillinger**.

3. Vælg **Indholdscenter i** menuen **Vælg en skabelon**.

4. Angiv Webstedsnavn, Primær administrator **og et** **Sprog for** det nye **websted**.</br>

   > [!NOTE] 
   > Du kan vælge et websted til indholdscenter, der skal gengives på et hvilket som helst af de tilgængelige sprog, men bemærk, at modeller i øjeblikket kun kan oprettes til engelske filer. Bemærk også, at ligesom andre webstedsskabeloner kan standardsproget for webstedet ikke redigeres, efter webstedet er oprettet.

5. Vælg **Udført**.
 
Når du har oprettet et indholdscenterwebsted, vises det på <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive**</a> websteder i SharePoint Administration. 

### <a name="give-access-to-additional-users"></a>Give adgang til flere brugere
 
Når du har oprettet webstedet, kan du give flere brugere adgang til webstedet via [standardtilladelsesmodellen SharePoint webstedet](/sharepoint/modern-experience-sharing-permissions).

### <a name="roll-up-of-models-in-the-default-content-center"></a>Opsnulning af modeller i standardindholdscenteret

I SharePoint Syntex er det første indholdscenter, der blev oprettet under installationen *, standardindholdscenteret*. Hvis efterfølgende indholdscentre oprettes, vises deres modeller i standardvisningen for indholdscenter.

![Skærmbillede af biblioteket Model i standardindholdscenteret.](../media/content-understanding/model-library-default-content-center.png)

Biblioteket **Modeller** i standardvisningen af indholdscenter grupperer de oprettede modeller efter indholdscenter for at få en oversigtsvisning af alle dokumenter, der forstå modeller og modeller til formularbehandling, der er blevet oprettet.

> [!NOTE]
> Du kan ikke ændre det angivne standardindholdscenter. Det er altid det første indholdscenter, der oprettes under installationen. 

## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en extractor](create-an-extractor.md)

[Opret et indholdscenter](create-a-content-center.md)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Oprette en formularbehandlingsmodel](create-a-form-processing-model.md)

[Anvend en model](apply-a-model.md)