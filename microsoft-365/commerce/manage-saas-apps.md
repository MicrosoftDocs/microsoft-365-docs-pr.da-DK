---
title: Administrer SAAS-apps for din organisation
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid: MET150
description: Få mere at vide om, hvordan du aktiverer og administrerer tredjepartsapps i Microsoft 365 Administration.
ms.date: 04/15/2021
ms.openlocfilehash: c85a0c93ee7f17953f7877cc1fd97765e0e63afd
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713861"
---
# <a name="manage-third-party-app-subscriptions-for-your-organization"></a>Administrer appabonnementer fra tredjepart for din organisation

Du kan administrere licenser og fakturering for tredjepartsapps i den nye <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Opdaterede funktioner omfatter forbedret abonnementsadministration, forbedret adgang til faktureringsoplysninger og forbedret fleksibilitet til administration af regninger. Administration af abonnementer er baseret på Microsofts opdaterede handelsplatform. Dette gælder for software-as-a-service-apps, som kunderne køber direkte eller fra en tredjepartsudbyder.

## <a name="how-to-get-software-as-a-service-apps"></a>Sådan får du apps fra software som en tjeneste

Der er et par måder at købe tredjepartsapps på.

- **Direkte køb** – kunder kan købe abonnementer direkte fra [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/) eller [AppSource](https://appsource.microsoft.com/).
- **Partnerkøb** – samarbejd med en partner via Partnercenter for at købe abonnementer.
- **Microsoft-forslag** – Svar på et forslag fra Microsoft Sales, der indeholder tredjepartsapps.

Når kunderne køber appsene og accepterer Microsoft-kundeaftale, kan de administrere dem i Microsoft 365 Administration eller Microsoft Store til Virksomheder.

Appudbydere sælger deres apps enten til en fast pris eller ved at købe licenser til brugere.

- **Fast pris** – også kaldet webstedsbaserede priser, apps prissættes med en månedlig eller årlig pris. På appsiden vises licensantallet på Ubegrænset.
- **Licenser** – apps prissættes efter licens. Kunder tildeler licenser til hver bruger i deres organisation

## <a name="supported-regions"></a>Understøttede områder

Understøttelse af tredjepartsapps er tilgængelig i disse områder:

- Argentina
- Australien
- Canada
- Chile
- Frankrig
- Tyskland
- Grækenland
- Puerto Rico
- Sydafrika
- Storbritannien
- USA
- Vesteuropa

## <a name="activate-third-party-apps"></a>Aktivér tredjepartsapps

Administratorer skal aktivere tredjepartsapps, før de kan tildele dem til brugere. Disse apps er aktiveret på tredjepartsudgiverens portal.

1. I Administration skal du gå til siden **FaktureringAf** >  **dine** <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">produkterApps</a> > .
2. Find og vælg den app, du vil administrere.
3. Under **Indstillinger & handlinger** skal du vælge **Administrer på udgiverportalen**.

Du bliver dirigeret til appudgiverens websted, hvor du kan aktivere appen.

## <a name="manage-third-party-apps"></a>Administrer tredjepartsapps

Administratorer administrerer tredjepartsapps på to placeringer: Microsoft 365 Administration og tredjepartsappudbyderens portal.

Her er, hvad du kan gøre på hver portal.

| Microsoft 365 Administration | Portal til appudgiver |
| --- | --- |
| Skift licensantal <br> Administrer, hvordan du betaler din regning <br> Administrer, hvordan du betaler din regning <br> Skift betalingsmetode (kreditkort) <br> Vis faktura <br> Annuller appabonnement | Konfigurer app (én gang for hver app) <br> Tildel licenser til brugerne <br> Teknisk support |

Når appen er aktiveret, forbliver den aktiv, medmindre den annulleres, udløber, eller hvis betalingen ikke holdes opdateret. Disse hændelser ændrer appens status til deaktiveret. Når en app er deaktiveret, kan den ikke genaktiveres. Hvis du vil fortsætte med at bruge appen, skal du købe en anden kopi af den.

## <a name="assign-licenses"></a>Tildel licenser

Administratorer skal aktivere tredjepartsapps, før de tildeles til brugere. De er aktiveret på tredjepartsudgiverens portal. På appsiden under **Indstillinger & handlinger** skal du vælge linket for at tildele licenser.

1. I Administration skal du gå til siden **FaktureringAf** >  **dine** <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">produkterApps</a> > .
2. Find og vælg den app, du vil administrere.
3. Under **Indstillinger & handlinger** skal du vælge linket til **Administrer på udgiverportalen**.

## <a name="change-license-quantity"></a>Skift licensantal

Administratorer kan ændre antallet af licenser, der ejes af deres organisation. Dette gælder kun for apps, der er købt med sædebaserede priser.

1. I Administration skal du gå til siden **FaktureringAf** >  **dine** <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">produkterApps</a> > .
2. Find og vælg den app, du vil administrere.
3. Vælg **Skift licensantal**.

## <a name="manage-payment-methods"></a>Administrer betalingsmetoder

Software-as-a-service-apps har hver fået tildelt en faktureringsprofil. Med faktureringsprofiler kan du tilpasse, hvilke produkter der er inkluderet på din faktura, og hvordan du betaler dine fakturaer. De omfatter:

- **Betalingsmetoder** – kreditkort eller check/bankoverførsel
- **Kontaktoplysninger** – faktureringsadresse og et kontaktnavn
- **Roller** – roller, der giver dig mulighed for at ændre faktureringsprofilen, betale regninger eller bruge betalingsmetoden på faktureringsprofilen til at foretage køb.

Du kan få flere oplysninger om faktureringsprofiler under [Forstå faktureringsprofiler](/microsoft-store/billing-profile).

### <a name="change-the-billing-profile-on-a-software-as-a-service-app-subscription"></a>Skift faktureringsprofilen for et appabonnement på en software som en tjeneste

1. I Administration skal du gå til siden **FaktureringAf** >  **dine** <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">produkterApps</a> > .
2. Find og vælg den app, du vil administrere.
3. Ud for **Faktureringsprofil** skal du vælge **Rediger**.

Du kan få flere oplysninger om fakturaer under [Forstå din faktura.](billing-and-payments/understand-your-invoice.md)

## <a name="cancel-a-software-as-a-service-app-subscription"></a>Annuller et appabonnement på en software som en service

Du kan annullere en app med software som en tjeneste fra appsiden.

1. I Administration skal du gå til siden **FaktureringAf** >  **dine** <a href="https://go.microsoft.com/fwlink/p/?linkid=2125823" target="_blank">produkterApps</a> > .
2. Find og vælg den app, du vil administrere.
3. Under **Indstillinger & handlinger** skal du vælge **Annuller abonnement**.
