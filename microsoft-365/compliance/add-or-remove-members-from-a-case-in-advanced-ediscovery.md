---
title: Tilføj eller fjern medlemmer fra en sag
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du tilføjer eller fjerner de medlemmer, der kan få adgang til en sag, når du administrerer en eDiscovery-sag (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 0b3ed53ee897e88d70a7b1322999e5b81de8ed81
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627707"
---
# <a name="add-or-remove-members-from-a-case"></a>Tilføj eller fjern medlemmer fra en sag

Du kan tilføje eller fjerne medlemmer for at administrere, hvem der har adgang til sagen. Før et medlem kan få adgang til en eDiscovery-sag (Premium) (og udføre opgaver i dette tilfælde), skal du dog føje brugeren til rollegruppen eDiscovery Manager på siden **Tilladelser** i Microsoft Purview-compliance-portal. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](./assign-ediscovery-permissions.md).

1. På siden **eDiscovery (Premium)** skal du gå til den sag, du vil føje et medlem til.

2. Klik på fanen **Indstillinger,** og klik derefter på **Vælg** i feltet **Adgang & tilladelser** .

3. Under **Administrer medlemmer** skal du klikke på **Tilføj** for at føje medlemmer til sagen. Du kan også vælge at føje en rollegruppe til sagen ved at klikke på  **Tilføj** under **Administrer rollegrupper**.

4. På listen over personer eller rollegrupper, der kan tilføjes som medlemmer af sagen, skal du markere afkrydsningsfeltet ud for navnene på de personer eller rollegrupper, du vil tilføje.

   > [!NOTE]
   > Når du føjer en rollegruppe til en sag, kan du kun tilføje de rollegrupper, du er medlem af.

5. Når du har valgt de personer eller rollegrupper, der skal tilføjes som medlemmer af sagen, skal du klikke på **Tilføj**.

6. Klik på **Gem** på siden **Administrer denne sag** for at gemme den nye liste over sagsmedlemmer.

> [!IMPORTANT]
> Hvis en rolle tilføjes eller fjernes fra en rollegruppe, som du har tilføjet som medlem af en sag, fjernes rollegruppen automatisk som medlem af sagen (eller i alle tilfælde rollegruppen er medlem af). Årsagen til dette er at beskytte din organisation mod utilsigtet at give yderligere tilladelser til medlemmer af en sag. Hvis en rollegruppe slettes, fjernes den på samme måde fra alle de sager, den var medlem af. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases).

## <a name="removing-members-from-a-case"></a>Fjernelse af medlemmer fra en sag

Det er kun [en eDiscovery-administrator, der](assign-ediscovery-permissions.md) kan fjerne medlemmer fra en sag. Selvom du er tildelt til rollegruppen eDiscovery Manager eller oprindeligt har oprettet sagen, kan du ikke fjerne dig selv eller andre medlemmer fra en sag, medmindre du også er eDiscovery-administrator. Hvis du vil fjerne dig selv eller andre medlemmer fra en sag, skal du kontakte en eDiscovery-administrator i din organisation.
