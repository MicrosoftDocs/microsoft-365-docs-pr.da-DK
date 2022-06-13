---
title: Angiv indstillinger for Microsoft Defender for Endpoint på Linux
ms.reviewer: ''
description: Beskriver, hvordan du konfigurerer Microsoft Defender for Endpoint på Linux i virksomheder.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, deploy, uninstallation, dukke, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: 6c39db3cceec62ef80cf19f34bbf3d89a219a4f3
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042970"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Angiv indstillinger for Microsoft Defender for Endpoint på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Dette emne indeholder instruktioner til, hvordan du angiver indstillinger for Defender for Endpoint på Linux i virksomhedsmiljøer. Hvis du er interesseret i at konfigurere produktet på en enhed fra kommandolinjen, skal du se [Ressourcer](linux-resources.md#configure-from-the-command-line).

I virksomhedsmiljøer kan Defender for Endpoint på Linux administreres via en konfigurationsprofil. Denne profil installeres fra det administrationsværktøj, du vælger. Indstillinger, der administreres af virksomheden, har forrang frem for dem, der er angivet lokalt på enheden. Med andre ord kan brugere i din virksomhed ikke ændre indstillinger, der er angivet via denne konfigurationsprofil. Hvis der blev tilføjet udeladelser via den administrerede konfigurationsprofil, kan de kun fjernes via den administrerede konfigurationsprofil. Kommandolinjen fungerer for undtagelser, der er tilføjet lokalt.

I denne artikel beskrives strukturen af denne profil (herunder en anbefalet profil, som du kan bruge til at komme i gang) og instruktioner til, hvordan du installerer profilen.

## <a name="configuration-profile-structure"></a>Struktur for konfigurationsprofil

Konfigurationsprofilen er en .json-fil, der består af poster, der er identificeret af en nøgle (som angiver navnet på præferencen) efterfulgt af en værdi, som afhænger af typen af præference. Værdier kan være enkle, f.eks. en numerisk værdi eller komplekse, f.eks. en indlejret liste over indstillinger.

Du vil typisk bruge et værktøj til administration af konfiguration til at pushoverføre en fil med navnet ```mdatp_managed.json``` på placeringen ```/etc/opt/microsoft/mdatp/managed/```.

Det øverste niveau i konfigurationsprofilen omfatter indstillinger for hele produktet og poster for underområder af produktet, som forklares mere detaljeret i de næste afsnit.

### <a name="antivirus-engine-preferences"></a>Indstillinger for antivirusprogram

Afsnittet *antivirusEngine* i konfigurationsprofilen bruges til at administrere indstillingerne for produktets antiviruskomponent.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|antivirusEngine|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|

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

|Beskrivelse|Værdi|
|---|---|
|**Tast**|enforcementLevel|
|**Datatype**|String|
|**Mulige værdier**|real_time (standard) <p> on_demand <p> Passiv|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.10.72 eller nyere.|

#### <a name="enabledisable-behavior-monitoring"></a>Aktivér/deaktiver adfærdsovervågning 

Bestemmer, om funktionsmådeovervågning og -blokering er aktiveret på enheden eller ej. Hvis du vil forbedre effektiviteten af sikkerhedsbeskyttelsen, anbefaler vi, at du holder denne funktion aktiveret.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|behaviorMonitoring|
|**Datatype**|String|
|**Mulige værdier**|deaktiveret (standard) <p> Aktiveret|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.45.00 eller nyere.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Kør en scanning, når definitioner er opdateret

Angiver, om en processcanning skal startes, når nye sikkerhedsintelligensopdateringer er downloadet på enheden. Aktivering af denne indstilling udløser en antivirusscanning på de kørende processer på enheden.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanAfterDefinitionUpdate|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.45.00 eller nyere.|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Scan arkiver (kun antivirusscanninger efter behov)

Angiver, om arkiver skal scannes under on-demand-antivirusscanninger.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanArchives|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.45.00 eller nyere.|

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Graden af parallelitet for scanninger efter behov

Angiver graden af parallelitet for scanninger efter behov. Dette svarer til antallet af tråde, der bruges til at udføre scanningen, og påvirker CPU-forbruget samt varigheden af scanningen efter behov.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|maximumOnDemandScanThreads|
|**Datatype**|Heltal|
|**Mulige værdier**|2 (standard). Tilladte værdier er heltal mellem 1 og 64.|
|**Kommentarer**|Tilgængelig i Microsoft Defender for Endpoint version 101.45.00 eller nyere.|

