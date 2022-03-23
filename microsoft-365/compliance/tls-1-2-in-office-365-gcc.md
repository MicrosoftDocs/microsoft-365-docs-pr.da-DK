---
title: Deaktivering af TLS 1.0 og 1.1 i Microsoft 365 GCC High og DoD
description: Diskuterer, hvordan Microsoft deaktiverer understøttelse af TLS 1.1 og 1.0 i GCC High- og DoD-miljøer i Microsoft 365.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.collection: M365-security-compliance
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 29ee02c7c54fc7de6ee178f8219f7148a8cb4bfd
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63590085"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Deaktivering af TLS 1.0 og 1.1 i Microsoft 365 GCC High og DoD

## <a name="summary"></a>Oversigt

For at overholde de nyeste overholdelsesstandarder for Federal Risk and Authorization Management Program (FedRAMP) deaktiverer vi TLS-versionerne (Transport Layer Security) 1.1 og 1.0 i Microsoft 365 til GCC High- og DoD-miljøer. Denne ændring blev tidligere annonceret via Microsoft Support i forbindelse med forberedelse til [obligatorisk brug af TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Sikkerheden for dine data er vigtig, og vi er forpligtet til gennemsigtighed om ændringer, der kan påvirke din brug af tjenesten.

Selvom implementeringen [af Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) ikke har kendte sikkerhedsrisici, er vi forpligtet til at overholde FedRAMP-overholdelsesstandarderne. Derfor har vi deaktiveret TLS 1.1 og 1.0 i Microsoft 365 i GCC High and DoD-miljøer den 15. januar 2020. For information about how to remove TLS 1.1 and 1.0 dependencies, see the following white paper:

[Løsning af problemet med TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Flere oplysninger

Fra den 15. januar 2020 deaktiverer Microsoft 365 i GCC High- og DoD-miljøer TLS 1.1 og 1.0.

Pr. 15. januar 2020 skal alle kombinationer af klientservere og browserservere bruge TLS version 1.2 (eller en nyere version) for at sikre, at alle forbindelser kan oprettes uden problemer Microsoft 365. Dette kræver muligvis opdateringer til visse kombinationer af klientservere og browserservere.

For SharePoint og OneDrive skal du opdatere og konfigurere .NET til at understøtte TLS 1.2. Du kan få mere at [vide under Sådan aktiverer du TLS 1.2 på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Du skal opdatere klientcomputerne for at sikre, at du fortsat har uafbrudt adgang til Office 365 GCC High og DoD.

Du skal opdatere programmer, der kalder Microsoft 365 API'er over TLS 1.0 eller TLS 1.1 for at bruge TLS 1.2. .NET 4.5 bruger som standard TLS 1.1. Hvis du vil opdatere din .NET-konfiguration, skal du se Sådan aktiveres [TLS 1.2 (Transport Layer Security) på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Få mere at vide under [Forberedelse til obligatorisk brug af TLS 1.2 Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Vi ved, at følgende klientprogrammer ikke kan bruge TLS 1.2:

- Android 4.3 og tidligere versioner
- Firefox version 5.0 og tidligere versioner
- Internet Explorer 8-10 på Windows 7 og tidligere versioner
- Internet Explorer 10 på Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 og tidligere versioner

Selvom den aktuelle analyse af forbindelser til Microsoft Online-tjenester viser, at de fleste tjenester og slutpunkter kun ser lidt TLS 1.1- og 1.0-forbrug, giver vi besked om denne ændring, så du kan opdatere eventuelle påvirkede klienter eller servere efter behov, før understøttelse af TLS 1.1 og 1.0 stopper. Hvis du bruger en lokal infrastruktur til hybridscenarier eller AD FS (Active Directory Federation Services), skal du sørge for, at infrastrukturen kan understøtte både indgående og udgående forbindelser, der bruger TLS 1.2 (eller en nyere version).

Ud over de strømsvigt, du kan opleve, hvis du bruger de klienter, der ikke kan bruge TLS 1.2, vil fjernelse af TLS 1.1 og 1.0 forhindre dig i at kunne bruge følgende Microsoft-produkt:

- Lync-telefon

## <a name="references"></a>Referencer

Hvis du vil have vejledning og referencer til at sikre, at dine kunder bruger TLS 1.2, skal du se Forberedelse til obligatorisk brug af [TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).