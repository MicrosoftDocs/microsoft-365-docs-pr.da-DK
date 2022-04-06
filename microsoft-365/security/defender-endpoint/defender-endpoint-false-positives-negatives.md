---
title: Adressere falske positive/negativer i Microsoft Defender til slutpunkt
description: Få mere at vide om, hvordan du håndterer falske positive eller falske negativer i Microsoft Defender til slutpunkt.
keywords: antivirus, undtagelse, udelukkelse, Microsoft Defender til slutpunkt, falsk positiv, falsk negativ, blokeret fil, blokeret URL-adresse
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
- m365solution-scenario
- m365scenario-fpfn
ms.topic: how-to
ms.date: 12/02/2021
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs, yonghree, jcedola
ms.custom:
- FPFN
- admindeeplinkDEFENDER
ms.openlocfilehash: 0352fde9756efce3011db24c915f287c358f313b
ms.sourcegitcommit: 677dcc74aa898b2a17eb8430a32e675fea4e3fe5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63606432"
---
# <a name="address-false-positivesnegatives-in-microsoft-defender-for-endpoint"></a>Adressere falske positive/negativer i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

I slutpunktsbeskyttelsesløsninger er en falsk positiv en enhed, f.eks. en fil eller en proces, der blev registreret og identificeret som skadelig, selvom enheden faktisk ikke er en trussel. En falsk negativ er en enhed, der ikke blev registreret som en trussel, selvom den faktisk er skadelig. Falske positive/negativer kan forekomme med enhver trusselsbeskyttelsesløsning, herunder [Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md).

![Definition af falske positive og negativer i Defender for Slutpunkt.](images/false-positives-overview.png)

Der kan heldigvis tages skridt til at løse og reducere disse typer problemer. Hvis du ser falske positive/negativer [i Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender), kan dine sikkerhedshandlinger tage skridt til at løse dem ved hjælp af følgende proces:

