---
title: Undersøg og afhjælp underretninger om kommunikationsoverholdelse
description: Undersøg og afhjælp beskeder om kommunikation med overholdelse af angivne standarder i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 7f1afe62dcb7dabf55b48985354653b9418d0561
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971621"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Undersøg og afhjælp underretninger om kommunikationsoverholdelse

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du har konfigureret politikkerne for overholdelse af angivne standarder for kommunikation, modtager du beskeder på Microsoft Purview-overholdelsesportalen for meddelelsesproblemer, der opfylder dine politikbetingelser. Følg vejledningen i arbejdsprocessen her for at undersøge og løse problemer med beskeder.

## <a name="investigate-alerts"></a>Undersøg beskeder

Det første trin til at undersøge problemer, der er registreret af dine politikker, er at gennemse beskeder om kommunikation med overholdelse af angivne standarder på Microsoft Purview-overholdelsesportalen. Der er flere områder i løsningsområdet til kommunikation med overholdelse af angivne standarder, der kan hjælpe dig med hurtigt at undersøge beskeder, afhængigt af hvordan du foretrækker at få vist gruppering af beskeder:

- **Siden Politik for kommunikation med overholdelse af regler og standarder**: Når du logger på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365 organisation, skal du vælge **Meddelelsesoverholdelse** for at få vist siden **Politik** for kommunikationoverholdelse. På denne side vises politikker for overholdelse af angivne standarder for kommunikation, der er konfigureret for din Microsoft 365 organisation, og links til anbefalede politikskabeloner. Hver politik på listen indeholder antallet af beskeder, der skal gennemses, antallet af eskalerede og løste elementer, status for politikken og dato og klokkeslæt for den sidste politikscanning. Når du vælger en politik, vises alle ventende beskeder om matches til politikken, vælg en bestemt besked for at starte siden med politikoplysninger og for at starte afhjælpningshandlinger.
- **Beskeder**: Naviger til **Overholdelse af** **kommunikationAlerts** >  for at få vist de sidste 30 dages beskeder grupperet efter politikforekomster. Denne visning giver dig mulighed for hurtigt at se, hvilke kommunikationspolitikker der genererer de fleste beskeder sorteret efter alvorsgrad. Hvis du vil starte afhjælpningshandlinger, skal du vælge den politik, der er knyttet til beskeden, for at starte siden **Politikoplysninger** . På siden **Politikoplysninger** kan du gennemse en oversigt over aktiviteterne på siden **Oversigt** , gennemse og reagere på beskeder på siden **Ventende** eller gennemse oversigten over lukkede beskeder på siden **Løst** .
- **Rapporter**: Naviger til **Kommunikation med overholdelse af angivne standarderRapporter** >  for at få vist **widgets** til rapporten om overholdelse af kommunikation. Hver widget indeholder en oversigt over aktiviteter og status for overholdelse af angivne standarder for kommunikation, herunder adgang til dybere indsigt i politikforekomster og afhjælpningshandlinger.

### <a name="using-filters"></a>Brug af filtre

Det næste trin er at sortere meddelelserne, så det er nemmere for dig at undersøge beskeder. Fra siden **Politikoplysninger** understøtter overholdelse af angivne standarder for kommunikation filtrering på flere niveauer for flere meddelelsesfelter, så du hurtigt kan undersøge og gennemse meddelelser med politikforekomster. Filtrering er tilgængelig for ventende og løste elementer for hver konfigureret politik. Du kan konfigurere filterforespørgsler for en politik eller konfigurere og gemme brugerdefinerede filterforespørgsler og standardfilterforespørgsler til brug i hver enkelt politik. Når du har konfigureret felter for et filter, kan du se de filterfelter, der vises øverst i beskedmeddelelseskøen, som du kan konfigurere for bestemte filterværdier.

For datofilteret er dato og klokkeslæt for hændelser angivet i UTC (Coordinated Universal Time). Når meddelelser filtreres efter visninger, bestemmer den anmodende brugers lokale dato/klokkeslæt resultaterne baseret på konverteringen af brugerens lokale dato/klokkeslæt til UTC. Hvis en bruger i USA f.eks. PDT (Pacific Daylight Time) filtrerer en rapport fra 30-08-2021 til 31-08-2021 kl. 00:00, indeholder rapporten meddelelser fra 30-08-2021 07:00 UTC til 8/31/2021 07:00 UTC. Hvis den samme bruger var i U.S. Eastern Daylight Time (EDT), da der filtreres kl. 00:00, indeholder rapporten meddelelser fra 30-08-2021 04:00 UTC til 31-08-2021 04:00 UTC.

