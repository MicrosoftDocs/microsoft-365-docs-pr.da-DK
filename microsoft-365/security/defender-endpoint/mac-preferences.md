---
title: Angiv indstillinger for Microsoft Defender for Endpoint på Mac
description: Konfigurer Microsoft Defender til Slutpunkt på Mac i virksomhedsorganisationer.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, management, preferences, enterprise, intune,propf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: cb3f38b861f85849165be330e03fe1d96a9c708c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591312"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>Angiv indstillinger for Microsoft Defender for Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender til Slutpunkt på macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Denne artikel indeholder instruktioner om, hvordan du angiver indstillinger for Microsoft Defender for Endpoint på macOS i virksomhedsorganisationer. Hvis du vil konfigurere Microsoft Defender til Slutpunkt på macOS ved hjælp af kommandolinjegrænsefladen, skal du se [Ressourcer](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>Oversigt

I virksomhedsorganisationer kan Microsoft Defender til slutpunkt på macOS administreres via en konfigurationsprofil, der er installeret ved hjælp af et af flere administrationsværktøjer. Indstillinger, der administreres af sikkerhedsteamet, tilsidesætter de indstillinger, der er angivet lokalt på enheden. Ændring af de indstillinger, der er angivet via konfigurationsprofilen, kræver eskalerede rettigheder og er ikke tilgængelig for brugere uden administrative tilladelser.

Denne artikel beskriver strukturen i konfigurationsprofilen, indeholder en anbefalet profil, som du kan bruge til at komme i gang, og indeholder instruktioner om, hvordan du installerer profilen.

## <a name="configuration-profile-structure"></a>Konfiguration af profilstruktur

Konfigurationsprofilen er en *.plist-fil* , der består af poster, der er identificeret med en nøgle (som angiver navnet på præferencen) efterfulgt af en værdi, der afhænger af indstillingens art. Værdier kan enten være enkle (f.eks. en numerisk værdi) eller komplekse, f.eks. en indlejret liste over indstillinger.

> [!CAUTION]
>Layoutet af konfigurationsprofilen afhænger af den administrationskonsol, du bruger. De følgende afsnit indeholder eksempler på konfigurationsprofiler for JAMF og Intune.

Det øverste niveau i konfigurationsprofilen omfatter indstillinger for hele produktet og poster for underområder af Microsoft Defender til slutpunkt, som er forklaret mere detaljeret i de næste afsnit.

### <a name="antivirus-engine-preferences"></a>Indstillinger for antivirusprogram

Afsnittet *antivirusEngine* i konfigurationsprofilen bruges til at administrere indstillingerne for antiviruskomponenten i Microsoft Defender til slutpunkt.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|antivirusEngine|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="enforcement-level-for-antivirus-engine"></a>Håndhævelsesniveau for antivirusprogrammer

Angiver indstillingen for håndhævelse af antivirusprogrammet. Der findes tre værdier til indstilling af håndhævelsesniveau:

- Beskyttelse i realtid (`real_time`): Beskyttelse i realtid (scanningsfiler, efterhånden som de åbnes) er aktiveret.
- Efter behov (`on_demand`): Filer scannes kun efter behov. I dette:
  - Beskyttelse i realtid er slået fra.
- Passiv (`passive`): Kører antivirusprogrammet i passiv tilstand. I dette:
  - Beskyttelse i realtid er slået fra.
  - Scanning efter behov er slået til.
  - Automatisk afhjælpning af trusler er slået fra.
  - Sikkerhedsintelligensopdateringer er slået til.
  - Ikonet statusmenu er skjult.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|enforcementLevel|
|**Datatype**|String|
|**Mulige værdier**|real_time (standard) <p> on_demand <p> passiv|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.10.72 eller nyere.|
|||

#### <a name="run-a-scan-after-definitions-are-updated"></a>Kør en scanning, efter definitioner er opdateret

