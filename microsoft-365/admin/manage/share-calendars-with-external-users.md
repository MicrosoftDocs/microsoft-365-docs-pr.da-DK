---
title: Dele kalendere med eksterne brugere
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd
description: Aktivér kalenderdeling på Microsoft 365 Administration så brugere kan dele deres kalendere med alle i eller uden for organisationen.
ms.openlocfilehash: 00ae4b96c54ae6b1471a90f598b9f96821947db3
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63599750"
---
# <a name="share-calendars-with-external-users"></a>Dele kalendere med eksterne brugere

Nogle gange er det nødvendigt, at dine brugere planlægger møder med personer uden for organisationen. For at gøre det nemmere at finde almindelige mødetider kan Microsoft 365 gøre kalendere tilgængelige for disse personer. Disse er personer, der har brug for at se ledige og optagede tider for brugere i organisationen, men som ikke har brugerkonti til din Microsoft 365 organisation.

Du kan aktivere kalenderdeling for alle brugere i organisationen i Microsoft 365 Administration. Når deling er aktiveret, kan brugerne bruge Outlook Web App til at dele deres kalendere med alle i eller uden for organisationen. Personer i organisationen kan se den delte kalender sammen med deres egen kalender. Personer uden for organisationen vil blive sendt en URL-adresse, som de kan bruge til at få vist kalenderen. Brugerne i din organisation bestemmer, hvornår de vil dele, og hvor meget de vil dele.

> [!NOTE]
> Hvis du vil dele kalendere med en organisation, der bruger Exchange Server 2013 (en lokal løsning), skal Exchange-administratoren konfigurere en godkendelsesrelation til skyen. Dette kaldes sammenslutning og skal opfylde minimumskravene til software. Se [Deling](/exchange/sharing-exchange-2013-help) for at få flere oplysninger.
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Aktivér kalenderdeling ved hjælp af Microsoft 365 Administration

1. I Administration skal du gå til **Indstillinger** \> **Org-indstillingerne**, og på <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**fanen Tjenester** skal</a> du vælge **Kalender**.
  
3. På siden **Kalender** skal du vælge, om du vil give brugere mulighed for at dele deres kalendere med personer uden for organisationen, som har Microsoft 365 eller Exchange. Vælg, om du vil give anonyme brugere (brugere uden legitimationsoplysninger) tilladelse til at få adgang til kalendere via en invitation via mail.

4. Vælg, hvilken type kalenderoplysninger der skal stilles til rådighed for brugerne. Du kan tillade alle oplysninger, eller du kan begrænse dem til kun tid, emne og kun placering.

## <a name="external-sharing-sync-interval"></a>Synkroniseringsinterval for ekstern deling

Øjeblikkelig synkronisering for deling uden for din lejer understøttes ikke i øjeblikket. Selvom du kan dele i disse konfigurationer, sker synkronisering med jævne mellemrum. Der findes to typer deling på tværs af lejere:

1. **Microsoft 365 en Microsoft 365 anden Microsoft 365 (** hvis ekstern deling er aktiveret): Der oprettes en fuldt delt kalender, men synkroniseringen sker ca. hver tredje time. Øjeblikkelig synkronisering vil med tiden blive aktiveret for denne konfiguration.

2. **Microsoft 365 til en Outlook.com-bruger**: Hvis ekstern deling er deaktiveret, hører deling med en anden Microsoft 365-bruger også ind under denne gruppe. Der genereres en ICS-URL-adresse ved deling, som modtageren kan bruge til at føje til en hvilken som helst kalendertjeneste. Med et ICS-abonnement vælger modtagerens kalendertjeneste, hvornår ICS-abonnementet skal synkroniseres for at modtage nye opdateringer. Hvis modtageren er en Outlook.com- eller Microsoft 365, sker synkroniseringen ca. hver tredje time.

## <a name="invite-people-to-access-calendars"></a>Inviter personer til at få adgang til kalendere

Når deling er aktiveret, kan kalenderejere sende invitationer til bestemte brugere. Du kan finde en vejledning [under Dele din kalender i Outlook Web App](https://support.microsoft.com/office/7ecef8ae-139c-40d9-bae2-a23977ee58d5).

## <a name="related-content"></a>Relateret indhold

[Slå ekstern deling til eller fra for et websted](/sharepoint/change-external-sharing-site) (artikel)\
[Oversigt over Microsoft 365 Administration](../admin-overview/admin-center-overview.md) (video)\
[Administrer mail og kalendere](/admin) (linkside)

