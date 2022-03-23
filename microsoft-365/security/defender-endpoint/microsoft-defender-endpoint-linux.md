---
title: Microsoft Defender til slutpunkt på Linux
ms.reviewer: ''
description: Beskrivelse af, hvordan du installerer og bruger Microsoft Defender til slutpunkt på Linux.
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ebcfea808e64c89772f36fb22f5dfd75e6e8e27f
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63592715"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I dette emne beskrives det, hvordan du installerer, konfigurerer, opdaterer og bruger Microsoft Defender til slutpunkt på Linux.

> [!CAUTION]
> Hvis du kører andre slutpunktsbeskyttelsesprodukter fra tredjepart sammen med Microsoft Defender til slutpunkt på Linux, vil det sandsynligvis føre til problemer med ydeevnen og uforudsete bivirkninger. Hvis ikke-Microsoft-slutpunktsbeskyttelse er et absolut krav i dit miljø, kan du stadig roligt drage fordel af Defender til slutpunkt på Linux Slutpunktsregistrering og -svar-funktionalitet, når du har konfigureret antivirusfunktionaliteten til at køre i [passiv tilstand](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Sådan installerer du Microsoft Defender til slutpunkt på Linux

### <a name="prerequisites"></a>Forudsætninger

- Adgang til Microsoft 365 Defender portalen
- Linux-distribution ved hjælp [af Systemd](https://systemd.io/) System Manager
- Begynderoplevelse i Linux- og BASH-scripting
- Administrative rettigheder på enheden (i tilfælde af manuel udrulning)

> [!NOTE]
> Microsoft Defender til slutpunkt på Linux-agent er uafhængig af [OMS-agent.](/azure/azure-monitor/agents/agents-overview#log-analytics-agent) Microsoft Defender til slutpunkt afhænger af sin egen uafhængige telemetripipeline.


### <a name="installation-instructions"></a>Installationsvejledning

Der er flere metoder og installationsværktøjer, du kan bruge til at installere og konfigurere Microsoft Defender til slutpunkt på Linux.

Generelt skal du gøre følgende:

- Sørg for, at du har et abonnement på Microsoft Defender til slutpunkt.
- Installér Microsoft Defender til Slutpunkt på Linux ved hjælp af en af følgende installationsmetoder:
  - Kommandolinjeværktøjet:
    - [Manuel udrulning](linux-install-manually.md)
  - Administrationsværktøjer fra tredjepart:
    - [Installér ved hjælp af Konfigurationsstyringsværktøj til softwarekonfiguration](linux-install-with-puppet.md)
    - [Installér ved hjælp af værktøjet Ansible Configuration Management](linux-install-with-ansible.md)
    - [Installér ved hjælp af konfigurationsstyringsværktøjet Chef](linux-deploy-defender-for-endpoint-with-chef.md)

Hvis du oplever installationsfejl, kan du se [Fejlfinding i forbindelse med installationsfejl i Microsoft Defender til slutpunkt på Linux](linux-support-install.md).

> [!NOTE]
> Det understøttes ikke at installere Microsoft Defender til slutpunkt på andre placeringer end standardinstallationsstien. 

### <a name="system-requirements"></a>Systemkrav

- Understøttede Linux-serverdistributioner og x64-versioner (AMD64/EM64T):

  - Red Hat Enterprise Linux 6.7 eller nyere
  - Red Hat Enterprise Linux 7.2 eller nyere
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 eller nyere 
  - CentOS 7.2 eller nyere
  - Ubuntu 16.04 LTS eller nyere LTS
  - 9 eller nyere
  - SUSE Linux Enterprise Server 12 eller nyere
  - Oracle Linux 7.2 eller nyere
  - Oracle Linux 8.x
  - Amazon Linux 2
  - 33 eller nyere

    > [!NOTE]
    > Fordelinger og versioner, der ikke eksplicit er angivet, understøttes ikke (også selvom de officielt er afledt af de officielt understøttede fordelinger).

- Liste over understøttede kerneversioner
  - Red Hat Enterprise Linux 6 og CentOS 6:
    - Til 6.7: 2.6.32-573.*
    - For 6.8: 2.6.32-642.*
    - For 6.9: 2.6.32-696.*
    - For 6.10: 2.6.32.754.2.1.el6.x86_64 til 2.6.32-754.41.2:
    
       - 2.6.32-754.10.1.el6.x86_64
       - 2.6.32-754.11.1.el6.x86_64
       - 2.6.32-754.12.1.el6.x86_64
       - 2.6.32-754.14.2.el6.x86_64
       - 2.6.32-754.15.3.el6.x86_64
       - 2.6.32-754.17.1.el6.x86_64
       - 2.6.32-754.18.2.el6.x86_64
       - 2.6.32-754.2.1.el6.x86_64
       - 2.6.32-754.22.1.el6.x86_64
       - 2.6.32-754.23.1.el6.x86_64
       - 2.6.32-754.24.2.el6.x86_64
       - 2.6.32-754.24.3.el6.x86_64
       - 2.6.32-754.25.1.el6.x86_64
       - 2.6.32-754.27.1.el6.x86_64
       - 2.6.32-754.28.1.el6.x86_64
       - 2.6.32-754.29.1.el6.x86_64
       - 2.6.32-754.29.2.el6.x86_64
       - 2.6.32-754.3.5.el6.x86_64
       - 2.6.32-754.30.2.el6.x86_64
       - 2.6.32-754.33.1.el6.x86_64
       - 2.6.32-754.35.1.el6.x86_64
       - 2.6.32-754.39.1.el6.x86_64
       - 2.6.32-754.41.2.el6.x86_64
       - 2.6.32-754.43.1.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64


    > [!NOTE]
    > Når en ny pakkeversion udgives, reduceres support til de to tidligere versioner kun til teknisk support. Versioner, der er ældre end dem, der er angivet i dette afsnit, er kun med til teknisk opgraderingssupport.

  - For resten af de understøttede fordelinger er minimumversionen af kerne påkrævet 3.10.0-327

- Begivenhedsudbydermekanismen
  - Red Hat Enterprise Linux 6 og CentOS 6: `Talpa` kernemodulbaseret løsning
  - For resten af de understøttede fordelinger: `Fanotify`
    - Indstillingen `fanotify` Kerne skal være aktiveret

      > [!CAUTION]
      > Kørsel af Defender til slutpunkt på Linux side om side med andre `fanotify`-baserede sikkerhedsløsninger understøttes ikke. Det kan føre til uforudsigelige resultater, herunder at operativsystemet hænger.

- Diskplads: 1 GB

- /opt/microsoft/mdatp/sbin/wdavdaemon kræver eksekverbar tilladelse. Få mere at vide under "Sørg for, at daemon har eksekverbar tilladelse" i Fejlfinding af [installationsproblemer med Microsoft Defender til Slutpunkt på Linux](/microsoft-365/security/defender-endpoint/linux-support-install).

- Kerner: 2 minimum, 4 foretrukken

- Hukommelse: minimum 1 GB, 4 foretrukket

    > [!NOTE]
    > Sørg for, at du har ledig diskplads i /var.

- Løsningen giver i øjeblikket beskyttelse i realtid til følgende filtyper:

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

Når du har aktiveret tjenesten, skal du muligvis konfigurere dit netværk eller din firewall til at tillade udgående forbindelser mellem den og dine slutpunkter.

- Overvågningsstruktur (`auditd`) skal være aktiveret.

  > [!NOTE]
  > Systemhændelser registreret af regler, der `/etc/audit/rules.d/` føjes til `audit.log`, føjes til (e) og kan påvirke værtsrevision og upstream-samling. Begivenheder, der tilføjes af Microsoft Defender for Slutpunkt på Linux, mærkes med `mdatp` nøgle.

### <a name="configuring-exclusions"></a>Konfiguration af udeladelse

Når du føjer udeladelse Microsoft Defender Antivirus, skal du være opmærksom [på almindelige udeladelsesfejl for Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Netværksforbindelser

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Du skal sikre dig, at der ikke er nogen firewall eller regler for netværksfiltrering, der vil nægte adgang til disse URL-adresser. Hvis der er, skal du muligvis oprette en *tilladelsesregel* specifikt for dem.

<br>

****


|Listen Regneark over domæner| Beskrivelse|
|---|---|
|URL-adresseliste for Microsoft Defender til slutpunkt for kommercielle kunder | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og operativsystem for kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| URL-adresseliste for Microsoft Defender til slutpunkt for Gov/GCC/DoD-kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|


> [!NOTE]
> Hvis du vil have en mere specifik URL-liste, skal [du se Konfigurer indstillinger for proxy og forbindelse til internettet](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Defender til Slutpunkt kan finde en proxyserver ved hjælp af følgende registreringsmetoder:

- Gennemsigtig proxy
- Manuel statisk proxykonfiguration

Hvis en proxy eller firewall blokerer anonym trafik, skal du sørge for, at anonym trafik er tilladt i de tidligere angivne URL-adresser. For gennemsigtige proxyer kræves der ingen yderligere konfiguration for Defender til slutpunkt. For statisk proxy skal du følge trinnene i [Manuel konfiguration af statisk proxy](linux-static-proxy-configuration.md).

> [!WARNING]
> PAC, WPAD og godkendte proxyer understøttes ikke. Sørg for, at der kun bruges en statisk proxy eller gennemsigtig proxy.
>
> SSL-inspektion og skærings-proxyer understøttes heller ikke af sikkerhedsmæssige årsager. Konfigurer en undtagelse for SSL-inspektion og din proxyserver til at gå direkte gennem data fra Defender til Slutpunkt på Linux til de relevante URL-adresser uden skæring. Tilføjelse af dit skæringscertifikat til det globale lager tillader ikke skæring.

Du kan finde fejlfindingstrin [under Fejlfinding af forbindelsesproblemer i skyen for Microsoft Defender til Slutpunkt på Linux](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Sådan opdaterer du Microsoft Defender til slutpunkt på Linux

Microsoft udgiver jævnligt softwareopdateringer for at forbedre ydeevnen, sikkerheden og levere nye funktioner. Hvis du vil opdatere Microsoft Defender til slutpunkt på Linux, skal du [se Installér opdateringer til Microsoft Defender til slutpunkt på Linux](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Sådan konfigurerer du Microsoft Defender til slutpunkt på Linux

Vejledning til, hvordan du konfigurerer produktet i virksomhedsmiljøer, findes [i Angiv indstillinger for Microsoft Defender til Slutpunkt på Linux](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Almindelige programmer til Microsoft Defender til slutpunkt kan påvirke

Store I/O-arbejdsbelastninger fra visse programmer kan opleve problemer med ydeevnen, når Microsoft Defender til slutpunkt er installeret. Disse omfatter programmer til udviklerscenarier som Jenkins og Jira og databasearbejdsbelastninger som OracleDB og Postgres. Hvis du oplever forringet ydeevne, kan du overveje at angive udeladelse for pålidelige programmer og holde almindelige [udeladelsesfejl Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) for øje. Du kan få yderligere vejledning ved at overveje rådgivning om antivirusfratagelser fra tredjepartsprogrammer.

## <a name="resources"></a>Ressourcer

- Du kan finde flere oplysninger om logføring, fjernelse eller andre emner under [Ressourcer](linux-resources.md).
