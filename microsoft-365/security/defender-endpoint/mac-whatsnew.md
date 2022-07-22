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
ms.openlocfilehash: 3ea2822adabcd0a747d34fbdb8c6d8d2c944afdf
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969529"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-mac"></a>Nyheder i Microsoft Defender for Endpoint på Mac

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Du kan få flere oplysninger om Microsoft Defender for Endpoint på andre operativsystemer: 
- [Nyheder i Microsoft Defender for Endpoint på Linux](linux-whatsnew.md) 
- [Nyheder i Microsoft Defender for Endpoint på iOS](ios-whatsnew.md)</br>

<details>
  <summary>Jul-2022 (build: 101.73.77 | Version: 20.122062.17377.0)</summary>

&ensp;Udgivet: **21. jul 2022**<br/>
&ensp;Publiceret: **21. jul 2022**<br/>
&ensp;Build: **101.73.77**<br/>
&ensp;Version: **20.122062.17377.0**<br/>
&ensp;Programversion: **1.1.19200.3**<br/>
&ensp;Signaturversion: **1.367.1011.0**<br/>

**Nyheder**

- Løste et problem, hvor udskrivningen ikke kunne fuldføres pga. netværksudvidelsen
- Tilføjede en indstilling til [konfiguration af beregning af filhash](mac-preferences.md#configure-file-hash-computation-feature)
- Fra dette build og frem har produktet som standard det nye antimalwareprogram
- Forbedringer af ydeevnen i forbindelse med filkopieringshandlinger
- Fejlrettelser

<br/>
</details>

<details>
  <summary>Jul-2022 (build: 101.71.18 | Version: 20.122052.17118.0)</summary>

&ensp;Udgivet: **7. jul 2022**<br/>
&ensp;Publiceret: **7. jul 2022**<br/>
&ensp;Build: **101.71.18**<br/>
&ensp;Version: **20.122052.17118.0**<br/>

**Nyheder**

- `mdatp connectivity test` blev udvidet med en ekstra URL-adresse, som produktet kræver for at fungere korrekt. Den nye URL-adresse er [https://go.microsoft.com/fwlink/?linkid=2144709](https://go.microsoft.com/fwlink/?linkid=2144709).
- Indtil nu har niveauet for produktloggen ikke været vedvarende mellem genstart af produktet. Fra og med denne version er der en ny kommandolinjeværktøjsparameter, der fastholder logniveauet. Den nye kommando er `mdatp log level persist --level <level>`.
- Løste en fejl i produktinstallationspakken, der i sjældne tilfælde kan medføre tab af produkttilstand under opdateringer
- Forbedringer af ydeevnen for filkopieringshandlinger og indbyggede macOS-programmer
- Fejlrettelser

<br/>
</details>

<details>
  <summary>Jun-2022 (build: 101.70.19 | Version: 20.122051.17019.0)</summary>

&ensp;Udgivet: **14. juni 2022**<br/>
&ensp;Publiceret: **14. juni 2022**<br/>
&ensp;Build: **101.70.19**<br/>
&ensp;Version: **20.122051.17019.0**<br/>

**Nyheder**

- Løste en fejl, hvor trusselsrelaterede meddelelser ikke altid blev præsenteret for slutbrugeren.
- Forbedringer af ydeevnen & andre fejlrettelser

<br/>
</details>


<details>
  <summary>Jun-2022 (build: 101.70.18 | Version: 20.122042.17018.0)</summary>

&ensp;Udgivet: **2. juni 2022**<br/>
&ensp;Publiceret: **2. juni 2022**<br/>
&ensp;Build: **101.70.18**<br/>
&ensp;Version: **20.122042.17018.0**<br/>

**Nyheder**

- Løste en fejl, hvor installationspakken nogle gange hængende på ubestemt tid under produktopdateringer
- Løste en fejl, hvor produktet nogle gange fejlagtigt registrerede filer i karantænemappen
- Forbedringer af ydeevnen & andre fejlrettelser

<br/>
</details>

<details>
  <summary>Maj-2022 (build: 101.66.54 | Version: 20.122041.16654.0) </summary>

&ensp;Udgivet: **11. maj 2022**<br/>
&ensp;Publiceret: **11. maj 2022**<br/>
&ensp;Build: **101.66.54**<br/>
&ensp;Version: **20.122041.16654.0**<br/>


**Nyheder**

- Løste et problem, hvor `mdatp diagnostic real-time-protection-statistics` den korrekte processti ikke blev udskrevet i nogle tilfælde.
- Fejlrettelser

<br/>
</details>

<details>
  <summary>Apr-2022 (build: 101.64.15 | Version: 20.122032.16415.0)</summary>

&ensp;Udgivet: **26. april 2022**<br/>
&ensp;Publiceret: **26. april 2022**<br/>
&ensp;Build: **101.64.15**<br/>
&ensp;Version: **20.122032.16415.0**<br/>

**Nyheder**

- Løste en regression, der blev introduceret i version 101.61.69, hvor ikonet for statusmenuen nogle gange viste et fejlikon, selvom der ikke kræves nogen handling fra slutbrugeren
- Forbedret feltet `conflicting_applications` i `mdatp health` for kun at vise de seneste 10 processer og også for at inkludere procesnavnene. Det gør det nemmere at identificere, hvilke processer der potentielt er i konflikt med Microsoft Defender for Endpoint til Mac.
- Løste en fejl, `mdatp device-control removable-media policy list` hvor leverandør-id og produkt-id blev vist som decimal i stedet for hexadecimale
- Forbedringer af ydeevnen & andre fejlrettelser

<br/>
</details>

<details>
  <summary>Mar-2022 (build: 101.61.69 | Version: 20.122022.16169.0) </summary>

&ensp;Udgivet: **25. mar 2022**<br/>
&ensp;Publiceret: **25. mar 2022**<br/>
&ensp;Build: **101.61.69**<br/>
&ensp;Version: **20.122022.16169.0**<br/>

**Nyheder**

- Fejlrettelser

<br/>
</details>

<details>
  <summary>Mar-2022 (build: 101.60.91 | Version: 20.122021.16091.0)</summary>

&ensp;Udgivet: **8. mar 2022**<br/>
&ensp;Udgivet: **8. marts 2022**<br/>
&ensp;Build: **101.60.91**<br/>
&ensp;Version: **20.122021.16091.0**<br/>

**Nyheder**

- Denne version indeholder en sikkerhedsopdatering til [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)

<br/>
</details>

<details>
  <summary>Feb-2022 (build: 101.59.50 | Version: 20.122021.15950.0) </summary>

&ensp;Udgivet: **28. feb. 2022**<br/>
&ensp;Publiceret: **28. februar 2022**<br/>
&ensp;Build: **101.59.50**<br/>
&ensp;Version: **20.122021.15950.0**<br/>

**Nyheder**

- Denne version tilføjer understøttelse af macOS 12.3. Fra og med macOS 12.3 [fjerner Apple Python 2.7](https://developer.apple.com/documentation/macos-release-notes/macos-12_3-release-notes). Der vil som standard ikke være installeret nogen Python-version på macOS. **HANDLING ER NØDVENDIG**: 
  - Brugerne skal opdatere Microsoft Defender for Endpoint til Mac til version 101.59.50 (eller nyere), før de opdaterer deres enheder til macOS Monterey 12.3 (eller nyere). Denne minimale version 101.59.50 er en forudsætning for at fjerne Python-relaterede problemer med Microsoft Defender for Endpoint til Mac på macOS Monterey.
  - I forbindelse med fjerninstallationer skal eksisterende MDM-konfigurationer opdateres til Microsoft Defender for Endpoint til Mac version 101.59.50 (eller nyere). Hvis du sender en ældre Microsoft Defender for Endpoint til Mac-versionen via MDM til macOS Monterey 12.3 (eller nyere), medfører det en installationsfejl.

<br/>
</details>

<details>
  <summary>Feb-2022 (build: 101.59.10 | Version: 20.122012.15910.0)</summary>

&ensp;Udgivet: **22. februar 2022**<br/>
&ensp;Publiceret: **22. februar 2022**<br/>
&ensp;Build: **101.59.10**<br/>
&ensp;Version: **20.122012.15910.0**<br/>

**Nyheder**

- Kommandolinjeværktøjet understøtter nu gendannelse af filer, der er sat i karantæne, på en anden placering end den, hvor filen oprindeligt blev registreret. Dette kan gøres via `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Udvidet enhedsstyring til håndtering af enheder, der er tilsluttet thunderbolt 3
- Forbedret håndteringen af politikker for enhedsstyring, der indeholder ugyldige leverandør-id'er og produkt-id'er. Før denne version blev hele politikken ignoreret, hvis politikken indeholdt et eller flere ugyldige id'er. Fra og med denne version ignoreres kun de ugyldige dele af politikken. Problemer med politikken vises via `mdatp device-control removable-media policy list`.
- Fejlrettelser

<br/>
</details>

<details>
  <summary>Feb-2022 (build: 101.56.62 | Version: 20.121122.15662.0)</summary>

&ensp;Udgivet: **7. feb. 2022**<br/>
&ensp;Udgivet: **7. feb. 2022**<br/>
&ensp;Build: **101.56.62**<br/>
&ensp;Version: **20.121122.15662.0**<br/>

**Nyheder**

- Fejlrettelser 

<br/>
</details>

<details>
  <summary> Jan-2022 (build: 101.56.35 | Version: 20.121121.15635.0)</summary>

&ensp;Udgivet: **30. januar 2022**<br/>
&ensp;Publiceret: **30. januar 2022**<br/>
&ensp;Build: **101.56.35**<br/>
&ensp;Version: **20.121121.15635.0**<br/>

**Nyheder**

- Programmet er blevet omdøbt fra "Microsoft Defender ATP" til "Microsoft Defender". Slutbrugerne vil se følgende ændringer:
- Stien til programinstallationen er ændret fra `/Application/Microsoft Defender ATP.app` til `/Applications/Microsoft Defender.app`.
- I brugeroplevelsen er forekomster af "Microsoft Defender ATP" blevet erstattet med "Microsoft Defender"
- Løste et problem, hvor nogle VPN-programmer ikke kunne oprette forbindelse på grund af netværksindholdsfilteret, der distribueres med Microsoft Defender for Endpoint til Mac
- Løste et problem, der blev fundet i macOS 12.2 beta 2, hvor installationspakken ikke kunne åbnes på grund af en ændring i operativsystemet, som forhindrer installation af pakker med visse egenskaber. Selvom det ser ud til, at denne os-ændring ikke er inkluderet i den endelige version af macOS 12.2, er det sandsynligt, at den vil blive genindført i en fremtidig macOS-version. Derfor opfordrer vi alle virksomhedsadministratorer til at opdatere Microsoft Defender for Endpoint-pakken i deres administrationskonsol til denne produktversion (eller en nyere version).
- Løste et problem, der kan ses på nogle M1-enheder, hvor produktet sidder fast med ugyldige antimalwaredefinitioner og ikke kunne opdateres til et arbejdssæt af definitioner.
- `mdatp health`output er blevet udvidet med en ekstra attribut kaldet `full_disk_access_enabled` , der kan bruges til at afgøre, om Full Disk Access er tildelt til alle komponenter i Microsoft Defender for Endpoint til Mac.
- Forbedringer af ydeevnen & fejlrettelser

<br/>
</details>

<details>
  <summary>Jan-2022 (build: 101.54.16 | Version: 20.121111.15416.0) </summary>

&ensp;Udgivet: **12. januar 2022**<br/>
&ensp;Publiceret: **12. januar 2022**<br/>
&ensp;Build: **101.54.16**<br/>
&ensp;Version: **20.121111.15416.0**<br/>

**Nyheder**

- macOS 10.14 (Mojave) understøttes ikke længere
- Når en produktindstilling stopper med at blive administreret af administratoren via MDM, vender den nu tilbage til den værdi, den havde, før den blev administreret (den værdi, der er konfigureret lokalt af slutbrugeren, eller, hvis en sådan lokal værdi ikke udtrykkeligt blev angivet, den standardværdi, der bruges af produktet). Før denne ændring bevares den administrerede værdi, efter at en indstilling stoppede med at blive administreret, og den blev stadig brugt af produktet.
- Forbedringer af ydeevnen & fejlrettelser
    
<br/>
</details>

<details><summary>Udgivelser fra 2021 </summary><blockquote>
    <details><summary>(Build: 101.49.25 | Version: 20.121092.14925.0)</summary>

&ensp;Build:  **101.49.25**<br/>
&ensp;Version:  **20.121092.14925.0** <br/>

**Nyheder**

- Tilføjede en ny parameter til kommandolinjeværktøjet for at styre, om arkiver scannes under scanninger efter behov. Dette kan konfigureres via `mdatp config scan-archives --value [enabled/disabled]` . Som standard er dette angivet til aktiveret. 
- Fejlrettelser  

<br/>
</details>
 
<details><summary>(Build: 101.47.27 | Version: 20.121082.14727.0)</summary>

&ensp;Build: **101.47.27**<br/>
&ensp;Version:  **20.121082.14727.0** <br/>

**Nyheder**
- Rettelse af en systemfrysning, der forekommer ved lukning på macOS Mojave og macOS Catalina. 

<br/>
</details>

<details><summary>(Build: 101.43.84 | Version: 20.121082.14384.0)</summary>

&ensp;Build: **101.43.84**<br/>
&ensp;Version:  **20.121082.14384.0** <br/>

**Nyheder**
- Kandidatbuild til macOS 12 (Monterey) 
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.41.10 | Version: 20.121072.14110.0)</summary>

&ensp;Build: **101.41.10**<br/>
&ensp;Version:  **20.121072.14110.0** <br/>

**Nyheder**
- Nye parametre er føjet til kommandolinjeværktøjet: 
    - Kontrollér graden af parallelitet for on-demand-scanninger. Dette kan konfigureres via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]` . Der bruges som standard en grad af parallelitet på 2. 
    - Kontrollér, om scanninger efter sikkerhedsintelligensopdateringer er aktiveret eller deaktiveret. Dette kan konfigureres via `mdatp config scan-after-definition-update --value [enabled/disabled]` . Som standard er dette angivet til aktiveret. 
- Ændring af niveauet for produktloggen kræver nu udvidede rettigheder. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.40.84 | Version: 20.121071.14084.0)</summary>

&ensp;Build:  **101.40.84**<br/>
&ensp;Version:  **20.121071.14084.0** <br/>

**Nyheder**
- Indbygget understøttelse af M1-chip 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.37.97 | Version: 20.121062.13797.0)</summary>

&ensp;Build: **101.37.97**<br/>
&ensp;Version:  **20.121062.13797.0** <br/>

**Nyheder**
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.34.28 | Version: 20.121061.13428.0)</summary>

