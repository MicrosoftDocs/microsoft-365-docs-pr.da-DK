---
title: Meddelelsescenter
f1.keywords:
- CSH
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
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 38fb3333-bfcc-4340-a37b-deda509c2093
description: Få et overblik over Microsoft 365 Meddelelsescenter og dets rolle i sporing af nye og ændrede funktioner og andre vigtige meddelelser.
ms.openlocfilehash: 687da2d7dec0ea913e629a4cf41740d4b664b346
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437695"
---
# <a name="track-new-and-changed-features-in-the-microsoft-365-message-center"></a>Spor nye og ændrede funktioner i Microsoft 365 Meddelelsescenter

Hvis du vil holde styr på kommende ændringer, herunder nye og ændrede funktioner, planlagt vedligeholdelse eller andre vigtige meddelelser, skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2070717" target="_blank">Meddelelsescenter</a>.
  
Sådan åbner du Meddelelsescenter:

::: moniker range="o365-worldwide"

- I Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2070717" target="_blank">Tilstandsmeddelelsescenter</a>>.

::: moniker-end

::: moniker range="o365-21vianet"

- I <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration</a> skal du gå til **Tilstandsmeddelelsescenter**>.

::: moniker-end

Du kan også bruge [appen Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=627216) på din mobilenhed til at få vist Meddelelsescenter, hvilket er en god måde at holde dig opdateret med pushmeddelelser på.

