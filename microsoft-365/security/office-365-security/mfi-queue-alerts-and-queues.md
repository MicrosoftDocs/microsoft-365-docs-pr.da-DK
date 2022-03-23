---
title: Indsigt i køen i dashboardet for mailflow
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.custom: ''
ms.localizationpriority: medium
ms.assetid: 37640c80-ce6f-47e2-afd1-bc1d3c50e637
description: Administratorer kan lære at bruge widgetten Køer i dashboardet for mailflow i Security & Compliance Center til at overvåge mislykket mailflow for deres lokale organisationer eller partnerorganisationer over udgående forbindelser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 197dbf1c50451f205b9a6f692faa7bab3c40fd11
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587322"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Køindsigt i Sikkerheds- & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Når meddelelser ikke kan sendes fra din organisation til dine lokale eller partnermailservere ved hjælp af forbindelser, står meddelelserne i kø i Microsoft 365. Almindelige eksempler, der forårsager denne betingelse, er:

- Forbindelsen er konfigureret forkert.
- Der har været ændringer af netværk eller firewall i dit lokale miljø.

Microsoft 365 fortsætter med at forsøge at levere i 24 timer. Efter 24 timer udløber meddelelserne og returneres til afsenderen i rapporter om manglende levering (også kaldet en rapport om manglende levering eller meddelelser om ikke-leveret mail).

Hvis mængden af mails i kø overstiger den foruddefinerede grænseværdi (standardværdien er 200 meddelelser), er oplysningerne tilgængelige på følgende placeringer:

- **Indsigten Køer** i [dashboardet for mailflow](mail-flow-insights-v2.md) i [& Security Compliance Center](https://protection.office.com). Du kan finde flere oplysninger i [indsigten Køer i afsnittet Dashboard for mailflow](#queues-insight-in-the-mail-flow-dashboard) i denne artikel.

- En besked vises i Seneste **vigtige beskeder dashboardet** Vigtige beskeder i [Security & Compliance Center](https://protection.office.com) (**Alerts** \> **Dashboard** eller <https://protection.office.com/alertsdashboard>).

  ![Seneste beskeder i dashboardet Vigtige beskeder i sikkerheds- & Overholdelsescenter.](../../media/mfi-queued-messages-alert.png)

- Administratorer modtager en mail, der er baseret på konfigurationen af standardpolitikken for påmindelser med navnet **Meddelelser er blevet forsinket**. Hvis du vil konfigurere indstillingerne for meddelelser for denne besked, skal du se næste afsnit.

  Du kan finde flere oplysninger om beskedpolitikker [under Beskedpolitikker i & Security & Compliance Center](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Tilpasse beskeder om kø

1. I [Security & Compliance Center skal](https://protection.office.com) du gå til **Politikker for vigtige** \> **beskeder** eller åbne <https://protection.office.com/alertpolicies>.

2. På siden **Beskedpolitikker** skal du finde og vælge politikken Meddelelser er **blevet forsinket**.

3. I pop **op-menuen Meddelelse er** blevet forsinket, som åbnes, kan du slå beskeden til eller fra og konfigurere indstillingerne for meddelelser.

   ![Meddelelser er blevet forsinket med oplysninger om politikken for sikkerhed og & overholdelsescenter.](../../media/mfi-queued-messages-alert-policy.png)

   - **Status**: Du kan slå beskeden til eller fra.

   - **Mailmodtagere og** Grænse **for daglig meddelelse**: Klik **på Rediger** for at konfigurere følgende indstillinger:

4. Klik på Rediger for at konfigurere **meddelelsesindstillingerne**. I pop **op-menuen** Rediger politik, der vises, skal du konfigurere følgende indstillinger:

   - **Send mailbeskeder**: Standardværdien er på .
   - **Mailmodtagere**: Standardværdien er **TenantAdmins**.
   - **Daglig beskedgrænse**: Standardværdien er **Ingen grænse**.
   - **Grænseværdi**: Standardværdien er 200.

   ![Meddelelsesindstillinger i meddelelserne er blevet forsinkede politikoplysninger om sikkerhed og & overholdelsescenter.](../../media/mfi-queued-messages-alert-policy-notification-settings.png)

5. Klik på Gem og luk, når **du er** **færdig**.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Indsigt i køen i dashboardet for mailflow

Selvom mængden af meddelelser i kø ikke har overskredet grænsen og genereret en besked, kan du stadig bruge indsigten Køer i  [dashboardet for mailflow](mail-flow-insights-v2.md) til at se meddelelser, der er sat i kø i mere end en time, og gøre noget, før antallet af meddelelser i kø bliver for stort.

![Widgetten Køer i dashboardet for mailflow i & Security & Compliance Center.](../../media/mfi-queues-widget.png)

Hvis du klikker på antallet af meddelelser på widgetten, vises en pop **op-vindue** i kø med følgende oplysninger:

- **Antal meddelelser i kø**
- **Forbindelsesnavn**: Vælg forbindelsesnavnet for at administrere forbindelsen Exchange Administration (EAC) på <https://admin.exchange.microsoft.com/#/connectors>.
- **Køtid i gang**
- **Ældste meddelelser er udløbet**
- **Destinationsserver**
- **Sidste IP-adresse**
- **Sidste fejl**
- **Sådan løser du** det: Almindelige problemer og løsninger er tilgængelige. Hvis linket **Fix it now** er tilgængeligt, skal du klikke på det for at løse problemet. Ellers skal du klikke på eventuelle links for at få flere oplysninger om fejlen og mulige løsninger.

![Detaljer efter klik på indsigten Køer i dashboardet for mailflow.](../../media/mfi-queues-details.png)

Det samme pop op-billede vises, når du klikker **på Vis** kø i detaljerne for en **meddelelse er blevet forsinket** .

![Meddelelser er blevet forsinkede oplysninger i Sikkerheds- & Overholdelsescenter.](../../media/mfi-queued-messages-alert-details.png)

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
