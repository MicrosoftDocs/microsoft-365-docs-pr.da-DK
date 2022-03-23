---
title: Få mere at vide om opbevaring af Yammer
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
description: Få mere at vide om opbevaringspolitikker, der gælder for Yammer.
ms.openlocfilehash: 3759f39a9ef2067d9719d4cf83d73ee7b67ef125
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63591675"
---
# <a name="learn-about-retention-for-yammer"></a>Få mere at vide om opbevaring af Yammer

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Denne funktion er i forhåndsvisning og kan ændres uden ændringer.

Oplysningerne i denne artikel tillæg Få [mere at vide om opbevaring](retention.md), fordi de indeholder oplysninger, der er specifikke for Yammer.

For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring af Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring af Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i opbevaring og sletning

Yammer brugermeddelelser og communitymeddelelser kan slettes ved hjælp af opbevaringspolitikker for Yammer, og ud over teksten i disse meddelelser, kan følgende elementer bevares af hensyn til overholdelse af regler og standarder: Hyperlinks og links til andre Yammer-meddelelser.

> [!NOTE]
> Som beskrevet i det følgende afsnit indeholder brugermeddelelser private meddelelser for en enkelt bruger og alle communitymeddelelser, der er knyttet til den pågældende bruger.

Brugermeddelelser indeholder alle navnene på personerne i samtalen, og communitymeddelelser indeholder communitynavnet og meddelelsestitlen (hvis dette er angivet).

Reaktioner fra andre i form af humørikoner bevares ikke, når du bruger opbevaringspolitikker til Yammer.

Filer, du bruger med Yammer, medtages ikke i opbevaringspolitikker for Yammer. Disse elementer har deres egne opbevaringspolitikker.

## <a name="how-retention-works-with-yammer"></a>Sådan fungerer opbevaring med Yammer

Brug dette afsnit til at forstå, hvordan dine overholdelseskrav opfyldes af backendlagring og -processer, og de skal bekræftes af eDiscovery-værktøjer i stedet for af meddelelser, der aktuelt er synlige i Yammer-appen.

Du kan bruge en opbevaringspolitik til at bevare data fra communitymeddelelser og brugermeddelelser i Yammer og slette disse meddelelser. I baggrunden bruges Exchange postkasser til at gemme data, der kopieres fra disse meddelelser. Data fra Yammer-brugermeddelelser gemmes i en skjult mappe i postkassen for hver bruger, der er inkluderet i brugerens meddelelse, og en lignende skjult mappe i en gruppepostkasse bruges til communitymeddelelser.

Kopier af communitymeddelelser kan også gemmes i den skjulte mappe med brugerpostkasser, når de @omtaler brugere eller underretter brugeren om et svar. Selvom disse meddelelser stammer som en communitymeddelelse, vil en opbevaringspolitik for Yammer ofte indeholde kopier af communitymeddelelser. Derfor er brugermeddelelser ikke begrænset til private meddelelser.

Disse skjulte mapper er ikke designet til at være direkte tilgængelige for brugere eller administratorer, men i stedet gemme data, som overholdelsesadministratorer kan søge med eDiscovery-værktøjer.

> [!IMPORTANT]
> Da kopier af communitymeddelelser også kan gemmes i brugerpostkasser, kan en opbevaringspolitik med en sletningshandling for Yammer-brugermeddelelser medføre, at den oprindelige communitymeddelelse ikke længere er synlig for brugere i Yammer-appen.
> 
> Men en kopi af den oprindelige meddelelse er stadig tilgængelig i den skjulte mappe i community-gruppepostkassen og tilgængelig med eDiscovery-søgninger med henblik på overholdelse af regler og standarder.

Selvom de er gemt i Exchange, er Yammer-meddelelser kun inkluderet i en opbevaringspolitik, der er konfigureret til **Yammer-communitymeddelelser** eller Yammer-brugermeddelelsersplaceringer.

> [!NOTE]
> Hvis en bruger er inkluderet i en aktiv opbevaringspolitik, der bevarer Yammer-data, og du sletter en postkasse for en bruger, som er inkluderet i denne politik, for at bevare Yammer-dataene, konverteres postkassen til en inaktiv [postkasse.](inactive-mailboxes-in-office-365.md) Hvis du ikke har brug for at bevare denne Yammer for brugeren, skal du udelade brugerkontoen fra opbevaringspolitikken, før du sletter brugerens postkasse.

