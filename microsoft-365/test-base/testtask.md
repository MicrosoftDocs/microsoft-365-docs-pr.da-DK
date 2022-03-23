---
title: Angive dine testopgaver
description: Angive dine testopgaver
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 8255cadfa77dec222527c79caf4d8737abfe2b8c
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63593320"
---
# <a name="step-4-the-tasks-tab"></a>Trin 4: Fanen Opgaver

På fanen Opgaver forventes det, at du skal angive stier til dine testscripts, som findes i den zip-mappe, du har uploadet, under fanen Binære.

  - **Out of Box Test-scripts:** Skriv de relative stier til din installation, start, luk og fjern scripts. Du har også mulighed for at vælge yderligere indstillinger for installationsscriptet.
  - **Funktionstestscripts:** Skriv den relative sti til hvert funktionelle testscript, der uploades. Yderligere funktionelle testscripts kan tilføjes ved hjælp af ```Add Script``` knappen. Du skal bruge mindst ét (1) script og kan tilføje op til otte (8) funktionelle testscripts. 
  
    Scripterne kører i den rækkefølge, de vises i. En fejl i et bestemt script forhindrer efterfølgende scripts i at blive udført.
    Du kan også vælge yderligere indstillinger for hvert script.

## <a name="set-script-path"></a>Angiv scriptsti

![Billede af testopgave.](Media/testtask.png)

Eksempel på, hvordan du angiver den relative sti i en mappestruktur nedenfor:

_**Zip_file_uploaded**_
~~~
├── file1.exe

├── ScriptX.ps1

├── folder1

│   ├── file3.exe

│   ├── script.ps1
~~~
  - **ScriptX.ps1** ville have gjort det. _ScriptX.ps1_ den relative sti.
  - **Script.ps1** ville have _mappe1/script.ps1_ som den relative sti.


## <a name="next-steps"></a>Næste trin

Få vist detaljer under fanen Testindstillinger i næste artikel 
> [!div class="nextstepaction"]
> [Næste trin](testoptions.md)
