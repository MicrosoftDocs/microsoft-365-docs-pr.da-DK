---
title: Vælg mellem Grundlæggende mobilitet og sikkerhed og Intune
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
description: Grundlæggende mobilitet og sikkerhed er en del af Microsoft 365-planerne.
ms.openlocfilehash: 79e5a641ad4c7c1966d1014376c9f1698caeff16
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63594293"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>Vælg mellem Grundlæggende mobilitet og sikkerhed eller Intune

[Microsoft Intune](/mem/intune/) er et enkeltstående produkt, der følger med visse Microsoft 365-planer, mens Grundlæggende mobilitet og sikkerhed er en del af Microsoft 365-planerne.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>Tilgængelighed af Grundlæggende mobilitet og sikkerhed og Intune

Både Grundlæggende mobilitet og sikkerhed og Intune er inkluderet i en række planer, som er beskrevet i følgende tabel.

| Plan | Grundlæggende mobilitet og sikkerhed | Microsoft Intune |
|:-----|:-----|:-----|
|Microsoft 365 Apps|Ja|Nej|
|Microsoft 365 Business Basic|Ja|Nej|
|Microsoft 365 Business Standard|Ja|Nej|
|Office 365 E1 |Ja|Nej|
|Office 365 E3 |Ja|Nej|
|Office 365 E5 |Ja|Nej|
|Microsoft 365 Business Premium |Ja|Ja|
|Microsoft 365 Firstline 3 |Ja|Ja|
|Microsoft 365 Enterprise E3 |Ja|Ja|
|Microsoft 365 Enterprise E5 |Ja|Ja|
|Microsoft 365 Education A1 |Ja|Ja|
|Microsoft 365 Education A3 |Ja|Ja|
|Microsoft 365 Education A5 |Ja|Ja|
|Microsoft Intune |Nej|Ja|
|Enterprise Mobility & Security E3 |Nej|Ja|
|Enterprise Mobility & Security E5 |Nej|Ja|

