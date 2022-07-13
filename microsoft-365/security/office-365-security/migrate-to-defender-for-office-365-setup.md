---
title: 'Overfør til Microsoft Defender for Office 365 fase 2: Installation'
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
description: Udfør trinnene for at begynde at overføre fra en beskyttelsestjeneste eller enhed fra tredjepart for at Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 899cf3894936ac154e61ef56204294d526aab33e
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772012"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Overfør til Microsoft Defender for Office 365 - fase 2: Konfiguration

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

<br>

|[![Fase 1: Forbered.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Fase 1: Forbered](migrate-to-defender-for-office-365-prepare.md)|![Fase 2: Konfigurer.](../../media/phase-diagrams/setup.png) <br> Fase 2: Konfigurer|[![Fase 3: Ombord.](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Fase 3: Onboard](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Du er her!*||

Velkommen til **fase 2: Konfiguration** af din **[migrering til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Denne overførselsfase omfatter følgende trin:

1. [Opret distributionsgrupper til pilotbrugere](#step-1-create-distribution-groups-for-pilot-users)
2. [Konfigurer brugerindsendelse til rapportering af brugermeddelelser](#step-2-configure-user-submission-for-user-message-reporting)
3. [Vedligehold eller opret reglen for SCL=-1-mailflow](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Konfigurer udvidet filtrering for forbindelser](#step-4-configure-enhanced-filtering-for-connectors)
5. [Opret pilotbeskyttelsespolitikker](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>Trin 1: Opret distributionsgrupper til pilotbrugere

Der kræves distributionsgrupper i Microsoft 365 til følgende aspekter af din migrering:

- **Undtagelser for reglen for SCL=-1-mailflow**: Pilotbrugere skal have fuld effekt af Defender for Office 365 beskyttelse, så du skal have, at deres indgående meddelelser scannes af Defender for Office 365. Det gør du ved at definere dine pilotbrugere i de relevante distributionsgrupper i Microsoft 365 og konfigurere disse grupper som undtagelser fra reglen for SCL=-1-mailflowet.

  Som vi beskrev i [Onboard Step 2: (Valgfrit) Undtaget pilotbrugere fra at filtrere efter din eksisterende beskyttelsestjeneste](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service), bør du overveje at fritage de samme pilotbrugere fra at scanne af din eksisterende beskyttelsestjeneste. Fjernelse af muligheden for filtrering af din eksisterende beskyttelsestjeneste og udelukkende at være afhængig af Defender for Office 365 er den bedste og tætteste repræsentation af, hvad der vil ske, når din migrering er fuldført.

- **Test af specifikke Defender for Office 365 beskyttelsesfunktioner**: Selv for pilotbrugerne ønsker du ikke at aktivere alt på én gang. Hvis du bruger en faseinddelt tilgang til de beskyttelsesfunktioner, der er i kraft for dine pilotbrugere, bliver fejlfinding og justering meget nemmere. Med denne fremgangsmåde i tankerne anbefaler vi følgende distributionsgrupper:
  - **En pilotgruppe for sikre vedhæftede filer**: F.eks. **MDOPilot\_SafeAttachments**
  - **En pilotgruppe af typen Safe Links**: F.eks. **MDOPilot\_SafeLinks**
  - **En pilotgruppe for standardindstillinger for politik for anti-spam og phishing**: F.eks. **MDOPilot\_SpamPhish\_Standard**
  - **En pilotgruppe for politikindstillinger for streng anti-spam og anti-phishing**: F.eks. **MDOPilot\_SpamPhish\_Strict**

Af hensyn til klarhed bruger vi disse specifikke gruppenavne i hele denne artikel, men du kan frit bruge din egen navngivningskonvention.

Når du er klar til at begynde at teste, skal du tilføje disse grupper som undtagelser til [reglen for SCL=-1-mailflowet](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Når du opretter politikker for de forskellige beskyttelsesfunktioner i Defender for Office 365, skal du bruge disse grupper som betingelser, der definerer, hvem politikken gælder for.

**Noter**:

- Udtrykkene Standard og Strict stammer fra vores [anbefalede sikkerhedsindstillinger](recommended-settings-for-eop-and-office365.md), som også bruges i [forudindstillede sikkerhedspolitikker](preset-security-policies.md). Ideelt set vil vi fortælle dig, at du skal definere dine pilotbrugere i Standard- og Strict-forudindstillede sikkerhedspolitikker, men det kan vi ikke gøre. Hvorfor? Da du ikke kan tilpasse indstillingerne i forudindstillede sikkerhedspolitikker (især handlinger, der udføres på meddelelser). Under din overførselstest skal du se, hvad Defender for Office 365 ville gøre med meddelelser, kontrollere, at det er det, du vil have, og eventuelt justere politikkonfigurationerne for at tillade eller forhindre disse resultater.

  Så i stedet for at bruge forudindstillede sikkerhedspolitikker skal du manuelt oprette brugerdefinerede politikker med indstillinger, der ligner hinanden meget, men i nogle tilfælde er anderledes end indstillingerne for Standard- og Strict-forudindstillede sikkerhedspolitikker.

- Hvis du vil eksperimentere med indstillinger, der **adskiller sig væsentligt** fra vores anbefalede Standard- eller Strict-værdier, bør du overveje at oprette og bruge yderligere og specifikke distributionsgrupper for pilotbrugerne i disse scenarier. Du kan bruge Konfigurationsanalyse til at se, hvor sikre dine indstillinger er. Du kan finde instruktioner [under Konfigurationsanalyse for beskyttelsespolitikker i EOP og Microsoft Defender for Office 365](configuration-analyzer-for-security-policies.md).

  For de fleste organisationer er den bedste tilgang at starte med politikker, der er tæt på vores anbefalede Standard-indstillinger. Efter så meget observation og feedback, som du kan gøre i din tilgængelige tidsramme, kan du gå videre til mere aggressive indstillinger senere. Repræsentationsbeskyttelse og levering til mappen Uønsket mail i forhold til levering til karantæne kan kræve tilpasning.

  Hvis du bruger brugerdefinerede politikker, skal du blot sørge for, at de anvendes _før_ de politikker, der indeholder vores anbefalede indstillinger for migreringen. Hvis en bruger identificeres i flere politikker af samme type (f.eks. anti-phishing), anvendes der kun én politik af denne type på brugeren (baseret på politikkens prioritetsværdi). Du kan få flere oplysninger under [Rækkefølgen og rækkefølgen af mailbeskyttelse](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>Trin 2: Konfigurer brugerindsendelse til rapportering af brugermeddelelser

Muligheden for, at brugerne kan identificere falske positiver eller falske negativer fra Defender for Office 365 er en vigtig del af migreringen.

Du kan angive en Exchange Online postkasse for at modtage meddelelser, som brugerne rapporterer som skadelige eller ikke skadelige. Du kan finde flere instruktioner under [Indstillinger for brugerrapporterede meddelelser](user-submission.md). Denne postkasse kan modtage kopier af meddelelser, som dine brugere har sendt til Microsoft, eller postkassen kan opfange meddelelser uden at rapportere dem til Microsoft (du er sikkerhedsteam kan manuelt analysere og sende meddelelserne). Denne aflytningstilgang tillader dog ikke tjenesten automatisk at indstille og lære.

Du skal også bekræfte, at alle brugere i pilotprojektet har installeret en understøttet meddelelsesrapporteringsapp i Outlook, der er kompatibel med indsendelse af brugere. Disse apps omfatter:

- [Tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md)
- [Tilføjelsesprogrammet Rapport phishing](enable-the-report-phish-add-in.md)
- Understøttede rapporteringsværktøjer fra tredjepart som beskrevet [her](user-submission.md#third-party-reporting-tools).

Undervurder ikke vigtigheden af dette trin. Data fra brugerindsendelser giver dig den feedbackløkke, du skal bruge for at bekræfte en god, ensartet slutbrugeroplevelse før og efter migreringen. Denne feedback hjælper dig med at træffe velunderbyggede beslutninger om politikkonfiguration samt levere databaserede rapporter til din administration om, at migreringen gik problemfrit.

I stedet for at stole på data, der understøttes af hele organisationens oplevelse, har mere end én migrering resulteret i følelsesmæssige spekulationer baseret på en enkelt negativ brugeroplevelse. Hvis du har kørt phishing-simuleringer, kan du desuden bruge feedback fra dine brugere til at informere dig, når de ser noget risikabelt, der kan kræve undersøgelse.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>Trin 3: Vedligehold eller opret reglen for SCL=-1-mailflow

Da din indgående mail distribueres via en anden beskyttelsestjeneste, der er placeret foran Microsoft 365, er det meget sandsynligt, at du allerede har en regel for mailflow (også kendt som en transportregel) i Exchange Online, der angiver niveauet for spamsikkerhed for alle indgående mails til værdien -1 (omgå filtrering af spam). De fleste beskyttelsestjenester fra tredjepart opfordrer til denne SCL=-1-mailflowregel for Microsoft 365-kunder, der vil bruge deres tjenester.

Hvis du bruger en anden mekanisme til at tilsidesætte Microsoft-filtreringsstakken (f.eks. en liste over tilladte IP-adresser), anbefaler vi, at du skifter til at bruge en regel for SCL=-1-mailflow, **så længe** alle indgående internetmails til Microsoft 365 kommer fra beskyttelsestjeneste fra tredjepart (ingen mailflows direkte fra internettet til Microsoft 365).

Reglen for SCL=-1-mailflow er vigtig under overførslen af følgende årsager:

- Du kan bruge [Threat Explorer](email-security-in-microsoft-defender.md) til at se, hvilke funktioner i Microsoft-stakken der *ville have* handlet på meddelelser, uden at det påvirkede resultaterne fra din eksisterende beskyttelsestjeneste.
- Du kan gradvist justere, hvem der er beskyttet af Microsoft 365-filtreringsstakken, ved at konfigurere undtagelser til reglen for SCL=-1-mailflowet. Undtagelserne er medlemmer af de pilotdistributionsgrupper, som vi anbefaler senere i denne artikel.

  Før eller under cutover af din MX-post til Microsoft 365 deaktiverer du denne regel for at aktivere fuld beskyttelse af Microsoft 365-beskyttelsesstakken for alle modtagere i din organisation.

Du kan få flere oplysninger under [Brug regler for mailflow til at angive niveauet for spamsikkerhed i meddelelser i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Noter**:

- Hvis du planlægger at tillade, at internetmails flyder gennem din eksisterende beskyttelsestjeneste **og** direkte ind i Microsoft 365 på samme tid, skal du begrænse reglen for SCL=-1-mailflow (mail, der tilsidesætter filtrering af spam) til mails, der kun har været i din eksisterende beskyttelsestjeneste. Du vil ikke have ufiltreret internetmaillanding i brugerpostkasser i Microsoft 365.

  Hvis du vil identificere mails, der allerede er blevet scannet af din eksisterende beskyttelsestjeneste, korrekt, kan du føje en betingelse til reglen for SCL=-1-mailflowet. Eksempel:

  - **Til skybaserede beskyttelsestjenester**: Du kan bruge en overskrifts- og overskriftsværdi, der er entydig for din organisation. Meddelelser med overskriften scannes ikke af Microsoft 365. Meddelelser uden overskriften scannes af Microsoft 365
  - **Til beskyttelsestjenester eller enheder i det lokale miljø**: Du kan bruge kildens IP-adresser. Meddelelser fra kildens IP-adresser scannes ikke af Microsoft 365. Meddelelser, der ikke kommer fra kildens IP-adresser, scannes af Microsoft 365.

- Brug ikke udelukkende MX-poster til at styre, om post filtreres. Afsendere kan nemt ignorere MX-posten og sende mail direkte til Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>Trin 4: Konfigurer udvidet filtrering for forbindelser

Det første, du skal gøre, er at konfigurere [Udvidet filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (også kendt som *oversigt over spring over*) på den connector, der bruges til mailflow, fra din eksisterende beskyttelsestjeneste til Microsoft 365. Du kan bruge [rapporten med indgående meddelelser](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) til at identificere connectoren.

Forbedret filtrering af forbindelser er påkrævet af Defender for Office 365 for at se, hvor internetmeddelelserne rent faktisk kom fra. Forbedret filtrering for forbindelser forbedrer i høj grad nøjagtigheden af Microsoft-filtreringsstakken (især [spoof intelligence](anti-spoofing-protection.md) samt funktioner efter brud i [Threat Explorer](threat-explorer.md) og [Automatiseret undersøgelse & Svar (AIR)](automated-investigation-response-office.md).

Hvis du vil aktivere udvidet filtrering for forbindelser korrekt, skal du tilføje de **offentlige** IP-adresser for \*\***alle\*\*** tredjepartstjenester og/eller lokale mailsystemværter, der dirigerer indgående mails til Microsoft 365.

Hvis du vil bekræfte, at udvidet filtrering for forbindelser fungerer, skal du kontrollere, at indgående meddelelser indeholder en eller begge af følgende headere:

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>Trin 5: Opret pilotbeskyttelsespolitikker

Ved at oprette produktionspolitikker, selvom de ikke anvendes på alle brugere, kan du teste funktioner efter sikkerhedsbrud som [Threat Explorer](threat-explorer.md) og teste integration Defender for Office 365 i dit sikkerhedssvarteams processer.

> [!IMPORTANT]
> Politikker kan være begrænset til brugere, grupper eller domæner. Vi anbefaler, at du ikke blander alle tre i én politik, da det kun er de brugere, der matcher alle tre, der falder inden for politikkens område. I forbindelse med pilotpolitikker anbefaler vi, at du bruger grupper eller brugere. I forbindelse med produktionspolitikker anbefaler vi, at du bruger domæner. Det er ekstremt vigtigt at forstå, at **det kun** er brugerens primære maildomæne, der bestemmer, om brugeren falder inden for politikkens område. Så hvis du skifter MX-posten for en brugers sekundære domæne, skal du sørge for, at brugerens primære domæne også er omfattet af en politik.

### <a name="create-pilot-safe-attachments-policies"></a>Opret pilotpolitikker for sikre vedhæftede filer

[Sikre vedhæftede filer](safe-attachments.md) er den nemmeste Defender for Office 365 funktion til at aktivere og teste, før du skifter din MX-post. Sikre vedhæftede filer har følgende fordele:

- Minimal konfiguration.
- Ekstremt lav chance for falske positiver.
- Lignende funktionsmåde som beskyttelse mod skadelig software, som altid er slået til og ikke påvirkes af reglen for SCL=-1-mailflow.

Opret en politik for vedhæftede filer, der er tillid til, for dine pilotbrugere.

Du kan se de anbefalede indstillinger under [Politikindstillinger for anbefalede vedhæftede filer, der er tillid til](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Bemærk, at Standard- og Strict-anbefalingerne er de samme. Hvis du vil oprette politikken, skal du se [Konfigurer politikker for vedhæftede filer, der er tillid til](set-up-safe-attachments-policies.md). Sørg for at bruge gruppen **MDOPilot\_SafeAttachments** som betingelse for politikken (hvem politikken gælder for).

> [!NOTE]
> Den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** giver beskyttelse mod vedhæftede filer til alle modtagere, der ikke er defineret i nogen politikker for vedhæftede filer, der er tillid til. Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

### <a name="create-pilot-safe-links-policies"></a>Opret pilotpolitikker for Sikre links

> [!NOTE]
> Vi understøtter ikke ombrydning eller omskrivning af allerede ombrudte eller omskrevne links. Hvis din aktuelle beskyttelsestjeneste allerede ombryder eller omskriver links i mails, skal du deaktivere denne funktion for dine pilotbrugere. En måde at sikre, at dette ikke sker på, er at udelade URL-domænet for den anden tjeneste i politikken Sikre links.

Opret en politik for sikre links til dine pilotbrugere. Chancerne for falske positiver i Safe Links er også ret lave, men du bør overveje at teste funktionen på et mindre antal pilotbrugere end Sikre vedhæftede filer. Da funktionen påvirker brugeroplevelsen, bør du overveje en plan for at uddanne brugerne.

Du kan se de anbefalede indstillinger under [Politikindstillinger for anbefalede sikre links](recommended-settings-for-eop-and-office365.md#safe-links-settings). Bemærk, at Standard- og Strict-anbefalingerne er de samme. Hvis du vil oprette politikken, skal du se [Konfigurer politikker for sikre links](set-up-safe-links-policies.md). Sørg for at bruge gruppen **MDOPilot\_SafeLinks** som betingelse for politikken (hvem politikken gælder for).

> [!NOTE]
> Den forudindstillede sikkerhedspolitik **for indbygget beskyttelse** giver beskyttelse af sikre links til alle modtagere, der ikke er defineret i nogen politikker for Sikre links. Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

### <a name="create-pilot-anti-spam-policies"></a>Opret pilotpolitikker mod spam

Opret to politikker til bekæmpelse af spam for pilotbrugere:

- En politik, der bruger Standardindstillinger. Brug gruppen **MDOPilot\_SpamPhish\_Standard** som betingelse for politikken (hvem politikken gælder for).
- En politik, der bruger indstillingerne Strict. Brug gruppen **MDOPilot\_SpamPhish\_Strict** som betingelse for politikken (hvem politikken gælder for). Denne politik skal have en højere prioritet (lavere tal) end politikken med Standardindstillinger.

Du kan se de anbefalede Standard- og [Strict-indstillinger under Anbefalede indstillinger for politik for anti-spam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). Hvis du vil oprette politikkerne, skal du se [Konfigurer politikker mod spam](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Opret pilotpolitikker mod phishing

Opret to politikker til bekæmpelse af phishing for pilotbrugere:

- En politik, der bruger Standardindstillinger med undtagelse af repræsentationsregistreringshandlinger som beskrevet nedenfor. Brug gruppen **MDOPilot\_SpamPhish\_Standard** som betingelse for politikken (hvem politikken gælder for).
- En politik, der bruger indstillingerne Strict med undtagelse af repræsentationsregistreringshandlinger som beskrevet nedenfor. Brug gruppen **MDOPilot\_SpamPhish\_Strict** som betingelse for politikken (hvem politikken gælder for). Denne politik skal have en højere prioritet (lavere tal) end politikken med Standardindstillinger.

For spoof-registreringer er den anbefalede Standard-handling **Flyt meddelelse til modtagernes mapper med uønsket mail**, og den anbefalede Strenge handling er **Sæt meddelelsen i karantæne**. Brug indsigten spoof intelligence til at overvåge resultaterne. Tilsidesættelser forklares i næste afsnit. Du kan få flere oplysninger under [Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md).

I forbindelse med repræsentationsregistreringer skal du ignorere de anbefalede Standard- og Strict-handlinger for pilotpolitikkerne. Brug i stedet værdien **Anvend ikke nogen handling** for følgende indstillinger:

- **Hvis meddelelsen registreres som en repræsenteret bruger**
- **Hvis meddelelsen registreres som repræsenteret domæne**
- **Hvis postkasseintelligens registrerer en repræsenteret bruger**

Brug repræsentationsindsigten til at overvåge resultaterne. Du kan få flere oplysninger under [Repræsentationsindsigt i Defender for Office 365](impersonation-insight.md).

Du skal indstille efterligningsbeskyttelse (justere tillader og blokke) og aktivere hver repræsentationsbeskyttelseshandling for at sætte meddelelserne i karantæne eller flytte dem til mappen Uønsket mail (baseret på Standard- eller Strict-anbefalingerne). Du kan observere resultaterne og justere deres indstillinger efter behov.

Du kan få flere oplysninger i følgende emner:

- [Beskyttelse mod forfalskning](anti-spoofing-protection.md)
- [Repræsentationsindstillinger i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har fuldført **installationsfasen** for [din migrering for at Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Fortsæt til [fase 3: Ombord](migrate-to-defender-for-office-365-onboard.md).