&ensp;Build: **101.34.28**<br/>
&ensp;Version:  **20.121061.13428.0** <br/>

**Nyheder**
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.34.27 | Version: 20.121052.13427.0)</summary>

&ensp;Build: **101.34.27**<br/>
&ensp;Version:  **20.121052.13427.0** <br/>

**Nyheder**
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.34.20 | Version: 20.121051.13420.0)</summary>

&ensp;Build: **101.34.20**<br/>
&ensp;Version:  **20.121051.13420.0** <br/>

**Nyheder**
- [Enhedsstyring til macOS](mac-device-control-overview.md)  er nu offentligt tilgængelig. 
- Løste et problem, hvor en hurtig scanning ikke kunne startes fra statusmenuen på macOS 11 (Big Sur). 
- Andre fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.32.69 | Version: 20.121042.13269.0)</summary>

&ensp;Build: **101.32.69**<br/>
&ensp;Version:  **20.121042.13269.0** <br/>

**Nyheder**
- Løste et problem, hvor samtidig adgang til nøglering fra Microsoft Defender for Endpoint og andre programmer kan føre til beskadigelse af nøglering.

<br/>
</details>

<details><summary>(Build: 101.29.64 | Version: 20.121042.12964.0)</summary>

&ensp;Build: **101.29.64**<br/>
&ensp;Version:  **20.121042.12964.0** <br/> 

