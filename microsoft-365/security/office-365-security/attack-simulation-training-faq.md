---
title: Overvejelser i forbindelse med implementering af angrebssimulering og ofte stillede spørgsmål
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
description: Administratorer kan få mere at vide om overvejelser i forbindelse med installation og ofte stillede spørgsmål om simulering af angreb og kurser i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2-organisationer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 57b4d684e52fd51a2ece279cc7322389a953a17c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467791"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Overvejelser i forbindelse med implementering af angrebssimulering og ofte stillede spørgsmål

Kursus i simulering af angreb gør det muligt for Microsoft 365 E5- eller Microsoft Defender for Office 365 Plan 2-organisationer at måle og administrere sociale risici ved at tillade oprettelse og administration af phishing-simulering, der drives af virkelige phishing-nyttedata. Hyper-målrettet uddannelse, leveret i partnerskab med Novanova-sikkerhed, hjælper med at forbedre viden og ændre medarbejdernes adfærd.

Du kan finde flere oplysninger om at komme i gang med at bruge angrebssimuleringskursus [i Kom i gang med at bruge simulering af angreb](attack-simulation-training-get-started.md).

Mens hele simuleringsoprettelses- og planlægningsoplevelsen er designet til at være frit flydende og uden problemer, kræver kørsel af simulering på en virksomhedsskala ofte planlægning. Denne artikel er med til at tage hånd om specifikke udfordringer, som vi ser, når vores kunder kører simulering i deres egne miljøer.

## <a name="issues-with-end-user-experiences"></a>Problemer med slutbrugeroplevelser

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>URL-adresser til phishing-simulering blokeret af Google Pengeskab browsing

En URL-rytjeneste kan identificere en eller flere af de URL-adresser, der bruges af angrebssimuleringstræning, som usikre. Google Pengeskab i Google Chrome blokerer nogle af de simulerede phishing-URL-adresser med en meddelelse om **, at webstedet er vil være vildledende**. Vi arbejder med mange leverandører af URL-omdømme til altid at tillade vores SIM-webadresser, men vi har ikke altid fuld dækning.

:::image type="content" source="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png" alt-text="Advarsel om vildledende websted i Google Chrome" lightbox="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png":::

Bemærk, at dette problem ikke påvirker Microsoft Edge.

