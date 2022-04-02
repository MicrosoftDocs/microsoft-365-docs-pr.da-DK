---
title: Installer Microsoft Defender til slutpunkt på Linux manuelt
ms.reviewer: ''
description: Beskriver, hvordan du manuelt installerer Microsoft Defender til slutpunkt på Linux fra kommandolinjen.
keywords: microsoft, defender, Microsoft Defender til Slutpunkt, linux, installation, deploy, uninstallation, defender, ansible, linux, redhat, ubuntu, defender, sles, suse, centos, amazon linux 2
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
ms.openlocfilehash: da05d702a2cb074ece2fec74371e7b5f560cb1ed
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63603097"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Installer Microsoft Defender til slutpunkt på Linux manuelt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


Denne artikel beskriver, hvordan du installerer Microsoft Defender til slutpunkt på Linux manuelt. En vellykket installation kræver, at alle følgende opgaver er gennemført:

  - [Forudsætninger og systemkrav](#prerequisites-and-system-requirements)
  - [Konfigurer Linux-softwarelageret](#configure-the-linux-software-repository)
    - [RHEL og varianter (CentOS, Linux, Oracle Linux og Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES og varianter](#sles-and-variants)
    - [Ubuntu- og Ink- systemer](#ubuntu-and-debian-systems)
  - [Programinstallation](#application-installation)
  - [Download onboardingpakken](#download-the-onboarding-package)
  - [Klientkonfiguration](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, skal du [se Microsoft Defender til slutpunkt på Linux](microsoft-defender-endpoint-linux.md) for at få en beskrivelse af forudsætningerne og systemkravene for den aktuelle softwareversion.

> [!WARNING]
> Opgradering af operativsystemet til en ny, større version efter produktinstallationen kræver, at produktet geninstalleres. Du skal fjerne [den](linux-resources.md#uninstall) eksisterende Defender til slutpunkt på Linux, opgradere operativsystemet og derefter konfigurere Defender til Endpoint på Linux ved at følge nedenstående trin.

## <a name="configure-the-linux-software-repository"></a>Konfigurer Linux-softwarelageret

Defender til slutpunkt på Linux kan installeres fra en af følgende kanaler (angivet nedenfor som *[kanal]*): *Insiders-fast*, *Insiders-slow* eller *prod*. Hver af disse kanaler svarer til et Linux-softwarelager. Instruktioner til konfiguration af din enhed til at bruge et af disse lager er angivet nedenfor.

Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes din enhed. Enheder i *Insiders-fast* er de første, der modtager opdateringer og nye funktioner, efterfulgt senere af *Insiders-slow* og til sidst *af professionelle*.

For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten *Insiders-fast* eller *Insiders-slow*.

> [!WARNING]
> Hvis du skifter kanal efter den indledende installation, skal produktet geninstalleres. Sådan skifter du produktkanalen: Fjern den eksisterende pakke, konfigurer enheden igen til at bruge den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL og varianter (CentOS, Linux, Oracle Linux og Amazon Linux 2)

- Installér `yum-utils` , hvis den endnu ikke er installeret:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > Din fordeling og version samt identificere den nærmeste post (efter hovedpost, derefter underordnet) for den under `https://packages.microsoft.com/config/rhel/`.

    Brug følgende tabel som hjælp til at finde pakken:

    <br>

    ****

    |Distributionsversion & version|Pakke|
    |---|---|
    |For RHEL/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |Til RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |<https://packages.microsoft.com/config/rhel/7/[channel].repo>|
    |For RHEL/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|
    |Til den 33. Ane|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Til Den 34- eller anden 34-2016|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    I de følgende kommandoer skal du erstatte *[version]* og *[kanal]* med de oplysninger, du har identificeret:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > Brug kommandoen hostnamectl til at identificere systemrelaterede oplysninger, herunder version *[version]*.

    Hvis du f.eks. kører CentOS 7 og vil installere Defender til Slutpunkt på Linux fra *den professionelle* kanal:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Eller hvis du vil udforske nye funktioner på udvalgte enheder, kan det være en ide at installere Microsoft Defender til Slutpunkt på Linux *til insiders-fast-kanalen* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Installér den offentlige Microsoft GPG-nøgle:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES og varianter

> [!NOTE]
> Din fordeling og version samt identificere den nærmeste post (efter hovedpost, derefter underordnet) for den under `https://packages.microsoft.com/config/sles/`.

   I de følgende kommandoer skal du erstatte *[distro]* *og [version]* med de oplysninger, du har identificeret:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Brug kommandoen SPident til at identificere systemrelaterede oplysninger, herunder udgivelse *[version]*.

   Hvis du f.eks. kører SLES 12 og ønsker at installere Microsoft Defender til Slutpunkt på Linux fra *den professionelle* kanal:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Installér den offentlige Microsoft GPG-nøgle:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Ubuntu- og Ink- systemer

- Installér `curl` , hvis den endnu ikke er installeret:

    ```bash
    sudo apt-get install curl
    ```

- Installér `libplist-utils` , hvis den endnu ikke er installeret:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> Din fordeling og version samt identificere den nærmeste post (efter hovedpost, derefter underordnet) for den under `https://packages.microsoft.com/config/[distro]/`.

   I kommandoen nedenfor skal du *erstatte [distro]* *og [version]* med de oplysninger, du har identificeret:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > Brug kommandoen hostnamectl til at identificere systemrelaterede oplysninger, herunder version *[version]*.

   Hvis du f.eks. kører Ubuntu 18.04 og ønsker at installere Microsoft Defender til Slutpunkt på Linux fra *prod-kanalen* :

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Installer lagerkonfigurationen:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Hvis du f.eks. har *valgt professionel* kanal:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- Installer pakken `gpg` , hvis den ikke allerede er installeret:

    ```bash
    sudo apt-get install gpg
    ```

  Hvis det `gpg` ikke er tilgængeligt, skal du installere `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- Installér den offentlige Microsoft GPG-nøgle:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- Installér https-driveren, hvis den ikke allerede findes:

    ```bash
    sudo apt-get install apt-transport-https
    ```

- Opdater metadataene for lageret:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Programinstallation

- RHEL og varianter (CentOS og Oracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > Hvis du har flere Microsoft-lagre konfigureret på din enhed, kan du være specifik for, hvilket lager pakken skal installeres fra. Følgende eksempel viser, hvordan du installerer pakken fra kanalen `production` , hvis du også har `insiders-fast` konfigureret lagerkanalen på denne enhed. Denne situation kan opstå, hvis du bruger flere Microsoft-produkter på din enhed. Afhængigt af fordelingen og versionen af din server kan aliasset for lageret være anderledes end i følgende eksempel.

    ```bash
    # list all repositories
    yum repolist
    ```

    ```Output
    ...
    packages-microsoft-com-prod               packages-microsoft-com-prod        316
    packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
    ...
    ```

    ```bash
    # install the package from the production repository
    sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
    ```

- SLES og varianter:

    ```bash
    sudo zypper install mdatp
    ```

    > [!NOTE]
    > Hvis du har flere Microsoft-lagre konfigureret på din enhed, kan du være specifik for, hvilket lager pakken skal installeres fra. Følgende eksempel viser, hvordan du installerer pakken fra kanalen `production` , hvis du også har `insiders-fast` konfigureret lagerkanalen på denne enhed. Denne situation kan opstå, hvis du bruger flere Microsoft-produkter på din enhed.

    ```bash
    zypper repos
    ```

    ```Output
    ...
    #  | Alias | Name | ...
    XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
    XX | packages-microsoft-com-prod | microsoft-prod | ...
    ...

    ```

    ```bash
    sudo zypper install packages-microsoft-com-prod:mdatp
    ```

- System med Ubuntu og Ubuntu og 2016:

    ```bash
    sudo apt-get install mdatp
    ```

    > [!NOTE]
    > Hvis du har flere Microsoft-lagre konfigureret på din enhed, kan du være specifik for, hvilket lager pakken skal installeres fra. Følgende eksempel viser, hvordan du installerer pakken fra kanalen `production` , hvis du også har `insiders-fast` konfigureret lagerkanalen på denne enhed. Denne situation kan opstå, hvis du bruger flere Microsoft-produkter på din enhed.

    ```bash
    cat /etc/apt/sources.list.d/*
    ```

    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod bionic main
    ```

    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a>Download onboardingpakken

Download onboardingpakken fra Microsoft 365 Defender portal.

> [!IMPORTANT]
> Hvis du ikke udfører dette trin, vises der en advarselsmeddelelse om, at produktet ikke har licens. Kommandoen returnerer `mdatp health` også en værdi på `false`.

1. I Microsoft 365 Defender skal du gå **til Indstillinger > slutpunkter > administration af > onboarding**.
2. I den første rullemenu skal du vælge **Linux Server** som operativsystem. I den anden rullemenu skal du vælge **Lokalt script som** installationsmetode.
3. Vælg **Download onboarding pakke**. Gem filen som WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft 365 Defender portalskærm.](images/portal-onboarding-linux.png)

4. I en kommandoprompt skal du bekræfte, at du har filen og udtrække indholdet af arkivet:

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

## <a name="client-configuration"></a>Klientkonfiguration

1. Kopiér MicrosoftDefenderATPOnboardingLinuxServer.py til destinationsenheden.

    > [!NOTE]
    > Til at starte med er klientenheden ikke knyttet til en organisation, og *orgId-attributten* er tom.

    ```bash
    mdatp health --field org_id
    ```

2. Kør MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > For at køre denne kommando skal du have eller `python` `python3` installeret på enheden afhængigt af disto og version. Hvis det er nødvendigt, [skal du se Trinvis instruktion til installation af Python på Linux](https://opensource.com/article/20/4/install-python-linux).
    
    Hvis du kører RHEL 8.x eller Ubuntu 20.04 eller nyere, skal du bruge `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    For resten af distributioner og versioner skal du bruge `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. Kontrollér, at enheden nu er knyttet til organisationen, og rapporterer et gyldigt organisations-id:

    ```bash
    mdatp health --field org_id
    ```

4. Kontrollér produktets tilstand ved at køre følgende kommando. En returværdi for `1` denoter, der angiver, at produktet fungerer som forventet:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Når produktet starter for første gang, downloader det de seneste antimalwaredefinitioner. Dette kan tage op til et par minutter, afhængigt af netværksforbindelsen. I dette tidsrum returnerer kommandoen ovenfor en værdi på `false`. Du kan kontrollere status for definitionsopdateringen ved hjælp af følgende kommando:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > Bemærk, at du muligvis også skal konfigurere en proxy, når den første installation er fuldført. Se [Konfigurer Defender til slutpunkt på Linux for statisk proxyregistrering: Konfiguration efter installation](linux-static-proxy-configuration.md#post-installation-configuration).

5. Kør en test til registrering af lyd/lyd for at bekræfte, at enheden er korrekt onboardet og rapporterer til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

    - Sørg for, at beskyttelse i realtid er aktiveret (angivet af et resultat af at `1` køre følgende kommando):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      Hvis den ikke er aktiveret, skal du udføre følgende kommando:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Åbn et Terminal-vindue, og udfør følgende kommando:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Filen skulle være sat i karantæne af Defender for Endpoint på Linux. Brug følgende kommando til at få vist en liste over alle registrerede trusler:

        ```bash
        mdatp threat list
        ```

6. Kør en Slutpunktsregistrering og -svar registreringstest, og simulere en registrering for at bekræfte, at enheden er korrekt onboardet og rapporterer til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

    - Kontrollér, at den onboardede Linux-server vises i Microsoft 365 Defender. Hvis dette er den første onboarding af computeren, kan det tage op til 20 minutter, før den vises.

    - Download og udtræk [scriptfilen](https://aka.ms/LinuxDIY) til en onboarded Linux-server, og kør følgende kommando: `./mde_linux_edr_diy.sh`

    - Efter et par minutter skal en registrering være hævet i Microsoft 365 Defender.

    - Kig på detaljerne, tidslinjen på computeren, og udfør dine typiske undersøgelsestrin.

## <a name="installer-script"></a>Installer script

Alternativt kan du bruge et automatiseret [installerings-bash-script](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh), der [leveres i vores offentlige GitHub-lager](https://github.com/microsoft/mdatp-xplat/).
Scriptet identificerer distributionen og versionen, forenkler valget af det rigtige lager, konfigurerer enheden til at trække den nyeste pakke og kombinerer produktinstallations- og onboardingtrinnene.

```bash
❯ ./mde_installer.sh --help
usage: basename ./mde_installer.sh [OPTIONS]
Options:
-c|--channel      specify the channel from which you want to install. Default: insiders-fast
-i|--install      install the product
-r|--remove       remove the product
-u|--upgrade      upgrade the existing product
-o|--onboard      onboard/offboard the product with <onboarding_script>
-p|--passive-mode set EPP to passive mode
-t|--tag          set a tag by declaring <name> and <value>. ex: -t GROUP Coders
-m|--min_req      enforce minimum requirements
-w|--clean        remove repo from package manager for a specific channel
-v|--version      print out script version
-h|--help         display help
```

Læs mere [her](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>Problemer med installation af logfil

Se [Problemer med installation af logfiler](linux-resources.md#log-installation-issues) for at få flere oplysninger om, hvordan du finder den automatisk oprettede log, der oprettes af installationsprogrammet, når der opstår en fejl.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Sådan overføres fra Insiders-Fast til produktionskanalen

1. Fjern "Insiders-Fast-kanal"-versionen af Defender til Slutpunkt på Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. Deaktiver Defender for Endpoint på Linux Insiders-Fast repo

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > Outputtet skal vise "packages-microsoft-com-fast-prod".

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. Reploy Microsoft Defender for Endpoint på Linux ved hjælp af "Production channel".

## <a name="uninstallation"></a>Fjernelse af installation

Se [Fjern](linux-resources.md#uninstall) for at få mere at vide om, hvordan du fjerner Defender for Endpoint på Linux fra klientenheder.

## <a name="see-also"></a>Se også

- [Undersøg agentens tilstandsproblemer](health-status.md)
