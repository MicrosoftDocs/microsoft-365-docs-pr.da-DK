---
title: Microsoft Sikkerhedsscanner download
ms.reviewer: ''
description: Få værktøjet Microsoft Sikkerhedsscanner til at finde og fjerne malware fra Windows computere.
keywords: sikkerhed, malware
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 2f0e3fd84a9df907aa50339a1e3a2108d023db81
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706125"
---
# <a name="microsoft-safety-scanner-download"></a>Microsoft Sikkerhedsscanner download

Microsoft Sikkerhedsscanner er et scanningsværktøj, der er udviklet til at finde og fjerne malware Windows computere. Du skal blot downloade den og køre en scanning for at finde malware og forsøge at fortryde ændringer, der er foretaget af identificerede trusler.

- **[Download Microsoft Sikkerhedsscanner (32-bit)](https://go.microsoft.com/fwlink/?LinkId=212733)**

- **[Download Microsoft Sikkerhedsscanner (64-bit)](https://go.microsoft.com/fwlink/?LinkId=212732)**

> [!NOTE]
> Fra november 2019 bliver Sikkerhedsscanner kun signeret med SHA-2. Dine enheder skal opdateres til at understøtte SHA-2 for at køre Sikkerhedsscanner. Du kan få mere at vide [i 2019 SHA-2 Krav til understøttelse af signering af kode Windows og WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

## <a name="important-information"></a>Vigtige oplysninger

- Sikkerhedsintelligens-opdateringsversionen af Microsoft Sikkerhedsscanner svarer til den version, der [er beskrevet på denne webside](https://www.microsoft.com/wdsi/definitions).

- Sikkerhedsscanner scanner kun scanninger, når det udløses manuelt, og er tilgængeligt 10 dage efter, de er blevet downloadet. Vi anbefaler, at du altid downloader den nyeste version af dette værktøj før hver scanning.

- Sikkerhedsscanner er en bærbar eksekverbar fil og vises ikke i Windows menuen Start eller som et ikon på skrivebordet. Læg mærke til, hvor du gemte denne download.

- Dette værktøj erstatter ikke dit antimalwareprodukt. Du kan få beskyttelse i realtid med automatiske opdateringer [ved at Microsoft Defender Antivirus på Windows 11, Windows 10 og Windows 8](https://www.microsoft.com/windows/comprehensive-security) eller [Microsoft Security Essentials på Windows 7](https://support.microsoft.com/help/14210/security-essentials-download) . Disse antimalwareprodukter giver også effektive muligheder for fjernelse af malware. Hvis du har problemer med at fjerne malware med disse produkter, kan du henvise til vores hjælp til [at fjerne svære trusler](https://www.microsoft.com/wdsi/help/troubleshooting-infection).

## <a name="system-requirements"></a>Systemkrav

Sikkerhedsscanner hjælper med at fjerne skadelig software fra computere, der kører Windows 11, Windows 10, Windows 10 Tech Preview, Windows 8.1, Windows 8, Windows 7, Windows Server 2019, Windows Server 2016, Windows Server Tech Preview Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2 eller Windows Server 2008. Du kan finde flere oplysninger i [Microsofts politik for livscyklus](/lifecycle/).

## <a name="how-to-run-a-scan"></a>Sådan kører du en scanning

1. Download dette værktøj, og åbn det.
2. Vælg den type scanning, du vil køre, og start scanningen.
3. Gennemse de scanningsresultater, der vises på skærmen. Du kan finde detaljerede registreringsresultater i loggen **på %SYSTEMROOT%\debug\msert.log**.

Hvis du vil fjerne dette værktøj, skal du slette den eksekverbare fil (msert.exe som standard).

Du kan finde flere oplysninger om Sikkerhedsscanner i supportartikel om fejlfinding af problemer [med Sikkerhedsscanner](https://support.microsoft.com/kb/2520970).

## <a name="related-resources"></a>Relaterede ressourcer

- [Fejlfinding af sikkerhedsscanner](https://support.microsoft.com/help/2520970/how-to-troubleshoot-an-error-when-you-run-the-microsoft-safety-scanner)
- [Microsoft Defender Antivirus](https://www.microsoft.com/windows/comprehensive-security)
- [Microsoft Security Essentials](https://support.microsoft.com/help/14210/security-essentials-download)
- [Fjerne svære trusler](https://support.microsoft.com/help/4466982/windows-10-troubleshoot-problems-with-detecting-and-removing-malware)
- [Indsend fil til malwareanalyse](https://www.microsoft.com/wdsi/filesubmission)
- [Microsofts antimalware- og trusselsbeskyttelsesløsninger](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
