---
title: Trin 3. Konfigurer politikker for overholdelse af angivne standarder for enheder med Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Få mere at vide om, hvordan du opretter politikker for enhedsoverholdelse, der angiver minimumskravene for, at en enhed kan få adgang til dit miljø.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: ae2866d2cabf21616b7aea74220dcf5ce8e4d4eb
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750292"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Trin 3. Konfigurer politikker for overholdelse af angivne standarder for enheder med Intune

Tilmelding af enheder til Intune giver dig mulighed for at opnå endnu større sikkerhed og kontrol over data i dit miljø. [Trin 2. Tilmeld enheder for at Intune](manage-devices-with-intune-enroll.md) oplysninger om, hvordan du opnår dette ved hjælp af Intune. I denne artikel beskrives næste trin, som er at konfigurere politikker for enhedens overholdelse af angivne standarder. 

![Trin til administration af enheder](../media/devices/intune-mdm-step-2.png#lightbox)

Du vil være sikker på, at enheder, der tilgår dine apps og data, opfylder minimumskravene, f.eks. at de er beskyttet med adgangskode eller pinkode, og at operativsystemet er opdateret. Politikker for overholdelse af regler og standarder er den måde, hvorpå du kan definere de krav, enhederne skal opfylde. MEM bruger disse politikker for overholdelse af angivne standarder til at markere en enhed som kompatibel eller ikke-kompatibel. Denne binære status overføres til Azure AD som kan bruge denne status i regler for betinget adgang til at tillade eller forhindre en enhed i at få adgang til ressourcer. 

## <a name="configuring-device-compliance-policies"></a>Konfiguration af politikker for enhedsoverholdelse

Denne vejledning er tæt koordineret med de anbefalede [Nul tillid politikker for identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

I denne illustration fremhæves det, hvor arbejdet med at definere politikker for overholdelse af regler og standarder passer ind i det overordnede Nul tillid anbefalede politiksæt. 

[![Nul tillid politikker for identitet og enhedsadgang](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

I denne illustration er definition af politikker for enhedsoverholdelse en afhængighed for at opnå det anbefalede beskyttelsesniveau inden for Nul tillid rammer. 

Hvis du vil konfigurere politikker for enhedsoverholdelse, skal du bruge den anbefalede vejledning og de indstillinger, der er foreskrevet i [Nul tillid politikker for identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Tabellen nedenfor linker direkte til instruktionerne til konfiguration af disse politikker i Intune, herunder de anbefalede indstillinger for hver platform.


|Politikker |Flere oplysninger  |Licensering |
|---------|---------|---------|
|[Definer politikker for enhedsoverholdelse ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Én politik for hver platform       |  Microsoft 365 E3 eller E5       |
|  |         |         |

## <a name="next-steps"></a>Næste trin

Gå til [trin 4. Kræv sunde og kompatible enheder](manage-devices-with-intune-require-compliance.md) for at få en vejledning i, hvordan du opretter reglen for betinget adgang i Azure AD.