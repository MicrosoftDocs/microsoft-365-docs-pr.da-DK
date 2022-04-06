---
title: Microsoft Defender for Office 365 prøveversion
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
description: Playbook med prøveversionen Office 365 Microsoft Defender for Office 365-løsninger.
ms.openlocfilehash: b8a0fedd01a3769f2ccf8952bd9e7bce0974a2f0
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683203"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>Prøvespilbog: Microsoft Defender til Office 365

Velkommen til playbooken Microsoft Defender for Office 365 prøveversionen. Denne spilbog hjælper dig med at få mest muligt ud af din 90 dages gratis prøveversion ved at lære dig, hvordan du beskytter din organisation med Defender Office 365. Ved hjælp af Microsoft-anbefalinger lærer du, hvordan Defender for Office 365 kan hjælpe dig med at definere beskyttelsespolitikker, analysere trusler mod din organisation og reagere på angreb.

![En grafisk gengivelse af alle komponenter i Microsoft Defender til Office 365.](../../media/mdo-trial-playbook-what-is-mdo.png)

Disse handlinger er anbefalinger fra Microsoft Defender-teamet vedrørende vigtige funktioner, du kan prøve i din 90 dages prøveversion.

## <a name="step-1-getting-started"></a>Trin 1: Introduktion

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>Start din Microsoft Defender for Office 365 prøveversion

Når du har startet prøveversionen og fuldført konfigurationen, kan det tage op til 2 timer, før ændringerne træder i kraft.

Vi har automatisk konfigureret [forudindstillede sikkerhedspolitikker](preset-security-policies.md) i dit miljø. Disse politikker repræsenterer en profil til beskyttelse af grundlinjer, der passer til de fleste brugere. Standardbeskyttelse omfatter:

- Pengeskab links, Pengeskab vedhæftede filer og antiphishing-politikker, der er tilpasset hele lejeren eller undersættet af brugere, som du kan have valgt under konfigurationen af prøveversionen.
- Beskyttelse af SharePoint, OneDrive, Office apps og Microsoft Teams.

