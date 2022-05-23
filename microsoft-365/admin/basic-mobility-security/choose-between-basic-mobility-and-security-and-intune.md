---
title: Vælg mellem grundlæggende mobilitet og sikkerhed og Intune
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- AdminTemplateSet
search.appverid:
- MET150
description: Basic Mobility and Security er en del af Microsoft 365 planer, mens Microsoft Intune er et separat produkt, der er inkluderet i visse Microsoft 365 planer.
ms.openlocfilehash: 01d2717aa0368e3d1dc5ed17f3adfd6313880dfe
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636102"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Vælg mellem grundlæggende mobilitet og sikkerhed eller Intune

[Microsoft Intune](/mem/intune/) er et separat produkt, der er inkluderet i visse Microsoft 365 planer, mens Grundlæggende mobilitet og sikkerhed er en del af Microsoft 365 planer.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Tilgængelighed af grundlæggende mobilitet og sikkerhed og Intune

Både grundlæggende mobilitet og sikkerhed og Intune er inkluderet i forskellige planer, som beskrevet i følgende tabel.

| Plan | Basic Mobility og Security | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Apps|Ja|Nej|
|Microsoft 365 Business Basic|Ja|Nej|
|Microsoft 365 Business Standard|Ja|Nej|
|Office 365 E1 |Ja|Nej|
|Office 365 E3 |Ja|Nej|
|Office 365 E5 |Ja|Nej|
|Microsoft 365 Business Premium |Ja|Ja|
|Microsoft 365 første linje 3 |Ja|Ja|
|Microsoft 365 Enterprise E3 |Ja|Ja|
|Microsoft 365 Enterprise E5 |Ja|Ja|
|Microsoft 365 Education A1 |Ja|Ja|
|Microsoft 365 Education A3 |Ja|Ja|
|Microsoft 365 Education A5 |Ja|Ja|
|Microsoft Intune |Nej|Ja|
|Enterprise Mobility & Security E3 |Nej|Ja|
|Enterprise Mobility & Security E5 |Nej|Ja|

