---
title: Trinvis trusselsbeskyttelsesstak i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
ms.reviewer: gigarrub
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
description: Følg stien til en indgående meddelelse via trusselsfiltreringsstakken i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 4548beaf8d3071006114a65fd95c16b06e8a875d
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648167"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Trinvis trusselsbeskyttelse i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Den Microsoft Defender for Office 365 beskyttelse eller filtreringsstak kan opdeles i fire faser, som i denne artikel. Generelt passerer indgående mails alle disse faser før levering, men den faktiske sti, som mailen bruger, er underlagt en organisations Defender for Office 365 konfiguration.

> [!TIP]
> Hold øje indtil slutningen af denne artikel for en *samlet* grafik af alle 4 faser af Defender for Office 365 beskyttelse!

## <a name="phase-1---edge-protection"></a>Fase 1 – Edge Protection

Desværre er Edge-blokke, der engang var *kritiske* , nu relativt enkle for dårlige aktører at overvinde. Med tiden blokeres mindre trafik her, men det er stadig en vigtig del af stakken.  

Edge-blokke er designet til at være automatiske. I tilfælde af falske positive, vil afsendere blive underrettet og fortalte, hvordan de skal løse deres problem. Forbindelser fra partnere, der er tillid til, med begrænset omdømme kan sikre leveringsdygtighed, eller der kan indføres midlertidige tilsidesættelser, når nye slutpunkter onboardes.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Filtreringen fase 1 i Defender for Office 365" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png":::

1. **Netværksbegrænsning** beskytter Office 365 infrastruktur og kunder mod DOS-angreb (Denial of Service) ved at begrænse antallet af meddelelser, der kan sendes af et bestemt sæt infrastruktur.

2. **IP-omdømme og begrænsning** blokerer meddelelser, der sendes fra kendte forkerte forbindelse til IP-adresser. Hvis en bestemt IP-adresse sender mange meddelelser inden for kort tid, begrænses de.

3. **Domæneomdømme** blokerer alle meddelelser, der sendes fra et kendt ugyldigt domæne.

4. **Katalogbaserede kantfiltreringsblokke** forsøger at hente en organisations mappeoplysninger via SMTP.

5. **Registrering af backscatter** forhindrer, at en organisation angribes via ugyldige rapporter om manglende levering.

6. **Forbedret filtrering af connectorer** bevarer godkendelsesoplysninger, selvom trafikken passerer gennem en anden enhed, før den når Office 365. Dette forbedrer nøjagtigheden af filtreringsstakken, herunder heuristisk klyngedannelse, anti-spoofing og modeller til anti-phishing-maskinel indlæring, selv i komplekse eller hybride routingscenarier.

## <a name="phase-2---sender-intelligence"></a>Fase 2 – Afsenderintelligens

Funktioner i afsenderintelligens er vigtige for at fange spam, masse, repræsentation og uautoriseret spoof-meddelelser og også faktor i phish-registrering. De fleste af disse funktioner kan konfigureres individuelt.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="Fase 2 af filtrering i Defender for Office 365 er Sender intelligence" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png":::

1. Udløsere og beskeder til **registrering af kompromitterede** konti udløses, når en konto har unormal funktionsmåde, der er i overensstemmelse med kompromitteret adfærd. I nogle tilfælde er brugerkontoen blokeret og forhindret i at sende yderligere mails, indtil problemet er løst af en organisations sikkerhedsteam.

2. **Mailgodkendelse** omfatter både kundekonfigurerede metoder og metoder, der er konfigureret i cloudmiljøet, med det formål at sikre, at afsendere er godkendte, autentiske mailere. Disse metoder modstå spoofing.
    - **SPF** kan afvise mails, der er baseret på DNS TXT-poster, der viser IP-adresser og servere, som må sende mails på organisationens vegne.
    - **DKIM** leverer en krypteret signatur, der godkender afsenderen.
    - **DMARC** gør det muligt for administratorer at markere SPF og DKIM som påkrævet i deres domæne og gennemtvinger justering mellem resultaterne af disse to teknologier.
    - **ARC** er ikke kundekonfigureret, men bygger på DMARC til at arbejde med videresendelse på adresselister, mens der registreres en godkendelseskæde.

