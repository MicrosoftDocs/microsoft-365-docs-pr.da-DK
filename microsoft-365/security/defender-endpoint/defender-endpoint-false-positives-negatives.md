---
title: Adresser falske positive/negativer i Microsoft Defender for Endpoint
description: Få mere at vide om, hvordan du håndterer falske positiver eller falske negativer i Microsoft Defender for Endpoint.
keywords: antivirus, undtagelse, udeladelse, Microsoft Defender for Endpoint, falsk positiv, falsk negativ, blokeret fil, blokeret URL-adresse
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
- m365solution-overview
- m365solution-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: 5cae5a4b305846617130ecdf7c267ffc4ca13037
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603962"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Adresser falske positive/negativer i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

I løsninger til beskyttelse af slutpunkter er en falsk positiv en enhed, f.eks. en fil eller en proces, der blev registreret og identificeret som skadelig, selvom enheden faktisk ikke er en trussel. Et falsk negativt er et objekt, der ikke blev registreret som en trussel, selvom det rent faktisk er skadeligt. Falske positiver/negativer kan forekomme med enhver trusselsbeskyttelsesløsning, herunder [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md).

:::image type="content" source="images/false-positives-overview.png" alt-text="Definitionen af falske positive og negative på portalen Microsoft Defender for Endpoint" lightbox="images/false-positives-overview.png":::

Heldigvis kan der tages skridt til at løse og reducere denne type problemer. Hvis du får vist falske positiver/negativer i [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender), kan dine sikkerhedshandlinger udføre trin for at løse dem ved hjælp af følgende proces:

