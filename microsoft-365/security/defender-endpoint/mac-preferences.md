---
title: Angiv indstillinger for Microsoft Defender for Endpoint på Mac
description: Konfigurer Microsoft Defender for Endpoint på Mac i virksomhedsorganisationer.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, management, præferencer, enterprise, intune, jamf, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ca619bbc2dd81dfe2f7de09186d748a0abb54e4c
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949209"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>Angiv indstillinger for Microsoft Defender for Endpoint på macOS-

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Denne artikel indeholder instruktioner til, hvordan du angiver indstillinger for Microsoft Defender for Endpoint på macOS i virksomhedsorganisationer. Hvis du vil konfigurere Microsoft Defender for Endpoint på macOS ved hjælp af kommandolinjegrænsefladen, skal du se [Ressourcer](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>Oversigt

I virksomhedsorganisationer kan Microsoft Defender for Endpoint på macOS administreres via en konfigurationsprofil, der udrulles ved hjælp af et af flere administrationsværktøjer. Indstillinger, der administreres af teamet for sikkerhedshandlinger, har forrang frem for indstillinger, der er angivet lokalt på enheden. Ændring af de indstillinger, der angives via konfigurationsprofilen, kræver eskalerede rettigheder og er ikke tilgængelig for brugere uden administrative tilladelser.

I denne artikel beskrives strukturen af konfigurationsprofilen, den indeholder en anbefalet profil, som du kan bruge til at komme i gang, og den indeholder instruktioner til, hvordan du installerer profilen.

## <a name="configuration-profile-structure"></a>Struktur for konfigurationsprofil

Konfigurationsprofilen er en *.plist-fil* , der består af poster, der er identificeret af en nøgle (som angiver navnet på præferencen) efterfulgt af en værdi, som afhænger af typen af præference. Værdier kan enten være enkle (f.eks. en numerisk værdi) eller komplekse, f.eks. en indlejret liste over indstillinger.

> [!CAUTION]
>Layoutet af konfigurationsprofilen afhænger af den administrationskonsol, du bruger. Følgende afsnit indeholder eksempler på konfigurationsprofiler til JAMF og Intune.

Det øverste niveau i konfigurationsprofilen omfatter indstillinger for hele produktet og poster for underområder med Microsoft Defender for Endpoint, hvilket forklares mere detaljeret i de næste afsnit.

### <a name="antivirus-engine-preferences"></a>Indstillinger for antivirusprogram

Afsnittet *antivirusEngine* i konfigurationsprofilen bruges til at administrere indstillingerne for antiviruskomponenten i Microsoft Defender for Endpoint.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|antivirusEngine|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="enforcement-level-for-antivirus-engine"></a>Håndhævelsesniveau for antivirusprogram

Angiver, hvordan antivirusprogrammet gennemtvinges. Der er tre værdier til angivelse af håndhævelsesniveau:

- Realtid (`real_time`): Beskyttelse i realtid (scanningsfiler, når de tilgås) er aktiveret.
- On-demand (`on_demand`): Filer scannes kun efter behov. I denne:
  - Beskyttelse i realtid er slået fra.
- Passiv (`passive`): Kører antivirusprogrammet i passiv tilstand. I denne:
  - Beskyttelse i realtid er slået fra.
  - Scanning efter behov er slået til.
  - Automatisk afhjælpning af trusler er slået fra.
  - Opdateringer til sikkerhedsintelligens er slået til.
  - Ikonet statusmenu er skjult.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|enforcementLevel|
|**Datatype**|String|
|**Mulige værdier**|real_time (standard) <p> on_demand <p> Passiv|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.10.72 eller nyere.|
|||

#### <a name="configure-file-hash-computation-feature"></a>Konfigurer funktionen til beregning af filhash

Aktiverer eller deaktiverer funktionen til beregning af filhash. Når denne funktion er aktiveret, beregner Defender for Endpoint hashværdier for filer, der scannes. Bemærk, at aktivering af denne funktion kan påvirke enhedens ydeevne. Du kan finde flere oplysninger i: [Opret indikatorer for filer](indicator-file.md).

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|enableFileHashComputation|
|**Datatype**|String|
|**Mulige værdier**|deaktiveret (standard) <p> Aktiveret|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.73.77 eller nyere.|

#### <a name="run-a-scan-after-definitions-are-updated"></a>Kør en scanning, når definitioner er opdateret

Angiver, om en processcanning skal startes, når nye sikkerhedsintelligensopdateringer er downloadet på enheden. Aktivering af denne indstilling udløser en antivirusscanning på de kørende processer på enheden.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanAfterDefinitionUpdate|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.41.10 eller nyere.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Scan arkiver (kun antivirusscanninger efter behov)

Angiver, om arkiver skal scannes under on-demand-antivirusscanninger.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanArchives|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.41.10 eller nyere.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Graden af parallelitet for scanninger efter behov

Angiver graden af parallelitet for scanninger efter behov. Dette svarer til antallet af tråde, der bruges til at udføre scanningen, og påvirker CPU-forbruget samt varigheden af scanningen efter behov.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|maximumOnDemandScanThreads|
|**Datatype**|Heltal|
|**Mulige værdier**|2 (standard). Tilladte værdier er heltal mellem 1 og 64.|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.41.10 eller nyere.|
|||

#### <a name="exclusion-merge-policy"></a>Politik for fletning af udeladelse

Angiv flettepolitikken for udeladelser. Dette kan være en kombination af administratordefinerede og brugerdefinerede udeladelser (`merge`) eller kun administratordefinerede udeladelser (`admin_only`). Denne indstilling kan bruges til at forhindre lokale brugere i at definere deres egne udeladelser.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|exclusionsMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 100.83.73 eller nyere.|
|||

#### <a name="scan-exclusions"></a>Scan udeladelser

Angiv enheder, der ikke kan scannes. Udeladelser kan angives af fulde stier, filtypenavne eller filnavne.
(Udeladelser er angivet som en matrix af elementer. administratoren kan angive lige så mange elementer, som det er nødvendigt, i vilkårlig rækkefølge).

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Udelukkelser|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

##### <a name="type-of-exclusion"></a>Type af udeladelse

Angiv det indhold, der ikke kan scannes efter type.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|$type|
|**Datatype**|String|
|**Mulige værdier**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>Sti til udeladt indhold

Angiv indhold, der ikke kan scannes af hele filstien.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Sti|
|**Datatype**|String|
|**Mulige værdier**|gyldige stier|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtPath*|
|||

## <a name="supported-exclusion-types"></a>Understøttede udeladelsestyper

I følgende tabel vises de udeladelsestyper, der understøttes af Defender for Endpoint på Mac.

<br>

****

|Udelukkelse|Definition|Eksempler|
|---|---|---|
|Filtypenavn|Alle filer med udvidelsen, hvor som helst på enheden|`.test`|
|Filer|En bestemt fil, der er identificeret af den fulde sti|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|Mappe|Alle filer under den angivne mappe (rekursivt)|`/var/log/` <p> `/var/*/`|
|Proces|En bestemt proces (angivet enten af den fulde sti eller det fulde filnavn) og alle filer, der er åbnet af den|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> Stierne ovenfor skal være hårde links, ikke symbolske links, for at kunne udelukkes. Du kan kontrollere, om en sti er en symbolsk kæde, ved at køre `file <path-name>`.

Fil-, mappe- og procesudeladelser understøtter følgende jokertegn:

<br>

****

|Wildcard|Beskrivelse|Eksempel|Kampe|Stemmer ikke overens|
|---|---|---|---|---|
|\*|Matcher et vilkårligt antal tegn, herunder ingen (bemærk, at når jokertegnet bruges i en sti, erstatter det kun én mappe)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|Matcher et vilkårligt tegn|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>Stitype (fil/mappe)

Angiv, om *stiegenskaben* refererer til en fil eller mappe.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|isDirectory|
|**Datatype**|Boolesk |
|**Mulige værdier**|false (standard) <p> Sandt|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtPath*|
|||

### <a name="file-extension-excluded-from-the-scan"></a>Filtypenavnet blev udelukket fra scanningen

Angiv indhold, der ikke kan scannes af filtypenavnet.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Udvidelse|
|**Datatype**|String|
|**Mulige værdier**|gyldige filtypenavne|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtFileExtension*|
|||

### <a name="process-excluded-from-the-scan"></a>Processen er udelukket fra scanningen

Angiv en proces, hvor al filaktivitet udelades fra scanning. Processen kan angives enten ved hjælp af dens navn (f.eks. `cat`) eller hele stien (f.eks. `/bin/cat`).

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Navn|
|**Datatype**|String|
|**Mulige værdier**|en hvilken som helst streng|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtFileName*|
|||

#### <a name="allowed-threats"></a>Tilladte trusler

Angiv trusler efter navn, der ikke er blokeret af Defender for Endpoint på Mac. Disse trusler vil få lov til at køre.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|allowedThreats|
|**Datatype**|Matrix af strenge|
|||

#### <a name="disallowed-threat-actions"></a>Ikke-tilladte trusselshandlinger

Begrænser de handlinger, som den lokale bruger af en enhed kan foretage, når der registreres trusler. De handlinger, der er inkluderet på denne liste, vises ikke i brugergrænsefladen.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|disallowedThreatActions|
|**Datatype**|Matrix af strenge|
|**Mulige værdier**|allow (begrænser brugernes mulighed for at tillade trusler) <p> gendannelse (begrænser brugere i at gendanne trusler fra karantænen)|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 100.83.73 eller nyere.|
|||

#### <a name="threat-type-settings"></a>Indstillinger for trusselstype

Angiv, hvordan visse trusselstyper håndteres af Microsoft Defender for Endpoint på macOS.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|threatTypeSettings|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

##### <a name="threat-type"></a>Trusselstype

Angiv trusselstyper.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Nøglen|
|**Datatype**|String|
|**Mulige værdier**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>Handling, der skal udføres

Angiv, hvilken handling der skal udføres, når der registreres en trussel af den type, der er angivet i foregående afsnit. Vælg mellem følgende indstillinger:

- **Overvågning**: Enheden er ikke beskyttet mod denne type trussel, men der logføres en post om truslen.
- **Blok**: Enheden er beskyttet mod denne type trussel, og du får besked i brugergrænsefladen og i sikkerhedskonsollen.
- **Fra**: Enheden er ikke beskyttet mod denne type trussel, og der logføres intet.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Værdi|
|**Datatype**|String|
|**Mulige værdier**|audit (standard) <p> Blok <p> Ud|
|||

#### <a name="threat-type-settings-merge-policy"></a>Politik for fletning af indstillinger for trusselstype

Angiv flettepolitikken for indstillinger for trusselstyper. Dette kan være en kombination af administratordefinerede og brugerdefinerede indstillinger (`merge`) eller kun administratordefinerede indstillinger (`admin_only`). Denne indstilling kan bruges til at begrænse lokale brugere fra at definere deres egne indstillinger for forskellige trusselstyper.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|threatTypeSettingsMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 100.83.73 eller nyere.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>Opbevaring af antivirusscanningshistorik (i dage)

Angiv det antal dage, resultaterne bevares i scanningshistorikken på enheden. Gamle scanningsresultater fjernes fra oversigten. Gamle filer i karantæne, der også er fjernet fra disken.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanResultsRetentionDays|
|**Datatype**|String|
|**Mulige værdier**|90 (standard). Tilladte værdier er fra 1 dag til 180 dage.|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.07.23 eller nyere.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksimalt antal elementer i historikken for antivirusscanning

Angiv det maksimale antal poster, der skal bevares i scanningsoversigten. Poster omfatter alle scanninger efter behov, der er udført tidligere, og alle antivirusregistreringer.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanHistoryMaximumItems|
|**Datatype**|String|
|**Mulige værdier**|10000 (standard). Tilladte værdier er fra 5000 elementer til 15000 elementer.|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.07.23 eller nyere.|
|||

### <a name="cloud-delivered-protection-preferences"></a>Indstillinger for skybaseret beskyttelse

Konfigurer skydrevne beskyttelsesfunktioner i Microsoft Defender for Endpoint på macOS.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|cloudService|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>Aktivér/deaktiver skybaseret beskyttelse

Angiv, om enheden skal aktivere skybaseret beskyttelse. Hvis du vil forbedre sikkerheden for dine tjenester, anbefaler vi, at du holder denne funktion aktiveret.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Aktiveret|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|||

#### <a name="diagnostic-collection-level"></a>Niveau for indsamling af diagnosticering

Diagnosticeringsdata bruges til at holde Microsoft Defender for Endpoint sikre og opdaterede, registrere, diagnosticere og løse problemer og også foretage produktforbedringer. Denne indstilling bestemmer niveauet af diagnosticering, der sendes af Microsoft Defender for Endpoint til Microsoft.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|diagnosticLevel|
|**Datatype**|String|
|**Mulige værdier**|valgfri (standard) <p> Kræves|
|||

#### <a name="configure-cloud-block-level"></a>Konfigurer niveau for skyblokering

Denne indstilling bestemmer, hvor aggressiv Defender for Endpoint vil være i forbindelse med blokering og scanning af mistænkelige filer. Hvis denne indstilling er slået til, vil Defender for Endpoint være mere aggressiv, når du identificerer mistænkelige filer, der skal blokeres og scannes. ellers vil det være mindre aggressivt og derfor blokere og scanne med mindre hyppighed. Der er fem værdier til angivelse af skyblokeringsniveau:

- Normal (`normal`): Standardblokeringsniveauet.
- Moderat (`moderate`): Leverer kun dom for registreringer med høj genkendelsessikkerhed.
- Høj (`high`): Blokerer aggressivt ukendte filer, samtidig med at de optimeres til ydeevne (større chance for at blokere ikke-skadelige filer).
- High Plus (`high_plus`): Blokerer ukendte filer aggressivt og anvender yderligere beskyttelsesforanstaltninger (kan påvirke klientens enheds ydeevne).
- Nultolerance (`zero_tolerance`): Blokerer alle ukendte programmer.

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|cloudBlockLevel|
|**Datatype**|String|
|**Mulige værdier**|normal (standard) <p> Moderat <p> Høj <p> high_plus <p> zero_tolerance|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.56.62 eller nyere.|

#### <a name="enable--disable-automatic-sample-submissions"></a>Aktivér/deaktiver automatiske eksempelindsendelser

Bestemmer, om mistænkelige eksempler (der sandsynligvis indeholder trusler) sendes til Microsoft. Du bliver spurgt, om den sendte fil sandsynligvis indeholder personlige oplysninger.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|automaticSampleSubmission|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Aktivér/deaktiver automatiske sikkerhedsintelligensopdateringer

Bestemmer, om sikkerhedsintelligensopdateringer installeres automatisk:

<br>

****

|Afsnit|Værdi|
|---|---|
|**Tast**|automaticDefinitionUpdateEnabled|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|||

### <a name="user-interface-preferences"></a>Indstillinger for brugergrænseflade

Administrer indstillingerne for brugergrænsefladen for Microsoft Defender for Endpoint på macOS.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|userInterface|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="show--hide-status-menu-icon"></a>Vis/skjul ikonet for statusmenu

Angiv, om ikonet for statusmenuen skal vises eller skjules i øverste højre hjørne af skærmen.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|hideStatusMenuIcon|
|**Datatype**|Boolesk |
|**Mulige værdier**|false (standard) <p> Sandt|
|||

#### <a name="show--hide-option-to-send-feedback"></a>Vis/skjul muligheden for at sende feedback

Angiv, om brugerne kan sende feedback til Microsoft ved at gå til `Help` > `Send Feedback`.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|userInitiatedFeedback|
|**Datatype**|String|
|**Mulige værdier**|aktiveret (standard) <p> Deaktiveret|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.19.61 eller nyere.|
|||



#### <a name="control-sign-in-to-consumer-version-of-microsoft-defender"></a>Kontrollér logon til forbrugerversionen af Microsoft Defender

Angiv, om brugerne kan logge på forbrugerversionen af Microsoft Defender.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|consumerExperience|
|**Datatype**|String|
|**Mulige værdier**|aktiveret (standard) <p> Deaktiveret|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.60.18 eller nyere.|
|||


### <a name="endpoint-detection-and-response-preferences"></a>Indstillinger for registrering af slutpunkter og svar

Administrer EDR-komponenten (endpoint detection and response) for Microsoft Defender for Endpoint på macOS.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Edr|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="device-tags"></a>Enhedstags

Angiv et kodenavn og dets værdi.

- Tagget GROUP, mærker enheden med den angivne værdi. Koden afspejles på portalen under enhedssiden og kan bruges til filtrering og gruppering af enheder.

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Tags|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

##### <a name="type-of-tag"></a>Mærketype

Angiver kodetypen

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Nøglen|
|**Datatype**|String|
|**Mulige værdier**|`GROUP`|
|||

##### <a name="value-of-tag"></a>Kodeværdi

Angiver kodens værdi

<br>

****

|Afsnit|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Værdi|
|**Datatype**|String|
|**Mulige værdier**|en hvilken som helst streng|
|||

> [!IMPORTANT]
>
> - Der kan kun angives én værdi pr. kodetype.
> - Kodetypen er entydig og må ikke gentages i den samme konfigurationsprofil.

## <a name="recommended-configuration-profile"></a>Anbefalet konfigurationsprofil

For at komme i gang anbefaler vi følgende konfiguration, så din virksomhed kan drage fordel af alle de beskyttelsesfunktioner, Microsoft Defender for Endpoint indeholder.

Følgende konfigurationsprofil (eller i tilfælde af JAMF en egenskabsliste, der kan uploades til konfigurationsprofilen for brugerdefinerede indstillinger) vil:

- Aktivér beskyttelse i realtid (RTP)
- Angiv, hvordan følgende trusselstyper skal håndteres:
  - **Potentielt uønskede programmer (PUA)** er blokeret
  - **Arkivbomber** (fil med en høj komprimeringshastighed) overvåges for at Microsoft Defender for Endpoint logfiler
- Aktivér automatiske sikkerhedsintelligensopdateringer
- Aktivér skybaseret beskyttelse
- Aktivér automatisk afsendelse af eksempel

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>Egenskabsliste for den anbefalede konfigurationsprofil JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
</dict>
</plist>
```

### <a name="intune-recommended-profile"></a>Intune anbefalede profil

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="full-configuration-profile-example"></a>Eksempel på profil med fuld konfiguration

Følgende skabeloner indeholder poster til alle de indstillinger, der er beskrevet i dette dokument, og kan bruges til mere avancerede scenarier, hvor du vil have mere kontrol over Microsoft Defender for Endpoint på macOS.

### <a name="property-list-for-jamf-full-configuration-profile"></a>Egenskabsliste for fuld JAMF-konfigurationsprofil

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>scanAfterDefinitionUpdate</key>
        <true/>
        <key>scanArchives</key>
        <true/>
        <key>maximumOnDemandScanThreads</key>
        <integer>2</integer>
        <key>exclusions</key>
        <array>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <false/>
                <key>path</key>
                <string>/var/log/system.log</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/home</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/Users/*/git</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileExtension</string>
                <key>extension</key>
                <string>pdf</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileName</string>
                <key>name</key>
                <string>cat</string>
            </dict>
        </array>
        <key>exclusionsMergePolicy</key>
        <string>merge</string>
        <key>allowedThreats</key>
        <array>
            <string>EICAR-Test-File (not a virus)</string>
        </array>
        <key>disallowedThreatActions</key>
        <array>
            <string>allow</string>
            <string>restore</string>
        </array>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
        <key>threatTypeSettingsMergePolicy</key>
        <string>merge</string>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>diagnosticLevel</key>
        <string>optional</string>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
    <key>edr</key>
    <dict>
        <key>tags</key>
        <array>
            <dict>
                <key>key</key>
                <string>GROUP</string>
                <key>value</key>
                <string>ExampleTag</string>
            </dict>
        </array>
    </dict>
    <key>userInterface</key>
    <dict>
        <key>hideStatusMenuIcon</key>
        <false/>
        <key>userInitiatedFeedback</key>
        <string>enabled</string>
    </dict>
</dict>
</plist>
```

### <a name="intune-full-profile"></a>Intune fuld profil

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>scanAfterDefinitionUpdate</key>
                    <true/>
                    <key>scanArchives</key>
                    <true/>
                    <key>maximumOnDemandScanThreads</key>
                    <integer>1</integer>
                    <key>exclusions</key>
                    <array>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <false/>
                            <key>path</key>
                            <string>/var/log/system.log</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/home</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/Users/*/git</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileExtension</string>
                            <key>extension</key>
                            <string>pdf</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileName</string>
                            <key>name</key>
                            <string>cat</string>
                        </dict>
                    </array>
                    <key>exclusionsMergePolicy</key>
                    <string>merge</string>
                    <key>allowedThreats</key>
                    <array>
                        <string>EICAR-Test-File (not a virus)</string>
                    </array>
                    <key>disallowedThreatActions</key>
                    <array>
                        <string>allow</string>
                        <string>restore</string>
                    </array>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                    <key>threatTypeSettingsMergePolicy</key>
                    <string>merge</string>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>diagnosticLevel</key>
                    <string>optional</string>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
                <key>edr</key>
                <dict>
                    <key>tags</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>GROUP</string>
                            <key>value</key>
                            <string>ExampleTag</string>
                        </dict>
                    </array>
                </dict>
                <key>userInterface</key>
                <dict>
                    <key>hideStatusMenuIcon</key>
                    <false/>
                    <key>userInitiatedFeedback</key>
                    <string>enabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="property-list-validation"></a>Validering af egenskabsliste

Egenskabslisten skal være en gyldig *.plist-fil* . Dette kan kontrolleres ved at udføre:

```bash
plutil -lint com.microsoft.wdav.plist
```

```Output
com.microsoft.wdav.plist: OK
```

Hvis filen er korrekt udformet, oprettes ovenstående kommando, og der returneres `OK` en afslutningskode for `0`. Ellers vises en fejl, der beskriver problemet, og kommandoen returnerer en afslutningskode for `1`.

## <a name="configuration-profile-deployment"></a>Udrulning af konfigurationsprofil

Når du har bygget konfigurationsprofilen for din virksomhed, kan du udrulle den via den administrationskonsol, som din virksomhed bruger. Følgende afsnit indeholder instruktioner til, hvordan du installerer denne profil ved hjælp af JAMF og Intune.

### <a name="jamf-deployment"></a>JAMF-udrulning

Åbn **Computers** \> **Configuration Profiles** i JAMF-konsollen, naviger til den konfigurationsprofil, du vil bruge, og vælg derefter **Brugerdefinerede indstillinger**. Opret en post med `com.microsoft.wdav` som det foretrukne domæne, og upload den *.plist* , der blev oprettet tidligere.

> [!CAUTION]
> Du skal angive det korrekte præferencedomæne (`com.microsoft.wdav`). Ellers genkendes indstillingerne ikke af Microsoft Defender for Endpoint.

### <a name="intune-deployment"></a>Intune installation

1. Åbn **Administrer** \> **enhedskonfiguration**. Vælg **Administrer** \> **profiler** \> **Opret profil**.

2. Vælg et navn til profilen. Skift **Platform=macOS** til **Profiltype=Brugerdefineret**. Vælg Konfigurer.

3. Gem den .plist, der blev oprettet tidligere som `com.microsoft.wdav.xml`.

4. Angiv `com.microsoft.wdav` som **navnet på den brugerdefinerede konfigurationsprofil**.

5. Åbn konfigurationsprofilen, og upload `com.microsoft.wdav.xml` filen. Denne fil blev oprettet i trin 3.

6. Vælg **OK**.

7. Vælg **Administrer** \> **tildelinger**. Under fanen **Medtag** skal du vælge **Tildel til alle brugere & Alle enheder**.

> [!CAUTION]
> Du skal angive det korrekte navn på den brugerdefinerede konfigurationsprofil. Ellers genkendes disse indstillinger ikke af Microsoft Defender for Endpoint.

## <a name="resources"></a>Ressourcer

- [Henvisning til profilkonfiguration (Apples udviklerdokumentation)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
