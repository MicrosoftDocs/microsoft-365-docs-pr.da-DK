---
title: Undersøg enheder på enheder, der bruger direkte svar Microsoft Defender for Endpoint
description: Få adgang til en enhed ved hjælp af en sikker ekstern shell-forbindelse for at udføre samtidig arbejde og udføre øjeblikkelige svarhandlinger på en enhed i realtid.
keywords: remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file,
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
ms.openlocfilehash: 8987c5642ea48e4c7887735cc0fce0e5bfccc119
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470389"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Undersøg enheder på enheder, der bruger direkte svar

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Livesvar giver sikkerhedsteams øjeblikkelig adgang til en enhed (også kaldet en maskine), der bruger en forbindelse til en fjern shell. Dette giver dig mulighed for at udføre en dybdegående indsats og reagere omgående for at kunne inddæmme identificerede trusler i realtid.

Liverespons er designet til at forbedre undersøgelser ved at give dit sikkerhedsteam mulighed for at indsamle analysere data, køre scripts, sende mistænkelige enheder til analyse, afhjælpe trusler og proaktivt lede efter nye trusler.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Med live respons kan analytikere udføre alle følgende opgaver:

- Kør grundlæggende og avancerede kommandoer for at udføre arbejdsområdet på en enhed.
- Download filer som f.eks. malwareeksempler og resultater af PowerShell-scripts.
- Download filer i baggrunden (ny!).
- Upload et PowerShell-script eller eksekverbar til biblioteket, og kør det på en enhed fra et lejerniveau.
- Tag eller fortryd afhjælpningshandlinger.

## <a name="before-you-begin"></a>Før du begynder

Før du kan starte en session på en enhed, skal du opfylde følgende krav:

