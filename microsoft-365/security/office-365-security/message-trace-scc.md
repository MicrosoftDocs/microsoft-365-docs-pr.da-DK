---
title: Meddelelsessporing i Microsoft 365 Defender portalen
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan bruge linket til meddelelsessporing i portalen til Microsoft 365 Defender at finde ud af, hvad der er sket med meddelelser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 934a8a0cf3c6eb0b828e334252707043d0d87e03
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587939"
---
# <a name="message-trace-in-the-microsoft-365-defender-portal"></a>Meddelelsessporing i Microsoft 365 Defender portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Meddelelsessporing følger mails, efterhånden som de passerer gennem Exchange Online organisation. Du kan afgøre, om en meddelelse er blevet modtaget, afvist, udskudt eller leveret af tjenesten. Den viser også, hvilke handlinger der blev foretaget på meddelelsen, før den nåede dens endelige status.

Du kan bruge oplysningerne fra meddelelsessporing til effektivt at besvare brugerspørgsmål om, hvad der er sket med meddelelser, foretage fejlfinding af problemer med mailflow og validere politikændringer.

> [!NOTE]
> Meddelelsessporing i Microsoft 365 Defender er blot en gennemløb til Meddelelsessporing i Exchange Administration. Du kan få mere at [vide under Meddelelsessporing i Exchange Administration](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du skal være medlem af rollegrupperne **Organisationsadministration****,** Overholdelsesstyring eller **Helpdesk** **i** Exchange Online at bruge meddelelsessporing. Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**: Medlemskab af den Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser og tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

- Det maksimale antal meddelelser, der vises i resultaterne af en meddelelsessporing, afhænger af den valgte rapporttype (se afsnittet Vælg [rapporttype](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac#choose-report-type) for at få mere at vide). [Cmdlet'en Get-HistoricalSearch](/powershell/module/exchange/get-historicalsearch) i Exchange Online PowerShell eller enkeltstående EOP PowerShell returnerer alle meddelelser i resultaterne.

## <a name="open-message-trace"></a>Åbn meddelelsessporing

I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & og Exchange** \> **meddelelsessporing**. Hvis du vil gå direkte til siden med meddelelsessporing, skal du bruge <https://admin.exchange.microsoft.com/#/messagetrace>.

På dette tidspunkt åbnes meddelelsessporing i EAC. Du kan få mere at [vide under Meddelelsessporing i Exchange Administration](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
