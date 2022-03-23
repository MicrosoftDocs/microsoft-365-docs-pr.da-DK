---
title: Konfigurer og valider udeladelse for Microsoft Defender til Slutpunkt på Mac
description: Angiv og valider udeladelse af Microsoft Defender til Slutpunkt på Mac. Udeladelse kan angives for filer, mapper og processer.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, udeladelse, scanninger, antivirus
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
ms.openlocfilehash: a069e3dd3ef99f094f96318277e077c56b7cb974
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592827"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-for-endpoint-on-macos"></a>Konfigurer og valider udeladelse for Microsoft Defender til Endpoint på macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Denne artikel indeholder oplysninger om, hvordan du definerer udeladelse, der gælder for on-demand-scanninger samt beskyttelse og overvågning i realtid.

> [!IMPORTANT]
> De undtagelser, der er beskrevet i denne artikel, gælder ikke for andre Defender til slutpunkter på Mac-funktioner, herunder slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar). Filer, som du udelader ved hjælp af de metoder, der er beskrevet i denne artikel, kan stadig Slutpunktsregistrering og -svar vigtige beskeder og andre registreringer.

Du kan udelade visse filer, mapper, processer og proces åbne filer fra Defender til Endpoint på Mac-scanninger.

Udeladelse kan være nyttige for at undgå forkerte registreringer af filer eller software, der er unikke eller tilpasset din organisation. De kan også være nyttige til at mindske problemer med ydeevnen forårsaget af Defender til slutpunkt på Mac.

> [!WARNING]
> Hvis du definerer udeladelse, sænkes den beskyttelse, der tilbydes af Defender til Slutpunkt på Mac. Du bør altid evaluere de risici, der er forbundet med implementering af udeladelse, og du bør kun udelade filer, som du er sikker på ikke er skadelige.

## <a name="supported-exclusion-types"></a>Understøttede udeladelsestyper

Følgende tabel viser de udeladelsestyper, der understøttes af Defender til Slutpunkt på Mac.

Udeladelse|Definition|Eksempler
---|---|---
Filtypenavn|Alle filer med udvidelsen, hvor som helst på computeren|`.test`
Filer|En bestemt fil identificeret ved den fulde sti|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`
Mappe|Alle filer under den angivne mappe (rekursivt)|`/var/log/` <p> `/var/*/`
Proces|En bestemt proces (angivet enten af den fulde sti eller filnavnet) og alle filer, der åbnes af den|`/bin/cat` <p> `cat` <p> `c?t`

Fil-, mappe- og procesude udeladelse understøtter følgende jokertegn:

Jokertegn|Beskrivelse|Eksempel|Matcher|Er ikke ens
---|---|---|---|---
\*|Finder forekomster af et vilkårligt antal tegn inklusive ingen (bemærk, at når dette jokertegn bruges inde i en sti, erstatter det kun én mappe)|`/var/*/*.log`|`/var/log/system.log`|`/var/log/nested/system.log`
?|Matcher et vilkårligt enkelttegn|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`

> [!NOTE]
> Produktet forsøger at løse firmalinks, når udeladelse evalueres. Fast forbindelsesløsning fungerer ikke, når udelukkelsen indeholder jokertegn, eller destinationsfilen `Data` (på mængden) ikke findes.

## <a name="how-to-configure-the-list-of-exclusions"></a>Sådan konfigureres listen over udeladelses undtagelser

### <a name="from-the-management-console"></a>Fra administrationskonsollen

Du kan finde flere oplysninger om, hvordan du konfigurerer udeladelse fra SYLF, Intune eller en anden administrationskonsol under Angiv indstillinger [for Defender til Slutpunkt på Mac](mac-preferences.md).

### <a name="from-the-user-interface"></a>Fra brugergrænsefladen

Åbn programmet Defender til slutpunkt, og gå til **Administrer indstillinger Tilføj** \> **eller fjern udelukkelse...**, som vist på følgende skærmbillede:

![Skærmbillede af Administrer udeladelse.](images/mdatp-37-exclusions.png)

Vælg den type udeladelse, du vil tilføje, og følg instruktionerne.

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>Valider udeladelseslister med EICAR-testfilen

Du kan validere, om udeladelseslisterne fungerer ved at `curl` hente en testfil.

Erstat med en fil, der overholder udeladelsesreglerne `test.txt` , i følgende Bash-kodestykke. Hvis du f.eks. har udeladt udvidelsen `.testing` , skal du erstatte `test.txt` med `test.testing`. Hvis du tester en sti, skal du sikre dig, at du kører kommandoen i den pågældende sti.

```bash
curl -o test.txt https://www.eicar.org/download/eicar.com.txt
```

Hvis Defender til Slutpunkt på Mac rapporterer malware, fungerer reglen ikke. Hvis der ikke er nogen rapport om malware, og den downloadede fil findes, fungerer udelukkelsen. Du kan åbne filen for at bekræfte, at indholdet er det samme som det, der beskrives på [webstedet for EICAR-testfilen](http://2016.eicar.org/86-0-Intended-use.html).

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
