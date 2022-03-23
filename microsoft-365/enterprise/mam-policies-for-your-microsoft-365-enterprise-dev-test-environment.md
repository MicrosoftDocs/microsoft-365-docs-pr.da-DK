---
title: Politikker for enhedsoverholdelse for Microsoft 365 til virksomhedstestmiljø
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Brug denne Test Lab-vejledning til at føje politikker for overholdelse af enhed i Intune til Microsoft 365 for Enterprise Test Environment.
ms.openlocfilehash: ec73211a21e9e064b729b93d9e88b7c5c69b21fe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589496"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Politikker for enhedsoverholdelse for Microsoft 365 til virksomhedstestmiljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

I denne artikel beskrives det, hvordan du føjer en Politik for overholdelse af intune-enhed til Windows 10-enheder og Microsoft 365 Apps for enterprise til dine Microsoft 365 til virksomhedstestmiljø.

Tilføjelse af en Politik for overholdelse af enhed i Intune omfatter to faser:
- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Opret en politik for enhedsoverholdelse for Windows 10 enheder](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du kun vil konfigurere MAM-politikker på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere MAM-politikker i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af automatiseret licensering og gruppemedlemskab kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS)-skov. Den findes her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskaber og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Fase 2: Opret en politik for enhedsoverholdelse for Windows 10 enheder

I denne fase opretter du en politik for enhedsoverholdelse for Windows 10 enheder. I denne fase Microsoft Intune administration Microsoft Endpoint Manager [til at](https://go.microsoft.com/fwlink/?linkid=2109431) tilføje en gruppe og oprette en politik for overholdelse af regler og standarder.

1. Gå [til Microsoft 365 Administration,](https://admin.microsoft.com) log på dit Microsoft 365 test lab-abonnement med din globale administratorkonto, og vælg Endpoint Manager <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">Administration</a>.

    Hvis en meddelelse, der **ligner Du ikke** har aktiveret administration af enheder, endnu vises, skal du vælge Intune som MDM-myndighed. Se de specifikke trin under [Angiv administrationscenteret for mobilenheder](/mem/intune/fundamentals/mdm-authority-set).

    Administration Endpoint Manager fokuserer på administration af enheder og appadministration. Du kan få en rundvisning i denne Administration [i Selvstudium: Gennemgang intune Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. I **Grupper** skal du tilføje en **ny Microsoft 365** eller **sikkerhedsgruppe** med **navnet Administrerede Windows 10** brugere af enheder med en **Tildelt** medlemskabstype. I de næste trin skal du tildele overholdelsespolitikken til denne gruppe. 

    Hvis du vil have mere at vide om specifikke trin **Microsoft 365** grupper eller **Sikkerhedsgrupper**, skal du [se Tilføj grupper for at organisere brugere og enheder](/mem/intune/fundamentals/groups-add).

3. Opret **en** politik for overholdelse Windows 10 Enheder. Tildel denne politik til gruppen **Administrerede Windows 10 brugere,** du har oprettet.

    I din politik kan du blokere simple adgangskoder, kræve en firewall, kræve, at Microsoft Defender Antimalware-tjenesten kører og meget mere. En politik for overholdelse omfatter typisk de grundlæggende indstillinger eller et minimum, som hver enhed skal have.

    For de specifikke trin og for at få oplysninger om de tilgængelige indstillinger for overholdelse, du kan konfigurere, skal du se Brug politikker for overholdelse af regler og standarder [til at angive regler for enheder, du administrerer](/mem/intune/protect/device-compliance-get-started).

Når du er færdig, har du en politik for enhedsoverholdelse til test af medlemmer i **gruppen administrerede Windows 10 af** enheder.
  
## <a name="next-step"></a>Næste trin

Udforsk yderligere [funktioner til administration af](m365-enterprise-test-lab-guides.md#mobile-device-management) mobilenheder samt funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab Guides](m365-enterprise-test-lab-guides.md).
  
[Tilmeld iOS- og Android-enheder i dit Microsoft 365 virksomhedstestmiljø](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