**Nyheder**
- Fra og med denne version afhjælpes trusler, der registreres under on-demand-antivirusscanninger, som udløses via kommandolinjeklienten, automatisk. Trusler, der registreres under scanninger, der udløses via brugergrænsefladen, kræver stadig manuel handling. 
- `mdatp diagnostic real-time-protection-statistics` understøtter nu to ekstra parametre: 
    - `--sort`: sorterer outputtet faldende efter det samlede antal scannede filer 
    - `--top N`: viser de øverste N-resultater (fungerer kun, hvis `--sort` der også er angivet) 
- Forbedringer af ydeevnen (specielt til hvornår `YARN` bruges) & fejlrettelser

<br/>
</details>

<details><summary>(Build: 101.27.50 | Version: 20.121022.12750.0)</summary>

&ensp;Build:  **101.27.50**<br/>
&ensp;Version:  **20.121022.12750.0** <br/> 

**Nyheder**
- Rettelse for at imødekomme udløb af Apple-certifikat til macOS Catalina og tidligere. Denne rettelse gendanner TVM-funktionalitet (Threat & Vulnerability Management).  

<br/>
</details>

<details><summary>(Build: 101.25.69 | Version: 20.121022.12569.0)</summary>

&ensp;Build: **101.25.69**<br/>
&ensp;Version:  **20.121022.12569.0** <br/> 

