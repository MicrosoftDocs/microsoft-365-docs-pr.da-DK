---
title: Simulerings automatisering til simulering af angreb
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorer kan lære, hvordan du opretter automatiserede simuleringer, der indeholder bestemte teknikker og nyttedata, der starter, når de angivne betingelser er opfyldt i Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 327091706ed7c8c2a6f1f1180af7888ed67c1a57
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596920"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Simulerings automatisering til simulering af angreb

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Du kan finde oplysninger om kursus i at simulere angreb i [Kom i gang med at bruge simulering af angreb](attack-simulation-training-get-started.md).

Hvis du vil oprette en automatisering af simulering, skal du gøre følgende:

1. I portalen Microsoft 365 Defender på skal du gå <https://security.microsoft.com/>til Mail og **& på** \> fanen **Simulering** \> af **simulering af automatisering.**

   For at gå direkte til fanen **Simulerings automatisering** skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulationautomation>.

2. På fanen **Simulerings automatisering** skal du vælge ![Opret automatiseringsikon.](../../media/m365-cc-sc-create-icon.png) **Opret automatisering**.

   ![Opret automatiseringsknappen på fanen Simulerings automatisering i Kursus i angrebssimulering Microsoft 365 Defender portalen.](../../media/attack-sim-training-sim-automations-create.png)

3. Guiden til oprettelse åbnes. Resten af denne artikel beskriver siderne og de indstillinger, de indeholder.

> [!NOTE]
> Under simuleringsguiden kan du når som helst  klikke på Gem og luk for at gemme din status og fortsætte med at konfigurere simulering senere. Den ufuldstændige simulering **har Statusværdien** **Kladde** under **fanen Simuleringer** . Du kan gå til det sted, hvor du slap, ved at vælge simulering og klikke på Rediger simuleringsikon ![.](../../media/m365-cc-sc-edit-icon.png) **Rediger** simulering.## Navn og beskriv simulering.

## <a name="name-and-describe-the-simulation-automation"></a>Navngive og beskrive simulerings automatiseringen

På siden **Navn på** automatisering skal du konfigurere følgende indstillinger:

- **Navn**: Angiv et entydigt, beskrivende navn til simulering.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse til simulering.

Klik på Næste, når du er **færdig**.

## <a name="select-one-or-more-social-engineering-techniques"></a>Vælg en eller flere social engineering-teknikker

