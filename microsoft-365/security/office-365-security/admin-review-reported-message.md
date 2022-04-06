---
title: Administratorgennemsyn for rapporterede meddelelser
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Få mere at vide om, hvordan du gennemser meddelelser, der rapporteres, og giver feedback til dine brugere.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 44476e7a8ad3bad9b21e82a9528593ceb350257d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470895"
---
# <a name="admin-review-for-reported-messages"></a>Administratorgennemsyn for rapporterede meddelelser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med Exchange Online postkasser og Microsoft Defender for Office 365 kan administratorer nu sende skabelonmeddelelser tilbage til slutbrugere, efter de har gennemset rapporterede meddelelser. Skabelonerne kan tilpasses til din organisation og baseres også på din administrators konklusion.

Funktionen er designet til at give feedback til dine brugere, men ændrer ikke konklusionen af meddelelser i systemet. For at hjælpe Microsoft med at opdatere og forbedre filtrene skal du sende meddelelser til analyse ved hjælp af [administratorindsendelse](admin-submission.md).

Du vil kun kunne markere og give brugere besked om korrekturresultater, hvis meddelelsen blev rapporteret som en [falsk positiv eller falsk negativ](report-false-positives-and-false-negatives.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

- Hvis du vil ændre konfigurationen for brugerindsendelser, skal du være medlem af en af følgende rollegrupper:
  - Organisationsadministration eller sikkerhedsadministrator i [Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).
  - Organisationsadministration [i Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Du skal også have adgang til Exchange Online PowerShell. Hvis den konto, du forsøger at bruge, ikke har adgang til Exchange Online PowerShell, modtager du en fejl, hvor der står Angiv en mailadresse i *dit domæne*. Du kan finde flere oplysninger om aktivering eller deaktivering af Exchange Online PowerShell under følgende emner:
  - [Aktivér eller deaktiver adgang til Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Regler for klientadgang i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="notify-users-from-within-the-portal"></a>Giv besked til brugere inde fra portalen

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **siden Indsendelser på &** **indsendelser af** \> **samarbejde**. For at gå direkte til siden **Indsendelser** skal du bruge <https://security.microsoft.com/reportsubmission>.

2. Klik **på Brugerrapporterede** meddelelser, og vælg derefter den meddelelse, du vil markere og underrette.

3. Vælg **rullelisten Markér som og giv** besked, og vælg derefter **Ingen trusler** fundet, **Phishing** eller **Uønsket**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/admin-review-send-message-from-portal.png" alt-text="Den side, der viser de brugerrapporterede meddelelser" lightbox="../../media/admin-review-send-message-from-portal.png":::

Den rapporterede meddelelse markeres som enten falsk positiv eller falsk negativ, og en mail sendes automatisk fra portalen og underretter den bruger, der rapporterede meddelelsen.

## <a name="customize-the-messages-used-to-notify-users"></a>Tilpasse de meddelelser, der bruges til at give brugerne besked

1. I Microsoft 365 Defender på   <https://security.microsoft.com>skal du gå til siden Brugerindsendelser på Mail **&-samarbejdspolitikker** \> **& Regler** \> \> for trusselspolitikker Brugeren har rapporteret **meddelelsesindstillinger** i **sektionen Andre.** For at gå direkte til **siden Brugerindsendelser** skal du bruge <https://security.microsoft.com/userSubmissionsReportMessage>.

2. Hvis du vil angive **afsenderens** viste navn på siden Brugerindsendelser, skal du markere afkrydsningsfeltet Angiv **Office 365-mailadresse**, der skal bruges som afsender under sektionen Mailbeskeder til administratorgennemsyn af resultater og skrive det navn, du vil bruge. Den mailadresse, der vises i Outlook, og alle svarene sendes dertil.

3. Hvis du vil tilpasse en af skabelonerne, skal du **klikke på Tilpas mailmeddelelse** nederst på siden. I pop op-dialogboksen, der åbnes, kan du kun tilpasse følgende:

    - Phishing
    - Uønsket
    - Der blev ikke fundet nogen trusler
    - Sidefod

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/admin-review-customize-message.png" alt-text="Siden Med bekræftelsesmeddelelsen Tilpas" lightbox="../../media/admin-review-customize-message.png":::

4. Klik på **Gem**, når du er færdig. Hvis du vil rydde disse værdier, skal **du klikke på** Slet **på siden Brugerindsendelser** .
