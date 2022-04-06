---
title: Udrul Microsoft Defender for Endpoint på Linux med Puppet
ms.reviewer: ''
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på Linux ved hjælp af Dukke.
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
ms.openlocfilehash: 5ec3eb5d12933b33f4af7d5af96b4ab54fda4604
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663792"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Udrul Microsoft Defender for Endpoint på Linux med Puppet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

I denne artikel beskrives det, hvordan du installerer Defender for Endpoint på Linux ved hjælp af Puppet. En vellykket installation kræver fuldførelse af alle følgende opgaver:

- [Download onboardingpakken](#download-the-onboarding-package)
- [Opret dukkemanifest](#create-a-puppet-manifest)
- [Installation](#deployment)
- [Kontrollér onboardingstatus](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

 Hvis du vil have en beskrivelse af forudsætninger og systemkrav til den aktuelle softwareversion, skal du se [hovedsiden Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md).

Derudover skal du være fortrolig med dukkeadministrationsopgaver i forbindelse med dukkeinstallation, have dukket op og vide, hvordan du installerer pakker. Dukken har mange måder at fuldføre den samme opgave på. Disse instruktioner forudsætter tilgængelighed af understøttede dukkemoduler, f.eks *. egnet* til at hjælpe med at installere pakken. Din organisation bruger muligvis en anden arbejdsproces. Du kan finde flere oplysninger i [dokumentationen til din dukke](https://puppet.com/docs) .

## <a name="download-the-onboarding-package"></a>Download onboardingpakken

Download onboardingpakken fra Microsoft 365 Defender portal:

1. I Microsoft 365 Defender portal skal du gå til **Indstillinger > Slutpunkter > Enhedshåndtering > Onboarding**.
2. Vælg **Linux Server** som operativsystem i den første rullemenu. I den anden rullemenu skal du vælge **Dit foretrukne Værktøj til administration af Linux-konfiguration** som installationsmetode.
3. Vælg **Download onboarding-pakke**. Gem filen som WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Muligheden for at downloade den onboardede pakke" lightbox="images/portal-onboarding-linux-2.png":::

4. Kontrollér, at du har filen, i en kommandoprompt. 

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

5. Udpak indholdet af arkivet.

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Opret et dukkemanifest

Du skal oprette et dukkemanifest til installation af Defender for Endpoint på Linux på enheder, der administreres af en dukkeserver. I dette eksempel bruges *de apt* - og *yumrepo-moduler* , der er tilgængelige fra dukkelabs, og det antages, at modulerne er installeret på din dukkeserver.

Opret mapperne *install_mdatp/filer* og *install_mdatp/manifester* under mappen Med moduler i din Dukkeinstallation. Denne mappe er typisk placeret i */etc/dukketeater/kode/miljøer/produktion/moduler* på din dukkeserver. Kopiér den mdatp_onboard.json-fil, der er oprettet ovenfor, til mappen *install_mdatp/filer* . Opret en *init.pp* fil, der indeholder installationsvejledningen:

```bash
pwd
```

```Output
/etc/puppetlabs/code/environments/production/modules
```

```bash
tree install_mdatp
```

```Output
install_mdatp
├── files
│   └── mdatp_onboard.json
└── manifests
    └── init.pp
```

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>Indhold af `install_mdatp/manifests/init.pp`

Defender for Endpoint på Linux kan udrulles fra en af følgende kanaler (angivet nedenfor som *[channel]*): *insiders-fast*, *insiders-slow* eller *prod*. Hver af disse kanaler svarer til et Linux-softwarelager.

Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes til din enhed. Enheder i *insiders-fast* er de første til at modtage opdateringer og nye funktioner, efterfulgt senere af *insiders-langsom* og til sidst af *prod*.

For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten *insiders-fast* eller *insiders-slow*.

> [!WARNING]
> Hvis du skifter kanal efter den første installation, skal produktet geninstalleres. Hvis du vil skifte produktkanal: Fjern den eksisterende pakke, genkonfigurer enheden, så den bruger den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.

Bemærk din distribution og version, og identificer den nærmeste post for den under `https://packages.microsoft.com/config/[distro]/`.

I nedenstående kommandoer skal du erstatte *[distro]* og *[version]* med de oplysninger, du har identificeret:

> [!NOTE]
> Hvis der er tale om RedHat, Oracle Linux, Amazon Linux 2 og CentOS 8, skal *du erstatte [distro]* med 'rhel'.

```puppet
# Puppet manifest to install Microsoft Defender for Endpoint on Linux.
# @param channel The release channel based on your environment, insider-fast or prod.
# @param distro The Linux distribution in lowercase. In case of RedHat, Oracle Linux, Amazon Linux 2, and CentOS 8, the distro variable should be 'rhel'.
# @param version The Linux distribution release number, e.g. 7.4.

class install_mdatp (
$channel = 'insiders-fast',
$distro = undef,
$version = undef
){
    case $::osfamily {
        'Debian' : {
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/${distro}/${version}/prod",
                release  => $channel,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/${distro}/${version}/${channel}",
                descr    => "packages-microsoft-com-prod-${channel}",
                enabled  => 1,
                gpgcheck => 1,
                gpgkey   => 'https://packages.microsoft.com/keys/microsoft.asc'
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }

    case $::osfamily {
        /(Debian|RedHat)/: {
            file { ['/etc/opt', '/etc/opt/microsoft', '/etc/opt/microsoft/mdatp']:
                ensure => directory,
                owner  => root,
                group  => root,
                mode   => '0755'
            }

            file { '/etc/opt/microsoft/mdatp/mdatp_onboard.json':
                source  => 'puppet:///modules/install_mdatp/mdatp_onboard.json',
                owner   => root,
                group   => root,
                mode    => '0600',
                require => File['/etc/opt/microsoft/mdatp']
            }

            package { 'mdatp':
                ensure  => 'installed',
                require => File['/etc/opt/microsoft/mdatp/mdatp_onboard.json']
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }
}
```

## <a name="deployment"></a>Installation

Medtag ovenstående manifest på webstedet.pp Fil:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```

```Output
node "default" {
    include install_mdatp
}
```

Tilmeldte agentenheder forespørger jævnligt dukkeserveren og installerer nye konfigurationsprofiler og politikker, så snart de registreres.

## <a name="monitor-puppet-deployment"></a>Overvåg udrulning af dukke

På agentenheden kan du også kontrollere onboardingstatussen ved at køre:

```bash
mdatp health
```

```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **licensed**: Dette bekræfter, at enheden er knyttet til din organisation.

- **orgId**: Dette er dit Defender for Endpoint-organisations-id.

## <a name="check-onboarding-status"></a>Kontrollér onboardingstatus

Du kan kontrollere, at enhederne er onboardet korrekt, ved at oprette et script. Følgende script kontrollerer f.eks. tilmeldte enheders onboardingstatus:

```bash
mdatp health --field healthy
```

Ovenstående kommando udskriver `1` , om produktet er onboardet og fungerer som forventet.

> [!IMPORTANT]
> Når produktet starter for første gang, downloades de nyeste antimalwaredefinitioner. Afhængigt af din internetforbindelse kan det tage op til et par minutter. I denne periode returnerer ovenstående kommando en værdi af typen `0`.

Hvis produktet ikke fungerer korrekt, angiver afslutningskoden (som kan kontrolleres gennem `echo $?`) problemet:

- 1, hvis enheden endnu ikke er onboardet.
- 3, hvis forbindelsen til daemon ikke kan etableres.

## <a name="log-installation-issues"></a>Problemer med loginstallation

 Du kan finde flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl, under [Problemer med loginstallation](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>Opgraderinger af operativsystem

Når du opgraderer operativsystemet til en ny overordnet version, skal du først fjerne Defender for Endpoint på Linux, installere opgraderingen og til sidst konfigurere Defender for Endpoint på Linux på din enhed.

## <a name="uninstallation"></a>Uninstallation

Opret et modul *remove_mdatp* på samme måde som *install_mdatp* med følgende indhold *i init.pp* Fil:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
