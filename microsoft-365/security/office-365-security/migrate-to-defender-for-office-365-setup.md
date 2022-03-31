---
title: 'Overfør til Microsoft Defender Office 365 Fase 2: Konfiguration'
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
description: Tag disse trin for at begynde overførslen fra en tredjepartsbeskyttelsestjeneste eller -enhed til Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cc16da76f4b863800bb4f1e7573bbe2fa106b4cf
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63601024"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Overfør til Microsoft Defender for Office 365 – Fase 2: Konfiguration

**Gælder for:**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)

<br>

|[![Fase 1: Forbered.](../../media/phase-diagrams/prepare.png)](migrate-to-defender-for-office-365-prepare.md) <br> [Fase 1: Forbered](migrate-to-defender-for-office-365-prepare.md)|![Fase 2: Konfigurer.](../../media/phase-diagrams/setup.png) <br> Fase 2: Konfigurer|[![Fase 3: Onboard.](../../media/phase-diagrams/onboard.png)](migrate-to-defender-for-office-365-onboard.md) <br> [Fase 3: Onboard](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Du er her!*||

Velkommen til **Fase 2: Konfiguration** af din **[overførsel til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Denne overførselsfase omfatter følgende trin:

1. [Opret distributionsgrupper for pilotbrugere](#step-1-create-distribution-groups-for-pilot-users)
2. [Konfigurere brugerindsendelse til rapportering af brugermeddelelse](#step-2-configure-user-submission-for-user-message-reporting)
3. [Vedligeholde eller oprette reglen for mailflow i SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Konfigurere udvidet filtrering for forbindelser](#step-4-configure-enhanced-filtering-for-connectors)
5. [Opret pilotbeskyttelsespolitikker](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>Trin 1: Opret distributionsgrupper for pilotbrugere

Distributionsgrupper er påkrævet Microsoft 365 af følgende aspekter af din overførsel:

- **Undtagelser for reglen SCL=-1-mailflow**: Du vil have pilotbrugere til at få den fulde effekt af Defender for Office 365-beskyttelse, så du skal scanne deres indgående meddelelser af Defender for Office 365. Det gør du ved at definere dine pilotbrugere i de relevante distributionsgrupper i Microsoft 365 og konfigurere disse grupper som undtagelser til SCL=-1-mailflowreglen.

  Som vi har beskrevet i [Onboard Step 2: (Valgfrit) Undtaget pilotbrugere](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service) fra filtrering af din eksisterende beskyttelsestjeneste, bør du overveje at undtage disse samme pilotbrugere fra scanning af din eksisterende beskyttelsestjeneste. At udelukke muligheden for filtrering af din eksisterende beskyttelsestjeneste og udelukkende at være afhængig af Defender til Office 365 er den bedste og nærmeste repræsentation af, hvad der vil ske, når overførslen er fuldført.

- **Test af specifikke Defender for Office 365 beskyttelsesfunktioner**: Selv for pilotbrugerne ønsker du ikke at slå alt til på én gang. Hvis du bruger en fasebaseret tilgang til de beskyttelsesfunktioner, der er gældende for dine pilotbrugere, bliver fejlfinding og justering meget nemmere. Med denne fremgangsmåde i tankerne anbefaler vi følgende distributionsgrupper:
  - **En Pengeskab gruppen Vedhæftede filer**: F.eks **. MDOPilotSafeAttachments\_**
  - **En Pengeskab Links-pilotgruppe**: F.eks **. MDOPilotSafeLinks\_**
  - **En pilotgruppe til politikindstillinger for Standardpolitik for uønsket post og phishing**: F.eks **. MDOPilotSpamPhishStandard\_\_**
  - **En pilotgruppe til politikindstillinger for restriktiv politik for uønsket post og phishing**: F.eks **. MDOPilotSpamPhishStrict\_\_**

For at gøre det klart bruger vi disse specifikke gruppenavne i denne artikel, men du kan frit bruge din egen navngivningskonvention.

Når du er klar til at begynde at teste, skal du tilføje disse grupper som undtagelser [til reglen for mailflow i SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Når du opretter politikker for de forskellige beskyttelsesfunktioner i Defender for Office 365, skal du bruge disse grupper som betingelser, der definerer, hvem politikken gælder for.

**Bemærkninger**:

- Begreberne Standard og Streng kommer fra vores [anbefalede sikkerhedsindstillinger](recommended-settings-for-eop-and-office365.md), som også bruges i [forudindstillede sikkerhedspolitikker](preset-security-policies.md). Ideelt set ville vi bede dig definere dine pilotbrugere i standard- og restriktive sikkerhedspolitikker, men det kan vi ikke. Hvorfor? Fordi du ikke kan tilpasse indstillingerne i foruddefinerede sikkerhedspolitikker (især handlinger, der foretages på meddelelser, eller justering af indstillinger for repræsentationsbeskyttelse). Under din overførselstest er du nødt til at se, hvad Defender til Office 365 ville gøre ved meddelelser, bekræfte, at det er det, du ønsker at ske, og muligvis justere politikkonfigurationerne for at tillade eller forhindre disse resultater.

  Så i stedet for at bruge forudindstillede sikkerhedspolitikker, skal du manuelt oprette brugerdefinerede politikker med indstillinger, der ligner meget, men i nogle tilfælde er anderledes end indstillingerne for Standard og Strenge forudindstillede sikkerhedspolitikker.

- Hvis du vil eksperimentere med indstillinger, der  er væsentligt anderledes end vores Standard- eller Streng anbefalede værdier, bør du overveje at oprette og bruge flere og bestemte distributionsgrupper til pilotbrugerne i disse scenarier. Du kan bruge Configuration Analyzer til at se, hvor sikre dine indstillinger er. Du kan finde en vejledning [i Konfigurationsanalyse til beskyttelsespolitikker i EOP og Microsoft Defender Office 365](configuration-analyzer-for-security-policies.md).

  For de fleste organisationer er den bedste fremgangsmåde at starte med politikker, der er tæt forbundet med vores anbefalede standardindstillinger. Efter så meget observation og feedback, som du kan gøre i din tilgængelige tidsramme, kan du senere gå videre til mere aggressive indstillinger. Beskyttelse mod efterligning og levering til mappen Uønsket mail vs. levering til karantæne kan kræve tilpasning.

  Hvis du bruger brugerdefinerede politikker, skal du blot sørge for, at de  anvendes før de politikker, der indeholder vores anbefalede indstillinger for overførslen. Hvis en bruger identificeres i flere politikker af samme type (f.eks. antiphishing), anvendes der kun én politik af den pågældende type på brugeren (baseret på politikkens prioritetsværdi). Du kan finde flere oplysninger [i Rækkefølgen og prioriteten af mailbeskyttelse](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>Trin 2: Konfigurere brugerindsendelse for rapportering af brugermeddelelse

Brugernes mulighed for at identificere falske positive eller falske negativer fra Defender for Office 365 er en vigtig del af overførslen.

Du kan angive en Exchange Online for at modtage meddelelser, som brugere rapporterer som skadelige eller ikke skadelige. Du kan finde flere instruktioner under [Brugerrapporterede meddelelsesindstillinger](user-submission.md). Denne postkasse kan modtage kopier af meddelelser, som dine brugere har sendt til Microsoft, eller postkassen kan opfange meddelelser uden at rapportere dem til Microsoft (I er sikkerhedsteamet kan analysere og sende meddelelserne manuelt). Denne opfangelsestilgang tillader dog ikke, at tjenesten automatisk finjusterer og lærer.

Du skal også bekræfte, at alle brugere i pilotprojektet har en understøttet meddelelsesrapporteringsapp installeret i Outlook der er kompatibel med brugerindsendelse. Disse apps omfatter:

- [Tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md)
- [Tilføjelsesprogrammet Report Phishing](enable-the-report-phish-add-in.md)
- Understøttede rapporteringsværktøjer fra tredjepart som beskrevet [her](user-submission.md#third-party-reporting-tools).

Lad være med at understrege vigtigheden af dette trin. Data fra brugerindsendelser giver dig den feedbackløkke, du skal bruge for at bekræfte en god og ensartet slutbrugeroplevelse før og efter overførslen. Denne feedback hjælper dig med at træffe velovervejede beslutninger om konfiguration af politikker samt levere data-sikkerhedskopierede rapporter til din administration om, at overførslen gik problemfrit.

I stedet for at være afhængig af data, der understøttes af hele organisationens oplevelse, har mere end én overførsel resulteret i følelsesmæssige konsekvenser baseret på en enkelt negativ brugeroplevelse. Hvis du har kørt phishing-simulering, kan du desuden bruge feedback fra dine brugere til at give dig besked, når de ser noget risikabelt, der kan kræve undersøgelse.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>Trin 3: Bevar eller opret reglen for mailflow i SCL=-1

Da din indgående mail dirigeres gennem en anden beskyttelsestjeneste, der står foran Microsoft 365, er det meget sandsynligt, at du allerede har en regel for mailflow (også kaldet en transportregel) i Exchange Online, der angiver SCL-niveauet for alle indgående mails til værdien -1 (tilsidesæt spamfiltrering). De fleste tredjepartsbeskyttelsestjenester opfordrer til denne SCL=-1-regel for mailflow til Microsoft 365 kunder, der ønsker at bruge deres tjenester.

Hvis du bruger en anden mekanisme til at tilsidesætte Microsoft-filtreringsstakken (f.eks. en liste over tilladte IP-adresser), anbefaler vi, at du skifter til at bruge en SCL=-1-mailflowregel, så længe al indgående internetmail til Microsoft 365 kommer fra tredjepartsbeskyttelsestjenesten (ingen mails flyder direkte fra internettet til Microsoft 365).

Reglen for mailflow i SCL=-1 er vigtig under overførslen af følgende årsager:

- Du kan bruge [Threat Explorer til](email-security-in-microsoft-defender.md) at se, hvilke funktioner i Microsoft-stakken der ville *have handlet* på meddelelser uden at påvirke resultaterne fra din eksisterende beskyttelsestjeneste.
- Du kan gradvist justere, hvem der er beskyttet af Microsoft 365 filtreringsstakken, ved at konfigurere undtagelser til reglen SCL=-1-mailflow. Undtagelserne vil være medlemmer af pilotdistributionsgrupperne, som vi anbefaler senere i denne artikel.

  Før eller under overgangen fra din MX-post til Microsoft 365 deaktiverer du denne regel for at aktivere den fulde beskyttelse af Microsoft 365-beskyttelsestakken for alle modtagere i organisationen.

Få mere at vide under [Brug regler for mailflow til at indstille spamtillidsniveauet (SCL) i meddelelser Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Bemærkninger**:

- Hvis du planlægger at tillade, at internetmail flyder gennem din eksisterende beskyttelsestjeneste og direkte ind i Microsoft 365 på samme tid, skal du begrænse SCL=-1-mailflowreglen (mail, der tilsidesætter spamfiltrering) til mails, der kun er gået gennem din eksisterende beskyttelsestjeneste. Du vil ikke have, at ufiltrerede internetmails lander i brugerpostkasser Microsoft 365.

  Hvis du vil identificere mails, der allerede er blevet scannet af din eksisterende beskyttelsestjeneste, kan du føje en betingelse til SCL=-1-mailflowreglen. Eksempel:

  - **Til skybaserede beskyttelsestjenester: Du** kan bruge en header- og headerværdi, der er entydig for din organisation. Meddelelser med sidehovedet scannes ikke af Microsoft 365. Meddelelser uden sidehovedet scannes af Microsoft 365
  - **Til lokale beskyttelsestjenester eller -enheder: Du** kan bruge kilde-IP-adresser. Meddelelser fra kilde-IP-adresser scannes ikke af Microsoft 365. Meddelelser, der ikke er fra kilde-IP-adresserne, scannes af Microsoft 365.

- Brug ikke udelukkende MX-poster til at styre, om mails bliver filtreret. Afsendere kan nemt ignorere MX-posten og sende mails direkte Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>Trin 4: Konfigurer udvidet filtrering for forbindelser

Det første, du skal gøre, er at konfigurere udvidet filtrering [for](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) forbindelser (også kaldet skip *listing) på* den forbindelse, der bruges til mailflow fra din eksisterende beskyttelsestjeneste til Microsoft 365. Du kan bruge rapporten [over indgående meddelelser til](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) at identificere forbindelsen.

Forbedret filtrering for forbindelser er påkrævet af Defender, for Office 365 at du kan se, hvor internetmeddelelser faktisk stammer fra. Udvidet filtrering for forbindelser forbedrer i høj grad nøjagtigheden af Microsoft-filtreringsstakken (især [efterlignet](anti-spoofing-protection.md) intelligens samt funktioner til efter brud i [Threat Explorer](threat-explorer.md) og [automated Investigation & Response (AIR)](automated-investigation-response-office.md)).

For at aktivere udvidet filtrering for forbindelser korrekt skal du tilføje de **offentlige IP-adresser** \***\*\***\* for alle tredjepartstjenester og/eller lokale mailsystemværter, der distribuerer indgående mail til Microsoft 365.

For at bekræfte at Udvidet filtrering for forbindelser fungerer, skal du kontrollere, at indgående meddelelser indeholder en eller begge af følgende overskrifter:

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>Trin 5: Opret pilotbeskyttelsespolitikker

Ved at oprette produktionspolitikker, også selvom de ikke anvendes for alle brugere, kan du teste funktioner efter brud som [f.eks. Threat Explorer](threat-explorer.md) og teste integrering af Defender for Office 365 i sikkerhedsresponsteamets processer.

> [!IMPORTANT]
> Politikker kan være begrænset til brugere, grupper eller domæner. Vi anbefaler ikke at blande alle tre i én politik, da kun brugere, der matcher alle tre, falder inden for politikkens omfang. For pilotpolitikker anbefaler vi brug af grupper eller brugere. Til produktionspolitikker anbefaler vi, at du bruger domæner. Det er meget vigtigt at forstå, at  det kun er brugerens primære maildomæne, der afgør, om brugeren falder inden for politikkens område. Så hvis du skifter MX-posten for en brugers sekundære domæne, skal du sørge for, at brugerens primære domæne også er dækket af en politik.

### <a name="create-pilot-safe-attachments-policies"></a>Opret et pilotprojekt Pengeskab politikker for vedhæftede filer

[Pengeskab vedhæftede filer](safe-attachments.md) er den nemmeste Defender for Office 365 at aktivere og teste, før du skifter din MX-post. Pengeskab vedhæftede filer har følgende fordele:

- Minimal konfiguration.
- Meget lav risiko for falske positive.
- Lignende funktionsmåde med beskyttelse mod malware, som altid er tændt og ikke påvirkes af SCL=-1-mailflowreglen.

Opret en Pengeskab politik for vedhæftede filer til dine pilotbrugere.

Du kan finde de anbefalede indstillinger [under Anbefalede Pengeskab politikindstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Bemærk, at standard- og strenganbefalinger er de samme. Hvis du vil oprette politikken, skal [du se Konfigurer Pengeskab politikker for vedhæftede filer](set-up-safe-attachments-policies.md). Sørg for at bruge gruppen **MDOPilotSafeAttachments\_** som betingelse for politikken (hvem politikken gælder for).

> [!IMPORTANT]
> I dag er der ingen standardpolitik for Pengeskab vedhæftede filer. Inden du skifter MX-poster, anbefaler vi, at du har en Pengeskab politik for vedhæftede filer, der beskytter hele organisationen.

### <a name="create-pilot-safe-links-policies"></a>Oprette pilotpolitikker Pengeskab links

> [!NOTE]
> Vi understøtter ikke ombrydning eller omskrivning af allerede ombrudte eller omskrevne links. Hvis din aktuelle beskyttelsestjeneste allerede ombrydes eller omskriver links i mails, skal du deaktivere denne funktion for dine pilotbrugere. En måde at sikre, at dette ikke sker, er at udelade URL-domænet for den anden tjeneste i Pengeskab Links-politikken.
>
> Pengeskab Links-beskyttelse for understøttede Office-apps er en global indstilling, der gælder for alle brugere med licens. Du kan aktivere eller deaktivere den globalt, ikke for bestemte brugere. Du kan finde flere oplysninger [under Konfigurere Pengeskab Links-beskyttelse til Office 365 apps](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Opret en Pengeskab Links-politik for dine pilotbrugere. Chancerne for falske positive i Pengeskab Links er også ret lave, men du bør overveje at teste funktionen for et mindre antal pilotbrugere end Pengeskab Vedhæftede filer. Da funktionen påvirker brugeroplevelsen, bør du overveje en plan for at informere brugerne.

Du kan finde de anbefalede indstillinger [under Anbefalede Pengeskab Links-politikindstillinger](recommended-settings-for-eop-and-office365.md#safe-links-settings). Bemærk, at standard- og strenganbefalinger er de samme. Hvis du vil oprette politikken, skal [du se Konfigurer Pengeskab Links-politikker](set-up-safe-links-policies.md). Sørg for at bruge gruppen **MDOPilotSafeLinks\_** som betingelse for politikken (hvem politikken gælder for).

> [!IMPORTANT]
> I dag er der ingen standardpolitik Pengeskab Links. Inden du skifter MX-poster, anbefaler vi, at du har en Pengeskab Links-politik, der beskytter hele organisationen.

### <a name="create-pilot-anti-spam-policies"></a>Opret pilotpolitikker for uønsket post

Opret to antispampolitikker for pilotbrugere:

- En politik, der bruger standardindstillingerne. Brug gruppen **MDOPilotSpamPhishStandard\_\_** som betingelse for politikken (hvem politikken gælder for).
- En politik, der anvender faste indstillinger. Brug gruppen **MDOPilotSpamPhishStrict\_\_** som betingelse for politikken (hvem politikken gælder for). Denne politik bør have en højere prioritet (lavere tal) end politikken med standardindstillingerne.

Du kan finde de anbefalede Standard- og Restriktive indstillinger [under Anbefalede indstillinger for politik mod uønsket post](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). Hvis du vil oprette politikkerne, skal [du se Konfigurer antispam-politikker](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Opret pilotpolitikker for phishing

Opret to antiphishing-politikker for pilotbrugere:

- En politik, der bruger standardindstillingerne, med undtagelse af handlinger til registrering af efterligning som beskrevet nedenfor. Brug gruppen **MDOPilotSpamPhishStandard\_\_** som betingelse for politikken (hvem politikken gælder for).
- En politik, der bruger faste indstillinger med undtagelse af registreringshandlinger efter efterligning som beskrevet nedenfor. Brug gruppen **MDOPilotSpamPhishStrict\_\_** som betingelse for politikken (hvem politikken gælder for). Denne politik bør have en højere prioritet (lavere tal) end politikken med standardindstillingerne.

Ved spoof-registreringer er den anbefalede standardhandling Flyt meddelelsen til **modtagernes** mapper med Uønsket mail, og den anbefalede Streng-handling er **Sæt meddelelsen i karantæne**. Brug efterlignet intelligensindsigt til at observere resultaterne. Tilsidesættelser forklares i næste afsnit. Du kan finde flere oplysninger [under Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

Ved repræsentationsregistreringer skal du ignorere de anbefalede Standard- og Restriktive handlinger for pilotpolitikkerne. Brug i stedet **værdien Anvend ikke nogen handling** til følgende indstillinger:

- **Hvis meddelelsen registreres som en efterligning af en bruger**
- **Hvis meddelelsen registreres som efterligning af domæne**
- **Hvis postkasseintelligens registrerer en efterligning af en bruger**

Brug repræsentationsindsigtet til at se resultaterne. Du kan få mere at [vide under Repræsentationsindsigt i Defender Office 365](impersonation-insight.md).

Du skal finjustere beskyttelse mod spoofing (juster tillader og blokke) og aktivere hver repræsentationsbeskyttelseshandling for at sætte i karantæne eller flytte meddelelserne til mappen Uønsket mail (baseret på standardanbefalinger eller restriktive anbefalinger). Du kan se resultaterne og justere indstillingerne efter behov.

Du kan finde flere oplysninger i følgende emner:

- [Beskyttelse mod spoofing](anti-spoofing-protection.md)
- [Indstillinger for repræsentation i antiphishing-politikker](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Konfigurer antiphishing-politikker i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Næste trin

**Tillykke**! Du har fuldført **konfigurationsfasen** for din [overførsel til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)!

- Fortsæt til [Fase 3: Onboard](migrate-to-defender-for-office-365-onboard.md).
