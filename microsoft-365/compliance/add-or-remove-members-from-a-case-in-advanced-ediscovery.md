---
title: Tilføj eller fjern medlemmer fra en sag
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Få mere at vide om, hvordan du tilføjer eller fjerner de medlemmer, der har adgang til en sag, når du administrerer Advanced eDiscovery sag.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 8e239622add6965a280e9c2b01bc00d9f2b9b0d5
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/15/2021
ms.locfileid: "63588923"
---
# <a name="add-or-remove-members-from-a-case"></a>Tilføj eller fjern medlemmer fra en sag

Du kan tilføje eller fjerne medlemmer for at administrere, hvem der har adgang til sagen. Før et medlem kan få adgang til en Advanced eDiscovery-sag (og udføre opgaver i sagen), skal du dog føje brugeren til rollegruppen eDiscovery Manager på siden Tilladelser i Microsoft 365 Overholdelsescenter. Få mere at vide under [Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

1. På **Advanced eDiscovery skal** du gå til den sag, du vil føje et medlem til.

2. Klik på **Indstillinger**, og klik **derefter på** Vælg **i & Access-tilladelser**.

3. Under **Administrer medlemmer skal** du klikke **på Tilføj** for at føje medlemmer til sagen. Du kan også vælge at føje en rollegruppe til sagen ved at klikke på  **Tilføj** under **Administrer rollegrupper**.

4. Markér afkrydsningsfeltet ud for navnene på de personer eller rollegrupper, du vil tilføje, på listen over personer eller rollegrupper, der kan tilføjes som medlemmer af sagen.

   > [!NOTE]
   > Når du føjer en rollegruppe til en sag, kan du kun tilføje de rollegrupper, du er medlem af.

5. Når du har valgt de personer eller rollegrupper, der skal tilføjes som medlemmer af sagen, skal du klikke på **Tilføj**.

6. På pop **op-siden Administrer denne** sag skal du klikke på **Gem for** at gemme den nye liste over sagsmedlemmer.

> [!IMPORTANT]
> Hvis en rolle tilføjes eller fjernes fra en rollegruppe, du har tilføjet som medlem af en sag, fjernes rollegruppen automatisk som medlem af sagen (eller hvis rollegruppen er medlem af). Dette skyldes, at du beskytter din organisation mod utilsigtet at give ekstra tilladelser til medlemmer af en sag. På samme måde vil en rollegruppe, hvis den slettes, blive fjernet fra alle tilfælde, den var medlem af. Få mere at vide under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases).

## <a name="removing-members-from-a-case"></a>Fjerne medlemmer fra en sag

Kun en [eDiscovery-administrator](assign-ediscovery-permissions.md) kan fjerne medlemmer fra en sag. Selvom du er tildelt eDiscovery Manager-rollegruppen eller indledningsvist oprettet sagen, kan du ikke fjerne dig selv eller andre medlemmer fra en sag, medmindre du også er eDiscovery-administrator. Hvis du vil fjerne dig selv eller andre medlemmer fra en sag, skal du kontakte en eDiscovery-administrator i din organisation.
