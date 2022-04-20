---
title: 'Migrer til Microsoft Defender for Office 365 fase 3: Onboard'
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
description: Fuldfør trinnene til overførsel fra en beskyttelsestjeneste eller enhed fra tredjepart til Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a2b70cdd53797a4985cc76f777401fa33f3e1163
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939207"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Migrer til Microsoft Defender for Office 365 – fase 3: Onboard

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

<br>

|[![Fase 1: Forbered.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Fase 1: Forbered](migrate-to-defender-for-office-365-prepare.md)|[![Fase 2: Konfigurer.](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Fase 2: Konfigurer](migrate-to-defender-for-office-365-setup.md)|![Fase 3: Ombord.](../../media/phase-diagrams/onboard.png) <br> Fase 3: Onboard|
|---|---|---|
|||*Du er her!*|

Velkommen til **fase 3: Onboard** af din **[migrering til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Denne overførselsfase omfatter følgende trin:

1. [Begynd onboarding af Teams for sikkerhed](#step-1-begin-onboarding-security-teams)
2. [(Valgfrit) Undtaget pilotbrugere fra filtrering efter din eksisterende beskyttelsestjeneste](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Juster spoof intelligence](#step-3-tune-spoof-intelligence)
4. [Juster repræsentationsbeskyttelse og postkasseintelligens](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Brug data fra brugerindsendelser til at måle og justere](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(Valgfrit) Føj flere brugere til din pilot, og gentage](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Udvid Microsoft 365 beskyttelse til alle brugere, og slå reglen for SCL=-1-mailflow fra](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [Skift dine MX-poster](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>Trin 1: Begynd at onboarde Teams

Hvis din organisation har et team for sikkerhedssvar, er det nu tid til at begynde at integrere Microsoft Defender for Office 365 i dine svarprocesser, herunder systemer til oprettelse af billetter. Dette er et helt emne for sig selv, men det er nogle gange overset. Hvis du henter det involverede sikkerhedssvarteam tidligt, sikrer du, at din organisation er klar til at håndtere trusler, når du skifter dine MX-poster. Svar på hændelser skal være veludstyret til at håndtere følgende opgaver:

- Få mere at vide om de nye værktøjer, og integrer dem i eksisterende flow. Eksempel:
  - Administration af karantænemeddelelser er vigtig. Du kan finde instruktioner under [Administrer karantænemeddelelser og filer som administrator](manage-quarantined-messages-and-files.md).
  - Meddelelsessporing giver dig mulighed for at se, hvad der skete med meddelelser, når de kommer ind eller forlader Microsoft 365. Du kan finde flere oplysninger [under Meddelelsessporing i det moderne Exchange Administration i Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Identificer risici, der kan være blevet overført til organisationen.
- Tilpas [beskeder](../../compliance/alert-policies.md) for organisationsprocesser.
- Administrer hændelseskøen, og afhjælp potentielle risici.

Hvis din organisation har købt Microsoft Defender for Office 365 Plan 2, bør de begynde at blive fortrolige med og bruge funktioner som Threat Explorer, Avanceret jagt og Hændelser. Du kan få mere at vide om relevante kurser under <https://aka.ms/mdoninja>.

Hvis dit sikkerhedssvarteam indsamler og analyserer ufiltrerede meddelelser, kan du konfigurere en SecOps-postkasse til at modtage disse ufiltrerede meddelelser. Du kan finde instruktioner under [Konfigurer SecOps-postkasser i politikken for avanceret levering](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

Du kan finde flere oplysninger om integration med din SIEM/SOAR i følgende artikler:

- [Oversigt over Microsoft 365 Defender API'er](/microsoft-365/security/defender/api-overview)
- [Streaming-API](/microsoft-365/security/defender/streaming-api)
- [Avanceret jagt-API](/microsoft-365/security/defender/api-advanced-hunting)
- [Hændelses-API'er](/microsoft-365/security/defender/api-incident)

Hvis din organisation ikke har et sikkerhedssvarteam eller eksisterende procesforløb, kan du bruge denne gang til at blive fortrolig med grundlæggende jagt- og svarfunktioner i Defender for Office 365. Du kan få flere oplysninger under [Trusselsundersøgelse og -svar](office-365-ti.md).

### <a name="rbac-roles"></a>RBAC-roller

Tilladelser i Defender for Office 365 er baseret på rollebaseret adgangskontrol og forklares i Tilladelser på [Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md). Dette er de vigtige punkter, du skal være opmærksom på:

- Azure AD-roller giver tilladelser til **alle** arbejdsbelastninger i Microsoft 365. Hvis du f.eks. føjer en bruger til sikkerhedsadministratoren i Azure Portal, har vedkommende tilladelser som sikkerhedsadministrator overalt.
- Mail & samarbejdsroller på Microsoft 365 Defender-portalen giver tilladelser til Microsoft 365 Defender-portalen, Microsoft Purview-overholdelsesportalen og det ældre center for sikkerhed & overholdelse. Hvis du f.eks. føjer en bruger til Sikkerhedsadministrator på Microsoft 365 Defender-portalen, har vedkommende **kun** adgang som sikkerhedsadministrator på Microsoft 365 Defender-portalen, i Microsoft Purview-overholdelsesportalen og i Security & Compliance Center.
- Mange funktioner i Microsoft 365 Defender-portalen er baseret på Exchange Online PowerShell-cmdlet'er og kræver derfor medlemskab af rollegrupper i de tilsvarende roller (teknisk set, rollegrupper) i Exchange Online (især for at få adgang til det tilsvarende Exchange Online  PowerShell-cmdlet'er).
- Der er mail & samarbejdsroller på Microsoft 365 Defender-portalen, der ikke har nogen roller, der svarer til Azure AD-roller, og som er vigtige for sikkerhedshandlinger (f.eks. rollen Prøveversion og rollen Søg og Fjern).

Det er typisk kun en delmængde af sikkerhedsafdelingen, der har brug for yderligere rettigheder til at downloade meddelelser direkte fra brugerpostkasser. Dette kræver en ekstra tilladelse, som Sikkerhedslæser ikke har som standard.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>Trin 2: (Valgfrit) Undtaget pilotbrugere fra at filtrere efter din eksisterende beskyttelsestjeneste

Selvom dette trin ikke er påkrævet, bør du overveje at konfigurere dine pilotbrugere til at omgå filtrering fra din eksisterende beskyttelsestjeneste. Denne handling gør det muligt for Defender for Office 365 at håndtere **alle** filtrerings- og beskyttelsesopgaver for pilotbrugerne. Hvis du ikke fritager dine pilotbrugere fra din eksisterende beskyttelsestjeneste, fungerer Defender for Office 365 kun effektivt på misser fra den anden tjeneste (filtrering af meddelelser, der allerede er filtreret).

> [!NOTE]
> Dette trin er udtrykkeligt påkrævet, hvis din aktuelle beskyttelsestjeneste indeholder linkombrydning, men du vil styre Pengeskab Links-funktionalitet. Dobbeltombrydning af links understøttes ikke.

## <a name="step-3-tune-spoof-intelligence"></a>Trin 3: Juster spoof intelligence

Kontrollér [Spoof Intelligence-indsigten](learn-about-spoof-intelligence.md) for at se, hvad der tillades eller blokeres som spoofing, og for at afgøre, om du har brug for at tilsidesætte systemoverskriften for spoofing. Nogle kilder til din forretningskritiske mail kan have konfigureret posterne for mailgodkendelse forkert i DNS (SPF, DKIM og DMARC), og du bruger muligvis tilsidesættelser i din eksisterende beskyttelsestjeneste til at maskere deres domæneproblemer.

Spoof intelligence kan redde mail fra domæner uden korrekte e-mail-godkendelsesposter i DNS, men funktionen har nogle gange brug for hjælp til at skelne god spoofing fra dårlig spoofing. Fokuser på følgende typer meddelelseskilder:

- Meddelelseskilder, der ligger uden for de IP-adresseområder, der er defineret i [Udvidet filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- Meddelelseskilder, der har det højeste antal meddelelser.
- Meddelelseskilder, der har den største indvirkning på din organisation.

Spoof intelligence vil efterhånden tilpasse sig selv, når du har konfigureret brugerindsendelser, så der er ikke behov for perfektion.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>Trin 4: Juster repræsentationsbeskyttelse og postkasseintelligens

Når du har haft tid nok til at overvåge resultaterne af repræsentationsbeskyttelse i **Anvend ikke nogen handlingstilstand** , kan du aktivere hver enkelt repræsentationsbeskyttelseshandling i politikker til beskyttelse mod phishing:

- Beskyttelse af brugeridentificeret repræsentation: **Sæt meddelelsen i karantæne** for både Standard og Strict.
- Beskyttelse mod repræsentation af domæner: **Sæt meddelelsen i karantæne** for både Standard og Strict.
- Beskyttelse af postkasseintelligens: **Flyt meddelelsen til modtagernes mapper med uønsket mail** for Standard. **Sæt meddelelsen i karantæne** for Strict.

Jo længere du overvåger resultaterne af repræsentationsbeskyttelse uden at reagere på meddelelserne, jo flere data skal du identificere, tillader eller blokerer, der kan være påkrævet. Overvej at bruge en forsinkelse mellem aktivering af hver enkelt beskyttelse, der er betydelig nok til at tillade observation og justering.

> [!NOTE]
> Det er vigtigt, at disse beskyttelser overvåges og justeres hyppigt og kontinuerligt. Hvis du har mistanke om et falsk positivt element, skal du kun undersøge årsagen og bruge tilsidesættelser efter behov og kun for den registreringsfunktion, der kræver den.

### <a name="tune-mailbox-intelligence"></a>Juster postkasseintelligens

Selvom postkasseintelligens er konfigureret til ikke at udføre nogen handling på meddelelser, der blev [bestemt til at være repræsentationsforsøg](impersonation-insight.md), har den været på og lært mønstret for afsendelse og modtagelse af mail fra pilotbrugerne. Hvis en ekstern bruger er i kontakt med en af dine pilotbrugere, identificeres meddelelser fra den eksterne bruger ikke som repræsentationsforsøg ved hjælp af postkasseintelligens (hvilket reducerer falske positiver).

Når du er klar, skal du gøre følgende for at tillade, at postkasseintelligens reagerer på meddelelser, der registreres som repræsentationsforsøg:

- I politikken til bekæmpelse af phishing med standardbeskyttelsesindstillingerne skal du ændre værdien af **Hvis mailbox intelligence registrerer en repræsenteret bruger** , så **meddelelsen flyttes til modtagernes mapper med uønsket mail**.

- I politikken til bekæmpelse af phishing med indstillingerne for streng beskyttelse skal du ændre værdien af **Hvis mailbox intelligence registrerer og repræsenterer bruger** fra til **Sæt meddelelsen i karantæne**.

Hvis du vil redigere politikkerne, skal du se [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Når du har observeret resultaterne og foretaget eventuelle justeringer, skal du gå til næste afsnit for at sætte meddelelser i karantæne, der er registreret af brugerens repræsentation.

### <a name="tune-user-impersonation-protection"></a>Juster beskyttelse mod repræsentation af brugere

I begge dine anti-phishing-politikker, der er baseret på Standard- og Strict-indstillinger, skal du ændre værdien af **If message is detected as a repersonated user to** **Quarantine the message**.

Kontrollér [repræsentationsindsigten](impersonation-insight.md) for at se, hvad der blokeres, når brugeren repræsenterer forsøg.

Hvis du vil redigere politikkerne, skal du se [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Når du har observeret resultaterne og foretaget eventuelle justeringer, skal du gå til næste afsnit for at sætte meddelelser i karantæne, der er registreret af domæne repræsentering.

### <a name="tune-domain-impersonation-protection"></a>Juster beskyttelse mod repræsentation af domæne

I begge dine anti-phishing-politikker, der er baseret på Standard- og Strict-indstillinger, skal du ændre værdien af **Hvis meddelelse registreres som et repræsenterede domæne** for at **sætte meddelelsen i karantæne**.

Kontrollér [repræsentationsindsigten](impersonation-insight.md) for at se, hvad der blokeres som forsøg på at repræsentere et domæne.

Hvis du vil redigere politikkerne, skal du se [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Se resultaterne, og foretag eventuelle justeringer efter behov.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>Trin 5: Brug data fra brugerindsendelser til at måle og justere

Når pilotbrugerne rapporterer falske positiver og falske negativer, vises meddelelserne på [siden Indsendelser på portalen Microsoft 365 Defender](admin-submission.md). Du kan rapportere de forkert identificerede meddelelser til Microsoft til analyse og bruge oplysningerne til at justere indstillingerne og undtagelserne i dine pilotpoliti efter behov.

Brug følgende funktioner til at overvåge og gentage beskyttelsesindstillinger i Defender for Office 365:

- [Karantæne](manage-quarantined-messages-and-files.md)
- [Trusselsoversigt](email-security-in-microsoft-defender.md)
- [Mailsikkerhedsrapporter](view-email-security-reports.md)
- [Defender for Office 365 rapporter](view-reports-for-mdo.md)
- [Indsigt i mailflow](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Mailflowrapporter](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Hvis din organisation bruger en tredjepartstjeneste til brugerrapporter, kan du integrere disse data i din feedbackløkke.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>Trin 6: (Valgfrit) Føj flere brugere til din pilot, og gentag

Efterhånden som du finder og løser problemer, kan du føje flere brugere til pilotgrupperne (og tilsvarende fritage disse nye pilotbrugere fra at scanne af din eksisterende beskyttelsestjeneste efter behov). Jo flere test, du udfører nu, jo færre brugerproblemer skal du håndtere senere. Denne "vandfalds"-tilgang giver mulighed for at tilpasse sig større dele af organisationen og giver dine sikkerhedsteams tid til at tilpasse sig de nye værktøjer og processer.

- Microsoft 365 genererer beskeder, når phishing-meddelelser med høj sikkerhed er tilladt af organisationens politikker. Du har følgende muligheder for at identificere disse meddelelser:
  - Tilsidesættelser i [statusrapporten om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
  - Filtrer i Threat Explorer for at identificere meddelelserne.
  - Filtrer i Avanceret jagt for at identificere meddelelserne.

  Rapportér eventuelle falske positiver til Microsoft så tidligt som muligt via administratorindsendelser, brug funktionen Tillad [/bloker](tenant-allow-block-list.md) lejer til at konfigurere sikre tilsidesættelser for disse falske positiver.

- Det er også en god idé at undersøge unødvendige tilsidesættelser. Med andre ord, se på de domme, som Microsoft 365 ville have givet på meddelelserne. Hvis Microsoft365 gengivede den korrekte dom, reduceres eller fjernes behovet for tilsidesættelse i høj grad.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>Trin 7: Udvid Microsoft 365 beskyttelse til alle brugere, og slå reglen for SCL=-1-mailflow fra

Udfør trinnene i dette afsnit, når du er klar til at skifte dine MX-poster, så de peger på Microsoft 365.

1. Udvid pilotpolitikkerne til hele organisationen. Grundlæggende er der forskellige måder at gøre dette på:
   - Brug [forudindstillede sikkerhedspolitikker](preset-security-policies.md) , og del dine brugere mellem standardbeskyttelsesprofilen og den strenge beskyttelsesprofil (sørg for, at alle er dækket). Forudindstillede sikkerhedspolitikker anvendes før brugerdefinerede politikker, som du har oprettet, eller nogen standardpolitikker. Du kan slå dine individuelle pilotpolitikker fra uden at slette dem.

     Ulempen ved forudindstillede sikkerhedspolitikker er, at du ikke kan ændre mange af de vigtige indstillinger, når du har oprettet dem.

   - Rediger omfanget af de politikker, du oprettede og justerede under pilotprojektet, så de omfatter alle brugere (f.eks. alle modtagere i alle domæner). Husk, at hvis flere politikker af samme type (f.eks. politikker til bekæmpelse af phishing) gælder for den samme bruger (individuelt, efter gruppemedlemskab eller maildomæne), er det kun indstillingerne for politikken med den højeste prioritet (det laveste prioritetsnummer), der anvendes, og behandlingsstop for denne type politik.

2. Deaktiver reglen for SCL=-1-mailflow (du kan slå den fra uden at slette den).

3. Kontrollér, at de tidligere ændringer er trådt i kraft, og at Defender for Office 365 nu er aktiveret korrekt for alle brugere. På dette tidspunkt er alle beskyttelsesfunktioner i Defender for Office 365 nu tilladt at handle på mail for alle modtagere, men denne mail er allerede blevet scannet af din eksisterende beskyttelsestjeneste.

Du kan sætte dataoptagelse og -justering på pause i denne fase.

## <a name="step-8-switch-your-mx-records"></a>Trin 8: Skift dine MX-poster

> [!NOTE]
>
> - Når du skifter MX-post for dit domæne, kan det tage op til 48 timer, før ændringerne overføres over hele internettet.
>
> - Vi anbefaler, at du sænker TTL-værdien for dine DNS-poster for at muliggøre hurtigere svar og mulig annullering (hvis det er nødvendigt). Du kan vende tilbage til den oprindelige TTL-værdi, når overgangen er fuldført og bekræftet.
>
> - Du bør overveje at starte med at ændre domæner, der bruges mindre hyppigt. Du kan afbryde og overvåge, før du flytter til større domæner. Selvom du gør dette, skal du dog stadig sørge for, at alle brugere og domæner er dækket af politikker, fordi sekundære SMTP-domæner fortolkes som primære domæner før politikprogrammet.
>   
> - Flere MX-poster for et enkelt domæne fungerer teknisk set, så du kan have opdelt routing, forudsat at du har fulgt alle vejledningen i denne artikel. Du skal især sørge for, at politikker anvendes på alle brugere, at reglen SCL=-1 mailflow kun anvendes på mails, der passerer gennem din eksisterende beskyttelsestjeneste, som beskrevet i [trin 3: Vedligehold eller opret reglen for SCL=-1-mailflowet](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Denne konfiguration introducerer dog funktionsmåde, der gør fejlfinding meget vanskeligere, og derfor anbefaler vi det normalt ikke, især ikke i længere tid.
>
> - Før du skifter MX-poster, skal du kontrollere, at følgende indstillinger ikke er aktiveret på den indgående connector fra beskyttelsestjenesten til Microsoft 365. Connectoren vil typisk have en eller flere af følgende indstillinger konfigureret:
>
>   - **og kræve, at emnenavnet på det certifikat, som partneren bruger til at godkende med Office 365 svarer til dette domænenavn** (*RestrictDomainsToCertificate*)
>   - **Afvis mails, hvis de ikke sendes fra dette IP-adresseområde** (*RestrictDomainsToIPAddresses*)
>
>   Hvis connectortypen er **Partner** , og en af disse indstillinger er slået til, mislykkes al postlevering til dine domæner, når du har skiftet dine MX-poster. Du skal deaktivere disse indstillinger, før du fortsætter. Hvis connectoren er en connector i det lokale miljø, der bruges til hybrid, behøver du ikke at ændre connectoren i det lokale miljø. Men du kan stadig kontrollere, om der findes en **Partner-connector** .
>   
> - Hvis din aktuelle mailgateway også giver modtagervalidering, kan det være en god idé at kontrollere, at domænet er konfigureret som [autoritativt](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i Microsoft 365. Dette kan forhindre unødvendige bounce-meddelelser.

Når du er klar, skal du skifte MX-posten for dine domæner. Du kan overføre alle dine domæner på én gang. Du kan også overføre mindre ofte anvendte domæner først og derefter overføre resten senere.

Du er velkommen til at afbryde og evaluere her når som helst. Men husk: Når du slår reglen for SCL=-1-mailflow fra, kan brugerne have to forskellige oplevelser til at kontrollere falske positiver. Jo hurtigere du kan give en enkelt, ensartet oplevelse, desto gladere er dine brugere og helpdeskteams, når de skal foretage fejlfinding af en manglende meddelelse.

## <a name="next-steps"></a>Næste trin

Tillykke! Du har fuldført [overførslen til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)! Da du har fulgt trinnene i denne migreringsvejledning, bør de første par dage, hvor mail leveres direkte til Microsoft 365, være meget jævnere.

Nu begynder du den normale drift og vedligeholdelse af Defender for Office 365. Overvåg og hold øje med problemer, der ligner det, du oplevede under pilotprojektet, men i større skala. [Spoof intelligence-indsigten](learn-about-spoof-intelligence.md) og [repræsentationsindsigten](impersonation-insight.md) vil være mest nyttig, men overvej at gøre følgende aktiviteter til en almindelig forekomst:

- Gennemse brugerindsendelser, især [brugerrapporterede phishing-meddelelser](automated-investigation-response-office.md)
- Gennemse tilsidesættelser i [rapporten over status for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- Brug [Avancerede](/microsoft-365/security/defender/advanced-hunting-example) jagtforespørgsler til at søge efter muligheder og risikable meddelelser.