1. [Gennemse og klassificer vigtige beskeder](#part-1-review-and-classify-alerts)
2. [Gennemse afhjælpningshandlinger, der er blevet taget](#part-2-review-remediation-actions)
3. [Gennemse og definer udeladelse](#part-3-review-or-define-exclusions)
4. [Sende en enhed til analyse](#part-4-submit-a-file-for-analysis)
5. [Gennemse og juster indstillingerne for trusselsbeskyttelse](#part-5-review-and-adjust-your-threat-protection-settings)

Du kan få hjælp, hvis du stadig har problemer med falske positive/negativer efter at have udført de opgaver, der er beskrevet i denne artikel. Se [Har du stadig brug for hjælp?](#still-need-help)

![Trin til at løse falske positive og negativer.](images/false-positives-step-diagram.png)

> [!NOTE]
> Denne artikel er beregnet som vejledning for sikkerhedsoperatorer og sikkerhedsadministratorer, der [bruger Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md).

## <a name="part-1-review-and-classify-alerts"></a>Del 1: Gennemse og klassificer beskeder

Hvis du [får vist en](alerts.md) besked, der blev udløst, fordi noget blev registreret som skadeligt eller mistænkeligt, der ikke burde have været, kan du undertrykke beskeden for den pågældende enhed. Du kan også undertrykke beskeder, der ikke nødvendigvis er falske positive, men som ikke er vigtige. Vi anbefaler, at du også klassificerer vigtige beskeder.

Administration af dine vigtige beskeder og klassificering af sand/falsk-positive hjælper dig med at oplære din løsning til trusselsbeskyttelse og kan reducere antallet af falske positive eller falske negativer over tid. Disse trin hjælper også med at reducere støj i dashboardet for sikkerhedshandlinger, så dit sikkerhedsteam kan fokusere på arbejdselementer med højere prioritet.

### <a name="determine-whether-an-alert-is-accurate"></a>Find ud af, om en besked er nøjagtig

Før du klassificerer eller undertrykker en besked, skal du afgøre, om beskeden er nøjagtig, en falsk positiv eller godartet.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg køen Beskeder i **navigationsruden**.

3. Vælg en besked for at få flere oplysninger om beskeden. (Se [Gennemse beskeder i Microsoft Defender til Slutpunkt](review-alerts.md)).

4. Afhængigt af beskedens status skal du følge de trin, der er beskrevet i følgende tabel:

   |Beskedstatus|Hvad kan du gøre?|
   |---|---|
   |Beskeden er nøjagtig|Tildel beskeden, og [undersøg den](investigate-alerts.md) derefter yderligere.|
   |Beskeden er falsk positiv|1. [Klassificer beskeden](#classify-an-alert) som en falsk positiv.<br/><br/>2. [Undertryk beskeden](#suppress-an-alert).<br/><br/>3. [Opret en indikator](#indicators-for-microsoft-defender-for-endpoint) for Microsoft Defender til slutpunkt.<br/><br/>4. [Indsend en fil til Microsoft til analyse](#part-4-submit-a-file-for-analysis).|
   |Beskeden er nøjagtig, men benlig (ikke-vigtig)|[Klassificer](#classify-an-alert) beskeden som en sand positiv, [og undertryk derefter beskeden](#suppress-an-alert).|

### <a name="classify-an-alert"></a>Klassificer en besked

Beskeder kan klassificeres som falske positive eller sande positive i Microsoft 365 Defender. Klassificering af beskeder hjælper med at træne Microsoft Defender til slutpunkt, så du med tiden får vist flere sande beskeder og færre falske beskeder.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **kø til beskeder**, og vælg derefter en besked.

3. For den markerede besked skal du vælge **Handlinger** \> **Administrer besked**. Der åbnes en pop op-rude.

4. I sektionen **Administrer besked** skal du vælge enten **Sand besked** eller **Falsk besked**. (Brug **falsk besked** til at klassificere en falsk positiv).

> [!TIP]
> Du kan finde flere oplysninger om at undertrykke beskeder i [Administrer Microsoft Defender for Endpoint-beskeder](/microsoft-365/security/defender-endpoint/manage-alerts). Og hvis din organisation bruger en sikkerhedsoplysninger og en SIEM-server (event management), skal du sørge for også at definere en undertrykkende regel der.

### <a name="suppress-an-alert"></a>Skjule en besked

Hvis du har beskeder, der enten er falske positive, eller som er sande positive, men ved ikke-vigtige hændelser, kan du undertrykke disse beskeder i Microsoft 365 Defender. Når du undertrykker beskeder, reduceres støj i dashboardet for sikkerhedshandlinger.

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg køen Beskeder i **navigationsruden**.

3. Vælg en besked, du vil skjule for at åbne **detaljeruden** .

4. Vælg **ellipsen** (**...**) i ruden Detaljer, og vælg **derefter Opret en undertrykkende regel**.

5. Angiv alle indstillinger for din undertrykkende regel, og vælg derefter **Gem**.

> [!TIP]
> Har du brug for hjælp til at undertrykke regler? Se [Undertrykke en besked og oprette en ny undertrykkende regel](/microsoft-365/security/defender-endpoint/manage-alerts#suppress-an-alert-and-create-a-new-suppression-rule).

## <a name="part-2-review-remediation-actions"></a>Del 2: Gennemse afhjælpningshandlinger

[Afhjælpningshandlinger](manage-auto-investigation.md#remediation-actions), f.eks. at sende en fil til karantæne eller stoppe en proces, bliver foretaget på enheder (f.eks filer), der registreres som trusler. Flere typer afhjælpningshandlinger sker automatisk via automatiseret undersøgelse og Microsoft Defender Antivirus:

- Sætte en fil i karantæne
- Fjern en registreringsdatabasenøgle
- Dræb en proces
- Stop en tjeneste
- Deaktiver en driver
- Fjerne en planlagt opgave

Andre handlinger, f.eks. start af en antivirusscanning eller indsamling af en undersøgelsespakke, sker manuelt eller via [Live Response](live-response.md). Handlinger, der er foretaget via Live Response, kan ikke fortrydes.

Når du har gennemset dine vigtige beskeder, er det næste trin [at gennemgå afhjælpningshandlinger.](manage-auto-investigation.md) Hvis nogen handlinger er blevet foretaget som et resultat af falske positive, kan du fortryde de fleste former for afhjælpningshandlinger. Du kan især:

- [Gendanne en fil, der er sat i karantæne, fra Handlingscenter](#restore-a-quarantined-file-from-the-action-center)
- [Fortryde flere handlinger på én gang](#undo-multiple-actions-at-one-time)
- [Fjern en fil fra karantæne på tværs af flere enheder](#remove-a-file-from-quarantine-across-multiple-devices). og
- [Gendan fil fra karantæne](#restore-file-from-quarantine)

Når du er færdig med at gennemse og fortryde handlinger, der er foretaget som et resultat af falske positive, skal du fortsætte med at gennemse [eller definere udeladelse](#part-3-review-or-define-exclusions).

### <a name="review-completed-actions"></a>Gennemse fuldførte handlinger

1. I venstre navigationsrude på Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">skal du</a> klikke på **Handlingscenter**.

2. Vælg fanen **Oversigt** for at få vist en liste over handlinger, der er blevet foretaget.

3. Vælg et element for at få vist flere oplysninger om afhjælpningshandlingen, der blev taget.

### <a name="restore-a-quarantined-file-from-the-action-center"></a>Gendanne en fil, der er sat i karantæne, fra Handlingscenter

1. I venstre navigationsrude på Microsoft 365 Defender skal du klikke på **Handlingscenter**.

2. Vælg en **handling** , du vil fortryde, under fanen Oversigt.

3. Vælg Fortryd i pop **op-ruden**. Hvis handlingen ikke kan fortrydes med denne metode, får du ikke vist knappen **Fortryd** . Du kan få mere at vide under [Fortryd fuldførte](manage-auto-investigation.md#undo-completed-actions) handlinger.

### <a name="undo-multiple-actions-at-one-time"></a>Fortryde flere handlinger på én gang

1. I venstre navigationsrude på Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">skal du</a> klikke på **Handlingscenter**.

2. Vælg **de handlinger** , du vil fortryde, under fanen Oversigt.

3. I ruden i højre side af skærmen skal du vælge **Fortryd**.

### <a name="remove-a-file-from-quarantine-across-multiple-devices"></a>Fjern en fil fra karantæne på tværs af flere enheder

> [!div class="mx-imgBorder"]
> ![Karantænefil.](images/autoir-quarantine-file-1.png)

1. I venstre navigationsrude på Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">skal du</a> klikke på **Handlingscenter**.

2. På fanen **Oversigt skal** du vælge en fil, der har filen Handlingstype **Karantæne**.

3. I ruden i højre side af skærmen skal du vælge Anvend på **X flere forekomster** af denne fil og derefter vælge Fortryd.

### <a name="restore-file-from-quarantine"></a>Gendan fil fra karantæne

Du kan rulle en fil tilbage og fjerne den fra karantæne, hvis du har besluttet, at den er ren efter en undersøgelse. Kør følgende kommando på hver enhed, hvor filen var i karantæne.

1. Åbn en kommandoprompt med administrator på enheden:

   1. Gå til **Start,** og skriv _cmd_.
   2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

    ```console
    "ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
    ```

    > [!IMPORTANT]
    > I nogle scenarier kan **ThreatName** blive vist som `EUS:Win32/CustomEnterpriseBlock!cl`. Defender til Slutpunkt gendanner alle bruger blokerede filer, der har været i karantæne på denne enhed inden for de seneste 30 dage.
    >
    > En fil, der var sat i karantæne som en potentiel netværkstrussel, kan muligvis ikke gendannes. Hvis en bruger forsøger at gendanne filen efter karantæne, er filen muligvis ikke tilgængelig. Dette kan skyldes, at systemet ikke længere har netværkslegitimationsoplysninger til at få adgang til filen. Dette er typisk et resultat af en midlertidig log på et system eller en delt mappe, og adgangstokensene er udløbet.

3. I ruden i højre side af skærmen skal du vælge Anvend på **X flere forekomster** af denne fil og derefter vælge Fortryd.

## <a name="part-3-review-or-define-exclusions"></a>Del 3: Gennemse eller definer udeladelse

En udelukkelse er en enhed, f.eks. en fil eller en URL-adresse, som du angiver som en undtagelse for afhjælpningshandlinger. Den ekskluderede enhed kan stadig findes, men der bliver ikke foretaget nogen afhjælpningshandlinger på den pågældende enhed. Det vil sige, at den registrerede fil eller proces ikke stoppes, sendes til karantæne, fjernes eller på anden måde ændres af Microsoft Defender til slutpunkt.

Hvis du vil definere udeladelse på tværs af Microsoft Defender for Endpoint, skal du udføre følgende opgaver:

- [Definere udeladelse for Microsoft Defender Antivirus](#exclusions-for-microsoft-defender-antivirus)
- [Opret "tillad"-indikatorer for Microsoft Defender til slutpunkt](#indicators-for-microsoft-defender-for-endpoint)

> [!NOTE]
> Microsoft Defender Antivirus gælder kun for antivirusbeskyttelse, ikke på tværs af andre Microsoft Defender for Endpoint-funktioner. Hvis du vil udelade filer bredt, skal du bruge udeladelse for Microsoft Defender Antivirus og [brugerdefinerede indikatorer](/microsoft-365/security/defender-endpoint/manage-indicators) for Microsoft Defender til slutpunkt.

Fremgangsmåderne i dette afsnit beskriver, hvordan du definerer udeladelse og indikatorer.

### <a name="exclusions-for-microsoft-defender-antivirus"></a>Udeladelse for Microsoft Defender Antivirus

Generelt bør du ikke være nødt til at definere udeladelse for Microsoft Defender Antivirus. Sørg for, at du definerer udeladelse med måde, og at du kun medtager de filer, mapper, processer og proces åbne filer, der resulterer i falske positive. Desuden skal du sørge for at gennemgå dine definerede undtagelser regelmæssigt. Vi anbefaler, [at Microsoft Endpoint Manager](/mem/endpoint-manager-overview) bruges til at definere eller redigere dine antivirus udelukkelser, men du kan bruge andre metoder, f.eks[. Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) (se Administrer [Microsoft Defender til slutpunkt](manage-mde-post-migration.md)).

> [!TIP]
> Har du brug for hjælp til udelukkelse af antivirus? Se [Konfigurere og validere udeladelse for Microsoft Defender Antivirus scanninger](configure-exclusions-microsoft-defender-antivirus.md).

#### <a name="use-microsoft-endpoint-manager-to-manage-antivirus-exclusions-for-existing-policies"></a>Brug Microsoft Endpoint Manager til at administrere antivirus udelukkelser (for eksisterende politikker)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus**, og vælg derefter en eksisterende politik. Hvis du ikke har en eksisterende politik, eller du vil oprette en ny politik, skal du gå videre [til den næste procedure](#use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions).

3. Vælg **Egenskaber**, og vælg **Rediger ud for** **Konfigurationsindstillinger**.

4. **Udvid Microsoft Defender Antivirus udeladelse,** og angiv derefter dine udeladelser.

5. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

#### <a name="use-microsoft-endpoint-manager-to-create-a-new-antivirus-policy-with-exclusions"></a>Brug Microsoft Endpoint Manager til at oprette en ny antiviruspolitik med udeladelse

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus** \> **+ Opret politik**.

3. Vælg en platform (**f.eks. Windows 10 og nyere**, **macOS** **eller Windows 10 og Windows Server**).

4. Ud **for** Profil skal **du Microsoft Defender Antivirus udeladelser** og derefter vælge **Opret**.

5. Angiv et navn og en beskrivelse af profilen, og vælg derefter **Næste**.

6. Angiv dine **antivirusudetagelser** under fanen Konfigurationsindstillinger, og vælg derefter **Næste**.

7. Hvis du **bruger omfangsmærker** i organisationen, skal du på fanen Omfangsmærker angive omfangsmærker for den politik, du opretter. (Se [Omfangsmærker](/mem/intune/fundamentals/scope-tags)).

8. På fanen **Opgaver skal** du angive de brugere og grupper, som din politik skal anvendes for, og derefter vælge **Næste**. (Hvis du har brug for hjælp til tildelinger, [skal du se Tildel bruger- og enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

9. Gennemgå indstillingerne **under fanen Gennemse** + opret, og vælg derefter **Opret**.

### <a name="indicators-for-microsoft-defender-for-endpoint"></a>Indikatorer for Microsoft Defender til slutpunkt

[Symboler](/microsoft-365/security/defender-endpoint/manage-indicators) (specifikt indikatorer for kompromis eller IoCs) gør det muligt for dit sikkerhedsteam at definere registrering, forebyggelse og udelukkelse af enheder. Du kan f.eks. angive bestemte filer, der skal udelades fra scanninger og afhjælpningshandlinger i Microsoft Defender til slutpunkt. Eller indikatorer kan bruges til at generere beskeder for bestemte filer, IP-adresser eller URL-adresser.

Hvis du vil angive enheder som undtagelser for Microsoft Defender til slutpunkt, skal du oprette "tillad"-indikatorer for disse enheder. Sådanne "tillad"-indikatorer i Microsoft Defender for Endpoint gælder for næste [generations beskyttelse](microsoft-defender-antivirus-in-windows-10.md), [slutpunktsregistrering og -svar](overview-endpoint-detection-response.md) og [automatiseret undersøgelse, & afhjælpning](/microsoft-365/security/defender-endpoint/automated-investigations).

Der kan oprettes "Tillad"-indikatorer for:

- [Filer](#indicators-for-files)
- [IP-adresser, URL-adresser og domæner](#indicators-for-ip-addresses-urls-or-domains)
- [Programcertifikater](#indicators-for-application-certificates)

![Diagram over indikatortyper.](images/false-positives-indicators.png)

#### <a name="indicators-for-files"></a>Indikatorer for filer

Når du [opretter en "tillad"](/microsoft-365/security/defender-endpoint/indicator-file)-indikator for en fil, f.eks. en eksekverbar fil, hjælper det med at forhindre, at filer, som din organisation bruger, blokeres. Filer kan omfatte portable eksekverbare filer (PE), f.eks. `.exe` og `.dll` filer.

Før du opretter indikatorer for filer, skal du kontrollere, at følgende krav er opfyldt:

- Microsoft Defender Antivirus er konfigureret med skybaseret beskyttelse aktiveret (se [Administrer skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus))
- Antimalware-klientversion er 4.18.1901.x eller nyere
- Enheder kører Windows 10 version 1703 eller nyere eller Windows 11; Windows Server 2016 eller Windows Server 2019 eller Windows Server 2022
- Funktionen [Bloker eller tillad er slået til](/microsoft-365/security/defender-endpoint/advanced-features)

#### <a name="indicators-for-ip-addresses-urls-or-domains"></a>Indikatorer for IP-adresser, URL-adresser eller domæner

Når du [opretter en "tillad"-indikator for en IP-adresse, URL-adresse](/microsoft-365/security/defender-endpoint/indicator-ip-domain) eller et domæne, hjælper det med at forhindre, at de websteder eller IP-adresser, som din organisation bruger, blokeres.

Før du opretter indikatorer for IP-adresser, URL-adresser eller domæner, skal du kontrollere, at følgende krav er opfyldt:

- Netværksbeskyttelse i Defender til slutpunkt er aktiveret i bloktilstand (se [Aktivér netværksbeskyttelse](/microsoft-365/security/defender-endpoint/enable-network-protection))
- Antimalware-klientversion er 4.18.1906.x eller nyere
- Enheder kører Windows 10, version 1709 eller nyere eller Windows 11

Brugerdefinerede netværksindikatorer er slået til i [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Du kan få mere at vide under [Avancerede funktioner](/microsoft-365/security/defender-endpoint/advanced-features).

#### <a name="indicators-for-application-certificates"></a>Indikatorer for programcertifikater

Når du [opretter en "tillad"](/microsoft-365/security/defender-endpoint/indicator-certificates)-indikator for et programcertifikat, hjælper det med at forhindre programmer, f.eks internt udviklet programmer, som din organisation bruger i at blive blokeret. `.CER` filtypenavne `.PEM` understøttes.

Før du opretter indikatorer for programcertifikater, skal du kontrollere, at følgende krav er opfyldt:

- Microsoft Defender Antivirus er konfigureret med skybaseret beskyttelse aktiveret (se [Administrer skybaseret beskyttelse](deploy-manage-report-microsoft-defender-antivirus.md)
- Antimalware-klientversion er 4.18.1901.x eller nyere
- Enheder kører Windows 10 version 1703 eller nyere eller Windows 11; Windows Server 2016 eller Windows Server 2019 eller Windows Server 2022
- Definitioner af virus- og trusselsbeskyttelse er opdateret

> [!TIP]
> Når du opretter indikatorer, kan du definere dem én efter én eller importere flere elementer på én gang. Husk, at der er en grænse på 15.000 indikatorer for en enkelt lejer. Og det kan være nødvendigt først at indsamle visse oplysninger, f.eks. oplysninger om filhash. Sørg for at gennemgå forudsætningerne, før du [opretter indikatorer](manage-indicators.md).

## <a name="part-4-submit-a-file-for-analysis"></a>Del 4: Indsend en fil til analyse

Du kan sende enheder, f.eks. filer og filløse registreringer, til analyse hos Microsoft. Microsofts sikkerhedseksperter analyserer alle indsendelser, og deres resultater hjælper med at informere Microsoft Defender om egenskaber for trusselsbeskyttelse i Microsoft Defender. Når du logger på indsendelseswebstedet, kan du spore dine indsendelser.

### <a name="submit-a-file-for-analysis"></a>Sende en fil til analyse

Hvis du har en fil, der blev fundet forkert som skadelig, eller som blev overset, skal du følge disse trin for at sende filen til analyse.

1. Gennemse retningslinjerne her: [Send filer til analyse](/windows/security/threat-protection/intelligence/submission-guide).

2. Besøg webstedet [Microsoft Sikkerhedsviden indsendelsen](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)og indsend din eller dine filer).

### <a name="submit-a-fileless-detection-for-analysis"></a>Sende en registrering uden fil til analyse

Hvis noget blev registreret som malware baseret på adfærd, og du ikke har en fil, kan du sende din fil `Mpsupport.cab` til analyse. Du kan hente *.cab* fil ved hjælp af værktøjet Microsoft Malware Protection Command-Line Utility (MPCmdRun.exe) på Windows 10 eller Windows 11.

1. Gå til ` C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`, og kør `MpCmdRun.exe` derefter som administrator.

2. Skriv `mpcmdrun.exe -GetFiles`, og tryk derefter på **Enter**.

   Der .cab en fil, der indeholder forskellige diagnostiske logfiler. Placeringen af filen er angivet i outputtet for kommandoprompten. Som standard er placeringen `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

3. Gennemse retningslinjerne her: [Send filer til analyse](/windows/security/threat-protection/intelligence/submission-guide).

4. Besøg webstedet [Microsoft Sikkerhedsviden indsendelsen](https://www.microsoft.com/wdsi/filesubmission) (https://www.microsoft.com/wdsi/filesubmission)og indsend dine .cab filer.

### <a name="what-happens-after-a-file-is-submitted"></a>Hvad sker der, når en fil er sendt?

Din indsendelse scannes straks af vores systemer for at give dig den seneste beslutning, selv før en analytiker begynder at håndtere din sag. Det er muligt, at en fil allerede er blevet sendt og behandlet af en analytiker. I disse tilfælde bliver der hurtigt truffet en bestemmelse.

For indsendelser, der ikke allerede er behandlet, prioriteres de til analyse på følgende måde:

- Udbredte filer med mulighed for at påvirke et stort antal computere prioriteres højere.
- Godkendte kunder, især virksomhedskunder med gyldige [Software Assurance-id'er (SAID'er),](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) får højere prioritet.
- Indsendelser, der er markeret som høj prioritet af SAID-ejere, får omgående opmærksomhed.

Hvis du vil søge efter opdateringer vedrørende din indsendelse, skal du logge [på Microsoft Sikkerhedsviden indsendelseswebstedet](https://www.microsoft.com/wdsi/filesubmission).

> [!TIP]
> Du kan få mere at vide [under Sende filer til analyse](/windows/security/threat-protection/intelligence/submission-guide#how-does-microsoft-prioritize-submissions).

## <a name="part-5-review-and-adjust-your-threat-protection-settings"></a>Del 5: Gennemse og juster indstillingerne for trusselsbeskyttelse

Microsoft Defender til Slutpunkt tilbyder en lang række indstillinger, herunder muligheden for at finjustere indstillingerne for forskellige funktioner og egenskaber. Hvis du får mange falske positive, skal du sørge for at gennemgå organisationens indstillinger for trusselsbeskyttelse. Det kan være nødvendigt at foretage nogle justeringer af:

- [Cloud-leveret beskyttelse](#cloud-delivered-protection)
- [Afhjælpning af potentielt uønskede programmer](#remediation-for-potentially-unwanted-applications)
- [Automatiseret undersøgelse og afhjælpning](#automated-investigation-and-remediation)

### <a name="cloud-delivered-protection"></a>Cloud-leveret beskyttelse

Kontrollér dit beskyttelsesniveau, der leveres i skyen, for Microsoft Defender Antivirus. Som standard er beskyttelse leveret i skyen indstillet til Ikke konfigureret **, hvilket** svarer til et normalt beskyttelsesniveau for de fleste organisationer. Hvis din cloud-leveret beskyttelse er indstillet til **Høj,** **Høj +** eller **Nul tolerance**, kan du opleve et større antal falske positive.

> [!TIP]
> Du kan få mere at vide om konfiguration af beskyttelsen, der leveres i skyen, [under Angive beskyttelsesniveauet, der leveres i skyen](/windows/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus).

Vi anbefaler, [at Microsoft Endpoint Manager](/mem/endpoint-manager-overview) bruges til at redigere eller angive dine skybaserede beskyttelsesindstillinger, men du kan bruge andre metoder, f.eks. [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) (se Administrer [Microsoft Defender til slutpunkt](manage-mde-post-migration.md)).

#### <a name="use-microsoft-endpoint-manager-to-review-and-edit-cloud-delivered-protection-settings-for-existing-policies"></a>Brug Microsoft Endpoint Manager til at gennemse og redigere beskyttelsesindstillinger, der leveres i skyen (for eksisterende politikker)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus** , og vælg derefter en eksisterende politik. Hvis du ikke har en eksisterende politik, eller du vil oprette en ny politik, skal du gå videre [til den næste procedure](#use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy).

3. Under **Administrer skal** du vælge **Egenskaber**. Derefter skal du ud **for Konfigurationsindstillinger** vælge **Rediger**.

4. **Udvid Skybeskyttelse**, og gennemse din aktuelle indstilling i **rækken Cloud-leveret beskyttelsesniveau**. Vi anbefaler, at du indstiller beskyttelse, der leveres i skyen **, til** ikke-konfigureret, hvilket giver stærk beskyttelse og samtidig reducerer risikoen for falske positive.

5. Vælg **Gennemse + gem**, og derefter **Gem**.

#### <a name="use-microsoft-endpoint-manager-to-set-cloud-delivered-protection-settings-for-a-new-policy"></a>Brug Microsoft Endpoint Manager til at angive beskyttelsesindstillinger, der leveres i skyen (for en ny politik)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Endpoint security** \> **Antivirus** \> **+ Opret politik**.

3. For **Platform** skal du vælge en indstilling, og **derefter skal du** for Profil **vælge antivirus- Microsoft Defender Antivirus** (den specifikke indstilling afhænger af, hvad du har valgt til **Platform**). Vælg derefter **Opret**.

4. Angiv **et navn og** en beskrivelse af politikken under fanen Grundlæggende. Vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du **udvide Skybeskyttelse** og angive følgende indstillinger:

   - Angiv **Slå beskyttelse, der leveres i skyen,** til **Ja**.
   - Angiv **beskyttelsesniveauet, der leveres i skyen****, til Ikke konfigureret**. (Dette niveau giver et højt beskyttelsesniveau som standard, samtidig med at det reducerer risikoen for falske positive).

6. Hvis du **bruger omfangsmærker** i organisationen, skal du angive omfangsmærker for politikken under fanen Omfangsmærker. (Se [Omfangsmærker](/mem/intune/fundamentals/scope-tags)).

7. På fanen **Opgaver skal** du angive de brugere og grupper, som din politik skal anvendes for, og derefter vælge **Næste**. (Hvis du har brug for hjælp til tildelinger, [skal du se Tildel bruger- og enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. Gennemgå indstillingerne **under fanen Gennemse** + opret, og vælg derefter **Opret**.

### <a name="remediation-for-potentially-unwanted-applications"></a>Afhjælpning af potentielt uønskede programmer

Potentielt uønskede programmer er en kategori af software, der kan få enheder til at køre langsomt, vise uventede reklamer eller installere anden software, der kan være uventet eller uønsket. Eksempler på PUA omfatter reklamesoftware, bundtningssoftware og software, der fungerer forskelligt med sikkerhedsprodukter. Selvom PUA ikke betragtes som malware, er visse typer software PUA baseret på deres adfærd og omdømme.

> [!TIP]
> Du kan få mere at vide om PUA [i Finde og blokere potentielt uønskede programmer](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

Afhængigt af de apps, din organisation bruger, får du muligvis falske positive som et resultat af indstillingerne for PUA-beskyttelse. Hvis det er nødvendigt, kan du overveje at køre PUA-beskyttelse i overvågningstilstand i et stykke tid eller anvende PUA-beskyttelse på et undersæt af enheder i organisationen. PUA-beskyttelse kan konfigureres til Microsoft Edge og til Microsoft Defender Antivirus.

Vi anbefaler, [at du Microsoft Endpoint Manager](/mem/endpoint-manager-overview) til at redigere eller angive indstillinger for PUA-beskyttelse. Du kan dog bruge andre metoder, f.eks. [Gruppepolitik](/azure/active-directory-domain-services/manage-group-policy) (se Administrer [Microsoft Defender til slutpunkt](manage-mde-post-migration.md)).

#### <a name="use-microsoft-endpoint-manager-to-edit-pua-protection-for-existing-configuration-profiles"></a>Brug Microsoft Endpoint Manager til at redigere PUA-beskyttelse (for eksisterende konfigurationsprofiler)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Enheders** \> **konfigurationsprofiler**, og vælg derefter en eksisterende politik. Hvis du ikke har en eksisterende politik, eller du vil oprette en ny politik, skal du gå videre [til den næste procedure](#use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile).

3. Under **Administrer** skal du **vælge Egenskaber** og derefter vælge **Rediger ud** for Konfigurationsindstillinger.

4. På fanen **Konfigurationsindstillinger** skal du rulle ned og **udvide Microsoft Defender Antivirus**.

5. Angiv **Registrer potentielt uønskede programmer** til **Overvågning**. (Du kan deaktivere den, men ved hjælp af overvågningstilstand kan du se registreringer).

6. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

#### <a name="use-microsoft-endpoint-manager-to-set-pua-protection-for-a-new-configuration-profile"></a>Brug Microsoft Endpoint Manager til at angive PUA-beskyttelse (for en ny konfigurationsprofil)

1. Gå til Microsoft Endpoint Manager Administration (<https://endpoint.microsoft.com>), og log på.

2. Vælg **Enheder** **Konfigurationsprofiler** \> \> **+ Opret profil**.

3. For platformen **skal** du vælge **Windows 10 og nyere**, og ud for **Profil skal** du vælge **Enhedsbegrænsninger**.

4. Angiv **et navn og** en beskrivelse af politikken under fanen Grundlæggende. Vælg derefter **Næste**.

5. På fanen **Konfigurationsindstillinger** skal du rulle ned og **udvide Microsoft Defender Antivirus**.

6. Angiv **Registrer potentielt uønskede programmer** til **Overvågning**, og vælg derefter **Næste**. (Du kan deaktivere PUA-beskyttelse, men ved hjælp af overvågningstilstand kan du se registreringer).

7. På fanen **Opgaver skal** du angive de brugere og grupper, som din politik skal anvendes for, og derefter vælge **Næste**. (Hvis du har brug for hjælp til tildelinger, [skal du se Tildel bruger- og enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profile-assign).)

8. På fanen **Regler for anvendelse skal du** angive de OS-udgaver eller -versioner, der skal medtages eller udelades fra politikken. Du kan f.eks. angive, at politikken skal anvendes på alle enheder af bestemte Windows 10. Vælg derefter **Næste**.

9. På fanen **Gennemse + Opret** skal du gennemgå dine indstillinger og derefter vælge **Opret**.

### <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

[Automatiserede undersøgelses- og](automated-investigations.md) afhjælpningsfunktioner (AIR) er designet til at undersøge vigtige beskeder og øjeblikkeligt gribe ind for at afhjælpe overtrædelser. Når der udløses beskeder, og en automatisk undersøgelse køres, genereres der en vurdering af hvert enkelt beviser, der undersøges. Det kan være *ondsindede*, *mistænkelige* eller *ingen trusler, der kan findes*.

Afhængigt af [niveauet af automatisering](/microsoft-365/security/defender-endpoint/automation-levels) , der er angivet for din organisation og andre sikkerhedsindstillinger, løses afhjælpningshandlinger på artefakter, der anses for *at være skadelige* eller *mistænkelige*. I nogle tilfælde udføres afhjælpningshandlinger automatisk. I andre tilfælde udføres afhjælpningshandlinger manuelt eller kun efter godkendelse fra dit sikkerhedsteam.

- [Få mere at vide om automatiseringsniveauer](/microsoft-365/security/defender-endpoint/automation-levels); og derefter
- [Konfigurer AIR-funktioner i Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation).

> [!IMPORTANT]
> Vi anbefaler, at *du bruger fuld* automatisering til automatisk undersøgelse og afhjælpning. Slå ikke disse funktioner fra på grund af en falsk positiv. Brug i stedet ["tillad"-indikatorer til at definere undtagelser](#indicators-for-microsoft-defender-for-endpoint), og sørg for, at automatiseret undersøgelse og afhjælpning er indstillet til at udføre relevante handlinger automatisk. Hvis [du følger denne](automation-levels.md#levels-of-automation) vejledning, reduceres antallet af beskeder, som sikkerhedsteamet skal håndtere.

## <a name="still-need-help"></a>Har du stadig brug for hjælp?

Hvis du har gennemarbejdet alle trinnene i denne artikel og stadig har brug for hjælp, kan du kontakte teknisk support.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> og log på.

2. I øverste højre hjørne skal du vælge spørgsmålstegnet (**?**) og derefter vælge **Microsoft support**.

3. **Beskriv dit** problem i vinduet Supportassistent, og send derefter meddelelsen. Derfra kan du åbne en serviceanmodning.

## <a name="see-also"></a>Se også

[Administrer Microsoft Defender til Slutpunkt](manage-mde-post-migration.md)

[Oversigt over Microsoft 365 Defender portal](/microsoft-365/security/defender-endpoint/use)
