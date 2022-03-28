---
title: Integration med Microsoft Defender til skyen
description: Få mere at vide om Microsoft Defender til endpoint-integration med Microsoft Defender for Cloud
keywords: integration, server, azure, 2012r2, 2016, 2019, server onboarding, enhedsstyring, konfigurer Microsoft Defender til Slutpunktsservere, onboard Microsoft Defender til Slutpunktsservere, onboard Microsoft Defender til Endpoint-servere
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2ed9d25336cd7e8162849aa5d1d1a3e3382063fc
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596898"
---
# <a name="integration-with-microsoft-defender-for-cloud"></a>Integration med Microsoft Defender til skyen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender til skyen

Microsoft Defender til slutpunkt kan integreres med Microsoft Defender for Cloud for at give en omfattende Windows-serverbeskyttelsesløsning. Med denne integration kan Microsoft Defender til cloud bruge styrken fra Defender til Slutpunkt til at levere forbedret trusselsregistrering til Windows Servere.

Følgende funktioner er inkluderet i denne integration:

- Automatiseret onboarding – Defender til Endpoint-sensoren aktiveres automatisk på Windows-servere, der er onboardet til Microsoft Defender for Cloud. Du kan finde flere oplysninger om Microsoft Defender til cloud-onboarding [under Brug den integrerede Microsoft Defender til slutpunktslicens](/azure/security-center/security-center-wdatp).

    > [!NOTE]
    > Integrationen mellem Microsoft Defender for servere og Microsoft Defender for Endpoint er blevet udvidet til at [understøtte Windows Server 2019 og Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview).

- Windows servere, der overvåges af Microsoft Defender for Cloud, vil også være tilgængelige i Defender for Endpoint – Microsoft Defender for Cloud opretter problemfri forbindelse til Defender for Endpoint-lejeren og giver en enkelt visning på tværs af klienter og servere.  Derudover er Defender for Endpoint-beskeder tilgængelige i microsoft Defender for Cloud-konsollen.
- Serverundersøgelse – Microsoft Defender for Cloud-kunder kan få adgang til Microsoft 365 Defender-portalen og foretage detaljeret undersøgelse for at afdække omfanget af en potentiel misligholdelse.

> [!IMPORTANT]
> - Når du bruger Microsoft Defender for Cloud til at overvåge servere, oprettes automatisk en Defender for Endpoint-lejer (i USA for amerikanske brugere i EU for europæiske og engelske brugere).<br>
Data, der indsamles af Defender til Slutpunkt, gemmes på lejerens geoplacering, som identificeret under klargøring.
> - Hvis du bruger Defender til slutpunkt, før du bruger Microsoft Defender til skyen, gemmes dine data på den placering, du angav, da du oprettede din lejer, også selvom du integrerer med Microsoft Defender for Cloud på et senere tidspunkt.
> - Når det er konfigureret, kan du ikke ændre den placering, hvor dine data er gemt. Hvis du vil flytte dine data til en anden placering, skal du kontakte Microsoft Support for at nulstille lejeren. <br>
Serverslutpunktovervågning, der udnytter denne integration, er deaktiveret for Office 365 GCC kunder.



## <a name="related-topics"></a>Relaterede emner
- [Onboard tidligere versioner af Windows](onboard-downlevel.md)
- [Onboard Windows Server 2012 R2, 2016, DEN 1803 og 2019](configure-server-endpoints.md)
