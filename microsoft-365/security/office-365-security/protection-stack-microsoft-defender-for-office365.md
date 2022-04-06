---
title: Stak med trinvis trusselsbeskyttelse i Microsoft Defender til Office 365
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
ms.openlocfilehash: 62d7ac9f13f59fce3b635f6d1dace2f22ee7f503
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683817"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Trinvis trusselsbeskyttelse i Microsoft Defender for Office 365

Stakken Microsoft Defender Office 365 beskyttelse eller filtrering kan opdeles i 4 faser, som i denne artikel. Generelt gennemgår indgående mails alle disse faser før levering, men den faktiske sti, som mailen tager, er underlagt en organisations Defender for Office 365 konfiguration.

> [!TIP]
> Hold dig klar til slutningen af denne artikel for at få  en samlet grafik af alle 4 faser af Defender Office 365 beskyttelse!

## <a name="phase-1---edge-protection"></a>Fase 1 – Edge Protection

Desværre er Edge-blokke, der tidligere *var kritiske* , nu relativt simple for en dårlig løsning. Over tid blokeres mindre trafik her, men den forbliver en vigtig del af stakken.  

Edge-blokke er designet til at være automatiske. I tilfælde af falsk positiv får afsendere besked om, hvordan problemet skal håndteres. Forbindelser fra partnere, der er tillid til, med begrænset ry kan sikre leverance, eller midlertidige tilsidesættelser kan sættes på plads, når du onboarder nye slutpunkter.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Fase 1 af filtrering i Defender til Office 365 er Edge Protection.":::

1. **Netværksbegrænsning beskytter** Office 365-infrastruktur og kunder fra DOS-angreb (Denial of Service) ved at begrænse antallet af meddelelser, der kan sendes af et bestemt sæt infrastruktur.

2. **IP-omdømme og begrænsning blokerer meddelelser** , der sendes fra kendte dårlige forbindelses-IP-adresser. Hvis en bestemt IP sender mange meddelelser i en kort tidsperiode, bliver de begrænser.

3. **Domæneomseelse** blokerer alle meddelelser, der sendes fra et kendt dårligt domæne.

4. **Mappebaseret kantfiltrering** blokerer forsøg på at indsamle en organisations mappeoplysninger via SMTP.

