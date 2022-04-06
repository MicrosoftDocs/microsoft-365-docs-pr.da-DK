---
title: Nyheder i Microsoft Defender for Endpoint på Mac
description: Få mere at vide om de overordnede ændringer af tidligere versioner af Microsoft Defender for Endpoint på Mac.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: d36d05a4abe36ffe63e53eb8e164e248755de0ec
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665904"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Nyheder i Microsoft Defender for Endpoint på Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1016169-20122022161690"></a>101.61.69 (20.122022.16169.0)

- Fejlrettelser

## <a name="1016091-20122021160910"></a>101.60.91 (20.122021.16091.0)

- Denne version indeholder en sikkerhedsopdatering til [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Denne version tilføjer understøttelse af macOS 12.3. Fra og med macOS 12.3 [fjerner Apple Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Der vil som standard ikke være installeret nogen Python-version på macOS. **HANDLING ER NØDVENDIG**: 
  - Brugerne skal opdatere Microsoft Defender for Endpoint til Mac til version 101.59.50 (eller nyere), før de opdaterer deres enheder til macOS Monterey 12.3 (eller nyere). Denne minimale version 101.59.50 er en forudsætning for at fjerne Python-relaterede problemer med Microsoft Defender for Endpoint til Mac på macOS Monterey.
  - I forbindelse med fjerninstallationer skal eksisterende MDM-konfigurationer opdateres til Microsoft Defender for Endpoint til Mac version 101.59.50 (eller nyere). Hvis du sender en ældre Microsoft Defender for Endpoint til Mac-versionen via MDM til macOS Monterey 12.3 (eller nyere), medfører det en installationsfejl.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- Kommandolinjeværktøjet understøtter nu gendannelse af filer, der er sat i karantæne, på en anden placering end den, hvor filen oprindeligt blev registreret. Dette kan gøres via `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Udvidet enhedsstyring til håndtering af enheder, der er tilsluttet thunderbolt 3
- Forbedret håndteringen af politikker for enhedsstyring, der indeholder ugyldige leverandør-id'er og produkt-id'er. Før denne version blev hele politikken ignoreret, hvis politikken indeholdt et eller flere ugyldige id'er. Fra og med denne version ignoreres kun de ugyldige dele af politikken. Problemer med politikken vises via `mdatp device-control removable-media policy list`.
- Fejlrettelser

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Fejlrettelser

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- Programmet er blevet omdøbt fra "Microsoft Defender ATP" til "Microsoft Defender". Slutbrugerne vil se følgende ændringer:
  - Stien til programinstallationen er ændret fra `/Application/Microsoft Defender ATP.app` til `/Applications/Microsoft Defender.app`.
  - I brugeroplevelsen er forekomster af "Microsoft Defender ATP" blevet erstattet med "Microsoft Defender"
- Løste et problem, hvor nogle VPN-programmer ikke kunne oprette forbindelse på grund af netværksindholdsfilteret, der distribueres med Microsoft Defender for Endpoint til Mac
- Løste et problem, der blev fundet i macOS 12.2 beta 2, hvor installationspakken ikke kunne åbnes på grund af en ændring i operativsystemet, som forhindrer installation af pakker med visse egenskaber. Selvom det ser ud til, at denne os-ændring ikke er inkluderet i den endelige version af macOS 12.2, er det sandsynligt, at den vil blive genindført i en fremtidig macOS-version. Derfor opfordrer vi alle virksomhedsadministratorer til at opdatere Microsoft Defender for Endpoint-pakken i deres administrationskonsol til denne produktversion (eller en nyere version).
- Løste et problem, der kan ses på nogle M1-enheder, hvor produktet sidder fast med ugyldige antimalwaredefinitioner og ikke kunne opdateres til et arbejdssæt af definitioner.
- `mdatp health`output er blevet udvidet med en ekstra attribut kaldet `full_disk_access_enabled` , der kan bruges til at afgøre, om Full Disk Access er tildelt til alle komponenter i Microsoft Defender for Endpoint til Mac.
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) understøttes ikke længere
- Når en produktindstilling stopper med at blive administreret af administratoren via MDM, vender den nu tilbage til den værdi, den havde, før den blev administreret (den værdi, der er konfigureret lokalt af slutbrugeren, eller, hvis en sådan lokal værdi ikke udtrykkeligt blev angivet, den standardværdi, der bruges af produktet). Før denne ændring bevares den administrerede værdi, efter at en indstilling stoppede med at blive administreret, og den blev stadig brugt af produktet.
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- Tilføjede en ny parameter til kommandolinjeværktøjet for at styre, om arkiver scannes under scanninger efter behov. Dette kan konfigureres via `mdatp config scan-archives --value [enabled/disabled]`. Som standard er dette angivet til `enabled`.
- Fejlrettelser

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- Rettelse til en systemfrysning, der forekommer ved lukning på macOS Mojave og macOS Catalina

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- Kandidatbuild til macOS 12 (Monterey)
- Fejlrettelser

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Nye parametre er føjet til kommandolinjeværktøjet:
  - Kontrollér graden af parallelitet for on-demand-scanninger. Dette kan konfigureres via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Der bruges som standard en grad af parallelitet af `2` .
  - Kontrollér, om scanninger efter sikkerhedsintelligensopdateringer er aktiveret eller deaktiveret. Dette kan konfigureres via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Som standard er dette angivet til `enabled`.
- Ændring af niveauet for produktloggen kræver nu udvidede rettigheder
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- Indbygget understøttelse af M1-chip
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Fejlrettelser

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Fejlrettelser

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [Enhedsstyring til macOS](mac-device-control-overview.md) er nu offentlig tilgængelig
- Løste et problem, hvor en hurtig scanning ikke kunne startes fra statusmenuen på macOS 11 (Big Sur)
- Andre fejlrettelser

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Løste et problem, hvor samtidig adgang til nøglering fra Microsoft Defender for Endpoint og andre programmer kan føre til beskadigelse af nøglering.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- Fra og med denne version afhjælpes trusler, der registreres under on-demand-antivirusscanninger, som udløses via kommandolinjeklienten, automatisk. Trusler, der registreres under scanninger, der udløses via brugergrænsefladen, kræver stadig manuel handling.
- `mdatp diagnostic real-time-protection-statistics` understøtter nu to ekstra parametre:
  - `--sort`: sorterer outputtet faldende efter det samlede antal scannede filer
  - `--top N`: viser de øverste N-resultater (fungerer kun, hvis `--sort` der også er angivet)
- Forbedringer af ydeevnen (specielt til når YARN bruges) & fejlrettelser

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- Rettelse for at imødekomme udløb af Apple-certifikat til macOS Catalina og tidligere. Denne rettelse gendanner TVM-funktionalitet (Threat & Vulnerability Management).

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Microsoft Defender for Endpoint på macOS er nu tilgængelig som prøveversion for us government-kunder. Du kan få flere oplysninger [under Microsoft Defender for Endpoint til US Government-kunder](gov.md).
- Forbedringer af ydeevnen (især i forbindelse med brug af XCode Simulator-appen) & fejlrettelser.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Der er føjet en ny indstilling til kommandolinjeværktøjet for at få vist oplysninger om den seneste scanning efter behov. Hvis du vil have vist oplysninger om den seneste scanning efter behov, skal du køre `mdatp health --details antivirus`
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> Den gamle kommandolinjeværktøjssyntaks frarådes i denne version. Du kan få oplysninger om den nye syntaks under [Ressourcer](mac-resources.md#configuring-from-the-command-line).

- Tilføjede en ny kommandolinjeparameter for at deaktivere netværksudvidelsen: `mdatp system-extension network-filter disable`. Denne kommando kan være nyttig til fejlfinding af netværksproblemer, der kan være relateret til Microsoft Defender for Endpoint på Mac
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Fejlrettelser

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Forbedret pålideligheden af agenten, når du kører på macOS 11 Big Sur
- Tilføjede en ny kommandolinjeparameter (`--ignore-exclusions`) for at ignorere AV-udeladelser under brugerdefinerede scanninger (`mdatp scan custom`)
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Fjernede betingelser, da Microsoft Defender for Endpoint udløste en macOS 11 (Big Sur)-fejl, der manifesterer sig i kerne panik
- Løste en hukommelsesfejl i endpoint Security-systemudvidelsen, når den kører på mac 11 (Big Sur)
- Fejlrettelser

## <a name="1011072"></a>101.10.72

- Fejlrettelser

## <a name="1010961"></a>101.09.61

- Tilføjede en ny administreret præference for [deaktivering af muligheden for at sende feedback](mac-preferences.md#show--hide-option-to-send-feedback)
- Statusmenuikonet viser nu en tilstand, der er i orden, når produktindstillingerne administreres. Tidligere viste ikonet for statusmenuen en advarsels- eller fejltilstand, selvom produktindstillingerne blev administreret af administratoren
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010950"></a>101.09.50

- Denne produktversion er blevet valideret på macOS Big Sur 11 beta 9

- Den nye syntaks for `mdatp` kommandolinjeværktøjet er nu standardsyntaksen. Du kan få flere oplysninger om den nye syntaks under [Ressourcer til Microsoft Defender for Endpoint på macOS](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > Den gamle kommandolinjeværktøjssyntaks fjernes fra produktet **den 1. januar 2021**.

- Udvidet `mdatp diagnostic create` med en ny parameter (`--path [directory]`), der gør det muligt at gemme diagnosticeringslogfilerne i en anden mappe
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010949"></a>101.09.49

- Forbedringer af brugergrænsefladen for at differentiere undtagelser, der administreres af it-administratoren i forhold til undtagelser, der er defineret af den lokale bruger
- Forbedret CPU-udnyttelse under on-demand-scanninger
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010723"></a>101.07.23

- Nye felter er føjet til outputtet for `mdatp --health` til kontrol af status for passiv tilstand og Slutpunktsregistrering og -svar gruppe-id

  > [!NOTE]
  > `mdatp --health` erstattes med `mdatp health` i en fremtidig produktopdatering.

- Løste en fejl, hvor automatisk indsendelse af eksempel ikke blev markeret som administreret i brugergrænsefladen
- Der er tilføjet nye indstillinger til styring af opbevaring af elementer i antivirusscanningshistorikken. Du kan nu [angive det antal dage, elementer skal bevares i scanningsoversigten](mac-preferences.md#antivirus-scan-history-retention-in-days) , og [angive det maksimale antal elementer i scanningsoversigten](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Fejlrettelser

## <a name="1010663"></a>101.06.63

- Løste en regression af ydeevnen, der blev introduceret i version `101.05.17`. Regressionen blev introduceret med rettelsen for at fjerne kerne panik nogle kunder har observeret, når de tilgår SMB-aktier. Vi har tilbageført denne kodeændring og undersøger alternative måder at eliminere kerne panik på.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Vi arbejder på en ny og forbedret syntaks for `mdatp` kommandolinjeværktøjet. Den nye syntaks er i øjeblikket standard i kanalerne Insider Fast og Insider Slow update. Vi opfordrer dig til at famliliarize dig selv med denne nye syntaks.
>
> Vi vil fortsætte med at understøtte den gamle syntaks parallelt med den nye syntaks og vil give mere kommunikation omkring udfasningsplanen for den gamle syntaks i de kommende måneder.

- Løste en kerne-panik, der nogle gange opstod under adgang til SMB-filshares
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010516"></a>101.05.16

- Forbedringer af hurtig scanningslogik for at reducere antallet af scannede filer væsentligt
- Tilføjede [understøttelse af autofuldførelse](mac-resources.md#how-to-enable-autocompletion) for kommandolinjeværktøjet
- Fejlrettelser

## <a name="1010312"></a>101.03.12

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010154"></a>101.01.54

- Forbedringer omkring kompatibilitet med tidsmaskine
- Forbedringer af hjælp til handicappede
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010031"></a>101.00.31

- Forbedret [produkt onboarding-oplevelse for Intune brugere](/mem/intune/apps/apps-advanced-threat-protection-macos)
- [Antivirusudeladelser understøtter nu jokertegn](mac-exclusions.md#supported-exclusion-types)
- Muligheden for at udløse antivirusscanninger er blevet tilføjet fra macOS-genvejsmenuen. Du kan nu højreklikke på en fil eller en mappe i Finder og vælge **Scan med Microsoft Defender for Endpoint**
- Nedgradering af produkter på stedet er nu udtrykkeligt ikke tilladt af installationsprogrammet. Hvis du har brug for at nedgradere, skal du først fjerne den eksisterende version og konfigurere din enhed igen
- Andre forbedringer af ydeevnen & fejlrettelser

## <a name="1009027"></a>100.90.27

- Du kan nu [angive en opdateringskanal](mac-updates.md#set-the-channel-name) for Microsoft Defender for Endpoint på macOS, der er forskellig fra opdateringskanalen for hele systemet
- Nyt produktikon
- Andre forbedringer af brugeroplevelsen
- Fejlrettelser

## <a name="1008692"></a>100.86.92

- Forbedringer omkring kompatibilitet med tidsmaskine
- Løste et problem, hvor produktet nogle gange ikke rensede alle filer under `/Library/Application Support/Microsoft/Defender` under fjernelsen
- Reducerede produktets CPU-udnyttelse, når Microsoft-produkter opdateres via Microsoft Automatiske opdateringer
- Andre forbedringer af ydeevnen & fejlrettelser

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> For at sikre den mest komplette beskyttelse af dine macOS-enheder og i overensstemmelse med Apple stopper leveringen af indbyggede sikkerhedsopdateringer fra MacOS til os-versioner, der er ældre end [aktuel - 2], understøttes udrulning og opdateringer af MDATP til Mac ikke længere på macOS Sierra [10.12]. MDATP til Mac-opdateringer og -forbedringer leveres til enheder, der kører versioner Catalina [10.15], Mojave [10.14] og High Sierra [10.13].
>
> Hvis du allerede har MDATP til Mac installeret på dine Sierra [10.12]-enheder, skal du opgradere til den nyeste macOS-version for at fjerne risikoen for at miste beskyttelse.

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1008373"></a>100.83.73

- Der er tilføjet flere kontrolelementer for it-administratorer i forbindelse [med administration af udelukkelser](mac-preferences.md#exclusion-merge-policy), [administration af indstillinger for trusselstyper](mac-preferences.md#threat-type-settings-merge-policy) og [ikke-tilladte trusselshandlinger](mac-preferences.md#disallowed-threat-actions)
- Når Fuld diskadgang ikke er aktiveret på enheden, vises der nu en advarsel i statusmenuen
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1008260"></a>100.82.60

- Løste et problem, hvor produktet ikke kan begynde at følge en definitionsopdatering.

## <a name="1008042"></a>100.80.42

- Fejlrettelser

## <a name="1007942"></a>100.79.42

- Løste et problem, hvor Microsoft Defender for Endpoint på Mac nogle gange forstyrrede Time Machine
- Tilføjede en ny parameter til kommandolinjeværktøjet til test af forbindelsen til backendtjenesten

  ```bash
  mdatp connectivity test
  ```

- Tilføjet mulighed for at få vist hele trusselshistorikken i brugergrænsefladen (kan tilgås fra **visningen Beskyttelseshistorik** )
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1007215"></a>100.72.15

- Fejlrettelser

## <a name="1007099"></a>100.70.99

- Løste et problem, der påvirker nogle brugeres mulighed for at opgradere til macOS Catalina, når beskyttelse i realtid er aktiveret. Dette sporadiske problem skyldtes, at Microsoft Defender for Endpoint låser filer i Catalina-opgraderingspakken under scanning efter trusler, hvilket førte til fejl i opgraderingssekvensen.

## <a name="1006899"></a>100.68.99

- Tilføjede muligheden for at konfigurere antivirusfunktionen til at køre i [passiv tilstand](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1006528"></a>100.65.28

- Tilføjet understøttelse af macOS Catalina

  > [!CAUTION]
  > macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til visse placeringer på disken (f.eks. dokumenter, downloads, desktop osv.) uden eksplicit samtykke. Hvis dette samtykke ikke er til stede, er Microsoft Defender for Endpoint ikke i stand til fuldt ud at beskytte din enhed.
  >
  > Mekanismen for tildeling af dette samtykke afhænger af, hvordan du har installeret Microsoft Defender for Endpoint:
  >
  > - I forbindelse med manuelle udrulninger skal du se de opdaterede instruktioner i emnet [Manuel udrulning](mac-install-manually.md#how-to-allow-full-disk-access) .
  > - I forbindelse med administrerede udrulninger skal du se de opdaterede instruktioner i emnerne [jamf-baseret udrulning](mac-install-with-jamf.md) og [Microsoft Intune-baseret udrulning](mac-install-with-intune.md#create-system-configuration-profiles).

- Forbedringer af ydeevnen & fejlrettelser
