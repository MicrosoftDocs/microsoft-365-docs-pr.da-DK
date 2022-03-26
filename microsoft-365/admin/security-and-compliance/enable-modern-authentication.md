---
title: Aktivér moderne godkendelse Office 2013 på Windows enheder
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7dc1c01a-090f-4971-9677-f1b192d6c910
description: Lær at angive registreringsdatabasenøgler for at aktivere moderne godkendelse for enheder, Microsoft Office 2013 er installeret.
ms.openlocfilehash: 468658c3b346c7923937ff9595699a20306ed6a9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754177"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Aktivér moderne godkendelse Office 2013 på Windows enheder

Microsoft Office 2013 på Microsoft Windows understøtter moderne godkendelse. Men hvis du vil aktivere den, skal du konfigurere følgende registreringsdatabasenøgler:

|Registreringsdatabasenøgle|Type|Værdi|
|:---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

> [!NOTE]
> Moderne godkendelse er allerede aktiveret i Office 2016 eller nyere. Du behøver ikke at angive disse registreringsdatabasenøgler for nyere versioner af Office.

## <a name="enable-modern-authentication-for-office-2013-clients"></a>Aktivere moderne godkendelse for Office 2013-klienter

1. Luk Outlook.

2. Kopiér og indsæt følgende tekst i Notesblok:

   ```text
   Windows Registry Editor Version 5.00

   [HKEY_CURRENT_USER\Software\Microsoft\Exchange]
   "AlwaysUseMSOAuthForAutoDiscover"=dword:00000001

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
   "EnableADAL"=dword:00000001
   "Version"=dword:00000001
   ```

3. Gem filen med filtypenavnet .reg i stedet for .txt på en placering, der er nem at finde. F.eks. `C:\Data\Office2013_Enable_ModernAuth.reg`.

4. Åbn Stifinder (tidligere kaldet Windows Stifinder), gå til placeringen af den .reg-fil, du lige har gemt, og dobbeltklik på den.

5. I dialogboksen **Kontrol af brugerkonti** , der vises, skal du **klikke på** Ja for at tillade, at appen foretager ændringer på din enhed.

6. I dialogboksen **registreringseditorens** advarselsdialogboks skal du **klikke på Ja** for at acceptere ændringerne.

Når du har angivet registreringsdatabasenøglerne, kan du indstille Office 2013-apps til at bruge multifaktorgodkendelse (MFA) med Microsoft 365. Få mere at vide under [Konfigurer multifaktorgodkendelse](set-up-multi-factor-authentication.md).

Hvis du i øjeblikket er logget på en af Office-klientappsene, skal du logge af og logge på igen, før ændringen træder i kraft. Ellers vil MRU og globale indstillinger ikke være tilgængelige, før identiteten er etableret.

## <a name="disable-modern-authentication-on-devices"></a>Deaktiver moderne godkendelse på enheder

Fremgangsmåden til at deaktivere moderne godkendelse på en enhed minder meget om den, men der kræves færre registreringsdatabasenøgler, og du skal angive deres værdier til 0.

|Registreringsdatabasenøgle|Type|Værdi|
|---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|

```text
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Exchange]
"AlwaysUseMSOAuthForAutoDiscover"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
"EnableADAL"=dword:00000000
```

## <a name="related-content"></a>Relateret indhold

[Log på Office 2013 med en anden godkendelsesmetode](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)

[Outlook beder om adgangskode og bruger ikke moderne godkendelse til at oprette forbindelse til Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled)
