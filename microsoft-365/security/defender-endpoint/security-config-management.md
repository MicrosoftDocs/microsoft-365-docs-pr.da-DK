---
title: Administrer konfigurationsindstillinger for Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager
description: Få mere at vide om, hvordan du aktiverer sikkerhedsindstillinger Microsoft Endpoint Manager via Microsoft Defender til Slutpunkt.
keywords: enhedshåndtering, konfigurer Microsoft Defender til slutpunktsenheder, Microsoft Endpoint Manager
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.openlocfilehash: e21346b48f65016465e669369aa14b3f4c85c23b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593615"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Administrer konfigurationsindstillinger for Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Administrer Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



[!include[Prerelease information](../../includes/prerelease.md)]


> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Sikkerhedsadministration for Microsoft Defender til slutpunkt er en funktion til enheder, der ikke administreres af en Microsoft Endpoint Manager, hverken Microsoft Intune eller Microsoft Endpoint Configuration Manager, til at modtage sikkerhedskonfigurationer for Microsoft Defender direkte fra Endpoint Manager.


Du kan finde flere oplysninger om Sikkerhedskonfigurationsstyring, herunder forudsætninger, understøttede platforme og meget mere, under Administrer [Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).



[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Denne funktion udrulles gradvist. 

Du kan få mere at vide om Sikkerhedskonfiguration [under Administrer Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Hvis du støder på registreringsproblemer, skal du se [Fejlfinding i forbindelse med onboarding af sikkerhedskonfiguration.](troubleshoot-security-config-mgt.md)

> [!NOTE]
> Denne funktion gælder ikke for enheder, der allerede er tilmeldt Microsoft Endpoint Manager (enten Intune eller Konfigurationsstyring). Enheder, der er tilmeldt Intune, vil fortsat modtage politikker via deres etablerede administrationskanal.

## <a name="identify-onboarded-devices"></a>Identificer onboardede enheder

Brug følgende trin til at validere, om dine slutpunkter har fuldført sikkerhedsadministrationen af onboardingprocessen for Microsoft Defender til Slutpunkt.

1.  Kontrollér, at enheden vises i sektionen Lager over enheder [i Microsoft 365 Defender](https://security.microsoft.com/).

2.  I [Azure Active Directory skal](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/) du bekræfte, at enheden er blevet tilmeldt.

3.  I Microsoft Endpoint Manager [Administration skal](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview) du bekræfte, at enheden er blevet tilmeldt, ved at søge efter den i sektionen **Enheder > Alle** enheder.


## <a name="offboard-devices"></a>Offboard-enheder
Hvis du vil have offboard-enheder, der er blevet onboardet via Security Management til Microsoft Defender til slutpunkt, skal du se [Offboard-enheder fra Microsoft Defender for Endpoint-tjenesten](offboard-machines.md).

>[!NOTE]
>Offboarding [deaktiverer Manipulationsbeskyttelse,](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) hvis den er aktiveret.

## <a name="troubleshooting-security-management"></a>Fejlfinding af sikkerhedsadministration 
Hvis du vil foretage fejlfinding af sikkerhedsadministration for Microsoft Defender til registrering af slutpunkt, skal du se Fejlfinding i forbindelse med [onboardingproblemer i forbindelse med Sikkerhedsadministration for Microsoft Defender til Slutpunkt](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>Relateret emne
- [Fejlfinding af onboardingproblemer i forbindelse med Sikkerhedsadministration for Microsoft Defender til Slutpunkt](troubleshoot-security-config-mgt.md)
- [Administrer Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