3. **Spoof intelligence** er i stand til at filtrere dem, der har tilladelse til at 'spoof' (dvs. dem, der sender mail på vegne af en anden konto eller videresender for en adresseliste) fra ondsindede afsendere, der efterligner organisatoriske eller kendte eksterne domæner. Det adskiller legitime "på vegne af" mail fra afsendere, der spoof til at levere spam og phishing-meddelelser.

    **Intern spoof intelligence** registrerer og blokerer spoof-forsøg fra et domæne i organisationen.

4. **Spoof intelligence på tværs af domæner** registrerer og blokerer spoof-forsøg fra et domæne uden for organisationen.

5. **Massefiltrering** gør det muligt for administratorer at konfigurere et massetillidsniveau (BCL), der angiver, om meddelelsen blev sendt fra en massesender. Administratorer kan bruge masseskyderen i Antispam-politikken til at beslutte, hvilket niveau af massemails der skal behandles som spam.

6. **Postkasseintelligens** lærer fra standardfunktionsmåder for brugermail. Den udnytter en brugers kommunikationsgraf til at registrere, hvornår en afsender kun ser ud til at være en person, som brugeren normalt kommunikerer med, men faktisk er ondsindet. Denne metode registrerer repræsentation.

7. **Repræsentation af postkasseintelligens** aktiverer eller deaktiverer forbedrede repræsentationsresultater baseret på hver brugers individuelle afsenderkort. Når funktionen er aktiveret, hjælper den med at identificere repræsentation.

8. **Bruger repræsentering** gør det muligt for en administrator at oprette en liste over mål med høje værdier, der sandsynligvis repræsenteres. Hvis der modtages en mail, hvor afsenderen kun ser ud til at have samme navn og adresse som den beskyttede konto med høj værdi, markeres eller mærkes mailen. (f.eks *. trα cye@contoso.com* for *tracye@contoso.com*).

9. **Domænerepræsentation** registrerer domæner, der ligner modtagerens domæne, og som forsøger at ligne et internt domæne. Denne repræsentation *tracye@liw α re.com* f.eks. for *tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Fase 3 – indholdsfiltrering

I denne fase begynder filtreringsstakken at håndtere det specifikke indhold af mailen, herunder links og vedhæftede filer.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="Fase 3-filtrering i MDO er indholdsfiltrering" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png":::

1. **Transportregler** (også kaldet regler for mailflow eller Exchange transportregler) gør det muligt for en administrator at udføre en lang række handlinger, når en meddelelse opfylder en lige så lang række betingelser. Alle meddelelser, der sendes gennem din organisation, evalueres i forhold til de aktiverede regler for mailflow/transport.

2. **Microsoft Defender Antivirus** og to *antivirusprogrammer fra tredjepart* bruges til at registrere al kendt malware i vedhæftede filer.

3. Antivirusprogrammer (AV) bruges også til true-type alle vedhæftede filer, så **typeblokering** kan blokere alle vedhæftede filer af typer, som administratoren angiver.

4. Når Microsoft Defender for Office 365 registrerer en skadelig vedhæftet fil, føjes filens hash og hash for dens aktive indhold til Exchange Online Protection (EOP)-omdømme. **Blokering af omdømme for vedhæftede filer** blokerer filen på tværs af alle Office 365 og på slutpunkter via MSAV-skykald.

5. **Heuristisk klyngedannelse** kan fastslå, at en fil er mistænkelig baseret på leverings-heuristik. Når der findes en mistænkelig vedhæftet fil, afbrydes hele kampagnen midlertidigt, og filen er sandkasse. Hvis filen er skadelig, blokeres hele kampagnen.

6. **Modeller til maskinel indlæring** fungerer på headeren, brødtekstindholdet og URL-adresserne i en meddelelse for at registrere phishingforsøg.

7. Microsoft bruger bestemmelse af omdømme fra SANDKASSE FOR URL-adresser samt URL-omdømme fra tredjepartsfeeds i **URL-omdømme, der blokerer** for meddelelser med en kendt skadelig URL-adresse.

8. **Indholds-heuristik** kan registrere mistænkelige meddelelser baseret på struktur og ordhyppighed i meddelelsens brødtekst ved hjælp af modeller til maskinel indlæring.

