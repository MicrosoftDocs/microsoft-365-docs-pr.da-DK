---
title: Administrer joinoplevelsen for virtuelle Teams-aftaler i browsere
author: lanachin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: ''
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- microsoftcloud-healthcare
- microsoftcloud-retail
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
ms.reviewer: hafarmer
description: Få mere at vide om joinoplevelsen for virtuelle Teams-aftaler i browsere.
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 869e554ed202f5e2ef24cf75e3dc2338c65de554
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823982"
---
# <a name="manage-the-join-experience-for-teams-virtual-appointments-on-browsers"></a>Administrer joinoplevelsen for virtuelle Teams-aftaler i browsere

Microsoft Teams gør det nemt for andre at deltage i virtuelle aftaler uden at skulle downloade Teams. For at få en mere problemfri oplevelse kan deltagerne deltage i aftaler som sundhedsbesøg og økonomiske konsultationer fra en stationær eller mobilbrowser. Deltagerne behøver ikke at installere Teams-appen på deres enhed.

Når en deltager tilmelder sig en aftale i browseren, bliver vedkommende ikke bedt om at downloade Teams. I stedet åbnes Teams i en browser, hvor deltagerne kan vælge **Deltag nu** for at deltage. Med denne funktion skal du huske på, at hvis Teams allerede er installeret på enheden, åbnes Teams i en browser og ikke i appen.

I øjeblikket er browserjoinforbindelse tilgængelig for aftaler, der er planlagt via følgende:

- [Appen Bookings](https://support.microsoft.com/office/what-is-bookings-42d4e852-8e99-4d8f-9b70-d7fc93973cb5)
- Microsoft Teams EHR-connector (Electronic Health Record)

  - Integration med [Cerner EHR](ehr-admin-cerner.md)
  - Integration med [Epic EHR](ehr-admin-epic.md)

## <a name="set-up-browser-join"></a>Konfigurer browserjoinforbindelse

### <a name="appointments-scheduled-through-the-bookings-app"></a>Aftaler, der er planlagt via Bookings-appen

Planlæggere i din organisation kan aktivere denne funktion for bestemte aftaletyper og for individuelle aftaler i appen Bookings.

Når denne funktion er slået til, indeholder bekræftelsesmailen eller sms'en, der sendes til deltagerne, et link til mødetilføjelse, der åbner Teams i en skrivebords- eller mobilbrowser. Du kan se en liste over understøttede browsere under [Understøttede browsere](#supported-browsers).

#### <a name="turn-on-browser-join-for-an-appointment-type"></a>Slå browserjoinforbindelse til for en aftaletype

I Bookinger skal du gå til **Indstillinger** > **Aftaletyper**, vælge en [aftaletype](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887) og derefter aktivere **Tillad deltagere at deltage fra en browser**. Hvis du gør det, aktiveres browserjoinforbindelse for alle aftaler af denne type.

:::image type="content" source="media/browser-join-bookings-appointment-type.png" alt-text="Skærmbillede af indstillingen Tillad, at deltagere kan deltage fra en browser for aftaletyper i appen Bookings":::

#### <a name="turn-on-browser-join-for-an-individual-appointment"></a>Slå browserjoinforbindelse til for en individuel aftale

I Bookinger skal du vælge **Ny booking** og derefter aktivere **Tillad, at deltagere kan deltage fra en browser**.

:::image type="content" source="media/browser-join-bookings-form.png" alt-text="Skærmbillede af indstillingen Tillad, at deltagere kan deltage fra en browser i den nye bookingformular i appen Bookings":::

### <a name="appointments-scheduled-through-the-teams-ehr-connector"></a>Aftaler, der er planlagt via Teams EHR-connectoren

Der kræves ingen konfiguration af dig eller dine medarbejdere!

**Integration med Cerner EHR**: Teams EHR-connectoren understøtter patienter, der deltager i virtuelle aftaler via et link i SMS-sms'en. På tidspunktet for aftalen kan patienterne deltage ved at trykke på linket i SMS-sms'en, og Teams åbnes i en browser.

**Integration med Epic EHR**: Teams EHR-connectoren understøtter patienter, der deltager i virtuelle aftaler via MyChart-web og mobil. På tidspunktet for aftalen kan patienterne starte aftalen fra MyChart ved hjælp af knappen **Start virtuelt besøg** , og Teams åbnes i en browser.

## <a name="supported-browsers"></a>Understøttede browsere

Her er de browsere, der understøttes i øjeblikket. Vi understøtter den nyeste version plus to tidligere versioner, medmindre andet er angivet.

|Platform  |Chrome |Safari |Kant (Chromium)|
|---------|:---|:---|:---:|
|Android   | &#x2714; &1.      |         |         |
|Ios    |         | &#x2714; &1. &, sup2; |         |
|Macos     | &#x2714; | &#x2714;|         |
|Windows    | &#x2714; |   | &#x2714; |
|Ubuntu/Linux     | &#x2714;         |     |         |

&1. Udgående skærmdeling understøttes ikke på iOS eller Android.

&, sup2; iOS-apps på Safari kan ikke vælge mikrofon- og højttalerenheder. For eksempel Bluetooth-enheder. Dette er en begrænsning i operativsystemet, som styrer valg af standardenhed.

## <a name="things-to-consider"></a>Ting, du skal overveje

Den medarbejder, der udfører aftalen, kan dele deres skærm fra deres Teams-skrivebords-, mobil- eller webklient med en deltager, der tilmelder sig fra en skrivebords- eller mobilbrowser. Deltagerne kan dog ikke dele deres skærm fra en desktop- eller mobilbrowser.

## <a name="related-articles"></a>Relaterede artikler

- [Virtuelle aftaler med Teams og Bookings-appen](bookings-virtual-visits.md)
- [Opret en bookingaftaletype](https://support.microsoft.com/office/create-an-appointment-type-810eac77-6a65-4dc8-964d-c00eadf43887)
- [Deltag i en Bookings-aftale som deltager](https://support.microsoft.com/office/join-a-bookings-appointment-as-an-attendee-95cea12d-2220-421f-a663-6efb20913c7f)
- [Virtuelle aftaler med Teams – integration i Cerner EHR](ehr-admin-cerner.md)
- [Virtuelle aftaler med Teams – integration i Epic EHR](ehr-admin-epic.md)
