---
title: Tilmeld iOS-/iPadOS- og Android-enheder i dit Microsoft 365 til virksomhedstestmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Brug denne testvejledning til at tilmelde enheder i dit Microsoft 365 testmiljø og administrere dem eksternt.
ms.openlocfilehash: 5cefabf6b995754f6febe117776ad2de97443df0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092927"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Tilmeld iOS- og Android-enheder i dit Microsoft 365 til virksomhedstestmiljøer

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

I denne artikel beskrives det, hvordan du tilmelder og tester grundlæggende funktioner til administration af mobilenheder til iOS-/iPadOS- og Android-enheder i dit Microsoft 365 til virksomhedstestmiljø.

Tilmelding af iOS-/iPadOS- og Android-enheder i dit testmiljø omfatter tre faser:
- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Tilmeld dine iOS-/iPadOS- og Android-enheder](#phase-2-enroll-your-ios-and-android-devices)
- [Fase 3: Fjernstyring af dine iOS-/iPadOS- og Android-enheder](#phase-3-manage-your-ios-and-android-devices-remotely)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du vil tilmelde iOS-/iPadOS- og Android-enheder på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af Letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil tilmelde iOS-/iPadOS- og Android-enheder i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af automatiserede licenser og gruppemedlemskaber kræver ikke det simulerede testmiljø for virksomheder, hvilket omfatter et simuleret intranet, der er forbundet til internet- og mappesynkronisering for et AD DS-område (Active Directory-domæneservices). Det leveres her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskab, og du kan eksperimentere med det i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Fase 2: Tilmeld dine iOS- og Android-enheder

Hvis du overvejer en MDM-løsning (Mobile Device Management) til administration af dine enheder, kan du bruge Microsoft Intune. Når du arbejder med en MDM-udbyder, herunder Intune, "tilmeldes enheder". Når de er tilmeldt, modtager de de funktioner og indstillinger, du konfigurerer. 

I Intune er der et par måder at tilmelde dine iOS-/iPadOS- og Android-enheder på. Du kan vælge den tilmeldingsindstilling, der fungerer bedst for din organisation. Du kan finde flere oplysninger og vejledning i følgende artikler:

- [Installationsvejledning: Tilmeld iOS- og iPadOS-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Installationsvejledning: Tilmeld Android-enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Hvis du er klar til at bruge Intune til enhedshåndtering og vil have vejledning, kan følgende oplysninger muligvis hjælpe:

- [Oversigt over enhedshåndtering](/mem/intune/fundamentals/what-is-device-management)
- [Selvstudium: Gennemgang Intune i Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Installationsvejledning: Konfigurer eller flyt til Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Fase 3: Fjernstyring af dine iOS- og Android-enheder

Microsoft Intune indeholder en funktion til fjernlås og nulstilling af adgangskode. Hvis en person mister sin enhed, kan du fjernlåse enheden. Hvis nogen glemmer sin adgangskode, kan du fjernnulstille den.

- Hvis du vil låse en iOS-/iPadOS- eller Android-enhed eksternt, skal du se [Fjernlåse enheder med Intune](/mem/intune/remote-actions/device-remote-lock).
- Hvis du vil nulstille adgangskoden eksternt, skal du se [Nulstil eller fjern en enhedsadgangskode i Intune](/mem/intune/remote-actions/device-passcode-reset).

Hvis du vil have flere opgaver, du kan køre eksternt, skal du se [tilgængelige enhedshandlinger](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Næste trin

Udforsk yderligere funktioner og funktioner til [administration af mobilenheder](m365-enterprise-test-lab-guides.md#mobile-device-management) i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)
  
[Politikker for enhedsoverholdelse for dit Microsoft 365 til virksomhedstestmiljø](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)
