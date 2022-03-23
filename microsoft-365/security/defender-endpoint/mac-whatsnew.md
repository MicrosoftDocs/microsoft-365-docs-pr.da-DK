---
title: Nyheder i Microsoft Defender til Slutpunkt på Mac
description: Få mere at vide om de større ændringer for tidligere versioner af Microsoft Defender til Slutpunkt på Mac.
keywords: microsoft, defender, Microsoft Defender til Endpoint, mac, installation, macos, whatsnew
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
ms.openlocfilehash: 80245af54aa6f7a3328515257fe6e6e73f0739b0
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591204"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Nyheder i Microsoft Defender til Slutpunkt på Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="1016091-20122021160910"></a>101.60.91 (20.122021.16091.0)

- Denne version indeholder en sikkerhedsopdatering til [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

## <a name="1015950-20122021159500"></a>101.59.50 (20.122021.15950.0)

- Denne version tilføjer understøttelse af macOS 12.3. Fra og med macOS 12.3 [fjerner Apple Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Der vil ikke være nogen Python-version forudinstalleret på macOS som standard. **HANDLING PÅKRÆVET**: 
  - Brugere skal opdatere Microsoft Defender til Slutpunkt til Mac til version 101.59.50 (eller nyere), før de opdaterer deres enheder til macOS Monterey 12.3 (eller nyere). Denne minimale version 101.59.50 er en forudsætning for at eliminere Python-relaterede problemer med Microsoft Defender til Slutpunkt til Mac på macOS Monterey.
  - For fjerninstallationer skal eksisterende MDM-konfigurationer opdateres til Microsoft Defender for Endpoint til Mac version 101.59.50 (eller nyere). Hvis du skubber via MDM en ældre version af Microsoft Defender til Endpoint til Mac til macOS Monterey 12.3 (eller nyere), så opstår der en installationsfejl.

## <a name="1015910-20122012159100"></a>101.59.10 (20.122012.15910.0)

- Kommandolinjeværktøjet understøtter nu gendannelse af filer, der er sat i karantæne, på en anden placering end den, hvor filen oprindeligt blev fundet. Det kan du gøre via `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Udvidet enhedsstyring til at håndtere enheder, der er forbundet via Thunderbolt 3
- Forbedret håndtering af politikker for enhedsstyring, der indeholder ugyldige leverandør-id'er og produkt-id'er. Før denne version blev hele politikken ignoreret, hvis politikken indeholdt et eller flere ugyldige id'er. Fra og med denne version ignoreres kun de ugyldige dele af politikken. Der kan komme problemer med politikken igennem `mdatp device-control removable-media policy list`.
- Fejlrettelser

## <a name="1015662-20121122156620"></a>101.56.62 (20.121122.15662.0)

- Fejlrettelser

## <a name="1015635-20121121156350"></a>101.56.35 (20.121121.15635.0)

- Programmet er blevet omdøbt fra "Microsoft Defender ATP" til "Microsoft Defender". Slutbrugerne vil overholde følgende ændringer:
  - Programinstallationsstien er blevet ændret fra `/Application/Microsoft Defender ATP.app` til `/Applications/Microsoft Defender.app`.
  - I brugeroplevelsen er forekomster af "Microsoft Defender ATP" blevet erstattet af "Microsoft Defender"
- Vi har løst et problem, hvor nogle VPN-programmer ikke kunne oprette forbindelse på grund af netværksindholdsfilteret, der er distribueret med Microsoft Defender til Slutpunkt til Mac
- Vi har løst et problem, der blev fundet i macOS 12.2 beta 2, hvor installationspakken ikke kunne åbnes på grund af en ændring i operativsystemet (OS), der forhindrer installation af pakker med visse egenskaber. Selvom det ser ud til, at denne ændring af operativsystemet ikke er inkluderet i den endelige version af macOS 12.2, vil den sandsynligvis blive genført i en fremtidig macOS-version. Derfor opfordrer vi alle virksomhedsadministratorer til at opdatere pakken Microsoft Defender for Endpoint i deres administrationskonsol til denne produktversion (eller en nyere version).
- Vi har løst et problem på nogle M1-enheder, hvor produktet sidder fast med ugyldige antimalwaredefinitioner og ikke kunne opdateres korrekt til et fungerende sæt definitioner.
- `mdatp health` output er blevet udvidet med `full_disk_access_enabled` en ekstra attribut kaldet, der kan bruges til at afgøre, om Fuld diskadgang er blevet tildelt til alle komponenter i Microsoft Defender til Slutpunkt til Mac.
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1015416-20121111154160"></a>101.54.16 (20.121111.15416.0)

- macOS 10.14 (Mojave) understøttes ikke længere
- Når en produktindstilling ikke længere administreres af administratoren via MDM, ændres den nu tilbage til den værdi, den havde, før den blev administreret (den værdi, der blev konfigureret lokalt af slutbrugeren, eller, hvis der ikke udtrykkeligt blev angivet en sådan lokal værdi, den standardværdi, der blev brugt af produktet). Før denne ændring bevares den administrerede værdi, efter at en indstilling er holdt op med at blive administreret, og den blev stadig brugt af produktet.
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1014925-20121092149250"></a>101.49.25 (20.121092.14925.0)

- Der er blevet tilføjet en ny parameter til kommandolinjeværktøjet til at styre, om arkiver scannes under scanninger efter behov. Dette kan konfigureres via `mdatp config scan-archives --value [enabled/disabled]`. Som standard er denne indstillet til `enabled`.
- Fejlrettelser

## <a name="1014727-20121082147270"></a>101.47.27 (20.121082.14727.0)

- Rettelse til et system, der fryser ved lukning på macOS Mojave og macOS Catalina

## <a name="1014384-20121082143840"></a>101.43.84 (20.121082.14384.0)

- Build for kandidater til macOS 12 (Monterey)
- Fejlrettelser

## <a name="1014110-20121072141100"></a>101.41.10 (20.121072.14110.0)

- Nye parametre er føjet til kommandolinjeværktøjet:
  - Kontrollere graden af parallelitet for scanninger efter behov. Dette kan konfigureres via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Som standard anvendes der en grad af `2` parallelitet.
  - Kontroller, om scanninger efter sikkerhedsintelligensopdateringer aktiveres eller deaktiveres. Dette kan konfigureres via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Som standard er denne indstillet til `enabled`.
- Ændring af produktlogniveauet kræver nu udvidelse
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1014084-20121071140840"></a>101.40.84 (20.121071.14084.0)

- Indbygget M1-chipsupport
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1013797-20121062137970"></a>101.37.97 (20.121062.13797.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1013428-20121061134280"></a>101.34.28 (20.121061.13428.0)

- Fejlrettelser

## <a name="1013427-20121052134270"></a>101.34.27 (20.121052.13427.0)

- Fejlrettelser

## <a name="1013420-20121051134200"></a>101.34.20 (20.121051.13420.0)

- [Enhedsstyring til macOS](mac-device-control-overview.md) er nu generelt tilgængelig
- Vi har rettet et problem, hvor en hurtig scanning ikke kunne startes fra statusmenuen på macOS 11 (Big Sur)
- Andre fejlrettelser

## <a name="1013269-20121042132690"></a>101.32.69 (20.121042.13269.0)

- Vi har rettet et problem, hvor samtidig adgang til nøgleringen fra Microsoft Defender til slutpunktet og andre programmer kan føre til beskadigelse af nøglering.

## <a name="1012964-20121042129640"></a>101.29.64 (20.121042.12964.0)

- Fra og med denne version afhjælpes de trusler, der registreres under antivirusscanninger efter behov, som udløses via kommandolinjeklienten, automatisk. Trusler, der registreres under scanninger, der udløses via brugergrænsefladen, kræver stadig manuel handling.
- `mdatp diagnostic real-time-protection-statistics` understøtter nu yderligere to parametre:
  - `--sort`: sorterer outputtet faldende efter det samlede antal scannede filer
  - `--top N`: viser de øverste N resultater (fungerer kun, hvis `--sort` det også er angivet)
- Forbedringer af ydeevnen (specielt ved brug af AFRLYS) & fejlrettelser

## <a name="1012750-20121022127500"></a>101.27.50 (20.121022.12750.0)

- Rettelse af plads til udløb af Apple-certifikat til macOS Catalina og tidligere. Denne løsning gendanner funktionaliteten & til administration af trusselssikkerhedsrisiko (TVM).

## <a name="1012569-20121022125690"></a>101.25.69 (20.121022.12569.0)

- Microsoft Defender til Endpoint på macOS er nu tilgængelig i prøveversionen for kunder i det amerikanske offentlige. Du kan finde flere oplysninger [under Microsoft Defender til slutpunkt for kunder i det amerikanske offentlige.](gov.md)
- Forbedringer af ydeevnen (specifikt for situationen, når appen XCodeRettelser bruges) & fejlrettelser.

## <a name="1012364-20121021123640"></a>101.23.64 (20.121021.12364.0)

- Der er blevet føjet en ny indstilling til kommandolinjeværktøjet for at få vist oplysninger om den seneste scanning efter behov. Hvis du vil have vist oplysninger om den seneste scanning efter behov, skal du køre `mdatp health --details antivirus`
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1012279-20121012122790"></a>101.22.79 (20.121012.12279.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011988-20121011119880"></a>101.19.88 (20.121011.11988.0)

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011948-20120121119480"></a>101.19.48 (20.120121.11948.0)

> [!NOTE]
> Den gamle syntaks for kommandolinjeværktøjet frarådes i denne version. Du kan finde oplysninger om den nye syntaks i [Ressourcer](mac-resources.md#configuring-from-the-command-line).

- Der er tilføjet en ny kommandolinjeskifter for at deaktivere netværksudvidelsen: `mdatp system-extension network-filter disable`. Denne kommando kan være nyttig til fejlfinding af netværksproblemer, der kan være relateret til Microsoft Defender til slutpunkt på Mac
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011921-20120101119210"></a>101.19.21 (20.120101.11921.0)

- Fejlrettelser

## <a name="1011526-20120102115260"></a>101.15.26 (20.120102.11526.0)

- Forbedret pålideligheden af agenten, når den kører på macOS 11 Big Sur
- Vi har tilføjet en ny kommandolinjekontakt (`--ignore-exclusions`) for at ignorere udeladelse af AV under brugerdefinerede scanninger (`mdatp scan custom`)
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1011375-20120101113750"></a>101.13.75 (20.120101.11375.0)

- Fjernede betingelser, når Microsoft Defender til slutpunkt udløste en macOS 11-fejl (Big Sur), der opstår som en grund til panik
- Vi har rettet en hukommelseslækage i Endpoint Security-systemudvidelsen, når den kørte på mac 11 (Big Sur)
- Fejlrettelser

## <a name="1011072"></a>101.10.72

- Fejlrettelser

## <a name="1010961"></a>101.09.61

- Der er tilføjet en ny administreret [indstilling til deaktivering af indstillingen til at sende feedback](mac-preferences.md#show--hide-option-to-send-feedback)
- Ikonet for statusmenu viser nu en sund tilstand, når produktindstillingerne administreres. Tidligere viste ikonet for statusmenuen en advarsel eller fejltilstand, selvom produktindstillingerne blev administreret af administratoren
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010950"></a>101.09.50

- Denne produktversion er blevet valideret på macOS Big Sur 11 beta 9

- Den nye syntaks `mdatp` for kommandolinjeværktøjet er nu standard. Du kan finde flere oplysninger om den nye [syntaks i Resources for Microsoft Defender for Endpoint på macOS](mac-resources.md#configuring-from-the-command-line)

  > [!NOTE]
  > Den gamle syntaks for kommandolinjeværktøj fjernes fra produktet d. **1. januar 2021**.

- Udvidet `mdatp diagnostic create` med en ny parameter (`--path [directory]`), der gør det muligt at gemme diagnosticeringslogfilerne i en anden mappe
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010949"></a>101.09.49

- Forbedringer af brugergrænsefladen til at skelne fra udeladelse, der administreres af it-administratoren kontra udeladelse, der er defineret af den lokale bruger
- Forbedret CPU-udnyttelse under on-demand-scanninger
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010723"></a>101.07.23

- Nye felter blev føjet til outputtet `mdatp --health` af til kontrol af status for passiv tilstand og Slutpunktsregistrering og -svar gruppe-id

  > [!NOTE]
  > `mdatp --health` udskiftes med i `mdatp health` en fremtidig produktopdatering.

- Vi har rettet en fejl, hvor automatisk indsendelse af eksempler ikke blev markeret som administreret i brugergrænsefladen
- Der er tilføjet nye indstillinger til at kontrollere opbevaring af elementer i antivirus-scanningsoversigten. Du kan nu [angive det antal dage,](mac-preferences.md#antivirus-scan-history-retention-in-days) elementer i scanningsoversigten skal bevares, og angive det [maksimale antal elementer i scanningsoversigten](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history)
- Fejlrettelser

## <a name="1010663"></a>101.06.63

- Adresseret en regression af ydeevnen, der blev introduceret i version `101.05.17`. Den regression blev introduceret med rettelsen for at eliminere den gå i panik, som nogle kunder har observeret ved åbning af SMB-shares. Vi har gendan denne kodeændring og er ved at undersøge alternative metoder til at fjerne kerne panik.

## <a name="1010517"></a>101.05.17

> [!IMPORTANT]
> Vi arbejder på en ny og forbedret syntaks `mdatp` for kommandolinjeværktøjet. Den nye syntaks er i øjeblikket standard i opdateringskanalerne Insider Fast og Insider Slow. Vi opfordrer dig til at bruge denne nye syntaks til at famliliarize dig selv.
>
> Vi fortsætter med at understøtte den gamle syntaks parallelt med den nye syntaks og giver mere kommunikation om uddegrænsningsplanen for den gamle syntaks i de kommende måneder.

- Løste en kernel-panik, der nogle gange opstod ved åbning af SMB-filshares
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010516"></a>101.05.16

- Forbedringer af hurtig scanningslogik for at reducere antallet af scannede filer betydeligt
- Vi [har tilføjet understøttelse af autofuldførelse](mac-resources.md#how-to-enable-autocompletion) for kommandolinjeværktøjet
- Fejlrettelser

## <a name="1010312"></a>101.03.12

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010154"></a>101.01.54

- Forbedringer af kompatibilitet med Time Machine
- Forbedringer af tilgængelighed
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1010031"></a>101.00.31

- Forbedret [onboardingoplevelse for Intune-brugere](/mem/intune/apps/apps-advanced-threat-protection-macos)
- [Antivirusudetagelser understøtter nu jokertegn](mac-exclusions.md#supported-exclusion-types)
- Vi har tilføjet muligheden for at udløse antivirusscanninger fra genvejsmenuen i macOS. Du kan nu højreklikke på en fil eller mappe i Finder og vælge **Scan med Microsoft Defender til Slutpunkt**
- Nedgradering af produkter direkte er nu eksplicit tilladt af installationsprogrammet. Hvis du vil nedgradere, skal du først fjerne den eksisterende version og omkonfigurere din enhed
- Andre forbedringer af ydeevnen & fejlrettelser

## <a name="1009027"></a>100.90.27

- Du kan nu [angive en opdateringskanal](mac-updates.md#set-the-channel-name) for Microsoft Defender til Slutpunkt på macOS, der er anderledes end den systembaserede opdateringskanal
- Ikon for nyt produkt
- Andre forbedringer af brugeroplevelsen
- Fejlrettelser

## <a name="1008692"></a>100.86.92

- Forbedringer af kompatibilitet med Time Machine
- Vi har rettet et problem, hvor produktet nogle gange ikke ryddede alle filer under `/Library/Application Support/Microsoft/Defender` installationen
- Reduceret CPU-udnyttelse af produktet, når Microsoft-produkter opdateres via Microsoft Automatiske opdateringer
- Andre forbedringer af ydeevnen & fejlrettelser

## <a name="1008691"></a>100.86.91

> [!CAUTION]
> For at sikre den mest komplette beskyttelse til dine macOS-enheder og i overensstemmelse med Apple stopper levering af macOS oprindelige sikkerhedsopdateringer til OS-versioner, der er ældre end [aktuel - 2], vil MDATP til Mac-installation og opdateringer ikke længere være understøttet på macOS Sierra [10.12]. MDATP til Mac-opdateringer og -forbedringer leveres til enheder, der kører versioner Catalina [10.15], Mojave [10.14] og High Sierra [10.13].
>
> Hvis du allerede har MDATP til Mac installeret på dine Enheder i Sierra [10.12], skal du opgradere til den nyeste macOS-version for at eliminere risikoen for at miste beskyttelse.

- Forbedringer af ydeevnen & fejlrettelser

## <a name="1008373"></a>100.83.73

- Der er blevet tilføjet flere kontrolelementer for [it-administratorer vedrørende administration af udeladelse](mac-preferences.md#exclusion-merge-policy)[, administration](mac-preferences.md#threat-type-settings-merge-policy) af indstillinger for trusselstyper og [handlinger, der ikke længere kan være trusler](mac-preferences.md#disallowed-threat-actions)
- Når Fuld diskadgang ikke er aktiveret på enheden, vises der nu en advarsel i statusmenuen
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1008260"></a>100.82.60

- Vi har løst et problem, hvor produktet ikke kunne begynde at følge en definitionsopdatering.

## <a name="1008042"></a>100.80.42

- Fejlrettelser

## <a name="1007942"></a>100.79.42

- Rettede et problem, hvor Microsoft Defender til slutpunkt på Mac nogle gange forstyrrede Time Machine
- Der er blevet føjet en ny parameter til kommandolinjeværktøjet til test af forbindelsen med backendtjenesten

  ```bash
  mdatp connectivity test
  ```

- Vi har tilføjet muligheden for at få vist hele trusselshistorikken i brugergrænsefladen (kan åbnes fra **historikvisningen for** Beskyttelse)
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1007215"></a>100.72.15

- Fejlrettelser

## <a name="1007099"></a>100.70.99

- Vi har rettet et problem, der påvirker nogle brugeres mulighed for at opgradere til macOS Catalina, når beskyttelse i realtid er aktiveret. Dette sporadisk problem blev forårsaget af Microsoft Defender til slutpunktslåsning af filer i Catalina-opgraderingspakken, mens du scanner dem for trusler, hvilket har ført til fejl i opgraderingssekvensen.

## <a name="1006899"></a>100.68.99

- Vi har tilføjet muligheden for at konfigurere antivirusfunktionaliteten til at køre i [passiv tilstand](mac-preferences.md#enforcement-level-for-antivirus-engine)
- Forbedringer af ydeevnen & fejlrettelser

## <a name="1006528"></a>100.65.28

- Understøttelse af macOS Catalina er blevet tilføjet

  > [!CAUTION]
  > macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til bestemte placeringer på disken (f.eks Dokumenter, Overførsler, Skrivebord osv.) uden udtrykkeligt samtykke. I fravær af dette samtykke kan Microsoft Defender til Slutpunkt ikke fuldt ud beskytte din enhed.
  >
  > Mekanismen til at give dette samtykke afhænger af, hvordan du har installeret Microsoft Defender til slutpunkt:
  >
  > - For manuelle installationer skal du se de opdaterede instruktioner i [emnet Manuel](mac-install-manually.md#how-to-allow-full-disk-access) installation.
  > - For administrerede installationer skal du se de opdaterede instruktioner i [de SYLF-baserede installations](mac-install-with-jamf.md)- [Microsoft Intune-baserede installationsemner](mac-install-with-intune.md#create-system-configuration-profiles).

- Forbedringer af ydeevnen & fejlrettelser
