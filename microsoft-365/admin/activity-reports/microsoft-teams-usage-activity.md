---
title: Microsoft 365 Administration Teams-forbrugsaktivitetsrapporter
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Teams-forbrugsrapporten viser dig, hvordan brugerne kommunikerer og samarbejder i Teams, herunder antallet af aktive brugere, kanaler og meddelelser.
ms.openlocfilehash: 700ceb8396224b27a29d34b9a84eb527a1dce956
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66662825"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-teams-usage-activity"></a>Microsoft 365-rapporter i Administration – Brugsaktivitet i Microsoft Teams

Dashboardet Microsoft 365-rapporter viser dig aktivitetsoversigten på tværs af produkterne i din organisation. Det giver dig mulighed for at få detaljeadgang til individuelle rapporter på produktniveau for at give dig mere detaljeret indsigt i aktiviteterne i hvert produkt. Se [emnet Oversigt over rapporter](activity-reports.md).

Den helt nye **forbrugsrapport for Teams** giver dig et overblik over forbrugsaktiviteten i Teams, herunder antallet af aktive brugere, kanaler og meddelelser, så du hurtigt kan se, hvor mange brugere på tværs af organisationen der bruger Teams til at kommunikere og samarbejde.  Det omfatter også andre Teams-specifikke aktiviteter, f.eks. antallet af aktive gæster, møder og meddelelser.

![Microsoft 365-rapporter – Microsoft Teams-aktivitetsrapport.](../../media/teams-usage.png)

## <a name="how-to-get-to-the-microsoft-teams-usage-activity-report"></a>Sådan kommer du til microsoft Teams-rapporten over forbrugsaktivitet

1. I Administration skal du gå til **Rapporter** og derefter vælge **Forbrug**.
2. Klik på knappen **Vis mere** på **aktivitetskortet i Microsoft Teams** på startsiden for dashboardet.

   ![Microsoft 365-rapporter – Microsoft Teams-aktivitetskort.](../../media/teams-usage-card.png)<br/>

3. På siden **Microsoft Teams-rapporter** skal du vælge fanen **Teams-forbrug** .

## <a name="interpret-the-microsoft-teams-usage-activity-report"></a>Fortolkning af Microsoft Teams-rapporten over forbrugsaktivitet

Du kan få vist brugeraktiviteten i Teams-rapporten ved at vælge fanen **Teams-forbrug** . Her vises følgende diagrammer:

- **Kanalanvendelse**: Sporer antallet af kanalanvendelser efter aktivitetstype over tid.

  ![Rapport over besøgsaktivitet i Teams – kanalforbrug.](../../media/teams-usage-channel.png)

- **Teamforbrug**: Sporer antallet af teams efter type og aktivitet over tid.

  ![Rapport over forbrugsaktivitet i Teams – teamforbrug.](../../media/teams-usage-usage.png)

Diagrammet indeholder desuden forbrugsoplysninger for individuelle teams, f.eks. sidste aktivitetsdato, aktive brugere, aktive kanaler og andre data.

![Microsoft 365-rapporter – Microsoft Teams-forbrugsaktivitetstabel.](../../media/teams-usage-table.png)

I tabellen skal du vælge **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.

![Rapport over forbrugsaktivitet i Teams – vælg kolonner.](../../media/teams-usage-columns.png)

Du kan også eksportere rapportdataene til en Excel-.csv-fil ved at vælge linket **Eksportér** . Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse.  Det eksporterede format for **lydtid**, **videotid** og **skærmdelingstid** følger ISO8601-varighedsformatet.

**Microsoft Teams-forbrugsaktivitetsrapporten** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).

For at sikre datakvaliteten udfører vi daglige datavalideringskontroller i de seneste tre dage og udfylder eventuelle huller, der er registreret. Du kan bemærke forskelle i historiske data under processen.

> [!Important]
> Data for en given dag vises inden for 48 timer. Data for 10. januar skal f.eks. vises i rapporten senest den 12. januar.

### <a name="channel-usage-metrics"></a>Forbrugsdata for kanal

Diagrammet Kanalforbrug viser data om følgende målepunkter.

