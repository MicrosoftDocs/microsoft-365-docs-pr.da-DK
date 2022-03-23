---
title: Konfigurer og valider udeladelse af Microsoft Defender til slutpunkt på Linux
description: Angiv og valider udeladelse af Microsoft Defender til slutpunkt på Linux. Udeladelse kan angives for filer, mapper og processer.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, udelukkelser, scanninger, antivirus
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
ms.openlocfilehash: b86cad016af0f7819d69f0156498336652e6292d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/29/2021
ms.locfileid: "63592066"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-linux"></a>Konfigurer og valider udeladelse af Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Denne artikel indeholder oplysninger om, hvordan du definerer udeladelse, der gælder for on-demand-scanninger samt beskyttelse og overvågning i realtid.

> [!IMPORTANT]
> De undtagelser, der er beskrevet i denne artikel, gælder ikke for andre Defender til slutpunkter på Linux-funktioner, herunder slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar). Filer, som du udelader ved hjælp af de metoder, der er beskrevet i denne artikel, kan stadig Slutpunktsregistrering og -svar vigtige beskeder og andre registreringer.

Du kan udelade visse filer, mapper, processer og proces åbne filer fra Defender til Slutpunkt på Linux-scanninger.

Udeladelse kan være nyttige for at undgå forkerte registreringer af filer eller software, der er unikke eller tilpasset din organisation. De kan også være nyttige til at mindske problemer med ydeevnen forårsaget af Defender til slutpunkt på Linux.

> [!WARNING]
> Hvis du definerer udeladelse, sænkes den beskyttelse, der tilbydes af Defender til Slutpunkt på Linux. Du bør altid evaluere de risici, der er forbundet med implementering af udeladelse, og du bør kun udelade filer, som du er sikker på ikke er skadelige.

## <a name="supported-exclusion-types"></a>Understøttede udeladelsestyper

Tabellen nedenfor viser de udeladelsestyper, der understøttes af Defender til Slutpunkt på Linux.

Udeladelse|Definition|Eksempler
---|---|---
Filtypenavn|Alle filer med udvidelsen, hvor som helst på enheden|`.test`
Filer|En bestemt fil identificeret ved den fulde sti|`/var/log/test.log`<br/>`/var/log/*.log`<br/>`/var/log/install.?.log`
Mappe|Alle filer under den angivne mappe (rekursivt)|`/var/log/`<br/>`/var/*/`
Proces|En bestemt proces (angivet enten af den fulde sti eller filnavnet) og alle filer, der åbnes af den|`/bin/cat`<br/>`cat`<br/>`c?t`

> [!IMPORTANT]
> Stierne ovenfor skal være hårde links, ikke symbolske links, for at blive udelukket korrekt. Du kan kontrollere, om en sti er et symbolsk link ved at køre `file <path-name>`.

Fil-, mappe- og procesude udeladelse understøtter følgende jokertegn:

Jokertegn|Beskrivelse|Eksempel|Matcher|Er ikke ens
---|---|---|---|---
\*|Finder forekomster af et vilkårligt antal tegn inklusive ingen (bemærk, at når dette jokertegn bruges inde i en sti, erstatter det kun én mappe)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|Matcher et vilkårligt enkelttegn|`file?.log`|`file1.log`<br/>`file2.log`|`file123.log`

## <a name="how-to-configure-the-list-of-exclusions"></a>Sådan konfigureres listen over udeladelses undtagelser

### <a name="from-the-management-console"></a>Fra administrationskonsollen

Hvis du vil have mere at vide om, hvordan du konfigurerer udeladelse fra Xbox, Ansible eller en anden administrationskonsol, skal du se Angive indstillinger [for Defender til Slutpunkt på Linux](linux-preferences.md).

### <a name="from-the-command-line"></a>Fra kommandolinjen

Kør følgende kommando for at få vist de tilgængelige parametre til administration af udeladelse:

```bash
mdatp exclusion
```

> [!TIP]
> Når du konfigurerer udeladelse med jokertegn, skal du omslutte parameteren med dobbelte anførselstegn for at forhindre globbing.

