---
title: Undersøg enheder på enheder, der bruger live-svar i Microsoft Defender for Endpoint
description: Få adgang til en enhed ved hjælp af en sikker ekstern shellforbindelse for at udføre undersøgelsesarbejde og udføre øjeblikkelige svarhandlinger på en enhed i realtid.
keywords: fjern, shell, forbindelse, live, svar, realtid, kommando, script, afhjælpe, jage, eksportere, log, slippe, downloade, fil,
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
ms.openlocfilehash: 5e5d2b2bd47ba30aaf152171605947bb9a627480
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666344"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Undersøg enheder på enheder ved hjælp af live-svar

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Live response giver teams for sikkerhedshandlinger øjeblikkelig adgang til en enhed (også kaldet en maskine) ved hjælp af en ekstern shellforbindelse. Dette giver dig mulighed for at udføre dybdegående undersøgelsesarbejde og reagere øjeblikkeligt for straks at indeholde identificerede trusler i realtid.

Liverespons er designet til at forbedre undersøgelser ved at gøre det muligt for dit team af sikkerhedshandlinger at indsamle tekniske data, køre scripts, sende mistænkelige enheder til analyse, afhjælpe trusler og proaktivt jage efter nye trusler.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Med direkte svar kan analytikere udføre alle følgende opgaver:

- Kør grundlæggende og avancerede kommandoer for at udføre undersøgelsesarbejde på en enhed.
- Download filer som malwareeksempler og resultater af PowerShell-scripts.
- Download filer i baggrunden (ny!).
- Upload et PowerShell-script eller en eksekverbar fil til biblioteket, og kør det på en enhed fra et lejerniveau.
- Udfør eller fortryd afhjælpningshandlinger.

## <a name="before-you-begin"></a>Før du begynder

Før du kan starte en session på en enhed, skal du sørge for at opfylde følgende krav:

