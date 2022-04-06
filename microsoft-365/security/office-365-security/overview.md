---
title: Office 365 sikkerhed, herunder Microsoft Defender for Office 365 og Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Sikkerhed i Office 365, fra EOP til Defender for Office 365 plan 1 og 2, Standard vs. Strenge sikkerhedskonfigurationer og meget mere. Forstå, hvad du har, og hvordan du sikrer dine egenskaber.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8ddf81e038b4c055134498ee0a26751b735d786a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472171"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Microsoft Defender for Office 365 oversigt over sikkerhed

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

I denne artikel introduceres dine nye Microsoft Defender for Office 365 i skyen. Uanset om du er en del af et Security Operations Center, er du en sikkerhedsadministrator, der er ny bruger af rummet, eller du vil have en opdatering, så lad os komme i gang.

> [!CAUTION]
> Hvis du bruger **Outlook.com**, **Microsoft 365 Family** eller **Microsoft 365 Personal**, og du har brug *Pengeskab oplysninger om links* eller *Pengeskab* vedhæftede filer, skal du klikke på dette ***link***: [Avanceret Outlook.com for Microsoft 365 abonnenter](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Hvad er Defender for Office 365 sikkerhed?

Hver Office 365-abonnement leveres med sikkerhedsfunktioner. De mål og handlinger, du kan udføre, afhænger af fokus på disse forskellige abonnementer. Af Office 365 er der tre primære sikkerhedstjenester (eller produkter) knyttet til din abonnementstype:

1. Exchange Online Protection (EOP)
1. Microsoft Defender for Office 365 Plan 1 (Defender til Office P1)
1. Microsoft Defender for Office 365 Plan 2 (Defender til Office P2)

> [!NOTE]
> Hvis du har købt dit abonnement og har brug for at udrulle sikkerhedsfunktionerne lige *nu, skal* du gå til trinnene i [artiklen Beskyt mod](protect-against-threats.md) trusler. Hvis du er ny bruger af dit abonnement og gerne vil kende din licens, før du begynder, kan du gennemse Fakturering > Dine produkter i [Microsoft 365 Administration](https://admin.microsoft.com/AdminPortal/#/homepage).

Office 365 bygger på de grundlæggende beskyttelser, der tilbydes af EOP. EOP findes i alle abonnementer, hvor Exchange Online postkasser kan findes (husk, at alle de sikkerhedsprodukter, der er nævnt her, er skybaserede).

Du er måske vant til at se disse tre komponenter diskuteret på denne måde:

|EOP|Microsoft Defender for Office 365 P1|Microsoft Defender for Office 365 P2|
|---|---|---|
|Forhindrer generelle, volumenbaserede, kendte angreb.|Beskytter mails og samarbejde mod malware på nul dage, phish og virksomhedsmail.|Tilføjer undersøgelse efter brud, jagt og svar samt automatisering og simulering (til uddannelse).|

Men med hensyn til arkitektur, så lad os starte med at tænke på hvert enkelt stykke som kumulativt lag af sikkerhed, hver med fokus på sikkerhed. Mere som dette:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP og Microsoft Defender for Office 365 og deres relationer med hinanden med tjeneste som fremhævelse, herunder en note til mailgodkendelse" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Selvom hver af disse tjenester fremhæver et mål blandt Beskyt, Find, Undersøg og Svar, kan ***all** _ tjenesterne udføre _ *_any_** af målene om at beskytte, registrere, undersøge og svare på.

Det centrale i Office 365 er EOP-beskyttelse. Microsoft Defender for Office 365 P1 indeholder EOP. Defender for Office 365 P2 indeholder P1 og EOP. Strukturen er kumulativ. Derfor skal du begynde med EOP, når du konfigurerer dette produkt, og arbejde Defender for Office 365.

Selvom konfiguration af mailgodkendelse foregår i offentlig DNS, er det vigtigt at konfigurere denne funktion for at hjælpe med at beskytte dig mod spoofing. *Hvis du har EOP, skal* ***du [konfigurere mailgodkendelse](email-validation-and-authentication.md)***.

Hvis du har en Office 365 E3, eller nedenfor, har du EOP, men med mulighed for at købe enkeltstående Defender for Office 365 P1 via opgradering. Hvis du har Office 365 E5, har du allerede Defender for Office 365 P2.

> [!TIP]
> Hvis dit abonnement hverken Office 365 E3 eller E5, kan du stadig kontrollere, om du har mulighed for at opgradere til Microsoft Defender for Office 365 P1. Hvis du er [interesseret, viser](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) denne webside abonnementer, der er berettiget til Microsoft Defender for Office 365 P1-opgraderingen (se slutningen af siden for at se, om der kan udskrives).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>Sikkerhedskontrollen Office 365 EOP til Microsoft Defender for Office 365

> [!IMPORTANT]
> Få mere at vide om oplysningerne på [disse sider: Exchange Online Protection](exchange-online-protection-overview.md) og [Defender for Office 365](defender-for-office-365.md).

Hvad gør tilføjelse Microsoft Defender for Office 365-planer til en fordel i kun administration af EOP-trusler kan være svært at se ved første øjekast. For at finde ud af, om en opgraderingssti passer til din organisation, så lad os se på egenskaberne for hvert produkt, når det kommer til:

- forhindring og registrering af trusler
- undersøge
- svarer

Start med **Exchange Online Protection**:
<p>

|Prevent/Detect|Undersøg|Svar|
|---|---|---|
|Teknologier omfatter:<ul><li>spam</li><li>phish</li><li>malware</li><li>masseforsendelser</li><li>efterlignet intelligens</li><li>Registrering af efterligning</li><li>Administratorkarantæne</li><li>Administrator- og brugerindsendelser af falske positive og falske negativer</li><li>Tillad/bloker for URL-adresser og filer</li><li>Rapporter</li></ul>|<li>Søgning i overvågningslogfil</li><li>Meddelelsessporing</li>|<li>Automatisk tømning (ZAP) uden time</li><li>Forbedring og test af tilladelses- og blokeringslister</li>|

Hvis du vil gå til EOP, kan **[du gå til denne artikel](exchange-online-protection-overview.md)**.

Da disse produkter er kumulative, tilføjes disse muligheder, hvis du evaluerer eller Microsoft Defender for Office 365 P1 og beslutter at abonnere på det.

Gevinster med **Defender for Office 365, Plan 1** (til dato):
<p>

|Prevent/Detect|Undersøg|Svar|
|---|---|---|
|Teknologier omfatter alt i EOP plus:<ul><li>Pengeskab vedhæftede filer</li><li>Pengeskab links<li>Microsoft Defender for Office 365 til arbejdsbelastninger (f.eks. SharePoint Online, Teams, OneDrive for Business)</li><li>Beskyttelse med tid ved klik i mail, Office klienter og Teams</li><li>antiphishing i Defender for Office 365</li><li>Bruger- og domæne efterligningsbeskyttelse</li><li>Beskeder og SIEM-integrations-API til beskeder</li>|<li>SIEM-integrations-API til registreringer</li><li>**Værktøj til registreringer i realtid**</li><li>URL-sporing</li>|<li>Samme</li></ul>

Så Microsoft Defender for Office 365 P1 udvides på ***prevention** _-siden af hus, og tilføjer ekstra former for _*_detection_**.

Microsoft Defender for Office 365 P1 tilføjer **også registreringer i realtid** til undersøgelser. Navnet på dette trussels-jagtværktøj står med fed skrift, fordi det at have  det er klart, at du har Defender for Office 365 P1. Den vises ikke i Defender for Office 365 P2.

Gevinster med **Defender for Office 365, Plan 2** (til dato):
<p>

|Prevent/Detect|Undersøg|Svar|
|---|---|---|
|Teknologier omfatter alt i EOP og Microsoft Defender for Office 365 P1 plus:<ul><li>Samme</li>|<li>**Threat Explorer**</li><li>Threat Trackers</li><li>Kampagnevisninger</li>|<li>Automatiseret undersøgelse og svar (AIR)</li><li>AIR fra Threat Explorer</li><li>AIR til kompromitterede brugere</li><li>SIEM-integrations-API til automatiserede undersøgelser</li>

Så Microsoft Defender for Office 365 P2 udvides på undersøgelses- og svarsiden af hus og tilføjer en ny jagtstyrke. Automatisering.

I Microsoft Defender for Office 365 P2 kaldes det primære søgeværktøj **Threat Explorer** i stedet for registreringer i realtid. Hvis du får vist Trusselsstifinder, når du navigerer til Microsoft 365 Defender, er du i Microsoft Defender for Office 365 P2.

Gå til denne artikel for at Microsoft Defender for Office 365 oplysninger om P1 **[og](defender-for-office-365.md)** P2.

> [!TIP]
> EOP og Microsoft Defender for Office 365 er også anderledes, når det gælder slutbrugere. I EOP og Defender for Office 365 P1 er fokus på *opmærksomhed, og* så omfatter disse to tjenester tilføjelsesprogrammet *Rapportmeddelelse Outlook*, så brugere kan rapportere mails, de finder mistænkelige, til yderligere analyse. <p> I Defender for Office 365 P2 (som indeholder alt i EOP og P1) skiftes fokus til yderligere *kurser til slutbrugere*, så Security Operations Center har adgang til et effektivt Trussels nu-værktøj og de  målepunkter, som det giver slutbrugeren.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Microsoft Defender for Office 365 plan 1 vs. plan 2,snationsark

Denne oversigtsreference hjælper dig med at forstå, hvilke funktioner der er med til Microsoft Defender for Office 365 abonnementet. Når det kombineres med din viden om EOP-funktioner, kan det hjælpe beslutningstagere med at afgøre Microsoft Defender for Office 365 hvad der bedst opfylder deres behov.

|Defender for Office 365 plan 1|Defender for Office 365 plan 2|
|---|---|
|Konfigurations-, beskyttelses- og registreringsfunktioner: <ul><li>[Pengeskab vedhæftede filer](safe-attachments.md)</li><li>[Sikre links](safe-links.md)</li><li>[Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Beskyttelse mod phishing i Defender for Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Registreringer i realtid](threat-explorer.md)</li></ul>|Defender for Office 365 plan 1-funktioner <p> --- plus --- <p> Automatisering, undersøgelse, afhjælpning og uddannelsesfunktioner: <ul><li>[Threat Trackers](threat-trackers.md)</li><li>[Threat Explorer](threat-explorer.md)</li><li>[Automatiseret undersøgelse og svar](office-365-air.md)</li><li>[Kursus i angrebssimulering](attack-simulation-training.md)</li><li>[Proaktivt på jagt efter trusler med avanceret jagt på Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[Undersøg hændelser i Microsoft 365 Defender](../defender/investigate-incidents.md)</li><li>[Undersøg beskeder i Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Microsoft Defender for Office 365 Plan 2 er inkluderet i Office 365 E5, Office 365 A5 og Microsoft 365 E5.

- Microsoft Defender for Office 365 Plan 1 er inkluderet i Microsoft 365 Business Premium.

- Microsoft Defender for Office 365 Plan 1 og Defender for Office 365 Plan 2 er hver især tilgængelige som et tilføjelsesprogrammet for visse abonnementer. For at få mere at vide er her et andet link [Tilgængelighed af funktioner på Microsoft Defender for Office 365 planer](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Funktionen [Pengeskab Dokumenter](safe-docs.md) er kun tilgængelig for brugere med Microsoft 365 E5 eller Microsoft 365 E5 Sikkerhed (ikke inkluderet i Microsoft Defender for Office 365-planer).

- Hvis dit nuværende abonnement ikke omfatter [Microsoft Defender for Office 365, og](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) du vil have det, skal du kontakte salg for at starte en prøveversion og finde ud af, Microsoft Defender for Office 365 kan arbejde for i din organisation.

- Microsoft Defender for Office 365 P2-kunder har **adgang til Microsoft 365 Defender integration** til effektivt at registrere, gennemgå og reagere på hændelser og beskeder.

> [!TIP]
> ***Insider tip** _. Du kan bruge docs.microsoft.com til at få mere at vide om EOP og Microsoft Defender for Office 365. Gå tilbage til denne side, [Office 365 Sikkerhedsoversigt](index.yml), og du vil bemærke, at indholdsfortegnelsen er organisation i sidepanelet. Det starter med Installation (herunder overførsel) og fortsætter derefter med forebyggelse, registrering, undersøgelse og svar. <p> Denne struktur er opdelt, så *emnerne _Security Administration** efterfølges af **emner om sikkerhedshandlinger** . Hvis du er nyt medlem af en af jobrollerne, kan du bruge linket i dette tip og din viden om indholdsfortegnelsen som en hjælp til at lære mere om rummet. Husk at bruge *feedbacklinks* *og artikler med bedømme,* efterhånden som du går. Feedback hjælper os med at forbedre det, vi tilbyder dig.

## <a name="where-to-go-next"></a>Hvor skal du gå næste gang?

Hvis du er sikkerhedsadministrator, skal du muligvis konfigurere DKIM eller DMARC til din mail. Det kan være en ide at udrulle "Strenge" sikkerhedsindstillinger for dine foretrukne brugere, eller se efter nyheder i produktet. Eller hvis du bruger Security Ops, kan det være en god ide at benytte registreringer i realtid eller Threat Explorer til at undersøge og reagere eller træne registrering af slutbrugere med Attack Train. Uanset hvad, er her nogle yderligere anbefalinger til, hvad du så skal se på.

[Mailgodkendelse, herunder SPF, DKIM og DMARC (med links til konfiguration af alle tre)](email-validation-and-authentication.md)

[Se de specifikke anbefalede 'gyldne' konfigurationer, og](recommended-settings-for-eop-and-office365.md) [brug deres anbefalede forudindstillinger til hurtigt at konfigurere sikkerhedspolitikker](preset-security-policies.md)

Se [nyhederne i Microsoft Defender for Office 365 (herunder udvikling af EOP)](whats-new-in-defender-for-office-365.md)

[Brug registreringer i Trusselsstifinder eller i realtid](threat-explorer.md)

Brug kursus [i angrebssimulering](attack-simulation-training.md)