Se denne video for at få mere at vide: [Beskyt dig mod ondsindede links Pengeskab Links i Microsoft Defender Office 365 – YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>Give brugerne mulighed for at rapportere mistænkeligt indhold

Defender for Office 365 giver brugerne mulighed for at rapportere meddelelser til deres sikkerhedsteam og giver administratorer mulighed for at sende meddelelser til Microsoft til analyse.

- Installér [tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Report Phishing](enable-the-report-message-add-in.md).
- Opret en arbejdsproces for [at rapportere falske positive og falske negativer](report-false-positives-and-false-negatives.md).
- Brug [indsendelsesportalen](admin-submission.md).

Se denne video for at få mere [at vide: Få mere at vide om, hvordan du bruger portalen til indsendelse af meddelelser til analyse – YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>Gennemse rapporter for at forstå trusselsbilledet

Brug rapporteringsfunktionerne i Defender for Office 365 at få flere oplysninger om dit miljø.

- Forstå trusler modtaget i mail- og samarbejdsværktøjer med [statusrapporten for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- Se, hvor trusler blokeres med [statusrapporten Mailflow](view-email-security-reports.md#mailflow-status-report).
- [Gennemse links](view-reports-for-mdo.md#url-protection-report) , der blev vist af brugere eller blokeret af systemet.

![Mail & rapporter om samarbejde i Microsoft 365 Defender-portalen.](../../media/mdo-trial-playbook-reporting.png)

## <a name="step-2-intermediate-steps"></a>Trin 2: Mellemliggende trin

### <a name="prioritize-focus-on-your-most-targeted-users"></a>Prioriter fokus på dine mest målrettede brugere

Beskyt dine mest målrettede og mest synlige brugere med Prioritetskontobeskyttelse i Defender Office 365, som hjælper dig med at prioritere arbejdsprocessen for at sikre, at disse brugere er sikre.

- Identificer dine mest målrettede eller mest synlige brugere.
- [Tag disse brugere som](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) prioritetskonti.
- Registrer trusler mod prioritet-konto i hele portalen.

Se denne video for at få mere at vide: [Beskyttelse af prioritetskonti i Microsoft Defender Office 365 – YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

![Beskeder i Microsoft 365 Defender portal.](../../media/mdo-trial-playbook-alerts.png)

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>Undgå dyre overtrædelser ved at forhindre brugerforlig

Bliv advaret om potentielle kompromiser og begræns automatisk effekten af disse trusler for at forhindre hackere i at få en dybere adgang til dit miljø.

- Gennemse [kompromitterede brugerbeskeder](address-compromised-users-quickly.md#compromised-user-alerts).
- [Undersøg og svar](address-compromised-users-quickly.md) på kompromitterede brugere.

![Undersøg kompromitterede brugere.](../../media/mdo-trial-playbook-investigation.png)

Se denne video for at få mere at vide: [Registrer og svar på kompromis med Microsoft Defender Office 365 – YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>Brug Threat Explorer til at undersøge skadelige mails

Defender for Office 365 giver dig mulighed for at undersøge aktiviteter, der sætter personer i din organisation i fare og kan handle for at beskytte din organisation. Du kan gøre dette ved [hjælp af Threat Explorer eller (registreringer i realtid)](threat-explorer.md).

- [Find mistænkelige mails, der blev](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered) leveret: Find og slet meddelelser, identificer IP-adressen på en ondsindet mailafsender, eller start en hændelse til yderligere undersøgelse.
- [Kontrollér leveringshandlingen og -](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location)placeringen: Denne kontrol giver dig besked om placeringen af problemmails.
- [Få vist tidslinjen for din mail](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): Du skal blot lede efter dit sikkerhedsteam.

### <a name="see-campaigns-targeting-your-organization"></a>Se kampagner, der målretter din organisation

Se det store billede med Kampagnevisninger i Defender for Office 365, som giver dig en oversigt over angrebskampagner, der er målrettet din organisation, og den påvirkning, de har på dine brugere.

- [Identificer kampagner](campaigns.md#what-is-a-campaign) , der målretter dine brugere.
- [Visualiser omfanget](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) af angrebene.
- [Spor brugerinteraktion](campaigns.md#campaign-details) med disse meddelelser.

![Kampagneoplysninger i Microsoft 365 Defender portal.](../../media/mdo-trial-playbook-campaign-details.png)

Se denne video for at få mere at vide: [Kampagnevisninger i Microsoft Defender Office 365 – YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>Brug automatisering til at afhjælpe risici

Resvar effektivt ved hjælp af automatiseret undersøgelse og svar (AIR) for at gennemse, prioritere og reagere på trusler.

- [Få mere at](automated-investigation-response-office.md) vide om undersøgelsesspilbøger.
- [Få vist detaljer og resultater](email-analysis-investigations.md) af en undersøgelse.
- Fjern trusler ved at [godkende afhjælpningshandlinger](air-remediation-actions.md).

![Undersøgelsesresultater.](../../media/mdo-trial-playbook-investigation-results.png)

## <a name="step-3-advanced-content"></a>Trin 3: Avanceret indhold

### <a name="dive-deep-into-data-with-query-based-hunting"></a>Dyk ned i data med forespørgselsbaseret jagt

Brug Avanceret på jagt efter at skrive brugerdefinerede registreringsregler, proaktivt undersøge hændelser i dit miljø og finde trusselsindikatorer. Udforsk rå data i dit miljø.

- [Opbyg brugerdefinerede registreringsregler](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [Delte forespørgsler i Access, der](../defender/advanced-hunting-shared-queries.md) er oprettet af andre.

Se denne video for at få mere at vide: [Trusselsspil med Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>Oplære brugere til at spotte trusler ved at simulerede angreb

Giv dine brugere den rigtige viden til at identificere trusler og rapportere mistænkelige meddelelser med kursus i angrebssimulering i Defender for Office 365.

- [Simulere realistiske trusler for](attack-simulation-training.md) at identificere følsomme brugere.
- [Tildel kurser](attack-simulation-training.md#assign-training) til brugere baseret på simuleringsresultater.
- [Spor din](attack-simulation-training-insights.md) organisations fremskridt i simulering og fuldførelse af kurser.

![Kursusindsigter for angrebssimulering Microsoft 365 Defender portalen.](../../media/mdo-trial-playbook-attack-simulation-training-results.png)

## <a name="additional-resources"></a>Yderligere ressourcer

- **Interaktiv guide**: Er du ikke fortrolig med Defender Office 365? Gennemse den [interaktive vejledning for at](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) forstå, hvordan du kommer i gang.
- **Microsoft-dokumenter**: Få detaljerede oplysninger om, hvordan Defender til Office 365 fungerer, og hvordan du bedst implementerer det for din organisation. Besøg [Docs](overview.md).
- **Hvad er inkluderet**: Hvis du vil se en komplet liste Office 365 alle mailsikkerhedsfunktioner, der er angivet efter produktniveau, skal du se [Funktionsmatrix](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **Hvorfor vælge Defender Office 365**: [Defender for Office 365 Dataark viser](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) de 10 vigtigste årsager til, at kunderne vælger Microsoft.
