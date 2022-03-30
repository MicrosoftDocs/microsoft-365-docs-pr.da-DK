---
title: Indsamle diagnostiske data for Microsoft Defender Antivirus
description: Brug et værktøj til at indsamle data til fejlfinding af Microsoft Defender Antivirus
keywords: fejlfinding, fejl, rettelse, opdateringsoverholdelse, oms, monitor, rapport, Microsoft Defender av, gruppepolitikobjekt, indstilling, diagnostiske data
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/29/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 73f07a7346edbaebe7e53cd4e17e29a5e6764073
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/25/2021
ms.locfileid: "63599356"
---
# <a name="collect-microsoft-defender-antivirus-diagnostic-data"></a>Indsaml Microsoft Defender Antivirus diagnostiske data

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I denne artikel beskrives det, hvordan du indsamler diagnostiske data, der kan bruges af Microsoft Support og tekniske teams til at foretage fejlfinding af problemer, der kan opstå, når du bruger Microsoft Defender Antivirus.

> [!NOTE]
> Som en del af undersøgelsen eller svarprocessen kan du indsamle en undersøgelsespakke fra en enhed. Sådan gør du: Samlet [undersøgelsespakke fra enheder](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices).

På mindst to enheder, der oplever det samme problem, kan du hente den .cab diagnosticeringsfil ved at gøre følgende:

1. Åbn en version på administratorniveau af kommandoprompten på følgende måde:

    a. Åbn **menuen Start** .

    b. Skriv **cmd**. Højreklik på **Kommandoprompt,** og vælg **derefter Kør som administrator**.

    c. Angiv administratorlegitimationsoplysninger, eller godkend anmodningen.

2. Gå til mappen for Microsoft Defender Antivirus. Som standard er dette `C:\Program Files\Windows Defender`.

   > [!NOTE]
   > Hvis du kører en opdateret version [af Microsoft Defender-antimalwareplatformen](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform), skal du `MpCmdRun` køre fra følgende placering: `C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`.

3. Skriv følgende kommando, og tryk derefter på **Enter**

    ```Dos
    mpcmdrun.exe -GetFiles
    ```

4. Der .cab en fil, der indeholder forskellige diagnostiske logfiler. Placeringen af filen angives i outputtet i kommandoprompten. Som standard er placeringen `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

   > [!NOTE]
   > For at omdirigere cab-filen til en anden sti eller UNC-deling skal du bruge følgende kommando:
   >
   > `mpcmdrun.exe -GetFiles -SupportLogLocation <path>`
   >
   > Få mere at vide under [Omdiriger diagnostiske data til en UNC-deling](#redirect-diagnostic-data-to-a-unc-share).

5. Kopiér disse .cab filer til en placering, der kan tilgås af Microsoft Support. Et eksempel kan være en adgangskodebeskyttet OneDrive, som du kan dele med os.

> [!NOTE]
> Hvis du har problemer med overholdelse af regler og standarder, skal du sende en mail ved hjælp af mailskabelonen Opdater overholdelse af <a href="mailto:ucsupport@microsoft.com?subject=WDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">regler</a> og standarder og udfylde skabelonen med følgende oplysninger:
>
> Jeg støder på følgende problem, når jeg bruger Microsoft Defender Antivirus i Overholdelse af opdatering:
>
> Jeg har leveret mindst 2 supportfiler .cab på følgende placering:
>
> \<accessible share, including access details such as password\>
>
> Mit OMS-arbejdsområde-id er:
>
> Kontakt mig på:

## <a name="redirect-diagnostic-data-to-a-unc-share"></a>Omdiriger diagnostiske data til en UNC-deling

Hvis du vil indsamle diagnostiske data på et centralt lager, kan du angive parameteren SupportLogLocation.

```Dos
mpcmdrun.exe -GetFiles -SupportLogLocation <path>
```

Kopierer diagnostiske data til den angivne sti. Hvis stien ikke er angivet, kopieres diagnosticeringsdataene til den placering, der er angivet i Konfiguration af supportlogplacering.

Når parameteret SupportLogLocation bruges, oprettes en mappestruktur som følger i destinationsstien:

```Dos
<path>\<MMDD>\MpSupport-<hostname>-<HHMM>.cab
```

<br>

****

|felt|Beskrivelse|
|---|---|
|sti|Stien som angivet på kommandolinjen eller hentet fra konfigurationen|
|MMDD|Måned og dag, da de diagnostiske data blev indsamlet (f.eks. 0530)|
|værtsnavn|Værtsnavnet på den enhed, som diagnostiske data blev indsamlet på|
|HHMM|Timer og minutter, da de diagnostiske data blev indsamlet (f.eks. 1422)|
|

> [!NOTE]
> Når du bruger en filshare, skal du sørge for, at den konto, der bruges til at indsamle diagnosticeringspakken, har skriveadgang til delingen.

## <a name="specify-location-where-diagnostic-data-is-created"></a>Angiv den placering, hvor diagnostiske data oprettes

Du kan også angive, hvor den .cab fil skal oprettes ved hjælp Gruppepolitik et gruppepolitikobjekt.

1. Åbn Editor til Gruppepolitik lokale placering, og find Gruppepolitikobjekt til SupportLogLocation på: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\SupportLogLocation`.

2. Vælg **Definer mappestien for at kopiere understøttede logfiler**.

   ![Skærmbillede af redigeringsprogram til lokal gruppepolitik](images/GPO1-SupportLogLocationDefender.png)

   ![Skærmbillede af indstillingen Definer sti til logfiler](images/GPO2-SupportLogLocationGPPage.png)

    ![Skærmbillede af redigeringsprogrammet til lokal gruppepolitik.](images/GPO1-SupportLogLocationDefender.png)  
        
     ![Skærmbillede af indstillingen Definer sti til logfiler.](images/GPO2-SupportLogLocationGPPage.png)  
3. I politikeditoren skal du vælge **Aktiveret**.

4. Angiv den mappesti, hvor du vil kopiere supportlogfilerne i **feltet** Indstillinger.
     ![Skærmbillede af brugerdefineret indstilling for Aktiveret mappesti.](images/GPO3-SupportLogLocationGPPageEnabledExample.png) 
5. Vælg **OK** eller **Anvend**.

## <a name="see-also"></a>Se også

- [Fejlfinding Microsoft Defender Antivirus rapportering](troubleshoot-reporting.md)
