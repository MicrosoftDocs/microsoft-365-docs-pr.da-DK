---
title: Simulere et phishingangreb med kursus i simulering af angreb
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
ms.custom: ''
description: Administratorer kan lære at simulere phishingangreb og træne deres brugere i forebyggelse af phishing ved hjælp af kursus i Microsoft Defender for Office 365 plan 2.
ms.technology: mdo
ms.openlocfilehash: 924fef8e5aba8a797cf6754b6c507624e51a64c2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474305"
---
# <a name="simulate-a-phishing-attack-with-attack-simulation-training-in-defender-for-office-365"></a>Simulere et phishingangreb med kursus i at simulere angreb Defender for Office 365

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Kursus i angrebssimulering Microsoft Defender for Office 365 plan 2 eller Microsoft 365 E5 du køre bengalsk cyberangrebssimulering i din organisation. Disse simulering test dine sikkerhedspolitikker og -fremgangsmåder, samt træn dine medarbejdere til at øge deres opmærksomhed og mindske deres følsomhed over for angreb. I denne artikel kan du se, hvordan du opretter simulerede phishingangreb ved hjælp af simulering af angreb.

Du kan finde oplysninger om kursus i at simulere angreb i [Kom i gang med at bruge simulering af angreb](attack-simulation-training-get-started.md).

Hvis du vil starte et simuleret phishingangreb, skal du gøre følgende:

1. I portalen Microsoft 365 Defender på skal du gå <https://security.microsoft.com>til Mail **og & på** \> fanen **Simulering af** **simulering** \> af samarbejde.

   For at gå direkte til fanen **Simuleringer** skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulations>.

2. På fanen **Simuleringer skal** du vælge Start et ![simuleringsikon.](../../media/m365-cc-sc-create-icon.png) **Start en simulering**.

   :::image type="content" source="../../media/attack-sim-training-simulations-launch.png" alt-text="Knappen Start en simulering under fanen Simulering i Angrebssimulering i Microsoft 365 Defender portal" lightbox="../../media/attack-sim-training-simulations-launch.png":::

3. Guiden til oprettelse af simulering åbnes. Resten af denne artikel beskriver siderne og de indstillinger, de indeholder.

> [!NOTE]
> Under simuleringsguiden kan du når som helst  klikke på Gem og luk for at gemme din status og fortsætte med at konfigurere simulering senere. Den ufuldstændige simulering **har Statusværdien** **Kladde** under **fanen Simuleringer** . Du kan gå til det sted, hvor du slap, ved at vælge simulering og klikke på Rediger simuleringsikon ![.](../../media/m365-cc-sc-edit-icon.png) **Rediger simulering** .

## <a name="select-a-social-engineering-technique"></a>Vælg en social tekniker