På siden **Vælg social engineering techniques** skal du vælge en eller flere af de tilgængelige social engineering-teknikker, som blev curated fra [MITRE ATT&CK framework®](https://attack.mitre.org/techniques/enterprise/). Forskellige nyttedata er tilgængelige for forskellige teknikker. Følgende social engineering-teknikker er tilgængelige:

- **Indsamling af** legitimationsoplysninger: Forsøg på at indsamle legitimationsoplysninger ved at tage brugere til et velkendt udseende websted med inputfelter til at indsende et brugernavn og en adgangskode.
- **Vedhæftet malware**: Føjer en ondsindet vedhæftet fil til en meddelelse. Når brugeren åbner den vedhæftede fil, køres en tilfældig kode, der kan hjælpe hackeren med at kompromittere destinationens enhed.
- **Link i vedhæftet** fil: En type legitimationstagningshybrid. En hacker indsætter en URL-adresse i en vedhæftet fil i en mail. URL-adressen i den vedhæftede fil følger den samme metode som indsamling af legitimationsoplysninger.
- **Link til malware**: Kører en vilkårlig kode fra en fil, der er hostet på en velkendt fildelingstjeneste. Den meddelelse, der sendes til brugeren, indeholder et link til denne skadelige fil. Åbne filen og hjælpe hackeren med at kompromittere målenheden.
- **Drev efter URL-adresse**: Den skadelige URL-adresse i meddelelsen fører brugeren til et velkendt websted, der uovervåget kører og/eller installerer kode på brugerens enhed.

Hvis du klikker på **linket** Vis detaljer i beskrivelsen, åbnes en pop op-vindue med detaljer, der beskriver den teknik og de simuleringstrin, der er resultatet af metoden.

![Pop op-pop op-pop-op-oplysninger for teknik til indsamling af legitimationsoplysninger på siden Vælg social engineering-teknikker.](../../media/attack-sim-training-simulations-select-technique-sim-steps.png)

Klik på Næste, når du er **færdig**.

## <a name="select-payloads"></a>Vælg nyttedata

På siden **Vælg nyttedata** skal du vælge en af følgende muligheder:

- **Vælg manuelt**
- **Randomiser**

Hvis du vælger **Randomize**, er der ikke noget at konfigurere på denne side, så klik på **Næste for** at fortsætte.

Hvis du vælger **Manuelt**, skal du vælge en eller flere nyttedata på listen. Følgende detaljer vises som en hjælp til at vælge:

- **Navn på nyttedata**
- **Teknik**: Du skal vælge mindst én nyttelast pr. teknik, du har valgt på den forrige side.
- **Sprog**: Sproget for indholdet af nyttedata. Microsofts katalog over nyttedata (global) leverer nyttedata på mere end 10 sprog, som også kan filtreres.
- **Klikhastighed**: Hvor mange personer, der har klikket på denne nyttedata.
- **Forudsagte forligssats**: Historiske data for nyttedata på tværs Microsoft 365 der forudsiger procentdelen af personer, der bliver kompromitteret af denne nyttedata.
- **De simuleringer** , der er startet, tæller det antal gange, denne nyttedata blev brugt i andre simuleringerne.

På ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefeltet** kan du skrive en del af navnet på nyttedata og trykke på Enter for at filtrere resultaterne.

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Kompleksitet**: Beregnet på baggrund af antallet af indikatorer i nyttedata, der angiver et muligt angreb (stavefejl, haster osv.). Flere indikatorer er nemmere at identificere som et angreb og angiver mindre kompleksitet. De tilgængelige værdier er:
  - **Lav**
  - **Mellem**
  - **Høj**
- **Kilde**: Angiver, om nyttedataene blev oprettet i din organisation eller er en del af Microsofts eksisterende nyttedatakatalog. Gyldige værdier er:
  - **Global**
  - **Lejer**
  - **Alle**
- **Sprog**: De tilgængelige værdier **er: engelsk****, spansk****, tysk****, japansk****, fransk****, portugisisk****, hollandsk****, italiensk****, svensk**, kinesisk (forenklet), norsk **bokmål****, polsk****, russisk**, **finsk**, **koreansk****,** tyrkisk **, ungarsk****, hebraisk**, **thai****, arabisk**, vietnamesisk, **slovakisk******, **græsk**, **indonesisk, rumænsk****,** slovensk, **kroatisk**, **catalansk** og **andet**.
- **Tilføj mærker**
- **Filtrer** efter tema: De tilgængelige værdier **er:** Kontoaktivering **,** Kontobekræftelse **, Fakturering**, Ryd op i **mail****, Dokument** **modtaget, Udgift**, **Fax****,** Økonomirapport **,** Indgående **meddelelser, Faktura****, Modtagne** **elementer,** Logonbesked, **Mail** **modtaget, Adgangskode****, Betaling****, Løn**, Personlig **tilbud**, **Karantæne**, **Fjernarbejde**, Gennemse **meddelelse**, **Sikkerhedsopdatering**, **Afbrudt tjeneste**, **Påkrævet signatur****,** Opgrader postkasselager Bekræft postkasse, **Telefonsvarer** og **Andet**.
- **Filtrer efter mærke**: De tilgængelige værdier er: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, Netflix, **Scotiabank**, **SendGrid**, **title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** og **Andre**. 
- **Filtrer** efter branche: De tilgængelige værdier er: **Bank****,** forretningstjenester **,** forbrugertjenester, **Uddannelse**, **Energi****, Konstruktion**, **Rådgivning**, Finansielle tjenester, **Government**, **Hotel**, **Forsikring**, **Juridiske**, **Courier services**, **IT****,** **Sundhedssektoren, Produktion**, **Retail**, **Telecom**, **Real Estate**, og **Andet**.
- **Aktuel hændelse**: De tilgængelige værdier er **Ja** eller **Nej**.
- **Til** rådighed: De tilgængelige værdier er **Ja** eller **Nej**.

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Hvis du vælger en nyttedata fra listen ved at klikke på navnet, vises oplysninger om nyttedata i et pop op-pop op-format:

- Fanen **Oversigt** indeholder et eksempel og andre oplysninger om nyttedata.
- Fanen **Simulering er** startet indeholder **Simuleringsnavn**, **Klikhastighed**, **Kompromitteret** hastighed og **Handling**.

![Pop op-flyv ind-oplysninger om nyttedata i angrebssimuleringskursus Microsoft 365 Defender portalen.](../../media/attack-sim-training-simulations-select-payload-details.png)

Klik på Næste, når du er **færdig**.

## <a name="target-users"></a>Målbrugere

På siden **Målbrugere skal** du vælge, hvem der skal modtage simulering. Konfigurer en af følgende indstillinger:

- **Medtag alle brugere i organisationen**: De berørte brugere vises på lister med 10. Du kan bruge knapperne **Næste** **og Forrige** direkte under listen over brugere til at rulle gennem listen. Du kan også bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgeikon** på siden for at finde de berørte brugere.
- **Medtag kun bestemte brugere og grupper**: Vælg en af følgende indstillinger:
  - ![Ikonet Tilføj brugere.](../../media/m365-cc-sc-create-icon.png) **Tilføj brugere**: I pop **op-dialogboksen Tilføj** brugere, der vises, kan du finde brugere og grupper ud fra følgende kriterier:
    - **Brugere eller grupper**: I ikonet ![Søg efter brugere og grupper.](../../media/m365-cc-sc-search-icon.png) **Feltet Søg efter brugere og** grupper kan du skrive en del af navnet  eller mailadressen på brugeren eller gruppen og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne. Klik på Tilføj x brugere, når **du er færdig**.

      > [!NOTE]
      > Hvis du klikker **på knappen Tilføj filtre** for at vende  tilbage til indstillingerne Filtrer brugere efter kategorier, ryddes alle brugere eller grupper, du har valgt i søgeresultaterne.

    - **Filtrer brugere efter** kategorier: Vælg mellem ingen, nogle eller alle af følgende indstillinger:
      - **Foreslåede brugergrupper**: Vælg mellem følgende værdier:
        - **Alle foreslåede brugergrupper**
        - **Brugere ikke målrettet af en simulering inden for de sidste tre måneder**
        - **Gentag gentagelser**
      - **Afdeling**: Brug følgende indstillinger:
        - **Søg**: I ikonet ![Søg efter afdeling.](../../media/m365-cc-sc-search-icon.png) **Feltet Søg efter** afdeling kan du skrive en del af værdien for Afdeling og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne.
        - Vælg **hele afdelingen**
        - Vælg eksisterende Afdelingsværdier.
      - **Titel**: Brug følgende indstillinger:
        - **Søg**: I ikonet ![Søg efter titel.](../../media/m365-cc-sc-search-icon.png) **Feltet Søg efter** titel kan du skrive en del af titelværdien og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne.
        - Markér **hele titlen**
        - Vælg eksisterende titelværdier.

      ![Brugerfiltrering på siden Målbrugere i Kursus i angrebssimulering i Microsoft 365 Defender portal.](../../media/attack-sim-training-simulations-target-users-filter-by-category.png)

      Når du har identificeret dine kriterier, vises de berørte brugere i  sektionen Brugerliste, der vises, hvor du kan vælge nogle eller alle de modtagere, der opdages.

      Når du er færdig, skal du klikke **på Anvend(x)** og derefter klikke på **Tilføj x brugere**.

  Tilbage på hovedsiden **Målbrugere** kan du bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefeltet** for at finde de berørte brugere. Du kan også klikke på ![ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** for at fjerne bestemte brugere.

- ![Ikonet Importér.](../../media/m365-cc-sc-create-icon.png) **Importér**: I den dialogboks, der åbnes, skal du angive en CSV-fil, der indeholder én mailadresse pr. linje.

  Når du har fundet en CSV-fil, importeres og vises listen over brugere på **siden Målrettede** brugere. Du kan bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefeltet** for at finde de berørte brugere. Du kan også klikke på ![ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** for at fjerne bestemte brugere.

Klik på Næste, når du er **færdig**.

## <a name="assign-training"></a>Tildel kurser

På siden **Tildel** kursus kan du tildele kurser til simulering. Vi anbefaler, at du tildeler kurser til hver simulering, da medarbejdere, der gennemgår kurser, er mindre følsomme for lignende angreb. Der findes følgende tilgængelige indstillinger:

- **Vælg indstillinger for undervisningsindhold**: Vælg en af følgende indstillinger:
  - **Microsoft-kursusoplevelse**: Dette er standardværdien, der har følgende tilknyttede indstillinger til konfiguration:
    - Vælg en af følgende indstillinger:
      - **Tildel mig kurser**: Dette er standardværdien og den anbefalede værdi. Vi tildeler kurser baseret på en brugers tidligere simulering og kursusresultater, og du kan gennemse valgene i de næste trin i guiden.
      - **Vælg selv kurser** og moduler: Hvis du vælger denne værdi, vil du stadig kunne se det anbefalede indhold samt alle tilgængelige kurser og moduler i næste trin af guiden.
    - **Forfaldsdato**: Vælg en af følgende værdier:
      - **30 dage efter simulering slutter**: Dette er standardværdien.
      - **15 dage efter simulering slutter**
      - **7 dage efter simulering slutter**
  - **Omdiriger til en brugerdefineret URL-adresse**: Denne værdi har følgende tilknyttede indstillinger til konfiguration:
    - **URL-adresse til brugerdefineret** kursus (påkrævet)
    - **Brugerdefineret kursusnavn** (påkrævet)
    - **Brugerdefineret kursusbeskrivelse**
    - **Brugerdefineret varighed af kurser (i minutter): Standardværdien** er 0, hvilket betyder, at der ikke er angivet nogen varighed for træningen.
    - **Forfaldsdato**: Vælg en af følgende værdier:
      - **30 dage efter simulering slutter**: Dette er standardværdien.
      - **15 dage efter simulering slutter**
      - **7 dage efter simulering slutter**
  - **Intet kursus**: Hvis du vælger denne værdi, er den eneste indstilling på siden knappen **Næste, der** fører dig til [**landingssiden**](#landing-page) .

![Tilføj anbefalede kurser på siden Undervisning i angrebssimulering i Microsoft 365 Defender portal.](../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png)

### <a name="training-assignment"></a>Kursustildeling

> [!NOTE]
> Siden **Undervisningstildeling** er kun tilgængelig, hvis du har **valgt Microsoft-kursusoplevelse** \> **Vælg selv kurser og moduler** på den forrige side.

På siden **Kursustildeling** skal du vælge de kurser, du vil føje til simulering, ved at klikke på ![ikonet Tilføj kurser.](../../media/m365-cc-sc-create-icon.png) **Tilføj kurser**.

I pop **op-dialogboksen** Tilføj kursus, der vises, kan du vælge de kurser, der skal bruges, på følgende tilgængelige faner:

- **Fanen** Anbefalet: Viser de anbefalede indbyggede kurser baseret på simuleringskonfigurationen. Dette er de samme kurser, der ville være blevet tildelt, hvis du valgte **Tildel kursus til mig** på den forrige side.
- **Fanen Alle kurser** : Viser alle indbyggede kurser, der er tilgængelige.

  Følgende oplysninger vises for hvert kursus:

  - **Kursusnavn**
  - **Kilde**: Værdien er **Global**.
  - **Varighed (min)**
  - **Eksempel**: Klik på **knappen Eksempel** for at se kurserne.

  På ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefeltet** , du kan skrive en del af navnet på kurset og trykke på Enter for at filtrere resultaterne på den aktuelle fane.

  Markér alle de kurser, du vil medtage fra den aktuelle fane, og klik derefter på **Tilføj**.

Tilbage på **hovedsiden for Undervisningstildeling** vises de kurser, du har valgt. Følgende oplysninger vises for hvert kursus:

- **Kursusnavn**
- **Kilde**
- **Varighed (min)**

For hvert kursus på listen skal du vælge, hvem der får træningen, ved at vælge værdierne i **kolonnen Tildel** til:

- **Alle brugere**

  eller en eller begge af følgende værdier:

- **Klikkede på nyttedata**
- **Kompromitteret**

Hvis du ikke vil bruge et kursus, der vises, skal du klikke på Slet ![ikon.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

![Kursusopgaveside i Angrebssimuleringskursus i Microsoft 365 Defender portal.](../../media/attack-sim-training-training-assignment.png)

Klik på Næste, når du er **færdig**.

### <a name="landing-page"></a>Landingsside

På **landingssiden** skal du konfigurere den webside, brugeren bliver ført til, hvis de åbner nyttedata i simulering.

- **Vælg landingssideindstilling**: De tilgængelige værdier afhænger af dine tidligere valg på siden Vælg [nyttedata](#select-payloads) som beskrevet i følgende tabel:

  <br>

  ****

  |Valg på siden Vælg nyttedata|Tilgængelige værdier for Indstillingen Vælg landingsside|
  |---|---|
  |Vælg manuelt|Brug Microsofts standardlandingsside <p> Opret din egen landingsside <p> Brug en brugerdefineret URL-adresse <p> **Bemærk**! Værdien **Brug en brugerdefineret URL-adresse** er ikke tilgængelig, hvis du tidligere har valgt vedhæftet **malware** eller **Link til malware** på [siden Vælg social engineering-teknikker](#select-one-or-more-social-engineering-techniques) .|
  |Randomiser|Brug Microsofts standardlandingsside|
  |

  De tilgængelige **Select landing Page preference-værdier** og deres tilknyttede indstillinger er beskrevet på følgende liste:

  - **Brug Microsofts standardlandingsside**. Dette er standardværdien, og resulterer i en handling med Microsoft-standardskabelon, -logo og -nyttedataindikator, der gælder for alle nyttedata.

    Du skal konfigurere følgende yderligere indstillinger på **landingssiden** :

    - **Vælg layout for landingsside**: Vælg en af de fem tilgængelige landingssideskabeloner.
    - **Tilføj logo**: Klik  på Gennemse for at finde og vælge en .png-, .jpeg- eller .gif-fil, der skal føjes til alle nyttedata, der er valgt af Microsoft. Logostørrelsen bør maksimalt være 210 x 70 for at undgå forvrængning. Klik på Fjern for at fjerne **logoet**.
    - **Indikatorer for nyttedata**: Denne indstilling er ikke tilgængelig, hvis du tidligere har valgt vedhæftet **malware** eller Link til **malware** på [siden Vælg sociale tekniske teknikker](#select-one-or-more-social-engineering-techniques) .

      Vælg **Tilføj indikatorer for nyttedata for at sende en mail** for at hjælpe brugerne med at finde ud af, hvordan phishingmeddelelser identificeres.

    Du kan få vist resultaterne ved at klikke **på knappen Åbn** panelet Vis udskrift midt på siden. I pop op-pop-op-eksemplet, der  vises, kan du bruge Vælg nyttedata for at få vist et eksempel på, hvordan hver enkelt nyttedata ser ud.

  - **Opret din egen landingsside**: Denne værdi resulterer i en enkelt handling med en nyttedataindikator, der anvendes på de valgte nyttedata.

    Du skal konfigurere følgende yderligere indstillinger på **landingssiden** :

    - **Indikatorer for nyttedata**: Denne indstilling kan kun vælges, hvis begge af følgende betingelser gælder:
      - Du har tidligere **valgt indsamling af legitimationsoplysninger**, **Link i** vedhæftet fil **eller Drive-by URL** på [siden Vælg social engineering-teknikker](#select-one-or-more-social-engineering-techniques) .
      - Når du har tilføjet mærket **Dynamisk med** **navnet Indsæt mailindhold** i sidens indhold.

    - Sideindhold: Der er to tilgængelige faner:

      - **Tekst**: Der kan oprettes en RTF-editor til at oprette din landingsside. Ud over de typiske skrifttype- og formateringsindstillinger er følgende indstillinger tilgængelige:
        - **Dynamisk mærke**: Vælg mellem følgende mærker:
          - **Indsæt navn**
          - **Indsæt afsendernavn**
          - **Indsæt afsendermail**
          - **Indsæt mailens emne**
          - **Indsæt mailindhold**
          - **Indsæt dato**
        - **Brug som standard**: Vælg en af de fem tilgængelige landingssideskabeloner til at starte med. Du kan ændre teksten og layoutet i redigeringsområdet. Hvis du vil nulstille landingssiden til skabelonens standardtekst og -layout, skal du klikke på **Nulstil til standard**.
        - **Kursuslink**: I dialogboksen **Url-adresse** til navnekursus, der vises, skal du angive en linktitel til kursuslinket og derefter klikke på Bekræft for at føje linket til landingssiden.
      - **Kode**: Du kan få vist og redigere HTML-koden direkte.

      Du kan få vist resultaterne ved at klikke **på knappen Åbn** panelet Vis udskrift midt på siden. I pop op-pop-op-eksemplet, der  vises, kan du bruge Vælg nyttedata for at få vist et eksempel på, hvordan hver enkelt nyttedata ser ud.

  - **Brug en brugerdefineret URL-adresse**: Tilføj URL-adressen i **feltet Angiv den brugerdefinerede url-adresse til landingssiden** , der vises. Der er ingen andre indstillinger tilgængelige på siden.

Klik på Næste, når du er **færdig**.

## <a name="select-end-user-notification"></a>Vælg meddelelse til slutbruger

På siden **Vælg besked til slutbruger** skal du vælge mellem følgende meddelelsesindstillinger:

- **Levér ikke meddelelser**: Klik **på Fortsæt** i den dialogboks, der vises. Hvis du vælger denne indstilling, kommer du til siden med [simuleringsplanen](#simulation-schedule) , når du klikker på **Næste**.

- **Microsoft-standardmeddelelse (anbefales)**: Følgende yderligere indstillinger er tilgængelige på siden:
  - **Vælg standardsprog**: De tilgængelige værdier er: kinesisk **(** forenklet), kinesisk **(traditionelt),** **engelsk, fransk****, tysk****, italiensk****, japansk****,** **koreansk****, portugisisk****, russisk****,** **spansk og hollandsk**.
  - Som standard er den eneste tilgængelige meddelelse, du kan vælge, **Meddelelse om positiv feedback fra Microsoft**. Følgende oplysninger er tilgængelige for meddelelsen:
    - **Meddelelser** (navn): Værdien er Microsofts **standardmeddelelse om positive forbedringer**.
    - **Sprog**: Hvis meddelelsen indeholder flere oversættelser, vises de første to sprog direkte. Hvis du vil se de resterende sprog, skal du holde markøren over det numeriske ikon (f.eks. **+10**).
    - **Type**: Værdien er **positiv til at se ud**.
    - **Indstillinger for** levering: Vælg mellem følgende værdier:
      - **Lever ikke**
      - **Lever, når kampagnen slutter**
      - **Lever under kampagne**
    - **Lever til**: Værdien er **Ikke tilgængelig**.
    - **Handlinger**: Hvis du klikker på ikonet ![Vis.](../../media/m365-cc-sc-view-icon.png) **Ikonet** Vis, **siden Gennemse** meddelelse vises med følgende oplysninger:
      - **Fanen** Eksempel: Se meddelelse. Hvis du vil have vist meddelelsen på forskellige sprog, skal du **bruge feltet Vælg** sprog.
      - **Fanen** Detaljer: Få vist oplysninger om meddelelsen:
        - **Beskrivelse af meddelelse**
        - **Kilde**: For indbyggede meddelelser er værdien **Global**. For brugerdefinerede meddelelser er værdien **Lejer**.
        - **Meddelelsestype**
        - **Ændret af**
        - **Senest ændret**

        Klik på Luk, når du er **færdig**.

  Hvis du vælger denne indstilling, kommer du til siden med [simuleringsplanen](#simulation-schedule) , når du klikker på **Næste**.

- **Tilpassede beskeder til** slutbrugere: Når du klikker på **Næste, kommer** du til siden Med  positive beskeder, som beskrevet i næste afsnit, hvor du kan vælge mellem eksisterende meddelelser eller oprette nye meddelelser.

Klik på Næste, når du er **færdig**.

### <a name="positive-reinforcement-notification"></a>Meddelelse om positiv meddelelse om meddelelser om positive notifikationer

Siden **besked om positive** beskeder om beskeder om positive brugere er kun tilgængelig, hvis du **har valgt Tilpassede beskeder til slutbrugere** på den forrige side.

- **Indstillinger for** levering: Vælg en af følgende værdier:
  - **Lever ikke**
  - **Lever, når brugeren rapporterer en phish, og kampagnen slutter**
  - **Lever umiddelbart efter, at brugeren rapporterer en phish**

- **Vælg en meddelelse med positive meddelelser**: Du kan vælge en eksisterende meddelelse eller oprette en ny meddelelse af typen Positiv meddelelse, **der skal** anvendes:
  - Hvis du vil vælge en eksisterende meddelelse, skal du klikke i det tomme område ud for meddelelsesnavnet. Hvis du klikker på meddelelsesnavnet, markeres meddelelsen, og der vises et eksempel. Hvis du vil fjerne markeringen i meddelelsen, skal du fjerne markeringen i afkrydsningsfeltet ud for meddelelsen.
  - Hvis du vil søge efter en eksisterende meddelelse, skal du bruge ![ikonet Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at søge efter navnet.
  - Hvis du vil oprette en ny meddelelse, skal du klikke ![på Opret nyt ikon.](../../media/m365-cc-sc-create-icon.png) **Opret ny**.
  - Hvis du vil ændre en eksisterende brugerdefineret meddelelse, skal du markere den og derefter klikke på ![Rediger meddelelsesikon.](../../media/m365-cc-sc-edit-icon.png) **Rediger meddelelse**.

#### <a name="create-new-notification-wizard"></a>Guiden Opret ny meddelelse

Hvis du klikkede på ![Opret nyt ikon.](../../media/m365-cc-sc-create-icon.png) **Opret en ny** **meddelelsesside med positive notifikationer** , og der åbnes en guide til oprettelse af meddelelser.

Trinnene til oprettelse er identiske som beskrevet [i Opret beskeder til slutbrugere](attack-simulation-traning-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> På siden **Definer detaljer** skal du sørge for at vælge værdien **Positiv meddelelse** for **Vælg meddelelsestype**. Vælg ikke **Simuleringsmeddelelse**.

Når du er færdig, kommer du tilbage til siden med meddelelsen om  positive positive, hvor den meddelelse, du lige har oprettet, nu vises på listen Vælg et **positivt** valg.

- Hvis du vil oprette en ny meddelelse, skal du klikke på ![Opret nyt ikon.](../../media/m365-cc-sc-create-icon.png).
- Hvis du vil ændre meddelelsen eller tilføje flere oversættelser, skal du vælge meddelelsen på listen og derefter klikke på ikonet ![Rediger meddelelse.](../../media/m365-cc-sc-edit-icon.png) **Rediger meddelelse** for at starte meddelelsesguiden som beskrevet tidligere (med de fleste værdier allerede udfyldt). Hvis meddelelsen allerede indeholder oversættelser for de 12 understøttede sprog, kan du ikke tilføje flere oversættelser.

Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

## <a name="simulation-schedule"></a>Simuleringsplan

På siden **Simuleringsplan** skal du vælge en af følgende værdier:

- **Randomiseret**: Du skal stadig vælge tidsplanen på næste side, men simuleringerne starter på tilfældige tidspunkter med tidsplanen.
- **Rettet**

Klik på Næste, når du er **færdig**.

## <a name="schedule-details"></a>Oplysninger om tidsplan

Hvad du ser på siden **Med tidsplanens detaljer** afhænger af, om du har valgt **Vilkårlig eller** **Fast** på den forrige side.

- **Randomiseret**: Følgende indstillinger er tilgængelige:
  - **Afsnittet Simuleringsstart** : Konfigurer følgende indstilling:
    - **Vælg den dato, simuleringerne skal starte fra**
  - **Afsnittet Simulerings** scoping: Konfigurer følgende indstillinger:
    - **Vælg de dage i ugen, som simuleringerne må starte** på: Vælg en eller flere dage i ugen.
    - **Angiv det maksimale antal simuleringer, der kan startes mellem start- og slutdatoerne**: Angiv en værdi fra 1 til 10.
    - **Randomisere afsendelsestider**: Vælg denne indstilling for at randomisere afsendelsestider.
  - **Afsnittet Simuleringsslut** : Konfigurer følgende indstilling:
    - **Vælg den dato, dine simuleringer skal slutte**

- **Rettet**: Følgende indstillinger er tilgængelige:
  - **Afsnittet Simuleringsstart** : Konfigurer følgende indstilling:
    - **Vælg den dato, simuleringerne skal starte fra**
  - **Afsnittet Gentagelse** af simulering: Konfigurer følgende indstillinger:
    - **Vælg, om du vil have simuleringer til at starte ugentligt** eller månedligt: Vælg en af følgende værdier:
      - **Ugentligt**: Dette er standardværdien.
      - **Månedligt**
    - **Angiv, hvor ofte i uger du vil have simuleringerne til at gentages**: Angiv en værdi fra 1 til 99 uger.
    - **Vælg den ugedag, du vil have simuleringerne til at starte fra**
  - **Afsnittet Simuleringsslut** : Vælge en af følgende værdier:
    - **Vælg den dato, dine simuleringer skal slutte**
    - **Angiv antallet af forekomster af simuleringer, der skal køres før afslutning**: Angiv en værdi fra 1 til 10.

Klik på Næste, når du er **færdig**.

## <a name="launch-details"></a>Startoplysninger

På siden **Start detaljer** skal du konfigurere følgende yderligere indstillinger for automatisering:

- **Brug entydige nyttedata på tværs af simulering i en automatisering**: Denne indstilling er som standard ikke valgt.
- **Destinationen gentages**: Denne indstilling er som standard ikke valgt. Hvis du vælger den, skal du konfigurere følgende indstilling, der vises:
  - **Angiv det maksimale antal gange, en bruger kan målrettes i denne automatisering**: Angiv en værdi fra 1 til 10.
- **Send simuleringsmail baseret på brugerens aktuelle tidszoneindstilling fra Outlook-webapp**: Denne indstilling er som standard ikke valgt.
- **Vis den samlede side for drive-by-tekniske data**: Denne indstilling er kun tilgængelig, hvis du har valgt **Drev efter URL-adresse** på siden **[Vælg social engineering-teknikker](#select-one-or-more-social-engineering-techniques)** . Som standard er indstillingen til (til![/fra-ikon.](../../media/scc-toggle-on.png)).

## <a name="review-simulation-automation"></a>Gennemse simulerings automatisering

På siden **Gennemse automatisering af simulering** kan du gennemgå detaljerne for din simulerings automatisering.

Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

Klik på Send, når du er **færdig**.
