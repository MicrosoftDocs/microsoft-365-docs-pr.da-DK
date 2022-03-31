---
title: Trin 3. Konfigurer politikker for overholdelse af regler og standarder for enheder med Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: Få mere at vide om, hvordan du opretter politikker for enhedsoverholdelse, der angiver minimumskravene for en enhed til at få adgang til dit miljø.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 7e55ad6bf1d1cb7d95e43cb23b9c74decc8548df
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/14/2022
ms.locfileid: "63601047"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>Trin 3. Konfigurer politikker for overholdelse af regler og standarder for enheder med Intune

Registrering af enheder i administration giver dig mulighed for at opnå endnu større sikkerhed og kontrol over data i dit miljø. [Trin 2. Tilmeld enheder til administrationsoplysninger,](manage-devices-with-intune-enroll.md) hvordan du gør dette ved hjælp af Intune og Autopilot. Denne artikel omhandler det næste trin, som er at konfigurere politikker for enhedsoverholdelse. 

![Trin til administration af enheder](../media/devices/intune-mdm-step-2.png#lightbox)

Du skal være sikker på, at enheder, der har adgang til dine apps og data, opfylder minimumskravene, f.eks. at de er beskyttet med adgangskode eller pinkode, og at operativsystemet er opdateret. Politikker for overholdelse af regler og standarder er den måde, hvorpå du kan definere de krav, som enhederne skal opfylde. MEM bruger disse overholdelsespolitikker til at markere en enhed som kompatibel eller ikke-kompatibel Denne binære status overføres til Azure AD, som kan bruge denne status i regler for betinget adgang til at tillade eller forhindre en enhed i at få adgang til ressourcer. 

## <a name="configuring-device-compliance-policies"></a>Konfiguration af politikker for enhedsoverholdelse

Denne vejledning er tæt koordineret med de anbefalede politikker for [Nul tillid til identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

Denne illustration fremhæver, hvor arbejdet med at definere overholdelsespolitikker passer ind i det overordnede politiksæt, der anbefales af Zero Trust. 

[![Politikker for nultillidshed og enhedsadgang](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

I denne illustration er definition af politikker for overholdelse af enheder en afhængighed af at opnå det anbefalede beskyttelsesniveau i Zero Trust-rammen. 

For at konfigurere politikker for enhedsoverholdelse skal du bruge den anbefalede vejledning og de indstillinger, der er angivet i [Null Trust-identitet og politikker for enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). Tabellen nedenfor linker direkte til instruktionerne til konfiguration af disse politikker i Intune, herunder de anbefalede indstillinger for hver platform.


|Politikker |Flere oplysninger  |Licensering |
|---------|---------|---------|
|[Definer politikker for enhedsoverholdelse ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  Én politik for hver platform       |  Microsoft 365 E3 eller E5       |
|  |         |         |

## <a name="next-steps"></a>Næste trin

Gå til [Trin 4. Kræv sunde og kompatible enheder](manage-devices-with-intune-require-compliance.md) for at få en vejledning i, hvordan du opretter reglen for betinget adgang i Azure AD.