9. **Pengeskab sandkasser til vedhæftede filer** for Defender for Office 365 kunder ved hjælp af dynamisk analyse til at registrere trusler, der aldrig før er set.

10. **Detonation af sammenkædet indhold** behandler alle URL-adresser, der linker til en fil i en mail, som en vedhæftet fil, som asynkront sandboxing af filen på leveringstidspunktet.

11. **URL-detonation** sker, når upstream anti-phishing-teknologi finder en meddelelse eller URL-adresse for at være mistænkelig. URL-detonationssandkasser angiver URL-adresserne i meddelelsen på leveringstidspunktet.

## <a name="phase-4---post-delivery-protection"></a>Fase 4 – beskyttelse efter levering

Den sidste fase finder sted efter mail eller fillevering, der handler på mail, der er i forskellige postkasser og filer og links, der vises i klienter som Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Fase 4-filtrering i Defender for Office 365 er beskyttelse efter levering" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png":::

1. **Pengeskab Links** er Defender for Office 365 beskyttelsestid for klik. Alle URL-adresser i hver meddelelse ombrydes, så de peger på Microsoft Pengeskab Links-servere. Når der klikkes på en URL-adresse, kontrolleres den i forhold til det seneste omdømme, før brugeren omdirigeres til destinationswebstedet. URL-adressen er asynkront sandkasse for at opdatere dens omdømme.

2. **Zap (automatisk fjernelse på nul timer) for phishing** med tilbagevirkende kraft registrerer og neutraliserer skadelige phishing-meddelelser, der allerede er blevet leveret til Exchange Online postkasser.

3. **ZAP for malware** med tilbagevirkende kraft registrerer og neutraliserer meddelelser om skadelig malware, der allerede er blevet leveret til Exchange Online postkasser.

4. **ZAP for spam** med tilbagevirkende kraft registrerer og neutraliserer skadelige spammeddelelser, der allerede er blevet leveret til Exchange Online postkasser.

5. **Kampagnevisninger** giver administratorer mulighed for at se det store billede af et angreb hurtigere og mere fuldstændigt, end et hvilket som helst team kunne uden automatisering. Microsoft udnytter de store mængder data om anti-phishing, anti-spam og antimalware på tværs af hele tjenesten til at hjælpe med at identificere kampagner og giver derefter administratorer mulighed for at undersøge dem fra start til slut, herunder mål, virkninger og flow, som også er tilgængelige i en kampagneskrivning, der kan downloades.

6. **Tilføjelsesprogrammer til rapportmeddelelse** gør det nemt for brugerne at rapportere falske positiver (god mail, der ved en fejl er markeret som *dårlige*) eller falske negativer (dårlig mail markeret som *god*) til Microsoft for yderligere analyse.

7. **Pengeskab Links til Office-klienter** tilbyder den samme Pengeskab Link-tid til klik-beskyttelse i Office klienter, f.eks. Word, PowerPoint og Excel.

8. **Beskyttelse af OneDrive, SharePoint og Teams** giver den samme Pengeskab beskyttelse mod vedhæftede filer, indbygget i OneDrive, SharePoint og Microsoft Teams.

9. Når en URL-adresse, der peger på en fil, vælges efter levering, viser **detonation af sammenkædet indhold** en advarselsside, indtil sandkassen for filen er fuldført, og URL-adressen er sikker.

## <a name="the-filtering-stack-diagram"></a>Filtreringsstakdiagrammet

Det endelige diagram (som med alle dele af diagrammet, der udgør det) *kan ændres, efterhånden som produktet vokser og udvikler sig*. Bogmærke denne side, og brug den **feedbackindstilling** , du finder nederst, hvis du har brug for at spørge efter opdateringer. For dine poster er dette stakken med alle faserne i rækkefølge:

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="Alle faserne i filtrering i Defender for Office 365 i rækkefølge fra 1 til 4" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png":::

## <a name="more-information"></a>Flere oplysninger

Har du brug for at konfigurere Microsoft Defender for Office 365 ***lige nu** _? Brug denne stak, _now*, med [denne trinvise](protect-against-threats.md) vejledning til at begynde at beskytte din organisation.

*En særlig tak fra MSFTTracyP og dokumentationsskrivningsteamet til Giulian Garruba for dette indhold*.
