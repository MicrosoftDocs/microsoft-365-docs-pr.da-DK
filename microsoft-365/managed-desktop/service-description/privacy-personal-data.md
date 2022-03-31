---
title: Beskyttelse af personlige oplysninger og personlige oplysninger
description: Oplysninger om de data, der indsamles, gemmes og bruges af tjenesten
keywords: GDPR, opbevaring, sletning, opbevaring, opbevaring, behandling, sikkerhed, overvågning
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
manager: dougeby
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.topic: article
audience: Admin, ITPro
ms.localizationpriority: medium
ms.openlocfilehash: c70b15a3d35dc4b19c5961e9fbe0404780c12309
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601655"
---
# <a name="privacy"></a>Beskyttelse af personlige oplysninger

Microsoft Managed Desktop er en IT-as-a-Service (ITaaS)-tjeneste til skykunder til virksomheder, som er designet til at holde medarbejdernes Windows enheder installeret og opdateret.

Den leverer også it-tjenesteadministration og -handlinger, overvåger sikkerhed og hændelsesrespons og brugersupport. Denne artikel indeholder flere oplysninger om dataplatform og overholdelse af regler og standarder for beskyttelse af personlige oplysninger for Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Datakilder og formål for Microsoft-administreret skrivebord

Microsoft Managed Desktop leverer sin tjeneste til virksomhedskunder og administrerer kundernes enheder, der er tilmeldt, korrekt ved hjælp af data fra forskellige kilder.

Disse kilder omfatter Azure Active Directory, Microsoft Intune, Microsoft Windows 10 og Microsoft Defender til slutpunkt. De giver en omfattende visning af de enheder, som Microsoft Managed Desktop administrerer. Tjenesten bruger også disse Microsoft-tjenester til at give Microsoft Managed Desktop mulighed for at levere ITaaS-funktioner:

