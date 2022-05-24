---
title: Mailflow i EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: Administration kan få mere at vide om indstillingerne for konfiguration af mailflow og distribution i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e0267af0297dce41657c76e97964e5c02fbe5815
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648739"
---
# <a name="mail-flow-in-eop"></a>Mailflow i EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med Exchange Online postkasser eller enkeltstående Exchange Online Protection -organisationer (EOP) uden Exchange Online postkasser passerer alle meddelelser, der sendes til din organisation, gennem EOP, før brugerne ser dem. Du har mulighed for at distribuere meddelelser, der sendes gennem EOP til behandling, før de distribueres til brugerpostkasser.

## <a name="working-with-messages-and-message-access-options"></a>Arbejde med meddelelser og indstillinger for meddelelsesadgang

EOP giver fleksibilitet i den måde, dine meddelelser distribueres på. I følgende emner beskrives trinnene i mailflowprocessen.

[Brug mappebaseret kantblokering til at afvise meddelelser, der er sendt til ugyldige modtagere](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Beskriver blokeringsfunktionen mappebaseret Edge, som giver dig mulighed for at afvise meddelelser for ugyldige modtagere ved tjenestens netværksperimeter.

[Få vist eller rediger accepterede domæner i EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) beskriver, hvordan du administrerer domæner, der er knyttet til din EOP-tjeneste.

Hvis du føjer underdomæner til din organisation, kan din EOP-tjeneste også hjælpe dig med at administrere disse. Få mere at vide om underdomæner under [Aktivér mailflow for underdomæner i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Konfigurer mailflow ved hjælp af connectorer](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) introducerer forbindelser og viser, hvordan du kan bruge dem til at tilpasse postdistribution. Scenarier omfatter sikring af sikker kommunikation med en partnerorganisation og konfiguration af en smart vært.

[Forbedret filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) beskriver, hvordan du konfigurerer forbindelser, hvis din mail distribueres til en tjeneste eller enhed før EOP.

I hybridmiljøer, hvor EOP beskytter Exchange postkasser i det lokale miljø, skal du konfigurere regler for mailflow (også kaldet transportregler) i Exchange i det lokale miljø. Disse regler for mailflow oversætter dommen til filtrering af uønsket mail, så reglen for uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan finde flere oplysninger under [Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). Hvis du ikke vil flytte meddelelser til hver brugers mappe med uønsket mail, kan du vælge en anden handling ved at redigere dine politikker til bekæmpelse af spam (også kendt som politikker for indholdsfilter). Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af spam](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Bekræft mailflow

Hvis du vil kontrollere, at din EOP-konfiguration, herunder din connectorkonfiguration, fungerer korrekt, skal du se "Hvordan ved du, at denne opgave fungerede?" i [Konfigurer din EOP-tjeneste](/exchange/standalone-eop/set-up-your-eop-service).

[Test mailflow ved at validere dine Microsoft 365-connectorer](/exchange/mail-flow-best-practices/test-mail-flow) indeholder instruktioner til test af, om dit mailflow er konfigureret korrekt.
