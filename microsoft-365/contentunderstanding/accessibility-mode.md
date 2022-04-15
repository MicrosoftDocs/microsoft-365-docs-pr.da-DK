---
title: Tilgængelighedstilstand i SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du bruger tilgængelighedsfunktioner, når du oplærer og arbejder med modeller i SharePoint Syntex.
ms.openlocfilehash: 567abb862af27457c1eb9395e32bf68d98446887
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882324"
---
# <a name="accessibility-mode-in-sharepoint-syntex"></a>Tilgængelighedstilstand i SharePoint Syntex

I [SharePoint Syntex](index.md) kan brugerne aktivere tilgængelighedstilstand i alle faser af modeltræning (mærkat, oplæring, test), når de arbejder med eksempeldokumenter. Brug af tilgængelighedstilstand kan hjælpe svagtseende brugere med at få lettere tastaturtilgængelighed, når de navigerer og navngiver elementer i dokumentfremviseren.

Dette hjælper brugerne med at bruge deres tastaturer til at navigere gennem tekst i dokumentfremviseren og høre en indtaling af ikke kun de valgte værdier, men også handlinger (f.eks. mærkning eller fjernelse af mærkning fra markeret tekst) eller forudsagte mærkatværdier, når du oplærer modellen med yderligere eksempeldokumenter. 


![Tilgængelighedstilstand.](../media/content-understanding/accessibility-mode.png)

## <a name="requirements"></a>Krav

Hvis du vil høre lyden af indtalingen, skal du sørge for at aktivere [appen Oplæser](https://support.microsoft.com/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1) i dine indstillinger for Oplæser på dit Windows 10 system.

![Slå Oplæser til.](../media/content-understanding/narrator-settings.png)

## <a name="labeling-for-keyboard-users"></a>Mærkning for tastaturbrugere

For tastaturbrugere, der bruger tilgængelighedstilstand, kan du bruge følgende taster, hvis du angiver tekst i et eksempeldokument i fremviseren:

- Fane: Flytter dig fremad og markerer det næste ord.
- Tab + Skift: Flytter dig bagud og markerer det forrige ord.
- Indtast: Navngør eller fjerner en etiket fra det markerede ord.
- Højre pil: Flytter dig fremad gennem enkelte tegn i et markeret ord.
- Venstre pil: Flytter dig tilbage gennem enkelte tegn i et markeret ord.

> [!NOTE]
> Hvis du navngiver flere ord for en enkelt etiket, skal du navngive hvert ord.


## <a name="narration"></a>Fortælling

For brugere af Oplæser, der bruger tilgængelighedstilstand, skal du bruge den samme tastaturnavigation, der er beskrevet for tastaturbrugere, til at gennemgå eksempeldokumentet i fremviseren.

Når du navigerer gennem eksempeldokumenterne og navnestrengværdierne, giver Oplæser brugeren følgende lydprompter:

- Når du bruger tastaturet til at navigere gennem dokumentfremviseren, angiver oplæserlyden den valgte streng.
- I en valgt streng angiver oplæserens lyd hvert tegn i strengen, når du markerer dem ved hjælp af venstre eller højre piletast.
- Hvis du vælger en streng, der er mærket, angiver Oplæser værdien og derefter "navngivet".  Hvis mærkatværdien f.eks. er "Contoso", angives "Costoso-mærket". 
- Hvis du under oplæringsfanen vælger en streng i dokumentfremviseren, der kun er blevet forudsagt, angiver oplæserlyden værdien og derefter "forudsagt". Dette sker, når oplæringen forudsiger en værdi i filen, der ikke stemmer overens med det, der er mærket af brugeren.
- Hvis du under oplæringsfanen vælger en streng i dokumentfremviseren, der er mærket og forudsagt, angiver oplæserlyden værdien og derefter "navngivet og forudsagt". Dette sker, når oplæringen lykkes, og der er et match mellem en forudsagt værdi og brugerbeskrivelsen.

Når en streng er mærket, eller en etiket er blevet fjernet i fremviseren, bliver du advaret om at gemme dine ændringer, før du afslutter.

## <a name="see-also"></a>Se også

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Opret en klassificering](create-a-classifier.md)










 


  
  



