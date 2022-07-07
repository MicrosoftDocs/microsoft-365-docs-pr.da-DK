---
title: Forstå faktureringsprofiler
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsBillingProfiles
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Få mere at vide om, hvordan faktureringsprofiler understøtter fakturaer.
ms.date: 04/02/2021
ms.openlocfilehash: 18e1eb23d0fcbdfd6eb374032f780a4f89a48cee
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66685871"
---
# <a name="understand-billing-profiles"></a>Forstå faktureringsprofiler

En faktureringsprofil indeholder en betalingsmetode, faktureringsoplysninger og andre fakturaindstillinger, f.eks. indkøbsordrenummer og mailfakturaindstillinger. Du kan bruge en faktureringsprofil til at betale for de produkter, du køber fra Microsoft. Faktureringsprofiler oprettes automatisk, og hver faktureres separat. 

> [!NOTE]
>
> Ikke alle konti har en faktureringsprofil. Hvis du ikke er sikker på, om du har en, kan du [få vist en liste over dine faktureringsprofiler] (administrer-faktureringsprofiler.md#view-my-fakturering-profiles).

## <a name="what-are-billing-profile-roles"></a>Hvad er faktureringsprofilroller?

Roller i faktureringsprofiler har tilladelse til at styre køb og få vist og administrere fakturaer. Tildel disse roller til brugere, der sporer, organiserer og betaler fakturaer. Det kan f.eks. være medlemmer af indkøbsteamet i din organisation.

| Rolle                         | Beskrivelse                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Ejer af faktureringsprofil        | Administrer alt for en faktureringsprofil                                          |
| Bidragyder til faktureringsprofil  | Administrer alt undtagen tilladelser i en faktureringsprofil                        |
| Læser til faktureringsprofil       | Skrivebeskyttet visning af alt i en faktureringsprofil                                |
| Fakturastyring              | Få vist og betal regninger, og har en skrivebeskyttet visning af alt i en faktureringsprofil  |

## <a name="view-my-billing-profiles"></a>Få vist mine faktureringsprofiler

> [!NOTE]
>
> Hvis du følger disse trin, og listen over faktureringsprofiler er tom, betyder det, at du ikke har en faktureringsprofil og ikke kan bruge denne funktion.

1. I Administration skal du gå til siden **Fakturering** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Fakturaer og betalinger</a>.
2. Vælg fanen **Faktureringsprofil** , og vælg derefter en faktureringsprofil på listen.

Hver faktureringsprofil indeholder følgende oplysninger:

- **Navn og status** &ndash; for faktureringsprofil Det entydige navn på faktureringsprofilen, og om faktureringsprofilen er aktiv eller deaktiveret for køb.
- **Fakturaindstillinger** &ndash; Valuta baseret på faktureringskontoens land, oplysninger om fakturahyppighed og -dato, muligheden for at modtage fakturaer som vedhæftede filer i mails og et valgfrit felt med et nummer på en faktura
- **Betalingsmetoder** &ndash; Viser den primære betalingsmetode og den eventuelle sikkerhedskopieringsmetode for profilen
- **Faktureringskonto** &ndash; Navnet på den faktureringskonto, som profilen er relateret til. Du kan få flere oplysninger om faktureringskonti under [Forstå faktureringskonti](../manage-billing-accounts.md).
- **Kontaktoplysninger** &ndash; Faktureringsadresse og kontaktnavn og mailadresse
- **Faktureringsprofilroller** &ndash; En liste over personer, der er tildelt en af faktureringsprofilrollerne til at gøre ting for den pågældende profil. Du kan f.eks. betale regninger, tilføje et nummer på en indkøbsordre eller erstatte den betalingsmetode, der bruges til at foretage køb.

> [!NOTE]
>
> Du kan kun tildele faktureringsprofilroller til brugere i din organisation.

## <a name="need-help-contact-support"></a>Har du brug for hjælp? Kontakt support

Hvis du har spørgsmål eller har brug for hjælp til dine Azure-gebyrer, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">kan du oprette en supportanmodning med Azure-support</a>.

Hvis du har spørgsmål eller har brug for hjælp til din faktureringsprofil i Microsoft 365 Administration, [skal du kontakte support](../../admin/get-help-support.md).

## <a name="related-content"></a>Relateret indhold

[Sådan betaler du for dit abonnement med en faktureringsprofil](pay-for-subscription-billing-profile.md) (artikel)\
[Forstå faktureringskonti](../manage-billing-accounts.md) (artikel)\
[Administrer betalingsmetoder](manage-payment-methods.md) (artikel)