Angiver, om du vil starte en processcanning, når der er hentet nye sikkerhedsintelligensopdateringer på enheden. Hvis du aktiverer denne indstilling, udløses en antivirusscanning af de kørende processer på enheden.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanAfterDefinitionUpdate|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.41.10 eller nyere.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Scan arkiver (kun antivirusscanninger efter behov)

Angiver, om arkiver skal scannes under antivirusscanninger efter behov.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanArchives|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.41.10 eller nyere.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Grad af parallelitet til on-demand-scanninger

Angiver graden af parallelitet for scanninger efter behov. Dette svarer til antallet af tråde, der bruges til at udføre scanningen og påvirker CPU-brugen samt varigheden af scanningen efter behov.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|maximumOnDemandScanThreads|
|**Datatype**|Heltal|
|**Mulige værdier**|2 (standard). Tilladte værdier er heltal mellem 1 og 64.|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.41.10 eller nyere.|
|||

#### <a name="exclusion-merge-policy"></a>Politik for udeladelsesfletning

Angiv fletpolitikken for udeladelse. Dette kan være en kombination af administratordefinerede og brugerdefinerede udeladelses undtagelser (`merge`) eller kun administratordefinerede udeladelser (`admin_only`). Denne indstilling kan bruges til at begrænse de lokale brugeres definition af deres egne udeladelser.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|udeladelseMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 100.83.73 eller nyere.|
|||

#### <a name="scan-exclusions"></a>Scanningsudelse

Angiv enheder, der ikke kan scannes. Udeladelse kan angives af hele stier, filtypenavne eller filnavne.
Udeladelse er angivet som en matrix med elementer, og administratoren kan angive så mange elementer, som det er nødvendigt, i en hvilken som helst rækkefølge.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|udeladelse|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

##### <a name="type-of-exclusion"></a>Udeladelsestype

Angiv det indhold, der ikke skal scannes efter type.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|$type|
|**Datatype**|String|
|**Mulige værdier**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>Sti til udeladt indhold

Angiv det indhold, der ikke skal scannes af hele filstien.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|sti|
|**Datatype**|String|
|**Mulige værdier**|gyldige stier|
|**Kommentarer**|Gælder kun, *hvis $type* er *udeladtPath*|
|||

## <a name="supported-exclusion-types"></a>Understøttede udeladelsestyper

Tabellen nedenfor viser de udeladelsestyper, der understøttes af Defender til Slutpunkt på Mac.

<br>

****

|Udeladelse|Definition|Eksempler|
|---|---|---|
|Filtypenavn|Alle filer med udvidelsen, hvor som helst på enheden|`.test`|
|Filer|En bestemt fil identificeret ved den fulde sti|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|Mappe|Alle filer under den angivne mappe (rekursivt)|`/var/log/` <p> `/var/*/`|
|Proces|En bestemt proces (angivet enten af den fulde sti eller filnavnet) og alle filer, der åbnes af den|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> Stierne ovenfor skal være hårde links, ikke symbolske links, for at blive udelukket korrekt. Du kan kontrollere, om en sti er et symbolsk link ved at køre `file <path-name>`.

Fil-, mappe- og procesude udeladelse understøtter følgende jokertegn:

<br>

****

|Jokertegn|Beskrivelse|Eksempel|Matcher|Er ikke ens|
|---|---|---|---|---|
|\*|Finder forekomster af et vilkårligt antal tegn inklusive ingen (bemærk, at når dette jokertegn bruges inde i en sti, erstatter det kun én mappe)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|Matcher et vilkårligt enkelttegn|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>Stitype (fil/mappe)

Angiv, om *egenskaben sti* refererer til en fil eller et bibliotek.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|isDirectory|
|**Datatype**|Boolesk |
|**Mulige værdier**|falsk (standard) <p> sand|
|**Kommentarer**|Gælder kun, *hvis $type* er *udeladtPath*|
|||

### <a name="file-extension-excluded-from-the-scan"></a>Filtypenavnet er udeladt af scanningen

Angiv det indhold, der ikke skal scannes med filtypenavnet.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|udvidelse|
|**Datatype**|String|
|**Mulige værdier**|gyldige filtypenavne|
|**Kommentarer**|Gælder kun, *$type* er *udeladtFileExtension*|
|||

