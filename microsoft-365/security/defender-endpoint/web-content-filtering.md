---
title: Filtrering af webindhold
description: Brug filtrering af webindhold i Microsoft Defender for Endpoint til at spore og regulere adgangen til websteder baseret på deres indholdskategorier.
keywords: webbeskyttelse, beskyttelse mod webtrusler, webbrowsing, overvågning, rapporter, kort, domæneliste, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Edge, Internet Explorer, Chrome, Firefox, webbrowser
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 14d45f4ac22a9707b380d817cb89da1bbee562e2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597543"
---
# <a name="web-content-filtering"></a>Filtrering af webindhold

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Filtrering af webindhold er en del af [webbeskyttelsesfunktionerne](web-protection-overview.md) i Microsoft Defender til slutpunkt. Det giver din organisation mulighed for at spore og regulere adgangen til websteder baseret på deres indholdskategorier. Mange af disse websteder, selvom de ikke er skadelige, kan være problematiske på grund af overholdelse af regler, båndbreddeforbrug eller andre problemer.

Konfigurer politikker på tværs af dine enhedsgrupper for at blokere bestemte kategorier. Blokering af en kategori forhindrer brugere inden for bestemte enhedsgrupper i at få adgang til URL-adresser, der er knyttet til kategorien. For enhver kategori, der ikke er blokeret, overvåges URL-adresserne automatisk. Brugerne kan få adgang til URL-adresserne uden afbrydelse, og du vil indsamle adgangsstatistik for at hjælpe med at oprette en mere brugerdefineret politikbeslutning. Brugerne får vist en meddelelse om blokering, hvis et element på den side, de får vist, foretager opkald til en blokeret ressource.

Filtrering af webindhold er tilgængelig i de større webbrowsere med blokke, der udføres af Windows Defender SmartScreen (Microsoft Edge) og Netværksbeskyttelse (Chrome, Firefox,Ering og Opera). Du kan finde flere oplysninger om browsersupport i afsnittet forudsætninger.

## <a name="benefits-of-web-content-filtering"></a>Fordele ved filtrering af webindhold

- Brugere er forhindret i at få adgang til websteder i blokerede kategorier, uanset om de søger lokalt eller væk.

- Dit sikkerhedsteam kan nemt udrulle politikker til grupper af brugere ved hjælp af enhedsgrupper, der er defineret i rollebaserede adgangskontrolindstillinger [for Microsoft Defender til Slutpunkt](/microsoft-365/security/defender-endpoint/rbac).

- Dit sikkerhedsteam kan få adgang til webrapporter på samme centrale placering med synlighed over faktiske blokke og webforbrug.

## <a name="prerequisites"></a>Forudsætninger

Før du prøver denne funktion, skal du sikre dig, at du opfylder følgende krav:

- Dit abonnement omfatter en af følgende: Windows 10 Enterprise E5, Microsoft 365 E5, Microsoft 365 E5 Sikkerhed, Microsoft 365 E3 + Microsoft 365 E5 Sikkerhed  tilføjelsesprogrammet eller den enkeltstående Licens til Microsoft Defender for Endpoint. 

- Du har adgang til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

- Din organisations enheder kører Windows 10 Jubilæumsopdatering (version 1607) eller nyere, eller Windows 11 med de nyeste [antivirus-/antimalwareopdateringer](manage-updates-baselines-microsoft-defender-antivirus.md).

- Windows Defender SmartScreen og netværksbeskyttelse er aktiveret på organisationens enheder.

## <a name="data-handling"></a>Datahåndtering

Data gemmes i det område, der blev valgt som en del af dine [indstillinger for datahåndtering i Microsoft Defender til slutpunkt](data-storage-privacy.md). Dine data forlader ikke datacenteret i det pågældende område. Derudover vil dine data ikke blive delt med tredjeparter, herunder vores dataudbydere.

## <a name="turn-on-web-content-filtering"></a>Aktivere filtrering af webindhold

I navigationen til venstre i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du vælge **Indstillinger** \> **Generelle avancerede funktioner** \> **for** \> **slutpunkter**. Rul ned, indtil du ser posten for **filtrering af webindhold**. Slå til/fra-knappen **til Til** og **Gem** indstillinger.

### <a name="configure-web-content-filtering-policies"></a>Konfigurere politikker for filtrering af webindhold

Politikker for filtrering af webindhold angiver, hvilke webstedskategorier der blokeres for hvilke enhedsgrupper. Hvis du vil administrere politikkerne, **skal Indstillinger** \> **vælge Filtrering af** \> **webindhold på slutpunkter** (under **Regler**).