| Datakilde | Formål |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | Administration af enhedskonfigurationsoplevelse, administration af forbindelser til andre tjenester og driftssupport til it-fagfolk. |
| [Windows til virksomheder](/windows/deployment/update/waas-manage-updates-wufb) | Bruger Windows 10 Enterprise til at give yderligere oplysninger om Windows 10 opdatering. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Administration af enheder og for at beskytte dine data. Følgende datakilder falder ind under Microsoft Endpoint Manager:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): Godkendelse og identifikation af alle brugerkonti.</li><li>[Microsoft Intune](/mem/intune/): Distribuere enhedskonfigurationer, administration af enheder og programadministration.</li><li>[Slutpunktsanalyse](/mem/analytics/overview): Analytisk indsigt om brug af enheder og apps.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot): Klargøring og udrulning af enheder.</li><li>[Microsoft Defender til Slutpunkt: Leverer sikkerhedstjenester](/microsoft-365/security/defender-endpoint/) som f.eks. overvågning af enhedssikkerhed og sikkerhedsintelligensdata.</li></ul>
| [Microsoft-administreret skrivebord](https://endpoint.microsoft.com/#home) | Data, der leveres af kunden eller genereres af tjenesten under kørsel af tjenesten. |
| [Microsoft 365 apps til virksomheder](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Administration af Microsoft 365 Apps.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft-administreret computerdataproces og -lagring

Microsoft Managed Desktop er afhængig af data fra flere Microsoft-produkter og -tjenester for at kunne levere sine tjenester til virksomhedskunder.

For at beskytte og vedligeholde registrerede enheder behandler og kopierer vi data fra disse tjenester til Microsoft Managed Desktop. Når vi behandler data, følger vi de dokumenterede anvisninger, som du angiver, som henvist til i [vilkårene for onlinetjenester](https://www.microsoft.com/licensing/product-licensing/products) og Microsofts erklæring om beskyttelse af [personlige oplysninger](https://privacy.microsoft.com/privacystatement).

Microsoft Managed Desktops processoropgaver omfatter at sikre den relevante fortrolighed, sikkerhed og fleksibilitet. Microsoft Managed Desktop anvender yderligere beskyttelse af personlige oplysninger og sikkerhedsforanstaltninger for at sikre korrekt håndtering af personlige identificerbare data.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft-administreret pc-datalager og medarbejderplacering

Microsoft Managed Desktop gemmer sine data i Azure-datacentrene i USA.

Personlige data, der indhentes af Microsoft Managed Desktop og andre tjenester, er nødvendige for at tjenesten kan fungere korrekt. Hvis en enhed fjernes fra Microsoft Managed Desktop, opbevarer vi personlige data i maksimalt 30 dage. Advarselsdata, der indsamles af Microsoft Defender til slutpunkt, gemmes dog i 180 dage af sikkerhedsmæssige årsager. Du kan finde flere oplysninger om opbevaring af [data i Dataopbevaring, sletning og](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview) Microsoft 365.

Microsoft Managed Desktop Engineering Operations and Security Operations teams er placeret i USA og Indien.

### <a name="microsoft-windows-10-diagnostic-data"></a>Diagnostiske Microsoft Windows 10 data

Microsoft Managed Desktop bruger [Windows 10 forbedrede diagnosticeringsdata](/windows/privacy/windows-diagnostic-data) til at Windows, holde dig opdateret, foretage fejlfinding af problemer og foretage produktforbedringer.

Den forbedrede indstilling for diagnostiske data indeholder mere detaljerede oplysninger om de enheder, der er tilmeldt Microsoft Managed Desktop, deres indstillinger, funktioner og enhedstilstand. Når udvidede diagnostiske data er markeret, indsamles der data, herunder nødvendige diagnostiske data. Du kan finde flere oplysninger [under Windows af diagnostiske data](/windows/privacy/changes-to-windows-diagnostic-data-collection) om Windows 10 og indsamling af data.

Terminologien for diagnostiske data ændres i fremtidige versioner Windows. Microsoft Managed Desktop er udelukkende forpligtet til at behandle de data, som tjenesten har brug for. Selv om det betyder, at diagnosticeringsniveauet ændres til **Valgfrit,** vil Microsoft Managed Desktop implementere de begrænsede diagnosticeringspolitikker til at finjustere indsamling af diagnostiske data, der kræves til tjenesten. Du kan finde flere oplysninger [under Ændringer Windows indsamling af diagnostiske data](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop behandler og gemmer kun data på systemniveau fra Windows 10 valgfrie diagnostiske data, der stammer fra registrerede enheder som f.eks. program- og enhedspålidelighed og oplysninger om ydeevne. Microsoft Managed Desktop behandler ikke og gemmer kundernes personlige data som f.eks. chat- og browserhistorik, tale-, tekst- eller taledata.

Du kan finde flere oplysninger om indsamling af diagnostiske data Windows 10 Microsoft Windows 10 i afsnittet Hvor vi gemmer og behandler personlige [data](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) i Microsofts erklæring om beskyttelse af personlige oplysninger.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows til virksomheder

Microsoft Windows til virksomheder bruger data fra Windows til at analysere opdateringsstatus og fejl. Microsoft Managed Desktop bruger disse data og bruger dem til at afhjælpe og løse problemer for at sikre, at alle registrerede enheder er opdateret baseret på en foruddefineret opdatering kadence.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Identifikation af data, der bruges af Microsoft Managed Desktop, gemmes af Azure Active Directory (Azure AD) på et geografisk sted. Den geografiske placering er baseret på den placering, der leveres af organisationen, når du abonnerer på Microsofts onlinetjenester, f.eks. Microsoft Apps til Enterprise og Azure. Du kan finde flere oplysninger om, hvor dine Azure AD-data er placeret, [Azure Active Directory – Hvor er dine data placeret?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune indsamler, behandler og deler data med Microsoft Managed Desktop for at understøtte virksomhedens aktiviteter og tjenester. Du kan finde flere oplysninger om de data, der indsamles i Intune, [under Dataindsamling i Intune](/mem/intune/protect/privacy-data-collect)

Du kan finde flere Microsoft Intune om dataplaceringer i [Hvor Microsoft 365 dine kundedata er gemt](/microsoft-365/enterprise/o365-data-locations). Intune respekterer de valg af lagerplacering, administratoren har foretaget for kundedata.

### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender til Slutpunkt

Microsoft Defender til slutpunkt indsamler og gemmer oplysninger for enheder, der er tilmeldt Microsoft Managed Desktop til administration, sporing og rapporteringsformål. De oplysninger, der indsamles, omfatter:

- Fildata (f.eks. filnavne, størrelse og hashes)
- Procesdata (kører processer, hash'er)
- Registreringsdatabasedata
- Data om netværksforbindelse
- Enhedsoplysninger (f.eks. enheds-identifikatorer, enhedsnavne og operativsystemversion)

Du kan finde flere oplysninger om Microsoft Defender for Endpoints dataindsamling og -lagerplaceringer i [Microsoft Defender til slutpunktsdatalagring og beskyttelse af personlige oplysninger](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps til store virksomheder

Microsoft 365 Apps til Enterprise indsamler og deler data med Microsoft Managed Desktop for at sikre, at disse apps er opdateret med den nyeste version. Disse opdateringer er baseret på foruddefinerede opdateringskanaler, der administreres af Microsoft Managed Desktop. Du kan finde flere Microsoft 365 Apps om datasamlings- og lagerplaceringer i [Microsoft Defender til slutpunktsdatalagring og beskyttelse af personlige oplysninger](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Besked om større dataændring

Microsoft Managed Desktop følger en ændringsproces som beskrevet i vores tjenestekommunikationsstruktur.

Vi giver kunder besked via Microsoft 365 Meddelelsescenter og Microsoft Managed Desktop Admin-portalen for både sikkerhedshændelser og større ændringer af tjenesten.

Ændringer af de typer data, der indsamles, og hvor de gemmes, betragtes som en materialeændring. Vi giver dig mindst 30 dages avanceret meddelelse om denne ændring, som det er standardpraksis for Microsoft 365-produkter og -tjenester. Få mere at vide under [Tjenesteændringer og -kommunikation](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Overholdelse af regler og standarder

Microsoft Managed Desktop har gennemgået ekstern revision og fået et omfattende sæt af overholdelsestilbud. Du kan finde flere oplysninger i Overholdelse af [regler og standarder](/microsoft-365/managed-desktop/intro/compliance). Overvågningsrapporter kan hentes på Microsoft [Service Trust Portal](https://aka.ms/stp), der fungerer som et centralt lager for Microsoft Enterprise Online Services. Microsoft Managed Desktop er angivet i disse dokumenter under kategorien "Overvågning og administration".

### <a name="data-subject-requests"></a>Anmodninger fra den registrerede

Microsoft Managed Desktop følger GDPR- og CCPA-regler for beskyttelse af personlige oplysninger, som giver dataemner specifikke rettigheder til deres personlige data.

Disse rettigheder omfatter:

- Få kopier af personlige data
- Anmode om rettelser til den
- Begrænsning af behandlingen af den
- Slette den
- Modtage den i et elektronisk format, så den kan flyttes til en anden controller.

Du kan finde flere generelle oplysninger om anmodninger fra registrerede i [Anmodninger fra registrerede og GDPR og CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Hvis du vil udnytte anmodninger fra den registrerede om data, der indsamles af Microsoft Managed Desktop-sagsadministrationssystemet, skal du se følgende anmodninger fra registrerede:

| Anmodninger fra den registrerede | Beskrivelse |
| ------ | ------ |
| Data fra Microsoft Defender til slutpunktsbeskeder | Din sikkerhedsadministrator kan anmode om sletning eller udtrækning af personlige data, der er relateret til microsoft Defender for Endpoint-beskeder, ved at sende en rapportanmodning i [administrationsportalen](https://aka.ms/memadmin). <br><br> Angiv følgende oplysninger: <br><ul><li>Anmodningstype: Skift anmodning</li><li>Kategori: Sikkerhed</li><li>Underkategori: Andet</li><li>Beskrivelse: Angiv de relevante enhedsnavne.</li></ul> |
| Data fra Microsoft-administrerede supportanmodninger på skrivebordet | Din it-administrator kan anmode om sletning eller udtrækning af supportanmodninger relateret til personlige data ved at sende en rapportanmodning på [administrationsportalen](https://aka.ms/memadmin). <br><br> Angiv følgende oplysninger: <ul><li>Anmodningstype: Skift anmodning</li><li>Kategori: Sikkerhed</li><li>Underkategori: Andet</li><li>Beskrivelse: Angiv de relevante enhedsnavne eller brugernavne.</li></ul>

For DSR'er fra andre produkter, der er relateret til tjenesten, skal du se følgende artikler:

- Windows [diagnostiske data](/compliance/regulatory/gdpr-dsr-windows)
- Microsoft [Intune-data](/compliance/regulatory/gdpr-dsr-intune)
- Azure Active [Directory-data](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Juridiske oplysninger

**Microsofts meddelelse om beskyttelse af personlige oplysninger til slutbrugere af produkter, der leveres af virksomhedskunder**:

[Microsofts erklæring om beskyttelse](https://privacy.microsoft.com/privacystatement) af personlige oplysninger giver slutbrugerne besked om, at de skal logge på Microsoft-produkter med en arbejdskonto:

1. Deres organisation kan styre og administrere deres konto (herunder kontrol af indstillinger relateret til beskyttelse af personlige oplysninger) samt få adgang til og behandle deres data.
1. Microsoft kan indsamle og behandle dataene for at levere tjenesten til organisationen og slutbrugerne.
