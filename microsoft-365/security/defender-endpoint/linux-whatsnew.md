---
title: Nyheder i Microsoft Defender for Endpoint på Linux
description: Liste over større ændringer af Microsoft Defender for Endpoint på Linux.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, whatsnew, release
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
ms.openlocfilehash: aa6255289ddffd7edb9025e36c69a49f4a3b855b
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603500"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Nyheder i Microsoft Defender for Endpoint på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Denne artikel opdateres ofte for at fortælle dig, hvad der er nyt i de nyeste versioner af Microsoft Defender for Endpoint på Linux. 

- [Nyheder i Defender for Endpoint på macOS](mac-whatsnew.md)
- [Nyheder i Defender for Endpoint på iOS](ios-whatsnew.md)

<details>
  <summary>Jun-2022 (build: 101.71.18 | Version: 30.122052.17118.0)</summary>

&ensp;Udgivet: **24. juni 2022**<br/>
&ensp;Publiceret: **24. juni 2022**<br/>
&ensp;Build: **101.71.18**<br/>
&ensp;Version: **30.122052.17118.0**<br/>


**Nyheder**

- Rettelse til understøttelse af definitionslager på ikke-standardplaceringer (uden for /var) for v2-definitionsopdateringer
- Løste et problem i den produktsensor, der bruges på RHEL 6, og som kan medføre, at operativsystemet hænger
- `mdatp connectivity test` blev udvidet med en ekstra URL-adresse, som produktet kræver for at fungere korrekt. Den nye URL-adresse er [https://go.microsoft.com/fwlink/?linkid=2144709](https://go.microsoft.com/fwlink/?linkid=2144709).
- Indtil nu har niveauet for produktloggen ikke været vedvarende mellem genstart af produktet. Fra og med denne version er der en ny kommandolinjeværktøjsparameter, der fastholder logniveauet. Den nye kommando er `mdatp log level persist --level <level>`.
- Fjernede afhængigheden `python` af fra produktinstallationspakken
- Forbedringer af ydeevnen for filkopihandlinger og behandling af netværkshændelser, der stammer fra `auditd`
- Fejlrettelser
</br>

<br/><br/>
</details>


<details>
  <summary>Maj-2022 (build: 101.68.80 | Version: 30.122042.16880.0)</summary>

&ensp;Udgivet: **23. maj 2022**<br/>
&ensp;Publiceret: **23. maj 2022**<br/>
&ensp;Build: **101.68.80**<br/>
&ensp;Version: **30.122042.16880.0**<br/>

**Nyheder** 

- Tilføjet understøttelse af kerneversion `2.6.32-754.47.1.el6.x86_64` , når du kører på RHEL 6
- På RHEL 6 kan produktet nu installeres på enheder, der kører UEK (Unbreakable Enterprise Kernel)
- Løste et problem, hvor procesnavnet nogle gange blev vist forkert, som `unknown` da det kørte `mdatp diagnostic real-time-protection-statistics`
- Løste en fejl, hvor produktet nogle gange fejlagtigt registrerede filer i karantænemappen
- Løste et problem, hvor `mdatp` kommandolinjeværktøjet ikke fungerede, da `/opt` det blev tilsluttet som et blødt link
- Forbedringer af ydeevnen & fejlrettelser
</br>

<br/><br/>
</details>

<details>
<summary>Maj-2022 (build: 101.65.77 | Version: 30.122032.16577.0)</summary>

&ensp;Udgivet: **2. maj 2022**<br/>
&ensp;Publiceret: **2. maj 2022**<br/>
&ensp;Build: **101.65.77**<br/>
&ensp;Version: **30.122032.16577.0**<br/>


**Nyheder**

- Forbedret feltet `conflicting_applications` i `mdatp health` for kun at vise de seneste 10 processer og også for at inkludere procesnavnene. Det gør det nemmere at identificere, hvilke processer der potentielt er i konflikt med Microsoft Defender for Endpoint til Linux.
- Fejlrettelser


<br/><br/>
</details><details>
<summary>Mar-2022 (build: 101.62.74 | Version: 30.122022.16274.0)</summary>

&ensp;Udgivet: **24. marts 2022**<br/>
&ensp;Publiceret: **24. marts 2022**<br/>
&ensp;Build: **101.62.74**<br/>
&ensp;Version: **30.122022.16274.0**<br/>


**Nyheder**

- Løste et problem, hvor produktet fejlagtigt ville blokere adgang til filer, der er større end 2 GB, når det kører på ældre kerneversioner
- Fejlrettelser


<br/><br/>
</details><details>
<summary>Mar-2022 (build: 101.60.93 | Version: 30.122012.16093.0)</summary>

&ensp;Udgivet: **9. mar 2022**<br/>
&ensp;Publiceret: **9. marts 2022**<br/>
&ensp;Build: **101.60.93**<br/>
&ensp;Version: **30.122012.16093.0**<br/>

**Nyheder**

- Denne version indeholder en sikkerhedsopdatering til [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/)


<br/><br/>
</details><details>
<summary>Mar-2022 (build: 101.60.05 | Version: 30.122012.16005.0)</summary>

&ensp;Udgivet: **3. mar 2022**<br/>
&ensp;Publiceret: **3. mar. 2022**<br/>
&ensp;Build: **101.60.05**<br/>
&ensp;Version: **30.122012.16005.0**<br/>

**Nyheder**

- Tilføjet understøttelse af kerneversion 2.6.32-754.43.1.el6.x86_64 til RHEL 6.10
- Fejlrettelser


<br/><br/>
</details><details>
<summary>Feb-2022 (build: 101.58.80 | Version: 30.122012.15880.0)</summary>

&ensp;Udgivet: **20. februar 2022**<br/>
&ensp;Publiceret: **20. feb. 2022**<br/>
&ensp;Build: **101.58.80**<br/>
&ensp;Version: **30.122012.15880.0**<br/>

**Nyheder**

- Kommandolinjeværktøjet understøtter nu gendannelse af filer, der er sat i karantæne, på en anden placering end den, hvor filen oprindeligt blev registreret. Dette kan gøres via `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`.
- Fra og med denne version kan netværksbeskyttelse til Linux evalueres efter behov
- Fejlrettelser



<br/><br/>
</details><details>
<summary>Jan-2022 (build: 101.56.62 | Version: 30.121122.15662.0)</summary>

&ensp;Udgivet: **26. januar 2022**<br/>
&ensp;Publiceret: **26. januar 2022**<br/>
&ensp;Build: **101.56.62**<br/>
&ensp;Version: **30.121122.15662.0**<br/>

**Nyheder**

- Løste et produktnedbrud, der blev introduceret i 101.53.02, og som har påvirket flere kunder


<br/><br/>
</details><details>
<summary>Jan-2022 (build: 101.53.02 | Version: (30.121112.15302.0)</summary>

&ensp;Udgivet: **8. januar 2022**<br/>
&ensp;Publiceret: **8. januar 2022**<br/>
&ensp;Build: **101.53.02**<br/>
&ensp;Version: **30.121112.15302.0**<br/>

**Nyheder**

- Forbedringer af ydeevnen & fejlrettelser



</details>

<details><summary> Udgivelser fra 2021</summary><blockquote>
  <details><summary>(Build: 101.52.57 | Version: 30.121092.15257.0)</summary>
   
  <p><b> Build: 101.52.57 <br>
Version: 30.121092.15257.0</b></p>
   
  <p><b> Hvad er nyt </b></p>

   - Tilføjede en funktion til at registrere sårbare log4j-jars, der bruges af Java-programmer. Maskinen undersøges jævnligt for kørsel af Java-processer med indlæste log4j-krukker. Oplysningerne rapporteres til backend-Microsoft Defender for Endpoint og vises i området Administration af sårbarhed på portalen.
   
   </details>

  <details><summary>(Build: 101.47.76 | Version: 30.121092.14776.0)</summary>
   
  <p><b> Build: 101.47.76 <br>
Version: 30.121092.14776.0</b></p>
   
  <p><b>Nyheder</b></p>

   - Tilføjede en ny parameter til kommandolinjeværktøjet for at styre, om arkiver scannes under scanninger efter behov. Dette kan konfigureres via mdatp config scan-archives --value [enabled/disabled]. Som standard er dette angivet til aktiveret.

   - Fejlrettelser

   </details>

   <details><summary>(Build: 101.45.13 | Version: 30.121082.14513.0)</summary>
   
  <p> 
  Build: <b>101.45.13 </b>  <br>
Version:<b> 30.121082.14513.0 </b></p>
   
  <p><b>Nyheder</b></p>

  - Fra og med denne version understøtter vi Microsoft Defender for Endpoint følgende distributioner:

    - RHEL6.7-6.10- og CentOS6.7-6.10-versioner.
    - Amazon Linux 2
    - Fedora 33 eller nyere

  - Fejlrettelser

   </details>


   <details><summary>(Build: 101.45.00 | Version: 30.121072.14500.0)</summary>
   
   <p> 
   Build:<b> 101.45.00</b> <br>
Version: <b>30.121072.14500.0</b></p>
   
   <p><b>Nyheder</b></p>
      

  - Nye parametre er føjet til kommandolinjeværktøjet:
    - Kontrollér graden af parallelitet for on-demand-scanninger. Dette kan konfigureres via `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Der bruges som standard en grad af parallelitet af `2` .
    - Kontrollér, om scanninger efter sikkerhedsintelligensopdateringer er aktiveret eller deaktiveret. Dette kan konfigureres via `mdatp config scan-after-definition-update --value [enabled/disabled]`. Som standard er dette angivet til `enabled`.
  - Ændring af niveauet for produktloggen kræver nu udvidede rettigheder
  - Fejlrettelser

   </details>

   <details><summary>(Build: 101.39.98 | Version: 30.121062.13998.0)</summary>
   
   <p> 
   Build: <b>101.39.98 </b><br>
Version: <b>30.121062.13998.0</b></p>
   
   <p><b>Nyheder</b></p>

  - Forbedringer af ydeevnen & fejlrettelser
  
   </details>

   <details><summary>(Build: 101.34.27 | Version: 30.121052.13427.0)</summary>
   
   <p> 
   Build:<b> 101.34.27</b> <br>
Version: <b>30.121052.13427.0</b></p>
   
   <p><b>Nyheder</b></p>

   - Forbedringer af ydeevnen & fejlrettelser
  
   </details>

   <details><summary>(Build: 101.29.64 | Version: 30.121042.12964.0)</summary>
   
   <p> 
   Build:<b> 101.29.64 </b><br>
Version:<b> 30.121042.12964.0</b></p>
   
   <p><b>Nyheder</b></p>

   - Fra og med denne version afhjælpes trusler, der registreres under on-demand-antivirusscanninger, som udløses via kommandolinjeklienten, automatisk. Trusler, der registreres under scanninger, der udløses via brugergrænsefladen, kræver stadig manuel handling.
   - `mdatp diagnostic real-time-protection-statistics` understøtter nu to ekstra parametre:
     - `--sort`: sorterer outputtet faldende efter det samlede antal scannede filer
     - `--top N`: viser de øverste N-resultater (fungerer kun, hvis `--sort` der også er angivet)
   - Forbedringer af ydeevnen & fejlrettelser
  
   </details>

   <details><summary>(Build: 101.25.72 | Version: 30.121022.12563.0)</summary>
   
   <p> 
   Build:<b> 101.25.72</b> <br>
Version: <b>30.121022.12563.0</b></p>
   
   <p><b>Nyheder</b></p>

   - Microsoft Defender for Endpoint på Linux er nu tilgængelig som prøveversion for us government-kunder. Du kan få flere oplysninger [under Microsoft Defender for Endpoint til US Government-kunder](gov.md).
   - Løste et problem, hvor brugen af Microsoft Defender for Endpoint på Linux på systemer med FUSE-filsystemer førte til, at operativsystemet hænger
   - Forbedringer af ydeevnen & andre fejlrettelser
  
   </details>

   
   <details><summary>(Build: 101.25.63 | Version: 30.121022.12563.0)</summary>
   
   <p> 
   Build:<b> 101.25.63</b> <br>
Version: <b>30.121022.12563.0</b></p>
   
   <p><b>Nyheder</b></p>

   - Forbedringer af ydeevnen & fejlrettelser
  
   </details>

   <details><summary>(Build: 101.23.64 | Version: 30.121021.12364.0)</summary>
   
   <p>
Build:<b> 101.23.64 </b><br>
Version: 30.121021.12364.0</b></p>
   
   <p><b>Nyheder</b></p>

   - Forbedring af ydeevnen i den situation, hvor der føjes et helt tilslutningspunkt til listen over antivirusudeladelser. Før denne version blev filaktivitet, der stammer fra tilslutningspunktet, stadig behandlet af produktet. Fra og med denne version skjules filaktivitet for udeladte tilslutningspunkter, hvilket fører til bedre produktydeevne
   - Der er føjet en ny indstilling til kommandolinjeværktøjet for at få vist oplysninger om den seneste scanning efter behov. Hvis du vil have vist oplysninger om den seneste scanning efter behov, skal du køre `mdatp health --details antivirus`
   - Andre forbedringer af ydeevnen & fejlrettelser
  
   </details>

   <details><summary>(Build: 101.18.53)</summary>
   
    <p> 
    Build:<b> 101.18.53 </b><br>
        
    <p>Nyheder</b></p>

   - EDR til Linux er nu [offentlig tilgængelig](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
   - Tilføjede en ny kommandolinjeparameter (`--ignore-exclusions`) for at ignorere AV-udeladelser under brugerdefinerede scanninger (`mdatp scan custom`)
   - Udvidet `mdatp diagnostic create` med en ny parameter (`--path [directory]`), der gør det muligt at gemme diagnosticeringslogfilerne i en anden mappe
    - Forbedringer af ydeevnen & fejlrettelser
    
   </details>





</blockquote></details>

