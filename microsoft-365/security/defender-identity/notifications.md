---
title: Microsoft Defender for Identity meddelelser i Microsoft 365 Defender
description: Få mere at vide om, Microsoft Defender for Identity konfigurerer meddelelser Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 89ed7ae50bf89c28bde81ea02e8905d0056ede53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470917"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Defender til identitetsmeddelelser i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

Denne artikel forklarer, hvordan du arbejder [med Microsoft Defender for Identity](/defender-for-identity) meddelelser [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

## <a name="health-issues-notifications"></a>Meddelelser om tilstandsproblemer

I Microsoft 365 Defender kan du tilføje modtagere for mailbeskeder om tilstandsproblemer i Defender for Identity.

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

  :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen Identiteter i kolonnen Navn" lightbox="../../media/defender-identity/settings-identities.png":::


1. Vælg **Meddelelser om tilstandsproblemer**.

1. Angiv modtagerens mailadresse. Vælg **Tilføj**.

   :::image type="content" source="../../media/defender-identity/health-email-recipient.png" alt-text="Undermenuelementet Beskeder om tilstandsproblemer" lightbox="../../media/defender-identity/health-email-recipient.png":::

1. Når Defender for Identity registrerer et tilstandsproblem, modtager modtagerne en mail med oplysningerne.

   :::image type="content" source="../../media/defender-identity/health-email.png" alt-text="Mail om tilstandsproblem" lightbox="../../media/defender-identity/health-email.png":::

    > [!NOTE]
    > Mailen indeholder to links til yderligere oplysninger om problemet. Du kan enten gå til **MDI Health Center eller** det nye **Sundhedscenter i M365D**.

## <a name="alert-notifications"></a>Beskedbeskeder

I Microsoft 365 Defender kan du tilføje modtagere for mailbeskeder om registrerede beskeder.

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen Identiteter" lightbox="../../media/defender-identity/settings-identities.png":::

1. Vælg **Vigtige beskeder**.

1. Angiv modtagerens mailadresse. Vælg **Tilføj**.

   :::image type="content" source="../../media/defender-identity/alert-email-recipient.png" alt-text="Undermenuelementet Beskedbeskeder" lightbox="../../media/defender-identity/alert-email-recipient.png":::

## <a name="syslog-notifications"></a>Syslog-meddelelser

Defender for Identity kan give dig besked, når den registrerer mistænkelige aktiviteter, ved at sende sikkerheds- og tilstandsbeskeder til syslog-serveren via en udpeget sensor.

> [!NOTE]
> Du kan få mere at vide om, hvordan du integrerer Defender for Identity med Microsoft Sentinel [Microsoft 365 Defender integration med Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du gå **til Indstillinger** og derefter **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Indstillingen Identiteter i kolonnen Navn" lightbox="../../media/defender-identity/settings-identities.png":::

1. Vælg **Syslog-meddelelser**.

1. Hvis du vil aktivere syslog-meddelelsen, skal **du indstille Syslog-tjenesten** til **positionen Til** .

   :::image type="content" source="../../media/defender-identity/syslog-service.png" alt-text="Indstillingen Syslog-tjeneste, der kan aktiveres" lightbox="../../media/defender-identity/syslog-service.png":::

1. Vælg **Konfigurer tjeneste**. Der åbnes en rude, hvor du kan angive oplysninger om syslog-tjenesten.

   :::image type="content" source="../../media/defender-identity/syslog-sensor.png" alt-text="Den side, hvor du angiver oplysninger om Syslog-tjenesten" lightbox="../../media/defender-identity/syslog-sensor.png":::

1. Angiv følgende oplysninger:

    - **Sensor** – På rullelisten skal du vælge den sensor, der skal sende beskederne.
    - **Tjenesteslutpunkt** og **Port** – Angiv IP-adressen eller det fulde domænenavn for syslog-serveren, og angiv portnummeret. Du kan kun konfigurere ét Syslog-slutpunkt.
    - **Transport** – Vælg **Transport-protokollen** (TCP eller UDP).
    - **Format** – Vælg formatet (RFC 3164 eller RFC 5424).

1. Vælg **Send siEM-meddelelse til test,** og bekræft derefter, at meddelelsen er modtaget i din Syslog-infrastrukturløsning.

1. Vælg **Gem**.

1. Når du har konfigureret **Syslog-tjenesten**, kan du vælge, hvilke typer meddelelser (beskeder eller tilstandsproblemer) der skal sendes til Syslog-serveren.

   :::image type="content" source="../../media/defender-identity/syslog-configured.png" alt-text="Indstillingen Syslog-tjeneste er konfigureret markeret" lightbox="../../media/defender-identity/syslog-configured.png":::

## <a name="see-also"></a>Se også

- [Administrer sikkerhedsadvarsler for Defender for Identity](manage-security-alerts.md)
