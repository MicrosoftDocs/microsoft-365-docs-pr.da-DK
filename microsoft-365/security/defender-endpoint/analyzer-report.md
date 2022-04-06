---
title: Forstå HTML-rapporten for klientanalyse
description: Få mere at vide om, hvordan du analyserer HTML Microsoft Defender for Endpoint Client Analyzer HTML-rapport
keywords: klientanalyserapport, html-rapport, klientanalyse
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1f843c62d44ed7c25f07568cc0ee92709fb080a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468893"
---
# <a name="understand-the-client-analyzer-html-report"></a>Forstå HTML-rapporten for klientanalyse

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Klientanalysen frembringer en rapport i HTML-format. Få mere at vide om, hvordan du gennemgår rapporten for at identificere potentielle sensorproblemer, så du kan foretage fejlfinding af dem.

Brug følgende eksempel til at forstå rapporten.

 Eksempeloutput fra analyseatoren på en maskine, der er onboardet til udløbet Org-id, og ikke når en af de påkrævede Microsoft Defender for Endpoint URL-adresser:

:::image type="content" source="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png" alt-text="Siden Resultater fra MDE Client Analyzer" lightbox="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png":::

- Øverst er scriptversionen og script-kørselstidspunktet angivet som reference
- Afsnittet **Enhedsoplysninger** indeholder grundlæggende OS- og enheds-id'er, der entydigt identificerer den enhed, som analyseenheden har kørt.
- **Sikkerhedsoplysninger om slutpunkter** indeholder generelle oplysninger Microsoft Defender for Endpoint relaterede processer, Microsoft Defender Antivirus arbejdsprocesser og sensorproces. Hvis vigtige processer ikke er online som forventet, ændres farven til rød.
  
-   **Sikkerhedsoplysninger om slutpunkter** indeholder generelle oplysninger Microsoft Defender for Endpoint relaterede processer, Microsoft Defender Antivirus arbejdsprocesser og sensorproces. Hvis vigtige processer ikke er online som forventet, ændres farven til rød.

    :::image type="content" source="images/85f56004dc6bd1679c3d2c063e36cb80.png" alt-text="Siden Kontrollér resultatoversigt" lightbox="images/85f56004dc6bd1679c3d2c063e36cb80.png":::

-   I **Kontrollér resultatoversigt** har du et aggregeret antal for fejl-, advarsels- eller informationshændelser, der er registreret af analyseatoren.

-   På **Detaljerede resultater** får du vist en liste (sorteret efter alvorsgrad) med resultaterne og retningslinjerne baseret på de observationer, analyseatoren har foretaget.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Åbn en supportbillet til Microsoft, og medtag analyzer-resultaterne

Hvis du vil medtage filer med [analyseresultat ved åbning af en supportbillet](contact-support.md#open-a-service-request), skal du sørge for at bruge **sektionen Vedhæftede** filer og inkludere `MDEClientAnalyzerResult.zip` filen:

:::image type="content" source="images/508c189656c3deb3b239daf811e33741.png" alt-text="En meddelelse om vedhæftet fil" lightbox="images/508c189656c3deb3b239daf811e33741.png":::

> [!NOTE]
> Hvis filstørrelsen er større end 25 MB, vil den supporttekniker, der er tildelt din sag, give et dedikeret sikkert arbejdsområde til overførsel af store filer til analyse.
