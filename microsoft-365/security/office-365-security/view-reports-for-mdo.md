---
title: Få vist Defender for Office 365-rapporter
f1.keywords:
- CSH
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
ms.assetid: e47e838c-d99e-4c0b-b9aa-e66c4fae902f
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorer kan få mere at vide om, hvordan de finder og bruger de Defender for Office 365 rapporter, der er tilgængelige på Microsoft 365 Defender-portalen.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 08fd6e2fed34296b42fb3b12bec9b5b2b4cb91f8
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535840"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>Få vist Defender for Office 365 rapporter på Microsoft 365 Defender-portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender for Office 365 organisationer (f.eks. Microsoft 365 E5 abonnementer eller Microsoft Defender for Office 365 Plan 1 eller Microsoft Defender for Office 365 Plan 2-tilføjelsesprogrammer) indeholder en række sikkerhedsrelaterede rapporter. Hvis du har de [nødvendige tilladelser](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports), kan du få vist og downloade disse rapporter på Microsoft 365 Defender-portalen.

## <a name="view-and-download-reports"></a>Få vist og download rapporter

### <a name="view-reports"></a>Få vist rapporter

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail i rapporter** \> **& samarbejde** \> **Mail & samarbejdsrapporter**. Hvis du vil gå direkte til siden **Mail & samarbejdsrapporter** , skal du bruge <https://security.microsoft.com/emailandcollabreport>.

1. Vælg den rapport, du vil have vist, og vælg derefter **Vis detaljer**.

