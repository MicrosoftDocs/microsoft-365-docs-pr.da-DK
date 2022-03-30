---
title: Onboard Windows enheder til Microsoft Defender til slutpunkt via Gruppepolitik
description: Brug Gruppepolitik til at installere konfigurationspakken på Windows enheder, så de er onboardet til tjenesten.
keywords: konfigurer enheder ved hjælp af gruppepolitik, enhedsstyring, konfigurer Microsoft Defender til slutpunktsenheder, onboard Microsoft Defender til slutpunktsenheder, gruppepolitik
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 12/07/2021
ms.technology: mde
ms.openlocfilehash: 3b20242247e33f8550ce4d153c2f2618c64d7007
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599289"
---
# <a name="onboard-windows-devices-using-group-policy"></a>Onboard Windows-enheder ved hjælp af Gruppepolitik 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**Gælder for:**

- Gruppepolitik
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsgp-abovefoldlink)

> [!NOTE]
> For at Gruppepolitik (GP)-opdateringer til at installere pakken skal du være på Windows Server 2008 R2 eller nyere.
>
> For Windows Server 2019 og Windows Server 2022 skal du muligvis erstatte NT AUTHORITY\Well-Known-System-Account med NT AUTHORITY\SYSTEM for den XML-fil, som Gruppepolitik-indstillingen opretter.

> [!NOTE]
> Hvis du bruger den nye, samlede Microsoft Defender for Endpoint-løsning til Windows Server 2012 R2 og 2016, skal du sørge for, at du bruger de nyeste ADMX-filer i din central butik for at få adgang til de korrekte politikindstillinger for Microsoft Defender til slutpunkt. Se Sådan opretter og administrerer du [Central Store til Gruppepolitik](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) administrative skabeloner i Windows og download de nyeste filer til brug med **Windows 10**.

Se [PDF-filen](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) eller [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) for at se de forskellige stier i udrulning af Defender til Slutpunkt.

1. Åbn GP-konfigurationspakkefilen (`WindowsDefenderATPOnboardingPackage.zip`), du hentede fra guiden til onboarding af tjenesten. Du kan også hente pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>:

    1. I **navigationsruden** skal du **vælge Indstillinger** >  **EndpointsDevice** >  **managementOnboarding**  > .

    1. Vælg operativsystemet.

    1. Vælg **Gruppepolitik i** feltet **Installationsmetode**.

    1. Klik **på Download** pakke, og gem .zip fil.

2. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enheden. Du skal have en mappe med *navnet OptionalParamsPolicy* og filen *WindowsDefenderATPOnboardingScript.cmd*.

3. Hvis du vil oprette et nyt gruppepolitikobjekt, [skal du åbne Gruppepolitik Management Console](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), højreklikke på **de Gruppepolitik** objekter, du vil konfigurere, og klikke på **Ny**. Skriv navnet på det nye gruppepolitikobjekt i dialogboksen, der vises, og klik på **OK**.

4. Åbn Gruppepolitik [(](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) GPMC), højreklik på det Gruppepolitik objekt (GPO), du vil konfigurere, og klik på **Rediger**.

5. I Gruppepolitik **administrationseditor** skal du **gå til Computerkonfiguration** **og derefter** Indstillinger og **derefter indstillinger for Kontrolpanel**.

6. Højreklik på Planlagte **opgaver**, peg på **Ny**, og klik derefter på **Øjeblikkelig opgave (mindst Windows 7)**.

7. I vinduet **Opgave** , der åbnes, skal du gå **til fanen** Generelt. Klik **på Skift bruger** **eller gruppe under Sikkerhedsindstillinger, og** skriv SYSTEM, og klik derefter **på Kontrollér navne** og **OK**. NT AUTHORITY\SYSTEM vises som den brugerkonto, opgaven kører som.

8. Vælg **Kør, om brugeren er logget på eller** ej, **og markér afkrydsningsfeltet Kør med højeste** rettigheder.

9. Skriv et velegnet navn til den planlagte opgave i feltet Navn (f.eks. Defender til slutpunktsinstallation).

10. Gå til fanen **Handlinger** , og vælg **Ny...** Sørg for **, at Start et** program er markeret i **feltet** Handling. Angiv UNC-stien ved hjælp af filserverens fulde domænenavn (FQDN) for den delte *WindowsDefenderATPOnboardingScript.cmd-fil* .

11. Vælg **OK,** og luk alle åbne GPMC-vinduer.

12. Hvis du vil knytte gruppepolitikobjektet til en organisationsenhed, skal du højreklikke og vælge **Sammenkæd et eksisterende gruppepolitikobjekt**. I dialogboksen, der vises, skal du vælge det Gruppepolitik objekt, du vil sammenkæde. Klik på **OK**.

