---
title: Ofte stillede spørgsmål og overvejelser i forbindelse med udrulning af kursus i angrebssimulering
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection: m365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om overvejelser i forbindelse med udrulning og ofte stillede spørgsmål om simulering af angreb og oplæring i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2-organisationer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 50f82d975e9dc4f534f9223b85fd9e841a3ad725
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490481"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Ofte stillede spørgsmål og overvejelser i forbindelse med udrulning af kursus i angrebssimulering

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Oplæring i simulering af angreb gør det muligt for Microsoft 365 E5- eller Microsoft Defender for Office 365 Plan 2-organisationer at måle og administrere risici inden for social engineering ved at tillade oprettelse og administration af phishing-simuleringer, der er drevet af den virkelige verden, de-våbeniserede phishing-nyttedata. Hyper-målrettet træning, der leveres i partnerskab med Terranova security, hjælper med at forbedre viden og ændre medarbejdernes adfærd.

Du kan finde flere oplysninger om at komme i gang med oplæringen af simulering af angreb under [Kom i gang med at bruge træningen til simulering af angreb](attack-simulation-training-get-started.md).

Mens hele simuleringsoprettelses- og planlægningsoplevelsen er designet til at være fristrøms- og friktionsfri, kræver det ofte planlægning at køre simuleringer i virksomhedsskala. Denne artikel hjælper med at håndtere specifikke udfordringer, som vi ser, når vores kunder kører simuleringer i deres egne miljøer.

## <a name="issues-with-end-user-experiences"></a>Problemer med slutbrugeroplevelser

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>URL-adresser til phishing-simulering blokeret af Google Safe Browsing

En TJENESTE til URL-omdømme identificerer muligvis en eller flere af de URL-adresser, der bruges af oplæringen i simulering af angreb som usikre. Google Sikker browsing i Google Chrome blokerer nogle af de simulerede phishing-URL-adresser med en **meddelelse om vildledende websted forude** . Selvom vi arbejder med mange leverandører af URL-omdømme for altid at tillade vores simulerings-URL-adresser, har vi ikke altid fuld dækning.

:::image type="content" source="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png" alt-text="Advarsel om vildledende websted i Google Chrome" lightbox="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png":::

Bemærk, at dette problem ikke påvirker Microsoft Edge.

