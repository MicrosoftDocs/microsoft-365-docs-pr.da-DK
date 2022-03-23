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
ms.openlocfilehash: c390e3b9858a4d7d8fc37ea5c5e6f1901d5e20fb
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63589940"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>Aktivér moderne godkendelse Office 2013 på Windows enheder

Hvis du vil aktivere moderne godkendelse for Windows enheder, der Office 2013 installeret, skal du angive bestemte registreringsdatabasenøgler.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>Aktivere moderne godkendelse for Office 2013-klienter

> [!NOTE]
> Moderne godkendelse er allerede aktiveret for Office 2016-klienter, du behøver ikke at angive registreringsdatabasenøgler for Office 2016. 
  
Hvis du vil aktivere moderne godkendelse for enheder, der kører Windows (f.eks. på bærbare computere og tablets), og som har Microsoft Office 2013 installeret, skal du angive følgende registreringsdatabasenøgler. Tasterne skal angives på hver enhed, du vil aktivere til moderne godkendelse:

<br>

****

|Registreringsdatabasenøgle|Type|Værdi|
|:---|:---:|---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

Opret eller rediger følgende registreringsdatabasenøgler for at tvinge Outlook bruge en nyere godkendelsesmetode til webtjenester som f.eks. EWS og Autodiscover. Vi anbefaler, at brugerne gennemtvinger Outlook at bruge moderne godkendelse.

1. Afslut Outlook.

2. Start registreringseditor ved hjælp af en af følgende procedurer, som passer til din version af Windows:

   - **Windows 10, Windows 8.1 og Windows 8:** Tryk på Windows+R for at åbne **dialogboksen** Kør. Skriv *regedit.exe*, og tryk derefter på **Enter.**
   - **Windows 7: Klik** **på Start**, *regedit.exe* i søgefeltet, og tryk derefter på **Enter.**

3. I Registreringseditor skal du finde og klikke på følgende undernøgler i registreringsdatabasen:

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Exchange\
   ```

4. Hvis nøglen *AlwaysUseMSOAuthForAutoDiscover* mangler, skal du i menuen Rediger pege på Ny og  derefter vælge **DWORD-værdi**. Skriv *AlwaysUseMSOAuthForAutoDiscover*, og tryk derefter på **Enter.**

5. Højreklik på *AlwaysUseMSOAuthForAutoDiscover*, og klik derefter på **Rediger.**

6. Skriv 1 **i feltet** **Værdidata**, og klik derefter på **OK.**

7. I Registreringseditor skal du finde og klikke på følgende undernøgler i registreringsdatabasen:

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\
   ```

8. Hvis *EnableADAL- og* *Version-tasterne* allerede findes, skal du ændre værdierne, hvis det er nødvendigt, og derefter afslutte Registreringseditor. Hvis de ikke gør det, skal du i menuen Rediger pege på **Ny** og derefter vælge **DWORD-værdi for** at oprette de manglende taster. 

9. Hvis f.eks. *EnableADAL-tasten* mangler, skal du *skrive EnableADAL* og derefter trykke på **Enter.**

10. Højreklik på *EnableADAL*, og klik derefter på **Rediger.**

11. Skriv 1 **i feltet** **Værdidata**, og klik derefter på **OK.**

12. Følg den samme fremgangsmåde for Version-tasten, hvis det er nødvendigt. 

13. **Afslut registreringseditor.**

Når du har angivet registreringsdatabasenøglerne, kan du indstille Office 2013-enheder til at bruge [multifaktorgodkendelse (MFA)](set-up-multi-factor-authentication.md) Microsoft 365. 
  
Hvis du i øjeblikket er logget på med en af klient-appsene, skal du logge af og logge på igen, før ændringen træder i kraft. Ellers vil MRU og globale indstillinger ikke være tilgængelige, før identiteten er etableret.
  
## <a name="disable-modern-authentication-on-devices"></a>Deaktiver moderne godkendelse på enheder

Hvis du vil deaktivere moderne godkendelse på en enhed, skal du angive følgende registreringsdatabasenøgler på enheden:

<br>

****

|Registreringsdatabasenøgle|Type|Værdi|
|:---|:---:|---:|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
   
## <a name="related-content"></a>Relateret indhold

[Log på Office 2013 med en anden godkendelsesmetode](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (artikel)\
[Outlook beder om adgangskode og bruger ikke moderne godkendelse til at oprette forbindelse til Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) (artikel)
