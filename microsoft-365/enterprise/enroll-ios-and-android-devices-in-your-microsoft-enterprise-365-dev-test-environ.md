---
title: Tilmeld iOS-/iPadOS- og Android-enheder i Microsoft 365 til virksomhedens testmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Brug denne Test Lab-vejledning til at tilmelde enheder i dit Microsoft 365 testmiljø og administrere dem eksternt.
ms.openlocfilehash: 7610348febcc8c2054c50d7f7a6f1433e9b62306
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587248"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Tilmeld iOS- og Android-enheder i dit Microsoft 365 virksomhedstestmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

I denne artikel beskrives det, hvordan du tilmelder og tester grundlæggende funktioner til administration af mobilenheder til iOS/iPadOS og Android-enheder i dit Microsoft 365 til virksomhedstestmiljø.

Tilmelding af iOS-/iPadOS- og Android-enheder i dit testmiljø omfatter tre faser:
- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Tilmeld dine iOS-/iPadOS- og Android-enheder](#phase-2-enroll-your-ios-and-android-devices)
- [Fase 3: Administrer dine iOS/iPadOS- og Android-enheder eksternt](#phase-3-manage-your-ios-and-android-devices-remotely)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du let vil tilmelde iOS/iPadOS- og Android-enheder på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil tilmelde iOS-/iPadOS- og Android-enheder i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af automatiseret licensering og gruppemedlemskab kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS)-skov. Den leveres her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskaber, og du kan eksperimentere med den i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Tilmeld dine iOS- og Android-enheder

Hvis du overvejer en løsning til administration af mobilenheder (MDM), til at administrere dine enheder, kan du Microsoft Intune. Når du arbejder med en MDM-udbyder, herunder Intune, bliver enhederne "tilmeldt". Når de er tilmeldt, modtager de de funktioner og indstillinger, du konfigurerer. 

I Intune er der et par måder, hvorpå du kan tilmelde dine iOS-/iPadOS- og Android-enheder. Du kan vælge den registreringsindstilling, der fungerer bedst for din organisation. Du kan finde flere oplysninger og vejledning i følgende artikler:

- [Installationsvejledning: Tilmeld iOS- og iPadOS-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Installationsvejledning: Tilmeld Android-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Hvis du er klar til at bruge Intune til administration af enheder, og du vil have vejledning, kan følgende oplysninger være en hjælp:

- [Oversigt over enhedshåndtering](/mem/intune/fundamentals/what-is-device-management)
- [Selvstudium: Intune med gennemgang Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Installationsvejledning: Konfiguration eller flytning til Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Fase 3: Administrer dine iOS- og Android-enheder eksternt

Microsoft Intune har funktion til nulstilling af fjernlås og adgangskode. Hvis en person mister sin enhed, kan du låse enheden fra en fjernenhed. Hvis nogen glemmer deres adgangskode, kan du nulstille den eksternt.

- Hvis du vil låse en iOS/iPadOS- eller Android-enhed eksternt, skal du se [Lås enheder eksternt med Intune](/mem/intune/remote-actions/device-remote-lock).
- Hvis du vil nulstille adgangskoden eksternt, skal du [se Nulstille eller fjerne en enhedsadgangskode i Intune](/mem/intune/remote-actions/device-passcode-reset).

Hvis du har flere opgaver, du kan køre fra en fjernforbindelse, skal [du se tilgængelige enhedshandlinger](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Næste trin

Udforsk yderligere [funktioner til administration af](m365-enterprise-test-lab-guides.md#mobile-device-management) mobilenheder samt funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)
  
[Politikker for enhedsoverholdelse for Microsoft 365 til virksomhedstestmiljø](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)