Politikker kan installeres til at blokere en af følgende overordnede eller underordnede kategorier:

<details>
<summary>Indhold beregnet for voksne</summary>

**Indhold:** Websteder, der er relateret til grupper eller bevægelser, hvis medlemmer demonstrerer passion i et trossystem, der er anderledes end dem, der er accepteret. 

**1**) Online- og websteder, der promoverer færdigheder og øvelse.

**Nudity**: Websteder, der indeholder billeder eller videoer i fuld frontal og semi-nude, typisk i kunstnerisk form, og som muligvis tillader download eller salg af disse materialer.

**Pornografi/seksuelt eksplicit: Websteder**, der indeholder seksuelt eksplicit indhold i billedbaseret eller tekstbaseret form. Alle former for materiale med et seksuelt indhold vises også her.

**Uddannelse** om køn: Websteder, der diskuterer køn og seksualitet på en informativ og ikke-voyeuristisk måde, herunder websteder, der tilbyder uddannelse om menneskelig reproduktion og contraception, websteder, der giver råd om at forhindre indisk institet fra seksuelt sundhedstilstand, og websteder, der giver råd om seksuel sundhed.

**Smagsløs**: Websteder, der er orienteret mod indhold, som skole børn kan få vist, eller som en arbejdsgiver vil være utilpasse med deres medarbejderes adgang til, men ikke nødvendigvis bevidste eller pornografiske.

**Vold**: Websteder, der viser eller fremmer indhold relateret til vold mod mennesker eller dyr.

</details>

<details>
<summary>Høj båndbredde</summary>

**Downloadwebsteder**: Websteder, hvis primære funktion er at tillade brugere at downloade medieindhold eller programmer, f.eks. computerprogrammer.

**Billeddeling**: Websteder, der primært bruges til at søge efter eller dele fotos, herunder dem, der har sociale aspekter.

**Peer-to-peer: Websteder**, der hoster peer-to-peer-software (P2P) eller letter deling af filer ved hjælp af P2P-software.

**Streaming media & downloads**: Websteder, hvis primære funktion er distributionen af streamingmedier, eller websteder, der giver brugere mulighed for at søge, se eller lytte til streamingmedier.
  
</details>

<details>
<summary>Juridisk ansvar</summary>

**Misbrugsbilleder af** børn: Websteder, der inkluderer misbrugsbilleder af børn eller pornografi. 

**Kriminelle aktiviteter**: Websteder, der giver instruktion om, råd om eller promovering af ulovlige aktiviteter.

**Hacking**: Websteder, der leverer ressourcer til ulovlig eller tvivlbar brug af computersoftware eller hardware, herunder websteder, der distribuerer copyrightbeskyttet materiale, der er blevet revnet.

**Had &** had: Websteder, der promoverer aggressive, nedgraderende eller krænkende meninger om en hvilken som helst del af populationen, der kan identificeres via race, religion, køn, alder, fortrolighed, fysisk handicap, økonomiske situation, seksuel præferencer eller andre valgmuligheder for livsstil.

**Ulovligt indhold**: Websteder, der sælger ulovlige/kontrollerede, fremmer misbrug eller sælger relateret paraphernalia.

**Ulovlig software**: Websteder, der indeholder eller promoverer brug af malware, spyware, botnet, forsøg på phishing eller & copyrighttyveri.

**Skolesvinding**: Websteder, der er relateret til plaism eller skolebedrag. 

**Skade på sig** selv: Websteder, der fremmer skade på sig selv, herunder cyberangreb, der indeholder skadelige og/eller skadelige meddelelser mod brugere.

**Alle** websteder, der sælger din arbejdsplads eller ønsker at bruge mange forskellige websteder, herunder, men ikke begrænset til, muligheder og muligheder.

</details>

<details>
<summary>Afslappende</summary>

**Chat**: Websteder, der primært er webbaserede chatrum.

**Spil**: Websteder, der vedrører video- eller computerspil, herunder websteder, der promoverer spil via hosting af onlinetjenester eller oplysninger vedrørende spil.

**Chat:** Websteder, der kan bruges til at downloade chatsoftware eller klientbaseret chat.

**Professionelt netværk**: Websteder, der tilbyder professionelle netværkstjenester.

**Sociale netværk**: Websteder, der tilbyder sociale netværkstjenester.

**Webbaseret mail**: Websteder, der tilbyder webbaserede mailtjenester.
  
</details>

<details>
<summary>Ikke kategoriseret</summary>