1. [Gennemse og klassificer beskeder](#part-1-review-and-classify-alerts)
2. [Gennemse afhjælpningshandlinger, der er foretaget](#part-2-review-remediation-actions)
3. [Gennemse og definer udeladelser](#part-3-review-or-define-exclusions)
4. [Send en enhed til analyse](#part-4-submit-a-file-for-analysis)
5. [Gennemse og juster dine indstillinger for trusselsbeskyttelse](#part-5-review-and-adjust-your-threat-protection-settings)

Du kan få hjælp, hvis du stadig har problemer med falske positiver/negativer, når du har udført de opgaver, der er beskrevet i denne artikel. Se [Har du stadig brug for hjælp?](#still-need-help)

:::image type="content" source="images/false-positives-step-diagram.png" alt-text="Trinnene til at håndtere falske positiver og negativer" lightbox="images/false-positives-step-diagram.png":::

> [!NOTE]
> Denne artikel er beregnet som vejledning til sikkerhedsoperatører og sikkerhedsadministratorer, der bruger [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md).

## <a name="part-1-review-and-classify-alerts"></a>Del 1: Gennemse og klassificer beskeder

Hvis du får vist en [besked](alerts.md) , der blev udløst, fordi noget blev registreret som skadeligt eller mistænkeligt, som ikke burde have været, kan du undertrykke beskeden for den pågældende enhed. Du kan også undertrykke beskeder, der ikke nødvendigvis er falske positiver, men som ikke er vigtige. Vi anbefaler, at du også klassificerer beskeder.

Administration af dine beskeder og klassificering af true/false-positive hjælper med at oplære din løsning til trusselsbeskyttelse og kan reducere antallet af falske positiver eller falske negativer over tid. Hvis du tager disse trin, hjælper det også med at reducere støj i dashboardet til sikkerhedshandlinger, så dit sikkerhedsteam kan fokusere på arbejdselementer med højere prioritet.

### <a name="determine-whether-an-alert-is-accurate"></a>Find ud af, om en besked er nøjagtig

Før du klassificerer eller undertrykker en besked, skal du afgøre, om beskeden er nøjagtig, en falsk positiv eller godartet.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Beskedkø** i navigationsruden.

3. Vælg en besked for at få flere oplysninger om beskeden. Se [Gennemse beskeder i Microsoft Defender for Endpoint](review-alerts.md).

4. Afhængigt af beskedstatus skal du udføre de trin, der er beskrevet i følgende tabel:

   |Beskedstatus|Sådan gør du|
   |---|---|
   |Beskeden er nøjagtig|Tildel beskeden, og [undersøg den](investigate-alerts.md) derefter yderligere.|
   |Beskeden er falsk positiv|1. [Klassificer beskeden](#classify-an-alert) som falsk positiv.<br/><br/>2. [Ignorer advarslen](#suppress-an-alert).<br/><br/>3. [Opret en indikator](#indicators-for-microsoft-defender-for-endpoint) for Microsoft Defender for Endpoint.<br/><br/>4. [Send en fil til Microsoft til analyse](#part-4-submit-a-file-for-analysis).|
   |Beskeden er nøjagtig, men godartet (uvæsentlig)|[Klassificer beskeden](#classify-an-alert) som en sand positiv, og [skjul derefter beskeden](#suppress-an-alert).|

### <a name="classify-an-alert"></a>Klassificer en besked

Beskeder kan klassificeres som falske positiver eller sande positiver i Microsoft 365 Defender. Klassificering af beskeder hjælper med at oplære Microsoft Defender for Endpoint, så du med tiden får vist flere sande beskeder og færre falske beskeder.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Beskedkø**, og vælg derefter en besked.

3. For den valgte besked skal du vælge **Handlinger** \> **Administrer besked**. Der åbnes en pop op-rude.

4. I afsnittet **Administrer besked** skal du vælge enten **Sand besked** eller **Falsk besked**. (Brug **beskeden Falsk** til at klassificere falsk positiv).

> [!TIP]
> Du kan få flere oplysninger om, hvordan du undertrykker beskeder, under [Administrer Microsoft Defender for Endpoint beskeder](/microsoft-365/security/defender-endpoint/manage-alerts). Og hvis din organisation bruger en SIEM-server (Security Information And Event Management), skal du også definere en undertrykkelsesregel der.

### <a name="suppress-an-alert"></a>Skjul en besked

Hvis du har beskeder, der enten er falske positiver, eller som er sande positive, men for uvæsentlige hændelser, kan du undertrykke disse beskeder i Microsoft 365 Defender. Undertrykkelse af beskeder hjælper med at reducere støj i dashboardet til sikkerhedshandlinger.

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Beskedkø** i navigationsruden.

3. Vælg en besked, som du vil undertrykke, for at åbne ruden **Detaljer** .

4. Vælg ellipsen (**...**) i ruden **Detaljer**, og **opret derefter en regel for undertrykkelse**.

5. Angiv alle indstillingerne for undertrykkelsesreglen, og vælg derefter **Gem**.

> [!TIP]
> Har du brug for hjælp til undertrykkelsesregler? Se [Undertryk en besked, og opret en ny undertrykkelsesregel](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>Del 2: Gennemse afhjælpningshandlinger

[Afhjælpningshandlinger](manage-auto-investigation.md#remediation-actions), f.eks. afsendelse af en fil for at sætte en proces i karantæne eller stoppe en proces, udføres på enheder (f.eks. filer), der registreres som trusler. Flere typer afhjælpningshandlinger forekommer automatisk gennem automatiseret undersøgelse og Microsoft Defender Antivirus:

- Sæt en fil i karantæne
- Fjern en registreringsdatabasenøgle
- Dræb en proces
- Stop en tjeneste
- Deaktiver en driver
- Fjern en planlagt opgave

Andre handlinger, f.eks. start af en antivirusscanning eller indsamling af en undersøgelsespakke, forekommer manuelt eller via [Live Response](live-response.md). Handlinger, der udføres via Live Response, kan ikke fortrydes.

Når du har gennemset dine beskeder, er dit næste trin at [gennemse afhjælpningshandlinger](manage-auto-investigation.md). Hvis der blev udført nogen handlinger som følge af falske positiver, kan du fortryde de fleste typer afhjælpningshandlinger. Du kan især:

- [Gendan en karantænefil fra Løsningscenter](#restore-a-quarantined-file-from-the-action-center)
- [Fortryd flere handlinger på én gang](#undo-multiple-actions-at-one-time)
- [Fjern en fil fra karantæne på tværs af flere enheder](#remove-a-file-from-quarantine-across-multiple-devices). Og
- [Gendan fil fra karantæne](#restore-file-from-quarantine)

Når du er færdig med at gennemse og fortryde handlinger, der er udført som følge af falske positiver, skal du fortsætte med at [gennemse eller definere undtagelser](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>Gennemse fuldførte handlinger

1. Klik på **Løsningscenter** i venstre navigationsrude i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

2. Vælg fanen **Oversigt** for at få vist en liste over udførte handlinger.

3. Vælg et element for at få vist flere oplysninger om den afhjælpningshandling, der blev udført.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>Gendan en karantænefil fra Løsningscenter

1. Klik på **Handlingscenter** i venstre navigationsrude i Microsoft 365 Defender portal.

2. Vælg en handling, du vil fortryde, under fanen **Oversigt** .

3. Vælg **Fortryd** i pop op-ruden. Hvis handlingen ikke kan fortrydes med denne metode, kan du ikke se knappen **Fortryd** . Du kan få mere at vide under [Fortryd fuldførte handlinger](manage-auto-investigation.md#undo-completed-actions).

### <a name="undo-multiple-actions-at-one-time"></a>Fortryd flere handlinger på én gang

1. Klik på **Løsningscenter** i venstre navigationsrude i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

2. Vælg de handlinger, du vil fortryde, under fanen **Oversigt** .

3. Vælg **Fortryd** i ruden til højre på skærmen.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Fjern en fil fra karantæne på tværs af flere enheder

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/autoir-quarantine-file-1.png" alt-text="Karantænefilen" lightbox="images/autoir-quarantine-file-1.png":::

1. Klik på **Løsningscenter** i venstre navigationsrude i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

2. Under fanen **Historik** skal du vælge en fil med handlingstypen **Karantænefil**.

3. I ruden til højre på skærmen skal du vælge **Anvend på X flere forekomster af denne fil** og derefter vælge **Fortryd**.

### <a name="restore-file-from-quarantine"></a>Gendan fil fra karantæne

Du kan annullere og fjerne en fil fra karantæne, hvis du har fastslået, at den er ren efter en undersøgelse. Kør følgende kommando på hver enhed, hvor filen blev sat i karantæne.

1. Åbn en kommandolinjeprompt med administratorrettigheder på enheden:

   1. Gå til **Start,** og skriv _cmd_.
   2. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

    ```console
    "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > I nogle scenarier kan **ThreatName** vises som `EUS:Win32/CustomEnterpriseBlock!cl`. Defender for Endpoint gendanner alle brugerdefinerede blokerede filer, der er sat i karantæne på denne enhed inden for de sidste 30 dage.
    >
    > En fil, der er sat i karantæne som en potentiel netværkstrussel, kan muligvis ikke genoprettes. Hvis en bruger forsøger at gendanne filen efter karantæne, er filen muligvis ikke tilgængelig. Dette kan skyldes, at systemet ikke længere har netværkslegitimationsoplysninger for at få adgang til filen. Dette er typisk et resultat af en midlertidig logon på et system eller en delt mappe, og adgangstokens er udløbet.

3. I ruden til højre på skærmen skal du vælge **Anvend på X flere forekomster af denne fil** og derefter vælge **Fortryd**.

## <a name="part-3-review-or-define-exclusions"></a>Del 3: Gennemse eller definer udeladelser

En udeladelse er en enhed, f.eks. en fil eller URL-adresse, som du angiver som en undtagelse til afhjælpningshandlinger. Den udeladte enhed kan stadig registreres, men der udføres ingen afhjælpningshandlinger på den pågældende enhed. Dvs. at den registrerede fil eller proces ikke stoppes, sendes i karantæne, fjernes eller på anden måde ændres af Microsoft Defender for Endpoint.

Hvis du vil definere udeladelser på tværs af Microsoft Defender for Endpoint, skal du udføre følgende opgaver:

- [Definer udeladelser for Microsoft Defender Antivirus](#exclusions-for-microsoft-defender-antivirus)
- [Opret "tillad"-indikatorer for Microsoft Defender for Endpoint](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Microsoft Defender Antivirus-udelukkelser gælder kun for antivirusbeskyttelse og ikke på tværs af andre Microsoft Defender for Endpoint egenskaber. Hvis du vil udelade filer bredt, skal du bruge udeladelser til Microsoft Defender Antivirus og [brugerdefinerede indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators) for Microsoft Defender for Endpoint.

Procedurerne i dette afsnit beskriver, hvordan du definerer udeladelser og indikatorer.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Undtagelser for Microsoft Defender Antivirus

Generelt skal du ikke definere undtagelser for Microsoft Defender Antivirus. Sørg for, at du definerer udeladelser sparsomt, og at du kun inkluderer de filer, mapper, processer og procesåbnede filer, der resulterer i falske positiver. Derudover skal du sørge for regelmæssigt at gennemse dine definerede undtagelser. Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) til at definere eller redigere dine antivirusudeladelser. Du kan dog bruge andre metoder, f.eks. [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) (se [Administrer Microsoft Defender for Endpoint](manage-mde-post-migration.md).

> [!TIP]
> Har du brug for hjælp til antivirusudeladelser? Se [Konfigurer og valider udeladelser for Microsoft Defender Antivirus-scanninger](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Brug Microsoft Endpoint Manager til at administrere antivirusudeladelser (for eksisterende politikker)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus**, og vælg derefter en eksisterende politik. (Hvis du ikke har en eksisterende politik, eller du vil oprette en ny politik, skal du gå til [næste procedure](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions)).

3. Vælg **Egenskaber**, og vælg **Rediger** ud for **Konfigurationsindstillinger**.

4. Udvid **Microsoft Defender Antivirus Exclusions,** og angiv derefter dine undtagelser.

5. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Brug Microsoft Endpoint Manager til at oprette en ny antiviruspolitik med udeladelser

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Slutpunktssikkerhed** \> **Antivirus** \> **+ Opret politik**.

3. Vælg en platform (f.eks **. Windows 10 og nyere**, **macOS** eller **Windows 10 og Windows Server**).

4. Som **Profil** skal du vælge **Microsoft Defender Antivirus-udeladelser** og derefter vælge **Opret**.

5. Angiv et navn og en beskrivelse til profilen, og vælg derefter **Næste**.

6. Angiv dine antivirusudeladelser under fanen **Konfigurationsindstillinger** , og vælg derefter **Næste**.

7. Hvis du bruger områdekoder i din organisation under fanen **Områdekoder** , skal du angive områdekoder for den politik, du opretter. (Se [Områdekoder](/mem/intune/fundamentals/scope-tags)).

8. Under fanen **Tildelinger** skal du angive de brugere og grupper, som politikken skal anvendes på, og derefter vælge **Næste**. Hvis du har brug for hjælp til tildelinger, skal du se [Tildel bruger- og enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profile-assign).

9. Gennemse indstillingerne under fanen **Gennemse + opret** , og vælg derefter **Opret**.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Indikatorer for Microsoft Defender for Endpoint

[Indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators) (specifikt indikatorer for kompromitteret eller IoCs) gør det muligt for dit sikkerhedsteam at definere registrering, forebyggelse og udeladelse af enheder. Du kan f.eks. angive, at visse filer skal udelades fra scanninger og afhjælpningshandlinger i Microsoft Defender for Endpoint. Eller indikatorer kan bruges til at generere beskeder for bestemte filer, IP-adresser eller URL-adresser.

Hvis du vil angive objekter som udeladelser for Microsoft Defender for Endpoint, skal du oprette "tillad"-indikatorer for disse objekter. Sådanne "tillad"-indikatorer i Microsoft Defender for Endpoint gælder for [næste generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md), [registrering og svar af slutpunkter](overview-endpoint-detection-response.md) og [automatiseret undersøgelse & afhjælpning](/microsoft-365/security/defender-endpoint/automated-investigations).

Der kan oprettes "Tillad"-indikatorer for:

- [Filer](#indicators-for-files)
- [IP-adresser, URL-adresser og domæner](#indicators-for-ip-addresses-urls-or-domains)
- [Programcertifikater](#indicators-for-application-certificates)

:::image type="content" source="images/false-positives-indicators.png" alt-text="Indikatortyperne" lightbox="images/false-positives-indicators.png":::

#### <a name="indicators-for-files"></a>Indikatorer for filer

Når du [opretter en "tillad"-indikator for en fil, f.eks. en eksekverbar fil](/microsoft-365/security/defender-endpoint/indicator-file), hjælper det med at forhindre, at filer, som din organisation bruger, blokeres. Filer kan indeholde pe-filer (portable executable), f.eks `.exe` . og `.dll` filer.

Før du opretter indikatorer for filer, skal du kontrollere, at følgende krav er opfyldt:

- Microsoft Defender Antivirus er konfigureret med cloudbaseret beskyttelse aktiveret (se [Administrer skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- Antimalware-klientversionen er 4.18.1901.x eller nyere
- Enheder kører Windows 10, version 1703 eller nyere eller Windows 11. Windows Server 2016 eller Windows Server 2019 eller Windows Server 2022
- [Funktionen Bloker eller tillad er slået til](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>Indikatorer for IP-adresser, URL-adresser eller domæner

Når du [opretter en "tillad"-indikator for en IP-adresse, EN URL-adresse eller et domæne,](/microsoft-365/security/defender-endpoint/indicator-ip-domain) hjælper det med at forhindre, at de websteder eller IP-adresser, din organisation bruger, blokeres.

Før du opretter indikatorer for IP-adresser, URL-adresser eller domæner, skal du kontrollere, at følgende krav er opfyldt:

- Netværksbeskyttelse i Defender for Endpoint er aktiveret i blokeringstilstand (se [Aktivér netværksbeskyttelse](/microsoft-365/security/defender-endpoint/enable-network-protection))
- Antimalware-klientversionen er 4.18.1906.x eller nyere
- Enheder kører Windows 10, version 1709 eller nyere eller Windows 11

Brugerdefinerede netværksindikatorer er slået til i [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Du kan få mere at vide under [Avancerede funktioner](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Indikatorer for programcertifikater

Når du [opretter en "tillad"-indikator for et programcertifikat](/microsoft-365/security/defender-endpoint/indicator-certificates), hjælper det med at forhindre, at programmer, f.eks. internt udviklede programmer, som din organisation bruger, blokeres. `.CER` eller `.PEM` filtypenavne understøttes.

Før du opretter indikatorer for programcertifikater, skal du kontrollere, at følgende krav er opfyldt:

- Microsoft Defender Antivirus er konfigureret med cloudbaseret beskyttelse aktiveret (se [Administrer skybaseret beskyttelse](deploy-manage-report-microsoft-defender-antivirus.md)
- Antimalware-klientversionen er 4.18.1901.x eller nyere
- Enheder kører Windows 10, version 1703 eller nyere eller Windows 11. Windows Server 2016 eller Windows Server 2019 eller Windows Server 2022
- Definitioner på beskyttelse af virus og trusler er opdaterede

> [!TIP]
> Når du opretter indikatorer, kan du definere dem én efter én eller importere flere elementer på én gang. Husk, at der er en grænse på 15.000 indikatorer for en enkelt lejer. Og du skal muligvis indsamle visse oplysninger først, f.eks. oplysninger om filhash. Sørg for at gennemse forudsætningerne, før du [opretter indikatorer](manage-indicators.md).

## <a name="part-4-submit-a-file-for-analysis"></a>Del 4: Send en fil til analyse

Du kan sende enheder, f.eks. filer og filløse registreringer, til Microsoft til analyse. Microsofts sikkerhedsforskere analyserer alle indsendelser, og deres resultater hjælper med at informere Microsoft Defender for Endpoint trusselsbeskyttelsesfunktioner. Når du logger på indsendelseswebstedet, kan du spore dine indsendelser.

### <a name="submit-a-file-for-analysis"></a>Send en fil til analyse

Hvis du har en fil, der enten fejlagtigt blev registreret som skadelig eller blev overset, skal du følge disse trin for at sende filen til analyse.

1. Gennemse retningslinjerne her: [Send filer til analyse](/windows/security/threat-protection/intelligence/submission-guide).

2. Besøg [webstedet for Microsoft Sikkerhedsviden indsendelse](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission), og send din eller dine filer).

### <a name="submit-a-fileless-detection-for-analysis"></a>Send en filløs registrering til analyse

Hvis noget blev registreret som malware baseret på funktionsmåde, og du ikke har en fil, kan du sende filen `Mpsupport.cab` til analyse. Du kan hente *.cab-filen* ved hjælp af værktøjet Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) på Windows 10 eller Windows 11.

1. Gå til ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`, og kør `MpCmdRun.exe` derefter som administrator.

2. Skriv `mpcmdrun.exe -GetFiles`, og tryk derefter på **Enter**.

   Der oprettes en .cab fil, der indeholder forskellige diagnosticeringslogge. Filens placering er angivet i outputtet fra kommandoprompten. Som standard er `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`placeringen .

3. Gennemse retningslinjerne her: [Send filer til analyse](/windows/security/threat-protection/intelligence/submission-guide).

4. Besøg [webstedet for Microsoft Sikkerhedsviden indsendelse](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission), og send dine .cab filer.

### <a name="what-happens-after-a-file-is-submitted"></a>Hvad sker der, når en fil er sendt?

Din indsendelse scannes straks af vores systemer for at give dig den seneste bestemmelse, selv før en analytiker begynder at håndtere din sag. Det er muligt, at en fil allerede er sendt og behandlet af en analytiker. I disse tilfælde træffes der hurtigt en afgørelse.

For indsendelser, der ikke allerede er behandlet, prioriteres de til analyse på følgende måde:

- Udbredt filer med potentiale til at påvirke et stort antal computere får en højere prioritet.
- Godkendte kunder, især virksomhedskunder med gyldige [Software Assurance-id'er (SAID'er),](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) får en højere prioritet.
- Indsendelser, der er markeret som høj prioritet af SAID-indehavere, får øjeblikkelig opmærksomhed.

Hvis du vil søge efter opdateringer vedrørende din indsendelse, skal du logge på [webstedet for Microsoft Sikkerhedsviden indsendelse](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> Du kan få mere at vide under [Send filer til analyse](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>Del 5: Gennemse og juster dine indstillinger for trusselsbeskyttelse

Microsoft Defender for Endpoint tilbyder en lang række muligheder, herunder muligheden for at finjustere indstillinger for forskellige funktioner og funktioner. Hvis du får mange falske positiver, skal du sørge for at gennemse din organisations indstillinger for trusselsbeskyttelse. Du skal muligvis foretage nogle justeringer af:

- [Skybaseret beskyttelse](#cloud-delivered-protection)
- [Afhjælpning af potentielt uønskede programmer](#remediation-for-potentially-unwanted-applications)
- [Automatiseret undersøgelse og afhjælpning](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Skybaseret beskyttelse

Kontrollér dit skybaserede beskyttelsesniveau for Microsoft Defender Antivirus. Cloudbaseret beskyttelse er som standard angivet til **Ikke konfigureret**, hvilket svarer til et normalt niveau af beskyttelse for de fleste organisationer. Hvis din skybaserede beskyttelse er indstillet til **høj**, **høj +** eller **nultolerance**, kan du opleve et højere antal falske positiver.

> [!TIP]
> Hvis du vil vide mere om konfiguration af din skybaserede beskyttelse, skal du se [Angiv det skybaserede beskyttelsesniveau](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) til at redigere eller angive dine skybaserede beskyttelsesindstillinger. Du kan dog bruge andre metoder, f.eks. [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) (se [Administrer Microsoft Defender for Endpoint](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Brug Microsoft Endpoint Manager til at gennemse og redigere skybaserede beskyttelsesindstillinger (for eksisterende politikker)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus** , og vælg derefter en eksisterende politik. (Hvis du ikke har en eksisterende politik, eller du vil oprette en ny politik, skal du gå til [næste procedure](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy)).

3. Under **Administrer** skal du vælge **Egenskaber**. Vælg derefter **Rediger** ud for **Konfigurationsindstillinger**.

4. Udvid **Cloud protection**, og gennemse din aktuelle indstilling i rækken **Cloud-leveret beskyttelsesniveau** . Vi anbefaler, at du indstiller skybaseret beskyttelse til **Ikke konfigureret**, hvilket giver stærk beskyttelse og samtidig reducerer chancen for at få falske positiver.

5. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Brug Microsoft Endpoint Manager til at angive indstillinger for skybaseret beskyttelse (til en ny politik)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus** \> **+ Opret politik**.

3. Vælg en indstilling for **Platform**, og vælg derefter **Antivirus** eller **Microsoft Defender Antivirus** for **Profil** (den specifikke indstilling afhænger af, hvad du har valgt til **Platform**). Vælg derefter **Opret**.

4. Under fanen **Grundlæggende** skal du angive et navn og en beskrivelse af politikken. Vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du udvide **Cloud protection** og angive følgende indstillinger:

   - Angiv **Slå skybaseret beskyttelse** til **Ja**.
   - Indstil **Skybaseret beskyttelsesniveau** til **Ikke konfigureret**. (Dette niveau giver et stærkt niveau for beskyttelse som standard, samtidig med at chancerne for at få falske positiver reduceres.)

6. Under fanen **Områdekoder** skal du angive områdekoder for politikken, hvis du bruger områdekoder i din organisation. (Se [Områdekoder](/mem/intune/fundamentals/scope-tags)).

7. Under fanen **Tildelinger** skal du angive de brugere og grupper, som politikken skal anvendes på, og derefter vælge **Næste**. Hvis du har brug for hjælp til tildelinger, skal du se [Tildel bruger- og enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profile-assign).

8. Gennemse indstillingerne under fanen **Gennemse + opret** , og vælg derefter **Opret**.

### <a name="remediation-for-potentially-unwanted-applications"></a>Afhjælpning af potentielt uønskede programmer

Potentielt uønskede programmer (PUA) er en kategori af software, der kan få enheder til at køre langsomt, vise uventede annoncer eller installere anden software, der kan være uventet eller uønsket. Eksempler på PUA omfatter reklame software, bundling software, og undvigelse software, der fungerer anderledes med sikkerhedsprodukter. Selvom PUA ikke betragtes som malware, nogle former for software er PUA baseret på deres adfærd og omdømme.

> [!TIP]
> Hvis du vil vide mere om PUA, skal du se [Registrer og bloker potentielt uønskede programmer](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

Afhængigt af de apps, din organisation bruger, får du muligvis falske positiver som følge af dine indstillinger for PUA-beskyttelse. Hvis det er nødvendigt, kan du overveje at køre PUA-beskyttelse i overvågningstilstand i et stykke tid eller anvende PUA-beskyttelse på et undersæt af enheder i din organisation. PUA-beskyttelse kan konfigureres til Microsoft Edge-browseren og til Microsoft Defender Antivirus.

Vi anbefaler, at du bruger [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) til at redigere eller angive indstillinger for PUA-beskyttelse. Du kan dog bruge andre metoder, f.eks. [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) (se [Administrer Microsoft Defender for Endpoint](manage-mde-post-migration.md).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>Brug Microsoft Endpoint Manager til at redigere PUA-beskyttelse (til eksisterende konfigurationsprofiler)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Profiler til enhedskonfiguration**\>, og vælg derefter en eksisterende politik. (Hvis du ikke har en eksisterende politik, eller du vil oprette en ny politik, skal du gå til [næste procedure](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile)).

3. Under **Administrer** skal du vælge **Egenskaber** og derefter vælge **Rediger** ud for **Konfigurationsindstillinger**.

4. På fanen **Konfigurationsindstillinger** skal du rulle ned og udvide **Microsoft Defender Antivirus**.

5. Angiv **Registrer potentielt uønskede programmer** til **Overvågning**. Du kan slå den fra, men ved hjælp af overvågningstilstand kan du se registreringer.

6. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>Brug Microsoft Endpoint Manager til at angive PUA-beskyttelse (til en ny konfigurationsprofil)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Enhedskonfigurationsprofiler** \>  \> **+ Opret profil**.

3. Vælg **Windows 10 og nyere** for **platformen**, og vælg **Enhedsbegrænsninger** for **Profil**.

4. Under fanen **Grundlæggende** skal du angive et navn og en beskrivelse til politikken. Vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du rulle ned og udvide **Microsoft Defender Antivirus**.

6. Angiv **Registrer potentielt uønskede programmer** til **Overvågning**, og vælg derefter **Næste**. Du kan slå PUA-beskyttelse fra, men ved hjælp af overvågningstilstand kan du se registreringer.

7. Under fanen **Tildelinger** skal du angive de brugere og grupper, som politikken skal anvendes på, og derefter vælge **Næste**. Hvis du har brug for hjælp til tildelinger, skal du se [Tildel bruger- og enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profile-assign).

8. Under fanen **Anvendelighedsregler** skal du angive de operativsystemversioner, der skal medtages eller udelades fra politikken. Du kan f.eks. angive, at politikken skal anvendes på alle enheder visse udgaver af Windows 10. Vælg derefter **Næste**.

9. Gennemse dine indstillinger under fanen **Gennemse + opret** , og vælg derefter **Opret**.

### <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

[Automatiserede funktioner til undersøgelse og afhjælpning](automated-investigations.md) (AIR) er designet til at undersøge beskeder og straks træffe foranstaltninger til at løse brud. Når beskeder udløses, og der køres en automatisk undersøgelse, genereres der en dom for hvert bevis, der undersøges. Dommene kan være *Ondsindede*, *Mistænkelige* eller *Ingen trusler fundet*.

Afhængigt af det [automatiseringsniveau](/microsoft-365/security/defender-endpoint/automation-levels) , der er angivet for din organisation og andre sikkerhedsindstillinger, udføres afhjælpningshandlinger på artefakter, der anses for at være *skadelige* eller *mistænkelige*. I nogle tilfælde sker afhjælpningshandlinger automatisk. i andre tilfælde udføres afhjælpningshandlinger manuelt eller kun efter godkendelse af dit team for sikkerhedshandlinger.

- [Få mere at vide om automatiseringsniveauer](/microsoft-365/security/defender-endpoint/automation-levels). og derefter
- [Konfigurer AIR-funktioner i Defender for Endpoint](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> Vi anbefaler, at du bruger *Fuld automatisering* til automatiseret undersøgelse og afhjælpning. Slå ikke disse egenskaber fra på grund af et falsk positivt. Brug i stedet ["tillad"-indikatorer til at definere undtagelser](#indicators-for-microsoft-defender-for-endpoint) og sørge for, at automatisk undersøgelse og afhjælpning er indstillet til automatisk at udføre relevante handlinger. Hvis du følger [denne vejledning](automation-levels.md#levels-of-automation) , hjælper det med at reducere antallet af beskeder, som sikkerhedsteamet skal håndtere.

## <a name="still-need-help"></a>Har du stadig brug for hjælp?

Hvis du har gennemgået alle trinnene i denne artikel og stadig har brug for hjælp, skal du kontakte teknisk support.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, og log på.

2. Vælg spørgsmålstegnet (**?**) i øverste højre hjørne, og vælg derefter **Microsoft Support**.

3. Beskriv dit problem i vinduet **Supportassistent** , og send derefter din meddelelse. Herfra kan du åbne en serviceanmodning.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md) 

## <a name="see-also"></a>Se også

[Administrer Microsoft Defender for Endpoint](manage-mde-post-migration.md)

[Oversigt over Microsoft 365 Defender portal](/microsoft-365/security/defender-endpoint/use)
