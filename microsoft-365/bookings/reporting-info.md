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
description: Få mere at vide om, hvordan du kan se en 4-månedsvisning af dine Bookings-aktiviteter
ms.openlocfilehash: 70d73da86e40555a5754a4284cbfbb0510e8c9e6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601657"
---
# <a name="reporting-info-for-bookings"></a>Rapporteringsoplysninger for Bookinger

Du kan nu se en fire måneders visning af din Bookings-kalender i en TSV-fil. TSV-filen viser dig fire måneders data, men du kan vælge forskellige perioder på fire måneder i løbet af et år.

Disse oplysninger på aftaleniveau kan bruges til at visualisere kundeaktiviteten omkring din Bookings-kalender. TSV-filer er tabulatorseparerede værdifiler. Du kan få vist eller redigere en fil som denne i et teksteditor- eller regnearksprogram, f.eks Excel.

## <a name="see-four-months-of-booking-activity"></a>Se fire måneders Booking-aktivitet

1. I Microsoft 365 skal du vælge Appstarteren og derefter vælge **Bookinger**.

1. På Bookings-startsiden skal du vælge **Eksportér**.

1. På siden **Eksportér seneste data** skal du vælge dit datointerval og vælge **Eksportér**.

1. Gem filen under et nyt navn, og angiv .xls eller xlsx-format.

1. Åbn filen for at få vist fire månedersvisning af Bookings-kalenderen.

1. Vælg datoen for rapporten, og vælg **Eksportér**.

1. Den hentede rapport indeholder et nyt sæt felter ud over de eksisterende felter.

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

- **Pristype**   Standardpristype, der er angivet for en tjeneste, når du opretter tjenesten.
- **Pris**   Pris, der svarer til den valgte pristype.
- **Valuta**   Valutatype angivet for en virksomhed.
- **Cc-deltagere**   De modtagere, der modtager mailbeskeder om en booking. Denne kan angives fra appen Teams, når du opretter en booking.
- **Antal deltagere tilmeldt**   Hvor mange kunder reserverede en gruppebookingtjeneste.
- **Sms-beskeder aktiveret**   Om kunderne kan modtage sms-relaterede beskeder.
- **Brugerdefinerede felter**   Alle de spørgsmål og svar, der er relateret til en enkelt booking, kombineres i dette felt.
- **Booking-id**   Dette er nyttigt for at identificere de samme bookinger for en gruppetjeneste.
