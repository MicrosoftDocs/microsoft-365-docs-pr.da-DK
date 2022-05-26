---
title: Microsoft Defender for Endpoint på Linux
ms.reviewer: ''
description: Beskriver, hvordan du installerer og bruger Microsoft Defender for Endpoint på Linux.
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e5f60e37765e562f0c1508778182f1f506773bff
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679236"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender for Endpoint på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I dette emne beskrives det, hvordan du installerer, konfigurerer, opdaterer og bruger Microsoft Defender for Endpoint på Linux.

> [!CAUTION]
> Kørsel af andre tredjepartsbeskyttelsesprodukter til slutpunkter sammen med Microsoft Defender for Endpoint på Linux vil sandsynligvis medføre problemer med ydeevnen og uforudsigelige bivirkninger. Hvis beskyttelse af slutpunkter, der ikke er fra Microsoft, er et absolut krav i dit miljø, kan du stadig trygt drage fordel af Defender for Endpoint på Linux-Slutpunktsregistrering og -svar funktionalitet, når du har konfigureret antivirusfunktionen til at køre i [passiv tilstand](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Sådan installerer du Microsoft Defender for Endpoint på Linux

Microsoft Defender for Endpoint til Linux indeholder funktioner til antimalware og slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar). 


### <a name="prerequisites"></a>Forudsætninger

