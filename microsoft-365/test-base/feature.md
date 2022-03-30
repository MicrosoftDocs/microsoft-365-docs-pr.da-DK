---
title: Validering af funktionsopdatering
description: Oplysninger om, hvordan du overfører dit program til validering af funktionsopdateringer
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
ms.openlocfilehash: f6e7cfffb92f64d92a4ad68d93d1d51dccc0f4bb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63599468"
---
# <a name="windows-feature-update-validation"></a>Windows funktionsopdatering

Har du brug for viden om, hvordan dine programmer fungerer med den næste version af Windows 10 eller Windows 11 – uden at du opretholder et miljø til at validere nye Windows funktioner? 

Vil du køre dine valideringstests mod Windows Insider Program-builds i vores Azure-miljø?

**Validering af** funktionsopdateringer på Test Base til M365 kan hjælpe dig med at opnå alt dette og meget mere!

Se den trinvise disposition nedenfor for at finde ud af, hvordan du får adgang til denne nye funktion i Test Base til M365-tjeneste.

For at komme i gang ```Feature update validation``` med i Test Base til M365 skal du uploade dine programmer (og relaterede filer) via selvbetjeningsportalen til onboarding. 

Nedenfor er de trin, du skal udføre, når du udfylder **oplysningerne om testen**:

1. Vælg **Funktionsopdatering** som opdateringstype for operativsystemet:

![Funktionsopdateringsvalidering af OS-type.](Media/Feature-update-validation-01.png)

2. Vælg den Windows Insider Channel, som du vil validere dit program med.  

![Validering af funktionsopdatering. Valg af Insider-betakanalen.](Media/Feature-update-validation-02.png)

3. Vælg en markedsudgivelse af Windows 10 eller Windows 11 som grundlinje for din test (og resulterende indsigt!), og angiv de andre oplysninger, der er nødvendige for at få pakken installeret korrekt.

![Validering af funktionsopdateringer med udgivne versioner Windows 10 og Windows 11.](Media/Feature-update-validation-03.png)

4. Hvis du vil have vist resultaterne fra valideringen af dit program mod foreløbige Windows 10 funktionsopdateringer, skal du gå til ```Feature Updates Test Results```.

![Validering af funktionsopdateringer giver dig mulighed for at gennemse resultater hurtigt.](Media/Feature-update-validation-04.png)


## <a name="next-steps"></a>Næste trin

Gå frem til næste artikel for at komme i gang med at forstå regressionsanalyse af hukommelse.
> [!div class="nextstepaction"]
> [Næste trin](memory.md)

<!---
Add button for next page
-->
