---
title: Undersøg og afhjulpet beskeder om kommunikationsoverholdelse
description: Undersøg og afhjulpet beskeder om kommunikationsoverholdelse Microsoft 365.
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
ms.openlocfilehash: c44d710b4067ec12b0234c88e02d2d89729819a6
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63587331"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Undersøg og afhjulpet beskeder om kommunikationsoverholdelse

Når du har konfigureret dine politikker for overholdelse af regler og standarder i kommunikation, begynder du at modtage beskeder i Microsoft 365 Overholdelsescenter om meddelelsesproblemer, der opfylder dine politikbetingelser. Følg arbejdsprocesinstruktionerne her for at undersøge og afhjælpe problemer med beskeder.

## <a name="investigate-alerts"></a>Undersøg beskeder

Det første trin til at undersøge problemer, der er registreret af dine politikker, er at gennemse beskeder om overholdelse af regler og standarder i Microsoft 365 Overholdelsescenter. Der er flere områder i området til løsning til overholdelse af kommunikation, som kan hjælpe dig med hurtigt at undersøge vigtige beskeder, afhængigt af hvordan du foretrækker at få vist gruppering af beskeder:

- Siden Politik for **overholdelse af** kommunikation: Når du logger på [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, skal du vælge  Kommunikationsoverholdelse for at få vist siden politik for overholdelse **af kommunikation.** Denne side viser politikker for overholdelse af kommunikation, der er konfigureret for Microsoft 365 organisationen, samt links til anbefalede politikskabeloner. Hver angivet politik omfatter antallet af vigtige beskeder, der skal gennemses, antallet af eskalerede og løste elementer, politikkens status og dato og klokkeslæt for den seneste politiks scanning. Når du vælger en politik, vises alle ventende beskeder om match til politikken, vælg en bestemt besked for at starte siden med politikdetaljer og for at starte afhjælpningshandlinger.
- **Beskeder**: Gå til Kommunikationsoverholdelsesoverholdelsesmeddelelse  >  for at få vist de seneste 30 dages beskeder, der er grupperet efter politikoverensstemmelse. Denne visning giver dig mulighed for hurtigt at se, hvilke politikker for overholdelse af kommunikation, der genererer de fleste beskeder sorteret efter alvorsgrad. For at starte afhjælpningshandlinger skal du vælge den politik, der er knyttet til beskeden, for at **starte siden Med politikoplysninger** . Fra siden **Politikoplysninger** kan du gennemse en oversigt over aktiviteterne på siden Oversigt, gennemse  og reagere på påmindelsesmeddelelser på siden Afventer eller  gennemse historikken for lukkede beskeder på siden Løst.
- **Rapporter**: Naviger til **Communication** **complianceReports** >  for at vise widgets til rapportering om overholdelse af kommunikation. Hver widget giver et overblik over aktiviteter og statusser for overholdelse af kommunikation, herunder adgang til dybere indsigt i match til politikker og afhjælpningshandlinger.

### <a name="using-filters"></a>Brug af filtre

Det næste trin er at sortere meddelelserne, så det er nemmere for dig at undersøge vigtige beskeder. På siden **Politikdetaljer understøtter** kommunikationsoverholdelse filtrering på flere niveauer for flere meddelelsesfelter for at hjælpe dig med hurtigt at undersøge og gennemse meddelelser med politikoverensstemmelse. Filtrering er tilgængelig for ventende og løste elementer for hver konfigureret politik. Du kan konfigurere filterforespørgsler for en politik eller konfigurere og gemme brugerdefinerede forespørgsler og standardfilterforespørgsler til brug i hver bestemt politik. Når du har konfigureret felter for et filter, vises filterfelterne øverst i meddelelseskøen, som du kan konfigurere for bestemte filterværdier.

For datofilteret vises dato og klokkeslæt for begivenheder i UTC (Coordinated Universal Time). Ved filtrering af meddelelser for visninger bestemmer den anmodende brugers lokale dato/klokkeslæt resultaterne baseret på konverteringen af brugerens lokale dato/klokkeslæt til UTC. Hvis en bruger i AMERIKANSK PACIFIC Daylight Time (PDT) filtrerer en rapport fra 30-08-2021 til 31-08-2021 kl. 00:00, indeholder rapporten meddelelser fra 30-08-2021 07:00 UTC til 31-08-2021 07:00 UTC. Hvis den samme bruger var i det amerikanske Eastern Daylight Time (EDT), når der blev filtreret kl. 00:00, medtager rapporten meddelelser fra 30-08-2021 04:00 UTC til d. 31-08-2021 04:00 UTC.

#### <a name="filter-details"></a>Filterdetaljer

Filtre til overholdelse af kommunikation giver dig mulighed for at filtrere og sortere meddelelser, så du hurtigere kan undersøge og afhjælpe handlinger. Filtrering er tilgængelig på fanerne **Afventer** **og Løst** for hver politik. Hvis du vil gemme et filter eller et filtersæt som en gemt filterforespørgsel, skal en eller flere værdier konfigureres som filtervalg.

Følgende tabel beskriver filterdetaljer:

|**Filter**|**Detaljer**|
|:-----|:-----|
| **Dato** | Den dato, hvor meddelelsen blev sendt eller modtaget af en bruger i organisationen. Hvis du vil filtrere efter en enkelt dag, skal du vælge et datointerval, der starter med den dag, du vil have resultater for, og slutte med den følgende dag. Hvis du f.eks. vil filtrere resultaterne for 20-09-2020, skal du vælge et filterdatointerval på 20-09-2020-21-2020.|
| **Filklasse** | Klassen for meddelelsen baseret på meddelelsestypen, enten meddelelse *eller vedhæftet* *fil*. |
| **Har vedhæftet fil** | Den vedhæftede fils tilstedeværelse i meddelelsen. |
| **Elementklasse** | Kilden til meddelelsen baseret på meddelelsestypen, mail, Microsoft Team-chat, Bloomberg osv. Du kan finde flere oplysninger om almindelige elementtyper og meddelelsesklasser under [Elementtyper og Meddelelsesklasser](/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Modtagerdomæner** | Det domæne, som meddelelsen blev sendt til. Dette domæne er normalt dit Microsoft 365-abonnementsdomæne som standard. |
| **Modtager** | Den bruger, som meddelelsen blev sendt til. |
| **Afsender** | Den person, der har sendt meddelelsen. |
| **Afsenderdomæne** | Det domæne, der sendte meddelelsen. |
| **Størrelse** | Størrelsen på meddelelsen i KB. |
| **Emne/titel** | Meddelelsens emne eller chattitel. |
| **Mærker** | De mærker, der er tildelt en meddelelse, *enten Tvivlbar*, *Kompatibel* eller *Ikke-kompatibel*. |
| **Sprog** | Det registrerede sprog for teksten i meddelelsen. Meddelelsen er klassificeret efter sproget for størstedelen af meddelelsesteksten. Hvis en meddelelse f.eks. indeholder både tysk og italiensk tekst, men størstedelen af teksten er tysk, bliver meddelelsen klassificeret som tysk (DE). Følgende sprog understøttes: kinesisk (forenklet – ZH), engelsk (EN), fransk (FR), tysk (DE), italiensk (IT), japansk (JP), portugisisk (PT) og spansk (ES). Hvis du f.eks. vil filtrere meddelelser, der er klassificeret som tysk og italiensk, skal du skrive "DE,IT" (de tocifrede sprogkoder) i søgefeltet sprogfilter. For at få vist det registrerede sprogklassifikationen for en meddelelse skal du vælge en meddelelse, vælge Vis meddelelsesdetaljer og rulle til feltet EmailDetectedLanguage. |
| **Eskaleret til** | Brugernavnet på den person, der er medtaget som en del af en meddelelseseskaleringshandling. |
| **Klassificeringer** | Navnet på indbyggede og brugerdefinerede klassificeringer, der gælder for meddelelsen. Nogle eksempler kan være *Målrettet Chikane*, *Bandeord*, *Trussel* og meget mere.

#### <a name="to-configure-a-filter"></a>Sådan konfigurerer du et filter

1. Log på computeren [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) legitimationsoplysningerne til en administratorkonto i din Microsoft 365 organisation.

2. I Microsoft 365 Overholdelsescenter skal du gå til Overholdelse **af kommunikationsreglerne**.

3. Vælg fanen **Politikker** , og vælg derefter en undersøgelsespolitik, dobbeltklik for at åbne **siden** Politik.

4. På siden **Politik** skal du vælge fanen **Afventer** **eller Løst** for at få vist elementerne til filtrering.

5. Vælg **kontrolelementet** Filtre for at åbne **siden med oplysninger** om filtre.

6. Markér et eller flere afkrydsningsfelter for at aktivere filtre for disse beskeder. Du kan vælge mellem mange filtre, herunder *Dato*, *Afsender*, *Emne/Titel*, *Klassificeringer*, *Sprog* og meget mere.

7. Hvis du vil gemme det filter, der er valgt som standardfilter, skal du vælge **Gem som standard**. Hvis du vil bruge dette filter som et gemt filter, skal du vælge **Udført**.

8. Hvis du vil gemme de valgte filtre som en filterforespørgsel, skal du  vælge Gem forespørgselskontrolelementet, når du har konfigureret mindst én filterværdi. Angiv et navn til filterforespørgslen, og vælg **Gem**. Dette filter er kun tilgængeligt for denne politik og er angivet i sektionen Gemte **filterforespørgsler** på **siden Med filtre** .

    ![Detaljer om kontrolelementer i kommunikationsoverholdelsesfilteret.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Brug af nær og præcis analyse af dubletter

Politikker for overholdelse af kommunikation scanner og forudgrupperer automatisk nær og præcis meddelelsesdubletter uden yderligere konfigurationstrin. Denne visning giver dig mulighed for hurtigt at reagere på lignende meddelelser en-til-en eller som en gruppe, hvilket reducerer belastningen af meddelelsesundersøgelse for korrekturlæsere. Efterhånden som der **registreres** dubletter **,** vises kontrolelementerne Nær dubletter og/eller Nøjagtige dubletter på værktøjslinjen til afhjælpning. Denne visning er ikke tilgængelig, hvis der ikke blev fundet nær eller nøjagtige dubletter.

#### <a name="to-remediate-duplicates"></a>Sådan afhjælper du dubletter

1. Log på computeren [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) legitimationsoplysningerne til en administratorkonto i din Microsoft 365 organisation.

2. I Microsoft 365 Overholdelsescenter skal du gå til Overholdelse **af kommunikationsreglerne**.

3. Vælg fanen **Politikker** , og vælg derefter en undersøgelsespolitik, dobbeltklik for at åbne **siden** Politik.

4. På siden **Politik skal** du vælge fanen **Afventer eller** **Løst** for at få vist dublerede meddelelser.

5. Vælg **kontrolelementerne Nær dubletter** eller **Nøjagtige dubletter** for at åbne siden med oplysninger om dubletter.

6. Vælg en eller flere meddelelser for at afhjælpe handlingskontrolelementerne for disse meddelelser.

7. Vælg **Løs**, **Giv besked**, **Eskaler** eller **Download** for at anvende handlingen på de valgte duplikerede meddelelser som standardfilteret.

8. Vælg **Luk** , når du har fuldført afhjælpningshandlingerne for meddelelserne.

    ![Nøjagtige kontrolelementer til overholdelse af regler og standarder i kommunikation.](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Afhjælpe beskeder

Uanset hvor du begynder at gennemse beskeder eller den filtrering, du konfigurerer, er næste trin at gøre noget for at løse problemet. Start afhjælpningen af din besked ved hjælp af følgende arbejdsproces **på siderne** Politik **eller Vigtige** beskeder.

### <a name="step-1-examine-the-message-basics"></a>Trin 1: Undersøg meddelelsen grundlæggende

 Nogle gange er det tydeligt fra kilden eller emnet, at en meddelelse straks kan afhjælpes. Det kan være, at meddelelsen er fejlagtig eller fejlagtigt matchet med en politik, og den skal løses som fejlklassificeret. Vælg **kontrolelementet Rapportér som** fejlklassificeret for at dele fejlklassificeret indhold med Microsoft, løs straks beskeden, og fjern fra den ventende beskedkø. Fra kilde- eller afsenderoplysningerne ved du måske allerede, hvordan meddelelsen skal distribueres eller håndteres under disse omstændigheder. Overvej at bruge **kontrolelementerne Mærke som** **eller Eskaler** til at tildele et mærke til relevante meddelelser eller sende meddelelser til en bestemt korrekturlæser.

![Kontrolelementer til afhjælpning af overholdelse af kommunikation.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>Trin 2: Undersøg meddelelsesdetaljerne

Når du har gennemset meddelelsens grundlæggende oplysninger, er det tid til at åbne en meddelelse for at undersøge detaljerne og for at fastlægge yderligere afhjælpningshandlinger. Vælg en meddelelse for at få vist hele meddelelsens brevhoved og brødtekst. Der findes flere forskellige muligheder og visninger, der kan hjælpe dig med at beslutte den rette handling:

- **Vedhæftede** filer: Denne indstilling giver dig mulighed for at undersøge moderne vedhæftede filer, der opfylder politikbetingelserne. Indholdet af moderne vedhæftede filer udtrækkes som tekst og kan vises på dashboardet Ventende beskeder for en politik. Du kan finde flere oplysninger i Reference [til funktioner til overholdelse af kommunikation](/microsoft-365/compliance/communication-compliance-channels).
- **Kilde**: Denne visning er den almindelige meddelelsesvisning, der ofte ses på de fleste webbaserede meddelelsesplatforme. Oplysningerne i sidehovedet er formateret i den normale typografi, og meddelelsesteksten understøtter indbrudte grafikfiler og tekst ombrudt tekst. Hvis [optisk tegngenkendelse (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) er aktiveret for politikken, vises billeder, der indeholder udskrevet eller håndskrevet tekst, som opfylder politikbetingede betingelser, som et underordnet element for den tilknyttede meddelelse i denne visning.
- Almindelig **tekst:** Tekstvisning viser kun tekst i linjenummereret visning af meddelelsen og indeholder fremhævning af nøgleord i meddelelser og vedhæftede filer for følsomme oplysningstypeord eller nøgleord, der matcher den tilknyttede politik for overholdelse af regler og standarder i kommunikation. Fremhævning af nøgleord kan hjælpe dig med hurtigt at scanne lange meddelelser og vedhæftede filer for at finde et interessant område. I nogle tilfælde er fremhævet tekst muligvis kun i vedhæftede filer for meddelelser, der matcher politikbetingelser. Fremhævning af nøgleord understøttes ikke i ord, der er identificeret af indbyggede klassificeringer, der er tildelt en politik. Integrerede filer vises ikke, og linjenummerering denne visning er praktisk, hvis du vil referere til relevante detaljer blandt flere korrekturlæsere.
- **Samtale (eksempel)**: Tilgængelig for Microsoft Teams chatmeddelelser, viser denne visning op til fem meddelelser før og efter en advarselsmeddelelse for at hjælpe korrekturlæsere med at se aktiviteten i den samtalekontekst. Denne kontekst hjælper korrekturlæsere med hurtigt at evaluere meddelelser og træffe mere informerede beslutninger om løsningen af meddelelser. Tilføjelser af beskeder i realtid i samtaler vises, herunder alle indbyggede billeder, emojis og mærkater, der er tilgængelige i Teams. Der vises ikke billeder eller vedhæftede filer i meddelelser. Meddelelser vises automatisk for meddelelser, der er blevet redigeret, eller for meddelelser, der er blevet slettet fra samtalevinduet. Når en meddelelse er løst, bevares de tilknyttede samtalemeddelelser ikke med den løste meddelelse. Samtaler er tilgængelige i op til 60 dage, efter advarslen er identificeret.
- **Brugerhistorik**: Visningen Brugeroversigt viser alle andre beskeder, der genereres af enhver politik for overholdelse af kommunikation for den bruger, der sender meddelelsen.
- **Meddelelse om registreret mønster**: Mange chikanerende og modsløringshandlinger over tid og involverer gentagelse af forekomster af samme funktionsmåde af en bruger. Meddelelsen *Mønsteret registreret* vises i detaljerne om beskeden og henleder opmærksomheden på beskeden. Registrering af mønstre er baseret på pr. politik og evaluerer funktionsmåden i løbet af de seneste 30 dage, når mindst to meddelelser sendes til den samme modtager af en afsender. Brugere og korrekturlæsere kan bruge denne meddelelse til at identificere gentagen funktionsmåde for at evaluere beskeden efter behov.
- **Oversættelse**: Denne visning konverterer automatisk meddelelsesteksten til det sprog, der er konfigureret i indstillingen for vist sprog i Microsoft 365 for hver korrekturlæser. Visningen *Oversættelse* hjælper med at finde praktiske praktiske supporttjenester for organisationer med flersprogede brugere og eliminerer behovet for yderligere oversættelsestjenester uden for processen til gennemgang af kommunikationsoverholdelse. Hvis du bruger Microsofts oversættelsestjenester *,* kan visningen Oversættelse slås til og fra efter behov og understøtter en lang række sprog. Du kan finde en komplet liste over understøttede sprog [under Microsoft Oversætter Sprog](https://www.microsoft.com/translator/business/languages/). De sprog, der *Oversætter på listen over* sprog, understøttes *i visningen* Oversættelse.

### <a name="step-3-decide-on-a-remediation-action"></a>Trin 3: Beslut dig for en afhjælpningshandling

Nu hvor du har gennemset detaljerne i meddelelsen for beskeden, kan du vælge flere afhjælpningshandlinger:

- **Løs**: Hvis du vælger **kontrolelementet** Løs, fjernes meddelelsen straks fra køen Ventende beskeder, og der kan ikke gøres yderligere på meddelelsen. Hvis du vælger **Løs**, har du i bund og grund lukket beskeden uden yderligere klassificering. Alle løste meddelelser vises på **fanen Løst** .
- **Rapportere som klassificeret forkert**: Du kan altid løse en meddelelse som klassificeret forkert på et hvilket som helst tidspunkt i arbejdsprocessen for meddelelsesgennemsyn. Forkert klassificeret betyder, at beskeden ikke kunne bruges, eller at beskeden blev genereret forkert af beskedprocessen og eventuelle klassificeringer, der kan trænes. Løsning af elementet som en fejlklassificeret sender meddelelsesindhold, vedhæftede filer og meddelelsesemnet (herunder metadata) til Microsoft for at forbedre klassificeringer, der kan trænes. Data, der sendes til Microsoft, indeholder ikke oplysninger, der kan identificere eller bruges til at identificere brugere i organisationen. Der kan ikke gøres yderligere på meddelelsen, og alle fejlklassificerede meddelelser vises under **fanen Løst** .
- **Power Automate (eksempel)**: Brug et Power Automate til at automatisere procesopgaver for en advarsel. Kommunikationsoverholdelse omfatter som standard *Notify Manager* , når en bruger har en skabelon til besked om overholdelse af regler og standarder, som korrekturlæsere kan bruge til at automatisere meddelelsesprocessen for brugere med beskedbeskeder. Du kan finde flere oplysninger om oprettelse og Power Automate flows i overholdelse af regler og standarder i kommunikation i **trin 5: Overvej Power Automate flows** i denne artikel.
- **Tag som**: Tag meddelelsen *som kompatibel,* *ikke-kompatibel*, eller så tvivlbar, som den relaterer til politikker og standarder for din organisation. Tilføjelse af mærker og mærkning af kommentarer hjælper dig med at give besked om mikrofiltreringspolitik for eskaleringer eller som en del af andre interne revisionsprocesser. Når mærkningen er fuldført, kan du også vælge at løse meddelelsen for at flytte den ud af køen til ventende gennemsyn.
- **Giv** besked: Du kan bruge **kontrolelementet Giv** besked til at tildele beskeden en brugerdefineret meddelelsesskabelon og sende en advarselsmeddelelse til brugeren. Vælg den relevante meddelelsesskabelon, der er  konfigureret i området Indstillinger for overholdelse af kommunikation, og vælg **Send** for at sende en påmindelse via mail til den bruger, der har sendt meddelelsen, og for at løse problemet.
- **Eskaler**: Ved **hjælp af kontrolelementet** Eskaler kan du vælge, hvem der ellers i organisationen skal gennemse meddelelsen. Vælg på en liste over korrekturlæsere, der er konfigureret i politikken til overholdelse af kommunikation for at sende en mail med anmodning om yderligere gennemgang af beskeden. Den valgte korrekturlæser kan bruge et link i mailbeskeden til at gå direkte til elementer, der er eskaleret til dem til gennemsyn.
- **Eskaler til undersøgelse**: Med **Eskaler til** undersøgelseskontrol kan du oprette en ny [Advanced eDiscovery én](overview-ediscovery-20.md) eller flere meddelelser. Du skal angive et navn og noter til den nye sag, og den bruger, der sendte den meddelelse, der matcher politikken, tildeles automatisk som sagsbruger. Du behøver ikke yderligere tilladelser for at administrere sagen. Det løser ikke at oprette en sag og opretter ikke et nyt mærke til meddelelsen. Du kan vælge i alt 100 meddelelser, når du opretter Advanced eDiscovery en sag under afhjælpningsprocessen. Meddelelser i alle kommunikationskanaler, der overvåges af kommunikationsoverholdelse, understøttes. Du kan f.eks. vælge 50 Microsoft Teams chatsamtaler, 25 Exchange Online mails og 25 Yammer-meddelelser, når du åbner en ny Advanced eDiscovery-sag for en bruger.
- **Fjern meddelelse i Teams**: Med kontrolelementet Fjern meddelelse **i Teams** kan du blokere upassende meddelelser og indhold, der er identificeret i beskeder fra Microsoft Teams-kanaler og 1:1- og gruppechats. Fjernede meddelelser og indhold erstattes med et politiktip, der forklarer, at det er blokeret, og den politik, der gælder for fjernelse af det fra visningen. Modtagerne får et link i politiktippen for at få mere at vide om den gældende politik og gennemsynsprocessen. Afsenderen modtager et politiktip til den blokerede meddelelse og det blokerede indhold, men kan gennemse oplysningerne om den blokerede meddelelse og det blokerede indhold for at se konteksten vedrørende fjernelsen.

    ![Fjern en meddelelse fra Microsoft Teams.](../media/communication-compliance-remove-teams-message.png)

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>Trin 4: Afgør, om oplysninger om meddelelser skal arkiveres uden for overholdelse af kommunikationsreglerne

Meddelelsesdetaljer kan eksporteres eller downloades, hvis du har brug for at arkivere meddelelserne i en separat lagerløsning. Når du vælger **kontrolelementet Download**, føjes der automatisk markerede meddelelser til .ZIP fil, der kan gemmes på lager uden for Microsoft 365.

### <a name="step-5-consider-power-automate-flows"></a>Trin 5: Overvej Power Automate flow

[Microsoft Power Automate er](/power-automate/getting-started) en arbejdsprocestjeneste, der automatiserer handlinger på tværs af programmer og tjenester. Ved hjælp af flows fra skabeloner eller oprettet manuelt kan du automatisere almindelige opgaver, der er knyttet til disse programmer og tjenester. Når du aktiverer Power Automate til overholdelse af regler og standarder i kommunikation, kan du automatisere vigtige opgaver for beskeder og brugere. Du kan konfigurere Power Automate til at give ledere besked, når brugere har beskeder om overholdelse af kommunikation og andre programmer.

Kunder med Microsoft 365 abonnementer, der omfatter kommunikationsoverholdelse, behøver ikke yderligere Power Automate-licenser for at bruge den anbefalede standardkommunikationsoverholdelsesskabelon Power Automate. Standardskabelonen kan tilpasses til at understøtte din organisation og dække centrale scenarier for kommunikationsoverholdelse. Hvis du vælger at bruge Premium Power Automate-funktioner i disse skabeloner, oprette en brugerdefineret skabelon ved hjælp af Microsoft 365-overholdelsesforbindelse eller bruge Power Automate-skabeloner til andre overholdelsesområder i Microsoft 365, skal du muligvis bruge flere Power Automate licenser.

> [!IMPORTANT]
> Modtager du beskeder om yderligere licensvalidering, når der testes Power Automate flows? Din organisation har muligvis ikke modtaget serviceopdateringer til denne preview-funktion endnu. Opdateringer installeres, og alle organisationer med Microsoft 365-abonnementer, der omfatter overholdelse af kommunikation, bør have licenssupport til flows, der er oprettet ud fra de anbefalede Power Automate-skabeloner senest d. 30. oktober 2020.

![Overholdelse af regler og standarder Power Automate kommunikation.](../media/communication-compliance-power-automate.png)

Følgende skabelon Power Automate til kunder for at understøtte process automatisering i forbindelse med beskeder om kommunikationsoverholdelse:

- **Notify manager når en bruger har** en besked om overholdelse af kommunikation: Nogle organisationer skal muligvis have øjeblikkelig besked om administration, når en bruger har en besked om kommunikationsoverholdelse. Når dette flow er konfigureret og valgt, sendes lederen for sagsbrugeren en mail med følgende oplysninger om alle beskeder:
  - Gældende politik for beskeden
  - Dato/klokkeslæt for beskeden
  - Beskedens alvorsniveau

#### <a name="create-a-power-automate-flow"></a>Opret et Power Automate flow

Hvis du vil oprette Power Automate flow ud fra en anbefalet standardskabelon, skal du bruge indstillingen Administrer **Power Automate flows** fra kontrolelementet **Automatiser**, når du arbejder direkte i en besked. Hvis du vil Power Automate kommunikationsflow med **Administrer Power Automate flow**, skal du være medlem af mindst én rollegruppe for kommunikationsoverholdelse.

Udfør følgende trin for at oprette et Power Automate fra en standardskabelon:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Politikker for** >  overholdelse af kommunikation og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen Afventer i politikken **, og** vælg en ventende besked.
3. Vælg **Power Automate** i handlingsmenuen for beskeder.
4. På siden **Power Automate skal** du vælge en standardskabelon fra sektionen Skabeloner til overholdelse af regler og standarder **i** Kommunikation, som du kan lide på siden.
5. Flowet viser de integrerede forbindelser, der skal bruges til flowet, og vil blive vist, hvis forbindelsesstatusserne er tilgængelige. Hvis det er nødvendigt, skal du opdatere eventuelle forbindelser, der ikke vises som tilgængelige. Vælg **Fortsæt**.
6. Som standard er de anbefalede flows forudkonfigureret med de anbefalede felter for kommunikationsoverholdelse og Microsoft 365 tjenestedata, der kræves for at fuldføre den tildelte opgave i flowet. Hvis det er nødvendigt, kan du tilpasse flowkomponenterne ved hjælp **af** kontrolelementet Vis avancerede indstillinger og konfigurere de tilgængelige egenskaber for flowkomponenten.
7. Hvis det er nødvendigt, kan du føje yderligere trin til flowet ved at **vælge knappen Nyt** trin. I de fleste tilfælde skulle denne ændring ikke være nødvendig for de anbefalede standardskabeloner.
8. Vælg **Gem kladde** for at gemme flowet til yderligere konfiguration senere, eller vælg **Gem for** at fuldføre konfigurationen for flowet.
9. Vælg **Luk** for at vende tilbage Power Automate flowsiden. Den nye skabelon vises som et flow på fanen Mine **flow** og er automatisk tilgængelig fra Power Automate-kontrolelementet for den bruger, der oprettede flowet, når der arbejdes med beskeder om kommunikationsoverholdelse.

#### <a name="share-a-power-automate-flow"></a>Del et Power Automate flow

Som standard er Power Automate, der er oprettet af en bruger, kun tilgængelige for den pågældende bruger. Hvis andre brugere af kommunikationsoverholdelse skal have adgang til og bruge et flow, skal flowet deles af flowudvikleren. Hvis du vil dele et flow, skal du bruge **kontrolelementet Power Automate**, når du arbejder direkte i en besked.

Hvis du vil Power Automate kommunikationsflow, skal du være medlem af mindst én rollegruppe for kommunikationsoverholdelse.
Udfør følgende trin for at dele et Power Automate flow:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Politikker for** >  overholdelse af kommunikation og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen Afventer i politikken **, og** vælg en ventende besked.
3. Vælg **Power Automate** i handlingsmenuen for beskeder.
4. På siden **Power Automate flows** skal du vælge **fanen Mine flow** **eller Teamflows**.
5. Vælg flowet, der skal deles, og vælg **derefter Del** i menuen med indstillinger for flow.
6. På siden flowdeling skal du skrive navnet på den bruger eller gruppe, du vil tilføje som ejer for flowet.
7. I dialogboksen **Forbindelse brugt** skal du vælge **OK for** at bekræfte, at den tilføjede bruger eller gruppe har fuld adgang til flowet.

#### <a name="edit-a-power-automate-flow"></a>Rediger et Power Automate flow

Hvis du har brug for at redigere et flow, skal du bruge **kontrolelementet Power Automate**, når du arbejder direkte i en besked. Hvis du vil redigere Power Automate kommunikationsflow, skal du være medlem af mindst én rollegruppe for overholdelse af kommunikation.

Udfør følgende trin for at redigere et Power Automate flow:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Politikker for** >  overholdelse af kommunikation og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen Afventer i politikken **, og** vælg en ventende besked.
3. Vælg **Power Automate** i handlingsmenuen for beskeder.
4. På siden **Power Automate flows skal** du vælge flow, der skal redigeres. Vælg **Rediger** i flowstyringsmenuen.
5. Vælg **ellipsen for** >  **Indstillinger at** ændre en indstilling for flowkomponent eller **ellipseSlette**  >  for at slette en flowkomponent.
6. Vælg **Gem og** derefter **Luk for at** fuldføre redigeringen af flowet.

#### <a name="delete-a-power-automate-flow"></a>Slet et Power Automate flow

Hvis du vil slette et flow, skal du bruge kontrolelementet til **Power Automate**, når du arbejder direkte i en besked. Hvis du vil Power Automate et kommunikationsflow, skal du være medlem af mindst én rollegruppe for overholdelse af kommunikation.

Udfør følgende trin for at slette et Power Automate flow:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Politikker for** >  overholdelse af kommunikation og vælge politikken med den besked, du vil gennemse.
2. Vælg fanen Afventer i politikken **, og** vælg en ventende besked.
3. Vælg **Power Automate** i handlingsmenuen for beskeder.
4. På siden **Power Automate flows skal** du vælge flow, der skal slettes. Vælg **Slet** i flowstyringsmenuen.
5. I bekræftelsesdialogboksen for sletning skal du **vælge Slet** for at fjerne flowet eller vælge **Annuller** for at afslutte sletningshandlingen.

### <a name="step-6-consider-creating-notice-templates"></a>Trin 6: Overvej at oprette meddelelsesskabeloner

Du kan oprette meddelelsesskabeloner, hvis du vil sende brugere en påmindelse via mail for politik matches som en del af processen til løsning af problemer. Meddelelser kan kun sendes til den brugermailadresse, der er knyttet til det politik match, der genererede den specifikke besked til afhjælpning. Når du vælger en meddelelsesskabelon, der skal anvendes på en overtrædelse af politikken som en del af afhjælpningsarbejdsprocessen, kan du vælge at acceptere feltværdierne, der er defineret i skabelonen, eller at overskrive felterne efter behov.

Meddelelsesskabeloner er brugerdefinerede mailskabeloner, hvor du kan definere følgende meddelelsesfelter i området **Indstillinger for overholdelse af kommunikation** :

|**Felt**|**Påkrævet**| **Detaljer** |
|:-----|:-----|:-----|
|**Skabelonnavn** | Ja | Brugervenligt navn til meddelelsesskabelonen, som du skal vælge i beskedarbejdsprocessen under afhjælpning, understøtter teksttegn. |
| **Afsenderadresse** | Ja | Adressen på en eller flere brugere eller grupper, der sender meddelelsen til brugeren med et match til politikken, som er valgt fra Active Directory for dit abonnement. |
| **CC- og BCC-adresser** | Nej | Valgfrie brugere eller grupper, der skal underrettes om matchet politik, som vælges fra Active Directory for dit abonnement. |
| **Emne** | Ja | Oplysninger, der vises i meddelelsens emnelinje, understøtter teksttegn. |
| **Meddelelsestekst** | Ja | Oplysninger, der vises i brødteksten, understøtter tekst- eller HTML-værdier. |

### <a name="html-for-notices"></a>HTML til meddelelser

Hvis du vil oprette mere end en enkel tekstbaseret mail til meddelelser, kan du oprette en mere detaljeret meddelelse ved hjælp af HTML i meddelelsesfeltet i en meddelelsesskabelon. Følgende eksempel indeholder brødtekstformatet til en grundlæggende HTML-baseret mailmeddelelsesskabelon:

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
> Implementering af HTML-attributten href i skabelonerne til meddelelser om overholdelse af kommunikation understøtter i øjeblikket kun enkelte anførselstegn i stedet for dobbelte anførselstegn for URL-referencer.

## <a name="unresolve-messages-preview"></a>Ikke-afklarede meddelelser (eksempel)

Når meddelelserne er løst, fjernes de fra **fanevisningen** Afventer og vises i **fanevisningen** Løst. Undersøgelses- og afhjælpningshandlinger er ikke tilgængelige for meddelelser i *visningen Løst* . Der kan dog være tilfælde, hvor du er nødt til at gøre yderligere på en meddelelse, der er blevet løst ved en fejltagelse, eller som kræver yderligere undersøgelse efter den indledende løsning. Du kan bruge kommandofunktionen, der ikke blev fundet, til at flytte *en eller flere* meddelelser fra visningen Løst tilbage til *visningen Afventer* .

Hvis du vil finde en ny meddelelse, skal du udføre følgende trin:

1. Log på computeren [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) legitimationsoplysninger for en bruger, der er tildelt rollegrupperne *Communication Compliance Analyst* eller *Communication Compliance Den* Microsoft 365 i organisationen.
2. I Microsoft 365 Overholdelsescenter skal du gå til Overholdelse **af kommunikationsreglerne**.
3. Vælg fanen **Politikker** , og vælg derefter en politik, der indeholder den løste advarselsmeddelelse, dobbeltklik for at åbne **siden** Politik.
4. På siden **Politik** skal du vælge **fanen Løst** .
5. På fanen **Løst skal** du vælge en eller flere meddelelser for at gå tilbage til *Afventer*.
6. På kommandolinjen skal du vælge **Ikke-løst**.
7. Tilføj eventuelle **kommentarer, der** er relevante for den ikke-afklarede handling, i ruden Ikke-løst element, og vælg **Gem** for at flytte elementet tilbage til *Afventer*.
8. Vælg fanen **Ventende** for at bekræfte, at de markerede elementer vises.