**Nyheder**
- Microsoft Defender for Endpoint på macOS er nu tilgængelig som prøveversion for us government-kunder. Du kan få flere oplysninger  [under Microsoft Defender for Endpoint for us government-kunder](gov.md) . 
- Forbedringer af ydeevnen (især i forbindelse med brug af XCode Simulator-appen) & fejlrettelser. 

<br/>
</details>

<details><summary>(Build: 101.23.64 | Version: 20.121021.12364.0)</summary>

&ensp;Build: **101.23.64**<br/>
&ensp;Version:  **20.121021.12364.0** <br/> 

**Nyheder**
- Der er føjet en ny indstilling til kommandolinjeværktøjet for at få vist oplysninger om den seneste scanning efter behov. Hvis du vil have vist oplysninger om den seneste scanning efter behov, skal du køre `mdatp health --details antivirus`. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

</details>

<details><summary>Tidligere udgivelser </summary><blockquote>
<details><summary>(Build: 101.22.79 | Version: 20.121012.12279.0)</summary>

&ensp;Build: **101.22.79** <br> &ensp;Version: **20.121012.12279.0**<br>

**Nyheder**
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.19.88 | Version: 20.121011.11988.0)</summary>

&ensp;Build:**101.19.88**<br>
&ensp;Version: **20.121011.11988.0**<br>