> [!NOTE]
> Du kan ikke begynde at bruge Basic Mobility and Security, hvis du allerede bruger Microsoft Intune.

 Du kan finde flere oplysninger under [tjenestebeskrivelser for Microsoft 365 og Office 365 platform](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Forskelle i egenskaber

Microsoft Intune og indbygget basismobilitet og sikkerhed giver dig både mulighed for at administrere mobilenheder i din organisation, men der er vigtige forskelle i funktionaliteten, som beskrevet i følgende tabel.

> [!NOTE]
> Du kan administrere brugere og deres mobilenheder ved hjælp af både Intune og Grundlæggende mobilitet og sikkerhed i den samme Microsoft 365 Business Standard organisation *ved først at konfigurere Basic Mobility og Security og derefter tilføje Microsoft Intune*. Det giver dig mulighed for at vælge Basic Mobility and Security eller den mere funktionsrige Intune løsning. Tildel en Intune licens for at aktivere de Intune funktioner.

| Funktionsområde | Fremhævninger af funktioner | Basic Mobility og Security | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Enhedstyper|Administration af forskellige OS-platforme og større varianter af administrationstilstand. |Windows<br/>Ios<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>Ios<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad OS|
|Enhedens overholdelse af angivne standarder|Angiv og administrer sikkerhedspolitikker, f.eks. pinkodelås på enhedsniveau og registrering af jailbreak. |Begrænsninger på Android-enheder. Se [detaljer](capabilities.md). |Ja|
|Betinget adgang baseret på enhedens overholdelse af angivne standarder |Undgå, at enheder, der ikke overholder regler og regler, får adgang til virksomhedens mail og data fra cloudmiljøet. |Understøttes ikke på Windows 10.<br/>Begrænset til at styre adgangen til Exchange Online, SharePoint Online og Outlook. |Ja |
|Enhedskonfiguration  |Konfigurer enhedsindstillinger (f.eks. deaktivering af kameraet)|Begrænset sæt indstillinger.|Ja|
|Mailprofiler  |Klargør en oprindelig mailprofil på enheden. |Ja|Ja|
|WiFi-profiler |Klargør en oprindelig WiFi-profil på enheden. |Nej|Ja|
|VPN-profiler |Klargør en oprindelig VPN-profil på enheden. |Nej|Ja|
|Administration af mobilapps  |Udrul dine interne line of business-apps og fra appbutikker til brugere. |Nej|Ja|
|Beskyttelse af mobilapps  |Gør det muligt for brugerne at få sikker adgang til firmaoplysninger ved hjælp af de Office mobil- og line of business-apps, de kender, samtidig med at de sikrer sikkerheden for data ved at hjælpe med at begrænse handlinger som f.eks. kopiere, klippe, indsætte og gemme som, så det kun er de apps, der administreres som godkendt til firmadata. Fungerer, selvom enhederne ikke er tilmeldt Basic Mobility og Security. Se Beskyt appdata ved hjælp af MAM-politikker. |Nej|Ja|
|Administreret browser  |Aktivér mere sikker webbrowsing ved hjælp af Edge-appen. |Nej|Ja|
|Programmer til nul touchtilmelding (AutoPilot) |Tilmeld et stort antal virksomhedsejede enheder, samtidig med at brugerkonfigurationen forenkles. |Nej|Ja|

Ud over de funktioner, der er angivet i den foregående tabel, omfatter Basic Mobility og Security og Intune begge et sæt fjernhandlinger, der sender kommandoer til enheder via internettet. Du kan f.eks. fjerne Office data fra en medarbejders enhed, mens du lader personlige data være på plads (gå på pension), fjerne Office apps fra en medarbejders enhed (slette) eller nulstille en enhed til fabriksindstillingerne (fuld sletning).

Grundlæggende handlinger i forbindelse med mobilitet og sikkerhed omfatter tilbagetrækning, sletning og fuld sletning. Du kan få flere oplysninger om grundlæggende mobilitets- og sikkerhedshandlinger under [Funktioner i Grundlæggende mobilitet og sikkerhed](capabilities.md).

Med Intune har du følgende handlinger:

- [Autopilotnulstilling](/mem/autopilot/windows-autopilot-reset) (kun Windows)
- [Bitlocker-nøglegendannelse](https://support.microsoft.com/windows/finding-your-bitlocker-recovery-key-in-windows-6b71ad27-0b89-ea08-f143-056f5ab347d6) (kun Windows)
- [Brug sletning, tilbagetrækning eller manuel framelding af enheden](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
- [Deaktiver aktiveringslås](/mem/intune/remote-actions/device-activation-lock-disable) (kun iOS)
- [Frisk start](/mem/intune/remote-actions/device-fresh-start) (kun Windows)
- [Fuld scanning](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (kun Windows 10)
- [Find enhed](/mem/intune/remote-actions/device-locate) (kun iOS)
- [Mistet tilstand](/mem/intune/remote-actions/device-lost-mode) (kun iOS)- [Hurtig scanning](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (kun Windows 10)
- [Fjernstyring til Android](/mem/intune/remote-actions/teamviewer-support)
- [Fjernlås](/mem/intune/remote-actions/device-remote-lock)
- [Omdøb enhed](/mem/intune/remote-actions/device-rename)
- [Nulstil](/mem/intune/remote-actions/device-passcode-reset) [adgangskodegenstart](/mem/intune/remote-actions/device-restart) (kun Windows)
- [Opdater Windows Defender Security Intelligence](https://www.microsoft.com/en-us/wdsi/defenderupdates) (kun Windows)
- [Windows 10 nulstilling af pinkode](/windows/security/identity-protection/hello-for-business/hello-feature-pin-reset) (kun Windows)
- [Send brugerdefinerede meddelelser](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device) (Android, iOS, iPad OS)
- [Synkroniser enhed](/mem/intune/remote-actions/device-sync)

Du kan få flere oplysninger om Intune handlinger [i dokumentationen til Microsoft Intune](/mem/intune/).
