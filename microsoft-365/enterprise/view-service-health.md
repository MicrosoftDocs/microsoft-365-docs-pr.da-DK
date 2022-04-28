---
title: Sådan kontrollerer du Microsoft 365 tjenestetilstand
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få vist tilstandsstatus for Microsoft 365 tjenester, før du ringer til support for at se, om der er en aktiv tjenesteafbrydelse.
ms.openlocfilehash: 3155d9a26fd2b34eb4f5bc820e906d35f1f7fdff
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090203"
---
# <a name="how-to-check-microsoft-365-service-health"></a>Sådan kontrollerer du Microsoft 365 tjenestetilstand

[![Mærkat, der giver dig besked om, at Administration ændres, og du kan finde flere oplysninger på aka.ms/aboutM365preview.](../media/O365-Admin-AdminCenterChanging.png)](/office365/admin/microsoft-365-admin-center-preview?preserve-view=true&view=o365-worldwide)

Du kan få vist tilstanden for dine Microsoft-tjenester, herunder Office på internettet, Yammer, Microsoft Dynamics CRM og cloudtjenester til administration af mobilenheder, på siden **Tjenestetilstand** på [siden Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339). Hvis du oplever problemer med en cloudtjeneste, kan du kontrollere tjenestetilstanden for at finde ud af, om dette er et kendt problem med en igangværende løsning, før du ringer til support eller bruger tid på fejlfinding.

