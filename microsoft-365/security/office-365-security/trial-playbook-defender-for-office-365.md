---
title: Microsoft Defender for Office 365 prøvelegebog
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: Microsoft Defender for Office 365 prøveversion af playbook til løsninger.
ms.custom: trial-playbook
ms.openlocfilehash: 6f19499a3c00fc1520d8bffb64336a789c017d28
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687740"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Playbook til prøveversion: Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Velkommen til den Microsoft Defender for Office 365 prøvetimebog! Denne playbook hjælper dig med at få mest ud af din 90-dages gratis prøveversion ved at lære dig, hvordan du beskytter din organisation med Defender for Office 365.

Nu har du mulighed for at prøve Defender for Office 365 på en af to måder:

- **Blokeringstilstand (anbefales):** Hvis din post for mailudveksling (MX) peger på Microsoft 365, kan du evaluere Defender for Office 365 funktioner i blokeringstilstand. Defender for Office 365 anvender automatisk [standardindstillingerne for forudindstillede sikkerhedspolitik](preset-security-policies.md).

  I løbet af evalueringsperioden kan du til enhver tid vælge at vælge en højere beskyttelsesskabelon (vores strenge forudindstillede sikkerhedspolitikindstillinger), eller du kan oprette dine egne individuelle beskyttelsespolitikker, der passer til dine behov.

- **Overvågningstilstand**: Hvis din MX-post peger et andet sted end til Microsoft 365 (f.eks. en mailgateway fra tredjepart), kan du evaluere Defender for Office 365 i overvågningstilstand. Defender for Office 365 blokerer ikke meddelelser, som vi finder skadelige.

  Disse trusler logføres og er tilgængelige til din gennemgang via [statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report), som giver dig detaljerede oplysninger om typerne af registrerede trusler, hvem truslerne var målrettet mod, og meget mere. Disse ekstra "fangster" angiver den ekstra beskyttelseskapacitet for Defender for Office 365 i forhold til standardfunktionerne for Exchange Online Protection (EOP) eller funktionerne i andre mailgateways fra tredjepart. Når du er tilfreds og er klar til at bruge Defender for Office 365, kan du [migrere til Defender for Office 365](migrate-to-defender-for-office-365.md).

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="En grafisk repræsentation af alle komponenter i Microsoft Defender for Office 365." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

Ved hjælp af anbefalingerne i denne vejledning lærer du, hvordan Defender for Office 365 kan hjælpe dig med at definere beskyttelsespolitikker, analysere trusler mod din organisation og reagere på angreb.

Lad os komme i gang!

## <a name="blocking-mode"></a>Blokeringstilstand

### <a name="step-1-getting-started-in-blocking-mode"></a>Trin 1: Introduktion til blokeringstilstand

#### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Start din Microsoft Defender for Office 365 prøveversion

Når du har startet prøveversionen og fuldført [konfigurationsprocessen](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-in-blocking-mode), kan det tage op til to timer, før ændringerne træder i kraft.

Vi har automatisk konfigureret [forudindstillede sikkerhedspolitikker](preset-security-policies.md) i dit miljø. Disse politikker repræsenterer en profil for grundlæggende beskyttelse, der passer til de fleste brugere. Standardbeskyttelse omfatter:

- Sikre links, sikre vedhæftede filer og anti-phishing-politikker, der er begrænset til hele lejeren eller undersættet af brugere, du har valgt under installationen af prøveversionen.
- Beskyttelse af sikre vedhæftede filer til SharePoint, OneDrive og Microsoft Teams.
- Beskyttelse af sikre links for understøttede Office 365 apps.

