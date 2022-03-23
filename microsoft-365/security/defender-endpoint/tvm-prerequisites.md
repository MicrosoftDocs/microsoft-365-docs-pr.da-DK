---
title: Forudsætninger & tilladelser – Håndtering af trusler og sikkerhedsrisici
description: Før du begynder at Håndtering af trusler og sikkerhedsrisici, skal du sørge for, at du har de relevante konfigurationer og tilladelser.
keywords: forudsætninger & håndtering af sikkerhedsrisici for tilladelser, Håndtering af trusler og sikkerhedsrisici tilladelser, forudsætninger for Microsoft Defender til Endpoint TVM, håndtering af sikkerhedsrisici
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 343a5fd1033a6d954c7cd62e2558a4b401f69b20
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591266"
---
# <a name="prerequisites--permissions---threat-and-vulnerability-management"></a>Forudsætninger & tilladelser – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Sørg for, at dine enheder:

- Er onboardet til Microsoft Defender til Slutpunkt

- Kør [understøttede operativsystemer og platforme](tvm-supported-os.md)

- Få følgende obligatoriske opdateringer installeret og installeret i dit netværk for at øge registreringshastighederne for din vurdering af sikkerhedsrisikoen:

  > Udgivelse | Kb-nummer og kæde til sikkerhedsopdatering
  > :---|:---
  > Windows 10 version 1709 | [KB4493441](https://support.microsoft.com/help/4493441/windows-10-update-kb4493441) [og KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
  > Windows 10 version 1803 | [KB4493464](https://support.microsoft.com/help/4493464) [og KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
  > Windows 10 version 1809 | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
  > Windows 10 version 1903 | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)

- Er onboardet til [Microsoft Intune og](/mem/intune/fundamentals/what-is-intune) [Microsoft Endpoint Configuration Manager hjælpe med](/mem/configmgr/protect/deploy-use/endpoint-protection-configure) at løse trusler, der findes af Håndtering af trusler og sikkerhedsrisici. Hvis du bruger en Konfigurationsstyring, skal du opdatere din konsol til den nyeste version.

  > [!NOTE]
  > Hvis du har aktiveret Intune-forbindelsen, får du mulighed for at oprette en Intune-sikkerhedsopgave, når du opretter en afhjælpningsanmodning. Denne indstilling vises ikke, hvis der ikke er angivet en forbindelse.

- Have mindst én sikkerhedsanbefaling, der kan vises på enhedssiden

- Mærkes eller markeres som administreret af andre

## <a name="relevant-permission-options"></a>Relevante tilladelsesindstillinger

1. Log på Microsoft 365 Defender via konto med en sikkerhedsadministrator eller tildelt global administratorrolle.
2. I **navigationsruden skal du vælge Indstillinger > slutpunkter > roller**.

Få mere at vide under [Opret og administrer roller for rollebaseret adgangskontrol](user-roles.md).

### <a name="view-data"></a>Vis data

- **Sikkerhedshandlinger** – Få vist alle data for sikkerhedshandlinger i portalen
- **Trussel og håndtering af sikkerhedsrisici** – vis Håndtering af trusler og sikkerhedsrisici data på portalen

### <a name="active-remediation-actions"></a>Aktive afhjælpningshandlinger

- **Sikkerhedshandlinger** – udføre svarhandlinger, godkende eller afvise afventende afhjælpningshandlinger, administrere tilladte/blokerede lister til automatisering og indikatorer
- **Trussel og håndtering af sikkerhedsrisici – Håndtering af undtagelser** – Oprette nye undtagelser og administrere aktive undtagelser
- **Trussels- håndtering af sikkerhedsrisici afhjælpning –** Indsend nye afhjælpningsanmodninger, opret billetter, og administrer eksisterende afhjælpningsaktiviteter

Du kan finde flere oplysninger under [Indstillinger for RBAC-tilladelser](user-roles.md#permission-options)

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Understøttede operativsystemer og platforme](tvm-supported-os.md)
- [Tildel enhedsværdi](tvm-assign-device-value.md)
- [Trussels- håndtering af sikkerhedsrisici dashboard](tvm-dashboard-insights.md)

