---
title: Deaktivering af TLS 1.0 og 1.1 i Microsoft 365 GCC High og DoD
description: Beskriver, hvordan Microsoft deaktiverer understøttelse af TLS 1.1 og 1.0 i GCC High- og DoD-miljøer i Microsoft 365.
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
ms.openlocfilehash: bad0dc997f2c564670858d2ac35b2cd3177e0578
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760377"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Deaktivering af TLS 1.0 og 1.1 i Microsoft 365 GCC High og DoD

## <a name="summary"></a>Oversigt

For at overholde de seneste standarder for overholdelse af FedRAMP (Federal Risk and Authorization Management Program) deaktiverer vi TLS-version 1.1 og 1.0 (Transport Layer Security) i Microsoft 365 til GCC high- og dod-miljøer. Denne ændring blev tidligere annonceret via Microsoft Support i [Forberedelse til obligatorisk brug af TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Sikkerheden af dine data er vigtig, og vi er forpligtet til gennemsigtighed omkring ændringer, der kan påvirke din brug af tjenesten.

Selvom [implementeringen af Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) ikke har nogen kendte sikkerhedsrisici, er vi fortsat forpligtet til at overholde FedRAMP-standarderne. Derfor deaktiverede vi TLS 1.1 og 1.0 i Microsoft 365 i GCC High- og DoD-miljøer den 15. januar 2020. Du kan få oplysninger om, hvordan du fjerner TLS 1.1- og 1.0-afhængigheder, i følgende whitepaper:

[Løsning af TLS 1.0-problemet](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Flere oplysninger

Fra og med den 15. januar 2020 deaktiverer Microsoft 365 i GCC High- og DoD-miljøer TLS 1.1 og 1.0.

Fra den 15. januar 2020 skal alle kombinationer af klientservere og browserservere bruge TLS version 1.2 (eller en nyere version) for at sikre, at alle forbindelser kan oprettes uden problemer for Microsoft 365. Dette kan kræve opdateringer af visse kombinationer af klientservere og browserservere.

Hvis du vil have SharePoint og OneDrive, skal du opdatere og konfigurere .NET til at understøtte TLS 1.2. Du kan få flere oplysninger under [Sådan aktiverer du TLS 1.2 på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Du skal opdatere klientcomputerne for at sikre, at du bevarer uafbrudt adgang til Office 365 GCC High og DoD.

Du skal opdatere programmer, der kalder Microsoft 365 API'er over TLS 1.0 eller TLS 1.1, for at bruge TLS 1.2. .NET 4.5 er som standard TLS 1.1. Hvis du vil opdatere din .NET-konfiguration, skal du se [Sådan aktiverer du TLS 1.2 (Transport Layer Security) på klienter](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Du kan finde flere oplysninger under [Forberedelse til obligatorisk brug af TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Vi ved, at følgende klientprogrammer ikke kan bruge TLS 1.2:

- Android 4.3 og tidligere versioner
- Firefox version 5.0 og tidligere versioner
- Internet Explorer 8-10 på Windows 7 og tidligere versioner
- Internet Explorer 10 den Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 og tidligere versioner

Selvom den aktuelle analyse af forbindelser til Microsoft Online-tjenester viser, at de fleste tjenester og slutpunkter kun ser lidt brug af TLS 1.1 og 1.0, bemærker vi denne ændring, så du kan opdatere alle berørte klienter eller servere efter behov, før supporten til TLS 1.1 og 1.0 slutter. Hvis du bruger en infrastruktur i det lokale miljø til hybride scenarier eller Active Directory Federation Services (AD FS), skal du sørge for, at infrastrukturen kan understøtte både indgående og udgående forbindelser, der bruger TLS 1.2 (eller en nyere version).

Ud over de afbrydelser, du kan opleve, hvis du bruger de angivne klienter, der ikke kan bruge TLS 1.2, vil fjernelse af TLS 1.1 og 1.0 forhindre dig i at bruge følgende Microsoft-produkt:

- Lync-telefon

## <a name="references"></a>Referencer

Hvis du vil have hjælp og referencer til at sikre, at dine klienter bruger TLS 1.2, skal du se [Forberedelse til obligatorisk brug af TLS 1.2 i Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