Når en opbevaringspolitik er konfigureret for Yammer-meddelelser, evaluerer et timerjob fra Exchange-tjenesten med jævne mellemrum elementer i den skjulte mappe, hvor disse Yammer meddelelser er gemt. Det tager op til syv dage at køre timerjobbet. Når opbevaringsperioden for disse elementer er udløbet, flyttes de til mappen SubstrateHolds – en skjult mappe, der findes i hver enkelt bruger- eller gruppepostkasse for at gemme "blød-slettede" elementer, før de slettes permanent.

> [!IMPORTANT]
> På grund af [](retention.md#the-principles-of-retention-or-what-takes-precedence) det første princip for opbevaring og siden Yammer-meddelelser gemmes i Exchange Online-postkasser, suspenderes permanent sletning fra mappen SubstrateHolds altid, hvis postkassen påvirkes af en anden opbevaringspolitik (herunder politikker, der er anvendt på Exchange  placering), retslig venteposition, forsinkelse i venteposition, eller hvis en eDiscovery-venteposition anvendes i postkassen af juridiske eller administrative årsager.
>
> Mens postkassen er inkluderet i en relevant venteposition, vil Yammer meddelelser, der er blevet slettet, ikke længere være synlige i Yammer men vil fortsat være synlige med eDiscovery.

Når en opbevaringspolitik er konfigureret for Yammer meddelelser, afhænger de stier, som indholdet tager, af, om opbevaringspolitikken er at bevare og derefter slette, kun at bevare eller slette.

Når opbevaringspolitikken skal bevares og derefter slettes:

![Diagram over opbevaringsflow til Yammer meddelelser.](../media/yammerretentionlifecycle.png)

For de to stier i diagrammet:

1. Hvis **en Yammer** meddelelse redigeres eller slettes af brugeren i opbevaringsperioden, kopieres den oprindelige meddelelse straks (hvis den redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds. Meddelelsen gemmes der, indtil opbevaringsperioden udløber, og derefter slettes meddelelsen med det samme permanent.

2. **Hvis en Yammer** ikke slettes, og for aktuelle meddelelser efter redigering, flyttes meddelelsen til mappen SubstrateHolds, når opbevaringsperioden udløber. Denne handling tager op til syv dage fra udløbsdatoen. Når meddelelsen er i mappen SubstrateHolds, slettes den straks permanent. 

> [!NOTE]
> Meddelelser i mappen SubstrateHolds kan søges i via eDiscovery-værktøjer. Indtil meddelelser er blevet slettet permanent (i mappen SubstrateHolds), forbliver de søgbare via eDiscovery-værktøjer.

Når opbevaringspolitikken kun er opbevarings- eller slet-only, er indholdets stier variationer af behold og slet.

### <a name="content-paths-for-retain-only-retention-policy"></a>Indholdsstier til opbevaringspolitik, der kun kan bevares

1. **Hvis en Yammer** meddelelse redigeres eller slettes: Der oprettes straks en kopi af den oprindelige meddelelse i mappen SubstrateHolds, som bevares, indtil opbevaringsperioden udløber. Derefter slettes meddelelsen straks permanent fra mappen SubstrateHolds.

2. **Hvis den Yammer** meddelelse ikke ændres eller slettes, og for aktuelle meddelelser efter redigering i en opbevaringsperiode: Intet sker før og efter opbevaringsperioden; meddelelsen forbliver på den oprindelige placering.

### <a name="content-paths-for-delete-only-retention-policy"></a>Indholdsstier til opbevaringspolitik kun for slette

1. **Hvis Yammer slettes ikke** under opbevaringsperioden: Ved slutningen af en opbevaringsperiode flyttes meddelelsen til mappen SubstrateHolds. Denne handling tager op til syv dage fra udløbsdatoen. Derefter slettes meddelelsen straks permanent fra mappen SubstrateHolds.

2. **Hvis Yammer** meddelelse slettes af brugeren i perioden, flyttes elementet straks til mappen SubstrateHolds, hvor det straks slettes permanent.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Eksempelflows og tidsindstillinger for opbevaringspolitikker

Brug følgende eksempler til at se, hvordan processer og tidsindstillinger, der er beskrevet i forrige afsnit, gælder for opbevaringspolitikker, der har følgende konfigurationer:

- [Eksempel 1: Behold kun i 7 år](#example-1-retain-only-for-7-years)
- [Eksempel 2: Be behold i 30 dage, og slet derefter](#example-2-retain-for-30-days-and-then-delete)
- [Eksempel 3: Slet kun efter 1 dag](#example-3-delete-only-after-1-day)

For alle eksempler, der refererer til permanent sletning på grund af principperne for [opbevaring,](retention.md#the-principles-of-retention-or-what-takes-precedence) suspenderes denne handling, hvis meddelelsen er underlagt en anden opbevaringspolitik for at bevare elementet, eller det er underlagt en eDiscovery-venteposition.

##### <a name="example-1-retain-only-for-7-years"></a>Eksempel 1: Behold kun i 7 år

På dag 1 slår en bruger en ny meddelelse Yammer meddelelse.

På dag 5 redigerer brugeren meddelelsen.

På dag 30 sletter brugeren den aktuelle meddelelse.

Opbevaringsresultater:

- For den oprindelige meddelelse:
    - På dag 5 kopieres meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst syv år fra dag 1 (opbevaringsperioden).

- For den aktuelle (redigerede) meddelelse:
    - På dag 30 flyttes meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst syv år fra dag 1 (opbevaringsperioden).

Hvis brugeren havde slettet den aktuelle meddelelse efter den angivne opbevaringsperiode, i stedet for inden for opbevaringsperioden, blev meddelelsen stadig flyttet til mappen SubstrateHolds. Men nu hvor en opbevaringsperiode er udløbet, slettes meddelelsen permanent efter minimum 1 dag og derefter typisk inden for 1-7 dage.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Eksempel 2: Be behold i 30 dage, og slet derefter

På dag 1 slår en bruger en ny meddelelse Yammer meddelelse.

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

På dag 1 slår en bruger en ny meddelelse Yammer meddelelse.

Eksempel på et opbevaringsresultat, hvis brugeren ikke redigerer eller sletter meddelelsen:

- Dag 5 (typisk 1-7 dage efter starten af en opbevaringsperiode på dag 2):
    - Meddelelsen flyttes til mappen SubstrateHolds og forbliver der i mindst én dag, hvor der stadig kan søges med eDiscovery-værktøjer.

- Dag 9 (typisk 1-7 dage efter mindst 1 dag i mappen SubstrateHolds):
    - Meddelelsen slettes permanent og returneres derefter ikke med eDiscovery-søgninger.

Som dette eksempel viser, gennemgår tjenesten flere processer for at sikre en kompatibel sletning, selvom du kan konfigurere en opbevaringspolitik til at slette meddelelser efter kun én dag. Derfor kan en sletningshandling efter 1 dag tage 16 dage, før meddelelsen slettes permanent, så den ikke længere returneres i eDiscovery-søgninger.

## <a name="messages-and-external-users"></a>Meddelelser og eksterne brugere

Som standard gælder en opbevaringspolitik for Yammer for alle brugere i organisationen, men ikke for eksterne brugere. Du kan anvende en opbevaringspolitik på eksterne brugere, hvis du bruger **indstillingen** Rediger for inkluderede brugere og angiver deres konto.

På nuværende tidspunkt understøttes Azure B2B-gæstebrugere ikke.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen 

Hvis en bruger forlader organisationen, og brugerens Microsoft 365-konto slettes, gemmes brugerens Yammer, som er underlagt opbevaring, i en inaktiv postkasse. Disse meddelelser forbliver underlagt en opbevaringspolitik, der blev lagt på brugeren, før brugerens postkasse blev gjort inaktiv, og indholdet er tilgængeligt for en eDiscovery-søgning. Du kan finde flere oplysninger [i Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md). 

Hvis brugeren har gemt filer i en Yammer, skal du se [det tilsvarende afsnit](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) for SharePoint og OneDrive.

## <a name="limitations"></a>Begrænsninger

Yammer opbevaringspolitikker er i øjeblikket en prøveversion, og vi arbejder hele tiden på optimering af opbevaringsfunktionalitet. I mellemtiden skal du være opmærksom på følgende begrænsning, når du bruger opbevaring til Yammer communitymeddelelser og brugermeddelelser:

- Når du vælger **Rediger** for placeringen Yammer **brugermeddelelser**, får du muligvis vist gæster og brugere uden postkasse. Opbevaringspolitikker er ikke udviklet til disse brugere, så du skal ikke markere dem.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du er ny bruger af konfiguration af opbevaring i Microsoft 365, skal du se [Introduktion til informationsstyring](get-started-with-information-governance.md).

Hvis du er klar til at konfigurere en opbevaringspolitik for Yammer, skal du [se Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).