**Nyheder**
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.19.48 | Version: 20.120121.11948.0)</summary>

&ensp;Build: **101.19.48**<br>
&ensp;Version: **20.120121.11948.0**<br>

**Nyheder**
> [!NOTE]
> Den gamle kommandolinjeværktøjssyntaks frarådes i denne version. Du kan få oplysninger om den nye syntaks under [Ressourcer](mac-resources.md#configuring-from-the-command-line). 
- Tilføjede en ny kommandolinjeparameter for at deaktivere netværksudvidelsen: `mdatp system-extension network-filter disable`. Denne kommando kan være nyttig til fejlfinding af netværksproblemer, der kan være relateret til Microsoft Defender for Endpoint på Mac. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.19.21 | Version: 20.120101.11921.0)</summary>

&ensp;Build: **101.19.21**<br>
&ensp;Version: **20.120101.11921.0** <br>

**Nyheder**
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.15.26 | Version: 20.120102.11526.0)</summary>

&ensp;Build: **101.15.26**<br>
&ensp;Version: **20.120102.11526.0**<br>

**Nyheder**
- Forbedret pålideligheden af agenten, når du kører på macOS 11 Big Sur. 
- Tilføjede en ny kommandolinjeparameter (`--ignore-exclusions`) for at ignorere AV-udeladelser under brugerdefinerede scanninger (`mdatp scan custom`). 
- Forbedringer af ydeevnen & fejlrettelser

