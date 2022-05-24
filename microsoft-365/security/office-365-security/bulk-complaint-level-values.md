---
title: Værdier for masseklageniveau
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om BCL-værdier (bulk complaint level), der bruges i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 08e747b704faa18aa73110256624d70c79d0307b
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647375"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Samlet klageniveau (BCL) i EOP

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser tildeler EOP et samlet klageniveau til indgående meddelelser fra masseforsendelser. BCL føjes til meddelelsen i en X-header og svarer til [det niveau for spamsikkerhed (SCL),](spam-confidence-levels.md) der bruges til at identificere meddelelser som spam. En højere BCL angiver, at der er større sandsynlighed for, at en massemeddelelse genererer klager (og er derfor mere tilbøjelige til at være spam). Microsoft bruger både interne kilder og tredjepartskilder til at identificere massemails og fastlægge den relevante BCL.

Masseforsendelser varierer i deres afsendelsesmønstre, indholdsoprettelse og modtagerkøbspraksisser. Gode masseforsendelser sender ønskede meddelelser med relevant indhold til deres abonnenter. Disse meddelelser genererer nogle få klager fra modtagere. Andre masseforsendelser sender uopfordrede meddelelser, der ligner spam, og genererer mange klager fra modtagere. Meddelelser fra en massemailer kaldes massemails eller grå mail.

 Filtrering af spam markerer meddelelser som **massemail** baseret på BCL-tærsklen (den standardværdi eller en værdi, du angiver) og udfører den angivne handling på meddelelsen (standardhandlingen er at levere meddelelsen til modtagerens mappe med uønsket mail). Du kan få flere oplysninger under [Konfigurer politikker mod spam](configure-your-spam-filter-policies.md) og [Hvad er forskellen mellem uønsket mail og massemail?](what-s-the-difference-between-junk-email-and-bulk-email.md)

BCL-tærsklerne er beskrevet i følgende tabel.

|BCL|Beskrivelse|
|:---:|---|
|0|Meddelelsen er ikke fra en massesender.|
|1, 2, 3|Meddelelsen er fra en massesender, der genererer få klager.|
|4, 5, 6, 7<sup>\*</sup>|Meddelelsen er fra en masse afsender, der genererer et blandet antal klager.|
|8, 9|Meddelelsen er fra en masse afsender, der genererer et højt antal klager.|

<sup>\*</sup> Dette er standardværdien for den grænseværdi, der bruges i politikker mod spam.
