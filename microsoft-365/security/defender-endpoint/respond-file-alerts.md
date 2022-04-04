---
title: Tag svarhandlinger på en fil i Microsoft Defender for Endpoint
description: Tag svarhandlinger på filrelaterede beskeder ved at stoppe og kvarte en fil eller blokere en fil og kontrollere oplysninger om aktivitet.
keywords: svar, stop og karantæne, bloker fil, dybdegående analyse
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 5c5a457d960f7dd7906c7d26a099d242507fbe86
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499193"
---
# <a name="take-response-actions-on-a-file"></a>Udføre svarhandlinger på en fil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-responddile-abovefoldlink)

Du kan hurtigt reagere på registrerede angreb ved at stoppe og kvarte filer eller blokere en fil. Når du har taget handling på filer, kan du kontrollere oplysninger om aktivitet i Handlingscenter.

Svarhandlinger er tilgængelige på en fils detaljerede profilside. Når du er på denne side, kan du skifte mellem de nye og gamle sidelayout ved at slå **ny filside til**. I resten af denne artikel beskrives det nyere sidelayout.

Svarhandlinger kører langs toppen af filsiden og omfatter:

- Stop og karantæne-fil
- Tilføj indikator
- Download fil
- Kontakt en trusselsekspert
- Handlingscenter

Du kan også sende filer til dybdegående analyse for at køre filen i en sikker skysandkasse. Når analysen er fuldført, får du en detaljeret rapport, der indeholder oplysninger om filens funktionsmåde. Du kan sende filer til dybdegående analyse og læse tidligere rapporter ved at vælge **fanen Dybdegående** analyse. Den er placeret under fil informationskortene.

Nogle handlinger kræver visse tilladelser. I følgende tabel beskrives, hvilken handling visse tilladelser kan udføre på portable eksekverbare filer (PE) og ikke-PE-filer:

|Tilladelse|PE-filer|Ikke-PE-filer|
|---|:---:|:---:|
|Vis data|X|X|
|Undersøgelse af beskeder|&#x2611;|X|
|Grundlæggende om live svar|X|X|
|Live svar avanceret|&#x2611;|&#x2611;|

Du kan finde flere oplysninger om roller [i Oprette og administrere roller for rollebaseret adgangskontrol](user-roles.md).

## <a name="stop-and-quarantine-files-in-your-network"></a>Stop og sæt filer i karantæne i dit netværk

Du kan indeholde et angreb i organisationen ved at stoppe den ondsindede proces og holde filen i kvartil, hvor den blev observeret.

> [!IMPORTANT]
> Du kan kun gøre følgende, hvis:
>
> - Den enhed, du tager handlingen på, kører Windows 10 version 1703 eller nyere og Windows 11
> - Filen tilhører ikke udgivere, der er tillid til, eller som ikke er signeret af Microsoft
> - Microsoft Defender Antivirus skal som minimum køre i passiv tilstand. Du kan finde flere oplysninger [Microsoft Defender Antivirus kompatibilitet.](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility)

Handlingen **Stop og karantæne fil** omfatter at stoppe med at køre processer, kvarte filerne og slette permanente data som registreringsdatabasenøgler.

Denne handling træder i kraft på enheder med Windows 10, version 1703 eller nyere og Windows 11, hvor filen er blevet observeret inden for de seneste 30 dage.

> [!NOTE]
> Du kan når som helst gendanne filen fra karantæne.

### <a name="stop-and-quarantine-files"></a>Stoppe og sætte filer i karantæne

