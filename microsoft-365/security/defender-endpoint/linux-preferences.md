---
title: Angiv indstillinger for Microsoft Defender til slutpunkt på Linux
ms.reviewer: ''
description: Beskriver, hvordan du konfigurerer Microsoft Defender til slutpunkt på Linux i virksomheder.
keywords: microsoft, defender, Microsoft Defender til slutpunkt, linux, installation, deploy, uninstallation, defender, ansible, linux, redhat, ubuntu, defender, sles, suse, centos
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
ms.openlocfilehash: 8f33208fd605193ec553ffb7901d75148e985fea
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63603103"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Angiv indstillinger for Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Dette emne indeholder instruktioner om, hvordan du angiver indstillinger for Defender for Endpoint på Linux i virksomhedsmiljøer. Hvis du er interesseret i at konfigurere produktet på en enhed fra kommandolinjen, skal du se [Ressourcer](linux-resources.md#configure-from-the-command-line).

I virksomhedsmiljøer kan Defender til slutpunkt på Linux administreres via en konfigurationsprofil. Denne profil installeres fra et administrationsværktøj efter eget valg. Indstillinger, der administreres af virksomheden, tilsidesætter dem, der er angivet lokalt på enheden. Med andre ord kan brugerne i virksomheden ikke ændre de indstillinger, der er angivet via denne konfigurationsprofil.

I denne artikel beskrives strukturen i denne profil (herunder en anbefalet profil, du kan bruge til at komme i gang), og en vejledning i at installere profilen.

## <a name="configuration-profile-structure"></a>Konfiguration af profilstruktur

Konfigurationsprofilen er en .json-fil, der består af poster, der er identificeret med en nøgle (som angiver navnet på præferencen) efterfulgt af en værdi, der afhænger af indstillingens art. Værdier kan være enkle, f.eks. numeriske værdier eller komplekse, f.eks. en indlejret liste over indstillinger.

Du vil typisk bruge et konfigurationsstyringsværktøj til at skubbe en fil med navnet ```mdatp_managed.json``` på placeringen ```/etc/opt/microsoft/mdatp/managed/```.

Det øverste niveau i konfigurationsprofilen omfatter indstillinger og poster for produktets underområde for hele produktet, som er forklaret mere detaljeret i de næste afsnit.

### <a name="antivirus-engine-preferences"></a>Indstillinger for antivirusprogram

Afsnittet *antivirusEngine* i konfigurationsprofilen bruges til at administrere indstillingerne for antiviruskomponenten for produktet.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|antivirusEngine|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|

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

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|enforcementLevel|
|**Datatype**|String|
|**Mulige værdier**|real_time (standard) <p> on_demand <p> passiv|
|**Kommentarer**|Tilgængelig i Defender til Slutpunkt version 101.10.72 eller nyere.|
|


#### <a name="enabledisable-behavior-monitoring"></a>Aktivér/deaktiver behavior-monitoring 

Bestemmer, om funktionsmådeovervågning og blokering er aktiveret på enheden eller ej. For at forbedre effektiviteten af sikkerhedsbeskyttelse anbefaler vi, at du holder denne funktion slået til.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|behaviorMonitoring|
|**Datatype**|String|
|**Mulige værdier**|deaktiveret <p> aktiveret (standard)|
|**Kommentarer**|Tilgængelig i Defender til slutpunktsversion 101.45.00 eller nyere.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Kør en scanning, efter definitioner er opdateret

Angiver, om du vil starte en processcanning, når der er hentet nye sikkerhedsintelligensopdateringer på enheden. Hvis du aktiverer denne indstilling, udløses en antivirusscanning af de kørende processer på enheden.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanAfterDefinitionUpdate|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|**Kommentarer**|Tilgængelig i Defender til slutpunktsversion 101.45.00 eller nyere.|
|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Scan arkiver (kun antivirusscanninger efter behov)

Angiver, om arkiver skal scannes under antivirusscanninger efter behov.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanArchives|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.45.00 eller nyere.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Grad af parallelitet til on-demand-scanninger