Hvis du vil ophæve abonnementet på mails i Meddelelsescenter, skal du se [Opsig abonnement på mails i Meddelelsescenter](#unsubscribe-from-message-center-emails) i denne artikel.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

<br>

****

|Spørgsmål|Svar|
|---|---|
|Who kan få vist meddelelser i Meddelelsescenter?|De fleste brugere, der har fået tildelt en hvilken som helst administratorrolle i Microsoft 365, kan få vist meddelelsescenterindlæg. [Her er en liste over](#admin-roles-that-dont-have-access-to-the-message-center) administratorroller, der ikke har adgang til Meddelelsescenter. Du kan også tildele rollen Læser i Meddelelsescenter til brugere, der skal kunne læse og dele meddelelsescenterindlæg uden at have andre administratorrettigheder.|
|Er dette den eneste måde, Hvorpå Microsoft kommunikerer ændringer om Microsoft 365?|Nej, men Meddelelsescenter er den primære måde, hvorpå vi kommunikerer timingen af individuelle ændringer i Microsoft 365. [Se Hold dig opdateret om Microsoft 365 ændringer](stay-on-top-of-updates.md) for at få oplysninger om yderligere ressourcer.|
|Hvordan kan jeg se indlæg på mit sprog?|Meddelelser i meddelelsescenter skrives kun på engelsk, men du kan styre, om indlæg som standard vises på engelsk eller automatisk maskinoversat til dit foretrukne sprog. Du kan også vælge at maskinoversætte indlæg til ethvert sprog, vi understøtter. Se [Sprogoversættelse for meddelelser i Meddelelsescenter](language-translation-for-message-center-posts.md) for at få flere oplysninger.|
|Kan jeg få vist ændringer eller funktioner, før de udrulles til min organisation?|Nogle ændringer og nye funktioner kan vises som prøveversion ved at vælge programmet Målrettet udgivelse. Hvis du vil tilmelde dig, skal du gå til **Indstillinger** >  Ellerg-indstillingerOrganisationsprofilReleaseindstillinger >  > . (I Administration skal du muligvis vælge **Vis alle** nederst i navigationsruden til venstre for at se **Indstillinger**). Du kan vælge Målrettet udgivelse for hele organisationen eller kun for udvalgte brugere. Se [Indstillinger for standardversion eller Målrettet udgivelse i Microsoft 365](release-options-in-office-365.md) for at få flere oplysninger om programmet.|
|Kan jeg finde ud af, præcis den dato en ændring vil være tilgængelig for min organisation?|Vi kan desværre ikke fortælle dig den nøjagtige dato, hvor der foretages en ændring i din organisation. I vores meddelelsescenterindlæg giver vi så mange oplysninger, som vi kan, om timingen af udgivelsen baseret på vores tillidsniveau. Vi arbejder på forbedringer for at blive bedre med dette detaljeniveau.|
|Er disse meddelelser specifikke for min organisation?|Vi gør vores bedste for at sikre, at du kun får vist meddelelser fra Meddelelsescenter, der påvirker din organisation. Køreplanen for Microsoft 365 indeholder alle de funktioner, vi i øjeblikket arbejder på og udruller, men ikke alle disse funktioner gælder for alle organisationer.|
|Kan jeg få meddelelsescenterindlæg sendt via mail i stedet?|Ja! Du kan vælge at få en ugentlig oversigt sendt til dig og op til to andre mailadresser. Den ugentlige oversigt via mail er som standard slået til. Hvis du ikke får dine ugentlige oversigter, skal du kontrollere din spammappe. Se afsnittet [Indstillinger](#preferences) i denne artikel for at få flere oplysninger om, hvordan du konfigurerer den ugentlige oversigt.|
|Hvordan gør jeg stoppe med at hente oversigt over meddelelsescenter?|Gå til Meddelelsescenter i Administration, og vælg **Indstillinger**. Under fanen **Mail** skal du slå indstillingen for **Send mig mailmeddelelser fra Meddelelsescenter fra**.|
|Hvordan kan jeg sikre, at meddelelser om beskyttelse af personlige oplysninger modtages af de rette kontakter i min organisation?|Som global administrator modtager du meddelelser om beskyttelse af personlige oplysninger for din organisation. Du kan også tildele rollen Læser til beskyttelse af personlige oplysninger i Meddelelsescenter til personer, der bør se meddelelser om beskyttelse af personlige oplysninger. Andre administratorroller med adgang til Meddelelsescenter kan ikke få vist meddelelser om beskyttelse af personlige oplysninger.   <br/><br/>Du kan finde flere oplysninger under [Indstillinger](#preferences) i denne artikel.|
|Hvorfor kan jeg ikke se en meddelelse, der tidligere var der?|Hvis du vil administrere antallet af meddelelser i Meddelelsescenter, udløber hver meddelelse og fjernes efter et stykke tid. Generelt udløber meddelelser 30 dage efter den tidsperiode, der er beskrevet i meddelelsens brødtekst.|
|

## <a name="filter-messages"></a>Filtrer meddelelser

Meddelelsescenter præsenterer en visning af alle aktive meddelelser i tabelformat. Som standard vises den nyeste meddelelse øverst på listen. Du kan vælge **Tjeneste** for at få vist meddelelser for forskellige tjenester, f.eks. Microsoft 365 Apps, SharePoint Online osv.   Under **Mærke** kan du vælge **Administratorpåvirkning**, **Beskyttelse af personlige oplysninger**, **Funktionsopdatering**, **Overordnet opdatering**, **Ny funktion**, **Udfasning** eller **Meddelelser om brugerpåvirkning**. Under **Meddelelsestilstand** kan du vælge **Favoritter**, **Ulæst** eller **Opdaterede** meddelelser.

Under fanen Arkiv vises de meddelelser, du har arkiveret. Hvis du vil arkivere en meddelelse, skal du vælge **Arkivér** i meddelelsesruden.

::: moniker range="o365-worldwide"

Brug rullemenuerne **Tjeneste**, **Mærke** og **Meddelelsestilstand**  til at vælge en filtreret visning af meddelelser. I dette diagram mærkes meddelelserne f.eks. med **virkningsmærket Administrator** .

Du kan vælge en hvilken som helst kolonneoverskrift, undtagen **Tjeneste** og **Mærke**, for at sortere meddelelser i stigende eller faldende rækkefølge.

:::image type="content" source="../../media/message-center-admin-impact1.png" alt-text="Visningen Meddelelsescenter sorteret efter administratorpåvirkning.":::

::: moniker-end

::: moniker range="o365-21vianet"

Brug rullemenuerne **Tjeneste**, **Mærke** og **Meddelelsestilstand**  til at vælge en filtreret visning af meddelelser. I dette diagram mærkes meddelelserne f.eks. med **administratorpåvirkningen**.

Du kan vælge en hvilken som helst kolonneoverskrift undtagen **Tjeneste** og **Mærker** for at sortere meddelelser i stigende eller faldende rækkefølge.

::: moniker-end

### <a name="major-updates"></a>Større opdateringer

Større opdateringer kan gennemses ved at vælge **Overordnet opdatering** på rullelisten **Mærker** .

Større opdateringer kommunikeres mindst 30 dage i forvejen, når en handling er påkrævet og kan omfatte:

- Ændringer i den daglige produktivitet, f.eks. indbakke, møder, delegationer, deling og adgang
- Ændringer af temaer, webdele og andre komponenter, der kan påvirke brugerdefinerede funktioner
- Øger eller reducerer synlig kapacitet, f.eks. lager, antal regler, elementer eller varigheder
- Ændringer af produktbranding, der kan:
  - Forårsager forvirring hos slutbrugeren,
  - Resultere i ændringer i helpdesk-processer og referencemateriale, eller
  - Skift en URL-adresse
- En ny tjeneste eller et nyt program
- Ændringer, der kræver en administratorhandling (eksklusive forebyggelse eller løsning af problemer)
- Ændringer af, hvor dine data er gemt
  
### <a name="preferences"></a>Indstillinger

Hvis administration er distribueret på tværs af din organisation, har du muligvis ikke brug for at se indlæg om alle Microsoft 365 tjenester. Hver administrator kan:

- Angiv indstillinger, der styrer, hvilke meddelelser der vises i Meddelelsescenter.
- Filtrer meddelelser
- Angiv mailindstillinger for at modtage en ugentlig oversigt over alle meddelelser, mails kun for større opdateringer og mails for meddelelser om beskyttelse af personlige oplysninger.  

::: moniker range="o365-worldwide"

1. Vælg **Indstillinger** øverst i Meddelelsescenter.

2. Under fanen **Brugerdefineret visning** skal du kontrollere, at afkrydsningsfeltet er markeret for hver tjeneste, du vil overvåge. Fjern markeringen i afkrydsningsfelterne for de tjenester, du vil filtrere ud af visningen Meddelelsescenter.

3. Oversigtsmails er som standard slået til og sendes til din primære mailadresse. Hvis du ikke længere vil modtage den ugentlige oversigt, skal du fjerne markeringen i afkrydsningsfeltet **Send mig mailmeddelelser fra meddelelsescenter** **under fanen Mail**. 

   Du kan også angive op til to mailadresser adskilt af et semikolon.

   Du kan også vælge de mails, du vil have, samt en ugentlig oversigt over de tjenester, du vælger.

4. Vælg **Gem** for at beholde dine ændringer.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. Vælg **Indstillinger** øverst i Meddelelsescenter.

2. Under fanen **Brugerdefineret visning** skal du kontrollere, at afkrydsningsfeltet er markeret for hver tjeneste, du vil overvåge. Fjern markeringen i afkrydsningsfelterne for de tjenester, du vil filtrere ud af visningen Meddelelsescenter.

3. Oversigtsmails er som standard slået til og sendes til din primære mailadresse. Hvis du ikke længere vil modtage den ugentlige oversigt, skal du fjerne markeringen i afkrydsningsfeltet **Send mig mailmeddelelser fra meddelelsescenter** **under fanen Mail**.

   Du kan også angive op til to mailadresser adskilt af et semikolon.

   Du kan også vælge de mails, du vil have, samt en ugentlig oversigt over de tjenester, du vælger.

4. Vælg **Gem** for at beholde dine ændringer.

::: moniker-end

### <a name="display-messages-in-your-preferred-language"></a>Vis meddelelser på dit foretrukne sprog
  
Vi bruger maskinoversættelse til automatisk at vise meddelelser på dit foretrukne sprog. Læs [Sprogoversættelse for Meddelelser i Meddelelsescenter](language-translation-for-message-center-posts.md) for at få flere oplysninger om, hvordan du angiver dit sprog.
  
> [!NOTE]
> Den ugentlige oversigt og eventuelle meddelelser, der sendes via mail, sendes kun på engelsk. Modtagerne kan bruge [Oversætter til Outlook](https://support.microsoft.com/office/3d7e12ed-99d6-406e-a453-b9db0d9653fa) til at læse meddelelsen på deres foretrukne sprog.

## <a name="monthly-active-users"></a>Månedlige aktive brugere

Når du åbner et meddelelsescenterindlæg, fortæller vi dig antallet af brugere, der har brugt den pågældende Microsoft 365 app eller tjeneste, i afsnittet **Tjeneste & månedlige aktive brugere**. Tallene er for de sidste 28 dage. Disse oplysninger kan hjælpe dig med at prioritere, hvilke ændringer du skal arbejde med.

:::image type="content" source="../../media/msgctr-mau-teams.png" alt-text="Skærmbillede: Viser siden med Microsoft Teams chattæthed i meddelelsescenterets indlæg med månedlige aktive brugerdata":::

Antallet af månedlige brugere gælder for alle brugere, der har brugt den pågældende Microsoft 365 app eller tjeneste på en hvilken som helst enhed.

> [!NOTE]
> Denne funktion er endnu ikke tilgængelig for alle Microsoft 365 apps og tjenester. Vi giver dig besked, når funktionen ikke er tilgængelig.

## <a name="choose-columns"></a>Vælg kolonner

Hvis du vil vælge kolonner, skal du vælge **Vælg kolonner** længst til højre på siden **Meddelelsescenter** og vælge dem, du vil have vist, i ruden **Vælg kolonner**.

Her er et hurtigt overblik over de oplysninger, du kan se i hver kolonne.

### <a name="column-information"></a>Kolonneoplysninger

<br>

****

|Kolonne|Beskrivelse|
|---|---|
|Markeret|Hvis du markerer afkrydsningsfeltet i kolonneoverskriftsrækken, markeres alle de meddelelser, der vises i øjeblikket. Hvis du markerer afkrydsningsfeltet ud for en eller flere meddelelser, kan du udføre handlinger på disse meddelelser.|
|Meddelelsestitel|Meddelelsestitler er korte beskrivelser af kommende ændringer. Hvis den fulde titel ikke vises, skal du holde markøren over den, så vises hele titlen i et pop op-felt.|
|Tjeneste|Ikoner angiver det program, som meddelelsen gælder for.|
|Flere indstillinger|Med flere indstillinger kan du afvise en meddelelse, markere den som læst eller ulæst eller dele den med en anden administrator. Hvis du vil gendanne en arkiveret meddelelse, skal du vælge fanen **Arkiv** , markere afkrydsningsfeltet ud for meddelelsen og vælge **Gendan**.|
|Tags| Du kan vælge mærker på rullelisten Mærkat for at filtrere meddelelser. <br> <p> **Beskyttelse af personlige oplysninger**: Meddelelse om beskyttelse af personlige oplysninger (begrænset til globale roller som administrator og læser af meddelelsescenter for beskyttelse af personlige oplysninger). <p> **Større opdatering**: Ændringer er kommunikeret mindst 30 dage i forvejen ([større opdateringer](#major-updates)). <p> **Pensionering**: Udfasning af en tjeneste eller funktion. <p> **Ny funktion**: Ny funktion eller tjeneste. <p> **Funktionsopdatering**: Opdater til en eksisterende funktion. <p> **Administratorvirkning**: Når ændringen tydeligt påvirker administratoren på følgende måder – ændring af brugergrænsefladen, ændring af arbejdsproces, kontrol tilgængelig og specifik/potentiel handling. <p> **Brugerpåvirkning**: Når ændringen af tjenesten tydeligt påvirker brugeren – ændring af brugergrænsefladen og ændring af arbejdsproces. <p> **Opdateret meddelelse**: Når en meddelelse opdateres.|
|Kategori| Dette vises ikke som standard, men kan angives i panelet **Vælg kolonner** . Meddelelser identificeres af en af følgende tre kategorier: <p> **Undgå eller løs problemer**: Informerer dig om kendte problemer, der påvirker din organisation, og kan kræve, at du gør noget for at undgå afbrydelser i tjenesten. Undgå eller løs problemer er anderledes end Tjenestetilstand meddelelser, fordi de beder dig om at være proaktiv for at undgå problemer. <p> **Plan for ændring**: Informerer dig om ændringer af Microsoft 365, der kan kræve, at du handler for at undgå afbrydelser i tjenesten. Vi giver dig f.eks. besked om ændringer af systemkrav eller om funktioner, der fjernes. Vi forsøger at give mindst 30 dages varsel om enhver ændring, der kræver, at en administrator handler for at holde tjenesten kørende normalt. <p> **Hold dig orienteret**: Fortæller dig om nye eller opdaterede funktioner, som vi aktiverer i din organisation. Funktionerne annonceres normalt først i [Microsoft 365 Roadmap](https://go.microsoft.com/fwlink/?linkid=2070821). <p> Kan også fortælle dig om planlagt vedligeholdelse i overensstemmelse med vores serviceniveauaftale. Planlagt vedligeholdelse kan resultere i nedetid, hvor du eller dine brugere ikke kan få adgang til Microsoft 365, en bestemt funktion eller en tjeneste, f.eks. mail eller OneDrive for Business.|
|Opdr. efter|Vi har kun datoer her, hvis vi foretager en ændring, der kræver, at du foretager en handling inden for en bestemt tidsfrist. Da vi sjældent bruger **Act by** column, hvis du ser noget her, skal du være ekstra opmærksom på det.|
|Senest opdateret|Den dato, hvor meddelelsen blev publiceret eller opdateret sidst.|
|Meddelelses-id|Microsoft sporer vores meddelelser i Meddelelsescenter efter meddelelses-id. Du kan henvise til dette id, hvis du vil give feedback, eller hvis du ringer til Support om en bestemt meddelelse.|
|

### <a name="admin-roles-that-dont-have-access-to-the-message-center"></a>Administratorroller, der ikke har adgang til Meddelelsescenter

- Overholdelsesadministrator
- Administrator af betinget adgang
- Godkender af kundelåskasseadgang
- Enhedsadministratorer
- Mappelæsere
- Katalogsynkroniseringskonti
- Mappeforfattere
- Intune tjenesteadministrator
- Privilegeret rolleadministrator
- Rapportlæser

## <a name="give-feedback-on-a-post"></a>Giv feedback på et indlæg

I Meddelelsescenter kan du vælge en meddelelse for at få vist detaljer.

Hvis du vil give feedback på meddelelsen, skal du i detaljeruden vælge enten ikonet **Synes godt om** eller **Synes ikke om** nederst i ruden med meddelelsesoplysninger og angive valgfri feedback i det viste tekstfelt. Angiv ingen personlige oplysninger. Du kan vælge **Det er OK at kontakte mig om denne feedback** og derefter vælge **Send**.

> [!NOTE]
> Hvis du bruger Microsoft 365 til Offentlige myndigheder – GCC, Microsoft 365 til offentlige myndigheder – GCC High og Office 365 Government – DoD, kan du ikke give feedback på et indlæg.

## <a name="share-a-message"></a>Del en meddelelse

Kan du se en meddelelse om, at en anden skal handle på? Du kan dele indholdet af meddelelsen med en hvilken som helst bruger via mail:
  
1. Vælg meddelelsen for at åbne den, og vælg derefter **Del**.
  
2. Hvis du vil dele meddelelsen, skal du angive op til to mailadresser adskilt af et kolon. Du kan sende til mailadresser for enkeltpersoner og grupper. Du kan eventuelt vælge at modtage en kopi af meddelelsen i en mail (meddelelsen går til din primære mailadresse) eller tilføje en personlig meddelelse for at give modtagerne mere kontekst.
  
3. Vælg **Del** for at sende mailen.

## <a name="get-a-link"></a>Hent et link

Har du brug for at følge op med en anden administrator for at sikre, at vedkommende er opmærksom på en ændring og foretager en handling? Du kan generere et link til deling i mail eller chat, som f.eks. vil forbinde brugeren direkte med denne meddelelse. Den person, du deler linket med, skal have adgang til Meddelelsescenter. Se [administratorroller, der ikke har adgang til Meddelelsescenter](message-center.md#admin-roles-that-dont-have-access-to-the-message-center) , for at få flere oplysninger.

1. Vælg meddelelsen for at åbne den.

2. Vælg **Kopiér link**.

3. Brug Ctrl+V, eller højreklik, og vælg **Sæt ind** for at indsætte linket til det ønskede dokument.

## <a name="read-and-unread-states"></a>Læse- og ulæst-tilstande

Alle meddelelser i Meddelelsescenter, der er ulæste, vises med fed skrift. Når du åbner en meddelelse, markeres den som læst. Du kan markere en meddelelse som ulæst.

På hovedsiden i meddelelsescenteret skal du vælge ellipsen **Flere indstillinger** ud for en meddelelse og derefter vælge **Markér som ulæst**.

Du kan også åbne en meddelelse og markere den som ulæst i detaljepanelet.
  
## <a name="archive-and-restore"></a>Arkivér og gendan

Hvis du får vist en meddelelse, der ikke vedrører dig, eller hvis du måske allerede har handlet på den, kan du arkivere meddelelsen for at fjerne den fra Indbakke. Den visning, du kan se i Meddelelsescenter, er specifik for din brugerkonto, så arkivering af den fra visningen påvirker ikke andre administratorer. Der er to måder at arkivere en meddelelse på.

- Vælg en meddelelse på hovedsiden i Meddelelsescenter, og vælg derefter **Arkivér** over listen over meddelelser.
- Åbn meddelelsen, og vælg derefter **Arkiv** øverst i meddelelsesruden.

Har du brug for at få en arkiveret meddelelse tilbage? Intet problem.
  
1. Vælg fanen **Arkiv** øverst i Meddelelsescenter. Der vises en liste over arkiverede meddelelser.

1. Vælg meddelelsen, vælg **Gendan**, hvorefter meddelelsen gendannes til Indbakke.

## <a name="favorite-messages"></a>Foretrukne meddelelser

Hvis du vil markere en meddelelse som en favorit, skal du holde markøren over meddelelsens titel, hvorefter du får vist en **favoritstjerne**:::image type="icon" source="../../media/favorite-star.png" border="false":::, som du kan vælge lige efter ellipsen **Flere indstillinger**. Når du har markeret meddelelser som favoritter, kan du også sortere og filtrere dem.

## <a name="scroll-messages-in-the-message-pane"></a>Rul i meddelelser i meddelelsesruden

Når du åbner en meddelelse i en læserude, kan du bruge pil **op** og **ned** :::image type="icon" source="../../media/updownarrows.png" border="false"::: øverst i ruden til at gå til næste eller den forrige meddelelse på listen.

## <a name="track-your-message-center-tasks-in-planner"></a>Spor dine opgaver i meddelelsescenter i Planner

En masse handlingsbare oplysninger om ændringer i Microsoft 365 tjenester ankommer i Microsoft 365 meddelelsescenter. Det kan være svært at holde styr på, hvilke ændringer der kræver, at der udføres opgaver, hvornår og af hvem, og at spore hver opgave til fuldførelse. Det kan også være en god idé at notere dig noget og mærke det til senere. Du kan gøre alt dette og meget mere, når du synkroniserer dine meddelelser fra Microsoft 365 Administration til Microsoft Planner. Du kan finde flere oplysninger under [Spor dine opgaver i meddelelsescenter i Planner](/office365/planner/track-message-center-tasks-planner).

Du kan få en oversigt over Meddelelsescenter [i Meddelelsescenter i Microsoft 365](message-center.md). Du kan også få mere at vide om, hvordan du angiver dine sprogindstillinger for at aktivere maskinoversættelse for meddelelser i Meddelelsescenter under [Sprogoversættelse for meddelelser i Meddelelsescenter](language-translation-for-message-center-posts.md). Hvis du vil programmere en alternativ måde at få oplysninger om tjenestetilstand i realtid og meddelelsescenterkommunikation på, skal du se [Arbejde med API til tjenestekommunikation i Microsoft Graph](/graph/api/resources/service-communications-api-overview).

## <a name="unsubscribe-from-message-center-emails"></a>Opsig abonnement på mails i Meddelelsescenter

1. Oversigtsmails er som standard slået til og sendes til din primære mailadresse. Hvis du ikke længere vil modtage den ugentlige oversigt, skal du vælge **Indstillinger** og derefter **Mail**.
    - Fjern markeringen i afkrydsningsfeltet **Send en ugentlig oversigt over mine meddelelser** .
    - Mailmeddelelse om større opdateringer er et separat kontrolelement. Hvis du ikke vil modtage meddelelser via mail om større opdateringer, skal du kontrollere, at afkrydsningsfeltet **Send mig mails til større opdateringer** ikke er markeret.
    - Hvis du ikke længere vil modtage mails om meddelelser om beskyttelse af personlige oplysninger, skal du kontrollere, at afkrydsningsfeltet **Send mig mails til meddelelser om beskyttelse af personlige oplysninger** ikke er markeret.  (Meddelelser om beskyttelse af personlige oplysninger er ikke inkluderet i den ugentlige oversigt).

2. Vælg **Gem** for at beholde dine ændringer.

## <a name="related-content"></a>Relateret indhold

[Konfigurer standardindstillingerne eller indstillingerne for målrettet udgivelse](../manage/release-options-in-office-365.md) (artikel)\
[Administrer, hvilke Office funktioner der vises i artiklen Nyheder](../manage/show-hide-new-features.md)
[Virksomhedsabonnementer og faktureringsdokumentation](../../commerce/index.yml) (linkside)
