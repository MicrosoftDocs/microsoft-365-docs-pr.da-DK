---
title: Forstå faktureringskonti
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: tugu, jmueller
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
ms.date: 03/17/2021
ms.openlocfilehash: 8d80e94cbb415f93015673065e47d2fe36194bc0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588579"
---
# <a name="understand-billing-accounts"></a>Forstå faktureringskonti

Der oprettes en faktureringskonto, når du tilmelder dig for at prøve eller købe Microsoft-produkter. Du kan bruge din faktureringskonto til at administrere dine kontoindstillinger, fakturaer, betalingsmetoder og køb. Du kan få adgang til flere faktureringskonti. Du har f.eks. tilmeldt dig Microsoft 365 direkte, eller du har adgang til din organisations Enterprise Agreement-, Microsofts &-serviceaftale eller Microsoft-kundeaftale. Du skal have en separat faktureringskonto for hvert af disse scenarier.

Den <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> understøtter i øjeblikket følgende type faktureringskonti:

- Microsoft Online Services-program: Denne faktureringskonto oprettes, når du tilmelder dig et Microsoft 365-abonnement direkte.
- Microsofts &-serviceaftale (MPSA)-program: Denne faktureringskonto oprettes, når din organisation signerer en MPSA-volumenlicensaftale for at købe software og onlinetjenester.
- Microsoft-kundeaftale: Denne faktureringskonto oprettes, når din organisation arbejder sammen med en Microsoft-repræsentant, en autoriseret partner eller køber enkeltvis.

Siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Faktureringskonti</a> giver en visning af dine erhvervskonti hos Microsoft. Som standard har din organisation mindst én faktureringskonto knyttet til en aftale, der accepteres enten på tidspunktet for et direkte køb eller via en volumenlicensaftale.

## <a name="understand-billing-account-details"></a>Forstå oplysninger om faktureringskonto

Øverst på detaljesiden **for faktureringskonti** finder du din kontoprofil og indeholder juridiske oplysninger og momsoplysninger om din organisation. Du kan opdatere din profil for at ændre din juridiske adresse og dit telefonnummer. Denne konto er den juridiske enhed, der betaler for de produkter, du køber.

I følgende tabel vises de vigtige vilkår, som du kan se på **detaljesiden Faktureringskonti** .

| Feltnavn | Beskrivelse |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Solgt til-adresse | Den juridiske enhed, der er ansvarlig for betaling og identificeret på fakturaen. Den adresse, du angiver her, bruges til at fastlægge din momssats, medmindre du vælger at angive en alternativ leveringsadresse under dit køb. Du kan finde flere oplysninger [under Momsoplysninger](billing-and-payments/tax-information.md). |
| Segment | Et skrivebeskyttet felt, der identificerer virksomhedssegmentet for din organisation (kommerciel, uddannelse, offentlig eller almennyttig virksomhed). |
| Kontostatus | Et skrivebeskyttet felt, der angiver status for din kommercielle konto hos Microsoft. |
| Moms-id | Hvis du er uden for USA, skal du angive moms eller tilsvarende lokalt. Du kan finde flere oplysninger [under Momsoplysninger](billing-and-payments/tax-information.md). |
| Aftale | Når der oprettes en faktureringskonto, enten via et direkte køb eller en volumenlicensaftale, accepterer eller signerer en aftale, der skitserer vilkårene & betingelserne for kontoen. Hvis det er relevant, viser denne visning en aftaleoversigt. Hvis du skal acceptere opdaterede vilkår, vises et link til **Godkend** aftale. |
| Faktureringsprofiler | En faktureringsprofil definerer egenskaber for din faktura, f.eks. hvem der modtager fakturaen, hvordan fakturaen leveres, betalingsvilkår og et IP-nummer. Hvis du vil distribuere fakturering på tværs af din organisation, kan du oprette flere faktureringsprofiler og identificere den relevante faktureringsprofil på købstidspunktet. Du kan finde flere oplysninger om faktureringsprofiler, og hvordan du kan bruge dem til at opbygge mere fleksible faktureringsmuligheder for din organisation, [Forstå faktureringsprofiler](billing-and-payments/manage-billing-profiles.md). |

> [!NOTE]
> Hvis du har brug for at **ændre solgt til-navnet** eller -adressen, men ikke kan se  linket Rediger, skal du kontakte [support](../admin/get-help-support.md) for at ændre det. Anmodninger om en **ændring af solgt** til navn kræver en kreditkontrol. Udfyld [denne formular](https://www.microsoft.com/download/details.aspx?id=102732), og vær klar til at dele et af følgende dokumenter med Microsoft, når du kontakter support:
>
> - Offentligt udstedt dokument eller registreringsbrev
> - Udskriv af det lokale firmas registreringsdatabase
>
> Support kan hjælpe med navne- og adresseændringer, hvor kun kundenavnet ændres, men enheden forbliver den samme. Den angivne dokumentation skal tydeligt vise, at det kun er enhedens navn, der er blevet ændret. Hvis ændringen er resultatet af en transaktion, herunder salg af forretning, en ændring af kontrolelementer eller en divestiture eller "spinoff" af et kundetilkretur, skal du kontakte din Microsoft-sælger.

## <a name="shipping-addresses"></a>Leveringsadresser

I dette afsnit vises de leveringsadresser, der er knyttet til din faktureringskonto. Når du foretager et køb, kan du bruge denne adresse til at identificere, hvor dit køb er leveret eller brugt. Forsendelsesadressen kan redigeres. Du kan tilføje en leveringsadresse eller opdatere den eksisterende adresse. Denne adresse bruges til at fastlægge momssatsen for dit køb.

## <a name="understand-access-to-billing-accounts"></a>Forstå adgang til faktureringskonti

Du kan give andre adgang til faktureringskontoen i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> gennem roller og tilladelser. Kun en ejer af en faktureringskonto kan give adgang til en faktureringskonto. Du kan tildele en af følgende roller til brugere:

- **Ejer af faktureringskonto** &mdash; Kan tildele tilladelser, redigere konti, signere aftaler og få vist konti.
- **Faktureringskontobidrager** &mdash; Kan redigere konti, signere aftaler og få vist konti.
- **Læser til faktureringskonto** &mdash; Kan få vist konti.

> [!Note]
> Faktureringskontoroller gælder kun for faktureringskonti og gælder ikke for Microsoft 365 Administration scenarier.

## <a name="related-content"></a>Relateret indhold

[Momsoplysninger](billing-and-payments/tax-information.md) (artikel) \
[Forstå faktureringsprofiler](billing-and-payments/manage-billing-profiles.md) (artikel)