#### <a name="exclusion-merge-policy"></a>Politik for fletning af udeladelse

Angiver flettepolitikken for udeladelser. Det kan være en kombination af administratordefinerede og brugerdefinerede udeladelser (`merge`) eller kun administratordefinerede udeladelser (`admin_only`). Denne indstilling kan bruges til at forhindre lokale brugere i at definere deres egne udeladelser.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|exclusionsMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 100.83.73 eller nyere.|

#### <a name="scan-exclusions"></a>Scan udeladelser

Enheder, der er blevet udelukket fra scanningen. Udeladelser kan angives af fulde stier, filtypenavne eller filnavne.
(Udeladelser er angivet som en matrix af elementer. administratoren kan angive lige så mange elementer, som det er nødvendigt, i vilkårlig rækkefølge).

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Udelukkelser|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|

##### <a name="type-of-exclusion"></a>Type af udeladelse

Angiver den type indhold, der er udeladt fra scanningen.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|$type|
|**Datatype**|String|
|**Mulige værdier**|excludedPath <p> excludedFileExtension <p> excludedFileName|

##### <a name="path-to-excluded-content"></a>Sti til udeladt indhold

Bruges til at udelade indhold fra scanningen ved hjælp af hele filstien.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Sti|
|**Datatype**|String|
|**Mulige værdier**|gyldige stier|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtPath*|

##### <a name="path-type-file--directory"></a>Stitype (fil/mappe)

Angiver, om *stiegenskaben* refererer til en fil eller mappe.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|isDirectory|
|**Datatype**|Boolesk |
|**Mulige værdier**|false (standard) <p> Sandt|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtPath*|

##### <a name="file-extension-excluded-from-the-scan"></a>Filtypenavnet blev udelukket fra scanningen

Bruges til at udelade indhold fra scanningen med filtypenavnet.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Udvidelse|
|**Datatype**|String|
|**Mulige værdier**|gyldige filtypenavne|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtFileExtension*|

##### <a name="process-excluded-from-the-scan"></a>Processen er udelukket fra scanningen*

Angiver en proces, hvor alle filaktiviteter udelades fra scanning. Processen kan angives enten ved hjælp af dens navn (f.eks. `cat`) eller hele stien (f.eks. `/bin/cat`).

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Navn|
|**Datatype**|String|
|**Mulige værdier**|en hvilken som helst streng|
|**Kommentarer**|Gælder kun, hvis *$type* er *udeladtFileName*|

#### <a name="allowed-threats"></a>Tilladte trusler

Liste over trusler (identificeret ved deres navn), der ikke er blokeret af produktet, og som i stedet har tilladelse til at køre.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|allowedThreats|
|**Datatype**|Matrix af strenge|

#### <a name="disallowed-threat-actions"></a>Ikke-tilladte trusselshandlinger

Begrænser de handlinger, som den lokale bruger af en enhed kan foretage, når der registreres trusler. De handlinger, der er inkluderet på denne liste, vises ikke i brugergrænsefladen.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|disallowedThreatActions|
|**Datatype**|Matrix af strenge|
|**Mulige værdier**|allow (begrænser brugernes mulighed for at tillade trusler) <p> gendannelse (begrænser brugere i at gendanne trusler fra karantænen)|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 100.83.73 eller nyere.|

#### <a name="threat-type-settings"></a>Indstillinger for trusselstype

Indstillingen *threatTypeSettings* i antivirusprogrammet bruges til at styre, hvordan visse trusselstyper håndteres af produktet.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|threatTypeSettings|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|

##### <a name="threat-type"></a>Trusselstype

Type af trussel, som funktionsmåden er konfigureret for.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Nøglen|
|**Datatype**|String|
|**Mulige værdier**|potentially_unwanted_application <p> archive_bomb|

##### <a name="action-to-take"></a>Handling, der skal udføres

Handling, der skal udføres, når der opstår en trussel af den type, der er angivet i det foregående afsnit. Kan være:

- **Overvågning**: Enheden er ikke beskyttet mod denne type trussel, men der logføres en post om truslen.
- **Blok**: Enheden er beskyttet mod denne type trussel, og du får besked i sikkerhedskonsollen.
- **Fra**: Enheden er ikke beskyttet mod denne type trussel, og der logføres intet.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Værdi|
|**Datatype**|String|
|**Mulige værdier**|audit (standard) <p> Blok <p> Ud|

#### <a name="threat-type-settings-merge-policy"></a>Politik for fletning af indstillinger for trusselstype