#### <a name="filter-details"></a>Filterdetaljer

Filtre for kommunikation med overholdelse af angivne standarder giver dig mulighed for at filtrere og sortere beskeder med henblik på hurtigere undersøgelses- og afhjælpningshandlinger. Filtrering er tilgængelig under fanerne **Ventende** og **Løst** for hver politik. Hvis du vil gemme et filter eller et filter, der er angivet som en gemt filterforespørgsel, skal en eller flere værdier konfigureres som filtervalg.

I følgende tabel beskrives filterdetaljer:

|**Filter**|**Detaljer**|
|:-----|:-----|
| **Dato** | Den dato, hvor meddelelsen blev sendt eller modtaget af en bruger i din organisation. Hvis du vil filtrere efter en enkelt dag, skal du vælge et datointerval, der starter med den dag, du vil have resultater for, og slutter med den følgende dag. Hvis du f.eks. vil filtrere resultaterne for 2020/9/2020, skal du vælge et filterdatointerval på 20-09-21-2020.|
| **Filklasse** | Meddelelsens klasse baseret på meddelelsestypen, enten *meddelelse* eller *vedhæftet fil*. |
| **Har vedhæftet fil** | Tilstedeværelsen af den vedhæftede fil i meddelelsen. |
| **Elementklasse** | Kilden til meddelelsen baseret på meddelelsestypen, mail, Microsoft Team-chat, Bloomberg osv. Du kan få flere oplysninger om almindelige elementtyper og meddelelsesklasser under [Elementtyper og Meddelelsesklasser](/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Modtagerdomæner** | Det domæne, som meddelelsen blev sendt til. Dette domæne er normalt dit Microsoft 365 abonnementsdomæne som standard. |
| **Modtager** | Den bruger, som meddelelsen blev sendt til. |
| **Afsender** | Den person, der sendte meddelelsen. |
| **Afsenderdomæne** | Det domæne, der sendte meddelelsen. |
| **Størrelse** | Meddelelsens størrelse i KB. |
| **Emne/titel** | Meddelelsens emne eller chattitel. |
| **Tags** | De mærker, der er tildelt til en meddelelse, enten *tvivlsomme*, *kompatible* eller *ikke-kompatible*. |
| **Sprog** | Det registrerede tekstsprog i meddelelsen. Meddelelsen klassificeres i henhold til sproget i størstedelen af meddelelsesteksten. For en meddelelse, der indeholder både tysk og italiensk tekst, men størstedelen af teksten er tysk, klassificeres meddelelsen som tysk (DE). Følgende sprog understøttes: kinesisk (forenklet – ZH), engelsk (EN), fransk (FR), tysk (DE), italiensk (IT), japansk (JP), portugisisk (PT) og spansk (ES). Hvis du f.eks. vil filtrere meddelelser, der er klassificeret som tysk og italiensk, skal du angive 'DE,IT' (de tocifrede sprogkoder) i søgefeltet Sprogfilter. Hvis du vil have vist den registrerede sprogklassificering for en meddelelse, skal du vælge en meddelelse, vælge Vis meddelelsesoplysninger og rulle til feltet EmailDetectedLanguage. |
| **Eskaleret til** | Brugernavnet på den person, der er inkluderet som en del af en eskaleringshandling for meddelelser. |
| **Klassificeringer** | Navnet på indbyggede og brugerdefinerede klassificeringer, der gælder for meddelelsen. Nogle eksempler omfatter *målrettet chikane*, *bandeord*, *trussel* m.m.

#### <a name="to-configure-a-filter"></a>Sådan konfigurerer du et filter

1. Log på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365 organisation.

2. På Microsoft Purview-overholdelsesportalen skal du gå til **Kommunikation med overholdelse**.

3. Vælg fanen **Politikker,** og vælg derefter en politik til undersøgelse. Dobbeltklik for at åbne siden **Politik** .

4. På siden **Politik** skal du vælge enten fanen **Ventende** eller **Løst** for at få vist elementerne til filtrering.

5. Vælg kontrolelementet **Filtre** for at åbne siden **Filtre** med detaljer.

6. Markér et eller flere afkrydsningsfelter for at aktivere filtre for disse beskeder. Du kan vælge mellem mange filtre, herunder *Dato*, *Afsender*, *Emne/Titel*, *Klassificeringer*, *Sprog* og meget mere.

7. Hvis du vil gemme det valgte filter som standardfilter, skal du vælge **Gem som standard**. Hvis du vil bruge dette filter som et gemt filter, skal du vælge **Udført**.

8. Hvis du vil gemme de valgte filtre som en filterforespørgsel, skal du vælge **Gem forespørgselskontrolelementet** , når du har konfigureret mindst én filterværdi. Angiv et navn til filterforespørgslen, og vælg **Gem**. Dette filter er kun tilgængeligt til brug for denne politik og er angivet i afsnittet **Gemte filterforespørgsler** på siden **med oplysninger om filtre** .

    ![Kontrolelementer til filtrering af kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Brug af nær- og nøjagtig dubletanalyse

Politikker for kommunikation med overholdelse af angivne standarder scanner og forbehandler automatisk dubletter af meddelelser nær og nøjagtigt uden yderligere konfigurationstrin. Denne visning giver dig mulighed for hurtigt at reagere på lignende meddelelser én for én eller som en gruppe, hvilket reducerer byrden med undersøgelse af meddelelser for korrekturlæsere. Når der registreres dubletter, vises **kontrolelementerne Near Duplicates** og/eller **Exact Duplicates** på værktøjslinjen til afhjælpningshandling. Denne visning er ikke tilgængelig, hvis der ikke findes nær eller nøjagtige dubletter.

#### <a name="to-remediate-duplicates"></a>Sådan afhjælpes dubletter

1. Log på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365 organisation.

2. På Microsoft Purview-overholdelsesportalen skal du gå til **Kommunikation med overholdelse**.

3. Vælg fanen **Politikker,** og vælg derefter en politik til undersøgelse. Dobbeltklik for at åbne siden **Politik** .

4. På siden **Politik** skal du vælge enten fanen **Ventende** eller **Løst** for at få vist dublerede meddelelser.

5. Vælg **kontrolelementerne Nær dubletter** eller **Nøjagtige dubletter** for at åbne siden med oplysninger om dubletter.

6. Vælg en eller flere meddelelser til afhjælpningshandlingskontrolelementer for disse meddelelser.

7. Vælg **Løs**, **Giv besked**, **Eskaler** eller **Hent** for at anvende handlingen på de valgte dubletmeddelelser som standardfilter.

8. Vælg **Luk** , når du har fuldført afhjælpningshandlingerne på meddelelserne.

    ![Kontrolelementer til nøjagtig overholdelse af kommunikationsoverholdelse dubletter.](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Afhjælp beskeder

Uanset hvor du begynder at gennemse beskeder eller den filtrering, du konfigurerer, er det næste trin at udføre en handling for at afhjælpe beskeden. Start afhjælpningen af dine beskeder ved hjælp af følgende arbejdsproces på siderne **Politik** eller **Beskeder** .

### <a name="step-1-examine-the-message-basics"></a>Trin 1: Undersøg de grundlæggende oplysninger om meddelelsen

 Nogle gange er det tydeligt fra kilden eller emnet, at en meddelelse kan afhjælpes med det samme. Det kan være, at meddelelsen er falsk eller forkert matchet med en politik, og at den skal løses som forkert klassificeret. Vælg kontrolelementet **Rapport som forkert klassificerede** for at dele forkert klassificeret indhold med Microsoft, løs straks beskeden, og fjern den fra den ventende beskedkø. Fra kilde- eller afsenderoplysningerne ved du muligvis allerede, hvordan meddelelsen skal distribueres eller håndteres i disse tilfælde. Overvej at bruge kontrolelementerne **Mærke som** eller **Eskaler** til at tildele en kode til relevante meddelelser eller til at sende meddelelser til en udpeget korrekturlæser.

![Afhjælpningskontroller for kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>Trin 2: Undersøg oplysningerne i meddelelsen

Når du har gennemset de grundlæggende oplysninger om meddelelsen, er det tid til at åbne en meddelelse for at undersøge detaljerne og fastlægge yderligere afhjælpningshandlinger. Vælg en meddelelse for at få vist hele meddelelsens brevhoved og brødtekstoplysninger. Der findes flere forskellige indstillinger og visninger, som kan hjælpe dig med at bestemme den korrekte fremgangsmåde:

- **Vedhæftede filer**: Med denne indstilling kan du undersøge moderne vedhæftede filer, der opfylder politikbetingelserne. Moderne indhold i vedhæftede filer udtrækkes som tekst og kan ses på dashboardet Ventende beskeder for en politik. Du kan få flere oplysninger i [referencen til funktionen til kommunikation med overholdelse af angivne standarder](/microsoft-365/compliance/communication-compliance-channels).
- **Kilde**: Denne visning er den standardmeddelelsesvisning, der ofte ses på de fleste webbaserede meddelelsesplatforme. Oplysningerne i sidehovedet er formateret i normal stil, og meddelelsesteksten understøtter indpakkede grafikfiler og tekstombrudt tekst. Hvis [optisk tegngenkendelse (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) er aktiveret for politikken, vises billeder, der indeholder trykt eller håndskrevet tekst, som svarer til politikbetingede betingelser, som et underordnet element for den tilknyttede meddelelse i denne visning.
- **Almindelig tekst**: Tekstvisning viser en tekstvisning med linjenummerering af meddelelsen og inkluderer fremhævning af nøgleord i meddelelser og vedhæftede filer for følsomme ord eller nøgleord, der matcher i den tilknyttede politik for kommunikation med overholdelse af angivne standarder. Fremhævning af nøgleord kan hjælpe dig med hurtigt at scanne lange meddelelser og vedhæftede filer for det interessante område. I nogle tilfælde kan fremhævet tekst kun være i vedhæftede filer for meddelelser, der opfylder politikbetingelserne. Fremhævning af nøgleord understøttes ikke for ord, der identificeres af indbyggede klassificeringer, der er tildelt til en politik. Integrerede filer vises ikke, og linjenummereringen af denne visning er nyttig til at referere til relevante oplysninger blandt flere korrekturlæsere.
- **Samtale (prøveversion)**: Denne visning er tilgængelig for Microsoft Teams chatbeskeder og viser op til fem meddelelser før og efter en besked for at hjælpe korrekturlæsere med at få vist aktiviteten i samtalekonteksten. Denne kontekst hjælper korrekturlæsere med hurtigt at evaluere meddelelser og træffe mere velunderbyggede beslutninger om løsning af meddelelser. Meddelelsestilføjelser i realtid til samtaler vises, herunder alle indbyggede billeder, emojis og klistermærker, der er tilgængelige i Teams. Vedhæftede filer i billeder eller tekstfiler i meddelelser vises ikke. Meddelelser vises automatisk for meddelelser, der er blevet redigeret, eller for meddelelser, der er blevet slettet fra samtalevinduet. Når en meddelelse er løst, bevares de tilknyttede samtalemeddelelser ikke sammen med den løste meddelelse. Samtalemeddelelser er tilgængelige i op til 60 dage, efter at beskedmeddelelsen er identificeret.
- **Brugerhistorik**: I visningen Brugerhistorik vises alle andre beskeder, der genereres af en politik for kommunikation med overholdelse af angivne standarder for den bruger, der sender meddelelsen.
- **Mønster registreret meddelelse**: Mange chikane- og mobninghandlinger over tid og involverer gentagne forekomster af den samme funktionsmåde af en bruger. Det *registrerede mønster* vises i oplysningerne om beskeden og gør opmærksom på beskeden. Registrering af mønstre sker pr. politik og evaluerer funktionsmåden i løbet af de sidste 30 dage, når mindst to meddelelser sendes til den samme modtager af en afsender. Efterforskere og validatorer kan bruge denne meddelelse til at identificere gentaget funktionsmåde for at evaluere beskeden efter behov.
- **Oversættelse**: Denne visning konverterer automatisk beskedtekst til det sprog, der er konfigureret i indstillingen *Vist sprog* i abonnementet Microsoft 365 for hver korrekturlæser. *Oversættelsesvisningen* hjælper med at udvide undersøgelsessupporten til organisationer med flersprogede brugere og fjerner behovet for yderligere oversættelsestjenester uden for korrekturprocessen for kommunikation med overholdelse af angivne standarder. Ved hjælp af *Microsoft-oversættelsestjenester kan visningen Oversættelse* slås til og fra efter behov og understøtter en lang række sprog. Du kan se en komplet liste over understøttede sprog [under Microsoft Oversætter Sprog](https://www.microsoft.com/translator/business/languages/). Sprog, der er angivet på *listen Oversætter sprog*, understøttes i *oversættelsesvisning*.

### <a name="step-3-decide-on-a-remediation-action"></a>Trin 3: Beslut en afhjælpningshandling

Nu, hvor du har gennemset oplysningerne i meddelelsen for beskeden, kan du vælge flere afhjælpningshandlinger:

- **Løs**: Hvis du vælger kontrolelementet **Løs** med det samme, fjernes meddelelsen fra køen **Ventende beskeder** , og der kan ikke udføres yderligere handlinger på meddelelsen. Når du vælger **Løs**, har du stort set lukket beskeden uden yderligere klassificering. Alle løste meddelelser vises under fanen **Løst** .
- **Rapportér som fejlklassificeret**: Du kan altid løse en meddelelse som fejlklassificeret på et hvilket som helst tidspunkt under arbejdsprocessen til gennemsyn af meddelelser. Forkert klassificerede angiver, at beskeden ikke kunne handles på, eller at beskeden blev genereret forkert af beskedprocessen og eventuelle klassificeringer, der kan oplæres. Løsning af elementet som forkert klassificerede sender meddelelsesindhold, vedhæftede filer og meddelelsens emne (herunder metadata) til Microsoft for at hjælpe med at forbedre klassificeringer, der kan oplæres. Data, der sendes til Microsoft, indeholder ikke oplysninger, der kan identificere eller bruges til at identificere brugere i din organisation. Der kan ikke udføres yderligere handlinger på meddelelsen, og alle forkert klassificerede meddelelser vises under fanen **Løst** .
- **Power Automate (prøveversion)**: Brug et Power Automate flow til at automatisere behandlingsopgaver for en besked. Som standard omfatter overholdelse af kommunikation *beskedstyringen, når en bruger har en skabelon til beskedflow for kommunikation med overholdelse af angivne standarder* , som korrekturlæsere kan bruge til at automatisere meddelelsesprocessen for brugere med meddelelsesbeskeder. Du kan få flere oplysninger om oprettelse og administration af Power Automate flow i forbindelse med overholdelse af angivne standarder for kommunikation i **afsnittet Trin 5: Overvej Power Automate flow** i denne artikel.
- **Tag som**: Mærk meddelelsen som *kompatibel*, *ikke-kompatibel* eller så *tvivlsom* , som den er relateret til politikker og standarder for din organisation. Tilføjelse af mærker og mærkningskommentarer hjælper dig med at filtrere politikbeskeder for eskalering eller som en del af andre interne korrekturprocesser. Når mærkningen er fuldført, kan du også vælge at løse problemet med meddelelsen for at flytte den ud af køen til ventende gennemsyn.
- **Notify**: Du kan bruge kontrolelementet **Notify** til at tildele en brugerdefineret meddelelsesskabelon til beskeden og til at sende en advarsel til brugeren. Vælg den relevante meddelelsesskabelon, der er konfigureret i området **Indstillinger for kommunikation med overholdelse af angivne standarder** , og vælg **Send** for at sende en påmindelse til den bruger, der sendte meddelelsen, og for at løse problemet.
- **Eskaler**: Ved hjælp af kontrolelementet **Eskaler** kan du vælge, hvem i organisationen der skal gennemse meddelelsen. Vælg på en liste over korrekturlæsere, der er konfigureret i politikken for kommunikation med overholdelse af angivne standarder, for at sende en mail med anmodning om yderligere gennemgang af meddelelsesbeskeden. Den valgte korrekturlæser kan bruge et link i mailmeddelelsen til at gå direkte til elementer, der eskaleres til dem til gennemsyn.
- **Eskaler til undersøgelse**: Ved hjælp af kontrolelementet **Eskaler til undersøgelse** kan du oprette en ny [eDiscovery-sag (Premium)](overview-ediscovery-20.md) for en enkelt eller flere meddelelser. Du skal angive et navn og noter til den nye sag, og den bruger, der har sendt den meddelelse, der stemmer overens med politikken, tildeles automatisk som sagsvagt. Du behøver ikke yderligere tilladelser til at administrere sagen. Oprettelse af en sag løser ikke eller opretter ikke et nyt mærke for meddelelsen. Du kan vælge i alt 100 meddelelser, når du opretter en eDiscovery-sag (Premium) under afhjælpningsprocessen. Meddelelser i alle kommunikationskanaler, der overvåges af overholdelse af angivne standarder for kommunikation, understøttes. Du kan f.eks. vælge 50 Microsoft Teams chats, 25 Exchange Online mails og 25 Yammer meddelelser, når du åbner en ny eDiscovery-sag (Premium) for en bruger.
- **Fjern meddelelse i Teams**: Ved hjælp af kontrolelementet **Fjern meddelelse i Teams** kan du blokere upassende meddelelser og indhold, der er identificeret i beskeder, fra Microsoft Teams kanaler og 1:1 og gruppechats. Fjernede meddelelser og indhold erstattes af et politiktip, der forklarer, at den er blokeret, og den politik, der gælder for fjernelsen af den. Modtagerne får vist et link i politiktippen for at få mere at vide om den relevante politik og korrekturprocessen. Afsenderen modtager et politiktip til den blokerede meddelelse og det blokerede indhold, men kan gennemse oplysningerne om den blokerede meddelelse og det blokerede indhold for at se konteksten vedrørende fjernelsen.

    ![Fjern en meddelelse fra Microsoft Teams.](../media/communication-compliance-remove-teams-message.png)

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>Trin 4: Find ud af, om meddelelsesdetaljer skal arkiveres uden for kommunikation med overholdelse af angivne standarder

Meddelelsesdetaljer kan eksporteres eller downloades, hvis du har brug for at arkivere meddelelserne i en separat lagerløsning. Hvis du vælger kontrolelementet **Download,** føjes de markerede meddelelser automatisk til en .ZIP fil, der kan gemmes på et lager uden for Microsoft 365.

### <a name="step-5-consider-power-automate-flows"></a>Trin 5: Overvej Power Automate flow

[Microsoft Power Automate](/power-automate/getting-started) er en arbejdsprocestjeneste, der automatiserer handlinger på tværs af programmer og tjenester. Ved hjælp af flow fra skabeloner eller oprettet manuelt kan du automatisere almindelige opgaver, der er knyttet til disse programmer og tjenester. Når du aktiverer Power Automate flow for overholdelse af angivne standarder for kommunikation, kan du automatisere vigtige opgaver for beskeder og brugere. Du kan konfigurere Power Automate flow for at give ledere besked, når brugerne har beskeder om kommunikation med overholdelse af angivne standarder og andre programmer.

Kunder med Microsoft 365 abonnementer, der indeholder overholdelse af angivne standarder for kommunikation, behøver ikke yderligere Power Automate licenser for at bruge den anbefalede skabelon til standardoverholdelse af kommunikation Power Automate. Standardskabelonen kan tilpasses for at understøtte din organisation og dække kernescenarier for kommunikation med overholdelse af angivne standarder. Hvis du vælger at bruge Premium Power Automate-funktioner i disse skabeloner, oprette en brugerdefineret skabelon ved hjælp af Microsoft Purview-connectoren eller bruge Power Automate skabeloner til andre overholdelsesområder i Microsoft Purview, skal du muligvis bruge yderligere Power Automate licenser.

> [!IMPORTANT]
> Modtager du en meddelelse om yderligere licensvalidering, når du tester Power Automate flow? Din organisation har muligvis endnu ikke modtaget tjenesteopdateringer til denne prøveversionsfunktion. Opdateringer udrulles, og alle organisationer med Microsoft 365 abonnementer, der omfatter overholdelse af kommunikation, skal have licensunderstøttelse for flow, der er oprettet ud fra de anbefalede Power Automate skabeloner senest den 30. oktober 2020.

![Overholdelse af angivne standarder for kommunikation Power Automate.](../media/communication-compliance-power-automate.png)

Følgende Power Automate skabelon leveres til kunder for at understøtte procesautomatisering for beskeder om kommunikation med overholdelse af angivne standarder:

- **Giv administratoren besked, når en bruger har en besked om overholdelse af angivne standarder for kommunikation**: Nogle organisationer skal muligvis have en øjeblikkelig meddelelse om administration, når en bruger har en besked om kommunikation med overholdelse af angivne standarder. Når dette flow er konfigureret og valgt, modtager sagsbrugerens leder en mail med følgende oplysninger om alle beskeder:
  - Gældende politik for beskeden
  - Dato/klokkeslæt for beskeden
  - Alvorsgrad for beskeden

#### <a name="create-a-power-automate-flow"></a>Opret et Power Automate flow

Hvis du vil oprette et Power Automate flow fra en anbefalet standardskabelon, skal du bruge indstillingen **Administrer Power Automate flow** fra kontrolelementet **Automate**, når du arbejder direkte i en besked. Hvis du vil oprette et Power Automate flow med **Administrer Power Automate flow**, skal du være medlem af mindst én rollegruppe for kommunikation med overholdelse af angivne standarder.

Udfør følgende trin for at oprette et Power Automate flow fra en standardskabelon:

1. På [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) skal du gå til **Kommunikation med overholdelse** >  **politikker** og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen **Ventende** i politikken, og vælg en ventende besked.
3. Vælg **Power Automate** i menuen med beskedhandlinger.
4. På siden **Power Automate** skal du vælge en standardskabelon i afsnittet **Skabeloner til kommunikation med overholdelse af angivne standarder, som du kan synes godt om** på siden.
5. Flowet viser de integrerede forbindelser, der er nødvendige for flowet, og vises, hvis forbindelsesstatusserne er tilgængelige. Opdater eventuelle forbindelser, der ikke vises som tilgængelige, hvis det er nødvendigt. Vælg **Fortsæt**.
6. De anbefalede flow er som standard forudkonfigureret med den anbefalede kommunikationsoverholdelse og Microsoft 365 tjenestedatafelter, der kræves for at fuldføre den tildelte opgave for flowet. Tilpas om nødvendigt flowkomponenterne ved hjælp af kontrolelementet **Vis avancerede indstillinger** og konfiguration af de tilgængelige egenskaber for flowkomponenten.
7. Hvis det er nødvendigt, kan du føje yderligere trin til flowet ved at vælge knappen **Nyt trin** . I de fleste tilfælde bør denne ændring ikke være nødvendig for de anbefalede standardskabeloner.
8. Vælg **Gem kladde** for at gemme flowet til yderligere konfiguration senere, eller vælg **Gem** for at fuldføre konfigurationen af flowet.
9. Vælg **Luk** for at vende tilbage til siden Power Automate flow. Den nye skabelon vises som et flow under fanen **Mine flow** og er automatisk tilgængelig fra kontrolelementet Power Automate for den bruger, der oprettede flowet, når der arbejdes med beskeder om kommunikation med overholdelse af angivne standarder.

#### <a name="share-a-power-automate-flow"></a>Del et Power Automate flow

Som standard er Power Automate flow, der er oprettet af en bruger, kun tilgængelige for den pågældende bruger. Hvis andre brugere af overholdelse af angivne standarder for kommunikation skal have adgang til og bruge et flow, skal flowet deles af flowopretteren. Hvis du vil dele et flow, skal du bruge kontrolelementet **Power Automate**, når du arbejder direkte i en besked.

Hvis du vil dele et Power Automate flow, skal du være medlem af mindst én rollegruppe for kommunikation med overholdelse af angivne standarder.
Fuldfør følgende trin for at dele et Power Automate flow:

1. På [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) skal du gå til **Kommunikation med overholdelse** >  **politikker** og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen **Ventende** i politikken, og vælg en ventende besked.
3. Vælg **Power Automate** i menuen med beskedhandlinger.
4. På siden **Power Automate flow** skal du vælge fanen **Mine flows** eller **Teamflows**.
5. Vælg det flow, der skal deles, og vælg derefter **Del** i menuen med flowindstillinger.
6. Angiv navnet på den bruger eller gruppe, du vil tilføje som ejer af flowet, på siden til deling af flowet.
7. I dialogboksen **Forbindelse brugt** skal du vælge **OK** for at bekræfte, at den tilføjede bruger eller gruppe har fuld adgang til flowet.

#### <a name="edit-a-power-automate-flow"></a>Rediger et Power Automate flow

Hvis du har brug for at redigere et flow, skal du bruge kontrolelementet **Power Automate**, når du arbejder direkte i en besked. Hvis du vil redigere et Power Automate flow, skal du være medlem af mindst én rollegruppe for kommunikation med overholdelse af angivne standarder.

Udfør følgende trin for at redigere et Power Automate flow:

1. På [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) skal du gå til **Kommunikation med overholdelse** >  **politikker** og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen **Ventende** i politikken, og vælg en ventende besked.
3. Vælg **Power Automate** i menuen med beskedhandlinger.
4. Vælg flow, der skal redigeres, på siden **Power Automate flow**. Vælg **Rediger** i flowkontrolmenuen.
5. Vælg **ellipsen** >  **Indstillinger** for at ændre en indstilling for en flowkomponent eller **ellipsenSlet** >  for at slette en flowkomponent.
6. Vælg **Gem** og derefter **Luk** for at fuldføre redigeringen af flowet.

#### <a name="delete-a-power-automate-flow"></a>Slet et Power Automate flow

Hvis du har brug for at slette et flow, skal du bruge kontrolelementet **Power Automate**, når du arbejder direkte i en besked. Hvis du vil slette et Power Automate flow, skal du være medlem af mindst én rollegruppe for kommunikation med overholdelse af angivne standarder.

Fuldfør følgende trin for at slette et Power Automate flow:

1. På [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) skal du gå til **Kommunikation med overholdelse** >  **politikker** og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen **Ventende** i politikken, og vælg en ventende besked.
3. Vælg **Power Automate** i menuen med beskedhandlinger.
4. Vælg flow, der skal slettes, på siden **Power Automate flow**. Vælg **Slet** i menuen for flowkontrolelementet.
5. Vælg **Slet** i bekræftelsesdialogboksen for sletning for at fjerne flowet, eller vælg **Annuller** for at afslutte sletningen.

### <a name="step-6-consider-creating-notice-templates"></a>Trin 6: Overvej at oprette meddelelsesskabeloner

Du kan oprette skabeloner til meddelelser, hvis du vil sende brugerne en påmindelse via mail for politikforekomster som en del af processen til problemløsning. Meddelelser kan kun sendes til den brugermailadresse, der er knyttet til politikmatch, som genererede den specifikke besked om afhjælpning. Når du vælger en meddelelsesskabelon, der skal anvendes på en politikovertrædelse som en del af afhjælpningsarbejdsprocessen, kan du vælge at acceptere de feltværdier, der er defineret i skabelonen, eller overskrive felterne efter behov.

Meddelelsers skabeloner er brugerdefinerede mailskabeloner, hvor du kan definere følgende meddelelsesfelter i området **Indstillinger for kommunikation med overholdelse af angivne standarder** :

|**Feltet**|**Påkrævet**| **Detaljer** |
|:-----|:-----|:-----|
|**Skabelonnavn** | Ja | Brugervenligt navn på den meddelelsesskabelon, du vælger i meddelelsesarbejdsprocessen under afhjælpning, understøtter teksttegn. |
| **Afsenderadresse** | Ja | Adressen på en eller flere brugere eller grupper, der sender meddelelsen til brugeren med et politikmatch, som er valgt i Active Directory for dit abonnement. |
| **CC- og BCC-adresser** | Nej | Valgfrie brugere eller grupper, der skal have besked om politikmatch, som er valgt i Active Directory for dit abonnement. |
| **Emne** | Ja | Oplysninger, der vises i meddelelsens emnelinje, understøtter teksttegn. |
| **Meddelelsestekst** | Ja | Oplysninger, der vises i meddelelsens brødtekst, understøtter tekst eller HTML-værdier. |

### <a name="html-for-notices"></a>HTML til meddelelser

Hvis du vil oprette mere end en simpel tekstbaseret mail til meddelelser, kan du oprette en mere detaljeret meddelelse ved hjælp af HTML i meddelelsesbrødtekstfeltet i en meddelelsesskabelon. I følgende eksempel vises meddelelsesbrødtekstformatet for en grundlæggende SKABELON til HTML-baseret mailmeddelelse:

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

> [!NOTE]
> Html href-attributimplementering i skabelonerne til meddelelse om overholdelse af angivne standarder understøtter i øjeblikket kun enkelte anførselstegn i stedet for dobbelte anførselstegn for URL-referencer.

## <a name="unresolve-messages-preview"></a>Uløste meddelelser (prøveversion)

Når meddelelser er løst, fjernes de fra fanevisningen **Ventende** og vises i fanevisningen **Løst** . Undersøgelses- og afhjælpningshandlinger er ikke tilgængelige for meddelelser i visningen *Løst* . Der kan dog være tilfælde, hvor du skal udføre yderligere handlinger på en meddelelse, der blev løst ved en fejl, eller som skal undersøges yderligere efter den første løsning. Du kan bruge den uløste kommandofunktion til at flytte en eller flere meddelelser fra visningen *Løst* tilbage til visningen *Ventende* .

Fuldfør følgende trin for at løse uløste meddelelser:

1. Log på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en bruger, der er tildelt *rollegrupperne Communication Compliance Analyst* eller *Communication Compliance Investigator* i din Microsoft 365 organisation.
2. På Microsoft Purview-overholdelsesportalen skal du gå til **Kommunikation med overholdelse**.
3. Vælg fanen **Politikker,** og vælg derefter en politik, der indeholder den løste besked, og dobbeltklik for at åbne siden **Politik** .
4. Vælg fanen **Løst** på siden **Politik**.
5. Under fanen **Løst** skal du vælge en eller flere meddelelser for at flytte tilbage til *Ventende*.
6. Vælg **Uløst på kommandolinjen**.
7. I ruden **Uløste elementer** skal du tilføje eventuelle kommentarer, der gælder for den uløste handling, og vælge **Gem** for at flytte elementet tilbage til *Ventende*.
8. Vælg fanen **Afventer** for at kontrollere, at de valgte elementer vises.
