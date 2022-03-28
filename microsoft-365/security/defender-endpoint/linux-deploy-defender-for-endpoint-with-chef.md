---
title: Sådan installeres Defender til Slutpunkt på Linux med Chef
description: Få mere at vide om, hvordan du installerer Defender til Slutpunkt på Linux med Chef
keywords: microsoft, defender, atp, linux, scans, antivirus, microsoft defender til slutpunkt (linux)
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
ms.openlocfilehash: 799fc4d163b120b4197b6cd044efe4740e4a3cc7
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63597903"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Deploy Defender for Endpoint på Linux med Chef

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Før du begynder: Installer udpakke, hvis den ikke allerede er installeret.

Chef-komponenterne er allerede installeret, og der findes et Chef-lager (chef generate repo \<reponame\>) for at gemme den kogebog, der skal bruges til at installere til Defender til slutpunkt på Chef-administrerede Linux-servere.

Du kan oprette en ny kogebog i dit eksisterende lager ved at køre følgende kommando inde fra mappen kogebøger, der findes i dit køkkenlager:

```bash
chef generate cookbook mdatp
```

Denne kommando opretter en ny mappestruktur for den nye kogebog ved navn mdatp. Du kan også bruge en eksisterende kogebog, hvis du allerede har en, du vil bruge til at føje MDE-installationen til.
Når kogebogen er oprettet, kan du oprette en filmappe i mappen Kogebog, der lige er blevet oprettet:

```bash
mkdir mdatp/files
```

Overfør zip-filen Linux Server Onboarding, som kan downloades fra Microsoft 365 Defender-portalen til denne nye filmappe.

På Chef-arbejdsstationen skal du gå til mappen mdatp/recipes. Denne mappe oprettes, når kogebogen blev oprettet. Brug din foretrukne teksteditor (f.eks. vi eller nano) til at føje følgende instruktioner til slutningen af standard.rb-filen:

- include_recipe '::onboard_mdatp'
- include_recipe '::install_mdatp'

Gem og luk derefter default.rb-filen.

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

Du skal ændre versionsnummeret, distributions- og repo-navnet, så det passer til den version, du udruller i, og den kanal, du gerne vil installere.
Derefter skal du oprette en onboard_mdatp.rb-fil i mappen mdatp/recipies. Føj følgende tekst til den pågældende fil:

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

Sørg for at opdatere navnet på stien til placeringen af onboardingfilen.
For at teste installationen på arbejdsstationen Chef skal du blot køre ``sudo chef-client -z -o mdatp``.
Efter installationen bør du overveje at oprette og udrulle en konfigurationsfil til de servere, der er baseret på [Angiv indstillinger for Microsoft Defender til slutpunkt på Linux](/linux-preferences.md).
Når du har oprettet og testet din konfigurationsfil, kan du placere den i mappen Cookbook/mdatp/files, hvor du også placerede onboardingpakken. Derefter kan du oprette en settings_mdatp.rb-fil i mappen mdatp/recipies og tilføje denne tekst:

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

Hvis du vil medtage dette trin som en del af opskriften, skal du blot include_recipe ":: settings_mdatp" til din default.rb-fil i opskriftsmappen.
Du kan også bruge crontab til at planlægge automatiske opdateringer [Planlæg en opdatering af Microsoft Defender til slutpunkt (Linux)](linux-update-MDE-Linux.md).

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
