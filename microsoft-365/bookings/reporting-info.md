---
title: Rapporteringsoplysninger for Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 03a9acc9-f29c-456b-9fb2-0f49474b2708
description: Få mere at vide om, hvordan du kan se en 4-måneders visning af din Bookings aktivitet
ms.openlocfilehash: 191194d112fe231c1a2f64245d33850ecb1266c0
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714301"
---
# <a name="reporting-info-for-bookings"></a>Rapporteringsoplysninger om Bookings

> [!NOTE]
> Denne artikel hjælper dig med at interagere med den nyeste version af Microsoft Bookings. Tidligere versioner udgår i de kommende måneder.

Du kan nu se en fire måneders visning af din Bookings kalender i en TSV-fil. I TSV-filen vises der fire måneders data, men du kan vælge forskellige fire måneder i løbet af et år.

Disse oplysninger på aftaleniveau kan bruges til at visualisere kundeaktiviteten omkring din Bookings kalender. TSV-filer er tabulatorseparerede værdifiler. Du kan få vist eller redigere en fil som denne med et hvilket som helst teksteditor- eller regnearksprogram, f.eks. Excel.

## <a name="see-four-months-of-booking-activity"></a>Se fire måneders bookingaktivitet

1. I Microsoft 365 skal du vælge appstarteren og derefter vælge **Bookings**.

1. Vælg **Eksportér** på startsiden Bookings.

1. På siden **Eksportér seneste data** skal du vælge dit datointerval og vælge **Eksportér**.

1. Gem filen under et nyt navn, og angiv .xls- eller xlsx-format.

1. Åbn filen for at se de fire måneders visning af din Bookings kalender.

1. Vælg datoen for din rapport, og vælg **Eksportér**.

1. Den downloadede rapport indeholder et nyt sæt felter ud over de eksisterende felter.

Rapporten indeholder følgende felter.

 - **Dato & klokkeslæt**
- **Kundenavn**
- **Kundemail**
- **Kunde Telefon**
- **Kundeadresse**
- **Personale**
- **Tjeneste**
- **Placering**
- **Varighed (minutter)**
- **Hændelsestype**

Den forbedrede rapport indeholder nu følgende felter.

- **Pristype**   Standardpristype, der er angivet for en tjeneste, når tjenesten oprettes.
- **Pris**   Pris, der svarer til den valgte pristype.
- **Valuta**   Valutatype, der er angivet for en virksomhed.
- **Cc-deltagere**   De modtagere, der modtager mailmeddelelser om en booking. Dette kan angives fra appen Teams, når du opretter en reservation.
- **Antal tilmeldte deltagere**   Hvor mange kunder reserverede en gruppebookingtjeneste.
- **Tekstbeskeder er aktiveret**   Om kunderne kan modtage sms-relaterede meddelelser.
- **Brugerdefinerede felter**   Alle spørgsmål og svar, der er relateret til en enkelt booking, kombineres i dette felt.
- **Booking-id**   Dette er nyttigt for at identificere de samme bookinger af en gruppetjeneste.