Angiver graden af parallelitet for scanninger efter behov. Dette svarer til antallet af tråde, der bruges til at udføre scanningen og påvirker CPU-brugen samt varigheden af scanningen efter behov.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|maximumOnDemandScanThreads|
|**Datatype**|Heltal|
|**Mulige værdier**|2 (standard). Tilladte værdier er heltal mellem 1 og 64.|
|**Kommentarer**|Tilgængelig i Microsoft Defender til slutpunktsversion 101.45.00 eller nyere.|
|||
  

#### <a name="exclusion-merge-policy"></a>Politik for udeladelsesfletning

Angiver fletpolitikken for udeladelse. Det kan være en kombination af administratordefinerede og brugerdefinerede udeladelses undtagelser (`merge`) eller kun administratordefinerede udeladelser (`admin_only`). Denne indstilling kan bruges til at begrænse de lokale brugeres definition af deres egne udeladelser.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|udeladelseMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Defender til Endpoint version 100.83.73 eller nyere.|
|

#### <a name="scan-exclusions"></a>Scanningsudelse

Enheder, der er udeladt af scanningen. Udeladelse kan angives af hele stier, filtypenavne eller filnavne.
Udeladelse er angivet som en matrix med elementer, og administratoren kan angive så mange elementer, som det er nødvendigt, i en hvilken som helst rækkefølge.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|udeladelse|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|

##### <a name="type-of-exclusion"></a>Udeladelsestype

Angiver den type indhold, der udelades fra scanningen.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|$type|
|**Datatype**|String|
|**Mulige værdier**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|

##### <a name="path-to-excluded-content"></a>Sti til udeladt indhold

Bruges til at udelukke indhold fra scanningen ved fuld filsti.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|sti|
|**Datatype**|String|
|**Mulige værdier**|gyldige stier|
|**Kommentarer**|Gælder kun, *hvis $type* er *udeladtPath*|
|

##### <a name="path-type-file--directory"></a>Stitype (fil/mappe)

Angiver, om egenskaben *sti* refererer til en fil eller et bibliotek.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|isDirectory|
|**Datatype**|Boolesk |
|**Mulige værdier**|falsk (standard) <p> sand|
|**Kommentarer**|Gælder kun, *hvis $type* er *udeladtPath*|
|

##### <a name="file-extension-excluded-from-the-scan"></a>Filtypenavnet er udeladt af scanningen

Bruges til at udelukke indhold fra scanningen efter filtypenavn.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|udvidelse|
|**Datatype**|String|
|**Mulige værdier**|gyldige filtypenavne|
|**Kommentarer**|Gælder kun, *$type* er *udeladtFileExtension*|
|

##### <a name="process-excluded-from-the-scan"></a>Processen er udeladt af scanningen*

Angiver en proces, hvor al filaktivitet er udeladt fra scanning. Processen kan angives enten ved dens navn (f.eks. `cat`) eller den fulde sti (f.eks. `/bin/cat`).

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|Navn|
|**Datatype**|String|
|**Mulige værdier**|en hvilken som helst streng|
|**Kommentarer**|Gælder kun, *hvis $type* er *udeladtFilnavn*|
|

#### <a name="allowed-threats"></a>Tilladte trusler

Liste over trusler (identificeres ved deres navn), der ikke er blokeret af produktet, og som i stedet har tilladelse til at køre.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|allowedThreats|
|**Datatype**|Matrix med strenge|
|

#### <a name="disallowed-threat-actions"></a>Ikke tilladte trusselshandlinger

Begrænser de handlinger, som den lokale bruger af en enhed kan udføre, når der registreres trusler. De handlinger, der er medtaget på denne liste, vises ikke i brugergrænsefladen.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|disallowedThreatActions|
|**Datatype**|Matrix med strenge|
|**Mulige værdier**|tillad (begrænser brugere i at tillade trusler) <p> gendannelse (begrænser brugere i at gendanne trusler fra karantæne)|
|**Kommentarer**|Tilgængelig i Defender til Endpoint version 100.83.73 eller nyere.|
|

#### <a name="threat-type-settings"></a>Indstillinger for trusselstype

Indstillingen threatTypeSettings i antivirusprogrammet bruges til at styre, hvordan bestemte *trusselstyper håndteres* af produktet.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|threatTypeSettings|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|

##### <a name="threat-type"></a>Trusselstype

