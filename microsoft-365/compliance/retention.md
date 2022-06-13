---
title: Få mere at vide om opbevaringspolitikker & mærkater til automatisk at bevare eller slette indhold
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
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om opbevaringspolitikker og opbevaringsmærkater, der hjælper dig med at bevare det, du har brug for, og slette det, du ikke har brug for.
ms.openlocfilehash: 7124d97c56e414a7c5a47488805bb4134426f073
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66018024"
---
# <a name="learn-about-retention-policies-and-retention-labels"></a>Få mere at vide om opbevaringspolitikker og opbevaringsmærkater

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*


[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Hvis du får vist meddelelser om opbevaringspolitikker i Teams eller har spørgsmål om opbevaringsmærkater i dine apps, skal du kontakte it-afdelingen for at få oplysninger om, hvordan de er konfigureret for dig. I mellemtiden kan følgende artikler være nyttige:
>
> - [Teams meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b)
> - [Anvend opbevaringsmærkater på filer i SharePoint eller OneDrive](https://support.microsoft.com/office/apply-retention-labels-to-files-in-sharepoint-or-onedrive-11a6835b-ec9f-40db-8aca-6f5ef18132df)
>
> Oplysningerne på denne side er til it-administratorer, der kan oprette opbevaringspolitikker og opbevaringsmærkater af hensyn til overholdelse af angivne standarder.

For de fleste organisationer øges mængden og kompleksiteten af deres data dagligt – mail, dokumenter, chatbeskeder og meget mere. Det er vigtigt, at du administrerer eller styrer disse oplysninger effektivt, fordi du har brug for at:

- **Overhold proaktivt brancheregler og interne politikker** , der kræver, at du bevarer indhold i en minimumsperiode – f.eks. kan den Sarbanes-Oxley lov kræve, at du bevarer visse typer indhold i syv år.

- **Reducer din risiko i tilfælde af en retssag eller et sikkerhedsbrud** ved permanent at slette gammelt indhold, som du ikke længere behøver at beholde.

- **Hjælp din organisation med at dele viden effektivt og være mere fleksibel** ved at sikre, at dine brugere kun arbejder med indhold, der er aktuelt og relevant for dem.

Opbevaringsindstillinger, som du konfigurerer, kan hjælpe dig med at nå disse mål. Administration af indhold kræver ofte to handlinger:

| Handling| Formål |
|:-----|:-----|
|Bevar indhold | Undgå permanent sletning, og bliv ved med at være tilgængelig for eDiscovery |
|Slet indhold | Slet indhold permanent fra din organisation|

Med disse to opbevaringshandlinger kan du konfigurere opbevaringsindstillinger for følgende resultater:

- Bevar kun: Bevar indhold for evigt eller i et angivet tidsrum.
- Kun sletning: Slet indhold permanent efter et angivet tidsrum.
- Bevar og slet derefter: Bevar indhold i et bestemt tidsrum, og slet det derefter permanent.

Disse opbevaringsindstillinger fungerer sammen med det indhold, der er på plads, hvilket sparer dig for de ekstra omkostninger ved at oprette og konfigurere ekstra lagerplads, når du har brug for at bevare indhold af hensyn til overholdelse af angivne standarder. Derudover behøver du ikke at implementere brugerdefinerede processer for at kopiere og synkronisere disse data.

Brug følgende afsnit til at få mere at vide om, hvordan opbevaringspolitikker og opbevaringsmærkater fungerer, hvornår de skal bruges, og hvordan de supplerer hinanden. Men hvis du er klar til at komme i gang og udrulle opbevaringsindstillinger for nogle almindelige scenarier, skal du se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md).

## <a name="how-retention-settings-work-with-content-in-place"></a>Sådan fungerer opbevaringsindstillinger med indhold på plads

Når indhold har fået tildelt opbevaringsindstillinger, forbliver dette indhold på den oprindelige placering. For det meste fortsætter folk med at arbejde med deres dokumenter eller mail, som om intet er ændret. Men hvis de redigerer eller sletter indhold, der er inkluderet i opbevaringspolitikken, bevares der automatisk en kopi af indholdet.

- For SharePoint og OneDrive websteder: Kopien bevares i biblioteket **Bevarelsesvente.**

- For Exchange postkasser: Kopien bevares i mappen **Gendanbare elementer**.

- I forbindelse med Teams og Yammer meddelelser: Kopien bevares i en skjult mappe med navnet **SubstrateHolds** som en undermappe i mappen Exchange **Elementer, der kan gendannes**.

> [!NOTE]
> Da biblioteket til bevarelse af venteposition er inkluderet i webstedets lagerkvote, skal du muligvis øge dit lager, når du bruger opbevaringsindstillinger for SharePoint og Microsoft 365 grupper.
>
Disse sikre placeringer og det bevarede indhold er ikke synlige for de fleste. I de fleste tilfælde behøver folk ikke engang at vide, at deres indhold er underlagt opbevaringsindstillinger.

Du kan finde flere detaljerede oplysninger om, hvordan opbevaringsindstillinger fungerer for forskellige arbejdsbelastninger, i følgende artikler:

- [Få mere at vide om opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md)
- [Få mere at vide om opbevaring for Microsoft Teams](retention-policies-teams.md)
- [Få mere at vide om opbevaring for Yammer](retention-policies-yammer.md)
- [Få mere at vide om opbevaring for Exchange](retention-policies-exchange.md)

## <a name="retention-policies-and-retention-labels"></a>Opbevaringspolitikker og opbevaringsmærkater

Hvis du vil tildele dine opbevaringsindstillinger til indhold, skal du bruge **opbevaringspolitikker** og **opbevaringsmærkater med mærkatpolitikker**. Du kan kun bruge en af disse metoder eller kombinere dem.

Brug en opbevaringspolitik til at tildele de samme opbevaringsindstillinger for indhold på websteds- eller postkasseniveau, og brug en opbevaringsmærkat til at tildele opbevaringsindstillinger på elementniveau (mappe, dokument, mail).

Hvis alle dokumenter på et SharePoint websted f.eks. skal bevares i fem år, er det mere effektivt at gøre dette med en opbevaringspolitik end at anvende den samme opbevaringsmærkat på alle dokumenter på det pågældende websted. Men hvis nogle dokumenter på dette websted skal opbevares i 5 år, og andre opbevares i 10 år, vil en opbevaringspolitik ikke være i stand til at gøre dette. Når du har brug for at angive opbevaringsindstillinger på elementniveau, skal du bruge opbevaringsmærkater.

I modsætning til opbevaringspolitikker følger opbevaringsindstillinger fra opbevaringsmærkater indholdet, hvis det flyttes til en anden placering i din Microsoft 365 lejer. Derudover har opbevaringsmærkater følgende funktioner, som opbevaringspolitikker ikke understøtter:

- Muligheder for at starte opbevaringsperioden fra det tidspunkt, hvor indholdet blev mærket eller baseret på en hændelse, ud over indholdets alder, eller hvornår det sidst blev ændret.

- Brug [klassificeringer, der kan oplæres](classifier-learn-about.md) , til at identificere indhold, der skal navngives.

- Anvend et standardnavn for SharePoint elementer eller Exchange meddelelser.

- Understøttede handlinger i slutopbevaringsperioden:
  - [Gennemgang af fordeling](./disposition.md) for at gennemse indholdet, før det slettes permanent.
  - Anvend automatisk en anden opbevaringsmærkat

- Markér indholdet som en [post](records-management.md#records) som en del af etiketindstillingerne, og hav altid [bevis for fordeling](disposition.md#disposition-of-records) , når indhold slettes ved slutningen af opbevaringsperioden.

### <a name="retention-policies"></a>Opbevaringspolitikker

Opbevaringspolitikker kan anvendes på følgende placeringer:

- Exchange mail
- SharePoint websted
- OneDrive konti
- Microsoft 365-grupper
- Skype for Business
- Exchange offentlige mapper
- Teams kanalmeddelelser
- Teams chats
- Teams private kanalmeddelelser
- Yammer communitymeddelelser
- Yammer brugermeddelelser

> [!NOTE]
> Teams kanalmeddelelser omfatter nu [delte kanaler](/MicrosoftTeams/shared-channels) (i øjeblikket en prøveversion) samt standardkanaler.

Du kan meget effektivt anvende en enkelt politik på flere placeringer eller på bestemte placeringer eller brugere.

I starten af opbevaringsperioden kan du vælge, hvornår indholdet blev oprettet, eller kun understøttes for filer og SharePoint, OneDrive og Microsoft 365-grupper placeringer, hvornår indholdet sidst blev ændret.

Elementer nedarver opbevaringsindstillingerne fra deres objektbeholder, der er angivet i opbevaringspolitikken. Hvis de derefter flyttes uden for denne objektbeholder, når politikken er konfigureret til at bevare indhold, bevares en kopi af dette element på arbejdsbelastningens sikre placering. Opbevaringsindstillingerne følger dog ikke med indholdet på den nye placering. Hvis det er påkrævet, skal du bruge opbevaringsmærkater i stedet for opbevaringspolitikker.

### <a name="retention-labels"></a>Opbevaringsmærkater

Brug opbevaringsmærkater til forskellige typer indhold, der kræver forskellige opbevaringsindstillinger. Eksempel:

- Skatteformularer, der skal opbevares i en minimumsperiode.

- Pressemateriale, der skal slettes permanent, når de når en bestemt alder.

- Konkurrencedygtig forskning, der skal bevares i en bestemt periode og derefter slettes permanent.

- Arbejdsvisum, der skal markeres som en post, så de ikke kan redigeres eller slettes.

I alle disse tilfælde kan du bruge opbevaringsmærkater til at anvende opbevaringsindstillinger for styringskontrol på elementniveau (dokument eller mail).

Med opbevaringsmærkater kan du:

- **Giv personer i din organisation mulighed for at anvende en opbevaringsmærkat manuelt** på indhold i grupperne Outlook og Outlook på internettet, OneDrive, SharePoint og Microsoft 365. Brugerne ved ofte bedst, hvilken type indhold de arbejder med, så de kan klassificere det og anvende de relevante opbevaringsindstillinger.

- **Anvend opbevaringsmærkater på indhold automatisk**, hvis det opfylder bestemte betingelser, som omfatter vedhæftede filer i skyen, som deles i en mail eller Teams, eller når indholdet indeholder:
  - Specifikke typer følsomme oplysninger.
  - Specifikke nøgleord, der svarer til en forespørgsel, du opretter.
  - Mønsterforekomster for en klassificering, der kan oplæres.

- **Start opbevaringsperioden fra det tidspunkt, hvor indholdet blev mærket** for dokumenter på SharePoint websteder og OneDrive konti og for mailelementer.

- **Start opbevaringsperioden, når der opstår en hændelse**, f.eks. medarbejdere, der forlader organisationen, eller kontrakterne udløber.

- **Anvend en standardopbevaringsmærkat på et dokumentbibliotek, en mappe eller et dokumentsæt** i SharePoint, så alle dokumenter, der er gemt på denne placering, nedarver standardopbevaringsetiket.

- **Markér elementer som en post som en** del af din strategi [for datastyring](records-management.md) . Når dette navngivne indhold forbliver i Microsoft 365, er der yderligere begrænsninger for det indhold, der kan være nødvendigt af lovmæssige årsager. Du kan få flere oplysninger under [Sammenlign begrænsninger for, hvilke handlinger der er tilladt eller blokeret](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

Opbevaringsmærkater bevares i modsætning til [følsomhedsmærkater](sensitivity-labels.md) ikke, hvis indholdet flyttes uden for Microsoft 365.

#### <a name="classifying-content-without-applying-any-actions"></a>Klassificering af indhold uden at anvende nogen handlinger

Selvom det primære formål med opbevaringsmærkater er at bevare eller slette indhold, kan du også bruge opbevaringsmærkater uden at aktivere nogen opbevaring eller andre handlinger. I dette tilfælde kan du bruge en opbevaringsmærkat blot som en tekstetiket uden at gennemtvinge nogen handlinger.

Du kan f.eks. oprette og anvende en opbevaringsmærkat med navnet "Gennemse senere" uden handlinger og derefter bruge denne mærkat til at finde indholdet senere.

![Navneindstillinger, der kun skal klassificeres.](../media/retention-label-retentionoff.png)

#### <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Brug af en opbevaringsmærkat som en betingelse i en DLP-politik

Du kan angive en opbevaringsmærkat som en betingelse i en DLP-politik (Microsoft Purview Data Loss Prevention) for dokumenter i SharePoint. Konfigurer f.eks. en DLP-politik for at forhindre, at dokumenter deles uden for organisationen, hvis der er anvendt en angivet opbevaringsmærkat på dem.

Du kan få flere oplysninger under [Brug af en opbevaringsmærkat som en betingelse i en DLP-politik](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

#### <a name="retention-labels-and-policies-that-apply-them"></a>Opbevaringsmærkater og politikker, der anvender dem

Når du publicerer opbevaringsmærkater, medtages de i en **politik for opbevaringsmærkater** , der gør dem tilgængelige for administratorer og brugere, så de kan anvende dem på indhold. Som vist i følgende diagram:

1. En enkelt opbevaringsmærkat kan inkluderes i flere politikker for opbevaringsmærkater.

2. Politikker for opbevaringsmærkat angiver de placeringer, hvor opbevaringsmærkater skal publiceres. Den samme placering kan inkluderes i flere politikker for opbevaringsmærkater.

![Sådan kan opbevaringsmærkater føjes til mærkatpolitikker, der angiver placeringer.](../media/retention-labels-and-policies.png)

Du kan også oprette en eller flere **politikker for automatisk anvendelse af opbevaringsmærkater**, der hver har en enkelt opbevaringsmærkat. Med denne politik anvendes der automatisk en opbevaringsmærkat, når de betingelser, du angiver i politikken, er opfyldt.

#### <a name="retention-label-policies-and-locations"></a>Politikker og placeringer for opbevaringsmærkat

Opbevaringsmærkater kan publiceres på forskellige placeringer, afhængigt af hvad opbevaringsmærkaten gør.

| Hvis opbevaringsmærkaten er... | Derefter kan mærkatpolitikken anvendes på... |
|:-----|:-----|
|Publiceret til administratorer og slutbrugere  |Exchange, SharePoint, OneDrive, Microsoft 365-grupper  |
|Automatisk anvendt baseret på følsomme oplysningstyper eller klassificeringer, der kan oplæres  |Exchange, SharePoint, OneDrive  |
|Anvendes automatisk baseret på nøgleord eller en forespørgsel  |Exchange, SharePoint, OneDrive, Microsoft 365-grupper  |
|Automatisk anvendt på vedhæftede filer i skyen  |SharePoint, OneDrive, Microsoft 365-grupper  |

Exchange offentlige mapper, Skype, Teams og Yammer meddelelser understøtter ikke opbevaringsmærkater. Hvis du vil bevare og slette indhold fra disse placeringer, skal du i stedet bruge opbevaringspolitikker.

#### <a name="only-one-retention-label-at-a-time"></a>Kun én opbevaringsmærkat ad gangen

Der kan kun anvendes en enkelt opbevaringsmærkat på en mail eller et dokument ad gangen. En opbevaringsmærkat kan anvendes [manuelt](create-apply-retention-labels.md#manually-apply-retention-labels) af en slutbruger eller administrator eller automatisk ved hjælp af en af følgende metoder:

- [Anvend automatisk mærkatpolitik](apply-retention-labels-automatically.md)
- [Dokumentforståelsesmodel for SharePoint Syntex](../contentunderstanding/apply-a-retention-label-to-a-model.md)
- [Standardnavn for SharePoint](create-apply-retention-labels.md#applying-a-default-retention-label-to-all-content-in-a-sharepoint-library-folder-or-document-set) eller [Outlook](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)
- [Outlook regler](create-apply-retention-labels.md#automatically-applying-a-retention-label-to-email-by-using-rules)

For standardopbevaringsmærkater (de markerer ikke elementer som en [post eller lovmæssig post](records-management.md#records)):

- Administratorer og slutbrugere kan manuelt ændre eller fjerne en eksisterende opbevaringsmærkat, der er anvendt på indhold.

- Når der allerede er anvendt en opbevaringsmærkat for indhold, fjernes eller erstattes den eksisterende mærkat ikke automatisk af en anden opbevaringsmærkat med en mulig undtagelse: Den eksisterende mærkat blev anvendt som standardetiket. Når du bruger et standardnavn, er der nogle scenarier, hvor det kan erstattes af et andet standardnavn eller fjernes automatisk.

- Når der allerede er anvendt en opbevaringsmærkat for indhold, fjernes eller erstattes den eksisterende mærkat ikke automatisk af en anden opbevaringsmærkat med to mulige undtagelser:

  - Den eksisterende mærkat er konfigureret til automatisk at anvende en anden opbevaringsmærkat i slutningen af opbevaringsperioden.
  - Den eksisterende etiket blev anvendt som en standardetiket. Når du bruger et standardnavn, er der nogle scenarier, hvor det kan erstattes af et andet standardnavn eller fjernes automatisk.

  Du kan finde flere oplysninger om funktionsmåden for mærkater, når den anvendes ved hjælp af et standardnavn:

  - Standardnavn for SharePoint: [Funktionsmåde for navne, når du bruger en standardetiket til SharePoint](create-apply-retention-labels.md#label-behavior-when-you-use-a-default-label-for-sharepoint)
  - Standardnavn til Outlook: [Anvendelse af en standardopbevaringsmærkat på en Outlook mappe](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder)

- Hvis der er flere politikker for automatisk anvendelse af mærkater, der kan anvende en opbevaringsmærkat, og indhold opfylder betingelserne i flere politikker, anvendes opbevaringsmærkaten for den ældste politik for automatisk anvendelse af mærkater (efter oprettelsesdato).

Når opbevaringsmærkater markerer elementer som en post eller en lovmæssig post, ændres disse mærkater aldrig automatisk i løbet af deres konfigurerede opbevaringsperiode. Det er kun administratorer af objektbeholderen, der manuelt kan ændre eller fjerne opbevaringsmærkater, der markerer elementer som en post, men ikke lovmæssige poster. Du kan få flere oplysninger under [Sammenlign begrænsninger for, hvilke handlinger der er tilladt eller blokeret](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

#### <a name="monitoring-retention-labels"></a>Overvågning af opbevaringsmærkater

På Microsoft Purview-overholdelsesportalen skal du vælge **Dataklassificering** og siden **Oversigt** for at overvåge, hvordan dine opbevaringsmærkater bruges i din lejer, og identificere, hvor dine mærkede elementer er placeret. Du kan finde flere oplysninger, herunder vigtige forudsætninger, under [Få mere at vide om dataklassificering](data-classification-overview.md).

Du kan derefter foretage detailudledning i detaljer ved hjælp af [Indholdsoversigt](data-classification-content-explorer.md) og [Aktivitetsoversigt](data-classification-activity-explorer.md).

> [!TIP]
>Overvej at bruge nogle af de andre indsigter i dataklassificering, f.eks. klassificeringstyper, der kan oplæres, og følsomme infotyper for at hjælpe dig med at identificere indhold, som du muligvis skal bevare eller slette eller administrere som poster.

#### <a name="using-content-search-to-find-all-content-with-a-specific-retention-label"></a>Brug af indholdssøgning til at finde alt indhold med en bestemt opbevaringsmærkat

Når opbevaringsmærkater er anvendt på indhold, enten af brugere eller automatisk anvendt, kan du bruge indholdssøgning til at finde alle elementer, der har en bestemt opbevaringsmærkat anvendt.

Når du opretter en indholdssøgning, skal du vælge betingelsen **Opbevaringsmærkat** og derefter angive det fulde navn på opbevaringsmærkaten eller en del af navnet og bruge et jokertegn. Du kan finde flere oplysninger under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

![Betingelse for opbevaringsmærkat.](../media/retention-label-condition.png)

## <a name="compare-capabilities-for-retention-policies-and-retention-labels"></a>Sammenlign egenskaber for opbevaringspolitikker og opbevaringsmærkater

Brug følgende tabel til at hjælpe dig med at identificere, om du vil bruge en opbevaringspolitik eller en opbevaringsmærkat baseret på egenskaber.

|Kapacitet|Opbevaringspolitik |Opbevaringsmærkat|
|:-----|:-----|:-----|:-----|
|Opbevaringsindstillinger, der kan bevare og derefter slette, kun bevare eller slette |Ja |Ja |
|Understøttede arbejdsbelastninger: <br />- Exchange <br />- SharePoint <br />- OneDrive <br />- Microsoft 365 grupper <br />- Skype for Business <br />- Teams<br />- Yammer|<br /> Ja <br /> Ja <br /> Ja <br /> Ja <br /> Ja <br /> Ja <br /> Ja | <br /> Ja, undtagen offentlige mapper <br /> Ja <br /> Ja <br /> Ja <br /> Nej <br /> Nej <br /> Nej |
|Opbevaring anvendes automatisk | Ja | Ja |
|Anvend automatisk forskellige opbevaringsindstillinger i slutningen af opbevaringsperioden | Nej | Ja |
|Opbevaring anvendt på baggrund af betingelser <br /> – følsomme infotyper, KQL-forespørgsler og -nøgleord, klassificeringer, der kan oplæres, vedhæftede filer i cloudmiljøet| Nej | Ja |
|Opbevaring anvendes manuelt | Nej | Ja |
|Slutbrugerinteraktion | Nej | Ja |
|Bevares, hvis indholdet flyttes | Nej | Ja, i din Microsoft 365 lejer |
|Erklær element som en post| Nej | Ja |
|Start opbevaringsperioden, når den er mærket eller baseret på en hændelse | Nej | Ja |
|Dispositionsgennemgang | Nej| Ja |
|Bevis for fordeling i op til 7 år | Nej |Ja, når du bruger dispositionsgennemsyn, eller når elementet markeres som en post|
|Overvågningsadministratoraktiviteter| Ja | Ja|
|Overvågningsopbevaringshandlinger| Nej | Ja <sup>\*</sup> |
|Identificer elementer, der skal opbevares: <br /> - Indholdssøgning <br /> - Dataklassificeringsside, indholdsoversigt, aktivitetsoversigt | <br /> Nej <br /> Nej | <br /> Ja <br /> Ja|

**Fodnote:**

<sup>\*</sup>For opbevaringsmærkater, der ikke markerer indholdet som en post eller lovgivningsmæssig post, er overvågningshændelser begrænset til, når et element i SharePoint eller OneDrive har en mærkat anvendt, ændret eller fjernet. Du kan finde overvågningsoplysninger for opbevaringsmærkater i afsnittet [Overvågningsopbevaringshandlinger](#auditing-retention-actions) på denne side.

### <a name="combining-retention-policies-and-retention-labels"></a>Kombination af opbevaringspolitikker og opbevaringsmærkater

Du behøver ikke at vælge mellem kun at bruge opbevaringspolitikker eller kun opbevaringsmærkater. Begge metoder kan bruges sammen og faktisk supplere hinanden for en mere omfattende løsning.

Følgende eksempler er blot nogle af de måder, hvorpå du kan kombinere opbevaringspolitikker og opbevaringsmærkater for den samme placering.

Du kan finde flere oplysninger om, hvordan opbevaringspolitikker og opbevaringsmærkater arbejder sammen, og hvordan du bestemmer deres kombinerede resultat, i afsnittet på denne side, der forklarer [principperne for opbevaring, og hvad der har forrang](#the-principles-of-retention-or-what-takes-precedence).

#### <a name="example-for-users-to-override-automatic-deletion"></a>Eksempel på, at brugere tilsidesætter automatisk sletning

Scenarie: Indhold i brugernes OneDrive-konti slettes som standard automatisk efter fem år, men brugerne skal have mulighed for at tilsidesætte dette for bestemte dokumenter.

1. Du opretter og konfigurerer en opbevaringspolitik, der automatisk sletter indhold fem år efter den seneste ændring, og anvender politikken på alle OneDrive konti.

2. Du opretter og konfigurerer en opbevaringsmærkat, der bevarer indhold for evigt, og føjer dette til en mærkatpolitik, som du publicerer til alle OneDrive konti. Du forklarer brugerne, hvordan de manuelt anvender denne mærkat på bestemte dokumenter, der skal udelukkes fra automatisk sletning, hvis de ikke ændres efter fem år.

Eksempel på bevarelse af elementer i længere tid**

Scenarie: Som standard bevares SharePoint elementer automatisk og slettes derefter efter fem år, men dokumenter i bestemte biblioteker skal opbevares i 10 år.

1. Du opretter og konfigurerer en opbevaringspolitik, der automatisk bevarer og derefter sletter indhold efter fem år og anvender politikken på alle SharePoint og Microsoft 365-grupper instanser.

2. Du opretter og konfigurerer en opbevaringsmærkat, der automatisk bevarer indhold i 10 år. Du publicerer dette navn til SharePoint webstedsadministratorer, så de kan anvende det som en standardetiket, der nedarves af alle elementer i bestemte dokumentbiblioteker.

#### <a name="example-to-delete-items-in-a-shorter-time-period"></a>Eksempel på sletning af elementer i en kortere tidsperiode

Scenarie: Mails bevares som standard ikke, men slettes automatisk efter 10 år. Mails relateret til et bestemt projekt, der har et kodenavn for forhåndsudgivelse, skal dog slettes automatisk efter et år.

1. Du opretter og konfigurerer en opbevaringspolitik, der automatisk sletter indhold efter ti år, og anvender politikken på alle Exchange modtagere.

2. Du opretter og konfigurerer en opbevaringsmærkat, der automatisk sletter indhold efter et år. Indstillinger for anvendelse af dette mærkat på relevante mails omfatter:
    - Du opretter en politik for automatisk mærkning, der identificerer indhold ved hjælp af projektkodenavnet som nøgleordet, og anvender politikken på alle Exchange modtagere
    - Du publicerer etiketten og instruerer de brugere, der er involveret i projektet, om, hvordan du opretter en automatisk regel i Outlook, der anvender denne mærkat
    - Du publicerer etiketten og instruerer brugerne i at oprette en mappe i Outlook for alle mails, der er relateret til projektet, og de anvender den publicerede mærkat på mappen og opretter derefter en Outlook regel for at flytte alle projektrelaterede mails til denne mappe

## <a name="how-long-it-takes-for-retention-settings-to-apply"></a>Hvor lang tid det tager at anvende opbevaringsindstillinger

Når du sender opbevaringspolitikker for arbejdsbelastninger og mærkatpolitikker for automatisk at anvende en opbevaringsmærkat, kan der gå op til 7 dage, før opbevaringsindstillingerne anvendes på indhold:

- [Hvor lang tid det tager for opbevaringspolitikker at træde i kraft](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- [Hvor lang tid det tager, før opbevaringsmærkater træder i kraft](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect)

På samme måde kan der gå op til syv dage, før opbevaringsmærkater er synlige i apps, når du har publiceret mærkaterne:

- [Når opbevaringsmærkater bliver tilgængelige for anvendelse](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply)

Politikkerne træder ofte i kraft, og mærkater vil være synlige hurtigere end 7 dage. Men med mange potentielle variabler, der kan påvirke denne proces, er det bedst at planlægge de maksimale syv dage.

## <a name="adaptive-or-static-policy-scopes-for-retention"></a>Tilpassede eller statiske politikområder for opbevaring

Når du opretter en politik for opbevaringspolitik eller opbevaringsmærkat, skal du vælge mellem adaptiv og statisk for at definere omfanget af politikken.

- Et **adaptivt område** bruger en forespørgsel, som du angiver, så medlemskabet er ikke statisk, men dynamisk ved at køre dagligt i forhold til de attributter eller egenskaber, du angiver for de valgte placeringer. Du kan bruge flere tilpassede områder med en enkelt politik.

    Eksempel: Mails og OneDrive dokumenter til direktører kræver en længere opbevaringsperiode end standardbrugere. Du opretter en opbevaringspolitik med et adaptivt omfang, der bruger den Azure AD attributjobtitel for "Direktør", og derefter vælger Exchange mail og OneDrive kontoplaceringer for politikken. Det er ikke nødvendigt at angive mailadresser eller OneDrive URL-adresser for disse brugere, fordi det tilpassede område automatisk henter disse værdier. For nye direktører er det ikke nødvendigt at konfigurere opbevaringspolitikken igen, fordi disse nye brugere med deres tilsvarende værdier for mail og OneDrive hentes automatisk.

- Et **statisk område** bruger ikke forespørgsler og er begrænset i konfigurationen, da det kan anvendes på alle instanser for en angivet placering eller bruge medtagelse og udeladelser for bestemte instanser for den pågældende placering. Disse tre valgmuligheder omtales nogle gange som henholdsvis "organisationsdækkende", "include", og "excludes".

    Eksempel: Mails og OneDrive dokumenter til direktører kræver en længere opbevaringsperiode end standardbrugere. Du opretter en opbevaringspolitik med et statisk område, der vælger Exchange mail og OneDrive kontoplaceringer for politikken. For den Exchange mailplacering kan du identificere en gruppe, der kun indeholder direktørerne, så du angiver denne gruppe for opbevaringspolitikken, og gruppemedlemskabet med de respektive mailadresser hentes, når politikken oprettes. For placeringen af OneDrive-konti skal du identificere og derefter angive URL-adresser for individuelle OneDrive for hver leder. For nye direktører skal du konfigurere opbevaringspolitikken igen for at tilføje de nye mailadresser og OneDrive URL-adresser. Du skal også opdatere OneDrive URL-adresser, når der er en ændring i en leders UPN.

    OneDrive URL-adresser er særligt udfordrende at angive pålideligt, da disse URL-adresser som standard ikke oprettes, før brugeren får adgang til deres OneDrive første gang. Og hvis en brugers UPN ændres, hvilket du måske ikke kender til, ændres vedkommendes OneDrive URL-adresse automatisk.

Fordele ved at bruge tilpassede områder:

- Der er ingen grænser for [antallet af elementer pr. politik](retention-limits.md#maximum-number-of-items-per-policy). Selvom tilpassede politikker stadig er underlagt det [maksimale antal politikker pr. lejerbegrænsninger](retention-limits.md#maximum-number-of-policies-per-tenant) , vil den mere fleksible konfiguration sandsynligvis resultere i langt færre politikker.

- Mere effektiv målretning i forhold til dine opbevaringskrav. Du kan f.eks. tildele forskellige opbevaringsindstillinger til brugerne i henhold til deres geografiske placering ved hjælp af eksisterende Azure AD attributter, uden at der er administrative omkostninger forbundet med at oprette og vedligeholde grupper til dette formål.

- Forespørgselsbaseret medlemskab sikrer robusthed over for forretningsændringer, der muligvis ikke afspejles pålideligt i gruppemedlemskab eller eksterne processer, der er afhængige af kommunikation på tværs af afdelinger.

- En enkelt opbevaringspolitik kan omfatte placeringer for både Microsoft Teams og Yammer, hvorimod disse placeringer kræver deres egen opbevaringspolitik, når du bruger et statisk område.

- Du kan kun anvende specifikke opbevaringsindstillinger for inaktive postkasser. Denne konfiguration er ikke mulig med et statisk område, fordi statiske områder ikke understøtter specifik medtagelse af modtagere med inaktive postkasser på det tidspunkt, hvor politikken tildeles.

Fordele ved at bruge statiske områder:

- Enklere konfiguration, hvis alle forekomster automatisk skal vælges for en arbejdsbelastning.

    For "include" og "excludes" kan dette valg være en enklere konfiguration i starten, hvis antallet af forekomster, du skal angive, er lavt og ikke ændres. Men når dette antal forekomster begynder at stige, og du ofte ændrer i din organisation, som kræver, at du omkonfigurerer dine politikker, kan tilpassede områder være nemmere at konfigurere og meget nemmere at vedligeholde.

- Placeringerne **Skype for Business** og **Exchange offentlige mapper** understøtter ikke tilpassede områder. For disse placeringer skal du bruge et statisk område.

Du kan finde konfigurationsoplysninger under [Konfiguration af tilpassede områder](retention-settings.md#configuration-information-for-adaptive-scopes).

Hvis du vil se et optaget webinar (kræver registrering), skal du gå [til Detaljeret gennemgang af adaptive omfang](https://mipc.eventbuilder.com/event/45703).

> [!IMPORTANT]
> I øjeblikket understøtter tilpassede områder ikke [Bevarelseslås for at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater](#use-preservation-lock-to-restrict-changes-to-policies).

## <a name="policy-lookup"></a>Politikopslag

Du kan konfigurere flere opbevaringspolitikker for Microsoft 365 placeringer samt flere politikker for opbevaringsmærkater, som du publicerer eller anvender automatisk. Hvis du vil finde de politikker for opbevaring, der er tildelt bestemte brugere, websteder og Microsoft 365 grupper, skal du bruge **Politikopslag** fra løsningerne til **administration af datalivscyklus** eller **Dataadministration** på Microsoft Purview-overholdelsesportalen.

Eksempel:

![Politikopslag for at finde politikker for opbevaring, der er tildelt bestemte brugere, websteder og Microsoft 365 grupper ](../media/policy-lookup.png)

Du skal angive den nøjagtige mailadresse for en bruger, den nøjagtige URL-adresse for et websted eller den nøjagtige mailadresse for en Microsoft 365 gruppe. Du kan f.eks. ikke bruge jokertegn eller delvise matches.

Indstillingen for websteder omfatter OneDrive konti. Du kan få oplysninger om, hvordan du angiver URL-adressen for en brugers OneDrive-konto, under [Hent en liste over alle bruger-OneDrive URL-adresser i din organisation](/onedrive/list-onedrive-urls).

## <a name="the-principles-of-retention-or-what-takes-precedence"></a>Principperne for opbevaring, eller hvad har forrang?

I modsætning til opbevaringsmærkater kan du anvende mere end én opbevaringspolitik på det samme indhold. Hver opbevaringspolitik kan resultere i en bevarelseshandling og en sletningshandling. Desuden kan elementet også være underlagt disse handlinger fra en opbevaringsmærkat.

Når elementer i dette scenarie kan være underlagt flere opbevaringsindstillinger, der kan være i konflikt med hinanden, hvad har så forrang for at bestemme resultatet?

Resultatet er ikke hvilken enkelt opbevaringspolitik eller en enkelt opbevaringsmærkat der vinder, men hvor længe et element bevares (hvis relevant), og hvornår et element slettes (hvis det er relevant). Disse to handlinger beregnes uafhængigt af hinanden ud fra alle de opbevaringsindstillinger, der anvendes på et element.

Et element kan f.eks. være underlagt én opbevaringspolitik, der er konfigureret til kun at blive slettet, og en anden opbevaringspolitik, der er konfigureret til at bevare og derefter slette. Derfor har dette element kun én bevarelseshandling, men to sletningshandlinger. Opbevarings- og sletningshandlingerne kan være i konflikt med hinanden, og de to sletningshandlinger kan have en modstridende dato. Principperne for opbevaring forklarer resultatet.

På et højt niveau kan du være sikker på, at opbevaring altid har forrang frem for permanent sletning, og at den længste opbevaringsperiode vinder. Disse to enkle regler bestemmer altid, hvor længe et element bevares.

Der er nogle flere faktorer, der bestemmer, hvornår et element slettes permanent, hvilket omfatter sletningshandlingen fra en opbevaringsmærkat, der altid har forrang for sletningshandlingen fra en opbevaringspolitik.

Brug følgende flow til at forstå resultaterne af opbevaring og sletning for et enkelt element, hvor hvert niveau fungerer som tie breaker for konflikter oppefra og ned. Hvis resultatet bestemmes af det første niveau, fordi der ikke er flere konflikter, er der ingen grund til at gå videre til det næste niveau osv.

> [!IMPORTANT]
> Hvis du bruger opbevaringsmærkater: Før du anvender principperne til at bestemme resultatet af flere opbevaringsindstillinger for det samme element, skal du sørge for, at du ved [, hvilken opbevaringsmærkat der anvendes](#only-one-retention-label-at-a-time).

![Diagram over principperne for opbevaring.](../media/principles-of-retention.png)

Før du forklarer hvert princip mere detaljeret, er det vigtigt at forstå forskellen mellem opbevaringsperioden for elementet i forhold til den angivne opbevaringsperiode i opbevaringspolitikken eller opbevaringsmærkaten. Det skyldes, at selvom standardkonfigurationen er at starte opbevaringsperioden, når der oprettes et element, så slutningen af opbevaringsperioden er fast for elementet, understøtter filer også konfigurationen til at starte opbevaringsperioden fra det tidspunkt, hvor filen sidst blev ændret. Med denne alternative konfiguration nulstilles starten af opbevaringsperioden, hver gang filen ændres, hvilket udvider slutningen af opbevaringsperioden for elementet. Opbevaringsmærkater understøtter også start af opbevaringsperioden, når de er mærket og i starten af en hændelse.

Hvis du vil anvende principperne i aktion med en række spørgsmål af typen Ja og Nej, kan du også bruge [opbevaringsrutediagrammet](retention-flowchart.md).

Forklaring af de fire forskellige principper:

1. **Opbevaring vinder over sletning.** Indhold slettes ikke permanent, når det også har opbevaringsindstillinger til at bevare det. Selvom dette princip sikrer, at indhold bevares af hensyn til overholdelse af angivne standarder, kan sletningsprocessen stadig startes (brugerinitieret eller systeminitieret) og kan derfor fjerne indholdet fra brugernes primære visning. Permanent sletning er dog suspenderet. Du kan få flere oplysninger om, hvordan og hvor indhold bevares, ved at bruge følgende links for hver arbejdsbelastning:

    - [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive)
    - [Sådan fungerer opbevaring sammen med Microsoft Teams](retention-policies-teams.md#how-retention-works-with-microsoft-teams)
    - [Sådan fungerer opbevaring sammen med Yammer](retention-policies-yammer.md#how-retention-works-with-yammer)
    - [Sådan fungerer opbevaring for Exchange](retention-policies-exchange.md#how-retention-works-for-exchange)

    **Eksempel på dette første princip**: En mail er underlagt en opbevaringspolitik for Exchange, der er konfigureret til at slette elementer tre år efter oprettelsen, og der er også anvendt en opbevaringsmærkat, der er konfigureret til at bevare elementer fem år efter oprettelsen.

    Mailen bevares i fem år, fordi denne opbevaringshandling har forrang frem for sletning. Mailen slettes permanent ved udgangen af de fem år på grund af den slettehandling, der blev suspenderet, mens opbevaringshandlingen var i kraft.

2. **Den længste opbevaringsperiode vinder.** Hvis indhold er underlagt flere opbevaringsindstillinger, der bevarer indhold i forskellige tidsperioder, bevares indholdet indtil udgangen af den længste opbevaringsperiode for elementet.

    > [!NOTE]
    > Det er muligt for en opbevaringsperiode på 5 år i en opbevaringspolitik eller mærkat vinder over en opbevaringsperiode på 7 år i en opbevaringspolitik eller en mærkat, fordi 5-års perioden er konfigureret til at starte på baggrund af, hvornår filen senest er ændret, og perioden på 7 år er konfigureret til at starte fra det tidspunkt, hvor filen oprettes.

    **Eksempel på dette andet princip**: Dokumenter på webstedet marketing SharePoint er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er konfigureret for alle SharePoint websteder for at bevare elementer i fem år, efter at de er oprettet. Den anden opbevaringspolitik er konfigureret for bestemte SharePoint websteder for at bevare elementer i ti år, efter at de er oprettet.

    Dokumenter på dette marketingwebsted SharePoint opbevares i 10 år, fordi det er den længste opbevaringsperiode for elementet.

3. **Eksplicitte gevinster over implicitte for sletninger.** Med konflikter, der nu er løst i forbindelse med opbevaring, er det kun konflikterne for sletninger, der forbliver:

    1. En opbevaringsmærkat (men den blev anvendt) indeholder eksplicit opbevaring i forhold til opbevaringspolitikker, fordi opbevaringsindstillingerne anvendes på et individuelt element i stedet for implicit tildelt fra en objektbeholder. Det betyder, at en sletning fra en opbevaringsmærkat altid har forrang for en sletningshandling fra en opbevaringspolitik.

        **Eksempel på dette tredje princip (mærkat):** Et dokument er underlagt to opbevaringspolitikker, der har en sletningshandling på henholdsvis fem år og ti år, og en opbevaringsmærkat, der har en sletningshandling på syv år.

        Dokumentet slettes permanent efter syv år, fordi sletningen fra opbevaringsmærkaten har forrang.

    2. Når du kun har opbevaringspolitikker: Hvis en opbevaringspolitik for en placering bruger et adaptivt omfang eller et statisk område, der indeholder bestemte instanser (f.eks. specifikke brugere for Exchange mail), har opbevaringspolitikken forrang over et statisk område, der er konfigureret for alle instanser for den samme placering.

        Et statisk område, der er konfigureret for alle instanser for en placering, kaldes nogle gange for en "politik for hele organisationen". Du kan f.eks. **Exchange mail** og standardindstillingen for **Alle modtagere**. Eller **SharePoint websteder** og standardindstillingen for **Alle websteder**. Når opbevaringspolitikker ikke er i hele organisationen, men er konfigureret med et adaptivt omfang eller et statisk omfang, der omfatter bestemte instanser, har de samme prioritet på dette niveau.

        **Eksempel 1 til dette tredje princip (politikker):** En mail er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er uden for området og sletter elementer efter ti år. Den anden opbevaringspolitik er begrænset til bestemte postkasser og sletter elementer efter fem år.

        Mailen slettes permanent efter fem år, fordi sletningen fra den områdebaserede opbevaringspolitik har forrang over opbevaringspolitikken for hele organisationen.

        **Eksempel 2 til dette tredje princip (politikker):** Et dokument på en brugers OneDrive konto er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er begrænset til at omfatte denne brugers OneDrive konto og har en sletningshandling efter 10 år. Den anden opbevaringspolitik er begrænset til at omfatte denne brugers OneDrive konto og har en sletningshandling efter syv år.

        Når dette dokument slettes permanent, kan det ikke bestemmes på dette niveau, fordi begge opbevaringspolitikker er begrænset til at omfatte bestemte instanser.

4. **Den korteste sletningsperiode vinder.** Gælder for at bestemme, hvornår elementer slettes fra opbevaringspolitikker, og resultatet ikke kunne løses fra det forrige niveau: Indholdet slettes permanent i slutningen af den korteste opbevaringsperiode for elementet.

    > [!NOTE]
    > Det er muligt, at en opbevaringspolitik, der har en opbevaringsperiode på 7 år, vinder i forhold til en opbevaringspolitik på 5 år, fordi den første politik er konfigureret til at starte opbevaringsperioden baseret på, hvornår filen oprettes, og den anden opbevaringspolitik fra, hvornår filen senest ændres.

    **Eksempel på dette fjerde princip**: Et dokument på en brugers OneDrive konto er underlagt to opbevaringspolitikker. Den første opbevaringspolitik er begrænset til at omfatte denne brugers OneDrive konto og har en sletningshandling på 10 år, efter at filen er oprettet. Den anden opbevaringspolitik er begrænset til at omfatte denne brugers OneDrive-konto og har en sletningshandling på syv år, efter at filen er oprettet.

    Dette dokument slettes permanent efter syv år, fordi det er den korteste opbevaringsperiode for elementet fra disse to områdeopbevaringspolitikker.

Elementer, der er omfattet af eDiscovery-venteposition, er også omfattet af det første opbevaringsprincip. De kan ikke slettes permanent af nogen opbevaringspolitik eller opbevaringsmærkat. Når denne bevarelse er frigivet, gælder principperne for opbevaring fortsat for dem. De kan f.eks. være underlagt en ikke-udløbet opbevaringsperiode eller en sletningshandling.

### <a name="principles-of-retention-examples-that-combine-retain-and-delete-actions"></a>Principper for opbevaringseksempler, der kombinerer bevarelses- og sletningshandlinger

Følgende eksempler er mere komplekse for at illustrere principperne for opbevaring, når forskellige bevarelses- og sletningshandlinger kombineres. For at gøre det nemmere at følge eksemplerne bruger alle opbevaringspolitikker og -mærkater standardindstillingen for at starte opbevaringsperioden, når elementet oprettes, så slutningen af opbevaringsperioden er den samme for elementet.

1. Der er anvendt følgende opbevaringsindstillinger for et element:

    - En opbevaringspolitik kun for sletning efter fem år
    - En opbevaringspolitik, der opbevares i tre år og derefter sletter
    - En opbevaringsmærkat, der kun opbevares i syv år

    **Resultat**: Elementet bevares i syv år, fordi opbevaring har forrang frem for sletning, og syv år er den længste opbevaringsperiode for elementet. Ved slutningen af denne opbevaringsperiode slettes elementet permanent på grund af sletningshandlingen fra opbevaringspolitikkerne.

    Selvom de to opbevaringspolitikker har forskellige datoer for sletningshandlinger, er den tidligste, at elementet kan slettes permanent, ved slutningen af den længste opbevaringsperiode, hvilket er længere end begge datoer for sletning.

2. Der er anvendt følgende opbevaringsindstillinger for et element:

    - En opbevaringspolitik for hele organisationen, der kun sletter efter 10 år
    - En opbevaringspolitik, der er begrænset til bestemte instanser, der opbevares i fem år og derefter sletter
    - En opbevaringsmærkat, der opbevares i tre år og derefter sletter

    **Resultat**: Elementet bevares i fem år, fordi det er den længste opbevaringsperiode for elementet. Ved slutningen af opbevaringsperioden slettes elementet permanent på grund af sletningshandlingen på tre år fra opbevaringsmærkaten. Sletning fra opbevaringsmærkater tilsidesætter sletning fra alle opbevaringspolitikker. I dette eksempel løses alle konflikter på tredje niveau.

## <a name="use-preservation-lock-to-restrict-changes-to-policies"></a>Brug Bevarelseslås til at begrænse ændringer af politikker

Nogle organisationer skal muligvis overholde regler, der er defineret af regulerende organer, f.eks. Sikkerhed og Exchange Commission (SEC) Rule 17a-4, hvilket kræver, at når en politik for opbevaring er slået til, kan den ikke slås fra eller gøres mindre restriktiv.

Bevarelseslås sikrer, at din organisation kan opfylde sådanne lovmæssige krav, fordi den låser en opbevaringspolitik eller en opbevaringsmærkatpolitik, så ingen – herunder en administrator – kan slå politikken fra, slette politikken eller gøre den mindre restriktiv.

Du anvender bevarelseslås, når opbevaringspolitikken eller opbevaringsmærkatpolitikken er oprettet. Du kan finde flere oplysninger og instruktioner under [Brug bevarelseslås til at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).

## <a name="releasing-a-policy-for-retention"></a>Frigivelse af en politik til opbevaring

Hvis du angiver, at dine politikker for opbevaring ikke har en bevarelseslås, kan du når som helst slette dine politikker, hvilket effektivt slår opbevaringsindstillingerne for en opbevaringspolitik fra, og opbevaringsmærkater kan ikke længere anvendes fra politikker for opbevaringsmærkater. Alle tidligere anvendte opbevaringsmærkater forbliver sammen med deres konfigurerede opbevaringsindstillinger, og for disse mærkater kan du stadig opdatere opbevaringsperioden, når den ikke er baseret på, hvornår elementer blev mærket.

Du kan også beholde en politik, men ændre placeringsstatus til Fra eller deaktivere politikken. En anden mulighed er at konfigurere politikken igen, så den ikke længere indeholder bestemte brugere, websteder, grupper osv.

Yderligere oplysninger om bestemte placeringer:

- **SharePoint websteder og OneDrive konti:**

    Når du frigiver en opbevaringspolitik for SharePoint websteder og OneDrive konti, bevares alt indhold, der er underlagt opbevaring fra politikken, i 30 dage for at forhindre utilsigtet datatab. I løbet af denne 30-dages udvidede periode bevares slettede filer stadig (filer føjes fortsat til biblioteket bevarelsesventeposition), men det timerjob, der jævnligt rydder op i biblioteket Bevarelsesposition, er midlertidigt afbrudt for disse filer, så du kan gendanne dem, hvis det er nødvendigt.

    En undtagelse til denne 30-dages respitperiode er, når du opdaterer politikken for at udelade et eller flere websteder for SharePoint eller konti for OneDrive. I dette tilfælde sletter timerjobbet filer for disse placeringer i biblioteket bevarelsesposition uden den 30-dages forsinkelse.

    Du kan få flere oplysninger om biblioteket bevarelsesposition under [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

    Hvis du genaktiverer politikken eller ændrer placeringsstatus til inden for 30 dage, fortsætter politikken på grund af funktionsmåden i den udvidede periode uden permanent tab af data i denne periode.

- **Exchange mail og Microsoft 365-grupper**

  Når du frigiver en opbevaringspolitik for postkasser, der er [inaktive](inactive-mailboxes-in-office-365.md) på det tidspunkt, hvor politikken udgives:

  - Hvis opbevaringspolitikken udtrykkeligt anvendes på en postkasse, gælder opbevaringsindstillingerne ikke længere. Når der ikke er anvendt nogen opbevaringsindstillinger, bliver en inaktiv postkasse berettiget til automatisk sletning på den sædvanlige måde.

    En eksplicit opbevaringspolitik kræver enten et adaptivt politikomfang eller et statisk politikomfang med en "include"-konfiguration, der angav en aktiv postkasse på det tidspunkt, hvor politikken blev anvendt og senere blev inaktiv

  - Hvis opbevaringspolitikken implicit anvendes på en postkasse, og den konfigurerede opbevaringshandling skal bevares, gælder opbevaringspolitikken fortsat, og en inaktiv postkasse bliver aldrig berettiget til automatisk sletning. Når opbevaringshandlingen ikke længere gælder, fordi opbevaringsperioden er udløbet, kan den Exchange administrator nu [slette den inaktive postkasse manuelt](delete-an-inactive-mailbox.md)

    En implicit opbevaringspolitik kræver et statisk politikområde med konfigurationen **Alle modtagere** (for Exchange mail) eller **Alle grupper** (for Microsoft 365-grupper).

    Du kan finde flere oplysninger om inaktive postkasser, hvor der er anvendt opbevaringspolitikker, under [Inaktive postkasser og Microsoft 365 opbevaring](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-microsoft-365-retention).

## <a name="auditing-retention-configuration-and-actions"></a>Konfiguration af overvågningsopbevaring og handlinger

Når [overvågning er aktiveret](turn-audit-log-search-on-or-off.md), understøttes overvågningshændelser for opbevaring for både administrationkonfiguration (opbevaringspolitikker og opbevaringsmærkater) og opbevaringshandlinger (kun opbevaringsmærkater).

### <a name="auditing-retention-configuration"></a>Konfiguration af overvågningsopbevaring

Administratorkonfiguration for opbevaringspolitikker og opbevaringsmærkater logføres som overvågningshændelser, når der oprettes, konfigureres eller slettes en opbevaringspolitik eller en mærkat.

Du kan se en komplet liste over overvågningshændelser under [Aktiviteter for opbevaringspolitik og opbevaringsmærkat](search-the-audit-log-in-security-and-compliance.md#retention-policy-and-retention-label-activities).

### <a name="auditing-retention-actions"></a>Overvågningsopbevaringshandlinger

Opbevaringshandlinger, der logføres som overvågningshændelser, er kun tilgængelige for opbevaringsmærkater og ikke for opbevaringspolitikker:

- Når der anvendes, ændres eller fjernes en opbevaringsmærkat fra et element i SharePoint eller OneDrive:
  - Fra **Fil- og sideaktiviteter** skal du vælge **Ændret opbevaringsmærkat for en fil**

- Når et navngivet element i SharePoint er markeret som en post, og det låses op eller låses af en bruger:
  - Fra **Fil- og sideaktiviteter** skal du vælge **Ændret poststatus til ulåst** og **Ændret poststatus til låst**

- Når en opbevaringsmærkat, der markerer indhold som en post eller lovmæssig post, anvendes på et element i Exchange:
  - Fra **Exchange postkasseaktiviteter** skal du vælge **Markeret meddelelse som en post**

- Når et navngivet element i SharePoint, OneDrive eller Exchange er markeret som en post eller lovmæssig post, og det slettes permanent:
  - Fra **Fil- og sideaktiviteter** skal du vælge **Slettet fil, der er markeret som en post**

- Når en dispositionslæser udfører en handling for et element, der har nået slutningen af opbevaringsperioden:
  - Fra **Dispositionsgennemgangsaktiviteter** skal du vælge **Godkendt bortskaffelse**, **Udvidet opbevaringsperiode**, **Genmærket element** eller **Tilføjede korrekturlæsere**

## <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>PowerShell-cmdlet'er til opbevaringspolitikker og opbevaringsmærkater

Hvis du vil bruge opbevarings-cmdlet'erne, skal du først [oprette forbindelse til Office 365 Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell). Brug derefter en af følgende cmdlet'er:

- [Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)

- [New-ComplianceTag](/powershell/module/exchange/new-compliancetag)

- [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag)

- [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag)

- [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage)

- [Get-ComplianceTagStorage](/powershell/module/exchange/get-compliancetagstorage)

- [Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig)

- [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy)

- [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy)

- [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy)

- [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/set-recordreviewnotificationtemplateconfig)

- [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy)

- [Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancerule)

- [Overholdelse af overholdelse af ny opbevaring](/powershell/module/exchange/new-retentioncompliancerule)

- [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)

- [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule)

## <a name="when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds"></a>Hvornår skal du bruge opbevaringspolitikker og opbevaringsmærkater eller eDiscovery-ventepositioner?

Selvom opbevaringsindstillinger og [ventepositioner, som du opretter med en eDiscovery-sag](create-ediscovery-holds.md) , begge kan forhindre, at data slettes permanent, er de udviklet til forskellige scenarier. Du kan få hjælp til at forstå forskellene og beslutte, hvilken du vil bruge, ved at bruge følgende vejledning:

- Opbevaringsindstillinger, som du angiver i opbevaringspolitikker og opbevaringsmærkater, er designet til en langsigtet strategi for administration af datalivscyklus for at bevare eller slette data med henblik på overholdelse af angivne standarder. Omfanget er normalt bredt, hvor hovedfokus er placeringen og indholdet i stedet for individuelle brugere. Start og afslutning af opbevaringsperioden kan konfigureres med mulighed for automatisk at slette indhold uden yderligere administratorinput.

- Ventepositioner for eDiscovery-sager (enten eDiscovery (Standard) eller eDiscovery-sager (Premium) er designet til en begrænset varighed for at bevare data til en juridisk undersøgelse. Omfanget er specifikt med fokus på indhold, der ejes af identificerede brugere. Starten og slutningen af bevarelsesperioden kan ikke konfigureres, men afhænger af individuelle administratorhandlinger uden mulighed for automatisk at slette indhold, når ventepositionen frigives.

Oversigt, der sammenligner opbevaring med ventepositioner:

|Overvejelse|Fastholdelse |eDiscovery-ventepositioner|
|:-----|:-----|:-----|:-----|
|Forretningsbehov: |Overholdelse af regler og standarder |Juridiske |
|Tidsområde: |Langsigtede |Kortsigtede |
|Fokus: |Bred, indholdsbaseret |Specifik, brugerbaseret |
|Konfigurerbar start- og slutdato: |Ja |Nej |
|Sletning af indhold: |Ja (valgfrit) |Nej |
|Administrative udgifter: |Lav |Høj |

Hvis indhold er underlagt både opbevaringsindstillinger og eDiscovery-venteposition, har bevarelse af indhold til eDiscovery-venteposition altid forrang. På denne måde udvides [principperne for opbevaring](#the-principles-of-retention-or-what-takes-precedence) til eDiscovery, fordi de bevarer data, indtil en administrator frigiver ventepositionen manuelt. På trods af denne prioritet skal du dog ikke bruge eDiscovery-ventepositioner til langsigtet administration af datalivscyklusser. Hvis du er bekymret for automatisk sletning af data, kan du konfigurere opbevaringsindstillinger for at bevare elementer for evigt eller bruge [dispositionsgennemsyn](disposition.md#disposition-reviews) med opbevaringsmærkater.

Hvis du bruger ældre eDiscovery-værktøjer til at bevare data, kan du se følgende ressourcer:

- Exchange:
  - [Bevarelse på stedet og procesførelse](/exchange/security-and-compliance/in-place-and-litigation-holds)
  - [Sådan identificeres den type venteposition, der er placeret i en Exchange Online postkasse](./identify-a-hold-on-an-exchange-online-mailbox.md)

- SharePoint og OneDrive:
  - [Føj indhold til en sag, og placer kilder i venteposition i eDiscovery Center](/SharePoint/governance/add-content-to-a-case-and-place-sources-on-hold-in-the-ediscovery-center)

- [Ophør af ældre eDiscovery-værktøjer](legacy-ediscovery-retirement.md)

## <a name="use-retention-policies-and-retention-labels-instead-of-older-features"></a>Brug opbevaringspolitikker og opbevaringsmærkater i stedet for ældre funktioner

Hvis du har brug for proaktivt at bevare eller slette indhold i Microsoft 365 til administration af datalivscyklus, anbefaler vi, at du bruger opbevaringspolitikker og opbevaringsmærkater i stedet for følgende ældre funktioner.

Hvis du i øjeblikket bruger disse ældre funktioner, vil de fortsat fungere side om side med Microsoft 365 opbevaringspolitikker og opbevaringsmærkater. Vi anbefaler dog, at du fremover bruger Microsoft 365 opbevaringspolitikker og opbevaringsmærkater til at drage fordel af en enkelt løsning til at administrere både opbevaring og sletning af indhold på tværs af flere arbejdsbelastninger i Microsoft 365.

**Ældre funktioner fra Exchange Online:**

- [Opbevaringstags og opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies), også kendt som [mrm (messaging records management)](/exchange/security-and-compliance/messaging-records-management/messaging-records-management) (kun sletning)

  Men hvis du bruger følgende MRM-funktioner, skal du være opmærksom på, at de i øjeblikket ikke understøttes af Microsoft 365 opbevaringspolitikker:

  - En arkivpolitik for [, at arkivpostkasser](enable-archive-mailboxes.md) automatisk flytter mails fra en brugers primære postkasse til deres arkivpostkasse efter et angivet tidsrum. En arkivpolitik (med alle indstillinger) kan bruges sammen med en opbevaringspolitik for Microsoft 365, der gælder for en brugers primære postkasse og arkivpostkasse.

  - Opbevaringspolitikker, der anvendes af en administrator på bestemte mapper i en postkasse. En Microsoft 365 opbevaringspolitik gælder for alle mapper i postkassen. En administrator kan dog konfigurere forskellige opbevaringsindstillinger ved hjælp af opbevaringsmærkater, som en bruger kan anvende på mapper i Outlook som [standardopbevaringsmærkat](create-apply-retention-labels.md#applying-a-default-retention-label-to-an-outlook-folder).

- [Procesførelse (](create-a-litigation-hold.md) kun opbevaring)

   Selvom tvister stadig understøttes, anbefaler vi, at du bruger Microsoft 365 opbevaring eller eDiscovery-bevarelse efter [behov](#when-to-use-retention-policies-and-retention-labels-or-ediscovery-holds).

**Ældre funktioner fra SharePoint og OneDrive:**

- [Politikker for sletning af dokumenter](https://support.office.com/article/Create-a-document-deletion-policy-in-SharePoint-Server-2016-4fe26e19-4849-4eb9-a044-840ab47458ff) (kun sletning)

- [Konfiguration af datastyring på stedet](https://support.office.com/article/7707a878-780c-4be6-9cb0-9718ecde050a) (kun opbevaring)

- [Brug politikker til lukning og sletning af webstedet](https://support.microsoft.com/en-us/office/use-policies-for-site-closure-and-deletion-a8280d82-27fd-48c5-9adf-8a5431208ba5) (kun sletning)

- [Politikker for administration af oplysninger](intro-to-info-mgmt-policies.md) (kun sletning)

Hvis du har konfigureret SharePoint websteder for politikker for indholdstyper eller politikker for administration af oplysninger for at bevare indhold for en liste eller et bibliotek, ignoreres disse politikker, mens en opbevaringspolitik er i kraft.

## <a name="related-information"></a>Relaterede oplysninger

- [SharePoint onlinegrænser](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
- [Grænser og specifikationer for Microsoft Teams](/microsoftteams/limits-specifications-teams) 
- [Ressourcer, der kan hjælpe dig med at opfylde lovmæssige krav til administration af datalivscyklus og datastyring](retention-regulatory-requirements.md)

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Se [Kom i gang med administration af datalivscyklus](get-started-with-data-lifecycle-management.md). Denne artikel indeholder oplysninger om abonnementer, tilladelser og links til komplette konfigurationsvejledninger til opbevaringsscenarier.