Angiver flettepolitikken for indstillinger for trusselstyper. Dette kan være en kombination af administratordefinerede og brugerdefinerede indstillinger (`merge`) eller kun administratordefinerede indstillinger (`admin_only`). Denne indstilling kan bruges til at begrænse lokale brugere fra at definere deres egne indstillinger for forskellige trusselstyper.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|threatTypeSettingsMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 100.83.73 eller nyere.|

#### <a name="antivirus-scan-history-retention-in-days"></a>Opbevaring af antivirusscanningshistorik (i dage)

Angiv det antal dage, resultaterne bevares i scanningshistorikken på enheden. Gamle scanningsresultater fjernes fra oversigten. Gamle filer i karantæne, der også er fjernet fra disken.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanResultsRetentionDays|
|**Datatype**|String|
|**Mulige værdier**|90 (standard). Tilladte værdier er fra 1 dag til 180 dage.|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.04.76 eller nyere.|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksimalt antal elementer i historikken for antivirusscanning

Angiv det maksimale antal poster, der skal bevares i scanningsoversigten. Poster omfatter alle scanninger efter behov, der er udført tidligere, og alle antivirusregistreringer.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanHistoryMaximumItems|
|**Datatype**|String|
|**Mulige værdier**|10000 (standard). Tilladte værdier er fra 5000 elementer til 15000 elementer.|
|**Kommentarer**|Tilgængelig i Defender for Endpoint version 101.04.76 eller nyere.|

### <a name="cloud-delivered-protection-preferences"></a>Indstillinger for skybaseret beskyttelse

Posten *cloudService* i konfigurationsprofilen bruges til at konfigurere produktets skybaserede beskyttelsesfunktion.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|cloudService|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|

#### <a name="enable--disable-cloud-delivered-protection"></a>Aktivér/deaktiver cloudbaseret beskyttelse

Bestemmer, om skybaseret beskyttelse er aktiveret på enheden eller ej. Hvis du vil forbedre sikkerheden for dine tjenester, anbefaler vi, at du holder denne funktion aktiveret.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Aktiveret|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|

#### <a name="diagnostic-collection-level"></a>Niveau for indsamling af diagnosticering

Diagnosticeringsdata bruges til at holde Defender for Endpoint sikker og opdateret, registrere, diagnosticere og løse problemer og også foretage produktforbedringer. Denne indstilling bestemmer niveauet af diagnosticering, der sendes af produktet til Microsoft.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|diagnosticLevel|
|**Datatype**|String|
|**Mulige værdier**|valgfri (standard) <p> Kræves|

#### <a name="enable--disable-automatic-sample-submissions"></a>Aktivér/deaktiver automatiske eksempelindsendelser

Bestemmer, om mistænkelige eksempler (der sandsynligvis indeholder trusler) sendes til Microsoft. Der er tre niveauer til styring af indsendelse af eksempler:

- **Ingen**: Der sendes ingen mistænkelige eksempler til Microsoft.
- **Pengeskab**: Der sendes kun mistænkelige eksempler, der ikke indeholder personidentificerbare oplysninger, automatisk. Dette er standardværdien for denne indstilling.
- **Alle**: Alle mistænkelige eksempler sendes til Microsoft.

|Beskrivelse|Værdi|
|---|---|
|**Tast**|automaticSampleSubmissionConsent|
|**Datatype**|String|
|**Mulige værdier**|Ingen <p> safe (standard) <p> Alle|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Aktivér/deaktiver automatiske sikkerhedsintelligensopdateringer

Bestemmer, om sikkerhedsintelligensopdateringer installeres automatisk:

|Beskrivelse|Værdi|
|---|---|
|**Tast**|automaticDefinitionUpdateEnabled|
|**Datatype**|Boolesk |
|**Mulige værdier**|true (standard) <p> Falsk|

## <a name="recommended-configuration-profile"></a>Anbefalet konfigurationsprofil

For at komme i gang anbefaler vi følgende konfigurationsprofil, så din virksomhed kan drage fordel af alle de beskyttelsesfunktioner, som Defender for Endpoint indeholder.

Følgende konfigurationsprofil vil:

- Aktivér beskyttelse i realtid (RTP)
- Angiv, hvordan følgende trusselstyper skal håndteres:
  - **Potentielt uønskede programmer (PUA)** er blokeret
  - **Arkivbomber** (fil med en høj komprimeringshastighed) overvåges til produktloggene
- Aktivér automatiske sikkerhedsintelligensopdateringer
- Aktivér skybaseret beskyttelse
- Aktivér automatisk afsendelse af eksempel på `safe` niveau
- Aktivér overvågning af funktionsmåde

