---
title: Få vist mailsikkerhedsrapporter
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 3a137e28-1174-42d5-99af-f18868b43e86
ms.collection:
- M365-security-compliance
description: Administratorer kan lære, hvordan de kan finde og bruge de mailsikkerhedsrapporter, der er tilgængelige i Microsoft 365 Defender-portalen.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b6d085d2e3c1e9c1e032f468f56d67a393269fe1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683049"
---
# <a name="view-email-security-reports-in-the-microsoft-365-defender-portal"></a>Få vist mailsikkerhedsrapporter Microsoft 365 Defender portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Der findes en række rapporter på Microsoft 365 Defender-portalen, som kan hjælpe dig med at <https://security.microsoft.com> se, hvordan mailsikkerhedsfunktioner som f.eks. antispam- og antimalwarefunktioner i Microsoft 365 beskytter din organisation. Hvis du har de [nødvendige tilladelser](#what-permissions-are-needed-to-view-these-reports), kan du få vist og hente disse rapporter som beskrevet i denne artikel.

> [!NOTE]
>
> Nogle af rapporterne på siden Rapporter **om & mailsamarbejde kræver** Microsoft Defender Office 365. Du kan finde oplysninger om disse rapporter [i View Defender for Office 365 rapporter i Microsoft 365 Defender portal](view-reports-for-mdo.md).
>
> Rapporter, der er relateret til mailflow, findes nu i Exchange Administration. Du kan finde flere oplysninger om disse rapporter [under Mailflowrapporter i den Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="email-security-report-changes-in-the-microsoft-365-defender-portal"></a>Ændringer i mailsikkerhedsrapporten Microsoft 365 Defender portalen

Rapporterne Exchange Online Protection (EOP) og Microsoft Defender til Office 365 i Microsoft 365 Defender-portalen, der er blevet erstattet, flyttet eller frarådet, er beskrevet i følgende tabel.

|Forældet rapport og cmdlet'er|Ny rapport og cmdlet'er|Meddelelsescenter-id|Dato|
|---|---|:---:|:---:|
|**URL-sporing** <p> Get-URLTrace|[Rapport over beskyttelse af URL-adresser](view-reports-for-mdo.md#url-protection-report) <p> [Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <br> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|MC239999|Juni 2021|
|**Rapport over sendte og modtagne mails** <p> Get-MailTrafficReport <br> Get-MailDetailReport|[Statusrapport over trusselsbeskyttelse](#threat-protection-status-report) <br> [Statusrapport for mailflow](#mailflow-status-report) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <br> [Get-MailFlowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|MC236025|Juni 2021|
|**Rapport for videresendelse** <p> ingen cmdlet'er|[Rapporten om automatisk videresendte meddelelser i EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) <p> ingen cmdlet'er|MC250533|Juni 2021|
|**Pengeskab rapport over vedhæftede filer** <p> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Statusrapport for trusselsbeskyttelse: Vis data efter mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250532|Juni 2021|
|**Pengeskab rapport over fordeling af vedhæftede filer** <p> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Statusrapport for trusselsbeskyttelse: Vis data efter mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250531|Juni 2021|
|**Malware registreret i mailrapport** <p> Get-MailTrafficReport <br> Get-MailDetailMalwareReport|[Statusrapport for trusselsbeskyttelse: Vis data efter mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250530|Juni 2021|
|**Rapport over registrering af spam** <p> Get-MailTrafficReport <br> Get-MailDetailSpamReport|[Statusrapport over trusselsbeskyttelse: Få vist data efter mailspam \>](#view-data-by-email--spam-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250529|Oktober 2021|
|Get-AdvancedThreatProtectionDocumentReport <p> Get-AdvancedThreatProtectionDocumentDetail|[Get-ContentMalwareMdoAggregateReport](/powershell/module/exchange/get-contentmalwaremdoaggregatereport) <p> [Get-ContentMalwareMdoDetailReport](/powershell/module/exchange/get-contentmalwaremdodetailreport)|TBA|Maj 2022|
|**Exchange transportregelrapport** <p> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailMailRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|[Exchange transportregelrapport i EAC](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report) <p> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailMailRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|MC316157|April 2022|
|Get-MailTrafficTopReport|[Statusrapport for trusselsbeskyttelse: Vis data efter mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <p> **Bemærk**! Der findes ingen erstatning for krypterings rapporteringsfunktionerne i Get-MailTrafficTopReport.|MC315742|April 2022|

## <a name="compromised-users-report"></a>Rapport over kompromitterede brugere

> [!NOTE]
> Denne rapport er tilgængelig i Microsoft 365 med Exchange Online postkasser. Det er ikke tilgængeligt i enkeltstående Exchange Online Protection (EOP)-organisationer.

Rapporten **Kompromitterede brugere** viser antallet af brugerkonti, der er markeret som **mistænkelige** eller **begrænsede inden** for de seneste 7 dage. Konti i en af disse tilstande er problematiske eller endda kompromitterede. Med hyppig brug kan du bruge rapporten til at få øje på samlingerne, og endda tendenser, på mistænkelige eller begrænsede konti. Du kan finde flere oplysninger om kompromitterede brugere under [Svare på en kompromitteret mailkonto](responding-to-a-compromised-email-account.md).

![Widget for kompromitterede brugere på siden & med samarbejdsrapporter.](../../media/compromised-users-report-widget.png)

Den aggregerede visning viser data for de seneste 90 dage, og detaljevisningen viser data for de seneste 30 dage.

Hvis du vil have vist rapporten i Microsoft 365 Defender på <https://security.microsoft.com>,  \> skal du gå til **Rapporter & mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & skal du** finde **Kompromitterede brugere og** derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/CompromisedUsers>.

På siden **Kompromitterede brugere** viser diagrammet følgende oplysninger for det angivne datointerval:

- **Begrænset**: Brugerkontoen er blevet begrænset i at kunne sende mail på grund af meget mistænkelige mønstre.
- **Mistænkelig**: Brugerkontoen har sendt mistænkelige mails og er i risiko for at blive begrænset i at kunne sende mails.

Detaljetabellen under grafen viser følgende oplysninger:

- **Oprettelsestid**
- **Bruger-id**
- **Handling**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)**: **Startdato** **og slutdato**.
- **Aktivitet**: **Begrænset eller** **mistænkelig**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Kompromitterede brugere** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

![Rapportvisning i rapporten Kompromitterede brugere.](../../media/compromised-users-report-activity-view.png)

## <a name="exchange-transport-rule-report"></a>Exchange transportregelrapport

> [!NOTE]
> Rapporten **Exchange transportregel er** nu tilgængelig i EAC. Du kan finde flere oplysninger [Exchange rapport over transportregel i den nye EAC](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

### <a name="chart-breakdown-by-direction"></a>Diagramopdeling efter retning

![Visning af retning for Exchange transportregler i Exchange transportregel.](../../media/transport-rule-report-etr-direction-view.png)

Hvis du vælger **Diagramopdeling efter Retning**, er følgende diagrammer tilgængelige:

- **Få vist data Exchange transportregler**: Antallet af **indgående** og **udgående** meddelelser, der blev påvirket af regler for mailflow.
- **Få vist data efter DLP Exchange-transportregler**: Antallet af **indgående** og udgående meddelelser, der blev påvirket af regler for forebyggelse af datatab (DLP).

Følgende oplysninger er vist i detaljetabellen under grafen:

- **Dato**
- **DLP-politik** (**Vis data efter DLP Exchange transportregler kun**)
- **Transportregel**
- **Emne**
- **Afsenderadresse**
- **Modtageradresse**
- **Alvorsgrad**
- **Retning**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)** **Startdato** og **Slutdato**.
- **Retning**: **Udgående** og **Indgående**.
- **Alvorsgrad**: **Høj alvorsgrad**, **Mellem alvorlighed** **og Lav alvorsgrad**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Exchange transportregel skal** du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="chart-breakdown-by-severity"></a>Diagramopdeling efter alvorsgrad

![Visning af alvorsgrad for Exchange for transportregler i Exchange for transportregel.](../../media/transport-rule-report-etr-severity-view.png)

Hvis du vælger **Diagramopdeling efter alvorsgrad**, er følgende diagrammer tilgængelige:

- **Få vist data Exchange brug af transportregler**: Antallet af meddelelser med høj alvorsgrad **, Mellem** alvorlighed **og Lav alvorsgrad**. Du angiver alvorsniveauet som en handling i reglen **(** Oversæt denne regel med _alvorsniveau eller AngivAuditSeverity_). Du kan finde flere oplysninger [i Handlinger for mailflowregel Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions).

- **Få vist data efter DLP Exchange-transportregler**: Antallet af meddelelser med høj alvorsgrad **, Mellem** alvorlighed og Lav  alvorsgrad **, der** blev påvirket af DLP-mailflowregler.

Følgende oplysninger er vist i detaljetabellen under grafen:

- **Dato**
- **DLP-politik** (**Vis data efter DLP Exchange transportregler kun**)
- **Transportregel**
- **Emne**
- **Afsenderadresse**
- **Modtageradresse**
- **Alvorsgrad**
- **Retning**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Retning**: **Udgående** og **indgående**
- **Alvorsgrad**: **Høj alvorsgrad**, **Mellem alvorlighed** **og Lav alvorsgrad**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Exchange transportregel skal** du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

## <a name="forwarding-report"></a>Rapport for videresendelse

> [!NOTE]
> Denne rapport er nu tilgængelig i EAC. Du kan finde flere oplysninger [i Rapporten om automatisk videresendte meddelelser i det nye EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Statusrapport for mailflow

**Statusrapporten For mailflow** er en smart rapport, der viser oplysninger om indgående og udgående mail, spamregistreringer, malware, mails, der er identificeret som "godt" og oplysninger om mails, der er tilladte eller blokeret i kanten. Dette er den eneste rapport, der indeholder oplysninger om edge protection og viser, hvor meget mail der blokeres, før de bliver tilladt i tjenesten til evaluering af Exchange Online Protection (EOP). Det er vigtigt at forstå, at hvis en meddelelse sendes til fem modtagere, tæller vi den som fem forskellige meddelelser og ikke én meddelelse.

Hvis du vil have vist rapporten i Microsoft 365 Defender på <https://security.microsoft.com>,  \> skal du gå til **Rapporter & mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & skal du** finde **Statusoversigt for mailflow og** derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/mailflowStatusReport>.

![Widget med statusoversigt for mailflow på siden & med samarbejdsrapporter.](../../media/mail-flow-status-report-widget.png)

### <a name="type-view-for-the-mailflow-status-report"></a>Skrive visning for statusrapporten for mailflow

![Skriv visning i statusrapporten for mailflow.](../../media/mail-flow-status-report-type-view.png)

På siden **Statusrapport for mailflow** er **fanen Type** valgt som standard. Diagrammet viser følgende oplysninger for det angivne datointerval:

- **God mail**: Mail, der vurderes ikke at være spam, eller som tillades af bruger- eller organisationspolitikker.
- **I alt**
- **Malware**: Mails, der blokeres som malware af forskellige filtre.
- **Phishingmail**: Mails, der blokeres som phishing af forskellige filtre.
- **Spam**: Mails, der blokeres som spam af forskellige filtre.
- **Edge-beskyttelse**: Mail, der er afvist i kanten/perimeteren, før den evalueres af EOP eller Defender for Office 365.
- **Regelmeddelelser**: Mails, der blev reageret på af regler for mailflow (også kaldet transportregler).

Detaljetabellen under grafen viser følgende oplysninger:

- **Retning**
- **Type**
- **24 timer**
- **3 dage**
- **7 dage**
- **15 dage**
- **30 dage**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)**: **Startdato** **og slutdato**.
- **Mailretning**: **Indgående** og **udgående**.
- **Skriv**:
  - **God mail**
  - **Malware**
  - **Spam**
  - **Edge-beskyttelse**
  - **Regelmeddelelser**
  - **Phishing-mail**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Tilbage på siden **Statusrapport for mailflow** kan du, hvis du klikker på Vælg en kategori **for** at få flere oplysninger, vælge mellem følgende værdier:

- **Phishing-mail**: Dette fører dig til [statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Malware i mail**: Dette fører dig til [statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Registrering af spam**: Dette fører dig til rapporten [Registrering af spam](view-email-security-reports.md#spam-detections-report).
- **Edge-blokeret spam**: Dette valg fører dig til [rapporten Spamregistreringer](view-email-security-reports.md#spam-detections-report).

På siden **Statusrapport for mailflow** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Ikonet Opret tidsplan](#schedule-report)** og ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="direction-view-for-the-mailflow-status-report"></a>Visning af retning for statusrapporten For mailflow

![Visning af retning i statusrapporten For mailflow.](../../media/mail-flow-status-report-direction-view.png)

Hvis du klikker på **fanen** Retning, viser diagrammet følgende oplysninger for det angivne datointerval:

- **Indgående**
- **Udgående**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)**: **Startdato** **og slutdato**.
- **Mailretning**: **Indgående** og **udgående**.
- **Skriv**:
  - **God mail**
  - **Malware**
  - **Spam**
  - **Edge-beskyttelse**
  - **Regelmeddelelser**
  - **Phishing-mail**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Tilbage på siden **Statusrapport for mailflow** kan du, hvis du klikker på Vælg en kategori **for** at få flere oplysninger, vælge mellem følgende værdier:

- **Phishing-mail**: Dette fører dig til [statusrapporten Trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Malware i mail**: Dette fører dig til [statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Registrering af spam**: Dette fører dig til rapporten [Registrering af spam](view-email-security-reports.md#spam-detections-report).
- **Edge-blokeret spam**: Dette valg fører dig til [rapporten Spamregistreringer](view-email-security-reports.md#spam-detections-report).

På siden **Statusrapport for mailflow** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **Ikonet Opret tidsplan** og ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knapperne** Eksportér er tilgængelige.

### <a name="mailflow-view-for-the-mailflow-status-report"></a>Mailflowvisning for statusrapporten For mailflow

Visningen **Mailflow viser** , hvordan Microsofts funktioner til trusselsbeskyttelse af mail filtrerer indgående og udgående mail i organisationen. Denne visning bruger et vandret rutediagram (kendt som et _Sankey-diagram_ ) til at angive oplysninger om det samlede antal mails, og hvordan de konfigurerede funktioner til trusselsbeskyttelse, herunder edge protection, antimalware, antiphishing, antispam og antispoofing, påvirker dette antal.

![Mailflowvisning i statusrapporten Mailflow.](../../media/mail-flow-status-report-mailflow-view.png)

Med den aggregerede visning og detaljetabelvisningen kan der filtreres i 90 dage.

Oplysningerne i diagrammet er farvekodede af **EOP** eller **Defender til Office 365** teknologier.

Diagrammet er organiseret i følgende vandrette bånd:

- **Samlet mailbånd** : Denne værdi vises altid først.
- **Edge-blok** **og Behandlet** bånd:
  - **Edge-blok**: Meddelelser, der filtreres ved kanten og identificeres som Edge Protection.
  - **Behandlet**: Meddelelser, der håndteres af filtreringsstakken.
- Resultatbånd:
  - **Regelblok**: Meddelelser, der behandles af Exchange regler for mailflow (transportregler).
  - **Malwareblokering**: Meddelelser, der identificeres som malware af forskellige filtre.<sup>\*</sup>
  - **Phish-blok**: Meddelelser, der er identificeret som phish under behandling af forskellige filtre.<sup>\*</sup>
  - **Spamblokering**: Meddelelser, der identificeres som spam under behandling af forskellige filtre.<sup>\*</sup>
  - **Impersonation block**: Messages detected as user impersonation or domain impersonation in Defender for Office 365.<sup>\*</sup>
  - **Detonation-blok**: Meddelelser, der registreres under fil- eller URL-detonation ved Pengeskab politikker for vedhæftede filer eller Pengeskab Links-politikker i Defender Office 365.<sup>\*</sup>
  - **ZAP er** fjernet: Meddelelser, der fjernes med automatisk tømning i nul timer (ZAP).<sup>\*</sup>
  - **Leveret**: Meddelelser leveret til brugere på grund af en tilladelse.<sup>\*</sup>

Hvis du peger på et vandret bånd i diagrammet, får du vist antallet af relaterede meddelelser.

<sup>\*</sup> Hvis du klikker på dette element, udvides diagrammet for at vise flere detaljer. Du kan finde en beskrivelse af hvert element i de udvidede noder i [Registreringsteknologier](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).

![Oplysninger om phishingblokering i mailflowvisning i statusrapporten Mailflow.](../../media/mail-flow-status-report-mailflow-view-details.png)

Detaljetabellen under diagrammet viser følgende oplysninger:

- **Dato**
- **Samlet mail**
- **Edge filtreret**
- **Regelmeddelelser**
- **Antimalwareprogrammet, vedhæftede Pengeskab, regelfiltreret**
- **DMARC-efterligning, efterlignet, phish filtreret**
- **Registrering af detonation**
- **Antispamfiltreret**
- **ZAP er fjernet**
- **Meddelelser, hvor der ikke blev fundet trusler**

Hvis du vælger en række i detaljetabellen, vises en yderligere oversigt over antallet af mails i pop op-dialogboksen med oplysninger.

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)** **Startdato** og **Slutdato**.
- **Retning**: **Udgående** og **Indgående**.

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Tilbage på siden **Statusrapport for mailflow** kan du klikke på  Vis tendenser for at få vist tendensdiagrammer i pop **op-menuen Mailflowtendenser**, der vises.

![Pop op-flowtendenser i mailflowvisning i statusrapporten Mailflow.](../../media/mail-flow-status-report-mailflow-view-show-trends.png)

På siden **Statusrapport for mailflow** skal du klikke på ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen** Eksportér er tilgængelig.

## <a name="malware-detections-report"></a>Rapport over malwareregistreringer

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger findes i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Rapport over mailventetid

Rapporten **Mailventetid i** Defender for Office 365 indeholder oplysninger om maillevering og denonationsventetid, der kan opleves i din organisation. Få mere at vide under [Rapport over mailventetid](view-reports-for-mdo.md#mail-latency-report).

## <a name="spam-detections-report"></a>Rapport over registrering af spam

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger findes i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="spoof-detections-report"></a>Rapport over spoof-registreringer

Rapporten **Spoof-registreringer** viser oplysninger om meddelelser, der blev blokeret eller tilladt på grund af spoofing. Du kan finde flere oplysninger om spoofing [under Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

I den aggregerede visning af rapporten kan der filtreres i 90 dage, mens der kun kan filtreres i ti dage i detaljevisningen.

Hvis du vil have vist rapporten i Microsoft 365 Defender,  \> skal du gå til **& mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & du** finde **Spoof-registreringer og** derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/SpoofMailReport>.

![Widget'en Spoof-registreringer på siden & med samarbejdsrapporter.](../../media/spoof-detections-widget.png)

Diagrammet viser følgende oplysninger:

- **Bestået**
- **Mislykkes**
- **SoftPass**
- **Ingen**
- **Andet**

Når du peger på en dag (datapunktet) i diagrammet, kan du se, hvor mange spoofede meddelelser, der blev registreret og hvorfor.

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Resultat**:
  - **Bestået**
  - **Mislykkes**
  - **SoftPass**
  - **Ingen**
  - **Andet**
- **Spoof-type**: **Intern** og **Ekstern**

![Siden Spoof-mailrapport i Microsoft 365 Defender portal.](../../media/spoof-detections-report-page.png)

Detaljetabellen under grafen viser følgende oplysninger:

- **Dato**
- **Spoofed bruger**
- **Afsendende infrastruktur**
- **Spoof-type**
- **Resultat**
- **Resultatkode**
- **SPF**
- **DKIM**
- **DMARC**
- **Antal meddelelser**

Du kan finde flere oplysninger om sammensatte [godkendelsesresultatkoder i Antispam-brevhoveder i Microsoft 365](anti-spam-message-headers.md).

På siden **Spoof-registreringer** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

## <a name="submissions-report"></a>Rapport over indsendelser

Rapporten **Indsendelser viser** oplysninger om elementer, som administratorer har rapporteret til Microsoft til analyse. Få mere at vide under [Brug administratorindsendelse til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

Hvis du vil have vist rapporten i Microsoft 365 Defender på <https://security.microsoft.com>,  \> skal du gå til **Rapporter & mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & du** finde **Indsendelser og** derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/adminSubmissionReport>. Hvis du vil gå [til administratorindsendelser i Microsoft 365 Defender, skal](admin-submission.md) du **klikke på Gå til indsendelser**. Administratorer vil kunne få vist rapporten i de seneste 30 dage.

![Widgetten Indsendelser på siden & med samarbejdsrapporter.](../../media/submissions-report-widget.png)

Diagrammet viser følgende oplysninger:

- **Afventer**
- **Fuldført**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Rapporteret dato**: **Start- og** **sluttidspunktet**
- **Indsendelsestype**:
  - **Mail**
  - **URL-adresse**
  - **Filer**
- **Indsendelses-id**
- **Netværksmeddelelses-id**
- **Afsender**
- **Navn**
- **Indsendt af**
- **Årsag til indsendelse:**
  - **Ikke uønsket**
  - **Phish**
  - **Malware**
  - **Spam**
- **Kan ændre status**:
  - **Afventer**
  - **Fuldført**

Detaljetabellen under grafen viser de samme oplysninger og har de samme indstillinger  **for** Gruppe  eller Tilpas kolonner som på fanen Indsendt til analyse på **Mail** \> & **indsendelser af samarbejde**. Få mere at vide under [Få vist administratorindsendelser til Microsoft](admin-submission.md#view-admin-submissions-to-microsoft).

På siden **Indsendelser** er **[knappen Eksportér](#export-report)** tilgængelig.

![Rapportside for indsendelser i Microsoft 365 Defender portalen.](../../media/submissions-report-page.png)

## <a name="threat-protection-status-report"></a>Statusrapport over trusselsbeskyttelse

**Statusrapporten for trusselsbeskyttelse** er tilgængelig i både EOP og Defender Office 365, men rapporterne indeholder forskellige data. Eksempelvis kan EOP-kunder få vist oplysninger om malware, der er registreret i en mail, men ikke oplysninger om skadelige filer, der registreres af Pengeskab Vedhæftede filer [til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Rapporten indeholder antallet af mails med skadeligt indhold, f.eks. filer eller webadresser( URL-adresser), der blev blokeret af antimalwareprogrammet, automatisk tømning [(ZAP) og Defender til Office 365-funktioner](zero-hour-auto-purge.md) som [Pengeskab Links](safe-links.md), [Pengeskab](safe-attachments.md) vedhæftede filer og funktioner til beskyttelse mod efterligning i [antiphishing-politikker](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Du kan bruge disse oplysninger til at identificere tendenser eller afgøre, om organisationens politikker skal justeres.

**Bemærk**! Det er vigtigt at forstå, at hvis en meddelelse sendes til fem modtagere, tæller vi den som fem forskellige meddelelser og ikke én meddelelse.

Hvis du vil have vist rapporten i Microsoft 365 Defender,  \> skal du gå til **& mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & skal du** finde Status **for trusselsbeskyttelse** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne en af følgende URL-adresser:

- Defender til Office 365:<https://security.microsoft.com/reports/TPSAggregateReportATP>
- EOP: <https://security.microsoft.com/reports/TPSAggregateReport>

![Statuswidget for trusselsbeskyttelse på & siden Med mailrapporter.](../../media/threat-protection-status-report-widget.png)

Diagrammet viser som standard data for de seneste 7 dage. Hvis du klikker **på Filter** på siden **Statusrapport for trusselsbeskyttelse** , kan du vælge et datointerval på 90 dage (prøveabonnementer kan være begrænset til 30 dage). Detaljetabellen tillader filtrering i 30 dage.

De tilgængelige visninger er beskrevet i de følgende afsnit.

### <a name="view-data-by-overview"></a>Få vist data efter oversigt

![Oversigtsvisning i statusrapporten for trusselsbeskyttelse.](../../media/threat-protection-status-report-overview-view.png)

I **visningen Vis data efter** oversigt vises følgende registreringsoplysninger i diagrammet:

- **Mailmalware**
- **Mail phish**
- **Mailspam**
- **Indholdsmalware**

Der findes ingen tabel med detaljer under diagrammet.

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**.
- **Registrering**:
  - **Mailmalware**
  - **Mail phish**
  - **Mailspam**
  - **Indholdsmalware**
- **Beskyttet af**: **MDO** (Defender for Office 365) og **EOP**.
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti). Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

### <a name="view-data-by-email--phish-and-chart-breakdown-by-detection-technology"></a>Få vist data efter Mail Phish \> - og Diagramopdeling efter registreringsteknologi

![Registreringsteknologivisning for phishing-mail i statusrapporten Trusselsbeskyttelse.](../../media/threat-protection-status-report-phishing-detection-tech-view.png)

> [!NOTE]
> Fra og med maj 2021 er phishingregistreringer i mails blevet opdateret til at  medtage vedhæftede meddelelser, der indeholder phishing-URL-adresser. Denne ændring kan rykke noget af registreringsmængden ud af visningen Vis **data \> via mailmalware** og i **visningen Vis data via phish\>**. Med andre ord kan vedhæftede meddelelser med phishing-URL-adresser, der traditionelt er identificeret som malware, nu identificeres som phishing i stedet.

I **oversigten Vis data efter Phish-mail \>** og diagram via visningen Registreringsteknologi vises følgende oplysninger i diagrammet:

- **URL-adressens skadelige**<sup>\*</sup> omdømme: Skadeligt URL-ry genereret fra Defender Office 365 deonationer i andre Microsoft 365 kunder.
- **Avanceret filter**: Phishing-signaler baseret på maskinel indlæring.
- **Generelt filter**: Phishing-signaler baseret på analytikerregler.
- **Spoof intra-org**: Afsenderen forsøger at efterligne modtagerdomænet.
- **Efterlignet eksternt domæne**: Afsenderen forsøger at efterligne et andet domæne.
- **Spoof DMARC**: DMARC-godkendelsesfejl på meddelelser.
- **Efterligningsbrand**: Efterligning af velkendte mærker baseret på afsendere.
- **Registrering af blandet analyse**
- **Filomseelse**
- **Fingeraftrykssammenholdelse**
- **URL-detonations ry**<sup>\*</sup>
- **URL-detonation**<sup>\*</sup>
- **Efterligningsbruger**<sup>\*</sup>
- **Repræsentationsdomæne**<sup>\*</sup>: Repræsentation af domæner, som kunden ejer eller definerer.
- **Postkasseintelligens**<sup>\*</sup>: Repræsentation af brugere defineret af administrator eller lært via postkasseintelligens.
- **Fildeonation**<sup>\*</sup>
- **Fildeonations ry**<sup>\*</sup>
- **Kampagne**<sup>\*</sup>

<sup>\*</sup>Defender kun Office 365 den

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Registrering**: De samme værdier som i diagrammet.
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Hele eller** den angivne politik.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="view-data-by-email--spam-and-chart-breakdown-by-detection-technology"></a>Få vist data efter mailspam \> og diagramopdeling ud fra registreringsteknologien

![Registreringsteknologivisning for spam i statusrapporten Trusselsbeskyttelse.](../../media/threat-protection-status-report-spam-detection-tech-view.png)

I visning **af data efter mailspam \>** **og diagramoversigten** efter visningen Registreringsteknologi vises følgende oplysninger i diagrammet:

- **ONDSINDET URL-ry**
- **Avanceret filter**
- **Generelt filter**
- **Registrering af blandet analyse**: Flere filtre har bidraget til konklusionen for meddelelsen.
- **Matchende fingeraftryk**: Meddelelsen blev markeret som dårlig på grund af tidligere meddelelser.
- **Domæneomseelse**: Denne meddelelse blev betragtet som spam baseret på afsenderens domæne ry.
- **Masse**: Elementer registreret som overskrider masseindstillingen for brugeren.
- **IP-omdømme**: Meddelelsen blev betragtet som spam baseret på det afsendende IP-adresse ry.

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Registrering**: De samme værdier som i diagrammet.
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Hele eller** den angivne politik.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="view-data-by-email--malware-and-chart-breakdown-by-detection-technology"></a>Få vist data efter mailmalware \> og diagramopdeling efter registreringsteknologi

![Den teknologivisning, der registreres for malware, i statusrapporten for trusselsbeskyttelse.](../../media/threat-protection-status-report-malware-detection-tech-view.png)

> [!NOTE]
> Fra og med maj 2021 blev registreringer af malware i mails opdateret til at medtage **skadelige URL-adresser** i vedhæftede meddelelser. Denne ændring kan rykke noget af registreringsmængden væk fra visningen Vis **data \> via Phish-mail** og i **visningen Vis data via mailmalware\>**. Med andre ord kan skadelige URL-adresser i vedhæftede filer, der traditionelt er identificeret som phishing, nu identificeres som malware i stedet.

I visningen **Vis data efter mailmalware \>** **og diagramoversigten** ved registreringsteknologivisning vises følgende oplysninger i diagrammet:

- **Fildeonation**<sup>\*</sup>: Registrering af Pengeskab vedhæftede filer.
- **Fildeonations ry**<sup>\*</sup>: Alt skadeligt fil ry genereret af Defender for Office 365 deonationer.
- **Filomseelse**
- **Antimalwareprogrammet**<sup>\*</sup>: Registrering fra antimalware-programmer.
- **Blokering af filtyper for antimalwarepolitik**: Disse er mails, der er filtreret fra på grund af den type skadelig fil, der identificeres i meddelelsen.
- **ONDSINDET URL-ry**<sup>\*</sup>
- **URL-detonation**<sup>\*</sup>
- **URL-detonations ry**<sup>\*</sup>
- **Kampagne**<sup>\*</sup>

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Registrering**: De samme værdier som i diagrammet.
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Hele eller** den angivne politik.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for beskyttelse af sikkerhed** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="chart-breakdown-by-policy-type"></a>Diagramopdeling efter politiktype

![Visning af politiktype for phishing-mail, spammail eller malwaremail i statusrapporten for trusselsbeskyttelse.](../../media/threat-protection-status-report-phishing-policy-type-view.png)

I visning **af data \> efter Phish-mail**, Vis **data \>** efter spammail eller Vis **data \>** efter mailmalwarevisninger, når  du vælger Diagramopdeling efter politiktype, vises følgende oplysninger i diagrammet:

- **Antimalware**
- **Pengeskab vedhæftede filer**<sup>\*</sup>
- **Antiphish**
- **Antispam**
- **Regel for mailflow** (også kaldet en transportregel)
- **Andre**

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Registrering**:
  - **URL-adressens skadelige**<sup>\*</sup> omdømme: Skadeligt URL-ry genereret fra Defender Office 365 deonationer i andre Microsoft 365 kunder.
  - **Avanceret filter**: Phishing-signaler baseret på maskinel indlæring.
  - **Generelt filter**: Phishing-signaler baseret på analytikerregler.
  - **Spoof intra-org**: Afsenderen forsøger at efterligne modtagerdomænet.
  - **Efterlignet eksternt domæne**: Afsenderen forsøger at efterligne et andet domæne.
  - **Spoof DMARC**: DMARC-godkendelsesfejl på meddelelser.
  - **Efterligningsbrand**: Efterligning af velkendte mærker baseret på afsendere.
  - **Registrering af blandet analyse**
  - **Filomseelse**
  - **Fingeraftrykssammenholdelse**
  - **URL-detonations ry**<sup>\*</sup>
  - **URL-detonation**<sup>\*</sup>
  - **Efterligningsbruger**<sup>\*</sup>
  - **Repræsentationsdomæne**<sup>\*</sup>: Repræsentation af domæner, som kunden ejer eller definerer.
  - **Postkasseintelligens**<sup>\*</sup>: Repræsentation af brugere defineret af administrator eller lært via postkasseintelligens.
  - **Fildeonation**<sup>\*</sup>
  - **Fildeonations ry**<sup>\*</sup>
  - **Kampagne**<sup>\*</sup>
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Hele eller** den angivne politik.
- **Modtagere**

<sup>\*</sup>Defender kun Office 365 den

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="chart-breakdown-by-delivery-status"></a>Diagramoversigt efter leveringsstatus

![Leveringsstatusvisning for phishing-mail og malwaremail i statusrapporten Trusselsbeskyttelse.](../../media/threat-protection-status-report-phishing-delivery-status-view.png)

I Visning **af data efter Phish-mail\>**, Vis **data \>** efter Spammail eller Vis **data \>** efter mailmalwarevisninger kan du  vælge Diagramopdeling efter Leveringsstatus og vise følgende oplysninger i diagrammet:

- **Hostet postkasse: Indbakke**
- **Hostet postkasse: Uønsket**
- **Hostet postkasse: Brugerdefineret mappe**
- **Hostet postkasse: Slettede elementer**
- **Videresendt**
- **Lokal server: Leveret**
- **Karantæne**
- **Leveringen mislykkedes**
- **Ind tabt**

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Registrering**:
  - **URL-adressens skadelige**<sup>\*</sup> omdømme: Skadeligt URL-ry genereret fra Defender Office 365 deonationer i andre Microsoft 365 kunder.
  - **Avanceret filter**: Phishing-signaler baseret på maskinel indlæring.
  - **Generelt filter**: Phishing-signaler baseret på analytikerregler.
  - **Spoof intra-org**: Afsenderen forsøger at efterligne modtagerdomænet.
  - **Efterlignet eksternt domæne**: Afsenderen forsøger at efterligne et andet domæne.
  - **Spoof DMARC**: DMARC-godkendelsesfejl på meddelelser.
  - **Efterligningsbrand**: Efterligning af velkendte mærker baseret på afsendere.
  - **Registrering af blandet analyse**
  - **Filomseelse**
  - **Fingeraftrykssammenholdelse**
  - **URL-detonations ry**<sup>\*</sup>
  - **URL-detonation**<sup>\*</sup>
  - **Efterligningsbruger**<sup>\*</sup>
  - **Repræsentationsdomæne**<sup>\*</sup>: Repræsentation af domæner, som kunden ejer eller definerer.
  - **Postkasseintelligens**<sup>\*</sup>: Repræsentation af brugere defineret af administrator eller lært via postkasseintelligens.
  - **Fildeonation**<sup>\*</sup>
  - **Fildeonations ry**<sup>\*</sup>
  - **Kampagne**<sup>\*</sup>
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Hele eller** den angivne politik.
- **Modtagere**

<sup>\*</sup>Defender kun Office 365 den

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="view-data-by-content--malware"></a>Få vist data efter indholdsmalware \>

![Visning af indholdsmalware i statusrapporten trusselsbeskyttelse.](../../media/threat-protection-status-report-content-malware-view.png)

I visningen **Vis data efter indholdsmalware \>** vises følgende oplysninger i diagrammet for Microsoft Defender Office 365 organisationer:

- **Antimalwareprogrammet**: Skadelige filer, der er registreret i SharePoint, OneDrive og Microsoft Teams af [den indbyggede virusregistrering i Microsoft 365](virus-detection-in-spo.md).
- **MDO-detonation**: Skadelige filer registreret [af Pengeskab vedhæftede filer for SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).
- **Filomseelse**

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato (UTC)**
- **Vedhæftet filnavn**
- **Arbejdsbelastning**
- **Registreringsteknologi**
- **Filstørrelse**
- **Senest redigerer bruger**

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Registrering**: **Antimalwareprogrammet**, **MDO-detonation** og **fildeonation**
- **Arbejdsbelastning****: Teams**, **SharePoint** og **OneDrive**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

### <a name="view-data-by-system-override-and-chart-breakdown-by-reason"></a>Få vist data efter Systemtilsidesættelse og Diagramopdeling efter årsag

![Tilsidesættelse af meddelelse og Diagramopdeling efter Årsagsvisning i statusrapporten Trusselsbeskyttelse.](../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png)

I **tilsidesættelse af data efter system** og **Diagramopdeling efter Årsagsvisning** vises følgende oplysninger om tilsidesættelse af årsag i diagrammet:

- **Spring over det lokale miljø**
- **Tillad IP**
- **Exchange transportregel** (regel for mailflow)
- **Organisationen tilladte afsendere**
- **Organisationens tilladte domæner**
- **ZAP ikke aktiveret**
- **Bruger Pengeskab afsender**
- **Bruger Pengeskab domæne**
- **Phishing-simulering**: Få mere at vide under Konfigurer levering af [phishing-simulering fra tredjeparter til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).
- **Tredjepartsfilter**

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Systemtilsidesættelse**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Årsag**: De samme værdier som diagrammet.
- **Leveringssted**: **Mappen Uønsket mail er ikke aktiveret** **eller SecOps-postkassen**.
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**: **Alle**
- **Politiknavn (kun detaljetabelvisning)**: **Alle**
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen](#export-report)** Eksportér er tilgængelig.

### <a name="view-data-by-system-override-and-chart-breakdown-by-delivery-location"></a>Få vist data efter Systemtilsidesættelse og Diagramopdeling efter leveringssted

![Tilsidesættelse af meddelelse og Diagramopdeling efter visningen Leveringsplacering i statusrapporten for trusselsbeskyttelse.](../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png)

I visningen **Vis data efter systemtilsidesættelse** og **Diagramopdeling** efter visningen Leveringsplacering vises følgende oplysninger om tilsidesættelse af årsag i diagrammet:

- **Mappen uønsket mail er ikke aktiveret**
- **SecOps-postkasse**: Få mere at vide under Konfigurer levering af phishing-simuleringer fra tredjeparter til brugere og ufiltrerede meddelelser til [SecOps-postkasser](configure-advanced-delivery.md).

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Systemtilsidesættelse**
- **Afsender-IP**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du klikker **på Filter**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** **og Slutdato**
- **Årsag**
  - **Spring over det lokale miljø**
  - **Tillad IP**
  - **Exchange transportregel** (regel for mailflow)
  - **Organisationen tilladte afsendere**
  - **Organisationens tilladte domæner**
  - **ZAP ikke aktiveret**
  - **Bruger Pengeskab afsender**
  - **Bruger Pengeskab domæne**
  - **Phishing-simulering**: Få mere at vide under Konfigurer levering af [phishing-simulering fra tredjeparter til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).
  - **Tredjepartsfilter**
- **Leveringssted**: **Mappen Uønsket mail er ikke aktiveret** **eller SecOps-postkassen**.
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle eller** det angivne brugermærke (herunder prioritetskonti). Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).
- **Domæne**: **Alle eller** et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**<sup>\*</sup>
  - **Antiphish**
  - **Antispam**
  - **Mailflowregel** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Alle**
- **Modtagere**

<sup>\*</sup>Defender kun Office 365 den

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På **statussiden for Trusselsbeskyttelse** skal du klikke ![på ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen](#export-report)** Eksportér er tilgængelig.

## <a name="top-malware-report"></a>Vigtigste malwarerapport

Den **vigtigste malwarerapport** viser de forskellige typer malware, der blev registreret af [beskyttelse mod malware i EOP](anti-malware-protection.md).

Hvis du vil have vist rapporten i Microsoft 365 Defender,  \> skal du gå til **& mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & du finde** **mest malware** og derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/TopMalware>.

![Den mest populære malwarewidget på siden & med samarbejdsrapporter.](../../media/top-malware-report-widget.png)

Når du peger på en kile i cirkeldiagrammet, kan du se navnet på en type malware, og hvor mange meddelelser der blev registreret som malware.

På siden **Øverste malwarerapport** vises der en større version af cirkeldiagrammet. Detaljetabellen under diagrammet viser følgende oplysninger:

- **Vigtigste malwares**
- **Antal**

Hvis du klikker **på Filter**, kan du angive et datointerval **med Startdato** **og Slutdato**.

På den **øverste malwareside** skal du klikke ![på ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Ikonet Opret tidsplan](#schedule-report)** og ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](#export-report)** Eksportér er tilgængelige.

![Den mest populære visning af malwarerapport.](../../media/top-malware-report-view.png)

## <a name="top-senders-and-recipients-report"></a>Rapport over de mest populære afsendere og modtagere

Rapporten **Bedste afsendere og modtagere** er tilgængelig både i EOP og Defender Office 365, men rapporterne indeholder forskellige data. Eksempelvis kan EOP-kunder få vist oplysninger om de mest populære modtagere af malware, spam og phishing , men ikke oplysninger om malware, der registreres af Pengeskab Vedhæftede filer eller phishing, der [registreres ved repræsentationsbeskyttelse](safe-attachments.md).[](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

De **mest populære** afsendere og modtagere viser de mest populære meddelelsesafsendere i organisationen samt de øverste modtagere af meddelelser, der blev registreret af EOP og Defender for Office 365 beskyttelsesfunktioner. Rapporten viser som standard data for den seneste uge, men der er tilgængelige data for de seneste 90 dage.

Hvis du vil have vist rapporten i Microsoft 365 Defender på <https://security.microsoft.com>,  \> skal du gå til **Rapporter & mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Rapporter & mailsamarbejde skal** du finde **rapporten Bedste afsendere og modtagere og** derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne en af følgende URL-adresser:

- Defender til Office 365:<https://security.microsoft.com/reports/TopSenderRecipientsATP>
- EOP: <https://security.microsoft.com/reports/TopSenderRecipient>

![Widget med de mest populære afsendere og modtagere i dashboardet Rapporter.](../../media/top-senders-and-recipients-widget.png)

Når du peger på en kile i cirkeldiagrammet, kan du se antallet af meddelelser til afsenderen eller modtageren.

På siden **Øverste afsendere og modtagere** vises der en større version af cirkeldiagrammet. Følgende diagrammer er tilgængelige:

- **Vis data for de mest populære mailafsendere** (dette er standardvisningen)
- **Vis data for de mest populære mailmodtagere**
- **Vis data for de mest populære modtagere af uønsket post**
- **Vis data for de vigtigste malwaremodtagere** (EOP)
- **Vis data for de mest populære phishing-modtagere**
- **Vis data for de vigtigste malwaremodtagere (MDO)**
- **Vis data for Top phish-modtagere (MDO)**

Dataene ændres på baggrund af dit valg.

Når du peger på en kile i cirkeldiagrammet, kan du se antallet af meddelelser for den pågældende afsender eller modtager.

Detaljetabellen under grafen viser afsendere eller modtagere og antal meddelelser baseret på den visning, du har valgt.

Du kan filtrere både diagrammet og detaljetabellen ved at klikke **på Filtrer** og **vælge Startdato** **og Slutdato**.

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Øverste afsendere og modtagere** skal du klikke på ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen** Eksportér er tilgængelig.

![Vis data for Visning af de mest populære mailafsendere i rapporten Bedste afsendere og modtagere.](../../media/top-senders-and-recipients-report-view.png)

## <a name="url-protection-report"></a>Rapport over beskyttelse af URL-adresser

Rapporten **om beskyttelse af URL-adresser** er kun tilgængelig i Microsoft Defender Office 365. Du kan få mere at vide under [Rapport om beskyttelse af URL-adresser](view-reports-for-mdo.md#url-protection-report).

## <a name="user-reported-messages-report"></a>Rapport over rapporterede meddelelser

> [!IMPORTANT]
> For at få rapporten **om meddelelser rapporteret** af brugeren til at fungere korrekt, skal **overvågningslogføring være aktiveret** for Microsoft 365 miljø. Dette udføres typisk af en person, der har fået tildelt overvågningslogrollen Exchange Online. Få mere at vide under [Slå Microsoft 365 søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

Rapporten **Bruger rapporterede meddelelser** viser oplysninger om mails, som brugere har rapporteret som uønsket mail, phishingforsøg eller gode mails ved hjælp af [](enable-the-report-message-add-in.md) tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet [Rapportphishing](enable-the-report-phish-add-in.md).

Hvis du vil have vist rapporten i Microsoft 365 Defender,  \> skal du gå til **& mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & du finde** **brugerrapporterede meddelelser og** derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/userSubmissionReport>. Hvis du vil gå [til administratorindsendelser i Microsoft 365 Defender, skal](admin-submission.md) du **klikke på Gå til indsendelser**.

![Brugeren rapporterede beskedwidget på siden & med samarbejdsrapporter.](../../media/user-reported-messages-widget.png)

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Rapporteret dato**: **Start- og** **sluttidspunktet**
- **Rapporteret af**
- **Mailens emne**
- **Meddelelse rapporteret id**
- **Netværksmeddelelses-id**
- **Afsender**
- **Rapporteret årsag**
  - **Ikke uønsket**
  - **Phish**
  - **Spam**
- **Phish-simulering**: **Ja** eller **Nej**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Hvis du vil gruppere posterne, **skal du** klikke på Grupper og vælge en af følgende værdier på rullelisten:

- **Ingen**
- **Årsag**
- **Afsender**
- **Rapporteret af**
- **Genscanne resultat**
- **Phish-simulering**

![Brugeren rapporterede meddelelsesrapporten.](../../media/user-reported-messages-report.png)

Detaljetabellen under grafen viser følgende oplysninger:

- **Mailens emne**
- **Rapporteret af**
- **Dato rapporteret**
- **Afsender**
- **Rapporteret årsag**
- **Genscanne resultat**
- **Mærker**: Du kan finde flere oplysninger om brugermærker under [Brugermærker](user-tags.md).

Hvis du vil sende en meddelelse til Microsoft til analyse, skal du vælge meddelelsesposten i tabellen, klikke på Send til **Microsoft** til analyse og derefter vælge en af følgende værdier på rullelisten:

- **Rapport rens**
- **Rapportér phishing**
- **Rapportér malware**
- **Rapportér spam**'
- **Undersøgelse af udløser** (Defender til Office 365)

På siden **Bruger rapporterede meddelelser** , ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen](#export-report)** Eksportér er tilgængelig.

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Hvilke tilladelser er nødvendige for at få vist disse rapporter?

For at få vist og bruge de rapporter, der er beskrevet i denne artikel, skal du være medlem af en af følgende rollegrupper på Microsoft 365 Defender portal:

- **Organisationsadministration**
- **Sikkerhedsadministrator**
- **Sikkerhedslæser**
- **Global læser**

Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

**Bemærk**! Når du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Hvad nu, hvis rapporterne ikke viser data?

Hvis du ikke kan se data i dine rapporter, skal du kontrollere de filtre, du bruger, og kontrollere, at dine politikker er konfigureret korrekt. Du kan få mere at vide [under Beskyt mod trusler](protect-against-threats.md).

## <a name="schedule-report"></a>Planlæg rapport

1. Klik på ikonet Opret tidsplan på hovedsiden for ![den specifikke rapport.](../../media/m365-cc-sc-create-icon.png) **Opret tidsplan**.
2. Guiden **Opret planlagt rapport** åbnes. På siden **Navngive planlagt rapport** skal du gennemse eller tilpasse **værdien Navn** og derefter klikke på **Næste**.
3. På siden **Angiv indstillinger** skal du konfigurere følgende indstillinger:
   - **Hyppighed**: Vælg en af følgende værdier:
     - **Ugentlig** (standard)
     - **Månedligt**
   - **Startdato**: Når generering af rapporten starter. Standardværdien er i dag.
   - **Udløbsdato:** Når generationen af rapporten slutter. Standardværdien er et år fra dags dato.

   Klik på Næste, når du er **færdig**.

4. Vælg **modtagere til** rapporten på siden Modtagere. Standardværdien er din mailadresse, men du kan tilføje andre.

   Klik på Næste, når du er **færdig**.

5. Gennemgå **dine** valg på siden Gennemse. Du kan klikke på **knappen** Tilbage eller **linket Rediger** i de pågældende sektioner for at foretage ændringer.

   Klik på Send, når du er **færdig**.

### <a name="managed-existing-scheduled-reports"></a>Administrerede eksisterende planlagte rapporter

Hvis du vil administrere planlagte rapporter, som du allerede har oprettet, skal du gøre følgende:

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå **til Rapporter og** \> **udvide & vælge** \> **Administrer tidsplaner**.

   For at gå direkte til siden **Administrer tidsplaner** skal du bruge <https://security.microsoft.com/ManageSubscription>.

2. På siden **Administrer tidsplaner** vises følgende oplysninger for hver planlagt rapport:
   - **Planlæg startdato**
   - **Navn på tidsplan**
   - **Rapporttype**
   - **Hyppighed**
   - **Senest sendt**

   Find den eksisterende planlagte rapport, du vil ændre.

3. Når du har valgt den planlagte rapport, skal du udføre en af følgende handlinger i pop op-menuen med oplysninger, der åbnes:
   - **Rediger navn**: Klik på denne knap, skift navnet på rapporten i pop op-menuen, der vises, og klik derefter på **Gem**.
   - **Slet tidsplan**: Klik på denne knap, læs den advarsel, der vises (tidligere rapporter kan ikke længere hentes), og klik derefter på **Gem**.
   - **Sektionen Planlægningsdetaljer** : Klik **på Rediger indstillinger** for at ændre følgende indstillinger:
     - **Hyppighed**: **Ugentlig eller** **Månedlig**
     - **Startdato**
     - **Udløbsdato**

     Klik på **Gem**, når du er færdig.

   - **Sektionen Modtagere** : Klik på **Rediger modtagere for** at tilføje eller fjerne modtagere for den planlagte rapport. Når du er færdig, skal du klikke på **Gem**

   Klik på Luk, når du er **færdig**.

## <a name="request-report"></a>Anmod om rapport

1. Klik på ikonet Anmod om rapport på hovedsiden for ![den specifikke rapport.](../../media/m365-cc-sc-download-icon.png) **Anmod om rapport**.
2. Guiden **Opret rapport efter behov** åbnes. På siden **Name on-demand-rapport** skal du gennemse eller tilpasse **værdien Navn** og derefter klikke på **Næste**.
3. På siden **Angiv indstillinger** skal du gennemse eller konfigurere følgende indstillinger:
   - **Startdato**: Når generering af rapporten starter. Standardværdien er en måned siden.
   - **Udløbsdato:** Når generationen af rapporten slutter. Standardværdien er i dag.

   Klik på Næste, når du er **færdig**.

4. Vælg **modtagere til** rapporten på siden Modtagere. Standardværdien er din mailadresse, men du kan tilføje andre.

   Klik på Næste, når du er **færdig**.

5. Gennemgå **dine** valg på siden Gennemse. Du kan klikke på **knappen** Tilbage eller **linket Rediger** i de pågældende sektioner for at foretage ændringer.

   Klik på Send, når du er **færdig**.

6. Når rapporten er blevet oprettet, kommer du til siden Ny rapport, der  er oprettet efter behov, hvor du kan klikke på Opret en anden **rapport** eller **Udført**.

   Rapporten findes også på siden **Rapporter til download** som beskrevet i næste afsnit.

### <a name="download-reports"></a>Download rapporter

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå **til Rapporter udvide** \> **& vælge** \> **Rapporter til download**.

   For at gå direkte til siden **Rapporter til overførsel** skal du bruge <https://security.microsoft.com/ReportsForDownload>.

2. På siden **Rapporter til overførsel** vises følgende oplysninger for hver tilgængelig rapport:
   - **Startdato**
   - **Navn**
   - **Rapporttype**
   - **Senest sendt**
   - **Retning**

   Find og vælg den rapport, du vil downloade.

## <a name="export-report"></a>Eksportér rapport

Klik på eksportikonet på hovedsiden for ![den specifikke rapport.](../../media/m365-cc-sc-download-icon.png) **Eksportér** (hvis dette link er tilgængeligt). Der **vises en** pop op-vindue med Eksportbetingelser, hvor du kan konfigurere følgende indstillinger:

- **Vælg en visning, der skal** eksporteres: Vælg en af følgende værdier:
  - **Oversigt**: Data er tilgængelige for de seneste 90 dage.
  - **Detaljer**: Data er tilgængelige for de seneste 30 dage.
- **Dato (UTC)**: **Startdato** **og slutdato**.

Klik på Eksportér, når du er færdig med at konfigurere **filtrene**. I den dialogboks, der åbnes, kan du vælge at åbne filen, gemme filen eller huske det valgte.

Hver .csv fil er begrænset til 150.000 rækker. Hvis dataene indeholder mere end 150.000 rækker, oprettes .csv filer.

## <a name="related-topics"></a>Relaterede emner

[Beskyttelse mod spam og antimalware i EOP](anti-spam-and-anti-malware-protection.md)

[Intelligente rapporter og indsigt i Microsoft 365 Defender-portalen](reports-and-insights-in-security-and-compliance.md)

[Få vist rapporter om mailflow i Microsoft 365 Defender-portalen](view-mail-flow-reports.md)

[Få vist rapporter for Defender for Office 365](view-reports-for-mdo.md)