Eksempler:

- Tilføj en udeladelse for et filtypenavn:

    ```bash
    mdatp exclusion extension add --name .txt
    ```

    ```Output
    Extension exclusion configured successfully
    ```

- Tilføj en udeladelse for en fil:

    ```bash
    mdatp exclusion file add --path /var/log/dummy.log
    ```

    ```Output
    File exclusion configured successfully
    ```

- Tilføj en udeladelse for en mappe:

    ```bash
    mdatp exclusion folder add --path /var/log/
    ```

    ```Output
    Folder exclusion configured successfully
    ```

- Tilføj en udeladelse for en anden mappe:

    ```bash
    mdatp exclusion folder add --path /var/log/
    mdatp exclusion folder add --path /other/folder
    ```

    ```Output
    Folder exclusion configured successfully
    ```

- Tilføj en udeladelse for en mappe med et jokertegn i den:

    ```bash
    mdatp exclusion folder add --path "/var/*/"
    ```

    > [!NOTE]
    > Dette udelader kun stier ét niveau under */var/*, men ikke mapper, der er mere indlejrede; for eksempel */var/denne-undermappe/men-ikke-denne-undermappe*.

    ```bash
    mdatp exclusion folder add --path "/var/"
    ```

    > [!NOTE]
    > Dette udelukker alle stier, hvis overordnede er */var/*; for eksempel */var/denne-undermappe/og-denne-undermappe-også*.

    ```Output
    Folder exclusion configured successfully
    ```

- Tilføj en udeladelse for en proces:

    ```bash
    mdatp exclusion process add --name cat
    ```

    ```Output
    Process exclusion configured successfully
    ```

- Tilføj en udeladelse for en anden proces:

    ```bash
    mdatp exclusion process add --name cat
    mdatp exclusion process add --name dog
    ```

    ```Output
    Process exclusion configured successfully
    ```

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider udeladelseslister med EICAR-testfilen

Du kan validere, om udeladelseslisterne fungerer ved at `curl` hente en testfil.

Erstat med en fil, der overholder udeladelsesreglerne `test.txt` , i følgende Bash-kodestykke. Hvis du f.eks. har udeladt udvidelsen `.testing` , skal du erstatte `test.txt` med `test.testing`. Hvis du tester en sti, skal du sikre dig, at du kører kommandoen i den pågældende sti.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

Hvis Defender til slutpunkt på Linux rapporterer malware, fungerer reglen ikke. Hvis der ikke er nogen rapport om malware, og den downloadede fil findes, fungerer udelukkelsen. Du kan åbne filen for at bekræfte, at indholdet er det samme som det, der beskrives på [webstedet for EICAR-testfilen](http://2016.eicar.org/86-0-Intended-use.html).

Hvis du ikke har internetadgang, kan du oprette din egen EICAR-testfil. Skriv EICAR-strengen til en ny tekstfil med følgende Bash-kommando:

```bash
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' > test.txt
```

Du kan også kopiere strengen til en tom tekstfil og forsøge at gemme den med filnavnet eller i den mappe, du forsøger at udelade.

## <a name="allow-threats"></a>Tillad trusler

Ud over at udelukke bestemt indhold fra at blive scannet, kan du også konfigurere produktet til ikke at registrere nogle klasser af trusler (identificeres ved hjælp af trusselsnavnet). Når du bruger denne funktionalitet, skal du være forsigtig, da den kan lade enheden være ubeskyttet.

Udfør følgende kommando for at føje et trusselsnavn til listen over tilladte:

```bash
mdatp threat allowed add --name [threat-name]
```

Det trusselsnavn, der er knyttet til en registrering på din enhed, kan fås ved hjælp af følgende kommando:

```bash
mdatp threat list
```

Hvis du f.eks. vil `EICAR-Test-File (not a virus)` føje (trusselsnavnet, der er knyttet til genkendelse af EICAR) til listen over tilladte, skal du udføre følgende kommando:

```bash
mdatp threat allowed add --name "EICAR-Test-File (not a virus)"
```
