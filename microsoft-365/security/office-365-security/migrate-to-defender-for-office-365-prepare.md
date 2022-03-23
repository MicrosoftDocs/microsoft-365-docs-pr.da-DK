---
title: 'Overfør til Microsoft Defender for Office 365 fase 1: Forbered'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Nødvendige trin til at overføre fra en tredjepartsbeskyttelsestjeneste eller -enhed til Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f8a35fa7e8ac469a87861d25f45e7078eb4be940
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63594071"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-1-prepare"></a>Overfør til Microsoft Defender for Office 365 – Fase 1: Forbered

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)

<br>

|![Fase 1: Forbered.](../../media/phase-diagrams/prepare.png) <br> Fase 1: Forbered|[![Fase 2: Konfigurer](../../media/phase-diagrams/setup.png)](migrate-to-defender-for-office-365-setup.md) <br> [Fase 2: Konfigurer](migrate-to-defender-for-office-365-setup.md)|[![Fase 3: Onboard](../../media/phase-diagrams/onboard.png)](migrate-to-defender-for-office-365-onboard.md) <br> [Fase 3: Onboard](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
|*Du er her!*|||

Velkommen til **Fase 1: Forbered** din **[overførsel til Microsoft Defender for at Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Denne overførselsfase omfatter følgende trin. Du bør lagerliste indstillingerne på din eksisterende beskyttelsestjeneste først, før du foretager ændringer. Ellers kan du udføre de resterende trin i en hvilken som helst rækkefølge:

1. [Opliste indstillingerne på din eksisterende beskyttelsestjeneste](#inventory-the-settings-at-your-existing-protection-service)
2. [Kontrollér din eksisterende beskyttelseskonfiguration i Microsoft 365](#check-your-existing-protection-configuration-in-microsoft-365)
3. [Kontrollér din mailroutingkonfiguration](#check-your-mail-routing-configuration)
4. [Flyt funktioner, der redigerer meddelelser, Microsoft 365](#move-features-that-modify-messages-into-microsoft-365)
5. [Definere spam og massebrugeroplevelser](#define-spam-and-bulk-user-experiences)
6. [Identificer og angiv prioritetskonti](#identify-and-designate-priority-accounts)

## <a name="inventory-the-settings-at-your-existing-protection-service"></a>Opliste indstillingerne på din eksisterende beskyttelsestjeneste

En komplet oversigt over indstillinger, regler, undtagelser osv. fra din eksisterende beskyttelsestjeneste er en god ide, fordi du sandsynligvis ikke vil have adgang til oplysningerne, når du annullerer dit abonnement.

**Det er dog meget vigtigt, at du ikke automatisk eller vilkårligt genskaber alle dine eksisterende tilpasninger i Defender til Office 365.** Du kan i bedste fald introducere indstillinger, der ikke længere er nødvendige, relevante eller funktionelle. Så værst kan nogle af dine tidligere tilpasninger faktisk skabe sikkerhedsproblemer i Defender Office 365.

Din test og observation af de oprindelige funktioner og funktionsmåden for Defender til Office 365 i sidste ende afgøre tilsidesættelser og indstillinger, du har brug for. Det kan være nyttigt at kategorisere indstillingerne fra din eksisterende beskyttelsestjeneste i følgende kategorier:

- **Filtrering af forbindelse eller indhold**: Du vil sandsynligvis opdage, at du ikke har brug for de fleste af disse tilpasninger i Defender til Office 365.
- **Virksomhedsrouting**: Størstedelen af de tilpasninger, du skal gendanne, falder sandsynligvis til denne kategori. Du kan f.eks. genskabe disse indstillinger i Microsoft 365 som Exchange regler for mailflow (også kaldet transportregler), forbindelser og undtagelser til efterlignet intelligens.

I stedet for blindt at flytte gamle indstillinger ind i Microsoft 365 anbefaler vi en vandfaldstilgang, der involverer en pilotfase med stadig større brugermedlemskab og observationsbaseret justering baseret på justering af sikkerhedsmæssige overvejelser i forhold til virksomhedens behov.

## <a name="check-your-existing-protection-configuration-in-microsoft-365"></a>Kontrollér din eksisterende beskyttelseskonfiguration i Microsoft 365

Som vi har nævnt tidligere, er det umuligt helt at deaktivere alle beskyttelsesfunktioner til mails, der leveres i Microsoft 365, selv når du bruger en tredjepartsbeskyttelsestjeneste. Så det er ikke usædvanligt, at en Microsoft 365 har konfigureret mindst nogle mailbeskyttelsesfunktioner. Eksempel:

- Tidligere brugte du ikke tredjepartsbeskyttelsestjenesten med Microsoft 365. Du kan have brugt og konfigureret nogle beskyttelsesfunktioner i Microsoft 365 der i øjeblikket ignoreres. Men disse indstillinger træder muligvis i kraft, når du "drejer skiven" for at aktivere beskyttelsesfunktioner i Microsoft 365.
- Der kan være logi i Microsoft 365 beskyttelse for falske positive (gode mails markeret som dårlige) eller falske negativer (dårlig mail tilladt), som er foretaget via din eksisterende beskyttelsestjeneste.

Gennemse dine eksisterende beskyttelsesfunktioner i Microsoft 365 og overvej at fjerne eller forenkle indstillinger, der ikke længere er nødvendige. En regel eller en politikindstilling, der blev krævet for flere år siden, kunne sætte organisationen i fare og skabe utilsigtede huller i beskyttelsen.

## <a name="check-your-mail-routing-configuration"></a>Kontrollér din mailroutingkonfiguration

- Hvis du bruger nogen form for kompleks routing (f.eks. [Centraliseret mail transport](/exchange/transport-options)), bør du overveje at forenkle din routing og grundigt dokumentere den. Eksterne hop, især når Microsoft 365 allerede har modtaget meddelelsen, kan komplicere konfiguration og fejlfinding.

- Udgående og videresendelse af mail er uden for omfanget i denne artikel. Du skal dog være opmærksom på, at det kan være nødvendigt at udføre en eller flere af følgende trin:
  - Kontrollér, at alle de domæner, du bruger til at sende mail, har de rigtige SPF-poster. Få mere at vide under [Konfigurer SPF for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  - Vi anbefaler på det kraftigste, at du konfigurerer DKIM-Microsoft 365. Få mere at vide under [Brug DKIM til at validere udgående mail](use-dkim-to-validate-outbound-email.md).
  - Hvis du ikke distribuerer mails direkte fra Microsoft 365, skal du ændre denne routing ved at fjerne eller ændre den udgående forbindelse.

- Det Microsoft 365 at videresende mails fra dine lokale mailservere som et komplekst projekt i sig selv. Et simpelt eksempel er et lille antal apps eller enheder, som sender de fleste af deres meddelelser til interne modtagere og ikke bruges til masseforsendelser. Se [denne vejledning for at](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365) få mere at vide. Mere omfattende miljøer skal være mere veltænkte. Marketingmails og meddelelser, der kan ses som spam af modtagere, er ikke tilladt.

- Defender til Office 365 ikke har en funktion til sammenlægning af DMARC-rapporter. Besøg [Kataloget Microsoft Intelligent Security Association (MISA)](https://www.microsoft.com/misapartnercatalog) for at få vist tredjepartsleverandører, der tilbyder DMARC-rapportering til Microsoft 365.

## <a name="move-features-that-modify-messages-into-microsoft-365"></a>Flyt funktioner, der redigerer meddelelser, Microsoft 365

Du skal overføre eventuelle tilpasninger eller funktioner, der ændrer meddelelser på nogen måde, til Microsoft 365. Din eksisterende beskyttelsestjeneste tilføjer f.eks. **et eksternt** mærke til emnet eller meddelelsens brødtekst i meddelelser fra eksterne afsendere. Enhver sammenkædningsfunktion vil også medføre problemer med visse meddelelser. Hvis du bruger sådan en funktion i dag, bør du prioritere udrulningen af Pengeskab Links som et alternativ til at minimere problemer.

Hvis du ikke deaktiverer funktionerne til redigering af meddelelser i din eksisterende beskyttelsestjeneste, kan du forvente følgende negative resultater Microsoft 365:

- DKIM brydes. Ikke alle afsendere er afhængige af DKIM, men dem, der ikke kan godkende.
- [Efterlignet intelligens](anti-spoofing-protection.md) og justeringstrinnet senere i denne vejledning fungerer ikke korrekt.
- Du vil sandsynligvis få et stort antal falske positive (gode mails markeret som dårlige).

Hvis du vil genskabe ekstern Microsoft 365 i en Microsoft 365, har du følgende indstillinger:

- Den [Outlook funktion til at ringe op til eksterne afsendere](https://techcommunity.microsoft.com/t5/exchange-team-blog/native-external-sender-callouts-on-email-in-outlook/ba-p/2250098) sammen med [de første sikkerhedstip til kontakter](set-up-anti-phishing-policies.md#first-contact-safety-tip).
- Regler for mailflow (også kaldet transportregler). Du kan finde flere oplysninger [under Ansvarsfraskrivelser, signaturer,](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers) sidefødder eller sidehoveder for hele organisationen i Exchange Online.

Microsoft arbejder sammen med branchen for at understøtte den godkendte modtagne kæde (ARC) i den nærmeste fremtid. Hvis du vil lade meddelelsesændringer være aktiveret hos din aktuelle mailgatewayudbyder, anbefaler vi, at du kontakter dem om deres planer for at understøtte denne standard.

## <a name="account-for-any-active-phishing-simulations"></a>Tage højde for alle aktive phishing-simuleringer

Hvis du har aktive phishingsimeringer fra tredjeparter, skal du forhindre, at meddelelser, links og vedhæftede filer bliver identificeret som phishing af Defender Office 365. Få mere at vide under [Konfigurer phishing-simuleringer fra tredjeparter i politikken for avanceret levering](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).

## <a name="define-spam-and-bulk-user-experiences"></a>Definere spam og massebrugeroplevelser

- **Karantæne vs. levering til mappen Uønsket** mail: Det naturlige og anbefalede svar på skadelige og absolut risikabelt svar er at sætte meddelelser i karantæne. Men hvordan skal brugerne håndtere mindre skadelige meddelelser, f.eks. spam og massemails (også kaldet *grå mail*). Skal disse typer meddelelser leveres til brugernes mapper med uønsket mail?

  Med vores Standardsikkerhedsindstillinger leverer vi generelt disse mindre risikabelt typer af meddelelser til mappen Uønsket mail. Denne funktionsmåde svarer til mange forbrugermailtilbud, hvor brugerne kan tjekke mappen uønsket mail for manglende meddelelser, og de kan hjælpe selve disse meddelelser. Eller hvis brugeren bevidst har tilmeldt sig et nyhedsbrev eller en marketingmail, kan vedkommende vælge at opsige abonnementet eller blokere afsenderen for sin egen postkasse.

  Mange virksomhedsbrugere er dog vant til kun at bruge små (hvis nogen) mails i mappen Uønsket mail. I stedet bruges disse virksomhedsbrugere til at sætte deres manglende meddelelser i karantæne. Karantæne medfører problemer med meddelelser i karantæne, beskedfrekvens og de tilladelser, der kræves for at få vist og frigive meddelelser.

  - Domænenøgler identificeret mail (DKIM) brydes.
  - [Efterlignet intelligens](anti-spoofing-protection.md) fungerer ikke korrekt.
  - Du vil sandsynligvis få et stort antal falske positive (gode mails markeret som dårlige).

  I sidste ende er det din beslutning, hvis du vil forhindre levering af mail til mappen Uønsket mail i stedet for levering til karantæne. Men der er én ting, der er sikker: Hvis oplevelsen i Defender til Office 365 er anderledes end den, dine brugere er vant til, skal du give dem besked og give grundlæggende kurser. Inkorkorer læring fra piloten, og sørg for, at brugerne er forberedt til enhver ny adfærd til levering af mail.

- **Ønsket massemail vs. uønsket massemail**: Mange beskyttelsessystemer giver brugerne mulighed for at tillade eller blokere massemails til sig selv. Disse indstillinger kan ikke let overføres til Microsoft 365, så du bør overveje at arbejde med VIP'er og deres medarbejdere for at genskabe deres eksisterende konfigurationer Microsoft 365.

  I dag Microsoft 365 nogle masseforsendelser (f.eks. nyhedsbreve) som sikre baseret på meddelelseskilden. Mail fra disse "sikre" kilder markeres i øjeblikket ikke som masseforsendelser (masseklageniveauet eller BCL er 0 eller 1), så det er svært globalt at blokere mail fra disse kilder. For de fleste brugere er løsningen at bede dem om at opsige abonnementet på disse massemeddelelser enkeltvis eller Outlook at blokere afsenderen. Men nogle brugere kan ikke lide at blokere eller fjerne abonnementet på selve massemeddelelser.

  Regler for mailflow, der filtrerer massemails, kan være nyttige, når VIP-brugere ikke ønsker at administrere dette selv. Få mere at vide under [Brug regler for mailflow til at filtrere massemail](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-filter-bulk-mail).

## <a name="identify-and-designate-priority-accounts"></a>Identificer og angiv prioritetskonti

Hvis funktionen er tilgængelig for **dig, kan** prioritetskonti  og brugermærker hjælpe dig med at identificere dine vigtige Microsoft 365 så de skiller sig ud i rapporter. Få mere at vide under [Brugermærker i Microsoft Defender til Office 365](user-tags.md) Administrer [og overvåg prioritetskonti](/microsoft-365/admin/setup/priority-accounts).

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har fuldført **klargøringsfasen** af [din overførsel til Microsoft Defender Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Fortsæt til [Fase 2: Konfiguration](migrate-to-defender-for-office-365-setup.md).
