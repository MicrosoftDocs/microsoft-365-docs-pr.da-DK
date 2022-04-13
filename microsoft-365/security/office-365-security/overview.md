---
title: Office 365 Sikkerhed, herunder Microsoft Defender for Office 365 og Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Sikkerhed i Office 365, fra EOP til Defender for Office 365 Plan 1 og 2, Standard vs. Strenge sikkerhedskonfigurationer og meget mere. Forstå, hvad du har, og hvordan du sikrer dine egenskaber.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a9f480575c712488a17dc7e9e91320edc11d0e50
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64835903"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>oversigt over sikkerhed Microsoft Defender for Office 365

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

I denne artikel introduceres du til dine nye Microsoft Defender for Office 365 sikkerhedsegenskaber i cloudmiljøet. Uanset om du er en del af Security Operations Center, er du sikkerhedsadministrator, der er ny på pladsen, eller du vil have en opdatering, så lad os komme i gang.

> [!CAUTION]
> Hvis du bruger **Outlook.com**, **Microsoft 365 Family** eller **Microsoft 365 Personal** og har brug for *Pengeskab links* eller *oplysninger om Pengeskab vedhæftede filer*, ***skal du klikke på dette link***: [Avanceret Outlook.com sikkerhed for Microsoft 365 abonnenter](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Hvad er Defender for Office 365 sikkerhed

Hvert Office 365 abonnement leveres med sikkerhedsfunktioner. De mål og handlinger, du kan tage, afhænger af fokus for disse forskellige abonnementer. I Office 365 sikkerhed er der tre primære sikkerhedstjenester (eller produkter), der er knyttet til din abonnementstype:

1. Exchange Online Protection (EOP)
1. Microsoft Defender for Office 365 Plan 1 (Defender for Office P1)
1. Microsoft Defender for Office 365 Plan 2 (Defender for Office P2)

> [!NOTE]
> Hvis du har købt dit abonnement og har brug for at udrulle sikkerhedsfunktioner *lige nu*, skal du gå til trinnene i artiklen [Beskyt mod trusler](protect-against-threats.md) . Hvis du ikke kender dit abonnement og gerne vil kende din licens, før du begynder, skal du gennemse Fakturering > Dine produkter i [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/#/homepage).

Office 365 sikkerhed bygger på de kernebeskyttelser, der tilbydes af EOP. EOP findes i et hvilket som helst abonnement, hvor Exchange Online postkasser kan findes (husk, at alle de sikkerhedsprodukter, der beskrives her, er cloudbaserede).

Du er muligvis vant til at se disse tre komponenter diskuteret på denne måde:

|EOP|Microsoft Defender for Office 365 P1|Microsoft Defender for Office 365 P2|
|---|---|---|
|Forhindrer brede, volumenbaserede kendte angreb.|Beskytter mail og samarbejde mod nuldages malware, phish og kompromis med virksomhedsmails.|Tilføjer undersøgelse efter sikkerhedsbrud, jagt og svar samt automatisering og simulering (til oplæring).|

Men med hensyn til arkitektur, lad os starte med at tænke på hvert stykke som akkumulerede lag af sikkerhed, hver med en vægt på sikkerhed. Mere i stil med dette:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP og Microsoft Defender for Office 365 og deres relationer til hinanden med fremhævelse af tjenesten, herunder en note til godkendelse via mail" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Selvom hver af disse tjenester fremhæver et mål blandt Protect, Detect, Investigate og Respond, kan ***all** _ tjenesterne udføre _ *_any_** af målene om at beskytte, registrere, undersøge og svare.

Kernen i Office 365 sikkerhed er EOP-beskyttelse. Microsoft Defender for Office 365 P1 indeholder EOP i den. Defender for Office 365 P2 indeholder P1 og EOP. Strukturen er kumulativ. Det er derfor, at når du konfigurerer dette produkt, skal du starte med EOP og arbejde på at Defender for Office 365.

Selvom konfiguration af mailgodkendelse finder sted i offentlig DNS, er det vigtigt at konfigurere denne funktion for at hjælpe med at forsvare sig mod spoofing. *Hvis du har EOP,* ***skal du [konfigurere godkendelse via mail](email-validation-and-authentication.md)***.

Hvis du har en Office 365 E3 eller nedenfor, har du EOP, men med mulighed for at købe separat Defender for Office 365 P1 via opgradering. Hvis du har Office 365 E5, har du allerede Defender for Office 365 P2.

> [!TIP]
> Hvis dit abonnement hverken er Office 365 E3 eller E5, kan du stadig kontrollere, om du har mulighed for at opgradere til Microsoft Defender for Office 365 P1. Hvis du er interesseret, viser [denne webside](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) en liste over abonnementer, der er berettiget til Microsoft Defender for Office 365 P1-opgraderingen (se slutningen af siden for at få det udskrevet med småt).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Den Office 365 sikkerhedsstige fra EOP til Microsoft Defender for Office 365

> [!IMPORTANT]
> Få mere at vide om detaljerne på disse sider: [Exchange Online Protection](exchange-online-protection-overview.md) og [Defender for Office 365](defender-for-office-365.md).

Det, der gør tilføjelse af Microsoft Defender for Office 365 planer til en fordel for ren EOP-trusselsstyring, kan være svært at se ved første øjekast. Lad os se på egenskaberne for hvert produkt, når det kommer til, for at få hjælp til at sortere efter, om en opgraderingssti passer til din organisation:

- forebyggelse og registrering af trusler
- Undersøge
- Reagerer

starter med **Exchange Online Protection**:
<p>

|Forebyg/registrer|Undersøg|Besvar|
|---|---|---|
|Teknologier omfatter:<ul><li>Spam</li><li>Phish</li><li>Malware</li><li>massepost</li><li>spoof intelligence</li><li>registrering af repræsentation</li><li>Administrator karantæne</li><li>Administrator- og brugerindsendelser af falske positiver og falske negativer</li><li>Tillad/bloker for URL-adresser og filer</li><li>Rapporter</li></ul>|<li>Søgning i overvågningslog</li><li>Meddelelsessporing</li>|<li>Automatisk udrensning på nul timer (ZAP)</li><li>Afgrænsning og test af allow- og block-lister</li>|

Hvis du vil gå i dybden med EOP, **[skal du gå til denne artikel](exchange-online-protection-overview.md)**.

Da disse produkter er kumulative, kan du tilføje disse egenskaber, hvis du evaluerer Microsoft Defender for Office 365 P1 og beslutter at abonnere på det.

Gevinster med **Defender for Office 365, Plan 1** (til dato):
<p>

|Forebyg/registrer|Undersøg|Besvar|
|---|---|---|
|Teknologier omfatter alt i EOP plus:<ul><li>Pengeskab vedhæftede filer</li><li>Pengeskab links<li>Microsoft Defender for Office 365 beskyttelse af arbejdsbelastninger (f.eks. SharePoint Online, Teams, OneDrive for Business)</li><li>Beskyttelsestid for klik i mail, Office klienter og Teams</li><li>anti-phishing i Defender for Office 365</li><li>Beskyttelse mod repræsentation af brugere og domæner</li><li>Beskeder og API til SIEM-integration for beskeder</li>|<li>SIEM-integrations-API til registreringer</li><li>**Værktøjet Registreringer i realtid**</li><li>URL-sporing</li>|<li>Samme</li></ul>

Så Microsoft Defender for Office 365 P1 udvider på ***forebyggelse** _ side af huset, og tilføjer ekstra former for _*_detection_**.

Microsoft Defender for Office 365 P1 tilføjer også **registreringer i realtid** i forbindelse med undersøgelser. Dette trussels jagtværktøjs navn er med fed, fordi det er klart middel til *at vide, at* du har Defender for Office 365 P1. Den vises ikke i Defender for Office 365 P2.

Gevinster med **Defender for Office 365, Plan 2** (til dato):
<p>

|Forebyg/registrer|Undersøg|Besvar|
|---|---|---|
|Teknologier omfatter alt i EOP og Microsoft Defender for Office 365 P1 plus:<ul><li>Samme</li>|<li>**Threat Explorer**</li><li>Trusselssporinger</li><li>Kampagnevisninger</li>|<li>Automatiseret undersøgelse og svar (AIR)</li><li>AIR fra Threat Explorer</li><li>AIR til kompromitterede brugere</li><li>SIEM Integration API til automatiserede undersøgelser</li>

Så Microsoft Defender for Office 365 P2 udvider ***undersøgelse og reaktion*** side af huset, og tilføjer en ny jagt styrke. Automatisering.

I Microsoft Defender for Office 365 P2 kaldes det primære jagtværktøj **Threat Explorer** i stedet for registreringer i realtid. Hvis du ser Threat Explorer, når du navigerer til Microsoft 365 Defender-portalen, er du i Microsoft Defender for Office 365 P2.

Hvis du vil vide mere om Microsoft Defender for Office 365 P1 og P2, skal **[du gå til denne artikel](defender-for-office-365.md)**.

> [!TIP]
> EOP og Microsoft Defender for Office 365 er også forskellige, når det gælder slutbrugere. I EOP og Defender for Office 365 P1 er fokus *opmærksomhed*, og derfor inkluderer disse to tjenester *meddelelsen Rapport Outlook tilføjelsesprogrammet*, så brugerne kan rapportere mails, de finder mistænkelige, til yderligere analyse. <p> I Defender for Office 365 P2 (som indeholder alt i EOP og P1) skifter fokus til *yderligere træning* for slutbrugere, og så Security Operations Center har adgang til et *kraftfuldt Threat Simulator-værktøj* og de slutbrugermålepunkter, det giver.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender for Office 365 Plan 1 vs. Plan 2 snydeark

Denne hurtig reference hjælper dig med at forstå, hvilke funktioner der følger med hvert Microsoft Defender for Office 365 abonnement. Når det kombineres med din viden om EOP-funktioner, kan det hjælpe virksomhedens beslutningstagere med at afgøre, hvad Microsoft Defender for Office 365 er bedst til deres behov.

|Defender for Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Konfigurations-, beskyttelses- og registreringsfunktioner: <ul><li>[Pengeskab vedhæftede filer](safe-attachments.md)</li><li>[Sikre links](safe-links.md)</li><li>[Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Beskyttelse mod phishing i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Registreringer i realtid](threat-explorer.md)</li></ul>|Defender for Office 365 Plan 1-funktioner <p> --- plus --- <p> Automatisering, undersøgelse, afhjælpning og uddannelsesfunktioner: <ul><li>[Trusselssporinger](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Automatiseret undersøgelse og svar](office-365-air.md)</li><li>[Træning i simulering af angreb](attack-simulation-training.md)</li><li>[Proaktivt jagt efter trusler med avanceret jagt i Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Undersøg hændelser i Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Undersøg beskeder i Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender for Office 365 Plan 2 er inkluderet i Office 365 E5, Office 365 A5 og Microsoft 365 E5.

- Microsoft Defender for Office 365 Plan 1 er inkluderet i Microsoft 365 Business Premium.

- Microsoft Defender for Office 365 Plan 1 og Defender for Office 365 Plan 2 er alle tilgængelige som et tilføjelsesprogram for visse abonnementer. Du kan få mere at vide ved at se et andet link [Funktionstilgængelighed på tværs af Microsoft Defender for Office 365 planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funktionen [Pengeskab dokumenter](safe-docs.md) er kun tilgængelig for brugere med Microsoft 365 E5- eller Microsoft 365 E5 Sikkerhed-licenser (ikke inkluderet i Microsoft Defender for Office 365 planer).

- Hvis dit aktuelle abonnement ikke indeholder Microsoft Defender for Office 365, og du vil have det, skal du [kontakte salg for at starte en prøveversion](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) og finde ud af, hvordan Microsoft Defender for Office 365 kan arbejde for i din organisation.

- Microsoft Defender for Office 365 P2-kunder har adgang til **Microsoft 365 Defender integration** for effektivt at registrere, gennemse og reagere på hændelser og beskeder.

> [!TIP]
> ***Insider tip** _. Du kan bruge docs.microsoft.com indholdsfortegnelse til at få mere at vide om EOP og Microsoft Defender for Office 365. Gå tilbage til denne side, [Office 365 Oversigt over sikkerhed](index.yml), hvorefter du vil bemærke denne organisering af indholdsfortegnelsen på sidepanelet. Det starter med udrulning (herunder migrering) og fortsætter derefter med forebyggelse, registrering, undersøgelse og svar. <p> Denne struktur er opdelt, så emnerne om _ *Sikkerhedsadministration** efterfølges af emner om **sikkerhedshandlinger** . Hvis du er nyt medlem af en af jobrollerne, skal du bruge linket i dette tip og din viden om indholdsfortegnelsen for at få mere at vide om området. Husk at bruge *feedbacklinks* , og *bedøm artikler* efterhånden. Feedback hjælper os med at forbedre det, vi tilbyder dig.

## <a name="where-to-go-next"></a>Hvor skal jeg gå hen næste?

Hvis du er sikkerhedsadministrator, skal du muligvis konfigurere DKIM eller DMARC til din mail. Det kan være en god idé at udrulle "Strict"-sikkerhedsindstillinger for dine prioriterede brugere, eller du kan søge efter nyheder i produktet. Eller hvis du bruger Sikkerhedsfunktioner, kan det være en god idé at bruge registreringer i realtid eller Threat Explorer til at undersøge og reagere eller oplære slutbrugerregistrering med Angrebssimulator. I begge tilfælde er her nogle yderligere anbefalinger til, hvad du skal se på næste.

[Mailgodkendelse, herunder SPF, DKIM og DMARC (med links til konfiguration af alle tre)](email-validation-and-authentication.md)

[Se de specifikke anbefalede "gyldne" konfigurationer](recommended-settings-for-eop-and-office365.md) , og [brug deres anbefalede forudindstillinger til hurtigt at konfigurere sikkerhedspolitikker](preset-security-policies.md)

Se[, hvad der er nyt i Microsoft Defender for Office 365 (herunder udviklingen af EOP)](whats-new-in-defender-for-office-365.md)

[Brug trusselsoversigt eller registreringer i realtid](threat-explorer.md)

Brug [oplæring i simulering af angreb](attack-simulation-training.md)
