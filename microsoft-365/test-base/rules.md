---
title: Program-/testregler
description: Regler, der skal følges, når du uploader et program/en test
search.appverid: MET150
author: andreicsibi-msft
ms.author: ancsibi
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 02/04/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: cebf888d7a17d6d589888d529cea1731b666f562
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63606824"
---
# <a name="applicationtest-rules"></a>Program-/testregler

Alle programmer eller test i Test Base skal overholde følgende regler:

## <a name="test-base-folders"></a>Test basemapper 

Følgende mapper bruges af testbaseinfrastrukturen:
* %SYSTEMDRIVE%\USL
* %SYSTEMDRIVE%\EtlExport
* %SYSTEMDRIVE%\Ffmpeg
* %SYSTEMDRIVE%\Monitoring
* %SYSTEMDRIVE%\powershell-yaml
* %SYSTEMDRIVE%\ProcMon
* %SYSTEMDRIVE%\PSTools
* %SYSTEMDRIVE%\TokenProviderTool
* %SYSTEMDRIVE%\USLPowershellModules
* %SYSTEMDRIVE%\UtcUtil
* %SYSTEMDRIVE%\WPT
* %SYSTEMDRIVE%\WULogs

> [!IMPORTANT]
> **Undgå følgende**:
> * Blokering af udførelse af en proces fra disse mapper. Hvis dit program er antimalwaresoftware, skal du konfigurere din appinstallation for at tillade utilsigtet udførelse af alle processer fra disse mapper.
> * Tæmme ved en af disse mapper.

## <a name="test-base-registry-keys"></a>Test af registreringsdatabasenøgler i grunddatabase

Programmerne/testene må ikke slette eller ændre registreringsdatabasenøgler i forbindelse med:
* Windows telemetriniveau
* Fjernelse af TLS 1.2
