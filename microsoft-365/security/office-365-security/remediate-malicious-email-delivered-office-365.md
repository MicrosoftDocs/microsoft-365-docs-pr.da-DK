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
ms.openlocfilehash: 49cd5f532f41fd05090592136e28ca2462a9efd6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681166"
---
# <a name="remediate-malicious-email-delivered-in-office-365"></a>Afhjælpe skadelig mail leveret i Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)

Afhjælpning betyder, at du skal tage en bestemt handling mod en trussel. Ondsindede mails, der sendes til din organisation, kan ryddes op enten af systemet, via automatisk tømning i nul timer (ZAP) eller af sikkerhedsteams via afhjælpningshandlinger som f.eks. flytning til *indbakke, flytning* til uønsket *mail, flytning* til slettede *elementer, blød* sletning eller hård *sletning.* Microsoft Defender for Office 365 Plan 2/E5 gør det muligt for sikkerhedsteams at løse trusler i mail og samarbejdsfunktionalitet via manuel og automatisk undersøgelse.

> [!NOTE]
> For at afhjælpe ondsindede mails skal sikkerhedsteams have *tildelt rollen Søg* og Tøm. Rolletildelingen udføres [via tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

## <a name="what-you-need-to-know-before-you-begin"></a>Hvad du bør vide, før du begynder

Administratorer kan udføre nødvendige handlinger på mails, men for at få godkendt disse handlinger skal de have rollen Søg  og tøm tildelt i tilladelserne mail **&-samarbejde** i Microsoft 365 Defender-portalen. Uden den *søge- og sletterolle*, der er føjet til en af rollegrupperne, kan de ikke udføre handlingen.

## <a name="manual-and-automated-remediation"></a>Manuel og automatisk afhjælpning

*Manuel jagt* sker, når sikkerhedsteams identificerer trusler manuelt ved hjælp af søge- og filtreringsfunktionerne i Stifinder. Manuel mailløsning kan udløses via en hvilken som helst mailvisning (*Malware*, *Phish* eller Alle *mails), når* du har identificeret et sæt mails, der skal afhjælpes.

> [!div class="mx-imgBorder"]
> [![Manuel jagt på Office 365 Threat Explorer efter dato.](../../media/tp-RemediationArticle1.png)](../../media/tp-RemediationArticle1.png#lightbox)

Sikkerhedsteams kan bruge Stifinder til at vælge mails på flere måder:

- Vælg mails i hånden: Brug filtre i forskellige visninger. Vælg op til 100 mails, der skal afhjælpes.

- Forespørgselsvalg: Markér en hel forespørgsel ved hjælp af knappen **Markér alt øverst** . Den samme forespørgsel vises også i handlingscenter med oplysninger om mailindsendelse.

- Udvælgelse af forespørgsler med udeladelse: Nogle gange kan sikkerhedsteams have brug for at løse mails ved at vælge en hel forespørgsel og udelukke bestemte mails fra forespørgslen manuelt. Det gør en administrator ved at bruge afkrydsningsfeltet **Markér alt** og rulle ned for at udelade mails manuelt. Forespørgslen kan maksimalt indeholde 1.000 mails. Det maksimale antal undtagelser er 100.

Når mails er markeret via Stifinder, kan du begynde at løse dem ved at gøre noget direkte eller ved at i kø til mails for en handling:

- Direkte godkendelse: Når handlinger som f.eks. flytning til *indbakke, flytning* til uønsket *mail, flytning* til slettede  *elementer, blød* sletning eller hård sletning vælges af sikkerhedsmedarbejdere, der har de rette tilladelser, og de næste trin i afhjælpningen følges, begynder afhjælpningsprocessen at udføre den valgte handling. En midlertidig pop op-pop-op viser afhjælpningen, der er i gang.

- Totrinsgodkendelse: En "Føj til afhjælpning"-handling kan udføres af administratorer, der ikke har de rette tilladelser, eller som skal vente på at udføre handlingen. I dette tilfælde føjes de målrettede mails til en afhjælpningsbeholder. Der kræves godkendelse, før afhjælpningen udføres.

**Automatiserede undersøgelses-** og svarhandlinger udløses af beskeder eller sikkerhedsteams fra Explorer. Disse kan omfatte anbefalede afhjælpningshandlinger, der skal godkendes af et sikkerhedsteam. Disse handlinger er inkluderet på **fanen Handling** i den automatiserede undersøgelse.

> [!div class="mx-imgBorder"]
> [![Mail med malware på siden "Zapped", der viser tidspunktet for udførelse af Zap.](../../media/tp-RemediationArticle3.png)](../../media/tp-RemediationArticle3.png#lightbox)

Alle afhjælpninger (enten direkte godkendelse eller totrinsgodkendelse), der er oprettet i Stifinder, samt godkendte handlinger, der kommer fra automatiserede undersøgelser, vises i handlingscenteret. Få adgang til disse via navigationspanelet i venstre side under **Handlingscenter** \> **for gennemse**.

> [!div class="mx-imgBorder"]
> [![Handlingscenter med en liste over trusler efter dato og alvorsgrad.](../../media/tp-RemediationArticle4.png)](../../media/tp-RemediationArticle4.png#lightbox)

Handlingscenter viser alle afhjælpningshandlinger for de seneste 30 dage. Handlinger, der er foretaget via Stifinder, er angivet med det navn, som sikkerhedsteamet havde angivet, da afhjælpningen blev oprettet. Handlinger, der er foretaget gennem automatiserede undersøgelser, har titler, der starter med den tilhørende besked, der udløste undersøgelsen, f.eks. "Zap email cluster... ."

Åbn et afhjælpningselement for at få vist oplysninger om det, herunder navn, oprettelsesdato, beskrivelse, alvorlighed af trusler og status. Den viser også følgende to faner.

- **Fanen Mailindsendelse** : Viser antallet af mails, der er sendt via Threat Explorer, eller automatiserede undersøgelser, der skal afhjælpes. Der kan gøres noget ved disse mails, eller der kan ikke gøres noget ved dem.

  > [!div class="mx-imgBorder"]
  > [![Handlingscenter med brugbare og ikke-brugbare trusler.](../../media/tp-RemediationArticle5.png)](../../media/tp-RemediationArticle5.png#lightbox)

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

  Følgende billede viser, hvordan en indsendelse ser ud i Handlingscenter. En afhjælpning kan indeholde flere indsendelser. Hvis flere handlinger bliver godkendt gennem én automatiseret undersøgelse, vises hver mail- eller mailklyngehandling i den samme afhjælpning som en anden indsendelse.

  > [!div class="mx-imgBorder"]
  > [![Pop op-panel med mailklynge i ZAP.](../../media/tp-RemediationArticle6.png)](../../media/tp-RemediationArticle6.png#lightbox)

  Vælg et mailindsendelseselement for at få vist detaljerne for den pågældende afhjælpning, f.eks. forespørgslen (når afhjælpning udløses gennem automatiserede undersøgelser eller Stifinder ved at vælge en forespørgsel) og start- og sluttidspunktet for afhjælpningen. Den viser også en liste over meddelelser, der blev sendt til afhjælpning. Efterhånden som meddelelser flyttes ud af Stifinders opbevaringsperiode, forsvinder meddelelserne fra denne liste. Listen viser også individuelle meddelelser, der kan afhjælpes.

- **Handlingslogfiler**: Denne fane viser de afhjælpede meddelelser, herunder godkendt dato, administrator, der godkendte handlingen, handlingen, status og optællingen.

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

Afhjælpning afhjælper trusler, adresserer mistænkelige mails og hjælper med at holde en organisation sikker.