På siden **Select technique** skal du vælge en tilgængelig social engineering-teknik, som er blevet curated fra [MITRE ATT&CK framework®](https://attack.mitre.org/techniques/enterprise/). Forskellige nyttedata er tilgængelige for forskellige teknikker. Følgende social engineering-teknikker er tilgængelige:

- **Indsamling af** legitimationsoplysninger: Forsøg på at indsamle legitimationsoplysninger ved at tage brugere til et velkendt udseende websted med inputfelter til at indsende et brugernavn og en adgangskode.
- **Vedhæftet malware**: Føjer en ondsindet vedhæftet fil til en meddelelse. Når brugeren åbner den vedhæftede fil, køres en tilfældig kode, der kan hjælpe hackeren med at kompromittere destinationens enhed.
- **Link i vedhæftet** fil: En type legitimationstagningshybrid. En hacker indsætter en URL-adresse i en vedhæftet fil i en mail. URL-adressen i den vedhæftede fil følger den samme metode som indsamling af legitimationsoplysninger.
- **Link til malware**: Kører en vilkårlig kode fra en fil, der er hostet på en velkendt fildelingstjeneste. Den meddelelse, der sendes til brugeren, indeholder et link til denne skadelige fil. Hvis du åbner filen, kan det hjælpe hackeren med at kompromittere målenheden.
- **Drev efter URL-adresse**: Den skadelige URL-adresse i meddelelsen fører brugeren til et velkendt websted, der uovervåget kører og/eller installerer kode på brugerens enhed.

Hvis du klikker på **linket** Vis detaljer i beskrivelsen, åbnes en pop op-vindue med detaljer, der beskriver den teknik og de simuleringstrin, der er resultatet af metoden.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Pop op-pop op-pop-op-dialogboksen Detaljer for teknik til indsamling af legitimationsoplysninger på siden Vælg teknik" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

Klik på Næste, når du er **færdig**.

## <a name="name-and-describe-the-simulation"></a>Navngive og beskrive simulering

På siden **Name-simulering** skal du konfigurere følgende indstillinger:

- **Navn**: Angiv et entydigt, beskrivende navn til simulering.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse til simulering.

Klik på Næste, når du er **færdig**.

## <a name="select-a-payload"></a>Vælg en nyttedata

På siden **Vælg nyttedata** skal du vælge en eksisterende nyttedata fra listen eller oprette en ny nyttedata.

Følgende oplysninger vises på listen over nyttedata, som du kan bruge til at vælge:

- **Navn**
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
  - **Global** (indbygget)
  - **Lejer** (brugerdefineret)
  - **Alle**
- **Sprog**: De tilgængelige værdier er: kinesisk **(** forenklet), kinesisk **(traditionelt),** **engelsk, fransk****, tysk****, italiensk****, japansk****,** **koreansk****, portugisisk****, russisk****, spansk** og **hollandsk**.
- **Tilføj mærker**
- **Filtrer** efter tema: De tilgængelige værdier **er:** Kontoaktivering **,** Kontobekræftelse **, Fakturering**, Ryd op i **mail****, Dokument** **modtaget, Udgift**, **Fax****,** Økonomirapport **,** Indgående **meddelelser, Faktura****, Modtagne** **elementer,** Logonbesked, **Mail** **modtaget, Adgangskode****, Betaling****, Løn**, Personlig **tilbud**, **Karantæne**, **Fjernarbejde**, Gennemse **meddelelse**, **Sikkerhedsopdatering**, **Afbrudt tjeneste**, **Påkrævet signatur****,** Opgrader postkasselager Bekræft postkasse, **Telefonsvarer** og **Andet**.
- **Filtrer efter mærke**: De tilgængelige værdier er: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, Netflix, **Scotiabank**, **SendGrid**, **title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** og **Andre**. 
- **Filtrer** efter branche: De tilgængelige værdier er: **Bank****,** forretningstjenester **,** forbrugertjenester, **Uddannelse**, **Energi****, Konstruktion**, **Rådgivning**, Finansielle tjenester, **Government**, **Hotel**, **Forsikring**, **Juridiske**, **Courier services**, **IT****,** **Sundhedssektoren, Produktion**, **Retail**, **Telecom**, **Real Estate**, og **Andet**.
- **Aktuel hændelse**: De tilgængelige værdier er **Ja** eller **Nej**.
- **Til** rådighed: De tilgængelige værdier er **Ja** eller **Nej**.

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload.png" alt-text="Siden Vælg nyttedata i angrebssimuleringskursus i Microsoft 365 Defender portal" lightbox="../../media/attack-sim-training-simulations-select-payload.png":::

Hvis du vælger en nyttedata fra listen, vises oplysninger om nyttedata i en pop op-pop-op-pop-op:

- Fanen **Oversigt** indeholder et eksempel og andre oplysninger om nyttedata.
- Fanen **Simulering er** startet indeholder **Simuleringsnavn**, **Klikhastighed**, **Kompromitteret** hastighed og **Handling**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details.png" alt-text="Pop op-siden med oplysninger om nyttedata i angrebssimuleringskursus Microsoft 365 Defender portalen" lightbox="../../media/attack-sim-training-simulations-select-payload-details.png":::

Hvis du vælger en nyttedata fra listen ved at klikke på navnet, så vises ikonet ![Send en test med nyttedata.](../../media/m365-cc-sc-create-icon.png) **Knappen Send en test** vises på hovedsiden, hvor du kan sende en kopi af din nyttedatamail til dig selv (den bruger, der er logget på i øjeblikket) til inspektion.

Hvis du vil oprette din egen nyttelast, skal du ![klikke på Opret et nyttedataikon.](../../media/m365-cc-sc-create-icon.png) **Opret en nyttedata**. Få mere at vide under [Opret brugerdefinerede nyttedata til simulering af angreb.](attack-simulation-training-payloads.md)

Klik på Næste, når du er **færdig**.

## <a name="target-users"></a>Målbrugere

På siden **Målbrugere skal** du vælge, hvem der skal modtage simulering. Konfigurer en af følgende indstillinger:

- **Medtag alle brugere i organisationen**: De berørte brugere vises på lister med 10. Du kan bruge knapperne **Næste** **og Forrige** direkte under listen over brugere til at rulle gennem listen. Du kan også bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgeikon** på siden for at finde de berørte brugere.

- **Medtag kun bestemte brugere og grupper**: Vælg en af følgende indstillinger:
  - ![Ikonet Tilføj brugere.](../../media/m365-cc-sc-create-icon.png) **Tilføj brugere**: I pop **op-dialogboksen Tilføj** brugere, der vises, kan du finde brugere og grupper ud fra følgende kriterier:

    - **Søg efter brugere eller grupper**: I feltet kan du skrive en del af navnet  eller mailadressen på brugeren eller gruppen og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne. Klik på Tilføj x brugere, når **du er færdig**.

      > [!NOTE]
      > Hvis du klikker **på knappen Tilføj filtre** for at vende  tilbage til indstillingerne Filtrer brugere efter kategorier, ryddes alle brugere eller grupper, du har valgt i søgeresultaterne.

    - **Filtrer brugere efter** kategorier: Vælg mellem ingen, nogle eller alle af følgende indstillinger:

      - **Foreslåede brugergrupper**: Vælg mellem følgende værdier:
        - **Alle foreslåede brugergrupper**
        - **Brugere ikke målrettet af en simulering inden for de sidste tre måneder**
        - **Gentag gentagelser**

      - **Brugermærker**: Brugermærker er identifikatorer for bestemte grupper af brugere (f.eks. Prioritetskonti). Du kan finde flere oplysninger [under Brugermærker i Microsoft Defender for Office 365](user-tags.md).

          Brug følgende indstillinger:

        - **Søg**: I ![Ikonet Søg efter brugermærker.](../../media/m365-cc-sc-search-icon.png) **Søg efter brugermærker**, du kan skrive en del af brugermærket og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne.
        - Markér **alle brugermærker**
        - Vælg eksisterende brugermærker.

      - **Afdeling**: Brug følgende indstillinger:
        - **Søg**: Ikonet Søg ![efter afdeling.](../../media/m365-cc-sc-search-icon.png) **Søg efter Afdeling**, du kan skrive en del af værdien for Afdeling og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne.
        - Vælg **hele afdelingen**
        - Vælg eksisterende Afdelingsværdier.

      - **Titel**: Brug følgende indstillinger:
        - **Søg**: I ![ikonet Søg efter titel.](../../media/m365-cc-sc-search-icon.png) **Søg efter titel**, du kan skrive en del af titelværdien og derefter trykke på Enter. Du kan markere nogle eller alle resultaterne.
        - Markér **hele titlen**
        - Vælg eksisterende titelværdier.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Brugerfiltrering på siden Målbrugere i kursus i angrebssimulering på Microsoft 365 Defender portal" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Når du har identificeret dine kriterier, vises de berørte brugere i  sektionen Brugerliste, der vises, hvor du kan vælge nogle eller alle de modtagere, der opdages.

      Når du er færdig, skal du klikke **på Anvend(x)** og derefter klikke på **Tilføj x brugere**.

  Tilbage på hovedsiden **Målbrugere** kan du bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefeltet** for at finde de berørte brugere. Du kan også klikke på ![ikonet Slet brugere.](../../media/m365-cc-sc-search-icon.png) **Slet** for at fjerne bestemte brugere.

- ![Ikonet Importér.](../../media/m365-cc-sc-create-icon.png) **Importér**: I den dialogboks, der åbnes, skal du angive en CSV-fil, der indeholder én mailadresse pr. linje.

  Når du har fundet en CSV-fil, importeres og vises listen over brugere på **siden Målrettede** brugere. Du kan bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgefeltet** for at finde de berørte brugere. Du kan også klikke på ![ikonet Slet målrettede brugere.](../../media/m365-cc-sc-delete-icon.png) **Slet** for at fjerne bestemte brugere.

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

:::image type="content" source="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png" alt-text="Muligheden for at tilføje de anbefalede kurser på siden Træningstildeling i Angrebssimuleringskursus i Microsoft 365 Defender portal" lightbox="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png":::

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

Hvis du ikke vil bruge et kursus, der vises, skal du klikke på Slet ![kursusikon.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Siden Training assignment i Attack-simuleringskursus i Microsoft 365 Defender portal" lightbox="../../media/attack-sim-training-training-assignment.png":::

Klik på Næste, når du er **færdig**.

### <a name="landing-page"></a>Landingsside

På **landingssiden** skal du konfigurere den webside, brugeren bliver ført til, hvis de åbner nyttedata i simulering.

Microsoft-installerede landingssider er tilgængelige på 12 sprog: kinesisk (forenklet), kinesisk (traditionelt), engelsk, fransk, tysk, italiensk, japansk, koreansk, portugisisk, russisk, spansk og hollandsk.

- **Vælg indstillinger for landingssiden**: De tilgængelige værdier er:
  - **Brug Microsofts standardlandingsside**: Dette er standardværdien, der har følgende tilknyttede indstillinger til konfiguration:
    - **Vælg layout til landingssiden**: Vælg en af de tilgængelige skabeloner.
    - **Tilføj logo**: Klik **på Gennemse** for at finde og vælge .png, .jpeg- eller .gif fil. Logostørrelsen bør maksimalt være 210 x 70 for at undgå forvrængning. Klik på Fjern for at fjerne **logoet**.
    - **Føj indikatorer for nyttedata til mail**: Denne indstilling er ikke tilgængelig, hvis du tidligere har valgt vedhæftet **malware** eller **Link til malware** på [siden Vælg](#select-a-social-engineering-technique) teknik.

    Du kan få vist resultaterne ved at klikke **på knappen Åbn panelet** Vis udskrift nederst på siden.

  - **Brug en brugerdefineret URL-adresse**: Denne indstilling er ikke tilgængelig, hvis du tidligere har valgt **vedhæftet malware** eller **Link til malware** på [siden Vælg](#select-a-social-engineering-technique) teknik.

    Hvis du vælger **Brug en brugerdefineret URL-adresse**, skal du tilføje URL-adressen i feltet Angiv den brugerdefinerede **URL-adresse til landingssiden** , der vises. Der er ingen andre indstillinger tilgængelige på siden.

  - **Opret din egen landingsside**: Denne værdi har følgende tilknyttede indstillinger for konfiguration:
    - **Føj indikatorer for nyttedata til mail**: Denne indstilling er kun tilgængelig, hvis begge af følgende betingelser er sande:
      - Du har tidligere **valgt indsamling af legitimationsoplysninger**, **Link i** vedhæftet fil **eller Drive-by URL** på [siden Udvælgelsesteknik](#select-a-social-engineering-technique) .
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
        - **Brug som standard**: Vælg en tilgængelig skabelon til at starte med. Du kan ændre teksten og layoutet i redigeringsområdet. Hvis du vil nulstille landingssiden til skabelonens standardtekst og -layout, skal du klikke på **Nulstil til standard**.
    - **Kode**: Du kan få vist og redigere HTML-koden direkte.

    Du kan få vist resultaterne ved at klikke **på knappen Åbn** panelet Vis udskrift midt på siden.

Klik på Næste, når du er **færdig**.

> [!NOTE]
> Visse varemærker, logoer, symboler, insignias og andre kildeidentifikatorer får en bedre beskyttelse i henhold til lokale, statslige og føderale love. Uautoriseret brug af sådanne indikatorer kan gøre det ulovligt for brugerne, herunder kriminelle fines. Selvom det ikke er en omfattende liste, omfatter dette selektorer, FYSyd, Vice- og Menhedske sæler, CIA, SOCIAL Security, Medicare og Medicaid, USA Internal Revenue Service og OL. Ud over disse kategorier af varemærker har anvendelse og ændring af tredjeparts varemærker en forbundet risiko. Det vil være mindre risikabelt at anvende dine egne varemærker og logoer i en nyttelast, især hvis din organisation tillader brug. Hvis du har yderligere spørgsmål om, hvad der er eller ikke er relevant at bruge, når du opretter eller konfigurerer en nyttedata, skal du rådføre dig med dine juridiske rådgivere.

## <a name="select-end-user-notification"></a>Vælg meddelelse til slutbruger

På siden **Vælg besked til slutbruger** skal du vælge mellem følgende meddelelsesindstillinger:

- **Levér ikke meddelelser**: Klik **på Fortsæt** i den dialogboks, der vises. Hvis du vælger denne indstilling, kommer du til siden Start detaljer [,](#launch-details) når du klikker på **Næste**.

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

  Hvis du vælger denne indstilling, kommer du til siden Start detaljer [,](#launch-details) når du klikker på **Næste**.

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

## <a name="launch-details"></a>Startoplysninger

På siden **Start detaljer skal** du vælge, hvornår simulering skal startes, og hvornår simulering skal afsluttes. Vi holder op med at registrere interaktion med denne simulering efter den slutdato, du angiver.

Der findes følgende tilgængelige indstillinger:

- Vælg en af følgende værdier:
  - **Start denne simulering, så snart jeg er færdig**
  - **Planlæg denne simulering til at blive startet** senere: Denne værdi har følgende tilknyttede indstillinger for konfiguration:
    - **Vælg startdato**
    - **Vælg starttid**
- **Konfigurer antallet af dage, der skal afsluttes simulering efter**: Standardværdien er 2.
- **Aktivér levering af område-klar tidszone**: Levere simulerede angrebsmeddelelser til dine medarbejdere i løbet af deres arbejdstid baseret på deres område.
- **Vise den forbundne drive-by-teknik for indsamlede data**: Du kan vise den overlejring, der vises for drive-bu URL-teknikangreb. Hvis du vil skjule overlejringen og gå direkte til landingssiden, skal du fravælge denne indstilling.

Klik på Næste, når du er **færdig**.

## <a name="review-simulation"></a>Gennemse simulering

På siden **Gennemse simulering** kan du gennemse detaljerne for din simulering.

Klik på ![ikonet Send en test.](../../media/m365-cc-sc-send-icon.png) **Send en testknap** for at sende en kopi af nyttedatamailen til dig selv (den bruger, der er logget på i øjeblikket) for undersøgelse.

Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

Klik på Send, når du er **færdig**.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Siden Gennemse simulering i angrebssimulering i Microsoft 365 Defender portalen" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::
