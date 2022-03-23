---
title: Brug term store-taksonomi, når du opretter en extractor i Microsoft SharePoint Syntex
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
description: Brug taksonomi i ordlageret, når du opretter en extractor i din dokumentforståelsesmodel i Microsoft SharePoint Syntex.
ms.openlocfilehash: 909f26026ddf26163a12e1d14c1790f4af93a160
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589827"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Brug term store-taksonomi, når du opretter en extractor i Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

Når du opretter en uddrager i din dokumentforståelsesmodel ved hjælp af SharePoint Syntex, kan du drage fordel af globale ordsæt [](/sharepoint/managed-metadata) i ordlageret til at vise foretrukne ord for data, som du udtrækker.  

Modellen identificerer og klassificerer som eksempel alle kontraktdokumenter **, der** uploades til dokumentbiblioteket.  Desuden udtrækker modellen også en kontrakttjenesteværdi  fra hver kontrakt og viser den i en kolonne i biblioteksvisningen. Blandt de forskellige kontrakttjenesters værdier i kontrakterne er der flere ældre værdier, som din virksomhed ikke længere bruger og er blevet omdøbt til. Alle referencer til vilkårene *Design*, *Grafik eller* *Topography-kontrakttjenester* bør nu hedde *Creative*. Når modellen henter en af de forældede vilkår fra et kontraktdokument, skal den vise det aktuelle udtryk – Kreativ – i biblioteksvisningen. I eksemplet nedenfor kan vi se, at et eksempeldokument indeholder den forældede periode for *Design*, mens vi ser modellen.

   ![Ordlager.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Brug en kolonne med administrerede metadata i din extractor

Ordsæt konfigureres i ordlageret for administrerede metadatatjenester (MMS) <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>. I eksemplet nedenfor er *ordsættet Kontrakttjenester* [konfigureret](/sharepoint/managed-metadata#term-set) til at omfatte flere vilkår, herunder *Creative*.  Detaljerne for det viser, at ordet har tre synonymer (*Design*, *Grafik* og *Topografi*), og synonymerne skal oversættes til *Kreativ*. 

   ![Ordsæt.](../media/content-understanding/term-store.png)</br>

Der kan være mange grunde til, at du vil bruge et synonym i ordsættet. Der kan f.eks. være forældede ord, omdøbte ord eller variationer mellem din organisationers afdelinger til navngivning.

For at gøre det administrerede metadatafelt tilgængeligt og vælge, når du opretter din extractor i modellen, skal du tilføje det som en webstedskolonne [med administrerede metadata](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Når du har tilføjet webstedskolonnen, kan du markere den, når du opretter uddraget for modellen.

   ![Kontrakttjeneste.](../media/content-understanding/contract-services.png)</br>

Når du har anvendt modellen på dokumentbiblioteket, vises det foretrukne ord (*Creative*) i kolonnen *Creative Services*, når dokumenter uploades til biblioteket, når den finder nogen af synonymværdierne (*Design**, Grafik* og *Topografi*).

   ![Kolonnen Kontrakttjeneste.](../media/content-understanding/creative.png)</br>


## <a name="see-also"></a>Se også
[Introduktion til administrerede metadata](/sharepoint/managed-metadata#terms)

[Opret en extractor](create-an-extractor.md)

[Oprette en kolonne med administrerede metadata](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)