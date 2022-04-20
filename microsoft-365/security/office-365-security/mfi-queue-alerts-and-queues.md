---
title: Sætter indsigt i kø i dashboardet Mailflow
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
description: Administratorer kan få mere at vide om, hvordan de bruger widgetten Køer i dashboardet Mailflow i Security & Compliance Center til at overvåge mislykket mailflow til deres lokale organisationer eller partnerorganisationer via udgående connectors.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 146ce26c32f1ff80a451b85fd343990db547a131
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972645"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Sætter indsigt i kø i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Når meddelelser ikke kan sendes fra din organisation til dine lokale eller partnermailservere ved hjælp af connectors, sættes meddelelserne i kø i Microsoft 365. Almindelige eksempler, der forårsager denne betingelse, er:

- Connectoren er konfigureret forkert.
- Der er foretaget netværks- eller firewallændringer i dit lokale miljø.

Microsoft 365 fortsætter med at forsøge at levere igen i 24 timer. Efter 24 timer udløber meddelelserne og returneres til afsenderne i rapporter om manglende levering (også kendt som NDR-anmodninger eller meddelelser om manglende levering).

Hvis den mailmængde, der er sat i kø, overskrider den foruddefinerede grænse (standardværdien er 200 meddelelser), er oplysningerne tilgængelige på følgende placeringer:

- Indsigten **Queues** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com). Du kan få flere oplysninger i afsnittet [Køindsigt i dashboardet Mailflow](#queues-insight-in-the-mail-flow-dashboard) i denne artikel.

- Der vises en besked i **Seneste beskeder** dashboardet Beskeder i [Security & Compliance Center](https://protection.office.com) (**Dashboard** for **beskeder** \> eller <https://protection.office.com/alertsdashboard>).

  :::image type="content" source="../../media/mfi-queued-messages-alert.png" alt-text="De seneste beskeder i dashboardet Beskeder i Security & Compliance Center" lightbox="../../media/mfi-queued-messages-alert.png":::

- Administratorer modtager en mailmeddelelse baseret på konfigurationen af standardbeskedpolitikken med navnet **Meddelelser er blevet forsinket**. Hvis du vil konfigurere beskedindstillingerne for denne besked, skal du se næste afsnit.

  Du kan få flere oplysninger om politikker for beskeder i [Beskedpolitikker i Security & Compliance Center](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Tilpas købeskeder

1. I [Security & Compliance Center](https://protection.office.com) skal du gå til **Beskedpolitikker** for **beskeder** \> eller åbne <https://protection.office.com/alertpolicies>.

2. På siden **Beskedpolitikker** skal du finde og vælge den politik, der hedder **Meddelelser er blevet forsinket**.

3. I pop op-vinduet **Meddelelse er forsinket** , der åbnes, kan du slå beskeden til eller fra og konfigurere meddelelsesindstillingerne.

   :::image type="content" source="../../media/mfi-queued-messages-alert-policy.png" alt-text="Oplysningerne om meddelelserne er blevet forsinket" lightbox="../../media/mfi-queued-messages-alert-policy.png":::

   - **Status**: Du kan slå beskeden til eller fra.

   - **Mailmodtagere** og **grænse for daglig meddelelse**: Klik på **Rediger** for at konfigurere følgende indstillinger:

4. Klik på **Rediger** for at konfigurere meddelelsesindstillingerne. Konfigurer følgende indstillinger i pop op-vinduet **Rediger politik** , der vises:

   - **Send mailmeddelelser**: Standardværdien er slået til.
   - **Mailmodtagere**: Standardværdien er **TenantAdmins**.
   - **Grænse for daglig meddelelse**: Standardværdien er **Ingen grænse**.
   - **Tærskel**: Standardværdien er 200.

     :::image type="content" source="../../media/mfi-queued-messages-alert-policy-notification-settings.png" alt-text="Beskedindstillingerne i meddelelserne er blevet forsinket" lightbox="../../media/mfi-queued-messages-alert-policy-notification-settings.png":::

5. Når du er færdig, skal du klikke på **Gem** og **luk**.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Sætter indsigt i kø i dashboardet Mailflow

Selvom mængden af meddelelser, der er sat i kø, ikke har overskredet grænsen og genereret en besked, kan du stadig bruge **indsigten Køer** i [dashboardet Mailflow](mail-flow-insights-v2.md) til at se meddelelser, der er sat i kø i mere end én time, og udføre handlinger, før antallet af meddelelser, der er sat i kø, bliver for stort.

:::image type="content" source="../../media/mfi-queues-widget.png" alt-text="Widgetten Køer i dashboardet Mailflow i Security & Compliance Center" lightbox="../../media/mfi-queues-widget.png":::

Hvis du klikker på antallet af meddelelser i widgetten, vises pop op-vinduet **Meddelelser i kø** med følgende oplysninger:

- **Antal meddelelser i kø**
- **Connectornavn**: Vælg connectornavnet for at administrere connectoren i Exchange Administration (EAC) på <https://admin.exchange.microsoft.com/#/connectors>.
- **Starttidspunkt for kø**
- **Ældste meddelelser er udløbet**
- **Destinationsserver**
- **Seneste IP-adresse**
- **Sidste fejl**
- **Sådan løses**: Almindelige problemer og løsninger er tilgængelige. Hvis linket **Ret det nu** er tilgængeligt, skal du klikke på det for at løse problemet. Ellers skal du klikke på eventuelle tilgængelige links for at få flere oplysninger om fejlen og mulige løsninger.

:::image type="content" source="../../media/mfi-queues-details.png" alt-text="Detaljerne, når du har klikket på indsigten Kø i dashboardet Mailflow" lightbox="../../media/mfi-queues-details.png":::

Det samme pop op-vindue vises, når du har klikket på **Vis kø** i oplysningerne om en **besked om, at meddelelser er blevet forsinket** .

:::image type="content" source="../../media/mfi-queued-messages-alert-details.png" alt-text="Oplysningerne om meddelelserne er blevet forsinket i Security & Compliance Center" lightbox="../../media/mfi-queued-messages-alert-details.png":::

## <a name="see-also"></a>Se også

Du kan få oplysninger om anden indsigt i dashboardet Mailflow under [Mailflowindsigt i Security & Compliance Center](mail-flow-insights-v2.md).