Hvis du ikke kan logge på Administration, kan du bruge [tjenestens statusside](https://status.office365.com) til at kontrollere, om der er kendte problemer, der forhindrer dig i at logge på din lejer.  Tilmeld dig også for at følge os på [@MSFT365status](https://twitter.com/MSFT365Status) på Twitter for at se oplysninger om bestemte begivenheder.

## <a name="how-to-check-service-health"></a>Sådan kontrollerer du tjenestetilstanden

1. Gå til Microsoft 365 Administration på [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), og log på med en administratorkonto.

    > [!NOTE]
    > Personer, der er tildelt rollen som global administrator eller administrator af tjenestesupport, kan få vist tjenestetilstand. Hvis administratorer af Exchange, SharePoint og Skype for Business kan få vist tjenestetilstand, skal de også have tildelt rollen Tjenesteadministrator. Du kan få flere oplysninger om roller, der kan få vist tjenestetilstand, under [Om administratorroller](../admin/add-users/about-admin-roles.md?preserve-view=true&view=o365-worldwide#commonly-used-microsoft-365-admin-center-roles).

2. Hvis du vil have vist tjenestetilstand, skal du gå til **Tilstand** >  **Tjenestetilstand** i venstre navigationsrude i Administration eller vælge kortet **Tjenestetilstand** på **dashboardet Hjem**. Dashboardkortet angiver, om der er et aktivt tjenesteproblem, og links til den detaljerede **Tjenestetilstand** side.

3. På siden **Tjenestetilstand** vises tilstanden for hver cloudtjeneste i tabelformat.

   ![Visning af aktuelle problemer i tjenestetilstand.](../media/shd-landing-page.png)

Fanen **Alle tjenester** (standardvisningen) viser alle tjenester, deres aktuelle tilstandstilstand og eventuelle aktive hændelser eller rådgivere. Et ikon og en status i kolonnen **Tilstand** angiver tilstanden for hver tjeneste.

Hvis der er en aktiv hændelse eller rådgivning for en tjeneste, vises de direkte under tjenestenavnet i en indlejret tabel. Du kan skjule den indlejrede tabel for at skjule hændelserne eller rådgiverne i denne visning ved at klikke på vinkelikonet til venstre for tjenestenavnet.

Hvis du vil filtrere visningen, så den kun viser alle de aktive hændelser, skal du vælge fanen **Hændelser** øverst på siden. Hvis du vælger fanen **Advisories** , vises kun alle de aktive rådgivere, der er slået op.

Fanen **Historik** viser alle hændelser og gode råd, der er blevet løst inden for de seneste syv eller 30 dage.

Hvis du oplever et problem med en Microsoft 365 tjeneste, og du ikke kan se den på **siden Tjenestetilstand**, kan du fortælle os om det ved at vælge **Rapportér et problem** og udfylde den korte formular. Vi kigger på relaterede data og rapporter fra andre organisationer for at se, hvor udbredt problemet er, og om det stammer fra vores tjeneste. Hvis den gjorde det, tilføjer vi den som en ny hændelse eller rådgivning på **siden Tjenestetilstand**, hvor du kan spore dens løsning. På siden **Rapporterede problemer** vises alle problemer, som din lejer har rapporteret fra denne formular, og status.

Hvis du vil tilpasse din visning af, hvilke tjenester der vises på dashboardet, skal du vælge **IndstillingerBrugerdefineret** >  visning og fjerne markeringen i afkrydsningsfelterne for de tjenester, du vil filtrere ud fra din Tjenestetilstand dashboardvisning. Sørg for, at afkrydsningsfeltet er markeret for hver tjeneste, du vil overvåge.

Hvis du vil tilmelde dig mailmeddelelser om nye hændelser, der påvirker din lejer og statusændringer for en aktiv hændelse, skal du vælge **IndstillingerMail** > , klikke på **Send mig meddelelser om tjenestetilstand i en mail** og derefter angive:

- Op til to mailadresser.
- Uanset om du vil have meddelelser om hændelser eller gode råd
- De tjenester, du vil have besked om

Du kan også abonnere på mailmeddelelser for individuelle begivenheder i stedet for alle begivenheder for en tjeneste. Det gør du ved at vælge det aktive problem, du vil modtage opdateringer af mailmeddelelser for, vælge **Administrer meddelelser for dette problem** og derefter angive:

- Op til to mailadresser.

> [!NOTE]
> Hver administrator kan have indstillet sine indstillinger, og ovenstående grænse på to mailadresser er pr. administratorkonto.

> [!TIP]
> Du kan også bruge [appen Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=627216) på din mobilenhed til at få vist Tjenestetilstand, hvilket er en god måde at holde dig opdateret med pushmeddelelser på.

### <a name="view-details-of-posted-service-health"></a>Få vist oplysninger om publiceret tjenestetilstand

I visningen **Alle tjenester** skal du vælge problemtitlen for at se siden med oplysninger om problemet, som viser flere oplysninger om problemet, herunder et feed med alle de meddelelser, der er sendt, mens vi arbejder på en løsning.

[![Skærmbillede, der viser tjenestens rådgivning.](../media/service-health-advisory.png)](../media/service-health-advisory.png#lightbox)

Oversigt over rådgivning eller hændelser indeholder følgende oplysninger:

- **Title** – En oversigt over problemet.
- **ID** – Et numerisk id for problemet.
- **Service** – Navnet på den pågældende tjeneste.
- **Sidst opdateret** – Sidste gang meddelelsen om tjenestetilstand blev opdateret.
- **Anslået starttidspunkt** – Det anslåede tidspunkt for, hvornår problemet startede.
- **Status** – Hvordan dette problem påvirker tjenesten.
- **Brugerpåvirkning** – En kort beskrivelse af, hvilken indvirkning dette problem har på slutbrugeren.
- **Alle opdateringer** – Vi sender ofte meddelelser for at fortælle dig, hvordan vi anvender en løsning.

![Et skærmbillede, der viser oplysninger om problemet.](../media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a>Oversæt oplysninger om tjenestetilstand

Vi bruger maskinoversættelse til automatisk at vise meddelelser på dit foretrukne sprog. Læs [Sprogoversættelse for Tjenestetilstand dashboard for](lang-service-health.md) at få flere oplysninger om, hvordan du angiver dit sprog.

### <a name="definitions"></a>Definitioner

For det meste vil tjenester se ud som værende i orden uden yderligere oplysninger. Når en tjeneste har et problem, identificeres problemet som enten en rådgivning eller en hændelse og viser en aktuel status.

> [!TIP]
> Planlagte vedligeholdelseshændelser vises ikke i tjenestetilstand. Du kan spore planlagte vedligeholdelseshændelser ved at holde dig opdateret med **Meddelelsescenter**. Filtrer efter meddelelser, der er kategoriseret som Plan for ændring, for at finde ud af, hvornår ændringen skal ske, dens virkning, og hvordan du forbereder dig på den. Se [Meddelelsescenter i Microsoft 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for at få flere oplysninger.

### <a name="incidents-and-advisories"></a>Hændelser og gode råd

| Ikon | Beskrivelse |
|:-----|:-----|
|![Oplysningsikon for rådgivning.](../media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Hvis en tjeneste har vist en rådgivning, er vi opmærksomme på et problem, der påvirker nogle brugere, men tjenesten er stadig tilgængelig. I en rådgivning er der ofte en løsning på problemet, og problemet kan være forbigående eller har begrænset omfang og brugerpåvirkning.  <br/> |
|![Ikon for udråbstegn for hændelse.](../media/a636db57-6083-44dc-bbd5-556850804f17.png)|Hvis der vises en aktiv hændelse for en tjeneste, er det et kritisk problem, og tjenesten eller en af tjenestens overordnede funktioner er ikke tilgængelige. Det kan f.eks. være, at brugerne ikke kan sende og modtage mail eller ikke kan logge på. Hændelser vil have mærkbar indvirkning på brugerne. Når der er en igangværende hændelse, leverer vi opdateringer vedrørende undersøgelsen, afhjælpningsindsatsen og bekræftelsen af løsningen på Tjenestetilstand dashboard.  <br/> |

### <a name="status-definitions"></a>Statusdefinitioner

| Status | Definition |
|:-----|:-----|
|**Undersøge** | Vi er opmærksomme på et muligt problem og indsamler flere oplysninger om, hvad der sker, og omfanget af indvirkningen. |
|**Tjenesteforringelse** | Vi har bekræftet, at der er et problem, der kan påvirke brugen af en tjeneste eller funktion. Du får muligvis vist denne status, hvis en tjeneste præsterer langsommere end normalt, der er periodiske afbrydelser, eller hvis en funktion f.eks. ikke fungerer. |
|**Tjenesteafbrydelse** | Du får vist denne status, hvis vi fastslår, at et problem påvirker brugernes mulighed for at få adgang til tjenesten. I dette tilfælde er problemet betydeligt og kan genskabes konsekvent. |
|**Gendanner tjenesten** | Årsagen til problemet er blevet identificeret, vi ved, hvilken korrigerende handling der skal udføres, og er i gang med at bringe tjenesten tilbage til en sund tilstand. |
|**Udvidet gendannelse** | Denne status angiver, at den korrigerende handling er i gang med at gendanne tjenesten til de fleste brugere, men det vil tage noget tid at nå alle de berørte systemer. Du kan også se denne status, hvis vi har foretaget en midlertidig rettelse for at reducere indvirkningen, mens vi venter på at anvende en permanent rettelse. |
|**Undersøgelsen er suspenderet** | Hvis vores detaljerede undersøgelse af et muligt problem resulterer i en anmodning om yderligere oplysninger fra kunder, så vi kan undersøge det nærmere, får du vist denne status. Hvis vi har brug for, at du handler, giver vi dig besked om, hvilke data eller logge vi har brug for. |
|**Tjenesten er gendannet** | Vi har bekræftet, at den korrigerende handling har løst det underliggende problem, og at tjenesten er gendannet til en tilstand, der fungerer korrekt. Du kan finde ud af, hvad der gik galt, ved at se oplysningerne om problemet. |
|**Falsk positiv** | Efter en detaljeret undersøgelse har vi bekræftet, at tjenesten er sund og fungerer som designet. Der blev ikke observeret nogen indvirkning på tjenesten, eller årsagen til hændelsen opstod uden for tjenesten. Hændelser og rådgivere med denne status vises i oversigtsvisningen, indtil de udløber (efter den tidsperiode, der er angivet i det sidste indlæg for den pågældende hændelse). |
|**Rapport efter hændelse er publiceret** | Vi har udgivet en rapport efter hændelser for et bestemt problem, der indeholder oplysninger om rodårsag og næste trin for at sikre, at et lignende problem ikke opstår igen. |

### <a name="message-post-types"></a>Meddelelsesposttyper

| Type | Definition |
|:-----|:-----|
|**Hurtig opdatering** | Korte og hyppige trinvise opdateringer for hændelser, der generelt påvirker hændelser, og som er tilgængelige for alle kunder. |
|**Yderligere oplysninger** | Disse yderligere indlæg giver mere detaljerede tekniske oplysninger og løsningsoplysninger, der giver en bedre indsigt i håndteringen af hændelser. Dette er tilgængeligt for lejere, der opfylder de samme krav som beskrevet for [Exchange Online overvågning](/microsoft-365/enterprise/microsoft-365-exchange-monitoring#requirements), |

### <a name="history"></a>Historie

Tjenestetilstand kan du se din aktuelle tilstandsstatus og få vist historikken for eventuelle tjenestemeddelelser og hændelser, der har påvirket din lejer inden for de seneste 30 dage. Hvis du vil have vist den tidligere tilstand for alle tjenester, skal du vælge **Oversigtsvisning** .

Du kan få flere oplysninger om vores forpligtelse til oppetid under [Gennemsigtige handlinger fra Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/service-health-and-continuity).

## <a name="related-topics"></a>Relaterede emner

- [Aktivitetsrapporter i Microsoft 365 Administration](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)
- [Indstillinger for meddelelsescenter](../admin/manage/message-center.md?preserve-view=true&view=o365-worldwide#preferences)
- [Sådan kontrollerer du Windows udgivelsestilstand i Administration](/windows/deployment/update/check-release-health)
