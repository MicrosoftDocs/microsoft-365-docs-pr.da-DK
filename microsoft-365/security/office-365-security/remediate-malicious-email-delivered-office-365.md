---
title: Afhjælp skadelig mail, der blev leveret i Office 365
author: msfttracyp
ms.author: tracyp
manager: dansimp
ms.topic: article
ms.collection: M365-security-compliance
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: ''
search.appverid: MET150
description: Trusselsafhjælpning
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6102d1e7d3b7e39787c3787b8bc0851eedbdcefb
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115537"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Afhjælp skadelig mail leveret i Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Afhjælpning betyder at tage en foreskrevet handling mod en trussel. Ondsindet mail, der sendes til din organisation, kan ryddes op enten af systemet, via automatisk sletning på nul timer (ZAP) eller af sikkerhedsteams via afhjælpningshandlinger, f.eks. *flytning til indbakke*, *flytning til uønsket post*, *flytning til slettede elementer*, *blød sletning* eller *hård sletning*. Microsoft Defender for Office 365 Plan 2/E5 gør det muligt for sikkerhedsteams at afhjælpe trusler i mail- og samarbejdsfunktioner via manuel og automatiseret undersøgelse.

> [!NOTE]
> Sikkerhedsteams skal have tildelt rollen *Søg og Fjern* for at afhjælpe skadelige mails. Rolletildeling sker via [tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Det har du brug for at vide, før du begynder

Administratorer kan udføre de nødvendige handlinger på mails, men for at få disse handlinger godkendt skal de have tildelt rollen *Søg og Fjern* i **& samarbejdstilladelser** i Microsoft 365 Defender portalen. Uden at rollen *Søg og fjern føjes* til en af rollegrupperne, kan de ikke udføre handlingen.

Da mailhandlinger opretter automatiserede undersøgelser i backend, skal du aktivere *Automatiseret undersøgelse*. Gå til **Indstillinger** \> **Slutpunkter** \> **Avancerede funktioner**, og slå **Automatiseret undersøgelse** til.

## <a name="manual-and-automated-remediation"></a>Manuel og automatiseret afhjælpning

*Manuel jagt* finder sted, når sikkerhedsteams identificerer trusler manuelt ved hjælp af søge- og filtreringsfunktionerne i Stifinder. Manuel mailafhjælpning kan udløses via en hvilken som helst mailvisning (*malware*, *phish* eller *alle mails*), når du har identificeret et sæt mails, der skal afhjælpes.

:::image type="content" source="../../media/microsoft-365-defender-threat-explorer-manual-remediation.png" alt-text="Skærmbillede af manuel jagt i Office 365 Explorer efter dato.":::

Sikkerhedsteams kan bruge Stifinder til at vælge mails på flere måder:

- Vælg mails i hånden: Brug filtre i forskellige visninger. Vælg op til 100 mails for at afhjælpe.

- Valg af forespørgsel: Markér en hel forespørgsel ved hjælp af knappen **Vælg alle** øverst. Den samme forespørgsel vises også i oplysninger om afsendelse af mail i Handlingscenter. Kunder kan sende maksimalt 200.000 mails fra trusselsoversigten.  

- Valg af forespørgsel med udeladelse: Nogle gange vil sikkerhedshandlingers teams måske afhjælpe mails ved at vælge en hel forespørgsel og udelade visse mails fra forespørgslen manuelt. Det gør en administrator ved at bruge afkrydsningsfeltet **Markér alle** og rulle ned for at udelade mails manuelt. Forespørgslen kan maksimalt indeholde 1.000 mails. Det maksimale antal undtagelser er 100.

Når mails er valgt via Stifinder, kan du starte afhjælpningen ved at udføre direkte handling eller ved at lægge mails i kø for en handling:

- Direkte godkendelse: Når handlinger som *f.eks. flytning til indbakke*, *flytning til uønsket* post, *flytning til slettede elementer*, *blød sletning* eller *hård sletning* vælges af sikkerhedsafdelingen, der har de nødvendige tilladelser, og de næste trin i afhjælpningen følges, begynder afhjælpningsprocessen at udføre den valgte handling.
> [!NOTE]
> Da afhjælpningen bliver sparket i gang, genererer den en advarsel og en undersøgelse parallelt. Der vises en besked i beskedkøen med navnet "Administrativ handling sendt af en administrator", hvilket tyder på, at sikkerhedsafdelingen har udført afhjælpning af en enhed. Der vises oplysninger som f.eks. navnet på den person, der udførte handlingen, understøttende undersøgelseslink, tid osv. Det fungerer rigtig godt at vide, hver gang en hård handling som afhjælpning udføres på enheder. Alle disse handlinger kan spores under **fanen** **Handlinger & Oversigt over indsendelser** \> **i Løsningscenter**  ->  (offentlig prøveversion).

- Totrinsgodkendelse: En handling af typen "Føj til afhjælpning" kan udføres af administratorer, der ikke har de nødvendige tilladelser, eller som skal vente med at udføre handlingen. I dette tilfælde føjes de målrettede mails til en afhjælpningsobjektbeholder. Der kræves godkendelse, før afhjælpningen udføres.

**Automatiserede undersøgelses- og svarhandlinger** udløses af beskeder eller af sikkerhedshandlinger fra Stifinder. Disse kan omfatte anbefalede afhjælpningshandlinger, der skal godkendes af et team af sikkerhedshandlinger. Disse handlinger er inkluderet under fanen **Handling** i den automatiserede undersøgelse.

> [!div class="mx-imgBorder"]
> [![Mail med malware på siden "Zapped", der viser tidspunktet for Zap-udførelse.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Al afhjælpning (direkte godkendelser), der er oprettet i Stifinder, Avanceret jagt eller via automatiseret undersøgelse, vises i Løsningscenter. Få adgang til disse via navigationspanelet til venstre under fanen Handlinger &**Oversigt over** **indsendelser** \> **i Løsningscenter**  -> .

Alle afhjælpninger (direkte godkendelser), der blev oprettet i Stifinder eller Avanceret jagt eller via automatiseret undersøgelse, vises i Løsningscenter. Få adgang til disse via navigationspanelet til venstre under fanen Handlinger &**Oversigt over** **indsendelser** \> **i Løsningscenter**  -> . 

Manuelle handlinger, der afventer godkendelse, ved hjælp af godkendelsesprocessen med to trin (1. føje til afhjælpning af et medlem af sikkerhedshandlingsteamet, 2. gennemset og godkendt af et andet medlem af sikkerhedshandlingsteamet) er kun synlige i de ældre Defender for Office 365 Action Center **Review** \> **Action Center** og ikke i hændelser/undersøgelser og Unified Action Center.

> [!NOTE]
> Totrinsgodkendelse: Handlinger, der kun er tilgængelige i Office Action Center  **Gennemse** \> **Løsningscenter**

:::image type="content" source="../../media/microsoft-365-defender-action-center-history.png" alt-text="I det samlede løsningscenter kan du se 30 dages afhjælpningshandlinger.":::

Unified Action Center viser afhjælpningshandlinger for de seneste 30 dage. Handlinger, der udføres via Stifinder, er angivet med det navn, som sikkerhedsteamet angav, da afhjælpningen blev oprettet, samt godkendelses-id, undersøgelses-id. Handlinger, der udføres via automatiserede undersøgelser, har titler, der starter med den relaterede besked, der udløste undersøgelsen, f.eks. *Zap-mailklynge*.

Åbn et afhjælpningselement for at få vist detaljer om det, herunder afhjælpningsnavn, godkendelses-id, undersøgelses-id, oprettelsesdato, beskrivelse, status, handlingskilde, handlingstype, bestemt af, status. Der åbnes også en siderude med handlingsdetaljer, oplysninger om mailklynge, beskeder og oplysninger om hændelser.

- *Siden Åbn undersøgelse* åbner en administratorundersøgelse, der indeholder færre detaljer og faner. Den viser detaljer som: relateret besked, enhed, der er valgt til afhjælpning, udført handling, afhjælpningsstatus, antal enheder, logge, godkender af handling. Denne undersøgelse holder styr på den undersøgelse, som administratoren udfører manuelt, og indeholder oplysninger om valg foretaget af administratoren, og derfor kaldes den undersøgelse af administratorhandlinger. Ingen grund til at handle på undersøgelsen og alarm sin allerede i godkendt tilstand.
- *Antal mails* Viser antallet af mails, der er sendt via Threat Explorer. Disse mails kan være handlingsbare eller ikke handlingsvenlige.
- *Handlingslogge* Vis detaljer om afhjælpningsstatusser som f.eks. vellykket, mislykket og allerede på destinationen.

:::image type="content" source="../../media/microsoft-365-defender-action-center-history-panel.png" alt-text="Løsningscenter med indstillingen Flyt til indbakke åben.":::

  - **Handlingsbaseret**: Mails på følgende placeringer i en cloudpostkasse kan reageres på og flyttes:
    - Indbakke
    - Junk
    - Mappen Slettet
    - Mappe, der er slettet med blød sletning

      > [!NOTE]
      > I øjeblikket er det kun en bruger med adgang til postkassen, der kan gendanne elementer fra en mappe med blød sletning.

  - **Der kan ikke handles** på: Mails på følgende placeringer kan ikke reageres på eller flyttes i afhjælpningshandlinger:
    - Karantæne
    - Hard-deleted mappe
    - I det lokale miljø/eksternt
    - Mislykkedes/slippes

  Mistænkelige meddelelser er kategoriseret som enten afhjælpelige eller umiddelbart anvendelige. I de fleste tilfælde er kombinerbare og ikke-umiddelbart anvendelige meddelelser lig med det samlede antal sendte meddelelser. Men i sjældne tilfælde er dette muligvis ikke sandt. Dette kan ske på grund af systemforsinkelser, timeout eller udløbne meddelelser. Meddelelser udløber baseret på opbevaringsperioden i Stifinder for din organisation.

  Medmindre du afhjælper gamle meddelelser efter din organisations opbevaringsperiode i Stifinder, anbefales det at forsøge at afhjælpe elementer igen, hvis du ser uoverensstemmelser mellem antallet. I forbindelse med systemforsinkelser opdateres afhjælpningsopdateringer typisk inden for nogle få timer.

  Hvis din organisations opbevaringsperiode for mail i Stifinder er 30 dage, og du afhjælper mails, der går 29-30 dage tilbage, vil antallet af afsendelser af mails muligvis ikke altid blive tilføjet. Mails kan allerede være begyndt at blive flyttet ud af opbevaringsperioden.

  Hvis afhjælpninger sidder fast i tilstanden "Igangværende" i et stykke tid, er det sandsynligvis på grund af systemforsinkelser. Det kan tage op til et par timer at afhjælpe. Du kan se variationer i antallet af indsendelser af mails, da nogle af mails muligvis ikke er blevet inkluderet i forespørgslen i starten af afhjælpningen på grund af systemforsinkelser. Det er en god idé at forsøge at løse problemet igen i sådanne tilfælde.

  > [!NOTE]
  > For at opnå det bedste resultat skal afhjælpningen udføres i batches på 50.000 eller færre.

  Der reageres kun på mails, der kan afhjælpes, under afhjælpningen. Ikke-umiddelbare mails kan ikke afhjælpes af Office 365 mailsystem, da de ikke er gemt i cloudpostkasser.

  Administratorer kan udføre handlinger på mails i karantæne, hvis det er nødvendigt, men disse mails udløber uden for karantæne, hvis de ikke fjernes manuelt. Som standard er mails, der er sat i karantæne på grund af skadeligt indhold, ikke tilgængelige for brugere, så sikkerhedspersonalet behøver ikke at foretage sig noget for at slippe af med trusler i karantæne. Hvis mails er i det lokale miljø eller eksterne, kan brugeren kontaktes for at håndtere den mistænkelige mail. Eller administratorer kan bruge separate værktøjer til mailserver/sikkerhed til fjernelse. Disse mails kan identificeres ved at anvende *leveringsplaceringen =* eksternt filter i det lokale miljø i Stifinder. For mislykkede eller mistede mails eller mails, der ikke er tilgængelige for brugerne, vil der ikke være nogen mail, der kan afhjælpes, da disse mails ikke når postkassen.

 
- **Handlingslogge**: Dette viser de meddelelser, der er afhjælpet, lykkedes, mislykkedes, og som allerede findes på destinationen.

  Status kan være:

  - **Startet**: Afhjælpningen udløses.
    - **Sat i kø**: Afhjælpning er sat i kø til afhjælpning af mails.
    - **Igangværende**: Afhjælpning er i gang.
    - **Fuldført**: Afhjælpning af alle afhjælpende mails er enten fuldført eller med nogle fejl.
    - **Mislykket**: Ingen afhjælpninger lykkedes.

  Da det kun er afhjælpende mails, der kan reageres på, vises oprydningen i hver mail som vellykket eller mislykket. Fra de samlede afhjælpende mails rapporteres vellykkede og mislykkede afhjælpninger.

  - **Succes**: Den ønskede handling på afhjælpende mails blev gennemført. Eksempel: En administrator ønsker at fjerne mails fra postkasser, så administratoren foretager en blød sletning af mails. Hvis der ikke findes en mail, der kan afhjælpes, i den oprindelige mappe, når handlingen er udført, vises statussen som fuldført.

  - **Fejl**: Den ønskede handling på afhjælpende mails mislykkedes. Eksempel: En administrator ønsker at fjerne mails fra postkasser, så administratoren foretager en blød sletning af mails. Hvis der stadig findes en mail, der kan afhjælpes, i postkassen, når handlingen er udført, vises status som mislykket.
  
  - **Allerede i destinationen**: Den ønskede handling blev allerede udført på mailen eller den mail, der allerede fandtes på destinationsplaceringen. Eksempel: En mail blev slettet af administratoren via Stifinder den første dag. Derefter vises lignende mails på dag 2, som igen er bløde slettet af administratoren. Mens du vælger disse mails, ender administratoren med at hente nogle mails fra dag 1, der allerede er bløde slettet. Nu vil disse e-mails ikke blive reageret på igen, vil de bare vise som "allerede i destinationen", da der ikke blev truffet nogen handling på dem, som de fandtes i destinationen placering.

  - **Ny**: Der er tilføjet en *kolonne, der allerede findes i destinationskolonnen* , i handlingsloggen. Denne funktion bruger den seneste leveringsplacering i Threat Explorer til at signalere, om mailen allerede er blevet afhjælpet. *Allerede i destinationen* hjælper sikkerhedsteams med at forstå det samlede antal meddelelser, der stadig skal håndteres.

Handlinger kan kun udføres på meddelelser i mapperne Indbakke, Uønsket, Slettet og Blød slettet i Threat Explorer. Her er et eksempel på, hvordan den nye kolonne fungerer. Der udføres en *blød sletning* af den meddelelse, der findes i indbakken, og derefter håndteres meddelelsen i henhold til politikker. Næste gang der udføres en blød sletning, vises denne meddelelse under kolonnen 'Allerede i destination', der signalerer, at den ikke behøver at blive behandlet igen.

Vælg et element i handlingsloggen for at få vist oplysninger om afhjælpning. Hvis der står "vellykket" eller "ikke fundet i postkassen" i oplysningerne, er elementet allerede fjernet fra postkassen. Nogle gange er der en systemfejl under afhjælpning. I disse tilfælde er det en god idé at prøve afhjælpningshandlingen igen.

I tilfælde af afhjælpning af store batches af mail, skal du eksportere de meddelelser, der er sendt til afhjælpning via Indsendelse af mail, og meddelelser, der blev afhjælpet via handlingslogge. Eksportgrænsen øges til 100.000 poster.

 Administratorer kan udføre afhjælpningshandlinger, f.eks. flytte mails til mappen Uønsket mail, Indbakke eller Slettet post og slette handlinger som blød sletning eller hård sletning fra avancerede jagtsider.

:::image type="content" source="../../media/microsoft-365-defender-advanced-hunting-actions-pane.png" alt-text="Panelet Avanceret jagt, Handlinger med dit valg af handlinger.":::

Afhjælpning afhjælper trusler, adresserer mistænkelige mails og hjælper med at beskytte en organisation.