> [!TIP]
> Efter onboarding af enheden kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Defender til slutpunktsenhed](run-detection-test.md).

## <a name="additional-defender-for-endpoint-configuration-settings"></a>Ekstra konfigurationsindstillinger for Defender til Slutpunkt

For hver enhed kan du angive, om der kan indsamles stikprøver fra enheden, når der foretages en anmodning via Microsoft 365 Defender at sende en fil til dybdegående analyse.

Du kan bruge Gruppepolitik (GP) til at konfigurere indstillinger, f.eks. indstillinger for eksempeldeling, der bruges i funktionen til dybdegående analyse.

### <a name="configure-sample-collection-settings"></a>Konfigurere indstillinger for eksempelsamling

1. På GP-administrationsenheden skal du kopiere følgende filer fra konfigurationspakken:

    - _Kopiér AtpConfiguration.admx_ _til C:\\Windows\\ PolicyDefinitions_

    - _Kopiér AtpConfiguration.adml_ _til C:\\Windows\\ PolicyDefinitionsen-US\\_

    Hvis du bruger en Central Store [til Gruppepolitik administrative](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra) skabeloner, skal du kopiere følgende filer fra konfigurationspakken:

    - _Kopiér AtpConfiguration.admx til_ _\\\<forest.root\>\\\\SysVolPoliciesPolicyDefinitions\\\<forest.root\>\\\\_

    - _Kopiér AtpConfiguration.adml_ til _\\\<forest.root\>\\\\SysVolPoliciesPolicyDefinitionsen-US\\\<forest.root\>\\\\\\_

2. Åbn [administrationskonsollen Gruppepolitik,](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) højreklik på det gruppepolitikobjekt, du vil konfigurere, og klik på **Rediger**.

3. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration**.

4. Klik **på Politikker** og derefter **på Administrative skabeloner**.

5. Klik **Windows komponenter,** og klik **derefter Windows Defender ATP**.

6. Vælg at aktivere eller deaktivere eksempeldeling fra dine enheder.

> [!NOTE]
> Hvis du ikke angiver en værdi, er standardværdien at aktivere indsamling af eksempler.

## <a name="other-recommended-configuration-settings"></a>Andre anbefalede konfigurationsindstillinger

### <a name="update-endpoint-protection-configuration"></a>Opdater konfiguration for slutpunktsbeskyttelse

Efter konfiguration af onboardingscriptet skal du fortsætte med at redigere den samme gruppepolitik for at tilføje slutpunktsbeskyttelseskonfigurationer. Udfør redigeringer af gruppepolitik fra et system, der kører Windows 10 eller Server 2019, Windows 11 eller Windows Server 2022, for at sikre, at du har alle de Microsoft Defender Antivirus funktioner. Du skal muligvis lukke og genåbne gruppepolitikobjektet for at registrere konfigurationsindstillingerne for Defender ATP.

Alle politikker er placeret under `Computer Configuration\Policies\Administrative Templates`.

**Politikplacering:** \Windows Components\Windows Defender ATP

Politik|Indstilling
---|---
Aktivér\Deaktiver eksempelsamling|Aktiveret – "Aktivér eksempelsamling på maskiner" markeret

<br>

**Politikplacering:** \Windows Components\Microsoft Defender Antivirus

Politik|Indstilling
---|---
Konfigurere registrering af potentielt uønskede programmer|Aktiveret, Bloker

<br>

**Politikplacering:** \Windows Components\Microsoft Defender Antivirus\MAPS

Politik|Indstilling
---|---
Deltag i Microsoft MAPS|Aktiveret, Avancerede KORT
Send fileksempler, når yderligere analyse er påkrævet | Aktiveret, Send sikre eksempler

<br>

**Politikplacering:** \Windows Components\Microsoft Defender Antivirus\Real-time Protection

Politik|Indstilling
---|---
Slå beskyttelse i realtid fra|Deaktiveret
Aktiver overvågning af funktionsmåder|Aktiveret
Scan alle downloadede filer og vedhæftede filer|Aktiveret
Overvåg fil- og programaktivitet på din computer|Aktiveret

<br>

**Politikplacering:** \Windows Components\Microsoft Defender Antivirus\Scan

Disse indstillinger konfigurerer periodiske scanninger af slutpunktet. Vi anbefaler, at du udfører en ugentlig hurtig scanning, hvor ydeevnen er tilladt.

Politik|Indstilling
---|---
Kontrollér, om der er de nyeste sikkerhedsoplysninger om virus og spyware, før du kører en planlagt scanning |Aktiveret

<br>

**Politikplacering:** \Windows Components\Microsoft Defender Antivirus\Microsoft Defender Exploit Guard\Attack Surface Reduction

