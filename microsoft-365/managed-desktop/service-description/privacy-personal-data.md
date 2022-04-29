---
title: Beskyttelse af personlige oplysninger og personlige oplysninger
description: Oplysninger om de data, der indsamles, gemmes og bruges af tjenesten
keywords: GDPR, opbevaring, sletning, lager, opbevaring, behandling, sikkerhed, overvågning
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
ms.openlocfilehash: e7c9912e3890d9b13003c7f3264490f67c4fc305
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128340"
---
# <a name="privacy"></a>Beskyttelse af personlige oplysninger

Microsoft Managed Desktop er en ITaaS-tjeneste (IT-as-a-Service) til virksomhedscloudkunder, der er designet til at holde medarbejdernes Windows enheder udrullet og opdateret.

Den leverer også administration og drift af it-tjenester, overvåger sikkerheds- og hændelsessvar og brugersupport. Denne artikel indeholder flere oplysninger om dataplatform og overholdelse af angivne standarder for beskyttelse af personlige oplysninger for Microsoft Managed Desktop.

## <a name="microsoft-managed-desktop-data-sources-and-purpose"></a>Microsoft Managed Desktop datakilder og formål

Microsoft Managed Desktop leverer tjenesten til virksomhedskunder og administrerer på korrekt vis kundernes tilmeldte enheder ved hjælp af data fra forskellige kilder.

Disse kilder omfatter Azure Active Directory, Microsoft Intune, Microsoft Windows 10 og Microsoft Defender for Endpoint. De giver en omfattende visning af de enheder, Microsoft Managed Desktop administrerer. Tjenesten bruger også disse Microsoft-tjenester til at gøre det muligt for Microsoft Managed Desktop at levere ITaaS-funktioner:

