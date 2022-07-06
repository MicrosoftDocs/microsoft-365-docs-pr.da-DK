---
title: Få mere at vide om arkivpostkasser til Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Få mere at vide om arkivpostkasser for at levere ekstra postkasselager.
ms.openlocfilehash: 57de7c7791615e8587222de992588f1923348059
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621243"
---
# <a name="learn-about-archive-mailboxes"></a>Få mere at vide om arkivpostkasser

Arkivering af postkasser i Microsoft 365 (også kaldet *direkte arkivering*) giver brugerne ekstra lagerplads til postkassen. Når du har slået arkivpostkasser til, bliver en brugers aktuelle postkasse deres *primære postkasse* , og der oprettes en ekstra postkasse, der kaldes *arkivpostkassen*. Begge postkasser betragtes som en brugers postkasse for funktioner til overholdelse af angivne standarder, f.eks. indholdssøgning fra Microsoft Purview-compliance-portal, Microsoft 365-opbevaring og Procesførelseshold.

Brugerne kan få adgang til og gemme meddelelser i deres arkivpostkasser ved hjælp af Outlook og Outlook på internettet. Brugerne kan også flytte eller kopiere meddelelser mellem deres primære postkasse og deres arkivpostkasse. De kan også gendanne slettede elementer fra mappen Gendan elementer i deres arkivpostkasse ved hjælp af værktøjet Gendan slettet post.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>Administration af arkivpostkasser med MRM (Messaging Records Management)

Meddelelser kan også flyttes til arkivpostkassen af [exchange-standardopbevaringspolitikken](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) fra Messaging Records Management (MRM). Denne standardpolitik tildeles automatisk til alle postkasser og gør følgende:

  - Flytter elementer, der er to år eller ældre, fra en brugers primære postkasse til deres arkivpostkasse.

  - Flytter elementer, der er 14 dage eller ældre, fra mappen Gendanbare elementer i brugerens primære postkasse til mappen Gendanbare elementer i deres arkivpostkasse.

Du kan tilpasse organisationens MRM-politik med [opbevaringskoder](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). Du kan se et eksempel på konfiguration under [Konfigurer en politik for arkiv og sletning for postkasser i din organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

> [!NOTE]
> MRM, ligesom Microsoft 365-opbevaringspolitikker og opbevaringsmærkater, kan også automatisk slette mails efter en angivet periode. Som en ældre teknologi end Microsoft 365-opbevaring fungerer MRM fortsat side om side med opbevaringspolitikker og opbevaringsmærkater fra Microsoft Purview. Du kan få flere oplysninger under [Brug opbevaringspolitikker og opbevaringsmærkater i stedet for ældre funktioner](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>Arkivering, der automatisk udvides 

Når en brugers arkivpostkasse er aktiveret, er der op til 100 GB ekstra lagerplads tilgængelig. Hvis brugerne har brug for mere lagerplads, kan du aktivere automatisk udvidelse af arkivering for at levere op til 1,5 TB ekstra lagerplads i arkivpostkasser. Du kan finde flere oplysninger under [Få mere at vide om automatisk udvidelse af arkivering](autoexpanding-archiving.md).

## <a name="licensing"></a>Licensering

Du kan se en liste over Outlook-licenser, der understøtter arkivpostkasser, i referencer til In-Place Arkivering i [Outlook-licenskrav til Exchange-funktioner](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>Næste trin

Se [Aktivér arkivpostkasser i Microsoft Purview-compliance-portal](enable-archive-mailboxes.md).
