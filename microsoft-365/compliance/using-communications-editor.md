---
title: Brug kommunikationseditoren
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
description: Brug Kommunikationseditor til at ændre tekst- og fletfeltvariabler, når du formaterer dit indhold.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: aceebf9f8a19448c05c137f668c2bca5db2d99bd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587729"
---
# <a name="use-the-communications-editor"></a>Brug kommunikationseditoren

Når du definerer indholdet af dit portalindhold, meddelelser om retslig venteposition og relaterede påmindelser/eskaleringer, kan du bruge Kommunikationseditor til at formatere og tilpasse dit indhold dynamisk.

## <a name="rich-text-editor"></a>RTF-editor

Kommunikationseditoren giver brugerne mulighed for at tilpasse teksten ved hjælp af redigeringsindstillingerne. Brugere kan f.eks ændre skrifttypetyper, oprette opstillinger med punkttegn, fremhæve indhold og meget mere.

## <a name="merge-field-variables"></a>Variabler for fletfelt

Du kan bruge variabler til mailfletning fra Kommunikationseditor til at integrere brugerdefinerede attributter for fletning i en kommunikations brødtekst. Når det sendes til hjælperen, udfyldes fletfeltet med det tilsvarende felt. Når f.eks. sendes til vagtleder John Smith, oversættes fletfeltet [navn på fletningsnavn] med det tilsvarende navn.

Du kan bruge felter til mailfletning ved at vælge **ikonerne for** Fletfelt øverst i RTF-editorkontrolelementet. Pladsholderen tilføjes baseret på placeringen af brugernes markør.

### <a name="list-of-merge-field-variables"></a>Liste over variabler for fletfelter

<br>

****

|Feltnavn|Feltoplysninger|
|---|---|
|Visningsnavn|Den andens for- og efternavn.|
|Bekræftelseslink|Et tilpasset link til at registrere hver af de ydsmandsforberedendes bekræftelse.|
|Portallink|Et tilpasset link til complianceianens overholdelsesportal.|
|Udstedelsesofficer|Mailadressen på den angivne udstederofficer.|
|Udstedelsesdato|Den dato, hvor meddelelsen blev udstedt (UTC).|
|
