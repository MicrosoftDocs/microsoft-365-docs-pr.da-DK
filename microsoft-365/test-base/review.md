---
title: Gennemse
description: Gennemgå afsnittet efter onboarding.
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
ms.openlocfilehash: 3bb6ef605d360e259ef9fa91ed51da35506a2942
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63598001"
---
# <a name="step-6-review-your-selections-to-create-your-package"></a>Trin 6: Gennemse dine valg for at oprette din pakke.

1. Under denne fane viser tjenesten dine testdetaljer og kører en hurtig kontrol af fuldførelse.

    En **meddelelse om, at** **valideringen blev udført,** eller Valideringen mislykkedes, viser, om du kan fortsætte til næste trin eller ej.

2. Gennemse dine testoplysninger, og klik på knappen Opret, hvis **du er** tilfreds.

    :::image type="content" alt-text="Vis validering." source="Media/validation.png" lightbox="Media/validation.png":::

3. Dette vil onboarde din pakke til Test Base-miljøet. Hvis pakken er oprettet, udløses en automatiseret test, der bekræfter, om din pakke kan udføres korrekt på Azure.

    ![Vellykket resultat.](Media/successful.png)

    > [!NOTE]
    > Du får en meddelelse fra Azure-portalen for at informere dig om et vellykket eller mislykket pakkebekræftelse.
    >
    > Bemærk, at processen kan tage op til 24 timer, så det er sandsynligt, at din webside får timeout, hvis du ikke er aktiv på den, og dermed vil meddelelsen ikke informere dig om fuldførelsen af denne kørsel efter behov.

    - Peradventure this happens, you can view the status of your package on the **Manage packages tab** .

      :::image type="content" alt-text="Billede til administration af pakker." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - For vellykkede tests kan resultaterne ses via siderne **Testoversigt****, Sikkerhedsopdateringer** og Resultater af funktionsopdateringer med faste intervaller, der ofte starter et par dage efter din upload.
  
    - Hvis testen ikke gennemføres, skal du overføre en ny pakke. 

      Du kan hente **testlogfilerne til** yderligere analyse fra siderne **Med sikkerhedsopdateringsresultater** **og Resultatsider med funktionsopdateringer** .

    - Hvis du oplever gentagne testfejl, skal du kontakte testbasepreview@microsoft.com med oplysninger om fejlen.

## <a name="next-steps"></a>Næste trin

Se vores retningslinjer for indhold via linket nedenfor.

> [!div class="nextstepaction"]
> [Næste trin](contentguideline.md)