<br/> 
</details>

<details><summary>(Build: 101.13.75 | Version: 20.120101.11375.0)</summary>

&ensp;Build: **101.13.75**<br>
&ensp;Version: **20.120101.11375.0**<br>

**Nyheder** 
- Fjernede betingelser, da Microsoft Defender for Endpoint udløste en macOS 11 (Big Sur)-fejl, der manifesterer sig i kerne panik. 
- Løste en hukommelsesfejl i Endpoint Security-systemudvidelsen, når den kører på mac 11 (Big Sur). 
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.10.72)</summary>

&ensp;Build: **101.10.72** <br>

**Nyheder** 
- Fejlrettelser  

<br/>
</details>

<details><summary>(Build: 101.09.61)</summary>

&ensp;Build: **101.09.61**<br>

**Nyheder** 
- Der er tilføjet en ny administreret indstilling for [deaktivering af muligheden for at sende feedback](mac-preferences.md#show--hide-option-to-send-feedback). 
- Statusmenuikonet viser nu en tilstand, der er i orden, når produktindstillingerne administreres. Tidligere viste ikonet for statusmenuen en advarsels- eller fejltilstand, selvom produktindstillingerne blev administreret af administratoren. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.09.50)</summary>

&ensp;Build: **101.09.50**<br>

**Nyheder** 
- Denne produktversion er blevet valideret på macOS Big Sur 11 beta 9. 
- Den nye syntaks for mdatp-kommandolinjeværktøjet er nu standardværktøjet. Du kan få flere oplysninger om den nye syntaks under [Ressourcer til Microsoft Defender for Endpoint på macOS](mac-resources.md#configuring-from-the-command-line). 
> [!NOTE]
> Den gamle kommandolinjeværktøjssyntaks fjernes fra produktet **den 1. januar 2021**.
- Udvidet `mdatp diagnostic create` med en ny parameter (`--path [directory]`), der gør det muligt at gemme diagnosticeringslogfilerne i en anden mappe. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.09.49)</summary>

&ensp;Build: **101.09.49**<br>

**Nyheder** 
- Forbedringer af brugergrænsefladen for at differentiere undtagelser, der administreres af it-administratoren i forhold til undtagelser, der er defineret af den lokale bruger. 
- Forbedret CPU-udnyttelse under on-demand-scanninger. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.07.23)</summary>

&ensp;Build: **101.07.23**<br>

**Nyheder** 
- Nye felter er føjet til outputtet for `mdatp --health` til kontrol af status for passiv tilstand og EDR-gruppe-id' et. 
> [!NOTE]
> `mdatp --health` erstattes med `mdatp health` i en fremtidig produktopdatering. 
- Løste en fejl, hvor automatisk indsendelse af eksempler ikke blev markeret som administreret i brugergrænsefladen. 
- Der er tilføjet nye indstillinger til styring af opbevaring af elementer i antivirusscanningshistorikken. Du kan nu [angive det antal dage, elementer skal bevares i scanningsoversigten](mac-preferences.md#antivirus-scan-history-retention-in-days) , og [angive det maksimale antal elementer i scanningshistorikken](mac-preferences.md#maximum-number-of-items-in-the-antivirus-scan-history). 
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.06.63)</summary>

&ensp;Build: **101.06.63**<br>

**Nyheder** 
- Håndterede en regression af ydeevnen, der blev introduceret i versionen `101.05.17`. Regressionen blev introduceret med rettelsen for at fjerne kerne panik nogle kunder har observeret, når de tilgår SMB-aktier. Vi har tilbageført denne kodeændring og undersøger alternative måder at eliminere kerne panik på. 

