---
title: Sådan kontrolleres Microsoft 365 tjeneste sundhed
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Få vist status for tjenestetilstanden for Microsoft 365 du ringer til support for at se, om der er en aktiv afbrydelse af tjenesten.
ms.openlocfilehash: 4a72132872c890f755cb537e06c42412aa17fb9f
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/14/2022
ms.locfileid: "63601617"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Sådan kontrolleres Microsoft 365 tjeneste sundhed

[![Navn, der giver dig besked om, at Administration ændres, og du kan finde flere oplysninger aka.ms/aboutM365preview.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

Du kan få vist tilstand for din Microsoft-tjenester, herunder Office på internettet, Yammer, Microsoft Dynamics CRM og skytjenester for administration af mobilenheder, på siden Tjeneste sundhed i  [ Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339). Hvis du oplever problemer med en skytjeneste, kan du kontrollere tjenestestilstanden for at afgøre, om dette er et kendt problem, og om der er en løsning i gang, før du ringer til support eller bruger tid på fejlfinding.

Hvis du ikke kan logge på Administration, kan du bruge siden [Tjenestestatus](https://status.office365.com) til at kontrollere, om der er kendte problemer, der forhindrer dig i at logge på din lejer.  Tilmeld dig også for at følge os [@MSFT365status](https://twitter.com/MSFT365Status) Twitter for at se oplysninger om bestemte begivenheder.

## <a name="how-to-check-service-health"></a>Sådan kontrollerer du tjenestestilstanden

1. Gå til Microsoft 365 Administration på [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), og log på med en administratorkonto.

    > [!NOTE]
    > Personer, der er tildelt rollen som global administrator eller tjenestesupportadministrator, kan få vist tjenestestilstanden. Hvis du Exchange tjenesteadministratorer SharePoint administratorer og Skype for Business til at få vist tjenestestilstanden, skal de også have tildelt rollen som tjenesteadministrator. Du kan finde flere oplysninger om roller, der kan få vist tjeneste sundhed, [under Om administratorroller](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. Hvis du vil have vist tjenestetilstanden, skal du gå til **HealthService** >  **Health** i navigationsruden til venstre i Administration eller vælge kortet **Tjenestetilstand** på **dashboardet i Startsiden**. Dashboardkortet angiver, om der er et aktivt problem med tjenesten og links til den detaljerede **tjenestetilstandsside** .

3. På siden **Tjenestetilstand** vises tilstanden for hver skytjeneste i et tabelformat.

   ![Visning af de aktuelle problemer i tjenestestilstand.](../media/shd-landing-page.png)

Fanen **Alle** tjenester (standardvisningen) viser alle tjenester, deres aktuelle tilstand og alle aktive hændelser eller rådgiver. Et ikon og status i **kolonnen** Tilstand angiver tilstanden for hver tjeneste.

Hvis der er en aktiv hændelse eller vejledning for en tjeneste, vil de blive vist direkte under tjenestenavnet i en indlejret tabel. Du kan skjule den indlejrede tabel for at skjule hændelserne eller rådgiverne i denne visning ved at klikke på vinkelikonet til venstre for tjenestenavnet.

Hvis du vil filtrere din visning til kun at vise alle de aktive hændelser, **skal du vælge** fanen Hændelser øverst på siden. Når du vælger **fanen Rådgiver** , vises kun alle de aktive rådgivere, der er slået op.

Fanen **Oversigt** viser alle hændelser og råd, der er blevet løst inden for de seneste syv eller 30 dage.

Hvis du oplever et problem med en  Microsoft 365-tjeneste **, og** du ikke kan se den på siden Tjenestestilstand, kan du fortælle os om det ved at vælge Rapportér et problem og udfylde den korte formular. Vi ser på relaterede data og rapporter fra andre organisationer for at se, hvor omfattende problemet er, og om det stammer fra vores tjeneste. Hvis den gjorde, tilføjer vi den som en ny hændelse eller vejledning på siden **Tjenestestilstand** , hvor du kan spore løsningen. På **siden Rapporterede** problemer vises alle de problemer, som din lejer har rapporteret fra denne formular, samt status.

Hvis du vil tilpasse visningen af de tjenester, der vises på dashboardet,  >  skal du vælge IndstillingerTilpasset visning og fjerne markeringen i afkrydsningsfelterne for de **tjenester, du** vil filtrere ud af dashboardvisningen Tjenestetilstand. Sørg for, at afkrydsningsfeltet er markeret for hver tjeneste, du vil overvåge.

Hvis du vil tilmelde dig mailbeskeder om nye hændelser, der påvirker din lejer, og statusændringer for en aktiv hændelse, skal du vælge **PreferencesEmail** > , klikke på Send mig service **heath notifications in email** og derefter angive:

- Op til to mailadresser.
- Uanset om du ønsker meddelelser om hændelser eller rådgivning
- De tjenester, du vil have besked om

Du kan også abonnere på mailbeskeder for individuelle begivenheder i stedet for hver enkelt begivenhed for en tjeneste. Det gør du ved at vælge det aktive problem, hvor du vil modtage opdateringer til mailmeddelelser, vælge **Administrer meddelelser for** dette problem og derefter angive:

- Op til to mailadresser.

> [!NOTE]
> Hver administrator kan angive deres Indstillinger, og den ovenstående grænse på to mailadresser er pr. administratorkonto.

> [!TIP]
> Du kan også bruge Microsoft 365 Administration [på](https://go.microsoft.com/fwlink/p/?linkid=627216) din mobilenhed til at få vist Tjeneste sundhed, hvilket er en god måde at holde dig opdateret med pushmeddelelser.

### <a name="view-details-of-posted-service-health"></a>Få vist detaljer om tjeneste sundhed opslået

I **visningen Alle** tjenester skal du vælge problemets titel for at få vist problemets detaljeside, som viser flere oplysninger om problemet, herunder et feed med alle de meddelelser, der er slået op, mens vi arbejder på en løsning.

[![Skærmbillede, der viser rådgivning om tjenesten.](../media/service-health-advisory.png)](../media/service-health-advisory.png#lightbox)

Oversigten over rådgivning eller hændelser indeholder følgende oplysninger:

- **Titel** – En oversigt over problemet.
- **Id** – En numerisk identifikator for problemet.
- **Tjeneste** – Navnet på den pågældende tjeneste.
- **Senest opdateret** – Sidste gang, tilstandsmeddelelsen om tjeneste blev opdateret.
- **Anslået starttid** – det anslåede tidspunkt, hvor problemet startede.
- **Status** – Sådan påvirker dette problem tjenesten.
- **Brugerpåvirkning** – En kort beskrivelse af den påvirkning, dette problem har på slutbrugeren.
- **Alle opdateringer** – Vi sender hyppige meddelelser for at fortælle dig, hvor langt vi er i løsningsprocessen.

![Et skærmbillede, der viser oplysninger om problemet.](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Oversæt oplysninger om tjenesteydelsestilstand

Vi bruger maskinoversættelse til automatisk at vise meddelelser på dit foretrukne sprog. Læs [Oversættelse af sprog for dashboardet Tjenestetilstand](lang-service-health.md) for at få mere at vide om, hvordan du angiver dit sprog.

### <a name="definitions"></a>Definitioner

Det meste af tiden vises tjenester uden sundhed uden yderligere oplysninger. Når en tjeneste har et problem, identificeres problemet som enten en vejledning eller en hændelse og viser en aktuel status.

> [!TIP]
> Planlagte vedligeholdelseshændelser vises ikke i tjenestestilstand. Du kan holde styr på planlagte vedligeholdelseshændelser ved at holde dig opdateret **i Meddelelsescenter**. Filtrer meddelelser, der er kategoriseret som Plan for ændring, for at finde ud af, hvornår ændringen finder sted, hvad den betyder, og hvordan du forbereder dig på den. Se [Meddelelsescenter i Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for at få mere at vide.

### <a name="incidents-and-advisories"></a>Hændelser og rådgivning

| Ikon | Beskrivelse |
|:-----|:-----|
|![Oplysningsikon for rådgivning.](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Hvis en tjeneste viser en vejledning, er vi klar over, at et problem påvirker nogle brugere, men tjenesten er stadig tilgængelig. En vejledning giver ofte en løsning på problemet, og problemet kan forekomme periodisk eller i begrænset omfang og have en begrænset brugerpåvirkning.  <br/> |
|![Udråbstegnsikon for hændelse.](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|Hvis en tjeneste viser en aktiv hændelse, er det et kritisk problem, og tjenesten eller en vigtig funktion af tjenesten er ikke tilgængelig. Brugere kan f.eks. være ude af stand til at sende og modtage mails eller ikke kunne logge på. Hændelser vil have væsentlig indvirkning på brugerne. Når der er en hændelse i gang, leverer vi opdateringer vedrørende undersøgelsen, afhjælpningsindsatsen og bekræftelsen af løsningen på dashboardet for tjenestetilstand.  <br/> |

### <a name="status-definitions"></a>Statusdefinitioner

| Status | Definition |
|:-----|:-----|
|**Undersøger** | Vi er opmærksomme på et potentielt problem og er i gang med at indsamle flere oplysninger om, hvad der foregår, og omfanget af indvirkning. |
|**Tjenesten er forringet** | Vi har bekræftet, at der er et problem, der kan påvirke brugen af en tjeneste eller funktion. Du får muligvis vist denne status, hvis en tjeneste udfører langsommere end normalt, der opstår midlertidige afbrydelser, eller hvis en funktion f.eks. ikke virker. |
|**Afbrydelse af tjenesten** | Du får vist denne status, hvis vi finder ud af, at et problem påvirker brugernes mulighed for at få adgang til tjenesten. I dette tilfælde er problemet væsentligt og kan genskabes konsekvent. |
|**Tjenesten gendannes** | Årsagen til problemet er identificeret. Vi ved, hvad der skal afhjælpes, og vi er i gang med at føre tjenesten tilbage til en sund tilstand. |
|**Udvidet gendannelse** | Denne status angiver, at der er taget skridt til at gendanne tjenesten for de fleste brugere, men at det vil tage noget tid at gendanne alle de påvirkede systemer. Du kan også få vist denne status, hvis vi har lavet en midlertidig rettelse for at reducere effekten, mens vi venter med at anvende en permanent rettelse. |
|**Afbrudt undersøgelse** | Hvis vores detaljerede undersøgelse af et potentielt problem resulterer i en anmodning om yderligere oplysninger fra kunder med henblik på yderligere undersøgelse, får du vist denne status. Hvis vi har brug for, at du handler, giver vi dig besked om, hvilke data eller logfiler vi har brug for. |
|**Tjenesten er gendannet** | Vi har bekræftet, at afhjælpende tiltag har løst det underliggende problem, og at tjenesten er blevet gendannet til den rette tilstand. Se problemets detaljer for at finde ud af, hvad der gik galt. |
|**Falsk positiv** | Efter en detaljeret undersøgelse har vi bekræftet, at tjenesten er sund og fungerer som designet. Der blev ikke observeret nogen indvirkning på tjenesten, eller årsagen til hændelsen opstod uden for tjenesten. Hændelser og rådgiver med denne status vises i oversigtsvisningen, indtil de udløber (efter den tidsperiode, der er angivet i det sidste indlæg for den pågældende begivenhed). |
|**Rapport publiceret efter hændelsen** | Vi har udgivet en rapport efter hændelse for et bestemt problem, der omfatter oplysninger om den egentlige årsag, og næste trin for at sikre, at et lignende problem ikke gentages. |

### <a name="message-post-types"></a>Typer af meddelelsesopslag

| Type | Definition |
|:-----|:-----|
|**Hurtig opdatering** | Korte og hyppige trinvise opdateringer til bredt påvirkende hændelser, der er tilgængelige for alle kunder. |
|**Yderligere oplysninger** | Disse yderligere indlæg giver mere detaljerede tekniske oplysninger og løsninger, så du kan få et dybere indblik i håndteringen af hændelser. Dette er tilgængeligt for lejere, der opfylder de samme krav, som er [beskrevet Exchange Online overvågning](/microsoft-365/enterprise/microsoft-365-exchange-monitoring#requirements), |

### <a name="history"></a>Historik

Tjenestetilstand giver dig mulighed for at se din aktuelle tilstandsstatus og få vist historikken for alle tjenesterådgivere og hændelser, der har påvirket din lejer i de seneste 30 dage. Hvis du vil have vist tidligere tilstand for alle tjenester, skal du vælge **Historikvisning** .

Du kan finde flere oplysninger om vores forpligtelse om oppetid [under Gennemsigtige handlinger fra Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity).

## <a name="related-topics"></a>Relaterede emner

- [Aktivitetsrapporter i Microsoft 365 Administration](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
- [Indstillinger i Meddelelsescenter](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)
- [Sådan kontrolleres Windows tilstand for udgivelse i Administration](/windows/deployment/update/check-release-health)
