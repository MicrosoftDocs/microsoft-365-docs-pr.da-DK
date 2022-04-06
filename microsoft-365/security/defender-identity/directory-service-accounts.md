---
title: Konfigurere adresselistekonto i Microsoft Defender for Identity
description: Lær, hvordan du konfigurerer Microsoft Defender for Identity Directory Services-kontoen i Microsoft 365 Defender
ms.date: 08/15/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e31c226037d5d9e945350ba73e1df9abc79571e9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469993"
---
# <a name="microsoft-defender-for-identity-directory-services-account-in-microsoft-365-defender"></a>Microsoft Defender for Identity konto til adresseliste i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

Denne artikel forklarer, hvordan du [konfigurerer Microsoft Defender for Identity](/defender-for-identity) Directory Services-kontoen [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

## <a name="configure-directory-services-account"></a>Konfigurere adresselistekonto

Hvis du vil [forbinde sensoren](sensor-health.md#add-a-sensor) med dine Active Directory-domæner, skal du konfigurere Directory Services-konti.

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen Identiteter på Indstillinger siden" lightbox="../../media/defender-identity/settings-identities.png":::


1. Vælg **Adresselistekonti**. Du kan se, hvilke konti der er knyttet til hvilke domæner.

   :::image type="content" source="../../media/defender-identity/directory-service-accounts.png" alt-text="Menuelementet Konti til adresseliste" lightbox="../../media/defender-identity/directory-service-accounts.png":::

1. Hvis du vælger en konto, åbnes en rude med indstillingerne for den pågældende konto.

   :::image type="content" source="../../media/defender-identity/account-settings.png" alt-text="Siden Kontoindstillinger" lightbox="../../media/defender-identity/account-settings.png":::

1. Hvis du vil tilføje en ny konto til adresseliste, **skal du** vælge Opret ny konto **og udfylde Kontonavn****, Domæne** og **Adgangskode**. Du kan også vælge, om det er en gruppe-administreret **tjenestekonto** (gMSA), og om den tilhører et **enkelt etiketdomæne**.

   :::image type="content" source="../../media/defender-identity/new-directory-service-account.png" alt-text="Indstillingen Opret ny konto" lightbox="../../media/defender-identity/new-directory-service-account.png":::

1. Vælg **Gem**.

## <a name="see-also"></a>Se også

- [Microsoft Defender for Identity og indstillinger for sensor](sensor-health.md)