5. **Backscatter-registrering** forhindrer en organisation i at blive angreb via ugyldige rapporter om manglende levering ( NDR'er).

6. **Udvidet filtrering for forbindelser bevarer godkendelsesoplysninger**, selv når trafikken passerer gennem en anden enhed, før den når Office 365. Dette forbedrer filtrering af staknøjagtighed, herunder heuristisk klyngedannelse, antispoofing og læringsmodeller til antiphishing-maskiner, selv når det er i komplekse eller hybride routingscenarier.

## <a name="phase-2---sender-intelligence"></a>Fase 2 – Afsenderintelligens

Funktioner i afsenderintelligens er afgørende for at modtage spam, masse, efterligning og uautoriserede spoof-meddelelser og også faktor til registrering af phish. De fleste af disse funktioner kan konfigureres enkeltvis.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="Fase 2 af filtrering i Defender for Office 365 er Sender Intelligence.":::

1. **Udløsere og påmindelser** om registrering af konto kompromitteres, når en konto har unormal adfærd, hvilket er i overensstemmelse med kompromis. I nogle tilfælde er brugerkontoen blokeret og forhindret i at sende yderligere mails, før problemet er løst af en organisations sikkerhedsteam.

2. **Mailgodkendelse** omfatter både kundekonfigurerede metoder og metoder, der er konfigureret i skyen, med henblik på at sikre, at afsendere er godkendt, autentiske mailere. Disse metoder modstå spoofing.
    - **SPF kan** afvise mails, der er baseret på DNS TXT-poster, som viser IP-adresser og servere, der har tilladelse til at sende mails på organisationens vegne.
    - **DKIM** leverer en krypteret signatur, der godkender afsenderen.
    - **DMARC** gør det muligt for administratorer at markere SPF og DKIM som påkrævet i deres domæne og gennemtvinger justering mellem resultaterne af disse to teknologier.
    - **ARC** er ikke kundekonfigureret, men bygger på DMARC til at arbejde med videresendelse i adresselister, mens der optages en godkendelseskæde.

3. **Efterlignet** intelligens kan filtrere dem, der har tilladelse til at 'spoof' (dvs. dem, der sender mails på vegne af en anden konto eller videresendelse for en adresseliste) fra ondsindede afsendere, der efterligner organisatoriske eller kendte eksterne domæner. Det adskiller legitime "på vegne af" mails fra afsendere, der forfalsker at levere spam- og phishingmeddelelser.

    **Intra-org spoof intelligence** registrerer og blokerer spoof forsøg fra et domæne i organisationen.

4. **Efterlignet intelligens på tværs af domæner** registrerer og blokerer spoof forsøg fra et domæne uden for organisationen.

5. **Massefiltrering giver** administratorer mulighed for at konfigurere et BCL (Bulk Confidence Level), der angiver, om meddelelsen blev sendt fra en masseafsender. Administratorer kan bruge masseskyderen i antispampolitikken til at beslutte, hvilket niveau af massemail der skal behandles som spam.

6. **Postkasseintelligens** lærer af standardbrugerens mailfunktionsmåder. Den udnytter en brugers kommunikationsgraf til at registrere, når en afsender kun ser ud til at være en person, som brugeren normalt kommunikerer med, men faktisk er skadelig. Denne metode registrerer efterligning.

7. **Postkasse intelligence-repræsentation aktiverer** eller deaktiverer udvidede repræsentationsresultater baseret på hver brugers individuelle afsenderkort. Når denne funktion er aktiveret, hjælper den med at identificere efterligning.

8. **Bruger efterligning giver** en administrator mulighed for at oprette en liste over mål med høj værdi, der sandsynligvis vil blive udgivet som efterligning. Hvis der modtages en mail, hvor afsenderen kun ser ud til at have samme navn og adresse som den beskyttede konto med høj værdi, markeres eller mærkes mailen. (For eksempel *trα cye@contoso.com* for *tracye@contoso.com*).

9. **Domænereligation** registrerer domæner, der ligner modtagerens domæne, og som forsøger at ligne et internt domæne. Denne efterligning tracye@liw *α re.com* f.eks *. tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Fase 3 – Indholdsfiltrering

I denne fase begynder filtreringsstakken at håndtere det specifikke indhold i mailen, herunder dens links og vedhæftede filer.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="Fase 3 af filtrering i MDO er Indholdsfiltrering.":::

1. **Transportregler** (også kaldet regler for mailflow eller Exchange-transportregler) giver en administrator mulighed for at udføre en lang række handlinger, når en lige så lang række betingelser er opfyldt for en meddelelse. Alle meddelelser, der flyder gennem din organisation, evalueres i forhold til de aktiverede regler for mailflow/transport.

2. **Microsoft Defender Antivirus** og to *tredjeparts antivirusprogrammer bruges til at* registrere al kendt malware i vedhæftede filer.

3. Antivirusprogrammer (AV) bruges også til at skrive alle vedhæftede filer i sand tekst, så blokering af type  kan blokere alle vedhæftede filer af typer, som administratoren angiver.

4. Når Microsoft Defender til Office 365 registrerer en ondsindet vedhæftet fil, føjes filens hash samt en hash hash for det aktive indhold til Exchange Online Protection (EOP)-omdømme. **Blokering af vedhæftede** filers omdømme blokerer denne fil på tværs Office 365 alle slutpunkter og slutpunkter via MSAV-skyopkald.

5. **Heuristisk klyngedannelse kan** afgøre, at en fil er mistænkelig baseret på leverings heuristics. Når der findes en mistænkelig vedhæftet fil, afbrydes hele kampagnen midlertidigt, og filen sandkasse. Hvis filen bliver fundet skadelig, blokeres hele kampagnen.

6. **Modeller til maskinel** indlæring fungerer på sidehovedet, brødteksten og URL-adresserne for en meddelelse til at registrere forsøg på phishing.

7. Microsoft bruger en bestemmelse af omdømme som følge af sandkasse af URL-adresser samt URL-omdømme fra tredjepartsfeeds, der er blokeret for **URL-adresser**, til at blokere enhver meddelelse med en kendt ondsindet URL-adresse.

8. **Indholds heuristics** kan registrere mistænkelige meddelelser baseret på struktur og ordfrekvens i meddelelsens brødtekst ved hjælp af maskinlæringsmodeller.

9. **Pengeskab vedhæftede filer** sandkasser alle vedhæftede filer til Defender Office 365 kunder ved hjælp af dynamisk analyse til at registrere trusler, der aldrig før er set.

10. **Sammenkædet indholdsdeonation** behandler alle URL-adresser, der linker til en fil i en mail, som en vedhæftet fil, asynkront sandkasse af filen på leveringstidspunktet.

11. **URL-detonation** sker, når en opstrøms antiphishing-teknologi finder en meddelelse eller URL-adresse, der er mistænkelig. URL-detonation-sandkasser URL-adresserne i meddelelsen på leveringstidspunktet.

## <a name="phase-4---post-delivery-protection"></a>Fase 4 – Beskyttelse efter levering

Det sidste trin finder sted efter levering af mail eller filer, hvor du handler på mail, som findes i forskellige postkasser, filer og links, der vises i klienter som Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Fase 4 af filtrering i Defender til Office 365 er beskyttelse efter levering.":::

1. **Pengeskab Links** er Defender Office 365 din time of click-beskyttelse. Hver webadresse i hver meddelelse ombrudt til at pege på Microsoft Pengeskab Links-servere. Når der klikkes på en URL-adresse, kontrolleres den ud fra det seneste ry, før brugeren omdirigeres til destinationswebstedet. URL-adressen er asynkront sandkasse for at opdatere dens omdømme.

2. **Automatisk tømning (ZAP) uden time for phishing** registrerer og neutraliserer med tilbagevirkende kraft skadelige phishingmeddelelser, der allerede er blevet leveret til Exchange Online postkasser.

3. **ZAP til malware** registrerer og neutraler ondsindede malwaremeddelelser, der allerede er blevet leveret til Exchange Online postkasser.

4. **ZAP til spam** registrerer og neutralerer skadelige spammeddelelser, der allerede er blevet leveret til Exchange Online-postkasser.

5. **Kampagnevisninger** giver administratorer mulighed for at få et overblik over et angreb, hurtigere og mere fuldstændigt, end et hvilket som helst team kan uden automatisering. Microsoft udnytter de enorme mængder antiphishing-, antispam- og antimalwaredata på tværs af hele tjenesten for at identificere kampagner og gør det derefter muligt for administratorer at undersøge dem fra start til slut, herunder mål, indvirkninger og flow, som også er tilgængelige i en opslaget kampagne, der kan downloades.

6. **Tilføjelsesprogrammet Rapportmeddelelse** giver brugerne mulighed for nemt at rapportere falske positive (gode mails, der fejlagtigt er markeret som *dårlige) eller* falske negativer (dårlig mail markeret som *god) til* Microsoft til yderligere analyse.

7. **Pengeskab Links til Office-klienter** tilbyder den samme beskyttelse med tid til klik Pengeskab Links indbygget i Office-klienter som Word, PowerPoint og Excel.

8. **Beskyttelse af OneDrive, SharePoint og Teams** giver den samme Pengeskab beskyttelse til vedhæftede filer mod skadelige filer indbygget i OneDrive, SharePoint og Microsoft Teams.

9. Når en URL-adresse, der peger på en fil, er  valgt efter levering, viser sammenkædet indholdsdeonation en advarselsside, indtil sandkassen af filen er fuldført, og URL-adressen findes som sikker.

## <a name="the-filtering-stack-diagram"></a>Filterstablingsdiagrammet

Det endelige diagram (som med alle dele af diagrammet, der skriver det) kan ændres uden problemer, efterhånden *som produktet vokser og udvikles*. Bogmærke denne side, og brug **feedbackindstillingen** , som du finder nederst, hvis du skal spørge efter opdateringer. For dine poster er dette stakken med alle faser i rækkefølge:

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="Alle faserne af filtrering i Defender for Office 365 i rækkefølge, 1 til 4.":::

## <a name="more-information"></a>Flere oplysninger

Har du brug for at konfigurere Microsoft Defender til Office 365 ***lige nu** _? Brug denne stak, _now* med [denne trinvise vejledning til at](protect-against-threats.md) begynde at beskytte din organisation.

*Særlige tak fra MSFTTracyP og docs-skriveteamet til Giulian Garruba for dette indhold*.