| Datakilde | Formål |
| ------ | ------ |
| [Microsoft Windows 10 Enterprise](/windows/windows-10/) | Administration af enhedskonfigurationsoplevelsen, administration af forbindelser til andre tjenester og driftssupport for it-teknikere. |
| [Windows Update til virksomheder](/windows/deployment/update/waas-manage-updates-wufb) | Bruger Windows 10 Enterprise diagnosticeringsdata til at levere yderligere oplysninger om Windows 10 opdatering. |
| [Microsoft Endpoint Manager](/mem/endpoint-manager-overview) | Enhedshåndtering og for at beskytte dine data. Følgende datakilder er omfattet af Microsoft Endpoint Manager:<br><ul><li>[Microsoft Azure Active Directory](/azure/active-directory/): Godkendelse og identifikation af alle brugerkonti.</li><li>[Microsoft Intune](/mem/intune/): Distribuer enhedskonfigurationer, enhedshåndtering og programadministration.</li><li>[Endpoint Analytics](/mem/analytics/overview): Analytisk indsigt i enheds- og appforbrug.</li><li>[Windows Autopilot](/microsoft-365/windows/windows-autopilot): Klargøring og installation af enheder.</li><li>[Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/): Leverer sikkerhedstjenester, f.eks. overvågning af enhedssikkerhed og sikkerhedsintelligensdata.</li></ul>
| [Microsoft-administreret skrivebord](https://endpoint.microsoft.com/#home) | Data, der leveres af kunden eller genereres af tjenesten under kørsel af tjenesten. |
| [Microsoft 365 apps til virksomheder](https://www.microsoft.com/en-us/microsoft-365/enterprise/compare-office-365-plans?rtc=1)| Administration af Microsoft 365 Apps.

## <a name="microsoft-managed-desktop-data-process-and-storage"></a>Microsoft Managed Desktop dataproces og -lager

Microsoft Managed Desktop er afhængig af data fra flere Microsoft-produkter og -tjenester for at kunne levere tjenesten til virksomhedskunder.

For at beskytte og vedligeholde tilmeldte enheder behandler og kopierer vi data fra disse tjenester til Microsoft Managed Desktop. Når vi behandler data, følger vi de dokumenterede anvisninger, du angiver, som der henvises til i [Vilkår for onlinetjenester](https://www.microsoft.com/licensing/product-licensing/products) og [Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement).

Microsoft Managed Desktop databehandleropgaver omfatter at sikre passende fortrolighed, sikkerhed og robusthed. Microsoft Managed Desktop anvender yderligere foranstaltninger til beskyttelse af personlige oplysninger og sikkerhed for at sikre korrekt håndtering af personidentificerbare data.

## <a name="microsoft-managed-desktop-data-storage-and-staff-location"></a>Microsoft Managed Desktop datalager og personaleplacering

Microsoft Managed Desktop gemmer sine data i Azure-datacentrene i USA.

Personlige data, der er hentet af Microsoft Managed Desktop og andre tjenester, er påkrævet for at holde tjenesten driftsklar. Hvis en enhed fjernes fra Microsoft Managed Desktop, opbevarer vi personlige data i højst 30 dage. Beskeddata, der indsamles af Microsoft Defender for Endpoint, gemmes dog i 180 dage af sikkerhedsmæssige årsager. Du kan få flere oplysninger om dataopbevaring under [Dataopbevaring, sletning og destruktion i Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

Microsoft Managed Desktop Engineering Operations and Security Operations-teams er placeret i USA, Indien og Rumænien.

### <a name="microsoft-windows-10-diagnostic-data"></a>Microsoft Windows 10 diagnosticeringsdata

Microsoft Managed Desktop bruger [Windows 10 Forbedrede diagnosticeringsdata](/windows/privacy/windows-diagnostic-data) til at holde Windows sikker, opdateret, foretage fejlfinding af problemer og foretage produktforbedringer.

Den forbedrede indstilling for diagnosticeringsdata indeholder mere detaljerede oplysninger om de enheder, der er tilmeldt Microsoft Managed Desktop, og deres indstillinger, funktioner og enhedstilstand. Når der vælges forbedrede diagnosticeringsdata, indsamles data, herunder påkrævede diagnosticeringsdata. Du kan få flere oplysninger under [Ændringer af Windows indsamling af diagnosticeringsdata](/windows/privacy/changes-to-windows-diagnostic-data-collection) om indstillingen Windows 10 diagnosticeringsdata og dataindsamling.

Terminologien for diagnosticeringsdata ændres i fremtidige versioner af Windows. Microsoft Managed Desktop er forpligtet til kun at behandle de data, som tjenesten har brug for. Selvom det betyder, at diagnosticeringsniveauet ændres til **Valgfrit**, implementerer Microsoft Managed Desktop de begrænsede diagnosticeringspolitikker for at finjustere den indsamling af diagnosticeringsdata, der kræves til tjenesten. Du kan få flere oplysninger under [Ændringer af Windows indsamling af diagnosticeringsdata](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Microsoft Managed Desktop behandler og gemmer data på systemniveau fra Windows 10 valgfri diagnosticeringsdata, der stammer fra tilmeldte enheder, f.eks. oplysninger om applikations- og enhedspålidelighed og ydeevne. Microsoft Managed Desktop behandler og gemmer ikke kundernes personlige data, f.eks. chat- og browserhistorik, stemme, tekst eller taledata.

Du kan få flere oplysninger om indsamling af diagnosticeringsdata for Microsoft Windows 10 i afsnittet [Hvor vi gemmer og behandler personlige data](https://privacy.microsoft.com/privacystatement#mainwherewestoreandprocessdatamodule) i Microsofts erklæring om beskyttelse af personlige oplysninger.

### <a name="microsoft-windows-update-for-business"></a>Microsoft Windows Update for Business

Microsoft Windows Update for Business bruger data fra Windows diagnosticering til at analysere opdateringsstatus og -fejl. Microsoft Managed Desktop bruger disse data og bruger dem til at afhjælpe og løse problemer for at sikre, at alle registrerede enheder er opdateret baseret på en foruddefineret opdateringsrytme.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

Identificerende data, der bruges af Microsoft Managed Desktop, gemmes af Azure Active Directory (Azure AD) på en geografisk placering. Den geografiske placering er baseret på den placering, som organisationen har leveret ved abonnement på Microsoft onlinetjenester, f.eks. Microsoft Apps til Enterprise og Azure. Du kan finde flere oplysninger om, hvor dine Azure AD data er placeret, [under Azure Active Directory – Hvor er dine data placeret?](https://msit.powerbi.com/view?r=eyJrIjoiODdjOWViZDctMWRhZS00ODUzLWI4MmQtNWM5NjBkZTBkNjFlIiwidCI6IjcyZjk4OGJmLTg2ZjEtNDFhZi05MWFiLTJkN2NkMDExZGI0NyIsImMiOjV9)

### <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune indsamler, behandler og deler data for at Microsoft Managed Desktop for at understøtte forretningshandlinger og -tjenester. Du kan få flere oplysninger om de data, der indsamles i Intune, [under Dataindsamling i Intune](/mem/intune/protect/privacy-data-collect)

Du kan få flere oplysninger om Microsoft Intune dataplaceringer under [Hvor dine Microsoft 365 kundedata er gemt](/microsoft-365/enterprise/o365-data-locations). Intune respekterer administratorens valg af lagringsplacering for kundedata.

### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

Microsoft Defender for Endpoint indsamler og gemmer oplysninger om enheder, der er tilmeldt Microsoft Managed Desktop til administration, sporing og rapportering. De indsamlede oplysninger omfatter:

- Fildata (f.eks. filnavne, størrelse og hashen)
- Behandl data (kører processer, hashen)
- Registreringsdatabasedata
- Netværksforbindelsesdata
- Enhedsoplysninger (f.eks. enheds-id'er, enhedsnavne og operativsystemversionen)

Du kan få flere oplysninger om Microsoft Defender for Endpoint dataindsamling og lagerplaceringer [under Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for Enterprise

Microsoft 365 Apps til Enterprise indsamler og deler data med Microsoft Managed Desktop for at sikre, at disse apps er opdateret med den nyeste version. Disse opdateringer er baseret på foruddefinerede opdateringskanaler, der administreres af Microsoft Managed Desktop. Du kan få flere oplysninger om Microsoft 365 Apps dataindsamlings- og lagerplaceringer [under Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger](/microsoft-365/security/defender-endpoint/data-storage-privacy#what-data-does-microsoft-defender-atp-collect).

## <a name="major-data-change-notification"></a>Meddelelse om ændring af overordnede data

Microsoft Managed Desktop følger en ændringskontrolproces som beskrevet i vores tjenestekommunikationsstruktur.

Vi giver kunderne besked via Microsoft 365 Meddelelsescenter og Microsoft Managed Desktop administrationsportal om både sikkerhedshændelser og større ændringer af tjenesten.

Ændringer af de datatyper, der indsamles, og hvor de gemmes, betragtes som en væsentlig ændring. Vi giver mindst 30 dages avanceret meddelelse om denne ændring, hvilket er standardpraksis for Microsoft 365 produkter og tjenester. Du kan få flere oplysninger under [Tjenesteændringer og -kommunikation](/microsoft-365/managed-desktop/service-description/servicechanges).

## <a name="compliance"></a>Overholdelse af regler og standarder

Microsoft Managed Desktop har gennemgået ekstern revision og fået et omfattende sæt af tilbud om overholdelse af angivne standarder. Du kan finde flere oplysninger i [Overholdelse](/microsoft-365/managed-desktop/intro/compliance). Overvågningsrapporter kan downloades på Microsoft [Service Trust Portal](https://aka.ms/stp), der fungerer som et centralt lager til Microsoft Enterprise Online Services. Microsoft Managed Desktop er opført i disse dokumenter under kategorien "overvågning og forvaltning".

### <a name="data-subject-requests"></a>Anmodninger fra den registrerede

Microsoft Managed Desktop følger GDPR- og CCPA-bestemmelserne om beskyttelse af personlige oplysninger, som giver fysiske personer specifikke rettigheder til deres personlige data.

Disse rettigheder omfatter:

- Hentning af kopier af personlige data
- Anmodning om rettelser til den
- Begrænsning af behandlingen af den
- Sletter den
- Modtage den i elektronisk format, så den kan flyttes til en anden controller.

Du kan få mere generelle oplysninger om DSR-anmodninger (Data Subject Requests) under [Anmodninger fra fysiske personer og GDPR og CCPA](/compliance/regulatory/gdpr-data-subject-requests).

Hvis du vil udføre den registreredes anmodninger om data, der indsamles af Microsoft Managed Desktop sagsstyringssystem, skal du se følgende anmodninger fra den registrerede:

| Anmodninger fra den registrerede | Beskrivelse |
| ------ | ------ |
| Data fra Microsoft Defender for Endpoint beskeder | Din sikkerhedsadministrator kan anmode om sletning eller udtrækning af personlige data, der er relateret til Microsoft Defender for Endpoint beskeder, ved at sende en rapportanmodning på [administrationsportalen](https://aka.ms/memadmin). <br><br> Angiv følgende oplysninger: <br><ul><li>Anmodningstype: Skift anmodning</li><li>Kategori: Sikkerhed</li><li>Underkategori: Andet</li><li>Beskrivelse: Angiv de relevante enhedsnavne.</li></ul> |
| Data fra Microsoft Managed Desktop supportanmodninger | It-administratoren kan anmode om sletning eller udtrækning af personlige datarelaterede supportanmodninger ved at sende en rapportanmodning på [administrationsportalen](https://aka.ms/memadmin). <br><br> Angiv følgende oplysninger: <ul><li>Anmodningstype: Skift anmodning</li><li>Kategori: Sikkerhed</li><li>Underkategori: Andet</li><li>Beskrivelse: Angiv de relevante enhedsnavne eller brugernavne.</li></ul>

Du kan se DSR-anmodninger fra andre produkter, der er relateret til tjenesten, i følgende artikler:

- Windows [diagnosticeringsdata](/compliance/regulatory/gdpr-dsr-windows)
- Microsoft [Intune-data](/compliance/regulatory/gdpr-dsr-intune)
- Azure Active [Directory-data](/compliance/regulatory/gdpr-dsr-azure)

## <a name="legal"></a>Juridiske

**Microsofts meddelelse om beskyttelse af personlige oplysninger for slutbrugere af produkter, der leveres af organisationskunder**:

[Microsofts erklæring om beskyttelse af personlige oplysninger](https://privacy.microsoft.com/privacystatement) giver slutbrugerne besked om, at når de logger på Microsoft-produkter med en arbejdskonto:

1. Deres organisation kan styre og administrere deres konto (herunder styre indstillinger relateret til beskyttelse af personlige oplysninger) og få adgang til og behandle deres data.
1. Microsoft kan indsamle og behandle dataene for at levere tjenesten til organisationen og slutbrugerne.
