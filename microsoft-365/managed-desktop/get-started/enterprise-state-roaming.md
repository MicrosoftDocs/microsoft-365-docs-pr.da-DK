---
title: Aktivér roaming i virksomhedstilstand
description: I denne artikel beskrives det, hvordan du aktiverer virksomhedsroaming
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 65056fc913b88ce0594c9a8b1a89bd2e92b221af
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589580"
---
# <a name="enable-enterprise-state-roaming"></a>Aktivér roaming i virksomhedstilstand

[Enterprise State Roaming giver](/azure/active-directory/devices/enterprise-state-roaming-overview) brugerne mulighed for sikkert at synkronisere data om bruger- og programindstillinger til skyen. Det betyder, at de får den samme oplevelse, uanset hvilken Windows de logger på. Hvis du f.eks. erstatter en af deres Microsoft Managed Desktop-enheder med en ny enhed, vil den se ud og fungere på præcis samme måde som den sidste.

Enterprise State Roaming er en valgfri funktion til tjenesten Microsoft Managed Desktop, som du kan konfigurere for dine brugere. Den er ikke inkluderet eller administreret som en del af Microsoft Managed Desktop.

Hvis du vil aktivere Enterprise State Roaming, skal du følge trinnene [i Aktivér enterprise state roaming Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable).

>[!NOTE]
>Hvis du aktiverer Enterprise State Roaming, overskriver din foretrukne sprogliste det valgte sprog under enhedskonfigurationen. Selvom brugerne nemt kan løse dette problem, kan det medføre en inkonsekvent lokaliseringsoplevelse i første omgang. Afgør, om Enterprise State Roaming er den rigtige for dine brugere, før du konfigurerer enheder.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
2. [Juster betinget adgang](conditional-access.md).
3. [Tildel licenser](assign-licenses.md).
4. [Installér Intune-firmaportal](company-portal.md).
5. Aktivér Enterprise State Roaming (dette emne).
6. [Klargør enheder](prepare-devices.md).
7. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
8. [Installér apps](deploy-apps.md).
