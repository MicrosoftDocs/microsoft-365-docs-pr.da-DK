---
title: Konfigurere administreret serviceudbyder support
description: Tag de nødvendige trin for at konfigurere MSSP-integration med Microsoft Defender for Endpoint
keywords: administreret sikkerheds serviceudbyder, mssp, konfigurer, integration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1a9a7e24bc08338549a78fcf9e9b2756701cd83f
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63597582"
---
# <a name="configure-managed-security-service-provider-integration"></a>Konfigurere administreret serviceudbyder integration

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Du skal følge disse konfigurationstrin for at aktivere den administrerede sikkerhedsintegration serviceudbyder (MSSP).

> [!NOTE]
> Følgende vilkår bruges i denne artikel til at skelne mellem serviceudbyder og forbruger af tjenester:
>
> - MSSP'er: Sikkerhedsorganisationer, der tilbyder at overvåge og administrere sikkerhedsenheder for en organisation.
> - MSSP-kunder: Organisationer, der involverer MSSP'ers tjenester.

Integrationen gør det muligt for MSSP'er at udføre følgende handlinger:

- Få adgang til MSSP-Microsoft 365 Defender portal
- Få mailbeskeder og
- Hente beskeder via sikkerhedsoplysninger og værktøjer til administration af begivenheder (SIEM)

Før MSSP'er kan udføre disse handlinger, skal MSSP-kunden give adgang til deres Defender for Endpoint-lejer, så MSSP'en kan få adgang til portalen.

MsSP-kunder tager typisk de indledende konfigurationstrin for at give MSSP'er adgang til deres Windows Defender Security Central-lejer. Når der tildeles adgang, kan andre konfigurationstrin udføres af MSSP-kunden eller MSSP'en.

Generelt skal der følgende konfigurationstrin:

- **Giv MSSP-adgang til Microsoft 365 Defender**

  Denne handling skal udføres af MSSP-kunden. Det giver MSSP-adgang til MSSP-kundens Defender for Endpoint-lejeren.

- **Konfigurere beskeder, der sendes til MSSP'er**

  Denne handling kan enten gøres af MSSP-kunden eller MSSP. På den måde kan MSSP'erne se, hvilke beskeder de skal adressere for MSSP-kunden.

- **Hent beskeder fra MSSP-kundens lejer i SIEM-systemet**

  Denne handling er foretaget af MSSP. Det gør det muligt for MSSP'er at hente beskeder i SIEM-værktøjer.

- **Hent beskeder fra MSSP-kundes lejer ved hjælp af API'er**

  Denne handling er foretaget af MSSP. Det gør det muligt for MSSP'er at hente beskeder ved hjælp af API'er.

## <a name="multi-tenant-access-for-mssps"></a>Adgang for flere lejere for MSSP'er

Du kan finde oplysninger om, hvordan du implementerer delegeret adgang for flere lejere under [Adgang for flere lejere til administrerede sikkerhedsudbydere](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440).

## <a name="related-topics"></a>Relaterede emner

- [Giv MSSP adgang til portalen](grant-mssp-access.md)
- [Få adgang til MSSP-kundeportalen](access-mssp-portal.md)
- [Konfigurere beskeder](configure-mssp-notifications.md)
- [Hent beskeder fra kundelejeren](fetch-alerts-mssp.md)
