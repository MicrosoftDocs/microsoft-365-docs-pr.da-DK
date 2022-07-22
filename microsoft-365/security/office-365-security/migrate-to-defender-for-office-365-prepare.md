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
- m365solution-mdo-migration
ms.custom: migrationguides
description: Forudsætningstrin for overførsel fra en beskyttelsestjeneste eller enhed fra tredjepart til Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7134d1e306de99b3af70a934ec9e9880ea98d268
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969830"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-1-prepare"></a>Migrer til Microsoft Defender for Office 365 - fase 1: Forbered

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

<br>

|![Fase 1: Forbered.](../../media/phase-diagrams/prepare.png) <br> Fase 1: Forbered|[![Fase 2: Konfigurer](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Fase 2: Konfigurer](migrate-to-defender-for-office-365-setup.md)|[![Fase 3: Onboard](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Fase 3: Onboard](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
|*Du er her!*|||

Velkommen til **fase 1: Forbered** **[din migrering til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Denne overførselsfase omfatter følgende trin. Du skal først oprette en oversigt over indstillingerne på din eksisterende beskyttelsestjeneste, før du foretager ændringer. Ellers kan du udføre de resterende trin i en vilkårlig rækkefølge:

1. [Oversigt over indstillingerne på din eksisterende beskyttelsestjeneste](#inventory-the-settings-at-your-existing-protection-service)
2. [Kontrollér din eksisterende beskyttelsekonfiguration i Microsoft 365](#check-your-existing-protection-configuration-in-microsoft-365)
3. [Kontrollér konfigurationen af postdistributionen](#check-your-mail-routing-configuration)
4. [Flyt funktioner, der ændrer meddelelser, til Microsoft 365](#move-features-that-modify-messages-into-microsoft-365)
5. [Definer spam og massebrugeroplevelser](#define-spam-and-bulk-user-experiences)
6. [Identificer og angiv prioritetskonti](#identify-and-designate-priority-accounts)

## <a name="inventory-the-settings-at-your-existing-protection-service"></a>Oversigt over indstillingerne på din eksisterende beskyttelsestjeneste

En komplet oversigt over indstillinger, regler, undtagelser osv. fra din eksisterende beskyttelsestjeneste er en god idé, da du sandsynligvis ikke har adgang til oplysningerne, når du har annulleret dit abonnement.

**Men det er meget vigtigt, at du ikke automatisk eller tilfældigt genskaber alle dine eksisterende tilpasninger i Defender for Office 365.** I bedste fald kan du introducere indstillinger, der ikke længere er påkrævede, relevante eller funktionelle. Værre kan det være, at nogle af dine tidligere tilpasninger rent faktisk kan medføre sikkerhedsproblemer i Defender for Office 365.

Din test og observation af de oprindelige egenskaber og funktionsmåden for Defender for Office 365 bestemmer i sidste ende de tilsidesættelser og indstillinger, du har brug for. Du kan finde det nyttigt at kategorisere indstillingerne fra din eksisterende beskyttelsestjeneste i følgende kategorier:

- **Forbindelses- eller indholdsfiltrering**: Du vil sandsynligvis opdage, at du ikke har brug for de fleste af disse tilpasninger i Defender for Office 365.
- **Forretningsrouting**: De fleste af de tilpasninger, du skal oprette igen, falder sandsynligvis inden for denne kategori. Du kan f.eks. genoprette disse indstillinger i Microsoft 365 som Exchange-regler for mailflow (også kendt som transportregler), forbindelser og undtagelser for spoof intelligence.

I stedet for at flytte gamle indstillinger blindt ind i Microsoft 365 anbefaler vi en vandfaldstilgang, der involverer en pilotfase med stadig stigende brugermedlemskab og observationbaseret justering baseret på balancering af sikkerhedsovervejelser med organisationens forretningsmæssige behov.

## <a name="check-your-existing-protection-configuration-in-microsoft-365"></a>Kontrollér din eksisterende beskyttelsekonfiguration i Microsoft 365

Som vi sagde tidligere, er det umuligt helt at deaktivere alle beskyttelsesfunktioner for mails, der leveres til Microsoft 365, selv når du bruger en beskyttelsestjeneste fra tredjepart. Det er derfor ikke usædvanligt, at en Microsoft 365-organisation i det mindste har konfigureret nogle funktioner til mailbeskyttelse. Eksempel:

- Tidligere brugte du ikke beskyttelsestjeneste fra tredjepart med Microsoft 365. Du har muligvis brugt og konfigureret nogle beskyttelsesfunktioner i Microsoft 365, der ignoreres i øjeblikket. Men disse indstillinger kan træde i kraft, når du "drejer opkaldet" for at aktivere beskyttelsesfunktionerne i Microsoft 365.
- Du kan have tilpasninger i Microsoft 365-beskyttelse til falske positiver (god post markeret som dårlig) eller falske negativer (dårlig post er tilladt), der er foretaget gennem din eksisterende beskyttelsestjeneste.

Gennemse dine eksisterende beskyttelsesfunktioner i Microsoft 365, og overvej at fjerne eller forenkle indstillinger, der ikke længere er påkrævet. En regel eller politikindstilling, der var påkrævet for år siden, kan bringe organisationen i fare og skabe utilsigtede huller i beskyttelsen.

## <a name="check-your-mail-routing-configuration"></a>Kontrollér konfigurationen af postdistributionen

- Hvis du bruger en hvilken som helst form for kompleks routing (f.eks [. Centraliseret posttransport](/exchange/transport-options)), bør du overveje at forenkle distributionen og dokumentere den grundigt. Eksterne hop, især når Microsoft 365 allerede har modtaget meddelelsen, kan komplicere konfigurationen og fejlfindingen.

- Udgående og videresendende mail-flow er uden for denne artikels område. Du skal dog være opmærksom på, at du muligvis skal gøre et eller flere af følgende trin:
  - Bekræft, at alle de domæner, du bruger til at sende mail, har de korrekte SPF-poster. Du kan finde flere oplysninger under [Konfigurer SPF for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  - Vi anbefaler på det kraftigste, at du konfigurerer DKIM-logon til Microsoft 365. Du kan få flere oplysninger under [Brug DKIM til at validere udgående mail](use-dkim-to-validate-outbound-email.md).
  - Hvis du ikke distribuerer mails direkte fra Microsoft 365, skal du ændre denne distribution ved at fjerne eller ændre den udgående connector.

- Brug af Microsoft 365 til at videresende mail fra dine lokale mailservere kan være et komplekst projekt i sig selv. Et simpelt eksempel er et lille antal apps eller enheder, der sender de fleste af deres meddelelser til interne modtagere og ikke bruges til masseforsendelser. Du kan finde flere oplysninger [i denne vejledning](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365) . Mere omfattende miljøer skal være mere betænksomme. Marketingmails og meddelelser, der kan ses som spam af modtagere, er ikke tilladt.

- Defender for Office 365 har ikke en funktion til sammenlægning af DMARC-rapporter. Besøg [Kataloget for Microsoft Intelligent Security Association (MISA)](https://www.microsoft.com/misapartnercatalog) for at få vist tredjepartsleverandører, der tilbyder DMARC-rapportering til Microsoft 365.

## <a name="move-features-that-modify-messages-into-microsoft-365"></a>Flyt funktioner, der ændrer meddelelser, til Microsoft 365

Du skal overføre alle tilpasninger eller funktioner, der ændrer meddelelser på nogen måde, til Microsoft 365. Din eksisterende beskyttelsestjeneste føjer f.eks. et **eksternt** mærke til emnet eller meddelelsesteksten i meddelelser fra eksterne afsendere. Enhver funktion til ombrydning af links vil også medføre problemer med nogle meddelelser. Hvis du bruger en sådan funktion i dag, skal du prioritere udrulningen af Sikre links som et alternativ til at minimere problemer.

Hvis du ikke slår funktioner til ændring af meddelelser fra i din eksisterende beskyttelsestjeneste, kan du forvente følgende negative resultater i Microsoft 365:

- DKIM går i stykker. Det er ikke alle afsendere, der er afhængige af DKIM, men dem, der ikke kan godkende.
- [Spoof intelligence](anti-spoofing-protection.md) og justeringstrinnet senere i denne vejledning fungerer ikke korrekt.
- Du får sandsynligvis et højt antal falske positiver (god post markeret som dårlig).

Hvis du vil genoprette id'et for den eksterne afsender i Microsoft 365, har du følgende muligheder:

- Funktionen [til opkald til eksterne afsendere i Outlook](https://techcommunity.microsoft.com/t5/exchange-team-blog/native-external-sender-callouts-on-email-in-outlook/ba-p/2250098) sammen med [tip til første kontaktsikkerhed](set-up-anti-phishing-policies.md#first-contact-safety-tip).
- Regler for mailflow (også kaldet transportregler). Du kan få flere oplysninger under [Ansvarsfraskrivelser, signaturer, sidefødder eller sidehoveder i Exchange Online for hele organisationen](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

Microsoft arbejder sammen med branchen om at understøtte ARC-standarden (Godkendt modtaget kæde) i den nærmeste fremtid. Hvis du vil lade funktioner til ændring af meddelelser være aktiveret hos din aktuelle mailgatewayudbyder, anbefaler vi, at du kontakter dem om deres planer for at understøtte denne standard.

## <a name="account-for-any-active-phishing-simulations"></a>Konto for alle aktive phishing-simuleringer

Hvis du har aktive phishing-simuleringer fra tredjepart, skal du forhindre, at meddelelser, links og vedhæftede filer identificeres som phishing af Defender for Office 365. Du kan få flere oplysninger under [Konfigurer phishing-simuleringer fra tredjepart i den avancerede leveringspolitik](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).

## <a name="define-spam-and-bulk-user-experiences"></a>Definer spam og massebrugeroplevelser

- **Karantæne vs. levering til mappen Uønsket mail**: Det naturlige og anbefalede svar på skadelige og helt sikkert risikable meddelelser er at sætte meddelelserne i karantæne. Men hvordan vil du have, at brugerne skal håndtere mindre skadelige meddelelser, f.eks. spam og massemails (også kendt som *grå mail*). Skal disse typer meddelelser leveres til brugerens mapper med uønsket mail?

  Med vores standardsikkerhedsindstillinger leverer vi generelt disse mindre risikable typer meddelelser til mappen Uønsket mail. Denne funktionsmåde svarer til mange forbrugermailtilbud, hvor brugerne kan kontrollere deres mappe med uønsket mail for manglende meddelelser, og de kan selv redde disse meddelelser. Eller hvis brugeren bevidst har tilmeldt sig et nyhedsbrev eller en marketingmail, kan vedkommende vælge at opsige abonnementet eller blokere afsenderen for sin egen postkasse.

  Mange virksomhedsbrugere er dog vant til kun at få (hvis nogen) mails i deres mappe med uønsket mail. I stedet bruges disse virksomhedsbrugere til at kontrollere en karantæne for deres manglende meddelelser. Karantæne introducerer problemer med karantænemeddelelser, meddelelseshyppighed og de tilladelser, der kræves for at få vist og frigive meddelelser.

  - Mail med identificerede domænenavne (DKIM) afbrydes.
  - [Spoof intelligence](anti-spoofing-protection.md) fungerer ikke korrekt.
  - Du får sandsynligvis et højt antal falske positiver (god post markeret som dårlig).

  I sidste ende er det din beslutning, hvis du vil forhindre levering af mail til mappen Uønsket mail til fordel for levering til karantæne. Men én ting er sikker: Hvis oplevelsen i Defender for Office 365 er anderledes end det, dine brugere er vant til, skal du give dem besked og give dem grundlæggende træning. Inkorporer erfaringer fra piloten, og sørg for, at brugerne er forberedt på enhver ny funktionsmåde for levering af mail.

- **Ønskede massemails i forhold til uønskede massemails**: Mange beskyttelsessystemer giver brugerne mulighed for selv at tillade eller blokere massemails. Disse indstillinger migrerer ikke let til Microsoft 365, så du bør overveje at arbejde med VIP'er og deres medarbejdere for at genskabe deres eksisterende konfigurationer i Microsoft 365.

  I dag betragter Microsoft 365 massemails (f.eks. nyhedsbreve) som sikre baseret på meddelelseskilden. Mail fra disse "sikre" kilder er i øjeblikket ikke markeret som bulk (masseklageniveauet eller BCL er 0 eller 1), så det er svært at blokere mail fra disse kilder globalt. For de fleste brugere er løsningen at bede dem om individuelt at opsige abonnementet på disse massemeddelelser eller bruge Outlook til at blokere afsenderen. Men nogle brugere vil ikke selv kunne lide at blokere eller ophæve abonnementet på massemeddelelser.

  Regler for mailflow, der filtrerer massemails, kan være nyttige, når VIP-brugere ikke ønsker at administrere dette selv. Du kan få flere oplysninger under [Brug regler for mailflow til at filtrere massemail](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-filter-bulk-mail).

## <a name="identify-and-designate-priority-accounts"></a>Identificer og angiv prioritetskonti

Hvis funktionen er tilgængelig for dig, kan **prioritetskonti** og **brugerkoder** hjælpe med at identificere dine vigtige Microsoft 365-brugere, så de skiller sig ud i rapporter. Du kan få flere oplysninger [under Brugerkoder i Microsoft Defender for Office 365](user-tags.md) og [Administrer og overvåg prioritetskonti](/microsoft-365/admin/setup/priority-accounts).

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har fuldført **forberedelsesfasen** for [din migrering til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Fortsæt til [fase 2: Installation](migrate-to-defender-for-office-365-setup.md).
