---
title: Windows serverprogramtest
description: Sådan valideres med test af Windows Server-program
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
ms.openlocfilehash: 99868e53e98bded9139ecedea9c9d62e9d48fd2f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63593327"
---
# <a name="windows-server-application-testing"></a>Windows serverprogramtest

Med Test Base for Microsoft 365 kan du nu validere dine programmer mod Windows Server 2016 og 2019, herunder Server Core!

For at komme i gang med at validere dine uploadede programmer mod foreløbige opdateringer til Windows Server 2016- og 2019-operativsystemer på Test Base for Microsoft 365 skal du overholde følgende trin:

1. Log på vores selvbetjenings-onboardingportal. I navigationsmenuen til venstre skal du `Upload new package` vælge under `Package catalogue` og udfylde Oplysningerne om test.

2. Vælg `Security updates` som opdateringstype for operativsystemet:

   ![Vælg sikkerhedsopdateringer.](Media/selecting-security-updates.png)

3. Under OS-versioner, der skal testes skal du vælge de relevante os-versioner. Du kan vælge Windows versioner af Server OS eller en kombination af server- og klient-OS-versioner.

   ![Vælg OS-version.](Media/selecting-OS-versions.png)

4. Angiv andre nødvendige oplysninger, gennemse de oplysninger, der er angivet, og upload din programpakke. Efter overførslen kan du få vist pakkestatus på menufanen Administrer pakker.

5. Hvis du vil have vist testresultater og indsigt fra valideringen af dit program mod foreløbige sikkerhedsopdateringer til Windows Server 2016 og 2019, skal du gå til siden Testoversigt eller siden med resultater af sikkerhedsopdatering.

   ![Få vist testresultater.](Media/access-test-results.png)

Gå videre til næste artikel for at komme i gang med **funktionstest**
> [!div class="nextstepaction"]
> [Næste trin](functional.md)
