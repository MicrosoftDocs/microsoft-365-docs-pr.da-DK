---
title: Filtrering af webindhold
description: Brug filtrering af webindhold i Microsoft Defender for Endpoint til at spore og regulere adgangen til websteder baseret på deres indholdskategorier.
keywords: webbeskyttelse, webtrusselsbeskyttelse, webbrowsing, overvågning, rapporter, kort, domæneliste, sikkerhed, phishing, malware, udnyttelse, websteder, netværksbeskyttelse, Edge, Internet Explorer, Chrome, Firefox, webbrowser
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: caee6f216ad5006eb31750d2c5cbd0d9e47f21ce
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438921"
---
# <a name="web-content-filtering"></a>Filtrering af webindhold

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

> [!TIP]
> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

## <a name="what-is-web-content-filtering"></a>Hvad er filtrering af webindhold?

Filtrering af webindhold er en del af [webbeskyttelsesfunktionerne](web-protection-overview.md) i Microsoft Defender for Endpoint og Microsoft Defender til virksomheder. Filtrering af webindhold gør det muligt for din organisation at spore og regulere adgangen til websteder baseret på deres indholdskategorier. Mange af disse websteder (selvom de ikke er skadelige) kan være problematiske på grund af overholdelsesregler, båndbreddeforbrug eller andre bekymringer.

Konfigurer politikker på tværs af dine enhedsgrupper for at blokere bestemte kategorier. Blokering af en kategori forhindrer brugere i angivne enhedsgrupper i at få adgang til URL-adresser, der er knyttet til kategorien. FOR alle kategorier, der ikke er blokeret, overvåges URL-adresserne automatisk. Dine brugere kan få adgang til URL-adresserne uden afbrydelser, og du skal indsamle adgangsstatistikker for at hjælpe med at oprette en mere brugerdefineret politikbeslutning. Brugerne får vist en meddelelse om blokering, hvis et element på den side, de får vist, foretager kald til en blokeret ressource.

