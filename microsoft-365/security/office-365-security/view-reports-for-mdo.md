---
title: Vis Defender for Office 365 rapporter
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
description: Administratorer kan lære, hvordan de finder og bruger de Defender for Office 365 rapporter, der er tilgængelige i Microsoft 365 Defender portal.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bcc77aaac71c8f8b4c3d3635b596a56ac12a3d7d
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507485"
---
# <a name="view-defender-for-office-365-reports-in-the-microsoft-365-defender-portal"></a>Få Defender for Office 365 vist rapporter i Microsoft 365 Defender portal

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender for Office 365 organisationer (f.eks. Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 1 eller Microsoft Defender for Office 365 Plan 2-tilføjelser) indeholder en række sikkerhedsrelaterede rapporter. Hvis du har de [nødvendige tilladelser](#what-permissions-are-needed-to-view-the-defender-for-office-365-reports), kan du få vist og downloade disse rapporter i Microsoft 365 Defender portal.

## <a name="view-and-download-reports"></a>Få vist og hente rapporter

### <a name="view-reports"></a>Vis rapporter

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Rapporter** \> & **mailsamarbejde** \> **& samarbejdsrapporter**. Hvis du vil gå direkte til **siden & om samarbejde, skal** du bruge <https://security.microsoft.com/emailandcollabreport>.

1. Vælg den rapport, du vil have vist, og vælg derefter **Vis detaljer**.  

### <a name="download-reports"></a>Download rapporter

1. I portalen Microsoft 365 Defender skal du <https://security.microsoft.com>gå til **ReportsEmail** >  **& Collaboration** \> **Reports for download**. For at gå direkte til siden **Rapporter til overførsel** skal du bruge <https://security.microsoft.com/ReportsForDownload?viewid=custom>.

:::image type="content" source="../../media/email-collaboration-download-reports.png" alt-text="Siden Rapporter & mailsamarbejde i Microsoft 365 Defender portal" lightbox="../../media/email-collaboration-download-reports.png":::

> [!NOTE]
>
> Mailsikkerhedsrapporter, der ikke kræver, at Defender for Office 365, er beskrevet i Få vist [mailsikkerhedsrapporter Microsoft 365 Defender portalen](view-email-security-reports.md).
>
> Rapporter, der er relateret til mailflow, findes nu i Exchange Administration (EAC). Du kan finde flere oplysninger om disse rapporter [under Mailflowrapporter i den Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

## <a name="safe-attachments-file-types-report"></a>Pengeskab rapport over vedhæftede filer

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger findes i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="safe-attachments-message-disposition-report"></a>Pengeskab rapport over fordeling af vedhæftede filer

> [!NOTE]
> Denne rapport frarådes. De samme oplysninger findes i [statusrapporten for trusselsbeskyttelse](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Rapport over mailventetid

Rapporten **Mailventetid viser** dig en samlet visning af maillevering og deonationventetid, som du har oplevet i din organisation. Leveringstider for mails i tjenesten påvirkes af en række faktorer, og det absolutte leveringstidstider i sekunder er ofte ikke en god indikator for succes eller et problem. Et langsomt leveringstids tidsrum på én dag kan betragtes som et gennemsnitlig leveringstidstid på en anden dag eller omvendt. Dette forsøger at kvalificere leveringen af meddelelser baseret på statistiske data om de observerede leveringstider for andre meddelelser.

Klientside- og netværksventetid er ikke inkluderet.

Hvis du vil have vist rapporten, skal Microsoft 365 Defender-portalen <https://security.microsoft.com>på ,  \> gå til **Rapporter & mailsamarbejde** \> **& samarbejdsrapporter**. Hvis du vil gå direkte til **siden & om samarbejde, skal** du bruge <https://security.microsoft.com/emailandcollabreport>.

På siden **Mailrapporter & skal du** finde **Rapport over mailventetid** og derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du bruge <https://security.microsoft.com/mailLatencyReport>.


:::image type="content" source="../../media/mail-latency-report-widget.png" alt-text="Widgetten Rapport over mailventetid på siden & med samarbejdsrapporter" lightbox="../../media/mail-latency-report-widget.png":::

På siden **Rapport over mailventetid** er følgende faner tilgængelige på **rapportsiden Mailventetid** :

- **50. fraktil**: Dette er midten for leveringen af meddelelser. Du kan betragte denne værdi som en gennemsnitlig leveringstid. Denne fane er valgt som standard.
- **90. fraktil**: Dette angiver en lang ventetid for levering af meddelelsen. Kun 10 % af meddelelser tog længere tid end denne værdi at levere.
- **99. fraktil**: Dette angiver den højeste ventetid for leveringen af meddelelsen.

Uanset hvilken fane du vælger, viser diagrammet meddelelser organiseret i følgende kategorier:

- **Generelt**
- **Detonation**

Når du peger på en kategori i diagrammet, kan du se en oversigt over ventetiden i hver kategori.

:::image type="content" source="../../media/mail-latency-report-50th-percentile-view.png" alt-text="Den 50. fraktilvisning af rapporten Mailventetid" lightbox="../../media/mail-latency-report-50th-percentile-view.png":::

Hvis du klikker **på** Filter, kan du filtrere både diagrammet og detaljetabellen efter følgende værdier:

- **Dato (UTC)**: **Startdato** **og slutdato**
- **Meddelelsesvisning**: En af følgende værdier:
  - **Alle meddelelser**
  - **Meddelelser, der er** blevet fjernet: En af følgende værdier:
    - **Indbygget detonation**: Omfatter meddelelser, der er helt testet før levering.
    - **Asynkron detonation**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Følgende oplysninger er tilgængelige i detaljetabellen under diagrammet:

- **Dato (UTC)**
- **Ventetid**
- **Antal meddelelser**
- **50. fraktil**
- **90. fraktil**
- **99. fraktil**

På hovedrapportsiden er ikonet ![Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knappen](view-email-security-reports.md#export-report)** Eksportér er tilgængelig.

## <a name="threat-protection-status-report"></a>Statusrapport over trusselsbeskyttelse

**Statusrapporten for trusselsbeskyttelse** er en enkelt visning, der samler oplysninger om skadeligt indhold og skadelig mail, der registreres og blokeres [af Exchange Online Protection](exchange-online-protection-overview.md) (EOP) og Microsoft Defender for Office 365. Du kan få mere at vide [under Statusrapport for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).

## <a name="top-senders-and-recipients-report"></a>Rapport over de mest populære afsendere og modtagere

Rapporten **Øverste afsendere og modtagere viser** de øverste modtagere af EOP og Defender for Office 365-beskyttelsesfunktioner. Du kan finde flere oplysninger [i Rapporten Vigtigste afsendere og modtagere](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="url-protection-report"></a>Rapport over beskyttelse af URL-adresser

Rapporten **beskyttelse af URL-adresser** indeholder oversigts- og tendensvisninger for registrerede trusler og handlinger, der er foretaget på URL-klik som en del [Pengeskab Links](safe-links.md). Denne rapport indeholder ikke klik på data fra brugere, hvor politikken Pengeskab kæder blev anvendt, når indstillingen Spor **brugerklik** ikke er valgt.

For at få vist rapporten skal [du åbne Microsoft 365 Defender](https://security.microsoft.com) portalen,  \> gå til **& mailsamarbejde** \> **& samarbejdsrapporter**. På siden **Mailrapporter & du finde** beskyttelse mod **URL-adresser og** derefter klikke på **Vis detaljer**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/URLProtectionActionReport>.

:::image type="content" source="../../media/url-protection-report-widget.png" alt-text="Widgetten URL-beskyttelsesrapport på siden & med samarbejdsrapporter" lightbox="../../media/url-protection-report-widget.png":::

De tilgængelige visninger på **siden til beskyttelse af** URL-adresser er beskrevet i de følgende afsnit.

> [!NOTE]
> Dette er en *rapport over en beskyttelsestendens*, der betyder, at data repræsenterer tendenser i et større datasæt. Det betyder, at dataene i diagrammerne ikke er tilgængelige i realtid her, men dataene i detaljetabellen er, så der kan være en lille forskel mellem de to. Diagrammerne opdateres én gang hver fjerde time og indeholder data for de seneste 90 dage.

### <a name="view-data-by-url-click-protection-action"></a>Vis data efter URL-adresse Klik på beskyttelse

:::image type="content" source="../../media/url-threat-protection-report-url-click-protection-action-view.png" alt-text="Visningen , der er en klikbeskyttelseshandling for URL-adresse, i rapporten om beskyttelse af URL-adresser" lightbox="../../media/url-threat-protection-report-url-click-protection-action-view.png":::

Klik **på beskyttelseshandlingsvisningen Vis** data efter URL-adresse viser antallet af URL-klik fra brugerne i organisationen og resultaterne af klikket:

- **Tilladt**: Klik tilladt.
- **Tilladt af lejeradministrator**: Klik på tilladt Pengeskab politikker for links.
- **Blokeret**: Klik på blokeret.
- **Blokeret af lejeradministrator**: Politikkerne Klik blokeret Pengeskab Links.
- **Blokeret og klikket igennem**: Blokerede klik, hvor brugere klikker igennem til den blokerede URL-adresse.
- **Blokeret af lejeradministrator og klikket** igennem: Administratoren har blokeret linket, men brugeren klikkede på det.
- **Klikket igennem under scanningen**: Klik på det sted, hvor brugerne klikker sig gennem den ventende scanningsside til URL-adressen.
- **Ventende scanning**: Klik på URL-adresser, der afventer en scanningsdom.

Et klik angiver, at brugeren har klikket gennem blokeringssiden til det skadelige websted (administratorer kan deaktivere klik igennem Pengeskab politikker for links).

Hvis du klikker **på** Filtre, kan du redigere rapporten og detaljetabellen ved at vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)**: **Startdato** **og slutdato**
- **Handling**:
  - **Tilladt**
  - **Blokeret**
  - **Tilladt af lejeradministrator**
  - **Blokeret og klikket igennem**
  - **Blokeret af lejeradministrator og klikket igennem**
  - **Klikket igennem under scanningen**
  - **Ventende scanning**
- **Domæner:** DE URL-domæner, der er angivet i resultaterne af rapporten.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Detaljetabellen under diagrammet indeholder følgende næsten realtidsvisning af alle klik, der er sket inden for organisationen de seneste 7 dage:

- **Klik på klokkeslæt**
- **Bruger**
- **URL-adresse**
- **Handling**
- **App**

På hovedrapportsiden er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](view-email-security-reports.md#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](view-email-security-reports.md#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](view-email-security-reports.md#export-report)** Eksportér er tilgængelige.

### <a name="view-data-by-url-click-by-application"></a>Få vist data efter URL-adresse Klik efter program

:::image type="content" source="../../media/url-threat-protection-report-url-click-by-application-view.png" alt-text="Klik på handlingsvisningen URL-adresse i rapporten om beskyttelse af URL-adresser" lightbox="../../media/url-threat-protection-report-url-click-by-application-view.png":::

Klik **på Vis data efter URL-adresse for programvisning** viser antallet af klik på URL-adresser i apps, der understøtter Pengeskab links:

- **Mailklient**
- **Office dokument**
- **Teams**

Hvis du klikker **på** Filtre, kan du redigere rapporten og detaljetabellen ved at vælge en eller flere af følgende værdier i pop op-menuen, der vises:

- **Dato (UTC)**: **Startdato** **og slutdato**
- **Registrering**: Tilgængelige apps fra diagrammet.
- **Domæner:** DE URL-domæner, der er angivet i resultaterne af rapporten.
- **Modtagere**

Når du er færdig med at konfigurere filtrene, skal du klikke **på Anvend**, **Annuller** eller **Ryd filtre**.

Detaljetabellen under diagrammet indeholder følgende næsten realtidsvisning af alle klik, der er sket inden for organisationen de seneste 7 dage:

- **Klik på klokkeslæt**
- **Bruger**
- **URL-adresse**
- **Handling**
- **App**

På hovedrapportsiden er ikonet ![Opret tidsplan.](../../media/m365-cc-sc-create-icon.png) **[Opret tidsplan](view-email-security-reports.md#schedule-report)**, ikon ![for Anmod om rapport.](../../media/m365-cc-sc-download-icon.png) **[Anmod om](view-email-security-reports.md#request-report)** rapport og ![ikonet Eksportér.](../../media/m365-cc-sc-download-icon.png) **[Knapperne](view-email-security-reports.md#export-report)** Eksportér er tilgængelige.

## <a name="additional-reports-to-view"></a>Yderligere rapporter, der skal vises

Ud over de rapporter, der er beskrevet i denne artikel, er flere andre rapporter tilgængelige som beskrevet i følgende tabel:

|Rapport|Emne|
|---|---|
|**Explorer** (Microsoft Defender for Office 365 Plan 2) **eller registreringer** i realtid (Microsoft Defender for Office 365 Plan 1)|[Trusselsstifinder (og registreringer i realtid)](threat-explorer.md)|
|Mailsikkerhedsrapporter, der ikke kræver Defender for Office 365|[Få vist mailsikkerhedsrapporter Microsoft 365 Defender portalen](view-email-security-reports.md)|
|Mailflowrapporter i Exchange Administration (EAC)|[Mailflowrapporter i den nye Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|

PowerShell-rapporterings-cmdlet'er:

|Rapport|Emne|
|---|---|
|Mest populære afsendere og modtagere|[Get-MailTrafficTopReport](/powershell/module/exchange/get-mailtraffictopreport) <p> [Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Vigtigste malwares|[Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport)|
|Mailtrafik|[Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <p> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|
|Sikre links|[Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <p> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|
|Kompromitterede brugere|[Get-CompromisedUserAggregateReport](/powershell/module/exchange/get-compromiseduseraggregatereport) <p> [Get-CompromisedUserDetailReport](/powershell/module/exchange/get-compromiseduserdetailreport)|
|Status for mailflow|[Get-MailflowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|
|Spoofed brugere|[Get-SpoofMailReport](/powershell/module/exchange/get-spoofmailreport)|

## <a name="what-permissions-are-needed-to-view-the-defender-for-office-365-reports"></a>Hvilke tilladelser er nødvendige for at få vist Defender for Office 365 rapporter?

For at få vist og bruge de rapporter, der er beskrevet i denne artikel, skal du være medlem af en af følgende rollegrupper på Microsoft 365 Defender portal:

- **Organisationsadministration**
- **Sikkerhedsadministrator**
- **Sikkerhedslæser**
- **Global læser**

Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

**Bemærk**! Når du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Hvad nu, hvis rapporterne ikke viser data?

Hvis du ikke kan se data i dine Defender for Office 365, skal du kontrollere, at dine politikker er konfigureret korrekt. Din organisation skal have [Pengeskab politikker](set-up-safe-links-policies.md) for [links Pengeskab](set-up-safe-attachments-policies.md) politikker for vedhæftede filer, der er defineret, Defender for Office 365 sikre beskyttelsen på plads. Se også [Beskyttelse mod spam og antimalware](anti-spam-and-anti-malware-protection.md).

## <a name="related-topics"></a>Relaterede emner

[Intelligente rapporter og indsigt i Microsoft 365 Defender-portalen](reports-and-insights-in-security-and-compliance.md)

[Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference)