Få den aktuelle liste over reduktionsregler for angrebsoverfladen GUID'er fra implementering af reduktionsregler for angrebsoverfladen [Trin 3: Implementer ASR-regler](attack-surface-reduction-rules-deployment-implement.md). Du kan finde flere oplysninger om de forskellige regler under [Reference til begrænsningsregler for angrebsoverfladen](attack-surface-reduction-rules-reference.md)

1. Åbn politikken **Konfigurer reduktion af angrebsoverfladen** .

1. Vælg **Aktiveret**.

1. Vælg **knappen** Vis.

1. Tilføj hvert GUID i **feltet Værdinavn** med en værdi på 2.

   Dette konfigurerer hver enkelt kun til overvågning.

   ![Billede af konfiguration af reduktion af angrebsoverfladen.](images/asr-guid.png)

Politik|Placering|Indstilling
---|---|---
Konfigurere styret mappeadgang| \Windows Components\Microsoft Defender Antivirus\Microsoft Defender Exploit Guard\Controlled Folder Access| Aktiveret, overvågningstilstand

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenhed](run-detection-test.md).

## <a name="offboard-devices-using-group-policy"></a>Offboard-enheder, der bruger Gruppepolitik

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

1. Hent offboarding-pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>:

    1. I **navigationsruden** skal du **vælge Indstillinger** >  **EndpointsDevice** >  **managementOffboarding** > .

    1. Vælg operativsystemet.
    
    1. Vælg **Gruppepolitik i** feltet **Installationsmetode**.

    1. Klik **på Download** pakke, og gem .zip fil.

2. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enheden. Du skal have en fil med *WindowsDefenderATPOffboardingScript_valid_until_YYYY-DD.cmd-mm*.

3. Åbn Gruppepolitik [(](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) GPMC), højreklik på det Gruppepolitik objekt (GPO), du vil konfigurere, og klik på **Rediger**.

4. I **administrationseditoren Gruppepolitik** skal du gå **til Computerkonfiguration og** **derefter Indstillinger og** **derefter indstillinger for Kontrolpanel**.

5. Højreklik på Planlagte **opgaver**, peg på Ny **, og** klik derefter på **Øjeblikkelig opgave**.

6. I vinduet **Opgave** , der åbnes, skal du gå **til fanen** Generelt. Vælg den lokale SYSTEM-brugerkonto (BUILTIN\SYSTEM) under **Sikkerhedsindstillinger**.

7. Vælg **Kør, om brugeren er logget på** eller ej, **og markér afkrydsningsfeltet Kør med** højeste rettigheder.

8. Skriv et velegnet navn til den planlagte opgave i feltet Navn (f.eks. Defender til slutpunktsinstallation).

9. Gå til fanen **Handlinger** , og vælg **Ny...**. Sørg for **, at Start et** program er markeret i **feltet** Handling. Angiv UNC-stien ved hjælp af filserverens fulde domænenavn (FQDN) for den delte *WindowsDefenderATPOffboardingScript_valid_until_YYYY-mm-DD.cmd-fil* .

10. Vælg **OK,** og luk alle åbne GPMC-vinduer.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Med Gruppepolitik er der ikke mulighed for at overvåge implementering af politikker på enhederne. Overvågning kan udføres direkte på portalen eller ved hjælp af de forskellige installationsværktøjer.

## <a name="monitor-devices-using-the-portal"></a>Overvåg enheder ved hjælp af portalen

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.
2. Klik **på Lager enheder**.
3. Kontrollér, at enheder vises.

> [!NOTE]
> Det kan tage flere dage, før enhederne begynder at blive vist **på listen Enheder**. Dette omfatter den tid, det tager for politikkerne at blive distribueret til enheden, den tid, det tager for brugeren at logge på, og den tid, det tager slutpunktet at starte rapporteringen.

## <a name="setup-defender-av-policies"></a>Politikker for konfiguration af Defender AV

Opret en ny Gruppepolitik eller gruppere disse indstillinger i med de andre politikker. Dette er afhængigt af kundemiljøet, og hvordan de vil udrulle tjenesten ved at målrette forskellige organisationsenheder.

1. Når du har valgt GP eller oprettet en ny, skal du redigere GP'en.

2. Gå til **Computer** **ConfigurationPoliciesAdministrative** >  >  **Templates** >  **Windows Components** >  **Microsoft Defender Antivirus** >  **Real-time Protection**.

    :::image type="content" source="images/realtime-protect.png" alt-text="beskyttelse i realtid.":::

1. I mappen Karantæne skal du konfigurere fjernelse af elementer fra mappen Karantæne.

    :::image type="content" source="images/removal-items-quarantine1.png" alt-text="mappen til fjernelse af elementer i karantæne.":::

    :::image type="content" source="images/config-removal-items-quarantine2.png" alt-text="konfigurations-fjernelseskarantæne.":::

