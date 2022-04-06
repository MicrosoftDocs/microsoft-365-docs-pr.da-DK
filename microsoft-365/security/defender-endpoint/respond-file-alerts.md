---
title: Udfør svarhandlinger på en fil i Microsoft Defender for Endpoint
description: Udfør svarhandlinger på filrelaterede beskeder ved at stoppe og quarantinere en fil eller blokere en fil og kontrollere aktivitetsoplysningerne.
keywords: respond, stop and quarantine, block file, deep analysis
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
ms.openlocfilehash: 8bfa08a92a011d32cdc30e2f68052715b4075fdf
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665508"
---
# <a name="take-response-actions-on-a-file"></a>Udfør svarhandlinger på en fil

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-responddile-abovefoldlink)

Reagere hurtigt på registrerede angreb ved at stoppe og quarantinere filer eller blokere en fil. Når du har foretaget en handling på filer, kan du kontrollere aktivitetsoplysningerne i Løsningscenter.

Svarhandlinger er tilgængelige på en fils detaljerede profilside. Når du er på denne side, kan du skifte mellem det nye og det gamle sidelayout ved at slå **den nye filside** til eller fra. I resten af denne artikel beskrives det nyere sidelayout.

Svarhandlinger kører langs toppen af filsiden og omfatter:

- Stop- og sæt filen i karantæne
- Tilføj indikator
- Download fil
- Kontakt en trusselsekspert
- Handlingscenter

Du kan også sende filer til dyb analyse for at køre filen i en sikker sandkasse i skyen. Når analysen er fuldført, får du vist en detaljeret rapport, der indeholder oplysninger om filens funktionsmåde. Du kan sende filer til dyb analyse og læse tidligere rapporter ved at vælge fanen **Dyb analyse** . Den findes under filoplysningskortene.

Nogle handlinger kræver visse tilladelser. I følgende tabel beskrives, hvilken handling visse tilladelser kan udføre på bærbare eksekverbare filer (PE) og ikke-PE-filer:

|Tilladelse|PE-filer|Ikke-PE-filer|
|---|:---:|:---:|
|Vis data|X|X|
|Undersøgelse af beskeder|&#x2611;|X|
|Grundlæggende livebesvaring|X|X|
|Live response avanceret|&#x2611;|&#x2611;|

Du kan få flere oplysninger om roller under [Opret og administrer roller for rollebaseret adgangskontrol](user-roles.md).

## <a name="stop-and-quarantine-files-in-your-network"></a>Stop og sæt filer i karantæne i dit netværk

Du kan indeholde et angreb i din organisation ved at stoppe den skadelige proces og quarantinere den fil, hvor den blev observeret.

