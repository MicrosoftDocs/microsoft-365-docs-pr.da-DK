---
title: Administrer brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du redigerer og fjerner brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0efbb93096fc3c0b61a57319aa2d23a079f684d1
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/18/2022
ms.locfileid: "63593082"
---
# <a name="manage-custom-sensitive-information-types-in-the-compliance-center"></a>Administrer brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter

I denne artikel bliver du vejet gennem trinnene til at ændre og fjerne en eksisterende brugerdefineret type af følsomme oplysninger i Overholdelsescenter.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Rediger brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> Typer af følsomme oplysninger og vælge typen af følsomme oplysninger på den liste, du vil ændre, og vælge **Rediger**.

2. Du kan tilføje andre mønstre med entydige primære og supplerende elementer, tillidsniveauer, tegntilflidshed og yderligere kontroller eller rediger/fjern de eksisterende.[](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks)

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Fjern brugerdefinerede typer af følsomme oplysninger i Overholdelsescenter 

> [!NOTE]
> Du kan kun fjerne brugerdefinerede typer af følsomme oplysninger. du kan ikke fjerne indbyggede følsomme oplysningstyper.

> [!IMPORTANT]
> Før du fjerner en brugerdefineret type af følsomme oplysninger, skal du kontrollere, at ingen DLP-politikker eller Exchange regler for mailflow (også kaldet transportregler) stadig henviser til typen af følsomme oplysninger.

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> Typer af følsomme oplysninger og vælge typen af følsomme oplysninger på den liste, du vil fjerne.

2. I pop op-vindue, der åbnes, skal du vælge **Slet**.
