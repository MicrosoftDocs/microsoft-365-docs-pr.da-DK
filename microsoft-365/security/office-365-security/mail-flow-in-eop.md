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
description: Administratoren kan få mere at vide om indstillingerne for konfiguration af mailflow og -routing Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 296cd8aaa92005f094de2ee7d1c9f8bb9427df16
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681012"
---
# <a name="mail-flow-in-eop"></a>Mailflow i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med Exchange Online-postkasser eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser passerer alle meddelelser, der sendes til din organisation, gennem EOP, før dine medarbejdere kan se dem. Du har indstillinger for, hvordan du distribuerer meddelelser, der passerer gennem EOP, til behandling, før de sendes til dine medarbejderes indbakker.

## <a name="working-with-messages-and-message-access-options"></a>Arbejde med indstillinger for meddelelser og meddelelsesadgang

EOP tilbyder fleksibilitet i, hvordan dine meddelelser distribueres. Følgende emner forklarer trinnene i mailflowprocessen.

[Brug blokering af mappebaseret kant til at afvise meddelelser, der sendes til ugyldige modtagere](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Beskriver funktionen Blokering af mappebaserede kanter, som giver dig mulighed for at afvise meddelelser for ugyldige modtagere på tjenestens netværksperimeter.

[Få vist eller rediger accepterede domæner i EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) beskriver, hvordan du administrerer domæner, der er knyttet til din EOP-tjeneste.

Hvis du føjer underdomæner til organisationen, kan din EOP-tjeneste også hjælpe dig med at administrere disse. Få mere at vide om underdomæner [på Aktivér mailflow for underdomæner Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Konfigurer mailflow ved hjælp af forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) introducerer forbindelser og viser, hvordan du kan bruge dem til at tilpasse mailrouting. Scenarierne omfatter at sikre sikker kommunikation med en partnerorganisation og at konfigurere en intelligent vært.

[Udvidet filtrering for forbindelser beskriver](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) , hvordan du konfigurerer forbindelser, hvis din mail dirigeres til en tjeneste eller enhed før EOP.

I hybridmiljøer, hvor EOP beskytter lokale Exchange-postkasser, skal du konfigurere regler for mailflow (også kaldet transportregler) i lokale Exchange. Disse regler for mailflow oversætter reglen om spamfiltrering for EOP, så reglen om uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan få mere at [vide under Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). Hvis du ikke vil flytte meddelelser til hver brugers mappe med Uønsket mail, kan du vælge en anden handling ved at redigere dine politikker for uønsket post (også kaldet politikker for filtrering af indhold). Få mere at vide under [Konfigurer antispam-politikker](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Bekræft mailflow

Hvis du vil bekræfte, at din EOP-konfiguration, herunder din forbindelseskonfiguration, fungerer korrekt, skal du se "Hvordan ved du, at denne opgave fungerede?" i [Konfigurere din EOP-tjeneste](/exchange/standalone-eop/set-up-your-eop-service).

[Test af mailflow ved at validere dine Microsoft 365-forbindelser indeholder](/exchange/mail-flow-best-practices/test-mail-flow) instruktioner til test af, at dit mailflow er konfigureret korrekt.
