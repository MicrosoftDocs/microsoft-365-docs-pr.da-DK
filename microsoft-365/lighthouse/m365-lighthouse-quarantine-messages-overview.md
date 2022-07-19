---
title: Oversigt over karantænemeddelelser i Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du administrerer karantænemeddelelser.
ms.openlocfilehash: 3a295802ba806c48f01f6f64c8b148169fe28102
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66858905"
---
# <a name="overview-of-quarantined-messages-in-microsoft-365-lighthouse"></a>Oversigt over karantænemeddelelser i Microsoft 365 Lighthouse

Med Microsoft 365 Lighthouse kan du se indsigt og oplysninger om karantænemails på tværs af alle dine kundelejere. Fra en enkelt visning kan du triage karantænerede mails og foretage de relevante handlinger. Dataene er tilgængelige, hvis lejeren har implementeret Exchange Online Protection (EOP) og Microsoft Defender for Office365 Plan 1 (MDO).

Du kan få adgang til oplysningerne ved at vælge **Databeskyttelse** i venstre navigationsrude **eller på** startsiden.

## <a name="quarantined-messages-page"></a>Side med karantænemeddelelser

Fra denne side kan du få vist konsolideret statistik på tværs af dine kundelejere, tendensdata for typen og mængden af karantænedata samt oplysninger, der er relateret til karantænekøer i individuelle kundelejere.

Afsnittet **Status for meddelelser** giver en samlet visning på tværs af berettigede lejere, der i øjeblikket er onboardet til Lighthouse. Visningen indeholder

- Samlet antal meddelelser i karantæne
- Samlet antal meddelelser, der afventer gennemsyn
- Meddelelser, der i øjeblikket nærmer sig standardgrænsen for karantæne på 30 dage og er ved at blive fjernet automatisk (udløber)
- Meddelelser, der er blevet frigivet fra karantæne
- Det samlede antal postkasser, der påvirkes på tværs af alle dine lejere

Dataene afspejler de seneste 30 dage. Du kan dog bruge filteret **Tidsinterval** til at redigere visningen.

Diagrammet **Karantæneårsag**  indeholder en opdeling af karantæneantal efter Exchange Online Protection (EOP) og Microsoft Defender for Office365 Plan 1 (MDO) politiktype. Disse typer omfatter

- Malware
- Phishing
- Phishing med høj genkendelsessikkerhed
- Spam
- Massemail

Karantænelisten er en sorterbar visning af karantæneoplysninger efter lejer. I denne visning kan du filtrere efter følgende oplysninger:

- **Karantæneårsag:** Any, Malware, Phish, High confidence phish, Spam, Bulk Email
- **Politiktype:** Any, Anti-malware, Anti-phishing, Anti-spam, Safe Attachments, Transport Rule, Unknown
- **Udløber snart:** Enhver, Today, inden for to dage, inden for syv dage

Du kan også justere kolonnerne og sortere data baseret på lejer, meddelelsesstatus og udløbsdatoer.

:::image type="content" source="../media/m365-lighthouse-data-protection/quarantine-email-page.png" alt-text="Siden Sæt meddelelser i karantæne i Microsoft 365 Lighthouse" lightbox="../media/m365-lighthouse-data-protection/quarantine-email-page.png":::

Indstillingen **Kopiér link til meddelelser i Microsoft** **365 Defender** indeholder et link til Microsoft 365 Defender portal, hvor du kan få adgang til og administrere din lejers mail karantænekø. Du skal godkende, før du kan udføre nogen handling.

## <a name="related-content"></a>Relateret indhold

[Mails i karantæne](../security/office-365-security/quarantine-email-messages.md) (artikel)\
[Microsofts anbefalinger til EOP og Defender for Office 365 sikkerhedsindstillinger](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (artikel)\
[oversigt over Exchange Online Protection (EOP)](../security/office-365-security/exchange-online-protection-overview.md) (artikel)