### <a name="process-excluded-from-the-scan"></a>Processen er udeladt af scanningen

Angiv en proces, hvor al filaktivitet er udeladt fra scanning. Processen kan angives enten ved dens navn (f.eks. `cat`) eller den fulde sti (f.eks. `/bin/cat`).

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|Navn|
|**Datatype**|String|
|**Mulige værdier**|en hvilken som helst streng|
|**Kommentarer**|Gælder kun, *hvis $type* er *udeladtFilnavn*|
|||

#### <a name="allowed-threats"></a>Tilladte trusler

Angiv trusler efter navn, der ikke er blokeret af Defender til Slutpunkt på Mac. Disse trusler får tilladelse til at køre.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|allowedThreats|
|**Datatype**|Matrix med strenge|
|||

#### <a name="disallowed-threat-actions"></a>Ikke tilladte trusselshandlinger

Begrænser de handlinger, som den lokale bruger af en enhed kan udføre, når der registreres trusler. De handlinger, der er medtaget på denne liste, vises ikke i brugergrænsefladen.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|disallowedThreatActions|
|**Datatype**|Matrix med strenge|
|**Mulige værdier**|tillad (begrænser brugere i at tillade trusler) <p> gendannelse (begrænser brugere i at gendanne trusler fra karantæne)|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 100.83.73 eller nyere.|
|||

#### <a name="threat-type-settings"></a>Indstillinger for trusselstype

Angiv, hvordan bestemte trusselstyper håndteres af Microsoft Defender for Endpoint på macOS.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|threatTypeSettings|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

##### <a name="threat-type"></a>Trusselstype

Angiv trusselstyper.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|tast|
|**Datatype**|String|
|**Mulige værdier**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>Handling, der skal tages

Angiv, hvilken handling der skal køres, når der registreres en trussel af den type, der er angivet i det foregående afsnit. Vælg mellem følgende indstillinger:

- **Overvågning**: Din enhed er ikke beskyttet mod denne type af trusler, men en post om truslerne logføres.
- **Bloker**: Din enhed er beskyttet mod denne type af trusler, og du får besked i brugergrænsefladen og sikkerhedskonsollen.
- **Fra**: Din enhed er ikke beskyttet mod denne type af trusler, og der logføres intet.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|værdi|
|**Datatype**|String|
|**Mulige værdier**|overvågning (standard) <p> bloker <p> fra|
|||

#### <a name="threat-type-settings-merge-policy"></a>Politik for sammenfletning af indstillinger for trusselstype

Angiv fletpolitikken for indstillinger for trusselstype. Dette kan være en kombination af administratordefinerede og brugerdefinerede indstillinger (`merge`) eller kun administratordefinerede indstillinger (`admin_only`). Denne indstilling kan bruges til at begrænse de lokale brugere i at definere deres egne indstillinger for forskellige trusselstyper.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|threatTypeSettingsMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 100.83.73 eller nyere.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>Opbevaring af scanningshistorik for antivirus (i dage)

Angiv det antal dage, resultaterne bevares i scanningsoversigten på enheden. Gamle scanningsresultater fjernes fra oversigten. Gamle filer, der er i karantæne, og som også fjernes fra disken.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanResultsRetentionDays|
|**Datatype**|String|
|**Mulige værdier**|90 (standard). Tilladte værdier er fra 1 dag til 180 dage.|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.07.23 eller nyere.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksimale antal elementer i antivirus-scanningsoversigten

Angiv det maksimale antal poster, der skal bevares i scanningsoversigten. Poster omfatter alle scanninger efter behov, der er udført tidligere, og alle antivirusregistreringer.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|scanHistoryMaximumItems|
|**Datatype**|String|
|**Mulige værdier**|10000 (standard). Tilladte værdier er fra 5.000 elementer til 15.000 elementer.|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.07.23 eller nyere.|
|||

### <a name="cloud-delivered-protection-preferences"></a>Indstillinger for beskyttelse leveret i skyen

