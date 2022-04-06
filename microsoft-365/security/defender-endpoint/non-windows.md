---
title: Microsoft Defender for Endpoint til ikke-Windows platforme
description: Få mere Microsoft Defender for Endpoint om funktioner til ikke-Windows platforme
keywords: ikke windows, mac, macos, linux, android
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1dc7f7f29206b7944120bc2b494beec575313336
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632377"
---
# <a name="microsoft-defender-for-endpoint-for-non-windows-platforms"></a>Microsoft Defender for Endpoint til ikke-Windows platforme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1 og Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft har været på en rejse mod at udvide sine brancheførende sikkerhedsfunktioner til slutpunkter ud over Windows og Windows Server til macOS, Linux, Android og iOS.

Organisationer er stødt på trusler på tværs af en række platforme og enheder. Vores teams har forpligtet sig til at opbygge sikkerhedsløsninger, ikke kun *til* Microsoft, men også *fra Microsoft,* så vores kunder kan beskytte og sikre deres hetergene miljøer. Vi lytter til kundefeedback og samarbejder tæt med vores kunder om at opbygge løsninger, der opfylder deres behov.

Med Microsoft Defender for Endpoint kan kunder drage fordel af en samlet visning af alle trusler og beskeder i Microsoft 365 Defender-portalen på tværs Windows og ikke-Windows  platforme, så de kan få et fuldt billede af, hvad der sker i deres miljø, så de hurtigere kan vurdere og reagere på trusler.

## <a name="microsoft-defender-for-endpoint-on-macos"></a>Microsoft Defender for Endpoint på macOS

Microsoft Defender for Endpoint på macOS tilbyder antivirus, slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) og håndtering af sikkerhedsrisici  funktioner for de tre nyeste udgivne versioner af macOS. Kunder kan installere og administrere løsningen via Microsoft Endpoint Manager og Jamf. Ligesom med Microsoft Office på macOS bruges Microsoft Auto Update til at administrere opdateringer Microsoft Defender for Endpoint på Mac. Du kan finde oplysninger om de vigtigste funktioner og fordele ved at [læse vores meddelelser](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/macOS).

Hvis du vil have mere at vide om, hvordan du kommer i gang, skal du se dokumentationen til Defender for Endpoint på [macOS.](microsoft-defender-endpoint-mac.md)

> [!NOTE]
> Følgende funktioner understøttes i øjeblikket ikke på macOS-slutpunkter:
>
> - Forebyggelse af datatab
> - Sikkerhedsadministration til Microsoft Defender for Endpoint

## <a name="microsoft-defender-for-endpoint-on-linux"></a>Microsoft Defender for Endpoint på Linux

Microsoft Defender for Endpoint på Linux tilbyder forebyggelse af antivirus (AV), slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) og håndtering af sikkerhedsrisici funktioner til Linux-servere. Dette omfatter en komplet kommandolinjeoplevelse til konfiguration og administration af agenten, start scanninger og administration af trusler. Vi understøtter de seneste versioner af de seks mest almindelige Linux Server-distributioner: RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS eller nyere LTS, SLES 12+, Den 9+ og Oracle Linux 7.2. Microsoft Defender for Endpoint på Linux kan installeres og konfigureres ved hjælp af Programmer, Ansible eller ved hjælp af dit eksisterende Linux-konfigurationsadministrationsværktøj. Du kan finde oplysninger om de vigtigste funktioner og fordele ved at [læse vores meddelelser](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Linux).

Du kan finde flere oplysninger om, hvordan du kommer i gang, under Microsoft Defender for Endpoint om [Linux-dokumentation](microsoft-defender-endpoint-linux.md).


> [!NOTE]
> Følgende funktioner understøttes i øjeblikket ikke på Linux-slutpunkter:
>
> - Forebyggelse af datatab
> - Sikkerhedsadministration til Microsoft Defender for Endpoint

## <a name="microsoft-defender-for-endpoint-on-android"></a>Microsoft Defender for Endpoint på Android

Microsoft Defender for Endpoint Android er vores mobile forsvarsløsning til trusler til enheder, der kører Android 6.0 og nyere. Tilstandene Android Enterprise (Arbejdsprofil) og Enhedsadministrator understøttes. På Android tilbyder vi webbeskyttelse, som omfatter antiphishing, blokering af usikre forbindelser og indstilling af brugerdefinerede indikatorer. Løsningen søger efter malware og potentielt uønskede programmer (PUA) og tilbyder yderligere funktioner til forebyggelse af brud via integration med Microsoft Endpoint Manager og betinget adgang. Du kan finde oplysninger om de vigtigste funktioner og fordele ved at [læse vores meddelelser](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/bg-p/MicrosoftDefenderATPBlog/label-name/Android).

Du kan finde flere oplysninger om, hvordan du kommer i gang, under Microsoft Defender for Endpoint på [Android-dokumentationen](microsoft-defender-endpoint-android.md).

## <a name="microsoft-defender-for-endpoint-on-ios"></a>Microsoft Defender for Endpoint på iOS

Microsoft Defender for Endpoint iOS er vores mobile forsvarsløsning til trusler til enheder, der kører iOS 11.0 og nyere. Enheder, der er registreret i en kundes lejer (tilmeldt eller ikke tilmeldt), understøttes. Både overvågede og ikke-overvågede enheder understøttes. På iOS tilbyder vi webbeskyttelse, som omfatter antiphishing, blokering af usikre forbindelser og konfiguration af brugerdefinerede indikatorer og registrering af jailbreak. Du kan finde flere oplysninger om de vigtigste funktioner og fordele ved at [læse vores meddelelser](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bg-p/MicrosoftDefenderATPBlog/label-name/iOS).

Du kan finde flere oplysninger om, hvordan du kommer i gang, under Microsoft Defender for Endpoint om [iOS-dokumentationen](microsoft-defender-endpoint-ios.md).

## <a name="licensing-requirements"></a>Licenskrav

Berettigede brugere med licens kan bruge Microsoft Defender for Endpoint på op til fem samtidige enheder. Microsoft Defender for Endpoint kan også købes hos en Cloud Solution Provider (CSP).

Kunder kan få Microsoft Defender for Endpoint på macOS via en separat Microsoft Defender for Endpoint licens, som en del af Microsoft 365 A5/E5 eller Microsoft 365 Security.

De senest offentliggjorte Microsoft Defender for Endpoint på Android og iOS er inkluderet i de ovennævnte tilbud som en del af de fem kvalificerede enheder for berettigede brugere med licens.

Defender til Slutpunkt på Linux er tilgængelig via Defender for Endpoint Server SKU, der er tilgængelig for både kommercielle og uddannelseskunder.

Kontakt dit kontoteam eller din CSP for at få priser og yderligere berettigelseskrav.
