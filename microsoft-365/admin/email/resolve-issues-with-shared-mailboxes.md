---
title: Løs problemer med delte postkasser
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Du får muligvis vist fejl, når du konfigurerer delte postkasser. Prøv disse løsninger, hvis du oplever problemer med delte postkasser.
ms.openlocfilehash: 08b5bbaa1ea952ee2b9bb6c626328fdb6b91d71c
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008573"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Løs problemer med delte postkasser

Hvis du får vist fejlmeddelelser, når du opretter eller bruger en delt postkasse, kan du prøve disse mulige løsninger. 

## <a name="error-when-creating-shared-mailboxes"></a>Fejl under oprettelse af delte postkasser

Hvis du får vist fejlmeddelelsen, **bruges proxyadressen "smtp:<delt postkassenavn\>" allerede af proxyadresserne eller LegacyExchangeDN for "\<name>". Vælg en anden proxyadresse**. Det betyder, at du forsøger at give den delte postkasse et navn, der allerede er i brug. Lad os f.eks. sige, at du vil have delte postkasser med navnet info@domain1 og info@domain2. Der er to måder at gøre dette på:

- Brug Exchange Online PowerShell. Se denne vejledning i dette blogindlæg: [Opret delte postkasser med samme alias på forskellige domæner](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)

- Navngiv den anden delte postkasse noget andet end starten for at omgå fejlen. Omdøb derefter den delte postkasse i Administration til det, du vil have, den skal være.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Fejl ved ikke at have afsendelsestilladelser, når der bruges en delt postkasse

Hvis du har oprettet en delt postkasse og derefter forsøger at sende en meddelelse fra den, får du muligvis følgende:

**Denne meddelelse kunne ikke sendes. Du har ikke tilladelse til at sende meddelelsen på vegne af den angivne bruger.**

Denne meddelelse vises, når Microsoft 365 oplever et problem med replikeringsventetid. Den bør forsvinde om ca. en time, når oplysningerne om din nye delte postkasse (eller den tilføjede bruger) replikeres på tværs af alle vores datacentre. Vent en time, og prøv derefter at sende en meddelelse igen.

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)