Konfigurer de skybaserede beskyttelsesfunktioner i Microsoft Defender til Endpoint på macOS.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|cloudService|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>Aktivér/deaktiver beskyttelse, der leveres i skyen

Angiv, om du vil aktivere skybaseret beskyttelse af enheden eller ej. For at forbedre sikkerheden for dine tjenester anbefaler vi, at du holder denne funktion slået til.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|aktiveret|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|||

#### <a name="diagnostic-collection-level"></a>Niveauet for diagnosticeringssamling

Diagnostiske data bruges til at holde Microsoft Defender til Slutpunkt sikker og opdateret, registrere, diagnosticere og løse problemer samt foretage produktforbedringer. Denne indstilling bestemmer niveauet af diagnosticering, der sendes af Microsoft Defender til Microsoft Endpoint.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|diagnosticLevel|
|**Datatype**|String|
|**Mulige værdier**|valgfrit (standard) <p> påkrævet|
|||

#### <a name="enable--disable-automatic-sample-submissions"></a>Aktivér/deaktiver automatiske indsendelser af eksempler

Bestemmer, om der sendes mistænkelige eksempler (der sandsynligvis indeholder trusler) til Microsoft. Du bliver spurgt, om den sendte fil sandsynligvis indeholder personlige oplysninger.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|automaticSampleSubmission|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Aktivér/deaktiver automatiske sikkerhedsintelligensopdateringer

Bestemmer, om sikkerhedsintelligensopdateringer installeres automatisk:

<br>

****

|Sektion|Værdi|
|---|---|
|**Tast**|automaticDefinitionUpdateEnabled|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|||

### <a name="user-interface-preferences"></a>Indstillinger for brugergrænsefladen

Administrer indstillingerne for brugergrænsefladen for Microsoft Defender til Slutpunkt på macOS.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|userInterface|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="show--hide-status-menu-icon"></a>Ikonet Vis/skjul statusmenu

Angiv, om statusmenuikonet skal vises eller skjules i øverste højre hjørne af skærmen.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|hideStatusMenuIcon|
|**Datatype**|Boolesk |
|**Mulige værdier**|falsk (standard) <p> sand|
|||

#### <a name="show--hide-option-to-send-feedback"></a>Indstillingen Vis/skjul for at sende feedback

Angiv, om brugere kan sende feedback til Microsoft ved at gå til `Help` > `Send Feedback`.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|userInitiatedFeedback|
|**Datatype**|String|
|**Mulige værdier**|aktiveret (standard) <p> deaktiveret|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.19.61 eller nyere.|
|||



#### <a name="control-sign-in-to-consumer-version-of-microsoft-defender"></a>Kontroller logon til forbrugerversionen af Microsoft Defender

Angiv, om brugerne kan logge på forbrugerversionen af Microsoft Defender.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|forbrugeroplevelse|
|**Datatype**|String|
|**Mulige værdier**|aktiveret (standard) <p> deaktiveret|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.60.18 eller nyere.|
|||


### <a name="endpoint-detection-and-response-preferences"></a>Slutpunktsregistrering og svarindstillinger

Administrer indstillingerne for den slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) komponent i Microsoft Defender til Endpoint på macOS.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|edr|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

#### <a name="device-tags"></a>Enhedsmærker

Angiv et kodenavn og dets værdi.

- MÆRKET GROUP mærker enheden med den angivne værdi. Mærket afspejles i portalen under enhedssiden og kan bruges til filtrering og gruppering af enheder.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|mærker|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|||

##### <a name="type-of-tag"></a>Mærketype

Angiver mærketypen

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|tast|
|**Datatype**|String|
|**Mulige værdier**|`GROUP`|
|||

##### <a name="value-of-tag"></a>Værdi af mærke

Angiver værdien af koden

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|værdi|
|**Datatype**|String|
|**Mulige værdier**|en hvilken som helst streng|
|||

> [!IMPORTANT]
>
> - Der kan kun angives én værdi pr. kodetype.
> - Type af mærker er entydige og må ikke gentages i den samme konfigurationsprofil.