Se denne video for at få mere at vide: [Beskyt mod skadelige links med Sikre links i Microsoft Defender for Office 365 – YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

#### <a name="enable-users-to-report-suspicious-content-in-blocking-mode"></a>Giv brugerne mulighed for at rapportere mistænkeligt indhold i blokeringstilstand

Defender for Office 365 giver brugerne mulighed for at rapportere meddelelser til deres sikkerhedsteams og giver administratorer mulighed for at sende meddelelser til Microsoft til analyse.

- Installer tilføjelsesprogrammet [Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing](enable-the-report-message-add-in.md).
- Opret en arbejdsproces for at [rapportere falske positiver og falske negativer](report-false-positives-and-false-negatives.md).
- Brug [portalen Indsendelser](admin-submission.md).

Se denne video for at få mere at [vide: Få mere at vide om, hvordan du bruger portalen Indsendelser til at indsende meddelelser til analyse – YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-blocking-mode"></a>Gennemse rapporter for at forstå trusselslandskabet i blokeringstilstand

Brug rapporteringsfunktionerne i Defender for Office 365 for at få flere oplysninger om dit miljø.

- Forstå trusler, der modtages i mail- og samarbejdsværktøjer med [statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- Se, hvor trusler er blokeret med [statusrapporten Mailflow](view-email-security-reports.md#mailflow-status-report).
- [Gennemse links](view-reports-for-mdo.md#url-protection-report) , der blev vist af brugere eller blokeret af systemet.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="Mail & samarbejdsrapporter på Microsoft 365 Defender-portalen." lightbox="../../media/mdo-trial-playbook-reporting.png":::

### <a name="step-2-intermediate-steps-in-blocking-mode"></a>Trin 2: Mellemliggende trin i blokeringstilstand

#### <a name="prioritize-focus-on-your-most-targeted-users"></a>Prioriter fokus på dine mest målrettede brugere

Beskyt dine mest målrettede og mest synlige brugere med prioritetskontobeskyttelse i Defender for Office 365, hvilket hjælper dig med at prioritere din arbejdsproces for at sikre, at disse brugere er sikre.

- Identificer dine mest målrettede eller mest synlige brugere.
- [Markér disse brugere](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) som prioritetskonti.
- Spor trusler mod prioritetskontoen på hele portalen.

Se denne video for at få mere at vide: [Beskyttelse af prioritetskonti i Microsoft Defender for Office 365 – YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

:::image type="content" source="../../media/mdo-trial-playbook-alerts.png" alt-text="Beskederne på Microsoft 365 Defender-portalen." lightbox="../../media/mdo-trial-playbook-alerts.png":::

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Undgå dyre brud ved at forhindre, at brugeren går på kompromis

Bliv advaret om potentielle kompromiser, og begræns automatisk virkningen af disse trusler for at forhindre hackere i at få bedre adgang til dit miljø.

- Gennemse [kompromitterede brugerbeskeder](address-compromised-users-quickly.md#compromised-user-alerts).
- [Undersøg og reager på](address-compromised-users-quickly.md) kompromitterede brugere.

:::image type="content" source="../../media/mdo-trial-playbook-investigation.png" alt-text="Undersøg kompromitterede brugere." lightbox="../../media/mdo-trial-playbook-investigation.png":::

Se denne video for at få mere at vide: [Registrer og reager på kompromis i Microsoft Defender for Office 365 – YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

#### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Brug Threat Explorer til at undersøge skadelig mail

Defender for Office 365 gør det muligt for dig at undersøge aktiviteter, der sætter personer i din organisation i fare, og udføre handlinger for at beskytte din organisation. Det kan du gøre ved hjælp af [Threat Explorer](threat-explorer.md).

- [Find mistænkelige mails, der blev leveret](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): Find og slet meddelelser, identificer IP-adressen på en ondsindet mailsender, eller start en hændelse for yderligere undersøgelse.
- [Kontrollér leveringshandlingen og -placeringen](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): Denne kontrol giver dig besked om placeringen af problemmailmeddelelser.
- [Se tidslinjen for din mail](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): Du skal blot jagte dit sikkerhedsteam.

#### <a name="see-campaigns-targeting-your-organization"></a>Se kampagner, der er målrettet din organisation

Se det større billede med kampagnevisninger i Defender for Office 365, hvilket giver dig et overblik over de angrebskampagner, der er målrettet til din organisation, og den indvirkning, de har på dine brugere.

- [Identificer kampagner](campaigns.md#what-is-a-campaign) , der er målrettet til dine brugere.
- [Visualiser omfanget](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) af angrebet.
- [Spor brugerinteraktion](campaigns.md#campaign-details) med disse meddelelser.

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="Oplysningerne om kampagnen på Microsoft 365 Defender portalen." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

Se denne video for at få mere at vide: [Kampagnevisninger i Microsoft Defender for Office 365 – YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

#### <a name="use-automation-to-remediate-risks"></a>Brug automatisering til at afhjælpe risici

Reager effektivt ved hjælp af automatiseret undersøgelse og svar (AIR) for at gennemse, prioritere og reagere på trusler.

- [Få mere at vide](automated-investigation-response-office.md) om undersøgelse af strategibøger.
- [Vis detaljer og resultater](email-analysis-investigations.md) for en undersøgelse.
- Fjern trusler ved [at godkende afhjælpningshandlinger](air-remediation-actions.md).

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="Undersøgelsesresultaterne." lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

### <a name="step-3-advanced-content-in-blocking-mode"></a>Trin 3: Avanceret indhold i blokeringstilstand

#### <a name="dive-deep-into-data-with-query-based-hunting"></a>Dyk dybt ned i data med forespørgselsbaseret jagt

Brug Avanceret jagt til at skrive brugerdefinerede regler for registrering, undersøge hændelser proaktivt i dit miljø og finde trusselsindikatorer. Udforsk rådata i dit miljø.

- [Opret brugerdefinerede registreringsregler](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [Få adgang til delte forespørgsler](../defender/advanced-hunting-shared-queries.md) , der er oprettet af andre.

Se denne video for at få mere at vide: [Trusselsjagt med Microsoft 365 Defender – YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

#### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Oplær brugere til at spotte trusler ved at simulere angreb

Udrust dine brugere med den rigtige viden til at identificere trusler og rapportere mistænkelige meddelelser med oplæring i simulering af angreb i Defender for Office 365.

- [Simuler realistiske trusler](attack-simulation-training.md) for at identificere sårbare brugere.
- [Tildel oplæring](attack-simulation-training.md#assign-training) til brugere baseret på simuleringsresultater.
- [Spor status](attack-simulation-training-insights.md) for din organisation i simuleringer og oplæringsafslutning.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Oplæringsindsigt i simulering af angreb på portalen Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="auditing-mode"></a>Overvågningstilstand

### <a name="step-1-get-started-in-auditing-mode"></a>Trin 1: Kom i gang i overvågningstilstand

#### <a name="start-your-defender-for-office-365-evaluation"></a>Start din Defender for Office 365 evaluering

Når du har fuldført [konfigurationsprocessen](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-in-audit-mode), kan det tage op til to timer, før ændringerne træder i kraft. Vi har automatisk konfigureret politikker for forudindstillet evaluering i dit miljø.

Evalueringspolitikker sikrer, at der ikke udføres nogen handling på mail, der registreres af Defender for Office 365.

#### <a name="enable-users-to-report-suspicious-content-in-auditing-mode"></a>Giv brugerne mulighed for at rapportere mistænkeligt indhold i overvågningstilstand

Defender for Office 365 giver brugerne mulighed for at rapportere meddelelser til deres sikkerhedsteams og giver administratorer mulighed for at sende meddelelser til Microsoft til analyse.

- Installer tilføjelsesprogrammet [Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing](enable-the-report-message-add-in.md).
- Opret en arbejdsproces for at [rapportere falske positiver og falske negativer](report-false-positives-and-false-negatives.md).
- Brug [portalen Indsendelser](admin-submission.md).

Se denne video for at få mere at [vide: Få mere at vide om, hvordan du bruger portalen Indsendelser til at indsende meddelelser til analyse – YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-auditing-mode"></a>Gennemse rapporter for at forstå trusselslandskabet i overvågningstilstand

Brug rapporteringsfunktionerne i Defender for Office 365 for at få flere oplysninger om dit miljø.

- [Evalueringsdashboardet](try-microsoft-defender-for-office-365.md#reporting-in-audit-mode) giver et nemt overblik over de trusler, der er registreret af Defender for Office 365 under evalueringen.
- Forstå trusler, der modtages i mail- og samarbejdsværktøjer med [statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).

### <a name="step-2-intermediate-steps-in-auditing-mode"></a>Trin 2: Mellemliggende trin i overvågningstilstand

#### <a name="use-threat-explorer-to-investigate-malicious-email-in-auditing-mode"></a>Brug Threat Explorer til at undersøge skadelige mails i overvågningstilstand

Defender for Office 365 gør det muligt for dig at undersøge aktiviteter, der sætter personer i din organisation i fare, og udføre handlinger for at beskytte din organisation. Det kan du gøre ved hjælp af [Threat Explorer](threat-explorer.md).

- [Find mistænkelige mails, der blev leveret](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): Find og slet meddelelser, identificer IP-adressen på en ondsindet mailsender, eller start en hændelse for yderligere undersøgelse.
- [Kontrollér leveringshandlingen og -placeringen](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): Denne kontrol giver dig besked om placeringen af problemmailmeddelelser.
- [Se tidslinjen for din mail](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): Du skal blot jagte dit sikkerhedsteam.

#### <a name="convert-to-standard-protection-at-the-end-of-evaluation-period"></a>Konvertér til Standard Protection i slutningen af evalueringsperioden

Når du er klar til at aktivere Defender for Office 365 politikker i produktionen, kan du bruge "Konvertér til standardbeskyttelse" i evalueringsadministrationsoplevelsen for nemt at flytte til Standardbeskyttelse i [forudindstillede sikkerhedspolitikker](preset-security-policies.md).

1. Klik på **Administrer** på siden **Microsoft Defender for Office 365 evaluering** på <https://security.microsoft.com/atpEvaluation>.

   :::image type="content" source="../../media/mdo-trial-playbook-mdo-evaluation-page.png" alt-text="Klik på Administrer på siden Defender for Office 365 evaluering på portalen Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-mdo-evaluation-page.png":::

2. Klik på **Konvertér til standardbeskyttelse** i det pop op-vindue, der åbnes

   :::image type="content" source="../../media/mdo-trial-playbook-manage-flyout.png" alt-text="Klik på Konvertér til standardbeskyttelse på pop op-vinduet Administrer på siden til evaluering af Defender for Office 365." lightbox="../../media/mdo-trial-playbook-manage-flyout.png":::

3. I dialogboksen **Konvertér til standardbeskyttelse** , der åbnes, skal du klikke på **Fortsæt** for at starte installationen.

#### <a name="migrate-from-a-third-party-protection-service-or-device-to-defender-for-office-365"></a>Overfør fra en tredjepartsbeskyttelsestjeneste eller -enhed til Defender for Office 365

Hvis du allerede har en eksisterende beskyttelsestjeneste eller enhed fra tredjepart, der er placeret foran Microsoft 365, kan du overføre din beskyttelse til Microsoft Defender for Office 365 for at få fordelene ved en konsolideret administration, potentielt reducerede omkostninger (ved hjælp af produkter, du allerede betaler for) og et modent produkt med integreret sikkerhedsbeskyttelse.

Du kan få flere oplysninger under [Overfør fra en beskyttelsestjeneste eller enhed fra tredjepart til Microsoft Defender for Office 365](migrate-to-defender-for-office-365.md).

### <a name="step-3-advanced-content-in-auditing-mode"></a>Trin 3: Avanceret indhold i overvågningstilstand

#### <a name="train-users-to-spot-threats-by-simulating-attacks-in-auditing-mode"></a>Oplær brugere til at spotte trusler ved at simulere angreb i overvågningstilstand

Udrust dine brugere med den rigtige viden til at identificere trusler og rapportere mistænkelige meddelelser med oplæring i simulering af angreb i Defender for Office 365.

- [Simuler realistiske trusler](attack-simulation-training.md) for at identificere sårbare brugere.
- [Tildel oplæring](attack-simulation-training.md#assign-training) til brugere baseret på simuleringsresultater.
- [Spor status](attack-simulation-training-insights.md) for din organisation i simuleringer og oplæringsafslutning.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="Oplæringsindsigt i simulering af angreb på portalen Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>Yderligere ressourcer

- **Interaktiv vejledning**: Ukendt med Defender for Office 365? Gennemse den [interaktive vejledning](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) for at forstå, hvordan du kommer i gang.
- **Introduktion til fast track**: [Microsoft Defender for Office 365](https://go.microsoft.com/fwlink/p/?linkid=2197415)
- **Microsoft-dokumenter**: Få detaljerede oplysninger om, hvordan Defender for Office 365 fungerer, og hvordan du bedst implementerer det for din organisation. Besøg [Docs](overview.md).
- **Inkluderet**: Du kan se en komplet liste over Office 365 sikkerhedsfunktioner for mail, der er angivet efter produktniveau, i [funktionsmatrixen](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **Hvorfor Defender for Office 365**: [Dataarket Defender for Office 365](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) viser de ti vigtigste årsager til, at kunderne vælger Microsoft.
