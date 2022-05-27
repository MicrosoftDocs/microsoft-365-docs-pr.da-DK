---
title: Få mere at vide om opbevaring for Teams
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Få mere at vide om opbevaringspolitikker, der gælder for Microsoft Teams.
ms.openlocfilehash: cadff304744fcf06c6717b0709b719e05f8ddfb6
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754328"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>Få mere at vide om opbevaring for Microsoft Teams

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Hvis du får vist en meddelelse i Teams om, at dine chats eller meddelelser er blevet slettet af en opbevaringspolitik, [skal du se Teams meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Oplysningerne på denne side er til it-administratorer, der administrerer disse opbevaringspolitikker.

Oplysningerne i denne artikel supplerer [Få mere at vide om opbevaring](retention.md), fordi den indeholder oplysninger, der er specifikke for Microsoft Teams meddelelser.

For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring for Yammer](retention-policies-yammer.md)
- [Få mere at vide om opbevaring for Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i forbindelse med opbevaring og sletning

> [!NOTE]
> Opbevaringspolitikker understøtter nu [delte kanaler](/MicrosoftTeams/shared-channels), der i øjeblikket er en prøveversion. Alle delte kanaler nedarver opbevaringsindstillinger fra den overordnede kanal.

Teams chatbeskeder, kanalmeddelelser og private kanalmeddelelser kan slettes ved hjælp af opbevaringspolitikker for Teams, og ud over teksten i meddelelserne kan følgende elementer bevares af hensyn til overholdelse af angivne standarder: Integrerede billeder, tabeller, hypertekstlinks, links til andre Teams meddelelser og filer og [kortindhold](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Chatbeskeder og private kanalmeddelelser indeholder alle navnene på personerne i samtalen, og kanalmeddelelser omfatter teamnavnet og meddelelsestitlen (hvis det er angivet). 

Kodestykker, optagne talenotater fra Teams mobilklient, miniaturer, meddelelsesbilleder og reaktioner fra andre i form af humørikoner bevares ikke, når du bruger opbevaringspolitikker til Teams.

Mails og filer, du bruger sammen med Teams, er ikke inkluderet i opbevaringspolitikker for Teams. Disse elementer har deres egne opbevaringspolitikker.

## <a name="how-retention-works-with-microsoft-teams"></a>Sådan fungerer opbevaring sammen med Microsoft Teams

Brug dette afsnit til at forstå, hvordan kravene til overholdelse af angivne standarder opfyldes af backendlager og -processer, og de skal bekræftes af eDiscovery-værktøjer i stedet for af meddelelser, der i øjeblikket er synlige i Teams-appen.

Du kan bruge en opbevaringspolitik til at gemme data fra chats og kanalmeddelelser i Teams og slette disse chats og meddelelser. I baggrunden bruges Exchange postkasser til at gemme data, der er kopieret fra disse meddelelser. Data fra Teams chats gemmes i en skjult mappe i postkassen for hver bruger, der er inkluderet i chatten, og en lignende skjult mappe i en gruppepostkasse bruges til Teams kanalmeddelelser. Disse skjulte mapper er ikke designet til at være direkte tilgængelige for brugere eller administratorer, men i stedet gemme data, som overholdelsesadministratorer kan søge efter med eDiscovery-værktøjer.

Disse postkasser er angivet af attributten RecipientTypeDetails:

- **UserMailbox**: Disse postkasser gemmer meddelelsesdata for skybaserede Teams brugere.
- **MailUser**: Disse postkasser gemmer meddelelsesdata for [brugere i det lokale miljø Teams](search-cloud-based-mailboxes-for-on-premises-users.md).
- **GroupMailbox**: Disse postkasser gemmer meddelelsesdata for Teams standardkanaler.
- **SubstrateGroup**: Disse postkasser gemmer meddelelsesdata for Teams delte kanaler.

Andre postkassetyper, f.eks. RoomMailbox, der bruges til Teams mødelokaler, understøttes ikke for Teams opbevaringspolitikker.

Teams bruger en Azure-drevet chattjeneste som det primære lager for alle meddelelser (chats og kanalmeddelelser). Hvis du har brug for at slette Teams meddelelser af hensyn til overholdelse af angivne standarder, kan opbevaringspolitikker for Teams slette meddelelser efter en angivet periode baseret på, hvornår de blev oprettet. Meddelelser slettes derefter permanent fra både de Exchange postkasser, hvor de er gemt til overholdelse af angivne standarder, og fra det primære lager, der bruges af den underliggende Azure-drevne chattjeneste. Du kan få flere oplysninger om den underliggende arkitektur [under Sikkerhed og overholdelse af angivne standarder i Microsoft Teams](/MicrosoftTeams/security-compliance-overview) og specifikt afsnittet [Information Protection arkitektur](/MicrosoftTeams/security-compliance-overview#information-protection-architecture).

Selvom disse data fra Teams chats og kanalmeddelelser gemmes i postkasser, skal du konfigurere en opbevaringspolitik for **de Teams kanalmeddelelser** og **Teams chatplaceringer**. Teams chats og kanalmeddelelser er ikke inkluderet i opbevaringspolitikker, der er konfigureret for Exchange bruger- eller gruppepostkasser. På samme måde påvirker opbevaringspolitikker for Teams ikke andre mailelementer, der er gemt i postkasser.

Hvis en bruger føjes til en chat, overføres der en kopi af alle meddelelser, der deles med brugeren, til deres postkasse. Den oprettede dato for disse meddelelser ændres ikke for den nye bruger og forbliver den samme for alle brugere.

> [!NOTE]
> Hvis en bruger er inkluderet i en aktiv opbevaringspolitik, der bevarer Teams meddelelser, og du sletter en postkasse for en bruger, der er inkluderet i denne politik, konverteres postkassen til en [inaktiv postkasse](inactive-mailboxes-in-office-365.md) for at bevare de Teams data. Hvis du ikke har brug for at gemme denne Teams data for brugeren, skal du udelade brugerkontoen fra opbevaringspolitikken og [vente på, at ændringen træder i kraft](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect), før du sletter vedkommendes postkasse.

Når en opbevaringspolitik er konfigureret for chat- og kanalmeddelelser, evaluerer et timerjob fra tjenesten Exchange jævnligt elementer i den skjulte postkassemappe, hvor disse Teams meddelelser er gemt. Timerjobbet tager typisk 1-7 dage at køre. Når disse elementer har udløbet deres opbevaringsperiode, flyttes de til mappen SubstrateHolds – en anden skjult mappe, der er i hver bruger- eller gruppepostkasse, hvor de kan gemme "blød slettede" elementer, før de slettes permanent. 

Meddelelser forbliver i mappen SubstrateHolds i mindst 1 dag, og hvis de er berettiget til sletning, sletter timerjobbet dem permanent, næste gang det køres.

> [!IMPORTANT]
> På grund [af det første opbevaringsprincip](retention.md#the-principles-of-retention-or-what-takes-precedence), og da Teams chat- og kanalmeddelelser gemmes i Exchange Online postkasser, afbrydes permanent sletning fra mappen SubstrateHolds altid midlertidigt, hvis postkassen påvirkes af en anden opbevaringspolitik for samme placering, Procesførelseshold, forsinkelse i venteposition, eller hvis der anvendes eDiscovery-venteposition på postkassen af juridiske eller undersøgelsesmæssige årsager.
>
> Selvom postkassen er inkluderet i en relevant venteposition, vil Teams chat- og kanalmeddelelser, der er blevet slettet, ikke længere være synlige i den Teams app, men vil fortsat kunne findes i eDiscovery.

Når en opbevaringspolitik er konfigureret for chat- og kanalmeddelelser, afhænger de stier, som indholdet følger, af, om opbevaringspolitikken skal bevares og derefter slettes, kun bevares eller slettes.

Når opbevaringspolitikken skal bevares og derefter slettes:

![Diagram over opbevaringsflow for Teams chat- og kanalmeddelelser.](../media/teamsretentionlifecycle.png)

For de to stier i diagrammet:

1. **Hvis en chat- eller kanalmeddelelse redigeres eller slettes** af en bruger i løbet af opbevaringsperioden, kopieres den oprindelige meddelelse (hvis den redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds. Meddelelsen gemmes der i mindst 1 dag. Når opbevaringsperioden udløber, slettes meddelelsen permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

2. **Hvis en chat- eller kanalmeddelelse ikke slettes** af en bruger og for aktuelle meddelelser efter redigering, flyttes meddelelsen til mappen SubstrateHolds, når opbevaringsperioden udløber. Denne handling tager typisk mellem 1-7 dage fra udløbsdatoen. Når meddelelsen er i mappen SubstrateHolds, gemmes den der i mindst 1 dag, og derefter slettes meddelelsen permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage). 

> [!NOTE]
> Meddelelser, der er gemt i postkasser, herunder skjulte mapper, kan søges i af eDiscovery-værktøjer. Indtil meddelelser slettes permanent fra mappen SubstrateHolds, kan der stadig søges i dem af eDiscovery-værktøjer.

Når opbevaringsperioden udløber og flytter en meddelelse til mappen SubstrateHolds, kommunikeres der en slettehandling til backend-Azure-chattjenesten, som derefter videresender den samme handling til Teams klientappen. Forsinkelser i denne kommunikation eller cachelagring kan forklare, hvorfor brugerne i en kort periode fortsat kan se disse meddelelser i deres Teams app.

I dette scenarie, hvor Azure-chattjenesten modtager en slettekommando på grund af en opbevaringspolitik, slettes den tilsvarende meddelelse i Teams klientappen for alle brugere i samtalen. Nogle af disse brugere kan være fra en anden organisation, have en opbevaringspolitik med en længere opbevaringsperiode eller ingen opbevaringspolitik tildelt dem. For disse brugere gemmes kopier af meddelelserne stadig i deres postkasser og forbliver søgbare efter eDiscovery, indtil meddelelserne slettes permanent af en anden opbevaringspolitik.

> [!IMPORTANT]
> Meddelelser, der er synlige i Teams-appen, er ikke en nøjagtig afspejling af, om de bevares eller slettes permanent i forbindelse med overholdelseskrav.

Når opbevaringspolitikken er bevar eller kun sletter, er indholdets stier variationer af bevarelse og sletning.

### <a name="content-paths-for-retain-only-retention-policy"></a>Indholdsstier til opbevaringspolitik kun for bevarelse

1. **Hvis en chat- eller kanalmeddelelse redigeres eller slettes** af en bruger i løbet af opbevaringsperioden: Den oprindelige meddelelse kopieres (hvis redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds og opbevares der i mindst 1 dag. Hvis opbevaringspolitikken er konfigureret til at bevare for evigt, forbliver elementet der. Hvis opbevaringspolitikken har en slutdato for opbevaringsperioden, og den udløber, slettes meddelelsen permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

2. **Hvis chat- eller kanalmeddelelsen ikke ændres eller slettes** af en bruger og for aktuelle meddelelser efter redigering i opbevaringsperioden: Der sker intet før og efter opbevaringsperioden. meddelelsen forbliver på den oprindelige placering.

### <a name="content-paths-for-delete-only-retention-policy"></a>Indholdsstier til opbevaringspolitik, der kun gælder for sletning

1. **Hvis chat- eller kanalmeddelelsen redigeres eller slettes** af en bruger i opbevaringsperioden: Den oprindelige meddelelse kopieres (hvis redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds. Meddelelsen opbevares der i mindst 1 dag og slettes permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

2. **Hvis en chat- eller kanalmeddelelse ikke slettes** af en bruger i løbet af opbevaringsperioden: I slutningen af opbevaringsperioden flyttes meddelelsen til mappen SubstrateHolds. Denne handling tager typisk mellem 1-7 dage fra udløbsdatoen. Meddelelsen opbevares der i mindst 1 dag og slettes derefter permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

#### <a name="example-flows-and-timings-for-retention-policies"></a>Eksempel på flow og tidsindstillinger for opbevaringspolitikker

Brug følgende eksempler til at se, hvordan de processer og tidsindstillinger, der er forklaret i de forrige afsnit, gælder for opbevaringspolitikker, der har følgende konfigurationer:

- [Eksempel 1: Bevar kun i 7 år](#example-1-retain-only-for-7-years)
- [Eksempel 2: Bevar i 30 dage, og slet derefter](#example-2-retain-for-30-days-and-then-delete)
- [Eksempel 3: Slet kun efter 1 dag](#example-3-delete-only-after-1-day)

For alle eksempler, der refererer til permanent sletning på grund [af principperne for opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence), afbrydes denne handling midlertidigt, hvis meddelelsen er underlagt en anden opbevaringspolitik for at bevare elementet, eller hvis det er i eDiscovery-venteposition.

##### <a name="example-1-retain-only-for-7-years"></a>Eksempel 1: Bevar kun i 7 år

På dag 1 opretter en bruger en chat- eller kanalmeddelelse.

Den 5. dag redigerer brugeren meddelelsen.

Den 30. dag sletter brugeren den aktuelle meddelelse.

Opbevaringsresultater:

- For den oprindelige meddelelse:
    - På dag 5 kopieres meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst syv år fra dag 1 (opbevaringsperioden).

- For den aktuelle (redigerede) meddelelse:
    - På dag 30 flyttes meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst 7 år fra dag 1 (opbevaringsperioden).

Hvis brugeren havde slettet den aktuelle meddelelse efter den angivne opbevaringsperiode i stedet for inden for opbevaringsperioden, ville meddelelsen stadig blive flyttet til mappen SubstrateHolds. Men nu, hvor opbevaringsperioden er udløbet, slettes meddelelsen permanent efter minimum 1 dag og derefter typisk inden for 1-7 dage.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Eksempel 2: Bevar i 30 dage, og slet derefter

På dag 1 opretter en bruger en chat- eller kanalmeddelelse.

Den 10. dag redigerer brugeren meddelelsen.

Brugeren foretager ikke yderligere ændringer og sletter ikke meddelelsen.

Opbevaringsresultater:

- For den oprindelige meddelelse:
    - Den 10. dag kopieres meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer.
    - I slutningen af opbevaringsperioden (30 dage fra dag 1) slettes meddelelsen permanent inden for 1-7 dage efter minimum 1 dag og returneres derefter ikke med eDiscovery-søgninger.

- For den aktuelle (redigerede) meddelelse:
    - I slutningen af opbevaringsperioden (30 dage fra dag 1) flyttes meddelelsen typisk til mappen SubstrateHolds inden for 1-7 dage, hvor der stadig kan søges i den med eDiscovery-værktøjer.
    - Meddelelsen slettes derefter permanent inden for 1-7 dage efter minimum 1 dag og returneres derefter ikke med eDiscovery-søgninger.

##### <a name="example-3-delete-only-after-1-day"></a>Eksempel 3: Slet kun efter 1 dag

> [!NOTE]
> På grund af den korte varighed på én dag af denne konfiguration og opbevaringsprocesser, der fungerer inden for en tidsperiode på 1-7 dage, viser dette afsnit eksempler på tidsindstillinger, der ligger inden for de typiske tidsintervaller.

På dag 1 opretter en bruger en chat- eller kanalmeddelelse.

Eksempel på resultat af opbevaring, hvis brugeren ikke redigerer eller sletter meddelelsen:

- Dag 5 (typisk 1-7 dage efter starten af opbevaringsperioden på dag 2):
    - Meddelelsen flyttes til mappen SubstrateHolds og forbliver der mindst én dag, hvor der stadig kan søges i den med eDiscovery-værktøjer.

- Dag 9 (typisk 1-7 dage efter mindst 1 dag i mappen SubstrateHolds):
    - Meddelelsen slettes permanent og returneres derefter ikke med eDiscovery-søgninger.

Som dette eksempel viser, gennemgår tjenesten flere processer for at sikre en kompatibel sletning, selvom du kan konfigurere en opbevaringspolitik til at slette meddelelser efter blot én dag. En sletning efter 1 dag kan derfor tage 16 dage, før meddelelsen slettes permanent, så den ikke længere returneres i eDiscovery-søgninger.

## <a name="skype-for-business-and-teams-interop-chats"></a>Skype for Business og Teams interop-chats

Når en Skype for Business chat kommer ind i Teams, bliver den en besked i en Teams chattråd og indtages i den relevante postkasse. Teams opbevaringspolitikker gælder for disse meddelelser fra Teams tråd. 

Men hvis samtaleoversigten er slået til for Skype for Business og fra Skype for Business klientsiden, gemmes oversigten i en postkasse, håndteres disse chatdata ikke af en Teams opbevaringspolitik. Til dette indhold skal du bruge en opbevaringspolitik, der er konfigureret til Skype for Business.

## <a name="meetings-and-external-users"></a>Møder og eksterne brugere

Kanalmødemeddelelser gemmes på samme måde som kanalmeddelelser, så for disse data skal du vælge placeringen **Teams kanalmeddelelser**, når du konfigurerer din opbevaringspolitik.

Impromptu- og planlagte mødemeddelelser gemmes på samme måde som gruppechatbeskeder, så for disse data skal du vælge placeringen **Teams chats**, når du konfigurerer din opbevaringspolitik.

Når eksterne brugere er inkluderet i et møde, som organisationen er vært for:

- Hvis en ekstern bruger tilmelder sig ved hjælp af en gæstekonto i din lejer, gemmes meddelelser fra mødet både i dine brugeres postkasse og i en skyggepostkasse, der er tildelt gæstekontoen. Opbevaringspolitikker understøttes dog ikke for skyggepostkasser, selvom de kan rapporteres som inkluderet i en opbevaringspolitik for hele placeringen (nogle gange kendt som en "politik for hele organisationen").

- Hvis en ekstern bruger tilmelder sig ved hjælp af en konto fra en anden Microsoft 365 organisation, kan dine opbevaringspolitikker ikke slette meddelelser for denne bruger, fordi de er gemt i den pågældende brugers postkasse i en anden lejer. I forbindelse med det samme møde kan dine opbevaringspolitikker slette meddelelser for dine brugere.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen 

Hvis en bruger, der har en postkasse i Exchange Online forlader organisationen, og vedkommendes Microsoft 365 konto slettes, gemmes de chatbeskeder, der er underlagt opbevaring, i en inaktiv postkasse. Chatbeskederne forbliver underlagt en hvilken som helst opbevaringspolitik, der blev placeret på brugeren, før brugerens postkasse blev gjort inaktiv, og indholdet er tilgængeligt for en eDiscovery-søgning. Du kan få flere oplysninger under [Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md). 

Hvis brugeren har gemt filer i Teams, skal du se det [tilsvarende afsnit](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) for SharePoint og OneDrive.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du ikke har arbejdet med at konfigurere opbevaring i Microsoft 365, skal du se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md).

Hvis du er klar til at konfigurere en opbevaringspolitik for Teams, skal du se [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).
