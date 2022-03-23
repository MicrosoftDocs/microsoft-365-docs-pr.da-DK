---
title: Forstå HTML-rapporten for klientanalyse
description: Få mere at vide om, hvordan du analyserer HTML-rapporten Microsoft Defender for Endpoint Client Analyzer
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
ms.openlocfilehash: ab6a23d1f2c8893a86fb6432ab9fece95a10006c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592323"
---
# <a name="understand-the-client-analyzer-html-report"></a>Forstå HTML-rapporten for klientanalyse

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

Klientanalysen frembringer en rapport i HTML-format. Få mere at vide om, hvordan du gennemgår rapporten for at identificere potentielle sensorproblemer, så du kan foretage fejlfinding af dem.

Brug følgende eksempel til at forstå rapporten.

 Eksempeloutput fra analyseatoren på en maskine, der er onboardet til udløbet Org-id og ikke når en af de nødvendige URL-adresser for Microsoft Defender til slutpunkter:

![Billede af resultat af klientanalyse.](images/147cbcf0f7b6f0ff65d200bf3e4674cb.png)

- Øverst er scriptversionen og script-kørselstidspunktet angivet som reference
- Afsnittet **Enhedsoplysninger** indeholder grundlæggende OS- og enheds-id'er, der entydigt identificerer den enhed, som analyseenheden har kørt.
- **Endpoint Security Details giver** generelle oplysninger om Microsoft Defender til slutpunktsrelaterede processer, herunder Microsoft Defender Antivirus og sensorprocessen. Hvis vigtige processer ikke er online som forventet, ændres farven til rød.

  ![Billede af detaljeret resultat for klientanalyse](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   **Endpoint Security Details giver** generelle oplysninger om Microsoft Defender til slutpunktsrelaterede processer, herunder Microsoft Defender Antivirus og sensorprocessen. Hvis vigtige processer ikke er online som forventet, ændres farven til rød.

  ![Billede af detaljeret resultat for klientanalyse.](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   I **Kontrollér resultatoversigt** har du et aggregeret antal for fejl-, advarsels- eller informationshændelser, der er registreret af analyseatoren.

-   På **Detaljerede resultater** får du vist en liste (sorteret efter alvorsgrad) med resultaterne og vejledningen baseret på de observationer, analyseatoren har foretaget.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>Åbn en supportbillet til Microsoft, og medtag analyzer-resultaterne

Hvis du vil medtage filer med [analyseresultat ved åbning af en supportbillet](contact-support.md#open-a-service-request), skal du sørge for at bruge **sektionen Vedhæftede** filer og inkludere `MDEClientAnalyzerResult.zip` filen:

![Billede af prompt om vedhæftet fil.](images/508c189656c3deb3b239daf811e33741.png)

> [!NOTE]
> Hvis filstørrelsen er større end 25 MB, vil den supporttekniker, der er tildelt din sag, give et dedikeret sikkert arbejdsområde til overførsel af store filer til analyse.
