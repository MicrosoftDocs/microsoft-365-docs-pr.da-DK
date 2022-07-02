---
title: Simuleringsautomatiseringer til oplæring af simulering af angreb
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
description: Administratorer kan få mere at vide om, hvordan de opretter automatiserede simuleringer, der indeholder bestemte teknikker og nyttedata, der startes, når de angivne betingelser er opfyldt i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 1efc6faaae0040e37aafac4faa0a10228d76e766
ms.sourcegitcommit: 03543c27c33427ac7f11af4c04fff35a181a2524
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66609408"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Simuleringsautomatiseringer til oplæring af simulering af angreb

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Du kan finde oplysninger om, hvordan du kommer i gang, om oplæring i simulering af angreb under [Kom i gang med at bruge oplæring i simulering af angreb](attack-simulation-training-get-started.md).

Benyt følgende fremgangsmåde for at oprette en automatisering af simulering:

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com/>skal du gå til **Mail & samarbejde** \> **Oplæring** \> i simulering af angreb **Automatiseringer Automatiseringer** \> **Automatiseringer af simulering**.

   Hvis du vil gå direkte til fanen **Automatiseringer** , hvor du kan vælge **Simuleringsautomatiseringer**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=automations>.

2. Vælg ![Opret **automatiseringsikon under Simuleringsautomatiseringer**.](../../media/m365-cc-sc-create-icon.png) **Opret automatisering**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Knappen Opret simulering på fanen Simuleringsautomatiseringer i Oplæring af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. Guiden Til oprettelse åbnes. I resten af denne artikel beskrives siderne og de indstillinger, de indeholder.

> [!NOTE]
> Når som helst under guiden til oprettelse af simulering kan du klikke på **Gem og luk** for at gemme dine fremskridt og fortsætte med at konfigurere simuleringen senere. Den ufuldstændige simulering har **statusværdien** **Kladde** under fanen **Simuleringer** . Du kan fortsætte, hvor du slap, ved at vælge simuleringen og klikke på ![Rediger simuleringsikon.](../../media/m365-cc-sc-edit-icon.png) **Rediger** simulering.## Navngiv og beskriv simuleringen.

## <a name="name-and-describe-the-simulation-automation"></a>Navngiv og beskriv simuleringsautomatisering

Konfigurer følgende indstillinger på siden **Automation-navn** :

- **Navn**: Angiv et entydigt, beskrivende navn til simuleringen.
- **Beskrivelse**: Angiv en valgfri detaljeret beskrivelse af simuleringen.

Klik på **Næste**, når du er færdig.

## <a name="select-one-or-more-social-engineering-techniques"></a>Vælg en eller flere teknikker til social engineering

