---
title: Udnyt taksonomi for ordbank, når du opretter en udtrækningsfunktion i Microsoft SharePoint Syntex
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Brug taksonomi for ordbank, når du opretter en udtrækningsfunktion i din dokumentforståelsesmodel i Microsoft SharePoint Syntex.
ms.openlocfilehash: d3f2acf32231558f9f56a62b18c6dd7ffbc4e20f
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861482"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Udnyt taksonomi for ordbank, når du opretter en udtrækningsfunktion i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

Når du opretter en udtrækningsmaskine i din model til dokumentforståelse ved hjælp af SharePoint Syntex, kan du drage fordel af globale ordsæt i [ordbanken](/sharepoint/managed-metadata) for at få vist foretrukne ord for de data, du udtrækker.  

Din model identificerer og klassificerer f.eks. alle **kontraktdokumenter** , der uploades til dokumentbiblioteket.  Derudover udtrækker modellen også en **kontrakttjenesteværdi** fra hver kontrakt og viser den i en kolonne i biblioteksvisningen. Blandt de forskellige Contract Services-værdier i kontrakterne er der flere ældre værdier, som din virksomhed ikke længere bruger og er blevet omdøbt. Alle referencer til vilkårene *Design*, *Grafik* eller *Topografi-kontrakttjenester* bør f.eks. nu kaldes *Creative*. Når din model udtrækker et af de forældede ord fra et kontraktdokument, skal det aktuelle udtryk – Creative – vises i biblioteksvisningen. I eksemplet nedenfor kan vi under oplæringen af modellen se, at ét eksempeldokument indeholder det forældede udtryk *Design*.

   ![Ordbank.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Brug en kolonne med administrerede metadata i udtrækningen

Ordsæt konfigureres i ordbanken for administrerede metadatatjenester i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>. I eksemplet nedenfor er [ordsættet](/sharepoint/managed-metadata#term-set) *Kontrakttjenester* konfigureret til at indeholde flere begreber, herunder *Creative*.  Oplysningerne om det viser, at ordet har tre synonymer (*Design*, *Grafik* og *Topografi*), og synonymerne skal oversættes til *Creative*. 

   ![Ordsæt.](../media/content-understanding/term-store.png)</br>

Der kan være mange grunde til, at du måske vil bruge et synonym i dit ordsæt. Der kan f.eks. være forældede ord, omdøbte ord eller variationer mellem organisationens afdelinger i forbindelse med navngivning.

Hvis du vil gøre det administrerede metadatafelt tilgængeligt, så det kan vælges, når du opretter udtrækningen i din model, skal du [tilføje det som en kolonne for webstedet med administrerede metadata](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Når du har tilføjet webstedskolonnen, kan du vælge den, når du opretter udtrækningsapparatet til din model.

   ![Kontraktservice.](../media/content-understanding/contract-services.png)</br>

Når du har anvendt din model på dokumentbiblioteket, viser kolonnen *Creative Services* det foretrukne ord (*Creative*), når udtrækningsfunktionen finder synonymværdierne (*design*, *grafik* og *topografi*).

   ![Kolonnen Kontraktservice.](../media/content-understanding/creative.png)</br>

> [!NOTE]
> Hvis ordsættet er åbent, føjes eventuelle udtrukne værdier, der ikke stemmer overens med et foretrukket ord eller en synonymværdi, som et nyt ord til roden af ordsættet. Disse nye ord kan flyttes, flettes eller gøres til synonymer i ordbanken, hvor ordsættet er placeret.

## <a name="see-also"></a>Se også
[Introduktion til administrerede metadata](/sharepoint/managed-metadata#terms)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Opret en kolonne med administrerede metadata](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)