Som en del af planlægningsfasen skal du sørge for at kontrollere tilgængeligheden af URL-adressen i dine understøttede webbrowsere, før du bruger URL-adressen i en phishingkampagne. Hvis URL-adresserne er blokeret af Google Pengeskab browsing, skal du følge denne [vejledning](https://support.google.com/chrome/a/answer/7532419) fra Google for at tillade adgang til URL-adresserne.

Se Kom i [gang med at bruge simulering af angreb](attack-simulation-training-get-started.md) for listen over URL-adresser, der aktuelt bruges af simuleringskurser til angreb.

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Phishing-simulering og administratorwebadresser blokeret af netværksproxyløsninger og filtreringsdrivere

Både URL-adresser til phishing-simulering og administratorwebadresser kan blive blokeret eller afbrudt af dine mellemliggende sikkerhedsenheder eller filtre. Eksempel:

- Firewalls
- WAF-løsninger (Web Application Firewall)
- Tredjepartsfilterdrivere (f.eks. filtre i kernetilstand)

Vi har oplevet, at få kunder blev blokeret i dette lag, men det sker. Hvis du støder på problemer, kan du overveje at konfigurere følgende URL-adresser til at tilsidesætte scanning fra dine sikkerhedsenheder eller filtre efter behov:

- De simulerede phishing-URL-adresser som beskrevet i Kom i [gang med at bruge simulering af angreb](attack-simulation-training-get-started.md).
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Simuleringsmeddelelser leveres ikke til alle målrettede brugere

Det er muligt, at antallet af brugere, der faktisk modtager simuleringsmails, er mindre end antallet af brugere, der blev målrettet af simulering. Følgende typer af brugere udelades som en del af målvalideringen:

- Ugyldig modtagermailadresser.
- Gæstebrugere.
- Brugere, der ikke længere er aktive i Azure Active Directory (Azure AD).

Kun gyldige, ikke-gæstebrugere med en gyldig postkasse medtages i simuleringerne. Hvis du bruger distributionsgrupper eller mailaktiverede sikkerhedsgrupper til at målrette brugere, kan du bruge cmdlet'en [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) [i Exchange Online PowerShell til](/powershell/exchange/connect-to-exchange-online-powershell) at få vist og validere distributionsgruppemedlemmer.

## <a name="issues-with-attack-simulation-training-reporting"></a>Problemer med rapportering af angrebssimulering

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Træningsrapporter for angrebssimulering indeholder ingen aktivitetsoplysninger

Kursus om angrebssimulering leveres med omfattende, brugbar indsigt, der holder dig informeret om status for trusselsparathed for dine medarbejdere. Hvis træningsrapporter for angrebssimulering ikke er udfyldt med data, skal du kontrollere, at søgning i overvågningsloggen er aktiveret i din organisation (den er slået til som standard).

Søgning i overvågningsloggen er påkrævet af kursus i simulering af angreb, så hændelser kan registreres, optages og læses tilbage. Hvis du deaktiverer søgning i overvågningsloggen, har det følgende konsekvenser for kursus i angrebssimulering:

- Rapporteringsdata er ikke tilgængelige på tværs af alle rapporter. Rapporterne vil blive vist som tomme.
- Uddannelsestildelinger blokeres, fordi data ikke er tilgængelige.

Hvis du vil aktivere søgning i overvågningsloggen, skal [du se Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Oplysninger om tom aktivitet kan også skyldes, at der ikke tildeles E5-licenser til brugere. Kontrollér, at der er tildelt mindst én E5-licens til en aktiv bruger for at sikre, at rapporteringshændelser registreres og optages.

### <a name="simulation-reports-are-not-updated-immediately"></a>Simuleringsrapporter opdateres ikke med det samme

Detaljerede simuleringsrapporter opdateres ikke, umiddelbart efter du starter en kampagne. Bare rolig; denne funktionsmåde forventes.

Hver enkelt simuleringskampagne har en livscyklus. Når simulering blev oprettet, er simulering i **tilstanden** Planlagt. Når simulering starter, skiftes der til **statussen I** gang. Når den er fuldført, skiftes simuleringsovergange **til tilstanden** Fuldført.

Mens en simulering er **i den planlagte** tilstand, vil simuleringsrapporterne for det meste være tomme. I dette trin er simuleringsprogrammet i gang med at løse brugerens mailadresser, udvide distributionsgrupper, fjerne gæstebrugere fra listen osv.:

:::image type="content" source="../../media/attack-sim-training-faq-scheduled-state.png" alt-text="Simuleringsoplysninger, der viser simulering i den planlagte tilstand" lightbox="../../media/attack-sim-training-faq-scheduled-state.png":::

Når simuleringen går **ind i fasen** I gang, vil du bemærke oplysninger, der begynder at gå ind i rapporteringen:

:::image type="content" source="../../media/attack-sim-training-faq-in-progress-state.png" alt-text="Simuleringsdetaljer, der viser simulering i statussen I gang" lightbox="../../media/attack-sim-training-faq-in-progress-state.png":::

Det kan tage op til 30 minutter, før de enkelte simuleringsrapporter opdateres efter overgangen **til den igangværende** tilstand. Rapportdataene fortsætter med at opbygge, indtil simulering når **tilstanden Fuldført** . Rapporteringsopdateringer sker med følgende intervaller:

- Hvert 10. minut i de første 60 minutter.
- Hvert 15. minut efter 60 minutter indtil 2 dage.
- Hver 30. minut efter 2 dage indtil 7 dage.
- Hver 60. minut efter 7 dage.

Widgets på **siden Oversigt** giver et hurtigt øjebliksbillede af din organisations simuleringsbaserede sikkerhedsoverholdelse over tid. Da disse widgets afspejler din overordnede sikkerhed og rejse over tid, opdateres de, når hver simuleringskampagne er gennemført.

> [!NOTE]
> Du kan bruge indstillingen **Eksportér** på de forskellige rapporteringssider til at udtrække data.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Meddelelser, der rapporteres som phishing af brugere, vises ikke i simuleringsrapporter

Simuleringsrapporter i angrebskursus giver oplysninger om brugeraktivitet. Eksempel:

- Brugere, der klikkede på linket i meddelelsen.
- Brugere, der har opgivet deres legitimationsoplysninger.
- Brugere, der har rapporteret meddelelsen som phishing.

Hvis meddelelser, som brugere rapporterede som phishing, ikke registreres i simuleringsrapporter for angrebssimulering, kan der være en Exchange-regel for mailflow (også kaldet en transportregel), der blokerer leveringen af de rapporterede meddelelser til Microsoft. Kontrollér, at regler for mailflow ikke blokerer levering til følgende mailadresser:

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- not\_ junk@office365.microsoft.com

## <a name="other-frequently-asked-questions"></a>Andre ofte stillede spørgsmål

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>Sp: Hvad er den anbefalede metode til at målrette brugere mod simulering af kampagner?

A: Der findes flere forskellige muligheder for målbrugere:

- Medtag alle brugere (i øjeblikket tilgængelige for organisationer med mindre end 40.000 brugere).
- Vælg bestemte brugere.
- Vælg brugere fra en CSV-fil (én mailadresse pr. linje).
- Azure AD - gruppebaseret målretning.

Vi har fundet ud af, at kampagner, hvor de målrettede brugere identificeres af Azure AD-grupper, generelt er nemmere at administrere.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>Sp: Er der nogen begrænsninger i målretning af brugere, når de importerer fra en CSV-fil eller tilføjer brugere?

A: Grænsen for at importere modtagere fra en CSV-fil eller føje individuelle modtagere til en simulering er 40.000.

En modtager kan være en individuel bruger eller en gruppe. En gruppe kan indeholde hundred- eller tusindvis af modtagere, så en faktisk grænse er ikke sat på antallet af individuelle brugere.

Det kan være besværligt at administrere en stor CSV-fil eller tilføje mange individuelle modtagere. Brug af Azure AD-grupper forenkler den overordnede administration af simulering.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>Sp: Leverer Microsoft nyttedata på andre sprog?

A: I øjeblikket er der mere end 40 oversatte nyttedata tilgængelige på mere end 10 sprog: kinesisk (forenklet), kinesisk (traditionelt), engelsk, fransk, tysk, italiensk, japansk, koreansk, portugisisk, russisk, spansk og hollandsk. Vi har bemærket, at enhver direkte oversættelse eller maskinoversættelse af eksisterende nyttedata til andre sprog vil føre til unøjagtigheder og reduceret relevans.

Når det er sagt, kan du oprette din egen nyttedata på et sprog efter eget valg ved hjælp af den brugerdefinerede oprettelsesoplevelse af nyttedata. Vi anbefaler også på det kraftigste, at du høster eksisterende nyttedata, der blev brugt til at målrette brugerne i en bestemt geografi. Med andre ord, lad hackere lokalisere indholdet for dig.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>Sp: Hvordan kan jeg skifte til andre sprog for min administrationsportal og kursusoplevelse?

A: I Microsoft 365 eller Office 365 er sprogkonfiguration specifik og centraliseret for hver brugerkonto. Du kan finde en vejledning til, hvordan du ændrer din sprogindstilling, under Skift [visningssprog og tidszone i Microsoft 365 for Business](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Bemærk, at det kan tage op til 30 minutter at synkronisere konfigurationen på tværs af alle tjenester.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>Sp: Kan jeg udløse en testsimulering for at forstå, hvordan den ser ud, før jeg starter en fuldgyldig kampagne?

A: Ja, det kan du! På den sidste side **i Simulering** af simulering i guiden til at oprette en ny simulering er der mulighed for **at Sende en test**. Denne indstilling sender en eksempel på phishing-simuleringsmeddelelse til den bruger, der er logget på i øjeblikket. Når du har valideret phishingmeddelelsen i din indbakke, kan du indsende simulering.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Knappen Send en test på simuleringssiden Gennemse" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>Sp: Kan jeg målrette brugere, der tilhører en anden lejer som en del af den samme simuleringskampagne?

Sv.: Nej. I øjeblikket understøttes simuleringer ikke på tværs af lejere. Kontrollér, at alle dine målrettede brugere er i samme lejer. Alle brugere på tværs af lejere eller gæstebrugere vil blive udelukket fra simuleringskampagnen.

### <a name="q-how-does-region-aware-delivery-work"></a>Sp: Hvordan fungerer områdeafhængig levering?

A: Områdeafhængig levering bruger timezone-attributten for den målrettede brugers postkasse og logikken "ikke før" til at bestemme, hvornår meddelelsen skal leveres. Overvej f.eks. følgende scenarie:

- Kl. 07:00 i tidszonen i Pacific (UTC-8) opretter og planlægger en kampagne, der starter kl. 9:00 på samme dag.
- UserA er i den østlig tidszone (UTC-5).
- UserB er også i Pacific-tidszonen.

Kl. 9:00 på samme dag sendes simuleringsmeddelelsen til BrugerB. Med områdeafhængig levering sendes meddelelsen ikke til UserA på samme dag, fordi tidspunktet for 9:00 Pacific time er 12:00 Eastern time. I stedet sendes meddelelsen til UserA kl. 9:00 Østlig tid den følgende dag.

Så under den indledende kørsel af en kampagne, hvor områdespecifik levering er aktiveret, kan det se ud som om, simuleringsmeddelelsen kun blev sendt til brugere i en bestemt tidszone. Men efterhånden som tiden går, og flere brugere kommer ind i området, øges de målrettede brugere.
