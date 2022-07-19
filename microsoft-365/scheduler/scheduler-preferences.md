---
title: Juster planlægningsindstillingerne for Oversigt over Tidsplaner for Microsoft 365
ms.author: shivb
author: shivbijlani
manager: charlle
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du justerer planlægningsindstillingerne for Scheduler for Microsoft 365.
ms.openlocfilehash: e6b6f4426b173bced90fcc8f2a705bc3e48cd09e
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "66858687"
---
# <a name="scheduling-preferences-used-by-scheduler"></a>Planlægningsindstillinger, der bruges af Planlægger

Planlægger bruger flere Outlook-indstillinger til at planlægge et møde for en arrangør. Eventuelle ændringer af indstillingerne i Outlook-klienter påvirker den måde, scheduler håndterer anmodninger, der sendes til Cortana. Hvis en assistent f.eks. ændrer tidszoneindstillingen på indstillingssiden i Outlook Web, vil alle anmodninger fra den efterfølgende arrangør som standard være den nye tidszone.

## <a name="supported-settings"></a>Understøttede indstillinger

- **Tidszone**. Tidszonen scheduler bruger til at bestemme et passende tidspunkt for møder. Se [Tilføj, fjern eller skift tidszoner for at](https://support.microsoft.com/en-us/office/add-remove-or-change-time-zones-5ab3e10e-5a6c-46af-ab48-156fedf70c04) få flere oplysninger.

- **Arbejdstimer og dage**. For de fleste mødetyper vælger Planlægger et tidspunkt i henhold til arrangørens indstillinger for arbejdsuge og mødetimer. Du kan få flere oplysninger [under Skift dine arbejdstimer og dage i Outlook](https://support.microsoft.com/en-us/office/change-your-work-hours-and-days-in-outlook-a27f261d-0681-415f-8ac1-388ab21e833f) .

- **Onlinemøder**. Du kan aktivere en kalenderindstilling, så alle de møder, du planlægger fra Outlook og Scheduler, bliver holdt online med mødeoplysninger. Planlægger understøtter i øjeblikket Teams og Skype som mødeudbydere. Se [Opret alle møder Teams-møder for at](https://support.microsoft.com/en-us/office/schedule-a-teams-meeting-from-outlook-883cc15c-580f-441a-92ea-0992c00a9b0f#bkmk_makeallteamsmtngs) få flere oplysninger.

- **Standardvarighed for møde**. Hvis arrangøren ikke angiver den ønskede mødevarighed i anmodningen, vil Scheduler bruge den foretrukne mødevarighed for anmodningen. Denne indstilling er kun tilgængelig i Windows Outlook-klienten.

   1. Vælg **Filindstillinger** >  for at se dialogboksen Outlook-indstillinger.

   2. Vælg **Kalender** på listen til venstre i dialogboksen.

   3. Under Indstillinger for kalender til højre for dialogboksen skal du vælge **Standardvarighed for nye aftaler og møder**.

      :::image type="content" source="../media/OutlookOptions.png" alt-text="Outlook Kalender dialogboks med indstillinger i Windows, hvor du kan konfigurere arbejdstid, standardmødevarighed og vælge forkortede møder, som Scheduler skal bruge.":::

- **Undgå back-to-back-møder**. En Outlook-indstilling kan starte møder for sent eller afslutte møder tidligt for at undgå back-to-back-møder. Planlægger kan også forkorte mødets varighed i henhold til de indstillinger, du har angivet. Se [Skift standardmødelængde](https://techcommunity.microsoft.com/t5/hybrid-work/change-default-meeting-length-in-outlook-avoid-back-to-back/m-p/1247361) for at få flere oplysninger.

> [!NOTE]
> Hvis du bruger Windows-klienten, skal du vælge **Gem mine Outlook-indstillinger i cloudmiljøet** for at synkronisere dine indstillinger på tværs af Scheduler og andre Outlook-klienter.
> :::image type="content" source="../media/OutlookOptions2.png" alt-text="dialogboksen Outlook Kalender indstillinger i Windows. Vælg Gem mine Outlook-indstillinger i skyen for at synkronisere planlægningsindstillingerne på tværs af klienter.":::