### <a name="download-reports"></a>Download rapporter

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **ReportsEmail** >  **& collaboration** \> **Reports til download**. Hvis du vil gå direkte til siden **Rapporter til download** , skal du bruge <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="Siden Mail & samarbejdsrapporter på Microsoft 365 Defender-portalen" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> Mailsikkerhedsrapporter, der ikke kræver Defender for Office 365, er beskrevet i [Få vist mailsikkerhedsrapporter på Microsoft 365 Defender-portalen](view-email-security-reports.md).
>
> Rapporter, der er relateret til mailflow, findes nu i Exchange Administration (EAC). Du kan få flere oplysninger om disse rapporter [under Mailflowrapporter i det nye Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>rapport over filtyper for vedhæftede filer Pengeskab

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger er tilgængelige i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>Pengeskab meddelelsesdispositionsrapport for vedhæftede filer

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger er tilgængelige i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Rapport over mailventetid

Rapporten **Mailventetid** viser dig en samlet visning af den maillevering og detonationstid, der opleves i din organisation. Leveringstiderne for post i tjenesten påvirkes af en række faktorer, og den absolutte leveringstid i sekunder er ofte ikke en god indikator for succes eller et problem. En langsom leveringstid på én dag kan betragtes som en gennemsnitlig leveringstid på en anden dag eller omvendt. Dette forsøger at kvalificere levering af meddelelser baseret på statistiske data om de observerede leveringstider for andre meddelelser.

Ventetiden på klientsiden og netværket er ikke inkluderet.

Hvis du vil have vist rapporten, skal du åbne Microsoft 365 Defender-portalen på <https://security.microsoft.com>, gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. Hvis du vil gå direkte til siden **Mail & samarbejdsrapporter** , skal du bruge <https://security.microsoft.com/emailandcollabreport>.

På siden **Mail & samarbejdsrapporter** skal du finde **rapporten Mailventetid** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du bruge <https://security.microsoft.com/mailLatencyReport>.

:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="Widgetten Mailventetidsrapport på siden Mail & samarbejdsrapporter" lightbox="../../media/mail-latency-report-widget.png":::

På **rapportsiden Mailventetid** er følgende faner tilgængelige på **rapportsiden Mailventetid** :

- **50. fraktil**: Dette er midt for leveringstider for meddelelser. Du kan betragte denne værdi som en gennemsnitlig leveringstid. Denne fane er valgt som standard.
- **90. fraktil**: Dette angiver en høj ventetid for levering af meddelelser. Det tog kun 10 % af meddelelserne længere tid at levere end denne værdi.
- **99. fraktil**: Dette angiver den højeste ventetid for meddelelseslevering.

Uanset hvilken fane du vælger, vises meddelelser organiseret i følgende kategorier i diagrammet:

- **Samlede**
- **Detonation**

Når du peger på en kategori i diagrammet, kan du se en opdeling af ventetiden i hver kategori.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="Visningen 50. fraktil i rapporten Mailventetid" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

Hvis du klikker på **Filtrer**, kan du filtrere både diagrammet og detaljetabellen efter følgende værdier:

- **Dato (UTC):****Startdato** og **Slutdato**
- **Meddelelsesvisning**: En af følgende værdier:
  - **Alle meddelelser**
  - **Deonerede meddelelser**: En af følgende værdier:
    - **Indbygget detonation**: Indeholder meddelelser, der er fuldt testet før levering.
    - **Asynkron sprængning**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

I detaljetabellen under diagrammet er følgende oplysninger tilgængelige:

- **Dato (UTC)**
- **Latency**
- **Antal meddelelser**
- **50. fraktil**
- **90. percentil**
- **99. fraktil**

På hovedrapportsiden er ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen Eksport er](view-email-security-reports.md#export-report)** tilgængelig.

## <a name="threat-protection-status-report"></a>Statusrapport om trusselsbeskyttelse

**Statusrapporten trusselsbeskyttelse** er en enkelt visning, der samler oplysninger om skadeligt indhold og skadelig mail, der registreres og blokeres af [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) og Microsoft Defender for Office 365. Du kan få flere oplysninger under [Rapport over status for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>Rapport over de vigtigste afsendere og modtagere

Rapporten **Top afsendere og modtagere** viser de vigtigste modtagere for EOP og beskyttelsesfunktionerne Defender for Office 365. Du kan få flere oplysninger i [Rapporten over de vigtigste afsendere og modtagere](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>URL-beskyttelsesrapport

**URL-beskyttelsesrapport** indeholder oversigts- og tendensvisninger af registrerede trusler og handlinger, der udføres på URL-klik som en del af [Pengeskab Links](safe-links.md). Denne rapport indeholder ikke klikdata fra brugere, hvor politikken Pengeskab links blev anvendt, da indstillingen **Spor bruger klik** ikke er valgt.

Hvis du vil have vist rapporten, skal du åbne [portalen Microsoft 365 Defender](https://security.microsoft.com), gå til **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter**. På siden **Mail & samarbejdsrapporter** skal du finde **siden URL-beskyttelse** og derefter klikke på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du åbne <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="Widgetten URL-beskyttelsesrapport på siden Mail & samarbejdsrapporter" lightbox="../../media/url-protection-report-widget.png":::

De tilgængelige visninger på rapportsiden for **BESKYTTELSE af URL-adresser** er beskrevet i følgende afsnit.

> [!NOTE]
> Dette er en *rapport over beskyttelsestendenser*, hvilket betyder, at data repræsenterer tendenser i et større datasæt. Derfor er dataene i diagrammerne ikke tilgængelige i realtid her, men dataene i detaljetabellen er, så du kan se en lille uoverensstemmelse mellem de to. Diagrammerne opdateres én gang hver 4. time og indeholder data for de sidste 90 dage.

### <a name="view-data-by-url-click-protection-action"></a>Få vist data efter handling til beskyttelse af klik på URL-adresse

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="Visningen, nemlig url-klikbeskyttelseshandlingen i URL-beskyttelsesrapporten" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

I **handlingsvisningen Vis data efter URL-adresse klikbeskyttelse** vises antallet af KLIK PÅ URL-adresser for brugere i organisationen og resultaterne af kliket:

- **Tilladt**: Klik er tilladt.
- **Tilladt af lejeradministrator**: Klik tilladt i politikker for Pengeskab links.
- **Blokeret**: Klik på Blokeret.
- **Blokeret af lejeradministrator**: De klik, der er blokeret i politikker for Pengeskab links.
- **Blokeret og klikket igennem**: Blokerede klik, hvor brugerne klikker sig igennem til den blokerede URL-adresse.
- **Blokeret af lejeradministratoren og klikket igennem**: Administratoren har blokeret linket, men brugeren har klikket sig igennem.
- **Klikkede sig igennem under scanningen**: Klikker, hvor brugerne klikker gennem den ventende scanningsside til URL-adressen.
- **Afventer scanning**: Klik på URL-adresser, der afventer en scanningsafsigelse.

Et klik angiver, at brugeren har klikket gennem blokeringssiden til det skadelige websted (administratorer kan deaktivere klikfrekvens i Pengeskab Links-politikker).

Hvis du klikker på **Filtre**, kan du redigere rapporten og detaljetabellen ved at vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC):****Startdato** og **Slutdato**
- **Handling**:
  - **Tilladt**
  - **Blokeret**
  - **Tilladt af lejeradministrator**
  - **Blokeret og klikket igennem**
  - **Blokeret af lejeradministrator og klikket igennem**
  - **Klikket igennem under scanningen**
  - **Afventer scanning**
- **Domæner**: De URL-domæner, der er angivet i rapportens resultater.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Detaljetabellen under diagrammet indeholder følgende visning næsten i realtid af alle de klik, der er foretaget i organisationen for de sidste 7 dage:

- **Kliktidspunkt**
- **Bruger**
- **URL**
- **Handling**
- **App**

På hovedrapportsiden er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](view-email-security-reports.md#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](view-email-security-reports.md#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](view-email-security-reports.md#export-report)** er tilgængelige.

### <a name="view-data-by-url-click-by-application"></a>Få vist data efter URL-adresse klik efter program

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="Url-adressens klikbeskyttelseshandlingsvisning i URL-beskyttelsesrapporten" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

Vis **data efter URL-adresse klik efter programvisning** viser antallet af klik på URL-adresser efter apps, der understøtter Pengeskab links:

- **Mailklient**
- **Office dokument**
- **Teams**

Hvis du klikker på **Filtre**, kan du redigere rapporten og detaljetabellen ved at vælge en eller flere af følgende værdier i det pop op-vindue, der vises:

- **Dato (UTC):****Startdato** og **Slutdato**
- **Registrering**: Tilgængelige apps fra diagrammet.
- **Domæner**: De URL-domæner, der er angivet i rapportens resultater.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke på **Anvend**, **Annuller** eller **Ryd filtre**.

Detaljetabellen under diagrammet indeholder følgende visning næsten i realtid af alle de klik, der er foretaget i organisationen for de sidste 7 dage:

- **Kliktidspunkt**
- **Bruger**
- **URL**
- **Handling**
- **App**

På hovedrapportsiden er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](view-email-security-reports.md#schedule-report)**, ![ikonet Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om rapport](view-email-security-reports.md#request-report)** og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Eksportknapper](view-email-security-reports.md#export-report)** er tilgængelige.

## <a name="additional-reports-to-view"></a>Yderligere rapporter, der skal vises

Ud over de rapporter, der er beskrevet i denne artikel, er flere andre rapporter tilgængelige, som beskrevet i følgende tabel:

|Rapport|Emne|
|---|---|
|**Explorer** (Microsoft Defender for Office 365 Plan 2) eller **registreringer i realtid** (Microsoft Defender for Office 365 Plan 1)|[Threat Explorer (og registreringer i realtid)](threat-explorer.md)|
|Mailsikkerhedsrapporter, der ikke kræver Defender for Office 365|[Få vist mailsikkerhedsrapporter på Microsoft 365 Defender-portalen](view-email-security-reports.md)|
|Mailflowrapporter i Exchange Administration (EAC)|[Mailflowrapporter i det nye Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

PowerShell-rapporterings-cmdlet'er:

|Rapport|Emne|
|---|---|
|Mest populære afsendere og modtagere|[Hent-MailTrafficTopReport](/powershell/module/exchange/get-mailtraffictopreport) <p> [Hent-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Mest populære malware|[Hent-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Posttrafik|[Hent-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|Sikre links|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|Kompromitterede brugere|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|Status for mailflow|[Hent-MailflowStatusRapport](/powershell/module/exchange/get-mailflowstatusreport)|
|Spoofed-brugere|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>Hvilke tilladelser kræves der for at få vist de Defender for Office 365 rapporter?

Hvis du vil have vist og bruge de rapporter, der er beskrevet i denne artikel, skal du være medlem af en af følgende rollegrupper på Microsoft 365 Defender portalen:

- **Organisationsadministration**
- **Sikkerhedsadministrator**
- **Sikkerhedslæser**
- **Global læser**

Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

**Bemærk**! Hvis du føjer brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration får brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Hvad sker der, hvis rapporterne ikke viser data?

Hvis du ikke får vist data i dine Defender for Office 365 rapporter, skal du dobbelttjekke, at dine politikker er konfigureret korrekt. Din organisation skal have [defineret politikker for Pengeskab links](set-up-safe-links-policies.md) og [Pengeskab vedhæftede filer](set-up-safe-attachments-policies.md), for at Defender for Office 365 beskyttelse kan være på plads. Se også [beskyttelse mod spam](anti-spam-protection.md) og [antimalware](anti-malware-protection.md).

## <a name="related-topics"></a>Relaterede emner

[Intelligente rapporter og indsigter på Microsoft 365 Defender-portalen](reports-and-insights-in-security-and-compliance.md)

[Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference)
