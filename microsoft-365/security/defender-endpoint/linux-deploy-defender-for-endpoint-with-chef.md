---
title: Sådan installerer du Defender for Endpoint på Linux med chef
description: Få mere at vide om, hvordan du installerer Defender for Endpoint på Linux med Chef
keywords: microsoft, defender, atp, linux, scans, antivirus, microsoft defender for endpoint (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8f610821b6c0bef7694d6ce8acd256f59f761f06
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872917"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Udrul Defender for Endpoint på Linux med Chef

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Før du begynder: Installer udpakket, hvis det ikke allerede er installeret.

Chef-komponenterne er allerede installeret, og der findes et cheflager (chef generér lager \<reponame\>) til lagring af den kogebog, der skal bruges til at udrulle til Defender for Endpoint på Chef-administrerede Linux-servere.

Du kan oprette en ny kogebog i dit eksisterende lager ved at køre følgende kommando inde fra mappen med kogebøger, der findes i dit cheflager:

```bash
chef generate cookbook mdatp
```

Denne kommando opretter en ny mappestruktur til den nye kogebog mdatp. Du kan også bruge en eksisterende kogebog, hvis du allerede har en, du vil bruge til at tilføje MDE-udrulningen i.
Når kogebogen er oprettet, skal du oprette en mappe med filer i kogebogens mappe, der lige er oprettet:

```bash
mkdir mdatp/files
```

Overfør den Linux Server Onboarding ZIP-fil, der kan downloades fra Microsoft 365 Defender-portalen, til denne mappe med nye filer.

På Chef Workstation skal du navigere til mappen mdatp/recipes. Denne mappe oprettes, når kogebogen blev oprettet. Brug din foretrukne teksteditor (f.eks. vi eller nano) til at føje følgende instruktioner til slutningen af filen default.rb:

- include_recipe '::onboard_mdatp'
- include_recipe '::install_mdatp'

Gem og luk derefter filen default.rb.

Opret derefter en ny opskriftsfil med navnet install_mdatp.rb i mappen opskrifter, og føj denne tekst til filen:

```powershell
#Add Microsoft Defender
Repo
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

Du skal ændre versionsnummeret, distributionen og lagerets navn, så det stemmer overens med den version, du installerer på, og den kanal, du vil installere.
Derefter skal du oprette en onboard_mdatp.rb-fil i mappen mdatp/recipies. Føj følgende tekst til filen:

```powershell
#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

Sørg for at opdatere stinavnet til placeringen af onboardingfilen.
Hvis du vil teste udrulningen på Chef-arbejdsstationen, skal du blot køre ``sudo chef-client -z -o mdatp``.
Efter udrulningen bør du overveje at oprette og installere en konfigurationsfil på serverne baseret på [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](/microsoft-365/security/defender-endpoint/linux-preferences).
Når du har oprettet og testet din konfigurationsfil, kan du placere den i mappen cookbook/mdatp/files, hvor du også har placeret onboardingpakken. Du kan derefter oprette en settings_mdatp.rb-fil i mappen mdatp/recipies og tilføje denne tekst:

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

Hvis du vil medtage dette trin som en del af opskriften, skal du blot føje include_recipe ':: settings_mdatp' til filen default.rb i opskriftsmappen.
Du kan også bruge crontab til at planlægge automatiske opdateringer [Planlæg en opdatering af Microsoft Defender for Endpoint (Linux)](linux-update-MDE-Linux.md).

Fjern MDATP-kogebog:

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```
