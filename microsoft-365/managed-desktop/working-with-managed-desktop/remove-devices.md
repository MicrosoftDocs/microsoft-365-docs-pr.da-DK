---
title: Fjern enheder
description: Fjern enheder fra Microsoft Administreret skrivebordsadministration
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 82e14fbd2bc991505c84d219c0624f52791376d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597910"
---
# <a name="remove-devices"></a>Fjern enheder

Du kan fjerne enheder fra Microsoft Administreret skrivebordsadministration ved hjælp af administrationsportalen. Denne handling er permanent, men du kan registrere dem på Microsoft Managed Desktop igen ved at følge de [manuelle registreringstrin](../get-started/manual-registration.md).

Når du fjerner en enhed, sker alt følgende:

- Vi fjerner enheden fra Autopilot.
- Vi fjerner enheden fra alle enhedsgrupper i "Moderne arbejdsplads".
- Vi fjerner enheden fra **bladet** Enheder i administrationsportalen.

Når du fjerner en enhed, kan du også fjerne den fra Azure Active Directory (Azure AD) og Microsoft Intune.
  
> [!CAUTION]
> Fjernelse af de objekter, der er relateret til en enhed fra Azure AD og Microsoft Intune, er permanent. Hvis du fjerner objekterne, kan du ikke få vist eller administrere enhederne fra Intune- og Azure-portalerne. Enhederne vil ikke kunne få adgang til virksomhedens virksomhedsressourcer. Firmadata kan blive slettet fra dem, hvis enhederne forsøger at logge på, efter de er blevet slettet.

**Sådan fjerner du en enhed:**

1. I [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) du vælge **Enheder** i venstre navigationsrude.
2. I sektionen **Microsoft Managed Desktop** skal du vælge **Enheder**.
3. I **arbejdsområdet Microsoft-administrerede stationære** enheder skal du vælge de enheder, du vil slette.
4. Vælg **Enhedshandlinger**, og vælg derefter **Slet enhed** , som åbner et pop op-vindue for at fjerne enhederne.
5. Gennemgå de valgte enheder i pop op-dialogboksen, og vælg derefter **Fjern enheder**. Hvis du også vil fjerne Azure AD- og Intune-objekter på samme tid, skal du markere afkrydsningsfeltet. Det kan tage et par minutter at fjerne enheden.

> [!NOTE]
> Du kan ikke fjerne enheder, der er i en **afventende** registreringstilstand.
