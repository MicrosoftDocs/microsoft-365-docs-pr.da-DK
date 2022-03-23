---
title: Forstå faktureringsprofiler
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
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
ms.openlocfilehash: 472b5c4754d686877077133467e33592b5c0b85e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589182"
---
# <a name="understand-billing-profiles"></a>Forstå faktureringsprofiler

En faktureringsprofil indeholder en betalingsmetode, fakturaoplysninger og andre fakturaindstillinger, f.eks. indkøbsordrenummer og mailfakturaindstilling. Du bruger en faktureringsprofil til at betale for de produkter, du køber hos Microsoft. En faktureringsprofil oprettes automatisk, når en bruger foretager et selvbetjeningskøb. Hver faktureringsprofil faktureres separat.

> [!NOTE]
>
> Faktureringsprofiler er ikke tilgængelige for kunder, der køber produkter og tjenester fra Microsoft.com eller på siden Køb  tjenester Microsoft 365 Administration.

## <a name="what-are-billing-profile-roles"></a>Hvad er faktureringsprofilroller?

Roller på faktureringsprofiler har tilladelse til at kontrollere køb og få vist og administrere fakturaer. Tildel disse roller til brugere, der sporer, organiserer og betaler fakturaer. Medlemmer af indkøbsteamet i organisationen.

| Rolle                         | Beskrivelse                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Ejer af faktureringsprofil        | Administrer alt for en faktureringsprofil                                          |
| Faktureringsprofilbidrager  | Administrer alt undtagen tilladelser i en faktureringsprofil                        |
| Faktureringsprofillæser       | Skrivebeskyttet visning af alt i en faktureringsprofil                                |
| Fakturaadministrator              | Få vist og betal fakturaer, og har en skrivebeskyttet visning af alt i en faktureringsprofil  |

## <a name="view-my-billing-profiles"></a>Få vist mine faktureringsprofiler

> [!NOTE]
>
> Hvis du følger disse trin, og listen med faktureringsprofiler er tom, betyder det, at du ikke har en faktureringsprofil, og at du ikke kan bruge denne funktion.

1. I Administration skal du gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Faktureringsfakturering</a>  \> & betalinger.
2. Vælg fanen **Faktureringsprofil** , og vælg derefter en faktureringsprofil på listen.

Hver faktureringsprofil indeholder følgende oplysninger:

- **Navn og status for faktureringsprofil** &ndash; Det entydige navn på faktureringsprofilen, og om faktureringsprofilen er aktiv eller deaktiveret ved køb.
- **Fakturaindstillinger** &ndash; Valuta baseret på faktureringskontoens land, oplysninger om fakturafrekvens og dato, muligheden for at modtage fakturaer som vedhæftede filer i mails og et valgfrit felt til købsfakturanummer
- **Betalingsmetoder** &ndash; Viser den primære og sikkerhedskopierede betalingsmetode for profilen, hvis det er nogen.
- **Faktureringskonto** &ndash; Navnet på den faktureringskonto, som profilen er relateret til. Du kan finde flere oplysninger om faktureringskonti under [Forstå faktureringskonti](../manage-billing-accounts.md).
- **Kontaktoplysninger** &ndash; Faktureringsadresse og kontaktnavn og mailadresse
- **Faktureringsprofilroller** &ndash; En liste over personer, der er tildelt en af faktureringsprofilrollerne til at gøre ting for den pågældende profil. Betal f.eks. fakturaer, tilføj et KØBsordrenummer, eller erstat den betalingsmetode, der bruges til at foretage køb.

> [!NOTE]
>
> Du kan kun tildele faktureringsprofilroller til brugere i organisationen.

## <a name="need-help-contact-support"></a>Har du brug for hjælp? Kontakt support

Hvis du har spørgsmål eller har brug for hjælp til dine Azure-gebyrer, kan <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">du oprette en supportanmodning med Azure-support</a>.

Hvis du har spørgsmål eller har brug for hjælp til din faktureringsprofil i Microsoft 365 Administration, kan [du kontakte support](../../admin/get-help-support.md).

## <a name="related-content"></a>Relateret indhold

[Sådan betaler du for dit abonnement med en faktureringsprofil](pay-for-subscription-billing-profile.md) (artikel)\
[Forstå faktureringskonti](../manage-billing-accounts.md) (artikel)\
[Administrer betalingsmetoder](manage-payment-methods.md) (artikel)
