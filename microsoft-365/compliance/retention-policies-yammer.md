---
title: Få mere at vide om opbevaring for Yammer
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
ms.openlocfilehash: c479b7b08fd74b957a8ef7d23147758948459dc8
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754306"
---
# <a name="learn-about-retention-for-yammer"></a>Få mere at vide om opbevaring for Yammer

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Oplysningerne i denne artikel supplerer [Få mere at vide om opbevaring](retention.md), fordi den indeholder oplysninger, der er specifikke for Yammer.

For andre arbejdsbelastninger skal du se:

- [Få mere at vide om opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring for Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring for Exchange](retention-policies-exchange.md)

## <a name="whats-included-for-retention-and-deletion"></a>Hvad er inkluderet i forbindelse med opbevaring og sletning

Yammer brugermeddelelser og communitymeddelelser kan slettes ved hjælp af opbevaringspolitikker for Yammer, og ud over teksten i disse meddelelser kan følgende elementer bevares af hensyn til overholdelse af angivne standarder: Hypertekstlinks og links til andre Yammer meddelelser.

> [!NOTE]
> Som forklaret i følgende afsnit omfatter brugermeddelelser private meddelelser for en enkelt bruger og alle communitymeddelelser, der er knyttet til den pågældende bruger.

Brugermeddelelser omfatter alle navnene på personerne i samtalen, og communitymeddelelser omfatter communitynavnet og meddelelsestitlen (hvis det er angivet).

Reaktioner fra andre i form af humørikoner bevares ikke, når du bruger opbevaringspolitikker til Yammer.

Filer, du bruger sammen med Yammer, er ikke inkluderet i opbevaringspolitikker for Yammer. Disse elementer har deres egne opbevaringspolitikker.

## <a name="how-retention-works-with-yammer"></a>Sådan fungerer opbevaring sammen med Yammer

Brug dette afsnit til at forstå, hvordan kravene til overholdelse af angivne standarder opfyldes af backendlager og -processer, og de skal bekræftes af eDiscovery-værktøjer i stedet for af meddelelser, der i øjeblikket er synlige i Yammer-appen.

Du kan bruge en opbevaringspolitik til at gemme data fra communitymeddelelser og brugermeddelelser i Yammer og slette disse meddelelser. I baggrunden bruges Exchange postkasser til at gemme data, der er kopieret fra disse meddelelser. Data fra Yammer brugermeddelelser gemmes i en skjult mappe i postkassen for hver bruger, der er inkluderet i brugermeddelelsen, og en lignende skjult mappe i en gruppepostkasse bruges til communitymeddelelser.

Kopier af communitymeddelelser kan også gemmes i den skjulte mappe med brugerpostkasser, når de @nævner brugere eller giver brugeren besked om et svar. Selvom disse meddelelser stammer fra en communitymeddelelse, vil en opbevaringspolitik for Yammer brugermeddelelser ofte indeholde kopier af communitymeddelelser. Det betyder, at brugermeddelelser ikke er begrænset til private meddelelser.

Disse skjulte mapper er ikke designet til at være direkte tilgængelige for brugere eller administratorer, men i stedet gemme data, som overholdelsesadministratorer kan søge efter med eDiscovery-værktøjer.

Selvom de gemmes i Exchange, medtages Yammer meddelelser kun i en opbevaringspolitik, der er konfigureret for **de Yammer communitymeddelelser** eller Yammer placeringer af **brugermeddelelser**.

> [!NOTE]
> Hvis en bruger er inkluderet i en aktiv opbevaringspolitik, der bevarer Yammer data, og du sletter en postkasse for en bruger, der er inkluderet i denne politik, for at bevare de Yammer data, konverteres postkassen til en [inaktiv postkasse](inactive-mailboxes-in-office-365.md). Hvis du ikke har brug for at gemme denne Yammer data for brugeren, skal du udelade brugerkontoen fra opbevaringspolitikken, før du sletter brugerens postkasse.

Når en opbevaringspolitik er konfigureret for Yammer meddelelser, evaluerer et timerjob fra tjenesten Exchange jævnligt elementer i den skjulte mappe, hvor disse Yammer meddelelser gemmes. Det tager op til syv dage at køre timerjobbet. Når disse elementer har udløbet deres opbevaringsperiode, flyttes de til mappen SubstrateHolds – en skjult mappe, der er i alle bruger- eller gruppepostkasser, hvor de kan gemme "blød slettede" elementer, før de slettes permanent.

