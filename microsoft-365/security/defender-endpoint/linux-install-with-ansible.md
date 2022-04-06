---
title: Installér Microsoft Defender for Endpoint på Linux med Ansible
ms.reviewer: ''
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på Linux ved hjælp af Ansible.
keywords: microsoft, defender, Microsoft Defender for Endpoint, linux, installation, deploy, uninstallation, installations, ansible, linux, redhat, ubuntu, defender, sles, suse, centos, amazon linux 2
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
ms.openlocfilehash: 57f0687fce422f26b76fc8b98a06ce0566f90f60
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476065"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-ansible"></a>Installér Microsoft Defender for Endpoint på Linux med Ansible

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Denne artikel beskriver, hvordan du installerer Defender til Slutpunkt på Linux ved hjælp af Ansible. En vellykket installation kræver, at alle følgende opgaver er gennemført:

- [Download onboardingpakken](#download-the-onboarding-package)
- [Opret ANSIBLE YAML-filer](#create-ansible-yaml-files)
- [Udrulning](#deployment)
- [Referencer](#references)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

Før du går i gang, skal du se den primære [Defender for Endpoint på Linux-siden](microsoft-defender-endpoint-linux.md) for en beskrivelse af forudsætningerne og systemkravene for den aktuelle softwareversion.

Desuden skal du ved, hvordan du kan installere Ansible-installation, være fortrolig med andre administrationsopgaver, have Ansible konfigureret og vide, hvordan du installerer playbooks og opgaver. Ansible har mange måder at fuldføre den samme opgave på. Denne vejledning forudsætter, at understøttede moduler( Ansible Modules) er tilgængelige, f.eks. *passende* og *ikke-arkivive* til at hjælpe med installationen af pakken. Din organisation bruger muligvis en anden arbejdsproces. Se denible [dokumentation for at](https://docs.ansible.com/) få mere at vide.

- Ansible skal installeres på mindst én computer (Ansible kalder dette kontrolnoden).
- SSH skal konfigureres til en administratorkonto mellem kontrolnoden og alle administrerede noder (enheder, der har Defender til Slutpunkt installeret), og det anbefales at konfigurere med godkendelse med offentlig nøgle.
- Følgende software skal installeres på alle administrerede noder:
  - krølle
  - python-apt

- Alle administrerede noder skal være angivet i følgende format i den `/etc/ansible/hosts` eller relevante fil:

    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- Ping-test:

    ```bash
    ansible -m ping all
    ```

## <a name="download-the-onboarding-package"></a>Download onboardingpakken

Download onboardingpakken fra Microsoft 365 Defender portal:

1. I Microsoft 365 Defender skal du gå **til Indstillinger > slutpunkter > administration af > onboarding**.
2. I den første rullemenu skal du vælge **Linux Server** som operativsystem. I den anden rullemenu skal du vælge Dit **foretrukne Linux-konfigurationsstyringsværktøj** som installationsmetode.
3. Vælg **Download onboarding pakke**. Gem filen som WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Indstillingen Download onboarding package" lightbox="images/portal-onboarding-linux-2.png":::

4. Kontrollér, at du har filen, i en kommandoprompt. Udtræk indholdet af arkivet:

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-ansible-yaml-files"></a>Opret ANSIBLE YAML-filer

Opret en underopgave eller rollefiler, der bidrager til en playbook eller opgave.

- Opret onboardingopgaven, `onboarding_setup.yml`:

    ```bash
    - name: Create MDATP directories
      file:
        path: /etc/opt/microsoft/mdatp/
        recurse: true
        state: directory
        mode: 0755
        owner: root
        group: root

    - name: Register mdatp_onboard.json
      stat:
        path: /etc/opt/microsoft/mdatp/mdatp_onboard.json
      register: mdatp_onboard

    - name: Extract WindowsDefenderATPOnboardingPackage.zip into /etc/opt/microsoft/mdatp
      unarchive:
        src: WindowsDefenderATPOnboardingPackage.zip
        dest: /etc/opt/microsoft/mdatp
        mode: 0600
        owner: root
        group: root
      when: not mdatp_onboard.stat.exists
    ```

- Tilføj lager og nøgle for Defender til slutpunkt: `add_apt_repo.yml`

    Defender til slutpunkt på Linux kan installeres fra en af følgende kanaler (angivet nedenfor som *[kanal]*): *Insiders-fast*, *Insiders-slow* eller *prod*. Hver af disse kanaler svarer til et Linux-softwarelager.

    Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes din enhed. Enheder i *Insiders-fast* er de første, der modtager opdateringer og nye funktioner, efterfulgt senere af *Insiders-slow* og til sidst *af professionelle*.

    For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten *Insiders-fast* eller *Insiders-slow*.

    > [!WARNING]
    > Hvis du skifter kanal efter den indledende installation, skal produktet geninstalleres. Sådan skifter du produktkanalen: Fjern den eksisterende pakke, konfigurer enheden igen til at bruge den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.

    Bemærk din fordeling og version, og identificer den nærmeste post for den under `https://packages.microsoft.com/config/[distro]/`.

    I de følgende kommandoer skal du erstatte *[distro]* *og [version]* med de oplysninger, du har identificeret.

    > [!NOTE]
    > Erstat *[distro]* med "rhel] med Oracle Linux og Amazon Linux 2.

  ```bash
  - name: Add Microsoft APT key
    apt_key:
      url: https://packages.microsoft.com/keys/microsoft.asc
      state: present
    when: ansible_os_family == "Debian"

  - name: Add Microsoft apt repository for MDATP
    apt_repository:
      repo: deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/[distro]/[version]/prod [codename] main
      update_cache: yes
      state: present
      filename: microsoft-[channel]
    when: ansible_os_family == "Debian"

  - name: Add Microsoft DNF/YUM key
    rpm_key:
      state: present
      key: https://packages.microsoft.com/keys/microsoft.asc
    when: ansible_os_family == "RedHat"

  - name: Add  Microsoft yum repository for MDATP
    yum_repository:
      name: packages-microsoft-[channel]
      description: Microsoft Defender for Endpoint
      file: microsoft-[channel]
      baseurl: https://packages.microsoft.com/[distro]/[version]/[channel]/ 
      gpgcheck: yes
      enabled: Yes
    when: ansible_os_family == "RedHat"
  ```

- Opret ansible installér og fjern YAML-filer.

    - Til nr-baserede fordelinger skal du bruge følgende YAML-fil:

        ```bash
        cat install_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_apt_repo.yml
            - name: Install MDATP
              apt:
                name: mdatp
                state: latest
                update_cache: yes
        ```

        ```bash
        cat uninstall_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              apt:
                name: mdatp
                state: absent
        ```

    - Til dnf-baserede fordelinger skal du bruge følgende YAML-fil:

        ```bash
        cat install_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_yum_repo.yml
            - name: Install MDATP
              dnf:
                name: mdatp
                state: latest
                enablerepo: packages-microsoft-[channel]
        ```

        ```bash
        cat uninstall_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              dnf:
                name: mdatp
                state: absent
        ```

## <a name="deployment"></a>Udrulning

Nu skal du køre opgavefilerne under `/etc/ansible/playbooks/` eller relevant mappe.

- Installation:

    ```bash
    ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts
    ```

> [!IMPORTANT]
> Når produktet starter for første gang, downloader det de seneste antimalwaredefinitioner. Afhængigt af din internetforbindelse kan det tage op til et par minutter.

- Validering/konfiguration:

    ```bash
    ansible -m shell -a 'mdatp connectivity test' all
    ```
    ```bash
    ansible -m shell -a 'mdatp health' all
    ```

- Fjern installation:

    ```bash
    ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts
    ```

## <a name="log-installation-issues"></a>Problemer med installation af logfil

Se [Problemer med installation af logfiler](linux-resources.md#log-installation-issues) for at få flere oplysninger om, hvordan du finder den automatisk oprettede log, der oprettes af installationsprogrammet, når der opstår en fejl.

## <a name="operating-system-upgrades"></a>Opgradering af operativsystem

Når du opgraderer dit operativsystem til en ny større version, skal du først fjerne Defender til slutpunkt på Linux, installere opgraderingen og til sidst konfigurere Defender til Slutpunkt på Linux på din enhed igen.

## <a name="references"></a>Referencer

- [Tilføj eller fjern YUM-lager](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_repository_module.html)

- [Administrer pakker med DNF Package Manager](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)

- [Tilføj og fjern APT-lagre](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html)

- [Administrer nr.-pakker](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

## <a name="see-also"></a>Se også
- [Undersøg agentens tilstandsproblemer](health-status.md)