### <a name="sample-profile"></a>Eksempelprofil

```JSON
{
   "antivirusEngine":{
      "enforcementLevel":"real_time",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "automaticDefinitionUpdateEnabled":true,
      "automaticSampleSubmissionConsent":"safe",
      "enabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="full-configuration-profile-example"></a>Eksempel på profil med fuld konfiguration

Følgende konfigurationsprofil indeholder poster for alle indstillinger, der er beskrevet i dette dokument, og kan bruges til mere avancerede scenarier, hvor du vil have mere kontrol over produktet.

### <a name="full-profile"></a>Fuld profil

```JSON
{
   "antivirusEngine":{
      "enforcementLevel":"real_time",
      "scanAfterDefinitionUpdate":true,
      "scanArchives":true,
      "maximumOnDemandScanThreads":2,
      "exclusionsMergePolicy":"merge",
      "exclusions":[
         {
            "$type":"excludedPath",
            "isDirectory":false,
            "path":"/var/log/system.log"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/run"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/home/*/git"
         },
         {
            "$type":"excludedFileExtension",
            "extension":".pdf"
         },
         {
            "$type":"excludedFileName",
            "name":"cat"
         }
      ],
      "allowedThreats":[
         "<EXAMPLE DO NOT USE>EICAR-Test-File (not a virus)"
      ],
      "disallowedThreatActions":[
         "allow",
         "restore"
      ],
      "threatTypeSettingsMergePolicy":"merge",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "enabled":true,
      "diagnosticLevel":"optional",
      "automaticSampleSubmissionConsent":"safe",
      "automaticDefinitionUpdateEnabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Føj mærke- eller gruppe-id'et til konfigurationsprofilen

Når du kører kommandoen `mdatp health` for første gang, er værdien for mærket og gruppe-id'et tom. Hvis du vil føje kode- eller gruppe-id'et til `mdatp_managed.json` filen, skal du følge nedenstående trin:
  
  1. Åbn konfigurationsprofilen fra stien `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Gå ned til bunden af filen, hvor `cloudService` blokken er placeret.
  3. Tilføj det påkrævede kode- eller gruppe-id som følgende eksempel i slutningen af den krøllede højreparentes for `cloudService`.

  ```JSON
    },
    "cloudService": {
      "enabled": true,
      "diagnosticLevel": "optional",
      "automaticSampleSubmissionConsent": "safe",
      "automaticDefinitionUpdateEnabled": true,
      "proxy": "http://proxy.server:port/"
  },
  "edr": {
    "groupIds":"GroupIdExample",
    "tags": [
              {
              "key": "GROUP",
              "value": "Tag"
              }
            ]
        }
  }
  ```

  > [!NOTE]
  > Glem ikke at tilføje kommaet efter den afsluttende krøllede parentes i slutningen af `cloudService` blokken. Sørg også for, at der er to krøllede højreparenteser efter tilføjelse af tag- eller gruppe-id-blok (se ovenstående eksempel). I øjeblikket er `GROUP`det eneste understøttede nøglenavn for mærker . 
  
## <a name="configuration-profile-validation"></a>Validering af konfigurationsprofil

Konfigurationsprofilen skal være en gyldig JSON-formateret fil. Der er en række værktøjer, der kan bruges til at bekræfte dette. Hvis du f.eks. har `python` installeret på din enhed:

```bash
python -m json.tool mdatp_managed.json
```

Hvis JSON er korrekt udformet, sender ovenstående kommando den tilbage til Terminal og returnerer en afslutningskode for `0`. Ellers vises en fejl, der beskriver problemet, og kommandoen returnerer en afslutningskode for `1`.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>Kontrollerer, at filen mdatp_managed.json fungerer som forventet

Hvis du vil kontrollere, at din /etc/opt/microsoft/mdatp/managed/mdatp_managed.json fungerer korrekt, skal du se "[managed]" ud for disse indstillinger:

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> Hvis mdatp_managed.json skal træde i kraft, kræves der ingen genstart af dæmonen `mdatp` .

## <a name="configuration-profile-deployment"></a>Udrulning af konfigurationsprofil

Når du har bygget konfigurationsprofilen for din virksomhed, kan du udrulle den via det administrationsværktøj, som din virksomhed bruger. Defender for Endpoint på Linux læser den administrerede konfiguration fra filen */etc/opt/microsoft/mdatp/managed/mdatp_managed.json* .
