---
title: Få mere at vide om opbevaring af Teams
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
description: Få mere at vide om opbevaringspolitikker, der gælder Microsoft Teams.
ms.openlocfilehash: f2b3b5a61eabbffc50da34b14baa20e025b8da0f
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568516"
---
# <a name="learn-about-retention-for-microsoft-teams"></a>Få mere at vide om opbevaring af Microsoft Teams

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Hvis du ser en meddelelse i Teams, at dine chats eller meddelelser er blevet slettet af en opbevaringspolitik, skal du Teams [meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).
> 
> Oplysningerne på denne side er til it-administratorer, der administrerer disse opbevaringspolitikker.

Oplysningerne i denne artikel tillæg Få [mere at vide om opbevaring](retention.md), fordi de indeholder oplysninger, der er specifikke for Microsoft Teams meddelelser.

For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring af Yammer](retention-policies-yammer.md)
- [Få mere at vide om opbevaring af Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i opbevaring og sletning

> [!NOTE]
> Opbevaringspolitikker understøtter nu [delte kanaler](/MicrosoftTeams/shared-channels), der i øjeblikket er i forhåndsvisning. Alle delte kanaler arver opbevaringsindstillinger fra den overordnede kanal.

Teams chats, kanalmeddelelser og private kanalmeddelelser kan slettes ved hjælp af opbevaringspolitikker for Teams, og ud over teksten i meddelelserne, kan følgende elementer bevares af hensyn til overholdelse af regler og standarder: Integrerede billeder, tabeller, hypertekstlinks, links til andre Teams-meddelelser og -filer og [kortindhold](/microsoftteams/platform/task-modules-and-cards/what-are-cards). Chatbeskeder og private kanalmeddelelser indeholder alle navnene på personerne i samtalen, og kanalmeddelelser indeholder teamnavnet og meddelelsestitlen (hvis det er angivet). 

Kodestykker, optegnede talenotater fra Teams-mobilklienten, miniaturebilleder, meddelelsesbilleder og reaktioner fra andre i form af humørikoner bevares ikke, når du bruger opbevaringspolitikker til Teams.

Mails og filer, du bruger med Teams, er ikke inkluderet i opbevaringspolitikker for Teams. Disse elementer har deres egne opbevaringspolitikker.

## <a name="how-retention-works-with-microsoft-teams"></a>Sådan fungerer opbevaring med Microsoft Teams

Brug dette afsnit til at forstå, hvordan dine overholdelseskrav opfyldes af backendlagring og -processer, og de skal bekræftes af eDiscovery-værktøjer i stedet for af meddelelser, der aktuelt er synlige i Teams-appen.

Du kan bruge en opbevaringspolitik til at bevare data fra chats og kanalmeddelelser i Teams og slette disse chats og meddelelser. I baggrunden bruges Exchange postkasser til at gemme data, der kopieres fra disse meddelelser. Data fra Teams-chats gemmes i en skjult mappe i postkassen for hver bruger, der er inkluderet i chatten, og en lignende skjult mappe i en gruppepostkasse bruges til Teams kanalmeddelelser. Disse skjulte mapper er ikke designet til at være direkte tilgængelige for brugere eller administratorer, men i stedet gemme data, som overholdelsesadministratorer kan søge med eDiscovery-værktøjer.

Disse postkasser er angivet af deres RecipientTypeDetails-attribut:

- **UserMailbox**: Disse postkasser gemmer meddelelsesdata for skybaserede brugere Teams brugere.
- **MailUser**: Disse postkasser gemmer meddelelsesdata for [lokale Teams brugere](search-cloud-based-mailboxes-for-on-premises-users.md).
- **GroupMailbox**: Disse postkasser gemmer meddelelsesdata for Teams standardkanaler.
- **UnderstrateGroup**: Disse postkasser gemmer meddelelsesdata for Teams delte kanaler.

Andre postkassetyper, f.eks. RoomMailbox, der Teams til mødelokaler, understøttes ikke Teams opbevaringspolitikker.

Teams bruger en Azure-drevet chattjeneste som det primære lager til alle meddelelser (chats og kanalmeddelelser). Hvis du har brug for at slette Teams meddelelser af hensyn til overholdelse af regler og standarder, kan opbevaringspolitikker for Teams slette meddelelser efter en bestemt tidsperiode baseret på, hvornår de blev oprettet. Meddelelser slettes derefter permanent fra både Exchange-postkasser, hvor de lagrede til overholdelseshandlinger, og fra den primære lagerplads, der bruges af den underliggende Azure-baserede chattjeneste. Du kan finde flere oplysninger om den [underliggende](/MicrosoftTeams/security-compliance-overview) arkitektur i Sikkerhed og overholdelse Microsoft Teams og specifikt [afsnittet Information Protection arkitektur](/MicrosoftTeams/security-compliance-overview#information-protection-architecture).

Selvom disse data fra Teams og kanalmeddelelser er gemt i postkasser, skal du konfigurere en opbevaringspolitik for **Teams-kanalmeddelelser** **og Teams chatplaceringer**. Teams chats og kanalmeddelelser er ikke medtaget i opbevaringspolitikker, der er konfigureret til Exchange bruger- eller gruppepostkasser. På samme måde påvirker opbevaringspolitikker Teams ikke andre mailelementer, der er gemt i postkasser.

Hvis en bruger føjes til en chat, indsættes en kopi af alle meddelelser, der deles med dem, i deres postkasse. Den oprettede dato for disse meddelelser ændres ikke for den nye bruger og forbliver den samme for alle brugere.

> [!NOTE]
> Hvis en bruger er inkluderet i en aktiv opbevaringspolitik, der bevarer Teams-meddelelser, og du sletter en postkasse for en bruger, som er inkluderet i denne politik, bliver postkassen konverteret til en inaktiv postkasse for at bevare de Teams data.[](inactive-mailboxes-in-office-365.md) Hvis du ikke har brug for at bevare denne Teams for brugeren, skal du udelade brugerkontoen fra opbevaringspolitikken og vente på, at denne [](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect) ændring træder i kraft, før du sletter brugerens postkasse.

Når en opbevaringspolitik er konfigureret for chat- og kanalmeddelelser, evaluerer et timerjob fra Exchange-tjenesten med jævne mellemrum elementer i den skjulte postkassemappe, hvor disse Teams meddelelser er gemt. Det tager typisk 1-7 dage at køre timerjobbet. Når opbevaringsperioden for disse elementer er udløbet, flyttes de til mappen SubstrateHolds – en anden skjult mappe, der findes i hver enkelt bruger- eller gruppepostkasse for at gemme "blød-slettede" elementer, før de slettes permanent. 

Meddelelser forbliver i mappen SubstrateHolds i mindst én dag, og hvis de er berettiget til sletning, sletter timerjobbet dem permanent, næste gang de køres.

> [!IMPORTANT]
> På grund af [](retention.md#the-principles-of-retention-or-what-takes-precedence) det første princip for opbevaring og siden Teams-chat og kanalmeddelelser gemmes i Exchange Online-postkasser, suspenderes permanent sletning fra mappen SubstrateHolds altid, hvis postkassen påvirkes af en anden opbevaringspolitik (herunder politikker, der er anvendt på Exchange  placering), retslig venteposition, forsinkelse i venteposition, eller hvis en eDiscovery-venteposition anvendes i postkassen af juridiske eller administrative årsager.
>
> Mens postkassen er inkluderet i en relevant venteposition, vil Teams-chat- og kanalmeddelelser, der er blevet slettet, ikke længere være synlige i Teams-appen, men vil fortsat være synlige med eDiscovery.

Når en opbevaringspolitik er konfigureret for chat- og kanalmeddelelser, afhænger de stier, som indholdet tager, af, om opbevaringspolitikken er at bevare og derefter slette, kun at bevare eller slette.

Når opbevaringspolitikken skal bevares og derefter slettes:

![Diagram over opbevaringsflow for Teams chat- og kanalmeddelelser.](../media/teamsretentionlifecycle.png)

For de to stier i diagrammet:

1. Hvis en **chat**- eller kanalmeddelelse redigeres eller slettes af en bruger i opbevaringsperioden, kopieres den oprindelige meddelelse (hvis den redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds. Meddelelsen gemmes der i mindst én dag. Når en opbevaringsperiode udløber, slettes meddelelsen permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

2. **Hvis en chat** - eller kanalmeddelelse ikke slettes af en bruger og for aktuelle meddelelser efter redigering, flyttes meddelelsen til mappen SubstrateHolds, når opbevaringsperioden udløber. Denne handling tager typisk mellem 1-7 dage fra udløbsdatoen. Når meddelelsen er i mappen SubstrateHolds, gemmes den der i mindst 1 dag, og derefter slettes meddelelsen permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage). 

> [!NOTE]
> Meddelelser, der er gemt i postkasser, herunder de skjulte mapper, kan søges i af eDiscovery-værktøjer. Indtil meddelelser slettes permanent fra mappen SubstrateHolds, forbliver de søgbare via eDiscovery-værktøjer.

Når en opbevaringsperiode udløber og flytter en meddelelse til mappen SubstrateHolds, videregives en sletningshandling til Backend Azure-chattjenesten, som derefter videresender den samme handling til Teams-klientappen. Forsinkelser i denne kommunikation eller cachelagring kan forklare, hvorfor brugerne i en kort periode fortsat får vist disse meddelelser i deres Teams-app.

I dette scenarie, hvor Azure-chattjenesten modtager en slettekommando på grund af en opbevaringspolitik, slettes den tilsvarende meddelelse i Teams-klientappen for alle brugere i samtalen. Nogle af disse brugere kan være fra en anden organisation, have en opbevaringspolitik med en længere opbevaringsperiode eller ingen opbevaringspolitik tildelt. For disse brugere gemmes kopier af meddelelserne stadig i deres postkasser og forbliver søgbare efter eDiscovery, indtil meddelelserne slettes permanent af en anden opbevaringspolitik.

> [!IMPORTANT]
> Meddelelser, der er synlige Teams appen, er ikke en nøjagtig afspejling af, om de bevares eller slettes permanent med henblik på overholdelse af krav.

Når opbevaringspolitikken kun er opbevarings- eller slet-only, er indholdets stier variationer af behold og slet.

### <a name="content-paths-for-retain-only-retention-policy"></a>Indholdsstier til opbevaringspolitik, der kun kan bevares

1. Hvis en **chat**- eller kanalmeddelelse redigeres eller slettes af en bruger i opbevaringsperioden: Den oprindelige meddelelse kopieres (hvis den redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds og bevares der i mindst én dag. Hvis opbevaringspolitikken er konfigureret til at bevares uendeligt, forbliver elementet der. Hvis opbevaringspolitikken har en slutdato for opbevaringsperioden, og den udløber, slettes meddelelsen permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

2. **Hvis chat-** eller kanalmeddelelsen ikke ændres eller slettes af en bruger og for aktuelle meddelelser efter redigering i opbevaringsperioden: Intet sker før og efter opbevaringsperioden; meddelelsen forbliver på den oprindelige placering.

### <a name="content-paths-for-delete-only-retention-policy"></a>Indholdsstier til opbevaringspolitik kun for slette

1. Hvis **chat**- eller kanalmeddelelsen redigeres eller slettes af en bruger i opbevaringsperioden: Den oprindelige meddelelse kopieres (hvis den redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds. Meddelelsen bevares der i mindst én dag og slettes permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

2. **Hvis en chat** - eller kanalmeddelelse ikke slettes af en bruger i opbevaringsperioden: Ved opbevaringsperiodens afslutning flyttes meddelelsen til mappen SubstrateHolds. Denne handling tager typisk mellem 1-7 dage fra udløbsdatoen. Meddelelsen bevares der i mindst én dag, og derefter slettes den permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage).

#### <a name="example-flows-and-timings-for-retention-policies"></a>Eksempelflows og tidsindstillinger for opbevaringspolitikker

Brug følgende eksempler til at se, hvordan processer og tidsindstillinger, der er beskrevet i forrige afsnit, gælder for opbevaringspolitikker, der har følgende konfigurationer:

- [Eksempel 1: Behold kun i 7 år](#example-1-retain-only-for-7-years)
- [Eksempel 2: Be behold i 30 dage, og slet derefter](#example-2-retain-for-30-days-and-then-delete)
- [Eksempel 3: Slet kun efter 1 dag](#example-3-delete-only-after-1-day)

For alle eksempler, der refererer til permanent sletning på grund af principperne for [opbevaring,](retention.md#the-principles-of-retention-or-what-takes-precedence) suspenderes denne handling, hvis meddelelsen er underlagt en anden opbevaringspolitik for at bevare elementet, eller det er underlagt en eDiscovery-venteposition.

##### <a name="example-1-retain-only-for-7-years"></a>Eksempel 1: Behold kun i 7 år

På dag 1 opretter en bruger en chat- eller kanalmeddelelse.

På dag 5 redigerer brugeren meddelelsen.

På dag 30 sletter brugeren den aktuelle meddelelse.

Opbevaringsresultater:

- For den oprindelige meddelelse:
    - På dag 5 kopieres meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst syv år fra dag 1 (opbevaringsperioden).

- For den aktuelle (redigerede) meddelelse:
    - På dag 30 flyttes meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst syv år fra dag 1 (opbevaringsperioden).

Hvis brugeren havde slettet den aktuelle meddelelse efter den angivne opbevaringsperiode, i stedet for inden for opbevaringsperioden, blev meddelelsen stadig flyttet til mappen SubstrateHolds. Men nu hvor en opbevaringsperiode er udløbet, slettes meddelelsen permanent efter minimum 1 dag og derefter typisk inden for 1-7 dage.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Eksempel 2: Be behold i 30 dage, og slet derefter

På dag 1 opretter en bruger en chat- eller kanalmeddelelse.

På dag 10 redigerer brugeren den pågældende meddelelse.

Brugeren foretager ikke yderligere ændringer og sletter ikke meddelelsen.

Opbevaringsresultater:

- For den oprindelige meddelelse:
    - På dag 10 kopieres meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer.
    - Ved slutningen af en opbevaringsperiode (30 dage fra dag 1) slettes meddelelsen permanent typisk inden for 1-7 dage efter minimum 1 dag, og derefter returneres den ikke med eDiscovery-søgninger.

- For den aktuelle (redigerede) meddelelse:
    - Ved slutningen af opbevaringsperioden (30 dage fra dag 1) flyttes meddelelsen til mappen SubstrateHolds typisk inden for 1-7 dage, hvor der stadig kan søges i den med eDiscovery-værktøjer.
    - Meddelelsen slettes derefter permanent typisk inden for 1-7 dage efter minimum 1 dag, og derefter returneres den ikke med eDiscovery-søgninger.

##### <a name="example-3-delete-only-after-1-day"></a>Eksempel 3: Slet kun efter 1 dag

> [!NOTE]
> På grund af den korte varighed af en dags varighed af denne konfiguration og opbevaringsprocesser, der fungerer inden for en tidsperiode på 1-7 dage, viser dette afsnit eksempeltidsindstillinger, der er inden for de typiske tidsintervaller.

På dag 1 opretter en bruger en chat- eller kanalmeddelelse.

Eksempel på et opbevaringsresultat, hvis brugeren ikke redigerer eller sletter meddelelsen:

- Dag 5 (typisk 1-7 dage efter starten af en opbevaringsperiode på dag 2):
    - Meddelelsen flyttes til mappen SubstrateHolds og forbliver der i mindst én dag, hvor der stadig kan søges med eDiscovery-værktøjer.

- Dag 9 (typisk 1-7 dage efter mindst 1 dag i mappen SubstrateHolds):
    - Meddelelsen slettes permanent og returneres derefter ikke med eDiscovery-søgninger.

Som dette eksempel viser, gennemgår tjenesten flere processer for at sikre en kompatibel sletning, selvom du kan konfigurere en opbevaringspolitik til at slette meddelelser efter kun én dag. Derfor kan en sletningshandling efter 1 dag tage 16 dage, før meddelelsen slettes permanent, så den ikke længere returneres i eDiscovery-søgninger.

## <a name="skype-for-business-and-teams-interop-chats"></a>Skype for Business og Teams-chatsamtaler

Når en Skype for Business-chat kommer ind i Teams, bliver det til en meddelelse i en Teams-chattråd og bliver inngested i den relevante postkasse. Teams opbevaringspolitikker gælder for disse meddelelser fra Teams tråd. 

Men hvis samtaleoversigten er aktiveret for Skype for Business og fra Skype for Business-klientsiden, at historikken gemmes i en postkasse, så håndteres chatdataene ikke af en Teams-opbevaringspolitik. Til dette indhold skal du bruge en opbevaringspolitik, der er konfigureret til Skype for Business.

## <a name="meetings-and-external-users"></a>Møder og eksterne brugere

Kanalmødemeddelelser gemmes på samme måde som kanalmeddelelser, så for disse data skal du vælge placeringen for **Teams** kanalmeddelelser, når du konfigurerer din opbevaringspolitik.

Improviserede og planlagte mødemeddelelser gemmes på samme måde som gruppechatmeddelelser, så for disse data skal du vælge den placering **Teams chatsamtaler**, når du konfigurerer din opbevaringspolitik.

Når eksterne brugere er inkluderet i et møde, som din organisation hoster:

- Hvis en ekstern bruger slutter sig til ved hjælp af en gæstekonto i din lejer, gemmes alle meddelelser fra mødet i både dine brugeres postkasse og en skyggepostkasse, der er tildelt gæstekontoen. Opbevaringspolitikker understøttes dog ikke for skyggepostkasser, selvom de kan rapporteres som en del af en opbevaringspolitik for hele placeringen (også kaldet en "politik for hele organisationen").

- Hvis en ekstern bruger joinfortræder ved hjælp af en konto fra en anden Microsoft 365-organisation, kan dine opbevaringspolitikker ikke slette meddelelser for denne bruger, fordi de er gemt i den pågældende brugers postkasse i en anden lejer. For det samme møde kan dine opbevaringspolitikker dog slette meddelelser for dine brugere.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen 

Hvis en bruger, der har en postkasse i Exchange Online forlader din organisation, og dennes Microsoft 365-konto slettes, gemmes deres chatmeddelelser, som er underlagt opbevaring, i en inaktiv postkasse. Chatmeddelelserne forbliver underlagt en opbevaringspolitik, der blev lagt på brugeren, før brugerens postkasse blev gjort inaktiv, og indholdet er tilgængelige for en eDiscovery-søgning. Du kan finde flere oplysninger [i Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md). 

Hvis brugeren har gemt filer i en Teams, skal du se [det tilsvarende afsnit](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) for SharePoint og OneDrive.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du er ny bruger af konfiguration af opbevaring i Microsoft 365, skal du se [Introduktion til informationsstyring](get-started-with-information-governance.md).

Hvis du er klar til at konfigurere en opbevaringspolitik for Teams, skal du [se Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).