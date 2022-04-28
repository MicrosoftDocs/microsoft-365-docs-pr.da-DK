---
title: Simuler et phishingangreb med kursus i angrebssimulering
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
description: Administratorer kan få mere at vide om, hvordan de simulerer phishingangreb og oplærer deres brugere i forebyggelse af phishing ved hjælp af oplæring i simulering af angreb i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 94e002adf3fcdefcb3d2483f4f32ce7b10be8dab
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077644"
---
# <a name="simulate-a-phishing-attack-with-attack-simulation-training-in-defender-for-office-365"></a>Simuler et phishing-angreb med oplæring i simulering af angreb i Defender for Office 365

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Træning i simulering af angreb i Microsoft Defender for Office 365 Plan 2 eller Microsoft 365 E5 giver dig mulighed for at køre godartede simuleringer af cyberangreb i din organisation. Disse simuleringer tester dine sikkerhedspolitikker og -praksisser samt oplærer dine medarbejdere til at øge deres bevidsthed og mindske deres følsomhed over for angreb. I denne artikel gennemgår vi, hvordan du opretter et simuleret phishing-angreb ved hjælp af oplæring i simulering af angreb.

Du kan finde oplysninger om, hvordan du kommer i gang, om oplæring i simulering af angreb under [Kom i gang med at bruge oplæring i simulering af angreb](attack-simulation-training-get-started.md).

Benyt følgende fremgangsmåde for at starte et simuleret phishing-angreb:

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til fanen **Mail & samarbejde** \> **Oplæring** \> **i simulering af angreb Simulering**.

   Hvis du vil gå direkte til fanen **Simuleringer** , skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulations>.

2. På fanen **Simuleringer** skal du vælge ![Start et simuleringsikon.](../../media/m365-cc-sc-create-icon.png) **Start en simulering**.

   :::image type="content" source="../../media/attack-sim-training-simulations-launch.png" alt-text="Knappen Start en simulering på fanen Simuleringer i Oplæring af angrebssimulering på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-launch.png":::

3. Guiden til oprettelse af simulering åbnes. I resten af denne artikel beskrives siderne og de indstillinger, de indeholder.

> [!NOTE]
> Når som helst under guiden til oprettelse af simulering kan du klikke på **Gem og luk** for at gemme dine fremskridt og fortsætte med at konfigurere simuleringen senere. Den ufuldstændige simulering har **statusværdien** **Kladde** under fanen **Simuleringer** . Du kan fortsætte, hvor du slap, ved at vælge simuleringen og klikke på ![Rediger simuleringsikon.](../../media/m365-cc-sc-edit-icon.png) **Rediger** simulering.

## <a name="select-a-social-engineering-technique"></a>Vælg en teknik til social engineering

