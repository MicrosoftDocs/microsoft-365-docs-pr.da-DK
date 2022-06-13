---
title: Del kalendere med eksterne brugere
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
description: Aktivér kalenderdeling i Microsoft 365 Administration, så brugerne kan dele deres kalendere med alle i eller uden for organisationen.
ms.openlocfilehash: b3ca1d4f2a6ef24a6958b4fe805ccf617c0984e7
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043138"
---
# <a name="share-microsoft-365-calendars-with-external-users"></a>Del Microsoft 365 kalendere med eksterne brugere

Det er nogle gange nødvendigt for dine brugere at planlægge møder med personer uden for din organisation. Hvis du vil forenkle processen med at finde almindelige mødetider, kan du Microsoft 365 gøre kalendere tilgængelige for disse personer. Det er personer, der har brug for at se ledige og travle tider for brugerne i din organisation, men som ikke har brugerkonti til din Microsoft 365 organisation.

Du kan aktivere kalenderdeling for alle brugere i din organisation i Microsoft 365 Administration. Når deling er aktiveret, kan brugerne bruge Outlook Web App til at dele deres kalendere med alle i eller uden for organisationen. Personer i organisationen kan få vist den delte kalender sammen med deres egen kalender. Personer uden for organisationen får tilsendt en URL-adresse, som de kan bruge til at få vist kalenderen. Brugerne i din organisation bestemmer, hvornår de vil dele, og hvor meget de skal dele.

> [!NOTE]
> Hvis du vil dele kalendere med en organisation, der bruger Exchange Server 2013 (en løsning i det lokale miljø), skal den Exchange administrator konfigurere en godkendelsesrelation til cloudmiljøet. Dette er kendt som sammenslutning, og skal opfylde minimum softwarekrav. Se [Deling for at](/exchange/sharing-exchange-2013-help) få flere oplysninger.
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Aktivér kalenderdeling ved hjælp af Microsoft 365 Administration

1. Log på som **global administrator** i Administration, gå til **Indstillinger** \> **Organisationsindstillinger**, og vælg **Kalender** <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">under fanen **Tjenester**</a>.
  
3. På siden **Kalender** skal du vælge, om du vil lade brugerne dele deres kalendere med personer uden for organisationen, som har Microsoft 365 eller Exchange. Vælg, om du vil give anonyme brugere (brugere uden legitimationsoplysninger) adgang til kalendere via en mailinvitation.

4. Vælg, hvilken type kalenderoplysninger brugerne skal have adgang til. Du kan tillade alle oplysninger eller begrænse dem til kun tid eller tid, emne og placering.

## <a name="external-sharing-sync-interval"></a>Synkroniseringsinterval for ekstern deling

Øjeblikkelig synkronisering til deling uden for din lejer understøttes ikke i øjeblikket. Selvom du kan dele i disse konfigurationer, sker synkronisering med jævne mellemrum. Der er to typer deling på tværs af lejere:

1. **Microsoft 365 til en anden Microsoft 365 bruger (hvis ekstern deling er aktiveret)**: Der oprettes en fuldt delt kalender, men synkroniseringen sker ca. hver tredje time. Øjeblikkelig synkronisering aktiveres til sidst for denne konfiguration.

2. **Microsoft 365 til en Outlook.com-bruger**: Hvis ekstern deling er deaktiveret, er deling med en anden Microsoft 365 bruger også omfattet af denne gruppe. Der genereres en URL-adresse til internetforbindelse ved deling, som modtageren kan bruge til at føje til en hvilken som helst kalendertjeneste. Med et ICS-abonnement vælger modtagerens kalendertjeneste, hvornår ICS-abonnementet skal synkroniseres for at modtage nye opdateringer. Hvis modtageren er en Outlook.com eller en Microsoft 365 bruger, sker synkroniseringen ca. hver tredje time.

## <a name="invite-people-to-access-calendars"></a>Inviter personer til at få adgang til kalendere

Når deling er aktiveret, kan kalenderejere udvide invitationer til bestemte brugere.

1. Åbn [Outlook på internettet](https://outlook.office365.com).

2. Øverst på siden skal du vælge appstarteren og vælge **Kalender**. Din primære kalender kaldes som standard "Kalender". Hvis du har oprettet andre kalendere, kan du vælge en af dem, der skal deles i stedet. Du kan ikke dele kalendere, der ejes af andre personer.

3. Angiv navnet eller mailadressen på den person, du vil dele kalenderen med, i feltet **Send en invitation til deling i mail** .

4. Vælg, hvor mange oplysninger personen skal se:

     - **Kan se, når jeg er optaget** , giver personen mulighed for at se, når du er optaget, men indeholder ikke oplysninger som f.eks. placeringen af begivenheden.

     - **Kan få vist titler og placeringer,** som personen kan se, når du er optaget, samt titlen på og placeringen af begivenheder.

     - **Kan få vist alle detaljer** giver personen mulighed for at se alle detaljer om dine begivenheder.

     - **Kan redigere** giver personen mulighed for at se alle detaljer om dine begivenheder og redigere din kalender (kun tilgængelig, når vedkommende deler med personer i din organisation).

5. Vælg **Del**. 

## <a name="related-content"></a>Relateret indhold

[Slå ekstern deling til eller fra for et websted](/sharepoint/change-external-sharing-site) (artikel)\
[Oversigt over Microsoft 365 Administration](../admin-overview/admin-center-overview.md) (video)\
[Administrer mail og kalendere](/admin) (linkside)