## <a name="recommended-configuration-profile"></a>Anbefalet konfigurationsprofil

For at komme i gang anbefaler vi, at du bruger følgende konfiguration til din virksomhed for at drage fordel af alle de beskyttelsesfunktioner, som Microsoft Defender for Endpoint indeholder.

Følgende konfigurationsprofil (eller, hvis det er tilfældet med SYLF, en egenskabsliste, der kan uploades til konfigurationsprofilen for brugerdefinerede indstillinger) vil:

- Aktivér beskyttelse i realtid (RTP)
- Angiv, hvordan følgende trusselstyper skal håndteres:
  - **Potentielt uønskede programmer (PUA)** blokeres
  - **Arkiveringsbomber** (fil med høj komprimeringshastighed) overvåges til Microsoft Defender til slutpunktslogfiler
- Aktivér automatiske sikkerhedsintelligensopdateringer
- Aktivér skybaseret leveringsbeskyttelse
- Aktivér automatisk indsendelse af eksempler

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>Egenskabsliste for ANBEFALET KONFIGURATIONSprofil

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

### <a name="intune-recommended-profile"></a>Anbefalet profil i Intune

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

## <a name="full-configuration-profile-example"></a>Eksempel på fuld konfigurationsprofil

Følgende skabeloner indeholder poster for alle indstillinger, der er beskrevet i dette dokument, og kan bruges til mere avancerede scenarier, hvor du ønsker mere kontrol over Microsoft Defender til Slutpunkt på macOS.

### <a name="property-list-for-jamf-full-configuration-profile"></a>Egenskabsliste for fuld konfigurationsprofil for SYLF

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

### <a name="intune-full-profile"></a>Intune- fuld profil

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

Hvis filen er korrekt udformet, returnerer kommandoen ovenfor en outputkode `OK` `0`for . Ellers vises en fejl, der beskriver problemet, og kommandoen returnerer en udgangskode for `1`.

## <a name="configuration-profile-deployment"></a>Konfiguration af profilinstallation

Når du har oprettet konfigurationsprofilen for din virksomhed, kan du implementere den via den administrationskonsol, din virksomhed bruger. De følgende afsnit indeholder instruktioner om, hvordan du installerer denne profil ved hjælp af SYLF og Intune.

### <a name="jamf-deployment"></a>JAMF-installation

Fra SYLF-konsollen skal du åbne **Computerkonfigurationsprofiler**\>, gå til den konfigurationsprofil, du vil bruge, og derefter vælge **Brugerdefineret Indstillinger**. Opret en post med som `com.microsoft.wdav` præferencedomæne, og upload *den .plist, der* blev produceret tidligere.

> [!CAUTION]
> Du skal angive det korrekte præferencedomæne (`com.microsoft.wdav`), ellers genkendes indstillingerne ikke af Microsoft Defender til slutpunkt.

### <a name="intune-deployment"></a>Intune-installation

1. Åbn **Administrer enhedskonfiguration**\>. Vælg **Administrer** \> **profiler Opret** \> **profil**.

2. Vælg et navn til profilen. Skift **Platform=macOS** til **Profiltype=Brugerdefineret**. Vælg Konfigurer.

3. Gem .plist-produceres tidligere som `com.microsoft.wdav.xml`.

4. Angiv `com.microsoft.wdav` som navnet på **den brugerdefinerede konfigurationsprofil**.

5. Åbn konfigurationsprofilen, og overfør `com.microsoft.wdav.xml` filen. (Denne fil blev oprettet i trin 3).

6. Vælg **OK**.

7. Vælg **Administrer** \> **opgaver**. På fanen **Medtag** skal du vælge **Tildel til alle brugere & Alle enheder**.

> [!CAUTION]
> Du skal angive det korrekte brugerdefinerede profilnavn for konfigurationen. Ellers genkendes disse indstillinger ikke af Microsoft Defender for Slutpunkt.

## <a name="resources"></a>Ressourcer

- [Henvisning til profilkonfiguration (Apples udviklerdokumentation)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
