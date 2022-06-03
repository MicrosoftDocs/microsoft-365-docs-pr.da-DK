---
title: Udrul Microsoft Defender for Endpoint på Linux manuelt
ms.reviewer: ''
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på Linux manuelt fra kommandolinjen.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, deploy, uninstallation, dukke, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
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
ms.openlocfilehash: a9d16cb82354bcb44e817de3207cb49de66dbf91
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873044"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Udrul Microsoft Defender for Endpoint på Linux manuelt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


I denne artikel beskrives det, hvordan du installerer Microsoft Defender for Endpoint på Linux manuelt. En vellykket installation kræver fuldførelse af alle følgende opgaver:

  - [Forudsætninger og systemkrav](#prerequisites-and-system-requirements)
  - [Konfigurer Linux-softwarelageret](#configure-the-linux-software-repository)
    - [RHEL og varianter (CentOS, Fedora, Oracle Linux og Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES og varianter](#sles-and-variants)
    - [Ubuntu- og Debian-systemer](#ubuntu-and-debian-systems)
  - [Programinstallation](#application-installation)
  - [Download onboardingpakken](#download-the-onboarding-package)
  - [Klientkonfiguration](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, skal du se [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md) for at få en beskrivelse af forudsætninger og systemkrav til den aktuelle softwareversion.

> [!WARNING]
> Opgradering af operativsystemet til en ny overordnet version, efter at produktinstallationen kræver, at produktet geninstalleres. Du skal [fjerne](linux-resources.md#uninstall) det eksisterende Defender for Endpoint på Linux, opgradere operativsystemet og derefter omkonfigurere Defender for Endpoint på Linux ved at følge nedenstående trin.

## <a name="configure-the-linux-software-repository"></a>Konfigurer Linux-softwarelageret

Defender for Endpoint på Linux kan udrulles fra en af følgende kanaler (angivet nedenfor som *[channel]*): *insiders-fast*, *insiders-slow* eller *prod*. Hver af disse kanaler svarer til et Linux-softwarelager. Du kan finde en vejledning i, hvordan du konfigurerer enheden til at bruge et af disse lagre, nedenfor.

Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes til din enhed. Enheder i *insiders-fast* er de første til at modtage opdateringer og nye funktioner, efterfulgt senere af *insiders-langsom* og til sidst af *prod*.

For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten *insiders-fast* eller *insiders-slow*.

> [!WARNING]
> Hvis du skifter kanal efter den første installation, skal produktet geninstalleres. Hvis du vil skifte produktkanal: Fjern den eksisterende pakke, genkonfigurer enheden, så den bruger den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL og varianter (CentOS, Fedora, Oracle Linux og Amazon Linux 2)

- Installér `yum-utils` , hvis den ikke er installeret endnu:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > Din distribution og version, og identificer den nærmeste post (efter overordnet og derefter underordnet) for den under `https://packages.microsoft.com/config/rhel/`.

    Brug følgende tabel til at hjælpe dig med at finde pakken:

    <br>

    ****

    |Distro & version|Pakke|
    |---|---|
    |Til RHEL/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |For RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |</azure/cognitive-services/speech-service/how-to-configure-rhel-centos-7>|
    <!--|For RHEL/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|-->
    |Til Fedora 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Til Fedora 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    I følgende kommandoer skal du erstatte *[version]* og *[channel]* med de oplysninger, du har identificeret:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > Brug kommandoen hostnamectl til at identificere systemrelaterede oplysninger, herunder version *[version]*.

    Hvis du f.eks. kører CentOS 7 og vil installere Defender for Endpoint på Linux fra *produktionskanalen* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Eller hvis du vil udforske nye funktioner på udvalgte enheder, kan det være en god idé at udrulle Microsoft Defender for Endpoint på Linux til *en kanal*, der er hurtig for insidere:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Installér den offentlige nøgle til Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES og varianter

> [!NOTE]
> Din distribution og version, og identificer den nærmeste post (efter overordnet og derefter underordnet) for den under `https://packages.microsoft.com/config/sles/`.

   I følgende kommandoer skal du erstatte *[distro]* og *[version]* med de oplysninger, du har identificeret:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Brug kommandoen SPident til at identificere systemrelaterede oplysninger, herunder version *[version]*.

   Hvis du f.eks. kører SLES 12 og ønsker at udrulle Microsoft Defender for Endpoint på Linux fra *produktionskanalen*:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Installér den offentlige nøgle til Microsoft GPG:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Ubuntu- og Debian-systemer

- Installér `curl` , hvis den ikke er installeret endnu:

    ```bash
    sudo apt-get install curl
    ```

- Installér `libplist-utils` , hvis den ikke er installeret endnu:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> Din distribution og version, og identificer den nærmeste post (efter overordnet og derefter underordnet) for den under `https://packages.microsoft.com/config/[distro]/`.

   I kommandoen nedenfor skal du erstatte *[distro]* og *[version]* med de oplysninger, du har identificeret:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > Brug kommandoen hostnamectl til at identificere systemrelaterede oplysninger, herunder version *[version]*.

   Hvis du f.eks. kører Ubuntu 18.04 og ønsker at installere Microsoft Defender for Endpoint på Linux fra *produktionskanalen*:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Installér lagerkonfigurationen:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Hvis du f.eks. vælger *prod-kanal* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- Installér pakken, hvis den `gpg` ikke allerede er installeret:

    ```bash
    sudo apt-get install gpg
    ```

  Hvis `gpg` ikke er tilgængelig, skal du installere `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- Installér den offentlige nøgle til Microsoft GPG:

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
    > Hvis du har flere Microsoft-lagre konfigureret på din enhed, kan du være specifik om, hvilket lager pakken skal installeres fra. I følgende eksempel kan du se, hvordan du installerer pakken fra `production` kanalen, hvis lagerkanalen `insiders-fast` også er konfigureret på denne enhed. Denne situation kan opstå, hvis du bruger flere Microsoft-produkter på din enhed. Afhængigt af distributionen og versionen af din server kan lagerets alias være anderledes end det i følgende eksempel.

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
    > Hvis du har flere Microsoft-lagre konfigureret på din enhed, kan du være specifik om, hvilket lager pakken skal installeres fra. I følgende eksempel kan du se, hvordan du installerer pakken fra `production` kanalen, hvis lagerkanalen `insiders-fast` også er konfigureret på denne enhed. Denne situation kan opstå, hvis du bruger flere Microsoft-produkter på din enhed.

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

- Ubuntu og Debian-system:

    ```bash
    sudo apt-get install mdatp
    ```

    > [!NOTE]
    > Hvis du har flere Microsoft-lagre konfigureret på din enhed, kan du være specifik om, hvilket lager pakken skal installeres fra. I følgende eksempel kan du se, hvordan du installerer pakken fra `production` kanalen, hvis lagerkanalen `insiders-fast` også er konfigureret på denne enhed. Denne situation kan opstå, hvis du bruger flere Microsoft-produkter på din enhed.

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
> Hvis du går glip af dette trin, viser en kommando, der udføres, en advarsel om, at produktet er uden licens. `mdatp health` Kommandoen returnerer også værdien .`false`

1. På Microsoft 365 Defender-portalen skal du gå til **Indstillinger > Slutpunkter > Enhedshåndtering > Onboarding**.
2. Vælg **Linux Server** som operativsystem i den første rullemenu. I den anden rullemenu skal du vælge **Lokalt script** som installationsmetode.
3. Vælg **Download onboarding-pakke**. Gem filen som WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="Download af en onboardingpakke på Microsoft 365 Defender-portalen" lightbox="images/portal-onboarding-linux.png":::

4. Kontrollér, at du har filen, i en kommandoprompt, og udtræk indholdet af arkivet:

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
    > Indledningsvist er klientenheden ikke knyttet til en organisation, og attributten *orgId* er tom.

    ```bash
    mdatp health --field org_id
    ```

2. Kør MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > Hvis du vil køre denne kommando, skal du have `python`  eller `python3` installeret på enheden, afhængigt af disto og versionen. Hvis det er nødvendigt, skal du se [Trinvis vejledning til installation af Python på Linux](https://opensource.com/article/20/4/install-python-linux).
    
    Hvis du kører RHEL 8.x eller Ubuntu 20.04 eller nyere, skal du bruge `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    I resten af distributioner og versioner skal du bruge `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. Bekræft, at enheden nu er knyttet til din organisation, og rapporterer et gyldigt organisations-id:

    ```bash
    mdatp health --field org_id
    ```

4. Kontrollér status for produktet ved at køre følgende kommando. En returværdi for `1` angiver, at produktet fungerer som forventet:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Når produktet starter for første gang, downloades de nyeste antimalwaredefinitioner. Dette kan tage op til et par minutter, afhængigt af netværksforbindelsen. I denne periode returnerer ovenstående kommando en værdi af typen `false`. Du kan kontrollere status for definitionsopdateringen ved hjælp af følgende kommando:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > Bemærk, at du muligvis også skal konfigurere en proxy, når du har fuldført den første installation. Se [Konfigurer Defender for Endpoint på Linux for at få oplysninger om registrering af statisk proxy: Konfiguration efter installation](linux-static-proxy-configuration.md#post-installation-configuration).

5. Kør en av-registreringstest for at bekræfte, at enheden er onboardet korrekt, og rapportering til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

    - Sørg for, at beskyttelse i realtid er aktiveret (angivet af et resultat af `1` at køre følgende kommando):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      Hvis den ikke er aktiveret, skal du udføre følgende kommando:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Åbn et terminalvindue, og udfør følgende kommando:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Filen skulle være sat i karantæne af Defender for Endpoint på Linux. Brug følgende kommando til at få vist alle registrerede trusler:

        ```bash
        mdatp threat list
        ```

6. Kør en Slutpunktsregistrering og -svar registreringstest, og simuler en registrering for at bekræfte, at enheden er onboardet korrekt, og rapportere til tjenesten. Udfør følgende trin på den nyligt onboardede enhed:

    - Bekræft, at den onboardede Linux-server vises i Microsoft 365 Defender. Hvis dette er den første onboarding af maskinen, kan det tage op til 20 minutter, indtil det vises.

    - Download og udpak [scriptfilen](https://aka.ms/LinuxDIY) til en onboardet Linux-server, og kør følgende kommando: `./mde_linux_edr_diy.sh`

    - Efter et par minutter skal en registrering opløftes i Microsoft 365 Defender.

    - Se beskedoplysningerne, computerens tidslinje, og udfør dine typiske undersøgelsestrin.

## <a name="installer-script"></a>Installationsscript

Du kan også bruge et automatiseret [bash-installationsscript](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) i vores [offentlige GitHub lager](https://github.com/microsoft/mdatp-xplat/).
Scriptet identificerer distributionen og versionen, forenkler valget af det rigtige lager, konfigurerer enheden til at trække den nyeste pakke og kombinerer produktinstallationen og onboardingtrinnene.

```bash
> ./mde_installer.sh --help
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

## <a name="log-installation-issues"></a>Problemer med loginstallation

Se [Problemer med installation af logfil](linux-resources.md#log-installation-issues) for at få flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Sådan overfører du fra Insiders-Fast til en produktionskanal

1. Fjern versionen "Insiders-Fast channel" af Defender for Endpoint på Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. Deaktiver Defender for Endpoint på Linux-Insiders-Fast lager

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > Outputtet skal vise "packages-microsoft-com-fast-prod".

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. Geninstaller Microsoft Defender for Endpoint på Linux ved hjælp af "Produktionskanal".

## <a name="uninstallation"></a>Uninstallation

Se [Fjern](linux-resources.md#uninstall) for at få oplysninger om, hvordan du fjerner Defender for Endpoint på Linux fra klientenheder.

## <a name="see-also"></a>Se også

- [Undersøg agentens tilstandsproblemer](health-status.md)
