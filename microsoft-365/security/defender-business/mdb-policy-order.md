---
title: Forstå politikrækkefølgen i Microsoft Defender til virksomheder
description: Få mere at vide om prioritetsrækkefølgen med politikker i Microsoft Defender til virksomheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 13e803666cc7af14af52031eb86a2f86edf06f80
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666300"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Forstå politikrækkefølgen i Microsoft Defender til virksomheder

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra den 1. marts 2022. Defender for Business som et separat abonnement fås som prøveversion og udrulles gradvist til kunder og [it-partnere, der tilmelder sig her](https://aka.ms/mdb-preview) for at anmode om det. Prøveversionen indeholder et [indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer jævnligt funktioner.
> 
> Nogle oplysninger i denne artikel er relateret til forhåndsudgivne produkter/tjenester, der kan blive ændret væsentligt, før de udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, for de oplysninger, der er angivet her. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>Politikrækkefølge i Microsoft Defender til virksomheder

Microsoft Defender til virksomheder indeholder foruddefinerede politikker, der hjælper med at sikre, at de enheder, dine medarbejdere bruger, er beskyttet. Dit sikkerhedsteam kan også tilføje nye politikker. Lad os f.eks. antage, at du vil anvende visse indstillinger på nogle enheder og andre indstillinger på andre enheder. Det kan du gøre ved at tilføje politikker, f.eks. næste generations beskyttelsespolitikker eller firewallpolitikker.

Når politikker tilføjes, kan du se, at der tildeles en prioritetsrækkefølge. Du kan redigere prioritetsrækkefølgen for de politikker, du definerer, men du kan ikke ændre prioritetsrækkefølgen for standardpolitikker. Lad os f.eks. antage, at du har tre beskyttelsespolitikker i næste generation for dine Windows klientenheder. I dette tilfælde er din standardpolitik nummer 3 i prioritet. Du kan ændre rækkefølgen af dine politikker med nummer 1 og 2, men standardpolitikken forbliver nummer 3 på listen. 

**Det vigtigste at huske på ved flere politikker er, at enheder kun modtager den første anvendte politik.** Med henvisning til vores tidligere eksempel på tre næste generations politikker kan du antage, at du har enheder, der er målrettet af alle tre politikker. I dette tilfælde modtager disse enheder politiknummer 1, men modtager ikke politikker nummer 2 og 3. 

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om Microsoft Defender til virksomheder</a>. Vi vil meget gerne høre fra dig!
>

## <a name="key-points-to-remember-about-policy-order"></a>Vigtige punkter at huske om politikrækkefølge

- Politikker tildeles en prioritetsrækkefølge.

- Enheder modtager kun den første anvendte politik.

- Du kan ændre prioritetsrækkefølgen for politikker.

- Standardpolitikker får den laveste prioritetsrækkefølge.

## <a name="next-steps"></a>Næste trin

- [Kom i gang med at bruge Defender for Business](mdb-get-started.md)

- [Administrer enheder](mdb-manage-devices.md)

- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)

- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)