4. Konfigurer scanningsindstillingerne i mappen Scanning.

    :::image type="content" source="images/gpo-scans.png" alt-text="gpo-scanninger.":::

### <a name="monitor-all-files-in-real-time-protection"></a>Overvåg alle filer i beskyttelse i realtid

Gå til **Politikker for computerkonfiguration** \>  \> **–** \> **administrative skabeloner Windows komponenter** \> **Microsoft Defender Antivirus** \> **beskyttelse i realtid**.

 Da værdien for "Scan indgående og udgående filer" (standard) er 0, ændres gruppepolitikken for indstillingen "Konfigurer overvågning af indgående og udgående fil og program" for "tovejs (fuld on-access)"-indstillingen ændres til deaktiveret.

:::image type="content" source="images/config-monitor-incoming-outgoing-file-act.png" alt-text="konfigurere overvågning af aktivitet for indgående udgående fil.":::

### <a name="configure-windows-defender-smartscreen-settings"></a>Konfigurere Windows Defender smartscreen-indstillinger

1. Gå til **Politikker for computerkonfiguration** \>  \> **Administrative skabeloner** \> **Windows komponenter** \> **Windows Defender SmartScreen** \> **Explorer**.

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="Konfiguration af Windows Defender Smart-skærmstifinder.":::
 
2. Gå til **Computer** **configurationPoliciesAdministrative** >  >  **Templates** >  **Windows Components** >  **Windows Defender SmartScreen** >  **Microsoft Edge**.

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="config windows defender smart screen Edge.":::

### <a name="configure-potentially-unwanted-applications"></a>Konfigurere potentielt uønskede programmer

Gå til **Politikker for computerkonfiguration** \>  \> **, Windows** \> **dokumentkomponenter** \> **Microsoft Defender Antivirus**.

:::image type="content" source="images/config-potential-unwanted-apps.png" alt-text="konfiguration af en potentiel uønsket app.":::

:::image type="content" source="images/config-potential-unwanted-apps2.png" alt-text="konfigurer potentielt.":::

### <a name="configure-cloud-deliver-protection-and-send-samples-automatically"></a>Konfigurere skyleveringsbeskyttelse og sende eksempler automatisk

Gå til **Politikker for computerkonfiguration** \>  \> **, Windows** \> **dokumentkomponenter** \> **Microsoft Defender Antivirus** \> **MAPS**.

:::image type="content" source="images/gpo-maps1.png" alt-text="kort.":::

:::image type="content" source="images/gpo-maps-block-atfirst-sight.png" alt-text="blok ved første øjekast.":::

:::image type="content" source="images/gpo-maps-join-ms-maps.png" alt-text="deltag i Microsoft Maps.":::

:::image type="content" source="images/send-file-sample-further-analysis-require.png" alt-text="Send fileksempel, når yderligere analyse er påkrævet.":::

> [!NOTE]
> Indstillingen **Send alle eksempler** giver den mest analyse af binære/scripts/dokumenter, hvilket øger sikkerheden.
Indstillingen **Send sikre eksempler** begrænser typen af binære/scripts/dokumenter, der analyseres, og mindsker sikkerheden. 

Få mere at vide under [Aktiver skybeskyttelse i Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md) og Skybeskyttelse [og eksempelindsendelse Microsoft Defender Antivirus.](cloud-protection-microsoft-antivirus-sample-submission.md)

### <a name="check-for-signature-update"></a>Søg efter signaturopdatering

Gå til **Politikker for computerkonfiguration** \>  \> **Administrative skabeloner** \> **Windows komponenter Microsoft Defender Antivirus** \>  \> **Security Intelligence-opdateringer**.

:::image type="content" source="images/signature-update-1.png" alt-text="signaturopdatering.":::

:::image type="content" source="images/signature-update-2.png" alt-text="opdatering af signaturdefinition.":::

### <a name="configure-cloud-deliver-timeout-and-protection-level"></a>Konfigurere timeout for skyleverance og beskyttelsesniveau

Gå til **Politikker for computerkonfiguration** \>  \> **Administrative skabeloner** \> **Windows komponenter** \> **Microsoft Defender Antivirus** \> **MpEngine**.
Når du konfigurerer politik på **skybeskyttelsesniveau til Microsoft Defender Antivirus politik for blokering** af skyen, vil dette deaktivere politikken. Dette er, hvad der kræves for at angive beskyttelsesniveauet til Windows-standarden.

:::image type="content" source="images/config-extended-cloud-check.png" alt-text="konfiguration af udvidet skykontrol.":::

:::image type="content" source="images/cloud-protection-level.png" alt-text="konfiguration af skybeskyttelsesniveau.":::

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)
- [Onboarde Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender til slutpunktsenheder](run-detection-test.md)
- [Fejlfinding af onboardingproblemer i Microsoft Defender til Slutpunkt](troubleshoot-onboarding.md)
