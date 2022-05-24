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
description: Sikkerhed i Office 365, fra Exchange Online Protection til Defender for Office 365 Plan 1 og 2, Standard vs. Strenge sikkerhedskonfigurationer og meget mere. Forstå, hvad du har, og hvordan du sikrer dine egenskaber.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 62a8d298c9b3e47acb9ba9af5782624646487677
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: HT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647771"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Sikkerhedsoversigt for Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

I denne artikel introduceres du til dine nye sikkerhedsegenskaber for Microsoft Defender for Office 365 i skyen. Lad os komme i gang, uanset om du er en del af et Security Operations Center, du er sikkerhedsadministrator eller har brug for en opdatering.

> [!CAUTION]
> Hvis du bruger **Outlook.com**, **Microsoft 365 Family** eller **Microsoft 365 Personal** og har brug for oplysninger om *sikre links* eller *sikre vedhæftede filer*, skal du ***klikke på dette link***: [Avanceret Outlook.com-sikkerhed for Microsoft 365-abonnenter](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Hvad er Defender for Office 365-sikkerhed

Alle Office 365-abonnementer leveres med sikkerhedsfunktioner. De mål og handlinger, du kan foretage, afhænger af fokusset i disse forskellige abonnementer. I Office 365-sikkerhed er der tre primære sikkerhedstjenester (eller produkter) knyttet til din abonnementstype:

1. Exchange Online Protection (EOP)
1. Microsoft Defender for Office 365 Plan 1 (Defender for Office P1)
1. Microsoft Defender for Office 365 Plan 2 (Defender for Office P2)

> [!NOTE]
> Hvis du har købt dit abonnement og har brug for at udrulle sikkerhedsfunktioner *lige nu*, skal du gå til trinnene i artiklen [Beskyt mod trusler](protect-against-threats.md). Hvis du er ny bruger af dit abonnement og gerne vil kende din licens, før du går i gang, skal du gennemse Fakturering > Dine produkter i [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/#/homepage).

Office 365-sikkerhed bygger på de kernebeskyttelser, der tilbydes af Exchange Online Protection. Exchange Online Protection findes i alle abonnementer, hvor Exchange Online-postkasser kan findes (husk, at alle de sikkerhedsprodukter, der er nævnt her, er skybaserede).

Du er måske vant til at se disse tre komponenter diskuteret på denne måde:

|Exchange Online Protection|Microsoft Defender for Office 365 P1|Microsoft Defender for Office 365 P2|
|---|---|---|
|Forhindrer omfattende, volumenbaserede, kendte angreb.|Beskytter mail og samarbejde mod zero-day-sårbarhed. malware, phishing og virksomhedsmail-kompromittering.|Tilføjer undersøgelse efter sikkerhedsbrud, jagt og svar samt automatisering og simulering (til oplæring).|

Men hvad angår arkitektur, så lad os starte med at tænke på hver enkelt del som akkumulerede sikkerhedslag, hver især med en sikkerhedsfokusering. Mere som dette:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="Exchange Online Protection og Microsoft Defender for Office 365 og deres relationer til hinanden med tjenestefokus, herunder en bemærkning til mailgodkendelse" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Selvom hver af disse tjenester fremhæver et mål blandt Beskyt, Registrer, Undersøg og Reager, ***alle** _ tjenesterne kan udføre _ *_alle_** for at beskytte, registrere, undersøge og reagere.

Kernen i Office 365-sikkerhed er Exchange Online Protection-beskyttelse. Microsoft Defender for Office 365 P1 indeholder Exchange Online Protection. Defender for Office 365 P2 indeholder P1 og Exchange Online Protection. Strukturen er kumulativ. Det er derfor, at når du konfigurerer dette produkt, skal du starte med Exchange Online Protection og arbejde mod Defender for Office 365.

Selvom konfiguration af mailgodkendelse finder sted i offentlig DNS, er det vigtigt at konfigurere denne funktion for at hjælpe med at beskytte mod forfalskning. *Hvis du har EOP,* ***bør du [konfigurere mailgodkendelse](email-validation-and-authentication.md)***.

Hvis du har en Office 365 E3 eller derunder, har du EOP, men med mulighed for at købe enkeltstående Defender for Office 365 P1 via opgradering. Hvis du har Office 365 E5, har du allerede Defender for Office 365 P2.

> [!TIP]
> Hvis dit abonnement hverken er Office 365 E3 eller E5, kan du stadig kontrollere, om du har mulighed for at opgradere til Microsoft Defender for Office 365 P1. Hvis du er interesseret, viser [denne webside](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) en liste over abonnementer, der er berettiget til Microsoft Defender for Office 365 P1-opgraderingen (se slutningen af siden for at se det med småt).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Office 365-sikkerhedsstigen fra Exchange Online Protection til Microsoft Defender for Office 365

> [!IMPORTANT]
> Få mere at vide om disse sider: [Exchange Online Protection](exchange-online-protection-overview.md) og [Defender for Office 365](defender-for-office-365.md).

Det, der gør tilføjelse af Microsoft Defender for Office 365-planer til en fordel for ren EOP-trusselsadministration, kan være svært at se ved første øjekast. Lad os se på egenskaberne for hvert produkt for at finde ud af, om en opgraderingssti passer til din organisation, når det drejer sig om:

- forebyggelse og registrering af trusler
- undersøgning
- reaktion

starter med **Exchange Online Protection-**:
<p>

|Forebyg/registrer|Undersøg|Besvar|
|---|---|---|
|Teknologier omfatter:<ul><li>spam</li><li>phishing</li><li>malware</li><li>masseforsendelser</li><li>efterretninger om forfalskning</li><li>registrering af efterligning</li><li>Administratorkarantæne</li><li>Administrator- og brugerindsendelser af falske positiver og falske negativer</li><li>Tillad/bloker for URL-adresser og filer</li><li>Rapporter</li></ul>|<li>Søgning i overvågningslog</li><li>Meddelelsessporing</li>|<li>Omgående automatisk flytning (ZAP)</li><li>Indsnævring og test af lister over tilladte og blokerede</li>|

Hvis du vil gå i dybden med Exchange Online Protection, kan du **[gå til denne artikel](exchange-online-protection-overview.md)**.

Da disse produkter er kumulative, skal du tilføje disse funktioner, hvis du evaluerer Microsoft Defender for Office 365 P1 og beslutter dig for at abonnere på det.

Forbedringer af **Defender for Office 365, Plan 1** (til dato):
<p>

|Forebyg/registrer|Undersøg|Besvar|
|---|---|---|
|Teknologier omfatter alt i Exchange Online Protection plus:<ul><li>Sikre vedhæftede filer</li><li>Sikre links<li>Microsoft Defender for Office 365-beskyttelse til arbejdsbelastninger (f.eks. SharePoint Online, Teams OneDrive for Business)</li><li>Beskyttelse ved klik i mail, Office-klienter og Teams</li><li>antiphishing i Defender for Office 365</li><li>Beskyttelse mod efterligning af bruger og domæne</li><li>Underretninger og SIEM-integrations-API til underretninger</li>|<li>SIEM-integrations-API til registreringer</li><li>**Værktøj til registrering i realtid**</li><li>URL-sporing</li>|<li>Samme</li></ul>

Så Microsoft Defender for Office 365 P1 udvider på ***forebyggelsessiden** _ af huset og tilføjer ekstra former for _*_registrering_**.

Microsoft Defender for Office 365 P1 tilføjer også **registreringer i realtid** til undersøgelser. Navnet på dette værktøj til trusselsjagt er med fed skrift, fordi det er en tydelig måde at *vide,* du har Defender for Office 365 P1. Den vises ikke i Defender for Office 365 P2.

Forbedringer af **Defender for Office 365, Plan 2** (til dato):
<p>

|Forebyg/registrer|Undersøg|Besvar|
|---|---|---|
|Teknologier omfatter alt i Exchange Online Protection og Microsoft Defender for Office 365 P1 plus:<ul><li>Samme</li>|<li>**Trusselsoversigt**</li><li>Trusselssporinger</li><li>Kampagnevisninger</li>|<li>Automatiseret undersøgelse og svar (AIR)</li><li>AIR fra Trusselsoversigt</li><li>AIR til kompromitterede brugere</li><li>SIEM-integrations-API til automatiserede undersøgelser</li>

Så Microsoft Defender til Office 365 P2 udvider ***undersøgelses- og svarsiden*** af huset og tilføjer en ny jagtstyrke. Automatisering.

I Microsoft Defender for Office 365 P2 kaldes det primære jagtværktøj **Trusselsoversigt** i stedet for Registreringer i realtid. Hvis du ser Trusselsoversigt, når du navigerer til Microsoft 365 Defender-portalen, er du i Microsoft Defender for Office 365 P2.

Du kan få mere at vide om Microsoft Defender for Office 365 P1 og P2 ved at **[gå til denne artikel](defender-for-office-365.md)**.

> [!TIP]
> EOP og Microsoft Defender til Office 365 er også forskellige, når det kommer til slutbrugere. I Exchange Online Protection og Defender for Office 365 P1 er fokus *opmærksomhed*, og derfor omfatter disse to tjenester Outlook-tilføjelsesprogrammet *Rapportér meddelelse* så brugerne kan rapportere mails, de finder mistænkelige, til yderligere analyse.<p> I Defender for Office 365 P2 (som indeholder alt i Exchange Online Protection og P1) skifter fokus til *yderligere træning* til slutbrugere, så Security Operations Center har adgang til et effektivt *Threat Simulator* -værktøj og de målepunkter, som slutbrugerne får.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Oversigtsark til Microsoft Defender for Office 365 Plan 1 vs. Plan 2

Denne hurtige reference hjælper dig med at forstå, hvilke funktioner der følger med hvert Microsoft Defender for Office 365-abonnement. Når det kombineres med din viden om Exchange Online Protection-funktioner, kan det hjælpe beslutningstagere i virksomheden med at afgøre, hvilken Microsoft Defender for Office 365 er bedst til deres behov.

|Defender for Office 365 Plan 1|Defender for Office 365 Plan 2|
|---|---|
|Konfiguration, beskyttelse og registreringsfunktioner: <ul><li>[Sikre vedhæftede filer](safe-attachments.md)</li><li>[Sikre links](safe-links.md)</li><li>[Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Beskyttelse mod phishing i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Registreringer i realtid](threat-explorer.md)</li></ul>|Funktioner i Defender for Office 365 Plan 1 <p> --- plus --- <p> Automatiserings-, undersøgelses-, afhjælpnings- og uddannelsesfunktioner: <ul><li>[Trusselssporinger](threat-trackers.md)</li><li>[Trusselsoversigt](threat-explorer.md)</li><li>[Automatiseret undersøgelse og svar](office-365-air.md)</li><li>[Oplæring i angrebssimulering](attack-simulation-training.md)</li><li>[Gå proaktivt på jagt efter trusler med avanceret jagt i Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Undersøg hændelser i Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Undersøg underretninger i Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender for Office 365 Plan 2 er inkluderet i Office 365 E5, Office 365 A5 og Microsoft 365 E5.

- Microsoft Defender for Office 365 Plan 1 er inkluderet i Microsoft 365 Business Premium.

- Microsoft Defender for Office 365 Plan 1 og Defender for Office 365 Plan 2 er hver især tilgængelige som et tilføjelsesprogram til visse abonnementer. Hvis du vil have mere at vide, kan du se dette link [Funktionstilgængelighed på tværs af Microsoft Defender for Office 365-planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funktionen [Sikre dokumenter](safe-docs.md) er kun tilgængelig for brugere med Microsoft 365 E5- eller Microsoft 365 E5-sikkerhedslicenser (ikke inkluderet i Microsoft Defender for Office 365-planer).

- Hvis dit aktuelle abonnement ikke omfatter Microsoft Defender for Office 365, og du vil have det, skal du [kontakte salg for at starte en prøveversion](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) og finde ud af, hvordan Microsoft Defender for Office 365 kan fungere i din organisation.

- Microsoft Defender for Office 365 P2-kunder har adgang til **Microsoft 365 Defender-integration** til effektivt at registrere, gennemse og reagere på hændelser og beskeder.

> [!TIP]
> ***Insider-tip** _. Du kan bruge docs.microsoft.com-indholdsfortegnelsen til at få mere at vide om EOP og Microsoft Defender for Office 365. Gå tilbage til denne side, [Office 365-sikkerhedsoversigt](index.yml), og du vil se indholdsfortegnelsen i sidebjælken. Den starter med Udrulning (herunder migrering) og fortsætter derefter til forebyggelse, registrering, undersøgelse og svar. <p> Denne struktur er opdelt, så _ *Sikkerhedsadministration**-emner efterfølges af **Sikkerhedsdrift**-emner. Hvis du er et nyt medlem af en af jobrollerne, kan du bruge linket i dette tip og din viden om indholdsfortegnelsen til at få mere at vide om området. Husk at bruge *feedbacklinks* og *bedømme artikler* undervejs. Feedback hjælper os med at forbedre det, vi tilbyder dig.

## <a name="where-to-go-next"></a>Hvor du skal hen nu

Hvis du er sikkerhedsadministrator, skal du muligvis konfigurere DKIM eller DMARC til din mail. Det kan være en god ide at udrulle "Strenge" sikkerhedsindstillinger for dine prioritetsbrugere eller se efter nyheder i produktet. Eller hvis du bruger Security Ops, kan det være en god ide at bruge registreringer i realtid eller Trusselsoversigt til at undersøge og svare eller oplære slutbrugerregistrering med Angrebssimulator. Uanset hvad, er her nogle flere anbefalinger til, hvad du skal se på som det næste.

[Mailgodkendelse, herunder SPF, DKIM og DMARC (med links til konfiguration af alle tre)](email-validation-and-authentication.md)

[Se de specifikke anbefalede "gyldne" konfigurationer](recommended-settings-for-eop-and-office365.md), og [brug deres anbefalede forudindstillinger til hurtigt at konfigurere sikkerhedspolitikker](preset-security-policies.md)

Få mere at vide om [nyheder i Microsoft Defender for Office 365 (herunder udviklinger i Exchange Online Protection)](whats-new-in-defender-for-office-365.md)

[Brug Trusselsoversigt eller Registreringer i realtid](threat-explorer.md)

Brug [oplæring i Attack-simulering](attack-simulation-training.md)
