---
title: Konfigurer directory services-konto i Microsoft Defender for Identity
description: Få mere at vide om, hvordan du konfigurerer kontoen Microsoft Defender for Identity Directory Services i Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.openlocfilehash: 8928441e27215e75dc4456116c9a0e7890073852
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/15/2021
ms.locfileid: "63596872"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Microsoft Defender for Identity Directory Services-konto i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

I denne artikel forklares det, hvordan [du konfigurerer kontoen Microsoft Defender for Identity](/defender-for-identity) Directory Services [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

## <a name="configure-directory-services-account"></a>Konfigurere adresselistekonto

Hvis du vil [forbinde sensoren](sensor-health.md#add-a-sensor) med dine Active Directory-domæner, skal du konfigurere Directory Services-konti.

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

    ![Gå til Indstillinger og derefter Identities.](../../media/defender-identity/settings-identities.png)

1. Vælg **Adresselistekonti**. Du kan se, hvilke konti der er knyttet til hvilke domæner.

    ![Adresselistekonti.](../../media/defender-identity/directory-service-accounts.png)

1. Hvis du vælger en konto, åbnes en rude med indstillingerne for den pågældende konto.

    ![Kontoindstillinger.](../../media/defender-identity/account-settings.png)

1. Hvis du vil tilføje en ny konto til adresseliste, **skal du** vælge Opret ny konto **og udfylde Kontonavn****, Domæne** og **Adgangskode**. Du kan også vælge, om det er en gruppe-administreret **tjenestekonto** (gMSA), og om den tilhører et **enkelt etiketdomæne**.

    ![Ny adresselistekonto.](../../media/defender-identity/new-directory-service-account.png)

1. Vælg **Gem**.

## <a name="see-also"></a>Se også

- [Microsoft Defender til sensorens tilstand og indstillinger for identitet](sensor-health.md)
