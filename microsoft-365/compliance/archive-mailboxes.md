---
title: Få mere at vide om arkivpostkasser til Microsoft 365 overholdelse af regler og standarder
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
description: Få mere at vide om arkivpostkasser, som giver ekstra lagerplads til postkasser.
ms.openlocfilehash: a863df7be1b73d6a50d818bca5948f3017e3d373
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63596996"
---
# <a name="learn-about-archive-mailboxes"></a>Få mere at vide om arkivpostkasser

Postkassearkivering i Microsoft 365 (også *kaldet direkte arkivering*) giver brugerne yderligere lagerplads til postkassen. Når du har aktiveret arkivpostkasser, bliver en brugers aktuelle postkasse til  deres primære postkasse, og der oprettes en ekstra postkasse, som kaldes *arkivpostkassen*. Begge postkasser betragtes som en brugers postkasse til overholdelsesfunktioner som f.eks indholdssøgning fra Microsoft 365 Overholdelsescenter, Microsoft 365 opbevaring og retslig tilbageholdelse.

Brugere kan få adgang til og gemme meddelelser i deres arkivpostkasser ved hjælp Outlook og Outlook på internettet. Brugere kan også flytte eller kopiere meddelelser mellem deres primære postkasse og deres arkivpostkasse. De kan også gendanne slettede elementer fra mappen Genoprettelige elementer i deres arkivpostkasse ved hjælp af værktøjet Gendan slettede elementer.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>Administrere arkivpostkasser med MRM (Messaging Records Management)

Meddelelser kan også flyttes til arkivpostkassen som standard Exchange [opbevaringspolitik](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) fra MESSAGING Records Management (MRM). Denne standardpolitik tildeles automatisk til alle postkasser og gør følgende:

  - Flytter elementer, der er to år eller ældre fra en brugers primære postkasse til arkivpostkassen.

  - Flytter elementer, der er 14 dage eller ældre, fra mappen Genoprettelige elementer i brugerens primære postkasse til mappen Genoprettelige elementer i brugerens arkivpostkasse.

Du kan tilpasse din organisations MRM-politik med [opbevaringsmærker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). Se Konfigurer en arkiverings [- og sletningspolitik for postkasser i organisationen for](set-up-an-archive-and-deletion-policy-for-mailboxes.md) eksempel konfiguration.

> [!NOTE]
> MRM, f.Microsoft 365 opbevaringspolitikker og opbevaringsetiketter, kan også automatisk slette mails efter en bestemt periode. Som en ældre teknologi end Microsoft 365 opbevaring, fortsætter MRM med at arbejde side om side med opbevaringspolitikker og opbevaringsetiketter Microsoft 365 Overholdelse af regler og standarder. Få mere at vide under [Brug opbevaringspolitikker og opbevaringsmærkater i stedet for ældre funktioner](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>Automatisk udvidende arkivering 

Når en brugers arkivpostkasse er aktiveret, får du adgang til op til 100 GB ekstra lagerplads. Hvis brugerne har brug for mere lagerplads, kan du aktivere automatisk arkivering for at give op til 1,5 TB ekstra lagerplads i arkivpostkasser. Få mere at vide under [Få mere at vide om automatisk udvidende arkivering](autoexpanding-archiving.md).

## <a name="licensing"></a>Licensering

Du kan finde en liste Outlook licenser, der understøtter arkivpostkasser, under referencerne til In-Place Arkivering [Outlook licenskrav til Exchange funktioner](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>Næste trin

Se [Aktivér arkivpostkasser i overholdelsescenter](enable-archive-mailboxes.md).