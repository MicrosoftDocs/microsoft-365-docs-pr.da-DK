---
title: Få vist sikkerhedsrapporter for mail
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
description: Administratorer kan få mere at vide om, hvordan de finder og bruger de mailsikkerhedsrapporter, der er tilgængelige på Microsoft 365 Defender-portalen.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c83213278c7f9bc3b63c141e4d964475d64599d1
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286620"
---
# <a name="view-email-security-reports-in-the-microsoft-365-defender-portal"></a>Få vist mailsikkerhedsrapporter på Microsoft 365 Defender-portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Der findes en række forskellige rapporter på Microsoft 365 Defender-portalen på <https://security.microsoft.com> for at hjælpe dig med at se, hvordan sikkerhedsfunktioner for mail, f.eks. anti-spam og antimalwarefunktioner i Microsoft 365 beskytter din organisation. Hvis du har de [nødvendige tilladelser](#what-permissions-are-needed-to-view-these-reports), kan du få vist og downloade disse rapporter som beskrevet i denne artikel.

> [!NOTE]
>
> Nogle af rapporterne på siden **Mail & samarbejdsrapporter** kræver Microsoft Defender for Office 365. Du kan få oplysninger om disse rapporter under [Få vist Defender for Office 365 rapporter på portalen Microsoft 365 Defender](view-reports-for-mdo.md).
>
> Rapporter, der er relateret til mailflow, findes nu i Exchange Administration. Du kan få flere oplysninger om disse rapporter [under Mailflowrapporter i det nye Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="email-security-report-changes-in-the-microsoft-365-defender-portal"></a>Ændringer i sikkerhedsrapporten via mail på Microsoft 365 Defender-portalen

De Exchange Online Protection (EOP) og Microsoft Defender for Office 365 rapporter på Microsoft 365 Defender-portalen, der er blevet erstattet, flyttet eller udfaset, er beskrevet i følgende tabel.

|Frarådet rapport og cmdlet'er|Ny rapport og cmdlet'er|Id for Meddelelsescenter|Dato|
|---|---|:---:|:---:|
|**URL-sporing** <p> Get-URLTrace|[URL-beskyttelsesrapport](view-reports-for-mdo.md#url-protection-report) <p> [Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <br> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|MC239999|Juni 2021|
|**Mailrapport sendt og modtaget** <p> Get-MailTrafficReport <br> Get-MailDetailReport|[Statusrapport om trusselsbeskyttelse](#threat-protection-status-report) <br> [Statusrapport for mailflow](#mailflow-status-report) <p> [Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <br> [Get-MailFlowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|MC236025|Juni 2021|
|**Videresender rapport** <p> ingen cmdlet'er|[Rapport over automatisk videresendte meddelelser i EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) <p> ingen cmdlet'er|MC250533|Juni 2021|
|**rapport over filtyper for vedhæftede filer Pengeskab** <p> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Statusrapport om trusselsbeskyttelse: Få vist data via mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250532|Juni 2021|
|**Pengeskab meddelelsesdispositionsrapport for vedhæftede filer** <p> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Statusrapport om trusselsbeskyttelse: Få vist data via mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250531|Juni 2021|
|**Malware, der er registreret i mailrapport** <p> Get-MailTrafficReport <br> Get-MailDetailMalwareReport|[Statusrapport om trusselsbeskyttelse: Få vist data via mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250530|Juni 2021|
|**Rapport over registrering af spam** <p> Get-MailTrafficReport <br> Get-MailDetailSpamReport|[Statusrapport om trusselsbeskyttelse: Få vist data via mailspam \>](#view-data-by-email--spam-and-chart-breakdown-by-detection-technology) <p> [Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250529|Oktober 2021|
|Get-AdvancedThreatProtectionDocumentReport <p> Get-AdvancedThreatProtectionDocumentDetail|[Get-ContentMalwareMdoAggregateReport](/powershell/module/exchange/get-contentmalwaremdoaggregatereport) <p> [Get-ContentMalwareMdoDetailReport](/powershell/module/exchange/get-contentmalwaremdodetailreport)|TBA|Maj 2022|
|**rapport over Exchange transportregel** <p> [Hent-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|[Exchange rapport over transportregel i EAC](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report) <p> [Hent-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|MC316157|April 2022|
|Get-MailTrafficTopReport|[Statusrapport om trusselsbeskyttelse: Få vist data via mailmalware \>](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <p> [Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <p> **Bemærk**! Der er ingen erstatning for krypteringsrapporteringsfunktionerne i Get-MailTrafficTopReport.|MC315742|April 2022|

## <a name="compromised-users-report"></a>Rapport over kompromitterede brugere

> [!NOTE]
> Denne rapport er tilgængelig i Microsoft 365 organisationer med Exchange Online postkasser. Den er ikke tilgængelig i enkeltstående Exchange Online Protection organisationer (EOP).

Rapporten **Kompromitterede brugere** viser antallet af brugerkonti, der er markeret som **mistænkelige** eller **begrænsede** inden for de seneste 7 dage. Konti i en af disse tilstande er problematiske eller endda kompromitterede. Med hyppig brug kan du bruge rapporten til at spotte stigninger og endda tendenser i mistænkelige eller begrænsede konti. Du kan få flere oplysninger om kompromitterede brugere under [Besvarelse af en kompromitteret mailkonto](responding-to-a-compromised-email-account.md).

:::image type="content" source="../../media/compromised-users-report-widget.png" alt-text="Widgetten Kompromitterede brugere på siden Mail & samarbejdsrapporter" lightbox="../../media/compromised-users-report-widget.png":::

I den samlede visning vises data for de seneste 90 dage, og i detaljevisningen vises data for de sidste 30 dage.

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. Find **kompromitterede brugere** på siden **Mail & samarbejdsrapporter**, og klik derefter på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/CompromisedUsers>.

På siden **Kompromitterede brugere** vises følgende oplysninger for det angivne datointerval i diagrammet:

- **Begrænset**: Brugerkontoen er blevet begrænset fra at sende mail på grund af meget mistænkelige mønstre.
- **Mistænkelig**: Brugerkontoen har sendt mistænkelig mail og er i fare for at blive begrænset fra at sende mail.

I detaljetabellen under grafen kan du se følgende oplysninger:

- **Oprettelsestidspunkt**
- **Bruger-id**
- **Handling**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC):****Startdato** og **Slutdato**.
- **Aktivitet**: **Begrænset** eller **mistænkelig**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Kompromitterede brugere** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

:::image type="content" source="../../media/compromised-users-report-activity-view.png" alt-text="Visningen Rapport i rapporten Kompromitterede brugere" lightbox="../../media/compromised-users-report-activity-view.png":::

## <a name="exchange-transport-rule-report"></a>rapport over Exchange transportregel

Rapporten **Exchange transportregel** viser effekten af regler for mailflow (også kaldet transportregler) på indgående og udgående meddelelser i din organisation.

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Exchange transportregel** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/transport-rule-report-widget.png" alt-text="Widgetten Exchange transportregel på siden Mail & samarbejdsrapporter" lightbox="../../media/transport-rule-report-widget.png":::

På **rapportsiden Exchange transportregel** er de tilgængelige diagrammer og data beskrevet i følgende afsnit.
> [!NOTE]
> **Rapporten Exchange transportregel** er nu tilgængelig i EAC. Du kan få flere oplysninger i [rapporten Exchange transportregel i den nye EAC](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

### <a name="chart-breakdown-by-direction"></a>Diagramopdeling efter retning

:::image type="content" source="../../media/transport-rule-report-etr-direction-view.png" alt-text="Retningsvisningen for Exchange transportregler i rapporten Exchange transportregel" lightbox="../../media/transport-rule-report-etr-direction-view.png":::

Hvis du vælger **Diagramopdeling efter Retning**, er følgende diagrammer tilgængelige:

- **Få vist data efter Exchange transportregler**: Antallet af **indgående** og **udgående** meddelelser, der blev påvirket af regler for mailflow.
- **Få vist data efter DLP-Exchange transportregler**: Antallet af **indgående** og **udgående** meddelelser, der blev påvirket af DLP-regler (forebyggelse af datatab).

Følgende oplysninger vises i detaljetabellen under grafen:

- **Dato**
- **DLP-politik** (**få vist data efter DLP-Exchange kun transportregler**)
- **Transportregel**
- **Emne**
- **Afsenderadresse**
- **Modtageradresse**
- **Sværhedsgraden**
- **Retning**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC)** **Startdato** og **Slutdato**.
- **Retning**: **Udgående** og **indgående**.
- **Alvorsgrad**: **Høj alvorsgrad**, **Mellem alvorsgrad** og **Lav alvorsgrad**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På **rapportsiden Exchange transportregel** vises ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="chart-breakdown-by-severity"></a>Diagramopdeling efter alvorsgrad

:::image type="content" source="../../media/transport-rule-report-etr-severity-view.png" alt-text="Alvorsgradsvisningen for Exchange transportregler i rapporten over Exchange transportregel" lightbox="../../media/transport-rule-report-etr-severity-view.png":::

Hvis du vælger **Diagramopdeling efter Alvorsgrad**, er følgende diagrammer tilgængelige:

- **Få vist data efter Exchange transportregler**: Meddelelserne **Høj alvorsgrad**, **Mellem alvorsgrad** og **Lav alvorsgrad**. Du angiver alvorsgradsniveauet som en handling i reglen (**Overvåg denne regel med alvorsgradsniveau** eller _AngivAuditSeverity_). Du kan få flere oplysninger under [Handlinger i mailflowregel i Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions).

- **Få vist data efter DLP-Exchange transportregler**: Antallet af meddelelser med **høj alvorsgrad**, **mellem alvorlighed** og **lav alvorsgrad**, der blev påvirket af DLP-regler for mailflow.

Følgende oplysninger vises i detaljetabellen under grafen:

- **Dato**
- **DLP-politik** (**få vist data efter DLP-Exchange kun transportregler**)
- **Transportregel**
- **Emne**
- **Afsenderadresse**
- **Modtageradresse**
- **Sværhedsgraden**
- **Retning**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Retning**: **Udgående** og **indgående**
- **Alvorsgrad**: **Høj alvorsgrad**, **Mellem alvorsgrad** og **Lav alvorsgrad**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På **rapportsiden Exchange transportregel** vises ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

## <a name="forwarding-report"></a>Videresender rapport

> [!NOTE]
> Denne rapport er nu tilgængelig i EAC. Du kan få flere oplysninger i [Rapport over automatisk videresendte meddelelser i den nye EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Statusrapport for mailflow

**Statusrapporten Mailflow** er en smart rapport, der viser oplysninger om indgående og udgående mail, registrering af spam, malware, mail, der er identificeret som "god", og oplysninger om tilladte eller blokerede mails på kanten. Dette er den eneste rapport, der indeholder oplysninger om edge-beskyttelse, og som viser, hvor meget mail, der er blokeret, før det tillades i tjenesten til evaluering af Exchange Online Protection (EOP). Det er vigtigt at forstå, at hvis en meddelelse sendes til fem modtagere, tæller vi den som fem forskellige meddelelser og ikke én meddelelse.

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Statusoversigt over mailflow** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/mail-flow-status-report-widget.png" alt-text="Widgetten Mailflowstatusoversigt på siden Mail & samarbejdsrapporter" lightbox="../../media/mail-flow-status-report-widget.png":::

### <a name="type-view-for-the-mailflow-status-report"></a>Typevisning for statusrapporten Mailflow

:::image type="content" source="../../media/mail-flow-status-report-type-view.png" alt-text="Visningen Type i statusrapporten Mailflow" lightbox="../../media/mail-flow-status-report-type-view.png":::

På **rapportsiden Mailflowstatus** er fanen **Type** valgt som standard. Diagrammet viser følgende oplysninger for det angivne datointerval:

- **God mail**: Mail, der er besluttet på ikke at være spam, eller som er tilladt af bruger- eller organisationspolitikker.
- **I alt**
- **Malware**: Mail, der er blokeret som malware af forskellige filtre.
- **Phishingmail**: Mail, der er blokeret som phishing af forskellige filtre.
- **Spam**: Mail, der er blokeret som spam af forskellige filtre.
- **Edge Protection**: Mail, der afvises ved kanten/perimeteren, før den evalueres af EOP eller Defender for Office 365.
- **Regelmeddelelser**: Mails, der blev reageret på efter regler for mailflow (også kendt som transportregler).

I detaljetabellen under grafen kan du se følgende oplysninger:

- **Retning**
- **Type**
- **24 timer**
- **3 dage**
- **7 dage**
- **15 dage**
- **30 dage**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC):****Startdato** og **Slutdato**.
- **Mailretning**: **Indgående** og **udgående**.
- **Type**:
  - **God mail**
  - **Malware**
  - **Spam**
  - **Edge-beskyttelse**
  - **Regelmeddelelser**
  - **Phishing-mail**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Tilbage på **rapportsiden Mailflowstatus** kan du vælge mellem følgende værdier, hvis du klikker på **Vælg en kategori for at få flere oplysninger**:

- **Phishingmail**: Dette valg fører dig til [statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Malware i mail**: Dette valg fører dig til [statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Spamregistreringer**: Dette valg fører dig til [rapporten Spamregistreringer](view-email-security-reports.md#spam-detections-report).
- **Grænseblokeret spam**: Dette valg fører dig til [rapporten Spamregistreringer](view-email-security-reports.md#spam-detections-report).

På **rapportsiden Mailflowstatus** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Ikonet Opret tidsplan](#schedule-report)** og ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="direction-view-for-the-mailflow-status-report"></a>Retningsvisning for statusrapporten Mailflow

:::image type="content" source="../../media/mail-flow-status-report-direction-view.png" alt-text="Visningen Retning i statusrapporten Mailflow" lightbox="../../media/mail-flow-status-report-direction-view.png":::

Hvis du klikker på fanen **Retning** , viser diagrammet følgende oplysninger for det angivne datointerval:

- **Indgående**
- **Udgående**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC):****Startdato** og **Slutdato**.
- **Mailretning**: **Indgående** og **udgående**.
- **Type**:
  - **God mail**
  - **Malware**
  - **Spam**
  - **Edge-beskyttelse**
  - **Regelmeddelelser**
  - **Phishing-mail**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Tilbage på **rapportsiden Mailflowstatus** kan du vælge mellem følgende værdier, hvis du klikker på **Vælg en kategori for at få flere oplysninger**:

- **Phishingmail**: Dette valg fører dig til [statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Malware i mail**: Dette valg fører dig til [statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).
- **Spamregistreringer**: Dette valg fører dig til [rapporten Spamregistreringer](view-email-security-reports.md#spam-detections-report).
- **Grænseblokeret spam**: Dette valg fører dig til [rapporten Spamregistreringer](view-email-security-reports.md#spam-detections-report).

På **rapportsiden Mailflowstatus** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **Ikonet Opret tidsplan** og ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **Eksportknapper** er tilgængelige.

### <a name="mailflow-view-for-the-mailflow-status-report"></a>Visningen Mailflow for statusrapporten Mailflow

I visningen **Mailflow** kan du se, hvordan Microsofts beskyttelse mod mailtrussel filtrerer indgående og udgående mails i din organisation. Denne visning bruger et vandret flowdiagram (også kaldet et _Sankey-diagram_ ) til at angive oplysninger om det samlede antal mails, og hvordan de konfigurerede funktioner til trusselsbeskyttelse, herunder edge protection, anti-malware, anti-phishing, anti-spam og anti-spoofing, påvirker dette antal.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view.png" alt-text="Visningen Mailflow i statusrapporten Mailflow" lightbox="../../media/mail-flow-status-report-mailflow-view.png":::

Den samlede visning og tabelvisningen Med detaljer kan der filtreres i 90 dage.

Oplysningerne i diagrammet er farvekodet af **EOP** eller **Defender for Office 365** teknologier.

Diagrammet er organiseret i følgende vandrette bånd:

- **Samlet mailbånd** : Denne værdi vises altid først.
- **Kantblok** og **behandlet** bånd:
  - **Edge-blok**: Meddelelser, der er filtreret ved kanten og identificeret som Edge Protection.
  - **Behandlet**: Meddelelser, der håndteres af filtreringsstakken.
- Resultatbånd:
  - **Regelblok**: Meddelelser, der behandles af Exchange regler for mailflow (transportregler).
  - **Malwareblok**: Meddelelser, der identificeres som malware af forskellige filtre.<sup>\*</sup>
  - **Phishblok**: Meddelelser, der er identificeret som phish under behandling af forskellige filtre.<sup>\*</sup>
  - **Spamblok**: Meddelelser, der er identificeret som spam under behandling af forskellige filtre.<sup>\*</sup>
  - **Repræsentationsblok**: Meddelelser registreret som bruger repræsentation eller domæne repræsentation i Defender for Office 365.<sup>\*</sup>
  - **Detonationsblok**: Meddelelser, der registreres under detonation af filer eller URL-adresser af politikker for Pengeskab vedhæftede filer eller politikker for Pengeskab links i Defender for Office 365.<sup>\*</sup>
  - **ZAP fjernet**: Meddelelser, der fjernes med automatisk udrensning på nul timer (ZAP).<sup>\*</sup>
  - **Leveret**: Meddelelser leveret til brugere på grund af en tilladelse.<sup>\*</sup>

Hvis du holder markøren over et vandret bånd i diagrammet, kan du se antallet af relaterede meddelelser.

<sup>\*</sup> Hvis du klikker på dette element, udvides diagrammet, så der vises flere detaljer. Du kan få en beskrivelse af hvert element i de udvidede noder under [Registreringsteknologier](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-details.png" alt-text="Oplysninger om phishingblokering i visningen Mailflow i statusrapporten Mailflow" lightbox="../../media/mail-flow-status-report-mailflow-view-details.png":::

I detaljetabellen under diagrammet vises følgende oplysninger:

- **Dato**
- **Mail i alt**
- **Filtreret kant**
- **Regelmeddelelser**
- **Antimalwareprogram, Pengeskab vedhæftede filer, filtreret regel**
- **DMARC-repræsentation, spoof, phishfiltreret**
- **Detonationsregistrering**
- **Filtreret anti-spam**
- **ZAP er fjernet**
- **Meddelelser, hvor der ikke blev registreret trusler**

Hvis du vælger en række i detaljetabellen, vises en yderligere opdeling af antallet af mails i det viste pop op-vindue med detaljer.

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC)** **Startdato** og **Slutdato**.
- **Retning**: **Udgående** og **indgående**.

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Tilbage på **rapportsiden Mailflowstatus** kan du klikke på **Vis tendenser** for at se tendensgrafer i pop **op-vinduet Mailflowtendenser** , der vises.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-show-trends.png" alt-text="Pop op-vinduet Mailflowtendenser i visningen Mailflow i statusrapporten Mailflow" lightbox="../../media/mail-flow-status-report-mailflow-view-show-trends.png":::

På **rapportsiden Mailflowstatus** skal du klikke på ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksport er** tilgængelig.

## <a name="malware-detections-report"></a>Rapport over malwareregistreringer

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger er tilgængelige i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Rapport over mailventetid

**Rapporten Mailventetid** i Defender for Office 365 indeholder oplysninger om levering af mail og ventetid for detonation i din organisation. Du kan få flere oplysninger under [Rapport over mailventetid](view-reports-for-mdo.md#mail-latency-report).

## <a name="spam-detections-report"></a>Rapport over spamregistreringer

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger er tilgængelige i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="spoof-detections-report"></a>Rapport over spoof registreringer

Rapporten **Spoof-registreringer** viser oplysninger om meddelelser, der blev blokeret eller tilladt på grund af spoofing. Du kan få flere oplysninger om spoofing under [Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

Den samlede visning af rapporten tillader 90 dages filtrering, mens detaljevisningen kun tillader filtrering i ti dage.

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Spoof-registreringer** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/SpoofMailReport>.

:::image type="content" source="../../media/spoof-detections-widget.png" alt-text="Widgetten Spoof detections på siden Mail & samarbejdsrapporter" lightbox="../../media/spoof-detections-widget.png":::

Diagrammet viser følgende oplysninger:

- **Passere**
- **Ikke**
- **SoftPass**
- **Ingen**
- **Andet**

Når du holder markøren over en dag (datapunkt) i diagrammet, kan du se, hvor mange spoofed meddelelser der blev registreret, og hvorfor.

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Resultat**:
  - **Passere**
  - **Ikke**
  - **SoftPass**
  - **Ingen**
  - **Andet**
- **Spoof-type**: **Intern** og **ekstern**

:::image type="content" source="../../media/spoof-detections-report-page.png" alt-text="Rapportsiden Spoof mail på Microsoft 365 Defender-portalen" lightbox="../../media/spoof-detections-report-page.png":::

I detaljetabellen under grafen kan du se følgende oplysninger:

- **Dato**
- **Poofed bruger**
- **Sender infrastruktur**
- **Spoof-type**
- **Resultat**
- **Resultatkode**
- **SPF**
- **DKIM**
- **DMARC**
- **Antal meddelelser**

Du kan få flere oplysninger om resultatkoder for sammensat godkendelse [under Brevhoveder til anti-spam i Microsoft 365](anti-spam-message-headers.md).

På siden **Spoof-registreringer** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

## <a name="submissions-report"></a>Rapport over indsendelser

Rapporten **Indsendelser** viser oplysninger om elementer, som administratorer har rapporteret til Microsoft til analyse. Du kan få flere oplysninger under [Brug indsendelse af administratorer til at sende mistanke om spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Indsendelser** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/adminSubmissionReport>. Hvis du vil gå til [administratorindsendelser på Microsoft 365 Defender-portalen](admin-submission.md), skal du klikke på **Gå til Indsendelser**. Administratorer kan få vist rapporten de sidste 30 dage.

:::image type="content" source="../../media/submissions-report-widget.png" alt-text="Widgetten Indsendelser på siden Mail & samarbejdsrapporter" lightbox="../../media/submissions-report-widget.png":::

Diagrammet viser følgende oplysninger:

- **Ventende**
- **Afsluttet**

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Rapporteret dato**: **Starttidspunkt** og **Sluttidspunkt**
- **Indsendelsestype**:
  - **E-mail**
  - **URL**
  - **Filer**
- **Afsendelses-id**
- **Netværksmeddelelses-id**
- **Afsender**
- **Navn**
- **Sendt af**
- **Årsag til afsendelse**:
  - **Ikke uønsket**
  - **Phish**
  - **Malware**
  - **Spam**
- **Status for scanning igen**:
  - **Ventende**
  - **Afsluttet**

Detaljetabellen under grafen viser de samme oplysninger og har de samme indstillinger for **Gruppér** eller **Tilpas kolonner** som under fanen **Sendt til analyse** under **Mail &** **samarbejdsindsendelser**\>. Du kan få flere oplysninger under [Få vist administratorindsendelser til Microsoft](admin-submission.md#view-admin-submissions-to-microsoft).

På siden **Indsendelser** er knappen **[Eksportér](#export-report)** tilgængelig.

:::image type="content" source="../../media/submissions-report-page.png" alt-text="Rapportsiden Afsendelser på portalen Microsoft 365 Defender" lightbox="../../media/submissions-report-page.png":::

## <a name="threat-protection-status-report"></a>Statusrapport om trusselsbeskyttelse

Statusrapporten **trusselsbeskyttelse** er tilgængelig i både EOP og Defender for Office 365, men rapporterne indeholder forskellige data. EOP-kunder kan f.eks. få vist oplysninger om malware, der er registreret i en mail, men ikke oplysninger om skadelige filer, der er registreret af [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Rapporten indeholder antallet af mails med skadeligt indhold, f.eks. filer eller webadresser (URL-adresser), der blev blokeret af antimalwareprogrammet, [ZAP (automatisk fjernelse på nul timer)](zero-hour-auto-purge.md) og Defender for Office 365 funktioner som f.eks. [Pengeskab Links](safe-links.md), [Pengeskab Vedhæftede filer](safe-attachments.md) og [repræsentationsbeskyttelsesfunktioner i anti-phishing-politikker](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Du kan bruge disse oplysninger til at identificere tendenser eller afgøre, om organisationens politikker skal justeres.

**Bemærk**! Det er vigtigt at forstå, at hvis en meddelelse sendes til fem modtagere, tæller vi den som fem forskellige meddelelser og ikke én meddelelse.

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Status for trusselsbeskyttelse** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne en af følgende URL-adresser:

- Defender for Office 365:<https://security.microsoft.com/reports/TPSAggregateReportATP>
- EOP: <https://security.microsoft.com/reports/TPSAggregateReport>

:::image type="content" source="../../media/threat-protection-status-report-widget.png" alt-text="Widgetten Status for trusselsbeskyttelse på siden Mail & samarbejdsrapporter" lightbox="../../media/threat-protection-status-report-widget.png":::

Diagrammet viser som standard data for de seneste 7 dage. Hvis du klikker på **Filtrer** på **rapportsiden Trusselsbeskyttelsesstatus** , kan du vælge et 90-dages datointerval (prøveabonnementer kan være begrænset til 30 dage). Detaljetabellen tillader filtrering i 30 dage.

De tilgængelige visninger er beskrevet i følgende afsnit.

### <a name="view-data-by-overview"></a>Få vist data efter oversigt

:::image type="content" source="../../media/threat-protection-status-report-overview-view.png" alt-text="Visningen Oversigt i rapporten over status for trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-overview-view.png":::

I visningen **Vis data efter oversigt** vises følgende registreringsoplysninger i diagrammet:

- **Mailmalware**
- **Mail-phish**
- **Mail spam**
- **Indholdsmalware**

Der er ingen detaljetabel tilgængelig under diagrammet.

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**.
- **Registrering**:
  - **Mailmalware**
  - **Mail-phish**
  - **Mail spam**
  - **Indholdsmalware**
- **Beskyttet af**: **MDO** (Defender for Office 365) og **EOP**.
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti). Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Sikre vedhæftede filer**
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

### <a name="view-data-by-email--phish-and-chart-breakdown-by-detection-technology"></a>Få vist data efter mail-phish \> og diagramopdeling efter registreringsteknologi

:::image type="content" source="../../media/threat-protection-status-report-phishing-detection-tech-view.png" alt-text="Teknologivisningen Registrering for phishing-mail i statusrapporten Trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-phishing-detection-tech-view.png":::

> [!NOTE]
> Fra maj 2021 blev phishing-registreringer i mails opdateret til at omfatte **vedhæftede filer i meddelelser** , der indeholder phishing-URL-adresser. Denne ændring kan flytte noget af registreringsmængden ud af visningen **Vis data via mailmalware \>** og ind i visningen **Vis data via mail-phish\>**. Med andre ord kan vedhæftede filer i meddelelser med phishing-URL-adresser, der traditionelt er identificeret som malware, i stedet identificeres som phishing.

I visningen **Vis data efter mail-phish \>** og **diagramopdeling efter registreringsteknologi** vises følgende oplysninger i diagrammet:

- **Skadeligt omdømme**<sup>\*</sup> for URL-adresse: Skadelig URL-omdømme, der genereres af Defender for Office 365 detonationer i andre Microsoft 365 kunder.
- **Avanceret filter**: Phishing-signaler baseret på maskinel indlæring.
- **Generelt filter**: Phishingsignaler baseret på analytikerregler.
- **Spoof intra-org**: Afsenderen forsøger at spoof modtagerdomænet.
- **Spoof eksternt domæne**: Afsenderen forsøger at spoof et andet domæne.
- **Spoof DMARC**: DMARC-godkendelsesfejl i meddelelser.
- **Repræsentationsmærke**: Repræsentation af velkendte mærker baseret på afsendere.
- **Registrering af blandet analyse**
- **Filomdømme**
- **Matchende fingeraftryk**
- **URL-detonationsomdømme**<sup>\*</sup>
- **URL-detonation**<sup>\*</sup>
- **Repræsentationsbruger**<sup>\*</sup>
- **Repræsentationsdomæne**<sup>\*</sup>: Repræsentation af domæner, som kunden ejer eller definerer.
- **Repræsentation af postkasseintelligens**<sup>\*</sup>: Repræsentation af brugere, der er defineret af administratoren eller lært via postkasseintelligens.
- **Fildeonation**<sup>\*</sup>
- **Omdømme for fildeonation**<sup>\*</sup>
- **Kampagne**<sup>\*</sup>

<sup>\*</sup>kun Defender for Office 365

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Detection**: De samme værdier som i diagrammet.
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Sikre vedhæftede filer**
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**
- **Politiknavn (kun tabelvisning med detaljer)**: **Alle** eller den angivne politik.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="view-data-by-email--spam-and-chart-breakdown-by-detection-technology"></a>Få vist data efter mailspam \> og diagramopdeling efter registreringsteknologi

:::image type="content" source="../../media/threat-protection-status-report-spam-detection-tech-view.png" alt-text="Teknologivisningen Registrering for spam i statusrapporten trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-spam-detection-tech-view.png":::

I visningen **Vis data efter mailspam \>** og **diagramopdeling efter teknologivisning til registrering** vises følgende oplysninger i diagrammet:

- **Skadeligt omdømme for URL-adresse**
- **Avanceret filter**
- **Generelt filter**
- **Registrering af blandet analyse**: Flere filtre bidrog til dommen for meddelelsen.
- **Matchning af fingeraftryk**: Meddelelsen var markeret som ugyldig på grund af tidligere meddelelser.
- **Domæneomdømme**: Denne meddelelse blev betragtet som spam baseret på afsenderens domæneomdømme.
- **Masse**: Elementer, der er registreret som overskrider masseindstillingen for brugeren.
- **IP-omdømme**: Meddelelsen blev betragtet som spam baseret på det afsendende IP-adresseomdømme.

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Detection**: De samme værdier som i diagrammet.
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Sikre vedhæftede filer**
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**
- **Politiknavn (kun tabelvisning med detaljer)**: **Alle** eller den angivne politik.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="view-data-by-email--malware-and-chart-breakdown-by-detection-technology"></a>Få vist data efter mailmalware \> og diagramopdeling efter registreringsteknologi

:::image type="content" source="../../media/threat-protection-status-report-malware-detection-tech-view.png" alt-text="Teknologivisningen Detection for malware i statusrapporten trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-malware-detection-tech-view.png":::

> [!NOTE]
> Fra maj 2021 blev malwareregistreringer i mails opdateret til at inkludere **skadelige URL-adresser** i vedhæftede filer i meddelelser. Denne ændring kan flytte noget af registreringsmængden ud af visningen **Vis data via mail-phish \>** og til visningen **Vis data via mailmalware\>**. Med andre ord kan skadelige URL-adresser i vedhæftede filer i meddelelser, der traditionelt er identificeret som phishing, i stedet blive identificeret som malware.

I visningen **Vis data efter mailmalware \>** og **diagramopdeling efter registreringsteknologi** vises følgende oplysninger i diagrammet:

- **Fil detonation**<sup>\*</sup>: Registrering af Pengeskab vedhæftede filer.
- **Omdømme for fildeonation**<sup>\*</sup>: Alt skadeligt filomdømme, der genereres af Defender for Office 365 detonationer.
- **Filomdømme**
- **Antimalwareprogram**<sup>\*</sup>: Registrering fra antimalwareprogrammer.
- **Filtype for antimalwarepolitik**: Dette er mails, der er filtreret ud på grund af den type skadelig fil, der er identificeret i meddelelsen.
- **Skadeligt omdømme for URL-adresse**<sup>\*</sup>
- **URL-detonation**<sup>\*</sup>
- **URL-detonationsomdømme**<sup>\*</sup>
- **Kampagne**<sup>\*</sup>

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Detection**: De samme værdier som i diagrammet.
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Sikre vedhæftede filer**
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**
- **Politiknavn (kun tabelvisning med detaljer)**: **Alle** eller den angivne politik.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På **sidenThreat-status for beskyttelse** skal du klikke på ![ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="chart-breakdown-by-policy-type"></a>Diagramopdeling efter politiktype

:::image type="content" source="../../media/threat-protection-status-report-phishing-policy-type-view.png" alt-text="Visningen Politiktype for phishingmail, spammail eller malware i statusrapporten Trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-phishing-policy-type-view.png":::

I **visningsdata efter mail-phish\>**, **vis data efter mailspam \>** eller **Vis data efter visning af malware i mail \>** viser valg **af diagramopdeling efter politiktype** følgende oplysninger i diagrammet:

- **Antimalware**
- **Pengeskab vedhæftede filer**<sup>\*</sup>
- **Anti-phish**
- **Anti-spam**
- **Regel for mailflow** (også kendt som en transportregel)
- **Andre**

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Registrering**:
  - **Skadeligt omdømme**<sup>\*</sup> for URL-adresse: Skadelig URL-omdømme, der genereres af Defender for Office 365 detonationer i andre Microsoft 365 kunder.
  - **Avanceret filter**: Phishing-signaler baseret på maskinel indlæring.
  - **Generelt filter**: Phishingsignaler baseret på analytikerregler.
  - **Spoof intra-org**: Afsenderen forsøger at spoof modtagerdomænet.
  - **Spoof eksternt domæne**: Afsenderen forsøger at spoof et andet domæne.
  - **Spoof DMARC**: DMARC-godkendelsesfejl i meddelelser.
  - **Repræsentationsmærke**: Repræsentation af velkendte mærker baseret på afsendere.
  - **Registrering af blandet analyse**
  - **Filomdømme**
  - **Matchende fingeraftryk**
  - **URL-detonationsomdømme**<sup>\*</sup>
  - **URL-detonation**<sup>\*</sup>
  - **Repræsentationsbruger**<sup>\*</sup>
  - **Repræsentationsdomæne**<sup>\*</sup>: Repræsentation af domæner, som kunden ejer eller definerer.
  - **Repræsentation af postkasseintelligens**<sup>\*</sup>: Repræsentation af brugere, der er defineret af administratoren eller lært via postkasseintelligens.
  - **Fildeonation**<sup>\*</sup>
  - **Omdømme for fildeonation**<sup>\*</sup>
  - **Kampagne**<sup>\*</sup>
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Sikre vedhæftede filer**
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**
- **Politiknavn (kun tabelvisning med detaljer)**: **Alle** eller den angivne politik.
- **Modtagere**

<sup>\*</sup>kun Defender for Office 365

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="chart-breakdown-by-delivery-status"></a>Diagramopdeling efter Leveringsstatus

:::image type="content" source="../../media/threat-protection-status-report-phishing-delivery-status-view.png" alt-text="Visningen Leveringsstatus for phishing-mail og malware-mail i statusrapporten Trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-phishing-delivery-status-view.png":::

I **visningsdataene efter mail-phish\>**, **vis data efter mailspam \>** eller **Vis data efter visning af mailmalware \>** viser valg **af diagramopdeling efter Leveringsstatus** følgende oplysninger i diagrammet:

- **Hostet postkasse: Indbakke**
- **Hostet postkasse: Uønsket**
- **Hostet postkasse: Brugerdefineret mappe**
- **Hostet postkasse: Slettede elementer**
- **Videresendt**
- **Server i det lokale miljø: Leveret**
- **Karantæne**
- **Levering mislykkedes**
- **Faldt**

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Registreringsteknologi**
- **Leveringsstatus**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Registrering**:
  - **Skadeligt omdømme**<sup>\*</sup> for URL-adresse: Skadelig URL-omdømme, der genereres af Defender for Office 365 detonationer i andre Microsoft 365 kunder.
  - **Avanceret filter**: Phishing-signaler baseret på maskinel indlæring.
  - **Generelt filter**: Phishingsignaler baseret på analytikerregler.
  - **Spoof intra-org**: Afsenderen forsøger at spoof modtagerdomænet.
  - **Spoof eksternt domæne**: Afsenderen forsøger at spoof et andet domæne.
  - **Spoof DMARC**: DMARC-godkendelsesfejl i meddelelser.
  - **Repræsentationsmærke**: Repræsentation af velkendte mærker baseret på afsendere.
  - **Registrering af blandet analyse**
  - **Filomdømme**
  - **Matchende fingeraftryk**
  - **URL-detonationsomdømme**<sup>\*</sup>
  - **URL-detonation**<sup>\*</sup>
  - **Repræsentationsbruger**<sup>\*</sup>
  - **Repræsentationsdomæne**<sup>\*</sup>: Repræsentation af domæner, som kunden ejer eller definerer.
  - **Repræsentation af postkasseintelligens**<sup>\*</sup>: Repræsentation af brugere, der er defineret af administratoren eller lært via postkasseintelligens.
  - **Fildeonation**<sup>\*</sup>
  - **Omdømme for fildeonation**<sup>\*</sup>
  - **Kampagne**<sup>\*</sup>
- **Beskyttet af**: **MDO** (Defender for Office 365) eller **EOP**
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Sikre vedhæftede filer**
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**
- **Politiknavn (kun tabelvisning med detaljer)**: **Alle** eller den angivne politik.
- **Modtagere**

<sup>\*</sup>kun Defender for Office 365

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="view-data-by-content--malware"></a>Få vist data efter indholdsmalware \>

:::image type="content" source="../../media/threat-protection-status-report-content-malware-view.png" alt-text="Visningen Indholdsmalware i statusrapporten trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-content-malware-view.png":::

I visningen **Vis data efter indholdsmalware \>** vises følgende oplysninger i diagrammet for Microsoft Defender for Office 365 organisationer:

- **Antimalwareprogram**: Skadelige filer, der er registreret i SharePoint, OneDrive og Microsoft Teams af den [indbyggede virusregistrering i Microsoft 365](virus-detection-in-spo.md).
- **MDO-detonation**: Skadelige filer, der registreres af [Pengeskab Vedhæftede filer til SharePoint, OneDrive og Microsoft Teams](mdo-for-spo-odb-and-teams.md).
- **Filomdømme**

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato (UTC)**
- **Navn på vedhæftet fil**
- **Arbejdsbyrde**
- **Registreringsteknologi**
- **Filstørrelse**
- **Seneste ændring af bruger**

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Detection**: **Antimalwareprogram**, **MDO-detonation** og **detonation af filer**
- **Arbejdsbelastning**: **Teams**, **SharePoint** og **OneDrive**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

### <a name="view-data-by-system-override-and-chart-breakdown-by-reason"></a>Få vist data efter systemtilsidesættelse og diagramopdeling efter årsag

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png" alt-text="Visningen Meddelelses tilsidesættelse og diagramopdeling efter årsag i statusrapporten Trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png":::

I visningen **Vis data efter systemtilsidesættelse** og **Diagramopdeling efter årsag** vises følgende oplysninger om årsag til tilsidesættelse i diagrammet:

- **Spring over i det lokale miljø**
- **TILLAD IP**
- **Exchange transportregel** (regel for mailflow)
- **Organisationen tillader afsendere**
- **Organisationens tilladte domæner**
- **ZAP er ikke aktiveret**
- **Afsender af Pengeskab bruger**
- **Brugerens Pengeskab domæne**
- **Phishing-simulering**: Du kan få flere oplysninger under [Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).
- **Tredjepartsfilter**

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Systemtilsidesættelse**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Årsag**: De samme værdier som diagrammet.
- **Leveringsplacering**: **Mappen Uønsket mail er ikke aktiveret** eller **SecOps-postkassen**.
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**: **Alle**
- **Politiknavn (kun detaljetabelvisning)**: **Alle**
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen Eksport er](#export-report)** tilgængelig.

### <a name="view-data-by-system-override-and-chart-breakdown-by-delivery-location"></a>Få vist data efter Systemtilsidesættelse og Diagramopdeling efter Leveringsplacering

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png" alt-text="Visningen Meddelelses tilsidesættelse og diagramopdeling efter Leveringsplacering i statusrapporten Trusselsbeskyttelse" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png":::

I visningen **Vis data efter systemtilsidesættelse** og **Diagramopdeling efter Leveringsplacering** vises følgende oplysninger om årsag til tilsidesættelse i diagrammet:

- **Mappen Uønsket mail er ikke aktiveret**
- **SecOps-postkasse**: Du kan få flere oplysninger under [Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato**
- **Emne**
- **Afsender**
- **Modtagere**
- **Systemtilsidesættelse**
- **Afsenders IP**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du klikker på **Filtrer**, er følgende filtre tilgængelige:

- **Dato (UTC)** **Startdato** og **Slutdato**
- **Grund**
  - **Spring over i det lokale miljø**
  - **TILLAD IP**
  - **Exchange transportregel** (regel for mailflow)
  - **Organisationen tillader afsendere**
  - **Organisationens tilladte domæner**
  - **ZAP er ikke aktiveret**
  - **Afsender af Pengeskab bruger**
  - **Brugerens Pengeskab domæne**
  - **Phishing-simulering**: Du kan få flere oplysninger under [Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser](configure-advanced-delivery.md).
  - **Tredjepartsfilter**
- **Leveringsplacering**: **Mappen Uønsket mail er ikke aktiveret** eller **SecOps-postkassen**.
- **Retning**:
  - **Alle**
  - **Indgående**
  - **Udgående**
- **Mærke**: **Alle** eller den angivne brugerkode (herunder prioritetskonti). Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).
- **Domæne**: **Hele** eller et [accepteret domæne](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Politiktype**:
  - **Alle**
  - **Antimalware**
  - **Pengeskab vedhæftede filer**<sup>\*</sup>
  - **Anti-phish**
  - **Anti-spam**
  - **Regel for mailflow** (transportregel)
  - **Andre**
- **Politiknavn (kun detaljetabelvisning)**: **Alle**
- **Modtagere**

<sup>\*</sup>kun Defender for Office 365

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Status for trusselsbeskyttelse** er ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen Eksport er](#export-report)** tilgængelig.

## <a name="top-malware-report"></a>Toprapport over malware

Den **øverste malware** rapport viser de forskellige former for malware, der blev opdaget af [anti-malware beskyttelse i EOP](anti-malware-protection.md).

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Den mest populære malware** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/TopMalware>.

:::image type="content" source="../../media/top-malware-report-widget.png" alt-text="Den mest populære malwarewidget på siden Mail & samarbejdsrapporter" lightbox="../../media/top-malware-report-widget.png":::

Når du holder markøren over en kile i cirkeldiagrammet, kan du se navnet på en slags malware, og hvor mange meddelelser der blev registreret som havende denne malware.

På rapportsiden **Top malware** vises en større version af cirkeldiagrammet. I detaljetabellen under diagrammet vises følgende oplysninger:

- **Mest populære malware**
- **Tælle**

Hvis du klikker på **Filtrer**, kan du angive et datointerval med **startdato** og **slutdato**.

På siden **Top malware** skal du klikke på ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Ikonet Opret tidsplan](#schedule-report)** og ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](#export-report)** er tilgængelige.

:::image type="content" source="../../media/top-malware-report-view.png" alt-text="Den mest populære rapportvisning for malware" lightbox="../../media/top-malware-report-view.png":::

## <a name="top-senders-and-recipients-report"></a>Rapport over de vigtigste afsendere og modtagere

Rapporten **Over de vigtigste afsendere og modtagere** er tilgængelig både i EOP og Defender for Office 365, men rapporterne indeholder forskellige data. EOP-kunder kan f.eks. få vist oplysninger om de vigtigste modtagere af malware, spam og phishing (spoofing), men ikke oplysninger om malware, der er registreret af [Pengeskab Vedhæftede filer](safe-attachments.md) eller phishing registreret af [repræsentationsbeskyttelse](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

De **øverste afsendere og modtagere** viser de vigtigste afsendere af meddelelser i din organisation samt de vigtigste modtagere af meddelelser, der blev registreret af EOP og Defender for Office 365 beskyttelsesfunktioner. Rapporten viser som standard data for den seneste uge, men data er tilgængelige for de sidste 90 dage.

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **rapporten Over de vigtigste afsendere og modtagere** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne en af følgende URL-adresser:

- Defender for Office 365:<https://security.microsoft.com/reports/TopSenderRecipientsATP>
- EOP: <https://security.microsoft.com/reports/TopSenderRecipient>

:::image type="content" source="../../media/top-senders-and-recipients-widget.png" alt-text="Widgetten Top afsendere og modtagere på dashboardet Rapporter" lightbox="../../media/top-senders-and-recipients-widget.png":::

Når du holder markøren over en kile i cirkeldiagrammet, kan du se antallet af meddelelser for afsenderen eller modtageren.

På siden **Øverste afsendere og modtagere** vises der en større version af cirkeldiagrammet. Følgende diagrammer er tilgængelige:

- **Vis data for de mest populære afsendere af mails** (dette er standardvisningen)
- **Vis data for de vigtigste postmodtagere**
- **Vis data for de vigtigste spammodtagere**
- **Vis data for de mest populære malwaremodtagere** (EOP)
- **Vis data til de mest populære phishing-modtagere**
- **Vis data for de mest populære malwaremodtagere (MDO)**
- **Vis data for de vigtigste phishmodtagere (MDO)**

Dataene ændres på baggrund af dit valg.

Når du holder markøren over en kile i cirkeldiagrammet, kan du se antallet af meddelelser for den pågældende afsender eller modtager.

Detaljetabellen under grafen viser afsendere eller modtagere og antallet af meddelelser baseret på den valgte visning.

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge **Startdato** og **Slutdato**. Brugerne kan også filtrere efter brugerkoder. 

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

På siden **Top afsendere og modtagere** skal du klikke på ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **Knappen Eksport er** tilgængelig.

:::image type="content" source="../../media/top-senders-and-recipients-report-view.png" alt-text="Visningen Vis data for de vigtigste afsendere af mails i rapporten Over de vigtigste afsendere og modtagere" lightbox="../../media/top-senders-and-recipients-report-view.png":::

## <a name="url-protection-report"></a>URL-beskyttelsesrapport

**URL-beskyttelsesrapport** er kun tilgængelig i Microsoft Defender for Office 365. Du kan få flere oplysninger under [URL-beskyttelsesrapport](view-reports-for-mdo.md#url-protection-report).

## <a name="user-reported-messages-report"></a>Rapport over brugerrapporterede meddelelser

> [!IMPORTANT]
> Hvis rapporten over **rapporterede brugermeddelelser** skal fungere korrekt, **skal overvågningslogføring være aktiveret** for dit Microsoft 365 miljø. Dette gøres typisk af en person, der har rollen Overvågningslogge tildelt i Exchange Online. Du kan finde flere oplysninger under [Slå søgning i Microsoft 365 overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

Rapporten **over brugerrapporterede meddelelser** viser oplysninger om mails, som brugerne har rapporteret som uønsket mail, phishing-forsøg eller god mail ved hjælp af [tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md) eller [tilføjelsesprogram til rapport phishing](enable-the-report-phish-add-in.md).

Hvis du vil have vist rapporten på Microsoft 365 Defender-portalen, skal du gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **Brugerrapporterede meddelelser** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/userSubmissionReport>. Hvis du vil gå til [administratorindsendelser på Microsoft 365 Defender-portalen](admin-submission.md), skal du klikke på **Gå til Indsendelser**.

:::image type="content" source="../../media/user-reported-messages-widget.png" alt-text="Widgetten Meddelelser, der er rapporteret af brugeren, på siden Mail & samarbejdsrapporter" lightbox="../../media/user-reported-messages-widget.png":::

Du kan filtrere både diagrammet og detaljetabellen ved at klikke på **Filtrer** og vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Rapporteret dato**: **Starttidspunkt** og **Sluttidspunkt**
- **Rapporteret af**
- **Mailemne**
- **Meddelelse rapporteret id**
- **Netværksmeddelelses-id**
- **Afsender**
- **Rapporteret årsag**
  - **Ikke uønsket**
  - **Phish**
  - **Spam**
- **Phish-simulering**: **Ja** eller **Nej**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Hvis du vil gruppere posterne, skal du klikke på **Gruppér** og vælge en af følgende værdier på rullelisten:

- **Ingen**
- **Grund**
- **Afsender**
- **Rapporteret af**
- **Genscan resultat**
- **Phish-simulering**

:::image type="content" source="../../media/user-reported-messages-report.png" alt-text="Rapporten over brugerrapporterede meddelelser" lightbox="../../media/user-reported-messages-report.png":::

I detaljetabellen under grafen kan du se følgende oplysninger:

- **Mailemne**
- **Rapporteret af**
- **Rapporteret dato**
- **Afsender**
- **Rapporteret årsag**
- **Genscan resultat**
- **Mærker**: Du kan få flere oplysninger om brugerkoder under [Brugerkoder](user-tags.md).

Hvis du vil sende en meddelelse til Microsoft til analyse, skal du vælge meddelelsesposten i tabellen, klikke på **Send til Microsoft til analyse** og derefter vælge en af følgende værdier på rullelisten:

- **Rapport ren**
- **Rapport phishing**
- **Rapportér malware**
- **Rapportér spam**'
- **Udløs undersøgelse** (Defender for Office 365)

På siden **Brugerrapporterede meddelelser** er ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen Eksport er](#export-report)** tilgængelig.

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Hvilke tilladelser er nødvendige for at få vist disse rapporter?

Hvis du vil have vist og bruge de rapporter, der er beskrevet i denne artikel, skal du være medlem af en af følgende rollegrupper på Microsoft 365 Defender portalen:

- **Organisationsadministration**
- **Sikkerhedsadministrator**
- **Sikkerhedslæser**
- **Global læser**

Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

**Bemærk**! Hvis du føjer brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration får brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Hvad sker der, hvis rapporterne ikke viser data?

Hvis du ikke får vist data i dine rapporter, skal du kontrollere de filtre, du bruger, og dobbelttjekke, at dine politikker er konfigureret korrekt. Du kan få mere at vide under [Beskyt mod trusler](protect-against-threats.md).

## <a name="schedule-report"></a>Planlæg rapport

1. På hovedsiden for den specifikke rapport skal du klikke på ![Ikonet Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **Opret tidsplan**.
2. Guiden **Opret planlagt rapport** åbnes. Gennemse eller tilpas værdien **Navn** på siden **Navngiv planlagt rapport**, og klik derefter på **Næste**.
3. Konfigurer følgende indstillinger på siden **Angiv indstillinger** :
   - **Hyppighed**: Vælg en af følgende værdier:
     - **Ugentligt** (standard)
     - **Månedlige**
   - **Startdato**: Når oprettelsen af rapporten starter. Standardværdien er i dag.
   - **Udløbsdato**: Når oprettelsen af rapporten slutter. Standardværdien er et år fra i dag.

   Klik på **Næste**, når du er færdig.

4. Vælg modtagere til rapporten på siden **Modtagere** . Standardværdien er din mailadresse, men du kan tilføje andre.

   Klik på **Næste**, når du er færdig.

5. Gennemse dine valg på siden **Gennemse** . Du kan klikke på knappen **Tilbage** eller linket **Rediger** i de respektive sektioner for at foretage ændringer.

   Klik på **Send**, når du er færdig.

### <a name="managed-existing-scheduled-reports"></a>Administrerede eksisterende planlagte rapporter

Hvis du vil administrere planlagte rapporter, som du allerede har oprettet, skal du gøre følgende:

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Rapporter** \> udvide **Mail & samarbejde** \> vælge **Administrer tidsplaner**.

   Hvis du vil gå direkte til siden **Administrer tidsplaner** , skal du bruge <https://security.microsoft.com/ManageSubscription>.

2. På siden **Administrer tidsplaner** vises følgende oplysninger for hver planlagt rapport:
   - **Startdato for tidsplan**
   - **Tidsplannavn**
   - **Rapporttype**
   - **Frekvens**
   - **Senest sendt**

   Find den eksisterende planlagte rapport, som du vil ændre.

3. Når du har valgt den planlagte rapport, skal du udføre en af følgende handlinger i det detaljerede pop op-vindue, der åbnes:
   - **Rediger navn**: Klik på denne knap, rediger navnet på rapporten i det pop op-vindue, der vises, og klik derefter på **Gem**.
   - **Slet tidsplan**: Klik på denne knap, læs den advarsel, der vises (tidligere rapporter kan ikke længere downloades), og klik derefter på **Gem**.
   - Afsnittet **Planlæg detaljer**: Klik på **Rediger indstillinger** for at ændre følgende indstillinger:
     - **Hyppighed**: **Ugentligt** eller **månedligt**
     - **Startdato**
     - **Udløbsdato**

     Klik på **Gem**, når du er færdig.

   - Sektionen **Modtagere**: Klik på **Rediger modtagere** for at tilføje eller fjerne modtagere for den planlagte rapport. Når du er færdig, skal du klikke på **Gem**

   Klik på **Luk**, når du er færdig.

## <a name="request-report"></a>Anmod om rapport

1. Klik på Ikonet Anmod om rapport på ![hovedsiden for den specifikke rapport.](../../media/m365-cc-sc-download-icon.png) **Anmod om rapport**.
2. Guiden **Opret rapport efter behov** åbnes. Gennemse eller tilpas værdien **Navn** **på rapportsiden Navn efter behov**, og klik derefter på **Næste**.
3. Gennemse eller konfigurer følgende indstillinger på siden **Angiv indstillinger** :
   - **Startdato**: Når oprettelsen af rapporten starter. Standardværdien er for en måned siden.
   - **Udløbsdato**: Når oprettelsen af rapporten slutter. Standardværdien er i dag.

   Klik på **Næste**, når du er færdig.

4. Vælg modtagere til rapporten på siden **Modtagere** . Standardværdien er din mailadresse, men du kan tilføje andre.

   Klik på **Næste**, når du er færdig.

5. Gennemse dine valg på siden **Gennemse** . Du kan klikke på knappen **Tilbage** eller linket **Rediger** i de respektive sektioner for at foretage ændringer.

   Klik på **Send**, når du er færdig.

6. Når rapporten er blevet oprettet, føres du til siden **Ny rapport oprettet efter behov** , hvor du kan klikke på **Opret en anden rapport** eller **Udført**.

   Rapporten er også tilgængelig på siden **Rapporter til download** , som beskrevet i næste afsnit.

### <a name="download-reports"></a>Download rapporter

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Rapporter** \> udvide **Mail & samarbejde** \> vælge **Rapporter til download**.

   Hvis du vil gå direkte til siden **Rapporter til download** , skal du bruge <https://security.microsoft.com/ReportsForDownload>.

2. På siden **Rapporter til download** vises følgende oplysninger for hver tilgængelig rapport:
   - **Startdato**
   - **Navn**
   - **Rapporttype**
   - **Senest sendt**
   - **Retning**

   Find og vælg den rapport, du vil downloade.

## <a name="export-report"></a>Eksportér rapport

Klik på Ikonet Eksportér på ![hovedsiden for den specifikke rapport.](../../media/m365-cc-sc-download-icon.png) **Eksportér** (hvis linket er tilgængeligt). Der vises et pop op-vindue til **eksportbetingelser** , hvor du kan konfigurere følgende indstillinger:

- **Vælg en visning, der skal eksporteres**: Vælg en af følgende værdier:
  - **Oversigt**: Data er tilgængelige for de sidste 90 dage.
  - **Detaljer**: Data er tilgængelige for de sidste 30 dage.
- **Dato (UTC):****Startdato** og **Slutdato**.

Når du er færdig med at konfigurere filtrene, skal du klikke på **Eksportér**. I den dialogboks, der åbnes, kan du vælge at åbne filen, gemme filen eller huske markeringen.

Hver eksporteret .csv fil er begrænset til 150.000 rækker. Hvis dataene indeholder mere end 150.000 rækker, oprettes der flere .csv filer.

## <a name="related-topics"></a>Relaterede emner

[Beskyttelse mod spam og antimalware i EOP](anti-spam-and-anti-malware-protection.md)

[Intelligente rapporter og indsigter på Microsoft 365 Defender-portalen](reports-and-insights-in-security-and-compliance.md)

[Få vist mailflowrapporter på Microsoft 365 Defender-portalen](view-mail-flow-reports.md)

[Få vist rapporter for Defender for Office 365](view-reports-for-mdo.md)