- Adgang til Microsoft 365 Defender-portalen
- Linux-distribution ved hjælp af [systemadministratoren](https://systemd.io/)

  >[!NOTE]
  >Linux-distribution ved hjælp af systemadministrator med undtagelse af RHEL/CentOS 6.x understøtter både SystemV og Upstart.

- Erfaring med Linux- og BASH-scripting på begynderniveau
- Administrative rettigheder på enheden (i tilfælde af manuel installation)

> [!NOTE]
> Microsoft Defender for Endpoint på Linux-agenten er uafhængig af [OMS-agenten](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). Microsoft Defender for Endpoint er afhængig af sin egen uafhængige telemetripipeline.


### <a name="installation-instructions"></a>Installationsvejledning

Der er flere metoder og installationsværktøjer, som du kan bruge til at installere og konfigurere Microsoft Defender for Endpoint på Linux.

Generelt skal du gøre følgende:

- Sørg for, at du har et Microsoft Defender for Endpoint abonnement.
- Udrul Microsoft Defender for Endpoint på Linux ved hjælp af en af følgende udrulningsmetoder:
  - Kommandolinjeværktøjet:
    - [Manuel udrulning](linux-install-manually.md)
  - Administrationsværktøjer fra tredjepart:
    - [Udrul ved hjælp af Værktøjet til administration af konfiguration af dukke](linux-install-with-puppet.md)
    - [Udrul ved hjælp af Værktøjet til administration af konfiguration, der kan bruges](linux-install-with-ansible.md)
    - [Udrul ved hjælp af Chef Configuration Management Tool](linux-deploy-defender-for-endpoint-with-chef.md)

Hvis du oplever installationsfejl, kan du se [Fejlfinding af installationsfejl i Microsoft Defender for Endpoint på Linux](linux-support-install.md).

> [!NOTE]
> Det understøttes ikke at installere Microsoft Defender for Endpoint på andre placeringer end standardinstallationsstien. 

### <a name="system-requirements"></a>Systemkrav

- Understøttede Linux-serverdistributioner og x64-versioner (AMD64/EM64T) og x86_64 versioner:

  - Red Hat Enterprise Linux 6.7 eller nyere (prøveversion)
  - Red Hat Enterprise Linux 7.2 eller nyere 
  - Red Hat Enterprise Linux 8.x 
  - CentOS 6,7 eller nyere 
  - CentOS 7,2 eller nyere
  - Ubuntu 16.04 LTS eller højere LTS
  - Debian 9 eller nyere
  - SUSE Linux Enterprise Server 12 eller nyere
  - Oracle Linux 7.2 eller nyere
  - Oracle Linux 8.x
  - Amazon Linux 2
  - Fedora 33 eller nyere

    > [!NOTE]
    > Distributioner og versioner, der ikke udtrykkeligt er angivet, understøttes ikke (også selvom de er afledt af de officielt understøttede distributioner).




- Liste over understøttede kerneversioner
  - Minimumkerneversion 3.10.0-327 (for alle de understøttede Linux-distributioner, der er nævnt ovenfor undtagen Red Hat Enterprise Linux 6 og CentOS 6)
  - Kerneindstillingen `fanotify` skal være aktiveret
  - Red Hat Enterprise Linux 6 og CentOS 6:
    - For 6.7: 2.6.32-573.*
    - For 6.8: 2.6.32-642.*
    - For 6.9: 2.6.32-696.* (undtagen 2.6.32-696.el6.x86_64)
    - For 6.10: 2.6.32.754.2.1.el6.x86_64 til 2.6.32-754.43.1:
    
       - 2.6.32-754.10.1.el6.x86_64
       - 2.6.32-754.11.1.el6.x86_64
       - 2.6.32 754.12.1.el6.x86_64
       - 2.6.32-754.14.2.el6.x86_64
       - 2.6.32 754.15.3.el6.x86_64
       - 2.6.32 754.17.1.el6.x86_64
       - 2.6.32-754.18.2.el6.x86_64
       - 2.6.32 754.2.1.el6.x86_64
       - 2.6.32-754.22.1.el6.x86_64
       - 2.6.32-754.23.1.el6.x86_64
       - 2.6.32-754.24.2.el6.x86_64
       - 2.6.32 754.24.3.el6.x86_64
       - 2.6.32-754.25.1.el6.x86_64
       - 2.6.32-754.27.1.el6.x86_64
       - 2.6.32 754.28.1.el6.x86_64
       - 2.6.32 754.29.1.el6.x86_64
       - 2.6.32 754.29.2.el6.x86_64
       - 2.6.32-754.3.5.el6.x86_64
       - 2.6.32 754.30.2.el6.x86_64
       - 2.6.32-754.33.1.el6.x86_64
       - 2.6.32-754.35.1.el6.x86_64
       - 2.6.32 754.39.1.el6.x86_64
       - 2.6.32 754.41.2.el6.x86_64
       - 2.6.32-754.43.1.el6.x86_64
       - 2.6.32-754.47.1.el6.x86_64
       - 2.6.32 754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64

 > [!NOTE]
 > Når en ny pakkeversion er udgivet, reduceres understøttelsen af de to tidligere versioner til kun teknisk support. Versioner, der er ældre end dem, der er angivet i dette afsnit, er kun beregnet til teknisk opgraderingssupport.


  > [!CAUTION]
  > Kørsel af Defender for Endpoint på Linux side om side med andre `fanotify`-baserede sikkerhedsløsninger understøttes ikke. Det kan føre til uforudsigelige resultater, herunder hængende operativsystemet.

- Diskplads: 1 GB

- /opt/microsoft/mdatp/sbin/wdavdaemon kræver eksekverbar tilladelse. Du kan finde flere oplysninger under "Kontrollér, at daemon har eksekverbar tilladelse" i [Fejlfinding af installationsproblemer for Microsoft Defender for Endpoint på Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- Kerner: 2 minimum, 4 foretrækkes

- Hukommelse: minimum 1 GB, 4 foretrækkes

    > [!NOTE]
    > Sørg for, at der er ledig diskplads i /var.

- Løsningen giver i øjeblikket beskyttelse i realtid for følgende filtyper:

  - `btrfs`
  - `ecryptfs`
  - `ext2`
  - `ext3`
  - `ext4`
  - `fuse`
  - `fuseblk`
  - `jfs`
  - `nfs`
  - `overlay`
  - `ramfs`
  - `reiserfs`
  - `tmpfs`
  - `udf`
  - `vfat`
  - `xfs`

Når du har aktiveret tjenesten, skal du muligvis konfigurere netværket eller firewallen for at tillade udgående forbindelser mellem den og dine slutpunkter.

- Overvågningsstrukturen (`auditd`) skal aktiveres.

  > [!NOTE]
  > Systemhændelser, der registreres af regler, der føjes til `/etc/audit/rules.d/` , føjes til `audit.log`(s) og kan påvirke værtsovervågning og upstream-samling. Hændelser, der tilføjes af Microsoft Defender for Endpoint på Linux, mærkes med `mdatp` nøglen.

### <a name="configuring-exclusions"></a>Konfiguration af udeladelser

Når du føjer udeladelser til Microsoft Defender Antivirus, skal du være opmærksom på [almindelige udeladelsesfejl for Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Netværksforbindelser

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Du skal sikre, at der ikke er nogen regler for firewall- eller netværksfiltrering, der vil nægte adgang til disse URL-adresser. Hvis der er, skal du muligvis oprette en *tilladelsesregel* specifikt for dem.

<br>

****

|Regneark med domæneliste| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresseliste til kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OPERATIVSYSTEM til kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

> [!NOTE]
> Du kan se en mere specifik URL-liste under [Konfigurer indstillinger for proxy- og internetforbindelse](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Defender for Endpoint kan finde en proxyserver ved hjælp af følgende registreringsmetoder:

- Gennemsigtig proxy
- Manuel konfiguration af statisk proxy

Hvis en proxy eller firewall blokerer anonym trafik, skal du sørge for, at anonym trafik er tilladt i de tidligere angivne URL-adresser. For gennemsigtige proxyer er der ikke behov for yderligere konfiguration for Defender for Endpoint. I forbindelse med statisk proxy skal du følge trinnene i [Manuel konfiguration af statisk proxy](linux-static-proxy-configuration.md).

> [!WARNING]
> PAC, WPAD og godkendte proxyer understøttes ikke. Sørg for, at der kun bruges en statisk proxy eller gennemsigtig proxy.
>
> SSL-inspektion og opfangelse af proxyer understøttes heller ikke af sikkerhedsmæssige årsager. Konfigurer en undtagelse for SSL-inspektion og din proxyserver til at overføre data direkte fra Defender for Endpoint på Linux til de relevante URL-adresser uden opfangelse. Tilføjelse af dit aflytningscertifikat til det globale lager tillader ikke opfangelse.

Du kan finde fejlfindingstrin under [Fejlfinding af problemer med cloudforbindelsen for Microsoft Defender for Endpoint på Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Sådan opdaterer du Microsoft Defender for Endpoint på Linux

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner. Hvis du vil opdatere Microsoft Defender for Endpoint på Linux, skal du se [Installér opdateringer til Microsoft Defender for Endpoint på Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Sådan konfigurerer du Microsoft Defender for Endpoint på Linux

Vejledning til, hvordan du konfigurerer produktet i virksomhedsmiljøer, er tilgængelig under [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Almindelige programmer til Microsoft Defender for Endpoint kan påvirke

Høje I/O-arbejdsbelastninger fra visse programmer kan opleve problemer med ydeevnen, når Microsoft Defender for Endpoint installeres. Disse omfatter programmer til udviklerscenarier, f.eks. Jenkins og Jira, og databasearbejdsbelastninger som OracleDB og Postgres. Hvis der er en forringelse af ydeevnen, kan du overveje at angive undtagelser for programmer, der er tillid til, og holde øje med [Almindelige udeladelsesfejl for Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus). Hvis du vil have yderligere vejledning, kan du overveje at konsultere dokumentation vedrørende antivirusudeladelser fra tredjepartsprogrammer.

## <a name="resources"></a>Ressourcer

- Du kan få flere oplysninger om logføring, fjernelse eller andre emner under [Ressourcer](linux-resources.md).
  
## <a name="related-articles"></a>Relaterede artikler
  
-  [Beskyt dine slutpunkter med Defender for Clouds integrerede Slutpunktsregistrering og -svar løsning: Microsoft Defender for Endpoint](/azure/defender-for-cloud/integration-defender-for-endpoint)
-  [Forbind dine ikke-Azure-maskiner til Microsoft Defender for Cloud](/azure/defender-for-cloud/quickstart-onboard-machines)

