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
description: Få mere at vide om, hvordan du redigerer og fjerner brugerdefinerede typer følsomme oplysninger i Overholdelsescenter.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5e0b1b91fd19a5e0705ad95affe888a87847caf8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621952"
---
# <a name="manage-custom-sensitive-information-types-in-the-compliance-center"></a>Administrer brugerdefinerede typer følsomme oplysninger i Overholdelsescenter

I denne artikel gennemgås trinnene til at redigere og fjerne en eksisterende brugerdefineret type følsomme oplysninger i Overholdelsescenter.

## <a name="modify-custom-sensitive-information-types-in-the-compliance-center"></a>Rediger brugerdefinerede typer følsomme oplysninger i Overholdelsescenter

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> **Følsomme oplysningstyper** og vælge typen af følsomme oplysninger på den liste, du vil redigere, vælge **Rediger**.

2. Du kan tilføje andre mønstre med unikke primære og understøttende elementer, tillidsniveauer, tegn nærhed og [**yderligere kontrol**](sit-regex-validators-additional-checks.md#sensitive-information-type-additional-checks) eller redigere/fjerne de eksisterende.

## <a name="remove-custom-sensitive-information-types-in-the-compliance-center"></a>Fjern brugerdefinerede typer følsomme oplysninger i Overholdelsescenter 

> [!NOTE]
> Du kan kun fjerne brugerdefinerede typer følsomme oplysninger. Du kan ikke fjerne indbyggede følsomme oplysningstyper.

> [!IMPORTANT]
> Før du fjerner en brugerdefineret type følsomme oplysninger, skal du kontrollere, at ingen DLP-politikker eller Exchange-regler for mailflow (også kaldet transportregler) stadig refererer til typen af følsomme oplysninger.

1. I Overholdelsescenter skal du gå til **Dataklassificering** \> **Følsomme oplysningstyper** og vælge typen af følsomme oplysninger på den liste, du vil fjerne.

2. Vælg **Slet** i den fly-out, der åbnes.