Filtrering af webindhold er tilgængelig i de større webbrowsere med blokke udført af Windows Defender SmartScreen (Microsoft Edge) og Network Protection (Chrome, Firefox, Brave og Opera). Du kan få flere oplysninger om browsersupport i afsnittet [Forudsætninger](#prerequisites) .

## <a name="benefits-of-web-content-filtering"></a>Fordele ved filtrering af webindhold

- Brugerne forhindres i at få adgang til websteder i blokerede kategorier, uanset om de søger i det lokale miljø eller væk fra webstedet.
- Dit sikkerhedsteam kan få adgang til webrapporter på den samme centrale placering med synlighed over faktiske blokke og webforbrug.
- Hvis du bruger Defender for Endpoint, kan dit sikkerhedsteam nemt udrulle politikker til grupper af brugere ved hjælp af enhedsgrupper, der er defineret i [Microsoft Defender for Endpoint rollebaserede indstillinger for adgangskontrol](/microsoft-365/security/defender-endpoint/rbac).
- Hvis du bruger Defender for Business, kan du definere én politik for filtrering af webindhold, der skal anvendes på alle brugere. 

## <a name="prerequisites"></a>Forudsætninger

Før du afprøver denne funktion, skal du sikre dig, at du opfylder de krav, der er beskrevet i følgende tabel:

| Krav | Beskrivelse |
|:---|:---|
| Abonnement | Dit abonnement skal indeholde en af følgende:<br/>- [Windows 10/11 Enterprise E5](/windows/deployment/deploy-enterprise-licenses)<br/>- [Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise/e5?activetab=pivot%3aoverviewtab)<br/>- Microsoft 365 E5 Sikkerhed<br/>- [Microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise/e3?activetab=pivot%3aoverviewtab)<br/>- [Microsoft Defender for Endpoint Plan 1 eller Plan 2](../defender/eval-defender-endpoint-overview.md)<br/>- [Microsoft Defender til virksomheder](../defender-business/mdb-overview.md) |
| Portaladgang | Du skal have adgang til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. |
| Operativsystem | Organisationens enheder skal køre et af følgende operativsystemer med de [nyeste antivirus-/antimalwareopdateringer](manage-updates-baselines-microsoft-defender-antivirus.md): <br/>- Windows 11<br/>- Windows 10 jubilæumsopdatering (version 1607) eller nyere |
| Relateret beskyttelse | [Windows Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) og [netværksbeskyttelse](network-protection.md) skal være aktiveret på organisationens enheder. |

## <a name="data-handling"></a>Datahåndtering

Data gemmes i det område, der blev valgt som en del af [indstillingerne for Microsoft Defender for Endpoint datahåndtering](data-storage-privacy.md). Dine data forlader ikke datacenteret i det pågældende område. Desuden deles dine data ikke med nogen tredjepart, herunder vores dataudbydere.

## <a name="turn-on-web-content-filtering"></a>Slå filtrering af webindhold til

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og log på.

2. Vælg **Indstillinger** \> **Slutpunkter** \> **Generelle** \> **avancerede funktioner** i navigationsruden. 

3. Rul ned, indtil du kan se **filtrering af webindhold**. 

4. Skift til/fra-knappen til **Til**, og vælg derefter **Gem indstillinger**.

### <a name="configure-web-content-filtering-policies"></a>Konfigurer politikker for filtrering af webindhold

Politikker for filtrering af webindhold angiver, hvilke webstedskategorier der er blokeret for, hvilke enhedsgrupper der er blokeret. Hvis du vil administrere politikkerne, **skal du** gå til Indstillinger \> **Filtrering af webindhold** **for slutpunkter** \> (under **Regler**).

Politikker kan installeres for at blokere en af følgende overordnede eller underordnede kategorier:

<details>
<summary>Indhold beregnet for voksne</summary>

**Sekter**: Websteder relateret til grupper eller bevægelser, hvis medlemmer demonstrerer passion for et trossystem, der er anderledes end dem, der er socialt accepteret. 

**Hasardspil**: Onlinespil og websteder, der fremmer spilfærdigheder og -praksis.

**Nøgenhed**: Websteder, der indeholder billeder eller videoer med fuld frontal og seminude, typisk i kunstnerisk form, og som kan tillade download eller salg af sådanne materialer.

**Pornografi/seksuelt eksplicit**: Websteder, der indeholder seksuelt eksplicit indhold i en billedbaseret eller tekstbaseret form. Enhver form for seksuelt orienteret materiale er også angivet her.

**Seksualundervisning**: Websteder, der diskuterer sex og seksualitet på en informativ og ikke-voyeuristisk måde, herunder websteder, der giver uddannelse om menneskelig reproduktion og svangerskabsforebyggelse, websteder, der tilbyder rådgivning om forebyggelse af infektion mod seksuelle sygdomme, og websteder, der tilbyder rådgivning om seksuelle sundhedsspørgsmål.

**Smagløs**: Websteder, der er orienteret mod indhold, der ikke er egnet til skolebørn at se, eller at en arbejdsgiver ville være utilpas med deres personale, men ikke nødvendigvis voldelig eller pornografisk.

**Vold**: Websteder, der viser eller promoverer indhold, der er relateret til vold mod mennesker eller dyr.

</details>

<details>
<summary>Høj båndbredde</summary>

**Downloadwebsteder**: Websteder, hvis primære funktion er at give brugerne mulighed for at downloade medieindhold eller programmer, f.eks. computerprogrammer.

**Billeddeling**: Websteder, der primært bruges til at søge efter eller dele fotos, herunder dem, der har sociale aspekter.

**Peer-to-peer**: Websteder, der hoster P2P-software (peer-to-peer) eller faciliterer deling af filer ved hjælp af P2P-software.

**Streamingmedier & downloads**: Websteder, hvis primære funktion er distribution af streamingmedier, eller websteder, der giver brugerne mulighed for at søge efter, se eller lytte til streamingmedier.
  
</details>

<details>
<summary>Juridisk ansvar</summary>

**Billeder af børnemishandling**: Websteder, der indeholder billeder af børnemishandling eller pornografi. 

**Kriminel aktivitet**: Websteder, der giver instruktion om, rådgivning om eller fremme af ulovlige aktiviteter.

**Hacking**: Websteder, der leverer ressourcer til ulovlig eller tvivlsom brug af computersoftware eller hardware, herunder websteder, der distribuerer ophavsretligt materiale, der er blevet knækket.

**Hate & intolerance**: Websteder, der fremmer aggressive, nedværdigende eller krænkende meninger om en del af befolkningen, der kunne identificeres af race, religion, køn, alder, nationalitet, fysisk handicap, økonomisk situation, seksuelle præferencer eller andre livsstil valg.

**Ulovligt stof**: Websteder, der sælger ulovlige/kontrollerede stoffer, fremmer stofmisbrug eller sælger relaterede tilbehør.

**Ulovlig software**: Websteder, der indeholder eller fremmer brugen af malware, spyware, botnets, phishing-svindel eller piratkopiering & tyveri af ophavsret.

**Skole snyd**: Websteder relateret til plagiering eller skole snyd. 

**Selvbesigtigelse**: Websteder, der fremmer selvbelastende, herunder cybermobning af websteder, der indeholder stødende og/eller truende meddelelser mod brugere.

**Våben**: Enhver hjemmeside, der sælger våben eller går ind for brugen af våben, herunder, men ikke begrænset til våben, knive og ammunition.

</details>

<details>
<summary>Fritid</summary>

**Chat**: Websteder, der primært er webbaserede chatrum.

**Spil**: Websteder relateret til video- eller computerspil, herunder websteder, der fremmer spil gennem hosting onlinetjenester eller oplysninger relateret til spil.

**Chat**: Websteder, der kan bruges til at downloade chatsoftware eller klientbaserede chatbeskeder.

**Professionelt netværk**: Websteder, der leverer professionelle netværkstjenester.

**Sociale netværk**: Websteder, der leverer sociale netværkstjenester.

**Webbaseret mail**: Websteder, der tilbyder webbaserede mailtjenester.
  
</details>

<details>
<summary>Uncategorized</summary>

**Nyligt registrerede domæner**: Websteder, der er blevet nyligt registreret inden for de seneste 30 dage, og som endnu ikke er blevet flyttet til en anden kategori.

**Parkerede domæner**: Websteder, der ikke har noget indhold eller parkeres til senere brug.
  
**BEMÆRK**! Ikke-kategoriseret indeholder kun nyligt registrerede domæner og parkerede domæner og omfatter ikke alle andre websteder uden for disse kategorier.
  
</details>

### <a name="create-a-policy"></a>Opret en politik

Hvis du vil tilføje en ny politik, skal du følge disse trin:

1. Vælg **Indstillinger** >  **Webindholdsfiltrering** > **+ Tilføj politik** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

2. Angiv et navn.

3. Vælg de kategorier, der skal blokeres. Brug udvidelsesikonet til fuldt ud at udvide hver overordnet kategori, og vælg specifikke kategorier for webindhold.

4. Angiv politikområdet. Vælg enhedsgrupperne for at angive, hvor politikken skal anvendes. Det er kun enheder i de valgte enhedsgrupper, der forhindres i at få adgang til websteder i de valgte kategorier.

   > [!IMPORTANT]
   > Hvis du bruger Defender for Business, gælder det ikke for et bestemt niveau. Spring dette trin over, og fortsæt til trin 5.

5. Gennemse oversigten, og gem politikken. Det kan tage op til to timer, før opdateringen af politikken gælder for de valgte enheder.

> [!NOTE]
> - Du kan installere en politik uden at vælge en hvilken som helst kategori i en enhedsgruppe. Denne handling opretter en politik, der kun tillader overvågning, for at hjælpe dig med at forstå brugeradfærd, før du opretter en blokpolitik.
> - Hvis du fjerner en politik eller ændrer enhedsgrupper på samme tid, kan det medføre en forsinkelse i udrulningen af politikken.
> - Blokering af kategorien "Ikke-kategoriseret" kan medføre uventede og uønskede resultater.

## <a name="end-user-experience"></a>Slutbrugeroplevelse

Blokeringsoplevelsen for tredjepartsunderstøttede browsere leveres af Network Protection, som giver en meddelelse på systemniveau, der giver brugeren besked om en blokeret forbindelse. Hvis du vil have en mere brugervenlig oplevelse i browseren, kan du overveje at bruge Microsoft Edge.

### <a name="allow-specific-websites"></a>Tillad bestemte websteder

Det er muligt at tilsidesætte den blokerede kategori i filtrering af webindhold for at tillade et enkelt websted ved at oprette en brugerdefineret indikatorpolitik. Den brugerdefinerede indikatorpolitik tilsidesætter politikken for filtrering af webindhold, når den anvendes på den pågældende enhedsgruppe.

Følg disse trin for at definere en brugerdefineret indikator:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> skal du gå til **Indstillinger** \> **URL-adresse til slutpunktsindikatorer** \>  \> **/****domænetilføj**\> element.

2. Angiv domænet for webstedet.

3. Angiv politikhandlingen til **Tillad**.

### <a name="dispute-categories"></a>Konfliktkategorier

Hvis du støder på et domæne, der er forkert kategoriseret, kan du bestride kategorien direkte fra portalen.

Hvis du vil bestride kategorien for et domæne, skal du gå til **Rapporter** \> **Web protection** \> **Web Content Filtering Details** \> **Domains**. På fanen Domæner i rapporter til filtrering af webindhold kan du se en ellipse ud for hvert af domænerne. Peg på denne ellipse, og vælg **Bestridelseskategori**.

Der åbnes et panel, hvor du kan vælge prioriteten og tilføje flere oplysninger, f.eks. den foreslåede kategori for omkategorisering. Når du har udfyldt formularen, skal du vælge **Send**. Vores team gennemgår anmodningen inden for én arbejdsdag. Hvis du vil fjerne blokeringen øjeblikkeligt, skal du oprette en [brugerdefineret tilladelsesindikator](indicator-ip-domain.md).

## <a name="web-content-filtering-cards-and-details"></a>Filtreringskort og oplysninger om webindhold

Vælg **Rapporter** \> **Webbeskyttelse** for at få vist kort med oplysninger om filtrering af webindhold og beskyttelse af webtrusler. Følgende kort indeholder oversigtsoplysninger om filtrering af webindhold.

### <a name="web-activity-by-category"></a>Webaktivitet efter kategori

Dette kort viser de overordnede webindholdskategorier med den største stigning eller reduktion i antallet af adgangsforsøg. Forstå drastiske ændringer i webaktivitetsmønstre i din organisation fra de seneste 30 dage, 3 måneder eller 6 måneder. Vælg et kategorinavn for at få vist flere oplysninger.

I de første 30 dage, hvor denne funktion bruges, har din organisation muligvis ikke nok data til at vise disse oplysninger.

:::image type="content" source="images/web-activity-by-category600.png" alt-text="Webaktiviteten efter kategorikort" lightbox="images/web-activity-by-category600.png":::

### <a name="web-content-filtering--summary-card"></a>Oversigtskort til filtrering af webindhold

Dette kort viser distributionen af blokerede adgangsforsøg på tværs af de forskellige overordnede webindholdskategorier. Vælg en af de farvede søjler for at få vist flere oplysninger om en bestemt overordnet webkategori.

:::image type="content" source="images/web-content-filtering-summary.png" alt-text="Oversigtskortet til filtrering af webindhold" lightbox="images/web-content-filtering-summary.png":::

### <a name="web-activity-summary-card"></a>Oversigtskort for webaktivitet

Dette kort viser det samlede antal anmodninger om webindhold i alle URL-adresser.

:::image type="content" source="images/web-activity-summary.png" alt-text="Oversigtskortet for webaktivitet" lightbox="images/web-activity-summary.png":::

### <a name="view-card-details"></a>Vis kortoplysninger

Du kan få adgang til **oplysningerne om rapporten** for hvert kort ved at vælge en tabelrække eller en farvet søjle i diagrammet på kortet. Siden med rapportoplysninger for hvert kort indeholder omfattende statistiske data om webindholdskategorier, webstedsdomæner og enhedsgrupper.

:::image type="content" source="images/web-protection-report-details.png" alt-text="Oplysninger om webbeskyttelsesrapporten" lightbox="images/web-protection-report-details.png":::

- **Webkategorier**: Viser de webindholdskategorier, der har haft adgangsforsøg i din organisation. Vælg en bestemt kategori for at åbne et oversigts-pop op-vindue.

- **Domæner**: Viser de webdomæner, der er blevet åbnet eller blokeret i din organisation. Vælg et bestemt domæne for at få vist detaljerede oplysninger om det pågældende domæne.

- **Enhedsgrupper**: Viser alle de enhedsgrupper, der har genereret webaktivitet i din organisation

Brug filteret for tidsinterval øverst til venstre på siden til at vælge en tidsperiode. Du kan også filtrere oplysningerne eller tilpasse kolonnerne. Vælg en række for at åbne en pop op-rude med endnu flere oplysninger om det valgte element.

### <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

Kun Microsoft Edge understøttes, hvis enhedens operativsystemkonfiguration er Server (**cmd** \> **Systeminfo** \> **OS Configuration**). Netværksbeskyttelse understøttes kun i tilstanden Undersøg på serverenheder, som er ansvarlig for at beskytte trafik på tværs af understøttede tredjepartsbrowsere.

Det er kun Microsoft Edge, der understøttes, og Network Protection understøttes ikke på Windows 10 Azure Virtual Desktop-værter med flere sessioner.

Network Protection understøtter i øjeblikket ikke SSL-inspektion, hvilket kan resultere i, at nogle websteder tillades af filtrering af webindhold, som normalt ville blive blokeret. Websteder vil blive tilladt på grund af manglende synlighed i krypteret trafik, efter at TLS-håndtrykket har fundet sted, og en manglende evne til at fortolke visse omdirigeringer.  Dette omfatter omdirigeringer fra nogle webbaserede maillogonsider til postkassesiden. Som en accepteret løsning kan du oprette en brugerdefineret blokeringsindikator for logonsiden for at sikre, at ingen brugere kan få adgang til webstedet. Vær opmærksom på, at dette kan blokere deres adgang til andre tjenester, der er knyttet til det samme websted. 

## <a name="see-also"></a>Se også

- [Oversigt over webbeskyttelse](web-protection-overview.md)
- [Beskyttelse mod webtrusler](web-threat-protection.md)
- [Overvåge websikkerhed](web-protection-monitoring.md)
- [Svar på webtrusler](web-protection-response.md)
- [Krav til netværksbeskyttelse](web-content-filtering.md)