**Nyligt registrerede domæner**: Websteder, der er nyligt registreret inden for de seneste 30 dage, og som endnu ikke er blevet flyttet til en anden kategori.

**Parkerede domæner**: Websteder, der ikke har indhold eller er parkeret til senere brug.
  
**BEMÆRK**! Ikke kategoriseret indeholder kun nyligt registrerede domæner og parkerede domæner og inkluderer ikke alle andre websteder uden for disse kategorier.
  
</details>

### <a name="create-a-policy"></a>Opret en politik

Hvis du vil tilføje en ny politik, skal du følge disse trin:

1. I portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du vælge **Indstillinger** >  **Filtrering af indhold +** >  **Tilføj politik**.

2. Angiv et navn.

3. Vælg de kategorier, der skal blokeres. Brug udvidelsesikonet til at udvide hver overordnet kategori fuldt ud og vælge bestemte kategorier for webindhold.

4. Angiv politikkens omfang. Vælg enhedsgrupperne for at angive, hvor politikken skal anvendes. Kun enheder i de valgte enhedsgrupper vil være forhindret i at få adgang til websteder i de valgte kategorier.

5. Gennemse oversigten, og gem politikken. Det kan tage op til to timer, før politikopdateringen anvendes på dine valgte enheder.

> [!NOTE]
>
> - Du kan implementere en politik uden at vælge en kategori på en enhedsgruppe. Denne handling opretter en politik, der kun omfatter overvågning, for at hjælpe dig med at forstå brugeradfærden, før du opretter en blokpolitik.
> - Hvis du fjerner en politik eller ændrer enhedsgrupper på samme tid, kan det medføre en forsinkelse i udrulningen af politikken.
> - Blokering af kategorien "Ikke kategoriseret" kan føre til uventede og uønskede resultater.

## <a name="end-user-experience"></a>Slutbrugeroplevelse

Blokeringsoplevelsen for understøttede tredjepartsbrowsere leveres af Network Protection, som indeholder en meddelelse på systemniveau, der informerer brugeren om en blokeret forbindelse. Hvis du vil have en mere brugervenlig browseroplevelse, skal du overveje at Microsoft Edge.

### <a name="allow-specific-websites"></a>Tillad bestemte websteder

Det er muligt at tilsidesætte den blokerede kategori i filtrering af webindhold for at tillade et enkelt websted ved at oprette en brugerdefineret indikatorpolitik. Politikken for brugerdefineret indikator erstatter politikken for filtrering af webindhold, når den anvendes på den pågældende enhedsgruppe.

Hvis du vil definere en brugerdefineret indikator, skal du følge disse trin:

1. I portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du **gå til Indstillinger** \> **URL-adresser** **for slutpunkter** \> \> **-/domæne tilføj** \> **element**.

2. Angiv webstedets domæne.

3. Indstil politikhandlingen til **Tillad**.

### <a name="dispute-categories"></a>Kategorier for tvister

Hvis du støder på et domæne, der er blevet kategoriseret forkert, kan du bestride kategorien direkte fra portalen.

Hvis du vil bestride kategorien for et domæne, skal du gå **til Reports** \> **Web Protection** \> **Web Content Filtering Details** \> **Domains**. På fanen Domæner i rapporterne til filtrering af webindhold kan du se en ellipse ud for hvert af domænerne. Hold markøren over denne ellipse, og vælg **Tvistkategori**.

Der åbnes et panel, hvor du kan vælge prioriteten og tilføje flere oplysninger, f.eks. den foreslåede kategori til geninddeling. Når du har fuldført formularen, skal du vælge **Send**. Vores team vil gennemgå anmodningen inden for én hverdag. Hvis du vil fjerne blokeringen med det samme, skal du oprette [en brugerdefineret tilladelsesindikator](indicator-ip-domain.md).

### <a name="url-category-lookup"></a>Opslag i URL-kategori

