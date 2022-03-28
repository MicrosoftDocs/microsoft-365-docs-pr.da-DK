---
title: Upload program binære
description: Sådan kommer du i gang med at bruge Test Base til M365
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
ms.openlocfilehash: 200da9ca73bc666f3f11fc3fda95493d2c0954fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63598000"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>Trin 3: Upload dine binære, afhængigheder og scripts

På denne fane skal du uploade en enkelt zip-pakke, der indeholder dine binære, afhængigheder og scripts, der bruges til at køre din testpakke.

> [!NOTE]
> Størrelsen af zip-pakken skal være mellem mindst 10 MB og maksimalt 2 GB.

## <a name="upload-package-zip-file"></a>Upload pakke-zip-fil

:::image type="content" alt-text="Upload dine binære." source="Media/AddBinaries.png":::

  - Overførte afhængigheder kan omfatte testrammer, scripting-programmer eller data, der kan benyttes til at køre dit program eller dine testtilfælde. Eksempelvis kan du uploade Selenium og et webdriver-installationsprogram for at køre browserbaserede test.
  - Den bedste fremgangsmåde er at sikre, at dine scriptaktiviteter holdes modulære, dvs. 
    - Scriptet `Install` udfører kun installationshandlinger.
    - Scriptet `Launch` åbner kun programmet.
    - Scriptet `Close` lukker kun programmet.
    - Det valgfri `Uninstall` script fjerner kun programmet.

**I øjeblikket understøtter portalen kun PowerShell-scripts.**


## <a name="next-steps"></a>Næste trin 

Gå videre til næste artikel for at gå til Trin 4: **Angiv dine testopgaver**.
> [!div class="nextstepaction"]
> [Gå tilbage](uploadApplication.md)
> [!div class="nextstepaction"]
> [Næste trin](testtask.md)

