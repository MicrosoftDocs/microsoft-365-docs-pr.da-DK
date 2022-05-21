---
title: Administrer konfigurationsindstillinger for Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager
description: Få mere at vide om, hvordan du aktiverer sikkerhedsindstillinger i Microsoft Endpoint Manager via Microsoft Defender for Endpoint.
keywords: enhedshåndtering, konfigurere Microsoft Defender for Endpoint enheder Microsoft Endpoint Manager
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
ms.openlocfilehash: 7e9e074e4aeaadf041a70baed1d741ea95a9f792
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622605"
---
# <a name="manage-microsoft-defender-for-endpoint-configuration-settings-on-devices-with-microsoft-endpoint-manager"></a>Administrer konfigurationsindstillinger for Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)


Sikkerhedsadministration for Microsoft Defender for Endpoint er en funktion for enheder, der ikke administreres af en Microsoft Endpoint Manager, enten Microsoft Intune eller Microsoft Endpoint Configuration Manager, hvis du vil modtage sikkerhedskonfigurationer til Microsoft Defender direkte fra Endpoint Manager.


Du kan få flere oplysninger om Administration af sikkerhedskonfiguration, herunder forudsætninger, understøttede platforme og meget mere, under [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Se denne video for at få mere at vide om, hvordan du bruger Microsoft Endpoint Manager til at administrere sikkerhedskonfiguration for Microsoft Defender for Endpoint.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVq]

[!INCLUDE [Prerequisites](../../includes/security-config-mgt-prerequisites.md)]

>[!NOTE]
>Denne funktion udrulles gradvist. 

Du kan få flere oplysninger om administration af sikkerhedskonfiguration under [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Hvis du støder på problemer med tilmelding, skal du se [Fejlfinding af onboardingproblemer i administration af sikkerhedskonfiguration](troubleshoot-security-config-mgt.md).

> [!NOTE]
> Denne funktion gælder ikke for enheder, der allerede er tilmeldt Microsoft Endpoint Manager (enten Intune eller Configuration Manager). Enheder, der er tilmeldt Intune, modtager fortsat politikker via deres etablerede administrationskanal.

## <a name="identify-onboarded-devices"></a>Identificer onboardede enheder

Brug følgende trin til at validere, at dine slutpunkter har fuldført sikkerhedsadministrationen for Microsoft Defender for Endpoint onboardingproces.

1.  Kontrollér, at enheden vises i afsnittet Enhedslager [i Microsoft 365 Defender](https://security.microsoft.com/).

2.  Kontrollér, at enheden er tilmeldt, på [Azure Active Directory-portalen](https://aad.portal.azure.com/#blade/Microsoft_AAD_Devices/DevicesMenuBlade/Devices/menuId/).

3.  I [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/#blade/Microsoft_Intune_DeviceSettings/DevicesMenu/mDMDevicesPreview) skal du kontrollere, at enheden er blevet tilmeldt, ved at slå den op i afsnittet **Enheder > Alle enheder**.


## <a name="offboard-devices"></a>Offboard-enheder
For offboard-enheder, der er onboardet via Sikkerhedsadministration for Microsoft Defender for Endpoint, skal du se [Offboard-enheder fra Microsoft Defender for Endpoint-tjenesten](offboard-machines.md).

>[!NOTE]
>Offboarding [deaktiverer Tamper Protection](prevent-changes-to-security-settings-with-tamper-protection.md#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal) , hvis den er aktiveret.

## <a name="troubleshooting-security-management"></a>Fejlfinding af sikkerhedsadministration 
Hvis du vil foretage fejlfinding af sikkerhedsadministration for Microsoft Defender for Endpoint problemer med tilmelding, skal du se [Fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).

## <a name="related-topic"></a>Relateret emne
- [Foretag fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md)
- [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-mde-security-configuration-management)