1. Vælg den fil, du vil stoppe og sætte i karantæne. Du kan vælge en fil fra en af følgende visninger eller bruge feltet Søg:

   - **Beskeder –** klik på de tilhørende links fra Beskrivelse eller Detaljer på tidslinjen Med beskedhistorie
   - **Søgefelt** – **vælg** Filer i rullemenuen, og angiv filnavnet

   > [!NOTE]
   > Handlingen stop- og karantænefil er begrænset til maksimalt 1000 enheder. Hvis du vil stoppe en fil på et større antal enheder, skal du se [Tilføj indikator for at blokere eller tillade fil](#add-indicator-to-block-or-allow-a-file).

2. Gå til den øverste linje, og vælg **Stop og karantæne fil**.

   :::image type="content" source="images/atp-stop-quarantine-file.png" alt-text="Handlingen Stop og sæt i karantæne" lightbox="images/atp-stop-quarantine-file.png":::

3. Angiv en årsag, og vælg derefter **Bekræft**.

   :::image type="content" source="images/atp-stop-quarantine.png" alt-text="Siden stop og karantæne fil" lightbox="images/atp-stop-quarantine.png":::

   Handlingscenter viser indsendelsesoplysningerne:

   :::image type="content" source="images/atp-stopnquarantine-file.png" alt-text="Handlingscenter for stop- og karantænefilen" lightbox="images/atp-stopnquarantine-file.png":::

   - **Indsendelsestid** – Viser, hvornår handlingen blev sendt.
   - **Succes** – Viser antallet af enheder, hvor filen er blevet stoppet og sat i karantæne.
   - **Mislykket** – Viser antallet af enheder, hvor handlingen mislykkedes, samt detaljer om fejlen.
   - **Afventer** – Viser antallet af enheder, hvor filen endnu ikke er blevet stoppet og sat i karantæne fra. Det kan tage tid, hvis enheden er offline eller ikke har forbindelse til netværket.

4. Vælg en statusindikatorer for at få vist flere oplysninger om handlingen. Vælg f.eks. **Kunne ikke** se, hvor handlingen mislykkedes.

#### <a name="notification-on-device-userf"></a>Meddelelse på enhed userf

Når filen fjernes fra en enhed, vises følgende meddelelse:

:::image type="content" source="images/atp-notification-file.png" alt-text="Meddelelsen en bruger på enheden" lightbox="images/atp-notification-file.png":::

På enhedens tidslinje tilføjes der en ny begivenhed for hver enhed, hvor en fil blev stoppet og sat i karantæne.

Der vises en advarsel, før handlingen gennemføres for filer, der anvendes bredt i hele organisationen. Den bruges til at validere, om handlingen er tiltænkt.

## <a name="restore-file-from-quarantine"></a>Gendan fil fra karantæne

Du kan rulle en fil tilbage og fjerne den fra karantæne, hvis du har besluttet, at den er ren efter en undersøgelse. Kør følgende kommando på hver enhed, hvor filen var i karantæne.

1. Åbn en kommandoprompt med administrator på enheden:

   1. Gå til **Start,** og skriv _cmd_.

   1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```dos
   "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
   ```

   > [!NOTE]
   > I nogle scenarier kan **ThreatName** blive vist som: EUS:Win32/CustomEnterpriseBlock!cl.
   >
   > Defender til Slutpunkt gendanner alle bruger blokerede filer, der har været i karantæne på denne enhed inden for de seneste 30 dage.

> [!IMPORTANT]
> En fil, der var sat i karantæne som en potentiel netværkstrussel, kan muligvis ikke gendannes. Hvis en bruger forsøger at gendanne filen efter karantæne, er filen muligvis ikke tilgængelig. Dette kan skyldes, at systemet ikke længere har netværkslegitimationsoplysninger til at få adgang til filen. Dette er typisk et resultat af en midlertidig log på et system eller en delt mappe, og adgangstokensene er udløbet.

## <a name="download-or-collect-file"></a>Download eller indsaml fil

Hvis du **vælger Download fil** fra svarhandlingerne, kan du downloade et lokalt, adgangskodebeskyttet .zip, der indeholder filen. Der vises en pop op-fil, hvor du kan optage en årsag til at hente filen og angive en adgangskode.

Som standard bør du kunne downloade filer, der er i karantæne.

:::image type="content" source="images/atp-download-file-action.png" alt-text="Handlingen Download fil" lightbox="images/atp-download-file-action.png":::

### <a name="download-quarantined-files"></a>Download filer, der er sat i karantæne

Filer, der er blevet sat i karantæne Microsoft Defender Antivirus dit sikkerhedsteam, vil blive gemt i overensstemmelse med dine [prøveindsendelseskonfigurationer](enable-cloud-protection-microsoft-defender-antivirus.md). Dit sikkerhedsteam kan hente filerne direkte fra filens detaljeside via knappen "Download fil". **Eksempelfunktionen er som standard slået Til**.

Placeringen afhænger af din organisations geoindstillinger (enten EU, Storbritannien eller USA). En fil, der er sat i karantæne, indsamles kun én gang pr. organisation. Få mere at vide om Microsofts databeskyttelse fra Service Trust Portal på https://aka.ms/STP.

Hvis denne indstilling er slået til, kan det hjælpe sikkerhedsteams med at undersøge potentielt dårlige filer og undersøge hændelser hurtigt og på en mindre risikabel måde. Men hvis du vil slå denne indstilling fra, skal du gå  **til Indstillinger** \>  \> \> avancerede funktioner Download filer, der er sat i karantæne, for at justere indstillingen. [Få mere at vide om avancerede funktioner](advanced-features.md)

#### <a name="backing-up-quarantined-files"></a>Sikkerhedskopiering af filer, der er sat i karantæne

Brugerne kan blive bedt om at give udtrykkeligt samtykke, før de sikkerhedskopier den fil, der er sat i karantæne, afhængigt af [konfigurationen af din prøveindsendelse](enable-cloud-protection-microsoft-defender-antivirus.md#use-group-policy-to-turn-on-cloud-protection).

Denne funktion fungerer ikke, hvis indsendelse af eksempler er slået fra. Hvis den automatiske indsendelse af eksempler er indstillet til at anmode om tilladelse fra brugeren, indsamles der kun eksempler, som brugeren accepterer at sende.

> [!IMPORTANT]
> Download krav til filer i karantæne:
>
> - Din organisation bruger Microsoft Defender Antivirus aktiv tilstand
> - Antivirusprogrammets version er 1.1.17300.4 eller nyere. Se [Månedlig platform og programversioner](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)
> - Skybaseret beskyttelse er aktiveret. Se [Slå skybaseret beskyttelse til](enable-cloud-protection-microsoft-defender-antivirus.md)
> - Eksempel på indsendelse er slået til
> - Enheder har Windows 10 version 1703 eller nyere, Windows Server 2016 eller 2019 eller Windows Server 2022 eller Windows 11

### <a name="collect-files"></a>Indsaml filer

Hvis en fil ikke allerede er gemt af Microsoft Defender for Endpoint, kan du ikke downloade den. I stedet får du vist knappen **Indsaml** fil på den samme placering. Hvis en fil ikke er blevet set i organisationen i de seneste 30 dage, **deaktiveres** Indsaml fil.
> [!Important]
> En fil, der var sat i karantæne som en potentiel netværkstrussel, kan muligvis ikke gendannes. Hvis en bruger forsøger at gendanne filen efter karantæne, er filen muligvis ikke tilgængelig. Dette kan skyldes, at systemet ikke længere har netværkslegitimationsoplysninger til at få adgang til filen. Dette er typisk et resultat af en midlertidig log på et system eller en delt mappe, og adgangstokensene er udløbet.

## <a name="add-indicator-to-block-or-allow-a-file"></a>Tilføj indikator for at blokere eller tillade en fil

Forebyg yderligere overførsel af et angreb i organisationen ved at udelukke potentielt skadelige filer eller mistanke om malware. Hvis du kender en potentielt skadelig eksekverbar eksekverbar fil (PE), kan du blokere den. Denne handling forhindrer den i at blive læst, skrevet eller udført på enheder i organisationen.

> [!IMPORTANT]
>
> - Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus og cloud-leveret beskyttelse er aktiveret. Få mere at vide under [Administrer beskyttelse, der leveres i skyen](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
>
> - Versionen af Antimalware-klienten skal være 4.18.1901.x eller nyere.
> - Denne funktion er udviklet til at forhindre mulig malware (eller potentielt skadelige filer) i at blive hentet fra internettet. It currently supports portable executable (PE) files, including _.exe_ and _.dll_ files. Dækningen udvides med tiden.
> - Denne svarhandling er tilgængelig for enheder på Windows 10, version 1703 eller nyere og Windows 11.
> - Funktionen Tillad eller Bloker kan ikke udføres på filer, hvis filens klassificering findes i enhedens cache, før handlingen tillades eller blokeres.

> [!NOTE]
> PE-filen skal være på enhedens tidslinje, for at du kan foretage denne handling.
>
> Der kan være et par minutters ventetid mellem det tidspunkt, hvor handlingen blev foretaget, og den faktiske fil blev blokeret.

### <a name="enable-the-block-file-feature"></a>Aktivér funktionen til blokering af fil

Hvis du vil begynde at blokere filer, skal [du først **slå funktionen Bloker eller** tillad til](advanced-features.md) Indstillinger.

### <a name="allow-or-block-file"></a>Tillad eller bloker fil

Når du tilføjer en indikatorhash for en fil, kan du vælge at hæve en besked og blokere filen, når en enhed i organisationen forsøger at køre den.

Filer, der automatisk blokeres af en indikator, vises ikke i filens handlingscenter, men beskederne vil stadig være synlige i køen Vigtige beskeder.

Se [Administrer indikatorer](manage-indicators.md) for at få flere oplysninger om at blokere og hæve beskeder om filer.

Hvis du vil stoppe med at blokere en fil, skal du fjerne indikatoren. Det kan du gøre via **handlingen Rediger** indikator på filens profilside. Denne handling vil være synlig i samme position som handlingen **Tilføj indikator** , før du tilføjede indikatoren.

Du kan også redigere indikatorer fra **Indstillinger** under **Regelindikatorer**\>. Symboler er angivet i dette område efter deres fils hash.

## <a name="consult-a-threat-expert"></a>Kontakt en trusselsekspert

Kontakt en Microsoft-trusselsekspert for at få mere indsigt i en potentielt kompromitteret enhed eller allerede kompromitterede enheder. Microsoft-trusselseksperter er engageret direkte fra Microsoft 365 Defender for rettidigt og nøjagtigt svar. Eksperter giver indsigt i en potentielt kompromitteret enhed og hjælper dig med at forstå komplekse trusler og målrettede meddelelser om angreb. De kan også give oplysninger om beskederne eller en kontekst med trusselsintelligens, som du kan se på portaldashboardet.

Se [Kontakt en Microsoft Threat Expert for at](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) få flere oplysninger.

## <a name="check-activity-details-in-action-center"></a>Kontrollér detaljer om aktivitet i Handlingscenter

**Handlingscenter indeholder** oplysninger om handlinger, der er foretaget på en enhed eller fil. Du kan få vist følgende detaljer:

- Undersøgelse af pakkesamling
- Antivirusscanning
- Appbegrænsning
- Enhedsisolation

Alle andre relaterede oplysninger vises også, f.eks. dato/klokkeslæt for indsendelse, afsendelse af bruger, og om handlingen lykkedes eller mislykkedes.

:::image type="content" source="images/action-center-details.png" alt-text="Handlingscenter med oplysninger" lightbox="images/action-center-details.png":::

## <a name="deep-analysis"></a>Dybdegående analyse

Cybersikkerhedsundersøgelse udløses typisk af en besked. Beskeder er relateret til en eller flere observerede filer, der ofte er nye eller ukendte. Når du vælger en fil, åbnes filvisningen, hvor du kan se filens metadata. For at forbedre de data, der er relateret til filen, kan du sende filen til dybdegående analyse.

Funktionen Deep-analyse udfører en fil i et sikkert, fuldt instrumenteret skymiljø. Grundige analyseresultater viser filens aktiviteter, observerede funktionsmåder og tilknyttede artefakter, f.eks. afbrudte filer, ændringer i registreringsdatabasen og kommunikation med IP'er.
Dybdegående analyse understøtter i øjeblikket omfattende analyse af portable eksekverbare (PE) filer ( _herunder.exe_ - _og.dll_ filer).

Dybdegående analyse af en fil tager flere minutter. Når filanalysen er fuldført, opdateres fanen Deep Analysis for at vise en oversigt samt dato og klokkeslæt for de seneste tilgængelige resultater.

Den omfattende analyseoversigt indeholder en liste over observerede funktionsmåder *, hvoraf* nogle kan indikere ondsindet aktivitet og *observerede*, herunder kontaktede IP'er og filer, der er oprettet på disken. Hvis der ikke blev fundet noget, vises der en kort meddelelse i disse sektioner.

Resultaterne af dybdegående analyse matches med trusselsintelligens, og alle resultater genererer relevante beskeder.

Brug funktionen til dybdegående analyse til at undersøge detaljerne i en hvilken som helst fil, normalt under en undersøgelse af en besked eller af andre årsager, hvor du har mistanke om skadelig opførsel. Denne funktion er tilgængelig på **fanen Deep-analyse** på filens profilside.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4aAYy?rel=0]

**Indsend til dybdegående** analyse er aktiveret, når filen er tilgængelig i samlingen af Backend-prøver for Defender til slutpunkt, eller hvis den er blevet observeret på en Windows 10-enhed, der understøtter indsendelse af dybdegående analyse.

> [!NOTE]
> Kun filer fra Windows 10 og Windows 11 kan indsamles automatisk.

Du kan også sende en prøve via [Microsoft 365 Defender-portalen](https://www.microsoft.com/security/portal/submission/submit.aspx), hvis filen ikke blev observeret på en Windows 10-enhed (eller Windows 11), og vente på, at knappen **Send** til dybdegående analyse bliver tilgængelig.

> [!NOTE]
> På grund af backendbehandlingsflows i Microsoft 365 Defender-portalen kan der være op til 10 minutters ventetid mellem filindsendelse og tilgængeligheden af funktionen til dybdegående analyse i Defender til slutpunkt.

### <a name="submit-files-for-deep-analysis"></a>Send filer til dybdegående analyse

1. Vælg den fil, du vil sende til dybdegående analyse. Du kan vælge eller søge i en fil fra en af følgende visninger:

    - **Beskeder –** vælg fillinkene fra Beskrivelse **eller** Detaljer **på** tidslinjen Med en påmindelseshistorie
    - **Listen Enheder** – vælg fillinkene fra **sektionen Beskrivelse** **eller** Detaljer **i sektionen Enhed i** organisation
    - **Søgefelt** – **vælg** Filer i rullemenuen, og angiv filnavnet

2. På fanen **Deep-analyse** i filvisningen skal du vælge **Send**.

   :::image type="content" source="images/submit-file.png" alt-text="Knappen Indsend PE-filer" lightbox="images/submit-file.png":::

   > [!NOTE]
   > Kun PE-filer understøttes, _herunder.exe_ og _.dll_ filer.

   En statuslinje vises og indeholder oplysninger om de forskellige faser i analysen. Du kan derefter få vist rapporten, når analysen er færdig.

> [!NOTE]
> Afhængigt af enhedens tilgængelighed kan prøveindsamlingstiden variere. Der er en timeout på 3 timer for eksempelsamling. Samlingen mislykkes, og handlingen afbrydes, hvis der ikke er nogen online Windows 10 (eller Windows 11) på det pågældende tidspunkt. Du kan sende filer igen til dybdegående analyse for at få nye data i filen.

### <a name="view-deep-analysis-reports"></a>Få vist dybtgående analyserapporter

Få vist den medfølgende detaljerede analyserapport for at få mere dybdegående indsigt i den fil, du har indsendt. Denne funktion er tilgængelig i filvisningskonteksten.

Du kan få vist den omfattende rapport, der indeholder oplysninger om følgende afsnit:

- Funktionsmåder
- Observerede

Oplysningerne kan hjælpe dig med at undersøge, om der er indikationer af et muligt angreb.

1. Vælg den fil, du sendte til dybdegående analyse.
2. Vælg **fanen Deep-analyse** . Hvis der er nogen tidligere rapporter, vises rapportoversigten på denne fane.

   :::image type="content" source="images/analysis-results-nothing500.png" alt-text="Den omfattende analyserapport, der viser detaljerede oplysninger på tværs af en række kategorier" lightbox="images/analysis-results-nothing500.png":::

#### <a name="troubleshoot-deep-analysis"></a>Fejlfinding i forbindelse med dybdegående analyse

Hvis du ser et problem, når du forsøger at sende en fil, kan du prøve følgende fejlfindingstrin.

1. Sørg for, at den pågældende fil er en PE-fil. PE-filer har typisk _.exe_ eller _.dll_ (eksekverbare programmer eller programmer).

2. Kontrollér, at tjenesten har adgang til filen, at den stadig findes og ikke er blevet beskadiget eller ændret.

3. Vent et øjeblik, og prøv at sende filen igen. Køen kan være fuld, eller der opstod en midlertidig forbindelses- eller kommunikationsfejl.

4. Hvis politikken for eksempelsamling ikke er konfigureret, er standardfunktionsmåden at tillade indsamling af eksempler. Hvis den er konfigureret, skal du kontrollere, at politikindstillingen tillader indsamling af eksempler, før du sender filen igen. Når eksempelsamlingen er konfigureret, skal du kontrollere følgende registreringsdatabaseværdi:

    ```text
    Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
    Name: AllowSampleCollection
    Type: DWORD
    Hexadecimal value :
      Value = 0 - block sample collection
      Value = 1 - allow sample collection
    ```

5. Skift organisationsenheden via Gruppepolitik. Du kan finde flere oplysninger [i Konfigurere med Gruppepolitik](configure-endpoints-gp.md).

6. Hvis disse trin ikke løser problemet, skal du kontakte support.

## <a name="related-topics"></a>Relaterede emner

- [Udføre svarhandlinger på en enhed](respond-machine-alerts.md)
- [Undersøg filer](investigate-files.md)
- [Manuelle svarhandlinger i Microsoft Defender for Endpoint Plan 1](defender-endpoint-plan-1.md#manual-response-actions)