> [!NOTE]
> Du kan ikke begynde at bruge Grundlæggende mobilitet og sikkerhed, hvis du allerede bruger Microsoft Intune.

 Du kan finde flere [Microsoft 365 og Office 365 platformstjenestebeskrivelser](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>Forskelle i egenskaber

Microsoft Intune og indbygget Standardmobilitet og Sikkerhed giver dig både mulighed for at administrere mobilenheder i organisationen, men der er vigtige forskelle i funktionaliteten, som er beskrevet i følgende tabel.

> [!NOTE]
> Du kan administrere brugere og deres mobilenheder ved hjælp af både Intune og Basic Mobility and Security i samme Microsoft 365 Business Standard-organisation ved først at konfigurere Grundlæggende mobilitet og sikkerhed og derefter tilføje *Microsoft Intune*. Dette giver dig mulighed for at vælge Grundlæggende mobilitet og sikkerhed eller den mere funktionsrige Intune-løsning. Tildel en Intune-licens for at aktivere Intune-funktionerne.

| Funktionsområde | Fremhævninger af funktioner | Grundlæggende mobilitet og sikkerhed | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|Enhedstyper|Administration af forskellige OS-platforme og større administrationstilstandsvarianter. |Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|Windows<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS, iPad OS|
|Enhedsoverholdelse|Angiv og administrer sikkerhedspolitikker, f.eks. registrering af pinkodelås og jailbreak på enhedsniveau. |Begrænsninger på Android-enheder. Se [detaljer](capabilities.md). |Ja|
|Betinget adgang baseret på enhedsoverholdelse |Undgå ikke-kompilerende enheder i at få adgang til virksomhedens mail og data fra skyen. |Understøttes ikke på Windows 10.<br/>Begrænset til at kontrollere adgang til Exchange Online, SharePoint Online og Outlook. |Ja |
|Enhedskonfiguration  |Konfigurere enhedsindstillinger (f.eks. deaktivere kameraet)|Begrænset antal indstillinger.|Ja|
|Mailprofiler  |Klargør en oprindelig mailprofil på enheden. |Ja|Ja|
|WiFi-profiler |Klargør en indbygget WiFi-profil på enheden. |Nej|Ja|
|VPN-profiler |Klargør en oprindelig VPN-profil på enheden. |Nej|Ja|
|Administration af mobilapps  |Installér dine interne line of business-apps og fra apps stores til brugere. |Nej|Ja|
|Beskyttelse af mobilapps  |Giv dine brugere mulighed for at få sikker adgang til virksomhedens oplysninger ved hjælp af de Office-mobilapps og line of business-apps, de kender, og samtidig sikre sikkerheden for data ved at hjælpe med at begrænse handlinger som kopiér, klip, sæt ind og gem som, så der kun er de apps, der administreres, som er godkendt til virksomhedens data. Fungerer, selvom enhederne ikke er tilmeldt Grundlæggende mobilitet og sikkerhed. Se Beskyt appdata ved hjælp af MAM-politikker. |Nej|Ja|
|Administreret browser  |Aktivér mere sikker webbrowsing ved hjælp af Edge-appen. |Nej|Ja|
|Tilmeldingsprogrammer uden berøring (AutoPilot) |Tilmeld et stort antal enheder, der ejes af virksomheden, mens du forenkler brugerkonfigurationen. |Nej|Ja|
|||

Ud over de funktioner, der er angivet i den foregående tabel, inkluderer Grundlæggende mobilitet og sikkerhed og Intune begge et sæt fjernhandlinger, der sender kommandoer til enheder via internettet. Du kan f.eks. fjerne Office-data fra en medarbejders enhed, mens personlige data bliver på deres plads (tilbagetrækning), fjerne Office-apps fra en medarbejders enhed (slette) eller nulstille en enhed til fabriksindstillingerne (fuldstændig sletning).

Grundlæggende handlinger for mobilitet og sikkerhed omfatter tilbagetrækning, sletning og fuld sletning. Du kan finde flere oplysninger om handlinger for grundlæggende mobilitet og sikkerhed [under Egenskaber for grundlæggende mobilitet og sikkerhed](capabilities.md).

Med Intune har du følgende sæt handlinger:

-   Nulstilling af Autopilot (kun Windows
-  [BitLocker-tasterotation](/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)  (Windows kun)
-  [Brug sletning, tilbagetrækning eller manuel ophæftning af tilmeldingen af enheden](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
-  [Deaktiver aktiverings-loc](/mem/intune/remote-actions/device-activation-lock-disable)  (kun iOS)
-  [Frisk start](/mem/intune/remote-actions/device-fresh-start)  (Windows kun)
- [Fuld scanning](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  (kun Windows 10 oplysninger)
- [Find enhed](/mem/intune/remote-actions/device-locate)  (kun iOS)
- [Mistet tilstand](/mem/intune/remote-actions/device-lost-mode)  (kun iOS)- [Hurtig scanning](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(kun Windows 10)
- [Fjernbetjening til Android](/mem/intune/remote-actions/teamviewer-support)
- [Fjernlås](/mem/intune/remote-actions/device-remote-lock)
- [Omdøb enhed](/mem/intune/remote-actions/device-rename)
-  [Nulstil genstart](/mem/intune/remote-actions/device-passcode-reset) [af adgangskode](/mem/intune/remote-actions/device-restart)  (kun Windows adgangskode)
-  Opdater Windows Defender Security Intelligence (kun Windows)
-  Windows 10 nulstilling af pinkode (kun Windows)
-  [Send brugerdefinerede beskeder](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  (Android, iOS, iPad OS)
-  [Synkroniser enhed](/mem/intune/remote-actions/device-sync)

Du kan finde flere oplysninger om Intune-handlinger [Microsoft Intune dokumentationen](/mem/intune/).
