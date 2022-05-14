---
title: Microsoft Defender for Office 365 - CSH
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
description: Microsoft Defender for Office 365 omfatter Pengeskab Attachments, Pengeskab Links, avancerede værktøjer til anti-phishing, rapporteringsværktøjer og funktioner til trusselsintelligens.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9be72102f9813394cb2d9eab1e4d163c6d87bd4b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417814"
---
# <a name="microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til erhvervskunder, der har [Microsoft Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Hvis du bruger Outlook.com, Microsoft 365 Family eller Microsoft 365 Personal, og du leder efter oplysninger om Pengeskab links eller Pengeskab vedhæftede filer i Outlook, skal du se [Avanceret Outlook.com sikkerhed for Microsoft 365 abonnenter](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Defender for Office 365 omfatter:

- **[Politikker til trusselsbeskyttelse](#configure-microsoft-defender-for-office-365-policies)**: Definer politikker for trusselsbeskyttelse for at angive det relevante beskyttelsesniveau for din organisation.

- **[Rapporter](#view-microsoft-defender-for-office-365-reports)**: Få vist rapporter i realtid for at overvåge Defender for Office 365 ydeevne i din organisation.

- **[Trusselsundersøgelses- og svarfunktioner](#use-threat-investigation-and-response-capabilities)**: Brug avancerede værktøjer til at undersøge, forstå, simulere og forhindre trusler.

- **[Automatiserede undersøgelses- og svarfunktioner](office-365-air.md)**: Spar tid og kræfter på at undersøge og afhjælpe trusler.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Interaktiv vejledning til Microsoft Defender for Office 365

I denne interaktive vejledning lærer du, hvordan du beskytter din organisation med Microsoft Defender for Office 365. Du kan se, hvordan Defender for Office 365 kan hjælpe dig med at definere beskyttelsespolitikker, analysere trusler mod din organisation og reagere på angreb.

[Se den interaktive vejledning](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Introduktion

Hvis du ikke kender Microsoft Defender for Office 365 eller lærer bedst ved *at gøre det*, kan det være en fordel at opdele den indledende Defender for Office 365 konfiguration i dele, undersøge og få vist rapporter ved hjælp af denne artikel som reference. Her er logiske tidlige konfigurationssegmenter:

- Konfigurer alt med "*anti*" i navnet.
  - antimalware
  - anti-phishing
  - anti-spam
- Konfigurer alt med "*sikker*" i navnet.
  - Sikre links
  - Pengeskab vedhæftede filer
- Forsvar arbejdsbelastningerne (f.eks. SharePoint Online, OneDrive og Teams)
- Beskyt med automatisk udrensning på nul timer (ZAP).

Klik [på dette link](protect-against-threats.md) for at få mere at vide ved at gøre det.

> [!NOTE]
> Microsoft Defender for Office 365 findes i to forskellige plantyper. Du kan se, om du har **Plan 1** , hvis du har 'Realtidsregistreringer' og **Plan 2**, hvis du har Threat Explorer. Den Plan, du har, påvirker de værktøjer, du vil se, så vær sikker på, at du er opmærksom på din plan, efterhånden som du lærer.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Microsoft Defender for Office 365 Plan 1 og Plan 2

I følgende tabel opsummeres det, der er inkluderet i de enkelte planer.

|Defender for Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Konfiguration, beskyttelse og registreringsfunktioner: <ul><li>[Sikre vedhæftede filer](safe-attachments.md)</li><li>[Sikre links](safe-links.md)</li><li>[Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Beskyttelse mod phishing i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Registreringer i realtid](threat-explorer.md)</li></ul>|Funktioner i Defender for Office 365 Plan 1 <p> --- plus --- <p> Automatiserings-, undersøgelses-, afhjælpnings- og uddannelsesfunktioner: <ul><li>[Trusselssporinger](threat-trackers.md)</li><li>[Trusselsoversigt](threat-explorer.md)</li><li>[Automatiseret undersøgelse og svar](office-365-air.md)</li><li>[Oplæring i angrebssimulering](attack-simulation-training.md)</li><li>[Gå proaktivt på jagt efter trusler med avanceret jagt i Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Undersøg hændelser i Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Undersøg underretninger i Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender for Office 365 Plan 2 er inkluderet i Office 365 E5, Office 365 A5 og Microsoft 365 E5.

- Microsoft Defender for Office 365 Plan 1 er inkluderet i Microsoft 365 Business Premium.

- Microsoft Defender for Office 365 Plan 1 og Defender for Office 365 Plan 2 er hver især tilgængelige som et tilføjelsesprogram til visse abonnementer. Hvis du vil have mere at vide, kan du se dette link [Funktionstilgængelighed på tværs af Microsoft Defender for Office 365-planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funktionen [Sikre dokumenter](safe-docs.md) er kun tilgængelig for brugere med Microsoft 365 E5- eller Microsoft 365 E5-sikkerhedslicenser (ikke inkluderet i Microsoft Defender for Office 365-planer).

- Hvis dit aktuelle abonnement ikke omfatter Microsoft Defender for Office 365, og du vil have det, skal du [kontakte salg for at starte en prøveversion](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) og finde ud af, hvordan Microsoft Defender for Office 365 kan fungere i din organisation.

- Microsoft Defender for Office 365 P2-kunder har adgang til **Microsoft 365 Defender-integration** til effektivt at registrere, gennemse og reagere på hændelser og beskeder. 

Se denne korte video for at få mere at vide om Microsoft Defender for Office 365 P2-funktioner, der er flyttet ind på Microsoft 365 Defender-portalen.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfx]


## <a name="configure-microsoft-defender-for-office-365-policies"></a>Konfigurer Microsoft Defender for Office 365 politikker

Med Microsoft Defender for Office 365 kan organisationens sikkerhedsteam konfigurere beskyttelse ved at definere politikker på Microsoft 365 Defender-portalen på <https://security.microsoft.com> **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker**. Du kan også gå direkte til siden **Trusselspolitikker** ved hjælp <https://security.microsoft.com/threatpolicy>af .

Få mere at vide ved at se [denne video](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> Du kan finde en hurtig liste over politikker, der skal defineres, under [Beskyt mod trusler](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>Defender for Office 365 politikker

De politikker, der er defineret for din organisation, bestemmer funktionsmåden og beskyttelsesniveauet for foruddefinerede trusler. Politikmulighederne er yderst fleksible. Organisationens sikkerhedsteam kan f.eks. angive detaljeret trusselsbeskyttelse på bruger-, organisations-, modtager- og domæneniveau. Det er vigtigt at gennemgå dine politikker regelmæssigt, fordi der dagligt opstår nye trusler og udfordringer.

- **[Pengeskab vedhæftede filer](safe-attachments.md)**: Giver nuldagsbeskyttelse til beskyttelse af dit meddelelsessystem ved at kontrollere vedhæftede filer i mails for skadeligt indhold. Den distribuerer alle meddelelser og vedhæftede filer, der ikke har en virus-/malwaresignatur, til et særligt miljø og bruger derefter teknikker til maskinel indlæring og analyse til at registrere ondsindede hensigter. Hvis der ikke blev fundet mistænkelig aktivitet, videresendes meddelelsen til postkassen. Du kan få mere at vide under [Konfigurer politikker for Pengeskab vedhæftede filer](set-up-safe-attachments-policies.md).

- **[Pengeskab Links](safe-links.md)**: Giver tid til klik-bekræftelse af URL-adresser, f.eks. i mails og Office filer. Beskyttelse foregår løbende og gælder på tværs af dine beskeder og Office miljø. Links scannes for hvert klik: Sikre links forbliver tilgængelige, og skadelige links blokeres dynamisk. Du kan få mere at vide under [Konfigurer politikker for Pengeskab links](set-up-safe-links-policies.md).

- **[Pengeskab vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)**: Beskytter din organisation, når brugerne samarbejder og deler filer, ved at identificere og blokere skadelige filer på teamwebsteder og i dokumentbiblioteker. Du kan få mere at vide under [Slå Defender for Office 365 til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Beskyttelse mod phishing i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**: Registrerer forsøg på at repræsentere dine brugere og interne eller brugerdefinerede domæner. Den anvender modeller til maskinel indlæring og avancerede algoritmer til registrering af repræsentation for at afværge phishing-angreb. Du kan få mere at vide under [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Få vist Microsoft Defender for Office 365 rapporter

Microsoft Defender for Office 365 indeholder [rapporter](view-reports-for-mdo.md) til overvågning af Defender for Office 365. Du kan få adgang til rapporterne på Microsoft 365 Defender-portalen på <https://security.microsoft.com> **Mail** \> **& samarbejde** \> **Mail & samarbejdsrapporter**. Du kan også gå direkte til siden **Mail- og samarbejdsrapporter** ved hjælp af <https://security.microsoft.com/securityreports>.

Rapporter opdateres i realtid, hvilket giver dig den nyeste indsigt. Disse rapporter indeholder også anbefalinger og advarer dig om forestående trusler. Foruddefinerede rapporter omfatter følgende:

- [Threat Explorer (eller registreringer i realtid)](threat-explorer.md)
- [Statusrapport om trusselsbeskyttelse](view-reports-for-mdo.md#threat-protection-status-report)
- ... og flere flere.

## <a name="use-threat-investigation-and-response-capabilities"></a>Brug trusselsundersøgelses- og svarfunktioner

Microsoft Defender for Office 365 Plan 2 indeholder de bedste [trusselsundersøgelses- og svarværktøjer](office-365-ti.md), der gør det muligt for din organisations sikkerhedsteam at forudse, forstå og forhindre skadelige angreb.

- **[Trusselssporing giver](threat-trackers.md)** den nyeste intelligens om gældende cybersikkerhedsproblemer. Du kan f.eks. få vist oplysninger om den nyeste malware og tage modforanstaltninger, før den bliver en faktisk trussel mod din organisation. Tilgængelige trackere omfatter [Bemærkelsesværdige trackere](threat-trackers.md#noteworthy-trackers), [Trending Trackers](threat-trackers.md#trending-trackers), [Sporede forespørgsler](threat-trackers.md#tracked-queries) og [Gemte forespørgsler](threat-trackers.md#saved-queries).

- **[Threat Explorer (eller registreringer i realtid)](threat-explorer.md)** (også kaldet Explorer) er en rapport i realtid, der giver dig mulighed for at identificere og analysere de seneste trusler. Du kan konfigurere Stifinder til at vise data for brugerdefinerede perioder.

- **[Oplæring i simulering af angreb](attack-simulation-training.md)** giver dig mulighed for at køre realistiske angrebsscenarier i din organisation for at identificere sikkerhedsrisici. Der er simuleringer af aktuelle typer angreb tilgængelige, herunder høst af phishing-legitimationsoplysninger og angreb på vedhæftede filer samt adgangskodesprøjt- og brute force-adgangskodeangreb.

## <a name="save-time-with-automated-investigation-and-response"></a>Spar tid med automatiseret undersøgelse og svar

(**NY!**) Når du undersøger et potentielt cyberangreb, er tiden af afgørende betydning. Jo hurtigere du kan identificere og afhjælpe trusler, desto bedre er det for din organisation. [Air-funktioner (Automatiseret undersøgelse og svar](office-365-air.md) ) omfatter et sæt sikkerhedslegebøger, der kan startes automatisk, f.eks. når en besked udløses, eller manuelt, f.eks. fra en visning i Stifinder. AIR kan spare dit sikkerhedsteam tid og kræfter på at afhjælpe trusler effektivt og effektivt. Du kan få mere at vide [under AIR i Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Tilladelser, der kræves for at bruge Microsoft Defender for Office 365 funktioner

Hvis du vil have adgang til Microsoft Defender for Office 365 funktioner, skal du have tildelt en relevant rolle. Følgende tabel indeholder nogle eksempler:

|Rolle eller rollegruppe|Ressourcer til at få mere at vide|
|---|---|
|global administrator (organisationsadministration)|Du kan tildele denne rolle i Azure Active Directory eller på Microsoft 365 Defender-portalen. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).|
|Sikkerhedsadministrator|Du kan tildele denne rolle i Azure Active Directory eller på Microsoft 365 Defender-portalen. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).|
|Organisationsadministration i Exchange Online|[Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|Søg og fjern|Denne rolle er kun tilgængelig på Microsoft 365 Defender-portalen eller i Microsoft Purview-compliance-portal. Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md) og [Tilladelser i Microsoft Purview-compliance-portal](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Hent Microsoft Defender for Office 365

Microsoft Defender for Office 365 er inkluderet i visse abonnementer, f.eks. Microsoft 365 E5, Office 365 E5, Office 365 A5 og Microsoft 365 Business Premium. Hvis dit abonnement ikke indeholder Defender for Office 365, kan du købe Defender for Office 365 Plan 1 eller Defender for Office 365 Plan 2 som et tilføjelsesprogram til visse abonnementer. Du kan få mere at vide i følgende ressourcer:

- [Microsoft Defender for Office 365 tilgængelighed](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) for en liste over abonnementer, der indeholder Defender for Office 365 planer.

- [Tilgængelighed af funktioner på tværs af Microsoft Defender for Office 365 planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) for en liste over funktioner, der er inkluderet i Plan 1 og 2.

- [Få de rigtige Microsoft Defender for Office 365](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) til at sammenligne planer og købe Defender for Office 365.

- [Start en gratis prøveversion](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Nye funktioner i Microsoft Defender for Office 365

Nye funktioner føjes løbende til Microsoft Defender for Office 365. Du kan få mere at vide i følgende ressourcer:

- [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) indeholder en liste over nye funktioner i udvikling og udrulning.

- [Microsoft Defender for Office 365 Tjenestebeskrivelse](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp) beskriver funktioner og tilgængelighed på tværs af Defender for Office 365 planer.

## <a name="see-also"></a>Se også

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Automatiseret undersøgelse og reaktion (AIR) i Microsoft 365 Defender](../defender/m365d-autoir.md)