- **Kontrollér, at du kører en understøttet version af Windows**.

  Enheder skal køre en af følgende versioner af Windows

  - **Windows 10 & 11**
    - [Version 1909](/windows/whats-new/whats-new-windows-10-version-1909) eller nyere
    - [Version 1903](/windows/whats-new/whats-new-windows-10-version-1903) med [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Version 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) [med KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Version 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) med [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Version 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) med [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **macOS** – Gælder kun for offentlig prøveversion, minimumskravet version: 101.43.84 
  
   > [!NOTE]
   > I øjeblikket understøttes kun Intel-baserede macOS-systemer.
    

  - **Linux** – Gælder kun for offentlig prøveversion, minimumskravet version: 101.45.13 
    
  - **Windows Server 2012 R2** – med [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)
  
  - **Windows Server 2016** – med [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Version 1903 eller (med [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)) senere
    - Version 1809 (med [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

       

- **Aktivér direkte svar fra siden avancerede indstillinger**.

  Du skal aktivere live svar-funktionen på siden [Avancerede funktioner.](advanced-features.md)

  > [!NOTE]
  > Det er kun brugere med administratorroller til administration eller globale administratorer, der kan redigere disse indstillinger.
  > 
  > Automatisk undersøgelse skal være aktiveret i [indstillingerne for Avancerede funktioner](advanced-features.md) , før du aktiverer livesvar.

- **Aktivér live-svar for servere fra siden avancerede indstillinger** (anbefales).

  > [!NOTE]
  > Det er kun brugere med administratorroller til administration eller globale administratorer, der kan redigere disse indstillinger.

- **Sørg for, at enheden har tildelt et niveau til afhjælpning af automatisering**.

  Du skal som minimum aktivere minimumniveauet for afhjælpning for en given enhedsgruppe. Ellers kan du ikke oprette en Direkte svarsession til et medlem af den pågældende gruppe.

  Du får vist følgende fejlmeddelelse:

  :::image type="content" source="images/live-response-error.png" alt-text="Fejlmeddelelsen" lightbox="images/live-response-error.png":::

- **Aktivér direkte svar usigneret scriptudførelse** (valgfrit).

  >[!IMPORTANT]
  >Signaturbekræftelse gælder kun for PowerShell-scripts. 

  > [!WARNING]
  > Hvis du tillader brug af usignerede scripts, kan det øge din eksponering for trusler.

  Det anbefales ikke at køre usignerede scripts, da det kan øge din eksponering for trusler. Hvis du skal bruge dem, skal du aktivere indstillingen på siden [Avancerede indstillinger for](advanced-features.md) funktioner.

- **Sørg for, at du har de rette tilladelser**.

  Kun brugere, der er blevet klargjort med de relevante tilladelser, kan starte en session. Du kan finde flere oplysninger om rolletildelinger [i Opret og administrer roller](user-roles.md).

  > [!IMPORTANT]
  > Muligheden for at overføre en fil til biblioteket er kun tilgængelig for brugere med tilladelsen "Administrer Indstillinger".
  > Knappen er nedtonet for brugere, der kun har delegerede tilladelser.

  Afhængigt af den rolle, du har fået tildelt, kan du køre grundlæggende eller avancerede Live Response-kommandoer. Brugertilladelser styres af den brugerdefinerede RBAC-rolle.

## <a name="live-response-dashboard-overview"></a>Oversigt over live svar-dashboard

Når du starter en direkte svarsession på en enhed, åbnes der et dashboard. Dashboardet indeholder oplysninger om sessionen, f.eks. følgende:

- Who oprettede sessionen
- Da sessionen startede
- Sessionens varighed

Dashboardet giver dig også adgang til:

- Afbryd session
- Upload filer til biblioteket
- Kommandokonsol
- Kommandolog

## <a name="initiate-a-live-response-session-on-a-device"></a>Starte en direkte svarsession på en enhed

1. Log på Microsoft 365 Defender portal.

2. Gå til **Slutpunkter > lagerenhed, og** vælg en enhed, der skal undersøges. Siden enheder åbnes.

3. Start den direkte svarsession ved at vælge **Påbegynde direkte svarsession**. Der vises en kommandokonsol. Vent, mens sessionen opretter forbindelse til enheden.

4. Brug de indbyggede kommandoer til at udføre lige arbejde. Du kan få mere at vide [under Kommandoer for direkte svar](#live-response-commands).

5. Når du er færdig med undersøgelsen, skal du **vælge Afbryd session** og derefter **vælge Bekræft**.

## <a name="live-response-commands"></a>Kommandoer for direkte svar

Afhængigt af den rolle, du har fået tildelt, kan du køre grundlæggende eller avancerede Live Response-kommandoer. Brugertilladelser styres af RBAC-brugerdefinerede roller. Du kan finde flere oplysninger om rolletildelinger [i Opret og administrer roller](user-roles.md).

> [!NOTE]
> Live-svar er en skybaseret interaktiv shell, som f.eks. kan en specifik kommandooplevelse variere i svartid afhængigt af netværkskvaliteten og systembelastningen mellem slutbrugeren og destinationsenheden.

### <a name="basic-commands"></a>Grundlæggende kommandoer

Følgende kommandoer er tilgængelige for brugerroller, der får mulighed for at køre **grundlæggende** Live Response-kommandoer. Du kan finde flere oplysninger om rolletildelinger [i Opret og administrer roller](user-roles.md).

<br>

****
| Kommando  | Beskrivelse  | Windows og Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| cd  | Ændrer den aktuelle mappe.  | Y  | Y  | Y  |
| cls  | Rydder konsolskærmen.  | Y  | Y  | Y  |
| opret forbindelse  | Starter en direkte svarsession på enheden.  | Y  | Y  | Y  |
| forbindelser  | Viser alle de aktive forbindelser.  | Y  | N  | N  |
| dir  | Viser en liste over filer og undermapper i en mappe.  | Y  | Y  | Y  |
| drivere  | Viser alle drivere, der er installeret på enheden.  | Y  | N  | N  |
| fg `<command ID>`  | Placer det angivne job i forgrunden i forgrunden, hvilket gør det til det aktuelle job.  BEMÆRK: fg får et "kommando-id" tilgængeligt fra jobs, ikke et PID  | Y  | Y  | Y  |
| fileinfo  | Få oplysninger om en fil.  | Y  | Y  | Y  |
| findfile  | Finder filer efter et givet navn på enheden.  | Y  | Y  | Y  |
| getfile <file_path>  | Downloader en fil.  | Y  | Y  | Y  |
| Hjælp  | Indeholder hjælpoplysninger til kommandoer til direkte svar.  | Y  | Y  | Y  |
| jobs  | Viser aktuelt kørende job, deres id og status.  | Y  | Y  | Y  |
| vedholdenhed  | Viser alle kendte metoder til vedholdende brug på enheden.  | Y  | N  | N  |
| processer  | Viser alle processer, der kører på enheden.  | Y  | Y  | Y  |
| registreringsdatabase  | Viser registreringsdatabaseværdier.  | Y  | N  | N  |
| planlagte opgaver  | Viser alle planlagte opgaver på enheden.  | Y  | N  | N  |
| tjenester  | Viser alle tjenester på enheden.  | Y  | N  | N  |
| startmapper  | Viser alle kendte filer i startmapper på enheden.  | Y  | N  | N  |
| status  | Viser status og output for en bestemt kommando.  | Y  | N  | N  |
| spor  | Indstiller terminalens logføringstilstand til fejlfinding.  | Y  | Y  | Y  |

### <a name="advanced-commands"></a>Avancerede kommandoer

Følgende kommandoer er tilgængelige for brugerroller, der får mulighed for at køre **avancerede** Live Response-kommandoer. Du kan finde flere oplysninger om rolletildelinger [i Opret og administrer roller](user-roles.md).

<br>

****

| Kommando  | Beskrivelse  | Windows og Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| analysér  | Analyserer enheden med forskellige inkriminationsmotorer for at opnå en konklusion.  | Y  | N  | N  |
| indsaml  | Indsamler pakker fra maskiner  | N  | Y  | Y  |
| isoler  | Afbryder forbindelsen mellem enheden og netværket, mens forbindelsen til Defender for Endpoint-tjenesten bevares  | N  | Y  | N  |
| version  | Frigør en enhed fra netværksisolation  | N  | Y  | N  |
| kør  | Kører et PowerShell-script fra biblioteket på enheden.  | Y  | Y  | Y  |
| bibliotek  | Viser filer, der er blevet overført til live response-biblioteket.  | Y  | Y  | Y  |
| putfile  | Placerer en fil fra biblioteket til enheden. Filer gemmes i en arbejdsmappe og slettes, når enheden genstarter som standard.  | Y  | Y  | Y  |
| afhjælpe  | Afhjælper en enhed på enheden. Afhjælpningshandlingen varierer afhængigt af enhedstypen: Fil: Slet Proces: stop, slet billedfiltjeneste: stop, slet billedfil Registreringsdatabasepost: slet Planlagt opgave: fjern mappeelementet Start: slet fil BEMÆRK: Denne kommando har en nødvendige kommando. Du kan bruge kommandoen -auto sammen med remediate til automatisk at køre kommandoen, der er nødvendige for at udføre forudsætningerne.  | Y  | Y  | Y  |
| scan | Kører en antivirusscanning for at identificere og afhjælpe malware. | N | Y | Y |
| fortryd  | Gendanner en enhed, der blev løst.  | Y  | Y  | Y  |


## <a name="use-live-response-commands"></a>Brug af live svarkommandoer

De kommandoer, du kan bruge i konsollen, følger de samme principper [som Windows Kommandoer](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

De avancerede kommandoer giver et mere robust sæt handlinger, der giver dig mulighed for at udføre mere effektive handlinger som download og upload af en fil, køre scripts på enheden og udføre afhjælpningshandlinger på en enhed.

### <a name="get-a-file-from-the-device"></a>Hent en fil fra enheden

Du kan bruge kommandoen til scenarier, hvor du vil hente en fil fra en enhed, du er ved at `getfile` undersøge. Dette giver dig mulighed for at gemme filen fra enheden til yderligere undersøgelse.

> [!NOTE]
> Følgende filstørrelsesbegrænsninger gælder:
>
> - `getfile` grænse: 3 GB
> - `fileinfo` grænse: 30 GB
> - `library` grænse: 250 MB

### <a name="download-a-file-in-the-background"></a>Download en fil i baggrunden

For at aktivere sikkerhedsteamet til at fortsætte med at undersøge en påvirket enhed kan filer nu downloades i baggrunden.

- Hvis du vil downloade en fil i baggrunden, skal du skrive i den live svarkommandokonsol.`download <file_path> &`
- Hvis du venter på, at en fil downloades, kan du flytte den til baggrunden ved hjælp af Ctrl+Z.
- Hvis du vil hente en fil til forgrunden, skal du skrive i den live svarkommandokonsol.`fg <command_id>`

Her er nogle eksempler:

<br>

****

|Kommando|Hvad den gør|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Begynder at downloade en fil *some_file.exe* en fil i baggrunden.|
|`fg 1234`|Returnerer en download med kommando-id *1234* til forgrunden.|
|

### <a name="put-a-file-in-the-library"></a>Placere en fil i biblioteket

Live-svar har et bibliotek, hvor du kan lægge filer ind. Biblioteket lagrer filer (f.eks. scripts), der kan køres i en direkte svarsession på lejerniveau.

Live-svar gør det muligt at køre PowerShell-scripts, men du skal først lægge filerne ind i biblioteket, før du kan køre dem.

Du kan have en samling af PowerShell-scripts, der kan køre på enheder, som du starter live svarsessioner med.

#### <a name="to-upload-a-file-in-the-library"></a>Sådan uploader du en fil i biblioteket

1. Klik **Upload fil til bibliotek**.

2. Klik **på Gennemse** , og vælg filen.

3. Angiv en kort beskrivelse.

4. Angiv, om du vil overskrive en fil med samme navn.

5. Hvis du gerne vil være det, skal du vide, hvilke parametre der er nødvendige for scriptet, og markere afkrydsningsfeltet scriptparametre. Skriv et eksempel og en beskrivelse i tekstfeltet.

6. Klik **på Bekræft**.

7. (Valgfrit) Kør kommandoen for at bekræfte, at filen blev overført til `library` biblioteket.

### <a name="cancel-a-command"></a>Annuller en kommando

Når du er i en session, kan du annullere en kommando ved at trykke på Ctrl+C.

> [!WARNING]
> Hvis du bruger denne genvej, stoppes kommandoen ikke i agentsiden. Det vil kun annullere kommandoen i portalen. Derfor kan ændring af handlinger som f.eks. "afhjælpe" fortsætte, mens kommandoen annulleres.

## <a name="run-a-script"></a>Kør et script

Før du kan køre et PowerShell/Bash-script, skal du først overføre det til biblioteket.

Når du har uploadet scriptet til biblioteket, kan du bruge `run` kommandoen til at køre scriptet.

Hvis du planlægger at bruge et usigneret PowerShell-script i sessionen, skal du aktivere indstillingen på siden [Avancerede funktioner.](advanced-features.md)

> [!WARNING]
> Hvis du tillader brug af usignerede scripts, kan det øge din eksponering for trusler.

## <a name="apply-command-parameters"></a>Anvend kommandoparametre

- Få vist konsollens hjælp for at få mere at vide om kommandoparametre. Hvis du vil vide mere om en enkelt kommando, skal du køre:

  ```powershell
  help <command name>
  ```

- Når du anvender parametre på kommandoer, skal du bemærke, at parametrene håndteres baseret på en fast rækkefølge:

  ```powershell
  <command name> param1 param2
  ```

- Når du angiver parametre uden for den faste rækkefølge, skal du angive navnet på parameteren med en bindestreg, før du angiver værdien:

  ```powershell
  <command name> -param2_name param2
  ```

- Når du bruger kommandoer, der har nødvendige kommandoer, kan du bruge flag:

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  eller

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Understøttede outputtyper

Live-svar understøtter outputtyper for tabeller og JSON-formater. For hver kommando er der en standardoutputfunktion. Du kan ændre outputtet i dit foretrukne outputformat ved hjælp af følgende kommandoer:

- `-output json`
- `-output table`

> [!NOTE]
> Færre felter vises i tabelformat på grund af den begrænsede plads. Hvis du vil se flere detaljer i outputtet, kan du bruge JSON-outputkommandoen, så der vises flere detaljer.

## <a name="supported-output-pipes"></a>Understøttede outputrør

Live-svar understøtter outputrør til CLI og fil. CLI er standardoutputfunktionsmåden. Du kan pipe outputtet til en fil ved hjælp af følgende kommando: [kommando] > [filnavn].txt.

Eksempel:

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Få vist kommandologgen

Vælg fanen **Kommandolog** for at se de kommandoer, der bruges på enheden under en session. Hver kommando registreres med alle oplysninger, f.eks.:

- Id
- Kommandolinje
- Varighed
- Sidepanelet Status og input eller output

## <a name="limitations"></a>Begrænsninger

- Sessioner med live svar er begrænset til 25 live svarsessioner ad gangen.
- Værdien for inaktiv tid for live svarsession er 30 minutter.
- Individuelle kommandoer for live svar har en tidsgrænse på 10 minutter, `getfile`med undtagelse af , `findfile``run`og , der har en grænse på 30 minutter.
- En bruger kan starte op til 10 samtidige sessioner.
- En enhed kan kun være i én session ad gangen.
- Følgende filstørrelsesbegrænsninger gælder:
  - `getfile` grænse: 3 GB
  - `fileinfo` grænse: 10 GB
  - `library` grænse: 250 MB

## <a name="related-article"></a>Relateret artikel

- [Eksempler på kommandoen Direkte svar](live-response-command-examples.md)
