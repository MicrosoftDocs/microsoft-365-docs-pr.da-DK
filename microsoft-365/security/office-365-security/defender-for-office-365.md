---
title: Microsoft Defender for Office 365 – CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- intro-overview
description: Microsoft Defender til Office 365 indeholder Pengeskab vedhæftede filer, Pengeskab links, avancerede antiphishing-værktøjer, rapporteringsværktøjer og funktioner til trusselsintelligens.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f78194541db8221aad1243966ddee6b6dc071d7d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591315"
---
# <a name="microsoft-defender-for-office-365"></a>Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til virksomhedskunder, der [har Microsoft Defender Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Hvis du bruger Outlook.com, Microsoft 365 Family eller Microsoft 365 Personal, og du leder efter oplysninger om Pengeskab Links eller Pengeskab Vedhæftede filer i Outlook, skal du se Avanceret [Outlook.com for Microsoft 365 abonnenter](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Defender til Office 365 omfatter:

- **[Politikker for trusselsbeskyttelse](#configure-microsoft-defender-for-office-365-policies)**: Definer politikker for trusselsbeskyttelse for at angive det passende beskyttelsesniveau for organisationen.

- **[Rapporter](#view-microsoft-defender-for-office-365-reports)**: Få vist rapporter i realtid for at overvåge Defender Office 365 ydeevnen i organisationen.

- **[Funktioner til trusselsundersøgelse og svar](#use-threat-investigation-and-response-capabilities)**: Brug førende værktøjer til at undersøge, forstå, simulere og forhindre trusler.

- **[Automatiserede undersøgelses- og svarmuligheder](office-365-air.md)**: Spar tid og besvær med at undersøge og mindske trusler.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Interaktiv guide til Microsoft Defender for Office 365

I denne interaktive vejledning lærer du, hvordan du beskytter din organisation med Microsoft Defender Office 365. Du kan se, hvordan Defender til Office 365 kan hjælpe dig med at definere beskyttelsespolitikker, analysere trusler til din organisation og reagere på angreb.

[Se den interaktive vejledning](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Introduktion

Hvis du er ny bruger af Microsoft Defender for Office 365, eller hvis du lærer bedst ved at gøre *det, kan* det være en fordel at bryde den indledende Defender for Office 365-konfiguration i dele, undersøge og få vist rapporter ved hjælp af denne artikel som en reference. Her er logiske dele af tidlig konfiguration:

- Konfigurer alt med "*anti*" i navnet.
  - antimalware
  - antiphishing
  - antispam
- Konfigurer alt med "*sikkert*" i navnet.
  - Sikre links
  - Pengeskab vedhæftede filer
- Forsvar arbejdsbelastningerne (f.eks. SharePoint Online, OneDrive og Teams)
- Beskyt med automatisk tømning uden time (ZAP).

Klik på dette link for at [lære ved at gøre dette](protect-against-threats.md).

> [!NOTE]
> Microsoft Defender til Office 365 fås i to forskellige Plan-typer. Du kan se, om du har **Plan 1** , hvis du har "Registreringer i realtid" og **Plan 2**, hvis du har Threat Explorer. Den Plan, du har, påvirker de værktøjer, du vil se, så du skal være sikker på, at du er opmærksom på din plan, efterhånden som du lærer.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender til Office 365 Plan 1 og Plan 2

Følgende tabel opsummerer, hvad hver plan indeholder.

****

|Defender til Office 365 Plan 1|Defender til Office 365 Plan 2|
|---|---|
|Konfigurations-, beskyttelses- og registreringsfunktioner: <ul><li>[Pengeskab vedhæftede filer](safe-attachments.md)</li><li>[Sikre links](safe-links.md)</li><li>[Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Beskyttelse mod phishing i Defender til Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Registreringer i realtid](threat-explorer.md)</li></ul>|Defender for Office 365 Plan 1-funktioner <p> --- plus --- <p> Automatisering, undersøgelse, afhjælpning og uddannelsesfunktioner: <ul><li>[Threat Trackers](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Automatiseret undersøgelse og svar](office-365-air.md)</li><li>[Kursus i angrebssimulering](attack-simulation-training.md)</li><li>[Proaktivt på jagt efter trusler med avanceret jagt på Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Undersøg hændelser i Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Undersøg beskeder i Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|


- Microsoft Defender til Office 365 Plan 2 er inkluderet i Office 365 E5, Office 365 A5 og Microsoft 365 E5.

- Microsoft Defender til Office 365 Plan 1 er inkluderet i Microsoft 365 Business Premium.

- Microsoft Defender for Office 365 Plan 1 og Defender Office 365 Plan 2 er hver især tilgængelige som et tilføjelsesprogrammet for visse abonnementer. Du kan få mere at vide ved at se her et andet link [Tilgængelighed af funktionen på tværs af Microsoft Defender Office 365-planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funktionen [Pengeskab Dokumenter](safe-docs.md) er kun tilgængelig for brugere med Microsoft 365 E5- eller Microsoft 365 E5 Sikkerhed-licenser (ikke inkluderet i Microsoft Defender til Office 365-planer).

- Hvis dit nuværende abonnement ikke omfatter Microsoft Defender til [Office 365, og](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) du vil have det, skal du kontakte salg for at starte en prøveversion og finde ud af, hvordan Microsoft Defender for Office 365 kan fungere for i din organisation.

- Microsoft Defender til Office 365 P2-kunder har **adgang til Microsoft 365 Defender integration** til effektivt at registrere, gennemse og reagere på hændelser og beskeder.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Konfigurer Microsoft Defender til Office 365 politikker

Med Microsoft Defender for Office 365 kan organisationens sikkerhedsteam konfigurere beskyttelsen ved at <https://security.microsoft.com> definere politikker på Microsoft 365 Defender-portalen på Mail **&-samarbejdspolitikker** \> **& regler** \> **for trusselspolitikker**. Eller du kan gå direkte til siden **Med Trusselspolitikker** ved hjælp af <https://security.microsoft.com/threatpolicy>.

Få mere at vide ved at [se denne video](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> Du kan finde en hurtig liste over de politikker, der skal [defineres, under Beskyt dig mod trusler](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>Defender for Office 365 politikker

De politikker, der er defineret for organisationen, bestemmer funktionsmåden og beskyttelsesniveauet for foruddefinerede trusler. Politikindstillingerne er meget fleksible. Organisationens sikkerhedsteam kan f.eks. angive en høj grad af trusselsbeskyttelse på bruger-, organisations-, modtager- og domæneniveau. Det er vigtigt regelmæssigt at gennemgå dine politikker, fordi nye trusler og udfordringer opstår dagligt.

- **[Pengeskab vedhæftede filer](safe-attachments.md)**: Giver nul dages beskyttelse for at beskytte dit meddelelsessystem ved at kontrollere vedhæftede filer i mails for skadeligt indhold. Det distribuerer alle meddelelser og vedhæftede filer, der ikke har en virus-/malwaresignatur, til et særligt miljø og bruger derefter maskinlærings- og analyseteknikker til at registrere ondsindede hensigter. Hvis der ikke findes nogen mistænkelig aktivitet, videresendes meddelelsen til postkassen. Du kan få mere at vide [under Konfigurere Pengeskab politikker for vedhæftede filer](set-up-safe-attachments-policies.md).

- **[Pengeskab Links](safe-links.md)**: Giver dig tid til klik-godkendelse af URL-adresser, f.eks. i mails og Office filer. Beskyttelse er løbende og gælder for alle dine meddelelser og Office miljø. Links scannes for hvert klik: sikre links forbliver tilgængelige, og skadelige links blokeres dynamisk. Du kan få mere at [vide under Konfigurere Pengeskab politikker for links](set-up-safe-links-policies.md).

- Pengeskab Vedhæftede filer **[til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)**: Beskytter organisationen, når brugere samarbejder og deler filer, ved at identificere og blokere skadelige filer på teamwebsteder og dokumentbiblioteker. Du kan få mere at [vide under Slå Defender til for Office 365 for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Beskyttelse mod phishing i Defender til Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**: Registrerer forsøg på at udgive sig for at være dine brugere og interne eller brugerdefinerede domæner. Den anvender maskinlæringsmodeller og avancerede algoritmer til registrering af efterligninger for at forhindre phishing-angreb. Du kan få mere at vide [under Konfigurer antiphishing-politikker i Microsoft Defender Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Få vist Microsoft Defender til Office 365 rapporter

Microsoft Defender til Office 365 indeholder [rapporter til](view-reports-for-mdo.md) at overvåge Defender for Office 365. Du kan få adgang til rapporterne iMicrosoft 365 Defender-portalen <https://security.microsoft.com>  \> på Rapporter & **mailsamarbejde** \> **& samarbejdsrapporter**. Eller du kan gå direkte til siden Mail **- og samarbejdsrapporter** ved hjælp af <https://security.microsoft.com/securityreports>.

Rapporter opdateres i realtid og giver dig de seneste indsigter. Disse rapporter indeholder også anbefalinger og giver dig besked om trusler i nær fremtid. Foruddefinerede rapporter omfatter følgende:

- [Trusselsstifinder (eller registreringer i realtid)](threat-explorer.md)
- [Statusrapport over trusselsbeskyttelse](view-reports-for-mdo.md#threat-protection-status-report)
- ... og flere.

## <a name="use-threat-investigation-and-response-capabilities"></a>Brug egenskaberne for trusselsundersøgelse og -svar

Microsoft Defender til Office 365 Plan 2 indeholder førsteklasses trusselsundersøgelse og svarværktøjer, der [](office-365-ti.md) gør det muligt for organisationens sikkerhedsteam at forudse, forstå og forhindre ondsindede angreb.

- **[Trusselssporing giver](threat-trackers.md)** den nyeste intelligens om aktuelle cybersikkerhedsproblemer. Du kan f.eks. få vist oplysninger om den nyeste malware og tage modforanstaltninger, før det bliver en egentlig trussel mod din organisation. Tilgængelige trackere [omfatter Trackers,](threat-trackers.md#noteworthy-trackers) Mest populære [trackere](threat-trackers.md#trending-trackers), [Sporede](threat-trackers.md#tracked-queries) forespørgsler [og Gemte forespørgsler](threat-trackers.md#saved-queries).

- **[Trusselsstifinder (](threat-explorer.md)** eller registreringer i realtid) (også kaldet Stifinder) er en rapport i realtid, der gør det muligt at identificere og analysere de seneste trusler. Du kan konfigurere Stifinder til at vise data for brugerdefinerede perioder.

- **[Kursus i angrebssimulering](attack-simulation-training.md)** giver dig mulighed for at køre realistiske angrebsscenarier i organisationen for at identificere sårbarheder. Der findes simuleringer af aktuelle typer angreb, herunder indsamling af phishing-oplysninger om phishing og vedhæftede filer samt adgangskoder og brute-force-adgangskodeangreb.

## <a name="save-time-with-automated-investigation-and-response"></a>Spar tid med automatisk undersøgelse og svar

(**NY!**) Når du undersøger et potentielt cyberangreb, er tiden essensen. Jo tidligere du kan identificere og afhjælpe trusler, jo bedre vil din organisation være. [Automatiserede](office-365-air.md) undersøgelses- og svarfunktioner (AIR) omfatter et sæt sikkerhedsspilebøger, der kan startes automatisk, f.eks. når der udløses en besked, eller manuelt, f.eks. fra en visning i Stifinder. AIR kan spare tid og besvær for dit sikkerhedsteam i forbindelse med at mindske trusler effektivt og effektivt. Du kan få mere at vide [under AIR i Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Tilladelser, der kræves for at bruge Microsoft Defender til Office 365 funktioner

Hvis du vil have adgang til Microsoft Defender Office 365 funktioner, skal du have tildelt en passende rolle. Følgende tabel indeholder nogle eksempler:

<br>

****

|Rolle eller rollegruppe|Ressourcer til at få mere at vide|
|---|---|
|global administrator (Organisationsadministration)|Du kan tildele denne rolle i Azure Active Directory eller i Microsoft 365 Defender portalen. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).|
|Sikkerhedsadministrator|Du kan tildele denne rolle i Azure Active Directory eller i Microsoft 365 Defender portalen. Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).|
|Organisationsadministration i Exchange Online|[Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|Søg og tøm|Denne rolle er kun tilgængelig i Microsoft 365 Defender-portalen eller Microsoft 365 Overholdelsescenter. Du kan finde flere [oplysninger i Tilladelser Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md) [og Tilladelser i Microsoft 365 Overholdelsescenter](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Få Microsoft Defender til Office 365

Microsoft Defender til Office 365 er inkluderet i visse abonnementer, f.eks. Microsoft 365 E5, Office 365 E5, Office 365 A5 og Microsoft 365 Business Premium. Hvis dit abonnement ikke omfatter Defender for Office 365, kan du købe Defender til Office 365 Plan 1 eller Defender Office 365 Plan 2 som et tilføjelsesprogrammet til visse abonnementer. Du kan få mere at vide i følgende ressourcer:

- [Microsoft Defender for Office 365 en](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) liste over abonnementer, der omfatter Defender til Office 365-planer.

- [Tilgængelighed af funktioner på tværs af Microsoft Defender Office 365 planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) for en liste over funktioner, der er inkluderet i Plan 1 og 2.

- [Få den rigtige Microsoft Defender til Office 365](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) at sammenligne planer, og køb Defender til Office 365.

- [Start en gratis prøveversion](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Nye funktioner i Microsoft Defender til Office 365

Nye funktioner føjes til Microsoft Defender til Office 365 kontinuerligt. Du kan få mere at vide i følgende ressourcer:

- [Microsoft 365 oversigt](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) indeholder en liste over nye funktioner under udvikling og udrulning.

- [Beskrivelse af Microsoft Defender Office 365-tjeneste](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) beskriver funktioner og tilgængelighed på tværs af Defender Office 365-planer.

## <a name="see-also"></a>Se også

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Automatiseret undersøgelse og svar (AIR) i Microsoft 365 Defender](../defender/m365d-autoir.md)