<br/>
</details>

<details><summary>(Build: 101.05.17)</summary>

&ensp;Build: **101.05.17**<br> 

**Nyheder** 
> [!IMPORTANT]
> Vi arbejder på en ny og forbedret syntaks for `mdatp` kommandolinjeværktøjet. Den nye syntaks er i øjeblikket standard i kanalerne Insider Fast og Insider Slow update. Vi opfordrer dig til at famliliarize dig selv med denne nye syntaks. Vi vil fortsætte med at understøtte den gamle syntaks parallelt med den nye syntaks og vil give mere kommunikation omkring udfasningsplanen for den gamle syntaks i de kommende måneder. 
- Løste en kerne-panik, der nogle gange opstod under adgang til SMB-filshares. 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.05.16)</summary>

&ensp;Build: **101.05.16**<br>

**Nyheder** 
- Forbedringer af hurtig scanningslogik for at reducere antallet af scannede filer væsentligt. 
- Tilføjede [understøttelse af autofuldførelse](mac-resources.md#how-to-enable-autocompletion) for kommandolinjeværktøjet. 
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.03.12)</summary>

&ensp;Build: **101.03.12**<br>

**Nyheder** 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.01.54)</summary>

&ensp;Build: **101.01.54**<br>

**Nyheder** 
- Forbedringer omkring kompatibilitet med tidsmaskine 
- Forbedringer af hjælp til handicappede 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 101.00.31)</summary>

&ensp;Build: **101.00.31** <br>

**Nyheder** 
- Forbedret [produkt onboardingoplevelse for Intune brugere](/mem/intune/apps/apps-advanced-threat-protection-macos) 
-  [Antivirusudeladelser understøtter nu jokertegn](mac-exclusions.md#supported-exclusion-types)
- Muligheden for at udløse antivirusscanninger er blevet tilføjet fra macOS-genvejsmenuen. Du kan nu højreklikke på en fil eller en mappe i Finder og vælge **Scan med Microsoft Defender for Endpoint**. 
- Nedgradering af produkter på stedet er nu udtrykkeligt ikke tilladt af installationsprogrammet. Hvis du har brug for at nedgradere, skal du først fjerne den eksisterende version og konfigurere din enhed igen. 
- Andre forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 100.90.27)</summary>

&ensp;Build: **100.90.27** <br>   

**Nyheder** 
- Du kan nu [angive en opdateringskanal](mac-updates.md#set-the-channel-name) for Microsoft Defender for Endpoint på macOS, der er forskellig fra opdateringskanalen for hele systemet. 
- Nyt produktikon 
- Andre forbedringer af brugeroplevelsen 
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 100.86.92)</summary>

&ensp;Build: **100.86.92**<br>

**Nyheder** 
- Forbedringer omkring kompatibilitet med tidsmaskine 
- Løste et problem, hvor produktet nogle gange ikke rensede alle filer under `/Library/Application Support/Microsoft/Defender` under fjernelsen. 
- Reducerede produktets CPU-udnyttelse, når Microsoft-produkter opdateres via Microsoft Automatiske opdateringer. 
- Andre forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 100.86.91)</summary>

&ensp;Build: **100.86.91**<br>

**Nyheder**
> [!CAUTION]
> For at sikre den mest komplette beskyttelse af dine macOS-enheder og i overensstemmelse med Apple stopper leveringen af indbyggede sikkerhedsopdateringer fra MacOS til os-versioner, der er ældre end [aktuel - 2], understøttes udrulning og opdateringer af MDATP til Mac ikke længere på macOS Sierra [10.12]. MDATP til Mac-opdateringer og -forbedringer leveres til enheder, der kører versioner Catalina [10.15], Mojave [10.14] og High Sierra [10.13].
>
> Hvis du allerede har MDATP til Mac installeret på dine Sierra [10.12]-enheder, skal du opgradere til den nyeste macOS-version for at fjerne risikoen for at miste beskyttelse.

-  Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 100.83.73)</summary>

