---
title: Forstå faktureringskonti
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Få mere at vide om faktureringskonti, og hvordan de bruges til at administrere kontoindstillinger, fakturaer, betalingsmetoder og køb.
ms.date: 05/24/2022
ms.openlocfilehash: 0c1dd2048cbe38ecca162f361f3f0bdbc6c3861f
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670052"
---
# <a name="understand-billing-accounts"></a>Forstå faktureringskonti

Der oprettes en faktureringskonto, når du tilmelder dig for at prøve eller købe Microsoft-produkter. Du kan bruge din faktureringskonto til at administrere dine kontoindstillinger, fakturaer, betalingsmetoder og køb. Du kan få adgang til flere faktureringskonti. Du har f.eks. tilmeldt dig Microsoft 365 direkte, eller du har adgang til organisationens Enterprise Agreement, Microsoft Product & Services Agreement eller Microsoft-kundeaftale. I hvert af disse scenarier har du en separat faktureringskonto.

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration understøtter</a> i øjeblikket følgende type faktureringskonti:

- Microsoft Online Services Program: Denne faktureringskonto oprettes, når du tilmelder dig et Microsoft 365 abonnement direkte.
- Microsoft Products & Services Agreement (MPSA) Program: Denne faktureringskonto oprettes, når din organisation signerer en MPSA-volumenlicensaftale for at købe software og onlinetjenester.
- Microsoft-kundeaftale: Denne faktureringskonto oprettes, når din organisation arbejder sammen med en Microsoft-repræsentant, en autoriseret partner eller køber uafhængigt af hinanden.

På siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Faktureringskonti</a> kan du se dine kommercielle konti hos Microsoft. Din organisation har som standard mindst én faktureringskonto tilknyttet en aftale, der accepteres enten på tidspunktet for et direkte køb eller via en volumenlicensordning.

## <a name="understand-billing-account-details"></a>Forstå oplysninger om faktureringskonto

Øverst på siden med oplysninger om **faktureringskonti** er din kontoprofil og indeholder juridiske og skatteoplysninger om din organisation. Du kan opdatere din profil for at ændre din juridiske adresse og dit telefonnummer. Denne konto er den juridiske enhed, der betaler for de produkter, du køber.

I følgende tabel vises de vigtige ord, du kan se på siden med oplysninger om **faktureringskonti** .

| Feltnavn | Beskrivelse |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Solgt til-adresse | Den juridiske enhed, der er ansvarlig for betalingen og identificeret på fakturaen. Den adresse, der angives her, bruges til at bestemme din skattesats, medmindre du vælger at angive en alternativ leveringsadresse under dit køb. Du kan få flere oplysninger under [Skatteoplysninger](billing-and-payments/tax-information.md). |
| Segment | Et skrivebeskyttet felt, der identificerer forretningssegmentet i din organisation (Commercial, Education, Government eller Non-profit). |
| Kontostatus | Et skrivebeskyttet felt, der angiver status for din kommercielle konto hos Microsoft. |
| Moms-id | Hvis du befinder dig uden for USA, skal du angive en moms eller en lokal ækvivalent. Du kan få flere oplysninger under [Skatteoplysninger](billing-and-payments/tax-information.md). |
| Aftale | Når der oprettes en faktureringskonto, enten via et direkte køb eller en volumenlicensordning, accepterer eller signerer en underskriver for organisationen en aftale, der beskriver vilkårene & betingelser for kontoen. Hvis det er relevant, viser denne visning en aftaleoversigt. Hvis du skal acceptere opdaterede vilkår, vises der et link til **Godkend aftale** . |
| Faktureringsprofiler | En faktureringsprofil definerer egenskaberne for din faktura, f.eks. hvem der modtager fakturaen, hvordan fakturaen leveres, betalingsvilkår og et nummer til en indkøbsordre. Hvis du vil distribuere fakturering på tværs af din organisation, kan du oprette flere faktureringsprofiler og identificere den relevante faktureringsprofil på købstidspunktet. Du kan få flere oplysninger om faktureringsprofiler, og hvordan du kan bruge dem til at oprette mere fleksible faktureringsmuligheder for din organisation, [forstå faktureringsprofiler](billing-and-payments/manage-billing-profiles.md). |

> [!NOTE]
> Hvis du har brug for at ændre **Solgt til-navn** eller -adresse, men ikke kan se linket **Rediger** , skal du [kontakte support](../admin/get-help-support.md) for at ændre det. Anmodninger om en ændring **af Solgt til-navn** kræver en kreditkontrol. Udfyld [denne formular](https://www.microsoft.com/download/details.aspx?id=102732), og vær klar til at dele et af følgende dokumenter med Microsoft, når du kontakter support:
>
> - Statsudstedt dokument eller registreringsbrev
> - Udskriv den lokale virksomheds registreringsdatabase
>
> Support kan hjælpe med ændringer af navn og adresse, hvor kun kundenavnet ændres, men objektet forbliver det samme. Den angivne dokumentation skal tydeligt vise, at kun enhedens navn er ændret. Hvis ændringen er resultatet af en transaktion, herunder salg af forretning, ændring af kontrolelementer eller afhændelse eller "spinoff" af en kundes affiliate, skal du kontakte din Microsoft-sælger.

## <a name="shipping-addresses"></a>Forsendelsesadresser

I dette afsnit vises de leveringsadresser, der er knyttet til din faktureringskonto. Når du foretager et køb, kan du bruge denne adresse til at identificere, hvor dit køb leveres eller bruges. Forsendelsesadressen kan redigeres. Du kan tilføje en leveringsadresse eller opdatere den eksisterende adresse. Denne adresse bruges til at bestemme momssatsen for dit køb.

## <a name="understand-access-to-billing-accounts"></a>Forstå adgang til faktureringskonti

Du kan give andre adgang til faktureringskontoen i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> via roller og tilladelser. Det er kun ejeren af en faktureringskonto, der kan give adgang til en faktureringskonto. Du kan tildele en af følgende roller til brugere:

- Ejer &mdash; **af faktureringskonto** Kan tildele tilladelser, redigere konti, signere aftaler og få vist konti.
- **Bidragyder til** &mdash; faktureringskonto Kan redigere konti, signere aftaler og få vist konti.
- Læser &mdash; **af faktureringskonto** Kan få vist konti.

> [!Note]
> - Faktureringskontoroller gælder kun for faktureringskonti og gælder ikke for andre Microsoft 365 Administration scenarier.
> - For faktureringskonti, der oprettes i Microsoft 365 tilmelding, tildeles nye administratorer af Global, Fakturering og Global Reader automatisk særskilte adgangsniveauer. Du kan administrere denne adgang fra siden **Faktureringskonti** >  ved udtrykkeligt at fjerne disse brugere fra afsnittet om rolletildeling nederst på siden.

## <a name="related-content"></a>Relateret indhold

[Skatteoplysninger](billing-and-payments/tax-information.md) (artikel) \
[Forstå faktureringsprofiler](billing-and-payments/manage-billing-profiles.md) (artikel)