Type af trussel, som funktionsmåden er konfigureret for.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|tast|
|**Datatype**|String|
|**Mulige værdier**|potentially_unwanted_application <p> archive_bomb|
|

##### <a name="action-to-take"></a>Handling, der skal tages

Handling, der skal ske, når der er tale om en trussel af den type, der er angivet i forrige afsnit. Kan være:

- **Overvågning**: Enheden er ikke beskyttet mod denne type af trusler, men en post om truslerne logføres.
- **Bloker**: Enheden er beskyttet mod denne type trusler, og du får besked i sikkerhedskonsollen.
- **Fra**: Enheden er ikke beskyttet mod denne type trussel, og der logføres intet.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|værdi|
|**Datatype**|String|
|**Mulige værdier**|overvågning (standard) <p> bloker <p> fra|
|

#### <a name="threat-type-settings-merge-policy"></a>Politik for sammenfletning af indstillinger for trusselstype

Angiver fletpolitikken for indstillinger for trusselstype. Dette kan være en kombination af administratordefinerede og brugerdefinerede indstillinger (`merge`) eller kun administratordefinerede indstillinger (`admin_only`). Denne indstilling kan bruges til at begrænse de lokale brugere i at definere deres egne indstillinger for forskellige trusselstyper.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|threatTypeSettingsMergePolicy|
|**Datatype**|String|
|**Mulige værdier**|flet (standard) <p> admin_only|
|**Kommentarer**|Tilgængelig i Defender til Endpoint version 100.83.73 eller nyere.|
|

#### <a name="antivirus-scan-history-retention-in-days"></a>Opbevaring af scanningshistorik for antivirus (i dage)

Angiv det antal dage, resultaterne bevares i scanningsoversigten på enheden. Gamle scanningsresultater fjernes fra oversigten. Gamle filer, der er i karantæne, og som også fjernes fra disken.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanResultsRetentionDays|
|**Datatype**|String|
|**Mulige værdier**|90 (standard). Tilladte værdier er fra 1 dag til 180 dage.|
|**Kommentarer**|Tilgængelig i Defender til slutpunktsversion 101.04.76 eller nyere.|
|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Maksimale antal elementer i antivirus-scanningsoversigten

Angiv det maksimale antal poster, der skal bevares i scanningsoversigten. Poster omfatter alle scanninger efter behov, der er udført tidligere, og alle antivirusregistreringer.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|scanHistoryMaximumItems|
|**Datatype**|String|
|**Mulige værdier**|10000 (standard). Tilladte værdier er fra 5.000 elementer til 15.000 elementer.|
|**Kommentarer**|Tilgængelig i Defender til slutpunktsversion 101.04.76 eller nyere.|
|

### <a name="cloud-delivered-protection-preferences"></a>Indstillinger for beskyttelse leveret i skyen

*CloudService-posten* i konfigurationsprofilen bruges til at konfigurere produktets skybaserede beskyttelsesfunktion.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|cloudService|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|

#### <a name="enable--disable-cloud-delivered-protection"></a>Aktivér/deaktiver beskyttelse mod leveret sky

Bestemmer, om cloud-leveret beskyttelse er aktiveret på enheden eller ej. For at forbedre sikkerheden for dine tjenester anbefaler vi, at du holder denne funktion slået til.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|aktiveret|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|

#### <a name="diagnostic-collection-level"></a>Niveauet for diagnosticeringssamling

Diagnostiske data bruges til at holde Defender til Slutpunkt sikker og opdateret, registrere, diagnosticere og løse problemer samt foretage produktforbedringer. Denne indstilling bestemmer niveauet af diagnosticering, der sendes af produktet til Microsoft.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|diagnosticLevel|
|**Datatype**|String|
|**Mulige værdier**|valgfrit (standard) <p> påkrævet|
|

#### <a name="enable--disable-automatic-sample-submissions"></a>Aktivér/deaktiver automatiske indsendelser af eksempler

Bestemmer, om der sendes mistænkelige eksempler (der sandsynligvis indeholder trusler) til Microsoft. Der er tre niveauer til kontrol af prøveindsendelse:

- **Ingen**: Der sendes ingen mistænkelige eksempler til Microsoft.
- **Pengeskab**: Der sendes kun automatisk mistænkelige eksempler, der ikke indeholder personidentificerbare oplysninger (PII). Dette er standardværdien for denne indstilling.
- **Alle**: alle mistænkelige eksempler sendes til Microsoft.

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|automaticSampleSubmissionConsent|
|**Datatype**|String|
|**Mulige værdier**|ingen <p> sikker (standard) <p> alle|
|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Aktivér/deaktiver automatiske sikkerhedsintelligensopdateringer

Bestemmer, om sikkerhedsintelligensopdateringer installeres automatisk:

<br>

****

|Beskrivelse|Værdi|
|---|---|
|**Tast**|automaticDefinitionUpdateEnabled|
|**Datatype**|Boolesk |
|**Mulige værdier**|sand (standard) <p> falsk|
|

## <a name="recommended-configuration-profile"></a>Anbefalet konfigurationsprofil

For at komme i gang anbefaler vi, at du bruger følgende konfigurationsprofil for din virksomhed for at drage fordel af alle de beskyttelsesfunktioner, som Defender til Slutpunkt indeholder.

Følgende konfigurationsprofil vil:

- Aktivér beskyttelse i realtid (RTP)
- Angiv, hvordan følgende trusselstyper skal håndteres:
  - **Potentielt uønskede programmer (PUA)** blokeres
  - **Arkivbomber** (fil med høj komprimeringshastighed) overvåges til produktlogfilerne
- Aktivér automatiske sikkerhedsintelligensopdateringer
- Aktivér skybaseret leveringsbeskyttelse
- Aktivere automatisk indsendelse af eksempler på niveau `safe`
- Aktivér adfærdsovervågning

### <a name="sample-profile"></a>Eksempelprofil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
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

## <a name="full-configuration-profile-example"></a>Eksempel på fuld konfigurationsprofil

Følgende konfigurationsprofil indeholder poster for alle indstillinger, der er beskrevet i dette dokument, og kan bruges til mere avancerede scenarier, hvor du ønsker mere kontrol over produktet.

### <a name="full-profile"></a>Fuld profil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
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

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Føj mærke- eller gruppe-id til konfigurationsprofilen

Når du kører kommandoen `mdatp health` for første gang, er værdien for koden og gruppe-id'et tom. Hvis du vil føje et mærke eller gruppe-id til `mdatp_managed.json` filen, skal du følge nedenstående trin:
  
  1. Åbn konfigurationsprofilen fra stien `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Gå ned til bunden af filen, hvor blokken `cloudService` er placeret.
  3. Tilføj det nødvendige mærke- eller gruppe-id som følgende eksempel i slutningen af den krøllede kantparentes for `cloudService`.

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
  > Husk at tilføje kommaet efter den krøllede højreparentes i slutningen af `cloudService` blokken. Sørg også for, at der er to kantede parenteser, når du har tilføjet Mærke- eller Gruppe-id-blok (se eksemplet ovenfor). Det eneste understøttede nøglenavn for mærker er i øjeblikket `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Konfiguration af profilvalidering

Konfigurationsprofilen skal være en gyldig JSON-formateret fil. Der findes en række værktøjer, der kan bruges til at bekræfte dette. Hvis du f.eks. har `python` installeret på din enhed:

```bash
python -m json.tool mdatp_managed.json
```

Hvis JSON er korrekt, angiver kommandoen ovenfor det tilbage til terminalen og returnerer en udgangskode for `0`. Ellers vises en fejl, der beskriver problemet, og kommandoen returnerer en udgangskode for `1`.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>Kontrollerer, at filen mdatp_managed.json fungerer som forventet

Hvis du vil bekræfte, at din /osv/opt/microsoft/mdatp/managed/mdatp_managed.json fungerer korrekt, skal du se "[administreret]" ud for disse indstillinger:

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> For at mdatp_managed.json træder i kraft, kræves ingen genstart af `mdatp` den deamon.

## <a name="configuration-profile-deployment"></a>Konfiguration af profilinstallation

Når du har oprettet konfigurationsprofilen for din virksomhed, kan du implementere den via det administrationsværktøj, din virksomhed bruger. Defender til Slutpunkt på Linux læser den administrerede konfiguration fra filen */etc/opt/microsoft/mdatp/managed/mdatp_managed.json* .
