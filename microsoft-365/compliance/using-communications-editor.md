---
title: Brug kommunikationseditoren
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
description: Brug kommunikationseditoren til at ændre variabler for tekst og fletfelter, når du formaterer dit indhold.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b44f6090f4a8bc9b09bb7934477741effc30ff6e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098400"
---
# <a name="use-the-communications-editor"></a>Brug kommunikationseditoren

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du definerer indholdet af portalindholdet, meddelelser om juridisk venteposition og relaterede påmindelser/eskaleringer, kan du bruge Kommunikationseditor til at formatere og tilpasse dit indhold dynamisk.

## <a name="rich-text-editor"></a>RTF-editor

Kommunikationseditoren gør det muligt for brugeren at tilpasse teksten ved hjælp af editorindstillingerne. Brugerne kan f.eks. ændre skrifttypetyper, oprette punktopstilling, fremhæve indhold og meget mere.

## <a name="merge-field-variables"></a>Flet feltvariabler

Du kan bruge variabler til mailfletning fra Kommunikationseditor til at integrere brugerdefinerede tilsynsførende attributter i brødteksten i en kommunikation. Når fletfeltet sendes til tilsynsførende, udfyldes det med det tilsvarende felt. Når fletfeltet [Navn på tilsynsførende] f.eks. sendes til tilsynsførende John Smith, oversættes det med det tilsvarende navn.

Du kan bruge felter til mailfletning ved at vælge ikonerne **fletfelter** øverst i RTF-editorkontrolelementet. Pladsholderen tilføjes baseret på placeringen af brugernes markør.

### <a name="list-of-merge-field-variables"></a>Liste over fletfeltvariabler

<br>

****

|Feltnavn|Feltoplysninger|
|---|---|
|Vist navn|Vogterens for- og efternavn.|
|Bekræftelseslink|Et tilpasset link til registrering af hver tilsynsførendes bekræftelse.|
|Portallink|Et tilpasset link til vogterens overholdelsesportal.|
|Udstedende myndighed|Mailadressen på den angivne udstedende officer.|
|Udstedelsesdato|Den dato, hvor meddelelsen blev udstedt (UTC).|
|