- **Kontrollér, at du kører en understøttet version af Windows**.

  Enheder skal køre en af følgende versioner af Windows

  - **Windows 10 & 11**
    - [Version 1909](/windows/whats-new/whats-new-windows-10-version-1909) eller nyere
    - [Version 1903](/windows/whats-new/whats-new-windows-10-version-1903) med [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Version 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) [med KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Version 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) med [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Version 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) med [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **macOS** – kun tilgængelig for offentlig prøveversion, minimumversion: 101.43.84

   > [!NOTE]
   > I øjeblikket understøttes kun Intel-baserede macOS-systemer.

  - **Linux** – gælder kun for offentlig prøveversion, minimumversion: 101.45.13

  - **Windows Server 2012 R2** – med [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2016** – med [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Version 1903 eller (med [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)) senere
    - Version 1809 (med [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))

  - **Windows Server 2022**

- **Aktivér live-svar fra siden med avancerede indstillinger**.

  Du skal aktivere funktionen til direkte svar på siden [Avancerede funktioner.](advanced-features.md)

  > [!NOTE]
  > Det er kun brugere med administrere sikkerhedsroller eller globale administratorroller, der kan redigere disse indstillinger.
  >
  > Automatiseret undersøgelse skal aktiveres i [indstillingerne for avancerede funktioner](advanced-features.md) , før liverespons aktiveres.

- **Aktivér live-svar for servere fra siden med avancerede indstillinger** (anbefales).

  > [!NOTE]
  > Det er kun brugere med administrere sikkerhedsroller eller globale administratorroller, der kan redigere disse indstillinger.

- **Sørg for, at enheden har fået tildelt et Automation Remediation-niveau**.

  Du skal som minimum aktivere afhjælpningsniveauet for en given enhedsgruppe. Ellers kan du ikke oprette en Live Response-session til et medlem af den pågældende gruppe.

  Du får vist følgende fejl:

  :::image type="content" source="images/live-response-error.png" alt-text="Fejlmeddelelsen" lightbox="images/live-response-error.png":::

- **Aktivér usigneret udførelse af live-svar-script** (valgfrit).

  >[!IMPORTANT]
  >Signaturbekræftelse gælder kun for PowerShell-scripts.

  > [!WARNING]
  > Hvis du tillader brugen af usignerede scripts, kan det øge din eksponering over for trusler.

  Det anbefales ikke at køre usignerede scripts, da det kan øge din eksponering over for trusler. Hvis du skal bruge dem, skal du aktivere indstillingen på siden [Avancerede funktioner](advanced-features.md) .

- **Sørg for, at du har de nødvendige tilladelser**.

  Det er kun brugere, der er blevet klargjort med de relevante tilladelser, der kan starte en session. Du kan få flere oplysninger om rolletildelinger under [Opret og administrer roller](user-roles.md).

  > [!IMPORTANT]
  > Muligheden for at overføre en fil til biblioteket er kun tilgængelig for brugere med tilladelsen "Administrer sikkerhed Indstillinger".
  > Knappen er nedtonet for brugere, der kun har delegerede tilladelser.

  Afhængigt af den rolle, du har fået tildelt, kan du køre grundlæggende eller avancerede kommandoer til direkte svar. Brugertilladelser styres af den brugerdefinerede rolle RBAC.

## <a name="live-response-dashboard-overview"></a>Oversigt over dashboard med livebesvaring

Når du starter en live-svarsession på en enhed, åbnes et dashboard. Dashboardet indeholder oplysninger om sessionen, f.eks. følgende:

- Who oprettede sessionen
- Da sessionen startede
- Sessionens varighed

Dashboardet giver dig også adgang til:

- Afbryd forbindelsen til session
- Upload filer til biblioteket
- Kommandokonsol
- Kommandolog

## <a name="initiate-a-live-response-session-on-a-device"></a>Start en live-svarsession på en enhed

1. Log på Microsoft 365 Defender portal.

2. Gå til **Slutpunkter > Enhedslager** , og vælg en enhed, der skal undersøges. Siden Enheder åbnes.

3. Start live-svar-sessionen ved at vælge **Start live-svar-session**. Der vises en kommandokonsol. Vent, mens sessionen opretter forbindelse til enheden.

4. Brug de indbyggede kommandoer til at udføre undersøgelsesarbejde. Du kan få flere oplysninger under [Kommandoer til direkte svar](#live-response-commands).

5. Når du har fuldført din undersøgelse, skal du vælge **Afbryd session** og derefter vælge **Bekræft**.

## <a name="live-response-commands"></a>Kommandoer til direkte svar

Afhængigt af den rolle, du har fået tildelt, kan du køre grundlæggende eller avancerede kommandoer til direkte svar. Brugertilladelser styres af brugerdefinerede RBAC-roller. Du kan få flere oplysninger om rolletildelinger under [Opret og administrer roller](user-roles.md).

> [!NOTE]
> Live response er en cloudbaseret interaktiv shell, da en bestemt kommandooplevelse kan variere i svartiden, afhængigt af netværkskvaliteten og systembelastningen mellem slutbrugeren og destinationsenheden.

### <a name="basic-commands"></a>Grundlæggende kommandoer

Følgende kommandoer er tilgængelige for brugerroller, der har fået mulighed for at køre **grundlæggende** kommandoer til direkte svar. Du kan få flere oplysninger om rolletildelinger under [Opret og administrer roller](user-roles.md).

| Kommando  | Beskrivelse  | Windows og Windows Server  | Macos  | Linux  |
|---|---|---|---|---|
| Cd  | Ændrer den aktuelle mappe.  | Y  | Y  | Y  |
| Cls  | Rydder konsolskærmen.  | Y  | Y  | Y  |
| Oprette forbindelse  | Starter en live-svarsession på enheden.  | Y  | Y  | Y  |
| Forbindelser  | Viser alle de aktive forbindelser.  | Y  | N  | N  |
| Dir  | Viser en liste over filer og undermapper i en mappe.  | Y  | Y  | Y  |
| Drivere  | Viser alle de drivere, der er installeret på enheden.  | Y  | N  | N  |
| Fg `<command ID>`  | Placer det angivne job i forgrunden i forgrunden, så det er det aktuelle job.  BEMÆRK! Fg tager et 'kommando-id', der er tilgængeligt fra job, ikke et PID  | Y  | Y  | Y  |
| filinfo  | Hent oplysninger om en fil.  | Y  | Y  | Y  |
| findfile  | Angiver filer med et givent navn på enheden.  | Y  | Y  | Y  |
| getfile <file_path>  | Downloader en fil.  | Y  | Y  | Y  |
| Hjælp  | Indeholder hjælp til kommandoer til direkte svar.  | Y  | Y  | Y  |
| Job  | Viser job, der kører i øjeblikket, deres id og status.  | Y  | Y  | Y  |
| Persistens  | Viser alle kendte persistensmetoder på enheden.  | Y  | N  | N  |
| Processer  | Viser alle processer, der kører på enheden.  | Y  | Y  | Y  |
| Registreringsdatabasen  | Viser registreringsdatabaseværdier.  | Y  | N  | N  |
| planlagte opgaver  | Viser alle planlagte opgaver på enheden.  | Y  | N  | N  |
| Tjenester  | Viser alle tjenester på enheden.  | Y  | N  | N  |
| startupfolders  | Viser alle kendte filer i startmapper på enheden.  | Y  | N  | N  |
| Status  | Viser status og output for en bestemt kommando.  | Y  | N  | N  |
| Spore  | Angiver terminalens logføringstilstand til fejlfinding.  | Y  | Y  | Y  |

### <a name="advanced-commands"></a>Avancerede kommandoer

Følgende kommandoer er tilgængelige for brugerroller, der har mulighed for at køre **avancerede** kommandoer til direkte svar. Du kan få flere oplysninger om rolletildelinger under [Opret og administrer roller](user-roles.md).

| Kommando  | Beskrivelse  | Windows og Windows Server  | Macos  | Linux  |
|---|---|---|---|---|
| Analysere  | Analyserer enheden med forskellige incriminationsmotorer for at nå frem til en dom.  | Y  | N  | N  |
| Indsamle  | Indsamler retsmedicinsk pakke fra maskine  | N  | Y  | Y  |
| Isolere  | Afbryder forbindelsen mellem enheden og netværket, samtidig med at forbindelsen til Defender for Endpoint-tjenesten bevares  | N  | Y  | N  |
| Frigivelse  | Frigiver en enhed fra netværksisolation  | N  | Y  | N  |
| Køre  | Kører et PowerShell-script fra biblioteket på enheden.  | Y  | Y  | Y  |
| Bibliotek  | Viser de filer, der blev overført til biblioteket med live-svar.  | Y  | Y  | Y  |
| putfile  | Placerer en fil fra biblioteket på enheden. Filer gemmes i en arbejdsmappe og slettes som standard, når enheden genstartes.  | Y  | Y  | Y  |
| afhjælp  | Afhjælper en enhed på enheden. Afhjælpningshandlingen varierer afhængigt af objekttypen: Fil: slet proces: stop, slet billedfilTjeneste: stop, slet billedfilpost i registreringsdatabasen: slet planlagt opgave: fjern elementet i mappen Start: slet fil BEMÆRK! Denne kommando har en nødvendig kommando. Du kan bruge kommandoen -auto sammen med remediate til automatisk at køre den påkrævede kommando.  | Y  | Y  | Y  |
| Skan | Kører en antivirusscanning for at hjælpe med at identificere og afhjælpe malware. | N | Y | Y |
| Fortryde  | Gendanner en enhed, der blev afhjælpet.  | Y  | Y  | Y  |

## <a name="use-live-response-commands"></a>Brug direkte svar-kommandoer

De kommandoer, du kan bruge i konsollen, følger de samme principper som [Windows Kommandoer](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

De avancerede kommandoer giver dig et mere robust sæt handlinger, der giver dig mulighed for at udføre mere effektive handlinger, f.eks. downloade og uploade en fil, køre scripts på enheden og udføre afhjælpningshandlinger på en enhed.

### <a name="get-a-file-from-the-device"></a>Hent en fil fra enheden

I forbindelse med scenarier, hvor du gerne vil hente en fil fra en enhed, du undersøger, kan du bruge `getfile` kommandoen . Dette giver dig mulighed for at gemme filen fra enheden til yderligere undersøgelse.

> [!NOTE]
> Der gælder følgende grænser for filstørrelsen:
>
> - `getfile` grænse: 3 GB
> - `fileinfo` grænse: 30 GB
> - `library` grænse: 250 MB

### <a name="download-a-file-in-the-background"></a>Download en fil i baggrunden

Hvis du vil gøre det muligt for dit team af sikkerhedshandlinger at fortsætte med at undersøge en påvirket enhed, kan filer nu downloades i baggrunden.

- Hvis du vil downloade en fil i baggrunden, skal du skrive `download <file_path> &`i kommandokonsollen med live-svar.
- Hvis du venter på, at en fil hentes, kan du flytte den til baggrunden ved hjælp af Ctrl + Z.
- Hvis du vil hente en fil til forgrunden, skal du skrive `fg <command_id>`i kommandokonsollen med live-svar.

Her er nogle eksempler:

<br>

****

|Kommando|Hvad gør den?|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Starter download af en fil med navnet *some_file.exe* i baggrunden.|
|`fg 1234`|Returnerer en download med kommando-id *1234* til forgrunden.|
|

### <a name="put-a-file-in-the-library"></a>Placer en fil i biblioteket

Live response har et bibliotek, hvor du kan placere filer i. Biblioteket gemmer filer (f.eks. scripts), der kan køres i en live-svarsession på lejerniveau.

Direkte svar gør det muligt at køre PowerShell-scripts, men du skal først placere filerne i biblioteket, før du kan køre dem.

Du kan have en samling PowerShell-scripts, der kan køre på enheder, som du starter live-svarsessioner med.

#### <a name="to-upload-a-file-in-the-library"></a>Sådan overfører du en fil i biblioteket

1. Klik **på Upload fil til bibliotek**.

2. Klik på **Gennemse** , og vælg filen.

3. Angiv en kort beskrivelse.

4. Angiv, om du vil overskrive en fil med det samme navn.

5. Hvis du gerne vil være, skal du vide, hvilke parametre der er nødvendige for scriptet, og markere afkrydsningsfeltet scriptparametre. Angiv et eksempel og en beskrivelse i tekstfeltet.

6. Klik på **Bekræft**.

7. (Valgfrit) Kør kommandoen for at bekræfte, at filen blev overført til biblioteket `library` .

### <a name="cancel-a-command"></a>Annuller en kommando

Når som helst under en session kan du annullere en kommando ved at trykke på Ctrl + C.

> [!WARNING]
> Hvis du bruger denne genvej, stopper kommandoen ikke på agentsiden. Kommandoen i portalen annulleres kun. Derfor kan du fortsætte med at ændre handlinger, f.eks. "remediate", mens kommandoen annulleres.

## <a name="run-a-script"></a>Kør et script

Før du kan køre et PowerShell/Bash-script, skal du først uploade det til biblioteket.

Når du har overført scriptet til biblioteket, skal du bruge `run` kommandoen til at køre scriptet.

Hvis du planlægger at bruge et PowerShell-script uden fortegn i sessionen, skal du aktivere indstillingen på siden [Avancerede funktioner](advanced-features.md) .

> [!WARNING]
> Hvis du tillader brugen af usignerede scripts, kan det øge din eksponering over for trusler.

## <a name="apply-command-parameters"></a>Anvend kommandoparametre

- Få vist hjælp til konsollen for at få mere at vide om kommandoparametre. Hvis du vil vide mere om en enkelt kommando, skal du køre:

  ```powershell
  help <command name>
  ```

- Når du anvender parametre på kommandoer, skal du være opmærksom på, at parametre håndteres baseret på en fast rækkefølge:

  ```powershell
  <command name> param1 param2
  ```

- Når du angiver parametre uden for den faste rækkefølge, skal du angive navnet på parameteren med en bindestreg, før du angiver værdien:

  ```powershell
  <command name> -param2_name param2
  ```

- Når du bruger kommandoer, der har forudsætningskommandoer, kan du bruge flag:

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  Eller

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Understøttede outputtyper

Live response understøtter outputtyper i tabel- og JSON-format. Der er en standardfunktionsmåde for output for hver kommando. Du kan ændre outputtet i dit foretrukne outputformat ved hjælp af følgende kommandoer:

- `-output json`
- `-output table`

> [!NOTE]
> Der vises færre felter i tabelformat pga. den begrænsede plads. Hvis du vil se flere oplysninger i outputtet, kan du bruge kommandoen JSON-output, så der vises flere oplysninger.

## <a name="supported-output-pipes"></a>Understøttede outputpiber

Direkte svar understøtter outputrør til kommandolinjegrænsefladen og filen. Kommandolinjegrænsefladen er standardfunktionsmåden for output. Du kan sende outputtet til en fil ved hjælp af følgende kommando: [command] > [filnavn].txt.

Eksempel:

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Vis kommandologgen

Vælg fanen **Kommandolog** for at se de kommandoer, der bruges på enheden under en session. Hver kommando spores med komplette oplysninger, f.eks.:

- ID
- Kommandolinjen
- Varighed
- Sidelinje for status og input eller output

## <a name="limitations"></a>Begrænsninger

- Live-svar-sessioner er begrænset til 25 live-svarsessioner ad gangen.
- Inaktiv timeoutværdi for live-svarsession er 30 minutter.
- Individuelle direkte svar-kommandoer har en tidsgrænse på 10 minutter med undtagelse af `getfile`, `findfile`og `run`, som har en grænse på 30 minutter.
- En bruger kan starte op til 10 samtidige sessioner.
- En enhed kan kun være i én session ad gangen.
- Der gælder følgende grænser for filstørrelsen:
  - `getfile` grænse: 3 GB
  - `fileinfo` grænse: 10 GB
  - `library` grænse: 250 MB

## <a name="related-article"></a>Relateret artikel

- [Eksempler på kommandoen Direkte svar](live-response-command-examples.md)
