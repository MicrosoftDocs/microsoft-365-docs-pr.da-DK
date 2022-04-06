---
title: Afhjælpe ondsindede mails, der blev leveret i Office 365
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
description: Trussels afhjælpning
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3ba8564ef5ecbd261dc47b2f0a48d6d4d77d620a
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64638294"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Afhjælpe skadelig mail leveret i Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

Afhjælpning betyder, at du skal tage en bestemt handling mod en trussel. Ondsindede mails, der sendes til din organisation, kan ryddes op enten af systemet, via automatisk tømning i nul timer (ZAP) eller af sikkerhedsteams via afhjælpningshandlinger som f.eks. flytning til *indbakke, flytning* til uønsket *mail, flytning* til slettede *elementer, blød* sletning eller hård *sletning.* Microsoft Defender for Office 365 Plan 2/E5 gør det muligt for sikkerhedsteams at løse trusler i mail- og samarbejdsfunktionalitet via manuel og automatisk undersøgelse.

> [!NOTE]
> For at afhjælpe ondsindede mails skal sikkerhedsteams have *tildelt rollen Søg* og Tøm. Rolletildelingen udføres [via tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Hvad du bør vide, før du begynder

Administratorer kan udføre nødvendige handlinger på mails, men for at få godkendt disse handlinger skal de have rollen Søg  og tøm tildelt i tilladelserne mail **&-samarbejde** i Microsoft 365 Defender-portalen. Uden den *søge- og sletterolle*, der er føjet til en af rollegrupperne, kan de ikke udføre handlingen.

## <a name="manual-and-automated-remediation"></a>Manuel og automatisk afhjælpning

*Manuel jagt* sker, når sikkerhedsteams identificerer trusler manuelt ved hjælp af søge- og filtreringsfunktionerne i Stifinder. Manuel mailløsning kan udløses via en hvilken som helst mailvisning (*Malware*, *Phish* eller Alle *mails), når* du har identificeret et sæt mails, der skal afhjælpes.

> [!div class="mx-imgBorder"]
> [![Skærmbillede af manuel Office 365 efter dato i Threat Explorer.](../../media/tp-RemediationArticle1.png)](../../media/tp-RemediationArticle1.png#lightbox)

Sikkerhedsteams kan bruge Stifinder til at vælge mails på flere måder:

- Vælg mails i hånden: Brug filtre i forskellige visninger. Vælg op til 100 mails, der skal afhjælpes.

- Forespørgselsvalg: Markér en hel forespørgsel ved hjælp af knappen **Markér alt øverst** . Den samme forespørgsel vises også i handlingscenter med oplysninger om mailindsendelse. Kunder kan sende maksimalt 200.000 mails fra Threat Explorer.  

- Udvælgelse af forespørgsler med udeladelse: Nogle gange kan sikkerhedsteams have brug for at løse mails ved at vælge en hel forespørgsel og udelukke bestemte mails fra forespørgslen manuelt. Det gør en administrator ved at bruge afkrydsningsfeltet **Markér alt** og rulle ned for at udelade mails manuelt. Forespørgslen kan maksimalt indeholde 1.000 mails. Det maksimale antal undtagelser er 100.

Når mails er markeret via Stifinder, kan du begynde at løse dem ved at gøre noget direkte eller ved at i kø til mails for en handling:

- Direkte godkendelse: Når handlinger som f.eks. flytning til *indbakke, flytning* til uønsket *mail, flytning* til slettede  *elementer, blød* sletning eller hård sletning vælges af sikkerhedsmedarbejdere, der har de rette tilladelser, og de næste trin i afhjælpningen følges, begynder afhjælpningsprocessen at udføre den valgte handling.
> [!NOTE]
>Efterhånden som afhjælpningen bliver kickstartet, genererer den en advarsel og en undersøgelse parallelt. Besked vises i køen til vigtige beskeder med navnet "Administrativ handling, der er indsendt af en administrator", der foreslår, at sikkerhedsmedarbejdere har løst en enhed. Den viser oplysninger som f.eks. navnet på den person, der udførte handlingen, linket til understøttende undersøgelse, klokkeslæt osv. Det fungerer rigtig godt at vide, hver gang en øjeblikkelig handling som afhjælpning udføres på enheder. Alle disse handlinger kan vises under fanen Handlinger & **HandlingscenterHistory** \>   ->  (offentlig eksempelvisning).

- Totrinsgodkendelse: En "Føj til afhjælpning"-handling kan udføres af administratorer, der ikke har de rette tilladelser, eller som skal vente på at udføre handlingen. I dette tilfælde føjes de målrettede mails til en afhjælpningsbeholder. Der kræves godkendelse, før afhjælpningen udføres.

**Automatiserede undersøgelses-** og svarhandlinger udløses af beskeder eller sikkerhedsteams fra Explorer. Disse kan omfatte anbefalede afhjælpningshandlinger, der skal godkendes af et sikkerhedsteam. Disse handlinger er inkluderet på **fanen Handling** i den automatiserede undersøgelse.

> [!div class="mx-imgBorder"]
> [![Mail med malware på siden "Zapped", der viser tidspunktet for udførelse af Zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Alle afhjælpninger (direkte godkendelser), der er oprettet i Stifinder, Avanceret jagt eller via Automatiseret undersøgelse, vises i Handlingscenter. Få adgang til disse via venstre **navigationspanel under & fanen Handlingshandlinger** \>   -> **i handlingscenterHistory**.

Alle afhjælpninger (direkte godkendelser), der er oprettet i Explorer eller Avanceret jagt eller via Automatiseret undersøgelse, vises i Handlingscenter. Få adgang til disse via venstre **navigationspanel under & fanen Handlingshandlinger** \>   -> **i handlingscenterHistory**. 

Manuelle handlinger, der afventer godkendelse ved hjælp af totrinsgodkendelsesprocessen (1. add to remediation by one security operation team member, 2. gennemgået og godkendt af et andet medlem af sikkerhedsteamet) kan kun ses i det ældre Defender for Office 365  \> handlingscenter **Gennemse handlingscenter** og ikke i hændelser/undersøgelser og i Unified Action Center.

> [!NOTE]
> Totrinsgodkendelse: Handlinger, der kun er tilgængelige i Office Handlingscenter  **, Gennemse** \> **handlingscenter**

:::image type="content" source="../../media/microsoft-365-defender-action-center-history.png" alt-text="Det samlede handlingscenter viser dig 30 dages afhjælpningshandlinger.":::

Samlet handlingscenter viser afhjælpningshandlinger for de seneste 30 dage. Handlinger, der er foretaget via Stifinder, angives efter det navn, som sikkerhedsteamet leverede, da afhjælpningen blev oprettet, samt godkendelses-id, undersøgelses-id. Handlinger, der udføres via automatiserede undersøgelser, har titler, der starter med den tilhørende besked, der udløste undersøgelsen, f.eks *. Zap-mailklynge*.

Åbn et afhjælpningselement for at få vist oplysninger om det, herunder dets afhjælpningsnavn, godkendelses-id, undersøgelses-id, oprettelsesdato, beskrivelse, status, handlingskilde, handlingstype, besluttet efter, status. Det åbner også en siderude med handlingsdetaljer, oplysninger om mailklynge, påmindelser og hændelsesoplysninger.

- *Siden Åben undersøgelse* åbner en administratorundersøgelse, der indeholder færre detaljer og faner. Den viser detaljer som f.eks.: relateret besked, enhed valgt til afhjælpning, foranstaltninger, der er taget, afhjælpningsstatus, enhedsantal, logfiler, godkender af handling. Denne undersøgelse holder styr på undersøgelsen, som udføres af administratoren manuelt, og indeholder detaljer til valg foretaget af administratoren, hvilket kaldes undersøgelse af administratorhandling. Der er ingen grund til at reagere på undersøgelsen og give besked om, at den allerede er i godkendt tilstand.   
- *Antal mails* Viser antallet af mails, der er sendt via Threat Explorer. Der kan gøres noget ved disse mails, eller der kan ikke gøres noget ved dem. 
- *Handlingslogfiler* Viser oplysninger om afhjælpningsstatus som vellykket/mislykket/ er allerede i destinationen

  > [!div class="mx-imgBorder"]
  > [![Skærmbillede af handlingscenteret med trusler, der kan handles på og ikke kan handle på.](../../media/tp-RemediationArticle5.png)](../../media/tp-RemediationArticle5.png#lightbox)

  - **Det kan der** gøres noget ved: Mails på følgende skybaserede postkasseplaceringer kan reageres på og flyttes:
    - Indbakke
    - Uønsket
    - Slettet mappe
    - Blød-slettet mappe

      > [!NOTE]
      > I øjeblikket er det kun en bruger med adgang til postkassen, der kan gendanne elementer fra en blød-slettet mappe.

  - **Ikke muligt at handle** på: Mails på følgende placeringer kan ikke reageres på eller flyttes i afhjælpningshandlinger:
    - Karantæne
    - Permanent slettet mappe
    - Lokal/ekstern
    - Mislykkedes/tabt

  Mistænkelige meddelelser kategoriseres som enten afhjælpende eller ikke-umiddelbar. I de fleste tilfælde er det muligt at kombinere afhjælpende og ikke-øjeblikkelige meddelelser med det samlede antal sendte meddelelser. Men i sjældne tilfælde er dette muligvis ikke sandt. Dette kan ske på grund af systemforsinkninger, timeouts eller udløbne meddelelser. Meddelelser udløber baseret på stifinderens opbevaringsperiode for organisationen.

  Medmindre du afhjælper gamle meddelelser efter din organisations Stifinder-opbevaringsperiode, kan det anbefales at forsøge at løse problemer igen, hvis du ser taluoverensstemmelser. For systemforsinkelse opdateres afhjælpningsopdateringer typisk inden for et par timer.

  Hvis din organisations opbevaringsperiode for mail i Stifinder er 30 dage, og du afhjælper mails, der går 29-30 dage tilbage, tælles antallet af mailindsendelser muligvis ikke altid sammen. Mailsne kan være begyndt at bevæge sig ud af opbevaringsperioden allerede.

  Hvis afhjælpningerne sidder fast i tilstanden "I gang" i et stykke tid, er det sandsynligvis på grund af systemforsinkelser. Det kan tage op til et par timer at afhjælpe dette. Du kan få vist variationer i antallet af mailindsendelser, da nogle af disse mails muligvis ikke blev medtaget i forespørgslen i starten af afhjælpningen på grund af systemforsinkelse. Det er en god ide at forsøge at løse i sådanne tilfælde igen.

  > [!NOTE]
  > For at få de bedste resultater bør afhjælpningen udføres i batches på 50.000 eller færre.

  Der reageres kun på afhjælpende mails under afhjælpningen. Mails, der ikke er direkte, kan ikke afhjælpes af Office 365, da de ikke gemmes i skybaserede postkasser.

  Administratorer kan foretage handlinger på mails, der er i karantæne, hvis det er nødvendigt, men disse mails udløber uden for karantæne, hvis de ikke bliver fjernet manuelt. Som standard er mails, der er sat i karantæne på grund af skadeligt indhold, ikke tilgængelige for brugerne, så sikkerhedsmedarbejdere behøver ikke at gøre noget for at fjerne trusler i karantæne. Hvis disse mails er lokale eller eksterne, kan brugeren kontaktes for at adressere den mistænkelige mail. Eller administratorer kan bruge separate mailserver-/sikkerhedsværktøjer til fjernelse. Disse mails kan identificeres ved at anvende *det eksterne filter leveringsplacering = i* Stifinder. For mislykkede eller mislykkede mails eller mails, der ikke er tilgængelige for brugere, vil der ikke være nogen mails at reducere, da disse mails ikke når postkassen.

 
- **Handlingslogfiler**: Dette viser de meddelelser, der afhjælpes, er gennemført, mislykkedes, allerede i destinationen.

  Status kan være:

  - **Startet**: Der udløses afhjælpning.
    - **I kø**: Afhjælpning er sat i kø til afhjælpning af mails.
    - **I gang**: Afhjælpning er i gang.
    - **Fuldført**: Afhjælpning i alle mails, der kan afhjælpes, enten fuldført eller med visse fejl.
    - **Mislykkedes**: Der blev ikke fundet nogen afhjælpninger.

  Da der kun kan reageres på afhjælpende mails, vises oprydningen i hver mail som fuldført eller mislykket. Fra de samlede afhjælpende mails rapporteres vellykkede og mislykkede afhjælpninger.

  - **Succes**: Den ønskede handling for afhjælpelige mails blev udført. For eksempel: En administrator ønsker at fjerne mails fra postkasser, så administratoren gør noget ved blød sletning af mails. Hvis en genoprettelig mail ikke findes i den oprindelige mappe, efter handlingen er udført, vises status som fuldført.

  - **Fejl**: Den ønskede handling for afhjælpelige mails mislykkedes. For eksempel: En administrator ønsker at fjerne mails fra postkasser, så administratoren gør noget ved blød sletning af mails. Hvis en genoprettelig mail stadig findes i postkassen, efter handlingen er udført, vises status som mislykket.
  
  - **Allerede på destinationen**: Den ønskede handling blev allerede taget på mailen ELLER mailen fandtes allerede i destinationsplaceringen. For eksempel: En mail blev blød-slettet af administratoren via Stifinder på dag ét. Derefter vises lignende mails på dag 2, som igen slettes blød af administratoren. Når du markerer disse mails, ender administratoren med at vælge nogle mails fra dag ét, der allerede er blød-slettet. Nu vil disse mails ikke blive reageret på igen, de vises blot som "allerede i destinationen", da der ikke blev foretaget nogen handling på dem, som de fandtes på destinationsplaceringen.

  - **Ny**: Der *er blevet tilføjet en allerede* i destinationskolonnen i handlingsloggen. Denne funktion bruger den seneste leveringsplacering i Threat Explorer til at signalere, hvis mailen allerede er blevet løst. *Hvis sikkerhedsteamene allerede* er på destinationen, kan de forstå det samlede antal meddelelser, der stadig skal behandles.

Du kan kun udføre handlinger for meddelelser i mapperne Indbakke, Uønsket, Slettet og Blød-slettet i Threat Explorer. Her er et eksempel på, hvordan den nye kolonne fungerer. Der *foretages en blød* sletning på den meddelelse, der findes i indbakken, og derefter håndteres meddelelsen i overensstemmelse med politikkerne. Næste gang der udføres en blød sletning, vises denne meddelelse under kolonnen "Allerede i destinationen", som signalerer, at den ikke skal behandles igen.

Vælg et element i handlingsloggen for at få vist afhjælpningsdetaljer. Hvis der står "vellykket" eller "blev ikke fundet i postkassen", er elementet allerede blevet fjernet fra postkassen. Nogle gange er der en systemfejl under afhjælpning. I disse tilfælde er det en god ide at prøve afhjælpningshandlingen igen.

Hvis du vil afhjælpe store batches af mails, skal du eksportere de meddelelser, der er sendt til afhjælpning via mailindsendelse, og meddelelser, der er løst via handlingslogfiler. Eksportgrænsen øges til 100.000 poster.

 Administratorer kan udføre afhjælpningshandlinger som f.eks. at flytte mails til mappen Uønsket mail, Indbakke eller Slettet post og slette handlinger som f.eks. blød sletning eller hård sletning fra avancerede rodsider.

:::image type="content" source="../../media/microsoft-365-defender-advanced-hunting-actions-pane.png" alt-text="Panelet Avanceret jagt, Gennemtag handlinger med dit valg af handlinger.":::

Afhjælpning afhjælper trusler, adresserer mistænkelige mails og hjælper med at holde en organisation sikker.