> [!IMPORTANT]
> På grund [af det første princip om opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence), og da Yammer meddelelser er gemt i Exchange Online postkasser, afbrydes permanent sletning fra mappen SubstrateHolds altid midlertidigt, hvis postkassen påvirkes af en anden opbevaringspolitik for samme placering, procesførelseshold, forsinkelse i venteposition, eller hvis der anvendes eDiscovery-venteposition på postkassen af juridiske eller undersøgelsesmæssige årsager.
>
> Selvom postkassen er inkluderet i en relevant venteposition, vil Yammer meddelelser, der er blevet slettet, ikke længere være synlige i Yammer, men vil fortsat kunne findes med eDiscovery.

Når en opbevaringspolitik er konfigureret for Yammer meddelelser, afhænger de stier, som indholdet følger, af, om opbevaringspolitikken skal bevares og derefter slettes, kun bevares eller slettes.

Når opbevaringspolitikken skal bevares og derefter slettes:

![Diagram over opbevaringsflow for Yammer meddelelser.](../media/yammerretentionlifecycle.png)

For de to stier i diagrammet:

1. **Hvis en Yammer meddelelse redigeres eller slettes** af brugeren i opbevaringsperioden, kopieres den oprindelige meddelelse straks (hvis den redigeres) eller flyttes (hvis den slettes) til mappen SubstrateHolds. Meddelelsen gemmes der, indtil opbevaringsperioden udløber, og derefter slettes meddelelsen straks permanent.

2. **Hvis en Yammer meddelelse ikke slettes**, og for aktuelle meddelelser efter redigering, flyttes meddelelsen til mappen SubstrateHolds, når opbevaringsperioden udløber. Denne handling tager op til syv dage fra udløbsdatoen. Når meddelelsen er i mappen SubstrateHolds, slettes den straks permanent. 

> [!NOTE]
> Der kan søges i meddelelser i mappen SubstrateHolds af eDiscovery-værktøjer. Indtil meddelelser slettes permanent (i mappen SubstrateHolds), kan der stadig søges i dem af eDiscovery-værktøjer.

Når opbevaringspolitikken er bevar eller kun sletter, er indholdets stier variationer af bevarelse og sletning.

### <a name="content-paths-for-retain-only-retention-policy"></a>Indholdsstier til opbevaringspolitik kun for bevarelse

1. **Hvis en Yammer meddelelse redigeres eller slettes**: Der oprettes straks en kopi af den oprindelige meddelelse i mappen SubstrateHolds og gemmes der, indtil opbevaringsperioden udløber. Derefter slettes meddelelsen straks permanent fra mappen SubstrateHolds.

2. **Hvis den Yammer meddelelse ikke ændres eller slettes** og for aktuelle meddelelser efter redigering i løbet af opbevaringsperioden: Der sker intet før og efter opbevaringsperioden. Meddelelsen forbliver på den oprindelige placering.

### <a name="content-paths-for-delete-only-retention-policy"></a>Indholdsstier til opbevaringspolitik, der kun gælder for sletning

1. **Hvis den Yammer meddelelse ikke slettes** i løbet af opbevaringsperioden: Ved slutningen af opbevaringsperioden flyttes meddelelsen til mappen SubstrateHolds. Denne handling tager op til syv dage fra udløbsdatoen. Derefter slettes meddelelsen straks permanent fra mappen SubstrateHolds.

2. **Hvis den Yammer meddelelse slettes af brugeren** i løbet af perioden, flyttes elementet straks til mappen SubstrateHolds, hvor det slettes med det samme permanent.

#### <a name="example-flows-and-timings-for-retention-policies"></a>Eksempel på flow og tidsindstillinger for opbevaringspolitikker

Brug følgende eksempler til at se, hvordan de processer og tidsindstillinger, der er forklaret i de forrige afsnit, gælder for opbevaringspolitikker, der har følgende konfigurationer:

- [Eksempel 1: Bevar kun i 7 år](#example-1-retain-only-for-7-years)
- [Eksempel 2: Bevar i 30 dage, og slet derefter](#example-2-retain-for-30-days-and-then-delete)
- [Eksempel 3: Slet kun efter 1 dag](#example-3-delete-only-after-1-day)

For alle eksempler, der refererer til permanent sletning på grund [af principperne for opbevaring](retention.md#the-principles-of-retention-or-what-takes-precedence), afbrydes denne handling midlertidigt, hvis meddelelsen er underlagt en anden opbevaringspolitik for at bevare elementet, eller hvis det er i eDiscovery-venteposition.

##### <a name="example-1-retain-only-for-7-years"></a>Eksempel 1: Bevar kun i 7 år

På dag 1 sender en bruger en ny Yammer meddelelse.

Den 5. dag redigerer brugeren meddelelsen.

Den 30. dag sletter brugeren den aktuelle meddelelse.

Opbevaringsresultater:

- For den oprindelige meddelelse:
    - På dag 5 kopieres meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst syv år fra dag 1 (opbevaringsperioden).

- For den aktuelle (redigerede) meddelelse:
    - På dag 30 flyttes meddelelsen til mappen SubstrateHolds, hvor der stadig kan søges i den med eDiscovery-værktøjer i mindst 7 år fra dag 1 (opbevaringsperioden).

Hvis brugeren havde slettet den aktuelle meddelelse efter den angivne opbevaringsperiode i stedet for inden for opbevaringsperioden, ville meddelelsen stadig blive flyttet til mappen SubstrateHolds. Men nu, hvor opbevaringsperioden er udløbet, slettes meddelelsen permanent efter minimum 1 dag og derefter typisk inden for 1-7 dage.

##### <a name="example-2-retain-for-30-days-and-then-delete"></a>Eksempel 2: Bevar i 30 dage, og slet derefter

På dag 1 sender en bruger en ny Yammer meddelelse.

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

På dag 1 sender en bruger en ny Yammer meddelelse.

Eksempel på resultat af opbevaring, hvis brugeren ikke redigerer eller sletter meddelelsen:

- Dag 5 (typisk 1-7 dage efter starten af opbevaringsperioden på dag 2):
    - Meddelelsen flyttes til mappen SubstrateHolds og forbliver der mindst én dag, hvor der stadig kan søges i den med eDiscovery-værktøjer.

- Dag 9 (typisk 1-7 dage efter mindst 1 dag i mappen SubstrateHolds):
    - Meddelelsen slettes permanent og returneres derefter ikke med eDiscovery-søgninger.

Som dette eksempel viser, gennemgår tjenesten flere processer for at sikre en kompatibel sletning, selvom du kan konfigurere en opbevaringspolitik til at slette meddelelser efter blot én dag. En sletning efter 1 dag kan derfor tage 16 dage, før meddelelsen slettes permanent, så den ikke længere returneres i eDiscovery-søgninger.

## <a name="messages-and-external-users"></a>Meddelelser og eksterne brugere

En opbevaringspolitik for Yammer brugermeddelelser gælder som standard for alle brugere i organisationen, men ikke for eksterne brugere. Du kan anvende en opbevaringspolitik på eksterne brugere, hvis du bruger indstillingen **Rediger** for de brugere, der er inkluderet, og angive deres konto.

På nuværende tidspunkt understøttes Azure B2B-gæstebrugere ikke.

## <a name="when-a-user-leaves-the-organization"></a>Når en bruger forlader organisationen 

Hvis en bruger forlader organisationen, og vedkommendes Microsoft 365 konto slettes, gemmes de Yammer brugermeddelelser, der skal opbevares, i en inaktiv postkasse. Disse meddelelser forbliver underlagt en hvilken som helst opbevaringspolitik, der blev placeret på brugeren, før postkassen blev gjort inaktiv, og indholdet er tilgængeligt for en eDiscovery-søgning. Du kan få flere oplysninger under [Inaktive postkasser i Exchange Online](inactive-mailboxes-in-office-365.md). 

Hvis brugeren har gemt filer i Yammer, skal du se det [tilsvarende afsnit](retention-policies-sharepoint.md#when-a-user-leaves-the-organization) for SharePoint og OneDrive.

## <a name="limitations"></a>Begrænsninger

Vær opmærksom på følgende begrænsning, når du bruger opbevaring til Yammer communitymeddelelser og brugermeddelelser:

- Når du vælger **Rediger** for **placeringen af Yammer brugermeddelelser**, kan du se gæster og brugere, der ikke har postkasse. Opbevaringspolitikker er ikke udviklet til disse brugere, så vælg dem ikke.

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Hvis du ikke har arbejdet med at konfigurere opbevaring i Microsoft 365, skal du se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md).

Hvis du er klar til at konfigurere en opbevaringspolitik for Yammer, skal du se [Opret og konfigurer opbevaringspolitikker](create-retention-policies.md).