På siden **Select technique** skal du vælge en tilgængelig social engineering-teknik, som blev udvalgt fra [MITRE ATT-&CK-strukturen®](https://attack.mitre.org/techniques/enterprise/). Der findes forskellige nyttedata til forskellige teknikker. Følgende teknikker til social engineering er tilgængelige:

- **Høst af legitimationsoplysninger**: Forsøger at indsamle legitimationsoplysninger ved at tage brugerne til et velkendt websted med inputfelter for at indsende et brugernavn og en adgangskode.
- **Vedhæftet malware**: Føjer en skadelig vedhæftet fil til en meddelelse. Når brugeren åbner den vedhæftede fil, køres der vilkårlig kode, der hjælper hackeren med at kompromittere målets enhed.
- **Link i vedhæftet fil**: En type af legitimationsoplysninger høst hybrid. En hacker indsætter en URL-adresse i en vedhæftet fil i en mail. URL-adressen i den vedhæftede fil følger samme teknik som høst af legitimationsoplysninger.
- **Link til malware**: Kører vilkårlig kode fra en fil, der hostes på en velkendt fildelingstjeneste. Den meddelelse, der sendes til brugeren, indeholder et link til denne skadelige fil. Hvis du åbner filen, hjælper det hackeren med at kompromittere målets enhed.
- **Drive-by URL**: Den skadelige URL-adresse i meddelelsen fører brugeren til et velkendt websted, der uovervåget kører og/eller installerer kode på brugerens enhed.

Hvis du klikker på linket **Vis detaljer** i beskrivelsen, åbnes der et pop op-vindue med detaljer, der beskriver teknikken og de simuleringstrin, der er resultatet af teknikken.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Pop op-vinduet Detaljer for teknikken til indsamling af legitimationsoplysninger på siden Vælg teknik" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

Klik på **Næste**, når du er færdig.

## <a name="name-and-describe-the-simulation"></a>Navngiv og beskriv simuleringen

Konfigurer følgende indstillinger på siden **Navnesimulering** :

- **Navn**: Angiv et entydigt, beskrivende navn til simuleringen.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af simuleringen.

Klik på **Næste**, når du er færdig.

## <a name="select-a-payload"></a>Vælg en nyttedata

På siden **Vælg nyttedata** skal du vælge en eksisterende nyttedata på listen eller oprette en ny nyttedata.

Følgende oplysninger vises på listen over nyttedata, som du kan bruge til at vælge:

- **Navn på nyttedata**
- **Sprog**: Sproget for nyttedataindholdet. Microsofts payload-katalog (global) leverer nyttedata på mere end 10 sprog, som også kan filtreres.
- **Klikfrekvens**: Hvor mange personer der har klikket på denne nyttedata.
- **Forudsagt kompromisrate**: Historiske data for nyttedataene på tværs af Microsoft 365, der forudsiger procentdelen af personer, der kompromitteres af denne nyttedata.
- **De startede simuleringer** tæller antallet af gange, denne nyttedata blev brugt i andre simuleringer.

På ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **I søgefeltet** kan du skrive en del af navnet på nyttedata og trykke på Enter for at filtrere resultaterne.

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Kilde**: Angiver, om nyttedataene blev oprettet i din organisation eller er en del af Microsofts eksisterende nyttedatakatalog. Gyldige værdier er:
  - **Global** (indbygget)
  - **Lejer** (brugerdefineret)
  - **Alle**

- **Kompleksitet**: Beregnet på baggrund af antallet af indikatorer i nyttedataene, der angiver et muligt angreb (stavefejl, uopsættelighed osv.). Flere indikatorer er nemmere at identificere som et angreb og angive lavere kompleksitet. De tilgængelige værdier er:
  - **Lav**
  - **Medium**
  - **Høj**

- **Sprog**: De tilgængelige værdier er: **kinesisk (forenklet),****kinesisk (traditionelt),****engelsk**, **fransk**, **tysk**, **italiensk**, **japansk**, **koreansk**, **portugisisk**, **russisk**, **spansk** og **hollandsk**.

- **Tilføj kode(r)**

- **Filtrer efter tema**: De tilgængelige værdier er: **Kontoaktivering**, **Kontobekræftelse**, **Fakturering**, **Ryd op i mail**, **Modtaget dokument**, **Udgift**, **Fax**, **Økonomirapport**, **Indgående meddelelser**, **Faktura**, **Modtagne elementer**, **Logonbesked**, **Post modtaget**, **Adgangskode**, **Betaling**, **Løn**, **Personligt tilbud**, **Karantæne**, **Fjernarbejde**, **Gennemse meddelelse**, **Sikkerhedsopdatering**, **Afbrudt tjeneste**, **Signatur påkrævet**, **Lager til opgradering af postkasse Bekræft postkasse**, **Voicemail** og **Andet**.

- **Filtrer efter brand**: De tilgængelige værdier er: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** og **Andet**.

- **Filtrer efter branche**: De tilgængelige værdier er: **Banking**, **Business services**, **Consumer services**, **Education**, **Energy**, **Construction**, **Consulting**, **Financial services**, **Government**, **Hospitality**, **Insurance**, **Legal**, **Courier services**, **IT**, **Healthcare**, **Manufacturing**, **Retail**, **Telecom**, **Real estate**, og **Andet**.

- **Aktuel hændelse**: De tilgængelige værdier er **Ja** eller **Nej**.

- **Kontroversiel**: De tilgængelige værdier er **Ja** eller **Nej**.

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload.png" alt-text="Siden Vælg nyttedata i Oplæring af simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload.png":::

Hvis du vælger en nyttedata på listen, vises oplysninger om nyttedataene i et pop op-vindue:

- Fanen **Oversigt** indeholder et eksempel og andre oplysninger om nyttedataene.
- Fanen **Simuleringer, der startes** , indeholder **simuleringsnavnet**, **klikfrekvensen**, **kompromitteret hastighed** og **handling**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details.png" alt-text="Pop op-vinduet Med oplysninger om nyttedata i oplæringen af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-select-payload-details.png":::

Hvis du vælger en nyttedata på listen ved at klikke på navnet, skal du klikke på ikonet ![Send en test nyttedata.](../../media/m365-cc-sc-create-icon.png) **Send en testknap** vises på hovedsiden, hvor du kan sende en kopi af nyttedatamailen til dig selv (den bruger, der aktuelt er logget på) til inspektion.

Hvis du vil oprette din egen nyttedata, skal du klikke på ![Opret et nyttedataikon.](../../media/m365-cc-sc-create-icon.png) **Opret en nyttedata**. Du kan få flere oplysninger under [Opret brugerdefinerede nyttedata til oplæring af simulering af angreb](attack-simulation-training-payloads.md).

Klik på **Næste**, når du er færdig.

## <a name="target-users"></a>Destinationsbrugere

På siden **Målbrugere** skal du vælge, hvem der skal modtage simuleringen. Konfigurer en af følgende indstillinger:

- **Medtag alle brugere i din organisation**: De berørte brugere vises på lister over 10. Du kan bruge knapperne **Næste** og **Forrige** direkte under listen over brugere til at rulle gennem listen. Du kan også bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgeikon** på siden for at finde berørte brugere.

- **Medtag kun bestemte brugere og grupper**: Vælg en af følgende indstillinger:
  - ![Ikonet Tilføj brugere.](../../media/m365-cc-sc-create-icon.png) **Tilføj brugere**: I pop op-vinduet **Tilføj brugere** , der vises, kan du finde brugere og grupper ud fra følgende kriterier:

    - **Søg efter brugere eller grupper**: I feltet kan du skrive en del af **brugerens** eller gruppens navn eller **mailadresse** og derefter trykke på Enter. Du kan vælge nogle af eller alle resultaterne. Når du er færdig, skal du klikke på **Tilføj x-brugere**.

      > [!NOTE]
      > Hvis du klikker på knappen **Tilføj filtre** for at vende tilbage til indstillingerne **Filtrer brugere efter kategorier** , ryddes alle de brugere eller grupper, du har valgt i søgeresultaterne.

    - **Filtrer brugere efter kategorier**: Vælg mellem ingen, nogle eller alle af følgende indstillinger:

      - **Foreslåede brugergrupper**: Vælg mellem følgende værdier:
        - **Alle foreslåede brugergrupper**
        - **Brugere, der ikke er målrettet mod en simulering inden for de sidste tre måneder**
        - **Gentag lovovertrædere**

      - **Brugerkoder**: Brugerkoder er identifikatorer for bestemte grupper af brugere (f.eks. prioritetskonti). Du kan få flere oplysninger [under Brugerkoder i Microsoft Defender for Office 365](user-tags.md).

          Brug følgende indstillinger:

        - **Søg**: Ikonet ![Søg efter brugerkoder.](../../media/m365-cc-sc-search-icon.png) **Søg efter brugerkoder**. Du kan skrive en del af brugerkoden og derefter trykke på Enter. Du kan vælge nogle af eller alle resultaterne.
        - Vælg **alle brugerkoder**
        - Vælg eksisterende brugerkoder.

      - **Afdeling**: Brug følgende indstillinger:
        - **Søg**: Ikonet ![Søg efter afdeling.](../../media/m365-cc-sc-search-icon.png) **Søg efter afdeling**. Du kan dele værdien Afdeling og derefter trykke på Enter. Du kan vælge nogle af eller alle resultaterne.
        - Vælg **alle afdelinger**
        - Vælg eksisterende afdelingsværdier.

      - **Titel**: Brug følgende indstillinger:
        - **Søg**: Ikonet ![Søg efter titel.](../../media/m365-cc-sc-search-icon.png) **Søg efter titel**. Du kan skrive en del af værdien Titel og derefter trykke på Enter. Du kan vælge nogle af eller alle resultaterne.
        - Markér **al titel**
        - Vælg eksisterende titelværdier.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Brugerfiltrering på siden Målbrugere i oplæringen af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Når du har identificeret dine kriterier, vises de berørte brugere i afsnittet **Brugerliste** , der vises, hvor du kan vælge nogle eller alle de registrerede modtagere.

      Når du er færdig, skal du klikke på **Anvend(x)** og derefter klikke på **Tilføj x-brugere**.

  Tilbage på den primære side **Målbrugere** kan du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at finde berørte brugere. Du kan også klikke på ![ikonet Slet brugere.](../../media/m365-cc-sc-search-icon.png) **Slet** for at fjerne bestemte brugere.

- ![Ikonet Importér.](../../media/m365-cc-sc-create-icon.png) **Import:** I den dialogboks, der åbnes, skal du angive en CSV-fil, der indeholder én mailadresse pr. linje.

  Når du har fundet en markering af CSV-filen, importeres listen over brugere og vises på siden **Målrettede brugere** . Du kan bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at finde berørte brugere. Du kan også klikke på ![ikonet Slet målrettede brugere.](../../media/m365-cc-sc-delete-icon.png) **Slet** for at fjerne bestemte brugere.

Klik på **Næste**, når du er færdig.

## <a name="assign-training"></a>Tildel oplæring

På siden **Tildel oplæring** kan du tildele oplæringer til simuleringen. Vi anbefaler, at du tildeler træning til hver simulering, da medarbejdere, der gennemgår træningen, er mindre sårbare over for lignende angreb. Følgende indstillinger er tilgængelige:

- **Vælg indstillinger for oplæringsindhold**: Vælg en af følgende indstillinger:
  - **Microsofts træningsoplevelse**: Dette er den standardværdi, der har følgende tilknyttede indstillinger, der skal konfigureres:
    - Vælg en af følgende indstillinger:
      - **Tildel oplæring for mig**: Dette er standardværdien og den anbefalede værdi. Vi tildeler oplæring baseret på en brugers tidligere simulerings- og oplæringsresultater, og du kan gennemse valgene i de næste trin i guiden.
      - **Vælg selv kurser og moduler**: Hvis du vælger denne værdi, kan du stadig se det anbefalede indhold samt alle tilgængelige kurser og moduler i næste trin i guiden.
    - **Forfaldsdato**: Vælg en af følgende værdier:
      - **30 dage efter, at simuleringen slutter**: Dette er standardværdien.
      - **15 dage efter simulering slutter**
      - **7 dage efter simulering slutter**
  - **Omdiriger til en brugerdefineret URL-adresse**: Denne værdi har følgende tilknyttede indstillinger, der skal konfigureres:
    - **URL-adresse til brugerdefineret oplæring** (påkrævet)
    - **Navn på brugerdefineret oplæring** (påkrævet)
    - **Beskrivelse af brugerdefineret oplæring**
    - **Varighed af brugerdefineret oplæring (i minutter):** Standardværdien er 0, hvilket betyder, at der ikke er angivet en bestemt varighed for oplæringen.
    - **Forfaldsdato**: Vælg en af følgende værdier:
      - **30 dage efter, at simuleringen slutter**: Dette er standardværdien.
      - **15 dage efter simulering slutter**
      - **7 dage efter simulering slutter**
  - **Ingen oplæring**: Hvis du vælger denne værdi, er den eneste indstilling på siden knappen **Næste** , der fører dig til [**landingssiden**](#landing-page) .

:::image type="content" source="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png" alt-text="Muligheden for at tilføje den anbefalede oplæring på siden Oplæringstildeling i Oplæringssimulering på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png":::

### <a name="training-assignment"></a>Oplæringstildeling

> [!NOTE]
> Siden **Oplæringstildeling** er kun tilgængelig, hvis du har valgt **Microsofts træningsoplevelse** \> **Vælg kurser og moduler mig selv** på den forrige side.

På siden **Oplæringstildeling** skal du vælge de oplæringer, du vil føje til simuleringen, ved at klikke på ![Ikonet Tilføj oplæringer.](../../media/m365-cc-sc-create-icon.png) **Tilføj oplæringer**.

I pop op-vinduet **Tilføj oplæring** , der vises, kan du vælge de kurser, der skal bruges, på følgende faner, der er tilgængelige:

- **Anbefalet** fane: Viser de anbefalede indbyggede kurser baseret på simuleringskonfigurationen. Det er de samme kurser, som ville være blevet tildelt, hvis du valgte **Tildel oplæring for mig på den forrige** side.
- **Fanen Alle oplæringer** : Viser alle indbyggede kurser, der er tilgængelige.

  Følgende oplysninger vises for hver oplæring:

  - **Oplæringsnavn**
  - **Kilde**: Værdien er **Global**.
  - **Varighed (minutter)**
  - **Eksempel**: Klik på knappen **Eksempel** for at se oplæringen.

  På ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **I søgefeltet** kan du skrive en del af oplæringsnavnet og trykke på Enter for at filtrere resultaterne under den aktuelle fane.

  Vælg alle de kurser, du vil medtage, under den aktuelle fane, og klik derefter på **Tilføj**.

Tilbage på hovedsiden **Oplæringstildeling** vises de oplæringer, du har valgt. Følgende oplysninger vises for hver oplæring:

- **Oplæringsnavn**
- **Kilde**
- **Varighed (minutter)**

For hver oplæring på listen skal du vælge, hvem der får oplæringen, ved at vælge værdier i kolonnen **Tildel til** :

- **Alle brugere**

  eller en eller begge af følgende værdier:

- **Nyttedata, der er klikket på**
- **Kompromitteret**

Hvis du ikke vil bruge en oplæring, der vises, skal du klikke på ![Slet oplæringsikon.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Siden Oplæringstildeling i Oplæring i simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-training-training-assignment.png":::

Klik på **Næste**, når du er færdig.

### <a name="landing-page"></a>Destinationsside

På **landingssiden** kan du konfigurere den webside, som brugeren sendes til, hvis brugeren åbner nyttedataene i simuleringen.

Microsoft-organiserede landingssider er tilgængelige på 12 sprog: kinesisk (forenklet), kinesisk (traditionelt), engelsk, fransk, tysk, italiensk, japansk, koreansk, portugisisk, russisk, spansk og hollandsk.

- **Vælg indstillinger for landingsside**: De tilgængelige værdier er:
  - **Brug Microsofts standardlandingsside**: Dette er den standardværdi, der har følgende tilknyttede indstillinger, der skal konfigureres:
    - **Vælg landingssidelayout**: Vælg en af de tilgængelige skabeloner.
    - **Tilføj logo**: Klik på **Gennemse** for at finde og vælge en .png-, .jpeg- eller .gif-fil. Logostørrelsen må højst være 210 x 70 for at undgå forvrængning. Klik på **Fjern** for at fjerne logoet.
    - **Føj nyttedataindikatorer til mail**: Denne indstilling er ikke tilgængelig, hvis du tidligere har valgt **Vedhæftet malware** eller **Link til malware** på siden [Vælg teknik](#select-a-social-engineering-technique) .

    Du kan få vist resultaterne ved at klikke på knappen **Åbn eksempelpanel** nederst på siden.

  - **Brug en brugerdefineret URL-adresse**: Denne indstilling er ikke tilgængelig, hvis du tidligere har valgt **Vedhæftet malware** eller **Link til malware** på siden [Vælg teknik](#select-a-social-engineering-technique) .

    Hvis du vælger **Brug en brugerdefineret URL-adresse**, skal du tilføje URL-adressen i feltet **Angiv url-adressen til den brugerdefinerede landingsside** , der vises. Der er ingen andre indstillinger tilgængelige på siden.

  - **Opret din egen landingsside**: Denne værdi har følgende tilknyttede indstillinger, der skal konfigureres:
    - **Føj nyttedataindikatorer til mail**: Denne indstilling er kun tilgængelig, hvis begge af følgende betingelser er opfyldt:
      - Du har tidligere valgt **Høst af legitimationsoplysninger**, **Link i vedhæftet fil** eller **URL-adresse til kørsel** på siden [Vælg teknik](#select-a-social-engineering-technique) .
      - Når du har føjet det **dynamiske mærke** med navnet **Indsæt mailindhold** til sideindholdet.

    - Sideindhold: To faner er tilgængelige:
      - **Tekst**: Der findes en RTF-editor, som du kan bruge til at oprette landingssiden. Ud over de almindelige skrifttype- og formateringsindstillinger er følgende indstillinger tilgængelige:
        - **Dynamisk mærke**: Vælg mellem følgende mærker:
          - **Indsæt navn**
          - **Indsæt afsendernavn**
          - **Indsæt afsendermail**
          - **Indsæt mailemne**
          - **Indsæt mailindhold**
          - **Indsæt dato**
        - **Brug fra standard**: Vælg en tilgængelig skabelon, du vil starte med. Du kan redigere teksten og layoutet i redigeringsområdet. Klik på **Nulstil til standard** for at nulstille landingssiden til standardteksten og layoutet for skabelonen.
    - **Kode**: Du kan få vist og redigere HTML-koden direkte.

    Du kan få vist resultaterne ved at klikke på knappen **Åbn eksempelpanel** midt på siden.

Klik på **Næste**, når du er færdig.

> [!NOTE]
> Visse varemærker, logoer, symboler, insignier og andre kilde-id'er modtager øget beskyttelse i henhold til lokale, statslige og føderale love og love. Uautoriseret brug af sådanne indikatorer kan straffe brugerne, herunder bøder. Men ikke en omfattende liste, dette omfatter præsidentielle, vice præsidentielle og Kongres sæler, CIA, FBI, Social Security, Medicare og Medicaid, USA Internal Revenue Service, og de olympiske lege. Ud over disse kategorier af varemærker indebærer brug og ændring af et tredjepartsmærke en indbygget risiko. Det vil være mindre risikabelt at bruge dine egne varemærker og logoer i en nyttedata, især hvor din organisation tillader brugen. Hvis du har yderligere spørgsmål om, hvad der er eller ikke er hensigtsmæssigt at bruge, når du opretter eller konfigurerer en nyttedata, bør du kontakte dine juridiske rådgivere.

## <a name="select-end-user-notification"></a>Vælg slutbrugermeddelelse

På siden **Vælg slutbrugermeddelelse** skal du vælge mellem følgende meddelelsesindstillinger:

- **Levér ikke meddelelser**: Klik på **Fortsæt** i den dialogboks med beskeder, der vises. Hvis du vælger denne indstilling, føres du til siden [Start detaljer](#launch-details) , når du klikker på **Næste**.

- **Microsofts standardmeddelelse (anbefales):** Følgende yderligere indstillinger er tilgængelige på siden:

  - **Vælg standardsprog**: De tilgængelige værdier er: **kinesisk (forenklet),** **kinesisk (traditionelt),** **engelsk**, **fransk**, **tysk**, **italiensk**, **japansk**, **koreansk**, **portugisisk**, **russisk**, **spansk** og **hollandsk**.

  - Følgende meddelelser er som standard inkluderet:
    - **Meddelelse om positiv forstærkning fra Microsoft**
    - **Microsofts standardmeddelelse om oplæringstildeling**
    - **Besked om påmindelse om standardtræning fra Microsoft**

    For hver meddelelse er følgende oplysninger tilgængelige:
    - **Meddelelser**: Navnet på meddelelsen.
    - **Sprog**: Hvis meddelelsen indeholder flere oversættelser, vises de første to sprog direkte. Hvis du vil se de resterende sprog, skal du holde markøren over det numeriske ikon (f.eks. **+10**).
    - **Type**: En af følgende værdier:
      - **Meddelelse om positiv forstærkning**
      - **Meddelelse om oplæringstildeling**
      - **Påmindelse om oplæring**
    - **Leveringspræferencer**: Følgende værdier er tilgængelige for **meddelelsestyper for positiv forstærkning** og **påmindelse om oplæring**
      - **Levér ikke**
      - **Levér, når kampagnen slutter**
      - **Levér under kampagnen**
    - **Handlinger**: Hvis du klikker på ikonet ![Vis.](../../media/m365-cc-sc-view-icon.png) **Ikonet Vis** , siden **Gennemse meddelelse** vises med følgende oplysninger:
      - **Fanen Eksempel** : Få vist meddelelsesmeddelelsen.
        - Hvis du vil have vist meddelelsen på forskellige sprog, skal du bruge feltet **Vælg sprog** .
        - Brug feltet **Vælg nyttedata til eksempelvisning** til at vælge meddelelsesmeddelelsen til simuleringer, der indeholder flere nyttedata.
      - Fanen **Detaljer**: Få vist detaljer om meddelelsen:
        - **Meddelelsesbeskrivelse**
        - **Kilde**: For indbyggede meddelelser er værdien **Global**. For brugerdefinerede meddelelser er værdien **Lejer**.
        - **Meddelelsestype**: En af følgende typer baserer sig på den meddelelse, du oprindeligt valgte:
          - **Meddelelse om positiv forstærkning**
          - **Meddelelse om oplæringstildeling**
          - **Påmindelse om oplæring**
        - **Ændret af**
        - **Senest ændret**

        Klik på **Luk**, når du er færdig.

  Du føres til siden [Start detaljer](#launch-details) , når du klikker på **Næste**.

- **Tilpassede slutbrugermeddelelser**: Når du klikker på **Næste**, føres du til siden **Med meddelelser om oplæringstildeling** , som beskrevet i de næste afsnit.

### <a name="training-assignment-notification"></a>Meddelelse om oplæringstildeling

Meddelelsessiden **Oplæringstildeling** er kun tilgængelig, hvis du har valgt **Tilpassede slutbrugermeddelelser** på siden **[Vælg slutbrugermeddelelse](#select-end-user-notification)** .

På denne side vises følgende meddelelser og deres konfigurerede sprog:

- **Microsofts standardmeddelelse om oplæringstildeling**
- Alle brugerdefinerede meddelelser om oplæringstildeling, som du tidligere har oprettet.

  Disse meddelelser er også tilgængelige på fanen **Slutbrugermeddelelser** under Oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>. **Microsofts standardmeddelelse om oplæringstildeling** er tilgængelig på fanen **Globale meddelelser** . Meddelelser om brugerdefinerede oplæringstildelinger er tilgængelige under fanen **Lejermeddelelser** . Du kan få flere oplysninger under [Slutbrugermeddelelser om oplæring i simulering af angreb](attack-simulation-training-end-user-notifications.md).

Du kan vælge en eksisterende meddelelse om oplæringstildeling eller oprette en ny meddelelse, der skal bruges:

- Hvis du vil vælge en eksisterende meddelelse, skal du klikke i det tomme område ud for meddelelsesnavnet. Hvis du klikker på meddelelsesnavnet, vælges meddelelsen, og der vises et eksempel. Hvis du vil fjerne markeringen af meddelelsen, skal du fjerne markeringen i afkrydsningsfeltet ud for meddelelsen.
- Hvis du vil søge efter en eksisterende meddelelse, skal du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** for at søge efter navnet.

  Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

- Klik på ![Opret nyt ikon for at oprette og bruge en ny meddelelse.](../../media/m365-cc-sc-create-icon.png) **Opret ny**.

#### <a name="create-new-training-assignment-notification-wizard"></a>Guiden Opret meddelelse om ny oplæringstildeling

Hvis du har klikket ![på Ikonet Opret ny.](../../media/m365-cc-sc-create-icon.png) **Opret ny** på **meddelelsessiden Oplæringstildeling** . Der åbnes en guide til oprettelse af meddelelser.

Oprettelsestrinnene er identiske som beskrevet i [Opret slutbrugermeddelelser](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> På siden **Definer detaljer** skal du sørge for at vælge **meddelelsen Oplæringstildeling** for **Vælg meddelelsestype**.

Når du er færdig, føres du tilbage til **meddelelsessiden Oplæringstildeling** , hvor den meddelelse, du netop har oprettet, vises på listen.

Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

### <a name="training-reminder-notification"></a>Påmindelse om oplæring

Meddelelsessiden **Påmindelse om oplæring** er kun tilgængelig, hvis du har valgt **Tilpassede slutbrugermeddelelser** på siden **[Vælg slutbrugermeddelelse](#select-end-user-notification)** .

- **Angiv hyppighed for påmindelsesmeddelelse**: Vælg **Ugentligt** (standard) eller **To gange om ugen**.

- **Vælg en påmindelsesmeddelelse**: I dette afsnit vises følgende meddelelser og deres konfigurerede sprog:

  - **Besked om påmindelse om standardtræning fra Microsoft**
  - Alle brugerdefinerede påmindelsesmeddelelser om oplæring, som du tidligere har oprettet.

    Disse meddelelser er også tilgængelige på fanen **Slutbrugermeddelelser** under Oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>. **Påmindelsesmeddelelse om Microsofts standardtræning** er tilgængelig på fanen **Globale meddelelser** . Påmindelsesmeddelelser om brugerdefineret oplæring er tilgængelige under fanen **Lejermeddelelser** . Du kan få flere oplysninger under [Slutbrugermeddelelser om oplæring i simulering af angreb](attack-simulation-training-end-user-notifications.md).

  Du kan vælge en eksisterende påmindelse om oplæring eller oprette en ny meddelelse, der skal bruges:

  - Hvis du vil vælge en eksisterende meddelelse, skal du klikke i det tomme område ud for meddelelsesnavnet. Hvis du klikker på meddelelsesnavnet, vælges meddelelsen, og der vises et eksempel. Hvis du vil fjerne markeringen af meddelelsen, skal du fjerne markeringen i afkrydsningsfeltet ud for meddelelsen.
  - Hvis du vil søge efter en eksisterende meddelelse, skal du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** for at søge efter navnet.

    Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

  - Klik på ![Opret nyt ikon for at oprette og bruge en ny meddelelse.](../../media/m365-cc-sc-create-icon.png) **Opret ny**.

#### <a name="create-new-training-reminder-notification-wizard"></a>Guiden Opret en ny påmindelse om oplæring

Hvis du har klikket ![på Ikonet Opret ny.](../../media/m365-cc-sc-create-icon.png) **Opret ny** på meddelelsessiden **Påmindelse om oplæring** . Der åbnes en guide til oprettelse af meddelelser.

Oprettelsestrinnene er identiske som beskrevet i [Opret slutbrugermeddelelser](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> På siden **Definer detaljer** skal du sørge for at vælge **påmindelsesmeddelelsen Oplæring** for **Vælg meddelelsestype**.

Når du er færdig, føres du tilbage til siden med **påmindelse om oplæring** , hvor den meddelelse, du netop har oprettet, vises på listen.

Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

### <a name="positive-reinforcement-notification"></a>Meddelelse om positiv forstærkning

Meddelelsessiden **Positiv forstærkning** er kun tilgængelig, hvis du har valgt **Tilpassede slutbrugermeddelelser** på siden **[Vælg slutbrugermeddelelse](#select-end-user-notification)** .

- **Leveringspræferencer**: Vælg en af følgende værdier:

  - **Levér ikke**: Hvis du vælger denne indstilling, føres du til siden [Start oplysninger](#launch-details) , når du klikker på **Næste**.

  - **Levér, når brugeren rapporterer en phish og kampagne slutter** eller **Levér umiddelbart efter brugeren rapporterer en phish**: I disse afsnit vises følgende meddelelser og deres konfigurerede sprog i afsnittet **Vælg en meddelelse om positiv forstærkning** , der vises:

  - **Microsofts standardmeddelelse om positiv forstærkning**
  - Alle brugerdefinerede meddelelser om positiv forstærkning, som du tidligere har oprettet.

    Disse meddelelser er også tilgængelige på fanen **Slutbrugermeddelelser** under Oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=endUserNotification>. **Microsofts standardmeddelelse om positiv forstærkning** er tilgængelig på fanen **Globale meddelelser** . Brugerdefinerede meddelelser om positiv forstærkning er tilgængelige på fanen **Lejermeddelelser** . Du kan få flere oplysninger under [Slutbrugermeddelelser om oplæring i simulering af angreb](attack-simulation-training-end-user-notifications.md).

  Du kan vælge en eksisterende meddelelse om positiv forstærkning eller oprette en ny meddelelse, der skal bruges:

  - Hvis du vil vælge en eksisterende meddelelse, skal du klikke i det tomme område ud for meddelelsesnavnet. Hvis du klikker på meddelelsesnavnet, vælges meddelelsen, og der vises et eksempel. Hvis du vil fjerne markeringen af meddelelsen, skal du fjerne markeringen i afkrydsningsfeltet ud for meddelelsen.
  - Hvis du vil søge efter en eksisterende meddelelse, skal du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** for at søge efter navnet.

    Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

  - Klik på ![Opret nyt ikon for at oprette og bruge en ny meddelelse.](../../media/m365-cc-sc-create-icon.png) **Opret ny**.

#### <a name="create-new-positive-reinforcement-notification-wizard"></a>Opret en ny guide til meddelelse om positiv forstærkning

Hvis du har klikket ![på Ikonet Opret ny.](../../media/m365-cc-sc-create-icon.png) **Opret ny** på meddelelsessiden **Positiv forstærkning** . Der åbnes en guide til oprettelse af meddelelser.

Oprettelsestrinnene er identiske som beskrevet i [Opret slutbrugermeddelelser](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> På siden **Definer detaljer** skal du sørge for at vælge værdien **Meddelelse om positiv forstærkning** for **Vælg meddelelsestype**.

Når du er færdig, føres du tilbage til siden med **meddelelse om positiv forstærkning** , hvor den meddelelse, du lige har oprettet, nu vises på listen.

Vælg den meddelelse, du vil bruge, og klik derefter på **Næste**.

## <a name="launch-details"></a>Startoplysninger

På siden **Start detaljer** skal du vælge, hvornår simuleringen skal startes, og hvornår simuleringen skal afsluttes. Vi holder op med at registrere interaktionen med denne simulering efter den angivne slutdato.

Følgende indstillinger er tilgængelige:

- Vælg en af følgende værdier:
  - **Start denne simulering, så snart jeg er færdig**
  - **Planlæg, at denne simulering startes senere**: Denne værdi har følgende tilknyttede indstillinger, der skal konfigureres:
    - **Vælg startdato**
    - **Vælg starttidspunkt**
- **Konfigurer det antal dage, simulering skal afsluttes efter**: Standardværdien er 2.
- **Aktivér levering af tidszone, der er opmærksom på området**: Levér simulerede angrebsmeddelelser til dine medarbejdere i løbet af deres arbejdstid baseret på deres område.
- **Vis den interstitiale side med drive-by-data, der er indsamlet**: Du kan få vist overlejringen, der kommer op til teknikangrebene for drive-bu URL. Hvis du vil skjule overlejringen og gå direkte til landingssiden, skal du fjerne markeringen af denne indstilling.

Klik på **Næste**, når du er færdig.

## <a name="review-simulation"></a>Gennemse simulering

På siden **Gennemse simulering** kan du gennemse detaljerne for din simulering.

Klik på ikonet ![Send en test.](../../media/m365-cc-sc-send-icon.png) **Send en testknap** for at sende en kopi af nyttedatamailen til dig selv (den bruger, der i øjeblikket er logget på) til inspektion.

Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

Klik på **Send**, når du er færdig.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Siden Gennemse simulering i Oplæring af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::
