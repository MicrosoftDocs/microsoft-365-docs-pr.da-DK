---
title: Indsaml diagnostiske data til overholdelse af regler og Microsoft Defender Antivirus
description: Brug et værktøj til at indsamle data til fejlfinding af problemer med overholdelse af regler og standarder ved Microsoft Defender Antivirus tilføjelsesprogrammet Bedømmelse.
keywords: fejlfinding, fejl, rettelse, opdateringsoverholdelse, oms, monitor, rapport, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 9e368f2cb3cecf9359c4aed5e727aef2ee21c02b
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63606498"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-antivirus-assessment"></a>Indsamle diagnostiske data om overholdelse af opdatering til Microsoft Defender Antivirus vurdering


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I denne artikel beskrives det, hvordan du indsamler diagnostiske data, der kan bruges af Microsoft support og tekniske teams til at foretage fejlfinding af problemer, der kan opstå, når du bruger sektionen Microsoft Defender Antivirus Assessment i tilføjelsesprogrammet Opdatering af overholdelse af regler og standarder.

Før du forsøger denne proces, skal du sikre dig, at du har læst [Fejlfinding Microsoft Defender Antivirus rapportering](troubleshoot-reporting.md), opfyldt alle krav og taget andre foreslåede fejlfindingstrin.

På mindst to enheder, der ikke rapporterer eller vises i Overholdelse af opdatering, skal du hente .cab diagnosticeringsfil ved at gøre følgende:

1. Åbn en version på administratorniveau af kommandoprompten på følgende måde:

    a. Åbn **menuen Start** .

    b. Skriv **cmd**. Højreklik på **Kommandoprompt,** og vælg **derefter Kør som administrator**.

    c. Angiv administratorlegitimationsoplysninger, eller godkend anmodningen.

2. Gå til Windows Defender adresseliste. Som standard er dette `C:\Program Files\Windows Defender`.

3. Skriv følgende kommando, og tryk derefter på **Enter**

    ```Dos
    mpcmdrun -getfiles
    ```

4. Der .cab en fil, der indeholder forskellige diagnostiske logfiler. Placeringen af filen angives i outputtet i kommandoprompten. Som standard er placeringen `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

5. Kopiér disse .cab filer til en placering, der kan tilgås af Microsoft Support. Et eksempel kan være en adgangskodebeskyttet OneDrive, som du kan dele med os.

6. Send en mail ved hjælp af <a href="mailto:ucsupport@microsoft.com?subject=MDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">mailskabelonen til understøttelse af</a> overholdelse af opdatering, og udfyld skabelonen med følgende oplysninger:

    ```text
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:

    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>Se også

- [Fejlfinding Microsoft Defender Antivirus rapportering](troubleshoot-reporting.md)
