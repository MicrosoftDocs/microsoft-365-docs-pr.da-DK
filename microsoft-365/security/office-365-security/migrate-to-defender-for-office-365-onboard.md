---
title: 'Overfør Microsoft Defender for Office 365 fase 3: Onboard'
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
description: Fuldfør trinnene for overførsel fra en tredjepartsbeskyttelsestjeneste eller -enhed for at Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9160a6fc79ba94e4cb86fb0f96f46e565c0f613c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467505"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Overfør til Microsoft Defender for Office 365 - Fase 3: Onboard

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

<br>

|[![Fase 1: Forbered.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Fase 1: Forbered](migrate-to-defender-for-office-365-prepare.md)|[![Fase 2: Konfigurer.](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Fase 2: Konfigurer](migrate-to-defender-for-office-365-setup.md)|![Fase 3: Onboard.](../../media/phase-diagrams/onboard.png) <br> Fase 3: Onboard|
|---|---|---|
|||*Du er her!*|

Velkommen til **Fase 3: Onboard** af din **[overførsel til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Denne overførselsfase omfatter følgende trin:

1. [Begynd onboardingsikkerhedsopdateringer Teams](#step-1-begin-onboarding-security-teams)
2. [(Valgfrit) Undtage pilotbrugere fra filtrering af din eksisterende beskyttelsestjeneste](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Finjuster efterlignet intelligens](#step-3-tune-spoof-intelligence)
4. [Finjustere repræsentationsbeskyttelse og postkasseintelligens](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Brug data fra brugerindsendelser til at måle og justere](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(Valgfrit) Føj flere brugere til dit pilotprojekt og din testning](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Udvide Microsoft 365 beskyttelse af mail til alle brugere og deaktivere reglen for mailflow i SCL=-1](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [Skifte dine MX-poster](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>Trin 1: Begynd onboardingsikkerhed Teams

Hvis din organisation har et sikkerhedsresponsteam, er det nu tid til at begynde at integrere Microsoft Defender for Office 365 i dine svarprocesser, herunder billetsystemer. Dette er for sig selv et helt emne, men det er nogle gange overset. Når sikkerhedsresponsteamet bliver involveret tidligt, sikrer du, at din organisation er klar til at håndtere trusler, når du skifter dine MX-poster. Hændelsesrespons skal være godt udstyret til at håndtere følgende opgaver:

- Lær de nye værktøjer at bruge, og integrer dem i eksisterende flow. Eksempel:
  - Administratorstyring af meddelelser, der er sat i karantæne, er vigtig. Du kan finde en vejledning [i Administrere meddelelser og filer, der er sat i karantæne, som administrator](manage-quarantined-messages-and-files.md).
  - Meddelelsessporing giver dig mulighed for at se, hvad der er sket med meddelelser, mens de skriver eller Microsoft 365. Få mere at vide under [Meddelelsessporing i den moderne Exchange Administration i Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Identificer risici, der kan være blevet ladt ind i organisationen.
- Finjuster og [tilpas beskeder](../../compliance/alert-policies.md) for organisatoriske processer.
- Administrer hændelseskøen, og afhjulpet potentielle risici.

Hvis din organisation har købt Microsoft Defender for Office 365 Plan 2, bør de begynde at blive fortrolige med og bruge funktioner som Threat Explorer, Avanceret jagt og Hændelser. Du kan finde relevante kurser under <https://aka.ms/mdoninja>.

Hvis dit sikkerhedssvarteam indsamler og analyserer ufiltrerede meddelelser, kan du konfigurere en SecOps-postkasse til at modtage disse ufiltrerede meddelelser. Du kan finde en vejledning [under Konfigurere SecOps-postkasser i politikken for avanceret levering](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

### <a name="siemsoar"></a>SIEM/SOAR

Du kan finde flere oplysninger om integration med din SIEM/SOAR i følgende artikler:

- [Oversigt over Microsoft 365 Defender API'er](/microsoft-365/security/defender/api-overview)
- [Streaming-API](/microsoft-365/security/defender/streaming-api)
- [Avanceret api til jagt](/microsoft-365/security/defender/api-advanced-hunting)
- [Api'er til hændelser](/microsoft-365/security/defender/api-incident)

Hvis din organisation ikke har et sikkerhedsresponsteam eller eksisterende procesflows, kan du bruge denne gang til at gøre dig bekendt med grundlæggende jagt og svarfunktioner Defender for Office 365. Du kan få mere at vide [under Trusselsundersøgelse og -svar](office-365-ti.md).

### <a name="rbac-roles"></a>RBAC-roller

Tilladelser i Defender for Office 365 er baseret på rollebaseret adgangskontrol og er beskrevet i Tilladelser i [Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md). Dette er de vigtige punkter, du skal huske på:

- Azure AD-roller giver tilladelser til **alle** arbejdsbelastninger i Microsoft 365. Hvis du f.eks. føjer en bruger til sikkerhedsadministratoren i Azure Portal, har de overalt sikkerhedsadministratortilladelser.
- Mail &-samarbejdsroller i Microsoft 365 Defender-portalen giver tilladelser til Microsoft 365 Defender-portalen, Microsoft 365 Overholdelsescenter og det ældre Security & Compliance Center. Hvis du f.eks. føjer en bruger til sikkerhedsadministrator i Microsoft 365 Defender-portalen, har de kun adgang til sikkerhedsadministratoren i Microsoft 365 Defender-portalen, Microsoft 365 Overholdelsescenter og Security & Compliance Center.
- Mange funktioner i Microsoft 365 Defender-portalen er baseret på Exchange Online PowerShell-cmdlet'er og kræver derfor rollegruppemedlemskab til de tilsvarende roller (teknisk set rollegrupper) i Exchange Online (især for at få adgang til de tilsvarende Exchange Online  PowerShell-cmdlet'er).
- Der findes roller for &-samarbejde i Microsoft 365 Defender-portalen, der ikke svarer til Azure AD-roller, og de er vigtige for sikkerhedshandlinger (f.eks. rollen Eksempel og rollen Søg og Tøm).

Typisk skal kun et undersæt af sikkerhedsmedarbejdere have yderligere rettigheder til at hente meddelelser direkte fra brugerpostkasserne. Dette kræver en ekstra tilladelse, som Sikkerhedslæser ikke har som standard.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>Trin 2: (Valgfrit) Undtage pilotbrugere fra filtrering af din eksisterende beskyttelsestjeneste

Selvom dette trin ikke er påkrævet, bør du overveje at konfigurere dine pilotbrugere til at tilsidesætte filtrering af din eksisterende beskyttelsestjeneste. Denne handling gør Defender for Office 365 håndtere **alle filtrerings**- og beskyttelsesopgaver for pilotbrugerne. Hvis du ikke undtager dine pilotbrugere fra din eksisterende beskyttelsestjeneste, kører Defender for Office 365 faktisk kun på misses fra den anden tjeneste (filtrering af meddelelser, der allerede er blevet filtreret).

> [!NOTE]
> Dette trin er eksplicit påkrævet, hvis din aktuelle beskyttelsestjeneste leverer sammenkædning, men du vil prøvekøre Pengeskab Links-funktionalitet. Dobbeltombrydning af kæder understøttes ikke.

## <a name="step-3-tune-spoof-intelligence"></a>Trin 3: Finjuster efterlignet intelligens

Tjek [Spoof](learn-about-spoof-intelligence.md) intelligence-indsigten for at se, hvad der bliver tilladt eller blokeret som spoofing, og for at afgøre, om du har brug for at tilsidesætte systemets vurdering af spoofing. Nogle kilder til din forretningskritiske mail kan have forkert konfigurerede mailgodkendelsesposter i DNS (SPF, DKIM og DMARC), og du bruger muligvis tilsidesættelser i din eksisterende beskyttelsestjeneste til at maskere deres domæneproblemer.

Efterlignet intelligens kan hjælpe med at redde mails fra domæner uden korrekte mailgodkendelsesposter i DNS, men funktionen har nogle gange brug for hjælp til at skelne god spoofing fra dårlig spoofing. Fokuser på følgende typer meddelelseskilder:

- Meddelelseskilder, der er uden for de IP-adresseintervaller, der [er defineret i Udvidet filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).
- Meddelelseskilder, der har det højeste antal meddelelser.
- Meddelelseskilder, der har størst påvirkning på organisationen.

Efterlignet intelligens vil med tiden finjustere sig selv, når du konfigurerer brugerindsendelser, så der er ikke behov for at efterligne.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>Trin 4: Finjuster repræsentationsbeskyttelse og postkasseintelligens

Når du har haft tilstrækkelig tid til at se resultaterne af beskyttelse mod efterligning i  Anvend ikke nogen handlingstilstand, kan du individuelt slå hver repræsentationsbeskyttelseshandling til i antiphishing-politikkerne:

- Bruger efterligningsbeskyttelse: **Sæt meddelelsen i karantæne** for både Standard og Streng.
- Domænebeskyttelse: Sæt meddelelsen **i karantæne** for både Standard og Streng.
- Postkasse-intelligencebeskyttelse: **Flyt meddelelsen til modtagernes mapper med uønsket mail** for Standard; **Sæt meddelelsen i karantæne** for Strict.

Jo længere du overvåger resultaterne for repræsentationsbeskyttelse uden at reagere på meddelelserne, jo flere data skal du identificere de tillader eller blokke, der kan være nødvendige. Overvej at bruge en forsinkelse mellem aktivering af hver beskyttelse, der er betydelig nok til at muliggøre observation og justering.

> [!NOTE]
> Hyppige og kontinuerlig overvågning og justering af disse beskyttelser er vigtig. Hvis du har mistanke om en falsk positiv, skal du kun undersøge årsagen og bruge tilsidesættelser efter behov og kun for den registreringsfunktion, der kræver det.

### <a name="tune-mailbox-intelligence"></a>Finjuster postkassens intelligens

Selvom postkasseintelligens er konfigureret til ikke at gøre noget ved [meddelelser, der](impersonation-insight.md) blev bestemt til at være efterligningsforsøg, er den blevet brugt til at lære mønstret for afsendelse og modtagelse af mails for pilotbrugerne. Hvis en ekstern bruger er i kontakt med en af dine pilotbrugere, bliver meddelelser fra den pågældende eksterne bruger ikke identificeret som forsøg på efterligning af postkassens intelligens (hvilket reducerer falske positive).

Når du er klar, skal du gøre følgende for at tillade postkasseintelligens at handle på meddelelser, der registreres som forsøg på efterligning:

- I antiphishing-politikken med **standardbeskyttelsesindstillingerne** kan du ændre værdien af Hvis postkasseintelligens registrerer en efterligning af en bruger for at flytte meddelelsen til **modtagernes** mapper med Uønsket mail.

- I antiphishing-politikken med indstillingerne for Streng beskyttelse skal du ændre værdien  af Hvis postkasseintelligens registrerer og efterligner brugeren fra til **Sæt meddelelsen i karantæne**.

Hvis du vil ændre politikkerne, [skal du se Konfigurer antiphishing-politikker Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Når du har observeret resultaterne og foretaget eventuelle justeringer, skal du gå videre til næste afsnit for at sætte meddelelser, der er registreret af brugeren, i karantæne.

### <a name="tune-user-impersonation-protection"></a>Finjustere beskyttelse af bruger efterligning

I begge dine antiphishing-politikker, der er baseret på Standard og Restriktive indstillinger, skal du ændre værdien af Hvis-meddelelsen registreres som en efterligning af brugeren og sætte meddelelsen **i karantæne**.

Kontrollér [repræsentationsindsigtet for](impersonation-insight.md) at se, hvad der blokeres som forsøg på bruger efterligning.

Hvis du vil ændre politikkerne, [skal du se Konfigurer antiphishing-politikker Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Når du har observeret resultaterne og foretaget eventuelle justeringer, skal du gå videre til næste afsnit for at sætte meddelelser, der er registreret af domænepersonation, i karantæne.

### <a name="tune-domain-impersonation-protection"></a>Finjustere domæne efterligningsbeskyttelse

I begge dine antiphishing-politikker, der er baseret på standardindstillinger og strenge indstillinger, skal du ændre værdien af Hvis-meddelelsen registreres som et efterligning af domæne til Sæt **meddelelsen i karantæne**.

Kontrollér [repræsentationsindsigtet for](impersonation-insight.md) at se, hvad der blokeres som forsøg på domæne efterligning.

Hvis du vil ændre politikkerne, [skal du se Konfigurer antiphishing-politikker Defender for Office 365](configure-mdo-anti-phishing-policies.md).

Se resultaterne, og foretag eventuelle justeringer efter behov.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>Trin 5: Brug data fra brugerindsendelser til at måle og justere

Når dine pilotbrugere rapporterer falske positive og falske negativer, vises meddelelserne på siden Indsendte [Microsoft 365 Defender portalen](admin-submission.md). Du kan rapportere de misidentificerede meddelelser til Microsoft til analyse og bruge oplysningerne til at justere indstillingerne og undtagelserne i dine pilotmetoder efter behov.

Brug følgende funktioner til at overvåge og genaktivere indstillingerne for beskyttelse i Defender for Office 365:

- [Karantæne](manage-quarantined-messages-and-files.md)
- [Threat Explorer](email-security-in-microsoft-defender.md)
- [Mailsikkerhedsrapporter](view-email-security-reports.md)
- [Defender for Office 365 rapporter](view-reports-for-mdo.md)
- [Indsigt i mailflow](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Mailflowrapporter](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Hvis din organisation bruger en tredjepartstjeneste til brugerrapporter, kan du integrere disse data i din feedbackløkke.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>Trin 6: (Valgfrit) Tilføj flere brugere til dit pilotprojekt og testning

Efterhånden som du finder og løser problemer, kan du føje flere brugere til pilotgrupperne (og tilsvarende undtage disse nye pilotbrugere fra at scanne af din eksisterende beskyttelsestjeneste efter behov). Jo flere test, du skal udføre nu, jo færre brugerproblemer skal du tage dig af senere. Denne tilgang med "vandfald" giver mulighed for justering af større dele af organisationen og giver dine sikkerhedsteams tid til at tilpasse sig de nye værktøjer og processer.

- Microsoft 365 genererer beskeder, når phishing-meddelelser med høj tillid tillades af organisationens politikker. Du kan identificere disse meddelelser på følgende måde:
  - Tilsidesætter i [statusrapporten for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
  - Filtrer i Threat Explorer for at identificere meddelelserne.
  - Filtrer i Avanceret jagt for at identificere meddelelserne.

  Rapportér falske positive til Microsoft så tidligt som muligt via administratorindsendelser. Brug lejerens tilladelses [-/blokeringslistefunktion](tenant-allow-block-list.md) til at konfigurere sikre tilsidesættelser for disse falske positive.

- Det er også en god ide at undersøge unødvendige tilsidesættelser. Med andre ord skal du kigge på de Microsoft 365, du ville have givet i meddelelserne. Hvis Microsoft365 gengivede den korrekte konklusion, så bliver behovet for tilsidesættelse markant reduceret eller slettet.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>Trin 7: Udvide Microsoft 365 beskyttelse af alle brugere og deaktivere reglen for mailflow i SCL=-1

Gør trinnene i dette afsnit, når du er klar til at skifte dine MX-poster, så de peger på Microsoft 365.

1. Udvid pilotpolitikkerne til hele organisationen. Grundlæggende er der forskellige måder at gøre dette på:
   - Brug [forudindstillede](preset-security-policies.md) sikkerhedspolitikker, og inddel dine brugere mellem standardbeskyttelsesprofilen og profilen Streng beskyttelse (sørg for, at alle er dækket). Forudindstillede sikkerhedspolitikker anvendes før eventuelle brugerdefinerede politikker, du har oprettet, eller eventuelle standardpolitikker. Du kan deaktivere dine individuelle pilotpolitikker uden at slette dem.

     Ulempen ved forudindstillede sikkerhedspolitikker er, at du ikke kan ændre mange af de vigtige indstillinger, efter du har oprettet dem.

   - Rediger omfanget af de politikker, du har oprettet og justeret i løbet af pilotprojektet for at medtage alle brugere (f.eks. alle modtagere i alle domæner). Husk, at hvis flere politikker af samme type (f.eks. antiphishing-politikker) gælder for den samme bruger (individuelt efter gruppemedlemskab eller maildomæne), anvendes kun indstillingerne for politikken med højeste prioritet (laveste prioritetsnummer) og behandlingsstop for den pågældende type politik.

2. Slå reglen SCL=-1-mailflow fra (du kan deaktivere den uden at slette den).

3. Kontrollér, at de tidligere ændringer er blevet aktiveret, og at Defender for Office 365 nu er aktiveret korrekt for alle brugere. På nuværende tidspunkt har alle beskyttelsesfunktionerne i Defender for Office 365 nu tilladelse til at handle på mail for alle modtagere, men den pågældende mail er allerede blevet scannet af din eksisterende beskyttelsestjeneste.

Du kan standse midlertidigt på dette tidspunkt for at få en mere omfattende dataoptagelse og -justering.

## <a name="step-8-switch-your-mx-records"></a>Trin 8: Skift dine MX-poster

> [!NOTE]
>
> - Når du skifter MX-posten for dit domæne, kan det tage op til 48 timer, før ændringerne overføres via internettet.
>
> - Vi anbefaler, at du sænker TTL-værdien af dine DNS-poster for at aktivere hurtigere svar og mulig annullering (hvis det er nødvendigt). Du kan vende tilbage til den oprindelige TTL-værdi, når overgangen er fuldført og bekræftet.
>
> - Du bør overveje at starte med at ændre domæner, der bruges mindre ofte. Du kan sætte på pause og overvåge, før du flytter til større domæner. Men selvom du gør dette, skal du stadig sørge for, at alle brugere og domæner er dækket af politikker, fordi sekundære SMTP-domæner løses til primære domæner før politikprogrammet.
>   
> - Flere MX-poster for et enkelt domæne fungerer teknisk, så du kan have opdelt routing, hvis du har fulgt alle vejledningen i denne artikel. Specifikt skal du sørge for, at politikkerne anvendes for alle brugere, at reglen for mailflow SCL=-1 kun anvendes på mails, der går gennem din eksisterende beskyttelsestjeneste, som beskrevet i Konfigurationstrin 3: Vedligehold eller opret [mailflowreglen for SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Denne konfiguration introducerer dog en funktionsmåde, der gør fejlfinding meget mere vanskelig, og derfor anbefaler vi det typisk ikke, især i længere perioder.
>
> - Før du skifter dine MX-poster, skal du kontrollere, at følgende indstillinger ikke er aktiveret på den indgående forbindelse fra beskyttelsestjenesten til Microsoft 365. Forbindelsen har typisk konfigureret en eller flere af følgende indstillinger:
>
>   - **og kræver, at** emnenavnet på det certifikat, som partneren bruger til at godkende med Office 365 svarer til dette domænenavn (*RestrictDomainsToCertificate*)
>   - **Afvis mails, hvis de ikke sendes fra dette IP-adresseområde** (*RestrictDomainsToIPAddresses*)
>
>   Hvis forbindelsestypen er **Partner** , og en af disse indstillinger er slået til, vil al maillevering til dine domæner mislykkes, når du har skiftet dine MX-poster. Du skal deaktivere disse indstillinger, før du fortsætter. Hvis forbindelsen er en lokal forbindelse, der bruges til hybrid, behøver du ikke at ændre den lokale forbindelse. Men du kan stadig kontrollere, om der er en **Partnerforbindelse** .
>   
> - Hvis din aktuelle mailgateway også leverer modtagervalidering, kan du kontrollere, at domænet er konfigureret som [Autoritativ](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i Microsoft 365. Dette kan forhindre unødvendige meddelelser om ikke-e-mail.

Når du er klar, skal du skifte MX-posten for dine domæner. Du kan overføre alle dine domæner på én gang. Eller du kan overføre mindre hyppigt brugte domæner først og derefter overføre resten senere.

Du er velkommen til at sætte på pause og evaluere her på et hvilket som helst tidspunkt. Men husk: Når du deaktiverer reglen for mailflow i SCL=-1, kan brugere have to forskellige oplevelser til at kontrollere falske positive. Jo tidligere du kan give en enkelt, ensartet oplevelse, jo mere tilfredse dine brugere og helpdeskteams bliver, når de skal foretage fejlfinding af en manglende meddelelse.

## <a name="next-steps"></a>Næste trin

Tillykke! Du har fuldført overførslen [til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md#the-migration-process)! Da du har fulgt trinnene i denne overførselsvejledning, bør de første par dage, hvor mail leveres direkte i Microsoft 365 være meget mere jævnere.

Nu kan du begynde den normale drift og vedligeholdelse af Defender for Office 365. Overvåg og hold øje med problemer, der ligner det, du har oplevet under pilotprojektet, men på en større skala. [Efterlignet intelligensindsigt](learn-about-spoof-intelligence.md) og [repræsentationsindsigt](impersonation-insight.md) vil være mest nyttigt, men overvej at gøre følgende aktiviteter til en almindelig forekomst:

- Gennemse brugerindsendelser, især [phishingmeddelelser, der er rapporteret af brugerne](automated-investigation-response-office.md)
- Gennemse tilsidesættelser i [statusrapporten for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- Brug [avancerede jagtforespørgsler](/microsoft-365/security/defender/advanced-hunting-example) til at søge efter tilpasningsmuligheder og risikabelt meddelelser.
