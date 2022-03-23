---
title: Forbind dit domæne til Microsoft 365
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Lær at bekræfte dit domæne og oprette DNS-poster med Microsoft 365.
ms.custom:
- AdminSurgePortfolio
ms.openlocfilehash: 3aa43cd798c26dde8eb064754ae3fb74bd520c29
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589866"
---
# <a name="connect-your-domain-to-microsoft-365"></a>Forbind dit domæne til Microsoft 365

> [!NOTE]
> Hvis du ikke tilføjer et domæne, vil personer i organisationen bruge domænet onmicrosoft.com deres mailadresser, indtil du gør det. Det er vigtigt at tilføje dit domæne, før du tilføjer brugere, så du ikke behøver at konfigurere dem to gange.

[Se Ofte stillede spørgsmål om](../setup/domains-faq.yml) domæner, hvis du ikke kan finde det, du leder efter, nedenfor.

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Tilføj en MX-post, så mail til dit domæne kommer til Microsoft

Du får oplysningerne om MX-posten fra konfigurationsguiden for domæner i Administration.

Tilføj en ny MX-post på din udbyders websted.
Sørg for, at felterne er angivet til følgende værdier:

- Record Type: `MX`
- Prioritet: Indstillet til den højeste tilgængelige værdi, typisk `0`.
- Værtsnavn: `@`
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

Gem posten, og fjern derefter eventuelle andre MX-poster.

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a>Tilføje en CNAME-post for at forbinde brugere til deres postkasser

Du får oplysningerne om CNAME-posterne fra konfigurationsguiden for domæner i Administration.

Tilføj følgende CNAME-post på din udbyders websted. Sørg for, at felterne er indstillet til følgende værdier for hver:

- Record Type: `CNAME (Alias)`
- Vært: Indsæt de værdier, du kopierer fra Administration, her.
- Peger på adresse: Kopiér værdien fra Administration, og indsæt den her.
- TTL: `3600` (eller din udbyders standard)

## <a name="add-a-txt-record-to-help-prevent-spam"></a>Tilføj en TXT-post for at forhindre spam

**Før du går i gang:** Hvis du allerede har en SPF-post for dit domæne, skal du ikke oprette en ny for Microsoft 365. I stedet skal du føje de påkrævede Microsoft 365-værdier til den aktuelle post på hostingudbydernes websted, så du har en *enkelt* SPF-post, der indeholder begge sæt af værdier.

Rediger den eksisterende SPF-post på din udbyders websted, eller opret en SPF-post.
Sørg for, at felterne er angivet til følgende værdier:

- Record Type: `TXT (Text)`
- Vært: `@`
- TXT-værdi: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (eller din udbyders standard)

Gem posten.

Valider din SPF-post ved hjælp af et af disse [SPF-valideringsværktøjer](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

SPF er udviklet til at forhindre spoofing, men der findes spoofing-teknikker, som SPF ikke kan beskytte sig mod. For at beskytte dig mod disse skal du, når du har konfigureret SPF, også konfigurere DKIM og DMARC til Microsoft 365.

For at komme i gang skal du se Brug DKIM til at validere udgående mails, der sendes fra dit domæne [i Microsoft 365](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) og [Brug DMARC til at validere mail i Microsoft 365](../../security/office-365-security/use-dmarc-to-validate-email.md).

Til sidst skal du gå tilbage til konfigurationsguiden for domæner i Administration for at fuldføre konfigurationen.