> [!IMPORTANT]
> Du kan kun udføre denne handling, hvis:
>
> - Den enhed, du udfører handlingen på, kører Windows 10 version 1703 eller nyere og Windows 11
> - Filen tilhører ikke tredjepartsudgivere, der er tillid til, eller den er ikke signeret af Microsoft
> - Microsoft Defender Antivirus skal som minimum køre i passiv tilstand. Du kan få flere oplysninger under [Microsoft Defender Antivirus kompatibilitet](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

Handlingen **Stop og sæt filer i karantæne** omfatter stop af kørsel af processer, quarantinering af filerne og sletning af vedvarende data, f.eks. registreringsdatabasenøgler.

Denne handling træder i kraft på enheder med Windows 10, version 1703 eller nyere og Windows 11, hvor filen blev observeret inden for de sidste 30 dage.

> [!NOTE]
> Du kan til enhver tid gendanne filen fra karantænen.

### <a name="stop-and-quarantine-files"></a>Stop og sæt filer i karantæne

1. Vælg den fil, du vil stoppe og sætte i karantæne. Du kan vælge en fil fra en af følgende visninger eller bruge søgefeltet:

   - **Beskeder** – klik på de tilsvarende links på tidslinjen Beskrivelse eller Detaljer på tidslinjen Beskedhistorie
   - **Søgefelt** – vælg **Filer** i rullemenuen, og angiv filnavnet

   > [!NOTE]
   > Handlingen stop- og karantænefil er begrænset til maksimalt 1000 enheder. Hvis du vil stoppe en fil på et større antal enheder, skal du se [Tilføj indikator for at blokere eller tillade fil](#add-indicator-to-block-or-allow-a-file).

2. Gå til den øverste linje, og vælg **Stop og sæt filen i karantæne**.

   :::image type="content" source="images/atp-stop-quarantine-file.png" alt-text="Handlingen Stop og sæt fil i karantæne" lightbox="images/atp-stop-quarantine-file.png":::

3. Angiv en årsag, og vælg derefter **Bekræft**.

   :::image type="content" source="images/atp-stop-quarantine.png" alt-text="Siden med stop- og karantænefiler" lightbox="images/atp-stop-quarantine.png":::

   Oplysningerne om indsendelse vises i Løsningscenter:

   :::image type="content" source="images/atp-stopnquarantine-file.png" alt-text="Handlingscenter for stop- og karantænefiler" lightbox="images/atp-stopnquarantine-file.png":::

   - **Afsendelsestid** – Viser, hvornår handlingen blev sendt.
   - **Success** – Viser antallet af enheder, hvor filen er blevet stoppet og sat i karantæne.
   - **Failed** – Viser antallet af enheder, hvor handlingen mislykkedes, og oplysninger om fejlen.
   - **Pending** – Viser antallet af enheder, hvor filen endnu ikke er stoppet og sat i karantæne. Det kan tage tid i tilfælde, hvor enheden er offline eller ikke har forbindelse til netværket.

4. Vælg en af statusindikatorerne for at få vist flere oplysninger om handlingen. Vælg f.eks **. Mislykkedes** for at se, hvor handlingen mislykkedes.

#### <a name="notification-on-device-userf"></a>Meddelelse på enhedens brugerf

Når filen fjernes fra en enhed, vises følgende meddelelse:

:::image type="content" source="images/atp-notification-file.png" alt-text="Meddelelsen en bruger på enheden" lightbox="images/atp-notification-file.png":::

På enhedens tidslinje tilføjes der en ny hændelse for hver enhed, hvor en fil blev stoppet og sat i karantæne.

Der vises en advarsel, før handlingen implementeres for filer, der bruges i hele organisationen. Det er for at validere, at handlingen er tiltænkt.

## <a name="restore-file-from-quarantine"></a>Gendan fil fra karantæne

Du kan annullere og fjerne en fil fra karantæne, hvis du har fastslået, at den er ren efter en undersøgelse. Kør følgende kommando på hver enhed, hvor filen blev sat i karantæne.

1. Åbn en kommandolinjeprompt med administratorrettigheder på enheden:

   1. Gå til **Start,** og skriv _cmd_.

   1. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```dos
   "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
   ```

   > [!NOTE]
   > I nogle scenarier kan **ThreatName** vises som: EUS:Win32/CustomEnterpriseBlock!cl.
   >
   > Defender for Endpoint gendanner alle brugerdefinerede blokerede filer, der er sat i karantæne på denne enhed inden for de sidste 30 dage.

> [!IMPORTANT]
> En fil, der er sat i karantæne som en potentiel netværkstrussel, kan muligvis ikke genoprettes. Hvis en bruger forsøger at gendanne filen efter karantæne, er filen muligvis ikke tilgængelig. Dette kan skyldes, at systemet ikke længere har netværkslegitimationsoplysninger for at få adgang til filen. Dette er typisk et resultat af en midlertidig logon på et system eller en delt mappe, og adgangstokens er udløbet.

## <a name="download-or-collect-file"></a>Download eller indsaml fil

Hvis du vælger **Download fil** fra svarhandlingerne, kan du downloade et lokalt, adgangskodebeskyttet .zip arkiv, der indeholder filen. Der vises et pop op-vindue, hvor du kan registrere en årsag til at downloade filen og angive en adgangskode.

Som standard skal du kunne downloade filer, der er i karantæne.

:::image type="content" source="images/atp-download-file-action.png" alt-text="Handlingen downloadfil" lightbox="images/atp-download-file-action.png":::

### <a name="download-quarantined-files"></a>Download filer, der er sat i karantæne

Filer, der er sat i karantæne af Microsoft Defender Antivirus eller dit sikkerhedsteam, gemmes på en kompatibel måde i henhold til [dine eksempelkonfigurationer for indsendelse](enable-cloud-protection-microsoft-defender-antivirus.md). Dit sikkerhedsteam kan downloade filerne direkte fra filens detaljeside via knappen "Download fil". **Denne prøveversionsfunktion er som standard slået til**.

Placeringen afhænger af din organisations geoindstillinger (enten EU, Storbritannien eller USA). En karantænefil indsamles kun én gang pr. organisation. Få mere at vide om Microsofts databeskyttelse fra Service Trust Portal på https://aka.ms/STP.

Hvis denne indstilling er slået til, kan det hjælpe sikkerhedsteams med at undersøge potentielt dårlige filer og undersøge hændelser hurtigt og på en mindre risikabel måde. Men hvis du har brug for at slå denne indstilling fra, skal du gå til **Indstillinger** \> **Slutpunkter** \> **Avancerede funktioner** \> **Download filer, der er sat i karantæne**, for at justere indstillingen. [Få mere at vide om avancerede funktioner](advanced-features.md)

#### <a name="backing-up-quarantined-files"></a>Sikkerhedskopierer filer, der er sat i karantæne

Brugerne kan blive bedt om at give eksplicit samtykke, før de sikkerhedskopierer den karantænerede fil, afhængigt af [konfigurationen af indsendelsen af dit eksempel](enable-cloud-protection-microsoft-defender-antivirus.md#use-group-policy-to-turn-on-cloud-protection).

Denne funktion fungerer ikke, hvis eksempelafsendelse er slået fra. Hvis automatisk indsendelse af eksempel er angivet til at anmode om tilladelse fra brugeren, indsamles der kun eksempler, som brugeren accepterer at sende.

> [!IMPORTANT]
> Krav til filer, der er sat i karantæne:
>
> - Din organisation bruger Microsoft Defender Antivirus i aktiv tilstand
> - Antivirusprogramversionen er 1.1.17300.4 eller nyere. Se [Månedlige platform- og programversioner](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)
> - Cloudbaseret beskyttelse er aktiveret. Se [Slå skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) til
> - Eksempelafsendelse er slået til
> - Enheder har Windows 10 version 1703 eller nyere eller Windows server 2016 eller 2019 eller Windows Server 2022 eller Windows 11

### <a name="collect-files"></a>Indsaml filer

Hvis en fil ikke allerede er gemt af Microsoft Defender for Endpoint, kan du ikke downloade den. I stedet får du vist knappen **Indsaml fil** på samme placering. Hvis en fil ikke er blevet set i organisationen inden for de seneste 30 dage, deaktiveres **Collect-filen** .
> [!Important]
> En fil, der er sat i karantæne som en potentiel netværkstrussel, kan muligvis ikke genoprettes. Hvis en bruger forsøger at gendanne filen efter karantæne, er filen muligvis ikke tilgængelig. Dette kan skyldes, at systemet ikke længere har netværkslegitimationsoplysninger for at få adgang til filen. Dette er typisk et resultat af en midlertidig logon på et system eller en delt mappe, og adgangstokens er udløbet.

## <a name="add-indicator-to-block-or-allow-a-file"></a>Tilføj indikator for at blokere eller tillade en fil

Undgå yderligere overførsel af et angreb i din organisation ved at forbyde potentielt skadelige filer eller mistanke om malware. Hvis du kender en potentielt skadelig PE-fil (Portable Executable), kan du blokere den. Denne handling forhindrer, at den læses, skrives eller udføres på enheder i din organisation.

> [!IMPORTANT]
>
> - Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus, og cloudbaseret beskyttelse er aktiveret. Du kan få flere oplysninger under [Administrer skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
>
> - Antimalware-klientversionen skal være 4.18.1901.x eller nyere.
> - Denne funktion er designet til at forhindre, at formodet malware (eller potentielt skadelige filer) downloades fra internettet. Den understøtter i øjeblikket bærbare pe-filer (eksekverbare filer), herunder _.exe_ - og _.dll-filer_ . Dækningen vil blive forlænget over tid.
> - Denne svarhandling er tilgængelig for enheder på Windows 10, version 1703 eller nyere og Windows 11.
> - Funktionen allow eller block kan ikke udføres på filer, hvis filens klassificering findes i enhedens cache før handlingen tillad eller bloker.

> [!NOTE]
> PE-filen skal være på enhedens tidslinje, for at du kan udføre denne handling.
>
> Der kan være et par minutters ventetid mellem det tidspunkt, hvor handlingen udføres, og den faktiske fil, der blokeres.

### <a name="enable-the-block-file-feature"></a>Aktivér funktionen Bloker fil

Hvis du vil starte blokering af filer, skal du først [slå funktionen **Bloker eller Tillad**](advanced-features.md) til i Indstillinger.

### <a name="allow-or-block-file"></a>Tillad eller bloker fil

Når du tilføjer en indikatorhash for en fil, kan du vælge at udløse en besked og blokere filen, når en enhed i organisationen forsøger at køre den.

Filer, der automatisk blokeres af en indikator, vises ikke i filens Løsningscenter, men beskederne vil stadig være synlige i beskedkøen.

Se [Administrer indikatorer](manage-indicators.md) for at få flere oplysninger om blokering og opløftning af beskeder om filer.

Hvis du vil stoppe blokeringen af en fil, skal du fjerne indikatoren. Det kan du gøre via handlingen **Rediger indikator** på filens profilside. Denne handling vil være synlig på samme placering som handlingen **Tilføj indikator** , før du tilføjede indikatoren.

Du kan også redigere indikatorer fra siden **Indstillinger** under **Regelindikatorer**\>. Indikatorer er angivet i dette område efter deres fils hash.

## <a name="consult-a-threat-expert"></a>Kontakt en trusselsekspert

Kontakt en Microsoft-trusselsekspert for at få mere indsigt på en potentielt kompromitteret enhed eller allerede kompromitterede enheder. Microsoft-trusselseksperter er engageret direkte fra Microsoft 365 Defender portalen for at få rettidig og præcis svar. Eksperter giver indsigt på en potentielt kompromitteret enhed og hjælper dig med at forstå komplekse trusler og målrettede angrebsmeddelelser. De kan også angive oplysninger om de beskeder eller en trusselsintelligenskontekst, som du kan se på portaldashboardet.

Se [Kontakt en Microsoft Threat-ekspert](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) for at få flere oplysninger.

## <a name="check-activity-details-in-action-center"></a>Kontrollér aktivitetsdetaljer i Handlingscenter

**Løsningscenter** indeholder oplysninger om handlinger, der er udført på en enhed eller fil. Du kan få vist følgende oplysninger:

- Undersøgelsespakkesamling
- Antivirusscanning
- Appbegrænsning
- Enhedsisolation

Alle andre relaterede oplysninger vises også, f.eks. afsendelsesdato/-klokkeslæt, afsendelsesbruger, og om handlingen lykkedes eller mislykkedes.

:::image type="content" source="images/action-center-details.png" alt-text="Handlingscenteret med oplysninger" lightbox="images/action-center-details.png":::

## <a name="deep-analysis"></a>Dybdegående analyse

Cybersikkerhedsundersøgelser udløses typisk af en besked. Beskeder er relateret til en eller flere observerede filer, der ofte er nye eller ukendte. Når du vælger en fil, kommer du til filvisningen, hvor du kan se filens metadata. Hvis du vil forbedre de data, der er relateret til filen, kan du sende filen til dyb analyse.

Funktionen Dyb analyse udfører en fil i et sikkert, fuldt instrumenteret cloudmiljø. Detaljerede analyseresultater viser filens aktiviteter, observerede funktionsmåder og tilknyttede artefakter, f.eks. mistede filer, ændringer i registreringsdatabasen og kommunikation med IP-adresser.
Dyb analyse understøtter i øjeblikket omfattende analyse af PE-filer (portable executable) (herunder _.exe_ - og _.dll-filer_ ).

Det tager flere minutter at analysere en fil dybt. Når filanalysen er fuldført, opdateres fanen Dyb analyse for at få vist en oversigt og datoen og klokkeslættet for de seneste tilgængelige resultater.

Den dybe analyseoversigt indeholder en liste over observerede *funktionsmåder*, hvoraf nogle kan indikere skadelig aktivitet og *observerede*, herunder kontaktede IP-adresser og filer, der er oprettet på disken. Hvis der ikke blev fundet noget, vises en kort meddelelse i disse afsnit.

Resultaterne af en detaljeret analyse matches mod trusselsintelligens, og eventuelle match genererer relevante beskeder.

Brug funktionen til detaljeret analyse til at undersøge detaljerne for en hvilken som helst fil, som regel under en undersøgelse af en besked eller af andre årsager, hvor du har mistanke om skadelig adfærd. Denne funktion er tilgængelig under fanen **Detaljeret analyse** på filens profilside.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4aAYy?rel=0]

**Send til detaljeret analyse** er aktiveret, når filen er tilgængelig i eksempelsamlingen Defender for Endpoint-backend, eller hvis den blev observeret på en Windows 10 enhed, der understøtter indsendelse til dyb analyse.

> [!NOTE]
> Det er kun filer fra Windows 10 og Windows 11, der kan indsamles automatisk.

Du kan også sende et eksempel via [Microsoft 365 Defender Portal](https://www.microsoft.com/security/portal/submission/submit.aspx), hvis filen ikke blev observeret på en Windows 10 enhed (eller Windows 11), og vente på, at knappen **Indsend til detaljeret analyse** bliver tilgængelig.

> [!NOTE]
> På grund af backend-behandlingsflows i Microsoft 365 Defender-portalen kan der være op til 10 minutters ventetid mellem indsendelse af filer og tilgængeligheden af funktionen til dyb analyse i Defender for Endpoint.

### <a name="submit-files-for-deep-analysis"></a>Indsend filer til dyb analyse

1. Vælg den fil, du vil sende til detaljeret analyse. Du kan vælge eller søge i en fil fra en af følgende visninger:

    - **Beskeder** – vælg fillinks på **tidslinjen Beskrivelse** eller **Detaljer** på tidslinjen Beskedhistorie
    - **Liste over enheder** – vælg fillinks i afsnittet **Beskrivelse** eller **Detaljer** i sektionen **Enhed i organisation**
    - **Søgefelt** – vælg **Filer** i rullemenuen, og angiv filnavnet

2. Under fanen **Detaljeret analyse** i filvisningen skal du vælge **Send**.

   :::image type="content" source="images/submit-file.png" alt-text="Knappen Send PE-filer" lightbox="images/submit-file.png":::

   > [!NOTE]
   > Det er kun PE-filer, der understøttes, herunder _.exe_ og _.dll_ filer.

   Der vises en statuslinje, som indeholder oplysninger om de forskellige faser i analysen. Du kan derefter få vist rapporten, når analysen er færdig.

> [!NOTE]
> Afhængigt af enhedens tilgængelighed kan indsamlingstiden variere. Der er en timeout på 3 timer for eksempelsamling. Samlingen mislykkes, og handlingen afbrydes, hvis der ikke er onlinerapportering Windows 10 enhed (eller Windows 11) på det pågældende tidspunkt. Du kan sende filer igen til dyb analyse for at hente nye data i filen.

### <a name="view-deep-analysis-reports"></a>Få vist detaljerede analyserapporter

Få vist den angivne detaljerede analyserapport for at få mere dybdegående indsigt i den fil, du har sendt. Denne funktion er tilgængelig i konteksten for filvisning.

Du kan få vist den omfattende rapport, der indeholder oplysninger om følgende afsnit:

- Adfærd
- Observables

De angivne oplysninger kan hjælpe dig med at undersøge, om der er tegn på et potentielt angreb.

1. Vælg den fil, du sendte til detaljeret analyse.
2. Vælg fanen **Detaljeret analyse** . Hvis der er tidligere rapporter, vises rapportoversigten under denne fane.

   :::image type="content" source="images/analysis-results-nothing500.png" alt-text="Den detaljerede analyserapport, der viser detaljerede oplysninger på tværs af en række kategorier" lightbox="images/analysis-results-nothing500.png":::

#### <a name="troubleshoot-deep-analysis"></a>Foretag fejlfinding af dyb analyse

Hvis du støder på et problem, når du forsøger at sende en fil, kan du prøve hvert af følgende fejlfindingstrin.

1. Kontrollér, at den pågældende fil er en PE-fil. PE-filer har typisk _.exe_ eller _.dll_ filtypenavne (eksekverbare programmer eller programmer).

2. Kontrollér, at tjenesten har adgang til filen, at den stadig findes, og at den ikke er blevet beskadiget eller ændret.

3. Vent et øjeblik, og prøv at sende filen igen. Køen er muligvis fuld, eller der opstod en midlertidig forbindelses- eller kommunikationsfejl.

4. Hvis politikken for indsamling af eksempler ikke er konfigureret, er standardfunktionsmåden at tillade indsamling af eksempler. Hvis den er konfigureret, skal du kontrollere, at politikindstillingen tillader indsamling af eksempler, før du sender filen igen. Når eksempelsamlingen er konfigureret, skal du kontrollere følgende værdi i registreringsdatabasen:

    ```text
    Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
    Name: AllowSampleCollection
    Type: DWORD
    Hexadecimal value :
      Value = 0 - block sample collection
      Value = 1 - allow sample collection
    ```

5. Skift organisationsenheden via Gruppepolitik. Du kan få flere oplysninger under [Konfigurer med Gruppepolitik](configure-endpoints-gp.md).

6. Hvis disse trin ikke løser problemet, skal du kontakte support.

## <a name="related-topics"></a>Relaterede emner

- [Udfør svarhandlinger på en enhed](respond-machine-alerts.md)
- [Undersøg filer](investigate-files.md)
- [Manuelle svarhandlinger i Microsoft Defender for Endpoint Plan 1](defender-endpoint-plan-1.md#manual-response-actions)
