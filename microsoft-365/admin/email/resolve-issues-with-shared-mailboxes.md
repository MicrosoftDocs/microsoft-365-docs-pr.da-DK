---
title: Løse problemer med delte postkasser
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
description: Du kan få fejl, når du konfigurerer delte postkasser. Prøv disse løsninger, hvis du oplever problemer med delte postkasser.
ms.openlocfilehash: 2be12810e6651da5b062afbd0a3437913b9a4d60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589343"
---
# <a name="resolve-issues-with-shared-mailboxes"></a>Løse problemer med delte postkasser

Hvis du får vist fejlmeddelelser, når du opretter eller bruger en delt postkasse, kan du prøve disse mulige løsninger. 

## <a name="error-when-creating-shared-mailboxes"></a>Fejl ved oprettelse af delte postkasser
<a name="bkmk_Fix"> </a>

Hvis du får vist fejlmeddelelsen, bruges **proxyadressen "smtp:<delt postkassenavn\>" allerede af proxyadresserne eller LegacyExchangeDN for "\<name>". Vælg en anden proxyadresse**, det betyder, at du forsøger at give den delte postkasse et navn, der allerede er i brug. Lad os f.eks. sige, at du vil have delte postkasser info@domain1 og info@domain2. Der er to måder at gøre dette på:

  - Brug Windows PowerShell. Se dette blogindlæg for at få [vejledning: Oprette delte postkasser med samme alias på forskellige domæner](https://www.cogmotive.com/blog/office-365-tips/create-shared-mailboxes-with-same-alias-at-different-domains-in-office-365)
    
  - Navngive den anden delte postkasse noget andet end det første for at løse fejlen. I Administration kan du omdøbe den delte postkasse til det ønskede navn.

## <a name="error-about-not-having-send-permissions-when-using-a-shared-mailbox"></a>Fejl om, at du ikke har send tilladelser, når du bruger en delt postkasse

Hvis du har oprettet en delt postkasse og derefter forsøger at sende en meddelelse fra den, får du muligvis følgende:

**Denne meddelelse kunne ikke sendes. Du har ikke tilladelse til at sende meddelelsen på vegne af den angivne bruger.**

Denne meddelelse vises, når Microsoft 365 oplever problemer med replikeringsventetid. Det bør gå væk om en time eller deromkring, når oplysningerne om din nye delte postkasse (eller tilføjede bruger) replikeres på tværs af alle vores datacentre. Vent en time, og prøv derefter igen for at sende en meddelelse.

## <a name="related-content"></a>Relateret indhold

[Om delte postkasser](about-shared-mailboxes.md) (artikel)\
[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)


    

