---
title: Politikker for enhedsoverholdelse for dit Microsoft 365 til virksomhedstestmiljø
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Brug denne testlaboratorievejledning til at føje Intune politikker for enhedsoverholdelse til dit Microsoft 365 til virksomhedstestmiljøer.
ms.openlocfilehash: 3037ca846fe74fb8de51c78799e69c510821a034
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099449"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Politikker for enhedsoverholdelse for dit Microsoft 365 til virksomhedstestmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

I denne artikel beskrives det, hvordan du føjer en politik for Intune enhedens overholdelse af angivne standarder for Windows 10 enheder og Microsoft 365 Apps for enterprise til dit Microsoft 365 for virksomhedstestmiljø.

Tilføjelse af en politik for Intune enhedens overholdelse af angivne standarder omfatter to faser:
- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Opret en politik for enhedsoverholdelse for Windows 10 enheder](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du kun vil konfigurere MAM-politikker på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere MAM-politikker i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af automatiserede licenser og gruppemedlemskaber kræver ikke det simulerede testmiljø for virksomheder, hvilket omfatter et simuleret intranet, der er forbundet til internet- og mappesynkronisering for et AD DS-område (Active Directory-domæneservices). Det leveres her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskab og eksperimentere med det i et miljø, der repræsenterer en typisk organisation.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Fase 2: Opret en politik for enhedsoverholdelse for Windows 10 enheder

I denne fase skal du oprette en politik for enhedsoverholdelse for Windows 10 enheder. I denne fase bruges Microsoft Intune og [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) til at tilføje en gruppe og oprette en politik for overholdelse af angivne standarder.

1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com), log på dit Microsoft 365 testlaboratorium med din globale administratorkonto, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">Endpoint Manager Administration</a>.

    Hvis en meddelelse, der ligner **Du endnu ikke har aktiveret enhedshåndtering**, vises, skal du vælge Intune som MDM-autoritet. Du kan finde de specifikke trin under [Angiv autoritet for administration af mobilenheder](/mem/intune/fundamentals/mdm-authority-set).

    I Endpoint Manager Administration fokuseres der på enhedshåndtering og appadministration. Du kan få en præsentation af dette administrationscenter under [Selvstudium: Gennemgang Intune i Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. I **Grupper** skal du tilføje en ny **Microsoft 365**- eller **sikkerhedsgruppe** med navnet **Administreret Windows 10 enhedsbrugere** med en **tildelt** medlemskabstype. I de næste trin skal du tildele din politik for overholdelse af regler og standarder til denne gruppe. 

    Du kan finde de specifikke trin og oplysninger om **Microsoft 365**- eller **sikkerhedsgrupper** under [Tilføj grupper for at organisere brugere og enheder](/mem/intune/fundamentals/groups-add).

3. Opret en politik for overholdelse af Windows 10 i **Enheder**. Tildel denne politik til gruppen **Administrerede Windows 10 enhedsbrugere**, du har oprettet.

    I din politik kan du blokere simple adgangskoder, kræve en firewall, kræve, at Microsoft Defender Antimalware-tjenesten kører og meget mere. En politik for overholdelse af angivne standarder indeholder typisk de grundlæggende indstillinger eller et minimum, som alle enheder skal have.

    Du kan finde oplysninger om de specifikke trin og de tilgængelige indstillinger for overholdelse af angivne standarder, du kan konfigurere, under [Brug politikker for overholdelse af regler og standarder til at angive regler for enheder, du administrerer](/mem/intune/protect/device-compliance-get-started).

Når du er færdig, har du en politik for enhedsoverholdelse til test af medlemmer i gruppen **Administrerede Windows 10 enhedsbrugere**.
  
## <a name="next-step"></a>Næste trin

Udforsk yderligere funktioner og funktioner til [administration af mobilenheder](m365-enterprise-test-lab-guides.md#mobile-device-management) i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md).
  
[Tilmeld iOS- og Android-enheder i dit Microsoft 365 til virksomhedstestmiljøer](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