Som en del af planlægningsfasen skal du kontrollere tilgængeligheden af URL-adressen i dine understøttede webbrowsere, før du bruger URL-adressen i en phishing-kampagne. Hvis URL-adresserne er blokeret af Google Safe Browsing, [skal du følge denne vejledning](https://support.google.com/chrome/a/answer/7532419) fra Google for at give adgang til URL-adresserne.

Se [Oplæring i at komme i gang med at bruge simulering af angreb](attack-simulation-training-get-started.md) for at få vist en liste over URL-adresser, der i øjeblikket bruges af træningen til simulering af angreb.

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Phishingsimulerings- og administrator-URL-adresser, der er blokeret af netværksproxyløsninger og filterdrivere

Både URL-adresser til phishing-simulering og administrator-URL-adresser kan blive blokeret eller droppet af dine mellemliggende sikkerhedsenheder eller filtre. Eksempel:

- Firewalls
- WAF-løsninger (Web Application Firewall)
- Filterdrivere fra tredjepart (f.eks. kernetilstandsfiltre)

Selvom vi har set få kunder blive blokeret på dette lag, sker det. Hvis du støder på problemer, kan du overveje at konfigurere følgende URL-adresser for at omgå scanning fra dine sikkerhedsenheder eller filtre efter behov:

- De simulerede phishing-URL-adresser som beskrevet i [Kom i gang med at bruge oplæring i simulering af angreb](attack-simulation-training-get-started.md).
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Simuleringsmeddelelser leveres ikke til alle målrettede brugere

Det er muligt, at antallet af brugere, der rent faktisk modtager simuleringsmails, er mindre end antallet af brugere, der blev målrettet af simuleringen. Følgende typer brugere udelades som en del af målvalideringen:

- Ugyldige modtagermailadresser.
- Gæstebrugere.
- Brugere, der ikke længere er aktive i Azure Active Directory (Azure AD).

Det er kun gyldige brugere, der ikke er gæstebrugere med en gyldig postkasse, der medtages i simuleringer. Hvis du bruger distributionsgrupper eller mailaktiverede sikkerhedsgrupper til målbrugere, kan du bruge cmdlet'en [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) til at få vist og validere medlemmer af distributionsgruppen.

## <a name="issues-with-attack-simulation-training-reporting"></a>Problemer med oplæringsrapportering af simulering af angreb

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Oplæringsrapporter om simulering af angreb indeholder ingen aktivitetsoplysninger

Træning i simulering af angreb leveres med omfattende indsigt, der kan handles på, og som holder dig informeret om dine medarbejderes trusselsparathed. Hvis oplæringsrapporter om simulering af angreb ikke udfyldes med data, skal du kontrollere, at søgning i overvågningsloggen er slået til i din organisation (den er som standard slået til).

Søgning i overvågningslog er påkrævet ved oplæring af simulering af angreb, så hændelser kan registreres, registreres og læses tilbage. Deaktivering af søgning i overvågningslog har følgende konsekvenser for oplæringen af simulering af angreb:

- Rapporteringsdata er ikke tilgængelige på tværs af alle rapporter. Rapporterne vil se tomme ud.
- Oplæringsopgaver er blokeret, fordi data ikke er tilgængelige.

Hvis du vil slå søgning i overvågningslog til, skal du se [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Tomme aktivitetsoplysninger kan også skyldes, at der ikke tildeles E5-licenser til brugerne. Bekræft, at mindst én E5-licens er tildelt en aktiv bruger for at sikre, at rapporteringshændelser registreres og registreres.

### <a name="simulation-reports-are-not-updated-immediately"></a>Simuleringsrapporter opdateres ikke med det samme

Detaljerede simuleringsrapporter opdateres ikke umiddelbart efter, at du har startet en kampagne. Bare rolig. denne funktionsmåde forventes.

Alle simuleringskampagner har en livscyklus. Når simuleringen oprettes første gang, er den i tilstanden **Planlagt** . Når simuleringen starter, skifter den til tilstanden **I gang** . Når det er fuldført, overgår simuleringstilstanden til tilstanden **Fuldført** .

Mens en simulering er i tilstanden **Planlagt** , er simuleringsrapporterne for det meste tomme. I denne fase løser simuleringsprogrammet mailadresserne for destinationsbrugeren, udvider distributionsgrupper, fjerner gæstebrugere fra listen osv.:

:::image type="content" source="../../media/attack-sim-training-faq-scheduled-state.png" alt-text="Simuleringsoplysninger, der viser simuleringen i tilstanden Planlagt" lightbox="../../media/attack-sim-training-faq-scheduled-state.png":::

Når simuleringen går ind i fasen **I gang** , vil du bemærke, at oplysninger begynder at sive ind i rapporteringen:

:::image type="content" source="../../media/attack-sim-training-faq-in-progress-state.png" alt-text="Simuleringsoplysninger, der viser simuleringen i tilstanden I gang" lightbox="../../media/attack-sim-training-faq-in-progress-state.png":::

Det kan tage op til 30 minutter, før de enkelte simuleringsrapporter opdateres efter overgangen til tilstanden **I gang** . Rapportdataene fortsætter med at blive oprettet, indtil simuleringen når tilstanden **Fuldført** . Rapporteringsopdateringer forekommer med følgende intervaller:

- Hvert 10. minut i de første 60 minutter.
- Hvert 15. minut efter 60 minutter indtil 2 dage.
- Hvert 30. minut efter 2 dage indtil 7 dage.
- Hvert 60. minut efter 7 dage.

Widgets på siden **Oversigt** giver et hurtigt øjebliksbillede af din organisations simuleringsbaserede sikkerhedsholdning over tid. Da disse widgets afspejler din overordnede sikkerhedsholdning og din rejse over tid, opdateres de, når hver simuleringskampagne er fuldført.

> [!NOTE]
> Du kan bruge indstillingen **Eksportér** på de forskellige rapporteringssider til at udtrække data.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Meddelelser, der er rapporteret som phishing af brugere, vises ikke i simuleringsrapporter

Simuleringsrapporter i Oplæring af angrebssimulator indeholder oplysninger om brugeraktivitet. Eksempel:

- Brugere, der har klikket på linket i meddelelsen.
- Brugere, der opgav deres legitimationsoplysninger.
- Brugere, der har rapporteret meddelelsen som phishing.

Hvis meddelelser, som brugere har rapporteret som phishing, ikke registreres i simuleringsrapporter om simulering af angrebssimulering, kan der være en regel for Exchange-mailflow (også kendt som en transportregel), der blokerer leveringen af de rapporterede meddelelser til Microsoft. Kontrollér, at alle regler for mailflow ikke blokerer levering til følgende mailadresser:

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- junk@office365.microsoft.com ikke\_

### <a name="users-are-assigned-training-after-they-report-a-simulated-message"></a>Brugerne tildeles oplæring, når de rapporterer en simuleret meddelelse

Hvis brugerne får tildelt oplæring, efter at de har rapporteret en phishingsimuleringsmeddelelse, skal du kontrollere, om din organisation har **konfigureret en brugerdefineret postkasse** i din **brugers indsendelsespolitik**. Når du konfigurerer en **brugerdefineret postkasse**, skal denne postkasse udelades fra politikker for sikre links og vedhæftede filer i henhold [til forudsætningerne for den brugerdefinerede postkasse](user-submission.md).

Hvis din organisation har konfigureret en **brugerdefineret postkasse** og ikke har konfigureret de påkrævede udeladelser, kan disse meddelelser blive detoneret, hvilket medfører oplæringsopgaver.

## <a name="other-frequently-asked-questions"></a>Andre ofte stillede spørgsmål

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>Spørgsmål: Hvad er den anbefalede metode til at målrette brugere til simuleringskampagner?

Svar: Der er flere tilgængelige indstillinger for målbrugere:

- Medtag alle brugere (i øjeblikket tilgængelige for organisationer med mindre end 40.000 brugere).
- Vælg bestemte brugere.
- Vælg brugere fra en CSV-fil (én mailadresse pr. linje).
- Azure AD gruppebaseret målretning.

Vi har opdaget, at kampagner, hvor de målrettede brugere identificeres af Azure AD grupper, generelt er nemmere at administrere.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>Spørgsmål: Er der nogen begrænsninger for målretning mod brugere, når du importerer fra en CSV eller tilføjer brugere?

Svar: Grænsen for import af modtagere fra en CSV-fil eller tilføjelse af individuelle modtagere til en simulering er 40.000.

En modtager kan være en individuel bruger eller en gruppe. En gruppe kan indeholde hundred- eller tusindvis af modtagere, så der er ikke en faktisk grænse for antallet af individuelle brugere.

Det kan være besværligt at administrere en stor CSV-fil eller tilføje mange individuelle modtagere. Brug af Azure AD grupper forenkler den overordnede administration af simuleringen.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>Spørgsmål: Leverer Microsoft nyttedata på andre sprog?

Svar: Der er i øjeblikket mere end 40 lokaliserede nyttedata tilgængelige på mere end 10 sprog: kinesisk (forenklet), kinesisk (traditionelt), engelsk, fransk, tysk, italiensk, japansk, koreansk, portugisisk, russisk, spansk og hollandsk. Vi har bemærket, at enhver direkte oversættelse eller maskinoversættelse af eksisterende nyttedata til andre sprog vil føre til unøjagtigheder og reduceret relevans.

Når det er sagt, kan du oprette din egen nyttedata på det sprog, du vælger, ved hjælp af den brugerdefinerede brugeroplevelse til oprettelse af nyttedata. Vi anbefaler også på det kraftigste, at du høster eksisterende nyttedata, der blev brugt til at målrette brugere i et bestemt geografisk område. Med andre ord skal du lade angriberne lokalisere indholdet for dig.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>Spørgsmål: Hvordan kan jeg skifte til andre sprog for min administrationsportal og uddannelse?

Svar: I Microsoft 365 eller Office 365 er sprogkonfigurationen specifik og centraliseret for hver brugerkonto. Du kan finde instruktioner til, hvordan du ændrer din sprogindstilling, [under Skift visningssprog og tidszone i Microsoft 365 for Business](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Bemærk, at det kan tage op til 30 minutter at synkronisere konfigurationsændringen på tværs af alle tjenester.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>Spørgsmål: Kan jeg udløse en testsimulering for at forstå, hvordan det ser ud, før jeg lancerer en færdig kampagne?

Svar: Ja, det kan du! På den allernyste side **med simulering af gennemsyn** i guiden til oprettelse af en ny simulering er der mulighed for at **sende en test**. Denne indstilling sender en eksempel på phishing-simulering til den bruger, der i øjeblikket er logget på. Når du har valideret phishing-meddelelsen i din indbakke, kan du sende simuleringen.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Knappen Send en test på siden Gennemse simulering" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>Spørgsmål: Kan jeg målrette brugere, der tilhører en anden lejer, som en del af den samme simuleringskampagne?

Sv.: Nej. Simuleringer på tværs af lejere understøttes ikke i øjeblikket. Bekræft, at alle dine målrettede brugere er i den samme lejer. Alle brugere på tværs af lejere eller gæstebrugere vil blive udelukket fra simuleringskampagnen.

### <a name="q-how-does-region-aware-delivery-work"></a>Spørgsmål: Hvordan fungerer levering, der er opmærksom på området?

Svar: Levering, der er opmærksom på områder, bruger attributten TimeZone for den målrettede brugers postkasse og logikken "ikke før" til at bestemme, hvornår meddelelsen skal leveres. Overvej f.eks. følgende scenarie:

- Kl. 07:00 i Pacific-tidszonen (UTC-8) opretter og planlægger en kampagne til at starte kl. 9:00 samme dag.
- UserA er i tidszonen Eastern (UTC-5).
- UserB er også i tidszonen Pacific.

Kl. 9:00 samme dag sendes simuleringsmeddelelsen til UserB. Med områdeorienteret levering sendes meddelelsen ikke til BrugerA samme dag, fordi kl. 9:00 Pacific time er kl. 12:00 Eastern time. Meddelelsen sendes i stedet til UserA kl. 9:00 Eastern time den følgende dag.

Så i den indledende kørsel af en kampagne med områdeorienteret levering aktiveret kan det se ud til, at simuleringsmeddelelsen kun blev sendt til brugere i en bestemt tidszone. Men efterhånden som tiden går, og flere brugere kommer i omfang, øges de målrettede brugere.


### <a name="q-does-microsoft-collect-or-store-any-information-that-users-enter-at-the-credential-harvest-sign-in-page-used-in-the-credential-harvest-simulation-technique"></a>Spørgsmål: Indsamler eller gemmer Microsoft oplysninger, som brugerne indtaster på logonsiden for Credential Harvest, og som bruges i simuleringsteknikken Til indsamling af legitimationsoplysninger?

Sv.: Nej. Alle oplysninger, der angives på logonsiden for indsamling af legitimationsoplysninger, kasseres uovervåget. Det er kun 'klik', der registreres for at registrere kompromishændelsen. Microsoft indsamler, logfører eller gemmer ikke oplysninger, som brugerne angiver på dette trin.
