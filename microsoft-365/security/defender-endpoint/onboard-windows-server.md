---
title: Defender for Endpoint onboarding Windows Server
description: Onboard Windows Server til Microsoft Defender for Endpoint.
keywords: onboarding, Microsoft Defender for Endpoint onboarding, sccm, gruppepolitik, mdm, lokalt script, registreringstest
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b25d60be243dd5d375fb6ed0f795e4a901a504b2
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858871"
---
# <a name="defender-for-endpoint-onboarding-windows-server"></a>Defender for Endpoint onboarding Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server Semi-Annual Enterprise Channel
- Windows Server 2019 og nyere
- Windows Server 2019 Core Edition
- Windows Server 2022
- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https:%2F%2Faka.ms%2FMDEp2OpenTrial)

Du skal gennemgå onboardingsektionen på Defender for Endpoint-portalen for at onboarde en hvilken som helst af de understøttede enheder. Afhængigt af enheden får du vejledning med de relevante trin og de indstillinger for administrations- og udrulningsværktøj, der passer til enheden.

Defender for Endpoint udvider understøttelsen til også at omfatte Windows Server-operativsystemet. Denne understøttelse leverer problemfrit avancerede funktioner til registrering og undersøgelse af angreb via Microsoft 365 Defender-konsollen. Understøttelse af Windows Server giver bedre indsigt i serveraktiviteter, dækning af registrering af kerne- og hukommelsesangreb og aktiverer svarhandlinger.

I dette emne beskrives det, hvordan du onboarder specifikke Windows-servere for at Microsoft Defender for Endpoint.

Du kan finde en vejledning i, hvordan du downloader og bruger Windows Sikkerhed Baselines til Windows-servere, [under Windows Sikkerhed Baselines.](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-baselines)

## <a name="windows-server-onboarding-overview"></a>Oversigt over onboarding af Windows Server

Du skal fuldføre følgende generelle trin for at onboarde servere 2008 R2, 2012 R2, 2016, 2019, 2022.

:::image type="content" source="images/server-onboarding.png" alt-text="Server Onboarding" lightbox="images/server-onboarding.png":::

> [!NOTE]
> Servere om bord bruger kun GP'er.

### <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 og Windows Server 2016
- Download installations- og onboardingpakker.
- Anvend installationspakken.
- Følg onboardingtrinnene for det tilsvarende værktøj.

### <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019"></a>Windows Server Semi-Annual Enterprise Channel og Windows Server 2019
- Download onboardingpakken.
- Følg onboardingtrinnene for det tilsvarende værktøj.

> [!IMPORTANT]
> For at være berettiget til at købe Microsoft Defender for Endpoint Server SKU skal du allerede have købt et kombineret minimum af følgende, Windows E5/A5, Microsoft 365 E5/A5 eller Microsoft 365 E5 Sikkerhed abonnementslicenser. Du kan få flere oplysninger om licenser under [Produktvilkår](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).

## <a name="offboard-windows-servers"></a>Windows-servere uden for bord

Du kan offboard Windows Server 2012 R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 og Windows Server 2019 Core edition med den samme metode, der er tilgængelig for Windows 10 klientenheder.

- [Offboard-enheder, der bruger Configuration Manager](/microsoft-365/security/defender-endpoint/configure-endpoints-sccm#offboard-devices-using-configuration-manager)
- [Offboard og overvåg enheder ved hjælp af værktøjer til Enhedshåndtering til mobilenheder](/microsoft-365/security/defender-endpoint/configure-endpoints-mdm#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [Offboard-enheder, der bruger Gruppepolitik](/microsoft-365/security/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy)
- [Offboard-enheder, der bruger et lokalt script](/microsoft-365/security/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script)

Efter offboarding kan du fortsætte med at fjerne den samlede løsningspakke på Windows Server 2012 R2 og Windows Server 2016.

I forbindelse med andre Windows-serverversioner har du to muligheder for at komme uden for Windows-servere fra tjenesten:
- Fjern MMA-agenten
- Fjern konfigurationen af Defender for Slutpunktarbejdsområde

> [!NOTE]
> Disse instruktioner til offboarding til andre Windows-serverversioner gælder også, hvis du kører den tidligere Microsoft Defender for Endpoint til Windows Server 2016 og Windows Server 2012 R2, der kræver MMA. Instruktioner til migrering til den nye samlede løsning finder du [i Server migrationsscenarier i Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Relaterede emner

- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