&ensp;Build: **100.83.73**<br>

**Nyheder**
- It-administratorer har tilføjet flere kontrolelementer i forbindelse [med administration af udelukkelser](mac-preferences.md#exclusion-merge-policy),  [administration af indstillinger for trusselstyper](mac-preferences.md#threat-type-settings-merge-policy) og [ikke-tilladte trusselshandlinger](mac-preferences.md#disallowed-threat-actions). 
- Når Fuld diskadgang ikke er aktiveret på enheden, vises der nu en advarsel i statusmenuen. 
- Forbedringer af ydeevnen & fejlrettelser
 
<br/>
</details>

<details><summary>(Build: 100.82.60)</summary>

&ensp;Build: **100.82.60** <br>

**Nyheder**
- Løste et problem, hvor produktet ikke kan begynde at følge en definitionsopdatering.

<br/> 
</details>

<details><summary>(Build: 100.80.42)</summary>

&ensp;Build: **100.80.42**<br>

**Nyheder**
- Fejlrettelser

<br/> 
</details>

<details><summary>(Build: 100.79.42)</summary>

&ensp;Build: **100.79.42**<br>

**Nyheder**
- Løste et problem, hvor Microsoft Defender for Endpoint på Mac nogle gange forstyrrede Time Machine. 
- Tilføjede en ny parameter til kommandolinjeværktøjet til test af forbindelsen til backendtjenesten
 
  ```bash
  mdatp connectivity test
  ```
- Tilføjede muligheden for at få vist hele trusselshistorikken i brugergrænsefladen (du kan få adgang til den i oversigtsvisningen **beskyttelse** ). 
- Forbedringer af ydeevnen & fejlrettelser

<br/>
</details>

<details><summary>(Build: 100.72.15)</summary> 

&ensp;Build: **100.72.15**<br>

**Nyheder**
- Fejlrettelser 

<br/>
</details>

<details><summary>(Build: 100.70.99)</summary> 

&ensp;Build: **100.70.99**<br>

**Nyheder**
- Løste et problem, der påvirker nogle brugeres mulighed for at opgradere til macOS Catalina, når beskyttelse i realtid er aktiveret. Dette sporadiske problem skyldtes, at Microsoft Defender for Endpoint låser filer i Catalina-opgraderingspakken under scanning efter trusler, hvilket førte til fejl i opgraderingssekvensen.

<br/>
</details> 

<details><summary>(Build: 100.68.99)</summary> 

&ensp;Build: **100.68.99**<br>

**Nyheder**
- Tilføjede muligheden for at konfigurere antivirusfunktionen til at køre i [passiv tilstand](mac-preferences.md#enforcement-level-for-antivirus-engine). 
- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<details><summary>(Build: 100.65.28)</summary> 

&ensp;Build: **100.65.28**<br>

**Nyheder**
- Tilføjet understøttelse af macOS Catalina. 
> [!CAUTION]
> macOS 10.15 (Catalina) indeholder nye forbedringer af sikkerhed og beskyttelse af personlige oplysninger. Fra og med denne version kan programmer som standard ikke få adgang til visse placeringer på disken (f.eks. dokumenter, downloads, desktop osv.) uden eksplicit samtykke. Hvis dette samtykke ikke er til stede, er Microsoft Defender for Endpoint ikke i stand til fuldt ud at beskytte din enhed.
> 
> Mekanismen for tildeling af dette samtykke afhænger af, hvordan du har installeret Microsoft Defender for Endpoint:
> 
> - I forbindelse med manuelle udrulninger skal du se de opdaterede instruktioner i [emnet Manuel udrulning](mac-install-manually.md#how-to-allow-full-disk-access).
> - I forbindelse med administrerede udrulninger skal du se de opdaterede instruktioner i emnerne [for JAMF-baseret udrulning](mac-install-with-jamf.md) og  [Microsoft Intune-baseret udrulning](mac-install-with-intune.md#create-system-configuration-profiles). 

- Forbedringer af ydeevnen & fejlrettelser 

<br/>
</details>

<br/><br/>
</details>