For at bestemme kategorien for et websted kan du bruge den URL-søgefunktion, der er tilgængelig på Microsoft 365 Defender-portalen (<https://security.microsoft.com>) under **Slutpunktssøgning**\>. I søgeresultaterne for URL-adressen vises kategorien til filtrering af webindhold under **URL-adresse/domæneoplysninger**. Administratorer kan også bestride kategorien for domænet direkte fra denne side, sådan som det er vist på følgende billede. Hvis kategoriresultatet ikke vises, er URL-adressen i øjeblikket ikke tildelt en eksisterende kategori til filtrering af webindhold.

![Billede af opslagsresultater for kategorien filtrering af webindhold.](../../media/web-content-filtering-category-lookup.png)

## <a name="web-content-filtering-cards-and-details"></a>Webindholdsfiltreringskort og detaljer

Vælg **Reports** \> **Web Protection for** at få vist kort med oplysninger om filtrering af webindhold og beskyttelse mod webtrusler. Følgende kort indeholder oversigtsoplysninger om filtrering af webindhold.

### <a name="web-activity-by-category"></a>Webaktivitet efter kategori

Dette kort viser de overordnede kategorier for webindhold med den største stigning eller det største fald i antallet af adgangsforsøg. Forstå ændringerne af ændringerne i webaktivitetsmønstre i din organisation fra de seneste 30 dage, 3 måneder eller 6 måneder. Vælg et kategorinavn for at få vist flere oplysninger.

I de første 30 dage, efter du har brugt denne funktion, har din organisation muligvis ikke nok data til at vise disse oplysninger.

![Billede af webaktivitet efter kategorikort.](images/web-activity-by-category600.png)

### <a name="web-content-filtering--summary-card"></a>Oversigtskort til filtrering af webindhold

Dette kort viser fordelingen af blokerede adgangsforsøg på tværs af de forskellige overordnede kategorier for webindhold. Vælg en af de farvede søjler for at få vist flere oplysninger om en bestemt overordnet webkategori.

![Billede af oversigtskort til filtrering af webindhold.](images/web-content-filtering-summary.png)

### <a name="web-activity-summary-card"></a>Oversigtskort for webaktivitet

Dette kort viser det samlede antal anmodninger om webindhold i alle URL-adresser.

![Billede af oversigtskort for webaktivitet.](images/web-activity-summary.png)

### <a name="view-card-details"></a>Vis kortdetaljer

Du kan få adgang **til rapportdetaljerne** for hvert kort ved at vælge en tabelrække eller en farvet søjle fra diagrammet på kortet. Siden med rapportoplysninger for hvert kort indeholder omfattende statistiske data om kategorier af webindhold, webstedsdomæner og enhedsgrupper.

![Billede af detaljer i rapport om webbeskyttelse.](images/web-protection-report-details.png)

- **Webkategorier**: Viser de webindholdskategorier, der har haft adgangsforsøg i organisationen. Vælg en bestemt kategori for at åbne en oversigts pop op-out.

- **Domæner:** Viser de webdomæner, der er blevet åbnet eller blokeret i organisationen. Vælg et bestemt domæne for at få vist detaljerede oplysninger om det pågældende domæne.

- **Enhedsgrupper**: Viser alle de enhedsgrupper, der har genereret webaktivitet i organisationen

Brug tidsintervalfilteret øverst til venstre på siden for at vælge en tidsperiode. Du kan også filtrere oplysningerne eller tilpasse kolonnerne. Vælg en række for at åbne en rude med pop op-vinduer med endnu flere oplysninger om det markerede element.

### <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

Kun Microsoft Edge understøttes, hvis din enheds OS-konfiguration er Server (**cmd** \> **Systeminfo** \> **OS Configuration**). Netværksbeskyttelse understøttes kun i tilstanden Undersøg på serverenheder, som er ansvarlig for sikring af trafik på tværs af understøttede tredjepartsbrowsere.

Kun Microsoft Edge understøttes, og Netværksbeskyttelse understøttes ikke på Windows 10 vært for flersessioner af Azure Virtual Desktop.

Netværksbeskyttelse understøtter i øjeblikket ikke SSL-inspektion, hvilket kan medføre, at nogle websteder tillades af filtrering af webindhold, som normalt ville være blokeret. Websteder ville være tilladt på grund af manglende synlighed i krypteret trafik, når TLS handshake er fundet sted, og en manglende mulighed for at fortolke visse omdirigeringer.  Dette omfatter omdirigeringer fra nogle webbaserede logonsider til postkassesiden. Som en accepteret løsning kan du oprette en brugerdefineret blokindikator til logonsiden for at sikre, at ingen brugere kan få adgang til webstedet. Husk, at dette kan blokere deres adgang til andre tjenester, der er knyttet til det samme websted. 

## <a name="see-also"></a>Se også

- [Oversigt over webbeskyttelse](web-protection-overview.md)
- [Webtrusselsbeskyttelse](web-threat-protection.md)
- [Overvåge websikkerhed](web-protection-monitoring.md)
- [Svar på webtrusler](web-protection-response.md)
- [Krav til netværksbeskyttelse](web-content-filtering.md)