|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Aktive kanalbrugere|Dette er det samlede antal interne aktive brugere, aktive gæster og eksterne aktive brugere.  <br/><br/> **Interne aktive brugere** – brugere, der har mindst én panelhandling i den angivne tidsperiode. Dette udelukker gæster.   <br/> **Aktive gæster** – Gæster, der har mindst én panelhandling i den angivne tidsperiode. En gæst er en person uden for din organisation, der tilgår delte ressourcer ved at logge på en gæstekonto i min mappe.  <br/> **Ekstern aktiv bruger** – Eksterne deltagere, der har mindst én panelhandling i den angivne tidsperiode. En ekstern deltager er en person uden for din organisation, der deltager i en ressource – f.eks. en delt kanal – ved hjælp af deres egen identitet og ikke en gæstekonto i din mappe.|
|Aktive kanaler|Gyldige kanaler i aktive teams, der har mindst én aktiv bruger i den angivne tidsperiode. Dette omfatter offentlige, private eller delte kanaler.|
|Kanalmeddelelser|Antallet af entydige meddelelser, som brugeren har sendt i en privat chat i den angivne tidsperiode.|

### <a name="team-usage-metrics"></a>Forbrugsdata for team

I teams-forbrugsdiagrammet vises data om følgende målepunkter.

|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Private teams|Et privat team, der enten er aktivt eller inaktivt.|
|Offentlige teams|Et offentligt team, der enten er aktivt eller inaktivt.|
|Aktive private teams|Et team, der er privat og aktivt.|
|Aktive offentlige teams|Et team, der er offentligt og aktivt.|

### <a name="teams-details"></a>Teams-oplysninger

Data til følgende målepunkter er tilgængelige for individuelle teams.

|Element|Beskrivelse|
|:-----|:-----|
|**Metriske**|**Definition**|
|Team-id|Team-id|
|Interne aktive brugere|Brugere, der har mindst én panelhandling i den angivne tidsperiode, herunder gæster. <br/> <br/> Interne brugere og gæster, der er placeret i den samme lejer. Interne brugere udelukker gæster.|
|Aktive gæster|Gæster, der har mindst én panelhandling i den angivne tidsperiode. <br/> <br/> En gæst defineres som personer uden for din organisation, der tilgår delte ressourcer ved at logge på en gæstekonto i min mappe.|
|Eksterne aktive brugere|Eksterne deltagere, der har mindst én panelhandling i den angivne tidsperiode.<br/><br/> En ekstern deltager defineres som en person uden for din organisation, der deltager i en ressource – f.eks. en delt kanal – ved hjælp af deres egen identitet og ikke en gæstekonto i din mappe.|
|Aktive kanaler|Gyldige kanaler i aktive teams, der har mindst én aktiv bruger i den angivne tidsperiode. Dette omfatter offentlige, private eller delte kanaler.|
|Aktive delte kanaler|Gyldige delte kanaler i aktive teams, der har mindst én aktiv bruger på det angivne tidspunkt. <br/> <br/>En delt kanal defineres som en Teams-kanal, der kan deles med personer uden for teamet. Disse personer kan være i din organisation eller fra andre Azure AD organisationer.|
|Samlede organiserede møder|Summen af engangs planlagte, tilbagevendende, ad hoc- og ikke-klassificerede møder, som en bruger har organiseret i den angivne tidsperiode.|
|Indlæg|Antallet af alle indlægsmeddelelser i kanaler i den angivne tidsperiode.|
|Svar|Antallet af alle svarmeddelelser i kanaler i den angivne tidsperiode.|
|Nævner|Antallet af alle omtaler, der er foretaget i den angivne tidsperiode.|
|Reaktioner|Antal reaktioner, som en aktiv bruger har foretaget i den angivne tidsperiode.|
|Vigtige meddelelser|Antallet af presserende meddelelser i den angivne tidsperiode.|
|Kanalmeddelelser|Antallet af entydige meddelelser, som brugeren har sendt i en teamchat i den angivne tidsperiode.|
|Seneste aktivitetsdato|Den seneste dato, hvor et medlem af teamet har bekræftet en handling.|

## <a name="make-the-user-specific-data-anonymous"></a>Gør de brugerspecifikke data anonyme

Hvis du vil gøre dataene i Teams-brugeraktivitetsrapporten anonyme, skal du være global administrator. Dette skjuler identificerbare oplysninger (ved hjælp af MD5-hashen), f.eks. vist navn, mail og Azure Active Directory-objekt-id i rapporten og deres eksport.

1. I Microsoft 365 Administration skal du gå til **Indstillinger** > **Organisationsindstillinger** og vælge **Rapporter** under fanen **Tjenester**.

2. Vælg **Rapporter**, og vælg derefter Vis **anonyme id'er**. Denne indstilling anvendes både på forbrugsrapporterne i Microsoft 365 Administration og Teams Administration.

3. Vælg **Gem ændringer**.

## <a name="see-also"></a>Se også

[Rapport over enhedsforbrug i Microsoft Teams](../activity-reports/microsoft-teams-device-usage-preview.md)

[Microsoft Teams-brugeraktivitetsrapport](../activity-reports/microsoft-teams-user-activity-preview.md)