På siden **Select social engineering techniques** skal du vælge en eller flere af de tilgængelige teknikker til social engineering, som blev udvalgt fra [MITRE ATT-&CK-strukturen®](https://attack.mitre.org/techniques/enterprise/). Der findes forskellige nyttedata til forskellige teknikker. Følgende teknikker til social engineering er tilgængelige:

- **Høst af legitimationsoplysninger**: Forsøger at indsamle legitimationsoplysninger ved at tage brugerne til et velkendt websted med inputfelter for at indsende et brugernavn og en adgangskode.
- **Vedhæftet malware**: Føjer en skadelig vedhæftet fil til en meddelelse. Når brugeren åbner den vedhæftede fil, køres der vilkårlig kode, der hjælper hackeren med at kompromittere målets enhed.
- **Link i vedhæftet fil**: En type af legitimationsoplysninger høst hybrid. En hacker indsætter en URL-adresse i en vedhæftet fil i en mail. URL-adressen i den vedhæftede fil følger samme teknik som høst af legitimationsoplysninger.
- **Link til malware**: Kører vilkårlig kode fra en fil, der hostes på en velkendt fildelingstjeneste. Den meddelelse, der sendes til brugeren, indeholder et link til denne skadelige fil. Åbning af filen og hjælp hackeren med at kompromittere målets enhed.
- **Drive-by URL**: Den skadelige URL-adresse i meddelelsen fører brugeren til et velkendt websted, der uovervåget kører og/eller installerer kode på brugerens enhed.

Hvis du klikker på linket **Vis detaljer** i beskrivelsen, åbnes der et pop op-vindue med detaljer, der beskriver teknikken og de simuleringstrin, der er resultatet af teknikken.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Pop op-vinduet Detaljer for teknikken til indsamling af legitimationsoplysninger på siden Vælg socialtekniske teknikker" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

Klik på **Næste**, når du er færdig.

## <a name="select-a-payload-and-login-page"></a>Vælg en nyttedata- og logonside

På siden **Vælg nyttedata og logon** skal du vælge en eksisterende nyttedata på listen eller oprette en ny nyttedata.

Du kan også få vist den logonside, der bruges i nyttedataene, vælge en anden logonside, du vil bruge, eller oprette en ny logonside, du vil bruge.

### <a name="payload"></a>Nyttelast

Vælg en af følgende indstillinger på siden **Vælg nyttedata** :

- **Vælg manuelt**
- **Randomisere**

Hvis du vælger **Randomiser**, er der ikke noget at konfigurere på denne side, så klik på **Næste** for at fortsætte.

Hvis du vælger **Vælg manuelt**, skal du vælge en eller flere nyttedata på listen. Følgende oplysninger vises for hver nyttedata:

- **Navn på nyttedata**
- **Teknik**: Du skal vælge mindst én nyttedata pr. teknik, som du valgte på den forrige side.
- **Sprog**: De tilgængelige værdier er: **engelsk**, **spansk**, **tysk**, **japansk**, **fransk**, **portugisisk**, **hollandsk**, **italiensk**, **svensk**, **kinesisk (forenklet)**, **norsk bokmål**, **polsk**, **russisk**, **finsk**, **koreansk**, **tyrkisk**, **ungarsk**, **hebraisk**, **thai**, **arabisk**, **vietnamesisk**, **slovakisk**, **græsk**, **indonesisk**, **rumænsk**, **slovensk**, **kroatisk**, **catalansk** eller **andet**.
- **Klikfrekvens**: Hvor mange personer der har klikket på denne nyttedata.
- **Forudsagt kompromisrate**: Historiske data for nyttedataene på tværs af Microsoft 365, der forudsiger procentdelen af personer, der bliver kompromitteret af denne nyttedata.
- **De startede simuleringer** tæller antallet af gange, denne nyttedata blev brugt i andre simuleringer.

På ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **I søgefeltet** kan du skrive en del af navnet på nyttedata og trykke på Enter for at filtrere resultaterne.

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Kompleksitet**: Beregnet på baggrund af antallet af indikatorer i nyttedataene, der angiver et muligt angreb (stavefejl, uopsættelighed osv.). Flere indikatorer er nemmere at identificere som et angreb og angive lavere kompleksitet. De tilgængelige værdier er:

  - **Høj**
  - **Medium**
  - **Lav**

- **Sprog**

- **Tilføj kode(r)**

- **Filtrer efter tema**: De tilgængelige værdier er: **Kontoaktivering**, **Kontobekræftelse**, **Fakturering**, **Ryd op i mail**, **Modtaget dokument**, **Udgift**, **Fax**, **Økonomirapport**, **Indgående meddelelser**, **Faktura**, **Modtagne elementer**, **Logonbesked**, **Post modtaget**, **Adgangskode**, **Betaling**, **Løn**, **Personligt tilbud**, **Karantæne**, **Fjernarbejde**, **Gennemse meddelelse**, **Sikkerhedsopdatering**, **Afbrudt tjeneste**, **Signatur påkrævet**, **Lager til opgradering af postkasse Bekræft postkasse**, **Voicemail** og **Andet**.

- **Filtrer efter brand**: De tilgængelige værdier er: **American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** og **Other**.

- **Filtrer efter branche**: De tilgængelige værdier er: **Banking**, **Business services**, **Consumer services**, **Education**, **Energy**, **Construction**, **Consulting**, **Financial services**, **Government**, **Hospitality**, **Insurance**, **Legal**, **Courier services**, **IT**, **Healthcare**, **Manufacturing**, **Retail**, **Telecom**, **Real estate**, og **Andet**.

- **Aktuel hændelse**: De tilgængelige værdier er **Ja** eller **Nej**.

- **Kontroversiel**: De tilgængelige værdier er **Ja** eller **Nej**.

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Hvis du vælger en nyttedata på listen ved at klikke et vilkårligt sted i rækken ud over afkrydsningsfeltet, vises oplysninger om nyttedataene i et pop op-vindue:

- Fanen **Nyttedata** indeholder et eksempel og andre oplysninger om nyttedataene.
- Fanen **Logonside** er beskrevet i næste afsnit.
- Fanen **Simuleringer, der startes** , indeholder **simuleringsnavnet**, **klikfrekvensen**, **kompromitteret hastighed** og **handling**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details-payload-tab.png" alt-text="Fanen Payload i pop op-vinduet med nyttedata under oplæring i simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-select-payload-details-payload-tab.png":::

### <a name="login-page"></a>Logonside

Vælg nyttedataene på listen ved at klikke et vilkårligt sted i rækken ud over afkrydsningsfeltet for at åbne pop op-vinduet med detaljer.

Fanen **Logonside** i pop op-vinduet med nyttedataoplysninger viser den logonside, der i øjeblikket er valgt for nyttedataene.

Hvis du vil have vist hele logonsiden, skal du bruge **linkene Side 1** og **Side 2** nederst på siden til tosidede logonsider.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details-login-page-tab.png" alt-text="Fanen Logonside i pop op-vinduet med nyttedata under oplæring i simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-select-payload-details-login-page-tab.png":::

Hvis du vil ændre den logonside, der bruges i nyttedataene, skal du klikke på ![ikonet Skift logonside.](../../media/m365-cc-sc-edit-icon.png) **Skift logonside**.

På pop op-vinduet **Vælg logonside** , der vises, vises følgende oplysninger for hver logonside:

- **Navn**
- **Sprog**
- **Kilde**: For indbyggede logonsider er værdien **Global**. For brugerdefinerede logonsider er værdien **Lejer**.
- **Status**: **Klar** eller **Kladde**.
- **Oprettet af**: For indbyggede logonsider er værdien **Microsoft**. For brugerdefinerede logonsider er værdien UPN for den bruger, der oprettede logonsiden.
- **Senest ændret**
- **Handlinger**: Klik på ![ikonet Eksempel.](../../media/m365-cc-sc-eye-icon.png) **Eksempelvisning** for at få vist logonsiden.

Hvis du vil finde en logonside på listen, skal du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** for at finde navnet på logonsiden.

Klik på ![Filterikon.](../../media/m365-cc-sc-filter-icon.png) **Filtrer** for at filtrere logonsiderne efter **kilde** eller **sprog**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-select-login-page.png" alt-text="Vælg logonsiden under fanen Logonside i pop op-vinduet med nyttedataoplysninger i Oplæring i simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-select-payload-select-login-page.png":::

Hvis du vil oprette en ny logonside, skal du klikke på [Opret nyt ikon.](../../media/m365-cc-sc-create-icon.png) **Opret ny** for at starte guiden Opret slutbrugerlogonside. Trinnene er de samme som på **logonsider** under **oplæring** \> af simulering af angreb **under fanen Simuleret indholdsbibliotek** . Du kan finde en vejledning under [Opret logonsider](attack-simulation-training-login-pages.md#create-login-pages).

Tilbage på **siden Vælg logon** skal du bekræfte, at den nye logonside, du har oprettet, er valgt, og derefter klikke på **Gem**.

Tilbage på pop op-vinduet med nyttedataoplysninger skal du klikke på [Ikonet Luk.](../../media/m365-cc-sc-close-icon.png) **Luk**.

Når du er færdig på **siden Vælg en nyttedata og logon**, skal du klikke på **Næste**.

## <a name="target-users"></a>Destinationsbrugere

På siden **Målbrugere** skal du vælge, hvem der skal modtage simuleringen. Konfigurer en af følgende indstillinger:

- **Medtag alle brugere i din organisation**: De berørte brugere vises på lister over 10. Du kan bruge knapperne **Næste** og **Forrige** direkte under listen over brugere til at rulle gennem listen. Du kan også bruge ikonet ![Søg.](../../media/m365-cc-sc-search-icon.png) **Søgeikon** på siden for at finde berørte brugere.
- **Medtag kun bestemte brugere og grupper**: Vælg en af følgende indstillinger:
  - ![Ikonet Tilføj brugere.](../../media/m365-cc-sc-create-icon.png) **Tilføj brugere**: I pop op-vinduet **Tilføj brugere** , der vises, kan du finde brugere og grupper ud fra følgende kriterier:
    - **Brugere eller grupper**: På ikonet ![Søg efter brugere og grupper.](../../media/m365-cc-sc-search-icon.png) **Søg efter brugere og grupper** . Du kan skrive en del af **brugerens** eller gruppens navn eller **mailadresse** og derefter trykke på Enter. Du kan vælge nogle af eller alle resultaterne. Når du er færdig, skal du klikke på **Tilføj x-brugere**.

      > [!NOTE]
      > Hvis du klikker på knappen **Tilføj filtre** for at vende tilbage til indstillingerne **Filtrer brugere efter kategorier** , ryddes alle de brugere eller grupper, du har valgt i søgeresultaterne.

    - **Filtrer brugere efter kategorier**: Vælg mellem ingen, nogle eller alle af følgende indstillinger:
      - **Foreslåede brugergrupper**: Vælg mellem følgende værdier:
        - **Alle foreslåede brugergrupper**
        - **Brugere, der ikke er målrettet mod en simulering inden for de sidste tre måneder**
        - **Gentag lovovertrædere**
      - **Afdeling**: Brug følgende indstillinger:
        - **Søg**: På ikonet ![Søg efter afdeling.](../../media/m365-cc-sc-search-icon.png) **Søg efter afdelingsfelt** , du kan skrive en del af værdien Afdeling og derefter trykke på Enter. Du kan vælge nogle af eller alle resultaterne.
        - Vælg **alle afdelinger**
        - Vælg eksisterende afdelingsværdier.
      - **Titel**: Brug følgende indstillinger:
        - **Søg**: I ikonet ![Søg efter titel.](../../media/m365-cc-sc-search-icon.png) **Søg efter titelfelt** , skriv en del af titelværdien, og tryk derefter på Enter. Du kan vælge nogle af eller alle resultaterne.
        - Markér **al titel**
        - Vælg eksisterende titelværdier.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Den bruger, der filtrerer på siden Målbrugere i oplæringen af simulering af angreb på Microsoft 365 Defender-portalen" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Når du har identificeret dine kriterier, vises de berørte brugere i afsnittet **Brugerliste** , der vises, hvor du kan vælge nogle eller alle de registrerede modtagere.

      Når du er færdig, skal du klikke på **Anvend(x)** og derefter klikke på **Tilføj x-brugere**.

  Tilbage på den primære side **Målbrugere** kan du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at finde berørte brugere. Du kan også klikke på ![ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** for at fjerne bestemte brugere.

- ![Ikonet Importér.](../../media/m365-cc-sc-create-icon.png) **Import:** I den dialogboks, der åbnes, skal du angive en CSV-fil, der indeholder én mailadresse pr. linje.

  Når du har fundet en markering af CSV-filen, importeres listen over brugere, og den vises på siden **Målrettede brugere** . Du kan bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** til at finde berørte brugere. Du kan også klikke på ![ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** for at fjerne bestemte brugere.

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

For hver oplæring på listen skal du vælge en eller flere af følgende værdier i kolonnen **Tildel til** for at konfigurere, hvem der får oplæringen:

- **Alle brugere**
- **Nyttedata, der er klikket på**
- **Kompromitteret**

Hvis du ikke vil bruge en oplæring, der vises, skal du klikke på ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Siden Oplæringstildeling i Oplæring i simulering af angreb på portalen Microsoft 365 Defender" lightbox="../../media/attack-sim-training-training-assignment.png":::

Klik på **Næste**, når du er færdig.

### <a name="landing-page"></a>Destinationsside

På **landingssiden** kan du konfigurere den webside, som brugeren sendes til, hvis brugeren åbner nyttedataene i simuleringen.

- **Vælg indstillinger for landingsside**: De tilgængelige værdier afhænger af dine tidligere valg af nyttedata på siden [Vælg en nyttedata og logonside](#select-a-payload-and-login-page) som beskrevet i følgende tabel:

  |Valg af nyttedata|Tilgængelige værdier for Vælg indstillinger for landingsside|
  |---|---|
  |Vælg manuelt|Brug Microsofts standardlandingsside <br><br> Opret din egen landingsside <p> Brug en brugerdefineret URL-adresse <p> **Bemærk**! Værdien **Brug en brugerdefineret URL-adresse** er ikke tilgængelig, hvis du tidligere har valgt **vedhæftet fil til malware** eller **Link til malware** på siden [Vælg teknikker til social engineering](#select-one-or-more-social-engineering-techniques) .|
  |Randomisere|Brug Microsofts standardlandingsside|

  De tilgængelige indstillinger **for Vælg landingsside** og deres tilknyttede indstillinger er beskrevet på følgende liste:

  - **Brug Microsofts standardlandingsside**. Dette er standardværdien og resulterer i én Microsoft-standardskabelon, -logo og -nyttedataindikatorhandling, der gælder for alle nyttedata.

    Du skal konfigurere følgende yderligere indstillinger på **landingssiden** :

    - **Vælg landingssidelayout**: Vælg en af de fem tilgængelige landingssideskabeloner.
    - **Tilføj logo**: Klik på **Gennemse** for at finde og vælge en .png-, .jpeg- eller .gif-fil, der skal føjes til alle de nyttedata, der er valgt af Microsoft. Logostørrelsen må højst være 210 x 70 for at undgå forvrængning. Klik på **Fjern** for at fjerne logoet.
    - **Payload-indikatorer**: Denne indstilling er ikke tilgængelig, hvis du tidligere har valgt **vedhæftet fil til malware** eller **Link til malware** på siden [Vælg teknikker til social engineering](#select-one-or-more-social-engineering-techniques) .

      Vælg **Føj nyttedataindikatorer til mail for at** hjælpe brugerne med at lære, hvordan de identificerer phishing-meddelelser.

    Du kan få vist resultaterne ved at klikke på knappen **Åbn eksempelpanel** midt på siden. I det pop op-vindue til eksempelvisning, der vises, kan du bruge **Vælg nyttedata til at få vist et eksempel** for at se, hvordan hver nyttedata ser ud.

  - **Opret din egen landingsside**: Denne værdi resulterer i en enkelt nyttedataindikatorhandling, der anvendes på de valgte nyttedata.

    Du skal konfigurere følgende yderligere indstillinger på **landingssiden** :

    - **Payloadindikatorer**: Denne indstilling er kun tilgængelig, hvis begge af følgende betingelser er opfyldt:
      - Du har tidligere valgt **Høst af legitimationsoplysninger**, **Link i vedhæftet fil** eller **URL-adresse til kørsel** på siden [Vælg teknikker til social engineering](#select-one-or-more-social-engineering-techniques) .
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
        - **Brug fra standard**: Vælg en af de fem tilgængelige landingssideskabeloner til at starte med. Du kan redigere teksten og layoutet i redigeringsområdet. Klik på **Nulstil til standard** for at nulstille landingssiden til standardteksten og layoutet for skabelonen.
        - **Træningslink**: I dialogboksen **URL-adresse til oplæring af navn** , der vises, skal du angive en linktitel til træningslinket og derefter klikke på **Bekræft** for at føje linket til landingssiden.
      - **Kode**: Du kan få vist og redigere HTML-koden direkte.

      Du kan få vist resultaterne ved at klikke på knappen **Åbn eksempelpanel** midt på siden. I det pop op-vindue til eksempelvisning, der vises, kan du bruge **Vælg nyttedata til at få vist et eksempel** for at se, hvordan hver nyttedata ser ud.

  - **Brug en brugerdefineret URL-adresse**: Tilføj URL-adressen i feltet **Angiv URL-adressen til den brugerdefinerede landingsside** , der vises. Der er ingen andre indstillinger tilgængelige på siden.

Klik på **Næste**, når du er færdig.

## <a name="select-end-user-notification"></a>Vælg slutbrugermeddelelse

På siden **Vælg slutbrugermeddelelse** skal du vælge mellem følgende meddelelsesindstillinger:

- **Levér ikke meddelelser**: Klik på **Fortsæt** i den dialogboks med beskeder, der vises. Hvis du vælger denne indstilling, føres du til siden [Simuleringsplan](#simulation-schedule) , når du klikker på **Næste**.

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
      - **Fanen Eksempel** : Få vist meddelelsesmeddelelsen, som brugerne kan se den.
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

  Du føres til siden [Simuleringsplan](#simulation-schedule) , når du klikker på **Næste**.

- **Tilpassede slutbrugermeddelelser**: Når du klikker på **Næste**, føres du til siden **Med meddelelser om oplæringstildeling** , som beskrevet i de næste afsnit.

### <a name="training-assignment-notification"></a>Meddelelse om oplæringstildeling

Meddelelsessiden **Oplæringstildeling** er kun tilgængelig, hvis du har valgt **Tilpassede slutbrugermeddelelser** på siden **[Vælg slutbrugermeddelelse](#select-end-user-notification)** .

På denne side vises følgende meddelelser og deres konfigurerede sprog:

- **Microsofts standardmeddelelse om oplæringstildeling**
- Alle brugerdefinerede meddelelser om oplæringstildeling, som du tidligere har oprettet.

  Disse meddelelser er også tilgængelige i **Meddelelser fra slutbrugere** på fanen **Simuleringsindholdsbibliotek** i Oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. **Microsofts standardmeddelelse om oplæringstildeling** er tilgængelig på fanen **Globale meddelelser** . Meddelelser om brugerdefinerede oplæringstildelinger er tilgængelige under fanen **Lejermeddelelser** . Du kan få flere oplysninger under [Slutbrugermeddelelser om oplæring i simulering af angreb](attack-simulation-training-end-user-notifications.md).

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

    Disse meddelelser er også tilgængelige i **Meddelelser fra slutbrugere** på fanen **Simuleringsindholdsbibliotek** i Oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. **Påmindelsesmeddelelse om Microsofts standardtræning** er tilgængelig på fanen **Globale meddelelser** . Påmindelsesmeddelelser om brugerdefineret oplæring er tilgængelige under fanen **Lejermeddelelser** . Du kan få flere oplysninger under [Slutbrugermeddelelser om oplæring i simulering af angreb](attack-simulation-training-end-user-notifications.md).

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

  - **Levér ikke**: Hvis du vælger denne indstilling, føres du til siden [Simuleringsplan](#simulation-schedule) , når du klikker på **Næste**.

  - **Levér, når brugeren rapporterer en phish og kampagne slutter** eller **Levér umiddelbart efter brugeren rapporterer en phish**: I disse afsnit vises følgende meddelelser og deres konfigurerede sprog i afsnittet **Vælg en meddelelse om positiv forstærkning** , der vises:

  - **Microsofts standardmeddelelse om positiv forstærkning**
  - Alle brugerdefinerede meddelelser om positiv forstærkning, som du tidligere har oprettet.

    Disse meddelelser er også tilgængelige i **Meddelelser fra slutbrugere** på fanen **Simuleringsindholdsbibliotek** i Oplæring i simulering af angreb på <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. **Microsofts standardmeddelelse om positiv forstærkning** er tilgængelig på fanen **Globale meddelelser** . Brugerdefinerede meddelelser om positiv forstærkning er tilgængelige på fanen **Lejermeddelelser** . Du kan få flere oplysninger under [Slutbrugermeddelelser om oplæring i simulering af angreb](attack-simulation-training-end-user-notifications.md).

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

## <a name="simulation-schedule"></a>Simuleringsplan

Vælg en af følgende værdier på siden **Simuleringsplan** :

- **Randomiseret**: Du skal stadig vælge tidsplanen på næste side, men simuleringerne startes på tilfældige tidspunkter med tidsplanen.
- **Fast**

Klik på **Næste**, når du er færdig.

## <a name="schedule-details"></a>Planlægningsoplysninger

Det, du kan se på siden **Planlæg detaljer** , afhænger af, om du har valgt **Randomiseret** eller **Fast** på den forrige side.

- **Randomiseret**: Følgende indstillinger er tilgængelige:
  - **Afsnittet Simuleringsstart** : Konfigurer følgende indstilling:
    - **Vælg den dato, hvor simuleringerne skal starte fra**
  - Afsnittet **Simuleringsinterval**: Konfigurer følgende indstillinger:
    - **Vælg de ugedage, som simuleringer må starte på**: Vælg en eller flere dage i ugen.
    - **Angiv det maksimale antal simuleringer, der kan startes mellem start- og slutdatoerne**: Angiv en værdi mellem 1 og 10.
    - **Randomiser afsendelsestider**: Vælg denne indstilling for at randomisere afsendelsestidspunkterne.
  - **Slutsektion til simulering** : Konfigurer følgende indstilling:
    - **Vælg den dato, hvor simuleringerne skal slutte**

- **Løst**: Følgende indstillinger er tilgængelige:
  - **Afsnittet Simuleringsstart** : Konfigurer følgende indstilling:
    - **Vælg den dato, hvor simuleringerne skal starte fra**
  - Afsnittet **Gentagelse af simulering**: Konfigurer følgende indstillinger:
    - **Vælg, om simuleringer skal startes ugentligt eller månedligt**: Vælg en af følgende værdier:
      - **Ugentligt**: Dette er standardværdien.
      - **Månedlige**
    - **Angiv, hvor ofte i uger simuleringen skal gentages**: Angiv en værdi fra 1 til 99 uger.
    - **Vælg den ugedag, simuleringen skal starte fra**
  - **Slutsektion til simulering** : Du kan vælge en af følgende værdier:
    - **Vælg den dato, hvor simuleringerne skal slutte**
    - **Angiv antallet af forekomster af de simuleringer, der skal køres, før de slutter**: Angiv en værdi mellem 1 og 10.

Klik på **Næste**, når du er færdig.

## <a name="launch-details"></a>Startoplysninger

Konfigurer følgende yderligere indstillinger for automatiseringen på siden **Start detaljer** :

- **Brug entydige nyttedata på tværs af simuleringer i en automatisering**: Denne indstilling er som standard ikke valgt.
- **Målrepeater for lovovertrædere**: Denne indstilling er som standard ikke valgt. Hvis du vælger den, skal du konfigurere følgende indstilling, der vises:
  - **Angiv det maksimale antal gange, en bruger kan målrettes inden for denne automatisering**: Angiv en værdi fra 1 til 10.
- **Send simuleringsmail baseret på brugerens aktuelle tidszoneindstilling fra Outlook Web App**: Denne indstilling er som standard ikke valgt.
- **Vis siden med interstitialdata, der indsamles via drive-by**: Denne indstilling er kun tilgængelig, hvis du har valgt **Drive-by URL på** siden **[Vælg teknikker til social engineering](#select-one-or-more-social-engineering-techniques)** . Indstillingen er som standard slået til (![til/fra-ikonet til).](../../media/scc-toggle-on.png)

## <a name="review-simulation-automation"></a>Gennemse simuleringsautomatisering

På siden **Gennemse automatisering af simulering** kan du gennemse oplysningerne om din simuleringsautomatisering.

Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

Klik på **Send**, når du er færdig.
