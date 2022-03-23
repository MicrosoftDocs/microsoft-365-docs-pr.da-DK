---
title: Installer Microsoft Defender til slutpunkt på Linux med Linux
ms.reviewer: ''
description: Beskriver, hvordan du installerer Microsoft Defender til slutpunkt på Linux ved hjælp af Linux.
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
ms.openlocfilehash: 305dd74d31f3cbbf07db23f8de89b2b57fe52326
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63592933"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Installer Microsoft Defender til slutpunkt på Linux med Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Denne artikel beskriver, hvordan du installerer Defender til Slutpunkt på Linux ved hjælp af Linux. En vellykket installation kræver, at alle følgende opgaver er gennemført:

- [Download onboardingpakken](#download-the-onboarding-package)
- [Opret manifest for Manifest](#create-a-puppet-manifest)
- [Udrulning](#deployment)
- [Kontrollér onboardingstatus](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Forudsætninger og systemkrav

 Hvis du vil have en beskrivelse af forudsætningerne for og systemkravene til den aktuelle softwareversion, skal du [se hovedsiden for Defender til slutpunkt på Linux](microsoft-defender-endpoint-linux.md).

Desuden skal du ved udrulning af Udrulning være fortrolig med administrationsopgaver i manuelt arbejde, have konfigureret og vide, hvordan du udruller pakker. Der findes mange måder at udføre den samme opgave på. Denne vejledning forudsætter, at understøttede moduler understøttes, f.eks *. nr* . til at hjælpe med installationen af pakken. Din organisation bruger muligvis en anden arbejdsproces. Se dokumentationen [om dokumentationen til dokumentationen](https://puppet.com/docs) for dokumentationen af dokumentationen for at få flere oplysninger.

## <a name="download-the-onboarding-package"></a>Download onboardingpakken

Download onboardingpakken fra Microsoft 365 Defender portal:

1. I Microsoft 365 Defender skal du gå **til Indstillinger > slutpunkter > administration af > onboarding**.
2. I den første rullemenu skal du vælge **Linux Server** som operativsystem. I den anden rullemenu skal du vælge Dit **foretrukne Linux-konfigurationsstyringsværktøj** som installationsmetode.
3. Vælg **Download onboarding pakke**. Gem filen som WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft 365 Defender portalskærm.](images/portal-onboarding-linux-2.png)

4. Kontrollér, at du har filen, i en kommandoprompt. 

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
5. Udtræk indholdet af arkivet.
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Oprette et manifest for manifest for manifester for manifester

Du skal oprette et manifest til at installere Defender for Endpoint på Linux på enheder, der administreres af en server, der administreres af den. I dette eksempel bruges *de apt* - og *yumrepo-moduler* , der er tilgængelige fra modullabs, og det antages, at modulerne er blevet installeret på Server, hvor Alle er installeret.

Opret mapperne *install_mdatp/filer* *og install_mdatp/manifester* under modulmappen i din Installation af Ford. Denne mappe er typisk placeret *i /etc/filtlabs/code/environments/production/modules* på din Server til server med server, hvor den starter. Kopiér den mdatp_onboard.json-fil, der er *oprettet ovenfor, install_mdatp/filer-mappen* . Opret en *init.pp* fil, der indeholder installationsvejledningen:

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

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>Indholdet af `install_mdatp/manifests/init.pp`

Defender til slutpunkt på Linux kan installeres fra en af følgende kanaler (angivet nedenfor som *[kanal]*): *Insiders-fast*, *Insiders-slow* eller *prod*. Hver af disse kanaler svarer til et Linux-softwarelager.

Valget af kanalen bestemmer typen og hyppigheden af opdateringer, der tilbydes din enhed. Enheder i *Insiders-fast* er de første, der modtager opdateringer og nye funktioner, efterfulgt senere af *Insiders-slow* og til sidst *af professionelle*.

For at få forhåndsvist nye funktioner og give tidlig feedback anbefales det, at du konfigurerer nogle enheder i din virksomhed til at bruge enten *Insiders-fast* eller *Insiders-slow*.

> [!WARNING]
> Hvis du skifter kanal efter den indledende installation, skal produktet geninstalleres. Sådan skifter du produktkanalen: Fjern den eksisterende pakke, konfigurer enheden igen til at bruge den nye kanal, og følg trinnene i dette dokument for at installere pakken fra den nye placering.

Bemærk din fordeling og version, og identificer den nærmeste post for den under `https://packages.microsoft.com/config/[distro]/`.

Udskift [distribution] og *[version] med* *de* oplysninger, du har identificeret, i nedenstående kommandoer:

> [!NOTE]
> Hvis det gælder RedHat, Oracle Linux, Amazon Linux 2 og CentOS 8, skal *du erstatte [distro]* med 'rhel'.

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
                location => "https://packages.microsoft.com/config/${distro}/${version}/prod",
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
                baseurl  => "https://packages.microsoft.com/config/${distro}/${version}/${channel}",
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

## <a name="deployment"></a>Udrulning

Medtag det ovenstående manifest på dit websted.pp fil:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```
```Output
node "default" {
    include install_mdatp
}
```

Tilmeldte agentenheder forespørger med jævne mellemrum På Server, og installer nye konfigurationsprofiler og politikker, så snart de registreres.

## <a name="monitor-puppet-deployment"></a>Skærm udrulning af 2010

På agentenheden kan du også kontrollere onboardingstatus ved at køre:

```bash
mdatp health
```
```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **licenseret**: Dette bekræfter, at enheden er knyttet til din organisation.

- **orgId**: Dette er din Defender for Endpoint-organisations-id.

## <a name="check-onboarding-status"></a>Kontrollér onboardingstatus

Du kan kontrollere, at enhederne er blevet installeret korrekt ved at oprette et script. Eksempelvis kontrollerer følgende script de enheder, der er tilmeldt, for at få onboardingstatus:

```bash
mdatp health --field healthy
```

Kommandoen ovenfor udskrives `1` , hvis produktet er onboardet og fungerer som forventet.

> [!IMPORTANT]
> Når produktet starter for første gang, downloader det de seneste antimalwaredefinitioner. Afhængigt af din internetforbindelse kan det tage op til et par minutter. I dette tidsrum returnerer kommandoen ovenfor en værdi på `0`.

Hvis produktet ikke er normalt, angiver udgangskoden (som kan kontrolleres `echo $?`via ) problemet:

- 1, hvis enheden endnu ikke er onboardet.
- 3, hvis forbindelsen til daemonen ikke kan etableres.

## <a name="log-installation-issues"></a>Problemer med installation af logfil

 Du kan finde flere oplysninger om, hvordan du finder den automatisk genererede log, der oprettes af installationsprogrammet, når der opstår en fejl, under [Problemer med installation af log](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>Opgradering af operativsystem

Når du opgraderer dit operativsystem til en ny større version, skal du først fjerne Defender til slutpunkt på Linux, installere opgraderingen og til sidst konfigurere Defender til Slutpunkt på Linux på din enhed igen.

## <a name="uninstallation"></a>Fjernelse af installation

Opret et modul *remove_mdatp* der *ligner install_mdatp* med følgende indhold i *init.pp* fil:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
